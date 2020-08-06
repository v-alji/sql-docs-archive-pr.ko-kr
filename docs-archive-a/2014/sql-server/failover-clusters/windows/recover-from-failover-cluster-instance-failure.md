---
title: 장애 조치(failover) 클러스터 인스턴스 오류 복구 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- clusters [SQL Server], recovery from failure
- failover clustering [SQL Server], recovery from failure
- hardware failures [SQL Server]
- recovering failover cluster failures [SQL Server]
ms.assetid: 3d151d0c-e841-4325-8606-c094de37d7d1
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 60db4c2e480b094c18d0a8071e947a38cdc779d8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740752"
---
# <a name="recover-from-failover-cluster-instance-failure"></a><span data-ttu-id="886c4-102">장애 조치(failover) 클러스터 인스턴스 오류 복구</span><span class="sxs-lookup"><span data-stu-id="886c4-102">Recover from Failover Cluster Instance Failure</span></span>
  <span data-ttu-id="886c4-103">이 항목에서는 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]에서 장애 조치(failover)가 발생한 후에 장애 조치(failover) 클러스터 관리자 스냅인을 사용하여 클러스터 오류를 복구하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="886c4-103">This topic describes how to recover from cluster failures by using the Failover Cluster Manager snap-in after a failover occurs in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="886c4-104">장애 조치 클러스터 관리자 스냅인은 WSFC(Windows Server 장애 조치(failover) 클러스터링) 서비스용 클러스터 관리 애플리케이션입니다.</span><span class="sxs-lookup"><span data-stu-id="886c4-104">The Failover Cluster Manager snap-in is the cluster management application for the Windows Serer Failover Clustering (WSFC) service.</span></span>  
  
-   [<span data-ttu-id="886c4-105">복구 불가능 오류 복구</span><span class="sxs-lookup"><span data-stu-id="886c4-105">Recover from an irreparable failure</span></span>](#Scenario1)  
  
-   [<span data-ttu-id="886c4-106">소프트웨어 오류 복구</span><span class="sxs-lookup"><span data-stu-id="886c4-106">Recover from a software failure</span></span>](#Scenario2)  
  
##  <a name="recover-from-an-irreparable-failure"></a><a name="Scenario1"></a><span data-ttu-id="886c4-107">불가능 오류 복구</span><span class="sxs-lookup"><span data-stu-id="886c4-107">Recover from an irreparable failure</span></span>  
 <span data-ttu-id="886c4-108">복구 불가능 오류를 복구하려면 다음 단계를 따르세요.</span><span class="sxs-lookup"><span data-stu-id="886c4-108">Use the following steps to recover from an irreparable failure.</span></span> <span data-ttu-id="886c4-109">예를 들어 디스크 컨트롤러 오류나 운영 체제 오류로 인해 이러한 오류가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="886c4-109">The failure could be caused, for example, by the failure of a disk controller or the operating system.</span></span> <span data-ttu-id="886c4-110">이런 경우, 오류는 두 노드 클러스터의 노드 1의 하드웨어 오류로 인해 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="886c4-110">In this case, failure is caused by hardware failure in Node 1 of a two-node cluster.</span></span>  
  
1.  <span data-ttu-id="886c4-111">노드 1에 오류가 발생한 후 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] FCI에서 노드 2로 장애 조치됩니다.</span><span class="sxs-lookup"><span data-stu-id="886c4-111">After Node 1 fails, the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] FCI fails over to Node 2.</span></span>  
  
2.  <span data-ttu-id="886c4-112">FCI에서 노드 1을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="886c4-112">Evict Node 1 from the FCI.</span></span> <span data-ttu-id="886c4-113">이렇게 하려면 노드 2에서 장애 조치(failover) 클러스터 관리자 스냅인을 열고 노드 1을 마우스 오른쪽 단추로 클릭하여 **이동 동작**을 클릭한 다음 **노드 제거**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="886c4-113">To do this, from Node 2, open the Failover Cluster Manager snap-in, right-click Node1, click **Move Actions**, and then click **Evict Node**.</span></span>  
  
