---
title: Excel 대상 편집기 (연결 관리자 페이지) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.exceldestadapter.connection.f1
helpviewer_keywords:
- Excel Destination Editor
ms.assetid: fc13f725-963c-488e-91e2-20627133e842
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1556bf713c49aac31f1cc1cd624336f10dbf832f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651808"
---
# <a name="excel-destination-editor-connection-manager-page"></a><span data-ttu-id="6bed9-102">Excel 대상 편집기(연결 관리자 페이지)</span><span class="sxs-lookup"><span data-stu-id="6bed9-102">Excel Destination Editor (Connection Manager Page)</span></span>
  <span data-ttu-id="6bed9-103">**Excel 대상 편집기** 대화 상자의 **연결 관리자** 페이지를 사용하여 데이터 원본 정보를 지정하고 그 결과를 미리 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6bed9-103">Use the **Connection Manager** page of the **Excel Destination Editor** dialog box to specify data source information, and to preview the results.</span></span> <span data-ttu-id="6bed9-104">Excel 대상은 데이터를 워크시트 또는 [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)] Excel 통합 문서의 명명된 범위로 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="6bed9-104">The Excel destination loads data into a worksheet or a named range in a [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)] workbook.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6bed9-105">Excel `CommandTimeout` 대상의 속성은 **Excel 대상 편집기**에서 사용할 수 없지만 **고급 편집기**를 사용 하 여 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6bed9-105">The `CommandTimeout` property of the Excel destination is not available in the **Excel Destination Editor**, but can be set by using the **Advanced Editor**.</span></span> <span data-ttu-id="6bed9-106">또한 특정 빠른 로드 옵션은 **고급 편집기**에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6bed9-106">In addition, certain Fast Load options are available only in the **Advanced Editor**.</span></span> <span data-ttu-id="6bed9-107">이러한 속성에 대한 자세한 내용은 [Excel Custom Properties](data-flow/excel-custom-properties.md)의 Excel 대상 섹션을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="6bed9-107">For more information on these properties, see the Excel Destination section of [Excel Custom Properties](data-flow/excel-custom-properties.md).</span></span>  
  
 <span data-ttu-id="6bed9-108">Excel 대상에 대한 자세한 내용은 [Excel Destination](data-flow/excel-destination.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="6bed9-108">To learn more about the Excel destination, see [Excel Destination](data-flow/excel-destination.md).</span></span>  
  
## <a name="static-options"></a><span data-ttu-id="6bed9-109">정적 옵션</span><span class="sxs-lookup"><span data-stu-id="6bed9-109">Static Options</span></span>  
 <span data-ttu-id="6bed9-110">**Excel 연결 관리자**</span><span class="sxs-lookup"><span data-stu-id="6bed9-110">**Excel connection manager**</span></span>  
 <span data-ttu-id="6bed9-111">목록에서 기존 Excel 연결 관리자를 선택하거나 **새로 만들기**를 클릭하여 새 연결을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="6bed9-111">Select an existing Excel connection manager from the list, or create a new connection by clicking **New**.</span></span>  
  
 <span data-ttu-id="6bed9-112">**새로 만들기**</span><span class="sxs-lookup"><span data-stu-id="6bed9-112">**New**</span></span>  
 <span data-ttu-id="6bed9-113">**Excel 연결 관리자** 대화 상자를 사용하여 새 연결 관리자를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="6bed9-113">Create a new connection manager by using the **Excel Connection Manager** dialog box.</span></span>  
  
 <span data-ttu-id="6bed9-114">**데이터 액세스 모드**</span><span class="sxs-lookup"><span data-stu-id="6bed9-114">**Data access mode**</span></span>  
 <span data-ttu-id="6bed9-115">원본에서 데이터를 선택하는 방법을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="6bed9-115">Specify the method for selecting data from the source.</span></span>  
  
|<span data-ttu-id="6bed9-116">옵션</span><span class="sxs-lookup"><span data-stu-id="6bed9-116">Option</span></span>|<span data-ttu-id="6bed9-117">Description</span><span class="sxs-lookup"><span data-stu-id="6bed9-117">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="6bed9-118">테이블 또는 뷰</span><span class="sxs-lookup"><span data-stu-id="6bed9-118">Table or view</span></span>|<span data-ttu-id="6bed9-119">데이터를 워크시트 또는 Excel 데이터 원본의 명명된 범위로 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="6bed9-119">Loads data into a worksheet or named range in the Excel data source.</span></span>|  
|<span data-ttu-id="6bed9-120">테이블 이름 또는 뷰 이름 변수</span><span class="sxs-lookup"><span data-stu-id="6bed9-120">Table name or view name variable</span></span>|<span data-ttu-id="6bed9-121">변수에 워크시트 또는 범위 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="6bed9-121">Specify the worksheet or range name in a variable.</span></span><br /><br /> <span data-ttu-id="6bed9-122">**관련 정보**: [패키지에서 변수 사용](../../2014/integration-services/use-variables-in-packages.md)</span><span class="sxs-lookup"><span data-stu-id="6bed9-122">**Related information**: [Use Variables in Packages](../../2014/integration-services/use-variables-in-packages.md)</span></span>|  
|<span data-ttu-id="6bed9-123">SQL 명령</span><span class="sxs-lookup"><span data-stu-id="6bed9-123">SQL command</span></span>|<span data-ttu-id="6bed9-124">SQL 쿼리를 사용하여 Excel 대상으로 데이터를 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="6bed9-124">Load data into the Excel destination by using an SQL query.</span></span>|  
  
 <span data-ttu-id="6bed9-125">**Excel 시트의 이름**</span><span class="sxs-lookup"><span data-stu-id="6bed9-125">**Name of the Excel sheet**</span></span>  
 <span data-ttu-id="6bed9-126">드롭다운 목록에서 Excel 대상을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6bed9-126">Select the excel destination from the drop-down list.</span></span> <span data-ttu-id="6bed9-127">목록이 비어 있는 경우 **새로 만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6bed9-127">If the list is empty, click **New**.</span></span>  
  
 <span data-ttu-id="6bed9-128">**새로 만들기**</span><span class="sxs-lookup"><span data-stu-id="6bed9-128">**New**</span></span>  
 <span data-ttu-id="6bed9-129">**새로 만들기** 를 클릭하여 **테이블 만들기** 대화 상자를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="6bed9-129">Click **New** to launch the **Create Table** dialog box.</span></span> <span data-ttu-id="6bed9-130">**확인**을 클릭하면 대화 상자에서 **Excel 연결 관리자** 가 가리키는 Excel 파일이 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="6bed9-130">When you click **OK**, the dialog box creates the excel file that the **Excel Connection Manager** points to.</span></span>  
  
 <span data-ttu-id="6bed9-131">**기존 데이터 보기**</span><span class="sxs-lookup"><span data-stu-id="6bed9-131">**View Existing Data**</span></span>  
 <span data-ttu-id="6bed9-132">**쿼리 결과 미리 보기** 대화 상자를 사용하여 결과를 미리 봅니다.</span><span class="sxs-lookup"><span data-stu-id="6bed9-132">Preview results by using the **Preview Query Results** dialog box.</span></span> <span data-ttu-id="6bed9-133">미리 보기에는 최대 200개의 행이 표시될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6bed9-133">Preview can display up to 200 rows.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="6bed9-134"> 선택한 **Excel 연결 관리자** 가 존재하지 않는 Excel 파일을 가리키는 경우 이 단추를 클릭하면 오류 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="6bed9-134">If the **Excel connection manager** you selected points to an excel file that does not exist, you will see an error message when you click this button.</span></span>  
  
## <a name="data-access-mode-dynamic-options"></a><span data-ttu-id="6bed9-135">데이터 액세스 모드 동적 옵션</span><span class="sxs-lookup"><span data-stu-id="6bed9-135">Data Access Mode Dynamic Options</span></span>  
  
### <a name="data-access-mode--table-or-view"></a><span data-ttu-id="6bed9-136">데이터 액세스 모드 = 테이블 또는 뷰</span><span class="sxs-lookup"><span data-stu-id="6bed9-136">Data access mode = Table or view</span></span>  
 <span data-ttu-id="6bed9-137">**Excel 시트의 이름**</span><span class="sxs-lookup"><span data-stu-id="6bed9-137">**Name of the Excel sheet**</span></span>  
 <span data-ttu-id="6bed9-138">데이터 원본에서 사용할 수 있는 워크시트 또는 명명된 범위 목록에서 이름을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6bed9-138">Select the name of the worksheet or named range from a list of those available in the data source.</span></span>  
  
### <a name="data-access-mode--table-name-or-view-name-variable"></a><span data-ttu-id="6bed9-139">데이터 액세스 모드 = 테이블 이름 또는 뷰 이름 변수</span><span class="sxs-lookup"><span data-stu-id="6bed9-139">Data access mode = Table name or view name variable</span></span>  
 <span data-ttu-id="6bed9-140">**변수 이름**</span><span class="sxs-lookup"><span data-stu-id="6bed9-140">**Variable name**</span></span>  
 <span data-ttu-id="6bed9-141">워크시트 또는 명명된 범위 이름이 포함된 변수를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6bed9-141">Select the variable that contains the name of the worksheet or named range.</span></span>  
  
### <a name="data-access-mode--sql-command"></a><span data-ttu-id="6bed9-142">데이터 액세스 모드 = SQL 명령</span><span class="sxs-lookup"><span data-stu-id="6bed9-142">Data access mode = SQL command</span></span>  
 <span data-ttu-id="6bed9-143">**SQL 명령 텍스트**</span><span class="sxs-lookup"><span data-stu-id="6bed9-143">**SQL command text**</span></span>  
 <span data-ttu-id="6bed9-144">SQL 쿼리 텍스트를 입력하고 **쿼리 작성**을 클릭하여 쿼리를 작성하거나 **찾아보기**를 클릭하여 쿼리 텍스트가 포함된 파일을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="6bed9-144">Enter the text of an SQL query, build the query by clicking **Build Query**, or locate the file that contains the query text by clicking **Browse**.</span></span>  
  
 <span data-ttu-id="6bed9-145">**쿼리 작성**</span><span class="sxs-lookup"><span data-stu-id="6bed9-145">**Build Query**</span></span>  
 <span data-ttu-id="6bed9-146">**쿼리 작성기** 대화 상자를 사용하여 시각적으로 SQL 쿼리를 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6bed9-146">Use the **Query Builder** dialog box to construct the SQL query visually.</span></span>  
  
 <span data-ttu-id="6bed9-147">**찾아보기**</span><span class="sxs-lookup"><span data-stu-id="6bed9-147">**Browse**</span></span>  
 <span data-ttu-id="6bed9-148">**열기** 대화 상자를 사용하여 SQL 쿼리 텍스트가 포함된 파일을 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6bed9-148">Use the **Open** dialog box to locate the file that contains the text of the SQL query.</span></span>  
  
 <span data-ttu-id="6bed9-149">**쿼리 구문 분석**</span><span class="sxs-lookup"><span data-stu-id="6bed9-149">**Parse Query**</span></span>  
 <span data-ttu-id="6bed9-150">쿼리 텍스트의 구문을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="6bed9-150">Verify the syntax of the query text.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6bed9-151">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6bed9-151">See Also</span></span>  
 <span data-ttu-id="6bed9-152">[Integration Services 오류 및 메시지 참조](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="6bed9-152">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="6bed9-153">[Excel 대상 편집기 &#40;매핑 페이지&#41;](../../2014/integration-services/excel-destination-editor-mappings-page.md) </span><span class="sxs-lookup"><span data-stu-id="6bed9-153">[Excel Destination Editor &#40;Mappings Page&#41;](../../2014/integration-services/excel-destination-editor-mappings-page.md) </span></span>  
 <span data-ttu-id="6bed9-154">[Excel 대상 편집기 &#40;오류 출력 페이지&#41;](../../2014/integration-services/excel-destination-editor-error-output-page.md) </span><span class="sxs-lookup"><span data-stu-id="6bed9-154">[Excel Destination Editor &#40;Error Output Page&#41;](../../2014/integration-services/excel-destination-editor-error-output-page.md) </span></span>  
 [<span data-ttu-id="6bed9-155">Foreach 루프 컨테이너를 사용하여 Excel 파일 및 테이블 루핑</span><span class="sxs-lookup"><span data-stu-id="6bed9-155">Loop through Excel Files and Tables by Using a Foreach Loop Container</span></span>](control-flow/foreach-loop-container.md)  
  
  
