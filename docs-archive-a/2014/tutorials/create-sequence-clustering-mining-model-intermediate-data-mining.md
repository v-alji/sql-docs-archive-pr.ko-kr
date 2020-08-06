---
title: 시퀀스 클러스터링 마이닝 모델 구조 만들기 (중급 데이터 마이닝 자습서) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: e9339227-6c2e-4c4b-8be2-8c1960bc4a8d
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 37d0a1738a758a9d8c4fd6b80310037937a9803f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649289"
---
# <a name="creating-a-sequence-clustering-mining-model-structure-intermediate-data-mining-tutorial"></a><span data-ttu-id="c0b76-102">시퀀스 클러스터링 마이닝 모델 구조 만들기(중급 데이터 마이닝 자습서)</span><span class="sxs-lookup"><span data-stu-id="c0b76-102">Creating a Sequence Clustering Mining Model Structure (Intermediate Data Mining Tutorial)</span></span>
  <span data-ttu-id="c0b76-103">시퀀스 클러스터링 마이닝 모델을 만드는 첫 번째 단계는 데이터 마이닝 마법사를 사용하여 [!INCLUDE[msCoName](../includes/msconame-md.md)] 시퀀스 클러스터링 알고리즘을 기반으로 하는 새 마이닝 구조 및 마이닝 모델을 만드는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="c0b76-103">The first step in creating a sequence clustering mining model is to use the Data Mining Wizard to create a new mining structure and a mining model based on the [!INCLUDE[msCoName](../includes/msconame-md.md)] Sequence Clustering algorithm.</span></span>  
  
 <span data-ttu-id="c0b76-104">시장 바구니 분석에 사용된 동일한 데이터 원본 뷰를 사용하지만 `sequence` 식별자가 포함되어 있는 열을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="c0b76-104">You will use the same data source view that you used for the market basket analysis, but you will add a column that contains the `sequence` identifier.</span></span> <span data-ttu-id="c0b76-105">이 시나리오에서 시퀀스는 고객이 시장 바구니에 항목을 추가한 순서를 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="c0b76-105">In this scenario, the sequence means the order in which the customer added items to the shopping basket.</span></span>  
  
 <span data-ttu-id="c0b76-106">또한 고객을 인구 통계별로 그룹화하는 모델 중 하나에 사용되는 일부 열을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="c0b76-106">You will also add some columns that are used in one of the models to group customers by demographics.</span></span>  
  
### <a name="to-create-a-sequence-clustering-structure-and-model"></a><span data-ttu-id="c0b76-107">시퀀스 클러스터링 구조 및 모델을 만들려면</span><span class="sxs-lookup"><span data-stu-id="c0b76-107">To create a sequence clustering structure and model</span></span>  
  
1.  <span data-ttu-id="c0b76-108">의 솔루션 탐색기에서 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] **마이닝 구조** 를 마우스 오른쪽 단추로 클릭 하 고 **새 마이닝 구조**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0b76-108">In Solution Explorer in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], right-click **Mining Structures** and select **New Mining Structure**.</span></span>  
  
2.  <span data-ttu-id="c0b76-109">**데이터 마이닝 마법사 시작** 페이지에서 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c0b76-109">On the **Welcome to the Data Mining Wizard** page, click **Next**.</span></span>  
  
3.  <span data-ttu-id="c0b76-110">**정의 방법 선택** 페이지에서 **기존 관계형 데이터베이스 또는 데이터 웨어하우스** 를 선택 했는지 확인 하 고 **다음**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0b76-110">On the **Select the Definition Method** page, verify that **From existing relational database or data warehouse** is selected, and then click **Next**.</span></span>  
  
