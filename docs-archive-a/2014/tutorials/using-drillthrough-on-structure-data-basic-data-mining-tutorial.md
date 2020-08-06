---
title: 구조 데이터에 드릴스루 사용 (기본 데이터 마이닝 자습서) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: a693979c-0564-4d6d-b35d-cbbc8f350469
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 49a1ced27150676def541548f47a90a3f847c8ca
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639130"
---
# <a name="using-drillthrough-on-structure-data-basic-data-mining-tutorial"></a><span data-ttu-id="43db3-102">구조 데이터에 드릴스루 사용(기본 데이터 마이닝 자습서)</span><span class="sxs-lookup"><span data-stu-id="43db3-102">Using Drillthrough on Structure Data (Basic Data Mining Tutorial)</span></span>
  <span data-ttu-id="43db3-103">광고 캠페인의 일환으로 [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] 는 34-40 시대의 인구 통계에서 잠재 고객에 게 메일을 보내는 중입니다.</span><span class="sxs-lookup"><span data-stu-id="43db3-103">As part of their advertising campaign, [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] is sending a mailer to potential customers in the 34-40 age demographic.</span></span> <span data-ttu-id="43db3-104">마케팅 부서에서는 5년 전에 [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] 에서 자전거를 구매한 고객에게도 메일러를 보내려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="43db3-104">The marketing department has decided that they would also like to send the mailer to the customers who purchased bikes from [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] more than five years ago.</span></span> <span data-ttu-id="43db3-105">이 단원에서는 오래 전에 자전거를 구매한 고객을 식별하고 그들의 연락처 정보를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="43db3-105">In this lesson you will identify customers with older bikes and retrieve their contact information.</span></span> <span data-ttu-id="43db3-106">이 정보는 모델에 포함되어 있지 않지만 구조에는 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="43db3-106">This information is not included in the model, but is included in the structure.</span></span> <span data-ttu-id="43db3-107">연락처 정보를 검색하려면 먼저 구조에 대해 드릴스루를 사용할 수 있는지 확인한 다음 드릴스루를 사용하여 대상 고객의 이름과 주소를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="43db3-107">To retrieve the contact information you will first ensure that drillthrough is enabled for the structure and then you will use drillthrough to reveal the names and addresses of the targeted customers.</span></span>  
  
### <a name="to-enable-drillthrough-on-a-mining-model"></a><span data-ttu-id="43db3-108">마이닝 모델에서 드릴스루를 사용하려면</span><span class="sxs-lookup"><span data-stu-id="43db3-108">To enable drillthrough on a mining model</span></span>  
  
1.  <span data-ttu-id="43db3-109">에서 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 데이터 마이닝 디자이너의 **마이닝 모델** 탭에 있는 **TM_Decision_Tree** 모델을 마우스 오른쪽 단추로 클릭 하 고 **속성**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="43db3-109">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], on the **Mining Models** tab of Data Mining Designer, right-click the **TM_Decision_Tree** model, and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="43db3-110">속성 창에서 **AllowDrillthrough**를 클릭하고 **True**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="43db3-110">In the Properties windows, click **AllowDrillthrough**, and select **True**.</span></span>  
  
