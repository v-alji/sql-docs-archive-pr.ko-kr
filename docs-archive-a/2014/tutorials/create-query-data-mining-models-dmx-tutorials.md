---
title: 'DMX를 사용 하 여 데이터 마이닝 모델 만들기 및 쿼리: 자습서 (Analysis Services-데이터 마이닝) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- content queries [DMX]
ms.assetid: 145b81a7-c0c3-4ca3-bb32-0b482423b9a0
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 22ed01105a32f460bcbeb2c067299fdf62af2eed
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87638471"
---
# <a name="creating-and-querying-data-mining-models-with-dmx-tutorials-analysis-services---data-mining"></a><span data-ttu-id="15972-102">DMX를 사용하여 데이터 마이닝 모델 만들기 및 쿼리: 자습서(Analysis Services - 데이터 마이닝)</span><span class="sxs-lookup"><span data-stu-id="15972-102">Creating and Querying Data Mining Models with DMX: Tutorials (Analysis Services - Data Mining)</span></span>
  <span data-ttu-id="15972-103">를 사용 하 여 데이터 마이닝 솔루션을 만든 후에 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 는 데이터 마이닝 모델에 대 한 쿼리를 만들어 추세를 예측 하 고, 데이터 패턴을 검색 하 고, 마이닝 모델의 정확도를 측정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15972-103">After you have created a data mining solution by using [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], you can create queries against the data mining models to predict trends, retrieve patterns in the data, and measure the accuracy of the mining models.</span></span>  
  
 <span data-ttu-id="15972-104">다음 목록의 단계별 자습서에서는 데이터를 최대한으로 활용할 수 있도록 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 를 사용하여 데이터 마이닝 쿼리를 작성하고 실행하는 방법을 배울 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15972-104">The step-by-step tutorials in the following list will help you learn how to build and run data mining queries by using [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] so that you can get the most from your data.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="15972-105">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="15972-105">In This Section</span></span>  
  
-   [<span data-ttu-id="15972-106">Bike Buyer DMX 자습서</span><span class="sxs-lookup"><span data-stu-id="15972-106">Bike Buyer DMX Tutorial</span></span>](../../2014/tutorials/bike-buyer-dmx-tutorial.md)  
  
     <span data-ttu-id="15972-107">이 자습서에서는 DMX(Data Mining Extensions) 언어를 사용하여 새 마이닝 구조 및 마이닝 모델을 만드는 과정을 안내하고 DMX 예측 쿼리를 만드는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="15972-107">This tutorial walks you through the creation of a new mining structure and mining models by using the Data Mining Extensions (DMX) language, and explains how to create DMX prediction queries.</span></span>  
  
-   [<span data-ttu-id="15972-108">Market Basket DMX 자습서</span><span class="sxs-lookup"><span data-stu-id="15972-108">Market Basket DMX Tutorial</span></span>](../../2014/tutorials/market-basket-dmx-tutorial.md)  
  
     <span data-ttu-id="15972-109">이 자습서에서는 고객이 함께 구매한 제품 간의 연관 관계를 찾는 일반적인 시장 바구니 시나리오를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="15972-109">This tutorial uses a typical market basket scenario, where you find associations between the products that customers purchase together.</span></span> <span data-ttu-id="15972-110">또한 이 자습서에서는 마이닝 구조를 만들 때 중첩 테이블을 사용하는 방법도 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="15972-110">This tutorial also demonstrates how to use nested tables when you create a mining structure.</span></span> <span data-ttu-id="15972-111">이 구조를 기반으로 모델을 작성하고 학습한 다음 DMX를 사용하여 예측을 만들어 봅니다.</span><span class="sxs-lookup"><span data-stu-id="15972-111">You build and train a model based on this structure, and then create predictions using DMX.</span></span>  
  
