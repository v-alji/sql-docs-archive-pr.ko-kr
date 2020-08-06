---
title: SharePoint 추적 로그에 대한 Reporting Services 이벤트 설정(ULS) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 81110ef6-4289-405c-a931-e7e9f49e69ba
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b7d1b0a936c234035baf18ca947661de2663195a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650619"
---
# <a name="turn-on-reporting-services-events-for-the-sharepoint-trace-log-uls"></a><span data-ttu-id="235b0-102">SharePoint 추적 로그에 대한 Reporting Services 이벤트 설정(ULS)</span><span class="sxs-lookup"><span data-stu-id="235b0-102">Turn on Reporting Services events for the SharePoint trace log (ULS)</span></span>
  <span data-ttu-id="235b0-103">[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]부터 SharePoint 모드의 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 서버는 SharePoint ULS(통합 로깅 서비스) 추적 로그에 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 이벤트를 기록할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="235b0-103">Starting with [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] servers in SharePoint mode can write [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] events to the SharePoint Unified Logging Service (ULS) trace log.</span></span> [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] <span data-ttu-id="235b0-104">관련 범주는 SharePoint 중앙 관리의 모니터링 페이지에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="235b0-104">specific categories are available on the Monitoring page of SharePoint Central Administration.</span></span>

 <span data-ttu-id="235b0-105">항목 내용</span><span class="sxs-lookup"><span data-stu-id="235b0-105">In this Topic:</span></span>

