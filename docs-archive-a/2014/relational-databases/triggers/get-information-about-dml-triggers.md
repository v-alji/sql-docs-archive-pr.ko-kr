---
title: DML 트리거에 대한 정보 가져오기 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- metadata [SQL Server], triggers
- viewing DML triggers
- DML triggers, metadata
- displaying DML triggers
- status information [SQL Server], triggers
- DML triggers, viewing
ms.assetid: 37574aac-181d-4aca-a2cc-8abff64237dc
author: rothja
ms.author: jroth
ms.openlocfilehash: 2f65976d2f517137e23bd9e5e1c98cc76324bc49
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660396"
---
# <a name="get-information-about-dml-triggers"></a><span data-ttu-id="0010f-102">DML 트리거에 대한 정보 가져오기</span><span class="sxs-lookup"><span data-stu-id="0010f-102">Get Information About DML Triggers</span></span>
  <span data-ttu-id="0010f-103">이 항목에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 에서 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 또는 [!INCLUDE[tsql](../../includes/tsql-md.md)]을 사용하여 DML 트리거에 대한 정보를 얻는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="0010f-103">This topic describes how to get information about DML triggers in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="0010f-104">이 정보에는 테이블에 있는 트리거의 유형, 이름, 소유자 및 작성 또는 수정 날짜가 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0010f-104">This information can include the types of triggers on a table, the name of a trigger, its owner and the date it was created or modified.</span></span> <span data-ttu-id="0010f-105">트리거를 만들었을 때 암호화하지 않은 경우 트리거의 정의를 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0010f-105">If the trigger was not encrypted when it was created, you obtain the definition of the trigger.</span></span> <span data-ttu-id="0010f-106">이 정의를 사용하여 테이블에 정의된 트리거가 해당 테이블에 어떠한 영향을 주는지를 이해할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0010f-106">You can use the definition to help you understand how a trigger affects the table up on which it is defined.</span></span> <span data-ttu-id="0010f-107">또한 특정 트리거가 사용하는 개체를 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0010f-107">Also, you can find out the objects that a specific trigger uses.</span></span> <span data-ttu-id="0010f-108">이 정보를 사용하면 데이터베이스에서 변경되거나 삭제될 때 트리거에 영향을 주는 개체를 식별할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0010f-108">With this information, you can identify the objects that affect the trigger if they are changed or deleted in the database.</span></span>  
  
 <span data-ttu-id="0010f-109">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="0010f-109">**In This Topic**</span></span>  
  
