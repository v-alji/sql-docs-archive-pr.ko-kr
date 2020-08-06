---
title: DDL 트리거 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- DDL triggers, about DDL triggers
ms.assetid: 1a4a6564-9820-4a14-9305-2c0e9ea37454
author: rothja
ms.author: jroth
ms.openlocfilehash: 6cbcc9f1efc477b8c54ad131f9efa9ff49cc5845
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660399"
---
# <a name="ddl-triggers"></a><span data-ttu-id="1d7b9-102">DDL 트리거</span><span class="sxs-lookup"><span data-stu-id="1d7b9-102">DDL Triggers</span></span>
  <span data-ttu-id="1d7b9-103">DDL 트리거는 다양한 DDL(데이터 정의 언어) 이벤트에 대한 응답으로 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="1d7b9-103">DDL triggers fire in response to a variety of Data Definition Language (DDL) events.</span></span> <span data-ttu-id="1d7b9-104">이러한 이벤트는 주로 CREATE, ALTER, DROP, GRANT, DENY, REVOKE 또는 UPDATE STATISTICS 키워드로 시작하는 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문에 해당합니다.</span><span class="sxs-lookup"><span data-stu-id="1d7b9-104">These events primarily correspond to [!INCLUDE[tsql](../../includes/tsql-md.md)] statements that start with the keywords CREATE, ALTER, DROP, GRANT, DENY, REVOKE or UPDATE STATISTICS.</span></span> <span data-ttu-id="1d7b9-105">DDL과 같은 작업을 수행하는 특정 시스템 저장 프로시저에서 DDL 트리거가 발생할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1d7b9-105">Certain system stored procedures that perform DDL-like operations can also fire DDL triggers.</span></span>  
  
 <span data-ttu-id="1d7b9-106">다음과 같은 경우 DDL 트리거를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="1d7b9-106">Use DDL triggers when you want to do the following:</span></span>  
  
-   <span data-ttu-id="1d7b9-107">데이터베이스 스키마에 대한 특정 변경 작업을 방지하려는 경우</span><span class="sxs-lookup"><span data-stu-id="1d7b9-107">Prevent certain changes to your database schema.</span></span>  
  
-   <span data-ttu-id="1d7b9-108">데이터 스키마가 변경될 때 데이터베이스에서 특정 작업이 수행되게 하려는 경우</span><span class="sxs-lookup"><span data-stu-id="1d7b9-108">Have something occur in the database in response to a change in your database schema.</span></span>  
  
-   <span data-ttu-id="1d7b9-109">데이터베이스 스키마의 변경 내용이나 이벤트를 기록하려는 경우</span><span class="sxs-lookup"><span data-stu-id="1d7b9-109">Record changes or events in the database schema.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="1d7b9-110">DDL 트리거를 테스트하여 실행된 시스템 저장 프로시저에 대한 응답을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="1d7b9-110">Test your DDL triggers to determine their responses to system stored procedures that are run.</span></span> <span data-ttu-id="1d7b9-111">예를 들어 CREATE TYPE 문과 **sp_addtype** 저장 프로시저는 모두 CREATE_TYPE 이벤트에서 생성되는 DDL 트리거를 발생시킵니다.</span><span class="sxs-lookup"><span data-stu-id="1d7b9-111">For example, the CREATE TYPE statement and the **sp_addtype** stored procedure will both fire a DDL trigger that is created on a CREATE_TYPE event.</span></span>  
  
