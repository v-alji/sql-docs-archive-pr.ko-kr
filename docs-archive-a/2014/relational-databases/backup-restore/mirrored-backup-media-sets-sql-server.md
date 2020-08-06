---
title: 미러된 백업 미디어 세트(SQL Server) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- recovery [SQL Server], mirrored backups
- mirrored media sets [SQL Server]
- backup mirrors [SQL Server]
- duplicate backup copies
- interchangeable backup copies [SQL Server]
- media sets [SQL Server], mirrored backup media sets
- backup media [SQL Server], mirrored media
ms.assetid: 05a0b8d1-3585-4f77-972f-69d1c0d4aa9b
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: ce3513c67a0087dd00021de75f360b19819b46db
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660637"
---
# <a name="mirrored-backup-media-sets-sql-server"></a><span data-ttu-id="a78d2-102">미러된 백업 미디어 세트(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="a78d2-102">Mirrored Backup Media Sets (SQL Server)</span></span>
    
> [!NOTE]  
>  <span data-ttu-id="a78d2-103">미러된 백업 미디어 세트는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Enterprise Edition에서만 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="a78d2-103">Mirrored backup media sets are supported only in the Enterprise edition of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="a78d2-104">미디어 세트를 미러링하면 백업 디바이스의 오작동에 따른 영향이 감소되어 백업 안정성이 향상됩니다.</span><span class="sxs-lookup"><span data-stu-id="a78d2-104">Mirroring a media set increases backup reliability by reducing the impact of backup-device malfunctions.</span></span> <span data-ttu-id="a78d2-105">데이터 손실을 방지할 수 있는 최후의 수단이 백업이므로 이러한 오작동은 매우 심각합니다.</span><span class="sxs-lookup"><span data-stu-id="a78d2-105">These malfunctions are very serious because backups are the last line of defense against data loss.</span></span> <span data-ttu-id="a78d2-106">데이터베이스가 커지면 백업 디바이스 또는 미디어의 실패로 복원 불가능한 백업을 만들게 될 가능성이 커집니다.</span><span class="sxs-lookup"><span data-stu-id="a78d2-106">As databases grow, the probability increases that a failure of a backup device or media will make a backup nonrestorable.</span></span> <span data-ttu-id="a78d2-107">백업 미디어를 미러링하면 중복이 가능하여 백업의 안정성이 향상됩니다.</span><span class="sxs-lookup"><span data-stu-id="a78d2-107">Mirroring backup media increases the reliability of backups by providing redundancy.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a78d2-108">일반적인 미디어 세트에 대한 자세한 내용은 [미디어 세트, 미디어 패밀리 및 백업 세트&#40;SQL Server&#41;](media-sets-media-families-and-backup-sets-sql-server.md)Enterprise Edition에서만 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="a78d2-108">For information about media sets in general, see [Media Sets, Media Families, and Backup Sets &#40;SQL Server&#41;](media-sets-media-families-and-backup-sets-sql-server.md).</span></span>  
  
 <span data-ttu-id="a78d2-109">**항목 내용:**</span><span class="sxs-lookup"><span data-stu-id="a78d2-109">**In this Topic:**</span></span>  
  
