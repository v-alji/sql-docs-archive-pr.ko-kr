---
title: 보고서 서버 실행 로그 및 ExecutionLog3 뷰 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- logs [Reporting Services], execution
- execution logs [Reporting Services]
ms.assetid: a7ead67d-1404-4e67-97e7-4c7b0d942070
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 868f8497e61c17662cb621850cdb8aee74c82706
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648299"
---
# <a name="report-server-execution-log-and-the-executionlog3-view"></a><span data-ttu-id="4717f-102">보고서 서버 실행 로그 및 ExecutionLog3 뷰</span><span class="sxs-lookup"><span data-stu-id="4717f-102">Report Server Execution Log and the ExecutionLog3 View</span></span>
  <span data-ttu-id="4717f-103">보고서 서버 실행 로그에는 단일 서버 또는 기본 모드를 사용하는 스케일 아웃 배포 또는 SharePoint 팜을 사용한 다중 서버에서 실행되는 보고서에 대한 정보가 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4717f-103">The report server execution log contains information about the reports that execute on the server or on multiple servers in a native mode scale-out deployment or a SharePoint farm.</span></span> <span data-ttu-id="4717f-104">보고서 실행 로그를 사용하여 보고서 요청 빈도, 가장 많이 사용되는 출력 형식 및 각 처리 단계에 소요된 처리 시간(밀리초)을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4717f-104">You can use the report execution log to find out how often a report is requested, what output formats are used the most, and how many milliseconds of processing time is spent on each processing phase.</span></span> <span data-ttu-id="4717f-105">로그에는 보고서의 데이터 세트 쿼리 실행에 걸린 시간 또는 데이터 처리에 걸린 시간에 대한 정보가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="4717f-105">The log contains information on the length of time spent executing a report's dataset query and the time spent processing the data.</span></span> <span data-ttu-id="4717f-106">보고서 서버 관리자는 로그 정보를 검토하여 오랫동안 실행되는 태스크를 식별하고 보고서 작성자가 보고서에서 기능을 향상시킬 수 있는 부문(데이터 세트 또는 처리)에 대한 사항을 제안할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4717f-106">If you are a report server administrator, you can review the log information and identify long running tasks and make suggestions to the report authors on the areas of the report (dataset or processing) they may be able to improve.</span></span>  
  
 <span data-ttu-id="4717f-107">SharePoint 모드용으로 구성된 보고서 서버는 또한 SharePoint ULS 로그를 활용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4717f-107">Report servers configured for SharePoint mode, can also utilize the SharePoint ULS logs.</span></span> <span data-ttu-id="4717f-108">자세한 내용은 [SharePoint 추적 로그에 대한 Reporting Services 이벤트 설정&#40;ULS&#41;](turn-on-reporting-services-events-for-the-sharepoint-trace-log-uls.md)</span><span class="sxs-lookup"><span data-stu-id="4717f-108">For more information, see [Turn on Reporting Services events for the SharePoint trace log &#40;ULS&#41;](turn-on-reporting-services-events-for-the-sharepoint-trace-log-uls.md)</span></span>  
  
##  <a name="viewing-log-information"></a><a name="bkmk_top"></a> <span data-ttu-id="4717f-109">로그 정보 보기</span><span class="sxs-lookup"><span data-stu-id="4717f-109">Viewing Log Information</span></span>  
 <span data-ttu-id="4717f-110">보고서 서버 실행은 내부 데이터베이스 테이블에 보고서 실행에 대한 데이터를 기록합니다.</span><span class="sxs-lookup"><span data-stu-id="4717f-110">The report server execution logs data about report execution into an internal database table.</span></span> <span data-ttu-id="4717f-111">테이블의 정보는 SQL Server 뷰에서 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4717f-111">The information from the table is available from SQL Server views.</span></span>  
  
 <span data-ttu-id="4717f-112">보고서 실행 로그는 기본적으로 이름이 **ReportServer**로 지정되는 보고서 서버 데이터베이스에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="4717f-112">The report execution log is stored in the report server database that by default is named **ReportServer**.</span></span> <span data-ttu-id="4717f-113">SQL 뷰는 실행 로그 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="4717f-113">The SQL views provide the execution log information.</span></span> <span data-ttu-id="4717f-114">최신 릴리스에는 "2"번과 "3"번 뷰가 추가되었으며, 이러한 뷰에는 새로운 필드 또는 이전 릴리스보다 친숙한 이름의 필드가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="4717f-114">The "2" and "3" views were added in more recent releases and contain new fields or they contain fields with friendlier names than the previous releases.</span></span> <span data-ttu-id="4717f-115">이전 뷰도 제품에 그대로 유지되므로 이러한 뷰를 사용하는 사용자 지정 애플리케이션에는 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4717f-115">The older views remain in the product so custom applications that depend on them are not impacted.</span></span> <span data-ttu-id="4717f-116">이전 뷰에 대한 종속성이 없는 경우(예: ExecutionLog) 최신 뷰인 ExecutionLog**3**를 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="4717f-116">If you do not have a dependence on an older view, for example ExecutionLog, it is recommended you use the most recent view, ExecutionLog**3**.</span></span>  
  
 <span data-ttu-id="4717f-117">이 항목의 내용:</span><span class="sxs-lookup"><span data-stu-id="4717f-117">In this topic:</span></span>  
  