## <a name="types-of-ddl-triggers"></a><span data-ttu-id="1d7b9-112">DDL 트리거 유형</span><span class="sxs-lookup"><span data-stu-id="1d7b9-112">Types of DDL Triggers</span></span>  
 <span data-ttu-id="1d7b9-113">Transact-SQL DDL 트리거</span><span class="sxs-lookup"><span data-stu-id="1d7b9-113">Transact-SQL DDL Trigger</span></span>  
 <span data-ttu-id="1d7b9-114">서버 범위 또는 데이터베이스 범위 이벤트에 대한 응답으로 하나 이상의 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문을 실행하는 특수 유형의 [!INCLUDE[tsql](../../includes/tsql-md.md)] 저장 프로시저입니다.</span><span class="sxs-lookup"><span data-stu-id="1d7b9-114">A special type of [!INCLUDE[tsql](../../includes/tsql-md.md)] stored procedure that executes one or more [!INCLUDE[tsql](../../includes/tsql-md.md)] statements in response to a server-scoped or database-scoped event.</span></span> <span data-ttu-id="1d7b9-115">예를 들어 ALTER SERVER CONFIGURATION과 같은 문을 실행하거나 DROP TABLE을 사용하여 테이블을 삭제하면 DDL 트리거가 실행될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1d7b9-115">For example, a DDL Trigger may fire if a statement such as ALTER SERVER CONFIGURATION is executed or if a table is deleted by using DROP TABLE.</span></span>  
  
 <span data-ttu-id="1d7b9-116">CLR DDL 트리거</span><span class="sxs-lookup"><span data-stu-id="1d7b9-116">CLR DDL Trigger</span></span>  
 <span data-ttu-id="1d7b9-117">CLR 트리거는 [!INCLUDE[tsql](../../includes/tsql-md.md)] 저장 프로시저를 실행하는 대신 .NET Framework에서 생성되고 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 업로드되는 어셈블리 멤버인 관리 코드로 작성된 하나 이상의 메서드를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="1d7b9-117">Instead of executing a [!INCLUDE[tsql](../../includes/tsql-md.md)] stored procedure, a CLR trigger executes one or more methods written in managed code that are members of an assembly created in the .NET Framework and uploaded in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="1d7b9-118">DDL 트리거를 시작하는 DDL 문이 실행된 후에만 DDL 트리거가 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="1d7b9-118">DDL triggers fire only after the DDL statements that trigger them are run.</span></span> <span data-ttu-id="1d7b9-119">DDL 트리거는 INSTEAD OF 트리거로 사용될 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1d7b9-119">DDL triggers cannot be used as INSTEAD OF triggers.</span></span> <span data-ttu-id="1d7b9-120">DDL 트리거는 로컬 또는 전역 임시 테이블과 저장 프로시저에 영향을 주는 이벤트에 대한 응답으로 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1d7b9-120">DDL triggers do not fire in response to events that affect local or global temporary tables and stored procedures.</span></span>  
  
 <span data-ttu-id="1d7b9-121">DDL 트리거는 특수 `inserted` 및 `deleted` 테이블을 만들 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1d7b9-121">DDL triggers do not create the special `inserted` and `deleted` tables.</span></span>  
  
 <span data-ttu-id="1d7b9-122">DDL 트리거를 실행하는 이벤트에 대한 정보 및 트리거로 변경되는 내용은 EVENTDATA 함수를 사용하여 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1d7b9-122">The information about an event that fires a DDL trigger, and the subsequent changes caused by the trigger, is captured by using the EVENTDATA function.</span></span>  
  
 <span data-ttu-id="1d7b9-123">각 DDL 이벤트에 대해 만들 다중 트리거입니다.</span><span class="sxs-lookup"><span data-stu-id="1d7b9-123">Multiple triggers to be created for each DDL event.</span></span>  
  
 <span data-ttu-id="1d7b9-124">DDL 트리거는 DML 트리거와 달리 스키마로 범위가 한정되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1d7b9-124">Unlike DML triggers, DDL triggers are not scoped to schemas.</span></span> <span data-ttu-id="1d7b9-125">DDL 트리거에 대한 메타데이터를 쿼리하는 데 OBJECT_ID, OBJECT_NAME, OBJECTPROPERTY 및 OBJECTPROPERTYEX와 같은 함수는 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1d7b9-125">Therefore, functions such as OBJECT_ID, OBJECT_NAME, OBJECTPROPERTY, and OBJECTPROPERTYEX cannot be used for querying metadata about DDL triggers.</span></span> <span data-ttu-id="1d7b9-126">대신 카탈로그 뷰를 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="1d7b9-126">Use the catalog views instead.</span></span>  
  
 <span data-ttu-id="1d7b9-127">서버 범위 DDL 트리거는 SQL Server Management Studio 개체 탐색기의 **트리거** 폴더에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="1d7b9-127">Server-scoped DDL triggers appear in the SQL Server Management Studio Object Explorer in the **Triggers** folder.</span></span> <span data-ttu-id="1d7b9-128">이 폴더는 **서버 개체** 폴더 아래에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1d7b9-128">This folder is located under the **Server Objects** folder.</span></span> <span data-ttu-id="1d7b9-129">데이터베이스 범위 DDL 트리거는 **데이터베이스 트리거** 폴더에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="1d7b9-129">Database-scoped DDL triggers appear in the **Database Triggers** folder.</span></span> <span data-ttu-id="1d7b9-130">이 폴더는 해당 데이터베이스의 **프로그래밍 기능** 폴더 아래에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1d7b9-130">This folder is located under the **Programmability** folder of the corresponding database.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="1d7b9-131">사용 권한 수준을 높이고 트리거를 실행하더라도 트리거 내의 악성 코드가 실행될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1d7b9-131">Malicious code inside triggers can run under escalated privileges.</span></span> <span data-ttu-id="1d7b9-132">이 위협을 완화하는 방법은 [트리거 보안 관리](manage-trigger-security.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1d7b9-132">For more information about how to help reduce this threat, see [Manage Trigger Security](manage-trigger-security.md).</span></span>  
  
