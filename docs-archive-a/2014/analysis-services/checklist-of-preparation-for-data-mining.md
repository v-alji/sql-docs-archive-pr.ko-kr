---
title: 데이터 마이닝 준비 검사 목록 | Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 0e056c95-ba06-413e-8dc1-4d411a447c3b
author: minewiskan
ms.author: owend
ms.openlocfilehash: e37b1adb6aebe5d5f8fd23f5289f52425f752a6e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648702"
---
# <a name="checklist-of-preparation-for-data-mining"></a><span data-ttu-id="9a92c-102">데이터 마이닝 준비 검사 목록</span><span class="sxs-lookup"><span data-stu-id="9a92c-102">Checklist of Preparation for Data Mining</span></span>
  <span data-ttu-id="9a92c-103">마이닝 추가 기능을 사용하여 쉽고 재미있게 모델을 만들고 시험해 볼 수 있지만 반복 및 실행 가능한 결과가 필요한 경우 기본 비즈니스 요구 사항을 공식화하고 데이터를 구하고 준비하는 데 충분한 시간을 가져야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9a92c-103">Although the Data Mining Add-ins make it fairly easy and fun to create and experiment with models, when you need to get repeatable, actionable results, you must allow adequate time for formulating basic business requirements, and for obtaining and preparing data.</span></span> <span data-ttu-id="9a92c-104">이 단원에서는 검사 활동을 계획하기 위한 검사 목록을 다루며, 일반적인 문제에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="9a92c-104">This section provides a checklist to help you plan your investigation, and describes common problems.</span></span>  
  
## <a name="checklist-of-data-preparation"></a><span data-ttu-id="9a92c-105">데이터 준비 검사 목록</span><span class="sxs-lookup"><span data-stu-id="9a92c-105">Checklist of Data Preparation</span></span>  
 <span data-ttu-id="9a92c-106">**명확하게 정의된 결과를 확인했습니다.**</span><span class="sxs-lookup"><span data-stu-id="9a92c-106">**I have identified a clearly defined output.**</span></span>  
 <span data-ttu-id="9a92c-107">결과 사용법에 대한 계획을 마련합니다.</span><span class="sxs-lookup"><span data-stu-id="9a92c-107">Have a plan for how you will use the results.</span></span> <span data-ttu-id="9a92c-108">모델 유형별로 출력이 서로 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="9a92c-108">Different types of models have different outputs.</span></span> <span data-ttu-id="9a92c-109">시계열 모델은 파악하고 작업하기 쉬운 계열 값을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="9a92c-109">A time series model generates values for a series in the future, which are easily understood and acted on.</span></span> <span data-ttu-id="9a92c-110">기타 모델에서는 해당 문제의 전문가가 분석해야 최상의 가치를 얻을 수 있는 복잡한 집합을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="9a92c-110">Other models generate complex sets that must be analyzed by subject matter experts to yield the most value.</span></span>  
  
-   <span data-ttu-id="9a92c-111">수행하려는 작업</span><span class="sxs-lookup"><span data-stu-id="9a92c-111">What output do you want?</span></span>  
  
-   <span data-ttu-id="9a92c-112">출력을 하나의 열 또는 값이나 기타 실행 가능한 결과로 정의할 수 있습니까?</span><span class="sxs-lookup"><span data-stu-id="9a92c-112">Can you define the output as a single column or value, or other actionable result?</span></span>  
  
-   <span data-ttu-id="9a92c-113">모델의 유용성을 파악하는 기준은 무엇입니까?</span><span class="sxs-lookup"><span data-stu-id="9a92c-113">What are your criteria for knowing that the model was useful?</span></span>  
  
-   <span data-ttu-id="9a92c-114">그러한 결과는 어떻게 사용하고 해석합니까?</span><span class="sxs-lookup"><span data-stu-id="9a92c-114">How will you use and interpret those results?</span></span>  
  
