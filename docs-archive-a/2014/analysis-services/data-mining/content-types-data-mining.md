---
title: 내용 유형 (데이터 마이닝) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- columns [data mining], content types
- KEY SEQUENCE column
- content types [data mining]
- attributes [data mining]
- DISCRETIZED column
- CONTINUOUS column
- CYCLICAL column
- ORDERED column
- discretized columns [data mining]
- discrete columns [Analysis Services]
- DISCRETE column
- KEY column
- KEY TIME column
- continuous columns
- coding [Data Mining]
ms.assetid: 2dacd968-70e8-4993-88b6-a6d36024a4e4
author: minewiskan
ms.author: owend
ms.openlocfilehash: 8e3400d904bc857bc282bb1ad9220c1e01fe5a4d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87727484"
---
# <a name="content-types-data-mining"></a><span data-ttu-id="a4560-102">내용 유형(데이터 마이닝)</span><span class="sxs-lookup"><span data-stu-id="a4560-102">Content Types (Data Mining)</span></span>
  <span data-ttu-id="a4560-103">에서는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 마이닝 구조의 열에 대 한 실제 데이터 형식과 모델에 사용 될 때 열에 대 한 논리적 내용 유형을 모두 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a4560-103">In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], you can define the both the physical data type for a column in a mining structure, and a logical content type for the column when used in a model,</span></span>  
  
 <span data-ttu-id="a4560-104">*데이터 형식* 은 마이닝 모델을 만들 때 알고리즘이 이 열의 데이터를 처리하는 방법을 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="a4560-104">The *data type* determines how algorithms process the data in those columns when you create mining models.</span></span> <span data-ttu-id="a4560-105">열의 데이터 형식을 정의하면 열의 데이터 처리 방법 및 해당 데이터 형식에 대한 알고리즘 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="a4560-105">Defining the data type of a column gives the algorithm information about the type of data in the columns, and how to process the data.</span></span> <span data-ttu-id="a4560-106">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 의 각 데이터 형식은 데이터 마이닝에 대해 하나 이상의 내용 유형을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="a4560-106">Each data type in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] supports one or more content types for data mining.</span></span>  
  
 <span data-ttu-id="a4560-107">*내용 유형* 은 열에 포함된 내용의 동작을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="a4560-107">The *content type* describes the behavior of the content that the column contains.</span></span> <span data-ttu-id="a4560-108">예를 들어 열 내용이 요일 등의 특정 간격으로 반복되는 경우 해당 열의 내용 유형을 순환으로 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a4560-108">For example, if the content in a column repeats in a specific interval, such as days of the week, you can specify the content type of that column as cyclical.</span></span>  
  
 <span data-ttu-id="a4560-109">일부 알고리즘의 경우 올바르게 실행되기 위해서는 특정한 데이터 형식과 특정한 내용 유형이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="a4560-109">Some algorithms require specific data types and specific content types to be able to function correctly.</span></span> <span data-ttu-id="a4560-110">예를 들어 Microsoft Naive Bayes 알고리즘은 연속 열을 입력으로 사용할 수 없고 연속 값을 예측할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a4560-110">For example, the Microsoft Naive Bayes algorithm cannot use continuous columns as input, and cannot predict continuous values.</span></span> <span data-ttu-id="a4560-111">Key Sequence와 같은 일부 내용 유형은 특정 알고리즘에서만 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="a4560-111">Some content types, such as Key Sequence, are used only by a specific algorithm.</span></span> <span data-ttu-id="a4560-112">알고리즘과 각 알고리즘이 지원하는 콘텐츠 형식 목록은 [데이터 마이닝 알고리즘&#40;Analysis Services - 데이터 마이닝&#41;](data-mining-algorithms-analysis-services-data-mining.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a4560-112">For a list of the algorithms and the content types that each supports, see [Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;](data-mining-algorithms-analysis-services-data-mining.md).</span></span>  
  
 <span data-ttu-id="a4560-113">다음 목록에서는 데이터 마이닝에 사용되는 내용 유형을 설명하고 각 유형을 지원하는 데이터 형식을 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="a4560-113">The following list describes the content types that are used in data mining, and identifies the data types that support each type.</span></span>  
  
