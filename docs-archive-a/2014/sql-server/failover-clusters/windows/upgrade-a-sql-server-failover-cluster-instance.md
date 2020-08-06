---
title: SQL Server 장애 조치 (Failover) 클러스터 업그레이드 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- upgrading failover clusters
- clusters [SQL Server], upgrading
- failover clustering [SQL Server], upgrading
ms.assetid: daac41fe-7d0b-4f14-84c2-62952ad8cbfa
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ca08e83c362e714f234a60ee358df3bcb03ade93
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650555"
---
# <a name="upgrade-a-sql-server-failover-cluster"></a><span data-ttu-id="b5d4a-102">SQL Server 장애 조치(Failover) 클러스터 업그레이드</span><span class="sxs-lookup"><span data-stu-id="b5d4a-102">Upgrade a SQL Server Failover Cluster</span></span>
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]<span data-ttu-id="b5d4a-103">는 모든 장애 조치(Failover) 클러스터 노드에서 [!INCLUDE[ssDE](../../../includes/ssde-md.md)], [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] 및 [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] 장애 조치(Failover) 클러스터의 [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] 및 [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)]를 개별적으로 업그레이드할 수 있도록 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="b5d4a-103">supports upgrade of the [!INCLUDE[ssDE](../../../includes/ssde-md.md)] and [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] from [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)], [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)], and [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] failover clusters separately on all failover cluster nodes.</span></span>  
  
 <span data-ttu-id="b5d4a-104">자세한 내용은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="b5d4a-104">Support details are as follows:</span></span>  
  
-   <span data-ttu-id="b5d4a-105">업그레이드는 사용자 인터페이스 및 명령 프롬프트를 사용하여 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b5d4a-105">Upgrade is supported both through the user interface and from the command prompt.</span></span> <span data-ttu-id="b5d4a-106">자세한 내용은 [SQL Server 장애 조치(failover) 클러스터 인스턴스 업그레이드&#40;설치 프로그램&#41;](upgrade-a-sql-server-failover-cluster-instance-setup.md) 및 [명령 프롬프트에서 SQL Server 2014 설치](../../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b5d4a-106">For more information, see [Upgrade a SQL Server Failover Cluster Instance &#40;Setup&#41;](upgrade-a-sql-server-failover-cluster-instance-setup.md) and [Install SQL Server 2014 from the Command Prompt](../../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md).</span></span>  
  
-   <span data-ttu-id="b5d4a-107">에서 업그레이드 [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] -각 장애 조치 (failover) 클러스터 노드의 명령 프롬프트에서 업그레이드를 실행 하거나 설치 UI를 사용 하 여 각 클러스터 노드를 업그레이드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b5d4a-107">Upgrading from [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] - You can run upgrade from the command prompt on each failover cluster node, or by using the Setup UI to upgrade each cluster node.</span></span> <span data-ttu-id="b5d4a-108">전체 텍스트 검색 및 복제 기능이 업그레이드 중인 인스턴스에 없는 경우 자동으로 설치되고 이를 생략할 수 있는 옵션은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b5d4a-108">If Full-text search and Replication features do not exist on the instance being upgraded, they will be installed automatically with no option to omit them.</span></span>  
  
-   <span data-ttu-id="b5d4a-109">서비스 팩 설치 - 모든 노드의 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 장애 조치(Failover) 클러스터에 개별적으로 [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] 서비스 팩 및 패치를 적용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b5d4a-109">Service pack installation - you must apply [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] service packs and patches to [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] failover clusters separately on all nodes.</span></span>  
  
-   <span data-ttu-id="b5d4a-110">다음과 같은 시나리오는 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b5d4a-110">The following scenarios are not supported:</span></span>  
  
    -   <span data-ttu-id="b5d4a-111">독립 실행형 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인스턴스를 장애 조치(Failover) 클러스터로 마이그레이션할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b5d4a-111">You cannot migrate from a stand-alone instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] to a failover cluster.</span></span>  
  
    -   <span data-ttu-id="b5d4a-112">장애 조치(Failover) 클러스터에 기능을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="b5d4a-112">Add features to a failover cluster.</span></span> <span data-ttu-id="b5d4a-113">예를 들어 기존의 [!INCLUDE[ssDE](../../../includes/ssde-md.md)] 전용 장애 조치(Failover) 클러스터에 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]을 추가할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b5d4a-113">For example, you cannot add the [!INCLUDE[ssDE](../../../includes/ssde-md.md)] to an existing [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]-only failover cluster.</span></span>  
  
    -   <span data-ttu-id="b5d4a-114">장애 조치(Failover) 클러스터 노드를 독립 실행형 인스턴스로 다운그레이드할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b5d4a-114">You cannot downgrade a failover cluster node to a stand-alone instance.</span></span>  
  
-   <span data-ttu-id="b5d4a-115">자세한 내용은 [Always On 장애 조치(failover) 클러스터 인스턴스(SQL Server)](always-on-failover-cluster-instances-sql-server.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b5d4a-115">For more information, see [AlwaysOn Failover Cluster Instances (SQL Server)](always-on-failover-cluster-instances-sql-server.md).</span></span>  
  
## <a name="upgrading-a-ssnoversion-multi-subnet-failover-cluster"></a><span data-ttu-id="b5d4a-116">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 다중 서브넷 장애 조치(Failover) 클러스터로 업그레이드</span><span class="sxs-lookup"><span data-stu-id="b5d4a-116">Upgrading a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Multi-Subnet Failover Cluster</span></span>  
 <span data-ttu-id="b5d4a-117">다중 서브넷 장애 조치 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (failover) 클러스터를 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 다중 서브넷 장애 조치 (failover) 클러스터로 직접 업그레이드할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b5d4a-117">You cannot directly upgrade a non-multi-subnet [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] failover cluster to a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] multi-subnet failover cluster.</span></span> <span data-ttu-id="b5d4a-118">자세한 내용은 [SQL Server 장애 조치(failover) 클러스터 인스턴스 업그레이드&#40;설치 프로그램&#41;](upgrade-a-sql-server-failover-cluster-instance-setup.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b5d4a-118">For more information, see [Upgrade a SQL Server Failover Cluster Instance &#40;Setup&#41;](upgrade-a-sql-server-failover-cluster-instance-setup.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5d4a-119">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b5d4a-119">See Also</span></span>  
 <span data-ttu-id="b5d4a-120">[지원되는 버전 및 에디션 업그레이드](../../../database-engine/install-windows/supported-version-and-edition-upgrades.md) </span><span class="sxs-lookup"><span data-stu-id="b5d4a-120">[Supported Version and Edition Upgrades](../../../database-engine/install-windows/supported-version-and-edition-upgrades.md) </span></span>  
 <span data-ttu-id="b5d4a-121">[SQL Server 장애 조치 (Failover) 클러스터 인스턴스를 업그레이드 &#40;설정&#41;](upgrade-a-sql-server-failover-cluster-instance-setup.md) </span><span class="sxs-lookup"><span data-stu-id="b5d4a-121">[Upgrade a SQL Server Failover Cluster Instance &#40;Setup&#41;](upgrade-a-sql-server-failover-cluster-instance-setup.md) </span></span>  
 [<span data-ttu-id="b5d4a-122">Install SQL Server 2014 from the Command Prompt</span><span class="sxs-lookup"><span data-stu-id="b5d4a-122">Install SQL Server 2014 from the Command Prompt</span></span>](../../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md)  
  
  
