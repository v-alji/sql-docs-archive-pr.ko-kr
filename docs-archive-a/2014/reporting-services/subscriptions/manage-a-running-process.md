---
title: 실행 중인 프로세스 관리 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- report processing [Reporting Services], status information
- jobs [Reporting Services]
- viewing jobs
- canceling jobs
- user jobs [Reporting Services]
- system jobs [Reporting Services]
- report processing [Reporting Services], managing running processes
- processes [Reporting Services]
- scanning processes [Reporting Services]
- status information [Reporting Services]
- report processing [Reporting Services]
- canceling subscriptions
- report servers [Reporting Services], jobs
- data-driven subscriptions
- displaying jobs
- subscriptions [Reporting Services], running processes
ms.assetid: 473e574e-f1ff-4ef9-bda6-7028b357ac42
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 002dda5a9708b68c6bbf978fb00e85f27b493da2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660320"
---
# <a name="manage-a-running-process"></a><span data-ttu-id="c3d77-102">실행 중인 프로세스 관리</span><span class="sxs-lookup"><span data-stu-id="c3d77-102">Manage a Running Process</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="c3d77-103">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]는 보고서 서버에서 실행 중인 작업의 상태를 모니터링합니다.</span><span class="sxs-lookup"><span data-stu-id="c3d77-103">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] monitors the status of jobs that are running on the report server.</span></span> <span data-ttu-id="c3d77-104">보고서 서버는 진행 중인 작업을 정기적으로 검색하고 SharePoint 모드용 서비스 애플리케이션 데이터베이스 또는 보고서 서버 데이터베이스에 상태 정보를 씁니다.</span><span class="sxs-lookup"><span data-stu-id="c3d77-104">At regular intervals, the report server does a scan of in-progress jobs and writes the status information to the report server database or the service application databases for SharePoint mode.</span></span> <span data-ttu-id="c3d77-105">원격 또는 로컬 데이터베이스 서버에서 쿼리가 실행되거나 보고서가 처리되거나 보고서가 렌더링되는 경우 작업이 진행 중인 것입니다.</span><span class="sxs-lookup"><span data-stu-id="c3d77-105">A job is in progress if any of the following processes are underway: query execution on a remote or local database server, report processing, and report rendering.</span></span>  
  
 <span data-ttu-id="c3d77-106">*사용자 작업* 과 *시스템 작업*을 모두 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c3d77-106">You can manage both *user jobs* and *system jobs*.</span></span>  
  
-   <span data-ttu-id="c3d77-107">사용자 작업은 개별 사용자나 구독에 의해 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="c3d77-107">User jobs are initiated by an individual user or subscription.</span></span> <span data-ttu-id="c3d77-108">여기에는 요청 시 보고서 실행, 보고서 기록 스냅샷 요청, 보고서 스냅샷의 수동 생성 및 표준 구독 처리 작업이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="c3d77-108">This includes running a report on demand, requesting a report history snapshot, manually creating a report snapshot, and processing a standard subscription.</span></span>  
  
