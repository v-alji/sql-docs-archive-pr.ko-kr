---
title: 게시 정보, 경고 (트랜잭션 게시, SQL Server 2005 이상) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.monitor.publicationinfo.warningsandagents.tran.f1
ms.assetid: 4d4baf1d-d0a1-4d09-bec7-137811f43f09
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: cac7ab0f712fe69d3736985921d70b0ce200d474
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87733871"
---
# <a name="publication-information-warnings-transactional-publication-sql-server-2005-and-later"></a><span data-ttu-id="b4cb3-102">게시 정보, 경고(트랜잭션 게시, SQL Server 2005 이상)</span><span class="sxs-lookup"><span data-stu-id="b4cb3-102">Publication Information, Warnings (Transactional Publication, SQL Server 2005 and Later)</span></span>
  <span data-ttu-id="b4cb3-103">**경고** 탭은 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 이상 버전을 실행하는 배포자에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b4cb3-103">The **Warnings** tab is available for Distributors that are running [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] and later versions.</span></span> <span data-ttu-id="b4cb3-104">**경고** 탭을 사용하면 선택한 게시에 대해 다음 태스크를 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b4cb3-104">The **Warnings** tab allows you to perform the following tasks for the selected publication:</span></span>  
  
-   <span data-ttu-id="b4cb3-105">복제 모니터에 경고를 표시하도록 설정</span><span class="sxs-lookup"><span data-stu-id="b4cb3-105">Enable warnings to be displayed in Replication Monitor.</span></span>  
  
-   <span data-ttu-id="b4cb3-106">경고와 연결된 임계값 지정</span><span class="sxs-lookup"><span data-stu-id="b4cb3-106">Specify thresholds associated with warnings.</span></span>  
  
-   <span data-ttu-id="b4cb3-107">경고와 연결된 알림 신호 정의</span><span class="sxs-lookup"><span data-stu-id="b4cb3-107">Define alerts associated with warnings.</span></span>  
  
## <a name="warnings-thresholds-and-alerts"></a><span data-ttu-id="b4cb3-108">경고, 임계값 및 알림 신호</span><span class="sxs-lookup"><span data-stu-id="b4cb3-108">Warnings, Thresholds, and Alerts</span></span>  
 <span data-ttu-id="b4cb3-109">기본적으로 복제 모니터는 초기화되지 않은 구독에 대해 경고를 표시합니다. **초기화되지 않은 구독** 상태는 구독 정보가 포함된 페이지의 **상태** 열에 경고로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="b4cb3-109">By default, Replication Monitor displays warnings for uninitialized subscriptions: a status of **Uninitialized subscription** is displayed as a warning in the **Status** column of pages that include subscription information.</span></span> <span data-ttu-id="b4cb3-110">트랜잭션 게시의 경우 다음과 같은 추가 조건을 경고로 처리할 것인지 여부를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b4cb3-110">For transactional publications, you can specify whether these additional conditions result in warnings:</span></span>  
  
-   <span data-ttu-id="b4cb3-111">구독 만료가 임박한 경우</span><span class="sxs-lookup"><span data-stu-id="b4cb3-111">Imminent subscription expiration.</span></span>  
  
     <span data-ttu-id="b4cb3-112">이 조건은 **구독이 임계값 내에 만료되는 경우 경고**옵션에 해당합니다.</span><span class="sxs-lookup"><span data-stu-id="b4cb3-112">This corresponds to the option **Warn if a subscription will expire within the threshold**.</span></span> <span data-ttu-id="b4cb3-113">지정한 임계값에 도달하거나 이 값을 초과하면 우선 순위가 더 높은 문제가 발생하지 않는 한 구독 상태가 **곧 만료됨/만료됨** 으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="b4cb3-113">If the specified threshold is met or exceeded, the subscription status is displayed as **Expiring soon/Expired** (unless an issue with a higher priority needs to be displayed).</span></span>  
  
