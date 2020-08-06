---
title: 시계열 예측 DMX 자습서 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 38ea7c03-4754-4e71-896a-f68cc2c98ce2
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: fbc9a0640767b3fbae04cebb9a047c2ec2b669b6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647367"
---
# <a name="time-series-prediction-dmx-tutorial"></a><span data-ttu-id="42dfb-102">시계열 예측 DMX 자습서</span><span class="sxs-lookup"><span data-stu-id="42dfb-102">Time Series Prediction DMX Tutorial</span></span>
  <span data-ttu-id="42dfb-103">이 자습서에서는 시계열 마이닝 구조 및 3개의 사용자 지정 시계열 마이닝 모델을 만든 다음 이러한 모델을 사용하여 예측을 수행하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="42dfb-103">In this tutorial, you will learn how to create a time series mining structure, create three custom time series mining models, and then make predictions by using those models.</span></span>  
  
 <span data-ttu-id="42dfb-104">마이닝 모델은 가상 회사인  [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] 에 대한 데이터를 저장하는 [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)]예제 데이터베이스에 포함된 데이터를 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="42dfb-104">The mining models are based on the data contained in the  [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] sample database, which stores data for the fictitious company [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)].</span></span> [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)]<span data-ttu-id="42dfb-105">는 규모가 큰 다국적 제조 회사입니다.</span><span class="sxs-lookup"><span data-stu-id="42dfb-105">is a large, multinational manufacturing company.</span></span>  
  
## <a name="tutorial-scenario"></a><span data-ttu-id="42dfb-106">자습서 시나리오</span><span class="sxs-lookup"><span data-stu-id="42dfb-106">Tutorial Scenario</span></span>  
 [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)]<span data-ttu-id="42dfb-107">는 예상 매출을 생성하는 데이터 마이닝을 사용하기로 결정했습니다.</span><span class="sxs-lookup"><span data-stu-id="42dfb-107">has decided to use data mining to generate sales projections.</span></span> <span data-ttu-id="42dfb-108">일부 지역 예측 모델을 이미 빌드 했습니다. 자세한 내용은 [2 단원: &#40;중급 데이터 마이닝 자습서&#41;예측 시나리오 구축 ](../../2014/tutorials/lesson-2-building-a-forecasting-scenario-intermediate-data-mining-tutorial.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="42dfb-108">They have already built some regional forecasting models; for more information, see [Lesson 2: Building a Forecasting Scenario &#40;Intermediate Data Mining Tutorial&#41;](../../2014/tutorials/lesson-2-building-a-forecasting-scenario-intermediate-data-mining-tutorial.md).</span></span> <span data-ttu-id="42dfb-109">그러나 영업부는 정기적으로 데이터 마이닝 모델을 새 매출 데이터로 업데이트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="42dfb-109">However, the Sales Department needs to be able to periodically update the data mining model with new sales data.</span></span> <span data-ttu-id="42dfb-110">또한 다른 예상을 제공할 모델을 사용자 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="42dfb-110">They also want to customize the models to provide different projections.</span></span>  
  
 [!INCLUDE[msCoName](../includes/msconame-md.md)]<span data-ttu-id="42dfb-111">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 에서는이 작업을 수행 하는 데 사용할 수 있는 여러 가지 도구를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="42dfb-111">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] provides several tools that can be used to accomplish this task:</span></span>  
  
-   <span data-ttu-id="42dfb-112">DMX(Data Mining Extensions) 쿼리 언어</span><span class="sxs-lookup"><span data-stu-id="42dfb-112">The Data Mining Extensions (DMX) query language</span></span>  
  
-   <span data-ttu-id="42dfb-113">Microsoft Time Series 알고리즘</span><span class="sxs-lookup"><span data-stu-id="42dfb-113">The Microsoft Time Series Algorithm</span></span>  
  
