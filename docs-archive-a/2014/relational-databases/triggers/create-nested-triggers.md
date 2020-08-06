---
title: 중첩 트리거 만들기 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- recursive DML triggers [SQL Server]
- DML triggers, nested
- triggers [SQL Server], nested
- direct recursion [SQL Server]
- triggers [SQL Server], recursive
- DML triggers, recursive
- RECURSIVE_TRIGGERS option
- indirect recursion [SQL Server]
- nested DML triggers
ms.assetid: cd522dda-b4ab-41b8-82b0-02445bdba7af
author: rothja
ms.author: jroth
ms.openlocfilehash: c0016fc3cdd93ea78ceed56efa076a01bd85be50
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660405"
---
# <a name="create-nested-triggers"></a><span data-ttu-id="f03d9-102">중첩 트리거 만들기</span><span class="sxs-lookup"><span data-stu-id="f03d9-102">Create Nested Triggers</span></span>
  <span data-ttu-id="f03d9-103">DML 및 DDL 트리거는 트리거가 다른 트리거를 시작하는 동작을 수행할 때 둘 다 중첩됩니다.</span><span class="sxs-lookup"><span data-stu-id="f03d9-103">Both DML and DDL triggers are nested when a trigger performs an action that initiates another trigger.</span></span> <span data-ttu-id="f03d9-104">이러한 동작이 다른 트리거를 시작할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f03d9-104">These actions can initiate other triggers, and so on.</span></span> <span data-ttu-id="f03d9-105">DML 및 DDL 트리거는 최대 32 수준까지 중첩될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f03d9-105">DML and DDL triggers can be nested up to 32 levels.</span></span> <span data-ttu-id="f03d9-106">**nested triggers** 서버 구성 옵션을 통해 AFTER 트리거를 중첩할 수 있는지를 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f03d9-106">You can control whether AFTER triggers can be nested through the **nested triggers** server configuration option.</span></span> <span data-ttu-id="f03d9-107">INSTEAD OF 트리거(DML 트리거만 INSTEAD OF 트리거가 될 수 있음)는 이 설정에 관계없이 중첩될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f03d9-107">INSTEAD OF triggers (only DML triggers can be INSTEAD OF triggers) can be nested regardless of this setting.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f03d9-108">[!INCLUDE[tsql](../../includes/tsql-md.md)] 트리거에서 관리 코드로의 참조는 32 수준 중첩 제한에서 한 수준으로 계산됩니다.</span><span class="sxs-lookup"><span data-stu-id="f03d9-108">Any reference to managed code from a [!INCLUDE[tsql](../../includes/tsql-md.md)] trigger counts as one level against the 32-level nesting limit.</span></span> <span data-ttu-id="f03d9-109">관리 코드 내에서 호출된 메서드는 이 제한에 따라 계산되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f03d9-109">Methods invoked from within managed code do not count against this limit.</span></span>  
  
 <span data-ttu-id="f03d9-110">중첩 트리거가 허용되고 체인에 있는 한 트리거가 무한 루프를 시작하면 중첩 수준을 초과하기 때문에 트리거가 종료됩니다.</span><span class="sxs-lookup"><span data-stu-id="f03d9-110">If nested triggers are allowed and a trigger in the chain starts an infinite loop, the nesting level is exceeded and the trigger terminates.</span></span>  
  
 <span data-ttu-id="f03d9-111">중첩 트리거를 사용하여 이전 트리거의 영향을 받는 행의 백업 복사본을 저장하는 등의 유용한 정리 작업 기능을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f03d9-111">You can use nested triggers to perform useful housekeeping functions such as storing a backup copy of rows affected by a previous trigger.</span></span> <span data-ttu-id="f03d9-112">예를 들어 `PurchaseOrderDetail` 트리거가 삭제한 `PurchaseOrderDetail` 행의 백업 복사본을 저장하는 트리거를 `delcascadetrig` 에 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f03d9-112">For example, you can create a trigger on `PurchaseOrderDetail` that saves a backup copy of the `PurchaseOrderDetail` rows that the `delcascadetrig` trigger deleted.</span></span> <span data-ttu-id="f03d9-113">`delcascadetrig` 트리거가 적용 중일 때 `PurchaseOrderID` 에서 `PurchaseOrderHeader` 1965를 삭제하면 `PurchaseOrderDetail`에서 해당 행이 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="f03d9-113">With the `delcascadetrig` trigger in effect, deleting `PurchaseOrderID` 1965 from `PurchaseOrderHeader` deletes the corresponding row or rows from `PurchaseOrderDetail`.</span></span> <span data-ttu-id="f03d9-114">삭제된 데이터를 별도로 만든 다른 테이블 `PurchaseOrderDetail` 에 저장하는 DELETE 트리거를 `del_save`에 만들면 삭제된 데이터를 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f03d9-114">To save the data, you can create a DELETE trigger on `PurchaseOrderDetail` that saves the deleted data into another separately created table, `del_save`.</span></span> <span data-ttu-id="f03d9-115">다음은 그 예입니다.</span><span class="sxs-lookup"><span data-stu-id="f03d9-115">For example:</span></span>  
  
