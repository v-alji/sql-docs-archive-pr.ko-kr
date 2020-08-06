---
title: 트리거 보안 관리 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- triggers [SQL Server], security
ms.assetid: e94720a8-a3a2-4364-b0a3-bbe86e3ce4d5
author: rothja
ms.author: jroth
ms.openlocfilehash: fdc176dcad50c3bf28f058c3724a01267975bfc5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660384"
---
# <a name="manage-trigger-security"></a><span data-ttu-id="7cda7-102">트리거 보안 관리</span><span class="sxs-lookup"><span data-stu-id="7cda7-102">Manage Trigger Security</span></span>
  <span data-ttu-id="7cda7-103">기본적으로 두 DML 및 DDL 트리거는 트리거를 호출하는 사용자의 컨텍스트에서 모두 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="7cda7-103">By default, both DML and DDL triggers execute under the context of the user that calls the trigger.</span></span> <span data-ttu-id="7cda7-104">트리거 호출자는 트리거를 실행시키는 문을 실행하는 사용자입니다.</span><span class="sxs-lookup"><span data-stu-id="7cda7-104">The caller of a trigger is the user that executes the statement that causes the trigger to run.</span></span> <span data-ttu-id="7cda7-105">예를 들어 **Mary** 라는 사용자가 DML 트리거 **DML_trigMary** 를 실행시키는 DELETE 문을 실행하면 **DML_trigMary** 내에 있는 코드는 **Mary**에 대한 사용자 권한 컨텍스트에서 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="7cda7-105">For example, if user **Mary** executes a DELETE statement that causes DML trigger **DML_trigMary** to run, the code inside **DML_trigMary** executes in the context of the user privileges for **Mary**.</span></span> <span data-ttu-id="7cda7-106">이러한 기본 동작은 데이터베이스나 서버 인스턴스에 악의적인 코드를 침투시키려는 사용자가 이용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7cda7-106">This default behavior can be exploited by users who want to introduce malicious code in the database or server instance.</span></span> <span data-ttu-id="7cda7-107">예를 들어 다음 DDL 트리거는 `JohnDoe`라는 사용자가 만든 것입니다.</span><span class="sxs-lookup"><span data-stu-id="7cda7-107">For example, the following DDL trigger is created by user `JohnDoe`:</span></span>  
  
 `CREATE TRIGGER DDL_trigJohnDoe`  
  
 `ON DATABASE`  
  
 `FOR ALTER_TABLE`  
  
 `AS`  
  
 `GRANT CONTROL SERVER TO JohnDoe ;`  
  
 `GO`  
  
 <span data-ttu-id="7cda7-108">이 트리거는 `GRANT CONTROL SERVER` sysadmin **고정 서버 역할의 멤버처럼** 문을 실행할 권한이 있는 사용자가 `ALTER TABLE` 문을 실행하면 바로 `JohnDoe` 에게 `CONTROL SERVER` 권한이 부여됨을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="7cda7-108">What this trigger means is that as soon as a user that has permission to execute a `GRANT CONTROL SERVER` statement, such as a member of the **sysadmin** fixed server role, executes an `ALTER TABLE` statement, `JohnDoe` is granted `CONTROL SERVER` permission.</span></span> <span data-ttu-id="7cda7-109">즉, `JohnDoe` 는 `CONTROL SERVER` 권한을 자신에게 부여할 수 없지만 자신에게 이 권한을 부여한 트리거 코드가 에스컬레이션된 권한으로 실행될 수 있도록 설정했습니다.</span><span class="sxs-lookup"><span data-stu-id="7cda7-109">In other words, although `JohnDoe` cannot grant `CONTROL SERVER` permission to himself, he enabled the trigger code that grants him this permission to execute under escalated privileges.</span></span> <span data-ttu-id="7cda7-110">DML과 DDL 트리거 모두 이러한 유형의 보안 위협에 노출되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7cda7-110">Both DML and DDL triggers are open to this kind of security threat.</span></span>  
  
## <a name="trigger-security-best-practices"></a><span data-ttu-id="7cda7-111">트리거 보안을 위한 가장 적절한 방법</span><span class="sxs-lookup"><span data-stu-id="7cda7-111">Trigger Security Best Practices</span></span>  
 <span data-ttu-id="7cda7-112">다음 방법을 사용하여 트리거 코드가 에스컬레이션된 권한으로 실행되는 것을 방지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7cda7-112">You can take the following measures to prevent trigger code from executing under escalated privileges:</span></span>  
  
