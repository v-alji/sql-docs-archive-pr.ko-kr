---
title: 통화 유형 차원 만들기 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- dimensions [Analysis Services], currency
- currency [Analysis Services]
- converting currency
- currency dimensions [Analysis Services]
ms.assetid: b1f037d1-ce47-4e47-a1c2-5ec9e781cff6
author: minewiskan
ms.author: owend
ms.openlocfilehash: 91123fb5fda898e90056057114295335fbd1d32c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730996"
---
# <a name="create-a-currency-type-dimension"></a><span data-ttu-id="8f131-102">통화 유형 차원 만들기</span><span class="sxs-lookup"><span data-stu-id="8f131-102">Create a Currency type Dimension</span></span>
  <span data-ttu-id="8f131-103">에서 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 통화 유형 차원은 재무 보고용 통화 목록을 나타내는 특성이 있는 차원입니다.</span><span class="sxs-lookup"><span data-stu-id="8f131-103">In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], a currency type dimension is a dimension whose attributes represent a list of currencies for financial reporting purposes.</span></span>  
  
 <span data-ttu-id="8f131-104">통화 차원을 사용하면 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]에서 통화 변환 기능을 큐브에 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8f131-104">A currency dimension lets you add currency conversion capabilities to a cube in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="8f131-105">통화 변환 기능을 큐브에 추가하려면 비즈니스 인텔리전스 마법사를 사용하여 통화 측정값을 클라이언트 애플리케이션의 로캘에 알맞은 값으로 변환하는 MDX(Multidimensional Expressions) 스크립트 명령을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="8f131-105">To add currency conversion to a cube, you use the Business Intelligence Wizard define a Multidimensional Expressions (MDX) script command that converts currency measures to values that are appropriate for the locale of the client application.</span></span> <span data-ttu-id="8f131-106">이 MDX 스크립트를 만들려면 비즈니스 인텔리전스 마법사에 다음 정보가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="8f131-106">To create this MDX script, the Business Intelligence Wizard needs the following information:</span></span>  
  
-   <span data-ttu-id="8f131-107">원본 통화를 나타내는 통화 차원.</span><span class="sxs-lookup"><span data-stu-id="8f131-107">A currency dimension that represents source currencies.</span></span> <span data-ttu-id="8f131-108">이 차원은 원본 통화 차원입니다.</span><span class="sxs-lookup"><span data-stu-id="8f131-108">(This dimension is the source currency dimension.)</span></span>  
  
