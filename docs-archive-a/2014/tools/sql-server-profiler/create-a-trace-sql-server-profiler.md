---
title: 추적 만들기 (SQL Server Profiler) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- traces [SQL Server], creating
ms.assetid: 0302fa6d-d2b5-43fe-ad70-7a337575b112
author: stevestein
ms.author: sstein
ms.openlocfilehash: 7d73333bbf0ba985ed4952e03584b4e4c130ab6f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87727596"
---
# <a name="create-a-trace-sql-server-profiler"></a><span data-ttu-id="58b15-102">추적 만들기(SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="58b15-102">Create a Trace (SQL Server Profiler)</span></span>
  <span data-ttu-id="58b15-103">이 항목에서는 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 를 사용하여 추적을 만드는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="58b15-103">This topic describes how to use [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] to create a trace.</span></span>  
  
### <a name="to-create-a-trace"></a><span data-ttu-id="58b15-104">추적 만들기</span><span class="sxs-lookup"><span data-stu-id="58b15-104">To create a trace</span></span>  
  
1.  <span data-ttu-id="58b15-105">**파일** 메뉴에서 **새 추적**을 클릭한 다음 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="58b15-105">On the **File** menu, click **New Trace**, and connect to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
     <span data-ttu-id="58b15-106">**추적 속성** 대화 상자가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="58b15-106">The **Trace Properties** dialog box appears.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="58b15-107">**연결한 후 즉시 추적 시작** 을 선택한 경우에는 **추적 속성** 대화 상자가 나타나지 않고 추적이 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="58b15-107">The **Trace Properties** dialog box fails to appear, and the trace begins instead, if **Start tracing immediately after making connection** is selected.</span></span> <span data-ttu-id="58b15-108">이 설정을 해제하려면 **도구**메뉴에서 **옵션**을 클릭한 다음 **연결한 후 즉시 추적 시작** 확인란의 선택을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="58b15-108">To turn off this setting, on the **Tools**menu, click **Options**, and clear the **Start tracing immediately after making connection** check box.</span></span>  
  
2.  <span data-ttu-id="58b15-109">**추적 이름** 입력란에 추적의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="58b15-109">In the **Trace name** box, type a name for the trace.</span></span>  
  
3.  <span data-ttu-id="58b15-110">**템플릿 사용** 목록에서 추적의 기반이 되는 추적 템플릿을 선택하거나 템플릿을 사용하지 않을 경우 **비어 있음** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="58b15-110">In the **Use the template** list, select a trace template on which to base the trace, or select **Blank** if you do not want to use a template.</span></span>  
  
