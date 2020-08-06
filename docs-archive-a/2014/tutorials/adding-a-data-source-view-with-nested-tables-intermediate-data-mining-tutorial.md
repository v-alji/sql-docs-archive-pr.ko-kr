---
title: 중첩 테이블이 있는 데이터 원본 뷰 추가 (중급 데이터 마이닝 자습서) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: a14cd7f1-7a10-4ec6-af6a-f5f0676a0308
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: da1a9bff093e0b59e9d1166554d95bcf61aded08
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87735675"
---
# <a name="adding-a-data-source-view-with-nested-tables-intermediate-data-mining-tutorial"></a><span data-ttu-id="e0296-102">중첩 테이블이 있는 데이터 원본 뷰 추가(중급 데이터 마이닝 자습서)</span><span class="sxs-lookup"><span data-stu-id="e0296-102">Adding a Data Source View with Nested Tables (Intermediate Data Mining Tutorial)</span></span>
  <span data-ttu-id="e0296-103">시장 바구니 모델을 만들려면 연관 데이터를 지원하는 데이터 원본 뷰를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0296-103">To create a market basket model, you must use a data source view that supports associative data.</span></span> <span data-ttu-id="e0296-104">이 데이터 원본 뷰는 시퀀스 클러스터링 시나리오에도 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="e0296-104">This data source view will also be used for the sequence clustering scenario.</span></span>  
  
 <span data-ttu-id="e0296-105">이 데이터 원본 뷰는 *중첩 테이블*을 포함 하기 때문에 사용 된 것과 다른 다른 데이터 원본 뷰를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0296-105">This data source view is different from others that you may have worked with because it contains a *nested table*.</span></span> <span data-ttu-id="e0296-106">*중첩 테이블* 은 사례 테이블의 단일 행에 대 한 여러 행의 정보를 포함 하는 테이블입니다.</span><span class="sxs-lookup"><span data-stu-id="e0296-106">A *nested table* is a table that contains multiple rows of information about a single row in the case table.</span></span> <span data-ttu-id="e0296-107">예를 들어 모델에서 고객의 구매 동작을 분석하는 경우 일반적으로 각 고객에 대한 고유 행이 있는 테이블을 사례 테이블로 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="e0296-107">For example, if your model analyzes the purchasing behavior of customers, you would typically use a table that has a unique row for each customer as the case table.</span></span> <span data-ttu-id="e0296-108">그러나 각 고객이 여러 제품을 구매할 수 있으며 이 경우 구매 순서 또는 함께 구매되는 빈도가 높은 제품을 분석할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0296-108">However, each customer might make multiple purchases, and you might want to analyze the sequence of purchases, or products that are frequently purchased together.</span></span> <span data-ttu-id="e0296-109">모델에서 이러한 구매를 논리적으로 나타내려면 각 고객에 대한 구매를 나열하는 데이터 원본 뷰에 다른 테이블을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="e0296-109">To logically represent these purchases in your model, you add another table to the data source view that lists the purchases for each customer.</span></span>  
  
 <span data-ttu-id="e0296-110">이 중첩 구매 테이블은 고객 테이블과 다 대 일 관계로 관련됩니다.</span><span class="sxs-lookup"><span data-stu-id="e0296-110">This nested purchases table is related to the customer table by a many-to-one relationship.</span></span> <span data-ttu-id="e0296-111">중첩 테이블에 각 고객에 대한 행이 많이 포함될 수 있습니다. 구매한 단일 제품을 포함하는 각 행에는 구매가 이루어진 주문, 주문 시 가격 또는 해당 제품에 대해 수행된 모든 홍보에 대한 추가 정보가 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0296-111">The nested table might contain many rows for each customer, each row containing a single product that was purchased, perhaps with additional information about the order that the purchases were made, the price at the time of the order, or any promotions that applied.</span></span> <span data-ttu-id="e0296-112">중첩 테이블에 있는 정보를 모델에 대한 입력 또는 예측 가능한 특성으로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0296-112">You can use the information in the nested table as inputs to the model, or as the predictable attribute.</span></span>  
  
 <span data-ttu-id="e0296-113">이 단원에서는 다음 태스크를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="e0296-113">In this lesson, you do the following tasks:</span></span>  
  
-   <span data-ttu-id="e0296-114">데이터 원본에 데이터 원본 뷰를 추가 [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)] 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0296-114">You add a data source view to the [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)] data source.</span></span>  
  
