---
title: 반 가산적 동작 정의 (비즈니스 인텔리전스 마법사) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.biwizard.semiadditivememberdetection.f1
ms.assetid: e57080ba-ce96-40f8-bca7-6701d1725b3c
author: minewiskan
ms.author: owend
ms.openlocfilehash: 5a3c46de038a7e45dcb39805e324260676a03228
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728952"
---
# <a name="define-semiadditive-behavior-business-intelligence-wizard"></a><span data-ttu-id="2abbe-102">반가산적 동작 정의(비즈니스 인텔리전스 마법사)</span><span class="sxs-lookup"><span data-stu-id="2abbe-102">Define Semiadditive Behavior (Business Intelligence Wizard)</span></span>
  <span data-ttu-id="2abbe-103">**반가산적 동작 정의** 페이지를 사용하여 측정값에 대한 반가산적 동작을 설정 또는 해제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2abbe-103">Use the **Define Semiadditive Behavior** page to enable or disable semi-additive behavior on measures.</span></span> <span data-ttu-id="2abbe-104">반가산적 동작은 큐브에 포함된 측정값이 시간 차원에 대해 집계되는 방법을 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="2abbe-104">Semi-additive behavior determines how measures that are contained by a cube are aggregated over a time dimension.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2abbe-105">표준 버전에서 제공되는 LastChild를 제외하고, 반가산적 동작은 비즈니스 인텔리전스 또는 엔터프라이즈 버전에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2abbe-105">With the exception of LastChild which is available in the standard edition, semi-additive behaviors are only available in the business intelligence or enterprise editions.</span></span> <span data-ttu-id="2abbe-106">또한 반가산적 동작이 측정값에 대해서만 정의되고 차원에 대해서는 정의되지 않기 때문에 차원 디자이너에서 시작되거나 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]의 솔루션 탐색기에서 차원을 마우스 오른쪽 단추로 클릭하여 시작된 비즈니스 인텔리전스 마법사에는 이 페이지가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2abbe-106">Furthermore, because semiadditive behavior is defined only on measures and not dimensions, you will not find this page in the Business Intelligence Wizard if it was started from Dimension Designer or by right-clicking a dimension in Solution Explorer in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span>  
  
