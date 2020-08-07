---
title: 추적 파일 속성 (이벤트 선택 탭) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- sql12.pro.tracefileproperties.eventsselection.f1
helpviewer_keywords:
- Trace File Properties dialog box
ms.assetid: 158d442f-2225-4173-8545-fb1cf611b4d0
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: abfadc2b1df4cda039d7e413e5ba0c7777e7c04e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734400"
---
# <a name="trace-file-properties-events-selection-tab"></a><span data-ttu-id="14335-102">추적 파일 속성(이벤트 선택 탭)</span><span class="sxs-lookup"><span data-stu-id="14335-102">Trace File Properties (Events Selection Tab)</span></span>
  <span data-ttu-id="14335-103">**추적 파일 템플릿 속성** 대화 상자의 **이벤트 선택** 탭을 사용하여 추적의 열 속성을 보거나 추적에서 데이터 열을 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="14335-103">Use the **Events Selection** tab of the **Trace File Template Properties** dialog box to view the column properties of the trace or remove data columns from the trace.</span></span>  
  
 <span data-ttu-id="14335-104">이 창을 보려면 추적 파일을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="14335-104">To view this window, open a trace file.</span></span> <span data-ttu-id="14335-105">그런 다음 **파일** 메뉴에서 **속성**을 클릭하고 **이벤트 선택** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="14335-105">Then, on the **File** menu, click **Properties**, and then click the **Events Selection** tab.</span></span>  
  
