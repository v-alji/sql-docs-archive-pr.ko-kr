---
title: 데이터 마이닝 구조 만들기 (데이터 마이닝 마법사) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.dmwizard.selectminingtechnique.f1
ms.assetid: d1ff17b2-fff3-4ed7-a5d6-42d131e59f93
author: minewiskan
ms.author: owend
ms.openlocfilehash: c9f738cff974bc0064fc9e93c86221f0b10c6e80
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649860"
---
# <a name="create-the-data-mining-structure-data-mining-wizard"></a><span data-ttu-id="6e5a7-102">데이터 마이닝 구조 만들기(데이터 마이닝 마법사)</span><span class="sxs-lookup"><span data-stu-id="6e5a7-102">Create the Data Mining Structure (Data Mining Wizard)</span></span>
  <span data-ttu-id="6e5a7-103">**데이터 마이닝 구조 만들기** 페이지를 사용하여 데이터 마이닝 구조를 만들고 선택적으로 연결된 마이닝 모델을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6e5a7-103">Use the **Create the Data Mining Structure** page to create a data mining structure and optionally create an associated mining model.</span></span>  
  
 <span data-ttu-id="6e5a7-104">마이닝 모델을 만들도록 선택한 경우 사용할 데이터 마이닝 알고리즘도 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6e5a7-104">If you choose to create a mining model, you must also specify the data mining algorithm that you want to use.</span></span> <span data-ttu-id="6e5a7-105">지금은 구조만 만들고 나중에 이 구조에 마이닝 모델을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6e5a7-105">If you create only the structure now, you can add a mining model to the structure later.</span></span>  
  
 <span data-ttu-id="6e5a7-106">**자세한 내용:** [데이터 마이닝 알고리즘&#40;Analysis Services - 데이터 마이닝&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md), [데이터 마이닝 마법사&#40;Analysis Services - 데이터 마이닝&#41;](data-mining/data-mining-wizard-analysis-services-data-mining.md), [관계형 마이닝 구조 만들기](data-mining/create-a-relational-mining-structure.md)</span><span class="sxs-lookup"><span data-stu-id="6e5a7-106">**For More Information:** [Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md), [Data Mining Wizard &#40;Analysis Services - Data Mining&#41;](data-mining/data-mining-wizard-analysis-services-data-mining.md), [Create a Relational Mining Structure](data-mining/create-a-relational-mining-structure.md)</span></span>  
  
## <a name="options"></a><span data-ttu-id="6e5a7-107">옵션</span><span class="sxs-lookup"><span data-stu-id="6e5a7-107">Options</span></span>  
 <span data-ttu-id="6e5a7-108">**마이닝 모델이 포함된 마이닝 구조 만들기**</span><span class="sxs-lookup"><span data-stu-id="6e5a7-108">**Create mining structure with a mining model**</span></span>  
 <span data-ttu-id="6e5a7-109">마이닝 구조를 만들려면 선택한 다음 연결된 모델을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="6e5a7-109">Select to create a mining structure and then create an associated model.</span></span>  
  
 <span data-ttu-id="6e5a7-110">**사용할 데이터 마이닝 기술 선택**</span><span class="sxs-lookup"><span data-stu-id="6e5a7-110">**Which data mining technique do you want to use?**</span></span>  
 <span data-ttu-id="6e5a7-111">이 모델에 사용할 데이터 마이닝 알고리즘을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6e5a7-111">Select the data mining algorithm to use with this model.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6e5a7-112">알고리즘 목록은 마이닝 구조를 만드는 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 인스턴스에서 채워집니다.</span><span class="sxs-lookup"><span data-stu-id="6e5a7-112">The list of algorithms is populated from the instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] on which you are creating the mining structure.</span></span> <span data-ttu-id="6e5a7-113">서버를 사용할 수 없는 경우에는 기본 알고리즘만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6e5a7-113">If the server is not available, only the default algorithms will be available.</span></span>  
  
 <span data-ttu-id="6e5a7-114">**모델을 포함하지 않는 마이닝 구조 만들기**</span><span class="sxs-lookup"><span data-stu-id="6e5a7-114">**Create mining structure with no models**</span></span>  
 <span data-ttu-id="6e5a7-115">마이닝 구조만 만들려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6e5a7-115">Select to create only a mining structure.</span></span>  
  
 <span data-ttu-id="6e5a7-116">**설명**</span><span class="sxs-lookup"><span data-stu-id="6e5a7-116">**Description**</span></span>  
 <span data-ttu-id="6e5a7-117">선택한 알고리즘에 대한 설명을 표시합니다</span><span class="sxs-lookup"><span data-stu-id="6e5a7-117">Displays a description of the selected algorithm.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e5a7-118">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6e5a7-118">See Also</span></span>  
 <span data-ttu-id="6e5a7-119">[데이터 마이닝 마법사 F1 도움말 &#40;Analysis Services 데이터 마이닝&#41;](data-mining-wizard-f1-help-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="6e5a7-119">[Data Mining Wizard F1 Help &#40;Analysis Services - Data Mining&#41;](data-mining-wizard-f1-help-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="6e5a7-120">[데이터 마이닝 마법사 &#40;데이터 원본 뷰를 선택&#41;](select-data-source-view-data-mining-wizard.md) </span><span class="sxs-lookup"><span data-stu-id="6e5a7-120">[Select Data Source View &#40;Data Mining Wizard&#41;](select-data-source-view-data-mining-wizard.md) </span></span>  
 [<span data-ttu-id="6e5a7-121">데이터 마이닝 마법사 &#40;정의 메서드를 선택&#41;</span><span class="sxs-lookup"><span data-stu-id="6e5a7-121">Select the Definition Method &#40;Data Mining Wizard&#41;</span></span>](select-the-definition-method-data-mining-wizard.md)  
  
  
