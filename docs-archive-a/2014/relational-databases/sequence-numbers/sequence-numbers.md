---
title: 시퀀스 번호 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- sequence number object, overview
- sequence [Database Engine]
- autonumbers, sequences
- sequence numbers [SQL Server]
- sequence number object
ms.assetid: c900e30d-2fd3-4d5f-98ee-7832f37e79d1
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 6c65b4df915a85cf0ec7c7c0c8c0ff9f6607ad96
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741687"
---
# <a name="sequence-numbers"></a><span data-ttu-id="764f8-102">시퀀스 번호</span><span class="sxs-lookup"><span data-stu-id="764f8-102">Sequence Numbers</span></span>
  <span data-ttu-id="764f8-103">시퀀스는 시퀀스를 만들 때 지정한 사양에 따라 숫자 값의 시퀀스를 생성하는 사용자 정의 스키마 바인딩된 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="764f8-103">A sequence is a user-defined schema-bound object that generates a sequence of numeric values according to the specification with which the sequence was created.</span></span> <span data-ttu-id="764f8-104">숫자 값의 시퀀스는 지정된 간격으로 올림차순 또는 내림차순으로 생성되며 요청된 경우 순환(반복)할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="764f8-104">The sequence of numeric values is generated in an ascending or descending order at a defined interval and may cycle (repeat) as requested.</span></span> <span data-ttu-id="764f8-105">ID 열과 달리 시퀀스는 테이블에 연결되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="764f8-105">Sequences, unlike identity columns, are not associated with tables.</span></span> <span data-ttu-id="764f8-106">애플리케이션은 다음 값을 가져오기 위해 시퀀스 개체를 참조합니다.</span><span class="sxs-lookup"><span data-stu-id="764f8-106">An application refers to a sequence object to receive its next value.</span></span> <span data-ttu-id="764f8-107">시퀀스와 테이블 간의 관계는 애플리케이션에서 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="764f8-107">The relationship between sequences and tables is controlled by the application.</span></span> <span data-ttu-id="764f8-108">사용자 애플리케이션에서는 시퀀스 개체를 참조하고 여러 행 및 테이블에 걸쳐 값 키를 조정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="764f8-108">User applications can reference a sequence object and coordinate the values keys across multiple rows and tables.</span></span>  
  
 <span data-ttu-id="764f8-109">시퀀스는 **CREATE SEQUENCE** 문을 사용하여 테이블과 독립적으로 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="764f8-109">A sequence is created independently of the tables by using the **CREATE SEQUENCE** statement.</span></span> <span data-ttu-id="764f8-110">옵션을 통해 증분, 최대값 및 최소값, 시작 지점, 자동 다시 시작 기능, 성능 개선을 위한 캐싱을 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="764f8-110">Options enable you to control the increment, maximum and minimum values, starting point, automatic restarting capability, and caching to improve performance.</span></span> <span data-ttu-id="764f8-111">옵션에 대한 자세한 내용은 [CREATE SEQUENCE](/sql/t-sql/statements/create-sequence-transact-sql)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="764f8-111">For information about the options, see [CREATE SEQUENCE](/sql/t-sql/statements/create-sequence-transact-sql).</span></span>  
  
 <span data-ttu-id="764f8-112">행을 삽입하면 생성되는 ID 열 값과는 달리 애플리케이션에서는 [NEXT VALUE FOR](/sql/t-sql/functions/next-value-for-transact-sql) 함수를 호출하여 행을 삽입하기 전에 다음 시퀀스 번호를 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="764f8-112">Unlike identity column values, which are generated when rows are inserted, an application can obtain the next sequence number before inserting the row by calling the [NEXT VALUE FOR](/sql/t-sql/functions/next-value-for-transact-sql) function.</span></span> <span data-ttu-id="764f8-113">NEXT VALUE FOR가 호출되면 테이블에 삽입되지 않더라도 시퀀스 번호가 할당됩니다.</span><span class="sxs-lookup"><span data-stu-id="764f8-113">The sequence number is allocated when NEXT VALUE FOR is called even if the number is never inserted into a table.</span></span> <span data-ttu-id="764f8-114">테이블 정의에서 행의 기본값으로 NEXT VALUE FOR 함수를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="764f8-114">The NEXT VALUE FOR function can be used as the default value for a column in a table definition.</span></span> <span data-ttu-id="764f8-115">일정 범위의 여러 시퀀스 번호를 한 번에 가져오려면 [sp_sequence_get_range](/sql/relational-databases/system-stored-procedures/sp-sequence-get-range-transact-sql) 를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="764f8-115">Use [sp_sequence_get_range](/sql/relational-databases/system-stored-procedures/sp-sequence-get-range-transact-sql) to get a range of multiple sequence numbers at once.</span></span>  
  
 <span data-ttu-id="764f8-116">시퀀스는 임의의 정수 데이터 형식으로 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="764f8-116">A sequence can be defined as any integer data type.</span></span> <span data-ttu-id="764f8-117">데이터 형식을 지정하지 않으면 시퀀스의 기본값은 `bigint`가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="764f8-117">If the data type is not specified, a sequence defaults to `bigint`.</span></span>  
  
