---
title: 기존 개체의 데이터 원본 (데이터 원본 마법사) (Analysis Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.datasourcewizard.specifyobject.f1
ms.assetid: e6ef6dea-9db8-45c4-8959-f9febd7caf7b
author: minewiskan
ms.author: owend
ms.openlocfilehash: 621c938f4902c95dee1e2fcccb0f292597a565f1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87733283"
---
# <a name="data-sources-from-existing-objects-data-source-wizard-analysis-services"></a><span data-ttu-id="f1834-102">기존 개체의 데이터 원본(데이터 원본 마법사)(Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="f1834-102">Data sources from existing objects (Data Source Wizard) (Analysis Services)</span></span>
  <span data-ttu-id="f1834-103">**기존 개체의 데이터 원본** 페이지를 사용하여 새 데이터 원본의 기반으로 사용할 기존 데이터 원본 또는 프로젝트를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f1834-103">Use the **Data sources from existing objects** page to specify an existing data source or project on which to base the new data source.</span></span>  
  
## <a name="options"></a><span data-ttu-id="f1834-104">옵션</span><span class="sxs-lookup"><span data-stu-id="f1834-104">Options</span></span>  
 <span data-ttu-id="f1834-105">**솔루션의 기존 데이터 원본을 사용하여 데이터 원본 만들기**</span><span class="sxs-lookup"><span data-stu-id="f1834-105">**Create a data source based on an existing data source in your solution**</span></span>  
 <span data-ttu-id="f1834-106">솔루션의 기존 데이터 원본을 기반으로 새 데이터 원본을 만들려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f1834-106">Select to base the new data source on an existing data source in the solution.</span></span> <span data-ttu-id="f1834-107">새 데이터 원본을 사용하는 프로젝트를 작성 또는 배포하거나 새로 고치면 새 데이터 원본은 이 옵션을 선택할 때 지정한 데이터 원본에서 설정을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="f1834-107">When a project that uses the new data source is built, refreshed, or deployed, the new data source acquires the settings from the data source you specify when you select this option.</span></span>  
  
 <span data-ttu-id="f1834-108">**데이터 원본**</span><span class="sxs-lookup"><span data-stu-id="f1834-108">**Data source**</span></span>  
 <span data-ttu-id="f1834-109">프로젝트별로 그룹화된 데이터 원본 목록에서 새 데이터 원본의 기반으로 사용할 데이터 원본을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f1834-109">Select a data source on which you want to base the new data source from the list of data sources, which is grouped by project.</span></span>  
  
 <span data-ttu-id="f1834-110">**Analysis Services 프로젝트를 기반으로 데이터 원본 만들기**</span><span class="sxs-lookup"><span data-stu-id="f1834-110">**Create a data source based on an Analysis Services project**</span></span>  
 <span data-ttu-id="f1834-111">현재 솔루션의 다른 프로젝트를 참조 하는 새 데이터 원본을 만들려면 선택 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1834-111">Select to create a new data source that references another [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] project in the current solution.</span></span> <span data-ttu-id="f1834-112">새 데이터 원본은 선택한 프로젝트의 `TargetServer` 및 `TargetDatabase` 속성에서 설정을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="f1834-112">The new data source acquires settings from the `TargetServer` and `TargetDatabase` properties of the selected project.</span></span> <span data-ttu-id="f1834-113">새 데이터 원본을 사용하는 프로젝트를 작성 또는 배포하거나 새로 고치면 새 데이터 원본은 이 옵션을 선택할 때 지정한 데이터 원본에서 설정을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="f1834-113">When a project that uses the new data source is built, refreshed, or deployed, the new data source acquires settings from the data source you specify when you select this option.</span></span>  
  
 <span data-ttu-id="f1834-114">**프로젝트**</span><span class="sxs-lookup"><span data-stu-id="f1834-114">**Project**</span></span>  
 <span data-ttu-id="f1834-115">새 데이터 원본에서 참조할 프로젝트를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f1834-115">Select the project that you want to reference in the new data source.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1834-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f1834-116">See Also</span></span>  
 <span data-ttu-id="f1834-117">[데이터 원본 마법사 F1 도움말 &#40;Analysis Services&#41;](data-source-wizard-f1-help-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="f1834-117">[Data Source Wizard F1 Help &#40;Analysis Services&#41;](data-source-wizard-f1-help-analysis-services.md) </span></span>  
 <span data-ttu-id="f1834-118">[다차원 모델의 데이터 원본](multidimensional-models/data-sources-in-multidimensional-models.md) </span><span class="sxs-lookup"><span data-stu-id="f1834-118">[Data Sources in Multidimensional Models](multidimensional-models/data-sources-in-multidimensional-models.md) </span></span>  
 [<span data-ttu-id="f1834-119">SSAS 다차원&#41;&#40;지원 되는 데이터 원본</span><span class="sxs-lookup"><span data-stu-id="f1834-119">Data Sources Supported &#40;SSAS Multidimensional&#41;</span></span>](multidimensional-models/supported-data-sources-ssas-multidimensional.md)  
  
  