-   <span data-ttu-id="42dfb-114">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]의 쿼리 편집기</span><span class="sxs-lookup"><span data-stu-id="42dfb-114">Query Editor in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]</span></span>  
  
 <span data-ttu-id="42dfb-115">[!INCLUDE[msCoName](../includes/msconame-md.md)] 시계열 알고리즘은 시간 관련 데이터 예측에 사용할 수 있는 모델을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="42dfb-115">The [!INCLUDE[msCoName](../includes/msconame-md.md)] Time Series algorithm creates models that can be used for prediction of time-related data.</span></span> <span data-ttu-id="42dfb-116">DMX(Data Mining Extensions)는 마이닝 모델 및 예측 쿼리를 만들 때 사용할 수 있는 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 에서 제공하는 쿼리 언어입니다.</span><span class="sxs-lookup"><span data-stu-id="42dfb-116">Data Mining Extensions (DMX) is a query language provided by [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] that you can use to create mining models and prediction queries.</span></span>  
  
## <a name="what-you-will-learn"></a><span data-ttu-id="42dfb-117">학습 내용</span><span class="sxs-lookup"><span data-stu-id="42dfb-117">What You Will Learn</span></span>  
 <span data-ttu-id="42dfb-118">이 자습서에서는 사용자가 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 에서 마이닝 모델을 만드는 데 사용하는 개체를 잘 알고 있다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="42dfb-118">This tutorial assumes that you are already familiar with the objects that [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] uses to create mining models.</span></span> <span data-ttu-id="42dfb-119">이전에 DMX를 사용하여 마이닝 구조 또는 마이닝 모델을 만든 적이 없는 경우에는 [Bike Buyer DMX Tutorial](../../2014/tutorials/bike-buyer-dmx-tutorial.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="42dfb-119">If you have not previously created a mining structure or mining model by using DMX, see [Bike Buyer DMX Tutorial](../../2014/tutorials/bike-buyer-dmx-tutorial.md).</span></span>  
  
 <span data-ttu-id="42dfb-120">이 자습서는 다음 단원으로 이루어져 있습니다.</span><span class="sxs-lookup"><span data-stu-id="42dfb-120">This tutorial is divided into the following lessons:</span></span>  
  
 [<span data-ttu-id="42dfb-121">1단원: 시계열 마이닝 모델 및 마이닝 구조 만들기</span><span class="sxs-lookup"><span data-stu-id="42dfb-121">Lesson 1: Creating a Time Series Mining Model and Mining Structure</span></span>](../../2014/tutorials/lesson-1-creating-a-time-series-mining-model-and-mining-structure.md)  
 <span data-ttu-id="42dfb-122">이 단원에서는 `CREATE MINING MODEL` 문을 사용하여 새 예측 모델 및 이와 관련된 마이닝 모델을 추가하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="42dfb-122">In this lesson, you will learn how to use the `CREATE MINING MODEL` statement to add a new forecasting model and a related mining model.</span></span>  
  
 [<span data-ttu-id="42dfb-123">2단원: 시계열 마이닝 구조에 마이닝 모델 추가</span><span class="sxs-lookup"><span data-stu-id="42dfb-123">Lesson 2: Adding Mining Models to the Time Series Mining Structure</span></span>](../../2014/tutorials/lesson-2-adding-mining-models-to-the-time-series-mining-structure.md)  
 <span data-ttu-id="42dfb-124">이 단원에서는 ALTER MINING STRUCTURE 문을 사용하여 시계열 구조에 새 마이닝 모델을 추가하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="42dfb-124">In this lesson, you will learn how to use the ALTER MINING STRUCTURE statement to add new mining models to the time series structure.</span></span> <span data-ttu-id="42dfb-125">시계열 분석에 사용된 알고리즘을 사용자 지정하는 방법에 대해서도 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="42dfb-125">You will also learn how to customize the algorithm used for analyzing a time series.</span></span>  
  
 [<span data-ttu-id="42dfb-126">3단원: 시계열 구조 및 모델 처리</span><span class="sxs-lookup"><span data-stu-id="42dfb-126">Lesson 3: Processing the Time Series Structure and Models</span></span>](../../2014/tutorials/lesson-3-processing-the-time-series-structure-and-models.md)  
 <span data-ttu-id="42dfb-127">이 단원에서는 `INSERT INTO` 문을 사용하고 [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] 데이터베이스의 데이터로 구조를 채워서 모델을 학습하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="42dfb-127">In this lesson, you will learn how to train the models by using the `INSERT INTO` statement and populating the structure with data from the [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] database.</span></span>  
  
 [<span data-ttu-id="42dfb-128">4단원: DMX를 사용하여 시계열 예측 만들기</span><span class="sxs-lookup"><span data-stu-id="42dfb-128">Lesson 4: Creating Time Series Predictions Using DMX</span></span>](../../2014/tutorials/lesson-4-creating-time-series-predictions-using-dmx.md)  
 <span data-ttu-id="42dfb-129">이 단원에서는 시계열 예측을 만드는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="42dfb-129">In this lesson, you will learn how to create time series predictions.</span></span>  
  
 [<span data-ttu-id="42dfb-130">5단원: 시계열 모델 확장</span><span class="sxs-lookup"><span data-stu-id="42dfb-130">Lesson 5: Extending the Time Series Model</span></span>](../../2014/tutorials/lesson-5-extending-the-time-series-model.md)  
 <span data-ttu-id="42dfb-131">이 단원에서는 `EXTEND_MODEL_CASES` 매개 변수를 사용하여 예측할 때 새 데이터로 모델을 업데이트하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="42dfb-131">In this lesson, you will learn how to use the `EXTEND_MODEL_CASES` parameter to update the model with new data when you make predictions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="42dfb-132">요구 사항</span><span class="sxs-lookup"><span data-stu-id="42dfb-132">Requirements</span></span>  
 <span data-ttu-id="42dfb-133">이 자습서를 사용하려면 먼저 다음을 설치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="42dfb-133">Before doing this tutorial, make sure that the following are installed:</span></span>  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)] <span data-ttu-id="42dfb-134">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="42dfb-134">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]</span></span>  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)] <span data-ttu-id="42dfb-135">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="42dfb-135">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]</span></span>  
  
