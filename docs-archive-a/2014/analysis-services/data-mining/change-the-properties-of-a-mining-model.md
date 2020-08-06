---
title: 마이닝 모델의 속성 변경 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining models [Analysis Services], properties
- properties [data mining]
ms.assetid: aefaeb7f-d174-48d1-a188-0987a3b1196b
author: minewiskan
ms.author: owend
ms.openlocfilehash: 395e6a4cb9c0f0dac0f0c717dfe0695033cad050
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646726"
---
# <a name="change-the-properties-of-a-mining-model"></a><span data-ttu-id="f7278-102">마이닝 모델의 속성 변경</span><span class="sxs-lookup"><span data-stu-id="f7278-102">Change the Properties of a Mining Model</span></span>
  <span data-ttu-id="f7278-103">일부 마이닝 모델 속성은 모델 전체에 적용되고 다른 모델 속성은 개별 열에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="f7278-103">Some mining model properties apply to the model as a whole, and other model properties apply to individual columns.</span></span> <span data-ttu-id="f7278-104">모델 전체에 적용되는 속성의 예로는 사례 데이터를 쿼리에 사용할지 여부를 지정하는 `Drillthrough` 속성과 `Description` 속성이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7278-104">Examples of properties that apply to the entire model would be the `Drillthrough` property, which specifies whether the case data should be available for querying, and the `Description` property.</span></span> <span data-ttu-id="f7278-105">열에 적용되는 속성으로는 모델 내에서 열의 데이터가 사용되는 방식을 제어하는 `Usage` 및 `ModelingFlags`가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7278-105">Properties that apply to the column include `Usage` and `ModelingFlags`, which control how data in the column is used within the model.</span></span>  
  
 <span data-ttu-id="f7278-106">다음 모델 속성의 경우 식을 만들거나 복잡한 모델 속성을 구성하는 데 사용할 수 있는 고급 편집기가</span><span class="sxs-lookup"><span data-stu-id="f7278-106">The following model properties have advanced editors that you can use to create expressions or configure complex model properties.</span></span> <span data-ttu-id="f7278-107">제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="f7278-107">The following properties provide:</span></span>  
  
-   <span data-ttu-id="f7278-108">`Filter`속성: [데이터 집합 필터 또는 모델 필터 대화 상자](../data-set-filter-or-model-filter-dialog-box.md)를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="f7278-108">`Filter` property: Opens the [Data Set Filter or Model Filter Dialog Box](../data-set-filter-or-model-filter-dialog-box.md).</span></span>  
  
-   <span data-ttu-id="f7278-109">`AlgorithmParameters`속성: [마이닝 모델 뷰&#41;&#40;알고리즘 매개 변수 대화 상자 ](../algorithm-parameters-dialog-box-mining-models-view.md)를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="f7278-109">`AlgorithmParameters` property: Opens the [Algorithm Parameters Dialog Box &#40;Mining Models View&#41;](../algorithm-parameters-dialog-box-mining-models-view.md).</span></span>  
  
 <span data-ttu-id="f7278-110">마이닝 모델의 속성을 설정하는 방법은 [마이닝 모델 열](mining-model-columns.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f7278-110">For information about how to set the properties in a mining model, see [Mining Model Columns](mining-model-columns.md).</span></span>  
  
### <a name="to-change-the-properties-of-a-mining-model"></a><span data-ttu-id="f7278-111">마이닝 모델의 속성을 변경하려면</span><span class="sxs-lookup"><span data-stu-id="f7278-111">To change the properties of a mining model</span></span>  
  
1.  <span data-ttu-id="f7278-112">데이터 마이닝 디자이너의 **마이닝 모델** 탭에서 마이닝 모델의 이름이 포함된 열 머리글 또는 마이닝 알고리즘의 이름이 포함된 표의 행을 마우스 오른쪽 단추로 클릭한 다음 **속성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f7278-112">In the **Mining Models** tab in Data Mining Designer, right-click either the column header that contains the name of the mining model, or the row in the grid that contains the name of the mining algorithm, and then select **Properties**.</span></span>  
  
2.  <span data-ttu-id="f7278-113">화면 오른쪽에 있는 **속성** 창에서 변경할 속성에 해당하는 값을 강조 표시하고 새 값을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="f7278-113">In the **Properties** window on the right side of the screen, highlight the value that corresponds to the property that you want to change, and enter the new value.</span></span>  
  
     <span data-ttu-id="f7278-114">디자이너에서 다른 요소를 선택하면 새 값이 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="f7278-114">The new value will take effect when you select a different element in the designer.</span></span>  
  
### <a name="to-change-the-properties-of-a-mining-model-column"></a><span data-ttu-id="f7278-115">마이닝 모델 열의 속성을 변경하려면</span><span class="sxs-lookup"><span data-stu-id="f7278-115">To change the properties of a mining model column</span></span>  
  
1.  <span data-ttu-id="f7278-116">데이터 마이닝 디자이너의 **마이닝 모델** 탭에서 마이닝 구조 열과 마이닝 모델이 교차하는 지점에 있는 표의 셀을 마우스 오른쪽 단추로 클릭한 다음 **속성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f7278-116">In the **Mining Models** tab in Data Mining Designer, right-click the cell in the grid at the intersection of the mining structure column and the mining model, and then select **Properties**.</span></span>  
  
2.  <span data-ttu-id="f7278-117">화면 오른쪽에 있는 **속성** 창에서 변경할 속성에 해당하는 값을 강조 표시하고 새 값을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="f7278-117">In the **Properties** window on the right side of the screen, highlight the value that corresponds to the property that you want to change, and enter the new value.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="f7278-118">열 사용법을로 설정 하면 해당 `Ignore` 열에 대 한 **속성** 창이 비어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7278-118">If the column usage is set to `Ignore`, the **Properties** window for the column is blank.</span></span>  
  
     <span data-ttu-id="f7278-119">디자이너에서 다른 요소를 선택하면 새 값이 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="f7278-119">The new value will take effect when you select a different element in the designer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7278-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f7278-120">See Also</span></span>  
 [<span data-ttu-id="f7278-121">마이닝 모델 태스크 및 방법</span><span class="sxs-lookup"><span data-stu-id="f7278-121">Mining Model Tasks and How-tos</span></span>](mining-model-tasks-and-how-tos.md)  
  
  
