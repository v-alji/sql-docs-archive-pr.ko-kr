---
title: 메모리 액세스에 최적화된 테이블에서 IDENTITY 구현 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: c0a704a3-3a31-4c2c-b967-addacda62ef8
author: rothja
ms.author: jroth
ms.openlocfilehash: 955f9f1a905a9d0c71304320f60abe300e430e4f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649557"
---
# <a name="implementing-identity-in-a-memory-optimized-table"></a><span data-ttu-id="a549a-102">메모리 액세스에 최적화된 테이블에서 IDENTITY 구현</span><span class="sxs-lookup"><span data-stu-id="a549a-102">Implementing IDENTITY in a Memory-Optimized Table</span></span>
  <span data-ttu-id="a549a-103">IDENTITY(1, 1)는 메모리 최적화 테이블에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="a549a-103">IDENTITY(1, 1) is supported on a memory-optimized table.</span></span> <span data-ttu-id="a549a-104">그러나 x != 1 또는 y != 1인 IDENTITY(x, y) 정의를 사용하는 ID 열은 메모리 최적화 테이블에서 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a549a-104">However, identity columns with definition of IDENTITY(x, y) where x != 1 or y != 1 are not supported on memory-optimized tables.</span></span> <span data-ttu-id="a549a-105">IDENTITY 값에 대한 해결 방법은 SEQUENCE 개체를 사용합니다([Sequence Numbers](../sequence-numbers/sequence-numbers.md)).</span><span class="sxs-lookup"><span data-stu-id="a549a-105">The workaround for IDENTITY values uses the SEQUENCE object ([Sequence Numbers](../sequence-numbers/sequence-numbers.md)).</span></span>  
  
 <span data-ttu-id="a549a-106">먼저 메모리 내 OLTP로 변환 중인 테이블에서 IDENTITY 속성을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="a549a-106">First remove the IDENTITY property from the table you are converting to In-Memory OLTP.</span></span> <span data-ttu-id="a549a-107">그런 다음 테이블의 행에 대해 새 SEQUENCE 개체를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="a549a-107">Then, define a new SEQUENCE object for the column in the table.</span></span> <span data-ttu-id="a549a-108">ID 열인 SEQUENCE 개체는 NEXT VALUE FOR 구문을 사용하여 새 ID 값을 얻기 위해 열의 DEFAULT 값을 만드는 기능에 의존합니다.</span><span class="sxs-lookup"><span data-stu-id="a549a-108">SEQUENCE objects as identity columns rely on the ability to create DEFAULT values for columns that use the NEXT VALUE FOR syntax to get a new identity value.</span></span> <span data-ttu-id="a549a-109">메모리 내 OLTP에서는 DEFAULT가 지원되지 않으므로 새로 생성된 SEQUENCE 값을 INSERT 문 또는 삽입을 수행하는 고유하게 컴파일된 저장 프로시저로 전달해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a549a-109">Since DEFAULTs are not supported in In-Memory OLTP, you need to pass the newly-generated SEQUENCE value either to the INSERT statement or to a natively compiled stored procedure that does the insert.</span></span> <span data-ttu-id="a549a-110">다음 예에서는 이러한 패턴을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="a549a-110">The following example demonstrates this pattern.</span></span>  
  
```sql  
-- Create a new In-Memory OLTP table to simulate IDENTITY insert  
-- Here the column C1 was the identity column in the original table  
--  
create table T1  
(  
  
[c1] integer not null primary key T1_c1 nonclustered,  
[c2] varchar(32) not null,  
[c3] datetime not null  
  
) with (memory_optimized = on)  
go  
  
-- This is a sequence provider that will give us values for column [c1]  
--  
create sequence usq_SequenceForT1 as integer start with 2 increment by 1  
go  
  
--   insert a sample row using the sequence  
--   note that a new value needs to be retrieved form   
--   the sequence object for every insert  
--  
declare @c1 integer = next value for [dbo].[usq_SequenceForT1]  
insert into T1 values (@c1, 'test', getdate())  
```  
  
 <span data-ttu-id="a549a-111">삽입을 여러 번 수행하면 [c1] 열에 단순하게 증가하는 유효한 값이 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="a549a-111">After performing the insert several times, you see valid monotonically increasing values in column [c1].</span></span> <span data-ttu-id="a549a-112">이 결과 집합은 `ORDER BY` 없이 테이블 검색과 해시 인덱스를 사용하여 생성되므로 행은 정렬되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a549a-112">This result set is generated using table scan and hash index without `ORDER BY` so the rows are not ordered.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a549a-113">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a549a-113">See Also</span></span>  
 [<span data-ttu-id="a549a-114">메모리 내 OLTP로 마이그레이션</span><span class="sxs-lookup"><span data-stu-id="a549a-114">Migrating to In-Memory OLTP</span></span>](migrating-to-in-memory-oltp.md)  
  
  
