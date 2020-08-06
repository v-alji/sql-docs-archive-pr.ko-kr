---
title: SQL Server 모니터 개요 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
f1_keywords:
- sql12.swb.sqlservermonitor.main.f1
helpviewer_keywords:
- SQL Server Monitor [SQL Server]
ms.assetid: 048ae16d-31c3-489a-9f1e-1400a3bacd39
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: ab90186ed493e616e672cfacf881fd61be166f88
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646630"
---
# <a name="sql-server-monitor-overview"></a><span data-ttu-id="2d824-102">SQL Server 모니터 개요</span><span class="sxs-lookup"><span data-stu-id="2d824-102">SQL Server Monitor Overview</span></span>
  <span data-ttu-id="2d824-103">SQL Server 모니터는 모니터링 기능을 수행하지 않지만 이 기능을 수행하는 모듈을 호스팅합니다.</span><span class="sxs-lookup"><span data-stu-id="2d824-103">SQL Server Monitor does not perform monitoring functions, but it hosts modules that do.</span></span> <span data-ttu-id="2d824-104">SQL Server 모니터 모듈에는 복제 모니터와 데이터베이스 미러링 모니터가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2d824-104">The SQL Server Monitor modules include Replication Monitor and Database Mirroring Monitor.</span></span>  
  
 <span data-ttu-id="2d824-105">이러한 모듈 중 하나를 사용하려면 **이동** 메뉴에서 해당 모듈을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="2d824-105">To use one of these modules, select that module on the **Go** menu.</span></span> <span data-ttu-id="2d824-106">현재 선택한 모듈에서 탐색 창과 세부 정보 창의 내용, 세부 정보 창의 사용자 상호 작용, 내용과 상태에 대한 쿼리 등을 소유합니다.</span><span class="sxs-lookup"><span data-stu-id="2d824-106">The currently selected module owns the content of the navigation and detail panes, user interaction in the detail panes, and the queries for content and status.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2d824-107">이러한 모니터에 대한 자세한 내용은 [복제 모니터링](../../relational-databases/replication/monitoring-replication.md) 및 [데이터베이스 미러링 모니터링&#40;SQL Server&#41;](../database-mirroring/database-mirroring-sql-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2d824-107">For more information about these monitors, see [Monitoring Replication](../../relational-databases/replication/monitoring-replication.md) and [Monitoring Database Mirroring &#40;SQL Server&#41;](../database-mirroring/database-mirroring-sql-server.md).</span></span>  
  
## <a name="permissions"></a><span data-ttu-id="2d824-108">사용 권한</span><span class="sxs-lookup"><span data-stu-id="2d824-108">Permissions</span></span>  
  
-   <span data-ttu-id="2d824-109">복제 모니터</span><span class="sxs-lookup"><span data-stu-id="2d824-109">Replication Monitor</span></span>  
  
     <span data-ttu-id="2d824-110">복제를 모니터링하려면 배포자에서 **sysadmin** 고정 서버 역할의 멤버이거나 배포 데이터베이스에서 **replmonitor** 고정 데이터베이스 역할의 멤버여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2d824-110">To monitor replication, you must be a member of the **sysadmin** fixed server role at the Distributor or a member of the **replmonitor** fixed database role in the distribution database.</span></span> <span data-ttu-id="2d824-111">시스템 관리자는 사용자를 **replmonitor** 역할에 추가할 수 있으며 이렇게 하면 해당 사용자가 복제 모니터에서 복제 작업을 볼 수 있습니다. 이때 사용자가 복제를 관리할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2d824-111">A system administrator can add any user to the **replmonitor** role, which allows that user to view replication activity in Replication Monitor; however, the user cannot administer replication.</span></span>  
  
-   <span data-ttu-id="2d824-112">데이터베이스 미러링 모니터</span><span class="sxs-lookup"><span data-stu-id="2d824-112">Database Mirroring Monitor</span></span>  
  
     <span data-ttu-id="2d824-113">데이터베이스 미러링을 모니터링하려면 서버 인스턴스에서 **sysadmin** 고정 서버 역할 또는 **dbm_monitor** 고정 데이터베이스 역할의 멤버여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2d824-113">To monitor database mirroring, you must be a member of either the **sysadmin** fixed server role or the **dbm_monitor** fixed database role on the server instance.</span></span> <span data-ttu-id="2d824-114">파트너 서버 인스턴스 중 하나에서만 **sysadmin** 또는 **dbm_monitor** 의 멤버인 경우 모니터는 해당 파트너에만 연결될 수 있습니다. 즉, 모니터는 다른 파트너에서 정보를 검색할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2d824-114">If you are a member of **sysadmin** or **dbm_monitor** on only one of the partner server instances, the monitor can connect only to that partner; the monitor cannot retrieve information from the other partner.</span></span> <span data-ttu-id="2d824-115">자세한 내용은 [Database Mirroring Monitor Overview](../database-mirroring/database-mirroring-monitor-overview.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2d824-115">For more information, see [Database Mirroring Monitor Overview](../database-mirroring/database-mirroring-monitor-overview.md).</span></span>  
  
## <a name="menu-options"></a><span data-ttu-id="2d824-116">메뉴 옵션</span><span class="sxs-lookup"><span data-stu-id="2d824-116">Menu Options</span></span>  
 <span data-ttu-id="2d824-117">SQL Server 모니터에는 SQL Server 모니터와 관련된 명령을 포함하는 메뉴가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2d824-117">SQL Server Monitor has a menu that contains commands that pertain to SQL Server Monitor.</span></span> <span data-ttu-id="2d824-118">또한 이 메뉴에는 선택한 모듈의 명령이 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2d824-118">This menu may also contain commands from the selected module.</span></span>  
  
 <span data-ttu-id="2d824-119">SQL Server 모니터와 관련된 메뉴 옵션은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="2d824-119">The following menu options pertain to SQL Server Monitor.</span></span>  
  
 <span data-ttu-id="2d824-120">**최근에 사용한 파일**</span><span class="sxs-lookup"><span data-stu-id="2d824-120">**File**</span></span>  
 <span data-ttu-id="2d824-121">이 메뉴는 **종료** 명령을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="2d824-121">This menu contains the **Exit** command.</span></span>  
  
 <span data-ttu-id="2d824-122">**동작**</span><span class="sxs-lookup"><span data-stu-id="2d824-122">**Action**</span></span>  
 <span data-ttu-id="2d824-123">탐색 트리에서 선택한 노드의 상황에 맞는 메뉴를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="2d824-123">Contains the context menu of the node selected in the navigation tree.</span></span>  
  
 <span data-ttu-id="2d824-124">**Go**</span><span class="sxs-lookup"><span data-stu-id="2d824-124">**Go**</span></span>  
 <span data-ttu-id="2d824-125">모니터링 구성 요소의 목록을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="2d824-125">Contains a list of monitoring components:</span></span>  
  
-   <span data-ttu-id="2d824-126">데이터베이스 미러링</span><span class="sxs-lookup"><span data-stu-id="2d824-126">Database Mirroring</span></span>  
  
-   <span data-ttu-id="2d824-127">복제</span><span class="sxs-lookup"><span data-stu-id="2d824-127">Replication</span></span>  
  
 <span data-ttu-id="2d824-128">**SQL Server Management Studio를 사용하여 데이터베이스 미러링을 모니터링하려면**</span><span class="sxs-lookup"><span data-stu-id="2d824-128">**To use SQL Server Management Studio to monitor database mirroring**</span></span>  
  
-   [<span data-ttu-id="2d824-129">데이터베이스 미러링 모니터 시작&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="2d824-129">Start Database Mirroring Monitor &#40;SQL Server Management Studio&#41;</span></span>](../database-mirroring/start-database-mirroring-monitor-sql-server-management-studio.md)  
  
## <a name="see-also"></a><span data-ttu-id="2d824-130">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2d824-130">See Also</span></span>  
 [<span data-ttu-id="2d824-131">데이터베이스 미러링 모니터링&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="2d824-131">Monitoring Database Mirroring &#40;SQL Server&#41;</span></span>](../database-mirroring/database-mirroring-sql-server.md)  
  
  
