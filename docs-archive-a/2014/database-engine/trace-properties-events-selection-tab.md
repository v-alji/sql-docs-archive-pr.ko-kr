---
title: 추적 속성 (이벤트 선택 탭) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- sql12.pro.traceproperties.eventsselection.f1
helpviewer_keywords:
- Trace Properties dialog box
ms.assetid: e1892f24-7272-4d5d-8926-6150cc82b2c3
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 11f4725865d39c21e36f5fd09eaf2afd4cde3017
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734399"
---
# <a name="trace-properties-events-selection-tab"></a><span data-ttu-id="9e391-102">추적 속성(이벤트 선택 탭)</span><span class="sxs-lookup"><span data-stu-id="9e391-102">Trace Properties (Events Selection Tab)</span></span>
  <span data-ttu-id="9e391-103">**추적 속성** 대화 상자의 **이벤트 선택** 탭을 사용하여 추적된 이벤트 및 데이터 열의 속성을 확인하거나 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e391-103">Use the **Events Selection** tab of the **Trace Properties** dialog box to view or specify traced events and data columns.</span></span>  
  
## <a name="options"></a><span data-ttu-id="9e391-104">옵션</span><span class="sxs-lookup"><span data-stu-id="9e391-104">Options</span></span>  
 <span data-ttu-id="9e391-105">**Events** 열</span><span class="sxs-lookup"><span data-stu-id="9e391-105">**Events** column</span></span>  
 <span data-ttu-id="9e391-106">이벤트 열에서 확인란을 선택하거나 선택 취소하여 추적된 이벤트를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="9e391-106">Specify traced events by selecting or clearing the check box in the event column.</span></span> <span data-ttu-id="9e391-107">**Events** 는 이벤트 범주별로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="9e391-107">**Events** are organized by event category.</span></span> <span data-ttu-id="9e391-108">템플릿에 지정된 이벤트 클래스는 자동으로 선택됩니다.</span><span class="sxs-lookup"><span data-stu-id="9e391-108">Event classes specified in the template are automatically selected.</span></span> <span data-ttu-id="9e391-109">자세한 내용은 [SQL Server Event Class Reference](../relational-databases/event-classes/sql-server-event-class-reference.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9e391-109">For more information, see [SQL Server Event Class Reference](../relational-databases/event-classes/sql-server-event-class-reference.md).</span></span>  
  
 <span data-ttu-id="9e391-110">데이터 열</span><span class="sxs-lookup"><span data-stu-id="9e391-110">Data columns</span></span>  
 <span data-ttu-id="9e391-111">원하는 이벤트 및 데이터 열에 해당하는 확인란을 선택하여 추적된 데이터 열을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="9e391-111">Specify traced data columns by checking the box that corresponds with the event and the data column you need.</span></span> <span data-ttu-id="9e391-112">추적에 포함된 각 이벤트와 관련된 모든 이벤트 열이 기본적으로 선택됩니다.</span><span class="sxs-lookup"><span data-stu-id="9e391-112">All relevant event columns are checked by default for each event included in the trace.</span></span>  
  
 <span data-ttu-id="9e391-113">데이터 열 머리글을 클릭하고 필터 조건을 입력하여 필터를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="9e391-113">Specify filters by clicking the data column heading and entering the filter criteria.</span></span> <span data-ttu-id="9e391-114">필터링된 데이터 열은 **필터 편집** 대화 상자에서 열 레이블 왼쪽에 있는 필터 아이콘으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="9e391-114">Filtered data columns are indicated by a filter icon to the left of the column label in the **Edit Filter** dialog box.</span></span> <span data-ttu-id="9e391-115">자세한 내용은 [SQL Server Profiler - 필터 편집](../../2014/database-engine/sql-server-profiler-edit-filter.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9e391-115">For more information, see [SQL Server Profiler - Edit Filter](../../2014/database-engine/sql-server-profiler-edit-filter.md).</span></span>  
  
 <span data-ttu-id="9e391-116">**모든 이벤트 표시**</span><span class="sxs-lookup"><span data-stu-id="9e391-116">**Show all events**</span></span>  
 <span data-ttu-id="9e391-117">사용할 수 있는 모든 이벤트를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="9e391-117">Show all available events.</span></span> <span data-ttu-id="9e391-118">기본적으로 **이벤트 선택** 표에서 선택된 행만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="9e391-118">By default, only rows in the **Events Selection** grid that are selected display.</span></span> <span data-ttu-id="9e391-119">**이벤트 선택** 표에서 선택되지 않은 모든 이벤트를 숨기려면 이 확인란의 선택을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="9e391-119">Uncheck this box to hide all unselected events in the **Events Selection** grid.</span></span>  
  
 <span data-ttu-id="9e391-120">**모든 열 표시**</span><span class="sxs-lookup"><span data-stu-id="9e391-120">**Show all columns**</span></span>  
 <span data-ttu-id="9e391-121">사용할 수 있는 모든 데이터 열을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="9e391-121">Show all available data columns.</span></span> <span data-ttu-id="9e391-122">기본적으로 선택된 데이터 열만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="9e391-122">By default, only data columns that are selected display.</span></span> <span data-ttu-id="9e391-123">**이벤트 선택** 표에서 선택되지 않은 모든 데이터 열을 숨기려면 이 확인란의 선택을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="9e391-123">Uncheck this box to hide all unselected data columns in the **Events Selection** grid.</span></span>  
  
 <span data-ttu-id="9e391-124">**열 필터**</span><span class="sxs-lookup"><span data-stu-id="9e391-124">**Column Filters**</span></span>  
 <span data-ttu-id="9e391-125">**필터 편집** 대화 상자를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="9e391-125">Launches the **Edit Filter** dialog box.</span></span> <span data-ttu-id="9e391-126">이 대화 상자를 사용하여 데이터 열 필터를 편집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e391-126">You can use this dialog to edit data column filters.</span></span>  
  
 <span data-ttu-id="9e391-127">**열 구성**</span><span class="sxs-lookup"><span data-stu-id="9e391-127">**Organize Columns**</span></span>  
 <span data-ttu-id="9e391-128">추적의 열 순서를 변경하고 결과를 하나 이상의 열로 그룹화합니다.</span><span class="sxs-lookup"><span data-stu-id="9e391-128">Changes the order of columns in the trace and groups results by one or more columns.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e391-129">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9e391-129">See Also</span></span>  
 <span data-ttu-id="9e391-130">[추적 파일 &#40;SQL Server Profiler&#41;에 대 한 이벤트 및 데이터 열을 지정 합니다.](../tools/sql-server-profiler/specify-events-and-data-columns-for-a-trace-file-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="9e391-130">[Specify Events and Data Columns for a Trace File &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/specify-events-and-data-columns-for-a-trace-file-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="9e391-131">[추적 &#40;SQL Server Profiler에 표시 되는 열 구성&#41;](../tools/sql-server-profiler/organize-columns-displayed-in-a-trace-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="9e391-131">[Organize Columns Displayed in a Trace &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/organize-columns-displayed-in-a-trace-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="9e391-132">[추적 &#40;SQL Server Profiler&#41;에서 이벤트를 필터링 합니다.](../tools/sql-server-profiler/filter-events-in-a-trace-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="9e391-132">[Filter Events in a Trace &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/filter-events-in-a-trace-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="9e391-133">[SQL Server Profiler&#41;&#40;필터 정보 보기](../tools/sql-server-profiler/view-filter-information-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="9e391-133">[View Filter Information &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/view-filter-information-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="9e391-134">[필터 &#40;SQL Server Profiler를 수정&#41;](../tools/sql-server-profiler/modify-a-filter-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="9e391-134">[Modify a Filter &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/modify-a-filter-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="9e391-135">[SQL Server Profiler 템플릿 및 권한](../tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md) </span><span class="sxs-lookup"><span data-stu-id="9e391-135">[SQL Server Profiler Templates and Permissions](../tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md) </span></span>  
 [<span data-ttu-id="9e391-136">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="9e391-136">SQL Server Profiler</span></span>](../tools/sql-server-profiler/sql-server-profiler.md)  
  
  
