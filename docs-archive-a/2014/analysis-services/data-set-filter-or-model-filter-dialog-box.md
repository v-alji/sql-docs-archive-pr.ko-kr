---
title: 데이터 집합 필터 또는 모델 필터 대화 상자 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: a9602174-b7e2-4e16-8ded-dfd8eb9264d7
author: minewiskan
ms.author: owend
ms.openlocfilehash: afa796cd8cb23894c059deba411b3e1d6676e3b9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87733319"
---
# <a name="data-set-filter-or-model-filter-dialog-box"></a><span data-ttu-id="8a3d6-102">데이터 집합 필터 또는 모델 필터 대화 상자</span><span class="sxs-lookup"><span data-stu-id="8a3d6-102">Data Set Filter or Model Filter Dialog Box</span></span>
  <span data-ttu-id="8a3d6-103">이 대화 상자를 사용하면 데이터 집합에 적용할 수 있는 필터를 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8a3d6-103">This dialog box helps you build the filters that you can apply to a data set.</span></span>  <span data-ttu-id="8a3d6-104">데이터 집합은 테스트에 사용되는 외부 데이터 집합이나 마이닝 모델의 사례 데이터일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8a3d6-104">The data set can be an external data set used for testing, or the case data for a mining model.</span></span> <span data-ttu-id="8a3d6-105">이 대화 상자의 이름은 필터가 외부 데이터 집합용인지, 아니면 마이닝 모델용인지에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="8a3d6-105">The name of the dialog box changes depending on whether the filter is for an external data set or for a mining model.</span></span>  
  
 <span data-ttu-id="8a3d6-106">새 데이터 집합에 필터를 적용하면 조건에 맞는 데이터 집합의 사례만 사용하여 데이터 마이닝 모델이 평가됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a3d6-106">If you apply the filter to a new data set, the data mining model is evaluated by using only those cases in the data set that meet the conditions.</span></span> <span data-ttu-id="8a3d6-107">마이닝 모델 자체에 필터를 적용하면 필터 조건에 맞는 기존 테스트 데이터 집합의 사례만 사용하여 모델이 학습 및 테스트됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a3d6-107">If you apply the filter to the mining model itself, the model will be trained and tested by using only the cases in the existing test data set that meet the filter criteria.</span></span>  
  
-   <span data-ttu-id="8a3d6-108">**데이터 집합 필터** 대화 상자는 **마이닝 정확도 차트** 디자이너의 **입력 선택** 탭에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8a3d6-108">The **Data Set Filter** dialog box is available from the **Input Selection** tab of the **Mining Accuracy Chart** designer.</span></span>  
  
-   <span data-ttu-id="8a3d6-109">**모델 필터** 대화 상자는 데이터 마이닝 디자이너의 **마이닝 모델** 탭에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8a3d6-109">The **Model Filter** dialog box is available from the **Mining Models** tab of the Data Miningdesigner.</span></span>  
  
-   <span data-ttu-id="8a3d6-110">**조건** 표에는 테이블 또는 열 이름, 연산자 및 대상 값을 지정할 수 있는 열이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8a3d6-110">The **Conditions** grid contains columns where you can specify a table or column name, an operator, and target values.</span></span> <span data-ttu-id="8a3d6-111">이 표를 사용할 때는 기본적으로 WHERE 절을 만드는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="8a3d6-111">By using this grid you are essentially creating a WHERE clause.</span></span>  
  