4.  <span data-ttu-id="58b15-111">추적 결과를 저장하려면 다음 중 하나를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="58b15-111">To save the trace results, do one of the following:</span></span>  
  
    -   <span data-ttu-id="58b15-112">**파일에 저장**을 클릭하면 추적이 파일에 캡처됩니다.</span><span class="sxs-lookup"><span data-stu-id="58b15-112">Click **Save to file**to capture the trace to a file.</span></span> <span data-ttu-id="58b15-113">**최대 파일 크기 설정**에 대한 값을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="58b15-113">Specify a value for **Set maximum file size**.</span></span> <span data-ttu-id="58b15-114">기본값은 5MB입니다.</span><span class="sxs-lookup"><span data-stu-id="58b15-114">The default value is 5 megabytes (MB).</span></span>  
  
         <span data-ttu-id="58b15-115">**파일 롤오버 사용** 을 선택하여 최대 파일 크기에 도달할 때 자동으로 새 파일을 만들 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="58b15-115">Optionally, select **Enable file rollover** to automatically create new files when the maximum file size is reached.</span></span> <span data-ttu-id="58b15-116">**서버에서 추적 데이터 처리**를 선택하면 클라이언트 애플리케이션 대신 추적을 실행하는 서비스에서 추적 데이터를 처리하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="58b15-116">You can also optionally select **Server processes trace data**, which causes the service that is running the trace to process trace data instead of the client application.</span></span> <span data-ttu-id="58b15-117">서버에서 추적 데이터를 처리하는 경우 스트레스 상태에서도 이벤트를 건너뛰지 않지만 서버 성능은 저하될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="58b15-117">When the server processes trace data, no events are skipped even under stress conditions, but server performance may be affected.</span></span>  
  
    -   <span data-ttu-id="58b15-118">**테이블에 저장** 을 클릭하여 추적을 데이터베이스 테이블에 캡처합니다.</span><span class="sxs-lookup"><span data-stu-id="58b15-118">Click **Save to table** to capture the trace to a database table.</span></span>  
  
         <span data-ttu-id="58b15-119">필요에 따라 **최대 행 수 설정**을 클릭하고 값을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="58b15-119">Optionally, click **Set maximum rows**, and specify a value.</span></span>  
  
    > [!CAUTION]  
    >  <span data-ttu-id="58b15-120">추적 결과를 파일이나 테이블에 저장하지 않아도 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 가 열려 있으면 추적을 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="58b15-120">When you do not save the trace results to a file or table, you can view the trace while [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] is open.</span></span> <span data-ttu-id="58b15-121">그러나 추적을 중지하고 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]를 닫으면 추적 결과가 손실됩니다.</span><span class="sxs-lookup"><span data-stu-id="58b15-121">However, you lose the trace results after you stop the trace and close [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span> <span data-ttu-id="58b15-122">이런 방식으로 추적 결과가 손실되는 것을 방지하려면 **를 닫기 전에** 파일 **메뉴에서** 저장 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="58b15-122">To avoid losing the trace results in this way, click **Save** on the **File** menu to save the results before you close [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span>  
  
5.  <span data-ttu-id="58b15-123">필요에 따라 **추적 중지 시간 설정** 확인란을 선택하여 중지 날짜 및 시간을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="58b15-123">Optionally, select the **Enable trace stop time** check box, and specify a stop date and time.</span></span>  
  
6.  <span data-ttu-id="58b15-124">이벤트, 데이터 열 또는 필터를 추가하거나 제거하려면 **이벤트 선택**탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="58b15-124">To add or remove events, data columns or filters, click the **Events Selection**tab.</span></span> <span data-ttu-id="58b15-125">자세한 내용은 [추적 파일에 대해 이벤트 및 데이터 열 지정&#40;SQL Server Profiler&#41;](sql-server-profiler.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="58b15-125">For more information, see: [Specify Events and Data Columns for a Trace File &#40;SQL Server Profiler&#41;](sql-server-profiler.md)</span></span>  
  
7.  <span data-ttu-id="58b15-126">**실행** 을 클릭하여 추적을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="58b15-126">Click **Run** to start the trace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58b15-127">참고 항목</span><span class="sxs-lookup"><span data-stu-id="58b15-127">See Also</span></span>  
 <span data-ttu-id="58b15-128">[SQL Server 프로파일러 실행에 필요한 권한](permissions-required-to-run-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="58b15-128">[Permissions Required to Run SQL Server Profiler](permissions-required-to-run-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="58b15-129">[SQL Server Profiler 템플릿 및 권한](sql-server-profiler-templates-and-permissions.md) </span><span class="sxs-lookup"><span data-stu-id="58b15-129">[SQL Server Profiler Templates and Permissions](sql-server-profiler-templates-and-permissions.md) </span></span>  
 <span data-ttu-id="58b15-130">[SQL Server 프로파일러](sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="58b15-130">[SQL Server Profiler](sql-server-profiler.md) </span></span>  
 [<span data-ttu-id="58b15-131">추적과 Windows 성능 로그 데이터의 상관 관계 지정&#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="58b15-131">Correlate a Trace with Windows Performance Log Data &#40;SQL Server Profiler&#41;</span></span>](../../database-engine/correlate-a-trace-with-windows-performance-log-data-sql-server-profiler.md)  
  
  
