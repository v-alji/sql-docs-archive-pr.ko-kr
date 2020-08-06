---
title: Analysis Services 인스턴스 모니터링 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- monitoring [Analysis Services - multidimensional data]
- multidimensional data [Analysis Services], monitoring
- monitoring performance [SQL Server], SQL Server Profiler
- performance [SQL Server], monitoring tools
ms.assetid: 2f0ab717-05f3-427e-b8cd-a8bdca374add
author: minewiskan
ms.author: owend
ms.openlocfilehash: b98037ea9f26c339cdf7aba22c37e2cfb3dfbb97
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653035"
---
# <a name="monitor-an-analysis-services-instance"></a><span data-ttu-id="49458-102">Analysis Services 인스턴스 모니터</span><span class="sxs-lookup"><span data-stu-id="49458-102">Monitor an Analysis Services Instance</span></span>
  <span data-ttu-id="49458-103">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 또는 성능 모니터( [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] PerfMon **)를 사용하여**의 성능을 모니터할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="49458-103">You can monitor the performance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] by using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] or Performance Monitor, an application sometimes referred to as **PerfMon**.</span></span> [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] <span data-ttu-id="49458-104">를 사용하면 추적을 작성 및 관리하고 추적 결과를 분석 및 재생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="49458-104">lets you create and manage traces and analyze and replay trace results.</span></span> <span data-ttu-id="49458-105">성능 모니터는 다음 섹션에서 설명하는 것처럼 특정 카운터를 통해 인덱싱된 서버 상태를 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="49458-105">Performance Monitor reports on server status, as indexed through certain counters, which are discussed in the next section.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="49458-106">모니터링에 대한 자세한 내용은 [SQL Server 2008 R2 Operations Guide](https://go.microsoft.com/fwlink/?LinkID=225539)(SQL Server 2008 R2 작업 가이드)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="49458-106">For more information about monitoring, see the [SQL Server 2008 R2 Operations Guide](https://go.microsoft.com/fwlink/?LinkID=225539).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="49458-107">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="49458-107">In This Section</span></span>  
 <span data-ttu-id="49458-108">모니터링에 대해 자세히 알아보려면 다음 링크를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="49458-108">Follow these links to learn more about monitoring.</span></span>  
  
 [<span data-ttu-id="49458-109">Analysis Services 추적 이벤트</span><span class="sxs-lookup"><span data-stu-id="49458-109">Analysis Services Trace Events</span></span>](https://docs.microsoft.com/bi-reference/trace-events/analysis-services-trace-events)  
  
 [<span data-ttu-id="49458-110">Use SQL Server Profiler to Monitor Analysis Services</span><span class="sxs-lookup"><span data-stu-id="49458-110">Use SQL Server Profiler to Monitor Analysis Services</span></span>](use-sql-server-profiler-to-monitor-analysis-services.md)  
  
 [<span data-ttu-id="49458-111">SQL Server 확장 이벤트 &#40;Xevent&#41;를 사용 하 여 모니터링 Analysis Services</span><span class="sxs-lookup"><span data-stu-id="49458-111">Use SQL Server Extended Events &#40;XEvents&#41; to Monitor Analysis Services</span></span>](../instances/monitor-analysis-services-with-sql-server-extended-events.md)  
  
 [<span data-ttu-id="49458-112">DMV&#40;동적 관리 뷰&#41;를 사용하여 Analysis Services 모니터링</span><span class="sxs-lookup"><span data-stu-id="49458-112">Use Dynamic Management Views &#40;DMVs&#41; to Monitor Analysis Services</span></span>](use-dynamic-management-views-dmvs-to-monitor-analysis-services.md)  
  
 [<span data-ttu-id="49458-113">성능 카운터&#40;SSAS&#41;</span><span class="sxs-lookup"><span data-stu-id="49458-113">Performance Counters &#40;SSAS&#41;</span></span>](performance-counters-ssas.md)  
  
  