## <a name="using-sequences"></a><span data-ttu-id="764f8-118">시퀀스 사용</span><span class="sxs-lookup"><span data-stu-id="764f8-118">Using Sequences</span></span>  
 <span data-ttu-id="764f8-119">다음 시나리오에서는 ID 열 대신 시퀀스를 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="764f8-119">Use sequences instead of identity columns in the following scenarios:</span></span>  
  
-   <span data-ttu-id="764f8-120">애플리케이션에서 테이블에 삽입하기 전에 번호가 필요한 경우</span><span class="sxs-lookup"><span data-stu-id="764f8-120">The application requires a number before the insert into the table is made.</span></span>  
  
-   <span data-ttu-id="764f8-121">애플리케이션에서 여러 테이블 또는 테이블 내의 여러 열 사이에 단일 번호 시리즈를 공유해야 하는 경우</span><span class="sxs-lookup"><span data-stu-id="764f8-121">The application requires sharing a single series of numbers between multiple tables or multiple columns within a table.</span></span>  
  
-   <span data-ttu-id="764f8-122">지정된 번호에 도달하면 애플리케이션이 번호 시리즈를 다시 시작해야 하는 경우.</span><span class="sxs-lookup"><span data-stu-id="764f8-122">The application must restart the number series when a specified number is reached.</span></span> <span data-ttu-id="764f8-123">예를 들어 1에서 10까지의 값을 할당한 후 애플리케이션이 다시 1에서 10까지의 값을 할당하는 경우가 여기에 해당합니다.</span><span class="sxs-lookup"><span data-stu-id="764f8-123">For example, after assigning values 1 through 10, the application starts assigning values 1 through 10 again.</span></span>  
  
-   <span data-ttu-id="764f8-124">애플리케이션에서 시퀀스 값을 다른 필드를 기준으로 정렬해야 하는 경우.</span><span class="sxs-lookup"><span data-stu-id="764f8-124">The application requires sequence values to be sorted by another field.</span></span> <span data-ttu-id="764f8-125">NEXT VALUE FOR 함수는 함수 호출에 OVER 절을 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="764f8-125">The NEXT VALUE FOR function can apply the OVER clause to the function call.</span></span> <span data-ttu-id="764f8-126">OVER 절을 사용하면 반환된 값이 OVER 절의 ORDER BY 절 순서에 따라 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="764f8-126">The OVER clause guarantees that the values returned are generated in the order of the OVER clause's ORDER BY clause.</span></span>  
  
-   <span data-ttu-id="764f8-127">애플리케이션에서 여러 번호를 동시에 할당해야 하는 경우.</span><span class="sxs-lookup"><span data-stu-id="764f8-127">An application requires multiple numbers to be assigned at the same time.</span></span> <span data-ttu-id="764f8-128">예를 들어 애플리케이션이 일련 번호를 다섯 개 예약해야 하는 경우가 여기에 해당합니다.</span><span class="sxs-lookup"><span data-stu-id="764f8-128">For example, an application needs to reserve five sequential numbers.</span></span> <span data-ttu-id="764f8-129">ID 값을 요청하는 경우 다른 프로세스가 동시에 번호를 요청하면 시리즈에 간격이 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="764f8-129">Requesting identity values could result in gaps in the series if other processes were simultaneously issued numbers.</span></span> <span data-ttu-id="764f8-130">sp_sequence_get_range를 호출하면 시퀀스에서 여러 개의 번호를 한 번에 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="764f8-130">Calling sp_sequence_get_range can retrieve several numbers in the sequence at once.</span></span>  
  
-   <span data-ttu-id="764f8-131">증분 값 등 시퀀스 사양을 변경해야 하는 경우</span><span class="sxs-lookup"><span data-stu-id="764f8-131">You need to change the specification of the sequence, such as the increment value.</span></span>  
  
