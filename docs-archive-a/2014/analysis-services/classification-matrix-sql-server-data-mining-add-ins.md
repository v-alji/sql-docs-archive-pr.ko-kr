---
title: 분류표 (SQL Server 데이터 마이닝 추가 기능) | Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining models, validating
- classification matrix
- confusion table
- mining models, testing
ms.assetid: d6f620f4-39af-4714-9628-28ce3c361fca
author: minewiskan
ms.author: owend
ms.openlocfilehash: a930f2628ac41fc5886cf41d7ec0ad274b42bf2f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648069"
---
# <a name="classification-matrix-sql-server-data-mining-add-ins"></a><span data-ttu-id="e7453-102">분류표(SQL Server 데이터 마이닝 추가 기능)</span><span class="sxs-lookup"><span data-stu-id="e7453-102">Classification Matrix (SQL Server Data Mining Add-ins)</span></span>
  <span data-ttu-id="e7453-103">![데이터 마이닝 리본, 분류표 단추](media/dmc-cmatrix.gif "데이터 마이닝 리본, 분류표 단추")</span><span class="sxs-lookup"><span data-stu-id="e7453-103">![Classification Matrix button, Data Mining ribbon](media/dmc-cmatrix.gif "Classification Matrix button, Data Mining ribbon")</span></span>  
  
 <span data-ttu-id="e7453-104">분류표를 사용하여 예측에 대한 모델의 정확도를 평가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e7453-104">You can use the classification matrix to assess the accuracy of a model for prediction.</span></span> <span data-ttu-id="e7453-105">분류표를 생성하려면 모델을 통해 테스트 데이터 집합을 실행해야 합니다. 분류표 도구는 테스트 집합의 실제 값과 모델로 산출된 예측을 비교합니다.</span><span class="sxs-lookup"><span data-stu-id="e7453-105">To generate a classification matrix, you run a set of testing data through the model, and the classification matrix tool compares the actual values from the testing set against the predictions made by the model.</span></span> <span data-ttu-id="e7453-106">분류표를 확인하여 모델이 올바르게 예측한 빈도와 잘못 예측한 빈도를 한눈에 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e7453-106">By looking at the matrix, you can tell at a glance how often the model is correct, and how often it predicts wrongly.</span></span>  
  
 <span data-ttu-id="e7453-107">이러한 추가 기능에서 **분류표** 마법사를 사용 하 여 모델을 선택 하 고 테스트 데이터를 지정한 다음 결과 행렬을 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="e7453-107">In these add-ins, use the **Classification Matrix** wizard to select a model, specify the testing data, and then generate a results matrix.</span></span>  
  
## <a name="how-to-read-a-classification-matrix"></a><span data-ttu-id="e7453-108">분류표를 읽는 방법</span><span class="sxs-lookup"><span data-stu-id="e7453-108">How to Read a Classification Matrix</span></span>  
 <span data-ttu-id="e7453-109">고객 충성도 프로그램을 디자인 한 후 적절 한 수준의 성과급을 제공할 수 있도록 고객을 적절 한 범주에 할당 하는 것이 목표 라고 가정 하겠습니다.</span><span class="sxs-lookup"><span data-stu-id="e7453-109">Let's assume your objective is to design a customer loyalty program and then assign customers to appropriate categories, so that you can provide them with the appropriate level of incentives.</span></span> <span data-ttu-id="e7453-110">보상 프로그램에 대 한 세 가지 수준인 브론즈, 실버 및 골드를 구현 했으며,이는 평가판 단계에서 고객에 게 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e7453-110">You have implemented three levels for the reward program -- bronze, silver, and gold - and given these out to customers in a trial phase.</span></span> <span data-ttu-id="e7453-111">또한 고객을 분석하고 올바른 범주를 예측하는 모델을 설계했습니다.</span><span class="sxs-lookup"><span data-stu-id="e7453-111">You have also designed a model that analyzes customers and predicts the correct categories.</span></span> <span data-ttu-id="e7453-112">이제 시험 데이터에 대한 분류표를 사용하여 모델이 모든 고객에 대한 올바른 보상을 얼마나 정확하게 예측했는지를 확인할 것입니다.</span><span class="sxs-lookup"><span data-stu-id="e7453-112">Now you will use the classification matrix on the trial data to determine how good the model was at predicting the correct offer for all customers.</span></span>  
  
 <span data-ttu-id="e7453-113">분류표의 표에서는 모델을 기반으로 각 범주에 할당될 고객 수를 알려주고 이 결과를 각 보상 수준에 실제로 등록한 고객 수와 비교합니다.</span><span class="sxs-lookup"><span data-stu-id="e7453-113">The table from the classification matrix tells you how many customers would be assigned to each category based on the model, and compares that result to the number of customers who actually signed up for each reward level.</span></span>  
  
