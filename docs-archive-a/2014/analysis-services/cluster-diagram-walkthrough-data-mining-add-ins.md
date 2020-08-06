---
title: 클러스터 다이어그램 연습 (데이터 마이닝 추가 기능) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Visio shapes, cluster
- diagram, cluster
- shapes, data mining
- shapes, cluster
- data mining layout toolbar
ms.assetid: 761bef6a-37d4-4b19-944e-f2aadc75a242
author: minewiskan
ms.author: owend
ms.openlocfilehash: 44ee8cce3cd2498d765c9b69e7f352b49cb0f115
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648685"
---
# <a name="cluster-diagram-walkthrough-data-mining-add-ins"></a><span data-ttu-id="a98e2-102">클러스터 다이어그램 연습(데이터 마이닝 추가 기능)</span><span class="sxs-lookup"><span data-stu-id="a98e2-102">Cluster Diagram Walkthrough (Data Mining Add-ins)</span></span>
  <span data-ttu-id="a98e2-103">클러스터링 모델을 만든 후에는 **Cluster** 셰이프를 사용 하 여 Visio로 가져온 다음 계속 해 서 레이아웃을 사용자 지정 하 고 향상 시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a98e2-103">After you have created a clustering model, you can import it into Visio using the **Cluster** shape and then continue to customize and enhance the layout.</span></span> <span data-ttu-id="a98e2-104">**Visio 용 데이터 마이닝 셰이프** 는 데이터 마이닝 다이어그램을 사용 하기 위한 다음과 같은 사용자 지정 컨트롤을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="a98e2-104">The **Data Mining Shapes for Visio** include the following custom controls for working with data mining diagrams:</span></span>  
  
-   <span data-ttu-id="a98e2-105">클러스터 다이어그램의 렌더링 컨트롤</span><span class="sxs-lookup"><span data-stu-id="a98e2-105">Rendering controls for the cluster diagram</span></span>  
  
     <span data-ttu-id="a98e2-106">이러한 옵션은 Visio 작업 영역에 셰이프를 놓을 때 시작 되는 **클러스터 마법사** 의 일부입니다.</span><span class="sxs-lookup"><span data-stu-id="a98e2-106">These options are part of the **Cluster Wizard** that is launched when you drop a shape into the Visio workspace.</span></span>  
  
-   <span data-ttu-id="a98e2-107">**데이터 마이닝 레이아웃** 도구 모음</span><span class="sxs-lookup"><span data-stu-id="a98e2-107">**Data Mining Layout** toolbar</span></span>  
  
     <span data-ttu-id="a98e2-108">이러한 옵션은 데이터 마이닝 셰이프와 상호 작용하는 데 도움이 되도록 Visio 작업 영역에 추가되며,</span><span class="sxs-lookup"><span data-stu-id="a98e2-108">These options are added to the Visio workspace to help you interact with the data mining shape.</span></span> <span data-ttu-id="a98e2-109">사용하고 있는 데이터 마이닝 모델의 유형에 따라 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="a98e2-109">The options are different depending on which type of data mining model you are using.</span></span>  
  
## <a name="build-a-cluster-diagram"></a><span data-ttu-id="a98e2-110">클러스터 다이어그램 작성</span><span class="sxs-lookup"><span data-stu-id="a98e2-110">Build a Cluster Diagram</span></span>  
 <span data-ttu-id="a98e2-111">이 연습에서는 Visio에서 클러스터링 다이어그램을 작성하고 사용자 지정하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="a98e2-111">This walkthrough demonstrates how to build and customize a clustering diagram in Visio.</span></span>  
  
 <span data-ttu-id="a98e2-112">이 연습을 실행하려면 사용할 수 있는 클러스터링 모델이 이미 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a98e2-112">To follow along, you should have a clustering model already available.</span></span> <span data-ttu-id="a98e2-113">모델이 없는 경우 클러스터 마법사를 사용 하 여 [Excel 용 데이터 마이닝 추가 기능&#41;](cluster-wizard-data-mining-add-ins-for-excel.md) 마법사를 &#40;하 고 모든 기본값을 사용 하 여 예제 통합 문서의 학습 데이터 집합을 사용 하 여 모델을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="a98e2-113">If you do not have a model, use the [Cluster Wizard &#40;Data Mining Add-ins for Excel&#41;](cluster-wizard-data-mining-add-ins-for-excel.md) wizard and create a model using the Training data set in the sample workbook, using all the defaults.</span></span>  
  