```  
CREATE TRIGGER Purchasing.savedel  
   ON Purchasing.PurchaseOrderDetail  
FOR DELETE  
AS  
   INSERT del_save;  
   SELECT * FROM deleted;  
```  
  
 <span data-ttu-id="f03d9-116">순서가 중요한 시퀀스에는 중첩 트리거를 사용하지 않는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="f03d9-116">We do not recommend using nested triggers in an order-dependent sequence.</span></span> <span data-ttu-id="f03d9-117">관련 데이터를 모두 수정할 때는 별도의 트리거를 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="f03d9-117">Use separate triggers to cascade data modifications.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f03d9-118">트랜잭션 안에서 트리거가 실행되기 때문에 중첩 트리거의 특정 수준에서 작업이 실패하면 전체 트랜잭션이 취소되고 모든 데이터 수정 내용이 롤백됩니다.</span><span class="sxs-lookup"><span data-stu-id="f03d9-118">Because triggers execute within a transaction, a failure at any level of a set of nested triggers cancels the entire transaction, and all data modifications are rolled back.</span></span> <span data-ttu-id="f03d9-119">트리거에 PRINT 문을 포함시키면 오류가 발생한 위치를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f03d9-119">Include PRINT statements in your triggers so that you can determine where the failure has occurred.</span></span>  
  
## <a name="recursive-triggers"></a><span data-ttu-id="f03d9-120">재귀 트리거</span><span class="sxs-lookup"><span data-stu-id="f03d9-120">Recursive Triggers</span></span>  
 <span data-ttu-id="f03d9-121">RECURSIVE_TRIGGERS 데이터베이스 옵션을 설정하지 않으면 AFTER 트리거가 자신을 재귀적으로 호출하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f03d9-121">An AFTER trigger does not call itself recursively unless the RECURSIVE_TRIGGERS database option is set.</span></span>  
  
 <span data-ttu-id="f03d9-122">다음과 같은 두 가지 유형의 재귀가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f03d9-122">There are two types of recursion:</span></span>  
  
