---
title: 클러스터 노드 구성 (전체) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 64174d54-edee-49b8-9b43-039574bf2ca1
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: cc1f8ce4574580746e20c478b23e40485c3e6ecc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650498"
---
# <a name="cluster-node-configuration-complete"></a><span data-ttu-id="2e73e-102">클러스터 노드 구성(전체)</span><span class="sxs-lookup"><span data-stu-id="2e73e-102">Cluster Node Configuration (Complete)</span></span>
  <span data-ttu-id="2e73e-103">클러스터 노드 구성(전체) 페이지를 사용하여 클러스터링용으로 준비된 기존 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스를 지정할 수 있습니다. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 장애 조치(Failover) 클러스터를 설치하거나 업그레이드하려면 장애 조치(Failover) 클러스터의 각 노드에서 설치 프로그램을 실행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2e73e-103">Use the Cluster Node Configuration (Complete) page to specify an existing instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that has been prepared for clustering.To install or upgrade a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] failover cluster, you must run the Setup program on each node of the failover cluster.</span></span> <span data-ttu-id="2e73e-104">기존의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 장애 조치(Failover) 클러스터에 노드를 추가하려면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 장애 조치(Failover) 클러스터 인스턴스에 추가할 노드에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 설치 프로그램을 실행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2e73e-104">To add a node to an existing [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] failover cluster, you must run [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup on the node that is to be added to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] failover cluster instance.</span></span>  
  
## <a name="options"></a><span data-ttu-id="2e73e-105">옵션</span><span class="sxs-lookup"><span data-stu-id="2e73e-105">Options</span></span>  
 <span data-ttu-id="2e73e-106">드롭다운 상자에서 다음을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="2e73e-106">From the drop-down boxes:</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="2e73e-107">인스턴스 이름- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 장애 조치 (failover) 클러스터에 대 한 인스턴스 이름을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="2e73e-107">instance name - Select the instance name for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] failover cluster.</span></span>  
  
-   <span data-ttu-id="2e73e-108">이 노드의 이름-이 필드는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 설치 프로그램이 실행 되는 컴퓨터 이름으로 미리 채워집니다.</span><span class="sxs-lookup"><span data-stu-id="2e73e-108">Name of this node - This field is pre-populated with the computer name where the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup program is running.</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="2e73e-109">장애 조치 (Failover) 클러스터 네트워크 이름-이 필드는 미리 채워지지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2e73e-109">Failover Cluster Network Name - This field is not pre-populated.</span></span> <span data-ttu-id="2e73e-110">새 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 장애 조치(Failover) 클러스터 인스턴스에 대한 네트워크 이름을 지정하십시오.</span><span class="sxs-lookup"><span data-stu-id="2e73e-110">Specify the network name for the new [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] failover cluster instance.</span></span> <span data-ttu-id="2e73e-111">이 이름은 네트워크에서 장애 조치(Failover) 클러스터 인스턴스를 식별하는 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="2e73e-111">This is the name that identifies the failover cluster instance on the network.</span></span>  
  
  
