---
title: 데이터베이스를 새 위치로 복원(SQL Server) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- restoring databases [SQL Server], moving
- database restores [SQL Server], creating new databases
- restoring [SQL Server], with move
- restoring databases [SQL Server], creating new databases
- database backups [SQL Server], creating new database from
- backing up databases [SQL Server], creating new database from
- restoring databases [SQL Server], renaming
- database creation [SQL Server], restoring with move
ms.assetid: 4da76d61-5e11-4bee-84f5-b305240d9f42
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 89b42f439b5622074327506b9f2ca2b2358cd12f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653463"
---
# <a name="restore-a-database-to-a-new-location-sql-server"></a><span data-ttu-id="46a05-102">데이터베이스를 새 위치로 복원(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="46a05-102">Restore a Database to a New Location (SQL Server)</span></span>
  <span data-ttu-id="46a05-103">이 항목에서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 또는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 을 사용하여 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 에서 [!INCLUDE[tsql](../../includes/tsql-md.md)]데이터베이스를 새 위치로 복원하고 선택적으로 데이터베이스 이름을 바꾸는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="46a05-103">This topic describes how to restore a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database to a new location, and optionally rename the database, in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="46a05-104">데이터베이스를 새 디렉터리 경로로 이동하거나 동일한 서버 인스턴스 또는 다른 서버 인스턴스에 데이터베이스의 복사본을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="46a05-104">You can move a database to a new directory path or create a copy of a database on either the same server instance or a different server instance.</span></span>  
  
 <span data-ttu-id="46a05-105">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="46a05-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="46a05-106">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="46a05-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="46a05-107">제한 사항</span><span class="sxs-lookup"><span data-stu-id="46a05-107">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="46a05-108">필수 구성 요소</span><span class="sxs-lookup"><span data-stu-id="46a05-108">Prerequisites</span></span>](#Prerequisites)  
  
     [<span data-ttu-id="46a05-109">권장 사항</span><span class="sxs-lookup"><span data-stu-id="46a05-109">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="46a05-110">보안</span><span class="sxs-lookup"><span data-stu-id="46a05-110">Security</span></span>](#Security)  
  
-   <span data-ttu-id="46a05-111">**다음을 사용하여 데이터베이스를 새 위치로 복원하고 선택적으로 데이터베이스 이름을 바꿉니다.**</span><span class="sxs-lookup"><span data-stu-id="46a05-111">**To restore a database to a new location, and optionally rename the database, using:**</span></span>  
  
     [<span data-ttu-id="46a05-112">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="46a05-112">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="46a05-113">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="46a05-113">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   [<span data-ttu-id="46a05-114">관련 작업</span><span class="sxs-lookup"><span data-stu-id="46a05-114">Related Tasks</span></span>](#RelatedTasks)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="46a05-115">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="46a05-115">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="46a05-116">제한 사항</span><span class="sxs-lookup"><span data-stu-id="46a05-116">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="46a05-117">전체 데이터베이스 백업을 복원하는 시스템 관리자는 복원할 데이터베이스를 현재 사용 중인 유일한 사람이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="46a05-117">The system administrator restoring a full database backup must be the only person currently using the database to be restored.</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="46a05-118">필수 조건</span><span class="sxs-lookup"><span data-stu-id="46a05-118">Prerequisites</span></span>  
  
-   <span data-ttu-id="46a05-119">전체 또는 대량 로그 복구 모델에서 데이터베이스를 복원하기 전에 활성 트랜잭션 로그를 백업해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="46a05-119">Under the full or bulk-logged recovery model, before you can restore a database, you must back up the active transaction log.</span></span> <span data-ttu-id="46a05-120">자세한 내용은 [트랜잭션 로그 백업&#40;SQL Server&#41;](back-up-a-transaction-log-sql-server.md)데이터베이스를 새 위치로 복원하고 선택적으로 데이터베이스 이름을 바꾸는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="46a05-120">For more information, see [Back Up a Transaction Log &#40;SQL Server&#41;](back-up-a-transaction-log-sql-server.md).</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="46a05-121">권장 사항</span><span class="sxs-lookup"><span data-stu-id="46a05-121">Recommendations</span></span>  
  
-   <span data-ttu-id="46a05-122">암호화된 데이터베이스를 복원하려면 데이터베이스를 암호화하는 데 사용된 인증서 또는 비대칭 키에 대한 액세스 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="46a05-122">To restore a database that is encrypted, you must have access to the certificate or asymmetric key that was used to encrypt the database.</span></span> <span data-ttu-id="46a05-123">인증서 또는 비대칭 키가 없으면 데이터베이스를 복원할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="46a05-123">Without the certificate or asymmetric key, the database cannot be restored.</span></span> <span data-ttu-id="46a05-124">따라서 데이터베이스 암호화 키를 암호화하는 데 사용되는 인증서는 백업이 필요한 동안에는 유지되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="46a05-124">As a result, the certificate that is used to encrypt the database encryption key must be retained as long as the backup is needed.</span></span> <span data-ttu-id="46a05-125">자세한 내용은 [SQL Server Certificates and Asymmetric Keys](../security/sql-server-certificates-and-asymmetric-keys.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="46a05-125">For more information, see [SQL Server Certificates and Asymmetric Keys](../security/sql-server-certificates-and-asymmetric-keys.md).</span></span>  
  
-   <span data-ttu-id="46a05-126">데이터베이스를 이동할 때 고려해야 할 사항에 대한 자세한 내용은 [백업 및 복원으로 데이터베이스 복사](../databases/copy-databases-with-backup-and-restore.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="46a05-126">For information about additional considerations for moving a database, see [Copy Databases with Backup and Restore](../databases/copy-databases-with-backup-and-restore.md).</span></span>  
  
-   <span data-ttu-id="46a05-127">[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 이상 데이터베이스를 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]로 복원하면 데이터베이스가 자동으로 업그레이드됩니다.</span><span class="sxs-lookup"><span data-stu-id="46a05-127">If you restore a [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] or higher  database to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], the database is automatically upgraded.</span></span> <span data-ttu-id="46a05-128">일반적으로 데이터베이스는 즉시 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="46a05-128">Typically, the database becomes available immediately.</span></span> <span data-ttu-id="46a05-129">그러나 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 데이터베이스에 전체 텍스트 인덱스가 있는 경우 업그레이드 프로세스는  **upgrade_option** 서버 속성의 설정에 따라 인덱스를 가져오거나 다시 설정하거나 다시 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="46a05-129">However, if a [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] database has full-text indexes, the upgrade process either imports, resets, or rebuilds them, depending on the setting of the  **upgrade_option** server property.</span></span> <span data-ttu-id="46a05-130">업그레이드 옵션이 가져오기(**upgrade_option** = 2) 또는 다시 작성(**upgrade_option** = 0)으로 설정되어 있는 경우 업그레이드하는 동안 전체 텍스트 인덱스를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="46a05-130">If the upgrade option is set to import (**upgrade_option** = 2) or rebuild (**upgrade_option** = 0), the full-text indexes will be unavailable during the upgrade.</span></span> <span data-ttu-id="46a05-131">인덱싱되는 데이터 양에 따라 가져오기 작업은 몇 시간씩 걸릴 수 있으며 다시 작성 작업은 10배 정도 더 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="46a05-131">Depending the amount of data being indexed, importing can take several hours, and rebuilding can take up to ten times longer.</span></span> <span data-ttu-id="46a05-132">업그레이드 옵션이 가져오기로 설정되어 있으면 전체 텍스트 카탈로그를 사용할 수 없는 경우 관련된 전체 텍스트 인덱스가 다시 작성됩니다.</span><span class="sxs-lookup"><span data-stu-id="46a05-132">Note also that when the upgrade option is set to import, the associated full-text indexes are rebuilt if a full-text catalog is not available.</span></span> <span data-ttu-id="46a05-133">**upgrade_option** 서버 속성의 설정을 변경하려면 [sp_fulltext_service](/sql/relational-databases/system-stored-procedures/sp-fulltext-service-transact-sql)를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="46a05-133">To change the setting of the **upgrade_option** server property, use [sp_fulltext_service](/sql/relational-databases/system-stored-procedures/sp-fulltext-service-transact-sql).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="46a05-134">보안</span><span class="sxs-lookup"><span data-stu-id="46a05-134">Security</span></span>  
 <span data-ttu-id="46a05-135">보안을 위해서는 알 수 없거나 신뢰할 수 없는 출처의 데이터베이스는 연결 또는 복원하지 않는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="46a05-135">For security purposes, we recommend that you do not attach or restore databases from unknown or untrusted sources.</span></span> <span data-ttu-id="46a05-136">이러한 데이터베이스에 포함된 악성 코드가 의도하지 않은 [!INCLUDE[tsql](../../includes/tsql-md.md)] 코드를 실행하거나 스키마 또는 물리적 데이터베이스 구조를 수정하여 오류가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="46a05-136">Such databases could contain malicious code that might execute unintended [!INCLUDE[tsql](../../includes/tsql-md.md)] code or cause errors by modifying the schema or the physical database structure.</span></span> <span data-ttu-id="46a05-137">알 수 없거나 신뢰할 수 없는 소스의 데이터베이스를 사용하기 전에 비프로덕션 서버의 데이터베이스에서 [DBCC CHECKDB](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) 를 실행하여 데이터베이스에서 코드(예: 저장 프로시저 또는 다른 사용자 정의 코드)를 시험해 보세요.</span><span class="sxs-lookup"><span data-stu-id="46a05-137">Before you use a database from an unknown or untrusted source, run [DBCC CHECKDB](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) on the database on a nonproduction server and also examine the code, such as stored procedures or other user-defined code, in the database.</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="46a05-138">권한</span><span class="sxs-lookup"><span data-stu-id="46a05-138">Permissions</span></span>  
 <span data-ttu-id="46a05-139">복원할 데이터베이스가 없으면 CREATE DATABASE 권한이 있어야 RESTORE를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="46a05-139">If the database being restored does not exist, the user must have CREATE DATABASE permissions to be able to execute RESTORE.</span></span> <span data-ttu-id="46a05-140">데이터베이스가 있으면 RESTORE 권한은 기본적으로 **sysadmin** 및 **dbcreator** 고정 서버 역할의 멤버와 데이터베이스의 소유자(**dbo**)에 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="46a05-140">If the database exists, RESTORE permissions default to members of the **sysadmin** and **dbcreator** fixed server roles and the owner (**dbo**) of the database.</span></span>  
  
 <span data-ttu-id="46a05-141">멤버 자격 정보를 서버에서 항상 사용할 수 있는 역할에 RESTORE 권한이 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="46a05-141">RESTORE permissions are given to roles in which membership information is always readily available to the server.</span></span> <span data-ttu-id="46a05-142">고정 데이터베이스 역할의 멤버 자격은 데이터베이스가 액세스 가능한 상태이며 손상되지 않은 경우에만 확인할 수 있는데, RESTORE 실행 시 데이터베이스가 항상 이러한 상태인 것은 아니므로 **db_owner** 고정 데이터베이스 역할의 멤버에게는 RESTORE 권한이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="46a05-142">Because fixed database role membership can be checked only when the database is accessible and undamaged, which is not always the case when RESTORE is executed, members of the **db_owner** fixed database role do not have RESTORE permissions.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="46a05-143">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="46a05-143">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-restore-a-database-to-a-new-location-and-optionally-rename-the-database"></a><span data-ttu-id="46a05-144">데이터베이스를 새 위치로 복원하고 선택적으로 데이터베이스 이름을 바꾸려면</span><span class="sxs-lookup"><span data-stu-id="46a05-144">To restore a database to a new location, and optionally rename the database</span></span>  
  
1.  <span data-ttu-id="46a05-145">[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]의 해당 인스턴스에 연결한 다음 개체 탐색기에서 서버 이름을 클릭하여 서버 트리를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="46a05-145">Connect to the appropriate instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then in Object Explorer, click the server name to expand the server tree.</span></span>  
  
2.  <span data-ttu-id="46a05-146">**데이터베이스**를 마우스 오른쪽 단추로 클릭한 다음 **데이터베이스 복원**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="46a05-146">Right-click **Databases**, and then click **Restore Database**.</span></span> <span data-ttu-id="46a05-147">**데이터베이스 복원** 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="46a05-147">The **Restore Database** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="46a05-148">**일반** 페이지에서 **원본** 섹션을 사용하여 복원할 백업 집합의 원본과 위치를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="46a05-148">On the **General** page, use the **Source** section to specify the source and location of the backup sets to restore.</span></span> <span data-ttu-id="46a05-149">다음 옵션 중 하나를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="46a05-149">Select one of the following options:</span></span>  
  
    -   <span data-ttu-id="46a05-150">**Database**</span><span class="sxs-lookup"><span data-stu-id="46a05-150">**Database**</span></span>  
  
         <span data-ttu-id="46a05-151">복원할 데이터베이스를 드롭다운 목록에서 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="46a05-151">Select the database to restore from the drop-down list.</span></span> <span data-ttu-id="46a05-152">목록에는 **msdb** 백업 기록에 따라 백업된 데이터베이스만 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="46a05-152">The list contains only databases that have been backed up according to the **msdb** backup history.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="46a05-153">백업을 다른 서버에서 가져온 경우 대상 서버에 지정한 데이터베이스에 대한 백업 기록 정보가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="46a05-153">If the backup is taken from a different server, the destination server will not have the backup history information for the specified database.</span></span> <span data-ttu-id="46a05-154">이 경우 **디바이스** 를 선택하여 복원할 파일이나 디바이스를 수동으로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="46a05-154">In this case, select **Device** to manually specify the file or device to restore.</span></span>  
  
    1.  <span data-ttu-id="46a05-155">**디바이스**</span><span class="sxs-lookup"><span data-stu-id="46a05-155">**Device**</span></span>  
  
         <span data-ttu-id="46a05-156">찾아보기( **...** ) 단추를 클릭하여 **백업 디바이스 선택** 대화 상자를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="46a05-156">Click the browse (**...**) button to open the **Select backup devices** dialog box.</span></span> <span data-ttu-id="46a05-157">**백업 미디어 유형** 상자에서 나열된 디바이스 유형 중 하나를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="46a05-157">In the **Backup media type** box, select one of the listed device types.</span></span> <span data-ttu-id="46a05-158">**백업 미디어** 상자에 대해 하나 이상의 디바이스를 선택하려면 **추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="46a05-158">To select one or more devices for the **Backup media** box, click **Add**.</span></span>  
  
         <span data-ttu-id="46a05-159">원하는 디바이스를 **백업 미디어** 목록 상자에 추가한 후 **확인** 을 클릭하여 **일반** 페이지로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="46a05-159">After you add the devices you want to the **Backup media** list box, click **OK** to return to the **General** page.</span></span>  
  
         <span data-ttu-id="46a05-160">**원본: 디바이스: 데이터베이스** 목록 상자에서 복원할 데이터베이스의 이름을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="46a05-160">In the **Source: Device: Database** list box, select the name of the database which should be restored.</span></span>  
  
         <span data-ttu-id="46a05-161">**참고** 이 목록은 **디바이스** 를 선택한 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="46a05-161">**Note** This list is only available when **Device** is selected.</span></span> <span data-ttu-id="46a05-162">선택한 디바이스에 백업이 있는 데이터베이스만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="46a05-162">Only databases that have backups on the selected device will be available.</span></span>  
  
4.  <span data-ttu-id="46a05-163">**대상** 섹션의 **데이터베이스** 상자에는 복원할 데이터베이스의 이름이 자동으로 채워집니다.</span><span class="sxs-lookup"><span data-stu-id="46a05-163">In the **Destination** section, the **Database** box is automatically populated with the name of the database to be restored.</span></span> <span data-ttu-id="46a05-164">데이터베이스의 이름을 변경하려면 **데이터베이스** 상자에 새 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="46a05-164">To change the name of the database, enter the new name in the **Database** box.</span></span>  
  
5.  <span data-ttu-id="46a05-165">**복원 위치** 상자에서 기본값인 **마지막으로 수행된 백업으로** 를 그대로 적용하거나 **시간대** 를 클릭하여 **백업 시간대** 대화 상자에 액세스한 후 복구 동작을 중지할 지정 시간을 직접 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="46a05-165">In the **Restore to** box, leave the default as **To the last backup taken** or click on **Timeline** to access the **Backup Timeline** dialog box to manually select a point in time to stop the recovery action.</span></span> <span data-ttu-id="46a05-166">특정 지정 시간을 지정하는 방법은 [Backup Timeline](backup-timeline.md) 를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="46a05-166">See [Backup Timeline](backup-timeline.md) for more information on designating a specific point in time.</span></span>  
  
6.  <span data-ttu-id="46a05-167">**복원에 사용할 백업 세트** 표에서 복원할 백업을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="46a05-167">In the **Backup sets to restore** grid, select the backups to restore.</span></span> <span data-ttu-id="46a05-168">이 표는 지정한 위치에서 사용 가능한 백업을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="46a05-168">This grid displays the backups available for the specified location.</span></span> <span data-ttu-id="46a05-169">기본적으로 복구 계획이 제안됩니다.</span><span class="sxs-lookup"><span data-stu-id="46a05-169">By default, a recovery plan is suggested.</span></span> <span data-ttu-id="46a05-170">제안된 복구 계획을 재정의하려면 표에서 선택 항목을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="46a05-170">To override the suggested recovery plan, you can change the selections in the grid.</span></span> <span data-ttu-id="46a05-171">이전 백업의 선택이 취소되면 이전 백업 복원에 기반하는 백업도 자동으로 선택이 취소됩니다.</span><span class="sxs-lookup"><span data-stu-id="46a05-171">Backups that depend on the restoration of an earlier backup are automatically deselected when the earlier backup is deselected.</span></span>  
  
     <span data-ttu-id="46a05-172">**복원에 사용할 백업 세트** 표의 열에 대한 자세한 내용은 [데이터베이스 복원&#40;일반 페이지&#41;](../../integration-services/general-page-of-integration-services-designers-options.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="46a05-172">For information about the columns in the **Backup sets to restore** grid, see [Restore Database &#40;General Page&#41;](../../integration-services/general-page-of-integration-services-designers-options.md).</span></span>  
  
7.  <span data-ttu-id="46a05-173">데이터베이스 파일의 새 위치를 지정하려면 **파일** 페이지를 선택한 다음 **모든 파일을 폴더로 위치 변경**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="46a05-173">To specify the new location of the database files, select the **Files** page, and then click **Relocate all files to folder**.</span></span> <span data-ttu-id="46a05-174">**데이터 파일 폴더** 및 **로그 파일 폴더**에 대한 새 위치를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="46a05-174">Provide a new location for the **Data file folder** and **Log file folder**.</span></span> <span data-ttu-id="46a05-175">이 표에 대한 자세한 내용은 [데이터베이스 복원&#40;파일 페이지&#41;](restore-database-files-page.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="46a05-175">For more information about this grid, see [Restore Database &#40;Files Page&#41;](restore-database-files-page.md).</span></span>  
  
8.  <span data-ttu-id="46a05-176">**옵션** 페이지에서 원하는 경우 옵션을 조정합니다.</span><span class="sxs-lookup"><span data-stu-id="46a05-176">On the **Options** page, adjust the options if you want.</span></span> <span data-ttu-id="46a05-177">이러한 옵션에 대한 자세한 내용은 [데이터베이스 복원&#40;옵션 페이지&#41;](restore-database-options-page.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="46a05-177">For more information about these options, see [Restore Database &#40;Options Page&#41;](restore-database-options-page.md).</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="46a05-178">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="46a05-178">Using Transact-SQL</span></span>  
  
#### <a name="to-restore-a-database-to-a-new-location-and-optionally-rename-the-database"></a><span data-ttu-id="46a05-179">데이터베이스를 새 위치로 복원하고 선택적으로 데이터베이스 이름을 바꾸려면</span><span class="sxs-lookup"><span data-stu-id="46a05-179">To restore a database to a new location, and optionally rename the database</span></span>  
  
1.  <span data-ttu-id="46a05-180">복원할 전체 데이터베이스 백업이 포함된 백업 세트에 있는 파일의 논리적 이름과 물리적 이름을 결정합니다(선택 사항).</span><span class="sxs-lookup"><span data-stu-id="46a05-180">Optionally, determine the logical and physical names of the files in the backup set that contains the full database backup that you want to restore.</span></span> <span data-ttu-id="46a05-181">이 문은 백업 세트에 포함된 데이터베이스와 로그 파일의 목록을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="46a05-181">This statement returns a list of the database and log files contained in the backup set.</span></span> <span data-ttu-id="46a05-182">기본 구문은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="46a05-182">The basic syntax is as follows:</span></span>  
  
     <span data-ttu-id="46a05-183">RESTORE FILELISTONLY FROM *<backup_device>* WITH FILE = *backup_set_file_number*</span><span class="sxs-lookup"><span data-stu-id="46a05-183">RESTORE FILELISTONLY FROM *<backup_device>* WITH FILE = *backup_set_file_number*</span></span>  
  
     <span data-ttu-id="46a05-184">여기서 *backup_set_file_number*는 미디어 세트에서의 백업 위치를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="46a05-184">Here, *backup_set_file_number* indicates the position of the backup in the media set.</span></span> <span data-ttu-id="46a05-185">백업 세트의 위치는 [RESTORE HEADERONLY](/sql/t-sql/statements/restore-statements-headeronly-transact-sql) 문을 사용하여 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="46a05-185">You can obtain the position of a backup set by using the [RESTORE HEADERONLY](/sql/t-sql/statements/restore-statements-headeronly-transact-sql) statement.</span></span> <span data-ttu-id="46a05-186">자세한 내용은 [RESTORE 인수&#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-arguments-transact-sql)에서 "백업 세트 지정"을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="46a05-186">For more information, see "Specifying a Backup Set" in [RESTORE Arguments &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-arguments-transact-sql).</span></span>  
  
     <span data-ttu-id="46a05-187">이 문에는 WITH 옵션을 여러 개 지정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="46a05-187">This statement also supports a number of WITH options.</span></span> <span data-ttu-id="46a05-188">자세한 내용은 [RESTORE FILELISTONLY&#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-filelistonly-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="46a05-188">For more information, see [RESTORE FILELISTONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-filelistonly-transact-sql).</span></span>  
  
2.  <span data-ttu-id="46a05-189">[RESTORE DATABASE](/sql/t-sql/statements/restore-statements-transact-sql) 문을 사용하여 전체 데이터베이스 백업을 복원합니다.</span><span class="sxs-lookup"><span data-stu-id="46a05-189">Use the [RESTORE DATABASE](/sql/t-sql/statements/restore-statements-transact-sql) statement to restore the full database backup.</span></span> <span data-ttu-id="46a05-190">기본적으로 데이터 및 로그 파일은 원래 위치로 복원됩니다.</span><span class="sxs-lookup"><span data-stu-id="46a05-190">By default, data and log files are restored to their original locations.</span></span> <span data-ttu-id="46a05-191">데이터베이스의 위치를 다시 지정하려면 MOVE 옵션을 사용하여 각 데이터베이스 파일 위치를 옮기고 기존 파일과의 충돌을 피합니다.</span><span class="sxs-lookup"><span data-stu-id="46a05-191">To relocate a database, use the MOVE option to relocate each of the database files and to avoid collisions with existing files.</span></span>  
  
     <span data-ttu-id="46a05-192">데이터베이스를 새 위치 및 새 이름으로 복원하는 데 사용되는 기본 [!INCLUDE[tsql](../../includes/tsql-md.md)] 구문은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="46a05-192">The basic [!INCLUDE[tsql](../../includes/tsql-md.md)] syntax for restoring the database to a new location and a new name is:</span></span>  
  
     <span data-ttu-id="46a05-193">RESTORE DATABASE *new_database_name*</span><span class="sxs-lookup"><span data-stu-id="46a05-193">RESTORE DATABASE *new_database_name*</span></span>  
  
     <span data-ttu-id="46a05-194">FROM *backup_device* [ ,...*n* ]</span><span class="sxs-lookup"><span data-stu-id="46a05-194">FROM *backup_device* [ ,...*n* ]</span></span>  
  
     <span data-ttu-id="46a05-195">[ WITH</span><span class="sxs-lookup"><span data-stu-id="46a05-195">[ WITH</span></span>  
  
     <span data-ttu-id="46a05-196">{</span><span class="sxs-lookup"><span data-stu-id="46a05-196">{</span></span>  
  
     <span data-ttu-id="46a05-197">[ **복구** | NORECOVERY</span><span class="sxs-lookup"><span data-stu-id="46a05-197">[ **RECOVERY** | NORECOVERY ]</span></span>  
  
     <span data-ttu-id="46a05-198">[ , ] [ FILE ={ *backup_set_file_number* | @*backup_set_file_number* } ]</span><span class="sxs-lookup"><span data-stu-id="46a05-198">[ , ] [ FILE ={ *backup_set_file_number* | @*backup_set_file_number* } ]</span></span>  
  
     <span data-ttu-id="46a05-199">[ , ] MOVE '*logical_file_name_in_backup*' TO '*operating_system_file_name*' [ ,...*n* ]</span><span class="sxs-lookup"><span data-stu-id="46a05-199">[ , ] MOVE '*logical_file_name_in_backup*' TO '*operating_system_file_name*' [ ,...*n* ]</span></span>  
  
     <span data-ttu-id="46a05-200">}</span><span class="sxs-lookup"><span data-stu-id="46a05-200">}</span></span>  
  
     <span data-ttu-id="46a05-201">;</span><span class="sxs-lookup"><span data-stu-id="46a05-201">;</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="46a05-202">데이터베이스 위치를 다른 디스크에 다시 지정할 때는 공간이 충분한지 확인하고 기존 파일과의 충돌 가능성이 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="46a05-202">When preparing to relocate a database on a different disk, you should verify that sufficient space is available and identify any potential collisions with existing files.</span></span> <span data-ttu-id="46a05-203">그러려면 RESTORE DATABASE 문에 사용하려는 것과 동일한 MOVE 매개 변수를 지정하는 [RESTORE VERIFYONLY](/sql/t-sql/statements/restore-statements-verifyonly-transact-sql) 문을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="46a05-203">This involves using a [RESTORE VERIFYONLY](/sql/t-sql/statements/restore-statements-verifyonly-transact-sql) statement that specifies the same MOVE parameters that you plan to use in your RESTORE DATABASE statement.</span></span>  
  
     <span data-ttu-id="46a05-204">다음 표에서는 새 위치로의 데이터베이스 복원과 관련된 이 RESTORE 문 인수에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="46a05-204">The following table describes arguments of this RESTORE statement in terms of restoring a database to a new location.</span></span> <span data-ttu-id="46a05-205">이러한 인수에 대한 자세한 내용은 [RESTORE&#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql)데이터베이스를 새 위치로 복원하고 선택적으로 데이터베이스 이름을 바꾸는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="46a05-205">For more information about these arguments, see [RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql).</span></span>  
  
     <span data-ttu-id="46a05-206">*new_database_name*</span><span class="sxs-lookup"><span data-stu-id="46a05-206">*new_database_name*</span></span>  
     <span data-ttu-id="46a05-207">데이터베이스의 새 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="46a05-207">The new name for the database.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="46a05-208">데이터베이스를 다른 서버 인스턴스로 복원하는 경우 새 이름 대신 원래 데이터베이스 이름을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="46a05-208">If you are restoring the database to a different server instance, you can use the original database name instead of a new name.</span></span>  
  
     <span data-ttu-id="46a05-209">*backup_device* [ `,` ...*n* ]</span><span class="sxs-lookup"><span data-stu-id="46a05-209">*backup_device* [ `,`...*n* ]</span></span>  
     <span data-ttu-id="46a05-210">데이터베이스 백업 복원에 사용할 1-64개의 백업 디바이스 목록(쉼표로 구분됨)을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="46a05-210">Specifies a comma-separated list of from 1 to 64 backup devices from which the database backup is to be restored.</span></span> <span data-ttu-id="46a05-211">물리적 백업 디바이스를 지정하거나, 정의된 경우 해당 논리적 백업 디바이스를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="46a05-211">You can specify a physical backup device, or you can specify a corresponding logical backup device, if defined.</span></span> <span data-ttu-id="46a05-212">물리적 백업 디바이스를 지정하려면 다음 DISK 또는 TAPE 옵션을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="46a05-212">To specify a physical backup device, use the DISK or TAPE option:</span></span>  
  
     <span data-ttu-id="46a05-213">{ DISK | TAPE } `=` *physical_backup_device_name*</span><span class="sxs-lookup"><span data-stu-id="46a05-213">{ DISK | TAPE } `=`*physical_backup_device_name*</span></span>  
  
     <span data-ttu-id="46a05-214">자세한 내용은 [백업 디바이스&#40;SQL Server&#41;](backup-devices-sql-server.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="46a05-214">For more information, see [Backup Devices &#40;SQL Server&#41;](backup-devices-sql-server.md).</span></span>  
  
     <span data-ttu-id="46a05-215">{ **RECOVERY** | NORECOVERY }</span><span class="sxs-lookup"><span data-stu-id="46a05-215">{ **RECOVERY** | NORECOVERY }</span></span>  
     <span data-ttu-id="46a05-216">전체 복구 모델을 사용하는 데이터베이스의 경우, 데이터베이스를 복원한 후 트랜잭션 로그 백업을 적용해야 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="46a05-216">If the database uses the full recovery model, you might need to apply transaction log backups after you restore the database.</span></span> <span data-ttu-id="46a05-217">이 경우 NORECOVERY 옵션을 지정하세요.</span><span class="sxs-lookup"><span data-stu-id="46a05-217">In this case, specify the NORECOVERY option.</span></span>  
  
     <span data-ttu-id="46a05-218">그렇지 않은 경우에는 기본값인 RECOVERY 옵션을 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="46a05-218">Otherwise, use the RECOVERY option, which is the default.</span></span>  
  
     <span data-ttu-id="46a05-219">FILE = { *backup_set_file_number* | @*backup_set_file_number* }</span><span class="sxs-lookup"><span data-stu-id="46a05-219">FILE = { *backup_set_file_number* | @*backup_set_file_number* }</span></span>  
     <span data-ttu-id="46a05-220">복원할 백업 세트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="46a05-220">Identifies the backup set to be restored.</span></span> <span data-ttu-id="46a05-221">예를 들어 *backup_set_file_number* 가 **1** 인 경우는 백업 미디어의 첫 번째 백업 세트를 나타내고 *backup_set_file_number* 가 **2** 인 경우는 두 번째 백업 세트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="46a05-221">For example, a *backup_set_file_number* of **1** indicates the first backup set on the backup medium and a *backup_set_file_number* of **2** indicates the second backup set.</span></span> <span data-ttu-id="46a05-222">백업 세트의 *backup_set_file_number* 는 [RESTORE HEADERONLY](/sql/t-sql/statements/restore-statements-headeronly-transact-sql) 문을 사용하여 가져올 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="46a05-222">You can obtain the *backup_set_file_number* of a backup set by using the [RESTORE HEADERONLY](/sql/t-sql/statements/restore-statements-headeronly-transact-sql) statement.</span></span>  
  
     <span data-ttu-id="46a05-223">이 옵션이 지정되지 않은 경우에는 기본적으로 백업 디바이스의 첫 번째 백업 세트가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="46a05-223">When this option is not specified, the default is to use the first backup set on the backup device.</span></span>  
  
     <span data-ttu-id="46a05-224">자세한 내용은 [RESTORE 인수&#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-arguments-transact-sql)에서 "백업 세트 지정"을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="46a05-224">For more information, see "Specifying a Backup Set," in [RESTORE Arguments &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-arguments-transact-sql).</span></span>  
  
     <span data-ttu-id="46a05-225">' '을 **' *`operating_system_file_name`* '** 로 이동 (... \*\* *`logical_file_name_in_backup`* \*\* `,` *n* ]</span><span class="sxs-lookup"><span data-stu-id="46a05-225">MOVE **'*`logical_file_name_in_backup`*'** TO **'*`operating_system_file_name`*'** [ `,`...*n* ]</span></span>  
     <span data-ttu-id="46a05-226">*logical_file_name_in_backup* 에 지정된 데이터 또는 로그 파일을 *operating_system_file_name*에 지정된 위치로 복원하도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="46a05-226">Specifies that the data or log file specified by *logical_file_name_in_backup* is to be restored to the location specified by *operating_system_file_name*.</span></span> <span data-ttu-id="46a05-227">백업 세트에서 새 위치로 복원할 모든 논리적 파일에 대해 MOVE 문을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="46a05-227">Specify a MOVE statement for every logical file you want to restore from the backup set to a new location.</span></span>  
  
    |<span data-ttu-id="46a05-228">옵션</span><span class="sxs-lookup"><span data-stu-id="46a05-228">Option</span></span>|<span data-ttu-id="46a05-229">Description</span><span class="sxs-lookup"><span data-stu-id="46a05-229">Description</span></span>|  
    |------------|-----------------|  
    |<span data-ttu-id="46a05-230">*logical_file_name_in_backup*</span><span class="sxs-lookup"><span data-stu-id="46a05-230">*logical_file_name_in_backup*</span></span>|<span data-ttu-id="46a05-231">백업 세트에 있는 데이터 또는 로그 파일의 논리적 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="46a05-231">Specifies the logical name of a data or log file in the backup set.</span></span> <span data-ttu-id="46a05-232">백업 세트에 있는 데이터 또는 로그 파일의 논리적 파일 이름은 백업 세트 생성 시 데이터베이스의 해당 논리적 이름과 일치합니다.</span><span class="sxs-lookup"><span data-stu-id="46a05-232">The logical file name of a data or log file in a backup set matches its logical name in the database when the backup set was created.</span></span><br /><br /> <span data-ttu-id="46a05-233">참고: 백업 세트에서 논리적 파일 목록을 가져오려면 [RESTORE FILELISTONLY](/sql/t-sql/statements/restore-statements-filelistonly-transact-sql)를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="46a05-233">Note: To obtain a list of the logical files from the backup set, use [RESTORE FILELISTONLY](/sql/t-sql/statements/restore-statements-filelistonly-transact-sql).</span></span>|  
    |<span data-ttu-id="46a05-234">*operating_system_file_name*</span><span class="sxs-lookup"><span data-stu-id="46a05-234">*operating_system_file_name*</span></span>|<span data-ttu-id="46a05-235">*logical_file_name_in_backup*에 지정된 파일의 새 위치를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="46a05-235">Specifies a new location for the file specified by *logical_file_name_in_backup*.</span></span> <span data-ttu-id="46a05-236">파일이 이 위치로 복원됩니다.</span><span class="sxs-lookup"><span data-stu-id="46a05-236">The file will be restored to this location.</span></span><br /><br /> <span data-ttu-id="46a05-237">*operating_system_file_name* 에서 복원 파일의 새 파일 이름을 지정합니다(선택 사항).</span><span class="sxs-lookup"><span data-stu-id="46a05-237">Optionally, *operating_system_file_name* specifies a new file name for the restored file.</span></span> <span data-ttu-id="46a05-238">이 작업은 동일한 서버 인스턴스에 기존 데이터베이스의 복사본을 만들려는 경우에 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="46a05-238">This is necessary if you are creating a copy of an existing database on the same server instance.</span></span>|  
    |<span data-ttu-id="46a05-239">*n*</span><span class="sxs-lookup"><span data-stu-id="46a05-239">*n*</span></span>|<span data-ttu-id="46a05-240">추가 MOVE 문을 지정할 수 있음을 나타내는 자리 표시자입니다.</span><span class="sxs-lookup"><span data-stu-id="46a05-240">Is a placeholder indicating that you can specify additional MOVE statements.</span></span>|  
  
###  <a name="example-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="46a05-241">예(Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="46a05-241">Example (Transact-SQL)</span></span>  
 <span data-ttu-id="46a05-242">이 예제에서는 `MyAdvWorks` 샘플 데이터베이스의 백업을 복원하여 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 라는 새 데이터베이스를 만듭니다. 여기에는 두 개의 파일 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]_Data 및 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]_Log가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="46a05-242">This example creates a new database named `MyAdvWorks` by restoring a backup of the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] sample database, which includes two files: [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]_Data and [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]_Log.</span></span> <span data-ttu-id="46a05-243">이 데이터베이스는 단순 복구 모델을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="46a05-243">This database uses the simple recovery model.</span></span> <span data-ttu-id="46a05-244">[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 데이터베이스가 이미 서버 인스턴스에 있으므로 백업에 들어 있는 파일을 새 위치로 복원해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="46a05-244">The [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database already exists on the server instance, so the files in the backup must be restored to a new location.</span></span> <span data-ttu-id="46a05-245">RESTORE FILELISTONLY 문은 복원할 데이터베이스에 있는 파일의 수와 이름을 확인하는 데 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="46a05-245">The RESTORE FILELISTONLY statement is used to determine the number and names of the files in the database being restored.</span></span> <span data-ttu-id="46a05-246">데이터베이스 백업은 백업 디바이스에 있는 첫 번째 백업 세트입니다.</span><span class="sxs-lookup"><span data-stu-id="46a05-246">The database backup is the first backup set on the backup device.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="46a05-247">지정 시간 복원을 비롯하여 트랜잭션 로그를 백업 및 복원하는 예에서는 다음 `MyAdvWorks_FullRM` 예와 마찬가지로 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]에서 만든 `MyAdvWorks` 데이터베이스를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="46a05-247">The examples of backing up and restoring the transaction log, including point-in-time restores, use the `MyAdvWorks_FullRM` database that is created from [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] just like the following `MyAdvWorks` example.</span></span> <span data-ttu-id="46a05-248">그러나 다음 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문을 사용하여 결과로 생성된 `MyAdvWorks_FullRM` 데이터베이스에서 전체 복구 모델을 사용하도록 변경해야 합니다. ALTER DATABASE <database_name> SET RECOVERY FULL.</span><span class="sxs-lookup"><span data-stu-id="46a05-248">However, the resulting `MyAdvWorks_FullRM` database must be changed to use the full recovery model by using the following [!INCLUDE[tsql](../../includes/tsql-md.md)] statement: ALTER DATABASE <database_name> SET RECOVERY FULL.</span></span>  
  
```sql  
USE master;  
GO  
-- First determine the number and names of the files in the backup.  
-- AdventureWorks2012_Backup is the name of the backup device.  
RESTORE FILELISTONLY  
   FROM AdventureWorks2012_Backup;  
-- Restore the files for MyAdvWorks.  
RESTORE DATABASE MyAdvWorks  
   FROM AdventureWorks2012_Backup  
   WITH RECOVERY,  
   MOVE 'AdventureWorks2012_Data' TO 'D:\MyData\MyAdvWorks_Data.mdf',   
   MOVE 'AdventureWorks2012_Log' TO 'F:\MyLog\MyAdvWorks_Log.ldf';  
GO  
  
```  
  
 <span data-ttu-id="46a05-249">[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 데이터베이스의 전체 데이터베이스 백업을 만드는 방법의 예제는 [전체 데이터베이스 백업 만들기&#40;SQL Server&#41;](create-a-full-database-backup-sql-server.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="46a05-249">For an example of how to create a full database backup of the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database, see [Create a Full Database Backup &#40;SQL Server&#41;](create-a-full-database-backup-sql-server.md).</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="46a05-250">관련 작업</span><span class="sxs-lookup"><span data-stu-id="46a05-250">Related Tasks</span></span>  
  
-   [<span data-ttu-id="46a05-251">전체 데이터베이스 백업 만들기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="46a05-251">Create a Full Database Backup &#40;SQL Server&#41;</span></span>](create-a-full-database-backup-sql-server.md)  
  
-   [<span data-ttu-id="46a05-252">데이터베이스 백업 복원 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="46a05-252">Restore a Database Backup &#40;SQL Server Management Studio&#41;</span></span>](restore-a-database-backup-using-ssms.md)  
  
-   [<span data-ttu-id="46a05-253">트랜잭션 로그 백업&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="46a05-253">Back Up a Transaction Log &#40;SQL Server&#41;</span></span>](back-up-a-transaction-log-sql-server.md)  
  
-   [<span data-ttu-id="46a05-254">트랜잭션 로그 백업 복원&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="46a05-254">Restore a Transaction Log Backup &#40;SQL Server&#41;</span></span>](restore-a-transaction-log-backup-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="46a05-255">참고 항목</span><span class="sxs-lookup"><span data-stu-id="46a05-255">See Also</span></span>  
 <span data-ttu-id="46a05-256">[다른 서버 인스턴스에서 데이터베이스를 사용할 수 있도록 할 때 메타데이터 관리&#40;SQL Server&#41;](../databases/manage-metadata-when-making-a-database-available-on-another-server.md) </span><span class="sxs-lookup"><span data-stu-id="46a05-256">[Manage Metadata When Making a Database Available on Another Server Instance &#40;SQL Server&#41;](../databases/manage-metadata-when-making-a-database-available-on-another-server.md) </span></span>  
 <span data-ttu-id="46a05-257">[RESTORE&#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="46a05-257">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span></span>  
 [<span data-ttu-id="46a05-258">백업 및 복원으로 데이터베이스 복사</span><span class="sxs-lookup"><span data-stu-id="46a05-258">Copy Databases with Backup and Restore</span></span>](../databases/copy-databases-with-backup-and-restore.md)  
  
  
