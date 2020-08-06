---
title: 추적 파일에 대해 이벤트 및 데이터 열 지정(SQL Server Profiler) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- adding events
- traces [SQL Server], data columns
- deleting events
- removing events
- traces [SQL Server], events
ms.assetid: 7da715a3-2f03-4063-b6a4-20fd7b44e675
author: stevestein
ms.author: sstein
ms.openlocfilehash: ffb8639a187f1e7e091e382031886659bd47d7d5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87638476"
---
# <a name="specify-events-and-data-columns-for-a-trace-file-sql-server-profiler"></a><span data-ttu-id="3faa1-102">추적 파일에 대해 이벤트 및 데이터 열 지정(SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="3faa1-102">Specify Events and Data Columns for a Trace File (SQL Server Profiler)</span></span>
  <span data-ttu-id="3faa1-103">이 항목에서는 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]를 사용하여 추적에 대해 이벤트 클래스 및 데이터 열을 지정하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="3faa1-103">This topic describes how to specify event classes and data columns for traces by using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span>  
  
### <a name="to-specify-events-and-data-columns-for-a-trace"></a><span data-ttu-id="3faa1-104">추적에 대해 이벤트 및 데이터 열을 지정하려면</span><span class="sxs-lookup"><span data-stu-id="3faa1-104">To specify events and data columns for a trace</span></span>  
  
1.  <span data-ttu-id="3faa1-105">**추적 속성** 또는 **추적 템플릿 속성** 대화 상자에서 **이벤트 선택** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3faa1-105">On the **Trace Properties** or **Trace Template Properties** dialog box, click the **Events Selection** tab.</span></span>  
  
     <span data-ttu-id="3faa1-106">**이벤트 선택** 탭에는 표 형태 컨트롤이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3faa1-106">The **Events Selection** tab contains a grid control.</span></span> <span data-ttu-id="3faa1-107">표 형태 컨트롤은 추적 가능한 각 이벤트 클래스가 들어 있는 테이블입니다.</span><span class="sxs-lookup"><span data-stu-id="3faa1-107">The grid control is a table that contains each of the traceable event classes.</span></span> <span data-ttu-id="3faa1-108">테이블에는 각 이벤트 클래스에 대한 행이 하나씩 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3faa1-108">The table contains one row for each event class.</span></span> <span data-ttu-id="3faa1-109">이벤트 클래스는 연결한 서버의 유형 및 버전에 따라 약간 다를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3faa1-109">The event classes can differ slightly depending on the type and version of server to which you are connected.</span></span> <span data-ttu-id="3faa1-110">이벤트 클래스는 표의 **이벤트**열에서 식별되며 이벤트 범주별로 그룹화됩니다.</span><span class="sxs-lookup"><span data-stu-id="3faa1-110">The event classes are identified in the **Events**column of the grid and are grouped by event category.</span></span> <span data-ttu-id="3faa1-111">나머지 열은 각 이벤트 클래스에 대해 반환할 수 있는 데이터 열을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="3faa1-111">The remaining columns list the data columns that can be returned for each event class.</span></span>  
  
2.  <span data-ttu-id="3faa1-112">**이벤트 선택**탭에서 표 형태 컨트롤을 사용하여 이벤트와 데이터 열을 추적 파일에서 추가하거나 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="3faa1-112">On the **Events Selection**tab, use the grid control to add or remove events and data columns from the trace file.</span></span>  
  
3.  <span data-ttu-id="3faa1-113">추적에서 이벤트를 제거하려면 각 이벤트 클래스에 대한 **이벤트** 열의 확인란을 선택 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="3faa1-113">To remove events from the trace, clear the check box in the **Events** column for each event class.</span></span>  
  
4.  <span data-ttu-id="3faa1-114">추적에 이벤트를 포함하려면 각 이벤트 클래스에 대한 **이벤트** 열에서 확인란을 선택하거나 이벤트에 해당하는 데이터 열을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3faa1-114">To include events in a trace, check the box in the **Events** column for each event class, or check a data column that corresponds to an event.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="3faa1-115">추적에 시스템 모니터 또는 성능 모니터 데이터와의 상관 관계를 지정하려면 **Start Time** 및 **End Time** 데이터 열이 모두 추적에 포함되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3faa1-115">If the trace is going be correlated with System Monitor or Performance Monitor data, both **Start Time** and **End Time** data columns must be included in the trace.</span></span>  
  
 <span data-ttu-id="3faa1-116">이벤트 클래스를 포함할 때 이벤트에 해당되는 확인란을 선택한 경우 연관된 데이터 열도 모두 추적에 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="3faa1-116">When you include an event class, every associated data column is also included to the trace, if you have checked the box corresponding to an event.</span></span> <span data-ttu-id="3faa1-117">특정 열에 대해 확인란을 선택한 경우에는 해당 열만 추적에 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="3faa1-117">If you checked the box for a particular column, only that column is included in the trace.</span></span>  
  
1.  <span data-ttu-id="3faa1-118">이벤트 클래스에서 데이터 열을 제거하려면 이벤트 클래스 행의 데이터 열에서 확인란 선택을 취소하거나 열 머리글을 마우스 오른쪽 단추로 클릭하고 **열 선택 취소** 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3faa1-118">To remove data columns from an event class, clear the check boxes from the data column in the event class row, or right-click on the column header and select the **Deselect column** option.</span></span>  
  
2.  <span data-ttu-id="3faa1-119">필요에 따라 추적에 필터를 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="3faa1-119">Optionally, apply filters to the trace.</span></span> <span data-ttu-id="3faa1-120">자세한 내용은 [추적에서의 이벤트 필터링&#40;SQL Server Profiler&#41;](filter-events-in-a-trace-sql-server-profiler.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3faa1-120">For more information, see [Filter Events in a Trace &#40;SQL Server Profiler&#41;](filter-events-in-a-trace-sql-server-profiler.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3faa1-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3faa1-121">See Also</span></span>  
 [<span data-ttu-id="3faa1-122">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="3faa1-122">SQL Server Profiler</span></span>](sql-server-profiler.md)  
  
  
