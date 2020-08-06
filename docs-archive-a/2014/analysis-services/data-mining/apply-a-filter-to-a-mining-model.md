---
title: 마이닝 모델에 필터 적용 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- model filter [data mining]
- filters [data mining]
- filtering input rows [Analysis Services]
- filtering data [Analysis Services]
ms.assetid: 4d0abeb5-e939-46d3-9097-6e0358244300
author: minewiskan
ms.author: owend
ms.openlocfilehash: d9f3147c36e69d9c2249d5bf6d1ba201799c6e27
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653057"
---
# <a name="apply-a-filter-to-a-mining-model"></a><span data-ttu-id="b1df4-102">마이닝 모델에 필터 적용</span><span class="sxs-lookup"><span data-stu-id="b1df4-102">Apply a Filter to a Mining Model</span></span>
  <span data-ttu-id="b1df4-103">마이닝 구조에 중첩 테이블이 포함된 경우 사례 테이블, 중첩 테이블 또는 두 테이블 모두에 필터를 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b1df4-103">If your mining structure contains a nested table, you can apply a filter to the case table, the nested table, or both.</span></span>  
  
 <span data-ttu-id="b1df4-104">다음 절차에서는 사례 필터 및 중첩 테이블 행의 필터와 같은 두 종류의 필터를 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="b1df4-104">The following procedure demonstrates how to create both kinds of filters: case filters, and filters on the nested table rows.</span></span>  
  
 <span data-ttu-id="b1df4-105">사례 테이블의 조건은 수입이 30000 ~ 40000인 고객으로 제한합니다.</span><span class="sxs-lookup"><span data-stu-id="b1df4-105">The condition on the case table restricts customers to those with income between 30000 and 40000.</span></span> <span data-ttu-id="b1df4-106">중첩 테이블의 조건은 특정 항목을 구입하지 않은 고객으로 제한합니다.</span><span class="sxs-lookup"><span data-stu-id="b1df4-106">The condition on the nested table restricts the customers to those who did not purchase a particular item.</span></span>  
  
 <span data-ttu-id="b1df4-107">이 예에서 만든 전체 필터 조건은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="b1df4-107">The complete filter condition created in this example is as follows:</span></span>  
  
```  
[Income] > '30000'   
AND  [Income] < '40000'   
AND EXISTS (SELECT * FROM [<nested table name>]   
WHERE [Model] <> 'Water Bottle' )   
```  
  
### <a name="to-create-a-case-filter-on-a-mining-model"></a><span data-ttu-id="b1df4-108">마이닝 모델에 사례 필터를 만들려면</span><span class="sxs-lookup"><span data-stu-id="b1df4-108">To create a case filter on a mining model</span></span>  
  
1.  <span data-ttu-id="b1df4-109">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]의 솔루션 탐색기에서 필터링할 마이닝 모델이 포함된 마이닝 구조를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b1df4-109">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], in Solution Explorer, click the mining structure that contains the mining model you want to filter.</span></span>  
  
2.  <span data-ttu-id="b1df4-110">**마이닝 모델** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b1df4-110">Click the **Mining Models** tab.</span></span>  
  
3.  <span data-ttu-id="b1df4-111">모델을 선택하고 마우스 오른쪽 단추를 클릭하여 바로 가기 메뉴를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="b1df4-111">Select the model, and right-click to open the shortcut menu.</span></span>  
  
     <span data-ttu-id="b1df4-112">또는</span><span class="sxs-lookup"><span data-stu-id="b1df4-112">-or-</span></span>  
  
     <span data-ttu-id="b1df4-113">모델을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b1df4-113">Select the model.</span></span> <span data-ttu-id="b1df4-114">**마이닝 모델** 메뉴에서 **모델 필터 설정**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b1df4-114">Then, on the **Mining Model** menu, select **Set Model Filter**.</span></span>  
  
4.  <span data-ttu-id="b1df4-115">**모델 필터** 대화 상자의 **마이닝 구조 열** 입력란에서 표의 첫 행을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b1df4-115">In the **Model Filter** dialog box, click the top row in the grid, in the **Mining Structure Column** text box.</span></span>  
  
