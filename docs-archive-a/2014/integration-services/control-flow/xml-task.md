---
title: XML 태스크 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.xmltask.f1
helpviewer_keywords:
- XML [Integration Services]
- XML task [Integration Services]
ms.assetid: 9f761846-390e-46d5-9db7-858943d40849
author: chugugrace
ms.author: chugu
ms.openlocfilehash: bd6c63a95f6972b53f88e4db1ab6f980971accac
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651835"
---
# <a name="xml-task"></a><span data-ttu-id="876aa-102">XML 태스크</span><span class="sxs-lookup"><span data-stu-id="876aa-102">XML Task</span></span>
  <span data-ttu-id="876aa-103">XML 태스크는 XML 데이터를 통한 작업 시 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="876aa-103">The XML task is used to work with XML data.</span></span> <span data-ttu-id="876aa-104">패키지는 이 태스크를 사용하여 XML 문서를 검색하고, XSLT(Extensible Stylesheet Language Transformations) 스타일시트 및 XPath 식을 통해 문서에 작업을 적용하고, 여러 문서를 병합하거나 업데이트된 문서를 파일 및 변수에 대해 유효성을 검사하고, 비교 및 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="876aa-104">Using this task, a package can retrieve XML documents, apply operations to the documents by using Extensible Stylesheet Language Transformations (XSLT) style sheets and XPath expressions, merge multiple documents, or validate, compare, and save the updated documents to files and variables.</span></span>  
  
 <span data-ttu-id="876aa-105">이 태스크를 사용하면 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 패키지에서 XML 문서를 런타임에 동적으로 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="876aa-105">This task enables an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package to dynamically modify XML documents at run time.</span></span> <span data-ttu-id="876aa-106">XML 태스크는 다음 용도로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="876aa-106">You can use the XML task for the following purposes:</span></span>  
  
-   <span data-ttu-id="876aa-107">XML 문서 형식을 다시 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="876aa-107">Reformat an XML document.</span></span> <span data-ttu-id="876aa-108">예를 들어 태스크에서 XML 파일에 있는 보고서에 액세스하고 XSLT 스타일시트를 동적으로 적용하여 문서를 사용자 지정 방식으로 표현할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="876aa-108">For example, the task can access a report that resides in an XML file and dynamically apply an XSLT style sheet to customize the document presentation.</span></span>  
  
-   <span data-ttu-id="876aa-109">XML 문서의 섹션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="876aa-109">Select sections of an XML document.</span></span> <span data-ttu-id="876aa-110">예를 들어 태스크에서 XML 파일에 있는 보고서에 액세스하고 XPath 식을 동적으로 적용하여 문서의 섹션을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="876aa-110">For example, the task can access a report that resides in an XML file and dynamically apply an XPath expression to select a section of the document.</span></span> <span data-ttu-id="876aa-111">이 작업은 문서의 값을 가져오고 처리할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="876aa-111">The operation can also get and process values in the document.</span></span>  
  
-   <span data-ttu-id="876aa-112">여러 원본으로부터 문서를 병합합니다.</span><span class="sxs-lookup"><span data-stu-id="876aa-112">Merge documents from many sources.</span></span> <span data-ttu-id="876aa-113">예를 들어 태스크에서 여러 원본으로부터 보고서를 다운로드하고 이를 하나의 포괄적인 XML 문서로 동적으로 병합할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="876aa-113">For example, the task can download reports from multiple sources and dynamically merge them into one comprehensive XML document.</span></span>  
  
