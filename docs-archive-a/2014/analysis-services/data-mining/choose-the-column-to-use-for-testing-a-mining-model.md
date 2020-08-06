---
title: 마이닝 모델을 테스트 하는 데 사용할 열을 선택 합니다. | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- columns [data mining], predictable mining columns
- Mining Accuracy Chart [Analysis Services], columns
- predictable mining columns [Analysis Services]
ms.assetid: c6a8f23a-da21-4f31-9521-99460d624649
author: minewiskan
ms.author: owend
ms.openlocfilehash: 326a7084600695d95d3a132f633041e9abad045b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652455"
---
# <a name="choose-the-column-to-use-for-testing-a-mining-model"></a><span data-ttu-id="1d695-102">마이닝 모델 테스트에 사용할 열 선택</span><span class="sxs-lookup"><span data-stu-id="1d695-102">Choose the Column to Use for Testing a Mining Model</span></span>
  <span data-ttu-id="1d695-103">마이닝 모델의 정확도를 측정하려면 먼저 평가할 결과를 결정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1d695-103">Before you can measure the accuracy of a mining model, you must decide which outcome it is that you want to assess.</span></span> <span data-ttu-id="1d695-104">대부분의 데이터 마이닝 모델에서는 모델을 만들 때 예측 가능한 특성으로 사용할 열을 하나 이상 선택해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1d695-104">Most data mining models require that you choose at least one column to use as the predictable attribute when you create the model.</span></span> <span data-ttu-id="1d695-105">따라서 모델의 정확도를 테스트할 때는 일반적으로 테스트할 특성을 선택해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1d695-105">Therefore, when you test the accuracy of the model, you generally must select that attribute to test.</span></span>  
  
 <span data-ttu-id="1d695-106">다음 목록에서는 테스트에 사용할 예측 가능한 특성을 선택할 때 추가적으로 고려할 사항에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="1d695-106">The following list describes some additional considerations for choosing the predictable attribute to use in testing:</span></span>  
  
-   <span data-ttu-id="1d695-107">일부 유형의 데이터 마이닝 모델에서는 여러 특성 간의 관계를 탐색할 수 있는 신경망과 같은 여러 특성을 예측할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1d695-107">Some types of data mining models can predict multiple attributes-such as neural networks, which can explore the relationships between many attributes.</span></span>  
  
-   <span data-ttu-id="1d695-108">클러스터링 모델과 같은 다른 유형의 마이닝 모델에는 예측 가능한 특성이 반드시 있어야 하는 것은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="1d695-108">Other types of mining models-such as clustering models-do not necessarily have a predictable attribute.</span></span> <span data-ttu-id="1d695-109">예측 가능한 특성이 없는 클러스터링 모델은 테스트할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1d695-109">Clustering models cannot be tested unless they have a predictable attribute.</span></span>  
  
-   <span data-ttu-id="1d695-110">회귀 모델의 산점도를 만들거나 정확도를 측정하려면 연속된 예측 가능한 특성을 결과로 선택해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1d695-110">To create a scatter plot or measure the accuracy of a regression model requires that you choose a continuous predictable attribute as the outcome.</span></span> <span data-ttu-id="1d695-111">이 경우 대상 값은 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1d695-111">In that case, you cannot specify a target value.</span></span> <span data-ttu-id="1d695-112">산점도가 아닌 다른 항목을 만들려면 기본 마이닝 구조 열의 내용 유형이 **불연속** 또는 **분할**이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1d695-112">If you are creating anything other than a scatter plot, the underlying mining structure column must also have a content type of **Discrete** or **Discretized**.</span></span>  
  
-   <span data-ttu-id="1d695-113">불연속 특성을 예측 가능한 결과로 선택한 경우에는 대상 값을 지정하거나 **예측 값** 필드를 비워 둘 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1d695-113">If you choose a discrete attribute as the predictable outcome, you can also specify a target value, or you can leave the **Predict Value** field blank.</span></span> <span data-ttu-id="1d695-114">**예측 값**을 포함 하는 경우 차트는 대상 값을 예측 하는 경우에만 모델의 유효성을 측정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1d695-114">If you include a **Predict Value**, the chart will measure only the model's effectiveness at predicting the target value.</span></span> <span data-ttu-id="1d695-115">대상 결과를 지정하지 않으면 모든 결과를 예측할 때 모델의 정확도가 측정됩니다.</span><span class="sxs-lookup"><span data-stu-id="1d695-115">If you do not specify a target outcome, the model is measured for its accuracy in predicting all outcomes.</span></span>  
  
