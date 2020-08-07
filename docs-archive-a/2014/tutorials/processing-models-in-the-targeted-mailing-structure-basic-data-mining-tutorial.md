---
title: 대상 메일 구조에서 모델 처리 (기본 데이터 마이닝 자습서) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 9d8233bb-117e-4563-9302-8a5a8ad1fae2
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: b8fb7b9f601f351520c3f611cc3c520614ed8ccc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731244"
---
# <a name="processing-models-in-the-targeted-mailing-structure-basic-data-mining-tutorial"></a><span data-ttu-id="888f3-102">대상 메일 구조에서 모델 처리(기본 데이터 마이닝 자습서)</span><span class="sxs-lookup"><span data-stu-id="888f3-102">Processing Models in the Targeted Mailing Structure (Basic Data Mining Tutorial)</span></span>
  <span data-ttu-id="888f3-103">만든 마이닝 모델을 찾아보거나 사용하기 전에 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 프로젝트를 배포하고 마이닝 구조 및 마이닝 모델을 처리해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="888f3-103">Before you can browse or work with the mining models that you have created, you must deploy the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] project and process the mining structure and mining models.</span></span>  
  
-   <span data-ttu-id="888f3-104">*배포* 하는 경우 프로젝트를 서버에 보내고 서버에 있는 해당 프로젝트에 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="888f3-104">*Deploying* sends the project to a server and creates any objects in that project on the server.</span></span>  
  