## <a name="discrete"></a><span data-ttu-id="a4560-114">불연속</span><span class="sxs-lookup"><span data-stu-id="a4560-114">Discrete</span></span>  
 <span data-ttu-id="a4560-115">*Discrete* 는 열에 연속되지 않은 한정된 수의 값이 포함되어 있음을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="a4560-115">*Discrete* means that the column contains a finite number of values with no continuum between values.</span></span> <span data-ttu-id="a4560-116">예를 들어 Gender 열은 전형적인 불연속 특성 열로서 해당 데이터가 특정 개수의 범주를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="a4560-116">For example, a gender column is a typical discrete attribute column, in that the data represents a specific number of categories.</span></span>  
  
 <span data-ttu-id="a4560-117">불연속 특성 열의 값은 숫자라 하더라도 순서를 의미하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a4560-117">The values in a discrete attribute column cannot imply ordering, even if the values are numeric.</span></span> <span data-ttu-id="a4560-118">또한 불연속 열에 사용된 값이 숫자라 하더라도 소수 값은 계산될 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a4560-118">Moreover, even if the values used for the discrete column are numeric, fractional values cannot be calculated.</span></span> <span data-ttu-id="a4560-119">불연속 숫자 데이터의 좋은 예로 전화 번호의 지역 번호가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a4560-119">Telephone area codes are a good example of discrete data that is numeric.</span></span>  
  
 <span data-ttu-id="a4560-120">`Discrete` 내용 유형은 모든 데이터 마이닝 데이터 형식에서 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="a4560-120">The `Discrete` content type is supported by all data mining data types.</span></span>  
  
