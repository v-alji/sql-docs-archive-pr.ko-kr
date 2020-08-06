---
title: 큐브 찾아보기 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 3819946e-d3fa-4c1d-afe3-599c938b1b2e
author: minewiskan
ms.author: owend
ms.openlocfilehash: 7cbf35866bb0a1f65074a7e106ecf556e98aa30b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639028"
---
# <a name="browsing-the-cube"></a><span data-ttu-id="f0078-102">큐브 찾아보기</span><span class="sxs-lookup"><span data-stu-id="f0078-102">Browsing the Cube</span></span>
  <span data-ttu-id="f0078-103">큐브를 배포하면 큐브 디자이너의 **브라우저** 탭에 큐브 데이터가 표시되고 차원 디자이너의 **브라우저** 탭에 차원 데이터가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="f0078-103">After you deploy a cube, the cube data is viewable on the **Browser** tab in Cube Designer, and the dimension data is viewable on the **Browser** tab in Dimension Designer.</span></span> <span data-ttu-id="f0078-104">큐브 및 차원 데이터 검색을 통해 작업을 증분 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f0078-104">Browsing cube and dimension data is way to check your work incrementally.</span></span> <span data-ttu-id="f0078-105">개체가 처리된 후 속성, 관계 및 기타 개체에 대한 약간의 변경으로 원하는 결과를 얻었는지 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f0078-105">You can verify that small changes to properties, relationships, and other objects have the desired effect once the object is processed.</span></span> <span data-ttu-id="f0078-106">브라우저 탭을 사용하여 큐브 데이터와 차원 데이터 모두를 확인할 수 있지만 이 탭에서는 검색하려는 개체에 따라 다른 기능을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="f0078-106">While the Browser tab is used to view both cube and dimension data, the tab provides different capabilities based on the object you are browsing.</span></span>  
  
 <span data-ttu-id="f0078-107">차원의 경우 브라우저 탭은 리프 노드까지 모두 계층을 탐색하거나 멤버를 볼 수 있는 방법을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="f0078-107">For dimensions, the Browser tab provides a way to view members or navigate a hierarchy all the way down to the leaf node.</span></span> <span data-ttu-id="f0078-108">모델에 번역을 추가한 경우 여러 다른 언어로 차원 데이터를 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f0078-108">You can browse dimension data in different languages, assuming you have added the translations to your model.</span></span>  
  
 <span data-ttu-id="f0078-109">큐브의 경우 브라우저 탭은 데이터를 탐색하는 두 가지 방법을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="f0078-109">For cubes, the Browser tab provides two approaches for exploring data.</span></span> <span data-ttu-id="f0078-110">기본 제공 MDX 쿼리 디자이너를 사용하여 다차원 데이터베이스에서 일반 행 집합을 반환하는 쿼리를 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f0078-110">You can use the built-in MDX Query Designer to build queries that return a flattened rowset from a multidimensional database.</span></span> <span data-ttu-id="f0078-111">또는 Excel 바로 가기를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f0078-111">Alternatively, you can use an Excel shortcut.</span></span> <span data-ttu-id="f0078-112">[!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]에서 Excel을 시작하면 이미 워크시트에 피벗 테이블이 있고 모델 작업 영역 데이터베이스에 연결이 미리 정의된 상태로 Excel이 열립니다.</span><span class="sxs-lookup"><span data-stu-id="f0078-112">When you start Excel from within [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], Excel opens with a PivotTable already in the worksheet and a predefined connection to the model workspace database.</span></span>  
  
 <span data-ttu-id="f0078-113">Excel에서는 가로 축과 세로 축을 통해 데이터의 관계를 분석하여 큐브 데이터를 대화형으로 탐색할 수 있도록 하므로 일반적으로 더 나은 검색 환경을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="f0078-113">Excel generally offers a better browsing experience because you can explore cube data interactively, using horizontal and vertical axes to analyze the relationships in your data.</span></span> <span data-ttu-id="f0078-114">반면 MDX 쿼리 디자이너는 단일 축으로 제한됩니다.</span><span class="sxs-lookup"><span data-stu-id="f0078-114">In contrast, the MDX Query Designer is limited to a single axis.</span></span> <span data-ttu-id="f0078-115">또한 행 집합이 일반화되므로 Excel 피벗 테이블에서 제공하는 드릴 다운을 얻지 못합니다.</span><span class="sxs-lookup"><span data-stu-id="f0078-115">Moreover, because the rowset is flattened, you do not get the drilldown that an Excel PivotTable provides.</span></span> <span data-ttu-id="f0078-116">이후 단원에서 큐브에 차원과 계층을 많이 추가할수록 Excel이 데이터를 검색하기에 좋은 솔루션임을 알게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f0078-116">As you add more dimensions and hierarchies to your cube, which you will do in subsequent lessons, Excel will be the preferred solution for browsing data.</span></span>  
  
