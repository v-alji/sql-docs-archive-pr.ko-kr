---
title: 게시 정보, 경고 (병합 게시, SQL Server 2005 이상) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.monitor.publicationinfo.warningsandagents.merge.f1
ms.assetid: 9bef3565-5f13-42ac-8723-ebe55b0c11e6
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 75f58a4cd9bd84791acf7fd9d28147ef3bbd6232
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651652"
---
# <a name="publication-information-warnings-merge-publication-sql-server-2005-and-later"></a><span data-ttu-id="42585-102">게시 정보, 경고(병합 게시, SQL Server 2005 이상)</span><span class="sxs-lookup"><span data-stu-id="42585-102">Publication Information, Warnings (Merge Publication, SQL Server 2005 and Later)</span></span>
  <span data-ttu-id="42585-103">**경고** 탭은 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 이상 버전을 실행하는 배포자에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="42585-103">The **Warnings** tab is available for Distributors that are running [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] and later versions.</span></span> <span data-ttu-id="42585-104">**경고** 탭을 사용하면 선택한 게시에 대해 다음 태스크를 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="42585-104">The **Warnings** tab allows you to perform the following tasks for the selected publication:</span></span>  
  
-   <span data-ttu-id="42585-105">경고 사용</span><span class="sxs-lookup"><span data-stu-id="42585-105">Enable warnings.</span></span>  
  
-   <span data-ttu-id="42585-106">경고와 연결된 임계값 지정</span><span class="sxs-lookup"><span data-stu-id="42585-106">Specify thresholds associated with warnings.</span></span>  
  
-   <span data-ttu-id="42585-107">경고와 연결된 알림 신호 정의</span><span class="sxs-lookup"><span data-stu-id="42585-107">Define alerts associated with warnings.</span></span>  
  
## <a name="warnings-thresholds-and-alerts"></a><span data-ttu-id="42585-108">경고, 임계값 및 알림 신호</span><span class="sxs-lookup"><span data-stu-id="42585-108">Warnings, Thresholds, and Alerts</span></span>  
 <span data-ttu-id="42585-109">기본적으로 복제 모니터는 초기화되지 않은 구독에 대해 경고를 표시합니다. **초기화되지 않은 구독** 상태는 구독 정보가 포함된 페이지의 **상태** 열에 경고로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="42585-109">By default, Replication Monitor displays warnings for uninitialized subscriptions: a status of **Uninitialized subscription** is displayed as a warning in the **Status** column of pages that include subscription information.</span></span> <span data-ttu-id="42585-110">병합 게시의 경우 다음 추가 조건으로 인한 경고 발생 여부를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="42585-110">For merge publications, you can specify whether these additional conditions result in warnings:</span></span>  
  
-   <span data-ttu-id="42585-111">구독 만료가 임박한 경우</span><span class="sxs-lookup"><span data-stu-id="42585-111">Imminent subscription expiration.</span></span>  
  
     <span data-ttu-id="42585-112">이 조건은 **구독이 임계값 내에 만료되는 경우 경고**옵션에 해당합니다.</span><span class="sxs-lookup"><span data-stu-id="42585-112">This corresponds to the option **Warn if a subscription will expire within the threshold**.</span></span> <span data-ttu-id="42585-113">지정한 임계값에 도달하거나 이 값을 초과하면 우선 순위가 더 높은 문제가 발생하지 않는 한 구독 상태가 **곧 만료됨/만료됨** 으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="42585-113">If the specified threshold is met or exceeded, the subscription status is displayed as **Expiring soon/Expired** (unless an issue with a higher priority needs to be displayed).</span></span>  
  