## <a name="continuous"></a><span data-ttu-id="a4560-121">계속</span><span class="sxs-lookup"><span data-stu-id="a4560-121">Continuous</span></span>  
 <span data-ttu-id="a4560-122">*Continuous* 는 열에 중간 값을 허용하는 소수 자릿수의 숫자 데이터를 나타내는 값이 포함되어 있음을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="a4560-122">*Continuous* means that the column contains values that represent numeric data on a scale that allows interim values.</span></span> <span data-ttu-id="a4560-123">한정된 개수의 데이터를 나타내는 불연속 열과는 달리 연속 열은 조정 가능한 측정을 나타내며 데이터가 무한 개의 소수 값을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="a4560-123">Unlike a discrete column, which represents finite, countable data, a continuous column represents scalable measurements, and it is possible for the data to contain an infinite number of fractional values.</span></span> <span data-ttu-id="a4560-124">연속 특성 열의 예로는 Temperatures 열이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a4560-124">A column of temperatures is an example of a continuous attribute column.</span></span>  
  
 <span data-ttu-id="a4560-125">열에 연속 숫자 데이터가 있고 데이터 배포 방법을 알고 있는 경우 값의 예상 분포를 지정하여 분석의 정확도를 향상시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a4560-125">When a column contains continuous numeric data, and you know how the data should be distributed, you can potentially improve the accuracy of the analysis by specifying the expected distribution of values.</span></span> <span data-ttu-id="a4560-126">마이닝 구조의 수준에서 열 배포를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a4560-126">You specify the column distribution at the level of the mining structure.</span></span> <span data-ttu-id="a4560-127">따라서 이 설정은 구조를 기반으로 하는 모든 모델에 적용됩니다. 자세한 내용은 [열 배포&#40;데이터 마이닝&#41;](column-distributions-data-mining.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a4560-127">Therefore, the setting applies to all models that are based on the structure, For more information, see [Column Distributions &#40;Data Mining&#41;](column-distributions-data-mining.md).</span></span>  
  
 <span data-ttu-id="a4560-128">`Continuous` 내용 유형은 `Date`, `Double` 및 `Long` 데이터 형식에서 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="a4560-128">The `Continuous` content type is supported by the following data types: `Date`, `Double`, and `Long`.</span></span>  
  
## <a name="discretized"></a><span data-ttu-id="a4560-129">불연속화됨</span><span class="sxs-lookup"><span data-stu-id="a4560-129">Discretized</span></span>  
 <span data-ttu-id="a4560-130">*분할* 은 제한된 개수의 가능한 값이 있도록 연속 데이터 집합의 값을 버킷에 넣는 프로세스입니다.</span><span class="sxs-lookup"><span data-stu-id="a4560-130">*Discretization* is the process of putting values of a continuous set of data into buckets so that there are a limited number of possible values.</span></span> <span data-ttu-id="a4560-131">숫자 데이터만 분할할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a4560-131">You can discretize only numeric data.</span></span>  
  
 <span data-ttu-id="a4560-132">따라서 *Discretized* 내용 유형은 열에 연속 열에서 파생된 값의 그룹 또는 버킷을 나타내는 값이 포함되어 있음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="a4560-132">Thus, the *discretized* content type indicates that the column contains values that represent groups, or buckets, of values that are derived from a continuous column.</span></span> <span data-ttu-id="a4560-133">버킷은 정렬된 불연속 값으로 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="a4560-133">The buckets are treated as ordered and discrete values.</span></span>  
  
 <span data-ttu-id="a4560-134">원하는 버킷을 얻기 위해 데이터를 수동으로 분할하거나 SQL Server Analysis Services에서 제공하는 분할 메서드를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a4560-134">You can discretize your data manually, to ensure that you get the buckets you want, or you can use the discretization methods provided in SQL Server Analysis Services.</span></span> <span data-ttu-id="a4560-135">일부 알고리즘의 경우 분할을 자동으로 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="a4560-135">Some algorithms perform discretization automatically.</span></span> <span data-ttu-id="a4560-136">자세한 내용은 [마이닝 모델에서 열의 불연속화 변경](change-the-discretization-of-a-column-in-a-mining-model.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a4560-136">For more information, see [Change the Discretization of a Column in a Mining Model](change-the-discretization-of-a-column-in-a-mining-model.md).</span></span>  
  
 <span data-ttu-id="a4560-137">`Discretized` 내용 유형은 `Date`, `Double`, `Long` 및 `Text` 데이터 형식에서 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="a4560-137">The `Discretized` content type is supported by the following data types: `Date`, `Double`, `Long`, and `Text`.</span></span>  
  
## <a name="key"></a><span data-ttu-id="a4560-138">키</span><span class="sxs-lookup"><span data-stu-id="a4560-138">Key</span></span>  
 <span data-ttu-id="a4560-139">*Key* 내용 유형은 열이 행을 고유하게 식별함을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="a4560-139">The *key* content type means that the column uniquely identifies a row.</span></span> <span data-ttu-id="a4560-140">사례 테이블에서 키 열은 일반적으로 숫자 또는 텍스트 식별자입니다.</span><span class="sxs-lookup"><span data-stu-id="a4560-140">In a case table, typically the key column is a numeric or text identifier.</span></span> <span data-ttu-id="a4560-141">내용 유형을 `key`로 설정하면 열을 분석에 사용해서는 안 되고 레코드 추적용으로만 사용해야 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="a4560-141">You set the content type to `key` to indicate that the column should not be used for analysis, only for tracking records.</span></span>  
  
 <span data-ttu-id="a4560-142">중첩 테이블에도 키가 있지만 중첩 테이블 키의 사용법은 약간 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="a4560-142">Nested tables also have keys, but the usage of the nested table key is a little different.</span></span> <span data-ttu-id="a4560-143">열이 분석하려는 특성일 경우 중첩 테이블에서 내용 유형을 `key`로 설정하십시오.</span><span class="sxs-lookup"><span data-stu-id="a4560-143">You set the content type to `key` in a nested table if the column is the attribute that you want to analyze.</span></span> <span data-ttu-id="a4560-144">중첩 테이블 키의 값은 각 사례에 대해 고유해야 하지만 사례 집합 전체에서는 중복될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a4560-144">The values in the nested table key must be unique for each case but there can be duplicates across the entire set of cases.</span></span>  
  
 <span data-ttu-id="a4560-145">예를 들어 고객이 구매한 제품을 분석하는 경우 사례 테이블의 **CustomerID** 열에 대해 내용 유형을 Key로 설정한 다음 중첩 테이블의 **PurchasedProducts** 열에 대해 내용 유형을 다시 Key로 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a4560-145">For example, if you are analyzing the products that customers purchase, you would set content type to key for the **CustomerID** column in the case table, and set content type to key again for the **PurchasedProducts** column in the nested table.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a4560-146">중첩 테이블은 Analysis Services 데이터 원본 뷰로 정의된 외부 데이터 원본의 데이터를 사용하는 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a4560-146">Nested tables are available only if you use data from an external data source that has been defined as an Analysis services data source view.</span></span>  
  
 <span data-ttu-id="a4560-147">이 내용 유형은 `Date`, `Double`, `Long` 및 `Text` 데이터 형식에서 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="a4560-147">This content type is supported by the following data types: `Date`, `Double`, `Long`, and `Text`.</span></span>  
  
## <a name="key-sequence"></a><span data-ttu-id="a4560-148">키 시퀀스</span><span class="sxs-lookup"><span data-stu-id="a4560-148">Key Sequence</span></span>  
 <span data-ttu-id="a4560-149">*Key Sequence* 내용 유형은 시퀀스 클러스터링 모델에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a4560-149">The *key sequence* content type can only be used in sequence clustering models.</span></span> <span data-ttu-id="a4560-150">내용 유형을 `key sequence`로 설정할 경우 이는 이벤트 시퀀스를 표시하는 값이 열에 포함되어 있음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="a4560-150">When you set content type to `key sequence`, it indicates that the column contains values that represent a sequence of events.</span></span> <span data-ttu-id="a4560-151">이러한 값은 정렬되지만 간격은 달라도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a4560-151">The values are ordered, but do not have to be an equal distance apart.</span></span>  
  
 <span data-ttu-id="a4560-152">이 내용 유형은 `Double`, `Long`, `Text` 및 `Date` 데이터 형식에서 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="a4560-152">This content type is supported by the following data types: `Double`, `Long`, `Text`, and `Date`.</span></span>  
  
## <a name="key-time"></a><span data-ttu-id="a4560-153">Key Time</span><span class="sxs-lookup"><span data-stu-id="a4560-153">Key Time</span></span>  
 <span data-ttu-id="a4560-154">*Key Time* 내용 유형은 시계열 모델에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a4560-154">The *key time* content type can only be used in time series models.</span></span> <span data-ttu-id="a4560-155">내용 유형을 `key time`으로 설정할 경우 이는 값이 정렬되고 시간 단위를 가리킴을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="a4560-155">When you set content type to `key time`, it indicates that the values are ordered and represent a time scale.</span></span>  
  
 <span data-ttu-id="a4560-156">이 내용 유형은 `Double`, `Long` 및 `Date` 데이터 형식에서 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="a4560-156">This content type is supported by the following data types: `Double`, `Long`, and `Date`.</span></span>  
  
## <a name="table"></a><span data-ttu-id="a4560-157">표</span><span class="sxs-lookup"><span data-stu-id="a4560-157">Table</span></span>  
 <span data-ttu-id="a4560-158">*Table* 내용 유형은 열에 행과 열이 각각 한 개 이상인 다른 데이터 테이블이 포함되어 있음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="a4560-158">The *table* content type indicates that the column contains another data table, with one or more columns and one or more rows.</span></span> <span data-ttu-id="a4560-159">이 열은 사례 테이블의 특정 행에 대해 여러 값을 포함할 수 있는데 이러한 값은 모두 부모 사례 레코드와 관련되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a4560-159">For any particular row in the case table, this column can contain multiple values, all related to the parent case record.</span></span> <span data-ttu-id="a4560-160">예를 들어 주 사례 테이블에 고객 목록이 포함되어 있는 경우 중첩 테이블을 포함하는 열이 여러 개 있을 수 있습니다. 예를 들어 **ProductsPurchased** 열의 중첩 테이블에는 이 고객이 과거에 구매한 제품이 나열되며 **Hobbies** 열에는 고객의 관심 사항이 나열됩니다.</span><span class="sxs-lookup"><span data-stu-id="a4560-160">For example, if the main case table contains a listing of customers, you could have several columns that contain nested tables, such as a **ProductsPurchased** column, where the nested table lists products bought by this customer in the past, and a **Hobbies** column that lists the interests of the customer.</span></span>  
  
 <span data-ttu-id="a4560-161">이 열의 데이터 형식은 항상 `Table`입니다.</span><span class="sxs-lookup"><span data-stu-id="a4560-161">The data type of this column is always `Table`.</span></span>  
  
## <a name="cyclical"></a><span data-ttu-id="a4560-162">Cyclical</span><span class="sxs-lookup"><span data-stu-id="a4560-162">Cyclical</span></span>  
 <span data-ttu-id="a4560-163">*Cyclical* 내용 유형은 열에 정렬된 순환 집합을 나타내는 값이 포함되어 있음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="a4560-163">The *cyclical* content type means that the column contains values that represent a cyclical ordered set.</span></span> <span data-ttu-id="a4560-164">예를 들어 각 주의 번호가 매겨진 날짜들은 제7일 다음에 제1일이 오는 순환 정렬 집합입니다.</span><span class="sxs-lookup"><span data-stu-id="a4560-164">For example, the numbered days of the week is a cyclical ordered set, because day number one follows day number seven.</span></span>  
  
 <span data-ttu-id="a4560-165">순환 열은 내용 유형 면에서 정렬 및 불연속 등 두 가지 모두로 인식됩니다.</span><span class="sxs-lookup"><span data-stu-id="a4560-165">Cyclical columns are considered both ordered and discrete in terms of content type.</span></span>  
  
 <span data-ttu-id="a4560-166">이 내용 유형은 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]의 모든 데이터 마이닝 데이터 형식에서 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="a4560-166">This content type is supported by all the data mining data types in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="a4560-167">그러나 대부분의 알고리즘은 순환 값을 불연속 값으로 처리하며 특수한 처리를 수행하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a4560-167">However, most algorithms treat cyclical values as discrete values and do not perform special processing.</span></span>  
  
