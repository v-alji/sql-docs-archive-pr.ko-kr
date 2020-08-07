---
title: Droponly 모드 요소 (DTA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- DropOnlyMode element
ms.assetid: 80960676-7581-4074-889b-80ee665963dd
author: stevestein
ms.author: sstein
ms.openlocfilehash: b274dc394a933308cf2161cc271d09b8391900c4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87727644"
---
# <a name="droponlymode-element-dta"></a><span data-ttu-id="32e9c-102">DropOnlyMode 요소(DTA)</span><span class="sxs-lookup"><span data-stu-id="32e9c-102">DropOnlyMode Element (DTA)</span></span>
  <span data-ttu-id="32e9c-103">데이터베이스 엔진 튜닝 관리자가 튜닝 세션 동안에 기존 인덱스, 인덱싱된 뷰 또는 파티션을 삭제하는 것만 고려해야 하도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="32e9c-103">Specifies that Database Engine Tuning Advisor should only consider dropping existing indexes, indexed views, or partitions during the tuning session.</span></span> <span data-ttu-id="32e9c-104">이 튜닝 옵션을 지정하면 새 물리적인 디자인 구조는 고려되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="32e9c-104">No new physical design structures are considered when this tuning option is specified.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32e9c-105">구문</span><span class="sxs-lookup"><span data-stu-id="32e9c-105">Syntax</span></span>  
  
```  
  
<DTAInput>  
...code removed...  
    <TuningOptions>  
      <DropOnlyMode>...</DropOnlyMode>  
```  
  
## <a name="element-characteristics"></a><span data-ttu-id="32e9c-106">요소 특징</span><span class="sxs-lookup"><span data-stu-id="32e9c-106">Element Characteristics</span></span>  
  
|<span data-ttu-id="32e9c-107">특성</span><span class="sxs-lookup"><span data-stu-id="32e9c-107">Characteristic</span></span>|<span data-ttu-id="32e9c-108">Description</span><span class="sxs-lookup"><span data-stu-id="32e9c-108">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="32e9c-109">**데이터 형식 및 길이**</span><span class="sxs-lookup"><span data-stu-id="32e9c-109">**Data type and length**</span></span>|<span data-ttu-id="32e9c-110">없음</span><span class="sxs-lookup"><span data-stu-id="32e9c-110">None.</span></span>|  
|<span data-ttu-id="32e9c-111">**기본값**</span><span class="sxs-lookup"><span data-stu-id="32e9c-111">**Default value**</span></span>|<span data-ttu-id="32e9c-112">없음</span><span class="sxs-lookup"><span data-stu-id="32e9c-112">None.</span></span>|  
|<span data-ttu-id="32e9c-113">**발생 빈도**</span><span class="sxs-lookup"><span data-stu-id="32e9c-113">**Occurrence**</span></span>|<span data-ttu-id="32e9c-114">(선택 사항)</span><span class="sxs-lookup"><span data-stu-id="32e9c-114">Optional.</span></span> <span data-ttu-id="32e9c-115">각 `TuningOptions` 요소에 한 번만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="32e9c-115">Can use only once for each `TuningOptions` element.</span></span> <span data-ttu-id="32e9c-116">`TuningOptions` 요소에 다음 요소를 지정한 경우 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="32e9c-116">Cannot be used if the following elements are specified in the `TuningOptions` element:</span></span><br /><br /> [<span data-ttu-id="32e9c-117">FeatureSet 요소&#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="32e9c-117">FeatureSet Element &#40;DTA&#41;</span></span>](featureset-element-dta.md)<br /><br /> [<span data-ttu-id="32e9c-118">Partitioning 요소&#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="32e9c-118">Partitioning Element &#40;DTA&#41;</span></span>](partitioning-element-dta.md)<br /><br /> <span data-ttu-id="32e9c-119">[KeepExisting 요소&#40;DTA&#41;](keepexisting-element-dta.md)는 **ALL**로 설정됨</span><span class="sxs-lookup"><span data-stu-id="32e9c-119">[KeepExisting Element &#40;DTA&#41;](keepexisting-element-dta.md) is set to **ALL**</span></span>|  
  
## <a name="element-relationships"></a><span data-ttu-id="32e9c-120">요소 관계</span><span class="sxs-lookup"><span data-stu-id="32e9c-120">Element Relationships</span></span>  
  
|<span data-ttu-id="32e9c-121">관계</span><span class="sxs-lookup"><span data-stu-id="32e9c-121">Relationship</span></span>|<span data-ttu-id="32e9c-122">요소</span><span class="sxs-lookup"><span data-stu-id="32e9c-122">Elements</span></span>|  
|------------------|--------------|  
|<span data-ttu-id="32e9c-123">**부모 요소**</span><span class="sxs-lookup"><span data-stu-id="32e9c-123">**Parent element**</span></span>|[<span data-ttu-id="32e9c-124">TuningOptions 요소&#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="32e9c-124">TuningOptions Element &#40;DTA&#41;</span></span>](tuningoptions-element-dta.md)|  
|<span data-ttu-id="32e9c-125">**자식 요소**</span><span class="sxs-lookup"><span data-stu-id="32e9c-125">**Child elements**</span></span>|<span data-ttu-id="32e9c-126">없음</span><span class="sxs-lookup"><span data-stu-id="32e9c-126">None.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="32e9c-127">예제</span><span class="sxs-lookup"><span data-stu-id="32e9c-127">Example</span></span>  
 <span data-ttu-id="32e9c-128">다음 예에서는 `TuningOptions`가 지정된 데이터베이스 엔진 튜닝 관리자 XML 입력 파일의 `DropOnlyMode` 섹션을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="32e9c-128">The following example shows the `TuningOptions` section of a Database Engine Tuning Advisor XML input file where the `DropOnlyMode` is specified.</span></span> <span data-ttu-id="32e9c-129">이 예에서 튜닝 시간은 24시간(1440분)으로 제한되며 기존의 모든 클러스터형 인덱스 및 비클러스터형 인덱스는 삭제 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="32e9c-129">In this example the tuning time is limited to 24 hours (1440 minutes) and all existing clustered and nonclustered indexes will be considered for dropping:</span></span>  
  
```xml  
<TuningOptions  
  <TuningTimeInMin>1440</Name>  
  <KeepExisting>ALIGNED</KeepExisting>  
  <DropOnlyMode />  
</TuningOptions>  
```  
  
## <a name="see-also"></a><span data-ttu-id="32e9c-130">참고 항목</span><span class="sxs-lookup"><span data-stu-id="32e9c-130">See Also</span></span>  
 [<span data-ttu-id="32e9c-131">XML 입력 파일 참조&#40;데이터베이스 엔진 튜닝 관리자&#41;</span><span class="sxs-lookup"><span data-stu-id="32e9c-131">XML Input File Reference &#40;Database Engine Tuning Advisor&#41;</span></span>](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