-   <span data-ttu-id="0010f-110">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="0010f-110">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="0010f-111">보안</span><span class="sxs-lookup"><span data-stu-id="0010f-111">Security</span></span>](#Security)  
  
-   <span data-ttu-id="0010f-112">**DML 트리거에 대한 정보를 얻으려면:**</span><span class="sxs-lookup"><span data-stu-id="0010f-112">**To get information about DML triggers, using:**</span></span>  
  
     [<span data-ttu-id="0010f-113">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="0010f-113">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="0010f-114">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="0010f-114">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="0010f-115">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="0010f-115">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="0010f-116">보안</span><span class="sxs-lookup"><span data-stu-id="0010f-116">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="0010f-117">권한</span><span class="sxs-lookup"><span data-stu-id="0010f-117">Permissions</span></span>  
 <span data-ttu-id="0010f-118">**sys.sql.modules**, **sys.object**, **sys.triggers**, **sys.events**, **sys.trigger_events**</span><span class="sxs-lookup"><span data-stu-id="0010f-118">**sys.sql.modules**, **sys.object**, **sys.triggers**, **sys.events**, **sys.trigger_events**</span></span>  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] <span data-ttu-id="0010f-119">자세한 내용은 [Metadata Visibility Configuration](../security/metadata-visibility-configuration.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0010f-119">For more information, see [Metadata Visibility Configuration](../security/metadata-visibility-configuration.md).</span></span>  
  
 <span data-ttu-id="0010f-120">OBJECT_DEFINITION, OBJECTPROPERTY, **sp_helptext**</span><span class="sxs-lookup"><span data-stu-id="0010f-120">OBJECT_DEFINITION, OBJECTPROPERTY, **sp_helptext**</span></span>  
 <span data-ttu-id="0010f-121">**public** 역할의 멤버 자격이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="0010f-121">Requires membership in the **public** role.</span></span> <span data-ttu-id="0010f-122">개체 소유자나 ALTER, CONTROL, TAKE OWNERSHIP 또는 VIEW DEFINITION 권한 중 하나를 부여 받은 사람은 사용자 개체의 정의를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0010f-122">The definition of user objects is visible to the object owner or grantees that have any one of the following permissions: ALTER, CONTROL, TAKE OWNERSHIP, or VIEW DEFINITION.</span></span> <span data-ttu-id="0010f-123">이 권한은 **db_owner**, **db_ddladmin**및 **db_securityadmin** 고정 데이터베이스 역할의 멤버가 암시적으로 보유합니다.</span><span class="sxs-lookup"><span data-stu-id="0010f-123">These permissions are implicitly held by members of the **db_owner**, **db_ddladmin**, and **db_securityadmin** fixed database roles.</span></span>  
  
 <span data-ttu-id="0010f-124">**sys.sql_expression_dependencies**</span><span class="sxs-lookup"><span data-stu-id="0010f-124">**sys.sql_expression_dependencies**</span></span>  
 <span data-ttu-id="0010f-125">데이터베이스에 대한 VIEW DEFINITION 권한과 데이터베이스의 **sys.sql_expression_dependencies** 에 대한 SELECT 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="0010f-125">Requires VIEW DEFINITION permission on the database and SELECT permission on **sys.sql_expression_dependencies** for the database.</span></span> <span data-ttu-id="0010f-126">기본적으로 SELECT 권한은 **db_owner** 고정 데이터베이스 역할의 멤버에게만 부여됩니다.</span><span class="sxs-lookup"><span data-stu-id="0010f-126">By default, SELECT permission is granted only to members of the **db_owner** fixed database role.</span></span> <span data-ttu-id="0010f-127">SELECT와 VIEW DEFINITION 권한을 다른 사용자에게 부여하면 피부여자는 데이터베이스의 모든 종속성을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0010f-127">When SELECT and VIEW DEFINITION permissions are granted to another user, the grantee can view all dependencies in the database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="0010f-128">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="0010f-128">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-view-the-definition-of-a-dml-trigger"></a><span data-ttu-id="0010f-129">DML 트리거의 정의를 보려면</span><span class="sxs-lookup"><span data-stu-id="0010f-129">To view the definition of a DML trigger</span></span>  
  
1.  <span data-ttu-id="0010f-130">**개체 탐색기**에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 의 인스턴스에 연결한 다음 해당 인스턴스를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="0010f-130">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)] and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="0010f-131">원하는 데이터베이스를 확장하고 **테이블**을 확장한 다음 정의를 볼 트리거가 포함된 테이블을 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="0010f-131">Expand the database that you want, expand **Tables**, and then expand the table that contains the trigger for which you want to view the definition.</span></span>  
  
3.  <span data-ttu-id="0010f-132">**트리거**를 확장하고 원하는 트리거를 마우스 오른쪽 단추로 클릭한 다음 **수정**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0010f-132">Expand **Triggers**, right-click the trigger you want, and then click **Modify**.</span></span> <span data-ttu-id="0010f-133">DML 트리거의 정의가 쿼리 창에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="0010f-133">The definition of the DML trigger appears in the query window.</span></span>  
  
#### <a name="to-view-the-dependencies-of-a-dml-trigger"></a><span data-ttu-id="0010f-134">DML 트리거의 종속성을 보려면</span><span class="sxs-lookup"><span data-stu-id="0010f-134">To view the dependencies of a DML trigger</span></span>  
  
1.  <span data-ttu-id="0010f-135">**개체 탐색기**에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 의 인스턴스에 연결한 다음 해당 인스턴스를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="0010f-135">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)] and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="0010f-136">원하는 데이터베이스를 확장하고 **테이블**을 확장한 다음 보려는 트리거와 해당 종속성이 포함된 테이블을 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="0010f-136">Expand the database that you want, expand **Tables**, and then expand the table that contains the trigger and its dependencies that you want to view.</span></span>  
  
