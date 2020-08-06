---
title: 비율 샘플링 변환 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.percentagesamplingtrans.f1
helpviewer_keywords:
- testing mining models
- sampling seeds [Integration Services]
- data mining [Analysis Services], sample data sets
- Percentage Sampling transformation
- sample data sets [Integration Services]
- datasets [Integration Services], sample
- training mining models
ms.assetid: 59767e52-f732-4b3f-8602-be50d0a64ef2
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e5fe41ecf4a2ca0f9d20eec2c8e10af8ed4cd47b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743423"
---
# <a name="percentage-sampling-transformation"></a><span data-ttu-id="665ea-102">비율 샘플링 변환</span><span class="sxs-lookup"><span data-stu-id="665ea-102">Percentage Sampling Transformation</span></span>
  <span data-ttu-id="665ea-103">비율 샘플링 변환은 변환 입력 행의 비율을 선택하여 샘플 데이터 집합을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="665ea-103">The Percentage Sampling transformation creates a sample data set by selecting a percentage of the transformation input rows.</span></span> <span data-ttu-id="665ea-104">샘플 데이터 집합은 입력을 대표하는 결과 샘플을 만들기 위해 변환 입력에서 임의로 선택한 행입니다.</span><span class="sxs-lookup"><span data-stu-id="665ea-104">The sample data set is a random selection of rows from the transformation input, to make the resultant sample representative of the input.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="665ea-105">지정한 비율 외에도 비율 샘플링 변환은 특정 행을 샘플 출력에 포함할지를 결정하는 알고리즘을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="665ea-105">In addition to the specified percentage, the Percentage Sampling transformation uses an algorithm to determine whether a row should be included in the sample output.</span></span> <span data-ttu-id="665ea-106">이는 샘플 출력의 행 수가 지정한 비율을 정확하게 반영하지 않을 수도 있다는 것을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="665ea-106">This means that the number of rows in the sample output may not exactly reflect the specified percentage.</span></span> <span data-ttu-id="665ea-107">예를 들어 행 수가 25,000개인 입력 데이터 집합에 대해 10%를 지정해도 2,500개 행을 가진 샘플이 생성되지 않고 샘플에 포함된 행 수가 이보다 많거나 적을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="665ea-107">For example, specifying 10 percent for an input data set that has 25,000 rows may not generate a sample with 2,500 rows; the sample may have a few more or a few less rows.</span></span>  
  
 <span data-ttu-id="665ea-108">비율 샘플링 변환은 특히 데이터 마이닝에 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="665ea-108">The Percentage Sampling transformation is especially useful for data mining.</span></span> <span data-ttu-id="665ea-109">이 변환을 사용하면 하나의 데이터 집합을 임의로 두 개의 데이터 집합으로 나눌 수 있으며 하나는 데이터 마이닝 모델 학습에 사용되고 다른 하나는 모델 테스트에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="665ea-109">By using this transformation, you can randomly divide a data set into two data sets: one for training the data mining model, and one for testing the model.</span></span>  
  
 <span data-ttu-id="665ea-110">비율 샘플링 변환은 패키지 개발을 위해 샘플 데이터 집합을 만드는 데에도 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="665ea-110">The Percentage Sampling transformation is also useful for creating sample data sets for package development.</span></span> <span data-ttu-id="665ea-111">비율 샘플링 변환을 데이터 흐름에 적용하면 데이터 특징을 유지하면서 데이터 집합의 크기를 균일하게 줄일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="665ea-111">By applying the Percentage Sampling transformation to a data flow, you can uniformly reduce the size of the data set while preserving its data characteristics.</span></span> <span data-ttu-id="665ea-112">테스트 패키지는 전체 데이터 집합을 대표하지만 크기가 작은 데이터 집합을 사용하기 때문에 보다 신속하게 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="665ea-112">The test package can then run more quickly because it uses a small, but representative, data set.</span></span>  
  
