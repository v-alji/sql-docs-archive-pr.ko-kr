---
title: SQL Server 에이전트, JobSteps 개체 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- JobSteps object
- SQLAgent:JobSteps
ms.assetid: 44f9983c-1753-4fe0-8475-973aa2460b3a
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 3759303807714e2bb7f71f59e644bc485d36cfcb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648337"
---
# <a name="sql-server-agent-jobsteps-object"></a><span data-ttu-id="fe8a7-102">SQL Server 에이전트, JobSteps 개체</span><span class="sxs-lookup"><span data-stu-id="fe8a7-102">SQL Server Agent, JobSteps Object</span></span>
  <span data-ttu-id="fe8a7-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 **JobSteps** 성능 개체에는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 작업 단계에 대한 정보를 보고하는 성능 카운터가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fe8a7-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent **JobSteps** performance object contains performance counters that report information about [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job steps.</span></span> <span data-ttu-id="fe8a7-104">다음 표에서는 이 개체가 포함하는 카운터를 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="fe8a7-104">The table below lists the counters that this object contains.</span></span>  
  
 <span data-ttu-id="fe8a7-105">아래 표에는 **SQLAgent:JobSteps** 카운터가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fe8a7-105">The table below contains the **SQLAgent:JobSteps** counters.</span></span>  
  
|<span data-ttu-id="fe8a7-106">Name</span><span class="sxs-lookup"><span data-stu-id="fe8a7-106">Name</span></span>|<span data-ttu-id="fe8a7-107">Description</span><span class="sxs-lookup"><span data-stu-id="fe8a7-107">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="fe8a7-108">**Active steps**</span><span class="sxs-lookup"><span data-stu-id="fe8a7-108">**Active steps**</span></span>|<span data-ttu-id="fe8a7-109">이 카운터는 현재 실행 중인 작업 단계 수를 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="fe8a7-109">This counter reports the number of job steps currently running.</span></span>|  
|<span data-ttu-id="fe8a7-110">**Queued steps**</span><span class="sxs-lookup"><span data-stu-id="fe8a7-110">**Queued steps**</span></span>|<span data-ttu-id="fe8a7-111">이 카운터는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트가 실행될 준비가 되어 있지만 아직 실행이 시작되지 않은 작업 단계 수를 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="fe8a7-111">This counter reports the number of job steps that are ready for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent to run, but which have not yet started running.</span></span>|  
|<span data-ttu-id="fe8a7-112">**Total step retries**</span><span class="sxs-lookup"><span data-stu-id="fe8a7-112">**Total step retries**</span></span>|<span data-ttu-id="fe8a7-113">이 카운터는 마지막 서버 다시 시작 이후에 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]가 작업 단계를 다시 시도한 총횟수를 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="fe8a7-113">This counter reports the total number of times that [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] has retried a job step since the last server restart.</span></span>|  
  
 <span data-ttu-id="fe8a7-114">개체의 각 카운터는 다음 인스턴스를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="fe8a7-114">Each counter in the object contains the following instances:</span></span>  
  
