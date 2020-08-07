---
title: Create 요소 (DTA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- Create element (DTA)
ms.assetid: 9d076c90-f933-45f4-b6d9-447793f6528b
author: stevestein
ms.author: sstein
ms.openlocfilehash: 407f16c3898e56cd393e36c39ed799b83e0092ea
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87727659"
---
# <a name="create-element-dta"></a><span data-ttu-id="057db-102">Create 요소(DTA)</span><span class="sxs-lookup"><span data-stu-id="057db-102">Create Element (DTA)</span></span>
  <span data-ttu-id="057db-103">인덱스, 통계 또는 힙 구조에 대한 정보를 사용자 지정 구성에 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="057db-103">Contains information about the indexes, statistics, or heap structures in a user-specified configuration.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="057db-104">구문</span><span class="sxs-lookup"><span data-stu-id="057db-104">Syntax</span></span>  
  
```  
  
<Recommendation>  
    <Create>  
    ...code removed here...  
    </Create>  
</Recommendation>  
```  
  
## <a name="element-characteristics"></a><span data-ttu-id="057db-105">요소 특징</span><span class="sxs-lookup"><span data-stu-id="057db-105">Element Characteristics</span></span>  
  
|<span data-ttu-id="057db-106">특성</span><span class="sxs-lookup"><span data-stu-id="057db-106">Characteristic</span></span>|<span data-ttu-id="057db-107">Description</span><span class="sxs-lookup"><span data-stu-id="057db-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="057db-108">**데이터 형식 및 길이**</span><span class="sxs-lookup"><span data-stu-id="057db-108">**Data type and length**</span></span>|<span data-ttu-id="057db-109">없음</span><span class="sxs-lookup"><span data-stu-id="057db-109">None.</span></span>|  
|<span data-ttu-id="057db-110">**기본값**</span><span class="sxs-lookup"><span data-stu-id="057db-110">**Default value**</span></span>|<span data-ttu-id="057db-111">없음</span><span class="sxs-lookup"><span data-stu-id="057db-111">None.</span></span>|  
|<span data-ttu-id="057db-112">**발생 빈도**</span><span class="sxs-lookup"><span data-stu-id="057db-112">**Occurrence**</span></span>|<span data-ttu-id="057db-113">각 물리적 디자인 구조 유형(인덱스, 통계 또는 힙 구조)에 한 번만 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="057db-113">Required once for each physical design structure type (indexes, statistics, or heap structures).</span></span>|  
  
## <a name="element-relationships"></a><span data-ttu-id="057db-114">요소 관계</span><span class="sxs-lookup"><span data-stu-id="057db-114">Element Relationships</span></span>  
  
|<span data-ttu-id="057db-115">관계</span><span class="sxs-lookup"><span data-stu-id="057db-115">Relationship</span></span>|<span data-ttu-id="057db-116">요소</span><span class="sxs-lookup"><span data-stu-id="057db-116">Elements</span></span>|  
|------------------|--------------|  
|<span data-ttu-id="057db-117">**부모 요소**</span><span class="sxs-lookup"><span data-stu-id="057db-117">**Parent element**</span></span>|[<span data-ttu-id="057db-118">Recommendation 요소&#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="057db-118">Recommendation Element &#40;DTA&#41;</span></span>](recommendation-element-dta.md)|  
|<span data-ttu-id="057db-119">**자식 요소**</span><span class="sxs-lookup"><span data-stu-id="057db-119">**Child elements**</span></span>|[<span data-ttu-id="057db-120">Index 요소&#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="057db-120">Index Element &#40;DTA&#41;</span></span>](index-element-dta.md)<br /><br /> <span data-ttu-id="057db-121">`Statistics`요소 (자세한 내용은 [데이터베이스 엔진 튜닝 관리자 XML 스키마](https://schemas.microsoft.com/sqlserver/) 참조)</span><span class="sxs-lookup"><span data-stu-id="057db-121">`Statistics` Element (see [Database Engine Tuning Advisor XML schema](https://schemas.microsoft.com/sqlserver/) for information)</span></span><br /><br /> <span data-ttu-id="057db-122">`Heap`요소 (자세한 내용은 [데이터베이스 엔진 튜닝 관리자 XML 스키마](https://schemas.microsoft.com/sqlserver/) 참조)</span><span class="sxs-lookup"><span data-stu-id="057db-122">`Heap` Element (see [Database Engine Tuning Advisor XML schema](https://schemas.microsoft.com/sqlserver/) for information)</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="057db-123">설명</span><span class="sxs-lookup"><span data-stu-id="057db-123">Remarks</span></span>  
 <span data-ttu-id="057db-124">데이터베이스 엔진 튜닝 관리자 XML 스키마에서 이 요소의 이름은 **CreateTypecomplexType** 입니다.</span><span class="sxs-lookup"><span data-stu-id="057db-124">This element is of the **CreateTypecomplexType** name in the Database Engine Tuning Advisor XML schema.</span></span> <span data-ttu-id="057db-125">이 요소는 사용자 지정 구성에 대한 인덱스, 통계 및 힙 구조를 만드는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="057db-125">It is used to create indexes, statistics, and heap structures for a user-specified configuration.</span></span> <span data-ttu-id="057db-126">이 `Create` 요소를 뷰(`CreateViewType`) 또는 분할(`CreatePType`)을 만드는 데 사용할 수 있는 다른 유형과 혼동하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="057db-126">Do not confuse this `Create` element with the other types that can be used to create views (`CreateViewType`) or partitioning (`CreatePType`).</span></span> <span data-ttu-id="057db-127">이러한 다른 요소 형식에 대 한 자세한 내용은 [데이터베이스 엔진 튜닝 관리자 XML 스키마](https://schemas.microsoft.com/sqlserver/) 를 참조 `Create` 하세요.</span><span class="sxs-lookup"><span data-stu-id="057db-127">Refer to the [Database Engine Tuning Advisor XML schema](https://schemas.microsoft.com/sqlserver/) for information about these other `Create` element types.</span></span>  
  
## <a name="example"></a><span data-ttu-id="057db-128">예제</span><span class="sxs-lookup"><span data-stu-id="057db-128">Example</span></span>  
 <span data-ttu-id="057db-129">이 요소의 사용 예를 보려면 [사용자 정의 구성이 포함된 XML 입력 파일 샘플&#40;DTA&#41;](xml-input-file-sample-with-user-specified-configuration-dta.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="057db-129">For a usage example of this element, see the [XML Input File Sample with User-specified Configuration &#40;DTA&#41;](xml-input-file-sample-with-user-specified-configuration-dta.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="057db-130">참고 항목</span><span class="sxs-lookup"><span data-stu-id="057db-130">See Also</span></span>  
 [<span data-ttu-id="057db-131">XML 입력 파일 참조&#40;데이터베이스 엔진 튜닝 관리자&#41;</span><span class="sxs-lookup"><span data-stu-id="057db-131">XML Input File Reference &#40;Database Engine Tuning Advisor&#41;</span></span>](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
