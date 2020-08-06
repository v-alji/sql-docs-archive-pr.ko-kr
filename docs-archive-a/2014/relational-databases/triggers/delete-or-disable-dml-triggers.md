---
title: DML 트리거 삭제 또는 해제 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- DML triggers, disabling
- removing DML triggers
- disabling DML triggers
- dropping DML triggers
- deleting DML triggers
- DML triggers, removing
ms.assetid: 0f97f953-33c5-4b26-afeb-db2a26ce38b4
author: rothja
ms.author: jroth
ms.openlocfilehash: 39b345ade1258987df06938791ac0024e8612365
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660400"
---
# <a name="delete-or-disable-dml-triggers"></a><span data-ttu-id="eb46d-102">DML 트리거 삭제 또는 해제</span><span class="sxs-lookup"><span data-stu-id="eb46d-102">Delete or Disable DML Triggers</span></span>
  <span data-ttu-id="eb46d-103">이 항목에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 또는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 을 사용하여 [!INCLUDE[tsql](../../includes/tsql-md.md)]에서 DML 트리거를 삭제하거나 비활성화하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="eb46d-103">This topic describes how to delete or disable a DML trigger in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="eb46d-104">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="eb46d-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="eb46d-105">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="eb46d-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="eb46d-106">권장 사항</span><span class="sxs-lookup"><span data-stu-id="eb46d-106">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="eb46d-107">보안</span><span class="sxs-lookup"><span data-stu-id="eb46d-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="eb46d-108">**DML 트리거를 삭제하거나 비활성화하려면:**</span><span class="sxs-lookup"><span data-stu-id="eb46d-108">**To delete or disable a DML trigger, using:**</span></span>  
  
     [<span data-ttu-id="eb46d-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="eb46d-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="eb46d-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="eb46d-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="eb46d-111">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="eb46d-111">Before You Begin</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="eb46d-112">권장 사항</span><span class="sxs-lookup"><span data-stu-id="eb46d-112">Recommendations</span></span>  
  
-   <span data-ttu-id="eb46d-113">트리거를 삭제하면 현재 데이터베이스에서 트리거가 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="eb46d-113">When a trigger is deleted, it is dropped from the current database.</span></span> <span data-ttu-id="eb46d-114">트리거의 기반이 되는 테이블과 데이터는 영향을 받지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eb46d-114">The table and the data upon which it is based are not affected.</span></span> <span data-ttu-id="eb46d-115">테이블을 삭제하면 테이블에 있는 트리거도 자동으로 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="eb46d-115">Deleting a table automatically deletes any triggers on the table.</span></span>  
  
-   <span data-ttu-id="eb46d-116">트리거를 만들면 이 트리거는 기본적으로 활성화됩니다.</span><span class="sxs-lookup"><span data-stu-id="eb46d-116">A trigger is enabled by default when it is created.</span></span>  
  
-   <span data-ttu-id="eb46d-117">트리거를 비활성화하면 트리거는 삭제되지 않고</span><span class="sxs-lookup"><span data-stu-id="eb46d-117">Disabling a trigger does not drop it.</span></span> <span data-ttu-id="eb46d-118">현재 데이터베이스의 개체로 남아 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eb46d-118">The trigger still exists as an object in the current database.</span></span> <span data-ttu-id="eb46d-119">그러나 해당 트리거가 프로그래밍된 INSERT, UPDATE 또는 DELETE 문이 실행될 때 트리거가 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eb46d-119">However, the trigger will not fire when any INSERT, UPDATE, or DELETE statement on which it was programmed is executed.</span></span> <span data-ttu-id="eb46d-120">트리거를 해제했다가 다시 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eb46d-120">Triggers that are disabled can be reenabled.</span></span> <span data-ttu-id="eb46d-121">트리거를 활성화하더라도 트리거를 다시 만드는 것은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="eb46d-121">Enabling a trigger does not re-create it.</span></span> <span data-ttu-id="eb46d-122">트리거는 원래 생성되었을 때와 동일하게 발생됩니다.</span><span class="sxs-lookup"><span data-stu-id="eb46d-122">The trigger fires in the same manner as when it was originally created.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="eb46d-123">보안</span><span class="sxs-lookup"><span data-stu-id="eb46d-123">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="eb46d-124">권한</span><span class="sxs-lookup"><span data-stu-id="eb46d-124">Permissions</span></span>  
 <span data-ttu-id="eb46d-125">DML 트리거를 삭제하려면 트리거가 정의된 테이블 또는 뷰에 대한 ALTER 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="eb46d-125">To delete a DML trigger requires ALTER permission on the table or view on which the trigger is defined.</span></span>  
  
 <span data-ttu-id="eb46d-126">DML 트리거를 비활성화하거나 활성화하려면 사용자에게 트리거가 만들어진 테이블 또는 뷰에 대한 ALTER 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb46d-126">To disable or enable a DML trigger, at a minimum, a user must have ALTER permission on the table or view on which the trigger was created.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="eb46d-127">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="eb46d-127">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-delete-a-dml-trigger"></a><span data-ttu-id="eb46d-128">DML 트리거를 삭제하려면</span><span class="sxs-lookup"><span data-stu-id="eb46d-128">To delete a DML trigger</span></span>  
  
1.  <span data-ttu-id="eb46d-129">**개체 탐색기**에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 의 인스턴스에 연결한 다음 해당 인스턴스를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="eb46d-129">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)] and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="eb46d-130">원하는 데이터베이스를 확장하고 **테이블**을 확장한 다음 삭제할 트리거가 포함된 테이블을 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="eb46d-130">Expand the database that you want, expand **Tables**, and then expand the table that contains the trigger that you want to delete.</span></span>  
  
