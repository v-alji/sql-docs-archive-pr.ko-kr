---
title: 집계 변환 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.aggregatetrans.f1
helpviewer_keywords:
- IsBig property
- aggregate functions [Integration Services]
- Aggregate transformation [Integration Services]
- large data, SSIS transformations
ms.assetid: 2871cf2a-fbd3-41ba-807d-26ffff960e81
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 9e69d741ddd2bd14a31d7aa79a8c825641713523
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728528"
---
# <a name="aggregate-transformation"></a><span data-ttu-id="d77f7-102">집계 변환</span><span class="sxs-lookup"><span data-stu-id="d77f7-102">Aggregate Transformation</span></span>
  <span data-ttu-id="d77f7-103">집계 변환은 Average와 같은 집계 함수를 열 값에 적용하고 결과를 변환 출력에 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="d77f7-103">The Aggregate transformation applies aggregate functions, such as Average, to column values and copies the results to the transformation output.</span></span> <span data-ttu-id="d77f7-104">집계 함수 외에도 변환은 집계할 그룹을 지정하는 데 사용할 수 있는 GROUP BY 절을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="d77f7-104">Besides aggregate functions, the transformation provides the GROUP BY clause, which you can use to specify groups to aggregate across.</span></span>  
  
## <a name="operations"></a><span data-ttu-id="d77f7-105">작업</span><span class="sxs-lookup"><span data-stu-id="d77f7-105">Operations</span></span>  
 <span data-ttu-id="d77f7-106">집계 변환은 다음과 같은 연산을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="d77f7-106">The Aggregate transformation supports the following operations.</span></span>  
  
