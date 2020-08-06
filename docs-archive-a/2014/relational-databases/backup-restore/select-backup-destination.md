---
title: 백업 대상 선택 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
f1_keywords:
- sql12.swb.selectbackupdest.f1
ms.assetid: f79e824b-1525-45de-8ede-513563af41b6
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 5ffd1d2529dd13e42689bcf168c972d757fb5499
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653447"
---
# <a name="select-backup-destination"></a><span data-ttu-id="69192-102">백업 대상 선택</span><span class="sxs-lookup"><span data-stu-id="69192-102">Select Backup Destination</span></span>
  <span data-ttu-id="69192-103">**백업 대상 선택** 대화 상자를 사용하여 디바이스를 백업 대상으로 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="69192-103">Use the **Select Backup Destination** dialog box to select a device as your backup destination.</span></span> <span data-ttu-id="69192-104">디스크 또는 논리적 백업 디바이스를 백업 대상으로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="69192-104">A backup destination can be either a disk or a logical backup device.</span></span>  
  
 <span data-ttu-id="69192-105">**SQL Server Management Studio를 사용하여 데이터베이스를 백업하려면**</span><span class="sxs-lookup"><span data-stu-id="69192-105">**To use SQL Server Management Studio to back up a database**</span></span>  
  
-   [<span data-ttu-id="69192-106">전체 데이터베이스 백업 만들기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="69192-106">Create a Full Database Backup &#40;SQL Server&#41;</span></span>](create-a-full-database-backup-sql-server.md)  
  
-   [<span data-ttu-id="69192-107">차등 데이터베이스 백업 만들기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="69192-107">Create a Differential Database Backup &#40;SQL Server&#41;</span></span>](create-a-differential-database-backup-sql-server.md)  
  
-   [<span data-ttu-id="69192-108">파일 및 파일 그룹 백업&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="69192-108">Back Up Files and Filegroups &#40;SQL Server&#41;</span></span>](back-up-files-and-filegroups-sql-server.md)  
  
-   [<span data-ttu-id="69192-109">트랜잭션 로그 백업&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="69192-109">Back Up a Transaction Log &#40;SQL Server&#41;</span></span>](back-up-a-transaction-log-sql-server.md)  
  
## <a name="options"></a><span data-ttu-id="69192-110">옵션</span><span class="sxs-lookup"><span data-stu-id="69192-110">Options</span></span>  
 <span data-ttu-id="69192-111">이 대화 상자의 옵션은 대상을 디스크에서 선택하는지 또는 테이프에서 선택하는지에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="69192-111">The options of this dialog box depend on whether you are selecting a destination on disk or on tape.</span></span>  
  
 <span data-ttu-id="69192-112">**디스크의 대상**</span><span class="sxs-lookup"><span data-stu-id="69192-112">**Destination on disk**</span></span>  
 <span data-ttu-id="69192-113">백업 대상을 지정하려면 다음 옵션 중 하나를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="69192-113">To specify a backup destination, choose one of the following options.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="69192-114">**파일 이름**</span><span class="sxs-lookup"><span data-stu-id="69192-114">**File name**</span></span>|<span data-ttu-id="69192-115">입력란에 로컬 파일 또는 원격 파일을 백업 대상으로 입력하려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="69192-115">Choose this option to enter a local or remote file as the backup destination in the text box.</span></span><br /><br /> <span data-ttu-id="69192-116">로컬 파일을 지정하려면 입력란 오른쪽의 찾아보기 단추를 클릭하고 서버를 실행하는 컴퓨터의 고정 드라이브에서 파일을 검색하거나 전체 경로 및 파일 이름을 직접 입력합니다(예: `C:\Program Files\Microsoft SQL Server\MSSQL\Backup\AdventureWorksBackup.bak`).</span><span class="sxs-lookup"><span data-stu-id="69192-116">To specify a local file, click the browse button to the right of the text box and navigate to a file on the fixed drives of the computer running the server, or enter the full path and file name directly; for example, `C:\Program Files\Microsoft SQL Server\MSSQL\Backup\AdventureWorksBackup.bak`.</span></span><br /><br /> <span data-ttu-id="69192-117">원격 파일을 백업 대상으로 지정하려면 해당 파일의 정규화된 UNC(Universal Naming Convention) 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="69192-117">To specify a remote file as your backup destination, enter its fully qualified universal naming convention (UNC) name.</span></span> <span data-ttu-id="69192-118">자세한 내용은 [백업 디바이스&#40;SQL Server&#41;](backup-devices-sql-server.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="69192-118">For more information, see [Backup Devices &#40;SQL Server&#41;](backup-devices-sql-server.md).</span></span><br /><br /> <span data-ttu-id="69192-119">**\*\* 중요 \*\*** 네트워크를 통해 데이터를 백업할 경우에는 네트워크 오류가 발생할 수 있으므로 완료된 후에 백업 작업을 확인하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="69192-119">**\*\* Important \*\*** Backing up data over a network can be subject to network errors; therefore, we recommend that you verify the backup operation after it finishes.</span></span> <span data-ttu-id="69192-120">자세한 내용은 [RESTORE VERIFYONLY&#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-verifyonly-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="69192-120">For more information, see [RESTORE VERIFYONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-verifyonly-transact-sql).</span></span>|  
|<span data-ttu-id="69192-121">**백업 디바이스**</span><span class="sxs-lookup"><span data-stu-id="69192-121">**Backup device**</span></span>|<span data-ttu-id="69192-122">논리적 백업 디바이스를 선택하려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="69192-122">Choose this option to select a logical backup device.</span></span><br /><br /> <span data-ttu-id="69192-123">참고: 디스크 백업 디바이스를 만드는 방법에 대한 자세한 내용은 [디스크 파일에 대한 논리적 백업 디바이스 정의&#40;SQL Server&#41;](define-a-logical-backup-device-for-a-disk-file-sql-server.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="69192-123">Note: For information about how to create a disk backup device, see [Define a Logical Backup Device for a Disk File &#40;SQL Server&#41;](define-a-logical-backup-device-for-a-disk-file-sql-server.md).</span></span>|  
  
 <span data-ttu-id="69192-124">**테이프의 대상**</span><span class="sxs-lookup"><span data-stu-id="69192-124">**Destination on tape**</span></span>  
 <span data-ttu-id="69192-125">서버를 실행하는 컴퓨터( [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스)에 물리적으로 연결된 테이프 드라이브에서 백업 대상을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="69192-125">Specify a backup destination on a tape drive physically connected to the computer running the server (that is, the instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)]).</span></span> <span data-ttu-id="69192-126">다음 옵션 중 하나를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="69192-126">Choose one of the following options.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="69192-127">**테이프 드라이브**</span><span class="sxs-lookup"><span data-stu-id="69192-127">**Tape drive**</span></span>|<span data-ttu-id="69192-128">서버 인스턴스를 실행하는 컴퓨터에 물리적으로 연결된 테이프 드라이브의 목록에서 테이프 드라이브를 백업 대상으로 선택하려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="69192-128">Choose this option to select a tape drive as the backup destination from the list of tape drives that are physically connected to the computer that is running the server instance.</span></span><br /><br /> <span data-ttu-id="69192-129">참고: 원격 컴퓨터의 테이프 백업 디바이스는 올바른 백업 대상이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="69192-129">Note: Tape backup devices on remote computers are not valid backup destinations.</span></span>|  
|<span data-ttu-id="69192-130">**백업 디바이스**</span><span class="sxs-lookup"><span data-stu-id="69192-130">**Backup device**</span></span>|<span data-ttu-id="69192-131">기존의 논리적 백업 디바이스를 선택하려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="69192-131">Choose this option to select an existing logical backup device.</span></span> <span data-ttu-id="69192-132">이러한 논리적 백업 디바이스는 서버 인스턴스를 실행하는 컴퓨터에 물리적으로 연결된 테이프 드라이브입니다.</span><span class="sxs-lookup"><span data-stu-id="69192-132">These logical backup devices correspond to tape drives that are physically connected to the computer that is running the server instance.</span></span><br /><br /> <span data-ttu-id="69192-133">참고: 테이프 백업 디바이스를 만드는 방법에 대한 자세한 내용은 [테이프 드라이브에 대한 논리적 백업 디바이스 정의&#40;SQL Server&#41;](define-a-logical-backup-device-for-a-tape-drive-sql-server.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="69192-133">Note: For information about how to create a tape backup device, see [Define a Logical Backup Device for a Tape Drive &#40;SQL Server&#41;](define-a-logical-backup-device-for-a-tape-drive-sql-server.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="69192-134">참고 항목</span><span class="sxs-lookup"><span data-stu-id="69192-134">See Also</span></span>  
 <span data-ttu-id="69192-135">[백업 디바이스&#40;SQL Server&#41;](backup-devices-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="69192-135">[Backup Devices &#40;SQL Server&#41;](backup-devices-sql-server.md) </span></span>  
 [<span data-ttu-id="69192-136">미디어 세트, 미디어 패밀리 및 백업 세트&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="69192-136">Media Sets, Media Families, and Backup Sets &#40;SQL Server&#41;</span></span>](media-sets-media-families-and-backup-sets-sql-server.md)  
  
  