-   <span data-ttu-id="42585-114">지정된 동기화 시간이 초과된 경우</span><span class="sxs-lookup"><span data-stu-id="42585-114">Exceeding the specified synchronization time.</span></span>  
  
     <span data-ttu-id="42585-115">이 조건은 **전화 접속 연결 시 병합 길이가 임계값을 초과하는 경우 경고** 및 **LAN 연결 시 병합 길이가 임계값을 초과하는 경우 경고**옵션에 해당합니다.</span><span class="sxs-lookup"><span data-stu-id="42585-115">This corresponds to the options **Warn if a merge length for dialup connections exceeds the threshold** and **Warn if a merge length for LAN connections exceeds the threshold**.</span></span> <span data-ttu-id="42585-116">두 임계값을 모두 설정할 수 있지만 지정한 동기화 중에는 임계값을 하나만 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="42585-116">Both of these thresholds can be set, but only one is used during a given synchronization.</span></span> <span data-ttu-id="42585-117">병합 에이전트에서는 연결 유형을 기준으로 적절한 임계값을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="42585-117">The Merge Agent applies the appropriate threshold based on the connection type.</span></span>  
  
     <span data-ttu-id="42585-118">지정한 임계값에 도달하거나 이 값을 초과하면 우선 순위가 더 높은 문제가 발생하지 않는 한 구독 상태가 **장기 실행 트랜잭션 병합** 으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="42585-118">If the specified threshold is met or exceeded, the subscription status is displayed as **Long-running merge** (unless an issue with a higher priority needs to be displayed).</span></span>  
  
-   <span data-ttu-id="42585-119">지정된 시간 내에 지정된 수의 행을 처리하지 못한 경우</span><span class="sxs-lookup"><span data-stu-id="42585-119">Falling short of processing the specified number of rows in a given amount of time.</span></span>  
  
     <span data-ttu-id="42585-120">이 조건은 **전화 접속 연결 시 초당 병합된 행이 임계값 미만인 경우 경고** 및 **LAN 연결 시 병합 길이가 임계값을 초과하는 경우 경고**옵션에 해당합니다.</span><span class="sxs-lookup"><span data-stu-id="42585-120">This corresponds to the options **Warn if rows merged per second for dialup connections is less than the threshold** and **Warn if a merge length for LAN connections exceeds the threshold**.</span></span> <span data-ttu-id="42585-121">두 임계값을 모두 설정할 수 있지만 지정한 동기화 중에는 임계값을 하나만 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="42585-121">Both of these thresholds can be set, but only one is used during a given synchronization.</span></span> <span data-ttu-id="42585-122">병합 에이전트에서는 연결 유형을 기준으로 적절한 임계값을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="42585-122">The Merge Agent applies the appropriate threshold based on the connection type.</span></span>  
  
     <span data-ttu-id="42585-123">지정한 임계값에 도달하거나 이 값을 초과하면 우선 순위가 더 높은 문제가 발생하지 않는 한 구독 상태가 **성능 심각** 으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="42585-123">If the specified threshold is met or exceeded, the subscription status is displayed as **Performance critical** (unless an issue with a higher priority needs to be displayed).</span></span>  
  
 <span data-ttu-id="42585-124">경고를 설정할 때는 임계값도 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="42585-124">When you enable a warning, you also set a threshold.</span></span> <span data-ttu-id="42585-125">예를 들어 **LAN 연결 시 병합 길이가 임계값을 초과하는 경우 경고**를 설정한 경우 병합 동기화에 대한 최대 허용 시간을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="42585-125">For example, if you enable the warning **Warn if a merge length for LAN connections exceeds the threshold**, set the maximum allowable length of time for a merge synchronization.</span></span>  
  
 <span data-ttu-id="42585-126">임계값에 도달하면 복제 모니터에 경고가 표시되는 것은 물론 알림 신호가 트리거될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="42585-126">In addition to displaying a warning in Replication Monitor, reaching a threshold can also trigger an alert.</span></span> <span data-ttu-id="42585-127">알림 신호는 **경고 구성** 을 클릭하고 **복제 경고 구성** 대화 상자에서 정보를 제공하여 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="42585-127">Alerts are defined by clicking **Configure Alerts** and providing information in the **Configure Replication Alerts** dialog box.</span></span>  
  
