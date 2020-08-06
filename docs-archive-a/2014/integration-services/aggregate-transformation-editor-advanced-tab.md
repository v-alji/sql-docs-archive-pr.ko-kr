---
title: 집계 변환 편집기 (고급 탭) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.aggregationtransformation.advanced.f1
helpviewer_keywords:
- Aggregate Transformation Editor
ms.assetid: 186a9736-2554-40a0-9cb2-877a8db5fde8
author: chugugrace
ms.author: chugu
ms.openlocfilehash: cb3742a83f363f74004a5aac0eefc589ee2a5be2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648527"
---
# <a name="aggregate-transformation-editor-advanced-tab"></a><span data-ttu-id="f0db1-102">집계 변환 편집기(고급 탭)</span><span class="sxs-lookup"><span data-stu-id="f0db1-102">Aggregate Transformation Editor (Advanced Tab)</span></span>
  <span data-ttu-id="f0db1-103">**집계 변환 편집기** 대화 상자의 **고급** 탭을 사용하여 구성 요소 속성을 설정하고, 집계를 지정하고, 입력 및 출력 열의 속성을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f0db1-103">Use the **Advanced** tab of the **Aggregate Transformation Editor** dialog box to set component properties, specify aggregations, and set properties of input and output columns.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f0db1-104">키 수, 키 배율, 고유 키 수, 고유 수 배율 옵션은 **고급** 탭에서 지정하면 구성 요소 수준에서 적용되고, **집계** 탭의 고급 디스플레이에서 지정하면 출력 수준에서 적용되고, **집계** 탭의 아래쪽에 있는 열 목록에서 지정하면 열 수준에서 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="f0db1-104">The options for key count, key scale, distinct key count, and distinct key scale apply at the component level when specified on the **Advanced** tab, at the output level when specified in the advanced display of the **Aggregations** tab, and at the column level when specified in the column list at the bottom of the **Aggregations** tab.</span></span>  
