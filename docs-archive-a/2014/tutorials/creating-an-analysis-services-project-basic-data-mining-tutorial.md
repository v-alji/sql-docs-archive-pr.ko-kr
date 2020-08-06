---
title: Analysis Services 프로젝트 만들기 (기본 데이터 마이닝 자습서) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 784c0401-0358-4117-9c85-4e8220ce71d9
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 83eb808bc7d18ebe715d309d9f911c010ee172d1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646770"
---
# <a name="creating-an-analysis-services-project-basic-data-mining-tutorial"></a><span data-ttu-id="57a9f-102">Analysis Services 프로젝트 만들기(기본 데이터 마이닝 자습서)</span><span class="sxs-lookup"><span data-stu-id="57a9f-102">Creating an Analysis Services Project (Basic Data Mining Tutorial)</span></span>
  <span data-ttu-id="57a9f-103">각 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 프로젝트는 단일 데이터베이스의 개체를 정의 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 합니다.</span><span class="sxs-lookup"><span data-stu-id="57a9f-103">Each [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] project defines the objects in a single [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database.</span></span> <span data-ttu-id="57a9f-104">[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 데이터베이스에는 여러 다른 유형의 개체가 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="57a9f-104">An [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database can contains many different types of objects</span></span>  
  
-   <span data-ttu-id="57a9f-105">다차원 모델(큐브)</span><span class="sxs-lookup"><span data-stu-id="57a9f-105">Multidimensional models (cubes)</span></span>  
  
-   <span data-ttu-id="57a9f-106">마이닝 구조 및 마이닝 모델</span><span class="sxs-lookup"><span data-stu-id="57a9f-106">Mining structures and mining models</span></span>  
  
-   <span data-ttu-id="57a9f-107">데이터 원본, 데이터 원본 뷰 및 사용자 지정 어셈블리와 같은 개체 지원</span><span class="sxs-lookup"><span data-stu-id="57a9f-107">Supporting objects such as data sources, data source views, and custom assemblies</span></span>  
  
 <span data-ttu-id="57a9f-108">데이터 마이닝을 수행하는 데는 큐브가 필요하지 **않습니다** .</span><span class="sxs-lookup"><span data-stu-id="57a9f-108">Note that you **do not** require a cube to do data mining.</span></span> <span data-ttu-id="57a9f-109">기존 큐브에서 데이터 마이닝을 수행해야 하는 경우 큐브를 빌드하는 데 사용한 동일한 프로젝트에 데이터 마이닝 모델을 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="57a9f-109">If you need to perform data mining on an existing cube, you should add the data mining models to the same project you used to build the cube.</span></span> <span data-ttu-id="57a9f-110">그러나 대부분의 경우 데이터 웨어하우스와 같은 관계형 데이터 원본에서 모델을 빌드할 수 있고 큐브가 포함되지 않는 경우 더 나은 성능을 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="57a9f-110">However, for most purposes you can build your models on relational data sources, such as a data warehouse, and get better performance if a cube is not involved.</span></span>  
  
 <span data-ttu-id="57a9f-111">이 자습서에서는 관계형 데이터 웨어하우스 [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)]를 데이터 원본으로 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="57a9f-111">In this tutorial you will use a relational data warehouse, [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)], as the data source.</span></span> <span data-ttu-id="57a9f-112">모든 데이터 마이닝 개체를 데이터 마이닝에만 사용되는 `BasicDataMining`이라는 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 데이터베이스로 배포합니다.</span><span class="sxs-lookup"><span data-stu-id="57a9f-112">You will deploy all your data mining objects to an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database named `BasicDataMining`, used just for data mining.</span></span>  
  
 <span data-ttu-id="57a9f-113">기본적으로 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 에서는 새 프로젝트에 **localhost** 인스턴스를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="57a9f-113">By default, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] uses the **localhost** instance for new projects.</span></span> <span data-ttu-id="57a9f-114">명명된 인스턴스나 다른 서버를 사용할 경우에는 먼저 프로젝트를 만들고 연 다음 인스턴스 이름을 변경해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="57a9f-114">If you are using a named instance or a different server, you must first create and open the project and then change the instance name.</span></span>  
  
 <span data-ttu-id="57a9f-115">프로젝트에 대 한 자세한 내용은 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] [Analysis Services 프로젝트 만들기](../analysis-services/lesson-1-1-creating-an-analysis-services-project.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="57a9f-115">For more information about [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] projects, see [Creating an Analysis Services Project](../analysis-services/lesson-1-1-creating-an-analysis-services-project.md).</span></span>  
  
### <a name="to-create-an-analysis-services-project"></a><span data-ttu-id="57a9f-116">Analysis Services 프로젝트를 만들려면</span><span class="sxs-lookup"><span data-stu-id="57a9f-116">To create an Analysis Services project</span></span>  
  
1.  <span data-ttu-id="57a9f-117">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="57a9f-117">Open [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span>  
  
2.  <span data-ttu-id="57a9f-118">**파일** 메뉴에서 **새로 만들기**를 가리킨 다음 **프로젝트**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="57a9f-118">On the **File** menu, point to **New**, and then select **Project**.</span></span>  
  
3.  <span data-ttu-id="57a9f-119">**프로젝트 형식** 창에서 **비즈니스 인텔리전스 프로젝트** 가 선택되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="57a9f-119">Verify that **Business Intelligence Projects** is selected in the **Project types** pane.</span></span>  
  
4.  <span data-ttu-id="57a9f-120">**템플릿** 창에서 **Analysis Services 다차원 및 데이터 마이닝 프로젝트**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="57a9f-120">In the **Templates** pane, select **Analysis Services Multidimensional and Data Mining Project**.</span></span>  
  
5.  <span data-ttu-id="57a9f-121">**이름** 상자에서 새 프로젝트의 이름을로 `BasicDataMining` 합니다.</span><span class="sxs-lookup"><span data-stu-id="57a9f-121">In the **Name** box, name the new project `BasicDataMining`.</span></span>  
  
6.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
### <a name="to-change-the-instance-where-data-mining-objects-are-stored"></a><span data-ttu-id="57a9f-122">데이터 마이닝 개체가 저장되는 인스턴스를 변경하려면</span><span class="sxs-lookup"><span data-stu-id="57a9f-122">To change the instance where data mining objects are stored</span></span>  
  
1.  <span data-ttu-id="57a9f-123">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]의 **프로젝트** 메뉴에서 **속성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="57a9f-123">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], on the **Project** menu, select **Properties**.</span></span>  
  
