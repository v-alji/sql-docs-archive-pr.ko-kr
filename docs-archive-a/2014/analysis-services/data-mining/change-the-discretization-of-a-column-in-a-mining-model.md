---
title: 마이닝 모델에서 열의 불연속화 변경 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- discretization [Analysis Services]
- mining structures [Analysis Services], how-to topics
- discretized columns [data mining]
- bucketing problems [Analysis Services]
ms.assetid: 3c49862b-595d-4fa4-b890-e2e1bde1d74f
author: minewiskan
ms.author: owend
ms.openlocfilehash: 25b20d6428afac5c1492fdc74aafd4d0c010159d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659742"
---
# <a name="change-the-discretization-of-a-column-in-a-mining-model"></a><span data-ttu-id="89160-102">마이닝 모델에서 열의 분할 변경</span><span class="sxs-lookup"><span data-stu-id="89160-102">Change the Discretization of a Column in a Mining Model</span></span>
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]<span data-ttu-id="89160-103">자동으로 값을 불연속화 합니다. 즉, 특정 시나리오에서 숫자 열의 데이터를 bin으로 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="89160-103">automatically discretizes values-that is to say, it bins data in numeric column-in certain scenarios.</span></span> <span data-ttu-id="89160-104">예를 들어 데이터에 연속 숫자 데이터가 포함되고 있고 의사 결정 트리 모델을 만드는 경우 데이터의 배포에 따라 연속 데이터의 각 열이 자동으로 범주화됩니다.</span><span class="sxs-lookup"><span data-stu-id="89160-104">For example, if your data contains continuous numeric data and you create a decision tree model, each column of continuous data will be automatically binned, depending on the distribution of the data.</span></span> <span data-ttu-id="89160-105">데이터가 불연속화되는 방법을 제어하려면 모델에서 데이터가 사용되는 방법을 제어하는 마이닝 구조 열의 속성을 변경해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="89160-105">If you want to control how the data is discretized, you must change the properties on the mining structure column that control how the data is used in the model.</span></span>  
  
 <span data-ttu-id="89160-106">마이닝 모델의 속성을 설정하는 방법에 대한 일반적인 내용은 [마이닝 모델 열](mining-model-columns.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="89160-106">For general information about how to set the properties in a mining model, see [Mining Model Columns](mining-model-columns.md).</span></span>  
  
### <a name="to-display-the-properties-for-a-mining-model-column"></a><span data-ttu-id="89160-107">마이닝 모델 열의 속성을 표시하려면</span><span class="sxs-lookup"><span data-stu-id="89160-107">To display the properties for a mining model column</span></span>  
  
1.  <span data-ttu-id="89160-108">데이터 마이닝 디자이너의 **마이닝 모델** 탭에서 마이닝 모델의 이름이 포함된 열 머리글 또는 마이닝 알고리즘의 이름이 포함된 표의 행을 마우스 오른쪽 단추로 클릭한 다음 **속성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="89160-108">In the **Mining Models** tab in Data Mining Designer, right-click the column header that contains the name of the mining model, or the row in the grid that contains the name of the mining algorithm, and then select **Properties**.</span></span>  
  
     <span data-ttu-id="89160-109">**속성** 창에 마이닝 모델과 연관된 모든 속성이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="89160-109">The **Properties** window displays the properties that are associated with the mining model as a whole.</span></span>  
  
2.  <span data-ttu-id="89160-110">화면 왼쪽에 가까이 있는 **구조** 열에서 불연속화하려는 연속 숫자 데이터가 포함된 열을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="89160-110">In the **Structure** column near the left side of the screen, click the column that contains the continuous numeric data you want to discretize.</span></span>  
  
     <span data-ttu-id="89160-111">**속성** 창에 선택한 열과 연관된 속성만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="89160-111">The **Properties** window changes to display just the properties associated with that column.</span></span>  
  
### <a name="to-change-the-discretization-method"></a><span data-ttu-id="89160-112">분할 메서드를 변경하려면</span><span class="sxs-lookup"><span data-stu-id="89160-112">To change the discretization method</span></span>  
  
1.  <span data-ttu-id="89160-113">**마이닝 속성** 창에서 **내용**옆에 있는 입력란을 클릭 하 고 `Discretized` 드롭다운 목록에서를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="89160-113">In the **Mining Properties** window, click the text box next to **Content**, and select `Discretized` from the dropdown list.</span></span>  
  
     <span data-ttu-id="89160-114">이제 <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn.DiscretizationBucketCount%2A> 및 <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn.DiscretizationMethod%2A> 속성을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="89160-114">The <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn.DiscretizationBucketCount%2A> and <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn.DiscretizationMethod%2A> properties are now enabled.</span></span>  
  
2.  <span data-ttu-id="89160-115">**속성** 창에서 옆의 텍스트 상자를 클릭 하 <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn.DiscretizationMethod%2A> 고, 또는 값 중 하나를 선택 `Automatic` `EqualAreas` `Cluster` 합니다.</span><span class="sxs-lookup"><span data-stu-id="89160-115">In the **Properties** window, click the text box next to <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn.DiscretizationMethod%2A> and select one of the following values: `Automatic`, `EqualAreas`, or `Cluster`.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="89160-116">열 사용법을로 설정 하면 해당 `Ignore` 열에 대 한 **속성** 창이 비어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="89160-116">If the column usage is set to `Ignore`, the **Properties** window for the column is blank.</span></span>  
  
     <span data-ttu-id="89160-117">디자이너에서 다른 요소를 선택하면 새 값이 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="89160-117">The new value will take effect when you select a different element in the designer.</span></span>  
  
3.  <span data-ttu-id="89160-118">데이터 마이닝 디자이너의 **속성** 창에서 <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn.DiscretizationBucketCount%2A> 옆에 있는 입력란을 클릭하고 숫자 값을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="89160-118">In the **Properties** window, click the text box next to <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn.DiscretizationBucketCount%2A> and type a numeric value.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="89160-119">이러한 속성을 변경하면 새 설정을 사용하려는 모든 모델과 함께 구조가 다시 처리되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="89160-119">If you change these properties, the structure must be reprocessed, along with any models that you want to use the new setting.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89160-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="89160-120">See Also</span></span>  
 [<span data-ttu-id="89160-121">마이닝 모델 태스크 및 방법</span><span class="sxs-lookup"><span data-stu-id="89160-121">Mining Model Tasks and How-tos</span></span>](mining-model-tasks-and-how-tos.md)  
  
  