-   [<span data-ttu-id="a78d2-110">미러된 미디어 세트 개요</span><span class="sxs-lookup"><span data-stu-id="a78d2-110">Overview of Mirrored Media Sets</span></span>](#OverviewofMirroredMediaSets)  
  
-   [<span data-ttu-id="a78d2-111">백업 미러에 대한 하드웨어 요구 사항</span><span class="sxs-lookup"><span data-stu-id="a78d2-111">Hardware Requirements for Backup Mirrors</span></span>](#HardwareReqs)  
  
-   [<span data-ttu-id="a78d2-112">관련 작업</span><span class="sxs-lookup"><span data-stu-id="a78d2-112">Related Tasks</span></span>](#RelatedTasks)  
  
##  <a name="overview-of-mirrored-media-sets"></a><a name="OverviewofMirroredMediaSets"></a> <span data-ttu-id="a78d2-113">미러된 미디어 세트 개요</span><span class="sxs-lookup"><span data-stu-id="a78d2-113">Overview of Mirrored Media Sets</span></span>  
 <span data-ttu-id="a78d2-114">미디어 미러링은 미디어 세트의 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="a78d2-114">Media mirroring is a property of the media set.</span></span> <span data-ttu-id="a78d2-115">*미러된 미디어 세트* 는 미디어 세트의 여러 복사본(*미러*)으로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="a78d2-115">A *mirrored media set* consists of multiple copies (*mirrors*) of the media set.</span></span> <span data-ttu-id="a78d2-116">미디어 세트에는 미디어 패밀리가 하나 이상 포함되어 있으며 각각은 백업 디바이스에 해당합니다.</span><span class="sxs-lookup"><span data-stu-id="a78d2-116">A media set contains one or more media families, each of which corresponds to a backup device.</span></span> <span data-ttu-id="a78d2-117">예를 들어 BACKUP DATABASE 문의 TO 절에 디바이스가 3개 나열되어 있으면 BACKUP에서는 디바이스당 하나씩 3개의 미디어 패밀리에 데이터를 분산합니다.</span><span class="sxs-lookup"><span data-stu-id="a78d2-117">For example, if the TO clause of a BACKUP DATABASE statement lists three devices, BACKUP spreads the data among three media families, one per device.</span></span> <span data-ttu-id="a78d2-118">미디어 패밀리 및 미러의 수는 WITH FORMAT을 지정하는 BACKUP DATABASE 문으로 미디어 세트를 만들 때 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="a78d2-118">The number of media families and mirrors is defined when the media set is created (by a BACKUP DATABASE statement that specifies WITH FORMAT).</span></span>  
  
 <span data-ttu-id="a78d2-119">미러된 미디어 세트에는 2~4개의 미러가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a78d2-119">A mirrored media set possesses from two to four mirrors.</span></span> <span data-ttu-id="a78d2-120">각 미러는 미디어 세트의 모든 미디어 패밀리를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="a78d2-120">Each mirror contains all the media families in the media set.</span></span> <span data-ttu-id="a78d2-121">미러 수는 미디어 패밀리당 하나씩이며 디바이스의 수와 같아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a78d2-121">The mirrors require the same number of devices, one per media family.</span></span> <span data-ttu-id="a78d2-122">각 미러에서는 미디어 패밀리마다 별도의 백업 디바이스가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a78d2-122">Each mirror requires a separate backup device for each media family.</span></span> <span data-ttu-id="a78d2-123">예를 들어 3개의 미러가 있는 미디어 패밀리 4개로 구성된 미러된 미디어 세트에는 12개의 백업 디바이스가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a78d2-123">For example, a mirrored media set that consists of four media families with three mirrors requires twelve backup devices.</span></span> <span data-ttu-id="a78d2-124">이러한 디바이스는 모두 같아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a78d2-124">All of these devices must be equivalent.</span></span> <span data-ttu-id="a78d2-125">예를 들어 테이프 드라이브는 동일한 제조업체에서 만든 장치로 모델 번호가 같아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a78d2-125">For example, tape drives that have the same model number from the same manufacturer.</span></span>  
  
 <span data-ttu-id="a78d2-126">다음 그림에서는 두 개의 미러가 있는 미디어 패밀리 두 개로 구성된 미러된 미디어 세트의 예를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="a78d2-126">The following illustration shows an example of a mirrored media set that consists of two media families with two mirrors.</span></span> <span data-ttu-id="a78d2-127">각 미디어 패밀리에는 미디어 볼륨이 3개씩 들어 있으며 미러당 한 번씩 백업됩니다.</span><span class="sxs-lookup"><span data-stu-id="a78d2-127">Each media family contains three media volumes, which are backed up one time per mirror.</span></span>  
  
 <span data-ttu-id="a78d2-128">![미러된 미디어 세트: 미러가 2개 있는 두 패밀리](../../database-engine/media/bnr-backup-media-mirror.gif "미러된 미디어 세트: 미러가 2개 있는 두 패밀리")</span><span class="sxs-lookup"><span data-stu-id="a78d2-128">![Mirrored media set: two families with two mirrors](../../database-engine/media/bnr-backup-media-mirror.gif "Mirrored media set: two families with two mirrors")</span></span>  
  
 <span data-ttu-id="a78d2-129">미러의 해당 볼륨의 내용은 동일하므로</span><span class="sxs-lookup"><span data-stu-id="a78d2-129">Corresponding volumes on the mirrors have identical contents.</span></span> <span data-ttu-id="a78d2-130">복원할 때 서로 교환될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a78d2-130">This makes them interchangeable at restore time.</span></span> <span data-ttu-id="a78d2-131">예를 들어 위의 그림에서 테이프 2의 3번째 볼륨은 테이프 0의 3번째 볼륨과 바꾸어 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a78d2-131">For example, in the previous illustration, the third volume of tape2 is interchangeable with the third volume of tape0.</span></span>  
  
 <span data-ttu-id="a78d2-132">[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 은 디바이스에 대한 쓰기를 동기화하여 미러된 미디어의 내용이 동일하도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="a78d2-132">The [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] guarantees that the mirrored media have identical contents by synchronizing writes to the devices.</span></span> <span data-ttu-id="a78d2-133">미러 중 하나가 채워지면 나머지 미러도 모두 동시에 스팬됩니다.</span><span class="sxs-lookup"><span data-stu-id="a78d2-133">When any one of the mirrors fills, all the mirrors are spanned at one time.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="a78d2-134">미러된 미디어 세트는 미러 제거를 통해 암시적으로 분할될 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a78d2-134">A mirrored media set cannot be implicitly broken (split) by removing a mirror.</span></span> <span data-ttu-id="a78d2-135">미러의 테이프 또는 디스크가 손상되거나 다시 포맷되는 경우 해당 미러는 추가 백업에 더 이상 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a78d2-135">If any tape or disk in a mirror is damaged or reformatted, the mirror is no longer usable for additional backups.</span></span> <span data-ttu-id="a78d2-136">채워진 미러가 하나 이상 그대로 유지되는 경우 해당 미디어 세트를 읽을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a78d2-136">If at least one full mirror remains intact, the media set can be read.</span></span> <span data-ttu-id="a78d2-137">모든 미러에서 지정된 미디어 패밀리가 손실될 경우 해당 미디어 세트는 쓸모없게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a78d2-137">If every mirror loses a given media family, the media set is useless.</span></span>  
  
 <span data-ttu-id="a78d2-138">백업 및 복원 작업은 모든 미러가 있어야 하는지에 따라 다른 요구 사항이 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="a78d2-138">Backup and restore operations impose different requirements on whether all the mirrors must be present.</span></span> <span data-ttu-id="a78d2-139">미러된 미디어 세트에 쓰는(즉, 작성하거나 확장하는) 백업 작업의 경우 모든 미러가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a78d2-139">For a backup operation to write (that is, to create or extend) a mirrored media set, all the mirrors must be present.</span></span> <span data-ttu-id="a78d2-140">반대로 미러된 미디어 세트의 백업을 복원하려는 경우 각 미디어 패밀리에 하나의 미러만 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a78d2-140">In contrast, when you are restoring a backup from a mirrored media set, you can specify only a single mirror for each media family.</span></span> <span data-ttu-id="a78d2-141">패밀리 수보다 적은 수의 디바이스에서 복원할 수 있으나 각 미디어 패밀리는 한 번만 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="a78d2-141">You can restore from fewer devices than families, but each media family is processed only one time.</span></span> <span data-ttu-id="a78d2-142">그러나 오류가 발생할 때 다른 미러가 있으면 일부 복원 문제를 빨리 해결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a78d2-142">In the presence of errors, however, having the other mirrors enables some restore problems to be resolved quickly.</span></span> <span data-ttu-id="a78d2-143">손상된 미디어 볼륨은 다른 미러에서 상응하는 볼륨으로 대체할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a78d2-143">You can substitute a damaged media volume with the corresponding volume from another mirror.</span></span> <span data-ttu-id="a78d2-144">이는 RESTORE 및 RESTORE VERIFYONLY가 손상된 미디어를 다른 미러의 해당 백업 미디어 볼륨으로 대체하는 기능을 지원하기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="a78d2-144">This is because RESTORE and RESTORE VERIFYONLY support substitution of damaged media with the corresponding backup-media volume from another mirror.</span></span>  
  
##  <a name="hardware-requirements-for-backup-mirrors"></a><a name="HardwareReqs"></a> <span data-ttu-id="a78d2-145">백업 미러에 대한 하드웨어 요구 사항</span><span class="sxs-lookup"><span data-stu-id="a78d2-145">Hardware Requirements for Backup Mirrors</span></span>  
 <span data-ttu-id="a78d2-146">미러링은 디스크와 테이프에 모두 적용됩니다. 디스크는 연속 테이프를 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a78d2-146">Mirroring applies both to disk and tape (disks do not support continuation tapes).</span></span> <span data-ttu-id="a78d2-147">단일 백업 작업 또는 복원 작업에서 사용하는 모든 백업 디바이스는 같은 유형의 디스크 또는 테이프여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a78d2-147">All backup devices for a single backup or restore operation must be of the same type, disk or tape.</span></span>  
  
 <span data-ttu-id="a78d2-148">다양한 여러 종류 중에서 속성이 같은 유사한 디바이스를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a78d2-148">Within these broader classes, you must use similar devices that have the same properties.</span></span> <span data-ttu-id="a78d2-149">유사하지 않은 디바이스를 사용하면 오류 메시지(3212)가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="a78d2-149">Insufficiently similar devices generate an error message (3212).</span></span> <span data-ttu-id="a78d2-150">부합되는 디바이스를 사용하려면 동일한 디바이스, 즉 제조업체가 같고 모델 번호도 같은 드라이브만 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="a78d2-150">To avoid the risk of a device mismatch, use devices that are equivalent, such as, only drives with the same model number from the same manufacturer.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="a78d2-151">관련 작업</span><span class="sxs-lookup"><span data-stu-id="a78d2-151">Related Tasks</span></span>  
 <span data-ttu-id="a78d2-152">**미러된 백업 디바이스에 백업하려면**</span><span class="sxs-lookup"><span data-stu-id="a78d2-152">**To back up to mirrored backup devices**</span></span>  
  
-   [<span data-ttu-id="a78d2-153">미러된 미디어 세트에 백업&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="a78d2-153">Back Up to a Mirrored Media Set &#40;Transact-SQL&#41;</span></span>](back-up-to-a-mirrored-media-set-transact-sql.md)  
  
## <a name="see-also"></a><span data-ttu-id="a78d2-154">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a78d2-154">See Also</span></span>  
 <span data-ttu-id="a78d2-155">[백업 및 복원 중 발생 가능한 미디어 오류&#40;SQL Server&#41;](possible-media-errors-during-backup-and-restore-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="a78d2-155">[Possible Media Errors During Backup and Restore &#40;SQL Server&#41;](possible-media-errors-during-backup-and-restore-sql-server.md) </span></span>  
 <span data-ttu-id="a78d2-156">[RESTORE VERIFYONLY&#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-verifyonly-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="a78d2-156">[RESTORE VERIFYONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-verifyonly-transact-sql) </span></span>  
 <span data-ttu-id="a78d2-157">[백업 디바이스&#40;SQL Server&#41;](backup-devices-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="a78d2-157">[Backup Devices &#40;SQL Server&#41;](backup-devices-sql-server.md) </span></span>  
 [<span data-ttu-id="a78d2-158">미디어 세트, 미디어 패밀리 및 백업 세트&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="a78d2-158">Media Sets, Media Families, and Backup Sets &#40;SQL Server&#41;</span></span>](media-sets-media-families-and-backup-sets-sql-server.md)  
  
  
