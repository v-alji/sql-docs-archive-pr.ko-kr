---
title: 복제 모니터에 임계값 및 경고 설정 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- alerts [SQL Server replication]
- Merge Agent, thresholds and warnings
- Distribution Agent, thresholds and warnings
- thresholds [SQL Server replication]
- Replication Monitor, thresholds and warnings
- monitoring performance [SQL Server replication], thresholds and warnings
ms.assetid: 3a409c2c-b77e-4001-b81a-1dcd918618ec
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f34878a6398df34e55e6dd3783f2da736bee0959
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741828"
---
# <a name="set-thresholds-and-warnings-in-replication-monitor"></a><span data-ttu-id="f9ae9-102">복제 모니터에 임계값 및 경고 설정</span><span class="sxs-lookup"><span data-stu-id="f9ae9-102">Set Thresholds and Warnings in Replication Monitor</span></span>
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)]<span data-ttu-id="f9ae9-103">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]복제 모니터는 게시 및 구독에 대 한 상태 정보를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="f9ae9-103">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Replication Monitor displays status information for publications and subscriptions.</span></span> <span data-ttu-id="f9ae9-104">기본적으로 복제 모니터는 초기화되지 않은 구독에 대해서만 경고를 표시하지만 다른 조건에 대한 경고를 활성화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f9ae9-104">By default, Replication Monitor displays warnings only for uninitialized subscriptions, but you can enable warnings for other conditions.</span></span> <span data-ttu-id="f9ae9-105">토폴로지에 대한 경고를 활성화하여 상태 및 성능 정보를 적시에 받아보는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="f9ae9-105">It is recommended that you enable warnings for your topology, so that you are informed about status and performance in a timely manner.</span></span>  
  
 <span data-ttu-id="f9ae9-106">경고를 활성화할 때는 임계값을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f9ae9-106">When you enable a warning, you specify a threshold.</span></span> <span data-ttu-id="f9ae9-107">임계값에 도달하거나 임계값이 초과되면 우선 순위가 더 높은 문제점이 표시될 필요가 없는 한 경고가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="f9ae9-107">When that threshold is met or exceeded, a warning is displayed (unless an issue with a higher priority needs to be displayed).</span></span> <span data-ttu-id="f9ae9-108">임계값에 도달하면 복제 모니터에 경고가 표시되는 것은 물론 알림 신호가 트리거될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f9ae9-108">In addition to displaying a warning in Replication Monitor, reaching a threshold can also trigger an alert.</span></span> <span data-ttu-id="f9ae9-109">다음 상황에 대해 경고를 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f9ae9-109">You can enable warnings for the following conditions:</span></span>  
  
-   <span data-ttu-id="f9ae9-110">구독 만료가 임박한 경우</span><span class="sxs-lookup"><span data-stu-id="f9ae9-110">Imminent subscription expiration</span></span>  
  
     <span data-ttu-id="f9ae9-111">모든 복제 유형에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="f9ae9-111">This applies to all types of replication.</span></span> <span data-ttu-id="f9ae9-112">지정한 임계값에 도달하거나 임계값을 초과하면 구독 상태가 **곧 만료됨/만료됨**으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="f9ae9-112">If the specified threshold is met or exceeded, the subscription status is displayed as **Expiring soon/Expired**.</span></span>  
  
-   <span data-ttu-id="f9ae9-113">지정한 대기 시간(게시자에서 트랜잭션이 커밋되는 시점과 구독자에서 해당 트랜잭션이 커밋되는 시점 간의 시간 간격)이 초과된 경우</span><span class="sxs-lookup"><span data-stu-id="f9ae9-113">Exceeding the specified latency (the amount of time that elapses between a transaction being committed at the Publisher and the corresponding transaction being committed at the Subscriber).</span></span>  
  
     <span data-ttu-id="f9ae9-114">이 조건은 트랜잭션 복제에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="f9ae9-114">This applies to transactional replication.</span></span> <span data-ttu-id="f9ae9-115">지정한 임계값에 도달하거나 임계값을 초과하면 구독 상태가 **성능 심각**으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="f9ae9-115">If the specified threshold is met or exceeded, the subscription status is displayed as **Performance critical**.</span></span>  
  