-   <span data-ttu-id="9a92c-115">새 입력 데이터를 예상된 데이터에 매핑할 수 있습니까?</span><span class="sxs-lookup"><span data-stu-id="9a92c-115">Can you map new input data to the expected results?</span></span>  
  
 <span data-ttu-id="9a92c-116">**의미, 데이터 형식 및 입력 데이터의 분포를 알고 있습니다.**</span><span class="sxs-lookup"><span data-stu-id="9a92c-116">**I know the meaning, data types, and distribution of the input data.**</span></span>  
 <span data-ttu-id="9a92c-117">시간을 들여 원본 데이터를 탐색하고 파악합니다.</span><span class="sxs-lookup"><span data-stu-id="9a92c-117">Take some time to explore and understand your source data.</span></span> <span data-ttu-id="9a92c-118">모델을 검토하는 사람은 어떤 종류의 입력 데이터가 사용되었는지를 이해하고 균형과 품질뿐만 아니라 데이터 형식과 가변성을 어떻게 해석할지 알고 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9a92c-118">It is important that people who review the model understand what kind of input data was used and know how to interpret the data types and the variability, as well as the balance and the quality.</span></span>  
  
-   <span data-ttu-id="9a92c-119">데이터는 얼마나 많이 있습니까?</span><span class="sxs-lookup"><span data-stu-id="9a92c-119">How much data do you have?</span></span> <span data-ttu-id="9a92c-120">모델링하기에 충분한 데이터가 있습니까?</span><span class="sxs-lookup"><span data-stu-id="9a92c-120">Is there sufficient data for modeling?</span></span>  
  
     <span data-ttu-id="9a92c-121">이는 크기가 더 작고 균형을 맞춰야 할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9a92c-121">It need not be a huge amount - smaller and balanced can be better.</span></span>  
  
-   <span data-ttu-id="9a92c-122">데이터 원본이 여러 개입니까, 아니면 하나입니까?</span><span class="sxs-lookup"><span data-stu-id="9a92c-122">Is the data from multiple sources, or a single source?</span></span>  
  
-   <span data-ttu-id="9a92c-123">이미 처리 및 정리를 마친 데이터입니까?</span><span class="sxs-lookup"><span data-stu-id="9a92c-123">Is the data already processed and clean?</span></span> <span data-ttu-id="9a92c-124">사용 가능한 입력 데이터가 더 있습니까?</span><span class="sxs-lookup"><span data-stu-id="9a92c-124">Is more input data available?</span></span>  
  
-   <span data-ttu-id="9a92c-125">데이터를 수신 하기 전에 조작 하는 방법을 알고 있나요? 데이터를 자르거나, 요약 하거나, 변환 하는 방법은 무엇입니까?</span><span class="sxs-lookup"><span data-stu-id="9a92c-125">Do you know how it was manipulated before you received it - how data might have been truncated, summarized, or converted?</span></span>  
  
-   <span data-ttu-id="9a92c-126">입력 데이터에는 학습에 사용할 수 있는 예제 결과가 있습니까?</span><span class="sxs-lookup"><span data-stu-id="9a92c-126">Does the input data have some example results that can be used for training?</span></span>  
  
 <span data-ttu-id="9a92c-127">**현재의 데이터 무결성 수준과 필요한 수준을 알고 있습니다.**</span><span class="sxs-lookup"><span data-stu-id="9a92c-127">**I understand the level of data integrity we have and the level we need.**</span></span>  
 <span data-ttu-id="9a92c-128">잘못된 데이터는 모델 품질에 영향을 미칠 수 있으며, 모델이 아예 생성되지 않을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9a92c-128">Bad data can affect the quality of the model, or prevent the model from being built at all.</span></span> <span data-ttu-id="9a92c-129">데이터의 분포 및 의미와 어떻게 이 상태가 되었는지에 대해 잘 알고 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9a92c-129">You should have a good understanding of both the distribution and meaning of the data, and how it came to this state.</span></span> <span data-ttu-id="9a92c-130">레이블 지정, 숫자 데이터 형식 자르기 또는 요약을 통해 데이터를 단순화 하는 것이 가능 하거나 적절 한지를 이해 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9a92c-130">You'll need to understand if it is possible or appropriate to simplify the data by labeling, truncating numeric data types, or by summarizing.</span></span>  
  
