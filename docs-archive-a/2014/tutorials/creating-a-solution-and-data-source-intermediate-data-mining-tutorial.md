---
title: 솔루션 및 데이터 원본 만들기 (중급 데이터 마이닝 자습서) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 0488b231-1045-4169-aabb-c1005d86ca30
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 48009fae653c4c1a231380e8d286363168ae28d6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648247"
---
# <a name="creating-a-solution-and-data-source-intermediate-data-mining-tutorial"></a><span data-ttu-id="7c2e8-102">솔루션 및 데이터 원본 만들기(중급 데이터 마이닝 자습서)</span><span class="sxs-lookup"><span data-stu-id="7c2e8-102">Creating a Solution and Data Source (Intermediate Data Mining Tutorial)</span></span>
  <span data-ttu-id="7c2e8-103">데이터 마이닝을 사용하려면 먼저 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] Analysis Services 다차원 및 데이터 마이닝 프로젝트 **템플릿을 사용하여**에서 프로젝트를 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7c2e8-103">To work with data mining, you must first create a project in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] using the template, **Analysis Services Multidimensional and Data Mining Project**.</span></span> <span data-ttu-id="7c2e8-104">템플릿을 열면 데이터 원본, 마이닝 구조 및 마이닝 모델뿐 아니라 마이닝 구조에서 다차원 데이터를 사용하는 경우 큐브도 포함하여 데이터 마이닝에 필요할 수 있는 모든 스키마가 디자이너로 로드됩니다.</span><span class="sxs-lookup"><span data-stu-id="7c2e8-104">When you open the template, it loads into the designer all the schemas that you might need for data mining: data sources, mining structures and mining models, and even cubes if your mining structure uses multidimensional data.</span></span>  
  
 <span data-ttu-id="7c2e8-105">프로젝트를 만들면 솔루션이 배포될 때까지 솔루션이 로컬 파일로 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="7c2e8-105">When you create the project, your solution is stored as a local file until the solution is deployed.</span></span> <span data-ttu-id="7c2e8-106">솔루션을 배포하면 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 는 프로젝트 속성에 지정된 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 서버를 찾은 다음 프로젝트와 동일한 이름의 새 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 데이터베이스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="7c2e8-106">When you deploy the solution, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] looks for the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] server specified in the project properties, and creates a new [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database with the same name as the project.</span></span> <span data-ttu-id="7c2e8-107">기본적으로 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 에서는 새 프로젝트에 **localhost** 인스턴스를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="7c2e8-107">By default, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] uses the **localhost** instance for new projects.</span></span> <span data-ttu-id="7c2e8-108">명명된 인스턴스를 사용하거나 기본 인스턴스에 대해 다른 이름을 지정한 경우에는 프로젝트의 배포 데이터베이스 속성을 데이터 마이닝 개체를 만들려는 위치로 변경해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7c2e8-108">If you are using a named instance, or if you specified a different name for the default instance, you must change the deployment database property of the project to the location where you want to create your data mining objects.</span></span>  
  
 <span data-ttu-id="7c2e8-109">프로젝트에 대 한 자세한 내용은 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] [Analysis Services 프로젝트 &#40;SSDT&#41;만들기 ](https://docs.microsoft.com/analysis-services/multidimensional-models/create-an-analysis-services-project-ssdt)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="7c2e8-109">For more information about [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] projects, see [Create an Analysis Services Project &#40;SSDT&#41;](https://docs.microsoft.com/analysis-services/multidimensional-models/create-an-analysis-services-project-ssdt).</span></span>  
  
### <a name="to-create-a-new-analysis-services-project-for-this-tutorial"></a><span data-ttu-id="7c2e8-110">이 자습서에 사용할 새 Analysis Services 프로젝트를 만들려면</span><span class="sxs-lookup"><span data-stu-id="7c2e8-110">To create a new Analysis Services project for this tutorial</span></span>  
  
1.  <span data-ttu-id="7c2e8-111">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="7c2e8-111">Open [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span>  
  
2.  <span data-ttu-id="7c2e8-112">**파일** 메뉴에서 **새로 만들기**를 가리킨 다음 **프로젝트**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7c2e8-112">On the **File** menu, point to **New**, and then click **Project**.</span></span>  
  
3.  <span data-ttu-id="7c2e8-113">**설치된 템플릿** 창에서 **Analysis Services 다차원 및 데이터 마이닝 프로젝트** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="7c2e8-113">Select **Analysis Services Multidimensional and Data Mining Project** from the **Installed Templates** pane.</span></span>  
  
4.  <span data-ttu-id="7c2e8-114">**이름** 상자에서 새 프로젝트의 이름을 **DM Intermediate**로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="7c2e8-114">In the **Name** box, name the new project **DM Intermediate**.</span></span>  
  
5.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
### <a name="to-change-the-instance-where-data-mining-objects-are-stored-optional"></a><span data-ttu-id="7c2e8-115">데이터 마이닝 개체가 저장되는 인스턴스를 변경하려면(선택 사항)</span><span class="sxs-lookup"><span data-stu-id="7c2e8-115">To change the instance where data mining objects are stored (optional)</span></span>  
  
1.  <span data-ttu-id="7c2e8-116">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]의 **프로젝트** 메뉴에서 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7c2e8-116">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], on the **Project** menu, click **Properties**.</span></span>  
  
2.  <span data-ttu-id="7c2e8-117">**속성 페이지** 창의 왼쪽에서 **배포**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7c2e8-117">In the left side of the **Property Pages** pane, click **Deployment**.</span></span>  
  
3.  <span data-ttu-id="7c2e8-118">**서버** 이름이 **localhost**인지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="7c2e8-118">Verify that the **Server** name is **localhost**.</span></span> <span data-ttu-id="7c2e8-119">다른 인스턴스를 사용할 경우에는 해당 인스턴스의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="7c2e8-119">If you are using a different instance, type the name of the instance.</span></span> <span data-ttu-id="7c2e8-120">[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]의 명명된 인스턴스를 사용할 경우 컴퓨터 이름을 입력한 다음 인스턴스 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="7c2e8-120">If you are using a named instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], type the machine name and then the instance name.</span></span> [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
### <a name="to-change-the-deployment-properties-for-a-project-optional"></a><span data-ttu-id="7c2e8-121">프로젝트의 배포 속성을 변경하려면(선택 사항)</span><span class="sxs-lookup"><span data-stu-id="7c2e8-121">To change the deployment properties for a project (optional)</span></span>  
  
1.  <span data-ttu-id="7c2e8-122">솔루션 탐색기에서 프로젝트를 마우스 오른쪽 단추로 클릭한 다음 **속성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="7c2e8-122">In Solution Explorer, right-click the project, and then select **Properties**.</span></span>  
  
     <span data-ttu-id="7c2e8-123">-- 또는 --</span><span class="sxs-lookup"><span data-stu-id="7c2e8-123">-- or --</span></span>  
  
     <span data-ttu-id="7c2e8-124">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]의 **프로젝트** 메뉴에서 **속성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="7c2e8-124">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], on the **Project** menu, select **Properties**.</span></span>  
  
