---
title: '새 일정: 일정 편집 페이지 (보고서 관리자) | Microsoft Docs'
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 52a4d250-e185-4116-a29c-d809940a00fb
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 701c1729eac1c2cf683c966dca58f47b88a2dd32
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738020"
---
# <a name="new-schedule-edit-schedule-page-report-manager"></a><span data-ttu-id="ece8b-102">새 일정: 일정 편집 페이지 (보고서 관리자)</span><span class="sxs-lookup"><span data-stu-id="ece8b-102">New Schedule: Edit Schedule Page (Report Manager)</span></span>
  <span data-ttu-id="ece8b-103">새 일정/일정 편집 페이지를 사용하여 보고서에 대한 일정을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ece8b-103">Use the New Schedule / Edit Schedule page to create a schedule for a report.</span></span> <span data-ttu-id="ece8b-104">일정은 캐시된 보고서를 새로 고치고 보고서 기록에 또는 독립 실행 항목으로 스냅샷을 만들기 위해 구독에서 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="ece8b-104">Schedules are used with subscriptions, to refresh cached reports, and to create snapshots as standalone items or in report history.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ece8b-105">이 기능은 일부 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]버전에서는 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ece8b-105">This feature is not available in every edition of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="ece8b-106">버전에서 지원 되는 기능 목록은 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [SQL Server 2014 버전에서 지 원하는 기능](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ece8b-106">For a list of features that are supported by the editions of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], see [Features Supported by the Editions of SQL Server 2014](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span>  
  
 <span data-ttu-id="ece8b-107">무인 모드로 실행될 수 있는 보고서에 대해서만 일정을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ece8b-107">You can create schedules only for reports that can run unattended.</span></span> <span data-ttu-id="ece8b-108">보고서를 무인 모드로 실행하려면 보고서 서버 데이터베이스에 보고서 데이터 원본 자격 증명을 저장해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ece8b-108">Running a report unattended requires that you store report data source credentials in the report server database.</span></span> <span data-ttu-id="ece8b-109">자세한 내용은 [데이터 원본 속성 페이지 &#40;보고서 관리자&#41;](../../2014/reporting-services/data-sources-properties-page-report-manager.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ece8b-109">For more information, see [Data Sources Properties Page &#40;Report Manager&#41;](../../2014/reporting-services/data-sources-properties-page-report-manager.md).</span></span>  
  
 <span data-ttu-id="ece8b-110">일부 빈도 조합은 단일 일정으로 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ece8b-110">Not all frequency combinations can be supported in a single schedule.</span></span> <span data-ttu-id="ece8b-111">예를 들어 매주 금요일 오후 12시와</span><span class="sxs-lookup"><span data-stu-id="ece8b-111">For example, if you want to run a report at 12:00 P.M.</span></span> <span data-ttu-id="ece8b-112">4시에</span><span class="sxs-lookup"><span data-stu-id="ece8b-112">and 4:00 P.M.</span></span> <span data-ttu-id="ece8b-113">보고서를 실행하려면 실행 날짜가 금요일, 시작 시간이 오후 12시와</span><span class="sxs-lookup"><span data-stu-id="ece8b-113">every Friday, you must create two daily schedules that specify a Friday run date, one with a start time of 12:00 P.M.</span></span> <span data-ttu-id="ece8b-114">4시로 지정된 두 개의 일별 일정을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ece8b-114">and another with a start time of 4:00 P.M.</span></span>  
  
 <span data-ttu-id="ece8b-115">일정 처리는 일정을 호스팅하고 처리하는 보고서 서버의 현지 시간을 기준으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="ece8b-115">Schedule processing is based on the local time of the report server that hosts and processes the schedule.</span></span>  
  
## <a name="navigation"></a><span data-ttu-id="ece8b-116">탐색</span><span class="sxs-lookup"><span data-stu-id="ece8b-116">Navigation</span></span>  
 <span data-ttu-id="ece8b-117">사용자 인터페이스(UI)에서 이 위치를 탐색하려면 다음 절차를 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="ece8b-117">Use the following procedures to navigate to this location in the user interface (UI).</span></span>  
  
### <a name="to-open-the-new-schedule-or-edit-schedule-page-from-the-execution-properties-page-of-a-report"></a><span data-ttu-id="ece8b-118">보고서의 실행 속성 페이지에서 새 일정 또는 일정 편집 페이지를 열려면</span><span class="sxs-lookup"><span data-stu-id="ece8b-118">To open the New Schedule or Edit Schedule page from the Execution properties page of a report</span></span>  
  
1.  <span data-ttu-id="ece8b-119">보고서 관리자를 열고 일정을 구성할 보고서를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="ece8b-119">Open Report Manager, and locate the report for which you want configure a schedule.</span></span>  
  
2.  <span data-ttu-id="ece8b-120">보고서 위로 마우스를 이동하여 드롭다운 화살표를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ece8b-120">Hover over the report, and click the drop-down arrow.</span></span>  
  
3.  <span data-ttu-id="ece8b-121">드롭다운 메뉴에서 **관리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ece8b-121">In the drop-down menu, click **Manage**.</span></span> <span data-ttu-id="ece8b-122">모델의 일반 속성 페이지가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="ece8b-122">This opens the General properties page for the model.</span></span>  
  
4.  <span data-ttu-id="ece8b-123">**실행** 탭을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ece8b-123">Select the **Execution** tab.</span></span>  
  
5.  <span data-ttu-id="ece8b-124">**보고서 실행 스냅샷에서 이 보고서 렌더링**옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ece8b-124">Select the **Render this report from a report execution snapshot option**.</span></span> <span data-ttu-id="ece8b-125">그런 다음 **다음 일정을 사용하여 스냅샷을 보고서 기록에 추가**, **보고서별 일정**을 차례로 선택한 후</span><span class="sxs-lookup"><span data-stu-id="ece8b-125">Then select **Use the following schedule to add snapshots to report history**, and select **Report-specific schedule**.</span></span> <span data-ttu-id="ece8b-126">**구성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ece8b-126">Then click **Configure**.</span></span>  
  
### <a name="to-open-the-new-schedule-or-edit-schedule-page-from-the-history-properties-page-of-a-report"></a><span data-ttu-id="ece8b-127">보고서의 기록 속성 페이지에서 새 일정 또는 일정 편집 페이지를 열려면</span><span class="sxs-lookup"><span data-stu-id="ece8b-127">To open the New Schedule or Edit Schedule page from the History properties page of a report</span></span>  
  
1.  <span data-ttu-id="ece8b-128">보고서 관리자를 열고 일정을 구성할 보고서를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="ece8b-128">Open Report Manager, and locate the report for which you want configure a schedule.</span></span>  
  
2.  <span data-ttu-id="ece8b-129">보고서 위로 마우스를 이동하여 드롭다운 화살표를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ece8b-129">Hover over the report, and click the drop-down arrow.</span></span>  
  
3.  <span data-ttu-id="ece8b-130">드롭다운 메뉴에서 **관리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ece8b-130">In the drop-down menu, click **Manage**.</span></span> <span data-ttu-id="ece8b-131">모델의 일반 속성 페이지가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="ece8b-131">This opens the General properties page for the model.</span></span>  
  
4.  <span data-ttu-id="ece8b-132">**기록** 탭을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ece8b-132">Select the **History** tab.</span></span>  
  
5.  <span data-ttu-id="ece8b-133">**다음 일정을 사용하여 스냅샷을 보고서 기록에 추가**, **보고서별 일정**을 차례로 선택한 후</span><span class="sxs-lookup"><span data-stu-id="ece8b-133">Select **Use the following schedule to add snapshots to report history**, and select **Report-specific schedule**.</span></span> <span data-ttu-id="ece8b-134">**구성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ece8b-134">Then click **Configure**.</span></span>  
  
### <a name="to-open-the-new-schedule-or-edit-schedule-page-from-the-subscriptions-page"></a><span data-ttu-id="ece8b-135">구독 페이지에서 새 일정 또는 일정 편집 페이지를 열려면</span><span class="sxs-lookup"><span data-stu-id="ece8b-135">To open the New Schedule or Edit Schedule page from the Subscriptions page</span></span>  
  
1.  <span data-ttu-id="ece8b-136">보고서 관리자를 열고 일정을 구성할 보고서를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="ece8b-136">Open Report Manager, and locate the report for which you want configure a schedule.</span></span>  
  
2.  <span data-ttu-id="ece8b-137">보고서 위로 마우스를 이동하여 드롭다운 화살표를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ece8b-137">Hover over the report, and click the drop-down arrow.</span></span>  
  
3.  <span data-ttu-id="ece8b-138">드롭다운 메뉴에서 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="ece8b-138">In the drop-down menu,</span></span>  
  
    -   <span data-ttu-id="ece8b-139">**관리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ece8b-139">Click **Manage**.</span></span> <span data-ttu-id="ece8b-140">보고서의 일반 속성 페이지가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="ece8b-140">This opens the General properties page for the report.</span></span> <span data-ttu-id="ece8b-141">**구독** 탭을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ece8b-141">Then select the **Subscriptions** tab.</span></span>  
  
    -   <span data-ttu-id="ece8b-142">**구독**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ece8b-142">Click **Subscribe**.</span></span> <span data-ttu-id="ece8b-143">보고서의 **구독** 속성 페이지가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="ece8b-143">This opens the **Subscriptions** properties page for the report.</span></span>  
  
4.  <span data-ttu-id="ece8b-144">도구 모음에서 **새 구독** 을 클릭하거나 편집할 기존 구독을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ece8b-144">In the toolbar, click **New Subscription** or select an existing subscription to edit.</span></span>  
  
5.  <span data-ttu-id="ece8b-145">**구독 처리 옵션**에서 **새 일정**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ece8b-145">Under **Subscription Processing Options**, click **New Schedule**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="ece8b-146">옵션</span><span class="sxs-lookup"><span data-stu-id="ece8b-146">Options</span></span>  
 <span data-ttu-id="ece8b-147">**일정 정보**</span><span class="sxs-lookup"><span data-stu-id="ece8b-147">**Schedule details**</span></span>  
 <span data-ttu-id="ece8b-148">보고서 실행 시간과 빈도를 지정하는 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ece8b-148">Select options that determine when and how often a report runs.</span></span> <span data-ttu-id="ece8b-149">빈도 옵션은 계층적입니다.</span><span class="sxs-lookup"><span data-stu-id="ece8b-149">Frequency options are layered.</span></span> <span data-ttu-id="ece8b-150">첫째 옵션 집합은 빈도 범주(시간별, 일별, 주별 등)를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ece8b-150">The first set of options specifies a category of frequency (hourly, daily, weekly, and so on).</span></span> <span data-ttu-id="ece8b-151">둘째 옵션 집합은 처음 선택에 따라 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="ece8b-151">The second set of options that appears is based on your initial selection.</span></span>  
  
-   <span data-ttu-id="ece8b-152">**시간** 은 시간 간격으로 실행되는 일정을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="ece8b-152">**Hour** defines a schedule that runs at hourly intervals.</span></span> <span data-ttu-id="ece8b-153">일정을 실행할 날짜를 지정하려면 **시작 및 끝 날짜** 섹션을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="ece8b-153">Use the **Start and end dates** section to specify the day on which to run the schedule.</span></span>  
  
-   <span data-ttu-id="ece8b-154">**일** 은 선택하는 요일의 특정 시간 및 분에 실행되는 일정을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="ece8b-154">**Day** defines a schedule that runs on the days you select at a specific hour and minute.</span></span> <span data-ttu-id="ece8b-155">매일, 매일, 매일 등의 방법으로 일을 지정할 수 있습니다. \<*day*> \<*number*></span><span class="sxs-lookup"><span data-stu-id="ece8b-155">You can specify days in the following ways: Every \<*day*>, Every weekday, and Every \<*number*> day.</span></span> <span data-ttu-id="ece8b-156">한 가지 방법을 선택하면 다른 날이 선택된 것처럼 보이더라도 다른 방법은 사용할 수 없게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ece8b-156">Choosing one approach voids the others, even if the other days appear to be selected.</span></span>  
  
-   <span data-ttu-id="ece8b-157">**주** 는 주별 간격으로 특정 시간 및 분에 실행되는 일정을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="ece8b-157">**Week** defines a schedule that runs at weekly intervals at a specific hour and minute.</span></span> <span data-ttu-id="ece8b-158">간격은 주 전체(예: 격주간)나 주 중의 요일로 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ece8b-158">The interval can be a complete week (for example, every two weeks), or days within a week.</span></span>  
  
-   <span data-ttu-id="ece8b-159">**월** 은 월별로 실행되는 일정을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="ece8b-159">**Month** defines a schedule that runs on a monthly basis.</span></span> <span data-ttu-id="ece8b-160">월에서 패턴에 따른 날짜(예: 매월 마지막 일요일)나 특정 달력 날짜(예: 매월 1일과 15일을 나타내는 1과 15)를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ece8b-160">Within a month, you can choose a day based on a pattern (for example, the last Sunday of every month) or specific calendar dates (such as 1 and 15 to indicate the first and fifteenth day of every month).</span></span> <span data-ttu-id="ece8b-161">쉼표와 하이픈을 사용하여 여러 날짜와 범위를 지정할 수 있습니다(예: 1, 5, 7-12, 21).</span><span class="sxs-lookup"><span data-stu-id="ece8b-161">Using commas and hyphens, you can specify multiple days and ranges, for example, 1, 5, 7-12, 21.</span></span>  
  
-   <span data-ttu-id="ece8b-162">**한 번** 은 한 번만 실행되는 일정을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="ece8b-162">**Once** defines a schedule that runs only once.</span></span> <span data-ttu-id="ece8b-163">일정을 실행할 날짜를 지정하려면 **시작 및 끝 날짜** 섹션을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="ece8b-163">Use the **Start and end dates** section to specify the day on which to run the schedule.</span></span> <span data-ttu-id="ece8b-164">이 일정은 처리되는 즉시 만료됩니다.</span><span class="sxs-lookup"><span data-stu-id="ece8b-164">This schedule expires as soon as it is processed.</span></span>  
  
 <span data-ttu-id="ece8b-165">**시작 및 끝 날짜**</span><span class="sxs-lookup"><span data-stu-id="ece8b-165">**Start and end dates**</span></span>  
 <span data-ttu-id="ece8b-166">일정이 개시되는 시작 날짜와 일정이 만료되는 끝 날짜를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ece8b-166">Specify a start date that determines when the schedule takes effect and an end date that determines when the schedule expires.</span></span>  
  
 <span data-ttu-id="ece8b-167">일정은 별도의 알림 메시지 없이 만료됩니다.</span><span class="sxs-lookup"><span data-stu-id="ece8b-167">Schedules expire without notification.</span></span> <span data-ttu-id="ece8b-168">끝 날짜 이후에는 일정이 더 이상 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ece8b-168">After the end date, they no longer run.</span></span> <span data-ttu-id="ece8b-169">만료된 일정은 삭제되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ece8b-169">Expired schedules are not deleted.</span></span> <span data-ttu-id="ece8b-170">일정은 수동으로 삭제해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ece8b-170">Schedules can only be deleted manually.</span></span> <span data-ttu-id="ece8b-171">따라서 일정이 계속되도록 선택하면 끝 날짜를 연장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ece8b-171">That way, if you choose to continue the schedule, you can extend the end date.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ece8b-172">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ece8b-172">See Also</span></span>  
 <span data-ttu-id="ece8b-173">[보고서 관리자&#40;SSRS 기본 모드&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="ece8b-173">[Report Manager  &#40;SSRS Native Mode&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md) </span></span>  
 <span data-ttu-id="ece8b-174">[일정 만들기, 수정 및 삭제](subscriptions/create-modify-and-delete-schedules.md) </span><span class="sxs-lookup"><span data-stu-id="ece8b-174">[Create, Modify, and Delete Schedules](subscriptions/create-modify-and-delete-schedules.md) </span></span>  
 [<span data-ttu-id="ece8b-175">보고서 관리자 F1 도움말</span><span class="sxs-lookup"><span data-stu-id="ece8b-175">Report Manager F1 Help</span></span>](../../2014/reporting-services/report-manager-f1-help.md)  
  
  
