---
title: 집계 사용법 검토 (사용 빈도 기반 최적화 마법사) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.storagedesignwizard.reviewaggregationusage.f1
ms.assetid: 49ce2094-c4dc-4e46-8cef-c17c5db084ca
author: minewiskan
ms.author: owend
ms.openlocfilehash: 5ef9f900e64858515db226d1f9b864874a4ba827
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647926"
---
# <a name="review-aggregation-usage-usage-based-optimiation-wizard"></a><span data-ttu-id="58821-102">집계 사용법 검토(사용 빈도 기반 최적화 마법사)</span><span class="sxs-lookup"><span data-stu-id="58821-102">Review Aggregation Usage (Usage-Based Optimiation Wizard)</span></span>
  <span data-ttu-id="58821-103">**집계 사용 검토** 페이지를 사용하여 집계 사용 설정을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="58821-103">Use the **Review Aggregation Usage** page to configure aggregation usage settings.</span></span>  
  
## <a name="options"></a><span data-ttu-id="58821-104">옵션</span><span class="sxs-lookup"><span data-stu-id="58821-104">Options</span></span>  
 <span data-ttu-id="58821-105">**기본값**</span><span class="sxs-lookup"><span data-stu-id="58821-105">**Default**</span></span>  
 <span data-ttu-id="58821-106">특성의 집계 사용 설정을 기본값으로 설정하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="58821-106">Select to set the aggregation usage setting for the attribute to Default.</span></span> <span data-ttu-id="58821-107">이 설정을 사용하면 디자이너에서 특성 및 차원의 유형을 기반으로 기본 규칙을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="58821-107">By using this setting, the designer applies a default rule based on the type of attribute and dimension.</span></span>  
  
 <span data-ttu-id="58821-108">**전체**</span><span class="sxs-lookup"><span data-stu-id="58821-108">**Full**</span></span>  
 <span data-ttu-id="58821-109">특성의 집계 사용 설정을 전체로 설정하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="58821-109">Select to set the aggregation usage setting for the attribute to Full.</span></span> <span data-ttu-id="58821-110">이 설정을 사용하면 큐브의 모든 집계에 이 특성이나 특성 체인에서 이 특성 아래에 있는 관련 특성이 포함되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="58821-110">By using this setting, every aggregation for the cube must include this attribute or a related attribute that is lower in the attribute chain.</span></span> <span data-ttu-id="58821-111">특성에 많은 멤버가 포함되어 있는 경우에는 전체 집계 사용 설정을 사용하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="58821-111">The Full aggregation usage setting should be avoided when an attribute contains many members.</span></span> <span data-ttu-id="58821-112">이 특성을 여러 특성이나 많은 멤버가 포함된 특성에 지정하면 크기가 너무 커지기 때문에 집계를 디자인할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="58821-112">If specified for multiple attributes or attributes that have many members, this setting might prevent aggregations from being designed because of excessive size.</span></span>  
  
 <span data-ttu-id="58821-113">**없음**</span><span class="sxs-lookup"><span data-stu-id="58821-113">**None**</span></span>  
 <span data-ttu-id="58821-114">특성의 집계 사용 설정을 없음으로 설정하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="58821-114">Select to set the aggregation usage setting for the attribute to None.</span></span> <span data-ttu-id="58821-115">이 설정을 사용하면 큐브의 집계에 이 특성을 포함할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="58821-115">By using this setting, no aggregation for the cube can include this attribute.</span></span>  
  
 <span data-ttu-id="58821-116">**무제한**</span><span class="sxs-lookup"><span data-stu-id="58821-116">**Unrestricted**</span></span>  
 <span data-ttu-id="58821-117">특성의 집계 사용 설정을 제한 없음으로 설정하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="58821-117">Select to set the aggregation usage setting for the attribute to Unrestricted.</span></span> <span data-ttu-id="58821-118">이 설정을 사용하면 집계 디자이너에 제한 사항이 지정되지 않지만</span><span class="sxs-lookup"><span data-stu-id="58821-118">By using this setting, no restrictions are put on the aggregation designer.</span></span> <span data-ttu-id="58821-119">해당 특성이 집계에 적절한 특성인지 여부는 계속 평가되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="58821-119">However, the attribute must still be evaluated to determine whether it is a valuable aggregation candidate.</span></span>  
  
 <span data-ttu-id="58821-120">**모두 기본값으로 설정**</span><span class="sxs-lookup"><span data-stu-id="58821-120">**Set All to Default**</span></span>  
 <span data-ttu-id="58821-121">모든 특성의 집계 사용 설정을 기본값으로 설정하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="58821-121">Select to set the aggregation usage settings for all attributes to Default.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58821-122">참고 항목</span><span class="sxs-lookup"><span data-stu-id="58821-122">See Also</span></span>  
 <span data-ttu-id="58821-123">[집계 디자인 마법사 F1 도움말](aggregation-design-wizard-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="58821-123">[Aggregation Design Wizard F1 Help](aggregation-design-wizard-f1-help.md) </span></span>  
 [<span data-ttu-id="58821-124">다차원 데이터를 &#40;마법사 Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="58821-124">Analysis Services Wizards &#40;Multidimensional Data&#41;</span></span>](analysis-services-wizards-multidimensional-data.md)  
  
  
