---
title: 멤버 선택 (비즈니스 인텔리전스 마법사) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.biwizard.currencyconversion.memberconversion.f1
ms.assetid: 1a147461-d594-41e7-a41d-09d2d003e1e0
author: minewiskan
ms.author: owend
ms.openlocfilehash: fd5f184e0d9670725609531b6d0a101f8e7f8647
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648624"
---
# <a name="select-members-business-intelligence-wizard"></a><span data-ttu-id="75e16-102">멤버 선택(비즈니스 인텔리전스 마법사)</span><span class="sxs-lookup"><span data-stu-id="75e16-102">Select Members (Business Intelligence Wizard)</span></span>
  <span data-ttu-id="75e16-103">**멤버 선택** 페이지를 사용하여 비즈니스 인텔리전스 마법사가 **통화 변환 옵션 설정** 페이지에 지정된 통화 변환 기능을 적용할 멤버를 결정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="75e16-103">Use the **Select Members** page to determine to which members the Business Intelligence Wizard should apply the currency conversion functionality specified on the **Set Currency Conversion Options** page.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="75e16-104">이 페이지는 차원 디자이너에서 비즈니스 인텔리전스 마법사를 시작하거나 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]의 솔루션 탐색기에서 차원을 마우스 오른쪽 단추로 클릭하여 비즈니스 인텔리전스 마법사를 시작할 경우 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="75e16-104">This page does not appear if the Business Intelligence Wizard was started from Dimension Designer or by right-clicking a dimension in Solution Explorer in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span>  
  
## <a name="options"></a><span data-ttu-id="75e16-105">옵션</span><span class="sxs-lookup"><span data-stu-id="75e16-105">Options</span></span>  
 <span data-ttu-id="75e16-106">**측정값 차원**</span><span class="sxs-lookup"><span data-stu-id="75e16-106">**Measures dimension**</span></span>  
 <span data-ttu-id="75e16-107">큐브에 포함된 하나 이상의 측정값에 통화 변환 기능을 적용하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="75e16-107">Select to apply the currency conversion functionality to one or more measures in the cube.</span></span>  
  
 <span data-ttu-id="75e16-108">선택하면 다음 표에 나열된 옵션이 표에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="75e16-108">If selected, the grid displays the options listed in the following table.</span></span>  
  
|<span data-ttu-id="75e16-109">옵션</span><span class="sxs-lookup"><span data-stu-id="75e16-109">Option</span></span>|<span data-ttu-id="75e16-110">Description</span><span class="sxs-lookup"><span data-stu-id="75e16-110">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="75e16-111">**기본 제공 측정값 유형**</span><span class="sxs-lookup"><span data-stu-id="75e16-111">**Built-in Measure Types**</span></span>|<span data-ttu-id="75e16-112">지정한 측정값에 대한 통화 변환 기능을 포함하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="75e16-112">Select to include currency conversion functionality for the specified measure.</span></span>|  
|<span data-ttu-id="75e16-113">**측정값**</span><span class="sxs-lookup"><span data-stu-id="75e16-113">**Measures**</span></span>|<span data-ttu-id="75e16-114">**기본 제공 측정값 유형** 에서 선택한 측정값을 변환할 때 사용할 환율이 포함된 요율 측정값 그룹에서 측정값을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="75e16-114">Select the measure from the rate measure group that contains the exchange rate to use when the measure selected in **Built-in Measure Types** is converted.</span></span>|  
  
 <span data-ttu-id="75e16-115">**계정 계층**</span><span class="sxs-lookup"><span data-stu-id="75e16-115">**Account hierarchy**</span></span>  
 <span data-ttu-id="75e16-116">큐브에 포함된 계정 차원의 계정 계층에서 하나 이상의 멤버에 통화 변환 기능을 적용하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="75e16-116">Select to apply the currency conversion functionality to one or more members in the account hierarchy of the account dimension included in the cube.</span></span> <span data-ttu-id="75e16-117">계정 계층은 `Type` 속성이 *account*로 설정 된 계정 차원 내의 계층입니다.</span><span class="sxs-lookup"><span data-stu-id="75e16-117">The account hierarchy is the hierarchy within the account dimension whose `Type` property is set to *Account*.</span></span>  
  
 <span data-ttu-id="75e16-118">선택하면 다음 표에 나열된 옵션이 표에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="75e16-118">If selected, the grid displays the options listed in the following table.</span></span>  
  