|<span data-ttu-id="d77f7-107">작업(Operation)</span><span class="sxs-lookup"><span data-stu-id="d77f7-107">Operation</span></span>|<span data-ttu-id="d77f7-108">Description</span><span class="sxs-lookup"><span data-stu-id="d77f7-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d77f7-109">Group By</span><span class="sxs-lookup"><span data-stu-id="d77f7-109">Group by</span></span>|<span data-ttu-id="d77f7-110">데이터 세트를 그룹으로 나눕니다.</span><span class="sxs-lookup"><span data-stu-id="d77f7-110">Divides datasets into groups.</span></span> <span data-ttu-id="d77f7-111">그룹화에는 모든 종류의 데이터 형식의 열을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d77f7-111">Columns of any data type can be used for grouping.</span></span> <span data-ttu-id="d77f7-112">자세한 내용은 [GROUP BY&#40;Transact-SQL&#41;](/sql/t-sql/queries/select-group-by-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d77f7-112">For more information, see [GROUP BY &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-group-by-transact-sql).</span></span>|  
|<span data-ttu-id="d77f7-113">합계</span><span class="sxs-lookup"><span data-stu-id="d77f7-113">Sum</span></span>|<span data-ttu-id="d77f7-114">열에 있는 값의 합계를 계산합니다.</span><span class="sxs-lookup"><span data-stu-id="d77f7-114">Sums the values in a column.</span></span> <span data-ttu-id="d77f7-115">숫자 데이터 형식의 열만 합계를 계산할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d77f7-115">Only columns with numeric data types can be summed.</span></span> <span data-ttu-id="d77f7-116">자세한 내용은 [SUM&#40;Transact-SQL&#41;](/sql/t-sql/functions/sum-transact-sql)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d77f7-116">For more information, see [SUM &#40;Transact-SQL&#41;](/sql/t-sql/functions/sum-transact-sql).</span></span>|  
|<span data-ttu-id="d77f7-117">평균</span><span class="sxs-lookup"><span data-stu-id="d77f7-117">Average</span></span>|<span data-ttu-id="d77f7-118">열에 있는 열 값의 평균을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="d77f7-118">Returns the average of the column values in a column.</span></span> <span data-ttu-id="d77f7-119">숫자 데이터 형식의 열만 평균을 계산할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d77f7-119">Only columns with numeric data types can be averaged.</span></span> <span data-ttu-id="d77f7-120">자세한 내용은 [AVG&#40;Transact-SQL&#41;](/sql/t-sql/functions/avg-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d77f7-120">For more information, see [AVG &#40;Transact-SQL&#41;](/sql/t-sql/functions/avg-transact-sql).</span></span>|  
|<span data-ttu-id="d77f7-121">개수</span><span class="sxs-lookup"><span data-stu-id="d77f7-121">Count</span></span>|<span data-ttu-id="d77f7-122">그룹의 항목 개수를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="d77f7-122">Returns the number of items in a group.</span></span> <span data-ttu-id="d77f7-123">자세한 내용은 [COUNT&#40;Transact-SQL&#41;](/sql/t-sql/functions/count-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d77f7-123">For more information, see [COUNT &#40;Transact-SQL&#41;](/sql/t-sql/functions/count-transact-sql).</span></span>|  
|<span data-ttu-id="d77f7-124">Count distinct</span><span class="sxs-lookup"><span data-stu-id="d77f7-124">Count distinct</span></span>|<span data-ttu-id="d77f7-125">그룹에서 Null이 아닌 고유한 값의 개수를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="d77f7-125">Returns the number of unique nonnull values in a group.</span></span>|  
|<span data-ttu-id="d77f7-126">최소</span><span class="sxs-lookup"><span data-stu-id="d77f7-126">Minimum</span></span>|<span data-ttu-id="d77f7-127">그룹의 최소값을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="d77f7-127">Returns the minimum value in a group.</span></span> <span data-ttu-id="d77f7-128">자세한 내용은 [MIN&#40;Transact-SQL&#41;](/sql/t-sql/functions/min-transact-sql)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d77f7-128">For more information, see [MIN &#40;Transact-SQL&#41;](/sql/t-sql/functions/min-transact-sql).</span></span> <span data-ttu-id="d77f7-129">Transact-SQL MIN 함수와는 반대로 이 연산은 숫자, 날짜 및 시간 데이터 형식에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d77f7-129">In contrast to the Transact-SQL MIN function, this operation can be used only with numeric, date, and time data types.</span></span>|  
|<span data-ttu-id="d77f7-130">최대</span><span class="sxs-lookup"><span data-stu-id="d77f7-130">Maximum</span></span>|<span data-ttu-id="d77f7-131">그룹의 최대값을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="d77f7-131">Returns the maximum value in a group.</span></span> <span data-ttu-id="d77f7-132">자세한 내용은 [MAX&#40;Transact-SQL&#41;](/sql/t-sql/functions/max-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d77f7-132">For more information, see [MAX &#40;Transact-SQL&#41;](/sql/t-sql/functions/max-transact-sql).</span></span> <span data-ttu-id="d77f7-133">Transact-SQL MAX 함수와는 반대로 이 연산은 숫자, 날짜 및 시간 데이터 형식에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d77f7-133">In contrast to the Transact-SQL MAX function, this operation can be used only with numeric, date, and time data types.</span></span>|  
  
 <span data-ttu-id="d77f7-134">집계 변환은 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 관계형 데이터베이스 엔진과 동일한 방식으로 Null 값을 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="d77f7-134">The Aggregate transformation handles null values in the same way as the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] relational database engine.</span></span> <span data-ttu-id="d77f7-135">이러한 동작은 SQL-92 표준에서 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="d77f7-135">The behavior is defined in the SQL-92 standard.</span></span> <span data-ttu-id="d77f7-136">다음 규칙이 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="d77f7-136">The following rules apply:</span></span>  
  
-   <span data-ttu-id="d77f7-137">GROUP BY 절에서 Null은 다른 열 값과 같이 취급됩니다.</span><span class="sxs-lookup"><span data-stu-id="d77f7-137">In a GROUP BY clause, nulls are treated like other column values.</span></span> <span data-ttu-id="d77f7-138">그룹화 열에 둘 이상의 Null 값이 있다면 단일 그룹에 이 Null 값을 둡니다.</span><span class="sxs-lookup"><span data-stu-id="d77f7-138">If the grouping column contains more than one null value, the null values are put into a single group.</span></span>  
  
-   <span data-ttu-id="d77f7-139">COUNT(column name) 및 COUNT (DISTINCT column name) 함수에서는 Null이 무시되고 결과에는 명명된 열에 Null 값이 포함된 행이 제외됩니다.</span><span class="sxs-lookup"><span data-stu-id="d77f7-139">In the COUNT (column name) and COUNT (DISTINCT column name) functions, nulls are ignored and the result excludes rows that contain null values in the named column.</span></span>  
  
-   <span data-ttu-id="d77f7-140">COUNT (\*) 함수에서는 Null 값이 포함된 행을 비롯한 모든 행의 개수가 계산됩니다.</span><span class="sxs-lookup"><span data-stu-id="d77f7-140">In the COUNT (\*) function, all rows are counted, including rows with null values.</span></span>  
  
## <a name="big-numbers-in-aggregates"></a><span data-ttu-id="d77f7-141">집계의 큰 숫자</span><span class="sxs-lookup"><span data-stu-id="d77f7-141">Big Numbers in Aggregates</span></span>  
 <span data-ttu-id="d77f7-142">열에는 필요한 값이나 전체 자릿수가 크기 때문에 특별한 고려가 필요한 숫자 값이 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d77f7-142">A column may contain numeric values that require special consideration because of their large value or precision requirements.</span></span> <span data-ttu-id="d77f7-143">집계 변환에는 숫자가 크거나 전체 자릿수가 많은 경우를 특별하게 처리하기 위해 출력 열에 설정할 수 있는 IsBig 속성이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="d77f7-143">The Aggregation transformation includes the IsBig property, which you can set on output columns to invoke special handling of big or high-precision numbers.</span></span> <span data-ttu-id="d77f7-144">열 값이 40억을 넘거나 부동 소수점 데이터 형식보다 큰 전체 자릿수가 필요한 경우에는 IsBig을 1로 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d77f7-144">If a column value may exceed 4 billion or a precision beyond a float data type is required, IsBig should be set to 1.</span></span>  
  
 <span data-ttu-id="d77f7-145">IsBig 속성을 1로 설정하면 집계 변환의 출력이 다음과 같이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d77f7-145">Setting the IsBig property to 1 affects the output of the aggregation transformation in the following ways:</span></span>  
  
-   <span data-ttu-id="d77f7-146">DT_R4 데이터 형식 대신 DT_R8 데이터 형식이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="d77f7-146">The DT_R8 data type is used instead of the DT_R4 data type.</span></span>  
  
-   <span data-ttu-id="d77f7-147">카운트 결과가 DT_UI8 데이터 형식으로 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="d77f7-147">Count results are stored as the DT_UI8 data type.</span></span>  
  
-   <span data-ttu-id="d77f7-148">고유 카운트 결과가 DT_UI4 데이터 형식으로 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="d77f7-148">Distinct count results are stored as the DT_UI4 data type.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d77f7-149">GROUP BY, Maximum 또는 Minimum 연산에서 사용되는 열에는 IsBig을 1로 설정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d77f7-149">You cannot set IsBig to 1 on columns that are used in the GROUP BY, Maximum, or Minimum operations.</span></span>  
  
## <a name="performance-considerations"></a><span data-ttu-id="d77f7-150">성능 고려 사항</span><span class="sxs-lookup"><span data-stu-id="d77f7-150">Performance Considerations</span></span>  
 <span data-ttu-id="d77f7-151">집계 변환에는 변환 성능을 향상시키기 위해 설정할 수 있는 일련의 속성이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="d77f7-151">The Aggregate transformation includes a set of properties that you can set to enhance the performance of the transformation.</span></span>  
  
-   <span data-ttu-id="d77f7-152">**Group by** 연산을 수행할 때 구성 요소 및 구성 요소 출력의 Keys 또는 KeysScale 속성을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="d77f7-152">When performing a **Group by** operation, set the Keys or KeysScale properties of the component and the component outputs.</span></span> <span data-ttu-id="d77f7-153">Keys를 사용하면 변환에서 처리할 정확한 개수의 키를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d77f7-153">Using Keys, you can specify the exact number of keys the transformation is expected to handle.</span></span> <span data-ttu-id="d77f7-154">여기서 말하는 Keys는 **Group by** 연산의 결과로 반환될 그룹 수를 나타냅니다. KeysScale을 사용하면 대략적인 개수의 키를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d77f7-154">(In this context, Keys refers to the number of groups that are expected to result from a **Group by** operation.) Using KeysScale, you can specify an approximate number of keys.</span></span> <span data-ttu-id="d77f7-155">Keys 또는 KeyScale에 대한 적절한 값을 지정하는 경우 변환이 캐시하는 데이터에 대해 적합한 메모리를 할당할 수 있으므로 성능이 향상됩니다.</span><span class="sxs-lookup"><span data-stu-id="d77f7-155">When you specify an appropriate value for Keys or KeyScale, you improve performance because the tranformation is able to allocate adequate memory for the data that the transformation caches.</span></span>  
  
-   <span data-ttu-id="d77f7-156">**고유 카운트** 연산을 수행할 때 구성 요소의 CountDistinctKeys 또는 CountDistinctScale 속성을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="d77f7-156">When performing a **Distinct count** operation, set the CountDistinctKeys or CountDistinctScale properties of the component.</span></span> <span data-ttu-id="d77f7-157">CountDistinctKeys를 사용하면 변환에서 Count distinct 연산에 대해 처리할 정확한 개수의 키를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d77f7-157">Using CountDistinctKeys, you can specify the exact number of keys the transformation is expected to handle for a count distinct operation.</span></span> <span data-ttu-id="d77f7-158">여기서 말하는 CountDistinctKeys는 **고유 카운트** 연산의 결과로 반환될 고유 값 수를 나타냅니다. CountDistinctScale을 사용하면 Count distinct 연산에 대한 대략적인 개수의 키를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d77f7-158">(In this context, CountDistinctKeys refers to the number of distinct values that are expected to result from a **Distinct count** operation.) Using CountDistinctScale, you can specify an approximate number of keys for a count distinct operation.</span></span> <span data-ttu-id="d77f7-159">CountDistinctKeys 또는 CountDistinctScale에 대한 적절한 값을 지정하는 경우 변환이 해당 변환이 캐시하는 데이터에 대해 적합한 메모리를 할당할 수 있으므로 성능이 향상됩니다.</span><span class="sxs-lookup"><span data-stu-id="d77f7-159">When you specify an appropriate value for CountDistinctKeys or CountDistinctScale, you improve performance because the transformation is able to allocate adequate memory for the data that the transformation caches.</span></span>  
  
## <a name="aggregate-transformation-configuration"></a><span data-ttu-id="d77f7-160">집계 변환 구성</span><span class="sxs-lookup"><span data-stu-id="d77f7-160">Aggregate Transformation Configuration</span></span>  
 <span data-ttu-id="d77f7-161">집계 변환은 변환, 출력 및 열 수준에서 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="d77f7-161">You configure the Aggregate transformation at the transformation, output, and column levels.</span></span>  
  
-   <span data-ttu-id="d77f7-162">변환 수준에서는 다음 값을 지정하여 집계 변환을 성능에 맞게 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="d77f7-162">At the transformation level, you configure the Aggregate transformation for performance by specifying the following values:</span></span>  
  
    -   <span data-ttu-id="d77f7-163">**Group by** 연산의 결과로 반환될 그룹 수</span><span class="sxs-lookup"><span data-stu-id="d77f7-163">The number of groups that are expected to result from a **Group by** operation.</span></span>  
  
    -   <span data-ttu-id="d77f7-164">**Count distinct** 연산의 결과로 반환될 고유 값 수</span><span class="sxs-lookup"><span data-stu-id="d77f7-164">The number of distinct values that are expected to result from a **Count distinct** operation.</span></span>  
  
    -   <span data-ttu-id="d77f7-165">집계 중에 메모리를 확장할 수 있는 비율</span><span class="sxs-lookup"><span data-stu-id="d77f7-165">The percentage by which memory can be extended during the aggregation.</span></span>  
  
     <span data-ttu-id="d77f7-166">또한 제수 값이 0일 때 오류가 발생하는 대신 경고를 생성하도록 집계 변환을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d77f7-166">The Aggregate transformation can also be configured to generate a warning instead of failing when the value of a divisor is zero.</span></span>  
  
-   <span data-ttu-id="d77f7-167">출력 수준에서는 **Group by** 연산의 결과로 반환될 그룹 수를 지정하여 집계 변환을 성능에 맞게 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="d77f7-167">At the output level, you configure the Aggregate transformation for performance by specifying the number of groups that are expected to result from a **Group by** operation.</span></span> <span data-ttu-id="d77f7-168">집계 변환에는 여러 출력이 지원되며 각 출력은 서로 다르게 구성될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d77f7-168">The Aggregate transformation supports multiple outputs, and each can be configured differently.</span></span>  
  
-   <span data-ttu-id="d77f7-169">열 수준에서는 다음 값을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d77f7-169">At the column level, you specify the following values:</span></span>  
  
    -   <span data-ttu-id="d77f7-170">열에서 수행하는 집계</span><span class="sxs-lookup"><span data-stu-id="d77f7-170">The aggregation that the column performs.</span></span>  
  
    -   <span data-ttu-id="d77f7-171">집계의 비교 옵션</span><span class="sxs-lookup"><span data-stu-id="d77f7-171">The comparison options of the aggregation.</span></span>  
  
 <span data-ttu-id="d77f7-172">또한 다음 값을 지정하여 집계 변환을 성능에 맞게 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d77f7-172">You can also configure the Aggregate transformation for performance by specifying these values:</span></span>  
  
-   <span data-ttu-id="d77f7-173">열에서 **Group by** 연산의 결과로 반환될 그룹 수</span><span class="sxs-lookup"><span data-stu-id="d77f7-173">The number of groups that are expected to result from a **Group by** operation on the column.</span></span>  
  
-   <span data-ttu-id="d77f7-174">열에서 **Count distinct** 연산의 결과로 반환될 고유 값 수</span><span class="sxs-lookup"><span data-stu-id="d77f7-174">The number of distinct values that are expected to result from a **Count distinct** operation on the column.</span></span>  
  
 <span data-ttu-id="d77f7-175">또한 열에 큰 숫자 값이나 전체 자릿수가 높은 숫자 값이 있는 경우 열을 IsBig으로 식별할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d77f7-175">You can also identify columns as IsBig if a column contains large numeric values or numeric values with high precision.</span></span>  
  
 <span data-ttu-id="d77f7-176">집계 변환은 비동기적이며 따라서 행별로 데이터를 사용하고 게시하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d77f7-176">The Aggregate transformation is asynchronous, which means that it does not consume and publish data row by row.</span></span> <span data-ttu-id="d77f7-177">대신 전체 행 집합을 사용하고 그룹화 및 집계를 수행한 다음 결과를 게시합니다.</span><span class="sxs-lookup"><span data-stu-id="d77f7-177">Instead it consumes the whole rowset, performs its groupings and aggregations, and then publishes the results.</span></span>  
  
 <span data-ttu-id="d77f7-178">이 변환은 어떤 열을 통해서도 전달되지 않지만 게시하는 데이터에 대한 데이터 흐름에 새 열을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d77f7-178">This transformation does not pass through any columns, but creates new columns in the data flow for the data it publishes.</span></span> <span data-ttu-id="d77f7-179">집계 함수가 적용하는 입력 열이나 변환에서 그룹화를 위해 사용되는 입력 열만 변환 출력으로 복사됩니다.</span><span class="sxs-lookup"><span data-stu-id="d77f7-179">Only the input columns to which aggregate functions apply or the input columns the transformation uses for grouping are copied to the transformation output.</span></span> <span data-ttu-id="d77f7-180">예를 들어 집계 변환 입력에는 **CountryRegion**, **City**및 **Population**과 같은 3개의 열만 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d77f7-180">For example, an Aggregate transformation input might have three columns: **CountryRegion**, **City**, and **Population**.</span></span> <span data-ttu-id="d77f7-181">변환은 **CountryRegion** 열에 따라 그룹화되며 Sum 함수를 **Population** 열에 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="d77f7-181">The transformation groups by the **CountryRegion** column and applies the Sum function to the **Population** column.</span></span> <span data-ttu-id="d77f7-182">따라서 출력에는 **City** 열이 포함되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d77f7-182">Therefore the output does not include the **City** column.</span></span>  
  
 <span data-ttu-id="d77f7-183">또한 집계 변환에 여러 출력을 추가하고 각 집계를 서로 다른 출력으로 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d77f7-183">You can also add multiple outputs to the Aggregate transformation and direct each aggregation to a different output.</span></span> <span data-ttu-id="d77f7-184">예를 들어 집계 변환이 Sum 및 the Average 함수를 적용하는 경우 각 집계는 서로 다른 출력으로 지정될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d77f7-184">For example, if the Aggregate transformation applies the Sum and the Average functions, each aggregation can be directed to a different output.</span></span>  
  
 <span data-ttu-id="d77f7-185">단일 입력 열에 여러 집계를 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d77f7-185">You can apply multiple aggregations to a single input column.</span></span> <span data-ttu-id="d77f7-186">예를 들어 **Sales**라는 입력 열에 대한 합계 및 평균 값이 필요하면 Sum 및 Average 함수를 모두 **Sales** 열에 적용하도록 변환을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d77f7-186">For example, if you want the sum and average values for an input column named **Sales**, you can configure the transformation to apply both the Sum and Average functions to the **Sales** column.</span></span>  
  
 <span data-ttu-id="d77f7-187">집계 변환에는 하나의 입력과 하나 이상의 출력이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="d77f7-187">The Aggregate transformation has one input and one or more outputs.</span></span> <span data-ttu-id="d77f7-188">오류 출력은 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d77f7-188">It does not support an error output.</span></span>  
  
 <span data-ttu-id="d77f7-189">[!INCLUDE[ssIS](../../../includes/ssis-md.md)] 디자이너를 사용하거나 프로그래밍 방식으로 속성을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d77f7-189">You can set properties through [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="d77f7-190">**집계 변환 편집기** 대화 상자에서 설정할 수 있는 속성에 대한 자세한 내용을 보려면 다음 항목 중 하나를 클릭하십시오.</span><span class="sxs-lookup"><span data-stu-id="d77f7-190">For more information about the properties that you can set in the **Aggregate Transformation Editor** dialog box, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="d77f7-191">집계 변환 편집기&#40;집계 탭&#41;</span><span class="sxs-lookup"><span data-stu-id="d77f7-191">Aggregate Transformation Editor &#40;Aggregations Tab&#41;</span></span>](../../aggregate-transformation-editor-aggregations-tab.md)  
  
-   [<span data-ttu-id="d77f7-192">집계 변환 편집기&#40;고급 탭&#41;</span><span class="sxs-lookup"><span data-stu-id="d77f7-192">Aggregate Transformation Editor &#40;Advanced Tab&#41;</span></span>](../../aggregate-transformation-editor-advanced-tab.md)  
  
 <span data-ttu-id="d77f7-193">**고급 편집기** 대화 상자에는 프로그래밍 방식으로 설정할 수 있는 속성이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="d77f7-193">The **Advanced Editor** dialog box reflects the properties that can be set programmatically.</span></span> <span data-ttu-id="d77f7-194">**고급 편집기** 대화 상자를 사용하거나 프로그래밍 방식으로 설정할 수 있는 속성에 대한 자세한 내용을 보려면 다음 항목 중 하나를 클릭하세요.</span><span class="sxs-lookup"><span data-stu-id="d77f7-194">For more information about the properties that you can set in the **Advanced Editor** dialog box or programmatically, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="d77f7-195">Common Properties</span><span class="sxs-lookup"><span data-stu-id="d77f7-195">Common Properties</span></span>](../../common-properties.md)  
  
-   [<span data-ttu-id="d77f7-196">변환 사용자 지정 속성</span><span class="sxs-lookup"><span data-stu-id="d77f7-196">Transformation Custom Properties</span></span>](transformation-custom-properties.md)  
  
 <span data-ttu-id="d77f7-197">속성 설정 방법을 보려면 다음 항목 중 하나를 클릭하세요.</span><span class="sxs-lookup"><span data-stu-id="d77f7-197">For more information about how to set properties, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="d77f7-198">집계 변환을 사용하여 데이터 세트의 값 집계</span><span class="sxs-lookup"><span data-stu-id="d77f7-198">Aggregate Values in a Dataset by Using the Aggregate Transformation</span></span>](aggregate-values-in-a-dataset-by-using-the-aggregate-transformation.md)  
  
-   [<span data-ttu-id="d77f7-199">데이터 흐름 구성 요소의 속성 설정</span><span class="sxs-lookup"><span data-stu-id="d77f7-199">Set the Properties of a Data Flow Component</span></span>](../set-the-properties-of-a-data-flow-component.md)  
  
-   [<span data-ttu-id="d77f7-200">병합 및 병합 조인 변환을 위한 데이터 정렬</span><span class="sxs-lookup"><span data-stu-id="d77f7-200">Sort Data for the Merge and Merge Join Transformations</span></span>](sort-data-for-the-merge-and-merge-join-transformations.md)  
  
## <a name="related-tasks"></a><span data-ttu-id="d77f7-201">관련 작업</span><span class="sxs-lookup"><span data-stu-id="d77f7-201">Related Tasks</span></span>  
 [<span data-ttu-id="d77f7-202">집계 변환을 사용하여 데이터 세트의 값 집계</span><span class="sxs-lookup"><span data-stu-id="d77f7-202">Aggregate Values in a Dataset by Using the Aggregate Transformation</span></span>](aggregate-values-in-a-dataset-by-using-the-aggregate-transformation.md)  
  
## <a name="see-also"></a><span data-ttu-id="d77f7-203">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d77f7-203">See Also</span></span>  
 <span data-ttu-id="d77f7-204">[데이터 흐름](../data-flow.md) </span><span class="sxs-lookup"><span data-stu-id="d77f7-204">[Data Flow](../data-flow.md) </span></span>  
 [<span data-ttu-id="d77f7-205">Integration Services 변환</span><span class="sxs-lookup"><span data-stu-id="d77f7-205">Integration Services Transformations</span></span>](integration-services-transformations.md)  
  
  
