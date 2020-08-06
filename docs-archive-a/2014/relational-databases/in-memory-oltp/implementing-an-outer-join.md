---
title: 외부 조인 구현 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 67084043-6b23-4975-b9db-6e49923d4bab
author: rothja
ms.author: jroth
ms.openlocfilehash: 73017541a8fc7b933c4ace1ef6539d53047ea5df
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646446"
---
# <a name="implementing-an-outer-join"></a><span data-ttu-id="3caf5-102">외부 조인 구현</span><span class="sxs-lookup"><span data-stu-id="3caf5-102">Implementing an Outer Join</span></span>
  <span data-ttu-id="3caf5-103">외부 조인은 고유하게 컴파일된 저장 프로시저에서 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3caf5-103">Outer join is not supported in natively compiled stored procedures.</span></span> <span data-ttu-id="3caf5-104">다음 예제에서는 고유하게 컴파일된 저장 프로시저에서 왼쪽 우선 외부 조인의 기능을 구현하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="3caf5-104">The following sample shows a way to implement the functionality of a left outer join in a natively compiled stored procedure.</span></span>  
  
 <span data-ttu-id="3caf5-105">이 예제에서는 테이블 변수를 사용하여 조인의 왼쪽에서 커서를 시뮬레이트하고 또 다른 테이블 변수를 사용하여 단일 결과 집합을 생성합니다. 이는 데이터 행의 추가 복사본을 만들어야 하므로 제한된 수의 행을 처리하는 경우에만 적합합니다.</span><span class="sxs-lookup"><span data-stu-id="3caf5-105">The samples uses a table variable to simulate a cursor on the left side of the join, and a table variable to construct a single result set, which is only suitable when processing a limited number of rows as it involves creating an additional copy of the data rows.</span></span>  
  
 <span data-ttu-id="3caf5-106">@outerT1의 행을 반복 하는 데 while 루프를 사용 하 여 커서를 시뮬레이션 하는 데 t1_type 형식의 변수 ()가 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3caf5-106">A variable (@outer) of type t1_type is used to iterate over the rows from t1, using a while loop to simulate a cursor.</span></span> <span data-ttu-id="3caf5-107">@result그런 다음 t1t2_join_type 형식의 변수를 사용 하 여 결과 집합을 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="3caf5-107">The variable @result of type t1t2_join_type is then used to construct the result set.</span></span>  
  
 <span data-ttu-id="3caf5-108">이 방법의 성능을 테스트하여 애플리케이션에서 예상대로 실행되는지 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3caf5-108">You should test the performance of this workaround, to be sure that it performs as expected in your application.</span></span>  
  
```  
-- original query:  
select   
   t1.c1 as t1c1,  
   t1.c2 as t1c2,  
   t2.c2 as t2c2,  
   t2.c3 as t2c3  
   from t1 left join t2 on t1.c2=t2.c3  
GO  
  
create table dbo.t1  
(c1 int not null primary key nonclustered,  
c2 int not null) with (memory_optimized=on)  
  
create table dbo.t2  
(c2 int not null primary key nonclustered,  
c3 int not null) with (memory_optimized=on)  
  
INSERT t1 VALUES (1,2)  
INSERT t1 VALUES (2,3)  
INSERT t1 VALUES (3,2)  
INSERT t2 VALUES (2,3)  
INSERT t2 VALUES (4,3)  
GO  
  
create type dbo.t1_type as table  
(  
   id int identity not null primary key nonclustered hash with (bucket_count=1024),  
   c1 int,  
   c2 int  
) with (memory_optimized=on)  
GO  
  
create type dbo.t1t2_join_type as table  
(  
   t1c1 int not null index ix_t1c1,  
   t1c2 int not null,  
   t2c2 int,  
   t2c3 int  
) with (memory_optimized=on)  
GO  
  
-- ====== scenario: generic left join  
  
-- stored procedure including the workaround  
create procedure dbo.usp_left_join  
with native_compilation, execute as owner, schemabinding  
as  
begin atomic with (transaction isolation level = snapshot, language = N'us_english')  
  
   DECLARE @outer dbo.t1_type  
   DECLARE @result dbo.t1t2_join_type  
  
   -- populate the variable used for iterating over the outer rows  
   INSERT @outer(c1, c2) select c1,c2 from dbo.t1  
  
   DECLARE @i int = 1  
   DECLARE @max int = scope_identity()  
  
   DECLARE @t1c1 int  
   DECLARE @t1c2 int  
  
   while @i <= @max  
   begin     
      select @t1c1 = c1, @t1c2 = c2 from @outer where id = @i  
  
      INSERT @result select @t1c1, @t1c2, c2, c3 from dbo.t2 where c3 = @t1c2  
  
      if @@rowcount = 0   
         INSERT @result (t1c1, t1c2) VALUES (@t1c1, @t1c2)  
  
      set @i += 1  
   end  
  
   select   
      t1c1,  
      t1c2,  
      t2c2,  
      t2c3  
   from @result  
end  
GO  
  
exec dbo.usp_left_join  
```  
  
## <a name="see-also"></a><span data-ttu-id="3caf5-109">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3caf5-109">See Also</span></span>  
 <span data-ttu-id="3caf5-110">[고유하게 컴파일된 저장 프로시저의 마이그레이션 문제](migration-issues-for-natively-compiled-stored-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="3caf5-110">[Migration Issues for Natively Compiled Stored Procedures](migration-issues-for-natively-compiled-stored-procedures.md) </span></span>  
 [<span data-ttu-id="3caf5-111">메모리 내 OLTP에서 지원되지 않는 Transact-SQL 구문</span><span class="sxs-lookup"><span data-stu-id="3caf5-111">Transact-SQL Constructs Not Supported by In-Memory OLTP</span></span>](transact-sql-constructs-not-supported-by-in-memory-oltp.md)  
  
  
