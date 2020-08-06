---
title: 마이닝 모델 속성 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining models [Analysis Services], properties
- data mining [Analysis Services], properties
- columns [data mining], properties
- Data Mining Designer
- properties [data mining]
ms.assetid: c5194619-8b31-42be-a95f-585711462945
author: minewiskan
ms.author: owend
ms.openlocfilehash: fb086f4a978ca96de8e6fc99f889f718247629af
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653651"
---
# <a name="mining-model-properties"></a><span data-ttu-id="3becf-102">마이닝 모델 속성</span><span class="sxs-lookup"><span data-stu-id="3becf-102">Mining Model Properties</span></span>
  <span data-ttu-id="3becf-103">마이닝 모델의 속성은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="3becf-103">Mining models have the following kinds of properties:</span></span>  
  
-   <span data-ttu-id="3becf-104">마이닝 구조에서 상속되며, 모델에서 사용하는 데이터의 데이터 형식 및 내용 유형을 정의하는 속성</span><span class="sxs-lookup"><span data-stu-id="3becf-104">Properties that are inherited from the mining structure that define the data type and content type of the data used by the model;</span></span>  
  
-   <span data-ttu-id="3becf-105">마이닝 모델을 만드는 데 사용된 알고리즘과 관련된 속성(사용자 지정 매개 변수 포함)</span><span class="sxs-lookup"><span data-stu-id="3becf-105">Properties that are related to the algorithm used to create the mining model, including any customer parameters;</span></span>  
  
-   <span data-ttu-id="3becf-106">모델을 학습하는 데 사용된 모델의 필터를 정의하는 속성</span><span class="sxs-lookup"><span data-stu-id="3becf-106">Properties that define a filter on the model used to train the model.</span></span>  
  
 <span data-ttu-id="3becf-107">마이닝 모델의 속성은 모델을 만들 때 초기에 정의됩니다. 그러나 알고리즘 매개 변수, 필터 및 열 사용법 속성을 포함하여 대부분의 속성을 나중에 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3becf-107">The properties of a mining model are initially defined when you create the model; however, you can alter most properties later, including the algorithm parameters, filters, and column usage properties.</span></span> <span data-ttu-id="3becf-108">데이터 마이닝 디자이너의 **마이닝 모델** 탭을 사용하거나 AMO 또는 XMLA를 사용하여 속성을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3becf-108">You change properties by using the **Mining Models** tab of Data Mining Designer, or by using AMO or XMLA.</span></span>  
  
 <span data-ttu-id="3becf-109">모델의 속성을 변경할 때마다 모델을 다시 처리해야 변경 내용이 모델에 반영됩니다.</span><span class="sxs-lookup"><span data-stu-id="3becf-109">Whenever you change any property of a model, you must reprocess the model for the changes to be reflected in the model.</span></span> <span data-ttu-id="3becf-110">열 별칭 또는 설명 추가와 같이 메타데이터만 변경한 경우에도 다시 처리해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3becf-110">Reprocessing is required even if the change only involves metadata, such as adding a column alias or description.</span></span>  
  
## <a name="properties-of-models"></a><span data-ttu-id="3becf-111">모델의 속성</span><span class="sxs-lookup"><span data-stu-id="3becf-111">Properties of Models</span></span>  
 <span data-ttu-id="3becf-112">다음 표에서는 마이닝 모델에 특정한 속성에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="3becf-112">The following table describes the properties that are specific to mining models.</span></span> <span data-ttu-id="3becf-113">또한 마이닝 시 개별 열에 대해 설정할 수 있는 속성도 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3becf-113">Additionally, there are properties that you can set on individual columns in the mining</span></span>  
  
|<span data-ttu-id="3becf-114">속성</span><span class="sxs-lookup"><span data-stu-id="3becf-114">Property</span></span>|<span data-ttu-id="3becf-115">Description</span><span class="sxs-lookup"><span data-stu-id="3becf-115">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="3becf-116">**알고리즘**</span><span class="sxs-lookup"><span data-stu-id="3becf-116">**Algorithm**</span></span>|<span data-ttu-id="3becf-117">마이닝 모델에 대한 알고리즘 유형을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="3becf-117">Sets the algorithm type for the mining model.</span></span>|  
|<span data-ttu-id="3becf-118">**AlgorithmParameters**</span><span class="sxs-lookup"><span data-stu-id="3becf-118">**AlgorithmParameters**</span></span>|<span data-ttu-id="3becf-119">각 알고리즘 유형에 사용할 수 있는 알고리즘 매개 변수의 값을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="3becf-119">Sets values for algorithm parameters that are available for each algorithm type.</span></span>|  
|<span data-ttu-id="3becf-120">**Filter**</span><span class="sxs-lookup"><span data-stu-id="3becf-120">**Filter**</span></span>|<span data-ttu-id="3becf-121">마이닝 모델을 학습하고 테스트할 때 사용하는 데이터에 적용되는 필터를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="3becf-121">Sets a filter that is applied to the data that is used for training and testing the mining model.</span></span> <span data-ttu-id="3becf-122">필터 정의는 모델에 저장되며 예측 쿼리를 만들거나 모델의 정확도를 테스트할 때 선택적으로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3becf-122">The filter definition is stored with the model and can be used optionally when you create prediction queries, or when you test the accuracy of the model.</span></span><br /><br /> <span data-ttu-id="3becf-123">모델을 학습할 경우 모델 필터는 선택 사항이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="3becf-123">The model filter is not optional when training the model.</span></span>|  
|<span data-ttu-id="3becf-124">**이름**</span><span class="sxs-lookup"><span data-stu-id="3becf-124">**Name**</span></span>|<span data-ttu-id="3becf-125">마이닝 모델의 이름을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="3becf-125">Sets the name of the mining model.</span></span>|  
|<span data-ttu-id="3becf-126">**AllowDrillThrough**</span><span class="sxs-lookup"><span data-stu-id="3becf-126">**AllowDrillThrough**</span></span>|<span data-ttu-id="3becf-127">드릴스루를 마이닝 모델에 설정할지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3becf-127">Specifies whether drill through is enabled on the mining model.</span></span>|  
  
