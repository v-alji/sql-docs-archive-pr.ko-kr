---
title: 사용 빈도 기반 최적화 마법사 F1 도움말 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.usagebasedoptimizationwizard.f1
helpviewer_keywords:
- Usage-Based Optimization Wizard
ms.assetid: e5f5a938-ae7c-4f4e-9416-a7f94ac82763
author: minewiskan
ms.author: owend
ms.openlocfilehash: 517c122f79421294e1dfa562665948c4dc7bf95f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87735544"
---
# <a name="usage-based-optimization-wizard-f1-help"></a><span data-ttu-id="7e70c-102">사용 빈도 기반 최적화 마법사 F1 도움말</span><span class="sxs-lookup"><span data-stu-id="7e70c-102">Usage-Based Optimization Wizard F1 Help</span></span>
  <span data-ttu-id="7e70c-103">사용 빈도 기반 최적화 마법사는 출력 면에서 집계 디자인 마법사와 유사하며 파티션에 대한 집계를 디자인하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="7e70c-103">The Usage-Based Optimization Wizard is similar in output to the Aggregation Design Wizard, and is used to design aggregations for a partition.</span></span> <span data-ttu-id="7e70c-104">그러나 사용 빈도 기반 최적화 마법사는 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 인스턴스의 쿼리 로그에 기록된 쿼리의 특정 사용 패턴을 기반으로 집계를 디자인합니다.</span><span class="sxs-lookup"><span data-stu-id="7e70c-104">However, the Usage-Based Optimization Wizard designs aggregations based on the specific usage patterns of queries recorded in the query log of an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance.</span></span> <span data-ttu-id="7e70c-105">집계는 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 각 쿼리에 대해 기본 데이터 원본의 데이터를 다시 계산할 필요 없이 큐브 저장소에서 직접 미리 계산 된 합계를 검색할 수 있도록 하 여 성능 향상을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="7e70c-105">Aggregations provide performance improvements by allowing [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] to retrieve pre-calculated totals directly from cube storage instead of having to recalculate data from an underlying data source for each query.</span></span>  
  
 <span data-ttu-id="7e70c-106">내에서 사용 빈도 기반 최적화 마법사를 열려면 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 프로젝트의 큐브 디자이너를 연 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 다음 **집계** 탭을 클릭 합니다. 도구 모음에서 **사용 빈도 기반 최적화** 단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="7e70c-106">To open the Usage-Based Optimization Wizard from within [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the cube designer for an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] project, and then click the **Aggregations** tab. Click the **Usage Based Optimization** button in the toolbar.</span></span>  
  
 <span data-ttu-id="7e70c-107">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]내에서 사용 빈도 기반 최적화 마법사를 열려면 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 데이터베이스에 연결한 다음 **큐브** 폴더를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="7e70c-107">To open the Usage-Based Optimization Wizard from within [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], connect to an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database and then open the **Cubes** folder.</span></span> <span data-ttu-id="7e70c-108">큐브를 선택한 다음 **측정값 그룹** 폴더를 열고 수정하려는 측정값 그룹을 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="7e70c-108">Select a cube and then open the **Measure Groups** folder and expand the measure group that you want to modify.</span></span> <span data-ttu-id="7e70c-109">**파티션** 폴더를 마우스 오른쪽 단추로 클릭한 다음 **사용 빈도 기반 최적화**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="7e70c-109">Right-click the **Partitions** folder and then select **Usage Based Optimization**.</span></span>  
  
 <span data-ttu-id="7e70c-110">이러한 집계를 디자인하려면 집계 디자인 마법사를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="7e70c-110">To design these aggregations, you can use the Aggregation Design Wizard.</span></span> <span data-ttu-id="7e70c-111">이 마법사는 다음 단계로 이루어져 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7e70c-111">This wizard guides you through the following steps:</span></span>  
  
-   <span data-ttu-id="7e70c-112">스토리지에 대한 표준 또는 사용자 지정 설정 선택 및 파티션, 측정값 그룹 또는 큐브의 캐싱 옵션 선택</span><span class="sxs-lookup"><span data-stu-id="7e70c-112">Selecting standard or custom settings for the storage and caching options of a partition, measure group, or cube.</span></span>  
  
