---
title: 마이닝 구조 열 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- data mining [Analysis Services], structure
- mining structures [Analysis Services], columns
- data sources [Analysis Services], mining structure columns
- columns [data mining], mining structure columns
ms.assetid: 20cbf433-70d1-4b61-a462-41a8435b27b4
author: minewiskan
ms.author: owend
ms.openlocfilehash: 0caebfaef9b80be2d8fb5586a061dcccd31981f3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653641"
---
# <a name="mining-structure-columns"></a><span data-ttu-id="b226c-102">마이닝 구조 열</span><span class="sxs-lookup"><span data-stu-id="b226c-102">Mining Structure Columns</span></span>
  <span data-ttu-id="b226c-103">마이닝 구조를 만들 때 외부 데이터 열을 선택한 다음 데이터가 모델링에 사용되는 방법을 지정하여 마이닝 구조의 열을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="b226c-103">You define the columns in a mining structure when you create the mining structure, by choosing columns of external data and then specifying how the data is to be used for modeling.</span></span> <span data-ttu-id="b226c-104">따라서 마이닝 구조 열이 데이터 원본의 데이터 복사본보다 많으며 마이닝 구조 열에 따라 원본 데이터가 마이닝 모델에 사용되는 방법이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="b226c-104">Therefore, mining structure columns are more than copies of data from a data source: they define how the data from the source is to be used by the mining model.</span></span> <span data-ttu-id="b226c-105">데이터를 분할하는 방법을 결정하는 속성과 데이터 값을 분산하는 방법을 설명하는 속성을 할당할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b226c-105">You can assign properties that determine how the data is discretized, properties that describe how the data values are distributed</span></span>  
  
 <span data-ttu-id="b226c-106">마이닝 모델 작성 시 사용하는 각 알고리즘이 구조의 여러 열을 사용하여 데이터를 해석할 수 있기 때문에 마이닝 구조 열은 유연성이 있고 확장 가능합니다.</span><span class="sxs-lookup"><span data-stu-id="b226c-106">Mining structure columns are designed to be flexible and extensible, because each algorithm that you use to build a mining model may use different columns from the structure to interpret the data.</span></span> <span data-ttu-id="b226c-107">각 모델에 대해 하나의 데이터 집합을 포함하는 대신 단일 마이닝 구조를 사용하고 해당 구조의 열을 사용하여 데이터를 각 모델에 맞게 사용자 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b226c-107">Rather than have one set of data for each model, you can use a single mining structure and use the columns in it to customize the data for each model.</span></span>  
  
## <a name="defining-mining-structure-columns"></a><span data-ttu-id="b226c-108">마이닝 구조 열 정의</span><span class="sxs-lookup"><span data-stu-id="b226c-108">Defining Mining Structure Columns</span></span>  
 <span data-ttu-id="b226c-109">구조 열을 정의하는 기본 데이터 형식과 내용 유형은 구조 생성 시 사용하는 데이터 원본에서 파생됩니다.</span><span class="sxs-lookup"><span data-stu-id="b226c-109">The basic data types and content types that define structure columns are derived from the data source that you use to create the structure.</span></span> <span data-ttu-id="b226c-110">마이닝 구조 내에서 이러한 설정을 변경할 수 있으며 연속 열에 대해 분포를 설정하고 모델링 플래그를 설정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b226c-110">You can change these settings within the mining structure, and you can also set modeling flags and set the distribution for continuous columns.</span></span>  
  
 <span data-ttu-id="b226c-111">마이닝 구조 열의 정의에는 다음 정보가 포함되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b226c-111">The definition of a mining structure column must contain the following information:</span></span>  
  
-   <span data-ttu-id="b226c-112">**ID**: 열의 고유 이름이며 이름과 동일한 경우가 많습니다.</span><span class="sxs-lookup"><span data-stu-id="b226c-112">**ID**: The unique name of the column, often the same as the name.</span></span> <span data-ttu-id="b226c-113">마이닝 구조를 만든 후 이름은 변경할 수 있지만 ID는 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b226c-113">This cannot be changed after you create the mining structure, whereas the name can be changed.</span></span>  
  
-   <span data-ttu-id="b226c-114">**이름**: 열의 이름 또는 별칭입니다.</span><span class="sxs-lookup"><span data-stu-id="b226c-114">**Name**: A name or alias for the column.</span></span>  
  