-   <span data-ttu-id="e0296-115">사례 및 중첩 테이블을 이 뷰에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="e0296-115">You add the case and nested tables to this view.</span></span>  
  
-   <span data-ttu-id="e0296-116">사례 및 중첩 테이블 간에 다 대 일 관계를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e0296-116">You specify the many-to-one relationship between the case and nested table.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="e0296-117">.</span><span class="sxs-lookup"><span data-stu-id="e0296-117">.</span></span> <span data-ttu-id="e0296-118">사례 테이블과 중첩 테이블 간의 관계를 올바르게 지정하고 모델을 처리할 때 오류를 피하려면 설명된 절차를 정확하게 따르는 것이 중요합니다.</span><span class="sxs-lookup"><span data-stu-id="e0296-118">It is important that you follow the described procedure exactly, to correctly specify the relationship between the case table and the nested table and to avoid errors when you process the model.</span></span>  
  
-   <span data-ttu-id="e0296-119">모델에서 데이터 열이 사용되는 방법을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="e0296-119">You define how the columns of data are used in the model.</span></span>  
  
 <span data-ttu-id="e0296-120">사례 및 중첩 테이블 작업에 대 한 자세한 내용 및 중첩 테이블 키를 선택 하는 방법에 대 한 자세한 내용은 [중첩 테이블 &#40;Analysis Services-데이터 마이닝&#41;](../../2014/analysis-services/data-mining/nested-tables-analysis-services-data-mining.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="e0296-120">For more information about working with case and nested tables, and how to choose a nested table key, see [Nested Tables &#40;Analysis Services - Data Mining&#41;](../../2014/analysis-services/data-mining/nested-tables-analysis-services-data-mining.md).</span></span>  
  
### <a name="to-add-a-data-source-view"></a><span data-ttu-id="e0296-121">데이터 원본 뷰를 추가하려면</span><span class="sxs-lookup"><span data-stu-id="e0296-121">To add a data source view</span></span>  
  
1.  <span data-ttu-id="e0296-122">솔루션 탐색기에서 **데이터 원본 뷰**를 마우스 오른쪽 단추로 클릭 한 다음 **새 데이터 원본 뷰**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0296-122">In Solution Explorer, right-click **Data Source Views**, and then select **New Data Source View**.</span></span>  
  
     <span data-ttu-id="e0296-123">데이터 원본 뷰 마법사가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="e0296-123">The Data Source View Wizard opens.</span></span>  
  
2.  <span data-ttu-id="e0296-124">**데이터 원본 뷰 마법사 시작** 페이지에서 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e0296-124">On the **Welcome to the Data Source View Wizard** page, click **Next**.</span></span>  
  
3.  <span data-ttu-id="e0296-125">**데이터 원본 선택** 페이지의 **관계형 데이터 원본**아래에서 [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)] 기본 데이터 마이닝 자습서에서 만든 데이터 원본을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0296-125">On the **Select a Data Source** page, under **Relational data sources**, select the [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)] data source that you created in the Basic Data Mining Tutorial.</span></span> <span data-ttu-id="e0296-126">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e0296-126">Click **Next**.</span></span>  
  
4.  <span data-ttu-id="e0296-127">**테이블 및 뷰 선택** 페이지에서 다음 테이블을 선택 하 고 오른쪽 화살표를 클릭 하 여 새 데이터 원본 뷰에 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0296-127">On the **Select Tables and Views** page, select the following tables, and then click the right arrow to include them in the new data source view:</span></span>  
  
    -   `vAssocSeqOrders`  
  
    -   `vAssocSeqLineItems`  
  
5.  <span data-ttu-id="e0296-128">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e0296-128">Click **Next**.</span></span>  
  
6.  <span data-ttu-id="e0296-129">**마법사 완료** 페이지에서는 기본적으로 데이터 원본 뷰의 이름이로 지정 됩니다 [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="e0296-129">On the **Completing the Wizard** page, by default the data source view is named [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)].</span></span> <span data-ttu-id="e0296-130">이름을로 변경 하 `Orders` 고 **마침**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0296-130">Change the name to `Orders`, and then click **Finish**.</span></span>  
  
     <span data-ttu-id="e0296-131">데이터 원본 뷰 디자이너가 열리고 `Orders` 데이터 원본 뷰가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="e0296-131">Data Source View Designer opens and the `Orders` data source view appears.</span></span>  
  
