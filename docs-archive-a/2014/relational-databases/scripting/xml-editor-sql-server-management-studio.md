---
title: XML 편집기
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- sql12.swb.editorxml.f1
- sql12.swb.xmleditor.f1
- vs.xmleditor
- sql12.swb.editor.xml.f1
helpviewer_keywords:
- XML Designer [SQL Server Management Studio]
ms.assetid: 0824a5ce-e67b-4b53-98d9-d371faf2d23c
author: rothja
ms.author: jroth
ms.openlocfilehash: b7c3bbbda4f5a31c4d83b559c1aa623ca2aff89f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659917"
---
# <a name="xml-editor-sql-server-management-studio"></a><span data-ttu-id="3ed09-102">XML 편집기(SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="3ed09-102">XML Editor (SQL Server Management Studio)</span></span>
  <span data-ttu-id="3ed09-103">XML 스키마, ADO.NET 데이터 세트 및 XML 문서 작업에 사용할 수 있는 다양한 시각적 도구를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="3ed09-103">Provides a set of visual tools for working with XML Schemas, ADO.NET datasets, and XML documents.</span></span> <span data-ttu-id="3ed09-104">XML 디자이너는 WC3(World Wide Web Consortium)에서 정의한 XSD(XML 스키마 정의) 언어를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="3ed09-104">The XML Designer supports the XML Schema Definition (XSD) language defined by the World Wide Web Consortium (WC3).</span></span> <span data-ttu-id="3ed09-105">DTD(문서 유형 정의)나 XDR(XML-Data Reduced)와 같은 다른 XML 스키마 언어는 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3ed09-105">The designer does not support DTDs (document type definitions) or other XML schema languages, such as XDR (XML-Data Reduced).</span></span>  
  
 <span data-ttu-id="3ed09-106">디자이너를 표시하려면 데이터 세트, XML 스키마 또는 XML 파일을 프로젝트에 추가하거나 아래 표에 나오는 파일 형식을 여십시오.</span><span class="sxs-lookup"><span data-stu-id="3ed09-106">To display the designer, add a dataset, XML Schema, or XML file to your project or open any of the file types listed in the table below.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="3ed09-107">스키마 뷰에서 작업할 때는 **실행 취소** 명령을 사용할 수 없으므로</span><span class="sxs-lookup"><span data-stu-id="3ed09-107">There is no **Undo** command when working in Schema view.</span></span> <span data-ttu-id="3ed09-108">작업을 신중하게 계획하고 파일을 자주 저장하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="3ed09-108">Plan your work carefully and save your files often.</span></span>  
  
 <span data-ttu-id="3ed09-109">XML 디자이너는 XML 파일, XML 스키마 및 데이터 세트 작업에 다음 세 가지 뷰(또는 모드)를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="3ed09-109">The designer provides the following three views (or modes) to work on XML files, XML Schemas, and datasets:</span></span>  
  
