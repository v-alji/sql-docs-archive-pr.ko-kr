---
title: 통화 변환 (Analysis Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- multiple currency conversions
- monetary data [SQL Server]
- currency [Analysis Services]
- converting currency
- one-to-many currency conversions
- many-to-many currency conversions [Analysis Services]
- many-to-one currency conversions [Analysis Services]
ms.assetid: e03f491c-7df8-46a0-ade9-f2e55b68db85
author: minewiskan
ms.author: owend
ms.openlocfilehash: b4fee100dea2b3aff99516175bf688337a33592e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659751"
---
# <a name="currency-conversions-analysis-services"></a><span data-ttu-id="e0ac9-102">통화 변환(Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="e0ac9-102">Currency Conversions (Analysis Services)</span></span>
  <span data-ttu-id="e0ac9-103">**[!INCLUDE[applies](../includes/applies-md.md)]** 다차원 전용</span><span class="sxs-lookup"><span data-stu-id="e0ac9-103">**[!INCLUDE[applies](../includes/applies-md.md)]**  Multidimensional only</span></span>  
  
 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] <span data-ttu-id="e0ac9-104">에서는 MDX(Multidimensional Expressions) 스크립트에서 지정하는 여러 기능을 사용하여 다중 통화를 지원하는 큐브에 통화 환산 지원을 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0ac9-104">uses a combination of features, guided by Multidimensional Expressions (MDX) scripts, to provide currency conversion support in cubes supporting multiple currencies.</span></span>  
  
## <a name="currency-conversion-terminology"></a><span data-ttu-id="e0ac9-105">통화 변환 용어</span><span class="sxs-lookup"><span data-stu-id="e0ac9-105">Currency Conversion Terminology</span></span>  
 <span data-ttu-id="e0ac9-106">다음은 통화 변환 기능을 설명하기 위해 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 에 사용되는 용어입니다.</span><span class="sxs-lookup"><span data-stu-id="e0ac9-106">The following terminology is used in [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] to describe currency conversion functionality:</span></span>  
  
 <span data-ttu-id="e0ac9-107">피벗 통화</span><span class="sxs-lookup"><span data-stu-id="e0ac9-107">Pivot currency</span></span>  
 <span data-ttu-id="e0ac9-108">환율이 요율 측정값 그룹에 입력되는 통화입니다.</span><span class="sxs-lookup"><span data-stu-id="e0ac9-108">The currency against which exchange rates are entered in the rate measure group.</span></span>  
  
 <span data-ttu-id="e0ac9-109">현지 통화</span><span class="sxs-lookup"><span data-stu-id="e0ac9-109">Local currency</span></span>  
 <span data-ttu-id="e0ac9-110">변환할 측정값이 기반으로 하는 트랜잭션을 저장하는 데 사용되는 통화입니다.</span><span class="sxs-lookup"><span data-stu-id="e0ac9-110">The currency used to store transactions on which measures to be converted are based.</span></span>  
  
 <span data-ttu-id="e0ac9-111">현지 통화는 다음 중 하나로 식별할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0ac9-111">The local currency can be identified by either:</span></span>  
  
-   <span data-ttu-id="e0ac9-112">트랜잭션과 함께 저장된 팩트 테이블의 통화 식별자 - 트랜잭션 자체가 해당 트랜잭션에 사용되는 통화를 식별하는 은행 애플리케이션에 일반적으로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="e0ac9-112">A currency identifier in the fact table stored with the transaction, as is commonly the case with banking applications where the transaction itself identifies the currency used for that transaction.</span></span>  
  
-   <span data-ttu-id="e0ac9-113">차원 테이블의 특성에 연결된 다음 팩트 테이블의 트랜잭션에 연결되는 통화 식별자 - 위치나 다른 식별자(자회사 등)가 연결된 트랜잭션에 사용되는 통화를 식별하는 재무 애플리케이션에 일반적으로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="e0ac9-113">A currency identifier associated with an attribute in a dimension table that is then associated with a transaction in the fact table, as is commonly the case in financial applications where a location or other identifier, such as a subsidiary, identifies the currency used for an associated transaction.</span></span>  
  
 <span data-ttu-id="e0ac9-114">보고 통화</span><span class="sxs-lookup"><span data-stu-id="e0ac9-114">Reporting currency</span></span>  
 <span data-ttu-id="e0ac9-115">트랜잭션이 피벗 통화에서 변환되는 통화입니다.</span><span class="sxs-lookup"><span data-stu-id="e0ac9-115">The currency to which transactions are converted from the pivot currency.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e0ac9-116">다 대 일 통화 변환의 경우 피벗 통화와 보고 통화가 같습니다.</span><span class="sxs-lookup"><span data-stu-id="e0ac9-116">For many-to-one currency conversions, the pivot currency and reporting currency are the same.</span></span>  
  
 <span data-ttu-id="e0ac9-117">통화 차원</span><span class="sxs-lookup"><span data-stu-id="e0ac9-117">Currency dimension</span></span>  
 <span data-ttu-id="e0ac9-118">다음 설정으로 정의된 데이터베이스 차원입니다.</span><span class="sxs-lookup"><span data-stu-id="e0ac9-118">A database dimension defined with the following settings:</span></span>  
  
