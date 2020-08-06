---
title: 열 내용 및 데이터 형식 지정 (데이터 마이닝 마법사) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 0634be64-4c38-4381-9b19-fe9a5889306c
author: minewiskan
ms.author: owend
ms.openlocfilehash: e22f46808877391376f721bcab55ea4fd9074186
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649716"
---
# <a name="specify-column-content-and-data-type-data-mining-wizard"></a><span data-ttu-id="47452-102">열 내용 및 데이터 형식 지정(데이터 마이닝 마법사)</span><span class="sxs-lookup"><span data-stu-id="47452-102">Specify Column Content and Data Type (Data Mining Wizard)</span></span>
  <span data-ttu-id="47452-103">**열 내용 및 데이터 형식 지정** 페이지를 사용하여 마법사의 이전 페이지에서 선택한 각 열의 사용법 및 데이터 형식을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="47452-103">Use the **Specify Column Content and Data Type** page to specify the usage and data type for each column that you selected on the previous page of the wizard.</span></span> <span data-ttu-id="47452-104">열을 무시하려면 **뒤로** 를 클릭하여 **학습 데이터 지정**페이지로 돌아간 다음 모든 확인란의 선택을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="47452-104">If you want to ignore the column, click **Back** to return to the page **Specify the Training Data**, and clear all checkboxes.</span></span>  
  
 <span data-ttu-id="47452-105">열 사용법은 모델에서 데이터가 사용되는 방법을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="47452-105">The usage of a column indicates how the data will be used in the model.</span></span> <span data-ttu-id="47452-106">열은 계열을 식별하는 키, 분석에서 사용할 입력 값 또는 예측할 값으로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="47452-106">A column can be used as a key to identify a series, as an input value to use in analysis, or as the value that you want to predict.</span></span> <span data-ttu-id="47452-107">열은 예측 및 입력에 모두 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="47452-107">Columns can be used for both prediction and input.</span></span>  
  
 <span data-ttu-id="47452-108">데이터 형식은 열에 포함되는 데이터 형식에 대한 추가 정보 및 학습 중에 데이터가 사용되는 방법을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="47452-108">The data type specifies additional detail about the type of data that is contained in the column, and how the data will be used during training.</span></span> <span data-ttu-id="47452-109">일부 내용 유형에는 특정 데이터 형식이 필요하고 특정 데이터 형식에는 일부 내용 유형이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="47452-109">Some content types require a specific data type, and vice versa.</span></span> <span data-ttu-id="47452-110">마이닝 모델을 만들 때 사용하는 알고리즘에 따라 특정 데이터 형식을 지정해야 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="47452-110">You might also need to specify a particular data type depending on the algorithm that you use when you create a mining model.</span></span> <span data-ttu-id="47452-111">마이닝 모델과 구조의 콘텐츠 형식 및 데이터 형식에 대한 자세한 내용은 [콘텐츠 형식&#40;데이터 마이닝&#41;](data-mining/content-types-data-mining.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="47452-111">For information about content types and data types in mining models and structures, see [Content Types &#40;Data Mining&#41;](data-mining/content-types-data-mining.md).</span></span>  
  
 <span data-ttu-id="47452-112">**자세한 내용:** [마이닝 구조&#40;Analysis Services - 데이터 마이닝&#41;](data-mining/mining-structures-analysis-services-data-mining.md), [마이닝 모델 열](data-mining/mining-model-columns.md), [데이터 마이닝 마법사&#40;Analysis Services - 데이터 마이닝&#41;](data-mining/data-mining-wizard-analysis-services-data-mining.md), [관계형 마이닝 구조 만들기](data-mining/create-a-relational-mining-structure.md)</span><span class="sxs-lookup"><span data-stu-id="47452-112">**For More Information:** [Mining Structures &#40;Analysis Services - Data Mining&#41;](data-mining/mining-structures-analysis-services-data-mining.md), [Mining Model Columns](data-mining/mining-model-columns.md), [Data Mining Wizard &#40;Analysis Services - Data Mining&#41;](data-mining/data-mining-wizard-analysis-services-data-mining.md), [Create a Relational Mining Structure](data-mining/create-a-relational-mining-structure.md)</span></span>  
  
## <a name="options"></a><span data-ttu-id="47452-113">옵션</span><span class="sxs-lookup"><span data-stu-id="47452-113">Options</span></span>  
 <span data-ttu-id="47452-114">**마이닝 모델 구조**</span><span class="sxs-lookup"><span data-stu-id="47452-114">**Mining model structure**</span></span>  
 <span data-ttu-id="47452-115">마법사의 이전 페이지에서 선택한 뷰 및 중첩 테이블의 열을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="47452-115">Displays the columns from the views and nested tables that you selected on the previous page of the wizard.</span></span>  
  
 <span data-ttu-id="47452-116">**열**</span><span class="sxs-lookup"><span data-stu-id="47452-116">**Columns**</span></span>  
 <span data-ttu-id="47452-117">열을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="47452-117">Lists the columns.</span></span>  
  
 <span data-ttu-id="47452-118">**내용 유형**</span><span class="sxs-lookup"><span data-stu-id="47452-118">**Content type**</span></span>  
 <span data-ttu-id="47452-119">열에 대한 내용 유형을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="47452-119">Specify the content type for the column.</span></span> <span data-ttu-id="47452-120">마법사의 이전 페이지에서 열을 키로 지정한 경우 다음 값을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="47452-120">If you specified that the column is a key on the previous page of the wizard, the following values are available:</span></span>  
  
|<span data-ttu-id="47452-121">옵션</span><span class="sxs-lookup"><span data-stu-id="47452-121">Option</span></span>|<span data-ttu-id="47452-122">Description</span><span class="sxs-lookup"><span data-stu-id="47452-122">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="47452-123">키</span><span class="sxs-lookup"><span data-stu-id="47452-123">Key</span></span>|<span data-ttu-id="47452-124">열에 사례 계열에 대한 고유 식별자가 포함되도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="47452-124">Specify that the column contains a unique identifier for the case series.</span></span>|  
|<span data-ttu-id="47452-125">키 시퀀스</span><span class="sxs-lookup"><span data-stu-id="47452-125">Key Sequence</span></span>|<span data-ttu-id="47452-126">열에 시퀀스 식별자가 포함되도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="47452-126">Specify that the column contains a sequence identifier.</span></span>|  
|<span data-ttu-id="47452-127">Key Time</span><span class="sxs-lookup"><span data-stu-id="47452-127">Key Time</span></span>|<span data-ttu-id="47452-128">열에 데이터나 시계열을 식별하는 데 사용되는 데이터 또는 다른 고유 연속 숫자가 포함되도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="47452-128">Specify that the column contains a date or other unique continuous number that is used to identify a date or time series.</span></span>|  
  
 <span data-ttu-id="47452-129">열을 키가 아닌 열로 선택한 경우 데이터 형식에 따라 다음 값을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="47452-129">If you selected the column as a non-key column, the following values are available, depending on the data type:</span></span>  
  
|<span data-ttu-id="47452-130">옵션</span><span class="sxs-lookup"><span data-stu-id="47452-130">Option</span></span>|<span data-ttu-id="47452-131">Description</span><span class="sxs-lookup"><span data-stu-id="47452-131">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="47452-132">계속</span><span class="sxs-lookup"><span data-stu-id="47452-132">Continuous</span></span>|<span data-ttu-id="47452-133">열에 연속 숫자 값이 포함되도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="47452-133">Specify that the column contains continuous numeric values.</span></span>|  
|<span data-ttu-id="47452-134">불연속화됨</span><span class="sxs-lookup"><span data-stu-id="47452-134">Discretized</span></span>|<span data-ttu-id="47452-135">열에 불연속화되거나 불연속 값으로 처리할 수 있는 숫자 값이 포함되도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="47452-135">Specify that the column contains numeric values that either have been discretized, or can be treated as discrete values.</span></span>|  
|<span data-ttu-id="47452-136">불연속</span><span class="sxs-lookup"><span data-stu-id="47452-136">Discrete</span></span>|<span data-ttu-id="47452-137">열에 텍스트 또는 숫자가 아닌 다른 값이 포함되도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="47452-137">Specify that the column contains text or other nonnumeric values.</span></span>|  
  
 <span data-ttu-id="47452-138">**데이터 형식**</span><span class="sxs-lookup"><span data-stu-id="47452-138">**Data type**</span></span>  
 <span data-ttu-id="47452-139">열에 대한 데이터 형식을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="47452-139">Specify the data type for the column.</span></span>  
  
 <span data-ttu-id="47452-140">사용할 수 있는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="47452-140">The following values are available:</span></span>  
  
-   `Boolean`  
  
-   `Date`  
  
-   `Double`  
  
-   `Long`  
  
-   `Text`  
  
 <span data-ttu-id="47452-141">**검색**</span><span class="sxs-lookup"><span data-stu-id="47452-141">**Detect**</span></span>  
 <span data-ttu-id="47452-142">모든 숫자 열에 있는 데이터 예제를 분석합니다.</span><span class="sxs-lookup"><span data-stu-id="47452-142">Analyze a sample of data in all numeric columns.</span></span> <span data-ttu-id="47452-143">지정된 **내용 유형** 값을 권장 내용 유형으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="47452-143">Replaces specified **Content Type** values with a recommended content type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47452-144">참고 항목</span><span class="sxs-lookup"><span data-stu-id="47452-144">See Also</span></span>  
 <span data-ttu-id="47452-145">[데이터 마이닝 마법사 F1 도움말 &#40;Analysis Services 데이터 마이닝&#41;](data-mining-wizard-f1-help-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="47452-145">[Data Mining Wizard F1 Help &#40;Analysis Services - Data Mining&#41;](data-mining-wizard-f1-help-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="47452-146">[데이터 마이닝 마법사 &#40;관련 열 제안&#41;](suggest-related-columns-data-mining-wizard.md) </span><span class="sxs-lookup"><span data-stu-id="47452-146">[Suggest Related Columns &#40;Data Mining Wizard&#41;](suggest-related-columns-data-mining-wizard.md) </span></span>  
 <span data-ttu-id="47452-147">[데이터 마이닝 마법사 &#40;테이블 형식을 지정&#41;](specify-table-types-data-mining-wizard.md) </span><span class="sxs-lookup"><span data-stu-id="47452-147">[Specify Table Types &#40;Data Mining Wizard&#41;](specify-table-types-data-mining-wizard.md) </span></span>  
 [<span data-ttu-id="47452-148">열 내용 및 데이터 형식 &#40;데이터 마이닝 마법사를 지정&#41;</span><span class="sxs-lookup"><span data-stu-id="47452-148">Specify the Column's Content and Data Type &#40;Data Mining Wizard&#41;</span></span>](specify-the-column-s-content-and-data-type-data-mining-wizard.md)  
  
  