-   <span data-ttu-id="7cda7-113">[sys.triggers](/sql/relational-databases/system-catalog-views/sys-triggers-transact-sql) 및 [sys.server_triggers](/sql/relational-databases/system-catalog-views/sys-server-triggers-transact-sql) 카탈로그 뷰를 쿼리하여 데이터베이스 및 서버 인스턴스에 있는 DML 및 DDL 트리거를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="7cda7-113">Be aware of the DML and DDL triggers that exist in the database and on the server instance by querying the [sys.triggers](/sql/relational-databases/system-catalog-views/sys-triggers-transact-sql) and [sys.server_triggers](/sql/relational-databases/system-catalog-views/sys-server-triggers-transact-sql) catalog views.</span></span> <span data-ttu-id="7cda7-114">다음 쿼리는 현재 데이터베이스에 모든 DML 및 데이터베이스 수준 DDL 트리거를 반환하고 서버 인스턴스에 모든 서버 수준 DDL 트리거를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="7cda7-114">The following query returns all DML and database-level DDL triggers in the current database, and all server-level DDL triggers on the server instance:</span></span>  
  
    ```  
    SELECT type, name, parent_class_desc FROM sys.triggers  
    UNION  
    SELECT type, name, parent_class_desc FROM sys.server_triggers ;  
    ```  
  
-   <span data-ttu-id="7cda7-115">[DISABLE TRIGGER](/sql/t-sql/statements/disable-trigger-transact-sql) 를 사용하여 트리거가 에스컬레이션된 권한으로 실행되는 경우 데이터베이스나 서버의 무결성에 손상을 줄 수 있는 트리거를 비활성화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7cda7-115">Use [DISABLE TRIGGER](/sql/t-sql/statements/disable-trigger-transact-sql) to disable triggers that can harm the integrity of the database or server if the triggers execute under escalated privileges.</span></span> <span data-ttu-id="7cda7-116">다음 문은 현재 데이터베이스에서 모든 데이터베이스 수준 DDL 트리거를 비활성화합니다.</span><span class="sxs-lookup"><span data-stu-id="7cda7-116">The following statement disables all database-level DDL triggers in the current database:</span></span>  
  
    ```  
    DISABLE TRIGGER ALL ON DATABASE  
    ```  
  
     <span data-ttu-id="7cda7-117">이 문은 서버 인스턴스에서 모든 서버 수준 DDL 트리거를 비활성화합니다.</span><span class="sxs-lookup"><span data-stu-id="7cda7-117">This statement disables all server-level DDL triggers on the server instance:</span></span>  
  
    ```  
    DISABLE TRIGGER ALL ON ALL SERVER  
    ```  
  
     <span data-ttu-id="7cda7-118">이 문은 현재 데이터베이스에서 모든 DML 트리거를 비활성화합니다.</span><span class="sxs-lookup"><span data-stu-id="7cda7-118">This statement disables all DML triggers in the current database:</span></span>  
  
    ```  
    DECLARE @schema_name sysname, @trigger_name sysname, @object_name sysname ;  
    DECLARE @sql nvarchar(max) ;  
    DECLARE trig_cur CURSOR FORWARD_ONLY READ_ONLY FOR  
        SELECT SCHEMA_NAME(schema_id) AS schema_name,  
            name AS trigger_name,  
            OBJECT_NAME(parent_object_id) as object_name  
        FROM sys.objects WHERE type in ('TR', 'TA') ;  
  
    OPEN trig_cur ;  
    FETCH NEXT FROM trig_cur INTO @schema_name, @trigger_name, @object_name ;  
  
    WHILE @@FETCH_STATUS = 0  
    BEGIN  
        SELECT @sql = 'DISABLE TRIGGER ' + QUOTENAME(@schema_name) + '.'  
            + QUOTENAME(@trigger_name) +  
            ' ON ' + QUOTENAME(@schema_name) + '.'   
            + QUOTENAME(@object_name) + ' ; ' ;  
        EXEC (@sql) ;  
        FETCH NEXT FROM trig_cur INTO @schema_name, @trigger_name, @object_name ;  
    END  
    GO  
  
    -- Verify triggers are disabled. Should return an empty result set.  
    SELECT * FROM sys.triggers WHERE is_disabled = 0 ;  
    GO  
  
    CLOSE trig_cur ;  
    DEALLOCATE trig_cur;  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="7cda7-119">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7cda7-119">See Also</span></span>  
 <span data-ttu-id="7cda7-120">[CREATE TRIGGER&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-trigger-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="7cda7-120">[CREATE TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-trigger-transact-sql) </span></span>  
 <span data-ttu-id="7cda7-121">[DML 트리거](../triggers/dml-triggers.md) </span><span class="sxs-lookup"><span data-stu-id="7cda7-121">[DML Triggers](../triggers/dml-triggers.md) </span></span>  
 [<span data-ttu-id="7cda7-122">DDL 트리거</span><span class="sxs-lookup"><span data-stu-id="7cda7-122">DDL Triggers</span></span>](../triggers/ddl-triggers.md)  
  
  