3.  <span data-ttu-id="0010f-137">**트리거**를 확장하고 원하는 트리거를 마우스 오른쪽 단추로 클릭한 다음 **종속성 보기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0010f-137">Expand **Triggers**, right-click the trigger you want, and then click **View Dependencies**.</span></span>  
  
4.  <span data-ttu-id="0010f-138">**개체 종속성** 창에서 DML 트리거에 종속되는 개체를 보려면 **\<DML trigger name>에 종속된 개체**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="0010f-138">In the **Object Dependencies** window, to view the objects that depend on the DML trigger, select **Objects that depend on \<DML trigger name>**.</span></span> <span data-ttu-id="0010f-139">개체가 **종속성** 영역에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="0010f-139">The objects appear in the **Dependencies** area.</span></span>  
  
     <span data-ttu-id="0010f-140">DML이 종속되는 개체를 보려면 **\<DML trigger name>이 종속된 개체**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="0010f-140">To view the objects on which the DML depends, select **Objects on which \<DML trigger name> depends**.</span></span> <span data-ttu-id="0010f-141">개체가 **종속성** 영역에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="0010f-141">The objects appear in the **Dependencies** area.</span></span> <span data-ttu-id="0010f-142">각 노드를 확장하여 모든 개체를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="0010f-142">Expand each node to see all the objects.</span></span>  
  
5.  <span data-ttu-id="0010f-143">**종속성** 영역에 나타나는 개체에 대한 정보를 얻으려면 개체를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0010f-143">To obtain information about an object that appears in the **Dependencies** area, click the object.</span></span> <span data-ttu-id="0010f-144">**선택한 개체** 필드에서 **이름**, **유형**및 **종속성 유형** 상자에 정보가 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="0010f-144">In the **Selected object** field, information is provided in the **Name**, **Type**, and **Dependency type** boxes.</span></span>  
  
6.  <span data-ttu-id="0010f-145">**개체 종속성** 창을 닫으려면 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0010f-145">To close the **Object Dependencies** window, click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="0010f-146">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="0010f-146">Using Transact-SQL</span></span>  
  
#### <a name="to-view-the-definition-of-a-dml-trigger"></a><span data-ttu-id="0010f-147">DML 트리거의 정의를 보려면</span><span class="sxs-lookup"><span data-stu-id="0010f-147">To view the definition of a DML trigger</span></span>  
  
1.  <span data-ttu-id="0010f-148">[!INCLUDE[ssDE](../../includes/ssde-md.md)]에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="0010f-148">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="0010f-149">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0010f-149">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="0010f-150">다음 예 중 하나를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0010f-150">Copy and paste one of the following examples into the query window and click **Execute**.</span></span> <span data-ttu-id="0010f-151">각 예에서는 `iuPerson` 트리거의 정의를 보는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="0010f-151">Each example shows how you can view the definition of the `iuPerson` trigger.</span></span>  
  
```sql  
USE AdventureWorks2012;  
GO  
SELECT definition   
FROM sys.sql_modules  
WHERE object_id = OBJECT_ID(N'Person.iuPerson');   
GO  
```  
  
```sql  
USE AdventureWorks2012;   
GO  
SELECT OBJECT_DEFINITION (OBJECT_ID(N'Person.iuPerson')) AS ObjectDefinition;   
GO  
  
```  
  
```sql  
USE AdventureWorks2012;   
GO  
EXEC sp_helptext 'Person.iuPerson'  
GO  
  
```  
  
#### <a name="to-view-the-dependencies-of-a-dml-trigger"></a><span data-ttu-id="0010f-152">DML 트리거의 종속성을 보려면</span><span class="sxs-lookup"><span data-stu-id="0010f-152">To view the dependencies of a DML trigger</span></span>  
  
