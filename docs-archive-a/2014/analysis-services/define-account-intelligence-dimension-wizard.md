---
title: 계정 인텔리전스 정의 (차원 마법사) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.dimensionwizard.accountintelligencetypemapping.f1
ms.assetid: cbcff072-3a7e-4e98-858f-1b4265461561
author: minewiskan
ms.author: owend
ms.openlocfilehash: 90871e2299d1531db1b678b1f4b16ddd7f1db767
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653049"
---
# <a name="define-account-intelligence-dimension-wizard"></a><span data-ttu-id="a976f-102">계정 인텔리전스 정의(차원 마법사)</span><span class="sxs-lookup"><span data-stu-id="a976f-102">Define Account Intelligence (Dimension Wizard)</span></span>
  <span data-ttu-id="a976f-103">**계정 인텔리전스 정의** 페이지를 사용하여 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 인스턴스에서 정의한 계정 유형을 차원의 **계정 유형** 특성 유형과 연결된 차원 특성에서 정의한 계정 유형으로 매핑할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a976f-103">Use the **Define Account Intelligence** page to map account types defined on the [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance to account types defined in the dimension attribute associated with the **Account Type** attribute type in the dimension.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a976f-104">**차원 유형 선택** 페이지에서 **표준 차원** 을 선택했으며 **차원 유형 지정** 페이지에서 차원 특성을 **계정 유형** 특성 유형에 매핑한 경우에만 이 페이지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="a976f-104">This page is displayed only if you selected **Standard dimension** on the **Select the Dimension Type** page and if you mapped a dimension attribute to the **Account Type** attribute type on the **Specify Dimension Type** page.</span></span>  
  
## <a name="options"></a><span data-ttu-id="a976f-105">옵션</span><span class="sxs-lookup"><span data-stu-id="a976f-105">Options</span></span>  
 <span data-ttu-id="a976f-106">**원본 테이블 계정 유형**</span><span class="sxs-lookup"><span data-stu-id="a976f-106">**Source Table Account Types**</span></span>  
 <span data-ttu-id="a976f-107">**차원 키 및 유형 지정** 페이지의 **계정 유형** 특성 유형에 할당된 차원 특성에 포함된 값을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="a976f-107">Displays the values contained in the dimension attribute assigned to the **Account Type** attribute type in the **Specify Dimension Key and Type** page.</span></span>  
  
 <span data-ttu-id="a976f-108">**기본 제공 계정 유형**</span><span class="sxs-lookup"><span data-stu-id="a976f-108">**Built-In Account Types**</span></span>  
 <span data-ttu-id="a976f-109">원본 테이블의 계정 유형에 매핑되는 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 인스턴스에 정의된 계정 유형을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="a976f-109">Select the account type defined on the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance that maps to the account types in the source table.</span></span>  
  
 <span data-ttu-id="a976f-110">다음 표에서는 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 인스턴스에 정의된 계정 유형을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="a976f-110">The following table lists the account types that are defined on an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance.</span></span>  
  
|<span data-ttu-id="a976f-111">값</span><span class="sxs-lookup"><span data-stu-id="a976f-111">Value</span></span>|<span data-ttu-id="a976f-112">Description</span><span class="sxs-lookup"><span data-stu-id="a976f-112">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="a976f-113">**자산**</span><span class="sxs-lookup"><span data-stu-id="a976f-113">**Asset**</span></span>|<span data-ttu-id="a976f-114">특정 시간에 소유하고 있는 항목의 가치입니다.</span><span class="sxs-lookup"><span data-stu-id="a976f-114">Value of things owned at a specific time.</span></span>|  
|<span data-ttu-id="a976f-115">**Balance**</span><span class="sxs-lookup"><span data-stu-id="a976f-115">**Balance**</span></span>|<span data-ttu-id="a976f-116">특정 시간의 항목 합계입니다.</span><span class="sxs-lookup"><span data-stu-id="a976f-116">Count of something at a specific time.</span></span>|  
|<span data-ttu-id="a976f-117">**Expense**</span><span class="sxs-lookup"><span data-stu-id="a976f-117">**Expense**</span></span>|<span data-ttu-id="a976f-118">지출한 비용입니다.</span><span class="sxs-lookup"><span data-stu-id="a976f-118">Value of things spent.</span></span>|  
|<span data-ttu-id="a976f-119">**흐름**</span><span class="sxs-lookup"><span data-stu-id="a976f-119">**Flow**</span></span>|<span data-ttu-id="a976f-120">항목의 증분 합계입니다.</span><span class="sxs-lookup"><span data-stu-id="a976f-120">Incremental count of things.</span></span>|  
|<span data-ttu-id="a976f-121">**Income**</span><span class="sxs-lookup"><span data-stu-id="a976f-121">**Income**</span></span>|<span data-ttu-id="a976f-122">받은 항목의 가치입니다.</span><span class="sxs-lookup"><span data-stu-id="a976f-122">Value of things received.</span></span>|  
|<span data-ttu-id="a976f-123">**Liability**</span><span class="sxs-lookup"><span data-stu-id="a976f-123">**Liability**</span></span>|<span data-ttu-id="a976f-124">특정 시간에 진 빚의 가치입니다.</span><span class="sxs-lookup"><span data-stu-id="a976f-124">Value of things owed at a specific time.</span></span>|  
|<span data-ttu-id="a976f-125">**통계**</span><span class="sxs-lookup"><span data-stu-id="a976f-125">**Statistical**</span></span>|<span data-ttu-id="a976f-126">항목의 계산된 비율 또는 집계되지 않는 항목의 합계입니다.</span><span class="sxs-lookup"><span data-stu-id="a976f-126">Calculated ratio of something, or count of something that does not aggregate.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a976f-127">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a976f-127">See Also</span></span>  
 <span data-ttu-id="a976f-128">[차원 마법사 F1 도움말](dimension-wizard-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="a976f-128">[Dimension Wizard F1 Help](dimension-wizard-f1-help.md) </span></span>  
 <span data-ttu-id="a976f-129">[차원 &#40;Analysis Services 다차원 데이터&#41;](multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="a976f-129">[Dimensions &#40;Analysis Services - Multidimensional Data&#41;](multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="a976f-130">다차원 모델의 차원</span><span class="sxs-lookup"><span data-stu-id="a976f-130">Dimensions in Multidimensional Models</span></span>](multidimensional-models/dimensions-in-multidimensional-models.md)  
  
  
