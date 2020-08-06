---
title: 분리 및 연결을 사용하여 데이터베이스 업그레이드(Transact-SQL) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- database attaching [SQL Server]
- upgrading databases
- database upgrades [SQL Server]
- database detaching [SQL Server]
- detaching databases [SQL Server]
- attaching databases [SQL Server]
ms.assetid: 99f66ed9-3a75-4e38-ad7d-6c27cc3529a9
author: stevestein
ms.author: sstein
ms.openlocfilehash: d430825fd862ff49b867790f366200a524df3c1c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649095"
---
# <a name="upgrade-a-database-using-detach-and-attach-transact-sql"></a><span data-ttu-id="24aed-102">분리 및 연결을 사용하여 데이터베이스 업그레이드(Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="24aed-102">Upgrade a Database Using Detach and Attach (Transact-SQL)</span></span>
  <span data-ttu-id="24aed-103">이 항목에서는 분리 및 연결 작업을 사용하여 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]에서 데이터베이스를 업그레이드하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="24aed-103">This topic describes how to use detach and attach operations to upgrade a database in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="24aed-104">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]에 연결하면 데이터베이스를 바로 사용할 수 있으며 자동으로 업그레이드됩니다.</span><span class="sxs-lookup"><span data-stu-id="24aed-104">After being attached to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], the database is available immediately and is automatically upgraded.</span></span>  
  
 <span data-ttu-id="24aed-105">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="24aed-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="24aed-106">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="24aed-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="24aed-107">제한 사항</span><span class="sxs-lookup"><span data-stu-id="24aed-107">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="24aed-108">권장 사항</span><span class="sxs-lookup"><span data-stu-id="24aed-108">Recommendations</span></span>](#Recommendations)  
  
-   <span data-ttu-id="24aed-109">**SQL Server 데이터베이스를 업그레이드하려면**</span><span class="sxs-lookup"><span data-stu-id="24aed-109">**To Upgrade a SQL Server Database:**</span></span>  
  
     [<span data-ttu-id="24aed-110">분리 및 연결 작업 사용</span><span class="sxs-lookup"><span data-stu-id="24aed-110">Using detach and attach operations</span></span>](#SSMSProcedure)  
  
-   <span data-ttu-id="24aed-111">**Follow Up:**  [후속 작업: SQL Server 데이터베이스를 업그레이드한 후](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="24aed-111">**Follow Up:**  [After Upgrading a SQL Server Database](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="24aed-112">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="24aed-112">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="24aed-113">제한 사항</span><span class="sxs-lookup"><span data-stu-id="24aed-113">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="24aed-114">시스템 데이터베이스는 연결할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="24aed-114">The system databases cannot be attached.</span></span>  
  
-   <span data-ttu-id="24aed-115">연결 및 분리는 **데이터베이스 간 소유권 체인** 옵션을 0으로 설정하여 데이터베이스에 대한 데이터베이스 간 소유권 체인을 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="24aed-115">Attach and detach disable cross-database ownership chaining for the database by setting its **cross db ownership chaining** option to 0.</span></span> <span data-ttu-id="24aed-116">체인 설정 방법은 [cross db ownership chaining 서버 구성 옵션](../../database-engine/configure-windows/cross-db-ownership-chaining-server-configuration-option.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="24aed-116">For information about enabling chaining, see [cross db ownership chaining Server Configuration Option](../../database-engine/configure-windows/cross-db-ownership-chaining-server-configuration-option.md).</span></span>  
  
-   <span data-ttu-id="24aed-117">분리되지 않고 복사된 복제 데이터베이스를 연결하는 경우에는 다음을 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="24aed-117">When attaching a replicated database that was copied instead of detached:</span></span>  
  
    -   <span data-ttu-id="24aed-118">동일한 서버 인스턴스의 업그레이드된 버전에 데이터베이스를 연결하는 경우 연결 작업이 완료된 후 **sp_vupgrade_replication** 을 실행하여 복제를 업그레이드해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="24aed-118">If you attach the database to an upgraded version of the same server instance, you must execute **sp_vupgrade_replication** to upgrade replication after the attach operation finishes.</span></span> <span data-ttu-id="24aed-119">자세한 내용은 [sp_vupgrade_replication&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-vupgrade-replication-transact-sql)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="24aed-119">For more information, see [sp_vupgrade_replication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-vupgrade-replication-transact-sql).</span></span>  
  
    -   <span data-ttu-id="24aed-120">버전에 관계없이 다른 서버 인스턴스에 데이터베이스를 연결하는 경우 연결 작업이 완료된 후 **sp_removedbreplication** 을 실행하여 복제를 제거해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="24aed-120">If you attach the database to a different server instance (regardless of version), you must execute **sp_removedbreplication** to remove replication after the attach operation finishes.</span></span> <span data-ttu-id="24aed-121">자세한 내용은 [sp_removedbreplication&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="24aed-121">For more information, see [sp_removedbreplication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql).</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="24aed-122">권장 사항</span><span class="sxs-lookup"><span data-stu-id="24aed-122">Recommendations</span></span>  
 <span data-ttu-id="24aed-123">알 수 없거나 신뢰할 수 없는 출처의 데이터베이스는 연결 또는 복원하지 않는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="24aed-123">We recommend that you do not attach or restore databases from unknown or untrusted sources.</span></span> <span data-ttu-id="24aed-124">이러한 데이터베이스에 포함된 악성 코드가 의도하지 않은 [!INCLUDE[tsql](../../includes/tsql-md.md)] 코드를 실행하거나 스키마 또는 물리적 데이터베이스 구조를 수정하여 오류가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="24aed-124">Such databases could contain malicious code that might execute unintended [!INCLUDE[tsql](../../includes/tsql-md.md)] code or cause errors by modifying the schema or the physical database structure.</span></span> <span data-ttu-id="24aed-125">알 수 없거나 신뢰할 수 없는 소스의 데이터베이스를 사용하기 전에 비프로덕션 서버의 데이터베이스에서 [DBCC CHECKDB](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) 를 실행하여 데이터베이스에서 코드(예: 저장 프로시저 또는 다른 사용자 정의 코드)를 시험해 보세요.</span><span class="sxs-lookup"><span data-stu-id="24aed-125">Before you use a database from an unknown or untrusted source, run [DBCC CHECKDB](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) on the database on a nonproduction server and also examine the code, such as stored procedures or other user-defined code, in the database.</span></span>  
  
##  <a name="to-upgrade-a-database-by-using-detach-and-attach"></a><a name="SSMSProcedure"></a> <span data-ttu-id="24aed-126">분리 및 연결을 사용하여 데이터베이스를 업그레이드하려면</span><span class="sxs-lookup"><span data-stu-id="24aed-126">To Upgrade a Database by Using Detach and Attach</span></span>  
  
1.  <span data-ttu-id="24aed-127">데이터베이스를 분리합니다.</span><span class="sxs-lookup"><span data-stu-id="24aed-127">Detach the database.</span></span> <span data-ttu-id="24aed-128">자세한 내용은 [데이터베이스 분리](detach-a-database.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="24aed-128">For more information, see [Detach a Database](detach-a-database.md).</span></span>  
  
2.  <span data-ttu-id="24aed-129">필요에 따라 분리된 데이터베이스 파일 및 로그 파일을 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="24aed-129">Optionally, move the detached database file or files and the log file or files.</span></span>  
  
     <span data-ttu-id="24aed-130">새 로그 파일을 만들려는 경우에도 데이터 파일뿐만 아니라 로그 파일도 이동해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="24aed-130">You should move the log files along with the data files, even if you intend to create new log files.</span></span> <span data-ttu-id="24aed-131">경우에 따라 데이터베이스를 다시 연결하려면 기존 로그 파일이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="24aed-131">In some cases, reattaching a database requires its existing log files.</span></span> <span data-ttu-id="24aed-132">따라서 데이터베이스가 분리된 로그 파일 없이도 성공적으로 연결될 때까지 모든 분리된 로그 파일을 항상 보존하세요.</span><span class="sxs-lookup"><span data-stu-id="24aed-132">Therefore, always keep all the detached log files until the database has been successfully attached without them.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="24aed-133">로그 파일을 지정하지 않고 데이터베이스를 연결할 경우 연결 작업은 원래 위치에서 로그 파일을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="24aed-133">If you try to attach the database without specifying the log file, the attach operation will look for the log file in its original location.</span></span> <span data-ttu-id="24aed-134">로그 파일의 원본이 여전히 원래 위치에 존재하는 경우 해당 복사본이 연결됩니다.</span><span class="sxs-lookup"><span data-stu-id="24aed-134">If the original copy of the log still exists in that location, that copy is attached.</span></span> <span data-ttu-id="24aed-135">원래 로그 파일을 사용하지 않으려면 새 로그 파일의 경로를 지정하거나 로그 파일의 원본을 새 위치로 복사한 후 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="24aed-135">To avoid using the original log file, either specify the path of the new log file or remove the original copy of the log file (after copying it to the new location).</span></span>  
  
3.  <span data-ttu-id="24aed-136">복사한 파일을 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="24aed-136">Attach the copied files to the instance of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="24aed-137">자세한 내용은 [Attach a Database](attach-a-database.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="24aed-137">For more information, see [Attach a Database](attach-a-database.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="24aed-138">예제</span><span class="sxs-lookup"><span data-stu-id="24aed-138">Example</span></span>  
 <span data-ttu-id="24aed-139">다음 예에서는 이전 버전의 SQL Server에서 데이터 복사본을 업그레이드합니다.</span><span class="sxs-lookup"><span data-stu-id="24aed-139">The following example upgrades a copy of a database from an earlier version of SQL Server.</span></span> <span data-ttu-id="24aed-140">[!INCLUDE[tsql](../../includes/tsql-md.md)] 문은 연결한 서버 인스턴스에 연결된 쿼리 편집기 창에서 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="24aed-140">The [!INCLUDE[tsql](../../includes/tsql-md.md)] statements are executed in a Query Editor window that is connected to the server instance to which is attached.</span></span>  
  
1.  <span data-ttu-id="24aed-141">다음 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문을 실행하여 데이터베이스를 분리합니다.</span><span class="sxs-lookup"><span data-stu-id="24aed-141">Detach the database by executing the following [!INCLUDE[tsql](../../includes/tsql-md.md)] statements:</span></span>  
  
    ```  
    USE master;  
    GO  
    EXEC sp_detach_db @dbname = N'MyDatabase';  
    GO  
    ```  
  
2.  <span data-ttu-id="24aed-142">선택한 방법을 사용하여 데이터 및 로그 파일을 새 위치로 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="24aed-142">Using the method of your choice, copy the data and log files to the new location.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="24aed-143">프로덕션 데이터베이스의 경우 데이터베이스와 트랜잭션 로그를 별도의 디스크에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="24aed-143">For a production database, place the database and transaction log on separate disks.</span></span>  
  
     <span data-ttu-id="24aed-144">네트워크를 통해 원격 컴퓨터의 디스크로 파일을 복사하려면 원격 위치의 UNC(Universal Naming Convention) 이름을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="24aed-144">To copy files over the network to a disk on a remote computer, use the universal naming convention (UNC) name of the remote location.</span></span> <span data-ttu-id="24aed-145">UNC 이름은 **\\\\** _Servername_ **\\** _Sharename_ **\\** _Path_ **\\** _Filename_형식으로 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="24aed-145">A UNC name takes the form **\\\\**_Servername_**\\**_Sharename_**\\**_Path_**\\**_Filename_.</span></span> <span data-ttu-id="24aed-146">로컬 하드 디스크에 파일을 쓸 경우 원격 디스크의 파일을 읽거나 파일에 쓰는 데 필요한 해당 권한은 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]인스턴스에서 사용하는 사용자 계정에게 부여되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="24aed-146">As with writing files to the local hard disk, the appropriate permissions that are required to read or write to a file on the remote disk must be granted to the user account used by the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
3.  <span data-ttu-id="24aed-147">다음 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문을 실행하여 이동된 데이터베이스와 필요에 따라 해당 로그를 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="24aed-147">Attach the moved database and, optionally, its log by executing the following [!INCLUDE[tsql](../../includes/tsql-md.md)] statement:</span></span>  
  
    ```  
    USE master;  
    GO  
    CREATE DATABASE MyDatabase   
        ON (FILENAME = 'C:\MySQLServer\MyDatabase.mdf'),  
        (FILENAME = 'C:\MySQLServer\Database.ldf')  
        FOR ATTACH;  
    GO  
    ```  
  
     <span data-ttu-id="24aed-148">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서 새로 연결되는 데이터베이스는 개체 탐색기에 즉시 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="24aed-148">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], a newly attached database is not immediately visible in Object Explorer.</span></span> <span data-ttu-id="24aed-149">데이터베이스를 보려면 개체 탐색기에서 **보기** , **새로 고침**을 차례로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="24aed-149">To view the database, in Object Explorer, click **View,** and then **Refresh**.</span></span> <span data-ttu-id="24aed-150">개체 탐색기에서 **데이터베이스** 노드가 확장될 때 새로 연결된 데이터베이스가 데이터베이스 목록에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="24aed-150">When the **Databases** node is expanded in Object Explorer, the newly attached database now appears in the list of databases.</span></span>  
  
##  <a name="follow-up-after-upgrading-a-sql-server-database"></a><a name="FollowUp"></a> <span data-ttu-id="24aed-151">후속 작업: SQL Server 데이터베이스를 업그레이드한 후</span><span class="sxs-lookup"><span data-stu-id="24aed-151">Follow Up: After Upgrading a SQL Server Database</span></span>  
 <span data-ttu-id="24aed-152">데이터베이스에 전체 텍스트 인덱스가 있는 경우 업그레이드 프로세스는 **upgrade_option** 서버 속성의 설정에 따라 인덱스를 가져오거나, 다시 설정하거나, 다시 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="24aed-152">If the database has full-text indexes, the upgrade process either imports, resets, or rebuilds them, depending on the setting of the **upgrade_option** server property.</span></span> <span data-ttu-id="24aed-153">업그레이드 옵션이 가져오기(**upgrade_option** = 2) 또는 다시 작성(**upgrade_option** = 0)으로 설정되어 있는 경우 업그레이드하는 동안 전체 텍스트 인덱스를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="24aed-153">If the upgrade option is set to import (**upgrade_option** = 2) or rebuild (**upgrade_option** = 0), the full-text indexes will be unavailable during the upgrade.</span></span> <span data-ttu-id="24aed-154">인덱싱되는 데이터 양에 따라 가져오기 작업은 몇 시간씩 걸릴 수 있으며 다시 작성 작업은 10배 정도 더 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="24aed-154">Depending the amount of data being indexed, importing can take several hours, and rebuilding can take up to ten times longer.</span></span> <span data-ttu-id="24aed-155">업그레이드 옵션이 가져오기로 설정되어 있으면 전체 텍스트 카탈로그를 사용할 수 없는 경우 관련된 전체 텍스트 인덱스가 다시 작성됩니다.</span><span class="sxs-lookup"><span data-stu-id="24aed-155">Note also that when the upgrade option is set to import, the associated full-text indexes are rebuilt if a full-text catalog is not available.</span></span> <span data-ttu-id="24aed-156">**upgrade_option** 서버 속성의 설정을 변경하려면 [sp_fulltext_service](/sql/relational-databases/system-stored-procedures/sp-fulltext-service-transact-sql)를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="24aed-156">To change the setting of the **upgrade_option** server property, use [sp_fulltext_service](/sql/relational-databases/system-stored-procedures/sp-fulltext-service-transact-sql).</span></span>  
  
### <a name="database-compatibility-level-after-upgrade"></a><span data-ttu-id="24aed-157">업그레이드 후 데이터베이스 호환성 수준</span><span class="sxs-lookup"><span data-stu-id="24aed-157">Database Compatibility Level After Upgrade</span></span>  
 <span data-ttu-id="24aed-158">사용자 데이터베이스의 호환성 수준이 업그레이드 이전에 100 이상이면 업그레이드 후에도 동일하게 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="24aed-158">If the compatibility level of a user database is 100 or higher before upgrade, it remains the same after upgrade.</span></span> <span data-ttu-id="24aed-159">업그레이드 이전에 호환성 수준이 90이면 업그레이드된 데이터베이스에서는 호환성 수준이 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]에서 지원되는 가장 낮은 호환성 수준인 100으로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="24aed-159">If the compatibility level is 90 before upgrade in the upgraded database, the compatibility level is set to 100, which is the lowest supported compatibility level in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="24aed-160">자세한 내용은 [ALTER DATABASE 호환성 수준&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-compatibility-level)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="24aed-160">For more information, see [ALTER DATABASE Compatibility Level &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-compatibility-level).</span></span>  
  
### <a name="managing-metadata-on-the-upgraded-server-instance"></a><span data-ttu-id="24aed-161">업그레이드한 서버 인스턴스의 메타데이터 관리</span><span class="sxs-lookup"><span data-stu-id="24aed-161">Managing Metadata on the Upgraded Server Instance</span></span>  
 <span data-ttu-id="24aed-162">데이터베이스를 다른 서버 인스턴스에 연결하는 경우 사용자와 애플리케이션에 일관된 환경을 제공하려면 로그인, 작업, 권한 등 데이터베이스의 일부 또는 모든 메타데이터를 다른 서버 인스턴스에서 다시 만들어야 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="24aed-162">When you attach a database onto another server instance, to provide a consistent experience to users and applications, you might have to re-create some or all of the metadata for the database, such as logins, jobs, and permissions, on the other server instance.</span></span> <span data-ttu-id="24aed-163">자세한 내용은 [다른 서버 인스턴스에서 데이터베이스를 사용할 수 있도록 할 때 메타데이터 관리&#40;SQL Server&#41;](manage-metadata-when-making-a-database-available-on-another-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="24aed-163">For more information, see [Manage Metadata When Making a Database Available on Another Server Instance &#40;SQL Server&#41;](manage-metadata-when-making-a-database-available-on-another-server.md).</span></span>  
  
### <a name="service-master-key-and-database-master-key-encryption-changes-from-3des-to-aes"></a><span data-ttu-id="24aed-164">3DES에서 AES로의 서비스 마스터 키 및 데이터베이스 마스터 키 암호화 변경</span><span class="sxs-lookup"><span data-stu-id="24aed-164">Service Master Key and Database Master Key Encryption changes from 3DES to AES</span></span>  
 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] <span data-ttu-id="24aed-165">이상 버전에서는 AES 암호화 알고리즘을 사용하여 SMK(서비스 마스터 키) 및 DMK(데이터베이스 마스터 키)를 보호합니다.</span><span class="sxs-lookup"><span data-stu-id="24aed-165">and higher versions uses the AES encryption algorithm to protect the service master key (SMK) and the database master key (DMK).</span></span> <span data-ttu-id="24aed-166">AES는 이전 버전에서 사용하는 3DES보다 최신 암호화 알고리즘입니다.</span><span class="sxs-lookup"><span data-stu-id="24aed-166">AES is a newer encryption algorithm than 3DES used in earlier versions.</span></span> <span data-ttu-id="24aed-167">데이터베이스가 새 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]인스턴스로 처음으로 연결되거나 복원될 때 데이터베이스 마스터 키(서비스 마스터 키로 암호화됨)의 복사본은 서버에 아직 저장되지 않은 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="24aed-167">When a database is first attached or restored to a new instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], a copy of the database master key (encrypted by the service master key) is not yet stored in the server.</span></span> <span data-ttu-id="24aed-168">DMK(데이터베이스 마스터 키)를 해독하려면 `OPEN MASTER KEY` 문을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="24aed-168">You must use the `OPEN MASTER KEY` statement to decrypt the database master key (DMK).</span></span> <span data-ttu-id="24aed-169">DMK를 해독한 후에는 `ALTER MASTER KEY REGENERATE` 문을 사용하여 자동 해독되도록 옵션을 설정하여 SMK(서비스 마스터 키)로 암호화된 DMK의 복사본을 서버에 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="24aed-169">Once the DMK has been decrypted, you have the option of enabling automatic decryption in the future by using the `ALTER MASTER KEY REGENERATE` statement to provision the server with a copy of the DMK, encrypted with the service master key (SMK).</span></span> <span data-ttu-id="24aed-170">데이터베이스가 이전 버전에서 업그레이드되지 않은 경우에는 DMK를 다시 생성해야 최신 AES 알고리즘을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="24aed-170">When a database has been upgraded from an earlier version, the DMK should be regenerated to use the newer AES algorithm.</span></span> <span data-ttu-id="24aed-171">DMK를 다시 생성하는 방법은 [ALTER MASTER KEY&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-master-key-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="24aed-171">For more information about regenerating the DMK, see [ALTER MASTER KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-master-key-transact-sql).</span></span> <span data-ttu-id="24aed-172">AES로 업그레이드하기 위해 DMK 키를 다시 생성하는 데 소요되는 시간은 DMK에서 보호하는 개체 수에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="24aed-172">The time required to regenerate the DMK key to upgrade to AES depends upon the number of objects protected by the DMK.</span></span> <span data-ttu-id="24aed-173">AES로 업그레이드하기 위해 DMK 키를 다시 생성하는 작업은 한 번만 필요하며 키 회전 전략의 일부로 이후에 수행하는 다시 생성 작업에 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="24aed-173">Regenerating the DMK key to upgrade to AES is only necessary once, and has no impact on future regenerations as part of a key rotation strategy.</span></span>  
  
  
