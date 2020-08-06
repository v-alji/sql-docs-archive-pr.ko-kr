---
title: 클러스터 쿼럼 NodeWeight 설정 보기 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], WSFC clusters
- quorum [SQL Server], AlwaysOn and WSFC quorum
ms.assetid: b845e73a-bb01-4de2-aac2-8ac12abebc95
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ef2176d4916e8affbb9ef89c9b26499289c520ce
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650553"
---
# <a name="view-cluster-quorum-nodeweight-settings"></a><span data-ttu-id="16ea0-102">클러스터 쿼럼 NodeWeight 설정 보기</span><span class="sxs-lookup"><span data-stu-id="16ea0-102">View Cluster Quorum NodeWeight Settings</span></span>
  <span data-ttu-id="16ea0-103">이 항목에서는 WSFC(Windows Server 장애 조치(failover) 클러스터링) 클러스터의 각 멤버 노드에 대한 NodeWeight 설정을 보는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="16ea0-103">This topic describes how to view NodeWeight settings for each member node in a Windows Server Failover Clustering (WSFC) cluster.</span></span> <span data-ttu-id="16ea0-104">NodeWeight 설정은 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 및 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 장애 조치(Failover) 클러스터 인스턴스의 재해 복구 및 다중 서브넷 시나리오를 지원하기 위한 쿼럼 투표 동안 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="16ea0-104">NodeWeight settings are used during quorum voting to support disaster recovery and multi-subnet scenarios for [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] and [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Failover Cluster Instances.</span></span>  
  
-   <span data-ttu-id="16ea0-105">**시작하기 전에:**  [필수 구성 요소](#Prerequisites), [보안](#Security)</span><span class="sxs-lookup"><span data-stu-id="16ea0-105">**Before you start:**  [Prerequisites](#Prerequisites), [Security](#Security)</span></span>  
  
-   <span data-ttu-id="16ea0-106">**쿼럼 NodeWeight 설정을 보려면 다음을 사용합니다.** [Transact-SQL 사용](#TsqlProcedure), [Powershell 사용](#PowerShellProcedure), [Cluster.exe 사용](#CommandPromptProcedure)</span><span class="sxs-lookup"><span data-stu-id="16ea0-106">**To view quorum NodeWeight settings using:** [Using Transact-SQL](#TsqlProcedure), [Using Powershell](#PowerShellProcedure), [Using Cluster.exe](#CommandPromptProcedure)</span></span>  
  
##  <a name="before-you-start"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="16ea0-107">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="16ea0-107">Before You Start</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="16ea0-108">필수 조건</span><span class="sxs-lookup"><span data-stu-id="16ea0-108">Prerequisites</span></span>  
 <span data-ttu-id="16ea0-109">이 기능은 [!INCLUDE[firstref_longhorn](../../../includes/firstref-longhorn-md.md)] 이상 버전에서만 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="16ea0-109">This feature is supported only in [!INCLUDE[firstref_longhorn](../../../includes/firstref-longhorn-md.md)] or later versions.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="16ea0-110">NodeWeight 설정을 사용하려면 WSFC 클러스터의 모든 서버에 다음 핫픽스를 적용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="16ea0-110">In order to use NodeWeight settings, the following hotfix must be applied to all servers in the WSFC cluster:</span></span>  
>   
>  <span data-ttu-id="16ea0-111">[KB2494036](https://support.microsoft.com/kb/2494036): [!INCLUDE[firstref_longhorn](../../../includes/firstref-longhorn-md.md)] 및 [!INCLUDE[winserver2008r2](../../../includes/winserver2008r2-md.md)]에서 쿼럼 투표가 없는 클러스터 노드를 구성하는 데 사용할 수 있는 핫픽스</span><span class="sxs-lookup"><span data-stu-id="16ea0-111">[KB2494036](https://support.microsoft.com/kb/2494036): A hotfix is available to let you configure a cluster node that does not have quorum votes in [!INCLUDE[firstref_longhorn](../../../includes/firstref-longhorn-md.md)] and in [!INCLUDE[winserver2008r2](../../../includes/winserver2008r2-md.md)]</span></span>  
  
> [!TIP]  
>  <span data-ttu-id="16ea0-112">이 핫픽스가 설치되어 있지 않은 경우 이 항목의 예는 NodeWeight에 대해 빈 값이나 NULL 값을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="16ea0-112">If this hotfix is not installed, the examples in this topic will return empty or NULL values for NodeWeight.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="16ea0-113">보안</span><span class="sxs-lookup"><span data-stu-id="16ea0-113">Security</span></span>  
 <span data-ttu-id="16ea0-114">사용자는 WSFC 클러스터의 각 노드에 대한 로컬 Administrators 그룹의 멤버인 도메인 계정이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="16ea0-114">The user must be a domain account that is member of the local Administrators group on each node of the WSFC cluster.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="16ea0-115">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="16ea0-115">Using Transact-SQL</span></span>  
  
##### <a name="to-view-nodeweight-settings"></a><span data-ttu-id="16ea0-116">NodeWeight 설정을 보려면</span><span class="sxs-lookup"><span data-stu-id="16ea0-116">To view NodeWeight settings</span></span>  
  
1.  <span data-ttu-id="16ea0-117">클러스터의 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="16ea0-117">Connect to any [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instance in the cluster.</span></span>  
  
2.  <span data-ttu-id="16ea0-118">[sys].[dm_hadr_cluster_members] 뷰를 쿼리합니다.</span><span class="sxs-lookup"><span data-stu-id="16ea0-118">Query the [sys].[dm_hadr_cluster_members] view.</span></span>  
  
### <a name="example-transact-sql"></a><span data-ttu-id="16ea0-119">예제(Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="16ea0-119">Example (Transact-SQL)</span></span>  
 <span data-ttu-id="16ea0-120">다음 예제에서는 시스템 뷰를 쿼리하여 해당 인스턴스의 클러스터에 있는 모든 노드에 대한 값을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="16ea0-120">The following example queries a system view to return values for all of the nodes in that instance's cluster.</span></span>  
  
```sql  
SELECT  member_name, member_state_desc, number_of_quorum_votes  
 FROM   sys.dm_hadr_cluster_members;  
```  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a> <span data-ttu-id="16ea0-121">Powershell 사용</span><span class="sxs-lookup"><span data-stu-id="16ea0-121">Using Powershell</span></span>  
  
### <a name="to-view-nodeweight-settings"></a><span data-ttu-id="16ea0-122">NodeWeight 설정을 보려면</span><span class="sxs-lookup"><span data-stu-id="16ea0-122">To view NodeWeight settings</span></span>
  
1.  <span data-ttu-id="16ea0-123">**관리자 권한으로 실행**을 통해 승격된 Windows PowerShell을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="16ea0-123">Start an elevated Windows PowerShell via **Run as Administrator**.</span></span>  
  
2.  <span data-ttu-id="16ea0-124">클러스터 commandlet을 사용할 수 있도록 `FailoverClusters` 모듈을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="16ea0-124">Import the `FailoverClusters` module to enable cluster commandlets.</span></span>  
  
3.  <span data-ttu-id="16ea0-125">`Get-ClusterNode` 개체를 사용하여 클러스터 노드 개체의 컬렉션을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="16ea0-125">Use the `Get-ClusterNode` object to return a collection of cluster node objects.</span></span>  
  
4.  <span data-ttu-id="16ea0-126">클러스터 노드 속성을 읽기 가능한 형식으로 출력합니다.</span><span class="sxs-lookup"><span data-stu-id="16ea0-126">Output the cluster node properties in a readable format.</span></span>  
  
### <a name="example-powershell"></a><span data-ttu-id="16ea0-127">예(Powershell)</span><span class="sxs-lookup"><span data-stu-id="16ea0-127">Example (Powershell)</span></span>  
 <span data-ttu-id="16ea0-128">다음 예제에서는 "Cluster001"이라는 클러스터의 노드 속성 일부를 출력합니다.</span><span class="sxs-lookup"><span data-stu-id="16ea0-128">The following example output some of the node properties for the cluster called "Cluster001".</span></span>  
  
```powershell  
Import-Module FailoverClusters  
  
$cluster = "Cluster001"  
$nodes = Get-ClusterNode -Cluster $cluster  
  
$nodes | Format-Table -Property NodeName, State, NodeWeight  
```  
  
##  <a name="using-clusterexe"></a><a name="CommandPromptProcedure"></a> <span data-ttu-id="16ea0-129">Cluster.exe 사용</span><span class="sxs-lookup"><span data-stu-id="16ea0-129">Using Cluster.exe</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="16ea0-130">cluster.exe 유틸리티는 [!INCLUDE[winserver2008r2](../../../includes/winserver2008r2-md.md)] 릴리스에서 더 이상 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="16ea0-130">The cluster.exe utility is deprecated in the [!INCLUDE[winserver2008r2](../../../includes/winserver2008r2-md.md)] release.</span></span>  <span data-ttu-id="16ea0-131">이후 개발에는 PowerShell과 장애 조치(failover) 클러스터링을 함께 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="16ea0-131">Please use PowerShell with Failover Clustering for future development.</span></span>  <span data-ttu-id="16ea0-132">cluster.exe 유틸리티는 Windows Server의 다음 릴리스에서 제거될 예정입니다.</span><span class="sxs-lookup"><span data-stu-id="16ea0-132">The cluster.exe utility will be removed in the next release of Windows Server.</span></span> <span data-ttu-id="16ea0-133">자세한 내용은 [Cluster.exe 명령을 장애 조치(failover) 클러스터용 Windows PowerShell Cmdlet에 매핑](https://technet.microsoft.com/library/ee619744\(WS.10\).aspx)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="16ea0-133">For more information, see [Mapping Cluster.exe Commands to Windows PowerShell Cmdlets for Failover Clusters](https://technet.microsoft.com/library/ee619744\(WS.10\).aspx).</span></span>  
  
##### <a name="to-view-nodeweight-settings"></a><span data-ttu-id="16ea0-134">NodeWeight 설정을 보려면</span><span class="sxs-lookup"><span data-stu-id="16ea0-134">To view NodeWeight settings</span></span>  
  
1.  <span data-ttu-id="16ea0-135">**관리자 권한으로 실행**을 통해 승격된 명령 프롬프트를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="16ea0-135">Start an elevated Command Prompt via **Run as Administrator**.</span></span>  
  
2.  <span data-ttu-id="16ea0-136">**cluster.exe** 를 사용하여 노드 상태 및 NodeWeight 값을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="16ea0-136">Use **cluster.exe** to return node status and NodeWeight values</span></span>  
  
### <a name="example-clusterexe"></a><span data-ttu-id="16ea0-137">예(Cluster.exe)</span><span class="sxs-lookup"><span data-stu-id="16ea0-137">Example (Cluster.exe)</span></span>  
 <span data-ttu-id="16ea0-138">다음 예제에서는 "Cluster001"이라는 클러스터의 노드 속성 일부를 출력합니다.</span><span class="sxs-lookup"><span data-stu-id="16ea0-138">The following example outputs some of the node properties for the cluster called "Cluster001".</span></span>  
  
```cmd
cluster.exe Cluster001 node /status /properties  
```  
  
## <a name="see-also"></a><span data-ttu-id="16ea0-139">참고 항목</span><span class="sxs-lookup"><span data-stu-id="16ea0-139">See Also</span></span>  
 <span data-ttu-id="16ea0-140">[WSFC 쿼럼 모드 및 투표 구성&#40;SQL Server&#41;](wsfc-quorum-modes-and-voting-configuration-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="16ea0-140">[WSFC Quorum Modes and Voting Configuration &#40;SQL Server&#41;](wsfc-quorum-modes-and-voting-configuration-sql-server.md) </span></span>  
 <span data-ttu-id="16ea0-141">[클러스터 쿼럼 NodeWeight 설정 구성](configure-cluster-quorum-nodeweight-settings.md) </span><span class="sxs-lookup"><span data-stu-id="16ea0-141">[Configure Cluster Quorum NodeWeight Settings](configure-cluster-quorum-nodeweight-settings.md) </span></span>  
 <span data-ttu-id="16ea0-142">[sys.dm_hadr_cluster_members&#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-cluster-members-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="16ea0-142">[sys.dm_hadr_cluster_members &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-cluster-members-transact-sql) </span></span>  
 <span data-ttu-id="16ea0-143">[태스크 기준으로 나열된 Windows PowerShell의 장애 조치(failover) 클러스터 Cmdlet](https://technet.microsoft.com/library/ee619761\(WS.10\).aspx)</span><span class="sxs-lookup"><span data-stu-id="16ea0-143">[Failover Cluster Cmdlets in Windows PowerShell Listed by Task Focus](https://technet.microsoft.com/library/ee619761\(WS.10\).aspx)</span></span>  