5.  <span data-ttu-id="b1df4-116">데이터 원본에 단일 플랫 테이블이 포함된 경우 드롭다운 목록에 해당 테이블의 열 이름만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="b1df4-116">If the data source contains a single flat table, the drop-down list displays only the names of the columns in that table.</span></span>  
  
     <span data-ttu-id="b1df4-117">마이닝 구조에 여러 테이블이 포함된 경우 목록에 원본 테이블 이름이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="b1df4-117">If the mining structure contains multiple tables, the list shows the names of the source tables.</span></span> <span data-ttu-id="b1df4-118">열 이름은 테이블을 선택한 후에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="b1df4-118">The column names do not display until a table has been selected.</span></span>  
  
     <span data-ttu-id="b1df4-119">마이닝 구조에 사례 테이블과 중첩 테이블이 포함된 경우 드롭다운 목록에 사례 테이블의 열과 중첩 테이블의 이름이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="b1df4-119">If the mining structure contains a case table and a nested table, the drop-down list shows columns from the case table, and the name of the nested table.</span></span>  
  
6.  <span data-ttu-id="b1df4-120">드롭다운 목록에서 열을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b1df4-120">Select a column from the drop-down list.</span></span>  
  
     <span data-ttu-id="b1df4-121">입력란의 왼쪽에 있는 아이콘이 변경되어 선택한 항목이 테이블인지 또는 열인지를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="b1df4-121">The icon at the left side of the text box changes to indicate that the selected item is a table or a column.</span></span>  
  
7.  <span data-ttu-id="b1df4-122">**연산자** 입력란을 클릭하고 목록에서 연산자를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b1df4-122">Click the **Operator** text box and select an operator from the list.</span></span> <span data-ttu-id="b1df4-123">선택한 열의 데이터 형식에 따라 유효한 연산자가 변경됩니다.</span><span class="sxs-lookup"><span data-stu-id="b1df4-123">The valid operators change depending on the data type of the column you selected.</span></span>  
  
8.  <span data-ttu-id="b1df4-124">**값** 입력란을 클릭하고 상자에 값을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="b1df4-124">Click the **Value** text box, and type a value in the box.</span></span>  
  
     <span data-ttu-id="b1df4-125">예를 들어을 `Income` 열로 선택 하 고 보다 큼 연산자 (>)를 선택한 다음을 입력 `30000` 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1df4-125">For example, select `Income` as the column, select the greater than operator (>), and then type `30000`.</span></span>  
  
9. <span data-ttu-id="b1df4-126">표에서 다음 행을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b1df4-126">Click the next row in the grid.</span></span>  
  
     <span data-ttu-id="b1df4-127">이전에 만든 필터 조건이 식 입력란에 자동으로 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="b1df4-127">The filter condition that you created is automatically added to the Expression text box.</span></span> <span data-ttu-id="b1df4-128">예를 들어 `[Income] > '30000'`</span><span class="sxs-lookup"><span data-stu-id="b1df4-128">For example, `[Income] > '30000'`</span></span>  
  
10. <span data-ttu-id="b1df4-129">표의 다음 행에서 **AND/OR** 입력란을 클릭하여 조건을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="b1df4-129">Click the **AND/OR** text box in the next row of the grid to add a condition.</span></span>  
  
     <span data-ttu-id="b1df4-130">예를 들어 BETWEEN 조건을 만들려면 `AND` 논리 피연산자의 드롭다운 목록에서를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1df4-130">For example, to create a BETWEEN condition, select `AND` from the drop-down list of logical operands.</span></span>  
  
11. <span data-ttu-id="b1df4-131">7-8단계의 설명에 따라 연산자를 선택하고 값을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="b1df4-131">Select an operator and type a value as described in Steps 7 and 8.</span></span>  
  
     <span data-ttu-id="b1df4-132">예를 들어를 `Income` 열로 다시 선택 하 고 보다 작음 연산자 (<)를 선택한 다음을 입력 `40000` 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1df4-132">For example, select `Income` as the column again, select the less than operator (<), and then type `40000`.</span></span>  
  
12. <span data-ttu-id="b1df4-133">표에서 다음 행을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b1df4-133">Click the next row in the grid.</span></span>  
  
