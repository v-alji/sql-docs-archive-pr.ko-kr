---
title: 테이프 드라이브에 대한 논리적 백업 디바이스 정의(SQL Server) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- backup devices [SQL Server], defining
- backup devices [SQL Server], tapes
- backing up databases [SQL Server], tapes
- database backups [SQL Server], tapes
- tape backup devices, creating
ms.assetid: 66f36e1d-0287-4fac-8a51-71f9f0d7ad5b
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 8728df2cc0b5907e51da84ed9e77d897a1718d36
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742335"
---
# <a name="define-a-logical-backup-device-for-a-tape-drive-sql-server"></a><span data-ttu-id="af8db-102">테이프 드라이브에 대한 논리적 백업 디바이스 정의(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="af8db-102">Define a Logical Backup Device for a Tape Drive (SQL Server)</span></span>
  <span data-ttu-id="af8db-103">이 항목에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 또는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 을 사용하여 [!INCLUDE[tsql](../../includes/tsql-md.md)]에서 테이프 드라이브에 대한 논리적 백업 디바이스를 정의하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="af8db-103">This topic describes how to define a logical backup device for a tape drive in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="af8db-104">논리적 디바이스는 특정 물리적 백업 디바이스(디스크 파일 또는 테이프 드라이브)를 가리키는 사용자 정의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="af8db-104">A logical device is a user-defined name that points to a specific physical backup device (a disk file or tape drive).</span></span>  <span data-ttu-id="af8db-105">물리적 디바이스의 초기화는 나중에 백업 디바이스에 백업이 기록될 때 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="af8db-105">The initialization of the physical device occurs later, when a backup is written to the backup device.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="af8db-106">테이프 백업 디바이스에 대한 지원은 이후 버전의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 제거될 예정입니다.</span><span class="sxs-lookup"><span data-stu-id="af8db-106">Support for tape backup devices will be removed in a future version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="af8db-107">새 개발 작업에서는 이 기능을 사용하지 않도록 하고, 현재 이 기능을 사용하는 애플리케이션은 수정하세요.</span><span class="sxs-lookup"><span data-stu-id="af8db-107">Avoid using this feature in new development work, and plan to modify applications that currently use this feature.</span></span>  
  
 <span data-ttu-id="af8db-108">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="af8db-108">**In This Topic**</span></span>  
  
-   <span data-ttu-id="af8db-109">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="af8db-109">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="af8db-110">제한 사항</span><span class="sxs-lookup"><span data-stu-id="af8db-110">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="af8db-111">보안</span><span class="sxs-lookup"><span data-stu-id="af8db-111">Security</span></span>](#Security)  
  
-   <span data-ttu-id="af8db-112">**다음을 사용하여 테이프 드라이브에 대한 논리적 백업 디바이스를 정의합니다.**</span><span class="sxs-lookup"><span data-stu-id="af8db-112">**To define a logical backup device for a tape drive, using:**</span></span>  
  
     [<span data-ttu-id="af8db-113">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="af8db-113">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="af8db-114">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="af8db-114">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="af8db-115">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="af8db-115">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="af8db-116">제한 사항</span><span class="sxs-lookup"><span data-stu-id="af8db-116">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="af8db-117">테이프 드라이브 또는 드라이브는 Microsoft Windows 운영 체제에 의해 지원되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="af8db-117">The tape drive or drives must be supported by the Microsoft Windows operating system.</span></span>  
  
-   <span data-ttu-id="af8db-118">테이프 디바이스는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 인스턴스를 실행하는 컴퓨터에 물리적으로 연결되어 있어야 하며</span><span class="sxs-lookup"><span data-stu-id="af8db-118">The tape device must be connected physically to the computer that is running an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="af8db-119">원격 테이프 디바이스로 백업할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="af8db-119">Backing up to remote tape devices is not supported.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="af8db-120">보안</span><span class="sxs-lookup"><span data-stu-id="af8db-120">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="af8db-121">권한</span><span class="sxs-lookup"><span data-stu-id="af8db-121">Permissions</span></span>  
 <span data-ttu-id="af8db-122">**diskadmin** 고정 서버 역할의 멤버 자격이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="af8db-122">Requires membership in the **diskadmin** fixed server role.</span></span>  
  
 <span data-ttu-id="af8db-123">디스크에 대한 쓰기 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="af8db-123">Requires permission to write to the disk.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="af8db-124">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="af8db-124">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-define-a-logical-backup-device-for-a-tape-drive"></a><span data-ttu-id="af8db-125">테이프 드라이브에 대한 논리적 백업 디바이스를 정의하려면</span><span class="sxs-lookup"><span data-stu-id="af8db-125">To define a logical backup device for a tape drive</span></span>  
  
1.  <span data-ttu-id="af8db-126">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]의 해당 인스턴스에 연결한 후 개체 탐색기에서 서버 이름을 클릭하여 서버 트리를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="af8db-126">After connecting to the appropriate instance of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], in Object Explorer, click the server name to expand the server tree.</span></span>  
  
