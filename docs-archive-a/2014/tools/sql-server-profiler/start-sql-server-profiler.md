---
title: SQL Server Profiler 시작 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- Profiler [SQL Server Profiler], starting
- SQL Server Profiler, starting
- starting SQL Server Profiler
ms.assetid: 22e57ffa-63b0-4de3-b92e-df297dda1226
author: stevestein
ms.author: sstein
ms.openlocfilehash: 05743927420865a9b6341fc050ca999f494d64d3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734744"
---
# <a name="start-sql-server-profiler"></a><span data-ttu-id="f41a6-102">SQL Server Profiler 시작</span><span class="sxs-lookup"><span data-stu-id="f41a6-102">Start SQL Server Profiler</span></span>
  <span data-ttu-id="f41a6-103">다양한 시나리오에서 추적 출력 수집을 지원하기 위해 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 를 여러 다른 방법으로 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f41a6-103">You can start [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] in several different ways to support gathering trace output in a variety of scenarios.</span></span> <span data-ttu-id="f41a6-104">[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 는 **시작** 메뉴, **튜닝 관리자의** 도구 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 메뉴 또는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]의 여러 위치에서 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f41a6-104">You can start [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] include from the **Start** menu, from the **Tools** menu in [!INCLUDE[ssDE](../../includes/ssde-md.md)] Tuning Advisor, and from several locations in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="f41a6-105">[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 를 처음 시작하고 **파일** 메뉴에서 **새 추적** 을 선택하면 연결할 **인스턴스를 지정할 수 있는** 서버에 연결 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 대화 상자가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="f41a6-105">When you first start [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] and select **New Trace** from the **File** menu, the application displays a **Connect to Server** dialog box where you can specify the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance to which you want to connect.</span></span>  
  
### <a name="to-start-sql-server-profiler-from-the-start-menu"></a><span data-ttu-id="f41a6-106">시작 메뉴에서 SQL Server Profiler를 시작하려면</span><span class="sxs-lookup"><span data-stu-id="f41a6-106">To start SQL Server Profiler from the Start menu</span></span>  
  
1.  <span data-ttu-id="f41a6-107">**시작** 메뉴에서 **모든 프로그램**, [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)], **성능 도구**를 차례로 가리킨 다음 **SQL Server Profiler**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f41a6-107">On the **Start** menu, point to **All Programs**, point to [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)], point to **Performance Tools**, and then click **SQL Server Profiler**.</span></span>  
  
### <a name="to-start-sql-server-profiler-in-database-engine-tuning-advisor"></a><span data-ttu-id="f41a6-108">데이터베이스 엔진 튜닝 관리자에서 SQL Server Profiler를 시작하려면</span><span class="sxs-lookup"><span data-stu-id="f41a6-108">To start SQL Server Profiler in Database Engine Tuning Advisor</span></span>  
  
1.  <span data-ttu-id="f41a6-109">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 튜닝 관리자의 **도구** 메뉴에서 **SQL Server Profiler**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f41a6-109">On the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Tuning Advisor **Tools** menu, click **SQL Server Profiler**.</span></span>  
  
## <a name="starting-sql-server-profiler-in-management-studio"></a><span data-ttu-id="f41a6-110">Management Studio에서 SQL Server Profiler 시작</span><span class="sxs-lookup"><span data-stu-id="f41a6-110">Starting SQL Server Profiler in Management Studio</span></span>  
 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] <span data-ttu-id="f41a6-111">는 각 프로파일러 세션을 자체 인스턴스에서 시작하므로 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]를 중지해도 이러한 프로파일러 세션은 계속 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="f41a6-111">starts each profiler session in its own instance and continues to run if you shutdown [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="f41a6-112">[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 는 다음 절차에서처럼 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]의 여러 위치에서 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f41a6-112">You can start [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] from several locations in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], as illustrated in the following procedures.</span></span> <span data-ttu-id="f41a6-113">[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 를 시작하면 시작 지점의 연결 컨텍스트, 추적 템플릿 및 필터 컨텍스트가 로드됩니다.</span><span class="sxs-lookup"><span data-stu-id="f41a6-113">When [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] starts it loads the connection context, trace template, and filter context of its launch point.</span></span>  
  
#### <a name="to-start-sql-server-profiler-from-the-tools-menu"></a><span data-ttu-id="f41a6-114">도구 메뉴에서 SQL Server Profiler를 시작하려면</span><span class="sxs-lookup"><span data-stu-id="f41a6-114">To start SQL Server Profiler from the Tools menu</span></span>  
  
1.  <span data-ttu-id="f41a6-115">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] **도구** 메뉴에서 **SQL Server Profiler**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f41a6-115">In the [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] **Tools** menu, click **SQL Server Profiler**.</span></span>  
  
