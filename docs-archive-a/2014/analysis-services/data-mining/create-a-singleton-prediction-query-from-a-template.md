---
title: 템플릿에서 단일 예측 쿼리 만들기 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- singleton query predictions [DMX]
ms.assetid: e0a68ab0-bece-4d25-b464-47f1719302e6
author: minewiskan
ms.author: owend
ms.openlocfilehash: a80e853875cce349dd8623fab3c30f1ad09bfbf6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647330"
---
# <a name="create-a-singleton-prediction-query-from-a-template"></a><span data-ttu-id="8ddcd-102">템플릿에서 단일 예측 쿼리 작성</span><span class="sxs-lookup"><span data-stu-id="8ddcd-102">Create a Singleton Prediction Query from a Template</span></span>
  <span data-ttu-id="8ddcd-103">단일 쿼리는 예측에 사용 하려는 모델이 있지만이 모델을 외부 입력 데이터 집합에 매핑하거나 대량 예측을 수행 하지 않으려는 경우에 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ddcd-103">A singleton query is useful when you have a model that you want to use for prediction, but don't want to map it to an external input data set or make bulk predictions.</span></span> <span data-ttu-id="8ddcd-104">단일 쿼리를 사용하면 모델에 값을 제공하고 바로 예측된 값을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ddcd-104">With a singleton query, you can provide a value or values to the model and instantly see the predicted value.</span></span>  
  
 <span data-ttu-id="8ddcd-105">예를 들어 다음 DMX 쿼리는 타겟 메일링 모델인 TM_Decision_Tree에 대한 단일 쿼리를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="8ddcd-105">For example, the following DMX query represents a singleton query against the targeted mailing model, TM_Decision_Tree.</span></span>  
  
```  
SELECT * FROM [TM_Decision_tree] ;  
NATURAL PREDICTION JOIN  
(SELECT '2' AS [Number Children At Home], '45' as [Age])  
AS [t]  
```  
  
 <span data-ttu-id="8ddcd-106">다음 절차에서는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 에서 템플릿 탐색기를 사용하여 이 쿼리를 빠르게 만드는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="8ddcd-106">The procedure that follows describes how to use the Template Explorer in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to quickly create this query.</span></span>  
  
### <a name="to-open-the-analysis-services-templates-in-sql-server-management-studio"></a><span data-ttu-id="8ddcd-107">SQL Server Management Studio에서 Analysis Services 템플릿을 열려면</span><span class="sxs-lookup"><span data-stu-id="8ddcd-107">To open the Analysis Services templates in SQL Server Management Studio</span></span>  
  
1.  <span data-ttu-id="8ddcd-108">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]의 **보기** 메뉴에서 **템플릿 탐색기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8ddcd-108">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], on the **View** menu, click **Template Explorer**.</span></span>  
  
2.  <span data-ttu-id="8ddcd-109">큐브 아이콘을 클릭하여 **Analysis Services**템플릿을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="8ddcd-109">Click the cube icon to open the **Analysis Server**templates.</span></span>  
  
### <a name="to-open-a-prediction-query-template"></a><span data-ttu-id="8ddcd-110">예측 쿼리 템플릿을 열려면</span><span class="sxs-lookup"><span data-stu-id="8ddcd-110">To open a prediction query template</span></span>  
  
1.  <span data-ttu-id="8ddcd-111">**템플릿 탐색기**의 Analysis Server 템플릿 목록에서 **DMX**, **예측 쿼리**를 차례로 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="8ddcd-111">In **Template Explorer**, in the list of Analysis Server templates, expand **DMX**, and thenexpand **Prediction Queries**.</span></span>  
  
2.  <span data-ttu-id="8ddcd-112">**단일 예측**을 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8ddcd-112">Double-click **Singleton Prediction**.</span></span>  
  
3.  <span data-ttu-id="8ddcd-113">**Analysis Services에 연결** 대화 상자에서 쿼리할 마이닝 모델을 포함하는 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 인스턴스가 있는 서버의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="8ddcd-113">In the **Connect to Analysis Services** dialog box, type the name of the server that has the instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] that contains the mining model to be queried.</span></span>  
  
4.  <span data-ttu-id="8ddcd-114">**연결**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8ddcd-114">Click **Connect**.</span></span>  
  
5.  <span data-ttu-id="8ddcd-115">데이터 마이닝 함수 및 데이터 마이닝 구조/관련 모델 목록을 포함하는 마이닝 모델 개체 브라우저와 함께 템플릿이 지정 데이터베이스에서 열립니다.</span><span class="sxs-lookup"><span data-stu-id="8ddcd-115">The template opens in the specified database, together with a mining model Object Browser that contains data mining functions and a list of data mining structures and related models.</span></span>  
  
### <a name="to-customize-the-singleton-query-template"></a><span data-ttu-id="8ddcd-116">단일 쿼리 템플릿을 사용자 지정하려면</span><span class="sxs-lookup"><span data-stu-id="8ddcd-116">To customize the singleton query template</span></span>  
  
1.  <span data-ttu-id="8ddcd-117">템플릿에서 **사용 가능한 데이터베이스** 드롭다운 목록을 클릭한 다음 목록에서 Analysis Services 인스턴스를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8ddcd-117">In the template, click the **Available Databases** drop-down list, and then select an instance of Analysis Service from the list.</span></span>  
  
2.  <span data-ttu-id="8ddcd-118">**마이닝 모델** 목록에서 쿼리할 마이닝 모델을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8ddcd-118">In the **Mining Model** list, select the mining model that you want to query.</span></span>  
  
     <span data-ttu-id="8ddcd-119">마이닝 모델의 열 목록이 개체 브라우저의 **메타데이터** 창에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="8ddcd-119">The list of columns in the mining model appears in the **Metadata** pane of the object browser.</span></span>  
  
