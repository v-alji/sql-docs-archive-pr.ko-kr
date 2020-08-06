---
title: OLE DB 연결 관리자를 사용 하 여 전체 캐시 모드에서 조회 변환 구현 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Lookup transformation [Integration Services]
ms.assetid: c4150e1b-bdff-4f7a-af4c-3401c34def83
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f77a753dd71bc487d57492371906fc48bc114357
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659610"
---
# <a name="implement-a-lookup-transformation-in-full-cache-mode-using-the-ole-db-connection-manager"></a><span data-ttu-id="91dbd-102">OLE DB 연결 관리자를 사용하여 전체 캐시 모드에서 조회 변환 구현</span><span class="sxs-lookup"><span data-stu-id="91dbd-102">Implement a Lookup Transformation in Full Cache Mode Using the OLE DB Connection Manager</span></span>
  <span data-ttu-id="91dbd-103">전체 캐시 모드와 OLE DB 연결 관리자를 사용하도록 조회 변환을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="91dbd-103">You can configure the Lookup transformation to use full cache mode and an OLE DB connection manager.</span></span> <span data-ttu-id="91dbd-104">전체 캐시 모드에서는 조회 변환이 실행되기 전에 참조 데이터 세트가 캐시에 로드됩니다.</span><span class="sxs-lookup"><span data-stu-id="91dbd-104">In the full cache mode, the reference dataset is loaded into cache before the Lookup transformation runs.</span></span>  
  
 <span data-ttu-id="91dbd-105">조회 변환은 연결된 데이터 원본의 입력 열에 있는 데이터를 참조 데이터 세트의 열과 조인하여 조회합니다.</span><span class="sxs-lookup"><span data-stu-id="91dbd-105">The Lookup transformation performs lookups by joining data in input columns from a connected data source with columns in a reference dataset.</span></span> <span data-ttu-id="91dbd-106">자세한 내용은 [Lookup Transformation](../data-flow/transformations/lookup-transformation.md)을(를) 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="91dbd-106">For more information, see [Lookup Transformation](../data-flow/transformations/lookup-transformation.md).</span></span>  
  
 <span data-ttu-id="91dbd-107">OLE DB 연결 관리자를 사용하도록 조회 변환을 구성할 때 참조 데이터 세트를 생성할 테이블, 뷰 또는 SQL 쿼리를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="91dbd-107">When you configure the Lookup transformation to use an OLE DB connection manager, you select a table, view, or SQL query to generate the reference dataset.</span></span>  
  
### <a name="to-implement-a-lookup-transformation-in-full-cache-mode-by-using-ole-db-connection-manager"></a><span data-ttu-id="91dbd-108">OLE DB 연결 관리자를 사용하여 전체 캐시 모드에서 조회 변환을 구현하려면</span><span class="sxs-lookup"><span data-stu-id="91dbd-108">To implement a Lookup transformation in full cache mode by using OLE DB connection manager</span></span>  
  
1.  <span data-ttu-id="91dbd-109">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]에서 원하는 패키지가 들어 있는 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 프로젝트를 열고 솔루션 탐색기에서 패키지를 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="91dbd-109">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] project that contains the package you want, and then double-click the package in Solution Explorer.</span></span>  
  
2.  <span data-ttu-id="91dbd-110">**데이터 흐름** 탭의 **도구 상자**에서 조회 변환을 디자인 화면으로 끌어 옵니다.</span><span class="sxs-lookup"><span data-stu-id="91dbd-110">On the **Data Flow** tab, from the **Toolbox**, drag the Lookup transformation to the design surface.</span></span>  
  
