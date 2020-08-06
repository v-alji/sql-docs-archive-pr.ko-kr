---
title: 백업 디바이스(미디어 내용 페이지) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
f1_keywords:
- sql12.swb.backupdevice.contents.f1
ms.assetid: 5fc7bd22-b6d8-4af1-8a58-2e7d0b994d08
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 07204b5e05ce9fc17e6ea23450066f9f58b7cf87
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651731"
---
# <a name="backup-device-media-contents-page"></a><span data-ttu-id="e860b-102">백업 디바이스(미디어 내용 페이지)</span><span class="sxs-lookup"><span data-stu-id="e860b-102">Backup Device (Media Contents Page)</span></span>
  <span data-ttu-id="e860b-103">**백업 디바이스** 대화 상자를 사용하여 백업 정보를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e860b-103">Use the **Backup Device** dialog box to view the backup information.</span></span> <span data-ttu-id="e860b-104">이 정보에는 디바이스, 미디어, 미디어 세트 및 백업 세트에 대한 설명이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="e860b-104">This information describes the device, the media, the media set, and the backup set or sets.</span></span>  
  
 <span data-ttu-id="e860b-105">**SQL Server Management Studio를 사용하여 백업 디바이스의 내용을 보려면**</span><span class="sxs-lookup"><span data-stu-id="e860b-105">**To use SQL Server Management Studio to view the contents of a backup device**</span></span>  
  
