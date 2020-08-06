---
title: 새 가용성 그룹 대화 상자 사용(SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], creating
ms.assetid: 1b0a6421-fbd4-4bb4-87ca-657f4782c433
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 811710051089dfeb402e59bf1b7f45d05c84d925
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649180"
---
# <a name="use-the-new-availability-group-dialog-box-sql-server-management-studio"></a><span data-ttu-id="e8d79-102">새 가용성 그룹 대화 상자 사용(SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="e8d79-102">Use the New Availability Group Dialog Box (SQL Server Management Studio)</span></span>
  <span data-ttu-id="e8d79-103">이 항목에서는 **의** 새 가용성 그룹 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 대화 상자를 사용하여 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 을 사용하도록 설정된 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]인스턴스에 AlwaysOn 가용성 그룹을 만드는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="e8d79-103">This topic contains information about how to use the **New Availability Group** dialog box of [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] to create an AlwaysOn availability group on instances of [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] that are enabled for [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)].</span></span> <span data-ttu-id="e8d79-104">*가용성 그룹* 은 단일 단위로 장애 조치(Failover)될 사용자 데이터베이스 집합과 장애 조치(Failover)를 지원하는 장애 조치(Failover) 파트너 집합( *가용성 복제본*이라고 함)을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="e8d79-104">An *availability group* defines a set of user databases that will fail over as a single unit and a set of failover partners, known as *availability replicas*, that support failover.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e8d79-105">가용성 그룹에 대한 소개는 [AlwaysOn 가용성 그룹 개요&#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e8d79-105">For an introduction to availability groups, see [Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md).</span></span>  
  

