---
title: AlwaysOn 대시보드 (SQL Server Management Studio) 사용 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.agdashboard.f1
helpviewer_keywords:
- Availability Groups [SQL Server], policies
- Availability Groups [SQL Server], dashboard
ms.assetid: c9ba2589-139e-42bc-99e1-94546717c64d
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c4ce0072bcd6642dcb4f3ac63e04c98786bd550e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648590"
---
# <a name="use-the-alwayson-dashboard-sql-server-management-studio"></a><span data-ttu-id="7b3c6-102">AlwaysOn 대시보드 사용(SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="7b3c6-102">Use the AlwaysOn Dashboard (SQL Server Management Studio)</span></span>
  <span data-ttu-id="7b3c6-103">데이터베이스 관리자는 AlwaysOn 대시보드를 사용하여 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]에서 AlwaysOn 가용성 그룹과 해당 가용성 복제본 및 데이터베이스의 상태 개요를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-103">Database administrators use the AlwaysOn Dashboard to obtains an at-a-glance view the health of an AlwaysOn availability group and its availability replicas and databases in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="7b3c6-104">AlwaysOn 대시보드의 일반적인 용도는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-104">Some of the typical uses for the AlwaysOn Dashboard are:</span></span>  
  
-   <span data-ttu-id="7b3c6-105">수동 장애 조치(failover)를 위한 복제본 선택</span><span class="sxs-lookup"><span data-stu-id="7b3c6-105">Choosing a replica for a manual failover.</span></span>  
  
-   <span data-ttu-id="7b3c6-106">장애 조치(failover)를 강제 실행하는 경우의 데이터 손실 예상</span><span class="sxs-lookup"><span data-stu-id="7b3c6-106">Estimating data loss if you force failover.</span></span>  
  
-   <span data-ttu-id="7b3c6-107">데이터 동기화 성능 평가</span><span class="sxs-lookup"><span data-stu-id="7b3c6-107">Evaluating data-synchronization performance.</span></span>  
  
-   <span data-ttu-id="7b3c6-108">동기-커밋 보조 복제본의 성능 영향 평가</span><span class="sxs-lookup"><span data-stu-id="7b3c6-108">Evaluating the performance impact of a synchronous-commit secondary replica</span></span>  
  
 <span data-ttu-id="7b3c6-109">AlwaysOn 대시보드는 다음과 같은 유형의 정보를 사용하여 고가용성 작업 결정을 쉽게 내릴 수 있도록 주요 가용성 그룹 상태 및 성과 지표를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-109">The AlwaysOn Dashboard provides key availability group states and performance indicators allowing you to easily make high availability operational decisions using the following types of information.</span></span>  
  
-   <span data-ttu-id="7b3c6-110">복제본 롤업 상태</span><span class="sxs-lookup"><span data-stu-id="7b3c6-110">Replica roll-up state</span></span>  
  
-   <span data-ttu-id="7b3c6-111">동기화 모드 및 상태</span><span class="sxs-lookup"><span data-stu-id="7b3c6-111">Synchronization mode and state</span></span>  
  
-   <span data-ttu-id="7b3c6-112">예상 데이터 손실</span><span class="sxs-lookup"><span data-stu-id="7b3c6-112">Estimate Data Loss</span></span>  
  
-   <span data-ttu-id="7b3c6-113">예상 복구 시간(catchup 다시 실행)</span><span class="sxs-lookup"><span data-stu-id="7b3c6-113">Estimated Recovery Time (redo catch up)</span></span>  
  
-   <span data-ttu-id="7b3c6-114">데이터베이스 복제본 정보</span><span class="sxs-lookup"><span data-stu-id="7b3c6-114">Database Replica details</span></span>  
  
-   <span data-ttu-id="7b3c6-115">동기화 모드 및 상태</span><span class="sxs-lookup"><span data-stu-id="7b3c6-115">Synchronization mode and state</span></span>  
  
-   <span data-ttu-id="7b3c6-116">로그 복원 시간</span><span class="sxs-lookup"><span data-stu-id="7b3c6-116">Time to restore log</span></span>  
  
 
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="7b3c6-117">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="7b3c6-117">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="7b3c6-118">필수 조건</span><span class="sxs-lookup"><span data-stu-id="7b3c6-118">Prerequisites</span></span>  
 <span data-ttu-id="7b3c6-119">가용성 그룹의 주 복제본 또는 보조 복제본을 호스팅하는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인스턴스(서버 인스턴스)에 연결해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-119">You must be connected to the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (server instance) that hosts either the primary replica or a secondary replica of an availability group.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="7b3c6-120">보안</span><span class="sxs-lookup"><span data-stu-id="7b3c6-120">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="7b3c6-121">권한</span><span class="sxs-lookup"><span data-stu-id="7b3c6-121">Permissions</span></span>  
 <span data-ttu-id="7b3c6-122">연결, 서버 상태 보기 및 모든 정의 보기 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-122">Requires CONNECT, VIEW SERVER STATE, and VIEW ANY DEFINITION permissions.</span></span>  
  
##  <a name="to-start-the-alwayson-dashboard"></a><a name="SSMSProcedure"></a><span data-ttu-id="7b3c6-123">AlwaysOn 대시보드를 시작 하려면</span><span class="sxs-lookup"><span data-stu-id="7b3c6-123">To start the AlwaysOn Dashboard</span></span>  
  
1.  <span data-ttu-id="7b3c6-124">개체 탐색기에서 AlwaysOn 대시보드를 실행할 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-124">In Object Explorer, connect to the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] on which you want to run the AlwaysOn Dashboard.</span></span>  
  
2.  <span data-ttu-id="7b3c6-125">**AlwaysOn 고가용성** 노드를 확장하고 **가용성 그룹** 노드를 마우스 오른쪽 단추로 클릭한 다음 **대시보드 표시**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-125">Expand the **AlwaysOn High Availability** node, right-click the **Availability Groups** node, and then click **Show Dashboard**.</span></span>  
  
###  <a name="to-change-alwayson-dashboard-options"></a><a name="DashboardOptions"></a><span data-ttu-id="7b3c6-126">AlwaysOn 대시보드 옵션을 변경 하려면</span><span class="sxs-lookup"><span data-stu-id="7b3c6-126">To Change AlwaysOn Dashboard Options</span></span>  
 <span data-ttu-id="7b3c6-127">[!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]**옵션** 대화 상자를 사용하여 자동 정의된 AlwaysOn 정책 자동 새로 고침 및 사용을 위한 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] AlwaysOn 대시보드 동작을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-127">You can use the [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]**Options** dialog box to configure the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] AlwaysOn Dashboard behavior for automatic refreshing and enabling an auto-defined AlwaysOn policy.</span></span>  
  
