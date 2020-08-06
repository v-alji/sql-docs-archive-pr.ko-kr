---
title: CDC 원본 편집기 (연결 관리자 페이지) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.designer.cdcsource.connection.f1
ms.assetid: 304e6717-e160-4a7b-a06f-32182449fef8
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 5b0ed4792f13006bb9013771c69053b04539bc0e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660096"
---
# <a name="cdc-source-editor-connection-manager-page"></a><span data-ttu-id="136db-102">CDC 원본 편집기(연결 관리자 페이지)</span><span class="sxs-lookup"><span data-stu-id="136db-102">CDC Source Editor (Connection Manager Page)</span></span>
  <span data-ttu-id="136db-103">**CDC 원본 편집기** 대화 상자의 **연결 관리자** 페이지를 사용하여 CDC 원본이 변경 행을 읽어오는 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] 데이터베이스(CDC 데이터베이스)에 대한 ADO.NET 연결 관리자를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="136db-103">Use the **Connection Manager** page of the **CDC Source Editor** dialog box to select the ADO.NET connection manager for the [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] database that the CDC source reads change rows from (the CDC database).</span></span> <span data-ttu-id="136db-104">CDC 데이터베이스를 선택한 후 데이터베이스에서 캡처된 테이블을 선택해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="136db-104">Once the CDC database is selected you need to select a captured table in the database.</span></span>  
  
 <span data-ttu-id="136db-105">CDC 원본에 대한 자세한 내용은 [CDC Source](data-flow/cdc-source.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="136db-105">For more information about the CDC source, see [CDC Source](data-flow/cdc-source.md).</span></span>  
  
## <a name="task-list"></a><span data-ttu-id="136db-106">작업 목록</span><span class="sxs-lookup"><span data-stu-id="136db-106">Task List</span></span>  
 <span data-ttu-id="136db-107">**CDC 원본 편집기의 연결 관리자 페이지를 열려면**</span><span class="sxs-lookup"><span data-stu-id="136db-107">**To open the CDC Source Editor Connection Manager Page**</span></span>  
  
1.  <span data-ttu-id="136db-108">[!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]에서 CDC 원본이 있는 [!INCLUDE[ssISCurrent](../includes/ssiscurrent-md.md)] 패키지를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="136db-108">In [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], open the [!INCLUDE[ssISCurrent](../includes/ssiscurrent-md.md)] package that has the CDC source.</span></span>  
  
2.  <span data-ttu-id="136db-109">**데이터 흐름** 탭에서 CDC 원본을 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="136db-109">On the **Data Flow** tab, double-click the CDC source.</span></span>  
  
3.  <span data-ttu-id="136db-110">**CDC 원본 편집기**에서 **연결 관리자**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="136db-110">In the **CDC Source Editor**, click **Connection Manager**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="136db-111">옵션</span><span class="sxs-lookup"><span data-stu-id="136db-111">Options</span></span>  
 <span data-ttu-id="136db-112">**ADO.NET 연결 관리자**</span><span class="sxs-lookup"><span data-stu-id="136db-112">**ADO.NET connection manager**</span></span>  
 <span data-ttu-id="136db-113">목록에서 기존 연결 관리자를 선택하거나 **새로 만들기** 를 클릭하여 새 연결을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="136db-113">Select an existing connection manager from the list, or click **New** to create a new connection.</span></span> <span data-ttu-id="136db-114">CDC에 사용할 수 있고 선택한 변경 테이블이 있는 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 데이터베이스에 연결해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="136db-114">The connection must be to a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] database that is enabled for CDC and where the selected change table is located.</span></span>  
  
 <span data-ttu-id="136db-115">**새로 만들기**</span><span class="sxs-lookup"><span data-stu-id="136db-115">**New**</span></span>  
 <span data-ttu-id="136db-116">**새로 만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="136db-116">Click **New**.</span></span> <span data-ttu-id="136db-117">새 연결 관리자를 만들 수 있는 **ADO.NET 연결 관리자 편집기 구성** 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="136db-117">The **Configure ADO.NET Connection Manager Editor** dialog box opens where you can create a new connection manager</span></span>  
  
 <span data-ttu-id="136db-118">**CDC 테이블**</span><span class="sxs-lookup"><span data-stu-id="136db-118">**CDC Table**</span></span>  
 <span data-ttu-id="136db-119">처리하기 위해 읽고 다운스트림 SSIS 구성 요소에 제공하려는 캡처된 변경 내용이 포함된 CDC 원본 테이블을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="136db-119">Select the CDC source table that contains the captured changes that you want read and feed to downstream SSIS components for processing.</span></span>  
  
 <span data-ttu-id="136db-120">**캡처 인스턴스**</span><span class="sxs-lookup"><span data-stu-id="136db-120">**Capture instance**</span></span>  
 <span data-ttu-id="136db-121">읽을 CDC 테이블이 있는 CDC 캡처 인스턴스의 이름을 선택하거나 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="136db-121">Select or type in the name of the CDC capture instance with the CDC table to be read.</span></span>  
  
 <span data-ttu-id="136db-122">캡처된 원본 테이블에는 스키마 변경을 통해 테이블 정의의 원활한 전환을 처리하도록 하나 또는 두 개의 캡처된 인스턴스가 포함되어 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="136db-122">A captured source table can have one or two captured instances to handle seamless transitioning of table definition through schema changes.</span></span> <span data-ttu-id="136db-123">캡처할 원본 테이블에 대해 두 개 이상의 캡처 인스턴스가 정의되어 있으면 여기에서 사용할 캡처 인스턴스를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="136db-123">If more than one capture instance is defined for the source table being captured, select the capture instance you want to use here.</span></span> <span data-ttu-id="136db-124">[schema].[table] 테이블의 기본 캡처 인스턴스 이름은 \<schema>_\<table>이지만 실제로 사용 중인 캡처 인스턴스 이름은 다를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="136db-124">The default capture instance name for a table [schema].[table] is \<schema>_\<table> but that actual capture instance names in use may be different.</span></span> <span data-ttu-id="136db-125">실제로 읽어 들인 테이블은 CDC 테이블인 **cdc .\<capture-instance>_CT**입니다.</span><span class="sxs-lookup"><span data-stu-id="136db-125">The actual table that is read from is the CDC table **cdc .\<capture-instance>_CT**.</span></span>  
  
 <span data-ttu-id="136db-126">**CDC 처리 모드**</span><span class="sxs-lookup"><span data-stu-id="136db-126">**CDC Processing Mode**</span></span>  
 <span data-ttu-id="136db-127">처리 요구를 처리할 최적의 처리 모드를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="136db-127">Select the processing mode that best handles your processing needs.</span></span> <span data-ttu-id="136db-128">가능한 옵션은 아래와 같습니다.</span><span class="sxs-lookup"><span data-stu-id="136db-128">The possible options are:</span></span>  
  
