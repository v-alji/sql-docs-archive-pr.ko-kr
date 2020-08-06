---
title: 현지 통화 참조 정의 (비즈니스 인텔리전스 마법사) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.biwizard.currencyconversion.localcurrency.f1
ms.assetid: 74993b0d-dfca-476b-acba-d66c593680a5
author: minewiskan
ms.author: owend
ms.openlocfilehash: bcd5c01839ecc7ae120089f17a1b909f18464e9d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734580"
---
# <a name="define-local-currency-reference-business-intelligence-wizard"></a><span data-ttu-id="c63be-102">현지 통화 참조 정의(비즈니스 인텔리전스 마법사)</span><span class="sxs-lookup"><span data-stu-id="c63be-102">Define Local Currency Reference (Business Intelligence Wizard)</span></span>
  <span data-ttu-id="c63be-103">**현지 통화 참조 정의** 페이지를 사용하여 **변환 유형 선택** 페이지에서 지정한 다 대 다 또는 다 대 일 변환 유형을 다루는 통화 변환 기능에 대한 현지 통화를 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c63be-103">Use the **Define Local Currency Reference** page to define the local currencies for currency conversion functionality that covers the many-to-many or many-to-one conversion types specified on the **Select Conversion Type** page.</span></span> <span data-ttu-id="c63be-104">현지 통화는 **측정값 선택** 페이지에서 선택한 측정값에 대한 트랜잭션이 저장되는 통화입니다.</span><span class="sxs-lookup"><span data-stu-id="c63be-104">A local currency is the currency in which the transactions for measures selected in the **Select Measures** page are stored.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c63be-105">이 페이지는 차원 디자이너에서 비즈니스 인텔리전스 마법사를 시작하거나 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]의 솔루션 탐색기에서 차원을 마우스 오른쪽 단추로 클릭하여 비즈니스 인텔리전스 마법사를 시작할 경우 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c63be-105">This page does not appear if the Business Intelligence Wizard was started from Dimension Designer or by right-clicking a dimension in Solution Explorer in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="c63be-106">**변환 유형 선택** 페이지에서 **일 대 다** 를 선택한 경우에도 이 페이지가 나타나지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c63be-106">This page also does not appear if **One-to-Many** was selected on the **Select Conversion Type** page.</span></span>  
  
