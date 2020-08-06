---
title: SQL Server 에이전트, Jobs 개체 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- SQLAgent:Jobs
- Jobs object
ms.assetid: 225b5e2d-4a78-4178-b2b6-b419df83c4aa
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 82ee57eba20d44c08eadc125e9dfd69e73c35751
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648338"
---
# <a name="sql-server-agent-jobs-object"></a><span data-ttu-id="3b0f4-102">SQL Server 에이전트, Jobs 개체</span><span class="sxs-lookup"><span data-stu-id="3b0f4-102">SQL Server Agent, Jobs Object</span></span>
  <span data-ttu-id="3b0f4-103">SQL Server 에이전트 **Jobs** 성능 개체에는 SQL Server 에이전트 작업에 관한 정보를 보고하는 성능 카운터가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3b0f4-103">The SQL Server Agent **Jobs** performance object contains performance counters that report information about SQL Server Agent jobs.</span></span> <span data-ttu-id="3b0f4-104">다음 표에서는 이 개체가 포함하는 카운터를 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="3b0f4-104">The table below lists the counters that this object contains.</span></span>  
  
 <span data-ttu-id="3b0f4-105">이 표에는 **SQLAgent:Jobs** 카운터가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3b0f4-105">The table below contains the **SQLAgent:Jobs** counters.</span></span>  
  
|<span data-ttu-id="3b0f4-106">Name</span><span class="sxs-lookup"><span data-stu-id="3b0f4-106">Name</span></span>|<span data-ttu-id="3b0f4-107">Description</span><span class="sxs-lookup"><span data-stu-id="3b0f4-107">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="3b0f4-108">**Active Jobs**</span><span class="sxs-lookup"><span data-stu-id="3b0f4-108">**Active Jobs**</span></span>|<span data-ttu-id="3b0f4-109">이 카운터는 현재 실행 중인 작업의 수를 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="3b0f4-109">This counter reports the number of jobs currently running.</span></span>|  
|<span data-ttu-id="3b0f4-110">**Failed jobs**</span><span class="sxs-lookup"><span data-stu-id="3b0f4-110">**Failed jobs**</span></span>|<span data-ttu-id="3b0f4-111">이 카운터는 오류 발생으로 종료된 작업의 수를 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="3b0f4-111">This counter reports the number of jobs that exited with failure.</span></span>|  
|<span data-ttu-id="3b0f4-112">**Job success rate**</span><span class="sxs-lookup"><span data-stu-id="3b0f4-112">**Job success rate**</span></span>|<span data-ttu-id="3b0f4-113">이 카운터는 성공적으로 완료된 실행 작업의 비율을 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="3b0f4-113">This counter reports the percentage of executed jobs that completed successfully.</span></span>|  
|<span data-ttu-id="3b0f4-114">**Jobs activated/minute**</span><span class="sxs-lookup"><span data-stu-id="3b0f4-114">**Jobs activated/minute**</span></span>|<span data-ttu-id="3b0f4-115">이 카운터는 마지막 1분간 실행된 작업의 수를 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="3b0f4-115">This counter reports the number of jobs launched within the last minute.</span></span>|  
|<span data-ttu-id="3b0f4-116">**Queued jobs**</span><span class="sxs-lookup"><span data-stu-id="3b0f4-116">**Queued jobs**</span></span>|<span data-ttu-id="3b0f4-117">이 카운터는 SQL Server 에이전트에서 실행할 준비가 완료되었지만 아직 실행되지 않은 작업의 수를 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="3b0f4-117">This counter reports the number of jobs that are ready for SQL Server Agent to run, but which have not yet started running.</span></span>|  
|<span data-ttu-id="3b0f4-118">**Successful jobs**</span><span class="sxs-lookup"><span data-stu-id="3b0f4-118">**Successful jobs**</span></span>|<span data-ttu-id="3b0f4-119">이 카운터는 성공적으로 종료된 작업의 수를 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="3b0f4-119">This counter reports the number of jobs that exited with success.</span></span>|  
  
 <span data-ttu-id="3b0f4-120">개체의 각 카운터는 다음 인스턴스를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="3b0f4-120">Each counter in the object contains the following instances:</span></span>  
  
|<span data-ttu-id="3b0f4-121">인스턴스</span><span class="sxs-lookup"><span data-stu-id="3b0f4-121">Instance</span></span>|<span data-ttu-id="3b0f4-122">Description</span><span class="sxs-lookup"><span data-stu-id="3b0f4-122">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="3b0f4-123">**_Total**</span><span class="sxs-lookup"><span data-stu-id="3b0f4-123">**_Total**</span></span>|<span data-ttu-id="3b0f4-124">모든 작업에 대한 정보입니다.</span><span class="sxs-lookup"><span data-stu-id="3b0f4-124">Information for all jobs.</span></span>|  
|<span data-ttu-id="3b0f4-125">**경고**</span><span class="sxs-lookup"><span data-stu-id="3b0f4-125">**Alerts**</span></span>|<span data-ttu-id="3b0f4-126">경고에 의해 시작된 작업의 정보입니다.</span><span class="sxs-lookup"><span data-stu-id="3b0f4-126">Information for jobs started by alerts.</span></span>|  
|<span data-ttu-id="3b0f4-127">**Others**</span><span class="sxs-lookup"><span data-stu-id="3b0f4-127">**Others**</span></span>|<span data-ttu-id="3b0f4-128">경고나 일정에 의해 시작되지 않은 작업의 정보입니다.</span><span class="sxs-lookup"><span data-stu-id="3b0f4-128">Information for jobs that were not started by alerts or schedules.</span></span> <span data-ttu-id="3b0f4-129">대개 이런 작업은 **sp_start_job**을 사용하여 수동으로 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="3b0f4-129">Typically these are jobs started manually using **sp_start_job**.</span></span>|  
|<span data-ttu-id="3b0f4-130">**일정**</span><span class="sxs-lookup"><span data-stu-id="3b0f4-130">**Schedules**</span></span>|<span data-ttu-id="3b0f4-131">일정에 의해 시작된 작업의 정보입니다.</span><span class="sxs-lookup"><span data-stu-id="3b0f4-131">Information for jobs started by schedules.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3b0f4-132">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3b0f4-132">See Also</span></span>  
 <span data-ttu-id="3b0f4-133">[작업 구현](../../ssms/agent/implement-jobs.md) </span><span class="sxs-lookup"><span data-stu-id="3b0f4-133">[Implement Jobs](../../ssms/agent/implement-jobs.md) </span></span>  
 <span data-ttu-id="3b0f4-134">[성능 개체 사용](../../ssms/agent/use-performance-objects.md) </span><span class="sxs-lookup"><span data-stu-id="3b0f4-134">[Use Performance Objects](../../ssms/agent/use-performance-objects.md) </span></span>  
 [<span data-ttu-id="3b0f4-135">리소스 사용 모니터링&#40;시스템 모니터&#41;</span><span class="sxs-lookup"><span data-stu-id="3b0f4-135">Monitor Resource Usage &#40;System Monitor&#41;</span></span>](monitor-resource-usage-system-monitor.md)  
  
  