3.  <span data-ttu-id="8ddcd-120">**쿼리** 메뉴에서 **템플릿 매개 변수 값 지정**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8ddcd-120">On the **Query** menu, select **Specify Values for Template Parameters**.</span></span>  
  
4.  <span data-ttu-id="8ddcd-121">**select list** 행에 \*를 입력하여 모든 열을 반환하거나 쉼표로 구분된 열과 식의 목록을 입력하여 특정 열을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="8ddcd-121">In the **select list** row, type \* to return all columns, or type a comma-delimited list of columns and expressions to return specific columns.</span></span>  
  
     <span data-ttu-id="8ddcd-122">\*를 입력하는 경우 6단계에서 새 값을 제공하는 열과 함께 예측 가능한 열이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ddcd-122">If you type \*, the predictable column is returned, together with any columns for which you provide new values for in step 6.</span></span>  
  
     <span data-ttu-id="8ddcd-123">이 항목의 시작 부분에 표시된 샘플 코드의 경우 **select list** 행이 \*로 설정되었습니다.</span><span class="sxs-lookup"><span data-stu-id="8ddcd-123">For the sample code shown at the start of this topic, the **select list** row was set to \*.</span></span>  
  
5.  <span data-ttu-id="8ddcd-124">**mining model** 행에 **개체 탐색기**에 나타나는 마이닝 모델 목록에 있는 마이닝 모델의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="8ddcd-124">In the **mining model** row, type the name of the mining model from among the list of mining models that appear in **Object Explorer**.</span></span>  
  
     <span data-ttu-id="8ddcd-125">이 항목의 시작 부분에 표시 된 예제 코드의 경우 **마이닝 모델** 행이 이름으로 설정 되었습니다 `TM_Decision_Tree` .</span><span class="sxs-lookup"><span data-stu-id="8ddcd-125">For the sample code shown at the start of this topic, the **mining model** row was set to the name, `TM_Decision_Tree`.</span></span>  
  
6.  <span data-ttu-id="8ddcd-126">**value** 행에 예측을 수행할 새 데이터 값을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="8ddcd-126">In the **value** row, type the new data value for which you want to make a prediction.</span></span>  
  
     <span data-ttu-id="8ddcd-127">이 항목의 시작 부분에 표시 된 샘플 코드의 경우, **value** `2` 홈의 자녀 수를 기반으로 자전거 구매 동작을 예측 하기 위해 value 행이로 설정 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="8ddcd-127">For the sample code shown at the start of this topic, the **value** row was set to `2` to predict bike buying behavior based on the number of children at home.</span></span>  
  
7.  <span data-ttu-id="8ddcd-128">**column** 행에 새 데이터가 매핑되어야 하는 마이닝 모델의 열 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="8ddcd-128">In the **column** row, type the name of the column in the mining model to which the new data should be mapped.</span></span>  
  
     <span data-ttu-id="8ddcd-129">이 항목의 시작 부분에 표시 된 예제 코드의 경우 **column** 행이로 설정 되었습니다 `Number Children at Home` .</span><span class="sxs-lookup"><span data-stu-id="8ddcd-129">For the sample code shown at the start of this topic, the **column** row was set to `Number Children at Home`.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="8ddcd-130">**템플릿 매개 변수 값 지정** 대화 상자를 사용할 때는 열 이름을 대괄호로 묶을 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8ddcd-130">When you use the **Specify Values for Template Parameters** dialog box, you do not have to add square brackets around the column name.</span></span> <span data-ttu-id="8ddcd-131">대괄호는 자동으로 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ddcd-131">The brackets will automatically be added for you.</span></span>  
  
8.  <span data-ttu-id="8ddcd-132">**입력 별칭** 을로 그대로 둡니다 `t` .</span><span class="sxs-lookup"><span data-stu-id="8ddcd-132">Leave the **input alias** as `t`.</span></span>  
  
9. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
10. <span data-ttu-id="8ddcd-133">쿼리 텍스트 창에서 구문 오류를 나타내는 쉼표 및 줄임표 아래의 빨간색 물결 기호를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="8ddcd-133">In the query text pane, find the red squiggle under the comma and ellipsis that indicates a syntax error.</span></span> <span data-ttu-id="8ddcd-134">줄임표를 삭제하고 원하는 쿼리 조건을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="8ddcd-134">Delete the ellipsis, and add any additional query condition that you want.</span></span> <span data-ttu-id="8ddcd-135">다른 조건을 추가하지 않는 경우 쉼표를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="8ddcd-135">If you do not add any other conditions, delete the comma.</span></span>  
  
     <span data-ttu-id="8ddcd-136">이 항목의 시작 부분에 표시된 예제 코드의 경우 추가 쿼리 조건이 `'45' as [Age]`로 설정되었습니다.</span><span class="sxs-lookup"><span data-stu-id="8ddcd-136">For the sample code shown at the start of this topic, the additional query condition was set to `'45' as [Age]`.</span></span>  
  
11. <span data-ttu-id="8ddcd-137">**실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8ddcd-137">Click **Execute**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ddcd-138">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8ddcd-138">See Also</span></span>  
 [<span data-ttu-id="8ddcd-139">예측 만들기&#40;기본 데이터 마이닝 자습서&#41;</span><span class="sxs-lookup"><span data-stu-id="8ddcd-139">Creating Predictions &#40;Basic Data Mining Tutorial&#41;</span></span>](../../tutorials/creating-predictions-basic-data-mining-tutorial.md)  
  
  