|<span data-ttu-id="3ed09-110">보기</span><span class="sxs-lookup"><span data-stu-id="3ed09-110">View</span></span>|<span data-ttu-id="3ed09-111">Description</span><span class="sxs-lookup"><span data-stu-id="3ed09-111">Description</span></span>|<span data-ttu-id="3ed09-112">지원되는 파일 형식</span><span class="sxs-lookup"><span data-stu-id="3ed09-112">File types supported</span></span>|  
|----------|-----------------|--------------------------|  
|<span data-ttu-id="3ed09-113">**스키마**</span><span class="sxs-lookup"><span data-stu-id="3ed09-113">**Schema**</span></span>|<span data-ttu-id="3ed09-114">XML 스키마 및 ADO.NET 데이터 세트를 시각적으로 만들고 수정할 때 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="3ed09-114">For visually creating and modifying XML Schemas and ADO.NET datasets.</span></span>|<span data-ttu-id="3ed09-115">.xsd</span><span class="sxs-lookup"><span data-stu-id="3ed09-115">.xsd</span></span>|  
|<span data-ttu-id="3ed09-116">**Data**</span><span class="sxs-lookup"><span data-stu-id="3ed09-116">**Data**</span></span>|<span data-ttu-id="3ed09-117">구조화된 데이터 표에서 XML 데이터 파일을 시각적으로 수정할 때 사용</span><span class="sxs-lookup"><span data-stu-id="3ed09-117">For visually modifying XML data files in a structured data grid.</span></span>|<span data-ttu-id="3ed09-118">.xml</span><span class="sxs-lookup"><span data-stu-id="3ed09-118">.xml</span></span>|  
|<span data-ttu-id="3ed09-119">**XML**</span><span class="sxs-lookup"><span data-stu-id="3ed09-119">**XML**</span></span>|<span data-ttu-id="3ed09-120">XML을 편집할 때 사용. 원본 편집기는 색 구분과 단어 자동 완성 및 멤버 목록 표시를 비롯한 IntelliSense 기능 제공</span><span class="sxs-lookup"><span data-stu-id="3ed09-120">For editing XML; the source editor provides color-coding and IntelliSense, including Complete Word and List Members.</span></span>|<span data-ttu-id="3ed09-121">.xml .xsd .xslt .wsdl .web. resx .tdl. wsf .hta .disco .vsdisco .config</span><span class="sxs-lookup"><span data-stu-id="3ed09-121">.xml .xsd .xslt .wsdl.web.resx.tdl.wsf.hta.disco.vsdisco.config</span></span>|  
|<span data-ttu-id="3ed09-122">**실행 계획**</span><span class="sxs-lookup"><span data-stu-id="3ed09-122">**ShowPlan**</span></span>|<span data-ttu-id="3ed09-123">SET SHOWPLAN_XML ON 옵션을 사용하여 만든 xml 쿼리 계획 표시</span><span class="sxs-lookup"><span data-stu-id="3ed09-123">Displays xml query plans created using the SET SHOWPLAN_XML ON option.</span></span>|<span data-ttu-id="3ed09-124">.showplan</span><span class="sxs-lookup"><span data-stu-id="3ed09-124">.showplan</span></span>|  
  
## <a name="schema-view"></a><span data-ttu-id="3ed09-125">스키마 뷰</span><span class="sxs-lookup"><span data-stu-id="3ed09-125">Schema View</span></span>  
 <span data-ttu-id="3ed09-126">스키마 뷰는 XML 스키마와 ADO.NET 데이터 세트를 구성하는 요소, 특성, 유형 등을 시각적으로 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="3ed09-126">Schema view provides a visual representation of the elements, attributes, types, and so on, that make up XML Schemas and ADO.NET datasets.</span></span>  
  
 <span data-ttu-id="3ed09-127">스키마 뷰에서는 도구 상자의 XML 스키마 탭이나 서버 탐색기 중 하나에서 디자인 화면으로 요소를 끌어 놓아 스키마와 데이터 세트를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3ed09-127">In Schema view you can construct schemas and datasets by dropping elements on the design surface from either the XML Schema tab of the Toolbox or from Server Explorer.</span></span> <span data-ttu-id="3ed09-128">또한 디자인 화면을 마우스 오른쪽 단추로 클릭하고 바로 가기 메뉴에서 추가를 선택하여 요소를 디자이너에 추가할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3ed09-128">Additionally, you can add elements to the designer by right-clicking the design surface and selecting Add from the shortcut menu.</span></span>  
  
 <span data-ttu-id="3ed09-129">스키마 뷰에서는 다음 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3ed09-129">In Schema view you can:</span></span>  
  
-   <span data-ttu-id="3ed09-130">기존 XML 스키마와 ADO.NET 데이터 세트 생성 및 수정</span><span class="sxs-lookup"><span data-stu-id="3ed09-130">Construct and modify existing XML Schemas and ADO.NET datasets</span></span>  
  
-   <span data-ttu-id="3ed09-131">테이블 간 관계 만들기 및 편집</span><span class="sxs-lookup"><span data-stu-id="3ed09-131">Create and edit relationships between tables</span></span>  
  
-   <span data-ttu-id="3ed09-132">키 만들기 및 편집</span><span class="sxs-lookup"><span data-stu-id="3ed09-132">Create and edit keys</span></span>  
  
-   <span data-ttu-id="3ed09-133">XML 스키마에서 ADO.NET 데이터 세트 생성</span><span class="sxs-lookup"><span data-stu-id="3ed09-133">Generate ADO.NET datasets from XML Schemas</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3ed09-134">스키마 뷰에서 요소의 레이아웃은 .xsx 파일로 저장됩니다. 솔루션 탐색기 도구 모음에서 **모든 파일 표시** 를 클릭한 다음 .xsd 파일을 확장하면 이 파일을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3ed09-134">The layout of elements in Schema view is stored in the .xsx file, which can be seen by clicking **Show All Files** in the Solution Explorer toolbar, and then expanding the .xsd file.</span></span> <span data-ttu-id="3ed09-135">.xsx 파일이 표시되지 않으면 이전에 XML 디자이너에서 .xsd 파일을 열어본 적이 없는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="3ed09-135">If there is no .xsx file present, it means the .xsd file has never been opened in the XML Designer.</span></span>  
  
