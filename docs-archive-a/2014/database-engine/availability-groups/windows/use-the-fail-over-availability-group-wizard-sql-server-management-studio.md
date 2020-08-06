---
title: 가용성 그룹 장애 조치 마법사 사용(SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.failoverwizard.progress.f1
- sql12.swb.failoverwizard.f1
- sql12.swb.failoverwizard.selectnewprimary.f1
- sql12.swb.failoverwizard.confirmdataloss.f1
- sql12.swb.failoverwizard.connecttoreplicas.f1
helpviewer_keywords:
- failover [SQL Server], failover
- Availability Groups [SQL Server], wizards
- Availability Groups [SQL Server], configuring
ms.assetid: 4a602584-63e4-4322-aafc-5d715b82b834
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 6bd059712aae9c23ebbda107370ad112d7917cd5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649179"
---
# <a name="use-the-fail-over-availability-group-wizard-sql-server-management-studio"></a><span data-ttu-id="3d6ce-102">가용성 그룹 장애 조치(Failover) 마법사 사용(SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="3d6ce-102">Use the Fail Over Availability Group Wizard (SQL Server Management Studio)</span></span>
  <span data-ttu-id="3d6ce-103">이 항목에서는 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]에서 [!INCLUDE[tsql](../../../includes/tsql-md.md)], [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 또는 PowerShell을 사용하여 AlwaysOn 가용성 그룹에 대해 계획된 수동 장애 조치(failover) 또는 강제 수동 장애 조치(강제 장애 조치)를 수행하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="3d6ce-103">This topic describes how to perform a planned manual failover or forced manual failover (forced failover) on an AlwaysOn availability group by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)], or PowerShell in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="3d6ce-104">가용성 그룹은 가용성 복제본의 수준에서 장애 조치(Failover)됩니다.</span><span class="sxs-lookup"><span data-stu-id="3d6ce-104">An availability group fails over at the level of an availability replica.</span></span> <span data-ttu-id="3d6ce-105">SYNCHRONIZED 상태의 보조 복제본으로 장애 조치하는 경우 마법사는 계획된 수동 장애 조치(데이터가 손실되지 않음)를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="3d6ce-105">If you fail over to a secondary replica in the SYNCHRONIZED state, the wizard performs a planned manual failover (without data loss).</span></span> <span data-ttu-id="3d6ce-106">UNSYNCHRONIZED 또는 NOT SYNCHRONIZING 상태의 보조 복제본으로 장애 조치하는 경우 마법사는 *강제 장애 조치*(데이터가 손실될 수 있음)로 강제 수동 장애 조치를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="3d6ce-106">If you fail over to a secondary replica in the UNSYNCHRONIZED or NOT SYNCHRONIZING state, the wizard performs a forced manual failover-also known as a *forced failover* (with possible data loss).</span></span> <span data-ttu-id="3d6ce-107">두 형태의 수동 장애 조치는 현재 연결되어 있는 보조 복제본을 주 역할로 전환합니다.</span><span class="sxs-lookup"><span data-stu-id="3d6ce-107">Both forms of manual failover transition the secondary replica to which you are connected to the primary role.</span></span> <span data-ttu-id="3d6ce-108">계획된 수동 장애 조치는 이전의 주 복제본을 보조 역할로 전환합니다.</span><span class="sxs-lookup"><span data-stu-id="3d6ce-108">A planned manual failover currently transitions the former primary replica to the secondary role.</span></span> <span data-ttu-id="3d6ce-109">강제 장애 조치가 끝난 후 이전의 주 복제본은 온라인 상태가 되면 보조 역할로 전환됩니다.</span><span class="sxs-lookup"><span data-stu-id="3d6ce-109">After a forced failover, when the former primary replica comes online, it transitions to the secondary role.</span></span>  
  


  
