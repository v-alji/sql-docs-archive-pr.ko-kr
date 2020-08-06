---
title: 미디어 세트, 미디어 패밀리 및 백업 세트(SQL Server) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- media sets [SQL Server], about media sets
- backup media [SQL Server], about backup media
- backups [SQL Server], media sets
- media sets [SQL Server]
- media headers [SQL Server]
- backup sets [SQL Server], about backup sets
- backup media [SQL Server], media sets
- backups [SQL Server], media families
- backup media [SQL Server], media families
- media families [SQL Server]
- backups [SQL Server], backup sets
- backup sets [SQL Server]
ms.assetid: 2b8f19a2-ee9d-4120-b194-fbcd2076a489
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 853451ea5a7c43cd073fdf75703b3c4651b442d0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653481"
---
# <a name="media-sets-media-families-and-backup-sets-sql-server"></a><span data-ttu-id="eaf9a-102">미디어 세트, 미디어 패밀리 및 백업 세트(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="eaf9a-102">Media Sets, Media Families, and Backup Sets (SQL Server)</span></span>
  <span data-ttu-id="eaf9a-103">이 항목에서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 를 처음 접하는 사용자를 위해 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]백업 및 복원의 기본적인 백업 미디어 관련 용어를 소개합니다.</span><span class="sxs-lookup"><span data-stu-id="eaf9a-103">This topic introduces the basic backup-media terminology of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] backup and restore and is intended for readers who are new to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="eaf9a-104">이 항목에서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서 백업 미디어를 사용하는 형식, 백업 미디어와 백업 디바이스 간의 관계, 백업 미디어에서의 백업 구성, 미디어 세트 및 미디어 패밀리에 대한 몇 가지 고려 사항에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="eaf9a-104">This topic describes the format that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] uses for backup media, the correspondence between backup media and backup devices, the organization of backups on backup media, and several considerations for media sets and media families.</span></span> <span data-ttu-id="eaf9a-105">이 항목에서는 백업 미디어를 처음 사용하기 전에 초기화하거나 포맷하는 방법과 기존 미디어 세트를 새로운 미디어 세트로 교체하는 방법, 미디어 세트의 기존 백업 세트를 덮어쓰는 방법 및 미디어 세트에 새로운 백업 세트를 추가하는 방법에 대해서도 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="eaf9a-105">The topic also describes the steps initializing or formatting backup media before you use it for the first time or replace an old media set with a new media set, how to overwrite old backup sets in a media set, and how to append new backup sets to a media set.</span></span>

> [!NOTE]
>  <span data-ttu-id="eaf9a-106">Azure Blob storage 서비스에 대 한 SQL Server 백업에 대 한 자세한 내용은을 참조 하세요. [Azure Blob Storage 서비스로 백업 및 복원을 SQL Server](sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md).</span><span class="sxs-lookup"><span data-stu-id="eaf9a-106">For more information on SQL Server backup to the Azure Blob storage service,, see, [SQL Server Backup and Restore with Azure Blob Storage Service](sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md).</span></span>


##  <a name="terms-and-definitions"></a><a name="TermsAndDefinitions"></a> <span data-ttu-id="eaf9a-107">용어 및 정의</span><span class="sxs-lookup"><span data-stu-id="eaf9a-107">Terms and Definitions</span></span>
 <span data-ttu-id="eaf9a-108">미디어 세트(미디어 세트(media set)) 하나 이상의 백업 작업에서 고정된 유형과 개수의 백업 디바이스를 사용하여 기록한 백업 미디어, 테이프 또는 디스크 파일의 모음입니다.</span><span class="sxs-lookup"><span data-stu-id="eaf9a-108">media set An ordered collection of backup media, tapes or disk files, to which one or more backup operations have written using a fixed type and number of backup devices.</span></span>

 <span data-ttu-id="eaf9a-109">미디어 패밀리(미디어 패밀리(media family)) 미디어 세트의 미러되지 않은 단일 디바이스나 일련의 미러된 디바이스에 생성된 백업입니다.</span><span class="sxs-lookup"><span data-stu-id="eaf9a-109">media family Backups created on a single nonmirrored device or a set of mirrored devices in a media set</span></span>

 <span data-ttu-id="eaf9a-110">백업 세트(백업 세트(backup set)) 백업 작업이 성공할 때 미디어 세트에 추가되는 백업 내용입니다.</span><span class="sxs-lookup"><span data-stu-id="eaf9a-110">backup set The backup content that is added to a media set by a successful backup operation.</span></span>


