---
title: DML 트리거 수정 또는 이름 바꾸기 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- renaming triggers
- modifying triggers
- DML triggers, modifying
ms.assetid: c7317eec-c0e9-479e-a4a7-83b6b6c58d59
author: rothja
ms.author: jroth
ms.openlocfilehash: 65bb13552b552d54b5547eadedc412977e423a57
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660383"
---
# <a name="modify-or-rename-dml-triggers"></a><span data-ttu-id="f744a-102">DML 트리거 수정 또는 이름 바꾸기</span><span class="sxs-lookup"><span data-stu-id="f744a-102">Modify or Rename DML Triggers</span></span>
  <span data-ttu-id="f744a-103">이 항목에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 에서 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 또는 [!INCLUDE[tsql](../../includes/tsql-md.md)]을 사용하여 DML 트리거를 수정하거나 이름을 바꾸는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="f744a-103">This topic describes how to modify or rename a DML trigger in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="f744a-104">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="f744a-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="f744a-105">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="f744a-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="f744a-106">제한 사항</span><span class="sxs-lookup"><span data-stu-id="f744a-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="f744a-107">권장 사항</span><span class="sxs-lookup"><span data-stu-id="f744a-107">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="f744a-108">보안</span><span class="sxs-lookup"><span data-stu-id="f744a-108">Security</span></span>](#Security)  
  