-   <span data-ttu-id="e0ac9-119"> 차원의 `Type` 속성을 Currency로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="e0ac9-119">The `Type` property of the dimension is set to Currency.</span></span>  
  
-   <span data-ttu-id="e0ac9-120"> 차원의 한 특성에 대한 `Type` 속성을 CurrencyName으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="e0ac9-120">The `Type` property of one attribute for the dimension is set to CurrencyName.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="e0ac9-121">이 특성 값은 통화 식별자를 포함해야 하는 모든 열에 사용되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0ac9-121">The values of this attribute must be used in all columns that should contain a currency identifier.</span></span>  
  
 <span data-ttu-id="e0ac9-122">요율 측정값 그룹</span><span class="sxs-lookup"><span data-stu-id="e0ac9-122">Rate measure group</span></span>  
 <span data-ttu-id="e0ac9-123">다음 설정으로 정의된 큐브의 측정값 그룹입니다.</span><span class="sxs-lookup"><span data-stu-id="e0ac9-123">A measure group in a cube, defined with the following settings:</span></span>  
  
-   <span data-ttu-id="e0ac9-124">통화 차원과 요율 측정값 그룹 사이에 일반 차원 관계가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0ac9-124">A regular dimension relationship exists between a currency dimension and the rate measure group.</span></span>  
  
-   <span data-ttu-id="e0ac9-125">시간 차원과 요율 측정값 그룹 사이에 일반 차원 관계가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0ac9-125">A regular dimension relationship exists between a time dimension and the rate measure group.</span></span>  
  
-   <span data-ttu-id="e0ac9-126"> 필요에 따라 `Type` 속성을 ExchangeRate로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="e0ac9-126">Optionally, the `Type` property is set to ExchangeRate.</span></span> <span data-ttu-id="e0ac9-127"> 비즈니스 인텔리전스 마법사는 통화 차원과 시간 차원 간의 관계를 사용하여 가능성이 있는 요율 측정값 그룹을 식별하므로 `Type` 속성을 ExchangeRate로 설정하면 클라이언트 애플리케이션에서 요율 측정값 그룹을 보다 쉽게 식별할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0ac9-127">While the Business Intelligence Wizard uses the relationships with the currency and time dimensions to identify likely rate measure groups, setting the `Type` property to ExchangeRate allows client applications to more easily identify rate measure groups.</span></span>  
  
-   <span data-ttu-id="e0ac9-128">요율 측정값 그룹에 포함된 환율을 나타내는 하나 이상의 측정값입니다.</span><span class="sxs-lookup"><span data-stu-id="e0ac9-128">One or more measures, representing the exchange rates contained by the rate measure group.</span></span>  
  
 <span data-ttu-id="e0ac9-129">보고 통화 차원</span><span class="sxs-lookup"><span data-stu-id="e0ac9-129">Reporting currency dimension</span></span>  
 <span data-ttu-id="e0ac9-130">통화 변환을 정의한 다음 비즈니스 인텔리전스 마법사에서 정의한 차원이며 해당 통화 변환에 대한 보고 통화를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="e0ac9-130">The dimension, defined by the Business Intelligence Wizard after a currency conversion is defined, that contains the reporting currencies for that currency conversion.</span></span> <span data-ttu-id="e0ac9-131">보고 통화 차원은 통화 차원의 주 차원 테이블에서 명명된 쿼리를 기반으로 합니다. 이 쿼리는 요율 측정값 그룹과 연결된 통화 차원이 기반으로 하는 데이터 원본 뷰에 정의되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0ac9-131">The reporting currency dimension is based on a named query, defined in the data source view on which the currency dimension associated with the rate measure group is based, from the dimension main table of the currency dimension.</span></span> <span data-ttu-id="e0ac9-132">다음 설정으로 보고 통화 차원이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="e0ac9-132">The dimension is defined with the following settings:</span></span>  
  
-   <span data-ttu-id="e0ac9-133"> 차원의 `Type` 속성을 Currency로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="e0ac9-133">The `Type` property of the dimension is set to Currency.</span></span>  
  
-   <span data-ttu-id="e0ac9-134"> 차원의 키 특성에 대한 `Type` 속성을 CurrencyName으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="e0ac9-134">The `Type` property of the key attribute for the dimension is set to CurrencyName.</span></span>  
  
-   <span data-ttu-id="e0ac9-135"> 차원 내의 한 특성에 대한 `Type` 속성을 CurrencyDestination으로 설정하고 해당 특성에 바인딩된 열에 통화 변환에 대한 보고 통화를 나타내는 통화 식별자를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="e0ac9-135">The `Type` property of one attribute within the dimension is set to CurrencyDestination, and the column bound to the attribute contains the currency identifiers that represent the reporting currencies for the currency conversion.</span></span>  
  
