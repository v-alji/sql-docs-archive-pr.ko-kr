---
title: 원본 큐브 조각화 (데이터 마이닝 마법사) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.dmwizard.slicesourcecube.f1
ms.assetid: 16485608-d3b9-49ee-8baa-948038cdd7ec
author: minewiskan
ms.author: owend
ms.openlocfilehash: 762248d4c2a268ac36b0dfa3ffeba20123017017
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736861"
---
# <a name="slice-source-cube-data-mining-wizard"></a><span data-ttu-id="2aed7-102">원본 큐브 조각화(데이터 마이닝 마법사)</span><span class="sxs-lookup"><span data-stu-id="2aed7-102">Slice Source Cube (Data Mining Wizard)</span></span>
  <span data-ttu-id="2aed7-103">**원본 큐브 조각화** 대화 상자를 사용하여 모델의 학습에 사용되는 데이터를 제한할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2aed7-103">You can use the **Slice Source Cube** dialog box to restrict the data used to train the model.</span></span> <span data-ttu-id="2aed7-104">일반적으로 큐브는 모든 상점, 모든 지역 및 모든 제품 등 여러 다른 차원 및 특성과 관련된 데이터를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="2aed7-104">Typically a cube contains data related to many different dimensions and attributes, such as all stores, all regions, and all products.</span></span> <span data-ttu-id="2aed7-105">제한 없는 특성 조합의 모델 학습은 실용적이지 않으므로 이 대화 상자를 사용하여 모델 학습에 사용할 특정 집합을 선택하십시오.</span><span class="sxs-lookup"><span data-stu-id="2aed7-105">It is not practical to train a model on unlimited combinations of attributes, so you use this dialog box to choose a specific set to use in training a model.</span></span>  
  
 <span data-ttu-id="2aed7-106">예를 들어 AdventureWorks 큐브에서 특정 제품 라인, 지역 또는 연도별로 조각화하여 일부 데이터를 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2aed7-106">For example, in the AdventureWorks cube, you might slice by a particular product line, region, or year, to get a portion of the data.</span></span>  
  
 <span data-ttu-id="2aed7-107">조각과 큐브에 대해 잘 모르는 경우 다음 문서를 검토하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="2aed7-107">If you are unfamiliar with slices and cubes, we recommend that you review these articles:</span></span>  
  
