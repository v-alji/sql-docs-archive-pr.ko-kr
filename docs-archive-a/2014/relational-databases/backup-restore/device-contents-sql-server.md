---
title: 디바이스 내용(SQL Server) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
f1_keywords:
- sql12.swb.bnrdevicecontents.f1
ms.assetid: 95e1902e-8c7a-4830-bdf9-1a6aca414a24
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: c904718eca671b1965a95d0d400f3f6fa075b500
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650131"
---
# <a name="device-contents-sql-server"></a><span data-ttu-id="e062f-102">디바이스 내용(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="e062f-102">Device Contents (SQL Server)</span></span>
  <span data-ttu-id="e062f-103">이 대화 상자를 사용하여 백업 정보를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e062f-103">Use this dialog box to view the backup information.</span></span> <span data-ttu-id="e062f-104">이 정보에는 디바이스, 미디어, 미디어 세트 및 백업 세트에 대한 설명이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="e062f-104">This information describes the device, the media, the media set, and the backup set or sets.</span></span>  
  
 <span data-ttu-id="e062f-105">**SQL Server Management Studio를 사용하여 백업 디바이스의 내용을 보려면**</span><span class="sxs-lookup"><span data-stu-id="e062f-105">**To use SQL Server Management Studio to view the contents of a backup device**</span></span>  
  
