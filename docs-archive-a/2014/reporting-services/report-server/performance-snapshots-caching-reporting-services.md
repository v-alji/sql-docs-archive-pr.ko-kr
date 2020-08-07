---
title: 성능, 스냅샷, 캐시(Reporting Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- performance [Reporting Services]
- Reporting Services, performance
ms.assetid: 85afd00f-e8d7-4ef7-9174-2ff84d82f960
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f171586e136b36bd694fa40b15272f62e1cb1378
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87732411"
---
# <a name="performance-snapshots-caching-reporting-services"></a><span data-ttu-id="12fea-102">성능, 스냅샷, 캐시(Reporting Services)</span><span class="sxs-lookup"><span data-stu-id="12fea-102">Performance, Snapshots, Caching (Reporting Services)</span></span>
  <span data-ttu-id="12fea-103">보고서 서버 성능은 하드웨어, 보고서에 액세스하는 동시 사용자 수, 보고서의 데이터 양, 출력 형식 등을 비롯한 여러 요소 조합의 영향을 받습니다.</span><span class="sxs-lookup"><span data-stu-id="12fea-103">Report server performance is affected by a combination of factors that include hardware, number of concurrent users accessing reports, the amount of data in a report, and output format.</span></span> <span data-ttu-id="12fea-104">설치와 관련된 성능 요소를 이해하고 원하는 결과를 생성하는 해결 방법을 찾으려면 기준선 데이터를 얻고 테스트를 실행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="12fea-104">To understand the performance factors that are specific to your installation and which remedies will produce the results you want, you will need to get baseline data and run tests.</span></span> <span data-ttu-id="12fea-105">도구 및 지침에 대한 자세한 내용은 MSDN의 [Reporting Services 성능 최적화](https://blogs.msdn.com/b/sqlcat/archive/2013/10/30/reporting-services-performance-and-optimization.aspx) 및 [Visual Studio 2005를 사용한 SQL Server 2005 Reporting Services 보고서 서버의 부하 테스트 수행](https://go.microsoft.com/fwlink/?LinkID=77519)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="12fea-105">For more information about tools and guidelines, see the following publications on MSDN: [Reporting Services Performance Optimization](https://blogs.msdn.com/b/sqlcat/archive/2013/10/30/reporting-services-performance-and-optimization.aspx) and [Using Visual Studio 2005 to Perform Load Testing on a SQL Server 2005 Reporting Services Report Server](https://go.microsoft.com/fwlink/?LinkID=77519).</span></span>  
  
 <span data-ttu-id="12fea-106">고려해야 할 일반 원칙은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="12fea-106">General principles to consider include the following:</span></span>  
  
-   <span data-ttu-id="12fea-107">보고서 처리 및 렌더링은 메모리를 많이 사용하는 작업입니다.</span><span class="sxs-lookup"><span data-stu-id="12fea-107">Report processing and rendering are memory intensive operations.</span></span> <span data-ttu-id="12fea-108">가능하면 메모리가 많은 컴퓨터를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="12fea-108">When possible, choose a computer that has a lot of memory.</span></span>  
  
-   <span data-ttu-id="12fea-109">별도의 컴퓨터에 보고서 서버 및 보고서 서버 데이터베이스를 호스팅하는 것이 단일 고성능 컴퓨터에 두 구성 요소를 모두 호스팅하는 것보다 성능이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="12fea-109">Hosting the report server and the report server database on separate computers tends to provide better performance than hosting both on a single high-end computer.</span></span>  
  
-   <span data-ttu-id="12fea-110">모든 보고서가 느리게 처리되는 경우 여러 보고서 서버 인스턴스가 단일 보고서 서버 데이터베이스를 지원하는 스케일 아웃 배포를 사용해 보세요.</span><span class="sxs-lookup"><span data-stu-id="12fea-110">If all reports are processing slowly, consider a scale-out deployment where multiple report server instances support a single report server database.</span></span> <span data-ttu-id="12fea-111">최상의 결과를 얻으려면 부하 분산 소프트웨어를 사용하여 배포에 요청을 균등하게 분산합니다.</span><span class="sxs-lookup"><span data-stu-id="12fea-111">For best results, use load balancing software to distribute requests evenly across the deployment.</span></span>  
  
-   <span data-ttu-id="12fea-112">단일 보고서가 느리게 처리되는 중이며 보고서를 요청 시 실행해야 하는 경우 보고서 데이터 세트 쿼리를 튜닝합니다.</span><span class="sxs-lookup"><span data-stu-id="12fea-112">If a single report is processing slowly, tune report dataset queries if the report must run on demand.</span></span> <span data-ttu-id="12fea-113">또한 캐시할 수 있는 공유 데이터 세트를 사용하거나 보고서를 캐시하거나 보고서를 스냅샷으로 실행하는 것을 고려할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="12fea-113">You might also consider using shared datasets that you can cache, caching the report, or running the report as a snapshot.</span></span>  
  
-   <span data-ttu-id="12fea-114">PDF로 렌더링할 때처럼 모든 보고서가 특정 형식에서 느리게 처리되는 경우 파일 공유 배달을 사용하거나 메모리를 추가하거나 다른 형식을 선택해 보십시오.</span><span class="sxs-lookup"><span data-stu-id="12fea-114">If all reports process slowly in a specific format (for example, while rendering to PDF), consider file share delivery, adding more memory, or choosing a different format.</span></span>  
  
-   <span data-ttu-id="12fea-115">보고서 및 기타 사용 메트릭을 처리하는 데 소요되는 시간을 확인하려면 보고서 서버 실행 로그를 검토합니다.</span><span class="sxs-lookup"><span data-stu-id="12fea-115">To find out how long it takes to process a report and other usage metrics, review the report server execution log.</span></span> <span data-ttu-id="12fea-116">자세한 내용은 [보고서 서버 실행 로그 및 ExecutionLog3 뷰](report-server-executionlog-and-the-executionlog3-view.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="12fea-116">For more information, see [Report Server Execution Log and the ExecutionLog3 View](report-server-executionlog-and-the-executionlog3-view.md).</span></span>  
  
-   <span data-ttu-id="12fea-117">메모리 관리 구성 설정을 조정하여 성능 문제를 완화하는 방법에 대한 자세한 내용은 [보고서 서버 애플리케이션을 위한 사용 가능한 메모리 구성](../report-server/configure-available-memory-for-report-server-applications.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="12fea-117">For more information about how to mitigate performance issues by tuning memory management configuration settings, see [Configure Available Memory for Report Server Applications](../report-server/configure-available-memory-for-report-server-applications.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="12fea-118">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="12fea-118">In This Section</span></span>  
 [<span data-ttu-id="12fea-119">보고서 서버 성능 모니터링</span><span class="sxs-lookup"><span data-stu-id="12fea-119">Monitoring Report Server Performance</span></span>](monitoring-report-server-performance.md)  
 <span data-ttu-id="12fea-120">서버의 처리 부하를 추적하는 데 사용할 수 있는 성능 개체에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="12fea-120">Describes the performance objects you can use to track the processing load on your server.</span></span>  
  
 [<span data-ttu-id="12fea-121">보고서 처리 속성 설정</span><span class="sxs-lookup"><span data-stu-id="12fea-121">Set Report Processing Properties</span></span>](set-report-processing-properties.md)  
 <span data-ttu-id="12fea-122">보고서가 요청 시 실행되거나 캐시에서 실행되거나 일정에 따라 보고서 스냅샷으로 실행되도록 구성하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="12fea-122">Describes ways of configuring a report to run on demand, from cache, or on a schedule as a report snapshot.</span></span>  
  
 [<span data-ttu-id="12fea-123">보고서 서버 애플리케이션을 위한 사용 가능한 메모리 구성</span><span class="sxs-lookup"><span data-stu-id="12fea-123">Configure Available Memory for Report Server Applications</span></span>](../report-server/configure-available-memory-for-report-server-applications.md)  
 <span data-ttu-id="12fea-124">기본 메모리 관리 동작을 재정의하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="12fea-124">Describes how you can override default memory management behavior.</span></span>  
  
 [<span data-ttu-id="12fea-125">보고서 캐시&#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="12fea-125">Caching Reports &#40;SSRS&#41;</span></span>](caching-reports-ssrs.md)  
 <span data-ttu-id="12fea-126">보고서 서버의 보고서 캐시 동작에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="12fea-126">Describes report caching behavior on a report server.</span></span>  
  
 [<span data-ttu-id="12fea-127">공유 데이터 세트 캐시&#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="12fea-127">Cache Shared Datasets &#40;SSRS&#41;</span></span>](cache-shared-datasets-ssrs.md)  
 <span data-ttu-id="12fea-128">보고서 서버의 공유 데이터 세트 캐싱 동작에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="12fea-128">Describes shared dataset caching behavior on a report server.</span></span>  
  
 [<span data-ttu-id="12fea-129">큰 보고서 처리</span><span class="sxs-lookup"><span data-stu-id="12fea-129">Process Large Reports</span></span>](process-large-reports.md)  
 <span data-ttu-id="12fea-130">대형 보고서를 구성 및 배포하는 권장 방법을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="12fea-130">Provides recommendations on how to configure and distribute a large report.</span></span>  
  
 [<span data-ttu-id="12fea-131">보고서 및 공유 데이터 세트 처리에 대한 제한 시간 값 설정&#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="12fea-131">Setting Time-out Values for Report and Shared Dataset Processing &#40;SSRS&#41;</span></span>](setting-time-out-values-for-report-and-shared-dataset-processing-ssrs.md)  
 <span data-ttu-id="12fea-132">쿼리 및 보고서 처리에 대한 제한 시간을 설정하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="12fea-132">Explains how to set time outs on query and report processing.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12fea-133">참고 항목</span><span class="sxs-lookup"><span data-stu-id="12fea-133">See Also</span></span>  
 <span data-ttu-id="12fea-134">[실행 중인 프로세스 관리](../subscriptions/manage-a-running-process.md) </span><span class="sxs-lookup"><span data-stu-id="12fea-134">[Manage a Running Process](../subscriptions/manage-a-running-process.md) </span></span>  
 [<span data-ttu-id="12fea-135">보고서 실행 확인</span><span class="sxs-lookup"><span data-stu-id="12fea-135">Verifying a Report Run</span></span>](verifying-a-report-run.md)  
  
  
