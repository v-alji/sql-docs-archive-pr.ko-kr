---
title: OnlineIndexOperation 요소 (DTA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- OnlineIndexOperation element
ms.assetid: 7c5614cd-09aa-4a59-9591-347aa7d36473
author: stevestein
ms.author: sstein
ms.openlocfilehash: 48943c1b31d7a0a24ae939050d44494476e50034
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653094"
---
# <a name="onlineindexoperation-element-dta"></a><span data-ttu-id="a1f0a-102">OnlineIndexOperation 요소(DTA)</span><span class="sxs-lookup"><span data-stu-id="a1f0a-102">OnlineIndexOperation Element (DTA)</span></span>
  <span data-ttu-id="a1f0a-103">데이터베이스 엔진 튜닝 관리자가 권장하는 인덱스, 인덱싱된 뷰 또는 파티션을 온라인으로 만들 수 있는지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a1f0a-103">Specifies whether the indexes, indexed views, or partitions that Database Engine Tuning Advisor recommends can be created online.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a1f0a-104">구문</span><span class="sxs-lookup"><span data-stu-id="a1f0a-104">Syntax</span></span>  
  
```  
  
<DTAInput>  
...code removed...  
    <TuningOptions>  
      <OnlineIndexOperation>...</OnlineIndexOperation>  
```  
  
## <a name="element-characteristics"></a><span data-ttu-id="a1f0a-105">요소 특징</span><span class="sxs-lookup"><span data-stu-id="a1f0a-105">Element Characteristics</span></span>  
  
|<span data-ttu-id="a1f0a-106">특성</span><span class="sxs-lookup"><span data-stu-id="a1f0a-106">Characteristic</span></span>|<span data-ttu-id="a1f0a-107">Description</span><span class="sxs-lookup"><span data-stu-id="a1f0a-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="a1f0a-108">**데이터 형식 및 길이**</span><span class="sxs-lookup"><span data-stu-id="a1f0a-108">**Data type and length**</span></span>|<span data-ttu-id="a1f0a-109">`string`, 최대 길이 없음</span><span class="sxs-lookup"><span data-stu-id="a1f0a-109">`string`, no maximum length.</span></span>|  
|<span data-ttu-id="a1f0a-110">**허용된 값**</span><span class="sxs-lookup"><span data-stu-id="a1f0a-110">**Allowed values**</span></span>|<span data-ttu-id="a1f0a-111">**OFF**</span><span class="sxs-lookup"><span data-stu-id="a1f0a-111">**OFF**</span></span><br /> <span data-ttu-id="a1f0a-112">권장되는 물리적 디자인 구조를 온라인으로 만들 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a1f0a-112">No recommended physical design structures can be created online.</span></span><br /><br /> <span data-ttu-id="a1f0a-113">**ON**</span><span class="sxs-lookup"><span data-stu-id="a1f0a-113">**ON**</span></span><br /> <span data-ttu-id="a1f0a-114">권장되는 모든 물리적 디자인 구조를 온라인으로 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1f0a-114">All recommended physical design structures can be created online.</span></span><br /><br /> <span data-ttu-id="a1f0a-115">**MIXED**</span><span class="sxs-lookup"><span data-stu-id="a1f0a-115">**MIXED**</span></span><br /> <span data-ttu-id="a1f0a-116">데이터베이스 엔진 튜닝 관리자는 가능한 경우 온라인으로 만들 수 있는 물리적 디자인 구조를 제안합니다.</span><span class="sxs-lookup"><span data-stu-id="a1f0a-116">Database Engine Tuning Advisor attempts to recommend physical design structures that can be created online when possible.</span></span><br /><br /> <span data-ttu-id="a1f0a-117">이 요소에 이러한 값 중 하나를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="a1f0a-117">Use one of these values with this element.</span></span> <span data-ttu-id="a1f0a-118">인덱스를 온라인으로 만들 경우 **ONLINE = ON** 키워드가 개체 정의에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="a1f0a-118">If indexes are created online, the keyword **ONLINE = ON** is appended to its object definition.</span></span>|  
|<span data-ttu-id="a1f0a-119">**기본값**</span><span class="sxs-lookup"><span data-stu-id="a1f0a-119">**Default value**</span></span>|<span data-ttu-id="a1f0a-120">없음</span><span class="sxs-lookup"><span data-stu-id="a1f0a-120">None.</span></span>|  
|<span data-ttu-id="a1f0a-121">**발생 빈도**</span><span class="sxs-lookup"><span data-stu-id="a1f0a-121">**Occurrence**</span></span>|<span data-ttu-id="a1f0a-122">(선택 사항)</span><span class="sxs-lookup"><span data-stu-id="a1f0a-122">Optional.</span></span> <span data-ttu-id="a1f0a-123">사용할 경우 `TuningOptions` 요소에 한 번만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1f0a-123">If used, can only be used once for the `TuningOptions` element.</span></span>|  
  
## <a name="element-relationships"></a><span data-ttu-id="a1f0a-124">요소 관계</span><span class="sxs-lookup"><span data-stu-id="a1f0a-124">Element Relationships</span></span>  
  
|<span data-ttu-id="a1f0a-125">관계</span><span class="sxs-lookup"><span data-stu-id="a1f0a-125">Relationship</span></span>|<span data-ttu-id="a1f0a-126">요소</span><span class="sxs-lookup"><span data-stu-id="a1f0a-126">Elements</span></span>|  
|------------------|--------------|  
|<span data-ttu-id="a1f0a-127">**부모 요소**</span><span class="sxs-lookup"><span data-stu-id="a1f0a-127">**Parent element**</span></span>|[<span data-ttu-id="a1f0a-128">TuningOptions 요소&#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="a1f0a-128">TuningOptions Element &#40;DTA&#41;</span></span>](tuningoptions-element-dta.md)|  
|<span data-ttu-id="a1f0a-129">**자식 요소**</span><span class="sxs-lookup"><span data-stu-id="a1f0a-129">**Child elements**</span></span>|<span data-ttu-id="a1f0a-130">없음</span><span class="sxs-lookup"><span data-stu-id="a1f0a-130">None.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="a1f0a-131">예제</span><span class="sxs-lookup"><span data-stu-id="a1f0a-131">Example</span></span>  
 <span data-ttu-id="a1f0a-132">이 요소의 사용 예제를 보려면 [단순 XML 입력 파일 예제&#40;DTA&#41;](simple-xml-input-file-sample-dta.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a1f0a-132">For a usage example of this element, see the [Simple XML Input File Sample &#40;DTA&#41;](simple-xml-input-file-sample-dta.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1f0a-133">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a1f0a-133">See Also</span></span>  
 [<span data-ttu-id="a1f0a-134">XML 입력 파일 참조&#40;데이터베이스 엔진 튜닝 관리자&#41;</span><span class="sxs-lookup"><span data-stu-id="a1f0a-134">XML Input File Reference &#40;Database Engine Tuning Advisor&#41;</span></span>](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