## <a name="options"></a><span data-ttu-id="2abbe-107">옵션</span><span class="sxs-lookup"><span data-stu-id="2abbe-107">Options</span></span>  
 <span data-ttu-id="2abbe-108">**반가산적 동작 해제**</span><span class="sxs-lookup"><span data-stu-id="2abbe-108">**Turn off semiadditive behavior**</span></span>  
 <span data-ttu-id="2abbe-109">큐브에 포함된 모든 측정값의 반가산적 동작을 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="2abbe-109">Disables semi-additive behavior in all measures contained by the cube.</span></span>  
  
 <span data-ttu-id="2abbe-110">**마법사에서 \<dimension name> 반 가산적 멤버가 포함 된 계정 차원을 검색 했습니다. 서버는 각 계정 유형에 지정 된 반 가산적 동작에 따라이 차원의 멤버를 집계 합니다.**</span><span class="sxs-lookup"><span data-stu-id="2abbe-110">**The wizard has detected the \<dimension name> account dimension, which contains semiadditive members. The server will aggregate members of this dimension according to the semiadditive behavior specified for each account type.**</span></span>  
 <span data-ttu-id="2abbe-111">반가산적 멤버를 포함하는 계정 차원에 대한 반가산적 동작을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="2abbe-111">Enables semi-additive behavior for account dimensions that contain semi-additive members.</span></span> <span data-ttu-id="2abbe-112">이 옵션을 선택하면 계정 차원을 참조하는 측정값 그룹의 모든 측정값 집계 함수가 `ByAccount`로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="2abbe-112">Selecting this option sets the aggregation function of all measures in measure groups that reference the account dimension to `ByAccount`.</span></span>  
  
 <span data-ttu-id="2abbe-113">계정 차원에 대한 자세한 내용은 [부모-자식 유형 차원의 재무 계정 만들기](multidimensional-models/database-dimensions-finance-account-of-parent-child-type.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2abbe-113">For more information about account dimensions, see [Create a Finance Account of parent-child type Dimension](multidimensional-models/database-dimensions-finance-account-of-parent-child-type.md).</span></span>  
  
 <span data-ttu-id="2abbe-114">**개별 측정값에 대한 반가산적 동작 정의**</span><span class="sxs-lookup"><span data-stu-id="2abbe-114">**Define semiadditive behavior for individual members**</span></span>  
 <span data-ttu-id="2abbe-115">반가산적 동작을 설정하고 특정 측정값에 대한 반가산적 집계 함수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2abbe-115">Enables semi-additive behavior and specifies the semi-additive aggregation function for specific measures.</span></span> <span data-ttu-id="2abbe-116">이 집계 함수는 해당 측정값을 포함하는 측정값 그룹이 참조하는 모든 차원에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="2abbe-116">The aggregation function applies to all dimensions that are referenced by the measure group that contains the measure.</span></span>  
  
 <span data-ttu-id="2abbe-117">**측정값**</span><span class="sxs-lookup"><span data-stu-id="2abbe-117">**Measures**</span></span>  
 <span data-ttu-id="2abbe-118">큐브에 포함된 측정값의 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="2abbe-118">Displays the name of a measure contained by the cube.</span></span>  
  
 <span data-ttu-id="2abbe-119">**반 가산적 함수**</span><span class="sxs-lookup"><span data-stu-id="2abbe-119">**Semiadditive Function**</span></span>  
 <span data-ttu-id="2abbe-120">선택한 측정값에 대한 집계 함수를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="2abbe-120">Select the aggregation function for the selected measure.</span></span> <span data-ttu-id="2abbe-121">다음 표에서는 사용 가능한 집계 함수를 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="2abbe-121">The following table lists the aggregation functions that are available.</span></span>  
  
|<span data-ttu-id="2abbe-122">값</span><span class="sxs-lookup"><span data-stu-id="2abbe-122">Value</span></span>|<span data-ttu-id="2abbe-123">Description</span><span class="sxs-lookup"><span data-stu-id="2abbe-123">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="2abbe-124">**AverageOfChildren**</span><span class="sxs-lookup"><span data-stu-id="2abbe-124">**AverageOfChildren**</span></span>|<span data-ttu-id="2abbe-125">측정값의 자식 평균을 반환하여 집계됩니다.</span><span class="sxs-lookup"><span data-stu-id="2abbe-125">Aggregated by returning the average of the measure's children.</span></span>|  
|`ByAccount`|<span data-ttu-id="2abbe-126">계정 차원에 지정된 특성의 계정 유형과 연결된 집계 함수에 의해 집계됩니다.</span><span class="sxs-lookup"><span data-stu-id="2abbe-126">Aggregated by the aggregation function associated with the specified account type of an attribute in an account dimension.</span></span>|  
|`Count`|<span data-ttu-id="2abbe-127">`Count` 함수를 사용하여 집계됩니다.</span><span class="sxs-lookup"><span data-stu-id="2abbe-127">Aggregated using the `Count` function.</span></span>|  
|`DistinctCount`|<span data-ttu-id="2abbe-128">`DistinctCount` 함수를 사용하여 집계됩니다.</span><span class="sxs-lookup"><span data-stu-id="2abbe-128">Aggregated using the `DistinctCount` function.</span></span>|  
|<span data-ttu-id="2abbe-129">**FirstChild**</span><span class="sxs-lookup"><span data-stu-id="2abbe-129">**FirstChild**</span></span>|<span data-ttu-id="2abbe-130">시간 차원에 대해 측정값의 첫 번째 자식 멤버를 반환하여 집계됩니다.</span><span class="sxs-lookup"><span data-stu-id="2abbe-130">Aggregated by returning the measure's first child member over a time dimension.</span></span>|  
|<span data-ttu-id="2abbe-131">**FirstNonEmpty**</span><span class="sxs-lookup"><span data-stu-id="2abbe-131">**FirstNonEmpty**</span></span>|<span data-ttu-id="2abbe-132">시간 차원에 대해 측정값의 첫 번째 비어 있지 않은 멤버를 반환하여 집계됩니다.</span><span class="sxs-lookup"><span data-stu-id="2abbe-132">Aggregated by returning the measure's first nonempty member over a time dimension.</span></span>|  
|<span data-ttu-id="2abbe-133">**LastChild**</span><span class="sxs-lookup"><span data-stu-id="2abbe-133">**LastChild**</span></span>|<span data-ttu-id="2abbe-134">시간 차원에 대해 측정값의 마지막 자식 멤버를 반환하여 집계됩니다.</span><span class="sxs-lookup"><span data-stu-id="2abbe-134">Aggregated by returning the measure's last child member over a time dimension.</span></span>|  
|<span data-ttu-id="2abbe-135">**LastNonEmpty**</span><span class="sxs-lookup"><span data-stu-id="2abbe-135">**LastNonEmpty**</span></span>|<span data-ttu-id="2abbe-136">시간 차원에 대해 측정값의 마지막 비어 있지 않은 멤버를 반환하여 집계됩니다.</span><span class="sxs-lookup"><span data-stu-id="2abbe-136">Aggregated by returning the measure's last nonempty member over a time dimension.</span></span>|  
|`Max`|<span data-ttu-id="2abbe-137">`Max` 함수를 사용하여 집계됩니다.</span><span class="sxs-lookup"><span data-stu-id="2abbe-137">Aggregated using the `Max` function.</span></span>|  
|`Min`|<span data-ttu-id="2abbe-138">`Min` 함수를 사용하여 집계됩니다.</span><span class="sxs-lookup"><span data-stu-id="2abbe-138">Aggregated using the `Min` function.</span></span>|  
|<span data-ttu-id="2abbe-139">**없음**</span><span class="sxs-lookup"><span data-stu-id="2abbe-139">**None**</span></span>|<span data-ttu-id="2abbe-140">집계가 수행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2abbe-140">No aggregation performed.</span></span>|  
|`Sum`|<span data-ttu-id="2abbe-141">`Sum` 함수를 사용하여 집계됩니다.</span><span class="sxs-lookup"><span data-stu-id="2abbe-141">Aggregated using the `Sum` function.</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="2abbe-142"> 이 옵션에 대해 선택한 사항은 **개별 측정값에 대한 반가산적 동작 정의** 를 선택한 경우에만 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="2abbe-142">Selections made for this option apply only if **Define semiadditive behavior for individual members** is selected.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2abbe-143">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2abbe-143">See Also</span></span>  
 <span data-ttu-id="2abbe-144">[비즈니스 인텔리전스 마법사 F1 도움말](business-intelligence-wizard-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="2abbe-144">[Business Intelligence Wizard F1 Help](business-intelligence-wizard-f1-help.md) </span></span>  
 <span data-ttu-id="2abbe-145">[큐브 디자이너 &#40;Analysis Services 다차원 데이터&#41;](cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="2abbe-145">[Cube Designer &#40;Analysis Services - Multidimensional Data&#41;](cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="2abbe-146">차원 디자이너 &#40;Analysis Services 다차원 데이터&#41;</span><span class="sxs-lookup"><span data-stu-id="2abbe-146">Dimension Designer &#40;Analysis Services - Multidimensional Data&#41;</span></span>](dimension-designer-analysis-services-multidimensional-data.md)  
  
  