3.  <span data-ttu-id="eb46d-131">**트리거**를 확장하고 삭제할 트리거를 마우스 오른쪽 단추로 클릭한 다음 **삭제**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="eb46d-131">Expand **Triggers**, right-click the trigger to delete, and then click **Delete**.</span></span>  
  
4.  <span data-ttu-id="eb46d-132">**개체 삭제** 대화 상자에서 삭제할 트리거를 확인한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="eb46d-132">In the **Delete Object** dialog box, verify the trigger to delete, and then click **OK**.</span></span>  
  
#### <a name="to-disable-and-enable-a-dml-trigger"></a><span data-ttu-id="eb46d-133">DML 트리거를 비활성화하거나 활성화하려면</span><span class="sxs-lookup"><span data-stu-id="eb46d-133">To disable and enable a DML trigger</span></span>  
  
1.  <span data-ttu-id="eb46d-134">**개체 탐색기**에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 의 인스턴스에 연결한 다음 해당 인스턴스를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="eb46d-134">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)] and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="eb46d-135">원하는 데이터베이스를 확장하고 **테이블**을 확장한 다음 비활성화할 트리거가 포함된 테이블을 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="eb46d-135">Expand the database that you want, expand **Tables**, and then expand the table that contains the trigger that you want to disable.</span></span>  
  
3.  <span data-ttu-id="eb46d-136">**트리거**를 확장하고 비활성화할 트리거를 마우스 오른쪽 단추로 클릭한 다음 **사용 안 함**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="eb46d-136">Expand **Triggers**, right-click the trigger to disable, and then click **Disable**.</span></span>  
  
4.  <span data-ttu-id="eb46d-137">트리거를 활성화하려면 **사용**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="eb46d-137">To enable the trigger, click **Enable**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="eb46d-138">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="eb46d-138">Using Transact-SQL</span></span>  
  
#### <a name="to-delete-a-dml-trigger"></a><span data-ttu-id="eb46d-139">DML 트리거를 삭제하려면</span><span class="sxs-lookup"><span data-stu-id="eb46d-139">To delete a DML trigger</span></span>  
  