-   <span data-ttu-id="f744a-109">**DML 트리거를 수정하거나 이름을 바꾸려면:**</span><span class="sxs-lookup"><span data-stu-id="f744a-109">**To modify or rename a DML trigger, using:**</span></span>  
  
     [<span data-ttu-id="f744a-110">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="f744a-110">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="f744a-111">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="f744a-111">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="f744a-112">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="f744a-112">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="f744a-113">제한 사항</span><span class="sxs-lookup"><span data-stu-id="f744a-113">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="f744a-114">트리거의 이름을 바꿀 때 트리거가 현재 데이터베이스에 있어야 하고 새 이름이 [식별자](../databases/database-identifiers.md)에 대한 규칙을 따라야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f744a-114">When you rename a trigger, the trigger must be in the current database, and the new name must follow the rules for [identifiers](../databases/database-identifiers.md).</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="f744a-115">권장 사항</span><span class="sxs-lookup"><span data-stu-id="f744a-115">Recommendations</span></span>  
  
-   <span data-ttu-id="f744a-116">트리거의 이름을 바꿀 때 [sp_rename](/sql/relational-databases/system-stored-procedures/sp-rename-transact-sql) 저장 프로시저를 사용하지 않는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="f744a-116">We recommend you do not use the [sp_rename](/sql/relational-databases/system-stored-procedures/sp-rename-transact-sql) stored procedure to rename a trigger.</span></span> <span data-ttu-id="f744a-117">개체 이름의 일부를 변경하면 스크립트나 저장 프로시저가 작동되지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f744a-117">Changing any part of an object name can break scripts and stored procedures.</span></span> <span data-ttu-id="f744a-118">트리거의 이름을 변경해도 [sys.sql_modules](/sql/relational-databases/system-catalog-views/sys-sql-modules-transact-sql) 카탈로그 뷰의 definition 열에 있는 해당 개체 이름은 변경되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f744a-118">Renaming a trigger does not change the name of the corresponding object name in the definition column of the [sys.sql_modules](/sql/relational-databases/system-catalog-views/sys-sql-modules-transact-sql) catalog view.</span></span> <span data-ttu-id="f744a-119">대신 트리거를 삭제하고 다시 만드는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="f744a-119">We recommend that you drop and re-create the trigger instead.</span></span>  
  
-   <span data-ttu-id="f744a-120">DML 트리거가 참조하는 개체의 이름을 변경하면 트리거 텍스트에 새 개체 이름이 반영되도록 트리거를 수정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f744a-120">If you change the name of an object referenced by a DML trigger, you must modify the trigger so that its text reflects the new name.</span></span> <span data-ttu-id="f744a-121">따라서 개체 이름을 바꾸기 전에 먼저 개체의 종속성을 표시하여 영향을 받는 트리거가 있는지 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f744a-121">Therefore, before you rename an object, display the dependencies of the object first to determine whether any triggers are affected by the proposed change.</span></span>  
  
-   <span data-ttu-id="f744a-122">DML 트리거 정의를 암호화할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f744a-122">A DML trigger can also be modified to encrypt its definition.</span></span>  
  
-   <span data-ttu-id="f744a-123">트리거의 종속성을 보려면 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 또는 다음 함수와 카탈로그 뷰를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f744a-123">To view the dependencies of a trigger, you can use [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or the following function and catalog views:</span></span>  
  
    -   [<span data-ttu-id="f744a-124">sys.sql_expression_dependencies&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="f744a-124">sys.sql_expression_dependencies &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql)  
  
    -   [<span data-ttu-id="f744a-125">sys.dm_sql_referenced_entities&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="f744a-125">sys.dm_sql_referenced_entities &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-sql-referenced-entities-transact-sql)  
  
    -   [<span data-ttu-id="f744a-126">sys.dm_sql_referencing_entities&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="f744a-126">sys.dm_sql_referencing_entities &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-sql-referencing-entities-transact-sql)  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="f744a-127">보안</span><span class="sxs-lookup"><span data-stu-id="f744a-127">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="f744a-128">권한</span><span class="sxs-lookup"><span data-stu-id="f744a-128">Permissions</span></span>  
 <span data-ttu-id="f744a-129">DML 트리거를 변경하려면 트리거가 정의된 테이블 또는 뷰에 대한 ALTER 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="f744a-129">To alter a DML trigger requires ALTER permission on the table or view on which the trigger is defined.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="f744a-130">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="f744a-130">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-modify-a-dml-trigger"></a><span data-ttu-id="f744a-131">DML 트리거를 수정하려면</span><span class="sxs-lookup"><span data-stu-id="f744a-131">To modify a DML trigger</span></span>  
  
1.  <span data-ttu-id="f744a-132">**개체 탐색기**에서 [!INCLUDE[ssDE](../../../includes/ssde-md.md)] 의 인스턴스에 연결한 다음 해당 인스턴스를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="f744a-132">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)] and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="f744a-133">원하는 데이터베이스를 확장하고 **테이블**을 확장한 다음 수정할 트리거가 포함된 테이블을 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="f744a-133">Expand the database that you want, expand **Tables**, and then expand the table that contains the trigger that you want to modify.</span></span>  
  
3.  <span data-ttu-id="f744a-134">**트리거**를 확장하고 수정할 트리거를 마우스 오른쪽 단추로 클릭한 다음 **수정**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f744a-134">Expand **Triggers**, right-click the trigger to modify, and then click **Modify**.</span></span>  
  
4.  <span data-ttu-id="f744a-135">트리거를 수정한 다음 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f744a-135">Modify the trigger, and then click **Execute**.</span></span>  
  
#### <a name="to-rename-a-dml-trigger"></a><span data-ttu-id="f744a-136">DML 트리거의 이름을 바꾸려면</span><span class="sxs-lookup"><span data-stu-id="f744a-136">To rename a DML trigger</span></span>  
  
1.  <span data-ttu-id="f744a-137">이름을 바꿀[트리거를 삭제합니다](../triggers/dml-triggers.md) .</span><span class="sxs-lookup"><span data-stu-id="f744a-137">[Delete the trigger](../triggers/dml-triggers.md) that you want to rename.</span></span>  
  
2.  <span data-ttu-id="f744a-138">새 이름을 지정하여[트리거를 다시 만듭니다](../triggers/create-dml-triggers.md).</span><span class="sxs-lookup"><span data-stu-id="f744a-138">[Re-create the trigger](../triggers/create-dml-triggers.md), specifying the new name.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="f744a-139">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="f744a-139">Using Transact-SQL</span></span>  
  