## <a name="limitations"></a><span data-ttu-id="764f8-132">제한 사항</span><span class="sxs-lookup"><span data-stu-id="764f8-132">Limitations</span></span>  
 <span data-ttu-id="764f8-133">값을 변경할 수 없는 ID 열과 달리 시퀀스 값은 테이블에 삽입된 이후에 자동으로 보호되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="764f8-133">Unlike identity columns, whose values cannot be changed, sequence values are not automatically protected after insertion into the table.</span></span> <span data-ttu-id="764f8-134">시퀀스 값이 변경되지 않도록 하려면 테이블에서 업데이트 트리거를 사용하여 변경 내용을 롤백합니다.</span><span class="sxs-lookup"><span data-stu-id="764f8-134">To prevent sequence values from being changed, use an update trigger on the table to roll back changes.</span></span>  
  
 <span data-ttu-id="764f8-135">시퀀스 값의 경우 고유성이 자동으로 적용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="764f8-135">Uniqueness is not automatically enforced for sequence values.</span></span> <span data-ttu-id="764f8-136">시퀀스 값을 다시 사용하는 것은 의도된 것입니다.</span><span class="sxs-lookup"><span data-stu-id="764f8-136">The ability to reuse sequence values is by design.</span></span> <span data-ttu-id="764f8-137">테이블의 시퀀스 값이 고유해야 하는 경우 열에 고유 인덱스를 만드십시오.</span><span class="sxs-lookup"><span data-stu-id="764f8-137">If sequence values in a table are required to be unique, create a unique index on the column.</span></span> <span data-ttu-id="764f8-138">테이블의 시퀀스 값이 테이블 그룹 전체에서 고유해야 하는 경우 업데이트 문이나 시퀀스 번호 순환으로 인해 중복이 발생하지 않도록 트리거를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="764f8-138">If sequence values in a table are required to be unique throughout a group of tables, create triggers to prevent duplicates caused by update statements or sequence number cycling.</span></span>  
  
 <span data-ttu-id="764f8-139">시퀀스 개체는 정의에 따라 번호를 생성하지만 어떻게 사용되는지는 제어하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="764f8-139">The sequence object generates numbers according to its definition, but the sequence object does not control how the numbers are used.</span></span> <span data-ttu-id="764f8-140">트랜잭션이 롤백되거나, 시퀀스 개체를 여러 테이블에서 공유하거나, 테이블에서 사용하지 않고 시퀀스 번호를 할당하는 경우 테이블에 삽입된 시퀀스 번호에 간격이 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="764f8-140">Sequence numbers inserted into a table can have gaps when a transaction is rolled back, when a sequence object is shared by multiple tables, or when sequence numbers are allocated without using them in tables.</span></span> <span data-ttu-id="764f8-141">CACHE 옵션을 사용하여 만들 경우 전원 오류와 같은 예기치 않은 종료로 인해 캐시의 시퀀스 번호가 손실될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="764f8-141">When created with the CACHE option, an unexpected shutdown, such as a power failure, can lose the sequence numbers in the cache.</span></span>  
  
 <span data-ttu-id="764f8-142">하나의 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 문 내에 동일한 시퀀스 생성기를 지정하는 `NEXT VALUE FOR` 함수 인스턴스가 여러 개 있는 경우 모든 인스턴스에서 해당 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 문으로 처리되는 지정된 행에 대해 동일한 값을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="764f8-142">If there are multiple instances of the `NEXT VALUE FOR` function specifying the same sequence generator within a single [!INCLUDE[tsql](../../../includes/tsql-md.md)] statement, all those instances return the same value for a given row processed by that [!INCLUDE[tsql](../../../includes/tsql-md.md)] statement.</span></span> <span data-ttu-id="764f8-143">이 동작은 ANSI 표준을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="764f8-143">This behavior is consistent with the ANSI standard.</span></span>  
  
## <a name="typical-use"></a><span data-ttu-id="764f8-144">일반적인 용도</span><span class="sxs-lookup"><span data-stu-id="764f8-144">Typical Use</span></span>  
 <span data-ttu-id="764f8-145">-2,147,483,648에서 2,147,483,647까지 1씩 증가하는 정수 시퀀스 번호를 만들려면 다음 문을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="764f8-145">To create an integer sequence number that increments by 1 from -2,147,483,648 to 2,147,483,647, use the following statement.</span></span>  
  
