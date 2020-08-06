---
title: 초기 데이터 동기화 페이지 선택 (AlwaysOn 가용성 그룹 마법사) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.addreplicawizard.selectinitialdatasync.f1
- sql12.swb.adddatabasewizard.selectinitialdatasync.f1
- sql12.swb.newagwizard.selectinitialdatasync.f1
ms.assetid: 457b1140-4819-4def-8f7c-54a406e6db12
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 20f7d8fbe6f885136e030c80719f2e16d1c689f9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740467"
---
# <a name="select-initial-data-synchronization-page-alwayson-availability-group-wizards"></a><span data-ttu-id="fd96c-102">초기 데이터 동기화 페이지 선택(AlwaysOn 가용성 그룹 마법사)</span><span class="sxs-lookup"><span data-stu-id="fd96c-102">Select Initial Data Synchronization Page (AlwaysOn Availability Group Wizards)</span></span>
  <span data-ttu-id="fd96c-103">AlwaysOn **초기 데이터 동기화 선택** 페이지를 사용하여 새 보조 데이터베이스의 초기 데이터 동기화에 대한 기본 설정을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="fd96c-103">Use the AlwaysOn **Select Initial Data Synchronization** page to indicate your preference for initial data synchronization of new secondary databases.</span></span> <span data-ttu-id="fd96c-104">이 페이지는 세 가지 마법사([!INCLUDE[ssAoNewAgWiz](../../../includes/ssaonewagwiz-md.md)], [!INCLUDE[ssAoAddRepWiz](../../../includes/ssaoaddrepwiz-md.md)]및 [!INCLUDE[ssAoAddDbWiz](../../../includes/ssaoadddbwiz-md.md)])에서 공유됩니다.</span><span class="sxs-lookup"><span data-stu-id="fd96c-104">This page is shared by three wizards-the [!INCLUDE[ssAoNewAgWiz](../../../includes/ssaonewagwiz-md.md)], the [!INCLUDE[ssAoAddRepWiz](../../../includes/ssaoaddrepwiz-md.md)], and the [!INCLUDE[ssAoAddDbWiz](../../../includes/ssaoadddbwiz-md.md)].</span></span>  
  
 <span data-ttu-id="fd96c-105">가능한 선택 항목에는 **전체**, **조인만**또는 **초기 데이터 동기화 건너뛰기**등이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fd96c-105">The possible choices include **Full**, **Join only**, or **Skip initial data synchronization**.</span></span> <span data-ttu-id="fd96c-106">**전체** 또는 **조인만** 을 선택하기 전에 현재 환경이 사전 요구 사항을 충족하는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="fd96c-106">Before you select **Full** or **Join only** ensure that your environment meets the prerequisites.</span></span>  
  

  
##  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="fd96c-107">권장 사항</span><span class="sxs-lookup"><span data-stu-id="fd96c-107">Recommendations</span></span>  
  
-   <span data-ttu-id="fd96c-108">초기 데이터 동기화 동안 주 데이터베이스에 대한 로그 백업 태스크를 일시 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="fd96c-108">Suspend log backup tasks for the primary databases during initial data synchronization.</span></span>  
  
