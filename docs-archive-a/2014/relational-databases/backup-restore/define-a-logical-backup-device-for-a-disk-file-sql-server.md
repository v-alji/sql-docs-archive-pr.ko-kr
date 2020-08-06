---
title: 디스크 파일에 대한 논리적 백업 디바이스 정의(SQL Server) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- backup devices [SQL Server], defining
- backup devices [SQL Server], disks
- disk backup devices [SQL Server]
- database backups [SQL Server], disks
- backing up databases [SQL Server], disks
ms.assetid: 86331d43-c738-4523-ae3d-7d6700348ed1
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 8aa92296da81f984f260deace887c15f13443b95
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742340"
---
# <a name="define-a-logical-backup-device-for-a-disk-file-sql-server"></a><span data-ttu-id="c4737-102">Define a Logical Backup Device for a Disk File (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="c4737-102">Define a Logical Backup Device for a Disk File (SQL Server)</span></span>
  <span data-ttu-id="c4737-103">이 항목에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 또는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 을 사용하여 [!INCLUDE[tsql](../../includes/tsql-md.md)]에서 디스크 파일에 대한 논리적 백업 디바이스를 정의하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="c4737-103">This topic describes how to define a logical backup device for a disk file in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="c4737-104">논리적 디바이스는 특정 물리적 백업 디바이스(디스크 파일 또는 테이프 드라이브)를 가리키는 사용자 정의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="c4737-104">A logical device is a user-defined name that points to a specific physical backup device (a disk file or tape drive).</span></span>  <span data-ttu-id="c4737-105">물리적 디바이스의 초기화는 나중에 백업 디바이스에 백업이 기록될 때 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="c4737-105">The initialization of the physical device occurs later, when a backup is written to the backup device.</span></span>  
  
 <span data-ttu-id="c4737-106">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="c4737-106">**In This Topic**</span></span>  
  
-   <span data-ttu-id="c4737-107">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="c4737-107">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="c4737-108">제한 사항</span><span class="sxs-lookup"><span data-stu-id="c4737-108">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="c4737-109">권장 사항</span><span class="sxs-lookup"><span data-stu-id="c4737-109">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="c4737-110">보안</span><span class="sxs-lookup"><span data-stu-id="c4737-110">Security</span></span>](#Security)  
  
-   <span data-ttu-id="c4737-111">**다음을 사용하여 디스크 파일에 대해 논리적 백업 디바이스를 정의합니다.**</span><span class="sxs-lookup"><span data-stu-id="c4737-111">**To define a logical backup device for a disk file, using:**</span></span>  
  
     [<span data-ttu-id="c4737-112">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="c4737-112">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="c4737-113">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="c4737-113">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="c4737-114">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="c4737-114">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="c4737-115">제한 사항</span><span class="sxs-lookup"><span data-stu-id="c4737-115">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="c4737-116">논리적 디바이스 이름은 서버 인스턴스의 모든 논리적 백업 디바이스에서 고유해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c4737-116">The logical device name must be unique among all the logical backup devices on the server instance.</span></span> <span data-ttu-id="c4737-117">기존의 논리적 디바이스 이름을 보려면 [sys.backup_devices](/sql/relational-databases/system-catalog-views/sys-backup-devices-transact-sql) 카탈로그 뷰를 쿼리합니다.</span><span class="sxs-lookup"><span data-stu-id="c4737-117">To view the existing logical device names, query the [sys.backup_devices](/sql/relational-databases/system-catalog-views/sys-backup-devices-transact-sql) catalog view.</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="c4737-118">권장 사항</span><span class="sxs-lookup"><span data-stu-id="c4737-118">Recommendations</span></span>  
  
-   <span data-ttu-id="c4737-119">데이터베이스 데이터 및 로그 디스크가 아닌 다른 디스크를 백업 디스크로 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="c4737-119">We recommend that a backup disk be a different disk than the database data and log disks.</span></span> <span data-ttu-id="c4737-120">이렇게 하면 데이터 또는 로그 디스크가 실패할 경우 백업에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c4737-120">This is necessary to make sure that you can access the backups if the data or log disk fails.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="c4737-121">보안</span><span class="sxs-lookup"><span data-stu-id="c4737-121">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="c4737-122">권한</span><span class="sxs-lookup"><span data-stu-id="c4737-122">Permissions</span></span>  
 <span data-ttu-id="c4737-123">**diskadmin** 고정 서버 역할의 멤버 자격이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="c4737-123">Requires membership in the **diskadmin** fixed server role.</span></span>  
  
 <span data-ttu-id="c4737-124">디스크에 대한 쓰기 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="c4737-124">Requires permission to write to the disk.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="c4737-125">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="c4737-125">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-define-a-logical-backup-device-for-a-disk-file"></a><span data-ttu-id="c4737-126">디스크 파일에 대해 논리적 백업 디바이스를 정의하려면</span><span class="sxs-lookup"><span data-stu-id="c4737-126">To define a logical backup device for a disk file</span></span>  
  
1.  <span data-ttu-id="c4737-127">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]의 해당 인스턴스에 연결한 후 개체 탐색기에서 서버 이름을 클릭하여 서버 트리를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="c4737-127">After connecting to the appropriate instance of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], in Object Explorer, click the server name to expand the server tree.</span></span>  
  