1.  <span data-ttu-id="eb46d-140">[!INCLUDE[ssDE](../../includes/ssde-md.md)]에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="eb46d-140">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="eb46d-141">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="eb46d-141">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="eb46d-142">다음 예를 복사하여 쿼리 창에 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="eb46d-142">Copy and paste the following examples into the query window.</span></span> <span data-ttu-id="eb46d-143">[트리거를 만들려면](/sql/t-sql/statements/create-trigger-transact-sql) CREATE TRIGGER `Sales.bonus_reminder` 문을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="eb46d-143">Execute the [CREATE TRIGGER](/sql/t-sql/statements/create-trigger-transact-sql) statement to create the `Sales.bonus_reminder` trigger.</span></span> <span data-ttu-id="eb46d-144">트리거를 삭제하려면 [DROP TRIGGER](/sql/t-sql/statements/drop-trigger-transact-sql) 문을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="eb46d-144">To delete the trigger, execute the [DROP TRIGGER](/sql/t-sql/statements/drop-trigger-transact-sql) statement.</span></span>  
  
```sql  
--Create the trigger.  
USE AdventureWorks2012;  
GO  
IF OBJECT_ID(N'Sales.bonus_reminder', N'TR') IS NOT NULL  
    DROP TRIGGER Sales.bonus_reminder;  
GO  
CREATE TRIGGER Sales.bonus_reminder  
ON Sales.SalesPersonQuotaHistory  
WITH ENCRYPTION  
AFTER INSERT, UPDATE   
AS RAISERROR ('Notify Compensation', 16, 10);  
GO  
  
```  
  
```sql  
--Delete the trigger.  
USE AdventureWorks2012;  
GO  
IF OBJECT_ID ('Sales.bonus_reminder', 'TR') IS NOT NULL  
   DROP TRIGGER Sales.bonus_reminder;  
GO  
  
```  
  
#### <a name="to-disable-and-enable-a-dml-trigger"></a><span data-ttu-id="eb46d-145">DML 트리거를 비활성화하거나 활성화하려면</span><span class="sxs-lookup"><span data-stu-id="eb46d-145">To disable and enable a DML trigger</span></span>  
  
1.  <span data-ttu-id="eb46d-146">[!INCLUDE[ssDE](../../includes/ssde-md.md)]에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="eb46d-146">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="eb46d-147">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="eb46d-147">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="eb46d-148">다음 예를 복사하여 쿼리 창에 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="eb46d-148">Copy and paste the following examples into the query window.</span></span> <span data-ttu-id="eb46d-149">[트리거를 만들려면](/sql/t-sql/statements/create-trigger-transact-sql) CREATE TRIGGER `Sales.bonus_reminder` 문을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="eb46d-149">Execute the [CREATE TRIGGER](/sql/t-sql/statements/create-trigger-transact-sql) statement to create the `Sales.bonus_reminder` trigger.</span></span> <span data-ttu-id="eb46d-150">트리거를 비활성화하거나 활성화려면 [DISABLE TRIGGER](/sql/t-sql/statements/disable-trigger-transact-sql) 및 [ENABLE TRIGGER](/sql/t-sql/statements/enable-trigger-transact-sql) 문을 각각 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="eb46d-150">To disable and enable the trigger, execute the [DISABLE TRIGGER](/sql/t-sql/statements/disable-trigger-transact-sql) and [ENABLE TRIGGER](/sql/t-sql/statements/enable-trigger-transact-sql) statements, respectively.</span></span>  
  
```sql  
--Create the trigger.  
USE AdventureWorks2012;  
GO  
IF OBJECT_ID(N'Sales.bonus_reminder', N'TR') IS NOT NULL  
    DROP TRIGGER Sales.bonus_reminder;  
GO  
CREATE TRIGGER Sales.bonus_reminder  
ON Sales.SalesPersonQuotaHistory  
WITH ENCRYPTION  
AFTER INSERT, UPDATE   
AS RAISERROR ('Notify Compensation', 16, 10);  
GO  
  
```  
  
