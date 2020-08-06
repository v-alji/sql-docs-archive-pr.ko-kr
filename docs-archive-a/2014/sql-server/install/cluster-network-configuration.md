---
title: 클러스터 네트워크 구성 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- cluster network selection, Setup
- cluster network selection
ms.assetid: 579482ef-a023-45b2-9176-b4a4188adf9d
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 17ab563817a3b9b476dfd566f4a7f2beda98ca26
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650496"
---
# <a name="cluster-network-configuration"></a><span data-ttu-id="caaad-102">클러스터 네트워크 구성</span><span class="sxs-lookup"><span data-stu-id="caaad-102">Cluster Network Configuration</span></span>
  <span data-ttu-id="caaad-103">**클러스터 네트워크 선택** 페이지를 사용하여 장애 조치(Failover) 클러스터 인스턴스에 대한 네트워크 리소스를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="caaad-103">Use the **Cluster Network Selection** page to specify the network resources for your failover cluster instance.</span></span>  
  
## <a name="options"></a><span data-ttu-id="caaad-104">옵션</span><span class="sxs-lookup"><span data-stu-id="caaad-104">Options</span></span>  
 <span data-ttu-id="caaad-105">\*\* [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 장애 조치 (Failover) 클러스터 네트워크 이름\*\* -네트워크에서 장애 조치 (failover) 클러스터 인스턴스를 식별 하는 데 사용 되는 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="caaad-105">**[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Failover Cluster Network Name** - This is the name used to identify your failover cluster instance on the network.</span></span>  
  
 <span data-ttu-id="caaad-106">**네트워크 설정** – 장애 조치(Failover) 클러스터 인스턴스의 IP 유형과 IP 주소를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="caaad-106">**Network Settings** - Specify the IP type and IP address for your failover cluster instance.</span></span>  
  
 <span data-ttu-id="caaad-107">노드 추가 및 노드 제거 작업 중에 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 장애 조치(Failover) 클러스터에 대한 기존 IP 주소의 읽기 전용 목록이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="caaad-107">During the Add Node and Remove Node operations, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] displays a read-only list of the existing IP addresses for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] failover cluster.</span></span>  
  
-   <span data-ttu-id="caaad-108">통합 설치:</span><span class="sxs-lookup"><span data-stu-id="caaad-108">Integrated Install:</span></span>  
  
    -   <span data-ttu-id="caaad-109">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 장애 조치(failover) 클러스터의 기존 노드에서 지원하는 것과 동일한 네트워크 서브넷 집합을 지원하는 노드를 추가하는 경우 IP 주소를 더 이상 추가할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="caaad-109">If you are adding a node that supports an identical set of network subnets supported by the existing nodes of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] failover cluster, no additional IP addresses can be added.</span></span> <span data-ttu-id="caaad-110">종속성 설정은 변경되지 않고 그대로 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="caaad-110">The dependency setting remains unchanged.</span></span>  
  
    -   <span data-ttu-id="caaad-111">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 장애 조치(failover) 클러스터의 기존 노드에서 지원되는 서브넷의 하위 집합을 지원하는 노드를 추가하는 경우 IP 주소 리소스를 더 이상 추가할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="caaad-111">If you are adding a node that supports a subset of the subnets supported by the existing nodes on the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] failover cluster, no additional IP address resources can be added.</span></span> <span data-ttu-id="caaad-112">지정된 모든 IP 주소가 모든 클러스터 노드에서 유효하지 않음을 나타내려면 IP 주소 리소스 종속성을 OR로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="caaad-112">The IP address resource dependency is set to OR to reflect that all the specified IP addresses are not valid on all the cluster nodes.</span></span>  
  
    -   <span data-ttu-id="caaad-113">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 장애 조치(failover) 클러스터의 기존 노드에서 이미 지원되는 서브넷 이외의 서브넷을 지원하는 노드를 추가하는 경우 새로운 유효 IP 주소를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="caaad-113">If you are adding a node that supports subnets in addition to the subnets already supported by the existing nodes on the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] failover cluster, you have the option of adding new valid IP addresses.</span></span> <span data-ttu-id="caaad-114">새 IP 주소를 지정하는 경우 지정된 모든 IP 주소가 모든 클러스터 노드에서 유효하지 않음을 나타내려면 IP 주소 리소스 종속성을 OR로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="caaad-114">If new IP addresses are specified, the IP address resource dependency is set to OR to reflect that all the specified IP addresses are not valid on all the cluster nodes.</span></span>  
  
    -   <span data-ttu-id="caaad-115">추가 네트워크 서브넷은 지원하지만 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 장애 조치(failover) 클러스터의 기존 노드에서 지원하는 서브넷은 지원하지 않는 노드를 추가하는 경우 IP 주소를 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="caaad-115">If you are adding a node that supports additional network subnets, but supports none of the subnets supported by the existing nodes on the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] failover cluster, you are required to add additional IP addresses.</span></span> <span data-ttu-id="caaad-116">지정된 모든 IP 주소가 모든 클러스터 노드에서 유효하지 않음을 나타내려면 IP 주소 리소스 종속성을 OR로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="caaad-116">The IP address resource dependency is set to OR to reflect that all the specified IP addresses are not valid on all the cluster nodes.</span></span>  
  
-   <span data-ttu-id="caaad-117">고급 설치: 설치 완료 단계 중에 장애 조치(Failover) 클러스터 인스턴스의 모든 모드와 서브넷에 대한 IP 주소를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="caaad-117">Advanced Install: During the Complete step of the installation, specify the IP address for all the nodes and subnets for your failover cluster instance.</span></span> <span data-ttu-id="caaad-118">다중 서브넷 장애 조치(Failover) 클러스터에 대해 여러 IP 주소를 지정할 수 있지만 IP 주소는 서브넷별로 하나씩만 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="caaad-118">You can specify multiple IP addresses for a multi-subnet failover cluster, but only one IP address per subnet is supported.</span></span> <span data-ttu-id="caaad-119">모든 준비된 노드는 하나 이상의 IP 주소에 대한 소유자여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="caaad-119">Every prepared node should be an owner of at least one IP address.</span></span> <span data-ttu-id="caaad-120">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 장애 조치(Failover) 클러스터에 여러 서브넷이 있는 경우 IP 주소 리소스 종속성을 OR로 설정하라는 메시지가 표시됩니다. 노드 제거:</span><span class="sxs-lookup"><span data-stu-id="caaad-120">If you have multiple subnets in your [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] failover cluster, you are prompted to set the IP address resource dependency to OR.Remove Node:</span></span>  
  
    -   <span data-ttu-id="caaad-121">나머지 IP 주소가 모든 나머지 노드에서 지원되는 경우 IP 주소 리소스 종속성을 AND로 설정하라는 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="caaad-121">If the remaining IP addresses are supported on all the remaining nodes, you are prompted to set the IP address resource dependencyto AND.</span></span>  
  
    -   <span data-ttu-id="caaad-122">나머지 IP 주소가 모든 나머지 노드에서 지원되지 않는 경우 IP 주소 리소스 종속성은 OR로 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="caaad-122">If the remaining IP addresses are not supported on all the remaining nodes, the IP address resource dependency is left as OR.</span></span>  
  
  
