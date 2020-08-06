---
title: Excel 원본 편집기 (연결 관리자 페이지) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.excelsourceadapter.connection.f1
helpviewer_keywords:
- Excel Source Editor
ms.assetid: 428e04e0-ad98-45d0-8345-12ec1b67b2eb
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 3285b5c8b14016b91005af79542e3e2f9b6559b6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651792"
---
# <a name="excel-source-editor-connection-manager-page"></a><span data-ttu-id="e2e0d-102">Excel 원본 편집기(연결 관리자 페이지)</span><span class="sxs-lookup"><span data-stu-id="e2e0d-102">Excel Source Editor (Connection Manager Page)</span></span>
  <span data-ttu-id="e2e0d-103">**Excel 원본 편집기** 대화 상자의 **연결 관리자** 노드를 사용하여 원본으로 사용할 [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)] 통합 문서를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e2e0d-103">Use the **Connection Manager** node of the **Excel Source Editor** dialog box to select the [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)] workbook for the source to use.</span></span> <span data-ttu-id="e2e0d-104">Excel 원본에서는 워크시트 또는 기존 통합 문서의 명명된 범위에서 데이터를 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="e2e0d-104">The Excel source reads data from a worksheet or named range in an existing workbook.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e2e0d-105">Excel 원본의 `CommandTimeout` 속성은 **Excel 원본 편집기**에서 사용할 수 없지만 **고급 편집기**를 사용 하 여 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e2e0d-105">The `CommandTimeout` property of the Excel source is not available in the **Excel Source Editor**, but can be set by using the **Advanced Editor**.</span></span> <span data-ttu-id="e2e0d-106">이 속성에 대한 자세한 내용은 [Excel Custom Properties](data-flow/excel-custom-properties.md)의 Excel 원본 섹션을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="e2e0d-106">For more information on this property, see the Excel Source section of [Excel Custom Properties](data-flow/excel-custom-properties.md).</span></span>  
  
 <span data-ttu-id="e2e0d-107">Excel 원본에 대한 자세한 내용은 [Excel Source](data-flow/excel-source.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="e2e0d-107">To learn more about the Excel source, see [Excel Source](data-flow/excel-source.md).</span></span>  
  
## <a name="static-options"></a><span data-ttu-id="e2e0d-108">정적 옵션</span><span class="sxs-lookup"><span data-stu-id="e2e0d-108">Static Options</span></span>  
 <span data-ttu-id="e2e0d-109">**캐시 없음**</span><span class="sxs-lookup"><span data-stu-id="e2e0d-109">**OLE DB connection manager**</span></span>  
 <span data-ttu-id="e2e0d-110">목록에서 기존 Excel 연결 관리자를 선택하거나 **새로 만들기**를 클릭하여 새 연결을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e2e0d-110">Select an existing Excel connection manager from the list, or create a new connection by clicking **New**.</span></span>  
  
 <span data-ttu-id="e2e0d-111">**새로 만들기**</span><span class="sxs-lookup"><span data-stu-id="e2e0d-111">**New**</span></span>  
 <span data-ttu-id="e2e0d-112">**Excel 연결 관리자** 대화 상자를 사용하여 새 연결 관리자를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e2e0d-112">Create a new connection manager by using the **Excel Connection Manager** dialog box.</span></span>  
  
 <span data-ttu-id="e2e0d-113">**데이터 액세스 모드**</span><span class="sxs-lookup"><span data-stu-id="e2e0d-113">**Data access mode**</span></span>  
 <span data-ttu-id="e2e0d-114">원본에서 데이터를 선택하는 방법을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e2e0d-114">Specify the method for selecting data from the source.</span></span>  
  
|<span data-ttu-id="e2e0d-115">값</span><span class="sxs-lookup"><span data-stu-id="e2e0d-115">Value</span></span>|<span data-ttu-id="e2e0d-116">Description</span><span class="sxs-lookup"><span data-stu-id="e2e0d-116">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="e2e0d-117">테이블 또는 뷰</span><span class="sxs-lookup"><span data-stu-id="e2e0d-117">Table or view</span></span>|<span data-ttu-id="e2e0d-118">Excel 파일의 워크시트나 명명된 범위에서 데이터를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="e2e0d-118">Retrieve data from a worksheet or named range in the Excel file.</span></span>|  
|<span data-ttu-id="e2e0d-119">테이블 이름 또는 뷰 이름 변수</span><span class="sxs-lookup"><span data-stu-id="e2e0d-119">Table name or view name variable</span></span>|<span data-ttu-id="e2e0d-120">변수에 워크시트 또는 범위 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e2e0d-120">Specify the worksheet or range name in a variable.</span></span><br /><br /> <span data-ttu-id="e2e0d-121">**관련 정보:** [패키지에서 변수 사용](../../2014/integration-services/use-variables-in-packages.md)</span><span class="sxs-lookup"><span data-stu-id="e2e0d-121">**Related information:** [Use Variables in Packages](../../2014/integration-services/use-variables-in-packages.md)</span></span>|  
|<span data-ttu-id="e2e0d-122">SQL 명령</span><span class="sxs-lookup"><span data-stu-id="e2e0d-122">SQL command</span></span>|<span data-ttu-id="e2e0d-123">SQL 쿼리를 사용하여 Excel 파일에서 데이터를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="e2e0d-123">Retrieve data from the Excel file by using a SQL query.</span></span> <span data-ttu-id="e2e0d-124">쿼리 구문에 대한 자세한 내용은 [Excel Source](data-flow/excel-source.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="e2e0d-124">For information about query syntax, see [Excel Source](data-flow/excel-source.md).</span></span>|  
|<span data-ttu-id="e2e0d-125">변수를 사용한 SQL 명령</span><span class="sxs-lookup"><span data-stu-id="e2e0d-125">SQL command from variable</span></span>|<span data-ttu-id="e2e0d-126">변수에 SQL 쿼리 텍스트를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e2e0d-126">Specify the SQL query text in a variable.</span></span>|  
  
 <span data-ttu-id="e2e0d-127">**미리 보기**</span><span class="sxs-lookup"><span data-stu-id="e2e0d-127">**Preview**</span></span>  
 <span data-ttu-id="e2e0d-128">**데이터 보기** 대화 상자를 사용하여 결과를 미리 봅니다.</span><span class="sxs-lookup"><span data-stu-id="e2e0d-128">Preview results by using the **Data View** dialog box.</span></span> <span data-ttu-id="e2e0d-129">미리 보기에는 최대 200개의 행이 표시될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e2e0d-129">Preview can display up to 200 rows.</span></span>  
  
## <a name="data-access-mode-dynamic-options"></a><span data-ttu-id="e2e0d-130">데이터 액세스 모드 동적 옵션</span><span class="sxs-lookup"><span data-stu-id="e2e0d-130">Data Access Mode Dynamic Options</span></span>  
  
### <a name="data-access-mode--table-or-view"></a><span data-ttu-id="e2e0d-131">데이터 액세스 모드 = 테이블 또는 뷰</span><span class="sxs-lookup"><span data-stu-id="e2e0d-131">Data access mode = Table or view</span></span>  
 <span data-ttu-id="e2e0d-132">**Excel 시트의 이름**</span><span class="sxs-lookup"><span data-stu-id="e2e0d-132">**Name of the Excel sheet**</span></span>  
 <span data-ttu-id="e2e0d-133">Excel 통합 문서에서 사용할 수 있는 워크시트 또는 명명된 범위 목록에서 이름을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e2e0d-133">Select the name of the worksheet or named range from a list of those available in the Excel workbook.</span></span>  
  
### <a name="data-access-mode--table-name-or-view-name-variable"></a><span data-ttu-id="e2e0d-134">데이터 액세스 모드 = 테이블 이름 또는 뷰 이름 변수</span><span class="sxs-lookup"><span data-stu-id="e2e0d-134">Data access mode = Table name or view name variable</span></span>  
 <span data-ttu-id="e2e0d-135">**변수 이름**</span><span class="sxs-lookup"><span data-stu-id="e2e0d-135">**Variable name**</span></span>  
 <span data-ttu-id="e2e0d-136">워크시트 또는 명명된 범위 이름이 포함된 변수를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e2e0d-136">Select the variable that contains the name of the worksheet or named range.</span></span>  
  
### <a name="data-access-mode--sql-command"></a><span data-ttu-id="e2e0d-137">데이터 액세스 모드 = SQL 명령</span><span class="sxs-lookup"><span data-stu-id="e2e0d-137">Data access mode = SQL command</span></span>  
 <span data-ttu-id="e2e0d-138">**SQL 명령 텍스트**</span><span class="sxs-lookup"><span data-stu-id="e2e0d-138">**SQL command text**</span></span>  
 <span data-ttu-id="e2e0d-139">SQL 쿼리 텍스트를 입력하고 **쿼리 작성**을 클릭하여 쿼리를 작성하거나 **찾아보기**를 클릭하여 쿼리 텍스트가 포함된 파일을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="e2e0d-139">Enter the text of a SQL query, build the query by clicking **Build Query**, or browse to the file that contains the query text by clicking **Browse**.</span></span>  
  
 <span data-ttu-id="e2e0d-140">**매개 변수**</span><span class="sxs-lookup"><span data-stu-id="e2e0d-140">**Parameters**</span></span>  
 <span data-ttu-id="e2e0d-141">쿼리 텍스트에 ?를</span><span class="sxs-lookup"><span data-stu-id="e2e0d-141">If you have entered a parameterized query by using ?</span></span> <span data-ttu-id="e2e0d-142">매개 변수 자리 표시자로 사용하여 매개 변수가 있는 쿼리를 입력한 경우 **쿼리 매개 변수 설정** 대화 상자를 사용하여 쿼리 입력 매개 변수를 패키지 변수에 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="e2e0d-142">as a parameter placeholder in the query text, use the **Set Query Parameters** dialog box to map query input parameters to package variables.</span></span>  
  
 <span data-ttu-id="e2e0d-143">**쿼리 작성**</span><span class="sxs-lookup"><span data-stu-id="e2e0d-143">**Build query**</span></span>  
 <span data-ttu-id="e2e0d-144">**쿼리 작성기** 대화 상자를 사용하여 시각적으로 SQL 쿼리를 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e2e0d-144">Use the **Query Builder** dialog box to construct the SQL query visually.</span></span>  
  
 <span data-ttu-id="e2e0d-145">**찾아보기**</span><span class="sxs-lookup"><span data-stu-id="e2e0d-145">**Browse**</span></span>  
 <span data-ttu-id="e2e0d-146">**열기** 대화 상자를 사용하여 SQL 쿼리 텍스트가 포함된 파일을 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e2e0d-146">Use the **Open** dialog box to locate the file that contains the text of the SQL query.</span></span>  
  
 <span data-ttu-id="e2e0d-147">**쿼리 구문 분석**</span><span class="sxs-lookup"><span data-stu-id="e2e0d-147">**Parse query**</span></span>  
 <span data-ttu-id="e2e0d-148">쿼리 텍스트의 구문을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="e2e0d-148">Verify the syntax of the query text.</span></span>  
  
### <a name="data-access-mode--sql-command-from-variable"></a><span data-ttu-id="e2e0d-149">데이터 액세스 모드 = 변수를 사용한 SQL 명령</span><span class="sxs-lookup"><span data-stu-id="e2e0d-149">Data access mode = SQL command from variable</span></span>  
 <span data-ttu-id="e2e0d-150">**변수 이름**</span><span class="sxs-lookup"><span data-stu-id="e2e0d-150">**Variable name**</span></span>  
 <span data-ttu-id="e2e0d-151">SQL 쿼리 텍스트가 포함된 변수를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e2e0d-151">Select the variable that contains the text of the SQL query.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2e0d-152">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e2e0d-152">See Also</span></span>  
 <span data-ttu-id="e2e0d-153">[Integration Services 오류 및 메시지 참조](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="e2e0d-153">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="e2e0d-154">[Excel 원본 편집기 &#40;열 페이지&#41;](../../2014/integration-services/excel-source-editor-columns-page.md) </span><span class="sxs-lookup"><span data-stu-id="e2e0d-154">[Excel Source Editor &#40;Columns Page&#41;](../../2014/integration-services/excel-source-editor-columns-page.md) </span></span>  
 <span data-ttu-id="e2e0d-155">[Excel 원본 편집기 &#40;오류 출력 페이지&#41;](../../2014/integration-services/excel-source-editor-error-output-page.md) </span><span class="sxs-lookup"><span data-stu-id="e2e0d-155">[Excel Source Editor &#40;Error Output Page&#41;](../../2014/integration-services/excel-source-editor-error-output-page.md) </span></span>  
 <span data-ttu-id="e2e0d-156">[Excel 연결 관리자](connection-manager/excel-connection-manager.md) </span><span class="sxs-lookup"><span data-stu-id="e2e0d-156">[Excel Connection Manager](connection-manager/excel-connection-manager.md) </span></span>  
 [<span data-ttu-id="e2e0d-157">Foreach 루프 컨테이너를 사용하여 Excel 파일 및 테이블 루핑</span><span class="sxs-lookup"><span data-stu-id="e2e0d-157">Loop through Excel Files and Tables by Using a Foreach Loop Container</span></span>](control-flow/foreach-loop-container.md)  
  
  
