---
title: CDC 원본을 사용하여 변경 데이터 추출 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 604fbafb-15fa-4d11-8487-77d7b626eed8
author: chugugrace
ms.author: chugu
ms.openlocfilehash: ef981a22e286f519c9b93b3181b47df43321548b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742443"
---
# <a name="extract-change-data-using-the-cdc-source"></a><span data-ttu-id="ed48d-102">CDC 원본을 사용하여 변경 데이터 추출</span><span class="sxs-lookup"><span data-stu-id="ed48d-102">Extract Change Data Using the CDC Source</span></span>
  <span data-ttu-id="ed48d-103">CDC 원본을 추가 및 구성하려면 패키지에 적어도 하나 이상의 데이터 흐름 태스크와 하나의 CDC 제어 태스크가 이미 들어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ed48d-103">To add and configure a CDC source, the package must already include at least one Data Flow task and a CDC Control task.</span></span>  
  
 <span data-ttu-id="ed48d-104">CDC 제어 태스크에 대한 자세한 내용은 [CDC Control Task](../control-flow/cdc-control-task.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="ed48d-104">For more information about the CDC Control task, see [CDC Control Task](../control-flow/cdc-control-task.md).</span></span>  
  
 <span data-ttu-id="ed48d-105">CDC 원본에 대한 자세한 내용은 [CDC Source](cdc-source.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="ed48d-105">For more information about the CDC source, see [CDC Source](cdc-source.md).</span></span>  
  
### <a name="to-extract-change-data-using-a-cdc-source"></a><span data-ttu-id="ed48d-106">CDC 원본을 사용하여 변경 데이터를 추출하려면</span><span class="sxs-lookup"><span data-stu-id="ed48d-106">To extract change data using a CDC source</span></span>  
  
1.  <span data-ttu-id="ed48d-107">[!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]에서 원하는 패키지가 들어 있는 [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] 프로젝트를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="ed48d-107">In [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], open the [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="ed48d-108">솔루션 탐색기에서 패키지를 두 번 클릭하여 엽니다.</span><span class="sxs-lookup"><span data-stu-id="ed48d-108">In the Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="ed48d-109">**데이터 흐름** 탭을 클릭한 다음 **도구 상자**에서 CDC 원본을 디자인 화면으로 끌어 옵니다.</span><span class="sxs-lookup"><span data-stu-id="ed48d-109">Click the **Data Flow** tab, and then from the **Toolbox**, drag the CDC source to the design surface.</span></span>  
  
4.  <span data-ttu-id="ed48d-110">CDC 원본을 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ed48d-110">Double-click the CDC source.</span></span>  
  
5.  <span data-ttu-id="ed48d-111">**CDC 원본 편집기** 대화 상자의 **연결 관리자** 페이지에 있는 목록에서 기존 ADO.NET 연결 관리자를 선택하거나 **새로 만들기** 를 클릭하여 새 연결을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ed48d-111">In the **CDC Source Editor** dialog box, on the **Connection Manager** page, select an existing ADO.NET connection manager from the list, or click **New** to create a new connection.</span></span> <span data-ttu-id="ed48d-112">연결은 읽을 변경 테이블을 포함하는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스에 대한 연결이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ed48d-112">The connection should be to a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database that contains the change tables to read.</span></span>  
  
6.  <span data-ttu-id="ed48d-113">변경 내용을 처리할 **CDC 테이블** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ed48d-113">Select the **CDC table** where you want to process changes.</span></span>  
  
7.  <span data-ttu-id="ed48d-114">읽을 CDC 테이블이 있는 **CDC 캡처 인스턴스** 의 이름을 선택하거나 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="ed48d-114">Select or type in the name of the **CDC capture instance** with the CDC table to be read.</span></span>  
  
     <span data-ttu-id="ed48d-115">캡처된 원본 테이블에는 스키마 변경을 통해 테이블 정의의 원활한 전환을 처리하도록 하나 또는 두 개의 캡처된 인스턴스가 포함되어 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ed48d-115">A captured source table can have one or two captured instances to handle seamless transitioning of table definition through schema changes.</span></span> <span data-ttu-id="ed48d-116">캡처할 원본 테이블에 대해 두 개 이상의 캡처 인스턴스가 정의되어 있으면 여기에서 사용할 캡처 인스턴스를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ed48d-116">If more than one capture instance is defined for the source table being captured, select the capture instance you want to use here.</span></span> <span data-ttu-id="ed48d-117">[schema].[table] 테이블의 기본 캡처 인스턴스 이름은 \<schema>_\<table>이지만 실제로 사용 중인 캡처 인스턴스 이름은 다를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ed48d-117">The default capture instance name for a table [schema].[table] is \<schema>_\<table> but that actual capture instance names in use may be different.</span></span> <span data-ttu-id="ed48d-118">실제로 읽어 들인 테이블은 CDC 테이블인 **cdc .\<capture-instance>_CT**입니다.</span><span class="sxs-lookup"><span data-stu-id="ed48d-118">The actual table that is read from is the CDC table **cdc .\<capture-instance>_CT**.</span></span>  
  
8.  <span data-ttu-id="ed48d-119">처리 요구를 처리할 최적의 처리 모드를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ed48d-119">Select the processing mode that best handles your processing needs.</span></span> <span data-ttu-id="ed48d-120">가능한 옵션은 아래와 같습니다.</span><span class="sxs-lookup"><span data-stu-id="ed48d-120">The possible options are:</span></span>  
  
    -   <span data-ttu-id="ed48d-121">**모두**: **업데이트 전** 값이 없는 현재 CDC 범위의 변경 내용을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="ed48d-121">**All**: Returns the changes in the current CDC range without the **Before Update** values.</span></span>  
  
    -   <span data-ttu-id="ed48d-122">**이전 값이 포함된 모두**: 이전 값(**업데이트 전**)을 포함한 현재 CDC 처리 범위의 변경 내용을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="ed48d-122">**All with old values**: Returns the changes in the current CDC processing range including the old values (**Before Update**).</span></span> <span data-ttu-id="ed48d-123">각 업데이트 작업에 대해 두 행이 있습니다. 이 중 한 행에는 업데이트 전 값이 포함되어 있고 다른 한 행에는 업데이트 후 값이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ed48d-123">For each Update operation, there will be two rows, one with the before-update values and one with the after-update value.</span></span>  
  
    -   <span data-ttu-id="ed48d-124">**순 변경 내용**: 현재 CDC 처리 범위에서 수정된 원본 행당 하나의 변경 행만 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="ed48d-124">**Net**: Returns only one change row per source row modified in the current CDC processing range.</span></span> <span data-ttu-id="ed48d-125">원본 행이 여러 번 업데이트된 경우에는 결합된 변경 내용이 생성됩니다. 예를 들어 삽입+업데이트는 단일 업데이트로 생성되고 업데이트+삭제는 단일 삭제로 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="ed48d-125">If a source row was updated multiple times, the combined change is produced (for example, insert+update is produced as a single update and update+delete is produced as a single delete).</span></span> <span data-ttu-id="ed48d-126">순 변경 내용 처리 모드에서 작업할 경우 단일 원본 행이 두 개 이상의 출력에 나타나므로 변경 내용을 삭제, 삽입 및 업데이트 출력으로 분할하고 해당 출력을 병렬로 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ed48d-126">When working in Net change processing mode, it is possible to split the changes to Delete, Insert and Update outputs and handle them in parallel because the single source row appears in more than one output.</span></span>  
  
    -   <span data-ttu-id="ed48d-127">**업데이트 마스크를 사용한 순 변경 내용**: 이 모드는 일반적인 순 변경 내용 모드와 비슷하지만 현재 변경 행에서 변경된 열을 나타내고 이름 패턴이 **__$\<column-name>\__Changed**인 부울 열도 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="ed48d-127">**Net with update mask**: This mode is similar to the regular Net mode but it also adds boolean columns with the name pattern **__$\<column-name>\__Changed** that indicate changed columns in the current change row.</span></span>  
  
    -   <span data-ttu-id="ed48d-128">**병합을 사용한 순 변경 내용**: 이 모드는 일반적인 순 변경 내용 모드와 비슷하지만 삽입 및 업데이트 작업을 사용할 경우 단일 병합 작업으로 병합됩니다(UPSERT).</span><span class="sxs-lookup"><span data-stu-id="ed48d-128">**Net with merge**: This mode is similar to the regular Net mode but with Insert and Update operations merged into a single Merge operation (UPSERT).</span></span>  
  
9. <span data-ttu-id="ed48d-129">현재 CDC 컨텍스트에 대한 CDC 상태를 유지 관리하는 SSIS 문자열 패키지 변수를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ed48d-129">Select the SSIS string package variable that maintains the CDC state for the current CDC context.</span></span> <span data-ttu-id="ed48d-130">CDC 상태 변수에 대한 자세한 내용은 [상태 변수 정의](define-a-state-variable.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ed48d-130">For more information about the CDC state variable, see [Define a State Variable](define-a-state-variable.md).</span></span>  
  
10. <span data-ttu-id="ed48d-131">**__$reprocessing** 이라는 특수 출력 열을 만들려면 **재처리 표시기 열 포함**확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ed48d-131">Select the **Include reprocessing indicator column** check box to create a special output column called **__$reprocessing**.</span></span> <span data-ttu-id="ed48d-132">CDC 처리 범위가 초기 처리 범위(초기 로드 기간에 해당하는 LSN의 범위)와 겹치거나 이전 실행의 오류 발생 후 CDC 처리 범위가 다시 처리되는 경우 이 열 값은 **true** 입니다.</span><span class="sxs-lookup"><span data-stu-id="ed48d-132">This column has a value of **true** when the CDC processing range overlaps with the initial processing range (the range of LSNs corresponding to the period of initial load) or when a CDC processing range is reprocessed following an error in a previous run.</span></span> <span data-ttu-id="ed48d-133">이 표시기 열을 사용하면 변경 내용을 다시 처리할 때 SSIS 개발자가 오류를 다르게 처리할 수 있습니다. 예를 들어 존재하지 않는 행의 삭제와 중복 키에 대해 실패한 삽입과 같은 동작은 무시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ed48d-133">This indicator column lets the SSIS developer handle errors differently when reprocessing changes (for example, actions such as a delete of a non-existing row and an insert that failed on a duplicate key can be ignored).</span></span>  
  
     <span data-ttu-id="ed48d-134">자세한 내용은 [CDC Source Custom Properties](cdc-source-custom-properties.md)을(를) 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ed48d-134">For more information, see [CDC Source Custom Properties](cdc-source-custom-properties.md).</span></span>  
  
11. <span data-ttu-id="ed48d-135">외부 및 출력 열 사이의 매핑을 업데이트하려면 **열** 을 클릭하고 **외부 열** 목록에서 다른 열을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ed48d-135">To update the mapping between external and output columns, click **Columns** and select different columns in the **External Column** list.</span></span>  
  
12. <span data-ttu-id="ed48d-136">필요에 따라 **출력 열** 목록에서 값을 삭제하여 출력 열의 값을 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="ed48d-136">Optionally update the values of the output columns by deleting values in the **Output Column** list.</span></span>  
  
13. <span data-ttu-id="ed48d-137">오류 출력을 구성하려면 **오류 출력**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ed48d-137">To configure the error output, click **Error Output**.</span></span>  
  
14. <span data-ttu-id="ed48d-138">**미리 보기** 를 클릭하면 CDC 원본에 의해 추출된 최대 200개의 데이터 행을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ed48d-138">You can click **Preview** to view up to 200 rows of data extracted by the CDC source.</span></span>  
  
15. <span data-ttu-id="ed48d-139">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ed48d-139">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed48d-140">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ed48d-140">See Also</span></span>  
 <span data-ttu-id="ed48d-141">[CDC 원본 편집기&#40;연결 관리자 페이지&#41;](../cdc-source-editor-connection-manager-page.md) </span><span class="sxs-lookup"><span data-stu-id="ed48d-141">[CDC Source Editor &#40;Connection Manager Page&#41;](../cdc-source-editor-connection-manager-page.md) </span></span>  
 <span data-ttu-id="ed48d-142">[CDC 원본 편집기&#40;열 페이지&#41;](../cdc-source-editor-columns-page.md) </span><span class="sxs-lookup"><span data-stu-id="ed48d-142">[CDC Source Editor &#40;Columns Page&#41;](../cdc-source-editor-columns-page.md) </span></span>  
 [<span data-ttu-id="ed48d-143">CDC 원본 편집기&#40;오류 출력 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="ed48d-143">CDC Source Editor &#40;Error Output Page&#41;</span></span>](../cdc-source-editor-error-output-page.md)  
  
  
