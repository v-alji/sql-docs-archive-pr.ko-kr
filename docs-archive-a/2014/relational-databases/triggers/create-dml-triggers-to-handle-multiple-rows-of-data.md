---
title: 여러 행의 데이터를 처리하기 위한 DML 트리거 만들기 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- multiple row DML triggers
- UPDATE statement [SQL Server], DML triggers
- DELETE statement [SQL Server], DML triggers
- multirow DML triggers [SQL Server]
- INSERT statement [SQL Server], DML triggers
- DML triggers, multirow
ms.assetid: d476c124-596b-4b27-a883-812b6b50a735
author: rothja
ms.author: jroth
ms.openlocfilehash: 11ea7aa457a5cdfcafd4a8c4e0ac170ae0e3b9c2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660408"
---
# <a name="create-dml-triggers-to-handle-multiple-rows-of-data"></a><span data-ttu-id="6a657-102">여러 행의 데이터를 처리하기 위한 DML 트리거 만들기</span><span class="sxs-lookup"><span data-stu-id="6a657-102">Create DML Triggers to Handle Multiple Rows of Data</span></span>
  <span data-ttu-id="6a657-103">DML 트리거 코드를 작성할 때는 트리거를 실행시키는 단일 문이 여러 행의 데이터에 영향을 줄 수 있다는 점을 고려해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6a657-103">When you write the code for a DML trigger, consider that the statement that causes the trigger to fire can be a single statement that affects multiple rows of data, instead of a single row.</span></span> <span data-ttu-id="6a657-104">이 동작은 여러 행에 영향을 줄 수 있는 UPDATE 및 DELETE 트리거의 경우에 일반적입니다.</span><span class="sxs-lookup"><span data-stu-id="6a657-104">This behavior is common for UPDATE and DELETE triggers because these statements frequently affect multiple rows.</span></span> <span data-ttu-id="6a657-105">기본 INSERT 문은 한 행만 추가하기 때문에 INSERT 트리거의 경우에는 일반적이지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6a657-105">The behavior is less common for INSERT triggers because the basic INSERT statement adds only a single row.</span></span> <span data-ttu-id="6a657-106">그러나 INSERT INTO (*table_name*) SELECT 문으로 INSERT 트리거를 실행할 수 있기 때문에 여러 행을 삽입하는 경우 단일 트리거를 호출할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6a657-106">However, because an INSERT trigger can be fired by an INSERT INTO (*table_name*) SELECT statement, the insertion of many rows may cause a single trigger invocation.</span></span>  
  
 <span data-ttu-id="6a657-107">DML 트리거 함수가 한 테이블의 요약 값을 자동으로 다시 계산하여 계속 계산하기 위해 그 결과를 다른 테이블에 저장하는 경우 특히 다중 행을 고려해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6a657-107">Multirow considerations are especially important when the function of a DML trigger is to automatically recalculate summary values from one table and store the results in another for ongoing tallies.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6a657-108">커서는 잠재적으로 성능을 저하시킬 수 있으므로 트리거에 사용하지 않는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="6a657-108">We do not recommend using cursors in triggers because they could potentially reduce performance.</span></span> <span data-ttu-id="6a657-109">다중 행에 영향을 주는 트리거를 디자인하려면 커서 대신 행 집합 기반 논리를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="6a657-109">To design a trigger that affects multiple rows, use rowset-based logic instead of cursors.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="6a657-110">예</span><span class="sxs-lookup"><span data-stu-id="6a657-110">Examples</span></span>  
 <span data-ttu-id="6a657-111">다음 예에서 DML 트리거는 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 예제 데이터베이스의 다른 테이블에 열의 누계를 저장하도록 디자인되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6a657-111">The DML triggers in the following examples are designed to store a running total of a column in another table of the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] sample database.</span></span>  
  