## <a name="properties-of-model-columns"></a><span data-ttu-id="3becf-128">모델 열의 속성</span><span class="sxs-lookup"><span data-stu-id="3becf-128">Properties of Model Columns</span></span>  
 <span data-ttu-id="3becf-129">마이닝 모델의 각 열에 대해 다음 데이터 마이닝 속성을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3becf-129">You can set the following data mining-specific properties for each column in a mining model.</span></span> <span data-ttu-id="3becf-130">마이닝 구조의 각 마이닝 모델에 대해 이러한 속성을 서로 다른 값으로 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3becf-130">You can set these properties to a different value for each mining model in a mining structure.</span></span>  
  
|<span data-ttu-id="3becf-131">속성</span><span class="sxs-lookup"><span data-stu-id="3becf-131">Property</span></span>|<span data-ttu-id="3becf-132">Description</span><span class="sxs-lookup"><span data-stu-id="3becf-132">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="3becf-133">**설명**</span><span class="sxs-lookup"><span data-stu-id="3becf-133">**Description**</span></span>|<span data-ttu-id="3becf-134">마이닝 열의 목적을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="3becf-134">Describes the purpose of the mining column.</span></span>|  
|<span data-ttu-id="3becf-135">**이름**</span><span class="sxs-lookup"><span data-stu-id="3becf-135">**Name**</span></span>|<span data-ttu-id="3becf-136">마이닝 모델 열의 이름을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="3becf-136">Sets the name of the mining model column.</span></span> <span data-ttu-id="3becf-137">새 이름을 입력하여 마이닝 모델 열의 별칭을 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3becf-137">You can type a new name, to provide an alias for the mining model column.</span></span>|  
|<span data-ttu-id="3becf-138">**ModelingFlags**</span><span class="sxs-lookup"><span data-stu-id="3becf-138">**ModelingFlags**</span></span>|<span data-ttu-id="3becf-139">열에 대해 알고리즘별 플래그를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="3becf-139">Sets any algorithm-specific flags for the column.</span></span>|  
|<span data-ttu-id="3becf-140">**SourceColumnID**</span><span class="sxs-lookup"><span data-stu-id="3becf-140">**SourceColumnID**</span></span>|<span data-ttu-id="3becf-141">모델 열의 기반이 되는 마이닝 구조 열의 이름을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="3becf-141">Indicates the name of the mining structure column on which the model column is based.</span></span><br /><br /> <span data-ttu-id="3becf-142">이 속성은 읽기 전용입니다.</span><span class="sxs-lookup"><span data-stu-id="3becf-142">This property is read-only.</span></span>|  
|<span data-ttu-id="3becf-143">**사용 현황**</span><span class="sxs-lookup"><span data-stu-id="3becf-143">**Usage**</span></span>|<span data-ttu-id="3becf-144">마이닝 모델에서 열을 사용하는 방법을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="3becf-144">Sets how the column will be used by the mining model.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3becf-145">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3becf-145">See Also</span></span>  
 <span data-ttu-id="3becf-146">[마이닝 모델 열](mining-model-columns.md) </span><span class="sxs-lookup"><span data-stu-id="3becf-146">[Mining Model Columns](mining-model-columns.md) </span></span>  
 <span data-ttu-id="3becf-147">[마이닝 구조 &#40;Analysis Services 데이터 마이닝&#41;](mining-structures-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="3becf-147">[Mining Structures &#40;Analysis Services - Data Mining&#41;](mining-structures-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="3becf-148">[마이닝 모델 태스크 및 방법](mining-model-tasks-and-how-tos.md) </span><span class="sxs-lookup"><span data-stu-id="3becf-148">[Mining Model Tasks and How-tos](mining-model-tasks-and-how-tos.md) </span></span>  
 <span data-ttu-id="3becf-149">[마이닝 모델의 속성 변경](change-the-properties-of-a-mining-model.md) </span><span class="sxs-lookup"><span data-stu-id="3becf-149">[Change the Properties of a Mining Model](change-the-properties-of-a-mining-model.md) </span></span>  
 <span data-ttu-id="3becf-150">[데이터 마이닝 도구](data-mining-tools.md) </span><span class="sxs-lookup"><span data-stu-id="3becf-150">[Data Mining Tools](data-mining-tools.md) </span></span>  
 <span data-ttu-id="3becf-151">[관계형 마이닝 구조 만들기](create-a-relational-mining-structure.md) </span><span class="sxs-lookup"><span data-stu-id="3becf-151">[Create a Relational Mining Structure](create-a-relational-mining-structure.md) </span></span>  
 [<span data-ttu-id="3becf-152">모델 열의 별칭 만들기</span><span class="sxs-lookup"><span data-stu-id="3becf-152">Create an Alias for a Model Column</span></span>](create-an-alias-for-a-model-column.md)  
  
  
