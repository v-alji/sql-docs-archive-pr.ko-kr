---
title: 시장 바구니 구조 및 모델 만들기 (중급 데이터 마이닝 자습서) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 659b7a4e-f687-44d9-a60a-86490ccbf90f
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: b276fe5bed1d9df8e8b2e3e2826966b6abfb734e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639189"
---
# <a name="creating-a-market-basket-structure-and-model-intermediate-data-mining-tutorial"></a><span data-ttu-id="1f8c4-102">시장 바구니 구조 및 모델 만들기(중급 데이터 마이닝 자습서)</span><span class="sxs-lookup"><span data-stu-id="1f8c4-102">Creating a Market Basket Structure and Model (Intermediate Data Mining Tutorial)</span></span>
  <span data-ttu-id="1f8c4-103">데이터 원본 뷰를 만들었으므로 이제 데이터 마이닝 마법사를 사용하여 새 마이닝 구조를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="1f8c4-103">Now that you have created a data source view, you will use the Data Mining Wizard to create a new mining structure.</span></span> <span data-ttu-id="1f8c4-104">이 태스크에서는 [!INCLUDE[msCoName](../includes/msconame-md.md)] 연결 알고리즘을 기반으로 하는 마이닝 구조 및 마이닝 모델을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="1f8c4-104">In this task, you will create a mining structure and a mining model that is based on the [!INCLUDE[msCoName](../includes/msconame-md.md)] Association algorithm.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1f8c4-105">vAssocSeqLineItems를 중첩 테이블로 사용할 수 없다는 오류가 발생하면 이 단원의 이전 태스크로 돌아가 vAssocSeqLineItems 테이블(다측)에서 vAssocSeqOrders 테이블(일측)로 끄는 방법으로 다 대 일 조인을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f8c4-105">If you encounter an error stating that vAssocSeqLineItems cannot be used as a nested table, return to the previous task in the lesson, and be sure to create the many-to-one join by dragging from the vAssocSeqLineItems table (the many side) to the vAssocSeqOrders table (the one side).</span></span> <span data-ttu-id="1f8c4-106">조인 선을 마우스 오른쪽 단추로 클릭하여 테이블 간의 관계를 편집할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1f8c4-106">You can also edit the relationship between the tables by right-clicking the join line.</span></span>  
  
### <a name="to-create-an-association-mining-structure"></a><span data-ttu-id="1f8c4-107">연결 마이닝 구조를 만들려면</span><span class="sxs-lookup"><span data-stu-id="1f8c4-107">To create an association mining structure</span></span>  
  
1.  <span data-ttu-id="1f8c4-108">의 솔루션 탐색기에서 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] **마이닝 구조** 를 마우스 오른쪽 단추로 클릭 하 고 **새 마이닝 구조** 를 선택 하 여 데이터 마이닝 마법사를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="1f8c4-108">In Solution Explorer in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], right-click **Mining Structures** and select **New Mining Structure** to open the Data Mining Wizard.</span></span>  
  
2.  <span data-ttu-id="1f8c4-109">**데이터 마이닝 마법사 시작** 페이지에서 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1f8c4-109">On the **Welcome to the Data Mining Wizard** page, click **Next**.</span></span>  
  
3.  <span data-ttu-id="1f8c4-110">**정의 방법 선택** 페이지에서 **기존 관계형 데이터베이스 또는 데이터 웨어하우스** 를 선택 했는지 확인 하 고 **다음**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f8c4-110">On the **Select the Definition Method** page, verify that **From existing relational database or data warehouse** is selected, and then click **Next**.</span></span>  
  
4.  <span data-ttu-id="1f8c4-111">**데이터 마이닝 구조 만들기** 페이지에서 **사용할 데이터 마이닝 기법**을 선택 하 고 목록에서 **Microsoft 연결 규칙** 을 선택한 후 **다음**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f8c4-111">On the **Create the Data Mining Structure** page, under **Which data mining technique do you want to use?**, select **Microsoft Association Rules** from the list, and then click **Next**.</span></span> <span data-ttu-id="1f8c4-112">**데이터 원본 뷰 선택** 페이지가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="1f8c4-112">The **Select Data Source View** page appears.</span></span>  
  
5.  <span data-ttu-id="1f8c4-113">**사용 가능한 데이터 원본 뷰**에서 **Orders**를 선택 하 고 **다음**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f8c4-113">Select **Orders**under **Available data source views**, and then click **Next**.</span></span>  
  
6.  <span data-ttu-id="1f8c4-114">**테이블 유형 지정** 페이지의 vAssocSeqLineItems 테이블에 대 한 행에서 **중첩** 확인란을 선택 하 고 중첩 테이블 VAssocSeqOrders의 행에서 **사례** 확인란을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f8c4-114">On the **Specify Table Types** page, in the row for the vAssocSeqLineItems table, select the **Nested** check box, and in the row for the nested table vAssocSeqOrders, select the **Case** check box.</span></span> <span data-ttu-id="1f8c4-115">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1f8c4-115">Click **Next**.</span></span>  
  
