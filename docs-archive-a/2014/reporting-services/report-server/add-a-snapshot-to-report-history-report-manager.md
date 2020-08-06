---
title: 보고서 기록에 스냅샷 추가(보고서 관리자) | Microsoft Docs
ms.prod: sql-server-2014
ms.technology: reporting-services
ms.topic: conceptual
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.reviewer: ''
helpviewer_keywords:
- report history [Reporting Services], adding snapshots
- historical data [Reporting Services]
- snapshots [Reporting Services], adding report snapshots
- adding snapshots to report history
- report snapshots [Reporting Services], adding
ms.custom: ''
ms.date: 06/13/2017
ms.openlocfilehash: 84d4c264ab0b82fca2a34e6356b53113d63e6994
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652623"
---
# <a name="add-a-snapshot-to-report-history-report-manager"></a><span data-ttu-id="c72a6-102">보고서 기록에 스냅샷 추가(보고서 관리자)</span><span class="sxs-lookup"><span data-stu-id="c72a6-102">Add a Snapshot to Report History (Report Manager)</span></span>

<span data-ttu-id="c72a6-103">보고서 기록은 시간에 따라 만든 보고서 스냅샷의 모음입니다.</span><span class="sxs-lookup"><span data-stu-id="c72a6-103">Report history is a collection of report snapshots that you create over time.</span></span> <span data-ttu-id="c72a6-104">보고서 스냅샷은 레이아웃 정보 및 특정 시점에 검색된 쿼리 결과가 들어 있는 보고서입니다.</span><span class="sxs-lookup"><span data-stu-id="c72a6-104">A report snapshot is a report that contains layout information and query results that were retrieved at a specific point in time.</span></span> <span data-ttu-id="c72a6-105">보고서를 선택할 때 최신 쿼리 결과를 얻을 수 있는 요청 시 실행 보고서와 달리 보고서 스냅샷은 예약된 시간에 처리되고 보고서 서버에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="c72a6-105">Unlike on-demand reports, which get up-to-date query results when you select the report, report snapshots are processed on a schedule and then saved to a report server.</span></span> <span data-ttu-id="c72a6-106">표시할 보고서 스냅샷을 선택하면 보고서 서버가 보고서 서버 데이터베이스에서 저장된 보고서를 검색하고 스냅샷이 만들어진 시점에 따른 보고서의 현재 데이터 및 레이아웃을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="c72a6-106">When you select a report snapshot for viewing, the report server retrieves the stored report from the report server database and shows the data and layout that were current for the report at the time the snapshot was created.</span></span>  
  
<span data-ttu-id="c72a6-107">보고서 스냅샷은 특정 렌더링 형식으로 저장되지 않으며</span><span class="sxs-lookup"><span data-stu-id="c72a6-107">Report snapshots are not saved in a particular rendering format.</span></span> <span data-ttu-id="c72a6-108">사용자나 애플리케이션이 보고서 스냅샷을 요청할 때만 HTML과 같은 최종 보기 형식으로 렌더링됩니다.</span><span class="sxs-lookup"><span data-stu-id="c72a6-108">Instead, report snapshots are rendered in a final viewing format (such as HTML) only when a user or an application requests it.</span></span> <span data-ttu-id="c72a6-109">지연된 렌더링은 스냅샷을 이동 가능하게 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c72a6-109">Deferred rendering makes a snapshot portable.</span></span> <span data-ttu-id="c72a6-110">요청 디바이스나 웹 브라우저에 적합한 형식으로 보고서를 렌더링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c72a6-110">The report can be rendered in the correct format for the requesting device or Web browser.</span></span>  
  
## <a name="to-manually-add-snapshots-to-report-history"></a><span data-ttu-id="c72a6-111">보고서 기록에 스냅샷을 수동으로 추가하려면</span><span class="sxs-lookup"><span data-stu-id="c72a6-111">To manually add snapshots to report history</span></span>

1. <span data-ttu-id="c72a6-112">보고서 관리자에서 **내용** 페이지로 이동하고 기록을 보려는 항목을 마우스로 가리킨 다음 드롭다운 화살표를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c72a6-112">In Report Manager, navigate to the **Contents** page, and hover over the item that you want to view history for, and click the drop-down arrow.</span></span>
  
2. <span data-ttu-id="c72a6-113">드롭다운 메뉴에서 **보고서 기록 보기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c72a6-113">In the drop-down menu, click **View Report History**.</span></span>  
  