||<span data-ttu-id="e7453-114">동(실제)</span><span class="sxs-lookup"><span data-stu-id="e7453-114">Bronze (Actual)</span></span>|<span data-ttu-id="e7453-115">금(실제)</span><span class="sxs-lookup"><span data-stu-id="e7453-115">Gold (Actual)</span></span>|<span data-ttu-id="e7453-116">은(실제)</span><span class="sxs-lookup"><span data-stu-id="e7453-116">Silver (Actual)</span></span>|  
|-|-----------------------|---------------------|-----------------------|  
|<span data-ttu-id="e7453-117">동</span><span class="sxs-lookup"><span data-stu-id="e7453-117">Bronze</span></span>|<span data-ttu-id="e7453-118">**94.45%**</span><span class="sxs-lookup"><span data-stu-id="e7453-118">**94.45%**</span></span>|<span data-ttu-id="e7453-119">15.18%</span><span class="sxs-lookup"><span data-stu-id="e7453-119">15.18%</span></span>|<span data-ttu-id="e7453-120">1.70%</span><span class="sxs-lookup"><span data-stu-id="e7453-120">1.70%</span></span>|  
|<span data-ttu-id="e7453-121">금</span><span class="sxs-lookup"><span data-stu-id="e7453-121">Gold</span></span>|<span data-ttu-id="e7453-122">2.72%</span><span class="sxs-lookup"><span data-stu-id="e7453-122">2.72%</span></span>|<span data-ttu-id="e7453-123">**84.82%**</span><span class="sxs-lookup"><span data-stu-id="e7453-123">**84.82%**</span></span>|<span data-ttu-id="e7453-124">0.00%</span><span class="sxs-lookup"><span data-stu-id="e7453-124">0.00%</span></span>|  
|<span data-ttu-id="e7453-125">은</span><span class="sxs-lookup"><span data-stu-id="e7453-125">Silver</span></span>|<span data-ttu-id="e7453-126">1.84%</span><span class="sxs-lookup"><span data-stu-id="e7453-126">1.84%</span></span>|<span data-ttu-id="e7453-127">0.00%</span><span class="sxs-lookup"><span data-stu-id="e7453-127">0.00%</span></span>|<span data-ttu-id="e7453-128">**93.80%**</span><span class="sxs-lookup"><span data-stu-id="e7453-128">**93.80%**</span></span>|  
|<span data-ttu-id="e7453-129">*맞는*</span><span class="sxs-lookup"><span data-stu-id="e7453-129">*Correct*</span></span>|<span data-ttu-id="e7453-130">*95.45%*</span><span class="sxs-lookup"><span data-stu-id="e7453-130">*95.45%*</span></span>|<span data-ttu-id="e7453-131">*84.82%*</span><span class="sxs-lookup"><span data-stu-id="e7453-131">*84.82%*</span></span>|<span data-ttu-id="e7453-132">*98.30%*</span><span class="sxs-lookup"><span data-stu-id="e7453-132">*98.30%*</span></span>|  
|<span data-ttu-id="e7453-133">*오분류*</span><span class="sxs-lookup"><span data-stu-id="e7453-133">*Misclassified*</span></span>|<span data-ttu-id="e7453-134">*4.55%*</span><span class="sxs-lookup"><span data-stu-id="e7453-134">*4.55%*</span></span>|<span data-ttu-id="e7453-135">*15.18%*</span><span class="sxs-lookup"><span data-stu-id="e7453-135">*15.18%*</span></span>|<span data-ttu-id="e7453-136">*1.70%*</span><span class="sxs-lookup"><span data-stu-id="e7453-136">*1.70%*</span></span>|  
  
-   <span data-ttu-id="e7453-137">각 열에는 테스트 데이터 세트의 실제 값이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="e7453-137">Each column shows the actual values in the testing dataset.</span></span>  
  
-   <span data-ttu-id="e7453-138">각 행에는 예측된 값이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="e7453-138">Each row shows the predicted values.</span></span>  
  
