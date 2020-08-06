---
title: Excel 원본 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.excelsource.f1
helpviewer_keywords:
- Excel [Integration Services]
- sources [Integration Services], Excel
ms.assetid: e66349f3-b1b8-4763-89b7-7803541a4d62
author: chugugrace
ms.author: chugu
ms.openlocfilehash: c1324ca9e9b9535b8598e3e2de22f6c06c350b7b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742448"
---
# <a name="excel-source"></a><span data-ttu-id="1ef29-102">Excel 원본</span><span class="sxs-lookup"><span data-stu-id="1ef29-102">Excel Source</span></span>
  <span data-ttu-id="1ef29-103">Excel 원본은 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Excel 통합 문서의 워크시트 또는 범위에서 데이터를 추출합니다.</span><span class="sxs-lookup"><span data-stu-id="1ef29-103">The Excel source extracts data from worksheets or ranges in [!INCLUDE[msCoName](../../includes/msconame-md.md)] Excel workbooks.</span></span>  
  
 <span data-ttu-id="1ef29-104">Excel 원본은 데이터 추출을 위한 4가지 데이터 액세스 모델을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="1ef29-104">The Excel source provides four different data access modes for extracting data:</span></span>  
  
-   <span data-ttu-id="1ef29-105">테이블 또는 뷰</span><span class="sxs-lookup"><span data-stu-id="1ef29-105">A table or view.</span></span>  
  
-   <span data-ttu-id="1ef29-106">변수에 지정된 테이블 또는 뷰</span><span class="sxs-lookup"><span data-stu-id="1ef29-106">A table or view specified in a variable.</span></span>  
  
-   <span data-ttu-id="1ef29-107">SQL 문의 결과</span><span class="sxs-lookup"><span data-stu-id="1ef29-107">The results of an SQL statement.</span></span> <span data-ttu-id="1ef29-108">쿼리는 매개 변수가 있는 쿼리일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1ef29-108">The query can be a parameterized query.</span></span>  
  
