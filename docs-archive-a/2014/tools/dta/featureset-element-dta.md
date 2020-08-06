---
title: FeatureSet 요소 (DTA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- FeatureSet element
ms.assetid: f2070c53-4a5c-4c11-ac38-96ee200c84f0
author: stevestein
ms.author: sstein
ms.openlocfilehash: d36c28b24a56ef2dcdf69578fb7e8c196306a416
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737287"
---
# <a name="featureset-element-dta"></a><span data-ttu-id="074d8-102">FeatureSet 요소(DTA)</span><span class="sxs-lookup"><span data-stu-id="074d8-102">FeatureSet Element (DTA)</span></span>
  <span data-ttu-id="074d8-103">데이터베이스 엔진 튜닝 관리자에서 분석 도중에 사용하도록 할 물리적 디자인 구조(인덱스 또는 인덱싱된 뷰)를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="074d8-103">Contains the physical design structures (indexes or indexed views) that you would like Database Engine Tuning Advisor to use during analysis.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="074d8-104">구문</span><span class="sxs-lookup"><span data-stu-id="074d8-104">Syntax</span></span>  
  
```  
  
<DTAInput>  
...code removed...  
    <TuningOptions>  
      <FeatureSet>...</FeatureSet>  
```  
  
## <a name="element-characteristics"></a><span data-ttu-id="074d8-105">요소 특징</span><span class="sxs-lookup"><span data-stu-id="074d8-105">Element Characteristics</span></span>  
  
|<span data-ttu-id="074d8-106">특성</span><span class="sxs-lookup"><span data-stu-id="074d8-106">Characteristic</span></span>|<span data-ttu-id="074d8-107">Description</span><span class="sxs-lookup"><span data-stu-id="074d8-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="074d8-108">**데이터 형식 및 길이**</span><span class="sxs-lookup"><span data-stu-id="074d8-108">**Data type and length**</span></span>|<span data-ttu-id="074d8-109">`string`, 최대 길이 없음</span><span class="sxs-lookup"><span data-stu-id="074d8-109">`string`, no maximum length.</span></span>|  
|<span data-ttu-id="074d8-110">**허용된 값**</span><span class="sxs-lookup"><span data-stu-id="074d8-110">**Allowed values**</span></span>|<span data-ttu-id="074d8-111">**IDX_IV**</span><span class="sxs-lookup"><span data-stu-id="074d8-111">**IDX_IV**</span></span><br /> <span data-ttu-id="074d8-112">인덱스와 인덱싱된 뷰</span><span class="sxs-lookup"><span data-stu-id="074d8-112">Indexes and indexed views.</span></span><br /><br /> <span data-ttu-id="074d8-113">**IDX**</span><span class="sxs-lookup"><span data-stu-id="074d8-113">**IDX**</span></span><br /> <span data-ttu-id="074d8-114">인덱스만</span><span class="sxs-lookup"><span data-stu-id="074d8-114">Indexes only.</span></span><br /><br /> <span data-ttu-id="074d8-115">**IV**</span><span class="sxs-lookup"><span data-stu-id="074d8-115">**IV**</span></span><br /> <span data-ttu-id="074d8-116">인덱싱된 뷰만</span><span class="sxs-lookup"><span data-stu-id="074d8-116">Indexed views only.</span></span><br /><br /> <span data-ttu-id="074d8-117">**NCL_IDX**</span><span class="sxs-lookup"><span data-stu-id="074d8-117">**NCL_IDX**</span></span><br /> <span data-ttu-id="074d8-118">비클러스터형 인덱스만</span><span class="sxs-lookup"><span data-stu-id="074d8-118">Nonclustered indexes only.</span></span><br /><br /> <span data-ttu-id="074d8-119">이 요소에 이러한 값 중 하나를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="074d8-119">Use one of these values with this element.</span></span>|  
|<span data-ttu-id="074d8-120">**기본값**</span><span class="sxs-lookup"><span data-stu-id="074d8-120">**Default value**</span></span>|<span data-ttu-id="074d8-121">**IDX**</span><span class="sxs-lookup"><span data-stu-id="074d8-121">**IDX**</span></span>|  
|<span data-ttu-id="074d8-122">**발생 빈도**</span><span class="sxs-lookup"><span data-stu-id="074d8-122">**Occurrence**</span></span>|<span data-ttu-id="074d8-123">`TuningOptions` 요소가 사용되지 않을 경우 각 `DropOnlyMode` 요소에 한 번만 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="074d8-123">Required once for each `TuningOptions` element, unless the `DropOnlyMode` element is used.</span></span> <span data-ttu-id="074d8-124">`DropOnlyMode`를 사용하는 경우 `FeatureSet`는 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="074d8-124">If `DropOnlyMode` is used, you cannot use `FeatureSet`.</span></span> <span data-ttu-id="074d8-125">이러한 요소는 함께 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="074d8-125">These elements are mutually exclusive.</span></span>|  
  
## <a name="element-relationships"></a><span data-ttu-id="074d8-126">요소 관계</span><span class="sxs-lookup"><span data-stu-id="074d8-126">Element Relationships</span></span>  
  
|<span data-ttu-id="074d8-127">관계</span><span class="sxs-lookup"><span data-stu-id="074d8-127">Relationship</span></span>|<span data-ttu-id="074d8-128">요소</span><span class="sxs-lookup"><span data-stu-id="074d8-128">Elements</span></span>|  
|------------------|--------------|  
|<span data-ttu-id="074d8-129">**부모 요소**</span><span class="sxs-lookup"><span data-stu-id="074d8-129">**Parent element**</span></span>|[<span data-ttu-id="074d8-130">TuningOptions 요소&#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="074d8-130">TuningOptions Element &#40;DTA&#41;</span></span>](tuningoptions-element-dta.md)|  
|<span data-ttu-id="074d8-131">**자식 요소**</span><span class="sxs-lookup"><span data-stu-id="074d8-131">**Child elements**</span></span>|<span data-ttu-id="074d8-132">없음</span><span class="sxs-lookup"><span data-stu-id="074d8-132">None.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="074d8-133">예제</span><span class="sxs-lookup"><span data-stu-id="074d8-133">Example</span></span>  
 <span data-ttu-id="074d8-134">이 요소의 사용 예제를 보려면 [단순 XML 입력 파일 예제&#40;DTA&#41;](simple-xml-input-file-sample-dta.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="074d8-134">For a usage example of this element, see the [Simple XML Input File Sample &#40;DTA&#41;](simple-xml-input-file-sample-dta.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="074d8-135">참고 항목</span><span class="sxs-lookup"><span data-stu-id="074d8-135">See Also</span></span>  
 [<span data-ttu-id="074d8-136">XML 입력 파일 참조&#40;데이터베이스 엔진 튜닝 관리자&#41;</span><span class="sxs-lookup"><span data-stu-id="074d8-136">XML Input File Reference &#40;Database Engine Tuning Advisor&#41;</span></span>](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
