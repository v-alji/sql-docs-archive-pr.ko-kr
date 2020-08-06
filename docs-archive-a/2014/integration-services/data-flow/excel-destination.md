---
title: Excel 대상 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.exceldest.f1
helpviewer_keywords:
- destinations [Integration Services], Excel
- Excel [Integration Services]
ms.assetid: 37c07446-1264-4814-b4f5-9c66d333bb24
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 3e959f14e52fc045cb0cbc2ba0255d20bd0356d6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742444"
---
# <a name="excel-destination"></a><span data-ttu-id="b634e-102">Excel 대상</span><span class="sxs-lookup"><span data-stu-id="b634e-102">Excel Destination</span></span>
  <span data-ttu-id="b634e-103">Excel 대상은 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Excel 통합 문서의 워크시트 또는 범위로 데이터를 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="b634e-103">The Excel destination loads data into worksheets or ranges in [!INCLUDE[msCoName](../../includes/msconame-md.md)] Excel workbooks.</span></span>  
  
## <a name="access-modes"></a><span data-ttu-id="b634e-104">액세스 모드</span><span class="sxs-lookup"><span data-stu-id="b634e-104">Access Modes</span></span>  
 <span data-ttu-id="b634e-105">Excel 대상은 데이터 로드를 위한 3가지 데이터 액세스 모델을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="b634e-105">The Excel destination provides three different data access modes for loading data:</span></span>  
  
-   <span data-ttu-id="b634e-106">테이블 또는 뷰</span><span class="sxs-lookup"><span data-stu-id="b634e-106">A table or view.</span></span>  
  
-   <span data-ttu-id="b634e-107">변수에 지정된 테이블 또는 뷰</span><span class="sxs-lookup"><span data-stu-id="b634e-107">A table or view specified in a variable.</span></span>  
  
-   <span data-ttu-id="b634e-108">SQL 문의 결과</span><span class="sxs-lookup"><span data-stu-id="b634e-108">The results of an SQL statement.</span></span> <span data-ttu-id="b634e-109">쿼리는 매개 변수가 있는 쿼리일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b634e-109">The query can be a parameterized query.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="b634e-110">Excel에서 워크시트나 범위는 테이블 또는 뷰에 해당합니다.</span><span class="sxs-lookup"><span data-stu-id="b634e-110">In Excel, a worksheet or range is the equivalent of a table or view.</span></span> <span data-ttu-id="b634e-111">Excel 원본 및 대상 편집기의 사용 가능한 테이블 목록은 기존 워크시트(Sheet1$와 같이 워크시트 이름에 $ 기호가 붙음)와 명명된 범위(MyRange와 같이 $ 기호가 없음)만 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="b634e-111">The lists of available tables in the Excel Source and Destination editors display only existing worksheets (identified by the $ sign appended to the worksheet name, such as Sheet1$) and named ranges (identified by the absence of the $ sign, such as MyRange).</span></span>  
  
