---
title: 모델 유효성 검사 및 예측을 위한 모델 사용 (Excel 용 데이터 마이닝 추가 기능) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining models, validating
- mining models, charting
- validation [data mining]
- mining models, testing
ms.assetid: e245ac1f-1230-48e9-9091-e70b131aa2a8
author: minewiskan
ms.author: owend
ms.openlocfilehash: c1dd4f9bab977a90579076b824d2c0aa525c84af
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649202"
---
# <a name="validating-models-and-using-models-for-prediction-data-mining-add-ins-for-excel"></a><span data-ttu-id="4d21e-102">모델 유효성 검사 및 예측용 모델 사용(Excel용 데이터 마이닝 추가 기능)</span><span class="sxs-lookup"><span data-stu-id="4d21e-102">Validating Models and Using Models for Prediction (Data Mining Add-ins for Excel)</span></span>
  <span data-ttu-id="4d21e-103">모델 테스트 및 유효성 검사는 데이터 마이닝 프로세스에서 중요한 단계입니다.</span><span class="sxs-lookup"><span data-stu-id="4d21e-103">Testing and validating your model is an important step in the data mining process.</span></span> <span data-ttu-id="4d21e-104">마이닝 모델을 프로덕션 환경에 배포하기 전에 실제 데이터에 대한 마이닝 모델의 성능을 알아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4d21e-104">You must know how well your mining models perform against real data before you deploy the models into a production environment.</span></span>  
  
 <span data-ttu-id="4d21e-105">데이터 마이닝 추가 기능에는 작성한 모델을 테스트하고 해당 모델을 사용하여 예측 및 권장 사항을 만들 수 있도록 지원하는 도구가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4d21e-105">The Data Mining Add-ins include tools that help you test the models you built, and create predictions and recommendations using the models.</span></span>  
  
