---
title: 추적 템플릿 수정 (SQL Server Profiler) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- templates [SQL Server], traces
- trace templates [SQL Server]
- modifying traces
ms.assetid: b81df2a1-e202-43d8-92b0-0beb145f0116
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 2a93baedb1875ac740e74065ae7188f9b576e083
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647187"
---
# <a name="modify-a-trace-template-sql-server-profiler"></a><span data-ttu-id="9c289-102">추적 템플릿 수정(SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="9c289-102">Modify a Trace Template (SQL Server Profiler)</span></span>
  <span data-ttu-id="9c289-103">이 항목에서는 [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)]를 사용하여 추적 템플릿을 수정하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="9c289-103">This topic describes how to modify a trace template by using [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)].</span></span>  
  
### <a name="to-modify-a-trace-template"></a><span data-ttu-id="9c289-104">추적 템플릿을 수정하려면</span><span class="sxs-lookup"><span data-stu-id="9c289-104">To modify a trace template</span></span>  
  
1.  <span data-ttu-id="9c289-105">**파일** 메뉴에서 **템플릿**- **템플릿 편집**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9c289-105">On the **File** menu, point to **Templates**, and then click **Edit Template**.</span></span>  
  
2.  <span data-ttu-id="9c289-106">**추적 템플릿 속성** 대화 상자의 **일반** 탭에서 서버 유형과 템플릿 이름을 수정하거나 서버 유형에 맞는 기본 템플릿을 사용하도록 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="9c289-106">In the **Trace Template Properties** dialog box, on the **General** tab, you can modify the server type and template name, or choose to use a default template for the server type.</span></span>  
  
3.  <span data-ttu-id="9c289-107">**이벤트 선택**탭에서 표 형태 컨트롤을 사용 하 여 다음과 같이 추적 파일에서 이벤트와 데이터 열을 추가 하거나 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c289-107">On the **Events Selection**tab, use the grid control to add or remove events and data columns from the trace file as follows.</span></span>  
  
    -   <span data-ttu-id="9c289-108">이벤트를 추가하려면 **이벤트** 열의 해당 이벤트 범주를 확장한 다음 이벤트 이름을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="9c289-108">To add an event, expand the appropriate event category in the **Events** column, and then select the event name.</span></span>  
  
    -   <span data-ttu-id="9c289-109">이벤트를 추가할 때는 관련된 모든 데이터 열이 기본적으로 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="9c289-109">When you add an event, all relevant data columns are included by default.</span></span> <span data-ttu-id="9c289-110">추적에서 이벤트에 대한 데이터 열을 제거하려면 해당 이벤트에 대한 데이터 열의 확인란 선택을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="9c289-110">To remove a data column for an event from a trace, clear the check box in the data column for the event.</span></span>  
  
    -   <span data-ttu-id="9c289-111">필터를 추가하려면 데이터 열 이름을 클릭하고 **필터 편집** 대화 상자에 필터 조건을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="9c289-111">To add filters, click the data column name and specify the filter criteria in the **Edit Filter** dialog box.</span></span> <span data-ttu-id="9c289-112">또한 데이터 열 이름을 마우스 오른쪽 단추로 클릭하고 **열 필터 편집** 을 클릭하여 **필터 편집** 대화 상자를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9c289-112">You can also right-click the data column name, and click **Edit Column Filter** to launch the **Edit Filter** dialog box.</span></span> <span data-ttu-id="9c289-113">**확인** 을 클릭하여 필터를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="9c289-113">Click **OK** to add the filter.</span></span>  
  
4.  <span data-ttu-id="9c289-114">**저장**또는 **다른 이름으로 저장**을 클릭하여 추적 템플릿을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="9c289-114">Click **Save**, or click **Save As**to save the trace template under another name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c289-115">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9c289-115">See Also</span></span>  
 <span data-ttu-id="9c289-116">[추적 파일 &#40;SQL Server Profiler&#41;에 대 한 이벤트 및 데이터 열을 지정 합니다.](../tools/sql-server-profiler/specify-events-and-data-columns-for-a-trace-file-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="9c289-116">[Specify Events and Data Columns for a Trace File &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/specify-events-and-data-columns-for-a-trace-file-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="9c289-117">[실행 중인 추적으로부터 템플릿 파생&#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/derive-a-template-from-a-running-trace-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="9c289-117">[Derive a Template from a Running Trace &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/derive-a-template-from-a-running-trace-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="9c289-118">[추적 파일 또는 추적 테이블에서 템플릿 파생&#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/derive-a-template-from-a-trace-file-or-trace-table-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="9c289-118">[Derive a Template from a Trace File or Trace Table &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/derive-a-template-from-a-trace-file-or-trace-table-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="9c289-119">[SQL Server Profiler 템플릿 및 권한](../tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md) </span><span class="sxs-lookup"><span data-stu-id="9c289-119">[SQL Server Profiler Templates and Permissions](../tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md) </span></span>  
 [<span data-ttu-id="9c289-120">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="9c289-120">SQL Server Profiler</span></span>](../tools/sql-server-profiler/sql-server-profiler.md)  
  
  