13. <span data-ttu-id="b1df4-134">식 입력란의 필터 조건이 새 조건을 포함하도록 자동으로 업데이트됩니다.</span><span class="sxs-lookup"><span data-stu-id="b1df4-134">The filter condition in the Expression text box is automatically updated to include the new condition.</span></span> <span data-ttu-id="b1df4-135">전체 식은 `[Income] > '30000'AND [Income] < '40000'`</span><span class="sxs-lookup"><span data-stu-id="b1df4-135">The completed expression is as follows: `[Income] > '30000'AND [Income] < '40000'`</span></span>  
  
### <a name="to-add-a-filter-on-the-nested-table-in-a-mining-model"></a><span data-ttu-id="b1df4-136">마이닝 모델의 중첩 테이블에 필터를 추가하려면</span><span class="sxs-lookup"><span data-stu-id="b1df4-136">To add a filter on the nested table in a mining model</span></span>  
  
1.  <span data-ttu-id="b1df4-137">\*\* \<name> 모델 필터\*\* 대화 상자의 **마이닝 구조 열**아래에 있는 표의 빈 행을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1df4-137">In the **\<name>Model Filter** Dialog box, click an empty row in the grid under **Mining Structure Column**.</span></span>  
  
2.  <span data-ttu-id="b1df4-138">드롭다운 목록에서 중첩 테이블 이름을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b1df4-138">Select the name of the nested table from the drop-down list.</span></span>  
  
     <span data-ttu-id="b1df4-139">입력란의 왼쪽에 있는 아이콘이 변경되어 선택한 항목이 테이블 이름임을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="b1df4-139">The icon at the left side of the text box changes to indicate that the selected item is the name of a table.</span></span>  
  
3.  <span data-ttu-id="b1df4-140">**연산자** 입력란을 클릭하고 **포함** 또는 **포함하지 않음**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b1df4-140">Click the **Operator** text box and select **Contains** or **Not Contain**.</span></span>  
  
     <span data-ttu-id="b1df4-141">사례 테이블에서 중첩 테이블의 특정 값을 포함하는 사례만 허용하도록 지정했으므로 이러한 조건만 **모델 필터** 대화 상자의 중첩 테이블에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b1df4-141">These are the only conditions available for the nested table in the **Model Filter** dialog box, because you are restricting the case table to only those cases that contain a certain value in the nested table.</span></span> <span data-ttu-id="b1df4-142">다음 단계에서는 중첩 테이블의 조건에 대한 값을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="b1df4-142">You will set the value for the condition on the nested table in the next step.</span></span>  
  
4.  <span data-ttu-id="b1df4-143">**값** 상자를 클릭 한 다음 **(...)** 단추를 클릭 하 여 식을 작성 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1df4-143">Click the **Value** box, and then click the **(...)** button to build an expression.</span></span>  
  
     <span data-ttu-id="b1df4-144">\*\* \<name> 필터\*\* 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="b1df4-144">The **\<name>Filter** dialog box opens.</span></span> <span data-ttu-id="b1df4-145">이 대화 상자에서는 현재 테이블의 조건만 설정할 수 있습니다. 이 사례에서 현재 테이블은 중첩 테이블입니다.</span><span class="sxs-lookup"><span data-stu-id="b1df4-145">This dialog box can set conditions only on the current table, which in this case is the nested table.</span></span>  
  
5.  <span data-ttu-id="b1df4-146">**마이닝 구조 열** 상자를 클릭하고 중첩 테이블 열의 드롭다운 목록에서 열 이름을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b1df4-146">Click the **Mining Structure Column** box and select a column name from the dropdown lists of nested table columns.</span></span>  
  
6.  <span data-ttu-id="b1df4-147">**연산자** 를 클릭하고 열에 대한 올바른 연산자 목록에서 연산자를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b1df4-147">Click **Operator** and select an operator from the list of valid operators for the column.</span></span>  
  
