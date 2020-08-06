---
title: 용어 추출 변환 편집기 (고급 탭) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.termextraction.advanced.f1
helpviewer_keywords:
- Term Extraction Transformation Editor
ms.assetid: 87118281-6e3c-499e-bac4-fa4c24bb12c6
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f4be56f8ac2deeab49e43071a07894a466019287
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734288"
---
# <a name="term-extraction-transformation-editor-advanced-tab"></a><span data-ttu-id="346fb-102">용어 추출 변환 편집기(고급 탭)</span><span class="sxs-lookup"><span data-stu-id="346fb-102">Term Extraction Transformation Editor (Advanced Tab)</span></span>
  <span data-ttu-id="346fb-103">**용어 추출 변환 편집기** 대화 상자의 **고급** 탭을 사용하여 빈도, 길이 및 단어 또는 구 추출 여부와 같은 추출에 대한 속성을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="346fb-103">Use the **Advanced** tab of the **Term Extraction Transformation Editor** dialog box to specify properties for the extraction such as frequency, length, and whether to extract words or phrases.</span></span>  
  
 <span data-ttu-id="346fb-104">용어 추출 변환에 대한 자세한 내용은 [Term Extraction Transformation](data-flow/transformations/term-extraction-transformation.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="346fb-104">To learn more about the Term Extraction transformation, see [Term Extraction Transformation](data-flow/transformations/term-extraction-transformation.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="346fb-105">옵션</span><span class="sxs-lookup"><span data-stu-id="346fb-105">Options</span></span>  
 <span data-ttu-id="346fb-106">**명사**</span><span class="sxs-lookup"><span data-stu-id="346fb-106">**Noun**</span></span>  
 <span data-ttu-id="346fb-107">변환에서 개별 명사만 추출하도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="346fb-107">Specify that the transformation extracts individual nouns only.</span></span>  
  
 <span data-ttu-id="346fb-108">**명사구**</span><span class="sxs-lookup"><span data-stu-id="346fb-108">**Noun phrase**</span></span>  
 <span data-ttu-id="346fb-109">변환에서 명사구만 추출하도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="346fb-109">Specify that the transformation extracts noun phrases only.</span></span>  
  
 <span data-ttu-id="346fb-110">**명사 및 명사구**</span><span class="sxs-lookup"><span data-stu-id="346fb-110">**Noun and noun phrase**</span></span>  
 <span data-ttu-id="346fb-111">변환에서 명사 및 명사구를 모두 추출하도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="346fb-111">Specify that the transformation extracts both nouns and noun phrases.</span></span>  
  
 <span data-ttu-id="346fb-112">**빈도**</span><span class="sxs-lookup"><span data-stu-id="346fb-112">**Frequency**</span></span>  
 <span data-ttu-id="346fb-113">점수를 용어의 빈도로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="346fb-113">Specify that the score is the frequency of the term.</span></span>  
  
 <span data-ttu-id="346fb-114">**TFIDF**</span><span class="sxs-lookup"><span data-stu-id="346fb-114">**TFIDF**</span></span>  
 <span data-ttu-id="346fb-115">점수를 용어의 TFIDF 값으로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="346fb-115">Specify that the score is the TFIDF value of the term.</span></span> <span data-ttu-id="346fb-116">TFIDF 점수는 TF(용어 빈도)와 IDF(역 문서 빈도)의 곱으로, 용어 T의 TFIDF = (T의 빈도) \* log((입력의 행 수)/(T를 포함하는 행 수))와 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="346fb-116">The TFIDF score is the product of Term Frequency and Inverse Document Frequency, defined as: TFIDF of a Term T = (frequency of T) \* log( (#rows in Input) / (#rows having T) )</span></span>  
  
 <span data-ttu-id="346fb-117">**빈도 임계값**</span><span class="sxs-lookup"><span data-stu-id="346fb-117">**Frequency threshold**</span></span>  
 <span data-ttu-id="346fb-118">단어 또는 구를 추출할 때까지 발생해야 하는 횟수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="346fb-118">Specify the number of times a word or phrase must occur before extracting it.</span></span> <span data-ttu-id="346fb-119">기본값은 2입니다.</span><span class="sxs-lookup"><span data-stu-id="346fb-119">The default value is 2.</span></span>  
  
 <span data-ttu-id="346fb-120">**최대 용어 길이**</span><span class="sxs-lookup"><span data-stu-id="346fb-120">**Maximum length of term**</span></span>  
 <span data-ttu-id="346fb-121">단어 구의 최대 길이를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="346fb-121">Specify the maximum length of a phrase in words.</span></span> <span data-ttu-id="346fb-122">이 옵션은 명사구에만 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="346fb-122">This option affects noun phrases only.</span></span> <span data-ttu-id="346fb-123">기본 값은 12입니다.</span><span class="sxs-lookup"><span data-stu-id="346fb-123">The default value is 12.</span></span>  
  
 <span data-ttu-id="346fb-124">**대/소문자 구분 용어 추출 사용**</span><span class="sxs-lookup"><span data-stu-id="346fb-124">**Use case-sensitive term extraction**</span></span>  
 <span data-ttu-id="346fb-125">추출 시 대/소문자 구분 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="346fb-125">Specify whether to make the extraction case-sensitive.</span></span> <span data-ttu-id="346fb-126">기본값은 `False`입니다.</span><span class="sxs-lookup"><span data-stu-id="346fb-126">The default is `False`.</span></span>  
  
 <span data-ttu-id="346fb-127">**오류 출력 구성**</span><span class="sxs-lookup"><span data-stu-id="346fb-127">**Configure Error Output**</span></span>  
 <span data-ttu-id="346fb-128">[오류 출력 구성](../../2014/integration-services/configure-error-output.md) 대화 상자를 사용하여 오류 발생의 원인이 되는 행에 대한 오류 처리를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="346fb-128">Use the [Configure Error Output](../../2014/integration-services/configure-error-output.md) dialog box to specify error handling for rows that cause errors.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="346fb-129">참고 항목</span><span class="sxs-lookup"><span data-stu-id="346fb-129">See Also</span></span>  
 <span data-ttu-id="346fb-130">[Integration Services 오류 및 메시지 참조](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="346fb-130">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="346fb-131">[용어 추출 변환 편집기 &#40;용어 추출 탭&#41;](../../2014/integration-services/term-extraction-transformation-editor-term-extraction-tab.md) </span><span class="sxs-lookup"><span data-stu-id="346fb-131">[Term Extraction Transformation Editor &#40;Term Extraction Tab&#41;](../../2014/integration-services/term-extraction-transformation-editor-term-extraction-tab.md) </span></span>  
 <span data-ttu-id="346fb-132">[용어 추출 변환 편집기 &#40;제외 탭&#41;](../../2014/integration-services/term-extraction-transformation-editor-exclusion-tab.md) </span><span class="sxs-lookup"><span data-stu-id="346fb-132">[Term Extraction Transformation Editor &#40;Exclusion Tab&#41;](../../2014/integration-services/term-extraction-transformation-editor-exclusion-tab.md) </span></span>  
 [<span data-ttu-id="346fb-133">용어 조회 변환</span><span class="sxs-lookup"><span data-stu-id="346fb-133">Term Lookup Transformation</span></span>](data-flow/transformations/lookup-transformation.md)  
  
  
