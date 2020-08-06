---
title: 정확도 차트 유형 선택 및 차트 옵션 설정 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Mining Accuracy Chart [Analysis Services]
- mining models [Analysis Services], validating
- classification accuracy [data mining]
- accuracy testing [data mining]
ms.assetid: bd24dd4a-624f-478a-9c94-b1361e857680
author: minewiskan
ms.author: owend
ms.openlocfilehash: 33c2b5e8a1e228a86328ef6df1b636742d3614ff
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649849"
---
# <a name="choose-an-accuracy-chart-type-and-set-chart-options"></a><span data-ttu-id="3bac1-102">정확도 차트 유형 선택 및 차트 옵션 설정</span><span class="sxs-lookup"><span data-stu-id="3bac1-102">Choose an Accuracy Chart Type and Set Chart Options</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="3bac1-103">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]에서는 마이닝 모델의 유효성을 확인 하기 위한 여러 가지 방법을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="3bac1-103">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] provides multiple methods for determining the validity of your mining models.</span></span> <span data-ttu-id="3bac1-104">각 모델 또는 구조에 대해 만들 수 있는 정확도 차트의 유형은 다음 요소에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="3bac1-104">The type of accuracy chart that you can create for each model or structure depends on these factors:</span></span>  
  
-   <span data-ttu-id="3bac1-105">모델을 만드는 데 사용된 알고리즘 유형</span><span class="sxs-lookup"><span data-stu-id="3bac1-105">The type of algorithm that was used to create the model</span></span>  
  
-   <span data-ttu-id="3bac1-106">예측 가능한 특성의 데이터 형식</span><span class="sxs-lookup"><span data-stu-id="3bac1-106">The data type of the predictable attribute</span></span>  
  
-   <span data-ttu-id="3bac1-107">측정할 예측 가능한 특성의 수</span><span class="sxs-lookup"><span data-stu-id="3bac1-107">The number of predictable attributes to measure</span></span>  
  
 <span data-ttu-id="3bac1-108">이 항목에서는 여러 가지 정확도 차트에 대해 간략하게 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="3bac1-108">This topic provides an overview of the different accuracy charts.</span></span>  
  
 <span data-ttu-id="3bac1-109">**참고** 차트와 차트 정의는 저장되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3bac1-109">**Note** Charts and their definitions are not saved.</span></span> <span data-ttu-id="3bac1-110">차트가 포함된 창을 닫으면 차트를 다시 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3bac1-110">If you close the window that contains a chart, you must create the chart again.</span></span>  
  
## <a name="accuracy-chart-types"></a><span data-ttu-id="3bac1-111">정확도 차트 유형</span><span class="sxs-lookup"><span data-stu-id="3bac1-111">Accuracy Chart Types</span></span>  
 <span data-ttu-id="3bac1-112">선택하는 차트 종류에 따라 옵션을 추가로 구성하거나, 차트를 찾아보거나, 차트를 클립보드에 복사하고 Excel에서 데이터를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3bac1-112">Depending on the chart type that you choose, you have the ability to further configure options, to browse the chart, or copy the chart to the Clipboard and work with the data in Excel.</span></span>  
  
#### <a name="lift-chart"></a><span data-ttu-id="3bac1-113">리프트 차트</span><span class="sxs-lookup"><span data-stu-id="3bac1-113">Lift chart</span></span>  
 <span data-ttu-id="3bac1-114">모델 및 테스트 데이터에 대한 옵션을 구성한 후에는 **리프트 차트** 탭을 클릭하여 결과를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3bac1-114">After you have configured the options for the models and the testing data, click the **Lift Chart** tab to view the results.</span></span> <span data-ttu-id="3bac1-115">또한 차트를 클립보드에 복사하거나 마이닝 범례에서 개별 추세 선 또는 데이터 요소에 대한 세부 정보를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3bac1-115">You can also copy the chart to the Clipboard, or view details of individual trend lines or data points in the Mining Legend.</span></span>  
  
