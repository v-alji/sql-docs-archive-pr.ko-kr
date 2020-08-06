---
title: 차원 유형 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- time dimensions [Analysis Services]
- quantitative dimensions [Analysis Services]
- BillOfMaterials dimension [Analysis Services]
- geography dimensions
- utility dimensions [Analysis Services]
- channel dimensions
- dimensions [Analysis Services], types
- products dimensions [Analysis Services]
- account dimensions [Analysis Services]
- organization dimensions
- currency dimensions [Analysis Services]
- rates dimensions
- promotion dimensions
- scenario dimensions [Analysis Services]
- customers dimensions [Analysis Services]
- Type property
ms.assetid: bd3195da-e762-4c98-b643-34c76e842343
author: minewiskan
ms.author: owend
ms.openlocfilehash: 5e0c16a57081aa1d9ed3cc6964d1f17fa7135986
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661382"
---
# <a name="dimension-types"></a><span data-ttu-id="6d4dd-102">차원 유형</span><span class="sxs-lookup"><span data-stu-id="6d4dd-102">Dimension Types</span></span>
  <span data-ttu-id="6d4dd-103">`Type` 속성 설정은 서버 및 클라이언트 애플리케이션에 차원 내용에 대한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="6d4dd-103">The `Type` property setting provides information about the contents of a dimension to server and client applications.</span></span> <span data-ttu-id="6d4dd-104">일부 경우에 `Type` 설정은 클라이언트 애플리케이션에 대한 지침만 제공하며 선택적입니다.</span><span class="sxs-lookup"><span data-stu-id="6d4dd-104">In some cases, the `Type` setting only provides guidance for client applications and is optional.</span></span> <span data-ttu-id="6d4dd-105">`Accounts` 또는 `Time` 차원의 경우처럼 차원 및 해당 특성에 대한 `Type` 속성 설정에 따라 특정 서버 기반 동작이 결정되는 경우도 있고 큐브의 특정 동작을 구현하는 데 이러한 속성 설정이 필요할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6d4dd-105">In other cases, such as `Accounts` or `Time` dimensions, the `Type` property settings for the dimension and its attributes determine specific server-based behaviors and may be required to implement certain behaviors in the cube.</span></span> <span data-ttu-id="6d4dd-106">예를 들어 차원의 `Type` 속성을 `Accounts`로 설정하여 표준 차원에 계정 특성이 포함되어 있다는 것을 클라이언트 애플리케이션에 나타낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6d4dd-106">For example, the `Type` property of a dimension can be set to `Accounts` to indicate to client applications that the standard dimension contains account attributes.</span></span> <span data-ttu-id="6d4dd-107">시간, 계정 및 통화 차원에 대 한 자세한 내용은 [날짜 유형 차원 만들기](../multidimensional-models/database-dimensions-create-a-date-type-dimension.md), [부모-자식 유형 차원의 재무 계정 만들기](../multidimensional-models/database-dimensions-finance-account-of-parent-child-type.md)및 [통화 유형 차원 만들기](../multidimensional-models/database-dimensions-create-a-currency-type-dimension.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="6d4dd-107">For more information about time, account, and currency dimensions, see [Create a Date type Dimension](../multidimensional-models/database-dimensions-create-a-date-type-dimension.md), [Create a Finance Account of parent-child type Dimension](../multidimensional-models/database-dimensions-finance-account-of-parent-child-type.md), and [Create a Currency type Dimension](../multidimensional-models/database-dimensions-create-a-currency-type-dimension.md).</span></span>  
  
 <span data-ttu-id="6d4dd-108">차원 유형의 기본 설정은 차원 내용에 대해 어떠한 가정도 하지 않는 `Regular`입니다.</span><span class="sxs-lookup"><span data-stu-id="6d4dd-108">The default setting for the dimension type is `Regular`, which makes no assumptions about the contents of the dimension.</span></span> <span data-ttu-id="6d4dd-109">이 설정은 차원 마법사를 사용하여 차원을 정의할 때 `Time`을 지정하지 않은 한 차원을 처음 정의할 때 모든 차원에 대한 기본 설정이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6d4dd-109">This is the default setting for all dimensions when you initially define a dimension unless you specify `Time` when defining the dimension using the Dimension Wizard.</span></span> <span data-ttu-id="6d4dd-110">차원 마법사가 차원 유형에 대한 적절한 유형을 나열하지 않는 경우 `Regular`를 차원 유형으로 유지해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6d4dd-110">You should also leave `Regular` as the dimension type if the Dimension Wizard does not list an appropriate type for Dimension type.</span></span>  
  
## <a name="available-dimension-types"></a><span data-ttu-id="6d4dd-111">사용 가능한 차원 유형</span><span class="sxs-lookup"><span data-stu-id="6d4dd-111">Available Dimension Types</span></span>  
 <span data-ttu-id="6d4dd-112">다음 표에서는에서 사용할 수 있는 차원 유형을 설명 합니다 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="6d4dd-112">The following table describes the dimension types available in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span>  
  
|<span data-ttu-id="6d4dd-113">차원 유형</span><span class="sxs-lookup"><span data-stu-id="6d4dd-113">Dimension type</span></span>|<span data-ttu-id="6d4dd-114">Description</span><span class="sxs-lookup"><span data-stu-id="6d4dd-114">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="6d4dd-115">주기적</span><span class="sxs-lookup"><span data-stu-id="6d4dd-115">Regular</span></span>|<span data-ttu-id="6d4dd-116">해당 유형이 특별한 차원 유형으로 설정되지 않은 차원입니다.</span><span class="sxs-lookup"><span data-stu-id="6d4dd-116">A dimension whose type has not been set to a special dimension type.</span></span>|  
|<span data-ttu-id="6d4dd-117">Time</span><span class="sxs-lookup"><span data-stu-id="6d4dd-117">Time</span></span>|<span data-ttu-id="6d4dd-118">해당 특성이 연도, 반기, 분기, 월 및 일과 같은 기간을 나타내는 차원입니다.</span><span class="sxs-lookup"><span data-stu-id="6d4dd-118">A dimension whose attributes represent time periods, such as years, semesters, quarters, months, and days.</span></span>|  
|<span data-ttu-id="6d4dd-119">조직</span><span class="sxs-lookup"><span data-stu-id="6d4dd-119">Organization</span></span>|<span data-ttu-id="6d4dd-120">해당 특성이 직원이나 자회사와 같은 조직 정보를 나타내는 차원입니다.</span><span class="sxs-lookup"><span data-stu-id="6d4dd-120">A dimension whose attributes represent organizational information, such as employees or subsidiaries.</span></span>|  
|<span data-ttu-id="6d4dd-121">Geography</span><span class="sxs-lookup"><span data-stu-id="6d4dd-121">Geography</span></span>|<span data-ttu-id="6d4dd-122">해당 특성이 도시 또는 우편 번호와 같은 지리적 정보를 나타내는 차원입니다.</span><span class="sxs-lookup"><span data-stu-id="6d4dd-122">A dimension whose attributes represent geographic information, such as cities or postal codes.</span></span>|  
|<span data-ttu-id="6d4dd-123">제품 구성 정보</span><span class="sxs-lookup"><span data-stu-id="6d4dd-123">BillOfMaterials</span></span>|<span data-ttu-id="6d4dd-124">해당 특성이 제품의 부품 목록 같은 재고 또는 제조 정보를 나타내는 차원입니다.</span><span class="sxs-lookup"><span data-stu-id="6d4dd-124">A dimension whose attributes represent inventory or manufacturing information, such as parts lists for products.</span></span>|  
|<span data-ttu-id="6d4dd-125">계정</span><span class="sxs-lookup"><span data-stu-id="6d4dd-125">Accounts</span></span>|<span data-ttu-id="6d4dd-126">해당 특성이 재무 보고용 계정 차트를 나타내는 차원입니다.</span><span class="sxs-lookup"><span data-stu-id="6d4dd-126">A dimension whose attributes represent a chart of accounts for financial reporting purposes.</span></span>|  
|<span data-ttu-id="6d4dd-127">고객</span><span class="sxs-lookup"><span data-stu-id="6d4dd-127">Customers</span></span>|<span data-ttu-id="6d4dd-128">해당 특성이 고객 또는 연락처 정보를 나타내는 차원입니다.</span><span class="sxs-lookup"><span data-stu-id="6d4dd-128">A dimension whose attributes represent customer or contact information.</span></span>|  
|<span data-ttu-id="6d4dd-129">제품</span><span class="sxs-lookup"><span data-stu-id="6d4dd-129">Products</span></span>|<span data-ttu-id="6d4dd-130">해당 특성이 제품 정보를 나타내는 차원입니다.</span><span class="sxs-lookup"><span data-stu-id="6d4dd-130">A dimension whose attributes represent product information.</span></span>|  
|<span data-ttu-id="6d4dd-131">시나리오</span><span class="sxs-lookup"><span data-stu-id="6d4dd-131">Scenario</span></span>|<span data-ttu-id="6d4dd-132">해당 특성이 기획 또는 전략 분석 정보를 나타내는 차원입니다.</span><span class="sxs-lookup"><span data-stu-id="6d4dd-132">A dimension whose attributes represent planning or strategic analysis information.</span></span>|  
|<span data-ttu-id="6d4dd-133">정량</span><span class="sxs-lookup"><span data-stu-id="6d4dd-133">Quantitative</span></span>|<span data-ttu-id="6d4dd-134">해당 특성이 정량 정보를 나타내는 차원입니다.</span><span class="sxs-lookup"><span data-stu-id="6d4dd-134">A dimension whose attributes represent quantitative information.</span></span>|  
|<span data-ttu-id="6d4dd-135">유틸리티</span><span class="sxs-lookup"><span data-stu-id="6d4dd-135">Utility</span></span>|<span data-ttu-id="6d4dd-136">해당 특성이 기타 정보를 나타내는 차원입니다.</span><span class="sxs-lookup"><span data-stu-id="6d4dd-136">A dimension whose attributes represent miscellaneous information.</span></span>|  
|<span data-ttu-id="6d4dd-137">Currency</span><span class="sxs-lookup"><span data-stu-id="6d4dd-137">Currency</span></span>|<span data-ttu-id="6d4dd-138">이 차원 유형에는 통화 데이터 및 메타데이터가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="6d4dd-138">This type of dimension contains currency data and metadata.</span></span>|  
|<span data-ttu-id="6d4dd-139">요율</span><span class="sxs-lookup"><span data-stu-id="6d4dd-139">Rates</span></span>|<span data-ttu-id="6d4dd-140">해당 특성이 환율 정보를 나타내는 차원입니다.</span><span class="sxs-lookup"><span data-stu-id="6d4dd-140">A dimension whose attributes represent currency rate information.</span></span>|  
|<span data-ttu-id="6d4dd-141">채널</span><span class="sxs-lookup"><span data-stu-id="6d4dd-141">Channel</span></span>|<span data-ttu-id="6d4dd-142">해당 특성이 채널 정보를 나타내는 차원입니다.</span><span class="sxs-lookup"><span data-stu-id="6d4dd-142">A dimension whose attributes represent channel information.</span></span>|  
|<span data-ttu-id="6d4dd-143">홍보 행사</span><span class="sxs-lookup"><span data-stu-id="6d4dd-143">Promotion</span></span>|<span data-ttu-id="6d4dd-144">해당 특성이 마케팅 홍보 행사 정보를 나타내는 차원입니다.</span><span class="sxs-lookup"><span data-stu-id="6d4dd-144">A dimension whose attributes represent marketing promotion information.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6d4dd-145">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6d4dd-145">See Also</span></span>  
 <span data-ttu-id="6d4dd-146">[기존 테이블을 사용 하 여 차원 만들기](../multidimensional-models/create-a-dimension-by-using-an-existing-table.md) </span><span class="sxs-lookup"><span data-stu-id="6d4dd-146">[Create a Dimension by Using an Existing Table](../multidimensional-models/create-a-dimension-by-using-an-existing-table.md) </span></span>  
 [<span data-ttu-id="6d4dd-147">차원&#40;Analysis Services - 다차원 데이터&#41;</span><span class="sxs-lookup"><span data-stu-id="6d4dd-147">Dimensions &#40;Analysis Services - Multidimensional Data&#41;</span></span>](dimensions-analysis-services-multidimensional-data.md)  
  
  