-   [<span data-ttu-id="e860b-106">백업 테이프 또는 파일의 내용 보기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="e860b-106">View the Contents of a Backup Tape or File &#40;SQL Server&#41;</span></span>](view-the-contents-of-a-backup-tape-or-file-sql-server.md)  
  
-   [<span data-ttu-id="e860b-107">논리적 백업 디바이스의 속성 및 내용 보기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="e860b-107">View the Properties and Contents of a Logical Backup Device &#40;SQL Server&#41;</span></span>](view-the-properties-and-contents-of-a-logical-backup-device-sql-server.md)  
  
## <a name="options"></a><span data-ttu-id="e860b-108">옵션</span><span class="sxs-lookup"><span data-stu-id="e860b-108">Options</span></span>  
 <span data-ttu-id="e860b-109">개별 미디어, 미디어 세트 및 백업 세트에 대한 정보를 봅니다.</span><span class="sxs-lookup"><span data-stu-id="e860b-109">View information about the individual media, media set, and backup sets.</span></span>  
  
 <span data-ttu-id="e860b-110">**미디어**</span><span class="sxs-lookup"><span data-stu-id="e860b-110">**Media**</span></span>  
 <span data-ttu-id="e860b-111">백업 정보가 저장되는 디스크 또는 테이프 세트입니다.</span><span class="sxs-lookup"><span data-stu-id="e860b-111">A disk or set of tapes on which backup information is stored.</span></span>  
  
 <span data-ttu-id="e860b-112">**미디어 시퀀스**</span><span class="sxs-lookup"><span data-stu-id="e860b-112">**Media sequence**</span></span>  
 <span data-ttu-id="e860b-113">미디어 시퀀스 번호, 패밀리 시퀀스 번호 및 미러 ID를 나열합니다(있는 경우).</span><span class="sxs-lookup"><span data-stu-id="e860b-113">Lists the media sequence number, the family sequence number, and the mirror identifier, if any.</span></span> <span data-ttu-id="e860b-114">각 물리적 백업 미디어에는 미디어가 사용된 순서를 나타내는 미디어 시퀀스 번호가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="e860b-114">The physical backup media are each tagged with a media sequence number that indicates the order in which the media were used.</span></span> <span data-ttu-id="e860b-115">초기 백업 미디어에는 1번이, 두 번째 미디어(첫 번째 연속 테이프)에는 2번이, 나머지 미디어에도 순서에 따라 태그가 붙습니다.</span><span class="sxs-lookup"><span data-stu-id="e860b-115">The initial backup media is tagged with 1, the second (the first continuation tape) is tagged with 2, and so forth.</span></span> <span data-ttu-id="e860b-116">미디어 시퀀스 번호는 백업 세트를 복원할 때 백업을 복원하는 운영자가 올바른 순서대로 정확하게 미디어를 탑재하도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="e860b-116">When the backup set is restored, the media sequence numbers ensure that the operator restoring the backup mounts the correct media in the correct order.</span></span>  
  
 <span data-ttu-id="e860b-117">**만든 날짜**</span><span class="sxs-lookup"><span data-stu-id="e860b-117">**Created on**</span></span>  
 <span data-ttu-id="e860b-118">미디어 세트를 만든 날짜와 시간을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="e860b-118">Displays the creation date and time of the media set.</span></span>  
  
 <span data-ttu-id="e860b-119">**미디어 세트**</span><span class="sxs-lookup"><span data-stu-id="e860b-119">**Media Set**</span></span>  
 <span data-ttu-id="e860b-120">미디어 세트는 일정한 개수의 백업 디바이스를 사용하여 하나 이상의 백업 작업을 기록한 백업 미디어의 모음입니다.</span><span class="sxs-lookup"><span data-stu-id="e860b-120">A media set is an ordered collection of backup media to which one or more backup operations have written by using a constant number of backup devices.</span></span>  
  
 <span data-ttu-id="e860b-121">**이름**</span><span class="sxs-lookup"><span data-stu-id="e860b-121">**Name**</span></span>  
 <span data-ttu-id="e860b-122">미디어 세트의 이름을 표시합니다(있는 경우).</span><span class="sxs-lookup"><span data-stu-id="e860b-122">Displays the name of the media set, if any.</span></span>  
  
 <span data-ttu-id="e860b-123">**설명**</span><span class="sxs-lookup"><span data-stu-id="e860b-123">**Description**</span></span>  
 <span data-ttu-id="e860b-124">미디어 세트에 대한 설명을 표시합니다(있는 경우).</span><span class="sxs-lookup"><span data-stu-id="e860b-124">Displays the description of the media set, if any.</span></span>  
  
 <span data-ttu-id="e860b-125">**미디어 패밀리 개수**</span><span class="sxs-lookup"><span data-stu-id="e860b-125">**Media family count**</span></span>  
 <span data-ttu-id="e860b-126">미디어 세트에 있는 패밀리 수를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="e860b-126">Displays the number of families in the media set.</span></span> <span data-ttu-id="e860b-127">각 미디어 세트는 하나 이상의 미디어 패밀리의 모음입니다.</span><span class="sxs-lookup"><span data-stu-id="e860b-127">Each media set is a collection of one or more media families.</span></span> <span data-ttu-id="e860b-128">단일 미디어 패밀리는 지정된 단일 백업 디바이스 또는 미러된 백업 디바이스 그룹에 대한 모든 출력으로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="e860b-128">All the output to a given single backup device (or group of mirrored backup devices) forms a single media family.</span></span> <span data-ttu-id="e860b-129">각 미디어 세트에는 각각의 디바이스 또는 미러된 디바이스 그룹마다 하나의 미디어 패밀리가 포함됩니다. 예를 들어 한 미디어 세트에서 미러되지 않은 두 백업 디바이스를 사용하면 해당 미디어 세트에 두 개의 미디어 패밀리가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="e860b-129">Each media set contains one media family per separate device (or group of mirrored devices); for instance, if a media set uses two non-mirrored backup devices, the media set contains two media families.</span></span>  
  
 <span data-ttu-id="e860b-130">**백업 세트**</span><span class="sxs-lookup"><span data-stu-id="e860b-130">**Backup sets**</span></span>  
 <span data-ttu-id="e860b-131">미디어에 포함된 백업 세트에 대한 정보를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="e860b-131">Displays information about the backup set or sets contained on the media.</span></span> <span data-ttu-id="e860b-132">백업 세트는 성공적인 백업 작업의 결과이며 백업 디바이스 집합의 미디어 간에 해당 내용이 분산됩니다.</span><span class="sxs-lookup"><span data-stu-id="e860b-132">A backup set is the result of a successful backup operation, whose content is distributed among the media on the set of backup devices.</span></span>  
  
|<span data-ttu-id="e860b-133">헤더</span><span class="sxs-lookup"><span data-stu-id="e860b-133">Header</span></span>|<span data-ttu-id="e860b-134">값</span><span class="sxs-lookup"><span data-stu-id="e860b-134">Values</span></span>|  
|------------|------------|  
|<span data-ttu-id="e860b-135">**이름**</span><span class="sxs-lookup"><span data-stu-id="e860b-135">**Name**</span></span>|<span data-ttu-id="e860b-136">백업 세트의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="e860b-136">The name of the backup set.</span></span>|  
|<span data-ttu-id="e860b-137">**형식**</span><span class="sxs-lookup"><span data-stu-id="e860b-137">**Type**</span></span>|<span data-ttu-id="e860b-138">백업된 개체입니다. 데이터베이스, 파일 또는 *\<blank>* (트랜잭션 로그의 경우)가 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e860b-138">The backed-up object: Database, File, or *\<blank>* (for transaction logs).</span></span>|  
|<span data-ttu-id="e860b-139">**구성 요소**</span><span class="sxs-lookup"><span data-stu-id="e860b-139">**Component**</span></span>|<span data-ttu-id="e860b-140">수행된 백업 유형: 전체, 차등 또는 트랜잭션 로그일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e860b-140">The type of backup performed: Full, Differential or Transaction Log.</span></span>|  
|<span data-ttu-id="e860b-141">**Server**</span><span class="sxs-lookup"><span data-stu-id="e860b-141">**Server**</span></span>|<span data-ttu-id="e860b-142">백업 작업을 수행한 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 인스턴스의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="e860b-142">The name of the instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] that performed the backup operation.</span></span>|  
|<span data-ttu-id="e860b-143">**Database**</span><span class="sxs-lookup"><span data-stu-id="e860b-143">**Database**</span></span>|<span data-ttu-id="e860b-144">백업한 데이터베이스 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="e860b-144">The name of the database that was backed up.</span></span>|  
|<span data-ttu-id="e860b-145">**위치**</span><span class="sxs-lookup"><span data-stu-id="e860b-145">**Position**</span></span>|<span data-ttu-id="e860b-146">볼륨에 있는 백업 세트의 위치입니다.</span><span class="sxs-lookup"><span data-stu-id="e860b-146">The position of the backup set in the volume.</span></span>|  
|<span data-ttu-id="e860b-147">**Date**</span><span class="sxs-lookup"><span data-stu-id="e860b-147">**Date**</span></span>|<span data-ttu-id="e860b-148">클라이언트의 국가별 설정으로 표시되는 백업 작업 완료 날짜 및 시간입니다.</span><span class="sxs-lookup"><span data-stu-id="e860b-148">The date and time when the backup operation finished, presented in the regional setting of the client.</span></span>|  
|<span data-ttu-id="e860b-149">**크기**</span><span class="sxs-lookup"><span data-stu-id="e860b-149">**Size**</span></span>|<span data-ttu-id="e860b-150">백업 세트의 크기를 바이트 단위로 표시한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="e860b-150">The size of the backup set in bytes.</span></span>|  
|<span data-ttu-id="e860b-151">**사용자 이름**</span><span class="sxs-lookup"><span data-stu-id="e860b-151">**User Name**</span></span>|<span data-ttu-id="e860b-152">백업 작업을 수행한 사용자의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="e860b-152">The name of the user who performed the backup operation.</span></span>|  
|<span data-ttu-id="e860b-153">**만료**</span><span class="sxs-lookup"><span data-stu-id="e860b-153">**Expiration**</span></span>|<span data-ttu-id="e860b-154">백업 세트가 만료되는 날짜 및 시간입니다.</span><span class="sxs-lookup"><span data-stu-id="e860b-154">The date and time the backup set expires.</span></span>|  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="e860b-155">관련 작업</span><span class="sxs-lookup"><span data-stu-id="e860b-155">Related Tasks</span></span>  
  
-   [<span data-ttu-id="e860b-156">디스크 파일에 대한 논리적 백업 디바이스 정의&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="e860b-156">Define a Logical Backup Device for a Disk File &#40;SQL Server&#41;</span></span>](define-a-logical-backup-device-for-a-disk-file-sql-server.md)  
  
-   [<span data-ttu-id="e860b-157">테이프 드라이브에 대한 논리적 백업 디바이스 정의&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="e860b-157">Define a Logical Backup Device for a Tape Drive &#40;SQL Server&#41;</span></span>](define-a-logical-backup-device-for-a-tape-drive-sql-server.md)  
  
-   [<span data-ttu-id="e860b-158">디스크 또는 테이프를 백업 대상으로 지정&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="e860b-158">Specify a Disk or Tape As a Backup Destination &#40;SQL Server&#41;</span></span>](specify-a-disk-or-tape-as-a-backup-destination-sql-server.md)  
  
-   [<span data-ttu-id="e860b-159">백업 디바이스 삭제&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="e860b-159">Delete a Backup Device &#40;SQL Server&#41;</span></span>](delete-a-backup-device-sql-server.md)  
  
-   [<span data-ttu-id="e860b-160">백업의 만료 날짜 설정&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="e860b-160">Set the Expiration Date on a Backup &#40;SQL Server&#41;</span></span>](set-the-expiration-date-on-a-backup-sql-server.md)  
  
-   [<span data-ttu-id="e860b-161">백업 테이프 또는 파일의 내용 보기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="e860b-161">View the Contents of a Backup Tape or File &#40;SQL Server&#41;</span></span>](view-the-contents-of-a-backup-tape-or-file-sql-server.md)  
  
-   [<span data-ttu-id="e860b-162">백업 세트의 데이터와 로그 파일 보기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="e860b-162">View the Data and Log Files in a Backup Set &#40;SQL Server&#41;</span></span>](view-the-data-and-log-files-in-a-backup-set-sql-server.md)  
  
-   [<span data-ttu-id="e860b-163">논리적 백업 디바이스의 속성 및 내용 보기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="e860b-163">View the Properties and Contents of a Logical Backup Device &#40;SQL Server&#41;</span></span>](view-the-properties-and-contents-of-a-logical-backup-device-sql-server.md)  
  
-   [<span data-ttu-id="e860b-164">디바이스에서 백업 복원&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="e860b-164">Restore a Backup from a Device &#40;SQL Server&#41;</span></span>](restore-a-backup-from-a-device-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="e860b-165">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e860b-165">See Also</span></span>  
 <span data-ttu-id="e860b-166">[백업 디바이스&#40;SQL Server&#41;](backup-devices-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="e860b-166">[Backup Devices &#40;SQL Server&#41;](backup-devices-sql-server.md) </span></span>  
 [<span data-ttu-id="e860b-167">미디어 세트, 미디어 패밀리 및 백업 세트&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="e860b-167">Media Sets, Media Families, and Backup Sets &#40;SQL Server&#41;</span></span>](media-sets-media-families-and-backup-sets-sql-server.md)  
  
  
