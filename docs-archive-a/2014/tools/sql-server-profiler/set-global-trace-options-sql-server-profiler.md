---
title: 전역 추적 옵션 설정 (SQL Server Profiler) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- global trace options [SQL Server]
ms.assetid: 2854608a-c3c7-4eb8-b567-034bfec4b1a9
author: stevestein
ms.author: sstein
ms.openlocfilehash: 2f0809ae11776e1bddf42c189b86f48689ff4859
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646776"
---
# <a name="set-global-trace-options-sql-server-profiler"></a><span data-ttu-id="36933-102">전역 추적 옵션 설정(SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="36933-102">Set Global Trace Options (SQL Server Profiler)</span></span>
  <span data-ttu-id="36933-103">이 항목에서는 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]의 특정 인스턴트로 생성되는 모든 추적에 적용되는 옵션을 설정하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="36933-103">This topic describes how to set options that apply to all traces that are created with a specific instance of [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span>  
  
### <a name="to-set-global-trace-options"></a><span data-ttu-id="36933-104">전역 추적 옵션을 설정하려면</span><span class="sxs-lookup"><span data-stu-id="36933-104">To set global trace options</span></span>  
  
1.  <span data-ttu-id="36933-105">**도구** 메뉴에서 **옵션**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="36933-105">On the **Tools** menu, click **Options**.</span></span>  
  
2.  <span data-ttu-id="36933-106">**일반 옵션**대화 상자에서 **글꼴 선택**을 클릭하여 표시 옵션을 수정한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="36933-106">In the **General Options**dialog box, click **Choose Font**to modify the display options, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="36933-107">필요에 따라 **연결한 후 즉시 추적 시작**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="36933-107">Optionally, select **Start tracing immediately after making connection**.</span></span>  
  
4.  <span data-ttu-id="36933-108">필요에 따라 **공급자 버전 변경 시 추적 정의 업데이트**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="36933-108">Optionally, select **Update trace definition when provider version changes**.</span></span> <span data-ttu-id="36933-109">이 옵션은 사용하는 것이 좋으며 기본적으로 선택되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36933-109">This option is recommended and is selected by default.</span></span> <span data-ttu-id="36933-110">이 옵션을 선택하면 추적 정의가 추적을 수행 중인 현재 버전의 서버로 자동으로 업데이트됩니다.</span><span class="sxs-lookup"><span data-stu-id="36933-110">When this option is selected, the trace definition is automatically updated to the current version of the server where tracing is performed.</span></span>  
  
5.  <span data-ttu-id="36933-111">필요에 따라 서버가 롤오버 파일을 관리하는 방법을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="36933-111">Optionally, specify how the server should manage rollover files:</span></span>  
  
    -   <span data-ttu-id="36933-112">**확인하지 않고 모든 롤오버 파일을 순서대로 로드** 를 선택하면 재생 시 롤오버 파일을 자동으로 로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36933-112">Select **Load all rollover files in sequence without prompting** to automatically load rollover files during replay.</span></span>  
  
    -   <span data-ttu-id="36933-113">**롤오버 파일 로드 전에 확인** 을 선택하면 재생 시 롤오버 파일을 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36933-113">Select **Prompt before loading rollover files** to control rollover files during replay.</span></span>  
  
    -   <span data-ttu-id="36933-114">**다음 롤오버 파일 로드 안 함** 을 선택하면 한 번에 한 개의 파일만 재생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36933-114">Select **Never load subsequent rollover files** to replay only one file at a time.</span></span>  
  
6.  <span data-ttu-id="36933-115">필요에 따라 재생 옵션을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="36933-115">Optionally, set replay options:</span></span>  
  
    -   <span data-ttu-id="36933-116">**기본 재생 스레드 수** 는 재생 중 사용할 프로세서 스레드 수를 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="36933-116">**Default number of replay threads** controls the number of processor threads to use during replay.</span></span> <span data-ttu-id="36933-117">스레드 수가 높을수록 재생이 더 빨리 완료되지만 재생 시 서버 성능이 저하됩니다.</span><span class="sxs-lookup"><span data-stu-id="36933-117">A higher number of threads causes replay to complete faster, but causes server performance to degrade during replay.</span></span> <span data-ttu-id="36933-118">**4**로 설정하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="36933-118">The recommended setting is **4**.</span></span> <span data-ttu-id="36933-119">다음 표에서는 사용 가능한 옵션을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="36933-119">The following table lists the available options:</span></span>  
  
        |<span data-ttu-id="36933-120">값</span><span class="sxs-lookup"><span data-stu-id="36933-120">Value</span></span>|<span data-ttu-id="36933-121">Description</span><span class="sxs-lookup"><span data-stu-id="36933-121">Description</span></span>|  
        |-----------|-----------------|  
        |<span data-ttu-id="36933-122">**2**</span><span class="sxs-lookup"><span data-stu-id="36933-122">**2**</span></span>|<span data-ttu-id="36933-123">최소값.</span><span class="sxs-lookup"><span data-stu-id="36933-123">Minimum value.</span></span> <span data-ttu-id="36933-124">두 스레드를 사용하여 재생합니다.</span><span class="sxs-lookup"><span data-stu-id="36933-124">Use two threads to replay.</span></span>|  
        |<span data-ttu-id="36933-125">**4**</span><span class="sxs-lookup"><span data-stu-id="36933-125">**4**</span></span>|<span data-ttu-id="36933-126">기본값.</span><span class="sxs-lookup"><span data-stu-id="36933-126">Default value.</span></span>|  
        |<span data-ttu-id="36933-127">**255**</span><span class="sxs-lookup"><span data-stu-id="36933-127">**255**</span></span>|<span data-ttu-id="36933-128">최대값.</span><span class="sxs-lookup"><span data-stu-id="36933-128">Maximum value.</span></span> <span data-ttu-id="36933-129">최대값을 설정하면 다른 프로세스 성능이 저하됩니다.</span><span class="sxs-lookup"><span data-stu-id="36933-129">Setting a maximum value will impede performance for other processes.</span></span>|  
  
    -   <span data-ttu-id="36933-130">**기본 상태 모니터 대기 간격(초)** 은 재생 스레드가 다른 프로세스를 차단할 수 있는 최대 시간(초)을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="36933-130">**Default health monitor wait interval (sec)** sets the maximum amount of time that a replay thread can block another process in seconds.</span></span> <span data-ttu-id="36933-131">다음 표에서는 값을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="36933-131">The following table explains the values.</span></span>  
  
        |<span data-ttu-id="36933-132">값</span><span class="sxs-lookup"><span data-stu-id="36933-132">Value</span></span>|<span data-ttu-id="36933-133">Description</span><span class="sxs-lookup"><span data-stu-id="36933-133">Description</span></span>|  
        |-----------|-----------------|  
        |<span data-ttu-id="36933-134">**0**</span><span class="sxs-lookup"><span data-stu-id="36933-134">**0**</span></span>|<span data-ttu-id="36933-135">최소값.</span><span class="sxs-lookup"><span data-stu-id="36933-135">Minimum value.</span></span> <span data-ttu-id="36933-136">**0** 은 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 가 차단 프로세스를 절대로 중지하지 않음을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="36933-136">A setting of **0** means that [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] will never stop a blocking process.</span></span>|  
        |<span data-ttu-id="36933-137">**3600**</span><span class="sxs-lookup"><span data-stu-id="36933-137">**3600**</span></span>|<span data-ttu-id="36933-138">기본값.</span><span class="sxs-lookup"><span data-stu-id="36933-138">Default value.</span></span> <span data-ttu-id="36933-139">**3600** 초 또는 한 시간을 초과하지 않는 차단 프로세스를 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="36933-139">Allow blocking processes that do not exceed **3600** seconds, or one hour.</span></span>|  
        |<span data-ttu-id="36933-140">**86400**</span><span class="sxs-lookup"><span data-stu-id="36933-140">**86400**</span></span>|<span data-ttu-id="36933-141">최대값.</span><span class="sxs-lookup"><span data-stu-id="36933-141">Maximum value.</span></span> <span data-ttu-id="36933-142">**86400** 초 또는 하루를 초과하지 않는 차단 프로세스를 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="36933-142">Allow blocking processes that do not exceed **86400** seconds, or one day.</span></span>|  
  
    -   <span data-ttu-id="36933-143">**기본 상태 모니터 폴링 간격(초)** 은 차단 프로세스용 재생 스레드를 폴링하는 빈도를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="36933-143">**Default health monitor poll interval (sec)** sets the frequency to poll replay threads for blocking processes.</span></span> <span data-ttu-id="36933-144">다음 표에서는 값을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="36933-144">The following table explains the values.</span></span>  
  
        |<span data-ttu-id="36933-145">값</span><span class="sxs-lookup"><span data-stu-id="36933-145">Value</span></span>|<span data-ttu-id="36933-146">Description</span><span class="sxs-lookup"><span data-stu-id="36933-146">Description</span></span>|  
        |-----------|-----------------|  
        |<span data-ttu-id="36933-147">**1**</span><span class="sxs-lookup"><span data-stu-id="36933-147">**1**</span></span>|<span data-ttu-id="36933-148">최소값.</span><span class="sxs-lookup"><span data-stu-id="36933-148">Minimum value.</span></span> <span data-ttu-id="36933-149">**1** 은 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 가 차단 프로세스를 초당 하나만 폴링함을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="36933-149">A setting of **1** means [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] will poll for blocking processes once per second.</span></span>|  
        |<span data-ttu-id="36933-150">**60**</span><span class="sxs-lookup"><span data-stu-id="36933-150">**60**</span></span>|<span data-ttu-id="36933-151">기본값.</span><span class="sxs-lookup"><span data-stu-id="36933-151">Default value.</span></span> <span data-ttu-id="36933-152">차단 프로세스를 _분당 하나만 폴링합니다.</span><span class="sxs-lookup"><span data-stu-id="36933-152">Poll for blocking processes once per minute.</span></span>|  
        |<span data-ttu-id="36933-153">**86400**</span><span class="sxs-lookup"><span data-stu-id="36933-153">**86400**</span></span>|<span data-ttu-id="36933-154">최대값.</span><span class="sxs-lookup"><span data-stu-id="36933-154">Maximum value.</span></span> <span data-ttu-id="36933-155">차단 프로세스를 **86400** 초당 또는 하루에 하나만 폴링합니다.</span><span class="sxs-lookup"><span data-stu-id="36933-155">Poll for blocking processes once per **86400** seconds, or one day.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="36933-156">참고 항목</span><span class="sxs-lookup"><span data-stu-id="36933-156">See Also</span></span>  
 <span data-ttu-id="36933-157">[추적 표시 기본값 설정&#40;SQL Server Profiler&#41;](sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="36933-157">[Set Trace Display Defaults &#40;SQL Server Profiler&#41;](sql-server-profiler.md) </span></span>  
 [<span data-ttu-id="36933-158">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="36933-158">SQL Server Profiler</span></span>](sql-server-profiler.md)  
  
  