-   <span data-ttu-id="f9ae9-116">지정된 동기화 시간이 초과된 경우</span><span class="sxs-lookup"><span data-stu-id="f9ae9-116">Exceeding the specified synchronization time.</span></span>  
  
     <span data-ttu-id="f9ae9-117">이 조건은 병합 복제에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="f9ae9-117">This applies to merge replication.</span></span> <span data-ttu-id="f9ae9-118">지정한 임계값에 도달하거나 임계값을 초과하면 상태가 **장기 실행 트랜잭션 병합**으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="f9ae9-118">If the specified threshold is met or exceeded, the status is displayed as **Long-running merge**.</span></span> <span data-ttu-id="f9ae9-119">전화 접속과 LAN 연결에 대해 서로 다른 임계값을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f9ae9-119">You can specify different thresholds for dialup and Local Area Network (LAN) connections.</span></span>  
  
-   <span data-ttu-id="f9ae9-120">지정된 시간 내에 지정된 수의 행을 처리하지 못한 경우</span><span class="sxs-lookup"><span data-stu-id="f9ae9-120">Falling short of processing the specified number of rows in a given amount of time.</span></span>  
  
     <span data-ttu-id="f9ae9-121">이 조건은 병합 복제에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="f9ae9-121">This applies to merge replication.</span></span> <span data-ttu-id="f9ae9-122">지정한 임계값에 도달하거나 임계값을 초과하면 상태가 **성능 심각**으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="f9ae9-122">If the specified threshold is met or exceeded, the status is displayed as **Performance critical**.</span></span> <span data-ttu-id="f9ae9-123">전화 접속과 LAN 연결에 대해 서로 다른 임계값을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f9ae9-123">You can specify different thresholds for dialup and LAN connections.</span></span>  
  
 <span data-ttu-id="f9ae9-124">**성능 심각** 및 **장기 실행 트랜잭션 병합** 경고에 대한 자세한 내용은 [복제 모니터로 성능 모니터링](monitor-performance-with-replication-monitor.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f9ae9-124">For more information on the warnings **Performance critical** and **Long-running merge**, see [Monitor Performance with Replication Monitor](monitor-performance-with-replication-monitor.md).</span></span>  
  
 <span data-ttu-id="f9ae9-125">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="f9ae9-125">**In This Topic**</span></span>  
  
-   [<span data-ttu-id="f9ae9-126">트랜잭션 게시에 대한 임계값 및 경고 설정</span><span class="sxs-lookup"><span data-stu-id="f9ae9-126">Set thresholds and warnings for a transactional publication</span></span>](#Transactional)  
  
-   [<span data-ttu-id="f9ae9-127">병합 게시에 대한 임계값 및 경고 설정</span><span class="sxs-lookup"><span data-stu-id="f9ae9-127">Set thresholds and warnings for a merge publication</span></span>](#Merge)  
  
-   [<span data-ttu-id="f9ae9-128">스냅샷 게시에 대한 임계값 및 경고 설정</span><span class="sxs-lookup"><span data-stu-id="f9ae9-128">Set thresholds and warnings for a snapshot publication</span></span>](#Snapshot)  
  
##  <a name="to-set-thresholds-and-warnings-for-a-transactional-publication"></a><a name="Transactional"></a><span data-ttu-id="f9ae9-129">트랜잭션 게시에 대 한 임계값 및 경고를 설정 하려면</span><span class="sxs-lookup"><span data-stu-id="f9ae9-129">To set thresholds and warnings for a transactional publication</span></span>  
  
1.  <span data-ttu-id="f9ae9-130">왼쪽 창에서 게시자 그룹을 확장하고 해당 게시자를 확장한 다음 해당 게시를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f9ae9-130">Expand a Publisher group in the left pane, expand a Publisher, and then click a publication.</span></span>  
  
2.  <span data-ttu-id="f9ae9-131">**경고** 탭을 클릭 합니다. 이 탭의 옵션에 대 한 자세한 정보를 보려면 메뉴 모음에서 **도움말** 을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="f9ae9-131">Click the **Warnings** tab. To view more information about the options on this tab click **Help** on the menu bar.</span></span>  
  
3.  <span data-ttu-id="f9ae9-132">**구독이 임계값 내에 만료되는 경우 경고** 또는 **대기 시간이 임계값을 초과하는 경우 경고**중 해당 확인란을 선택하여 경고를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="f9ae9-132">Enable a warning by selecting the appropriate check box: **Warn if a subscription will expire within the threshold** or **Warn if latency exceeds the threshold**.</span></span>  
  
4.  <span data-ttu-id="f9ae9-133">**임계값** 열에서 경고에 대한 임계값을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="f9ae9-133">Set a threshold for the warnings in the **Threshold** column.</span></span> <span data-ttu-id="f9ae9-134">예를 들어 3단계에서 **대기 시간이 임계값을 초과하는 경우 경고** 를 선택한 경우 **임계값** 열에서 대기 시간에 대해 **60초** 를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f9ae9-134">For example, if you selected **Warn if latency exceeds the threshold** in step 3, you could select a latency of **60 seconds** in the **Threshold** column.</span></span>  
  
5.  <span data-ttu-id="f9ae9-135">**변경 내용 저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f9ae9-135">Click **Save Changes**.</span></span>  
  
#### <a name="to-configure-an-alert-for-a-threshold"></a><span data-ttu-id="f9ae9-136">임계값에 대한 경고를 구성하려면</span><span class="sxs-lookup"><span data-stu-id="f9ae9-136">To configure an alert for a threshold</span></span>  
  
1.  <span data-ttu-id="f9ae9-137">**경고 구성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f9ae9-137">Click **Configure Alerts**.</span></span>  
  
2.  <span data-ttu-id="f9ae9-138">**복제 경고 구성** 대화 상자에서 경고를 선택한 다음 **구성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f9ae9-138">In the **Configure Replication Alerts** dialog box, select an alert, and then click **Configure**.</span></span>  
  
     <span data-ttu-id="f9ae9-139">이 대화 상자에 모니터링 임계값과 관련 없는 경고를 포함하여 모든 게시 유형에 대한 경고가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="f9ae9-139">This dialog box displays alerts for all publication types, including alerts that are not related to monitoring thresholds.</span></span> <span data-ttu-id="f9ae9-140">자세한 내용은 [복제 에이전트 이벤트에 대한 경고 사용](../agents/use-alerts-for-replication-agent-events.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f9ae9-140">For more information, see [Use Alerts for Replication Agent Events](../agents/use-alerts-for-replication-agent-events.md).</span></span>  
  
3.  <span data-ttu-id="f9ae9-141">**\<AlertName> 경고 속성** 대화 상자에서 다음과 같은 옵션을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="f9ae9-141">Set options in the **\<AlertName> alert properties** dialog box:</span></span>  
  
    -   <span data-ttu-id="f9ae9-142">**일반** 페이지에서 **사용**을 클릭하고 경고를 적용할 데이터베이스를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f9ae9-142">On the **General** page, click **Enable**; specify which database the alert should apply to.</span></span>  
  
    -   <span data-ttu-id="f9ae9-143">**응답** 페이지에서 전자 메일의 발송 여부 및/또는 작업의 실행 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f9ae9-143">On the **Response** page, specify whether an e-mail should be sent and/or a job should be executed.</span></span>  
  
    -   <span data-ttu-id="f9ae9-144">**옵션** 페이지에서 응답 텍스트를 사용자 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f9ae9-144">On the **Options** page, customize the text of the response.</span></span>  
  
4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
5.  <span data-ttu-id="f9ae9-145">**닫기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f9ae9-145">Click **Close**.</span></span>  
  
##  <a name="set-thresholds-and-warnings-for-a-merge-publication"></a><a name="Merge"></a><span data-ttu-id="f9ae9-146">병합 게시에 대 한 임계값 및 경고 설정</span><span class="sxs-lookup"><span data-stu-id="f9ae9-146">Set thresholds and warnings for a merge publication</span></span>  
  
1.  <span data-ttu-id="f9ae9-147">왼쪽 창에서 게시자 그룹을 확장하고 해당 게시자를 확장한 다음 해당 게시를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f9ae9-147">Expand a Publisher group in the left pane, expand a Publisher, and then click a publication.</span></span>  
  
2.  <span data-ttu-id="f9ae9-148">**경고** 탭을 클릭 합니다. 이 탭의 옵션에 대 한 자세한 내용을 보려면 메뉴 모음에서 **도움말** 을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="f9ae9-148">Click the **Warnings** tab. To view more information about the options on this tab, click **Help** on the menu bar.</span></span>  
  
3.  <span data-ttu-id="f9ae9-149">다음 중 해당 확인란을 선택하여 경고를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="f9ae9-149">Enable a warning by selecting the appropriate check box:</span></span>  
  
    -   <span data-ttu-id="f9ae9-150">**구독이 임계값 내에 만료되는 경우 경고**</span><span class="sxs-lookup"><span data-stu-id="f9ae9-150">**Warn if a subscription will expire within the threshold**</span></span>  
  
    -   <span data-ttu-id="f9ae9-151">**전화 접속 연결 시 병합 길이가 임계값을 초과하는 경우 경고**</span><span class="sxs-lookup"><span data-stu-id="f9ae9-151">**Warn if a merge length for dialup connections exceeds the threshold**</span></span>  
  
    -   <span data-ttu-id="f9ae9-152">**LAN 연결 시 병합 길이가 임계값을 초과하는 경우 경고**</span><span class="sxs-lookup"><span data-stu-id="f9ae9-152">**Warn if a merge length for LAN connections exceeds the threshold**</span></span>  
  
    -   <span data-ttu-id="f9ae9-153">**LAN 연결 시 초당 병합된 행이 임계값 미만인 경우 경고**</span><span class="sxs-lookup"><span data-stu-id="f9ae9-153">**Warn if rows merged per second for LAN connections is less than the threshold**</span></span>  
  
    -   <span data-ttu-id="f9ae9-154">**전화 접속 연결 시 초당 병합된 행이 임계값 미만인 경우 경고**</span><span class="sxs-lookup"><span data-stu-id="f9ae9-154">**Warn if rows merged per second for dialup connections is less than the threshold**</span></span>  
  
4.  <span data-ttu-id="f9ae9-155">**임계값** 열에 경고 임계값을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="f9ae9-155">Set thresholds for the warnings in the **Threshold** column.</span></span> <span data-ttu-id="f9ae9-156">예를 들어 3단계에서 **전화 접속 연결 시 병합 길이가 임계값을 초과하는 경우 경고** 를 선택한 경우 **임계값** 열에서 **10분** 을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f9ae9-156">For example, if you selected **Warn if a merge length for dialup connections exceeds the threshold** in step 3, you could select a time of **10 minutes** in the **Threshold** column.</span></span>  
  
5.  <span data-ttu-id="f9ae9-157">**변경 내용 저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f9ae9-157">Click **Save Changes**.</span></span>  
  
#### <a name="to-configure-an-alert-for-a-threshold"></a><span data-ttu-id="f9ae9-158">임계값에 대한 경고를 구성하려면</span><span class="sxs-lookup"><span data-stu-id="f9ae9-158">To configure an alert for a threshold</span></span>  
  
1.  <span data-ttu-id="f9ae9-159">**경고 구성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f9ae9-159">Click **Configure Alerts**.</span></span>  
  
2.  <span data-ttu-id="f9ae9-160">**복제 경고 구성** 대화 상자에서 경고를 선택한 다음 **구성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f9ae9-160">In the **Configure Replication Alerts** dialog box, select an alert, and then click **Configure**.</span></span>  
  
     <span data-ttu-id="f9ae9-161">이 대화 상자에 모니터링 임계값과 관련 없는 경고를 포함하여 모든 게시 유형에 대한 경고가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="f9ae9-161">This dialog box displays alerts for all publication types, including alerts that are not related to monitoring thresholds.</span></span>  
  
3.  <span data-ttu-id="f9ae9-162">**\<AlertName> 경고 속성** 대화 상자에서 다음과 같은 옵션을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="f9ae9-162">Set options in the **\<AlertName> alert properties** dialog box:</span></span>  
  
    -   <span data-ttu-id="f9ae9-163">**일반** 페이지에서 **사용**을 클릭하고 경고를 적용할 데이터베이스를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f9ae9-163">On the **General** page, click **Enable**; specify which database the alert should apply to.</span></span>  
  
    -   <span data-ttu-id="f9ae9-164">**응답** 페이지에서 전자 메일의 발송 여부 및/또는 작업의 실행 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f9ae9-164">On the **Response** page, specify whether an e-mail should be sent and/or a job should be executed.</span></span>  
  
    -   <span data-ttu-id="f9ae9-165">**옵션** 페이지에서 응답 텍스트를 사용자 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f9ae9-165">On the **Options** page, customize the text of the response.</span></span>  
  
4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
5.  <span data-ttu-id="f9ae9-166">**닫기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f9ae9-166">Click **Close**.</span></span>  
  
##  <a name="set-thresholds-and-warnings-for-a-snapshot-publication"></a><a name="Snapshot"></a><span data-ttu-id="f9ae9-167">스냅숏 게시에 대 한 임계값 및 경고 설정</span><span class="sxs-lookup"><span data-stu-id="f9ae9-167">Set thresholds and warnings for a snapshot publication</span></span>  
  
1.  <span data-ttu-id="f9ae9-168">왼쪽 창에서 게시자 그룹을 확장하고 해당 게시자를 확장한 다음 해당 게시를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f9ae9-168">Expand a Publisher group in the left pane, expand a Publisher, and then click a publication.</span></span>  
  
2.  <span data-ttu-id="f9ae9-169">**경고** 탭을 클릭 합니다. 이 탭의 옵션에 대 한 자세한 내용을 보려면 최상위 메뉴에서 **도움말** 을 클릭 하십시오.</span><span class="sxs-lookup"><span data-stu-id="f9ae9-169">Click the **Warnings** tab. To view more information about the options on this tab click **Help** on the top menu.</span></span>  
  
3.  <span data-ttu-id="f9ae9-170">**구독이 임계값 내에 만료되는 경우 경고**확인란을 선택하여 경고를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="f9ae9-170">Enable a warning by selecting the check box **Warn if a subscription will expire within the threshold**.</span></span>  
  
4.  <span data-ttu-id="f9ae9-171">**임계값** 열에서 경고에 대한 임계값을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="f9ae9-171">Set a threshold for the warning in the **Threshold** column.</span></span> <span data-ttu-id="f9ae9-172">예를 들어 **임계값** 열에서 **70%** 를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f9ae9-172">For example, you could select a value of **70%** in the **Threshold** column.</span></span>  
  
5.  <span data-ttu-id="f9ae9-173">**변경 내용 저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f9ae9-173">Click **Save Changes**.</span></span>  
  
#### <a name="to-configure-an-alert-for-a-threshold"></a><span data-ttu-id="f9ae9-174">임계값에 대한 경고를 구성하려면</span><span class="sxs-lookup"><span data-stu-id="f9ae9-174">To configure an alert for a threshold</span></span>  
  
1.  <span data-ttu-id="f9ae9-175">**경고 구성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f9ae9-175">Click **Configure Alerts**.</span></span>  
  
2.  <span data-ttu-id="f9ae9-176">**복제 경고 구성** 대화 상자에서 경고를 선택한 다음 **구성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f9ae9-176">In the **Configure Replication Alerts** dialog box, select an alert, and then click **Configure**.</span></span>  
  
     <span data-ttu-id="f9ae9-177">이 대화 상자에 모니터링 임계값과 관련 없는 경고를 포함하여 모든 게시 유형에 대한 경고가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="f9ae9-177">This dialog box displays alerts for all publication types, including alerts that are not related to monitoring thresholds.</span></span> <span data-ttu-id="f9ae9-178">자세한 내용은 [복제 에이전트 이벤트에 대한 경고 사용](../agents/use-alerts-for-replication-agent-events.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f9ae9-178">For more information, see [Use Alerts for Replication Agent Events](../agents/use-alerts-for-replication-agent-events.md).</span></span>  
  
3.  <span data-ttu-id="f9ae9-179">**\<AlertName> 경고 속성** 대화 상자에서 다음과 같은 옵션을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="f9ae9-179">Set options in the **\<AlertName> alert properties** dialog box:</span></span>  
  
    -   <span data-ttu-id="f9ae9-180">**일반** 페이지에서 **사용**을 클릭하고 경고를 적용할 데이터베이스를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f9ae9-180">On the **General** page, click **Enable**; specify which database the alert should apply to.</span></span>  
  
    -   <span data-ttu-id="f9ae9-181">**응답** 페이지에서 전자 메일의 발송 여부 및/또는 작업의 실행 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f9ae9-181">On the **Response** page, specify whether an e-mail should be sent and/or a job should be executed.</span></span>  
  
    -   <span data-ttu-id="f9ae9-182">**옵션** 페이지에서 응답 텍스트를 사용자 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f9ae9-182">On the **Options** page, customize the text of the response.</span></span>  
  
4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
5.  <span data-ttu-id="f9ae9-183">**닫기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f9ae9-183">Click **Close**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9ae9-184">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f9ae9-184">See Also</span></span>  
 [<span data-ttu-id="f9ae9-185">복제 모니터링</span><span class="sxs-lookup"><span data-stu-id="f9ae9-185">Monitoring Replication</span></span>](../monitoring-replication.md)  
  
  