-   <span data-ttu-id="b226c-115">**콘텐츠**: 데이터가 불연속형인지 연속형인지 여부를 설명하는 열거형입니다.</span><span class="sxs-lookup"><span data-stu-id="b226c-115">**Content**: An enumeration that describes whether the data is discrete or continuous.</span></span>  
  
-   <span data-ttu-id="b226c-116">**형식**: 일반 데이터 형식을 나타내는 열거형입니다.</span><span class="sxs-lookup"><span data-stu-id="b226c-116">**Type**: An enumeration that indicates the general data type.</span></span>  
  
-   <span data-ttu-id="b226c-117">**분포**: 예상 분포 값을 설명하는 열거형입니다.</span><span class="sxs-lookup"><span data-stu-id="b226c-117">**Distribution**: An enumeration that describes the expected distribution of values.</span></span> <span data-ttu-id="b226c-118">열이 연속인 경우 분포가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="b226c-118">A distribution is included if the column is continuous.</span></span>  
  
-   <span data-ttu-id="b226c-119">**모델링 플래그**: 누락 값 등을 처리하는 방법을 나타내는 열거형입니다.</span><span class="sxs-lookup"><span data-stu-id="b226c-119">**Modeling flags**: An enumeration that indicates how to handle missing values and so forth.</span></span> <span data-ttu-id="b226c-120">마이닝 모델에 대해 모델링 플래그를 정의할 수도 있지만 모델 플래그는 구조 열에 사용되는 플래그와 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="b226c-120">Modeling flags can also be defined on the mining model, but the model flags are different than the flags used on structure columns.</span></span>  
  
