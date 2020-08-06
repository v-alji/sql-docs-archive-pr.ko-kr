---
title: 변환 유형 선택 (비즈니스 인텔리전스 마법사) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.biwizard.currencyconversion.conversiontype.f1
ms.assetid: 2c664138-e8a1-4c47-8e7d-ee01c57e4692
author: minewiskan
ms.author: owend
ms.openlocfilehash: 1f83fdf566b52a5fe79bea7a4a676274423d1091
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647886"
---
# <a name="select-conversion-type-business-intelligence-wizard"></a><span data-ttu-id="5446d-102">변환 유형 선택(비즈니스 인텔리전스 마법사)</span><span class="sxs-lookup"><span data-stu-id="5446d-102">Select Conversion Type (Business Intelligence Wizard)</span></span>
  <span data-ttu-id="5446d-103">**변환 유형 선택** 페이지를 사용하여 여러 통화로 저장된 트랜잭션에 대해 현지 통화와 보고 통화 간의 관계를 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5446d-103">Use the **Select Conversion Type** page to define the relationship between local currencies and reporting currencies for transactions stored in multiple currencies.</span></span> <span data-ttu-id="5446d-104">현지 통화는 **측정값 선택** 페이지에서 선택한 측정값에 대한 트랜잭션이 저장되는 통화입니다.</span><span class="sxs-lookup"><span data-stu-id="5446d-104">A local currency is the currency in which the transactions for measures selected in the **Select Measures** page are stored.</span></span> <span data-ttu-id="5446d-105">보고 통화는 **측정값 선택** 페이지에서 선택한 트랜잭션이 번역되는 통화입니다.</span><span class="sxs-lookup"><span data-stu-id="5446d-105">A reporting currency is the currency in which the transactions selected in the **Select Measures** page are translated.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5446d-106">이 페이지는 차원 디자이너에서 비즈니스 인텔리전스 마법사를 시작하거나 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]의 솔루션 탐색기에서 차원을 마우스 오른쪽 단추로 클릭하여 비즈니스 인텔리전스 마법사를 시작할 경우 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5446d-106">This page does not appear if the Business Intelligence Wizard was started from Dimension Designer or by right-clicking a dimension in Solution Explorer in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span>  
  
