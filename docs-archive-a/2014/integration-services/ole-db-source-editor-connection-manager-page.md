---
title: OLE DB 원본 편집기 (연결 관리자 페이지) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.oledbsourceadapter.connection.f1
helpviewer_keywords:
- OLE DB Source Editor
ms.assetid: 53699902-8699-4547-b56b-a5b2079e98b6
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e6b9d841ff902107847a9d85779af41f476315db
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660059"
---
# <a name="ole-db-source-editor-connection-manager-page"></a><span data-ttu-id="4cc36-102">OLE DB 원본 편집기(연결 관리자 페이지)</span><span class="sxs-lookup"><span data-stu-id="4cc36-102">OLE DB Source Editor (Connection Manager Page)</span></span>
  <span data-ttu-id="4cc36-103">**OLE DB 원본 편집기** 대화 상자의 **연결 관리자** 페이지를 사용하여 원본의 OLE DB 연결 관리자를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4cc36-103">Use the **Connection Manager** page of the **OLE DB Source Editor** dialog box to select the OLE DB connection manager for the source.</span></span> <span data-ttu-id="4cc36-104">이 페이지를 사용하면 데이터베이스에서 테이블이나 뷰를 선택할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4cc36-104">This page also lets you select a table or view from the database.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4cc36-105">[!INCLUDE[msCoName](../includes/msconame-md.md)] Office Excel 2007을 사용하는 데이터 원본에서 데이터를 로드하려면 OLE DB 원본을 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="4cc36-105">To load data from a data source that uses [!INCLUDE[msCoName](../includes/msconame-md.md)] Office Excel 2007, use an OLE DB source.</span></span> <span data-ttu-id="4cc36-106">Excel 원본을 사용하여 Excel 2007 데이터 원본에서 데이터를 로드할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4cc36-106">You cannot use an Excel source to load data from an Excel 2007 data source.</span></span> <span data-ttu-id="4cc36-107">자세한 내용은 [Configure OLE DB Connection Manager](configure-ole-db-connection-manager.md)을(를) 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4cc36-107">For more information, see [Configure OLE DB Connection Manager](configure-ole-db-connection-manager.md).</span></span>  
