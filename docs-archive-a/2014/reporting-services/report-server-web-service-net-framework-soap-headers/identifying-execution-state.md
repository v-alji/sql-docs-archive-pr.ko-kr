---
title: 실행 상태 식별 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- session states [Reporting Services]
- lifetimes [Reporting Services]
- sessions [Reporting Services]
- SessionHeader SOAP header
ms.assetid: d8143a4b-08a1-4c38-9d00-8e50818ee380
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: fe53254a5da39c4e7d003ba37d5812ad130293e9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659803"
---
# <a name="identifying-execution-state"></a><span data-ttu-id="0fddc-102">실행 상태 식별</span><span class="sxs-lookup"><span data-stu-id="0fddc-102">Identifying Execution State</span></span>
  <span data-ttu-id="0fddc-103">HTTP(Hypertext Transfer Protocol)는 연결 없는 상태 비저장 프로토콜이므로 다양한 요청이 동일한 클라이언트에서 나온 것인지 여부 또는 단일 브라우저 인스턴스에서 페이지나 사이트를 계속 사용 중인지 여부를 자동으로 나타내지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0fddc-103">Hypertext Transfer Protocol (HTTP) is a connectionless and stateless protocol, which means that it does not automatically indicate whether different requests come from the same client or even whether a single browser instance is still actively viewing a page or site.</span></span> <span data-ttu-id="0fddc-104">다수의 세션에서 논리적 연결이 만들어져 서버와 클라이언트 간의 상태가 HTTP를 통해 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="0fddc-104">Sessions create a logical connection to maintain state between server and client over HTTP.</span></span> <span data-ttu-id="0fddc-105">특정 세션과 관련된 사용자별 정보를 세션 상태라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="0fddc-105">The user-specific information relevant to a particular session is known as the session state.</span></span>

 <span data-ttu-id="0fddc-106">세션 관리에는 HTTP 요청과 동일 세션에서 생성된 다른 이전 요청과의 상관 관계를 지정하는 작업이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="0fddc-106">Session management involves correlating an HTTP request with other previous requests generated from the same session.</span></span> <span data-ttu-id="0fddc-107">세션 관리가 없으면 HTTP 프로토콜의 연결 없는 상태 비저장 특성으로 인해 이러한 요청은 보고서 서버 웹 서비스와 관련이 없는 것으로 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="0fddc-107">Without session management, these requests appear unrelated to the Report Server Web service because of the connectionless and stateless nature of the HTTP protocol.</span></span>

 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]<span data-ttu-id="0fddc-108">는 [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)]에서 표시하는 것과 같이 세션 상태의 전체적 개념을 표시하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0fddc-108">does not expose a holistic concept of session state such as that exposed by [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)].</span></span> <span data-ttu-id="0fddc-109">하지만 보고서를 실행할 때 보고서 서버에서는 **실행**의 형태로 메서드 호출 간의 상태를 유지 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="0fddc-109">However, when executing reports, the report server maintains state between method calls in the form of an **execution**.</span></span> <span data-ttu-id="0fddc-110">실행을 통해 사용자는 보고서 서버에서 보고서 로드, 보고서에 대한 자격 증명 및 매개 변수 설정, 보고서 렌더링 등을 포함하여 보고서에 여러 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0fddc-110">An execution allows the user to interact with the report in several ways - including loading the report from the report server, setting credentials and parameters for the report, and rendering the report.</span></span>

 <span data-ttu-id="0fddc-111">보고서 서버와 통신하는 동안 클라이언트에서는 실행을 사용하여 보고서 보기, 보고서의 다른 페이지로 사용자 이동 등을 관리하며 보고서의 섹션을 표시하거나 숨깁니다.</span><span class="sxs-lookup"><span data-stu-id="0fddc-111">While they are communicating to a report server, clients use the execution to manage report viewing and user navigation to other pages in a report, and to show or hide sections of a report.</span></span> <span data-ttu-id="0fddc-112">클라이언트 애플리케이션에서 실행 중인 각 보고서별로 고유한 실행이 존재합니다.</span><span class="sxs-lookup"><span data-stu-id="0fddc-112">A unique execution exists for each report the client application is running.</span></span>

 <span data-ttu-id="0fddc-113">일반적으로 실행의 수명은 사용자가 브라우저나 클라이언트 애플리케이션으로 이동하여 보려는 보고서를 선택할 때 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="0fddc-113">In general, the lifetime of an execution starts when a user navigates to a browser or client application and selects a report to view.</span></span> <span data-ttu-id="0fddc-114">마지막 실행 요청이 수신된 후 짧은 제한 시간이 지나면 실행은 폐기됩니다(기본 제한 시간은 20분).</span><span class="sxs-lookup"><span data-stu-id="0fddc-114">The execution is discarded after a short time out period after the last request to the execution has been received (the default time out is 20 minutes).</span></span>

 <span data-ttu-id="0fddc-115">웹 서비스 측면에서 수명은 보고서 서버 웹 서비스 <xref:ReportExecution2005.ReportExecutionService.LoadReport%2A>, <xref:ReportExecution2005.ReportExecutionService.LoadReportDefinition%2A> 또는 <xref:ReportExecution2005.ReportExecutionService.Render%2A> 메서드가 호출될 때 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="0fddc-115">From a Web service perspective, the lifetime starts when the Report Server Web service <xref:ReportExecution2005.ReportExecutionService.LoadReport%2A>, <xref:ReportExecution2005.ReportExecutionService.LoadReportDefinition%2A>, or <xref:ReportExecution2005.ReportExecutionService.Render%2A> methods are called.</span></span> <span data-ttu-id="0fddc-116">애플리케이션에서는 다른 메서드를 사용하여 활성 실행을 조작할 수 있습니다(예: 매개 변수 설정 및 데이터 원본 설정).</span><span class="sxs-lookup"><span data-stu-id="0fddc-116">The application can use other methods to manipulate the active execution (for example, setting parameters and setting data sources).</span></span> <span data-ttu-id="0fddc-117">마지막 실행 요청이 수신된 후 짧은 제한 시간이 지나면 실행은 폐기됩니다(기본 제한 시간은 20분).</span><span class="sxs-lookup"><span data-stu-id="0fddc-117">The execution is discarded after a short time out period after the last request to the execution has been received (the default time out is 20 minutes).</span></span>

 <span data-ttu-id="0fddc-118">애플리케이션에서는 <xref:ReportExecution2005.ReportExecutionService.Render%2A> 및 <xref:ReportExecution2005.ReportExecutionService.RenderStream%2A> 메서드에서 SOAP 헤더로 반환되는 <xref:ReportExecution2005.ExecutionHeader.ExecutionID%2A>를 저장하여 웹 서비스 <xref:ReportExecution2005.ReportExecutionService.LoadReport%2A> 및 <xref:ReportExecution2005.ReportExecutionService.LoadReportDefinition%2A> 메서드 호출 간의 여러 활성 실행을 추적합니다.</span><span class="sxs-lookup"><span data-stu-id="0fddc-118">An application keep track of multiple active executions between calls to the Web service <xref:ReportExecution2005.ReportExecutionService.Render%2A> and <xref:ReportExecution2005.ReportExecutionService.RenderStream%2A> methods by saving the <xref:ReportExecution2005.ExecutionHeader.ExecutionID%2A>, which is returned in the SOAP header from the <xref:ReportExecution2005.ReportExecutionService.LoadReport%2A> and <xref:ReportExecution2005.ReportExecutionService.LoadReportDefinition%2A> methods.</span></span>

 <span data-ttu-id="0fddc-119">다음 다이어그램은 보고서에 대한 처리 및 렌더링 경로를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="0fddc-119">The following diagram shows the processing and rendering path for reports.</span></span>

 <span data-ttu-id="0fddc-120">![보고서 처리/렌더링 경로](../../../2014/reporting-services/media/rs-render-process-diagram.gif "보고서 처리/렌더링 경로")</span><span class="sxs-lookup"><span data-stu-id="0fddc-120">![Report processing/rendering path](../../../2014/reporting-services/media/rs-render-process-diagram.gif "Report processing/rendering path")</span></span>

 <span data-ttu-id="0fddc-121">위에 나타난 함수를 지원하기 위해 현재 SOAP Render 메서드는 실행 초기화, 처리 및 렌더링 단계를 포함한 여러 메서드로 분할되었습니다.</span><span class="sxs-lookup"><span data-stu-id="0fddc-121">To support the functions described above, the current SOAP Render method has been split into multiple methods encompassing execution initialization, processing, and rendering phases.</span></span>

 <span data-ttu-id="0fddc-122">보고서를 프로그래밍 방식으로 렌더링하려면 다음 작업을 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0fddc-122">To programmatically render a report, you must:</span></span>

