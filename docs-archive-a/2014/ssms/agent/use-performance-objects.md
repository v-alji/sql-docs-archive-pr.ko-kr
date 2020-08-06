---
title: 성능 개체 사용 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent, monitoring
- SQL Server Agent service, monitoring
- SQL Server Agent service, performance objects
- SQL Server Agent, performance objects
- performance objects [SQL Server Agent]
- monitoring [SQL Server], SQL Server Agent
- monitoring [SQL Server Agent]
- performance counters [SQL Server], SQL Server Agent
- counters [SQL Server], SQL Server Agent
ms.assetid: 830b843a-6b2a-4620-a51b-98358e9fc54b
author: stevestein
ms.author: sstein
ms.openlocfilehash: d7c1fe3f4a7d9a5fec901f84d8e913e49a4dbd1b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652527"
---
# <a name="use-performance-objects"></a><span data-ttu-id="f3bc3-102">성능 개체 사용</span><span class="sxs-lookup"><span data-stu-id="f3bc3-102">Use Performance Objects</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="f3bc3-103">에이전트에는 서비스 수행 방법을 모니터링하는 성능 개체와 카운터가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="f3bc3-103">Agent includes performance objects and counters to monitor how the service is performing.</span></span> <span data-ttu-id="f3bc3-104">이러한 성능 개체를 사용하면 Windows 도구인 성능 모니터를 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 서비스가 백그라운드에서 수행하는 작업을 식별할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f3bc3-104">These performance objects allow you to use Performance Monitor, a Windows tool, to identify what the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service is doing in the background.</span></span> <span data-ttu-id="f3bc3-105">예를 들어 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 서비스가 현재 실행 중인 활성 작업 수를 확인하여 차단된 작업을 식별할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f3bc3-105">For example, you can identify how many active jobs the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service is currently running to identify those jobs that are blocked.</span></span>  
  
 <span data-ttu-id="f3bc3-106">컴퓨터에 설치된 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스마다 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 서비스 성능 개체와 카운터가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f3bc3-106">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service performance objects and counters exist for each instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that is installed on a computer.</span></span> <span data-ttu-id="f3bc3-107">성능 개체는 각 개체가 나타내는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에 따라 이름이 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="f3bc3-107">Performance objects are named according to the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that each object represents.</span></span>  
  
 <span data-ttu-id="f3bc3-108">다음 표에서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 서비스 성능 개체의 이름 지정 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="f3bc3-108">The following table shows how the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service performance objects are named:</span></span>  
  
|<span data-ttu-id="f3bc3-109">인스턴스 유형</span><span class="sxs-lookup"><span data-stu-id="f3bc3-109">Instance type</span></span>|<span data-ttu-id="f3bc3-110">개체 이름</span><span class="sxs-lookup"><span data-stu-id="f3bc3-110">Object name</span></span>|  
|-------------------|-----------------|  
|<span data-ttu-id="f3bc3-111">기본값</span><span class="sxs-lookup"><span data-stu-id="f3bc3-111">Default</span></span>|<span data-ttu-id="f3bc3-112">**SQLAgent:** *object*:*counter*</span><span class="sxs-lookup"><span data-stu-id="f3bc3-112">**SQLAgent:** *object*:*counter*</span></span>|  
|<span data-ttu-id="f3bc3-113">named</span><span class="sxs-lookup"><span data-stu-id="f3bc3-113">Named</span></span>|<span data-ttu-id="f3bc3-114">**SQLAgent$**</span><span class="sxs-lookup"><span data-stu-id="f3bc3-114">**SQLAgent$**</span></span><br /> <span data-ttu-id="f3bc3-115">***instance_name* :** *object*:*카운터*</span><span class="sxs-lookup"><span data-stu-id="f3bc3-115">***instance_name* :** *object*:*counter*</span></span>|  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="f3bc3-116">다음과 같은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 성능 개체가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="f3bc3-116">includes the following performance objects for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.</span></span>  
  
|<span data-ttu-id="f3bc3-117">개체 이름</span><span class="sxs-lookup"><span data-stu-id="f3bc3-117">Object name</span></span>|<span data-ttu-id="f3bc3-118">Description</span><span class="sxs-lookup"><span data-stu-id="f3bc3-118">Description</span></span>|  
|-----------------|-----------------|  
|[<span data-ttu-id="f3bc3-119">SQLAgent:Jobs</span><span class="sxs-lookup"><span data-stu-id="f3bc3-119">SQLAgent:Jobs</span></span>](../../relational-databases/performance-monitor/sql-server-agent-jobs-object.md)|<span data-ttu-id="f3bc3-120">시작된 작업, 성공률 및 현재 상태에 대한 성능 정보</span><span class="sxs-lookup"><span data-stu-id="f3bc3-120">Performance information about jobs that have been started, success rates, and current status</span></span>|  
|[<span data-ttu-id="f3bc3-121">SQLAgent:JobSteps</span><span class="sxs-lookup"><span data-stu-id="f3bc3-121">SQLAgent:JobSteps</span></span>](../../relational-databases/performance-monitor/sql-server-agent-jobsteps-object.md)|<span data-ttu-id="f3bc3-122">작업 단계에 대한 상태 정보</span><span class="sxs-lookup"><span data-stu-id="f3bc3-122">Status information about job steps</span></span>|  
|[<span data-ttu-id="f3bc3-123">SQLAgent:Alerts</span><span class="sxs-lookup"><span data-stu-id="f3bc3-123">SQLAgent:Alerts</span></span>](../../relational-databases/performance-monitor/sql-server-agent-alerts-object.md)|<span data-ttu-id="f3bc3-124">경고 및 알림 수에 대한 정보</span><span class="sxs-lookup"><span data-stu-id="f3bc3-124">Information about number of alerts and notifications</span></span>|  
|[<span data-ttu-id="f3bc3-125">SQLAgent:Statistics</span><span class="sxs-lookup"><span data-stu-id="f3bc3-125">SQLAgent:Statistics</span></span>](../../relational-databases/performance-monitor/sql-server-agent-statistics-object.md)|<span data-ttu-id="f3bc3-126">일반 성능 정보</span><span class="sxs-lookup"><span data-stu-id="f3bc3-126">General performance information</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f3bc3-127">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f3bc3-127">See Also</span></span>  
 <span data-ttu-id="f3bc3-128">[성능 모니터링 및 튜닝](../../relational-databases/performance/monitor-and-tune-for-performance.md) </span><span class="sxs-lookup"><span data-stu-id="f3bc3-128">[Monitor and Tune for Performance](../../relational-databases/performance/monitor-and-tune-for-performance.md) </span></span>  
 [<span data-ttu-id="f3bc3-129">시스템 모니터 시작&#40;Windows&#41;</span><span class="sxs-lookup"><span data-stu-id="f3bc3-129">Start System Monitor &#40;Windows&#41;</span></span>](../../relational-databases/performance/start-system-monitor-windows.md)  
  
  