## <a name="usage-considerations"></a><span data-ttu-id="b634e-112">사용 시 고려 사항</span><span class="sxs-lookup"><span data-stu-id="b634e-112">Usage Considerations</span></span>  
 <span data-ttu-id="b634e-113">Excel 연결 관리자는 Jet 4.0용 [!INCLUDE[msCoName](../../includes/msconame-md.md)] OLE DB Provider와 공급자에서 지원하는 Excel ISAM(Indexed Sequential Access Method) 드라이버를 사용하여 Excel 데이터 원본에 연결하고 데이터를 읽고 씁니다.</span><span class="sxs-lookup"><span data-stu-id="b634e-113">The Excel Connection Manager uses the [!INCLUDE[msCoName](../../includes/msconame-md.md)] OLE DB Provider for Jet 4.0 and its supporting Excel ISAM (Indexed Sequential Access Method) driver to connect and read and write data to Excel data sources.</span></span>  
  
 <span data-ttu-id="b634e-114">이 공급자와 드라이버의 동작에 대해 다루는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 기술 자료 문서가 많이 있습니다. 이러한 문서가 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 또는 이전 기능인 데이터 변환 서비스와 반드시 관련된 것은 아니지만 예기치 않은 결과를 발생시킬 수 있는 특정 동작에 대해 살펴보는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="b634e-114">Many existing [!INCLUDE[msCoName](../../includes/msconame-md.md)] Knowledge Base articles document the behavior of this provider and driver, and although these articles are not specific to [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] or its predecessor Data Transformation Services, you may want to know about certain behaviors that can lead to unexpected results.</span></span> <span data-ttu-id="b634e-115">Excel 드라이버의 사용 방법과 동작에 대한 일반 정보는 [Visual Basic 또는 VBA에서 Excel 데이터에 ADO를 사용하는 방법](https://support.microsoft.com/kb/257819)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="b634e-115">For general information on the use and behavior of the Excel driver, see [HOWTO: Use ADO with Excel Data from Visual Basic or VBA](https://support.microsoft.com/kb/257819).</span></span>  
  
 <span data-ttu-id="b634e-116">Excel 드라이버에 포함된 Jet 공급자의 다음 동작은 데이터를 Excel 대상에 저장할 때 예기치 않은 결과를 초래할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b634e-116">The following behaviors of the Jet provider that is included with the Excel driver can lead to unexpected results when saving data to an Excel destination.</span></span>  
  
-   <span data-ttu-id="b634e-117">**텍스트 데이터 저장**.</span><span class="sxs-lookup"><span data-stu-id="b634e-117">**Saving text data**.</span></span> <span data-ttu-id="b634e-118">Excel 드라이버가 텍스트 데이터 값을 Excel 대상에 저장하면 드라이버는 각 셀에서 작은따옴표(')가 있는 텍스트 앞에 오므로 저장된 값이 텍스트 값으로 해석됩니다.</span><span class="sxs-lookup"><span data-stu-id="b634e-118">When the Excel driver saves text data values to an Excel destination, the driver precedes the text in each cell with the single quote character (') to ensure that the saved values will be interpreted as text values.</span></span> <span data-ttu-id="b634e-119">저장된 데이터를 읽거나 처리하는 다른 애플리케이션을 갖고 있거나 개발한 경우 각 텍스트 값을 처리하는 작은따옴표에 대한 특별한 처리 방식을 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b634e-119">If you have or develop other applications that read or process the saved data, you may need to include special handling for the single quote character that precedes each text value.</span></span>  
  
     <span data-ttu-id="b634e-120">작은따옴표가 포함되지 않도록 하는 방법에 대한 내용은 msdn.com의 블로그 게시물 중 [SSIS 패키지에서 Excel 대상 데이터 흐름 구성 요소를 사용하여 Excel로 데이터를 변환할 때 모든 문자열에 추가되는 작은따옴표](https://go.microsoft.com/fwlink/?LinkId=400876)(영문)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b634e-120">For information on how to avoid including the single quote, see this blog post, [Single quote is appended to all strings when data is transformed to excel when using Excel destination data flow component in SSIS package](https://go.microsoft.com/fwlink/?LinkId=400876), on msdn.com.</span></span>  
  
-   <span data-ttu-id="b634e-121">**메모(ntext) 데이터 저장**.</span><span class="sxs-lookup"><span data-stu-id="b634e-121">**Saving memo (ntext) da**ta.</span></span> <span data-ttu-id="b634e-122">255자보다 긴 문자열을 Excel 열에 저장하려면 드라이버에서 대상 열의 데이터 형식을 **string** 이 아닌 **memo**로 인식해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b634e-122">Before you can successfully save strings longer than 255 characters to an Excel column, the driver must recognize the data type of the destination column as **memo** and not **string**.</span></span> <span data-ttu-id="b634e-123">대상 테이블에 이미 데이터 행이 포함된 경우 드라이버에서 샘플링하는 처음 몇 개 행의 메모 열에 값이 255자보다 긴 인스턴스가 하나 이상 들어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b634e-123">If the destination table already contains rows of data, then the first few rows that are sampled by the driver must contain at least one instance of a value longer than 255 characters in the memo column.</span></span> <span data-ttu-id="b634e-124">패키지 디자인 또는 런타임에 대상 테이블을 만드는 경우 CREATE TABLE 문은 메모 열의 데이터 형식으로 LONGTEXT (또는 해당 동의어 중 하나)를 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b634e-124">If the destination table is created during package design or at run time, then the CREATE TABLE statement must use LONGTEXT (or one of its synonyms) as the data type of the memo column.</span></span>  
  
-   <span data-ttu-id="b634e-125">**데이터 형식**.</span><span class="sxs-lookup"><span data-stu-id="b634e-125">**Data types**.</span></span> <span data-ttu-id="b634e-126">Excel 드라이버는 제한된 데이터 형식 집합만 인식합니다.</span><span class="sxs-lookup"><span data-stu-id="b634e-126">The Excel driver recognizes only a limited set of data types.</span></span> <span data-ttu-id="b634e-127">예를 들어 모든 숫자 열은 double(DT_R8)로 해석되고 모든 문자열 열(메모 열 제외)은 255자 유니코드 문자열(DT_WSTR)로 해석됩니다.</span><span class="sxs-lookup"><span data-stu-id="b634e-127">For example, all numeric columns are interpreted as doubles (DT_R8), and all string columns (other than memo columns) are interpreted as 255-character Unicode strings (DT_WSTR).</span></span> [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] <span data-ttu-id="b634e-128">에서는 Excel 데이터 형식을 다음과 같이 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="b634e-128">maps the Excel data types as follows:</span></span>  
  
    -   <span data-ttu-id="b634e-129">숫자    배정밀도 부동 소수점 수(DT_R8)</span><span class="sxs-lookup"><span data-stu-id="b634e-129">Numeric    double-precision float (DT_R8)</span></span>  
  
    -   <span data-ttu-id="b634e-130">통화    currency(DT_CY)</span><span class="sxs-lookup"><span data-stu-id="b634e-130">Currency     currency (DT_CY)</span></span>  
  
    -   <span data-ttu-id="b634e-131">부울    Boolean(DT_BOOL)</span><span class="sxs-lookup"><span data-stu-id="b634e-131">Boolean     Boolean (DT_BOOL)</span></span>  
  
    -   <span data-ttu-id="b634e-132">날짜/시간 `datetime` (DT_DATE)</span><span class="sxs-lookup"><span data-stu-id="b634e-132">Date/time     `datetime` (DT_DATE)</span></span>  
  
    -   <span data-ttu-id="b634e-133">문자열    길이가 255인 유니코드 문자열(DT_WSTR)</span><span class="sxs-lookup"><span data-stu-id="b634e-133">String     Unicode string, length 255 (DT_WSTR)</span></span>  
  
    -   <span data-ttu-id="b634e-134">메모    유니코드 텍스트 스트림(DT_NTEXT)</span><span class="sxs-lookup"><span data-stu-id="b634e-134">Memo     Unicode text stream (DT_NTEXT)</span></span>  
  
-   <span data-ttu-id="b634e-135">**데이터 형식 및 길이 변환**.</span><span class="sxs-lookup"><span data-stu-id="b634e-135">**Data type and length conversions**.</span></span> [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] <span data-ttu-id="b634e-136">에서는 데이터 형식을 암시적으로 변환하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b634e-136">does not implicitly convert data types.</span></span> <span data-ttu-id="b634e-137">따라서 파생 열 변환이나 데이터 변환을 사용하여 Excel 데이터를 비 Excel 대상으로 로드하기 전에 명시적으로 변환하거나 비 Excel 데이터를 Excel 대상으로 로드하기 전에 변환해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b634e-137">As a result, you may need to use the Derived Column or Data Conversion transformations to convert Excel data explicitly before loading it into a non-Excel destination, or to convert non-Excel data before loading it into an Excel destination.</span></span> <span data-ttu-id="b634e-138">이 경우 필요한 변환을 구성해 주는 가져오기 및 내보내기 마법사를 사용하여 초기 패키지를 만들면 유용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b634e-138">In this case, it may be useful to create the initial package by using the Import and Export Wizard, which configures the necessary conversions for you.</span></span> <span data-ttu-id="b634e-139">필요할 수 있는 일부 변환 예는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="b634e-139">Some examples of the conversions that may be required include the following:</span></span>  
  
    -   <span data-ttu-id="b634e-140">유니코드 Excel 문자열 열과 특정 코드 페이지가 있는 비유니코드 문자열 열 간 변환</span><span class="sxs-lookup"><span data-stu-id="b634e-140">Conversion between Unicode Excel string columns and non-Unicode string columns with specific codepages.</span></span>  
  
    -   <span data-ttu-id="b634e-141">255자 Excel 문자열 열과 길이가 다른 문자열 열 간 변환</span><span class="sxs-lookup"><span data-stu-id="b634e-141">Conversion between 255-character Excel string columns and string columns of different lengths.</span></span>  
  
    -   <span data-ttu-id="b634e-142">배정밀도 Excel 숫자 열과 다른 유형의 숫자 열 간 변환</span><span class="sxs-lookup"><span data-stu-id="b634e-142">Conversion between double-precision Excel numeric columns and numeric columns of other types.</span></span>  
  
## <a name="configuration-of-the-excel-destination"></a><span data-ttu-id="b634e-143">Excel 집합 대상 구성</span><span class="sxs-lookup"><span data-stu-id="b634e-143">Configuration of the Excel Destination</span></span>  
 <span data-ttu-id="b634e-144">Excel 대상은 Excel 연결 관리자를 사용하여 데이터 원본에 연결하며 연결 관리자가 사용할 통합 문서 파일을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b634e-144">The Excel destination uses an Excel connection manager to connect to a data source, and the connection manager specifies the workbook file to use.</span></span> <span data-ttu-id="b634e-145">자세한 내용은 [Excel Connection Manager](../connection-manager/excel-connection-manager.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b634e-145">For more information, see [Excel Connection Manager](../connection-manager/excel-connection-manager.md).</span></span>  
  
 <span data-ttu-id="b634e-146">Excel 대상에는 하나의 일반 입력 및 하나의 오류 출력이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b634e-146">The Excel destination has one regular input and one error output.</span></span>  
  
 <span data-ttu-id="b634e-147">[!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너를 사용하거나 프로그래밍 방식으로 속성을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b634e-147">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="b634e-148">**Excel 대상 편집기** 대화 상자에서 설정할 수 있는 속성에 대한 자세한 내용을 보려면 다음 항목 중 하나를 클릭하세요.</span><span class="sxs-lookup"><span data-stu-id="b634e-148">For more information about the properties that you can set in the **Excel Destination Editor** dialog box, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="b634e-149">Excel 대상 편집기&#40;연결 관리자 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="b634e-149">Excel Destination Editor &#40;Connection Manager Page&#41;</span></span>](../excel-destination-editor-connection-manager-page.md)  
  
-   [<span data-ttu-id="b634e-150">Excel 대상 편집기&#40;매핑 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="b634e-150">Excel Destination Editor &#40;Mappings Page&#41;</span></span>](../excel-destination-editor-mappings-page.md)  
  
-   [<span data-ttu-id="b634e-151">Excel 대상 편집기&#40;오류 출력 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="b634e-151">Excel Destination Editor &#40;Error Output Page&#41;</span></span>](../excel-destination-editor-error-output-page.md)  
  
 <span data-ttu-id="b634e-152">**고급 편집기** 대화 상자에는 프로그래밍 방식으로 설정할 수 있는 모든 속성이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="b634e-152">The **Advanced Editor** dialog box reflects all the properties that can be set programmatically.</span></span> <span data-ttu-id="b634e-153">**고급 편집기** 대화 상자를 사용하거나 프로그래밍 방식으로 설정할 수 있는 속성에 대한 자세한 내용을 보려면 다음 항목 중 하나를 클릭하세요.</span><span class="sxs-lookup"><span data-stu-id="b634e-153">For more information about the properties that you can set in the **Advanced Editor** dialog box or programmatically, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="b634e-154">Common Properties</span><span class="sxs-lookup"><span data-stu-id="b634e-154">Common Properties</span></span>](../common-properties.md)  
  
-   [<span data-ttu-id="b634e-155">Excel 사용자 지정 속성</span><span class="sxs-lookup"><span data-stu-id="b634e-155">Excel Custom Properties</span></span>](excel-custom-properties.md)  
  
 <span data-ttu-id="b634e-156">속성을 설정하는 방법에 대한 자세한 내용은 [데이터 흐름 구성 요소의 속성 설정](set-the-properties-of-a-data-flow-component.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b634e-156">For more information about how to set properties, see [Set the Properties of a Data Flow Component](set-the-properties-of-a-data-flow-component.md).</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="b634e-157">관련 작업</span><span class="sxs-lookup"><span data-stu-id="b634e-157">Related Tasks</span></span>  
  
-   [<span data-ttu-id="b634e-158">SSIS(SQL Server Integration Services)를 사용하여 Excel에서 데이터 가져오기 또는 Excel로 데이터 내보내기</span><span class="sxs-lookup"><span data-stu-id="b634e-158">Import data from Excel or export data to Excel with SQL Server Integration Services (SSIS)</span></span>](../load-data-to-from-excel-with-ssis.md)  
  
-   [<span data-ttu-id="b634e-159">Foreach 루프 컨테이너를 사용하여 Excel 파일 및 테이블 루핑</span><span class="sxs-lookup"><span data-stu-id="b634e-159">Loop through Excel Files and Tables by Using a Foreach Loop Container</span></span>](../control-flow/foreach-loop-container.md)  
  
-   [<span data-ttu-id="b634e-160">데이터 흐름 구성 요소의 속성 설정</span><span class="sxs-lookup"><span data-stu-id="b634e-160">Set the Properties of a Data Flow Component</span></span>](set-the-properties-of-a-data-flow-component.md)  
  
## <a name="see-also"></a><span data-ttu-id="b634e-161">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b634e-161">See Also</span></span>  
 <span data-ttu-id="b634e-162">[Excel 원본](excel-source.md) </span><span class="sxs-lookup"><span data-stu-id="b634e-162">[Excel Source](excel-source.md) </span></span>  
 <span data-ttu-id="b634e-163">[Integration Services&#40;SSIS&#41; 변수](../integration-services-ssis-variables.md) </span><span class="sxs-lookup"><span data-stu-id="b634e-163">[Integration Services &#40;SSIS&#41; Variables](../integration-services-ssis-variables.md) </span></span>  
 <span data-ttu-id="b634e-164">[데이터 흐름](data-flow.md) </span><span class="sxs-lookup"><span data-stu-id="b634e-164">[Data Flow](data-flow.md) </span></span>  
 [<span data-ttu-id="b634e-165">스크립트 태스크를 사용한 Excel 파일 작업</span><span class="sxs-lookup"><span data-stu-id="b634e-165">Working with Excel Files with the Script Task</span></span>](../extending-packages-scripting-task-examples/working-with-excel-files-with-the-script-task.md)  
  
  