-   <span data-ttu-id="b226c-121">**바인딩**: 원본 데이터를 지정하는 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="b226c-121">**Bindings**: Properties that specify the source data.</span></span>  
  
 <span data-ttu-id="b226c-122">타사 알고리즘은 마이닝 구조 열에 대해 정의할 수 있는 사용자 지정 속성을 포함할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b226c-122">Third-party algorithms may also include custom properties that can be defined on the mining structure column.</span></span>  
  
 <span data-ttu-id="b226c-123">데이터 마이닝 구조와 데이터 마이닝 모델에 대한 자세한 내용은 [마이닝 구조&#40;Analysis Services - 데이터 마이닝&#41;](mining-structures-analysis-services-data-mining.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b226c-123">For more information about the data mining structure and the data mining model, see [Mining Structures &#40;Analysis Services - Data Mining&#41;](mining-structures-analysis-services-data-mining.md).</span></span>  
  
## <a name="related-content"></a><span data-ttu-id="b226c-124">관련 내용</span><span class="sxs-lookup"><span data-stu-id="b226c-124">Related Content</span></span>  
 <span data-ttu-id="b226c-125">마이닝 구조 열을 정의하고 사용하는 방법은 다음 항목을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="b226c-125">See the following topics for more information about how to define and use mining structure columns.</span></span>  
  
|<span data-ttu-id="b226c-126">항목</span><span class="sxs-lookup"><span data-stu-id="b226c-126">Topic</span></span>|<span data-ttu-id="b226c-127">링크</span><span class="sxs-lookup"><span data-stu-id="b226c-127">Links</span></span>|  
|-----------|-----------|  
|<span data-ttu-id="b226c-128">마이닝 구조 열을 정의하는 데 사용할 수 있는 데이터 형식에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="b226c-128">Describes the data types that you can use to define a mining structure column.</span></span>|[<span data-ttu-id="b226c-129">데이터 형식&#40;데이터 마이닝&#41;</span><span class="sxs-lookup"><span data-stu-id="b226c-129">Data Types &#40;Data Mining&#41;</span></span>](data-types-data-mining.md)|  
|<span data-ttu-id="b226c-130">마이닝 구조 열에 포함되어 있는 각 데이터 형식에 사용할 수 있는 내용 유형에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="b226c-130">Describes the content types that are available for each type of data that is contained in a mining structure column.</span></span> <span data-ttu-id="b226c-131">내용 유형은 데이터 형식에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="b226c-131">Content types are dependent on data type.</span></span> <span data-ttu-id="b226c-132">내용 유형은 모델 수준에서 할당되며 모델에 열 데이터가 사용되는 방법을 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="b226c-132">The content type is assigned at the model level, and determines how the column data is used by the model.</span></span>|[<span data-ttu-id="b226c-133">콘텐츠 형식&#40;데이터 마이닝&#41;</span><span class="sxs-lookup"><span data-stu-id="b226c-133">Content Types &#40;Data Mining&#41;</span></span>](content-types-data-mining.md)|  
|<span data-ttu-id="b226c-134">중첩 테이블의 개념을 도입하고, 중첩 테이블을 데이터 원본에 마이닝 구조 열로 추가하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="b226c-134">Introduces the concept of nested tables, and explains how nested tables can be added to the data source as mining structure columns.</span></span>|[<span data-ttu-id="b226c-135">분류된 열&#40;데이터 마이닝&#41;</span><span class="sxs-lookup"><span data-stu-id="b226c-135">Classified Columns &#40;Data Mining&#41;</span></span>](classified-columns-data-mining.md)|  
|<span data-ttu-id="b226c-136">열의 예상 분포 값을 지정하기 위해 마이닝 구조 열에 대해 설정할 수 있는 분포 속성을 나열하고 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="b226c-136">Lists and explains the distribution properties that you can set on a mining structure column to specify the expected distribution of values in the column.</span></span>|[<span data-ttu-id="b226c-137">열 배포&#40;데이터 마이닝&#41;</span><span class="sxs-lookup"><span data-stu-id="b226c-137">Column Distributions &#40;Data Mining&#41;</span></span>](column-distributions-data-mining.md)|  
|<span data-ttu-id="b226c-138">*범주화*라고도 하는 불연속화의 개념을 설명하고 Analysis Services에서 연속 숫자 데이터 불연속화를 위해 제공하는 메서드에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="b226c-138">Explains the concept of discretization (sometimes referred to as *binning*) and describes the methods that Analysis Services provides for discretizing continuous numeric data.</span></span>|[<span data-ttu-id="b226c-139">분할 메서드&#40;데이터 마이닝&#41;</span><span class="sxs-lookup"><span data-stu-id="b226c-139">Discretization Methods &#40;Data Mining&#41;</span></span>](discretization-methods-data-mining.md)|  
|<span data-ttu-id="b226c-140">마이닝 구조 열에 대해 설정할 수 있는 모델링 플래그에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="b226c-140">Describes the modeling flags that you can set on a mining structure column.</span></span>|[<span data-ttu-id="b226c-141">모델링 플래그&#40;데이터 마이닝&#41;</span><span class="sxs-lookup"><span data-stu-id="b226c-141">Modeling Flags &#40;Data Mining&#41;</span></span>](modeling-flags-data-mining.md)|  
|<span data-ttu-id="b226c-142">한 마이닝 구조 열을 다른 마이닝 구조 열과 연결하는 데 사용할 수 있는 특수한 유형의 열인 분류된 열에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="b226c-142">Describes classified columns, which are a special type of column that you can use to relate one mining structure column to another.</span></span>|[<span data-ttu-id="b226c-143">분류된 열&#40;데이터 마이닝&#41;</span><span class="sxs-lookup"><span data-stu-id="b226c-143">Classified Columns &#40;Data Mining&#41;</span></span>](classified-columns-data-mining.md)|  
|<span data-ttu-id="b226c-144">마이닝 구조 열을 추가하고 수정하는 방법에 대해 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="b226c-144">Learn to add and modify mining structure columns.</span></span>|[<span data-ttu-id="b226c-145">마이닝 구조 태스크 및 방법</span><span class="sxs-lookup"><span data-stu-id="b226c-145">Mining Structure Tasks and How-tos</span></span>](mining-structure-tasks-and-how-tos.md)|  
  
## <a name="see-also"></a><span data-ttu-id="b226c-146">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b226c-146">See Also</span></span>  
 <span data-ttu-id="b226c-147">[마이닝 구조 &#40;Analysis Services 데이터 마이닝&#41;](mining-structures-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="b226c-147">[Mining Structures &#40;Analysis Services - Data Mining&#41;](mining-structures-analysis-services-data-mining.md) </span></span>  
 [<span data-ttu-id="b226c-148">마이닝 모델 열</span><span class="sxs-lookup"><span data-stu-id="b226c-148">Mining Model Columns</span></span>](mining-model-columns.md)  
  
  
