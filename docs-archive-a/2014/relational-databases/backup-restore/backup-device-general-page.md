---
title: 백업 디바이스(일반 페이지) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
f1_keywords:
- sql12.swb.backupdevice.general.f1
ms.assetid: c557e37d-319e-4adb-a0c1-94189b15d2ac
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: d73bdf3ce4b88214286b5f232924d811716a247e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647069"
---
# <a name="backup-device-general-page"></a><span data-ttu-id="4633c-102">백업 디바이스(일반 페이지)</span><span class="sxs-lookup"><span data-stu-id="4633c-102">Backup Device (General Page)</span></span>
  <span data-ttu-id="4633c-103">**일반** 페이지를 사용하여 논리적 백업 디바이스의 일반 속성을 지정하거나 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4633c-103">Use the **General** page to specify or view the general properties of a logical backup device.</span></span>  
  
 <span data-ttu-id="4633c-104">**SQL Server Management Studio를 사용하여 백업 디바이스의 내용을 보려면**</span><span class="sxs-lookup"><span data-stu-id="4633c-104">**To use SQL Server Management Studio to view the contents of a backup device**</span></span>  
  
-   [<span data-ttu-id="4633c-105">백업 테이프 또는 파일의 내용 보기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="4633c-105">View the Contents of a Backup Tape or File &#40;SQL Server&#41;</span></span>](view-the-contents-of-a-backup-tape-or-file-sql-server.md)  
  
-   [<span data-ttu-id="4633c-106">논리적 백업 디바이스의 속성 및 내용 보기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="4633c-106">View the Properties and Contents of a Logical Backup Device &#40;SQL Server&#41;</span></span>](view-the-properties-and-contents-of-a-logical-backup-device-sql-server.md)  
  
## <a name="options"></a><span data-ttu-id="4633c-107">옵션</span><span class="sxs-lookup"><span data-stu-id="4633c-107">Options</span></span>  
 <span data-ttu-id="4633c-108">**디바이스 이름**</span><span class="sxs-lookup"><span data-stu-id="4633c-108">**Device name**</span></span>  
 <span data-ttu-id="4633c-109">기존 논리적 백업 디바이스의 이름을 확인하거나 새 논리적 백업 디바이스의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="4633c-109">View the name of an existing logical backup device or specify the name of a new logical backup device.</span></span>  
  
 <span data-ttu-id="4633c-110">**테이프**</span><span class="sxs-lookup"><span data-stu-id="4633c-110">**Tape**</span></span>  
 <span data-ttu-id="4633c-111">**테이프** 목록에서 대상 테이프 디바이스를 확인하거나 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="4633c-111">View or select the destination tape device in the **Tape** list.</span></span> <span data-ttu-id="4633c-112">이 옵션은 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 인스턴스를 실행하는 컴퓨터에 테이프 드라이브가 연결된 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4633c-112">This option is available only if a tape drive is attached to the computer that is running the instance of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4633c-113">원격 컴퓨터의 테이프 백업 디바이스는 올바른 백업 대상이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="4633c-113">Tape backup devices on remote computers are not valid backup destinations.</span></span>  
  
 <span data-ttu-id="4633c-114">**최근에 사용한 파일**</span><span class="sxs-lookup"><span data-stu-id="4633c-114">**File**</span></span>  
 <span data-ttu-id="4633c-115">기존 논리적 백업 디바이스의 대상 파일을 확인하거나 새 논리적 백업 디바이스의 대상 파일을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="4633c-115">View the destination file of an existing logical backup device, or specify a destination file for a new logical backup device.</span></span>  
  
-   <span data-ttu-id="4633c-116">기존 논리적 백업 디바이스의 경우 백업 파일의 경로가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="4633c-116">For an existing logical backup device, the path of the backup file is displayed.</span></span> <span data-ttu-id="4633c-117">**파일** 필드를 편집할 수 없으며 찾아보기 단추를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4633c-117">The **File** field is not editable, and the Browse button is unavailable.</span></span>  
  
-   <span data-ttu-id="4633c-118">새 논리적 백업 디바이스의 경우 논리적 백업 디바이스를 정의할 백업 파일의 경로를 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4633c-118">For a new logical backup device, you must supply the path of the backup file for which you are defining the logical backup device.</span></span> <span data-ttu-id="4633c-119">아직 이 파일이 있을 필요는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4633c-119">This file does not have to exist yet.</span></span>  
  
     <span data-ttu-id="4633c-120">로컬 백업 파일을 지정하려면 **파일** 입력란 오른쪽에 있는 찾아보기 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4633c-120">To specify a local backup file, you can click the Browse button to the right of the **File** text box.</span></span> <span data-ttu-id="4633c-121">그런 다음 **데이터베이스 파일 찾기** 대화 상자에서 서버 인스턴스를 실행하는 컴퓨터의 고정 드라이브 중 하나에 있는 임의의 위치로 이동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4633c-121">Then, in the **Locate Database Files** dialog box, you can navigate to any location on any of the fixed drives on the computer running the server instance.</span></span> <span data-ttu-id="4633c-122">백업 파일이 아직 없을 경우 해당 대화 상자의 **파일 이름** 필드에 사용할 파일 이름을 입력해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4633c-122">If the backup file does not exist yet, you must enter the filename you want to use in the **File name** field of that dialog box.</span></span>  
  
     <span data-ttu-id="4633c-123">또는 **파일** 필드를 수동으로 편집하여 기본 경로, 파일 이름 및 확장명을 재정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4633c-123">Alternatively, you can edit the **File** field manually to override the default path, file name, and extension.</span></span> <span data-ttu-id="4633c-124">원격 파일을 백업 대상으로 지정하려면 해당 파일의 정규화된 UNC(Universal Naming Convention) 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="4633c-124">To specify a remote file as your backup destination, enter its fully qualified universal naming convention (UNC) name.</span></span> <span data-ttu-id="4633c-125">자세한 내용은 [백업 디바이스&#40;SQL Server&#41;](backup-devices-sql-server.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4633c-125">For more information, see [Backup Devices &#40;SQL Server&#41;](backup-devices-sql-server.md).</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="4633c-126">네트워크를 통해 데이터를 백업할 경우에는 네트워크 오류가 발생할 수 있으므로 완료된 후에 백업 작업을 확인하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="4633c-126">Backing up data over a network can be subject to network errors; therefore, we recommend that you verify the backup operation after it finishes.</span></span> <span data-ttu-id="4633c-127">자세한 내용은 [RESTORE VERIFYONLY&#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-verifyonly-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4633c-127">For more information, see [RESTORE VERIFYONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-verifyonly-transact-sql).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4633c-128">설명</span><span class="sxs-lookup"><span data-stu-id="4633c-128">Remarks</span></span>  
 <span data-ttu-id="4633c-129">하나 이상의 백업 디바이스 세트에서의 백업이 미디어 세트 하나를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="4633c-129">The backups on a set of one or more backup devices compose a single media set.</span></span> <span data-ttu-id="4633c-130">*미디어 세트* 는 하나 이상의 백업 작업에서 고정된 유형과 개수의 백업 디바이스를 사용하여 기록한 백업 미디어, 테이프 또는 디스크 파일의 모음입니다.</span><span class="sxs-lookup"><span data-stu-id="4633c-130">A *media set* is an ordered collection of backup media, tapes or disk files, to which one or more backup operations have written using a fixed type and number of backup devices.</span></span> <span data-ttu-id="4633c-131">미디어 세트에 대한 자세한 내용은 [미디어 세트, 미디어 패밀리 및 백업 세트&#40;SQL Server&#41;](media-sets-media-families-and-backup-sets-sql-server.md)인스턴스를 실행하는 컴퓨터에 테이프 드라이브가 연결되어 있는 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4633c-131">For information about media sets, see [Media Sets, Media Families, and Backup Sets &#40;SQL Server&#41;](media-sets-media-families-and-backup-sets-sql-server.md).</span></span>  
  
 <span data-ttu-id="4633c-132">미디어 세트의 첫 번째 백업이 논리적 백업 디바이스에 기록되면 논리적 백업 디바이스에 해당하는 물리적 백업 디바이스가 초기화됩니다.</span><span class="sxs-lookup"><span data-stu-id="4633c-132">The physical backup device corresponding to a logical backup device is initialized when the first backup in the media set is written to the logical backup device.</span></span> <span data-ttu-id="4633c-133">물리적 백업 디바이스가 아직 존재하지 않는 파일인 경우 이 시점에 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="4633c-133">If the physical backup device is a file that does not exist yet, it is created at that time.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="4633c-134">관련 작업</span><span class="sxs-lookup"><span data-stu-id="4633c-134">Related Tasks</span></span>  
  
-   [<span data-ttu-id="4633c-135">디스크 파일에 대한 논리적 백업 디바이스 정의&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="4633c-135">Define a Logical Backup Device for a Disk File &#40;SQL Server&#41;</span></span>](define-a-logical-backup-device-for-a-disk-file-sql-server.md)  
  
-   [<span data-ttu-id="4633c-136">테이프 드라이브에 대한 논리적 백업 디바이스 정의&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="4633c-136">Define a Logical Backup Device for a Tape Drive &#40;SQL Server&#41;</span></span>](define-a-logical-backup-device-for-a-tape-drive-sql-server.md)  
  
-   [<span data-ttu-id="4633c-137">디스크 또는 테이프를 백업 대상으로 지정&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="4633c-137">Specify a Disk or Tape As a Backup Destination &#40;SQL Server&#41;</span></span>](specify-a-disk-or-tape-as-a-backup-destination-sql-server.md)  
  
-   [<span data-ttu-id="4633c-138">백업 디바이스 삭제&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="4633c-138">Delete a Backup Device &#40;SQL Server&#41;</span></span>](delete-a-backup-device-sql-server.md)  
  
-   [<span data-ttu-id="4633c-139">백업의 만료 날짜 설정&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="4633c-139">Set the Expiration Date on a Backup &#40;SQL Server&#41;</span></span>](set-the-expiration-date-on-a-backup-sql-server.md)  
  
-   [<span data-ttu-id="4633c-140">백업 테이프 또는 파일의 내용 보기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="4633c-140">View the Contents of a Backup Tape or File &#40;SQL Server&#41;</span></span>](view-the-contents-of-a-backup-tape-or-file-sql-server.md)  
  
-   [<span data-ttu-id="4633c-141">백업 세트의 데이터와 로그 파일 보기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="4633c-141">View the Data and Log Files in a Backup Set &#40;SQL Server&#41;</span></span>](view-the-data-and-log-files-in-a-backup-set-sql-server.md)  
  
-   [<span data-ttu-id="4633c-142">논리적 백업 디바이스의 속성 및 내용 보기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="4633c-142">View the Properties and Contents of a Logical Backup Device &#40;SQL Server&#41;</span></span>](view-the-properties-and-contents-of-a-logical-backup-device-sql-server.md)  
  
-   [<span data-ttu-id="4633c-143">디바이스에서 백업 복원&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="4633c-143">Restore a Backup from a Device &#40;SQL Server&#41;</span></span>](restore-a-backup-from-a-device-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="4633c-144">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4633c-144">See Also</span></span>  
 <span data-ttu-id="4633c-145">[백업 디바이스&#40;SQL Server&#41;](backup-devices-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="4633c-145">[Backup Devices &#40;SQL Server&#41;](backup-devices-sql-server.md) </span></span>  
 [<span data-ttu-id="4633c-146">미디어 세트, 미디어 패밀리 및 백업 세트&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="4633c-146">Media Sets, Media Families, and Backup Sets &#40;SQL Server&#41;</span></span>](media-sets-media-families-and-backup-sets-sql-server.md)  
  
  
