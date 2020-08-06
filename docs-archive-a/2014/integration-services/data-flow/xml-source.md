---
title: XML 원본 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.xmlsource.f1
helpviewer_keywords:
- sources [Integration Services], XML
- XML source [Integration Services]
- XML Source Editor
ms.assetid: 68c27ea5-e93d-4e26-bfb2-d967ca0a5282
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d13a1bf01729932eaa6b232ac7839d2e3001f5fe
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659537"
---
# <a name="xml-source"></a><span data-ttu-id="13707-102">XML 원본</span><span class="sxs-lookup"><span data-stu-id="13707-102">XML Source</span></span>
  <span data-ttu-id="13707-103">XML 원본은 XML 데이터 파일을 읽고 원본 출력의 열을 해당 데이터로 채웁니다.</span><span class="sxs-lookup"><span data-stu-id="13707-103">The XML source reads an XML data file and populates the columns in the source output with the data.</span></span>  
  
 <span data-ttu-id="13707-104">XML 파일의 데이터에 계층 관계가 포함되어 있는 경우가 많습니다.</span><span class="sxs-lookup"><span data-stu-id="13707-104">The data in XML files frequently includes hierarchical relationships.</span></span> <span data-ttu-id="13707-105">예를 들어 XML 데이터 파일은 카탈로그 및 카탈로그의 항목을 나타낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="13707-105">For example, an XML data file can represent catalogs and items in catalogs.</span></span> <span data-ttu-id="13707-106">데이터가 데이터 흐름을 시작할 수 있으려면 먼저 XML 데이터 파일에 있는 각 요소의 관계를 결정하고 파일의 각 요소에 대해 출력을 생성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="13707-106">Before the data can enter the data flow, the relationship of the elements in XML data file must be determined, and an output must be generated for each element in the file.</span></span>  
  
## <a name="schemas"></a><span data-ttu-id="13707-107">스키마</span><span class="sxs-lookup"><span data-stu-id="13707-107">Schemas</span></span>  
 <span data-ttu-id="13707-108">XML 원본은 스키마를 사용하여 XML 데이터를 해석합니다.</span><span class="sxs-lookup"><span data-stu-id="13707-108">The XML source uses a schema to interpret the XML data.</span></span> <span data-ttu-id="13707-109">XML 원본은 XML 데이터를 테이블 형식으로 변환하는 인라인 스키마 또는 XML 스키마 정의(XSD) 파일 사용을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="13707-109">The XML source supports use of a XML Schema Definition (XSD) file or inline schemas to translate the XML data into a tabular format.</span></span> <span data-ttu-id="13707-110">**XML 원본 편집기** 대화 상자를 사용하여 XML 원본을 구성하면 사용자 인터페이스가 지정한 XML 데이터 파일에서 XSD를 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="13707-110">If you configure the XML source by using the **XML Source Editor** dialog box, the user interface can generate an XSD from the specified XML data file.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="13707-111">DTD는 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="13707-111">DTDs are not supported.</span></span>  
  
 <span data-ttu-id="13707-112">스키마는 하나의 네임스페이스만 지원할 수 있으며 스키마 컬렉션을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="13707-112">The schemas can support a single namespace only; they do not support schema collections.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="13707-113">XML 원본은 XSD와 비교하여 XML 파일 데이터의 유효성을 검사하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="13707-113">The XML source does not validate the data in the XML file against the XSD.</span></span>  
  
