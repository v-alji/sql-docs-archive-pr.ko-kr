---
title: TuningOptions 요소 (DTA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- TuningOptions element
ms.assetid: 58a22ba1-8e03-411f-bd46-85e4540f217a
author: stevestein
ms.author: sstein
ms.openlocfilehash: 2fab1c55c9d036424142b2692e8335ea65c22340
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87735724"
---
# <a name="tuningoptions-element-dta"></a><span data-ttu-id="248e5-102">TuningOptions 요소(DTA)</span><span class="sxs-lookup"><span data-stu-id="248e5-102">TuningOptions Element (DTA)</span></span>
  <span data-ttu-id="248e5-103">특정 튜닝 세션에 대한 튜닝 옵션을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="248e5-103">Contains the tuning options for a specific tuning session.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="248e5-104">구문</span><span class="sxs-lookup"><span data-stu-id="248e5-104">Syntax</span></span>  
  
```  
  
<DTAInput>  
    <Server>  
...code removed...  
    <Workload>...</Workload>  
    <TuningOptions>...</TuningOptions>  
```  
  
## <a name="element-characteristics"></a><span data-ttu-id="248e5-105">요소 특징</span><span class="sxs-lookup"><span data-stu-id="248e5-105">Element Characteristics</span></span>  
  
|<span data-ttu-id="248e5-106">특성</span><span class="sxs-lookup"><span data-stu-id="248e5-106">Characteristic</span></span>|<span data-ttu-id="248e5-107">Description</span><span class="sxs-lookup"><span data-stu-id="248e5-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="248e5-108">**데이터 형식 및 길이**</span><span class="sxs-lookup"><span data-stu-id="248e5-108">**Data type and length**</span></span>|<span data-ttu-id="248e5-109">없음</span><span class="sxs-lookup"><span data-stu-id="248e5-109">None.</span></span>|  
|<span data-ttu-id="248e5-110">**기본값**</span><span class="sxs-lookup"><span data-stu-id="248e5-110">**Default value**</span></span>|<span data-ttu-id="248e5-111">없음</span><span class="sxs-lookup"><span data-stu-id="248e5-111">None.</span></span>|  
|<span data-ttu-id="248e5-112">**발생 빈도**</span><span class="sxs-lookup"><span data-stu-id="248e5-112">**Occurrence**</span></span>|<span data-ttu-id="248e5-113">(선택 사항)</span><span class="sxs-lookup"><span data-stu-id="248e5-113">Optional.</span></span> <span data-ttu-id="248e5-114">사용할 경우 각 `DTAInput` 요소에 한 번만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="248e5-114">If used, can only be used once for each `DTAInput` element.</span></span>|  
  
## <a name="element-relationships"></a><span data-ttu-id="248e5-115">요소 관계</span><span class="sxs-lookup"><span data-stu-id="248e5-115">Element Relationships</span></span>  
  
|<span data-ttu-id="248e5-116">관계</span><span class="sxs-lookup"><span data-stu-id="248e5-116">Relationship</span></span>|<span data-ttu-id="248e5-117">요소</span><span class="sxs-lookup"><span data-stu-id="248e5-117">Elements</span></span>|  
|------------------|--------------|  
|<span data-ttu-id="248e5-118">**부모 요소**</span><span class="sxs-lookup"><span data-stu-id="248e5-118">**Parent element**</span></span>|[<span data-ttu-id="248e5-119">DTAInput 요소&#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="248e5-119">DTAInput Element &#40;DTA&#41;</span></span>](dtainput-element-dta.md)|  
|<span data-ttu-id="248e5-120">**자식 요소**</span><span class="sxs-lookup"><span data-stu-id="248e5-120">**Child elements**</span></span>|<span data-ttu-id="248e5-121">`ReportSet` 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="248e5-121">`ReportSet` element.</span></span> <span data-ttu-id="248e5-122">자세한 내용은 [데이터베이스 엔진 튜닝 관리자 XML 스키마](https://go.microsoft.com/fwlink/?linkid=43100)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="248e5-122">For more information, see the [Database Engine Tuning Advisor XML schema](https://go.microsoft.com/fwlink/?linkid=43100).</span></span><br /><br /> <span data-ttu-id="248e5-123">`TuningLogTable` 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="248e5-123">`TuningLogTable` element.</span></span> <span data-ttu-id="248e5-124">자세한 내용은 [데이터베이스 엔진 튜닝 관리자 XML 스키마](https://go.microsoft.com/fwlink/?linkid=43100)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="248e5-124">For more information, see the [Database Engine Tuning Advisor XML schema](https://go.microsoft.com/fwlink/?linkid=43100).</span></span><br /><br /> <span data-ttu-id="248e5-125">`NumberOfEvents` 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="248e5-125">`NumberOfEvents` element.</span></span> <span data-ttu-id="248e5-126">자세한 내용은 [데이터베이스 엔진 튜닝 관리자 XML 스키마](https://go.microsoft.com/fwlink/?linkid=43100)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="248e5-126">For more information, see the [Database Engine Tuning Advisor XML schema](https://go.microsoft.com/fwlink/?linkid=43100).</span></span><br /><br /> [<span data-ttu-id="248e5-127">TuningTimeInMin 요소&#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="248e5-127">TuningTimeInMin Element &#40;DTA&#41;</span></span>](tuningtimeinmin-element-dta.md)<br /><br /> [<span data-ttu-id="248e5-128">StorageBoundInMB 요소&#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="248e5-128">StorageBoundInMB Element &#40;DTA&#41;</span></span>](storageboundinmb-element-dta.md)<br /><br /> <span data-ttu-id="248e5-129">`MaxKeyColumnsInIndex` 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="248e5-129">`MaxKeyColumnsInIndex` element.</span></span> <span data-ttu-id="248e5-130">자세한 내용은 [데이터베이스 엔진 튜닝 관리자 XML 스키마](https://go.microsoft.com/fwlink/?linkid=43100)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="248e5-130">For more information, see the [Database Engine Tuning Advisor XML schema](https://go.microsoft.com/fwlink/?linkid=43100).</span></span><br /><br /> <span data-ttu-id="248e5-131">`MaxColumnsInIndex` 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="248e5-131">`MaxColumnsInIndex` element.</span></span> <span data-ttu-id="248e5-132">자세한 내용은 [데이터베이스 엔진 튜닝 관리자 XML 스키마](https://go.microsoft.com/fwlink/?linkid=43100)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="248e5-132">For more information, see the [Database Engine Tuning Advisor XML schema](https://go.microsoft.com/fwlink/?linkid=43100).</span></span><br /><br /> <span data-ttu-id="248e5-133">`MinPercentageImprovement` 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="248e5-133">`MinPercentageImprovement` element.</span></span> <span data-ttu-id="248e5-134">자세한 내용은 [데이터베이스 엔진 튜닝 관리자 XML 스키마](https://go.microsoft.com/fwlink/?linkid=43100)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="248e5-134">For more information, see the [Database Engine Tuning Advisor XML schema](https://go.microsoft.com/fwlink/?linkid=43100)</span></span><br /><br /> [<span data-ttu-id="248e5-135">TestServer 요소&#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="248e5-135">TestServer Element &#40;DTA&#41;</span></span>](server-element-dta.md)<br /><br /> [<span data-ttu-id="248e5-136">FeatureSet 요소&#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="248e5-136">FeatureSet Element &#40;DTA&#41;</span></span>](featureset-element-dta.md)<br /><br /> [<span data-ttu-id="248e5-137">Partitioning 요소&#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="248e5-137">Partitioning Element &#40;DTA&#41;</span></span>](partitioning-element-dta.md)<br /><br /> [<span data-ttu-id="248e5-138">DropOnlyMode 요소&#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="248e5-138">DropOnlyMode Element &#40;DTA&#41;</span></span>](droponlymode-element-dta.md)<br /><br /> [<span data-ttu-id="248e5-139">KeepExisting 요소&#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="248e5-139">KeepExisting Element &#40;DTA&#41;</span></span>](keepexisting-element-dta.md)<br /><br /> [<span data-ttu-id="248e5-140">OnlineIndexOperation 요소&#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="248e5-140">OnlineIndexOperation Element &#40;DTA&#41;</span></span>](onlineindexoperation-element-dta.md)<br /><br /> [<span data-ttu-id="248e5-141">DatabaseToConnect 요소&#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="248e5-141">DatabaseToConnect Element &#40;DTA&#41;</span></span>](databasetoconnect-element-dta.md)<br /><br /> <span data-ttu-id="248e5-142">`IgnoreConstantsInWorkload` 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="248e5-142">`IgnoreConstantsInWorkload` element.</span></span> <span data-ttu-id="248e5-143">자세한 내용은 [데이터베이스 엔진 튜닝 관리자 XML 스키마](https://go.microsoft.com/fwlink/?linkid=43100)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="248e5-143">For more information, see the [Database Engine Tuning Advisor XML schema](https://go.microsoft.com/fwlink/?linkid=43100).</span></span><br /><br /> <span data-ttu-id="248e5-144">`RetainShellDB` 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="248e5-144">`RetainShellDB` element.</span></span> <span data-ttu-id="248e5-145">자세한 내용은 [데이터베이스 엔진 튜닝 관리자 XML 스키마](https://go.microsoft.com/fwlink/?linkid=43100)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="248e5-145">For more information, see the [Database Engine Tuning Advisor XML schema](https://go.microsoft.com/fwlink/?linkid=43100).</span></span>|  
  
## <a name="example"></a><span data-ttu-id="248e5-146">예제</span><span class="sxs-lookup"><span data-stu-id="248e5-146">Example</span></span>  
 <span data-ttu-id="248e5-147">요소에 대 한 예제 `TuningOptions` 는 [DTA&#41;&#40;XML 입력 파일 샘플 ](xml-input-file-samples-dta.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="248e5-147">For examples of the `TuningOptions` element, see the [XML Input File Samples &#40;DTA&#41;](xml-input-file-samples-dta.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="248e5-148">참고 항목</span><span class="sxs-lookup"><span data-stu-id="248e5-148">See Also</span></span>  
 [<span data-ttu-id="248e5-149">XML 입력 파일 참조&#40;데이터베이스 엔진 튜닝 관리자&#41;</span><span class="sxs-lookup"><span data-stu-id="248e5-149">XML Input File Reference &#40;Database Engine Tuning Advisor&#41;</span></span>](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