## <a name="defining-currency-conversions"></a><span data-ttu-id="e0ac9-136">통화 변환 정의</span><span class="sxs-lookup"><span data-stu-id="e0ac9-136">Defining Currency Conversions</span></span>  
 <span data-ttu-id="e0ac9-137">비즈니스 인텔리전스 마법사를 사용하여 큐브에 대한 통화 변환 기능을 정의하거나 MDX 스크립트를 사용하여 수동으로 통화 변환을 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0ac9-137">You can use the Business Intelligence Wizard to define currency conversion functionality for a cube, or you can manually define currency conversions using MDX scripts.</span></span>  
  
### <a name="prerequisites"></a><span data-ttu-id="e0ac9-138">사전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="e0ac9-138">Prerequisites</span></span>  
 <span data-ttu-id="e0ac9-139">비즈니스 인텔리전스 마법사를 사용하여 큐브에 통화 변환을 정의하려면 먼저 하나 이상의 통화 차원, 하나 이상의 시간 차원 및 하나 이상의 요율 측정값 그룹을 정의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0ac9-139">Before you can define a currency conversion in a cube using the Business Intelligence Wizard, you must first define at least one currency dimension, at least one time dimension, and at least one rate measure group.</span></span> <span data-ttu-id="e0ac9-140">비즈니스 인텔리전스 마법사는 통화 변환 기능 제공에 필요한 보고 통화 차원 및 MDX 스크립트를 생성하는 데 사용되는 데이터 및 메타데이터를 이러한 개체에서 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0ac9-140">From these objects, the Business Intelligence Wizard can retrieve the data and metadata used to construct the reporting currency dimension and MDX script needed to provide currency conversion functionality.</span></span>  
  
### <a name="decisions"></a><span data-ttu-id="e0ac9-141">의사 결정</span><span class="sxs-lookup"><span data-stu-id="e0ac9-141">Decisions</span></span>  
 <span data-ttu-id="e0ac9-142">비즈니스 인텔리전스 마법사에서 통화 변환 기능 제공에 필요한 보고 통화 차원 및 MDX 스크립트를 생성하려면 먼저 다음 사항을 결정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0ac9-142">You need to make the following decisions before the Business Intelligence Wizard can construct the reporting currency dimension and MDX script needed to provide currency conversion functionality:</span></span>  
  
-   <span data-ttu-id="e0ac9-143">환율 방향</span><span class="sxs-lookup"><span data-stu-id="e0ac9-143">Exchange rate direction</span></span>  
  
-   <span data-ttu-id="e0ac9-144">변환된 멤버</span><span class="sxs-lookup"><span data-stu-id="e0ac9-144">Converted members</span></span>  
  
-   <span data-ttu-id="e0ac9-145">변환 유형</span><span class="sxs-lookup"><span data-stu-id="e0ac9-145">Conversion type</span></span>  
  
-   <span data-ttu-id="e0ac9-146">현지 통화</span><span class="sxs-lookup"><span data-stu-id="e0ac9-146">Local currencies</span></span>  
  
-   <span data-ttu-id="e0ac9-147">보고 통화</span><span class="sxs-lookup"><span data-stu-id="e0ac9-147">Reporting currencies</span></span>  
  
### <a name="exchange-rate-directions"></a><span data-ttu-id="e0ac9-148">환율 방향</span><span class="sxs-lookup"><span data-stu-id="e0ac9-148">Exchange Rate Directions</span></span>  
 <span data-ttu-id="e0ac9-149">요율 측정값 그룹은 현지 통화와 피벗 통화(통합 통화) 사이의 환율을 나타내는 측정값을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="e0ac9-149">The rate measure group contains measures representing exchange rates between local currencies and the pivot currency (commonly referred to as the corporate currency).</span></span> <span data-ttu-id="e0ac9-150">환율 방향과 변환 유형을 조합하여 비즈니스 인텔리전스 마법사에서 생성한 MDX 스크립트로 변환할 측정값에서 수행되는 작업이 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="e0ac9-150">The combination of exchange rate direction and conversion type determines the operation performed on measures to be converted by the MDX script generated using the Business Intelligence Wizard.</span></span> <span data-ttu-id="e0ac9-151">다음 표에서는 비즈니스 인텔리전스 마법사에서 사용 가능한 환율 방향 옵션 및 변환 방향을 기반으로 환율 방향 및 변환 유형에 따라 수행되는 작업을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="e0ac9-151">The following table describes the operations performed depending on the exchange rate direction and conversion type, based on the exchange rate direction options and conversion directions available in the Business Intelligence Wizard.</span></span>  
  