## <a name="xml-source-editor"></a><span data-ttu-id="13707-114">XML 원본 편집기</span><span class="sxs-lookup"><span data-stu-id="13707-114">XML Source Editor</span></span>  
 <span data-ttu-id="13707-115">XML 파일의 데이터에 계층 관계가 포함되어 있는 경우가 많습니다.</span><span class="sxs-lookup"><span data-stu-id="13707-115">The data in the XML files frequently includes hierarchical relationships.</span></span> <span data-ttu-id="13707-116">**XML 원본 편집기** 대화 상자는 지정한 스키마를 사용하여 XML 원본 출력을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="13707-116">The **XML Source Editor** dialog box uses the specified schema to generate the XML source outputs.</span></span> <span data-ttu-id="13707-117">XSD 파일을 지정하거나 인라인 스키마를 사용하거나 지정한 XML 데이터 파일에서 XSD를 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="13707-117">You can specify an XSD file, use an inline schema, or generate an XSD from the specified XML data file.</span></span> <span data-ttu-id="13707-118">디자인 타임에 해당 스키마를 사용할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="13707-118">The schema must be available at design time.</span></span>  
  
 <span data-ttu-id="13707-119">XML 원본은 XML 파일의 다른 요소가 포함된 모든 요소에 대해 출력을 만들어 XML 데이터에서 테이블 구조를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="13707-119">The XML source generates tabular structures from the XML data by creating an output for every element that contains other elements in the XML files.</span></span> <span data-ttu-id="13707-120">예를 들어 XML 데이터가 카탈로그 및 카탈로그의 항목을 나타내는 경우 XML 원본은 카탈로그에 대한 출력과 카탈로그에 포함된 각 항목 유형에 대한 출력을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="13707-120">For example, if the XML data represents catalogs and items in catalogs, the XML source creates an output for catalogs and an output for each type of item that the catalogs contain.</span></span> <span data-ttu-id="13707-121">각 항목의 출력에는 해당 항목의 속성에 대한 출력 열이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="13707-121">The output of each item will contain output columns for the attributes of that item.</span></span>  
  
 <span data-ttu-id="13707-122">출력에서 데이터 계층 관계에 대한 정보를 제공하기 위해 XML 원본은 각 자식 요소의 부모 요소를 식별하는 열을 출력에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="13707-122">To provide information about the hierarchical relationship of the data in the outputs, the XML source adds a column in the outputs that identifies the parent element for each child element.</span></span> <span data-ttu-id="13707-123">여러 유형의 항목이 포함된 카탈로그를 예로 들면 각 항목은 해당 항목이 속해 있는 카탈로그를 식별하는 열 값을 갖습니다.</span><span class="sxs-lookup"><span data-stu-id="13707-123">Using the example of catalogs with different types of items, each item would have a column value that identifies the catalog to which it belongs.</span></span>  
  
 <span data-ttu-id="13707-124">XML 원본은 모든 요소에 대해 출력을 만들지만 모든 출력을 사용할 필요는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="13707-124">The XML source creates an output for every element, but it is not required that you use all the outputs.</span></span> <span data-ttu-id="13707-125">사용하지 않을 출력을 삭제하거나 다운스트림 구성 요소에 연결하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="13707-125">You can delete any output that you do not want to use, or just not connect it to a downstream component.</span></span>  
  
 <span data-ttu-id="13707-126">또한 XML 원본은 출력 이름을 생성하여 이름이 명확하게 구분되게 합니다.</span><span class="sxs-lookup"><span data-stu-id="13707-126">The XML source also generates the output names, to ensure that the names are unambiguous.</span></span> <span data-ttu-id="13707-127">이러한 이름이 너무 길면 출력을 식별하는 데 도움이 되지 않을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="13707-127">These names may be long and may not identify the outputs in a way that is useful to you.</span></span> <span data-ttu-id="13707-128">고유한 이름을 지정한다면 출력 이름을 바꿀 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="13707-128">You can rename the outputs, as long as their names remain unique.</span></span> <span data-ttu-id="13707-129">출력 열의 길이와 데이터 형식도 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="13707-129">You can also modify the data type and the length of output columns.</span></span>  
  
 <span data-ttu-id="13707-130">XML 원본은 모든 출력에 대해 오류 출력을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="13707-130">For every output, the XML source adds an error output.</span></span> <span data-ttu-id="13707-131">기본적으로 오류 출력의 열은 길이가 255인 유니코드 문자열 데이터 형식(DT_WSTR)이지만 데이터 형식과 길이를 수정하여 오류 출력의 열을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="13707-131">By default the columns in error outputs have Unicode string data type (DT_WSTR) with a length of 255, but you can configure the columns in the error outputs by modifying their data type and length.</span></span>  
  
 <span data-ttu-id="13707-132">XSD에 없는 요소가 XML 데이터 파일에 포함되어 있으면 해당 요소는 무시되며 출력이 생성되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="13707-132">If the XML data file contains elements that are not in the XSD, these elements are ignored and no output is generated for them.</span></span> <span data-ttu-id="13707-133">반면 XSD에 표시된 요소가 XML 데이터 파일에 없을 경우 Null 값을 가진 열이 출력에 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="13707-133">On the other hand, if the XML data file is missing elements that are represented in the XSD, the output will contain columns with null values.</span></span>  
  
 <span data-ttu-id="13707-134">XML 데이터 파일에서 데이터를 추출하면 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 데이터 형식으로 변환됩니다.</span><span class="sxs-lookup"><span data-stu-id="13707-134">When the data is extracted from the XML data file, it is converted to an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] data type.</span></span> <span data-ttu-id="13707-135">그러나 XML 원본은 DT_TIME2 또는 DT_DBTIMESTAMP2 데이터 형식을 지원하지 않기 때문에 XML 데이터를 이러한 데이터 형식으로 변환할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="13707-135">However, the XML source cannot convert the XML data to the DT_TIME2 or DT_DBTIMESTAMP2 data types because the source does not support these data types.</span></span> <span data-ttu-id="13707-136">자세한 내용은 [Integration Services Data Types](integration-services-data-types.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="13707-136">For more information, see [Integration Services Data Types](integration-services-data-types.md).</span></span>  
  
 <span data-ttu-id="13707-137">XSD 또는 인라인 스키마에서 요소의 데이터 형식을 지정할 수도 있지만 그렇지 않을 경우 **XML 원본 편집기** 대화 상자는 요소가 포함된 출력 열에 유니코드 문자열 데이터 형식(DT_WSTR)을 할당하고 열 길이를 255자로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="13707-137">The XSD or inline schema may specify the data type for elements, but if it does not, the **XML Source Editor** dialog box assigns the Unicode string data type (DT_WSTR) to the column in the output that contains the element, and sets the column length to 255 characters.</span></span>  
  
 <span data-ttu-id="13707-138">스키마에서 요소의 최대 길이를 지정하는 경우 출력 열의 길이는 이 값으로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="13707-138">If the schema specifies the maximum length of an element, the length of output column is set to this value.</span></span> <span data-ttu-id="13707-139">요소가 변환되는 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 데이터 형식에서 지원되는 길이보다 최대 길이가 큰 경우 해당 데이터 형식의 최대 길이로 데이터가 잘립니다.</span><span class="sxs-lookup"><span data-stu-id="13707-139">If the maximum length is greater than the length supported by the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] data type to which the element is converted, then the data is truncated to the maximum length of the data type.</span></span> <span data-ttu-id="13707-140">예를 들어 문자열의 길이가 5,000자인 경우 DT_WSTR 데이터 형식의 최대 길이는 4,000자이므로 4,000자로 잘리며 BYTE 데이터는 DT_BYTES 데이터 형식의 최대 길이인 8,000자로 잘립니다.</span><span class="sxs-lookup"><span data-stu-id="13707-140">For example, if a string has a length of 5000, it is truncated to 4000 characters because the maximum length of the DT_WSTR data type is 4000 characters; likewise, byte data is truncated to 8000 characters, the maximum length of the DT_BYTES data type.</span></span> <span data-ttu-id="13707-141">스키마에서 최대 길이를 지정하지 않는 경우 두 데이터 형식의 열 기본 길이는 255자로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="13707-141">If the schema specifies no maximum length, the default length of columns with either data type is set to 255.</span></span> <span data-ttu-id="13707-142">XML 원본에서의 데이터 잘림은 다른 데이터 흐름 구성 요소에서의 잘림과 동일하게 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="13707-142">Data truncation in the XML source is handled the same way as truncation in other data flow components.</span></span> <span data-ttu-id="13707-143">자세한 내용은 [데이터 오류 처리](error-handling-in-data.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="13707-143">For more information, see [Error Handling in Data](error-handling-in-data.md).</span></span>  
  
 <span data-ttu-id="13707-144">데이터 형식과 열 길이는 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="13707-144">You can modify the data type and the column length.</span></span> <span data-ttu-id="13707-145">자세한 내용은 [Integration Services Data Types](integration-services-data-types.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="13707-145">For more information, see [Integration Services Data Types](integration-services-data-types.md).</span></span>  
  
## <a name="configuration-of-the-xml-source"></a><span data-ttu-id="13707-146">XML 원본 구성</span><span class="sxs-lookup"><span data-stu-id="13707-146">Configuration of the XML Source</span></span>  
 <span data-ttu-id="13707-147">XML 원본은 3가지 데이터 액세스 모드를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="13707-147">The XML source supports three different data access modes.</span></span> <span data-ttu-id="13707-148">XML 데이터 파일의 파일 위치, 이 파일 위치가 포함된 변수 또는 XML 데이터가 포함된 변수를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="13707-148">You can specify the file location of the XML data file, the variable that contains the file location, or the variable that contains the XML data.</span></span>  
  
 <span data-ttu-id="13707-149">XML 원본은 패키지 로드 시 속성 식을 사용하여 업데이트할 수 있는 `XMLData` 및 `XMLSchemaDefinition` 사용자 지정 속성을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="13707-149">The XML source includes the `XMLData` and `XMLSchemaDefinition` custom properties that can be updated by property expressions when the package is loaded.</span></span> <span data-ttu-id="13707-150">자세한 내용은 [Integration Services&#40;SSIS&#41; 식](../expressions/integration-services-ssis-expressions.md), [패키지에서 속성 식 사용](../expressions/use-property-expressions-in-packages.md) 및 [XML 원본 사용자 지정 속성](xml-source-custom-properties.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="13707-150">For more information, see [Integration Services &#40;SSIS&#41; Expressions](../expressions/integration-services-ssis-expressions.md), [Use Property Expressions in Packages](../expressions/use-property-expressions-in-packages.md), and [XML Source Custom Properties](xml-source-custom-properties.md).</span></span>  
  
 <span data-ttu-id="13707-151">XML 원본은 여러 개의 일반 출력과 여러 개의 오류 출력을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="13707-151">The XML source supports multiple regular outputs and multiple error outputs.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="13707-152">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]에는 XML 원본 구성을 위한 **XML 원본 편집기** 대화 상자가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="13707-152">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] includes the **XML Source Edito**r dialog box for configuring the XML source.</span></span> <span data-ttu-id="13707-153">이 대화 상자는 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="13707-153">This dialog box is available in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer.</span></span>  
  
 <span data-ttu-id="13707-154">[!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너를 사용하거나 프로그래밍 방식으로 속성을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="13707-154">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="13707-155">**XML 원본 편집기** 대화 상자에서 설정할 수 있는 속성에 대한 자세한 내용을 보려면 다음 항목 중 하나를 클릭하십시오.</span><span class="sxs-lookup"><span data-stu-id="13707-155">For more information about the properties that you can set in the **XML Source Editor** dialog box, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="13707-156">XML 원본 편집기&#40;연결 관리자 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="13707-156">XML Source Editor &#40;Connection Manager Page&#41;</span></span>](../xml-source-editor-connection-manager-page.md)  
  
-   [<span data-ttu-id="13707-157">XML 원본 편집기&#40;열 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="13707-157">XML Source Editor &#40;Columns Page&#41;</span></span>](../xml-source-editor-columns-page.md)  
  
-   [<span data-ttu-id="13707-158">XML 원본 편집기&#40;오류 출력 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="13707-158">XML Source Editor &#40;Error Output Page&#41;</span></span>](../xml-source-editor-error-output-page.md)  
  
 <span data-ttu-id="13707-159">**고급 편집기** 대화 상자에는 프로그래밍 방식으로 설정할 수 있는 속성이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="13707-159">The **Advanced Editor** dialog box reflects the properties that can be set programmatically.</span></span> <span data-ttu-id="13707-160">**고급 편집기** 대화 상자를 사용하거나 프로그래밍 방식으로 설정할 수 있는 속성에 대한 자세한 내용을 보려면 다음 항목 중 하나를 클릭하세요.</span><span class="sxs-lookup"><span data-stu-id="13707-160">For more information about the properties that you can set in the **Advanced Editor** dialog box or programmatically, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="13707-161">Common Properties</span><span class="sxs-lookup"><span data-stu-id="13707-161">Common Properties</span></span>](../common-properties.md)  
  
-   [<span data-ttu-id="13707-162">XML 원본 사용자 지정 속성</span><span class="sxs-lookup"><span data-stu-id="13707-162">XML Source Custom Properties</span></span>](xml-source-custom-properties.md)  
  
 <span data-ttu-id="13707-163">속성 설정 방법을 보려면 다음 항목 중 하나를 클릭하십시오.</span><span class="sxs-lookup"><span data-stu-id="13707-163">For more information about how to set the properties, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="13707-164">데이터 흐름 구성 요소의 속성 설정</span><span class="sxs-lookup"><span data-stu-id="13707-164">Set the Properties of a Data Flow Component</span></span>](set-the-properties-of-a-data-flow-component.md)  
  
## <a name="related-tasks"></a><span data-ttu-id="13707-165">관련 작업</span><span class="sxs-lookup"><span data-stu-id="13707-165">Related Tasks</span></span>  
 [<span data-ttu-id="13707-166">XML 원본을 사용하여 데이터 추출</span><span class="sxs-lookup"><span data-stu-id="13707-166">Extract Data by Using the XML Source</span></span>](xml-source.md)  
  
## <a name="related-content"></a><span data-ttu-id="13707-167">관련 내용</span><span class="sxs-lookup"><span data-stu-id="13707-167">Related Content</span></span>  
 <span data-ttu-id="13707-168">[XML 파일을 사용 하 여 SSIS 패키지를 구성](https://www.sqlshack.com/using-xml-file-configure-ssis-package/)하는 기술 문서.</span><span class="sxs-lookup"><span data-stu-id="13707-168">Technical article, [Using an XML file to configure an SSIS package](https://www.sqlshack.com/using-xml-file-configure-ssis-package/).</span></span>  
  
  