-   <span data-ttu-id="9a92c-131">데이터 레이블: 명확 하 고 정확한 가요?</span><span class="sxs-lookup"><span data-stu-id="9a92c-131">Data labels: are they clear and correct?</span></span>  
  
-   <span data-ttu-id="9a92c-132">데이터 형식: 적합 하 고 변경 되었습니까?</span><span class="sxs-lookup"><span data-stu-id="9a92c-132">Data types: are they appropriate, and have they been changed?</span></span>  
  
-   <span data-ttu-id="9a92c-133">잘못된 데이터를 분류하여 정리 또는 삭제했습니까?</span><span class="sxs-lookup"><span data-stu-id="9a92c-133">Have you sorted, cleaned up, or discarded wrong data?</span></span>  
  
     <span data-ttu-id="9a92c-134">중복이 없는지 확인했습니까?</span><span class="sxs-lookup"><span data-stu-id="9a92c-134">Have you verified there are no duplicates?</span></span>  
  
-   <span data-ttu-id="9a92c-135">누락된 값을 어떻게 처리하시겠습니까?</span><span class="sxs-lookup"><span data-stu-id="9a92c-135">How will you handle missing values?</span></span> <span data-ttu-id="9a92c-136">누락된 값에 의미가 있습니까?</span><span class="sxs-lookup"><span data-stu-id="9a92c-136">Do missing values have a meaning?</span></span>  
  
-   <span data-ttu-id="9a92c-137">가져오기 프로세스 중 오류가 발생했는지 확인하기 위해 원본을 확인했습니까?</span><span class="sxs-lookup"><span data-stu-id="9a92c-137">Have you verified the sources to see if any errors might have been introduced in the import process?</span></span>  
  
     <span data-ttu-id="9a92c-138">입력은 어디에 저장됩니까?</span><span class="sxs-lookup"><span data-stu-id="9a92c-138">Where is the input stored?</span></span> <span data-ttu-id="9a92c-139">얼마나 오래 사용 가능한 상태로 유지됩니까?</span><span class="sxs-lookup"><span data-stu-id="9a92c-139">How long does it stay available?</span></span>  
  
     <span data-ttu-id="9a92c-140">데이터 사전이 있습니까?</span><span class="sxs-lookup"><span data-stu-id="9a92c-140">Is there a data dictionary?</span></span> <span data-ttu-id="9a92c-141">만들 수 있습니까?</span><span class="sxs-lookup"><span data-stu-id="9a92c-141">Can you create one?</span></span>  
  
-   <span data-ttu-id="9a92c-142">데이터 집합을 결합한 경우, 동일한 데이터 열이 여러 개 있는지 확인했습니까?</span><span class="sxs-lookup"><span data-stu-id="9a92c-142">If you combined data sets, did you check for multiple columns representing the same data?</span></span>  
  
 <span data-ttu-id="9a92c-143">**원본 데이터가 저장 되는 위치, 위치 및 처리 방법을 알고 있습니다. 필요한 경우 프로세스를 쉽게 반복할 수 있습니다.**</span><span class="sxs-lookup"><span data-stu-id="9a92c-143">**I know where source data is stored, where it came from, and how it is processed. The process can be easily repeated if needed.**</span></span>  
 <span data-ttu-id="9a92c-144">일회용 데이터 집합은 실험에 적합 하지만 모델을 프로덕션 환경으로 이동 하려는 경우 운영 데이터에 정리 프로세스를 적용 하는 방법을 미리 생각해 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9a92c-144">One-off data sets are fine for experiments, but if you ever want to move the model into production, you'll want to think in advance about how the cleaning process can be applied to operational data.</span></span> <span data-ttu-id="9a92c-145">또한 운영 데이터를 보유 하 고 있는 경우에는 데이터를 수정 하기 전에 변경 된 방법을 알고 있어야 합니다. 이러한 데이터를 반올림 하거나 요약 한 방법을 알아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9a92c-145">Also, if you have operational data, you need to know how it might have been altered before you got it-you'll need to know how it was rounded, or summarized, certainly.</span></span>  
  
