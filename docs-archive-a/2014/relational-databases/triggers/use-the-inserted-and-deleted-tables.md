---
title: inserted 및 deleted 테이블 사용 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- inserted tables
- UPDATE statement [SQL Server], DML triggers
- DELETE statement [SQL Server], DML triggers
- INSTEAD OF triggers
- deleted tables
- INSERT statement [SQL Server], DML triggers
- DML triggers, deleted or inserted tables
ms.assetid: ed84567f-7b91-4b44-b5b2-c400bda4590d
author: rothja
ms.author: jroth
ms.openlocfilehash: facc534177113bd93e56e50fca3ae14c3e6b2cfc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660379"
---
# <a name="use-the-inserted-and-deleted-tables"></a><span data-ttu-id="8d37e-102">inserted 및 deleted 테이블 사용</span><span class="sxs-lookup"><span data-stu-id="8d37e-102">Use the inserted and deleted Tables</span></span>
  <span data-ttu-id="8d37e-103">DML 트리거 문은 두 개의 특수 테이블(inserted 및 deleted 테이블)을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="8d37e-103">DML trigger statements use two special tables: the deleted table and the inserted tables.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="8d37e-104">에서는 이러한 테이블을 자동으로 만들고 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="8d37e-104">automatically creates and manages these tables.</span></span> <span data-ttu-id="8d37e-105">메모리에 상주하는 이러한 임시 테이블을 사용하여 특정 데이터의 수정 결과를 테스트하고 DML 트리거 동작에 대한 조건을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8d37e-105">You can use these temporary, memory-resident tables to test the effects of certain data modifications and to set conditions for DML trigger actions.</span></span> <span data-ttu-id="8d37e-106">이 테이블에서 데이터를 직접 수정하거나 CREATE INDEX와 같은 DDL(데이터 정의 언어) 작업을 수행할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8d37e-106">You cannot directly modify the data in the tables or perform data definition language (DDL) operations on the tables, such as CREATE INDEX.</span></span>  
  
 <span data-ttu-id="8d37e-107">DML 트리거에서 inserted 및 deleted 테이블은 주로 다음 작업을 수행하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="8d37e-107">In DML triggers, the inserted and deleted tables are primarily used to perform the following:</span></span>  
  
-   <span data-ttu-id="8d37e-108">테이블 간 참조 무결성을 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="8d37e-108">Extend referential integrity between tables.</span></span>  
  
-   <span data-ttu-id="8d37e-109">뷰를 원본으로 사용하는 기본 테이블에 데이터를 삽입하거나 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="8d37e-109">Insert or update data in base tables underlying a view.</span></span>  
  
-   <span data-ttu-id="8d37e-110">오류가 있는지 테스트하고 오류에 따른 적절한 동작을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="8d37e-110">Test for errors and take action based on the error.</span></span>  
  