2.  <span data-ttu-id="57a9f-124">**속성 페이지** 창 왼쪽의 **구성 속성**에서 **배포**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="57a9f-124">On the left side of the **Property Pages** pane, under **Configuration Properties**, click **Deployment**.</span></span>  
  
3.  <span data-ttu-id="57a9f-125">**속성 페이지** 창 오른쪽의 **대상**에서 **서버** 이름이 **localhost**인지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="57a9f-125">On the right side of the **Property Pages** pane, under **Target**, verify that the **Server** name is **localhost**.</span></span> <span data-ttu-id="57a9f-126">다른 인스턴스를 사용할 경우에는 해당 인스턴스의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="57a9f-126">If you are using a different instance, type the name of the instance.</span></span> [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="57a9f-127">단원의 다음 태스크</span><span class="sxs-lookup"><span data-stu-id="57a9f-127">Next Task in Lesson</span></span>  
 [<span data-ttu-id="57a9f-128">기본 데이터 마이닝 &#40;데이터 원본 만들기 자습서&#41;</span><span class="sxs-lookup"><span data-stu-id="57a9f-128">Creating a Data Source &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/creating-a-data-source-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a><span data-ttu-id="57a9f-129">참고 항목</span><span class="sxs-lookup"><span data-stu-id="57a9f-129">See Also</span></span>  
 <span data-ttu-id="57a9f-130">[SSDT &#40;Analysis Services 프로젝트 빌드&#41;](https://docs.microsoft.com/analysis-services/multidimensional-models/build-analysis-services-projects-ssdt) </span><span class="sxs-lookup"><span data-stu-id="57a9f-130">[Build Analysis Services Projects &#40;SSDT&#41;](https://docs.microsoft.com/analysis-services/multidimensional-models/build-analysis-services-projects-ssdt) </span></span>  
 [<span data-ttu-id="57a9f-131">Analysis Services 프로젝트 만들기&#40;SSDT&#41;</span><span class="sxs-lookup"><span data-stu-id="57a9f-131">Create an Analysis Services Project &#40;SSDT&#41;</span></span>](https://docs.microsoft.com/analysis-services/multidimensional-models/create-an-analysis-services-project-ssdt)  
  
  