##  <a name="overview-of-media-sets-media-families-and-backup-sets"></a><a name="OvMediaSetsFamiliesBackupSets"></a><span data-ttu-id="eaf9a-111">미디어 세트, 미디어 패밀리 및 백업 세트 개요</span><span class="sxs-lookup"><span data-stu-id="eaf9a-111">Overview of Media Sets, Media Families, and Backup Sets</span></span>
 <span data-ttu-id="eaf9a-112">백업 미디어가 하나 이상인 세트의 백업이 미디어 세트 하나를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="eaf9a-112">The backups on a set of one or more backup media compose a single media set.</span></span> <span data-ttu-id="eaf9a-113">*미디어 세트* 는 하나 이상의 백업 작업에서 고정된 유형과 개수의 백업 디바이스를 사용하여 기록한 *백업 미디어*, 테이프 또는 디스크 파일, 또는 Windows Azure Blob을 정렬하여 모아 놓은 것입니다.</span><span class="sxs-lookup"><span data-stu-id="eaf9a-113">A *media set* is an ordered collection of *backup media*, tapes or disk files, or Azure Blobs, to which one or more backup operations have written using a fixed type and number of backup devices.</span></span> <span data-ttu-id="eaf9a-114">지정된 미디어 세트에서는 테이프 드라이브, 디스크 드라이브 또는 Azure Blob을 사용하지만 둘 이상을 조합하여 사용하지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eaf9a-114">A given media set uses tape drives, or disk drives or Azure blobs, but not a combination of two or more.</span></span> <span data-ttu-id="eaf9a-115">예를 들어 미디어 세트와 연결된 백업 디바이스는 `\\.\TAPE0`, `\\.\TAPE1`및 `\\.\TAPE2`라는 3개의 테이프 드라이브일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eaf9a-115">For example, the backup devices associated with a media set might be three tape drives named `\\.\TAPE0`, `\\.\TAPE1`, and `\\.\TAPE2`.</span></span> <span data-ttu-id="eaf9a-116">이 미디어 세트에는 드라이브마다 최소한 3개로 시작되는 테이프만 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="eaf9a-116">That media set contains only tapes, starting with a minimum of three tapes (one per drive).</span></span> <span data-ttu-id="eaf9a-117">미디어 세트가 만들어질 때 백업 디바이스 유형과 개수가 설정되며 이 값은 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="eaf9a-117">The type and number of backup devices are established when a media set is created, and they cannot be changed.</span></span> <span data-ttu-id="eaf9a-118">그러나 필요할 경우 백업 작업과 복원 작업 중간에 지정된 디바이스를 같은 유형의 디바이스로 바꿀 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eaf9a-118">However, if necessary, between backup and restore operations a given device can be replaced with a device of the same type.</span></span>

 <span data-ttu-id="eaf9a-119">백업 미디어를 포맷하여 백업 작업을 수행하는 동안 백업 미디어에 미디어 세트가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="eaf9a-119">A media set is created on the backup media during a backup operation by formatting the backup media.</span></span> <span data-ttu-id="eaf9a-120">자세한 내용은 이 항목의 뒷부분에 나오는 [새 미디어 세트 만들기](#CreatingMediaSet)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="eaf9a-120">For more information, see [Creating a New Media Set](#CreatingMediaSet), later in this topic.</span></span> <span data-ttu-id="eaf9a-121">포맷 후에는 각 파일이나 테이프에 미디어 세트의 미디어 헤더가 포함되어 파일이나 테이프가 백업 내용을 수신할 수 있는 준비가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="eaf9a-121">After formatting, each file or tape contains a media header for the media set and is ready to receive backup content.</span></span> <span data-ttu-id="eaf9a-122">헤더가 있으면 백업 작업에서 작업에 지정된 모든 백업 디바이스에 있는 백업 미디어에 지정된 데이터를 백업합니다.</span><span class="sxs-lookup"><span data-stu-id="eaf9a-122">With the header in place, the backup operation proceeds to back up the specified data to the backup media on all of the backup devices specified for the operation.</span></span>

> [!NOTE]
>  <span data-ttu-id="eaf9a-123">미디어 세트를 미러링하여 손상된 미디어 볼륨(테이프 또는 디스크 파일)으로부터 보호할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eaf9a-123">Media sets can be mirrored to protect against a damaged media volume (a tape or disk file).</span></span> <span data-ttu-id="eaf9a-124">자세한 내용은 이 항목의 뒷부분에 나오는 [미러된 백업 미디어 세트&#40;SQL Server&#41;](mirrored-backup-media-sets-sql-server.md)백업 및 복원의 기본적인 백업 미디어 관련 용어를 소개합니다.</span><span class="sxs-lookup"><span data-stu-id="eaf9a-124">For more information, see [Mirrored Backup Media Sets &#40;SQL Server&#41;](mirrored-backup-media-sets-sql-server.md).</span></span>

 [!INCLUDE[ssEnterpriseEd10](../../includes/sskatmai-md.md)]<span data-ttu-id="eaf9a-125">이상에서는 압축 된 백업을 읽을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eaf9a-125">or later can read compressed backups.</span></span> <span data-ttu-id="eaf9a-126">자세한 내용은 [백업 압축&#40;SQL Server&#41;](backup-compression-sql-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="eaf9a-126">For more information, see [Backup Compression &#40;SQL Server&#41;](backup-compression-sql-server.md).</span></span>


### <a name="media-families"></a><span data-ttu-id="eaf9a-127">미디어 패밀리</span><span class="sxs-lookup"><span data-stu-id="eaf9a-127">Media Families</span></span>
 <span data-ttu-id="eaf9a-128">*미디어 패밀리*는 미디어 세트의 미러되지 않은 단일 디바이스나 일련의 미러된 디바이스에 생성된 백업으로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="eaf9a-128">Backups created on a single nonmirrored device or a set of mirrored devices in a media set constitute a *media family*.</span></span> <span data-ttu-id="eaf9a-129">미디어 세트에 사용된 백업 디바이스 수에 따라 미디어 세트의 미디어 패밀리 수가 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="eaf9a-129">The number of backup devices used for the media set determines the number of media families in a media set.</span></span> <span data-ttu-id="eaf9a-130">예를 들어 미디어 세트에 미러되지 않은 백업 디바이스 두 개가 사용되면 미디어 세트에는 두 개의 미디어 패밀리가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="eaf9a-130">For example, if a media set uses two nonmirrored backup devices, the media set contains two media families.</span></span>

> [!NOTE]
>  <span data-ttu-id="eaf9a-131">미러된 미디어 세트의 각 미디어 패밀리가 미러됩니다.</span><span class="sxs-lookup"><span data-stu-id="eaf9a-131">In a mirrored media set, each media family is mirrored.</span></span> <span data-ttu-id="eaf9a-132">예를 들어 미러 두 개가 사용되는 미디어 세트 포맷에 백업 디바이스 6개가 사용되면 백업 데이터의 해당 복사본 두 개를 각각 포함하는 미디어 패밀리가 3개가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="eaf9a-132">For example, if six backup devices are used to format a media set, where two mirrors are used, there are three media families, each containing two equivalent copies of backup data.</span></span> <span data-ttu-id="eaf9a-133">미러된 미디어 세트에 대한 자세한 내용은 [미러된 백업 미디어 세트&#40;SQL Server&#41;](mirrored-backup-media-sets-sql-server.md)백업 및 복원의 기본적인 백업 미디어 관련 용어를 소개합니다.</span><span class="sxs-lookup"><span data-stu-id="eaf9a-133">For more information about mirrored media sets, see [Mirrored Backup Media Sets &#40;SQL Server&#41;](mirrored-backup-media-sets-sql-server.md).</span></span>

 <span data-ttu-id="eaf9a-134">미디어 패밀리의 각 테이프나 디스크에는 *미디어 시퀀스 번호*가 할당됩니다.</span><span class="sxs-lookup"><span data-stu-id="eaf9a-134">Each tape or disk in a media family is assigned a *media sequence number*.</span></span> <span data-ttu-id="eaf9a-135">디스크의 미디어 시퀀스 번호는 항상 1입니다.</span><span class="sxs-lookup"><span data-stu-id="eaf9a-135">The media sequence number of a disk is always 1.</span></span> <span data-ttu-id="eaf9a-136">테이프 미디어 패밀리에서 초기 테이프의 시퀀스 번호는 1이고 두 번째 테이프의 시퀀스 번호는 2이며 나머지 시퀀스 번호도 이와 같은 순서로 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="eaf9a-136">In a tape media family, the sequence number of the initial tape is 1, the sequence number of the second tape is 2, and so forth.</span></span> <span data-ttu-id="eaf9a-137">자세한 내용은 [미디어 세트 및 패밀리 사용](#ConsiderationsForMediaSetFamilies)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="eaf9a-137">For more information, see [Using Media Sets and Families](#ConsiderationsForMediaSetFamilies).</span></span>

#### <a name="the-media-header"></a><span data-ttu-id="eaf9a-138">미디어 헤더</span><span class="sxs-lookup"><span data-stu-id="eaf9a-138">The Media Header</span></span>
 <span data-ttu-id="eaf9a-139">모든 백업 미디어(디스크 파일 또는 테이프) 볼륨에는 테이프나 디스크를 사용하는 첫 번째 백업 작업에서 만들어진 미디어 헤더가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="eaf9a-139">Every volume of backup media (disk file or tape) contains a media header that is created when by the first backup operation that uses the tape (or disk).</span></span> <span data-ttu-id="eaf9a-140">미디어를 다시 포맷할 때까지 이 헤더가 그대로 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="eaf9a-140">That header remains intact until the media is reformatted.</span></span>

 <span data-ttu-id="eaf9a-141">미디어 헤더에는 미디어(디스크 파일 또는 테이프)와 미디어가 포함된 미디어 패밀리에서의 위치를 식별하는 데 필요한 정보가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="eaf9a-141">The media header contains all of the information required to identify the media (disk file or tape) and its place within the media family to which it belongs.</span></span> <span data-ttu-id="eaf9a-142">여기에는 다음 정보가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="eaf9a-142">This information includes:</span></span>

-   <span data-ttu-id="eaf9a-143">미디어 이름</span><span class="sxs-lookup"><span data-stu-id="eaf9a-143">The name of the media.</span></span>

     <span data-ttu-id="eaf9a-144">미디어 이름은 선택 사항이지만 미디어를 잘 나타내는 이름을 일관되게 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="eaf9a-144">The media name is optionally, but we recommend consistently using media names that clearly identify your media.</span></span> <span data-ttu-id="eaf9a-145">미디어를 포맷하는 사용자는 누구든지 미디어 이름을 할당할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eaf9a-145">A media name is assigned by whoever formats the media.</span></span>

-   <span data-ttu-id="eaf9a-146">미디어 세트의 고유 ID 번호</span><span class="sxs-lookup"><span data-stu-id="eaf9a-146">The unique identification number of the media set.</span></span>

-   <span data-ttu-id="eaf9a-147">미디어 세트의 미디어 패밀리 수</span><span class="sxs-lookup"><span data-stu-id="eaf9a-147">The number of media families in the media set.</span></span>

-   <span data-ttu-id="eaf9a-148">해당 미디어가 포함된 미디어 패밀리의 시퀀스 번호</span><span class="sxs-lookup"><span data-stu-id="eaf9a-148">The sequence number of the media family containing this media.</span></span>

-   <span data-ttu-id="eaf9a-149">미디어 패밀리의 고유 ID 번호</span><span class="sxs-lookup"><span data-stu-id="eaf9a-149">The unique identification number for the media family.</span></span>

-   <span data-ttu-id="eaf9a-150">미디어 패밀리에 있는 해당 미디어의 시퀀스 번호.</span><span class="sxs-lookup"><span data-stu-id="eaf9a-150">The sequence number of this media in the media family.</span></span> <span data-ttu-id="eaf9a-151">디스크 파일의 경우는 이 값이 항상 1입니다.</span><span class="sxs-lookup"><span data-stu-id="eaf9a-151">For a disk file, this value is always 1.</span></span>

-   <span data-ttu-id="eaf9a-152">미디어 설명에 MTF 미디어 레이블이나 미디어 설명이 포함되는지 여부</span><span class="sxs-lookup"><span data-stu-id="eaf9a-152">Whether the media description contains an MTF media label or a media description.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="eaf9a-153">백업 또는 복원 작업에 사용 되는 모든 미디어는 [!INCLUDE[msCoName](../../includes/ssnoversion-md.md)] 다른 응용 프로그램에서 작성 한 모든 MTF 미디어 레이블을 유지 하지만 MTF 미디어 레이블은 쓰지 않는 표준 백업 형식을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="eaf9a-153">All media that is used for a backup or restore operation use a standard backup format called [!INCLUDE[msCoName](../../includes/ssnoversion-md.md)] preserves any MTF media label written by another application but does not write MTF media labels.</span></span>

-   <span data-ttu-id="eaf9a-154">[!INCLUDE[msCoName](../../../includes/msconame-md.md)] Tape Format 미디어 레이블 또는 자유형 텍스트로 된 미디어 설명</span><span class="sxs-lookup"><span data-stu-id="eaf9a-154">The [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Tape Format media label or the media description (in free-form text).</span></span>

-   <span data-ttu-id="eaf9a-155">레이블을 기록한 백업 소프트웨어의 이름</span><span class="sxs-lookup"><span data-stu-id="eaf9a-155">The name of the backup software that wrote the label.</span></span>

-   <span data-ttu-id="eaf9a-156">미디어를 포맷한 소프트웨어 공급업체의 고유 공급업체 ID 번호</span><span class="sxs-lookup"><span data-stu-id="eaf9a-156">The unique vendor identification number of the software vendor that formatted the media.</span></span>

-   <span data-ttu-id="eaf9a-157">레이블을 작성한 날짜와 시간</span><span class="sxs-lookup"><span data-stu-id="eaf9a-157">The date and time the label was written.</span></span>

-   <span data-ttu-id="eaf9a-158">세트의 미러 개수(1-4). 1은 미러되지 않은 디바이스를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="eaf9a-158">The number of mirrors in the set (1-4); 1 indicates an unmirrored device.</span></span>

 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] <span data-ttu-id="eaf9a-159">에서는 이전 버전의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 포맷된 미디어를 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eaf9a-159">can process media formatted by earlier versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>

### <a name="backup-sets"></a><span data-ttu-id="eaf9a-160">백업 세트</span><span class="sxs-lookup"><span data-stu-id="eaf9a-160">Backup Sets</span></span>
 <span data-ttu-id="eaf9a-161">백업 작업에 성공하면 미디어 세트에 *백업 세트* 하나가 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="eaf9a-161">A successful backup operation adds a single *backup set* to the media set.</span></span> <span data-ttu-id="eaf9a-162">백업 세트는 백업이 속해 있는 미디어 세트와 관련해서 설명됩니다.</span><span class="sxs-lookup"><span data-stu-id="eaf9a-162">The backup set is described in terms of the media set to which the backup belongs.</span></span> <span data-ttu-id="eaf9a-163">백업 미디어에 미디어 패밀리가 하나뿐이면 해당 패밀리에 전체 백업 세트가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="eaf9a-163">If the backup media consists of only one media family, that family contains the entire backup set.</span></span> <span data-ttu-id="eaf9a-164">백업 미디어에 미디어 패밀리가 여러 개 있으면 백업 세트가 여러 패밀리에 분산됩니다.</span><span class="sxs-lookup"><span data-stu-id="eaf9a-164">If the backup media consists of multiple media families, the backup set is distributed among them.</span></span> <span data-ttu-id="eaf9a-165">각 미디어에서 백업 세트를 설명하는 헤더가 백업 세트에 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="eaf9a-165">On each medium, the backup set contains a header that describes the backup set.</span></span>

 <span data-ttu-id="eaf9a-166">다음 예에서는 테이프 드라이브 세 개를 백업 디바이스로 사용하여 [!INCLUDE[tsql](../../includes/tsql-md.md)] 데이터베이스에 대해 `MyAdvWorks_MediaSet_1` 이라는 미디어 세트를 만드는 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 문을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="eaf9a-166">The following example shows a [!INCLUDE[tsql](../../includes/tsql-md.md)] statement that creates a media set called `MyAdvWorks_MediaSet_1` for the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database using three tape drives as backup devices:</span></span>

```
BACKUP DATABASE AdventureWorks2012
TO TAPE = '\\.\tape0', TAPE = '\\.\tape1', TAPE = '\\.\tape2'
WITH 
   FORMAT,
   MEDIANAME = 'MyAdvWorks_MediaSet_1'
```

 <span data-ttu-id="eaf9a-167">이 백업 작업이 성공하면 새로운 미디어 헤더와 백업 세트 하나가 포함된 새 미디어 세트가 테이프 3개에 분산됩니다.</span><span class="sxs-lookup"><span data-stu-id="eaf9a-167">If successful, this backup operation results in a new media set containing a new media header and one backup set spread across three tapes.</span></span> <span data-ttu-id="eaf9a-168">다음 그림에서는 이러한 결과를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="eaf9a-168">The following figure illustrates these results:</span></span>

 <span data-ttu-id="eaf9a-169">![3개 테이프의 미디어 헤더 및 첫 번째 백업 세트](../../database-engine/media/bnr-mediaset-new.gif "3개 테이프의 미디어 헤더 및 첫 번째 백업 세트")</span><span class="sxs-lookup"><span data-stu-id="eaf9a-169">![Media header and first backup set on 3 tapes](../../database-engine/media/bnr-mediaset-new.gif "Media header and first backup set on 3 tapes")</span></span>

 <span data-ttu-id="eaf9a-170">일반적으로 미디어 세트가 만들어지면 다음 백업 작업에서 해당 백업 세트를 미디어 세트에 차례로 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="eaf9a-170">Typically, after a media set is created, subsequent backup operations, one after another, append their backup sets to the media set.</span></span> <span data-ttu-id="eaf9a-171">백업 세트에 사용된 모든 미디어는 포함된 미디어나 백업 디바이스 수에 관계없이 미디어 세트를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="eaf9a-171">All of the media used by a backup set make up the media set, regardless of the number of media or backup devices involved.</span></span> <span data-ttu-id="eaf9a-172">미디어 세트에서의 위치에 따라 백업 세트에 순차적으로 번호가 지정되어 복원할 백업 세트를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eaf9a-172">Backup sets are sequentially numbered by their position in the media set, allowing you to specify which backup set to restore.</span></span>

 <span data-ttu-id="eaf9a-173">미디어 세트에 대한 모든 백업 작업에서 개수와 유형이 같은 백업 디바이스에 써야 합니다.</span><span class="sxs-lookup"><span data-stu-id="eaf9a-173">Every backup operation to a media set must write to the same number and type of backup devices.</span></span> <span data-ttu-id="eaf9a-174">첫 번째 백업 세트와 마찬가지로 디바이스가 여러 개일 경우 모든 후속 백업 세트의 내용은 모든 디바이스에 있는 백업 미디어에 분산됩니다.</span><span class="sxs-lookup"><span data-stu-id="eaf9a-174">With multiple devices, as with the first backup set, the content of every subsequent backup set is distributed among the backup media on all of the devices.</span></span> <span data-ttu-id="eaf9a-175">위의 예를 계속 수행하기 위해 두 번째 백업 작업(차등 백업)에서 같은 미디어 세트에 정보를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="eaf9a-175">To continue the above example, a second backup operation (a differential backup) appends information to the same media set:</span></span>

```
BACKUP DATABASE AdventureWorks2012
TO TAPE = '\\.\tape0', TAPE = '\\.\tape1', TAPE = '\\.\tape2'
WITH 
   NOINIT,
   MEDIANAME = 'AdventureWorksMediaSet1',
   DIFFERENTIAL
```

> [!NOTE]
>  <span data-ttu-id="eaf9a-176">NOINIT 옵션은 기본값이지만 의미를 강조하기 위해 포함되었습니다.</span><span class="sxs-lookup"><span data-stu-id="eaf9a-176">The NOINIT option is the default, but is included for clarity.</span></span>

 <span data-ttu-id="eaf9a-177">두 번째 백업 작업이 성공하면 백업 내용을 다음과 같이 분산하여 두 번째 백업 세트를 미디어 세트에 씁니다.</span><span class="sxs-lookup"><span data-stu-id="eaf9a-177">If the second backup operation succeeds, it writes a second backup set to the media set, with the following distribution of backup content:</span></span>

 <span data-ttu-id="eaf9a-178">![3개 미디어 세트 테이프에 분산된 두 번째 백업 세트](../../database-engine/media/bnr-mediaset-appendedto.gif "3개 미디어 세트 테이프에 분산된 두 번째 백업 세트")</span><span class="sxs-lookup"><span data-stu-id="eaf9a-178">![Second backup set spread across 3 media-set tapes](../../database-engine/media/bnr-mediaset-appendedto.gif "Second backup set spread across 3 media-set tapes")</span></span>

 <span data-ttu-id="eaf9a-179">백업을 복원할 때 FILE 옵션을 사용하여 사용할 백업을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eaf9a-179">When you are restoring backups, you can use you the FILE option to specify which backups you want to use.</span></span> <span data-ttu-id="eaf9a-180">다음 예제에서는 **=** _데이터베이스의 전체 데이터베이스 백업을 복원한 후 동일한 미디어 세트에서 차등 데이터베이스 백업을 복원하는 경우 FILE_ backup_set_file_number [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 절의 사용을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="eaf9a-180">The following example shows the use of FILE **=**_backup_set_file_number_ clauses when restoring a full database backup of the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database followed by a differential database backup on the same media set.</span></span> <span data-ttu-id="eaf9a-181">미디어 세트는 `\\.\tape0`, `tape1`및 `tape2`의 테이프 드라이브에 있는 세 개의 백업 테이프를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="eaf9a-181">The media set uses three backup tapes, which are on tape drives `\\.\tape0`, `tape1`, and `tape2`.</span></span>

```
RESTORE DATABASE AdventureWorks2012 FROM TAPE = '\\.\tape0', TAPE = '\\.\tape1', TAPE = '\\.\tape2'
   WITH 
   MEDIANAME = 'AdventureWorksMediaSet1',
   FILE=1, 
   NORECOVERY;
RESTORE DATABASE AdventureWorks2012 FROM TAPE = '\\.\tape0', TAPE = '\\.\tape1', TAPE = '\\.\tape2' 
   WITH 
   MEDIANAME = 'AdventureWorksMediaSet1',
   FILE=2, 
   RECOVERY;
GO
```

 <span data-ttu-id="eaf9a-182">미디어 세트 및 해당 미디어 패밀리와 백업 세트 관련 정보를 저장하는 기록 테이블에 대한 자세한 내용은 [백업 기록 및 헤더 정보&#40;SQL Server&#41;](backup-history-and-header-information-sql-server.md)백업 및 복원의 기본적인 백업 미디어 관련 용어를 소개합니다.</span><span class="sxs-lookup"><span data-stu-id="eaf9a-182">For information about the history tables that store information about media sets and their media families and backup sets, see [Backup History and Header Information &#40;SQL Server&#41;](backup-history-and-header-information-sql-server.md).</span></span>

 <span data-ttu-id="eaf9a-183">미디어 세트의 백업 미디어 개수는 다음과 같은 요소에 따라 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="eaf9a-183">The number of backup media in a media set depends on several factors:</span></span>

-   <span data-ttu-id="eaf9a-184">백업 디바이스 개수</span><span class="sxs-lookup"><span data-stu-id="eaf9a-184">Number of backup devices</span></span>

-   <span data-ttu-id="eaf9a-185">백업 서비스 유형</span><span class="sxs-lookup"><span data-stu-id="eaf9a-185">Type of backup devices</span></span>

-   <span data-ttu-id="eaf9a-186">백업 세트 개수</span><span class="sxs-lookup"><span data-stu-id="eaf9a-186">Number of backup sets</span></span>

##  <a name="using-media-sets-and-families"></a><a name="ConsiderationsForMediaSetFamilies"></a><span data-ttu-id="eaf9a-187">미디어 세트 및 패밀리 사용</span><span class="sxs-lookup"><span data-stu-id="eaf9a-187">Using Media Sets and Families</span></span>
 <span data-ttu-id="eaf9a-188">이 섹션에서는 미디어 세트와 미디어 패밀리를 사용할 때의 몇 가지 고려 사항에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="eaf9a-188">This section discusses several considerations for using media sets and media families.</span></span>



###  <a name="creating-a-new-media-set"></a><a name="CreatingMediaSet"></a><span data-ttu-id="eaf9a-189">새 미디어 세트 만들기</span><span class="sxs-lookup"><span data-stu-id="eaf9a-189">Creating a New Media Set</span></span>
 <span data-ttu-id="eaf9a-190">새 미디어 세트를 만들려면 백업 미디어(하나 이상의 테이프 또는 디스크 파일)를 포맷해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="eaf9a-190">To create a new media set, you must format the backup media (one or more tapes or disk files).</span></span> <span data-ttu-id="eaf9a-191">포맷 프로세스 동안 다음과 같이 백업 미디어가 변경됩니다.</span><span class="sxs-lookup"><span data-stu-id="eaf9a-191">The formatting process changes the backup media as follows:</span></span>

1.  <span data-ttu-id="eaf9a-192">오래된 헤더(있는 경우)를 삭제하여 백업 미디어의 이전 내용을 효율적으로 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="eaf9a-192">Deletes the old header (if any), effectively deleting the previous contents of the backup media.</span></span>

     <span data-ttu-id="eaf9a-193">테이프 디바이스를 포맷하면 현재 탑재된 테이프의 이전 내용이 모두 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="eaf9a-193">Formatting a tape device deletes all previous contents of the currently mounted tape.</span></span> <span data-ttu-id="eaf9a-194">디스크를 포맷하면 백업 작업에 지정한 파일만 영향을 받습니다.</span><span class="sxs-lookup"><span data-stu-id="eaf9a-194">Formatting a disk affects only the file that you specify for the backup operation</span></span>

2.  <span data-ttu-id="eaf9a-195">각 백업 디바이스에서 백업 미디어(테이프 또는 디스크 파일)에 새 미디어 헤더를 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="eaf9a-195">Writes a new media header on the backup media (tape or disk file) on each of the backup devices.</span></span>


###  <a name="backing-up-to-an-existing-media-set"></a><a name="UseExistingMediaSet"></a><span data-ttu-id="eaf9a-196">기존 미디어 세트에 백업</span><span class="sxs-lookup"><span data-stu-id="eaf9a-196">Backing Up to an Existing Media Set</span></span>
 <span data-ttu-id="eaf9a-197">기존 미디어 세트에 백업하는 경우 다음 두 가지 옵션이 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="eaf9a-197">When you are backing up to an existing media set, you have the following two options:</span></span>

-   <span data-ttu-id="eaf9a-198">기존 백업 세트에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="eaf9a-198">Append to the existing backup set.</span></span>

     <span data-ttu-id="eaf9a-199">사용 가능한 공간을 가장 적합하게 사용하기 위해 일반적으로 새 백업 세트가 기존 미디어 세트에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="eaf9a-199">To make the best possible use of the available space, new backup sets typically are appended to existing media set.</span></span> <span data-ttu-id="eaf9a-200">백업에 추가하면 이전 백업이 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="eaf9a-200">Appending to the backup preserves any prior backups.</span></span> <span data-ttu-id="eaf9a-201">자세한 내용은 이 항목의 뒷부분에 나오는 [기존 백업 세트에 추가](#Appending)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="eaf9a-201">For more information, see [Appending to Existing Backup Sets](#Appending), later in this section.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="eaf9a-202">BACKUP의 기본 동작인 추가는 NOINIT 옵션을 사용하여 명시적으로 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eaf9a-202">Appending, which is the default behavior of the BACKUP, can be explicitly specified by using the NOINIT option.</span></span>

-   <span data-ttu-id="eaf9a-203">현재 미디어 헤더를 그대로 유지하면서 현재 백업으로 기존 백업 세트를 덮어씁니다.</span><span class="sxs-lookup"><span data-stu-id="eaf9a-203">Overwrite all existing backup sets with the current backup, leaving the current media header in place.</span></span>

     [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="eaf9a-204">에는 실수로 미디어를 덮어쓰지 않도록 하는 보호 장치가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eaf9a-204">backup has safeguards to prevent you from accidentally overwriting media.</span></span> <span data-ttu-id="eaf9a-205">그러나 백업을 사용하면 미리 정의한 만료 날짜에 이른 백업 세트를 자동으로 덮어쓸 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eaf9a-205">However, backup can automatically overwrite backup sets that have reached a predefined expiration date.</span></span>

     <span data-ttu-id="eaf9a-206">테이프 헤더는 현재 위치에 두어도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="eaf9a-206">For tape headers, leaving the header in place can make sense.</span></span> <span data-ttu-id="eaf9a-207">자세한 내용은 이 항목의 뒷부분에 나오는 [백업 세트 덮어쓰기](#Overwriting)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="eaf9a-207">For more information, see [Overwriting Backup Sets](#Overwriting), later in this section.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="eaf9a-208">기존 백업 세트를 덮어쓰는 작업은 BACKUP 문의 INIT 옵션을 사용하여 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="eaf9a-208">Overwriting existing backup sets is specified by using the INIT option of the BACKUP statement.</span></span>

####  <a name="appending-to-existing-backup-sets"></a><a name="Appending"></a><span data-ttu-id="eaf9a-209">기존 백업 세트에 추가</span><span class="sxs-lookup"><span data-stu-id="eaf9a-209">Appending to Existing Backup Sets</span></span>
 <span data-ttu-id="eaf9a-210">같거나 다른 데이터베이스에 대해 서로 다른 시간에 수행한 백업은 같은 미디어에 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eaf9a-210">Backups performed at different times from the same or different databases can be stored on the same media.</span></span> <span data-ttu-id="eaf9a-211">다른 백업 세트를 기존의 미디어에 추가하면 미디어의 이전 내용은 그대로 남아 있고 새 백업은 미디어에서 마지막 백업의 끝에 이어서 기록됩니다.</span><span class="sxs-lookup"><span data-stu-id="eaf9a-211">By appending another backup set to existing media, the previous contents of the media remain intact, and the new backup is written after the end of the last backup on the media.</span></span>

 <span data-ttu-id="eaf9a-212">기본적으로 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 는 항상 새 백업을 미디어에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="eaf9a-212">By default, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] always appends new backups to media.</span></span> <span data-ttu-id="eaf9a-213">추가는 미디어의 끝에서만 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="eaf9a-213">Appending can occur only at the end of the media.</span></span> <span data-ttu-id="eaf9a-214">예를 들어 미디어 볼륨에 백업 세트가 5개 있을 때 첫 번째 3개의 백업 세트를 건너 뛰고 네 번째 백업 세트를 새 백업 세트로 덮어쓸 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="eaf9a-214">For example, if a media volume contains five backup sets, it is not possible to skip the first three backup sets to overwrite the fourth backup set with a new backup set.</span></span>

 <span data-ttu-id="eaf9a-215">테이프 백업 시 BACKUP WITH NOREWIND를 사용하면 테이프는 작업이 끝날 때 열린 채로 남아 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eaf9a-215">If you use BACKUP WITH NOREWIND for a tape backup, the tape will be left open at the end of the operation.</span></span> <span data-ttu-id="eaf9a-216">따라서 테이프를 되감은 다음 마지막 백업 세트를 찾기 위해 앞으로 검색하지 않고 그대로 다른 백업을 테이프에 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eaf9a-216">This allows you to append further backups to the tape without rewinding the tape and then scanning forward again to find the last backup set.</span></span> <span data-ttu-id="eaf9a-217">열려 있는 테이프 드라이브 목록은 **sys.dm_io_backup_tapes** 동적 관리 뷰에 있습니다. 자세한 내용은 [sys.dm_io_backup_tapes&#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-io-backup-tapes-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="eaf9a-217">You can find the list of open tape drives in the **sys.dm_io_backup_tapes** dynamic management view; for more information, see [sys.dm_io_backup_tapes &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-io-backup-tapes-transact-sql).</span></span>

 <span data-ttu-id="eaf9a-218">Microsoft Windows 백업 및 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 백업은 같은 미디어를 공유할 수 있지만 상호 운용되지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eaf9a-218">Microsoft Windows backups and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] backups can share the same media, but they are not interoperable.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="eaf9a-219">백업에서는 Windows 데이터를 백업할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="eaf9a-219">backup cannot back up Windows data.</span></span>

> [!IMPORTANT]
>  [!INCLUDE[ssEnterpriseEd10](../../includes/sskatmai-md.md)]<span data-ttu-id="eaf9a-220">이상 버전에서는 압축 된 백업을 읽을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eaf9a-220">or later versions can read compressed backups.</span></span> <span data-ttu-id="eaf9a-221">자세한 내용은 [백업 압축&#40;SQL Server&#41;](backup-compression-sql-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="eaf9a-221">For more information, see [Backup Compression &#40;SQL Server&#41;](backup-compression-sql-server.md).</span></span>


####  <a name="overwriting-backup-sets"></a><a name="Overwriting"></a><span data-ttu-id="eaf9a-222">백업 세트 덮어쓰기</span><span class="sxs-lookup"><span data-stu-id="eaf9a-222">Overwriting Backup Sets</span></span>
 <span data-ttu-id="eaf9a-223">기존 백업 세트를 덮어쓰는 작업은 BACKUP 문의 INIT 옵션을 사용하여 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="eaf9a-223">Overwriting of existing backup sets is specified by using the INIT option of the BACKUP statement.</span></span> <span data-ttu-id="eaf9a-224">이 옵션은 미디어에 있는 모든 백업 세트를 덮어쓰고 미디어 헤더를 보관합니다(있는 경우).</span><span class="sxs-lookup"><span data-stu-id="eaf9a-224">This option overwrites all the backup sets on the media and preserve the media header, if any.</span></span> <span data-ttu-id="eaf9a-225">미디어 헤더가 없다면 하나 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="eaf9a-225">If no media header exists, one is created.</span></span>

 <span data-ttu-id="eaf9a-226">테이프 헤더는 현재 위치에 두어도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="eaf9a-226">For tape headers, leaving the header in place can make sense.</span></span> <span data-ttu-id="eaf9a-227">디스크 백업 미디어의 경우 백업 작업에서 지정하여 백업 디바이스에서 사용하는 파일만 덮어쓰므로 디스크의 다른 파일에는 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eaf9a-227">For disk backup media, only the files used by the backup devices specified in the backup operation are overwritten; other files on the disk are unaffected.</span></span> <span data-ttu-id="eaf9a-228">백업을 덮어쓸 때 기존의 미디어 헤더는 모두 보존되며 새 백업은 백업 디바이스의 첫 번째 백업으로 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="eaf9a-228">When overwriting backups, any existing media header is preserved, and the new backup is created as the first backup on the backup device.</span></span> <span data-ttu-id="eaf9a-229">기존에 미디어 헤더가 없으면 관련된 미디어 이름과 미디어 설명이 있는 유효한 미디어 헤더가 자동으로 작성됩니다.</span><span class="sxs-lookup"><span data-stu-id="eaf9a-229">If there is no existing media header, a valid media header with an associated media name and media description is written automatically.</span></span> <span data-ttu-id="eaf9a-230">기존의 미디어 헤더가 잘못되었으면 백업 작업이 종료됩니다.</span><span class="sxs-lookup"><span data-stu-id="eaf9a-230">If the existing media header is invalid, the backup operation terminates.</span></span> <span data-ttu-id="eaf9a-231">미디어가 비어 있으면 지정된 MEDIANAME, MEDIAPASSWORD 및 MEDIADESCRIPTION(있는 경우)으로 새 미디어 헤더가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="eaf9a-231">If the media is empty, the new media header is generated with the given MEDIANAME, MEDIAPASSWORD, and MEDIADESCRIPTION, if any.</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="eaf9a-232">[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]부터 MEDIAPASSWORD 옵션은 백업을 만드는 데 더 이상 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eaf9a-232">Beginning with [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], the MEDIAPASSWORD option is discontinued for creating backups.</span></span> <span data-ttu-id="eaf9a-233">하지만 암호를 사용하여 만든 백업은 계속 복원할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eaf9a-233">However, you can still restore backups created with passwords.</span></span>

 <span data-ttu-id="eaf9a-234">백업 미디어가 다음 조건 중 하나를 만족하면 덮어쓰지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eaf9a-234">Backup media is not overwritten if either of the following conditions exists:</span></span>

-   <span data-ttu-id="eaf9a-235">미디어의 기존 백업이 만료되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="eaf9a-235">The existing backups on the media have not expired.</span></span> <span data-ttu-id="eaf9a-236">건너뛰기가 지정된 경우 만료를 확인하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eaf9a-236">(If SKIP is specified, expiration is not checked.)</span></span>

     <span data-ttu-id="eaf9a-237">만료 날짜를 사용하여 백업이 만료되는 날짜를 지정하고 다른 백업으로 덮어쓸 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eaf9a-237">The expiration date specifies the date that the backup expires and can be overwritten by another backup.</span></span> <span data-ttu-id="eaf9a-238">백업을 만들 때 만료 날짜를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eaf9a-238">You can specify the expiration date when a backup is created.</span></span> <span data-ttu-id="eaf9a-239">기본적으로 만료 날짜는 **sp_configure** 로 설정된 **media retention**옵션에 따라 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="eaf9a-239">By default, the expiration date is determined by the **media retention** option set with **sp_configure**.</span></span> <span data-ttu-id="eaf9a-240">자세한 내용은 이 항목의 뒷부분에 나오는 [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)백업 및 복원의 기본적인 백업 미디어 관련 용어를 소개합니다.</span><span class="sxs-lookup"><span data-stu-id="eaf9a-240">For more information, see [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql).</span></span>

-   <span data-ttu-id="eaf9a-241">미디어 이름(제공된 경우)이 백업 미디어에 있는 이름과 일치하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eaf9a-241">The media name, if provided, does not match the name on the backup media.</span></span>

     <span data-ttu-id="eaf9a-242">미디어 이름은 미디어를 쉽게 식별하기 위해 사용되는 설명적인 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="eaf9a-242">The media name is a descriptive name used for easy identification of the media.</span></span>

 <span data-ttu-id="eaf9a-243">그러나 기존의 미디어를 덮어쓰기로 결정했으면(예를 들어 테이프의 백업이 더 이상 필요하지 않은 경우) 이 검사는 생략해도 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="eaf9a-243">If you are sure you want to overwrite the existing media (for example, if you know that the backups on the tape are no longer needed), you can explicitly skip these checks.</span></span>

 <span data-ttu-id="eaf9a-244">백업 미디어가 Microsoft Windows에 의해 암호로 보호되는 경우 Microsoft SQL Server는 해당 미디어에 기록하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eaf9a-244">If the backup media is password protected by Microsoft Windows, Microsoft SQL Server does not write to the media.</span></span> <span data-ttu-id="eaf9a-245">암호가 설정된 미디어를 덮어쓰려면 미디어를 다시 초기화해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="eaf9a-245">To overwrite media that is password protected, you must reinitialize the media.</span></span>


###  <a name="sequence-numbers"></a><a name="SequenceNumbers"></a><span data-ttu-id="eaf9a-246">시퀀스 번호</span><span class="sxs-lookup"><span data-stu-id="eaf9a-246">Sequence Numbers</span></span>
 <span data-ttu-id="eaf9a-247">미디어 세트에 미디어 패밀리가 여러 개 있거나 미디어 패밀리 안에 백업 미디어가 여러 개 있을 경우 올바른 순서가 중요합니다.</span><span class="sxs-lookup"><span data-stu-id="eaf9a-247">The correct order is important for multiple media families within a media set or multiple backup media within a media family.</span></span> <span data-ttu-id="eaf9a-248">따라서 백업은 다음과 같은 방법으로 시퀀스 번호를 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="eaf9a-248">Therefore, backup assigns sequence numbers in the following ways:</span></span>

-   <span data-ttu-id="eaf9a-249">미디어 세트 안의 순차적 미디어 패밀리</span><span class="sxs-lookup"><span data-stu-id="eaf9a-249">Sequential media families within a media set</span></span>

     <span data-ttu-id="eaf9a-250">미디어 세트 안에서는 미디어 세트 내 위치에 따라 미디어 패밀리에 순차적으로 번호가 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="eaf9a-250">Within a media set, the media families are numbered sequentially according to their position in the media set.</span></span> <span data-ttu-id="eaf9a-251">미디어 패밀리 번호는 **backupmediafamily** 테이블의 **family_sequence_number** 열에 기록됩니다.</span><span class="sxs-lookup"><span data-stu-id="eaf9a-251">The media-family number is recorded in the **family_sequence_number** column of the **backupmediafamily** table.</span></span>

-   <span data-ttu-id="eaf9a-252">미디어 패밀리 안의 실제 미디어</span><span class="sxs-lookup"><span data-stu-id="eaf9a-252">Physical media within a media family</span></span>

     <span data-ttu-id="eaf9a-253">미디어 시퀀스 번호는 미디어 패밀리 안의 실제 미디어 순서를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="eaf9a-253">A media sequence number indicates the order of the physical media within a media family.</span></span> <span data-ttu-id="eaf9a-254">초기 백업 미디어의 시퀀스 번호는 1로 지정되어</span><span class="sxs-lookup"><span data-stu-id="eaf9a-254">The sequence number is 1 for the initial backup media.</span></span> <span data-ttu-id="eaf9a-255">1로 태그를 붙이고 두 번째 미디어(첫 번째 연속 미디어)는 2로 태그를 붙이며 나머지 미디어도 이와 같은 순서로 태그를 붙입니다.</span><span class="sxs-lookup"><span data-stu-id="eaf9a-255">This is tagged with 1; the second (the first continuation tape) is tagged with 2; and so on.</span></span> <span data-ttu-id="eaf9a-256">백업을 복원하는 운영자는 백업 세트를 복원할 때 미디어 시퀀스 번호를 사용하여 올바른 순서로 정확하게 미디어를 탑재할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eaf9a-256">When the backup set is restored, the media sequence numbers make sure that the operator restoring the backup mounts the correct media in the correct order.</span></span>

###  <a name="multiple-devices"></a><a name="MultipleDevices"></a> <span data-ttu-id="eaf9a-257">여러 디바이스</span><span class="sxs-lookup"><span data-stu-id="eaf9a-257">Multiple Devices</span></span>
 <span data-ttu-id="eaf9a-258">테이프 드라이브나 디스크 파일을 여러 개 사용할 때는 다음 사항을 고려해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="eaf9a-258">When you use multiple tape drives or disk files, the following considerations apply:</span></span>

-   <span data-ttu-id="eaf9a-259">백업의 경우</span><span class="sxs-lookup"><span data-stu-id="eaf9a-259">For backup:</span></span>

     <span data-ttu-id="eaf9a-260">백업 작업에서 만든 전체 미디어 세트는 모든 후속 백업 작업에서 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="eaf9a-260">The complete media set that is created by a backup operation must be used by all subsequent backup operations.</span></span> <span data-ttu-id="eaf9a-261">예를 들어 두 가지 테이프 백업 디바이스를 사용하여 미디어 세트를 만든 경우 같은 미디어 세트의 모든 후속 백업 작업에서 두 가지 백업 디바이스를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="eaf9a-261">For example, if a media set was created by using two tape backup devices, all subsequent backup operations that involve the same media set must use two backup devices.</span></span>

-   <span data-ttu-id="eaf9a-262">복원의 경우</span><span class="sxs-lookup"><span data-stu-id="eaf9a-262">For restore:</span></span>

     <span data-ttu-id="eaf9a-263">디스크 백업에서 복원하는 경우와 온라인 복원의 경우 모든 미디어 패밀리를 동시에 탑재해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="eaf9a-263">For any restore from disk backups and for any online restore, all the all media families must be concurrently mounted.</span></span> <span data-ttu-id="eaf9a-264">테이프 백업에서 오프라인으로 복원하는 경우 더 적은 백업 디바이스의 미디어 패밀리를 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eaf9a-264">For an offline restore from tape backups, you can process the media families from fewer backup devices.</span></span> <span data-ttu-id="eaf9a-265">각 미디어 패밀리를 완전히 처리한 후에 다른 미디어 패밀리의 처리를 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eaf9a-265">Each media family must be processed completely before starting to process another media family.</span></span> <span data-ttu-id="eaf9a-266">단일 디바이스를 사용하여 복원하는 경우가 아니면 미디어 패밀리는 항상 병렬로 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="eaf9a-266">Media families are always processed in parallel, unless they are being restored with a single device.</span></span>

##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="eaf9a-267">관련 작업</span><span class="sxs-lookup"><span data-stu-id="eaf9a-267">Related Tasks</span></span>
 <span data-ttu-id="eaf9a-268">**새 미디어 세트를 만들려면**</span><span class="sxs-lookup"><span data-stu-id="eaf9a-268">**To create a new media set**</span></span>

-   <span data-ttu-id="eaf9a-269">[전체 데이터베이스 백업 만들기&#40;SQL Server&#41;](create-a-full-database-backup-sql-server.md)(**새 미디어 세트에 백업하고 기존 백업 세트 모두 지우기** 옵션)</span><span class="sxs-lookup"><span data-stu-id="eaf9a-269">[Create a Full Database Backup &#40;SQL Server&#41;](create-a-full-database-backup-sql-server.md) (**Back up to a new media set, and erase all existing backup sets** option)</span></span>

-   <span data-ttu-id="eaf9a-270">[BACKUP&#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) (FORMAT 옵션)</span><span class="sxs-lookup"><span data-stu-id="eaf9a-270">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) (FORMAT option)</span></span>

-   <xref:Microsoft.SqlServer.Management.Smo.Backup.FormatMedia%2A>

 <span data-ttu-id="eaf9a-271">**기존 미디어에 새 백업을 추가하려면**</span><span class="sxs-lookup"><span data-stu-id="eaf9a-271">**To append a new backup to existing media**</span></span>

-   <span data-ttu-id="eaf9a-272">[전체 데이터베이스 백업 만들기&#40;SQL Server&#41;](create-a-full-database-backup-sql-server.md)(**기존 백업 세트에 추가** 옵션)</span><span class="sxs-lookup"><span data-stu-id="eaf9a-272">[Create a Full Database Backup &#40;SQL Server&#41;](create-a-full-database-backup-sql-server.md) (**Append to the existing backup set** option)</span></span>

-   <span data-ttu-id="eaf9a-273">[BACKUP&#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) (NOINIT 옵션)</span><span class="sxs-lookup"><span data-stu-id="eaf9a-273">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) (NOINIT option)</span></span>

 <span data-ttu-id="eaf9a-274">**기존 백업 세트를 덮어쓰려면**</span><span class="sxs-lookup"><span data-stu-id="eaf9a-274">**To overwrite existing backup sets**</span></span>

-   <span data-ttu-id="eaf9a-275">[전체 데이터베이스 백업 만들기&#40;SQL Server&#41;](create-a-full-database-backup-sql-server.md)(**기존 백업 세트 모두 덮어쓰기** 옵션)</span><span class="sxs-lookup"><span data-stu-id="eaf9a-275">[Create a Full Database Backup &#40;SQL Server&#41;](create-a-full-database-backup-sql-server.md) (**Overwrite all existing backup sets** option)</span></span>

-   <span data-ttu-id="eaf9a-276">[BACKUP&#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) (INIT 옵션)</span><span class="sxs-lookup"><span data-stu-id="eaf9a-276">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) (INIT option)</span></span>

 <span data-ttu-id="eaf9a-277">**만료 날짜를 설정하려면**</span><span class="sxs-lookup"><span data-stu-id="eaf9a-277">**To set the expiration date**</span></span>

-   [<span data-ttu-id="eaf9a-278">백업의 만료 날짜 설정&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="eaf9a-278">Set the Expiration Date on a Backup &#40;SQL Server&#41;</span></span>](set-the-expiration-date-on-a-backup-sql-server.md)

 <span data-ttu-id="eaf9a-279">**미디어 시퀀스 번호 및 패밀리 시퀀스 번호를 보려면**</span><span class="sxs-lookup"><span data-stu-id="eaf9a-279">**To view the media sequence and family sequence numbers**</span></span>

-   [<span data-ttu-id="eaf9a-280">논리적 백업 디바이스의 속성 및 내용 보기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="eaf9a-280">View the Properties and Contents of a Logical Backup Device &#40;SQL Server&#41;</span></span>](view-the-properties-and-contents-of-a-logical-backup-device-sql-server.md)

-   <span data-ttu-id="eaf9a-281">[backupmediafamily&#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupmediafamily-transact-sql)(**family_sequence_number** 열)</span><span class="sxs-lookup"><span data-stu-id="eaf9a-281">[backupmediafamily &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupmediafamily-transact-sql) (**family_sequence_number** column)</span></span>

 <span data-ttu-id="eaf9a-282">**특정 백업 디바이스에 있는 백업 세트를 보려면**</span><span class="sxs-lookup"><span data-stu-id="eaf9a-282">**To view the backup sets on a particular backup device**</span></span>

-   [<span data-ttu-id="eaf9a-283">백업 세트의 데이터와 로그 파일 보기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="eaf9a-283">View the Data and Log Files in a Backup Set &#40;SQL Server&#41;</span></span>](view-the-data-and-log-files-in-a-backup-set-sql-server.md)

-   [<span data-ttu-id="eaf9a-284">논리적 백업 디바이스의 속성 및 내용 보기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="eaf9a-284">View the Properties and Contents of a Logical Backup Device &#40;SQL Server&#41;</span></span>](view-the-properties-and-contents-of-a-logical-backup-device-sql-server.md)

-   [<span data-ttu-id="eaf9a-285">RESTORE HEADERONLY&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="eaf9a-285">RESTORE HEADERONLY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/restore-statements-headeronly-transact-sql)

 <span data-ttu-id="eaf9a-286">**백업 디바이스에 있는 미디어의 미디어 헤더를 읽으려면**</span><span class="sxs-lookup"><span data-stu-id="eaf9a-286">**To read the media header of the media on a backup device**</span></span>

-   [<span data-ttu-id="eaf9a-287">RESTORE LABELONLY&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="eaf9a-287">RESTORE LABELONLY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/restore-statements-labelonly-transact-sql)


## <a name="see-also"></a><span data-ttu-id="eaf9a-288">참고 항목</span><span class="sxs-lookup"><span data-stu-id="eaf9a-288">See Also</span></span>
 <span data-ttu-id="eaf9a-289">[SQL Server 데이터베이스의 백업 및 복원](back-up-and-restore-of-sql-server-databases.md) [&#40;백업 및 복원 중에 미디어 오류가 발생할 수 있습니다. SQL Server&#41;](possible-media-errors-during-backup-and-restore-sql-server.md) [백업 기록 및 헤더 정보](backup-history-and-header-information-sql-server.md) &#40;SQL Server&#41;의 백업 기록 및 헤더 정보 &#40;[SQL Server&#41;&#40;](mirrored-backup-media-sets-sql-server.md) [백업](/sql/t-sql/statements/backup-transact-sql)&#41;&#40;transact-sql&#41;복원 [&#40;](/sql/t-sql/statements/restore-statements-transact-sql) transact-sql&#41;restore [REWINDONLY sp_configure](/sql/t-sql/statements/restore-statements-rewindonly-transact-sql) transact-sql &#40;[&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)</span><span class="sxs-lookup"><span data-stu-id="eaf9a-289">[Back Up and Restore of SQL Server Databases](back-up-and-restore-of-sql-server-databases.md) [Possible Media Errors During Backup and Restore &#40;SQL Server&#41;](possible-media-errors-during-backup-and-restore-sql-server.md) [Backup History and Header Information &#40;SQL Server&#41;](backup-history-and-header-information-sql-server.md) [Mirrored Backup Media Sets &#40;SQL Server&#41;](mirrored-backup-media-sets-sql-server.md) [BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) [RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) [RESTORE REWINDONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-rewindonly-transact-sql) [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)</span></span>


