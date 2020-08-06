---
title: 데이터 마이닝 도구 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- tools [Analysis Services]
- mining models [Analysis Services], tools
- data mining [Analysis Services], tools
- data mining [Analysis Services], development
ms.assetid: 003ada6a-0bcd-4f16-8c34-1a9ffc75cd2c
author: minewiskan
ms.author: owend
ms.openlocfilehash: 4be2f343f0fb7969f76b63ec1eb1677c1c9e589f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661429"
---
# <a name="data-mining-tools"></a><span data-ttu-id="ab1e3-102">데이터 마이닝 도구</span><span class="sxs-lookup"><span data-stu-id="ab1e3-102">Data Mining Tools</span></span>
  [!INCLUDE[msCoName](../../includes/msconame-md.md)]<span data-ttu-id="ab1e3-103">는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 데이터 마이닝 솔루션을 만드는 데 사용할 수 있는 다음과 같은 도구를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="ab1e3-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] provides the following tools that you can use to create data mining solutions:</span></span>  
  
-   <span data-ttu-id="ab1e3-104">\*\*\*\* 의 데이터 마이닝 마법사 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 는 관계형 데이터 원본이나 큐브의 다차원 데이터를 사용하여 마이닝 구조와 마이닝 모델을 쉽게 만들 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="ab1e3-104">The **Data Mining Wizard** in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] makes it easy to create mining structures and mining models, using either relational data sources or multidimensional data in cubes.</span></span>  
  
     <span data-ttu-id="ab1e3-105">이 마법사에서 사용할 데이터를 선택한 다음 클러스터링, 신경망 또는 시계열 모델링과 같은 특정 데이터 마이닝 기술을 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ab1e3-105">In the wizard, you choose data to use, and then apply specific data mining techniques, such as clustering, neural networks, or time series modeling.</span></span>  
  
-   <span data-ttu-id="ab1e3-106">**모델 뷰어** 는 마이닝 모델이 만들어진 후 마이닝 모델을 탐색하기 위해 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 및 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]에서 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="ab1e3-106">**Model viewers** are provided in both [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] and [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], for exploring your mining models after they are created.</span></span>  <span data-ttu-id="ab1e3-107">각 알고리즘에 맞게 조정된 뷰어를 사용하여 모델을 찾아보거나 모델 콘텐츠 뷰어를 사용하여 세부적으로 분석할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ab1e3-107">You can browse models using viewers tailored to each algorithm, or go deeper into analysis by using the model content viewer.</span></span>  
  
