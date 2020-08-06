---
title: 행 샘플링 변환 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.rowsamplingtrans.f1
helpviewer_keywords:
- sampling seeds [Integration Services]
- random seeds
- random sampling
- sample data sets [Integration Services]
- Row Sampling transformation
- packages [Integration Services], samples
- datasets [Integration Services], sample
ms.assetid: b6caafd3-30b2-4368-82af-a44611d4cd39
author: chugugrace
ms.author: chugu
ms.openlocfilehash: c56f07d9fafa03752ef8c6572a13c6ad7c02a8c8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743416"
---
# <a name="row-sampling-transformation"></a><span data-ttu-id="a2a8d-102">행 샘플링 변환</span><span class="sxs-lookup"><span data-stu-id="a2a8d-102">Row Sampling Transformation</span></span>
  <span data-ttu-id="a2a8d-103">행 샘플링 변환은 임의로 선택된 입력 데이터 세트의 하위 세트를 얻는 데 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="a2a8d-103">The Row Sampling transformation is used to obtain a randomly selected subset of an input dataset.</span></span> <span data-ttu-id="a2a8d-104">출력 샘플의 정확한 크기와 난수 생성기의 초기값을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a2a8d-104">You can specify the exact size of the output sample, and specify a seed for the random number generator.</span></span>  
  
 <span data-ttu-id="a2a8d-105">무작위 샘플링은 다양한 용도로 응용될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a2a8d-105">There are many applications for random sampling.</span></span> <span data-ttu-id="a2a8d-106">예를 들어 복권 당첨 경품을 받을 50명의 직원을 임의로 선택하려는 회사는 직원 데이터베이스에 대해 행 샘플링 변환을 사용하여 정확한 수의 당첨자를 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a2a8d-106">For example, a company that wanted to randomly select 50 employees to receive prizes in a lottery could use the Row Sampling transformation on the employee database to generate the exact number of winners.</span></span>  
  
 <span data-ttu-id="a2a8d-107">행 샘플링 변환은 패키지 개발 중에 전체 데이터 세트를 대표하지만 크기가 작은 데이터 세트를 만드는 데에도 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="a2a8d-107">The Row Sampling transformation is also useful during package development for creating a small but representative dataset.</span></span> <span data-ttu-id="a2a8d-108">유효한 대표 데이터를 사용하여 패키지 실행과 데이터 변환을 테스트할 수 있을 뿐만 아니라 전체 데이터 세트 대신 무작위 샘플링을 사용하기 때문에 시간이 훨씬 단축됩니다.</span><span class="sxs-lookup"><span data-stu-id="a2a8d-108">You can test package execution and data transformation with richly representative data, but more quickly because a random sample is used instead of the full dataset.</span></span> <span data-ttu-id="a2a8d-109">테스트 패키지에 사용되는 샘플 데이터 세트는 항상 크기가 같기 때문에 샘플 하위 집합을 사용하면 패키지의 성능 문제도 쉽게 식별할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a2a8d-109">Because the sample dataset used by the test package is always the same size, using the sample subset also makes it easier to identify performance problems in the package.</span></span>  
  
 <span data-ttu-id="a2a8d-110">이 변환은 입력 행의 비율을 선택하여 샘플 데이터 세트를 만드는 비율 샘플링 변환과 유사합니다.</span><span class="sxs-lookup"><span data-stu-id="a2a8d-110">This transformation is similar to the Percentage Sampling transformation, which creates a sample dataset by selecting a percentage of the input rows.</span></span> <span data-ttu-id="a2a8d-111">[Percentage Sampling Transformation](percentage-sampling-transformation.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a2a8d-111">See [Percentage Sampling Transformation](percentage-sampling-transformation.md).</span></span>  
  
## <a name="configuring-the-row-sampling-transformation"></a><span data-ttu-id="a2a8d-112">행 샘플링 변환 구성</span><span class="sxs-lookup"><span data-stu-id="a2a8d-112">Configuring the Row Sampling Transformation</span></span>  
 <span data-ttu-id="a2a8d-113">행 샘플링 변환은 지정한 수의 변환 입력 행을 선택하여 샘플 데이터 세트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="a2a8d-113">The Row Sampling transformation creates a sample dataset by selecting a specified number of the transformation input rows.</span></span> <span data-ttu-id="a2a8d-114">변환 입력에서 임의로 행이 선택되기 때문에 결과 샘플은 전체 입력을 대표합니다.</span><span class="sxs-lookup"><span data-stu-id="a2a8d-114">Because the selection of rows from the transformation input is random, the resultant sample is representative of the input.</span></span> <span data-ttu-id="a2a8d-115">난수 생성기에 사용되는 초기값을 지정하여 변환의 행 선택 방법에 영향을 줄 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a2a8d-115">You can also specify the seed that is used by the random number generator, to affect how the transformation selects rows.</span></span>  
  
 <span data-ttu-id="a2a8d-116">동일한 변환 입력에 대해 같은 임의 초기값을 사용하면 항상 동일한 샘플 출력이 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="a2a8d-116">Using the same random seed on the same transformation input always creates the same sample output.</span></span> <span data-ttu-id="a2a8d-117">초기값을 지정하지 않으면 변환에서 운영 체제의 틱 수를 사용하여 난수를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="a2a8d-117">If no seed is specified, the transformation uses the tick count of the operating system to create the random number.</span></span> <span data-ttu-id="a2a8d-118">따라서 패키지 개발 및 테스트 중에 변환 결과를 확인하기 위해 테스트 시에는 동일한 초기값을 사용한 다음 패키지를 프로덕션으로 이동할 때 임의 초기값으로 변경할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a2a8d-118">Therefore, you could use the same seed during testing, to verify the transformation results during the development and testing of the package, and then change to a random seed when the package is moved into production.</span></span>  
  
 <span data-ttu-id="a2a8d-119">행 샘플링 변환은 `SamplingValue` 사용자 지정 속성을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="a2a8d-119">The Row Sampling transformation includes the `SamplingValue` custom property.</span></span> <span data-ttu-id="a2a8d-120">이 속성은 패키지가 로드되면 속성 식을 사용하여 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a2a8d-120">This property can be updated by a property expression when the package is loaded.</span></span> <span data-ttu-id="a2a8d-121">자세한 내용은 [Integration Services&#40;SSIS&#41; 식](../../expressions/integration-services-ssis-expressions.md), [패키지에서 속성 식 사용](../../expressions/use-property-expressions-in-packages.md) 및 [변환 사용자 지정 속성](transformation-custom-properties.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a2a8d-121">For more information, see [Integration Services &#40;SSIS&#41; Expressions](../../expressions/integration-services-ssis-expressions.md), [Use Property Expressions in Packages](../../expressions/use-property-expressions-in-packages.md), and [Transformation Custom Properties](transformation-custom-properties.md).</span></span>  
  
 <span data-ttu-id="a2a8d-122">이 변환에는 하나의 입력과 두 개의 출력이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a2a8d-122">This transformation has one input and two outputs.</span></span> <span data-ttu-id="a2a8d-123">오류 출력은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a2a8d-123">It has no error output.</span></span>  
  
 <span data-ttu-id="a2a8d-124">[!INCLUDE[ssIS](../../../includes/ssis-md.md)] 디자이너를 사용하거나 프로그래밍 방식으로 속성을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a2a8d-124">You can set properties through [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="a2a8d-125">**행 샘플링 변환 편집기** 대화 상자에서 설정할 수 있는 속성에 대한 자세한 내용은 [행 샘플링 변환 편집기&#40;샘플링 페이지&#41;](../../row-sampling-transformation-editor-sampling-page.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a2a8d-125">For more information about the properties that you can set in the **Row Sampling Transformation Editor** dialog box, see [Row Sampling Transformation Editor &#40;Sampling Page&#41;](../../row-sampling-transformation-editor-sampling-page.md).</span></span>  
  
 <span data-ttu-id="a2a8d-126">**고급 편집기** 대화 상자에는 프로그래밍 방식으로 설정할 수 있는 속성이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="a2a8d-126">The **Advanced Editor** dialog box reflects the properties that can be set programmatically.</span></span> <span data-ttu-id="a2a8d-127">**고급 편집기** 대화 상자를 사용하거나 프로그래밍 방식으로 설정할 수 있는 속성에 대한 자세한 내용을 보려면 다음 항목 중 하나를 클릭하세요.</span><span class="sxs-lookup"><span data-stu-id="a2a8d-127">For more information about the properties that you can set in the **Advanced Editor** dialog box or programmatically, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="a2a8d-128">Common Properties</span><span class="sxs-lookup"><span data-stu-id="a2a8d-128">Common Properties</span></span>](../../common-properties.md)  
  
-   [<span data-ttu-id="a2a8d-129">변환 사용자 지정 속성</span><span class="sxs-lookup"><span data-stu-id="a2a8d-129">Transformation Custom Properties</span></span>](transformation-custom-properties.md)  
  
## <a name="related-tasks"></a><span data-ttu-id="a2a8d-130">관련 작업</span><span class="sxs-lookup"><span data-stu-id="a2a8d-130">Related Tasks</span></span>  
 [<span data-ttu-id="a2a8d-131">데이터 흐름 구성 요소의 속성 설정</span><span class="sxs-lookup"><span data-stu-id="a2a8d-131">Set the Properties of a Data Flow Component</span></span>](../set-the-properties-of-a-data-flow-component.md)  
  
  