-   <span data-ttu-id="0fddc-123"><xref:ReportExecution2005.ReportExecutionService.LoadReport%2A> 또는 <xref:ReportExecution2005.ReportExecutionService.LoadReportDefinition%2A>을 사용하여 보고서 또는 보고서 정의를 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="0fddc-123">Load the report or the report definition using <xref:ReportExecution2005.ReportExecutionService.LoadReport%2A> or <xref:ReportExecution2005.ReportExecutionService.LoadReportDefinition%2A>.</span></span>

-   <span data-ttu-id="0fddc-124"><xref:ReportExecution2005.ExecutionInfo.CredentialsRequired%2A> 또는 <xref:ReportExecution2005.ExecutionInfo.ParametersRequired%2A>에 의해 반환된 <xref:ReportExecution2005.ExecutionInfo> 개체의 <xref:ReportExecution2005.ReportExecutionService.LoadReport%2A> 및 <xref:ReportExecution2005.ReportExecutionService.LoadReportDefinition%2A> 속성 값을 검토하여 보고서에 자격 증명 또는 매개 변수가 필요한지 여부를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="0fddc-124">Check to see if the report needs credentials or parameters by checking the values of the <xref:ReportExecution2005.ExecutionInfo.CredentialsRequired%2A> and <xref:ReportExecution2005.ExecutionInfo.ParametersRequired%2A> properties of the <xref:ReportExecution2005.ExecutionInfo> object returned by <xref:ReportExecution2005.ReportExecutionService.LoadReport%2A> or <xref:ReportExecution2005.ReportExecutionService.LoadReportDefinition%2A></span></span>