### <a name="customizing-schema-view"></a><span data-ttu-id="3ed09-136">스키마 뷰 사용자 지정</span><span class="sxs-lookup"><span data-stu-id="3ed09-136">Customizing Schema View</span></span>  
 <span data-ttu-id="3ed09-137">다음 기능은 스키마 뷰에서 요소의 시각적 레이아웃을 수정하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="3ed09-137">The following features modify the visual layout of elements in Schema view:</span></span>  
  
-   <span data-ttu-id="3ed09-138">확대/축소</span><span class="sxs-lookup"><span data-stu-id="3ed09-138">Zooming</span></span>  
  
-   <span data-ttu-id="3ed09-139">중첩된 요소 확장 또는 축소</span><span class="sxs-lookup"><span data-stu-id="3ed09-139">Expanding or collapsing of nested elements</span></span>  
  
-   <span data-ttu-id="3ed09-140">요소 레이아웃 자동 정렬</span><span class="sxs-lookup"><span data-stu-id="3ed09-140">Automatically arranging layout of elements</span></span>  
  
-   <span data-ttu-id="3ed09-141">축소된 요소의 기본 상태 다시 설정</span><span class="sxs-lookup"><span data-stu-id="3ed09-141">Resetting default state of collapsed elements</span></span>  
  
##### <a name="to-expand-hidden-nested-elements"></a><span data-ttu-id="3ed09-142">숨겨진 중첩 요소를 확장하려면</span><span class="sxs-lookup"><span data-stu-id="3ed09-142">To expand hidden nested elements</span></span>  
  
-   <span data-ttu-id="3ed09-143">요소 아래쪽의 더하기 아이콘을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3ed09-143">Click the plus icon on the bottom of the element.</span></span>  
  
##### <a name="to-collapse-nested-elements"></a><span data-ttu-id="3ed09-144">중첩 요소를 축소하려면</span><span class="sxs-lookup"><span data-stu-id="3ed09-144">To collapse nested elements</span></span>  
  
-   <span data-ttu-id="3ed09-145">디자이너에 표시하려는 맨 아래 요소의 빼기 아이콘을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3ed09-145">Click the minus icon on the bottom-most element that you want to appear on the designer.</span></span>  
  
## <a name="data-view"></a><span data-ttu-id="3ed09-146">데이터 뷰</span><span class="sxs-lookup"><span data-stu-id="3ed09-146">Data View</span></span>  
 <span data-ttu-id="3ed09-147">데이터 뷰는 .xml 파일을 수정하는 데 사용할 수 있는 데이터 표를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="3ed09-147">Data view provides a data grid that can be used to modify .xml files.</span></span> <span data-ttu-id="3ed09-148">데이터 뷰에서는 XML 파일의 내용만 편집할 수 있으며 태그와 구조는 편집할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3ed09-148">Only the content (but not the tags and structure) in an XML file can be edited in Data view.</span></span>  
  
 <span data-ttu-id="3ed09-149">데이터 뷰에는 **데이터 테이블** 및 **데이터**의 두 가지 별도 영역이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3ed09-149">There are two separate areas in Data view: **Data Tables** and **Data**.</span></span> <span data-ttu-id="3ed09-150">**데이터 테이블** 영역은 XML 파일에 정의되어 있는 관계를 중첩된 순서(바깥쪽에서부터 안쪽으로)대로 보여 주는 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="3ed09-150">The **Data Tables** area is a list of relations defined in the XML file, in the order of its nesting (from the outermost to the innermost).</span></span> <span data-ttu-id="3ed09-151">**데이터** 영역은 데이터 테이블 영역에서 선택한 내용에 따라 해당 데이터를 표시하는 데이터 표입니다.</span><span class="sxs-lookup"><span data-stu-id="3ed09-151">The **Data** area is a data grid that displays data based on the selection in the Data Tables area.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3ed09-152">새로 만든 XML 파일에는 데이터가 들어 있지 않으므로 데이터 뷰에서 표시할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3ed09-152">Newly created XML files contain no data and therefore cannot be displayed in Data view.</span></span> <span data-ttu-id="3ed09-153">이외에도 일부 XML 문서에서는 데이터 뷰를 실행할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3ed09-153">There are also some instances of XML documents where data view cannot be invoked at all.</span></span> <span data-ttu-id="3ed09-154">XML의 형식이 올바르더라도 구조화된 데이터가 아닌 경우 데이터 뷰로 전환하려고 하면 "이 XML 문서는 형식이 올바르지만 데이터 뷰에서 표시할 수 없는 구조를 포함하고 있습니다"라는 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="3ed09-154">Although the XML would be considered well formed, if it is not structured data trying to switch to Data view will generate the following message: "Although this document is well formed, it contains structure that Data View cannot display."</span></span>  
  
 <span data-ttu-id="3ed09-155">데이터 뷰에서는 다음 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3ed09-155">In Data view you can:</span></span>  
  