-   <span data-ttu-id="8f131-109">사용할 환율을 나타내는 측정값 그룹</span><span class="sxs-lookup"><span data-stu-id="8f131-109">A measure group that represents the exchange rates that will be used.</span></span>  
  
 <span data-ttu-id="8f131-110">비즈니스 인텔리전스 마법사는 이 정보를 사용하여 대상 통화를 나타내는 통화 차원인 적합한 대상 통화 차원을 식별하는 통화 변환 프로세스를 디자인합니다.</span><span class="sxs-lookup"><span data-stu-id="8f131-110">From this information, the Business Intelligence Wizard will design a currency conversion process that identifies the appropriate destination currency dimension (the currency dimension that represents destination currencies).</span></span> <span data-ttu-id="8f131-111">비즈니스 인텔리전스 마법사는 비즈니스 인텔리전스 솔루션에 필요한 통화 변환 수에 따라 여러 대상 통화 차원을 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8f131-111">Depending on the number of currency conversions that your business intelligence solution requires, the Business Intelligence Wizard can define multiple destination currency dimensions.</span></span> <span data-ttu-id="8f131-112">통화 환산을 정의하는 방법은 [통화 환산&#40;Analysis Services&#41;](../currency-conversions-analysis-services.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8f131-112">For more information about defining currency conversions, see [Currency Conversions &#40;Analysis Services&#41;](../currency-conversions-analysis-services.md).</span></span>  
  
 <span data-ttu-id="8f131-113">차원을 통화 차원으로 식별하려면 차원의 `Type` 속성을 `Currency`로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="8f131-113">To identify a dimension as a currency dimension, set the `Type` property of the dimension to `Currency`.</span></span>  
  
## <a name="dimension-structure"></a><span data-ttu-id="8f131-114">차원 구조</span><span class="sxs-lookup"><span data-stu-id="8f131-114">Dimension Structure</span></span>  
 <span data-ttu-id="8f131-115">통화 차원에는 통화 차원의 차원 테이블에 있는 개별 통화를 식별하는 키 특성이 기본적으로 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8f131-115">A currency dimension contains, at least, a key attribute identifying individual currencies in the dimension table for the currency dimension.</span></span> <span data-ttu-id="8f131-116">키 특성의 값은 원본 통화 차원 및 대상 통화 차원에 따라 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="8f131-116">The value of the key attribute is different in both source and destination currency dimensions:</span></span>  
  
-   <span data-ttu-id="8f131-117">특성을 원본 통화 차원의 키 특성으로 식별하려면 특성의 `Type` 속성을 `CurrencySource`로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="8f131-117">To identify an attribute as the key attribute of a source currency dimension, set the `Type` property of the attribute to `CurrencySource`.</span></span>  
  
-   <span data-ttu-id="8f131-118">특성을 대상 통화 차원으로 식별하려면 특성의 `Type` 속성을 `CurrencyDestination`으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="8f131-118">To identify an attribute as the destination currency dimension, set the `Type` property of the attribute to `CurrencyDestination`.</span></span>  
  
 <span data-ttu-id="8f131-119">보고를 위해 필요한 경우 원본 통화 차원과 대상 통화 차원 모두에 다음 특성이 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8f131-119">For reporting purposes, both source and destination currency dimensions can optionally contain the following attributes:</span></span>  
  
-   <span data-ttu-id="8f131-120">통화 이름 특성</span><span class="sxs-lookup"><span data-stu-id="8f131-120">A currency name attribute.</span></span>  
  
     <span data-ttu-id="8f131-121">특성을 통화 이름 특성으로 식별하려면 특성의 `Type` 속성을 `CurrencyName`으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="8f131-121">To identify an attribute as a currency name attribute, set the `Type` property of the attribute to `CurrencyName`.</span></span>  
  
-   <span data-ttu-id="8f131-122">통화 원본 특성</span><span class="sxs-lookup"><span data-stu-id="8f131-122">A currency source attribute.</span></span>  
  
     <span data-ttu-id="8f131-123">특성을 통화 원본 특성으로 식별하려면 특성의 `Type` 속성을 `CurrencySource`로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="8f131-123">To identify an attribute as a currency source attribute, set the `Type` property of the attribute to `CurrencySource`.</span></span>  
  
-   <span data-ttu-id="8f131-124">통화 ISO(International Standards Organization) 코드</span><span class="sxs-lookup"><span data-stu-id="8f131-124">A currency International Standards Organization (ISO) code.</span></span>  
  
     <span data-ttu-id="8f131-125">특성을 통화 ISO 코드 특성으로 식별하려면 특성의 `Type` 속성을 `CurrencyIsoCode`로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="8f131-125">To identify an attribute as a currency ISO code attribute, set the `Type` property of the attribute to `CurrencyIsoCode`.</span></span>  
  
 <span data-ttu-id="8f131-126">특성 유형에 대한 자세한 내용은 [특성 유형 구성](attribute-properties-configure-attribute-types.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8f131-126">For more information about attribute types, see [Configure Attribute Types](attribute-properties-configure-attribute-types.md).</span></span>  
  
## <a name="defining-account-intelligence-with-the-business-intelligence-wizard"></a><span data-ttu-id="8f131-127">비즈니스 인텔리전스 마법사를 사용하여 계정 인텔리전스 정의</span><span class="sxs-lookup"><span data-stu-id="8f131-127">Defining Account Intelligence with the Business Intelligence Wizard</span></span>  
 <span data-ttu-id="8f131-128">계정 차원을 정의하여 큐브에 추가한 후에는 비즈니스 인텔리전스 마법사를 사용하여 계정 유형 식별 및 매핑과 같은 계정 인텔리전스 기능을 차원에 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8f131-128">After you have defined an account dimension and added that dimension to a cube, you can use the Business Intelligence Wizard to add account intelligence functionality, such as identifying and mapping account types, to the dimension.</span></span> <span data-ttu-id="8f131-129">자세한 내용은 [차원에 계정 인텔리전스 추가](bi-wizard-add-account-intelligence-to-a-dimension.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8f131-129">For more information, see [Add Account Intelligence to a Dimension](bi-wizard-add-account-intelligence-to-a-dimension.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f131-130">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8f131-130">See Also</span></span>  
 <span data-ttu-id="8f131-131">[특성 및 특성 계층](../multidimensional-models-olap-logical-dimension-objects/attributes-and-attribute-hierarchies.md) </span><span class="sxs-lookup"><span data-stu-id="8f131-131">[Attributes and Attribute Hierarchies](../multidimensional-models-olap-logical-dimension-objects/attributes-and-attribute-hierarchies.md) </span></span>  
 <span data-ttu-id="8f131-132">[비즈니스 인텔리전스 마법사 F1 도움말](../business-intelligence-wizard-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="8f131-132">[Business Intelligence Wizard F1 Help](../business-intelligence-wizard-f1-help.md) </span></span>  
 [<span data-ttu-id="8f131-133">차원 유형</span><span class="sxs-lookup"><span data-stu-id="8f131-133">Dimension Types</span></span>](../multidimensional-models-olap-logical-dimension-objects/database-dimension-properties-types.md)  
  
  