3.  <span data-ttu-id="43db3-111">마이닝 모델 탭에서 모델을 마우스 오른쪽 단추로 클릭하고 **모델 처리**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="43db3-111">In the Mining Models tab, right-click the model, and select **Process Model**.</span></span>  
  
 <span data-ttu-id="43db3-112">자세한 내용은 [드릴스루 쿼리 &#40;데이터 마이닝](../../2014/analysis-services/data-mining/drillthrough-queries-data-mining.md) 을 참조 하세요&#41;</span><span class="sxs-lookup"><span data-stu-id="43db3-112">For more information, see [Drillthrough Queries &#40;Data Mining&#41;](../../2014/analysis-services/data-mining/drillthrough-queries-data-mining.md)</span></span>  
  
### <a name="to-view-drillthrough-data-from-a-mining-model"></a><span data-ttu-id="43db3-113">마이닝 모델에서 드릴스루 데이터를 보려면</span><span class="sxs-lookup"><span data-stu-id="43db3-113">To view drillthrough data from a mining model</span></span>  
  
1.  <span data-ttu-id="43db3-114">데이터 마이닝 디자이너에서 **마이닝 모델 뷰어** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="43db3-114">In Data Mining Designer, click the **Mining Model Viewer** tab.</span></span>  
  
2.  <span data-ttu-id="43db3-115">**마이닝 모델** 목록에서 **TM_Decision_Tree** 모델을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="43db3-115">Select the **TM_Decision_Tree** model from the **Mining Model** list.</span></span>  
  
3.  <span data-ttu-id="43db3-116">**배경** 값을로 변경 `1` 합니다.</span><span class="sxs-lookup"><span data-stu-id="43db3-116">Change the **Background** value to `1`.</span></span> <span data-ttu-id="43db3-117">이렇게 하면 모델 중에서 자전거를 구매한 고객과 관련된 부분만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="43db3-117">By doing this, you show only the part of the model that is related to customer who bought bikes.</span></span>  
  
4.  <span data-ttu-id="43db3-118">**뷰어** 목록에서 Microsoft 트리 뷰어를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="43db3-118">Select the Microsoft Tree viewer from the **Viewer** list.</span></span> <span data-ttu-id="43db3-119">그러면 뷰어가 새 필터 조건으로 새로 고쳐집니다.</span><span class="sxs-lookup"><span data-stu-id="43db3-119">This will force the viewer to refresh with the new filter conditions.</span></span> <span data-ttu-id="43db3-120">그런 다음 **Age >= 34 및 <41** 노드를 찾아 해당 노드를 마우스 오른쪽 단추로 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="43db3-120">Then, locate the **Age >=34 and <41** node and right-click the node.</span></span>  
  
5.  <span data-ttu-id="43db3-121">**드릴스루**를 선택한 다음 **모델 및 구조 열** 을 선택하여 **드릴스루** 창을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="43db3-121">Select **Drill Through**, and then select **Model and Structure Columns** to open the **Drill Through** window.</span></span>  
  
6.  <span data-ttu-id="43db3-122">**Structure.Date First Purchase** 열로 스크롤하여 오래 전에 구매한 자전거에 대한 구매 날짜를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="43db3-122">Scroll to the **Structure.Date First Purchase** column to view the purchase dates for the older bikes.</span></span>  
  
7.  <span data-ttu-id="43db3-123">데이터를 클립보드에 복사하려면 테이블에서 임의의 행을 마우스 오른쪽 단추로 클릭하고 **모두 복사**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="43db3-123">To copy the data to the Clipboard, right-click any row in the table, and select **Copy All**.</span></span>  
  
 <span data-ttu-id="43db3-124">축하합니다. 기본 데이터 마이닝 자습서를 완료했습니다.</span><span class="sxs-lookup"><span data-stu-id="43db3-124">Congratulations, you have completed the basic data mining tutorial.</span></span> <span data-ttu-id="43db3-125">이제 데이터 마이닝 도구를 능숙하게 사용할 수 있게 되었으므로 예측, 시장 바구니 분석 및 시퀀스 클러스터링에 대한 모델을 만드는 방법을 보여 주는 중급 데이터 마이닝 자습서도 완료하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="43db3-125">Now that you are comfortable using the data mining tools, we recommend that you also complete the intermediate data mining tutorial, which demonstrates how to create models for forecasting, market basket analysis, and sequence clustering.</span></span>  
  
## <a name="previous-task-in-lesson"></a><span data-ttu-id="43db3-126">단원의 이전 태스크</span><span class="sxs-lookup"><span data-stu-id="43db3-126">Previous Task in Lesson</span></span>  
 [<span data-ttu-id="43db3-127">예측 만들기&#40;기본 데이터 마이닝 자습서&#41;</span><span class="sxs-lookup"><span data-stu-id="43db3-127">Creating Predictions &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/creating-predictions-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a><span data-ttu-id="43db3-128">참고 항목</span><span class="sxs-lookup"><span data-stu-id="43db3-128">See Also</span></span>  
 [<span data-ttu-id="43db3-129">예측 쿼리 작성기를 사용하여 예측 쿼리 만들기</span><span class="sxs-lookup"><span data-stu-id="43db3-129">Create a Prediction Query Using the Prediction Query Builder</span></span>](../../2014/analysis-services/data-mining/create-a-prediction-query-using-the-prediction-query-builder.md)  
  
  