-   <span data-ttu-id="3d6ce-110">**[!INCLUDE[ssAoFoAgWiz](../../../includes/ssaofoagwiz-md.md)]마주보**</span><span class="sxs-lookup"><span data-stu-id="3d6ce-110">**[!INCLUDE[ssAoFoAgWiz](../../../includes/ssaofoagwiz-md.md)] pages:**</span></span>  
  
     <span data-ttu-id="3d6ce-111">[새로운 주 복제본 선택 페이지](#SelectNewPrimaryReplica) (이 항목의 뒷부분에 나옴)</span><span class="sxs-lookup"><span data-stu-id="3d6ce-111">[Select New Primary Replica page](#SelectNewPrimaryReplica) (later in this topic)</span></span>  
  
     <span data-ttu-id="3d6ce-112">[복제본에 연결 페이지](#ConnectToReplica) (이 항목의 뒷부분에 나옴)</span><span class="sxs-lookup"><span data-stu-id="3d6ce-112">[Connect to Replica page](#ConnectToReplica) (later in this topic)</span></span>  
  
     <span data-ttu-id="3d6ce-113">[잠재적인 데이터 손실 확인 페이지](#ConfirmPotentialDataLoss) (이 항목의 뒷부분에 나옴)</span><span class="sxs-lookup"><span data-stu-id="3d6ce-113">[Confirm Potential Data Loss page](#ConfirmPotentialDataLoss) (later in this topic)</span></span>  
  
     [<span data-ttu-id="3d6ce-114">AlwaysOn 가용성 그룹 마법사의 요약 페이지 &#40;&#41;</span><span class="sxs-lookup"><span data-stu-id="3d6ce-114">Summary Page &#40;AlwaysOn Availability Group Wizards&#41;</span></span>](summary-page-always-on-availability-group-wizards.md)  
  
     [<span data-ttu-id="3d6ce-115">AlwaysOn 가용성 그룹 마법사 &#40;진행률 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="3d6ce-115">Progress Page &#40;AlwaysOn Availability Group Wizards&#41;</span></span>](progress-page-always-on-availability-group-wizards.md)  
  
     [<span data-ttu-id="3d6ce-116">AlwaysOn 가용성 그룹 마법사를 &#40;결과 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="3d6ce-116">Results Page &#40;AlwaysOn Availability Group Wizards&#41;</span></span>](results-page-always-on-availability-group-wizards.md)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="3d6ce-117">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="3d6ce-117">Before You Begin</span></span>  
 <span data-ttu-id="3d6ce-118">첫 번째 계획된 수동 장애 조치를 시작하기 전에 [가용성 그룹의 계획된 수동 장애 조치(Failover) 수행&#40;SQL Server&#41;](perform-a-planned-manual-failover-of-an-availability-group-sql-server.md)또는 PowerShell을 사용하여 AlwaysOn 가용성 그룹에 대해 계획된 수동 장애 조치(failover) 또는 강제 수동 장애 조치(강제 장애 조치)를 수행하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="3d6ce-118">Before your first planned manual failover, see the "Before You Begin" section in [Perform a Planned Manual Failover of an Availability Group &#40;SQL Server&#41;](perform-a-planned-manual-failover-of-an-availability-group-sql-server.md).</span></span>  
  
 <span data-ttu-id="3d6ce-119">첫 번째 강제 장애 조치(failover)를 시작하기 전에 "시작하기 전 주의 사항" 및 "후속 작업: [가용성 그룹의 강제 수동 장애 조치(failover) 수행&#40;SQL Server&#41;](perform-a-forced-manual-failover-of-an-availability-group-sql-server.md)의 강제 장애 조치(failover) 후의 필수 작업" 세션을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3d6ce-119">Before your first forced failover, see the "Before You Begin" and "Follow Up: Essential Tasks After a Forced Failover" sections in [Perform a Forced Manual Failover of an Availability Group &#40;SQL Server&#41;](perform-a-forced-manual-failover-of-an-availability-group-sql-server.md).</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="3d6ce-120">제한 사항</span><span class="sxs-lookup"><span data-stu-id="3d6ce-120">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="3d6ce-121">장애 조치 명령은 대상 복제본에서 명령을 수락하는 즉시 반환하지만</span><span class="sxs-lookup"><span data-stu-id="3d6ce-121">A failover command returns as soon as the target secondary replica has accepted the command.</span></span> <span data-ttu-id="3d6ce-122">데이터베이스 복구는 가용성 그룹의 장애 조치가 끝난 후 비동기로 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="3d6ce-122">However, database recovery occurs asynchronously after the availability group has finished failing over.</span></span>  
  
-   <span data-ttu-id="3d6ce-123">장애 조치 시 가용성 그룹 내에서 데이터베이스 간 일관성은 유지되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3d6ce-123">Cross-database consistency across databases within the availability group is not maintained on failover.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="3d6ce-124">데이터베이스 간 트랜잭션 또는 분산 트랜잭션은 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]에서 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3d6ce-124">Cross-database transactions and distributed transactions are not supported by [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)].</span></span> <span data-ttu-id="3d6ce-125">자세한 내용은 [데이터베이스 미러링 또는 AlwaysOn 가용성 그룹에 대해 지원되지 않는 데이터베이스 간 트랜잭션&#40;SQL Server&#41;](transactions-always-on-availability-and-database-mirroring.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3d6ce-125">For more information, see [Cross-Database Transactions Not Supported For Database Mirroring or AlwaysOn Availability Groups &#40;SQL Server&#41;](transactions-always-on-availability-and-database-mirroring.md).</span></span>  
  
###  <a name="prerequisites-for-using-the-failover-availability-group-wizard"></a><a name="Prerequisites"></a> <span data-ttu-id="3d6ce-126">가용성 그룹 장애 조치 마법사를 사용하기 위한 사전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="3d6ce-126">Prerequisites for Using the Failover Availability Group Wizard</span></span>  
  
-   <span data-ttu-id="3d6ce-127">현재 사용할 수 있는 가용성 복제본을 호스팅하는 서버 인스턴스에 연결되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3d6ce-127">You must be connected to the server instance that hosts an availability replica that is currently available.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="3d6ce-128">보안</span><span class="sxs-lookup"><span data-stu-id="3d6ce-128">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="3d6ce-129">권한</span><span class="sxs-lookup"><span data-stu-id="3d6ce-129">Permissions</span></span>  
 <span data-ttu-id="3d6ce-130">가용성 그룹에 대한 ALTER AVAILABILITY GROUP 권한, CONTROL AVAILABILITY GROUP 권한, ALTER ANY AVAILABILITY GROUP 권한 또는 CONTROL SERVER 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="3d6ce-130">Requires ALTER AVAILABILITY GROUP permission on the availability group, CONTROL AVAILABILITY GROUP permission, ALTER ANY AVAILABILITY GROUP permission, or CONTROL SERVER permission.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="3d6ce-131">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="3d6ce-131">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="3d6ce-132">**가용성 그룹 장애 조치 마법사를 사용하려면**</span><span class="sxs-lookup"><span data-stu-id="3d6ce-132">**To Use the Failover Availability Group Wizard**</span></span>  
  
1.  <span data-ttu-id="3d6ce-133">개체 탐색기에서 장애 조치해야 할 가용성 그룹의 보조 복제본을 호스팅하는 서버 인스턴스에 연결하고 서버 트리를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="3d6ce-133">In Object Explorer, connect to the server instance that hosts a secondary replica of the availability group that needs to be failed over, and expand the server tree.</span></span>  
  
2.  <span data-ttu-id="3d6ce-134">**AlwaysOn 고가용성** 및 **가용성 그룹** 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="3d6ce-134">Expand the **AlwaysOn High Availability** node and the **Availability Groups** node.</span></span>  
  
3.  <span data-ttu-id="3d6ce-135">가용성 그룹 장애 조치 마법사를 시작하려면 장애 조치할 가용성 그룹을 마우스 오른쪽 단추로 클릭하고 **장애 조치(Failover)** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3d6ce-135">To launch the Failover Availability Group Wizard, right-click the availability group that you are going to fail over, and select **Failover**.</span></span>  
  
4.  <span data-ttu-id="3d6ce-136">**소개** 페이지에 제공되는 정보는 보조 복제본에 대해 계획된 장애 조치를 수행할 수 있는지 여부에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="3d6ce-136">The information presented by the **Introduction** page depends on whether any secondary replica is eligible for a planned failover.</span></span> <span data-ttu-id="3d6ce-137">페이지에 "**이 가용성 그룹에 대해 계획된 장애 조치(Failover)를 수행합니다.** "라고 표시되면 데이터 손실 없이 가용성 그룹을 장애 조치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3d6ce-137">If this page says, "**Perform a planned failover for this availability group**", you can failover the availability group without data loss.</span></span>  
  
5.  <span data-ttu-id="3d6ce-138">새로운 주 복제본( **장애 조치 대상** )이 될 보조 복제본을 선택하기 전에 *새로운 주 복제본 선택*페이지에서 현재 주 복제본의 상태와 WSFC 쿼럼의 상태를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3d6ce-138">On the **Select New Primary Replica** page, you can view the status of the current primary replica and of the WSFC quorum, before you choose the secondary replica that will become the new primary replica (the *failover target*).</span></span> <span data-ttu-id="3d6ce-139">계획된 수동 장애 조치를 수행할 경우 **장애 조치(Failover) 준비** 값이 "**데이터 손실 없음**"인 보조 복제본을 선택해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3d6ce-139">For a planned manual failover, be sure to select a secondary replica whose **Failover Readiness** value is "**No data loss**".</span></span> <span data-ttu-id="3d6ce-140">강제 장애 조치 (failover)의 경우 가능한 모든 장애 조치 대상에 대해이 값이 "**데이터 손실, 경고 ( ***#*** )**"로 표시 됩니다. 여기서은 *#* 지정 된 보조 복제본에 대해 존재 하는 경고 수를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="3d6ce-140">For a forced failover, for all the possible failover targets, this value will be "**Data loss, Warnings(***#***)**", where *#* indicates the number of warnings that exist for a given secondary replica.</span></span> <span data-ttu-id="3d6ce-141">지정된 장애 조치 대상에 대한 경고를 보려면 해당 "장애 조치(Failover) 준비" 값을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3d6ce-141">To view the warnings for a given failover target, click its "Failover Readiness" value.</span></span>  
  
     <span data-ttu-id="3d6ce-142">자세한 내용은 이 항목의 뒷부분에 나오는 [새로운 주 복제본 선택 페이지](#SelectNewPrimaryReplica)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3d6ce-142">For more information, see [Select New Primary Replica page](#SelectNewPrimaryReplica), later in this topic.</span></span>  
  
6.  <span data-ttu-id="3d6ce-143">**복제본에 연결** 페이지에서 장애 조치 대상에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="3d6ce-143">On the **Connect to Replica** page,  connect to the failover target.</span></span> <span data-ttu-id="3d6ce-144">자세한 내용은 이 항목의 뒷부분에 나오는 [복제본에 연결 페이지](#ConnectToReplica)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3d6ce-144">For more information, see [Connect to Replica page](#ConnectToReplica), later in this topic.</span></span>  
  
7.  <span data-ttu-id="3d6ce-145">강제 장애 조치를 수행하는 경우 **잠재적인 데이터 손실 확인** 페이지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="3d6ce-145">If you are performing a forced failover, the wizard displays the **Confirm Potential Data Loss** page.</span></span> <span data-ttu-id="3d6ce-146">장애 조치를 계속하려면 **데이터가 손실될 가능성이 있는 장애 조치(Failover)를 확인하려면 여기를 클릭하세요.** 를 선택해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3d6ce-146">To proceed with the failover, you must select **Click here to confirm failover with potential data loss**.</span></span> <span data-ttu-id="3d6ce-147">자세한 내용은 이 항목의 뒷부분에 나오는[잠재적인 데이터 손실 확인 페이지](#ConfirmPotentialDataLoss)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3d6ce-147">For more information, see .[Confirm Potential Data Loss page](#ConfirmPotentialDataLoss), later in this topic.</span></span>  
  
8.  <span data-ttu-id="3d6ce-148">**요약** 페이지에서, 선택한 보조 복제본으로 장애 조치할 경우 발생할 영향을 검토합니다.</span><span class="sxs-lookup"><span data-stu-id="3d6ce-148">On the **Summary** page, review the implications of failing over to the selected secondary replica.</span></span>  
  
     <span data-ttu-id="3d6ce-149">선택이 완료되었으면 필요에 따라 **스크립트** 를 클릭하여 마법사에서 실행할 단계에 대한 스크립트를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3d6ce-149">If you are satisfied with your selections, optionally click **Script** to create a script of the steps the wizard will execute.</span></span> <span data-ttu-id="3d6ce-150">그런 다음 가용성 그룹을 선택한 보조 복제본으로 장애 조치하려면 **마침**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3d6ce-150">Then, to failover the availability group to the selected secondary replica, click **Finish**.</span></span>  
  
9. <span data-ttu-id="3d6ce-151">**진행률** 페이지에 가용성 그룹 장애 조치 진행률이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="3d6ce-151">The **Progress** page displays the progress of failing over the availability group.</span></span>  
  
10. <span data-ttu-id="3d6ce-152">장애 조치 작업이 끝나면 **결과** 페이지에 결과가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="3d6ce-152">When the failover operation finishes, the **Results** page displays the result.</span></span> <span data-ttu-id="3d6ce-153">마법사가 완료되면 **닫기** 를 클릭하여 종료합니다.</span><span class="sxs-lookup"><span data-stu-id="3d6ce-153">When the wizard completes, click **Close** to exit.</span></span>  
  
     <span data-ttu-id="3d6ce-154">자세한 내용은 [결과 페이지&#40;AlwaysOn 가용성 그룹 마법사&#41;](results-page-always-on-availability-group-wizards.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3d6ce-154">For more information, see [Results Page &#40;AlwaysOn Availability Group Wizards&#41;](results-page-always-on-availability-group-wizards.md).</span></span>  
  
11. <span data-ttu-id="3d6ce-155">강제 장애 조치(failover) 작업이 끝나면 "후속 작업: [가용성 그룹의 강제 수동 장애 조치(failover) 수행&#40;SQL Server&#41;](perform-a-forced-manual-failover-of-an-availability-group-sql-server.md)의 강제 장애 조치(failover) 후의 필수 작업" 세션을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3d6ce-155">After a forced failover, see the "Follow Up: After a Forced Failover" section in the [Perform a Forced Manual Failover of an Availability Group &#40;SQL Server&#41;](perform-a-forced-manual-failover-of-an-availability-group-sql-server.md).</span></span>  
  
## <a name="help-for-pages-that-are-exclusive-to-this-wizard"></a><span data-ttu-id="3d6ce-156">이 마법사에만 있는 페이지에 대한 도움말</span><span class="sxs-lookup"><span data-stu-id="3d6ce-156">Help for Pages that are Exclusive to This Wizard</span></span>  
 <span data-ttu-id="3d6ce-157">이 섹션에서는 [!INCLUDE[ssAoFoAgWiz](../../../includes/ssaofoagwiz-md.md)]에만 있는 페이지에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="3d6ce-157">This section describes the pages that are unique to the [!INCLUDE[ssAoFoAgWiz](../../../includes/ssaofoagwiz-md.md)].</span></span>  
  
 
  
 <span data-ttu-id="3d6ce-158">이외 이 마법사의 나머지 페이지는 하나 이상의 다른 AlwaysOn 가용성 그룹 마법사와 도움말을 공유하며 별도의 F1 도움말 항목에 문서화되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3d6ce-158">The other pages of this wizard share help with one or more of the other AlwaysOn Availability Groups wizards and are documented in separate F1 help topics.</span></span>  
  
###  <a name="select-new-primary-replica-page"></a><a name="SelectNewPrimaryReplica"></a> <span data-ttu-id="3d6ce-159">Select New Primary Replica Page</span><span class="sxs-lookup"><span data-stu-id="3d6ce-159">Select New Primary Replica Page</span></span>  
 <span data-ttu-id="3d6ce-160">이 섹션에서는 **새로운 주 복제본 선택** 페이지의 옵션에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="3d6ce-160">This section describes the options of the **Select New Primary Replica** page.</span></span> <span data-ttu-id="3d6ce-161">이 페이지에서 가용성 그룹을 장애 조치할 대상 보조 복제본(장애 조치 대상)을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3d6ce-161">Use this page to select the secondary replica (failover target) to which the availability group will fail over.</span></span> <span data-ttu-id="3d6ce-162">이 복제본은 새로운 주 복제본이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3d6ce-162">This replica will become the new primary replica.</span></span>  
  
#### <a name="page-options"></a><span data-ttu-id="3d6ce-163">페이지 옵션</span><span class="sxs-lookup"><span data-stu-id="3d6ce-163">Page Options</span></span>  
 <span data-ttu-id="3d6ce-164">**현재 주 복제본**</span><span class="sxs-lookup"><span data-stu-id="3d6ce-164">**Current Primary Replica**</span></span>  
 <span data-ttu-id="3d6ce-165">현재 주 복제본의 이름을 표시합니다(복제본이 온라인 상태인 경우).</span><span class="sxs-lookup"><span data-stu-id="3d6ce-165">Displays the name of the current primary replica, if it is online.</span></span>  
  
 <span data-ttu-id="3d6ce-166">**주 복제본 상태**</span><span class="sxs-lookup"><span data-stu-id="3d6ce-166">**Primary Replica Status**</span></span>  
 <span data-ttu-id="3d6ce-167">현재 주 복제본의 상태를 표시합니다(복제본이 온라인 상태인 경우).</span><span class="sxs-lookup"><span data-stu-id="3d6ce-167">Displays the status of the current primary replica, if it is online.</span></span>  
  
 <span data-ttu-id="3d6ce-168">**쿼럼 상태**</span><span class="sxs-lookup"><span data-stu-id="3d6ce-168">**Quorum Status**</span></span>  
 <span data-ttu-id="3d6ce-169">가용성 복제본의 WSFC 쿼럼 상태를 표시하며 다음 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="3d6ce-169">Displays the WSFC quorum status for the availability replica, one of:</span></span>  
  
|<span data-ttu-id="3d6ce-170">값</span><span class="sxs-lookup"><span data-stu-id="3d6ce-170">Value</span></span>|<span data-ttu-id="3d6ce-171">Description</span><span class="sxs-lookup"><span data-stu-id="3d6ce-171">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="3d6ce-172">**일반 쿼럼**</span><span class="sxs-lookup"><span data-stu-id="3d6ce-172">**Normal quorum**</span></span>|<span data-ttu-id="3d6ce-173">클러스터가 일반 쿼럼으로 시작했습니다.</span><span class="sxs-lookup"><span data-stu-id="3d6ce-173">The cluster has started with normal quorum.</span></span>|  
|<span data-ttu-id="3d6ce-174">**강제 쿼럼**</span><span class="sxs-lookup"><span data-stu-id="3d6ce-174">**Forced quorum**</span></span>|<span data-ttu-id="3d6ce-175">클러스터가 강제 쿼럼으로 시작했습니다.</span><span class="sxs-lookup"><span data-stu-id="3d6ce-175">The cluster has started with forced quorum.</span></span>|  
|<span data-ttu-id="3d6ce-176">**알 수 없는 쿼럼 상태**</span><span class="sxs-lookup"><span data-stu-id="3d6ce-176">**Unknown quorum**</span></span>|<span data-ttu-id="3d6ce-177">클러스터 쿼럼 상태를 알 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3d6ce-177">The cluster quorum status is unavailable.</span></span>|  
|<span data-ttu-id="3d6ce-178">**해당 사항 없음**</span><span class="sxs-lookup"><span data-stu-id="3d6ce-178">**Not applicable**</span></span>|<span data-ttu-id="3d6ce-179">가용성 복제본을 호스팅하는 노드에 쿼럼이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3d6ce-179">The node that hosts the availability replica has no quorum.</span></span>|  
  
 <span data-ttu-id="3d6ce-180">자세한 내용은 [WSFC 쿼럼 모드 및 투표 구성&#40;SQL Server&#41;](../../../sql-server/failover-clusters/windows/wsfc-quorum-modes-and-voting-configuration-sql-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3d6ce-180">For more information, see [WSFC Quorum Modes and Voting Configuration &#40;SQL Server&#41;](../../../sql-server/failover-clusters/windows/wsfc-quorum-modes-and-voting-configuration-sql-server.md).</span></span>  
  
 <span data-ttu-id="3d6ce-181">**새로운 주 복제본 선택**</span><span class="sxs-lookup"><span data-stu-id="3d6ce-181">**Choose a new primary replica**</span></span>  
 <span data-ttu-id="3d6ce-182">이 표에서 새로운 주 복제본으로 설정할 보조 복제본을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3d6ce-182">Use this grid to select a secondary replica to become the new primary replica.</span></span> <span data-ttu-id="3d6ce-183">이 표의 열은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="3d6ce-183">The columns in this grid are as follows:</span></span>  
  
 <span data-ttu-id="3d6ce-184">**서버 인스턴스**</span><span class="sxs-lookup"><span data-stu-id="3d6ce-184">**Server Instance**</span></span>  
 <span data-ttu-id="3d6ce-185">보조 복제본을 호스팅하는 서버 인스턴스의 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="3d6ce-185">Displays the name of a server instance that hosts a secondary replica.</span></span>  
  
 <span data-ttu-id="3d6ce-186">**가용성 모드**</span><span class="sxs-lookup"><span data-stu-id="3d6ce-186">**Availability Mode**</span></span>  
 <span data-ttu-id="3d6ce-187">서버 인스턴스의 가용성 모드를 표시하며 다음 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="3d6ce-187">Displays the availability mode of the server instance, one of:</span></span>  
  
|<span data-ttu-id="3d6ce-188">값</span><span class="sxs-lookup"><span data-stu-id="3d6ce-188">Value</span></span>|<span data-ttu-id="3d6ce-189">Description</span><span class="sxs-lookup"><span data-stu-id="3d6ce-189">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="3d6ce-190">**동기 커밋**</span><span class="sxs-lookup"><span data-stu-id="3d6ce-190">**Synchronous commit**</span></span>|<span data-ttu-id="3d6ce-191">동기-커밋 모드에서는 동기-커밋 주 복제본이 트랜잭션을 커밋하기 전에 동기-커밋 보조 복제본이 로그 확정을 완료했음을 확인할 때까지 기다립니다.</span><span class="sxs-lookup"><span data-stu-id="3d6ce-191">Under synchronous-commit mode, before committing transactions, a synchronous-commit primary replica waits for a synchronous-commit secondary replica to acknowledge that it has finished hardening the log.</span></span> <span data-ttu-id="3d6ce-192">동기-커밋 모드에서는 지정된 보조 데이터베이스가 주 데이터베이스와 동기화되고 나면 커밋된 트랜잭션이 완전히 보호됩니다.</span><span class="sxs-lookup"><span data-stu-id="3d6ce-192">Synchronous-commit mode ensures that once a given secondary database is synchronized with the primary database, committed transactions are fully protected.</span></span>|  
|<span data-ttu-id="3d6ce-193">**비동기 커밋**</span><span class="sxs-lookup"><span data-stu-id="3d6ce-193">**Asynchronous commit**</span></span>|<span data-ttu-id="3d6ce-194">비동기-커밋 모드에서는 주 복제본이 비동기-커밋 보조 복제본이 로그를 확정할 때까지 기다리지 않고 트랜잭션을 커밋합니다.</span><span class="sxs-lookup"><span data-stu-id="3d6ce-194">Under asynchronous-commit mode, the primary replica commits transactions without waiting for acknowledgement that an asynchronous-commit secondary replica has hardened the log.</span></span> <span data-ttu-id="3d6ce-195">비동기-커밋 모드에서는 보조 데이터베이스의 트랜잭션 대기 시간이 최소화되지만 보조 데이터베이스가 주 데이터베이스보다 뒤쳐질 수 있어 일부 데이터가 손실될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3d6ce-195">Asynchronous-commit mode minimizes transaction latency on the secondary databases but allows them to lag behind the primary databases, making some data loss possible.</span></span>|  
  
 <span data-ttu-id="3d6ce-196">자세한 내용은 [가용성 모드 (AlwaysOn 가용성 그룹)](availability-modes-always-on-availability-groups.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="3d6ce-196">For more information, see [Availability Modes (AlwaysOn Availability Groups)](availability-modes-always-on-availability-groups.md).</span></span>  
  
 <span data-ttu-id="3d6ce-197">**장애 조치(Failover) 모드**</span><span class="sxs-lookup"><span data-stu-id="3d6ce-197">**Failover Mode**</span></span>  
 <span data-ttu-id="3d6ce-198">서버 인스턴스의 장애 조치(failover) 모드를 표시하며 다음 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="3d6ce-198">Displays the failover mode of the server instance, one of:</span></span>  
  
|<span data-ttu-id="3d6ce-199">값</span><span class="sxs-lookup"><span data-stu-id="3d6ce-199">Value</span></span>|<span data-ttu-id="3d6ce-200">Description</span><span class="sxs-lookup"><span data-stu-id="3d6ce-200">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="3d6ce-201">**자동**</span><span class="sxs-lookup"><span data-stu-id="3d6ce-201">**Automatic**</span></span>|<span data-ttu-id="3d6ce-202">자동 장애 조치(Failover)를 사용하도록 구성된 보조 복제본은 주 복제본과 동기활 때마다 계획된 수동 장애 조치도 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="3d6ce-202">A secondary replica that is configured for automatic failover also supports planned manual failover whenever the secondary replica is synchronized with the primary replica.</span></span>|  
|<span data-ttu-id="3d6ce-203">**수동**</span><span class="sxs-lookup"><span data-stu-id="3d6ce-203">**Manual**</span></span>|<span data-ttu-id="3d6ce-204">수동 장애 조치에는 계획된 장애 조치(데이터가 손실되지 않음)와 강제 장애 조치(데이터가 손실될 수 있음)의 두 가지 유형이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3d6ce-204">Two types of manual failover exist: planned (without data loss) and forced (with possible data loss).</span></span> <span data-ttu-id="3d6ce-205">가용성 모드 및 동기-커밋 모드의 경우 보조 복제본의 동기화 상태에 따라 지정된 보조 복제본에 대해 이 두 가지 중 하나만 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="3d6ce-205">For a given secondary replica, only one of these is supported, depending on the availability mode and, for synchronous-commit mode, the synchronization state of the secondary replica.</span></span> <span data-ttu-id="3d6ce-206">지정된 보조 복제본에 현재 지원되는 수동 장애 조치 형태를 확인하려면 이 표에서 **장애 조치(Failover) 준비** 열을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3d6ce-206">To determine which form of manual failover is currently supported by a given secondary replica, see the **Failover Readiness** column of this grid.</span></span>|  
  
 <span data-ttu-id="3d6ce-207">자세한 내용은 [장애 조치(Failover) 및 장애 조치(Failover) 모드&#40;AlwaysOn 가용성 그룹&#41;](failover-and-failover-modes-always-on-availability-groups.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3d6ce-207">For more information, see [Failover and Failover Modes &#40;AlwaysOn Availability Groups&#41;](failover-and-failover-modes-always-on-availability-groups.md).</span></span>  
  
 <span data-ttu-id="3d6ce-208">**장애 조치(Failover) 준비**</span><span class="sxs-lookup"><span data-stu-id="3d6ce-208">**Failover Readiness**</span></span>  
 <span data-ttu-id="3d6ce-209">보조 복제본의 장애 조치 준비를 표시하며 다음 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="3d6ce-209">Displays failover readiness of the secondary replica, one of:</span></span>  
  
|<span data-ttu-id="3d6ce-210">값</span><span class="sxs-lookup"><span data-stu-id="3d6ce-210">Value</span></span>|<span data-ttu-id="3d6ce-211">Description</span><span class="sxs-lookup"><span data-stu-id="3d6ce-211">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="3d6ce-212">**데이터 손실 없음**</span><span class="sxs-lookup"><span data-stu-id="3d6ce-212">**No data loss**</span></span>|<span data-ttu-id="3d6ce-213">이 보조 복제본이 현재 계획된 장애 조치를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="3d6ce-213">This secondary replica currently supports planned failover.</span></span> <span data-ttu-id="3d6ce-214">이 값은 동기-커밋 모드 보조 복제본이 현재 주 복제본과 동기화된 경우에만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="3d6ce-214">This value occurs only when a synchronous-commit mode secondary replica is currently synchronized with the primary replica.</span></span>|  
|<span data-ttu-id="3d6ce-215">**데이터 손실, 경고(** *#* **)**</span><span class="sxs-lookup"><span data-stu-id="3d6ce-215">**Data loss, Warnings(** *#* **)**</span></span>|<span data-ttu-id="3d6ce-216">이 보조 복제본이 현재 강제 장애 조치(데이터가 손실될 수 있음)를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="3d6ce-216">This secondary replica currently supports forced failover (with possible data loss).</span></span> <span data-ttu-id="3d6ce-217">이 값은 보조 복제본이 주 복제본과 동기화되지 않은 상태일 때마다 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="3d6ce-217">This value occurs whenever the secondary replica is not synchronized with the primary replica.</span></span> <span data-ttu-id="3d6ce-218">가능한 데이터 손실에 대한 자세한 내용을 보려면 데이터 손실 경고 링크를 클릭하세요.</span><span class="sxs-lookup"><span data-stu-id="3d6ce-218">Click the data-loss warnings link for information about the possible data loss.</span></span>|  
  
 <span data-ttu-id="3d6ce-219">**새로 고침**</span><span class="sxs-lookup"><span data-stu-id="3d6ce-219">**Refresh**</span></span>  
 <span data-ttu-id="3d6ce-220">표를 업데이트하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3d6ce-220">Click to update the grid.</span></span>  
  
 <span data-ttu-id="3d6ce-221">**취소**</span><span class="sxs-lookup"><span data-stu-id="3d6ce-221">**Cancel**</span></span>  
 <span data-ttu-id="3d6ce-222">마법사를 취소하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3d6ce-222">Click to cancel the wizard.</span></span> <span data-ttu-id="3d6ce-223">**새로운 주 복제본 선택** 페이지에서 마법사를 취소하면 동작이 수행되지 않고 마법사가 종료됩니다.</span><span class="sxs-lookup"><span data-stu-id="3d6ce-223">On the **Select New Primary Replica** page, cancelling the wizard cause it to exit without performing any actions.</span></span>  
  
###  <a name="confirm-potential-data-loss-page"></a><a name="ConfirmPotentialDataLoss"></a> <span data-ttu-id="3d6ce-224">Confirm Potential Data Loss Page</span><span class="sxs-lookup"><span data-stu-id="3d6ce-224">Confirm Potential Data Loss Page</span></span>  
 <span data-ttu-id="3d6ce-225">이 섹션에서는 강제 장애 조치를 수행하는 경우에만 표시되는 **잠재적인 데이터 손실 확인** 페이지의 옵션에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="3d6ce-225">This section describes the options of the **Confirm Potential Data Loss** page, which is displayed only if you are performing a forced failover.</span></span> <span data-ttu-id="3d6ce-226">이 항목은 [!INCLUDE[ssAoFoAgWiz](../../../includes/ssaofoagwiz-md.md)]에만 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="3d6ce-226">This topic is used only by the [!INCLUDE[ssAoFoAgWiz](../../../includes/ssaofoagwiz-md.md)].</span></span> <span data-ttu-id="3d6ce-227">이 페이지에서 데이터 손실의 위험을 감수하고 가용성 그룹을 강제 장애 조치할지 여부를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3d6ce-227">Use this page to indicate whether you are willing to risk possible data loss in order to force the availability group to fail over.</span></span>  
  
#### <a name="confirm-potential-data-loss-options"></a><span data-ttu-id="3d6ce-228">잠재적인 데이터 손실 확인 옵션</span><span class="sxs-lookup"><span data-stu-id="3d6ce-228">Confirm Potential Data Loss Options</span></span>  
 <span data-ttu-id="3d6ce-229">선택한 보조 복제본이 주 복제본과 동기화되어 있지 않은 경우 마법사는 이 보조 복제본으로 장애 조치할 경우 하나 이상의 데이터베이스에서 데이터가 손실될 수 있다는 경고를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="3d6ce-229">If the selected secondary replica is not synchronized with the primary replica, the wizard displays a warning that failing over to this secondary replica could cause data loss on one or more databases.</span></span>  
  
 <span data-ttu-id="3d6ce-230">**데이터가 손실될 가능성이 있는 장애 조치(Failover)를 확인하려면 여기를 클릭하세요.**</span><span class="sxs-lookup"><span data-stu-id="3d6ce-230">**Click here to confirm failover with potential data loss.**</span></span>  
 <span data-ttu-id="3d6ce-231">데이터 손실의 위험을 감수하고 이 가용성 그룹의 데이터베이스를 사용하려면 이 확인란을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3d6ce-231">If you are willing to risk data loss in order to make the databases in this availability group available to users, click this checkbox.</span></span> <span data-ttu-id="3d6ce-232">데이터가 손실되지 않도록 하려면 **이전** 을 클릭하여 **새로운 주 복제본 선택** 페이지로 돌아가거나 **취소** 를 클릭하여 가용성 그룹을 장애 조치하지 않고 마법사를 종료합니다.</span><span class="sxs-lookup"><span data-stu-id="3d6ce-232">If you are not willing to risk data loss, you can either click **Previous** to return to the **Select New Primary Replica** page, or click **Cancel** to exit the wizard without failing over the availability group.</span></span>  
  
 <span data-ttu-id="3d6ce-233">**취소**</span><span class="sxs-lookup"><span data-stu-id="3d6ce-233">**Cancel**</span></span>  
 <span data-ttu-id="3d6ce-234">마법사를 취소하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3d6ce-234">Click to cancel the wizard.</span></span> <span data-ttu-id="3d6ce-235">**잠재적인 데이터 손실 확인** 페이지에서 마법사를 취소하면 동작이 수행되지 않고 마법사가 종료됩니다.</span><span class="sxs-lookup"><span data-stu-id="3d6ce-235">On the **Confirm Potential Data Loss** page, cancelling the wizard cause it to exit without performing any actions.</span></span>  
  
###  <a name="connect-to-replica-page"></a><a name="ConnectToReplica"></a> <span data-ttu-id="3d6ce-236">Connect to Replica Page</span><span class="sxs-lookup"><span data-stu-id="3d6ce-236">Connect to Replica Page</span></span>  
 <span data-ttu-id="3d6ce-237">이 섹션에서는 **의** 복제본에 연결 [!INCLUDE[ssAoFoAgWiz](../../../includes/ssaofoagwiz-md.md)]페이지에 있는 옵션에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="3d6ce-237">This section describes the options of the **Connect to Replica** page of the [!INCLUDE[ssAoFoAgWiz](../../../includes/ssaofoagwiz-md.md)].</span></span> <span data-ttu-id="3d6ce-238">이 페이지는 대상 보조 복제본에 연결되어 있지 않은 경우에만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="3d6ce-238">This page is displayed only if you are not connected to the target secondary replica.</span></span> <span data-ttu-id="3d6ce-239">이 페이지에서 새로운 주 복제본으로 선택한 보조 복제본에 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3d6ce-239">Use this page to connect to the secondary replica that you have selected as the new primary replica.</span></span>  
  
#### <a name="page-options"></a><span data-ttu-id="3d6ce-240">페이지 옵션</span><span class="sxs-lookup"><span data-stu-id="3d6ce-240">Page Options</span></span>  
 <span data-ttu-id="3d6ce-241">**표 열:**</span><span class="sxs-lookup"><span data-stu-id="3d6ce-241">**Grid columns:**</span></span>  
 <span data-ttu-id="3d6ce-242">**서버 인스턴스**</span><span class="sxs-lookup"><span data-stu-id="3d6ce-242">**Server Instance**</span></span>  
 <span data-ttu-id="3d6ce-243">가용성 복제본을 호스팅할 서버 인스턴스의 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="3d6ce-243">Displays the name of the server instance that will host the availability replica.</span></span>  
  
 <span data-ttu-id="3d6ce-244">**다음 계정으로 연결**</span><span class="sxs-lookup"><span data-stu-id="3d6ce-244">**Connected As**</span></span>  
 <span data-ttu-id="3d6ce-245">연결이 설정된 후에 서버 인스턴스에 연결되는 계정을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="3d6ce-245">Displays the account that is connected to the server instance, once the connection has been established.</span></span> <span data-ttu-id="3d6ce-246">이 열이 지정된 서버 인스턴스에 대해 "**연결되지 않음**"으로 표시되면 **연결** 단추를 클릭해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3d6ce-246">If this column displays "**Not Connected**" for a given server instance, you will need to click the **Connect** button.</span></span>  
  
 <span data-ttu-id="3d6ce-247">**연결**</span><span class="sxs-lookup"><span data-stu-id="3d6ce-247">**Connect**</span></span>  
 <span data-ttu-id="3d6ce-248">이 서버 인스턴스가 연결해야 하는 다른 서버 인스턴스와 다른 계정으로 실행 중인 경우 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3d6ce-248">Click if this server instance is running under a different account than other server instances to which you need to connect.</span></span>  
  
 <span data-ttu-id="3d6ce-249">**취소**</span><span class="sxs-lookup"><span data-stu-id="3d6ce-249">**Cancel**</span></span>  
 <span data-ttu-id="3d6ce-250">마법사를 취소하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3d6ce-250">Click to cancel the wizard.</span></span> <span data-ttu-id="3d6ce-251">**복제본에 연결** 페이지에서 마법사를 취소하면 동작이 수행되지 않고 마법사가 종료됩니다.</span><span class="sxs-lookup"><span data-stu-id="3d6ce-251">On the **Connect to Replica** page, cancelling the wizard cause it to exit without performing any actions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d6ce-252">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3d6ce-252">See Also</span></span>  
 <span data-ttu-id="3d6ce-253">[AlwaysOn 가용성 그룹 &#40;SQL Server 개요&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="3d6ce-253">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="3d6ce-254">[가용성 모드 (AlwaysOn 가용성 그룹)](availability-modes-always-on-availability-groups.md) </span><span class="sxs-lookup"><span data-stu-id="3d6ce-254">[Availability Modes (AlwaysOn Availability Groups)](availability-modes-always-on-availability-groups.md) </span></span>  
 <span data-ttu-id="3d6ce-255">[장애 조치 (failover) 및 장애 조치 (failover) 모드 &#40;AlwaysOn 가용성 그룹&#41;](failover-and-failover-modes-always-on-availability-groups.md) </span><span class="sxs-lookup"><span data-stu-id="3d6ce-255">[Failover and Failover Modes &#40;AlwaysOn Availability Groups&#41;](failover-and-failover-modes-always-on-availability-groups.md) </span></span>  
 <span data-ttu-id="3d6ce-256">[가용성 그룹의 계획된 수동 장애 조치(Failover) 수행&#40;SQL Server&#41;](perform-a-planned-manual-failover-of-an-availability-group-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="3d6ce-256">[Perform a Planned Manual Failover of an Availability Group &#40;SQL Server&#41;](perform-a-planned-manual-failover-of-an-availability-group-sql-server.md) </span></span>  
 <span data-ttu-id="3d6ce-257">[가용성 그룹의 강제 수동 장애 조치(Failover) 수행&#40;SQL Server&#41;](perform-a-forced-manual-failover-of-an-availability-group-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="3d6ce-257">[Perform a Forced Manual Failover of an Availability Group &#40;SQL Server&#41;](perform-a-forced-manual-failover-of-an-availability-group-sql-server.md) </span></span>  
 [<span data-ttu-id="3d6ce-258">강제 쿼럼을 통해 WSFC 재해 복구&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="3d6ce-258">WSFC Disaster Recovery through Forced Quorum &#40;SQL Server&#41;</span></span>](../../../sql-server/failover-clusters/windows/wsfc-disaster-recovery-through-forced-quorum-sql-server.md)  
  
  