#### <a name="profit-chart"></a><span data-ttu-id="3bac1-116">수익 차트</span><span class="sxs-lookup"><span data-stu-id="3bac1-116">Profit Chart</span></span>  
 <span data-ttu-id="3bac1-117">모델 및 테스트 데이터에 대한 옵션을 구성한 후에는 **리프트 차트** 탭을 클릭하고 **차트 종류** 목록에서 **수익 차트** 를 선택하여 수익 차트 옵션을 설정한 다음 **확인** 을 클릭하여 결과를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3bac1-117">After you have configured the options for the models and the testing data, click the **Lift Chart** tab, select **Profit Chart** from the **Chart Type** list to set profit chart options, and then click **OK** to view the results.</span></span>  
  
 <span data-ttu-id="3bac1-118">**수익 차트 설정** 대화 상자를 원하는 만큼 여러 번 사용하여 다른 비용 옵션을 시도하고 차트를 다시 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3bac1-118">You can use the **Profit Chart Settings** dialog box as many times as you want to try different cost options and redisplay the chart.</span></span> <span data-ttu-id="3bac1-119">마이닝 범례에는 각 모델의 예상 수익에 대한 세부 정보가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="3bac1-119">The Mining Legend contains detailed information about the estimated profit for each model.</span></span> <span data-ttu-id="3bac1-120">차트와 마이닝 범례의 내용을 클립보드에 복사하고 Excel에서 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3bac1-120">You can also copy the chart and the contents of the Mining Legend to the Clipboard to work with it in Excel.</span></span>  
  
#### <a name="scatter-plot"></a><span data-ttu-id="3bac1-121">산점도</span><span class="sxs-lookup"><span data-stu-id="3bac1-121">Scatter Plot</span></span>  
 <span data-ttu-id="3bac1-122">적절한 모델 유형을 선택한 경우 **리프트 차트** 탭을 클릭하면 차트 종류가 **산점도** 로 자동 설정되고 산점도가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="3bac1-122">If you have selected the appropriate type of model, when you click the **Lift Chart** tab, the chart type is automatically set to **Scatter Plot** and a scatter plot is displayed.</span></span> <span data-ttu-id="3bac1-123">더 이상의 추가 구성은 불가능합니다.</span><span class="sxs-lookup"><span data-stu-id="3bac1-123">No further configuration is possible.</span></span> <span data-ttu-id="3bac1-124">차트를 클립보드에 복사하고 Excel 또는 다른 애플리케이션에 그래픽으로 붙여넣을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3bac1-124">You can also copy the chart to the Clipboard and paste the chart as a graphic into Excel or another application.</span></span>  
  
#### <a name="classification-matrix"></a><span data-ttu-id="3bac1-125">분류표</span><span class="sxs-lookup"><span data-stu-id="3bac1-125">Classification Matrix</span></span>  
 <span data-ttu-id="3bac1-126">분류 행렬의 경우 **입력 선택** 탭을 사용하여 모델 및 테스트 데이터를 선택한 다음 **분류 행렬** 탭을 클릭하여 결과를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3bac1-126">For a classification matrix, use the **Input Selection** tab to choose the models and the testing data, and then click the **Classification Matrix** tab to view the results.</span></span>  
  
 <span data-ttu-id="3bac1-127">분류 행렬의 내용은 모든 모델 유형에서 동일하며 구성할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3bac1-127">The contents of a classification matrix are the same for all model types, and cannot be configured.</span></span> <span data-ttu-id="3bac1-128">차트의 데이터를 클립보드에 복사한 다음 Excel에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3bac1-128">You can copy the data in the chart to the Clipboard and then work with it in Excel.</span></span>  
  
#### <a name="cross-validation-report"></a><span data-ttu-id="3bac1-129">교차 유효성 검사 보고서</span><span class="sxs-lookup"><span data-stu-id="3bac1-129">Cross-Validation Report</span></span>  
 <span data-ttu-id="3bac1-130">교차 유효성 검사 보고서의 경우 솔루션 탐색기에서 마이닝 구조 또는 마이닝 모델을 선택한 후 **교차 유효성 검사** 탭을 클릭하고 모든 관련 옵션을 구성한 다음 **결과 가져오기** 를 클릭하여 보고서를 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3bac1-130">For a cross-validation report, after you have selected a mining structure or mining model in Solution Explorer, click the **Cross Validation** tab, configure all relevant options, and then click **Get Results** to generate the report.</span></span> <span data-ttu-id="3bac1-131">더 이상의 추가 구성은 불가능합니다.</span><span class="sxs-lookup"><span data-stu-id="3bac1-131">No further configuration is possible.</span></span>  
  
 <span data-ttu-id="3bac1-132">교차 유효성 검사 보고서의 형식은 모든 모델 유형에서 동일하며 구성할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3bac1-132">The format of the cross-validation report is the same for all model types, and cannot be configured.</span></span> <span data-ttu-id="3bac1-133">그러나 보고서의 내용은 분석하는 모델의 유형 및 예측 가능한 특성의 데이터 형식에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="3bac1-133">However, the content of the report differs depending on the type of model that you are analyzing, and the data type of the predictable attribute.</span></span> <span data-ttu-id="3bac1-134">보고서의 결과를 클립보드에 복사하고 Excel에서 데이터를 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3bac1-134">You can also copy the results of the report to the Clipboard and work with the data in Excel.</span></span>  
  
  