-   <span data-ttu-id="e7453-139">분류표의 왼쪽 위 모퉁이에서 오른쪽 아래 모퉁이까지 대각선 방향으로 굵게 표시된 값은 모델이 올바르게 예측한 값을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="e7453-139">The values in boldface, which run diagonally from the upper-left corner to the lower-right corner of the matrix, give you the picture of what the model got right.</span></span>  
  
-   <span data-ttu-id="e7453-140">대각선 밖의 다른 모든 값은 오류를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="e7453-140">All other values outside the diagonal represent errors.</span></span> <span data-ttu-id="e7453-141">일부 오류는 거짓 긍정입니다. 즉, 모델은 고객이 금 프로그램에 참여할 것으로 예측했지만 틀린 경우입니다.</span><span class="sxs-lookup"><span data-stu-id="e7453-141">Some errors are false positives, meaning the model predicted the customer would join the gold program but was wrong.</span></span>  <span data-ttu-id="e7453-142">분야에 따라 거짓 긍정은 비용이 매우 많이 들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e7453-142">Depending on your domain, false positives can be very costly.</span></span>  
  
     <span data-ttu-id="e7453-143">다른 오류는 거짓 부정입니다. 즉, 모델은 고객이 관심이 없을 것이라고 예측했지만 고객은 프로그램에 참여한 경우입니다.</span><span class="sxs-lookup"><span data-stu-id="e7453-143">Others are false negatives, meaning the model predicted the customer would not be interested though he or she did join the program.</span></span> <span data-ttu-id="e7453-144">마찬가지로 문제 분야에 따라 이 손실된 기회 비용은 상당히 클 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e7453-144">Again, depending on the problem domain, this lost opportunity cost might be significant.</span></span>  
  
## <a name="using-the-classification-matrix-wizard"></a><span data-ttu-id="e7453-145">분류표 마법사 사용</span><span class="sxs-lookup"><span data-stu-id="e7453-145">Using the Classification Matrix Wizard</span></span>  
  
1.  <span data-ttu-id="e7453-146">예측의 기반이 될 마이닝 모델을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e7453-146">Select the mining model on which to base predictions.</span></span>  
  
2.  <span data-ttu-id="e7453-147">새 테스트 데이터의 원본을 선택하거나 구조와 함께 저장된 테스트 데이터를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="e7453-147">Select a source of new test data, or use testing data that was saved with the structure.</span></span>  
  
3.  <span data-ttu-id="e7453-148">정확도를 평가하려는 열을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e7453-148">Select the column for which you want to assess accuracy.</span></span> <span data-ttu-id="e7453-149">분류표를 만들 때 열을 하나만 선택할 수 있지만 열의 값이 여러 개일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e7453-149">You can choose only one column when creating a matrix, but the column can have multiple values.</span></span>  
  
     <span data-ttu-id="e7453-150">팁: 예측 가능한 열에 비교할 열이 여러 개 있는 경우에는 분류 행렬을 해석 하기가 어려울 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e7453-150">Tip: It can be difficult to interpret a classification matrix if your predictable column has many columns to compare.</span></span>  
  
     <span data-ttu-id="e7453-151">**예측할 열 선택** 페이지에서 잘못 된 값과 잘못 된 값의 개수를 표시할지 아니면 백분율을 표시할지를 지정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e7453-151">In the **Select Columns to Predict** page, you can also specify whether you want to display the count of incorrect and incorrect values, or display a percentage.</span></span>  
  
4.  <span data-ttu-id="e7453-152">원본 데이터 선택 페이지에서 외부 테스트 데이터를 사용할지, 아니면 모델과 함께 저장된 테스트 데이터를 사용할지를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="e7453-152">On the Select Source Data page, indicate whether you are using external testing data, or the test data saved with the model.</span></span>  
  
5.  <span data-ttu-id="e7453-153">외부 테스트 데이터를 사용 하는 경우 마법사의 **관계 지정** 페이지에서 모델을 입력 열에 매핑해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e7453-153">If you use external testing data, you need to map the model to the input columns on the **Specify Relationship** page of the wizard.</span></span>  
  
     <span data-ttu-id="e7453-154">포함된 테스트 데이터 집합을 사용하는 경우 매핑이 자동으로 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="e7453-154">If you use the embedded test data set, the mapping is done for you</span></span>  
  