-   <span data-ttu-id="b4cb3-114">지정한 대기 시간,</span><span class="sxs-lookup"><span data-stu-id="b4cb3-114">Exceeding the specified latency.</span></span> <span data-ttu-id="b4cb3-115">즉 게시자에서 트랜잭션이 커밋되는 시점과 구독자에서 해당 트랜잭션이 커밋되는 시점 간의 시간 간격이 초과된 경우</span><span class="sxs-lookup"><span data-stu-id="b4cb3-115">This is the amount of time that elapses between a transaction being committed at the Publisher and the corresponding transaction being committed at the Subscriber.</span></span>  
  
     <span data-ttu-id="b4cb3-116">이 조건은 **대기 시간이 임계값을 초과하는 경우 경고**옵션에 해당합니다.</span><span class="sxs-lookup"><span data-stu-id="b4cb3-116">This corresponds to the option **Warn if latency exceeds the threshold**.</span></span> <span data-ttu-id="b4cb3-117">지정한 임계값에 도달하거나 이 값을 초과하면 우선 순위가 더 높은 문제가 발생하지 않는 한 구독 상태가 **성능 심각** 으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="b4cb3-117">If the specified threshold is met or exceeded, the subscription status is displayed as **Performance critical** (unless an issue with a higher priority needs to be displayed).</span></span> <span data-ttu-id="b4cb3-118">또한 임계값은 구독 정보가 포함된 페이지의 **성능** 열에 표시되는 성능 등급을 제공하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="b4cb3-118">The threshold is also used to provide a performance rating, which is displayed in the **Performance** column of pages that include subscription information.</span></span> <span data-ttu-id="b4cb3-119">성능 등급은 다음 값 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="b4cb3-119">The performance rating is one of the following values:</span></span>  
  
    -   <span data-ttu-id="b4cb3-120">우수</span><span class="sxs-lookup"><span data-stu-id="b4cb3-120">Excellent</span></span>  
  
    -   <span data-ttu-id="b4cb3-121">좋음</span><span class="sxs-lookup"><span data-stu-id="b4cb3-121">Good</span></span>  
  
    -   <span data-ttu-id="b4cb3-122">보통</span><span class="sxs-lookup"><span data-stu-id="b4cb3-122">Fair</span></span>  
  
    -   <span data-ttu-id="b4cb3-123">나쁨</span><span class="sxs-lookup"><span data-stu-id="b4cb3-123">Poor</span></span>  
  
    -   <span data-ttu-id="b4cb3-124">위험</span><span class="sxs-lookup"><span data-stu-id="b4cb3-124">Critical</span></span>  
  
 <span data-ttu-id="b4cb3-125">경고를 설정할 때는 임계값도 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4cb3-125">When you enable a warning, you also set a threshold.</span></span> <span data-ttu-id="b4cb3-126">예를 들어 경고 **대기 시간이 임계값을 초과하는 경우 경고**를 설정하면 게시자에서 커밋 중인 트랜잭션과 구독자에서 커밋 중인 트랜잭션 간에 허용 가능한 시간을 선택해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4cb3-126">For example, if you enable the warning **Warn if latency exceeds the threshold**, select the amount of time allowable between a transaction being committed at the Publisher and the transaction being committed at the Subscriber.</span></span>  
  
 <span data-ttu-id="b4cb3-127">임계값에 도달하면 복제 모니터에 경고가 표시되는 것은 물론 알림 신호가 트리거될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b4cb3-127">In addition to displaying a warning in Replication Monitor, reaching a threshold can also trigger an alert.</span></span> <span data-ttu-id="b4cb3-128">알림 신호는 **경고 구성** 을 클릭하고 **복제 경고 구성** 대화 상자에서 정보를 제공하여 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="b4cb3-128">Alerts are defined by clicking **Configure Alerts** and providing information in the **Configure Replication Alerts** dialog box.</span></span>  
  