-   [<span data-ttu-id="15972-112">시계열 예측 DMX 자습서</span><span class="sxs-lookup"><span data-stu-id="15972-112">Time Series Prediction DMX Tutorial</span></span>](../../2014/tutorials/time-series-prediction-dmx-tutorial.md)  
  
     <span data-ttu-id="15972-113">이 자습서에서는 예측 모델을 만들어 CREATE MODEL (DMX) 문 사용을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="15972-113">This tutorial creates a forecasting model to illustrate the use of the CREATE MODEL (DMX) statement.</span></span> <span data-ttu-id="15972-114">그런 다음 관련 모델을 추가하고 Microsoft Time Series 알고리즘의 매개 변수를 변경하여 각 모델의 동작을 사용자 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="15972-114">You then add related models and customize the behavior of each by changing the parameters of the Microsoft Time Series algorithm.</span></span> <span data-ttu-id="15972-115">마지막으로 예측을 만들고 새 데이터를 사용하여 해당 예측을 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="15972-115">Finally you create predictions and update the predictions with new data.</span></span> <span data-ttu-id="15972-116">예측을 만들면서 시계열을 업데이트하는 기능은 [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)]부터 추가되었습니다.</span><span class="sxs-lookup"><span data-stu-id="15972-116">The ability to update a time series while making predictions was added in [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)].</span></span>  
  
## <a name="reference"></a><span data-ttu-id="15972-117">참조</span><span class="sxs-lookup"><span data-stu-id="15972-117">Reference</span></span>  
 [<span data-ttu-id="15972-118">데이터 마이닝 알고리즘&#40;Analysis Services - 데이터 마이닝&#41;</span><span class="sxs-lookup"><span data-stu-id="15972-118">Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;</span></span>](../../2014/analysis-services/data-mining/data-mining-algorithms-analysis-services-data-mining.md)  
  
 [<span data-ttu-id="15972-119">DMX&#40;Data Mining Extensions&#41; 참조</span><span class="sxs-lookup"><span data-stu-id="15972-119">Data Mining Extensions &#40;DMX&#41; Reference</span></span>](/sql/dmx/data-mining-extensions-dmx-reference)  
  
## <a name="related-sections"></a><span data-ttu-id="15972-120">관련 단원</span><span class="sxs-lookup"><span data-stu-id="15972-120">Related Sections</span></span>  
  
-   [<span data-ttu-id="15972-121">기본 데이터 마이닝 자습서</span><span class="sxs-lookup"><span data-stu-id="15972-121">Basic Data Mining Tutorial</span></span>](../../2014/tutorials/basic-data-mining-tutorial.md)  
  
     <span data-ttu-id="15972-122">이 자습서에서는 프로젝트를 만드는 방법, 마이닝 구조 및 마이닝 모델을 작성하는 방법 등의 기본 개념을 소개합니다.</span><span class="sxs-lookup"><span data-stu-id="15972-122">This tutorial introduces basic concepts, such as how to create a project and how to build mining structures and mining models.</span></span>  
  
-   [<span data-ttu-id="15972-123">Analysis Services 데이터 마이닝&#41;&#40;중급 데이터 마이닝 자습서</span><span class="sxs-lookup"><span data-stu-id="15972-123">Intermediate Data Mining Tutorial &#40;Analysis Services - Data Mining&#41;</span></span>](../../2014/tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md)  
  
     <span data-ttu-id="15972-124">이 자습서에는 각각 서로 다른 모델 유형을 소개하는 여러 독립적인 단원이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15972-124">This tutorial contains a number of independent lessons, each introducing you to a different model type.</span></span> <span data-ttu-id="15972-125">각 단원에서는 모델을 만들고 탐색하며 사용자 지정하고 예측 쿼리를 만드는 과정을 단계별로 안내합니다.</span><span class="sxs-lookup"><span data-stu-id="15972-125">Each lesson walks you through the process of creating a model, exploring the model, and then customizing the model and creating prediction queries.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15972-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="15972-126">See Also</span></span>  
 <span data-ttu-id="15972-127">[데이터 마이닝 솔루션](../../2014/analysis-services/data-mining/data-mining-solutions.md) </span><span class="sxs-lookup"><span data-stu-id="15972-127">[Data Mining Solutions](../../2014/analysis-services/data-mining/data-mining-solutions.md) </span></span>  
 <span data-ttu-id="15972-128">[데이터 마이닝 도구](../../2014/analysis-services/data-mining/data-mining-tools.md) </span><span class="sxs-lookup"><span data-stu-id="15972-128">[Data Mining Tools](../../2014/analysis-services/data-mining/data-mining-tools.md) </span></span>  
 [<span data-ttu-id="15972-129">데이터 마이닝 프로젝트</span><span class="sxs-lookup"><span data-stu-id="15972-129">Data Mining Projects</span></span>](../../2014/analysis-services/data-mining/data-mining-projects.md)  
  
  