## <a name="ddl-trigger-scope"></a><span data-ttu-id="1d7b9-133">DDL 트리거 범위</span><span class="sxs-lookup"><span data-stu-id="1d7b9-133">DDL Trigger Scope</span></span>  
 <span data-ttu-id="1d7b9-134">DDL 트리거는 현재 데이터베이스나 서버에서 처리되는 [!INCLUDE[tsql](../../includes/tsql-md.md)] 이벤트에 응답하여 시작될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1d7b9-134">DDL triggers can fire in response to a [!INCLUDE[tsql](../../includes/tsql-md.md)] event processed in the current database, or on the current server.</span></span> <span data-ttu-id="1d7b9-135">트리거의 범위는 이벤트에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="1d7b9-135">The scope of the trigger depends on the event.</span></span> <span data-ttu-id="1d7b9-136">예를 들어 CREATE_TABLE 이벤트에 대한 응답으로 시작되도록 만들어진 DDL 트리거는 데이터베이스 또는 서버 인스턴스에서 CREATE_TABLE 이벤트가 발생할 때마다 시작될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1d7b9-136">For example, a DDL trigger created to fire in response to a CREATE_TABLE event can do so whenever a CREATE_TABLE event occurs in the database, or on the server instance.</span></span> <span data-ttu-id="1d7b9-137">CREATE_LOGIN 이벤트에 대한 응답으로 시작되도록 만들어진 DDL 트리거는 서버 인스턴스에서 CREATE_LOGIN 이벤트가 발생할 경우에만 시작될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1d7b9-137">A DDL trigger created to fire in response to a CREATE_LOGIN event can do so only when a CREATE_LOGIN event occurs in the server instance.</span></span>  
  
 <span data-ttu-id="1d7b9-138">다음 예에서는 데이터베이스에서 `safety` 또는 `DROP_TABLE` 이벤트가 발생할 때마다 DDL 트리거 `ALTER_TABLE` 가 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="1d7b9-138">In the following example, DDL trigger `safety` will fire whenever a `DROP_TABLE` or `ALTER_TABLE` event occurs in the database.</span></span>  
  