### <a name="to-create-a-relationship-between-tables"></a><span data-ttu-id="e0296-132">테이블 간에 관계를 만들려면</span><span class="sxs-lookup"><span data-stu-id="e0296-132">To create a relationship between tables</span></span>  
  
1.  <span data-ttu-id="e0296-133">데이터 원본 뷰 디자이너에서 테이블이 가로로 정렬되어 왼쪽에는 vAssocSeqLineItems 테이블이, 오른쪽에는 vAssocSeqOrders 테이블이 있도록 두 테이블을 배치합니다.</span><span class="sxs-lookup"><span data-stu-id="e0296-133">In Data Source View Designer, position the two tables so that the tables are aligned horizontally, with the vAssocSeqLineItems table on the left side and the vAssocSeqOrders table on the right side.</span></span>  
  
2.  <span data-ttu-id="e0296-134">VAssocSeqLineItems 테이블에서 **Ordernumber** 열을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0296-134">Select the **OrderNumber** column in the vAssocSeqLineItems table.</span></span>  
  
3.  <span data-ttu-id="e0296-135">열을 vAssocSeqOrders 테이블로 끌어 **Ordernumber** 열에 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="e0296-135">Drag the column to the vAssocSeqOrders table, and put it on the **OrderNumber** column.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="e0296-136">조인의 다를 나타내는 vAssocSeqLineItems 중첩 테이블에서 **Ordernumber** 열을 조인의 한 쪽을 나타내는 vAssocSeqOrders case 테이블로 끌어 놓습니다 (이 경우).</span><span class="sxs-lookup"><span data-stu-id="e0296-136">Make sure to drag the **OrderNumber** column from the vAssocSeqLineItems nested table, which represents the many side of the join, to the vAssocSeqOrders case table, which represents the one side of the join.</span></span>  
  
     <span data-ttu-id="e0296-137">이제 vAssocSeqLineItems 테이블과 vAssocSeqOrders 테이블 간에 새로운 *다대일 관계가* 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0296-137">A new *many-to-one relationship* now exists between the vAssocSeqLineItems and vAssocSeqOrders tables.</span></span> <span data-ttu-id="e0296-138">테이블을 올바르게 조인한 경우 데이터 원본 뷰는 다음과 같아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0296-138">If you have joined the tables correctly, the data source view should appear as follows:</span></span>  
  
     <span data-ttu-id="e0296-139">![중첩 테이블과 사례 테이블에 대 한 다대일 조인이 필요 합니다.](../../2014/tutorials/media/dsv-nestedjoin-illustration.gif "중첩 테이블과 사례 테이블에 대 한 다대일 조인이 필요 합니다.")</span><span class="sxs-lookup"><span data-stu-id="e0296-139">![expected many-to-one join on nested and case table](../../2014/tutorials/media/dsv-nestedjoin-illustration.gif "expected many-to-one join on nested and case table")</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="e0296-140">단원의 다음 태스크</span><span class="sxs-lookup"><span data-stu-id="e0296-140">Next Task in Lesson</span></span>  
 [<span data-ttu-id="e0296-141">&#40;중급 데이터 마이닝 자습서&#41;시장 바구니 구조 및 모델 만들기</span><span class="sxs-lookup"><span data-stu-id="e0296-141">Creating a Market Basket Structure and Model &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/creating-a-market-basket-structure-and-model-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a><span data-ttu-id="e0296-142">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e0296-142">See Also</span></span>  
 <span data-ttu-id="e0296-143">[Analysis Services 데이터 마이닝&#41;&#40;중급 데이터 마이닝 자습서](../../2014/tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="e0296-143">[Intermediate Data Mining Tutorial &#40;Analysis Services - Data Mining&#41;](../../2014/tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="e0296-144">[마이닝 구조 &#40;Analysis Services 데이터 마이닝&#41;](../../2014/analysis-services/data-mining/mining-structures-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="e0296-144">[Mining Structures &#40;Analysis Services - Data Mining&#41;](../../2014/analysis-services/data-mining/mining-structures-analysis-services-data-mining.md) </span></span>  
 [<span data-ttu-id="e0296-145">마이닝 모델&#40;Analysis Services - 데이터 마이닝&#41;</span><span class="sxs-lookup"><span data-stu-id="e0296-145">Mining Models &#40;Analysis Services - Data Mining&#41;</span></span>](../../2014/analysis-services/data-mining/mining-models-analysis-services-data-mining.md)  
  
  