-   <span data-ttu-id="c3d77-109">시스템 작업은 보고서 서버에 의해 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="c3d77-109">System jobs are initiated by the report server.</span></span> <span data-ttu-id="c3d77-110">시스템 작업에는 예약된 보고서 실행 스냅샷, 예약된 보고서 기록 스냅샷 및 데이터 기반 구독이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="c3d77-110">System jobs include scheduled report execution snapshots, scheduled report history snapshots, and data-driven subscriptions.</span></span>  
  
 <span data-ttu-id="c3d77-111">보고서 처리 시간과 리소스 사용량은 보고서, 쿼리 복잡성, 데이터의 양 및 보고서에 대해 지정된 렌더링 형식에 따라 크게 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="c3d77-111">Report processing time and resource use varies considerably depending on the report, the query complexity, the amount of data, and the rendering format that is specified for the report.</span></span> <span data-ttu-id="c3d77-112">로컬 데이터 원본에 대한 단순 쿼리를 포함하는 보고서는 밀리초 단위로 완료되며 관리나 튜닝이 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c3d77-112">Reports that have simple queries against a local data source will often complete in milliseconds and never require management or tuning.</span></span> <span data-ttu-id="c3d77-113">이와는 반대로 PDF나 Excel에서 렌더링한 큰 보고서는 하드웨어 리소스, 배달 옵션 및 다른 프로세스의 동시 실행 여부에 따라 처리하는 데 시간이 상당히 오래 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c3d77-113">In contrast, a large report that is rendered in PDF or Excel might require significant processing time depending on hardware resources, delivery options, and whether other processes are running concurrently.</span></span> <span data-ttu-id="c3d77-114">보고서 서버에서 장기간 실행되는 대부분의 프로세스는 쿼리 처리가 끝나기를 기다리는 보고서 렌더링 작업 및 프로세스입니다.</span><span class="sxs-lookup"><span data-stu-id="c3d77-114">On a report server, most long-running processes are report rendering operations and processes that are waiting for query processing to conclude.</span></span> <span data-ttu-id="c3d77-115">경우에 따라 컴퓨터를 오프라인으로 전환한 경우 보고서 프로세스를 취소하거나 완료되는 데 시간이 많이 걸리는 실행 중인 작업을 중지해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c3d77-115">Occasionally, you might need to cancel a report process if you want to take a computer offline, or stop a running job that is taking too long to complete.</span></span>  
  
 <span data-ttu-id="c3d77-116">다음 프로세스를 취소할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c3d77-116">The following processes can be cancelled:</span></span>  
  
-   <span data-ttu-id="c3d77-117">요청 시 실행 보고서 처리</span><span class="sxs-lookup"><span data-stu-id="c3d77-117">On-demand report processing.</span></span>  
  
-   <span data-ttu-id="c3d77-118">예약된 보고서 처리</span><span class="sxs-lookup"><span data-stu-id="c3d77-118">Scheduled report processing.</span></span>  
  
