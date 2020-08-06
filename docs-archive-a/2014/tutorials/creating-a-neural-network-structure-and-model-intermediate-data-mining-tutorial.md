---
title: 신경망 구조 및 모델 만들기 (중급 데이터 마이닝 자습서) | Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- discretization [Analysis Services]
- DISCRETIZED column
- DiscretizationBuckets property
- DiscretizationMethod property
- EQUAL_AREAS method
ms.assetid: 3f16215c-531e-4ecf-a11f-ee7c6a764463
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 91c0210213083868eaab36cf34a05d0b7824a654
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646773"
---
# <a name="creating-a-neural-network-structure-and-model-intermediate-data-mining-tutorial"></a><span data-ttu-id="c6d68-102">신경망 구조 및 모델 만들기(중급 데이터 마이닝 자습서)</span><span class="sxs-lookup"><span data-stu-id="c6d68-102">Creating a Neural Network Structure and Model (Intermediate Data Mining Tutorial)</span></span>
  <span data-ttu-id="c6d68-103">데이터 마이닝 모델을 만들려면 먼저 데이터 마이닝 마법사를 사용하여 새 데이터 원본 뷰를 기반으로 새 마이닝 구조를 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6d68-103">To create a data mining model, you must first use the Data Mining Wizard to create a new mining structure based on the new data source view.</span></span> <span data-ttu-id="c6d68-104">이 태스크에서는 마법사를 사용하여 [!INCLUDE[msCoName](../includes/msconame-md.md)] 신경망 알고리즘 기반의 마이닝 구조를 만들고 이와 동시에 관련 마이닝 모델을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c6d68-104">In this task you will use the wizard to create a mining structure, and at the same time create an associated mining model that is based on the [!INCLUDE[msCoName](../includes/msconame-md.md)] Neural Network algorithm.</span></span>  
  
 <span data-ttu-id="c6d68-105">신경망은 매우 유연하고 많은 입력 및 출력 조합을 분석할 수 있기 때문에 최상의 결과를 얻기 위해 여러 가지 데이터 처리 방법을 시험해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6d68-105">Because neural networks are extremely flexible and can analyze many combinations of inputs and outputs, you should experiment with several ways of processing the data to get the best results.</span></span> <span data-ttu-id="c6d68-106">예를 들어 특정 비즈니스 요구 사항을 대상으로 지정 하기 위해 서비스 품질에 대 한 숫자 대상을 범주화 하거나 그룹화 *하는 방법을*사용자 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c6d68-106">For example, you might want to customize the way that the numerical target for service quality is *binned*, or grouped, to target specific business requirements.</span></span> <span data-ttu-id="c6d68-107">이렇게 하려면 숫자 데이터를 다른 방식으로 그룹화하는 새 열을 마이닝 구조에 추가한 다음 새 열을 사용하는 모델을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c6d68-107">To do this, you will add a new column to the mining structure that groups numerical data in a different way, and then create a model that uses the new column.</span></span> <span data-ttu-id="c6d68-108">이러한 마이닝 모델을 사용하여 탐색을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="c6d68-108">You will use these mining models to do some exploration.</span></span>  
  
 <span data-ttu-id="c6d68-109">마지막으로, 신경망 모델을 통해 비즈니스 질문에 가장 큰 영향을 주는 요인을 찾았으면 예측 및 평가에 사용할 별도의 모델을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6d68-109">Finally, when you have learned from the neural network model which factors have the greatest impact for your business question, you will build a separate model for prediction and scoring.</span></span> <span data-ttu-id="c6d68-110">여기서는 신경망 모델에 기반을 두지만 특정 입력을 바탕으로 솔루션을 찾도록 최적화된 [!INCLUDE[msCoName](../includes/msconame-md.md)] 로지스틱 회귀 알고리즘을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="c6d68-110">You will use the [!INCLUDE[msCoName](../includes/msconame-md.md)] Logistic Regression algorithm, which is based on the neural networks model but is optimized for finding a solution based on specific inputs.</span></span>  
  
 <span data-ttu-id="c6d68-111">**단계**</span><span class="sxs-lookup"><span data-stu-id="c6d68-111">**Steps**</span></span>  
  
 [<span data-ttu-id="c6d68-112">기본 마이닝 구조 및 모델 만들기</span><span class="sxs-lookup"><span data-stu-id="c6d68-112">Create the default mining structure and model</span></span>](#bkmk_defaul)  
  
 [<span data-ttu-id="c6d68-113">분할을 사용하여 예측 가능한 열 범주화</span><span class="sxs-lookup"><span data-stu-id="c6d68-113">Use discretization to bin the predictable column</span></span>](#bkmk_ColumnCopy)  
  
 [<span data-ttu-id="c6d68-114">열을 복사하고 다른 모델에 대한 분할 메서드 변경</span><span class="sxs-lookup"><span data-stu-id="c6d68-114">Copy the column and change the discretization method for a different model</span></span>](#bkmk_Alias)  
  
 [<span data-ttu-id="c6d68-115">모델을 비교할 수 있도록 예측 가능한 열에 대한 별칭 만들기</span><span class="sxs-lookup"><span data-stu-id="c6d68-115">Create an alias for the predictable column so that you can compare models</span></span>](#bkmk_Alias2)  
  
 [<span data-ttu-id="c6d68-116">모든 모델 처리</span><span class="sxs-lookup"><span data-stu-id="c6d68-116">Process all models</span></span>](#bkmk_SeedProcess)  
  
## <a name="create-the-default-call-center-structure"></a><span data-ttu-id="c6d68-117">기본 콜 센터 구조 만들기<a name="bkmk_defaul"></a></span><span class="sxs-lookup"><span data-stu-id="c6d68-117">Create the Default Call Center Structure  <a name="bkmk_defaul"></a></span></span>  
  
1.  <span data-ttu-id="c6d68-118">의 솔루션 탐색기에서 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] **마이닝 구조** 를 마우스 오른쪽 단추로 클릭 하 고 **새 마이닝 구조**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6d68-118">In Solution Explorer in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], right-click **Mining Structures** and select **New Mining Structure**.</span></span>  
  
2.  <span data-ttu-id="c6d68-119">**데이터 마이닝 마법사 시작** 페이지에서 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c6d68-119">On the **Welcome to the Data Mining Wizard** page, click **Next**.</span></span>  
  
3.  <span data-ttu-id="c6d68-120">**정의 방법 선택** 페이지에서 **기존 관계형 데이터베이스 또는 데이터 웨어하우스** 를 선택 했는지 확인 하 고 **다음**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6d68-120">On the **Select the Definition Method** page, verify that **From existing relational database or data warehouse** is selected, and then click **Next**.</span></span>  
  
4.  <span data-ttu-id="c6d68-121">**데이터 마이닝 구조 만들기** 페이지에서 **마이닝 모델을 사용 하 여 마이닝 구조 만들기** 옵션이 선택 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6d68-121">On the **Create the Data Mining Structure** page, verify that the option **Create mining structure with a mining model** is selected.</span></span>  
  
5.  <span data-ttu-id="c6d68-122">**사용할 데이터 마이닝 기술 선택** 옵션에 대한 드롭다운 목록을 클릭한 다음 **Microsoft 신경망**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c6d68-122">Click the dropdown list for the option **Which data mining technique do you want to use?**, then select **Microsoft Neural Networks**.</span></span>  
  
     <span data-ttu-id="c6d68-123">로지스틱 회귀 모델이 신경망을 기반으로 하기 때문에 동일한 구조를 다시 사용하여 새 마이닝 모델을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c6d68-123">Because the logistic regression models are based on the neural networks, you can reuse the same structure and add a new mining model.</span></span>  
  
6.  <span data-ttu-id="c6d68-124">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c6d68-124">Click **Next**.</span></span>  
  
     <span data-ttu-id="c6d68-125">**데이터 원본 뷰 선택** 페이지가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="c6d68-125">The **Select Data Source View** page appears.</span></span>  
  
7.  <span data-ttu-id="c6d68-126">**사용 가능한 데이터 원본 뷰**에서 `Call Center` 을 선택 하 고 **다음**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6d68-126">Under **Available data source views**, select `Call Center`, and click **Next**.</span></span>  
  
8.  <span data-ttu-id="c6d68-127">**테이블 유형 지정** 페이지에서 **FactCallCenter** 테이블 옆의 **사례** 확인란을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6d68-127">On the **Specify Table Types** page, select the **Case** check box next to the **FactCallCenter** table.</span></span> <span data-ttu-id="c6d68-128">나이 **날짜**에는 아무것도 선택 하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="c6d68-128">Do not select anything for **DimDate**.</span></span> <span data-ttu-id="c6d68-129">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c6d68-129">Click **Next**.</span></span>  
  
9. <span data-ttu-id="c6d68-130">**학습 데이터 지정** 페이지에서 FactCallCenterID 열 옆에 있는 **키** 를 선택 합니다 **.**</span><span class="sxs-lookup"><span data-stu-id="c6d68-130">On the **Specify the Training Data** page, select **Key** next to the column **FactCallCenterID.**</span></span>  
  
10. <span data-ttu-id="c6d68-131">`Predict`및 **입력** 확인란을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6d68-131">Select the `Predict` and **Input** check boxes.</span></span>  
  
11. <span data-ttu-id="c6d68-132">다음 표와 같이 **키**, **입력**및 확인란을 선택 합니다 `Predict` .</span><span class="sxs-lookup"><span data-stu-id="c6d68-132">Select the **Key**, **Input**, and `Predict` check boxes as shown in the following table:</span></span>  
  
    |<span data-ttu-id="c6d68-133">테이블/열</span><span class="sxs-lookup"><span data-stu-id="c6d68-133">Tables/Columns</span></span>|<span data-ttu-id="c6d68-134">키/입력/예측</span><span class="sxs-lookup"><span data-stu-id="c6d68-134">Key/Input/Predict</span></span>|  
    |---------------------|-------------------------|  
    |<span data-ttu-id="c6d68-135">AutomaticResponses</span><span class="sxs-lookup"><span data-stu-id="c6d68-135">AutomaticResponses</span></span>|<span data-ttu-id="c6d68-136">입력</span><span class="sxs-lookup"><span data-stu-id="c6d68-136">Input</span></span>|  
    |<span data-ttu-id="c6d68-137">AverageTimePerIssue</span><span class="sxs-lookup"><span data-stu-id="c6d68-137">AverageTimePerIssue</span></span>|<span data-ttu-id="c6d68-138">입력/예측</span><span class="sxs-lookup"><span data-stu-id="c6d68-138">Input/Predict</span></span>|  
    |<span data-ttu-id="c6d68-139">호출</span><span class="sxs-lookup"><span data-stu-id="c6d68-139">Calls</span></span>|<span data-ttu-id="c6d68-140">입력</span><span class="sxs-lookup"><span data-stu-id="c6d68-140">Input</span></span>|  
    |<span data-ttu-id="c6d68-141">DateKey</span><span class="sxs-lookup"><span data-stu-id="c6d68-141">DateKey</span></span>|<span data-ttu-id="c6d68-142">사용 안 함</span><span class="sxs-lookup"><span data-stu-id="c6d68-142">Do not use</span></span>|  
    |<span data-ttu-id="c6d68-143">DayOfWeek</span><span class="sxs-lookup"><span data-stu-id="c6d68-143">DayOfWeek</span></span>|<span data-ttu-id="c6d68-144">입력</span><span class="sxs-lookup"><span data-stu-id="c6d68-144">Input</span></span>|  
    |<span data-ttu-id="c6d68-145">FactCallCenterID</span><span class="sxs-lookup"><span data-stu-id="c6d68-145">FactCallCenterID</span></span>|<span data-ttu-id="c6d68-146">키</span><span class="sxs-lookup"><span data-stu-id="c6d68-146">Key</span></span>|  
    |<span data-ttu-id="c6d68-147">IssuesRaised</span><span class="sxs-lookup"><span data-stu-id="c6d68-147">IssuesRaised</span></span>|<span data-ttu-id="c6d68-148">입력</span><span class="sxs-lookup"><span data-stu-id="c6d68-148">Input</span></span>|  
    |<span data-ttu-id="c6d68-149">LevelOneOperators</span><span class="sxs-lookup"><span data-stu-id="c6d68-149">LevelOneOperators</span></span>|<span data-ttu-id="c6d68-150">입력/예측</span><span class="sxs-lookup"><span data-stu-id="c6d68-150">Input/Predict</span></span>|  
    |<span data-ttu-id="c6d68-151">LevelTwoOperators</span><span class="sxs-lookup"><span data-stu-id="c6d68-151">LevelTwoOperators</span></span>|<span data-ttu-id="c6d68-152">입력</span><span class="sxs-lookup"><span data-stu-id="c6d68-152">Input</span></span>|  
    |<span data-ttu-id="c6d68-153">Orders</span><span class="sxs-lookup"><span data-stu-id="c6d68-153">Orders</span></span>|<span data-ttu-id="c6d68-154">입력/예측</span><span class="sxs-lookup"><span data-stu-id="c6d68-154">Input/Predict</span></span>|  
    |<span data-ttu-id="c6d68-155">ServiceGrade</span><span class="sxs-lookup"><span data-stu-id="c6d68-155">ServiceGrade</span></span>|<span data-ttu-id="c6d68-156">입력/예측</span><span class="sxs-lookup"><span data-stu-id="c6d68-156">Input/Predict</span></span>|  
    |<span data-ttu-id="c6d68-157">Shift</span><span class="sxs-lookup"><span data-stu-id="c6d68-157">Shift</span></span>|<span data-ttu-id="c6d68-158">입력</span><span class="sxs-lookup"><span data-stu-id="c6d68-158">Input</span></span>|  
    |<span data-ttu-id="c6d68-159">TotalOperators</span><span class="sxs-lookup"><span data-stu-id="c6d68-159">TotalOperators</span></span>|<span data-ttu-id="c6d68-160">사용 안 함</span><span class="sxs-lookup"><span data-stu-id="c6d68-160">Do not use</span></span>|  
    |<span data-ttu-id="c6d68-161">WageType</span><span class="sxs-lookup"><span data-stu-id="c6d68-161">WageType</span></span>|<span data-ttu-id="c6d68-162">입력</span><span class="sxs-lookup"><span data-stu-id="c6d68-162">Input</span></span>|  
  
     <span data-ttu-id="c6d68-163">여러 개의 예측 가능한 열이 선택되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c6d68-163">Note that multiple predictable columns have been selected.</span></span> <span data-ttu-id="c6d68-164">신경망 알고리즘의 강점 중 하나는 입력 및 출력 특성의 가능한 모든 조합을 분석할 수 있다는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="c6d68-164">One of the strengths of the neural network algorithm is that it can analyze all possible combinations of input and output attributes.</span></span> <span data-ttu-id="c6d68-165">대량 데이터 집합에 대해이 작업을 수행 하지 않는 것이 좋습니다 .이 경우 처리 시간이 크게 늘어날 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c6d68-165">You wouldn't want to do this for a large data set, as it could exponentially increase processing time..</span></span>  
  
12. <span data-ttu-id="c6d68-166">**열 내용 및 데이터 형식 지정** 페이지에서 다음 표와 같이 표에 열, 내용 유형 및 데이터 형식이 포함 되어 있는지 확인 한 **후 다음을 클릭 합니다**.</span><span class="sxs-lookup"><span data-stu-id="c6d68-166">On the **Specify Columns' Content and Data Type** page, verify that the grid contains the columns, content types, and data types as shown in the following table, and then click **Next**.</span></span>  
  
    |<span data-ttu-id="c6d68-167">열</span><span class="sxs-lookup"><span data-stu-id="c6d68-167">Columns</span></span>|<span data-ttu-id="c6d68-168">콘텐츠 유형</span><span class="sxs-lookup"><span data-stu-id="c6d68-168">Content Type</span></span>|<span data-ttu-id="c6d68-169">데이터 형식</span><span class="sxs-lookup"><span data-stu-id="c6d68-169">Data Types</span></span>|  
    |-------------|------------------|----------------|  
    |<span data-ttu-id="c6d68-170">AutomaticResponses</span><span class="sxs-lookup"><span data-stu-id="c6d68-170">AutomaticResponses</span></span>|<span data-ttu-id="c6d68-171">계속</span><span class="sxs-lookup"><span data-stu-id="c6d68-171">Continuous</span></span>|<span data-ttu-id="c6d68-172">Long</span><span class="sxs-lookup"><span data-stu-id="c6d68-172">Long</span></span>|  
    |<span data-ttu-id="c6d68-173">AverageTimePerIssue</span><span class="sxs-lookup"><span data-stu-id="c6d68-173">AverageTimePerIssue</span></span>|<span data-ttu-id="c6d68-174">계속</span><span class="sxs-lookup"><span data-stu-id="c6d68-174">Continuous</span></span>|<span data-ttu-id="c6d68-175">Long</span><span class="sxs-lookup"><span data-stu-id="c6d68-175">Long</span></span>|  
    |<span data-ttu-id="c6d68-176">호출</span><span class="sxs-lookup"><span data-stu-id="c6d68-176">Calls</span></span>|<span data-ttu-id="c6d68-177">계속</span><span class="sxs-lookup"><span data-stu-id="c6d68-177">Continuous</span></span>|<span data-ttu-id="c6d68-178">Long</span><span class="sxs-lookup"><span data-stu-id="c6d68-178">Long</span></span>|  
    |<span data-ttu-id="c6d68-179">DayOfWeek</span><span class="sxs-lookup"><span data-stu-id="c6d68-179">DayOfWeek</span></span>|<span data-ttu-id="c6d68-180">불연속</span><span class="sxs-lookup"><span data-stu-id="c6d68-180">Discrete</span></span>|<span data-ttu-id="c6d68-181">텍스트</span><span class="sxs-lookup"><span data-stu-id="c6d68-181">Text</span></span>|  
    |<span data-ttu-id="c6d68-182">FactCallCenterID</span><span class="sxs-lookup"><span data-stu-id="c6d68-182">FactCallCenterID</span></span>|<span data-ttu-id="c6d68-183">키</span><span class="sxs-lookup"><span data-stu-id="c6d68-183">Key</span></span>|<span data-ttu-id="c6d68-184">Long</span><span class="sxs-lookup"><span data-stu-id="c6d68-184">Long</span></span>|  
    |<span data-ttu-id="c6d68-185">IssuesRaised</span><span class="sxs-lookup"><span data-stu-id="c6d68-185">IssuesRaised</span></span>|<span data-ttu-id="c6d68-186">계속</span><span class="sxs-lookup"><span data-stu-id="c6d68-186">Continuous</span></span>|<span data-ttu-id="c6d68-187">Long</span><span class="sxs-lookup"><span data-stu-id="c6d68-187">Long</span></span>|  
    |<span data-ttu-id="c6d68-188">LevelOneOperators</span><span class="sxs-lookup"><span data-stu-id="c6d68-188">LevelOneOperators</span></span>|<span data-ttu-id="c6d68-189">계속</span><span class="sxs-lookup"><span data-stu-id="c6d68-189">Continuous</span></span>|<span data-ttu-id="c6d68-190">Long</span><span class="sxs-lookup"><span data-stu-id="c6d68-190">Long</span></span>|  
    |<span data-ttu-id="c6d68-191">LevelTwoOperators</span><span class="sxs-lookup"><span data-stu-id="c6d68-191">LevelTwoOperators</span></span>|<span data-ttu-id="c6d68-192">계속</span><span class="sxs-lookup"><span data-stu-id="c6d68-192">Continuous</span></span>|<span data-ttu-id="c6d68-193">Long</span><span class="sxs-lookup"><span data-stu-id="c6d68-193">Long</span></span>|  
    |<span data-ttu-id="c6d68-194">Orders</span><span class="sxs-lookup"><span data-stu-id="c6d68-194">Orders</span></span>|<span data-ttu-id="c6d68-195">계속</span><span class="sxs-lookup"><span data-stu-id="c6d68-195">Continuous</span></span>|<span data-ttu-id="c6d68-196">Long</span><span class="sxs-lookup"><span data-stu-id="c6d68-196">Long</span></span>|  
    |<span data-ttu-id="c6d68-197">ServiceGrade</span><span class="sxs-lookup"><span data-stu-id="c6d68-197">ServiceGrade</span></span>|<span data-ttu-id="c6d68-198">계속</span><span class="sxs-lookup"><span data-stu-id="c6d68-198">Continuous</span></span>|<span data-ttu-id="c6d68-199">Double</span><span class="sxs-lookup"><span data-stu-id="c6d68-199">Double</span></span>|  
    |<span data-ttu-id="c6d68-200">Shift</span><span class="sxs-lookup"><span data-stu-id="c6d68-200">Shift</span></span>|<span data-ttu-id="c6d68-201">불연속</span><span class="sxs-lookup"><span data-stu-id="c6d68-201">Discrete</span></span>|<span data-ttu-id="c6d68-202">텍스트</span><span class="sxs-lookup"><span data-stu-id="c6d68-202">Text</span></span>|  
    |<span data-ttu-id="c6d68-203">WageType</span><span class="sxs-lookup"><span data-stu-id="c6d68-203">WageType</span></span>|<span data-ttu-id="c6d68-204">불연속</span><span class="sxs-lookup"><span data-stu-id="c6d68-204">Discrete</span></span>|<span data-ttu-id="c6d68-205">텍스트</span><span class="sxs-lookup"><span data-stu-id="c6d68-205">Text</span></span>|  
  
13. <span data-ttu-id="c6d68-206">**테스트 집합 만들기** 페이지에서 **테스트용 데이터 비율**옵션에 대 한 텍스트 상자의 선택을 취소 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6d68-206">On the **Create testing set** page, clear the text box for the option, **Percentage of data for testing**.</span></span> <span data-ttu-id="c6d68-207">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c6d68-207">Click **Next**.</span></span>  
  
14. <span data-ttu-id="c6d68-208">**마법사 완료** 페이지에서 **마이닝 구조 이름**에을 입력 `Call Center` 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6d68-208">On the **Completing the Wizard** page, for the **Mining structure name**, type `Call Center`.</span></span>  
  
15. <span data-ttu-id="c6d68-209">**마이닝 모델 이름**에를 입력 한 `Call Center Default NN` 다음 **마침**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6d68-209">For the **Mining model name**, type `Call Center Default NN`, and then click **Finish**.</span></span>  
  
     <span data-ttu-id="c6d68-210">신경망 모델을 사용 하 여 데이터로 드릴스루할 수 없으므로 **드릴스루 허용** 상자를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c6d68-210">The **Allow drill through** box is disabled because you cannot drill through to data with neural network models.</span></span>  
  
16. <span data-ttu-id="c6d68-211">솔루션 탐색기에서 방금 만든 데이터 마이닝 구조의 이름을 마우스 오른쪽 단추로 클릭 하 고 **처리**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6d68-211">In Solution Explorer, right-click the name of the data mining structure that you just created, and select **Process**.</span></span>  
  
## <a name="use-discretization-to-bin-the-target-column"></a><span data-ttu-id="c6d68-212">분할을 사용하여 대상 열 범주화</span><span class="sxs-lookup"><span data-stu-id="c6d68-212">Use Discretization to Bin the Target Column</span></span>  
 <span data-ttu-id="c6d68-213">기본적으로 예측 가능한 숫자 특성을 포함하는 신경망 모델을 만들 때 Microsoft 신경망 알고리즘은 특성을 연속 숫자로 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="c6d68-213">By default, when you create a neural network model that has a numeric predictable attribute, the Microsoft Neural Network algorithm treats the attribute as a continuous number.</span></span> <span data-ttu-id="c6d68-214">예를 들어 ServiceGrade 특성은 이론상으로 0.00(모든 호출이 응답됨)에서 1.00(모든 호출자가 호출을 중단함)에 이르는 숫자입니다.</span><span class="sxs-lookup"><span data-stu-id="c6d68-214">For example, the ServiceGrade attribute is a number that theoretically ranges from 0.00 (all calls are answered) to 1.00 (all callers hang up).</span></span> <span data-ttu-id="c6d68-215">이 데이터 집합의 경우 값이 다음과 같이 분포됩니다.</span><span class="sxs-lookup"><span data-stu-id="c6d68-215">In this data set, the values have the following distribution:</span></span>  
  
 <span data-ttu-id="c6d68-216">![서비스 등급 값 분포](../../2014/tutorials/media/skt-service-grade-valuesc.gif "서비스 등급 값 분포")</span><span class="sxs-lookup"><span data-stu-id="c6d68-216">![distribution of service grade values](../../2014/tutorials/media/skt-service-grade-valuesc.gif "distribution of service grade values")</span></span>  
  
 <span data-ttu-id="c6d68-217">따라서 모델을 처리할 때 출력이 예상과 다르게 그룹화될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c6d68-217">As a result, when you process the model the outputs might be grouped differently than you expect.</span></span> <span data-ttu-id="c6d68-218">예를 들어 클러스터링을 사용 하 여 가장 적합 한 값 그룹을 식별 하는 경우 알고리즘은 ServiceGrade의 값을 0.0748051948-0.09716216215와 같은 범위로 나눕니다.</span><span class="sxs-lookup"><span data-stu-id="c6d68-218">For example, if you use clustering to identify the best groups of values, the algorithm divides the values in ServiceGrade into ranges such as this one: 0.0748051948 - 0.09716216215.</span></span> <span data-ttu-id="c6d68-219">이 그룹화가 수학적으로 정확하기는 하지만 비즈니스 사용자에게는 이러한 범위가 의미가 없을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c6d68-219">Although this grouping is mathematically accurate, such ranges might not be as meaningful to business users.</span></span>  
  
 <span data-ttu-id="c6d68-220">이 단계에서는 결과를 보다 직관적으로 만들기 위해 숫자 값을 다르게 그룹화 하 여 숫자 데이터 열의 복사본을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c6d68-220">In this step, to make the result more intuitive, you'll group the numerical values differently, creating copies of the numerical data column.</span></span>  
  
### <a name="how-discretization-works"></a><span data-ttu-id="c6d68-221">분할 작동 방법</span><span class="sxs-lookup"><span data-stu-id="c6d68-221">How Discretization Works</span></span>  
 <span data-ttu-id="c6d68-222">Analysis Services에서는 숫자 데이터를 범주화하거나 처리하는 다양한 방법을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="c6d68-222">Analysis Services provides a variety of methods for binning or processing numerical data.</span></span> <span data-ttu-id="c6d68-223">다음 표에서는 출력 특성 ServiceGrade를 세 가지 방식으로 처리했을 때 결과의 차이를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="c6d68-223">The following table illustrates the differences between the results when the output attribute ServiceGrade has been processed three different ways:</span></span>  
  
-   <span data-ttu-id="c6d68-224">연속 숫자로 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="c6d68-224">Treating it as a continuous number.</span></span>  
  
-   <span data-ttu-id="c6d68-225">알고리즘이 클러스터링을 사용하여 최적의 값 배열을 식별하도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c6d68-225">Having the algorithm use clustering to identify the best arrangement of values.</span></span>  
  
-   <span data-ttu-id="c6d68-226">Equal Areas 메서드를 사용하여 숫자를 범주화하도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c6d68-226">Specifying that the numbers be binned by the Equal Areas method.</span></span>  
  
 <span data-ttu-id="c6d68-227">기본 모델(연속)</span><span class="sxs-lookup"><span data-stu-id="c6d68-227">Default model (continuous)</span></span>  
  
|<span data-ttu-id="c6d68-228">값</span><span class="sxs-lookup"><span data-stu-id="c6d68-228">VALUE</span></span>|<span data-ttu-id="c6d68-229">별칭</span><span class="sxs-lookup"><span data-stu-id="c6d68-229">SUPPORT</span></span>|  
|-----------|-------------|  
|<span data-ttu-id="c6d68-230">Missing</span><span class="sxs-lookup"><span data-stu-id="c6d68-230">Missing</span></span>|<span data-ttu-id="c6d68-231">0</span><span class="sxs-lookup"><span data-stu-id="c6d68-231">0</span></span>|  
|<span data-ttu-id="c6d68-232">0.09875</span><span class="sxs-lookup"><span data-stu-id="c6d68-232">0.09875</span></span>|<span data-ttu-id="c6d68-233">120</span><span class="sxs-lookup"><span data-stu-id="c6d68-233">120</span></span>|  
  
 <span data-ttu-id="c6d68-234">클러스터링에 의한 범주화</span><span class="sxs-lookup"><span data-stu-id="c6d68-234">Binned by clustering</span></span>  
  
|<span data-ttu-id="c6d68-235">값</span><span class="sxs-lookup"><span data-stu-id="c6d68-235">VALUE</span></span>|<span data-ttu-id="c6d68-236">별칭</span><span class="sxs-lookup"><span data-stu-id="c6d68-236">SUPPORT</span></span>|  
|-----------|-------------|  
|<span data-ttu-id="c6d68-237">\<0.0748051948</span><span class="sxs-lookup"><span data-stu-id="c6d68-237">\< 0.0748051948</span></span>|<span data-ttu-id="c6d68-238">34</span><span class="sxs-lookup"><span data-stu-id="c6d68-238">34</span></span>|  
|<span data-ttu-id="c6d68-239">0.0748051948-0.09716216215</span><span class="sxs-lookup"><span data-stu-id="c6d68-239">0.0748051948 - 0.09716216215</span></span>|<span data-ttu-id="c6d68-240">27</span><span class="sxs-lookup"><span data-stu-id="c6d68-240">27</span></span>|  
|<span data-ttu-id="c6d68-241">0.09716216215 - 0.13297297295</span><span class="sxs-lookup"><span data-stu-id="c6d68-241">0.09716216215 - 0.13297297295</span></span>|<span data-ttu-id="c6d68-242">39</span><span class="sxs-lookup"><span data-stu-id="c6d68-242">39</span></span>|  
|<span data-ttu-id="c6d68-243">0.13297297295 - 0.167499999975</span><span class="sxs-lookup"><span data-stu-id="c6d68-243">0.13297297295 - 0.167499999975</span></span>|<span data-ttu-id="c6d68-244">10</span><span class="sxs-lookup"><span data-stu-id="c6d68-244">10</span></span>|  
|<span data-ttu-id="c6d68-245">>= 0.167499999975</span><span class="sxs-lookup"><span data-stu-id="c6d68-245">>= 0.167499999975</span></span>|<span data-ttu-id="c6d68-246">10</span><span class="sxs-lookup"><span data-stu-id="c6d68-246">10</span></span>|  
  
 <span data-ttu-id="c6d68-247">Equal Areas에 의한 범주화</span><span class="sxs-lookup"><span data-stu-id="c6d68-247">Binned by equal areas</span></span>  
  
|<span data-ttu-id="c6d68-248">값</span><span class="sxs-lookup"><span data-stu-id="c6d68-248">VALUE</span></span>|<span data-ttu-id="c6d68-249">별칭</span><span class="sxs-lookup"><span data-stu-id="c6d68-249">SUPPORT</span></span>|  
|-----------|-------------|  
|<span data-ttu-id="c6d68-250">\<0.07</span><span class="sxs-lookup"><span data-stu-id="c6d68-250">\< 0.07</span></span>|<span data-ttu-id="c6d68-251">26</span><span class="sxs-lookup"><span data-stu-id="c6d68-251">26</span></span>|  
|<span data-ttu-id="c6d68-252">0.07-0.00</span><span class="sxs-lookup"><span data-stu-id="c6d68-252">0.07 - 0.00</span></span>|<span data-ttu-id="c6d68-253">22</span><span class="sxs-lookup"><span data-stu-id="c6d68-253">22</span></span>|  
|<span data-ttu-id="c6d68-254">0.09-0.11</span><span class="sxs-lookup"><span data-stu-id="c6d68-254">0.09 - 0.11</span></span>|<span data-ttu-id="c6d68-255">36</span><span class="sxs-lookup"><span data-stu-id="c6d68-255">36</span></span>|  
|<span data-ttu-id="c6d68-256">>= 0.12</span><span class="sxs-lookup"><span data-stu-id="c6d68-256">>= 0.12</span></span>|<span data-ttu-id="c6d68-257">36</span><span class="sxs-lookup"><span data-stu-id="c6d68-257">36</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="c6d68-258">이러한 통계는 모든 데이터를 처리한 후 모델의 한계 통계 노드에서 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c6d68-258">You can obtain these statistics from the marginal statistics node of the model, after all the data has been processed.</span></span> <span data-ttu-id="c6d68-259">한계 통계 노드에 대 한 자세한 내용은 [Analysis Services 데이터 마이닝&#41;&#40;신경망 모델에 대 한 마이닝 모델 콘텐츠 ](../../2014/analysis-services/data-mining/mining-model-content-for-neural-network-models-analysis-services-data-mining.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="c6d68-259">For more information about the marginal statistics node, see [Mining Model Content for Neural Network Models &#40;Analysis Services - Data Mining&#41;](../../2014/analysis-services/data-mining/mining-model-content-for-neural-network-models-analysis-services-data-mining.md).</span></span>  
  
 <span data-ttu-id="c6d68-260">이 테이블에서 VALUE 열은 ServiceGrade 수가 어떻게 처리되었는지를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="c6d68-260">In this table, the VALUE column shows you how the number for ServiceGrade has been handled.</span></span> <span data-ttu-id="c6d68-261">SUPPORT 열은 해당 값을 갖고 있거나 해당 범위에 속한 사례 수를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="c6d68-261">The SUPPORT column shows you how many cases had that value, or that fell in that range.</span></span>  
  
-   <span data-ttu-id="c6d68-262">**연속 숫자 사용(기본값)**</span><span class="sxs-lookup"><span data-stu-id="c6d68-262">**Use continuous numbers (default)**</span></span>  
  
     <span data-ttu-id="c6d68-263">기본 메서드를 사용한 경우 알고리즘은 평균 값이 0.09875인 고유 값 120에 대한 결과를 컴퓨팅합니다.</span><span class="sxs-lookup"><span data-stu-id="c6d68-263">If you used the default method, the algorithm would compute outcomes for 120 distinct values, the mean value of which is 0.09875.</span></span> <span data-ttu-id="c6d68-264">또한 누락된 값의 개수도 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c6d68-264">You can also see the number of missing values.</span></span>  
  
-   <span data-ttu-id="c6d68-265">**클러스터링에 의한 범주화**</span><span class="sxs-lookup"><span data-stu-id="c6d68-265">**Bin by clustering**</span></span>  
  
     <span data-ttu-id="c6d68-266">Microsoft 클러스터링 알고리즘에서 선택 사항인 값의 그룹화를 결정하도록 한 경우, 알고리즘은 ServiceGrade에 대한 값을 다섯 개의 범위로 그룹화합니다.</span><span class="sxs-lookup"><span data-stu-id="c6d68-266">When you let the Microsoft Clustering algorithm determine the optional grouping of values, the algorithm would group the values for ServiceGrade into five (5) ranges.</span></span> <span data-ttu-id="c6d68-267">SUPPORT 열로부터 알 수 있듯, 각 범위의 사례 수는 고르게 분산되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c6d68-267">The number of cases in each range is not evenly distributed, as you can see from the support column.</span></span>  
  
-   <span data-ttu-id="c6d68-268">**Equal Areas에 의한 범주화**</span><span class="sxs-lookup"><span data-stu-id="c6d68-268">**Bin by equal areas**</span></span>  
  
     <span data-ttu-id="c6d68-269">이 메서드를 선택한 경우 알고리즘은 동일한 크기의 버킷에 값을 강제로 집어넣어 결과적으로 각 범위의 상한 및 하한이 변경됩니다.</span><span class="sxs-lookup"><span data-stu-id="c6d68-269">When you choose this method, the algorithm forces the values into buckets of equal size, which in turn changes the upper and lower bounds of each range.</span></span> <span data-ttu-id="c6d68-270">버킷 수를 지정할 수는 있지만 버킷에 너무 적은 수의 값이 포함되지 않도록 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="c6d68-270">You can specify the number of buckets, but you want to avoid having two few values in any bucket.</span></span>  
  
 <span data-ttu-id="c6d68-271">범주화 옵션에 대 한 자세한 내용은 [데이터 마이닝&#41;&#40;분할 방법 ](../../2014/analysis-services/data-mining/discretization-methods-data-mining.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="c6d68-271">For more information about binning options, see [Discretization Methods &#40;Data Mining&#41;](../../2014/analysis-services/data-mining/discretization-methods-data-mining.md).</span></span>  
  
 <span data-ttu-id="c6d68-272">또는 숫자 값을 사용 하는 것 보다는 서비스 등급을 미리 정의 된 대상 범위로 분류 하는 별도의 파생 열을 추가할 수 있습니다 (예: **Best** (servicegrade \<= 0.05), **Acceptable** (0.10 > servicegrade > **Poor** 0.05) 0.10 >).</span><span class="sxs-lookup"><span data-stu-id="c6d68-272">Alternatively, rather than using the numeric values, you could add a separate derived column that classifies the service grades into predefined target ranges, such as **Best** (ServiceGrade \<= 0.05), **Acceptable** (0.10 > ServiceGrade > 0.05), and **Poor** (ServiceGrade >= 0.10).</span></span>  
  
###  <a name="create-a-copy-of-a-column-and-change-the-discretization-method"></a><a name="bkmk_newColumn"></a><span data-ttu-id="c6d68-273">열의 복사본을 만들고 분할 메서드를 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6d68-273">Create a Copy of a Column and Change the Discretization Method</span></span>  
 <span data-ttu-id="c6d68-274">대상 특성인 ServiceGrade를 포함 하는 마이닝 열의 복사본을 만들고 숫자를 그룹화 하는 방법을 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6d68-274">You'll make a copy of the mining column that contains the target attribute, ServiceGrade and change the way the numbers are grouped.</span></span> <span data-ttu-id="c6d68-275">예측 가능한 특성을 비롯하여 임의의 열의 여러 복사본을 마이닝 구조에서 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c6d68-275">You can create multiple copies of any column in a mining structure, including the predictable attribute.</span></span>  
  
 <span data-ttu-id="c6d68-276">이 자습서에서는 Equal Areas 분할 메서드를 사용하고 4개의 버킷을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c6d68-276">For this tutorial, you will use the Equal Areas method of discretization, and specify four buckets.</span></span> <span data-ttu-id="c6d68-277">이 메서드에서 생성되는 그룹화는 비즈니스 사용자가 관심을 가지는 대상 값에 매우 근접해 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c6d68-277">The groupings that result from this method are fairly close to the target values of interest to your business users.</span></span>  
  
####  <a name="to-create-a-customized-copy-of-a-column-in-the-mining-structure"></a><a name="bkmk_ColumnCopy"></a><span data-ttu-id="c6d68-278">마이닝 구조에 열에 대 한 사용자 지정 복사본을 만들려면</span><span class="sxs-lookup"><span data-stu-id="c6d68-278">To create a customized copy of a column in the mining structure</span></span>  
  
1.  <span data-ttu-id="c6d68-279">솔루션 탐색기에서 앞에서 만든 마이닝 구조를 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c6d68-279">In Solution Explorer, double-click the mining structure that you just created.</span></span>  
  
2.  <span data-ttu-id="c6d68-280">마이닝 구조 탭에서 **마이닝 구조 열 추가**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6d68-280">In the Mining Structure tab, click **Add a mining structure column**.</span></span>  
  
3.  <span data-ttu-id="c6d68-281">**열 선택** 대화 상자의 **원본 열**목록에서 servicegrade를 선택 하 고 **확인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6d68-281">In the **Select column** dialog box, select ServiceGrade from the list in **Source column**, then click **OK**.</span></span>  
  
     <span data-ttu-id="c6d68-282">새 열이 마이닝 구조 열의 목록에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="c6d68-282">A new column is added to the list of mining structure columns.</span></span> <span data-ttu-id="c6d68-283">기본적으로 새 마이닝 열의 이름은 기존 열의 이름과 같으며 ServiceGrade 1과 같이 뒤에 숫자가 붙습니다.</span><span class="sxs-lookup"><span data-stu-id="c6d68-283">By default, the new mining column has the same name as the existing column, with a numerical postfix: for example, ServiceGrade 1.</span></span> <span data-ttu-id="c6d68-284">이 열의 이름을 좀 더 구체적인 이름으로 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c6d68-284">You can change the name of this column to be more descriptive.</span></span>  
  
     <span data-ttu-id="c6d68-285">분할 메서드도 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c6d68-285">You will also specify the discretization method.</span></span>  
  
4.  <span data-ttu-id="c6d68-286">ServiceGrade 1을 마우스 오른쪽 단추로 클릭 하 고 **속성**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6d68-286">Right-click ServiceGrade 1 and select **Properties**.</span></span>  
  
5.  <span data-ttu-id="c6d68-287">**속성** 창에서 **이름** 속성을 찾아 이름을 **서비스 등급** 에 맞게 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6d68-287">In the **Properties** window, locate the **Name** property, and change the name to **Service Grade Binned** .</span></span>  
  
6.  <span data-ttu-id="c6d68-288">관련된 모든 마이닝 모델 열의 이름을 동일하게 변경할 것인지 묻는 대화 상자가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="c6d68-288">A dialog box appears asking whether you want to make the same change to the name of all related mining model columns.</span></span> <span data-ttu-id="c6d68-289">**아니요**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c6d68-289">Click **No**.</span></span>  
  
7.  <span data-ttu-id="c6d68-290">**속성** 창에서 섹션 **데이터 형식을** 찾고 필요한 경우 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6d68-290">In the **Properties** window, locate the section **Data Type** and expand it if necessary.</span></span>  
  
8.  <span data-ttu-id="c6d68-291">`Content` 속성의 값을 `Continuous`에서 `Discretized`로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="c6d68-291">Change the value of the property `Content` from `Continuous` to `Discretized`.</span></span>  
  
     <span data-ttu-id="c6d68-292">이제 사용할 수 있는 속성은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="c6d68-292">The following properties are now available.</span></span> <span data-ttu-id="c6d68-293">다음 표에 있는 대로 속성 값을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="c6d68-293">Change the values of the properties as shown in the following table:</span></span>  
  
    |<span data-ttu-id="c6d68-294">속성</span><span class="sxs-lookup"><span data-stu-id="c6d68-294">Property</span></span>|<span data-ttu-id="c6d68-295">기본값</span><span class="sxs-lookup"><span data-stu-id="c6d68-295">Default value</span></span>|<span data-ttu-id="c6d68-296">새 값</span><span class="sxs-lookup"><span data-stu-id="c6d68-296">New value</span></span>|  
    |--------------|-------------------|---------------|  
    |`DiscretizationMethod`|`Continuous`|`EqualAreas`|  
    |`DiscretizationBucketCount`|<span data-ttu-id="c6d68-297">값 없음</span><span class="sxs-lookup"><span data-stu-id="c6d68-297">No value</span></span>|<span data-ttu-id="c6d68-298">4</span><span class="sxs-lookup"><span data-stu-id="c6d68-298">4</span></span>|  
  
    > [!NOTE]  
    >  <span data-ttu-id="c6d68-299"><xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn.DiscretizationBucketCount%2A>의 기본값은 0이며, 이는 알고리즘이 자동으로 최적의 버킷 수를 결정함을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="c6d68-299">The default value of <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn.DiscretizationBucketCount%2A> is actually 0, which means that the algorithm automatically determines the optimum number of buckets.</span></span> <span data-ttu-id="c6d68-300">따라서 이 속성 값을 기본값으로 다시 설정하려면 0을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="c6d68-300">Therefore, if you want to reset the value of this property to its default, type 0.</span></span>  
  
9. <span data-ttu-id="c6d68-301">데이터 마이닝 디자이너에서 **마이닝 모델** 탭을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6d68-301">In Data Mining Designer, click the **Mining Models** tab.</span></span>  
  
     <span data-ttu-id="c6d68-302">마이닝 구조 열의 복사본을 추가할 때 복사본의 사용법 플래그가 자동으로 `Ignore`로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="c6d68-302">Notice that when you add a copy of a mining structure column, the usage flag for the copy is automatically set to `Ignore`.</span></span> <span data-ttu-id="c6d68-303">일반적으로 열의 복사본을 마이닝 구조에 추가할 때 원래 열과 함께 분석용 복사본을 사용하지 않습니다. 복사본을 사용하면 알고리즘에서 두 열의 강한 상관 관계를 발견하므로 다른 관계가 명확하게 드러나지 않을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c6d68-303">Usually, when you add a copy of a column to a mining structure, you would not use the copy for analysis together with the original column, or the algorithm will find a strong correlation between the two columns that might obscure other relationships.</span></span>  
  
##  <a name="add-a-new-mining-model-to-the-mining-structure"></a><a name="bkmk_NewModel"></a><span data-ttu-id="c6d68-304">마이닝 구조에 새 마이닝 모델 추가</span><span class="sxs-lookup"><span data-stu-id="c6d68-304">Add a New Mining Model to the Mining Structure</span></span>  
 <span data-ttu-id="c6d68-305">대상 특성의 새로운 그룹화 방식을 만들었으므로 분할 열을 사용하는 새 마이닝 모델을 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6d68-305">Now that you have created a new grouping for the target attribute, you need to add a new mining model that uses the discretized column.</span></span> <span data-ttu-id="c6d68-306">완료하면 CallCenter 마이닝 구조에 두 가지 마이닝 모델이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="c6d68-306">When you are done, the CallCenter mining structure will have two mining models:</span></span>  
  
-   <span data-ttu-id="c6d68-307">Call Center Default NN 마이닝 모델은 ServiceGrade 값을 연속 범위로 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="c6d68-307">The mining model, Call Center Default NN, handles the ServiceGrade values as a continuous range.</span></span>  
  
-   <span data-ttu-id="c6d68-308">동일한 크기의 네 버킷으로 분산 된 ServiceGrade 열의 값을 대상으로 하는 것으로를 사용 하는 새 마이닝 모델 인 Call Center는 새 마이닝 모델을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c6d68-308">You will create a new mining model, Call Center Binned NN, that uses as its target outcomes the values of the ServiceGrade column, distributed into four buckets of equal size.</span></span>  
  
#### <a name="to-add-a-mining-model-based-on-the-new-discretized-column"></a><span data-ttu-id="c6d68-309">새로운 불연속화 열 기반의 마이닝 모델을 추가하려면</span><span class="sxs-lookup"><span data-stu-id="c6d68-309">To add a mining model based on the new discretized column</span></span>  
  
1.  <span data-ttu-id="c6d68-310">솔루션 탐색기에서 방금 만든 마이닝 구조를 마우스 오른쪽 단추로 클릭 하 고 **열기**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6d68-310">In Solution Explorer, right-click the mining structure that you just created, and select **Open**.</span></span>  
  
2.  <span data-ttu-id="c6d68-311">**마이닝 모델** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c6d68-311">Click the **Mining Models** tab.</span></span>  
  
3.  <span data-ttu-id="c6d68-312">**관련 마이닝 모델 만들기를**클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6d68-312">Click **Create a related mining model**.</span></span>  
  
4.  <span data-ttu-id="c6d68-313">**새 마이닝 모델** 대화 상자의 **모델 이름**에을 입력 `Call Center Binned NN` 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6d68-313">In the **New Mining Model** dialog box, for **Model name**, type `Call Center Binned NN`.</span></span> <span data-ttu-id="c6d68-314">**알고리즘 이름** 드롭다운 목록에서 **Microsoft 신경망**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6d68-314">In the **Algorithm name** dropdown list, select **Microsoft Neural Network**.</span></span>  
  
5.  <span data-ttu-id="c6d68-315">새 마이닝 모델에 포함된 열의 목록에서 ServiceGrade를 찾고 사용법을 `Predict`에서 `Ignore`로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="c6d68-315">In the list of columns contained in the new mining model, locate ServiceGrade, and change the usage from `Predict` to `Ignore`.</span></span>  
  
6.  <span data-ttu-id="c6d68-316">이와 마찬가지로 ServiceGrade Binned를 찾고 사용법을 `Ignore`에서 `Predict`로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="c6d68-316">Similarly, locate ServiceGrade Binned, and change the usage from `Ignore` to `Predict`.</span></span>  
  
##  <a name="create-an-alias-for-the-target-column"></a><a name="bkmk_Alias2"></a><span data-ttu-id="c6d68-317">대상 열에 대 한 별칭 만들기</span><span class="sxs-lookup"><span data-stu-id="c6d68-317">Create an Alias for the Target Column</span></span>  
 <span data-ttu-id="c6d68-318">일반적으로 예측 가능한 여러 특성을 사용하는 마이닝 모델은 비교할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c6d68-318">Ordinarily you cannot compare mining models that use different predictable attributes.</span></span> <span data-ttu-id="c6d68-319">그러나 마이닝 모델 열의 별칭을 만들 수는 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c6d68-319">However, you can create an alias for a mining model column.</span></span> <span data-ttu-id="c6d68-320">즉, 마이닝 모델 내에서 원본 열과 동일한 이름을 갖도록 ServiceGrade 열의 이름을 바꿀 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c6d68-320">That is, you can rename the column, ServiceGrade Binned, within the mining model so that it has the same name as the original column.</span></span> <span data-ttu-id="c6d68-321">이렇게 한 다음 데이터가 다르게 분할된 경우에도 정확도 차트에서 이러한 두 모델을 직접 비교할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c6d68-321">You can then directly compare these two models in an accuracy chart, even though the data is discretized differently.</span></span>  
  
###  <a name="to-add-an-alias-for-a-mining-structure-column-in-a-mining-model"></a><a name="bkmk_Alias"></a><span data-ttu-id="c6d68-322">마이닝 모델의 마이닝 구조 열에 대 한 별칭을 추가 하려면</span><span class="sxs-lookup"><span data-stu-id="c6d68-322">To add an alias for a mining structure column in a mining model</span></span>  
  
1.  <span data-ttu-id="c6d68-323">**마이닝 모델** 탭의 **구조**에서 servicegrade 범주화를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6d68-323">In the **Mining Models** tab, under **Structure**, select ServiceGrade Binned.</span></span>  
  
     <span data-ttu-id="c6d68-324">**속성** 창에는 ScalarMiningStructure column 개체의 속성이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c6d68-324">Note that the **Properties** window displays the properties of the object, ScalarMiningStructure column.</span></span>  
  
2.  <span data-ttu-id="c6d68-325">ServiceGrade Binned NN 마이닝 모델의 열 아래에서 ServiceGrade Binned 열에 해당하는 셀을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c6d68-325">Under the column for the mining model, ServiceGrade Binned NN, click the cell corresponding to the column ServiceGrade Binned.</span></span>  
  
     <span data-ttu-id="c6d68-326">이제 **속성** 창에 MiningModelColumn 개체의 속성이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c6d68-326">Note that now the **Properties** window displays the properties for the object, MiningModelColumn.</span></span>  
  
3.  <span data-ttu-id="c6d68-327">**Name** 속성을 찾고 값을로 변경 `ServiceGrade` 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6d68-327">Locate the **Name** property, and change the value to `ServiceGrade`.</span></span>  
  
4.  <span data-ttu-id="c6d68-328">**설명** 속성을 찾고 **임시 열 별칭**을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6d68-328">Locate the **Description** property and type **Temporary column alias**.</span></span>  
  
     <span data-ttu-id="c6d68-329">**속성** 창에는 다음 정보가 포함 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6d68-329">The **Properties** window should contain the following information:</span></span>  
  
    |<span data-ttu-id="c6d68-330">속성</span><span class="sxs-lookup"><span data-stu-id="c6d68-330">Property</span></span>|<span data-ttu-id="c6d68-331">값</span><span class="sxs-lookup"><span data-stu-id="c6d68-331">Value</span></span>|  
    |--------------|-----------|  
    |<span data-ttu-id="c6d68-332">**설명**</span><span class="sxs-lookup"><span data-stu-id="c6d68-332">**Description**</span></span>|<span data-ttu-id="c6d68-333">Temporary column alias</span><span class="sxs-lookup"><span data-stu-id="c6d68-333">Temporary column alias</span></span>|  
    |<span data-ttu-id="c6d68-334">**ID**</span><span class="sxs-lookup"><span data-stu-id="c6d68-334">**ID**</span></span>|<span data-ttu-id="c6d68-335">ServiceGrade Binned</span><span class="sxs-lookup"><span data-stu-id="c6d68-335">ServiceGrade Binned</span></span>|  
    |<span data-ttu-id="c6d68-336">**모델링 플래그**</span><span class="sxs-lookup"><span data-stu-id="c6d68-336">**Modeling Flags**</span></span>||  
    |<span data-ttu-id="c6d68-337">**이름**</span><span class="sxs-lookup"><span data-stu-id="c6d68-337">**Name**</span></span>|<span data-ttu-id="c6d68-338">Service Grade</span><span class="sxs-lookup"><span data-stu-id="c6d68-338">Service Grade</span></span>|  
    |<span data-ttu-id="c6d68-339">**SourceColumn ID**</span><span class="sxs-lookup"><span data-stu-id="c6d68-339">**SourceColumn ID**</span></span>|<span data-ttu-id="c6d68-340">Service Grade 1</span><span class="sxs-lookup"><span data-stu-id="c6d68-340">Service Grade 1</span></span>|  
    |<span data-ttu-id="c6d68-341">**사용 현황**</span><span class="sxs-lookup"><span data-stu-id="c6d68-341">**Usage**</span></span>|<span data-ttu-id="c6d68-342">예측</span><span class="sxs-lookup"><span data-stu-id="c6d68-342">Predict</span></span>|  
  
5.  <span data-ttu-id="c6d68-343">**마이닝 모델** 탭에서 아무 곳 이나 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6d68-343">Click anywhere in the **Mining Model** tab.</span></span>  
  
     <span data-ttu-id="c6d68-344">표를 업데이트 하 여 열 사용 옆에 새 임시 열 별칭을 표시 합니다 `ServiceGrade` .</span><span class="sxs-lookup"><span data-stu-id="c6d68-344">The grid is updated to show the new temporary column alias, `ServiceGrade`, beside the column usage.</span></span> <span data-ttu-id="c6d68-345">마이닝 구조와 두 마이닝 모델이 포함된 표는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="c6d68-345">The grid containing the mining structure and two mining models should look like the following:</span></span>  
  
    |<span data-ttu-id="c6d68-346">구조체</span><span class="sxs-lookup"><span data-stu-id="c6d68-346">Structure</span></span>|<span data-ttu-id="c6d68-347">Call Center Default NN</span><span class="sxs-lookup"><span data-stu-id="c6d68-347">Call Center Default NN</span></span>|<span data-ttu-id="c6d68-348">Call Center Binned NN</span><span class="sxs-lookup"><span data-stu-id="c6d68-348">Call Center Binned NN</span></span>|  
    |---------------|----------------------------|---------------------------|  
    ||<span data-ttu-id="c6d68-349">Microsoft 신경망</span><span class="sxs-lookup"><span data-stu-id="c6d68-349">Microsoft Neural Network</span></span>|<span data-ttu-id="c6d68-350">Microsoft 신경망</span><span class="sxs-lookup"><span data-stu-id="c6d68-350">Microsoft Neural Network</span></span>|  
    |<span data-ttu-id="c6d68-351">AutomaticResponses</span><span class="sxs-lookup"><span data-stu-id="c6d68-351">AutomaticResponses</span></span>|<span data-ttu-id="c6d68-352">입력</span><span class="sxs-lookup"><span data-stu-id="c6d68-352">Input</span></span>|<span data-ttu-id="c6d68-353">입력</span><span class="sxs-lookup"><span data-stu-id="c6d68-353">Input</span></span>|  
    |<span data-ttu-id="c6d68-354">AverageTimePerIssue</span><span class="sxs-lookup"><span data-stu-id="c6d68-354">AverageTimePerIssue</span></span>|<span data-ttu-id="c6d68-355">예측</span><span class="sxs-lookup"><span data-stu-id="c6d68-355">Predict</span></span>|<span data-ttu-id="c6d68-356">예측</span><span class="sxs-lookup"><span data-stu-id="c6d68-356">Predict</span></span>|  
    |<span data-ttu-id="c6d68-357">호출</span><span class="sxs-lookup"><span data-stu-id="c6d68-357">Calls</span></span>|<span data-ttu-id="c6d68-358">입력</span><span class="sxs-lookup"><span data-stu-id="c6d68-358">Input</span></span>|<span data-ttu-id="c6d68-359">입력</span><span class="sxs-lookup"><span data-stu-id="c6d68-359">Input</span></span>|  
    |<span data-ttu-id="c6d68-360">DayOfWeek</span><span class="sxs-lookup"><span data-stu-id="c6d68-360">DayOfWeek</span></span>|<span data-ttu-id="c6d68-361">입력</span><span class="sxs-lookup"><span data-stu-id="c6d68-361">Input</span></span>|<span data-ttu-id="c6d68-362">입력</span><span class="sxs-lookup"><span data-stu-id="c6d68-362">Input</span></span>|  
    |<span data-ttu-id="c6d68-363">FactCallCenterID</span><span class="sxs-lookup"><span data-stu-id="c6d68-363">FactCallCenterID</span></span>|<span data-ttu-id="c6d68-364">키</span><span class="sxs-lookup"><span data-stu-id="c6d68-364">Key</span></span>|<span data-ttu-id="c6d68-365">키</span><span class="sxs-lookup"><span data-stu-id="c6d68-365">Key</span></span>|  
    |<span data-ttu-id="c6d68-366">IssuesRaised</span><span class="sxs-lookup"><span data-stu-id="c6d68-366">IssuesRaised</span></span>|<span data-ttu-id="c6d68-367">입력</span><span class="sxs-lookup"><span data-stu-id="c6d68-367">Input</span></span>|<span data-ttu-id="c6d68-368">입력</span><span class="sxs-lookup"><span data-stu-id="c6d68-368">Input</span></span>|  
    |<span data-ttu-id="c6d68-369">LevelOneOperators</span><span class="sxs-lookup"><span data-stu-id="c6d68-369">LevelOneOperators</span></span>|<span data-ttu-id="c6d68-370">입력</span><span class="sxs-lookup"><span data-stu-id="c6d68-370">Input</span></span>|<span data-ttu-id="c6d68-371">입력</span><span class="sxs-lookup"><span data-stu-id="c6d68-371">Input</span></span>|  
    |<span data-ttu-id="c6d68-372">LevelTwoOperators</span><span class="sxs-lookup"><span data-stu-id="c6d68-372">LevelTwoOperators</span></span>|<span data-ttu-id="c6d68-373">입력</span><span class="sxs-lookup"><span data-stu-id="c6d68-373">Input</span></span>|<span data-ttu-id="c6d68-374">입력</span><span class="sxs-lookup"><span data-stu-id="c6d68-374">Input</span></span>|  
    |<span data-ttu-id="c6d68-375">Orders</span><span class="sxs-lookup"><span data-stu-id="c6d68-375">Orders</span></span>|<span data-ttu-id="c6d68-376">입력</span><span class="sxs-lookup"><span data-stu-id="c6d68-376">Input</span></span>|<span data-ttu-id="c6d68-377">입력</span><span class="sxs-lookup"><span data-stu-id="c6d68-377">Input</span></span>|  
    |<span data-ttu-id="c6d68-378">ServceGrade Binned</span><span class="sxs-lookup"><span data-stu-id="c6d68-378">ServceGrade Binned</span></span>|<span data-ttu-id="c6d68-379">무시</span><span class="sxs-lookup"><span data-stu-id="c6d68-379">Ignore</span></span>|<span data-ttu-id="c6d68-380">예측(ServiceGrade)</span><span class="sxs-lookup"><span data-stu-id="c6d68-380">Predict (ServiceGrade)</span></span>|  
    |<span data-ttu-id="c6d68-381">ServiceGrade</span><span class="sxs-lookup"><span data-stu-id="c6d68-381">ServiceGrade</span></span>|<span data-ttu-id="c6d68-382">예측</span><span class="sxs-lookup"><span data-stu-id="c6d68-382">Predict</span></span>|<span data-ttu-id="c6d68-383">무시</span><span class="sxs-lookup"><span data-stu-id="c6d68-383">Ignore</span></span>|  
    |<span data-ttu-id="c6d68-384">Shift</span><span class="sxs-lookup"><span data-stu-id="c6d68-384">Shift</span></span>|<span data-ttu-id="c6d68-385">입력</span><span class="sxs-lookup"><span data-stu-id="c6d68-385">Input</span></span>|<span data-ttu-id="c6d68-386">입력</span><span class="sxs-lookup"><span data-stu-id="c6d68-386">Input</span></span>|  
    |<span data-ttu-id="c6d68-387">Total Operators</span><span class="sxs-lookup"><span data-stu-id="c6d68-387">Total Operators</span></span>|<span data-ttu-id="c6d68-388">입력</span><span class="sxs-lookup"><span data-stu-id="c6d68-388">Input</span></span>|<span data-ttu-id="c6d68-389">입력</span><span class="sxs-lookup"><span data-stu-id="c6d68-389">Input</span></span>|  
    |<span data-ttu-id="c6d68-390">WageType</span><span class="sxs-lookup"><span data-stu-id="c6d68-390">WageType</span></span>|<span data-ttu-id="c6d68-391">입력</span><span class="sxs-lookup"><span data-stu-id="c6d68-391">Input</span></span>|<span data-ttu-id="c6d68-392">입력</span><span class="sxs-lookup"><span data-stu-id="c6d68-392">Input</span></span>|  
  
## <a name="process-all-models"></a><span data-ttu-id="c6d68-393">모든 모델 처리</span><span class="sxs-lookup"><span data-stu-id="c6d68-393">Process All Models</span></span>  
 <span data-ttu-id="c6d68-394">마지막으로, 위에서 만든 모델을 쉽게 비교할 수 있도록 기본 모델과 범주화된 모델에 대한 초기값 매개 변수를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="c6d68-394">Finally, to ensure that the models you have created can be easily compared, you will set the seed parameter for both the default and binned models.</span></span> <span data-ttu-id="c6d68-395">초기값을 설정하면 각 모델이 동일한 지점에서 데이터 처리를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="c6d68-395">Setting a seed value guarantees that each model starts processing the data from the same point.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c6d68-396">초기값 매개 변수에 대한 숫자 값을 지정하지 않으면 SQL Server Analysis Services에서 모델 이름을 기반으로 하여 초기값을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="c6d68-396">If you do not specify a numeric value for the seed parameter, SQL Server Analysis Services will generate a seed based on the name of the model.</span></span> <span data-ttu-id="c6d68-397">모델의 이름은 항상 서로 다르므로 동일한 순서로 데이터를 처리하도록 초기값을 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6d68-397">Because the models always have different names, you must set a seed value to ensure that they process data in the same order.</span></span>  
  
###  <a name="to-specify-the-seed-and-process-the-models"></a><a name="bkmk_SeedProcess"></a><span data-ttu-id="c6d68-398">초기값을 지정 하 고 모델을 처리 하려면</span><span class="sxs-lookup"><span data-stu-id="c6d68-398">To specify the seed and process the models</span></span>  
  
1.  <span data-ttu-id="c6d68-399">**마이닝 모델** 탭에서 Call CENTER-LR 이라는 모델의 열을 마우스 오른쪽 단추로 클릭 하 고 **알고리즘 매개 변수 설정**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6d68-399">In the **Mining Model** tab, right-click the column for the model named Call Center - LR, and select **Set Algorithm Parameters**.</span></span>  
  
2.  <span data-ttu-id="c6d68-400">HOLDOUT_SEED 매개 변수에 대 한 행에서 **값**아래에 있는 빈 셀을 클릭 하 고을 입력 `1` 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6d68-400">In the row for the HOLDOUT_SEED parameter, click the empty cell under **Value**, and type `1`.</span></span> <span data-ttu-id="c6d68-401">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c6d68-401">Click **OK**.</span></span> <span data-ttu-id="c6d68-402">구조와 연관된 각 모델에 대해 이 단계를 반복합니다.</span><span class="sxs-lookup"><span data-stu-id="c6d68-402">Repeat this step for each model associated with the structure.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="c6d68-403">모든 관련 모델에 대해 동일한 초기값을 사용하는 경우에는 초기값으로 선택한 값이 중요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c6d68-403">The value that you choose as the seed does not matter, as long as you use the same seed for all related models.</span></span>  
  
3.  <span data-ttu-id="c6d68-404">**마이닝 모델** 메뉴에서 **마이닝 구조 및 모든 모델 처리**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6d68-404">In the **Mining Models** menu, select **Process Mining Structure and All Models**.</span></span> <span data-ttu-id="c6d68-405">업데이트 된 데이터 마이닝 프로젝트를 서버에 배포 하려면 **예** 를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6d68-405">Click **Yes** to deploy the updated data mining project to the server.</span></span>  
  
4.  <span data-ttu-id="c6d68-406">**마이닝 모델 처리** 대화 상자에서 **실행**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6d68-406">In the **Process Mining Model** dialog box, click **Run**.</span></span>  
  
5.  <span data-ttu-id="c6d68-407">**닫기** 를 클릭 하 여 **처리 진행률** 대화 상자를 닫은 다음 **마이닝 모델 처리** 대화 상자에서 **닫기** 를 다시 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6d68-407">Click **Close** to close the **Process Progress** dialog box, and then click **Close** again in the **Process Mining Model** dialog box.</span></span>  
  
 <span data-ttu-id="c6d68-408">관련된 두 가지 마이닝 모델을 만들었으므로 데이터를 탐색하여 데이터에서 관계를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="c6d68-408">Now that you have created the two related mining models, you will explore the data to discover relationships in the data.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="c6d68-409">단원의 다음 태스크</span><span class="sxs-lookup"><span data-stu-id="c6d68-409">Next Task in Lesson</span></span>  
 [<span data-ttu-id="c6d68-410">중급 데이터 마이닝 자습서 &#40;콜 센터 모델 탐색&#41;</span><span class="sxs-lookup"><span data-stu-id="c6d68-410">Exploring the Call Center Model &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/exploring-the-call-center-model-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a><span data-ttu-id="c6d68-411">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c6d68-411">See Also</span></span>  
 [<span data-ttu-id="c6d68-412">마이닝 구조&#40;Analysis Services - 데이터 마이닝&#41;</span><span class="sxs-lookup"><span data-stu-id="c6d68-412">Mining Structures &#40;Analysis Services - Data Mining&#41;</span></span>](../../2014/analysis-services/data-mining/mining-structures-analysis-services-data-mining.md)  
  
  