|<span data-ttu-id="fe8a7-115">인스턴스</span><span class="sxs-lookup"><span data-stu-id="fe8a7-115">Instance</span></span>|<span data-ttu-id="fe8a7-116">Description</span><span class="sxs-lookup"><span data-stu-id="fe8a7-116">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="fe8a7-117">**_Total**</span><span class="sxs-lookup"><span data-stu-id="fe8a7-117">**_Total**</span></span>|<span data-ttu-id="fe8a7-118">모든 작업 단계에 대한 정보입니다.</span><span class="sxs-lookup"><span data-stu-id="fe8a7-118">Information for all job steps.</span></span>|  
|<span data-ttu-id="fe8a7-119">**ActiveScripting**</span><span class="sxs-lookup"><span data-stu-id="fe8a7-119">**ActiveScripting**</span></span>|<span data-ttu-id="fe8a7-120">**ActiveScripting** 하위 시스템을 사용하는 작업 단계에 대한 정보입니다.</span><span class="sxs-lookup"><span data-stu-id="fe8a7-120">Information for job steps that use the **ActiveScripting** subsystem.</span></span>|  
|<span data-ttu-id="fe8a7-121">**ANALYSISCOMMAND**</span><span class="sxs-lookup"><span data-stu-id="fe8a7-121">**ANALYSISCOMMAND**</span></span>|<span data-ttu-id="fe8a7-122">ANALYSISCOMMAND 하위 시스템을 사용하는 작업 단계에 대한 정보입니다.</span><span class="sxs-lookup"><span data-stu-id="fe8a7-122">Information for job steps that use the ANALYSISCOMMAND subsystem.</span></span>|  
|<span data-ttu-id="fe8a7-123">**ANALYSISQUERY**</span><span class="sxs-lookup"><span data-stu-id="fe8a7-123">**ANALYSISQUERY**</span></span>|<span data-ttu-id="fe8a7-124">ANALYSISQUERY 하위 시스템을 사용하는 작업 단계에 대한 정보입니다.</span><span class="sxs-lookup"><span data-stu-id="fe8a7-124">Information for job steps that use the ANALYSISQUERY subsystem.</span></span>|  
|<span data-ttu-id="fe8a7-125">**CmdExec**</span><span class="sxs-lookup"><span data-stu-id="fe8a7-125">**CmdExec**</span></span>|<span data-ttu-id="fe8a7-126">**CmdExec** 하위 시스템을 사용하는 작업 단계에 대한 정보입니다.</span><span class="sxs-lookup"><span data-stu-id="fe8a7-126">Information for job steps that use the **CmdExec** subsystem.</span></span>|  
|<span data-ttu-id="fe8a7-127">**배포**</span><span class="sxs-lookup"><span data-stu-id="fe8a7-127">**Distribution**</span></span>|<span data-ttu-id="fe8a7-128">**Distribution** 하위 시스템을 사용하는 작업 단계에 대한 정보입니다.</span><span class="sxs-lookup"><span data-stu-id="fe8a7-128">Information for job steps that use the **Distribution** subsystem.</span></span>|  
|<span data-ttu-id="fe8a7-129">**Dts**</span><span class="sxs-lookup"><span data-stu-id="fe8a7-129">**Dts**</span></span>|<span data-ttu-id="fe8a7-130">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 하위 시스템을 사용하는 작업 단계에 대한 정보입니다.</span><span class="sxs-lookup"><span data-stu-id="fe8a7-130">Information for job steps that use the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] subsystem.</span></span>|  
|<span data-ttu-id="fe8a7-131">**LogReader**</span><span class="sxs-lookup"><span data-stu-id="fe8a7-131">**LogReader**</span></span>|<span data-ttu-id="fe8a7-132">**LogReader** 하위 시스템을 사용하는 작업 단계에 대한 정보입니다.</span><span class="sxs-lookup"><span data-stu-id="fe8a7-132">Information for job steps that use the **LogReader** subsystem.</span></span>|  
|<span data-ttu-id="fe8a7-133">**병합**</span><span class="sxs-lookup"><span data-stu-id="fe8a7-133">**Merge**</span></span>|<span data-ttu-id="fe8a7-134">**Merge** 하위 시스템을 사용하는 작업 단계에 대한 정보입니다.</span><span class="sxs-lookup"><span data-stu-id="fe8a7-134">Information for job steps that use the **Merge** subsystem.</span></span>|  
|<span data-ttu-id="fe8a7-135">**PowerShell**</span><span class="sxs-lookup"><span data-stu-id="fe8a7-135">**PowerShell**</span></span>|<span data-ttu-id="fe8a7-136">**PowerShell** 하위 시스템을 사용하는 작업 단계에 대한 정보입니다.</span><span class="sxs-lookup"><span data-stu-id="fe8a7-136">Information for job steps that use the **PowerShell** subsystem.</span></span>|  
|<span data-ttu-id="fe8a7-137">**QueueReader**</span><span class="sxs-lookup"><span data-stu-id="fe8a7-137">**QueueReader**</span></span>|<span data-ttu-id="fe8a7-138">**QueueReader** 하위 시스템을 사용하는 작업 단계에 대한 정보입니다.</span><span class="sxs-lookup"><span data-stu-id="fe8a7-138">Information for job steps that use the **QueueReader** subsystem.</span></span>|  
|<span data-ttu-id="fe8a7-139">**스냅샷**</span><span class="sxs-lookup"><span data-stu-id="fe8a7-139">**Snapshot**</span></span>|<span data-ttu-id="fe8a7-140">**Snapshot** 하위 시스템을 사용하는 작업 단계에 대한 정보입니다.</span><span class="sxs-lookup"><span data-stu-id="fe8a7-140">Information for job steps that use the **Snapshot** subsystem.</span></span>|  
|<span data-ttu-id="fe8a7-141">**TSQL**</span><span class="sxs-lookup"><span data-stu-id="fe8a7-141">**TSQL**</span></span>|<span data-ttu-id="fe8a7-142">[!INCLUDE[tsql](../../includes/tsql-md.md)]을 실행하는 작업 단계에 대한 정보입니다.</span><span class="sxs-lookup"><span data-stu-id="fe8a7-142">Information for job steps that execute [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fe8a7-143">참고 항목</span><span class="sxs-lookup"><span data-stu-id="fe8a7-143">See Also</span></span>  
 <span data-ttu-id="fe8a7-144">[작업 단계 관리](../../ssms/agent/manage-job-steps.md) </span><span class="sxs-lookup"><span data-stu-id="fe8a7-144">[Manage Job Steps](../../ssms/agent/manage-job-steps.md) </span></span>  
 <span data-ttu-id="fe8a7-145">[성능 개체 사용](../../ssms/agent/use-performance-objects.md) </span><span class="sxs-lookup"><span data-stu-id="fe8a7-145">[Use Performance Objects](../../ssms/agent/use-performance-objects.md) </span></span>  
 [<span data-ttu-id="fe8a7-146">리소스 사용 모니터링&#40;시스템 모니터&#41;</span><span class="sxs-lookup"><span data-stu-id="fe8a7-146">Monitor Resource Usage &#40;System Monitor&#41;</span></span>](monitor-resource-usage-system-monitor.md)  
  
  
