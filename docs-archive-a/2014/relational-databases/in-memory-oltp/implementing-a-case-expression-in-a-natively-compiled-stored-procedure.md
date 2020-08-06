---
title: CASE 문 구현 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 2f82db01-da7e-4a7d-8bc0-48b245e6f768
author: rothja
ms.author: jroth
ms.openlocfilehash: 27059cc09d5507bf2548b23b60f3c2f485c3fe36
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738386"
---
# <a name="implementing-a-case-statement"></a><span data-ttu-id="24cb0-102">CASE 문 구현</span><span class="sxs-lookup"><span data-stu-id="24cb0-102">Implementing a CASE Statement</span></span>
  <span data-ttu-id="24cb0-103">CASE 문은 고유하게 컴파일된 저장 프로시저에서 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="24cb0-103">Case statements are not supported in natively compiled stored procedures.</span></span> <span data-ttu-id="24cb0-104">다음 예제에서는 고유하게 컴파일된 저장 프로시저에서 CASE 문의 기능을 구현하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="24cb0-104">The following sample shows a way to implement the functionality of a case statement in a natively compiled stored procedure.</span></span>  
  
 <span data-ttu-id="24cb0-105">이 예제에서는 테이블 변수를 사용하여 단일 결과 집합을 생성합니다. 이는 데이터 행의 추가 복사본을 만들어야 하므로 제한된 수의 행을 처리하는 경우에만 적합합니다.</span><span class="sxs-lookup"><span data-stu-id="24cb0-105">The samples uses a table variable to construct a single result set, which is only suitable when processing a limited number of rows, as it involves creating an additional copy of the data rows.</span></span>  
  
 <span data-ttu-id="24cb0-106">이 방법의 성능을 테스트하여 애플리케이션에서 예상대로 실행되는지 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="24cb0-106">You should test the performance of this workaround, to be sure that it performs as expected in your application.</span></span>  
  
```  
-- original query  
SELECT   
   SalesOrderID,   
   CASE (OnlineOrderFlag)   
   WHEN 1 THEN N'Order placed online by customer'  
   ELSE N'Order placed by sales person'  
   END  
FROM Sales.SalesOrderHeader_inmem  
  
--  workaround for CASE in natively compiled stored procedures  
--  use a table for the single resultset  
CREATE TYPE dbo.SOHOnlineOrderResult AS TABLE  
(  
   SalesOrderID uniqueidentifier not null index ix_SalesOrderID,  
     OrderFlag nvarchar(100) not null  
) with (memory_optimized=on)  
go  
  
-- natively compiled stored procedure that includes the query  
CREATE PROCEDURE dbo.usp_SOHOnlineOrderResult  
   WITH NATIVE_COMPILATION, SCHEMABINDING, EXECUTE AS OWNER  
   AS BEGIN ATOMIC WITH  
      (TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE=N'us_english')  
  
   -- table variable for creating the single resultset  
   DECLARE @result dbo.SOHOnlineOrderResult  
  
   -- CASE OnlineOrderFlag=1  
   INSERT @result   
   SELECT SalesOrderID, N'Order placed online by customer'  
      FROM Sales.SalesOrderHeader_inmem  
      WHERE OnlineOrderFlag=1  
  
   -- ELSE  
   INSERT @result   
   SELECT SalesOrderID, placed by sales person'  
      FROM Sales.SalesOrderHeader_inmem  
      WHERE OnlineOrderFlag!=1  
  
   -- return single resultset  
   SELECT SalesOrderID, OrderFlag FROM @result  
END  
GO  
  
EXEC dbo.usp_SOHOnlineOrderResult  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="24cb0-107">참고 항목</span><span class="sxs-lookup"><span data-stu-id="24cb0-107">See Also</span></span>  
 <span data-ttu-id="24cb0-108">[고유하게 컴파일된 저장 프로시저의 마이그레이션 문제](migration-issues-for-natively-compiled-stored-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="24cb0-108">[Migration Issues for Natively Compiled Stored Procedures](migration-issues-for-natively-compiled-stored-procedures.md) </span></span>  
 [<span data-ttu-id="24cb0-109">메모리 내 OLTP에서 지원되지 않는 Transact-SQL 구문</span><span class="sxs-lookup"><span data-stu-id="24cb0-109">Transact-SQL Constructs Not Supported by In-Memory OLTP</span></span>](transact-sql-constructs-not-supported-by-in-memory-oltp.md)  
  
  