-   [<span data-ttu-id="2aed7-108">파티션 조각 속성 &#40;Analysis Services 설정&#41;</span><span class="sxs-lookup"><span data-stu-id="2aed7-108">Set the Partition Slice Property &#40;Analysis Services&#41;</span></span>](multidimensional-models/set-the-partition-slice-property-analysis-services.md)  
  
-   [<span data-ttu-id="2aed7-109">로컬 파티션 만들기 및 관리&#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="2aed7-109">Create and Manage a Local Partition &#40;Analysis Services&#41;</span></span>](multidimensional-models/create-and-manage-a-local-partition-analysis-services.md)  
  
> [!NOTE]  
>  <span data-ttu-id="2aed7-110">동적 MDX 함수(예: [Generate&#40;MDX&#41;](/sql/mdx/generate-mdx) 또는 [Except&#40;MDX&#41;](/sql/mdx/except-mdx-function))는 파티션에 대한 Slice 속성에서 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2aed7-110">Note that dynamic MDX functions (such as [Generate &#40;MDX&#41;](/sql/mdx/generate-mdx) or [Except &#40;MDX&#41;](/sql/mdx/except-mdx-function)) are not supported in the Slice property for partitions.</span></span> <span data-ttu-id="2aed7-111">명시적 튜플 또는 멤버 참조를 사용하여 조각을 정의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2aed7-111">You must define the slice by using explicit tuples or member references.</span></span>  
>   
>  <span data-ttu-id="2aed7-112">예를 들어 &#40;범위를 사용 하 여 범위를 정의 하는 대신, 범위를 정의 하는 데 [&#41; &#40;MDX&#41;](/sql/mdx/range-mdx) 를 사용 하는 대신 각 멤버를 특정 연도로 열거 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2aed7-112">For example, rather than using  [: &#40;Range&#41; &#40;MDX&#41;](/sql/mdx/range-mdx) to define a range, you would need to enumerate each member by the specific years.</span></span>  
>   
>  <span data-ttu-id="2aed7-113">복잡한 조각을 정의해야 하는 경우 XMLA Alter 스크립트를 사용하여 조각에서 튜플을 정의하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="2aed7-113">If you need to define a complex slice, we recommend that you define the tuples in the slice by using an XMLA Alter script.</span></span> <span data-ttu-id="2aed7-114">그런 다음 ascmd 명령줄 도구 또는 SSIS [Analysis Services Execute DDL Task](../integration-services/control-flow/analysis-services-execute-ddl-task.md) 를 사용하여 스크립트를 실행하고 지정된 멤버 집합을 만든 후 곧바로 파티션을 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2aed7-114">Then, you can use either the ascmd command-line tool or the SSIS [Analysis Services Execute DDL Task](../integration-services/control-flow/analysis-services-execute-ddl-task.md) to run the script and create the specified set of members immediately before you process the partition.</span></span>  
  
 <span data-ttu-id="2aed7-115">**자세한 내용:** [데이터 마이닝 마법사&#40;Analysis Services - 데이터 마이닝&#41;](data-mining/data-mining-wizard-analysis-services-data-mining.md), [관계형 마이닝 구조 만들기](data-mining/create-a-relational-mining-structure.md)</span><span class="sxs-lookup"><span data-stu-id="2aed7-115">**For More Information:** [Data Mining Wizard &#40;Analysis Services - Data Mining&#41;](data-mining/data-mining-wizard-analysis-services-data-mining.md), [Create a Relational Mining Structure](data-mining/create-a-relational-mining-structure.md)</span></span>  
  
## <a name="options"></a><span data-ttu-id="2aed7-116">옵션</span><span class="sxs-lookup"><span data-stu-id="2aed7-116">Options</span></span>  
 <span data-ttu-id="2aed7-117">**크기**</span><span class="sxs-lookup"><span data-stu-id="2aed7-117">**Dimension**</span></span>  
 <span data-ttu-id="2aed7-118">조각화하려는 차원을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="2aed7-118">Select the dimension that you want to slice.</span></span>  
  
 <span data-ttu-id="2aed7-119">**계층**</span><span class="sxs-lookup"><span data-stu-id="2aed7-119">**Hierarchy**</span></span>  
 <span data-ttu-id="2aed7-120">조각화하려는 계층을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="2aed7-120">Select the hierarchy that you want to slice.</span></span> <span data-ttu-id="2aed7-121">계층의 모든 수준을 선택할 수 있지만 모델에 사용되는 특성은 선택한 수준에만 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2aed7-121">You can choose any level of a hierarchy, but the attributes used in the model will be only at the level that you choose.</span></span>  
  
 <span data-ttu-id="2aed7-122">예를 들어 Geography 계층을 선택하고 Country를 수준으로 선택하는 경우 City를 특성으로 사용하는 모델을 작성할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2aed7-122">For example, if you choose the Geography hierarchy, and select Country as the level, you cannot build a model that uses City as the attributes.</span></span> <span data-ttu-id="2aed7-123">반대로 City를 조각화할 계층의 수준으로 선택하는 경우 Country를 기준으로 마이닝 모델을 만들 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2aed7-123">Conversely, if you choose City as the level of the hierarchy on which to slice, you cannot create a mining model based on Country.</span></span>  
  
 <span data-ttu-id="2aed7-124">**연산자**</span><span class="sxs-lookup"><span data-stu-id="2aed7-124">**Operator**</span></span>  
 <span data-ttu-id="2aed7-125">조각화 식을 작성하는 데 사용할 연산자를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="2aed7-125">Select the operator to use in building a slice expression.</span></span>  
  
 <span data-ttu-id="2aed7-126">예를 들어 Geography를 계층으로 선택한 경우 연산자 =를 선택한 다음 "유럽"을 필터로 입력 하 여 유럽의 큐브 데이터만 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2aed7-126">For example, if you chose Geography as the hierarchy, you could select the operator = and then type "Europe" as the filter, to get cube data for Europe only.</span></span>  
  
 <span data-ttu-id="2aed7-127">**필터 식**</span><span class="sxs-lookup"><span data-stu-id="2aed7-127">**Filter Expression**</span></span>  
 <span data-ttu-id="2aed7-128">선택한 차원의 큐브를 필터링할 때 조건 유형으로 사용할 식을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="2aed7-128">Type an expression to use as a criterion when filtering the cube on the selected dimension.</span></span>  
  
 <span data-ttu-id="2aed7-129">**매개 변수**</span><span class="sxs-lookup"><span data-stu-id="2aed7-129">**Parameters**</span></span>  
 <span data-ttu-id="2aed7-130">이 옵션은 데이터 마이닝 모델에는 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2aed7-130">This option is not used for data mining models.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2aed7-131">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2aed7-131">See Also</span></span>  
 <span data-ttu-id="2aed7-132">[마법사 완료 &#40;데이터 마이닝 마법사&#41;](completing-the-wizard-data-mining-wizard.md) </span><span class="sxs-lookup"><span data-stu-id="2aed7-132">[Completing the Wizard &#40;Data Mining Wizard&#41;](completing-the-wizard-data-mining-wizard.md) </span></span>  
 <span data-ttu-id="2aed7-133">[데이터 마이닝 마법사 F1 도움말 &#40;Analysis Services 데이터 마이닝&#41;](data-mining-wizard-f1-help-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="2aed7-133">[Data Mining Wizard F1 Help &#40;Analysis Services - Data Mining&#41;](data-mining-wizard-f1-help-analysis-services-data-mining.md) </span></span>  
 [<span data-ttu-id="2aed7-134">데이터 마이닝 마법사 &#40;마이닝 모델 열 사용법 지정&#41;</span><span class="sxs-lookup"><span data-stu-id="2aed7-134">Specify Mining Model Column Usage &#40;Data Mining Wizard&#41;</span></span>](specify-mining-model-column-usage-data-mining-wizard.md)  
  
  