#### <a name="to-modify-a-trigger-using-alter-trigger"></a><span data-ttu-id="f744a-140">ALTER TRIGGER를 사용하여 트리거를 수정하려면</span><span class="sxs-lookup"><span data-stu-id="f744a-140">To modify a trigger using ALTER TRIGGER</span></span>  
  
1.  <span data-ttu-id="f744a-141">[!INCLUDE[ssDE](../../../includes/ssde-md.md)]에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="f744a-141">Connect to the [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="f744a-142">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f744a-142">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="f744a-143">다음 예를 복사하여 쿼리에 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="f744a-143">Copy and paste the following examples into the query.</span></span> <span data-ttu-id="f744a-144">첫 번째 예를 실행하여 사용자가 `SalesPersonQuotaHistory` 테이블에 데이터를 추가 또는 변경하려고 시도하면 클라이언트로 사용자 정의 메시지를 인쇄하는 DML 트리거를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f744a-144">Execute the first example to create a DML trigger that prints a user-defined message to the client when a user tries to add or change data in the `SalesPersonQuotaHistory` table.</span></span> <span data-ttu-id="f744a-145">[ALTER TRIGGER](/sql/t-sql/statements/alter-trigger-transact-sql) 문을 실행하여 `INSERT` 작업에 대해서만 발생하도록 트리거를 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="f744a-145">Execute the [ALTER TRIGGER](/sql/t-sql/statements/alter-trigger-transact-sql) statement to modify the trigger to fire only on `INSERT` activities.</span></span> <span data-ttu-id="f744a-146">이 트리거는 테이블에 행을 삽입하거나 업데이트하는 사용자에게 `Compensation` 부서에도 해당 사실을 통지하도록 알려 줍니다.</span><span class="sxs-lookup"><span data-stu-id="f744a-146">This trigger is helpful because it reminds the user that updates or inserts rows into this table to also notify the `Compensation` department.</span></span>  
  
```sql  
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
USE AdventureWorks2012;  
GO  
ALTER TRIGGER Sales.bonus_reminder  
ON Sales.SalesPersonQuotaHistory  
AFTER INSERT  
AS RAISERROR ('Notify Compensation', 16, 10);  
GO  
  
```  
  
#### <a name="to-rename-a-trigger-using-drop-trigger-and-alter-trigger"></a><span data-ttu-id="f744a-147">DROP TRIGGER 및 ALTER TRIGGER를 사용하여 트리거의 이름을 바꾸려면</span><span class="sxs-lookup"><span data-stu-id="f744a-147">To rename a trigger using DROP TRIGGER and ALTER TRIGGER</span></span>  
  
1.  <span data-ttu-id="f744a-148">[!INCLUDE[ssDE](../../../includes/ssde-md.md)]에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="f744a-148">Connect to the [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="f744a-149">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f744a-149">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="f744a-150">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f744a-150">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="f744a-151">이 예에서는 [DROP TRIGGER](/sql/t-sql/statements/drop-trigger-transact-sql) 및 [ALTER TRIGGER](/sql/t-sql/statements/alter-trigger-transact-sql) 문을 사용하여 `Sales.bonus_reminder` 트리거의 이름을 `Sales.bonus_reminder_2`로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="f744a-151">This example use the [DROP TRIGGER](/sql/t-sql/statements/drop-trigger-transact-sql) and [ALTER TRIGGER](/sql/t-sql/statements/alter-trigger-transact-sql) statements to rename the `Sales.bonus_reminder` trigger to `Sales.bonus_reminder_2`.</span></span>  
  
```sql  
USE AdventureWorks2012;  
GO  
IF OBJECT_ID(N'Sales.bonus_reminder', N'TR') IS NOT NULL  
    DROP TRIGGER Sales.bonus_reminder;  
GO  
CREATE TRIGGER Sales.bonus_reminder_2  
ON Sales.SalesPersonQuotaHistory  
WITH ENCRYPTION  
AFTER INSERT, UPDATE   
AS RAISERROR ('Notify Compensation', 16, 10);  
GO  
  
```  
  
## <a name="see-also"></a><span data-ttu-id="f744a-152">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f744a-152">See Also</span></span>  
 <span data-ttu-id="f744a-153">[CREATE TRIGGER&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-trigger-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="f744a-153">[CREATE TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-trigger-transact-sql) </span></span>  
 <span data-ttu-id="f744a-154">[DROP TRIGGER&#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-trigger-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="f744a-154">[DROP TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-trigger-transact-sql) </span></span>  
 <span data-ttu-id="f744a-155">[ENABLE TRIGGER&#40;Transact-SQL&#41;](/sql/t-sql/statements/enable-trigger-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="f744a-155">[ENABLE TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/enable-trigger-transact-sql) </span></span>  
 <span data-ttu-id="f744a-156">[DISABLE TRIGGER&#40;Transact-SQL&#41;](/sql/t-sql/statements/disable-trigger-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="f744a-156">[DISABLE TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/disable-trigger-transact-sql) </span></span>  
 <span data-ttu-id="f744a-157">[EVENTDATA&#40;Transact-SQL&#41;](/sql/t-sql/functions/eventdata-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="f744a-157">[EVENTDATA &#40;Transact-SQL&#41;](/sql/t-sql/functions/eventdata-transact-sql) </span></span>  
 <span data-ttu-id="f744a-158">[sp_rename&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-rename-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="f744a-158">[sp_rename &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-rename-transact-sql) </span></span>  
 <span data-ttu-id="f744a-159">[ALTER TRIGGER&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-trigger-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="f744a-159">[ALTER TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-trigger-transact-sql) </span></span>  
 <span data-ttu-id="f744a-160">[DML 트리거에 대한 정보 가져오기](../triggers/get-information-about-dml-triggers.md) </span><span class="sxs-lookup"><span data-stu-id="f744a-160">[Get Information About DML Triggers](../triggers/get-information-about-dml-triggers.md) </span></span>  
 <span data-ttu-id="f744a-161">[sp_help&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="f744a-161">[sp_help &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-transact-sql) </span></span>  
 <span data-ttu-id="f744a-162">[sp_helptrigger&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helptrigger-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="f744a-162">[sp_helptrigger &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helptrigger-transact-sql) </span></span>  
 <span data-ttu-id="f744a-163">[sys.triggers&#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-triggers-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="f744a-163">[sys.triggers &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-triggers-transact-sql) </span></span>  
 <span data-ttu-id="f744a-164">[sys.trigger_events&#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-trigger-events-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="f744a-164">[sys.trigger_events &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-trigger-events-transact-sql) </span></span>  
 <span data-ttu-id="f744a-165">[sys.sql_modules&#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-sql-modules-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="f744a-165">[sys.sql_modules &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-sql-modules-transact-sql) </span></span>  
 <span data-ttu-id="f744a-166">[sys.assembly_modules&#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-assembly-modules-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="f744a-166">[sys.assembly_modules &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-assembly-modules-transact-sql) </span></span>  
 <span data-ttu-id="f744a-167">[sys.server_triggers&#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-triggers-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="f744a-167">[sys.server_triggers &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-triggers-transact-sql) </span></span>  
 <span data-ttu-id="f744a-168">[sys.server_trigger_events&#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-trigger-events-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="f744a-168">[sys.server_trigger_events &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-trigger-events-transact-sql) </span></span>  
 <span data-ttu-id="f744a-169">[sys.server_sql_modules&#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-sql-modules-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="f744a-169">[sys.server_sql_modules &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-sql-modules-transact-sql) </span></span>  
 [<span data-ttu-id="f744a-170">sys.server_assembly_modules&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="f744a-170">sys.server_assembly_modules &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-server-assembly-modules-transact-sql)  
  
  
