---
title: 집계 변환 편집기 (집계 탭) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.aggregationtransformation.aggregations.f1
helpviewer_keywords:
- Aggregate Transformation Editor
ms.assetid: a01cb124-ec79-4673-b1a1-bf4d60ee1b45
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 30cafb68a69a061fe4b79e832f356b82926c9761
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648524"
---
# <a name="aggregate-transformation-editor-aggregations-tab"></a><span data-ttu-id="51128-102">집계 변환 편집기(집계 탭)</span><span class="sxs-lookup"><span data-stu-id="51128-102">Aggregate Transformation Editor (Aggregations Tab)</span></span>
  <span data-ttu-id="51128-103">**집계 변환 편집기** 대화 상자의 **집계** 탭을 사용하여 집계 및 집계 속성에 대한 열을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51128-103">Use the **Aggregations** tab of the **Aggregate Transformation Editor** dialog box to specify columns for aggregation and aggregation properties.</span></span> <span data-ttu-id="51128-104">이때 여러 집계를 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51128-104">You can apply multiple aggregations.</span></span> <span data-ttu-id="51128-105">이 변환으로 인해 오류 출력이 생성되지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="51128-105">This transformation does not generate an error output.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="51128-106">키 수, 키 배율, 고유 키 수, 고유 수 배율 옵션은 **고급** 탭에서 지정하면 구성 요소 수준에서 적용되고, **집계** 탭의 고급 디스플레이에서 지정하면 출력 수준에서 적용되고, **집계** 탭의 아래쪽에 있는 열 목록에서 지정하면 열 수준에서 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="51128-106">The options for key count, key scale, distinct key count, and distinct key scale apply at the component level when specified on the **Advanced** tab, at the output level when specified in the advanced display of the **Aggregations** tab, and at the column level when specified in the column list at the bottom of the **Aggregations** tab.</span></span>  