```sql  
--Disable the trigger.  
USE AdventureWorks2012;  
GO  
DISABLE TRIGGER Sales.bonus_reminder ON Sales.SalesPersonQuotaHistory;  
GO  
  
```  
  
```sql  
--Enable the trigger.  
USE AdventureWorks2012;  
GO  
ENABLE TRIGGER Sales.bonus_reminder ON Sales.SalesPersonQuotaHistory;  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="eb46d-151">참고 항목</span><span class="sxs-lookup"><span data-stu-id="eb46d-151">See Also</span></span>  
 <span data-ttu-id="eb46d-152">[ALTER TRIGGER&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-trigger-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="eb46d-152">[ALTER TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-trigger-transact-sql) </span></span>  
 <span data-ttu-id="eb46d-153">[CREATE TRIGGER&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-trigger-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="eb46d-153">[CREATE TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-trigger-transact-sql) </span></span>  
 <span data-ttu-id="eb46d-154">[DROP TRIGGER&#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-trigger-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="eb46d-154">[DROP TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-trigger-transact-sql) </span></span>  
 <span data-ttu-id="eb46d-155">[ENABLE TRIGGER&#40;Transact-SQL&#41;](/sql/t-sql/statements/enable-trigger-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="eb46d-155">[ENABLE TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/enable-trigger-transact-sql) </span></span>  
 <span data-ttu-id="eb46d-156">[DISABLE TRIGGER&#40;Transact-SQL&#41;](/sql/t-sql/statements/disable-trigger-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="eb46d-156">[DISABLE TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/disable-trigger-transact-sql) </span></span>  
 <span data-ttu-id="eb46d-157">[EVENTDATA&#40;Transact-SQL&#41;](/sql/t-sql/functions/eventdata-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="eb46d-157">[EVENTDATA &#40;Transact-SQL&#41;](/sql/t-sql/functions/eventdata-transact-sql) </span></span>  
 <span data-ttu-id="eb46d-158">[DML 트리거에 대한 정보 가져오기](dml-triggers.md) </span><span class="sxs-lookup"><span data-stu-id="eb46d-158">[Get Information About DML Triggers](dml-triggers.md) </span></span>  
 <span data-ttu-id="eb46d-159">[sp_help&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="eb46d-159">[sp_help &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-transact-sql) </span></span>  
 <span data-ttu-id="eb46d-160">[sp_helptrigger&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helptrigger-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="eb46d-160">[sp_helptrigger &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helptrigger-transact-sql) </span></span>  
 <span data-ttu-id="eb46d-161">[sys.triggers&#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-triggers-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="eb46d-161">[sys.triggers &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-triggers-transact-sql) </span></span>  
 <span data-ttu-id="eb46d-162">[sys.trigger_events&#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-trigger-events-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="eb46d-162">[sys.trigger_events &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-trigger-events-transact-sql) </span></span>  
 <span data-ttu-id="eb46d-163">[sys.sql_modules&#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-sql-modules-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="eb46d-163">[sys.sql_modules &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-sql-modules-transact-sql) </span></span>  
 <span data-ttu-id="eb46d-164">[sys.assembly_modules&#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-assembly-modules-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="eb46d-164">[sys.assembly_modules &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-assembly-modules-transact-sql) </span></span>  
 <span data-ttu-id="eb46d-165">[sys.server_triggers&#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-triggers-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="eb46d-165">[sys.server_triggers &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-triggers-transact-sql) </span></span>  
 <span data-ttu-id="eb46d-166">[sys.server_trigger_events&#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-trigger-events-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="eb46d-166">[sys.server_trigger_events &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-trigger-events-transact-sql) </span></span>  
 <span data-ttu-id="eb46d-167">[sys.server_sql_modules&#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-sql-modules-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="eb46d-167">[sys.server_sql_modules &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-sql-modules-transact-sql) </span></span>  
 [<span data-ttu-id="eb46d-168">sys.server_assembly_modules&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="eb46d-168">sys.server_assembly_modules &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-server-assembly-modules-transact-sql)  
  
  
