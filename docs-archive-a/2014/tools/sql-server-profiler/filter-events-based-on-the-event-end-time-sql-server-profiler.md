---
title: 이벤트 종료 시간 기반의 이벤트 필터링(SQL Server Profiler) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- event end times [SQL Server]
- filters [SQL Server], traces
- traces [SQL Server], filters
- traces [SQL Server], events
ms.assetid: 74628f9e-2d39-496a-a443-0a3887db223d
author: stevestein
ms.author: sstein
ms.openlocfilehash: d25d8e1adbd95f48d88fd1516c48dcc0f8374a7c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741491"
---
# <a name="filter-events-based-on-the-event-end-time-sql-server-profiler"></a><span data-ttu-id="c3d9a-102">이벤트 종료 시간 기반의 이벤트 필터링(SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="c3d9a-102">Filter Events Based on the Event End Time (SQL Server Profiler)</span></span>
  <span data-ttu-id="c3d9a-103">이 항목에서는 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]를 사용하여 이벤트 종료 시간을 기반으로 추적 이벤트를 필터링하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="c3d9a-103">This topic describes how to filter trace events based on the event ending time by using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span>  
  
### <a name="to-filter-events-based-on-the-event-end-time"></a><span data-ttu-id="c3d9a-104">이벤트 종료 시간을 기반으로 이벤트를 필터링하려면</span><span class="sxs-lookup"><span data-stu-id="c3d9a-104">To filter events based on the event end time</span></span>  
  
1.  <span data-ttu-id="c3d9a-105">**파일** 메뉴에서 **새 추적**을 클릭한 다음 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="c3d9a-105">On the **File** menu, click **New Trace**, and then connect to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
     <span data-ttu-id="c3d9a-106">**추적 속성**대화 상자가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c3d9a-106">The **Trace Properties**dialog box appears.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="c3d9a-107">**연결한 후 즉시 추적 시작**을 선택한 경우에는 **추적 속성**대화 상자가 나타나지 않고 추적이 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="c3d9a-107">If **Start tracing immediately after making connection**is selected, the **Trace Properties**dialog box fails to appear and the trace begins instead.</span></span> <span data-ttu-id="c3d9a-108">이 설정을 해제하려면 **도구**메뉴에서 **옵션**을 클릭한 다음 **연결한 후 즉시 추적 시작** 확인란의 선택을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="c3d9a-108">To turn off this setting, on the **Tools**menu, click **Options**, and clear the **Start tracing immediately after making connection** check box.</span></span>  
  
2.  <span data-ttu-id="c3d9a-109">**추적 속성** 대화 상자에서 **일반** 탭이 선택되어 있는지 확인하고 **추적 이름** 입력란에 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="c3d9a-109">In the **Trace Properties** dialog box, make sure the **General** tab is selected, and enter a name in the **TraceName** text box.</span></span>  
  
3.  <span data-ttu-id="c3d9a-110">**템플릿 사용**목록에서 추적 템플릿을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c3d9a-110">From the **Use the template**list, select a trace template.</span></span>  
  
4.  <span data-ttu-id="c3d9a-111">필요에 따라 추적 결과를 저장할 대상 파일이나 테이블을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c3d9a-111">Optionally, specify a destination file or table in which to save the trace results.</span></span>  
  
5.  <span data-ttu-id="c3d9a-112">**이벤트 선택**탭에서 **EndTime** 데이터 열을 클릭하여 **필터 편집** 대화 상자를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="c3d9a-112">On the **Events Selection**tab, click the **EndTime** data column to launch the **Edit Filter** dialog box.</span></span> <span data-ttu-id="c3d9a-113">열 제목을 마우스 오른쪽 단추로 클릭한 다음 **열 필터 편집**을 선택할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c3d9a-113">You can also right-click the column heading, and select **Edit Column Filter**.</span></span>  
  
6.  <span data-ttu-id="c3d9a-114">보다 **큼** 또는 **보다 작음**을 확장 하 고 `datetime` 비교 연산자 아래에 나타나는 필드에 값을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3d9a-114">Expand **Greater than** or **Less than**, and enter a `datetime`value in the field that appears beneath the comparison operator.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3d9a-115">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c3d9a-115">See Also</span></span>  
 <span data-ttu-id="c3d9a-116">[SQL Server 프로파일러](sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="c3d9a-116">[SQL Server Profiler](sql-server-profiler.md) </span></span>  
 [<span data-ttu-id="c3d9a-117">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="c3d9a-117">SQL Server Profiler</span></span>](sql-server-profiler.md)  
  
  