2.  <span data-ttu-id="c4737-128">**서버 개체**를 확장한 다음 **백업 디바이스**를 마우스 오른쪽 단추로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c4737-128">Expand **Server Objects**, and right-click **Backup Devices**.</span></span>  
  
3.  <span data-ttu-id="c4737-129">**새 백업 디바이스**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c4737-129">Click **New Backup Device**.</span></span> <span data-ttu-id="c4737-130">**백업 디바이스** 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="c4737-130">The **Backup Device** dialog box opens.</span></span>  
  
4.  <span data-ttu-id="c4737-131">디바이스 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="c4737-131">Enter a device name.</span></span>  
  
5.  <span data-ttu-id="c4737-132">대상으로 **파일** 을 클릭하고 파일의 전체 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c4737-132">For the destination, click **File** and specify the full path of the file.</span></span>  
  
6.  <span data-ttu-id="c4737-133">새 디바이스를 정의하려면 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c4737-133">To define the new device, click **OK**.</span></span>  
  
 <span data-ttu-id="c4737-134">이 새 디바이스로 백업하려면 **데이터베이스 백업** 대화 상자의 **일반** 페이지에 있는**백업할 위치:** 필드에 디바이스를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="c4737-134">To back up to this new device, add it to the **Back up to:** field in the **Back up Database** (**General**) dialog box.</span></span> <span data-ttu-id="c4737-135">자세한 내용은 [전체 데이터베이스 백업 만들기&#40;SQL Server&#41;](create-a-full-database-backup-sql-server.md)에서 차등 데이터베이스 백업을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c4737-135">For more information, see [Create a Full Database Backup &#40;SQL Server&#41;](create-a-full-database-backup-sql-server.md).</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="c4737-136">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="c4737-136">Using Transact-SQL</span></span>  
  
#### <a name="to-define-a-logical-backup-for-a-disk-file"></a><span data-ttu-id="c4737-137">디스크 파일에 대해 논리적 백업을 정의하려면</span><span class="sxs-lookup"><span data-stu-id="c4737-137">To define a logical backup for a disk file</span></span>  
  
1.  <span data-ttu-id="c4737-138">[!INCLUDE[ssDE](../../includes/ssde-md.md)]에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="c4737-138">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="c4737-139">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c4737-139">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="c4737-140">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c4737-140">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="c4737-141">이 예에서는 [sp_addumpdevice](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql) 를 사용하여 디스크 파일의 논리적 백업 디바이스를 정의하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="c4737-141">This example shows how to use [sp_addumpdevice](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql) to define a logical backup device for a disk file.</span></span> <span data-ttu-id="c4737-142">이 예에서는 `mydiskdump``c:\dump\dump1.bak`라는 디스크 백업 디바이스를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="c4737-142">The example adds the disk backup device named `mydiskdump`, with the physical name `c:\dump\dump1.bak`.</span></span>  
  
```sql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_addumpdevice 'disk', 'mydiskdump', 'c:\dump\dump1.bak' ;  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="c4737-143">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c4737-143">See Also</span></span>  
 <span data-ttu-id="c4737-144">[BACKUP&#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c4737-144">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 <span data-ttu-id="c4737-145">[백업 디바이스&#40;SQL Server&#41;](backup-devices-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="c4737-145">[Backup Devices &#40;SQL Server&#41;](backup-devices-sql-server.md) </span></span>  
 <span data-ttu-id="c4737-146">[sys.backup_devices&#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-backup-devices-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c4737-146">[sys.backup_devices &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-backup-devices-transact-sql) </span></span>  
 <span data-ttu-id="c4737-147">[sp_addumpdevice&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c4737-147">[sp_addumpdevice &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql) </span></span>  
 <span data-ttu-id="c4737-148">[sp_dropdevice&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropdevice-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c4737-148">[sp_dropdevice &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropdevice-transact-sql) </span></span>  
 <span data-ttu-id="c4737-149">[테이프 드라이브에 대한 논리적 백업 디바이스 정의&#40;SQL Server&#41;](define-a-logical-backup-device-for-a-tape-drive-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="c4737-149">[Define a Logical Backup Device for a Tape Drive &#40;SQL Server&#41;](define-a-logical-backup-device-for-a-tape-drive-sql-server.md) </span></span>  
 [<span data-ttu-id="c4737-150">논리적 백업 디바이스의 속성 및 내용 보기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="c4737-150">View the Properties and Contents of a Logical Backup Device &#40;SQL Server&#41;</span></span>](view-the-properties-and-contents-of-a-logical-backup-device-sql-server.md)  
  
  