1.  <span data-ttu-id="7b3c6-128">**도구** 메뉴에서 **옵션**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-128">From the **Tools** menu, click **Options**.</span></span>  
  
2.  <span data-ttu-id="7b3c6-129">대시보드를 자동으로 새로 고치려면 **옵션** 대화 상자에서 **자동 새로 고침 설정**을 선택하고 새로 고침 간격(초)을 입력한 다음 연결을 다시 시도할 횟수를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-129">To automatically refresh the dashboard, in the **Options** dialog box, select **Turn on automatic refresh**, enter the refresh interval in seconds, and then enter the number of times you want to retry the connection.</span></span>  
  
3.  <span data-ttu-id="7b3c6-130">사용자 정의 정책을 사용하도록 설정하려면 **사용자 정의 AlwaysOn 정책 사용**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-130">To enable a user-defined policy, select **Enable user-defined AlwaysOn policy**.</span></span>  
  
##  <a name="availability-group-summary"></a><a name="AvGroupsView"></a> <span data-ttu-id="7b3c6-131">가용성 그룹 요약</span><span class="sxs-lookup"><span data-stu-id="7b3c6-131">Availability Group Summary</span></span>  
 <span data-ttu-id="7b3c6-132">가용성 그룹 화면에 연결된 서버 인스턴스가 복제본을 호스팅하는 각 가용성 그룹에 대한 요약 행을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-132">The availability group screen displays a summary line for each availability group for which the connected server instance hosts a replica.</span></span> <span data-ttu-id="7b3c6-133">이 창에는 다음과 같은 열이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-133">This pane displays the following columns.</span></span>  
  
 <span data-ttu-id="7b3c6-134">**가용성 그룹 이름**</span><span class="sxs-lookup"><span data-stu-id="7b3c6-134">**Availability Group Name**</span></span>  
 <span data-ttu-id="7b3c6-135">연결된 서버 인스턴스에서 복제본을 호스팅하는 가용성 그룹의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-135">The name of an availability group for which the connected server instance hosts a replica.</span></span>  
  
 <span data-ttu-id="7b3c6-136">**주 인스턴스**</span><span class="sxs-lookup"><span data-stu-id="7b3c6-136">**Primary Instance**</span></span>  
 <span data-ttu-id="7b3c6-137">가용성 그룹의 주 복제본을 호스팅하는 서버 인스턴스의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-137">Name of the server instance that is hosting the primary replica of the availability group.</span></span>  
  
 <span data-ttu-id="7b3c6-138">**장애 조치(Failover) 모드**</span><span class="sxs-lookup"><span data-stu-id="7b3c6-138">**Failover Mode**</span></span>  
 <span data-ttu-id="7b3c6-139">복제본이 구성되는 장애 조치(failover) 모드를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-139">Displays the failover mode for which the replica is configured.</span></span> <span data-ttu-id="7b3c6-140">가능한 장애 조치(failover) 모드 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-140">The possible failover mode values are:</span></span>  
  
-   <span data-ttu-id="7b3c6-141">**자동**.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-141">**Automatic**.</span></span> <span data-ttu-id="7b3c6-142">하나 이상의 복제본이 자동 장애 조치 모드임을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-142">Indicates that one or more replicas is in automatic-failover mode.</span></span>  
  
-   <span data-ttu-id="7b3c6-143">**수동**.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-143">**Manual**.</span></span> <span data-ttu-id="7b3c6-144">자동 장애 조치 모드인 복제본이 없음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-144">Indicates that no replica is automatic-failover mode.</span></span>  
  
 <span data-ttu-id="7b3c6-145">**문제**</span><span class="sxs-lookup"><span data-stu-id="7b3c6-145">**Issues**</span></span>  
 <span data-ttu-id="7b3c6-146">지정된 문제에 대한 문제 해결 설명서를 열려면 **문제** 링크를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-146">Click the **Issues** link to open troubleshooting documentation for a given issue.</span></span> <span data-ttu-id="7b3c6-147">모든 AlwaysOn 정책 문제 목록은 [AlwaysOn 가용성 그룹의 작동 문제에 대 한 Alwayson 정책 (SQL Server)](always-on-policies-for-operational-issues-always-on-availability.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-147">For a list of all the AlwaysOn policy issues, see [AlwaysOn Policies for Operational Issues with AlwaysOn Availability Groups (SQL Server)](always-on-policies-for-operational-issues-always-on-availability.md).</span></span>  
  
> [!TIP]  
>  <span data-ttu-id="7b3c6-148">열 머리글을 클릭하여 가용성 그룹, 주 인스턴스, 장애 조치(failover) 모드 또는 문제의 이름을 기준으로 가용성 그룹 정보를 정렬할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-148">Click the column headings to sort the availability group information by the name of the availability group, primary instance, failover mode, or Issue.</span></span>  
  
##  <a name="availability-group-details"></a><a name="AvGroupDetails"></a> <span data-ttu-id="7b3c6-149">가용성 그룹 정보</span><span class="sxs-lookup"><span data-stu-id="7b3c6-149">Availability Group Details</span></span>  
 <span data-ttu-id="7b3c6-150">요약 화면에서 선택하는 가용성 그룹에 대한 다음 정보가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-150">The following detail information is displayed for the availability group that you select from the summary screen:</span></span>  
  
 <span data-ttu-id="7b3c6-151">**가용성 그룹 상태**</span><span class="sxs-lookup"><span data-stu-id="7b3c6-151">**Availability group state**</span></span>  
 <span data-ttu-id="7b3c6-152">가용성 그룹의 상태를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-152">Displays the state of health for the availability group.</span></span>  
  
 <span data-ttu-id="7b3c6-153">**Primary instance**</span><span class="sxs-lookup"><span data-stu-id="7b3c6-153">**Primary instance**</span></span>  
 <span data-ttu-id="7b3c6-154">가용성 그룹의 주 복제본을 호스팅하는 서버 인스턴스의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-154">Name of the server instance that is hosting the primary replica of the availability group.</span></span>  
  
 <span data-ttu-id="7b3c6-155">**Failover mode**</span><span class="sxs-lookup"><span data-stu-id="7b3c6-155">**Failover mode**</span></span>  
 <span data-ttu-id="7b3c6-156">복제본이 구성되는 장애 조치(failover) 모드를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-156">Displays the failover mode for which the replica is configured.</span></span> <span data-ttu-id="7b3c6-157">가능한 장애 조치(failover) 모드 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-157">The possible failover mode values are:</span></span>  
  
-   <span data-ttu-id="7b3c6-158">**자동**.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-158">**Automatic**.</span></span> <span data-ttu-id="7b3c6-159">하나 이상의 복제본이 자동 장애 조치 모드임을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-159">Indicates that one or more replicas is in automatic-failover mode.</span></span>  
  
