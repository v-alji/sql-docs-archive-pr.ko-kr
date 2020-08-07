---
title: Configuration 요소 (DTA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- Configuration element
ms.assetid: 1478e56f-57c4-4441-bac9-1ac91453839b
author: stevestein
ms.author: sstein
ms.openlocfilehash: d11938d9a9a694f994a3ea977022a393cbae23d4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87727679"
---
# <a name="configuration-element-dta"></a><span data-ttu-id="914d0-102">Configuration 요소(DTA)</span><span class="sxs-lookup"><span data-stu-id="914d0-102">Configuration Element (DTA)</span></span>
  <span data-ttu-id="914d0-103">작업 튜닝 시에 데이터베이스 엔진 튜닝 관리자가 분석할 기존 및 가상 물리적 디자인 구조로 구성된 사용자 지정 구성입니다.</span><span class="sxs-lookup"><span data-stu-id="914d0-103">Specifies a user-specified configuration consisting of existing and hypothetical physical design structures for the Database Engine Tuning Advisor to analyze when tuning a workload.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="914d0-104">구문</span><span class="sxs-lookup"><span data-stu-id="914d0-104">Syntax</span></span>  
  
```  
  
<DTAInput>  
    <Server>...</Server>  
    <Workload>...</Workload>  
    <TuningOptions>...</TuningOptions  
    <Configuration [SpecificationMode="Relative" | "Absolute"]>  
    ...code removed here...  
    </Configuration>  
</DTAInput>  
```  
  
## <a name="element-attributes"></a><span data-ttu-id="914d0-105">요소 특성</span><span class="sxs-lookup"><span data-stu-id="914d0-105">Element Attributes</span></span>  
  
|<span data-ttu-id="914d0-106">Configuration 특성</span><span class="sxs-lookup"><span data-stu-id="914d0-106">Configuration Attribute</span></span>|<span data-ttu-id="914d0-107">Description</span><span class="sxs-lookup"><span data-stu-id="914d0-107">Description</span></span>|  
|-----------------------------|-----------------|  
|`SpecificationMode`|<span data-ttu-id="914d0-108">(선택 사항)</span><span class="sxs-lookup"><span data-stu-id="914d0-108">Optional.</span></span> <span data-ttu-id="914d0-109">데이터베이스 엔진 튜닝 관리자가 지정된 구성을 현재의 기존 구성과 관련하여 분석해야 하는지 아니면 완전히 새로운 독립 실행형 구성으로 분석해야 하는지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="914d0-109">Specifies whether Database Engine Tuning Advisor should analyze the specified configuration in relation to the current existing configuration, or as a completely new, standalone one.</span></span> <span data-ttu-id="914d0-110">**string** 데이터 형식을 사용하여 허용된 다음 값 중 하나로 이 특성을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="914d0-110">Use a **string** data type to specify this attribute with one of the following allowed values:</span></span><br /><br /> <span data-ttu-id="914d0-111">`Relative`:</span><span class="sxs-lookup"><span data-stu-id="914d0-111">`Relative`:</span></span> <br />                  <span data-ttu-id="914d0-112">튜닝할 데이터베이스에 있는 물리적 디자인 구조(인덱스, 인덱싱된 뷰, 분할)의 현재 기존 구성과 관련하여 지정된 구성을 평가합니다.</span><span class="sxs-lookup"><span data-stu-id="914d0-112">Evaluates the specified configuration in relation to the current existing configuration of physical design structures (indexes, indexed views, partitioning) in the database that is being tuned.</span></span> <span data-ttu-id="914d0-113">다음은 그 예입니다.</span><span class="sxs-lookup"><span data-stu-id="914d0-113">For example:</span></span> <br />`<Configuration SpecificationMode="Relative">`<br /><br /> <span data-ttu-id="914d0-114">`Absolute`:</span><span class="sxs-lookup"><span data-stu-id="914d0-114">`Absolute`:</span></span> <br />                  <span data-ttu-id="914d0-115">지정된 구성을 독립 실행형 구성으로 평가합니다.</span><span class="sxs-lookup"><span data-stu-id="914d0-115">Evaluates the specified configuration as a standalone configuration.</span></span> <span data-ttu-id="914d0-116">Absolute를 지정한 경우 데이터베이스 엔진 튜닝 관리자는 기존 구성을 고려하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="914d0-116">When Absolute is specified, Database Engine Tuning Advisor does not consider the existing configuration.</span></span> <span data-ttu-id="914d0-117">다음은 그 예입니다.</span><span class="sxs-lookup"><span data-stu-id="914d0-117">For example:</span></span><br />`<Configuration SpecificationMode="Absolute">`|  
  
## <a name="element-characteristics"></a><span data-ttu-id="914d0-118">요소 특징</span><span class="sxs-lookup"><span data-stu-id="914d0-118">Element Characteristics</span></span>  
  
|<span data-ttu-id="914d0-119">특성</span><span class="sxs-lookup"><span data-stu-id="914d0-119">Characteristic</span></span>|<span data-ttu-id="914d0-120">Description</span><span class="sxs-lookup"><span data-stu-id="914d0-120">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="914d0-121">**데이터 형식 및 길이**</span><span class="sxs-lookup"><span data-stu-id="914d0-121">**Data type and length**</span></span>|<span data-ttu-id="914d0-122">없음</span><span class="sxs-lookup"><span data-stu-id="914d0-122">None.</span></span>|  
|<span data-ttu-id="914d0-123">**기본값**</span><span class="sxs-lookup"><span data-stu-id="914d0-123">**Default value**</span></span>|<span data-ttu-id="914d0-124">없음</span><span class="sxs-lookup"><span data-stu-id="914d0-124">None.</span></span>|  
|<span data-ttu-id="914d0-125">**발생 빈도**</span><span class="sxs-lookup"><span data-stu-id="914d0-125">**Occurrence**</span></span>|<span data-ttu-id="914d0-126">(선택 사항)</span><span class="sxs-lookup"><span data-stu-id="914d0-126">Optional.</span></span> <span data-ttu-id="914d0-127">각 `DTAInput` 요소에 한 번만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="914d0-127">Can use once for each `DTAInput` element.</span></span>|  
  
## <a name="element-relationships"></a><span data-ttu-id="914d0-128">요소 관계</span><span class="sxs-lookup"><span data-stu-id="914d0-128">Element Relationships</span></span>  
  
|<span data-ttu-id="914d0-129">관계</span><span class="sxs-lookup"><span data-stu-id="914d0-129">Relationship</span></span>|<span data-ttu-id="914d0-130">요소</span><span class="sxs-lookup"><span data-stu-id="914d0-130">Elements</span></span>|  
|------------------|--------------|  
|<span data-ttu-id="914d0-131">**부모 요소**</span><span class="sxs-lookup"><span data-stu-id="914d0-131">**Parent element**</span></span>|[<span data-ttu-id="914d0-132">DTAInput 요소&#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="914d0-132">DTAInput Element &#40;DTA&#41;</span></span>](dtainput-element-dta.md)|  
|<span data-ttu-id="914d0-133">**자식 요소**</span><span class="sxs-lookup"><span data-stu-id="914d0-133">**Child elements**</span></span>|[<span data-ttu-id="914d0-134">Configuration의 Server 요소&#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="914d0-134">Server Element for Configuration &#40;DTA&#41;</span></span>](server-element-for-configuration-dta.md)|  
  
## <a name="example"></a><span data-ttu-id="914d0-135">예제</span><span class="sxs-lookup"><span data-stu-id="914d0-135">Example</span></span>  
 <span data-ttu-id="914d0-136">이 요소의 사용 예를 보려면 [사용자 정의 구성이 포함된 XML 입력 파일 샘플&#40;DTA&#41;](xml-input-file-sample-with-user-specified-configuration-dta.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="914d0-136">For a usage example of this element, see the [XML Input File Sample with User-specified Configuration &#40;DTA&#41;](xml-input-file-sample-with-user-specified-configuration-dta.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="914d0-137">참고 항목</span><span class="sxs-lookup"><span data-stu-id="914d0-137">See Also</span></span>  
 [<span data-ttu-id="914d0-138">XML 입력 파일 참조&#40;데이터베이스 엔진 튜닝 관리자&#41;</span><span class="sxs-lookup"><span data-stu-id="914d0-138">XML Input File Reference &#40;Database Engine Tuning Advisor&#41;</span></span>](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
