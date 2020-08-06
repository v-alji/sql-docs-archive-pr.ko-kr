---
title: 연결 규칙 모델에서 규칙 필터링 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- filtering rules [Analysis Services]
- Mining Model Viewer [Analysis Services], rules
- Rules Viewer
ms.assetid: 26cdba5b-5bf1-439e-80a3-8759774e918b
author: minewiskan
ms.author: owend
ms.openlocfilehash: 3c904713acc6eaf132e7cb1195186165f21d971a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652448"
---
# <a name="filter-a-rule-in-an-association-rules-model"></a><span data-ttu-id="d3499-102">연결 규칙 모델에서 규칙 필터링</span><span class="sxs-lookup"><span data-stu-id="d3499-102">Filter a Rule in an Association Rules Model</span></span>
  <span data-ttu-id="d3499-103">연결 모델에 필터링을 사용하여 보고자 하는 연결로만 결과를 제한할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d3499-103">You can use filtering with association models to restrict the results to just the associations that interest you.</span></span> <span data-ttu-id="d3499-104">예를 들어 특정 제품이 포함된 규칙만 표시하도록 규칙을 필터링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d3499-104">For example, you might filter the rules to show only those that include a specific product.</span></span>  
  
 <span data-ttu-id="d3499-105">데이터 마이닝 디자이너에서는 **연결 규칙 뷰어의** 규칙 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 탭의 컨트롤을 사용하여 표시되는 규칙을 필터링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d3499-105">In Data Mining Designer, you use the controls on the **Rules** tab of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Association Rules Viewer to filter the rules that are displayed.</span></span>  <span data-ttu-id="d3499-106">또한 모델에 쿼리를 만들어 특정 값이 포함된 항목 집합만 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d3499-106">You can also create a query on the model to see only itemset that contains a particular value.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d3499-107">이 옵션은 Microsoft 연결 알고리즘을 사용하여 만든 마이닝 모델에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d3499-107">This option is available only for mining models that have been created by using the Microsoft Association Algorithm.</span></span>  
  
### <a name="filter-a-rule-in-an-association-model"></a><span data-ttu-id="d3499-108">연결 모델에서 규칙 필터링</span><span class="sxs-lookup"><span data-stu-id="d3499-108">Filter a rule in an association model</span></span>  
  
1.  <span data-ttu-id="d3499-109">**연결 규칙 뷰어**를 사용하여 마이닝 모델을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="d3499-109">Open the mining model by using the **Association Rules Viewer**.</span></span> <span data-ttu-id="d3499-110">SQL Server Management Studio에서 마이닝 모델을 열려면 모델 이름을 마우스 오른쪽 단추로 클릭하고 **찾아보기**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d3499-110">To do this in SQL Server Management Studio, right click the model name and select **Browse**.</span></span> <span data-ttu-id="d3499-111">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]에서 마이닝 모델을 열려면 모델이 들어 있는 마이닝 구조를 두 번 클릭한 다음 **데이터 마이닝 디자이너** 의 **마이닝 모델 뷰어**탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d3499-111">To do this in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], double-click the mining structure that contains the model, and then click the **Mining Model Viewer** tab of **Data Mining Designer**.</span></span>  
  
2.  <span data-ttu-id="d3499-112">**연결 규칙 뷰어** 에서 **규칙**탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d3499-112">Click the **Rules** tab of the **Association Rules Viewer**.</span></span>  
  
3.  <span data-ttu-id="d3499-113">**규칙 필터** 상자에 규칙 조건을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="d3499-113">Type a rule condition into the **Filter Rule** box.</span></span> <span data-ttu-id="d3499-114">예를 들어 "Bike Stand"와 같은 규칙 조건을 입력합니다. 이 규칙 조건은 "Bike Stands"도 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="d3499-114">For example, a rule condition might be "Bike Stand", which also returns "Bike Stands".</span></span>  
  
     <span data-ttu-id="d3499-115">**규칙 필터** 입력란에는 .NET 언어에서 정의하는 정규식을 입력할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d3499-115">The **Filter Rule** text box supports regular expressions as defined by the .NET language.</span></span> <span data-ttu-id="d3499-116">따라서 `((.Helmets.*Fenders.*)|(.*Fenders.*Helmets.*))`와 같은 식을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d3499-116">Therefore, you can use expressions such as the following: `((.Helmets.*Fenders.*)|(.*Fenders.*Helmets.*))`.</span></span> <span data-ttu-id="d3499-117">이 식은 순서에 관계없이 Helmets와 Fenders라는 단어가 있는 특성이 포함된 모든 항목 집합을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="d3499-117">This expression would return any itemsets that include attributes with the words Helmets and Fenders, in any order.</span></span>  
  
4.  <span data-ttu-id="d3499-118">**최소 확률**에서 결과 규칙 수를 줄이려면 확률 값을 늘리고 결과 규칙 수를 늘리려면 확률 값을 줄입니다.</span><span class="sxs-lookup"><span data-stu-id="d3499-118">For **Minimum probability**, increase the value of probability to see fewer rules, or decrease the value to see more rules.</span></span>  
  