-   <span data-ttu-id="1d695-116">여러 모델을 포함하여 하나의 정확도 차트에서 비교하려면 모든 모델에서 동일한 예측 가능한 열을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1d695-116">If you want to include multiple models and compare them in a single accuracy chart, all models must use the same predictable column.</span></span>  
  
-   <span data-ttu-id="1d695-117">교차 유효성 검사 보고서를 만드는 경우에는 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 에서 예측 가능한 특성이 동일한 모든 모델을 자동으로 분석합니다.</span><span class="sxs-lookup"><span data-stu-id="1d695-117">When you create a cross-validation report, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] will automatically analyze all models that have the same predictable attribute.</span></span>  
  
-   <span data-ttu-id="1d695-118">**예측 열과 값 동기화**옵션을 선택한 경우에는 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 에서 이름이 같고 데이터 형식이 일치하는 예측 가능한 열을 자동으로 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="1d695-118">When the option, **Synchronize Prediction columns and Values**, is selected, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] automatically chooses predictable columns that have the same names and matching data types.</span></span> <span data-ttu-id="1d695-119">열이 이러한 조건을 충족하지 않는 경우 이 옵션을 해제하고 예측 가능한 열을 수동으로 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1d695-119">If your columns do not meet these criteria, you can turn off this option and manually choose a predictable column.</span></span> <span data-ttu-id="1d695-120">모델과 다른 열이 있는 외부 데이터 집합을 사용하여 모델을 테스트하는 경우에 예측 가능한 열을 수동으로 선택해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1d695-120">You might need to do this if you are testing the model with an external data set that has different columns than the model.</span></span> <span data-ttu-id="1d695-121">그러나 데이터 형식이 잘못된 열을 선택하면 오류가 발생하거나 잘못된 결과가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="1d695-121">However, if you choose a column with the wrong the type of data you will either get an error or bad results.</span></span>  
  
### <a name="specify-the-outcome-to-predict"></a><span data-ttu-id="1d695-122">예측할 결과 지정</span><span class="sxs-lookup"><span data-stu-id="1d695-122">Specify the outcome to predict</span></span>  
  
1.  <span data-ttu-id="1d695-123">마이닝 구조를 두 번 클릭하여 데이터 마이닝 디자이너에서 엽니다.</span><span class="sxs-lookup"><span data-stu-id="1d695-123">Double-click the mining structure to open it in Data Mining Designer.</span></span>  
  
2.  <span data-ttu-id="1d695-124">**마이닝 정확도 차트** 탭을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="1d695-124">Select the **Mining Accuracy Chart** tab.</span></span>  
  
3.  <span data-ttu-id="1d695-125">**입력 선택** 탭을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="1d695-125">Select the **Input Selection** tab.</span></span>  
  
4.  <span data-ttu-id="1d695-126">**입력 선택** 탭의 **예측 가능한 열 이름**에서 행을 클릭하고 차트에 포함할 각 모델에 대한 예측 가능한 열을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="1d695-126">On the **Input Selection** tab, under **Predictable Column Name**, select a predictable column for each model that you include in the chart.</span></span>  
  
     <span data-ttu-id="1d695-127">**예측 가능한 열 이름** 상자에 제공되는 마이닝 모델 열은 사용 유형이 **예측** 또는 **예측만**으로 설정된 열로 제한됩니다.</span><span class="sxs-lookup"><span data-stu-id="1d695-127">The mining model columns that are available in the **Predictable Column Name** box are only those with the usage type set to **Predict** or **Predict Only**.</span></span>  
  
5.  <span data-ttu-id="1d695-128">모델의 리프트를 결정하려면 **예측 값** 목록에서 측정할 특정 결과 값을 선택해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1d695-128">If you want to determine the lift for a model, you must select a specific outcome value to measure, for by choosing from the **Predict Value** list.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d695-129">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1d695-129">See Also</span></span>  
 <span data-ttu-id="1d695-130">[모델 테스트 데이터 선택 및 매핑](choose-and-map-model-testing-data.md) </span><span class="sxs-lookup"><span data-stu-id="1d695-130">[Choose and Map Model Testing Data](choose-and-map-model-testing-data.md) </span></span>  
 [<span data-ttu-id="1d695-131">정확도 차트 유형 선택 및 차트 옵션 설정</span><span class="sxs-lookup"><span data-stu-id="1d695-131">Choose an Accuracy Chart Type and Set Chart Options</span></span>](choose-an-accuracy-chart-type-and-set-chart-options.md)  
  
  
