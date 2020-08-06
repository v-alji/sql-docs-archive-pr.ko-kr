---
title: 원본 큐브 차원 선택 (데이터 마이닝 마법사) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.dmwizard.selectsourcecube.f1
ms.assetid: 556e216b-5e21-4160-967d-4c57591fbab4
author: minewiskan
ms.author: owend
ms.openlocfilehash: 6295a5312b4501236e0ce8f5776fc43c0d014581
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647884"
---
# <a name="select-the-source-cube-dimension-data-mining-wizard"></a><span data-ttu-id="47f0b-102">원본 큐브 차원 선택(데이터 마이닝 마법사)</span><span class="sxs-lookup"><span data-stu-id="47f0b-102">Select the Source Cube Dimension (Data Mining Wizard)</span></span>
  <span data-ttu-id="47f0b-103">**원본 큐브 차원 선택** 페이지를 사용하여 분석할 사례를 포함하는 큐브의 차원을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="47f0b-103">Use the **Select the Source Cube Dimension** page to select the dimension from the cube that contains the cases you want to analyze.</span></span> <span data-ttu-id="47f0b-104">예를 들어 인구 통계를 기반으로 하여 고객의 구매 행동을 분석하는 모델을 작성하는 경우 일반적으로 각 고객 및 성별, 위치 또는 수입과 같은 인구 통계를 나타내는 여러 특성에 대해 고유한 레코드를 포함하는 Customer 차원을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="47f0b-104">For example, if you are building a model that analyzes the purchasing behavior of customers based on demographics, you would select the Customer dimension, which typically contains a unique record for each customer and various attributes that represent demographics, such as gender, location, or income.</span></span> <span data-ttu-id="47f0b-105">마법사의 뒷부분에서는 이 사례 테이블과 관련된 테이블을 추가할 수 있습니다. 예를 들어 고객이 구매한 제품을 보여 주는 중첩 테이블을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="47f0b-105">Later in the wizard you will have the opportunity to add a table that is related to this case table: for example, you might add a nested table that shows which products the customer has purchased.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="47f0b-106">이 페이지는 마법사의 **정의 방법 선택** 페이지에서 **기존 큐브 사용**을 선택한 경우에만 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="47f0b-106">This page will appear only if you have selected **From existing cube** on the **Select the Definition Method** page of the wizard.</span></span>  
  
## <a name="options"></a><span data-ttu-id="47f0b-107">옵션</span><span class="sxs-lookup"><span data-stu-id="47f0b-107">Options</span></span>  
 <span data-ttu-id="47f0b-108">**원본 큐브 차원 선택**</span><span class="sxs-lookup"><span data-stu-id="47f0b-108">**Select a Source Cube Dimension**</span></span>  
 <span data-ttu-id="47f0b-109">마이닝 구조의 원본 데이터를 제공할 큐브의 차원을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="47f0b-109">Select the dimension of the cube that will provide the source data for your mining structure.</span></span>  
  
## <a name="choosing-a-dimension"></a><span data-ttu-id="47f0b-110">차원 선택</span><span class="sxs-lookup"><span data-stu-id="47f0b-110">Choosing a Dimension</span></span>  
 <span data-ttu-id="47f0b-111">모델에 사용할 차원 하나만 선택할 수 있기 때문에 큐브 구조를 이해하고 모델에 대한 최상의 정보를 제공하는 차원을 선택하는 것이 중요합니다.</span><span class="sxs-lookup"><span data-stu-id="47f0b-111">Because you can select only one dimension for use in your model, it is important that you understand the cube structure and select the dimension that provides the best information for your model.</span></span> <span data-ttu-id="47f0b-112">사용할 차원을 잘 모르는 경우 차원 디자이너를 사용하여 큐브를 찾고 해당 큐브의 필드 및 데이터를 검토하는 것이 유용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="47f0b-112">If you are not sure which dimension to use, it might be helpful to browse the cube and review the fields and the data in them by using Dimension Designer.</span></span> <span data-ttu-id="47f0b-113">자세한 내용은 [차원 디자이너에서 차원 데이터 찾아보기](multidimensional-models/database-dimensions-browse-dimension-data-in-dimension-designer.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="47f0b-113">For more information, see [Browse Dimension Data in Dimension Designer](multidimensional-models/database-dimensions-browse-dimension-data-in-dimension-designer.md).</span></span>  
  
 <span data-ttu-id="47f0b-114">일반적으로 차원을 잘 모르는 경우 [차원 소개&#40;Analysis Services - 다차원 데이터&#41;](multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="47f0b-114">If you are unfamiliar with dimensions in general, see [Introduction to Dimensions &#40;Analysis Services - Multidimensional Data&#41;](multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md).</span></span>  
  
 <span data-ttu-id="47f0b-115">데이터 마이닝에 유용할 수 있는 특성 및 측정값을 포함하여 일반적으로 단일 차원에 포함되어 있는 정보 유형에 대한 자세한 내용은 [Dimension Relationships](multidimensional-models-olap-logical-cube-objects/dimension-relationships.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="47f0b-115">For more information about the type of information that is typically contained in a single dimension, including attributes and measures that might be useful for data mining, see [Dimension Relationships](multidimensional-models-olap-logical-cube-objects/dimension-relationships.md).</span></span>  
  
 <span data-ttu-id="47f0b-116">선택하는 차원에 데이터 마이닝 모델을 작성하는 데 필요한 관련 특성이 모두 포함되어 있지는 않은 경우 차원을 수정할 필요가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="47f0b-116">If the dimension that you choose does not contain all of the related attributes that you need to build the data mining model, you might need to modify the dimension.</span></span> <span data-ttu-id="47f0b-117">자세한 내용은 [데이터베이스 차원 정의](multidimensional-models/define-database-dimensions.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="47f0b-117">For more information, see [Define Database Dimensions](multidimensional-models/define-database-dimensions.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47f0b-118">참고 항목</span><span class="sxs-lookup"><span data-stu-id="47f0b-118">See Also</span></span>  
 <span data-ttu-id="47f0b-119">[데이터 마이닝 마법사 F1 도움말 &#40;Analysis Services 데이터 마이닝&#41;](data-mining-wizard-f1-help-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="47f0b-119">[Data Mining Wizard F1 Help &#40;Analysis Services - Data Mining&#41;](data-mining-wizard-f1-help-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="47f0b-120">[데이터 마이닝 마법사 &#40;데이터 마이닝 구조를 만듭니다&#41;](create-the-data-mining-structure-data-mining-wizard.md) </span><span class="sxs-lookup"><span data-stu-id="47f0b-120">[Create the Data Mining Structure &#40;Data Mining Wizard&#41;](create-the-data-mining-structure-data-mining-wizard.md) </span></span>  
 [<span data-ttu-id="47f0b-121">데이터 마이닝 마법사 &#40;사례 키를 선택&#41;</span><span class="sxs-lookup"><span data-stu-id="47f0b-121">Select the Case Key &#40;Data Mining Wizard&#41;</span></span>](select-the-case-key-data-mining-wizard.md)  
  
  