-   <span data-ttu-id="7b3c6-160">**수동**.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-160">**Manual**.</span></span> <span data-ttu-id="7b3c6-161">자동 장애 조치 모드인 복제본이 없음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-161">Indicates that no replica is automatic-failover mode.</span></span>  
  
 <span data-ttu-id="7b3c6-162">**클러스터 상태**</span><span class="sxs-lookup"><span data-stu-id="7b3c6-162">**Cluster state**</span></span>  
 <span data-ttu-id="7b3c6-163">연결된 서버의 인스턴스와 가용성 그룹이 구성원 노드인 클러스터의 이름과 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-163">Name and state of the cluster where the instance of the connected server and the availability group is a member node.</span></span>  
  
##  <a name="availability-replica-details"></a><a name="AvReplicaDetails"></a> <span data-ttu-id="7b3c6-164">가용성 복제본 정보</span><span class="sxs-lookup"><span data-stu-id="7b3c6-164">Availability Replica Details</span></span>  
 <span data-ttu-id="7b3c6-165">**가용성 복제본** 창에 다음 열이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-165">The **Availability replica** pane displays the following columns:</span></span>  
  
 <span data-ttu-id="7b3c6-166">**이름**</span><span class="sxs-lookup"><span data-stu-id="7b3c6-166">**Name**</span></span>  
 <span data-ttu-id="7b3c6-167">가용성 복제본을 호스팅하는 서버 인스턴스의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-167">The name of the server instance that hosts the availability replica.</span></span> <span data-ttu-id="7b3c6-168">이 열은 기본적으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-168">This column is shown by default.</span></span>  
  
 <span data-ttu-id="7b3c6-169">**역할**</span><span class="sxs-lookup"><span data-stu-id="7b3c6-169">**Role**</span></span>  
 <span data-ttu-id="7b3c6-170">가용성 복제본의 현재 역할( **주** 또는 **보조**)을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-170">Indicates the current role of the availability replica, either **Primary** or **Secondary**.</span></span> <span data-ttu-id="7b3c6-171">[!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 역할에 대한 자세한 내용은 [AlwaysOn 가용성 그룹 개요&#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-171">For information about [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] roles, see [Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md).</span></span> <span data-ttu-id="7b3c6-172">이 열은 기본적으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-172">This column is shown by default.</span></span>  
  
 <span data-ttu-id="7b3c6-173">**장애 조치(Failover) 모드**</span><span class="sxs-lookup"><span data-stu-id="7b3c6-173">**Failover Mode**</span></span>  
 <span data-ttu-id="7b3c6-174">복제본이 구성되는 장애 조치(failover) 모드를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-174">Displays the failover mode for which the replica is configured.</span></span> <span data-ttu-id="7b3c6-175">가능한 장애 조치(failover) 모드 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-175">The possible failover mode values are:</span></span>  
  
-   <span data-ttu-id="7b3c6-176">**자동**.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-176">**Automatic**.</span></span> <span data-ttu-id="7b3c6-177">하나 이상의 복제본이 자동 장애 조치 모드임을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-177">Indicates that one or more replicas is in automatic-failover mode.</span></span>  
  
-   <span data-ttu-id="7b3c6-178">**수동**.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-178">**Manual**.</span></span> <span data-ttu-id="7b3c6-179">자동 장애 조치 모드인 복제본이 없음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-179">Indicates that no replica is automatic-failover mode.</span></span>  
  
 <span data-ttu-id="7b3c6-180">**동기화 상태**</span><span class="sxs-lookup"><span data-stu-id="7b3c6-180">**Synchronization State**</span></span>  
 <span data-ttu-id="7b3c6-181">보조 복제본이 주 복제본에 현재 동기화되어 있는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-181">Indicates whether a secondary replica is currently synchronized with primary replica.</span></span> <span data-ttu-id="7b3c6-182">이 열은 기본적으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-182">This column is shown by default.</span></span> <span data-ttu-id="7b3c6-183">가능한 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-183">The possible values are:</span></span>  
  
-   <span data-ttu-id="7b3c6-184">**동기화 되지 않았습니다**.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-184">**Not Synchronized**.</span></span> <span data-ttu-id="7b3c6-185">복제본에 있는 하나 이상의 데이터베이스가 동기화되지 않았거나 가용성 그룹에 아직 조인되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-185">One or more databases in the replica are not synchronized or have not yet been joined to the availability group.</span></span>  
  
-   <span data-ttu-id="7b3c6-186">**동기화**중.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-186">**Synchronizing**.</span></span> <span data-ttu-id="7b3c6-187">복제본에 있는 하나 이상의 데이터베이스가 동기화되고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-187">One or more databases in the replica are being synchronized.</span></span>  
  
-   <span data-ttu-id="7b3c6-188">**동기화**됨.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-188">**Synchronized**.</span></span> <span data-ttu-id="7b3c6-189">보조 복제본에 있는 모든 데이터베이스가 현재 주 복제본 또는 마지막 주 복제본(있는 경우)의 해당 주 데이터베이스와 동기화되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-189">All databases in the secondary replica are synchronized with the corresponding primary databases on the current primary replica, if any, or on the last primary replica.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="7b3c6-190">성능 모드에서는 데이터베이스가 절대 Synchronized 상태로 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-190">In performance mode, the database is never in the synchronized state.</span></span>  
  