-   [<span data-ttu-id="e062f-106">백업 테이프 또는 파일의 내용 보기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="e062f-106">View the Contents of a Backup Tape or File &#40;SQL Server&#41;</span></span>](view-the-contents-of-a-backup-tape-or-file-sql-server.md)  
  
-   [<span data-ttu-id="e062f-107">논리적 백업 디바이스의 속성 및 내용 보기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="e062f-107">View the Properties and Contents of a Logical Backup Device &#40;SQL Server&#41;</span></span>](view-the-properties-and-contents-of-a-logical-backup-device-sql-server.md)  
  
## <a name="options"></a><span data-ttu-id="e062f-108">옵션</span><span class="sxs-lookup"><span data-stu-id="e062f-108">Options</span></span>  
 <span data-ttu-id="e062f-109">**미디어**</span><span class="sxs-lookup"><span data-stu-id="e062f-109">**Media**</span></span>  
 <span data-ttu-id="e062f-110">백업 정보가 저장되는 디스크 또는 테이프 세트입니다.</span><span class="sxs-lookup"><span data-stu-id="e062f-110">A disk or set of tapes on which backup information is stored.</span></span>  
  
 <span data-ttu-id="e062f-111">**미디어 시퀀스**</span><span class="sxs-lookup"><span data-stu-id="e062f-111">**Media sequence**</span></span>  
 <span data-ttu-id="e062f-112">미디어 시퀀스 번호, 패밀리 시퀀스 번호 및 미러 ID를 나열합니다(있는 경우).</span><span class="sxs-lookup"><span data-stu-id="e062f-112">Lists the media sequence number, the family sequence number, and the mirror identifier, if any.</span></span> <span data-ttu-id="e062f-113">각 물리적 백업 미디어에는 미디어가 사용된 순서를 나타내는 미디어 시퀀스 번호가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="e062f-113">The physical backup media are each tagged with a media sequence number that indicates the order in which the media were used.</span></span> <span data-ttu-id="e062f-114">첫 번째 백업 미디어에는 1번이, 두 번째 미디어(첫 번째 연속 테이프)에는 2번이, 나머지 미디어에도 순서에 따라 번호가 붙습니다.</span><span class="sxs-lookup"><span data-stu-id="e062f-114">The initial backup medium is tagged with 1, the second (the first continuation tape) is tagged with 2, and so forth.</span></span> <span data-ttu-id="e062f-115">미디어 시퀀스 번호는 백업 세트를 복원할 때 백업을 복원하는 운영자가 올바른 순서대로 정확하게 미디어를 탑재하도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="e062f-115">When the backup set is restored, the media sequence numbers ensure that the operator that restores the backup mounts the correct media in the correct order.</span></span>  
  
 <span data-ttu-id="e062f-116">**만든 날짜**</span><span class="sxs-lookup"><span data-stu-id="e062f-116">**Created on**</span></span>  
 <span data-ttu-id="e062f-117">미디어 날짜를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="e062f-117">Displays the media date.</span></span>  
  
 <span data-ttu-id="e062f-118">**미디어 세트**</span><span class="sxs-lookup"><span data-stu-id="e062f-118">**Media Set**</span></span>  
 <span data-ttu-id="e062f-119">미디어 세트는 일정한 개수의 백업 디바이스를 사용하여 하나 이상의 백업 작업을 기록한 백업 미디어의 정렬된 모음입니다.</span><span class="sxs-lookup"><span data-stu-id="e062f-119">A media set is an ordered collection of backup media to which one or more backup operations have written using a constant number of backup devices.</span></span>  
  
 <span data-ttu-id="e062f-120">**이름**</span><span class="sxs-lookup"><span data-stu-id="e062f-120">**Name**</span></span>  
 <span data-ttu-id="e062f-121">미디어 세트 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="e062f-121">Displays the name of the media set.</span></span>  
  
 <span data-ttu-id="e062f-122">**설명**</span><span class="sxs-lookup"><span data-stu-id="e062f-122">**Description**</span></span>  
 <span data-ttu-id="e062f-123">미디어 세트에 대한 설명을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="e062f-123">Displays the description media set.</span></span>  
  
 <span data-ttu-id="e062f-124">**미디어 패밀리 개수**</span><span class="sxs-lookup"><span data-stu-id="e062f-124">**Media family count**</span></span>  
 <span data-ttu-id="e062f-125">미디어 패밀리 수를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="e062f-125">Displays the media family count.</span></span> <span data-ttu-id="e062f-126">각 미디어 세트는 하나 이상의 미디어 패밀리의 모음입니다.</span><span class="sxs-lookup"><span data-stu-id="e062f-126">Each media set is a collection of one or more media families.</span></span> <span data-ttu-id="e062f-127">단일 미디어 패밀리는 지정된 단일 백업 디바이스 또는 미러된 백업 디바이스 그룹에 대한 모든 출력으로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="e062f-127">All the output to a given single backup device (or group of mirrored backup devices) forms a single media family.</span></span> <span data-ttu-id="e062f-128">각 미디어 세트에는 별개의 디바이스 또는 미러된 디바이스 그룹마다 하나의 미디어 패밀리가 포함됩니다. 예를 들어 한 미디어 세트에서 미러되지 않은 두 백업 디바이스를 사용하는 경우 미디어 세트에 두 개의 미디어 패밀리가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="e062f-128">Each media set contains one media family per separate device (or group of mirrored devices); for example, if a media set uses two nonmirrored backup devices, the media set contains two media families.</span></span>  
  
 <span data-ttu-id="e062f-129">**백업 세트**</span><span class="sxs-lookup"><span data-stu-id="e062f-129">**Backup sets**</span></span>  
 <span data-ttu-id="e062f-130">미디어에 포함된 백업 세트에 대한 정보를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="e062f-130">Displays information about the backup set or sets contained on the media.</span></span> <span data-ttu-id="e062f-131">백업 세트는 백업 디바이스 집합의 미디어 간에 해당 내용이 분산되는 성공적인 백업 작업의 결과입니다.</span><span class="sxs-lookup"><span data-stu-id="e062f-131">A backup set is the result of a successful backup operation whose content is distributed among the media on the set of backup devices.</span></span>  
  
|<span data-ttu-id="e062f-132">헤더</span><span class="sxs-lookup"><span data-stu-id="e062f-132">Header</span></span>|<span data-ttu-id="e062f-133">값</span><span class="sxs-lookup"><span data-stu-id="e062f-133">Values</span></span>|  
|------------|------------|  
|<span data-ttu-id="e062f-134">**이름**</span><span class="sxs-lookup"><span data-stu-id="e062f-134">**Name**</span></span>|<span data-ttu-id="e062f-135">백업 세트의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="e062f-135">The name of the backup set.</span></span>|  
|<span data-ttu-id="e062f-136">**형식**</span><span class="sxs-lookup"><span data-stu-id="e062f-136">**Type**</span></span>|<span data-ttu-id="e062f-137">수행된 백업 유형: 전체, 차등 또는 트랜잭션 로그일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e062f-137">The type of backup performed: Full, Differential or Transaction Log.</span></span>|  
|<span data-ttu-id="e062f-138">**구성 요소**</span><span class="sxs-lookup"><span data-stu-id="e062f-138">**Component**</span></span>|<span data-ttu-id="e062f-139">백업된 구성 요소: 데이터베이스, 파일 또는 *\<blank>* (트랜잭션 로그의 경우)가 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e062f-139">The backed-up component: Database, File, or *\<blank>* (for transaction logs).</span></span>|  
|<span data-ttu-id="e062f-140">**Server**</span><span class="sxs-lookup"><span data-stu-id="e062f-140">**Server**</span></span>|<span data-ttu-id="e062f-141">백업 작업을 수행한 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 인스턴스의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="e062f-141">The name of the instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] that performed the backup operation.</span></span>|  
|<span data-ttu-id="e062f-142">**Database**</span><span class="sxs-lookup"><span data-stu-id="e062f-142">**Database**</span></span>|<span data-ttu-id="e062f-143">백업한 데이터베이스 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="e062f-143">The name of the database that was backed up.</span></span>|  
|<span data-ttu-id="e062f-144">**위치**</span><span class="sxs-lookup"><span data-stu-id="e062f-144">**Position**</span></span>|<span data-ttu-id="e062f-145">볼륨에 있는 백업 세트의 위치입니다.</span><span class="sxs-lookup"><span data-stu-id="e062f-145">The position of the backup set in the volume.</span></span>|  
|<span data-ttu-id="e062f-146">**Date**</span><span class="sxs-lookup"><span data-stu-id="e062f-146">**Date**</span></span>|<span data-ttu-id="e062f-147">클라이언트의 국가별 설정으로 표시되는 백업 작업 완료 날짜 및 시간입니다.</span><span class="sxs-lookup"><span data-stu-id="e062f-147">The date and time when the backup operation finished, presented in the regional setting of the client.</span></span>|  
|<span data-ttu-id="e062f-148">**크기**</span><span class="sxs-lookup"><span data-stu-id="e062f-148">**Size**</span></span>|<span data-ttu-id="e062f-149">백업 세트의 크기를 바이트 단위로 표시한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="e062f-149">The size of the backup set in bytes.</span></span>|  
|<span data-ttu-id="e062f-150">**사용자 이름**</span><span class="sxs-lookup"><span data-stu-id="e062f-150">**User Name**</span></span>|<span data-ttu-id="e062f-151">백업 작업을 수행한 사용자의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="e062f-151">The name of the user who performed the backup operation.</span></span>|  
|<span data-ttu-id="e062f-152">**만료**</span><span class="sxs-lookup"><span data-stu-id="e062f-152">**Expiration**</span></span>|<span data-ttu-id="e062f-153">백업 세트가 만료되는 날짜 및 시간입니다.</span><span class="sxs-lookup"><span data-stu-id="e062f-153">The date and time the backup set expires.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e062f-154">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e062f-154">See Also</span></span>  
 [<span data-ttu-id="e062f-155">미디어 세트, 미디어 패밀리 및 백업 세트&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="e062f-155">Media Sets, Media Families, and Backup Sets &#40;SQL Server&#41;</span></span>](media-sets-media-families-and-backup-sets-sql-server.md)  
  
  