-   <span data-ttu-id="f03d9-123">직접 재귀</span><span class="sxs-lookup"><span data-stu-id="f03d9-123">Direct recursion</span></span>  
  
     <span data-ttu-id="f03d9-124">이 재귀는 트리거가 같은 트리거를 다시 시작하는 동작을 시작 및 수행할 때 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="f03d9-124">This recursion occurs when a trigger fires and performs an action that causes the same trigger to fire again.</span></span> <span data-ttu-id="f03d9-125">예를 들어 애플리케이션이 **T3**테이블을 업데이트하면 **Trig3** 트리거가 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="f03d9-125">For example, an application updates table **T3**; this causes trigger **Trig3** to fire.</span></span> <span data-ttu-id="f03d9-126">**Trig3** 은 다시 **T3** 테이블을 업데이트하고 이로 인해 **Trig3** 트리거가 다시 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="f03d9-126">**Trig3** updates table **T3** again; this causes trigger **Trig3** to fire again.</span></span>  
  
     <span data-ttu-id="f03d9-127">다른 유형(AFTER 또는 INSTEAD OF)의 트리거를 호출한 후 동일한 트리거를 다시 호출할 때도 직접 재귀가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f03d9-127">Direct recursion can also occur when the same trigger is called again, but after a trigger of a different type (AFTER or INSTEAD OF) is called.</span></span> <span data-ttu-id="f03d9-128">즉, 하나 이상의 AFTER 트리거를 중간에 호출해도 동일한 INSTEAD OF 트리거를 두 번째로 호출하면 INSTEAD OF 트리거의 직접 재귀가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f03d9-128">In other words, direct recursion of an INSTEAD OF trigger can occur when the same INSTEAD OF trigger is called for a second time, even if one or more AFTER triggers are called in between.</span></span> <span data-ttu-id="f03d9-129">마찬가지로 하나 이상의 INSTEAD OF 트리거를 중간에 호출해도 동일한 AFTER 트리거를 두 번째로 호출하면 AFTER 트리거의 직접 재귀가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f03d9-129">Likewise, direct recursion of an AFTER trigger can occur when the same AFTER trigger is called for a second time, even if one or more INSTEAD OF triggers are called in between.</span></span> <span data-ttu-id="f03d9-130">예를 들어 애플리케이션이 **T4**테이블을 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="f03d9-130">For example, an application updates table **T4**.</span></span> <span data-ttu-id="f03d9-131">이 업데이트로 인해 INSTEAD OF 트리거 **Trig4** 가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="f03d9-131">This update causes INSTEAD OF trigger **Trig4** to fire.</span></span> <span data-ttu-id="f03d9-132">**Trig4** 는 **T5**테이블을 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="f03d9-132">**Trig4** updates table **T5**.</span></span> <span data-ttu-id="f03d9-133">이 업데이트로 인해 AFTER 트리거 **Trig5** 가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="f03d9-133">This update causes AFTER trigger **Trig5** to fire.</span></span> <span data-ttu-id="f03d9-134">**Trig5** 는 **T4**테이블을 업데이트하고 이 업데이트로 인해 INSTEAD OF 트리거 **Trig4** 가 다시 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="f03d9-134">**Trig5** updates table **T4**, and this update causes INSTEAD OF trigger **Trig4** to fire again.</span></span> <span data-ttu-id="f03d9-135">이 이벤트 체인을 **Trig4**의 직접 재귀로 간주합니다.</span><span class="sxs-lookup"><span data-stu-id="f03d9-135">This chain of events is considered direct recursion for **Trig4**.</span></span>  
  
-   <span data-ttu-id="f03d9-136">간접 재귀</span><span class="sxs-lookup"><span data-stu-id="f03d9-136">Indirect recursion</span></span>  
  
     <span data-ttu-id="f03d9-137">트리거가 발생하고 같은 유형(AFTER 또는 INSTEAD OF)의 다른 트리거를 발생시키는 동작을 수행하면 이 재귀가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="f03d9-137">This recursion occurs when a trigger fires and performs an action that causes another trigger of the same type (AFTER or INSTEAD OF) to fire.</span></span> <span data-ttu-id="f03d9-138">이 두 번째 트리거는 원래 트리거를 다시 시작하는 동작을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="f03d9-138">This second trigger performs an action that causes the original trigger to fire again.</span></span> <span data-ttu-id="f03d9-139">즉, 다른 INSTEAD OF 트리거를 중간에 호출한 후 INSTEAD OF 트리거를 두 번째로 호출하면 간접 재귀가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f03d9-139">In other words, indirect recursion can occur when an INSTEAD OF trigger is called for a second time, but not until another INSTEAD OF trigger is called in between.</span></span> <span data-ttu-id="f03d9-140">마찬가지로 다른 AFTER 트리거를 중간에 호출한 후 AFTER 트리거를 두 번째로 호출하면 간접 재귀가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f03d9-140">Likewise, indirect recursion can occur when an AFTER trigger is called for a second time, but not until another AFTER trigger is called in between.</span></span> <span data-ttu-id="f03d9-141">예를 들어 애플리케이션이 **T1**테이블을 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="f03d9-141">For example, an application updates table **T1**.</span></span> <span data-ttu-id="f03d9-142">이 업데이트로 인해 AFTER 트리거 **Trig1** 이 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="f03d9-142">This update causes AFTER trigger **Trig1** to fire.</span></span> <span data-ttu-id="f03d9-143">**Trig1** 은 **T2**테이블을 업데이트하고 이 업데이트로 인해 AFTER 트리거 **Trig2** 가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="f03d9-143">**Trig1** updates table **T2**, and this update causes AFTER trigger **Trig2** to fire.</span></span> <span data-ttu-id="f03d9-144">**Trig2** 는 다시 **T1** 테이블을 업데이트하고 이로 인해 AFTER 트리거 **Trig1** 이 다시 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="f03d9-144">**Trig2** in turn updates table **T1** that causes AFTER trigger **Trig1** to fire again.</span></span>  
  
 <span data-ttu-id="f03d9-145">RECURSIVE_TRIGGERS 데이터베이스 옵션을 OFF로 설정하면 AFTER 트리거의 직접 재귀만 금지됩니다.</span><span class="sxs-lookup"><span data-stu-id="f03d9-145">Only direct recursion of AFTER triggers is prevented when the RECURSIVE_TRIGGERS database option is set to OFF.</span></span> <span data-ttu-id="f03d9-146">AFTER 트리거의 간접 재귀를 해제하려면 **nested triggers** 서버 옵션도 **0**으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="f03d9-146">To disable indirect recursion of AFTER triggers, also set the **nested triggers** server option to **0**.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="f03d9-147">예</span><span class="sxs-lookup"><span data-stu-id="f03d9-147">Examples</span></span>  
 <span data-ttu-id="f03d9-148">다음 예에서는 재귀 트리거를 사용하여 자체 참조 관계(전이 종료라고도 함)를 해결하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="f03d9-148">The following example shows using recursive triggers to solve a self-referencing relationship (also known as transitive closure).</span></span> <span data-ttu-id="f03d9-149">예를 들어 `emp_mgr` 테이블은 다음을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="f03d9-149">For example, the table `emp_mgr` defines the following:</span></span>  
  
