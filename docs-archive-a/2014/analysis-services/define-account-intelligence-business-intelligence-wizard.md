---
title: 계정 인텔리전스 정의 (비즈니스 인텔리전스 마법사) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.biwizard.acctintelligence.mapaccounttype.f1
ms.assetid: fe4c204b-1031-4ac4-9916-8052ce2301cc
author: minewiskan
ms.author: owend
ms.openlocfilehash: 17b8136e79097cd502d6b239ba6867c4e678c70f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728960"
---
# <a name="define-account-intelligence-business-intelligence-wizard"></a><span data-ttu-id="a6a11-102">계정 인텔리전스 정의(비즈니스 인텔리전스 마법사)</span><span class="sxs-lookup"><span data-stu-id="a6a11-102">Define Account Intelligence (Business Intelligence Wizard)</span></span>
  <span data-ttu-id="a6a11-103">**계정 인텔리전스 정의** 페이지를 사용하여 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 인스턴스에 정의된 계정 유형을 계정 차원에 데이터를 제공하는 데이터 원본의 원본 테이블에서 정의한 계정 유형으로 매핑할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a6a11-103">Use the **Define Account Intelligence** page to map account types defined on the [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance to account types defined by a source table in the data source that supplies the data for the account dimension.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a6a11-104"> 이 페이지는 **차원 특성 구성** 페이지에서 **계정 유형** 특성 유형에 차원 특성을 매핑한 경우에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="a6a11-104">This page will appear if a dimension attribute was mapped to the **Account Type** attribute type on the **Configure Dimension Attributes** page.</span></span>  
  
## <a name="options"></a><span data-ttu-id="a6a11-105">옵션</span><span class="sxs-lookup"><span data-stu-id="a6a11-105">Options</span></span>  
 <span data-ttu-id="a6a11-106">**원본 테이블 계정 유형**</span><span class="sxs-lookup"><span data-stu-id="a6a11-106">**Source Table Account Types**</span></span>  
 <span data-ttu-id="a6a11-107">**차원 특성 구성** 페이지에서 **계정 유형** 특성 유형에 할당한 차원 특성에 포함된 값을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="a6a11-107">Displays the values that are contained in the dimension attribute assigned to the **Account Type** attribute type on the **Configure Dimension Attributes** page.</span></span>  
  
 <span data-ttu-id="a6a11-108">**기본 제공 계정 유형**</span><span class="sxs-lookup"><span data-stu-id="a6a11-108">**Built-In Account Types**</span></span>  
 <span data-ttu-id="a6a11-109">원본 테이블의 계정 유형에 매핑되는 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 인스턴스에 정의된 계정 유형을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="a6a11-109">Select the account type defined on the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance that maps to the account types in the source table.</span></span>  
  
 <span data-ttu-id="a6a11-110">다음 표에서는 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 인스턴스에 정의된 계정 유형을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="a6a11-110">The following table lists the account types that are defined on an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance.</span></span>  
  
|<span data-ttu-id="a6a11-111">값</span><span class="sxs-lookup"><span data-stu-id="a6a11-111">Value</span></span>|<span data-ttu-id="a6a11-112">Description</span><span class="sxs-lookup"><span data-stu-id="a6a11-112">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="a6a11-113">**자산**</span><span class="sxs-lookup"><span data-stu-id="a6a11-113">**Asset**</span></span>|<span data-ttu-id="a6a11-114">특정 시간에 소유하고 있는 항목의 가치입니다.</span><span class="sxs-lookup"><span data-stu-id="a6a11-114">Value of things owned at a specific time.</span></span>|  
|<span data-ttu-id="a6a11-115">**Balance**</span><span class="sxs-lookup"><span data-stu-id="a6a11-115">**Balance**</span></span>|<span data-ttu-id="a6a11-116">특정 시간의 항목 합계입니다.</span><span class="sxs-lookup"><span data-stu-id="a6a11-116">Count of something at a specific time.</span></span>|  
|<span data-ttu-id="a6a11-117">**Expense**</span><span class="sxs-lookup"><span data-stu-id="a6a11-117">**Expense**</span></span>|<span data-ttu-id="a6a11-118">지출한 비용입니다.</span><span class="sxs-lookup"><span data-stu-id="a6a11-118">Value of things spent.</span></span>|  
|<span data-ttu-id="a6a11-119">**흐름**</span><span class="sxs-lookup"><span data-stu-id="a6a11-119">**Flow**</span></span>|<span data-ttu-id="a6a11-120">항목의 증분 합계입니다.</span><span class="sxs-lookup"><span data-stu-id="a6a11-120">Incremental count of things.</span></span>|  
|<span data-ttu-id="a6a11-121">**Income**</span><span class="sxs-lookup"><span data-stu-id="a6a11-121">**Income**</span></span>|<span data-ttu-id="a6a11-122">받은 항목의 가치입니다.</span><span class="sxs-lookup"><span data-stu-id="a6a11-122">Value of things received.</span></span>|  
|<span data-ttu-id="a6a11-123">**Liability**</span><span class="sxs-lookup"><span data-stu-id="a6a11-123">**Liability**</span></span>|<span data-ttu-id="a6a11-124">특정 시간에 진 빚의 가치입니다.</span><span class="sxs-lookup"><span data-stu-id="a6a11-124">Value of things owed at a specific time.</span></span>|  
|<span data-ttu-id="a6a11-125">**통계**</span><span class="sxs-lookup"><span data-stu-id="a6a11-125">**Statistical**</span></span>|<span data-ttu-id="a6a11-126">항목의 계산된 비율 또는 집계되지 않는 항목의 합계입니다.</span><span class="sxs-lookup"><span data-stu-id="a6a11-126">Calculated ratio of something, or count of something that does not aggregate.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a6a11-127">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a6a11-127">See Also</span></span>  
 <span data-ttu-id="a6a11-128">[비즈니스 인텔리전스 마법사 F1 도움말](business-intelligence-wizard-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="a6a11-128">[Business Intelligence Wizard F1 Help](business-intelligence-wizard-f1-help.md) </span></span>  
 <span data-ttu-id="a6a11-129">[큐브 디자이너 &#40;Analysis Services 다차원 데이터&#41;](cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="a6a11-129">[Cube Designer &#40;Analysis Services - Multidimensional Data&#41;](cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="a6a11-130">차원 디자이너 &#40;Analysis Services 다차원 데이터&#41;</span><span class="sxs-lookup"><span data-stu-id="a6a11-130">Dimension Designer &#40;Analysis Services - Multidimensional Data&#41;</span></span>](dimension-designer-analysis-services-multidimensional-data.md)  
  
  