2.  <span data-ttu-id="7c2e8-125">**속성 페이지** 창의 왼쪽에서 **배포**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7c2e8-125">In the left side of the **Property Pages** pane, click **Deployment**.</span></span>  
  
     <span data-ttu-id="7c2e8-126">**옵션** 창에서 **배포 모드**를 선택하고 옵션을 **모두 배포** 로 설정하여 덮어쓰거나 **변경 내용만 배포** 로 설정하여 개체를 업데이트하거나 개체를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="7c2e8-126">In the **Options** pane, select **Deployment Mode**, and set the options to **Deploy All** to overwrite, or to **Deploy Changes Only** to update objects or add objects.</span></span>  
  
## <a name="creating-a-data-source"></a><span data-ttu-id="7c2e8-127">데이터 원본 만들기</span><span class="sxs-lookup"><span data-stu-id="7c2e8-127">Creating a Data Source</span></span>  
 <span data-ttu-id="7c2e8-128">기본 데이터 마이닝 자습서에서는 *데이터베이스에 대한 연결 정보를 저장하는* 데이터 원본 [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] 을 만들었습니다.</span><span class="sxs-lookup"><span data-stu-id="7c2e8-128">In the Basic Data Mining Tutorial, you created a *data source* that stores connection information for the [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] database.</span></span> <span data-ttu-id="7c2e8-129">동일한 단계를 수행하여 이 솔루션에 [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] 데이터 원본을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="7c2e8-129">Follow the same steps to create the [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] data source in this solution.</span></span>  
  
#### <a name="to-create-a-data-source"></a><span data-ttu-id="7c2e8-130">데이터 원본을 만들려면</span><span class="sxs-lookup"><span data-stu-id="7c2e8-130">To create a data source</span></span>  
  
