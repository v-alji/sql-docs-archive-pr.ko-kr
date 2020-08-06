---
title: 작업 모니터 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Activity Monitor [SQL Server]
ms.assetid: 1e6c430d-3a2a-468e-a3d5-ef5459c36c15
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 71fd0d1172b4fcd5739a3af1a60246cc7dce3b93
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739759"
---
# <a name="activity-monitor"></a><span data-ttu-id="c2aa1-102">작업 모니터</span><span class="sxs-lookup"><span data-stu-id="c2aa1-102">Activity Monitor</span></span>
  <span data-ttu-id="c2aa1-103">작업 모니터는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 프로세스와 이러한 프로세스가 현재 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스에 미치는 영향에 대한 정보를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="c2aa1-103">Activity Monitor displays information about [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] processes and how these processes affect the current instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="benefits-of-activity-monitor"></a><span data-ttu-id="c2aa1-104">작업 모니터의 이점</span><span class="sxs-lookup"><span data-stu-id="c2aa1-104">Benefits of Activity Monitor</span></span>  
 <span data-ttu-id="c2aa1-105">작업 모니터는 **개요**, **활성 사용자 태스크**, **리소스 대기**, **데이터 파일 I/O**및 **비용이 드는 최근 쿼리**와 같은 확장 및 축소 가능한 창이 있는 탭 문서 창입니다.</span><span class="sxs-lookup"><span data-stu-id="c2aa1-105">Activity Monitor is a tabbed document window that has the following expandable and collapsible panes: **Overview**, **Active User Tasks**, **Resource Waits**, **Data File I/O**, and **Recent Expensive Queries**.</span></span> <span data-ttu-id="c2aa1-106">창을 확장하면 작업 모니터는 인스턴스에서 정보를 쿼리합니다.</span><span class="sxs-lookup"><span data-stu-id="c2aa1-106">When any pane is expanded, Activity Monitor queries the instance for information.</span></span> <span data-ttu-id="c2aa1-107">창을 축소하면 해당 창에 대한 모든 쿼리 작업이 중지됩니다.</span><span class="sxs-lookup"><span data-stu-id="c2aa1-107">When a pane is collapsed, all querying activity stops for that pane.</span></span> <span data-ttu-id="c2aa1-108">또한 하나 이상의 창을 동시에 확장하여 인스턴스에 대한 여러 종류의 작업을 볼 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c2aa1-108">You can also expand one or more panes at the same time to view different kinds of activity on the instance.</span></span>  
  
 <span data-ttu-id="c2aa1-109">**활성 사용자 태스크**, **리소스 대기**, **데이터 파일 I/O**및 **비용이 드는 최근 쿼리** 창에 포함된 열의 경우 다음과 같은 방법으로 표시를 사용자 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c2aa1-109">For the columns that are included in the **Active User Tasks**, **Resource Waits**, **Data File I/O**, and **Recent Expensive Queries** panes, you can customize the display in the following ways:</span></span>  
  
1.  <span data-ttu-id="c2aa1-110">열 순서를 다시 정렬하려면 열 머리글을 클릭한 다음 머리글 리본의 다른 위치로 끕니다.</span><span class="sxs-lookup"><span data-stu-id="c2aa1-110">To rearrange the order of the columns, click the column heading and drag it to another location in the heading ribbon.</span></span>  
  
2.  <span data-ttu-id="c2aa1-111">열을 정렬하려면 열 이름을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c2aa1-111">To sort a column, click the column name.</span></span>  
  
3.  <span data-ttu-id="c2aa1-112">하나 이상의 열을 필터링하려면 열 머리글에 있는 드롭다운 화살표를 클릭한 다음 값을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c2aa1-112">To filter on one or more columns, click the drop-down arrow in the column heading, and then select a value.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="c2aa1-113">관련 작업</span><span class="sxs-lookup"><span data-stu-id="c2aa1-113">Related Tasks</span></span>  
 <span data-ttu-id="c2aa1-114">다음 태스크를 사용하여 작업 모니터를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="c2aa1-114">Use the following tasks to get started with Activity Monitor:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c2aa1-115">**설명**</span><span class="sxs-lookup"><span data-stu-id="c2aa1-115">**Description**</span></span>|<span data-ttu-id="c2aa1-116">**항목**</span><span class="sxs-lookup"><span data-stu-id="c2aa1-116">**Topic**</span></span>|  
|<span data-ttu-id="c2aa1-117">작업 모니터를 여는 방법 및 작업 모니터 새로 고침 간격을 설정하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="c2aa1-117">Describes how to open Activity Monitor and how to set the Activity Monitor refresh interval.</span></span>|[<span data-ttu-id="c2aa1-118">작업 모니터 열기&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="c2aa1-118">Open Activity Monitor &#40;SQL Server Management Studio&#41;</span></span>](../performance-monitor/open-activity-monitor-sql-server-management-studio.md)|  
|<span data-ttu-id="c2aa1-119">서버 성능 및 작업 모니터링 관련 항목을 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="c2aa1-119">Links to topics for server performance and activity monitoring.</span></span>|[<span data-ttu-id="c2aa1-120">서버 성능 및 작업 모니터링</span><span class="sxs-lookup"><span data-stu-id="c2aa1-120">Server Performance and Activity Monitoring</span></span>](../performance/server-performance-and-activity-monitoring.md)|  
  
  
