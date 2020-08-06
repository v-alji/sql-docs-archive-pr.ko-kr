---
title: 알고리즘 매개 변수 대화 상자 (마이닝 모델 뷰) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.models.algorithmparameters.f1
helpviewer_keywords:
- Algorithm Parameters dialog box
ms.assetid: 57f9f6f8-8ca4-4a6e-8f18-85f0571b7060
author: minewiskan
ms.author: owend
ms.openlocfilehash: 303d8b5bd3437690c65873e106a94cf2ce8eb9f0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648218"
---
# <a name="algorithm-parameters-dialog-box-mining-models-view"></a><span data-ttu-id="0c59a-102">알고리즘 매개 변수 대화 상자(마이닝 모델 뷰)</span><span class="sxs-lookup"><span data-stu-id="0c59a-102">Algorithm Parameters Dialog Box (Mining Models View)</span></span>
  <span data-ttu-id="0c59a-103">**알고리즘 매개 변수** 대화 상자를 사용하여 선택한 모델에 해당하는 알고리즘 매개 변수를 조정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0c59a-103">Use the **Algorithm Parameters** dialog box to adjust algorithm parameters that are specific to the selected model.</span></span> <span data-ttu-id="0c59a-104">알고리즘 매개 변수를 변경하면 항상 마이닝 모델의 결과가 변경됩니다.</span><span class="sxs-lookup"><span data-stu-id="0c59a-104">When you change an algorithm parameter, you will usually change the results of the mining model.</span></span> <span data-ttu-id="0c59a-105">각 매개 변수가 결과에 영향을 미치는 방식은 사용 중인 알고리즘과 데이터에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="0c59a-105">The way that each parameter affects the results depends on the algorithm you are using, and on your data.</span></span> <span data-ttu-id="0c59a-106">자세한 내용은 [마이닝 모델 및 구조 사용자 지정](data-mining/customize-mining-models-and-structure.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0c59a-106">For more information, see [Customize Mining Models and Structure](data-mining/customize-mining-models-and-structure.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="0c59a-107">옵션</span><span class="sxs-lookup"><span data-stu-id="0c59a-107">Options</span></span>  
 <span data-ttu-id="0c59a-108">**매개 변수**</span><span class="sxs-lookup"><span data-stu-id="0c59a-108">**Parameters**</span></span>  
 <span data-ttu-id="0c59a-109">선택한 마이닝 모델에 사용할 수 있는 매개 변수를 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="0c59a-109">Lists the parameters that are available for the selected mining model.</span></span>  
  
 <span data-ttu-id="0c59a-110">다음 목록에서는 사용 가능한 열에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="0c59a-110">The following list describes the available columns.</span></span>  
  
|<span data-ttu-id="0c59a-111">열</span><span class="sxs-lookup"><span data-stu-id="0c59a-111">Column</span></span>|<span data-ttu-id="0c59a-112">Description</span><span class="sxs-lookup"><span data-stu-id="0c59a-112">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="0c59a-113">**매개 변수**</span><span class="sxs-lookup"><span data-stu-id="0c59a-113">**Parameter**</span></span>|<span data-ttu-id="0c59a-114">매개 변수의 이름을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="0c59a-114">List the name of the parameter.</span></span>|  
|<span data-ttu-id="0c59a-115">**값**</span><span class="sxs-lookup"><span data-stu-id="0c59a-115">**Value**</span></span>|<span data-ttu-id="0c59a-116">매개 변수의 기본값을 변경하려는 경우에만 값을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="0c59a-116">Enter a value only if you want to change the default value of the parameter.</span></span>|  
|<span data-ttu-id="0c59a-117">**기본값**</span><span class="sxs-lookup"><span data-stu-id="0c59a-117">**Default**</span></span>|<span data-ttu-id="0c59a-118">**값** 열에 값을 입력하지 않은 경우 알고리즘에서 사용할 매개 변수의 기본값을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="0c59a-118">List the default value of the parameter that the algorithm will use if you do not supply a value in the **Value** column.</span></span>|  
|<span data-ttu-id="0c59a-119">**Range**</span><span class="sxs-lookup"><span data-stu-id="0c59a-119">**Range**</span></span>|<span data-ttu-id="0c59a-120">**값** 열에 입력할 수 있는 값의 범위를 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="0c59a-120">List the range of possible values that you can enter into the **Value** column.</span></span> <span data-ttu-id="0c59a-121">범위는 다음 중 하나일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0c59a-121">The ranges can be one of the following:</span></span><br /><br /> <span data-ttu-id="0c59a-122">1, 2, 3과 같은 불연속 목록</span><span class="sxs-lookup"><span data-stu-id="0c59a-122">A discrete list, such as 1, 2, 3</span></span><br /><br /> <span data-ttu-id="0c59a-123">[0, 100]와 같은 포함 범위</span><span class="sxs-lookup"><span data-stu-id="0c59a-123">An inclusive range, such as [0, 100]</span></span><br /><br /> <span data-ttu-id="0c59a-124">(0,...)와 같은 배타적 범위</span><span class="sxs-lookup"><span data-stu-id="0c59a-124">An exclusive range, such as (0,...)</span></span><br /><br /> <span data-ttu-id="0c59a-125">[0,...)와 같은 조합</span><span class="sxs-lookup"><span data-stu-id="0c59a-125">A combination, such as [0,...)</span></span>|  
  
 <span data-ttu-id="0c59a-126">**설명**</span><span class="sxs-lookup"><span data-stu-id="0c59a-126">**Description**</span></span>  
 <span data-ttu-id="0c59a-127">**매개 변수** 목록에서 선택한 매개 변수에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="0c59a-127">Describes the selected parameter in the **Parameters** list.</span></span>  
  
 <span data-ttu-id="0c59a-128">**추가**</span><span class="sxs-lookup"><span data-stu-id="0c59a-128">**Add**</span></span>  
 <span data-ttu-id="0c59a-129">목록에 알고리즘 특정 매개 변수를 추가하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0c59a-129">Click to add additional, algorithm specific-parameters to the list.</span></span> <span data-ttu-id="0c59a-130">매개 변수를 추가한 다음에는 **매개 변수** 열에 올바른 이름을 입력하고 **값** 열에 값을 입력할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0c59a-130">After adding the parameter, you can enter the correct name in the **Parameter** column and provide a value in the **Value** column.</span></span>  
  
 <span data-ttu-id="0c59a-131">**제거**</span><span class="sxs-lookup"><span data-stu-id="0c59a-131">**Remove**</span></span>  
 <span data-ttu-id="0c59a-132">목록에서 사용자 지정 매개 변수를 삭제하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0c59a-132">Click to delete a custom parameter from the list.</span></span>  
  
 <span data-ttu-id="0c59a-133">목록에서 표준 Analysis Services 알고리즘 매개 변수 중 하나를 삭제하는 경우에도 매개 변수가 계속 모델에 사용되지만 해당 매개 변수의 기본값으로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="0c59a-133">If you delete one of the standard Analysis Services algorithm parameters from the list, the parameter will still be used in the model, but with the default values for that parameter.</span></span> <span data-ttu-id="0c59a-134">매개 변수는 영구적으로 삭제되지 않으며 다음에 대화 상자를 열면 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="0c59a-134">The parameter is not permanently deleted and will appear the next time that you open the dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c59a-135">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0c59a-135">See Also</span></span>  
 <span data-ttu-id="0c59a-136">[데이터 마이닝 알고리즘 &#40;Analysis Services 데이터 마이닝&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="0c59a-136">[Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="0c59a-137">[마이닝 모델 뷰 &#40;데이터 마이닝 모델 디자이너&#41;](mining-models-view-data-mining-model-designer.md) </span><span class="sxs-lookup"><span data-stu-id="0c59a-137">[Mining Models View &#40;Data Mining Model Designer&#41;](mining-models-view-data-mining-model-designer.md) </span></span>  
 [<span data-ttu-id="0c59a-138">데이터 마이닝 개체 이동</span><span class="sxs-lookup"><span data-stu-id="0c59a-138">Moving Data Mining Objects</span></span>](data-mining/moving-data-mining-objects.md)  
  
  
