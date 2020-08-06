---
title: CDC 원본 편집기 (오류 출력 페이지) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.designer.cdcsource.errorhandling.f1
ms.assetid: 8a4c2cb8-fd2f-4c45-824f-b93473a8981e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b39532304fddfa90fabe8cafe2a6caf5b1fb5c8b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660094"
---
# <a name="cdc-source-editor-error-output-page"></a><span data-ttu-id="84dd7-102">CDC 원본 편집기(오류 출력 페이지)</span><span class="sxs-lookup"><span data-stu-id="84dd7-102">CDC Source Editor (Error Output Page)</span></span>
  <span data-ttu-id="84dd7-103">**CDC 원본 편집기** 대화 상자의 **오류 출력** 페이지를 사용하여 오류 처리 옵션을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="84dd7-103">Use the **Error Output** page of the **CDC Source Editor** dialog box to select error handling options.</span></span>  
  
 <span data-ttu-id="84dd7-104">CDC 원본에 대한 자세한 내용은 [CDC Source](data-flow/cdc-source.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="84dd7-104">To learn more about the CDC source, see [CDC Source](data-flow/cdc-source.md).</span></span>  
  
## <a name="task-list"></a><span data-ttu-id="84dd7-105">작업 목록</span><span class="sxs-lookup"><span data-stu-id="84dd7-105">Task List</span></span>  
 <span data-ttu-id="84dd7-106">**CDC 원본 편집기 오류 출력 페이지를 열려면**</span><span class="sxs-lookup"><span data-stu-id="84dd7-106">**To open the CDC Source Editor Error Output Page**</span></span>  
  
1.  <span data-ttu-id="84dd7-107">[!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]에서 CDC 원본이 있는 [!INCLUDE[ssISCurrent](../includes/ssiscurrent-md.md)] 패키지를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="84dd7-107">In [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], open the [!INCLUDE[ssISCurrent](../includes/ssiscurrent-md.md)] package that has the CDC source.</span></span>  
  
2.  <span data-ttu-id="84dd7-108">**데이터 흐름** 탭에서 CDC 원본을 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="84dd7-108">On the **Data Flow** tab, double-click the CDC source.</span></span>  
  
3.  <span data-ttu-id="84dd7-109">**CDC 원본 편집기**에서 **오류 출력**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="84dd7-109">In the **CDC Source Editor**, click **Error Output**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="84dd7-110">옵션</span><span class="sxs-lookup"><span data-stu-id="84dd7-110">Options</span></span>  
 <span data-ttu-id="84dd7-111">**입/출력**</span><span class="sxs-lookup"><span data-stu-id="84dd7-111">**Input/Output**</span></span>  
 <span data-ttu-id="84dd7-112">데이터 원본의 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="84dd7-112">View the name of the data source.</span></span>  
  
 <span data-ttu-id="84dd7-113">**열**</span><span class="sxs-lookup"><span data-stu-id="84dd7-113">**Column**</span></span>  
 <span data-ttu-id="84dd7-114">**CDC 원본 편집기** 대화 상자의 **연결 관리자** 페이지에서 선택한 외부(원본) 열을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="84dd7-114">View the external (source) columns that you selected on the **Connection Manager** page of the **CDC Source Editor** dialog box.</span></span>  
  
 <span data-ttu-id="84dd7-115">**오류**</span><span class="sxs-lookup"><span data-stu-id="84dd7-115">**Error**</span></span>  
 <span data-ttu-id="84dd7-116">CDC 원본에서 흐름의 오류를 처리하는 방법을 선택합니다. 오류 무시, 행 리디렉션 또는 구성 요소 실패를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="84dd7-116">Select how the CDC source should handle errors in a flow: ignore the failure, redirect the row, or fail the component.</span></span>  
  
 <span data-ttu-id="84dd7-117">**잘림**</span><span class="sxs-lookup"><span data-stu-id="84dd7-117">**Truncation**</span></span>  
 <span data-ttu-id="84dd7-118">CDC 원본에서 흐름의 잘림을 처리하는 방법을 선택합니다. 오류 무시, 행 리디렉션 또는 구성 요소 실패를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="84dd7-118">Select how the CDC source should handle truncation in a flow: ignore the failure, redirect the row, or fail the component.</span></span>  
  
 <span data-ttu-id="84dd7-119">**설명**</span><span class="sxs-lookup"><span data-stu-id="84dd7-119">**Description**</span></span>  
 <span data-ttu-id="84dd7-120">사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="84dd7-120">Not used.</span></span>  
  
 <span data-ttu-id="84dd7-121">**이 값을 선택한 셀에 설정**</span><span class="sxs-lookup"><span data-stu-id="84dd7-121">**Set this value to selected cells**</span></span>  
 <span data-ttu-id="84dd7-122">오류나 잘림 발생 시 CDC 원본에서 선택한 모든 셀을 처리하는 방법을 선택합니다. 오류 무시, 행 리디렉션 또는 구성 요소 실패를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="84dd7-122">Select how the CDC source handles all selected cells when an error or truncation occurs: ignore the failure, redirect the row, or fail the component.</span></span>  
  
 <span data-ttu-id="84dd7-123">**적용**</span><span class="sxs-lookup"><span data-stu-id="84dd7-123">**Apply**</span></span>  
 <span data-ttu-id="84dd7-124">선택한 셀에 오류 처리 옵션을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="84dd7-124">Apply the error handling options to the selected cells.</span></span>  
  
## <a name="error-handling-options"></a><span data-ttu-id="84dd7-125">오류 처리 옵션</span><span class="sxs-lookup"><span data-stu-id="84dd7-125">Error Handling Options</span></span>  
 <span data-ttu-id="84dd7-126">다음 옵션을 사용하여 CDC 원본에서 오류 및 잘림을 처리하는 방법을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="84dd7-126">You use the following options to configure how the CDC source handles errors and truncations.</span></span>  
  
 <span data-ttu-id="84dd7-127">**구성 요소 실패**</span><span class="sxs-lookup"><span data-stu-id="84dd7-127">**Fail Component**</span></span>  
 <span data-ttu-id="84dd7-128">오류 또는 잘림이 발생하면 데이터 흐름 태스크가 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="84dd7-128">The Data Flow task fails when an error or a truncation occurs.</span></span> <span data-ttu-id="84dd7-129">기본 동작입니다.</span><span class="sxs-lookup"><span data-stu-id="84dd7-129">This is the default behavior.</span></span>  
  
 <span data-ttu-id="84dd7-130">**오류 무시**</span><span class="sxs-lookup"><span data-stu-id="84dd7-130">**Ignore Failure**</span></span>  
 <span data-ttu-id="84dd7-131">오류 또는 잘림이 무시되고 데이터 행이 CDC 원본 출력으로 전달됩니다.</span><span class="sxs-lookup"><span data-stu-id="84dd7-131">The error or the truncation is ignored and the data row is directed to the CDC source output.</span></span>  
  
 <span data-ttu-id="84dd7-132">**흐름 리디렉션**</span><span class="sxs-lookup"><span data-stu-id="84dd7-132">**Redirect Flow**</span></span>  
 <span data-ttu-id="84dd7-133">오류 또는 잘림 데이터 행이 CDC 원본의 오류 출력으로 전달됩니다.</span><span class="sxs-lookup"><span data-stu-id="84dd7-133">The error or the truncation data row is directed to the error output of the CDC source.</span></span> <span data-ttu-id="84dd7-134">이 경우에는 CDC 원본 오류 처리가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="84dd7-134">In this case the CDC source error handling is used.</span></span> <span data-ttu-id="84dd7-135">자세한 내용은 [CDC Source](data-flow/cdc-source.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="84dd7-135">For more information, see [CDC Source](data-flow/cdc-source.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84dd7-136">참고 항목</span><span class="sxs-lookup"><span data-stu-id="84dd7-136">See Also</span></span>  
 <span data-ttu-id="84dd7-137">[CDC 원본 편집기&#40;연결 관리자 페이지&#41;](../../2014/integration-services/cdc-source-editor-connection-manager-page.md) </span><span class="sxs-lookup"><span data-stu-id="84dd7-137">[CDC Source Editor &#40;Connection Manager Page&#41;](../../2014/integration-services/cdc-source-editor-connection-manager-page.md) </span></span>  
 [<span data-ttu-id="84dd7-138">CDC 원본 편집기&#40;열 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="84dd7-138">CDC Source Editor &#40;Columns Page&#41;</span></span>](../../2014/integration-services/cdc-source-editor-columns-page.md)  
  
  
