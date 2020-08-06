---
title: 추적에서 이벤트 필터링 (SQL Server Profiler) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- filters [SQL Server], traces
- traces [SQL Server], filters
- traces [SQL Server], events
ms.assetid: 0fd63573-3b35-4f67-9e1e-ed9aabee11a8
author: stevestein
ms.author: sstein
ms.openlocfilehash: fef9dd6956d407011261c54f796a751a0bf94941
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739028"
---
# <a name="filter-events-in-a-trace-sql-server-profiler"></a><span data-ttu-id="4bab5-102">추적에서의 이벤트 필터링(SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="4bab5-102">Filter Events in a Trace (SQL Server Profiler)</span></span>
  <span data-ttu-id="4bab5-103">필터가 설정되면 추적에서 수집하는 이벤트가 제한됩니다.</span><span class="sxs-lookup"><span data-stu-id="4bab5-103">Filters limit the events collected in a trace.</span></span> <span data-ttu-id="4bab5-104">필터가 설정되어 있지 않으면 선택된 이벤트 클래스의 모든 이벤트가 추적 출력에서 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="4bab5-104">If a filter is not set, all events of the selected event classes are returned in the trace output.</span></span> <span data-ttu-id="4bab5-105">반드시 추적에 대한 필터를 설정해야 하는 것은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="4bab5-105">It is not mandatory to set a filter for a trace.</span></span> <span data-ttu-id="4bab5-106">그러나 필터를 설정하면 추적하는 동안 발생하는 오버헤드가 최소화됩니다.</span><span class="sxs-lookup"><span data-stu-id="4bab5-106">However, a filter minimizes the overhead that is incurred during tracing.</span></span>  
  
 <span data-ttu-id="4bab5-107">**추적 속성** 또는 **추적 템플릿 속성** 대화 상자의 **이벤트 선택** 탭을 사용하여 추적 정의에 필터를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="4bab5-107">You add filters to trace definitions by using the **Events Selection** tab of the **Trace Properties** or **Trace Template Properties** dialog box.</span></span>  
  
### <a name="to-filter-events-in-a-trace"></a><span data-ttu-id="4bab5-108">추적에서 이벤트를 필터링하려면</span><span class="sxs-lookup"><span data-stu-id="4bab5-108">To filter events in a trace</span></span>  
  
1.  <span data-ttu-id="4bab5-109">**추적 속성** 또는 **추적 템플릿 속성** 대화 상자에서 **이벤트 선택** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4bab5-109">In the **Trace Properties** or **Trace Template Properties** dialog box, click the **Events Selection** tab.</span></span>  
  
     <span data-ttu-id="4bab5-110">**이벤트 선택** 탭에는 표 형태 컨트롤이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4bab5-110">The **Events Selection** tab contains a grid control.</span></span> <span data-ttu-id="4bab5-111">표 형태 컨트롤은 추적 가능한 각 이벤트 클래스가 들어 있는 테이블입니다.</span><span class="sxs-lookup"><span data-stu-id="4bab5-111">The grid control is a table that contains each of the traceable event classes.</span></span> <span data-ttu-id="4bab5-112">테이블에는 각 이벤트 클래스에 대한 행이 하나씩 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4bab5-112">The table contains one row for each event class.</span></span> <span data-ttu-id="4bab5-113">이벤트 클래스는 사용자가 연결된 서버의 유형 및 버전에 따라 약간 다를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4bab5-113">The event classes may differ slightly, depending on the type and version of server to which you are connected.</span></span> <span data-ttu-id="4bab5-114">이벤트 클래스는 표의 **이벤트**열에서 식별되며 이벤트 범주별로 그룹화됩니다.</span><span class="sxs-lookup"><span data-stu-id="4bab5-114">The event classes are identified in the **Events**column of the grid and are grouped by event category.</span></span> <span data-ttu-id="4bab5-115">나머지 열은 각 이벤트 클래스에 대해 반환할 수 있는 데이터 열을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="4bab5-115">The remaining columns list the data columns that can be returned for each event class.</span></span>  
  
2.  <span data-ttu-id="4bab5-116">**열 필터**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4bab5-116">Click **Column Filters.**</span></span>  
  
     <span data-ttu-id="4bab5-117">**필터 편집**대화 상자가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="4bab5-117">The **Edit Filter**dialog box appears.</span></span> <span data-ttu-id="4bab5-118">**필터 편집**대화 상자에는 추적에서 이벤트를 필터링하는 데 사용할 수 있는 비교 연산자 목록이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4bab5-118">The **Edit Filter**dialog box contains a list of comparison operators that you can use to filter events in a trace.</span></span>  
  
3.  <span data-ttu-id="4bab5-119">필터를 적용하려면 비교 연산자를 클릭하고 필터에 사용할 값을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="4bab5-119">To apply a filter, click the comparison operator, and type a value to use for the filter.</span></span>  
  
4.  <span data-ttu-id="4bab5-120">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4bab5-120">Click **OK**.</span></span>  
  
 <span data-ttu-id="4bab5-121">**고려 사항:**</span><span class="sxs-lookup"><span data-stu-id="4bab5-121">**Considerations:**</span></span>  
  
-   <span data-ttu-id="4bab5-122">이벤트 선택 탭의 **StartTime** 및 **EndTime** 데이터 열에서 필터 조건을 설정할 경우 다음 사항을 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="4bab5-122">If you set filter conditions on the **StartTime** and **EndTime** data columns of the Events Selection tab, then make sure that:</span></span>  
  
    -   <span data-ttu-id="4bab5-123">입력한 날짜의 다음 `YYYY/MM/DD HH:mm:sec`형식과 같아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4bab5-123">The date you enter matches this format: `YYYY/MM/DD HH:mm:sec`.</span></span>  
  
         <span data-ttu-id="4bab5-124">또는</span><span class="sxs-lookup"><span data-stu-id="4bab5-124">-OR-</span></span>  
  
    -   <span data-ttu-id="4bab5-125">**일반 옵션** 대화 상자에서 **날짜 및 시간 값 표시에 국가별 설정 사용** 이 선택되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4bab5-125">**Use regional settings to display date and time values** is checked in the **General Options** dialog box.</span></span> <span data-ttu-id="4bab5-126">**일반 옵션** 대화 상자를 보려면 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] **도구** 메뉴에서 **옵션**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4bab5-126">To view the **General Options** dialog box, on the [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] **Tools** menu, click **Option**.</span></span>  
  
         <span data-ttu-id="4bab5-127">-그리고-</span><span class="sxs-lookup"><span data-stu-id="4bab5-127">-AND-</span></span>  
  
    -   <span data-ttu-id="4bab5-128">입력한 날짜가 1753년 1월 1일에서 9999년 12월 31일 사이여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4bab5-128">The date you enter is between January 1, 1753 and December 31, 9999.</span></span>  
  
-   <span data-ttu-id="4bab5-129">**osql** 유틸리티 또는 **sqlcmd** 유틸리티에서 이벤트를 추적하는 경우 항상 **%** 를 **TextData** 데이터 열의 필터에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="4bab5-129">If tracing events from the **osql** utility or from the **sqlcmd** utility, always append **%** to filters on the **TextData** data column.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4bab5-130">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4bab5-130">See Also</span></span>  
 [<span data-ttu-id="4bab5-131">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="4bab5-131">SQL Server Profiler</span></span>](sql-server-profiler.md)  
  
  