6.  <span data-ttu-id="e7453-155">**마침** 을 클릭 하 여 모델에 대 한 예측을 실행 하 고 분류 행렬을 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="e7453-155">Click **Finish** to run predictions against the model and generate the classification matrix.</span></span>  
  
     <span data-ttu-id="e7453-156">마법사가 분류표 및 분석에 대한 기타 세부 사항이 포함된 보고서를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e7453-156">The wizard creates a report that contains the classification matrix and other details about the analysis.</span></span> <span data-ttu-id="e7453-157">이 보고서는 Excel에서 테이블로 저장되며 보고서 위에는 올바르게 예측된 경우의 수와 잘못된 예측의 수를 나타내는 요약이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e7453-157">This report is saved as a table in Excel, with a summary above the report that indicates how many cases were correctly predicted and how many predictions were wrong.</span></span>  
  
### <a name="requirements"></a><span data-ttu-id="e7453-158">요구 사항</span><span class="sxs-lookup"><span data-stu-id="e7453-158">Requirements</span></span>  
  
-   <span data-ttu-id="e7453-159">분류표를 만들려면 정확도 측정을 지원하는 기존 마이닝 모델에 액세스할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e7453-159">To create a classification matrix, you must have access to an existing mining model that supports accuracy measurement.</span></span> <span data-ttu-id="e7453-160">예측 모델과 연결 모델은 이 도구를 사용하여 측정될 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e7453-160">Forecasting models and association models cannot be measured using this tool.</span></span>  
  
-   <span data-ttu-id="e7453-161">측정할 모델은 불연속 값이거나 이미 불연속화된 값을 예측해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e7453-161">The model that you are measuring needs to predict a value that is either discrete or that has already been discretized.</span></span>  
  
-   <span data-ttu-id="e7453-162">구조 나 모델과 함께 테스트 집합을 저장 하는 옵션을 사용 하지 않은 경우 모델에 사용 되는 것과 일치 하는 데이터 형식을 사용 하 여 기본적으로 동일한 수의 열이 있는 입력 데이터 집합을 가져와야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e7453-162">If you didn't use the option to save a testing set along with your structure or model, you need to obtain an input data set that has essentially the same number of columns, with matching data types, as those used in the model.</span></span>  
  
-   <span data-ttu-id="e7453-163">데이터 마이닝 모델과 테스트에 사용할 새 데이터에는 예측 가능한 열이 한 개 이상 있어야 하며 열은 반드시 동일한 종류의 데이터를 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e7453-163">Both the data mining model and the new data that you are using for testing must contain at least one column that can be predicted, and the columns must contain the same kind of data.</span></span>  
  
### <a name="known-issues"></a><span data-ttu-id="e7453-164">알려진 문제</span><span class="sxs-lookup"><span data-stu-id="e7453-164">Known Issues</span></span>  
 <span data-ttu-id="e7453-165">SQL Server 2012 및 SQL Server 2014에서는 내부 테스트 데이터 집합을 모델에 매핑하는 기능이 **분류표** 도구에서 작동 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e7453-165">In SQL Server 2012 and SQL Server 2014, the ability to map the internal test data set to the model is not working in the **Classification Matrix** tool.</span></span> <span data-ttu-id="e7453-166">그러나 외부 데이터 집합을 지정한 다음 학습 집합을 입력으로 선택하여 원래 데이터 집합에 대한 오류를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e7453-166">However, you can specify an external data set, and then select the training set as the input to determine error on the original data set.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7453-167">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e7453-167">See Also</span></span>  
 <span data-ttu-id="e7453-168">[Excel 용 데이터 마이닝 추가 기능에 대 한 예측 &#40;모델 유효성 검사 및 모델 사용&#41;](validating-models-and-using-models-for-prediction-data-mining-add-ins-for-excel.md) </span><span class="sxs-lookup"><span data-stu-id="e7453-168">[Validating Models and Using Models for Prediction &#40;Data Mining Add-ins for Excel&#41;](validating-models-and-using-models-for-prediction-data-mining-add-ins-for-excel.md) </span></span>  
 <span data-ttu-id="e7453-169">[데이터 마이닝 추가 기능 SQL Server 데이터 &#40;탐색&#41;](explore-data-sql-server-data-mining-add-ins.md) </span><span class="sxs-lookup"><span data-stu-id="e7453-169">[Explore Data &#40;SQL Server Data Mining Add-ins&#41;](explore-data-sql-server-data-mining-add-ins.md) </span></span>  
 [<span data-ttu-id="e7453-170">Excel 용 테이블 분석 도구 &#40;범주 검색&#41;</span><span class="sxs-lookup"><span data-stu-id="e7453-170">Detect Categories &#40;Table Analysis Tools for Excel&#41;</span></span>](detect-categories-table-analysis-tools-for-excel.md)  
  
  
