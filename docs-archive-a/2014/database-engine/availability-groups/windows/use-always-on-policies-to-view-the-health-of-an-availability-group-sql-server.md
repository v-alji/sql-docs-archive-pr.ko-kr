---
title: AlwaysOn 정책을 사용 하 여 가용성 그룹의 상태 보기 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2019
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], policies
ms.assetid: 6f1bcbc3-1220-4071-8e53-4b957f5d3089
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 5c4444afc2348b2407dc19c1c12761ef0251631e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741263"
---
# <a name="use-alwayson-policies-to-view-the-health-of-an-availability-group-sql-server"></a><span data-ttu-id="8444e-102">AlwaysOn 정책을 사용하여 가용성 그룹의 상태 보기(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="8444e-102">Use AlwaysOn Policies to View the Health of an Availability Group (SQL Server)</span></span>
  <span data-ttu-id="8444e-103">이 항목에서는 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 의 AlwaysOn 정책 또는 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]의 PowerShell을 사용하여 AlwaysOn 가용성 그룹의 작동 상태를 확인하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="8444e-103">This topic describes how to determine the operational health of an AlwaysOn availability group by using an AlwaysOn policy in [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] or PowerShell in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="8444e-104">AlwaysOn 정책 기반 관리에 대 한 자세한 내용은 [AlwaysOn 가용성 그룹의 작업 문제에 대 한 Alwayson 정책 (SQL Server)](always-on-policies-for-operational-issues-always-on-availability.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="8444e-104">For information about AlwaysOn Policy Based Management, see [AlwaysOn Policies for Operational Issues with AlwaysOn Availability Groups (SQL Server)](always-on-policies-for-operational-issues-always-on-availability.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="8444e-105">AlwaysOn 정책의 경우 범주 이름이 ID로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="8444e-105">For AlwaysOn policies, the category names are used as IDs.</span></span> <span data-ttu-id="8444e-106">AlwaysOn 범주의 이름을 변경하면 상태 평가 기능이 작동하지 않으므로</span><span class="sxs-lookup"><span data-stu-id="8444e-106">Changing the name of an AlwaysOn category would break its health-evaluation functionality.</span></span> <span data-ttu-id="8444e-107">따라서 AlwaysOn 범주의 이름을 수정해서는 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8444e-107">Therefore, the names of AlwaysOn category should never be modified.</span></span>  
  

  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="8444e-108">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="8444e-108">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="8444e-109">보안</span><span class="sxs-lookup"><span data-stu-id="8444e-109">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="8444e-110">권한</span><span class="sxs-lookup"><span data-stu-id="8444e-110">Permissions</span></span>  
 <span data-ttu-id="8444e-111">연결, 서버 상태 보기 및 모든 정의 보기 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="8444e-111">Requires CONNECT, VIEW SERVER STATE, and VIEW ANY DEFINITION permissions.</span></span>  
  
##  <a name="using-the-alwayson-dashboard"></a><a name="SSMSProcedure"></a><span data-ttu-id="8444e-112">AlwaysOn 대시보드 사용</span><span class="sxs-lookup"><span data-stu-id="8444e-112">Using the AlwaysOn Dashboard</span></span>  
 <span data-ttu-id="8444e-113">**AlwaysOn 대시보드를 열려면**</span><span class="sxs-lookup"><span data-stu-id="8444e-113">**To open the AlwaysOn Dashboard**</span></span>  
  
1.  <span data-ttu-id="8444e-114">개체 탐색기에서 가용성 복제본 중 하나를 호스팅하는 서버 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="8444e-114">In Object Explorer, connect to the server instance that hosts one of the availability replicas.</span></span> <span data-ttu-id="8444e-115">가용성 그룹의 모든 가용성 복제본에 대한 정보를 보려면 주 복제본을 호스팅하는 서버 인스턴스를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="8444e-115">To view information about all of the availability replicas in an availability group, use to the server instance that hosts the primary replica.</span></span>  
  
2.  <span data-ttu-id="8444e-116">서버 이름을 클릭하여 서버 트리를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="8444e-116">Click the server name to expand the server tree.</span></span>  
  
3.  <span data-ttu-id="8444e-117">**AlwaysOn 고가용성** 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="8444e-117">Expand the **AlwaysOn High Availability** node.</span></span>  
  
     <span data-ttu-id="8444e-118">**가용성 그룹** 을 마우스 오른쪽 단추로 클릭하거나 이 노드를 확장하고 특정 가용성 그룹을 마우스 오른쪽 단추로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8444e-118">Either right-click the **Availability Groups** node or expand this node and right-click a specific availability group.</span></span>  
  
4.  <span data-ttu-id="8444e-119">**대시보드 표시** 명령을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8444e-119">Select the **Show Dashboard** command.</span></span>  
  
 <span data-ttu-id="8444e-120">AlwaysOn 대시보드를 사용하는 방법에 대한 자세한 내용은 [AlwaysOn 대시보드 사용&#40;SQL Server Management Studio&#41;](use-the-always-on-dashboard-sql-server-management-studio.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8444e-120">For information about how to use the AlwaysOn Dashboard, see [Use the AlwaysOn Dashboard &#40;SQL Server Management Studio&#41;](use-the-always-on-dashboard-sql-server-management-studio.md).</span></span>  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a> <span data-ttu-id="8444e-121">PowerShell 사용</span><span class="sxs-lookup"><span data-stu-id="8444e-121">Using PowerShell</span></span>  
 <span data-ttu-id="8444e-122">**AlwaysOn 정책을 사용 하 여 가용성 그룹의 상태 보기**</span><span class="sxs-lookup"><span data-stu-id="8444e-122">**Use AlwaysOn policies to view the health of an availability group**</span></span>  
  
1.  <span data-ttu-id="8444e-123">가용성 복제본 중 하나를 호스팅하는 서버 인스턴스로 기본값을 설정(`cd`)합니다.</span><span class="sxs-lookup"><span data-stu-id="8444e-123">Set default (`cd`) to a server instance that hosts one of the availability replicas.</span></span> <span data-ttu-id="8444e-124">가용성 그룹의 모든 가용성 복제본에 대한 정보를 보려면 주 복제본을 호스팅하는 서버 인스턴스를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="8444e-124">To view information about all of the availability replicas in an availability group, use to the server instance that hosts the primary replica.</span></span>  
  
2.  <span data-ttu-id="8444e-125">다음 cmdlet을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="8444e-125">Use the following cmdlets:</span></span>  
  
     `Test-SqlAvailabilityGroup`  
     <span data-ttu-id="8444e-126">SQL Server PBM(정책 기반 관리) 정책을 평가하여 가용성 그룹의 상태를 평가합니다.</span><span class="sxs-lookup"><span data-stu-id="8444e-126">Assesses the health of an availability group by evaluating SQL Server policy based management (PBM) policies.</span></span> <span data-ttu-id="8444e-127">이 cmdlet을 실행하려면 연결, 서버 상태 보기 및 모든 정의 보기 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8444e-127">You must have CONNECT, VIEW SERVER STATE, and VIEW ANY DEFINITION permissions to execute this cmdlet.</span></span>  
  
     <span data-ttu-id="8444e-128">예를 들어 다음 명령은 서버 인스턴스 `Computer\Instance`에서 상태가 "오류"인 모든 가용성 그룹을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="8444e-128">For example, the following command shows all availability groups with a health state of "Error" on the server instance `Computer\Instance`.</span></span>  
  
    ```powershell
    Get-ChildItem SQLSERVER:\Sql\Computer\Instance\AvailabilityGroups |
        Test-SqlAvailabilityGroup |
        Where-Object { $_.HealthState -eq "Error" }  
    ```  
  
     `Test-SqlAvailabilityReplica`  
     <span data-ttu-id="8444e-129">SQL Server PBM(정책 기반 관리) 정책을 평가하여 가용성 복제본의 상태를 평가합니다.</span><span class="sxs-lookup"><span data-stu-id="8444e-129">Assesses the health of availability replicas by evaluating SQL Server policy based management (PBM) policies.</span></span> <span data-ttu-id="8444e-130">이 cmdlet을 실행하려면 연결, 서버 상태 보기 및 모든 정의 보기 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8444e-130">You must have CONNECT, VIEW SERVER STATE, and VIEW ANY DEFINITION permissions to execute this cmdlet.</span></span>  
  
     <span data-ttu-id="8444e-131">예를 들어 다음 명령은 `MyReplica` 가용성 그룹에서 `MyAg` 라는 가용성 복제본의 상태를 평가하고 간단한 요약을 출력합니다.</span><span class="sxs-lookup"><span data-stu-id="8444e-131">For example, the following command evaluates the health of the availability replica named `MyReplica` in the availability group `MyAg` and outputs a brief summary.</span></span>  
  
    ```powershell
    Test-SqlAvailabilityReplica -Path SQLSERVER:\Sql\Computer\Instance\AvailabilityGroups\MyAg\AvailabilityReplicas\MyReplica  
    ```  
  
     `Test-SqlDatabaseReplicaState`  
     <span data-ttu-id="8444e-132">SQL Server PBM(정책 기반 관리) 정책을 평가하여 모든 조인된 가용성 복제본에 대한 가용성 데이터베이스 상태를 평가합니다.</span><span class="sxs-lookup"><span data-stu-id="8444e-132">Assesses the health of an availability database on all joined availability replicas by evaluating SQL Server policy based management (PBM) policies.</span></span>  
  
     <span data-ttu-id="8444e-133">예를 들어 다음 명령은 `MyAg` 가용성 그룹에서 모든 가용성 데이터베이스의 상태를 평가하고 각 데이터베이스에 대해 간단한 요약을 출력합니다.</span><span class="sxs-lookup"><span data-stu-id="8444e-133">For example, the following command evaluates the health of all availability databases in the availability group `MyAg` and outputs a brief summary for each database.</span></span>  
  
    ```powershell
    Get-ChildItem SQLSERVER:\Sql\Computer\Instance\AvailabilityGroups\MyAg\DatabaseReplicaStates |
        Test-SqlDatabaseReplicaState  
    ```  
  
     <span data-ttu-id="8444e-134">이러한 cmdlet은 다음 옵션을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="8444e-134">These cmdlets accept the following options:</span></span>  
  
    |<span data-ttu-id="8444e-135">옵션</span><span class="sxs-lookup"><span data-stu-id="8444e-135">Option</span></span>|<span data-ttu-id="8444e-136">설명</span><span class="sxs-lookup"><span data-stu-id="8444e-136">Description</span></span>|  
    |------------|-----------------|  
    |`AllowUserPolicies`|<span data-ttu-id="8444e-137">AlwaysOn 정책 범주에 있는 사용자 정책을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="8444e-137">Runs user policies found in the AlwaysOn policy categories.</span></span>|  
    |`InputObject`|<span data-ttu-id="8444e-138">사용 중인 cmdlet에 따라 가용성 그룹, 가용성 복제본 또는 가용성 데이터베이스 상태를 나타내는 개체 모음입니다.</span><span class="sxs-lookup"><span data-stu-id="8444e-138">A collection of objects that, represent availability groups, availability replicas, or availability database states (depending on which cmdlet you are using).</span></span> <span data-ttu-id="8444e-139">cmdlet은 지정된 개체의 상태를 컴퓨팅합니다.</span><span class="sxs-lookup"><span data-stu-id="8444e-139">The cmdlet will compute the health of the specified objects.</span></span>|  
    |`NoRefresh`|<span data-ttu-id="8444e-140">이 매개 변수를 설정한 경우 cmdlet은 `-Path` 또는 `-InputObject` 매개 변수에 지정된 개체를 수동으로 새로 고치지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8444e-140">When this parameter is set, the cmdlet will not manually refresh the objects specified by the `-Path` or `-InputObject` parameter.</span></span>|  
    |`Path`|<span data-ttu-id="8444e-141">사용 중인 cmdlet에 따라 가용성 그룹의 경로, 하나 이상의 가용성 복제본 또는 가용성 데이터베이스의 데이터베이스 복제본 클러스터 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="8444e-141">The path to the availability group, one or more availability replicas, or database replica cluster state of the availability database (depending on which cmdlet you are using).</span></span> <span data-ttu-id="8444e-142">선택적 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="8444e-142">This is an optional parameter.</span></span> <span data-ttu-id="8444e-143">지정하지 않으면 이 매개 변수의 값은 기본적으로 현재 작업 위치입니다.</span><span class="sxs-lookup"><span data-stu-id="8444e-143">If not specified, the value of this parameter defaults to the current working location.</span></span>|  
    |`ShowPolicyDetails`|<span data-ttu-id="8444e-144">이 cmdlet에서 수행하는 각 정책 평가의 결과를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="8444e-144">Shows the result of each policy evaluation performed by this cmdlet.</span></span> <span data-ttu-id="8444e-145">cmdlet은 정책 평가당 하나의 개체를 출력하며, 이 개체에는 평가 결과(정책 통과 여부, 정책 이름과 범주 등)를 설명하는 필드가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8444e-145">The cmdlet outputs one object per policy evaluation, and this object has fields describing the results of evaluation (whether the policy passed or not, the policy name and category, and so forth).</span></span>|  
  
     <span data-ttu-id="8444e-146">예를 들어 다음 `Test-SqlAvailabilityGroup` 명령은 `-ShowPolicyDetails` 매개 변수를 지정하고 `MyAg`라는 가용성 그룹에서 실행된 각 PBM(정책 기반 관리) 정책에 대해 이 cmdlet에서 수행한 정책 평가 결과를 각각 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="8444e-146">For example, the following `Test-SqlAvailabilityGroup` command specifies the `-ShowPolicyDetails` parameter to show the result of each policy evaluation performed by this cmdlet for each policy-based management (PBM) policy that was executed on the availability group named `MyAg`.</span></span>  
  
    ```powershell
    Test-SqlAvailabilityGroup -Path SQLSERVER:\Sql\Computer\Instance\AvailabilityGroups\AgName -ShowPolicyDetails  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="8444e-147">cmdlet의 구문을 보려면 `Get-Help` PowerShell 환경에서 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] cmdlet을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="8444e-147">To view the syntax of a cmdlet, use the `Get-Help` cmdlet in the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell environment.</span></span> <span data-ttu-id="8444e-148">자세한 내용은 [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8444e-148">For more information, see [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).</span></span>  
  
 <span data-ttu-id="8444e-149">**SQL Server PowerShell 공급자를 설정하고 사용하려면**</span><span class="sxs-lookup"><span data-stu-id="8444e-149">**To set up and use the SQL Server PowerShell provider**</span></span>  
  
-   [<span data-ttu-id="8444e-150">SQL Server PowerShell 공급자</span><span class="sxs-lookup"><span data-stu-id="8444e-150">SQL Server PowerShell Provider</span></span>](../../../powershell/sql-server-powershell-provider.md)  
  
-   [<span data-ttu-id="8444e-151">Get Help SQL Server PowerShell</span><span class="sxs-lookup"><span data-stu-id="8444e-151">Get Help SQL Server PowerShell</span></span>](../../../powershell/sql-server-powershell.md)  
  
##  <a name="related-content"></a><a name="RelatedContent"></a> <span data-ttu-id="8444e-152">관련 내용</span><span class="sxs-lookup"><span data-stu-id="8444e-152">Related Content</span></span>  
 <span data-ttu-id="8444e-153">**AlwaysOn 팀 블로그-PowerShell을 사용 하 여 AlwaysOn 상태 모니터링: SQL Server**</span><span class="sxs-lookup"><span data-stu-id="8444e-153">**SQL Server AlwaysOn Team Blogs-Monitoring AlwaysOn Health with PowerShell:**</span></span>  
  
-   [<span data-ttu-id="8444e-154">1부: 기본 Cmdlet 개요</span><span class="sxs-lookup"><span data-stu-id="8444e-154">Part 1: Basic Cmdlet Overview</span></span>](https://docs.microsoft.com/archive/blogs/sqlalwayson/monitoring-alwayson-health-with-powershell-part-1-basic-cmdlet-overview)  
  
-   [<span data-ttu-id="8444e-155">2부: 고급 Cmdlet 사용</span><span class="sxs-lookup"><span data-stu-id="8444e-155">Part 2: Advanced Cmdlet Usage</span></span>](https://docs.microsoft.com/archive/blogs/sqlalwayson/the-alwayson-health-model-part-2-extending-the-health-model)  
  
-   [<span data-ttu-id="8444e-156">3부: 간단한 모니터링 애플리케이션</span><span class="sxs-lookup"><span data-stu-id="8444e-156">Part 3: A Simple Monitoring Application</span></span>](https://docs.microsoft.com/archive/blogs/sqlalwayson/monitoring-alwayson-health-with-powershell-part-3-a-simple-monitoring-application)  
  
-   [<span data-ttu-id="8444e-157">4부: SQL Server 에이전트와의 통합</span><span class="sxs-lookup"><span data-stu-id="8444e-157">Part 4: Integration with SQL Server Agent</span></span>](https://docs.microsoft.com/archive/blogs/sqlalwayson/monitoring-alwayson-health-with-powershell-part-4-integration-with-sql-server-agent)  
  
## <a name="see-also"></a><span data-ttu-id="8444e-158">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8444e-158">See Also</span></span>  
 <span data-ttu-id="8444e-159">[AlwaysOn 가용성 그룹 &#40;SQL Server 개요&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="8444e-159">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="8444e-160">[가용성 그룹 관리 &#40;SQL Server&#41;](administration-of-an-availability-group-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="8444e-160">[Administration of an Availability Group &#40;SQL Server&#41;](administration-of-an-availability-group-sql-server.md) </span></span>  
 <span data-ttu-id="8444e-161">[가용성 그룹 모니터링&#40;SQL Server&#41;](monitoring-of-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="8444e-161">[Monitoring of Availability Groups &#40;SQL Server&#41;](monitoring-of-availability-groups-sql-server.md) </span></span>  
 [<span data-ttu-id="8444e-162">AlwaysOn 가용성 그룹의 운영 문제에 대한 AlwaysOn 정책(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="8444e-162">AlwaysOn Policies for Operational Issues with AlwaysOn Availability Groups (SQL Server)</span></span>](always-on-policies-for-operational-issues-always-on-availability.md) 
