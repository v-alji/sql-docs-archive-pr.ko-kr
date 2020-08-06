---
title: 차원에 사용자 지정 집계 추가 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- dimensions [Analysis Services], Business Intelligence enhancements
- Business Intelligence enhancements [Analysis Services], custom aggregations
- aggregations [Analysis Services], custom
- unary operators
- custom aggregations [Analysis Services]
ms.assetid: 3199a6c2-a06d-47b9-bd1c-604dbb085318
author: minewiskan
ms.author: owend
ms.openlocfilehash: ed843b8b0005ff62f05b13ebd20024d528857388
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646696"
---
# <a name="add-a-custom-aggregation-to-a-dimension"></a><span data-ttu-id="06a78-102">차원에 사용자 지정 집계 추가</span><span class="sxs-lookup"><span data-stu-id="06a78-102">Add a Custom Aggregation to a Dimension</span></span>
  <span data-ttu-id="06a78-103">큐브나 차원에 향상된 사용자 지정 집계 기능을 추가하여 차원 멤버와 연결되는 기본 집계를 다른 단항 연산자로 바꿀 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="06a78-103">Add a custom aggregation enhancement to a cube or dimension to replace the default aggregations that are associated with a dimension member with a different unary operator.</span></span> <span data-ttu-id="06a78-104">이 향상된 기능은 부모-자식 계층의 멤버에 대한 롤업을 정의하는 차원 테이블에 단항 연산자 열을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="06a78-104">This enhancement specifies a unary operator column in the dimension table that defines rollup for members in a parent-child hierarchy.</span></span> <span data-ttu-id="06a78-105">단항 연산자는 부모-자식 계층의 부모 특성에 대해 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="06a78-105">The unary operator acts on the parent attribute in a parent-child hierarchy.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="06a78-106">사용자 지정 집계는 기존 데이터 원본 기반의 차원에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="06a78-106">A custom aggregation is available only for dimensions that are based on existing data sources.</span></span> <span data-ttu-id="06a78-107">데이터 원본을 사용하지 않고 만든 차원의 경우 스키마 생성 마법사를 실행하여 사용자 지정 집계를 추가하기 전에 데이터 원본 뷰를 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="06a78-107">For dimensions that were created without using a data source, you must run the Schema Generation Wizard to create a data source view before adding the custom aggregation.</span></span>  
  
 <span data-ttu-id="06a78-108">사용자 지정 집계를 추가하기 전에 비즈니스 인텔리전스 마법사를 실행하여 **기능 선택** 페이지에서 **단항 연산자 지정** 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="06a78-108">To add a custom aggregation, you use the Business Intelligence Wizard, and select the **Specify a unary operator** option on the **Choose Enhancement** page.</span></span> <span data-ttu-id="06a78-109">그런 다음 마법사의 안내를 따라 사용자 지정 집계를 적용할 차원을 선택하고 사용자 지정 집계를 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="06a78-109">This wizard then guides you through the steps of selecting a dimension to which you want to apply a custom aggregation and identifying the custom aggregation.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="06a78-110">비즈니스 인텔리전스 마법사를 실행하여 사용자 지정 집계를 추가하기 전에 기능을 향상시킬 차원에 부모-자식 특성 계층이 있는지 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="06a78-110">Before you run the Business Intelligence Wizard to add a custom aggregation, make sure that the dimension that you want to enhance contains a parent-child attribute hierarchy.</span></span> <span data-ttu-id="06a78-111">자세한 내용은 [부모-자식 계층](parent-child-dimension.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="06a78-111">For more information, see [Parent-Child Hierarchy](parent-child-dimension.md).</span></span>  
  
## <a name="selecting-a-dimension"></a><span data-ttu-id="06a78-112">차원 선택</span><span class="sxs-lookup"><span data-stu-id="06a78-112">Selecting a Dimension</span></span>  
 <span data-ttu-id="06a78-113">마법사의 첫 번째 **단항 연산자 지정** 페이지에서 사용자 지정 집계를 적용할 차원을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="06a78-113">On the first **Specify a Unary Operator** page of the wizard, you specify the dimension to which you want to apply a custom aggregation.</span></span> <span data-ttu-id="06a78-114">이렇게 선택한 차원에 추가되는 사용자 지정 집계에 따라 차원이 변경됩니다.</span><span class="sxs-lookup"><span data-stu-id="06a78-114">The custom aggregation added to this selected dimension will result in changes to the dimension.</span></span> <span data-ttu-id="06a78-115">이러한 변경 내용은 선택된 차원을 포함하는 모든 큐브에 상속됩니다.</span><span class="sxs-lookup"><span data-stu-id="06a78-115">These changes will be inherited by all cubes that include the selected dimension.</span></span>  
  
## <a name="adding-custom-aggregation-unary-operator"></a><span data-ttu-id="06a78-116">사용자 지정 집계 추가(단항 연산자)</span><span class="sxs-lookup"><span data-stu-id="06a78-116">Adding Custom Aggregation (Unary Operator)</span></span>  
 <span data-ttu-id="06a78-117">두 번째 **단항 연산자 지정** 페이지에서 사용자 지정 집계에 대한 부모 특성과 단항 연산자에 대한 차원 테이블의 원본 열을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="06a78-117">On the second **Specify a Unary Operator** page, you specify the parent attribute that you want for the custom aggregation and the source column in the dimension table for the unary operator.</span></span> <span data-ttu-id="06a78-118">**부모 특성** 속성이로 설정 된 특성을 나열 `Usage` `Parent` 합니다.</span><span class="sxs-lookup"><span data-stu-id="06a78-118">**Parent attribute** lists attributes that have their `Usage` property set to `Parent`.</span></span> <span data-ttu-id="06a78-119">부모 특성이 여러 개 있는 경우 사용할 부모-자식 관계에 해당하는 부모 특성을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="06a78-119">If there is more than one parent attribute, choose the parent attribute that corresponds to the parent-child relationship that you want to use.</span></span> <span data-ttu-id="06a78-120">나열된 부모 특성이 없는 경우에는 차원에 유효한 부모-자식 계층이 없는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="06a78-120">If there is no parent attribute listed, then the dimension does not have a valid parent-child hierarchy.</span></span>  
  
 <span data-ttu-id="06a78-121">**원본 열**에서 단항 연산자가 있는 문자열 열을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="06a78-121">In **Source column**, you select the string column that contains the unary operators.</span></span> <span data-ttu-id="06a78-122">이 선택 항목은 `UnaryOperatorColumn` 부모 특성에 대 한 속성을 설정 합니다. 또한 차원 테이블에는 단항 rollup 연산자를 지정 하는 문자열 열이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="06a78-122">(This selection sets the `UnaryOperatorColumn` property on the parent attribute.) The dimension table should also have a string column that specifies the unary rollup operator.</span></span> <span data-ttu-id="06a78-123">이 열의 문자열 값에는 올바른 집계 연산자가 포함되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="06a78-123">The string values in this column should contain valid aggregation operators.</span></span> <span data-ttu-id="06a78-124">행이 비어 있으면 해당 멤버가 정상적으로 계산됩니다.</span><span class="sxs-lookup"><span data-stu-id="06a78-124">If a row is empty, the corresponding member is calculated normally.</span></span> <span data-ttu-id="06a78-125">열의 수식이 유효하지 않으면 멤버를 사용하는 셀 값이 검색될 때마다 런타임 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="06a78-125">If the formula in a column is not valid, a run-time error occurs when a cell value that uses the member is retrieved.</span></span> <span data-ttu-id="06a78-126">자세한 내용은 [부모-자식 차원의 단항 연산자](parent-child-dimension-attributes-unary-operators.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="06a78-126">For more information, see [Unary Operators in Parent-Child Dimensions](parent-child-dimension-attributes-unary-operators.md).</span></span>  
  
  