-   <span data-ttu-id="9a92c-146">실험을 반복 실행하시겠습니까?</span><span class="sxs-lookup"><span data-stu-id="9a92c-146">Do you want to be able to repeat the experiment?</span></span>  
  
-   <span data-ttu-id="9a92c-147">데이터 분석을 지원하는 형식으로 데이터를 준비하는 데 어느 도구를 사용하시겠습니까?</span><span class="sxs-lookup"><span data-stu-id="9a92c-147">What tools will you use to prepare data in a format that supports data analysis?</span></span> <span data-ttu-id="9a92c-148">자동화 가능합니까 아니면 Excel에서 검토하고 정리할 사람이 필요합니까?</span><span class="sxs-lookup"><span data-stu-id="9a92c-148">Can it be automated or do you need someone to review and clean up in Excel?</span></span>  
  
-   <span data-ttu-id="9a92c-149">다른 시스템의 원본에서 데이터를 가져오는 경우, 적용된 필터를 캡처하고 추적할 수 있습니까?</span><span class="sxs-lookup"><span data-stu-id="9a92c-149">If you are sourcing data from another system, will you be able to capture and track filters that were applied?</span></span>  
  
-   <span data-ttu-id="9a92c-150">데이터 처리 프레임워크에서 시스템 학습 알고리즘을 적용하고, 테스트를 수행하고, 결과를 시각화합니까?</span><span class="sxs-lookup"><span data-stu-id="9a92c-150">Can your data processing framework also apply machine learning algorithms, perform tests, and visualize results?</span></span>  
  
 <span data-ttu-id="9a92c-151">**원하는 예측 수준에 대해 합의했으며 데이터가 해당 단위를 출력하도록 수정되었습니다.**</span><span class="sxs-lookup"><span data-stu-id="9a92c-151">**We have agreed on the desired granularity of predictions and our data has been modified to output those units.**</span></span>  
 <span data-ttu-id="9a92c-152">데이터 준비 전에 원하는 결과 수준을 결정하십시오. 예를 들어, 판매 예측을 일별이나 분기별로 수행하시겠습니까?</span><span class="sxs-lookup"><span data-stu-id="9a92c-152">Decide on the granularity of the results you want before preparing data, For example, do you want sales predictions by the day, or for each quarter?</span></span> <span data-ttu-id="9a92c-153">동일한 데이터에 대해 다른 데이터 구조를 설정하여 다양한 요약 수준으로 처리해 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9a92c-153">You might consider setting up different data structures for the same data, to handle different levels of summary.</span></span>  
  
-   <span data-ttu-id="9a92c-154">현재 측정 단위 또는 시간 단위는 무엇입니까?</span><span class="sxs-lookup"><span data-stu-id="9a92c-154">What is the current unit of measure or unit of time?</span></span>  
  
     <span data-ttu-id="9a92c-155">결과에 어떤 단위를 사용하시겠습니까?</span><span class="sxs-lookup"><span data-stu-id="9a92c-155">What unit do you want to use in the results?</span></span>  
  
-   <span data-ttu-id="9a92c-156">모든 입력 데이터에 대해 기본 단위 (예: 일/시간/분/명령 호출)를 정의할 수 있나요?</span><span class="sxs-lookup"><span data-stu-id="9a92c-156">Is it possible to define a basic unit (e.g. day/ hour / min / instruction call) for all input data?</span></span>  
  
     <span data-ttu-id="9a92c-157">더 높은 단위로 롤업하시겠습니까?</span><span class="sxs-lookup"><span data-stu-id="9a92c-157">Do you want to rollup to higher units?</span></span>  
  