### <a name="a-storing-a-running-total-for-a-single-row-insert"></a><span data-ttu-id="6a657-112">A.</span><span class="sxs-lookup"><span data-stu-id="6a657-112">A.</span></span> <span data-ttu-id="6a657-113">단일 행 삽입의 누계 저장</span><span class="sxs-lookup"><span data-stu-id="6a657-113">Storing a running total for a single-row insert</span></span>  
 <span data-ttu-id="6a657-114">`PurchaseOrderDetail` 테이블에 데이터 행 하나를 로드하는 경우 첫 번째 버전의 DML 트리거는 단일 행 삽입에 대해 제대로 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="6a657-114">The first version of the DML trigger works well for a single-row insert when a row of data is loaded into the `PurchaseOrderDetail` table.</span></span> <span data-ttu-id="6a657-115">INSERT 문이 DML 트리거를 시작하면 트리거가 실행되는 동안 새 행이 **inserted** 테이블에 로드됩니다.</span><span class="sxs-lookup"><span data-stu-id="6a657-115">An INSERT statement fires the DML trigger, and the new row is loaded into the **inserted** table for the duration of the trigger execution.</span></span> <span data-ttu-id="6a657-116">`UPDATE` 문에서는 추가된 행의 `LineTotal` 열 값을 읽어 `SubTotal` 테이블에 있는 `PurchaseOrderHeader` 열의 기존 값에 더합니다.</span><span class="sxs-lookup"><span data-stu-id="6a657-116">The `UPDATE` statement reads the `LineTotal` column value for the row and adds that value to the existing value in the `SubTotal` column in the `PurchaseOrderHeader` table.</span></span> <span data-ttu-id="6a657-117">`WHERE` 절은 `PurchaseOrderDetail` 테이블에 있는 업데이트된 행이 `PurchaseOrderID` inserted **테이블에 있는** 행과 일치하는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="6a657-117">The `WHERE` clause makes sure that the updated row in the `PurchaseOrderDetail` table matches the `PurchaseOrderID` of the row in the **inserted** table.</span></span>  
  
```  
-- Trigger is valid for single-row inserts.  
USE AdventureWorks2012;  
GO  
CREATE TRIGGER NewPODetail  
ON Purchasing.PurchaseOrderDetail  
AFTER INSERT AS  
   UPDATE PurchaseOrderHeader  
   SET SubTotal = SubTotal + LineTotal  
   FROM inserted  
   WHERE PurchaseOrderHeader.PurchaseOrderID = inserted.PurchaseOrderID ;  
```  
  
### <a name="b-storing-a-running-total-for-a-multirow-or-single-row-insert"></a><span data-ttu-id="6a657-118">B.</span><span class="sxs-lookup"><span data-stu-id="6a657-118">B.</span></span> <span data-ttu-id="6a657-119">다중 행 또는 단일 행 삽입에 대한 누계 저장</span><span class="sxs-lookup"><span data-stu-id="6a657-119">Storing a running total for a multirow or single-row insert</span></span>  
 <span data-ttu-id="6a657-120">다중 행을 삽입하는 경우에는 예 1의 DML 트리거가 제대로 실행되지 않을 수 있습니다. UPDATE 문에 있는 대입 식의 오른쪽 식(`SubTotal` + `LineTotal`)은 여러 값이 아니라 한 값만 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6a657-120">For a multirow insert, the DML trigger in example A might not operate correctly; the expression to the right of an assignment expression in an UPDATE statement (`SubTotal` + `LineTotal`) can be only a single value, not a list of values.</span></span> <span data-ttu-id="6a657-121">따라서 트리거의 결과로 **inserted** 테이블의 단일 행에서 값을 검색하여 이 값을 특정 `SubTotal` 값에 대한 `PurchaseOrderHeader` 테이블의 기존 `PurchaseOrderID` 값에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="6a657-121">Therefore, the effect of the trigger is to retrieve a value from any single row in the **inserted** table and add that value to the existing `SubTotal` value in the `PurchaseOrderHeader` table for a specific `PurchaseOrderID` value.</span></span> <span data-ttu-id="6a657-122">이 작업에서 `PurchaseOrderID` inserted **테이블에 단일** 값이 두 번 이상 나타난 경우 예상한 결과가 나오지 않을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6a657-122">This operation might not have the expected effect if a single `PurchaseOrderID` value occurred more than one time in the **inserted** table.</span></span>  
  
 <span data-ttu-id="6a657-123">`PurchaseOrderHeader` 테이블을 올바르게 업데이트하려면 트리거가 **inserted** 테이블에 있는 다중 행을 변경할 수 있도록 허용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6a657-123">To correctly update the `PurchaseOrderHeader` table, the trigger must allow for the chance of multiple rows in the **inserted** table.</span></span> <span data-ttu-id="6a657-124">이 작업은 각 `SUM` 에 대해 `LineTotal` inserted **테이블에 있는 행 그룹의 전체** 을 계산하는 `PurchaseOrderID`함수를 사용하여 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6a657-124">You can do this by using the `SUM` function that calculates the total `LineTotal` for a group of rows in the **inserted** table for each `PurchaseOrderID`.</span></span> <span data-ttu-id="6a657-125">`SUM` 함수는 상호 관련된 하위 쿼리(괄호 안에 있는 `SELECT` 문)에 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6a657-125">The `SUM` function is included in a correlated subquery (the `SELECT` statement in parentheses).</span></span> <span data-ttu-id="6a657-126">이 하위 쿼리는 `PurchaseOrderID` 테이블의 **와 일치하거나 상호 관련된** inserted `PurchaseOrderID` 테이블의 각 `PurchaseOrderHeader` 에 대해 단일 값을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="6a657-126">This subquery returns a single value for each `PurchaseOrderID` in the **inserted** table that matches or is correlated with a `PurchaseOrderID` in the `PurchaseOrderHeader` table.</span></span>  
  