-   <span data-ttu-id="ab1e3-108">**예측 쿼리 작성기** 는 예측 쿼리를 쉽게 만들 수 있도록 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 및 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 에서 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="ab1e3-108">The **Prediction Query Builder** is provided in both [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] and [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] to help you create prediction queries.</span></span> <span data-ttu-id="ab1e3-109">홀드아웃 데이터 집합 또는 외부 데이터에 대해 모델의 정확도를 테스트하거나 교차 유효성 검사를 사용하여 데이터 집합의 품질을 평가할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ab1e3-109">You can also test the accuracy of models against a holdout data set or external data, or use cross-validation to assess the quality of your data set.</span></span>  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] <span data-ttu-id="ab1e3-110">는 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]인스턴스에 배포된 기존 데이터 마이닝 솔루션을 관리하는 인터페이스입니다.</span><span class="sxs-lookup"><span data-stu-id="ab1e3-110">is the interface where you manage existing data mining solutions that have been deployed to an instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="ab1e3-111">구조와 모델을 다시 처리하여 구조와 모델의 데이터를 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ab1e3-111">You can reprocess structures and models to update the data in them.</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="ab1e3-112">에 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 는 데이터를 정리 하 고, 예측 생성, 모델 업데이트 등의 태스크를 자동화 하 고, 텍스트 마이닝 솔루션을 만드는 데 사용할 수 있는 도구가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ab1e3-112">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] contains tools that you can use to clean data, to automate tasks such as creating predictions and updating models, and to create text mining solutions.</span></span>  
  
 <span data-ttu-id="ab1e3-113">다음 섹션에서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 데이터 마이닝 도구에 대한 추가 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="ab1e3-113">The following sections provide more information about the data mining tools in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="data-mining-wizard"></a><span data-ttu-id="ab1e3-114">데이터 마이닝 마법사</span><span class="sxs-lookup"><span data-stu-id="ab1e3-114">Data Mining Wizard</span></span>  
 <span data-ttu-id="ab1e3-115">데이터 마이닝 마법사를 사용하여 데이터 마이닝 솔루션 생성을 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ab1e3-115">Use the Data Mining Wizard to get started creating data mining solutions.</span></span> <span data-ttu-id="ab1e3-116">이 마법사는 빠르고 쉬우며 데이터 마이닝 구조 및 초기 관련 마이닝 모델을 만드는 과정을 안내하고 알고리즘 유형 및 데이터 원본 선택 태스크와 분석에 사용되는 사례 데이터 정의 태스크를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="ab1e3-116">The wizard is quick and easy, and guides you through the process of creating a data mining structure and an initial related mining model, and includes the tasks of selecting an algorithm type and a data source, and defining the case data used for analysis.</span></span>  
  
 <span data-ttu-id="ab1e3-117">**자세한 내용:** [데이터 마이닝 마법사&#40;Analysis Services - 데이터 마이닝&#41;](data-mining-wizard-analysis-services-data-mining.md)</span><span class="sxs-lookup"><span data-stu-id="ab1e3-117">**For More Information:** [Data Mining Wizard &#40;Analysis Services - Data Mining&#41;](data-mining-wizard-analysis-services-data-mining.md)</span></span>  
  
## <a name="data-mining-designer"></a><span data-ttu-id="ab1e3-118">Data Mining Designer</span><span class="sxs-lookup"><span data-stu-id="ab1e3-118">Data Mining Designer</span></span>  
 <span data-ttu-id="ab1e3-119">데이터 마이닝 마법사를 사용하여 마이닝 구조와 마이닝 모델을 만든 후 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 또는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 에서 데이터 마이닝 디자이너를 사용하여 기존 모델과 구조로 작업할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ab1e3-119">After you have created a mining structure and mining model by using the Data Mining Wizard, you can use the Data Mining Designer from either [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] or [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to work with existing models and structures.</span></span>  
  
 <span data-ttu-id="ab1e3-120">디자이너에는 다음 태스크를 위한 도구가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ab1e3-120">The designer includes tools for these tasks:</span></span>  
  
-   <span data-ttu-id="ab1e3-121">마이닝 구조의 속성을 수정하고, 열을 추가하고 열 별칭을 만들고, 범주화 방법이나 값의 예상 분포를 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="ab1e3-121">Modify the properties of mining structures, add columns and create column aliases, change the binning method or expected distribution of values.</span></span>  
  
-   <span data-ttu-id="ab1e3-122">기존 구조에 새 모델을 추가하고, 모델을 복사하고, 모델 속성이나 메타데이터를 변경하고, 마이닝 모델에 대한 필터를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="ab1e3-122">Add new models to an existing structure; copy models, change model properties or metadata, or define filters on a mining model.</span></span>  
  
-   <span data-ttu-id="ab1e3-123">모델 내의 패턴과 규칙을 찾아보고, 연결 또는 의사 결정 트리를 탐색하고,</span><span class="sxs-lookup"><span data-stu-id="ab1e3-123">Browse the patterns and rules within the model; explore associations or decision trees.</span></span> <span data-ttu-id="ab1e3-124">자세한 통계를 얻습니다.</span><span class="sxs-lookup"><span data-stu-id="ab1e3-124">Get detailed statistics about</span></span>  
  
     <span data-ttu-id="ab1e3-125">데이터를 분석하고 데이터 마이닝으로 드러난 패턴을 탐색하는 데 도움을 주기 위해 사용자 지정 뷰어가 모델의 각기 다른 각 시간에 대해 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="ab1e3-125">Custom viewers are provided for each different time of model, to help you analyze your data and explore the patterns revealed by data mining.</span></span>  
  
-   <span data-ttu-id="ab1e3-126">리프트 차트를 만들거나 모델의 수익 곡선을 분석하여 모델의 유효성을 검사합니다.</span><span class="sxs-lookup"><span data-stu-id="ab1e3-126">Validate models by creating lift charts, or analyzing the profit curve for models.</span></span> <span data-ttu-id="ab1e3-127">분류 행렬을 사용하여 모델을 비교하거나 교차 유효성 검사를 사용하여 데이터 집합과 해당 모델의 유효성을 검사합니다.</span><span class="sxs-lookup"><span data-stu-id="ab1e3-127">Compare models using classification matrices, or validate a data set and its models by using cross-validation.</span></span>  
  
-   <span data-ttu-id="ab1e3-128">기존 마이닝 모델에 대해 예측 및 내용 쿼리를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ab1e3-128">Create predictions and content queries against existing mining models.</span></span> <span data-ttu-id="ab1e3-129">외부 데이터의 전체 테이블에 대한 예측을 생성하기 위해 쿼리를 설정하거나 일회용 쿼리를 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="ab1e3-129">Build one-off queries, or set up queries to generate predictions for entire tables of external data.</span></span>  
  
 <span data-ttu-id="ab1e3-130">**참조 항목:** [데이터 마이닝 디자이너](data-mining-designer.md)</span><span class="sxs-lookup"><span data-stu-id="ab1e3-130">**For More Information:** [Data Mining Designer](data-mining-designer.md)</span></span>  
  
## <a name="sql-server-management-studio"></a><span data-ttu-id="ab1e3-131">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="ab1e3-131">SQL Server Management Studio</span></span>  
 <span data-ttu-id="ab1e3-132">마이닝 모델을 만들어 서버에 배포한 후 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 를 사용하여 데이터 마이닝 개체를 호스팅하는 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 데이터베이스를 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ab1e3-132">After you create and deploy mining models to a server, you can use [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to manage the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database that hosts the data mining objects.</span></span> <span data-ttu-id="ab1e3-133">또한 모델 탐색, 새 데이터 처리, 예측 생성 등의 모델을 사용하는 태스크를 계속 수행할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ab1e3-133">You can also continue to perform tasks that use the model, such as exploring the models, processing new data, and creating predictions.</span></span>  
  
 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] <span data-ttu-id="ab1e3-134">에는 DMX(Data Mining Extensions) 쿼리를 디자인하고 실행하거나 XMLA를 사용하여 데이터 마이닝 개체로 작업하는 데 사용할 수 있는 쿼리 편집기도 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ab1e3-134">also contains query editors that you can use to design and execute Data Mining Extensions (DMX) queries, or ot work with data mining objects by using XMLA.</span></span>  
  
