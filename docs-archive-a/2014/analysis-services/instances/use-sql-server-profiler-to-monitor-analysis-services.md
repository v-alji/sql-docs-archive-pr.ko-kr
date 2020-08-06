---
title: SQL Server Profiler를 사용 하 여 Analysis Services 모니터링 Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Profiler, Analysis Services
- monitoring Analysis Services [SQL Server]
- performance [Analysis Services], SQL Server Profiler
- Profiler [SQL Server Profiler], Analysis Services
ms.assetid: 8b77dafc-4584-4e93-8ad7-299304391bfd
author: minewiskan
ms.author: owend
ms.openlocfilehash: e144c1d858670f8a46b164ffc9885e6e082c4b0a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647958"
---
# <a name="use-sql-server-profiler-to-monitor-analysis-services"></a><span data-ttu-id="f7949-102">Use SQL Server Profiler to Monitor Analysis Services</span><span class="sxs-lookup"><span data-stu-id="f7949-102">Use SQL Server Profiler to Monitor Analysis Services</span></span>
  [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] <span data-ttu-id="f7949-103">일괄 처리나 트랜잭션 시작 같은 엔진 프로세스 이벤트를 추적하여 이러한 이벤트에 대한 데이터를 캡처하므로 서버와 데이터베이스 작업(예: 사용자 쿼리 또는 로그인 작업)을 모니터할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7949-103">tracks engine process events, such as the start of a batch or a transaction, and it captures data about those events, thus enabling you to monitor server and database activity (for example, user queries or login activity).</span></span> <span data-ttu-id="f7949-104">[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 데이터를 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 테이블이나 파일에 캡처해 나중에 분석할 때 사용할 수 있으며 같거나 다른 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 인스턴스에서 캡처한 이벤트를 재생해 그 영향을 정확하게 확인할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7949-104">You can capture [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] data to a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table or a file for later analysis, and you can also replay the events captured on the same or another [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance to see exactly what happened.</span></span> <span data-ttu-id="f7949-105">실시간이나 단계별로 이벤트를 재생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7949-105">You can replay events in real time or on a step-by-step basis.</span></span> <span data-ttu-id="f7949-106">같은 시스템에서 성능 카운터와 함께 추적 이벤트를 실행하는 것도 매우 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="f7949-106">It is also very useful to run the trace events along with the Performance counters on the same machine.</span></span> <span data-ttu-id="f7949-107">프로파일러는 시간을 기반으로 이 둘의 상관 관계를 지정하고 단일 시간대로 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7949-107">The profiler can correlate these two based on time and display them together along a single timeline.</span></span> <span data-ttu-id="f7949-108">추적 이벤트는 세부 정보를 제공하고 성능 카운터는 집계 뷰를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="f7949-108">Trace events will give you more details while Performance counters give you an aggregate view.</span></span> <span data-ttu-id="f7949-109">추적을 만들고 실행하는 방법에 대한 자세한 내용은 [재생에 대한 프로파일러 추적 만들기&#40;Analysis Services&#41;](create-profiler-traces-for-replay-analysis-services.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f7949-109">For information about how to create and run traces, see [Create Profiler Traces for Replay &#40;Analysis Services&#41;](create-profiler-traces-for-replay-analysis-services.md).</span></span>  
  
 <span data-ttu-id="f7949-110">다음 표에서는 이 섹션에서 다루는 항목에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="f7949-110">The following table describes the topics in this section.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f7949-111">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="f7949-111">In This Section</span></span>  
  
|<span data-ttu-id="f7949-112">항목</span><span class="sxs-lookup"><span data-stu-id="f7949-112">Topic</span></span>|<span data-ttu-id="f7949-113">Description</span><span class="sxs-lookup"><span data-stu-id="f7949-113">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="f7949-114">SQL Server 프로파일러를 사용한 Analysis Services 모니터링 소개</span><span class="sxs-lookup"><span data-stu-id="f7949-114">Introduction to Monitoring Analysis Services with SQL Server Profiler</span></span>](introduction-to-monitoring-analysis-services-with-sql-server-profiler.md)|<span data-ttu-id="f7949-115">[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 를 사용하여 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 인스턴스를 모니터링하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="f7949-115">Describes how to use [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] to monitor an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance.</span></span>|  
|[<span data-ttu-id="f7949-116">재생에 대한 프로파일러 추적 만들기&#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="f7949-116">Create Profiler Traces for Replay &#40;Analysis Services&#41;</span></span>](create-profiler-traces-for-replay-analysis-services.md)|<span data-ttu-id="f7949-117">[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]를 사용하여 재생용 추적을 만들기 위한 요구 사항에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="f7949-117">Describes the requirements for creating a trace for replay by using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span>|  
|[<span data-ttu-id="f7949-118">Analysis Services 추적 이벤트</span><span class="sxs-lookup"><span data-stu-id="f7949-118">Analysis Services Trace Events</span></span>](https://docs.microsoft.com/bi-reference/trace-events/analysis-services-trace-events)|<span data-ttu-id="f7949-119">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 이벤트 클래스에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="f7949-119">Describes [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] event classes.</span></span> <span data-ttu-id="f7949-120">이러한 이벤트 클래스는 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 에서 생성한 동작에 매핑되고 추적 재생에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="f7949-120">These event classes map to actions generated by [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] and are used for trace replays.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f7949-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f7949-121">See Also</span></span>  
 [<span data-ttu-id="f7949-122">Analysis Services 인스턴스 모니터</span><span class="sxs-lookup"><span data-stu-id="f7949-122">Monitor an Analysis Services Instance</span></span>](monitor-an-analysis-services-instance.md)  
  
  