#### <a name="use-the-cluster-visio-shape-wizard"></a><span data-ttu-id="a98e2-114">클러스터 Visio 셰이프 마법사 사용</span><span class="sxs-lookup"><span data-stu-id="a98e2-114">Use the Cluster Visio Shape Wizard</span></span>  
  
1.  <span data-ttu-id="a98e2-115">**셰이프** 목록에 **Microsoft 데이터 마이닝 셰이프가** 표시 되지 않는 경우 **추가 셰이프**를 클릭 하 고, **스텐실 열기**를 선택 하 고, 기본 설치 위치에서 템플릿을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="a98e2-115">If you do not see **Microsoft Data Mining Shapes** in the **Shapes** list, click **More Shapes**, select **Open Stencil**, and open the template from the default installation location.</span></span>  
  
     <span data-ttu-id="a98e2-116">\<drive>: Files\Microsoft SQL Server 2012 DM 추가 기능</span><span class="sxs-lookup"><span data-stu-id="a98e2-116">\<drive>:\Program files\Microsoft SQL Server 2012 DM Add-Ins</span></span>  
  
2.  <span data-ttu-id="a98e2-117">**클러스터** 셰이프를 페이지로 끌어옵니다.</span><span class="sxs-lookup"><span data-stu-id="a98e2-117">Drag the **Cluster** shape onto the page.</span></span>  
  
3.  <span data-ttu-id="a98e2-118">**클러스터 Visio 셰이프 마법사**의 시작 페이지에서 **다음**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="a98e2-118">On the welcome page of the **Cluster Visio Shape Wizard**, click **Next**.</span></span>  
  
4.  <span data-ttu-id="a98e2-119">**클러스터 마법사**의 **데이터 원본 선택** 페이지에서 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 시각화할 데이터 마이닝 모델을 포함 하는 서버에 대 한 연결을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="a98e2-119">On the **Select a Data Source** page of the **Cluster Wizard**, choose a connection to an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] server that contains the data mining models you want to visualize.</span></span>  
  
5.  <span data-ttu-id="a98e2-120">적절 한 마이닝 모델을 선택 하 고 **다음**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="a98e2-120">Select an appropriate mining model, and click **Next**.</span></span>  
  
     <span data-ttu-id="a98e2-121">클러스터링 모델을 선택 하려면 **속성** 창에서 설명을 검토 합니다.</span><span class="sxs-lookup"><span data-stu-id="a98e2-121">To make sure you choose a clustering model, review the description in the **Properties** pane.</span></span>  
  
6.  <span data-ttu-id="a98e2-122">연결에 성공 하면 **클러스터 다이어그램의 옵션**페이지에서 Visio 프레젠테이션에 포함할 클러스터 다이어그램의 유형을 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a98e2-122">If the connection is successful, on the page, **Options for cluster diagram**, you decide which type of cluster diagram to include in your Visio presentation:</span></span>  
  
     <span data-ttu-id="a98e2-123">**클러스터 셰이프만 표시**</span><span class="sxs-lookup"><span data-stu-id="a98e2-123">**Show cluster shapes only**</span></span>  
     <span data-ttu-id="a98e2-124">이 옵션은 각 클러스터가 사각형이나 선택한 다른 셰이프로 표시되는 간단한 클러스터 다이어그램을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="a98e2-124">This option creates a simple cluster diagram, with each cluster represented by a rectangle or other shape you choose</span></span>  
  
     <span data-ttu-id="a98e2-125">**특징 차트로 클러스터 표시**</span><span class="sxs-lookup"><span data-stu-id="a98e2-125">**Show clusters with characteristics chart**</span></span>  
     <span data-ttu-id="a98e2-126">이 옵션은 위와 동일한 차트를 만들지만 셰이프 내에 클러스터의 특징을 설명하는 히스토그램이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a98e2-126">This option creates the same chart as above, but inside the shapes are histograms that describe the characteristics of the cluster.</span></span>  
  
     <span data-ttu-id="a98e2-127">![Visio의 클러스터 특징 차트 예](media/dm13-visio-cluster-samplecharshape.gif "Visio의 클러스터 특징 차트 예")</span><span class="sxs-lookup"><span data-stu-id="a98e2-127">![Example of cluster characteristics chart in Visio](media/dm13-visio-cluster-samplecharshape.gif "Example of cluster characteristics chart in Visio")</span></span>  
  
     <span data-ttu-id="a98e2-128">**판별 차트로 클러스터 표시**</span><span class="sxs-lookup"><span data-stu-id="a98e2-128">**Show clusters with discrimination chart**</span></span>  
     <span data-ttu-id="a98e2-129">이 옵션은 클러스터 다이어그램과 동일한 차트를 만들지만 다른 클러스터와 가장 크게 구별되는 현재 클러스터의 특징을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="a98e2-129">This option creates the same chart as the cluster diagram, but instead lists the characteristics of the current cluster that most strongly distinguish it from other clusters.</span></span>  
  
     <span data-ttu-id="a98e2-130">마법사에서 다이어그램이 작성된 후 클러스터를 마우스 오른쪽 단추로 클릭하고 새 차트 유형을 선택하여 다른 차트 유형으로 전환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a98e2-130">You can switch to another chart type after the wizard has built the diagram, by right-clicking a cluster and selecting a new chart type.</span></span> <span data-ttu-id="a98e2-131">지금은 **특성 차트를 사용 하 여 클러스터 표시**옵션을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="a98e2-131">For now, choose the option, **Show clusters with characteristics chart**.</span></span>  
  