-   <span data-ttu-id="f03d9-150">회사 직원(`emp`)</span><span class="sxs-lookup"><span data-stu-id="f03d9-150">An employee (`emp`) in a company.</span></span>  
  
-   <span data-ttu-id="f03d9-151">각 직원의 관리자(`mgr`)</span><span class="sxs-lookup"><span data-stu-id="f03d9-151">The manager for each employee (`mgr`).</span></span>  
  
-   <span data-ttu-id="f03d9-152">조직 트리 내에서 각 직원에게 보고하는 총 직원 수(`NoOfReports`)</span><span class="sxs-lookup"><span data-stu-id="f03d9-152">The total number of employees in the organizational tree reporting to each employee (`NoOfReports`).</span></span>  
  
 <span data-ttu-id="f03d9-153">재귀 UPDATE 트리거를 사용하여 새 직원 레코드가 삽입될 때 `NoOfReports` 열을 최신 상태로 유지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f03d9-153">A recursive UPDATE trigger can be used to keep the `NoOfReports` column up-to-date as new employee records are inserted.</span></span> <span data-ttu-id="f03d9-154">INSERT 트리거가 관리자 레코드의 `NoOfReports` 열을 업데이트하면 관리 계층 위에 있는 다른 레코드의 `NoOfReports` 열이 재귀적으로 업데이트됩니다.</span><span class="sxs-lookup"><span data-stu-id="f03d9-154">The INSERT trigger updates the `NoOfReports` column of the manager record, which recursively updates the `NoOfReports` column of other records up the management hierarchy.</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
-- Turn recursive triggers ON in the database.  
ALTER DATABASE AdventureWorks2012  
   SET RECURSIVE_TRIGGERS ON;  
GO  
CREATE TABLE dbo.emp_mgr (  
   emp char(30) PRIMARY KEY,  
    mgr char(30) NULL FOREIGN KEY REFERENCES emp_mgr(emp),  
    NoOfReports int DEFAULT 0  
);  
GO  
CREATE TRIGGER dbo.emp_mgrins ON dbo.emp_mgr  
FOR INSERT  
AS  
DECLARE @e char(30), @m char(30);  
DECLARE c1 CURSOR FOR  
   SELECT emp_mgr.emp  
   FROM   emp_mgr, inserted  
   WHERE emp_mgr.emp = inserted.mgr;  
  
OPEN c1;  
FETCH NEXT FROM c1 INTO @e;  
WHILE @@fetch_status = 0  
BEGIN  
   UPDATE dbo.emp_mgr  
   SET emp_mgr.NoOfReports = emp_mgr.NoOfReports + 1 -- Add 1 for newly  
   WHERE emp_mgr.emp = @e ;                           -- added employee.  
  
   FETCH NEXT FROM c1 INTO @e;  