```  
CREATE SEQUENCE Schema.SequenceName  
    AS int  
    INCREMENT BY 1 ;  
```  
  
 <span data-ttu-id="764f8-146">1에서 2,147,483,647까지 1씩 증가하는 ID 열과 유사한 정수 시퀀스 번호를 만들려면 다음 문을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="764f8-146">To create an integer sequence number similar to an identity column that increments by 1 from 1 to 2,147,483,647, use the following statement.</span></span>  
  
```  
CREATE SEQUENCE Schema.SequenceName  
    AS int  
    START WITH 1  
    INCREMENT BY 1 ;  
  
```  
  
## <a name="managing-sequences"></a><span data-ttu-id="764f8-147">시퀀스 관리</span><span class="sxs-lookup"><span data-stu-id="764f8-147">Managing Sequences</span></span>  
 <span data-ttu-id="764f8-148">시퀀스에 대한 자세한 내용을 보려면 [sys.sequences](/sql/relational-databases/system-catalog-views/sys-sequences-transact-sql)를 쿼리하십시오.</span><span class="sxs-lookup"><span data-stu-id="764f8-148">For information about sequences, query [sys.sequences](/sql/relational-databases/system-catalog-views/sys-sequences-transact-sql).</span></span>  
  
## <a name="examples"></a><span data-ttu-id="764f8-149">예</span><span class="sxs-lookup"><span data-stu-id="764f8-149">Examples</span></span>  
 <span data-ttu-id="764f8-150">[CREATE SEQUENCE&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-sequence-transact-sql), [NEXT VALUE FOR&#40;Transact-SQL&#41;](/sql/t-sql/functions/next-value-for-transact-sql) 및 [sp_sequence_get_range](/sql/relational-databases/system-stored-procedures/sp-sequence-get-range-transact-sql) 항목에서 또 다른 예제를 찾아볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="764f8-150">There are additional examples in the topics [CREATE SEQUENCE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-sequence-transact-sql), [NEXT VALUE FOR &#40;Transact-SQL&#41;](/sql/t-sql/functions/next-value-for-transact-sql), and [sp_sequence_get_range](/sql/relational-databases/system-stored-procedures/sp-sequence-get-range-transact-sql).</span></span>  
  
### <a name="a-using-a-sequence-number-in-a-single-table"></a><span data-ttu-id="764f8-151">A.</span><span class="sxs-lookup"><span data-stu-id="764f8-151">A.</span></span> <span data-ttu-id="764f8-152">단일 테이블에서 시퀀스 번호 사용</span><span class="sxs-lookup"><span data-stu-id="764f8-152">Using a sequence number in a single table</span></span>  
 <span data-ttu-id="764f8-153">다음 예에서는 Test라는 스키마, Orders라는 테이블, CountBy1이라는 시퀀스를 만든 다음 NEXT VALUE FOR 함수를 사용하여 테이블에 행을 삽입합니다.</span><span class="sxs-lookup"><span data-stu-id="764f8-153">The following example creates a schema named Test, a table named Orders, and a sequence named CountBy1, and then inserts rows into the table using the NEXT VALUE FOR function.</span></span>  
  
```  
--Create the Test schema  
CREATE SCHEMA Test ;  
GO  
  
-- Create a table  
CREATE TABLE Test.Orders  
    (OrderID int PRIMARY KEY,  
    Name varchar(20) NOT NULL,  
    Qty int NOT NULL);  
GO  
  
-- Create a sequence  
CREATE SEQUENCE Test.CountBy1  
    START WITH 1  
    INCREMENT BY 1 ;  
GO  
  
-- Insert three records  
INSERT Test.Orders (OrderID, Name, Qty)  
    VALUES (NEXT VALUE FOR Test.CountBy1, 'Tire', 2) ;  
INSERT test.Orders (OrderID, Name, Qty)  
    VALUES (NEXT VALUE FOR Test.CountBy1, 'Seat', 1) ;  
INSERT test.Orders (OrderID, Name, Qty)  
    VALUES (NEXT VALUE FOR Test.CountBy1, 'Brake', 1) ;  
GO  
  
-- View the table  
SELECT * FROM Test.Orders ;  
GO  
```  
  
 [!INCLUDE[ssResult](../../../includes/ssresult-md.md)]  
  
 `OrderID  Name    Qty`  
  
 `1        Tire    2`  
  
 `2        Seat    1`  
  
 `3        Brake   1`  
  
### <a name="b-calling-next-value-for-before-inserting-a-row"></a><span data-ttu-id="764f8-154">B.</span><span class="sxs-lookup"><span data-stu-id="764f8-154">B.</span></span> <span data-ttu-id="764f8-155">행을 삽입하기 전에 NEXT VALUE FOR 호출</span><span class="sxs-lookup"><span data-stu-id="764f8-155">Calling NEXT VALUE FOR before inserting a row</span></span>  
 <span data-ttu-id="764f8-156">예 1에서 만든 `Orders` 테이블을 사용하여 다음 예에서는 `@nextID`라는 변수를 선언한 다음 NEXT VALUE FOR 함수를 사용하여 변수를 다음으로 사용 가능한 시퀀스 번호로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="764f8-156">Using the `Orders` table created in example A, the following example declares a variable named `@nextID`, and then uses the NEXT VALUE FOR function to set the variable to the next available sequence number.</span></span> <span data-ttu-id="764f8-157">애플리케이션은 고객에게 잠재적 주문에 대한 `OrderID` 번호를 제공하고 주문의 유효성을 검사하는 등 주문에 대한 처리를 수행하고 있는 것으로 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="764f8-157">The application is presumed to do some processing of the order, such as providing the customer with the `OrderID` number of their potential order, and then validates the order.</span></span> <span data-ttu-id="764f8-158">처리에 걸리는 시간이나 처리 중 추가되는 다른 주문 수에 관계없이 이 연결에서 사용하도록 원래 번호가 보관됩니다.</span><span class="sxs-lookup"><span data-stu-id="764f8-158">No matter how long this processing might take, or how many other orders are added during the process, the original number is preserved for use by this connection.</span></span> <span data-ttu-id="764f8-159">마지막으로 `INSERT` 문은 `Orders` 테이블에 주문을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="764f8-159">Finally, the `INSERT` statement adds the order to the `Orders` table.</span></span>  
  
```  
DECLARE @NextID int ;  
SET @NextID = NEXT VALUE FOR Test.CountBy1;  
-- Some work happens  
INSERT Test.Orders (OrderID, Name, Qty)  
    VALUES (@NextID, 'Rim', 2) ;  
GO  
  
```  
  
### <a name="c-using-a-sequence-number-in-multiple-tables"></a><span data-ttu-id="764f8-160">C.</span><span class="sxs-lookup"><span data-stu-id="764f8-160">C.</span></span> <span data-ttu-id="764f8-161">여러 테이블에서 시퀀스 사용</span><span class="sxs-lookup"><span data-stu-id="764f8-161">Using a sequence number in multiple tables</span></span>  
 <span data-ttu-id="764f8-162">이 예에서는 생산 라인의 모니터링 프로세스가 작업장 전체에서 발생하는 이벤트 알림을 받는다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="764f8-162">This example assumes that a production-line monitoring process receives notification of events that occur throughout the workshop.</span></span> <span data-ttu-id="764f8-163">각 이벤트는 고유하며 일정 간격으로 증가하는 `EventID` 번호를 받습니다.</span><span class="sxs-lookup"><span data-stu-id="764f8-163">Each event receives a unique and monotonically increasing `EventID` number.</span></span> <span data-ttu-id="764f8-164">모든 이벤트를 조합하는 보고서가 각 이벤트를 고유하게 식별할 수 있도록 모든 이벤트는 같은 `EventID` 시퀀스 번호를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="764f8-164">All events use the same `EventID` sequence number so that reports that combine all events can uniquely identify each event.</span></span> <span data-ttu-id="764f8-165">하지만 이벤트 데이터는 이벤트 유형에 따라 세 개의 다른 테이블에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="764f8-165">However the event data is stored in three different tables, depending on the type of event.</span></span> <span data-ttu-id="764f8-166">코드 예에서는 `Audit`이라는 스키마, `EventCounter`라는 시퀀스 및 `EventCounter` 시퀀스를 기본값으로 사용하는 세 개의 테이블을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="764f8-166">The code example creates a schema named `Audit`, a sequence named `EventCounter`, and three tables which each use the `EventCounter` sequence as a default value.</span></span> <span data-ttu-id="764f8-167">그런 다음 이 예에서는 세 테이블에 행을 추가하고 결과를 쿼리합니다.</span><span class="sxs-lookup"><span data-stu-id="764f8-167">Then the example adds rows to the three tables and queries the results.</span></span>  
  
```  
CREATE SCHEMA Audit ;  
GO  
CREATE SEQUENCE Audit.EventCounter  
    AS int  
    START WITH 1  
    INCREMENT BY 1 ;  
GO  
  
CREATE TABLE Audit.ProcessEvents  
(  
    EventID int PRIMARY KEY CLUSTERED   
        DEFAULT (NEXT VALUE FOR Audit.EventCounter),  
    EventTime datetime NOT NULL DEFAULT (getdate()),  
    EventCode nvarchar(5) NOT NULL,  
    Description nvarchar(300) NULL  
) ;  
GO  
  
CREATE TABLE Audit.ErrorEvents  
(  
    EventID int PRIMARY KEY CLUSTERED  
        DEFAULT (NEXT VALUE FOR Audit.EventCounter),  
    EventTime datetime NOT NULL DEFAULT (getdate()),  
    EquipmentID int NULL,  
    ErrorNumber int NOT NULL,  
    EventDesc nvarchar(256) NULL  
) ;  
GO  
  
CREATE TABLE Audit.StartStopEvents  
(  
    EventID int PRIMARY KEY CLUSTERED  
        DEFAULT (NEXT VALUE FOR Audit.EventCounter),  
    EventTime datetime NOT NULL DEFAULT (getdate()),  
    EquipmentID int NOT NULL,  
    StartOrStop bit NOT NULL  
) ;  
GO  
  
INSERT Audit.StartStopEvents (EquipmentID, StartOrStop)   
    VALUES (248, 0) ;  
INSERT Audit.StartStopEvents (EquipmentID, StartOrStop)   
    VALUES (72, 0) ;  
INSERT Audit.ProcessEvents (EventCode, Description)   
    VALUES (2735,   
    'Clean room temperature 18 degrees C.') ;  
INSERT Audit.ProcessEvents (EventCode, Description)   
    VALUES (18, 'Spin rate threashold exceeded.') ;  
INSERT Audit.ErrorEvents (EquipmentID, ErrorNumber, EventDesc)   
    VALUES (248, 82, 'Feeder jam') ;  
INSERT Audit.StartStopEvents (EquipmentID, StartOrStop)   
    VALUES (248, 1) ;  
INSERT Audit.ProcessEvents (EventCode, Description)   
    VALUES (1841, 'Central feed in bypass mode.') ;  
-- The following statement combines all events, though not all fields.  
SELECT EventID, EventTime, Description FROM Audit.ProcessEvents   
UNION SELECT EventID, EventTime, EventDesc FROM Audit.ErrorEvents   
UNION SELECT EventID, EventTime,   
CASE StartOrStop   
    WHEN 0 THEN 'Start'   
    ELSE 'Stop'  
END   
FROM Audit.StartStopEvents  
ORDER BY EventID ;  
GO  
  
```  
  
 [!INCLUDE[ssResult](../../../includes/ssresult-md.md)]  
  
 `EventID  EventTime                Description`  
  
 `1        2009-11-02 15:00:51.157  Start`  
  
 `2        2009-11-02 15:00:51.160  Start`  
  
 `3        2009-11-02 15:00:51.167  Clean room temperature 18 degrees C.`  
  
 `4        2009-11-02 15:00:51.167  Spin rate threshold exceeded.`  
  
 `5        2009-11-02 15:00:51.173  Feeder jam`  
  
 `6        2009-11-02 15:00:51.177  Stop`  
  
 `7        2009-11-02 15:00:51.180  Central feed in bypass mode.`  
  
### <a name="d-generating-repeating-sequence-numbers-in-a-result-set"></a><span data-ttu-id="764f8-168">D.</span><span class="sxs-lookup"><span data-stu-id="764f8-168">D.</span></span> <span data-ttu-id="764f8-169">결과 집합에 반복 시퀀스 번호 생성</span><span class="sxs-lookup"><span data-stu-id="764f8-169">Generating repeating sequence numbers in a result set</span></span>  
 <span data-ttu-id="764f8-170">다음 예에서는 순환 기능 및 SELECT 문에서 `NEXT VALUE FOR` 를 사용하는 기능을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="764f8-170">The following example demonstrates two features of sequence numbers: cycling, and using `NEXT VALUE FOR` in a select statement.</span></span>  
  
```  
CREATE SEQUENCE CountBy5  
   AS tinyint  
    START WITH 1  
    INCREMENT BY 1  
    MINVALUE 1  
    MAXVALUE 5  
    CYCLE ;  
GO  
  
SELECT NEXT VALUE FOR CountBy5 AS SurveyGroup, Name FROM sys.objects ;  
GO  
```  
  
### <a name="e-generating-sequence-numbers-for-a-result-set-by-using-the-over-clause"></a><span data-ttu-id="764f8-171">E.</span><span class="sxs-lookup"><span data-stu-id="764f8-171">E.</span></span> <span data-ttu-id="764f8-172">OVER 절을 사용하여 결과 집합에 대한 시퀀스 번호 생성</span><span class="sxs-lookup"><span data-stu-id="764f8-172">Generating sequence numbers for a result set by using the OVER clause</span></span>  
 <span data-ttu-id="764f8-173">다음 예에서는 시퀀스 번호 열을 추가하기 전에 `OVER` 절을 사용하여 `Name` 을 기준으로 결과 집합을 정렬합니다.</span><span class="sxs-lookup"><span data-stu-id="764f8-173">The following example uses the `OVER` clause to sort the result set by `Name` before it adds the sequence number column.</span></span>  
  
```  
USE AdventureWorks2012 ;  
GO  
  
CREATE SCHEMA Samples ;  
GO  
  
CREATE SEQUENCE Samples.IDLabel  
    AS tinyint  
    START WITH 1  
    INCREMENT BY 1 ;  
GO  
  
SELECT NEXT VALUE FOR Samples.IDLabel OVER (ORDER BY Name) AS NutID, ProductID, Name, ProductNumber FROM Production.Product  
WHERE Name LIKE '%nut%' ;  
```  
  
### <a name="f-resetting-the-sequence-number"></a><span data-ttu-id="764f8-174">F.</span><span class="sxs-lookup"><span data-stu-id="764f8-174">F.</span></span> <span data-ttu-id="764f8-175">시퀀스 번호 다시 설정</span><span class="sxs-lookup"><span data-stu-id="764f8-175">Resetting the sequence number</span></span>  
 <span data-ttu-id="764f8-176">예 5에서는 `Samples.IDLabel` 시퀀스 번호의 첫 79개를 소비했습니다.</span><span class="sxs-lookup"><span data-stu-id="764f8-176">Example E consumed the first 79 of the `Samples.IDLabel` sequence numbers.</span></span> <span data-ttu-id="764f8-177">`AdventureWorks2012` 버전에 따라 다른 개수의 결과가 반환되었을 수 있습니다. 다음을 실행하여 다음 시퀀스 번호 79개(80 ~ 158)를 소비합니다.</span><span class="sxs-lookup"><span data-stu-id="764f8-177">(Your version of `AdventureWorks2012` may return a different number of results.) Execute the following to consume the next 79 sequence numbers (80 though 158).</span></span>  
  
```  
SELECT NEXT VALUE FOR Samples.IDLabel OVER (ORDER BY Name) AS NutID, ProductID, Name, ProductNumber FROM Production.Product  
WHERE Name LIKE '%nut%' ;  
```  
  
 <span data-ttu-id="764f8-178">다음 문을 실행하여 `Samples.IDLabel` 시퀀스를 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="764f8-178">Execute the following statement to restart the `Samples.IDLabel` sequence.</span></span>  
  
```  
ALTER SEQUENCE Samples.IDLabel  
RESTART WITH 1 ;  
```  
  
 <span data-ttu-id="764f8-179">SELECT 문을 다시 실행하여 `Samples.IDLabel` 시퀀스가 번호 1로 다시 시작하는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="764f8-179">Execute the select statement again to verify that the `Samples.IDLabel` sequence restarted with number 1.</span></span>  
  
```  
SELECT NEXT VALUE FOR Samples.IDLabel OVER (ORDER BY Name) AS NutID, ProductID, Name, ProductNumber FROM Production.Product  
WHERE Name LIKE '%nut%' ;  
```  
  
### <a name="g-changing-a-table-from-identity-to-sequence"></a><span data-ttu-id="764f8-180">G.</span><span class="sxs-lookup"><span data-stu-id="764f8-180">G.</span></span> <span data-ttu-id="764f8-181">ID에서 시퀀스로 테이블 변경</span><span class="sxs-lookup"><span data-stu-id="764f8-181">Changing a table from identity to sequence</span></span>  
 <span data-ttu-id="764f8-182">다음 예에서는 스키마 한 개와 행을 세 개 포함하는 테이블 한 개를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="764f8-182">The following example creates a schema and table containing three rows for the example.</span></span> <span data-ttu-id="764f8-183">그런 다음 새 열을 추가하고 이전 열을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="764f8-183">Then the example adds a new column and drops the old column.</span></span>  
  
```  
-- Create a schema  
CREATE SCHEMA Test ;  
GO  
  
-- Create a table  
CREATE TABLE Test.Department  
    (  
        DepartmentID smallint IDENTITY(1,1) NOT NULL,  
        Name nvarchar(100) NOT NULL,  
        GroupName nvarchar(100) NOT NULL  
    CONSTRAINT PK_Department_DepartmentID PRIMARY KEY CLUSTERED   
         (DepartmentID ASC)   
    ) ;  
GO  
  
-- Insert three rows into the table  
INSERT Test.Department(Name, GroupName)  
    VALUES ('Engineering', 'Research and Development');  
GO  
  
INSERT Test.Department(Name, GroupName)  
    VALUES ('Tool Design', 'Research and Development');  
GO  
  
INSERT Test.Department(Name, GroupName)  
    VALUES ('Sales', 'Sales and Marketing');  
GO  
  
-- View the table that will be changed  
SELECT * FROM Test.Department ;  
GO  
  
-- End of portion creating a sample table  
--------------------------------------------------------  
-- Add the new column that does not have the IDENTITY property  
ALTER TABLE Test.Department   
    ADD DepartmentIDNew smallint NULL  
GO  
  
-- Copy values from the old column to the new column  
UPDATE Test.Department  
    SET DepartmentIDNew = DepartmentID ;  
GO  
  
-- Drop the primary key constraint on the old column  
ALTER TABLE Test.Department  
    DROP CONSTRAINT [PK_Department_DepartmentID];  
-- Drop the old column  
ALTER TABLE Test.Department  
    DROP COLUMN DepartmentID ;  
GO  
  
-- Rename the new column to the old columns name  
EXEC sp_rename 'Test.Department.DepartmentIDNew',   
    'DepartmentID', 'COLUMN';  
GO  
  
-- Change the new column to NOT NULL  
ALTER TABLE Test.Department  
    ALTER COLUMN DepartmentID smallint NOT NULL ;  
-- Add the unique primary key constraint  
ALTER TABLE Test.Department  
    ADD CONSTRAINT PK_Department_DepartmentID PRIMARY KEY CLUSTERED   
         (DepartmentID ASC) ;  
-- Get the highest current value from the DepartmentID column   
-- and create a sequence to use with the column. (Returns 3.)  
SELECT MAX(DepartmentID) FROM Test.Department ;  
-- Use the next desired value (4) as the START WITH VALUE;  
CREATE SEQUENCE Test.DeptSeq  
    AS smallint  
    START WITH 4  
    INCREMENT BY 1 ;  
GO  
  
-- Add a default value for the DepartmentID column  
ALTER TABLE Test.Department  
    ADD CONSTRAINT DefSequence DEFAULT (NEXT VALUE FOR Test.DeptSeq)   
        FOR DepartmentID;  
GO  
  
-- View the result  
SELECT DepartmentID, Name, GroupName  
FROM Test.Department ;   
-- Test insert  
INSERT Test.Department (Name, GroupName)  
    VALUES ('Audit', 'Quality Assurance') ;  
GO  
  
-- View the result  
SELECT DepartmentID, Name, GroupName  
FROM Test.Department ;  
GO  
  
```  
  
 <span data-ttu-id="764f8-184">`SELECT *`를 사용하는 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 문은 새 열을 첫 번째 열이 아니라 마지막 열로 받습니다.</span><span class="sxs-lookup"><span data-stu-id="764f8-184">[!INCLUDE[tsql](../../../includes/tsql-md.md)] statements that use `SELECT *` will receive the new column as the last column instead of the first column.</span></span> <span data-ttu-id="764f8-185">이렇게 되지 않도록 하려면 완전히 새로운 테이블을 만들고 데이터를 이 테이블로 이동한 다음 새 테이블에서 사용 권한을 다시 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="764f8-185">If this is not acceptable, then you must create an entirely new table, move the data to it, and then recreate the permissions on the new table.</span></span>  
  
## <a name="related-content"></a><span data-ttu-id="764f8-186">관련 내용</span><span class="sxs-lookup"><span data-stu-id="764f8-186">Related Content</span></span>  
 [<span data-ttu-id="764f8-187">CREATE SEQUENCE&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="764f8-187">CREATE SEQUENCE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-sequence-transact-sql)  
  
 [<span data-ttu-id="764f8-188">ALTER SEQUENCE&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="764f8-188">ALTER SEQUENCE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-sequence-transact-sql)  
  
 [<span data-ttu-id="764f8-189">DROP SEQUENCE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="764f8-189">DROP SEQUENCE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/drop-sequence-transact-sql)  
  
 [<span data-ttu-id="764f8-190">IDENTITY&#40;속성&#41;&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="764f8-190">IDENTITY &#40;Property&#41; &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-table-transact-sql-identity-property)  
  
  