7.  <span data-ttu-id="a98e2-132">**차트의 행 수**옵션을 5로 둡니다.</span><span class="sxs-lookup"><span data-stu-id="a98e2-132">Leave the option, **Number of rows in the chart**, as 5.</span></span>  
  
     <span data-ttu-id="a98e2-133">이 옵션은 모델의 클러스터 수를 변경 하지 않습니다. 각 클러스터의 기능으로 표시할 수 있는 특성의 수를 제한 하기만 합니다.</span><span class="sxs-lookup"><span data-stu-id="a98e2-133">This option doesn't change the number of clusters in the model; it simply limits the number of attributes that can be displayed as features of each cluster.</span></span>  
  
     <span data-ttu-id="a98e2-134">그러나이 옵션은 차트 데이터의 필터 역할을 하므로 나중에 항목 수를 늘릴 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a98e2-134">However, the option acts as a filter on the chart data, so you can't increase the number of items later.</span></span>  
  
8.  <span data-ttu-id="a98e2-135">**고급**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a98e2-135">Click **Advanced**.</span></span>  
  
     <span data-ttu-id="a98e2-136">**클러스터 옵션** 대화 상자에서 다이어그램에 사용 되는 셰이프의 시각적 모양을 사용자 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a98e2-136">The **Cluster Options** dialog box is where you customize the visual appearance of shapes used in the diagram.</span></span> <span data-ttu-id="a98e2-137">그래프에 사용된 색과 클러스터에 사용된 셰이프를 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a98e2-137">You can change the colors used in the graph, and the shape used for clusters.</span></span>  
  
     <span data-ttu-id="a98e2-138">**음영 변수** 컨트롤은 Office 2013에서 작동 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a98e2-138">The **Shading Variable** control does not work in Office 2013.</span></span>  
  
     <span data-ttu-id="a98e2-139">![고급을 클릭하여 셰이프 색 선택](media/dm13-visio-clusteroptions-advanced.gif "고급을 클릭하여 셰이프 색 선택")</span><span class="sxs-lookup"><span data-stu-id="a98e2-139">![click Advanced to choose shape colors](media/dm13-visio-clusteroptions-advanced.gif "click Advanced to choose shape colors")</span></span>  
  
     <span data-ttu-id="a98e2-140">**팁:** 일부 색은 나중에 Visio 테마 및 셰이프 편집 컨트롤을 사용 하 여 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a98e2-140">**Tip:** Some colors can be altered later by using Visio themes and shape editing controls.</span></span> <span data-ttu-id="a98e2-141">그러나 Visio 테마는 이러한 색 선택 중 일부를 재정의하기도 하므로 기본 색부터 시작하여 점차적으로 변경을 적용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="a98e2-141">However, Visio themes will also override some of these color selections, so we recommend starting with the default colors and gradually applying changes.</span></span>  
  
