---
title: 추적 테이블 속성 (이벤트 선택 탭) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- sql12.pro.tracetableproperties.eventsselection.f1
helpviewer_keywords:
- Trace Table Properties dialog box
ms.assetid: fa21df6a-b6b5-4b15-9104-957385821594
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: a2e72f299c9d83762876ce250f750924430ba2f3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741211"
---
# <a name="trace-table-properties-events-selection-tab"></a><span data-ttu-id="791e9-102">추적 테이블 속성(이벤트 선택 탭)</span><span class="sxs-lookup"><span data-stu-id="791e9-102">Trace Table Properties (Events Selection Tab)</span></span>
  <span data-ttu-id="791e9-103">**추적 테이블 속성** 대화 상자의 **이벤트 선택** 탭을 사용하여 추적의 이벤트 및 데이터 열 속성을 보거나 추적에서 이벤트나 열을 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="791e9-103">Use the **Events Selection** tab of the **Trace Table Properties** dialog box to view the events and data column properties of the trace or to remove events or columns from the trace.</span></span>  
  
 <span data-ttu-id="791e9-104">이 창을 표시하려면 [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] 를 사용하여 추적 테이블을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="791e9-104">To view this window, use [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] to open a trace table.</span></span> <span data-ttu-id="791e9-105">그런 다음 **파일** 메뉴에서 **속성**을 클릭 하 고 **이벤트 선택** 탭을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="791e9-105">Then on the **File** menu, click **Properties**, and then click the **Events Selection** tab.</span></span>  
  
