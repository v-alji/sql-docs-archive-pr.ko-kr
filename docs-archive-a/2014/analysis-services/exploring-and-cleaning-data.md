---
title: 데이터 탐색 및 정리 | Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 7c888c95-8986-461e-9f11-2395044b9d97
author: minewiskan
ms.author: owend
ms.openlocfilehash: 154c711f735bcbb472e49654139fd16a036a0dd5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639073"
---
# <a name="exploring-and-cleaning-data"></a><span data-ttu-id="f5410-102">데이터 탐색 및 지우기</span><span class="sxs-lookup"><span data-stu-id="f5410-102">Exploring and Cleaning Data</span></span>
  <span data-ttu-id="f5410-103">데이터 준비는 데이터 정리보다 훨씬 많이 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="f5410-103">Data preparation is much more than data cleansing.</span></span> <span data-ttu-id="f5410-104">데이터가 준비되는 방식은 결과가 결국 해석되는 방식에도 영향을 미칩니다.</span><span class="sxs-lookup"><span data-stu-id="f5410-104">Remember that how data is prepared also affects how results are interpreted in the end.</span></span> <span data-ttu-id="f5410-105">데이터 준비는 다음과 같은 태스크로 이루어집니다.</span><span class="sxs-lookup"><span data-stu-id="f5410-105">Data preparation involves these tasks:</span></span>  
  
-   <span data-ttu-id="f5410-106">데이터 분포 탐색 및 확인</span><span class="sxs-lookup"><span data-stu-id="f5410-106">Exploring and checking the distribution of data.</span></span>  
  
-   <span data-ttu-id="f5410-107">잘못된 레코드 정리 및 데이터 마이닝 열 선택</span><span class="sxs-lookup"><span data-stu-id="f5410-107">Cleaning bad records, and choosing columns for data mining.</span></span>  
  
-   <span data-ttu-id="f5410-108">적절하게 Null 처리</span><span class="sxs-lookup"><span data-stu-id="f5410-108">Handling nulls appropriately.</span></span>  
  
-   <span data-ttu-id="f5410-109">다양한 시간 단위를 기준으로 값 범주화 또는 값 집계</span><span class="sxs-lookup"><span data-stu-id="f5410-109">Binning values, or aggregating values by different chunks of time.</span></span>  
  
-   <span data-ttu-id="f5410-110">결과의 사용 편의성을 높이기 위해 레이블 추가</span><span class="sxs-lookup"><span data-stu-id="f5410-110">Adding labels to improve the usability of the results.</span></span>  
  
-   <span data-ttu-id="f5410-111">분석에 필요한 경우 데이터 형식 변환 또는 값 범주화</span><span class="sxs-lookup"><span data-stu-id="f5410-111">Converting data types or categorizing values where necessary for analysis.</span></span>  
  
 <span data-ttu-id="f5410-112">데이터 모델링을 처음 접하는 경우 관련 항목인 [데이터 마이닝 준비 검사 목록](checklist-of-preparation-for-data-mining.md)을 읽어 보는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="f5410-112">If you are new to data modeling, we recommend that you read the related topic, [Checklist of Preparation for Data Mining](checklist-of-preparation-for-data-mining.md).</span></span>  
  
## <a name="data-preparation-tools"></a><span data-ttu-id="f5410-113">데이터 준비 도구</span><span class="sxs-lookup"><span data-stu-id="f5410-113">Data Preparation Tools</span></span>  
 <span data-ttu-id="f5410-114">Office용 데이터 마이닝 추가 기능에는 다음과 같은 데이터 정리 및 준비 도구가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="f5410-114">The Data Mining Add-ins for Office includes the following tools for data cleansing and preparation:</span></span>  
  
### <a name="explore-data"></a><span data-ttu-id="f5410-115">데이터 탐색</span><span class="sxs-lookup"><span data-stu-id="f5410-115">Explore Data</span></span>  
 <span data-ttu-id="f5410-116">이러한 데이터 준비 태스크는 **데이터 탐색** 마법사를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="f5410-116">Use the **Explore Data** wizard for these data preparation tasks:</span></span>  
  