9. <span data-ttu-id="a98e2-142">**마침** 을 클릭 하 여 그래프를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="a98e2-142">Click **Finish** to create the graph.</span></span>  
  
     <span data-ttu-id="a98e2-143">마법사는 데이터 마이닝 모델에서 정보를 검색하고 셰이프를 렌더링한 다음 각 클러스터를 특성 및 값으로 채웁니다.</span><span class="sxs-lookup"><span data-stu-id="a98e2-143">The wizard retrieves information from the data mining model, renders the shapes, and populates each cluster with attributes and values.</span></span>  
  
     <span data-ttu-id="a98e2-144">![종속성 네트워크](media/dm13-visiodepnet-defaultgraph.gif "종속성 네트워크")</span><span class="sxs-lookup"><span data-stu-id="a98e2-144">![a dependency network](media/dm13-visiodepnet-defaultgraph.gif "a dependency network")</span></span>  
  
## <a name="explore-and-modify-the-finished-diagram"></a><span data-ttu-id="a98e2-145">완성된 다이어그램 탐색 및 수정</span><span class="sxs-lookup"><span data-stu-id="a98e2-145">Explore and Modify the Finished Diagram</span></span>  
 <span data-ttu-id="a98e2-146">다이어그램이 완성된 후 다음 예와 같이 Visio 컨트롤을 사용하여 모양을 계속해서 사용자 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a98e2-146">After the diagram is complete, you can continue to customize the appearance using the Visio controls, as shown in the following example.</span></span>  
  
 <span data-ttu-id="a98e2-147">![Visio를 사용하여 사용자 지정된 클러스터 다이어그램](media/dm13-visio-clustercomplete1.gif "Visio를 사용하여 사용자 지정된 클러스터 다이어그램")</span><span class="sxs-lookup"><span data-stu-id="a98e2-147">![cluster diagram customized using Visio](media/dm13-visio-clustercomplete1.gif "cluster diagram customized using Visio")</span></span>  
  
 <span data-ttu-id="a98e2-148">기본적인 클러스터 셰이프는 모두 마법사에서 생성됩니다. 다이어그램을 업데이트하고 개인 설정하려면 다음 도구를 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="a98e2-148">All of the basic cluster shapes are generated by the wizard; use the following tools to update and personalize the diagram:</span></span>  
  
1.  <span data-ttu-id="a98e2-149">**클러스터 옵션** 컨트롤에서 슬라이더를 끌어 약한 관계를 필터링 하 고 다이어그램을 간소화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a98e2-149">Drag the slider in the **Cluster Options** control, to filter out weaker relationships and simplify the diagram.</span></span>  
  
2.  <span data-ttu-id="a98e2-150">Visio **레이아웃 다시 사용 페이지** 옵션을 사용 하 여 다른 클러스터 레이아웃을 시험해 봅니다.</span><span class="sxs-lookup"><span data-stu-id="a98e2-150">Use the Visio **Re-Layout Page** option to experiment with different cluster layouts.</span></span>  
  
3.  <span data-ttu-id="a98e2-151">**디자인** 탭에서 연결선 옵션을 사용 하 **여 커넥터 스타일** 을 변경 하 여 행이 클러스터에서 교차 하지 않도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="a98e2-151">Use the **Connectors** option on the **Design** tab to change the connector style to keep lines from crossing over clusters.</span></span>  
  