## <a name="accuracy-chart"></a><span data-ttu-id="4d21e-106">정확도 차트</span><span class="sxs-lookup"><span data-stu-id="4d21e-106">Accuracy Chart</span></span>  
 <span data-ttu-id="4d21e-107">**정확도 차트** 마법사를 사용 하 여 리프트 차트나 산 점도 차트를 만들어 예측 쿼리를 만들고 데이터 마이닝 모델의 성능을 평가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4d21e-107">The **Accuracy Chart** wizard helps you create a prediction query and assess the performance of a data mining model by creating a lift chart or scatter plot chart.</span></span> <span data-ttu-id="4d21e-108">리프트 차트는 한 구조에서 거의 같은 모델을 구별하여 가장 적합한 예측을 제공하는 모델을 판별하는 데 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="4d21e-108">The lift chart helps distinguish between models in a structure that are almost the same, to help you determine which model provides the best predictions.</span></span>  
  
 [<span data-ttu-id="4d21e-109">정확도 차트 &#40;SQL Server 데이터 마이닝 추가 기능&#41;</span><span class="sxs-lookup"><span data-stu-id="4d21e-109">Accuracy Chart &#40;SQL Server Data Mining Add-ins&#41;</span></span>](accuracy-chart-sql-server-data-mining-add-ins.md)  
  
## <a name="classification-matrix"></a><span data-ttu-id="4d21e-110">분류표</span><span class="sxs-lookup"><span data-stu-id="4d21e-110">Classification Matrix</span></span>  
 <span data-ttu-id="4d21e-111">분류표 **마법사를** 사용 하면 예측 쿼리를 만들어 분류 모델의 성능을 평가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4d21e-111">The **Classification Matrix** wizard helps you create a prediction query to assess the performance of a classification model.</span></span> <span data-ttu-id="4d21e-112">해당 모델로 산출한 결과는 정확한 예측과 정확하지 않은 예측을 모두 요약하는 차트로 출력됩니다.</span><span class="sxs-lookup"><span data-stu-id="4d21e-112">The output is a chart that summarizes both accurate and inaccurate predictions made by the model.</span></span> <span data-ttu-id="4d21e-113">행렬은 모델이 값을 정확하게 예측한 빈도뿐만 아니라 모델이 자주 잘못 예측한 값도 표시하기 때문에 매우 유용한 도구입니다.</span><span class="sxs-lookup"><span data-stu-id="4d21e-113">The matrix is a valuable tool because it not only shows how frequently the model correctly predicted a value, but also shows which values the model most frequently predicted incorrectly.</span></span>  
  
 [<span data-ttu-id="4d21e-114">분류표는 데이터 마이닝 추가 기능을 SQL Server &#40;&#41;</span><span class="sxs-lookup"><span data-stu-id="4d21e-114">Classification Matrix &#40;SQL Server Data Mining Add-ins&#41;</span></span>](classification-matrix-sql-server-data-mining-add-ins.md)  
  
## <a name="profit-chart"></a><span data-ttu-id="4d21e-115">수익 차트</span><span class="sxs-lookup"><span data-stu-id="4d21e-115">Profit Chart</span></span>  
 <span data-ttu-id="4d21e-116">**수익 차트** 마법사를 사용 하면 데이터 마이닝 모델을 사용 하 여 얻을 수 있는 이점을 비교 하 고 거짓 긍정 및 거짓 네거티브의 비용을 평가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4d21e-116">The **Profit Chart** wizard helps you weigh the benefits of using a data mining model and assess the costs of both false positives and false negatives</span></span>  
  
 <span data-ttu-id="4d21e-117">이 차트 유형은 모델의 예측 정확도를 측정하고 지정한 단위와 전반적인 비용을 통합합니다.</span><span class="sxs-lookup"><span data-stu-id="4d21e-117">This chart type measures the prediction accuracy of the model and incorporates unit and overall costs that you specify.</span></span>  
  
 <span data-ttu-id="4d21e-118">[수익 차트는&#41;SQL Server 데이터 마이닝 추가 기능을 &#40;](profit-chart-sql-server-data-mining-add-ins.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="4d21e-118">[Profit Chart &#40;SQL Server Data Mining Add-ins&#41;](profit-chart-sql-server-data-mining-add-ins.md).</span></span>  
  
## <a name="cross-validation"></a><span data-ttu-id="4d21e-119">교차 유효성 검사</span><span class="sxs-lookup"><span data-stu-id="4d21e-119">Cross-Validation</span></span>  
 <span data-ttu-id="4d21e-120">교차 유효성 검사는 데이터 마이닝 커뮤니티에서 설정된 기술로 데이터 집합의 타당성과 해당 데이터 집합에 대한 마이닝 모델의 정확도를 평가합니다.</span><span class="sxs-lookup"><span data-stu-id="4d21e-120">Cross-validation is an established technique in the data mining community for assessing the validity of a data set and the accuracy of a mining model on that data set.</span></span> <span data-ttu-id="4d21e-121">이 검사는 데이터 집합을 하위 집합으로 분할한 다음 각각의 하위 집합에 대한 모델을 반복해서 만들어 학습하고 테스트합니다.</span><span class="sxs-lookup"><span data-stu-id="4d21e-121">It divides a set of data into subsets, and then iteratively creates, trains, and tests models on each subset.</span></span>  
  
 <span data-ttu-id="4d21e-122">**교차 유효성 검사** 마법사를 사용 하면 데이터를 나눌 접기 수를 지정한 다음 이러한 교차 섹션 간의 차이점을 통계적으로 설명 하는 교차 유효성 검사 보고서를 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4d21e-122">The **Cross-Validation** wizard lets you specify the number of folds to divide your data by, and then provides a cross-validation report that statistically describes the differences among these cross-sections.</span></span> <span data-ttu-id="4d21e-123">여기에서 모델이 모든 학습 데이터에 대해 잘 수행되고 있는지 또는 특정 하위 집합에 대해 비대칭인지 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4d21e-123">From this you can determine whether the model performs well on all training data, or might be skewed to a particular subset.</span></span>  
  
 [<span data-ttu-id="4d21e-124">교차 유효성 검사는 데이터 마이닝 추가 기능 SQL Server &#40;&#41;</span><span class="sxs-lookup"><span data-stu-id="4d21e-124">Cross-Validation &#40;SQL Server Data Mining Add-ins&#41;</span></span>](cross-validation-sql-server-data-mining-add-ins.md)  
  
## <a name="query-wizard"></a><span data-ttu-id="4d21e-125">쿼리 마법사</span><span class="sxs-lookup"><span data-stu-id="4d21e-125">Query Wizard</span></span>  
 <span data-ttu-id="4d21e-126">**쿼리** 마법사는 예측 쿼리를 작성 하는 데 도움이 되는 대화형 도구입니다.</span><span class="sxs-lookup"><span data-stu-id="4d21e-126">The **Query** wizard is an interactive tool that helps you build a prediction query.</span></span> <span data-ttu-id="4d21e-127">쿼리는 권장 사항, 미래 예측 등을 생성하는 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="4d21e-127">Queries are how you generate recommendations, future forecasts, and so forth.</span></span>  
  
 <span data-ttu-id="4d21e-128">**쿼리** 마법사에서 모델을 선택한 다음 입력 데이터를 단일 값 이나 테이블이 나 범위에서 제공 하 고 마법사를 사용 하 여 출력할 열을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4d21e-128">In the **Query** wizard, you pick a model, and then provide input data, either as single values or from a table or range, and the wizard helps you select columns to output.</span></span> <span data-ttu-id="4d21e-129">쿼리에 기능을 추가하여 확률 점수 및 기타 유용한 통계를 생성할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4d21e-129">You can also add functions to your query to generate probability scores and other useful statistics.</span></span>  
  
 [<span data-ttu-id="4d21e-130">쿼리 &#40;SQL Server 데이터 마이닝 추가 기능&#41;</span><span class="sxs-lookup"><span data-stu-id="4d21e-130">Query &#40;SQL Server Data Mining Add-ins&#41;</span></span>](query-sql-server-data-mining-add-ins.md)  
  
## <a name="advanced-query-editor"></a><span data-ttu-id="4d21e-131">고급 쿼리 편집기</span><span class="sxs-lookup"><span data-stu-id="4d21e-131">Advanced Query Editor</span></span>  
 <span data-ttu-id="4d21e-132">**고급 쿼리 편집기** 는 모든 종류의 DMX 문을 작성 하는 데 도움이 되는 대화 상자의 대화형 대화 상자 집합으로, 새 모델을 만들고 학습 하거나 모델을 삭제 하거나 새 데이터 집합을 만들기 위해 사용자 지정 쿼리 실행에서 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4d21e-132">The **Advanced Query Editor** is an interactive set of dialog boxes that helps you build all kinds of DMX statements, anything from running custom queries to creating and training new models, deleting models, or creating new data sets.</span></span>  
  
 [<span data-ttu-id="4d21e-133">고급 데이터 마이닝 쿼리 편집기</span><span class="sxs-lookup"><span data-stu-id="4d21e-133">Advanced Data Mining Query Editor</span></span>](advanced-data-mining-query-editor.md)  
  
## <a name="see-also"></a><span data-ttu-id="4d21e-134">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4d21e-134">See Also</span></span>  
 <span data-ttu-id="4d21e-135">[데이터 탐색 및 정리](exploring-and-cleaning-data.md) </span><span class="sxs-lookup"><span data-stu-id="4d21e-135">[Exploring and Cleaning Data](exploring-and-cleaning-data.md) </span></span>  
 <span data-ttu-id="4d21e-136">[데이터 마이닝 모델 만들기](creating-a-data-mining-model.md) </span><span class="sxs-lookup"><span data-stu-id="4d21e-136">[Creating a Data Mining Model](creating-a-data-mining-model.md) </span></span>  
 [<span data-ttu-id="4d21e-137">Excel 용 데이터 마이닝 추가 기능 &#40;마이닝 모델 배포 및 확장&#41;</span><span class="sxs-lookup"><span data-stu-id="4d21e-137">Deploying and Scaling Mining Models &#40;Data Mining Add-ins for Excel&#41;</span></span>](deploying-and-scaling-mining-models-data-mining-add-ins-for-excel.md)  
  
  
