---
title: 클러스터 쿼럼 NodeWeight 설정 구성 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], WSFC clusters
- quorum [SQL Server], AlwaysOn and WSFC quorum
ms.assetid: cb3fd9a6-39a2-4e9c-9157-619bf3db9951
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e469d5fc0fc030304a7cf2f1bdd894eb578aa056
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650568"
---
# <a name="configure-cluster-quorum-nodeweight-settings"></a><span data-ttu-id="71636-102">클러스터 쿼럼 NodeWeight 설정 구성</span><span class="sxs-lookup"><span data-stu-id="71636-102">Configure Cluster Quorum NodeWeight Settings</span></span>
  <span data-ttu-id="71636-103">이 항목에서는 WSFC(Windows Server 장애 조치(failover) 클러스터링) 클러스터의 멤버 노드에 대한 NodeWeight 설정을 구성하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="71636-103">This topic describes how to configure NodeWeight settings for a member node in a Windows Server Failover Clustering (WSFC) cluster.</span></span> <span data-ttu-id="71636-104">NodeWeight 설정은 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 및 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 장애 조치(Failover) 클러스터 인스턴스의 재해 복구 및 다중 서브넷 시나리오를 지원하기 위한 쿼럼 투표 동안 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="71636-104">NodeWeight settings are used during quorum voting to support disaster recovery and multi-subnet scenarios for [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] and [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Failover Cluster Instances.</span></span>  
  
-   <span data-ttu-id="71636-105">**시작하기 전에:**  [필수 구성 요소](#Prerequisites), [보안](#Security)</span><span class="sxs-lookup"><span data-stu-id="71636-105">**Before you start:**  [Prerequisites](#Prerequisites), [Security](#Security)</span></span>  
  
-   <span data-ttu-id="71636-106">**쿼럼 NodeWeight 설정을 보려면 다음을 사용합니다.** [PowerShell 사용](#PowerShellProcedure), [Cluster.exe 사용](#CommandPromptProcedure)</span><span class="sxs-lookup"><span data-stu-id="71636-106">**To view quorum NodeWeight settings using:** [Using Powershell](#PowerShellProcedure), [Using Cluster.exe](#CommandPromptProcedure)</span></span>  
  
-   [<span data-ttu-id="71636-107">관련 내용</span><span class="sxs-lookup"><span data-stu-id="71636-107">Related Content</span></span>](#RelatedContent)  
  
##  <a name="before-you-start"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="71636-108">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="71636-108">Before You Start</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="71636-109">필수 조건</span><span class="sxs-lookup"><span data-stu-id="71636-109">Prerequisites</span></span>  
 <span data-ttu-id="71636-110">이 기능은 [!INCLUDE[firstref_longhorn](../../../includes/firstref-longhorn-md.md)] 이상 버전에서만 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="71636-110">This feature is supported only in [!INCLUDE[firstref_longhorn](../../../includes/firstref-longhorn-md.md)] or later versions.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="71636-111">NodeWeight 설정을 사용하려면 WSFC 클러스터의 모든 서버에 다음 핫픽스를 적용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="71636-111">In order to use NodeWeight settings, the following hotfix must be applied to all servers in the WSFC cluster:</span></span>  
>   
>  <span data-ttu-id="71636-112">[KB2494036](https://support.microsoft.com/kb/2494036): [!INCLUDE[firstref_longhorn](../../../includes/firstref-longhorn-md.md)] 및 [!INCLUDE[winserver2008r2](../../../includes/winserver2008r2-md.md)]에서 쿼럼 투표가 없는 클러스터 노드를 구성하는 데 사용할 수 있는 핫픽스</span><span class="sxs-lookup"><span data-stu-id="71636-112">[KB2494036](https://support.microsoft.com/kb/2494036): A hotfix is available to let you configure a cluster node that does not have quorum votes in [!INCLUDE[firstref_longhorn](../../../includes/firstref-longhorn-md.md)] and in [!INCLUDE[winserver2008r2](../../../includes/winserver2008r2-md.md)]</span></span>  
  
> [!TIP]  
>  <span data-ttu-id="71636-113">이 핫픽스가 설치되어 있지 않은 경우 이 항목의 예는 NodeWeight에 대해 빈 값이나 NULL 값을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="71636-113">If this hotfix is not installed, the examples in this topic will return empty or NULL values for NodeWeight.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="71636-114">보안</span><span class="sxs-lookup"><span data-stu-id="71636-114">Security</span></span>  
 <span data-ttu-id="71636-115">사용자는 WSFC 클러스터의 각 노드에 대한 로컬 Administrators 그룹의 멤버인 도메인 계정이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="71636-115">The user must be a domain account that is member of the local Administrators group on each node of the WSFC cluster.</span></span>  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a> <span data-ttu-id="71636-116">Powershell 사용</span><span class="sxs-lookup"><span data-stu-id="71636-116">Using Powershell</span></span>  
  
### <a name="to-configure-nodeweight-settings"></a><span data-ttu-id="71636-117">NodeWeight 설정을 구성하려면</span><span class="sxs-lookup"><span data-stu-id="71636-117">To configure NodeWeight settings</span></span>
  
1.  <span data-ttu-id="71636-118">**관리자 권한으로 실행**을 통해 승격된 Windows PowerShell을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="71636-118">Start an elevated Windows PowerShell via **Run as Administrator**.</span></span>  
  
2.  <span data-ttu-id="71636-119">클러스터 commandlet을 사용할 수 있도록 `FailoverClusters` 모듈을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="71636-119">Import the `FailoverClusters` module to enable cluster commandlets.</span></span>  
  
3.  <span data-ttu-id="71636-120">`Get-ClusterNode` 개체를 사용하여 클러스터의 각 노드에 대한 `NodeWeight` 속성을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="71636-120">Use the `Get-ClusterNode` object to set the `NodeWeight` property for each node in the cluster.</span></span>  
  
4.  <span data-ttu-id="71636-121">클러스터 노드 속성을 읽기 가능한 형식으로 출력합니다.</span><span class="sxs-lookup"><span data-stu-id="71636-121">Output the cluster node properties in a readable format.</span></span>  
  
 <span data-ttu-id="71636-122">다음 예제에서는 NodeWeight 설정을 변경하여 "AlwaysOnSrv1" 노드에 대한 쿼럼 투표를 제거한 다음, 클러스터의 모든 노드에 대한 설정을 출력합니다.</span><span class="sxs-lookup"><span data-stu-id="71636-122">The following example changes the NodeWeight setting to remove the quorum vote for the "AlwaysOnSrv1" node, and then outputs the settings for all nodes in the cluster.</span></span>
  
```powershell  
Import-Module FailoverClusters  
  
$node = "AlwaysOnSrv1"  
(Get-ClusterNode $node).NodeWeight = 0  
  
$cluster = (Get-ClusterNode $node).Cluster  
$nodes = Get-ClusterNode -Cluster $cluster  
  
$nodes | Format-Table -property NodeName, State, NodeWeight  
```  
  
##  <a name="using-clusterexe"></a><a name="CommandPromptProcedure"></a> <span data-ttu-id="71636-123">Cluster.exe 사용</span><span class="sxs-lookup"><span data-stu-id="71636-123">Using Cluster.exe</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="71636-124">cluster.exe 유틸리티는 [!INCLUDE[winserver2008r2](../../../includes/winserver2008r2-md.md)] 릴리스에서 더 이상 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="71636-124">The cluster.exe utility is deprecated in the [!INCLUDE[winserver2008r2](../../../includes/winserver2008r2-md.md)] release.</span></span>  <span data-ttu-id="71636-125">이후 개발에는 PowerShell과 장애 조치(failover) 클러스터링을 함께 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="71636-125">Please use PowerShell with Failover Clustering for future development.</span></span>  <span data-ttu-id="71636-126">cluster.exe 유틸리티는 Windows Server의 다음 릴리스에서 제거될 예정입니다.</span><span class="sxs-lookup"><span data-stu-id="71636-126">The cluster.exe utility will be removed in the next release of Windows Server.</span></span> <span data-ttu-id="71636-127">자세한 내용은 [Cluster.exe 명령을 장애 조치(failover) 클러스터용 Windows PowerShell Cmdlet에 매핑](https://technet.microsoft.com/library/ee619744\(WS.10\).aspx)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="71636-127">For more information, see [Mapping Cluster.exe Commands to Windows PowerShell Cmdlets for Failover Clusters](https://technet.microsoft.com/library/ee619744\(WS.10\).aspx).</span></span>  
  
### <a name="to-configure-nodeweight-settings"></a><span data-ttu-id="71636-128">NodeWeight 설정을 구성하려면</span><span class="sxs-lookup"><span data-stu-id="71636-128">To configure NodeWeight settings</span></span>
  
1.  <span data-ttu-id="71636-129">**관리자 권한으로 실행**을 통해 승격된 명령 프롬프트를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="71636-129">Start an elevated Command Prompt via **Run as Administrator**.</span></span>  
  
2.  <span data-ttu-id="71636-130">**cluster.exe** 를 사용하여 `NodeWeight` 값을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="71636-130">Use **cluster.exe** to set `NodeWeight` values.</span></span>  

 <span data-ttu-id="71636-131">다음 예제에서는 NodeWeight 값을 변경하여 “Cluster001” 클러스터의 “AlwaysOnSrv1” 노드에 대한 쿼럼 투표를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="71636-131">The following example changes the NodeWeight value to remove the quorum vote of the "AlwaysOnSrv1" node in the "Cluster001" cluster.</span></span>  
  
```cmd
cluster.exe Cluster001 node AlwaysOnSrv1 /prop NodeWeight=0  
```  
  
##  <a name="related-content"></a><a name="RelatedContent"></a> <span data-ttu-id="71636-132">관련 내용</span><span class="sxs-lookup"><span data-stu-id="71636-132">Related Content</span></span>  
  
-   <span data-ttu-id="71636-133">[장애 조치(Failover) 클러스터에 대한 이벤트 및 로그 보기](https://technet.microsoft.com/library/cc772342\(WS.10\).aspx)</span><span class="sxs-lookup"><span data-stu-id="71636-133">[View Events and Logs for a Failover Cluster](https://technet.microsoft.com/library/cc772342\(WS.10\).aspx)</span></span>  
  
-   [<span data-ttu-id="71636-134">Get-ClusterLog 장애 조치(Failover) 클러스터 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="71636-134">Get-ClusterLog Failover Cluster Cmdlet</span></span>](https://technet.microsoft.com/library/ee461045.aspx)  
  
## <a name="see-also"></a><span data-ttu-id="71636-135">참고 항목</span><span class="sxs-lookup"><span data-stu-id="71636-135">See Also</span></span>  
 <span data-ttu-id="71636-136">[WSFC 쿼럼 모드 및 투표 구성 &#40;SQL Server&#41;](wsfc-quorum-modes-and-voting-configuration-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="71636-136">[WSFC Quorum Modes and Voting Configuration &#40;SQL Server&#41;](wsfc-quorum-modes-and-voting-configuration-sql-server.md) </span></span>  
 <span data-ttu-id="71636-137">[클러스터 쿼럼 NodeWeight 설정 보기](view-cluster-quorum-nodeweight-settings.md) </span><span class="sxs-lookup"><span data-stu-id="71636-137">[View Cluster Quorum NodeWeight Settings](view-cluster-quorum-nodeweight-settings.md) </span></span>  
 <span data-ttu-id="71636-138">[태스크 기준으로 나열된 Windows PowerShell의 장애 조치(failover) 클러스터 Cmdlet](https://technet.microsoft.com/library/ee619761\(WS.10\).aspx)</span><span class="sxs-lookup"><span data-stu-id="71636-138">[Failover Cluster Cmdlets in Windows PowerShell Listed by Task Focus](https://technet.microsoft.com/library/ee619761\(WS.10\).aspx)</span></span>  
