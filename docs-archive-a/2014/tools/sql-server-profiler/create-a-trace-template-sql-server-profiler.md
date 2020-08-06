---
title: 추적 템플릿 만들기 (SQL Server Profiler) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- templates [SQL Server], traces
- trace templates [SQL Server]
- saving trace template
ms.assetid: 025868b0-3790-4cda-8757-5a58327bfba0
author: stevestein
ms.author: sstein
ms.openlocfilehash: 355f97c7fecd8a9e31f10de881d1ae6df3b8f122
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87727579"
---
# <a name="create-a-trace-template-sql-server-profiler"></a><span data-ttu-id="369b2-102">추적 템플릿 만들기(SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="369b2-102">Create a Trace Template (SQL Server Profiler)</span></span>
  <span data-ttu-id="369b2-103">이 항목에서는 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]을 사용하여 새 추적 템플릿을 만드는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="369b2-103">This topic describes how to create a new trace template by using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span>  
  
### <a name="to-create-a-trace-template"></a><span data-ttu-id="369b2-104">추적 템플릿을 만들려면</span><span class="sxs-lookup"><span data-stu-id="369b2-104">To create a trace template</span></span>  
  
1.  <span data-ttu-id="369b2-105">**파일** 메뉴에서 **템플릿**을 가리킨 다음 **새 템플릿**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="369b2-105">On the **File** menu, point to **Templates**, and then click **New Template**.</span></span>  
  
2.  <span data-ttu-id="369b2-106">**추적 템플릿 속성** 대화 상자의 **서버 유형 선택**목록에서 서버 유형을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="369b2-106">In the **Trace Template Properties** dialog box, select a server type from the **Select server type**list.</span></span>  
  
3.  <span data-ttu-id="369b2-107">**새 템플릿 이름** 상자에 템플릿 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="369b2-107">In the **New template name** box, enter a template name.</span></span>  
  
4.  <span data-ttu-id="369b2-108">필요에 따라 **기존 템플릿에서 새 템플릿 만들기**를 클릭한 다음 목록에서 템플릿을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="369b2-108">Optionally, click **Base new template on existing one**, and then select a template from the list.</span></span>  
  
     <span data-ttu-id="369b2-109">모든 이벤트, 데이터 열 및 필터는 처음에 선택한 템플릿에서 지정한 대로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="369b2-109">All events, data columns, and filters are initially set as specified in the selected template.</span></span>  
  
5.  <span data-ttu-id="369b2-110">필요에 따라 **선택한 서버 유형에 대한 기본 템플릿으로 사용**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="369b2-110">Optionally, click **Use as a default template for selected server type**.</span></span>  
  
6.  <span data-ttu-id="369b2-111">**이벤트 선택** 탭에서 이벤트, 데이터 열 또는 필터를 추가, 제거 또는 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="369b2-111">On the **Events Selection** tab, add, remove, or modify events, data columns, or filters.</span></span>  
  
7.  <span data-ttu-id="369b2-112">**이벤트 선택**탭에서 표 형태 컨트롤을 사용하여 다음과 같이 추적 파일에서 이벤트와 데이터 열을 추가하거나 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="369b2-112">On the **Events Selection**tab, use the grid control to add or remove events and data columns from the trace file as follows:</span></span>  
  
    -   <span data-ttu-id="369b2-113">이벤트를 추가하려면 **이벤트** 열의 해당 이벤트 범주를 확장한 다음 이벤트 이름을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="369b2-113">To add an event, expand the appropriate event category in the **Events** column, and then select the event name.</span></span>  
  
    -   <span data-ttu-id="369b2-114">이벤트를 추가할 때는 관련된 모든 데이터 열이 기본적으로 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="369b2-114">When you add an event, all relevant data columns are included by default.</span></span> <span data-ttu-id="369b2-115">추적에서 이벤트에 대한 데이터 열을 제거하려면 해당 이벤트에 대한 데이터 열의 확인란 선택을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="369b2-115">To remove a data column for an event from a trace, clear the check box in the data column for the event.</span></span>  
  
    -   <span data-ttu-id="369b2-116">필터를 추가하려면 데이터 열 이름을 클릭하고 **필터 편집** 대화 상자에 필터 조건을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="369b2-116">To add filters, click the data column name and specify the filter criteria in the **Edit Filter** dialog box.</span></span> <span data-ttu-id="369b2-117">또한 데이터 열 이름을 마우스 오른쪽 단추로 클릭하고 **열 필터 편집** 을 클릭하여 **필터 편집** 대화 상자를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="369b2-117">You can also right-click the data column name, and click **Edit Column Filter** to launch the **Edit Filter** dialog box.</span></span> <span data-ttu-id="369b2-118">**확인** 을 클릭하여 필터를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="369b2-118">Click **OK** to add the filter.</span></span>  
  
8.  <span data-ttu-id="369b2-119">**저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="369b2-119">Click **Save.**</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="369b2-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="369b2-120">See Also</span></span>  
 <span data-ttu-id="369b2-121">[추적 파일에 대해 이벤트 및 데이터 열 지정&#40;SQL Server Profiler&#41;](specify-events-and-data-columns-for-a-trace-file-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="369b2-121">[Specify Events and Data Columns for a Trace File &#40;SQL Server Profiler&#41;](specify-events-and-data-columns-for-a-trace-file-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="369b2-122">[실행 중인 추적으로부터 템플릿 파생&#40;SQL Server Profiler&#41;](derive-a-template-from-a-running-trace-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="369b2-122">[Derive a Template from a Running Trace &#40;SQL Server Profiler&#41;](derive-a-template-from-a-running-trace-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="369b2-123">[추적 파일 또는 추적 테이블에서 템플릿 파생&#40;SQL Server Profiler&#41;](derive-a-template-from-a-trace-file-or-trace-table-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="369b2-123">[Derive a Template from a Trace File or Trace Table &#40;SQL Server Profiler&#41;](derive-a-template-from-a-trace-file-or-trace-table-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="369b2-124">[SQL Server Profiler 템플릿 및 권한](sql-server-profiler-templates-and-permissions.md) </span><span class="sxs-lookup"><span data-stu-id="369b2-124">[SQL Server Profiler Templates and Permissions](sql-server-profiler-templates-and-permissions.md) </span></span>  
 [<span data-ttu-id="369b2-125">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="369b2-125">SQL Server Profiler</span></span>](sql-server-profiler.md)  
  
  
