---
title: 데이터 마이닝 모델 학습 대상 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.dataminingmodeltrainingdest.f1
helpviewer_keywords:
- destinations [Integration Services], Data Mining Model Training
- Data Mining Model Training destination
- mining models [Analysis Services], training
- training mining models
ms.assetid: 6bc8cbe2-46af-4f7b-93d6-86779313c9d7
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e101a7e374f16b12b3a5aa30a49dbecd2632f06f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651827"
---
# <a name="data-mining-model-training-destination"></a><span data-ttu-id="b6f3c-102">데이터 마이닝 모델 학습 대상</span><span class="sxs-lookup"><span data-stu-id="b6f3c-102">Data Mining Model Training Destination</span></span>
  <span data-ttu-id="b6f3c-103">데이터 마이닝 모델 학습 대상은 데이터 마이닝 모델 알고리즘을 통해 대상에서 수신하는 데이터를 전달함으로써 데이터 마이닝 모델을 학습합니다.</span><span class="sxs-lookup"><span data-stu-id="b6f3c-103">The Data Mining Model Training destination trains data mining models by passing the data that the destination receives through the data mining model algorithms.</span></span> <span data-ttu-id="b6f3c-104">동일 데이터 마이닝 구조를 기반으로 모델을 작성한 경우에는 하나의 대상에서 여러 데이터 마이닝 모델의 성향을 습득할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b6f3c-104">Multiple data mining models can be trained by one destination if the models are built on the same data mining structure.</span></span> <span data-ttu-id="b6f3c-105">자세한 내용은 [Mining Structure Columns](https://docs.microsoft.com/analysis-services/data-mining/mining-structure-columns) 및 [Mining Model Columns](https://docs.microsoft.com/analysis-services/data-mining/mining-model-columns)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b6f3c-105">For more information, see [Mining Structure Columns](https://docs.microsoft.com/analysis-services/data-mining/mining-structure-columns) and [Mining Model Columns](https://docs.microsoft.com/analysis-services/data-mining/mining-model-columns).</span></span>  
  
## <a name="configuration-of-the-data-mining-model-training-destination"></a><span data-ttu-id="b6f3c-106">데이터 마이닝 모델 학습 대상 구성</span><span class="sxs-lookup"><span data-stu-id="b6f3c-106">Configuration of the Data Mining Model Training Destination</span></span>  
 <span data-ttu-id="b6f3c-107">대상 구조의 사례 수준 열과 이 구조에서 작성된 모델의 내용 유형이 KEY TIME 또는 KEY SEQUENCE인 경우 입력 데이터는 해당 열에서 정렬되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6f3c-107">If a case level column of the target structure and the models built on the structure has the content type KEY TIME or KEY SEQUENCE, the input data must be sorted on that column.</span></span> <span data-ttu-id="b6f3c-108">예를 들어 Microsoft Time Series 알고리즘을 사용하여 작성된 모델에서는 KEY TIME 내용 유형이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="b6f3c-108">For example, models built using the Microsoft Time Series algorithm use the content type KEY TIME.</span></span> <span data-ttu-id="b6f3c-109">입력 데이터가 정렬되지 않은 경우 모델 처리가 실패할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b6f3c-109">If input data is not sorted, the processing of the model may fail.</span></span> <span data-ttu-id="b6f3c-110">데이터에 정렬이 필요한 경우 데이터 흐름의 초반에 정렬 변환을 사용하여 데이터를 정렬할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b6f3c-110">If the data requires sorting, you can use a Sort transformation earlier in the data flow to sort the data.</span></span> <span data-ttu-id="b6f3c-111">내용 유형이 KEY인 열에서는 이렇게 할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b6f3c-111">This requirement does not apply to columns with the KEY content type.</span></span> <span data-ttu-id="b6f3c-112">자세한 내용은 [콘텐츠 형식&#40;데이터 마이닝&#41;](https://docs.microsoft.com/analysis-services/data-mining/content-types-data-mining) 및 [정렬 변환](transformations/sort-transformation.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b6f3c-112">For more information, see [Content Types &#40;Data Mining&#41;](https://docs.microsoft.com/analysis-services/data-mining/content-types-data-mining) and [Sort Transformation](transformations/sort-transformation.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b6f3c-113">데이터 마이닝 모델 학습 대상에 대한 입력은 정렬되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6f3c-113">The input to the Data Mining Model training destination must be sorted.</span></span> <span data-ttu-id="b6f3c-114">데이터를 정렬하기 위해서는 데이터 마이닝 모델 학습 대상의 정렬 대상 업스트림을 데이터 흐름에 포함시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b6f3c-114">To sort the data, you can include a Sort destination upstream from the Data Mining Model Training destination in the data flow.</span></span> <span data-ttu-id="b6f3c-115">자세한 내용은 [Sort Transformation](transformations/sort-transformation.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b6f3c-115">For more information, see [Sort Transformation](transformations/sort-transformation.md).</span></span>  
  
 <span data-ttu-id="b6f3c-116">이 대상에는 하나의 입력이 포함되며 출력은 포함되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b6f3c-116">This destination has one input and no output.</span></span>  
  
 <span data-ttu-id="b6f3c-117">데이터 마이닝 모델 학습 대상은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 연결 관리자를 사용하여 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 프로젝트 또는 대상이 학습하는 마이닝 구조와 마이닝 모델이 포함된 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="b6f3c-117">The Data Mining Model Training destination uses an [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] connection manager to connect to the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project or the instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] that contains the mining structure and mining models that the destination trains.</span></span> <span data-ttu-id="b6f3c-118">자세한 내용은 [Analysis Services Connection Manager](../connection-manager/analysis-services-connection-manager.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b6f3c-118">For more information, see [Analysis Services Connection Manager](../connection-manager/analysis-services-connection-manager.md).</span></span>  
  
 <span data-ttu-id="b6f3c-119">[!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너를 사용하거나 프로그래밍 방식으로 속성을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b6f3c-119">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="b6f3c-120">**데이터 마이닝 모델 학습 편집기** 대화 상자에서 설정할 수 있는 속성에 대한 자세한 내용을 보려면 다음 항목 중 하나를 클릭하십시오.</span><span class="sxs-lookup"><span data-stu-id="b6f3c-120">For more information about the properties that you can set in the **Data Mining Model Training Editor** dialog box, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="b6f3c-121">데이터 마이닝 모델 학습 편집기&#40;연결 탭&#41;</span><span class="sxs-lookup"><span data-stu-id="b6f3c-121">Data Mining Model Training Editor &#40;Connection Tab&#41;</span></span>](../data-mining-model-training-editor-connection-tab.md)  
  
-   [<span data-ttu-id="b6f3c-122">데이터 마이닝 모델 학습 편집기&#40;열 탭&#41;</span><span class="sxs-lookup"><span data-stu-id="b6f3c-122">Data Mining Model Training Editor &#40;Columns Tab&#41;</span></span>](../data-mining-model-training-editor-columns-tab.md)  
  
 <span data-ttu-id="b6f3c-123">**고급 편집기** 대화 상자에는 프로그래밍 방식으로 설정할 수 있는 속성이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="b6f3c-123">The **Advanced Editor** dialog box reflects the properties that can be set programmatically.</span></span> <span data-ttu-id="b6f3c-124">**고급 편집기** 대화 상자를 사용하거나 프로그래밍 방식으로 설정할 수 있는 속성에 대한 자세한 내용을 보려면 다음 항목 중 하나를 클릭하세요.</span><span class="sxs-lookup"><span data-stu-id="b6f3c-124">For more information about the properties that you can set in the **Advanced Editor** dialog box or programmatically, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="b6f3c-125">Common Properties</span><span class="sxs-lookup"><span data-stu-id="b6f3c-125">Common Properties</span></span>](../common-properties.md)  
  
-   [<span data-ttu-id="b6f3c-126">데이터 마이닝 모델 학습 대상 사용자 지정 속성</span><span class="sxs-lookup"><span data-stu-id="b6f3c-126">Data Mining Model Training Destination Custom Properties</span></span>](data-mining-model-training-destination-custom-properties.md)  
  
 <span data-ttu-id="b6f3c-127">속성을 설정하는 방법에 대한 자세한 내용은 [데이터 흐름 구성 요소의 속성 설정](set-the-properties-of-a-data-flow-component.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b6f3c-127">For more information about how to set properties, see [Set the Properties of a Data Flow Component](set-the-properties-of-a-data-flow-component.md).</span></span>  
  
  