-   <span data-ttu-id="f5410-117">분석하기 전에 데이터를 미리 보고 수정이 필요한 오류를 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="f5410-117">Preview your data and identify errors that must be fixed prior to analysis.</span></span>  
  
-   <span data-ttu-id="f5410-118">데이터의 균형과 필요한 정리 태스크를 이해하는 데 유용한 통계 정보를 수집합니다.</span><span class="sxs-lookup"><span data-stu-id="f5410-118">Gather statistical information that is useful for understanding the balance of data and the required clean-up tasks.</span></span>  
  
-   <span data-ttu-id="f5410-119">분석에 유용한 열을 식별하고 데이터 모델링 단계를 계획합니다.</span><span class="sxs-lookup"><span data-stu-id="f5410-119">Identify columns that are useful for analysis, and plan the data modeling phase.</span></span>  
  
 <span data-ttu-id="f5410-120">데이터 [마이닝 추가 기능을&#41;SQL Server &#40;데이터를 탐색 ](explore-data-sql-server-data-mining-add-ins.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="f5410-120">[Explore Data &#40;SQL Server Data Mining Add-ins&#41;](explore-data-sql-server-data-mining-add-ins.md).</span></span>  
  
### <a name="detect-and-handle-outliers"></a><span data-ttu-id="f5410-121">이상값 검색 및 처리</span><span class="sxs-lookup"><span data-stu-id="f5410-121">Detect and Handle Outliers</span></span>  
 <span data-ttu-id="f5410-122">이상 **값 마법사는** 데이터의 값 분포를 그래프로 표시 하 여 극단적인 값을 제거할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="f5410-122">The **Outliers** wizard graphs the distribution of values in your data and helps you remove extreme values.</span></span> <span data-ttu-id="f5410-123">다음 데이터 준비 태스크에는 이상 **값 도구를 사용 합니다.**</span><span class="sxs-lookup"><span data-stu-id="f5410-123">Use the **Outliers** tool for the following data preparation tasks:</span></span>  
  
-   <span data-ttu-id="f5410-124">데이터의 패턴에 따라 개별 값을 신뢰할 수 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="f5410-124">Determine whether individual values are reliable, based on patterns found in the data.</span></span>  
  
-   <span data-ttu-id="f5410-125">비정상적인 값을 검토한 후 삭제 또는 교체합니다.</span><span class="sxs-lookup"><span data-stu-id="f5410-125">Review unusual values and take action by deleting or replacing them.</span></span>  
  
-   <span data-ttu-id="f5410-126">모델을 특정 범위의 값으로 정의</span><span class="sxs-lookup"><span data-stu-id="f5410-126">Scope a model to a specific range of values.</span></span> <span data-ttu-id="f5410-127">예를 들어, 특정 저장소에 이상값이 있다는 것을 아는 경우 이 값을 제거하고 다른 저장소를 보다 잘 예측하는 모델을 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f5410-127">For example, if you know that you have outliers at a particular store, you can eliminate that value and get a model that better predicts other stores.</span></span>  
  
 <span data-ttu-id="f5410-128">[데이터 마이닝 추가 기능을&#41;SQL Server ](outliers-sql-server-data-mining-add-ins.md)이상 값 &#40;입니다.</span><span class="sxs-lookup"><span data-stu-id="f5410-128">[Outliers &#40;SQL Server Data Mining Add-ins&#41;](outliers-sql-server-data-mining-add-ins.md).</span></span>  
  
### <a name="relabel-and-bin-data"></a><span data-ttu-id="f5410-129">데이터 레이블 재지정 및 범주화</span><span class="sxs-lookup"><span data-stu-id="f5410-129">Relabel and Bin Data</span></span>  
 <span data-ttu-id="f5410-130">**레이블 재지정** 마법사는 데이터에 대 한 레이블을 변경할 수 있도록 데이터를 값으로 그룹화 합니다.</span><span class="sxs-lookup"><span data-stu-id="f5410-130">The **Relabel** wizard groups data by values so that you can change the labels on the data.</span></span> <span data-ttu-id="f5410-131">다음 데이터 준비 작업에 레이블 재지정 도구를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="f5410-131">Use the Relabel tool for these data preparation tasks:</span></span>  
  
-   <span data-ttu-id="f5410-132">설문 조사 결과에 사용된 숫자 코드를 해당 숫자 코드가 의미하는 바에 대한 텍스트 설명으로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="f5410-132">Change numeric codes used in survey results to a text description of what the numeric code means.</span></span>  
  
     <span data-ttu-id="f5410-133">예를 들어 성별 = 1과 같은 데이터 항목을 성별 = 여성으로 바꿀 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f5410-133">For example, you might replace data entries such as Gender = 1 with Gender = Female.</span></span>  
  
-   <span data-ttu-id="f5410-134">숫자 범위를 나타내는 그룹을 만들어 데이터를 범주화합니다.</span><span class="sxs-lookup"><span data-stu-id="f5410-134">Bin data, by creating groups to represents number ranges.</span></span>  
  
     <span data-ttu-id="f5410-135">예를 들어 숫자의 소득 열을 **수입-보통** 및 **수입**등의 레이블로 바꿀 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f5410-135">For example, you might want to replace an Income column of numbers with labels such as **Income - Moderate** and **Income - High**.</span></span>  
  
-   <span data-ttu-id="f5410-136">고유 값들을 범주별로 분류합니다.</span><span class="sxs-lookup"><span data-stu-id="f5410-136">Collapse discrete values into categories.</span></span>  
  
     <span data-ttu-id="f5410-137">예를 들어 개별 제품의 수가 너무 많아 구매 간 패턴을 검색하기 어려운 경우 더 광범위한 범주에 제품을 할당할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f5410-137">For example, if you have too many individual products to detect a pattern among purchases, you could try assigning products into broader categories.</span></span>  
  
 [<span data-ttu-id="f5410-138">레이블 재지정 &#40;SQL Server 데이터 마이닝 추가 기능&#41;</span><span class="sxs-lookup"><span data-stu-id="f5410-138">Relabel &#40;SQL Server Data Mining Add-ins&#41;</span></span>](relabel-sql-server-data-mining-add-ins.md)  
  
### <a name="cleanse-data"></a><span data-ttu-id="f5410-139">데이터 지우기</span><span class="sxs-lookup"><span data-stu-id="f5410-139">Cleanse Data</span></span>  
 <span data-ttu-id="f5410-140">데이터 정리는 다음과 같은 다양한 작업을 포함하며 대부분 추가 기능에서 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="f5410-140">Data cleansing encompasses a wide range of activities, most of which are supported by the add-ins</span></span>  
  
-   <span data-ttu-id="f5410-141">Null 값을 식별하고 이러한 값을 실제 값으로 변경할지 또는 `Missing` 값으로 처리할지 여부를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="f5410-141">Identify nulls and determine whether they should be changed to a real value or handled as `Missing` values.</span></span>  
  
-   <span data-ttu-id="f5410-142">누락된 값을 탐색하여 제거하거나 중간값, Null 또는 기타 값 등의 적절한 값으로 돌립니다.</span><span class="sxs-lookup"><span data-stu-id="f5410-142">Detect missing values, and then remove them, or impute an appropriate value, such as a mean, null, or other value.</span></span>  
  
 [<span data-ttu-id="f5410-143">데이터 마이닝 추가 기능 SQL Server 데이터 &#40;탐색&#41;</span><span class="sxs-lookup"><span data-stu-id="f5410-143">Explore Data &#40;SQL Server Data Mining Add-ins&#41;</span></span>](explore-data-sql-server-data-mining-add-ins.md)  
  
 [<span data-ttu-id="f5410-144">레이블 재지정 &#40;SQL Server 데이터 마이닝 추가 기능&#41;</span><span class="sxs-lookup"><span data-stu-id="f5410-144">Relabel &#40;SQL Server Data Mining Add-ins&#41;</span></span>](relabel-sql-server-data-mining-add-ins.md)  
  
 [<span data-ttu-id="f5410-145">예제로 채우기</span><span class="sxs-lookup"><span data-stu-id="f5410-145">Fill From Example</span></span>](fill-from-example-table-analysis-tools-for-excel.md)  
  
### <a name="sample-data"></a><span data-ttu-id="f5410-146">데이터 샘플링</span><span class="sxs-lookup"><span data-stu-id="f5410-146">Sample Data</span></span>  
 <span data-ttu-id="f5410-147">데이터 샘플링 마법사에서 모델 학습 및 테스트에 사용되는 균형 잡힌 데이터 집합을 만드는 방법은 두 가지입니다.</span><span class="sxs-lookup"><span data-stu-id="f5410-147">The Sample Data wizard provides two methods for creating balanced data sets for training and testing models.</span></span>  
  
-   <span data-ttu-id="f5410-148">**무작위 샘플링.**</span><span class="sxs-lookup"><span data-stu-id="f5410-148">**Random sampling.**</span></span> <span data-ttu-id="f5410-149">학습 또는 테스트에 사용하기 위해 큰 데이터 집합에서 대표성을 지닌 데이터 집합을 추출하려면 이 옵션을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="f5410-149">Use this option to extract a representative set of data from a larger data set, for use in either training or testing.</span></span> <span data-ttu-id="f5410-150">데이터 마이닝 추가 기능은 *층 화 샘플링* 을 사용 하 여 샘플링 된 각 변수에 대해 분산 된 값 집합을 얻을 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="f5410-150">The Data Mining Add-ins use *stratified sampling* to ensure that a balanced set of values is obtained for each variable sampled.</span></span>  
  
-   <span data-ttu-id="f5410-151">**과다 샘플링.**</span><span class="sxs-lookup"><span data-stu-id="f5410-151">**Oversampling.**</span></span> <span data-ttu-id="f5410-152">대상 결과에 사용하려는 것보다 데이터의 양이 적고 해당 데이터의 가중치를 높게 잡아야 하는 경우 이 옵션을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="f5410-152">Use this option when you have less data than you would like for a target outcome, and need to weight that data more heavily.</span></span> <span data-ttu-id="f5410-153">예를 들어 부정 행위가 거의 발생하지 않을 수 있지만 부정 행위와 관련된 사례를 과다 샘플링하여 모델링에 충분한 데이터를 구할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f5410-153">For example, fraud might be relatively rare, but you can oversample cases involving fraud to get adequate data for modeling.</span></span>  
  
 <span data-ttu-id="f5410-154">[데이터 마이닝 추가 기능을&#41;SQL Server 예제 데이터 &#40;](sample-data-sql-server-data-mining-add-ins.md)입니다.</span><span class="sxs-lookup"><span data-stu-id="f5410-154">[Sample Data &#40;SQL Server Data Mining Add-ins&#41;](sample-data-sql-server-data-mining-add-ins.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5410-155">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f5410-155">See Also</span></span>  
 <span data-ttu-id="f5410-156">[데이터 마이닝 모델 만들기](creating-a-data-mining-model.md) </span><span class="sxs-lookup"><span data-stu-id="f5410-156">[Creating a Data Mining Model](creating-a-data-mining-model.md) </span></span>  
 <span data-ttu-id="f5410-157">[Excel 용 데이터 마이닝 추가 기능에 대 한 예측 &#40;모델 유효성 검사 및 모델 사용&#41;](validating-models-and-using-models-for-prediction-data-mining-add-ins-for-excel.md) </span><span class="sxs-lookup"><span data-stu-id="f5410-157">[Validating Models and Using Models for Prediction &#40;Data Mining Add-ins for Excel&#41;](validating-models-and-using-models-for-prediction-data-mining-add-ins-for-excel.md) </span></span>  
 [<span data-ttu-id="f5410-158">Excel 용 데이터 마이닝 추가 기능 &#40;마이닝 모델 배포 및 확장&#41;</span><span class="sxs-lookup"><span data-stu-id="f5410-158">Deploying and Scaling Mining Models &#40;Data Mining Add-ins for Excel&#41;</span></span>](deploying-and-scaling-mining-models-data-mining-add-ins-for-excel.md)  
  
  