-   <span data-ttu-id="c3d77-119">개별 사용자가 소유한 표준 구독</span><span class="sxs-lookup"><span data-stu-id="c3d77-119">Standard subscriptions owned by individual users.</span></span>  
  
 <span data-ttu-id="c3d77-120">작업을 취소하면 보고서 서버에서 실행 중인 프로세스만 취소됩니다.</span><span class="sxs-lookup"><span data-stu-id="c3d77-120">Canceling a job only cancels the processes that are running on the report server.</span></span> <span data-ttu-id="c3d77-121">보고서 서버는 다른 컴퓨터에서 발생하는 데이터 처리를 관리하지 않으므로 이후에 다른 시스템에서 분리되는 쿼리 프로세스는 수동으로 취소해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3d77-121">Because the report server does not manage data processing that occurs on other computers, you must manually cancel query processes that are subsequently orphaned on other systems.</span></span> <span data-ttu-id="c3d77-122">실행하는 데 시간이 너무 오래 걸리는 쿼리는 자동으로 종료되도록 쿼리 제한 시간 값을 지정하세요.</span><span class="sxs-lookup"><span data-stu-id="c3d77-122">Consider specifying query time-out values to automatically shut down queries that are taking too long to execute.</span></span> <span data-ttu-id="c3d77-123">자세한 내용은 [보고서 및 공유 데이터 세트 처리에 대한 제한 시간 값 설정&#40;SSRS&#41;](../report-server/setting-time-out-values-for-report-and-shared-dataset-processing-ssrs.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c3d77-123">For more information, see [Setting Time-out Values for Report and Shared Dataset Processing &#40;SSRS&#41;](../report-server/setting-time-out-values-for-report-and-shared-dataset-processing-ssrs.md).</span></span> <span data-ttu-id="c3d77-124">보고서를 일시적으로 일시 중지 하는 방법에 대 한 자세한 내용은 [보고서 및 구독 처리 일시 중지](disable-or-pause-report-and-subscription-processing.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="c3d77-124">For more information about temporarily pausing a report, see [Pause Report and Subscription Processing](disable-or-pause-report-and-subscription-processing.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c3d77-125">간혹 프로세스를 취소하기 위해 서버를 다시 시작해야 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c3d77-125">In rare circumstances, you may need to restart the server to cancel a process.</span></span> <span data-ttu-id="c3d77-126">SharePoint 모드의 경우 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 서비스 애플리케이션을 호스팅하는 애플리케이션 풀을 다시 시작해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c3d77-126">For SharePoint mode, you may need to restart the application pool hosting the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service application.</span></span> <span data-ttu-id="c3d77-127">자세한 내용은 [보고서 서버 서비스 시작 및 중지](../report-server/start-and-stop-the-report-server-service.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c3d77-127">For more information, see [Start and Stop the Report Server Service](../report-server/start-and-stop-the-report-server-service.md).</span></span>  
  
 <span data-ttu-id="c3d77-128">항목 내용</span><span class="sxs-lookup"><span data-stu-id="c3d77-128">In this Topic:</span></span>  
  
-   [<span data-ttu-id="c3d77-129">작업 보기 및 취소(기본 모드)</span><span class="sxs-lookup"><span data-stu-id="c3d77-129">View and Cancel Jobs (Native Mode)</span></span>](#bkmk_native)  
  
-   [<span data-ttu-id="c3d77-130">작업 보기 및 취소(SharePoint 모드)</span><span class="sxs-lookup"><span data-stu-id="c3d77-130">View and Cancel Jobs (SharePoint Mode)</span></span>](#bkmk_sharepoint)  
  
-   [<span data-ttu-id="c3d77-131">프로그래밍 방식으로 작업 관리</span><span class="sxs-lookup"><span data-stu-id="c3d77-131">Managing Jobs Programmatically</span></span>](#bkmk_programmatically)  
  
##  <a name="view-and-cancel-jobs-native-mode"></a><a name="bkmk_native"></a> <span data-ttu-id="c3d77-132">작업 보기 및 취소(기본 모드)</span><span class="sxs-lookup"><span data-stu-id="c3d77-132">View and Cancel Jobs (Native Mode)</span></span>  
 <span data-ttu-id="c3d77-133">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]를 사용하여 보고서 서버에서 실행 중인 작업을 보거나 취소할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c3d77-133">You can use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] to view or cancel a job that is running on the report server.</span></span> <span data-ttu-id="c3d77-134">현재 실행 중인 작업 목록을 검색하거나 보고서 서버 데이터베이스에서 최신 작업 상태를 가져오려면 페이지를 새로 고쳐야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3d77-134">You must refresh the page to retrieve a list of jobs that are currently running or to get up-to-date job status from the report server database.</span></span> <span data-ttu-id="c3d77-135">[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]에서 보고서 서버에 연결하면 작업 폴더를 열어 보고서 서버 컴퓨터에서 현재 처리 중인 보고서 목록을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c3d77-135">When you connect to a report server in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], you can open a Jobs folder to view a list of reports that are currently processing on the report server computer.</span></span> <span data-ttu-id="c3d77-136">각 작업에 대한 상태 정보는 작업 속성 페이지에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c3d77-136">Status information for each job is displayed in the Job Properties page.</span></span> <span data-ttu-id="c3d77-137">보고서 서버 작업 취소 대화 상자를 열어 모든 작업에 대한 상태 정보를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c3d77-137">You can view status information for all jobs by opening the Cancel Report Server Jobs dialog box.</span></span>  
  
 <span data-ttu-id="c3d77-138">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]를 사용하여 보고서 서버에서 실행 중인 작업을 보거나 취소할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c3d77-138">You can use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] to view or cancel a job that is running on the report server.</span></span> <span data-ttu-id="c3d77-139">현재 실행 중인 작업 목록을 검색하거나 보고서 서버 데이터베이스에서 최신 작업 상태를 가져오려면 페이지를 새로 고쳐야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3d77-139">You must refresh the page to retrieve a list of jobs that are currently running or to get up-to-date job status from the report server database.</span></span> <span data-ttu-id="c3d77-140">[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]에서 보고서 서버에 연결하면 작업 폴더를 열어 보고서 서버 컴퓨터에서 현재 처리 중인 보고서 목록을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c3d77-140">When you connect to a report server in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], you can open a Jobs folder to view a list of reports that are currently processing on the report server computer.</span></span> <span data-ttu-id="c3d77-141">각 작업에 대한 상태 정보는 작업 속성 페이지에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c3d77-141">Status information for each job is displayed in the Job Properties page.</span></span> <span data-ttu-id="c3d77-142">보고서 서버 작업 취소 대화 상자를 열어 모든 작업에 대한 상태 정보를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c3d77-142">You can view status information for all jobs by opening the Cancel Report Server Jobs dialog box.</span></span>  
  
 <span data-ttu-id="c3d77-143">[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 를 사용하여 모델 생성, 모델 처리 또는 데이터 기반 구독을 나열하거나 취소할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c3d77-143">You cannot use [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] to list or cancel model generation, model processing, or data-driven subscriptions.</span></span> <span data-ttu-id="c3d77-144">Reporting Services는 모델 생성 또는 처리를 취소하는 방법을 제공하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c3d77-144">Reporting a Services does not provide a way to cancel model generation or processing.</span></span> <span data-ttu-id="c3d77-145">그러나 이 항목에 제공된 지침에 따라 데이터 기반 구독을 취소할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c3d77-145">However, you can cancel data-driven subscriptions using the instructions provided in this topic.</span></span>  
  
### <a name="how-to-cancel-report-processing-or-subscription"></a><span data-ttu-id="c3d77-146">보고서 처리 또는 구독을 취소하는 방법</span><span class="sxs-lookup"><span data-stu-id="c3d77-146">How to Cancel Report Processing or Subscription</span></span>  
  
1.  <span data-ttu-id="c3d77-147">[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]에서 보고서 서버에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="c3d77-147">In [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], connect to the report server.</span></span> <span data-ttu-id="c3d77-148">자세한 내용은 [Management Studio에서 보고서 서버에 연결](../tools/connect-to-a-report-server-in-management-studio.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c3d77-148">For instructions, see [Connect to a Report Server in Management Studio](../tools/connect-to-a-report-server-in-management-studio.md).</span></span>  
  
2.  <span data-ttu-id="c3d77-149">**작업** 폴더를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="c3d77-149">Open the **Jobs** folder.</span></span>  
  
3.  <span data-ttu-id="c3d77-150">보고서를 마우스 오른쪽 단추로 클릭한 다음 **작업 취소**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c3d77-150">Right-click the report and then click **Cancel Jobs**.</span></span>  
  
### <a name="how-to-cancel-a-data-driven-subscription"></a><span data-ttu-id="c3d77-151">데이터 기반 구독을 취소하는 방법</span><span class="sxs-lookup"><span data-stu-id="c3d77-151">How to Cancel a Data-driven Subscription</span></span>  
  
1.  <span data-ttu-id="c3d77-152">텍스트 편집기에서 RSReportServer.config 파일을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="c3d77-152">Open the RSReportServer.config file in a text editor.</span></span>  
  
2.  <span data-ttu-id="c3d77-153">`IsNotificationService` 찾기.</span><span class="sxs-lookup"><span data-stu-id="c3d77-153">Find `IsNotificationService`.</span></span>  
  
3.  <span data-ttu-id="c3d77-154">`False`로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="c3d77-154">Set it to `False`.</span></span>  
  
4.  <span data-ttu-id="c3d77-155">파일을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="c3d77-155">Save the file.</span></span>  
  
5.  <span data-ttu-id="c3d77-156">보고서 관리자에서 보고서의 구독 탭 또는 **내 구독**에서 데이터 기반 구독을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="c3d77-156">In Report Manager, delete the data-driven subscription from the Subscriptions tab of the report or from **My Subscriptions**.</span></span>  
  
6.  <span data-ttu-id="c3d77-157">구독을 삭제한 후 RSReportServer.config 파일에서 `IsNotificationService`를 찾아 `True`로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="c3d77-157">After you delete the subscription, in the RSReportServer.config file, find `IsNotificationService` and set it to `True`.</span></span>  
  
7.  <span data-ttu-id="c3d77-158">파일을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="c3d77-158">Save the file.</span></span>  
  
### <a name="configuring-frequency-settings-for-retrieving-job-status"></a><span data-ttu-id="c3d77-159">작업 상태 검색을 위한 빈도 설정 구성</span><span class="sxs-lookup"><span data-stu-id="c3d77-159">Configuring Frequency Settings for Retrieving Job Status</span></span>  
 <span data-ttu-id="c3d77-160">실행 중인 작업은 보고서 서버 임시 데이터베이스에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="c3d77-160">A running job is stored in the report server temporary database.</span></span> <span data-ttu-id="c3d77-161">RSReportServer.config 파일에서 구성 설정을 수정하여 보고서 서버가 진행 중인 작업을 검색하는 빈도 및 실행 작업의 상태가 새 작업에서 실행 중인 작업으로 변경되는 간격을 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c3d77-161">You can modify configuration settings in the RSReportServer.config file to control how often the report server scans for in-progress jobs and the interval after which the status of a running job changes from new to running.</span></span> <span data-ttu-id="c3d77-162">`RunningRequestsDbCycle` 설정은 보고서 서버가 실행 중인 프로세스를 검색하는 빈도를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c3d77-162">The `RunningRequestsDbCycle` setting specifies how often the report server scans for running processes.</span></span> <span data-ttu-id="c3d77-163">기본적으로 상태 정보는 60초마다 기록됩니다.</span><span class="sxs-lookup"><span data-stu-id="c3d77-163">By default, status information is recorded every 60 seconds.</span></span> <span data-ttu-id="c3d77-164">`RunningRequestsAge` 설정은 작업이 새 작업에서 실행 중인 작업으로 전환되는 간격을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c3d77-164">The `RunningRequestsAge` setting specifies the interval at which a job is transitioned from new to running.</span></span>  
  
##  <a name="view-and-cancel-jobs-sharepoint-mode"></a><a name="bkmk_sharepoint"></a> <span data-ttu-id="c3d77-165">작업 보기 및 취소(SharePoint 모드)</span><span class="sxs-lookup"><span data-stu-id="c3d77-165">View and Cancel Jobs (SharePoint Mode)</span></span>  
 <span data-ttu-id="c3d77-166">SharePoint 모드 배포에서 작업 관리는 각 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 서비스 애플리케이션에 대해 SharePoint 중앙 관리를 사용하여 완료됩니다.</span><span class="sxs-lookup"><span data-stu-id="c3d77-166">Management of jobs in a SharePoint mode deployment is completed using SharePoint Central Administration, for each [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service application.</span></span>  
  
#### <a name="to-manage-jobs-in-sharepoint-mode"></a><span data-ttu-id="c3d77-167">SharePoint 모드에서 작업을 관리하려면</span><span class="sxs-lookup"><span data-stu-id="c3d77-167">To manage jobs in SharePoint mode</span></span>  
  
1.  <span data-ttu-id="c3d77-168">SharePoint 중앙 관리에서 **서비스 애플리케이션 관리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c3d77-168">In SharePoint Central Administration, click **Manage service applications**.</span></span>  
  
2.  <span data-ttu-id="c3d77-169">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 서비스 애플리케이션의 이름을 찾아서 클릭하여 애플리케이션 관리 페이지를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="c3d77-169">Find and click the name of your [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service application to open the manage application page.</span></span>  
  
3.  <span data-ttu-id="c3d77-170">**작업 관리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c3d77-170">Click **Manage Jobs**</span></span>  
  
4.  <span data-ttu-id="c3d77-171">작업 세부 정보를 보려면 **작업 ID** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c3d77-171">Click the **Job Id** to see the details of the job.</span></span>  
  
5.  <span data-ttu-id="c3d77-172">또는 작업에 대한 상자를 클릭하고 **삭제** 를 클릭하여 작업을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="c3d77-172">Or click the box for your job and click **Delete** to cancel the job.</span></span> <span data-ttu-id="c3d77-173">작업을 삭제해도 구독은 삭제되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c3d77-173">Deleting the job does not delete the subscription.</span></span>  
  
##  <a name="managing-jobs-programmatically"></a><a name="bkmk_programmatically"></a> <span data-ttu-id="c3d77-174">프로그래밍 방식으로 작업 관리</span><span class="sxs-lookup"><span data-stu-id="c3d77-174">Managing Jobs Programmatically</span></span>  
 <span data-ttu-id="c3d77-175">프로그래밍 방식으로 또는 스크립트를 사용하여 작업을 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c3d77-175">You can manage jobs programmatically or by using a script.</span></span> <span data-ttu-id="c3d77-176">자세한 내용은 <xref:ReportService2010.ReportingService2010.ListJobs%2A>, <xref:ReportService2010.ReportingService2010.CancelJob%2A>을 모두 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c3d77-176">For more information, see <xref:ReportService2010.ReportingService2010.ListJobs%2A>, <xref:ReportService2010.ReportingService2010.CancelJob%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3d77-177">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c3d77-177">See Also</span></span>  
 <span data-ttu-id="c3d77-178">[보고서 서버 작업 취소&#40;Management Studio&#41;](../tools/cancel-report-server-jobs-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="c3d77-178">[Cancel Report Server Jobs &#40;Management Studio&#41;](../tools/cancel-report-server-jobs-management-studio.md) </span></span>  
 <span data-ttu-id="c3d77-179">[작업 속성&#40;Management Studio&#41;](../tools/job-properties-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="c3d77-179">[Job Properties &#40;Management Studio&#41;](../tools/job-properties-management-studio.md) </span></span>  
 <span data-ttu-id="c3d77-180">[Reporting Services 구성 파일 수정&#40;RSreportserver.config&#41;](../report-server/modify-a-reporting-services-configuration-file-rsreportserver-config.md) </span><span class="sxs-lookup"><span data-stu-id="c3d77-180">[Modify a Reporting Services Configuration File &#40;RSreportserver.config&#41;](../report-server/modify-a-reporting-services-configuration-file-rsreportserver-config.md) </span></span>  
 <span data-ttu-id="c3d77-181">[Rsreportserver.config 구성 파일](../report-server/rsreportserver-config-configuration-file.md) </span><span class="sxs-lookup"><span data-stu-id="c3d77-181">[RSReportServer Configuration File](../report-server/rsreportserver-config-configuration-file.md) </span></span>  
 <span data-ttu-id="c3d77-182">[보고서 관리자&#40;SSRS 기본 모드&#41;](../report-manager-ssrs-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="c3d77-182">[Report Manager  &#40;SSRS Native Mode&#41;](../report-manager-ssrs-native-mode.md) </span></span>  
 [<span data-ttu-id="c3d77-183">보고서 서버 성능 모니터링</span><span class="sxs-lookup"><span data-stu-id="c3d77-183">Monitoring Report Server Performance</span></span>](../report-server/monitoring-report-server-performance.md)  
  
  
