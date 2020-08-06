---
title: 집계 사용 검토 (집계 디자인 마법사) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.aggregationdesignwizard.reviewusage.f1
ms.assetid: 107ee872-3df2-4931-b56c-af11e38f6745
author: minewiskan
ms.author: owend
ms.openlocfilehash: afbb02dae64f3f7ebd57065c3ff8a7d1e202dcf2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647927"
---
# <a name="review-aggregation-usage-aggregation-design-wizard"></a><span data-ttu-id="9f997-102">집계 사용 검토(집계 디자인 마법사)</span><span class="sxs-lookup"><span data-stu-id="9f997-102">Review Aggregation Usage (Aggregation Design Wizard)</span></span>
  <span data-ttu-id="9f997-103">**집계 사용 검토** 페이지를 사용하여 집계 사용 설정을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9f997-103">Use the **Review Aggregation Usage** page to configure aggregation usage settings.</span></span>  
  
## <a name="options"></a><span data-ttu-id="9f997-104">옵션</span><span class="sxs-lookup"><span data-stu-id="9f997-104">Options</span></span>  
 <span data-ttu-id="9f997-105">**기본값**</span><span class="sxs-lookup"><span data-stu-id="9f997-105">**Default**</span></span>  
 <span data-ttu-id="9f997-106">특성의 집계 사용 설정을 기본값으로 설정하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="9f997-106">Select to set the aggregation usage setting for the attribute to Default.</span></span> <span data-ttu-id="9f997-107">이 설정을 사용하면 디자이너에서 특성 및 차원의 유형을 기반으로 기본 규칙을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="9f997-107">By using this setting, the designer applies a default rule based on the type of attribute and dimension.</span></span>  
  
 `Full`  
 <span data-ttu-id="9f997-108">특성의 집계 사용 설정을 `Full`로 설정하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="9f997-108">Select to set the aggregation usage setting for the attribute to `Full`.</span></span> <span data-ttu-id="9f997-109">이 설정을 사용하면 큐브의 모든 집계에 이 특성이나 특성 체인에서 이 특성 아래에 있는 관련 특성이 포함되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9f997-109">By using this setting, every aggregation for the cube must include this attribute or a related attribute that is lower in the attribute chain.</span></span> <span data-ttu-id="9f997-110">특성에 많은 멤버가 포함되어 있는 경우에는 `Full` 집계 사용 설정을 사용하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9f997-110">The `Full` aggregation usage setting should be avoided when an attribute contains many members.</span></span> <span data-ttu-id="9f997-111">이 특성을 여러 특성이나 많은 멤버가 포함된 특성에 지정하면 크기가 너무 커지기 때문에 집계를 디자인할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9f997-111">If specified for multiple attributes or attributes that have many members, this setting might prevent aggregations from being designed because of excessive size.</span></span>  
  
 <span data-ttu-id="9f997-112">**없음**</span><span class="sxs-lookup"><span data-stu-id="9f997-112">**None**</span></span>  
 <span data-ttu-id="9f997-113">특성의 집계 사용 설정을 없음으로 설정하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="9f997-113">Select to set the aggregation usage setting for the attribute to None.</span></span> <span data-ttu-id="9f997-114">이 설정을 사용하면 큐브의 집계에 이 특성을 포함할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9f997-114">By using this setting, no aggregation for the cube can include this attribute.</span></span>  
  
 `Unrestricted`  
 <span data-ttu-id="9f997-115">특성의 집계 사용 설정을 `Unrestricted`로 설정하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="9f997-115">Select to set the aggregation usage setting for the attribute to `Unrestricted`.</span></span> <span data-ttu-id="9f997-116">이 설정을 사용하면 집계 디자이너에 제한 사항이 지정되지 않지만 해당 특성이 집계에 적절한 특성인지 여부는 계속 평가되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9f997-116">By using this setting, no restrictions are put on the aggregation designer; however, the attribute must still be evaluated to determine whether it is a valuable aggregation candidate.</span></span>  
  
 <span data-ttu-id="9f997-117">**모두 기본값으로 설정**</span><span class="sxs-lookup"><span data-stu-id="9f997-117">**Set All to Default**</span></span>  
 <span data-ttu-id="9f997-118">모든 특성의 집계 사용 설정을 기본값으로 설정하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="9f997-118">Select to set the aggregation usage settings for all attributes to Default.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f997-119">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9f997-119">See Also</span></span>  
 <span data-ttu-id="9f997-120">[집계 디자인 마법사 F1 도움말](aggregation-design-wizard-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="9f997-120">[Aggregation Design Wizard F1 Help](aggregation-design-wizard-f1-help.md) </span></span>  
 [<span data-ttu-id="9f997-121">다차원 데이터를 &#40;마법사 Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="9f997-121">Analysis Services Wizards &#40;Multidimensional Data&#41;</span></span>](analysis-services-wizards-multidimensional-data.md)  
  
  
