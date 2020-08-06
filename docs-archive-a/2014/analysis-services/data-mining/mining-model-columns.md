---
title: 마이닝 모델 열 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- columns [data mining], mining model columns
- columns [data mining]
- REGRESSOR column
- columns [data mining], modeling flags
- modeling flags [data mining]
- MODEL_EXISTENCE_ONLY column
- usage property [data mining]
ms.assetid: fab47643-5bfd-424e-a0f7-69e665db6bab
author: minewiskan
ms.author: owend
ms.openlocfilehash: 6f936f3f4e0b8f65326e9a6e84f75e6f4e82657f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87732207"
---
# <a name="mining-model-columns"></a><span data-ttu-id="38f2e-102">마이닝 모델 열</span><span class="sxs-lookup"><span data-stu-id="38f2e-102">Mining Model Columns</span></span>
  <span data-ttu-id="38f2e-103">데이터 마이닝 모델은 마이닝 구조가 나타나는 데이터에 마이닝 모델 알고리즘을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="38f2e-103">A data mining model applies a mining model algorithm to the data that is represented by a mining structure.</span></span> <span data-ttu-id="38f2e-104">마이닝 구조와 마찬가지로 마이닝 모델에는 열이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="38f2e-104">Like the mining structure, the mining model contains columns.</span></span> <span data-ttu-id="38f2e-105">마이닝 모델은 마이닝 구조 내에 포함되며 마이닝 구조에서 정의한 속성의 모든 값을 상속받습니다.</span><span class="sxs-lookup"><span data-stu-id="38f2e-105">A mining model is contained within the mining structure, and inherits all the values of the properties that are defined by the mining structure.</span></span> <span data-ttu-id="38f2e-106">모델은 마이닝 구조에 포함된 모든 열이나 이 열의 하위 집합을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38f2e-106">The model can use all the columns that the mining structure contains or a subset of the columns.</span></span>  
  
 <span data-ttu-id="38f2e-107">마이닝 모델 열에는 사용법 및 모델링 플래그 정보를 추가로 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38f2e-107">You can define two additional pieces of information on a mining model column: usage, and modeling flags.</span></span>  
  
-   <span data-ttu-id="38f2e-108">**사용법** 은 모델이 열을 사용하는 방법을 정의하는 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="38f2e-108">**Usage** is a property that defines how the model uses the column.</span></span> <span data-ttu-id="38f2e-109">열은 입력 열, 키 열 또는 예측 가능한 열로 사용될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38f2e-109">Columns can be used as input columns, key columns, or predictable columns.</span></span>  
  
-   <span data-ttu-id="38f2e-110">**모델링 플래그** 는 사례 테이블에 정의된 데이터에 대한 추가 정보를 알고리즘에 제공하므로 알고리즘이 보다 정확한 모델을 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38f2e-110">**Modeling flags** provide the algorithm with additional information about the data that is defined in the case table, so that the algorithm can build a more accurate model.</span></span> <span data-ttu-id="38f2e-111">모델링 플래그는 DMX(Data Mining Extensions) 언어를 사용하여 프로그래밍 방식으로 정의하거나 **의** 데이터 마이닝 디자이너 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]에서 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38f2e-111">You can define modeling flags programmatically by using the Data Mining Extensions (DMX) language, or in **Data Mining Designer** in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="38f2e-112">다음 목록에서는 마이닝 모델 열에 정의할 수 있는 모델링 플래그를 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="38f2e-112">The following list describes the modeling flags that you can define on a mining model column.</span></span>  
  
 `MODEL_EXISTENCE_ONLY`  
 <span data-ttu-id="38f2e-113">특성의 존재 여부가 특성 열에 있는 값보다 더 중요함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="38f2e-113">Indicates that the presence of the attribute is more important than the values that are in the attribute column.</span></span> <span data-ttu-id="38f2e-114">예를 들어 특정 고객과 관련된 주문 항목 목록이 포함된 사례 테이블이 있다고 가정해 봅니다.</span><span class="sxs-lookup"><span data-stu-id="38f2e-114">For example, consider a case table that contains a list of order items that are associated with a particular customer.</span></span> <span data-ttu-id="38f2e-115">이 테이블 데이터에는 제품 종류, ID 및 각 항목의 값이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38f2e-115">The table data includes the product type, ID, and cost of each item.</span></span> <span data-ttu-id="38f2e-116">모델링을 위해서는 고객이 특정 주문 항목을 구입했다는 사실이 주문 항목의 값 자체보다 더 중요할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38f2e-116">For modeling purposes, the fact that the customer purchased a particular order item may be more important than the cost of the order item itself.</span></span> <span data-ttu-id="38f2e-117">이 경우 값 열을 `MODEL_EXISTENCE_ONLY`로 표시해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="38f2e-117">In this case, the cost column should be marked as `MODEL_EXISTENCE_ONLY`.</span></span>  
  
 `REGRESSOR`  
 <span data-ttu-id="38f2e-118">회귀 알고리즘의 회귀 수식에 지정된 열을 사용할 수 있음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="38f2e-118">Indicates that the algorithm can use the specified column in the regression formula of regression algorithms.</span></span> <span data-ttu-id="38f2e-119">이 플래그는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 의사 결정 트리 및 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 시계열 알고리즘에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38f2e-119">This flag is supported by the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Decision Trees and [!INCLUDE[msCoName](../../includes/msconame-md.md)] Time Series algorithms.</span></span>  
  
 <span data-ttu-id="38f2e-120">사용법 속성을 설정하고 DMX를 사용하여 프로그래밍 방식으로 모델링 플래그를 정의하는 방법은 [CREATE MINING MODEL&#40;DMX&#41;](/sql/dmx/create-mining-model-dmx)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="38f2e-120">For more information about setting the usage property and defining modeling flags programmatically with DMX, see [CREATE MINING MODEL &#40;DMX&#41;](/sql/dmx/create-mining-model-dmx).</span></span> <span data-ttu-id="38f2e-121">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]에서 사용법 속성을 설정하고 모델링 플래그를 정의하는 방법은 [데이터 마이닝 개체 이동](moving-data-mining-objects.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="38f2e-121">For more information about setting the usage property and defining modeling flags in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], see [Moving Data Mining Objects](moving-data-mining-objects.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38f2e-122">참고 항목</span><span class="sxs-lookup"><span data-stu-id="38f2e-122">See Also</span></span>  
 <span data-ttu-id="38f2e-123">[데이터 마이닝 알고리즘 &#40;Analysis Services 데이터 마이닝&#41;](data-mining-algorithms-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="38f2e-123">[Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;](data-mining-algorithms-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="38f2e-124">[마이닝 구조 &#40;Analysis Services 데이터 마이닝&#41;](mining-structures-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="38f2e-124">[Mining Structures &#40;Analysis Services - Data Mining&#41;](mining-structures-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="38f2e-125">[마이닝 모델의 속성 변경](change-the-properties-of-a-mining-model.md) </span><span class="sxs-lookup"><span data-stu-id="38f2e-125">[Change the Properties of a Mining Model](change-the-properties-of-a-mining-model.md) </span></span>  
 <span data-ttu-id="38f2e-126">[마이닝 모델에서 열 제외](exclude-a-column-from-a-mining-model.md) </span><span class="sxs-lookup"><span data-stu-id="38f2e-126">[Exclude a Column from a Mining Model](exclude-a-column-from-a-mining-model.md) </span></span>  
 [<span data-ttu-id="38f2e-127">마이닝 구조 열</span><span class="sxs-lookup"><span data-stu-id="38f2e-127">Mining Structure Columns</span></span>](mining-structure-columns.md)  
  
  
