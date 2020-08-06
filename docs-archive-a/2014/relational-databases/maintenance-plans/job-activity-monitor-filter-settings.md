---
title: 작업 활동 모니터(필터 설정) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- sql12.swb.jobactivitymon.filter.f1
ms.assetid: 89cb0055-5262-447f-8464-7203d4caba78
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: feba7b992d5d1d375b93df12135487a092792ee1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653348"
---
# <a name="job-activity-monitor-filter-settings"></a><span data-ttu-id="b9340-102">작업 활동 모니터(필터 설정)</span><span class="sxs-lookup"><span data-stu-id="b9340-102">Job Activity Monitor (Filter Settings)</span></span>
  <span data-ttu-id="b9340-103">이 페이지를 사용하여 작업 활동 모니터에 표시되는 행 수를 줄일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b9340-103">Use this page to reduce the number of rows visible in the Job Activity Monitor.</span></span> <span data-ttu-id="b9340-104">하나 또는 여러 개의 사용 가능한 상자에 조건을 입력하여 지정한 값을 만족하는 행만 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="b9340-104">Enter criteria in one or several of the available boxes, to show only the rows that meet the specified values.</span></span> <span data-ttu-id="b9340-105">**상태** 또는 **차단 유형** 과 같은 일부 상자에서는 드롭다운 목록으로 한정된 수의 가능한 값을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="b9340-105">Some of the boxes, such as **Status** or **Blocking Type** offer a finite number of possible values, provided by a drop-down list.</span></span> <span data-ttu-id="b9340-106">**애플리케이션** 과 같은 기타 상자에서는 어떤 값이든 원하는 만큼 쉼표로 구분된 목록으로 입력할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b9340-106">Others, such as **Application,** allow you to enter whatever value and as many values as you wish, as a comma separated list.</span></span> <span data-ttu-id="b9340-107">도구 모음 아이콘을 사용하면 범주별 또는 사전순으로 사용 가능한 상자를 정렬할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b9340-107">Toolbar icons allow you to sort the available boxes by category or alphabetically.</span></span> <span data-ttu-id="b9340-108">각각에 대해 간단한 설명을 표시할 조건을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b9340-108">Click the criteria to show a short description of the each one.</span></span>  
  
 <span data-ttu-id="b9340-109">작업 활동 모니터를 필터링하려면 원하는 개수만큼 필터 조건을 제공하고 **필터 적용**을 클릭한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b9340-109">To filter the Job Activity Monitor, provide as many filter criteria as you want, click **Apply filter**, and then click **OK**.</span></span>  
  