## <a name="options"></a><span data-ttu-id="b4cb3-129">옵션</span><span class="sxs-lookup"><span data-stu-id="b4cb3-129">Options</span></span>  
 <span data-ttu-id="b4cb3-130">**Enabled**</span><span class="sxs-lookup"><span data-stu-id="b4cb3-130">**Enabled**</span></span>  
 <span data-ttu-id="b4cb3-131">경고를 설정하고 임계값을 지정하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b4cb3-131">Select to enable a warning and specify a threshold.</span></span>  
  
 <span data-ttu-id="b4cb3-132">**경고**</span><span class="sxs-lookup"><span data-stu-id="b4cb3-132">**Warning**</span></span>  
 <span data-ttu-id="b4cb3-133">임계값과 연결된 경고에 대한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="b4cb3-133">A description of the warning associated with a threshold.</span></span>  
  
 <span data-ttu-id="b4cb3-134">**임계값**</span><span class="sxs-lookup"><span data-stu-id="b4cb3-134">**Threshold**</span></span>  
 <span data-ttu-id="b4cb3-135">임계값을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b4cb3-135">Specify a value for the threshold.</span></span>  
  
 <span data-ttu-id="b4cb3-136">**경고 구성**</span><span class="sxs-lookup"><span data-stu-id="b4cb3-136">**Configure Alerts**</span></span>  
 <span data-ttu-id="b4cb3-137">**경고** 표에서 행을 선택하고 **경고 구성** 을 클릭하여 **복제 경고 구성** 대화 상자를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="b4cb3-137">Select a row in the **Warnings** grid, and click **Configure Alerts** to launch the **Configure Replication Alerts** dialog box.</span></span> <span data-ttu-id="b4cb3-138">이 대화 상자를 사용하면 선택한 임계값 및 경고와 연결된 알림 메시지를 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b4cb3-138">The dialog box allows you to define an alert, which is associated with the selected threshold and warning.</span></span>  
  
 <span data-ttu-id="b4cb3-139">**변경 내용 취소**</span><span class="sxs-lookup"><span data-stu-id="b4cb3-139">**Discard Changes**</span></span>  
 <span data-ttu-id="b4cb3-140">경고 및 임계값에 대한 모든 변경 내용을 취소하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b4cb3-140">Click to discard any changes to warnings and thresholds.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b4cb3-141">**변경 내용 취소** 를 클릭해도 **복제 경고 구성** 대화 상자에서 정의한 알림 신호에는 적용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b4cb3-141">Clicking **Discard Changes** does not affect alerts defined in the **Configure Replication Alerts** dialog box.</span></span>  
  
 <span data-ttu-id="b4cb3-142">**변경 내용 저장**</span><span class="sxs-lookup"><span data-stu-id="b4cb3-142">**Save Changes**</span></span>  
 <span data-ttu-id="b4cb3-143">경고 및 임계값에 대한 모든 변경 내용을 저장하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b4cb3-143">Click to save any changes to warnings and thresholds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4cb3-144">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b4cb3-144">See Also</span></span>  
 <span data-ttu-id="b4cb3-145">[복제 모니터 시작](monitor/start-the-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="b4cb3-145">[Start the Replication Monitor](monitor/start-the-replication-monitor.md) </span></span>  
 <span data-ttu-id="b4cb3-146">[복제 모니터를 사용하여 정보 보기 및 태스크 수행](monitor/view-information-and-perform-tasks-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="b4cb3-146">[View Information and Perform Tasks using Replication Monitor](monitor/view-information-and-perform-tasks-replication-monitor.md) </span></span>  
 <span data-ttu-id="b4cb3-147">[복제 모니터를 사용 하 여 성능 모니터링](monitor/monitor-performance-with-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="b4cb3-147">[Monitor Performance with Replication Monitor](monitor/monitor-performance-with-replication-monitor.md) </span></span>  
 <span data-ttu-id="b4cb3-148">[복제 모니터링](monitoring-replication.md) </span><span class="sxs-lookup"><span data-stu-id="b4cb3-148">[Monitoring Replication](monitoring-replication.md) </span></span>  
 [<span data-ttu-id="b4cb3-149">복제 모니터에 임계값 및 경고 설정</span><span class="sxs-lookup"><span data-stu-id="b4cb3-149">Set Thresholds and Warnings in Replication Monitor</span></span>](monitor/set-thresholds-and-warnings-in-replication-monitor.md)  
  
  