> [!TIP]  
>  <span data-ttu-id="8a3d6-112"> 원래 학습 데이터의 하위 집합에 대한 정확도를 테스트하려면 학습 집합을 정의하는 데 사용된 데이터 원본 뷰를 외부 테스트 데이터로 추가한 다음 **데이터 집합 필터** 표에서 조건을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8a3d6-112">To test accuracy on a subset of the original training data, you can add the data source view that was used to define the training set as the external testing data, and then add conditions in the **Data Set Filter** grid.</span></span>  
  
 <span data-ttu-id="8a3d6-113">**자세한 내용:** [테스트 및 유효성 검사&#40;데이터 마이닝&#41;](data-mining/testing-and-validation-data-mining.md)</span><span class="sxs-lookup"><span data-stu-id="8a3d6-113">**For more information:** [Testing and Validation &#40;Data Mining&#41;](data-mining/testing-and-validation-data-mining.md)</span></span>  
  
## <a name="options"></a><span data-ttu-id="8a3d6-114">옵션</span><span class="sxs-lookup"><span data-stu-id="8a3d6-114">Options</span></span>  
 <span data-ttu-id="8a3d6-115">**조건**</span><span class="sxs-lookup"><span data-stu-id="8a3d6-115">**Conditions**</span></span>  
 <span data-ttu-id="8a3d6-116">테이블 이름 다음에 조건이 있는 열 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="8a3d6-116">Displays table names, followed by column names with conditions.</span></span>  
  
|<span data-ttu-id="8a3d6-117">값</span><span class="sxs-lookup"><span data-stu-id="8a3d6-117">Value</span></span>|<span data-ttu-id="8a3d6-118">설명</span><span class="sxs-lookup"><span data-stu-id="8a3d6-118">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="8a3d6-119">**및/또는**</span><span class="sxs-lookup"><span data-stu-id="8a3d6-119">**And/Or**</span></span>|<span data-ttu-id="8a3d6-120">여러 조건을 조인할 연산자를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8a3d6-120">Choose an operator to join multiple conditions.</span></span>|  
|<span data-ttu-id="8a3d6-121">**마이닝 구조 열**</span><span class="sxs-lookup"><span data-stu-id="8a3d6-121">**Mining Structure Column**</span></span>|<span data-ttu-id="8a3d6-122">데이터 원본을 선택한 다음 표의 연속되는 줄을 클릭하여 데이터 원본의 열을 추가하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8a3d6-122">Click to select a data source, and then click successive lines in the grid to add columns from the data source.</span></span><br /><br /> <span data-ttu-id="8a3d6-123">표의 첫 번째 줄은 데이터 원본 뷰를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8a3d6-123">The first line in the grid specifies the data source view.</span></span> <span data-ttu-id="8a3d6-124">데이터 원본 뷰를 선택하면 **마이닝 구조 열** 에 테이블 아이콘이 표시되고 **값** 필드에 이 데이터 원본에 대해 정의한 모든 조건의 조합이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a3d6-124">After you select a data source view, **Mining Structure Column** displays a table icon, and the **Value** field displays the combination of all criteria that you have defined for this data source.</span></span><br /><br /> <span data-ttu-id="8a3d6-125">데이터 원본을 선택하면 **마이닝 구조 열** 상자에 데이터 원본에 있는 개별 열이 포함된 드롭다운 목록이 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a3d6-125">After you have selected a data source, the **Mining Structure Column** box provides a dropdown list of individual columns in the data source.</span></span>|  
|<span data-ttu-id="8a3d6-126">**연산자**</span><span class="sxs-lookup"><span data-stu-id="8a3d6-126">**Operator**</span></span>|<span data-ttu-id="8a3d6-127">목록에서 연산자를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8a3d6-127">Select an operator from the list.</span></span>|  
|<span data-ttu-id="8a3d6-128">**값**</span><span class="sxs-lookup"><span data-stu-id="8a3d6-128">**Value**</span></span>|<span data-ttu-id="8a3d6-129">테이블의 경우 **값** 필드에는 데이터 원본에 적용된 모든 필터의 조합이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a3d6-129">For tables, the **Value** field shows the combination of all filters applied to the data source.</span></span> <span data-ttu-id="8a3d6-130">텍스트 상자 오른쪽에 있는 빌드 **(...)** 단추를 클릭 하 여 **필터** 대화 상자를 열고 조건을 작성할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8a3d6-130">You can also click the build **(...)** button at the right of the text box to open the **Filter** dialog box and build a condition.</span></span>|  
  
 <span data-ttu-id="8a3d6-131">**식**</span><span class="sxs-lookup"><span data-stu-id="8a3d6-131">**Expression**</span></span>  
 <span data-ttu-id="8a3d6-132">표를 사용하여 작성하는 조건 집합을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="8a3d6-132">Displays the set of criteria that you built by using the grid.</span></span>  
  
 <span data-ttu-id="8a3d6-133">**쿼리 편집**</span><span class="sxs-lookup"><span data-stu-id="8a3d6-133">**Edit Query**</span></span>  
 <span data-ttu-id="8a3d6-134">**식** 입력란에 필터 식을 직접 입력할 수 있도록 필터 편집 모드를 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="8a3d6-134">Changes the filter editing mode so that you can type a filter expression directly in the **Expression** text box.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8a3d6-135">필터 식을 수동으로 변경한 후에는 **입력 선택** 탭의 **필터 식** 상자에 식을 저장 한 후에도 그리드 편집 모드로 돌아갈 수 없습니다. 표를 사용 하 여 식을 작성 하려면 기존 필터 식을 삭제 하 고 다시 시작 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a3d6-135">After you have made manual changes to the filter expression, you cannot return to grid edit mode, even after you have saved the expression in the **Filter Expression** box on the **Input Selection** tab. If you want to build an expression by using the grid, you must delete the existing filter expression and start over.</span></span>  
  
 <span data-ttu-id="8a3d6-136">**쿼리 편집 내용 되돌리기**</span><span class="sxs-lookup"><span data-stu-id="8a3d6-136">**Revert Query Edits**</span></span>  
 <span data-ttu-id="8a3d6-137">표를 원래 상태로 복원하고 필터 식에 대한 모든 변경 내용을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="8a3d6-137">Restores the grid to its previous state and cancels any changes that you made to the filter expression.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a3d6-138">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8a3d6-138">See Also</span></span>  
 <span data-ttu-id="8a3d6-139">[테스트 및 유효성 검사 태스크 및 방법 &#40;데이터 마이닝&#41;](data-mining/testing-and-validation-tasks-and-how-tos-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="8a3d6-139">[Testing and Validation Tasks and How-tos &#40;Data Mining&#41;](data-mining/testing-and-validation-tasks-and-how-tos-data-mining.md) </span></span>  
 [<span data-ttu-id="8a3d6-140">마이닝 정확도 차트 디자이너 &#40;데이터 마이닝&#41;</span><span class="sxs-lookup"><span data-stu-id="8a3d6-140">Mining Accuracy Chart Designer &#40;Data Mining&#41;</span></span>](mining-accuracy-chart-designer-data-mining.md)  
  
  
