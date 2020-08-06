---
title: 리프트 차트 탭 (마이닝 정확도 차트 뷰) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.accuracychart.liftchart.f1
ms.assetid: f1674e2e-d38e-40c7-b8d1-5585ce9a0168
author: minewiskan
ms.author: owend
ms.openlocfilehash: 7cdad01ff3549140bf4fed606b1e8f9eaed10dac
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743576"
---
# <a name="lift-chart-tab-mining-accuracy-chart-view"></a><span data-ttu-id="12dc9-102">리프트 차트 탭(마이닝 정확도 차트 뷰)</span><span class="sxs-lookup"><span data-stu-id="12dc9-102">Lift Chart Tab (Mining Accuracy Chart View)</span></span>
  <span data-ttu-id="12dc9-103">**리프트 차트** 창을 사용하여 선택한 마이닝 구조에서 선택한 모든 마이닝 모델을 비교하는 차트를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="12dc9-103">Use the **Lift Chart** pane to view a chart that compares all the selected mining models in the selected mining structure.</span></span>  
  
 <span data-ttu-id="12dc9-104">모델에서 불연속 특성을 예측하는 경우 이 창에 리프트 차트나 수익 차트가 표시될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="12dc9-104">If the model predicts a discrete attribute, the pane can display either a lift chart or a profit chart.</span></span> <span data-ttu-id="12dc9-105">리프트 차트에 대한 자세한 내용은 [리프트 차트&#40;Analysis Services - 데이터 마이닝&#41;](data-mining/lift-chart-analysis-services-data-mining.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="12dc9-105">For information about lift charts, see [Lift Chart &#40;Analysis Services - Data Mining&#41;](data-mining/lift-chart-analysis-services-data-mining.md).</span></span>  
  
 <span data-ttu-id="12dc9-106">수익 차트를 만들려면 마이닝 모델의 권장 사항을 구현하는 비용과 예상 수익에 대한 추가 정보를 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="12dc9-106">To create a profit chart, you must provide additional information about the cost of implementing the recommendations of the mining model, as well as the expected return.</span></span> <span data-ttu-id="12dc9-107">자세한 내용은 [수익 차트&#40;Analysis Services - 데이터 마이닝&#41;](data-mining/profit-chart-analysis-services-data-mining.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="12dc9-107">For more information, see [Profit Chart &#40;Analysis Services - Data Mining&#41;](data-mining/profit-chart-analysis-services-data-mining.md).</span></span>  
  
 <span data-ttu-id="12dc9-108">모델에서 연속 특성을 예측하는 경우에는 이 창에 산점도 그래프가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="12dc9-108">If the model predicts a continuous attribute, the pane will display a scatter plot graph.</span></span>  
  
 <span data-ttu-id="12dc9-109">마이닝 모델의 정확도 측정 방법에 대한 일반적인 내용은 [리프트 차트&#40;Analysis Services - 데이터 마이닝&#41;](data-mining/lift-chart-analysis-services-data-mining.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="12dc9-109">For general information about methods of measuring the accuracy of a mining model, see [Lift Chart &#40;Analysis Services - Data Mining&#41;](data-mining/lift-chart-analysis-services-data-mining.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="12dc9-110">옵션</span><span class="sxs-lookup"><span data-stu-id="12dc9-110">Options</span></span>  
 <span data-ttu-id="12dc9-111">**차트 종류**</span><span class="sxs-lookup"><span data-stu-id="12dc9-111">**Chart Type**</span></span>  
 <span data-ttu-id="12dc9-112">뷰어에 표시할 차트의 종류를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="12dc9-112">Sets the type of chart to display in the viewer.</span></span> <span data-ttu-id="12dc9-113">**리프트 차트** 또는 **수익 차트**를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="12dc9-113">You can select either **Lift Chart** or **Profit Chart**.</span></span>  
  
 <span data-ttu-id="12dc9-114">**설정**</span><span class="sxs-lookup"><span data-stu-id="12dc9-114">**Settings**</span></span>  
 <span data-ttu-id="12dc9-115">수익 차트를 구성하는 데 사용할 수 있는 **수익 차트 설정** 대화 상자를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="12dc9-115">Opens the **Profit Chart Settings** dialog box, which you can use to configure a profit chart.</span></span>  
  
 <span data-ttu-id="12dc9-116">**열 매핑** 탭에서 예측 가능한 연속 열을 선택한 경우에는 수익 차트를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="12dc9-116">The profit chart is not available if a continuous predictable column was selected in the **Column Mapping** tab.</span></span>  
  
 <span data-ttu-id="12dc9-117">**복사**</span><span class="sxs-lookup"><span data-stu-id="12dc9-117">**Copy**</span></span>  
 <span data-ttu-id="12dc9-118">차트를 클립보드에 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="12dc9-118">Copies the chart to the Clipboard.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12dc9-119">참고 항목</span><span class="sxs-lookup"><span data-stu-id="12dc9-119">See Also</span></span>  
 <span data-ttu-id="12dc9-120">[마이닝 정확도 차트 디자이너 &#40;데이터 마이닝&#41;](mining-accuracy-chart-designer-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="12dc9-120">[Mining Accuracy Chart Designer &#40;Data Mining&#41;](mining-accuracy-chart-designer-data-mining.md) </span></span>  
 <span data-ttu-id="12dc9-121">[테스트 및 유효성 검사 태스크 및 방법 &#40;데이터 마이닝&#41;](data-mining/testing-and-validation-tasks-and-how-tos-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="12dc9-121">[Testing and Validation Tasks and How-tos &#40;Data Mining&#41;](data-mining/testing-and-validation-tasks-and-how-tos-data-mining.md) </span></span>  
 [<span data-ttu-id="12dc9-122">테스트 및 유효성 검사&#40;데이터 마이닝&#41;</span><span class="sxs-lookup"><span data-stu-id="12dc9-122">Testing and Validation &#40;Data Mining&#41;</span></span>](data-mining/testing-and-validation-data-mining.md)  
  
  
