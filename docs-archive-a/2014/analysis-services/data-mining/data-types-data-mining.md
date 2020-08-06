---
title: 데이터 형식 (데이터 마이닝) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- data types [data mining]
- columns [data mining], data types
- data mining [Analysis Services], data types
ms.assetid: 4af5b7db-790b-459c-b2b4-00f0cf6b5ce4
author: minewiskan
ms.author: owend
ms.openlocfilehash: 9027ff3928f40d43f16bb31b52e0c1d52e072847
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661425"
---
# <a name="data-types-data-mining"></a><span data-ttu-id="7482d-102">데이터 형식(데이터 마이닝)</span><span class="sxs-lookup"><span data-stu-id="7482d-102">Data Types (Data Mining)</span></span>
  <span data-ttu-id="7482d-103">에서 마이닝 모델 또는 마이닝 구조를 만들 때는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 마이닝 구조의 각 열에 대 한 데이터 형식을 정의 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7482d-103">When you create a mining model or a mining structure in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], you must define the data types for each of the columns in the mining structure.</span></span> <span data-ttu-id="7482d-104">데이터 형식은 데이터 마이닝 엔진에게 데이터 원본의 데이터가 숫자인지, 아니면 텍스트인지 여부와 데이터 처리 방법을 알려 줍니다.</span><span class="sxs-lookup"><span data-stu-id="7482d-104">The data type tells the data mining engine whether the data in the data source is numerical or text, and how the data should be processed.</span></span> <span data-ttu-id="7482d-105">예를 들어 원본 데이터에 숫자 데이터가 포함되어 있는 경우 숫자를 정수로 처리할지, 아니면 소수 자릿수를 사용하여 처리할지 여부를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7482d-105">For example, if your source data contains numerical data, you can specify whether the numbers be treated as integers or by using decimal places.</span></span>  
  
 <span data-ttu-id="7482d-106">각 데이터 형식은 하나 이상의 내용 유형을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="7482d-106">Each data type supports one or more content types.</span></span> <span data-ttu-id="7482d-107">내용 유형을 설정하여 마이닝 모델에서 열의 데이터를 처리하거나 계산하는 방법을 사용자 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7482d-107">By setting the content type, you can customize the way that data in the column is processed or calculated in the mining model.</span></span>  
  
 <span data-ttu-id="7482d-108">예를 들어 열에 숫자 데이터가 있는 경우 해당 데이터를 숫자 데이터 형식 또는 텍스트 데이터 형식으로 처리하도록 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7482d-108">For example, if you have numeric data in a column, you can choose to handle it either as a numeric or text data type.</span></span> <span data-ttu-id="7482d-109">숫자 데이터 형식을 선택하는 경우 여러 개의 서로 다른 내용 유형을 설정할 수 있습니다. 즉, 숫자를 분할하거나 숫자를 연속 값으로 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7482d-109">If you choose the numeric data type, you can set several different content types: you can discretize the numbers, or handle them as continuous values.</span></span> <span data-ttu-id="7482d-110">모든 콘텐츠 형식의 목록을 보려면 [콘텐츠 형식&#40;데이터 마이닝&#41;](content-types-data-mining.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7482d-110">For a list of all the content types, see [Content Types &#40;Data Mining&#41;](content-types-data-mining.md).</span></span>  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="7482d-111">에서는 마이닝 구조 열에 대해 다음과 같은 데이터 형식을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="7482d-111">supports the following data types for mining structure columns:</span></span>  
  
|<span data-ttu-id="7482d-112">데이터 형식</span><span class="sxs-lookup"><span data-stu-id="7482d-112">Data Type</span></span>|<span data-ttu-id="7482d-113">지원하는 내용 유형</span><span class="sxs-lookup"><span data-stu-id="7482d-113">Supported Content Types</span></span>|  
|---------------|-----------------------------|  
|`Text`|<span data-ttu-id="7482d-114">Cyclical, Discrete, Discretized, Key Sequence, Ordered, Sequence</span><span class="sxs-lookup"><span data-stu-id="7482d-114">Cyclical, Discrete, Discretized, Key Sequence, Ordered, Sequence</span></span>|  
|`Long`|<span data-ttu-id="7482d-115">Continuous, Cyclical, Discrete, Discretized, Key, Key Sequence, Key Time, Ordered, Sequence, Time</span><span class="sxs-lookup"><span data-stu-id="7482d-115">Continuous, Cyclical, Discrete, Discretized, Key, Key Sequence, Key Time, Ordered, Sequence, Time</span></span><br /><br /> <span data-ttu-id="7482d-116">Classified</span><span class="sxs-lookup"><span data-stu-id="7482d-116">Classified</span></span>|  
|`Boolean`|<span data-ttu-id="7482d-117">Cyclical, Discrete, Ordered</span><span class="sxs-lookup"><span data-stu-id="7482d-117">Cyclical, Discrete, Ordered</span></span>|  
|`Double`|<span data-ttu-id="7482d-118">Continuous, Cyclical, Discrete, Discretized, Key, Key Sequence, Key Time, Ordered, Sequence, Time</span><span class="sxs-lookup"><span data-stu-id="7482d-118">Continuous, Cyclical, Discrete, Discretized, Key, Key Sequence, Key Time, Ordered, Sequence, Time</span></span><br /><br /> <span data-ttu-id="7482d-119">Classified</span><span class="sxs-lookup"><span data-stu-id="7482d-119">Classified</span></span>|  
|`Date`|<span data-ttu-id="7482d-120">Continuous, Cyclical, Discrete, Discretized, Key, Key Sequence, Key Time, Ordered</span><span class="sxs-lookup"><span data-stu-id="7482d-120">Continuous, Cyclical, Discrete, Discretized, Key, Key Sequence, Key Time, Ordered</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="7482d-121">Time 및 Sequence 내용 유형은 타사 알고리즘에서만 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="7482d-121">The Time and Sequence content types are only supported by third-party algorithms.</span></span> <span data-ttu-id="7482d-122">Cyclical 및 Ordered 내용 유형이 지원되기는 하지만 대부분의 알고리즘은 해당 유형을 불연속 값으로 처리하고 특수한 처리를 수행하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7482d-122">The Cyclical and Ordered content types are supported, but most algorithms treat them as discrete values and do not perform special processing.</span></span>  
  
## <a name="specifying-a-data-type"></a><span data-ttu-id="7482d-123">데이터 형식 지정</span><span class="sxs-lookup"><span data-stu-id="7482d-123">Specifying a Data Type</span></span>  
 <span data-ttu-id="7482d-124">DMX(Data Mining Extensions)를 사용하여 직접 마이닝 모델을 만드는 경우 모델을 정의할 때 각 열에 대한 데이터 형식을 정의할 수 있으며 동시에 Analysis Services가 지정된 데이터 형식을 사용하여 해당되는 마이닝 구조를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="7482d-124">If you create the mining model directly by using Data Mining Extensions (DMX), you can define the data type for each column as you define the model, and Analysis Services will create the corresponding mining structure with the specified data types at the same time.</span></span> <span data-ttu-id="7482d-125">마법사를 사용하여 마이닝 모델 또는 마이닝 구조를 만드는 경우 Analysis Services에서 데이터 형식을 제안하거나 사용자가 목록에서 데이터 형식을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7482d-125">If you create the mining model or mining structure by using a wizard, Analysis Services will suggest a data type, or you can choose a data type from a list.</span></span>  
  
## <a name="changing-a-data-type"></a><span data-ttu-id="7482d-126">데이터 형식 변경</span><span class="sxs-lookup"><span data-stu-id="7482d-126">Changing a Data Type</span></span>  
 <span data-ttu-id="7482d-127">열의 데이터 형식을 변경하는 경우 항상 마이닝 구조 및 이 구조를 기반으로 하는 모든 마이닝 모델을 다시 처리해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7482d-127">If you change the data type of a column, you must always reprocess the mining structure and any mining models that are based on that structure.</span></span> <span data-ttu-id="7482d-128">데이터 형식을 변경하는 경우 특정 모델에서 해당 열을 더 이상 사용할 수 없는 경우가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7482d-128">Sometimes if you change the data type, that column can no longer be used in a particular model.</span></span> <span data-ttu-id="7482d-129">이 경우 Analysis Services에서는 사용자가 모델을 다시 처리할 때 오류를 발생시키거나 모델을 처리하지만 해당 특정 열을 제외합니다.</span><span class="sxs-lookup"><span data-stu-id="7482d-129">In that case, Analysis Services will either raise an error when you reprocess the model, or will process the model but leave out that particular column.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7482d-130">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7482d-130">See Also</span></span>  
 <span data-ttu-id="7482d-131">[데이터 마이닝&#41;&#40;내용 유형](content-types-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="7482d-131">[Content Types &#40;Data Mining&#41;](content-types-data-mining.md) </span></span>  
 <span data-ttu-id="7482d-132">[DMX&#41;콘텐츠 형식 &#40;](/sql/dmx/content-types-dmx) </span><span class="sxs-lookup"><span data-stu-id="7482d-132">[Content Types &#40;DMX&#41;](/sql/dmx/content-types-dmx) </span></span>  
 <span data-ttu-id="7482d-133">[데이터 마이닝 알고리즘 &#40;Analysis Services 데이터 마이닝&#41;](data-mining-algorithms-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="7482d-133">[Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;](data-mining-algorithms-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="7482d-134">[마이닝 구조 &#40;Analysis Services 데이터 마이닝&#41;](mining-structures-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="7482d-134">[Mining Structures &#40;Analysis Services - Data Mining&#41;](mining-structures-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="7482d-135">[DMX&#41;&#40;데이터 형식](/sql/dmx/data-types-dmx) </span><span class="sxs-lookup"><span data-stu-id="7482d-135">[Data Types &#40;DMX&#41;](/sql/dmx/data-types-dmx) </span></span>  
 <span data-ttu-id="7482d-136">[마이닝 모델 열](mining-model-columns.md) </span><span class="sxs-lookup"><span data-stu-id="7482d-136">[Mining Model Columns](mining-model-columns.md) </span></span>  
 [<span data-ttu-id="7482d-137">마이닝 구조 열</span><span class="sxs-lookup"><span data-stu-id="7482d-137">Mining Structure Columns</span></span>](mining-structure-columns.md)  
  
  
