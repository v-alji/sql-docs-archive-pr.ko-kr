---
title: KeepExisting 요소 (DTA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- KeepExisting element
ms.assetid: e67aae61-d06d-4a03-85ba-6516c3502dce
author: stevestein
ms.author: sstein
ms.openlocfilehash: cde9b3091b75f55e4b9c79137853fbd7d4e0daf9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734796"
---
# <a name="keepexisting-element-dta"></a><span data-ttu-id="571fa-102">KeepExisting 요소(DTA)</span><span class="sxs-lookup"><span data-stu-id="571fa-102">KeepExisting Element (DTA)</span></span>
  <span data-ttu-id="571fa-103">데이터베이스 엔진 튜닝 관리자가 권장 구성을 생성할 때 유지해야 하는 물리적인 디자인 구조(인덱스, 인덱싱된 뷰 또는 분할)를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="571fa-103">Specifies the physical design structures (indexes, indexed views, or partitioning) that Database Engine Tuning Advisor must retain when generating its recommendation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="571fa-104">구문</span><span class="sxs-lookup"><span data-stu-id="571fa-104">Syntax</span></span>  
  
```  
  
<DTAInput>  
...code removed...  
    <TuningOptions>  
      <KeepExisting>...</KeepExisting>  
```  
  
## <a name="element-characteristics"></a><span data-ttu-id="571fa-105">요소 특징</span><span class="sxs-lookup"><span data-stu-id="571fa-105">Element Characteristics</span></span>  
  
|<span data-ttu-id="571fa-106">특성</span><span class="sxs-lookup"><span data-stu-id="571fa-106">Characteristic</span></span>|<span data-ttu-id="571fa-107">Description</span><span class="sxs-lookup"><span data-stu-id="571fa-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="571fa-108">**데이터 형식 및 길이**</span><span class="sxs-lookup"><span data-stu-id="571fa-108">**Data type and length**</span></span>|<span data-ttu-id="571fa-109">`string`, 서버에서 지정한 길이 제한 적용</span><span class="sxs-lookup"><span data-stu-id="571fa-109">`string`, length limit enforced by the server.</span></span>|  
|<span data-ttu-id="571fa-110">**허용된 값**</span><span class="sxs-lookup"><span data-stu-id="571fa-110">**Allowed values**</span></span>|<span data-ttu-id="571fa-111">**NONE**</span><span class="sxs-lookup"><span data-stu-id="571fa-111">**NONE**</span></span><br /> <span data-ttu-id="571fa-112">기존 구조 없음</span><span class="sxs-lookup"><span data-stu-id="571fa-112">No existing structures.</span></span><br /><br /> <span data-ttu-id="571fa-113">**ALL**</span><span class="sxs-lookup"><span data-stu-id="571fa-113">**ALL**</span></span><br /> <span data-ttu-id="571fa-114">모든 기존 구조</span><span class="sxs-lookup"><span data-stu-id="571fa-114">All existing structures.</span></span><br /><br /> <span data-ttu-id="571fa-115">**ALIGNED**</span><span class="sxs-lookup"><span data-stu-id="571fa-115">**ALIGNED**</span></span><br /> <span data-ttu-id="571fa-116">모든 파티션 정렬 구조</span><span class="sxs-lookup"><span data-stu-id="571fa-116">All partition-aligned structures.</span></span><br /><br /> <span data-ttu-id="571fa-117">**CL_IDX**</span><span class="sxs-lookup"><span data-stu-id="571fa-117">**CL_IDX**</span></span><br /> <span data-ttu-id="571fa-118">테이블의 모든 클러스터형 인덱스</span><span class="sxs-lookup"><span data-stu-id="571fa-118">All clustered indexes on tables.</span></span><br /><br /> <span data-ttu-id="571fa-119">**IDX**</span><span class="sxs-lookup"><span data-stu-id="571fa-119">**IDX**</span></span><br /> <span data-ttu-id="571fa-120">테이블의 모든 클러스터형 및 비클러스터형 인덱스</span><span class="sxs-lookup"><span data-stu-id="571fa-120">All clustered and nonclustered indexes on tables.</span></span><br /><br /> <span data-ttu-id="571fa-121">이 요소에 이러한 값 중 하나만 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="571fa-121">Use only one of these values with this element.</span></span>|  
|<span data-ttu-id="571fa-122">**기본값**</span><span class="sxs-lookup"><span data-stu-id="571fa-122">**Default value**</span></span>|<span data-ttu-id="571fa-123">없음</span><span class="sxs-lookup"><span data-stu-id="571fa-123">None.</span></span>|  
|<span data-ttu-id="571fa-124">**발생 빈도**</span><span class="sxs-lookup"><span data-stu-id="571fa-124">**Occurrence**</span></span>|<span data-ttu-id="571fa-125">(선택 사항)</span><span class="sxs-lookup"><span data-stu-id="571fa-125">Optional.</span></span> <span data-ttu-id="571fa-126">각 `TuningOptions` 요소에 한 번만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="571fa-126">Can use only once for each `TuningOptions` element.</span></span>|  
  
## <a name="element-relationships"></a><span data-ttu-id="571fa-127">요소 관계</span><span class="sxs-lookup"><span data-stu-id="571fa-127">Element Relationships</span></span>  
  
|<span data-ttu-id="571fa-128">관계</span><span class="sxs-lookup"><span data-stu-id="571fa-128">Relationship</span></span>|<span data-ttu-id="571fa-129">요소</span><span class="sxs-lookup"><span data-stu-id="571fa-129">Elements</span></span>|  
|------------------|--------------|  
|<span data-ttu-id="571fa-130">**부모 요소**</span><span class="sxs-lookup"><span data-stu-id="571fa-130">**Parent element**</span></span>|[<span data-ttu-id="571fa-131">TuningOptions 요소&#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="571fa-131">TuningOptions Element &#40;DTA&#41;</span></span>](tuningoptions-element-dta.md)|  
|<span data-ttu-id="571fa-132">**자식 요소**</span><span class="sxs-lookup"><span data-stu-id="571fa-132">**Child elements**</span></span>|<span data-ttu-id="571fa-133">없음</span><span class="sxs-lookup"><span data-stu-id="571fa-133">None.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="571fa-134">예제</span><span class="sxs-lookup"><span data-stu-id="571fa-134">Example</span></span>  
 <span data-ttu-id="571fa-135">이 요소의 사용 예제를 보려면 [단순 XML 입력 파일 예제&#40;DTA&#41;](simple-xml-input-file-sample-dta.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="571fa-135">For a usage example of this element, see the [Simple XML Input File Sample &#40;DTA&#41;](simple-xml-input-file-sample-dta.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="571fa-136">참고 항목</span><span class="sxs-lookup"><span data-stu-id="571fa-136">See Also</span></span>  
 [<span data-ttu-id="571fa-137">XML 입력 파일 참조&#40;데이터베이스 엔진 튜닝 관리자&#41;</span><span class="sxs-lookup"><span data-stu-id="571fa-137">XML Input File Reference &#40;Database Engine Tuning Advisor&#41;</span></span>](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