## <a name="options"></a><span data-ttu-id="c63be-107">옵션</span><span class="sxs-lookup"><span data-stu-id="c63be-107">Options</span></span>  
 <span data-ttu-id="c63be-108">**팩트 테이블의 식별자**</span><span class="sxs-lookup"><span data-stu-id="c63be-108">**Identifiers in the fact table**</span></span>  
 <span data-ttu-id="c63be-109">**측정값 선택** 페이지에서 선택한 측정값을 포함하는 팩트 테이블이 참조하는 통화 차원의 현지 통화에 대한 통화 식별자를 제공하는 특성을 지정하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c63be-109">Select to specify an attribute that provides currency identifiers for local currencies in a currency dimension referenced by the fact table that contains the measures selected on the **Select Measures** page.</span></span> <span data-ttu-id="c63be-110">(해당 `Type` 속성이 *통화로*설정 된 통화 차원</span><span class="sxs-lookup"><span data-stu-id="c63be-110">(A currency dimension in one whose `Type` property is set to *Currency*.)</span></span>  
  
 <span data-ttu-id="c63be-111">트랜잭션 자체에서 해당 트랜잭션에 대한 현지 통화를 결정하는 경우 이 옵션을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="c63be-111">Use this option when the transaction itself determines the local currency for that transaction.</span></span> <span data-ttu-id="c63be-112">예를 들어 예제 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 데이터베이스에서 [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)] Internet Sales 측정값 그룹은 Currency 차원에 대 한 일반 차원 관계를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="c63be-112">For example, in the [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] sample database-[!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)], the Internet Sales measure group has a regular dimension relationship to the Currency dimension.</span></span> <span data-ttu-id="c63be-113">이 측정값 그룹의 팩트 테이블에는 해당 차원의 차원 테이블에 있는 통화 식별자를 참조하는 외래 키 열이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c63be-113">The fact table for that measure group contains a foreign key column that references the currency identifiers in the dimension table for that dimension.</span></span>  
  
 <span data-ttu-id="c63be-114">**팩트 데이터에서 참조하는 통화 차원 및 특성**</span><span class="sxs-lookup"><span data-stu-id="c63be-114">**Currency dimension and attribute referenced by the fact data**</span></span>  
 <span data-ttu-id="c63be-115">해당 멤버가 현지 통화에 대한 통화 식별자를 나타내는 통화 차원 내에서 통화 특성을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c63be-115">Select the currency attribute within a currency dimension whose members represent currency identifiers for local currencies.</span></span> <span data-ttu-id="c63be-116">통화 특성은 해당 `Type` 속성이 *통화로*설정 된 항목입니다.</span><span class="sxs-lookup"><span data-stu-id="c63be-116">(A currency attribute is one whose `Type` property is set to *Currency*.)</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c63be-117"> 이 옵션은 **팩트 테이블의 식별자** 옵션을 선택하지 않으면 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c63be-117">This option is not available if the **Identifiers in the fact table** option is not selected.</span></span>  
  
 <span data-ttu-id="c63be-118">**차원 테이블의 특성**</span><span class="sxs-lookup"><span data-stu-id="c63be-118">**Attributes in the dimension table**</span></span>  
 <span data-ttu-id="c63be-119">현지 통화에 대한 통화 식별자를 포함하는 측정값 그룹과 관련된 차원에서 특성을 지정하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c63be-119">Select to specify an attribute from a dimension related to the measure group that contains currency identifiers for local currencies.</span></span>  
  
 <span data-ttu-id="c63be-120">트랜잭션과 다른 비즈니스 엔터티 간의 관계(위치 등)가 해당 트랜잭션에 대한 현지 통화를 결정하는 경우 이 옵션을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="c63be-120">Use this option when the relationship between a transaction and another business entity, such as a location, determines the local currency for that transaction.</span></span> <span data-ttu-id="c63be-121">예를 들어 예제 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 데이터베이스에서 [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)] Financial Reporting 측정값 그룹은 조직 차원을 통해 Currency 차원에 대 한 참조 된 차원 관계를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="c63be-121">For example, in the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] sample database-[!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)], the Financial Reporting measure group has a referenced dimension relationship to the Currency dimension through the Organization dimension.</span></span> <span data-ttu-id="c63be-122">즉, Financial Reporting 측정값 그룹의 팩트 테이블에는 Organization 차원의 차원 테이블에 있는 멤버를 참조하는 외래 키 열이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c63be-122">That is, the fact table for the Financial Reporting measure group contains a foreign key column that references members in the dimension table for the Organization dimension.</span></span> <span data-ttu-id="c63be-123">Organization 차원의 차원 테이블에는 Currency 차원의 차원 테이블에 있는 통화 식별자를 참조하는 외래 키 열이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c63be-123">The dimension table for the Organization dimension, in turn, contains a foreign key column that references the currency identifiers in the dimension table for the Currency dimension.</span></span>  
  
 <span data-ttu-id="c63be-124">**통화를 참조하는 차원 특성**</span><span class="sxs-lookup"><span data-stu-id="c63be-124">**Dimension attribute that references currency**</span></span>  
 <span data-ttu-id="c63be-125">해당 멤버가 현지 통화에 대한 통화 식별자를 참조하는 차원 내에서 특성을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c63be-125">Select the attribute within a dimension whose members reference the currency identifiers for local currency.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c63be-126"> 이 옵션은 **차원 테이블의 특성** 옵션을 선택하지 않으면 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c63be-126">This option is not available if the **Attributes in the dimension table** option is not selected.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c63be-127">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c63be-127">See Also</span></span>  
 <span data-ttu-id="c63be-128">[비즈니스 인텔리전스 마법사 F1 도움말](business-intelligence-wizard-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="c63be-128">[Business Intelligence Wizard F1 Help](business-intelligence-wizard-f1-help.md) </span></span>  
 <span data-ttu-id="c63be-129">[큐브 디자이너 &#40;Analysis Services 다차원 데이터&#41;](cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="c63be-129">[Cube Designer &#40;Analysis Services - Multidimensional Data&#41;](cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="c63be-130">차원 디자이너 &#40;Analysis Services 다차원 데이터&#41;</span><span class="sxs-lookup"><span data-stu-id="c63be-130">Dimension Designer &#40;Analysis Services - Multidimensional Data&#41;</span></span>](dimension-designer-analysis-services-multidimensional-data.md)  
  
  