-   [<span data-ttu-id="235b0-106">일반 ULS 로그 권장 사항</span><span class="sxs-lookup"><span data-stu-id="235b0-106">General ULS Log Recommendations</span></span>](#bkmk_general)

-   [<span data-ttu-id="235b0-107">Reporting Services 범주에서 Reporting Services 이벤트를 설정 및 해제하려면</span><span class="sxs-lookup"><span data-stu-id="235b0-107">To turn on and off Reporting Services events in the Reporting Services Category</span></span>](#bkmk_turnon)

-   [<span data-ttu-id="235b0-108">권장 구성</span><span class="sxs-lookup"><span data-stu-id="235b0-108">Recommended Configuration</span></span>](#bkmk_recommended)

-   [<span data-ttu-id="235b0-109">로그 항목 읽기</span><span class="sxs-lookup"><span data-stu-id="235b0-109">Reading the logs entries</span></span>](#bkmk_readentries)

-   [<span data-ttu-id="235b0-110">SQL Server Reporting Services 이벤트 목록</span><span class="sxs-lookup"><span data-stu-id="235b0-110">List of SQL Server Reporting Services Events</span></span>](#bkmk_list)

-   [<span data-ttu-id="235b0-111">PowerShell에서 로그 파일 보기</span><span class="sxs-lookup"><span data-stu-id="235b0-111">View a Log file with PowerShell</span></span>](#bkmk_powershell)

-   [<span data-ttu-id="235b0-112">추적 로그 위치</span><span class="sxs-lookup"><span data-stu-id="235b0-112">Trace Log Location</span></span>](#bkmk_trace)

##  <a name="general-uls-log-recommendations"></a><a name="bkmk_general"></a> <span data-ttu-id="235b0-113">일반 ULS 로그 권장 사항</span><span class="sxs-lookup"><span data-stu-id="235b0-113">General ULS Log Recommendations</span></span>
 <span data-ttu-id="235b0-114">다음 표에서는 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 환경을 모니터링하는 데 권장되는 이벤트 범주 및 수준을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="235b0-114">The following table lists event categories and levels that are recommended for monitoring a [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] environment..</span></span> <span data-ttu-id="235b0-115">이벤트를 기록하면 각 항목에 이벤트 기록 시간, 프로세스 이름 및 스레드 ID가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="235b0-115">When an event is logged, each entry includes the time the event was logged, the process name, and the thread ID.</span></span>

|<span data-ttu-id="235b0-116">Category</span><span class="sxs-lookup"><span data-stu-id="235b0-116">Category</span></span>|<span data-ttu-id="235b0-117">Level</span><span class="sxs-lookup"><span data-stu-id="235b0-117">Level</span></span>|<span data-ttu-id="235b0-118">Description</span><span class="sxs-lookup"><span data-stu-id="235b0-118">Description</span></span>|
|--------------|-----------|-----------------|
|<span data-ttu-id="235b0-119">데이터베이스</span><span class="sxs-lookup"><span data-stu-id="235b0-119">Database</span></span>|<span data-ttu-id="235b0-120">자세히</span><span class="sxs-lookup"><span data-stu-id="235b0-120">Verbose</span></span>|<span data-ttu-id="235b0-121">데이터베이스 액세스를 포함하는 이벤트를 기록합니다.</span><span class="sxs-lookup"><span data-stu-id="235b0-121">Logs events that involve database access.</span></span>|
|<span data-ttu-id="235b0-122">일반</span><span class="sxs-lookup"><span data-stu-id="235b0-122">General</span></span>|<span data-ttu-id="235b0-123">자세히</span><span class="sxs-lookup"><span data-stu-id="235b0-123">Verbose</span></span>|<span data-ttu-id="235b0-124">다음 항목에 대한 액세스를 포함하는 이벤트를 기록합니다.</span><span class="sxs-lookup"><span data-stu-id="235b0-124">Logs events that involve access to the following items:</span></span><br /><br /> [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] <span data-ttu-id="235b0-125">웹 페이지</span><span class="sxs-lookup"><span data-stu-id="235b0-125">Web pages</span></span><br /><br /> <span data-ttu-id="235b0-126">보고서 뷰어 HTTP 처리기</span><span class="sxs-lookup"><span data-stu-id="235b0-126">Report Viewer HTTP handler</span></span><br /><br /> <span data-ttu-id="235b0-127">보고서 액세스 파일(.rdl)</span><span class="sxs-lookup"><span data-stu-id="235b0-127">Report access (.rdl files)</span></span><br /><br /> <span data-ttu-id="235b0-128">데이터 원본 파일(.rsds)</span><span class="sxs-lookup"><span data-stu-id="235b0-128">Data sources (.rsds files)</span></span><br /><br /> <span data-ttu-id="235b0-129">SharePoint 사이트의 URL(.smdl 파일)</span><span class="sxs-lookup"><span data-stu-id="235b0-129">URLs on the SharePoint site (.smdl files)</span></span>|
|<span data-ttu-id="235b0-130">Office Server 일반</span><span class="sxs-lookup"><span data-stu-id="235b0-130">Office Server General</span></span>|<span data-ttu-id="235b0-131">예외</span><span class="sxs-lookup"><span data-stu-id="235b0-131">Exception</span></span>|<span data-ttu-id="235b0-132">로그온 실패를 기록합니다.</span><span class="sxs-lookup"><span data-stu-id="235b0-132">Logs logon failures.</span></span>|
|<span data-ttu-id="235b0-133">토폴로지</span><span class="sxs-lookup"><span data-stu-id="235b0-133">Topology</span></span>|<span data-ttu-id="235b0-134">자세히</span><span class="sxs-lookup"><span data-stu-id="235b0-134">Verbose</span></span>|<span data-ttu-id="235b0-135">현재 사용자 정보를 기록합니다.</span><span class="sxs-lookup"><span data-stu-id="235b0-135">Logs current user information.</span></span>|
|<span data-ttu-id="235b0-136">웹 파트</span><span class="sxs-lookup"><span data-stu-id="235b0-136">Web Parts</span></span>|<span data-ttu-id="235b0-137">자세히</span><span class="sxs-lookup"><span data-stu-id="235b0-137">Verbose</span></span>|<span data-ttu-id="235b0-138">보고서 뷰어 웹 파트에 대한 액세스를 포함하는 이벤트를 기록합니다.</span><span class="sxs-lookup"><span data-stu-id="235b0-138">Logs events that involve access to the Report Viewer Web Part.</span></span>|

##  <a name="to-turn-on-and-off-reporting-services-events-in-the-reporting-services-category"></a><a name="bkmk_turnon"></a> <span data-ttu-id="235b0-139">Reporting Services 범주에서 Reporting Services 이벤트를 설정 및 해제하려면</span><span class="sxs-lookup"><span data-stu-id="235b0-139">To turn on and off Reporting Services events in the Reporting Services Category</span></span>

1.  <span data-ttu-id="235b0-140">SharePoint 중앙 관리에서</span><span class="sxs-lookup"><span data-stu-id="235b0-140">From SharePoint Central Administration</span></span>

2.  <span data-ttu-id="235b0-141">**모니터링**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="235b0-141">Click **Monitoring**.</span></span>

3.  <span data-ttu-id="235b0-142">**보고** 그룹에서 **진단 로깅 구성** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="235b0-142">Click **Configure Diagnostic Logging** in the **Reporting** group.</span></span>

4.  <span data-ttu-id="235b0-143">범주 목록에서 **SQL Server Reporting Services** 를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="235b0-143">Find **SQL Server Reporting Services** in the category list.</span></span>

5.  <span data-ttu-id="235b0-144">더하기 기호(+)를 클릭하여 **SQL Server Reporting Services**의 하위 범주를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="235b0-144">Click the plus symbol (+) to expand the sub categories under **SQL Server Reporting Services**.</span></span>

6.  <span data-ttu-id="235b0-145">추적 로그에 추가할 하위 범주를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="235b0-145">Select the subcategories to be added to the trace log.</span></span>

7.  <span data-ttu-id="235b0-146">범주 목록 아래쪽에서 **추적 로그에 보고할 최소 중요 이벤트**에 대한 이벤트 수준을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="235b0-146">At the bottom of the categories list, select an event level for the **Least critical event to report to the trace log**.</span></span> <span data-ttu-id="235b0-147">**없음** 을 선택하여 추적을 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="235b0-147">Select **None** to disable tracing.</span></span>

> [!NOTE]
>  <span data-ttu-id="235b0-148">**이벤트 로그에 보고할 최소 중요 이벤트** 옵션은 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]에서 지원되지 않으므로</span><span class="sxs-lookup"><span data-stu-id="235b0-148">The option **Least critical event to report to the event log** is not supported by [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="235b0-149">무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="235b0-149">The option is ignored.</span></span>

##  <a name="recommended-configuration"></a><a name="bkmk_recommended"></a> <span data-ttu-id="235b0-150">권장 구성</span><span class="sxs-lookup"><span data-stu-id="235b0-150">Recommended Configuration</span></span>
 <span data-ttu-id="235b0-151">다음 로깅 옵션을 표준 구성으로 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="235b0-151">The following logging options are recommended as a standard configuration:</span></span>

-   <span data-ttu-id="235b0-152">**HTTP 리디렉터**</span><span class="sxs-lookup"><span data-stu-id="235b0-152">**HTTP Redirector**</span></span>

-   <span data-ttu-id="235b0-153">**SOAP 클라이언트 프록시**</span><span class="sxs-lookup"><span data-stu-id="235b0-153">**SOAP Client Proxy**</span></span>

-   <span data-ttu-id="235b0-154">구성에 문제가 있으면 **구성 페이지**를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="235b0-154">If you are experiencing issues with configuration, add **Configuration Pages**.</span></span>

 <span data-ttu-id="235b0-155">다음 PowerShell cmdlet을 사용하여 모든 현재 팜 진단 로그 설정을 검토할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="235b0-155">You can review all of the current farm diagnostic log settings with the following PowerShell cmdlet:</span></span>

```powershell
Get-SPDiagnosticConfig
```

##  <a name="reading-the-logs-entries"></a><a name="bkmk_readentries"></a> <span data-ttu-id="235b0-156">로그 항목 읽기</span><span class="sxs-lookup"><span data-stu-id="235b0-156">Reading the logs entries</span></span>
 <span data-ttu-id="235b0-157">로그에서 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 항목의 서식은 다음과 같은 방법으로 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="235b0-157">The [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] entries in the log are formatted in the following way.</span></span>

1.  <span data-ttu-id="235b0-158">**제품: SQL Server Reporting Services**</span><span class="sxs-lookup"><span data-stu-id="235b0-158">**Product:SQL Server Reporting Services**</span></span>

2.  <span data-ttu-id="235b0-159">**범주:** 서버 관련 이벤트는 이름의 시작 부분에 "Report Server"라는 문자가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="235b0-159">**Category:** Events related to the server will have the characters "Report Server", at the beginning of the name.</span></span> <span data-ttu-id="235b0-160">예: "Report Server Alerting Runtime" 이러한 이벤트는 보고서 서버 로그 파일에도 기록됩니다.</span><span class="sxs-lookup"><span data-stu-id="235b0-160">For example "Report Server Alerting Runtime" These events are also logged to the report server log files.</span></span>

3.  <span data-ttu-id="235b0-161">**범주:** 웹 프런트 엔드 구성 요소와 관련된 이벤트나 웹 프런트 엔드 구성 요소로부터 전달되는 이벤트에는 "Report Server"가 포함되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="235b0-161">**Category:** Events related to or communicated from a web front-end component do not contain "Report Server".</span></span> <span data-ttu-id="235b0-162">예 "Service Application Proxy" Report Server Alerting Runtime"</span><span class="sxs-lookup"><span data-stu-id="235b0-162">For example "Service Application Proxy" Report Server Alerting Runtime".</span></span> <span data-ttu-id="235b0-163">WFE 항목은 CorrelationID를 포함하지만 서버 항목은 CorrelationID를 포함하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="235b0-163">The WFE entries do contain a CorrelationID but the server entries do not.</span></span>

##  <a name="list-of-sql-server-reporting-services-events"></a><a name="bkmk_list"></a> <span data-ttu-id="235b0-164">SQL Server Reporting Services 이벤트 목록</span><span class="sxs-lookup"><span data-stu-id="235b0-164">List of SQL Server Reporting Services Events</span></span>
 <span data-ttu-id="235b0-165">다음 표에는 SQL Server Reporting Services 범주의 이벤트 목록이 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="235b0-165">The following table is a list of the events in the SQL Server Reporting Services Category:</span></span>

|<span data-ttu-id="235b0-166">영역 이름</span><span class="sxs-lookup"><span data-stu-id="235b0-166">Area Name</span></span>|<span data-ttu-id="235b0-167">설명 또는 샘플 항목</span><span class="sxs-lookup"><span data-stu-id="235b0-167">Description or sample entries</span></span>|
|---------------|-----------------------------------|
|<span data-ttu-id="235b0-168">구성 페이지</span><span class="sxs-lookup"><span data-stu-id="235b0-168">Configuration Pages</span></span>||
|<span data-ttu-id="235b0-169">HTTP 리디렉터</span><span class="sxs-lookup"><span data-stu-id="235b0-169">HTTP Redirector</span></span>||
|<span data-ttu-id="235b0-170">로컬 모드 처리</span><span class="sxs-lookup"><span data-stu-id="235b0-170">Local Mode Processing</span></span>||
|<span data-ttu-id="235b0-171">로컬 모드 렌더링</span><span class="sxs-lookup"><span data-stu-id="235b0-171">Local Mode Rendering</span></span>||
|<span data-ttu-id="235b0-172">SOAP 클라이언트 프록시</span><span class="sxs-lookup"><span data-stu-id="235b0-172">SOAP Client Proxy</span></span>||
|<span data-ttu-id="235b0-173">UI 페이지</span><span class="sxs-lookup"><span data-stu-id="235b0-173">UI Pages</span></span>||
|<span data-ttu-id="235b0-174">파워 뷰</span><span class="sxs-lookup"><span data-stu-id="235b0-174">Power View</span></span>|<span data-ttu-id="235b0-175">**LogClientTraceEvents** API에 쓴 로그 항목입니다.</span><span class="sxs-lookup"><span data-stu-id="235b0-175">Log entries that were written to the **LogClientTraceEvents** API.</span></span> <span data-ttu-id="235b0-176">이러한 항목은 [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] Enterprise Edition 용 추가 기능의 기능인를 포함 하 여 클라이언트 응용 프로그램에서 시작 됩니다 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[SPS2010](../../includes/sps2010-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="235b0-176">These entries are sourced from client applications, including [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)], a feature of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] Add-in for [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[SPS2010](../../includes/sps2010-md.md)] Enterprise Edition.</span></span><br /><br /> <span data-ttu-id="235b0-177">LogClientTraceEvents API의 모든 로그 항목은 "SQL Server Reporting Services" 및 "파워 뷰" **영역**의 **범주**에 기록됩니다.</span><span class="sxs-lookup"><span data-stu-id="235b0-177">All log entries from the LogClientTraceEvents API will be logged under the **Category** of "SQL Server Reporting Services" and the **Area** of "Power View".</span></span><br /><br /> <span data-ttu-id="235b0-178">"파워 뷰" 영역으로 기록된 항목의 내용은 클라이언트 애플리케이션에 의해 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="235b0-178">The content of entries logged with the area of "Power View" is determined by the client application.</span></span>|
|<span data-ttu-id="235b0-179">보고서 서버 경고 런타임</span><span class="sxs-lookup"><span data-stu-id="235b0-179">Report Server Alerting Runtime</span></span>||
|<span data-ttu-id="235b0-180">보고서 서버 응용 프로그램 도메인 관리자</span><span class="sxs-lookup"><span data-stu-id="235b0-180">Report Server App Domain Manager</span></span>||
|<span data-ttu-id="235b0-181">보고서 서버 버퍼링 응답</span><span class="sxs-lookup"><span data-stu-id="235b0-181">Report Server Buffered Response</span></span>||
|<span data-ttu-id="235b0-182">보고서 서버 캐시</span><span class="sxs-lookup"><span data-stu-id="235b0-182">Report Server Cache</span></span>||
|<span data-ttu-id="235b0-183">보고서 서버 카탈로그</span><span class="sxs-lookup"><span data-stu-id="235b0-183">Report Server Catalog</span></span>||
|<span data-ttu-id="235b0-184">보고서 서버 청크</span><span class="sxs-lookup"><span data-stu-id="235b0-184">Report Server Chunk</span></span>||
|<span data-ttu-id="235b0-185">보고서 서버 정리</span><span class="sxs-lookup"><span data-stu-id="235b0-185">Report Server Cleanup</span></span>||
|<span data-ttu-id="235b0-186">보고서 서버 구성 관리자</span><span class="sxs-lookup"><span data-stu-id="235b0-186">Report Server Configuration Manager</span></span>|<span data-ttu-id="235b0-187">샘플 항목:</span><span class="sxs-lookup"><span data-stu-id="235b0-187">Sample entries:</span></span><br /><br /> <span data-ttu-id="235b0-188">MediumUsing 보고서 서버 내부 url http://localhost:80/ReportServer.</span><span class="sxs-lookup"><span data-stu-id="235b0-188">MediumUsing report server internal url http://localhost:80/ReportServer.</span></span><br /><br /> <span data-ttu-id="235b0-189">UnexpectedMissing 또는 잘못된 ExtendedProtectionLevel 설정</span><span class="sxs-lookup"><span data-stu-id="235b0-189">UnexpectedMissing or Invalid ExtendedProtectionLevel setting</span></span>|
|<span data-ttu-id="235b0-190">보고서 서버 암호화</span><span class="sxs-lookup"><span data-stu-id="235b0-190">Report Server Crypto</span></span>||
|<span data-ttu-id="235b0-191">보고서 서버 데이터 확장 프로그램</span><span class="sxs-lookup"><span data-stu-id="235b0-191">Report Server Data Extension</span></span>||
|<span data-ttu-id="235b0-192">보고서 서버 DB 폴링</span><span class="sxs-lookup"><span data-stu-id="235b0-192">Report Server DB Polling</span></span>||
|<span data-ttu-id="235b0-193">보고서 서버 기본값</span><span class="sxs-lookup"><span data-stu-id="235b0-193">Report Server Default</span></span>||
|<span data-ttu-id="235b0-194">보고서 서버 전자 메일 확장 프로그램</span><span class="sxs-lookup"><span data-stu-id="235b0-194">Report Server Email Extension</span></span>||
|<span data-ttu-id="235b0-195">보고서 서버 Excel 렌더러</span><span class="sxs-lookup"><span data-stu-id="235b0-195">Report Server Excel Renderer</span></span>||
|<span data-ttu-id="235b0-196">보고서 서버 확장 프로그램 팩터리</span><span class="sxs-lookup"><span data-stu-id="235b0-196">Report Server Extension Factory</span></span>||
|<span data-ttu-id="235b0-197">보고서 서버 HTTP 런타임</span><span class="sxs-lookup"><span data-stu-id="235b0-197">Report Server HTTP Runtime</span></span>||
|<span data-ttu-id="235b0-198">보고서 서버 이미지 렌더러</span><span class="sxs-lookup"><span data-stu-id="235b0-198">Report Server Image Renderer</span></span>||
|<span data-ttu-id="235b0-199">보고서 서버 메모리 모니터링</span><span class="sxs-lookup"><span data-stu-id="235b0-199">Report Server Memory Monitoring</span></span>||
|<span data-ttu-id="235b0-200">보고서 서버 알림</span><span class="sxs-lookup"><span data-stu-id="235b0-200">Report Server Notification</span></span>||
|<span data-ttu-id="235b0-201">보고서 서버 처리</span><span class="sxs-lookup"><span data-stu-id="235b0-201">Report Server Processing</span></span>||
|<span data-ttu-id="235b0-202">보고서 서버 공급자</span><span class="sxs-lookup"><span data-stu-id="235b0-202">Report Server Provider</span></span>||
|<span data-ttu-id="235b0-203">보고서 서버 렌더링</span><span class="sxs-lookup"><span data-stu-id="235b0-203">Report Server Rendering</span></span>||
|<span data-ttu-id="235b0-204">보고서 서버 보고서 미리 보기</span><span class="sxs-lookup"><span data-stu-id="235b0-204">Report Server Report Preview</span></span>||
|<span data-ttu-id="235b0-205">보고서 서버 리소스 유틸리티</span><span class="sxs-lookup"><span data-stu-id="235b0-205">Report Server Resource Utility</span></span>|<span data-ttu-id="235b0-206">샘플 항목:</span><span class="sxs-lookup"><span data-stu-id="235b0-206">Sample Entries:</span></span><br /><br /> <span data-ttu-id="235b0-207">MediumReporting 서비스 시작 SKU: 평가</span><span class="sxs-lookup"><span data-stu-id="235b0-207">MediumReporting Services starting SKU: Evaluation</span></span><br /><br /> <span data-ttu-id="235b0-208">MediumEvaluation 복사: 180일 남음</span><span class="sxs-lookup"><span data-stu-id="235b0-208">MediumEvaluation copy: 180 days left</span></span>|
|<span data-ttu-id="235b0-209">보고서 서버 실행 작업</span><span class="sxs-lookup"><span data-stu-id="235b0-209">Report Server Running Jobs</span></span>||
|<span data-ttu-id="235b0-210">보고서 서버 실행 요청</span><span class="sxs-lookup"><span data-stu-id="235b0-210">Report Server Running Requests</span></span>||
|<span data-ttu-id="235b0-211">보고서 서버 예약</span><span class="sxs-lookup"><span data-stu-id="235b0-211">Report Server Schedule</span></span>||
|<span data-ttu-id="235b0-212">보고서 서버 보안</span><span class="sxs-lookup"><span data-stu-id="235b0-212">Report Server Security</span></span>||
|<span data-ttu-id="235b0-213">보고서 서버 서비스 컨트롤러</span><span class="sxs-lookup"><span data-stu-id="235b0-213">Report Server Service Controller</span></span>||
|<span data-ttu-id="235b0-214">보고서 서버 세션</span><span class="sxs-lookup"><span data-stu-id="235b0-214">Report Server Session</span></span>||
|<span data-ttu-id="235b0-215">보고서 서버 구독</span><span class="sxs-lookup"><span data-stu-id="235b0-215">Report Server Subscription</span></span>||
|<span data-ttu-id="235b0-216">보고서 서버 WCF 런타임</span><span class="sxs-lookup"><span data-stu-id="235b0-216">Report Server WCF Runtime</span></span>||
|<span data-ttu-id="235b0-217">보고서 서버 웹 서버</span><span class="sxs-lookup"><span data-stu-id="235b0-217">Report Server Web Server</span></span>||
|<span data-ttu-id="235b0-218">서비스 애플리케이션 프록시</span><span class="sxs-lookup"><span data-stu-id="235b0-218">Service Application Proxy</span></span>||
|<span data-ttu-id="235b0-219">공유 서비스</span><span class="sxs-lookup"><span data-stu-id="235b0-219">Shared Service</span></span>|<span data-ttu-id="235b0-220">샘플 항목:</span><span class="sxs-lookup"><span data-stu-id="235b0-220">Sample entries:</span></span><br /><br /> <span data-ttu-id="235b0-221">MediumUpdating ReportingWebServiceApplication</span><span class="sxs-lookup"><span data-stu-id="235b0-221">MediumUpdating ReportingWebServiceApplication</span></span><br /><br /> <span data-ttu-id="235b0-222">콘텐츠 데이터베이스에 대한 MediumGranting 액세스입니다.</span><span class="sxs-lookup"><span data-stu-id="235b0-222">MediumGranting access to content databases.</span></span><br /><br /> <span data-ttu-id="235b0-223">ReportingWebServiceApplication의 MediumProvisioning 인스턴스</span><span class="sxs-lookup"><span data-stu-id="235b0-223">MediumProvisioning instances for ReportingWebServiceApplication</span></span><br /><br /> <span data-ttu-id="235b0-224">ReportingWebServiceApplication에 대한 MediumProcessing 서비스 계정 변경 내용</span><span class="sxs-lookup"><span data-stu-id="235b0-224">MediumProcessing service account change for ReportingWebServiceApplication</span></span><br /><br /> <span data-ttu-id="235b0-225">MediumSetting 데이터베이스 사용 권한입니다.</span><span class="sxs-lookup"><span data-stu-id="235b0-225">MediumSetting database permissions.</span></span>|

##  <a name="view-a-log-file-with-powershell"></a><a name="bkmk_powershell"></a> <span data-ttu-id="235b0-226">PowerShell에서 로그 파일 보기</span><span class="sxs-lookup"><span data-stu-id="235b0-226">View a Log file with PowerShell</span></span>
 <span data-ttu-id="235b0-227">![PowerShell 관련 콘텐츠](../media/rs-powershellicon.jpg "PowerShell 관련 콘텐츠")PowerShell을 사용하여 ULS 로그 파일에서 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 관련 이벤트 목록을 반환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="235b0-227">![PowerShell related content](../media/rs-powershellicon.jpg "PowerShell related content")You can use PowerShell to return a list of the [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] related events from a ULS Log file.</span></span> <span data-ttu-id="235b0-228">ULS 로그 파일 UESQL11SPOINT-20110606-1530.log 파일에서 "**sql server reporting services**"가 포함된 필터링된 행 목록을 반환하려면 SharePoint 2010 관리 셸에서 다음 명령을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="235b0-228">Type the following command from the SharePoint 2010 Management Shell to return a filtered list of rows from the file a ULS log file UESQL11SPOINT-20110606-1530.log, that contain "**sql server reporting services**":</span></span>

```powershell
Get-Content -Path "C:\Program Files\Common Files\Microsoft Shared\Web Server Extensions\14\LOGS\UESQL11SPOINT-20110606-1530.log" | Select-String "sql server reporting services"
```

 <span data-ttu-id="235b0-229">ULS 로그를 읽는 데 사용할 수 있는 다운로드 가능한 많은 도구가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="235b0-229">There are also many tools you can download which will allow you read ULS logs.</span></span> <span data-ttu-id="235b0-230">예를 들어 [SharePoint LogViewer](https://sharepointlogviewer.codeplex.com/) 또는 [SharePoint ULS 로그 뷰어](http://ulsviewer.codeplex.com/workitem/list/basic)를 다운로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="235b0-230">For example, the [SharePoint LogViewer](https://sharepointlogviewer.codeplex.com/) or [SharePoint ULS Log Viewer](http://ulsviewer.codeplex.com/workitem/list/basic).</span></span> <span data-ttu-id="235b0-231">이 두 도구는 Codeplex에서 다운로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="235b0-231">Both are available on CodePlex.</span></span>

 <span data-ttu-id="235b0-232">PowerShell을 사용하여 로그 데이터를 보는 방법에 대한 자세한 내용은 [진단 로그 보기(SharePoint Server 2010)](https://technet.microsoft.com/library/ff463595.aspx)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="235b0-232">For more information on how to use PowerShell to view log data, see [View diagnostic logs (SharePoint Server 2010)](https://technet.microsoft.com/library/ff463595.aspx)</span></span>

##  <a name="trace-log-location"></a><a name="bkmk_trace"></a><span data-ttu-id="235b0-233">추적 로그 위치</span><span class="sxs-lookup"><span data-stu-id="235b0-233">Trace Log Location</span></span>
 <span data-ttu-id="235b0-234">추적 로그 파일은 일반적으로 **c:\Program Files\Common files\Microsoft Shared\Web Server Extensions\14\logs** 폴더에 있지만 SharePoint 중앙 관리의 **진단 로깅** 페이지에서 경로를 확인하거나 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="235b0-234">The Trace Log files are usually found in the folder **c:\Program Files\Common files\Microsoft Shared\Web Server Extensions\14\logs** but you can verify or change the path from the **Diagnostic Logging** page in SharePoint Central Administration.</span></span>