>   
>  <span data-ttu-id="f0db1-105">집계 변환에서 **키** 및 **키 배율** 은 **Group by** 연산의 결과로 반환될 그룹 수를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="f0db1-105">In the Aggregate transformation, **Keys** and **Keys scale** refer to the number of groups that are expected to result from a **Group by** operation.</span></span> <span data-ttu-id="f0db1-106">**고유 키 수** 및 **고유 수 배율** 은 **고유 카운트** 연산의 결과로 반환될 고유 값 수를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="f0db1-106">**Count distinct keys** and **Count distinct scale** refer to the number of distinct values that are expected to result from a **Distinct count** operation.</span></span>  
  
 <span data-ttu-id="f0db1-107">집계 변환에 대한 자세한 내용은 [Aggregate Transformation](data-flow/transformations/aggregate-transformation.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="f0db1-107">To learn more about the Aggregate transformation, see [Aggregate Transformation](data-flow/transformations/aggregate-transformation.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="f0db1-108">옵션</span><span class="sxs-lookup"><span data-stu-id="f0db1-108">Options</span></span>  
 <span data-ttu-id="f0db1-109">**키 배율**</span><span class="sxs-lookup"><span data-stu-id="f0db1-109">**Keys scale**</span></span>  
 <span data-ttu-id="f0db1-110">필요에 따라 집계에 필요한 키 수를 대략적으로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f0db1-110">Optionally specify the approximate number of keys that the aggregation expects.</span></span> <span data-ttu-id="f0db1-111">변환 시 이 정보를 사용하여 최초 캐시 크기를 최적화합니다.</span><span class="sxs-lookup"><span data-stu-id="f0db1-111">The transformation uses this information to optimize its initial cache size.</span></span> <span data-ttu-id="f0db1-112">이 옵션의 기본값은 **Unspecified**입니다.</span><span class="sxs-lookup"><span data-stu-id="f0db1-112">By default, the value of this option is **Unspecified**.</span></span> <span data-ttu-id="f0db1-113">**키 배율** 과 **키 수** 를 모두 지정하면 **키 수** 가 우선 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="f0db1-113">If both **Keys scale** and **Number of keys** are specified, **Number of keys** takes precedence.</span></span>  
  
|<span data-ttu-id="f0db1-114">값</span><span class="sxs-lookup"><span data-stu-id="f0db1-114">Value</span></span>|<span data-ttu-id="f0db1-115">Description</span><span class="sxs-lookup"><span data-stu-id="f0db1-115">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="f0db1-116">Unspecified</span><span class="sxs-lookup"><span data-stu-id="f0db1-116">Unspecified</span></span>|<span data-ttu-id="f0db1-117">**키 배율** 속성이 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f0db1-117">The **Keys scale** property is not used.</span></span>|  
|<span data-ttu-id="f0db1-118">낮음</span><span class="sxs-lookup"><span data-stu-id="f0db1-118">Low</span></span>|<span data-ttu-id="f0db1-119">집계에서 약 500,000개의 키를 쓸 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f0db1-119">Aggregation can write approximately 500,000 keys.</span></span>|  
|<span data-ttu-id="f0db1-120">중간</span><span class="sxs-lookup"><span data-stu-id="f0db1-120">Medium</span></span>|<span data-ttu-id="f0db1-121">집계에서 약 5,000,000개의 키를 쓸 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f0db1-121">Aggregation can write approximately 5,000,000 keys.</span></span>|  
|<span data-ttu-id="f0db1-122">높은</span><span class="sxs-lookup"><span data-stu-id="f0db1-122">High</span></span>|<span data-ttu-id="f0db1-123">집계에서 25,000,000개 이상의 키를 쓸 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f0db1-123">Aggregation can write more than 25,000,000 keys.</span></span>|  
  
 <span data-ttu-id="f0db1-124">**키 수**</span><span class="sxs-lookup"><span data-stu-id="f0db1-124">**Number of keys**</span></span>  
 <span data-ttu-id="f0db1-125">필요에 따라 집계에 필요한 키 수를 정확하게 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f0db1-125">Optionally specify the exact number of keys that the aggregation expects.</span></span> <span data-ttu-id="f0db1-126">변환 시 이 정보를 사용하여 최초 캐시 크기를 최적화합니다.</span><span class="sxs-lookup"><span data-stu-id="f0db1-126">The transformation uses this information to optimize its initial cache size.</span></span> <span data-ttu-id="f0db1-127">**키 배율** 과 **키 수** 를 모두 지정하면 **키 수** 가 우선 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="f0db1-127">If both **Keys scale** and **Number of keys** are specified, **Number of keys** takes precedence.</span></span>  
  
 <span data-ttu-id="f0db1-128">**고유 수 배율**</span><span class="sxs-lookup"><span data-stu-id="f0db1-128">**Count distinct scale**</span></span>  
 <span data-ttu-id="f0db1-129">필요에 따라 집계에서 쓸 수 있는 고유한 값의 수를 대략적으로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f0db1-129">Optionally specify the approximate number of distinct values that the aggregation can write.</span></span> <span data-ttu-id="f0db1-130">이 옵션의 기본값은 **Unspecified**입니다.</span><span class="sxs-lookup"><span data-stu-id="f0db1-130">By default, the value of this option is **Unspecified**.</span></span> <span data-ttu-id="f0db1-131">**고유 수 배율** 과 **고유 키 수** 를 모두 지정하면 **고유 키 수** 가 우선 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="f0db1-131">If both **Count distinct scale** and **Count distinct keys** are specified, **Count distinct keys** takes precedence.</span></span>  
  
|<span data-ttu-id="f0db1-132">값</span><span class="sxs-lookup"><span data-stu-id="f0db1-132">Value</span></span>|<span data-ttu-id="f0db1-133">Description</span><span class="sxs-lookup"><span data-stu-id="f0db1-133">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="f0db1-134">Unspecified</span><span class="sxs-lookup"><span data-stu-id="f0db1-134">Unspecified</span></span>|<span data-ttu-id="f0db1-135">CountDistinctScale 속성이 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f0db1-135">The CountDistinctScale property is not used.</span></span>|  
|<span data-ttu-id="f0db1-136">낮음</span><span class="sxs-lookup"><span data-stu-id="f0db1-136">Low</span></span>|<span data-ttu-id="f0db1-137">집계에서 약 500,000개의 고유한 값을 쓸 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f0db1-137">Aggregation can write approximately 500,000 distinct values.</span></span>|  
|<span data-ttu-id="f0db1-138">중간</span><span class="sxs-lookup"><span data-stu-id="f0db1-138">Medium</span></span>|<span data-ttu-id="f0db1-139">집계에서 약 5,000,000개의 고유한 값을 쓸 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f0db1-139">Aggregation can write approximately 5,000,000 distinct values.</span></span>|  
|<span data-ttu-id="f0db1-140">높은</span><span class="sxs-lookup"><span data-stu-id="f0db1-140">High</span></span>|<span data-ttu-id="f0db1-141">집계에서 25,000,000개 이상의 고유한 값을 쓸 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f0db1-141">Aggregation can write more than 25,000,000 distinct values.</span></span>|  
  
 <span data-ttu-id="f0db1-142">**고유 키 수**</span><span class="sxs-lookup"><span data-stu-id="f0db1-142">**Count distinct keys**</span></span>  
 <span data-ttu-id="f0db1-143">필요에 따라 집계에서 쓸 수 있는 고유한 값의 수를 정확하게 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f0db1-143">Optionally specify the exact number of distinct values that the aggregation can write.</span></span> <span data-ttu-id="f0db1-144">**고유 수 배율** 과 **고유 키 수** 를 모두 지정하면 **고유 키 수** 가 우선 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="f0db1-144">If both **Count distinct scale** and **Count distinct keys** are specified, **Count distinct keys** takes precedence.</span></span>  
  
 <span data-ttu-id="f0db1-145">**자동 확장 비율**</span><span class="sxs-lookup"><span data-stu-id="f0db1-145">**Auto extend factor**</span></span>  
 <span data-ttu-id="f0db1-146">1에서 100 사이의 값을 사용하여 집계 중에 메모리를 확장할 수 있는 비율을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f0db1-146">Use a value between 1 and 100 to specify the percentage by which memory can be extended during the aggregation.</span></span> <span data-ttu-id="f0db1-147">이 옵션의 기본값은 **25%** 입니다.</span><span class="sxs-lookup"><span data-stu-id="f0db1-147">By default, the value of this option is **25%**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0db1-148">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f0db1-148">See Also</span></span>  
 <span data-ttu-id="f0db1-149">[Integration Services 오류 및 메시지 참조](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="f0db1-149">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="f0db1-150">[집계 변환 편집기 &#40;집계 탭&#41;](../../2014/integration-services/aggregate-transformation-editor-aggregations-tab.md) </span><span class="sxs-lookup"><span data-stu-id="f0db1-150">[Aggregate Transformation Editor &#40;Aggregations Tab&#41;](../../2014/integration-services/aggregate-transformation-editor-aggregations-tab.md) </span></span>  
 [<span data-ttu-id="f0db1-151">집계 변환을 사용하여 데이터 세트의 값 집계</span><span class="sxs-lookup"><span data-stu-id="f0db1-151">Aggregate Values in a Dataset by Using the Aggregate Transformation</span></span>](data-flow/transformations/aggregate-values-in-a-dataset-by-using-the-aggregate-transformation.md)  
  
  