## <a name="all-jobs"></a><span data-ttu-id="b9340-110">모든 작업</span><span class="sxs-lookup"><span data-stu-id="b9340-110">All Jobs</span></span>  
 <span data-ttu-id="b9340-111">이 필터 조건 그룹은 작업 활동 모니터를 필터링할 때 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b9340-111">This group of filter criteria is available when filtering the Job Activity Monitor.</span></span>  
  
 <span data-ttu-id="b9340-112">**이름**</span><span class="sxs-lookup"><span data-stu-id="b9340-112">**Name**</span></span>  
 <span data-ttu-id="b9340-113">이름으로 작업을 필터링합니다.</span><span class="sxs-lookup"><span data-stu-id="b9340-113">Filter jobs by name.</span></span>  
  
 <span data-ttu-id="b9340-114">**다음 실행**</span><span class="sxs-lookup"><span data-stu-id="b9340-114">**Next Run**</span></span>  
 <span data-ttu-id="b9340-115">다음에 실행하도록 예약된 날짜로 필터링합니다.</span><span class="sxs-lookup"><span data-stu-id="b9340-115">Filter by the date next scheduled to run.</span></span>  
  
 <span data-ttu-id="b9340-116">**실행 가능**</span><span class="sxs-lookup"><span data-stu-id="b9340-116">**Runnable**</span></span>  
 <span data-ttu-id="b9340-117">실행할 수 있는 작업을 표시하거나 실행할 수 없는 작업을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="b9340-117">View jobs that can be run, or jobs that cannot be run.</span></span> <span data-ttu-id="b9340-118">**예** 를 선택하여 실행할 수 있는 작업만 표시하거나 **아니요** 를 선택하여 실행할 수 없는 작업만 표시하거나 또는 **모두** 를 선택하여 실행할 수 있는 작업과 실행할 수 없는 작업을 모두 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="b9340-118">Select **Yes** to view only jobs that can be run, select **No** to view only jobs that cannot be run, or select **All** to view both jobs that can be run and those that cannot.</span></span>  
  
 <span data-ttu-id="b9340-119">**마지막 실행**</span><span class="sxs-lookup"><span data-stu-id="b9340-119">**Last Run**</span></span>  
 <span data-ttu-id="b9340-120">마지막으로 실행한 날짜로 필터링합니다.</span><span class="sxs-lookup"><span data-stu-id="b9340-120">Filter by the date last run.</span></span>  
  
 <span data-ttu-id="b9340-121">**마지막 실행 결과**</span><span class="sxs-lookup"><span data-stu-id="b9340-121">**Last Run Outcome**</span></span>  
 <span data-ttu-id="b9340-122">마지막으로 작업을 실행했을 때의 상태로 작업을 필터링합니다.</span><span class="sxs-lookup"><span data-stu-id="b9340-122">Filter jobs by the status last time the jobs were run.</span></span>  
  
 <span data-ttu-id="b9340-123">**Enabled**</span><span class="sxs-lookup"><span data-stu-id="b9340-123">**Enabled**</span></span>  
 <span data-ttu-id="b9340-124">사용하는 작업만 표시하거나 사용하지 않는 작업만 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="b9340-124">View only enabled or not enabled jobs</span></span>  
  
 <span data-ttu-id="b9340-125">**범주**</span><span class="sxs-lookup"><span data-stu-id="b9340-125">**Category**</span></span>  
 <span data-ttu-id="b9340-126">작업 범주로 작업을 필터링합니다.</span><span class="sxs-lookup"><span data-stu-id="b9340-126">Filter jobs by the job category.</span></span>  
  
 <span data-ttu-id="b9340-127">**예약됨**</span><span class="sxs-lookup"><span data-stu-id="b9340-127">**Scheduled**</span></span>  
 <span data-ttu-id="b9340-128">일정이 있는 작업을 모두 표시하거나 일정이 없는 작업을 모두 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="b9340-128">View all jobs with schedules, or without schedules.</span></span>  
  
 <span data-ttu-id="b9340-129">**상태**</span><span class="sxs-lookup"><span data-stu-id="b9340-129">**Status**</span></span>  
 <span data-ttu-id="b9340-130">상태로 작업을 필터링합니다.</span><span class="sxs-lookup"><span data-stu-id="b9340-130">Filter jobs by the status.</span></span>  
  
## <a name="description-area"></a><span data-ttu-id="b9340-131">설명 영역</span><span class="sxs-lookup"><span data-stu-id="b9340-131">Description Area</span></span>  
 <span data-ttu-id="b9340-132">**설명 상자**</span><span class="sxs-lookup"><span data-stu-id="b9340-132">**Description Box**</span></span>  
 <span data-ttu-id="b9340-133">이름이 지정되지 않은 이 상자에서는 선택된 조건에 대한 간단한 설명을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="b9340-133">This unnamed box provides a short description of the criteria as they are selected.</span></span>  
  
 <span data-ttu-id="b9340-134">**필터 적용**</span><span class="sxs-lookup"><span data-stu-id="b9340-134">**Apply filter**</span></span>  
 <span data-ttu-id="b9340-135">필터를 적용 하려면 **필터 적용** 을 클릭 한 다음 **확인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="b9340-135">To apply the filter, click **Apply filter** and then click **OK**.</span></span> <span data-ttu-id="b9340-136">**필터 설정 대화 상자** 에서 필터 설정을 유지 하 되 적용 하지 않으려면 **필터 적용**의 선택을 취소 한 다음 **확인**을 클릭 하 여 모든 행을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="b9340-136">To retain the filter settings in the **Filter Settings** dialog box, but not apply them, uncheck **Apply filter**, and then click **OK**, to display all rows.</span></span>  
  
 <span data-ttu-id="b9340-137">**지우기**</span><span class="sxs-lookup"><span data-stu-id="b9340-137">**Clear**</span></span>  
 <span data-ttu-id="b9340-138">필터 설정을 기본 설정으로 되돌립니다.</span><span class="sxs-lookup"><span data-stu-id="b9340-138">Returns the filter settings back to the default settings.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9340-139">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b9340-139">See Also</span></span>  
 [<span data-ttu-id="b9340-140">작업 활동 모니터링</span><span class="sxs-lookup"><span data-stu-id="b9340-140">Monitor Job Activity</span></span>](../../ssms/agent/monitor-job-activity.md)  
  
  
