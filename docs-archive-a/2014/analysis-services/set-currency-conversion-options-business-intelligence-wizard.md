---
title: 통화 변환 옵션 설정 (비즈니스 인텔리전스 마법사) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.biwizard.currencyconversion.calculationsettings.f1
ms.assetid: a49d4e1f-bdda-4a83-ab4f-ce8c500e1d6d
author: minewiskan
ms.author: owend
ms.openlocfilehash: 61877deb0bc422d65f977e3fc9de3e678f7d8477
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736909"
---
# <a name="set-currency-conversion-options-business-intelligence-wizard"></a><span data-ttu-id="309f8-102">통화 변환 옵션 설정(비즈니스 인텔리전스 마법사)</span><span class="sxs-lookup"><span data-stu-id="309f8-102">Set Currency Conversion Options (Business Intelligence Wizard)</span></span>
  <span data-ttu-id="309f8-103">**통화 변환 옵션 설정** 페이지를 사용하여 환율이 포함된 측정값 그룹에 대해 통화 변환 계산을 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="309f8-103">Use the **Set Currency Conversion** page to define currency conversion calculations for a measure group that contains exchange rates.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="309f8-104">이 페이지는 차원 디자이너에서 비즈니스 인텔리전스 마법사를 시작하거나 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]의 솔루션 탐색기에서 차원을 마우스 오른쪽 단추로 클릭하여 비즈니스 인텔리전스 마법사를 시작할 경우 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="309f8-104">This page does not appear if the Business Intelligence Wizard was started from Dimension Designer or by right-clicking a dimension in Solution Explorer in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span>  
  
## <a name="options"></a><span data-ttu-id="309f8-105">옵션</span><span class="sxs-lookup"><span data-stu-id="309f8-105">Options</span></span>  
 <span data-ttu-id="309f8-106">**환율이 포함된 측정값 그룹 선택**</span><span class="sxs-lookup"><span data-stu-id="309f8-106">**Select the measure group that contains exchange rates**</span></span>  
 <span data-ttu-id="309f8-107">통화 변환 계산에서 참조할 환율이 포함된 측정값 그룹을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="309f8-107">Select the measure group that contains the exchange rates that the currency conversion calculations should reference.</span></span>  
  
 <span data-ttu-id="309f8-108">**피벗 통화 지정**</span><span class="sxs-lookup"><span data-stu-id="309f8-108">**Specify the pivot currency**</span></span>  
 <span data-ttu-id="309f8-109">측정값 그룹의 피벗 통화 역할을 하는 멤버를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="309f8-109">Select the member that serves as the pivot currency for the measure group.</span></span>  
  
 <span data-ttu-id="309f8-110">**환율 입력 방법 선택(샘플 통화 선택)**</span><span class="sxs-lookup"><span data-stu-id="309f8-110">**Select how you entered your exchange rates (select a sample currency)**</span></span>  
 <span data-ttu-id="309f8-111">환율 방향을 잘 표시하도록 통화 차원에서 샘플 통화를 나타내는 멤버를 선택하여 1 샘플 통화당 X 피벗 통화 및 1 피벗 통화당 X 샘플 통화 옵션에 대한 텍스트를 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="309f8-111">Select a member representing a sample currency from the currency dimension to change the text for the X pivot currency per 1 sample currency and X sample currency per 1 pivot currency options to better display the exchange rate direction.</span></span>  
  
 <span data-ttu-id="309f8-112">**1 샘플 통화당 X 피벗 통화**</span><span class="sxs-lookup"><span data-stu-id="309f8-112">**X pivot currency per 1 sample currency**</span></span>  
 <span data-ttu-id="309f8-113">요율 측정값 그룹의 환율이 지정한 피벗 통화에 대한 승수임을 표시하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="309f8-113">Select to indicate that the exchange rates in the rate measure group represent a multiplier for the specified pivot currency.</span></span>  
  
 <span data-ttu-id="309f8-114">**1 피벗 통화당 X 샘플 통화**</span><span class="sxs-lookup"><span data-stu-id="309f8-114">**X sample currency per 1 pivot currency**</span></span>  
 <span data-ttu-id="309f8-115">요율 측정값 그룹의 환율이 지정한 샘플 통화에 대한 승수임을 표시하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="309f8-115">Select to indicate that the exchange rates in the rate measure group represent a multiplier for the specified sample currency.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="309f8-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="309f8-116">See Also</span></span>  
 <span data-ttu-id="309f8-117">[비즈니스 인텔리전스 마법사 F1 도움말](business-intelligence-wizard-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="309f8-117">[Business Intelligence Wizard F1 Help](business-intelligence-wizard-f1-help.md) </span></span>  
 <span data-ttu-id="309f8-118">[큐브 디자이너 &#40;Analysis Services 다차원 데이터&#41;](cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="309f8-118">[Cube Designer &#40;Analysis Services - Multidimensional Data&#41;](cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="309f8-119">차원 디자이너 &#40;Analysis Services 다차원 데이터&#41;</span><span class="sxs-lookup"><span data-stu-id="309f8-119">Dimension Designer &#40;Analysis Services - Multidimensional Data&#41;</span></span>](dimension-designer-analysis-services-multidimensional-data.md)  
  
  
