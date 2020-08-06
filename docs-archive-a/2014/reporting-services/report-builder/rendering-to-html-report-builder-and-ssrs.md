---
title: HTML로 렌더링(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 04/26/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: cf559b0a-499a-4d74-b520-b382b87e0b17
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 44f43d079aa81b566a39fe053bdf80c7800fc500
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648317"
---
# <a name="rendering-to-html-report-builder-and-ssrs"></a><span data-ttu-id="884df-102">HTML로 렌더링(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="884df-102">Rendering to HTML (Report Builder and SSRS)</span></span>
  <span data-ttu-id="884df-103">HTML 렌더링 확장 프로그램은 보고서를 HTML 형식으로 렌더링합니다.</span><span class="sxs-lookup"><span data-stu-id="884df-103">The HTML rendering extension renders a report in HTML format.</span></span> <span data-ttu-id="884df-104">완전한 형식의 HTML 페이지 또는 HTML 조각을 만들어 다른 HTML 페이지에 포함시킬 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="884df-104">The rendering extension can also produce fully formed HTML pages or fragments of HTML to embed in other HTML pages.</span></span> <span data-ttu-id="884df-105">모든 HTML은 UTF-8 인코딩을 사용하여 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="884df-105">All HTML is generated with UTF-8 encoding.</span></span>  
  
 <span data-ttu-id="884df-106">HTML 렌더링 확장 프로그램은 보고서 관리자에서 실행될 때를 포함하여 브라우저에 표시되는 보고서의 기본 렌더링 확장 프로그램입니다.</span><span class="sxs-lookup"><span data-stu-id="884df-106">The HTML rendering extension is the default rendering extension for reports that are viewed in a browser, including when run in Report Manager.</span></span>  
  
 <span data-ttu-id="884df-107">HTML 렌더링 확장 프로그램은 보고서 관리자에서 실행될 때를 포함하여 브라우저에 표시되는 보고서의 기본 렌더링 확장 프로그램입니다.</span><span class="sxs-lookup"><span data-stu-id="884df-107">The HTML rendering extension is the default rendering extension for reports that are viewed in a browser, including when run in Report Manager.</span></span> <span data-ttu-id="884df-108">HTML 렌더링 확장 프로그램은 HTML을 조각 또는 전체 HTML 문서로 렌더링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="884df-108">The HTML rendering extension can render HTML as a fragment or as a full HTML document.</span></span> <span data-ttu-id="884df-109">HTML이 조각인 경우 HTML 문서의 `HEAD`, `HTML` 및 `BODY` 태그는 제거되고</span><span class="sxs-lookup"><span data-stu-id="884df-109">If the HTML is a fragment, the `HEAD`, `HTML`, and `BODY` tags of the HTML document are removed.</span></span> <span data-ttu-id="884df-110">`BODY` 태그의 내용만 렌더링됩니다.</span><span class="sxs-lookup"><span data-stu-id="884df-110">Only the contents of the `BODY` tag are rendered.</span></span> <span data-ttu-id="884df-111">이 기능은 다른 애플리케이션에서 만든 HTML에 HTML을 포함하는 경우에 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="884df-111">This is useful for embedding the HTML in the HTML produced by another application.</span></span>  
  
 <span data-ttu-id="884df-112">일부 시나리오에서는 보고서를 HTML로 렌더링할 때 보고서 매개 변수를 사용하여 스크립트 삽입 공격을 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="884df-112">In some scenarios, report parameters can be used to launch script injection attacks when rendering reports to HTML.</span></span> <span data-ttu-id="884df-113">보고서를 안전하게 보호하는 방법에 대한 자세한 내용은 [보고서 및 리소스 보안](../security/secure-reports-and-resources.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="884df-113">For more information about securing reports, see [Secure Reports and Resources](../security/secure-reports-and-resources.md).</span></span>  
  
 <span data-ttu-id="884df-114">브라우저에 대 한 자세한 내용은 [Reporting Services 계획 및 파워 뷰 브라우저 지원 &#40;Reporting Services 2014&#41;](../browser-support-for-reporting-services-and-power-view.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="884df-114">For more information about browsers, see [Planning for Reporting Services and Power View Browser Support &#40;Reporting Services 2014&#41;](../browser-support-for-reporting-services-and-power-view.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
##  <a name="rendering-in-mhtml"></a><a name="RenderingMHTML"></a> <span data-ttu-id="884df-115">MHTML로 렌더링</span><span class="sxs-lookup"><span data-stu-id="884df-115">Rendering in MHTML</span></span>  
 <span data-ttu-id="884df-116">HTML 렌더링 확장 프로그램은 보고서를 MHTML(MIME Encapsulation of Aggregate HTML Documents)로도 렌더링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="884df-116">The HTML rendering extension can also render reports in MHTML (MIME Encapsulation of Aggregate HTML Documents).</span></span> <span data-ttu-id="884df-117">MHTML은 HTML을 확장하여 이미지와 같이 인코딩된 개체를 HTML에 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="884df-117">MHTML extends HTML to embed encoded objects, such as images, in the HTML document.</span></span> <span data-ttu-id="884df-118">MHTML 렌더링 확장 프로그램을 사용하여 이미지, 문서 또는 다른 이진 파일과 같은 리소스를 보고서 HTML 내의 MIME 구조로 단일 파일에 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="884df-118">Using the MHTML rendering extension, you can embed resources such as images, documents, or other binary files as MIME structures within the report HTML, into a single file.</span></span> <span data-ttu-id="884df-119">MHTML 보고서에는 모든 리소스가 포함되어 있으므로 MHTML 보고서는 전자 메일 메시지 내에 포함하는 데에도 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="884df-119">MHTML reports are also useful for embedding within e-mail messages because all resources are included with the report.</span></span> <span data-ttu-id="884df-120">이 기능은 실제로는 MHTML을 렌더링하는 HTML 렌더링 확장 프로그램이지만, MHTML 렌더링 확장 프로그램이라고 부릅니다.</span><span class="sxs-lookup"><span data-stu-id="884df-120">Although it is actually the HTML rendering extension that renders MHTML, this functionality may also be referred to as the MHTML rendering extension.</span></span>  
  
##  <a name="browser-support"></a><a name="BrowserSupport"></a><span data-ttu-id="884df-121">브라우저 지원</span><span class="sxs-lookup"><span data-stu-id="884df-121">Browser Support</span></span>  
 <span data-ttu-id="884df-122">이 렌더링 확장 프로그램은 다음 브라우저 버전을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="884df-122">This rendering extension supports the following browser versions:</span></span>  
  
-   <span data-ttu-id="884df-123">Internet Explorer 5.5 이상</span><span class="sxs-lookup"><span data-stu-id="884df-123">Internet Explorer 5.5 and later</span></span>  
  
-   <span data-ttu-id="884df-124">Firefox 1.5 이상</span><span class="sxs-lookup"><span data-stu-id="884df-124">Firefox 1.5 and later</span></span>  
  
-   <span data-ttu-id="884df-125">Safari 3.0 이상</span><span class="sxs-lookup"><span data-stu-id="884df-125">Safari 3.0 and later</span></span>  
  
 <span data-ttu-id="884df-126">브라우저 간 고려 사항으로 인해 렌더링된 보고서는 브라우저마다 조금씩 다를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="884df-126">Due to cross browser considerations, the rendered report may vary slightly from browser to browser.</span></span> <span data-ttu-id="884df-127">예를 들어 입력란에는 WritingMode라는 속성이 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="884df-127">For example, the text box contains a property called WritingMode.</span></span> <span data-ttu-id="884df-128">이 속성은 Firefox에서 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="884df-128">This property is not supported in Firefox.</span></span>  
  
##  <a name="html-specific-rendering-rules"></a><a name="HTMLSpecificRenderingRules"></a><span data-ttu-id="884df-129">HTML 관련 렌더링 규칙</span><span class="sxs-lookup"><span data-stu-id="884df-129">HTML-Specific Rendering Rules</span></span>  
 <span data-ttu-id="884df-130">렌더링할 때에는 다음과 같은 HTML 관련 규칙이 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="884df-130">The following HTML-specific rules are applied when rendering:</span></span>  
  
-   <span data-ttu-id="884df-131">렌더러는 항목이 여러 개인 경우 각 `ReportItems` 컬렉션의 모든 항목을 포함하기 위한 HTML 테이블 구조를 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="884df-131">The renderer builds an HTML table structure to contain all of the items in each `ReportItems` collection, if there is more than one.</span></span>  
  
-   <span data-ttu-id="884df-132">테이블 구조 내부의 모든 항목은 각각 단일 셀을 차지합니다.</span><span class="sxs-lookup"><span data-stu-id="884df-132">Every item within the table structure occupies a single cell.</span></span>  
  
-   <span data-ttu-id="884df-133">빈 셀은 HTML 크기를 줄이기 위해 가능한 한 축소됩니다.</span><span class="sxs-lookup"><span data-stu-id="884df-133">Empty cells are collapsed together as much as possible to reduce the size of the HTML.</span></span>  
  
-   <span data-ttu-id="884df-134">브라우저가 테이블을 렌더링하는 속도가 향상되도록 빈 셀로 구성된 행은 위쪽 가장자리에 추가되고 다른 열은 왼쪽 가장자리에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="884df-134">A row of empty cells is added to the top edge and another column to the left edge to improve the speed at which browsers can render the table.</span></span>  
  
-   <span data-ttu-id="884df-135">항목이 들어있지 않으므로 항목 간 간격에 불과한 테이블의 행 또는 열에는 고정 너비 및 높이가 부여됩니다.</span><span class="sxs-lookup"><span data-stu-id="884df-135">Table rows or columns that contain no items, just gaps between items, are given fixed widths and heights.</span></span>  
  
-   <span data-ttu-id="884df-136">다른 모든 행 및 열은 각 보고서 항목의 크기에 따라 커질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="884df-136">All other rows and columns are allowed to grow depending on the size of each report item.</span></span>  
  
-   <span data-ttu-id="884df-137">모든 좌표 및 보고서 항목 크기는 밀리미터로 변환됩니다.</span><span class="sxs-lookup"><span data-stu-id="884df-137">All coordinates and report item sizes are converted to millimeters.</span></span> <span data-ttu-id="884df-138">스타일 속성을 비롯한 다른 모든 크기에는 원래의 단위가 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="884df-138">All other sizes, including style properties, retain their original units.</span></span> <span data-ttu-id="884df-139">0.2mm보다 작은 크기 및 위치 차이는 0mm로 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="884df-139">Size and position differences smaller than .2mm are treated as 0mm.</span></span>  
  
##  <a name="interactivity"></a><a name="Interactivity"></a><span data-ttu-id="884df-140">대화형 작업</span><span class="sxs-lookup"><span data-stu-id="884df-140">Interactivity</span></span>  
 <span data-ttu-id="884df-141">HTML에서는 일부 대화형 요소가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="884df-141">Some interactive elements are supported in HTML.</span></span> <span data-ttu-id="884df-142">다음은 특정 동작에 대한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="884df-142">The following is a description of specific behaviors.</span></span>  
  
### <a name="show-and-hide"></a><span data-ttu-id="884df-143">표시 및 숨기기</span><span class="sxs-lookup"><span data-stu-id="884df-143">Show and Hide</span></span>  
 <span data-ttu-id="884df-144">표시 유형을 전환할 수 있는 보고서 항목은 +/- 토글 이미지와 함께 렌더링되며 클릭할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="884df-144">A report item whose visibility can be toggled is rendered with a +/- toggle image and is clickable.</span></span> <span data-ttu-id="884df-145">항목을 클릭하면 서버에 대한 콜백이 발생하여 변경된 표시/숨기기 상태로 출력이 다시 렌더링됩니다.</span><span class="sxs-lookup"><span data-stu-id="884df-145">When the item is clicked, a call back to the server takes place in order to re-render the output with the changed show or hide state.</span></span>  
  
### <a name="document-map"></a><span data-ttu-id="884df-146">문서 구조</span><span class="sxs-lookup"><span data-stu-id="884df-146">Document Map</span></span>  
 <span data-ttu-id="884df-147">문서 구조 레이블이 렌더링되고 뷰어 컨트롤에서 문서 구조를 사용하여 탐색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="884df-147">Document map labels are rendered and can be navigated to by using the document map in the viewer control.</span></span> <span data-ttu-id="884df-148">데이터 영역 머리글이 생략된 경우 레이블은 첫 번째 자식 셀에 렌더링됩니다.</span><span class="sxs-lookup"><span data-stu-id="884df-148">For omitted data region headers, labels are rendered on the first child cell.</span></span> <span data-ttu-id="884df-149">자식 셀이 없으면 레이블은 그 앞에 있는 자식에 렌더링됩니다.</span><span class="sxs-lookup"><span data-stu-id="884df-149">If there is no child cell present, the label is rendered on the child that precedes it.</span></span>  
  
### <a name="bookmarks"></a><span data-ttu-id="884df-150">책갈피</span><span class="sxs-lookup"><span data-stu-id="884df-150">Bookmarks</span></span>  
 <span data-ttu-id="884df-151">책갈피 링크는 렌더링되어 하이퍼링크로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="884df-151">Bookmark links are rendered and appear as hyperlinks.</span></span> <span data-ttu-id="884df-152">책갈피 대상이 렌더링되고 책갈피 링크를 클릭하여 탐색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="884df-152">Bookmark targets are rendered and can be navigated to by clicking the bookmark links.</span></span> <span data-ttu-id="884df-153">책갈피 링크를 클릭하면 제일 앞에 있는 대상 책갈피 레이블로 보고서가 이동하며 가능한 경우 해당 책갈피 링크가 창의 맨 위에 오도록 브라우저가 스크롤됩니다.</span><span class="sxs-lookup"><span data-stu-id="884df-153">When a bookmark link is clicked, the report goes to the first occurrence of the target bookmark label and, when possible, the browser is scrolled so that the bookmark link is at the top of the window.</span></span> <span data-ttu-id="884df-154">HTML 앵커 ( \<a> ) 태그는 책갈피 대상을 표시 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="884df-154">HTML anchor (\<a>) tags are used to mark bookmark targets.</span></span>  
  
### <a name="interactive-sorting"></a><span data-ttu-id="884df-155">대화형 정렬</span><span class="sxs-lookup"><span data-stu-id="884df-155">Interactive Sorting</span></span>  
 <span data-ttu-id="884df-156">입력란에 사용자 정렬이 정의되어 있으면 HTML 렌더링 확장 프로그램은 입력란의 정렬 아이콘을 입력란 내용의 오른쪽에 렌더링합니다.</span><span class="sxs-lookup"><span data-stu-id="884df-156">If a text box has user sort defined, the HTML rendering extension renders the sort icons in the text box to the right of its contents.</span></span> <span data-ttu-id="884df-157">보고서에 사용자 정렬이 정의된 입력란이 포함되어 있으면 정렬 이미지가 클릭될 때 서버로 포스트백을 보낼 JavaScript가 렌더링됩니다.</span><span class="sxs-lookup"><span data-stu-id="884df-157">If a report contains any text box where user sort is defined, JavaScript is rendered that causes a postback to the server when the sort image is clicked.</span></span>  
  
### <a name="hyperlinks-and-drillthrough"></a><span data-ttu-id="884df-158">하이퍼링크 및 드릴스루</span><span class="sxs-lookup"><span data-stu-id="884df-158">Hyperlinks and Drillthrough</span></span>  
 <span data-ttu-id="884df-159">하이퍼링크 및 드릴스루 링크는 정의 된 항목 주위에 HTML 앵커 () 태그를 사용 하 여 보고서 항목에 대 한 하이퍼링크로 렌더링 됩니다 \<a> .</span><span class="sxs-lookup"><span data-stu-id="884df-159">Hyperlinks and drillthrough links are rendered as hyperlinks on report items using the HTML anchor (\<a>) tags around the item on which they are defined.</span></span>  
  
### <a name="search"></a><span data-ttu-id="884df-160">검색</span><span class="sxs-lookup"><span data-stu-id="884df-160">Search</span></span>  
 <span data-ttu-id="884df-161">검색 기능을 통해 사용자는 보고서 내의 텍스트 문자열을 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="884df-161">The Search feature allows users to search for a string of text within the report.</span></span>  
  
 <span data-ttu-id="884df-162">ReportViewer Web Forms 컨트롤을 통해 추가 검색 및 찾기 기능이 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="884df-162">Additional search and find functionality is provided by the ReportViewer Web Forms control.</span></span>  
  
##  <a name="device-information-settings"></a><a name="DeviceInfo"></a><span data-ttu-id="884df-163">장치 정보 설정</span><span class="sxs-lookup"><span data-stu-id="884df-163">Device Information Settings</span></span>  
 <span data-ttu-id="884df-164">디바이스 정보 설정을 변경하여 렌더링할 모드를 비롯한 이 렌더러의 일부 기본 설정을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="884df-164">You can change some default settings for this renderer, including which mode to render in, by changing the device information settings.</span></span> <span data-ttu-id="884df-165">자세한 내용은 [HTML Device Information Settings](../html-device-information-settings.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="884df-165">For more information, see [HTML Device Information Settings](../html-device-information-settings.md).</span></span>  

## <a name="see-also"></a><span data-ttu-id="884df-166">참고 항목</span><span class="sxs-lookup"><span data-stu-id="884df-166">See Also</span></span>  
 <span data-ttu-id="884df-167">[Reporting Services &#40;보고서 작성기 및 SSRS의 페이지 매김&#41;](../report-design/pagination-in-reporting-services-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="884df-167">[Pagination in Reporting Services &#40;Report Builder  and SSRS&#41;](../report-design/pagination-in-reporting-services-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="884df-168">[보고서 작성기 및 SSRS&#41;&#40;렌더링 동작](../report-design/rendering-behaviors-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="884df-168">[Rendering Behaviors &#40;Report Builder  and SSRS&#41;](../report-design/rendering-behaviors-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="884df-169">[여러 보고서 렌더링 확장 프로그램에 대 한 대화형 기능 &#40;보고서 작성기 및 SSRS&#41;](interactive-functionality-different-report-rendering-extensions.md) </span><span class="sxs-lookup"><span data-stu-id="884df-169">[Interactive Functionality for Different Report Rendering Extensions &#40;Report Builder and SSRS&#41;](interactive-functionality-different-report-rendering-extensions.md) </span></span>  
 <span data-ttu-id="884df-170">[보고서 항목 &#40;보고서 작성기 및 SSRS&#41;렌더링](../report-design/rendering-report-items-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="884df-170">[Rendering Report Items &#40;Report Builder and SSRS&#41;](../report-design/rendering-report-items-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="884df-171">테이블, 행렬 및 목록&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="884df-171">Tables, Matrices, and Lists &#40;Report Builder and SSRS&#41;</span></span>](../report-design/create-invoices-and-forms-with-lists-report-builder-and-ssrs.md)  
