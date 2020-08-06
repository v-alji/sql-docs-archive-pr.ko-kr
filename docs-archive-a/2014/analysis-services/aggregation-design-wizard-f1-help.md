---
title: 집계 디자인 마법사 F1 도움말 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Aggregation Design Wizard
ms.assetid: 39e23cf1-6405-4fb6-bc14-ba103314362d
author: minewiskan
ms.author: owend
ms.openlocfilehash: ace30a07970b1871d037ebe6f31b2079f1895ffa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648229"
---
# <a name="aggregation-design-wizard-f1-help"></a><span data-ttu-id="54eb6-102">집계 디자인 마법사 F1 도움말</span><span class="sxs-lookup"><span data-stu-id="54eb6-102">Aggregation Design Wizard F1 Help</span></span>
  <span data-ttu-id="54eb6-103">집계는 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 각 쿼리에 대해 기본 데이터 원본의 데이터를 다시 계산할 필요 없이 큐브 저장소에서 직접 미리 계산 된 합계를 검색할 수 있도록 하 여 성능 향상을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="54eb6-103">Aggregations provide performance improvements by allowing [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] to retrieve pre-calculated totals directly from cube storage instead of having to recalculate data from an underlying data source for each query.</span></span>  
  
 <span data-ttu-id="54eb6-104">이러한 집계를 디자인하려면 집계 디자인 마법사를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="54eb6-104">To design these aggregations, you can use the Aggregation Design Wizard.</span></span> <span data-ttu-id="54eb6-105">이 마법사는 다음 단계로 이루어져 있습니다.</span><span class="sxs-lookup"><span data-stu-id="54eb6-105">This wizard guides you through the following steps:</span></span>  
  
-   <span data-ttu-id="54eb6-106">스토리지에 대한 표준 또는 사용자 지정 설정 선택 및 파티션, 측정값 그룹 또는 큐브의 캐싱 옵션 선택</span><span class="sxs-lookup"><span data-stu-id="54eb6-106">Selecting standard or custom settings for the storage and caching options of a partition, measure group, or cube.</span></span>  
  
-   <span data-ttu-id="54eb6-107">파티션, 측정값 그룹 또는 큐브에서 참조하는 예상 또는 실제 개체 수 제공</span><span class="sxs-lookup"><span data-stu-id="54eb6-107">Providing estimated or actual counts for objects referenced by the partition, measure group, or cube.</span></span>  
  
-   <span data-ttu-id="54eb6-108">집계 옵션 및 제한을 지정하여 디자인된 집계에서 제공하는 스토리지 및 쿼리 성능 최적화</span><span class="sxs-lookup"><span data-stu-id="54eb6-108">Specifying aggregation options and limits to optimize the storage and query performance delivered by designed aggregations.</span></span>  
  
-   <span data-ttu-id="54eb6-109">파티션, 측정값 그룹 또는 큐브를 저장하고 선택적으로 처리하여 정의된 집계 생성</span><span class="sxs-lookup"><span data-stu-id="54eb6-109">Saving and optionally processing the partition, measure group, or cube to generate the defined aggregations.</span></span>  
  
 <span data-ttu-id="54eb6-110">집계 디자인 마법사를 사용한 후 사용 빈도 기반 최적화 마법사를 사용하여 큐브를 쿼리하는 클라이언트 애플리케이션 및 비즈니스 사용자의 사용 패턴을 기반으로 집계를 디자인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="54eb6-110">After you use the Aggregation Design Wizard, you can use the Usage-Based Optimization Wizard to design aggregations based on the usage patterns of the business users and client applications that query the cube.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="54eb6-111">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="54eb6-111">In This Section</span></span>  
  
-   [<span data-ttu-id="54eb6-112">&#40;집계 디자인 마법사를 수정할 파티션 선택&#41;</span><span class="sxs-lookup"><span data-stu-id="54eb6-112">Select Partitions to Modify &#40;Aggregation Design Wizard&#41;</span></span>](select-partitions-to-modify-aggregation-design-wizard.md)  
  
-   [<span data-ttu-id="54eb6-113">집계 사용 &#40;집계 디자인 마법사를 검토&#41;</span><span class="sxs-lookup"><span data-stu-id="54eb6-113">Review Aggregation Usage &#40;Aggregation Design Wizard&#41;</span></span>](review-aggregation-usage-aggregation-design-wizard.md)  
  
-   [<span data-ttu-id="54eb6-114">집계 디자인 마법사 &#40;개체 개수 지정&#41;</span><span class="sxs-lookup"><span data-stu-id="54eb6-114">Specify Object Counts &#40;Aggregation Design Wizard&#41;</span></span>](specify-object-counts-aggregation-design-wizard.md)  
  
-   [<span data-ttu-id="54eb6-115">집계 옵션 &#40;집계 디자인 마법사를 설정&#41;</span><span class="sxs-lookup"><span data-stu-id="54eb6-115">Set Aggregation Options &#40;Aggregation Design Wizard&#41;</span></span>](set-aggregation-options-aggregation-design-wizard.md)  
  
-   [<span data-ttu-id="54eb6-116">&#40;집계 디자인 마법사를 완료 하는 중&#41;</span><span class="sxs-lookup"><span data-stu-id="54eb6-116">Completing the Wizard &#40;Aggregation Design Wizard&#41;</span></span>](completing-the-wizard-aggregation-design-wizard.md)  
  
## <a name="see-also"></a><span data-ttu-id="54eb6-117">참고 항목</span><span class="sxs-lookup"><span data-stu-id="54eb6-117">See Also</span></span>  
 <span data-ttu-id="54eb6-118">[집계 및 집계 디자인](multidimensional-models-olap-logical-cube-objects/aggregations-and-aggregation-designs.md) </span><span class="sxs-lookup"><span data-stu-id="54eb6-118">[Aggregations and Aggregation Designs](multidimensional-models-olap-logical-cube-objects/aggregations-and-aggregation-designs.md) </span></span>  
 <span data-ttu-id="54eb6-119">[다차원 모델의 큐브](multidimensional-models/cubes-in-multidimensional-models.md) </span><span class="sxs-lookup"><span data-stu-id="54eb6-119">[Cubes in Multidimensional Models](multidimensional-models/cubes-in-multidimensional-models.md) </span></span>  
 <span data-ttu-id="54eb6-120">[사용 빈도 기반 최적화 마법사 F1 도움말](usage-based-optimization-wizard-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="54eb6-120">[Usage-Based Optimization Wizard F1 Help](usage-based-optimization-wizard-f1-help.md) </span></span>  
 [<span data-ttu-id="54eb6-121">다차원 데이터를 &#40;마법사 Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="54eb6-121">Analysis Services Wizards &#40;Multidimensional Data&#41;</span></span>](analysis-services-wizards-multidimensional-data.md)  
  
  