-   <span data-ttu-id="136db-129">**모두**: **업데이트 전** 값이 없는 현재 CDC 범위의 변경 내용을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="136db-129">**All**: Returns the changes in the current CDC range without the **Before Update** values.</span></span>  
  
-   <span data-ttu-id="136db-130">**이전 값이 포함된 모두**: 이전 값(**업데이트 전**)을 포함한 현재 CDC 처리 범위의 변경 내용을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="136db-130">**All with old values**: Returns the changes in the current CDC processing range including the old values (**Before Update**).</span></span> <span data-ttu-id="136db-131">각 업데이트 작업에 대해 두 행이 있습니다. 이 중 한 행에는 업데이트 전 값이 포함되어 있고 다른 한 행에는 업데이트 후 값이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="136db-131">For each Update operation, there will be two rows, one with the before-update values and one with the after-update value.</span></span>  
  
-   <span data-ttu-id="136db-132">**순 변경 내용**: 현재 CDC 처리 범위에서 수정된 원본 행당 하나의 변경 행만 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="136db-132">**Net**: Returns only one change row per source row modified in the current CDC processing range.</span></span> <span data-ttu-id="136db-133">원본 행이 여러 번 업데이트된 경우에는 결합된 변경 내용이 생성됩니다. 예를 들어 삽입+업데이트는 단일 업데이트로 생성되고 업데이트+삭제는 단일 삭제로 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="136db-133">If a source row was updated multiple times, the combined change is produced (for example, insert+update is produced as a single update and update+delete is produced as a single delete).</span></span> <span data-ttu-id="136db-134">순 변경 내용 처리 모드에서 작업할 경우 단일 원본 행이 두 개 이상의 출력에 나타나므로 변경 내용을 삭제, 삽입 및 업데이트 출력으로 분할하고 해당 출력을 병렬로 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="136db-134">When working in Net change processing mode, it is possible to split the changes to Delete, Insert and Update outputs and handle them in parallel because the single source row appears in more than one output.</span></span>  
  
