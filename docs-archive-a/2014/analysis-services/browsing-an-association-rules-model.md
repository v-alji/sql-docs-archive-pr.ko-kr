---
title: 연결 규칙 모델 찾아보기 | Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining models, browsing
- mining model, association
- mining models, viewing
- association [data mining]
ms.assetid: faffe208-7a64-4ec6-825f-ecbaa79caff7
author: minewiskan
ms.author: owend
ms.openlocfilehash: de5adbca264fff81b44424d865a2c8201a6fdfc3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648094"
---
# <a name="browsing-an-association-rules-model"></a><span data-ttu-id="0044e-102">연결 규칙 모델 찾아보기</span><span class="sxs-lookup"><span data-stu-id="0044e-102">Browsing an Association Rules Model</span></span>
  <span data-ttu-id="0044e-103">**찾아보기**를 사용 하 여 연결 모델을 열면의 연결 규칙 뷰어와 비슷한 대화형 뷰어에 모델이 표시 됩니다 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="0044e-103">When you open an association model using **Browse**, the model is displayed in an interactive viewer, similar to the Association Rules Viewer in [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span>  <span data-ttu-id="0044e-104">이 뷰어에서는 서로 연관된 항목을 한 눈에 확인할 수 있으며 예측 또는 제안에 사용할 수 있는 규칙이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="0044e-104">The viewer lets you see at a glance which items were correlated with each other, and displays rules that you can use for prediction or making recommendations.</span></span>  
  
##  <a name="explore-the-model"></a><a name="BKMK_ViewerTabs"></a><span data-ttu-id="0044e-105">모델 탐색</span><span class="sxs-lookup"><span data-stu-id="0044e-105">Explore the Model</span></span>  
 <span data-ttu-id="0044e-106">연결 규칙 알고리즘을 사용 하 여 만든 마이닝 모델을 열 때 [!INCLUDE[msCoName](../includes/msconame-md.md)] **찾아보기** 창에는 모델의 다른 측면을 탐색할 수 있도록 설계 된 다음 뷰가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0044e-106">When you open a mining model that was created using the [!INCLUDE[msCoName](../includes/msconame-md.md)] Association Rules algorithm, the **Browse** window includes the following views, each designed to let you explore a different aspect of the model:</span></span>  
  
-   [<span data-ttu-id="0044e-107">항목 집합</span><span class="sxs-lookup"><span data-stu-id="0044e-107">Itemsets</span></span>](#BKMK_Itemsets)  
  
-   [<span data-ttu-id="0044e-108">규칙.</span><span class="sxs-lookup"><span data-stu-id="0044e-108">Rules</span></span>](#BKMK_Rules)  
  
-   [<span data-ttu-id="0044e-109">종속성 네트워크</span><span class="sxs-lookup"><span data-stu-id="0044e-109">Dependency Net</span></span>](#BKMK_Dependency)  
  
 <span data-ttu-id="0044e-110">각 탭에 있는 옵션을 적어 두고 **긴 이름을 표시** 합니다.</span><span class="sxs-lookup"><span data-stu-id="0044e-110">Take note of the option on each tab, **Show long name** .</span></span> <span data-ttu-id="0044e-111">이 옵션을 선택하면 항목 집합을 가져온 테이블을 표시하거나 숨길 수 있고, 규칙 또는 항목 집합 이름을 짧게 또는 길게 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0044e-111">By selecting this option, you can show or hide the table from which the itemset originates, and shorten or lengthen the name of the rule or itemset.</span></span> <span data-ttu-id="0044e-112">이 옵션은 사례 데이터와 특성 데이터의 데이터 원본이 다른 경우에 특히 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="0044e-112">This option is particularly useful when your case data and attribute data are from different data sources.</span></span>  
  
 <span data-ttu-id="0044e-113">연결 모델을 시험해 보려면 샘플 데이터 통합 문서에서 연결 탭의 샘플 데이터를 사용하고 모두 기본값을 사용해서 연결 모델을 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0044e-113">To experiment with an association model, you can use the sample data on the Associate tab of the sample data workbook, and build an association model using all the defaults.</span></span> <span data-ttu-id="0044e-114">또한 쇼핑 바구니 분석 모델을 작성 하 고 **찾아보기**를 사용 하 여 열 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0044e-114">You can also build a Shopping Basket Analysis model and open that using **Browse**.</span></span>  
  
###  <a name="itemsets"></a><a name="BKMK_Itemsets"></a><span data-ttu-id="0044e-115">항목 집합</span><span class="sxs-lookup"><span data-stu-id="0044e-115">Itemsets</span></span>  
 <span data-ttu-id="0044e-116">**항목 집합** 탭은 연결 모델 탐색을 시작 하는 데 적합 한 장소입니다.</span><span class="sxs-lookup"><span data-stu-id="0044e-116">The **Itemsets** tab is a good place to begin exploring an association model.</span></span> <span data-ttu-id="0044e-117">이 탭에는 모델에서 자주 함께 발견되는 항목 목록이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="0044e-117">This tab shows a list of the items that the model frequently found together.</span></span>  
  
 <span data-ttu-id="0044e-118">![연결 모델의 항목 목록](media/dm13-association-itemsets.gif "연결 모델의 항목 목록")</span><span class="sxs-lookup"><span data-stu-id="0044e-118">![List of items in an association model](media/dm13-association-itemsets.gif "List of items in an association model")</span></span>  
  
 <span data-ttu-id="0044e-119">항목 집합의 가장 일반적인 예로, 시장 바구니 모델을 들 수 있습니다. 이 모델에서 항목 집합은 많은 고객들이 동시에 구입하는 제품 쌍 또는 집합을 나타낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0044e-119">The most common example of itemsets is in a shopping basket model, where an itemset represents pairs or sets of products that lots of customers purchase at the same time.</span></span> <span data-ttu-id="0044e-120">하지만 항목의 그룹 지정 및 순서에 따라 항목 집합에는 고객들이 일정 기간 동안 주문한 일련의 영화들이 포함되거나 특정 위치에서 자주 발생하는 이벤트가 포함될 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0044e-120">However, depending on how you group and order your items, the itemset might contain a sequence of movies that customers order over a period of time, or events that tend to occur in  a particular location.</span></span>  
  
 <span data-ttu-id="0044e-121">항목 *집합은* 한 항목을 2 개, 3 개 또는 여러 항목으로 포함할 수 있습니다. 그러나 대부분은 모델의 최대 항목 집합 크기로 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0044e-121">An *itemset* can contain as few as one item to two, three, or however, many is set as the maximum itemset size for the model.</span></span> <span data-ttu-id="0044e-122">각 항목 집합에 대해 뷰어는 항목 집합 *지원*, *확률*및 *크기*를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="0044e-122">For each itemset, the viewer displays the itemset  *support*,  *probability*, and *size*.</span></span> <span data-ttu-id="0044e-123">지지도 및 확률은 연결 모델에서 생성된 항목 집합 및 규칙의 순위를 지정하는 데 사용되는 주요 통계입니다.</span><span class="sxs-lookup"><span data-stu-id="0044e-123">Support and probability are the principal statistics used to rank the itemsets and rules generated by an association model.</span></span> <span data-ttu-id="0044e-124">이러한 값은 해당 중요도를 계산 및 기술하는 데에도 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="0044e-124">These values are also used to calculate and describe their importance.</span></span>  
  
 <span data-ttu-id="0044e-125">**지원**.</span><span class="sxs-lookup"><span data-stu-id="0044e-125">**Support**.</span></span> <span data-ttu-id="0044e-126">지지도는 이 항목이 포함된 사례 수 또는 입력 데이터 행 수를 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="0044e-126">Support means the number of cases or rows of input data that have this item.</span></span> <span data-ttu-id="0044e-127">예를 들어 항목 집합이 장바구니에 있는 두 항목을 포함 하는 경우 **지원** 열의 숫자는 원본 데이터에서 항목 조합이 발생 한 횟수를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="0044e-127">For example, if an itemset contains two items that are found in a shopping cart, the number in the **Support** column indicates how many times that combination of items occurred in the source data.</span></span>  
  
 <span data-ttu-id="0044e-128">**크기**.</span><span class="sxs-lookup"><span data-stu-id="0044e-128">**Size**.</span></span> <span data-ttu-id="0044e-129">항목 집합 크기를 변경하면 항목 집합 목록의 길이를 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0044e-129">By changing itemset size, you can control the length of the lists of itemsets.</span></span> <span data-ttu-id="0044e-130">목록에 단일 제품을 표시 하지 않으려면 **최소 항목 집합 크기**를 2 이상으로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="0044e-130">If you don't want to see single products in the list, change the option, **Minimum itemset size**, to 2 or more.</span></span>  <span data-ttu-id="0044e-131">항목 집합의 최소 크기를 늘려 목록을 제한하면 매우 구체적인 패턴을 찾을 수 있는데</span><span class="sxs-lookup"><span data-stu-id="0044e-131">Restricting the list by increasing the minimum size of itemsets lets you look for very specific patterns.</span></span> <span data-ttu-id="0044e-132">이는 대량의 데이터 집합으로 작업하는 경우에 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="0044e-132">This might be useful if you are working with a very large set of data.</span></span>  
  
 <span data-ttu-id="0044e-133">**최소 지원** 및 **최대 행** 수 값을 변경 하 여 탭에 표시 되는 항목 집합 수를 필터링 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0044e-133">You can filter the number of itemsets that are displayed in the tab by changing the **Minimum support** and **Maximum rows** values.</span></span> <span data-ttu-id="0044e-134">**최소 지원** 값을 늘리면 목록에 항목 집합 더 작은 값이 표시 되지만 항목 집합는 입력 데이터에서 더 일반적인 것입니다.</span><span class="sxs-lookup"><span data-stu-id="0044e-134">If you increase the **Minimum Support** value, the list will show fewer itemsets, but the itemsets will be the more common ones in the input data.</span></span> <span data-ttu-id="0044e-135">공통 여부는 중요 한 질문입니다. 다른 질문은 **규칙** 탭을 사용 하 여 탐색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0044e-135">Whether common is the same as important is another question, which you can explore using the **Rules** tab.</span></span>  
  
 <span data-ttu-id="0044e-136">**항목 집합** 탭에서 지원 값 또는 기타 컨트롤을 변경 하면 표시 되는 항목만 변경 되며 기본 모델에는 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0044e-136">Note that changing the support value or other controls on the **Itemsets** tab only changes the items that are displayed, and does not affect the underlying model.</span></span> <span data-ttu-id="0044e-137">항목 집합을 더 많이 생성 하거나 크기를 제한 하려는 경우 `MINIMUM_SUPPORT` `MAXIMUM_SUPPORT` **알고리즘 매개 변수** 대화 상자에서 사용할 수 있는 및 매개 변수를 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0044e-137">If you want to generate fewer or more itemsets, or limit their size, you should use the parameters, `MINIMUM_SUPPORT` and `MAXIMUM_SUPPORT`, available in the **Algorithm Parameters** dialog box.</span></span>  
  
##### <a name="explore-the-itemsets-list"></a><span data-ttu-id="0044e-138">항목 집합 목록 탐색</span><span class="sxs-lookup"><span data-stu-id="0044e-138">Explore the itemsets list</span></span>  
  
1.  <span data-ttu-id="0044e-139">**지원** 열을 클릭 하 여 가장 낮은 지원으로 정렬 합니다.</span><span class="sxs-lookup"><span data-stu-id="0044e-139">Click the **Support** column to sort by highest to lowest support.</span></span> <span data-ttu-id="0044e-140">그러면 고객이 가장 자주 구입하는 항목을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0044e-140">This will give you an idea of what customers are buying most often.</span></span>  
  
2.  <span data-ttu-id="0044e-141">원하는 특정 항목 집합에 초점을 맞추기 위해 가능한 한 많은 수의 조합에 초점을 맞추기 위해 항목 **집합 필터** 상자에 텍스트를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="0044e-141">To focus on a particular itemset of interest, out of the many thousand combinations possible, type some text in the **Filter Itemset** box.</span></span>  
  
     <span data-ttu-id="0044e-142">여기서는를 입력 했습니다 `Gloves` .</span><span class="sxs-lookup"><span data-stu-id="0044e-142">Here we typed `Gloves`.</span></span> <span data-ttu-id="0044e-143">필터를 적용하면 목록이 새로 고쳐지고 gloves가 포함된 항목 집합만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="0044e-143">When you apply the filter, the list is refreshed to show only itemsets containing gloves.</span></span> <span data-ttu-id="0044e-144">그러면 고객이 다른 항목과 함께 장갑을 구입한 트랜잭션만 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0044e-144">This lets you focus on the transactions where customers purchased gloves and some other item.</span></span>  
  
     <span data-ttu-id="0044e-145">**항목 집합 필터** 옵션에서는 이전에 사용한 필터 목록도 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="0044e-145">The **Filter Itemset** option also displays a list of the filters that you have used previously.</span></span>  
  
3.  <span data-ttu-id="0044e-146">**최소 항목 집합 크기** 값을 변경 하 여 장갑만 구입 하 고 다른 항목은 구입 하지 않은 고객을 필터링 합니다.</span><span class="sxs-lookup"><span data-stu-id="0044e-146">Change the value of **Minimum itemset size** to filter out the customers who bought only gloves and no other items.</span></span>  
  
4.  <span data-ttu-id="0044e-147">**표시**옵션에 대 한 드롭다운 목록을 클릭 하 여 특성이 표시 되는 방식을 제어 합니다.</span><span class="sxs-lookup"><span data-stu-id="0044e-147">Click the dropdown list for the option **Show**, to control how the attributes are displayed:</span></span>  
  
    -   <span data-ttu-id="0044e-148">**특성 이름 및 값 표시**</span><span class="sxs-lookup"><span data-stu-id="0044e-148">**Show attribute name and value**</span></span>  
  
    -   <span data-ttu-id="0044e-149">**특성 값만 표시**</span><span class="sxs-lookup"><span data-stu-id="0044e-149">**Show attribute value only**</span></span>  
  
    -   <span data-ttu-id="0044e-150">**특성 이름만 표시**</span><span class="sxs-lookup"><span data-stu-id="0044e-150">**Show attribute name only**</span></span>  
  
     <span data-ttu-id="0044e-151">이름이 어떻게 변경되는지 주의하십시오.</span><span class="sxs-lookup"><span data-stu-id="0044e-151">Notice how the name changes.</span></span> <span data-ttu-id="0044e-152">여러 고객이 구입한 제품들의 중첩된 테이블로 작성된 시장 바구니 모델의 경우, 특성 이름은 일반적으로 제품 이름이며, 목록에 제품이 있으면 고객이 해당 항목을 구입했음을 의미하는 `Existing`으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="0044e-152">In the case of a market basket model, which is built on nested tables of products that were purchased by multiple customers, the attribute name is typically the product name, and the presence of the product in the list is marked as `Existing`, meaning that the customer did buy the item.</span></span>  
  
     <span data-ttu-id="0044e-153">`Existing`의 반대는 `Missing`입니다. 이 특성은 데이터 마이닝을 조사할 때 매우 유용하게 사용될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0044e-153">The opposite of `Existing` is `Missing`, which can be a very useful attribute to investigate in data mining.</span></span> <span data-ttu-id="0044e-154">예를 들어 항목 A + B가 항목 A를 구매 했지만 항목 B가 아닌 고객을 찾기 위해 매우 인기 있는 것으로 가정 합니다. 예측 쿼리를 사용 하 여이 작업을 수행 하 고 다른 하나는 포함 하지 않고 트랜잭션을 검색 하 여 이러한 작업을 추가로 분석할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0044e-154">For example, suppose the itemset A +B is so very popular that you wanted to find customers who purchased Item A but not item B. You could do this by using a prediction query and retrieving the transactions with one but not the other, and do some further analysis on those.</span></span> <span data-ttu-id="0044e-155">연결 모델에 대 한 예측 쿼리를 만드는 방법에 대 한 자세한 내용은 SQL Server 온라인 설명서의 [연결 모델 쿼리 예제](data-mining/association-model-query-examples.md) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="0044e-155">For information about how to create prediction queries on association models, see [Association Model Query Examples](data-mining/association-model-query-examples.md) in SQL Server Books Online</span></span>  
  
5.  <span data-ttu-id="0044e-156">새 필터 조건을 사용 하 여 항목 집합 목록이 다시 표시 되도록 하려면 **긴 이름 표시** 확인란을 선택 하거나 선택 취소 합니다.</span><span class="sxs-lookup"><span data-stu-id="0044e-156">To force the list of itemsets to redisplay using your new filter criteria, you can select or clear the **Show long name** check box.</span></span>  
  
 [<span data-ttu-id="0044e-157">맨 위로 이동</span><span class="sxs-lookup"><span data-stu-id="0044e-157">Back to Top</span></span>](#BKMK_ViewerTabs)  
  
###  <a name="rules"></a><a name="BKMK_Rules"></a><span data-ttu-id="0044e-158">역할</span><span class="sxs-lookup"><span data-stu-id="0044e-158">Rules</span></span>  
 <span data-ttu-id="0044e-159">**규칙** 탭에는 항목 집합와 관련 값에 대 한 정보가 결합 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0044e-159">The **Rules** tab combines information about the itemsets and their relative value.</span></span>  
  
 <span data-ttu-id="0044e-160">![연관 모델로 생성된 규칙 목록](media/dm13-association-rules.gif "연관 모델로 생성된 규칙 목록")</span><span class="sxs-lookup"><span data-stu-id="0044e-160">![List of rules created by an association model](media/dm13-association-rules.gif "List of rules created by an association model")</span></span>  
  
 <span data-ttu-id="0044e-161">*확률* 은 대상 항목 조합을 포함 하는 데이터 집합 내 사례의 비율을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="0044e-161">*Probability* represents the fraction of cases in the dataset that contain the targeted combination of items.</span></span> <span data-ttu-id="0044e-162">확률은 *신뢰도*의 통계 개념과 비슷하며 규칙 결과가 발생 하는 정도를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="0044e-162">Probability is similar to the statistical concept of *confidence*, and gives you an indication of how likely the result of a rule is to occur.</span></span> <span data-ttu-id="0044e-163">이 창의 **최소 확률** 값을 변경 하 여 표시 되는 규칙을 필터링 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0044e-163">You can change the value of **Minimum probability** in this pane to filter the rules that are displayed.</span></span>  
  
 <span data-ttu-id="0044e-164">처음에 표시 되는 **최소 확률** 값은 모델을 작성할 때 알고리즘에서 사용 된 임계값입니다.</span><span class="sxs-lookup"><span data-stu-id="0044e-164">The value for **Minimum probability** that you initially see is the threshold value that was used by the algorithm when building the model.</span></span> <span data-ttu-id="0044e-165">모델이 완료 된 후에는이 값을 줄일 수 없지만 더 높은 확률 항목만 표시 하도록 늘릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0044e-165">After the model is complete, you can't decrease this value, but you can increase it to show only the higher probability items.</span></span>  
  
 <span data-ttu-id="0044e-166">*중요도* 는 규칙의 유용성을 측정 하도록 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="0044e-166">*Importance* is designed to measure the usefulness of a rule.</span></span> <span data-ttu-id="0044e-167">매우 일반적인 규칙은 해당되는 경우가 너무 많아서 값의 중요도가 거의 없을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0044e-167">A rule that is very common might be so ubiquitous that is has little information value.</span></span> <span data-ttu-id="0044e-168">중요도가 높을수록 결과 예측에서 규칙의 유용성도 높아집니다.</span><span class="sxs-lookup"><span data-stu-id="0044e-168">The greater the importance, the more valuable the rule is for predicting the outcome.</span></span> <span data-ttu-id="0044e-169">시장 [바구니 분석 &#40;Table AnalysisTools For Excel&#41;](shopping-basket-analysis-table-analysistools-for-excel.md) tool에서 중요도는 항목의 가격과 결합 하 여 판매 측면에서 잠재적으로 가장 가치가 있는 번들을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0044e-169">In the [Shopping Basket Analysis &#40;Table AnalysisTools for Excel&#41;](shopping-basket-analysis-table-analysistools-for-excel.md) tool, importance can be combined with the price of items to determine the bundles that are potentially most valuable in terms of sales.</span></span>  
  
##### <a name="explore-the-rules-list"></a><span data-ttu-id="0044e-170">규칙 목록 탐색</span><span class="sxs-lookup"><span data-stu-id="0044e-170">Explore the rules list</span></span>  
  
1.  <span data-ttu-id="0044e-171">열 제목- **확률**, **중요도**및 **규칙** 을 클릭 하 여 데이터가 어떻게 변경 되는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="0044e-171">Try clicking the column headings - **Probability**, **Importance**, and **Rule** - to see how the data changes.</span></span>  
  
2.  <span data-ttu-id="0044e-172">**필터 규칙** 옵션을 사용 하 여 값을 입력 하 고 대상 규칙에 초점을 맞출 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0044e-172">Use the **Filter Rule** option to type in values and focus on targeted rules.</span></span>  
  
     <span data-ttu-id="0044e-173">예를 들어 고객이 장갑과 함께 구매할 가능성이 있는 항목을 예측 하는 모든 규칙을 보려면 텍스트 상자에 "글러브"를 입력 하 고 창을 새로 고칩니다.</span><span class="sxs-lookup"><span data-stu-id="0044e-173">For example, if you want to see all the rules that predict what customers are likely to purchase along with gloves, type "gloves" in the text box and refresh the pane.</span></span>  
  
     <span data-ttu-id="0044e-174">**항목 집합 필터** 옵션에서는 이전에 사용한 필터 목록도 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="0044e-174">The **Filter Itemset** option also displays a list of the filters that you have used previously.</span></span>  
  
3.  <span data-ttu-id="0044e-175">필터 조건을 사용 하 여 규칙 목록을 다시 **표시 하려면 긴 이름 표시** 확인란을 선택 하거나 선택 취소할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0044e-175">To force the list of rules to redisplay using filter criteria, you can select or clear the **Show long name** check box.</span></span>  
  
4.  <span data-ttu-id="0044e-176">**표시** 옵션을 사용 하 여 규칙 이름이 표시 되는 방식을 제어 합니다.</span><span class="sxs-lookup"><span data-stu-id="0044e-176">Use the option, **Show** to control the way that rule names are displayed.</span></span>  
  
5.  <span data-ttu-id="0044e-177">**최대 행** 수 옵션의 값을 100로 설정 하 고 **Excel로 복사**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="0044e-177">Set the value for the **Maximum rows** option to 100, and then click **Copy to Excel**.</span></span>  
  
     <span data-ttu-id="0044e-178">이 값을 변경 해도 모델의 데이터 양에는 영향을 주지 않습니다. 표시 목록에서 행의 수를 제어 하기만 합니다.</span><span class="sxs-lookup"><span data-stu-id="0044e-178">Note that changing this value doesn't have any effect on the amount of data in the model; it simply controls the number of rows in the display list.</span></span> <span data-ttu-id="0044e-179">이 옵션은 매우 큰 모델을 사용할 때 유용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0044e-179">This option can be useful when working with very large models.</span></span>  
  
 [<span data-ttu-id="0044e-180">맨 위로 이동</span><span class="sxs-lookup"><span data-stu-id="0044e-180">Back to Top</span></span>](#BKMK_ViewerTabs)  
  
###  <a name="dependency-network"></a><a name="BKMK_Dependency"></a><span data-ttu-id="0044e-181">종속성 네트워크</span><span class="sxs-lookup"><span data-stu-id="0044e-181">Dependency Network</span></span>  
 <span data-ttu-id="0044e-182">**종속성 네트워크** 탭은 항목 간의 상관 관계의 시각적 맵입니다.</span><span class="sxs-lookup"><span data-stu-id="0044e-182">The **Dependency Network** tab is a visual map of the correlations among items.</span></span> <span data-ttu-id="0044e-183">그래프의 각 타원 ( *노드라고*함)은 "Vest = Existing" 또는 "Age = 1-30"와 같은 특성-값 쌍을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="0044e-183">Each oval in the graph (referred to as a *node*) represents an attribute-value pair, such as "Vest = Existing" or "Age = 1-30".</span></span>  <span data-ttu-id="0044e-184">타원 (에 *지*)을 연결 하는 각 줄은 상관 관계의 형식을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="0044e-184">Each line connecting the ovals (referred to as an *edge*) represents a type of correlation.</span></span>  
  
 <span data-ttu-id="0044e-185">![연결 모델에 대한 종속성 네트워크 그래프](media/dm13-association-dependencynetwork.gif "연결 모델에 대한 종속성 네트워크 그래프")</span><span class="sxs-lookup"><span data-stu-id="0044e-185">![Dependency network graph for an association model](media/dm13-association-dependencynetwork.gif "Dependency network graph for an association model")</span></span>  
  
##### <a name="explore-the-dependency-network"></a><span data-ttu-id="0044e-186">종속성 네트워크 탐색</span><span class="sxs-lookup"><span data-stu-id="0044e-186">Explore the dependency network</span></span>  
  
1.  <span data-ttu-id="0044e-187">**찾기** 단추를 클릭 하 고 **노드 찾기** 대화 상자를 사용 하 여 원하는 항목을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="0044e-187">Click the **Find** button and use the **Find Node** dialog box to type an item of interest.</span></span>  
  
     <span data-ttu-id="0044e-188">예를 들어 "글러브"를 입력 한 후 결과를 쉽게 볼 수 있도록 창에서 그래프를 최대화 합니다.</span><span class="sxs-lookup"><span data-stu-id="0044e-188">For example, type "gloves" and then maximize the graph in the window so that you can easily see the results.</span></span>  
  
     <span data-ttu-id="0044e-189">항목이 포함된 노드가 강조 표시되고 노드를 가리키는 화살표는 항목을 연결하는 규칙을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="0044e-189">The node that contains the item is highlighted, while the arrows pointing to the node represent a rule that connects the items.</span></span>  
  
     <span data-ttu-id="0044e-190">화살표의 방향은 규칙의 방향을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="0044e-190">The direction of the arrow tells you the direction of the rule.</span></span> <span data-ttu-id="0044e-191">예를 들어, 글러브를 구매한 누군가가 vest를 구입 하는 경우 "글러브" 노드에서 화살표가 시작 되 고 "vest" 노드에서 종료 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0044e-191">For example, if someone who buys gloves is also likely to buy a vest, the arrow will start from the "glove" node and terminate on the "vest" node.</span></span>  
  
     <span data-ttu-id="0044e-192">이 규칙에 대 한 추가 통계를 얻으려면 **규칙** 탭을 클릭 하 고 "글러브"-> "vest-existing" 설명이 포함 된 규칙을 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0044e-192">To get additional statistics about this rule, you can click the **Rules** tab and look for a rule with the description, "Glove - Existing" -> "Vest - Existing.")</span></span>  
  
2.  <span data-ttu-id="0044e-193">뷰어 왼쪽에서 슬라이더를 클릭해서 끕니다.</span><span class="sxs-lookup"><span data-stu-id="0044e-193">Click and drag the slider at the left of the viewer.</span></span>  
  
     <span data-ttu-id="0044e-194">슬라이더는 규칙의 확률에 대한 필터로 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="0044e-194">The slider acts as a filter on the probability of the rules.</span></span> <span data-ttu-id="0044e-195">슬라이더를 내리면 가장 강력한 규칙만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="0044e-195">Lowering the slider shows only the strongest rules.</span></span>  
  
3.  <span data-ttu-id="0044e-196">**Excel로 복사** 를 클릭 하 여 현재 창의 스냅숏을 excel에 복사 합니다.</span><span class="sxs-lookup"><span data-stu-id="0044e-196">Click **Copy to Excel** to copy a snapshot of the current window to Excel.</span></span>  
  
     <span data-ttu-id="0044e-197">Excel로 복사 하는 그래프에서는 작업을 수행할 수 없습니다. 대화형 네트워크 그래프가 필요한 경우 [Visio에서 데이터 마이닝 모델 보기 &#40;데이터 마이닝 추가 기능&#41;](viewing-data-mining-models-in-visio-data-mining-add-ins.md)를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="0044e-197">You won't be able to work with the graph that you copy into Excel; if you need an interactive network graph, use the [Viewing Data Mining Models in Visio &#40;Data Mining Add-ins&#41;](viewing-data-mining-models-in-visio-data-mining-add-ins.md).</span></span>  
  
 [<span data-ttu-id="0044e-198">맨 위로 이동</span><span class="sxs-lookup"><span data-stu-id="0044e-198">Back to Top</span></span>](#BKMK_ViewerTabs)  
  
## <a name="more-about-association-models"></a><span data-ttu-id="0044e-199">연결 모델에 대한 추가 정보</span><span class="sxs-lookup"><span data-stu-id="0044e-199">More about Association Models</span></span>  
 <span data-ttu-id="0044e-200">**찾아보기** 기능을 사용 하 여 Microsoft 연결 규칙 알고리즘을 사용 하 여 만든 모델을 열고 탐색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0044e-200">You can use the **Browse** feature to open and explore any model that was created using the Microsoft Association Rules algorithm.</span></span> <span data-ttu-id="0044e-201">여기에는 시장 [바구니 분석 &#40;테이블 AnalysisTools For Excel&#41;](shopping-basket-analysis-table-analysistools-for-excel.md) 도구, **테이블 분석 도구** 리본 또는의를 사용 하 여 작성 된 모델이 포함 됩니다 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="0044e-201">This includes models built using the [Shopping Basket Analysis &#40;Table AnalysisTools for Excel&#41;](shopping-basket-analysis-table-analysistools-for-excel.md) tool, in the **Table Analysis Tools** ribbon, or in [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="0044e-202">시장 바구니 분석 도구를 사용하여 연결 규칙 모델을 만들면 많은 고급 옵션이 자동으로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="0044e-202">If you create an association rules model using the Shopping Basket Analysis tool, many of the advanced options are configured automatically for you.</span></span>  
  
 <span data-ttu-id="0044e-203">고급 매개 변수를 설정 하거나 최소 확률 및 지원을 변경 하려면 [연결 마법사 &#40;excel 용 데이터 마이닝 클라이언트&#41;](associate-wizard-data-mining-client-for-excel.md) 마법사를 사용 하거나 [&#40;구조에 모델 추가를 사용 하 여 Excel 용 데이터 마이닝 추가 기능&#41;](add-model-to-structure-data-mining-add-ins-for-excel.md) 모델링 옵션을 사용 하 여 모델을 직접 작성 합니다.</span><span class="sxs-lookup"><span data-stu-id="0044e-203">If you want to set advanced parameters or alter minimum probability and support, use the [Associate Wizard &#40;Data Mining Client for Excel&#41;](associate-wizard-data-mining-client-for-excel.md) wizard, or build your own model using the [Add Model to Structure &#40;Data Mining Add-ins for Excel&#41;](add-model-to-structure-data-mining-add-ins-for-excel.md) modeling option.</span></span>  
  
-   <span data-ttu-id="0044e-204">**항목 집합:** 모델을 만들 때 MINIMUM_PROBABILITY 매개 변수에 값을 할당 하 여 생성 되는 항목 집합 수를 제어할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0044e-204">**Itemsets:** When you create the model, you can also control the number of itemsets that are generated by assigning a value to the MINIMUM_PROBABILITY parameter.</span></span> <span data-ttu-id="0044e-205">이 매개 변수는 알고리즘 매개 변수 대화 상자에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0044e-205">This parameter is available in the Algorithm Parameters dialog box.</span></span>  
  
-   <span data-ttu-id="0044e-206">**규칙:** [!INCLUDE[msCoName](../includes/msconame-md.md)]연결 규칙 알고리즘은 확률 값을 사용 하 여 생성 되는 규칙 수를 제한 합니다.</span><span class="sxs-lookup"><span data-stu-id="0044e-206">**Rules:** The [!INCLUDE[msCoName](../includes/msconame-md.md)] Association Rules algorithm uses probability values to restrict the number of rules that are generated.</span></span> <span data-ttu-id="0044e-207">`MINIMUM_PROBABILITY` 또는 `MINIMUM _IMPORTANCE` 매개 변수를 설정해서 규칙 수를 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0044e-207">You can control the number of rules by setting the parameters, `MINIMUM_PROBABILITY` or `MINIMUM _IMPORTANCE`.</span></span>  
  
 <span data-ttu-id="0044e-208">고급 매개 변수를 구성 하는 방법에 대 한 자세한 내용은 데이터 마이닝 [알고리즘 &#40;SQL Server 데이터 마이닝 추가 기능&#41;](data-mining-algorithms-sql-server-data-mining-add-ins.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="0044e-208">For more information about configuring advanced parameters, see [Data Mining Algorithms &#40;SQL Server Data Mining Add-ins&#41;](data-mining-algorithms-sql-server-data-mining-add-ins.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0044e-209">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0044e-209">See Also</span></span>  
 [<span data-ttu-id="0044e-210">Excel &#40;SQL Server 데이터 마이닝 추가 기능을 검색 하는 모델&#41;</span><span class="sxs-lookup"><span data-stu-id="0044e-210">Browsing Models in Excel &#40;SQL Server Data Mining Add-ins&#41;</span></span>](browsing-models-in-excel-sql-server-data-mining-add-ins.md)  
  
  