3. <span data-ttu-id="c72a6-114">**새 스냅샷**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c72a6-114">Click **New Snapshot**.</span></span> <span data-ttu-id="c72a6-115">**실행 날짜** 열에 새 스냅샷이 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="c72a6-115">A new snapshot is created in the **When Run** column.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="c72a6-116">이를 위해 관리자는 보고서 기록을 **수동으로 기록 작성 허용**상태로 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c72a6-116">In order to do this, the report history must be configured by the administrator to **Allow history to be created manually**.</span></span> <span data-ttu-id="c72a6-117">자세한 내용은 [보고서 기록 제한&#40;보고서 관리자&#41;](../reports/limit-report-history-report-manager.md)를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c72a6-117">For more information, see [Limit Report History &#40;Report Manager&#41;](../reports/limit-report-history-report-manager.md).</span></span>

4. <span data-ttu-id="c72a6-118">**적용**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c72a6-118">Click **Apply**.</span></span>

## <a name="to-automatically-add-all-snapshots-to-report-history"></a><span data-ttu-id="c72a6-119">보고서 기록에 모든 스냅샷을 자동으로 추가하려면</span><span class="sxs-lookup"><span data-stu-id="c72a6-119">To automatically add all snapshots to report history</span></span>  
  
1. <span data-ttu-id="c72a6-120">보고서 실행 스냅샷으로 실행하도록 구성된 보고서의 경우 스냅샷이 새로 고쳐질 때마다 보고서 기록에 스냅샷 복사본을 저장하도록 추가 속성을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c72a6-120">For a report that is already configured to run as a report execution snapshot, you can set additional properties to save a copy of the snapshot to report history each time the snapshot is refreshed.</span></span>  
  
2. <span data-ttu-id="c72a6-121">보고서 관리자에서 **내용** 페이지로 이동하고 기록을 보려는 항목을 마우스로 가리킨 다음 드롭다운 화살표를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c72a6-121">In Report Manager, navigate to the **Contents** page, hover over the item that you want to view history for, and click the drop-down arrow.</span></span>  
  
3. <span data-ttu-id="c72a6-122">드롭다운 메뉴에서 **관리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c72a6-122">In the drop-down menu, click **Manage**.</span></span>  
  
4. <span data-ttu-id="c72a6-123">**스냅샷 옵션**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c72a6-123">Click **Snapshot Options**.</span></span>  
  
5. <span data-ttu-id="c72a6-124">**모든 보고서 실행 스냅샷을 기록에 저장**확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c72a6-124">Select the check box for **Store all report execution snapshots in history**.</span></span>  
  
6. <span data-ttu-id="c72a6-125">**적용**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c72a6-125">Click **Apply**.</span></span>  
  
### <a name="to-automatically-add-snapshots-to-report-history-based-on-a-schedule"></a><span data-ttu-id="c72a6-126">일정에 따라 보고서 기록에 스냅샷을 자동으로 추가하려면</span><span class="sxs-lookup"><span data-stu-id="c72a6-126">To automatically add snapshots to report history based on a schedule</span></span>  
  
1. <span data-ttu-id="c72a6-127">보고서 관리자에서 **내용** 페이지로 이동하고 기록을 보려는 항목을 마우스로 가리킨 다음 드롭다운 화살표를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c72a6-127">In Report Manager, navigate to the **Contents** page, and hover over the item that you want to view history for, and click the drop-down arrow.</span></span>  
  
2. <span data-ttu-id="c72a6-128">드롭다운 메뉴에서 **관리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c72a6-128">In the drop-down menu, click **Manage**.</span></span>  
  
3. <span data-ttu-id="c72a6-129">**스냅샷 옵션**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c72a6-129">Click **Snapshot Options**.</span></span>  
  
4. <span data-ttu-id="c72a6-130">**다음 일정을 사용하여 스냅샷을 보고서 기록에 추가**확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c72a6-130">Select the check box for **Use the following schedule to add snapshots to report history**.</span></span> <span data-ttu-id="c72a6-131">다음 중 하나를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="c72a6-131">Perform one of the following:</span></span>  
  
    - <span data-ttu-id="c72a6-132">**보고서별 일정**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c72a6-132">Select **Report-specific schedule**.</span></span> <span data-ttu-id="c72a6-133">일정 정보를 채우고 일정의 시작일과 종료일을 선택한 후 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c72a6-133">Fill in the schedule details, select the start and end dates for the schedule, and then click **OK**.</span></span>  
  
    - <span data-ttu-id="c72a6-134">**공유 일정**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c72a6-134">Select **Shared schedule**.</span></span> <span data-ttu-id="c72a6-135">목록에서 원하는 일정을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c72a6-135">From the list, select the preferred schedule.</span></span>  
  
5. <span data-ttu-id="c72a6-136">**적용**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c72a6-136">Click **Apply**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c72a6-137">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c72a6-137">See Also</span></span>

- [<span data-ttu-id="c72a6-138">보고서에 실행 속성 구성&#40;보고서 관리자&#41;</span><span class="sxs-lookup"><span data-stu-id="c72a6-138">Configure Execution Properties for a Report  &#40;Report Manager&#41;</span></span>](../reports/configure-execution-properties-for-a-report-report-manager.md)
- [<span data-ttu-id="c72a6-139">보고서 열기 및 닫기&#40;보고서 관리자&#41;</span><span class="sxs-lookup"><span data-stu-id="c72a6-139">Open and Close a Report &#40;Report Manager&#41;</span></span>](../reports/open-and-close-a-report-report-manager.md)
- [<span data-ttu-id="c72a6-140">보고서 기록 제한&#40;보고서 관리자&#41;</span><span class="sxs-lookup"><span data-stu-id="c72a6-140">Limit Report History &#40;Report Manager&#41;</span></span>](../reports/limit-report-history-report-manager.md)
- [<span data-ttu-id="c72a6-141">일정</span><span class="sxs-lookup"><span data-stu-id="c72a6-141">Schedules</span></span>](../subscriptions/schedules.md)   
- [<span data-ttu-id="c72a6-142">보고서 관리자&#40;SSRS 기본 모드&#41;</span><span class="sxs-lookup"><span data-stu-id="c72a6-142">Report Manager  &#40;SSRS Native Mode&#41;</span></span>](../report-manager-ssrs-native-mode.md)