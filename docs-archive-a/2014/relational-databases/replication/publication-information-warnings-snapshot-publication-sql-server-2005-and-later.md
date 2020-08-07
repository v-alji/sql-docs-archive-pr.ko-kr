---
title: 게시 정보, 경고 (스냅숏 게시, SQL Server 2005 이상) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.monitor.publicationinfo.warningsandagents.snapshot.f1
ms.assetid: 7aa2eb52-b6b7-4dd3-8483-8ef00d9f0435
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: a3ae662a339e1e211ce4f46a588f4d7de65bf5e6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87733912"
---
# <a name="publication-information-warnings-snapshot-publication-sql-server-2005-and-later"></a><span data-ttu-id="2d595-102">게시 정보, 경고(스냅샷 게시, SQL Server 2005 이상)</span><span class="sxs-lookup"><span data-stu-id="2d595-102">Publication Information, Warnings (Snapshot Publication, SQL Server 2005 and Later)</span></span>
  <span data-ttu-id="2d595-103">**경고** 탭은 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 이상 버전을 실행하는 배포자에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2d595-103">The **Warnings** tab is available for Distributors that are running [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] and later versions.</span></span> <span data-ttu-id="2d595-104">**경고** 탭을 사용하면 선택한 게시에 대해 다음 태스크를 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2d595-104">The **Warnings** tab allows you to perform the following tasks for the selected publication:</span></span>  
  
-   <span data-ttu-id="2d595-105">경고 사용</span><span class="sxs-lookup"><span data-stu-id="2d595-105">Enable warnings.</span></span>  
  
-   <span data-ttu-id="2d595-106">경고와 연결된 임계값 지정</span><span class="sxs-lookup"><span data-stu-id="2d595-106">Specify thresholds associated with warnings.</span></span>  
  
-   <span data-ttu-id="2d595-107">경고와 연결된 알림 신호 정의</span><span class="sxs-lookup"><span data-stu-id="2d595-107">Define alerts associated with warnings.</span></span>  
  
## <a name="warnings-thresholds-and-alerts"></a><span data-ttu-id="2d595-108">경고, 임계값 및 알림 신호</span><span class="sxs-lookup"><span data-stu-id="2d595-108">Warnings, Thresholds, and Alerts</span></span>  
 <span data-ttu-id="2d595-109">기본적으로 복제 모니터는 초기화되지 않은 구독에 대해 경고를 표시합니다. **초기화되지 않은 구독** 상태는 구독 정보가 포함된 페이지의 **상태** 열에 경고로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="2d595-109">By default, Replication Monitor displays warnings for uninitialized subscriptions: a status of **Uninitialized subscription** is displayed as a warning in the **Status** column of pages that include subscription information.</span></span> <span data-ttu-id="2d595-110">스냅샷 게시의 경우 **구독이 임계값 내에 만료되는 경우 경고**옵션을 설정하여 구독의 만료가 임박하면 경고를 표시하도록 지정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2d595-110">For snapshot publications, you can also specify that imminent subscription expiration results in a warning by setting the option **Warn if a subscription will expire within the threshold**.</span></span> <span data-ttu-id="2d595-111">지정한 임계값에 도달하거나 이 값을 초과하면 우선 순위가 더 높은 문제가 발생하지 않는 한 구독 상태가 **곧 만료됨/만료됨** 으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="2d595-111">If the specified threshold is met or exceeded, the subscription status is displayed as **Expiring soon/Expired** (unless an issue with a higher priority needs to be displayed).</span></span>  
  
 <span data-ttu-id="2d595-112">임계값에 도달하면 복제 모니터에 경고가 표시되는 것은 물론 알림 신호가 트리거될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2d595-112">In addition to displaying a warning in Replication Monitor, reaching a threshold can also trigger an alert.</span></span> <span data-ttu-id="2d595-113">알림 신호는 **경고 구성** 을 클릭하고 **복제 경고 구성** 대화 상자에서 정보를 제공하여 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="2d595-113">Alerts are defined by clicking **Configure Alerts** and providing information in the **Configure Replication Alerts** dialog box.</span></span>  
  
## <a name="options"></a><span data-ttu-id="2d595-114">옵션</span><span class="sxs-lookup"><span data-stu-id="2d595-114">Options</span></span>  
 <span data-ttu-id="2d595-115">**Enabled**</span><span class="sxs-lookup"><span data-stu-id="2d595-115">**Enabled**</span></span>  
 <span data-ttu-id="2d595-116">경고를 설정하고 임계값을 지정하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="2d595-116">Select to enable a warning and specify a threshold.</span></span>  
  
 <span data-ttu-id="2d595-117">**경고**</span><span class="sxs-lookup"><span data-stu-id="2d595-117">**Warning**</span></span>  
 <span data-ttu-id="2d595-118">임계값과 연결된 경고에 대한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="2d595-118">A description of the warning associated with a threshold.</span></span>  
  
 <span data-ttu-id="2d595-119">**임계값**</span><span class="sxs-lookup"><span data-stu-id="2d595-119">**Threshold**</span></span>  
 <span data-ttu-id="2d595-120">임계값을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2d595-120">Specify a value for the threshold.</span></span>  
  
 <span data-ttu-id="2d595-121">**경고 구성**</span><span class="sxs-lookup"><span data-stu-id="2d595-121">**Configure Alerts**</span></span>  
 <span data-ttu-id="2d595-122">**경고** 표에서 행을 선택하고 **경고 구성** 을 클릭하여 **복제 경고 구성** 대화 상자를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="2d595-122">Select a row in the **Warnings** grid, and click **Configure Alerts** to launch the **Configure Replication Alerts** dialog box.</span></span> <span data-ttu-id="2d595-123">이 대화 상자를 사용하면 선택한 임계값 및 경고와 연결된 알림 메시지를 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2d595-123">The dialog box allows you to define an alert, which is associated with the selected threshold and warning.</span></span>  
  
 <span data-ttu-id="2d595-124">**변경 내용 취소**</span><span class="sxs-lookup"><span data-stu-id="2d595-124">**Discard Changes**</span></span>  
 <span data-ttu-id="2d595-125">경고 및 임계값에 대한 모든 변경 내용을 취소하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2d595-125">Click to discard any changes to warnings and thresholds.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2d595-126">**변경 내용 취소** 를 클릭해도 **복제 경고 구성** 대화 상자에서 정의한 알림 신호에는 적용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2d595-126">Clicking **Discard Changes** does not affect alerts defined in the **Configure Replication Alerts** dialog box.</span></span>  
  
 <span data-ttu-id="2d595-127">**변경 내용 저장**</span><span class="sxs-lookup"><span data-stu-id="2d595-127">**Save Changes**</span></span>  
 <span data-ttu-id="2d595-128">경고 및 임계값에 대한 모든 변경 내용을 저장하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2d595-128">Click to save any changes to warnings and thresholds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d595-129">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2d595-129">See Also</span></span>  
 <span data-ttu-id="2d595-130">[복제 모니터 시작](monitor/start-the-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="2d595-130">[Start the Replication Monitor](monitor/start-the-replication-monitor.md) </span></span>  
 <span data-ttu-id="2d595-131">[복제 모니터를 사용하여 정보 보기 및 태스크 수행](monitor/view-information-and-perform-tasks-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="2d595-131">[View Information and Perform Tasks using Replication Monitor](monitor/view-information-and-perform-tasks-replication-monitor.md) </span></span>  
 [<span data-ttu-id="2d595-132">복제 모니터링</span><span class="sxs-lookup"><span data-stu-id="2d595-132">Monitoring Replication</span></span>](monitoring-replication.md)  
  
  