## <a name="options"></a><span data-ttu-id="5446d-107">옵션</span><span class="sxs-lookup"><span data-stu-id="5446d-107">Options</span></span>  
 <span data-ttu-id="5446d-108">**다 대 다**</span><span class="sxs-lookup"><span data-stu-id="5446d-108">**Many-to-many**</span></span>  
 <span data-ttu-id="5446d-109">현지 통화를 사용하여 트랜잭션을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="5446d-109">Stores transactions using local currencies.</span></span> <span data-ttu-id="5446d-110">통화 변환 기능은 트랜잭션을 **통화 변환 옵션 설정** 페이지에서 지정한 피벗 통화로 변환한 다음 하나 이상의 다른 보고 통화로 변환합니다.</span><span class="sxs-lookup"><span data-stu-id="5446d-110">The currency conversion functionality converts such transactions into the pivot currency specified in the **Set Currency Conversion Options** page, and then to one or more other reporting currencies.</span></span>  
  
 <span data-ttu-id="5446d-111">예를 들어 피벗 통화를 미국 달러(USD)로 설정하면 팩트 테이블에서는 트랜잭션을 유로(EUR), 오스트레일리아 달러(AUD) 및 멕시코 페소(MXN)로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="5446d-111">For example, the pivot currency can be set to United States dollars (USD), and the fact table stores transactions in euros (EUR), Australian dollars (AUD), and Mexican pesos (MXN).</span></span> <span data-ttu-id="5446d-112">이 옵션을 선택하면 이러한 트랜잭션이 지정한 현지 통화에서 피벗 통화로 변환된 다음 변환된 트랜잭션이 다시 피벗 통화에서 지정한 보고 통화로 변환됩니다.</span><span class="sxs-lookup"><span data-stu-id="5446d-112">Selecting this option converts these transactions from their specified local currencies to the pivot currency, and then the converted transactions are converted again from the pivot currency to the specified reporting currencies.</span></span> <span data-ttu-id="5446d-113">그 결과 트랜잭션을 지정한 현지 통화로 저장하고 지정한 피벗 통화 또는 **보고 통화 지정** 페이지에서 지정한 보고 통화 중 하나로 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5446d-113">The result is that transactions can be stored in the specified local currencies and viewed either in the specified pivot currency or in any one of the reporting currencies specified in the **Specify Reporting Currencies** page.</span></span>  
  
 <span data-ttu-id="5446d-114">**다 대 일**</span><span class="sxs-lookup"><span data-stu-id="5446d-114">**Many-to-one**</span></span>  
 <span data-ttu-id="5446d-115">현지 통화를 사용하여 트랜잭션을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="5446d-115">Stores transactions using local currencies.</span></span> <span data-ttu-id="5446d-116">통화 변환 기능은 트랜잭션을 **통화 변환 옵션 설정** 페이지에서 지정한 피벗 통화로 변환합니다.</span><span class="sxs-lookup"><span data-stu-id="5446d-116">The currency conversion functionality converts such transactions into the pivot currency specified in the **Set Currency Conversion Options** page.</span></span> <span data-ttu-id="5446d-117">피벗 통화는 지정된 유일한 보고 통화로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="5446d-117">The pivot currency serves as the only specified reporting currency.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5446d-118">이 옵션을 선택하면 **보고 통화 지정** 페이지가 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5446d-118">If this option is selected, the **Specify Reporting Currencies** page does not appear.</span></span>  
  
 <span data-ttu-id="5446d-119">예를 들어 피벗 통화를 미국 달러(USD)로 설정하면 팩트 테이블에서는 트랜잭션을 유로(EUR), 오스트레일리아 달러(AUD) 및 멕시코 페소(MXN)로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="5446d-119">For example, the pivot currency can be set to United States dollars (USD), and the fact table stores transactions in euros (EUR), Australian dollars (AUD), and Mexican pesos (MXN).</span></span> <span data-ttu-id="5446d-120">이 옵션을 선택하면 이러한 트랜잭션이 지정한 현지 통화에서 피벗 통화로 변환됩니다.</span><span class="sxs-lookup"><span data-stu-id="5446d-120">Selecting this option converts these transactions from their specified local currencies to the pivot currency.</span></span> <span data-ttu-id="5446d-121">그 결과 트랜잭션을 지정한 현지 통화로 저장하고 지정한 피벗 통화로 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5446d-121">The result is that transactions can be stored in the specified local currencies and viewed in the specified pivot currency.</span></span>  
  
 <span data-ttu-id="5446d-122">**일 대 다**</span><span class="sxs-lookup"><span data-stu-id="5446d-122">**One-to-many**</span></span>  
 <span data-ttu-id="5446d-123">**통화 변환 옵션 설정** 페이지에서 지정한 피벗 통화를 사용하여 트랜잭션을 저장한 다음 하나 이상의 다른 보고 통화로 변환합니다.</span><span class="sxs-lookup"><span data-stu-id="5446d-123">Store transactions using the pivot currency specified in the **Set Currency Conversion Options** page, and then to one or more other reporting currencies.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5446d-124">이 옵션을 선택하면 **현지 통화 참조 정의** 페이지가 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5446d-124">If this option is selected, the **Define Local Currency Reference** page does not appear.</span></span>  
  
 <span data-ttu-id="5446d-125">예를 들어 피벗 통화를 미국 달러(USD)로 설정하면 팩트 테이블에서는 트랜잭션을 USD로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="5446d-125">For example, the pivot currency can be set to United States dollars (USD), and the fact table stores transactions in USD.</span></span> <span data-ttu-id="5446d-126">이 옵션을 선택하면 이러한 트랜잭션이 피벗 통화에서 지정한 보고 통화로 변환됩니다.</span><span class="sxs-lookup"><span data-stu-id="5446d-126">Selecting this option converts these transactions from the pivot currency to the specified reporting currencies.</span></span> <span data-ttu-id="5446d-127">그 결과 트랜잭션을 지정한 피벗 통화로 저장하고 지정한 피벗 통화 또는 **보고 통화 지정** 페이지에서 지정한 보고 통화 중 하나로 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5446d-127">The result is that transactions can be stored in the specified pivot currency and viewed either in the specified pivot currency or in any one of the reporting currencies specified in the **Specify Reporting Currencies** page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5446d-128">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5446d-128">See Also</span></span>  
 <span data-ttu-id="5446d-129">[비즈니스 인텔리전스 마법사 F1 도움말](business-intelligence-wizard-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="5446d-129">[Business Intelligence Wizard F1 Help](business-intelligence-wizard-f1-help.md) </span></span>  
 <span data-ttu-id="5446d-130">[큐브 디자이너 &#40;Analysis Services 다차원 데이터&#41;](cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="5446d-130">[Cube Designer &#40;Analysis Services - Multidimensional Data&#41;](cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="5446d-131">차원 디자이너 &#40;Analysis Services 다차원 데이터&#41;</span><span class="sxs-lookup"><span data-stu-id="5446d-131">Dimension Designer &#40;Analysis Services - Multidimensional Data&#41;</span></span>](dimension-designer-analysis-services-multidimensional-data.md)  
  
  
