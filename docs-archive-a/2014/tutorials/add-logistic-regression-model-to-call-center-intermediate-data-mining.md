---
title: 콜 센터 구조에 로지스틱 회귀 모델 추가 (중급 데이터 마이닝 자습서) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 97abb77a-346c-44fa-8959-688dee1af6a8
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 7d0100313d1ea5a1af5f729249bc2d743a730222
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87735683"
---
# <a name="adding-a-logistic-regression-model-to-the-call-center-structure-intermediate-data-mining-tutorial"></a><span data-ttu-id="fe338-102">콜 센터 구조에 로지스틱 회귀 모델 추가(중급 데이터 마이닝 자습서)</span><span class="sxs-lookup"><span data-stu-id="fe338-102">Adding a Logistic Regression Model to the Call Center Structure (Intermediate Data Mining Tutorial)</span></span>
  <span data-ttu-id="fe338-103">콜 센터 운영에 영향을 줄 수 있는 요인을 분석하는 것 외에 직원이 서비스 품질을 향상시킬 수 있는 방법에 대한 일부 특정 권장 사항을 제공할 것도 요청받았습니다.</span><span class="sxs-lookup"><span data-stu-id="fe338-103">In addition to analyzing the factors that might affect call center operations, you were also asked to provide some specific recommendations on how the staff can improve service quality.</span></span> <span data-ttu-id="fe338-104">이 작업에서는 탐색 모델을 작성하는 데 사용한 마이닝 구조를 그대로 사용하고 예측을 만드는 데 사용될 마이닝 모델을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="fe338-104">In this task, you will use the same mining structure that you used to build the exploratory model and add a mining model that will be used for creating predictions.</span></span>  
  
 <span data-ttu-id="fe338-105">[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]에서 로지스틱 회귀 모델은 신경망 알고리즘을 기반으로 하므로 신경망 모델과 동일한 유연성과 강력한 기능을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="fe338-105">In [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], a logistic regression model is based on the neural networks algorithm, and therefore provides the same flexibility and power as a neural network model.</span></span> <span data-ttu-id="fe338-106">그러나 로지스틱 회귀는 이진 결과 예측에 특히 적합합니다.</span><span class="sxs-lookup"><span data-stu-id="fe338-106">However, logistic regression is particularly well-suited for predicting binary outcomes.</span></span>  
  
 <span data-ttu-id="fe338-107">이 시나리오에서는 신경망 모델에 사용한 것과 같은 마이닝 구조를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="fe338-107">For this scenario, you will use the same mining structure that you used for the neural network model.</span></span> <span data-ttu-id="fe338-108">다만 해당 비즈니스 질문에 맞게 새 모델을 사용자 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="fe338-108">However, you will customize the new model to target your business questions.</span></span> <span data-ttu-id="fe338-109">서비스 품질을 향상시키고 필요한 경력 전화 상담원 수를 결정하는 데 관심이 있으므로 그러한 값을 예측하도록 모델을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="fe338-109">You are interested in improving service quality and determining how many experienced operators you need, so you will set up your model to predict those values.</span></span>  
  
 <span data-ttu-id="fe338-110">콜 센터 데이터를 기반으로 한 전체 모델이 가능한 한 유사하도록 하려면 이전과 동일한 초기값을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="fe338-110">To ensure that all the models based on the call center data are as similar as possible, you will use the same seed value as before.</span></span> <span data-ttu-id="fe338-111">초기값 매개 변수를 설정하면 모델이 동일한 시작점에서 데이터를 처리하고 데이터의 아티팩트로 인해 발생한 변형을 최소화합니다.</span><span class="sxs-lookup"><span data-stu-id="fe338-111">Setting the seed parameter ensures that the model processes the data from the same starting point, and minimizes variations caused by artifacts in the data.</span></span>  
  
### <a name="to-add-a-new-mining-model-to-the-call-center-mining-structure"></a><span data-ttu-id="fe338-112">콜 센터 마이닝 구조에 새 마이닝 모델을 추가하려면</span><span class="sxs-lookup"><span data-stu-id="fe338-112">To add a new mining model to the call center mining structure</span></span>  
  
1.  <span data-ttu-id="fe338-113">의 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 솔루션 탐색기에서 마이닝 구조를 마우스 오른쪽 단추로 클릭 하 고 **호출 센터**를 클릭 한 다음 **디자이너 열기**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe338-113">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], in Solution Explorer, right-click the mining structure, **Call Center Binned**, and select **Open Designer**.</span></span>  
  
2.  <span data-ttu-id="fe338-114">데이터 마이닝 디자이너에서 **마이닝 모델** 탭을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe338-114">In Data Mining Designer, click the **Mining Models** tab.</span></span>  
  
3.  <span data-ttu-id="fe338-115">**관련 마이닝 모델 만들기를**클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe338-115">Click **Create a related mining model**.</span></span>  
  
4.  <span data-ttu-id="fe338-116">**새 마이닝 모델** 대화 상자의 **모델 이름**에을 입력 `Call Center - LR` 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe338-116">In the **New Mining Model** dialog box, for **Model name**, type `Call Center - LR`.</span></span>  <span data-ttu-id="fe338-117">**알고리즘 이름**에 대해 **Microsoft 로지스틱 회귀**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe338-117">For **Algorithm name**, select **Microsoft Logistic Regression**.</span></span>  
  