-   <span data-ttu-id="9a92c-158">범주 레이블이 일관성 있게 지정되었습니까?</span><span class="sxs-lookup"><span data-stu-id="9a92c-158">Are categories labeled consistently?</span></span> <span data-ttu-id="9a92c-159">범주를 쉽게 추가하거나 제거할 수 있습니까?</span><span class="sxs-lookup"><span data-stu-id="9a92c-159">Is it easy to add or remove categories?</span></span>  
  
 <span data-ttu-id="9a92c-160">**실험 디자인이 반복 및 재현 가능합니다.**</span><span class="sxs-lookup"><span data-stu-id="9a92c-160">**Our experimental design is repeatable and reproducible.**</span></span>  
 <span data-ttu-id="9a92c-161">결과를 분석하고 그 유효성을 검사하기 위한 전략과 데이터 스냅샷의 캡처 계획을 수립하여 데이터에 미치는 효과를 역추적할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9a92c-161">Consider strategies for analyzing and validating your results and plan to capture a data snapshot, to make sure you can trace back effects to data.</span></span> <span data-ttu-id="9a92c-162">임의 초기값 사용시 결과가 약간 다를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9a92c-162">If a random seed is used, the results can differ subtly.</span></span> <span data-ttu-id="9a92c-163">이로 인해 모델을 비교하고 유효성을 검사하기 어려울 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9a92c-163">This can make it difficult to compare and validate models.</span></span>  
  
-   <span data-ttu-id="9a92c-164">데이터에 사용자 지정 변경 내용이 많은 경우 다음 번에 모델을 작성하려고 하면 어떻게 됩니까?</span><span class="sxs-lookup"><span data-stu-id="9a92c-164">If you make a lot of custom changes to the data, what happens the next time you want to build the model?</span></span>  
  
-   <span data-ttu-id="9a92c-165">입력을 처리하고 원하는 출력을 얻을 때 사용해야 하는 수동 절차 또는 승인된 프로세스가 이미 정의되어 있습니까?</span><span class="sxs-lookup"><span data-stu-id="9a92c-165">Has a manual procedure or approved process already been defined that you should use to process input and get the desired outputs?</span></span>  
  
-   <span data-ttu-id="9a92c-166">모델에 초기값을 사용하기로 결정했습니까?</span><span class="sxs-lookup"><span data-stu-id="9a92c-166">Have you decided to use a seed for the model?</span></span>  
  
 <span data-ttu-id="9a92c-167">**결과의 유효성을 검사할 만한 도메인 지식이 있거나 조언을 할 수 있는 해당 문제의 전문가를 알고 있습니다.**</span><span class="sxs-lookup"><span data-stu-id="9a92c-167">**We have the domain knowledge to validate the results, or have access to subject matter experts who can advise.**</span></span>  
 <span data-ttu-id="9a92c-168">시간을 가지고 변수, 모델 및 그 결과의 유효성을 검사하십시오.</span><span class="sxs-lookup"><span data-stu-id="9a92c-168">Take time to validate the variables, the model, and the results.</span></span> <span data-ttu-id="9a92c-169">전문가의 도움을 받아 상호 작용 및 결과를 평가하십시오.</span><span class="sxs-lookup"><span data-stu-id="9a92c-169">Get the help of experts to assess interactions and results.</span></span> <span data-ttu-id="9a92c-170">그러나 과도 한 규칙 증명을 가정 하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="9a92c-170">However, don't let assumptions overrule evidence.</span></span> <span data-ttu-id="9a92c-171">새로운 상황이나 예기치 못한 결과를 받아들이십시오.</span><span class="sxs-lookup"><span data-stu-id="9a92c-171">Be open to new and unexpected findings.</span></span>  
  
-   <span data-ttu-id="9a92c-172">데이터를 필터링하고 의미 없는 입력을 줄이는 데 도메인 정보를 활용할 수 있습니까?</span><span class="sxs-lookup"><span data-stu-id="9a92c-172">Is domain knowledge available to help in filtering data and reducing input noise?</span></span>  
  
-   <span data-ttu-id="9a92c-173">도메인 전문가의 도움을 받아 결과를 해석하고 개선 사항을 제안 받을 수 있습니까?</span><span class="sxs-lookup"><span data-stu-id="9a92c-173">Can domain experts help understand interpret the results and suggest improvements?</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a92c-174">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9a92c-174">See Also</span></span>  
 [<span data-ttu-id="9a92c-175">데이터 마이닝을 위한 데이터 선택</span><span class="sxs-lookup"><span data-stu-id="9a92c-175">Choosing Data for Data Mining</span></span>](choosing-data-for-data-mining.md)  
  
  
