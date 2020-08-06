---
title: 유사 항목 조회 변환 편집기 (열 탭) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.fuzzylookuptransformation.columns.f1
helpviewer_keywords:
- Fuzzy Lookup Transformation Editor
ms.assetid: aaf45327-79e9-4760-9b4d-546ace91b5b4
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f9294022b52536940916a381d7b811437eaa5814
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87729627"
---
# <a name="fuzzy-lookup-transformation-editor-columns-tab"></a><span data-ttu-id="ae1e9-102">유사 항목 조회 변환 편집기(열 탭)</span><span class="sxs-lookup"><span data-stu-id="ae1e9-102">Fuzzy Lookup Transformation Editor (Columns Tab)</span></span>
  <span data-ttu-id="ae1e9-103">**유사 항목 조회 변환 편집기** 대화 상자의 **열** 탭을 사용하여 입력 및 출력 열의 속성을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ae1e9-103">Use the **Columns** tab of the **Fuzzy Lookup Transformation Editor** dialog box to set properties for input and output columns.</span></span>  
  
 <span data-ttu-id="ae1e9-104">유사 항목 조회 변환에 대한 자세한 내용은 [Fuzzy Lookup Transformation](data-flow/transformations/lookup-transformation.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="ae1e9-104">To learn more about the Fuzzy Lookup transformation, see [Fuzzy Lookup Transformation](data-flow/transformations/lookup-transformation.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="ae1e9-105">옵션</span><span class="sxs-lookup"><span data-stu-id="ae1e9-105">Options</span></span>  
 <span data-ttu-id="ae1e9-106">**사용 가능한 입력 열**</span><span class="sxs-lookup"><span data-stu-id="ae1e9-106">**Available Input Columns**</span></span>  
 <span data-ttu-id="ae1e9-107">입력 열을 사용 가능한 조회 열로 끌어 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="ae1e9-107">Drag input columns to connect them to available lookup columns.</span></span> <span data-ttu-id="ae1e9-108">이러한 열에는 일치하며 지원되는 데이터 형식이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ae1e9-108">These columns must have matching, supported data types.</span></span> <span data-ttu-id="ae1e9-109">매핑 선을 선택하고 마우스 오른쪽 단추를 클릭하여 [관계 만들기](data-flow/transformations/create-relationships.md) 대화 상자에서 매핑을 편집합니다.</span><span class="sxs-lookup"><span data-stu-id="ae1e9-109">Select a mapping line and right-click to edit the mappings in the [Create Relationships](data-flow/transformations/create-relationships.md) dialog box.</span></span>  
  
 <span data-ttu-id="ae1e9-110">**이름**</span><span class="sxs-lookup"><span data-stu-id="ae1e9-110">**Name**</span></span>  
 <span data-ttu-id="ae1e9-111">사용 가능한 입력 열의 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="ae1e9-111">View the names of the available input columns.</span></span>  
  
 <span data-ttu-id="ae1e9-112">**통과**</span><span class="sxs-lookup"><span data-stu-id="ae1e9-112">**Pass Through**</span></span>  
 <span data-ttu-id="ae1e9-113">입력 열을 변환의 출력에 포함할지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ae1e9-113">Specify whether to include the input columns in the output of the transformation.</span></span>  
  
 <span data-ttu-id="ae1e9-114">**사용 가능한 조회 열**</span><span class="sxs-lookup"><span data-stu-id="ae1e9-114">**Available Lookup Columns**</span></span>  
 <span data-ttu-id="ae1e9-115">확인란을 사용하여 유사 항목 조회 작업을 수행할 열을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ae1e9-115">Use the check boxes to select columns on which to perform fuzzy lookup operations.</span></span>  
  
 <span data-ttu-id="ae1e9-116">**조회 열**</span><span class="sxs-lookup"><span data-stu-id="ae1e9-116">**Lookup Column**</span></span>  
 <span data-ttu-id="ae1e9-117">사용 가능한 참조 테이블 열 목록에서 조회 열을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ae1e9-117">Select lookup columns from the list of available reference table columns.</span></span> <span data-ttu-id="ae1e9-118">선택 내용에 따라 **사용 가능한 조회 열** 테이블의 확인란이 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="ae1e9-118">Your selections are reflected in the check box selections in the **Available Lookup Columns** table.</span></span> <span data-ttu-id="ae1e9-119">**사용 가능한 조회 열** 테이블에서 열을 선택하면 반환된 일치하는 각 행에 대한 참조 테이블 열 값이 포함된 출력 열이 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="ae1e9-119">Selecting a column in the **Available Lookup Columns** table creates an output column that contains the reference table column value for each matching row returned.</span></span>  
  
 <span data-ttu-id="ae1e9-120">**출력 별칭**</span><span class="sxs-lookup"><span data-stu-id="ae1e9-120">**Output Alias**</span></span>  
 <span data-ttu-id="ae1e9-121">각 조회 열에 대한 출력의 별칭을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="ae1e9-121">Type an alias for the output for each lookup column.</span></span> <span data-ttu-id="ae1e9-122">기본값은 추가된 숫자 인덱스 값이 있는 조회 열의 이름이지만 설명이 포함된 고유 이름을 임의로 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ae1e9-122">The default is the name of the lookup column with a numeric index value appended; however, you can choose any unique, descriptive name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae1e9-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ae1e9-123">See Also</span></span>  
 <span data-ttu-id="ae1e9-124">[Integration Services 오류 및 메시지 참조](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="ae1e9-124">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="ae1e9-125">[유사 항목 조회 변환 편집기 &#40;참조 테이블 탭&#41;](../../2014/integration-services/fuzzy-lookup-transformation-editor-reference-table-tab.md) </span><span class="sxs-lookup"><span data-stu-id="ae1e9-125">[Fuzzy Lookup Transformation Editor &#40;Reference Table Tab&#41;](../../2014/integration-services/fuzzy-lookup-transformation-editor-reference-table-tab.md) </span></span>  
 [<span data-ttu-id="ae1e9-126">유사 항목 조회 변환 편집기&#40;고급 탭&#41;</span><span class="sxs-lookup"><span data-stu-id="ae1e9-126">Fuzzy Lookup Transformation Editor &#40;Advanced Tab&#41;</span></span>](../../2014/integration-services/fuzzy-lookup-transformation-editor-advanced-tab.md)  
  
  