#### <a name="to-start-sql-server-profiler-from-the-query-editor"></a><span data-ttu-id="f41a6-116">쿼리 편집기에서 SQL Server Profiler를 시작하려면</span><span class="sxs-lookup"><span data-stu-id="f41a6-116">To start SQL Server Profiler from the Query Editor</span></span>  
  
1.  <span data-ttu-id="f41a6-117">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 메뉴에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f41a6-117">On the [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] menu bar, click **New Query**.</span></span>  
  
2.  <span data-ttu-id="f41a6-118">쿼리 편집기에서 마우스 오른쪽 단추를 클릭한 다음 **SQL Server Profiler에서 쿼리 추적**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f41a6-118">In Query Editor, right-click and then select **Trace Query in SQL Server Profiler**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="f41a6-119">연결 컨텍스트는 편집기 연결이고, 추적 템플릿은 TSQL_SP이며, 적용된 필터는 SPID = 쿼리 창 SPID입니다.</span><span class="sxs-lookup"><span data-stu-id="f41a6-119">The connection context is the editor connection, the trace template is TSQL_SPs, and the applied filter is SPID = query window SPID.</span></span>  
  
#### <a name="to-start-sql-server-profiler-from-activity-monitor"></a><span data-ttu-id="f41a6-120">작업 모니터에서 SQL Server Profiler를 시작하려면</span><span class="sxs-lookup"><span data-stu-id="f41a6-120">To start SQL Server Profiler from Activity Monitor</span></span>  
  
1.  <span data-ttu-id="f41a6-121">개체 탐색기에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스를 마우스 오른쪽 단추로 클릭한 다음 **작업 모니터**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f41a6-121">In Object Explorer, right-click an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], and then click **Activity Monitor**.</span></span>  
  
2.  <span data-ttu-id="f41a6-122">**프로세스** 창을 클릭하고 프로파일링할 프로세스를 마우스 오른쪽 단추로 클릭한 다음 **SQL Server Profiler의 추적 프로세스**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f41a6-122">Click the **Processes** pane, right-click the process that you want to profile, and then click **Trace Process in SQL Server Profiler**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="f41a6-123">프로세스를 선택하면 작업 모니터가 열릴 당시의 개체 탐색기 연결이 연결 컨텍스트가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f41a6-123">When a process is selected, the connection context is the Object Explorer connection when Activity Monitor was opened.</span></span> <span data-ttu-id="f41a6-124">추적 템플릿은 서버 유형을 기반으로 하는 기본 템플릿이고 SPID가 선택한 프로세스의 SPID와 같게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f41a6-124">The trace template is the default based on the server type, and the SPID equals the SPID for the selected process.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="f41a6-125">.NET Framework 보안</span><span class="sxs-lookup"><span data-stu-id="f41a6-125">.NET Framework Security</span></span>  
 <span data-ttu-id="f41a6-126">Windows 인증 모드를 사용하여 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 를 실행하는 사용자 계정은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스에 연결할 수 있는 사용 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f41a6-126">In Windows Authentication mode, the user account that runs [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] must have permission to connect to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="f41a6-127">[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]를 사용하여 추적을 수행하려면 또한 ALTER TRACE 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f41a6-127">To perform tracing with [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)], users must also have the ALTER TRACE permission.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f41a6-128">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f41a6-128">See Also</span></span>  
 <span data-ttu-id="f41a6-129">[SQL Server Profiler](sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="f41a6-129">[SQL Server Profiler](sql-server-profiler.md) </span></span>  
 [<span data-ttu-id="f41a6-130">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="f41a6-130">Use SQL Server Management Studio</span></span>](../../database-engine/use-sql-server-management-studio.md)  
  
  