5.  <span data-ttu-id="d3499-119">**최소 중요도**에서 결과 규칙 수를 줄이려면 중요도 값을 늘리고 결과 규칙 수를 늘리려면 중요도 값을 줄입니다.</span><span class="sxs-lookup"><span data-stu-id="d3499-119">For **Minimum importance**, increase the value of importance to see fewer rules, or decrease the value to see more rules.</span></span>  
  
6.  <span data-ttu-id="d3499-120">**표시**에서 **특성 이름 및 값 표시**, **특성 이름만 표시**또는 **특성 값만 표시**옵션 중 하나를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d3499-120">For **Show**, select one of the following options: **Show attribute name and value**, **Show attribute name only**, or **Show attribute value only**.</span></span>  
  
7.  <span data-ttu-id="d3499-121">**최대 행 수**에서 지정한 조건을 만족하는 총 규칙 수를 늘리려면 값을 늘리고 반환되는 규칙 수를 제한하려면 값을 줄입니다.</span><span class="sxs-lookup"><span data-stu-id="d3499-121">For **Maximum rows**, increase the value to increase the total number of rules that meet the specified conditions, or decrease the value to limit the number of rules returned.</span></span> <span data-ttu-id="d3499-122">확률을 기준으로 규칙이 정렬되므로 확률 또는 중요도에 대해 지정한 조건을 만족하는 추가 규칙을 제거할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d3499-122">Rules are ordered by probability, so you might eliminate additional rules that meet the specified conditions for probability or importance.</span></span>  
  
8.  <span data-ttu-id="d3499-123">규칙 이름의 표시 방법을 전환하려면 **긴 이름 표시** 확인란을 선택하거나 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="d3499-123">Select or deselect the **Show long name** check box to toggle the way that the rules names are displayed.</span></span>  
  
     <span data-ttu-id="d3499-124">이렇게 하면 규칙이 필터링되어 지정한 항목을 포함하는 규칙만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="d3499-124">The rules are now filtered to only display rules that contain the indicated item.</span></span> <span data-ttu-id="d3499-125">필터 조건은 규칙 구분자("->") 앞이나 뒤에 있는 특성 값에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="d3499-125">The filter condition applies to attribute values either before or after the rule delimiter, "->".</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="d3499-126">뷰어에서는 마이닝 모델에 대한 쿼리를 기준으로 초기 규칙 목록을 캐시하며 최대 행 수, 확률, 중요도 또는 긴 이름 표시 옵션을 설정하여 쿼리 조건을 변경하지 않는 한 이 규칙 목록을 새로 고치지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d3499-126">The viewer caches the initial list of rules, based on a query to the mining model, and does not refresh the list of rules unless you change the conditions of the query by setting the maximum rows, the probability, importance, or the display of long names.</span></span> <span data-ttu-id="d3499-127">따라서 조건을 입력했는데 화면이 곧바로 새로 고쳐지지 않으면 **긴 이름 표시** 확인란을 선택한 다음 선택을 취소하여 뷰어의 데이터를 새로 고칠 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d3499-127">Therefore, if you type a condition and the display does not immediately refresh, you can force the viewer to refresh the data by selecting and then deselecting the **Show long names** check box.</span></span>  
  
### <a name="create-a-query-on-the-itemsets-in-an-association-model"></a><span data-ttu-id="d3499-128">연결 모델의 항목 집합에 대한 쿼리 만들기</span><span class="sxs-lookup"><span data-stu-id="d3499-128">Create a query on the itemsets in an association model</span></span>  
  
-   [<span data-ttu-id="d3499-129">연결 모델 쿼리 예제</span><span class="sxs-lookup"><span data-stu-id="d3499-129">Association Model Query Examples</span></span>](association-model-query-examples.md)  
  
## <a name="see-also"></a><span data-ttu-id="d3499-130">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d3499-130">See Also</span></span>  
 <span data-ttu-id="d3499-131">[마이닝 모델 뷰어 태스크 및 방법](mining-model-viewer-tasks-and-how-tos.md) </span><span class="sxs-lookup"><span data-stu-id="d3499-131">[Mining Model Viewer Tasks and How-tos](mining-model-viewer-tasks-and-how-tos.md) </span></span>  
 <span data-ttu-id="d3499-132">[Microsoft 연결 규칙 뷰어를 사용 하 여 모델 찾아보기](browse-a-model-using-the-microsoft-association-rules-viewer.md) </span><span class="sxs-lookup"><span data-stu-id="d3499-132">[Browse a Model Using the Microsoft Association Rules Viewer](browse-a-model-using-the-microsoft-association-rules-viewer.md) </span></span>  
 [<span data-ttu-id="d3499-133">3단원: 시장 바구니 시나리오 구축&#40;중급 데이터 마이닝 자습서&#41;</span><span class="sxs-lookup"><span data-stu-id="d3499-133">Lesson 3: Building a Market Basket Scenario &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../tutorials/lesson-3-building-a-market-basket-scenario-intermediate-data-mining-tutorial.md)  
  
  