-   <span data-ttu-id="7e70c-113">파티션, 측정값 그룹 또는 큐브에서 참조하는 예상 또는 실제 개체 수 제공</span><span class="sxs-lookup"><span data-stu-id="7e70c-113">Providing estimated or actual counts for objects referenced by the partition, measure group, or cube.</span></span>  
  
-   <span data-ttu-id="7e70c-114">집계 옵션 및 제한을 지정하여 디자인된 집계에서 제공하는 스토리지 및 쿼리 성능 최적화</span><span class="sxs-lookup"><span data-stu-id="7e70c-114">Specifying aggregation options and limits to optimize the storage and query performance delivered by designed aggregations.</span></span>  
  
-   <span data-ttu-id="7e70c-115">파티션, 측정값 그룹 또는 큐브를 저장하고 선택적으로 처리하여 정의된 집계 생성</span><span class="sxs-lookup"><span data-stu-id="7e70c-115">Saving and optionally processing the partition, measure group, or cube to generate the defined aggregations.</span></span>  
  
 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]<span data-ttu-id="7e70c-116">의 집계 디자인 마법사를 사용하여 스토리지 크기 또는 예상 성능 향상으로 제한할 수 있는 집계 디자인의 배달을 위해 파티션 구조의 통계 분석을 기반으로 집계를 디자인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7e70c-116">provides the Aggregation Design Wizard to design aggregations based on statistical analysis of the structure of the partition to deliver an aggregation design that can be limited by storage size or estimated performance gain.</span></span> <span data-ttu-id="7e70c-117">집계 디자인 마법사를 사용하여 파티션의 전반적인 성능을 향상시킬 수도 있지만 집계 디자인이 비즈니스 사용자의 특정 요구에 부합하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7e70c-117">You can use the Aggregation Design Wizard to improve the overall performance of a partition, but the aggregation design is not targeted to the specific needs of your business users.</span></span> <span data-ttu-id="7e70c-118">사용 빈도 기반 최적화 마법사에서는 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 인스턴스에 대한 쿼리 로그에 특정 쿼리 생성에 필요한 정보가 충분히 포함된 경우 이러한 특정 요구에 부합하는 집계 디자인을 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7e70c-118">The Usage-Based Optimization Wizard can provide an aggregation design targeted to these specific needs, but the wizard can do so only if the query log for the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance contains enough information to construct such queries.</span></span>  
  
 <span data-ttu-id="7e70c-119">일반적으로 두 마법사를 함께 사용하여 배포 시는 물론 지속적으로 성능을 향상시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7e70c-119">Typically, both wizards are used together to improve performance both upon deployment and over time.</span></span> <span data-ttu-id="7e70c-120">파티션 또는 파티션이 포함된 큐브 또는 측정값 그룹을 처음에 배포한 경우에는 집계 디자인 마법사를 먼저 사용하여 전반적인 성능을 향상시켜야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7e70c-120">The Aggregation Design Wizard should be used first, when the partition (or the cube or measure group containing the partition) is initially deployed, to provide an overall performance benefit.</span></span> <span data-ttu-id="7e70c-121">일정 기간이 지나 쿼리 로그에 파티션에 대한 비즈니스 사용자의 쿼리를 기록한 다음에는 사용 빈도 기반 최적화 마법사를 사용하여 집계 디자인이 비즈니스 사용자의 성능 및 쿼리 요구 사항을 보다 잘 처리할 수 있도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7e70c-121">After a period of time during which you have recorded the queries of business users for the partition in the query log, you can then use the Usage-Based Optimization Wizard to further focus the aggregation design to better serve the performance and query requirements of your business users.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7e70c-122"> 쿼리 로그 구성 방법은 [Analysis Services 쿼리 로그 구성(Configuring the Analysis Services Query Log)](instances/log-operations-in-analysis-services.md?view=sql-server-2014#bkmk_querylog)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="7e70c-122">For information about configuring the query log, see [Configuring the Analysis Services Query Log](instances/log-operations-in-analysis-services.md?view=sql-server-2014#bkmk_querylog).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7e70c-123">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="7e70c-123">In This Section</span></span>  
  
-   [<span data-ttu-id="7e70c-124">사용 빈도 기반 최적화 마법사 &#40;수정할 파티션 선택&#41;</span><span class="sxs-lookup"><span data-stu-id="7e70c-124">Select Partitions to Modify &#40;Usage-Based Optimization Wizard&#41;</span></span>](select-partitions-to-modify-usage-based-optimization-wizard.md)  
  
-   [<span data-ttu-id="7e70c-125">사용 빈도 기반 최적화 마법사 &#40;쿼리 조건을 지정&#41;</span><span class="sxs-lookup"><span data-stu-id="7e70c-125">Specify Query Criteria &#40;Usage-Based Optimization Wizard&#41;</span></span>](specify-query-criteria-usage-based-optimization-wizard.md)  
  
-   [<span data-ttu-id="7e70c-126">사용 빈도 기반 최적화 마법사 &#40;최적화 될 쿼리를 검토&#41;</span><span class="sxs-lookup"><span data-stu-id="7e70c-126">Review the Queries that will be Optimized &#40;Usage-Based Optimization Wizard&#41;</span></span>](review-the-queries-that-will-be-optimized-usage-based-optimization-wizard.md)  
  
-   [<span data-ttu-id="7e70c-127">집계 사용 &#40;사용량 기반 최적화 마법사를 검토&#41;</span><span class="sxs-lookup"><span data-stu-id="7e70c-127">Review Aggregation Usage &#40;Usage-Based Optimiation Wizard&#41;</span></span>](review-aggregation-usage-usage-based-optimiation-wizard.md)  
  
-   [<span data-ttu-id="7e70c-128">&#40;사용 빈도 기반 최적화 마법사를 사용 하 여 개체 수를 지정&#41;</span><span class="sxs-lookup"><span data-stu-id="7e70c-128">Specify Object Counts &#40;Usage-Based Optimization Wizard&#41;</span></span>](specify-object-counts-usage-based-optimization-wizard.md)  
  
-   [<span data-ttu-id="7e70c-129">&#40;사용 빈도 기반 최적화 마법사를 사용 하 여 집계 옵션을 설정&#41;</span><span class="sxs-lookup"><span data-stu-id="7e70c-129">Set Aggregation Options &#40;Usage-Based Optimization Wizard&#41;</span></span>](set-aggregation-options-usage-based-optimization-wizard.md)  
  
-   [<span data-ttu-id="7e70c-130">마법사 완료 &#40;사용 빈도 기반 최적화 마법사&#41;</span><span class="sxs-lookup"><span data-stu-id="7e70c-130">Completing the Wizard &#40;Usage-Based Optimization Wizard&#41;</span></span>](completing-the-wizard-usage-based-optimization-wizard.md)  
  
## <a name="see-also"></a><span data-ttu-id="7e70c-131">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7e70c-131">See Also</span></span>  
 <span data-ttu-id="7e70c-132">[집계 및 집계 디자인](multidimensional-models-olap-logical-cube-objects/aggregations-and-aggregation-designs.md) </span><span class="sxs-lookup"><span data-stu-id="7e70c-132">[Aggregations and Aggregation Designs](multidimensional-models-olap-logical-cube-objects/aggregations-and-aggregation-designs.md) </span></span>  
 <span data-ttu-id="7e70c-133">[다차원 모델의 큐브](multidimensional-models/cubes-in-multidimensional-models.md) </span><span class="sxs-lookup"><span data-stu-id="7e70c-133">[Cubes in Multidimensional Models](multidimensional-models/cubes-in-multidimensional-models.md) </span></span>  
 <span data-ttu-id="7e70c-134">[집계 디자인 마법사 F1 도움말](aggregation-design-wizard-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="7e70c-134">[Aggregation Design Wizard F1 Help](aggregation-design-wizard-f1-help.md) </span></span>  
 [<span data-ttu-id="7e70c-135">다차원 데이터를 &#40;마법사 Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="7e70c-135">Analysis Services Wizards &#40;Multidimensional Data&#41;</span></span>](analysis-services-wizards-multidimensional-data.md)  
  
  