## <a name="options"></a><span data-ttu-id="14335-106">옵션</span><span class="sxs-lookup"><span data-stu-id="14335-106">Options</span></span>  
 <span data-ttu-id="14335-107">**Events** 열</span><span class="sxs-lookup"><span data-stu-id="14335-107">**Events** column</span></span>  
 <span data-ttu-id="14335-108">이벤트 범주별로 구성된 추적된 이벤트를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="14335-108">View traced events which are organized by event category.</span></span> <span data-ttu-id="14335-109">처음에는 추적의 모든 이벤트가 선택됩니다.</span><span class="sxs-lookup"><span data-stu-id="14335-109">Initially, all events in the trace are selected.</span></span> <span data-ttu-id="14335-110">이벤트는 해당 확인란을 선택하거나 이벤트에 대한 데이터 열을 선택하여 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="14335-110">Events can be selected by checking the box or by checking a data column for an event.</span></span> <span data-ttu-id="14335-111">이벤트 확인란을 선택하면 해당 이벤트에 대해 사용할 수 있는 모든 데이터 열이 선택됩니다.</span><span class="sxs-lookup"><span data-stu-id="14335-111">If the event box is checked, all data columns available for that event are selected.</span></span> <span data-ttu-id="14335-112">이벤트에 대한 데이터 열을 선택하면 이벤트가 선택되고 필요한 다른 열도 자동으로 선택됩니다.</span><span class="sxs-lookup"><span data-stu-id="14335-112">If the data column for an event is checked, the event is checked and any other required column is also automatically checked.</span></span> <span data-ttu-id="14335-113">추적 파일 또는 테이블을 볼 때 이벤트 또는 데이터 열에 대한 확인란의 선택을 취소하면 추적 창에 표시되는 데이터의 양이 줄어들므로 보다 쉽게 분석할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="14335-113">If you are viewing a trace file or table, clearing check boxes for events or data columns reduces the amount of visible data in the trace window for easier analysis.</span></span> <span data-ttu-id="14335-114">추적 창에 표시되는 데이터의 양은 열 필터를 변경하여 줄일 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="14335-114">You can also change column filters to reduce the amount of visible data in the trace window.</span></span> <span data-ttu-id="14335-115">이벤트 클래스에 대한 자세한 내용은 [SQL Server Event Class Reference](../relational-databases/event-classes/sql-server-event-class-reference.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="14335-115">For more information about event classes, see [SQL Server Event Class Reference](../relational-databases/event-classes/sql-server-event-class-reference.md).</span></span>  
  
 <span data-ttu-id="14335-116">데이터 열</span><span class="sxs-lookup"><span data-stu-id="14335-116">Data Columns</span></span>  
 <span data-ttu-id="14335-117">추적된 데이터 열을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="14335-117">View traced data columns.</span></span> <span data-ttu-id="14335-118">추적에 포함된 각 이벤트에 대해 기본적으로 추적의 모든 관련 데이터 열이 선택됩니다.</span><span class="sxs-lookup"><span data-stu-id="14335-118">All relevant data columns in the trace are checked by default for each event included in the trace.</span></span>  
  
 <span data-ttu-id="14335-119">데이터 열 머리글을 클릭하고 필터 조건을 입력하여 필터를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="14335-119">Specify filters by clicking the data column heading and entering the filter criteria.</span></span> <span data-ttu-id="14335-120">필터링된 데이터 열은 **필터 편집** 대화 상자에서 열 레이블 왼쪽에 있는 필터 아이콘으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="14335-120">Filtered data columns are indicated by a filter icon to the left of the column label in the **Edit Filter** dialog box.</span></span>  
  
 <span data-ttu-id="14335-121">**모든 이벤트 표시**</span><span class="sxs-lookup"><span data-stu-id="14335-121">**Show all events**</span></span>  
 <span data-ttu-id="14335-122">사용할 수 있는 모든 이벤트를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="14335-122">Show all available events.</span></span> <span data-ttu-id="14335-123">기본적으로 **이벤트 선택** 표에서 선택된 행만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="14335-123">By default, only rows in the **Events Selection** grid that are selected display.</span></span> <span data-ttu-id="14335-124">**이벤트 선택** 표에서 선택되지 않은 모든 이벤트를 숨기려면 이 확인란의 선택을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="14335-124">Uncheck this box to hide all unselected events in the **Events Selection** grid.</span></span> <span data-ttu-id="14335-125">**모든 이벤트 표시** 를 선택한 상태에서 추적 파일 또는 테이블을 볼 때는 추적에 기록된 모든 이벤트가 추적 창에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="14335-125">If **Show all events** is checked and you are viewing a trace file or table, all events that were recorded in the trace display in the trace window.</span></span>  
  
 <span data-ttu-id="14335-126">**모든 열 표시**</span><span class="sxs-lookup"><span data-stu-id="14335-126">**Show all columns**</span></span>  
 <span data-ttu-id="14335-127">사용할 수 있는 모든 데이터 열을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="14335-127">Show all available data columns.</span></span> <span data-ttu-id="14335-128">기본적으로 선택된 데이터 열만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="14335-128">By default, only data columns that are selected display.</span></span> <span data-ttu-id="14335-129">**이벤트 선택** 표에서 선택되지 않은 모든 데이터 열을 숨기려면 이 확인란의 선택을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="14335-129">Uncheck this box to hide all unselected data columns in the **Events Selection** grid.</span></span>  
  
 <span data-ttu-id="14335-130">**열 필터**</span><span class="sxs-lookup"><span data-stu-id="14335-130">**Column Filters**</span></span>  
 <span data-ttu-id="14335-131">**필터 편집** 대화 상자를 시작합니다. 필터링된 데이터 열의 열 레이블 왼쪽에 필터 아이콘이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="14335-131">Launches the **Edit Filter** dialog box, which displays a filter icon to the left of the column label for filtered data columns.</span></span> <span data-ttu-id="14335-132">**필터 편집** 대화 상자를 사용하여 데이터 열 필터를 편집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="14335-132">Use the **Edit Filter** dialog box to edit data column filters.</span></span>  
  
 <span data-ttu-id="14335-133">**열 구성**</span><span class="sxs-lookup"><span data-stu-id="14335-133">**Organize Columns**</span></span>  
 <span data-ttu-id="14335-134">**이벤트** 를 선택하고 추적할 데이터 열을 선택한 다음 **열 구성** 을 클릭하여 추적 결과 창에서 표에 있는 열의 순서를 다시 정렬합니다.</span><span class="sxs-lookup"><span data-stu-id="14335-134">After selecting **Events** and data columns to trace, click **Organize Columns** to force the grid to reorder the column in the trace results window.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14335-135">참고 항목</span><span class="sxs-lookup"><span data-stu-id="14335-135">See Also</span></span>  
 <span data-ttu-id="14335-136">[추적 파일 &#40;SQL Server Profiler&#41;에 대 한 이벤트 및 데이터 열을 지정 합니다.](../tools/sql-server-profiler/specify-events-and-data-columns-for-a-trace-file-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="14335-136">[Specify Events and Data Columns for a Trace File &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/specify-events-and-data-columns-for-a-trace-file-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="14335-137">[추적 &#40;SQL Server Profiler&#41;에서 이벤트를 필터링 합니다.](../tools/sql-server-profiler/filter-events-in-a-trace-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="14335-137">[Filter Events in a Trace &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/filter-events-in-a-trace-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="14335-138">[SQL Server Profiler&#41;&#40;필터 정보 보기](../tools/sql-server-profiler/view-filter-information-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="14335-138">[View Filter Information &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/view-filter-information-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="14335-139">[필터 &#40;SQL Server Profiler를 수정&#41;](../tools/sql-server-profiler/modify-a-filter-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="14335-139">[Modify a Filter &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/modify-a-filter-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="14335-140">[SQL Server Profiler](../tools/sql-server-profiler/sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="14335-140">[SQL Server Profiler](../tools/sql-server-profiler/sql-server-profiler.md) </span></span>  
 [<span data-ttu-id="14335-141">SQL Server Profiler 템플릿 및 권한</span><span class="sxs-lookup"><span data-stu-id="14335-141">SQL Server Profiler Templates and Permissions</span></span>](../tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md)  
  
  
