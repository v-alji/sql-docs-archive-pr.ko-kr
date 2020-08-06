---
title: URL 액세스(SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- URL access [Reporting Services]
- links [Reporting Services], URL access
- URL access [Reporting Services], about URL access
- parameters [Reporting Services], URL access
- report servers [Reporting Services], URL access
- hyperlinks [Reporting Services]
ms.assetid: 52c3f2a3-3d6d-4fee-9c46-83f366919398
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: bf44ea3c15c12f37eebf6e89faf4ff3affd64433
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649352"
---
# <a name="url-access-ssrs"></a><span data-ttu-id="3ae8f-102">URL 액세스(SSRS)</span><span class="sxs-lookup"><span data-stu-id="3ae8f-102">URL Access (SSRS)</span></span>
  <span data-ttu-id="3ae8f-103">SQL Server Reporting Services(SSRS)에서 보고서 서버의 URL 액세스를 사용하면 URL 요청을 통해 보고서 서버에 명령을 보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3ae8f-103">URL access of the report server in SQL Server Reporting Services (SSRS) enables you to send commands to a report server through a URL request.</span></span> <span data-ttu-id="3ae8f-104">예를 들어 기본 모드 보고서 서버 또는 SharePoint 라이브러리에서 보고서 렌더링을 사용자 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3ae8f-104">For example, you can customize the rendering of a report on a native mode report server or in a SharePoint library.</span></span> <span data-ttu-id="3ae8f-105">특정 보고서 매개 변수 값 집합을 사용하여 보고서를 보거나 보고서의 관심 있는 특정 페이지를 본 경우</span><span class="sxs-lookup"><span data-stu-id="3ae8f-105">You may have viewed the report using a specific set of report parameter values, or you may have been viewing a particular page of interest in the report.</span></span> <span data-ttu-id="3ae8f-106">미리 정의된 URL 액세스 매개 변수를 사용하여 이 정보를 URL에 캡슐화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3ae8f-106">You can encapsulate this information in the URL using predefined URL access parameters.</span></span> <span data-ttu-id="3ae8f-107">또한 렌더링 형식 및 보고서 뷰어의 디자인에 대한 매개 변수를 포함하여 보고서 서버에서 보고서를 처리하는 방식을 사용자 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3ae8f-107">You can further customize how the report server processes the report by embedding parameters for rendering formats or for the look and feel of the report viewer.</span></span> <span data-ttu-id="3ae8f-108">그런 다음 이 URL을 전자 메일이나 웹 페이지에 직접 붙여넣어 다른 사용자가 브라우저에서 같은 방식으로 보고서에 액세스하도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3ae8f-108">You can then paste this URL directly into an email or Web page to let others to access your report in the same manner in the browser.</span></span>  
  
 <span data-ttu-id="3ae8f-109">URL 액세스를 통해 수행할 수 있는 다음 동작의 예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="3ae8f-109">Other actions you can perform through URL access are:</span></span>  
  
-   <span data-ttu-id="3ae8f-110">HTML 뷰어에 명령(예: 디자인 조정) 보내기</span><span class="sxs-lookup"><span data-stu-id="3ae8f-110">Send commands to the HTML viewer, such as adjusting its look and feel</span></span>  
  
-   <span data-ttu-id="3ae8f-111">카탈로그 폴더의 자식 나열</span><span class="sxs-lookup"><span data-stu-id="3ae8f-111">List the children of a catalog folder</span></span>  
  
-   <span data-ttu-id="3ae8f-112">카탈로그 항목의 XML 정의 검색</span><span class="sxs-lookup"><span data-stu-id="3ae8f-112">Retrieve the XML definition of a catalog item</span></span>  
  
-   <span data-ttu-id="3ae8f-113">특정 보고서 기록 스냅샷 렌더링</span><span class="sxs-lookup"><span data-stu-id="3ae8f-113">Render a specific report history snapshot</span></span>  
  
-   <span data-ttu-id="3ae8f-114">보고서 세션 관리</span><span class="sxs-lookup"><span data-stu-id="3ae8f-114">Manage report sessions</span></span>  
  
 <span data-ttu-id="3ae8f-115">URL 액세스를 통해 사용할 수 있는 설정 및 명령의 전체 목록은 [URL 액세스 매개 변수 참조](url-access-parameter-reference.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3ae8f-115">For the complete list of commands and settings available through URL access, see [URL Access Parameter Reference](url-access-parameter-reference.md).</span></span>  
  
## <a name="url-access-concepts"></a><span data-ttu-id="3ae8f-116">URL 액세스 개념</span><span class="sxs-lookup"><span data-stu-id="3ae8f-116">URL Access Concepts</span></span>  
 <span data-ttu-id="3ae8f-117">보고서 서버에 대한 URL 요청에는 보고서 서버에서 처리하는 매개 변수가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="3ae8f-117">URL requests to the report server contain parameters that are processed by the report server.</span></span> <span data-ttu-id="3ae8f-118">보고서 서버에서 URL 요청을 처리하는 방법은 매개 변수, 매개 변수 접두사, URL에 포함된 항목의 종류 등에 따라 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="3ae8f-118">The way in which the report server handles URL requests depends on the parameters, parameter prefixes, and types of items that are included in the URL.</span></span> <span data-ttu-id="3ae8f-119">보고서 서버 URL은 W3C(World Wide Web 컨소시엄)와 IETF의 공동 초안 표준에서 제안한 대로 URL 형식 지정 지침을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="3ae8f-119">Report server URLs adhere to the URL formatting guidelines as proposed by the joint World Wide Web Consortium W3C/IETF draft standard.</span></span> [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] <span data-ttu-id="3ae8f-120">URL 기능은 표준 URL 주소 지정을 지원하는 대부분의 인터넷 브라우저나 애플리케이션에서 호환됩니다.</span><span class="sxs-lookup"><span data-stu-id="3ae8f-120">URL functionality is compatible with most Internet browsers or applications that support standard URL addressing.</span></span>  
  
### <a name="url-access-syntax"></a><span data-ttu-id="3ae8f-121">URL 액세스 구문</span><span class="sxs-lookup"><span data-stu-id="3ae8f-121">URL Access Syntax</span></span>  
 <span data-ttu-id="3ae8f-122">URL 요청에는 임의의 순서로 나열된 여러 매개 변수가 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3ae8f-122">URL requests can contain multiple parameters that are listed in any order.</span></span> <span data-ttu-id="3ae8f-123">매개 변수는 앰퍼샌드(&)로 구분되고 이름/값 쌍은 등호(=)로 구분됩니다.</span><span class="sxs-lookup"><span data-stu-id="3ae8f-123">Parameters are separated by an ampersand (&) and name/value pairs are separated by an equal sign (=).</span></span>  
  
```  
  
rswebserviceurl  
?  
reportpath  
      [&prefix:param=value]...n]  
  
```  
  
### <a name="syntax-description"></a><span data-ttu-id="3ae8f-124">구문 설명</span><span class="sxs-lookup"><span data-stu-id="3ae8f-124">Syntax Description</span></span>  
 <span data-ttu-id="3ae8f-125">*rswebserviceurl*</span><span class="sxs-lookup"><span data-stu-id="3ae8f-125">*rswebserviceurl*</span></span>  
 <span data-ttu-id="3ae8f-126">보고서 서버의 웹 서비스 URL입니다.</span><span class="sxs-lookup"><span data-stu-id="3ae8f-126">The Web service URL of the report server.</span></span> <span data-ttu-id="3ae8f-127">기본 모드의 경우 Reporting Services 구성 관리자에 구성된 보고서 서버 인스턴스의 웹 서비스 URL입니다([보고서 서버 URL 구성&#40;SSRS Configuration Manager&#41;](install-windows/configure-report-server-urls-ssrs-configuration-manager.md) 참조).</span><span class="sxs-lookup"><span data-stu-id="3ae8f-127">For native mode, it is the Web service URL of the report server instance configured in Reporting Services Configuration Manager (see [Configure Report Server URLs  &#40;SSRS Configuration Manager&#41;](install-windows/configure-report-server-urls-ssrs-configuration-manager.md)).</span></span> <span data-ttu-id="3ae8f-128">다음은 그 예입니다.</span><span class="sxs-lookup"><span data-stu-id="3ae8f-128">For example:</span></span>  
  
```  
http://myrshost/reportserver  
https://machine.adventure-works.com/reportserver_MYNAMEDINSTANCE  
```  
  
 <span data-ttu-id="3ae8f-129">SharePoint 통합 모드의 경우 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 와 통합된 SharePoint 사이트의 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]프록시 URL입니다.</span><span class="sxs-lookup"><span data-stu-id="3ae8f-129">For SharePoint integrated mode, it is the URL of the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] proxy at a SharePoint site integrated with [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="3ae8f-130">다음은 그 예입니다.</span><span class="sxs-lookup"><span data-stu-id="3ae8f-130">For example:</span></span>  
  
```  
http://myspsite/subsite/_vti_bin/reportserver  
```  
  
> [!TIP]  
>  <span data-ttu-id="3ae8f-131">URL에는 SharePoint를 통해 요청을 라우팅하는 `_vti_bin` 프록시 구문과 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] HTTP 프록시를 포함하는 것이 중요합니다.</span><span class="sxs-lookup"><span data-stu-id="3ae8f-131">It is important the URL include the `_vti_bin` proxy syntax to route the request through SharePoint and the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] HTTP proxy.</span></span> <span data-ttu-id="3ae8f-132">프록시는 몇 가지 컨텍스트를 HTTP 요청에 추가하며 이 컨텍스트는 SharePoint 모드 보고서 서버에 대한 보고서의 올바른 실행을 보장하는 데 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="3ae8f-132">The proxy adds some context to the HTTP request, context that is required to ensure proper execution of the report for SharePoint mode report servers.</span></span>  
  
 <span data-ttu-id="3ae8f-133">*pathinfo*</span><span class="sxs-lookup"><span data-stu-id="3ae8f-133">*pathinfo*</span></span>  
 <span data-ttu-id="3ae8f-134">기본 모드 보고서 서버 데이터베이스 항목의 상대 경로 이름 또는 SharePoint 카탈로그 항목의 정규화된 URL입니다.</span><span class="sxs-lookup"><span data-stu-id="3ae8f-134">The relative path name of the item in the native mode report server database, or the fully qualified URL of the item in a SharePoint catalog.</span></span>  
  
 <span data-ttu-id="3ae8f-135">카탈로그 항목의 경로입니다.</span><span class="sxs-lookup"><span data-stu-id="3ae8f-135">The path of the catalog item.</span></span> <span data-ttu-id="3ae8f-136">기본 모드의 경우 보고서 서버 데이터베이스 항목의 상대 경로(슬래시(`/`로 시작)입니다.</span><span class="sxs-lookup"><span data-stu-id="3ae8f-136">For native mode, it is the relative path of the item in the report server database, beginning with a slash (`/`).</span></span> <span data-ttu-id="3ae8f-137">다음은 그 예입니다.</span><span class="sxs-lookup"><span data-stu-id="3ae8f-137">For example:</span></span>  
  
```  
/AdventureWorks 2008R2/Employee_Sales_Summary_2008R2  
```  
  
 <span data-ttu-id="3ae8f-138">SharePoint 통합 모드의 경우 SharePoint 라이브러리 항목의 정규화된 URL(항목 확장명 포함)입니다.</span><span class="sxs-lookup"><span data-stu-id="3ae8f-138">For SharePoint integrated mode, it is the fully qualified URL of the item in the SharePoint library, including the item extension.</span></span> <span data-ttu-id="3ae8f-139">다음은 그 예입니다.</span><span class="sxs-lookup"><span data-stu-id="3ae8f-139">For example:</span></span>  
  
```  
http://myspsite/subsite/AdventureWorks 2008R2/Employee_Sales_Summary_2008R2.rdl  
```  
  
 `&`  
 <span data-ttu-id="3ae8f-140">URL 액세스 매개 변수의 이름/값 쌍을 구분하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="3ae8f-140">Used to separate name and value pairs of URL access parameters.</span></span>  
  
 <span data-ttu-id="3ae8f-141">**prefix**</span><span class="sxs-lookup"><span data-stu-id="3ae8f-141">**prefix**</span></span>  
 <span data-ttu-id="3ae8f-142">(선택 사항)</span><span class="sxs-lookup"><span data-stu-id="3ae8f-142">Optional.</span></span> <span data-ttu-id="3ae8f-143">보고서 서버 내에서 실행 중인 특정 프로세스에 액세스하는 URL 액세스 매개 변수의 접두사(예: `rs:` 또는 `rc:`)입니다.</span><span class="sxs-lookup"><span data-stu-id="3ae8f-143">A prefix for the URL access parameter (for example, `rs:` or `rc:`) that accesses a specific process running within the report server.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3ae8f-144">URL 액세스 매개 변수의 접두사가 포함되지 않은 경우 매개 변수는 보고서 서버에서 보고서 매개 변수로 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="3ae8f-144">If a prefix for a URL access parameter is not included, the parameter is processed by the report server as a report parameter.</span></span> <span data-ttu-id="3ae8f-145">보고서 매개 변수는 매개 변수 접두사를 사용하지 않으며 대/소문자를 구분합니다.</span><span class="sxs-lookup"><span data-stu-id="3ae8f-145">Report parameters do not use a parameter prefix and are case-sensitive.</span></span>  
  
 <span data-ttu-id="3ae8f-146">**param**</span><span class="sxs-lookup"><span data-stu-id="3ae8f-146">**param**</span></span>  
 <span data-ttu-id="3ae8f-147">매개 변수 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="3ae8f-147">The parameter name.</span></span>  
  
 <span data-ttu-id="3ae8f-148">*value*</span><span class="sxs-lookup"><span data-stu-id="3ae8f-148">*value*</span></span>  
 <span data-ttu-id="3ae8f-149">사용 중인 매개 변수의 값에 해당하는 URL 텍스트입니다.</span><span class="sxs-lookup"><span data-stu-id="3ae8f-149">URL text corresponding to the value of the parameter being used.</span></span>  
  
 <span data-ttu-id="3ae8f-150">**참고:** 사용 가능한 URL 액세스 매개 변수의 목록은 [URL Access Parameter Reference](url-access-parameter-reference.md)을(를) 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="3ae8f-150">**Note:** For a list of the available URL access parameters, see [URL Access Parameter Reference](url-access-parameter-reference.md).</span></span> <span data-ttu-id="3ae8f-151">URL에 보고서 매개 변수를 전달하는 예제는 [Pass a Report Parameter Within a URL](pass-a-report-parameter-within-a-url.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="3ae8f-151">For examples passing report parameters on the URL, see [Pass a Report Parameter Within a URL](pass-a-report-parameter-within-a-url.md).</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="3ae8f-152">관련 작업</span><span class="sxs-lookup"><span data-stu-id="3ae8f-152">Related Tasks</span></span>  
  
|<span data-ttu-id="3ae8f-153">태스크 설명</span><span class="sxs-lookup"><span data-stu-id="3ae8f-153">Task Descriptions</span></span>|<span data-ttu-id="3ae8f-154">링크</span><span class="sxs-lookup"><span data-stu-id="3ae8f-154">Links</span></span>|  
|-----------------------|-----------|  
|<span data-ttu-id="3ae8f-155">보고서, 공유 데이터 원본 및 리소스와 같은 보고서 서버 항목 액세스</span><span class="sxs-lookup"><span data-stu-id="3ae8f-155">Access report server items, such as reports, shared data sources, and resources.</span></span>|[<span data-ttu-id="3ae8f-156">URL 액세스를 사용하여 보고서 서버 항목 액세스</span><span class="sxs-lookup"><span data-stu-id="3ae8f-156">Access Report Server Items Using URL Access</span></span>](access-report-server-items-using-url-access.md)|  
|<span data-ttu-id="3ae8f-157">보고서 매개 변수를 보고서로 전달</span><span class="sxs-lookup"><span data-stu-id="3ae8f-157">Pass report parameters to a report.</span></span>|[<span data-ttu-id="3ae8f-158">URL에 보고서 매개 변수 전달</span><span class="sxs-lookup"><span data-stu-id="3ae8f-158">Pass a Report Parameter Within a URL</span></span>](pass-a-report-parameter-within-a-url.md)|  
|<span data-ttu-id="3ae8f-159">URL 액세스 문자열에서 날짜, 통화 등의 로캘별 해석을 정의하는 보고서 매개 변수의 로캘 설정</span><span class="sxs-lookup"><span data-stu-id="3ae8f-159">Set the locale of the report parameters in the URL access string, which defines the locale-specific interpretations of dates, currencies, and so on.</span></span>|[<span data-ttu-id="3ae8f-160">URL에 보고서 매개 변수 언어 설정</span><span class="sxs-lookup"><span data-stu-id="3ae8f-160">Set the Language for Report Parameters in a URL</span></span>](set-the-language-for-report-parameters-in-a-url.md)|  
|<span data-ttu-id="3ae8f-161">보고서 렌더링 방식을 사용자 지정하는 렌더링 확장자별 설정 보내기</span><span class="sxs-lookup"><span data-stu-id="3ae8f-161">Send rendering extension specific settings that customize how the report is rendered.</span></span>|[<span data-ttu-id="3ae8f-162">URL에 디바이스 정보 설정 지정</span><span class="sxs-lookup"><span data-stu-id="3ae8f-162">Specify Device Information Settings in a URL</span></span>](specify-device-information-settings-in-a-url.md)|  
|<span data-ttu-id="3ae8f-163">보고서를 브라우저에서 보지 않고 파일 형식으로 직접 내보내기</span><span class="sxs-lookup"><span data-stu-id="3ae8f-163">Export a report directly to a file format without viewing it in the browser.</span></span>|[<span data-ttu-id="3ae8f-164">URL 액세스를 사용하여 보고서 내보내기</span><span class="sxs-lookup"><span data-stu-id="3ae8f-164">Export a Report Using URL Access</span></span>](export-a-report-using-url-access.md)|  
|<span data-ttu-id="3ae8f-165">보고서를 열고 문자열 위치로 직접 이동</span><span class="sxs-lookup"><span data-stu-id="3ae8f-165">Open a report and navigate directly to the location of a string.</span></span>|[<span data-ttu-id="3ae8f-166">URL 액세스를 사용하여 보고서 검색</span><span class="sxs-lookup"><span data-stu-id="3ae8f-166">Search a Report Using URL Access</span></span>](search-a-report-using-url-access.md)|  
|<span data-ttu-id="3ae8f-167">특정 보고서 기록 스냅샷 렌더링</span><span class="sxs-lookup"><span data-stu-id="3ae8f-167">Render a specific report history snapshot.</span></span>|[<span data-ttu-id="3ae8f-168">URL 액세스를 사용하여 보고서 기록 스냅샷 렌더링</span><span class="sxs-lookup"><span data-stu-id="3ae8f-168">Render a Report History Snapshot Using URL Access</span></span>](render-a-report-history-snapshot-using-url-access.md)|  
  
## <a name="see-also"></a><span data-ttu-id="3ae8f-169">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3ae8f-169">See Also</span></span>  
 <span data-ttu-id="3ae8f-170">[Pass a Report Parameter Within a URL](pass-a-report-parameter-within-a-url.md) </span><span class="sxs-lookup"><span data-stu-id="3ae8f-170">[Pass a Report Parameter Within a URL](pass-a-report-parameter-within-a-url.md) </span></span>  
 <span data-ttu-id="3ae8f-171">[URL 액세스 매개 변수 참조](url-access-parameter-reference.md) </span><span class="sxs-lookup"><span data-stu-id="3ae8f-171">[URL Access Parameter Reference](url-access-parameter-reference.md) </span></span>  
 <span data-ttu-id="3ae8f-172">[URL 액세스를 사용하여 Reporting Services 통합](application-integration/integrating-reporting-services-using-url-access.md) </span><span class="sxs-lookup"><span data-stu-id="3ae8f-172">[Integrating Reporting Services Using URL Access](application-integration/integrating-reporting-services-using-url-access.md) </span></span>  
 [<span data-ttu-id="3ae8f-173">보고서 찾기, 보기 및 관리&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="3ae8f-173">Finding, Viewing, and Managing Reports &#40;Report Builder and SSRS &#41;</span></span>](report-builder/finding-viewing-and-managing-reports-report-builder-and-ssrs.md)  
  
  