-   <span data-ttu-id="fd96c-109">큰 데이터베이스에 대한 전체 백업 및 복원 작업에는 많은 시간과 자원이 소모될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fd96c-109">For large database, full backup and restore operations can take extensive time and resources.</span></span> <span data-ttu-id="fd96c-110">이러한 경우 보조 데이터베이스를 직접 준비하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="fd96c-110">In such cases, we recommend that you prepare secondary databases yourself.</span></span> <span data-ttu-id="fd96c-111">자세한 내용은 이 항목의 뒷부분에 나오는 [수동으로 보조 데이터베이스를 준비하려면](#PrepareSecondaryDbs)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fd96c-111">For more information, see [To Prepare Secondary Databases Manually](#PrepareSecondaryDbs), later in this topic.</span></span>  
  
-   <span data-ttu-id="fd96c-112">전체 초기 데이터 동기화를 수행하려면 네트워크 공유를 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fd96c-112">Full initial data synchronization requires you to specify a network share.</span></span> <span data-ttu-id="fd96c-113">마법사를 사용하여 전체 초기 데이터 동기화를 수행하기 전에 네트워크 공유 폴더의 액세스 권한에 대해 보안 계획을 구현하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="fd96c-113">Before you use a wizard to perform full initial data synchronization, we recommend that you implement a security plan for the access permissions on the network share folder.</span></span> <span data-ttu-id="fd96c-114">폴더에 대해 READ 권한이 있는 사람이 백업 파일의 중요한 데이터에 액세스할 수 있으므로 이 예방 조치가 중요합니다.</span><span class="sxs-lookup"><span data-stu-id="fd96c-114">This precaution is important because potentially sensitive data in the backup file can be accessed by anyone who has a READ permission on the folder.</span></span> <span data-ttu-id="fd96c-115">또한 백업 및 복원 작업을 보호하려면 가용성 복제본을 호스팅하는 모든 서버 인스턴스와 네트워크 공유 폴더 사이의 네트워크 채널에 대해 보안을 유지하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="fd96c-115">Also, to protect your backup and restore operations, we recommend that you secure the network channels between every server instance that hosts an availability replica and the network share folder.</span></span>  
  
     <span data-ttu-id="fd96c-116">백업 및 복원 작업에 대해 엄격히 보안을 유지해야 하는 경우 **조인만** 또는 **초기 데이터 동기화 건너뛰기** 옵션을 선택하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="fd96c-116">If your backup and restore operations must be highly secured, we recommend that you select either the **Join only** or **Skip initial data synchronization** option.</span></span>  
  
##  <a name="full"></a><a name="Full"></a><span data-ttu-id="fd96c-117">차지</span><span class="sxs-lookup"><span data-stu-id="fd96c-117">Full</span></span>  
 <span data-ttu-id="fd96c-118">각 주 데이터베이스에 대해 **전체** 옵션은 하나의 워크플로에서 여러 작업을 수행합니다. 예를 들어 주 데이터베이스의 전체 및 로그 백업 만들기, 보조 복제본을 호스팅하는 모든 서버 인스턴스에서 이러한 백업을 복원하여 해당 보조 데이터베이스 만들기, 가용성 그룹에 각 보조 데이터베이스 조인 등의 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fd96c-118">For each primary database, the **Full** option performs several operations in one workflow:  create a full and log backup of the primary database, create the corresponding secondary databases by restoring these backups on every server instance that is hosting a secondary replica, and join each secondary database to availability group.</span></span>  
  
 <span data-ttu-id="fd96c-119">현재 환경이 전체 초기 데이터 동기화를 사용하기 위한 다음 사전 요구 사항을 충족하고 마법사를 사용하여 데이터 동기화를 자동으로 시작하려는 경우에만 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="fd96c-119">Select this option only if your environment meets the following prerequisites for using full initial data synchronization, and you want the wizard to automatically start data synchronization.</span></span>  
  
 <span data-ttu-id="fd96c-120">**전체 초기 데이터 동기화를 사용하기 위한 사전 요구 사항**</span><span class="sxs-lookup"><span data-stu-id="fd96c-120">**Prerequisites for using full initial data synchronization**</span></span>  
  
-   <span data-ttu-id="fd96c-121">모든 데이터베이스 파일 경로는 가용성 그룹에 대한 복제본을 호스팅하는 모든 서버 인스턴스에서 동일해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fd96c-121">All the database-file paths must be identical on every server instance that hosts a replica for the availability group.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="fd96c-122">마법사를 실행하는 서버 인스턴스와 보조 복제본을 호스팅할 서버 인스턴스 간에 백업 및 복원 파일 경로가 다른 경우,</span><span class="sxs-lookup"><span data-stu-id="fd96c-122">If the backup and restore file paths differ between the server instance where you run the wizard and any server instance that is to host a secondary replica.</span></span> <span data-ttu-id="fd96c-123">WITH MOVE 옵션을 사용하여 수동으로 백업 및 복원 작업을 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fd96c-123">The backup and restore operations must be performed manually using the WITH MOVE option.</span></span> <span data-ttu-id="fd96c-124">자세한 내용은 이 항목의 뒷부분에 나오는 [수동으로 보조 데이터베이스를 준비하려면](#PrepareSecondaryDbs)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fd96c-124">For more information, see [To Prepare Secondary Databases Manually](#PrepareSecondaryDbs), later in this topic.</span></span>  
  
-   <span data-ttu-id="fd96c-125">보조 복제본을 호스팅하는 서버 인스턴스에 주 데이터베이스 이름이 없을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fd96c-125">No primary database name can exist on any server instance that hosts a secondary replica.</span></span> <span data-ttu-id="fd96c-126">즉, 새 보조 데이터베이스가 아직 없을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fd96c-126">This means that none of the new secondary databases can exist yet.</span></span>  
  
-   <span data-ttu-id="fd96c-127">마법사에서 백업을 만들고 액세스하려면 네트워크 공유를 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fd96c-127">You will need to specify a network share in order for the wizard to create and access backups.</span></span> <span data-ttu-id="fd96c-128">주 복제본의 경우 [!INCLUDE[ssDE](../../../includes/ssde-md.md)] 을 시작하는 데 사용되는 계정은 네트워크 공유에 대한 읽기 및 쓰기 파일 시스템 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fd96c-128">For the primary replica, the account used to start the [!INCLUDE[ssDE](../../../includes/ssde-md.md)] must have read and write file-system permissions on a network share.</span></span> <span data-ttu-id="fd96c-129">보조 복제본에 대한 계정은 네트워크 공유에 대한 읽기 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fd96c-129">For secondary replicas, the account must have read permission on the network share.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="fd96c-130">로그 백업이 로그 백업 체인의 일부입니다.</span><span class="sxs-lookup"><span data-stu-id="fd96c-130">The log backups will be part of your log backup chain.</span></span> <span data-ttu-id="fd96c-131">로그 백업 파일을 적절히 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="fd96c-131">Store the log backup files appropriately.</span></span>  
  
 <span data-ttu-id="fd96c-132">**사전 요구 사항이 충족되지 않는 경우**</span><span class="sxs-lookup"><span data-stu-id="fd96c-132">**If prerequisites are not met**</span></span>  
  
 <span data-ttu-id="fd96c-133">마법사에서 이 가용성 그룹에 대한 보조 데이터베이스를 만들 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="fd96c-133">The wizard cannot create the secondary databases for this availability group.</span></span> <span data-ttu-id="fd96c-134">보조 데이터를 준비하는 방법에 대한 자세한 내용은 이 항목의 뒷부분에 나오는 [수동으로 보조 데이터베이스를 준비하려면](#PrepareSecondaryDbs)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fd96c-134">For information on how to prepare them, see [To Prepare Secondary Databases Manually](#PrepareSecondaryDbs), later in this topic.</span></span>  
  
 <span data-ttu-id="fd96c-135">**사전 요구 사항이 충족되는 경우**</span><span class="sxs-lookup"><span data-stu-id="fd96c-135">**If prerequisites are met**</span></span>  
  
 <span data-ttu-id="fd96c-136">이러한 사전 요구 사항이 모두 충족되고 마법사를 사용하여 전체 초기 데이터 동기화를 수행하려면 **전체** 옵션을 선택하고 네트워크 공유를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="fd96c-136">If these prerequisites are all met and you want the wizard to perform full initial data synchronization, select the **Full** option and specify a network share.</span></span> <span data-ttu-id="fd96c-137">그러면 마법사가 선택한 모든 데이터베이스에 대해 전체 데이터베이스 및 로그 백업를 만들고 지정한 네트워크 공유에 이러한 백업을 배치합니다.</span><span class="sxs-lookup"><span data-stu-id="fd96c-137">This will cause  the wizard to create full database and log backups of every selected database and to place these backups on the network share that you specify.</span></span> <span data-ttu-id="fd96c-138">그런 다음 새로운 보조 복제본 중 하나를 호스팅하는 모든 서버 인스턴스에서 마법사는 RESTORE WITH NORECOVERY를 사용하여 백업을 복원하는 방법으로 보조 데이터베이스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="fd96c-138">Then, on every server instance that hosts one of the new secondary replicas, the wizard will create the secondary databases by restoring backups using RESTORE WITH NORECOVERY.</span></span> <span data-ttu-id="fd96c-139">각 보조 데이터베이스를 만든 후 마법사는 새 보조 데이터베이스를 가용성 그룹에 조인합니다.</span><span class="sxs-lookup"><span data-stu-id="fd96c-139">After creating each of the secondary databases, the wizard will join the new secondary database to the availability group.</span></span> <span data-ttu-id="fd96c-140">보조 데이터베이스가 조인되는 즉시 해당 데이터베이스에서 데이터 동기화가 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="fd96c-140">As soon as a secondary database is joined, data synchronizations starts on that database.</span></span>  
  
 <span data-ttu-id="fd96c-141">**모든 복제본에서 액세스할 수 있는 공유 네트워크 위치 지정**</span><span class="sxs-lookup"><span data-stu-id="fd96c-141">**Specify a shared network location accessible by all replicas**</span></span>  
 <span data-ttu-id="fd96c-142">백업을 만들고 복원하려면 마법사에서 네트워크 공유를 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fd96c-142">To create and restore backups, the wizard requires that you specify a network share.</span></span> <span data-ttu-id="fd96c-143">가용성 복제본을 호스팅하는 각 서버 인스턴스에서 [!INCLUDE[ssDE](../../../includes/ssde-md.md)] 을 시작하는 데 사용하는 계정은 네트워크 공유에 대한 읽기 및 쓰기 파일 시스템 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fd96c-143">The account used to start the [!INCLUDE[ssDE](../../../includes/ssde-md.md)] on each server instance that will host an availability replica must have read and write file-system permissions on the network share.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="fd96c-144">로그 백업이 로그 백업 체인의 일부입니다.</span><span class="sxs-lookup"><span data-stu-id="fd96c-144">The log backups will be part of your log backup chain.</span></span> <span data-ttu-id="fd96c-145">백업 파일을 적절히 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="fd96c-145">Store their backup files appropriately.</span></span>  
  
##  <a name="join-only"></a><a name="Joinonly"></a><span data-ttu-id="fd96c-146">조인만</span><span class="sxs-lookup"><span data-stu-id="fd96c-146">Join only</span></span>  
 <span data-ttu-id="fd96c-147">가용성 그룹의 보조 복제본을 호스팅하는 각 서버 인스턴스에 새 보조 데이터베이스가 이미 있는 경우에만 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="fd96c-147">Select this option only if the new secondary databases already exist on each server instance that hosts a secondary replica for the availability group.</span></span> <span data-ttu-id="fd96c-148">보조 데이터베이스 준비에 대한 자세한 내용은 이 섹션의 뒷부분에 나오는 [수동으로 보조 데이터베이스를 준비하려면](#PrepareSecondaryDbs)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fd96c-148">For information about preparing secondary databases, see [To Prepare Secondary Databases Manually](#PrepareSecondaryDbs), later in this section.</span></span>  
  
 <span data-ttu-id="fd96c-149">**조인만**을 선택하면 마법사는 각 기존 보조 데이터베이스를 가용성 그룹에 조인하려고 시도합니다.</span><span class="sxs-lookup"><span data-stu-id="fd96c-149">If you select **Join only**, the wizard will attempt to join each existing secondary database to the availability group.</span></span>  
  
## <a name="skip-initial-data-synchronization"></a><span data-ttu-id="fd96c-150">초기 데이터 동기화 건너뛰기</span><span class="sxs-lookup"><span data-stu-id="fd96c-150">Skip initial data synchronization</span></span>  
 <span data-ttu-id="fd96c-151">모든 주 데이터베이스의 데이터베이스 및 로그 백업을 직접 수행하고 보조 복제본을 호스팅하는 모든 서버 인스턴스로 복원하려는 경우에만 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="fd96c-151">Select this option if you want to perform your own database and log backups of every primary database, restore them to every server instance that hosts a secondary replica.</span></span> <span data-ttu-id="fd96c-152">마법사를 종료한 후 모든 보조 복제본에서 모든 보조 데이터베이스를 조인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fd96c-152">After you exit the wizard, you will then need to join every secondary database on every secondary replica.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="fd96c-153">자세한 내용은 [AlwaysOn 보조 데이터베이스에서 데이터 이동 시작&#40;SQL Server&#41;](start-data-movement-on-an-always-on-secondary-database-sql-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fd96c-153">For more information, see [Start Data Movement on an AlwaysOn Secondary Database &#40;SQL Server&#41;](start-data-movement-on-an-always-on-secondary-database-sql-server.md).</span></span>  
  
##  <a name="to-prepare-secondary-databases-manually"></a><a name="PrepareSecondaryDbs"></a><span data-ttu-id="fd96c-154">수동으로 보조 데이터베이스를 준비 하려면</span><span class="sxs-lookup"><span data-stu-id="fd96c-154">To Prepare Secondary Databases Manually</span></span>  
 <span data-ttu-id="fd96c-155">[!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 마법사와 독립적으로 보조 데이터베이스를 준비하려면 다음 방법 중 하나를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="fd96c-155">To prepare secondary databases independently of any [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] wizard, you can use either of the following approaches:</span></span>  
  
-   <span data-ttu-id="fd96c-156">RESTORE WITH NORECOVERY를 사용하여 주 데이터베이스의 최신 데이터베이스 백업을 수동으로 복원한 다음 RESTORE WITH NORECOVERY를 사용하여 각 후속 로그 백업을 복원합니다.</span><span class="sxs-lookup"><span data-stu-id="fd96c-156">Manually restore a recent database backup of the primary database using RESTORE WITH NORECOVERY, and then restore each subsequent log backup using RESTORE WITH NORECOVERY.</span></span> <span data-ttu-id="fd96c-157">주 데이터베이스와 보조 데이터베이스의 파일 경로가 다른 경우에는 WITH MOVE 옵션을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fd96c-157">If the primary and secondary databases have different file paths, you must use the WITH MOVE option.</span></span> <span data-ttu-id="fd96c-158">가용성 그룹의 보조 복제본을 호스팅하는 모든 서버 인스턴스에서 이 복원 시퀀스를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="fd96c-158">Perform this restore sequence on every server instance that hosts a secondary replica for the availability group.</span></span>  <span data-ttu-id="fd96c-159">[!INCLUDE[tsql](../../../includes/tsql-md.md)] 및 PowerShell을 사용하여 이러한 백업 및 복원 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fd96c-159">You can use [!INCLUDE[tsql](../../../includes/tsql-md.md)] or PowerShell to perform these backup and restore operations.</span></span>  
  
     <span data-ttu-id="fd96c-160">**자세한 내용:**</span><span class="sxs-lookup"><span data-stu-id="fd96c-160">**For more information:**</span></span>  
  
     [<span data-ttu-id="fd96c-161">가용성 그룹에 대한 보조 데이터베이스 준비&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="fd96c-161">Manually Prepare a Secondary Database for an Availability Group &#40;SQL Server&#41;</span></span>](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md)  
  
-   <span data-ttu-id="fd96c-162">하나 이상의 로그 전달 주 데이터베이스를 가용성 그룹에 추가하는 경우 로그 전달에서 하나 이상의 해당 보조 데이터베이스를 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]로 마이그레이션할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fd96c-162">If you are adding one or more log shipping primary databases to an availability group, you might be able to migrate one or more of the corresponding secondary databases from log shipping to [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)].</span></span> <span data-ttu-id="fd96c-163">자세한 내용은 [로그 전달에서 AlwaysOn 가용성 그룹 &#40;SQL Server&#41;로 마이그레이션하기 위한 필수 조건 ](prereqs-migrating-log-shipping-to-always-on-availability-groups.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="fd96c-163">For more information, see [Prerequisites for Migrating from Log Shipping to AlwaysOn Availability Groups &#40;SQL Server&#41;](prereqs-migrating-log-shipping-to-always-on-availability-groups.md).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="fd96c-164">가용성 그룹에 대해 모든 보조 데이터베이스를 만든 후에는 보조 복제본에서 백업을 수행할 경우 가용성 그룹의 자동화된 백업 기본 설정을 다시 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fd96c-164">After you have created all the secondary databases for the availability group, if you want to perform backups on secondary replicas, you will need to re-configure the automated backup preference of the availability group.</span></span>  
  
     <span data-ttu-id="fd96c-165">**자세한 내용:**</span><span class="sxs-lookup"><span data-stu-id="fd96c-165">**For more information:**</span></span>  
  
     [<span data-ttu-id="fd96c-166">로그 전달에서 AlwaysOn 가용성 그룹 &#40;SQL Server로 마이그레이션하기 위한 필수 구성 요소&#41;</span><span class="sxs-lookup"><span data-stu-id="fd96c-166">Prerequisites for Migrating from Log Shipping to AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](prereqs-migrating-log-shipping-to-always-on-availability-groups.md)  
  
     [<span data-ttu-id="fd96c-167">가용성 복제본에 백업 구성&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="fd96c-167">Configure Backup on Availability Replicas &#40;SQL Server&#41;</span></span>](configure-backup-on-availability-replicas-sql-server.md)  
  
 <span data-ttu-id="fd96c-168">보조 데이터베이스를 만든 후 모든 현재 로그 백업을 새 보조 데이터베이스에 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="fd96c-168">After creating a secondary database, apply all current log backups to the new secondary database.</span></span>  
  
 <span data-ttu-id="fd96c-169">필요에 따라 마법사를 실행하기 전에 모든 보조 데이터베이스를 준비할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fd96c-169">Optionally, you can prepare all the secondary databases before you run the wizard.</span></span> <span data-ttu-id="fd96c-170">그런 다음 마법사의 **초기 데이터 동기화 지정** 페이지에서 **조인만** 을 선택하여 새 보조 데이터베이스를 가용성 그룹에 자동으로 조인합니다.</span><span class="sxs-lookup"><span data-stu-id="fd96c-170">Then, on the wizard's **Specify Initial Data Synchronization** page, select **Join only** to automatically join your new secondary databases to the availability group.</span></span>  
  
##  <a name="related-tasks"></a><a name="LaunchWiz"></a> <span data-ttu-id="fd96c-171">관련 작업</span><span class="sxs-lookup"><span data-stu-id="fd96c-171">Related Tasks</span></span>  
  
-   [<span data-ttu-id="fd96c-172">새 가용성 그룹 대화 상자 사용&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="fd96c-172">Use the New Availability Group Dialog Box &#40;SQL Server Management Studio&#41;</span></span>](use-the-new-availability-group-dialog-box-sql-server-management-studio.md)  
  
-   [<span data-ttu-id="fd96c-173">가용성 그룹에 복제본 추가 마법사 사용&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="fd96c-173">Use the Add Replica to Availability Group Wizard &#40;SQL Server Management Studio&#41;</span></span>](use-the-add-replica-to-availability-group-wizard-sql-server-management-studio.md)  
  
-   [<span data-ttu-id="fd96c-174">가용성 그룹에 데이터베이스 추가 마법사 사용&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="fd96c-174">Use the Add Database to Availability Group Wizard &#40;SQL Server Management Studio&#41;</span></span>](availability-group-add-database-to-group-wizard.md)  
  
-   [<span data-ttu-id="fd96c-175">가용성 그룹 장애 조치(Failover) 마법사 사용&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="fd96c-175">Use the Fail Over Availability Group Wizard &#40;SQL Server Management Studio&#41;</span></span>](use-the-fail-over-availability-group-wizard-sql-server-management-studio.md)  
  
-   [<span data-ttu-id="fd96c-176">AlwaysOn 보조 데이터베이스에서 데이터 이동을 시작 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="fd96c-176">Start Data Movement on an AlwaysOn Secondary Database &#40;SQL Server&#41;</span></span>](start-data-movement-on-an-always-on-secondary-database-sql-server.md)  
  
-   [<span data-ttu-id="fd96c-177">가용성 그룹에 보조 데이터베이스 조인&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="fd96c-177">Join a Secondary Database to an Availability Group &#40;SQL Server&#41;</span></span>](join-a-secondary-database-to-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="fd96c-178">새 가용성 그룹 대화 상자 사용&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="fd96c-178">Use the New Availability Group Dialog Box &#40;SQL Server Management Studio&#41;</span></span>](use-the-new-availability-group-dialog-box-sql-server-management-studio.md)  
  
## <a name="see-also"></a><span data-ttu-id="fd96c-179">참고 항목</span><span class="sxs-lookup"><span data-stu-id="fd96c-179">See Also</span></span>  
 [<span data-ttu-id="fd96c-180">AlwaysOn 가용성 그룹 &#40;SQL Server 개요&#41;</span><span class="sxs-lookup"><span data-stu-id="fd96c-180">Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](overview-of-always-on-availability-groups-sql-server.md)  
  
  
