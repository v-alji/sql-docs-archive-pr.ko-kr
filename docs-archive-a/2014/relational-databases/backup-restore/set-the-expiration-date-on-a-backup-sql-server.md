---
title: 백업의 만료 날짜 설정(SQL Server) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- backing up databases [SQL Server], expiration dates
- expiration [SQL Server]
- database backups [SQL Server], expiration dates
ms.assetid: 76e814df-6487-4893-9f09-7759f1863a5c
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 9185222df93e0a1150256535526ba910c593cf6c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649106"
---
# <a name="set-the-expiration-date-on-a-backup-sql-server"></a><span data-ttu-id="14b8c-102">백업의 만료 날짜 설정(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="14b8c-102">Set the Expiration Date on a Backup (SQL Server)</span></span>
  <span data-ttu-id="14b8c-103">이 항목에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 또는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 을 사용하여 [!INCLUDE[tsql](../../includes/tsql-md.md)]에서 백업에 대한 만료 날짜를 설정하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="14b8c-103">This topic describes how to set the expiration date on a backup in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="14b8c-104">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="14b8c-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="14b8c-105">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="14b8c-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="14b8c-106">보안</span><span class="sxs-lookup"><span data-stu-id="14b8c-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="14b8c-107">**다음을 사용하여 백업의 만료 날짜를 설정합니다.**</span><span class="sxs-lookup"><span data-stu-id="14b8c-107">**To set the expiration date on a backup, using:**</span></span>  
  
     [<span data-ttu-id="14b8c-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="14b8c-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="14b8c-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="14b8c-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="14b8c-110">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="14b8c-110">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="14b8c-111">보안</span><span class="sxs-lookup"><span data-stu-id="14b8c-111">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="14b8c-112">권한</span><span class="sxs-lookup"><span data-stu-id="14b8c-112">Permissions</span></span>  
 <span data-ttu-id="14b8c-113">BACKUP DATABASE 및 BACKUP LOG 권한은 기본적으로 **sysadmin** 고정 서버 역할과 **db_owner** 및 **db_backupoperator** 고정 데이터베이스 역할의 멤버로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="14b8c-113">BACKUP DATABASE and BACKUP LOG permissions default to members of the **sysadmin** fixed server role and the **db_owner** and **db_backupoperator** fixed database roles.</span></span>  
  
 <span data-ttu-id="14b8c-114">백업 디바이스의 물리적 파일에서 발생하는 소유권과 사용 권한 문제는 백업 작업에 영향을 미칠 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="14b8c-114">Ownership and permission problems on the backup device's physical file can interfere with a backup operation.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="14b8c-115">는 디바이스를 읽고 쓸 수 있어야 하므로 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 서비스가 실행되는 계정에는 쓰기 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="14b8c-115">must be able to read and write to the device; the account under which the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service runs must have write permissions.</span></span> <span data-ttu-id="14b8c-116">그러나 시스템 테이블의 백업 디바이스에 대한 항목을 추가하는 [sp_addumpdevice](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql)는 파일 액세스 권한을 확인하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="14b8c-116">However, [sp_addumpdevice](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql), which adds an entry for a backup device in the system tables, does not check file access permissions.</span></span> <span data-ttu-id="14b8c-117">백업 디바이스의 물리적 파일에서 발생하는 이러한 문제는 백업 또는 복원을 시도할 때 실제 리소스를 액세스하기 전까지는 발생하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="14b8c-117">Such problems on the backup device's physical file may not appear until the physical resource is accessed when the backup or restore is attempted.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="14b8c-118">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="14b8c-118">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-set-the-expiration-date-on-a-backup"></a><span data-ttu-id="14b8c-119">백업의 만료 날짜를 설정하려면</span><span class="sxs-lookup"><span data-stu-id="14b8c-119">To set the expiration date on a backup</span></span>  
  
1.  <span data-ttu-id="14b8c-120">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../../includes/ssdenoversion-md.md)]의 해당 인스턴스에 연결한 후 개체 탐색기에서 서버 이름을 클릭하여 서버 트리를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="14b8c-120">After connecting to the appropriate instance of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../../includes/ssdenoversion-md.md)], in Object Explorer, click the server name to expand the server tree.</span></span>  
  
2.  <span data-ttu-id="14b8c-121">**데이터베이스**를 확장하고 해당 데이터베이스에 따라 사용자 데이터베이스를 선택하거나 **시스템 데이터베이스** 를 확장한 다음 시스템 데이터베이스를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="14b8c-121">Expand **Databases**, and, depending on the database, either select a user database or expand **System Databases** and select a system database.</span></span>  
  
3.  <span data-ttu-id="14b8c-122">데이터베이스를 마우스 오른쪽 단추로 클릭하고 **태스크**를 가리킨 다음 **백업**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="14b8c-122">Right-click the database, point to **Tasks**, and then click **Back Up**.</span></span> <span data-ttu-id="14b8c-123">**데이터베이스 백업** 대화 상자가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="14b8c-123">The **Back Up Database** dialog box appears.</span></span>  
  