-   [<span data-ttu-id="7c2e8-131">기본 데이터 마이닝 &#40;데이터 원본 만들기 자습서&#41;</span><span class="sxs-lookup"><span data-stu-id="7c2e8-131">Creating a Data Source &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/creating-a-data-source-basic-data-mining-tutorial.md)  
  
 <span data-ttu-id="7c2e8-132">단일 데이터 원본으로 여러 데이터 원본 뷰를 지원할 수 있으며 각 데이터 원본 뷰에 여러 테이블을 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7c2e8-132">A single data source can support multiple data source views, and each data source view can have multiple tables.</span></span> <span data-ttu-id="7c2e8-133">그러나 데이터 원본 및 데이터 원본 뷰가 사용자가 만드는 데이터 마이닝 모델과 함께 데이터베이스에 배포 되기 때문에 각 데이터 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 원본 뷰에 각 데이터 마이닝 모델 또는 모델 그룹에 필요한 테이블만 포함 하는 것이 가장 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="7c2e8-133">However, because the data source and data source view are deployed to your [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database together with the data mining models that you create, as a best practice you should include in each data source view only those tables that are required for each data mining model or group of models.</span></span>  
  
 <span data-ttu-id="7c2e8-134">다음 단원에서는 각 새 시나리오를 지원하기 위해 데이터 원본 뷰를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="7c2e8-134">In the following lessons, you will add data source views to support each of the new scenarios.</span></span> <span data-ttu-id="7c2e8-135">시장 바구니 및 시퀀스 클러스터링 단원에서만 동일한 데이터 원본 뷰를 사용하고 각 시나리오에서 다른 데이터 원본 뷰를 사용하므로 두 단원은 서로 독립적이며 별도로 완료할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7c2e8-135">Only the market basket and sequence clustering lessons use the same data source view; otherwise, each scenario uses a different data source view, so the lessons are independent of each other and can be completed separately.</span></span>  
  
|<span data-ttu-id="7c2e8-136">시나리오</span><span class="sxs-lookup"><span data-stu-id="7c2e8-136">Scenario</span></span>|<span data-ttu-id="7c2e8-137">데이터 원본 뷰에 포함된 데이터</span><span class="sxs-lookup"><span data-stu-id="7c2e8-137">Data included in the data source view</span></span>|  
|--------------|-------------------------------------------|  
|[<span data-ttu-id="7c2e8-138">2 단원: 중급 데이터 마이닝 자습서 &#40;예측 시나리오 구축&#41;</span><span class="sxs-lookup"><span data-stu-id="7c2e8-138">Lesson 2: Building a Forecasting Scenario &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-2-building-a-forecasting-scenario-intermediate-data-mining-tutorial.md)|<span data-ttu-id="7c2e8-139">단일 뷰로 수집된 여러 지역의 자전거 모델에 대한 월별 판매 보고서</span><span class="sxs-lookup"><span data-stu-id="7c2e8-139">Monthly sales reports for bicycle models in different regions, collected as a single view.</span></span>|  
|[<span data-ttu-id="7c2e8-140">3단원: 시장 바구니 시나리오 구축&#40;중급 데이터 마이닝 자습서&#41;</span><span class="sxs-lookup"><span data-stu-id="7c2e8-140">Lesson 3: Building a Market Basket Scenario &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-3-building-a-market-basket-scenario-intermediate-data-mining-tutorial.md)|<span data-ttu-id="7c2e8-141">고객 주문 목록이 포함된 테이블 및 각 고객의 개별 구매가 표시된 중첩 테이블</span><span class="sxs-lookup"><span data-stu-id="7c2e8-141">A table containing a list of customer orders, and a nested table showing the individual purchases for each customer.</span></span>|  
|[<span data-ttu-id="7c2e8-142">4 단원: 중간 데이터 마이닝 자습서 &#40;시퀀스 클러스터링 시나리오 빌드&#41;</span><span class="sxs-lookup"><span data-stu-id="7c2e8-142">Lesson 4: Building a Sequence Clustering Scenario &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-4-build-sequence-clustering-scenario-intermediate-data-mining.md)|<span data-ttu-id="7c2e8-143">항목이 구매된 순서를 표시하는 식별자를 추가하여 시장 바구니 분석에 사용되는 동일한 데이터</span><span class="sxs-lookup"><span data-stu-id="7c2e8-143">The same data that is used for the market basket analysis, with the addition of an identifier that shows the order in which items were purchased.</span></span>|  
|[<span data-ttu-id="7c2e8-144">5단원: 신경망 및 로지스틱 회귀 모델 작성&#40;중급 데이터 마이닝 자습서&#41;</span><span class="sxs-lookup"><span data-stu-id="7c2e8-144">Lesson 5: Building Neural Network and Logistic Regression Models &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-5-build-models-intermediate-data-mining-tutorial.md)|<span data-ttu-id="7c2e8-145">콜 센터에서 받은 일부 예비 성과 추적 데이터가 포함된 단일 테이블</span><span class="sxs-lookup"><span data-stu-id="7c2e8-145">A single table containing some preliminary performance tracking data from a call center.</span></span>|  
  
## <a name="next-lesson"></a><span data-ttu-id="7c2e8-146">다음 단원</span><span class="sxs-lookup"><span data-stu-id="7c2e8-146">Next Lesson</span></span>  
 [<span data-ttu-id="7c2e8-147">2 단원: 중급 데이터 마이닝 자습서 &#40;예측 시나리오 구축&#41;</span><span class="sxs-lookup"><span data-stu-id="7c2e8-147">Lesson 2: Building a Forecasting Scenario &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-2-building-a-forecasting-scenario-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a><span data-ttu-id="7c2e8-148">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7c2e8-148">See Also</span></span>  
 <span data-ttu-id="7c2e8-149">[데이터 마이닝 프로젝트](../../2014/analysis-services/data-mining/data-mining-projects.md) </span><span class="sxs-lookup"><span data-stu-id="7c2e8-149">[Data Mining Projects](../../2014/analysis-services/data-mining/data-mining-projects.md) </span></span>  
 [<span data-ttu-id="7c2e8-150">다차원 모델의 데이터 원본 뷰</span><span class="sxs-lookup"><span data-stu-id="7c2e8-150">Data Source Views in Multidimensional Models</span></span>](https://docs.microsoft.com/analysis-services/multidimensional-models/data-source-views-in-multidimensional-models)  
  
  