### <a name="to-browse-the-deployed-cube"></a><span data-ttu-id="f0078-117">배포된 큐브를 찾아보려면</span><span class="sxs-lookup"><span data-stu-id="f0078-117">To browse the deployed cube</span></span>  
  
1.  <span data-ttu-id="f0078-118">**에서 Product 차원에 대한** 차원 디자이너 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]로 전환합니다.</span><span class="sxs-lookup"><span data-stu-id="f0078-118">Switch to **Dimension Designer** for the Product dimension in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="f0078-119">이렇게 하려면 솔루션 탐색기의 **차원** 노드에서 **Product** 차원을 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f0078-119">To do this, double-click the **Product** dimension in the **Dimensions** node of Solution Explorer.</span></span>  
  
2.  <span data-ttu-id="f0078-120">**브라우저** 탭을 클릭 하 여 특성 계층의 **All** 멤버를 표시 합니다 `Product Key` .</span><span class="sxs-lookup"><span data-stu-id="f0078-120">Click the **Browser** tab to display the **All** member of the `Product Key` attribute hierarchy.</span></span> <span data-ttu-id="f0078-121">3단원에서는 차원을 탐색할 수 있도록 Product 차원에 대한 사용자 계층을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="f0078-121">In lesson three, you will define a user hierarchy for the Product dimension that will let you browse the dimension.</span></span>  
  
3.  <span data-ttu-id="f0078-122">**에서** 큐브 디자이너 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]로 전환합니다.</span><span class="sxs-lookup"><span data-stu-id="f0078-122">Switch to **Cube Designer** in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="f0078-123">이렇게 하려면 솔루션 탐색기의 **큐브** 노드에서 **Analysis Services Tutorial** 큐브를 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f0078-123">To do this, double-click the **Analysis Services Tutorial** cube in the **Cubes** node of Solution Explorer.</span></span>  
  
4.  <span data-ttu-id="f0078-124">**브라우저** 탭을 선택한 다음 디자이너 도구 모음에서 **다시 연결** 아이콘을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f0078-124">Select the **Browser** tab, and then click the **Reconnect** icon on the toolbar of the designer.</span></span>  
  
     <span data-ttu-id="f0078-125">디자이너 왼쪽 창에 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial 큐브의 개체가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="f0078-125">The left pane of the designer shows the objects in the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube.</span></span> <span data-ttu-id="f0078-126">**브라우저** 탭의 오른쪽에는 두 개의 창이 있습니다. 위쪽 창은 **필터** 창이고 아래쪽 창은 **데이터** 창입니다.</span><span class="sxs-lookup"><span data-stu-id="f0078-126">On the right side of the **Browser** tab, there are two panes: the upper pane is the **Filter** pane, and the lower pane is the **Data** pane.</span></span> <span data-ttu-id="f0078-127">다음 단원에서는 큐브 브라우저를 사용하여 분석을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="f0078-127">In an upcoming lesson, you will use the cube browser to do analysis.</span></span>  
  
## <a name="next-lesson"></a><span data-ttu-id="f0078-128">다음 단원</span><span class="sxs-lookup"><span data-stu-id="f0078-128">Next Lesson</span></span>  
 [<span data-ttu-id="f0078-129">3단원: 측정값, 특성 및 계층 수정</span><span class="sxs-lookup"><span data-stu-id="f0078-129">Lesson 3: Modifying Measures, Attributes and Hierarchies</span></span>](lesson-3-modifying-measures-attributes-and-hierarchies.md)  
  
## <a name="see-also"></a><span data-ttu-id="f0078-130">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f0078-130">See Also</span></span>  
 [<span data-ttu-id="f0078-131">MDX 쿼리 편집기&#40;Analysis Services - 다차원 데이터&#41;</span><span class="sxs-lookup"><span data-stu-id="f0078-131">MDX Query Editor &#40;Analysis Services - Multidimensional Data&#41;</span></span>](mdx-query-editor-analysis-services-multidimensional-data.md)  
  
  