## <a name="ordered"></a><span data-ttu-id="a4560-168">주문됨</span><span class="sxs-lookup"><span data-stu-id="a4560-168">Ordered</span></span>  
 <span data-ttu-id="a4560-169">*Ordered* 내용 유형도 열에 시퀀스 또는 순서를 정의하는 값이 포함되어 있음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="a4560-169">The *Ordered* content type also indicates that the column contains values that define a sequence or order.</span></span> <span data-ttu-id="a4560-170">그러나 이 내용 유형에서는 정렬에 사용되는 값이 집합 내에 있는 값 간의 거리 또는 크기 관계를 의미하는 것은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="a4560-170">However, in this content type the values used for ordering do not imply any distance or magnitude relationship between values in the set.</span></span> <span data-ttu-id="a4560-171">예를 들어 정렬된 특성 열에 1부터 5까지 범위의 기술 수준에 대한 정보가 포함된 경우 기술 수준 간의 거리를 나타내는 정보는 포함되어 있지 않으므로 기술 수준 5가 기술 수준 1보다 반드시 5배 우수한 것은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="a4560-171">For example, if an ordered attribute column contains information about skill levels in rank order from one to five, there is no implied information in the distance between skill levels; a skill level of five is not necessarily five times better than a skill level of one.</span></span>  
  
 <span data-ttu-id="a4560-172">정렬된 특성 열은 내용 유형 면에서 불연속으로 인식됩니다.</span><span class="sxs-lookup"><span data-stu-id="a4560-172">Ordered attribute columns are considered to be discrete in terms of content type.</span></span>  
  
 <span data-ttu-id="a4560-173">이 내용 유형은 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]의 모든 데이터 마이닝 데이터 형식에서 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="a4560-173">This content type is supported by all the data mining data types in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="a4560-174">그러나 대부분의 알고리즘은 정렬된 값을 불연속 값으로 처리하며 특수한 처리를 수행하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a4560-174">However, however, most algorithms treat ordered values as discrete values and do not perform special processing.</span></span>  
  
