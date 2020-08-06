---
title: 마이닝 모델에서 필터 삭제 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- filters [Analysis Services]
ms.assetid: 91220b21-adbc-49a9-b200-8bf0a724eff1
author: minewiskan
ms.author: owend
ms.openlocfilehash: 404c23c0e55bffba2ce8410c9c30d6ad1fa1991b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647324"
---
# <a name="delete-a-filter-from-a-mining-model"></a><span data-ttu-id="5b3f9-102">마이닝 모델에서 필터 삭제</span><span class="sxs-lookup"><span data-stu-id="5b3f9-102">Delete a Filter from a Mining Model</span></span>
  <span data-ttu-id="5b3f9-103">마이닝 모델에 대한 필터를 정의할 때 데이터 원본 뷰에서 데이터의 하위 집합에 대한 모델을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5b3f9-103">When you create a filter on a mining model, you can create models on a subset of the data in the data source view.</span></span> <span data-ttu-id="5b3f9-104">필터는 원래 데이터의 하위 집합에 대한 모델의 정확도를 테스트하는 데에도 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="5b3f9-104">Filters are also useful for testing the accuracy of the model on a subset of the original data.</span></span>  
  
 <span data-ttu-id="5b3f9-105">그러나 전체 사례 집합을 다시 보려면 필터를 삭제해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5b3f9-105">However, you must delete the filter if you want to view the complete set of cases again.</span></span> <span data-ttu-id="5b3f9-106">이 절차에서는 필터에서 조건을 제거하거나 필터를 완전히 삭제하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="5b3f9-106">This procedure describes how to remove conditions on a filter, or delete the filter completely.</span></span>  
  
### <a name="to-delete-a-condition-from-a-filter-on-a-mining-model"></a><span data-ttu-id="5b3f9-107">마이닝 모델의 필터에서 조건을 삭제하려면</span><span class="sxs-lookup"><span data-stu-id="5b3f9-107">To delete a condition from a filter on a mining model</span></span>  
  
1.  <span data-ttu-id="5b3f9-108">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]의 솔루션 탐색기에서 필터링할 마이닝 모델이 포함된 마이닝 구조를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5b3f9-108">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], in Solution Explorer, click the mining structure that contains the mining model you want to filter.</span></span>  
  
2.  <span data-ttu-id="5b3f9-109">**마이닝 모델** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5b3f9-109">Click the **Mining Models** tab.</span></span>  
  
3.  <span data-ttu-id="5b3f9-110">모델을 선택하고 마우스 오른쪽 단추를 클릭하여 바로 가기 메뉴를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="5b3f9-110">Select the model, and right-click to open the shortcut menu.</span></span>  
  
     <span data-ttu-id="5b3f9-111">또는</span><span class="sxs-lookup"><span data-stu-id="5b3f9-111">-or-</span></span>  
  
     <span data-ttu-id="5b3f9-112">모델을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="5b3f9-112">Select the model.</span></span> <span data-ttu-id="5b3f9-113">**마이닝 모델** 메뉴에서 **모델 필터 설정**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="5b3f9-113">On the **Mining Model** menu, select **Set Model Filter**.</span></span>  
  
4.  <span data-ttu-id="5b3f9-114">**모델 필터** 대화 상자에서 삭제할 조건이 포함된 표의 행을 마우스 오른쪽 단추로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5b3f9-114">In the **Model Filter** dialog box, right-click the row in the grid that contains the condition you want to delete.</span></span>  
  
5.  <span data-ttu-id="5b3f9-115">**삭제**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="5b3f9-115">Select **Delete**.</span></span>  
  
### <a name="to-clear-the-filter-on-a-mining-model-in-the-filter-editor-dialog-box"></a><span data-ttu-id="5b3f9-116">필터 편집기 대화 상자에서 마이닝 모델의 필터를 지우려면</span><span class="sxs-lookup"><span data-stu-id="5b3f9-116">To clear the filter on a mining model in the Filter Editor dialog box</span></span>  
  
-   <span data-ttu-id="5b3f9-117">**필터 편집기** 대화 상자에서 표의 아무 행이나 마우스 오른쪽 단추로 클릭하고 **모두 삭제**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="5b3f9-117">In the **Filter Editor** dialog box, right-click any row in the grid, and select **Delete All**.</span></span>  
  
## <a name="working-with-model-filters-using-the-properties-window"></a><span data-ttu-id="5b3f9-118">속성 창을 사용하여 모델 필터 작업</span><span class="sxs-lookup"><span data-stu-id="5b3f9-118">Working with Model Filters Using the Properties Window</span></span>  
 <span data-ttu-id="5b3f9-119">전체 필터를 삭제하는 경우에는 필터 편집기 대화 상자를 열지 않아도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5b3f9-119">If you want to delete the whole filter, you do not need to open the filter editor dialog boxes.</span></span> <span data-ttu-id="5b3f9-120">만든 필터 조건은 마이닝 모델의 `Filter` 속성에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5b3f9-120">The filter conditions that you created are available in the `Filter` property of the mining model.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5b3f9-121">마이닝 모델의 속성은 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]에서는 볼 수 있지만 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서는 볼 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5b3f9-121">You can view the properties of a mining model in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], but not in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
#### <a name="to-clear-the-filter-on-a-mining-model-in-solution-explorer"></a><span data-ttu-id="5b3f9-122">솔루션 탐색기에서 마이닝 모델의 필터를 지우려면</span><span class="sxs-lookup"><span data-stu-id="5b3f9-122">To clear the filter on a mining model in Solution Explorer</span></span>  
  
1.  <span data-ttu-id="5b3f9-123">솔루션 탐색기에서 필터가 포함된 마이닝 모델을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5b3f9-123">In Solution Explorer, click the mining model that contains the filter.</span></span>  
  
2.  <span data-ttu-id="5b3f9-124">**속성** 창에서 속성의 필터 텍스트를 마우스 오른쪽 단추로 클릭 `Filter` 하 고 **모두 선택**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="5b3f9-124">In the **Properties** window, right-click the filter text in the `Filter` property, and select **Select All**.</span></span>  
  
3.  <span data-ttu-id="5b3f9-125">백스페이스 또는 Delete 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="5b3f9-125">Press the Backspace or Delete key.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b3f9-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5b3f9-126">See Also</span></span>  
 <span data-ttu-id="5b3f9-127">[마이닝 모델에서 사례 데이터로 드릴스루](drill-through-to-case-data-from-a-mining-model.md) </span><span class="sxs-lookup"><span data-stu-id="5b3f9-127">[Drill Through to Case Data from a Mining Model](drill-through-to-case-data-from-a-mining-model.md) </span></span>  
 <span data-ttu-id="5b3f9-128">[마이닝 모델 태스크 및 방법](mining-model-tasks-and-how-tos.md) </span><span class="sxs-lookup"><span data-stu-id="5b3f9-128">[Mining Model Tasks and How-tos](mining-model-tasks-and-how-tos.md) </span></span>  
 [<span data-ttu-id="5b3f9-129">마이닝 모델에 대한 필터&#40;Analysis Services - 데이터 마이닝&#41;</span><span class="sxs-lookup"><span data-stu-id="5b3f9-129">Filters for Mining Models &#40;Analysis Services - Data Mining&#41;</span></span>](mining-models-analysis-services-data-mining.md)  
  
  
