---
title: SQL Server 2014 | 제거 Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
ms.assetid: e6255f8e-a25e-4b3d-9310-c5da2f9c9333
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e72f153c28a1ccd827150eb3dddc0b52321518a5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650427"
---
# <a name="uninstall-sql-server-2014"></a><span data-ttu-id="6231f-102">SQL Server 2014 제거</span><span class="sxs-lookup"><span data-stu-id="6231f-102">Uninstall SQL Server 2014</span></span>
  <span data-ttu-id="6231f-103">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 의 기존 인스턴스를 완전히 제거하고 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]를 다시 설치할 수 있도록 시스템을 준비하려면 아래 항목을 따르십시오.</span><span class="sxs-lookup"><span data-stu-id="6231f-103">Follow the topics below to uninstall an existing instance of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] completely, and prepare the system so that you can reinstall [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6231f-104">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="6231f-104">In This Section</span></span>  
 [<span data-ttu-id="6231f-105">SQL Server의 기존 인스턴스 제거&#40;설치 프로그램&#41;</span><span class="sxs-lookup"><span data-stu-id="6231f-105">Uninstall an Existing Instance of SQL Server &#40;Setup&#41;</span></span>](uninstall-an-existing-instance-of-sql-server-setup.md)  
 <span data-ttu-id="6231f-106">이 항목에서는 독립 실행형 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스를 수동으로 제거하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="6231f-106">This topic describes how to manually uninstall a stand-alone instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 [<span data-ttu-id="6231f-107">SharePoint용 PowerPivot 제거</span><span class="sxs-lookup"><span data-stu-id="6231f-107">Uninstall PowerPivot for SharePoint</span></span>](uninstall-power-pivot-for-sharepoint.md)  
 <span data-ttu-id="6231f-108">이 항목에서는 SharePoint용 PowerPivot을 수동으로 제거하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="6231f-108">This topic describes how to manually uninstall PowerPivot for SharePoint.</span></span>  
  
 [<span data-ttu-id="6231f-109">Reporting Services 제거</span><span class="sxs-lookup"><span data-stu-id="6231f-109">Uninstall Reporting Services</span></span>](uninstall-reporting-services.md)  
 <span data-ttu-id="6231f-110">이 항목에서는 SharePoint 모드 및 기본 모드 서버 모두에서 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 서버를 제거하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="6231f-110">This topic describes how to uninstall [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] servers for both SharePoint mode and Native mode servers.</span></span>  
  
 [<span data-ttu-id="6231f-111">Master Data Services 제거</span><span class="sxs-lookup"><span data-stu-id="6231f-111">Uninstall and Remove Master Data Services</span></span>](uninstall-and-remove-master-data-services.md)  
 <span data-ttu-id="6231f-112">이 항목에서는 로컬 컴퓨터에서 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] 를 제거하는 과정에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="6231f-112">This topic describes the process of uninstalling and removing [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] from the local computer.</span></span>  
  
 [<span data-ttu-id="6231f-113">Data Quality 서버 개체 제거</span><span class="sxs-lookup"><span data-stu-id="6231f-113">Remove Data Quality Server Objects</span></span>](remove-data-quality-server-objects.md)  
 <span data-ttu-id="6231f-114">이 항목에서는 [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] 를 제거한 후 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 개체를 수동으로 제거하거나 DQS( [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] )의 [!INCLUDE[ssDQSnoversion](../../includes/ssdqsnoversion-md.md)] 구성 요소만 제거하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="6231f-114">This topic describes how to manually remove the [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] objects after uninstalling either [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] or just the [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] component in [!INCLUDE[ssDQSnoversion](../../includes/ssdqsnoversion-md.md)] (DQS).</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="6231f-115">관련 섹션</span><span class="sxs-lookup"><span data-stu-id="6231f-115">Related Sections</span></span>  
  
-   [<span data-ttu-id="6231f-116">SQL Server 장애 조치(Failover) 클러스터 인스턴스 제거&#40;설치&#41;</span><span class="sxs-lookup"><span data-stu-id="6231f-116">Remove a SQL Server Failover Cluster Instance &#40;Setup&#41;</span></span>](../failover-clusters/install/remove-a-sql-server-failover-cluster-instance-setup.md)  
  
-   [<span data-ttu-id="6231f-117">SQL Server 장애 조치(Failover) 클러스터에서 노드 추가 또는 제거&#40;설치&#41;</span><span class="sxs-lookup"><span data-stu-id="6231f-117">Add or Remove Nodes in a SQL Server Failover Cluster &#40;Setup&#41;</span></span>](../failover-clusters/install/add-or-remove-nodes-in-a-sql-server-failover-cluster-setup.md)  
  
-   [<span data-ttu-id="6231f-118">SQL Server 2014 설치 삭제</span><span class="sxs-lookup"><span data-stu-id="6231f-118">Drop a SQL Server 2014 Installation</span></span>](../../database-engine/install-windows/repair-a-failed-sql-server-installation.md)  
  
## <a name="see-also"></a><span data-ttu-id="6231f-119">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6231f-119">See Also</span></span>  
 <span data-ttu-id="6231f-120">[SQL Server 설치 계획](planning-a-sql-server-installation.md) </span><span class="sxs-lookup"><span data-stu-id="6231f-120">[Planning a SQL Server Installation](planning-a-sql-server-installation.md) </span></span>  
 <span data-ttu-id="6231f-121">[SQL Server 2014 설치](../../database-engine/install-windows/install-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="6231f-121">[Install SQL Server 2014](../../database-engine/install-windows/install-sql-server.md) </span></span>  
 [<span data-ttu-id="6231f-122">SQL Server 2014로 업그레이드</span><span class="sxs-lookup"><span data-stu-id="6231f-122">Upgrade to SQL Server 2014</span></span>](../../database-engine/install-windows/upgrade-sql-server.md)  
  
  