```  
CREATE TRIGGER safety   
ON DATABASE   
FOR DROP_TABLE, ALTER_TABLE   
AS   
   PRINT 'You must disable Trigger "safety" to drop or alter tables!'   
   ROLLBACK;  
```  
  
 <span data-ttu-id="1d7b9-139">다음 예에서는 현재 서버 인스턴스에서 `CREATE_DATABASE` 이벤트가 발생할 경우 DLL 트리거가 메시지를 출력합니다.</span><span class="sxs-lookup"><span data-stu-id="1d7b9-139">In the following example, a DDL trigger prints a message if any `CREATE_DATABASE` event occurs on the current server instance.</span></span> <span data-ttu-id="1d7b9-140">또한 `EVENTDATA` 함수를 사용하여 해당 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문의 텍스트를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="1d7b9-140">The example uses the `EVENTDATA` function to retrieve the text of the corresponding [!INCLUDE[tsql](../../includes/tsql-md.md)] statement.</span></span> <span data-ttu-id="1d7b9-141">DDL 트리거와 함께 EVENTDATA를 사용하는 방법은 [EVENTDATA 함수 사용](use-the-eventdata-function.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1d7b9-141">For more information about how to use EVENTDATA with DDL triggers, see [Use the EVENTDATA Function](use-the-eventdata-function.md).</span></span>  
  
```  
IF EXISTS (SELECT * FROM sys.server_triggers  
    WHERE name = 'ddl_trig_database')  
DROP TRIGGER ddl_trig_database  
ON ALL SERVER;  
GO  
CREATE TRIGGER ddl_trig_database   
ON ALL SERVER   
FOR CREATE_DATABASE   
AS   
    PRINT 'Database Created.'  
    SELECT EVENTDATA().value('(/EVENT_INSTANCE/TSQLCommand/CommandText)[1]','nvarchar(max)')  
GO  
DROP TRIGGER ddl_trig_database  
ON ALL SERVER;  
GO  
  
```  
  
 <span data-ttu-id="1d7b9-142">[!INCLUDE[tsql](../../includes/tsql-md.md)] 문을 지정 가능한 범위에 매핑하는 목록은 이 항목의 뒷부분에 나오는 "DDL 트리거를 시작하기 위한 특정 DDL 문 선택" 섹션에 제공된 링크를 통해 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1d7b9-142">The lists that map the [!INCLUDE[tsql](../../includes/tsql-md.md)] statements to the scopes that can be specified for them are available through the links provided in the section "Selecting a Particular DDL Statement to Fire a DDL Trigger," later in this topic.</span></span>  
  
 <span data-ttu-id="1d7b9-143">데이터베이스 범위 DDL 트리거는 해당 트리거를 만든 데이터베이스에 개체로 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="1d7b9-143">Database-scoped DDL triggers are stored as objects in the database in which they are created.</span></span> <span data-ttu-id="1d7b9-144">**master** 데이터베이스에서 DDL 트리거를 만들 수 있으며 이러한 DDL 트리거는 사용자가 디자인한 데이터베이스에서 만든 DDL 트리거와 똑같이 동작합니다.</span><span class="sxs-lookup"><span data-stu-id="1d7b9-144">DDL triggers can be created in the **master** database and behave just like those created in user-designed databases.</span></span> <span data-ttu-id="1d7b9-145">DDL 트리거에 대한 정보는 **sys.triggers** 카탈로그 뷰를 쿼리하여 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1d7b9-145">You can obtain information about DDL triggers by querying the **sys.triggers** catalog view.</span></span> <span data-ttu-id="1d7b9-146">**sys.triggers** 는 트리거가 만들어진 데이터베이스 컨텍스트 내에서 또는 **master.sys.triggers**와 같이 데이터베이스 이름을 식별자로 지정하여 쿼리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1d7b9-146">You can query **sys.triggers** within the database context in which the triggers are created or by specifying the database name as an identifier, such as **master.sys.triggers**.</span></span>  
  
 <span data-ttu-id="1d7b9-147">서버 범위 DDL 트리거는 **master** 데이터베이스에 개체로 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="1d7b9-147">Server-scoped DDL triggers are stored as objects in the **master** database.</span></span> <span data-ttu-id="1d7b9-148">그러나 서버 범위 DDL 트리거에 대한 정보는 임의의 데이터베이스 컨텍스트에서 **sys.server_triggers** 카탈로그 뷰를 쿼리하여 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1d7b9-148">However, you can obtain information about server-scoped DDL triggers by querying the **sys.server_triggers** catalog view in any database context.</span></span>  
  
## <a name="specifying-a-transact-sql-statement-or-group-of-statements"></a><span data-ttu-id="1d7b9-149">Transact-SQL 문 또는 문 그룹 지정</span><span class="sxs-lookup"><span data-stu-id="1d7b9-149">Specifying a Transact-SQL Statement or Group of Statements</span></span>  
  
### <a name="selecting-a-particular-ddl-statement-to-fire-a-ddl-trigger"></a><span data-ttu-id="1d7b9-150">DDL 트리거를 시작하기 위한 특정 DDL 문 선택</span><span class="sxs-lookup"><span data-stu-id="1d7b9-150">Selecting a Particular DDL Statement to Fire a DDL Trigger</span></span>  
 <span data-ttu-id="1d7b9-151">하나 이상의 특정 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문이 실행된 이후에 DDL 트리거가 시작되도록 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1d7b9-151">DDL triggers can be designed to fire after one or more particular [!INCLUDE[tsql](../../includes/tsql-md.md)] statements are run.</span></span> <span data-ttu-id="1d7b9-152">이전 예에서 `safety` 트리거는 `DROP_TABLE` 또는 `ALTER_TABLE` 이벤트가 발생한 이후에 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="1d7b9-152">In the previous example, trigger `safety` fires after any `DROP_TABLE` or `ALTER_TABLE` event.</span></span> <span data-ttu-id="1d7b9-153">DDL 트리거를 시작하도록 지정할 수 있는 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문 목록과 트리거 시작 범위는 [DDL 이벤트](ddl-events.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1d7b9-153">For lists of the [!INCLUDE[tsql](../../includes/tsql-md.md)] statements that can be specified to fire a DDL trigger, and the scope at which the trigger can fire, see [DDL Events](ddl-events.md).</span></span>  
  
### <a name="selecting-a-predefined-group-of-ddl-statements-to-fire-a-ddl-trigger"></a><span data-ttu-id="1d7b9-154">DDL 트리거를 시작하기 위한 미리 정의된 DDL 문 그룹 선택</span><span class="sxs-lookup"><span data-stu-id="1d7b9-154">Selecting a Predefined Group of DDL Statements to Fire a DDL Trigger</span></span>  
 <span data-ttu-id="1d7b9-155">DDL 트리거는 미리 정의된 유사 이벤트 그룹에 속한 [!INCLUDE[tsql](../../includes/tsql-md.md)] 이벤트가 실행된 이후에 시작될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1d7b9-155">A DDL trigger can fire after execution of any [!INCLUDE[tsql](../../includes/tsql-md.md)] event that belongs to a predefined grouping of similar events.</span></span> <span data-ttu-id="1d7b9-156">예를 들어 CREATE TABLE, ALTER TABLE 또는 DROP TABLE 문이 실행된 이후에 DDL 트리거가 시작되도록 하려면 CREATE TRIGGER 문에 FOR DDL_TABLE_EVENTS를 지정하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1d7b9-156">For example, if you want a DDL trigger to fire after any CREATE TABLE, ALTER TABLE, or DROP TABLE statement is run, you can specify FOR DDL_TABLE_EVENTS in the CREATE TRIGGER statement.</span></span> <span data-ttu-id="1d7b9-157">CREATE TRIGGER가 실행되면 이벤트 그룹에 속하는 이벤트가 **sys.trigger_events** 카탈로그 뷰에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="1d7b9-157">After CREATE TRIGGER is run, the events that are covered by an event group are added to the **sys.trigger_events** catalog view.</span></span>  
  
 <span data-ttu-id="1d7b9-158">[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]에서 트리거가 이벤트 그룹에 만들어지는 경우 **sys.trigger_events** 에는 이벤트 그룹에 대한 정보가 포함되지 않고 **sys.trigger_events** 에는 이벤트 그룹에 속한 개별 이벤트에 대한 정보만 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="1d7b9-158">In [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], if a trigger is created on an event group, **sys.trigger_events** does not include information about the event group, **sys.trigger_events** includes information only about the individual events covered by that group.</span></span> <span data-ttu-id="1d7b9-159">[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 이상 버전에서 **sys.trigger_events** 는 트리거가 만들어진 이벤트 그룹에 대한 메타데이터와 이벤트 그룹에 속한 개별 이벤트에 대한 메타데이터를 보존합니다.</span><span class="sxs-lookup"><span data-stu-id="1d7b9-159">In [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] and higher, **sys.trigger_events** persists metadata about the event group on which the triggers is created, and also about the individual events that the event group covers.</span></span> <span data-ttu-id="1d7b9-160">따라서 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 이상 버전의 이벤트 그룹에 속한 이벤트에 대한 변경 사항은 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]의 이벤트 그룹에 만들어진 DDL 트리거에 적용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1d7b9-160">Therefore, changes to the events that are covered by event groups in [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] and higher do not apply to DDL triggers that are created on those event groups in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].</span></span>  
  
 <span data-ttu-id="1d7b9-161">DDL 트리거에 사용할 수 있는 미리 정의된 DDL 문 그룹 목록, 이벤트 그룹에 포함된 특정 문 및 이러한 이벤트 그룹을 프로그래밍할 수 있는 범위는 [DDL Event Groups](ddl-event-groups.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="1d7b9-161">For a list of the predefined groups of DDL statements that are available for DDL triggers, the particular statements the event groups cover, and the scopes at which these event groups can be programmed, see [DDL Event Groups](ddl-event-groups.md).</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="1d7b9-162">관련 작업</span><span class="sxs-lookup"><span data-stu-id="1d7b9-162">Related Tasks</span></span>  
  
|<span data-ttu-id="1d7b9-163">Task</span><span class="sxs-lookup"><span data-stu-id="1d7b9-163">Task</span></span>|<span data-ttu-id="1d7b9-164">항목</span><span class="sxs-lookup"><span data-stu-id="1d7b9-164">Topic</span></span>|  
|----------|-----------|  
|<span data-ttu-id="1d7b9-165">DDL 트리거 생성, 수정 또는 삭제하거나 사용하지 않도록 설정하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="1d7b9-165">Describes how to create, modify, delete or disable DDL triggers.</span></span>|[<span data-ttu-id="1d7b9-166">DDL 트리거 구현</span><span class="sxs-lookup"><span data-stu-id="1d7b9-166">Implement DDL Triggers</span></span>](implement-ddl-triggers.md)|  
|<span data-ttu-id="1d7b9-167">CLR DDL 트리거를 만드는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="1d7b9-167">Describes how to create a CLR DDL trigger.</span></span>|[<span data-ttu-id="1d7b9-168">CLR 트리거 만들기</span><span class="sxs-lookup"><span data-stu-id="1d7b9-168">Create CLR Triggers</span></span>](create-clr-triggers.md)|  
|<span data-ttu-id="1d7b9-169">DDL 트리거에 대한 정보를 반환하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="1d7b9-169">Describes how to return information about DDL triggers.</span></span>|[<span data-ttu-id="1d7b9-170">DDL 트리거에 대한 정보 가져오기</span><span class="sxs-lookup"><span data-stu-id="1d7b9-170">Get Information About DDL Triggers</span></span>](get-information-about-ddl-triggers.md)|  
|<span data-ttu-id="1d7b9-171">EVENTDATA 함수를 사용하여 DDL 트리거를 발생하는 이벤트에 대한 정보를 반환하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="1d7b9-171">Describes how to return information about an event that fires a DDL trigger by using the EVENTDATA function.</span></span>|[<span data-ttu-id="1d7b9-172">EVENTDATA 함수 사용</span><span class="sxs-lookup"><span data-stu-id="1d7b9-172">Use the EVENTDATA Function</span></span>](use-the-eventdata-function.md)|  
|<span data-ttu-id="1d7b9-173">트리거 보안을 관리하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="1d7b9-173">Describes how to manage trigger security.</span></span>|[<span data-ttu-id="1d7b9-174">트리거 보안 관리</span><span class="sxs-lookup"><span data-stu-id="1d7b9-174">Manage Trigger Security</span></span>](manage-trigger-security.md)|  
  
## <a name="see-also"></a><span data-ttu-id="1d7b9-175">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1d7b9-175">See Also</span></span>  
 <span data-ttu-id="1d7b9-176">[DML 트리거](dml-triggers.md) </span><span class="sxs-lookup"><span data-stu-id="1d7b9-176">[DML Triggers](dml-triggers.md) </span></span>  
 <span data-ttu-id="1d7b9-177">[LOGON 트리거](logon-triggers.md) </span><span class="sxs-lookup"><span data-stu-id="1d7b9-177">[Logon Triggers](logon-triggers.md) </span></span>  
 [<span data-ttu-id="1d7b9-178">CREATE TRIGGER&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="1d7b9-178">CREATE TRIGGER &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-trigger-transact-sql)  
  
  
