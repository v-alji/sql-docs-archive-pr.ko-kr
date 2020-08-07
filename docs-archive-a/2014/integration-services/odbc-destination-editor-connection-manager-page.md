---
title: ODBC 대상 편집기 (연결 관리자 페이지) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.designer.odbcdest.connection.f1
ms.assetid: f6d9c6c2-e4c4-468b-9e0d-af7b9609614d
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 6e4fc1073bb187c0864d2991459a358a7f81d066
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734364"
---
# <a name="odbc-destination-editor-connection-manager-page"></a><span data-ttu-id="1ca52-102">ODBC 대상 편집기(연결 관리자 페이지)</span><span class="sxs-lookup"><span data-stu-id="1ca52-102">ODBC Destination Editor (Connection Manager Page)</span></span>
  <span data-ttu-id="1ca52-103">**ODBC 대상 편집기** 대화 상자의 **연결 관리자** 페이지를 사용하여 대상에 대한 ODBC 연결 관리자를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1ca52-103">Use the **Connection Manager** page of the **ODBC Destination Editor** dialog box to select the ODBC connection manager for the destination.</span></span> <span data-ttu-id="1ca52-104">이 페이지를 사용하면 데이터베이스에서 테이블이나 뷰를 선택할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1ca52-104">This page also lets you select a table or view from the database</span></span>  
  
 <span data-ttu-id="1ca52-105">ODBC 대상에 대한 자세한 내용은 [ODBC Destination](data-flow/odbc-destination.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="1ca52-105">For more information about the ODBC destination, see [ODBC Destination](data-flow/odbc-destination.md).</span></span>  
  
 <span data-ttu-id="1ca52-106">**ODBC 대상 편집기의 연결 관리자 페이지를 열려면**</span><span class="sxs-lookup"><span data-stu-id="1ca52-106">**To open the ODBC Destination Editor Connection Manager Page**</span></span>  
  
## <a name="task-list"></a><span data-ttu-id="1ca52-107">작업 목록</span><span class="sxs-lookup"><span data-stu-id="1ca52-107">Task List</span></span>  
  
-   <span data-ttu-id="1ca52-108">[!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]에서 ODBC 대상이 있는 [!INCLUDE[ssISCurrent](../includes/ssiscurrent-md.md)] 패키지를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="1ca52-108">In [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], open the [!INCLUDE[ssISCurrent](../includes/ssiscurrent-md.md)] package that has the ODBC destination.</span></span>  
  
-   <span data-ttu-id="1ca52-109">**데이터 흐름** 탭에서 ODBC 대상을 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1ca52-109">On the **Data Flow** tab, double-click the ODBC destination.</span></span>  
  
-   <span data-ttu-id="1ca52-110">**ODBC 대상 편집기**에서 **연결 관리자**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1ca52-110">In the **ODBC Destination Editor**, click **Connection Manager**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="1ca52-111">옵션</span><span class="sxs-lookup"><span data-stu-id="1ca52-111">Options</span></span>  
  
### <a name="connection-manager"></a><span data-ttu-id="1ca52-112">ODBC 대상 편집기</span><span class="sxs-lookup"><span data-stu-id="1ca52-112">Connection manager</span></span>  
 <span data-ttu-id="1ca52-113">목록에서 기존 ODBC 연결 관리자를 선택하거나 새로 만들기를 클릭하여 새 연결을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="1ca52-113">Select an existing ODBC connection manager from the list, or click New to create a new connection.</span></span> <span data-ttu-id="1ca52-114">어느 ODBC 지원 데이터베이스에나 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1ca52-114">The connection can be to any ODBC-supported database.</span></span>  
  
### <a name="new"></a><span data-ttu-id="1ca52-115">새로 만들기</span><span class="sxs-lookup"><span data-stu-id="1ca52-115">New</span></span>  
 <span data-ttu-id="1ca52-116">**새로 만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1ca52-116">Click **New**.</span></span> <span data-ttu-id="1ca52-117">새 연결 관리자를 만들 수 있는 **ODBC 연결 관리자 편집기 구성** 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="1ca52-117">The **Configure ODBC Connection Manager Editor** dialog box opens where you can create a new connection manager.</span></span>  
  
### <a name="data-access-mode"></a><span data-ttu-id="1ca52-118">데이터 액세스 모드</span><span class="sxs-lookup"><span data-stu-id="1ca52-118">Data Access Mode</span></span>  
 <span data-ttu-id="1ca52-119">대상으로 데이터를 로드하는 방법을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="1ca52-119">Select the method for loading data to the destination.</span></span> <span data-ttu-id="1ca52-120">옵션은 다음 표에 표시되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1ca52-120">The options are shown in the following table:</span></span>  
  
|<span data-ttu-id="1ca52-121">옵션</span><span class="sxs-lookup"><span data-stu-id="1ca52-121">Option</span></span>|<span data-ttu-id="1ca52-122">Description</span><span class="sxs-lookup"><span data-stu-id="1ca52-122">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="1ca52-123">테이블 이름 - 일괄 처리</span><span class="sxs-lookup"><span data-stu-id="1ca52-123">Table Name - Batch</span></span>|<span data-ttu-id="1ca52-124">일괄 처리 모드에서 작업하도록 ODBC 대상을 구성하려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="1ca52-124">Select this option to configure the ODBC destination to work in batch mode.</span></span> <span data-ttu-id="1ca52-125">이 옵션을 선택하면 다음 옵션을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1ca52-125">When you select this option the following options are available:</span></span>|  
||<span data-ttu-id="1ca52-126">**테이블 또는 뷰 이름**: 목록에서 사용 가능한 테이블이나 뷰를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="1ca52-126">**Name of the table or the view**: Select an available table or view from the list.</span></span><br /><br /> <span data-ttu-id="1ca52-127">이 목록에는 처음 1000개의 테이블만 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1ca52-127">This list contains the first 1000 tables only.</span></span> <span data-ttu-id="1ca52-128">데이터베이스에 포함되어 있는 테이블이 1000개를 넘는 경우 테이블 이름의 시작 부분을 입력하거나 와일드카드(\*)를 통해 이름의 일부를 입력하여 사용할 테이블을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="1ca52-128">If your database contains more than 1000 tables, you can type the beginning of a table name or use the (\*) wild card to enter any part of the name to display the table or tables you want to use.</span></span><br /><br /> <span data-ttu-id="1ca52-129">**일괄 처리 크기**: 대량 로드에 대한 일괄 처리 크기를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="1ca52-129">**Batch size**: Type the size of the batch for bulk loading.</span></span> <span data-ttu-id="1ca52-130">일괄 처리로 로드되는 행의 개수입니다.</span><span class="sxs-lookup"><span data-stu-id="1ca52-130">This is the number of rows loaded as a batch</span></span>|  
|<span data-ttu-id="1ca52-131">테이블 이름 - 행 단위</span><span class="sxs-lookup"><span data-stu-id="1ca52-131">Table Name - Row by Row</span></span>|<span data-ttu-id="1ca52-132">각 행을 한 번에 하나씩 대상 테이블에 삽입하도록 ODBC 대상을 구성하려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="1ca52-132">Select this option to configure the ODBC destination to insert each of the rows into the destination table one at a time.</span></span> <span data-ttu-id="1ca52-133">이 옵션을 선택하면 다음 옵션을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1ca52-133">When you select this option the following option is available:</span></span>|  
||<span data-ttu-id="1ca52-134">**테이블 또는 뷰 이름**: 목록의 데이터베이스에서 사용 가능한 테이블이나 뷰를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="1ca52-134">**Name of the table or the view**: Select an available table or view from the database from the list.</span></span><br /><br /> <span data-ttu-id="1ca52-135">이 목록에는 처음 1000개의 테이블만 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1ca52-135">This list contains the first 1000 tables only.</span></span> <span data-ttu-id="1ca52-136">데이터베이스에 포함되어 있는 테이블이 1000개를 넘는 경우 테이블 이름의 시작 부분을 입력하거나 와일드카드(\*)를 통해 이름의 일부를 입력하여 사용할 테이블을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="1ca52-136">If your database contains more than 1000 tables, you can type the beginning of a table name or use the (\*) wild card to enter any part of the name to display the table or tables you want to use.</span></span>|  
  
### <a name="preview"></a><span data-ttu-id="1ca52-137">미리 보기</span><span class="sxs-lookup"><span data-stu-id="1ca52-137">Preview</span></span>  
 <span data-ttu-id="1ca52-138">**미리 보기** 를 클릭하면 선택한 테이블의 데이터 행을 최대 200개까지 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1ca52-138">Click **Preview** to view up to 200 rows of data for the table that you selected.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ca52-139">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1ca52-139">See Also</span></span>  
 <span data-ttu-id="1ca52-140">[ODBC 대상 사용자 지정 속성](data-flow/odbc-destination-custom-properties.md) </span><span class="sxs-lookup"><span data-stu-id="1ca52-140">[ODBC Destination Custom Properties](data-flow/odbc-destination-custom-properties.md) </span></span>  
 <span data-ttu-id="1ca52-141">[ODBC 대상 편집기 &#40;매핑 페이지&#41;](../../2014/integration-services/odbc-destination-editor-mappings-page.md) </span><span class="sxs-lookup"><span data-stu-id="1ca52-141">[ODBC Destination Editor &#40;Mappings Page&#41;](../../2014/integration-services/odbc-destination-editor-mappings-page.md) </span></span>  
 [<span data-ttu-id="1ca52-142">ODBC 대상 편집기&#40;오류 출력 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="1ca52-142">ODBC Destination Editor &#40;Error Output Page&#41;</span></span>](../../2014/integration-services/odbc-destination-editor-error-output-page.md)  
  
  
