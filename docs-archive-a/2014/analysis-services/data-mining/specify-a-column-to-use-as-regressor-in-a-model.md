---
title: 모델에서 회귀 변수로 사용할 열을 지정 합니다. | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: d8e0cb8e-302a-4166-9ed0-e2d9e2919b0a
author: minewiskan
ms.author: owend
ms.openlocfilehash: 86899d3793985b5e3c07618360d7b6a540935a54
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639094"
---
# <a name="specify-a-column-to-use-as-regressor-in-a-model"></a><span data-ttu-id="3486d-102">모델에서 회귀 변수로 사용할 열 지정</span><span class="sxs-lookup"><span data-stu-id="3486d-102">Specify a Column to Use as Regressor in a Model</span></span>
  <span data-ttu-id="3486d-103">선형 회귀 모델은 데이터를 예상 회귀선에 가능한 한 근접하게 맞추는 방식으로 입력을 조합하는 수식의 결과로 예측 가능한 특성 값을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="3486d-103">A linear regression model represents the value of the predictable attribute as the result of a formula that combines the inputs in such a way that the data is fitted as a closely as possible to an estimated regression line.</span></span> <span data-ttu-id="3486d-104">알고리즘은 숫자 값만 입력으로 받으며 가장 적합한 입력을 자동으로 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="3486d-104">The algorithm accepts only numeric values as inputs, and automatically detects the inputs that provide the best fit.</span></span>  
  
 <span data-ttu-id="3486d-105">그러나 FORCE_REGRESSOR 매개 변수를 모델에 추가하고 사용할 회귀 변수를 지정하여 열을 회귀 변수로 포함하도록 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3486d-105">However, you can specify that a column be included as a regressor by adding the FORCE_REGRESSOR parameter to the model and specifying the regressors to use.</span></span> <span data-ttu-id="3486d-106">효과가 너무 작아 모델에서 검색할 수 없어도 특성이 의미를 가지는 경우 또는 특성을 수식에 포함해야 할 경우 이 작업을 원할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3486d-106">You might want to do this in cases where the attribute has meaning even if the effect is too small to be detected by the model, or when you want to ensure that the attribute is included in the formula.</span></span>  
  
 <span data-ttu-id="3486d-107">다음 절차에서는 [신경망 자습서](../../tutorials/lesson-5-build-models-intermediate-data-mining-tutorial.md)에 사용된 것과 동일한 예제 데이터를 사용하여 간단한 선형 회귀 모델을 만드는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="3486d-107">The following procedure describes how to create a simple linear regression model, using the same sample data that is used for the [neural networks tutorial](../../tutorials/lesson-5-build-models-intermediate-data-mining-tutorial.md).</span></span> <span data-ttu-id="3486d-108">모델은 견고할 필요는 없지만 데이터 마이닝 디자이너를 사용하여 선형 회귀 모델을 사용자 지정하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="3486d-108">The model is not necessarily robust, but demonstrates how to use the Data Mining Designer to customize a linear regression model.</span></span>  
  
### <a name="how-to-create-a-simple-linear-regression-model"></a><span data-ttu-id="3486d-109">단순 선형 회귀 모델을 만드는 방법</span><span class="sxs-lookup"><span data-stu-id="3486d-109">How to create a simple linear regression model</span></span>  
  
1.  <span data-ttu-id="3486d-110">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]의 **솔루션 탐색기**에서 **마이닝 구조**를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="3486d-110">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], in **Solution Explorer**, expand **Mining Structures**.</span></span>  
  
2.  <span data-ttu-id="3486d-111">Call Center.dmm을 두 번 클릭하여 디자이너에서 엽니다.</span><span class="sxs-lookup"><span data-stu-id="3486d-111">Double-click Call Center.dmm to open it in the designer.</span></span>  
  
3.  <span data-ttu-id="3486d-112">**마이닝 모델** 메뉴에서 **새 마이닝 모델**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3486d-112">From the **Mining Model** menu, select **New Mining Model**.</span></span>  
  
4.  <span data-ttu-id="3486d-113">알고리즘에 대해 **Microsoft 선형 회귀**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3486d-113">For the algorithm, select **Microsoft Linear Regression**.</span></span> <span data-ttu-id="3486d-114">이름에 대해 **Call Center Regression**을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="3486d-114">For the name, type **Call Center Regression**.</span></span>  
  
