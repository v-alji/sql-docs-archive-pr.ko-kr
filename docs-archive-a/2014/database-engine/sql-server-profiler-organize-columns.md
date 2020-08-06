---
title: 열 SQL Server Profiler 구성 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- sql12.pro.organize.columns.f1
ms.assetid: bf5674f4-da5e-43f9-aeb2-76ca37993790
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: b63c2f7d882bac05fc6baf10614170ec23125c12
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736718"
---
# <a name="sql-server-profiler---organize-columns"></a><span data-ttu-id="4ec41-102">SQL Server 프로파일러 - 열 구성</span><span class="sxs-lookup"><span data-stu-id="4ec41-102">SQL Server Profiler - Organize Columns</span></span>
  <span data-ttu-id="4ec41-103">**열 구성** 대화 상자를 사용하여 데이터 열을 선택한 후 추적 파일에 표시되는 이벤트를 그룹화하거나 집계하면 큰 추적 파일 또는 테이블을 쉽게 확인 및 분석할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4ec41-103">Use the **Organize Columns** dialog box to select data columns for grouping or aggregating events that are displayed in a trace, which makes large trace files or tables easier to view and analyze.</span></span>  
  
 <span data-ttu-id="4ec41-104">집계할 경우 해당 이벤트 클래스 형식의 추적에 포함된 모든 이벤트가 이동 또는 축소됩니다.</span><span class="sxs-lookup"><span data-stu-id="4ec41-104">Aggregating moves and collapses all events in the trace under its respective event class type.</span></span> <span data-ttu-id="4ec41-105">**+** 이벤트 클래스 이름의 왼쪽에 더하기 기호 ()가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="4ec41-105">A plus sign (**+**) appears to the left of the event class name.</span></span> <span data-ttu-id="4ec41-106">더하기 기호를 클릭하면 이벤트 클래스가 확장되어 해당 형식의 모든 이벤트가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="4ec41-106">Clicking the plus sign expands the event class so you can view all events of that type.</span></span>  
  
 <span data-ttu-id="4ec41-107">그룹화하면 추적 창 화면에 이벤트 클래스가 형식별로 분류되어 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="4ec41-107">Grouping organizes all event classes of a specific type together in the trace window display.</span></span> <span data-ttu-id="4ec41-108">그러나 각 이벤트 클래스 형식의 이벤트는 축소되어 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4ec41-108">However, the events are not collapsed under the event class type.</span></span>  
  
 <span data-ttu-id="4ec41-109">추적 창 화면에서 이벤트를 그룹화하거나 집계하면, 그룹화 또는 집계하도록 선택한 열은 창에서 고정되어 있지만 오른쪽 또는 왼쪽으로 스크롤하여 다른 데이터 열을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4ec41-109">When you group or aggregate events in a trace window display, the columns selected for grouping or aggregating remain fixed in the display window, but you can scroll to the right or left to view all other data columns.</span></span>  
  
 <span data-ttu-id="4ec41-110">이 대화 상자에 액세스하려면 기존 추적 파일 또는 테이블을 열고 [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] **파일** 메뉴에서 **파일**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4ec41-110">To access this dialog box, open an existing trace file or table, and click **Properties** on the [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] **File** menu.</span></span> <span data-ttu-id="4ec41-111">**추적 속성** 대화 상자에서 **이벤트 선택** 탭을 클릭한 다음 **열 구성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4ec41-111">In the **Trace Properties** dialog box, click the **Events Selection** tab, and then click **Organize Columns**.</span></span> <span data-ttu-id="4ec41-112">또한 새 추적을 만들 때 **이벤트 선택** 탭에서 **열 구성** 을 클릭해도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4ec41-112">You can also click **Organize Columns** on the **Events Selection** tab when you are creating a new trace.</span></span>  
  