## <a name="options"></a><span data-ttu-id="791e9-106">옵션</span><span class="sxs-lookup"><span data-stu-id="791e9-106">Options</span></span>  
 <span data-ttu-id="791e9-107">**Events** 열</span><span class="sxs-lookup"><span data-stu-id="791e9-107">**Events** column</span></span>  
 <span data-ttu-id="791e9-108">이벤트 범주별로 구성된 추적된 이벤트를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="791e9-108">View traced events which are organized by event category.</span></span> <span data-ttu-id="791e9-109">이벤트는 해당 확인란을 선택하거나 이벤트에 대한 데이터 열을 선택하여 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="791e9-109">Events can be selected by checking the box or by checking a data column for an event.</span></span> <span data-ttu-id="791e9-110">이벤트 확인란을 선택하면 해당 이벤트에 대해 사용할 수 있는 모든 데이터 열이 선택됩니다.</span><span class="sxs-lookup"><span data-stu-id="791e9-110">If the event box is checked, all data columns available for that event are selected.</span></span> <span data-ttu-id="791e9-111">이벤트에 대한 데이터 열을 선택하면 이벤트가 선택되고 필요한 다른 열도 자동으로 선택됩니다.</span><span class="sxs-lookup"><span data-stu-id="791e9-111">If the data column for an event is checked, the event is checked and any other required column is also automatically checked.</span></span> <span data-ttu-id="791e9-112">추적 파일 또는 테이블을 볼 때 이벤트 또는 데이터 열에 대한 확인란의 선택을 취소하면 추적 창에 표시되는 데이터의 양이 줄어들므로 보다 쉽게 분석할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="791e9-112">If you are viewing a trace file or table, clearing check boxes for events or data columns reduces the amount of visible data in the trace window for easier analysis.</span></span> <span data-ttu-id="791e9-113">추적 창에 표시되는 데이터의 양은 열 필터를 변경하여 줄일 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="791e9-113">You can also change column filters to reduce the amount of visible data in the trace window.</span></span> <span data-ttu-id="791e9-114">이벤트 클래스에 대한 자세한 내용은 [SQL Server Event Class Reference](../relational-databases/event-classes/sql-server-event-class-reference.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="791e9-114">For more information about event classes, see [SQL Server Event Class Reference](../relational-databases/event-classes/sql-server-event-class-reference.md).</span></span>  
  
 <span data-ttu-id="791e9-115">기타 데이터 열</span><span class="sxs-lookup"><span data-stu-id="791e9-115">Other data columns</span></span>  
 <span data-ttu-id="791e9-116">추적된 데이터 열을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="791e9-116">View traced data columns.</span></span> <span data-ttu-id="791e9-117">추적에 포함된 각 이벤트에 대해 기본적으로 추적의 모든 관련 데이터 열이 선택됩니다.</span><span class="sxs-lookup"><span data-stu-id="791e9-117">All relevant data columns in the trace are checked by default for each event included in the trace.</span></span>  
  
 <span data-ttu-id="791e9-118">데이터 열 머리글을 클릭하고 필터 조건을 입력하여 필터를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="791e9-118">Specify filters by clicking the data column heading and entering the filter criteria.</span></span> <span data-ttu-id="791e9-119">필터링된 데이터 열은 **필터 편집** 대화 상자에서 열 레이블 왼쪽에 있는 필터 아이콘으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="791e9-119">Filtered data columns are indicated by a filter icon to the left of the column label in the **Edit Filter** dialog box.</span></span>  
  
 <span data-ttu-id="791e9-120">**모든 이벤트 표시**</span><span class="sxs-lookup"><span data-stu-id="791e9-120">**Show all events**</span></span>  
 <span data-ttu-id="791e9-121">사용할 수 있는 모든 이벤트를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="791e9-121">Show all available events.</span></span> <span data-ttu-id="791e9-122">기본적으로 **이벤트 선택** 표에서 선택된 행만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="791e9-122">By default, only rows in the **Events Selection** grid that are selected display.</span></span> <span data-ttu-id="791e9-123">**이벤트 선택** 표에서 선택되지 않은 모든 이벤트를 숨기려면 이 확인란의 선택을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="791e9-123">Uncheck this box to hide all unselected events in the **Events Selection** grid.</span></span> <span data-ttu-id="791e9-124">**모든 이벤트 표시** 를 선택한 상태에서 추적 파일 또는 테이블을 볼 때는 추적에 기록된 모든 이벤트가 추적 창에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="791e9-124">If **Show all events** is checked and you are viewing a trace file or table, all events that were recorded in the trace display in the trace window.</span></span>  
  
 <span data-ttu-id="791e9-125">**모든 열 표시**</span><span class="sxs-lookup"><span data-stu-id="791e9-125">**Show all columns**</span></span>  
 <span data-ttu-id="791e9-126">사용할 수 있는 모든 데이터 열을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="791e9-126">Show all available data columns.</span></span> <span data-ttu-id="791e9-127">기본적으로 선택된 데이터 열만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="791e9-127">By default, only data columns that are selected display.</span></span> <span data-ttu-id="791e9-128">**이벤트 선택** 표에서 선택되지 않은 모든 데이터 열을 숨기려면 이 확인란의 선택을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="791e9-128">Uncheck this box to hide all unselected data columns in the **Events Selection** grid.</span></span>  
  
 <span data-ttu-id="791e9-129">**열 필터**</span><span class="sxs-lookup"><span data-stu-id="791e9-129">**Column Filters**</span></span>  
 <span data-ttu-id="791e9-130">열 레이블 왼쪽에 필터 아이콘을 표시하는 **필터 편집** 대화 상자를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="791e9-130">Launches the **Edit Filter** dialog box, which displays a filter icon to the left of the column label.</span></span> <span data-ttu-id="791e9-131">이 대화 상자를 사용하여 데이터 열 필터를 편집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="791e9-131">You can use this dialog box to edit data column filters.</span></span>  
  
 <span data-ttu-id="791e9-132">**열 구성**</span><span class="sxs-lookup"><span data-stu-id="791e9-132">**Organize Columns**</span></span>  
 <span data-ttu-id="791e9-133">**이벤트** 를 선택하고 추적할 데이터 열을 선택한 다음 **열 구성** 을 클릭하여 추적 결과 창에서 표에 있는 열의 순서를 다시 정렬합니다.</span><span class="sxs-lookup"><span data-stu-id="791e9-133">After selecting **Events** and data columns to trace, click **Organize Columns** to force the grid to reorder the column in the trace results window.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="791e9-134">참고 항목</span><span class="sxs-lookup"><span data-stu-id="791e9-134">See Also</span></span>  
 <span data-ttu-id="791e9-135">[SQL Server Profiler &#40;추적 테이블을 엽니다&#41;](../tools/sql-server-profiler/open-a-trace-table-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="791e9-135">[Open a Trace Table &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/open-a-trace-table-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="791e9-136">[SQL Server Profiler 템플릿 및 권한](../tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md) </span><span class="sxs-lookup"><span data-stu-id="791e9-136">[SQL Server Profiler Templates and Permissions](../tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md) </span></span>  
 [<span data-ttu-id="791e9-137">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="791e9-137">SQL Server Profiler</span></span>](../tools/sql-server-profiler/sql-server-profiler.md)  
  
  