5.  <span data-ttu-id="3486d-115">**마이닝 모델** 탭에서 열 사용법을 다음과 같이 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="3486d-115">In the **Mining Models** tab, change the column usage as follows.</span></span> <span data-ttu-id="3486d-116">다음 목록에 없는 열은 모두 **Ignore**로 설정(이미 설정되어 있지 않은 경우)해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3486d-116">All columns not in the following list should be set to **Ignore**, if they are not already.</span></span>  
  
     <span data-ttu-id="3486d-117">FactCallCenterID**Key**</span><span class="sxs-lookup"><span data-stu-id="3486d-117">FactCallCenterID**Key**</span></span>  
  
     <span data-ttu-id="3486d-118">ServiceGrade**PredictOnly**</span><span class="sxs-lookup"><span data-stu-id="3486d-118">ServiceGrade**PredictOnly**</span></span>  
  
     <span data-ttu-id="3486d-119">Total Operators**Input**</span><span class="sxs-lookup"><span data-stu-id="3486d-119">Total Operators**Input**</span></span>  
  
     <span data-ttu-id="3486d-120">AverageTimePerIssue**Input**</span><span class="sxs-lookup"><span data-stu-id="3486d-120">AverageTimePerIssue**Input**</span></span>  
  
6.  <span data-ttu-id="3486d-121">**마이닝 모델** 메뉴에서 **모델 매개 변수 설정**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3486d-121">From the **Mining Model** menu, select **Set Model Parameters**.</span></span>  
  
7.  <span data-ttu-id="3486d-122">매개 변수 FORCE_REGRESSOR의 경우 **값** 열에서 다음과 같이 괄호로 묶고 쉼표로 구분한 열 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="3486d-122">For the parameter, FORCE_REGRESSOR, in the **Value** column, type the column names enclosed in brackets and separated by a comma, as follows:</span></span>  
  
    ```  
    [Average Time Per Issue],[Total Operators]  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="3486d-123">알고리즘이 자동으로 최상의 회귀 변수인 열을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="3486d-123">The algorithm will automatically detect which columns are the best regressors.</span></span> <span data-ttu-id="3486d-124">열을 최종 수식에 포함하려는 경우 회귀 변수를 적용하기만 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3486d-124">You only need to force regressors when you want to ensure that a column is included in the final formula.</span></span>  
  
8.  <span data-ttu-id="3486d-125">**마이닝 모델** 메뉴에서 **모델 처리**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3486d-125">From the **Mining Model** menu, select **Process Model**.</span></span>  
  
     <span data-ttu-id="3486d-126">뷰어에서 모델은 회귀 수식을 포함하는 단일 노드로 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="3486d-126">In the viewer, the model is represented a single node containing the regression formula.</span></span> <span data-ttu-id="3486d-127">**마이닝 범례**에서 수식을 보거나 쿼리를 사용하여 수식에 대한 계수를 추출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3486d-127">You can view the formula in the **Mining Legend**, or you can extract the coefficients for the formula by using queries.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3486d-128">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3486d-128">See Also</span></span>  
 <span data-ttu-id="3486d-129">[Microsoft 선형 회귀 알고리즘](microsoft-linear-regression-algorithm.md) </span><span class="sxs-lookup"><span data-stu-id="3486d-129">[Microsoft Linear Regression Algorithm](microsoft-linear-regression-algorithm.md) </span></span>  
 <span data-ttu-id="3486d-130">[데이터 마이닝 쿼리](data-mining-queries.md) </span><span class="sxs-lookup"><span data-stu-id="3486d-130">[Data Mining Queries](data-mining-queries.md) </span></span>  
 <span data-ttu-id="3486d-131">[Microsoft 선형 회귀 알고리즘 기술 참조](microsoft-linear-regression-algorithm-technical-reference.md) </span><span class="sxs-lookup"><span data-stu-id="3486d-131">[Microsoft Linear Regression Algorithm Technical Reference](microsoft-linear-regression-algorithm-technical-reference.md) </span></span>  
 [<span data-ttu-id="3486d-132">선형 회귀 모델에 대한 마이닝 모델 콘텐츠&#40;Analysis Services - 데이터 마이닝&#41;</span><span class="sxs-lookup"><span data-stu-id="3486d-132">Mining Model Content for Linear Regression Models &#40;Analysis Services - Data Mining&#41;</span></span>](mining-model-content-for-linear-regression-models-analysis-services-data-mining.md)  
  
  