## <a name="options"></a><span data-ttu-id="4ec41-113">옵션</span><span class="sxs-lookup"><span data-stu-id="4ec41-113">Options</span></span>  
 <span data-ttu-id="4ec41-114">**그룹**</span><span class="sxs-lookup"><span data-stu-id="4ec41-114">**Groups**</span></span>  
 <span data-ttu-id="4ec41-115">추적 창에서 이벤트 클래스를 그룹화하거나 집계하려면 **그룹** 아래에 있는 데이터 열 이름을 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="4ec41-115">Move data column names under **Groups** to group or aggregate event classes in the trace window.</span></span>  
  
 <span data-ttu-id="4ec41-116">이벤트를 집계하려면 데이터 열을 하나씩 **그룹**으로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="4ec41-116">To aggregate events, move one data column into **Groups**.</span></span> <span data-ttu-id="4ec41-117">그러면 추적 창 화면의 이벤트 형식 이름 아래에 있는 특정 형식의 모든 이벤트가 축소됩니다.</span><span class="sxs-lookup"><span data-stu-id="4ec41-117">This causes all events of a specific type to be collapsed under event class type name in the trace window display.</span></span> <span data-ttu-id="4ec41-118">**+** 이벤트 클래스 이름의 왼쪽에 더하기 기호 ()가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="4ec41-118">A plus sign (**+**) appears to the left of the event class name.</span></span> <span data-ttu-id="4ec41-119">이벤트 클래스 형식을 확장하고 모든 이벤트를 표시하려면 더하기 기호를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4ec41-119">Click the plus sign to expand the event class type and view all events.</span></span> <span data-ttu-id="4ec41-120">**보기** 메뉴에서 **집계 보기** 또는 **그룹화 보기** 를 클릭하여 집계 및 그룹화 옵션을 설정하거나 해제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4ec41-120">You can set aggregation and grouping on and off by clicking **Aggregated View** or **Grouped View** on the **View** menu.</span></span>  
  
 <span data-ttu-id="4ec41-121">이벤트를 그룹화하려면 둘 이상의 데이터 열을 **그룹**으로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="4ec41-121">To group events, move more than one data column into **Groups**.</span></span> <span data-ttu-id="4ec41-122">그러면 추적 창 화면에서 특정 형식의 모든 이벤트가 그룹화되지만 각 이벤트 클래스 형식 이름 아래에 있는 이벤트는 축소되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4ec41-122">This causes all events of a specific type to be grouped together in the trace window display, but does not collapse the events under each event class type name.</span></span> <span data-ttu-id="4ec41-123">보기 메뉴에서 **그룹화 보기** 를 클릭하여 그룹화된 보기와 그룹화되지 않은 보기 간에 전환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4ec41-123">You can switch back and forth between a grouped view and an ungrouped view by clicking **Grouped View** on the View menu.</span></span> <span data-ttu-id="4ec41-124">데이터 열을 두 개 이상 **그룹**으로 이동한 경우에는 **집계 보기** 로 전환할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4ec41-124">When more than one data column is moved into **Groups**, the option to switch to **Aggregated View** is not available.</span></span>  
  
 <span data-ttu-id="4ec41-125">**열**</span><span class="sxs-lookup"><span data-stu-id="4ec41-125">**Columns**</span></span>  
 <span data-ttu-id="4ec41-126">**그룹**으로 이동할 수 있는 데이터 열의 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="4ec41-126">List of data columns available to move into **Groups**.</span></span> <span data-ttu-id="4ec41-127">열 왼쪽에 있는 더하기 기호 ( **+** )를 클릭 **Columns** 하 여 목록을 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="4ec41-127">Click the plus sign (**+**) to the left of **Columns** to expand the list.</span></span>  
  
 <span data-ttu-id="4ec41-128">**최대**</span><span class="sxs-lookup"><span data-stu-id="4ec41-128">**Up**</span></span>  
 <span data-ttu-id="4ec41-129">데이터 열을 선택한 다음 **위로** 를 클릭하여 데이터 열을 **그룹**으로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="4ec41-129">After selecting a data column, click **Up** to move data columns up into **Groups**.</span></span> <span data-ttu-id="4ec41-130">**위로** 를 클릭하여 추적 창 화면에서 열이 표시되는 순서를 다시 정렬할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4ec41-130">You can also click **Up** to rearrange the display of columns in the trace window display.</span></span>  
  
 <span data-ttu-id="4ec41-131">**아래로**</span><span class="sxs-lookup"><span data-stu-id="4ec41-131">**Down**</span></span>  
 <span data-ttu-id="4ec41-132">데이터 열을 선택한 다음 **아래로** 를 클릭하여 데이터 열을 **그룹**밖으로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="4ec41-132">After selecting a data column, click **Down** to move data columns out of **Groups**.</span></span> <span data-ttu-id="4ec41-133">**아래로** 를 클릭하여 추적 창 화면에서 열이 표시되는 순서를 다시 정렬할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4ec41-133">You can also click **Down** to rearrange the display of columns in the trace window display.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ec41-134">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4ec41-134">See Also</span></span>  
 <span data-ttu-id="4ec41-135">[추적 &#40;SQL Server Profiler에 표시 되는 열 구성&#41;](../tools/sql-server-profiler/organize-columns-displayed-in-a-trace-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="4ec41-135">[Organize Columns Displayed in a Trace &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/organize-columns-displayed-in-a-trace-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="4ec41-136">[추적 &#40;SQL Server Profiler를 만듭니다&#41;](../tools/sql-server-profiler/create-a-trace-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="4ec41-136">[Create a Trace &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/create-a-trace-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="4ec41-137">[추적 템플릿 만들기&#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/create-a-trace-template-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="4ec41-137">[Create a Trace Template &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/create-a-trace-template-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="4ec41-138">[SQL Server Profiler &#40;추적 파일을 엽니다&#41;](../tools/sql-server-profiler/open-a-trace-file-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="4ec41-138">[Open a Trace File &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/open-a-trace-file-sql-server-profiler.md) </span></span>  
 [<span data-ttu-id="4ec41-139">추적 테이블 열기&#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="4ec41-139">Open a Trace Table &#40;SQL Server Profiler&#41;</span></span>](../tools/sql-server-profiler/open-a-trace-table-sql-server-profiler.md)  
  
  