1.  <span data-ttu-id="0010f-153">[!INCLUDE[ssDE](../../includes/ssde-md.md)]에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="0010f-153">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="0010f-154">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0010f-154">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="0010f-155">다음 예 중 하나를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0010f-155">Copy and paste one of the following examples into the query window and click **Execute**.</span></span> <span data-ttu-id="0010f-156">각 예에서는 `iuPerson` 트리거의 종속성을 보는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="0010f-156">Each example shows how you can view the dependencies of `iuPerson` trigger.</span></span>  
  
```  
USE AdventureWorks2012;   
GO  
SELECT OBJECT_NAME(referencing_id) AS referencing_entity_name,   
    o.type_desc AS referencing_desciption,   
    COALESCE(COL_NAME(referencing_id, referencing_minor_id), '(n/a)') AS referencing_minor_id,   
    referencing_class_desc, referenced_class_desc,   
    referenced_server_name, referenced_database_name, referenced_schema_name,   
    referenced_entity_name,   
    COALESCE(COL_NAME(referenced_id, referenced_minor_id), '(n/a)') AS referenced_column_name,   
    is_caller_dependent, is_ambiguous  
FROM sys.sql_expression_dependencies AS sed  
INNER JOIN sys.objects AS o ON sed.referencing_id = o.object_id  
WHERE referencing_id = OBJECT_ID(N'Person.iuPerson');   
GO  
  
```  
  
#### <a name="to-view-information-about-dml-triggers-in-the-database"></a><span data-ttu-id="0010f-157">데이터베이스의 DML 트리거에 대한 정보를 보려면</span><span class="sxs-lookup"><span data-stu-id="0010f-157">To view information about DML triggers in the database</span></span>  
  
1.  <span data-ttu-id="0010f-158">[!INCLUDE[ssDE](../../includes/ssde-md.md)]에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="0010f-158">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="0010f-159">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0010f-159">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="0010f-160">다음 예 중 하나를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0010f-160">Copy and paste one of the following examples into the query window and click **Execute**.</span></span> <span data-ttu-id="0010f-161">각 예에서는 데이터베이스에서 DML 트리거(`TR`)에 대한 정보를 보는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="0010f-161">Each example shows how you can view information about DML triggers (`TR`) in the database.</span></span>  
  
```  
USE AdventureWorks2012;   
GO  
SELECT  name, parent_id, create_date, modify_date, is_instead_of_trigger  
FROM sys.triggers  
WHERE type = 'TR';   
GO  
  
```  
  
```sql  
USE AdventureWorks2012;   
GO  
SELECT  name, object_id, schema_id, parent_object_id, type_desc, create_date, modify_date, is_published  
FROM sys.objects  
WHERE type = 'TR';   
GO  
  
```  
  
```sql  
USE AdventureWorks2012;   
GO  
SELECT OBJECTPROPERTY(OBJECT_ID(N'Person.iuPerson'), 'ExecIsInsteadOfTrigger');   
GO  
  
```  
  
#### <a name="to-view-information-about-events-that-fire-a-dml-trigger"></a><span data-ttu-id="0010f-162">DML 트리거를 실행하는 이벤트에 대한 정보를 보려면</span><span class="sxs-lookup"><span data-stu-id="0010f-162">To view information about events that fire a DML trigger</span></span>  
  
1.  <span data-ttu-id="0010f-163">[!INCLUDE[ssDE](../../includes/ssde-md.md)]에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="0010f-163">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="0010f-164">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0010f-164">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="0010f-165">다음 예 중 하나를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0010f-165">Copy and paste one of the following examples into the query window and click **Execute**.</span></span> <span data-ttu-id="0010f-166">각 예에서는 `iuPerson` 트리거를 실행하는 이벤트를 보는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="0010f-166">Each example shows how you can view the events that fire the `iuPerson` trigger.</span></span>  
  
```sql  
USE AdventureWorks2012;   
GO  
SELECT object_id, type, type_desc, is_trigger_event, event_group_type, event_group_type_desc   
FROM sys.events  
WHERE object_id = OBJECT_ID('Person.iuPerson');   
GO  
```  
  