## <a name="classified"></a><span data-ttu-id="a4560-175">Classified</span><span class="sxs-lookup"><span data-stu-id="a4560-175">Classified</span></span>  
 <span data-ttu-id="a4560-176">모든 모델에서 일반적으로 사용되는 위의 내용 유형 외에도 일부 데이터 형식에 대해 분류된 열을 사용하여 내용 유형을 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a4560-176">In addition to the preceding content types that are in common use with all models, for some data types you can use classified columns to define content types.</span></span> <span data-ttu-id="a4560-177">분류된 열에 대한 자세한 내용은 [분류된 열&#40;데이터 마이닝&#41;](classified-columns-data-mining.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a4560-177">For more information about classified columns, see [Classified Columns &#40;Data Mining&#41;](classified-columns-data-mining.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4560-178">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a4560-178">See Also</span></span>  
 <span data-ttu-id="a4560-179">[DMX&#41;콘텐츠 형식 &#40;](/sql/dmx/content-types-dmx) </span><span class="sxs-lookup"><span data-stu-id="a4560-179">[Content Types &#40;DMX&#41;](/sql/dmx/content-types-dmx) </span></span>  
 <span data-ttu-id="a4560-180">[데이터 마이닝 &#40;데이터 형식&#41;](data-types-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="a4560-180">[Data Types &#40;Data Mining&#41;](data-types-data-mining.md) </span></span>  
 <span data-ttu-id="a4560-181">[DMX&#41;&#40;데이터 형식](/sql/dmx/data-types-dmx) </span><span class="sxs-lookup"><span data-stu-id="a4560-181">[Data Types &#40;DMX&#41;](/sql/dmx/data-types-dmx) </span></span>  
 <span data-ttu-id="a4560-182">[마이닝 구조 속성 변경](change-the-properties-of-a-mining-structure.md) </span><span class="sxs-lookup"><span data-stu-id="a4560-182">[Change the Properties of a Mining Structure](change-the-properties-of-a-mining-structure.md) </span></span>  
 [<span data-ttu-id="a4560-183">마이닝 구조 열</span><span class="sxs-lookup"><span data-stu-id="a4560-183">Mining Structure Columns</span></span>](mining-structure-columns.md)  
  
  