7.  <span data-ttu-id="1f8c4-116">**학습 데이터 지정** 페이지에서 선택할 수 있는 모든 확인란의 선택을 취소 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f8c4-116">On the **Specify the Training Data** page, clear any boxes that might be checked.</span></span> <span data-ttu-id="1f8c4-117">OrderNumber 옆의 **키** 확인란을 선택 하 여 사례 테이블 vAssocSeqOrders의 키를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f8c4-117">Set the key for the case table, vAssocSeqOrders, by selecting the **Key** check box next to OrderNumber.</span></span>  
  
     <span data-ttu-id="1f8c4-118">시장 바구니 분석의 목적은 단일 트랜잭션에 포함 되는 제품을 확인 하는 것 이므로 **Customerkey** 필드를 사용할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1f8c4-118">Because the purpose of the market basket analysis is to determine which products are included in a single transaction, you do not have to use the **CustomerKey** field.</span></span>  
  
8.  <span data-ttu-id="1f8c4-119">모델 옆의 **키** 확인란을 선택 하 여 중첩 테이블 vAssocSeqLineItems의 키를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f8c4-119">Set the key for the nested table, vAssocSeqLineItems, by selecting the **Key** check box next to Model.</span></span> <span data-ttu-id="1f8c4-120">**입력** 확인란은이 작업을 수행 하는 경우에도 자동으로 선택 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1f8c4-120">The **Input** check box is also automatically selected when you do this.</span></span> <span data-ttu-id="1f8c4-121">에 대 한 **예측** 가능 확인란도 선택 `Model` 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f8c4-121">Select the **Predictable** check box for `Model` as well.</span></span>  
  
     <span data-ttu-id="1f8c4-122">시장 바구니 모델에서는 시장 바구니의 제품 순서를 고려 하지 않으므로 중첩 테이블의 키로 **LineNumber** 를 포함 하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1f8c4-122">In a market basket model, you do not care about the sequence of products in the shopping basket, and therefore you should not include **LineNumber** as a key for the nested table.</span></span> <span data-ttu-id="1f8c4-123">시퀀스가 중요 한 모델 에서만 **LineNumber** 을 키로 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f8c4-123">You would use **LineNumber** as a key only in a model where the sequence is important.</span></span> <span data-ttu-id="1f8c4-124">4단원에서 [!INCLUDE[msCoName](../includes/msconame-md.md)] 시퀀스 클러스터링 알고리즘을 사용하는 모델을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="1f8c4-124">You will create a model that uses the [!INCLUDE[msCoName](../includes/msconame-md.md)] Sequence Clustering algorithm in Lesson 4.</span></span>  
  
9. <span data-ttu-id="1f8c4-125">IncomeGroup 및 Region 왼쪽의 확인란을 선택하고 다른 항목은 선택하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1f8c4-125">Select the check box to the left of IncomeGroup and Region,but do not make any other selections.</span></span> <span data-ttu-id="1f8c4-126">맨 왼쪽 열의 확인란을 선택하면 나중에 참조할 수 있도록 해당 열이 구조에 추가되지만 모델에 사용되지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1f8c4-126">Checking the leftmost column adds the columns to the structure for later reference, but the columns will not be used in the model.</span></span> <span data-ttu-id="1f8c4-127">선택 항목은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="1f8c4-127">Your selections should look like the following:</span></span>  
  
     <span data-ttu-id="1f8c4-128">![대화 상자 표시 방법](../../2014/tutorials/media/tutorial-configassocmodel.gif "대화 상자 표시 방법")</span><span class="sxs-lookup"><span data-stu-id="1f8c4-128">![how dialog box should look](../../2014/tutorials/media/tutorial-configassocmodel.gif "how dialog box should look")</span></span>  
  
10. <span data-ttu-id="1f8c4-129">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1f8c4-129">Click **Next**.</span></span>  
  