-   <span data-ttu-id="8d37e-111">데이터를 수정하기 전과 후의 테이블 상태 차이를 찾고 이 차이에 따라 동작을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="8d37e-111">Find the difference between the state of a table before and after a data modification and take actions based on that difference.</span></span>  
  
 <span data-ttu-id="8d37e-112">deleted 테이블에는 DELETE 및 UPDATE 문을 실행할 때 영향을 받는 행의 복사본이 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="8d37e-112">The deleted table stores copies of the affected rows during DELETE and UPDATE statements.</span></span> <span data-ttu-id="8d37e-113">DELETE 또는 UPDATE 문을 실행하는 동안 트리거 테이블에서 행이 삭제되어 deleted 테이블로 이동됩니다.</span><span class="sxs-lookup"><span data-stu-id="8d37e-113">During the execution of a DELETE or UPDATE statement, rows are deleted from the trigger table and transferred to the deleted table.</span></span> <span data-ttu-id="8d37e-114">deleted 테이블과 트리거 테이블은 보통 서로 공통되는 행이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8d37e-114">The deleted table and the trigger table ordinarily have no rows in common.</span></span>  
  
 <span data-ttu-id="8d37e-115">inserted 테이블에는 INSERT 및 UPDATE 문을 실행할 때 영향을 받는 행의 복사본이 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="8d37e-115">The inserted table stores copies of the affected rows during INSERT and UPDATE statements.</span></span> <span data-ttu-id="8d37e-116">삽입 또는 업데이트 트랜잭션 동안 새 행은 inserted 테이블과 트리거 테이블에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="8d37e-116">During an insert or update transaction, new rows are added to both the inserted table and the trigger table.</span></span> <span data-ttu-id="8d37e-117">inserted 테이블의 행은 트리거 테이블에 있는 새 행의 복사본입니다.</span><span class="sxs-lookup"><span data-stu-id="8d37e-117">The rows in the inserted table are copies of the new rows in the trigger table.</span></span>  
  
 <span data-ttu-id="8d37e-118">업데이트 트랜잭션은 삭제 작업과 삽입 작업을 차례로 수행하는 것과 비슷합니다. 즉 이전 행이 먼저 deleted 테이블로 복사된 다음 새 행이 트리거 테이블과 inserted 테이블로 복사됩니다.</span><span class="sxs-lookup"><span data-stu-id="8d37e-118">An update transaction is similar to a delete operation followed by an insert operation; the old rows are copied to the deleted table first, and then the new rows are copied to the trigger table and to the inserted table.</span></span>  
  
 <span data-ttu-id="8d37e-119">트리거 조건을 설정할 때는 트리거를 실행한 동작에 적합한 inserted 및 deleted 테이블을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="8d37e-119">When you set trigger conditions, use the inserted and deleted tables appropriately for the action that fired the trigger.</span></span> <span data-ttu-id="8d37e-120">INSERT를 테스트할 때 deleted 테이블을 참조하거나 DELETE를 테스트할 때 inserted 테이블을 참조해도 오류가 발생하지는 않지만 이러한 경우 트리거 테스트 테이블에는 아무 행도 들어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8d37e-120">Although referencing the deleted table when testing an INSERT or the inserted table when testing a DELETE does not cause any errors, these trigger test tables do not contain any rows in these cases.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8d37e-121">트리거 동작이 데이터 수정의 영향을 받는 행의 수에 따라 달라지는 경우 여러 행 데이터 수정(SELECT 문을 기반으로 하는 INSERT, DELETE 또는 UPDATE)에 @@ROWCOUNT 검사 같은 테스트를 사용하고 적합한 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="8d37e-121">If trigger actions depend on the number of rows a data modification effects, use tests (such as an examination of @@ROWCOUNT) for multirow data modifications (an INSERT, DELETE, or UPDATE based on a SELECT statement), and take appropriate actions.</span></span>  
  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<span data-ttu-id="8d37e-122">에서는 inserted 및 deleted 테이블에서 AFTER 트리거에 대한 `text`, `ntext` 또는 `image` 열 참조를 허용하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8d37e-122">does not allow for `text`, `ntext`, or `image` column references in the inserted and deleted tables for AFTER triggers.</span></span> <span data-ttu-id="8d37e-123">하지만 이러한 데이터 형식은 단지 이전 버전과의 호환성을 위해 포함된 것입니다.</span><span class="sxs-lookup"><span data-stu-id="8d37e-123">However, these data types are included for backward compatibility purposes only.</span></span> <span data-ttu-id="8d37e-124">큰 데이터를 스토리지하는 경우 `varchar(max)`, `nvarchar(max)` 및 `varbinary(max)` 데이터 형식을 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="8d37e-124">The preferred storage for large data is to use the `varchar(max)`, `nvarchar(max)`, and `varbinary(max)` data types.</span></span> <span data-ttu-id="8d37e-125">AFTER 및 INSTEAD OF 트리거는 모두 inserted 및 deleted 테이블에서 `varchar(max)`, `nvarchar(max)` 및 `varbinary(max)` 데이터를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="8d37e-125">Both AFTER and INSTEAD OF triggers support `varchar(max)`, `nvarchar(max)`, and `varbinary(max)` data in the inserted and deleted tables.</span></span> <span data-ttu-id="8d37e-126">자세한 내용은 [CREATE TRIGGER&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-trigger-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8d37e-126">For more information, see [CREATE TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-trigger-transact-sql).</span></span>  
  
 <span data-ttu-id="8d37e-127">**비즈니스 규칙을 적용하기 위해 트리거의 inserted 테이블을 사용하는 예**</span><span class="sxs-lookup"><span data-stu-id="8d37e-127">**An Example of Using the inserted Table in a Trigger to Enforce Business Rules**</span></span>  
  
 <span data-ttu-id="8d37e-128">CHECK 제약 조건은 열 수준 또는 테이블 수준 제약 조건이 정의된 열만 참조할 수 있으므로 모든 상호 테이블 제약 조건(이 경우 업무 규칙)을 트리거로 정의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8d37e-128">Because CHECK constraints can reference only the columns on which the column-level or table-level constraint is defined, any cross-table constraints (in this case, business rules) must be defined as triggers.</span></span>  
  
 <span data-ttu-id="8d37e-129">다음 예에서는 DML 트리거를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="8d37e-129">The following example creates a DML trigger.</span></span> <span data-ttu-id="8d37e-130">이 트리거는 `PurchaseOrderHeader` 테이블에 새 구매 주문을 삽입하려고 할 때 공급업체의 신용 등급이 양호한지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="8d37e-130">This trigger checks to make sure the credit rating for the vendor is good when an attempt is made to insert a new purchase order into the `PurchaseOrderHeader` table.</span></span> <span data-ttu-id="8d37e-131">방금 삽입된 구매 주문에 해당하는 공급업체의 신용 등급을 가져오려면 `Vendor` 테이블이 참조되어 inserted 테이블과 조인되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8d37e-131">To obtain the credit rating of the vendor corresponding to the purchase order that was just inserted, the `Vendor` table must be referenced and joined with the inserted table.</span></span> <span data-ttu-id="8d37e-132">신용 등급이 너무 낮으면 메시지가 표시되고 삽입이 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8d37e-132">If the credit rating is too low, a message is displayed and the insertion does not execute.</span></span> <span data-ttu-id="8d37e-133">이 예에서는 다중 행 데이터 수정을 허용하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8d37e-133">Note that this example does not allow for multirow data modifications.</span></span> <span data-ttu-id="8d37e-134">자세한 내용은 [Create DML Triggers to Handle Multiple Rows of Data](../triggers/create-dml-triggers-to-handle-multiple-rows-of-data.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8d37e-134">For more information, see [Create DML Triggers to Handle Multiple Rows of Data](../triggers/create-dml-triggers-to-handle-multiple-rows-of-data.md).</span></span>  
  
 [!code-sql[TriggerDDL#CreateTrigger3](../../snippets/tsql/SQL14/tsql/triggerddl/transact-sql/snippet_create_alter_drop_trigger.sql#createtrigger3)]  
  
## <a name="using-the-inserted-and-deleted-tables-in-instead-of-triggers"></a><span data-ttu-id="8d37e-135">INSTEAD OF 트리거에서 inserted 및 deleted 테이블 사용</span><span class="sxs-lookup"><span data-stu-id="8d37e-135">Using the inserted and deleted Tables in INSTEAD OF Triggers</span></span>  
 <span data-ttu-id="8d37e-136">테이블에 정의된 INSTEAD OF 트리거로 전달되는 inserted 및 deleted 테이블은 AFTER 트리거로 전달되는inserted 및 deleted 테이블과 같은 규칙을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="8d37e-136">The inserted and deleted tables passed to INSTEAD OF triggers defined on tables follow the same rules as the inserted and deleted tables passed to AFTER triggers.</span></span> <span data-ttu-id="8d37e-137">inserted 및 deleted 테이블의 형식은 INSTEAD OF 트리거가 정의된 테이블의 형식과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="8d37e-137">The format of the inserted and deleted tables is the same as the format of the table on which the INSTEAD OF trigger is defined.</span></span> <span data-ttu-id="8d37e-138">inserted 및 deleted 테이블의 각 열은 기본 테이블의 열로 직접 매핑됩니다.</span><span class="sxs-lookup"><span data-stu-id="8d37e-138">Each column in the inserted and deleted tables maps directly to a column in the base table.</span></span>  
  
 <span data-ttu-id="8d37e-139">INSTEAD OF 트리거가 있는 테이블을 참조하는 INSERT 또는 UPDATE 문이 열 값을 제공해야 하는 경우와 관련된 다음 규칙은 테이블에 INSTEAD OF 트리거가 없는 경우와 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="8d37e-139">The following rules regarding when an INSERT or UPDATE statement referencing a table with an INSTEAD OF trigger must supply values for columns are the same as if the table did not have an INSTEAD OF trigger:</span></span>  
  
-   <span data-ttu-id="8d37e-140">계산 열이나 `timestamp` 데이터 형식의 열에는 값을 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8d37e-140">Values cannot be specified for computed columns or columns with a `timestamp` data type.</span></span>  
  
-   <span data-ttu-id="8d37e-141">해당 테이블에 대해 IDENTITY_INSERT가 ON으로 설정되어 있지 않으면 IDENTITY 속성이 있는 열에 값을 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8d37e-141">Values cannot be specified for columns with an IDENTITY property, unless IDENTITY_INSERT is ON for that table.</span></span> <span data-ttu-id="8d37e-142">IDENTITY_INSERT가 ON이면 INSERT 문이 값을 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8d37e-142">When IDENTITY_INSERT is ON, INSERT statements must supply a value.</span></span>  
  
-   <span data-ttu-id="8d37e-143">INSERT 문은 DEFAULT 제약 조건이 없는 모든 NOT NULL 열에 값을 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8d37e-143">INSERT statements must supply values for all NOT NULL columns that do not have DEFAULT constraints.</span></span>  
  
-   <span data-ttu-id="8d37e-144">계산 열, ID 열 또는 `timestamp` 열을 제외한 모든 열에서 Null을 허용하는 열 또는 DEFAULT 정의가 있는 NOT NULL 열의 경우 값이 선택적입니다.</span><span class="sxs-lookup"><span data-stu-id="8d37e-144">For any columns except computed, identity, or `timestamp` columns, values are optional for any column that allows nulls, or any NOT NULL column that has a DEFAULT definition.</span></span>  
  
 <span data-ttu-id="8d37e-145">INSERT, UPDATE 또는 DELETE 문에서 INSTEAD OF 트리거가 있는 뷰를 참조할 때 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 은 테이블에 대해 직접 동작을 수행하는 대신 트리거를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="8d37e-145">When an INSERT, UPDATE, or DELETE statement references a view that has an INSTEAD OF trigger, the [!INCLUDE[ssDE](../../includes/ssde-md.md)] calls the trigger instead of taking any direct action against any table.</span></span> <span data-ttu-id="8d37e-146">뷰에 대해 작성된 inserted 및 deleted 테이블의 정보 형식이 기본 테이블에 있는 데이터 형식과 다른 경우에도 트리거는 inserted 및 deleted 테이블에 있는 정보를 사용하여 기본 테이블에서 요청된 동작을 구현하는 데 필요한 문을 작성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8d37e-146">The trigger must use the information presented in the inserted and deleted tables to build any statements required to implement the requested action in the base tables, even when the format of the information in the inserted and deleted tables built for the view is different from the format of the data in the base tables.</span></span>  
  
 <span data-ttu-id="8d37e-147">뷰에 정의된 INSTEAD OF 트리거로 전달되는 inserted 및 deleted 테이블의 형식은 뷰에 대해 정의된 SELECT 문의 선택 목록과 일치합니다.</span><span class="sxs-lookup"><span data-stu-id="8d37e-147">The format of the inserted and deleted tables passed to an INSTEAD OF trigger defined on a view matches the select list of the SELECT statement defined for the view.</span></span> <span data-ttu-id="8d37e-148">다음은 그 예입니다. </span><span class="sxs-lookup"><span data-stu-id="8d37e-148">For example:</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
CREATE VIEW dbo.EmployeeNames (BusinessEntityID, LName, FName)  
AS  
SELECT e.BusinessEntityID, p.LastName, p.FirstName  
FROM HumanResources.Employee AS e   
JOIN Person.Person AS p  
ON e.BusinessEntityID = p.BusinessEntityID;  
```  
  
 <span data-ttu-id="8d37e-149">이 뷰의 결과 집합에는 `int` 열 하나와 `nvarchar` 열 두 개가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8d37e-149">The result set for this view has three columns: an `int` column and two `nvarchar` columns.</span></span> <span data-ttu-id="8d37e-150">뷰에 정의된 INSTEAD OF 트리거로 전달되는 inserted 및 deleted 테이블에는 또한 `BusinessEntityID`라는 `int` 열, `LName`이라는 `nvarchar` 열 및 `FName`이라는 `nvarchar` 열이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8d37e-150">The inserted and deleted tables passed to an INSTEAD OF trigger defined on the view also have an `int` column named `BusinessEntityID`, an `nvarchar` column named `LName`, and an `nvarchar` column named `FName`.</span></span>  
  
 <span data-ttu-id="8d37e-151">뷰의 선택 목록에는 단일 기본 테이블 열에 직접 매핑되지 않는 식이 포함될 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8d37e-151">The select list of a view can also contain expressions that do not directly map to a single base-table column.</span></span> <span data-ttu-id="8d37e-152">상수 또는 함수 호출과 같은 일부 뷰 식은 열을 참조하지 않으므로 무시될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8d37e-152">Some view expressions, such as a constant or function invocation, may not reference any columns and can be ignored.</span></span> <span data-ttu-id="8d37e-153">복합 식은 여러 개의 열을 참조할 수 있지만 inserted 및 deleted 테이블에는 삽입된 각 행에 대해 하나의 값만 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8d37e-153">Complex expressions can reference multiple columns, yet the inserted and deleted tables have only one value for each inserted row.</span></span> <span data-ttu-id="8d37e-154">뷰의 단순 식에서 복합 식이 있는 계산 열을 참조하는 경우에도 마찬가지입니다.</span><span class="sxs-lookup"><span data-stu-id="8d37e-154">The same issues apply to simple expressions in a view if they reference a computed column that has a complex expression.</span></span> <span data-ttu-id="8d37e-155">뷰의 INSTEAD OF 트리거는 이러한 유형의 식을 처리해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8d37e-155">An INSTEAD OF trigger on the view must handle these types of expressions.</span></span>  
  
  