## <a name="configuration-the-percentage-sampling-transformation"></a><span data-ttu-id="665ea-113">비율 샘플링 변환 구성</span><span class="sxs-lookup"><span data-stu-id="665ea-113">Configuration the Percentage Sampling Transformation</span></span>  
 <span data-ttu-id="665ea-114">샘플링 초기값을 지정하여 비율 샘플링 변환이 행 선택 시 사용하는 난수 생성기의 동작을 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="665ea-114">You can specify a sampling seed to modify the behavior of the random number generator that the transformation uses to select rows.</span></span> <span data-ttu-id="665ea-115">같은 샘플링 초기값을 사용하면 이 변환은 항상 동일한 샘플 출력을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="665ea-115">If the same sampling seed is used, the transformation always creates the same sample output.</span></span> <span data-ttu-id="665ea-116">초기값을 지정하지 않으면 변환에서 운영 체제의 틱 수를 사용하여 난수를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="665ea-116">If no seed is specified, the transformation uses the tick count of the operating system to create the random number.</span></span> <span data-ttu-id="665ea-117">따라서 패키지 개발 및 테스트 중에 변환 결과를 확인하기 위해 표준 초기값을 사용하도록 선택한 다음 패키지를 프로덕션으로 이동할 때 임의 초기값을 사용하도록 변경할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="665ea-117">Therefore, you might choose to use a standard seed when you want to verify the transformation results during the development and testing of a package, and then change to use a random seed when the package is moved into production.</span></span>  
  
 <span data-ttu-id="665ea-118">이 변환은 지정한 수의 입력 행을 선택하여 샘플 데이터 집합을 만드는 행 샘플링 변환과 유사합니다.</span><span class="sxs-lookup"><span data-stu-id="665ea-118">This transformation is similar to the Row Sampling transformation, which creates a sample data set by selecting a specified number of the input rows.</span></span> <span data-ttu-id="665ea-119">자세한 내용은 [Row Sampling Transformation](row-sampling-transformation.md)을(를) 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="665ea-119">For more information, see [Row Sampling Transformation](row-sampling-transformation.md).</span></span>  
  
 <span data-ttu-id="665ea-120">비율 샘플링 변환은 `SamplingValue` 사용자 지정 속성을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="665ea-120">The Percentage Sampling transformation includes the `SamplingValue` custom property.</span></span> <span data-ttu-id="665ea-121">이 속성은 패키지가 로드되면 속성 식을 사용하여 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="665ea-121">This property can be updated by a property expression when the package is loaded.</span></span> <span data-ttu-id="665ea-122">자세한 내용은 [Integration Services&#40;SSIS&#41; 식](../../expressions/integration-services-ssis-expressions.md), [패키지에서 속성 식 사용](../../expressions/use-property-expressions-in-packages.md) 및 [변환 사용자 지정 속성](transformation-custom-properties.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="665ea-122">For more information, see [Integration Services &#40;SSIS&#41; Expressions](../../expressions/integration-services-ssis-expressions.md), [Use Property Expressions in Packages](../../expressions/use-property-expressions-in-packages.md), and [Transformation Custom Properties](transformation-custom-properties.md).</span></span>  
  
 <span data-ttu-id="665ea-123">이 변환에는 하나의 입력과 두 개의 출력이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="665ea-123">The transformation has one input and two outputs.</span></span> <span data-ttu-id="665ea-124">오류 출력은 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="665ea-124">It does not support an error output.</span></span>  
  
 <span data-ttu-id="665ea-125">[!INCLUDE[ssIS](../../../includes/ssis-md.md)] 디자이너를 사용하거나 프로그래밍 방식으로 속성을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="665ea-125">You can set properties through [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="665ea-126">**비율 샘플링 변환 편집기** 대화 상자에서 설정할 수 있는 속성에 대한 자세한 내용은 [Percentage Sampling Transformation Editor](../../percentage-sampling-transformation-editor.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="665ea-126">For more information about the properties that you can set in the **Percentage Sampling Transformation Editor** dialog box, see [Percentage Sampling Transformation Editor](../../percentage-sampling-transformation-editor.md).</span></span>  
  
 <span data-ttu-id="665ea-127">**고급 편집기** 대화 상자에는 프로그래밍 방식으로 설정할 수 있는 속성이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="665ea-127">The **Advanced Editor** dialog box reflects the properties that can be set programmatically.</span></span> <span data-ttu-id="665ea-128">**고급 편집기** 대화 상자를 사용하거나 프로그래밍 방식으로 설정할 수 있는 속성에 대한 자세한 내용을 보려면 다음 항목 중 하나를 클릭하세요.</span><span class="sxs-lookup"><span data-stu-id="665ea-128">For more information about the properties that you can set in the **Advanced Editor** dialog box or programmatically, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="665ea-129">Common Properties</span><span class="sxs-lookup"><span data-stu-id="665ea-129">Common Properties</span></span>](../../common-properties.md)  
  
-   [<span data-ttu-id="665ea-130">변환 사용자 지정 속성</span><span class="sxs-lookup"><span data-stu-id="665ea-130">Transformation Custom Properties</span></span>](transformation-custom-properties.md)  
  
 <span data-ttu-id="665ea-131">속성을 설정하는 방법에 대한 자세한 내용은 [데이터 흐름 구성 요소의 속성 설정](../set-the-properties-of-a-data-flow-component.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="665ea-131">For more information about how to set properties, see [Set the Properties of a Data Flow Component](../set-the-properties-of-a-data-flow-component.md).</span></span>  
  
  