4.  <span data-ttu-id="14b8c-124">**일반** 페이지에서 백업 세트를 다른 백업으로 덮어쓸 수 있는 만료 날짜를 **백업 세트 만료 기한**에 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="14b8c-124">On the **General** page, for **Backup set will expire**, specify an expiration date to indicate when the backup set can be overwritten by another backup:</span></span>  
  
    -   <span data-ttu-id="14b8c-125">백업 세트가 특정 일수가 지난 후에 만료되도록 하려면 **다음 이후** (기본 옵션)를 클릭한 다음 백업 세트를 만든 후 백업 세트가 만료되기까지 경과해야 하는 일수를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="14b8c-125">To have the backup set expire after a specific number of days, click **After** (the default option), and enter the number of days after set creation that the set will expire.</span></span> <span data-ttu-id="14b8c-126">이 값은 0일에서 99999일 사이일 수 있습니다. 값 0일은 백업 세트 기간 제한이 없음을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="14b8c-126">This value can be from 0 to 99999 days; a value of 0 days means that the backup set will never expire.</span></span>  
  
         <span data-ttu-id="14b8c-127">기본값은 **서버 속성** 대화 상자( **데이터베이스 설정** 페이지)의**백업 미디어 기본 보존 기간(일)** 옵션에 설정되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="14b8c-127">The default value is set in the **Default backup media retention (in days)** option of the **Server Properties** dialog box (**Database Settings** page).</span></span> <span data-ttu-id="14b8c-128">이 페이지에 액세스하려면 개체 탐색기에서 서버 이름을 마우스 오른쪽 단추로 클릭하고 속성을 선택한 다음 **데이터베이스 설정** 페이지를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="14b8c-128">To access this, right-click the server name in Object Explorer and select properties; then select the **Database Settings** page.</span></span>  
  
    -   <span data-ttu-id="14b8c-129">백업 세트가 특정 일자에 만료되게 하려면 **날짜**를 클릭한 다음 백업 세트가 만료될 날짜를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="14b8c-129">To have the backup set expire on a specific date, click **On**, and enter the date on which the set will expire.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="14b8c-130">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="14b8c-130">Using Transact-SQL</span></span>  
  
#### <a name="to-set-the-expiration-date-on-a-backup"></a><span data-ttu-id="14b8c-131">백업의 만료 날짜를 설정하려면</span><span class="sxs-lookup"><span data-stu-id="14b8c-131">To set the expiration date on a backup</span></span>  
  
1.  <span data-ttu-id="14b8c-132">[!INCLUDE[ssDE](../../includes/ssde-md.md)]에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="14b8c-132">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="14b8c-133">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="14b8c-133">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="14b8c-134">[BACKUP](/sql/t-sql/statements/backup-transact-sql) 문에서 EXPIREDATE 또는 RETAINDAYS 옵션을 지정하여 [!INCLUDE[ssDEnoversion](../../../includes/ssdenoversion-md.md)] 이 백업을 덮어 쓸 수 있는 시간을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="14b8c-134">In the [BACKUP](/sql/t-sql/statements/backup-transact-sql) statement, specify either the EXPIREDATE or RETAINDAYS option to determine when the [!INCLUDE[ssDEnoversion](../../../includes/ssdenoversion-md.md)] can overwrite the backup.</span></span> <span data-ttu-id="14b8c-135">두 옵션 모두 지정하지 않으면 [미디어 보존](../../database-engine/configure-windows/configure-the-media-retention-server-configuration-option.md) 서버 구성 설정에 따라 만료 날짜가 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="14b8c-135">If neither option is specified, the expiration date is determined by the [media retention](../../database-engine/configure-windows/configure-the-media-retention-server-configuration-option.md) server configuration setting.</span></span> <span data-ttu-id="14b8c-136">이 예에서는 `EXPIREDATE` 옵션을 사용하여 만료 날짜를 2015년 6월 30일(`6/30/2015`)로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="14b8c-136">This example uses the `EXPIREDATE` option to specify an expiration date of June 30, 2015 (`6/30/2015`).</span></span>  
  
```sql  
USE AdventureWorks2012;  
GO  
BACKUP DATABASE AdventureWorks2012  
 TO DISK = 'Z:\SQLServerBackups\AdventureWorks2012.Bak'  
   WITH EXPIREDATE = '6/30/2015' ;  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="14b8c-137">참고 항목</span><span class="sxs-lookup"><span data-stu-id="14b8c-137">See Also</span></span>  
 <span data-ttu-id="14b8c-138">[전체 데이터베이스 백업 만들기&#40;SQL Server&#41;](create-a-full-database-backup-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="14b8c-138">[Create a Full Database Backup &#40;SQL Server&#41;](create-a-full-database-backup-sql-server.md) </span></span>  
 <span data-ttu-id="14b8c-139">[파일 및 파일 그룹 백업&#40;SQL Server&#41;](back-up-files-and-filegroups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="14b8c-139">[Back Up Files and Filegroups &#40;SQL Server&#41;](back-up-files-and-filegroups-sql-server.md) </span></span>  
 <span data-ttu-id="14b8c-140">[트랜잭션 로그 백업&#40;SQL Server&#41;](back-up-a-transaction-log-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="14b8c-140">[Back Up a Transaction Log &#40;SQL Server&#41;](back-up-a-transaction-log-sql-server.md) </span></span>  
 [<span data-ttu-id="14b8c-141">차등 데이터베이스 백업 만들기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="14b8c-141">Create a Differential Database Backup &#40;SQL Server&#41;</span></span>](create-a-differential-database-backup-sql-server.md)  
  
  
