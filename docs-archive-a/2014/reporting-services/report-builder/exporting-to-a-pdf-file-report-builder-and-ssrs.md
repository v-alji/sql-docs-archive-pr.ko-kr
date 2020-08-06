---
title: PDF 파일로 내보내기(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: f22497b7-f6c1-4c7b-b831-8c731e26ae37
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 4b4a324ad40d01d302196fe40ffb4232deb62a17
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639369"
---
# <a name="exporting-to-a-pdf-file-report-builder-and-ssrs"></a><span data-ttu-id="9d7f6-102">PDF 파일로 내보내기(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="9d7f6-102">Exporting to a PDF File (Report Builder and SSRS)</span></span>
  <span data-ttu-id="9d7f6-103">PDF 렌더링 확장 프로그램은 Adobe Acrobat 및 PDF 1.3을 지원하는 타사 PDF 뷰어에서 열 수 있는 파일로 보고서를 렌더링합니다.</span><span class="sxs-lookup"><span data-stu-id="9d7f6-103">The PDF rendering extension renders a report to files that can be opened in Adobe Acrobat and other third-party PDF viewers that support PDF 1.3.</span></span> <span data-ttu-id="9d7f6-104">PDF 1.3은 Adobe Acrobat 4.0 이상 버전과 호환되지만 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 에서는 Adobe Acrobat 6 이상 버전을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="9d7f6-104">Although PDF 1.3 is compatible with Adobe Acrobat 4.0 and later versions, [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] supports Adobe Acrobat 6 or later.</span></span> <span data-ttu-id="9d7f6-105">이 렌더링 확장 프로그램으로 보고서를 렌더링하기 위해 Adobe 소프트웨어가 필요한 것은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="9d7f6-105">The rendering extension does not require Adobe software to render the report.</span></span> <span data-ttu-id="9d7f6-106">그러나 PDF 형식으로 보고서를 보거나 인쇄하기 위해서는 Adobe Acrobat과 같은 PDF 뷰어가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="9d7f6-106">However, PDF viewers such as Adobe Acrobat are required to view or print a report in PDF format.</span></span>  
  
 <span data-ttu-id="9d7f6-107">PDF 렌더링 확장 프로그램에서는 ANSI 문자를 지원하며 한국어, 일본어, 중국어 번체, 중국어 간체, 키릴 자모, 히브리어 및 아랍어를 특정 제한과 함께 유니코드 문자로 변환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9d7f6-107">The PDF rendering extension supports ANSI characters and can translate Unicode characters from Japanese, Korean, Traditional Chinese, Simplified Chinese, Cyrillic, Hebrew, and Arabic with certain limitations.</span></span> <span data-ttu-id="9d7f6-108">제한 사항에 대 한 자세한 내용은 [보고서 &#40;보고서 작성기 및 SSRS&#41;내보내기 ](export-reports-report-builder-and-ssrs.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="9d7f6-108">For more information about the limitations, see [Exporting Reports &#40;Report Builder and SSRS&#41;](export-reports-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="9d7f6-109">PDF 렌더러는 물리적 페이지 렌더러이므로 페이지 매김 동작이 HTML 및 Excel 같은 다른 렌더러와는 차이가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9d7f6-109">The PDF renderer is a physical page renderer and, therefore, has pagination behavior that differs from other renderers such as HTML and Excel.</span></span> <span data-ttu-id="9d7f6-110">이 항목에서는 PDF 렌더러 관련 정보를 제공하고 규칙의 예외를 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="9d7f6-110">This topic provides PDF renderer-specific information and describes exceptions to the rules.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
##  <a name="font-embedding"></a><a name="FontRequirements"></a><span data-ttu-id="9d7f6-111">글꼴 포함</span><span class="sxs-lookup"><span data-stu-id="9d7f6-111">Font Embedding</span></span>  
 <span data-ttu-id="9d7f6-112">가능한 경우 PDF 렌더링 확장 프로그램에는 보고서를 PDF 파일로 표시하는 데 필요한 각 하위 집합이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9d7f6-112">When possible, the PDF rendering extension embeds the subset of each font that is needed to display the report in the PDF file.</span></span> <span data-ttu-id="9d7f6-113">보고서에 사용된 글꼴이 보고서 서버에 설치되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9d7f6-113">Fonts that are used in the report must be installed on the report server.</span></span> <span data-ttu-id="9d7f6-114">보고서 서버는 PDF 형식으로 보고서를 생성할 때 보고서에서 참조하는 글꼴로 저장된 정보를 사용하여 PDF 파일 내에 문자 매핑을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="9d7f6-114">When the report server generates a report in PDF format, it uses the information stored in the font referenced by the report to create character mappings within the PDF file.</span></span> <span data-ttu-id="9d7f6-115">렌더링된 글꼴이 보고서 서버에 설치되어 있지 않으면 결과 PDF 파일이 올바른 매핑을 포함하지 않을 수 있으며 화면에 올바르게 표시되지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9d7f6-115">If the referenced font is not installed on the report server, the resulting PDF file might not contain the correct mappings and might not display correctly when viewed.</span></span>  
  
 <span data-ttu-id="9d7f6-116">다음 조건을 만족할 경우 PDF 파일에 글꼴이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="9d7f6-116">Fonts are embedded in the PDF file when the following conditions apply:</span></span>  
  
-   <span data-ttu-id="9d7f6-117">글꼴 작성자가 글꼴 포함 권한을 허가한 경우.</span><span class="sxs-lookup"><span data-stu-id="9d7f6-117">Font embedding privileges are granted by the font author.</span></span> <span data-ttu-id="9d7f6-118">설치된 글꼴에는 글꼴 작성자가 문서에 글꼴 포함을 허용했는지 여부를 나타내는 속성이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9d7f6-118">Installed fonts include a property that indicates whether the font author intends to allow embedding a font in a document.</span></span> <span data-ttu-id="9d7f6-119">속성 값이 EMBED_NOEMBEDDING이면 글꼴이 PDF 파일에 포함되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9d7f6-119">If the property value is EMBED_NOEMBEDDING, the font is not embedded in the PDF file.</span></span> <span data-ttu-id="9d7f6-120">자세한 내용은 msdn.microsoft.com의 "TTGetEmbeddingType"을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="9d7f6-120">For more information, see "TTGetEmbeddingType" on msdn.microsoft.com.</span></span>  
  
-   <span data-ttu-id="9d7f6-121">글꼴이 트루타입인 경우</span><span class="sxs-lookup"><span data-stu-id="9d7f6-121">The Font is TrueType.</span></span>  
  
-   <span data-ttu-id="9d7f6-122">보고서에 표시되는 항목이 글꼴을 참조하는 경우.</span><span class="sxs-lookup"><span data-stu-id="9d7f6-122">Fonts are referenced by visible items in a report.</span></span> <span data-ttu-id="9d7f6-123">숨김 속성이 True로 설정된 항목이 글꼴을 참조하는 경우 렌더링된 데이터를 표시하는 데 글꼴이 필요하지 않으므로 파일에 포함되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9d7f6-123">If a font is referenced by an item that has the Hidden property set to True, the font is not needed to display rendered data and will not be included in the file.</span></span> <span data-ttu-id="9d7f6-124">렌더링된 보고서 데이터를 표시하는 데 필요한 글꼴만 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="9d7f6-124">Fonts are embedded only when they are needed to display the rendered report data.</span></span>  
  
 <span data-ttu-id="9d7f6-125">이러한 조건을 모두 만족하는 경우에만 PDF 파일에 글꼴이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="9d7f6-125">If all of these conditions are met for a font, the font is embedded in the PDF file.</span></span> <span data-ttu-id="9d7f6-126">이 조건 중 하나라도 만족하지 않으면 PDF 파일에 글꼴이 포함되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9d7f6-126">If one or more of these conditions is not met, the font is not embedded in the PDF file.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9d7f6-127">조건이 충족되는 경우에도 글꼴이 PDF 파일에 포함되지 않는 한 가지 상황이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9d7f6-127">Although the conditions are met, there is one circumstance under which fonts are not embedded in the PDF file.</span></span> <span data-ttu-id="9d7f6-128">사용된 글꼴이 표준 유형 1 글꼴 또는 기본 14 글꼴이라고 하는 PDF 사양 항목인 경우 글꼴이 ANSI 콘텐츠에 포함되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9d7f6-128">If the fonts used are the ones in the PDF specification that are commonly known as standard type 1 fonts or the base fourteen fonts, then fonts are not embedded for ANSI content.</span></span>  
  
  
  
### <a name="fonts-on-the-client-computer"></a><span data-ttu-id="9d7f6-129">클라이언트 컴퓨터의 글꼴</span><span class="sxs-lookup"><span data-stu-id="9d7f6-129">Fonts on the Client Computer</span></span>  
 <span data-ttu-id="9d7f6-130">글꼴이 PDF 파일에 포함되면 컴퓨터(클라이언트 컴퓨터)에 해당 글꼴이 설치되어 있지 않아도 보고서가 제대로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="9d7f6-130">When a font is embedded in the PDF file, the computer that is used to view the report (the client computer) does not need to have the font installed for the report to display correctly.</span></span>  
  
 <span data-ttu-id="9d7f6-131">글꼴이 PDF 파일에 포함되지 않으면 컴퓨터에 해당 글꼴이 설치되어 있어야 보고서가 제대로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="9d7f6-131">When a font is not embedded in the PDF file, the client computer must have the correct font installed for the report to display correctly.</span></span> <span data-ttu-id="9d7f6-132">클라이언트 컴퓨터에 글꼴이 설치되어 있지 않으면 PDF 파일에서 지원되지 않는 글자가 물음표(?)로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="9d7f6-132">If the font is not installed on the client computer, the PDF file displays a question mark character (?) for unsupported characters.</span></span>  
  
### <a name="verifying-fonts-in-a-pdf-file"></a><span data-ttu-id="9d7f6-133">PDF 파일의 글꼴 확인</span><span class="sxs-lookup"><span data-stu-id="9d7f6-133">Verifying Fonts in a PDF File</span></span>  
 <span data-ttu-id="9d7f6-134">PDF 출력 결과가 다르게 나타나는 현상은 주로 보고서에 사용된 글꼴이 라틴어 이외의 문자를 지원하지 않는데 라틴어 이외의 문자를 보고서에 추가한 경우 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="9d7f6-134">Differences in PDF output occur most often when a font that does not support non-Latin characters is used in a report and then non-Latin characters are added to the report.</span></span> <span data-ttu-id="9d7f6-135">보고서가 제대로 렌더링되는지 확인하려면 보고서 서버와 클라이언트 컴퓨터 모두에서 PDF 렌더링 출력을 테스트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9d7f6-135">You should test the PDF rendering output on both the report server and the client computers to verify that the report renders correctly.</span></span>  
  
 <span data-ttu-id="9d7f6-136">그래픽 디자인 인터페이스나 Microsoft Internet Explorer에서는 자동으로 글꼴이 대체되어 올바르게 표시되기 때문에 미리 보기나 HTML로 내보낸 결과만 믿어서는 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9d7f6-136">Do not rely on viewing the report in Preview or exporting to HTML because the report will look correct due to automatic font substitution performed by the graphical design interface or by Microsoft Internet Explorer, respectively.</span></span> <span data-ttu-id="9d7f6-137">서버에 유니코드 문자가 없으면 문자가 물음표(?)로 바뀌어 표시될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9d7f6-137">If there are Unicode Glyphs missing on the server, you may see characters replaced with a question mark (?).</span></span> <span data-ttu-id="9d7f6-138">클라이언트에 글꼴이 없으면 문자가 사각형( )으로 바뀌어 표시될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9d7f6-138">If there is a font missing on the client, you may see characters replaced with boxes (□).</span></span>  
  
 <span data-ttu-id="9d7f6-139">PDF 파일에 포함된 글꼴은 파일에 저장된 Fonts 속성에 메타데이터로 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="9d7f6-139">The fonts that are embedded in the PDF file are included in the Fonts property that is saved with the file, as metadata.</span></span>  
  
##  <a name="metadata"></a><a name="Metadata"></a> <span data-ttu-id="9d7f6-140">메타데이터</span><span class="sxs-lookup"><span data-stu-id="9d7f6-140">Metadata</span></span>  
 <span data-ttu-id="9d7f6-141">PDF 렌더링 확장 프로그램에서는 보고서 레이아웃 이외에 다음과 같은 메타데이터를 PDF 문서 정보 사전에 기록합니다.</span><span class="sxs-lookup"><span data-stu-id="9d7f6-141">In addition to the report layout, the PDF rendering extension writes the following metadata to the PDF Document Information Dictionary.</span></span>  
  
|<span data-ttu-id="9d7f6-142">PDF 속성</span><span class="sxs-lookup"><span data-stu-id="9d7f6-142">PDF property</span></span>|<span data-ttu-id="9d7f6-143">정보 출처</span><span class="sxs-lookup"><span data-stu-id="9d7f6-143">Created from</span></span>|  
|------------------|------------------|  
|`Title`|<span data-ttu-id="9d7f6-144">`Name` RDL 요소의 `Report` 특성</span><span class="sxs-lookup"><span data-stu-id="9d7f6-144">The `Name` attribute of the `Report` RDL element.</span></span>|  
|`Author`|<span data-ttu-id="9d7f6-145">`Author` RDL 요소</span><span class="sxs-lookup"><span data-stu-id="9d7f6-145">The `Author` RDL element.</span></span>|  
|`Subject`|<span data-ttu-id="9d7f6-146">`Description` RDL 요소</span><span class="sxs-lookup"><span data-stu-id="9d7f6-146">The `Description` RDL element.</span></span>|  
|`Creator`|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="9d7f6-147">제품 이름 및 버전</span><span class="sxs-lookup"><span data-stu-id="9d7f6-147">product name and version.</span></span>|  
|`Producer`|<span data-ttu-id="9d7f6-148">렌더링 확장 프로그램 이름 및 버전</span><span class="sxs-lookup"><span data-stu-id="9d7f6-148">Rendering extension name and version.</span></span>|  
|`CreationDate`|<span data-ttu-id="9d7f6-149">PDF `datetime` 형식의 보고서 실행 시간</span><span class="sxs-lookup"><span data-stu-id="9d7f6-149">Report execution time in PDF `datetime` format.</span></span>|  
  
  
  
##  <a name="interactivity"></a><a name="Interactivity"></a><span data-ttu-id="9d7f6-150">대화형 작업</span><span class="sxs-lookup"><span data-stu-id="9d7f6-150">Interactivity</span></span>  
 <span data-ttu-id="9d7f6-151">PDF에서는 일부 대화형 요소가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="9d7f6-151">Some interactive elements are supported in PDF.</span></span> <span data-ttu-id="9d7f6-152">다음은 특정 동작에 대한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="9d7f6-152">The following is a description of specific behaviors.</span></span>  
  
### <a name="show-and-hide"></a><span data-ttu-id="9d7f6-153">표시 및 숨기기</span><span class="sxs-lookup"><span data-stu-id="9d7f6-153">Show and Hide</span></span>  
 <span data-ttu-id="9d7f6-154">동적 표시 및 숨기기 요소는 PDF에서 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9d7f6-154">Dynamic show and hide elements are not supported in PDF.</span></span> <span data-ttu-id="9d7f6-155">PDF 문서는 보고서에 포함된 모든 항목의 현재 상태와 일치하도록 렌더링됩니다.</span><span class="sxs-lookup"><span data-stu-id="9d7f6-155">The PDF document is rendered to match the current state of any items in the report.</span></span> <span data-ttu-id="9d7f6-156">예를 들어 보고서를 처음 실행할 때 항목이 표시된 상태이면 해당 항목이 렌더링됩니다.</span><span class="sxs-lookup"><span data-stu-id="9d7f6-156">For example, if the item is displayed when the report is run initially, then the item is rendered.</span></span> <span data-ttu-id="9d7f6-157">설정/해제할 수 있는 이미지의 경우 보고서를 내보낼 당시 숨겨진 상태이면 해당 이미지가 렌더링되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9d7f6-157">Images that can be toggled are not rendered, if they are hidden when the report is exported.</span></span>  
  
### <a name="document-map"></a><span data-ttu-id="9d7f6-158">문서 구조</span><span class="sxs-lookup"><span data-stu-id="9d7f6-158">Document Map</span></span>  
 <span data-ttu-id="9d7f6-159">보고서에 문서 구조 레이블이 있으면 PDF 파일에 문서 개요가 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="9d7f6-159">If there are any document map labels present in the report, a document outline is added to the PDF file.</span></span> <span data-ttu-id="9d7f6-160">각 문서 구조 레이블은 보고서에 표시된 것과 같은 순서에 따라 문서 개요의 항목으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="9d7f6-160">Each document map label appears as an entry in the document outline in the order that it appears in the report.</span></span> <span data-ttu-id="9d7f6-161">Acrobat에서는 문서 개요가 있는 페이지를 렌더링하는 경우에만 문서 개요에 대상 책갈피를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="9d7f6-161">In Acrobat, a target bookmark is added to the document outline only if the page it is on is rendered.</span></span>  
  
 <span data-ttu-id="9d7f6-162">한 페이지만 렌더링하는 경우에는 문서 개요가 추가되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9d7f6-162">If only a single page is rendered, no document outline is added.</span></span> <span data-ttu-id="9d7f6-163">문서 구조는 보고서의 중첩 수준을 반영하는 계층 구조에 따라 배열됩니다.</span><span class="sxs-lookup"><span data-stu-id="9d7f6-163">The document map is arranged hierarchically to reflect the level of nesting in the report.</span></span> <span data-ttu-id="9d7f6-164">문서 개요는 Acrobat의 책갈피 탭 아래에서 액세스할 수 있습니다. 문서 개요 내의 항목을 클릭 하면 문서가 책갈피가 설정 된 위치로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="9d7f6-164">The document outline is accessible in Acrobat under the Bookmarks tab. Clicking an entry within the document outline causes the document to go to the bookmarked location.</span></span>  
  
### <a name="bookmarks"></a><span data-ttu-id="9d7f6-165">책갈피</span><span class="sxs-lookup"><span data-stu-id="9d7f6-165">Bookmarks</span></span>  
 <span data-ttu-id="9d7f6-166">책갈피는 PDF 렌더링에 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9d7f6-166">Bookmarks are not supported in PDF rendering.</span></span>  
  
### <a name="drillthrough-links"></a><span data-ttu-id="9d7f6-167">드릴스루 링크</span><span class="sxs-lookup"><span data-stu-id="9d7f6-167">Drillthrough Links</span></span>  
 <span data-ttu-id="9d7f6-168">드릴스루 링크는 PDF 렌더링에 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9d7f6-168">Drillthrough links are not supported in PDF rendering.</span></span> <span data-ttu-id="9d7f6-169">드릴스루 링크는 클릭 가능한 링크로 렌더링되지 않으며 드릴스루 보고서는 드릴스루 대상에 연결할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9d7f6-169">The drillthrough links are not rendered as clickable links and drillthrough reports cannot connect to the target of the drillthrough.</span></span>  
  
### <a name="hyperlinks"></a><span data-ttu-id="9d7f6-170">하이퍼링크</span><span class="sxs-lookup"><span data-stu-id="9d7f6-170">Hyperlinks</span></span>  
 <span data-ttu-id="9d7f6-171">보고서의 하이퍼링크는 PDF 파일에서 클릭하여 연결할 수 있는 링크로 렌더링됩니다.</span><span class="sxs-lookup"><span data-stu-id="9d7f6-171">Hyperlinks in reports are rendered as clickable links in the PDF file.</span></span> <span data-ttu-id="9d7f6-172">이를 클릭하면 Acrobat에서 클라이언트의 기본 브라우저가 열리고 하이퍼링크 URL로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="9d7f6-172">When clicked, Acrobat will open the default client browser and navigate to the hyperlink URL.</span></span>  
  
  
  
##  <a name="compression"></a><a name="Compression"></a><span data-ttu-id="9d7f6-173">수신</span><span class="sxs-lookup"><span data-stu-id="9d7f6-173">Compression</span></span>  
 <span data-ttu-id="9d7f6-174">이미지 압축은 이미지의 원래 파일 형식을 기준으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="9d7f6-174">Image compression is based on the original file type of the image.</span></span> <span data-ttu-id="9d7f6-175">PDF 렌더링 확장 프로그램에서는 기본적으로 PDF 파일을 압축합니다.</span><span class="sxs-lookup"><span data-stu-id="9d7f6-175">The PDF rendering extension compresses PDF files by default.</span></span>  
  
 <span data-ttu-id="9d7f6-176">PDF 파일에 포함된 이미지의 모든 압축을 가능한 한 계속 유지하기 위해 JPEG 이미지는 JPEG로 저장되고 다른 모든 이미지 형식은 BMP로 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="9d7f6-176">To preserve any compression for images included in the PDF file when possible, JPEG images are stored as JPEG and all other image types are stored as BMP.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9d7f6-177">PDF 파일은 PNG 포함 이미지를 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9d7f6-177">PDF files don't support embedding PNG images.</span></span>  
  
  
  
##  <a name="device-information-settings"></a><a name="DeviceInfo"></a><span data-ttu-id="9d7f6-178">장치 정보 설정</span><span class="sxs-lookup"><span data-stu-id="9d7f6-178">Device Information Settings</span></span>  
 <span data-ttu-id="9d7f6-179">디바이스 정보 설정을 변경하여 이 렌더러의 기본 설정을 일부 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9d7f6-179">You can change some default settings for this renderer by changing the device information settings.</span></span> <span data-ttu-id="9d7f6-180">자세한 내용은 [PDF Device Information Settings](../pdf-device-information-settings.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9d7f6-180">For more information, see [PDF Device Information Settings](../pdf-device-information-settings.md).</span></span>  
  
  
  
## <a name="see-also"></a><span data-ttu-id="9d7f6-181">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9d7f6-181">See Also</span></span>  
 <span data-ttu-id="9d7f6-182">[Reporting Services &#40;보고서 작성기 및 SSRS의 페이지 매김&#41;](../report-design/pagination-in-reporting-services-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="9d7f6-182">[Pagination in Reporting Services &#40;Report Builder  and SSRS&#41;](../report-design/pagination-in-reporting-services-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="9d7f6-183">[보고서 작성기 및 SSRS&#41;&#40;렌더링 동작](../report-design/rendering-behaviors-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="9d7f6-183">[Rendering Behaviors &#40;Report Builder  and SSRS&#41;](../report-design/rendering-behaviors-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="9d7f6-184">[여러 보고서 렌더링 확장 프로그램에 대 한 대화형 기능 &#40;보고서 작성기 및 SSRS&#41;](interactive-functionality-different-report-rendering-extensions.md) </span><span class="sxs-lookup"><span data-stu-id="9d7f6-184">[Interactive Functionality for Different Report Rendering Extensions &#40;Report Builder and SSRS&#41;](interactive-functionality-different-report-rendering-extensions.md) </span></span>  
 <span data-ttu-id="9d7f6-185">[보고서 항목 &#40;보고서 작성기 및 SSRS&#41;렌더링](../report-design/rendering-report-items-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="9d7f6-185">[Rendering Report Items &#40;Report Builder and SSRS&#41;](../report-design/rendering-report-items-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="9d7f6-186">테이블, 행렬 및 목록&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="9d7f6-186">Tables, Matrices, and Lists &#40;Report Builder and SSRS&#41;</span></span>](../report-design/create-invoices-and-forms-with-lists-report-builder-and-ssrs.md)  
  
  