5.  <span data-ttu-id="fe338-118">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="fe338-118">Click **OK**.</span></span>  
  
     <span data-ttu-id="fe338-119">**마이닝** 모델 탭에 새 마이닝 모델이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="fe338-119">The new mining model is displayed in the **Mining Models** tab.</span></span>  
  
### <a name="to-customize-the-logistic-regression-model"></a><span data-ttu-id="fe338-120">로지스틱 회귀 모델을 사용자 지정하려면</span><span class="sxs-lookup"><span data-stu-id="fe338-120">To customize the logistic regression model</span></span>  
  
1.  <span data-ttu-id="fe338-121">새 마이닝 모델의 열에서 `Call Center - LR` 팩트 CallCenter ID를 키로 유지 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe338-121">In the column for the new mining model, `Call Center - LR`, leave Fact CallCenter ID as the key.</span></span>  
  
2.  <span data-ttu-id="fe338-122">ServiceGrade 및 Level 2 연산자의 값을 **예측**으로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe338-122">Change the value of ServiceGrade and Level Two Operators to **Predict**.</span></span>  
  
     <span data-ttu-id="fe338-123">이러한 열은 입력 및 예측에 모두 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="fe338-123">These columns will be used both as input and for prediction.</span></span> <span data-ttu-id="fe338-124">기본적으로 동일한 데이터에서 두 개의 모델을 만듭니다. 하나는 연산자 수를 예측 하 고 다른 하나는 서비스 등급을 예측 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe338-124">In essence, you are creating two separate models on the same data: one that predicts the number of operators, and one that predicts the service grade.</span></span>  
  
3.  <span data-ttu-id="fe338-125">다른 모든 열을 **입력**으로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe338-125">Change all other columns to **Input**.</span></span>  
  
### <a name="to-specify-the-seed-and-process-the-models"></a><span data-ttu-id="fe338-126">초기값을 지정하고 모델을 처리하려면</span><span class="sxs-lookup"><span data-stu-id="fe338-126">To specify the seed and process the models</span></span>  
  
1.  <span data-ttu-id="fe338-127">**마이닝 모델** 탭에서 Call CENTER-LR 이라는 모델의 열을 마우스 오른쪽 단추로 클릭 하 고 **알고리즘 매개 변수 설정**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe338-127">In the **Mining Model** tab, right-click the column for the model named Call Center - LR, and select **Set Algorithm Parameters**.</span></span>  
  
2.  <span data-ttu-id="fe338-128">HOLDOUT_SEED 매개 변수에 대 한 행에서 **값**아래에 있는 빈 셀을 클릭 하 고을 입력 `1` 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe338-128">In the row for the HOLDOUT_SEED parameter, click the empty cell under **Value**, and type `1`.</span></span> <span data-ttu-id="fe338-129">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="fe338-129">Click **OK**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="fe338-130">모든 관련 모델에 대해 동일한 초기값을 사용하는 경우에는 초기값으로 선택한 값이 중요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="fe338-130">The value that you choose as the seed does not matter, as long as you use the same seed for all related models.</span></span>  
  
3.  <span data-ttu-id="fe338-131">**마이닝 모델** 메뉴에서 **마이닝 구조 및 모든 모델 처리**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe338-131">In the **Mining Models** menu, select **Process Mining Structure and All Models**.</span></span> <span data-ttu-id="fe338-132">업데이트 된 데이터 마이닝 프로젝트를 서버에 배포 하려면 **예** 를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe338-132">Click **Yes** to deploy the updated data mining project to the server.</span></span>  
  
4.  <span data-ttu-id="fe338-133">**마이닝 모델 처리** 대화 상자에서 **실행**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe338-133">In the **Process Mining Model** dialog box, click **Run**.</span></span>  
  
5.  <span data-ttu-id="fe338-134">**닫기** 를 클릭 하 여 **처리 진행률** 대화 상자를 닫은 다음 **마이닝 모델 처리** 대화 상자에서 **닫기** 를 다시 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe338-134">Click **Close** to close the **Process Progress** dialog box, and then click **Close** again in the **Process Mining Model** dialog box.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="fe338-135">단원의 다음 태스크</span><span class="sxs-lookup"><span data-stu-id="fe338-135">Next Task in Lesson</span></span>  
 [<span data-ttu-id="fe338-136">중급 데이터 마이닝 자습서 &#40;콜 센터 모델에 대 한 예측 만들기&#41;</span><span class="sxs-lookup"><span data-stu-id="fe338-136">Creating Predictions for the Call Center Models &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/create-predictions-call-center-models-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a><span data-ttu-id="fe338-137">참고 항목</span><span class="sxs-lookup"><span data-stu-id="fe338-137">See Also</span></span>  
 [<span data-ttu-id="fe338-138">처리 요구 사항 및 고려 사항&#40;데이터 마이닝&#41;</span><span class="sxs-lookup"><span data-stu-id="fe338-138">Processing Requirements and Considerations &#40;Data Mining&#41;</span></span>](../../2014/analysis-services/data-mining/processing-requirements-and-considerations-data-mining.md)  
  
  
