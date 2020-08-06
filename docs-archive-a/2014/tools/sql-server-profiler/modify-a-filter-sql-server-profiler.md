---
title: 필터 수정 (SQL Server Profiler) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- filters [SQL Server], modifying
- modifying filters, modifying
- filters [SQL Server], traces
ms.assetid: 8b317813-4918-4485-b930-77b1951aa00c
author: stevestein
ms.author: sstein
ms.openlocfilehash: 5a7bab18952820a3dc49c9479797a411521f8e71
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649880"
---
# <a name="modify-a-filter-sql-server-profiler"></a><span data-ttu-id="47d8d-102">필터 수정(SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="47d8d-102">Modify a Filter (SQL Server Profiler)</span></span>
  <span data-ttu-id="47d8d-103">추적 정의가 포함된 추적 템플릿에 필터를 추가하여 추적에서 수집하는 이벤트의 수를 제한할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="47d8d-103">You add filters to trace templates, which contain the trace definitions, to limit the number of events that are gathered by a trace.</span></span> <span data-ttu-id="47d8d-104">수집된 이벤트의 수를 제한하면 추적의 성능 효과가 저하될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="47d8d-104">Limiting the number of events gathered can reduce the performance effects of tracing.</span></span> <span data-ttu-id="47d8d-105">추적 템플릿에 필터를 설정했고 추적에서 필요한 유형의 정보를 수집하고 있지 않는 것을 확인하는 경우 해당 필터를 편집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="47d8d-105">If you set filters for a trace template and find that the trace is not gathering the kind of information that you need, you can edit the filter.</span></span>  
  
### <a name="to-modify-a-filter"></a><span data-ttu-id="47d8d-106">필터를 수정하려면</span><span class="sxs-lookup"><span data-stu-id="47d8d-106">To modify a filter</span></span>  
  
1.  <span data-ttu-id="47d8d-107">[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]에서 수정하려는 추적 필터에 대한 템플릿을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="47d8d-107">In [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)], open the template for the trace filter that you want to modify.</span></span> <span data-ttu-id="47d8d-108">**파일** 메뉴에서 **템플릿**을 클릭한 다음 **템플릿 편집**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="47d8d-108">On the **File** menu, click **Templates**, and then choose **Edit Template**.</span></span>  
  
2.  <span data-ttu-id="47d8d-109">**추적 템플릿 속성** 대화 상자의 **일반** 탭에 있는 **템플릿 이름 선택** 목록에서 템플릿을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="47d8d-109">In the **General** tab of the **Trace Template Properties** dialog, select a template from the **Select template name** list.</span></span>  
  
3.  <span data-ttu-id="47d8d-110">**이벤트 선택** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="47d8d-110">Click the **Events Selection** tab.</span></span>  
  
     <span data-ttu-id="47d8d-111">**이벤트 선택** 탭에는 표 형태 컨트롤이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="47d8d-111">The **Events Selection** tab contains a grid control.</span></span> <span data-ttu-id="47d8d-112">표 형태 컨트롤은 추적 가능한 각 이벤트 클래스가 들어 있는 테이블입니다.</span><span class="sxs-lookup"><span data-stu-id="47d8d-112">The grid control is a table that contains each of the traceable event classes.</span></span> <span data-ttu-id="47d8d-113">테이블에는 각 이벤트 클래스에 대한 행이 하나씩 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="47d8d-113">The table contains one row for each event class.</span></span> <span data-ttu-id="47d8d-114">이벤트 클래스는 사용자가 연결된 서버의 유형 및 버전에 따라 약간 다를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="47d8d-114">The event classes may differ slightly, depending on the type and version of server to which you are connected.</span></span> <span data-ttu-id="47d8d-115">이벤트 클래스는 표의 **이벤트**열에서 식별되며 이벤트 범주별로 그룹화됩니다.</span><span class="sxs-lookup"><span data-stu-id="47d8d-115">The event classes are identified in the **Events**column of the grid and are grouped by event category.</span></span> <span data-ttu-id="47d8d-116">나머지 열은 각 이벤트 클래스에 대해 반환할 수 있는 데이터 열을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="47d8d-116">The remaining columns list the data columns that can be returned for each event class.</span></span>  
  
4.  <span data-ttu-id="47d8d-117">**열 필터**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="47d8d-117">Click **Column Filters**.</span></span>  
  
5.  <span data-ttu-id="47d8d-118">**필터 편집** 대화 상자에서 편집하려는 비교 연산자 옆에 있는 값을 클릭하고 새 값을 입력하거나 값을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="47d8d-118">In the **Edit Filter** dialog box, click the value next to the comparison operator that you want to edit, and type the new value or delete a value.</span></span> <span data-ttu-id="47d8d-119">다른 필터를 추가할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="47d8d-119">You can also add additional filters.</span></span>  
  
6.  <span data-ttu-id="47d8d-120">**확인** 을 클릭하여 템플릿을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="47d8d-120">Click **OK** and save the template.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47d8d-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="47d8d-121">See Also</span></span>  
 [<span data-ttu-id="47d8d-122">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="47d8d-122">SQL Server Profiler</span></span>](sql-server-profiler.md)  
  
  