## <a name="integration-services-data-mining-tasks-and-transformations"></a><span data-ttu-id="ab1e3-135">Integration Services 데이터 마이닝 태스크 및 변환</span><span class="sxs-lookup"><span data-stu-id="ab1e3-135">Integration Services Data Mining Tasks and Transformations</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="ab1e3-136">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]는 데이터 마이닝을 지 원하는 많은 구성 요소를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="ab1e3-136">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] provides many components that support data mining.</span></span>  
  
 <span data-ttu-id="ab1e3-137">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 의 일부 도구는 예측, 모델 작성, 처리 등의 일반적인 데이터 마이닝 태스크를 쉽게 자동화할 수 있도록 설계되었습니다.</span><span class="sxs-lookup"><span data-stu-id="ab1e3-137">Some tools in [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] are designed to help automate common data mining tasks, including prediction, model building, and processing.</span></span> <span data-ttu-id="ab1e3-138">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="ab1e3-138">For example:</span></span>  
  
-   <span data-ttu-id="ab1e3-139">데이터 세트가 새 고객으로 업데이트될 때마다 모델을 자동으로 업데이트하는 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 패키지를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ab1e3-139">Create an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package that automatically updates the model every time the dataset is updated with new customers</span></span>  
  
-   <span data-ttu-id="ab1e3-140">사례 레코드의 사용자 지정 구분 또는 사용자 지정 샘플링을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="ab1e3-140">Perform custom segmentation or custom sampling of case records.</span></span>  
  