|<span data-ttu-id="75e16-119">옵션</span><span class="sxs-lookup"><span data-stu-id="75e16-119">Option</span></span>|<span data-ttu-id="75e16-120">Description</span><span class="sxs-lookup"><span data-stu-id="75e16-120">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="75e16-121">**계정 멤버**</span><span class="sxs-lookup"><span data-stu-id="75e16-121">**Account Member**</span></span>|<span data-ttu-id="75e16-122">지정한 계정 계층 멤버에 대한 통화 변환 기능을 포함하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="75e16-122">Select to include currency conversion functionality for the specified member of the account hierarchy.</span></span>|  
|<span data-ttu-id="75e16-123">**측정값**</span><span class="sxs-lookup"><span data-stu-id="75e16-123">**Measures**</span></span>|<span data-ttu-id="75e16-124">**계정 멤버** 에서 선택한 멤버의 측정값을 변환할 때 사용할 환율이 포함된 요율 측정값 그룹에서 측정값을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="75e16-124">Select the measure from the rate measure group that contains the exchange rate to use when the measures for the member selected in **Account Member** are converted.</span></span>|  
  
 <span data-ttu-id="75e16-125">**유형을 기반으로 하는 계정 계층**</span><span class="sxs-lookup"><span data-stu-id="75e16-125">**Account hierarchy based on type**</span></span>  
 <span data-ttu-id="75e16-126">`Type` 속성이 지정한 계정 유형으로 설정된 계정 계층에서 특성의 모든 멤버에 통화 변환 기능을 적용하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="75e16-126">Select to apply the currency conversion functionality to all members of attributes in the account hierarchy whose `Type` property is set to a specified account type.</span></span>  
  
 <span data-ttu-id="75e16-127">선택하면 다음 표에 나열된 옵션이 표에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="75e16-127">If selected, the grid displays the options listed in the following table.</span></span>  
  
|<span data-ttu-id="75e16-128">옵션</span><span class="sxs-lookup"><span data-stu-id="75e16-128">Option</span></span>|<span data-ttu-id="75e16-129">Description</span><span class="sxs-lookup"><span data-stu-id="75e16-129">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="75e16-130">**계정 유형**</span><span class="sxs-lookup"><span data-stu-id="75e16-130">**Account Type**</span></span>|<span data-ttu-id="75e16-131">지정한 계정 유형에 대한 통화 변환 기능을 포함하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="75e16-131">Select to include currency conversion functionality for the specified account type.</span></span>|  
|<span data-ttu-id="75e16-132">**측정값**</span><span class="sxs-lookup"><span data-stu-id="75e16-132">**Measures**</span></span>|<span data-ttu-id="75e16-133">**계정 유형** 에서 선택한 계정 유형을 사용하는 특성 멤버에 대한 측정값을 변환할 때 사용할 환율이 포함된 요율 측정값 그룹에서 측정값을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="75e16-133">Select the measure from the rate measure group that contains the exchange rate to use when measures for the members of attributes using the account type selected in **Account Type** are converted.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="75e16-134">참고 항목</span><span class="sxs-lookup"><span data-stu-id="75e16-134">See Also</span></span>  
 <span data-ttu-id="75e16-135">[비즈니스 인텔리전스 마법사 F1 도움말](business-intelligence-wizard-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="75e16-135">[Business Intelligence Wizard F1 Help](business-intelligence-wizard-f1-help.md) </span></span>  
 <span data-ttu-id="75e16-136">[큐브 디자이너 &#40;Analysis Services 다차원 데이터&#41;](cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="75e16-136">[Cube Designer &#40;Analysis Services - Multidimensional Data&#41;](cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="75e16-137">차원 디자이너 &#40;Analysis Services 다차원 데이터&#41;</span><span class="sxs-lookup"><span data-stu-id="75e16-137">Dimension Designer &#40;Analysis Services - Multidimensional Data&#41;</span></span>](dimension-designer-analysis-services-multidimensional-data.md)  
  
  