```  
-- Trigger is valid for multirow and single-row inserts.  
USE AdventureWorks2012;  
GO  
CREATE TRIGGER NewPODetail2  
ON Purchasing.PurchaseOrderDetail  
AFTER INSERT AS  
   UPDATE Purchasing.PurchaseOrderHeader  
   SET SubTotal = SubTotal +   
      (SELECT SUM(LineTotal)  
      FROM inserted  
      WHERE PurchaseOrderHeader.PurchaseOrderID  
       = inserted.PurchaseOrderID)  
   WHERE PurchaseOrderHeader.PurchaseOrderID IN  
      (SELECT PurchaseOrderID FROM inserted);  
```  
  
 <span data-ttu-id="6a657-127">`LineTotal` 값 열의 합계가 단일 행의 합계와 같기 때문에 이 트리거는 단일 행만 삽입할 때도 제대로 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="6a657-127">This trigger also works correctly in a single-row insert; the sum of the `LineTotal` value column is the sum of a single row.</span></span> <span data-ttu-id="6a657-128">그러나 이 트리거를 사용하면 상호 관련된 하위 쿼리 및 `IN` 절에서 사용되는 `WHERE` 연산자에 대해 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 추가 처리 작업이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="6a657-128">However, with this trigger the correlated subquery and the `IN` operator that is used in the `WHERE` clause require additional processing from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="6a657-129">단일 행 삽입에는 이 작업이 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6a657-129">This is unnecessary for a single-row insert.</span></span>  
  
### <a name="c-storing-a-running-total-based-on-the-type-of-insert"></a><span data-ttu-id="6a657-130">C.</span><span class="sxs-lookup"><span data-stu-id="6a657-130">C.</span></span> <span data-ttu-id="6a657-131">삽입 유형에 따른 누계 저장</span><span class="sxs-lookup"><span data-stu-id="6a657-131">Storing a running total based on the type of insert</span></span>  
 <span data-ttu-id="6a657-132">트리거를 변경하여 행 수에 맞는 최적의 방법을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6a657-132">You can change the trigger to use the method optimal for the number of rows.</span></span> <span data-ttu-id="6a657-133">예를 들어 트리거 논리에서 `@@ROWCOUNT` 함수를 사용하여 단일 행 삽입과 다중 행 삽입을 구별할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6a657-133">For example, the `@@ROWCOUNT` function can be used in the logic of the trigger to distinguish between a single and a multirow insert.</span></span>  
  
```  
-- Trigger valid for multirow and single row inserts  
-- and optimal for single row inserts.  
USE AdventureWorks2012;  
GO  
CREATE TRIGGER NewPODetail3  
ON Purchasing.PurchaseOrderDetail  
FOR INSERT AS  
IF @@ROWCOUNT = 1  
BEGIN  
   UPDATE Purchasing.PurchaseOrderHeader  
   SET SubTotal = SubTotal + LineTotal  
   FROM inserted  
   WHERE PurchaseOrderHeader.PurchaseOrderID = inserted.PurchaseOrderID  
END  
ELSE  
BEGIN  
      UPDATE Purchasing.PurchaseOrderHeader  
   SET SubTotal = SubTotal +   
      (SELECT SUM(LineTotal)  
      FROM inserted  
      WHERE PurchaseOrderHeader.PurchaseOrderID  
       = inserted.PurchaseOrderID)  
   WHERE PurchaseOrderHeader.PurchaseOrderID IN  
      (SELECT PurchaseOrderID FROM inserted)  
END;  
```  
  
## <a name="see-also"></a><span data-ttu-id="6a657-134">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6a657-134">See Also</span></span>  
 [<span data-ttu-id="6a657-135">DML 트리거</span><span class="sxs-lookup"><span data-stu-id="6a657-135">DML Triggers</span></span>](dml-triggers.md)  
  
  
