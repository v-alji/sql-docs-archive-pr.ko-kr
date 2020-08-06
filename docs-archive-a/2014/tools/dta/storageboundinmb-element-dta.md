---
title: StorageBoundInMB 요소 (DTA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- StorageBoundInMB element
ms.assetid: a8374910-bf68-4edb-b464-53a3a705e7f4
author: stevestein
ms.author: sstein
ms.openlocfilehash: ea49b0af981b8f8d96efb087033d8f1466364c76
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87735752"
---
# <a name="storageboundinmb-element-dta"></a><span data-ttu-id="d4d16-102">StorageBoundInMB 요소(DTA)</span><span class="sxs-lookup"><span data-stu-id="d4d16-102">StorageBoundInMB Element (DTA)</span></span>
  <span data-ttu-id="d4d16-103">데이터베이스 엔진 튜닝 관리자 튜닝 권장 구성(인덱스 및 분할 집합)에 사용될 수 있는 최대 공간(MB)을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d4d16-103">Specifies the maximum space in megabytes that can be consumed by the Database Engine Tuning Advisor tuning recommendation (index and partitioning set).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4d16-104">구문</span><span class="sxs-lookup"><span data-stu-id="d4d16-104">Syntax</span></span>  
  
```  
  
<DTAInput>  
...code removed...  
    <TuningOptions>  
      <StorageBoundInMB>...</ StorageBoundInMB >  
```  
  
## <a name="element-characteristics"></a><span data-ttu-id="d4d16-105">요소 특징</span><span class="sxs-lookup"><span data-stu-id="d4d16-105">Element Characteristics</span></span>  
  
|<span data-ttu-id="d4d16-106">특성</span><span class="sxs-lookup"><span data-stu-id="d4d16-106">Characteristic</span></span>|<span data-ttu-id="d4d16-107">Description</span><span class="sxs-lookup"><span data-stu-id="d4d16-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="d4d16-108">**데이터 형식 및 길이**</span><span class="sxs-lookup"><span data-stu-id="d4d16-108">**Data type and length**</span></span>|<span data-ttu-id="d4d16-109">`unsignedInt`, 길이 제한 없음</span><span class="sxs-lookup"><span data-stu-id="d4d16-109">`unsignedInt`, unlimited length.</span></span>|  
|<span data-ttu-id="d4d16-110">**기본값**</span><span class="sxs-lookup"><span data-stu-id="d4d16-110">**Default value**</span></span>|<span data-ttu-id="d4d16-111">없음</span><span class="sxs-lookup"><span data-stu-id="d4d16-111">None.</span></span>|  
|<span data-ttu-id="d4d16-112">**발생 빈도**</span><span class="sxs-lookup"><span data-stu-id="d4d16-112">**Occurrence**</span></span>|<span data-ttu-id="d4d16-113">(선택 사항)</span><span class="sxs-lookup"><span data-stu-id="d4d16-113">Optional.</span></span> <span data-ttu-id="d4d16-114">`TuningOptions` 요소에 한 번만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d4d16-114">Can only be used once for the `TuningOptions` element.</span></span>|  
  
## <a name="element-relationships"></a><span data-ttu-id="d4d16-115">요소 관계</span><span class="sxs-lookup"><span data-stu-id="d4d16-115">Element Relationships</span></span>  
  
|<span data-ttu-id="d4d16-116">관계</span><span class="sxs-lookup"><span data-stu-id="d4d16-116">Relationship</span></span>|<span data-ttu-id="d4d16-117">요소</span><span class="sxs-lookup"><span data-stu-id="d4d16-117">Elements</span></span>|  
|------------------|--------------|  
|<span data-ttu-id="d4d16-118">**부모 요소**</span><span class="sxs-lookup"><span data-stu-id="d4d16-118">**Parent element**</span></span>|[<span data-ttu-id="d4d16-119">TuningOptions 요소&#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="d4d16-119">TuningOptions Element &#40;DTA&#41;</span></span>](tuningoptions-element-dta.md)|  
|<span data-ttu-id="d4d16-120">**자식 요소**</span><span class="sxs-lookup"><span data-stu-id="d4d16-120">**Child elements**</span></span>|<span data-ttu-id="d4d16-121">None</span><span class="sxs-lookup"><span data-stu-id="d4d16-121">None</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d4d16-122">설명</span><span class="sxs-lookup"><span data-stu-id="d4d16-122">Remarks</span></span>  
 <span data-ttu-id="d4d16-123">여러 개의 데이터베이스를 튜닝할 경우 모든 데이터베이스에 대한 권장 구성은 공간 계산을 고려하여 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="d4d16-123">When multiple databases are tuned, recommendations for all databases are considered for the space calculation.</span></span> <span data-ttu-id="d4d16-124">기본적으로 데이터베이스 엔진 튜닝 관리자는 다음 스토리지 크기보다 작은 공간을 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="d4d16-124">By default, Database Engine Tuning Advisor assumes the smaller of the following storage sizes:</span></span>  
  
-   <span data-ttu-id="d4d16-125">현재 원시 데이터 크기의 3배이며 테이블에 있는 힙과 클러스터형 인덱스의 전체 크기를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="d4d16-125">Three times the current raw data size, which includes the total size of heaps and clustered indexes on tables.</span></span>  
  
-   <span data-ttu-id="d4d16-126">연결된 모든 디스크 드라이브의 여유 공간과 원시 데이터 크기를 더한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="d4d16-126">The free space on all attached disk drives plus the raw data size.</span></span>  
  
 <span data-ttu-id="d4d16-127">기본 스토리지 크기는 비클러스터형 인덱스 및 인덱싱된 뷰를 포함하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d4d16-127">The default storage size does not include nonclustered indexes and indexed views.</span></span>  
  
 <span data-ttu-id="d4d16-128">`StorageBoundInMB` 요소에 지정된 값이 실제 디스크 공간을 초과할 경우 데이터베이스 엔진 튜닝 관리자는 오류를 반환하지만 튜닝 작업은 계속합니다.</span><span class="sxs-lookup"><span data-stu-id="d4d16-128">If the value specified for the `StorageBoundInMB` element exceeds the actual disk space, Database Engine Tuning Advisor returns an error, but continues tuning.</span></span> <span data-ttu-id="d4d16-129">튜닝이 완료된 후 권장 구성을 구현하려는 경우에는 디스크 공간을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d4d16-129">After tuning is complete, you can add disk space if you decide to implement the recommendation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d4d16-130">예제</span><span class="sxs-lookup"><span data-stu-id="d4d16-130">Example</span></span>  
  
## <a name="description"></a><span data-ttu-id="d4d16-131">Description</span><span class="sxs-lookup"><span data-stu-id="d4d16-131">Description</span></span>  
 <span data-ttu-id="d4d16-132">다음 코드 예에서는 튜닝 권장 구성에서 사용할 수 있는 최대 디스크 공간으로 1500MB를 설정하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="d4d16-132">The following code example shows how to set a limit of 1500 megabytes as the maximum disk space that a tuning recommendation can consume:</span></span>  
  
## <a name="code"></a><span data-ttu-id="d4d16-133">코드</span><span class="sxs-lookup"><span data-stu-id="d4d16-133">Code</span></span>  
  
```  
<DTAInput>  
  <Server>...</Server>  
  <Workload>...</Workload>  
  <TuningOptions>  
    <StorageBoundInMB>1500</StorageBoundInMB>  
...code removed here...  
</DTAInput>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d4d16-134">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d4d16-134">See Also</span></span>  
 [<span data-ttu-id="d4d16-135">XML 입력 파일 참조&#40;데이터베이스 엔진 튜닝 관리자&#41;</span><span class="sxs-lookup"><span data-stu-id="d4d16-135">XML Input File Reference &#40;Database Engine Tuning Advisor&#41;</span></span>](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