>   
>  <span data-ttu-id="4cc36-108">[!INCLUDE[msCoName](../includes/msconame-md.md)] Office Excel 2003 이전 버전을 사용하는 데이터 원본에서 데이터를 로드하려면 Excel 원본을 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="4cc36-108">To load data from a data source that uses [!INCLUDE[msCoName](../includes/msconame-md.md)] Office Excel 2003 or earlier, use an Excel source.</span></span> <span data-ttu-id="4cc36-109">자세한 내용은 [Excel 원본 편집기&#40;연결 관리자 페이지&#41;](../../2014/integration-services/excel-source-editor-connection-manager-page.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4cc36-109">For more information, see [Excel Source Editor &#40;Connection Manager Page&#41;](../../2014/integration-services/excel-source-editor-connection-manager-page.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4cc36-110">`CommandTimeout`OLE DB 원본의 속성은 **OLE DB 원본 편집기**에서 사용할 수 없지만 **고급 편집기**를 사용 하 여 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4cc36-110">The `CommandTimeout` property of the OLE DB source is not available in the **OLE DB Source Editor**, but can be set by using the **Advanced Editor**.</span></span> <span data-ttu-id="4cc36-111">이 속성에 대한 자세한 내용은 [OLE DB Custom Properties](data-flow/ole-db-custom-properties.md)의 Excel 원본 섹션을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="4cc36-111">For more information on this property, see the Excel Source section of [OLE DB Custom Properties](data-flow/ole-db-custom-properties.md).</span></span>  
  
 <span data-ttu-id="4cc36-112">OLE DB 원본에 대한 자세한 내용은 [OLE DB Source](data-flow/ole-db-source.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="4cc36-112">To learn more about the OLE DB source, see [OLE DB Source](data-flow/ole-db-source.md).</span></span>  
  
## <a name="open-the-ole-db-source-editor-connection-manager-page"></a><span data-ttu-id="4cc36-113">OLE DB 원본 편집기 열기(연결 관리자 페이지)</span><span class="sxs-lookup"><span data-stu-id="4cc36-113">Open the OLE DB Source Editor (Connection Manager Page</span></span>  
  
1.  <span data-ttu-id="4cc36-114">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 에서 OLE DB 원본을 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="4cc36-114">Add the OLE DB source to the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] package, in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span>  
  
2.  <span data-ttu-id="4cc36-115">원본 구성 요소를 마우스 오른쪽 단추로 클릭한 다음 **편집**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4cc36-115">Right-click the source component and when click **Edit**.</span></span>  
  
3.  <span data-ttu-id="4cc36-116">**연결 관리자**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4cc36-116">Click **Connection Manager**.</span></span>  
  
## <a name="static-options"></a><span data-ttu-id="4cc36-117">정적 옵션</span><span class="sxs-lookup"><span data-stu-id="4cc36-117">Static Options</span></span>  
 <span data-ttu-id="4cc36-118">**캐시 없음**</span><span class="sxs-lookup"><span data-stu-id="4cc36-118">**OLE DB connection manager**</span></span>  
 <span data-ttu-id="4cc36-119">목록에서 기존 연결 관리자를 선택하거나 **새로 만들기**를 클릭하여 새 연결을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="4cc36-119">Select an existing connection manager from the list, or create a new connection by clicking **New**.</span></span>  
  
 <span data-ttu-id="4cc36-120">**새로 만들기**</span><span class="sxs-lookup"><span data-stu-id="4cc36-120">**New**</span></span>  
 <span data-ttu-id="4cc36-121">**OLE DB 연결 관리자 구성** 대화 상자를 사용하여 새 연결 관리자를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="4cc36-121">Create a new connection manager by using the **Configure OLE DB Connection Manager** dialog box.</span></span>  
  
 <span data-ttu-id="4cc36-122">**데이터 액세스 모드**</span><span class="sxs-lookup"><span data-stu-id="4cc36-122">**Data access mode**</span></span>  
 <span data-ttu-id="4cc36-123">원본에서 데이터를 선택하는 방법을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="4cc36-123">Specify the method for selecting data from the source.</span></span>  
  
|<span data-ttu-id="4cc36-124">옵션</span><span class="sxs-lookup"><span data-stu-id="4cc36-124">Option</span></span>|<span data-ttu-id="4cc36-125">Description</span><span class="sxs-lookup"><span data-stu-id="4cc36-125">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="4cc36-126">테이블 또는 뷰</span><span class="sxs-lookup"><span data-stu-id="4cc36-126">Table or view</span></span>|<span data-ttu-id="4cc36-127">OLE DB 데이터 원본에 있는 테이블이나 뷰에서 데이터를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="4cc36-127">Retrieve data from a table or view in the OLE DB data source.</span></span>|  
|<span data-ttu-id="4cc36-128">테이블 이름 또는 뷰 이름 변수</span><span class="sxs-lookup"><span data-stu-id="4cc36-128">Table name or view name variable</span></span>|<span data-ttu-id="4cc36-129">변수에 테이블 또는 뷰 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="4cc36-129">Specify the table or view name in a variable.</span></span><br /><br /> <span data-ttu-id="4cc36-130">**관련 정보:** [패키지에서 변수 사용](../../2014/integration-services/use-variables-in-packages.md)</span><span class="sxs-lookup"><span data-stu-id="4cc36-130">**Related information:** [Use Variables in Packages](../../2014/integration-services/use-variables-in-packages.md)</span></span>|  
|<span data-ttu-id="4cc36-131">SQL 명령</span><span class="sxs-lookup"><span data-stu-id="4cc36-131">SQL command</span></span>|<span data-ttu-id="4cc36-132">SQL 쿼리를 사용하여 OLE DB 데이터 원본에서 데이터를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="4cc36-132">Retrieve data from the OLE DB data source by using a SQL query.</span></span>|  
|<span data-ttu-id="4cc36-133">변수를 사용한 SQL 명령</span><span class="sxs-lookup"><span data-stu-id="4cc36-133">SQL command from variable</span></span>|<span data-ttu-id="4cc36-134">변수에 SQL 쿼리 텍스트를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="4cc36-134">Specify the SQL query text in a variable.</span></span>|  
  
 <span data-ttu-id="4cc36-135">**미리 보기**</span><span class="sxs-lookup"><span data-stu-id="4cc36-135">**Preview**</span></span>  
 <span data-ttu-id="4cc36-136">**데이터 보기** 대화 상자를 사용하여 결과를 미리 봅니다.</span><span class="sxs-lookup"><span data-stu-id="4cc36-136">Preview results by using the **Data View** dialog box.</span></span> <span data-ttu-id="4cc36-137">**미리 보기** 에는 최대 200개의 행이 표시될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4cc36-137">**Preview** can display up to 200 rows.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4cc36-138">데이터를 미리 보면 CLR 사용자 정의 형식의 열에 데이터가 포함되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4cc36-138">When you preview data, columns with a CLR user-defined type do not contain data.</span></span> <span data-ttu-id="4cc36-139">대신 \<value too big to display> 또는 System.Byte[] 값이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="4cc36-139">Instead the values \<value too big to display> or System.Byte[] display.</span></span> <span data-ttu-id="4cc36-140">전자는 SQL OLE DB 공급자를 사용하여 데이터 원본에 액세스하는 경우 표시되고 후자는 &lt; [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Native Client 공급자를 사용하는 경우 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="4cc36-140">The former displays when the data source is accessed using the SQL OLE DB provider, the latter when using the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Native Client provider.</span></span>  
  
## <a name="data-access-mode-dynamic-options"></a><span data-ttu-id="4cc36-141">데이터 액세스 모드 동적 옵션</span><span class="sxs-lookup"><span data-stu-id="4cc36-141">Data Access Mode Dynamic Options</span></span>  
  
### <a name="data-access-mode--table-or-view"></a><span data-ttu-id="4cc36-142">데이터 액세스 모드 = 테이블 또는 뷰</span><span class="sxs-lookup"><span data-stu-id="4cc36-142">Data access mode = Table or view</span></span>  
 <span data-ttu-id="4cc36-143">**테이블 또는 뷰 이름**</span><span class="sxs-lookup"><span data-stu-id="4cc36-143">**Name of the table or the view**</span></span>  
 <span data-ttu-id="4cc36-144">데이터 원본의 사용 가능한 테이블 또는 뷰 목록에서 테이블 또는 뷰 이름을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="4cc36-144">Select the name of the table or view from a list of those available in the data source.</span></span>  
  
### <a name="data-access-mode--table-name-or-view-name-variable"></a><span data-ttu-id="4cc36-145">데이터 액세스 모드 = 테이블 이름 또는 뷰 이름 변수</span><span class="sxs-lookup"><span data-stu-id="4cc36-145">Data access mode = Table name or view name variable</span></span>  
 <span data-ttu-id="4cc36-146">**변수 이름**</span><span class="sxs-lookup"><span data-stu-id="4cc36-146">**Variable name**</span></span>  
 <span data-ttu-id="4cc36-147">테이블 또는 뷰 이름이 포함된 변수를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="4cc36-147">Select the variable that contains the name of the table or view.</span></span>  
  
### <a name="data-access-mode--sql-command"></a><span data-ttu-id="4cc36-148">데이터 액세스 모드 = SQL 명령</span><span class="sxs-lookup"><span data-stu-id="4cc36-148">Data access mode = SQL command</span></span>  
 <span data-ttu-id="4cc36-149">**SQL 명령 텍스트**</span><span class="sxs-lookup"><span data-stu-id="4cc36-149">**SQL command text**</span></span>  
 <span data-ttu-id="4cc36-150">SQL 쿼리 텍스트를 입력하고 **쿼리 작성**을 클릭하여 쿼리를 작성하거나 **찾아보기**를 클릭하여 쿼리 텍스트가 포함된 파일을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="4cc36-150">Enter the text of a SQL query, build the query by clicking **Build Query**, or locate the file that contains the query text by clicking **Browse**.</span></span>  
  
 <span data-ttu-id="4cc36-151">**매개 변수**</span><span class="sxs-lookup"><span data-stu-id="4cc36-151">**Parameters**</span></span>  
 <span data-ttu-id="4cc36-152">쿼리 텍스트에 ?를</span><span class="sxs-lookup"><span data-stu-id="4cc36-152">If you have entered a parameterized query by using ?</span></span> <span data-ttu-id="4cc36-153">매개 변수 자리 표시자로 사용하여 매개 변수가 있는 쿼리를 입력한 경우 **쿼리 매개 변수 설정** 대화 상자를 사용하여 쿼리 입력 매개 변수를 패키지 변수에 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="4cc36-153">as a parameter placeholder in the query text, use the **Set Query Parameters** dialog box to map query input parameters to package variables.</span></span>  
  
 <span data-ttu-id="4cc36-154">**쿼리 작성**</span><span class="sxs-lookup"><span data-stu-id="4cc36-154">**Build query**</span></span>  
 <span data-ttu-id="4cc36-155">**쿼리 작성기** 대화 상자를 사용하여 시각적으로 SQL 쿼리를 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4cc36-155">Use the **Query Builder** dialog box to construct the SQL query visually.</span></span>  
  
 <span data-ttu-id="4cc36-156">**찾아보기**</span><span class="sxs-lookup"><span data-stu-id="4cc36-156">**Browse**</span></span>  
 <span data-ttu-id="4cc36-157">**열기** 대화 상자를 사용하여 SQL 쿼리 텍스트가 포함된 파일을 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4cc36-157">Use the **Open** dialog box to locate the file that contains the text of the SQL query.</span></span>  
  
 <span data-ttu-id="4cc36-158">**쿼리 구문 분석**</span><span class="sxs-lookup"><span data-stu-id="4cc36-158">**Parse query**</span></span>  
 <span data-ttu-id="4cc36-159">쿼리 텍스트의 구문을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="4cc36-159">Verify the syntax of the query text.</span></span>  
  
### <a name="data-access-mode--sql-command-from-variable"></a><span data-ttu-id="4cc36-160">데이터 액세스 모드 = 변수를 사용한 SQL 명령</span><span class="sxs-lookup"><span data-stu-id="4cc36-160">Data access mode = SQL command from variable</span></span>  
 <span data-ttu-id="4cc36-161">**변수 이름**</span><span class="sxs-lookup"><span data-stu-id="4cc36-161">**Variable name**</span></span>  
 <span data-ttu-id="4cc36-162">SQL 쿼리 텍스트가 포함된 변수를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="4cc36-162">Select the variable that contains the text of the SQL query.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4cc36-163">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4cc36-163">See Also</span></span>  
 <span data-ttu-id="4cc36-164">[Integration Services 오류 및 메시지 참조](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="4cc36-164">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="4cc36-165">[OLE DB 원본 편집기 &#40;열 페이지&#41;](../../2014/integration-services/ole-db-source-editor-columns-page.md) </span><span class="sxs-lookup"><span data-stu-id="4cc36-165">[OLE DB Source Editor &#40;Columns Page&#41;](../../2014/integration-services/ole-db-source-editor-columns-page.md) </span></span>  
 <span data-ttu-id="4cc36-166">[원본 편집기 &#40;오류 출력 페이지를 OLE DB&#41;](../../2014/integration-services/ole-db-source-editor-error-output-page.md) </span><span class="sxs-lookup"><span data-stu-id="4cc36-166">[OLE DB Source Editor &#40;Error Output Page&#41;](../../2014/integration-services/ole-db-source-editor-error-output-page.md) </span></span>  
 <span data-ttu-id="4cc36-167">[OLE DB 소스를 사용 하 여 데이터 추출](data-flow/extract-data-by-using-the-ole-db-source.md) </span><span class="sxs-lookup"><span data-stu-id="4cc36-167">[Extract Data by Using the OLE DB Source](data-flow/extract-data-by-using-the-ole-db-source.md) </span></span>  
 [<span data-ttu-id="4cc36-168">OLE DB 연결 관리자</span><span class="sxs-lookup"><span data-stu-id="4cc36-168">OLE DB Connection Manager</span></span>](connection-manager/ole-db-connection-manager.md)  
  
  