-   <span data-ttu-id="7b3c6-191">**NULL**입니다.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-191">**NULL**.</span></span> <span data-ttu-id="7b3c6-192">알 수 없는 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-192">Unknown state.</span></span> <span data-ttu-id="7b3c6-193">이 값은 로컬 서버 인스턴스가 WSFC 장애 조치(Failover) 클러스터와 통신할 수 없는 경우(즉, 로컬 노드가 WSFC 쿼럼의 일부가 아닌 경우)에 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-193">This value occurs when the local server instance cannot communicate with the WSFC failover cluster (that is the local node is not part of WSFC quorum).</span></span>  
  
 <span data-ttu-id="7b3c6-194">**문제**</span><span class="sxs-lookup"><span data-stu-id="7b3c6-194">**Issues**</span></span>  
 <span data-ttu-id="7b3c6-195">문제 이름을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-195">Lists the issue name.</span></span> <span data-ttu-id="7b3c6-196">이 값은 기본적으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-196">This value is shown by default.</span></span> <span data-ttu-id="7b3c6-197">모든 AlwaysOn 정책 문제 목록은 [AlwaysOn 가용성 그룹의 작동 문제에 대 한 Alwayson 정책 (SQL Server)](always-on-policies-for-operational-issues-always-on-availability.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-197">For a list of all the AlwaysOn policy issues, see [AlwaysOn Policies for Operational Issues with AlwaysOn Availability Groups (SQL Server)](always-on-policies-for-operational-issues-always-on-availability.md).</span></span>  
  
 <span data-ttu-id="7b3c6-198">**가용성 모드**</span><span class="sxs-lookup"><span data-stu-id="7b3c6-198">**Availability Mode**</span></span>  
 <span data-ttu-id="7b3c6-199">각 가용성 복제본에 대해 별도로 설정한 복제본 속성을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-199">Indicates the replica property that you set separately for each availability replica.</span></span> <span data-ttu-id="7b3c6-200">이 값은 기본적으로 숨겨집니다.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-200">This value is hidden by default.</span></span> <span data-ttu-id="7b3c6-201">가능한 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-201">The possible values are:</span></span>  
  
-   <span data-ttu-id="7b3c6-202">**비동기**.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-202">**Asynchronous**.</span></span> <span data-ttu-id="7b3c6-203">보조 복제본이 주 복제본과 동기화되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-203">The secondary replica never becomes synchronized with the primary replica.</span></span>  
  
-   <span data-ttu-id="7b3c6-204">**동기**.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-204">**Synchronous**.</span></span> <span data-ttu-id="7b3c6-205">주 데이터베이스에 catchup할 때 보조 데이터베이스가 이 상태로 전환되고 데이터베이스에 대해 데이터 동기화가 지속되는 동안 catchup 상태를 유지합니다.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-205">When catching up to the primary database, a secondary database enters this state, and it remains caught up as long as data synchronization continues for the database.</span></span>  
  
 <span data-ttu-id="7b3c6-206">**주 연결 모드**</span><span class="sxs-lookup"><span data-stu-id="7b3c6-206">**Primary Connection Mode**</span></span>  
 <span data-ttu-id="7b3c6-207">주 복제본에 연결하는 데 사용되는 모드를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-207">Indicates the mode that is used to connect to the primary replica.</span></span>  <span data-ttu-id="7b3c6-208">이 값은 기본적으로 숨겨집니다.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-208">This value is hidden by default.</span></span>  
  
 <span data-ttu-id="7b3c6-209">**보조 연결 모드**</span><span class="sxs-lookup"><span data-stu-id="7b3c6-209">**Secondary Connection Mode**</span></span>  
 <span data-ttu-id="7b3c6-210">보조 복제본에 연결하는 데 사용되는 모드를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-210">Indicates the mode that is used to connect to the secondary replica.</span></span>  <span data-ttu-id="7b3c6-211">이 값은 기본적으로 숨겨집니다.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-211">This value is hidden by default.</span></span>  
  
 <span data-ttu-id="7b3c6-212">**연결 상태**</span><span class="sxs-lookup"><span data-stu-id="7b3c6-212">**Connection State**</span></span>  
 <span data-ttu-id="7b3c6-213">보조 복제본이 주 복제본에 현재 연결되어 있는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-213">Indicates whether a secondary replica is currently connected to the primary replica.</span></span> <span data-ttu-id="7b3c6-214">이 열은 기본적으로 숨겨집니다.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-214">This column is hidden by default.</span></span> <span data-ttu-id="7b3c6-215">가능한 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-215">The possible values are:</span></span>  
  
-   <span data-ttu-id="7b3c6-216">**연결 끊김**.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-216">**Disconnected**.</span></span> <span data-ttu-id="7b3c6-217">원격 가용성 복제본의 경우 로컬 가용성 복제본에서 연결이 끊어져 있는지를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-217">For a remote availability replica, indicates that it is disconnected from the local availability replica.</span></span> <span data-ttu-id="7b3c6-218">연결이 끊긴 상태에 대한 로컬 복제본의 응답은 역할별로 다음과 같이 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-218">The response of the local replica to the Disconnected state depends on its role, as follows:</span></span>  
  
    -   <span data-ttu-id="7b3c6-219">주 복제본에서 보조 복제본의 연결이 끊어지면 보조 데이터베이스는 주 복제본에 **동기화되지 않음** 으로 표시되고 주 복제본은 보조 복제본이 다시 연결될 때까지 기다립니다.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-219">On the primary replica, if a secondary replica is disconnected, the secondary databases are marked as **Not Synchronized** on the primary replica, and the primary replica waits for the secondary to reconnect.</span></span>  
  
    -   <span data-ttu-id="7b3c6-220">보조 복제본에서 보조 복제본의 연결이 끊어지면 보조 복제본은 주 복제본에 다시 연결하려고 시도합니다.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-220">On the secondary replica, upon detecting that it is disconnected, the secondary replica attempts to reconnect to the primary replica.</span></span>  
  
-   <span data-ttu-id="7b3c6-221">**연결**되었습니다.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-221">**Connected**.</span></span> <span data-ttu-id="7b3c6-222">로컬 복제본에 현재 연결되어 있는 원격 가용성 복제본입니다.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-222">A remote availability replica that is currently connected to the local replica.</span></span>  
  
 <span data-ttu-id="7b3c6-223">**작동 상태**</span><span class="sxs-lookup"><span data-stu-id="7b3c6-223">**Operational State**</span></span>  
 <span data-ttu-id="7b3c6-224">보조 복제본의 현재 작동 상태를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-224">Indicates the current operational state of the secondary replica.</span></span> <span data-ttu-id="7b3c6-225">이 값은 기본적으로 숨겨집니다.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-225">This value is hidden by default.</span></span> <span data-ttu-id="7b3c6-226">가능한 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-226">The possible values are:</span></span>  
  
 <span data-ttu-id="7b3c6-227">**0**. 장애 조치(failover) 보류 중</span><span class="sxs-lookup"><span data-stu-id="7b3c6-227">**0**. Pending failover</span></span>  
  
 <span data-ttu-id="7b3c6-228">**1**. 보류 중</span><span class="sxs-lookup"><span data-stu-id="7b3c6-228">**1**. Pending</span></span>  
  
 <span data-ttu-id="7b3c6-229">**2**. 온라인</span><span class="sxs-lookup"><span data-stu-id="7b3c6-229">**2**. Online</span></span>  
  
 <span data-ttu-id="7b3c6-230">**3**. 오프라인</span><span class="sxs-lookup"><span data-stu-id="7b3c6-230">**3**. Offline</span></span>  
  
 <span data-ttu-id="7b3c6-231">**4**. 실패</span><span class="sxs-lookup"><span data-stu-id="7b3c6-231">**4**. Failed</span></span>  
  
 <span data-ttu-id="7b3c6-232">**5**. 실패, 쿼럼 없음</span><span class="sxs-lookup"><span data-stu-id="7b3c6-232">**5**. Failed, no quorum</span></span>  
  
 <span data-ttu-id="7b3c6-233">**NULL**입니다.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-233">**NULL**.</span></span> <span data-ttu-id="7b3c6-234">복제본이 로컬이 아님</span><span class="sxs-lookup"><span data-stu-id="7b3c6-234">Replica is not local</span></span>  
  
 <span data-ttu-id="7b3c6-235">**마지막 연결 오류 번호**</span><span class="sxs-lookup"><span data-stu-id="7b3c6-235">**Last Connection Error No.**</span></span>  
 <span data-ttu-id="7b3c6-236">마지막 연결 오류의 번호입니다.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-236">Number of the last connection error.</span></span>  <span data-ttu-id="7b3c6-237">이 값은 기본적으로 숨겨집니다.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-237">This value is hidden by default.</span></span>  
  
 <span data-ttu-id="7b3c6-238">**마지막 연결 오류 설명**</span><span class="sxs-lookup"><span data-stu-id="7b3c6-238">**Last Connection Error Description**</span></span>  
 <span data-ttu-id="7b3c6-239">마지막 연결 오류에 대한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-239">Description of the last connection error.</span></span>  <span data-ttu-id="7b3c6-240">이 값은 기본적으로 숨겨집니다.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-240">This value is hidden by default.</span></span>  
  
 <span data-ttu-id="7b3c6-241">**마지막 연결 오류 타임스탬프**</span><span class="sxs-lookup"><span data-stu-id="7b3c6-241">**Last Connection Error Timestamp**</span></span>  
 <span data-ttu-id="7b3c6-242">마지막 연결 오류의 타임스탬프입니다.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-242">Timestamp of the last connection error.</span></span> <span data-ttu-id="7b3c6-243">이 값은 기본적으로 숨겨집니다.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-243">This value is hidden by default.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7b3c6-244">가용성 복제본의 성능 카운터에 대한 자세한 내용은 [SQL Server, 가용성 복제본](../../../relational-databases/performance-monitor/sql-server-availability-replica.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-244">For information about performance counters for availability replicas, see [SQL Server, Availability Replica](../../../relational-databases/performance-monitor/sql-server-availability-replica.md).</span></span>  
  
##  <a name="to-group-availability-group-information"></a><a name="AvDbDetails"></a> <span data-ttu-id="7b3c6-245">가용성 그룹 정보를 그룹화하려면</span><span class="sxs-lookup"><span data-stu-id="7b3c6-245">To Group Availability Group Information</span></span>  
 <span data-ttu-id="7b3c6-246">정보를 그룹화하려면 **그룹화 방법**을 클릭하고 다음 중 하나를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-246">To group the information, click **Group by**, and select one of the following:</span></span>  
  
-   <span data-ttu-id="7b3c6-247">**가용성 복제본**</span><span class="sxs-lookup"><span data-stu-id="7b3c6-247">**Availability replicas**</span></span>  
  
-   <span data-ttu-id="7b3c6-248">**가용성 데이터베이스**</span><span class="sxs-lookup"><span data-stu-id="7b3c6-248">**Availability databases**</span></span>  
  
-   <span data-ttu-id="7b3c6-249">**동기화 상태**</span><span class="sxs-lookup"><span data-stu-id="7b3c6-249">**Synchronization state**</span></span>  
  
-   <span data-ttu-id="7b3c6-250">**장애 조치 준비**</span><span class="sxs-lookup"><span data-stu-id="7b3c6-250">**Failover readiness**</span></span>  
  
-   <span data-ttu-id="7b3c6-251">**문제**</span><span class="sxs-lookup"><span data-stu-id="7b3c6-251">**Issues**</span></span>  
  
 <span data-ttu-id="7b3c6-252">그룹화된 정보를 표시하는 창에 다음 열이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-252">The pane that displays the grouped information displays the following columns:</span></span>  
  
 <span data-ttu-id="7b3c6-253">**이름**</span><span class="sxs-lookup"><span data-stu-id="7b3c6-253">**Name**</span></span>  
 <span data-ttu-id="7b3c6-254">가용성 데이터베이스의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-254">The name of the availability database.</span></span> <span data-ttu-id="7b3c6-255">이 값은 기본적으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-255">This value is shown by default.</span></span>  
  
 <span data-ttu-id="7b3c6-256">**복제본**</span><span class="sxs-lookup"><span data-stu-id="7b3c6-256">**Replica**</span></span>  
 <span data-ttu-id="7b3c6-257">가용성 복제본을 호스팅하는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 의 인스턴스 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-257">The name of the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] that hosts the availability replica.</span></span> <span data-ttu-id="7b3c6-258">이 값은 기본적으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-258">This value is shown by default.</span></span>  
  
 <span data-ttu-id="7b3c6-259">**동기화 상태**</span><span class="sxs-lookup"><span data-stu-id="7b3c6-259">**Synchronization State**</span></span>  
 <span data-ttu-id="7b3c6-260">가용성 데이터베이스가 주 복제본에 현재 동기화되어 있는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-260">Indicates whether the availability database is currently synchronized with primary replica.</span></span> <span data-ttu-id="7b3c6-261">이 값은 기본적으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-261">This value is shown by default.</span></span> <span data-ttu-id="7b3c6-262">가능한 동기화 상태는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-262">The possible synchronization states are:</span></span>  
  
-   <span data-ttu-id="7b3c6-263">**비동기화 중**.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-263">**Not synchronizing**.</span></span>  
  
    -   <span data-ttu-id="7b3c6-264">주 역할의 경우 데이터베이스에서 트랜잭션 로그를 해당 보조 데이터베이스와 동기화할 준비가 되지 않았음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-264">For the primary role, indicates that the database is not ready to synchronize its transaction log with the corresponding secondary databases.</span></span>  
  
    -   <span data-ttu-id="7b3c6-265">보조 데이터베이스의 경우 데이터베이스에서 연결 문제로 인해 로그 동기화를 시작하지 않았거나 데이터베이스가 일시 중지되었거나, 시작 중에 전환 상태를 진행하고 있거나 역할 전환 중임을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-265">For a secondary database, indicates that the database has not started log synchronization because of a connection issue, is being suspended, or is going through transition states during startup or a role switch.</span></span>  
  
-   <span data-ttu-id="7b3c6-266">**동기화**중.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-266">**Synchronizing**.</span></span>  
  
     <span data-ttu-id="7b3c6-267">주 복제본에서:</span><span class="sxs-lookup"><span data-stu-id="7b3c6-267">On a primary replica:</span></span>  
  
    -   <span data-ttu-id="7b3c6-268">주 데이터베이스의 경우 이 데이터베이스가 보조 데이터베이스의 검색 요청을 받을 준비가 되었음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-268">For a primary database, indicates that this database is ready to accept a scan request from a secondary database.</span></span>  
  
    -   <span data-ttu-id="7b3c6-269">보조 복제본에서 해당 보조 데이터베이스에 대해 진행 중인 활성 데이터 이동이 있음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-269">On a secondary replica, indicates that there is active data movement going on for that secondary database.</span></span>  
  
     <span data-ttu-id="7b3c6-270">보조 복제본에서 해당 복제본에 대해 진행 중인 활성 데이터 이동이 있음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-270">On a secondary replica, indicates that there is active data movement going on for that replica.</span></span>  
  
-   <span data-ttu-id="7b3c6-271">**동기화**됨.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-271">**Synchronized**.</span></span>  
  
     <span data-ttu-id="7b3c6-272">주 데이터베이스의 경우 하나 이상의 보조 데이터베이스가 동기화되었음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-272">For a primary database, indicates that at least one secondary database is synchronized.</span></span>  
  
     <span data-ttu-id="7b3c6-273">보조 데이터베이스의 경우 데이터베이스가 해당 주 데이터베이스와 동기화되었음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-273">For a secondary database, indicates that the database is synchronized with the corresponding primary database.</span></span>  
  
-   <span data-ttu-id="7b3c6-274">**되돌리는 중**.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-274">**Reverting**.</span></span>  
  
     <span data-ttu-id="7b3c6-275">보조 데이터베이스가 주 데이터베이스에서 페이지 가져오기를 현재 진행 중인 경우의 실행 취소 프로세스의 단계를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-275">Indicates the phase in the undo process when a secondary database is actively getting pages from the primary database.</span></span>  
  
    > [!CAUTION]  
    >  <span data-ttu-id="7b3c6-276">데이터베이스가 REVERTING 상태일 때 보조 복제본에 대한 장애 조치를 강제로 실행하면 해당 데이터베이스가 시작할 수 없는 상태로 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-276">When a database is in the REVERTING state, forcing failover to the secondary replica can leave that database in a state in which it cannot be started.</span></span>  
  
-   <span data-ttu-id="7b3c6-277">**초기화 중**.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-277">**Initializing**.</span></span>  
  
     <span data-ttu-id="7b3c6-278">보조 데이터베이스에서 실행 취소 LSN을 catch하는 데 필요한 트랜잭션 로그가 보조 복제본에서 제공되고 확정 중인 경우의 실행 취소 단계를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-278">Indicates the phase of undo when the transaction log required for a secondary database to catch up to the undo LSN is being shipped and hardened on a secondary replica.</span></span>  
  
    > [!CAUTION]  
    >  <span data-ttu-id="7b3c6-279">데이터베이스가 INITIALIZING 상태일 때 보조 복제본에 대한 장애 조치를 강제로 실행하면 해당 데이터베이스가 시작할 수 없는 상태로 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-279">When a database is in the INITIALIZING state, forcing failover to the secondary replica will always leave that database in a state in which it cannot be started.</span></span>  
  
 <span data-ttu-id="7b3c6-280">**장애 조치(Failover) 준비**</span><span class="sxs-lookup"><span data-stu-id="7b3c6-280">**Failover Readiness**</span></span>  
 <span data-ttu-id="7b3c6-281">잠재적인 데이터 손실을 발생 또는 발생하지 않고 장애 조치할 수 있는 가용성 복제본을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-281">Indicates which availability replica can be failed over with or without potential data loss.</span></span> <span data-ttu-id="7b3c6-282">이 열은 기본적으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-282">This column is shown by default.</span></span> <span data-ttu-id="7b3c6-283">사용 가능한 값은</span><span class="sxs-lookup"><span data-stu-id="7b3c6-283">The possible values are:</span></span>  
  
-   <span data-ttu-id="7b3c6-284">**데이터 손실**</span><span class="sxs-lookup"><span data-stu-id="7b3c6-284">**Data Loss**</span></span>  
  
-   <span data-ttu-id="7b3c6-285">**데이터 손실 없음**</span><span class="sxs-lookup"><span data-stu-id="7b3c6-285">**No Data Loss**</span></span>  
  
 <span data-ttu-id="7b3c6-286">**문제**</span><span class="sxs-lookup"><span data-stu-id="7b3c6-286">**Issues**</span></span>  
 <span data-ttu-id="7b3c6-287">문제 이름을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-287">Lists the issue name.</span></span> <span data-ttu-id="7b3c6-288">이 열은 기본적으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-288">This column is shown by default.</span></span> <span data-ttu-id="7b3c6-289">사용 가능한 값은</span><span class="sxs-lookup"><span data-stu-id="7b3c6-289">The possible values are:</span></span>  
  
-   <span data-ttu-id="7b3c6-290">**경고**.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-290">**Warnings**.</span></span> <span data-ttu-id="7b3c6-291">임계값 및 경고 문제를 표시하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-291">Click to display the thresholds and warnings issues.</span></span>  
  
-   <span data-ttu-id="7b3c6-292">**심각**.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-292">**Critical**.</span></span> <span data-ttu-id="7b3c6-293">심각한 문제를 표시하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-293">Click to display the critical issues.</span></span>  
  
 <span data-ttu-id="7b3c6-294">모든 AlwaysOn 정책 문제 목록은 [AlwaysOn 가용성 그룹의 작동 문제에 대 한 Alwayson 정책 (SQL Server)](always-on-policies-for-operational-issues-always-on-availability.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-294">For a list of all the AlwaysOn policy issues, see [AlwaysOn Policies for Operational Issues with AlwaysOn Availability Groups (SQL Server)](always-on-policies-for-operational-issues-always-on-availability.md).</span></span>  
  
 <span data-ttu-id="7b3c6-295">**일시 중지됨**</span><span class="sxs-lookup"><span data-stu-id="7b3c6-295">**Suspended**</span></span>  
 <span data-ttu-id="7b3c6-296">데이터베이스가 **일시 중지됨** 상태인지 아니면 **재개됨**상태인지 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-296">Indicates whether the database is **Suspended** or has been **Resumed**.</span></span> <span data-ttu-id="7b3c6-297">이 값은 기본적으로 숨겨집니다.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-297">This value is hidden by default.</span></span>  
  
 <span data-ttu-id="7b3c6-298">**일시 중지 원인**</span><span class="sxs-lookup"><span data-stu-id="7b3c6-298">**Suspend Reason**</span></span>  
 <span data-ttu-id="7b3c6-299">일시 중지됨 상태에 대한 이유를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-299">Indicates the reason for the suspended state.</span></span> <span data-ttu-id="7b3c6-300">이 값은 기본적으로 숨겨집니다.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-300">This value is hidden by default.</span></span>  
  
 <span data-ttu-id="7b3c6-301">**예상 데이터 손실(초)**</span><span class="sxs-lookup"><span data-stu-id="7b3c6-301">**Estimate Data Loss (seconds)**</span></span>  
 <span data-ttu-id="7b3c6-302">주 복제본과 보조 복제본에서 마지막 트랜잭션 로그 레코드의 시간 차이를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-302">Indicates the time difference of the last transaction log record in the primary replica and secondary replica.</span></span> <span data-ttu-id="7b3c6-303">주 복제본이 실패하는 경우 시간 창 내의 모든 트랜잭션 로그 레코드가 손실됩니다.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-303">If the primary replica fails, all transaction log records within the time window will be lost.</span></span> <span data-ttu-id="7b3c6-304">이 값은 기본적으로 숨겨집니다.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-304">This value is hidden by default.</span></span>  
  
 <span data-ttu-id="7b3c6-305">**예상 복구 시간(초)**</span><span class="sxs-lookup"><span data-stu-id="7b3c6-305">**Estimated Recovery Time (seconds)**</span></span>  
 <span data-ttu-id="7b3c6-306">catchup 시간을 다시 실행하는 데 걸리는 시간(초)을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-306">Indicates the time in seconds it takes to redo the catch-up time.</span></span> <span data-ttu-id="7b3c6-307">*catch-up 시간* 은 보조 복제본이 주 복제본을 따라잡기 위해 걸리는 시간입니다.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-307">The *catch-up time* is the time it will take for the secondary replica to catch up with the primary replica.</span></span> <span data-ttu-id="7b3c6-308">이 값은 기본적으로 숨겨집니다.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-308">This value is hidden by default.</span></span>  
  
 <span data-ttu-id="7b3c6-309">**동기화 성능(초)**</span><span class="sxs-lookup"><span data-stu-id="7b3c6-309">**Synchronization Performance (seconds)**</span></span>  
 <span data-ttu-id="7b3c6-310">주 복제본과 보조 복제본을 동기화하는 데 걸리는 시간(초)을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-310">Indicates the time in seconds it takes to synchronize between the primary and secondary replicas.</span></span> <span data-ttu-id="7b3c6-311">이 값은 기본적으로 숨겨집니다.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-311">This value is hidden by default.</span></span>  
  
 <span data-ttu-id="7b3c6-312">**로그 전송 큐 크기(KB)**</span><span class="sxs-lookup"><span data-stu-id="7b3c6-312">**Log Send Queue Size (KB)**</span></span>  
 <span data-ttu-id="7b3c6-313">보조 복제본으로 전송되지 않은 주 데이터베이스의 로그 파일에 있는 로그 레코드의 크기를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-313">Indicates the amount of log records in the log files of the primary database that have not been sent to the secondary replica.</span></span> <span data-ttu-id="7b3c6-314">이 값은 기본적으로 숨겨집니다.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-314">This value is hidden by default.</span></span>  
  
 <span data-ttu-id="7b3c6-315">**로그 전송 속도(KB/초)**</span><span class="sxs-lookup"><span data-stu-id="7b3c6-315">**Log Send Rate (KB/sec)**</span></span>  
 <span data-ttu-id="7b3c6-316">로그 레코드를 보조 복제본으로 전송하는 속도(KB/초)를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-316">Indicates the rate in KB per second at which log records are being sent to the secondary replica This value is hidden by default.</span></span>  
  
 <span data-ttu-id="7b3c6-317">**Redo Queue 크기(KB)**</span><span class="sxs-lookup"><span data-stu-id="7b3c6-317">**Redo Queue Size (KB)**</span></span>  
 <span data-ttu-id="7b3c6-318">아직 다시 실행되지 않은 보조 복제본의 로그 파일에 있는 로그 레코드 크기를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-318">Indicates the amount of log records in the log files of the secondary replica that have not yet been redone.</span></span> <span data-ttu-id="7b3c6-319">이 값은 기본적으로 숨겨집니다.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-319">This value is hidden by default.</span></span>  
  
 <span data-ttu-id="7b3c6-320">**다시 실행 속도(KB/초)**</span><span class="sxs-lookup"><span data-stu-id="7b3c6-320">**Redo Rate (KB/sec)**</span></span>  
 <span data-ttu-id="7b3c6-321">로그 레코드를 다시 실행하는 속도(KB/초)를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-321">Indicates the rate in KB per second at which the log records are being redone.</span></span> <span data-ttu-id="7b3c6-322">이 값은 기본적으로 숨겨집니다.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-322">This value is hidden by default.</span></span>  
  
 <span data-ttu-id="7b3c6-323">**파일 스트림 전송 속도(KB/초)**</span><span class="sxs-lookup"><span data-stu-id="7b3c6-323">**FileStream Send Rate (KB/sec)**</span></span>  
 <span data-ttu-id="7b3c6-324">트랜잭션을 복제본으로 전송 중인 파일 스트림의 속도(KB/초)를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-324">Indicates the rate of the FileStream in KB per second at which transactions are being sent to the replica.</span></span> <span data-ttu-id="7b3c6-325">이 값은 기본적으로 숨겨집니다.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-325">This value is hidden by default.</span></span>  
  
 <span data-ttu-id="7b3c6-326">**로그 LSN의 끝**</span><span class="sxs-lookup"><span data-stu-id="7b3c6-326">**End of Log LSN**</span></span>  
 <span data-ttu-id="7b3c6-327">주 복제본과 보조 복제본의 로그 캐시에 있는 마지막 로그 레코드에 해당하는 실제 LSN(로그 시퀀스 번호)을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-327">Indicates the actual log sequence number (LSN) that corresponds to the last log record in the log cache on the primary and secondary replicas.</span></span> <span data-ttu-id="7b3c6-328">이 값은 기본적으로 숨겨집니다.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-328">This value is hidden by default.</span></span>  
  
 <span data-ttu-id="7b3c6-329">**복구 LSN**</span><span class="sxs-lookup"><span data-stu-id="7b3c6-329">**Recovery LSN**</span></span>  
 <span data-ttu-id="7b3c6-330">복제본이 주 복제본에서 복구 또는 장애 조치(failover) 후 새 로그 레코드를 쓰기 전의 트랜잭션 로그 끝을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-330">Indicates the end of the transaction log before the replica writes any new log records after recovery or failover on the primary replica.</span></span> <span data-ttu-id="7b3c6-331">이 값은 기본적으로 숨겨집니다.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-331">This value is hidden by default.</span></span>  
  
 <span data-ttu-id="7b3c6-332">**잘림 LSN**</span><span class="sxs-lookup"><span data-stu-id="7b3c6-332">**Truncation LSN**</span></span>  
 <span data-ttu-id="7b3c6-333">주 복제본에 대한 최소 로그 잘림 값을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-333">Indicates the minimum log truncation value for the primary replica.</span></span> <span data-ttu-id="7b3c6-334">이 값은 기본적으로 숨겨집니다.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-334">This value is hidden by default.</span></span>  
  
 <span data-ttu-id="7b3c6-335">**마지막 커밋 LSN**</span><span class="sxs-lookup"><span data-stu-id="7b3c6-335">**Last Commit LSN**</span></span>  
 <span data-ttu-id="7b3c6-336">트랜잭션 로그의 마지막 커밋 레코드에 해당하는 실제 LSN을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-336">Indicates the actual LSN corresponding to the last commit record in the transaction log.</span></span> <span data-ttu-id="7b3c6-337">이 값은 기본적으로 숨겨집니다.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-337">This value is hidden by default.</span></span>  
  
 <span data-ttu-id="7b3c6-338">**마지막 커밋 시간**</span><span class="sxs-lookup"><span data-stu-id="7b3c6-338">**Last Commit Time**</span></span>  
 <span data-ttu-id="7b3c6-339">마지막 커밋 레코드에 해당하는 시간을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-339">Indicates the time corresponding to the last commit record.</span></span> <span data-ttu-id="7b3c6-340">이 값은 기본적으로 숨겨집니다.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-340">This value is hidden by default.</span></span>  
  
 <span data-ttu-id="7b3c6-341">**마지막 전송 LSN**</span><span class="sxs-lookup"><span data-stu-id="7b3c6-341">**Last Sent LSN**</span></span>  
 <span data-ttu-id="7b3c6-342">모든 로그 블록이 주 복제본에 의해 전송된 지점을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-342">Indicates the point up to which all log blocks have been sent by the primary replica.</span></span> <span data-ttu-id="7b3c6-343">이 값은 기본적으로 숨겨집니다.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-343">This value is hidden by default.</span></span>  
  
 <span data-ttu-id="7b3c6-344">**마지막 전송 시간**</span><span class="sxs-lookup"><span data-stu-id="7b3c6-344">**Last Sent Time**</span></span>  
 <span data-ttu-id="7b3c6-345">마지막 로그 블록이 전송된 시간을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-345">Indicates the time when the last log block was sent.</span></span> <span data-ttu-id="7b3c6-346">이 값은 기본적으로 숨겨집니다.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-346">This value is hidden by default.</span></span>  
  
 <span data-ttu-id="7b3c6-347">**마지막으로 받은 LSN**</span><span class="sxs-lookup"><span data-stu-id="7b3c6-347">**Last Received LSN**</span></span>  
 <span data-ttu-id="7b3c6-348">보조 데이터베이스를 호스팅하는 보조 복제본이 모든 로그 블록을 받은 지점을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-348">Indicates the point up to which all log blocks have been received by the secondary replica that hosts the secondary database.</span></span> <span data-ttu-id="7b3c6-349">이 값은 기본적으로 숨겨집니다.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-349">This value is hidden by default.</span></span>  
  
 <span data-ttu-id="7b3c6-350">**마지막으로 받은 시간**</span><span class="sxs-lookup"><span data-stu-id="7b3c6-350">**Last Received Time**</span></span>  
 <span data-ttu-id="7b3c6-351">보조 복제본에서 마지막으로 받은 메시지의 로그 블록 식별자를 읽은 시간을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-351">Indicates the time when the log block identifier in last message received was read on the secondary replica.</span></span> <span data-ttu-id="7b3c6-352">이 값은 기본적으로 숨겨집니다.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-352">This value is hidden by default.</span></span>  
  
 <span data-ttu-id="7b3c6-353">**마지막으로 확정된 LSN**</span><span class="sxs-lookup"><span data-stu-id="7b3c6-353">**Last Hardened LSN**</span></span>  
 <span data-ttu-id="7b3c6-354">모든 로그 블록이 보조 복제본의 디스크에 플러시된 지점을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-354">Indicates the point up to which all log records have been flushed to disk on the secondary replica.</span></span> <span data-ttu-id="7b3c6-355">이 값은 기본적으로 숨겨집니다.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-355">This value is hidden by default.</span></span>  
  
 <span data-ttu-id="7b3c6-356">**마지막으로 확정된 시간**</span><span class="sxs-lookup"><span data-stu-id="7b3c6-356">**Last Hardened Time**</span></span>  
 <span data-ttu-id="7b3c6-357">보조 복제본에서 마지막으로 확정된 LSN에 대한 로그 블록 식별자를 수신한 시간을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-357">Indicates the time when the log-block identifier was received for the last hardened LSN on the secondary replica.</span></span> <span data-ttu-id="7b3c6-358">이 값은 기본적으로 숨겨집니다.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-358">This value is hidden by default.</span></span>  
  
 <span data-ttu-id="7b3c6-359">**마지막으로 다시 실행된 LSN**</span><span class="sxs-lookup"><span data-stu-id="7b3c6-359">**Last Redone LSN**</span></span>  
 <span data-ttu-id="7b3c6-360">보조 복제본에서 마지막으로 다시 실행된 로그 레코드의 실제 LSN을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-360">Indicates the actual LSN of the log record that was redone last on the secondary replica.</span></span> <span data-ttu-id="7b3c6-361">이 값은 기본적으로 숨겨집니다.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-361">This value is hidden by default.</span></span>  
  
 <span data-ttu-id="7b3c6-362">**마지막으로 다시 실행된 시간**</span><span class="sxs-lookup"><span data-stu-id="7b3c6-362">**Last Redone Time**</span></span>  
 <span data-ttu-id="7b3c6-363">보조 데이터베이스에서 마지막 로그 레코드가 다시 실행된 시간을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-363">Indicates the time when the last log record was redone on the secondary database.</span></span> <span data-ttu-id="7b3c6-364">이 값은 기본적으로 숨겨집니다.</span><span class="sxs-lookup"><span data-stu-id="7b3c6-364">This value is hidden by default.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="7b3c6-365">관련 작업</span><span class="sxs-lookup"><span data-stu-id="7b3c6-365">Related Tasks</span></span>  
  
-   [<span data-ttu-id="7b3c6-366">AlwaysOn 정책을 사용 하 여 가용성 그룹 &#40;SQL Server 상태를 확인&#41;</span><span class="sxs-lookup"><span data-stu-id="7b3c6-366">Use AlwaysOn Policies to View the Health of an Availability Group &#40;SQL Server&#41;</span></span>](use-always-on-policies-to-view-the-health-of-an-availability-group-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="7b3c6-367">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7b3c6-367">See Also</span></span>  
 <span data-ttu-id="7b3c6-368">[sys.dm_os_performance_counters&#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-os-performance-counters-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="7b3c6-368">[sys.dm_os_performance_counters &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-os-performance-counters-transact-sql) </span></span>  
 [<span data-ttu-id="7b3c6-369">가용성 그룹 모니터링&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="7b3c6-369">Monitoring of Availability Groups &#40;SQL Server&#41;</span></span>](monitoring-of-availability-groups-sql-server.md)  
  
  