> [!NOTE]  
>  <span data-ttu-id="e8d79-106">가용성 그룹을 만드는 다른 방법에 대한 자세한 내용은 이 항목의 뒷부분에 있는 [관련 작업](#RelatedTasks)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e8d79-106">For information about alternative ways to create an availability group, see [Related Tasks](#RelatedTasks), later in this topic.</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="e8d79-107">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="e8d79-107">Before You Begin</span></span>  
 <span data-ttu-id="e8d79-108">가용성 그룹을 처음 만들어 보는 경우 이 섹션을 먼저 읽는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="e8d79-108">We strongly recommend that you read this section before attempting to create your first availability group.</span></span>  
  
###  <a name="prerequisites"></a><a name="PrerequisitesRestrictions"></a> <span data-ttu-id="e8d79-109">필수 조건</span><span class="sxs-lookup"><span data-stu-id="e8d79-109">Prerequisites</span></span>  
  
-   <span data-ttu-id="e8d79-110">가용성 그룹을 만들기 전에 가용성 복제본을 호스팅하는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인스턴스가 동일한 WSFC 장애 조치(Failover) 클러스터 내의 다른 WSFC(Windows Server 장애 조치(Failover) 클러스터링) 노드에 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="e8d79-110">Before creating an availability group, verify that the instances of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] that host availability replicas reside on different Windows Server Failover Clustering (WSFC) node within the same WSFC failover cluster.</span></span> <span data-ttu-id="e8d79-111">또한 각 서버 인스턴스가 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 을 사용하도록 설정되어 있고 다른 모든 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 사전 요구 사항을 충족하는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="e8d79-111">Also, verify that each of the server instance is enabled for [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] and meets all other [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] prerequisites.</span></span> <span data-ttu-id="e8d79-112">자세한 내용은 [AlwaysOn 가용성 그룹에 대한 필수 조건, 제한 사항 및 권장 사항&#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e8d79-112">For more information, we strongly recommend that you read [Prerequisites, Restrictions, and Recommendations for AlwaysOn Availability Groups &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md).</span></span>  
  
-   <span data-ttu-id="e8d79-113">가용성 그룹을 만들기 전에 가용성 복제본을 호스팅하는 모든 서버 인스턴스에 완전하게 기능하는 데이터베이스 미러링 엔드포인트가 있는지 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="e8d79-113">Before you create an availability group, ensure that every server instance that will host an availability replica has a fully functioning database mirroring endpoint.</span></span> <span data-ttu-id="e8d79-114">자세한 내용은 [데이터베이스 미러링 엔드포인트&#40;SQL Server&#41;](../../database-mirroring/the-database-mirroring-endpoint-sql-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e8d79-114">For more information, see [The Database Mirroring Endpoint &#40;SQL Server&#41;](../../database-mirroring/the-database-mirroring-endpoint-sql-server.md).</span></span>  
  
-   <span data-ttu-id="e8d79-115">**새 가용성 그룹** 대화 상자를 사용하려면 가용성 복제본을 호스팅하는 서버 인스턴스의 이름을 알고 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8d79-115">To use the **New Availability Group** dialog box, you need to know the names of the server instances that will host availability replicas.</span></span> <span data-ttu-id="e8d79-116">또한 새 가용성 그룹에 추가할 모든 데이터베이스의 이름을 알고 있어야 하며 이러한 데이터베이스는 [AlwaysOn 가용성 그룹에 대한 필수 조건, 제한 사항 및 권장 사항&#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md)에 설명된 가용성 데이터베이스 필수 조건 및 제한 사항을 충족해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8d79-116">Also, you need know the names of any databases that you intend to add to your new availability group, and you need to ensure that these databases meet the availability database prerequisites and restrictions described in [Prerequisites, Restrictions, and Recommendations for AlwaysOn Availability Groups &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md).</span></span> <span data-ttu-id="e8d79-117">잘못된 값을 입력하면 새 가용성 그룹이 작동하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e8d79-117">If you enter invalid values, the new availability group will not work.</span></span>  
  
###  <a name="limitations"></a><a name="Limitations"></a> <span data-ttu-id="e8d79-118">제한 사항</span><span class="sxs-lookup"><span data-stu-id="e8d79-118">Limitations</span></span>  
 <span data-ttu-id="e8d79-119">**새 가용성 그룹** 대화 상자에서는 다음과 같은 작업을 수행할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e8d79-119">The **New Availability Group** dialog box does not:</span></span>  
  
-   <span data-ttu-id="e8d79-120">가용성 그룹 수신기를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e8d79-120">Create an availability group listener.</span></span>  
  
-   <span data-ttu-id="e8d79-121">보조 복제본을 가용성 그룹에 조인할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e8d79-121">Join secondary replicas to the availability group.</span></span>  
  
-   <span data-ttu-id="e8d79-122">초기 데이터 동기화를 수행할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e8d79-122">Perform initial data synchronization.</span></span>  
  
 <span data-ttu-id="e8d79-123">이러한 구성 태스크에 대한 자세한 내용은 이 항목의 뒷부분에 있는 [후속 작업: 가용성 그룹을 만든 후](#FollowUp)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e8d79-123">For information about these configuration tasks, see [Follow Up: After Creating an Availability Group](#FollowUp), later in this topic.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="e8d79-124">보안</span><span class="sxs-lookup"><span data-stu-id="e8d79-124">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="e8d79-125">권한</span><span class="sxs-lookup"><span data-stu-id="e8d79-125">Permissions</span></span>  
 <span data-ttu-id="e8d79-126">CREATE AVAILABILITY GROUP 서버 권한, ALTER ANY AVAILABILITY GROUP 권한, CONTROL SERVER 권한 중 하나와 **sysadmin** 고정 서버 역할의 멤버 자격이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="e8d79-126">Requires membership in the **sysadmin** fixed server role and either CREATE AVAILABILITY GROUP server permission, ALTER ANY AVAILABILITY GROUP permission, or CONTROL SERVER permission.</span></span>  
  
##  <a name="using-the-new-availability-group-dialog-box-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="e8d79-127">새 가용성 그룹 대화 상자(SQL Server Management Studio) 사용</span><span class="sxs-lookup"><span data-stu-id="e8d79-127">Using the New Availability Group Dialog Box (SQL Server Management Studio)</span></span>  
 <span data-ttu-id="e8d79-128">**가용성 그룹을 만들려면**</span><span class="sxs-lookup"><span data-stu-id="e8d79-128">**To create an availability group**</span></span>  
  
1.  <span data-ttu-id="e8d79-129">개체 탐색기에서 주 복제본을 호스팅하는 서버 인스턴스에 연결하고 서버 이름을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e8d79-129">In Object Explorer, connect to the server instance that hosts the primary replica, and click the server name.</span></span>  
  
2.  <span data-ttu-id="e8d79-130">**AlwaysOn 고가용성** 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="e8d79-130">Expand the **AlwaysOn High Availability** node.</span></span>  
  
3.  <span data-ttu-id="e8d79-131">**가용성 그룹** 노드를 마우스 오른쪽 단추로 클릭하고 **새 가용성 그룹** 명령을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e8d79-131">Right-click the **Availability Groups** node, and select the **New Availability Group** command.</span></span>  
  
4.  <span data-ttu-id="e8d79-132">이 명령을 실행하면 **새 가용성 그룹** 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="e8d79-132">This command opens up the **New Availability Group** dialog box.</span></span>  
  
5.  <span data-ttu-id="e8d79-133">**일반** 페이지의 **가용성 그룹 이름** 필드에 새 가용성 그룹의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="e8d79-133">On the **General** page, use the **Availability group name** field to enter a name for the new availability group.</span></span> <span data-ttu-id="e8d79-134">이 이름은 WSFC 클러스터의 모든 가용성 그룹에서 고유한 올바른 SQL Server 식별자여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8d79-134">This name must be a valid SQL Server identifier that is unique across all availability groups in the WSFC cluster.</span></span> <span data-ttu-id="e8d79-135">가용성 그룹 이름의 최대 길이는 128자입니다.</span><span class="sxs-lookup"><span data-stu-id="e8d79-135">The maximum length for an availability group name is 128 characters.</span></span>  
  
6.  <span data-ttu-id="e8d79-136">**가용성 데이터베이스** 표에서 **추가** 를 클릭하고 이 가용성 그룹에 포함할 로컬 데이터베이스 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="e8d79-136">In the **Availability Databases** grid, click **Add** and enter the name of a local database that you want to belong to this availability group.</span></span> <span data-ttu-id="e8d79-137">추가할 모든 데이터베이스에 대해 이 동작을 반복합니다.</span><span class="sxs-lookup"><span data-stu-id="e8d79-137">Repeat this for every database to be added.</span></span> <span data-ttu-id="e8d79-138">**확인**을 클릭하면 지정된 데이터베이스가 가용성 그룹에 속하기 위한 사전 요구 사항을 충족하는지 여부가 확인됩니다.</span><span class="sxs-lookup"><span data-stu-id="e8d79-138">When you click **OK**, the dialog will verify whether your specified database meet the prerequisites for belonging to an availability group.</span></span> <span data-ttu-id="e8d79-139">이러한 필수 조건에 대한 자세한 내용은 [AlwaysOn 가용성 그룹에 대한 필수 조건, 제한 사항 및 권장 사항&#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e8d79-139">For information about these prerequisites, see [Prerequisites, Restrictions, and Recommendations for AlwaysOn Availability Groups &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md).</span></span>  
  
7.  <span data-ttu-id="e8d79-140">**가용성 데이터베이스** 표에서 **추가** 를 클릭하여 보조 복제본을 호스팅할 서버 인스턴스 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="e8d79-140">In the **Availability Databases** grid, click **Add** and enter the name of a server instance to host a secondary replica.</span></span> <span data-ttu-id="e8d79-141">이 대화 상자에서는 해당 인스턴스에 연결하려고 시도하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e8d79-141">The dialog will not attempt to connect to these instances.</span></span> <span data-ttu-id="e8d79-142">잘못된 서버 이름을 지정하면 보조 복제본이 추가되지만 이 복제본에는 연결할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e8d79-142">If you specify an incorrect server name, a secondary replica will be added but you will be unable to connect to that replica.</span></span>  
  
    > [!TIP]  
    >  <span data-ttu-id="e8d79-143">복제본을 추가했지만 호스트 서버 인스턴스에 연결할 수 없는 경우 해당 복제본을 제거하고 새 복제본을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="e8d79-143">If you have added a replica and cannot connect to the host server instance, you can remove the replica and add a new one.</span></span> <span data-ttu-id="e8d79-144">자세한 내용은 [가용성 그룹에서 보조 복제본 제거&#40;SQL Server&#41;](remove-a-secondary-replica-from-an-availability-group-sql-server.md) 및 [가용성 그룹에 보조 복제본 추가&#40;SQL Server&#41;](add-a-secondary-replica-to-an-availability-group-sql-server.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e8d79-144">For more information, see [Remove a Secondary Replica from an Availability Group &#40;SQL Server&#41;](remove-a-secondary-replica-from-an-availability-group-sql-server.md) and [Add a Secondary Replica to an Availability Group &#40;SQL Server&#41;](add-a-secondary-replica-to-an-availability-group-sql-server.md).</span></span>  
  
8.  <span data-ttu-id="e8d79-145">대화 상자의 **페이지 선택** 창에서 **백업 기본 설정**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e8d79-145">On the **Select a page** pane of the dialog box, click **Backup Preferences**.</span></span> <span data-ttu-id="e8d79-146">그런 다음 **백업 기본 설정** 페이지에서 복제본 역할에 따라 백업을 실행할 위치를 지정하고 이 가용성 그룹에 대한 가용성 복제본을 호스팅할 각 서버 인스턴스에 백업 속성을 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="e8d79-146">Then, on the **Backup Preferences** page, specify where backups should occur based on replica role and assign backup priorities to each server instances that will host an availability replica for this availability group.</span></span> <span data-ttu-id="e8d79-147">자세한 내용은 [가용성 그룹 속성: 새 가용성 그룹 &#40;백업 기본 설정 페이지&#41;](availability-group-properties-new-availability-group-backup-preferences-page.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e8d79-147">For more information, see [Availability Group Properties: New Availability Group &#40;Backup Preferences Page&#41;](availability-group-properties-new-availability-group-backup-preferences-page.md).</span></span>  
  
9. <span data-ttu-id="e8d79-148">가용성 그룹을 만들려면 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e8d79-148">To create the availability group, click **OK**.</span></span> <span data-ttu-id="e8d79-149">이렇게 하면 지정된 데이터베이스가 사전 요구 사항을 충족하는지 여부가 확인됩니다.</span><span class="sxs-lookup"><span data-stu-id="e8d79-149">This causes the dialog to verify whether that specified databases meet the prerequisites.</span></span>  
  
     <span data-ttu-id="e8d79-150">가용성 그룹을 만들지 않고 대화 상자를 종료하려면 **취소**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e8d79-150">To exit the dialog box without creating the availability group, click **Cancel**.</span></span>  
  
##  <a name="follow-up-after-using-the-new-availability-group-dialog-box-to-create-an-availability-group"></a><a name="FollowUp"></a> <span data-ttu-id="e8d79-151">후속 작업: 새 가용성 그룹 대화 상자를 사용하여 가용성 그룹을 만든 후</span><span class="sxs-lookup"><span data-stu-id="e8d79-151">Follow Up: After Using the New Availability Group Dialog Box to Create an Availability Group</span></span>  
  
-   <span data-ttu-id="e8d79-152">가용성 그룹의 보조 복제본을 호스팅하는 각 서버 인스턴스에 차례로 연결하여 다음 단계를 완료해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8d79-152">You will need to connect, in turn, to each server instance that is hosting a secondary replica for the availability group and complete the following steps:</span></span>  
  
    1.  <span data-ttu-id="e8d79-153">보조 복제본을 가용성 그룹에 조인합니다.</span><span class="sxs-lookup"><span data-stu-id="e8d79-153">Join the secondary replica to the availability group.</span></span> <span data-ttu-id="e8d79-154">자세한 내용은 [가용성 그룹에 보조 복제본 조인&#40;SQL Server&#41;](join-a-secondary-replica-to-an-availability-group-sql-server.md)또는 PowerShell을 사용하여 Always On 가용성 그룹에 보조 데이터베이스를 조인하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="e8d79-154">For more information, see [Join a Secondary Replica to an Availability Group &#40;SQL Server&#41;](join-a-secondary-replica-to-an-availability-group-sql-server.md).</span></span>  
  
    2.  <span data-ttu-id="e8d79-155">각 주 데이터베이스와 해당 트랜잭션 로그의 현재 백업을 복원합니다(RESTORE WITH NORECOVERY 사용).</span><span class="sxs-lookup"><span data-stu-id="e8d79-155">Restore current backups of each primary database and its transaction log (using RESTORE WITH NORECOVERY).</span></span> <span data-ttu-id="e8d79-156">자세한 내용은 [가용성 그룹에 대한 보조 데이터베이스 수동 준비&#40;SQL Server&#41;](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md)또는 PowerShell을 사용하여 Always On 가용성 그룹에 보조 데이터베이스를 조인하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="e8d79-156">For more information, see [Manually Prepare a Secondary Database for an Availability Group &#40;SQL Server&#41;](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md).</span></span>  
  
    3.  <span data-ttu-id="e8d79-157">새로 준비된 각 보조 데이터베이스를 즉시 가용성 그룹에 조인합니다.</span><span class="sxs-lookup"><span data-stu-id="e8d79-157">Immediately join each newly prepared secondary database to the availability group.</span></span> <span data-ttu-id="e8d79-158">자세한 내용은 [가용성 그룹에 보조 데이터베이스 조인&#40;SQL Server&#41;](join-a-secondary-database-to-an-availability-group-sql-server.md)인스턴스에 AlwaysOn 가용성 그룹을 만드는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="e8d79-158">For more information, see [Join a Secondary Database to an Availability Group &#40;SQL Server&#41;](join-a-secondary-database-to-an-availability-group-sql-server.md).</span></span>  
  
-   <span data-ttu-id="e8d79-159">새 가용성 그룹에 대해 가용성 그룹 수신기를 만드는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="e8d79-159">We recommend that you create an availability group listener for the new availability group.</span></span> <span data-ttu-id="e8d79-160">이렇게 하려면 현재 주 복제본을 호스팅하는 서버 인스턴스에 연결되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8d79-160">This requires that you be connected to the server instance that hosts the current primary replica.</span></span> <span data-ttu-id="e8d79-161">자세한 내용은 [가용성 그룹 수신기 만들기 또는 구성&#40;SQL Server&#41;](create-or-configure-an-availability-group-listener-sql-server.md)가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8d79-161">For more information, see [Create or Configure an Availability Group Listener &#40;SQL Server&#41;](create-or-configure-an-availability-group-listener-sql-server.md).</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="e8d79-162">관련 작업</span><span class="sxs-lookup"><span data-stu-id="e8d79-162">Related Tasks</span></span>  
 <span data-ttu-id="e8d79-163">**가용성 그룹 및 복제본 속성을 구성하려면**</span><span class="sxs-lookup"><span data-stu-id="e8d79-163">**To configure availability group and replica properties**</span></span>  
  
-   [<span data-ttu-id="e8d79-164">가용성 복제본의 가용성 모드 변경&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="e8d79-164">Change the Availability Mode of an Availability Replica &#40;SQL Server&#41;</span></span>](change-the-availability-mode-of-an-availability-replica-sql-server.md)  
  
-   [<span data-ttu-id="e8d79-165">가용성 복제본의 장애 조치(failover) 모드 변경&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="e8d79-165">Change the Failover Mode of an Availability Replica &#40;SQL Server&#41;</span></span>](change-the-failover-mode-of-an-availability-replica-sql-server.md)  
  
-   [<span data-ttu-id="e8d79-166">가용성 그룹 수신기 만들기 또는 구성&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="e8d79-166">Create or Configure an Availability Group Listener &#40;SQL Server&#41;</span></span>](create-or-configure-an-availability-group-listener-sql-server.md)  
  
-   [<span data-ttu-id="e8d79-167">유연한 장애 조치(failover) 정책을 구성하여 자동 장애 조치의 상태 제어(AlwaysOn 가용성 그룹)</span><span class="sxs-lookup"><span data-stu-id="e8d79-167">Configure the Flexible Failover Policy to Control Conditions for Automatic Failover (AlwaysOn Availability Groups)</span></span>](configure-flexible-automatic-failover-policy.md)  
  
-   [<span data-ttu-id="e8d79-168">가용성 복제본 추가 또는 수정 시 엔드포인트 URL 지정&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="e8d79-168">Specify the Endpoint URL When Adding or Modifying an Availability Replica &#40;SQL Server&#41;</span></span>](specify-endpoint-url-adding-or-modifying-availability-replica.md)  
  
-   [<span data-ttu-id="e8d79-169">가용성 복제본에 백업 구성&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="e8d79-169">Configure Backup on Availability Replicas &#40;SQL Server&#41;</span></span>](configure-backup-on-availability-replicas-sql-server.md)  
  
-   [<span data-ttu-id="e8d79-170">가용성 복제본에 대한 읽기 전용 액세스 구성&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="e8d79-170">Configure Read-Only Access on an Availability Replica &#40;SQL Server&#41;</span></span>](configure-read-only-access-on-an-availability-replica-sql-server.md)  
  
-   [<span data-ttu-id="e8d79-171">가용성 그룹에 대한 읽기 전용 라우팅 구성&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="e8d79-171">Configure Read-Only Routing for an Availability Group &#40;SQL Server&#41;</span></span>](configure-read-only-routing-for-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="e8d79-172">가용성 복제본에 대한 세션 제한 시간 변경&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="e8d79-172">Change the Session-Timeout Period for an Availability Replica &#40;SQL Server&#41;</span></span>](change-the-session-timeout-period-for-an-availability-replica-sql-server.md)  
  
 <span data-ttu-id="e8d79-173">**가용성 그룹 구성을 완료하려면**</span><span class="sxs-lookup"><span data-stu-id="e8d79-173">**To complete availability group configuration**</span></span>  
  
-   [<span data-ttu-id="e8d79-174">가용성 그룹에 보조 복제본 조인&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="e8d79-174">Join a Secondary Replica to an Availability Group &#40;SQL Server&#41;</span></span>](join-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="e8d79-175">가용성 그룹에 대한 보조 데이터베이스 준비&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="e8d79-175">Manually Prepare a Secondary Database for an Availability Group &#40;SQL Server&#41;</span></span>](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="e8d79-176">가용성 그룹에 보조 데이터베이스 조인&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="e8d79-176">Join a Secondary Database to an Availability Group &#40;SQL Server&#41;</span></span>](join-a-secondary-database-to-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="e8d79-177">가용성 그룹 수신기 만들기 또는 구성&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="e8d79-177">Create or Configure an Availability Group Listener &#40;SQL Server&#41;</span></span>](create-or-configure-an-availability-group-listener-sql-server.md)  
  
 <span data-ttu-id="e8d79-178">**가용성 그룹을 만드는 다른 방법**</span><span class="sxs-lookup"><span data-stu-id="e8d79-178">**Alternative ways to create an availability group**</span></span>  
  
-   [<span data-ttu-id="e8d79-179">가용성 그룹 마법사 사용&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="e8d79-179">Use the Availability Group Wizard &#40;SQL Server Management Studio&#41;</span></span>](use-the-availability-group-wizard-sql-server-management-studio.md)  
  
-   [<span data-ttu-id="e8d79-180">가용성 그룹 만들기&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="e8d79-180">Create an Availability Group &#40;Transact-SQL&#41;</span></span>](create-an-availability-group-transact-sql.md)  
  
-   [<span data-ttu-id="e8d79-181">가용성 그룹 만들기&#40;SQL Server PowerShell&#41;</span><span class="sxs-lookup"><span data-stu-id="e8d79-181">Create an Availability Group &#40;SQL Server PowerShell&#41;</span></span>](../../../powershell/sql-server-powershell.md)  
  
 <span data-ttu-id="e8d79-182">**AlwaysOn 가용성 그룹을 사용하도록 설정하려면**</span><span class="sxs-lookup"><span data-stu-id="e8d79-182">**To enable AlwaysOn Availability Groups**</span></span>  
  
-   [<span data-ttu-id="e8d79-183">AlwaysOn 가용성 그룹 활성화 및 비활성화&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="e8d79-183">Enable and Disable AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](enable-and-disable-always-on-availability-groups-sql-server.md)  
  
 <span data-ttu-id="e8d79-184">**데이터베이스 미러링 엔드포인트를 구성하려면**</span><span class="sxs-lookup"><span data-stu-id="e8d79-184">**To configure a database mirroring endpoint**</span></span>  
  
-   [<span data-ttu-id="e8d79-185">AlwaysOn 가용성 그룹 &#40;SQL Server PowerShell에 대 한 데이터베이스 미러링 끝점을 만듭니다&#41;</span><span class="sxs-lookup"><span data-stu-id="e8d79-185">Create a Database Mirroring Endpoint for AlwaysOn Availability Groups &#40;SQL Server PowerShell&#41;</span></span>](database-mirroring-always-on-availability-groups-powershell.md)  
  
-   [<span data-ttu-id="e8d79-186">Windows 인증에 대한 데이터베이스 미러링 엔드포인트 만들기&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="e8d79-186">Create a Database Mirroring Endpoint for Windows Authentication &#40;Transact-SQL&#41;</span></span>](../../database-mirroring/create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md)  
  
-   [<span data-ttu-id="e8d79-187">데이터베이스 미러링 엔드포인트에 대한 인증서 사용&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="e8d79-187">Use Certificates for a Database Mirroring Endpoint &#40;Transact-SQL&#41;</span></span>](../../database-mirroring/use-certificates-for-a-database-mirroring-endpoint-transact-sql.md)  
  
-   [<span data-ttu-id="e8d79-188">가용성 복제본 추가 또는 수정 시 엔드포인트 URL 지정&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="e8d79-188">Specify the Endpoint URL When Adding or Modifying an Availability Replica &#40;SQL Server&#41;</span></span>](specify-endpoint-url-adding-or-modifying-availability-replica.md)  
  
 <span data-ttu-id="e8d79-189">**AlwaysOn 가용성 그룹 구성 문제를 해결하려면**</span><span class="sxs-lookup"><span data-stu-id="e8d79-189">**To troubleshoot AlwaysOn Availability Groups configuration**</span></span>  
  
-   [<span data-ttu-id="e8d79-190">삭제 된 SQL Server (AlwaysOn 가용성 그룹 구성) 문제 해결</span><span class="sxs-lookup"><span data-stu-id="e8d79-190">Troubleshoot AlwaysOn Availability Groups Configuration (SQL Server)deleted</span></span>](troubleshoot-always-on-availability-groups-configuration-sql-server.md)  
  
-   [<span data-ttu-id="e8d79-191">실패 한 파일 추가 작업 문제 해결 AlwaysOn 가용성 그룹 &#40;&#41;</span><span class="sxs-lookup"><span data-stu-id="e8d79-191">Troubleshoot a Failed Add-File Operation &#40;AlwaysOn Availability Groups&#41;</span></span>](troubleshoot-a-failed-add-file-operation-always-on-availability-groups.md)  
  
##  <a name="related-content"></a><a name="RelatedContent"></a> <span data-ttu-id="e8d79-192">관련 내용</span><span class="sxs-lookup"><span data-stu-id="e8d79-192">Related Content</span></span>  
  
-   [<span data-ttu-id="e8d79-193">고가용성 및 재해 복구를 위한 Microsoft SQL Server AlwaysOn 솔루션 가이드</span><span class="sxs-lookup"><span data-stu-id="e8d79-193">Microsoft SQL Server AlwaysOn Solutions Guide for High Availability and Disaster Recovery</span></span>](https://go.microsoft.com/fwlink/?LinkId=227600)  
  
## <a name="see-also"></a><span data-ttu-id="e8d79-194">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e8d79-194">See Also</span></span>  
 <span data-ttu-id="e8d79-195">[AlwaysOn 가용성 그룹 &#40;SQL Server 개요&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="e8d79-195">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="e8d79-196">[데이터베이스 미러링 엔드포인트&#40;SQL Server&#41;](../../database-mirroring/the-database-mirroring-endpoint-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="e8d79-196">[The Database Mirroring Endpoint &#40;SQL Server&#41;](../../database-mirroring/the-database-mirroring-endpoint-sql-server.md) </span></span>  
 <span data-ttu-id="e8d79-197">[가용성 그룹 수신기, 클라이언트 연결 및 애플리케이션 장애 조치(failover)&#40;SQL Server&#41;](../../listeners-client-connectivity-application-failover.md) </span><span class="sxs-lookup"><span data-stu-id="e8d79-197">[Availability Group Listeners, Client Connectivity, and Application Failover &#40;SQL Server&#41;](../../listeners-client-connectivity-application-failover.md) </span></span>  
 [<span data-ttu-id="e8d79-198">AlwaysOn 가용성 그룹 &#40;SQL Server에 대 한 필수 조건, 제한 사항 및 권장 사항&#41;</span><span class="sxs-lookup"><span data-stu-id="e8d79-198">Prerequisites, Restrictions, and Recommendations for AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](prereqs-restrictions-recommendations-always-on-availability.md)  
