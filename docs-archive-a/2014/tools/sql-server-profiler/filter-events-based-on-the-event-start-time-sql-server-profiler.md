---
title: 이벤트 시작 시간을 기준으로 이벤트 필터링(SQL Server Profiler) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- event start times [SQL Server]
- filters [SQL Server], traces
- traces [SQL Server], filters
- traces [SQL Server], events
ms.assetid: e965579e-d006-41a3-89ec-cfd5398c67d2
author: stevestein
ms.author: sstein
ms.openlocfilehash: 7f652952ec6706580b876e3e9a20f96e62598f81
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739027"
---
# <a name="filter-events-based-on-the-event-start-time-sql-server-profiler"></a><span data-ttu-id="fd785-102">이벤트 시작 시간을 기준으로 이벤트 필터링(SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="fd785-102">Filter Events Based on the Event Start Time (SQL Server Profiler)</span></span>
  <span data-ttu-id="fd785-103">이 항목에서는 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]를 사용하여 이벤트 시작 시간을 기준으로 추적 이벤트를 필터링하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="fd785-103">This topic describes how to filter trace events based on the event start time by using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span>  
  
### <a name="to-filter-an-event-based-on-the-event-start-time"></a><span data-ttu-id="fd785-104">이벤트 시작 시간을 기준으로 이벤트를 필터링하려면</span><span class="sxs-lookup"><span data-stu-id="fd785-104">To filter an event based on the event start time</span></span>  
  
1.  <span data-ttu-id="fd785-105">**파일** 메뉴에서 **새 추적**을 클릭한 다음 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="fd785-105">On the **File** menu, click **New Trace**, and then connect to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
     <span data-ttu-id="fd785-106">**추적 속성**대화 상자가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="fd785-106">The **Trace Properties**dialog box appears.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="fd785-107">**연결한 후 즉시 추적 시작**을 선택한 경우에는 **추적 속성**대화 상자가 나타나지 않고 추적이 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="fd785-107">If **Start tracing immediately after making connection**is selected, the **Trace Properties**dialog box fails to appear, and the trace begins instead.</span></span> <span data-ttu-id="fd785-108">이 설정을 해제하려면 **도구**메뉴에서 **옵션**을 클릭한 다음 **연결한 후 즉시 추적 시작** 확인란의 선택을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="fd785-108">To turn off this setting, on the **Tools**menu, click **Options**, and clear the **Start tracing immediately after making connection** check box.</span></span>  
  
2.  <span data-ttu-id="fd785-109">**추적 이름** 입력란에 추적의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="fd785-109">In the **Trace name** box, type a name for the trace.</span></span>  
  
3.  <span data-ttu-id="fd785-110">**템플릿 사용**이름 목록에서 추적 템플릿을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="fd785-110">In the **Use the template**name list, select a trace template.</span></span>  
  
4.  <span data-ttu-id="fd785-111">필요에 따라 추적 결과의 저장 대상을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="fd785-111">Optionally specify a destination for the trace results.</span></span>  
  
5.  <span data-ttu-id="fd785-112">**이벤트 선택**탭에서 **StartTime** 열 머리글을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="fd785-112">On the **Events Selection**tab, click the **StartTime** column heading.</span></span> <span data-ttu-id="fd785-113">열 머리글을 마우스 오른쪽 단추로 클릭한 다음 **열 필터 편집** 을 클릭하여 **필터 편집** 대화 상자를 시작할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fd785-113">You can also right-click the column heading, and then click **Edit Column Filter** to launch the **Edit Filter** dialog box.</span></span>  
  
6.  <span data-ttu-id="fd785-114">보다 **큼** 또는 **보다 작음**을 확장 한 다음 `datetime` 비교 연산자 아래에 나타나는 필드에 값을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="fd785-114">Expand **Greater than** or **Less than**, and then enter a `datetime` value in the field that appears beneath the comparison operator.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd785-115">참고 항목</span><span class="sxs-lookup"><span data-stu-id="fd785-115">See Also</span></span>  
 [<span data-ttu-id="fd785-116">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="fd785-116">SQL Server Profiler</span></span>](sql-server-profiler.md)  
  
  