-   <span data-ttu-id="0fddc-125">필요한 경우 <xref:ReportExecution2005.ReportExecutionService.SetExecutionCredentials%2A> 및 <xref:ReportExecution2005.ReportExecutionService.SetExecutionParameters%2A> 메서드를 사용하여 자격 증명 및/또는 매개 변수를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="0fddc-125">If necessary, set the credentials and/or parameters using the <xref:ReportExecution2005.ReportExecutionService.SetExecutionCredentials%2A> and <xref:ReportExecution2005.ReportExecutionService.SetExecutionParameters%2A> methods.</span></span>

-   <span data-ttu-id="0fddc-126"><xref:ReportExecution2005.ReportExecutionService.Render%2A> 메서드를 호출하여 보고서를 렌더링합니다.</span><span class="sxs-lookup"><span data-stu-id="0fddc-126">Call the <xref:ReportExecution2005.ReportExecutionService.Render%2A> method to render the report.</span></span>

 <span data-ttu-id="0fddc-127">보고서가 세션에 있는 동안 보고서 서버 데이터베이스에 저장된 원본 보고서가 변경될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0fddc-127">While a report is in session, the underlying report stored in the report server database can change.</span></span> <span data-ttu-id="0fddc-128">예를 들어 보고서 정의가 변경되거나, 보고서가 삭제 또는 이동되거나, 사용자 권한이 바뀔 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0fddc-128">For example, the report definition can change, the report can be deleted or moved, and user permissions can change.</span></span> <span data-ttu-id="0fddc-129">보고서가 활성 세션에 있는 경우에는 원본 보고서, 즉 보고서 서버 데이터베이스에 저장된 보고서의 변경으로 인한 영향을 받지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0fddc-129">If the report is in an active session, it is not affected by changes made to the underlying report (that is, the report stored in the report server database).</span></span>

 <span data-ttu-id="0fddc-130">URL 액세스 명령을 사용하여 보고서 세션을 관리할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0fddc-130">You can also manage a report session using URL access commands.</span></span>

## <a name="see-also"></a><span data-ttu-id="0fddc-131">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0fddc-131">See Also</span></span>
 <span data-ttu-id="0fddc-132"><xref:ReportExecution2005.ReportExecutionService.Render%2A>[REPORTING SERVICES SOAP 헤더를 사용 하 여](../report-server-web-service-net-framework-soap-headers/using-reporting-services-soap-headers.md) [SSRS&#41;&#40;기술 참조](../../../2014/reporting-services/technical-reference-ssrs.md)</span><span class="sxs-lookup"><span data-stu-id="0fddc-132"><xref:ReportExecution2005.ReportExecutionService.Render%2A> [Technical Reference &#40;SSRS&#41;](../../../2014/reporting-services/technical-reference-ssrs.md) [Using Reporting Services SOAP Headers](../report-server-web-service-net-framework-soap-headers/using-reporting-services-soap-headers.md)</span></span>


