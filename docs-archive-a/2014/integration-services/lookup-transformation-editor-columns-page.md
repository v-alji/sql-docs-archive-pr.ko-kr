---
title: 조회 변환 편집기 (열 페이지) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.lookuptransformation.columns.f1
helpviewer_keywords:
- Lookup Transformation Editor
ms.assetid: 690ffef5-fd59-4e95-a27d-4fcf0d6b1c0b
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b768076d8acbcaef8cbff21783a7697020e027eb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651101"
---
# <a name="lookup-transformation-editor-columns-page"></a><span data-ttu-id="5a55a-102">조회 변환 편집기(열 페이지)</span><span class="sxs-lookup"><span data-stu-id="5a55a-102">Lookup Transformation Editor (Columns Page)</span></span>
  <span data-ttu-id="5a55a-103">**조회 변환 편집기** 대화 상자의 **열** 페이지를 사용하여 원본 테이블과 참조 테이블 간의 조인을 지정하고 참조 테이블에서 조회 열을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5a55a-103">Use the **Columns** page of the **Lookup Transformation Editor** dialog box to specify the join between the source table and the reference table, and to select lookup columns from the reference table.</span></span>  
  
 <span data-ttu-id="5a55a-104">조회 변환에 대한 자세한 내용은 [Lookup Transformation](data-flow/transformations/lookup-transformation.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="5a55a-104">To learn more about the Lookup transformation, see [Lookup Transformation](data-flow/transformations/lookup-transformation.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="5a55a-105">옵션</span><span class="sxs-lookup"><span data-stu-id="5a55a-105">Options</span></span>  
 <span data-ttu-id="5a55a-106">**사용 가능한 입력 열**</span><span class="sxs-lookup"><span data-stu-id="5a55a-106">**Available Input Columns**</span></span>  
 <span data-ttu-id="5a55a-107">사용 가능한 입력 열 목록을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="5a55a-107">View the list of available input columns.</span></span> <span data-ttu-id="5a55a-108">입력 열은 연결된 원본에서 데이터 흐름에 있는 열입니다.</span><span class="sxs-lookup"><span data-stu-id="5a55a-108">The input columns are the columns in the data flow from a connected source.</span></span> <span data-ttu-id="5a55a-109">입력 열과 조회 열의 데이터 형식은 동일해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5a55a-109">The input columns and lookup column must have matching data types.</span></span>  
  
 <span data-ttu-id="5a55a-110">끌어서 놓기 작업을 사용하여 사용 가능한 입력 열을 조회 열에 매핑할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5a55a-110">Use a drag-and-drop operation to map available input columns to lookup columns.</span></span>  
  
 <span data-ttu-id="5a55a-111">또한 키보드로 **사용 가능한 입력 열** 테이블의 열을 강조 표시하고 애플리케이션 키를 누른 다음 **매핑 편집**을 클릭하여 입력 열을 조회 열에 매핑할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5a55a-111">You can also map input columns to lookup columns using the keyboard, by highlighting a column in the **Available Input Columns** table, pressing the Application key, and then clicking **Edit Mappings**.</span></span>  
  
 <span data-ttu-id="5a55a-112">**사용 가능한 조회 열**</span><span class="sxs-lookup"><span data-stu-id="5a55a-112">**Available Lookup Columns**</span></span>  
 <span data-ttu-id="5a55a-113">조회 열 목록을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="5a55a-113">View the list of lookup columns.</span></span> <span data-ttu-id="5a55a-114">조회 열은 입력 열과 일치하는 값을 조회할 참조 테이블의 열입니다.</span><span class="sxs-lookup"><span data-stu-id="5a55a-114">The lookup columns are columns in the reference table in which you want to look up values that match the input columns.</span></span>  
  
 <span data-ttu-id="5a55a-115">끌어서 놓기 작업을 사용하여 사용 가능한 조회 열을 입력 열에 매핑할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5a55a-115">Use a drag-and-drop operation to map available lookup columns to input columns.</span></span>  
  
 <span data-ttu-id="5a55a-116">확인란을 사용하여 조회 작업을 수행할 참조 테이블의 조회 열을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5a55a-116">Use the check boxes to select lookup columns in the reference table on which to perform lookup operations.</span></span>  
  
 <span data-ttu-id="5a55a-117">또한 키보드로 **사용 가능한 조회 열** 테이블의 열을 강조 표시하고 애플리케이션 키를 누른 다음 **매핑 편집**을 클릭하여 조회 열을 입력 열에 매핑할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5a55a-117">You can also map lookup columns to input columns using the keyboard, by highlighting a column in the **Available Lookup Columns** table, pressing the Application key, and then clicking **Edit Mappings**.</span></span>  
  
 <span data-ttu-id="5a55a-118">**조회 열**</span><span class="sxs-lookup"><span data-stu-id="5a55a-118">**Lookup Column**</span></span>  
 <span data-ttu-id="5a55a-119">선택한 조회 열을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="5a55a-119">View the selected lookup columns.</span></span> <span data-ttu-id="5a55a-120">선택 내용에 따라 **사용 가능한 조회 열** 테이블의 확인란이 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="5a55a-120">The selections are reflected in the check box selections in the **Available Lookup Columns** table.</span></span>  
  
 <span data-ttu-id="5a55a-121">**조회 작업**</span><span class="sxs-lookup"><span data-stu-id="5a55a-121">**Lookup Operation**</span></span>  
 <span data-ttu-id="5a55a-122">목록에서 조회 열에 수행할 조회 작업을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="5a55a-122">Select a lookup operation from the list to perform on the lookup column.</span></span>  
  
 <span data-ttu-id="5a55a-123">**출력 별칭**</span><span class="sxs-lookup"><span data-stu-id="5a55a-123">**Output Alias**</span></span>  
 <span data-ttu-id="5a55a-124">각 조회 열에 대한 출력의 별칭을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="5a55a-124">Type an alias for the output for each lookup column.</span></span> <span data-ttu-id="5a55a-125">기본값은 조회 열의 이름이지만 설명이 포함된 고유 이름을 임의로 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5a55a-125">The default is the name of the lookup column; however, you can select any unique, descriptive name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a55a-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5a55a-126">See Also</span></span>  
 <span data-ttu-id="5a55a-127">[조회 변환 편집기 &#40;일반 페이지&#41;](general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="5a55a-127">[Lookup Transformation Editor &#40;General Page&#41;](general-page-of-integration-services-designers-options.md) </span></span>  
 <span data-ttu-id="5a55a-128">[조회 변환 편집기 &#40;연결 페이지&#41;](../../2014/integration-services/lookup-transformation-editor-connection-page.md) </span><span class="sxs-lookup"><span data-stu-id="5a55a-128">[Lookup Transformation Editor &#40;Connection Page&#41;](../../2014/integration-services/lookup-transformation-editor-connection-page.md) </span></span>  
 <span data-ttu-id="5a55a-129">[조회 변환 편집기 &#40;고급 페이지&#41;](../../2014/integration-services/lookup-transformation-editor-advanced-page.md) </span><span class="sxs-lookup"><span data-stu-id="5a55a-129">[Lookup Transformation Editor &#40;Advanced Page&#41;](../../2014/integration-services/lookup-transformation-editor-advanced-page.md) </span></span>  
 <span data-ttu-id="5a55a-130">[조회 변환 편집기 &#40;오류 출력 페이지&#41;](../../2014/integration-services/lookup-transformation-editor-error-output-page.md) </span><span class="sxs-lookup"><span data-stu-id="5a55a-130">[Lookup Transformation Editor &#40;Error Output Page&#41;](../../2014/integration-services/lookup-transformation-editor-error-output-page.md) </span></span>  
 [<span data-ttu-id="5a55a-131">유사 항목 조회 변환</span><span class="sxs-lookup"><span data-stu-id="5a55a-131">Fuzzy Lookup Transformation</span></span>](data-flow/transformations/fuzzy-lookup-transformation.md)  
  
  