## <a name="options"></a><span data-ttu-id="42585-128">옵션</span><span class="sxs-lookup"><span data-stu-id="42585-128">Options</span></span>  
 <span data-ttu-id="42585-129">**Enabled**</span><span class="sxs-lookup"><span data-stu-id="42585-129">**Enabled**</span></span>  
 <span data-ttu-id="42585-130">경고를 설정하고 임계값을 지정하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="42585-130">Select to enable a warning and specify a threshold.</span></span>  
  
 <span data-ttu-id="42585-131">**경고**</span><span class="sxs-lookup"><span data-stu-id="42585-131">**Alert**</span></span>  
 <span data-ttu-id="42585-132">지정된 복제 경고에 대한 경고 설정을 사용하도록 설정하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="42585-132">Select to enable the alert setting for a given replication warning.</span></span>  
  
 <span data-ttu-id="42585-133">**경고**</span><span class="sxs-lookup"><span data-stu-id="42585-133">**Warning**</span></span>  
 <span data-ttu-id="42585-134">임계값과 연결된 경고에 대한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="42585-134">A description of the warning associated with a threshold.</span></span>  
  
 <span data-ttu-id="42585-135">**임계값**</span><span class="sxs-lookup"><span data-stu-id="42585-135">**Threshold**</span></span>  
 <span data-ttu-id="42585-136">임계값을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="42585-136">Specify a value for the threshold.</span></span>  
  
 <span data-ttu-id="42585-137">**경고 구성**</span><span class="sxs-lookup"><span data-stu-id="42585-137">**Configure Alerts**</span></span>  
 <span data-ttu-id="42585-138">**경고** 표에서 행을 선택하고 **경고 구성** 을 클릭하여 **복제 경고 구성** 대화 상자를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="42585-138">Select a row in the **Warnings** grid, and click **Configure Alerts** to launch the **Configure Replication Alerts** dialog box.</span></span> <span data-ttu-id="42585-139">이 대화 상자를 사용하면 선택한 임계값 및 경고와 연결된 알림 메시지를 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="42585-139">The dialog box allows you to define an alert, which is associated with the selected threshold and warning.</span></span>  
  
 <span data-ttu-id="42585-140">**변경 내용 취소**</span><span class="sxs-lookup"><span data-stu-id="42585-140">**Discard Changes**</span></span>  
 <span data-ttu-id="42585-141">경고 및 임계값에 대한 모든 변경 내용을 취소하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="42585-141">Click to discard any changes to warnings and thresholds.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="42585-142">**변경 내용 취소** 를 클릭해도 **복제 경고 구성** 대화 상자에서 정의한 알림 신호에는 적용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="42585-142">Clicking **Discard Changes** does not affect alerts defined in the **Configure Replication Alerts** dialog box.</span></span>  
  
 <span data-ttu-id="42585-143">**변경 내용 저장**</span><span class="sxs-lookup"><span data-stu-id="42585-143">**Save Changes**</span></span>  
 <span data-ttu-id="42585-144">경고 및 임계값에 대한 모든 변경 내용을 저장하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="42585-144">Click to save any changes to warnings and thresholds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42585-145">참고 항목</span><span class="sxs-lookup"><span data-stu-id="42585-145">See Also</span></span>  
 <span data-ttu-id="42585-146">[복제 모니터 시작](monitor/start-the-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="42585-146">[Start the Replication Monitor](monitor/start-the-replication-monitor.md) </span></span>  
 <span data-ttu-id="42585-147">[복제 모니터를 사용하여 정보 보기 및 태스크 수행](monitor/view-information-and-perform-tasks-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="42585-147">[View Information and Perform Tasks using Replication Monitor](monitor/view-information-and-perform-tasks-replication-monitor.md) </span></span>  
 <span data-ttu-id="42585-148">[복제 모니터를 사용 하 여 성능 모니터링](monitor/monitor-performance-with-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="42585-148">[Monitor Performance with Replication Monitor](monitor/monitor-performance-with-replication-monitor.md) </span></span>  
 <span data-ttu-id="42585-149">[복제 모니터링](monitoring-replication.md) </span><span class="sxs-lookup"><span data-stu-id="42585-149">[Monitoring Replication](monitoring-replication.md) </span></span>  
 [<span data-ttu-id="42585-150">복제 모니터에 임계값 및 경고 설정</span><span class="sxs-lookup"><span data-stu-id="42585-150">Set Thresholds and Warnings in Replication Monitor</span></span>](monitor/set-thresholds-and-warnings-in-replication-monitor.md)  
  
  