3.  <span data-ttu-id="886c4-114">노드 1이 클러스터 정의에서 제거되었는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="886c4-114">Verify that Node 1 has been evicted from the cluster definition.</span></span>  
  
4.  <span data-ttu-id="886c4-115">새 하드웨어를 설치하여 노드 1에서 장애가 발생한 하드웨어를 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="886c4-115">Install new hardware to replace the failed hardware in Node 1.</span></span>  
  
5.  <span data-ttu-id="886c4-116">장애 조치(Failover) 클러스터 관리자 스냅인을 사용하여 기존 클러스터에 노드 1을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="886c4-116">Using the Failover Cluster Manager snap-in, add Node 1 to the existing cluster.</span></span> <span data-ttu-id="886c4-117">자세한 내용은 [장애 조치(failover) 클러스터링을 설치하기 전에](../install/before-installing-failover-clustering.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="886c4-117">For more information, see [Before Installing Failover Clustering](../install/before-installing-failover-clustering.md).</span></span>  
  
6.  <span data-ttu-id="886c4-118">관리자 계정이 모든 클러스터 노드에서 동일한지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="886c4-118">Ensure that the administrator accounts are the same on all cluster nodes.</span></span>  
  
7.  <span data-ttu-id="886c4-119">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 설치 프로그램을 실행하여 FCI에 노드 1을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="886c4-119">Run [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Setup to add Node 1 to the FCI.</span></span> <span data-ttu-id="886c4-120">자세한 내용은 [SQL Server 장애 조치(failover) 클러스터에서 노드 추가 또는 제거&#40;설치 프로그램&#41;](../install/add-or-remove-nodes-in-a-sql-server-failover-cluster-setup.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="886c4-120">For more information, see [Add or Remove Nodes in a SQL Server Failover Cluster &#40;Setup&#41;](../install/add-or-remove-nodes-in-a-sql-server-failover-cluster-setup.md).</span></span>  
  
##  <a name="recover-from-a-reparable-failure"></a><a name="Scenario2"></a><span data-ttu-id="886c4-121">가능 오류 복구</span><span class="sxs-lookup"><span data-stu-id="886c4-121">Recover from a reparable failure</span></span>  
 <span data-ttu-id="886c4-122">복구 가능 오류를 복구하려면 다음 단계를 따르세요.</span><span class="sxs-lookup"><span data-stu-id="886c4-122">Us the following steps to recover from a reparable failure.</span></span> <span data-ttu-id="886c4-123">이 단계에서 오류는 노드 1이 다운되거나 오프라인 상태가 되어 발생하지만 회복할 수 없는 상태는 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="886c4-123">In this case, failure is caused by Node 1 being down or offline but not irretrievably broken.</span></span> <span data-ttu-id="886c4-124">이는 운영 체제의 오류, 하드웨어 오류 또는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인스턴스 자체의 오류에 의해 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="886c4-124">This could be caused by an operating system failure, hardware failure, or failure in the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instance itself.</span></span>  
  
1.  <span data-ttu-id="886c4-125">노드 1에 오류가 발생한 후 FCI에서 노드 2로 장애 조치됩니다.</span><span class="sxs-lookup"><span data-stu-id="886c4-125">After Node 1 fails, the FCI fails over to Node 2.</span></span>  
  
2.  <span data-ttu-id="886c4-126">노드 1의 문제를 해결합니다.</span><span class="sxs-lookup"><span data-stu-id="886c4-126">Resolve the problem with Node 1.</span></span>  
  
3.  <span data-ttu-id="886c4-127">WSFC 서비스가 작동하고 모든 노드가 온라인 상태인지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="886c4-127">Ensure that all nodes are online and the WSFC service is working.</span></span>  
  
4.  <span data-ttu-id="886c4-128">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 를 복구된 노드로 장애 조치합니다.</span><span class="sxs-lookup"><span data-stu-id="886c4-128">Fail over [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] to the recovered node.</span></span>  
  
  