3.  <span data-ttu-id="91dbd-111">원본이나 이전 변환에서 연결선을 조회 변환으로 끌어서 조회 변환을 데이터 흐름에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="91dbd-111">Connect the Lookup transformation to the data flow by dragging a connector from a source or a previous transformation to the Lookup transformation.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="91dbd-112">조회 변환이 빈 데이터 필드가 포함된 플랫 파일에 연결되면 이러한 조회 변환의 유효성을 검사하지 못할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="91dbd-112">A Lookup transformation might not validate if that transformation connects to a flat file that contains an empty date field.</span></span> <span data-ttu-id="91dbd-113">변환의 유효성 검사 여부는 플랫 파일의 연결 관리자가 Null 값을 유지하도록 구성되었는지 여부에 따라 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="91dbd-113">Whether the transformation validates depends on whether the connection manager for the flat file has been configured to retain null values.</span></span> <span data-ttu-id="91dbd-114">조회 변환의 유효성 검사가 수행되도록 하려면 **플랫 파일 원본 편집기**의 **연결 관리자 페이지**에서 **원본의 Null 값을 데이터 흐름의 Null 값으로 유지** 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="91dbd-114">To ensure that the Lookup transformation validates, in the **Flat File Source Editor**, on the **Connection Manager Page**, select the **Retain null values from the source as null values in the data flow** option.</span></span>  
  
4.  <span data-ttu-id="91dbd-115">원본이나 이전 변환을 두 번 클릭하여 구성 요소를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="91dbd-115">Double-click the source or previous transformation to configure the component.</span></span>  
  
5.  <span data-ttu-id="91dbd-116">조회 변환을 두 번 클릭한 다음 **조회 변환 편집기**의 **일반** 페이지에서 **전체 캐시**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="91dbd-116">Double-click the Lookup transformation, and then in the **Lookup Transformation Editor**, on the **General** page, select **Full cache**.</span></span>  
  
6.  <span data-ttu-id="91dbd-117">**연결 형식** 영역에서 **OLE DB 연결 관리자**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="91dbd-117">In the **Connection type** area, select **OLE DB connection manager**.</span></span>  
  
7.  <span data-ttu-id="91dbd-118">**일치하는 항목이 없는 행 처리 방법 지정** 목록에서 일치하는 항목이 없는 행에 대한 오류 처리 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="91dbd-118">In the **Specify how to handle rows with no matching entries** list, select an error handling option for rows without matching entries.</span></span>  
  
