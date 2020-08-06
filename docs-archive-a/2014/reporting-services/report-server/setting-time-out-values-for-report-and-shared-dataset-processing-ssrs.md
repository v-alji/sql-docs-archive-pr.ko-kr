---
title: 보고서 및 공유 데이터 세트 처리에 대한 시간 제한 값 설정(SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- time-outs [Reporting Services]
- query time-outs [Reporting Services]
- report processing [Reporting Services], time-outs
- report execution time-outs [Reporting Services]
ms.assetid: 0f9dc61d-d03c-4bbf-8090-7a53844350f8
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c891b4911994ba2814a612439f141d16e4ad12a6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650627"
---
# <a name="setting-time-out-values-for-report-and-shared-dataset-processing-ssrs"></a><span data-ttu-id="b76f0-102">보고서 및 공유 데이터 세트 처리에 대한 시간 제한 값 설정(SSRS)</span><span class="sxs-lookup"><span data-stu-id="b76f0-102">Setting Time-out Values for Report and Shared Dataset Processing (SSRS)</span></span>
  <span data-ttu-id="b76f0-103">제한 시간 값을 지정하여 시스템 리소스 사용 방식에 대해 제한을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b76f0-103">You can specify time-out values to set limits on how system resources are used.</span></span> <span data-ttu-id="b76f0-104">보고서 서버는 다음 두 가지 제한 시간 값을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="b76f0-104">Report server supports two time-out values:</span></span>  
  
-   <span data-ttu-id="b76f0-105">포함된 데이터 세트 쿼리 제한 시간 값은 보고서 서버가 데이터베이스의 응답을 기다리는 시간(초)입니다.</span><span class="sxs-lookup"><span data-stu-id="b76f0-105">An embedded dataset query time-out value is the number of seconds that the report server waits for a response from the database.</span></span> <span data-ttu-id="b76f0-106">이 값은 보고서에서 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="b76f0-106">This value is defined in a report.</span></span>  
  
-   <span data-ttu-id="b76f0-107">공유 데이터 세트 쿼리 제한 시간 값은 보고서 서버가 데이터베이스의 응답을 기다리는 시간(초)입니다.</span><span class="sxs-lookup"><span data-stu-id="b76f0-107">A shared dataset query time-out value is the number of seconds that the report server waits for a response from the database.</span></span> <span data-ttu-id="b76f0-108">이 값은 공유 데이터 세트 정의의 일부이며 보고서 서버에서 공유 데이터 세트를 관리할 때 변경될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b76f0-108">This value is part of the shared dataset definition and can be changed when you manage the shared dataset on the report server.</span></span>  
  
-   <span data-ttu-id="b76f0-109">보고서 실행 제한 시간 값은 보고서 처리가 중지되기까지 계속될 수 있는 최대 시간(초)입니다.</span><span class="sxs-lookup"><span data-stu-id="b76f0-109">A report execution time-out value is the maximum number of seconds that report processing can continue before it is stopped.</span></span> <span data-ttu-id="b76f0-110">이 값은 시스템 수준에서 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="b76f0-110">This value is defined at the system level.</span></span> <span data-ttu-id="b76f0-111">이 설정은 보고서마다 다르게 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b76f0-111">You can vary this setting for individual reports.</span></span>  
  
 <span data-ttu-id="b76f0-112">대부분의 제한 시간 오류는 쿼리가 처리되는 동안 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="b76f0-112">Most time-out errors occur during query processing.</span></span> <span data-ttu-id="b76f0-113">제한 시간 오류가 발생하면 쿼리 제한 시간 값을 늘려 보십시오.</span><span class="sxs-lookup"><span data-stu-id="b76f0-113">If you are encountering time-out errors, try increasing the query time-out value.</span></span> <span data-ttu-id="b76f0-114">보고서 실행 제한 시간 값을 쿼리 제한 시간 보다 크게 조정 해야 합니다. 기간은 쿼리 및 보고서 처리를 모두 완료 하기에 충분 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b76f0-114">Make sure to adjust the report execution time-out value so that it is larger than the query time-out. The time period should be sufficient to complete both query and report processing.</span></span>  
  
## <a name="setting-a-query-time-out-for-an-embedded-dataset-in-a-report"></a><span data-ttu-id="b76f0-115">보고서에 포함된 데이터 세트의 쿼리 제한 시간 설정</span><span class="sxs-lookup"><span data-stu-id="b76f0-115">Setting a Query Time-Out for an Embedded Dataset in a Report</span></span>  
 <span data-ttu-id="b76f0-116">쿼리 제한 시간 값은 보고서를 작성하는 동안 포함된 데이터 세트를 정의할 때 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="b76f0-116">Query time-out values are specified during report authoring when you define an embedded dataset.</span></span> <span data-ttu-id="b76f0-117">쿼리 제한 시간 값은 보고서 정의의 `Timeout` 요소에 보고서와 함께 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="b76f0-117">The time-out value is stored with the report, in the `Timeout` element of the report definition.</span></span> <span data-ttu-id="b76f0-118">기본적으로 이 값은 30초로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="b76f0-118">By default, this value is set to 30 seconds.</span></span> <span data-ttu-id="b76f0-119">자세한 내용은 [보고서 포함된 데이터 세트 및 공유 데이터 세트&#40;보고서 작성기 및 SSRS&#41;](../report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b76f0-119">For more information, see [Report Embedded Datasets and Shared Datasets &#40;Report Builder and SSRS&#41;](../report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="b76f0-120">게시된 보고서의 속성을 수정할 권한이 있는 사용자는 보고서 정의 파일을 편집하여 이 값을 다시 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b76f0-120">Users who have permission to modify the properties of a published report can reset this value by editing the report definition file.</span></span>  
  
 <span data-ttu-id="b76f0-121">데이터 기반 구독에 대한 쿼리 제한 시간 값도 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b76f0-121">You can also specify a query time-out value for data-driven subscriptions.</span></span> <span data-ttu-id="b76f0-122">이 쿼리 제한 시간 값은 데이터 기반 구독 페이지에서 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b76f0-122">The query time-out value is specified in the Data-Driven Subscription pages.</span></span> <span data-ttu-id="b76f0-123">지정한 값에 따라 구독자 데이터 원본에서 데이터를 검색할 때 보고서 서버에서 쿼리 처리가 완료되기를 기다리는 시간이 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="b76f0-123">The value you specify determines how long the report server waits for query processing to complete when retrieving data from the subscriber data source.</span></span>  
  
## <a name="setting-a-query-time-out-for-a-shared-dataset"></a><span data-ttu-id="b76f0-124">공유 데이터 세트의 쿼리 제한 시간 설정</span><span class="sxs-lookup"><span data-stu-id="b76f0-124">Setting a Query Time-Out for a Shared Dataset</span></span>  
 <span data-ttu-id="b76f0-125">쿼리 제한 시간 값은 보고서 서버에서 공유 데이터 세트를 만들거나 관리할 때 초 단위로 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="b76f0-125">Query time-out values are specified in seconds on the report server when you create or manage a shared dataset.</span></span> <span data-ttu-id="b76f0-126">기본적으로 이 값은 0초로 설정되며 이것은 제한 시간 값이 없는 것과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="b76f0-126">By default, this value is set to 0 seconds, which is the equivalent of no time-out value.</span></span> <span data-ttu-id="b76f0-127">자세한 내용은 [공유 데이터 세트 관리](../report-data/manage-shared-datasets.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b76f0-127">For more information, see [Manage Shared Datasets](../report-data/manage-shared-datasets.md).</span></span>  
  
## <a name="setting-a-report-execution-time-out"></a><span data-ttu-id="b76f0-128">보고서 실행 제한 시간 설정</span><span class="sxs-lookup"><span data-stu-id="b76f0-128">Setting a Report Execution Time-Out</span></span>  
 <span data-ttu-id="b76f0-129">보고서 실행 제한 시간 값을 설정하여 보고서 서버에서 보고서를 처리하는 데 사용하는 시간을 제한할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b76f0-129">You can set the report execution time-out value to limit the amount of time that a report server uses to process a report.</span></span> <span data-ttu-id="b76f0-130">보고서 실행 제한 시간 값은 보고서 관리자에서 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b76f0-130">Report execution time-out values can be specified in Report Manager.</span></span> <span data-ttu-id="b76f0-131">사이트 설정 페이지에서 모든 보고서에 대해 기본값을 설정한 다음 특정 보고서에 대한 실행 속성 페이지에서 해당 값을 재정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b76f0-131">You can set a default value for all reports in the Site Settings page, and then override that value in the Execution properties page for a specific report.</span></span> <span data-ttu-id="b76f0-132">기본적으로 이 값은 1800초로 설정되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b76f0-132">By default, the value is set to 1800 seconds.</span></span> <span data-ttu-id="b76f0-133">자세한 내용은 [보고서 처리 속성 설정](set-report-processing-properties.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b76f0-133">For more information, see [Set Report Processing Properties](set-report-processing-properties.md).</span></span>  
  
## <a name="how-report-execution-time-out-values-are-evaluated"></a><span data-ttu-id="b76f0-134">보고서 실행 제한 시간 값 평가 방법</span><span class="sxs-lookup"><span data-stu-id="b76f0-134">How Report Execution Time-Out Values are Evaluated</span></span>  
 <span data-ttu-id="b76f0-135">보고서 서버는 60초 간격으로 실행 작업을 평가합니다.</span><span class="sxs-lookup"><span data-stu-id="b76f0-135">The report server evaluates running jobs at 60 second intervals.</span></span> <span data-ttu-id="b76f0-136">60초마다 실제 처리 시간을 보고서 실행 제한 시간 값과 비교하여</span><span class="sxs-lookup"><span data-stu-id="b76f0-136">At each 60 second interval, the report server compares actual process time against the report execution time-out value.</span></span> <span data-ttu-id="b76f0-137">보고서 처리 시간이 보고서 실행 제한 시간 값을 초과하면 보고서 처리가 중지됩니다.</span><span class="sxs-lookup"><span data-stu-id="b76f0-137">If the processing time for a report exceeds the report execution time-out value, report processing will stop.</span></span>  
  
 <span data-ttu-id="b76f0-138">제한 시간 값을 60초 이내로 지정한 경우 보고서 서버에서 실행 작업을 평가하지 않는 휴지 시간 동안 보고서 처리가 시작되어 완료되면 보고서를 완전하게 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b76f0-138">Note that if you specify a time-out value that is smaller than 60 seconds, the report may execute in full if processing starts and completes during the quiet part of the cycle when the report server is not evaluating running jobs.</span></span> <span data-ttu-id="b76f0-139">예를 들어 실행 시간이 20초인 보고서에 실행 제한 시간 값을 10초로 설정하면 보고서가 60초 주기의 초반에 실행되는 경우 보고서는 완전하게 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="b76f0-139">For example, if you set a time-out value of 10 seconds for a report that takes 20 seconds to run, the report will process in full if report execution starts early in the 60 second cycle.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b76f0-140">RSReportServer.config 파일에서 `RunningRequestsDbCycle`을 설정하여 실행 작업의 평가 빈도를 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b76f0-140">You can set the `RunningRequestsDbCycle` setting in the RSReportServer.config file to change the frequency of how often running jobs are evaluated.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b76f0-141">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b76f0-141">See Also</span></span>  
 <span data-ttu-id="b76f0-142">[SharePoint 통합 모드에서 처리 옵션을 Reporting Services &#40;설정&#41;](../set-processing-options-reporting-services-in-sharepoint-integrated-mode.md) </span><span class="sxs-lookup"><span data-stu-id="b76f0-142">[Set Processing Options &#40;Reporting Services in SharePoint Integrated Mode&#41;](../set-processing-options-reporting-services-in-sharepoint-integrated-mode.md) </span></span>  
 <span data-ttu-id="b76f0-143">[Reporting Services 보고서 서버&#40;기본 모드&#41;](reporting-services-report-server-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="b76f0-143">[Reporting Services Report Server &#40;Native Mode&#41;](reporting-services-report-server-native-mode.md) </span></span>  
 <span data-ttu-id="b76f0-144">[실행 중인 프로세스 관리](../subscriptions/manage-a-running-process.md) </span><span class="sxs-lookup"><span data-stu-id="b76f0-144">[Manage a Running Process](../subscriptions/manage-a-running-process.md) </span></span>  
 [<span data-ttu-id="b76f0-145">보고서 관리자&#40;SSRS 기본 모드&#41;</span><span class="sxs-lookup"><span data-stu-id="b76f0-145">Report Manager  &#40;SSRS Native Mode&#41;</span></span>](../report-manager-ssrs-native-mode.md)  
  
  