-   <span data-ttu-id="136db-135">**업데이트 마스크를 사용한 순 변경 내용**: 이 모드는 일반적인 순 변경 내용 모드와 비슷하지만 현재 변경 행에서 변경된 열을 나타내고 이름 패턴이 **__$\<column-name>\__Changed**인 부울 열도 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="136db-135">**Net with update mask**: This mode is similar to the regular Net mode but it also adds boolean columns with the name pattern **__$\<column-name>\__Changed** that indicate changed columns in the current change row.</span></span>  
  
-   <span data-ttu-id="136db-136">**병합을 사용한 순 변경 내용**: 이 모드는 일반적인 순 변경 내용 모드와 비슷하지만 삽입 및 업데이트 작업을 사용할 경우 단일 병합 작업으로 병합됩니다(UPSERT).</span><span class="sxs-lookup"><span data-stu-id="136db-136">**Net with merge**: This mode is similar to the regular Net mode but with Insert and Update operations merged into a single Merge operation (UPSERT).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="136db-137">모든 순 변경 내용 옵션의 경우 원본 테이블에 기본 키 또는 고유 인덱스가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="136db-137">For all Net change options, the source table must have a primary key or unique index.</span></span> <span data-ttu-id="136db-138">기본 키 또는 고유 인덱스가 없는 테이블의 경우에는 **모두** 옵션을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="136db-138">For tables without a primary key or unique indes, you must yse the **All** option.</span></span>  
  
 <span data-ttu-id="136db-139">**CDC 상태를 포함하는 변수**</span><span class="sxs-lookup"><span data-stu-id="136db-139">**Variable containing the CDC state**</span></span>  
 <span data-ttu-id="136db-140">현재 CDC 컨텍스트에 대한 CDC 상태를 유지 관리하는 SSIS 문자열 패키지 변수를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="136db-140">Select the SSIS string package variable that maintains the CDC state for the current CDC context.</span></span> <span data-ttu-id="136db-141">CDC 상태 변수에 대한 자세한 내용은 [상태 변수 정의](data-flow/define-a-state-variable.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="136db-141">For more information about the CDC state variable, see [Define a State Variable](data-flow/define-a-state-variable.md).</span></span>  
  
 <span data-ttu-id="136db-142">**재처리 표시기 열 포함**</span><span class="sxs-lookup"><span data-stu-id="136db-142">**Include reprocessing indicator column**</span></span>  
 <span data-ttu-id="136db-143">**__$reprocessing**이라는 특수 출력 열을 만들려면 이 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="136db-143">Select this check box to create a special output column called **__$reprocessing**.</span></span>  
  
 <span data-ttu-id="136db-144">CDC 처리 범위가 초기 처리 범위(초기 로드 기간에 해당하는 LSN의 범위)와 겹치거나 이전 실행의 오류 발생 후 CDC 처리 범위가 다시 처리되는 경우 이 열 값은 **true** 입니다.</span><span class="sxs-lookup"><span data-stu-id="136db-144">This column has a value of **true** when the CDC processing range overlaps with the initial processing range (the range of LSNs corresponding to the period of initial load) or when a CDC processing range is reprocessed following an error in a previous run.</span></span> <span data-ttu-id="136db-145">이 표시기 열을 사용하면 변경 내용을 다시 처리할 때 SSIS 개발자가 오류를 다르게 처리할 수 있습니다. 예를 들어 존재하지 않는 행의 삭제와 중복 키에 대해 실패한 삽입과 같은 동작은 무시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="136db-145">This indicator column lets the SSIS developer handle errors differently when reprocessing changes (for example, actions such as a delete of a non-existing row and an insert that failed on a duplicate key can be ignored).</span></span>  
  
 <span data-ttu-id="136db-146">자세한 내용은 [CDC Source Custom Properties](data-flow/cdc-source-custom-properties.md)을(를) 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="136db-146">For more information, see [CDC Source Custom Properties](data-flow/cdc-source-custom-properties.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="136db-147">참고 항목</span><span class="sxs-lookup"><span data-stu-id="136db-147">See Also</span></span>  
 <span data-ttu-id="136db-148">[CDC 원본 편집기&#40;열 페이지&#41;](../../2014/integration-services/cdc-source-editor-columns-page.md) </span><span class="sxs-lookup"><span data-stu-id="136db-148">[CDC Source Editor &#40;Columns Page&#41;](../../2014/integration-services/cdc-source-editor-columns-page.md) </span></span>  
 [<span data-ttu-id="136db-149">CDC 원본 편집기&#40;오류 출력 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="136db-149">CDC Source Editor &#40;Error Output Page&#41;</span></span>](../../2014/integration-services/cdc-source-editor-error-output-page.md)  
  
  