2.  <span data-ttu-id="af8db-127">**서버 개체**를 확장한 다음 마우스 오른쪽 단추로 **백업 디바이스**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="af8db-127">Expand **Server Objects**, and then right-click **Backup Devices**.</span></span>  
  
3.  <span data-ttu-id="af8db-128">**새 백업 디바이스**를 클릭하면 **백업 디바이스** 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="af8db-128">Click **New Backup Device**, which opens the **Backup Device** dialog box.</span></span>  
  
4.  <span data-ttu-id="af8db-129">디바이스 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="af8db-129">Enter a device name.</span></span>  
  
5.  <span data-ttu-id="af8db-130">대상에 대해 **테이프** 를 클릭하고 다른 백업 디바이스에 연결되어 있지 않은 테이프 드라이브를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="af8db-130">For the destination, click **Tape** and select a tape drive that is not already associated with another backup device.</span></span> <span data-ttu-id="af8db-131">사용 가능한 테이프 드라이브가 없으면 **테이프** 옵션은 비활성 상태로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="af8db-131">If no such tape drives are available, the **Tape** option is inactive.</span></span>  
  
6.  <span data-ttu-id="af8db-132">새 디바이스를 정의하려면 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="af8db-132">To define the new device, click **OK**.</span></span>  
  
 <span data-ttu-id="af8db-133">이 새 디바이스로 백업하려면 **데이터베이스 백업** 대화 상자의 **일반** 페이지에 있는**백업할 위치:** 필드에 디바이스를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="af8db-133">To back up to this new device, add it to the **Back up to:** field in the **Back up Database** (**General**) dialog box.</span></span> <span data-ttu-id="af8db-134">자세한 내용은 [전체 데이터베이스 백업 만들기&#40;SQL Server&#41;](create-a-full-database-backup-sql-server.md)에서 차등 데이터베이스 백업을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="af8db-134">For more information, see [Create a Full Database Backup &#40;SQL Server&#41;](create-a-full-database-backup-sql-server.md).</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="af8db-135">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="af8db-135">Using Transact-SQL</span></span>  
  
#### <a name="to-define-a-logical-backup-device-for-a-tape-drive"></a><span data-ttu-id="af8db-136">테이프 드라이브에 대한 논리적 백업 디바이스를 정의하려면</span><span class="sxs-lookup"><span data-stu-id="af8db-136">To define a logical backup device for a tape drive</span></span>  
  
1.  <span data-ttu-id="af8db-137">[!INCLUDE[ssDE](../../includes/ssde-md.md)]에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="af8db-137">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="af8db-138">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="af8db-138">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="af8db-139">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="af8db-139">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="af8db-140">이 예에서는 [sp_addumpdevice](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql) 를 사용하여 테이프의 논리적 백업 디바이스를 정의하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="af8db-140">This example shows how to use [sp_addumpdevice](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql) to define a logical backup device for a tape.</span></span> <span data-ttu-id="af8db-141">이 예에서는 `tapedump1`라는 물리적 이름으로 `\\.\tape0`이라는 테이프 백업 디바이스를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="af8db-141">The example adds the tape backup device named `tapedump1`, with the physical name `\\.\tape0`.</span></span>  
  
```sql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_addumpdevice 'tape', 'tapedump1', '\\.\tape0' ;  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="af8db-142">참고 항목</span><span class="sxs-lookup"><span data-stu-id="af8db-142">See Also</span></span>  
 <span data-ttu-id="af8db-143">[BACKUP&#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="af8db-143">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 <span data-ttu-id="af8db-144">[sys.backup_devices&#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-backup-devices-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="af8db-144">[sys.backup_devices &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-backup-devices-transact-sql) </span></span>  
 <span data-ttu-id="af8db-145">[sp_addumpdevice&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="af8db-145">[sp_addumpdevice &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql) </span></span>  
 <span data-ttu-id="af8db-146">[sp_dropdevice&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropdevice-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="af8db-146">[sp_dropdevice &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropdevice-transact-sql) </span></span>  
 <span data-ttu-id="af8db-147">[백업 디바이스&#40;SQL Server&#41;](backup-devices-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="af8db-147">[Backup Devices &#40;SQL Server&#41;](backup-devices-sql-server.md) </span></span>  
 <span data-ttu-id="af8db-148">[디스크 파일에 대한 논리적 백업 디바이스 정의&#40;SQL Server&#41;](define-a-logical-backup-device-for-a-disk-file-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="af8db-148">[Define a Logical Backup Device for a Disk File &#40;SQL Server&#41;](define-a-logical-backup-device-for-a-disk-file-sql-server.md) </span></span>  
 [<span data-ttu-id="af8db-149">논리적 백업 디바이스의 속성 및 내용 보기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="af8db-149">View the Properties and Contents of a Logical Backup Device &#40;SQL Server&#41;</span></span>](view-the-properties-and-contents-of-a-logical-backup-device-sql-server.md)  
  
  