7.  <span data-ttu-id="b1df4-148">**값** 을 클릭한 다음 값을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="b1df4-148">Click **Value** and type a value.</span></span>  
  
     <span data-ttu-id="b1df4-149">예를 들어 **마이닝 구조 열** 에 대해를 선택 `Model` 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1df4-149">For example, for **Mining Structure Column,** select `Model`.</span></span> <span data-ttu-id="b1df4-150">**연산자**에 대해 `<>` 를 선택 하 고 값을 입력 `Water Bottle` 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1df4-150">For **Operator**, select `<>`, and type the value `Water Bottle`.</span></span> <span data-ttu-id="b1df4-151">이 조건은 다음 필터 식을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b1df4-151">This condition creates the following filter expression:</span></span>  
  
```  
EXISTS (SELECT * FROM [<nested table name>] WHERE [Model] <> 'Water Bottle' )   
```  
  
> [!NOTE]  
>  <span data-ttu-id="b1df4-152">중첩 테이블 특성의 수는 잠재적으로 제한이 없기 때문에 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 는 선택 가능한 값 목록을 제공하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b1df4-152">Because the number of nested table attributes is potentially unlimited, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] does not supply a list of possible values from which to select.</span></span> <span data-ttu-id="b1df4-153">정확한 값을 입력해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1df4-153">You must type the exact value.</span></span> <span data-ttu-id="b1df4-154">또한 중첩 테이블에서는 LIKE 연산자를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b1df4-154">Also, you cannot use a LIKE operator in a nested table.</span></span>  
  
1.  <span data-ttu-id="b1df4-155">조건 `AND` `OR` 표의 왼쪽에 있는 **AND/or** 상자에서 **Conditions** 또는를 선택 하 여 조건을 결합 하 여 필요에 따라 조건을 더 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1df4-155">Add more conditions as necessary, combining the conditions by selecting `AND` or `OR` in the **AND/OR** box at the left side of the **Conditions** grid.</span></span> [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
2.  <span data-ttu-id="b1df4-156">**모델 필터** 대화 상자에서 **필터** 대화 상자를 사용하여 만든 조건을 검토합니다.</span><span class="sxs-lookup"><span data-stu-id="b1df4-156">In the **Model Filter** dialog box, review the conditions that you created by using the **Filter** dialog box.</span></span> <span data-ttu-id="b1df4-157">중첩 테이블의 조건이 사례 테이블의 조건에 추가되며 필터 조건의 전체 집합이 **식** 입력란에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="b1df4-157">The conditions for the nested table are appended to the conditions for the case table, and the complete set of filter conditions is displayed in the **Expression** text box.</span></span>  
  
3.  <span data-ttu-id="b1df4-158">필요에 따라 **쿼리 편집** 을 클릭하여 필터 식을 수동으로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="b1df4-158">Optionally, click **Edit Query** to manually change the filter expression.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="b1df4-159">필터 식의 임의 부분을 수동으로 변경하면 표가 비활성화되어 텍스트 편집 모드에서만 필터 식 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b1df4-159">If you change any part of a filter expression manually, the grid will be disabled and thereafter you must work with the filter expression in text edit mode only.</span></span> <span data-ttu-id="b1df4-160">표 편집 모드를 복원하려면 해당 필터 식을 지우고 다시 시작해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1df4-160">To restore grid editing mode, you must clear the filter expression and start over.</span></span>  
  
  
## <a name="see-also"></a><span data-ttu-id="b1df4-161">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b1df4-161">See Also</span></span>  
 <span data-ttu-id="b1df4-162">[마이닝 모델 &#40;Analysis Services 데이터 마이닝&#41;필터](mining-models-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="b1df4-162">[Filters for Mining Models &#40;Analysis Services - Data Mining&#41;](mining-models-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="b1df4-163">[마이닝 모델 태스크 및 방법](mining-model-tasks-and-how-tos.md) </span><span class="sxs-lookup"><span data-stu-id="b1df4-163">[Mining Model Tasks and How-tos](mining-model-tasks-and-how-tos.md) </span></span>  
 [<span data-ttu-id="b1df4-164">마이닝 모델에서 필터 삭제</span><span class="sxs-lookup"><span data-stu-id="b1df4-164">Delete a Filter from a Mining Model</span></span>](delete-a-filter-from-a-mining-model.md)  
  
  