-   <span data-ttu-id="3ed09-156">수동으로 데이터 테이블 채우기</span><span class="sxs-lookup"><span data-stu-id="3ed09-156">Manually populate data tables</span></span>  
  
-   <span data-ttu-id="3ed09-157">기존 데이터 테이블 편집</span><span class="sxs-lookup"><span data-stu-id="3ed09-157">Edit existing data tables</span></span>  
  
-   <span data-ttu-id="3ed09-158">XML 문서에서 XML 스키마 생성</span><span class="sxs-lookup"><span data-stu-id="3ed09-158">Generate an XML Schema from an XML document</span></span>  
  
## <a name="xml-view"></a><span data-ttu-id="3ed09-159">XML 뷰</span><span class="sxs-lookup"><span data-stu-id="3ed09-159">XML View</span></span>  
 <span data-ttu-id="3ed09-160">XML 뷰는 원시 XML을 편집할 수 있는 편집기와 IntelliSense 및 색 구분 기능을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="3ed09-160">XML view provides an editor for editing raw XML and provides IntelliSense and color coding.</span></span> <span data-ttu-id="3ed09-161">스키마가 연결되어 있는 .xml 파일과 .xsd 파일로 작업할 때는 문 완성 기능을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3ed09-161">Statement completion is available when working on .xsd files and .xml files that have an associated schema.</span></span> <span data-ttu-id="3ed09-162">을 입력 \< 하 여 태그를 시작 하면 해당 위치에서 유효한 요소 목록이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3ed09-162">Type \< to initiate a tag and you will be presented with a list of elements that are valid at that location.</span></span> <span data-ttu-id="3ed09-163">요소 이름을 입력한 후 스페이스바를 누르면 요소가 지원하는 특성이 목록으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="3ed09-163">After you type the element name and press the SPACEBAR, you will be presented with a list of attributes that the element supports.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="3ed09-164">IntelliSense 옵션은 도구 모음에서 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3ed09-164">IntelliSense options are not available on the toolbar.</span></span> <span data-ttu-id="3ed09-165">XML 편집기에서 이 옵션을 사용하려면 **편집** 메뉴에서 **IntelliSense**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3ed09-165">When in the XML Editor, to access the options, on the **Edit** menu, click **IntelliSense**.</span></span>  
  
## <a name="showplan-view"></a><span data-ttu-id="3ed09-166">실행 계획 뷰</span><span class="sxs-lookup"><span data-stu-id="3ed09-166">SHOWPLAN view</span></span>  
 <span data-ttu-id="3ed09-167">SET SHOWPLAN_XML ON 옵션을 사용하여 만든 쿼리 계획을 XML 형식으로 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3ed09-167">Query plans can be saved in XML format when created using SET SHOWPLAN_XML ON option.</span></span> <span data-ttu-id="3ed09-168">쿼리 계획을 열려면 확장명이 .showplan인 파일을 두 번 클릭하십시오.</span><span class="sxs-lookup"><span data-stu-id="3ed09-168">Double-click a file with the .showplan extension to open the query plan.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ed09-169">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3ed09-169">See Also</span></span>  
 [<span data-ttu-id="3ed09-170">XML 형식으로 실행 계획 저장</span><span class="sxs-lookup"><span data-stu-id="3ed09-170">Save an Execution Plan in XML Format</span></span>](../performance/save-an-execution-plan-in-xml-format.md)  
  
  