|||||  
|-|-|-|-|  
|<span data-ttu-id="e0ac9-152">환율 방향</span><span class="sxs-lookup"><span data-stu-id="e0ac9-152">Exchange rate direction</span></span>|<span data-ttu-id="e0ac9-153">**다 대 일**</span><span class="sxs-lookup"><span data-stu-id="e0ac9-153">**Many-to-one**</span></span>|<span data-ttu-id="e0ac9-154">**일 대 다**</span><span class="sxs-lookup"><span data-stu-id="e0ac9-154">**One-to-many**</span></span>|<span data-ttu-id="e0ac9-155">**다 대 다**</span><span class="sxs-lookup"><span data-stu-id="e0ac9-155">**Many-to-many**</span></span>|  
|<span data-ttu-id="e0ac9-156">**1 샘플 통화당 n 피벗 통화**</span><span class="sxs-lookup"><span data-stu-id="e0ac9-156">**n pivot currency to 1 sample currency**</span></span>|<span data-ttu-id="e0ac9-157">측정값을 피벗 통화로 변환하기 위해 변환할 측정값에 현지 통화에 대한 환율 측정값을 곱합니다.</span><span class="sxs-lookup"><span data-stu-id="e0ac9-157">Multiply the measure to be converted by the exchange rate measure for the local currency in order to convert the measure into the pivot currency.</span></span>|<span data-ttu-id="e0ac9-158">측정값을 보고 통화로 변환하기 위해 변환할 측정값을 보고 통화에 대한 환율 측정값으로 나눕니다.</span><span class="sxs-lookup"><span data-stu-id="e0ac9-158">Divide the measure to be converted by the exchange rate measure for the reporting currency in order to convert the measure into the reporting currency.</span></span>|<span data-ttu-id="e0ac9-159">측정값을 피벗 통화로 변환하기 위해 변환할 측정값에 현지 통화에 대한 환율 측정값을 곱한 다음 측정값을 보고 통화로 변환하기 위해 변환된 측정값을 보고 통화에 대한 환율 측정값으로 나눕니다.</span><span class="sxs-lookup"><span data-stu-id="e0ac9-159">Multiply the measure to be converted by the exchange rate measure for the local currency in order to convert the measure into the pivot currency, then divide the converted measure by the exchange rate measure for the reporting currency in order to convert the measure into the reporting currency.</span></span>|  
|<span data-ttu-id="e0ac9-160">**1 피벗 통화당 n 샘플 통화**</span><span class="sxs-lookup"><span data-stu-id="e0ac9-160">**n sample currency to 1 pivot currency**</span></span>|<span data-ttu-id="e0ac9-161">측정값을 피벗 통화로 변환하기 위해 변환할 측정값을 현지 통화에 대한 환율 측정값으로 나눕니다.</span><span class="sxs-lookup"><span data-stu-id="e0ac9-161">Divide the measure to be converted by the exchange rate measure for the local currency in order to convert the measure into the pivot currency.</span></span>|<span data-ttu-id="e0ac9-162">측정값을 보고 통화로 변환하기 위해 변환할 측정값에 보고 통화에 대한 환율 측정값을 곱합니다.</span><span class="sxs-lookup"><span data-stu-id="e0ac9-162">Multiply the measure to be converted by the exchange rate measure for the reporting currency in order to convert the measure into the reporting currency.</span></span>|<span data-ttu-id="e0ac9-163">측정값을 피벗 통화로 변환하기 위해 변환할 측정값을 현지 통화에 대한 환율 측정값으로 나눈 다음 측정값을 보고 통화로 변환하기 위해 변환된 측정값에 보고 통화에 대한 환율 측정값을 곱합니다.</span><span class="sxs-lookup"><span data-stu-id="e0ac9-163">Divide the measure to be converted by the exchange rate measure for the local currency in order to convert the measure into the pivot currency, then multiply the converted measure by the exchange rate measure for the reporting currency in order to convert the measure into the reporting currency.</span></span>|  
  
 <span data-ttu-id="e0ac9-164">비즈니스 인텔리전스 마법사의 **통화 변환 옵션 설정** 페이지에서 환율 방향을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e0ac9-164">You choose the exchange rate direction on the **Set currency conversion options** page of the Business Intelligence Wizard.</span></span> <span data-ttu-id="e0ac9-165">변환 방향 설정에 대한 자세한 내용은 [통화 환산 옵션 설정&#40;비즈니스 인텔리전스 마법사&#41;](set-currency-conversion-options-business-intelligence-wizard.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e0ac9-165">For more information about setting conversion direction, see [Set Currency Conversion Options &#40;Business Intelligence Wizard&#41;](set-currency-conversion-options-business-intelligence-wizard.md).</span></span>  
  
### <a name="converted-members"></a><span data-ttu-id="e0ac9-166">변환된 멤버</span><span class="sxs-lookup"><span data-stu-id="e0ac9-166">Converted Members</span></span>  
 <span data-ttu-id="e0ac9-167">비즈니스 인텔리전스 마법사를 사용하여 다음에 대한 값을 변환하는 데 사용할 요율 측정값 그룹의 측정값을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0ac9-167">You can use the Business Intelligence Wizard to specify which measures from the rate measure group are used to convert values for:</span></span>  
  
-   <span data-ttu-id="e0ac9-168">다른 측정값 그룹의 측정값</span><span class="sxs-lookup"><span data-stu-id="e0ac9-168">Measures in other measure groups.</span></span>  
  
-   <span data-ttu-id="e0ac9-169">데이터베이스 차원의 계정 특성에 대한 특성 계층의 멤버</span><span class="sxs-lookup"><span data-stu-id="e0ac9-169">Members of an attribute hierarchy for an account attribute in a database dimension.</span></span>  
  
-   <span data-ttu-id="e0ac9-170">데이터베이스 차원의 계정 특성에 대한 특성 계층의 멤버에 사용되는 계정 유형</span><span class="sxs-lookup"><span data-stu-id="e0ac9-170">Account types, used by members of an attribute hierarchy for an account attribute in a database dimension.</span></span>  
  
 <span data-ttu-id="e0ac9-171">비즈니스 인텔리전스 마법사는 마법사에서 생성한 MDX 스크립트 내에서 이 정보를 사용하여 통화 변환 계산의 범위를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="e0ac9-171">The Business Intelligence Wizard uses this information within the MDX script generated by the wizard to determine the scope of the currency conversion calculation.</span></span> <span data-ttu-id="e0ac9-172">통화 환산에 대한 멤버 지정 방법은 [멤버 선택&#40;비즈니스 인텔리전스 마법사&#41;](select-members-business-intelligence-wizard.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e0ac9-172">For more information about specifying members for currency conversion, see [Select Members &#40;Business Intelligence Wizard&#41;](select-members-business-intelligence-wizard.md).</span></span>  
  
### <a name="conversion-types"></a><span data-ttu-id="e0ac9-173">변환 유형</span><span class="sxs-lookup"><span data-stu-id="e0ac9-173">Conversion Types</span></span>  
 <span data-ttu-id="e0ac9-174">비즈니스 인텔리전스 마법사에서는 다음과 같은 3가지 유형의 통화 변환을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0ac9-174">The Business Intelligence Wizard supports three different types of currency conversion:</span></span>  
  
-   <span data-ttu-id="e0ac9-175">**일 대 다**</span><span class="sxs-lookup"><span data-stu-id="e0ac9-175">**One-to-many**</span></span>  
  
     <span data-ttu-id="e0ac9-176">트랜잭션이 팩트 테이블에 피벗 통화로 저장된 다음 하나 이상의 다른 보고 통화로 변환됩니다.</span><span class="sxs-lookup"><span data-stu-id="e0ac9-176">Transactions are stored in the fact table in the pivot currency, and then converted to one or more other reporting currencies.</span></span>  
  
     <span data-ttu-id="e0ac9-177">예를 들어 피벗 통화를 미국 달러(USD)로 설정하면 팩트 테이블에서는 트랜잭션을 USD로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="e0ac9-177">For example, the pivot currency can be set to United States dollars (USD), and the fact table stores transactions in USD.</span></span> <span data-ttu-id="e0ac9-178">이 변환 유형은 이러한 트랜잭션을 피벗 통화에서 지정한 보고 통화로 변환합니다.</span><span class="sxs-lookup"><span data-stu-id="e0ac9-178">This conversion type converts these transactions from the pivot currency to the specified reporting currencies.</span></span> <span data-ttu-id="e0ac9-179">그 결과 트랜잭션을 지정한 피벗 통화로 저장한 다음 지정한 피벗 통화 또는 해당 통화 변환에 대해 정의한 보고 통화 차원에 지정된 임의의 보고 통화로 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0ac9-179">The result is that transactions can be stored in the specified pivot currency and viewed either in the specified pivot currency or in any of the reporting currencies specified in the reporting currency dimension defined for the currency conversion.</span></span>  
  
-   <span data-ttu-id="e0ac9-180">**다 대 일**</span><span class="sxs-lookup"><span data-stu-id="e0ac9-180">**Many-to-one**</span></span>  
  
     <span data-ttu-id="e0ac9-181">트랜잭션이 팩트 테이블에 현지 통화로 저장된 다음 피벗 통화로 변환됩니다.</span><span class="sxs-lookup"><span data-stu-id="e0ac9-181">Transactions are stored in the fact table in local currencies, and then converted into the pivot currency.</span></span> <span data-ttu-id="e0ac9-182">피벗 통화는 보고 통화 차원에서 지정된 유일한 보고 통화의 역할을 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0ac9-182">The pivot currency serves as the only specified reporting currency in the reporting currency dimension.</span></span>  
  
     <span data-ttu-id="e0ac9-183">예를 들어 피벗 통화를 미국 달러(USD)로 설정하면 팩트 테이블에서는 트랜잭션을 유로(EUR), 오스트레일리아 달러(AUD) 및 멕시코 페소(MXN)로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="e0ac9-183">For example, the pivot currency can be set to United States dollars (USD), and the fact table stores transactions in euros (EUR), Australian dollars (AUD), and Mexican pesos (MXN).</span></span> <span data-ttu-id="e0ac9-184">이 변환 유형은 이러한 트랜잭션을 지정한 현지 통화에서 피벗 통화로 변환합니다.</span><span class="sxs-lookup"><span data-stu-id="e0ac9-184">This conversion type converts these transactions from their specified local currencies to the pivot currency.</span></span> <span data-ttu-id="e0ac9-185">그 결과 트랜잭션을 지정한 현지 통화로 저장한 다음 해당 통화 변환에 대해 정의한 보고 통화 차원에 지정된 피벗 통화로 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0ac9-185">The result is that transactions can be stored in the specified local currencies and viewed in the pivot currency, which is specified in the reporting currency dimension defined for the currency conversion.</span></span>  
  
-   <span data-ttu-id="e0ac9-186">**다 대 다**</span><span class="sxs-lookup"><span data-stu-id="e0ac9-186">**Many-to-many**</span></span>  
  
     <span data-ttu-id="e0ac9-187">트랜잭션이 팩트 테이블에 현지 통화로 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="e0ac9-187">Transactions are stored in the fact table in local currencies.</span></span> <span data-ttu-id="e0ac9-188">통화 변환 기능은 이러한 트랜잭션을 피벗 통화로 변환한 다음 하나 이상의 다른 보고 통화로 변환합니다.</span><span class="sxs-lookup"><span data-stu-id="e0ac9-188">The currency conversion functionality converts such transactions into the pivot currency, and then to one or more other reporting currencies.</span></span>  
  
     <span data-ttu-id="e0ac9-189">예를 들어 피벗 통화를 미국 달러(USD)로 설정하면 팩트 테이블에서는 트랜잭션을 유로(EUR), 오스트레일리아 달러(AUD) 및 멕시코 페소(MXN)로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="e0ac9-189">For example, the pivot currency can be set to United States dollars (USD), and the fact table stores transactions in euros (EUR), Australian dollars (AUD), and Mexican pesos (MXN).</span></span> <span data-ttu-id="e0ac9-190">이 변환 유형은 이러한 트랜잭션을 지정한 현지 통화에서 피벗 통화로 변환한 다음 변환된 트랜잭션을 다시 피벗 통화에서 지정한 보고 통화로 변환합니다.</span><span class="sxs-lookup"><span data-stu-id="e0ac9-190">This conversion type converts these transactions from their specified local currencies to the pivot currency, and then the converted transactions are converted again from the pivot currency to the specified reporting currencies.</span></span> <span data-ttu-id="e0ac9-191">그 결과 트랜잭션을 지정한 현지 통화로 저장한 다음 지정한 피벗 통화 또는 해당 통화 변환에 대해 정의한 보고 통화 차원에 지정된 임의의 보고 통화로 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0ac9-191">The result is that transactions can be stored in the specified local currencies and viewed either in the specified pivot currency or in any of the reporting currencies that are specified in the reporting currency dimension defined for the currency conversion.</span></span>  
  
 <span data-ttu-id="e0ac9-192">변환 유형을 지정하면 비즈니스 인텔리전스 마법사에서 통화 변환에 대해 정의한 MDX 스크립트의 구조뿐 아니라 보고 통화 차원의 명명된 쿼리 및 차원 구조를 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0ac9-192">Specifying the conversion type allows the Business Intelligence Wizard to define the named query and dimension structure of the reporting currency dimension, as well as the structure of the MDX script defined for the currency conversion.</span></span>  
  
### <a name="local-currencies"></a><span data-ttu-id="e0ac9-193">현지 통화</span><span class="sxs-lookup"><span data-stu-id="e0ac9-193">Local Currencies</span></span>  
 <span data-ttu-id="e0ac9-194">통화 변환에 대해 다 대 다 또는 다 대 일 변환 유형을 선택하는 경우 비즈니스 인텔리전스 마법사에서 생성한 MDX 스크립트가 통화 변환 계산을 수행할 현지 통화를 식별하는 방법을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0ac9-194">If you choose a many-to-many or many-to-one conversion type for your currency conversion, you need to specify how to identify the local currencies from which the MDX script generated by the Business Intelligence Wizard performs the currency conversion calculations.</span></span> <span data-ttu-id="e0ac9-195">팩트 테이블의 트랜잭션에 대한 현지 통화는 다음 두 방법 중 하나로 식별할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0ac9-195">The local currency for a transaction in a fact table can be identified in one of two ways:</span></span>  
  
-   <span data-ttu-id="e0ac9-196">측정값 그룹은 통화 차원에 대한 일반 차원 관계를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="e0ac9-196">The measure group contains a regular dimension relationship to the currency dimension.</span></span> <span data-ttu-id="e0ac9-197">예를 들어 [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)] 예제 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 데이터베이스에서 Internet Sales 측정값 그룹은 Currency 차원에 대한 일반 차원 관계를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="e0ac9-197">For example, in the [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)] sample [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database, the Internet Sales measure group has a regular dimension relationship to the Currency dimension.</span></span> <span data-ttu-id="e0ac9-198">이 측정값 그룹의 팩트 테이블에는 해당 차원의 차원 테이블에 있는 통화 식별자를 참조하는 외래 키 열이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0ac9-198">The fact table for that measure group contains a foreign key column that references the currency identifiers in the dimension table for that dimension.</span></span> <span data-ttu-id="e0ac9-199">이 경우 측정값 그룹에서 참조하는 통화 차원에서 특성을 선택하여 해당 측정값 그룹에 대한 팩트 테이블의 트랜잭션에 대한 현지 통화를 식별할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0ac9-199">In this case, you can select the attribute from the currency dimension that is referenced by the measure group to identify the local currency for transactions in the fact table for that measure group.</span></span> <span data-ttu-id="e0ac9-200">이러한 경우는 트랜잭션 자체가 해당 트랜잭션 내에 사용되는 통화를 결정하는 은행 애플리케이션에서 일반적으로 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="e0ac9-200">This situation most often occurs in banking applications, where the transaction itself determines the currency used within the transaction.</span></span>  
  
-   <span data-ttu-id="e0ac9-201">측정값 그룹은 통화 차원을 직접 참조하는 다른 차원을 통해 통화 차원에 대한 참조된 차원 관계를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="e0ac9-201">The measure group contains a referenced dimension relationship to the currency dimension, through another dimension that directly references the currency dimension.</span></span> <span data-ttu-id="e0ac9-202">예를 들어 [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)] 예제 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 데이터베이스에서 Financial Reporting 측정값 그룹은 Organization 차원을 통해 Currency 차원에 대한 참조된 차원 관계를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="e0ac9-202">For example, in the [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)] sample [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database, the Financial Reporting measure group has a referenced dimension relationship to the Currency dimension through the Organization dimension.</span></span> <span data-ttu-id="e0ac9-203">해당 측정값 그룹의 팩트 테이블에는 Organization 차원의 차원 테이블에 있는 멤버를 참조하는 외래 키 열이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0ac9-203">The fact table for that measure group contains a foreign key column that references members in the dimension table for the Organization dimension.</span></span> <span data-ttu-id="e0ac9-204">Organization 차원의 차원 테이블에는 Currency 차원의 차원 테이블에 있는 통화 식별자를 참조하는 외래 키 열이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0ac9-204">The dimension table for the Organization dimension, in turn, contains a foreign key column that references the currency identifiers in the dimension table for the Currency dimension.</span></span> <span data-ttu-id="e0ac9-205">이러한 경우는 트랜잭션에 대한 위치 또는 자회사가 트랜잭션에 대한 통화를 결정하는 재무 보고 애플리케이션에서 일반적으로 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="e0ac9-205">This situation most often occurs in financial reporting applications, where the location or subsidiary for a transaction determines the currency for the transaction.</span></span> <span data-ttu-id="e0ac9-206">이 경우 비즈니스 엔터티에 대한 차원에서 통화 차원을 참조하는 특성을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0ac9-206">In this case, you can select the attribute that references the currency dimension from the dimension for the business entity.</span></span>  
  
### <a name="reporting-currencies"></a><span data-ttu-id="e0ac9-207">보고 통화</span><span class="sxs-lookup"><span data-stu-id="e0ac9-207">Reporting Currencies</span></span>  
 <span data-ttu-id="e0ac9-208">통화 변환에 대해 다 대 다 또는 일 대 다 변환 유형을 선택하는 경우 비즈니스 인텔리전스 마법사에서 생성한 MDX 스크립트가 통화 변환 계산을 수행할 보고 통화를 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0ac9-208">If you choose a many-to-many or one-to-many conversion type for your currency conversion, you need to specify the reporting currencies for which the MDX script generated by the Business Intelligence Wizard performs the currency conversion calculations.</span></span> <span data-ttu-id="e0ac9-209">요율 측정값 그룹과 관련된 통화 차원의 모든 멤버를 지정하거나 차원에서 개별 멤버를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0ac9-209">You can either specify all the members of the currency dimension related to the rate measure group, or select individual members from the dimension.</span></span>  
  
 <span data-ttu-id="e0ac9-210">비즈니스 인텔리전스 마법사는 선택한 보고 통화를 사용하여 통화 차원의 차원 테이블에서 생성한 명명된 쿼리를 기반으로 하여 보고 통화 차원을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e0ac9-210">The Business Intelligence Wizard creates a reporting currency dimension, based on a named query constructed from the dimension table for the currency dimension using the selected reporting currencies.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e0ac9-211">일 대 다 변환 유형을 선택하면 보고 통화 차원도 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="e0ac9-211">If you select the one-to-many conversion type, a reporting currency dimension is also created.</span></span> <span data-ttu-id="e0ac9-212">피벗 통화는 일 대 다 통화 변환에 대한 보고 통화로도 사용되므로 차원은 피벗 통화를 나타내는 멤버를 하나만 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="e0ac9-212">The dimension contains only one member representing the pivot currency, because the pivot currency is also used as the reporting currency for a one-to-many currency conversion.</span></span>  
  
 <span data-ttu-id="e0ac9-213">큐브에 정의된 각 통화 변환에 대해 별도의 보고 통화 차원이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="e0ac9-213">A separate reporting currency dimension is defined for each currency conversion defined in a cube.</span></span> <span data-ttu-id="e0ac9-214">보고 통화 차원을 만든 다음 이름을 변경하는 경우에는 해당 보고 통화 차원을 참조할 때 스크립트 명령에서 올바른 이름이 사용되도록 해당 통화 변환에 대해 생성된 MDX 스크립트도 업데이트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0ac9-214">You can change the name of the reporting currency dimensions after creation, but if you do so you must also update the MDX script generated for that currency conversion to ensure that the correct name is used by the script command when referencing the reporting currency dimension.</span></span>  
  
## <a name="defining-multiple-currency-conversions"></a><span data-ttu-id="e0ac9-215">다중 통화 변환 정의</span><span class="sxs-lookup"><span data-stu-id="e0ac9-215">Defining Multiple Currency Conversions</span></span>  
 <span data-ttu-id="e0ac9-216">비즈니스 인텔리전스 마법사를 사용하여 비즈니스 인텔리전스 솔루션에 필요한 만큼 통화 변환을 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0ac9-216">Using the Business Intelligence Wizard, you can define as many currency conversions as needed for your business intelligence solution.</span></span> <span data-ttu-id="e0ac9-217">기존 통화 변환을 덮어쓰거나 큐브에 대한 MDX 스크립트에 새 통화 변환을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0ac9-217">You can either overwrite an existing currency conversion or append a new currency conversion to the MDX script for a cube.</span></span> <span data-ttu-id="e0ac9-218">단일 큐브에 정의된 다중 통화 변환을 사용하면 국제적 보고를 위해 다양하고도 개별적인 변환 요구 사항을 지원하는 재무 보고 애플리케이션과 같이 보고 요구 사항이 복잡한 비즈니스 인텔리전스 애플리케이션의 유연성을 높일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0ac9-218">Multiple currency conversions defined in a single cube provide flexibility in business intelligence applications that have complex reporting requirements, such as financial reporting applications that support multiple, separate conversion requirements for international reporting.</span></span>  
  
### <a name="identifying-currency-conversions"></a><span data-ttu-id="e0ac9-219">통화 변환 식별</span><span class="sxs-lookup"><span data-stu-id="e0ac9-219">Identifying Currency Conversions</span></span>  
 <span data-ttu-id="e0ac9-220">비즈니스 인텔리전스 마법사는 다음 주석에서 통화 변환에 대한 스크립트 명령을 프레이밍하여 각 통화 변환을 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="e0ac9-220">The Business Intelligence Wizard identifies each currency conversion by framing the script commands for the currency conversion in the following comments:</span></span>  
  
 `//<Currency conversion>`  
  
 `...`  
  
 `[MDX statements for the currency conversion]`  
  
 `...`  
  
 `//</Currency conversion>`  
  
 <span data-ttu-id="e0ac9-221">이러한 주석을 변경하거나 제거하면 비즈니스 인텔리전스 마법사에서 통화 변환을 검색할 수 없게 되므로 이러한 주석을 변경하지 말아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0ac9-221">If you change or remove these comments, the Business Intelligence Wizard is unable to detect the currency conversion, so you should not change these comments.</span></span>  
  
 <span data-ttu-id="e0ac9-222">또한 마법사에서는 이러한 주석 내에 생성 날짜 및 시간, 사용자, 변환 유형 등의 메타데이터를 주석으로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="e0ac9-222">The wizard also stores metadata in comments within these comments, including the creation date and time, the user, and the conversion type.</span></span> <span data-ttu-id="e0ac9-223">비즈니스 인텔리전스 마법사에서 기존 통화 변환을 표시할 때 이러한 메타데이터를 사용하므로 이러한 주석도 변경하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e0ac9-223">These comments should also not be changed because the Business Intelligence Wizard uses this metadata when displaying existing currency conversions.</span></span>  
  
 <span data-ttu-id="e0ac9-224">필요한 경우 통화 변환에 포함된 스크립트 명령을 변경할 수 있지만</span><span class="sxs-lookup"><span data-stu-id="e0ac9-224">You can change the script commands contained in a currency conversion as needed.</span></span> <span data-ttu-id="e0ac9-225">통화 변환을 덮어쓰면 변경 내용이 손실됩니다.</span><span class="sxs-lookup"><span data-stu-id="e0ac9-225">If you overwrite the currency conversion, however, your changes will be lost.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0ac9-226">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e0ac9-226">See Also</span></span>  
 [<span data-ttu-id="e0ac9-227">Analysis Services 다차원에 대한 세계화 시나리오</span><span class="sxs-lookup"><span data-stu-id="e0ac9-227">Globalization scenarios for Analysis Services Multiidimensional</span></span>](globalization-scenarios-for-analysis-services-multiidimensional.md)  
  
  
