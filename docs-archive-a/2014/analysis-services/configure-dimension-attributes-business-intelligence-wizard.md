---
title: 차원 특성 구성 (비즈니스 인텔리전스 마법사) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.biwizard.acctintelligence.selectattributes.f1
ms.assetid: 3d046e63-bcb1-4ab1-9c37-652463fa68c3
author: minewiskan
ms.author: owend
ms.openlocfilehash: 1d2e9bc83b7a6d83b6d2808b472d67169266ff07
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648041"
---
# <a name="configure-dimension-attributes-business-intelligence-wizard"></a><span data-ttu-id="70bc7-102">차원 특성 구성(비즈니스 인텔리전스 마법사)</span><span class="sxs-lookup"><span data-stu-id="70bc7-102">Configure Dimension Attributes (Business Intelligence Wizard)</span></span>
  <span data-ttu-id="70bc7-103">**차원 특성 구성** 페이지를 사용하여 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 에서 계정 차원에 대한 특성을 식별하는 데 사용하는 특성 유형으로 차원 특성을 매핑할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="70bc7-103">Use the **Configure Dimension Attributes** page to map the dimension attributes to the attribute types that [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] uses to identify attributes for account dimensions.</span></span>  
  
## <a name="options"></a><span data-ttu-id="70bc7-104">옵션</span><span class="sxs-lookup"><span data-stu-id="70bc7-104">Options</span></span>  
 <span data-ttu-id="70bc7-105">**차원 유형**</span><span class="sxs-lookup"><span data-stu-id="70bc7-105">**Dimension type**</span></span>  
 <span data-ttu-id="70bc7-106">선택한 차원 유형을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="70bc7-106">Displays the selected dimension type.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="70bc7-107">`Type`차원의 속성을 계정 차원에 대 한 *계정* 이외의 값으로 변경할 수 없으므로이 옵션을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="70bc7-107">This option is not available because the `Type` property of the dimension cannot be changed to a value other than *Account* for account dimensions.</span></span>  
  
 <span data-ttu-id="70bc7-108">**차원 특성**</span><span class="sxs-lookup"><span data-stu-id="70bc7-108">**Dimension attributes**</span></span>  
 <span data-ttu-id="70bc7-109">차원의 기존 차원 특성으로 매핑할 수 있는 유효한 특성 유형을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="70bc7-109">Displays the valid attribute types that can be mapped to existing dimension attributes in the dimension.</span></span>  
  
 <span data-ttu-id="70bc7-110">**되어야**</span><span class="sxs-lookup"><span data-stu-id="70bc7-110">**Include**</span></span>  
 <span data-ttu-id="70bc7-111">확인란을 선택하여 차원에 해당 특성 유형을 포함시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="70bc7-111">Select a check box to include the corresponding attribute type in the dimension.</span></span>  
  
 <span data-ttu-id="70bc7-112">**특성 유형**</span><span class="sxs-lookup"><span data-stu-id="70bc7-112">**Attribute Type**</span></span>  
 <span data-ttu-id="70bc7-113">차원의 기존 차원 특성으로 매핑할 수 있는 특성 유형을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="70bc7-113">Lists the attribute types that can be mapped to existing dimension attributes in the dimension.</span></span>  
  
 <span data-ttu-id="70bc7-114">**차원 특성**</span><span class="sxs-lookup"><span data-stu-id="70bc7-114">**Dimension Attribute**</span></span>  
 <span data-ttu-id="70bc7-115">해당 특성 유형으로 매핑해야 하는 차원 특성을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="70bc7-115">Select the dimension attribute that should be mapped to the corresponding attribute type.</span></span>  
  
 <span data-ttu-id="70bc7-116">**계정 유형에 따라 측정값을 반가산성으로 설정**</span><span class="sxs-lookup"><span data-stu-id="70bc7-116">**Set measures to be semiadditive based on account type**</span></span>  
 <span data-ttu-id="70bc7-117">계정 유형별로 집계될 이 차원과 관련된 모든 측정값을 변경하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="70bc7-117">Select to change every measure associated with this dimension to be aggregated by account type.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="70bc7-118">이 옵션은 차원 디자이너에서 비즈니스 인텔리전스 마법사를 시작하거나 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]의 솔루션 탐색기에서 차원을 마우스 오른쪽 단추로 클릭하여 비즈니스 인텔리전스 마법사를 시작할 경우 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="70bc7-118">This option does not appear if the Business Intelligence Wizard was started from Dimension Designer or by right-clicking a dimension in Solution Explorer in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70bc7-119">참고 항목</span><span class="sxs-lookup"><span data-stu-id="70bc7-119">See Also</span></span>  
 <span data-ttu-id="70bc7-120">[비즈니스 인텔리전스 마법사 F1 도움말](business-intelligence-wizard-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="70bc7-120">[Business Intelligence Wizard F1 Help](business-intelligence-wizard-f1-help.md) </span></span>  
 <span data-ttu-id="70bc7-121">[큐브 디자이너 &#40;Analysis Services 다차원 데이터&#41;](cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="70bc7-121">[Cube Designer &#40;Analysis Services - Multidimensional Data&#41;](cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="70bc7-122">차원 디자이너 &#40;Analysis Services 다차원 데이터&#41;</span><span class="sxs-lookup"><span data-stu-id="70bc7-122">Dimension Designer &#40;Analysis Services - Multidimensional Data&#41;</span></span>](dimension-designer-analysis-services-multidimensional-data.md)  
  
  