11. <span data-ttu-id="1f8c4-130">**열 내용 및 데이터 형식 지정**페이지에서 다음 표에 표시 된 대로 선택 항목을 검토 한 후 **다음**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f8c4-130">On the **Specify Columns' Content and Data Type**page, review the selections, which should be as shown in the following table, and then click **Next**.</span></span>  
  
    |<span data-ttu-id="1f8c4-131">열</span><span class="sxs-lookup"><span data-stu-id="1f8c4-131">Columns</span></span>|<span data-ttu-id="1f8c4-132">콘텐츠 유형</span><span class="sxs-lookup"><span data-stu-id="1f8c4-132">Content Type</span></span>|<span data-ttu-id="1f8c4-133">데이터 형식</span><span class="sxs-lookup"><span data-stu-id="1f8c4-133">Data Type</span></span>|  
    |-------------|------------------|---------------|  
    |<span data-ttu-id="1f8c4-134">IncomeGroup</span><span class="sxs-lookup"><span data-stu-id="1f8c4-134">IncomeGroup</span></span>|<span data-ttu-id="1f8c4-135">불연속</span><span class="sxs-lookup"><span data-stu-id="1f8c4-135">Discrete</span></span>|<span data-ttu-id="1f8c4-136">텍스트</span><span class="sxs-lookup"><span data-stu-id="1f8c4-136">Text</span></span>|  
    |<span data-ttu-id="1f8c4-137">주문 번호</span><span class="sxs-lookup"><span data-stu-id="1f8c4-137">Order Number</span></span>|<span data-ttu-id="1f8c4-138">키</span><span class="sxs-lookup"><span data-stu-id="1f8c4-138">Key</span></span>|<span data-ttu-id="1f8c4-139">텍스트</span><span class="sxs-lookup"><span data-stu-id="1f8c4-139">Text</span></span>|  
    |<span data-ttu-id="1f8c4-140">지역</span><span class="sxs-lookup"><span data-stu-id="1f8c4-140">Region</span></span>|<span data-ttu-id="1f8c4-141">불연속</span><span class="sxs-lookup"><span data-stu-id="1f8c4-141">Discrete</span></span>|<span data-ttu-id="1f8c4-142">텍스트</span><span class="sxs-lookup"><span data-stu-id="1f8c4-142">Text</span></span>|  
    |<span data-ttu-id="1f8c4-143">vAssocSeqLineItems</span><span class="sxs-lookup"><span data-stu-id="1f8c4-143">vAssocSeqLineItems</span></span>|||  
    |<span data-ttu-id="1f8c4-144">모델</span><span class="sxs-lookup"><span data-stu-id="1f8c4-144">Model</span></span>|<span data-ttu-id="1f8c4-145">키</span><span class="sxs-lookup"><span data-stu-id="1f8c4-145">Key</span></span>|<span data-ttu-id="1f8c4-146">텍스트</span><span class="sxs-lookup"><span data-stu-id="1f8c4-146">Text</span></span>|  
  
12. <span data-ttu-id="1f8c4-147">**테스트 집합 만들기** 페이지에서 **테스트용 데이터 백분율** 옵션의 기본값은 30%입니다.</span><span class="sxs-lookup"><span data-stu-id="1f8c4-147">On the **Create testing set** page, the default value for the option **Percentage of data for testing** is 30 percent.</span></span> <span data-ttu-id="1f8c4-148">이를 **0**으로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f8c4-148">Change this to **0**.</span></span> <span data-ttu-id="1f8c4-149">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1f8c4-149">Click **Next**.</span></span>  
  
    > [!NOTE]  
    >  [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]<span data-ttu-id="1f8c4-150">에서는 모델 정확도를 측정하는 여러 다른 차트를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="1f8c4-150">provides different charts for measuring model accuracy.</span></span> <span data-ttu-id="1f8c4-151">그러나 리프트 차트 및 교차 유효성 검사 보고서와 같은 일부 정확도 차트 유형은 분류 및 추정용으로 디자인되었으며</span><span class="sxs-lookup"><span data-stu-id="1f8c4-151">However, some accuracy chart types, such as the lift chart and cross-validation report, are designed for classification and estimation.</span></span> <span data-ttu-id="1f8c4-152">연결 예측에 대해서는 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1f8c4-152">They are not supported for associative prediction.</span></span>  
  
13. <span data-ttu-id="1f8c4-153">**마법사 완료** 페이지의 **마이닝 구조 이름**에을 입력 `Association` 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f8c4-153">On the **Completing the Wizard** page, in **Mining structure name**, type `Association`.</span></span>  
  
14. <span data-ttu-id="1f8c4-154">**마이닝 모델 이름**에을 입력 `Association` 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f8c4-154">In **Mining model name**, type `Association`.</span></span>  
  
15. <span data-ttu-id="1f8c4-155">**드릴스루 허용**옵션을 선택 하 고 **마침**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f8c4-155">Select the option **Allow drill through**, and then click **Finish**.</span></span>  
  
     <span data-ttu-id="1f8c4-156">데이터 마이닝 디자이너가 열리고 `Association` 방금 만든 마이닝 구조가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1f8c4-156">Data Mining Designer opens to display the `Association` mining structure that you just created.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="1f8c4-157">단원의 다음 태스크</span><span class="sxs-lookup"><span data-stu-id="1f8c4-157">Next Task in Lesson</span></span>  
 [<span data-ttu-id="1f8c4-158">중급 데이터 마이닝 자습서 &#40;시장 바구니 모델 수정 및 처리&#41;</span><span class="sxs-lookup"><span data-stu-id="1f8c4-158">Modifying and Processing the Market Basket Model &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/modify-process-market-basket-model-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a><span data-ttu-id="1f8c4-159">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1f8c4-159">See Also</span></span>  
 <span data-ttu-id="1f8c4-160">[Microsoft 연결 알고리즘](../../2014/analysis-services/data-mining/microsoft-association-algorithm.md) </span><span class="sxs-lookup"><span data-stu-id="1f8c4-160">[Microsoft Association Algorithm](../../2014/analysis-services/data-mining/microsoft-association-algorithm.md) </span></span>  
 [<span data-ttu-id="1f8c4-161">콘텐츠 형식&#40;데이터 마이닝&#41;</span><span class="sxs-lookup"><span data-stu-id="1f8c4-161">Content Types &#40;Data Mining&#41;</span></span>](../../2014/analysis-services/data-mining/content-types-data-mining.md)  
  
  