-   [<span data-ttu-id="4717f-118">SharePoint 모드 보고서 서버에 대한 구성 설정</span><span class="sxs-lookup"><span data-stu-id="4717f-118">Configuration Settings for a SharePoint mode Report Server</span></span>](#bkmk_sharepoint)  
  
-   [<span data-ttu-id="4717f-119">기본 모드 보고서 서버에 대한 구성 설정</span><span class="sxs-lookup"><span data-stu-id="4717f-119">Configuration Settings for a Native Mode Report Server</span></span>](#bkmk_native)  
  
-   [<span data-ttu-id="4717f-120">로그 필드(ExecutionLog3)</span><span class="sxs-lookup"><span data-stu-id="4717f-120">Log Fields (ExecutionLog3)</span></span>](#bkmk_executionlog3)  
  
-   [<span data-ttu-id="4717f-121">AdditionalInfo 필드</span><span class="sxs-lookup"><span data-stu-id="4717f-121">The AdditionalInfo Field</span></span>](#bkmk_additionalinfo)  
  
-   [<span data-ttu-id="4717f-122">로그 필드(ExecutionLog2)</span><span class="sxs-lookup"><span data-stu-id="4717f-122">Log Fields (ExecutionLog2)</span></span>](#bkmk_executionlog2)  
  
-   [<span data-ttu-id="4717f-123">로그 필드(ExecutionLog)</span><span class="sxs-lookup"><span data-stu-id="4717f-123">Log Fields (ExecutionLog)</span></span>](#bkmk_executionlog)  
  
##  <a name="configuration-settings-for-a-sharepoint-mode-report-server"></a><a name="bkmk_sharepoint"></a> <span data-ttu-id="4717f-124">SharePoint 모드 보고서 서버에 대한 구성 설정</span><span class="sxs-lookup"><span data-stu-id="4717f-124">Configuration Settings for a SharePoint mode Report Server</span></span>  
 <span data-ttu-id="4717f-125">보고서 실행 로깅은 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 서비스 애플리케이션의 시스템 설정에서 설정 또는 해제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4717f-125">You can turn report execution logging on or off from the system settings of a [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service application.</span></span>  
  
 <span data-ttu-id="4717f-126">기본적으로 로그 항목은 60일 동안 보관됩니다.</span><span class="sxs-lookup"><span data-stu-id="4717f-126">By default, log entries are kept 60 days.</span></span> <span data-ttu-id="4717f-127">이 날짜를 초과한 항목은 매일 오전 2시에</span><span class="sxs-lookup"><span data-stu-id="4717f-127">Entries that exceed this date are removed at 2:00 A.M.</span></span> <span data-ttu-id="4717f-128">제거됩니다.</span><span class="sxs-lookup"><span data-stu-id="4717f-128">every day.</span></span> <span data-ttu-id="4717f-129">제대로 된 설치에서는 항상 60일 동안의 정보만 사용할 수 있게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4717f-129">On a mature installation, only 60 days of information will be available at any given time.</span></span>  
  
 <span data-ttu-id="4717f-130">로깅된 행 수와 항목 유형에 대한 제한을 설정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4717f-130">You cannot set limits on the number of rows or on the type of entries that are logged.</span></span>  
  
 <span data-ttu-id="4717f-131">**실행 로깅을 설정하려면**</span><span class="sxs-lookup"><span data-stu-id="4717f-131">**To enable execution logging:**</span></span>  
  
1.  <span data-ttu-id="4717f-132">SharePoint 중앙 관리의 **애플리케이션 관리** 그룹에서 **서비스 애플리케이션 관리** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4717f-132">From SharePoint Central Administration, click **Manage service applications** in the **Application Management** group.</span></span>  
  
2.  <span data-ttu-id="4717f-133">구성하려는 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 서비스 애플리케이션의 이름을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4717f-133">Click the name of the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service application you want to configure.</span></span>  
  
3.  <span data-ttu-id="4717f-134">**시스템 설정**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4717f-134">Click **System Settings**.</span></span>  
  
4.  <span data-ttu-id="4717f-135">**로깅** 섹션에서 **실행 로깅 사용** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="4717f-135">Select **Enable Execution Logging** in the **Logging** section.</span></span>  
  
5.  <span data-ttu-id="4717f-136">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4717f-136">Click **OK**.</span></span>  
  
 <span data-ttu-id="4717f-137">**자세한 로깅을 설정하려면**</span><span class="sxs-lookup"><span data-stu-id="4717f-137">**To enable verbose logging:**</span></span>  
  
 <span data-ttu-id="4717f-138">이전 단계에 설명된 대로 로깅을 설정한 후 다음을 완료해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4717f-138">You need to enable logging as described in the previous steps and then complete the following:</span></span>  
  
1.  <span data-ttu-id="4717f-139">**서비스 애플리케이션의** 시스템 설정 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 페이지에서 **사용자 정의** 섹션을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="4717f-139">From the **System Settings** page of your [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] services application, find the **User-defined** section.</span></span>  
  
2.  <span data-ttu-id="4717f-140">**ExecutionLogLevel** 을 **자세히**로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="4717f-140">Change the **ExecutionLogLevel** to **verbose**.</span></span> <span data-ttu-id="4717f-141">이 필드는 텍스트 입력 필드이며 **자세히** 및 **보통**중에서 값을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4717f-141">This field is a text entry field and the two possible values are **verbose** and **normal**.</span></span>  
  
##  <a name="configuration-settings-for-a-native-mode-report-server"></a><a name="bkmk_native"></a> <span data-ttu-id="4717f-142">기본 모드 보고서 서버에 대한 구성 설정</span><span class="sxs-lookup"><span data-stu-id="4717f-142">Configuration Settings for a Native Mode Report Server</span></span>  
 <span data-ttu-id="4717f-143">SQL Server Management Studio의 서버 속성 페이지에서 보고서 실행 로깅을 설정하거나 해제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4717f-143">You can turn report execution logging on or off from the Server Properties page in SQL Server Management Studio.</span></span> <span data-ttu-id="4717f-144">**EnableExecutionLogging** 은 고급 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="4717f-144">The **EnableExecutionLogging** is and Advanced property.</span></span>  
  
 <span data-ttu-id="4717f-145">기본적으로 로그 항목은 60일 동안 보관됩니다.</span><span class="sxs-lookup"><span data-stu-id="4717f-145">By default, log entries are kept 60 days.</span></span> <span data-ttu-id="4717f-146">이 날짜를 초과한 항목은 매일 오전 2시에</span><span class="sxs-lookup"><span data-stu-id="4717f-146">Entries that exceed this date are removed at 2:00 A.M.</span></span> <span data-ttu-id="4717f-147">제거됩니다.</span><span class="sxs-lookup"><span data-stu-id="4717f-147">every day.</span></span> <span data-ttu-id="4717f-148">제대로 된 설치에서는 항상 60일 동안의 정보만 사용할 수 있게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4717f-148">On a mature installation, only 60 days of information will be available at any given time.</span></span>  
  
 <span data-ttu-id="4717f-149">로깅된 행 수와 항목 유형에 대한 제한을 설정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4717f-149">You cannot set limits on the number of rows or on the type of entries that are logged.</span></span>  
  
 <span data-ttu-id="4717f-150">**실행 로깅을 설정하려면**</span><span class="sxs-lookup"><span data-stu-id="4717f-150">**To enable execution logging:**</span></span>  
  
1.  <span data-ttu-id="4717f-151">관리 권한을 사용하여 SQL Server Management Studio를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="4717f-151">Start SQL Server Management Studio with administrative privileges.</span></span> <span data-ttu-id="4717f-152">예를 들어 Management Studio 아이콘을 마우스 오른쪽 단추로 클릭하고 '관리자 권한으로 실행'을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4717f-152">For example right-click the Management Studio icon and click 'Run as administrator'.</span></span>  
  
2.  <span data-ttu-id="4717f-153">원하는 보고서 서버에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="4717f-153">Connect to the desired report server.</span></span>  
  
3.  <span data-ttu-id="4717f-154">서버 이름을 마우스 오른쪽 단추로 클릭하고 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4717f-154">Right-click the server name and click **Properties**.</span></span> <span data-ttu-id="4717f-155">속성 옵션이 해제되어 있으면 관리 권한을 사용하여 SQL Server Management Studio를 실행했는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="4717f-155">If the Properties option is disabled, verify you ran SQL Server Management Studio with administrative privileges.</span></span>  
  
4.  <span data-ttu-id="4717f-156">**로깅** 페이지를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4717f-156">Click the **Logging** page.</span></span>  
  
5.  <span data-ttu-id="4717f-157">**보고서 실행 로깅 사용**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="4717f-157">Select **Enable report execution Logging**.</span></span>  
  
 <span data-ttu-id="4717f-158">**자세한 로깅을 설정하려면**</span><span class="sxs-lookup"><span data-stu-id="4717f-158">**To enable verbose logging:**</span></span>  
  
 <span data-ttu-id="4717f-159">이전 단계에 설명된 대로 로깅을 설정한 후 다음을 완료해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4717f-159">You need to enable logging as described in the previous steps and then complete the following:</span></span>  
  
1.  <span data-ttu-id="4717f-160">**서버 속성** 대화 상자에서 **고급** 페이지를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4717f-160">From the **Server Properties** dialog, click the **Advanced** page.</span></span>  
  
2.  <span data-ttu-id="4717f-161">**사용자 정의** 섹션에서 **ExecutionLogLevel** 을 **자세히**로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="4717f-161">In the **User-defined** section, change the **ExecutionLogLevel** to **verbose**.</span></span> <span data-ttu-id="4717f-162">이 필드는 텍스트 입력 필드이며 **자세히** 및 **보통**중에서 값을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4717f-162">This field is a text entry field and the two possible values are **verbose** and **normal**.</span></span>  
  
##  <a name="log-fields-executionlog3"></a><a name="bkmk_executionlog3"></a> <span data-ttu-id="4717f-163">로그 필드(ExecutionLog3)</span><span class="sxs-lookup"><span data-stu-id="4717f-163">Log Fields (ExecutionLog3)</span></span>  
 <span data-ttu-id="4717f-164">이 뷰에는 XML 기반 **AdditionalInfo** 열 안에 추가 성능 진단 노드가 추가되었습니다.</span><span class="sxs-lookup"><span data-stu-id="4717f-164">This view added additional performance diagnostics node inside the XML based **AdditionalInfo** column.</span></span> <span data-ttu-id="4717f-165">AdditionalInfo 열에는 여러 추가 정보 필드에 대한 1의 XML 구조가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4717f-165">The AdditionalInfo column contains an XML structure of 1 to many additional fields of information.</span></span> <span data-ttu-id="4717f-166">다음은 ExecutionLog3 뷰에서 행을 검색하는 샘플 Transact SQL 문입니다.</span><span class="sxs-lookup"><span data-stu-id="4717f-166">The following is a sample Transact SQL statement to retrieve rows from the view ExecutionLog3.</span></span> <span data-ttu-id="4717f-167">이 샘플에서는 보고서 서버 데이터베이스 이름이 **ReportServer**라고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="4717f-167">The sample assumes the report server database is named **ReportServer**:</span></span>  
  
```  
Use ReportServer  
select * from ExecutionLog3 order by TimeStart DESC  
```  
  
 <span data-ttu-id="4717f-168">다음 표에서는 보고서 실행 로그에 캡처되는 데이터에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="4717f-168">The following table describes the data that is captured in the report execution log</span></span>  
  
|<span data-ttu-id="4717f-169">열</span><span class="sxs-lookup"><span data-stu-id="4717f-169">Column</span></span>|<span data-ttu-id="4717f-170">Description</span><span class="sxs-lookup"><span data-stu-id="4717f-170">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="4717f-171">InstanceName</span><span class="sxs-lookup"><span data-stu-id="4717f-171">InstanceName</span></span>|<span data-ttu-id="4717f-172">요청을 처리한 보고서 서버 인스턴스 이름</span><span class="sxs-lookup"><span data-stu-id="4717f-172">Name of the report server instance that handled the request.</span></span> <span data-ttu-id="4717f-173">사용자 환경에 보고서 서버가 두 개 이상 포함된 경우 InstanceName 배포를 분석하여 네트워크 부하 분산 장치가 예상한 대로 보고서 서버 간에 요청을 분배하는지 모니터링 및 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4717f-173">If your environment has more than one report server, you can analyze the InstanceName distribution to monitor and determine if your network-load balancer distributes requests across report servers as expected.</span></span>|  
|<span data-ttu-id="4717f-174">ItemPath</span><span class="sxs-lookup"><span data-stu-id="4717f-174">ItemPath</span></span>|<span data-ttu-id="4717f-175">보고서 또는 보고서 항목이 저장된 위치의 경로</span><span class="sxs-lookup"><span data-stu-id="4717f-175">Path of where a report or report item is stored.</span></span>|  
|<span data-ttu-id="4717f-176">UserName</span><span class="sxs-lookup"><span data-stu-id="4717f-176">UserName</span></span>|<span data-ttu-id="4717f-177">사용자 식별자</span><span class="sxs-lookup"><span data-stu-id="4717f-177">User identifier.</span></span>|  
|<span data-ttu-id="4717f-178">ExecutionID</span><span class="sxs-lookup"><span data-stu-id="4717f-178">ExecutionID</span></span>|<span data-ttu-id="4717f-179">요청과 연결된 내부 식별자입니다.</span><span class="sxs-lookup"><span data-stu-id="4717f-179">The internal identifier associated with a request.</span></span> <span data-ttu-id="4717f-180">동일한 사용자 세션에 대한 요청은 같은 실행 ID를 공유합니다.</span><span class="sxs-lookup"><span data-stu-id="4717f-180">Requests on the same user sessions share the same execution id.</span></span>|  
|<span data-ttu-id="4717f-181">RequestType</span><span class="sxs-lookup"><span data-stu-id="4717f-181">RequestType</span></span>|<span data-ttu-id="4717f-182">가능한 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="4717f-182">Possible Values:</span></span><br /><span data-ttu-id="4717f-183">**대화형**</span><span class="sxs-lookup"><span data-stu-id="4717f-183">**Interactive**</span></span><br /><span data-ttu-id="4717f-184">**구독**</span><span class="sxs-lookup"><span data-stu-id="4717f-184">**Subscription**</span></span><br /><br /> <br /><br /> <span data-ttu-id="4717f-185">RequestType=Subscription으로 필터링되고 TimeStart로 정렬된 로그 데이터를 분석하면 구독 사용량이 많은 기간을 확인할 수 있으며, 그에 따라 보고서 구독 중 일부를 다른 시간으로 수정해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4717f-185">Analyzing log data filtered by RequestType=Subscription and sorted by TimeStart may reveal periods of heavy subscription usage and you may want to modify some of the report subscriptions to a different time.</span></span>|  
|<span data-ttu-id="4717f-186">형식</span><span class="sxs-lookup"><span data-stu-id="4717f-186">Format</span></span>|<span data-ttu-id="4717f-187">렌더링 형식</span><span class="sxs-lookup"><span data-stu-id="4717f-187">Rendering format.</span></span>|  
|<span data-ttu-id="4717f-188">매개 변수</span><span class="sxs-lookup"><span data-stu-id="4717f-188">Parameters</span></span>|<span data-ttu-id="4717f-189">보고서 실행에 사용된 매개 변수 값</span><span class="sxs-lookup"><span data-stu-id="4717f-189">Parameter values used for a report execution.</span></span>|  
|<span data-ttu-id="4717f-190">ItemAction</span><span class="sxs-lookup"><span data-stu-id="4717f-190">ItemAction</span></span>|<span data-ttu-id="4717f-191">가능한 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="4717f-191">Possible values:</span></span><br /><br /> <span data-ttu-id="4717f-192">**렌더링**</span><span class="sxs-lookup"><span data-stu-id="4717f-192">**Render**</span></span><br /><br /> <span data-ttu-id="4717f-193">**Sort**</span><span class="sxs-lookup"><span data-stu-id="4717f-193">**Sort**</span></span><br /><br /> <span data-ttu-id="4717f-194">**BookMarkNavigation**</span><span class="sxs-lookup"><span data-stu-id="4717f-194">**BookMarkNavigation**</span></span><br /><br /> <span data-ttu-id="4717f-195">**DocumentNavigation**</span><span class="sxs-lookup"><span data-stu-id="4717f-195">**DocumentNavigation**</span></span><br /><br /> <span data-ttu-id="4717f-196">**GetDocumentMap**</span><span class="sxs-lookup"><span data-stu-id="4717f-196">**GetDocumentMap**</span></span><br /><br /> <span data-ttu-id="4717f-197">**Findstring**</span><span class="sxs-lookup"><span data-stu-id="4717f-197">**Findstring**</span></span><br /><br /> <span data-ttu-id="4717f-198">**실행**</span><span class="sxs-lookup"><span data-stu-id="4717f-198">**Execute**</span></span><br /><br /> <span data-ttu-id="4717f-199">**RenderEdit**</span><span class="sxs-lookup"><span data-stu-id="4717f-199">**RenderEdit**</span></span>|  
|<span data-ttu-id="4717f-200">TimeStart</span><span class="sxs-lookup"><span data-stu-id="4717f-200">TimeStart</span></span>|<span data-ttu-id="4717f-201">보고서 처리 기간을 나타내는 시작 및 중지 시간</span><span class="sxs-lookup"><span data-stu-id="4717f-201">Start and stop times that indicate the duration of a report process.</span></span>|  
|<span data-ttu-id="4717f-202">TimeEnd</span><span class="sxs-lookup"><span data-stu-id="4717f-202">TimeEnd</span></span>||  
|<span data-ttu-id="4717f-203">TimeDataRetrieval</span><span class="sxs-lookup"><span data-stu-id="4717f-203">TimeDataRetrieval</span></span>|<span data-ttu-id="4717f-204">데이터를 검색하는 데 걸린 시간(밀리초)</span><span class="sxs-lookup"><span data-stu-id="4717f-204">Number of milliseconds spent retrieving the data.</span></span>|  
|<span data-ttu-id="4717f-205">TimeProcessing</span><span class="sxs-lookup"><span data-stu-id="4717f-205">TimeProcessing</span></span>|<span data-ttu-id="4717f-206">보고서를 처리하는 데 걸린 시간(밀리초)</span><span class="sxs-lookup"><span data-stu-id="4717f-206">Number of milliseconds spent processing the report.</span></span>|  
|<span data-ttu-id="4717f-207">TimeRendering</span><span class="sxs-lookup"><span data-stu-id="4717f-207">TimeRendering</span></span>|<span data-ttu-id="4717f-208">보고서를 렌더링하는 데 걸린 시간(밀리초)</span><span class="sxs-lookup"><span data-stu-id="4717f-208">Number of milliseconds spent rendering the report.</span></span>|  
|<span data-ttu-id="4717f-209">원본</span><span class="sxs-lookup"><span data-stu-id="4717f-209">Source</span></span>|<span data-ttu-id="4717f-210">보고서 실행의 원본입니다.</span><span class="sxs-lookup"><span data-stu-id="4717f-210">Source of the report execution.</span></span> <span data-ttu-id="4717f-211">가능한 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="4717f-211">Possible values:</span></span><br /><br /> <span data-ttu-id="4717f-212">**라이브**</span><span class="sxs-lookup"><span data-stu-id="4717f-212">**Live**</span></span><br /><br /> <span data-ttu-id="4717f-213">**Cache**: 캐시 된 실행을 나타냅니다. 예를 들어 데이터 집합 쿼리는 실시간으로 실행 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4717f-213">**Cache**: Indicates a cached execution, for example, dataset queries are not executed live.</span></span><br /><br /> <span data-ttu-id="4717f-214">**스냅샷**</span><span class="sxs-lookup"><span data-stu-id="4717f-214">**Snapshot**</span></span><br /><br /> <span data-ttu-id="4717f-215">**History**</span><span class="sxs-lookup"><span data-stu-id="4717f-215">**History**</span></span><br /><br /> <span data-ttu-id="4717f-216">**임시** : 동적으로 생성 된 보고서 모델 기반 드릴스루 보고서 또는 처리 및 렌더링을 위해 보고서 서버를 활용 하는 클라이언트에서 미리 본 보고서 작성기 보고서를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="4717f-216">**AdHoc** : Indicates either a dynamically generated report model based drill through report, or a Report Builder report that is previewed on a client utilizing the report server for processing and rendering.</span></span><br /><br /> <span data-ttu-id="4717f-217">**세션**: 이미 설정 된 세션 내에서 후속 요청을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="4717f-217">**Session**: Indicates a follow up request within an already established session.</span></span>  <span data-ttu-id="4717f-218">예를 들어 초기 요청은 1페이지를 보는 것이고 후속 요청은 현재 세션 상태로 Excel로 내보내는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="4717f-218">For example the initial request is to view page 1, and the follow up request is to export to Excel with the current session state.</span></span><br /><br /> <span data-ttu-id="4717f-219">**Rdce**: 보고서 정의 사용자 지정 확장 프로그램을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="4717f-219">**Rdce**:  Indicates a Report Definition Customization Extension.</span></span> <span data-ttu-id="4717f-220">RDCE 사용자 지정 확장 프로그램에서는 보고서 실행 시 보고서 정의가 처리 엔진에 전달되기 전에 보고서 정의를 동적으로 사용자 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4717f-220">An RDCE custom extension can dynamically customize a report definition before it is passed to the processing engine upon report execution.</span></span>|  
|<span data-ttu-id="4717f-221">상태</span><span class="sxs-lookup"><span data-stu-id="4717f-221">Status</span></span>|<span data-ttu-id="4717f-222">상태(rsSuccess 또는 오류 코드: 여러 개의 오류가 발생하면 첫 번째 오류만 기록됨)</span><span class="sxs-lookup"><span data-stu-id="4717f-222">Status (either rsSuccess or an error code; if multiple errors occur, only the first error is recorded).</span></span>|  
|<span data-ttu-id="4717f-223">ByteCount</span><span class="sxs-lookup"><span data-stu-id="4717f-223">ByteCount</span></span>|<span data-ttu-id="4717f-224">렌더링된 보고서 크기(바이트)</span><span class="sxs-lookup"><span data-stu-id="4717f-224">Size of rendered reports in bytes.</span></span>|  
|<span data-ttu-id="4717f-225">RowCount</span><span class="sxs-lookup"><span data-stu-id="4717f-225">RowCount</span></span>|<span data-ttu-id="4717f-226">쿼리에서 반환된 행 수</span><span class="sxs-lookup"><span data-stu-id="4717f-226">Number of rows returned from queries.</span></span>|  
|<span data-ttu-id="4717f-227">AdditionalInfo</span><span class="sxs-lookup"><span data-stu-id="4717f-227">AdditionalInfo</span></span>|<span data-ttu-id="4717f-228">실행에 대한 추가 정보가 포함된 XML 속성 모음</span><span class="sxs-lookup"><span data-stu-id="4717f-228">An XML property bag containing additional information about the execution.</span></span> <span data-ttu-id="4717f-229">콘텐츠는 각 행마다 서로 다를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4717f-229">The contents can be different for each row.</span></span>|  
  
##  <a name="the-additionalinfo-field"></a><a name="bkmk_additionalinfo"></a> <span data-ttu-id="4717f-230">AdditionalInfo 필드</span><span class="sxs-lookup"><span data-stu-id="4717f-230">The AdditionalInfo Field</span></span>  
 <span data-ttu-id="4717f-231">AdditionalInfo 필드는 실행에 대한 추가 정보가 포함된 XML 속성 모음 또는 구조입니다.</span><span class="sxs-lookup"><span data-stu-id="4717f-231">The AdditionalInfo field is an XML property bag or structure containing additional information about the execution.</span></span> <span data-ttu-id="4717f-232">콘텐츠는 로그에서 각 행마다 서로 다를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4717f-232">The contents can be different for each row in the log.</span></span>  
  
 <span data-ttu-id="4717f-233">다음 표는 표준 및 자세한 로깅에 대한 AddtionalInfo 필드 내용의 예입니다.</span><span class="sxs-lookup"><span data-stu-id="4717f-233">The following tables are examples  of the contents of the AddtionalInfo field for both standard and verbose logging:</span></span>  
  
 <span data-ttu-id="4717f-234">**Addtionalinfo의 표준 로깅 예**</span><span class="sxs-lookup"><span data-stu-id="4717f-234">**Standard logging example of AddtionalInfo**</span></span>  
  
```  
<AdditionalInfo>  
  <ProcessingEngine>2</ProcessingEngine>  
  <ScalabilityTime>  
    <Pagination>0</Pagination>  
    <Processing>0</Processing>  
  </ScalabilityTime>  
  <EstimatedMemoryUsageKB>  
    <Pagination>0</Pagination>  
    <Processing>6</Processing>  
  </EstimatedMemoryUsageKB>  
  <DataExtension>  
    <SQL>1</SQL>  
  </DataExtension>  
  <Connections>  
    <Connection>  
      <ConnectionOpenTime>147</ConnectionOpenTime>  
      <DataSets>  
        <DataSet>  
          <Name>DataSet1</Name>  
          <RowsRead>16</RowsRead>  
          <TotalTimeDataRetrieval>642</TotalTimeDataRetrieval>  
          <ExecuteReaderTime>63</ExecuteReaderTime>  
        </DataSet>  
        <DataSet>  
          <Name>DataSet2</Name>  
          <RowsRead>3</RowsRead>  
          <TotalTimeDataRetrieval>157</TotalTimeDataRetrieval>  
          <ExecuteReaderTime>60</ExecuteReaderTime>  
        </DataSet>  
      </DataSets>  
    </Connection>  
  </Connections>  
</AdditionalInfo>  
  
```  
  
 <span data-ttu-id="4717f-235">**Addtionalinfo의 자세한 로깅 예**</span><span class="sxs-lookup"><span data-stu-id="4717f-235">**Verbose logging example of AdditionalInfo**</span></span>  
  
```  
<AdditionalInfo>  
  <ProcessingEngine>2</ProcessingEngine>  
  <ScalabilityTime>  
    <Pagination>0</Pagination>  
    <Processing>0</Processing>  
  </ScalabilityTime>  
  <EstimatedMemoryUsageKB>  
    <Pagination>0</Pagination>  
    <Processing>6</Processing>  
  </EstimatedMemoryUsageKB>  
  <DataExtension>  
    <SQL>1</SQL>  
  </DataExtension>  
  <Connections>  
    <Connection>  
      <ConnectionOpenTime>127</ConnectionOpenTime>  
      <DataSource>  
        <Name>DataSource1</Name>  
        <DataExtension>SQL</DataExtension>  
      </DataSource>  
      <DataSets>  
        <DataSet>  
          <Name>DataSet1</Name>  
          <RowsRead>16</RowsRead>  
          <TotalTimeDataRetrieval>655</TotalTimeDataRetrieval>  
          <QueryPrepareAndExecutionTime>94</QueryPrepareAndExecutionTime>  
          <ExecuteReaderTime>33</ExecuteReaderTime>  
          <DataReaderMappingTime>30</DataReaderMappingTime>  
          <DisposeDataReaderTime>1</DisposeDataReaderTime>  
        </DataSet>  
        <DataSet>  
          <Name>DataSet2</Name>  
          <RowsRead>3</RowsRead>  
          <TotalTimeDataRetrieval>16</TotalTimeDataRetrieval>  
          <QueryPrepareAndExecutionTime>2</QueryPrepareAndExecutionTime>  
          <ExecuteReaderTime>1</ExecuteReaderTime>  
          <DataReaderMappingTime>0</DataReaderMappingTime>  
          <DisposeDataReaderTime>0</DisposeDataReaderTime>  
        </DataSet>  
      </DataSets>  
    </Connection>  
  </Connections>  
</AdditionalInfo>  
  
```  
  
 <span data-ttu-id="4717f-236">다음은 AdditionalInfo 필드에 표시 되는 일부 속성에 대 한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="4717f-236">The following describes some of the properties you will see in the AdditionalInfo field:</span></span>  
  
-   <span data-ttu-id="4717f-237">**ProcessingEngine**: 1 = SQL Server 2005, 2 = 새로운 요청 시 처리 엔진입니다.</span><span class="sxs-lookup"><span data-stu-id="4717f-237">**ProcessingEngine**: 1=SQL Server 2005, 2=The new On-demand Processing Engine.</span></span> <span data-ttu-id="4717f-238">대부분의 보고서에 값이 계속 1로 표시되면 보다 효율적이고 새로운 요청 시 처리 엔진을 활용할 수 있도록 보고서를 다시 디자인할 방법을 조사해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4717f-238">If a majority of your reports are still showing the value of 1, you may investigate how to redesign them so they utilize the newer and more efficient on-demand processing engine.</span></span>  
  
     `<ProcessingEngine>2</ProcessingEngine>`  
  
-   <span data-ttu-id="4717f-239">**ScalabilityTime**: 처리 엔진에서 확장 관련 작업을 수행 하는 데 걸린 시간 (밀리초)입니다.</span><span class="sxs-lookup"><span data-stu-id="4717f-239">**ScalabilityTime**: The number of milliseconds spent performing scale related operations in the processing engine.</span></span> <span data-ttu-id="4717f-240">값이 0이면 확장 작업에 추가 시간이 걸리지 않았으며, 해당 요청이 메모리 부담을 주지 않은 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="4717f-240">A value of 0 indicates that no additional time was spent on scale operations and a 0 also indicates the request was not under memory pressure.</span></span>  
  
    ```  
    <ScalabilityTime>  
        <Processing>0</Processing>  
    </ScalabilityTime>  
    ```  
  
-   <span data-ttu-id="4717f-241">**EstimatedMemoryUsageKB**: 특정 요청 중에 각 구성 요소에서 사용 되는 최대 메모리 양 (킬로바이트)입니다.</span><span class="sxs-lookup"><span data-stu-id="4717f-241">**EstimatedMemoryUsageKB**: An estimate of the peak amount of memory, in kilobytes, consumed by each component during a particular request.</span></span>  
  
    ```  
    <EstimatedMemoryUsageKB>  
        <Processing>38</Processing>  
    </EstimatedMemoryUsageKB>  
    ```  
  
-   <span data-ttu-id="4717f-242">**Dataextension**: 보고서에 사용 되는 데이터 확장 프로그램 또는 데이터 원본의 유형입니다.</span><span class="sxs-lookup"><span data-stu-id="4717f-242">**DataExtension**: The types of data extensions or data sources used in the report.</span></span> <span data-ttu-id="4717f-243">이 수치는 특정 데이터 원본의 발생 횟수입니다.</span><span class="sxs-lookup"><span data-stu-id="4717f-243">The number is a count of the number of occurrences of the particular data source.</span></span>  
  
    ```  
    <DataExtension>  
       <DAX>2</DAX>  
    </DataExtension>  
    ```  
  
-   <span data-ttu-id="4717f-244">**Externalimages** 값은 밀리초 단위로 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4717f-244">**ExternalImages**The value is in miliseconds.</span></span> <span data-ttu-id="4717f-245">이 데이터를 사용하여 성능 문제를 진단할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4717f-245">This data can be used to diagnose performance issues.</span></span> <span data-ttu-id="4717f-246">외부 웹 서버에서 이미지를 검색하는 데 필요한 시간으로 인해 전반적인 보고서 실행 속도가 느려질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4717f-246">The time needed to retrieve images from an external webserver may slow the overall report execution.</span></span> <span data-ttu-id="4717f-247">에 추가 되었습니다 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="4717f-247">Added in [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)].</span></span>  
  
    ```  
    <ExternalImages>  
        <Count>3</Count>  
        <ByteCount>9268</ByteCount>  
        <ResourceFetchTime>9</ResourceFetchTime>  
    </ExternalImages>  
    ```  
  
-   <span data-ttu-id="4717f-248">**연결**: 다단 구조입니다.</span><span class="sxs-lookup"><span data-stu-id="4717f-248">**Connections**: A multi-leveled structure.</span></span> <span data-ttu-id="4717f-249">에 추가 되었습니다 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="4717f-249">Added in [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)].</span></span>  
  
    ```  
    <Connections>  
        <Connection>  
          <ConnectionOpenTime>127</ConnectionOpenTime>  
          <DataSource>  
            <Name>DataSource1</Name>  
            <DataExtension>SQL</DataExtension>  
          </DataSource>  
          <DataSets>  
            <DataSet>  
              <Name>DataSet1</Name>  
              <RowsRead>16</RowsRead>  
              <TotalTimeDataRetrieval>655</TotalTimeDataRetrieval>  
              <QueryPrepareAndExecutionTime>94</QueryPrepareAndExecutionTime>  
              <ExecuteReaderTime>33</ExecuteReaderTime>  
              <DataReaderMappingTime>30</DataReaderMappingTime>  
              <DisposeDataReaderTime>1</DisposeDataReaderTime>  
            </DataSet>  
            <DataSet>  
              <Name>DataSet2</Name>  
              <RowsRead>3</RowsRead>  
              <TotalTimeDataRetrieval>16</TotalTimeDataRetrieval>  
              <QueryPrepareAndExecutionTime>2</QueryPrepareAndExecutionTime>  
              <ExecuteReaderTime>1</ExecuteReaderTime>  
              <DataReaderMappingTime>0</DataReaderMappingTime>  
              <DisposeDataReaderTime>0</DisposeDataReaderTime>  
            </DataSet>  
          </DataSets>  
        </Connection>  
    </Connections>  
  
    ```  
  
##  <a name="log-fields-executionlog2"></a><a name="bkmk_executionlog2"></a> <span data-ttu-id="4717f-250">로그 필드(ExecutionLog2)</span><span class="sxs-lookup"><span data-stu-id="4717f-250">Log Fields (ExecutionLog2)</span></span>  
 <span data-ttu-id="4717f-251">이 뷰에는 몇 가지 새로운 필드가 추가되었으며, 다른 일부 필드는 이름이 바뀌었습니다.</span><span class="sxs-lookup"><span data-stu-id="4717f-251">This view added a few new fields and renamed a few others.</span></span> <span data-ttu-id="4717f-252">다음은 ExecutionLog2 뷰에서 행을 검색하는 샘플 Transact SQL 문입니다.</span><span class="sxs-lookup"><span data-stu-id="4717f-252">The following is a sample Transact SQL statement to retrieve rows from the view ExecutionLog2.</span></span> <span data-ttu-id="4717f-253">이 샘플에서는 보고서 서버 데이터베이스 이름이 **ReportServer**라고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="4717f-253">The sample assumes the report server database is named **ReportServer**:</span></span>  
  
```  
Use ReportServer  
select * from ExecutionLog2 order by TimeStart DESC  
```  
  
 <span data-ttu-id="4717f-254">다음 표에서는 보고서 실행 로그에 캡처되는 데이터에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="4717f-254">The following table describes the data that is captured in the report execution log</span></span>  
  
|<span data-ttu-id="4717f-255">열</span><span class="sxs-lookup"><span data-stu-id="4717f-255">Column</span></span>|<span data-ttu-id="4717f-256">Description</span><span class="sxs-lookup"><span data-stu-id="4717f-256">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="4717f-257">InstanceName</span><span class="sxs-lookup"><span data-stu-id="4717f-257">InstanceName</span></span>|<span data-ttu-id="4717f-258">요청을 처리한 보고서 서버 인스턴스 이름</span><span class="sxs-lookup"><span data-stu-id="4717f-258">Name of the report server instance that handled the request.</span></span>|  
|<span data-ttu-id="4717f-259">ReportPath</span><span class="sxs-lookup"><span data-stu-id="4717f-259">ReportPath</span></span>|<span data-ttu-id="4717f-260">보고서의 경로 구조입니다.</span><span class="sxs-lookup"><span data-stu-id="4717f-260">The path structure to the report.</span></span>  <span data-ttu-id="4717f-261">예를 들어 보고서 관리자의 루트 폴더에 있고 이름이 "test"인 보고서의 ReportPath는 "/test"입니다.</span><span class="sxs-lookup"><span data-stu-id="4717f-261">For example a report named "test" which is the in root folder in Report Manager, would have a ReportPath of "/test".</span></span><br /><br /> <span data-ttu-id="4717f-262">보고서 관리자에서 "samples" 폴더에 저장된 이름이 "test"인 보고서의 ReportPath는 "/Samples/test"입니다.</span><span class="sxs-lookup"><span data-stu-id="4717f-262">A report named "test" that is saved in the folder "samples" on Report Manager , will have a ReportPath of "/Samples/test/"</span></span>|  
|<span data-ttu-id="4717f-263">UserName</span><span class="sxs-lookup"><span data-stu-id="4717f-263">UserName</span></span>|<span data-ttu-id="4717f-264">사용자 식별자</span><span class="sxs-lookup"><span data-stu-id="4717f-264">User identifier.</span></span>|  
|<span data-ttu-id="4717f-265">ExecutionID</span><span class="sxs-lookup"><span data-stu-id="4717f-265">ExecutionID</span></span>||  
|<span data-ttu-id="4717f-266">RequestType</span><span class="sxs-lookup"><span data-stu-id="4717f-266">RequestType</span></span>|<span data-ttu-id="4717f-267">요청 형식(사용자 또는 시스템)</span><span class="sxs-lookup"><span data-stu-id="4717f-267">Request type (either user or system).</span></span>|  
|<span data-ttu-id="4717f-268">서식</span><span class="sxs-lookup"><span data-stu-id="4717f-268">Format</span></span>|<span data-ttu-id="4717f-269">렌더링 형식</span><span class="sxs-lookup"><span data-stu-id="4717f-269">Rendering format.</span></span>|  
|<span data-ttu-id="4717f-270">매개 변수</span><span class="sxs-lookup"><span data-stu-id="4717f-270">Parameters</span></span>|<span data-ttu-id="4717f-271">보고서 실행에 사용된 매개 변수 값</span><span class="sxs-lookup"><span data-stu-id="4717f-271">Parameter values used for a report execution.</span></span>|  
|<span data-ttu-id="4717f-272">ReportAction</span><span class="sxs-lookup"><span data-stu-id="4717f-272">ReportAction</span></span>|<span data-ttu-id="4717f-273">가능한 값: Render, Sort, BookMarkNavigation, DocumentNavigation, GetDocumentMap, Findstring</span><span class="sxs-lookup"><span data-stu-id="4717f-273">Possible values: Render, Sort, BookMarkNavigation, DocumentNavigation, GetDocumentMap, Findstring</span></span>|  
|<span data-ttu-id="4717f-274">TimeStart</span><span class="sxs-lookup"><span data-stu-id="4717f-274">TimeStart</span></span>|<span data-ttu-id="4717f-275">보고서 처리 기간을 나타내는 시작 및 중지 시간</span><span class="sxs-lookup"><span data-stu-id="4717f-275">Start and stop times that indicate the duration of a report process.</span></span>|  
|<span data-ttu-id="4717f-276">TimeEnd</span><span class="sxs-lookup"><span data-stu-id="4717f-276">TimeEnd</span></span>||  
|<span data-ttu-id="4717f-277">TimeDataRetrieval</span><span class="sxs-lookup"><span data-stu-id="4717f-277">TimeDataRetrieval</span></span>|<span data-ttu-id="4717f-278">데이터 검색, 보고서 처리 및 보고서 렌더링에 걸린 시간(밀리초 단위)</span><span class="sxs-lookup"><span data-stu-id="4717f-278">Number of milliseconds spent retrieving the data, processing the report, and rendering the report.</span></span>|  
|<span data-ttu-id="4717f-279">TimeProcessing</span><span class="sxs-lookup"><span data-stu-id="4717f-279">TimeProcessing</span></span>||  
|<span data-ttu-id="4717f-280">TimeRendering</span><span class="sxs-lookup"><span data-stu-id="4717f-280">TimeRendering</span></span>||  
|<span data-ttu-id="4717f-281">원본</span><span class="sxs-lookup"><span data-stu-id="4717f-281">Source</span></span>|<span data-ttu-id="4717f-282">보고서 실행 원본(1=라이브, 2=캐시, 3=스냅샷, 4=기록)</span><span class="sxs-lookup"><span data-stu-id="4717f-282">Source of the report execution (1=Live, 2=Cache, 3=Snapshot, 4=History).</span></span>|  
|<span data-ttu-id="4717f-283">상태</span><span class="sxs-lookup"><span data-stu-id="4717f-283">Status</span></span>|<span data-ttu-id="4717f-284">상태(rsSuccess 또는 오류 코드: 여러 개의 오류가 발생하면 첫 번째 오류만 기록됨)</span><span class="sxs-lookup"><span data-stu-id="4717f-284">Status (either rsSuccess or an error code; if multiple errors occur, only the first error is recorded).</span></span>|  
|<span data-ttu-id="4717f-285">ByteCount</span><span class="sxs-lookup"><span data-stu-id="4717f-285">ByteCount</span></span>|<span data-ttu-id="4717f-286">렌더링된 보고서 크기(바이트)</span><span class="sxs-lookup"><span data-stu-id="4717f-286">Size of rendered reports in bytes.</span></span>|  
|<span data-ttu-id="4717f-287">RowCount</span><span class="sxs-lookup"><span data-stu-id="4717f-287">RowCount</span></span>|<span data-ttu-id="4717f-288">쿼리에서 반환된 행 수</span><span class="sxs-lookup"><span data-stu-id="4717f-288">Number of rows returned from queries.</span></span>|  
|<span data-ttu-id="4717f-289">AdditionalInfo</span><span class="sxs-lookup"><span data-stu-id="4717f-289">AdditionalInfo</span></span>|<span data-ttu-id="4717f-290">실행에 대한 추가 정보가 포함된 XML 속성 모음</span><span class="sxs-lookup"><span data-stu-id="4717f-290">An XML property bag containing additional information about the execution.</span></span>|  
  
##  <a name="log-fields-executionlog"></a><a name="bkmk_executionlog"></a> <span data-ttu-id="4717f-291">로그 필드(ExecutionLog)</span><span class="sxs-lookup"><span data-stu-id="4717f-291">Log Fields (ExecutionLog)</span></span>  
 <span data-ttu-id="4717f-292">다음은 ExecutionLog 뷰에서 행을 검색하는 샘플 Transact SQL 문입니다.</span><span class="sxs-lookup"><span data-stu-id="4717f-292">The following is a sample Transact SQL statement to retrieve rows from the view ExecutionLog.</span></span> <span data-ttu-id="4717f-293">이 샘플에서는 보고서 서버 데이터베이스 이름이 **ReportServer**라고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="4717f-293">The sample assumes the report server database is named **ReportServer**:</span></span>  
  
```  
Use ReportServer  
select * from ExecutionLog order by TimeStart DESC  
  
```  
  
 <span data-ttu-id="4717f-294">다음 표에서는 보고서 실행 로그에 캡처되는 데이터에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="4717f-294">The following table describes the data that is captured in the report execution log</span></span>  
  
|<span data-ttu-id="4717f-295">열</span><span class="sxs-lookup"><span data-stu-id="4717f-295">Column</span></span>|<span data-ttu-id="4717f-296">Description</span><span class="sxs-lookup"><span data-stu-id="4717f-296">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="4717f-297">InstanceName</span><span class="sxs-lookup"><span data-stu-id="4717f-297">InstanceName</span></span>|<span data-ttu-id="4717f-298">요청을 처리한 보고서 서버 인스턴스 이름</span><span class="sxs-lookup"><span data-stu-id="4717f-298">Name of the report server instance that handled the request.</span></span>|  
|<span data-ttu-id="4717f-299">ReportID</span><span class="sxs-lookup"><span data-stu-id="4717f-299">ReportID</span></span>|<span data-ttu-id="4717f-300">보고서 식별자</span><span class="sxs-lookup"><span data-stu-id="4717f-300">Report identifier.</span></span>|  
|<span data-ttu-id="4717f-301">UserName</span><span class="sxs-lookup"><span data-stu-id="4717f-301">UserName</span></span>|<span data-ttu-id="4717f-302">사용자 식별자</span><span class="sxs-lookup"><span data-stu-id="4717f-302">User identifier.</span></span>|  
|<span data-ttu-id="4717f-303">RequestType</span><span class="sxs-lookup"><span data-stu-id="4717f-303">RequestType</span></span>|<span data-ttu-id="4717f-304">가능한 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="4717f-304">Possible values:</span></span><br /><br /> <span data-ttu-id="4717f-305">True = 구독 요청</span><span class="sxs-lookup"><span data-stu-id="4717f-305">True = A Subscription request</span></span><br /><br /> <span data-ttu-id="4717f-306">False= 대화형 요청</span><span class="sxs-lookup"><span data-stu-id="4717f-306">False= An Interactive request</span></span>|  
|<span data-ttu-id="4717f-307">서식</span><span class="sxs-lookup"><span data-stu-id="4717f-307">Format</span></span>|<span data-ttu-id="4717f-308">렌더링 형식</span><span class="sxs-lookup"><span data-stu-id="4717f-308">Rendering format.</span></span>|  
|<span data-ttu-id="4717f-309">매개 변수</span><span class="sxs-lookup"><span data-stu-id="4717f-309">Parameters</span></span>|<span data-ttu-id="4717f-310">보고서 실행에 사용된 매개 변수 값</span><span class="sxs-lookup"><span data-stu-id="4717f-310">Parameter values used for a report execution.</span></span>|  
|<span data-ttu-id="4717f-311">TimeStart</span><span class="sxs-lookup"><span data-stu-id="4717f-311">TimeStart</span></span>|<span data-ttu-id="4717f-312">보고서 처리 기간을 나타내는 시작 및 중지 시간</span><span class="sxs-lookup"><span data-stu-id="4717f-312">Start and stop times that indicate the duration of a report process.</span></span>|  
|<span data-ttu-id="4717f-313">TimeEnd</span><span class="sxs-lookup"><span data-stu-id="4717f-313">TimeEnd</span></span>||  
|<span data-ttu-id="4717f-314">TimeDataRetrieval</span><span class="sxs-lookup"><span data-stu-id="4717f-314">TimeDataRetrieval</span></span>|<span data-ttu-id="4717f-315">데이터 검색, 보고서 처리 및 보고서 렌더링에 걸린 시간(밀리초 단위)</span><span class="sxs-lookup"><span data-stu-id="4717f-315">Number of milliseconds spent retrieving the data, processing the report, and rendering the report.</span></span>|  
|<span data-ttu-id="4717f-316">TimeProcessing</span><span class="sxs-lookup"><span data-stu-id="4717f-316">TimeProcessing</span></span>||  
|<span data-ttu-id="4717f-317">TimeRendering</span><span class="sxs-lookup"><span data-stu-id="4717f-317">TimeRendering</span></span>||  
|<span data-ttu-id="4717f-318">원본</span><span class="sxs-lookup"><span data-stu-id="4717f-318">Source</span></span>|<span data-ttu-id="4717f-319">보고서 실행의 원본입니다.</span><span class="sxs-lookup"><span data-stu-id="4717f-319">Source of the report execution.</span></span> <span data-ttu-id="4717f-320">가능한 값: 1=라이브, 2=캐시, 3=스냅샷, 4=기록, 5=임시, 6=세션, 7=RDCE입니다.</span><span class="sxs-lookup"><span data-stu-id="4717f-320">Possible values: (1=Live, 2=Cache, 3=Snapshot, 4=History, 5=Adhoc, 6=Session, 7=RDCE).</span></span>|  
|<span data-ttu-id="4717f-321">상태</span><span class="sxs-lookup"><span data-stu-id="4717f-321">Status</span></span>|<span data-ttu-id="4717f-322">가능한 값: rsSuccess, rsProcessingAborted 또는 오류 코드입니다.</span><span class="sxs-lookup"><span data-stu-id="4717f-322">Possible values: rsSuccess, rsProcessingAborted, or an error code.</span></span> <span data-ttu-id="4717f-323">여러 오류가 발생한 경우 첫 번째 오류만 기록됩니다.</span><span class="sxs-lookup"><span data-stu-id="4717f-323">If multiple errors occur, only the first error is recorded.</span></span>|  
|<span data-ttu-id="4717f-324">ByteCount</span><span class="sxs-lookup"><span data-stu-id="4717f-324">ByteCount</span></span>|<span data-ttu-id="4717f-325">렌더링된 보고서 크기(바이트)</span><span class="sxs-lookup"><span data-stu-id="4717f-325">Size of rendered reports in bytes.</span></span>|  
|<span data-ttu-id="4717f-326">RowCount</span><span class="sxs-lookup"><span data-stu-id="4717f-326">RowCount</span></span>|<span data-ttu-id="4717f-327">쿼리에서 반환된 행 수</span><span class="sxs-lookup"><span data-stu-id="4717f-327">Number of rows returned from queries.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4717f-328">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4717f-328">See Also</span></span>  
 <span data-ttu-id="4717f-329">[SharePoint 추적 로그 &#40;ULS에 대 한 Reporting Services 이벤트 설정&#41;](turn-on-reporting-services-events-for-the-sharepoint-trace-log-uls.md) </span><span class="sxs-lookup"><span data-stu-id="4717f-329">[Turn on Reporting Services events for the SharePoint trace log &#40;ULS&#41;](turn-on-reporting-services-events-for-the-sharepoint-trace-log-uls.md) </span></span>  
 <span data-ttu-id="4717f-330">[Reporting Services 로그 파일 및 소스](../report-server/reporting-services-log-files-and-sources.md) </span><span class="sxs-lookup"><span data-stu-id="4717f-330">[Reporting Services Log Files and Sources](../report-server/reporting-services-log-files-and-sources.md) </span></span>  
 [<span data-ttu-id="4717f-331">오류 및 이벤트 참조&#40;Reporting Services&#41;</span><span class="sxs-lookup"><span data-stu-id="4717f-331">Errors and Events Reference &#40;Reporting Services&#41;</span></span>](../troubleshooting/errors-and-events-reference-reporting-services.md)  
  
  