4.  <span data-ttu-id="c0b76-111">**데이터 마이닝 구조 만들기** 페이지에서 **마이닝 모델을 사용 하 여 마이닝 구조 만들기** 옵션이 선택 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0b76-111">On the **Create the Data Mining Structure** page, verify that the option **Create mining structure with a mining model** is selected.</span></span> <span data-ttu-id="c0b76-112">그런 다음 **사용 하려는 데이터 마이닝 기술**옵션의 드롭다운 목록을 클릭 하 고 **Microsoft 시퀀스 클러스터링**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0b76-112">Next, click the dropdown list for the option, **Which data mining technique do you want to use?**, and select **Microsoft Sequence Clustering**.</span></span> <span data-ttu-id="c0b76-113">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c0b76-113">Click **Next**.</span></span>  
  
     <span data-ttu-id="c0b76-114">**데이터 원본 뷰 선택** 페이지가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="c0b76-114">The **Select Data Source View** page appears.</span></span> <span data-ttu-id="c0b76-115">**사용 가능한 데이터 원본 뷰**에서을 선택 `Orders` 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0b76-115">Under **Available data source views**, select `Orders`.</span></span>  
  
     <span data-ttu-id="c0b76-116">Orders는 시장 바구니 시나리오에 사용한 동일한 데이터 원본 뷰입니다.</span><span class="sxs-lookup"><span data-stu-id="c0b76-116">Orders is the same data source view that you used for the market basket scenario.</span></span> <span data-ttu-id="c0b76-117">이 데이터 원본 뷰를 만들지 않은 경우 [중첩 테이블을 사용 하 여 데이터 원본 뷰 추가 &#40;중급 데이터 마이닝 자습서&#41;](../../2014/tutorials/adding-a-data-source-view-with-nested-tables-intermediate-data-mining-tutorial.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="c0b76-117">If you have not created this data source view, see [Adding a Data Source View with Nested Tables &#40;Intermediate Data Mining Tutorial&#41;](../../2014/tutorials/adding-a-data-source-view-with-nested-tables-intermediate-data-mining-tutorial.md).</span></span>  
  
5.  <span data-ttu-id="c0b76-118">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c0b76-118">Click **Next**.</span></span>  
  
6.  <span data-ttu-id="c0b76-119">**테이블 유형 지정** 페이지에서 **vAssocSeqOrders** 테이블 옆의 **사례** 확인란을 선택 하 고 **vAssocSeqLineItems** 테이블 옆의 **중첩** 된 확인란을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0b76-119">On the **Specify Table Types** page, select the **Case** check box next to the **vAssocSeqOrders** table, and select the **Nested** check box next to the **vAssocSeqLineItems** table.</span></span> <span data-ttu-id="c0b76-120">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c0b76-120">Click **Next**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="c0b76-121">**사례** 또는 **중첩** 된 확인란을 선택할 때 오류가 발생 하는 경우 데이터 원본 뷰의 조인이 올바르지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c0b76-121">If an error occurs when you select the **Case** or **Nested** check boxes, it may be that the join in the data source view is not correct.</span></span> <span data-ttu-id="c0b76-122">중첩 테이블 **vAssocSeqLineItems**는 다 대 일 조인으로 사례 테이블 **vAssocSeqOrders** 에 연결 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0b76-122">The nested table, **vAssocSeqLineItems**, must be connected to the case table, **vAssocSeqOrders,** by a many-to-one join.</span></span> <span data-ttu-id="c0b76-123">조인 선을 마우스 오른쪽 단추로 클릭한 다음 조인 방향을 반대로 바꿔 관계를 편집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c0b76-123">You can edit the relationship by right-clicking on the join line and then reversing the direction of the join.</span></span> <span data-ttu-id="c0b76-124">자세한 내용은 [Analysis Services-다차원 데이터&#41;&#40;관계 만들기 또는 편집 대화 상자 ](../../2014/analysis-services/create-or-edit-relationship-dialog-box-analysis-services-multidimensional-data.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="c0b76-124">For more information, see [Create or Edit Relationship Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](../../2014/analysis-services/create-or-edit-relationship-dialog-box-analysis-services-multidimensional-data.md).</span></span>  
  
7.  <span data-ttu-id="c0b76-125">**학습 데이터 지정** 페이지에서 다음과 같이 확인란을 선택 하 여 모델에서 사용할 열을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0b76-125">On the **Specify the Training Data** page, choose the columns for use in the model by selecting a check box as follows:</span></span>  
  
    -   <span data-ttu-id="c0b76-126">**IncomeGroup** **입력** 확인란을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0b76-126">**IncomeGroup** Select the **Input** check box.</span></span>  
  
         <span data-ttu-id="c0b76-127">이 열에는 클러스터링에 사용할 수 있는 고객에 대한 유용한 정보가 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c0b76-127">This column contains interesting information about the customers that you can use for clustering.</span></span> <span data-ttu-id="c0b76-128">첫 번째 모델에서 이 열을 사용한 다음 두 번째 모델에서 무시합니다.</span><span class="sxs-lookup"><span data-stu-id="c0b76-128">You will use it in the first model and then ignore it in the second model.</span></span>  
  
    -   <span data-ttu-id="c0b76-129">**Ordernumber** 확인란을 선택 `Key` 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0b76-129">**OrderNumber** Select the `Key` check box.</span></span>  
  
         <span data-ttu-id="c0b76-130">이 필드는 사례 테이블에 대한 식별자인 `Key`로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="c0b76-130">This field will be used as the identifier for the case table, or `Key`.</span></span> <span data-ttu-id="c0b76-131">일반적으로 키에 클러스터링에 유용하지 않은 고유 값이 포함되어 있으므로 사례 테이블의 키 필드를 입력으로 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c0b76-131">In general, you should never use the key field of the case table as an input, because the key contains unique values that are not useful for clustering.</span></span>  
  
    -   <span data-ttu-id="c0b76-132">**영역** **입력** 확인란을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0b76-132">**Region** Select the **Input** check box.</span></span>  
  
         <span data-ttu-id="c0b76-133">이 열에는 클러스터링에 사용할 수 있는 고객에 대한 유용한 정보가 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c0b76-133">This column contains interesting information about the customers that you can use for clustering.</span></span> <span data-ttu-id="c0b76-134">첫 번째 모델에서 이 열을 사용한 다음 두 번째 모델에서 무시합니다.</span><span class="sxs-lookup"><span data-stu-id="c0b76-134">You will use it in the first model and then ignore it in the second model.</span></span>  
  
    -   <span data-ttu-id="c0b76-135">**LineNumber** `Key`및 **입력** 확인란을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0b76-135">**LineNumber** Select the `Key` and **Input** check boxes.</span></span>  
  
         <span data-ttu-id="c0b76-136">**LineNumber** 필드는 중첩 테이블에 대 한 식별자로 사용 됩니다 `Sequence Key` .</span><span class="sxs-lookup"><span data-stu-id="c0b76-136">The **LineNumber** field will be used as the identifier for the nested table, or `Sequence Key`.</span></span> <span data-ttu-id="c0b76-137">중첩 테이블의 키는 항상 입력으로 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0b76-137">The key for a nested table must always be used for input.</span></span>  
  
    -   <span data-ttu-id="c0b76-138">**모델** **입력** 및 **예측** 가능 확인란을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0b76-138">**Model** Select the **Input** and **Predictable** check boxes.</span></span>  
  
     <span data-ttu-id="c0b76-139">선택 항목이 올바른지 확인 하 고 **다음**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0b76-139">Verify that the selections are correct, and then click **Next**.</span></span>  
  
8.  <span data-ttu-id="c0b76-140">**열 내용 및 데이터 형식 지정** 페이지에서 표에 다음 표에 표시 된 열, 내용 유형 및 데이터 형식이 포함 되어 있는지 확인 하 **고 다음을 클릭 합니다**.</span><span class="sxs-lookup"><span data-stu-id="c0b76-140">On the **Specify Columns' Content and Data Type** page, verify that the grid contains the columns, content types, and data types shown in the following table, and then click **Next**.</span></span>  
  
    |<span data-ttu-id="c0b76-141">테이블/열</span><span class="sxs-lookup"><span data-stu-id="c0b76-141">Tables/Columns</span></span>|<span data-ttu-id="c0b76-142">콘텐츠 유형</span><span class="sxs-lookup"><span data-stu-id="c0b76-142">Content Type</span></span>|<span data-ttu-id="c0b76-143">데이터 형식</span><span class="sxs-lookup"><span data-stu-id="c0b76-143">Data Type</span></span>|  
    |---------------------|------------------|---------------|  
    |<span data-ttu-id="c0b76-144">IncomeGroup</span><span class="sxs-lookup"><span data-stu-id="c0b76-144">IncomeGroup</span></span>|<span data-ttu-id="c0b76-145">불연속</span><span class="sxs-lookup"><span data-stu-id="c0b76-145">Discrete</span></span>|<span data-ttu-id="c0b76-146">텍스트</span><span class="sxs-lookup"><span data-stu-id="c0b76-146">Text</span></span>|  
    |<span data-ttu-id="c0b76-147">OrderNumber</span><span class="sxs-lookup"><span data-stu-id="c0b76-147">OrderNumber</span></span>|<span data-ttu-id="c0b76-148">키</span><span class="sxs-lookup"><span data-stu-id="c0b76-148">Key</span></span>|<span data-ttu-id="c0b76-149">텍스트</span><span class="sxs-lookup"><span data-stu-id="c0b76-149">Text</span></span>|  
    |<span data-ttu-id="c0b76-150">지역</span><span class="sxs-lookup"><span data-stu-id="c0b76-150">Region</span></span>|<span data-ttu-id="c0b76-151">불연속</span><span class="sxs-lookup"><span data-stu-id="c0b76-151">Discrete</span></span>|<span data-ttu-id="c0b76-152">텍스트</span><span class="sxs-lookup"><span data-stu-id="c0b76-152">Text</span></span>|  
    |<span data-ttu-id="c0b76-153">vAssocSeqLineItems</span><span class="sxs-lookup"><span data-stu-id="c0b76-153">vAssocSeqLineItems</span></span>|||  
    |<span data-ttu-id="c0b76-154">Line Number</span><span class="sxs-lookup"><span data-stu-id="c0b76-154">Line Number</span></span>|<span data-ttu-id="c0b76-155">키 시퀀스</span><span class="sxs-lookup"><span data-stu-id="c0b76-155">Key Sequence</span></span>|<span data-ttu-id="c0b76-156">Long</span><span class="sxs-lookup"><span data-stu-id="c0b76-156">Long</span></span>|  
    |<span data-ttu-id="c0b76-157">모델</span><span class="sxs-lookup"><span data-stu-id="c0b76-157">Model</span></span>|<span data-ttu-id="c0b76-158">불연속</span><span class="sxs-lookup"><span data-stu-id="c0b76-158">Discrete</span></span>|<span data-ttu-id="c0b76-159">텍스트</span><span class="sxs-lookup"><span data-stu-id="c0b76-159">Text</span></span>|  
  
9. <span data-ttu-id="c0b76-160">**테스트 집합 만들기** 페이지에서 **테스트에 사용할 데이터의 백분율** 을 20으로 변경 하 고 **다음**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0b76-160">On the **Create Testing Set** page, change the **Percentage of data for testing** to 20, and then click **Next**.</span></span>  
  
10. <span data-ttu-id="c0b76-161">**마법사 완료** 페이지에서 **마이닝 구조 이름**에을 입력 `Sequence Clustering with Region` 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0b76-161">On the **Completing the Wizard** page, for the **Mining structure name**, type `Sequence Clustering with Region`.</span></span>  
  
11. <span data-ttu-id="c0b76-162">**마이닝 모델 이름**에을 입력 `Sequence Clustering with Region` 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0b76-162">For the **Mining model name**, type `Sequence Clustering with Region`.</span></span>  
  
12. <span data-ttu-id="c0b76-163">**드릴스루 허용** 상자를 선택 하 고 **마침**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0b76-163">Check the **Allow drill through** box, and then click **Finish**.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="c0b76-164">단원의 다음 태스크</span><span class="sxs-lookup"><span data-stu-id="c0b76-164">Next Task in Lesson</span></span>  
 [<span data-ttu-id="c0b76-165">시퀀스 클러스터링 모델 처리</span><span class="sxs-lookup"><span data-stu-id="c0b76-165">Processing the Sequence Clustering Model</span></span>](../../2014/tutorials/processing-the-sequence-clustering-model.md)  
  
## <a name="see-also"></a><span data-ttu-id="c0b76-166">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c0b76-166">See Also</span></span>  
 <span data-ttu-id="c0b76-167">[데이터 마이닝 디자이너](../../2014/analysis-services/data-mining/data-mining-designer.md) </span><span class="sxs-lookup"><span data-stu-id="c0b76-167">[Data Mining Designer](../../2014/analysis-services/data-mining/data-mining-designer.md) </span></span>  
 [<span data-ttu-id="c0b76-168">Microsoft 시퀀스 클러스터링 알고리즘</span><span class="sxs-lookup"><span data-stu-id="c0b76-168">Microsoft Sequence Clustering Algorithm</span></span>](../../2014/analysis-services/data-mining/microsoft-sequence-clustering-algorithm.md)  
  
  
