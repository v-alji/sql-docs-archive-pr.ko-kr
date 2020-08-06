---
title: 관계 만들기 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.createrelationships.f1
ms.assetid: 6ebd305f-ffd2-4a1d-b24c-e28c151b94f5
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 5a1095e193587ae7d416311031e5297a035ca37e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648457"
---
# <a name="create-relationships"></a><span data-ttu-id="15d32-102">관계 만들기</span><span class="sxs-lookup"><span data-stu-id="15d32-102">Create Relationships</span></span>
  <span data-ttu-id="15d32-103">**관계 만들기** 대화 상자를 사용하여 유사 항목 조회 변환 편집기, 조회 변환 편집기 및 용어 조회 변환 편집기에서 구성한 원본 열과 조회 테이블 열 간의 매핑을 편집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15d32-103">Use the **Create Relationships** dialog box to edit mappings between the source columns and the lookup table columns that you configured in the Fuzzy Lookup Transformation Editor, the Lookup Transformation Editor, and the Term Lookup Transformation Editor.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="15d32-104">용어 조회 변환 편집기에서 호출하는 경우 **관계 만들기** 대화 상자는 **입력 열** 및 **조회 열** 목록만 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="15d32-104">The **Create Relationships** dialog box displays only the **Input Column** and **Lookup Column** lists when invoked from the Term Lookup Transformation Editor.</span></span>  
  
 <span data-ttu-id="15d32-105">**관계 만들기** 대화 상자를 사용하는 변환에 대한 자세한 내용은 [Fuzzy Lookup Transformation](lookup-transformation.md), [Lookup Transformation](lookup-transformation.md)및 [Term Lookup Transformation](term-lookup-transformation.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="15d32-105">To learn more about the transformations that use the **Create Relationships** dialog box, see [Fuzzy Lookup Transformation](lookup-transformation.md), [Lookup Transformation](lookup-transformation.md), and [Term Lookup Transformation](term-lookup-transformation.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="15d32-106">옵션</span><span class="sxs-lookup"><span data-stu-id="15d32-106">Options</span></span>  
 <span data-ttu-id="15d32-107">**입력 열**</span><span class="sxs-lookup"><span data-stu-id="15d32-107">**Input Column**</span></span>  
 <span data-ttu-id="15d32-108">사용 가능한 입력 열 목록에서 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="15d32-108">Select from the list of available input columns.</span></span>  
  
 <span data-ttu-id="15d32-109">**조회 열**</span><span class="sxs-lookup"><span data-stu-id="15d32-109">**Lookup Column**</span></span>  
 <span data-ttu-id="15d32-110">사용 가능한 조회 열 목록에서 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="15d32-110">Select from the list of available lookup columns.</span></span>  
  
 <span data-ttu-id="15d32-111">**매핑 유형**</span><span class="sxs-lookup"><span data-stu-id="15d32-111">**Mapping Type**</span></span>  
 <span data-ttu-id="15d32-112">유사 항목 일치 또는 정확히 일치를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="15d32-112">Select fuzzy or exact matching.</span></span>  
  
 <span data-ttu-id="15d32-113">유사 항목 일치를 사용하는 경우 행이 유사 항목 일치 유형이 있는 모든 열에서 충분히 유사하면 중복으로 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="15d32-113">When you use fuzzy matching, rows are considered duplicates if they are sufficiently similar across all columns that have a fuzzy match type.</span></span> <span data-ttu-id="15d32-114">유사 항목 일치에서 더 정확한 결과를 얻으려면 일부 열에서 유사 항목 일치 대신 정확히 일치를 사용하도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="15d32-114">To obtain better results from fuzzy matching, you can specify that some columns should use exact matching instead of fuzzy matching.</span></span> <span data-ttu-id="15d32-115">예를 들어 특정 열에 오류 또는 불일치가 없는 경우 해당 열에 정확히 일치를 지정하여 이 열에서 값이 동일한 행만 중복일 가능성이 있는 것으로 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15d32-115">For example, if you know that a certain column contains no errors or inconsistencies, you can specify exact matching on that column, so that only rows which contain identical values in this column are considered as possible duplicates.</span></span> <span data-ttu-id="15d32-116">이렇게 하면 다른 열에서의 유사 항목 일치 정확도가 증가합니다.</span><span class="sxs-lookup"><span data-stu-id="15d32-116">This increases the accuracy of fuzzy matching on other columns.</span></span>  
  
 <span data-ttu-id="15d32-117">**비교 플래그**</span><span class="sxs-lookup"><span data-stu-id="15d32-117">**Comparison Flags**</span></span>  
 <span data-ttu-id="15d32-118">문자열 비교 옵션에 대한 자세한 내용은 [문자열 데이터 비교](../comparing-string-data.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="15d32-118">For information about the string comparison options, see [Comparing String Data](../comparing-string-data.md).</span></span>  
  
 <span data-ttu-id="15d32-119">**최소 유사성**</span><span class="sxs-lookup"><span data-stu-id="15d32-119">**Minimum Similarity**</span></span>  
 <span data-ttu-id="15d32-120">슬라이더를 사용하여 열 수준에서 유사성 임계값을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="15d32-120">Set the similarity threshold at the column level by using the slider.</span></span> <span data-ttu-id="15d32-121">값이 1에 가까울수록 조회 값과 원본 값이 근접하여 일치 항목으로 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="15d32-121">The closer the value is to 1, the more the lookup value must resemble the source value to qualify as a match.</span></span> <span data-ttu-id="15d32-122">임계값을 높이면 고려할 레코드 수가 감소하기 때문에 비교 속도를 향상시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15d32-122">Increasing the threshold can improve the speed of matching because fewer candidate records have to be considered.</span></span>  
  
 <span data-ttu-id="15d32-123">**유사성 출력 별칭**</span><span class="sxs-lookup"><span data-stu-id="15d32-123">**Similarity Output Alias**</span></span>  
 <span data-ttu-id="15d32-124">선택한 열에 대한 유사성 점수를 포함하는 새 출력 열의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="15d32-124">Specify the name for a new output column that contains the similarity scores for the selected column.</span></span> <span data-ttu-id="15d32-125">이 값을 비워 놓으면 출력 열이 생성되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="15d32-125">If you leave this value empty, the output column is not created.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15d32-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="15d32-126">See Also</span></span>  
 <span data-ttu-id="15d32-127">[Integration Services 오류 및 메시지 참조](../../integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="15d32-127">[Integration Services Error and Message Reference](../../integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="15d32-128">[유사 항목 조회 변환 편집기&#40;열 탭&#41;](../../fuzzy-lookup-transformation-editor-columns-tab.md) </span><span class="sxs-lookup"><span data-stu-id="15d32-128">[Fuzzy Lookup Transformation Editor &#40;Columns Tab&#41;](../../fuzzy-lookup-transformation-editor-columns-tab.md) </span></span>  
 <span data-ttu-id="15d32-129">[조회 변환 편집기&#40;열 페이지&#41;](../../lookup-transformation-editor-columns-page.md) </span><span class="sxs-lookup"><span data-stu-id="15d32-129">[Lookup Transformation Editor &#40;Columns Page&#41;](../../lookup-transformation-editor-columns-page.md) </span></span>  
 [<span data-ttu-id="15d32-130">용어 조회 변환 편집기&#40;용어 조회 탭&#41;</span><span class="sxs-lookup"><span data-stu-id="15d32-130">Term Lookup Transformation Editor &#40;Term Lookup Tab&#41;</span></span>](../../term-lookup-transformation-editor-term-lookup-tab.md)  
  
  