-   <span data-ttu-id="1ef29-109">변수에 저장된 SQL 문의 결과</span><span class="sxs-lookup"><span data-stu-id="1ef29-109">The results of an SQL statement stored in a variable.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="1ef29-110">Excel에서 워크시트나 범위는 테이블 또는 뷰에 해당합니다.</span><span class="sxs-lookup"><span data-stu-id="1ef29-110">In Excel, a worksheet or range is the equivalent of a table or view.</span></span> <span data-ttu-id="1ef29-111">Excel 원본 및 대상 편집기의 사용 가능한 테이블 목록은 기존 워크시트(Sheet1$와 같이 워크시트 이름에 $ 기호가 붙음)와 명명된 범위(MyRange와 같이 $ 기호가 없음)를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="1ef29-111">The list of available tables in the Excel Source and Destination editors displays existing worksheets (identified by the $ sign appended to the worksheet name, such as Sheet1$) and named ranges (identified by the absence of the $ sign, such as MyRange).</span></span> <span data-ttu-id="1ef29-112">자세한 내용은 "사용 시 고려 사항" 섹션을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="1ef29-112">For more information, see the Usage Considerations section.</span></span>  
  
 <span data-ttu-id="1ef29-113">Excel 원본은 Excel 연결 관리자를 사용하여 데이터 원본에 연결하며 연결 관리자가 사용할 통합 문서 파일을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="1ef29-113">The Excel source uses an Excel connection manager to connect to a data source, and the connection manager specifies the workbook file to use.</span></span> <span data-ttu-id="1ef29-114">자세한 내용은 [Excel Connection Manager](../connection-manager/excel-connection-manager.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1ef29-114">For more information, see [Excel Connection Manager](../connection-manager/excel-connection-manager.md).</span></span>  
  
 <span data-ttu-id="1ef29-115">Excel 원본에는 하나의 일반 출력 및 하나의 오류 출력이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1ef29-115">The Excel source has one regular output and one error output.</span></span>  
  
## <a name="usage-considerations"></a><span data-ttu-id="1ef29-116">사용 시 고려 사항</span><span class="sxs-lookup"><span data-stu-id="1ef29-116">Usage Considerations</span></span>  
 <span data-ttu-id="1ef29-117">Excel 연결 관리자는 Jet 4.0용 [!INCLUDE[msCoName](../../includes/msconame-md.md)] OLE DB Provider와 공급자에서 지원하는 Excel ISAM(Indexed Sequential Access Method) 드라이버를 사용하여 Excel 데이터 원본에 연결하고 데이터를 읽고 씁니다.</span><span class="sxs-lookup"><span data-stu-id="1ef29-117">The Excel Connection Manager uses the [!INCLUDE[msCoName](../../includes/msconame-md.md)] OLE DB Provider for Jet 4.0 and its supporting Excel ISAM (Indexed Sequential Access Method) driver to connect and read and write data to Excel data sources.</span></span>  
  
 <span data-ttu-id="1ef29-118">이 공급자와 드라이버의 동작에 대해 다루는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 기술 자료 문서가 많이 있습니다. 이러한 문서가 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 또는 이전 기능인 데이터 변환 서비스와 반드시 관련된 것은 아니지만 예기치 않은 결과를 발생시킬 수 있는 특정 동작에 대해 살펴보는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="1ef29-118">Many existing [!INCLUDE[msCoName](../../includes/msconame-md.md)] Knowledge Base articles document the behavior of this provider and driver, and although these articles are not specific to [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] or its predecessor Data Transformation Services, you may want to know about certain behaviors that can lead to unexpected results.</span></span> <span data-ttu-id="1ef29-119">Excel 드라이버의 사용 방법과 동작에 대한 일반 정보는 [Visual Basic 또는 VBA에서 Excel 데이터에 ADO를 사용하는 방법](https://support.microsoft.com/kb/257819)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="1ef29-119">For general information on the use and behavior of the Excel driver, see [HOWTO: Use ADO with Excel Data from Visual Basic or VBA](https://support.microsoft.com/kb/257819).</span></span>  
  
 <span data-ttu-id="1ef29-120">Excel 드라이버를 사용하는 Jet 공급자의 다음 동작은 Excel 데이터 원본에서 데이터를 읽을 때 예기치 않은 결과를 발생시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1ef29-120">The following behaviors of the Jet provider with the Excel driver can lead to unexpected results when reading data from an Excel data source.</span></span>  
  
-   <span data-ttu-id="1ef29-121">**데이터 원본**.</span><span class="sxs-lookup"><span data-stu-id="1ef29-121">**Data sources**.</span></span> <span data-ttu-id="1ef29-122">Excel 통합 문서의 데이터 원본은 $ 기호가 붙은 워크시트(예: Sheet1$) 또는 명명된 범위(예: MyRange)일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1ef29-122">The source of data in an Excel workbook can be a worksheet, to which the $ sign must be appended (for example, Sheet1$), or a named range (for example, MyRange).</span></span> <span data-ttu-id="1ef29-123">SQL 문에서 $ 기호로 인한 구문 오류가 없도록 워크시트의 이름을 구분해야 합니다(예: [Sheet1$]).</span><span class="sxs-lookup"><span data-stu-id="1ef29-123">In a SQL statement, the name of a worksheet must be delimited (for example, [Sheet1$]) to avoid a syntax error caused by the $ sign.</span></span> <span data-ttu-id="1ef29-124">쿼리 작성기는 자동으로 이러한 구분 기호를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="1ef29-124">The Query Builder automatically adds these delimiters.</span></span> <span data-ttu-id="1ef29-125">워크시트 또는 범위를 지정하면 드라이버는 워크시트 또는 범위의 가장 왼쪽에서 비어 있지 않은 첫 번째 셀부터 인접한 블록의 셀을 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="1ef29-125">When you specify a worksheet or range, the driver reads the contiguous block of cells starting with the first non-empty cell in the upper-left corner of the worksheet or range.</span></span> <span data-ttu-id="1ef29-126">따라서 원본 데이터나 제목 또는 머리글 행과 데이터 행 사이에 빈 행이 있을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1ef29-126">Therefore you cannot have empty rows in the source data, or an empty row between title or header rows and the data rows.</span></span>  
  
-   <span data-ttu-id="1ef29-127">**누락 된 값**.</span><span class="sxs-lookup"><span data-stu-id="1ef29-127">**Missing values**.</span></span> <span data-ttu-id="1ef29-128">Excel 드라이버는 지정한 원본에서 특정 개수의 행(기본값: 8행)을 읽어 각 열의 데이터 형식을 추측합니다.</span><span class="sxs-lookup"><span data-stu-id="1ef29-128">The Excel driver reads a certain number of rows (by default, 8 rows) in the specified source to guess at the data type of each column.</span></span> <span data-ttu-id="1ef29-129">열에 혼합된 데이터 형식, 특히 숫자 데이터와 텍스트 데이터가 혼합되어 있으면 드라이버는 주로 사용된 데이터 형식을 지정하고 다른 형식의 데이터가 포함된 셀에 Null 값을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="1ef29-129">When a column appears to contain mixed data types, especially numeric data mixed with text data, the driver decides in favor of the majority data type, and returns null values for cells that contain data of the other type.</span></span> <span data-ttu-id="1ef29-130">사용된 횟수가 같은 경우에는 숫자 유형이 적용됩니다. Excel 워크시트에서 대부분의 셀 서식 옵션은 이러한 데이터 형식 결정에 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1ef29-130">(In a tie, the numeric type wins.) Most cell formatting options in the Excel worksheet do not seem to affect this data type determination.</span></span> <span data-ttu-id="1ef29-131">가져오기 모드를 지정하여 Excel 드라이버의 이러한 동작을 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1ef29-131">You can modify this behavior of the Excel driver by specifying Import Mode.</span></span> <span data-ttu-id="1ef29-132">가져오기 모드를 지정 하려면 `IMEX=1` **속성** 창에서 Excel 연결 관리자의 연결 문자열에 있는 확장 속성 값에을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="1ef29-132">To specify Import Mode, add `IMEX=1` to the value of Extended Properties in the connection string of the Excel connection manager in the **Properties** window.</span></span> <span data-ttu-id="1ef29-133">자세한 내용은 [PRB: DAO OpenRecordset를 사용할 때 Excel 값이 NULL로 반환된다](https://support.microsoft.com/kb/194124)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="1ef29-133">For more information, see [PRB: Excel Values Returned as NULL Using DAO OpenRecordset](https://support.microsoft.com/kb/194124).</span></span>  
  
-   <span data-ttu-id="1ef29-134">**잘린 텍스트**.</span><span class="sxs-lookup"><span data-stu-id="1ef29-134">**Truncated text**.</span></span> <span data-ttu-id="1ef29-135">Excel 열에 텍스트 데이터가 포함되어 있음이 확인되면 드라이버는 샘플링하는 값 중 가장 긴 값을 기준으로 데이터 형식(문자열 또는 메모)을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="1ef29-135">When the driver determines that an Excel column contains text data, the driver selects the data type (string or memo) based on the longest value that it samples.</span></span> <span data-ttu-id="1ef29-136">샘플링하는 행에서 255자보다 긴 값이 검색되지 않으면 이 드라이버는 해당 열을 메모 열이 아닌 255자 문자열 열로 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="1ef29-136">If the driver does not discover any values longer than 255 characters in the rows that it samples, it treats the column as a 255-character string column instead of a memo column.</span></span> <span data-ttu-id="1ef29-137">따라서 255자보다 긴 값은 잘릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1ef29-137">Therefore, values longer than 255 characters may be truncated.</span></span> <span data-ttu-id="1ef29-138">메모 열에서 데이터를 가져올 때 데이터가 잘리지 않도록 하려면 샘플링된 행 중 하나 이상의 행에 있는 메모 열에 255자보다 긴 값을 포함시키거나 드라이버가 샘플링하는 행 수를 늘려 이러한 행을 포함하도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="1ef29-138">To import data from a memo column without truncation, you must make sure that the memo column in at least one of the sampled rows contains a value longer than 255 characters, or you must increase the number of rows sampled by the driver to include such a row.</span></span> <span data-ttu-id="1ef29-139">**HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Jet\4.0\Engines\Excel** 레지스트리 키 아래 **TypeGuessRows** 값을 늘려 샘플링된 행 수를 늘릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1ef29-139">You can increase the number of rows sampled by increasing the value of **TypeGuessRows** under the **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Jet\4.0\Engines\Excel** registry key.</span></span> <span data-ttu-id="1ef29-140">자세한 내용은 [PRB: Transfer of Data from Jet 4.0 OLEDB Source Fails w/ Error](https://support.microsoft.com/kb/281517)(PRB: Jet 4.0 OLEDB 원본에서 데이터를 전송하면 버퍼 오버플로 오류가 발생하면서 실패)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1ef29-140">For more information, see [PRB: Transfer of Data from Jet 4.0 OLEDB Source Fails w/ Error](https://support.microsoft.com/kb/281517).</span></span>  
  
-   <span data-ttu-id="1ef29-141">**데이터 형식**.</span><span class="sxs-lookup"><span data-stu-id="1ef29-141">**Data types**.</span></span> <span data-ttu-id="1ef29-142">Excel 드라이버는 제한된 데이터 형식 집합만 인식합니다.</span><span class="sxs-lookup"><span data-stu-id="1ef29-142">The Excel driver recognizes only a limited set of data types.</span></span> <span data-ttu-id="1ef29-143">예를 들어 모든 숫자 열은 double(DT_R8)로 해석되고 모든 문자열 열(메모 열 제외)은 255자 유니코드 문자열(DT_WSTR)로 해석됩니다.</span><span class="sxs-lookup"><span data-stu-id="1ef29-143">For example, all numeric columns are interpreted as doubles (DT_R8), and all string columns (other than memo columns) are interpreted as 255-character Unicode strings (DT_WSTR).</span></span> [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] <span data-ttu-id="1ef29-144">에서는 Excel 데이터 형식을 다음과 같이 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="1ef29-144">maps the Excel data types as follows:</span></span>  
  
    -   <span data-ttu-id="1ef29-145">숫자 - 배정밀도 부동 소수점 수(DT_R8)</span><span class="sxs-lookup"><span data-stu-id="1ef29-145">Numeric - double-precision float (DT_R8)</span></span>  
  
    -   <span data-ttu-id="1ef29-146">통화 - currency(DT_CY)</span><span class="sxs-lookup"><span data-stu-id="1ef29-146">Currency - currency (DT_CY)</span></span>  
  
    -   <span data-ttu-id="1ef29-147">부울 - Boolean(DT_BOOL)</span><span class="sxs-lookup"><span data-stu-id="1ef29-147">Boolean - Boolean (DT_BOOL)</span></span>  
  
    -   <span data-ttu-id="1ef29-148">날짜/시간- `datetime` (DT_DATE)</span><span class="sxs-lookup"><span data-stu-id="1ef29-148">Date/time - `datetime` (DT_DATE)</span></span>  
  
    -   <span data-ttu-id="1ef29-149">문자열 - 길이가 255인 유니코드 문자열(DT_WSTR)</span><span class="sxs-lookup"><span data-stu-id="1ef29-149">String - Unicode string, length 255 (DT_WSTR)</span></span>  
  
    -   <span data-ttu-id="1ef29-150">메모 - 유니코드 텍스트 스트림(DT_NTEXT)</span><span class="sxs-lookup"><span data-stu-id="1ef29-150">Memo - Unicode text stream (DT_NTEXT)</span></span>  
  
-   <span data-ttu-id="1ef29-151">**데이터 형식 및 길이 변환**.</span><span class="sxs-lookup"><span data-stu-id="1ef29-151">**Data type and length conversions**.</span></span> [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] <span data-ttu-id="1ef29-152">에서는 데이터 형식을 암시적으로 변환하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1ef29-152">does not implicitly convert data types.</span></span> <span data-ttu-id="1ef29-153">따라서 파생 열 변환이나 데이터 변환을 사용하여 Excel 데이터를 비 Excel 대상으로 로드하기 전에 명시적으로 변환하거나 비 Excel 데이터를 Excel 대상으로 로드하기 전에 변환해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1ef29-153">As a result, you may need to use Derived Column or Data Conversion transformations to convert Excel data explicitly before loading it into a non-Excel destination, or to convert non-Excel data before loading it into an Excel destination.</span></span> <span data-ttu-id="1ef29-154">이 경우 필요한 변환을 구성해 주는 가져오기 및 내보내기 마법사를 사용하여 초기 패키지를 만들면 유용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1ef29-154">In this case, it may be useful to create the initial package by using the Import and Export Wizard, which configures the necessary conversions for you.</span></span> <span data-ttu-id="1ef29-155">필요할 수 있는 일부 변환 예는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="1ef29-155">Some examples of the conversions that may be required include the following:</span></span>  
  
    -   <span data-ttu-id="1ef29-156">유니코드 Excel 문자열 열과 특정 코드 페이지가 있는 비유니코드 문자열 열 간 변환</span><span class="sxs-lookup"><span data-stu-id="1ef29-156">Conversion between Unicode Excel string columns and non-Unicode string columns with specific codepages</span></span>  
  
    -   <span data-ttu-id="1ef29-157">255자 Excel 문자열 열과 길이가 다른 문자열 열 간 변환</span><span class="sxs-lookup"><span data-stu-id="1ef29-157">Conversion between 255-character Excel string columns and string columns of different lengths</span></span>  
  
    -   <span data-ttu-id="1ef29-158">배정밀도 Excel 숫자 열과 다른 유형의 숫자 열 간 변환</span><span class="sxs-lookup"><span data-stu-id="1ef29-158">Conversion between double-precision Excel numeric columns and numeric columns of other types</span></span>  
  
## <a name="excel-source-configuration"></a><span data-ttu-id="1ef29-159">Excel 원본 구성</span><span class="sxs-lookup"><span data-stu-id="1ef29-159">Excel Source Configuration</span></span>  
 <span data-ttu-id="1ef29-160">[!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너를 사용하거나 프로그래밍 방식으로 속성을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1ef29-160">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="1ef29-161">**Excel 원본 편집기** 대화 상자에서 설정할 수 있는 속성에 대한 자세한 내용을 보려면 다음 항목 중 하나를 클릭하십시오.</span><span class="sxs-lookup"><span data-stu-id="1ef29-161">For more information about the properties that you can set in the **Excel Source Editor** dialog box, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="1ef29-162">Excel 원본 편집기&#40;연결 관리자 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="1ef29-162">Excel Source Editor &#40;Connection Manager Page&#41;</span></span>](../excel-source-editor-connection-manager-page.md)  
  
-   [<span data-ttu-id="1ef29-163">Excel 원본 편집기&#40;열 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="1ef29-163">Excel Source Editor &#40;Columns Page&#41;</span></span>](../excel-source-editor-columns-page.md)  
  
-   [<span data-ttu-id="1ef29-164">Excel 원본 편집기&#40;오류 출력 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="1ef29-164">Excel Source Editor &#40;Error Output Page&#41;</span></span>](../excel-source-editor-error-output-page.md)  
  
 <span data-ttu-id="1ef29-165">**고급 편집기** 대화 상자에는 프로그래밍 방식으로 설정할 수 있는 모든 속성이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="1ef29-165">The **Advanced Editor** dialog box reflects all the properties that can be set programmatically.</span></span> <span data-ttu-id="1ef29-166">**고급 편집기** 대화 상자를 사용하거나 프로그래밍 방식으로 설정할 수 있는 속성에 대한 자세한 내용을 보려면 다음 항목 중 하나를 클릭하세요.</span><span class="sxs-lookup"><span data-stu-id="1ef29-166">For more information about the properties that you can set in the **Advanced Editor** dialog box or programmatically, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="1ef29-167">Common Properties</span><span class="sxs-lookup"><span data-stu-id="1ef29-167">Common Properties</span></span>](../common-properties.md)  
  
-   [<span data-ttu-id="1ef29-168">Excel 사용자 지정 속성</span><span class="sxs-lookup"><span data-stu-id="1ef29-168">Excel Custom Properties</span></span>](excel-custom-properties.md)  
  
 <span data-ttu-id="1ef29-169">Excel 파일 그룹을 통한 루핑 방법에 대한 자세한 내용은 [Foreach 루프 컨테이너를 사용하여 Excel 파일 및 테이블 루핑](../control-flow/foreach-loop-container.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1ef29-169">For information about looping through a group of Excel files, see [Loop through Excel Files and Tables by Using a Foreach Loop Container](../control-flow/foreach-loop-container.md).</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="1ef29-170">관련 작업</span><span class="sxs-lookup"><span data-stu-id="1ef29-170">Related Tasks</span></span>  

-   [<span data-ttu-id="1ef29-171">SSIS(SQL Server Integration Services)를 사용하여 Excel에서 데이터 가져오기 또는 Excel로 데이터 내보내기</span><span class="sxs-lookup"><span data-stu-id="1ef29-171">Import data from Excel or export data to Excel with SQL Server Integration Services (SSIS)</span></span>](../load-data-to-from-excel-with-ssis.md)

-   [<span data-ttu-id="1ef29-172">쿼리 매개 변수를 데이터 흐름 구성 요소의 변수에 매핑</span><span class="sxs-lookup"><span data-stu-id="1ef29-172">Map Query Parameters to Variables in a Data Flow Component</span></span>](map-query-parameters-to-variables-in-a-data-flow-component.md)  
  
-   [<span data-ttu-id="1ef29-173">데이터 흐름 구성 요소의 속성 설정</span><span class="sxs-lookup"><span data-stu-id="1ef29-173">Set the Properties of a Data Flow Component</span></span>](set-the-properties-of-a-data-flow-component.md)  
  
-   [<span data-ttu-id="1ef29-174">병합 및 병합 조인 변환을 위한 데이터 정렬</span><span class="sxs-lookup"><span data-stu-id="1ef29-174">Sort Data for the Merge and Merge Join Transformations</span></span>](transformations/sort-data-for-the-merge-and-merge-join-transformations.md)  
  
-   [<span data-ttu-id="1ef29-175">Foreach 루프 컨테이너를 사용하여 Excel 파일 및 테이블 루핑</span><span class="sxs-lookup"><span data-stu-id="1ef29-175">Loop through Excel Files and Tables by Using a Foreach Loop Container</span></span>](../control-flow/foreach-loop-container.md)  
  
## <a name="related-content"></a><span data-ttu-id="1ef29-176">관련 내용</span><span class="sxs-lookup"><span data-stu-id="1ef29-176">Related Content</span></span>  
  
-   <span data-ttu-id="1ef29-177">hrvoje.piasevoli.com의 블로그 항목 - [SSIS의 64비트 Excel에서 데이터 가져오기](https://go.microsoft.com/fwlink/?LinkId=217673)</span><span class="sxs-lookup"><span data-stu-id="1ef29-177">Blog entry, [Importing data from 64-bit Excel in SSIS](https://go.microsoft.com/fwlink/?LinkId=217673), on hrvoje.piasevoli.com</span></span>  
  
-   <span data-ttu-id="1ef29-178">블로그 항목, [SSIS에서 Excel (.xlsx)에 연결](https://microsoft-ssis.blogspot.com/2014/02/connecting-to-excel-xlsx-in-ssis.html)</span><span class="sxs-lookup"><span data-stu-id="1ef29-178">Blog entry, [Connecting to Excel (XLSX) in SSIS](https://microsoft-ssis.blogspot.com/2014/02/connecting-to-excel-xlsx-in-ssis.html).</span></span>  
  
  