8.  <span data-ttu-id="91dbd-119">연결 페이지에서, **OLE DB 연결 관리자** 목록에서 연결 관리자를 선택하거나 **새로 만들기** 를 클릭하여 새 연결 관리자를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="91dbd-119">On the Connection page, select a connection manager from the **OLE DB connection manager** list or click **New** to create a new connection manager.</span></span> <span data-ttu-id="91dbd-120">자세한 내용은 [OLE DB Connection Manager](ole-db-connection-manager.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="91dbd-120">For more information, see [OLE DB Connection Manager](ole-db-connection-manager.md).</span></span>  
  
9. <span data-ttu-id="91dbd-121">다음 태스크 중 하나를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="91dbd-121">Do one of the following tasks:</span></span>  
  
    -   <span data-ttu-id="91dbd-122">**테이블 또는 뷰 사용**을 클릭한 다음 테이블이나 뷰를 선택하거나, **새로 만들기** 를 클릭하여 테이블이나 뷰를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="91dbd-122">Click **Use a table or a view**, and then either select a table or view, or click **New** to create a table or view.</span></span>  
  
         <span data-ttu-id="91dbd-123">또는</span><span class="sxs-lookup"><span data-stu-id="91dbd-123">-or-</span></span>  
  
    -   <span data-ttu-id="91dbd-124">**SQL 쿼리 결과 사용**을 클릭한 후 **SQL 명령** 창에서 쿼리를 작성하거나 **쿼리 작성** 을 클릭하여 **쿼리 작성기** 에서 제공하는 그래픽 도구를 사용하여 쿼리를 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="91dbd-124">Click **Use results of an SQL query**, and then build a query in the **SQL Command** window, or click **Build Query** to build a query by using the graphical tools that the **Query Builder** provides.</span></span>  
  
         <span data-ttu-id="91dbd-125">또는</span><span class="sxs-lookup"><span data-stu-id="91dbd-125">-or-</span></span>  
  
    -   <span data-ttu-id="91dbd-126">또는 **찾아보기** 를 클릭하여 파일에서 SQL 문을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="91dbd-126">Alternatively, click **Browse** to import an SQL statement from a file.</span></span>  
  
     <span data-ttu-id="91dbd-127">SQL 쿼리의 유효성을 검사하려면 **쿼리 구문 분석**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="91dbd-127">To validate the SQL query, click **Parse Query**.</span></span>  
  
     <span data-ttu-id="91dbd-128">데이터 예제를 보려면 **미리 보기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="91dbd-128">To view a sample of the data, click **Preview**.</span></span>  
  
10. <span data-ttu-id="91dbd-129">**열** 페이지를 클릭한 다음 **사용 가능한 입력 열** 목록에 있는 하나 이상의 열을 **사용 가능한 조회 열** 목록에 있는 열로 끌어 옵니다.</span><span class="sxs-lookup"><span data-stu-id="91dbd-129">Click the **Columns** page, and then from the **Available Input Columns** list, drag at least one column to a column in the **Available Lookup Column** list.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="91dbd-130">조회 변환은 이름과 데이터 형식이 같은 열을 자동으로 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="91dbd-130">The Lookup transformation automatically maps columns that have the same name and the same data type.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="91dbd-131">열을 매핑하려면 데이터 형식이 일치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="91dbd-131">Columns must have matching data types to be mapped.</span></span> <span data-ttu-id="91dbd-132">자세한 내용은 [Integration Services Data Types](../data-flow/integration-services-data-types.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="91dbd-132">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>  
  
11. <span data-ttu-id="91dbd-133">다음 태스크를 수행하여 출력에 조회 열을 포함시킵니다.</span><span class="sxs-lookup"><span data-stu-id="91dbd-133">Include lookup columns in the output by doing the following tasks:</span></span>  
  
    1.  <span data-ttu-id="91dbd-134">**사용 가능한 조회 열** 목록에서</span><span class="sxs-lookup"><span data-stu-id="91dbd-134">In the **Available Lookup Columns** list.</span></span> <span data-ttu-id="91dbd-135">열을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="91dbd-135">select columns.</span></span>  
  
    2.  <span data-ttu-id="91dbd-136">**조회 작업** 목록에서 조회 열의 값으로 입력 열의 값을 교체하거나 새 열에 기록할지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="91dbd-136">In **Lookup Operation** list, specify whether the values from the lookup columns replace values in the input column or are written to a new column.</span></span>  
  
12. <span data-ttu-id="91dbd-137">오류 출력을 구성하려면 **오류 출력** 페이지를 클릭하고 오류 처리 옵션을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="91dbd-137">To configure the error output, click the **Error Output** page and set the error handling options.</span></span> <span data-ttu-id="91dbd-138">자세한 내용은 [조회 변환 편집기&#40;오류 출력 페이지&#41;](../lookup-transformation-editor-error-output-page.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="91dbd-138">For more information, see [Lookup Transformation Editor &#40;Error Output Page&#41;](../lookup-transformation-editor-error-output-page.md).</span></span>  
  
13. <span data-ttu-id="91dbd-139">조회 변환의 변경 내용을 저장한 다음 패키지를 실행하려면 **확인** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="91dbd-139">Click **OK** to save your changes to the Lookup transformation, and then run the package.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91dbd-140">참고 항목</span><span class="sxs-lookup"><span data-stu-id="91dbd-140">See Also</span></span>  
 <span data-ttu-id="91dbd-141">[캐시 연결 관리자 변환을 사용하여 전체 캐시 모드에서 조회 변환 구현](lookup-transformation-full-cache-mode-ole-db-connection-manager.md) </span><span class="sxs-lookup"><span data-stu-id="91dbd-141">[Implement a Lookup Transformation in Full Cache Mode Using the Cache Connection Manager](lookup-transformation-full-cache-mode-ole-db-connection-manager.md) </span></span>  
 <span data-ttu-id="91dbd-142">[캐시 없음 또는 부분 캐시 모드로 조회 구현](../data-flow/transformations/implement-a-lookup-in-no-cache-or-partial-cache-mode.md) </span><span class="sxs-lookup"><span data-stu-id="91dbd-142">[Implement a Lookup in No Cache or Partial Cache Mode](../data-flow/transformations/implement-a-lookup-in-no-cache-or-partial-cache-mode.md) </span></span>  
 [<span data-ttu-id="91dbd-143">Integration Services 변환</span><span class="sxs-lookup"><span data-stu-id="91dbd-143">Integration Services Transformations</span></span>](../data-flow/transformations/integration-services-transformations.md)  
  
  
