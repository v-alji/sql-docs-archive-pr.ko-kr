---
title: 추적 템플릿 속성 (이벤트 선택 탭) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- sql12.pro.tracetemplateproperties.eventsselection.f1
helpviewer_keywords:
- Trace Template Properties dialog box
ms.assetid: 5b202457-ab42-4902-8012-7f3f40aa09f5
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: da497db6e9373c63836753dc2be96deb3ce90244
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740288"
---
# <a name="trace-template-properties-events-selection-tab"></a><span data-ttu-id="5b263-102">추적 템플릿 속성(이벤트 선택 탭)</span><span class="sxs-lookup"><span data-stu-id="5b263-102">Trace Template Properties (Events Selection Tab)</span></span>
  <span data-ttu-id="5b263-103">**추적 템플릿 속성** 대화 상자의 **이벤트 선택** 탭을 사용하여 [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] 추적 템플릿에 포함할 이벤트 클래스와 데이터 열을 표시, 편집 또는 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5b263-103">Use the **Events Selection** tab of the **Trace Template Properties** dialog box to view, edit, or specify event classes and data columns to include in a [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] trace template.</span></span>  
  
## <a name="options"></a><span data-ttu-id="5b263-104">옵션</span><span class="sxs-lookup"><span data-stu-id="5b263-104">Options</span></span>  
 <span data-ttu-id="5b263-105">**Events** 열</span><span class="sxs-lookup"><span data-stu-id="5b263-105">**Events** column</span></span>  
 <span data-ttu-id="5b263-106">이벤트 열에서 확인란을 선택하거나 선택 취소하여 추적해야 할 이벤트를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="5b263-106">Specify events that should be traced by selecting or clearing the check box in the event column.</span></span> <span data-ttu-id="5b263-107">이벤트는 이벤트 범주별로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="5b263-107">Events are organized by event category.</span></span>  
  
 <span data-ttu-id="5b263-108">**일반** 탭에서 **기존 템플릿을 바탕으로 새 템플릿 만들기** 를 선택한 경우 지정한 템플릿에 따라 이벤트가 자동으로 선택됩니다.</span><span class="sxs-lookup"><span data-stu-id="5b263-108">If you selected **Base new template on existing one** on the **General** tab, events are automatically selected according to the specified template.</span></span> <span data-ttu-id="5b263-109">이벤트 클래스에 대한 자세한 내용은 [SQL Server Event Class Reference](../relational-databases/event-classes/sql-server-event-class-reference.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="5b263-109">For more information about event classes, see [SQL Server Event Class Reference](../relational-databases/event-classes/sql-server-event-class-reference.md).</span></span>  
  
 <span data-ttu-id="5b263-110">데이터 열</span><span class="sxs-lookup"><span data-stu-id="5b263-110">Data columns</span></span>  
 <span data-ttu-id="5b263-111">필요한 데이터 열과 이벤트에 해당하는 확인란을 선택하여 추적해야 할 데이터 열을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="5b263-111">Specify data columns that should be traced by checking the box that corresponds with the event and the data column you need.</span></span> <span data-ttu-id="5b263-112">이벤트에 해당하는 확인란을 선택한 경우 추적에 포함된 이벤트마다 관련된 모든 이벤트 열이 기본적으로 선택되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5b263-112">All relevant event columns are checked by default for each event included in the trace, if the checkbox corresponding to the event is checked.</span></span> <span data-ttu-id="5b263-113">**일반** 탭에서 **기존 템플릿을 바탕으로 새 템플릿 만들기** 를 선택한 경우 지정한 템플릿에 따라 데이터 열과 필터가 자동으로 선택됩니다.</span><span class="sxs-lookup"><span data-stu-id="5b263-113">If you checked **Base new template on existing one** on the **General** tab, data columns and filters are automatically selected according to the specified template.</span></span>  
  
 <span data-ttu-id="5b263-114">데이터 열 머리글을 클릭하고 필터 조건을 입력하여 필터를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="5b263-114">Specify filters by clicking the data column heading and entering the filter criteria.</span></span> <span data-ttu-id="5b263-115">필터링된 데이터 열은 **필터 편집** 대화 상자에서 열 레이블 왼쪽에 있는 필터 아이콘으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="5b263-115">Filtered data columns are indicated by a filter icon to the left of the column label in the **Edit Filter** dialog box.</span></span>  
  
 <span data-ttu-id="5b263-116">**모든 이벤트 표시**</span><span class="sxs-lookup"><span data-stu-id="5b263-116">**Show all events**</span></span>  
 <span data-ttu-id="5b263-117">사용할 수 있는 모든 이벤트를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="5b263-117">Show all available events.</span></span> <span data-ttu-id="5b263-118">기존 템플릿을 기반으로 하지 않고 새 템플릿을 만드는 중이면 이 옵션이 기본적으로 선택되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5b263-118">This option is checked by default if you are creating a new template that is not based on an existing template.</span></span> <span data-ttu-id="5b263-119">**이벤트 선택** 표에서 선택되지 않은 이벤트를 모두 숨기려면 확인란의 선택을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="5b263-119">Uncheck to hide all unselected events in the **Events Selection** grid.</span></span>  
  
 <span data-ttu-id="5b263-120">**모든 열 표시**</span><span class="sxs-lookup"><span data-stu-id="5b263-120">**Show all columns**</span></span>  
 <span data-ttu-id="5b263-121">사용할 수 있는 모든 데이터 열을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="5b263-121">Show all available data columns.</span></span> <span data-ttu-id="5b263-122">기존 템플릿을 기반으로 하지 않고 새 템플릿을 만드는 중이면 이 옵션이 기본적으로 선택되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5b263-122">This option is checked by default if you are creating a new template that is not based on an existing template.</span></span> <span data-ttu-id="5b263-123">**이벤트 선택** 표에서 선택되지 않은 데이터 열을 모두 숨기려면 확인란의 선택을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="5b263-123">Uncheck to hide all unselected data columns in the **Events Selection** grid.</span></span>  
  
 <span data-ttu-id="5b263-124">**열 필터**</span><span class="sxs-lookup"><span data-stu-id="5b263-124">**Column Filters**</span></span>  
 <span data-ttu-id="5b263-125">데이터 열 레이블 왼쪽에 필터 아이콘을 표시하는 **필터 편집** 대화 상자를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="5b263-125">Launches the **Edit Filter** dialog box, which displays a filter icon to the left of the data column label.</span></span> <span data-ttu-id="5b263-126">**필터 편집** 대화 상자를 사용하여 데이터 열 필터를 편집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5b263-126">Use the **Edit Filter** dialog box to edit data column filters.</span></span>  
  
 <span data-ttu-id="5b263-127">**열 구성**</span><span class="sxs-lookup"><span data-stu-id="5b263-127">**Organize Columns**</span></span>  
 <span data-ttu-id="5b263-128">추적의 열 순서를 변경하고 결과를 하나 이상의 열로 그룹화합니다.</span><span class="sxs-lookup"><span data-stu-id="5b263-128">Changes the order of columns in the trace and groups results by one or more columns.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b263-129">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5b263-129">See Also</span></span>  
 <span data-ttu-id="5b263-130">[추적 파일 &#40;SQL Server Profiler&#41;에 대 한 이벤트 및 데이터 열을 지정 합니다.](../tools/sql-server-profiler/specify-events-and-data-columns-for-a-trace-file-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="5b263-130">[Specify Events and Data Columns for a Trace File &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/specify-events-and-data-columns-for-a-trace-file-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="5b263-131">[추적 &#40;SQL Server Profiler에 표시 되는 열 구성&#41;](../tools/sql-server-profiler/organize-columns-displayed-in-a-trace-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="5b263-131">[Organize Columns Displayed in a Trace &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/organize-columns-displayed-in-a-trace-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="5b263-132">[추적 &#40;SQL Server Profiler&#41;에서 이벤트를 필터링 합니다.](../tools/sql-server-profiler/filter-events-in-a-trace-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="5b263-132">[Filter Events in a Trace &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/filter-events-in-a-trace-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="5b263-133">[SQL Server Profiler&#41;&#40;필터 정보 보기](../tools/sql-server-profiler/view-filter-information-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="5b263-133">[View Filter Information &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/view-filter-information-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="5b263-134">[필터 &#40;SQL Server Profiler를 수정&#41;](../tools/sql-server-profiler/modify-a-filter-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="5b263-134">[Modify a Filter &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/modify-a-filter-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="5b263-135">[SQL Server Profiler 템플릿 및 권한](../tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md) </span><span class="sxs-lookup"><span data-stu-id="5b263-135">[SQL Server Profiler Templates and Permissions](../tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md) </span></span>  
 [<span data-ttu-id="5b263-136">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="5b263-136">SQL Server Profiler</span></span>](../tools/sql-server-profiler/sql-server-profiler.md)  
  
  
