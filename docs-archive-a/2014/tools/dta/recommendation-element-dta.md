---
title: 권장 요소 (DTA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- Recommendation element
ms.assetid: 679ea535-865a-4633-a4d3-5b3090515158
author: stevestein
ms.author: sstein
ms.openlocfilehash: b4eb54a106d67f0217a2604b2d08754d0d2c0765
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647410"
---
# <a name="recommendation-element-dta"></a><span data-ttu-id="bcffd-102">Recommendation 요소(DTA)</span><span class="sxs-lookup"><span data-stu-id="bcffd-102">Recommendation Element (DTA)</span></span>
  <span data-ttu-id="bcffd-103">사용자 지정 구성의 일부인 가상 인덱스에 대한 정보를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="bcffd-103">Contains information about the hypothetical indexes that are part of a user-specified configuration.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bcffd-104">구문</span><span class="sxs-lookup"><span data-stu-id="bcffd-104">Syntax</span></span>  
  
```  
  
<Configuration>  
    ...code removed here...  
    <Table>  
      <Name>...</Name>  
      <Recommendation>  
      ...code removed here...  
      </Recommendation>  
```  
  
## <a name="element-characteristics"></a><span data-ttu-id="bcffd-105">요소 특징</span><span class="sxs-lookup"><span data-stu-id="bcffd-105">Element Characteristics</span></span>  
  
|<span data-ttu-id="bcffd-106">특성</span><span class="sxs-lookup"><span data-stu-id="bcffd-106">Characteristic</span></span>|<span data-ttu-id="bcffd-107">Description</span><span class="sxs-lookup"><span data-stu-id="bcffd-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="bcffd-108">**데이터 형식 및 길이**</span><span class="sxs-lookup"><span data-stu-id="bcffd-108">**Data type and length**</span></span>|<span data-ttu-id="bcffd-109">없음</span><span class="sxs-lookup"><span data-stu-id="bcffd-109">None.</span></span>|  
|<span data-ttu-id="bcffd-110">**기본값**</span><span class="sxs-lookup"><span data-stu-id="bcffd-110">**Default value**</span></span>|<span data-ttu-id="bcffd-111">없음</span><span class="sxs-lookup"><span data-stu-id="bcffd-111">None.</span></span>|  
|<span data-ttu-id="bcffd-112">**발생 빈도**</span><span class="sxs-lookup"><span data-stu-id="bcffd-112">**Occurrence**</span></span>|<span data-ttu-id="bcffd-113">(선택 사항)</span><span class="sxs-lookup"><span data-stu-id="bcffd-113">Optional.</span></span> <span data-ttu-id="bcffd-114">각 `Table` 요소에 한 번만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bcffd-114">Can use once for each `Table` element.</span></span>|  
  
## <a name="element-relationships"></a><span data-ttu-id="bcffd-115">요소 관계</span><span class="sxs-lookup"><span data-stu-id="bcffd-115">Element Relationships</span></span>  
  
|<span data-ttu-id="bcffd-116">관계</span><span class="sxs-lookup"><span data-stu-id="bcffd-116">Relationship</span></span>|<span data-ttu-id="bcffd-117">요소</span><span class="sxs-lookup"><span data-stu-id="bcffd-117">Elements</span></span>|  
|------------------|--------------|  
|<span data-ttu-id="bcffd-118">**부모 요소**</span><span class="sxs-lookup"><span data-stu-id="bcffd-118">**Parent element**</span></span>|[<span data-ttu-id="bcffd-119">Schema의 Table 요소&#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="bcffd-119">Table Element for Schema &#40;DTA&#41;</span></span>](table-element-for-schema-dta.md)|  
|<span data-ttu-id="bcffd-120">**자식 요소**</span><span class="sxs-lookup"><span data-stu-id="bcffd-120">**Child elements**</span></span>|[<span data-ttu-id="bcffd-121">Create 요소&#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="bcffd-121">Create Element &#40;DTA&#41;</span></span>](create-element-dta.md)<br /><br /> <span data-ttu-id="bcffd-122">`Drop` 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="bcffd-122">`Drop` element.</span></span> <span data-ttu-id="bcffd-123">자세한 내용은 [데이터베이스 엔진 튜닝 관리자 XML 스키마](https://go.microsoft.com/fwlink/?linkid=43100)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="bcffd-123">For more information, see the [Database Engine Tuning Advisor XML schema](https://go.microsoft.com/fwlink/?linkid=43100).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bcffd-124">설명</span><span class="sxs-lookup"><span data-stu-id="bcffd-124">Remarks</span></span>  
 <span data-ttu-id="bcffd-125">데이터베이스 엔진 튜닝 관리자 XML 스키마에서 이 요소의 이름은 **RecommendationTypecomplexType** 입니다.</span><span class="sxs-lookup"><span data-stu-id="bcffd-125">This element is of the **RecommendationTypecomplexType** name in the Database Engine Tuning Advisor XML schema.</span></span> <span data-ttu-id="bcffd-126">이 요소는 가상 구성에 대한 인덱스를 지정하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="bcffd-126">It is used to specify indexes for a hypothetical configuration.</span></span> <span data-ttu-id="bcffd-127">이 `Recommendation` 요소를 분할(`RecommendationPType`) 또는 뷰(`RecommendationViewType`)를 지정하는 데 사용할 수 있는 다른 유형과 혼동하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="bcffd-127">Do not confuse this `Recommendation` element with the other types that can be used to specify partitioning (`RecommendationPType`) or views (`RecommendationViewType`).</span></span> <span data-ttu-id="bcffd-128">이러한 다른 요소 형식에 대 한 자세한 내용은 `Recommendation` [데이터베이스 엔진 튜닝 관리자 XML 스키마](https://go.microsoft.com/fwlink/?linkid=43100)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="bcffd-128">For information about these other `Recommendation` element types, see the [Database Engine Tuning Advisor XML schema](https://go.microsoft.com/fwlink/?linkid=43100).</span></span>  
  
## <a name="example"></a><span data-ttu-id="bcffd-129">예제</span><span class="sxs-lookup"><span data-stu-id="bcffd-129">Example</span></span>  
 <span data-ttu-id="bcffd-130">이 요소의 사용 예를 보려면 [사용자 정의 구성이 포함된 XML 입력 파일 샘플&#40;DTA&#41;](xml-input-file-sample-with-user-specified-configuration-dta.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="bcffd-130">For a usage example of this element, see the [XML Input File Sample with User-specified Configuration &#40;DTA&#41;](xml-input-file-sample-with-user-specified-configuration-dta.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bcffd-131">참고 항목</span><span class="sxs-lookup"><span data-stu-id="bcffd-131">See Also</span></span>  
 [<span data-ttu-id="bcffd-132">XML 입력 파일 참조&#40;데이터베이스 엔진 튜닝 관리자&#41;</span><span class="sxs-lookup"><span data-stu-id="bcffd-132">XML Input File Reference &#40;Database Engine Tuning Advisor&#41;</span></span>](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
