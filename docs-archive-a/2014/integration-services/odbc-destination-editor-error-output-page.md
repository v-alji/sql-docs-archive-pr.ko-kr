---
title: ODBC 대상 편집기 (오류 출력 페이지) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.designer.odbcdest.errorhandling.f1
ms.assetid: 0a743f8d-2a51-4296-9976-8104f5ca22d3
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 475a2e00d67b221ddf05fdd273317fbab5248cd6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734363"
---
# <a name="odbc-destination-editor-error-output-page"></a><span data-ttu-id="789ce-102">ODBC 대상 편집기(오류 출력 페이지)</span><span class="sxs-lookup"><span data-stu-id="789ce-102">ODBC Destination Editor (Error Output Page)</span></span>
  <span data-ttu-id="789ce-103">**ODBC 대상 편집기** 대화 상자의 **오류 출력** 페이지를 사용하여 오류 처리 옵션을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="789ce-103">Use the **Error Output** page of the **ODBC Destination Editor** dialog box to select error handling options.</span></span>  
  
 <span data-ttu-id="789ce-104">ODBC 대상에 대한 자세한 내용은 [ODBC Destination](data-flow/odbc-destination.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="789ce-104">To learn more about the ODBC destination, see [ODBC Destination](data-flow/odbc-destination.md).</span></span>  
  
 <span data-ttu-id="789ce-105">**ODBC 대상 편집기 오류 출력 페이지를 열려면**</span><span class="sxs-lookup"><span data-stu-id="789ce-105">**To open the ODBC Destination Editor Error Output Page**</span></span>  
  
## <a name="task-list"></a><span data-ttu-id="789ce-106">작업 목록</span><span class="sxs-lookup"><span data-stu-id="789ce-106">Task List</span></span>  
  
-   <span data-ttu-id="789ce-107">[!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]에서 ODBC 대상이 있는 [!INCLUDE[ssISCurrent](../includes/ssiscurrent-md.md)] 패키지를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="789ce-107">In [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], open the [!INCLUDE[ssISCurrent](../includes/ssiscurrent-md.md)] package that has the ODBC destination.</span></span>  
  
-   <span data-ttu-id="789ce-108">**데이터 흐름** 탭에서 ODBC 대상을 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="789ce-108">On the **Data Flow** tab, double-click the ODBC destination.</span></span>  
  
-   <span data-ttu-id="789ce-109">**ODBC 대상 편집기**에서 **오류 출력**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="789ce-109">In the **ODBC Destination Editor**, click **Error Output**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="789ce-110">옵션</span><span class="sxs-lookup"><span data-stu-id="789ce-110">Options</span></span>  
  
### <a name="inputoutput"></a><span data-ttu-id="789ce-111">입/출력</span><span class="sxs-lookup"><span data-stu-id="789ce-111">Input/Output</span></span>  
 <span data-ttu-id="789ce-112">데이터 원본의 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="789ce-112">View the name of the data source.</span></span>  
  
### <a name="column"></a><span data-ttu-id="789ce-113">열</span><span class="sxs-lookup"><span data-stu-id="789ce-113">Column</span></span>  
 <span data-ttu-id="789ce-114">사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="789ce-114">Not used.</span></span>  
  
### <a name="error"></a><span data-ttu-id="789ce-115">Error</span><span class="sxs-lookup"><span data-stu-id="789ce-115">Error</span></span>  
 <span data-ttu-id="789ce-116">ODBC 대상에서 흐름 오류를 처리하는 방법을 선택합니다. 오류 무시, 행 리디렉션 또는 구성 요소 실패를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="789ce-116">Select how the ODBC destination should handle errors in a flow: ignore the failure, redirect the row, or fail the component.</span></span>  
  
### <a name="truncation"></a><span data-ttu-id="789ce-117">잘림</span><span class="sxs-lookup"><span data-stu-id="789ce-117">Truncation</span></span>  
 <span data-ttu-id="789ce-118">ODBC 대상에서 흐름 잘림을 처리하는 방법을 선택합니다. 오류 무시, 행 리디렉션 또는 구성 요소 실패를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="789ce-118">Select how the ODBC destination should handle truncation in a flow: ignore the failure, redirect the row, or fail the component.</span></span>  
  
### <a name="description"></a><span data-ttu-id="789ce-119">Description</span><span class="sxs-lookup"><span data-stu-id="789ce-119">Description</span></span>  
 <span data-ttu-id="789ce-120">오류에 대한 설명을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="789ce-120">View a description of the error.</span></span>  
  
### <a name="set-this-value-to-selected-cells"></a><span data-ttu-id="789ce-121">이 값을 선택한 셀에 설정</span><span class="sxs-lookup"><span data-stu-id="789ce-121">Set this value to selected cells</span></span>  
 <span data-ttu-id="789ce-122">오류나 잘림 발생 시 ODBC 대상에서 선택한 모든 셀을 처리하는 방법을 선택합니다. 오류 무시, 행 리디렉션 또는 구성 요소 실패를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="789ce-122">Select how the ODBC destination handles all selected cells when an error or truncation occurs: ignore the failure, redirect the row, or fail the component.</span></span>  
  
### <a name="apply"></a><span data-ttu-id="789ce-123">적용</span><span class="sxs-lookup"><span data-stu-id="789ce-123">Apply</span></span>  
 <span data-ttu-id="789ce-124">선택한 셀에 오류 처리 옵션을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="789ce-124">Apply the error handling options to the selected cells.</span></span>  
  
## <a name="error-handling-options"></a><span data-ttu-id="789ce-125">오류 처리 옵션</span><span class="sxs-lookup"><span data-stu-id="789ce-125">Error Handling Options</span></span>  
 <span data-ttu-id="789ce-126">다음 옵션을 사용하여 ODBC 대상에서 오류 및 잘림을 처리하는 방법을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="789ce-126">You use the following options to configure how the ODBC destination handles errors and truncations.</span></span>  
  
### <a name="fail-component"></a><span data-ttu-id="789ce-127">구성 요소 실패</span><span class="sxs-lookup"><span data-stu-id="789ce-127">Fail Component</span></span>  
 <span data-ttu-id="789ce-128">오류 또는 잘림이 발생하면 데이터 흐름 태스크가 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="789ce-128">The Data Flow task fails when an error or a truncation occurs.</span></span> <span data-ttu-id="789ce-129">기본 동작입니다.</span><span class="sxs-lookup"><span data-stu-id="789ce-129">This is the default behavior.</span></span>  
  
### <a name="ignore-failure"></a><span data-ttu-id="789ce-130">오류 무시</span><span class="sxs-lookup"><span data-stu-id="789ce-130">Ignore Failure</span></span>  
 <span data-ttu-id="789ce-131">오류 또는 잘림이 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="789ce-131">The error or the truncation is ignored.</span></span>  
  
### <a name="redirect-flow"></a><span data-ttu-id="789ce-132">흐름 리디렉션</span><span class="sxs-lookup"><span data-stu-id="789ce-132">Redirect Flow</span></span>  
 <span data-ttu-id="789ce-133">오류 또는 잘림을 발생시키는 행이 ODBC 대상의 오류 출력으로 전송됩니다.</span><span class="sxs-lookup"><span data-stu-id="789ce-133">The row that is causing the error or the truncation is directed to the error output of the ODBC destination.</span></span> <span data-ttu-id="789ce-134">자세한 내용은 ODBC 대상을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="789ce-134">For more information, see ODBC Destination.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="789ce-135">참고 항목</span><span class="sxs-lookup"><span data-stu-id="789ce-135">See Also</span></span>  
 <span data-ttu-id="789ce-136">[ODBC 대상 편집기 &#40;연결 관리자 페이지&#41;](../../2014/integration-services/odbc-destination-editor-connection-manager-page.md) </span><span class="sxs-lookup"><span data-stu-id="789ce-136">[ODBC Destination Editor &#40;Connection Manager Page&#41;](../../2014/integration-services/odbc-destination-editor-connection-manager-page.md) </span></span>  
 [<span data-ttu-id="789ce-137">ODBC 대상 편집기&#40;매핑 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="789ce-137">ODBC Destination Editor &#40;Mappings Page&#41;</span></span>](../../2014/integration-services/odbc-destination-editor-mappings-page.md)  
  
  