-   <span data-ttu-id="888f3-105">*처리* [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 는 관계형 데이터 원본의 데이터로 개체를 채웁니다.</span><span class="sxs-lookup"><span data-stu-id="888f3-105">*Processing* populates [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] objects with data from relational data sources.</span></span>  
  
 <span data-ttu-id="888f3-106">모델은 배포 및 처리될 때까지 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="888f3-106">Models cannot be used until they have been deployed and processed.</span></span> <span data-ttu-id="888f3-107">또한 새 데이터를 추가 하는 등 모델을 변경 하는 경우에는 모델을 다시 배포 하 고 다시 처리 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="888f3-107">Also, when you make any changes to the model, such as adding new data, you must redeploy and reprocess the models.</span></span>  
  
## <a name="ensuring-consistency-with-holdoutseed"></a><span data-ttu-id="888f3-108">HoldoutSeed와의 일관성 확인</span><span class="sxs-lookup"><span data-stu-id="888f3-108">Ensuring Consistency with HoldoutSeed</span></span>  
 <span data-ttu-id="888f3-109">프로젝트를 배포 하 고 구조 및 모델을 처리 하는 경우 데이터 구조의 개별 행은 숫자 시드 값을 기반으로 학습 집합 또는 테스트 집합에 할당 됩니다.</span><span class="sxs-lookup"><span data-stu-id="888f3-109">When you deploy a project and process the structure and models, individual rows in your data structure are assigned to either the training set or testing set based on a numerical seed value.</span></span> <span data-ttu-id="888f3-110">기본적으로 숫자 초기값은 데이터 구조의 특성을 기반으로 계산 됩니다.</span><span class="sxs-lookup"><span data-stu-id="888f3-110">By default, the numerical seed value is computed based on attributes of the data structure.</span></span> <span data-ttu-id="888f3-111">그러나 모델의 일부 측면을 변경 하는 경우 초기값이 변경 되어 약간 다른 결과를 초래 합니다.</span><span class="sxs-lookup"><span data-stu-id="888f3-111">However, if you ever change some aspects of your model, the seed value would change, leading to subtly different results.</span></span> <span data-ttu-id="888f3-112">따라서 결과가 여기에 설명 된 것과 동일 하도록 하기 위해의 고정 *홀드 아웃 초기값* 을 임의로 할당 `12` 합니다.</span><span class="sxs-lookup"><span data-stu-id="888f3-112">Therefore, in order to ensure that your results are the same as described here, we will arbitrarily assign a fixed *holdout seed* of `12`.</span></span> <span data-ttu-id="888f3-113">홀드 아웃 초기값은 샘플링 알고리즘을 초기화 하는 데 사용 되 고 데이터는 모든 마이닝 구조 및 해당 모델에 대해 거의 동일한 방식으로 분할 됩니다.</span><span class="sxs-lookup"><span data-stu-id="888f3-113">The holdout seed is used to initialize the sampling algorithm, and ensures that the data is partitioned in roughly the same way for all mining structures and their models.</span></span>  
  
 <span data-ttu-id="888f3-114">이 값은 학습 집합의 사례 수에 영향을 주지 않습니다. 모델을 빌드할 때마다 동일한 분할 방법이 사용 되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="888f3-114">This value does not affect the number of cases in the training set; it simply ensures that the same partitioning method will be used each time you build the model.</span></span>  
  
 <span data-ttu-id="888f3-115">홀드 아웃 초기값에 대 한 자세한 내용은 [데이터 집합 학습 및 테스트](../../2014/analysis-services/data-mining/training-and-testing-data-sets.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="888f3-115">For more information on holdout seed, see [Training and Testing Data Sets](../../2014/analysis-services/data-mining/training-and-testing-data-sets.md).</span></span>  
  
#### <a name="to-set-the-holdout-seed"></a><span data-ttu-id="888f3-116">홀드아웃 초기값을 설정하려면</span><span class="sxs-lookup"><span data-stu-id="888f3-116">To set the Holdout Seed</span></span>  
  
1.  <span data-ttu-id="888f3-117">의 데이터 마이닝 디자이너에서 마이닝 **구조** 탭 이나 **마이닝 모델** 탭을 클릭 합니다 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="888f3-117">Click on the **Mining Structure** tab or the **Mining Models** tab in Data Mining Designer in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span>  
  
     <span data-ttu-id="888f3-118">**타겟 메일링 MiningStructure** 는 **속성** 창에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="888f3-118">**Targeted Mailing MiningStructure** displays in the **Properties** pane.</span></span>  
  
2.  <span data-ttu-id="888f3-119">**F4**키를 눌러 **속성** 창이 열려 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="888f3-119">Ensure that the **Properties** pane is open by pressing **F4**.</span></span>  
  
3.  <span data-ttu-id="888f3-120">**Cachemode** 가 **KeepTrainingCases**으로 설정 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="888f3-120">Ensure that **CacheMode** is set to **KeepTrainingCases**.</span></span>  
  
4.  <span data-ttu-id="888f3-121">`12` **HoldoutSeed**에 대해을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="888f3-121">Enter `12` for **HoldoutSeed**.</span></span>  
  
## <a name="deploying-and-processing-the-models"></a><span data-ttu-id="888f3-122">모델 배포 및 처리</span><span class="sxs-lookup"><span data-stu-id="888f3-122">Deploying and Processing the Models</span></span>  
 <span data-ttu-id="888f3-123">데이터 마이닝 디자이너에서 모델에 대 한 변경 내용 또는 기본 데이터의 범위에 따라 처리할 개체를 결정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="888f3-123">In Data Mining Designer, you can decide which objects to process, depending on the scope of changes you've made to your model or the underlying data:</span></span>  
  
 <span data-ttu-id="888f3-124">이 태스크의 경우 데이터 및 모델이 새로운 것 이므로 구조와 모든 모델을 동시에 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="888f3-124">For this task, because the data and the models are new, you will process the structure and all the models at the same time.</span></span>  
  
#### <a name="to-deploy-the-project-and-process-all-the-mining-models"></a><span data-ttu-id="888f3-125">프로젝트를 배포하고 모든 마이닝 모델을 처리하려면</span><span class="sxs-lookup"><span data-stu-id="888f3-125">To deploy the project and process all the mining models</span></span>  
  
1.  <span data-ttu-id="888f3-126">**마이닝 모델** 메뉴에서 **마이닝 구조 및 모든 모델 처리**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="888f3-126">In the **Mining Model** menu, select **Process Mining Structure and All Models**.</span></span>  
  
     <span data-ttu-id="888f3-127">마이닝 구조를 변경한 경우 모델을 처리하기 전에 프로젝트를 빌드하고 배포할지 묻는 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="888f3-127">If you made changes to the structure, you will be prompted to build and deploy the project before processing the models.</span></span> <span data-ttu-id="888f3-128">**예**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="888f3-128">Click **Yes**.</span></span>  
  
2.  <span data-ttu-id="888f3-129">**마이닝 구조 처리-대상 메일링** 대화 상자에서 **실행** 을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="888f3-129">Click **Run** in the **Processing Mining Structure - Targeted Mailing** dialog box.</span></span>  
  
     <span data-ttu-id="888f3-130">**처리 진행률** 대화 상자가 열리고 모델 처리 세부 정보를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="888f3-130">The **Process Progress** dialog box opens to display the details of model processing.</span></span> <span data-ttu-id="888f3-131">컴퓨터에 따라 모델 처리에 시간이 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="888f3-131">Model processing might take some time, depending on your computer.</span></span>  
  
3.  <span data-ttu-id="888f3-132">모델 처리가 완료되면 **처리 진행률** 대화 상자에서 **닫기** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="888f3-132">Click **Close** in the **Process Progress** dialog box after the models have completed processing.</span></span>  
  
4.  <span data-ttu-id="888f3-133">**마이닝 구조 처리 \<structure> -** 대화 상자에서 **닫기** 를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="888f3-133">Click **Close** in the **Processing Mining Structure - \<structure>** dialog box.</span></span>  
  
## <a name="previous-task-in-lesson"></a><span data-ttu-id="888f3-134">단원의 이전 태스크</span><span class="sxs-lookup"><span data-stu-id="888f3-134">Previous Task in Lesson</span></span>  
 [<span data-ttu-id="888f3-135">&#40;기본 데이터 마이닝 자습서를 대상으로 지정 된 메일링 구조에 새 모델 추가&#41;</span><span class="sxs-lookup"><span data-stu-id="888f3-135">Adding New Models to the Targeted Mailing Structure &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/adding-new-models-to-the-targeted-mailing-structure-basic-data-mining-tutorial.md)  
  
## <a name="next-lesson"></a><span data-ttu-id="888f3-136">다음 단원</span><span class="sxs-lookup"><span data-stu-id="888f3-136">Next Lesson</span></span>  
 [<span data-ttu-id="888f3-137">4 단원: 기본 데이터 마이닝 자습서 &#40;대상 메일링 모델 탐색&#41;</span><span class="sxs-lookup"><span data-stu-id="888f3-137">Lesson 4: Exploring the Targeted Mailing Models &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-4-exploring-the-targeted-mailing-models-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a><span data-ttu-id="888f3-138">참고 항목</span><span class="sxs-lookup"><span data-stu-id="888f3-138">See Also</span></span>  
 [<span data-ttu-id="888f3-139">처리 요구 사항 및 고려 사항&#40;데이터 마이닝&#41;</span><span class="sxs-lookup"><span data-stu-id="888f3-139">Processing Requirements and Considerations &#40;Data Mining&#41;</span></span>](../../2014/analysis-services/data-mining/processing-requirements-and-considerations-data-mining.md)  
  
  