-   <span data-ttu-id="42dfb-136">[!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] 데이터베이스</span><span class="sxs-lookup"><span data-stu-id="42dfb-136">The [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] database</span></span>  
  
 <span data-ttu-id="42dfb-137">보안을 위해 예제 데이터베이스는 기본적으로 설치되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="42dfb-137">By default, the sample databases are not installed, to enhance security.</span></span> <span data-ttu-id="42dfb-138">의 공식 예제 데이터베이스를 설치 하려면 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [http://www.CodePlex.com/MSFTDBProdSamples](https://go.microsoft.com/fwlink/?LinkId=88417) Microsoft SQL Server 제품 샘플 섹션의 Microsoft SQL Server 샘플 및 커뮤니티 프로젝트 홈 페이지에서 또는으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="42dfb-138">To install the official sample databases for [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], go to [http://www.CodePlex.com/MSFTDBProdSamples](https://go.microsoft.com/fwlink/?LinkId=88417) or on the Microsoft SQL Server Samples and Community Projects home page in the section Microsoft SQL Server Product Samples.</span></span> <span data-ttu-id="42dfb-139">**Databases**, **Releases** 탭을 차례로 클릭한 다음 원하는 데이터베이스를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="42dfb-139">Click **Databases**, then click the **Releases** tab and select the databases that you want.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="42dfb-140">자습서를 검토할 때는 문서 뷰어 도구 모음에 **다음 항목** 단추 및 **이전 항목** 단추를 추가하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="42dfb-140">When you review tutorials, we recommend that you add **Next topic** and **Previous topic** buttons to the document viewer toolbar.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42dfb-141">참고 항목</span><span class="sxs-lookup"><span data-stu-id="42dfb-141">See Also</span></span>  
 <span data-ttu-id="42dfb-142">[기본 데이터 마이닝 자습서](../../2014/tutorials/basic-data-mining-tutorial.md) </span><span class="sxs-lookup"><span data-stu-id="42dfb-142">[Basic Data Mining Tutorial](../../2014/tutorials/basic-data-mining-tutorial.md) </span></span>  
 [<span data-ttu-id="42dfb-143">Analysis Services 데이터 마이닝&#41;&#40;중급 데이터 마이닝 자습서</span><span class="sxs-lookup"><span data-stu-id="42dfb-143">Intermediate Data Mining Tutorial &#40;Analysis Services - Data Mining&#41;</span></span>](../../2014/tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md)  
  
  
