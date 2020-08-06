---
title: 부분적으로 포함된 데이터베이스로 마이그레이션 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- contained database, migrating to
ms.assetid: 90faac38-f79e-496d-b589-e8b2fe01c562
author: stevestein
ms.author: sstein
ms.openlocfilehash: 6142d46dc0540e5998fa66d463538d1453a17d84
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742160"
---
# <a name="migrate-to-a-partially-contained-database"></a><span data-ttu-id="13ce6-102">Migrate to a Partially Contained Database</span><span class="sxs-lookup"><span data-stu-id="13ce6-102">Migrate to a Partially Contained Database</span></span>
  <span data-ttu-id="13ce6-103">이 항목에서는 부분적으로 포함된 데이터베이스 모델 변경을 준비하는 방법에 대해 설명한 다음 마이그레이션 단계를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="13ce6-103">This topic discusses how to prepare to change to the partially contained database model and then provides the migration steps.</span></span>  
  
 <span data-ttu-id="13ce6-104">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="13ce6-104">**In this topic:**</span></span>  
  
-   [<span data-ttu-id="13ce6-105">데이터베이스 마이그레이션 준비</span><span class="sxs-lookup"><span data-stu-id="13ce6-105">Preparing to Migrate a Database</span></span>](#prepare)  
  
-   [<span data-ttu-id="13ce6-106">포함된 데이터베이스 사용</span><span class="sxs-lookup"><span data-stu-id="13ce6-106">Enable Contained Databases</span></span>](#enable)  
  
-   [<span data-ttu-id="13ce6-107">데이터베이스를 부분적으로 포함된 데이터베이스로 변환</span><span class="sxs-lookup"><span data-stu-id="13ce6-107">Converting a Database to Partially Contained</span></span>](#convert)  
  
-   [<span data-ttu-id="13ce6-108">포함된 데이터베이스 사용자로 사용자 마이그레이션</span><span class="sxs-lookup"><span data-stu-id="13ce6-108">Migrating Users to Contained Database Users</span></span>](#users)  
  
##  <a name="preparing-to-migrate-a-database"></a><a name="prepare"></a> <span data-ttu-id="13ce6-109">데이터베이스 마이그레이션 준비</span><span class="sxs-lookup"><span data-stu-id="13ce6-109">Preparing to Migrate a Database</span></span>  
 <span data-ttu-id="13ce6-110">데이터베이스를 부분적으로 포함된 데이터베이스 모델로 마이그레이션하려고 할 때 다음 항목을 검토합니다.</span><span class="sxs-lookup"><span data-stu-id="13ce6-110">Review the following items when considering migrating a database to the partially contained database model.</span></span>  
  
-   <span data-ttu-id="13ce6-111">부분적으로 포함된 데이터베이스 모델을 이해해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="13ce6-111">You should understand the partially contained database model.</span></span> <span data-ttu-id="13ce6-112">자세한 내용은 [Contained Databases](contained-databases.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="13ce6-112">For more information, see [Contained Databases](contained-databases.md).</span></span>  
  
-   <span data-ttu-id="13ce6-113">부분적으로 포함된 데이터베이스에서만 발생할 수 있는 위험을 이해해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="13ce6-113">You should understand risks that are unique to partially contained databases.</span></span> <span data-ttu-id="13ce6-114">자세한 내용은 [Security Best Practices with Contained Databases](security-best-practices-with-contained-databases.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="13ce6-114">For more information, see [Security Best Practices with Contained Databases](security-best-practices-with-contained-databases.md).</span></span>  
  
-   <span data-ttu-id="13ce6-115">포함된 데이터베이스는 복제, 변경 데이터 캡처 또는 변경 내용 추적 기능을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="13ce6-115">Contained databases do not support replication, change data capture, or change tracking.</span></span> <span data-ttu-id="13ce6-116">데이터베이스에서 이러한 기능을 사용하지 않는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="13ce6-116">Confirm the database does not use these features.</span></span>  
  
-   <span data-ttu-id="13ce6-117">부분적으로 포함된 데이터베이스에 대해 수정된 데이터베이스 기능 목록을 검토합니다.</span><span class="sxs-lookup"><span data-stu-id="13ce6-117">Review the list of database features that are modified for partially contained databases.</span></span> <span data-ttu-id="13ce6-118">자세한 내용은 [수정된 기능&#40;포함된 데이터베이스&#41;](modified-features-contained-database.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="13ce6-118">For more information, see [Modified Features &#40;Contained Database&#41;](modified-features-contained-database.md).</span></span>  
  
-   <span data-ttu-id="13ce6-119">데이터베이스에 포함되지 않은 개체 또는 기능을 찾으려면 [sys.dm_db_uncontained_entities&#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-uncontained-entities-transact-sql) 를 쿼리합니다.</span><span class="sxs-lookup"><span data-stu-id="13ce6-119">Query [sys.dm_db_uncontained_entities &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-uncontained-entities-transact-sql) to find uncontained objects or features in the database.</span></span> <span data-ttu-id="13ce6-120">자세한 내용은 다음을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="13ce6-120">For more information, see.</span></span>  
  
-   <span data-ttu-id="13ce6-121">**database_uncontained_usage** XEvent를 모니터링하여 포함되지 않은 기능이 사용되는 경우를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="13ce6-121">Monitor the **database_uncontained_usage** XEvent to see when uncontained features are used.</span></span>  
  
##  <a name="enable-contained-databases"></a><a name="enable"></a> <span data-ttu-id="13ce6-122">포함된 데이터베이스 사용</span><span class="sxs-lookup"><span data-stu-id="13ce6-122">Enable Contained Databases</span></span>  
 <span data-ttu-id="13ce6-123">포함된 데이터베이스를 만들려면 먼저 포함된 데이터베이스가 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]인스턴스에서 사용 가능하도록 설정되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="13ce6-123">Contained databases must be enabled on the instance of [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], before contained databases can be created.</span></span>  
  
### <a name="enabling-contained-databases-using-transact-sql"></a><span data-ttu-id="13ce6-124">Transact-SQL을 사용하여 포함된 데이터베이스 설정</span><span class="sxs-lookup"><span data-stu-id="13ce6-124">Enabling Contained Databases Using Transact-SQL</span></span>  
 <span data-ttu-id="13ce6-125">다음 예에서는 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]인스턴스에서 포함된 데이터베이스를 사용 가능하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="13ce6-125">The following example enables contained databases on the instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].</span></span>  
  
```sql  
sp_configure 'contained database authentication', 1;  
GO  
RECONFIGURE ;  
GO  
```  
  
#### <a name="enabling-contained-databases-using-management-studio"></a><span data-ttu-id="13ce6-126">SQL Server Management Studio를 사용하여 포함된 데이터베이스 설정</span><span class="sxs-lookup"><span data-stu-id="13ce6-126">Enabling Contained Databases Using Management Studio</span></span>  
 <span data-ttu-id="13ce6-127">다음 예에서는 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]인스턴스에서 포함된 데이터베이스를 사용 가능하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="13ce6-127">The following example enables contained databases on the instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].</span></span>  
  
1.  <span data-ttu-id="13ce6-128">개체 탐색기에서 서버 이름을 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="13ce6-128">In Object Explorer, right-click the server name, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="13ce6-129">**고급** 페이지의 **포함** 섹션에서 **포함된 데이터베이스 사용** 옵션을 **True**로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="13ce6-129">On the **Advanced** page, in the **Containment** section, set the **Enable Contained Databases** option to **True**.</span></span>  
  
3.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
##  <a name="converting-a-database-to-partially-contained"></a><a name="convert"></a> <span data-ttu-id="13ce6-130">데이터베이스를 부분적으로 포함된 데이터베이스로 변환</span><span class="sxs-lookup"><span data-stu-id="13ce6-130">Converting a Database to Partially Contained</span></span>  
 <span data-ttu-id="13ce6-131">**CONTAINMENT** 옵션을 변경하여 데이터베이스를 포함된 데이터베이스로 변환합니다.</span><span class="sxs-lookup"><span data-stu-id="13ce6-131">A database is converted to a contained database by changing the **CONTAINMENT** option.</span></span>  
  
### <a name="converting-a-database-to-partially-contained-using-transact-sql"></a><span data-ttu-id="13ce6-132">Transact-SQL을 사용하여 데이터베이스를 부분적으로 포함된 데이터베이스로 변환</span><span class="sxs-lookup"><span data-stu-id="13ce6-132">Converting a Database to Partially Contained Using Transact-SQL</span></span>  
 <span data-ttu-id="13ce6-133">다음 예에서는 이름이 `Accounting` 인 데이터베이스를 부분적으로 포함된 데이터베이스로 변환합니다.</span><span class="sxs-lookup"><span data-stu-id="13ce6-133">The following example converts a database named `Accounting` to a partially contained database.</span></span>  
  
```sql  
USE [master]  
GO  
ALTER DATABASE [Accounting] SET CONTAINMENT = PARTIAL  
GO  
```  
  
### <a name="converting-a-database-to-partially-contained-using-management-studio"></a><span data-ttu-id="13ce6-134">Management Studio를 사용하여 데이터베이스를 부분적으로 포함된 데이터베이스로 변환</span><span class="sxs-lookup"><span data-stu-id="13ce6-134">Converting a Database to Partially contained Using Management Studio</span></span>  
 <span data-ttu-id="13ce6-135">다음 예에서는 데이터베이스를 부분적으로 포함된 데이터베이스로 변환합니다.</span><span class="sxs-lookup"><span data-stu-id="13ce6-135">The following example converts a database to a partially contained database.</span></span>  
  
1.  <span data-ttu-id="13ce6-136">개체 탐색기에서 **데이터베이스**를 확장하고, 변환할 데이터베이스를 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="13ce6-136">In Object Explorer, expand **Databases**, right-click the database to be converted, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="13ce6-137">**옵션** 페이지에서 **포함 유형** 옵션을 **부분**으로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="13ce6-137">On the **Options** page, change the **Containment type** option to **Partial**.</span></span>  
  
3.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
##  <a name="migrating-users-to-contained-database-users"></a><a name="users"></a> <span data-ttu-id="13ce6-138">포함된 데이터베이스 사용자로 사용자 마이그레이션</span><span class="sxs-lookup"><span data-stu-id="13ce6-138">Migrating Users to Contained Database Users</span></span>  
 <span data-ttu-id="13ce6-139">다음 예에서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 로그인을 기반으로 하는 모든 사용자를 암호를 가진 포함된 데이터베이스 사용자로 마이그레이션합니다.</span><span class="sxs-lookup"><span data-stu-id="13ce6-139">The following example migrates all users that are based on [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] logins to contained database users with passwords.</span></span> <span data-ttu-id="13ce6-140">이 예에서는 활성화되지 않은 로그인을 제외합니다.</span><span class="sxs-lookup"><span data-stu-id="13ce6-140">The example excludes logins that are not enabled.</span></span> <span data-ttu-id="13ce6-141">이 예는 포함된 데이터베이스에서 실행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="13ce6-141">The example must be executed in the contained database.</span></span>  
  
```sql  
DECLARE @username sysname ;  
DECLARE user_cursor CURSOR  
    FOR   
        SELECT dp.name   
        FROM sys.database_principals AS dp  
        JOIN sys.server_principals AS sp   
        ON dp.sid = sp.sid  
        WHERE dp.authentication_type = 1 AND sp.is_disabled = 0;  
OPEN user_cursor  
FETCH NEXT FROM user_cursor INTO @username  
    WHILE @@FETCH_STATUS = 0  
    BEGIN  
        EXECUTE sp_migrate_user_to_contained   
        @username = @username,  
        @rename = N'keep_name',  
        @disablelogin = N'disable_login';  
    FETCH NEXT FROM user_cursor INTO @username  
    END  
CLOSE user_cursor ;  
DEALLOCATE user_cursor ;  
```  
  
## <a name="see-also"></a><span data-ttu-id="13ce6-142">참고 항목</span><span class="sxs-lookup"><span data-stu-id="13ce6-142">See Also</span></span>  
 <span data-ttu-id="13ce6-143">[포함된 데이터베이스](contained-databases.md) </span><span class="sxs-lookup"><span data-stu-id="13ce6-143">[Contained Databases](contained-databases.md) </span></span>  
 <span data-ttu-id="13ce6-144">[sp_migrate_user_to_contained&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-migrate-user-to-contained-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="13ce6-144">[sp_migrate_user_to_contained &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-migrate-user-to-contained-transact-sql) </span></span>  
 [<span data-ttu-id="13ce6-145">sys.dm_db_uncontained_entities&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="13ce6-145">sys.dm_db_uncontained_entities &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-uncontained-entities-transact-sql)  
  
  