-   <span data-ttu-id="876aa-114">XML 문서의 유효성을 검사하고 필요에 따라 자세한 오류 출력을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="876aa-114">Validate an XML document and optionally get detailed error output.</span></span> <span data-ttu-id="876aa-115">자세한 내용은 [Validate XML with the XML Task](xml-task.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="876aa-115">For more info, see [Validate XML with the XML Task](xml-task.md).</span></span>  
  
 <span data-ttu-id="876aa-116">XML 원본을 사용하여 XML 문서에서 값을 추출하면 데이터 흐름에 XML 데이터를 포함시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="876aa-116">You can include XML data in a data flow by using an XML source to extract values from an XML document.</span></span> <span data-ttu-id="876aa-117">자세한 내용은 [XML Source](../data-flow/xml-source.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="876aa-117">For more information, see [XML Source](../data-flow/xml-source.md).</span></span>  
  
## <a name="xml-operations"></a><span data-ttu-id="876aa-118">XML 작업</span><span class="sxs-lookup"><span data-stu-id="876aa-118">XML Operations</span></span>  
 <span data-ttu-id="876aa-119">XML 태스크에서 수행하는 첫 번째 동작은 특정 XML 문서를 검색하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="876aa-119">The first action the XML task performs is to retrieve a specific XML document.</span></span> <span data-ttu-id="876aa-120">이 동작은 XML 태스크에 포함되며 자동으로 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="876aa-120">This action is built into the XML task and occurs automatically.</span></span> <span data-ttu-id="876aa-121">검색된 XML 문서는 XML 태스크에서 수행하는 작업에 대한 데이터 원본으로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="876aa-121">The retrieved XML document is used as the source of data for the operation that the XML task performs.</span></span>  
  
 <span data-ttu-id="876aa-122">비교, 병합 및 패치와 같은 XML 작업에는 두 개의 피연산자가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="876aa-122">The XML operations Diff, Merge, and Patch require two operands.</span></span> <span data-ttu-id="876aa-123">첫 번째 피연산자는 원본 XML 문서를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="876aa-123">The first operand specifies the source XML document.</span></span> <span data-ttu-id="876aa-124">두 번째 피연산자도 XML 문서를 지정하지만 이 문서의 내용은 작업 요구 사항에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="876aa-124">The second operand also specifies an XML document, the contents of which depend on the requirements of the operation.</span></span> <span data-ttu-id="876aa-125">예를 들어 비교 작업은 두 문서를 비교하므로 두 번째 피연산자는 원본 XML 문서가 비교될 비슷한 다른 XML 문서를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="876aa-125">For example, the Diff operation compares two documents; therefore, the second operand specifies another, similar XML document to which the source XML document is compared.</span></span>  
  
 <span data-ttu-id="876aa-126">XML 태스크는 변수나 파일 연결 관리자를 원본으로 사용하거나 태스크 속성에 XML 데이터를 포함시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="876aa-126">The XML task can use a variable or a File connection manager as its source, or include the XML data in a task property.</span></span>  
  
 <span data-ttu-id="876aa-127">원본이 변수인 경우 지정된 변수에는 XML 문서의 경로가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="876aa-127">If the source is a variable, the specified variable contains the path of the XML document.</span></span>  
  
 <span data-ttu-id="876aa-128">원본이 파일 연결 관리자인 경우 지정된 파일 연결 관리자는 원본 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="876aa-128">If the source is a File connection manager, the specified File connection manager provides the source information.</span></span> <span data-ttu-id="876aa-129">파일 연결 관리자는 XML 태스크와 별도로 구성되며 XML 태스크에서 참조됩니다.</span><span class="sxs-lookup"><span data-stu-id="876aa-129">The File connection manager is configured separately from the XML task, and is referenced in the XML task.</span></span> <span data-ttu-id="876aa-130">파일 연결 관리자의 연결 문자열은 XML 파일의 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="876aa-130">The connection string of the File connection manager specifies the path of the XML file.</span></span> <span data-ttu-id="876aa-131">자세한 내용은 [File Connection Manager](../connection-manager/file-connection-manager.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="876aa-131">For more information, see [File Connection Manager](../connection-manager/file-connection-manager.md).</span></span>  
  
 <span data-ttu-id="876aa-132">XML 태스크는 작업 결과를 변수나 파일로 저장하도록 구성될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="876aa-132">The XML task can be configured to save the result of the operation to a variable or to a file.</span></span> <span data-ttu-id="876aa-133">파일로 저장하는 경우 XML 태스크는 파일 연결 관리자를 사용하여 파일에 액세스합니다.</span><span class="sxs-lookup"><span data-stu-id="876aa-133">If saving to a file, the XML task uses a File connection manager to access the file.</span></span> <span data-ttu-id="876aa-134">또한 비교 작업으로 생성된 Diffgram의 결과를 파일 및 변수로 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="876aa-134">You can also save the results of the Diffgram generated by the Diff operation to files and variables.</span></span>  
  
## <a name="predefined-xml-operations"></a><span data-ttu-id="876aa-135">미리 정의된 XML 작업</span><span class="sxs-lookup"><span data-stu-id="876aa-135">Predefined XML Operations</span></span>  
 <span data-ttu-id="876aa-136">XML 태스크에는 XML 문서 작업을 위해 미리 정의된 일련의 작업이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="876aa-136">The XML task includes a predefined set of operations for working with XML documents.</span></span> <span data-ttu-id="876aa-137">다음 표에서는 이러한 작업을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="876aa-137">The following table describes these operations.</span></span>  
  
|<span data-ttu-id="876aa-138">작업(Operation)</span><span class="sxs-lookup"><span data-stu-id="876aa-138">Operation</span></span>|<span data-ttu-id="876aa-139">Description</span><span class="sxs-lookup"><span data-stu-id="876aa-139">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="876aa-140">Diff</span><span class="sxs-lookup"><span data-stu-id="876aa-140">Diff</span></span>|<span data-ttu-id="876aa-141">두 개의 XML 문서를 비교합니다.</span><span class="sxs-lookup"><span data-stu-id="876aa-141">Compares two XML documents.</span></span> <span data-ttu-id="876aa-142">원본 XML 문서를 기본 문서로 사용하는 비교 작업은 원본 XML 문서를 보조 XML 문서와 비교하고, 차이점을 검색하고, 해당 차이점을 XML Diffgram 문서에 기록합니다.</span><span class="sxs-lookup"><span data-stu-id="876aa-142">Using the source XML document as the base document, the Diff operation compares it to a second XML document, detects their differences, and writes the differences to an XML Diffgram document.</span></span> <span data-ttu-id="876aa-143">이 작업에는 비교를 사용자 지정하기 위한 속성이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="876aa-143">This operation includes properties for customizing the comparison.</span></span>|  
|<span data-ttu-id="876aa-144">병합</span><span class="sxs-lookup"><span data-stu-id="876aa-144">Merge</span></span>|<span data-ttu-id="876aa-145">두 개의 XML 문서를 병합합니다.</span><span class="sxs-lookup"><span data-stu-id="876aa-145">Merges two XML documents.</span></span> <span data-ttu-id="876aa-146">원본 XML 문서를 기본 문서로 사용하는 병합 작업은 보조 문서의 내용을 기본 문서에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="876aa-146">Using the source XML document as the base document, the Merge operation adds the content of a second document into the base document.</span></span> <span data-ttu-id="876aa-147">이 작업에서는 기본 문서 내의 병합 위치를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="876aa-147">The operation can specify a merge location within the base document.</span></span>|  
|<span data-ttu-id="876aa-148">패치</span><span class="sxs-lookup"><span data-stu-id="876aa-148">Patch</span></span>|<span data-ttu-id="876aa-149">Diffgram 문서로 불리는 비교 작업의 출력을 XML 문서에 적용하여 Diffgram 문서 내용이 포함된 새로운 상위 문서를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="876aa-149">Applies the output from the Diff operation, called a Diffgram document, to an XML document, to create a new parent document that includes content from the Diffgram document.</span></span>|  
|<span data-ttu-id="876aa-150">유효성 검사</span><span class="sxs-lookup"><span data-stu-id="876aa-150">Validate</span></span>|<span data-ttu-id="876aa-151">DTD(문서 유형 정의) 또는 XSD(XML 스키마 정의) 스키마와 비교하여 XML 문서의 유효성을 검사합니다.</span><span class="sxs-lookup"><span data-stu-id="876aa-151">Validates the XML document against a Document Type Definition (DTD) or XML Schema definition (XSD) schema.</span></span>|  
|<span data-ttu-id="876aa-152">XPath</span><span class="sxs-lookup"><span data-stu-id="876aa-152">XPath</span></span>|<span data-ttu-id="876aa-153">XPath 쿼리 및 계산을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="876aa-153">Performs XPath queries and evaluations.</span></span>|  
|<span data-ttu-id="876aa-154">XSLT</span><span class="sxs-lookup"><span data-stu-id="876aa-154">XSLT</span></span>|<span data-ttu-id="876aa-155">XML 문서에 대해 XSL 변환을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="876aa-155">Performs XSL transformations on XML documents.</span></span>|  
  
### <a name="diff-operation"></a><span data-ttu-id="876aa-156">비교 작업</span><span class="sxs-lookup"><span data-stu-id="876aa-156">Diff Operation</span></span>  
 <span data-ttu-id="876aa-157">비교 작업의 속도 또는 정확도가 필요한지 여부에 따라 다른 비교 알고리즘을 사용하도록 비교 작업을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="876aa-157">The Diff operation can be configured to use a different comparison algorithm depending on whether the comparison must be fast or precise.</span></span> <span data-ttu-id="876aa-158">또한 비교되는 문서의 크기를 기준으로 빠른 비교나 정확한 비교를 자동으로 선택하도록 작업을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="876aa-158">The operation can also be configured to automatically select a fast or precise comparison based on the size of the documents being compared.</span></span>  
  
 <span data-ttu-id="876aa-159">비교 작업에는 XML 비교를 사용자 지정하는 일련의 옵션이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="876aa-159">The Diff operation includes a set of options that customize the XML comparison.</span></span> <span data-ttu-id="876aa-160">다음 표에서는 옵션에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="876aa-160">The following table describes the options.</span></span>  
  
|<span data-ttu-id="876aa-161">옵션</span><span class="sxs-lookup"><span data-stu-id="876aa-161">Option</span></span>|<span data-ttu-id="876aa-162">Description</span><span class="sxs-lookup"><span data-stu-id="876aa-162">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="876aa-163">**IgnoreComments**</span><span class="sxs-lookup"><span data-stu-id="876aa-163">**IgnoreComments**</span></span>|<span data-ttu-id="876aa-164">열 노드가 비교되는지 여부를 지정하는 값입니다.</span><span class="sxs-lookup"><span data-stu-id="876aa-164">A value that specifies whether comment nodes are compared.</span></span>|  
|<span data-ttu-id="876aa-165">**IgnoreNamespaces**</span><span class="sxs-lookup"><span data-stu-id="876aa-165">**IgnoreNamespaces**</span></span>|<span data-ttu-id="876aa-166">요소의 네임스페이스 URI(Uniform Resource Identifier)와 해당 특성 이름이 비교되는지 여부를 지정하는 값입니다.</span><span class="sxs-lookup"><span data-stu-id="876aa-166">A value that specifies whether the namespace uniform resource identifier (URI) of an element and its attribute names are compared.</span></span> <span data-ttu-id="876aa-167">이 옵션을 `true`로 설정하면 로컬 이름이 같지만 네임스페이스가 다른 두 요소는 동일한 것으로 간주됩니다.</span><span class="sxs-lookup"><span data-stu-id="876aa-167">If this option is set to `true`, two elements that have the same local name but a different namespace are considered to be identical.</span></span>|  
|<span data-ttu-id="876aa-168">**IgnorePrefixes**</span><span class="sxs-lookup"><span data-stu-id="876aa-168">**IgnorePrefixes**</span></span>|<span data-ttu-id="876aa-169">요소의 접두사 및 특성 이름이 비교되는지 여부를 지정하는 값입니다.</span><span class="sxs-lookup"><span data-stu-id="876aa-169">A value that specifies whether prefixes of element and attribute names are compared.</span></span> <span data-ttu-id="876aa-170">이 옵션을 `true,`로 설정하면 로컬 이름이 같지만 네임스페이스 URI가 다른 두 요소는 동일한 것으로 간주됩니다.</span><span class="sxs-lookup"><span data-stu-id="876aa-170">If this option is set to `true,` two elements that have the same local name but a different namespace URI and prefix are considered identical.</span></span>|  
|<span data-ttu-id="876aa-171">**IgnoreXMLDeclaration**</span><span class="sxs-lookup"><span data-stu-id="876aa-171">**IgnoreXMLDeclaration**</span></span>|<span data-ttu-id="876aa-172">XML 선언이 비교되는지 여부를 지정하는 값입니다.</span><span class="sxs-lookup"><span data-stu-id="876aa-172">A value that specifies whether the XML declarations are compared.</span></span>|  
|<span data-ttu-id="876aa-173">**IgnoreOrderOfChildElements**</span><span class="sxs-lookup"><span data-stu-id="876aa-173">**IgnoreOrderOfChildElements**</span></span>|<span data-ttu-id="876aa-174">자식 요소의 순서가 비교되는지 여부를 지정하는 값입니다.</span><span class="sxs-lookup"><span data-stu-id="876aa-174">A value that specifies whether the order of child elements is compared.</span></span> <span data-ttu-id="876aa-175">이 옵션을 `true`로 설정하면 형제 목록에서 위치만 다른 자식 요소는 동일한 것으로 간주됩니다.</span><span class="sxs-lookup"><span data-stu-id="876aa-175">If this option is set to `true`, child elements that differ only in their position in a list of siblings are considered to be identical.</span></span>|  
|<span data-ttu-id="876aa-176">**IgnoreWhiteSpaces**</span><span class="sxs-lookup"><span data-stu-id="876aa-176">**IgnoreWhiteSpaces**</span></span>|<span data-ttu-id="876aa-177">공백이 비교되는지 여부를 지정하는 값입니다.</span><span class="sxs-lookup"><span data-stu-id="876aa-177">A value that specifies whether white spaces are compared.</span></span>|  
|<span data-ttu-id="876aa-178">**IgnoreProcessingInstructions**</span><span class="sxs-lookup"><span data-stu-id="876aa-178">**IgnoreProcessingInstructions**</span></span>|<span data-ttu-id="876aa-179">처리 명령이 비교되는지 여부를 지정하는 값입니다.</span><span class="sxs-lookup"><span data-stu-id="876aa-179">A value that specifies whether processing instructions are compared.</span></span>|  
|<span data-ttu-id="876aa-180">**IgnoreDTD**</span><span class="sxs-lookup"><span data-stu-id="876aa-180">**IgnoreDTD**</span></span>|<span data-ttu-id="876aa-181">DTD가 무시되는지 여부를 지정하는 값입니다.</span><span class="sxs-lookup"><span data-stu-id="876aa-181">A value that specifies whether the DTD is ignored.</span></span>|  
  
### <a name="merge-operation"></a><span data-ttu-id="876aa-182">병합 작업</span><span class="sxs-lookup"><span data-stu-id="876aa-182">Merge Operation</span></span>  
 <span data-ttu-id="876aa-183">XPath 문을 사용하여 원본 문서의 병합 위치를 식별하는 경우 이 문은 단일 노드를 반환해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="876aa-183">When you use an XPath statement to identify the merge location in the source document, this statement is expected to return a single node.</span></span> <span data-ttu-id="876aa-184">여러 노드가 반환되는 경우에는 첫 번째 노드만 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="876aa-184">If the statement returns multiple nodes, only the first node is used.</span></span> <span data-ttu-id="876aa-185">두 번째 문서의 내용은 XPath 쿼리에서 반환하는 첫 번째 노드 아래에 병합됩니다.</span><span class="sxs-lookup"><span data-stu-id="876aa-185">The contents of the second document are merged under the first node that the XPath query returns.</span></span>  
  
### <a name="xpath-operation"></a><span data-ttu-id="876aa-186">XPath 작업</span><span class="sxs-lookup"><span data-stu-id="876aa-186">XPath Operation</span></span>  
 <span data-ttu-id="876aa-187">XPath 작업은 다른 유형의 XPath 기능을 사용하도록 구성될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="876aa-187">The XPath operation can be configured to use different types of XPath functionality.</span></span>  
  
-   <span data-ttu-id="876aa-188">sum()과 같은 XPath 함수를 구현하려면 **Evaluation** 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="876aa-188">Select the **Evaluation** option to implement XPath functions such as sum().</span></span>  
  
-   <span data-ttu-id="876aa-189">선택된 노드를 XML 조각으로 반환하려면 **Node list** 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="876aa-189">Select the **Node list** option to return the selected nodes as an XML fragment.</span></span>  
  
-   <span data-ttu-id="876aa-190">선택한 모든 노드의 내부 텍스트 값을 연결된 문자열로 반환하려면 **Values** 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="876aa-190">Select the **Values** option to return the inner text value of all the selected nodes, concatenated into a string.</span></span>  
  
### <a name="validation-operation"></a><span data-ttu-id="876aa-191">유효성 검사 작업</span><span class="sxs-lookup"><span data-stu-id="876aa-191">Validation Operation</span></span>  
 <span data-ttu-id="876aa-192">유효성 검사 작업은 DTD(문서 유형 정의) 또는 XSD(XML 스키마 정의) 스키마를 사용하도록 구성될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="876aa-192">The Validation operation can be configured to use either a Document Type Definition (DTD) or XML Schema definition (XSD) schema.</span></span>  
  
 <span data-ttu-id="876aa-193">`ValidationDetails`를 사용하도록 설정하여 자세한 오류 출력을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="876aa-193">Enable `ValidationDetails` to get detailed error output.</span></span> <span data-ttu-id="876aa-194">자세한 내용은 [Validate XML with the XML Task](xml-task.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="876aa-194">For more info, see [Validate XML with the XML Task](xml-task.md).</span></span>  
  
## <a name="xml-document-encoding"></a><span data-ttu-id="876aa-195">XML 문서 인코딩</span><span class="sxs-lookup"><span data-stu-id="876aa-195">XML Document Encoding</span></span>  
 <span data-ttu-id="876aa-196">XML 태스크는 유니코드 문서의 병합만 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="876aa-196">The XML task supports merging of Unicode documents only.</span></span> <span data-ttu-id="876aa-197">즉, 태스크에서 유니코드 인코딩이 포함된 문서로만 병합 작업을 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="876aa-197">This means the task can apply the Merge operation only to documents that have a Unicode encoding.</span></span> <span data-ttu-id="876aa-198">다른 인코딩을 사용하면 XML 태스크가 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="876aa-198">Use of other encodings will cause the XML task to fail.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="876aa-199">비교 및 패치 작업에는 두 번째 피연산자 XML 데이터의 XML 선언을 무시하는 옵션이 포함되어 있어서 다른 인코딩이 포함된 문서를 해당 작업에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="876aa-199">The Diff and Patch operations include an option to ignore the XML declaration in the second-operand XML data, making it possible to use documents that have other encodings in these operations.</span></span>  
  
 <span data-ttu-id="876aa-200">XML 문서를 사용할 수 있는지 여부를 확인하려면 XML 선언을 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="876aa-200">To verify that the XML document can be used, review the XML declaration.</span></span> <span data-ttu-id="876aa-201">선언에는 8비트 유니코드 인코딩을 나타내는 UTF-8이 명시적으로 지정되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="876aa-201">The declaration must explicitly specify UTF-8, which indicates 8-bit Unicode encoding.</span></span>  
  
 <span data-ttu-id="876aa-202">다음 태그는 유니코드 8비트 인코딩을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="876aa-202">The following tag shows the Unicode 8-bit encoding.</span></span>  
  
 `<?xml version="1.0" encoding="UTF-8"?>`  
  
## <a name="custom-logging-messages-available-on-the-xml-task"></a><span data-ttu-id="876aa-203">XML 태스크에 사용할 수 있는 사용자 지정 로깅 메시지</span><span class="sxs-lookup"><span data-stu-id="876aa-203">Custom Logging Messages Available on the XML Task</span></span>  
 <span data-ttu-id="876aa-204">다음 표에서는 XML 태스크에 대한 사용자 지정 로그 항목을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="876aa-204">The following table describes the custom log entry for the XML task.</span></span> <span data-ttu-id="876aa-205">자세한 내용은 [Integration Services&#40;SSIS&#41; 로깅](../performance/integration-services-ssis-logging.md) 및 [로깅할 메시지 사용자 지정](../custom-messages-for-logging.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="876aa-205">For more information, see [Integration Services &#40;SSIS&#41; Logging](../performance/integration-services-ssis-logging.md) and [Custom Messages for Logging](../custom-messages-for-logging.md).</span></span>  
  
|<span data-ttu-id="876aa-206">로그 항목</span><span class="sxs-lookup"><span data-stu-id="876aa-206">Log entry</span></span>|<span data-ttu-id="876aa-207">Description</span><span class="sxs-lookup"><span data-stu-id="876aa-207">Description</span></span>|  
|---------------|-----------------|  
|`XMLOperation`|<span data-ttu-id="876aa-208">태스크에서 수행한 작업에 대한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="876aa-208">Provides information about the operation that the task performs</span></span>|  
  
## <a name="configuration-of-the-xml-task"></a><span data-ttu-id="876aa-209">XML 태스크 구성</span><span class="sxs-lookup"><span data-stu-id="876aa-209">Configuration of the XML Task</span></span>  
 <span data-ttu-id="876aa-210">[!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너를 사용하거나 프로그래밍 방식으로 속성을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="876aa-210">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="876aa-211">[!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너에서 설정할 수 있는 속성에 대한 자세한 내용을 보려면 다음 항목 중 하나를 클릭하십시오.</span><span class="sxs-lookup"><span data-stu-id="876aa-211">For more information about the properties that you can set in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="876aa-212">XML 태스크 편집기&#40;일반 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="876aa-212">XML Task Editor &#40;General Page&#41;</span></span>](../general-page-of-integration-services-designers-options.md)  
  
-   [<span data-ttu-id="876aa-213">XML 태스크를 사용하여 XML 유효성 검사</span><span class="sxs-lookup"><span data-stu-id="876aa-213">Validate XML with the XML Task</span></span>](xml-task.md)  
  
-   [<span data-ttu-id="876aa-214">식 페이지</span><span class="sxs-lookup"><span data-stu-id="876aa-214">Expressions Page</span></span>](../expressions/expressions-page.md)  
  
 <span data-ttu-id="876aa-215">[!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너에서 속성을 설정하는 방법을 보려면 다음 항목을 클릭하십시오.</span><span class="sxs-lookup"><span data-stu-id="876aa-215">For more information about how to set properties in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click the following topic:</span></span>  
  
-   [<span data-ttu-id="876aa-216">태스크 또는 컨테이너의 속성 설정</span><span class="sxs-lookup"><span data-stu-id="876aa-216">Set the Properties of a Task or Container</span></span>](../set-the-properties-of-a-task-or-container.md)  
  
## <a name="programmatic-configuration-of-the-xml-task"></a><span data-ttu-id="876aa-217">XML 태스크의 프로그래밍 방식 구성</span><span class="sxs-lookup"><span data-stu-id="876aa-217">Programmatic Configuration of the XML Task</span></span>  
 <span data-ttu-id="876aa-218">이러한 속성을 프로그래밍 방식으로 설정하는 방법을 보려면 다음 항목을 클릭하십시오.</span><span class="sxs-lookup"><span data-stu-id="876aa-218">For more information about programmatically setting these properties, click the following topic:</span></span>  
  
-   <xref:Microsoft.SqlServer.Dts.Tasks.XMLTask.XMLTask>  
  
## <a name="related-tasks"></a><span data-ttu-id="876aa-219">관련 작업</span><span class="sxs-lookup"><span data-stu-id="876aa-219">Related Tasks</span></span>  
 [<span data-ttu-id="876aa-220">태스크 또는 컨테이너의 속성 설정</span><span class="sxs-lookup"><span data-stu-id="876aa-220">Set the Properties of a Task or Container</span></span>](../set-the-properties-of-a-task-or-container.md)  
  
## <a name="related-content"></a><span data-ttu-id="876aa-221">관련 내용</span><span class="sxs-lookup"><span data-stu-id="876aa-221">Related Content</span></span>  
  
-   <span data-ttu-id="876aa-222">agilebi.com의 블로그 항목 - [XML 대상 스크립트 구성 요소](http://agilebi.com/jwelch/2007/06/02/xml-destination-script-component/)</span><span class="sxs-lookup"><span data-stu-id="876aa-222">Blog entry, [XML Destination Script Component](http://agilebi.com/jwelch/2007/06/02/xml-destination-script-component/), on agilebi.com</span></span>  
  
-   <span data-ttu-id="876aa-223">www.codeplex.com 의 CodePlex 예제 - [프로세스 XML 데이터 패키지 예제](https://msftisprodsamples.codeplex.com/wikipage?title=SS2008!Process%20XML%20Data%20Package%20Sample&version=10&ProjectName=msftisprodsamples)</span><span class="sxs-lookup"><span data-stu-id="876aa-223">CodePlex sample, [Process XML Data Package Sample](https://msftisprodsamples.codeplex.com/wikipage?title=SS2008!Process%20XML%20Data%20Package%20Sample&version=10&ProjectName=msftisprodsamples), on www.codeplex.com</span></span>  
  