>   
>  <span data-ttu-id="51128-107">집계 변환에서 **키** 및 **키 배율** 은 **Group by** 연산의 결과로 반환될 그룹 수를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="51128-107">In the Aggregate transformation, **Keys** and **Keys scale** refer to the number of groups that are expected to result from a **Group by** operation.</span></span> <span data-ttu-id="51128-108">**고유 키 수** 및 **고유 수 배율** 은 **고유 카운트** 연산의 결과로 반환될 고유 값 수를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="51128-108">**Count distinct keys** and **Count distinct scale** refer to the number of distinct values that are expected to result from a **Distinct count** operation.</span></span>  
  
 <span data-ttu-id="51128-109">집계 변환에 대한 자세한 내용은 [Aggregate Transformation](data-flow/transformations/aggregate-transformation.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="51128-109">To learn more about the Aggregate transformation, see [Aggregate Transformation](data-flow/transformations/aggregate-transformation.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="51128-110">옵션</span><span class="sxs-lookup"><span data-stu-id="51128-110">Options</span></span>  
 <span data-ttu-id="51128-111">**고급/기본**</span><span class="sxs-lookup"><span data-stu-id="51128-111">**Advanced / Basic**</span></span>  
 <span data-ttu-id="51128-112">여러 개의 출력에 대한 여러 집계를 구성하는 옵션을 표시하거나 숨깁니다.</span><span class="sxs-lookup"><span data-stu-id="51128-112">Display or hide options to configure multiple aggregations for multiple outputs.</span></span> <span data-ttu-id="51128-113">기본적으로 고급 옵션은 숨겨져 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51128-113">By default, the Advanced options are hidden.</span></span>  
  
 <span data-ttu-id="51128-114">**집계 이름**</span><span class="sxs-lookup"><span data-stu-id="51128-114">**Aggregation Name**</span></span>  
 <span data-ttu-id="51128-115">고급 디스플레이에서 집계의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="51128-115">In the Advanced display, type a friendly name for the aggregation.</span></span>  
  
 <span data-ttu-id="51128-116">**Group By 열**</span><span class="sxs-lookup"><span data-stu-id="51128-116">**Group By Columns**</span></span>  
 <span data-ttu-id="51128-117">고급 디스플레이에서 아래에 설명된 **사용 가능한 입력 열** 목록을 사용하여 그룹화할 열을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="51128-117">In the Advanced display, select columns for grouping by using the **Available Input Columns** list as described below.</span></span>  
  
 <span data-ttu-id="51128-118">**키 배율**</span><span class="sxs-lookup"><span data-stu-id="51128-118">**Key Scale**</span></span>  
 <span data-ttu-id="51128-119">고급 디스플레이에서 필요에 따라 집계가 쓸 수 있는 키의 수를 대략적으로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="51128-119">In the Advanced display, optionally specify the approximate number of keys that the aggregation can write.</span></span> <span data-ttu-id="51128-120">이 옵션의 기본값은 **Unspecified**입니다.</span><span class="sxs-lookup"><span data-stu-id="51128-120">By default, the value of this option is **Unspecified**.</span></span> <span data-ttu-id="51128-121">**키 배율** 과 **키** 속성을 모두 설정하면 **키** 의 값이 우선 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="51128-121">If both the **Key Scale** and **Keys** properties are set, the value of **Keys** takes precedence.</span></span>  
  
|<span data-ttu-id="51128-122">값</span><span class="sxs-lookup"><span data-stu-id="51128-122">Value</span></span>|<span data-ttu-id="51128-123">Description</span><span class="sxs-lookup"><span data-stu-id="51128-123">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="51128-124">Unspecified</span><span class="sxs-lookup"><span data-stu-id="51128-124">Unspecified</span></span>|<span data-ttu-id="51128-125">키 배율 속성을 사용하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="51128-125">The Key Scale property is not used.</span></span>|  
|<span data-ttu-id="51128-126">낮음</span><span class="sxs-lookup"><span data-stu-id="51128-126">Low</span></span>|<span data-ttu-id="51128-127">집계에서 약 500,000개의 키를 쓸 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51128-127">Aggregation can write approximately 500,000 keys.</span></span>|  
|<span data-ttu-id="51128-128">중간</span><span class="sxs-lookup"><span data-stu-id="51128-128">Medium</span></span>|<span data-ttu-id="51128-129">집계에서 약 5,000,000개의 키를 쓸 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51128-129">Aggregation can write approximately 5,000,000 keys.</span></span>|  
|<span data-ttu-id="51128-130">높은</span><span class="sxs-lookup"><span data-stu-id="51128-130">High</span></span>|<span data-ttu-id="51128-131">집계에서 25,000,000개 이상의 키를 쓸 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51128-131">Aggregation can write more than 25,000,000 keys.</span></span>|  
  
 <span data-ttu-id="51128-132">**키**</span><span class="sxs-lookup"><span data-stu-id="51128-132">**Keys**</span></span>  
 <span data-ttu-id="51128-133">고급 디스플레이에서 필요에 따라 집계가 쓸 수 있는 키의 수를 정확하게 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="51128-133">In the Advanced display, optionally specify the exact number of keys that the aggregation can write.</span></span> <span data-ttu-id="51128-134">**키 배율** 과 **키** 를 모두 지정하면 **키** 의 값이 우선 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="51128-134">If both **Key Scale** and **Keys** are specified, **Keys** takes precedence.</span></span>  
  
 <span data-ttu-id="51128-135">**사용 가능한 입력 열**</span><span class="sxs-lookup"><span data-stu-id="51128-135">**Available Input Columns**</span></span>  
 <span data-ttu-id="51128-136">이 테이블의 확인란을 사용하여 사용 가능한 입력 열 목록에서 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="51128-136">Select from the list of available input columns by using the check boxes in this table.</span></span>  
  
 <span data-ttu-id="51128-137">**입력 열**</span><span class="sxs-lookup"><span data-stu-id="51128-137">**Input Column**</span></span>  
 <span data-ttu-id="51128-138">사용 가능한 입력 열 목록에서 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="51128-138">Select from the list of available input columns.</span></span>  
  
 <span data-ttu-id="51128-139">**출력 별칭**</span><span class="sxs-lookup"><span data-stu-id="51128-139">**Output Alias**</span></span>  
 <span data-ttu-id="51128-140">각 열의 별칭을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="51128-140">Type an alias for each column.</span></span> <span data-ttu-id="51128-141">기본값은 입력 열의 이름이지만 설명이 포함된 고유 이름을 임의로 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51128-141">The default is the name of the input column; however, you can choose any unique, descriptive name.</span></span>  
  
 <span data-ttu-id="51128-142">**작업**</span><span class="sxs-lookup"><span data-stu-id="51128-142">**Operation**</span></span>  
 <span data-ttu-id="51128-143">다음 표를 참조하여 사용 가능한 연산 목록에서 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="51128-143">Choose from the list of available operations, using the following table as a guide.</span></span>  
  
|<span data-ttu-id="51128-144">작업(Operation)</span><span class="sxs-lookup"><span data-stu-id="51128-144">Operation</span></span>|<span data-ttu-id="51128-145">Description</span><span class="sxs-lookup"><span data-stu-id="51128-145">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="51128-146">**GroupBy**</span><span class="sxs-lookup"><span data-stu-id="51128-146">**GroupBy**</span></span>|<span data-ttu-id="51128-147">데이터 세트를 그룹으로 나눕니다.</span><span class="sxs-lookup"><span data-stu-id="51128-147">Divides datasets into groups.</span></span> <span data-ttu-id="51128-148">모든 데이터 형식의 열을 그룹화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51128-148">Columns with any data type can be used for grouping.</span></span> <span data-ttu-id="51128-149">자세한 내용은 GROUP BY를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="51128-149">For more information, see GROUP BY.</span></span>|  
|<span data-ttu-id="51128-150">**총합**</span><span class="sxs-lookup"><span data-stu-id="51128-150">**Sum**</span></span>|<span data-ttu-id="51128-151">열에 있는 값의 합계를 계산합니다.</span><span class="sxs-lookup"><span data-stu-id="51128-151">Sums the values in a column.</span></span> <span data-ttu-id="51128-152">숫자 데이터 형식의 열만 합계를 계산할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51128-152">Only columns with numeric data types can be summed.</span></span> <span data-ttu-id="51128-153">자세한 내용은 SUM을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="51128-153">For more information, see SUM.</span></span>|  
|<span data-ttu-id="51128-154">**평균**</span><span class="sxs-lookup"><span data-stu-id="51128-154">**Average**</span></span>|<span data-ttu-id="51128-155">열에 있는 열 값의 평균을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="51128-155">Returns the average of the column values in a column.</span></span> <span data-ttu-id="51128-156">숫자 데이터 형식의 열만 평균을 계산할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51128-156">Only columns with numeric data types can be averaged.</span></span> <span data-ttu-id="51128-157">자세한 내용은 AVG를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="51128-157">For more information, see AVG.</span></span>|  
|<span data-ttu-id="51128-158">**Count**</span><span class="sxs-lookup"><span data-stu-id="51128-158">**Count**</span></span>|<span data-ttu-id="51128-159">그룹의 항목 개수를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="51128-159">Returns the number of items in a group.</span></span> <span data-ttu-id="51128-160">자세한 내용은 COUNT를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="51128-160">For more information, see COUNT.</span></span>|  
|<span data-ttu-id="51128-161">**CountDistinct**</span><span class="sxs-lookup"><span data-stu-id="51128-161">**CountDistinct**</span></span>|<span data-ttu-id="51128-162">그룹에서 Null이 아닌 고유한 값의 개수를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="51128-162">Returns the number of unique nonnull values in a group.</span></span> <span data-ttu-id="51128-163">자세한 내용은 COUNT 및 DISTINCT를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="51128-163">For more information, see COUNT and Distinct.</span></span>|  
|<span data-ttu-id="51128-164">**최소**</span><span class="sxs-lookup"><span data-stu-id="51128-164">**Minimum**</span></span>|<span data-ttu-id="51128-165">그룹의 최소값을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="51128-165">Returns the minimum value in a group.</span></span> <span data-ttu-id="51128-166">숫자 데이터 형식에서만 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="51128-166">Restricted to numeric data types.</span></span>|  
|<span data-ttu-id="51128-167">**최댓값**</span><span class="sxs-lookup"><span data-stu-id="51128-167">**Maximum**</span></span>|<span data-ttu-id="51128-168">그룹의 최대값을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="51128-168">Returns the maximum value in a group.</span></span> <span data-ttu-id="51128-169">숫자 데이터 형식에서만 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="51128-169">Restricted to numeric data types.</span></span>|  
  
 <span data-ttu-id="51128-170">**비교 플래그**</span><span class="sxs-lookup"><span data-stu-id="51128-170">**Comparison Flags**</span></span>  
 <span data-ttu-id="51128-171">**Group By**를 선택하는 경우 확인란을 사용하여 변환이 비교를 수행하는 방법을 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51128-171">If you choose **Group By**, use the check boxes to control how the transformation performs the comparison.</span></span> <span data-ttu-id="51128-172">문자열 비교 옵션에 대한 자세한 내용은 [Comparing String Data](data-flow/comparing-string-data.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="51128-172">For information on the string comparison options, see [Comparing String Data](data-flow/comparing-string-data.md).</span></span>  
  
 <span data-ttu-id="51128-173">**Count Distinct Scale**</span><span class="sxs-lookup"><span data-stu-id="51128-173">**Count Distinct Scale**</span></span>  
 <span data-ttu-id="51128-174">필요에 따라 집계에서 쓸 수 있는 고유한 값의 수를 대략적으로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="51128-174">Optionally specify the approximate number of distinct values that the aggregation can write.</span></span> <span data-ttu-id="51128-175">이 옵션의 기본값은 **Unspecified**입니다.</span><span class="sxs-lookup"><span data-stu-id="51128-175">By default, the value of this option is **Unspecified**.</span></span> <span data-ttu-id="51128-176">`CountDistinctScale`및 **CountDistinctKeys** 가 모두 지정 된 경우 **CountDistinctKeys** 가 우선적으로 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="51128-176">If both `CountDistinctScale` and **CountDistinctKeys** are specified, **CountDistinctKeys** takes precedence.</span></span>  
  
|<span data-ttu-id="51128-177">값</span><span class="sxs-lookup"><span data-stu-id="51128-177">Value</span></span>|<span data-ttu-id="51128-178">Description</span><span class="sxs-lookup"><span data-stu-id="51128-178">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="51128-179">Unspecified</span><span class="sxs-lookup"><span data-stu-id="51128-179">Unspecified</span></span>|<span data-ttu-id="51128-180">`CountDistinctScale` 속성을 사용하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="51128-180">The `CountDistinctScale` property is not used.</span></span>|  
|<span data-ttu-id="51128-181">낮음</span><span class="sxs-lookup"><span data-stu-id="51128-181">Low</span></span>|<span data-ttu-id="51128-182">집계에서 약 500,000개의 고유한 값을 쓸 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51128-182">Aggregation can write approximately 500,000 distinct values.</span></span>|  
|<span data-ttu-id="51128-183">중간</span><span class="sxs-lookup"><span data-stu-id="51128-183">Medium</span></span>|<span data-ttu-id="51128-184">집계에서 약 5,000,000개의 고유한 값을 쓸 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51128-184">Aggregation can write approximately 5,000,000 distinct values.</span></span>|  
|<span data-ttu-id="51128-185">높은</span><span class="sxs-lookup"><span data-stu-id="51128-185">High</span></span>|<span data-ttu-id="51128-186">집계에서 25,000,000개 이상의 고유한 값을 쓸 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51128-186">Aggregation can write more than 25,000,000 distinct values.</span></span>|  
  
 <span data-ttu-id="51128-187">**Count Distinct Keys**</span><span class="sxs-lookup"><span data-stu-id="51128-187">**Count Distinct Keys**</span></span>  
 <span data-ttu-id="51128-188">필요에 따라 집계에서 쓸 수 있는 고유한 값의 수를 정확하게 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="51128-188">Optionally specify the exact number of distinct values that the aggregation can write.</span></span> <span data-ttu-id="51128-189">`CountDistinctScale`및 **CountDistinctKeys** 가 모두 지정 된 경우 **CountDistinctKeys** 가 우선적으로 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="51128-189">If both `CountDistinctScale` and **CountDistinctKeys** are specified, **CountDistinctKeys** takes precedence.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51128-190">참고 항목</span><span class="sxs-lookup"><span data-stu-id="51128-190">See Also</span></span>  
 <span data-ttu-id="51128-191">[Integration Services 오류 및 메시지 참조](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="51128-191">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="51128-192">[집계 변환 편집기 &#40;고급 탭&#41;](../../2014/integration-services/aggregate-transformation-editor-advanced-tab.md) </span><span class="sxs-lookup"><span data-stu-id="51128-192">[Aggregate Transformation Editor &#40;Advanced Tab&#41;](../../2014/integration-services/aggregate-transformation-editor-advanced-tab.md) </span></span>  
 [<span data-ttu-id="51128-193">집계 변환을 사용하여 데이터 세트의 값 집계</span><span class="sxs-lookup"><span data-stu-id="51128-193">Aggregate Values in a Dataset by Using the Aggregate Transformation</span></span>](data-flow/transformations/aggregate-values-in-a-dataset-by-using-the-aggregate-transformation.md)  
  
  