4.  <span data-ttu-id="a98e2-152">**추가 기능** 리본을 클릭 한 다음 데이터 마이닝 다이어그램 작업에 사용 되는 사용자 지정 도구 모음 중 하나를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="a98e2-152">Click the **Add-Ins** ribbon, and then display one of the custom toolbars used for working with data mining diagrams:</span></span>  
  
     <span data-ttu-id="a98e2-153">**레이아웃**</span><span class="sxs-lookup"><span data-stu-id="a98e2-153">**Layout**</span></span>  
     <span data-ttu-id="a98e2-154">현재 페이지에 맞도록 클러스터의 정렬을 최적화합니다.</span><span class="sxs-lookup"><span data-stu-id="a98e2-154">Optimizes the arrangement of clusters to fit in the current page.</span></span>  
  
     <span data-ttu-id="a98e2-155">**페이지 크기 조정**</span><span class="sxs-lookup"><span data-stu-id="a98e2-155">**Resize Page**</span></span>  
     <span data-ttu-id="a98e2-156">이 컨트롤은 이전 HTML 버전용입니다.</span><span class="sxs-lookup"><span data-stu-id="a98e2-156">This control was intended for earlier HTML versions.</span></span> <span data-ttu-id="a98e2-157">Visio 페이지 크기 조정 컨트롤을 대신 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="a98e2-157">Use the Visio page resizing controls instead.</span></span>  
  
     <span data-ttu-id="a98e2-158">**설명**</span><span class="sxs-lookup"><span data-stu-id="a98e2-158">**Description**</span></span>  
     <span data-ttu-id="a98e2-159">클러스터가 선택된 경우 이 옵션을 클릭하면 클러스터에 대한 세부 정보가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="a98e2-159">If a cluster is selected, click this option to display details about the cluster.</span></span>  
  
     <span data-ttu-id="a98e2-160">![설명을 클릭하여 클러스터에 대한 정보 가져오기](media/dm13-visio-cluster-description-control.gif "설명을 클릭하여 클러스터에 대한 정보 가져오기")</span><span class="sxs-lookup"><span data-stu-id="a98e2-160">![click Description to get details about the cluster](media/dm13-visio-cluster-description-control.gif "click Description to get details about the cluster")</span></span>  
  
     <span data-ttu-id="a98e2-161">**가장자리 수준**</span><span class="sxs-lookup"><span data-stu-id="a98e2-161">**Edge Strength**</span></span>  
     <span data-ttu-id="a98e2-162">클러스터를 연결하는 선에 대한 신뢰성 점수를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="a98e2-162">Displays confidence scores on the lines connecting clusters.</span></span>  
  
     <span data-ttu-id="a98e2-163">그러나 일부 배경을 비롯하여 마법사에서 생성된 기본 서식 이외의 특수한 서식을 적용하는 경우 이러한 점수가 표시되지 않을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a98e2-163">However, if you apply any special formatting other than the default generated by the wizard, including some backgrounds, these numbers might not be visible.</span></span>  
  
     <span data-ttu-id="a98e2-164">**슬라이더**</span><span class="sxs-lookup"><span data-stu-id="a98e2-164">**Slider**</span></span>  
     <span data-ttu-id="a98e2-165">클러스터 사이의 선을 필터링합니다.</span><span class="sxs-lookup"><span data-stu-id="a98e2-165">Filters the lines between clusters.</span></span> <span data-ttu-id="a98e2-166">슬라이더를 위로 이동하면 가장 중요한 연결을 제외하고 모두 제거됩니다.</span><span class="sxs-lookup"><span data-stu-id="a98e2-166">Moving the slider up removes all but the most important associations.</span></span>  
  
     <span data-ttu-id="a98e2-167">**음영**</span><span class="sxs-lookup"><span data-stu-id="a98e2-167">**Shading**</span></span>  
     <span data-ttu-id="a98e2-168">이 컨트롤은 Office 2013에서 작동하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a98e2-168">This control does not work in Office 2013.</span></span>  
  
5.  <span data-ttu-id="a98e2-169">Visio **뷰** 리본의 **작업 창** 영역에서 **팬 및 확대/축소** 컨트롤을 사용 하 여 클러스터 집합에 초점을 맞춘 후 다이어그램 주위로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="a98e2-169">Use the **Pan and Zoom** control, in the **Task Pane** area of the Visio **View** ribbon, to focus on a set of clusters and move around the diagram.</span></span>  
  
6.  <span data-ttu-id="a98e2-170">클러스터를 마우스 오른쪽 단추로 클릭하여 클러스터 셰이프와 관련된 옵션을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="a98e2-170">Right-click any cluster to see options specific to the cluster shape:</span></span>  
  
    -   <span data-ttu-id="a98e2-171">차트 스타일 변경</span><span class="sxs-lookup"><span data-stu-id="a98e2-171">Change the chart style.</span></span>  
  
    -   <span data-ttu-id="a98e2-172">클러스터 특징 차트 추가</span><span class="sxs-lookup"><span data-stu-id="a98e2-172">Add a cluster characteristics chart.</span></span>  
  
    -   <span data-ttu-id="a98e2-173">클러스터 판별 차트 추가</span><span class="sxs-lookup"><span data-stu-id="a98e2-173">Add a cluster discrimination chart.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a98e2-174">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a98e2-174">See Also</span></span>  
 [<span data-ttu-id="a98e2-175">Visio 데이터 마이닝 다이어그램 문제 해결 SQL Server 데이터 마이닝 추가 기능을 &#40;&#41;</span><span class="sxs-lookup"><span data-stu-id="a98e2-175">Troubleshooting Visio Data Mining Diagrams &#40;SQL Server Data Mining Add-ins&#41;</span></span>](troubleshooting-visio-data-mining-diagrams-sql-server-data-mining-add-ins.md)  
  
  