```sql  
USE AdventureWorks2012;   
GO   
SELECT object_id, type,is_first, is_last  
FROM sys.trigger_events  
WHERE object_id = OBJECT_ID('Person.iuPerson');   
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="0010f-167">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0010f-167">See Also</span></span>  
 <span data-ttu-id="0010f-168">[CREATE TRIGGER&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-trigger-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="0010f-168">[CREATE TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-trigger-transact-sql) </span></span>  
 <span data-ttu-id="0010f-169">[DROP TRIGGER&#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-trigger-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="0010f-169">[DROP TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-trigger-transact-sql) </span></span>  
 <span data-ttu-id="0010f-170">[ENABLE TRIGGER&#40;Transact-SQL&#41;](/sql/t-sql/statements/enable-trigger-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="0010f-170">[ENABLE TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/enable-trigger-transact-sql) </span></span>  
 <span data-ttu-id="0010f-171">[DISABLE TRIGGER&#40;Transact-SQL&#41;](/sql/t-sql/statements/disable-trigger-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="0010f-171">[DISABLE TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/disable-trigger-transact-sql) </span></span>  
 <span data-ttu-id="0010f-172">[EVENTDATA&#40;Transact-SQL&#41;](/sql/t-sql/functions/eventdata-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="0010f-172">[EVENTDATA &#40;Transact-SQL&#41;](/sql/t-sql/functions/eventdata-transact-sql) </span></span>  
 <span data-ttu-id="0010f-173">[sp_rename&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-rename-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="0010f-173">[sp_rename &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-rename-transact-sql) </span></span>  
 <span data-ttu-id="0010f-174">[ALTER TRIGGER&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-trigger-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="0010f-174">[ALTER TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-trigger-transact-sql) </span></span>  
 <span data-ttu-id="0010f-175">[sp_help&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="0010f-175">[sp_help &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-transact-sql) </span></span>  
 <span data-ttu-id="0010f-176">[sp_helptrigger&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helptrigger-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="0010f-176">[sp_helptrigger &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helptrigger-transact-sql) </span></span>  
 <span data-ttu-id="0010f-177">[sys.triggers&#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-triggers-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="0010f-177">[sys.triggers &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-triggers-transact-sql) </span></span>  
 <span data-ttu-id="0010f-178">[sys.trigger_events&#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-trigger-events-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="0010f-178">[sys.trigger_events &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-trigger-events-transact-sql) </span></span>  
 <span data-ttu-id="0010f-179">[sys.sql_modules&#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-sql-modules-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="0010f-179">[sys.sql_modules &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-sql-modules-transact-sql) </span></span>  
 <span data-ttu-id="0010f-180">[sys.assembly_modules&#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-assembly-modules-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="0010f-180">[sys.assembly_modules &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-assembly-modules-transact-sql) </span></span>  
 <span data-ttu-id="0010f-181">[sys.server_triggers&#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-triggers-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="0010f-181">[sys.server_triggers &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-triggers-transact-sql) </span></span>  
 <span data-ttu-id="0010f-182">[sys.server_trigger_events&#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-trigger-events-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="0010f-182">[sys.server_trigger_events &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-trigger-events-transact-sql) </span></span>  
 <span data-ttu-id="0010f-183">[sys.server_sql_modules&#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-sql-modules-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="0010f-183">[sys.server_sql_modules &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-sql-modules-transact-sql) </span></span>  
 <span data-ttu-id="0010f-184">[sys.server_assembly_modules&#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-assembly-modules-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="0010f-184">[sys.server_assembly_modules &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-assembly-modules-transact-sql) </span></span>  
 <span data-ttu-id="0010f-185">[OBJECTPROPERTY&#40;Transact-SQL&#41;](/sql/t-sql/functions/objectpropertyex-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="0010f-185">[OBJECTPROPERTY &#40;Transact-SQL&#41;](/sql/t-sql/functions/objectpropertyex-transact-sql) </span></span>  
 [<span data-ttu-id="0010f-186">OBJECT_DEFINITION&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="0010f-186">OBJECT_DEFINITION &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/object-definition-transact-sql)  
  
  