END  
CLOSE c1;  
DEALLOCATE c1;  
GO  
-- This recursive UPDATE trigger works assuming:  
--   1. Only singleton updates on emp_mgr.  
--   2. No inserts in the middle of the org tree.  
CREATE TRIGGER dbo.emp_mgrupd ON dbo.emp_mgr FOR UPDATE  
AS  
IF UPDATE (mgr)  
BEGIN  
   UPDATE dbo.emp_mgr  
   SET emp_mgr.NoOfReports = emp_mgr.NoOfReports + 1 -- Increment mgr's  
   FROM inserted                            -- (no. of reports) by  
   WHERE emp_mgr.emp = inserted.mgr;         -- 1 for the new report.  
  
   UPDATE dbo.emp_mgr  
   SET emp_mgr.NoOfReports = emp_mgr.NoOfReports - 1 -- Decrement mgr's  
   FROM deleted                             -- (no. of reports) by 1  
   WHERE emp_mgr.emp = deleted.mgr;          -- for the new report.  
END  
GO  
-- Insert some test data rows.  
INSERT dbo.emp_mgr(emp, mgr) VALUES  
    ('Harry', NULL)  
    ,('Alice', 'Harry')  
    ,('Paul', 'Alice')  
    ,('Joe', 'Alice')  
    ,('Dave', 'Joe');  
GO  
SELECT emp,mgr,NoOfReports  
FROM dbo.emp_mgr;  
GO  
-- Change Dave's manager from Joe to Harry  
UPDATE dbo.emp_mgr SET mgr = 'Harry'  
WHERE emp = 'Dave';  
GO  
SELECT emp,mgr,NoOfReports FROM emp_mgr;  
  
GO  
```  
  
 <span data-ttu-id="f03d9-155">다음은 업데이트되기 전의 결과입니다.</span><span class="sxs-lookup"><span data-stu-id="f03d9-155">Here are the results before the update.</span></span>  
  
```  
emp                            mgr                           NoOfReports  
------------------------------ ----------------------------- -----------  
Alice                          Harry                          2  
Dave                           Joe                            0  
Harry                          NULL                           1  
Joe                            Alice                          1  
Paul                           Alice                          0  
```  
  
 <span data-ttu-id="f03d9-156">다음은 업데이트된 후의 결과입니다.</span><span class="sxs-lookup"><span data-stu-id="f03d9-156">Here are the results after the update.</span></span>  
  
```  
emp                            mgr                           NoOfReports  
------------------------------ ----------------------------- -----------  
Alice                          Harry                          2  
Dave                           Harry                          0  
Harry                          NULL                           2  
Joe                            Alice                          0  
Paul                           Alice                          0  
```  
  
 <span data-ttu-id="f03d9-157">**중첩 트리거 옵션을 설정하려면**</span><span class="sxs-lookup"><span data-stu-id="f03d9-157">**To set the nested triggers option**</span></span>  
  
-   [<span data-ttu-id="f03d9-158">sp_configure &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="f03d9-158">sp_configure &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
 <span data-ttu-id="f03d9-159">**RECURSIVE_TRIGGERS 데이터베이스 옵션을 설정하려면**</span><span class="sxs-lookup"><span data-stu-id="f03d9-159">**To set the RECURSIVE_TRIGGERS database option**</span></span>  
  
-   [<span data-ttu-id="f03d9-160">ALTER DATABASE SET 옵션&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="f03d9-160">ALTER DATABASE SET Options &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-database-transact-sql-set-options)  
  
## <a name="see-also"></a><span data-ttu-id="f03d9-161">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f03d9-161">See Also</span></span>  
 <span data-ttu-id="f03d9-162">[CREATE TRIGGER&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-trigger-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="f03d9-162">[CREATE TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-trigger-transact-sql) </span></span>  
 [<span data-ttu-id="f03d9-163">nested triggers 서버 구성 옵션 구성</span><span class="sxs-lookup"><span data-stu-id="f03d9-163">Configure the nested triggers Server Configuration Option</span></span>](../../database-engine/configure-windows/configure-the-nested-triggers-server-configuration-option.md)  
  
  