-   <span data-ttu-id="ab1e3-141">매개 변수에서 전달된 모델을 자동으로 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="ab1e3-141">Automatically generate models passed on parameters.</span></span>  
  
 <span data-ttu-id="ab1e3-142">그러나 다른 프로세스에 대한 입력으로 패키지 워크플로에서 데이터 마이닝을 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ab1e3-142">However, you can also use data mining in a package workflow, as an input to other processes.</span></span> <span data-ttu-id="ab1e3-143">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="ab1e3-143">For example:</span></span>  
  
-   <span data-ttu-id="ab1e3-144">모델에서 생성된 확률 값을 사용하여 텍스트 마이닝 또는 다른 분류 태스크에 대한 점수에 가중치를 부여합니다.</span><span class="sxs-lookup"><span data-stu-id="ab1e3-144">Use probability values generated by the model to weight scores for text mining or other classification tasks.</span></span>  
  
-   <span data-ttu-id="ab1e3-145">이전 데이터를 기반으로 자동으로 예측을 생성하고 해당 값을 사용하여 새 데이터의 유효성을 평가합니다.</span><span class="sxs-lookup"><span data-stu-id="ab1e3-145">Automatically generate predictions based on prior data and use those values to assess the validity of new data.</span></span>  
  
-   <span data-ttu-id="ab1e3-146">로지스틱 회귀를 사용하여 위험을 기준으로 들어오는 고객을 구분합니다.</span><span class="sxs-lookup"><span data-stu-id="ab1e3-146">Using logistic regression to segment incoming customers by risk.</span></span>  
  
 <span data-ttu-id="ab1e3-147">**자세한 내용:** [데이터 마이닝 솔루션 관련 프로젝트](data-mining-solutions.md)</span><span class="sxs-lookup"><span data-stu-id="ab1e3-147">**For More Information:** [Related Projects for Data Mining Solutions](data-mining-solutions.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab1e3-148">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ab1e3-148">See Also</span></span>  
 <span data-ttu-id="ab1e3-149">[DMX&#41; 참조 &#40;데이터 마이닝 확장](/sql/dmx/data-mining-extensions-dmx-reference) </span><span class="sxs-lookup"><span data-stu-id="ab1e3-149">[Data Mining Extensions &#40;DMX&#41; Reference](/sql/dmx/data-mining-extensions-dmx-reference) </span></span>  
 <span data-ttu-id="ab1e3-150">[마이닝 모델 태스크 및 방법](mining-model-tasks-and-how-tos.md) </span><span class="sxs-lookup"><span data-stu-id="ab1e3-150">[Mining Model Tasks and How-tos](mining-model-tasks-and-how-tos.md) </span></span>  
 <span data-ttu-id="ab1e3-151">[마이닝 모델 뷰어 태스크 및 방법](mining-model-viewer-tasks-and-how-tos.md) </span><span class="sxs-lookup"><span data-stu-id="ab1e3-151">[Mining Model Viewer Tasks and How-tos](mining-model-viewer-tasks-and-how-tos.md) </span></span>  
 [<span data-ttu-id="ab1e3-152">데이터 마이닝 솔루션</span><span class="sxs-lookup"><span data-stu-id="ab1e3-152">Data Mining Solutions</span></span>](data-mining-solutions.md)  
  
  
