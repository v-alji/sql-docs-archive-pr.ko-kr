---
title: '6 단원: 계산 열 만들기 | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: d126766a-5699-4e9f-8213-8c7eea0fc14e
author: minewiskan
ms.author: owend
ms.openlocfilehash: dcebf61955e230c9e61c955683b897026553cb52
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649791"
---
# <a name="lesson-6-create-calculated-columns"></a><span data-ttu-id="12142-102">6단원: 계산 열 만들기</span><span class="sxs-lookup"><span data-stu-id="12142-102">Lesson 6: Create Calculated Columns</span></span>
  <span data-ttu-id="12142-103">이 단원에서는 계산 열을 추가하여 모델에 새 데이터를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="12142-103">In this lesson, you will create new data in your model by adding calculated columns.</span></span> <span data-ttu-id="12142-104">계산 열은 모델에 이미 있는 데이터를 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="12142-104">A calculated column is based on data that already exists in the model.</span></span> <span data-ttu-id="12142-105">자세한 내용은 [계산 열&#40;SSAS 테이블 형식&#41;](tabular-models/ssas-calculated-columns.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="12142-105">To learn more, see [Calculated Columns &#40;SSAS Tabular&#41;](tabular-models/ssas-calculated-columns.md).</span></span>  
  
 <span data-ttu-id="12142-106">서로 다른 세 테이블에 5개의 새 계산된 열을 만들겠습니다.</span><span class="sxs-lookup"><span data-stu-id="12142-106">You will create five new calculated columns in three different tables.</span></span> <span data-ttu-id="12142-107">태스크마다 단계가 조금씩 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="12142-107">The steps are slightly different for each task.</span></span> <span data-ttu-id="12142-108">이는 새 열을 만들고 열의 이름을 바꾸고 테이블의 다양한 위치에 열을 배치하는 데 여러 가지 방법이 있음을 보여 주기 위한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="12142-108">This is to show you there are several ways to create new columns, rename them, and place them in various locations in a table.</span></span>  
  
 <span data-ttu-id="12142-109">이 단원을 완료하기 위한 예상 시간: **15분**</span><span class="sxs-lookup"><span data-stu-id="12142-109">Estimated time to complete this lesson: **15 minutes**</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="12142-110">사전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="12142-110">Prerequisites</span></span>  
 <span data-ttu-id="12142-111">이 항목은 테이블 형식 모델링 자습서에 포함되며 순서대로 완료해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="12142-111">This topic is part of a tabular modeling tutorial, which should be completed in order.</span></span> <span data-ttu-id="12142-112">이 단원의 태스크를 수행하려면 이전 단원인 [5단원: 관계 만들기](lesson-4-create-relationships.md)를 완료해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="12142-112">Before performing the tasks in this lesson, you should have completed the previous lesson: [Lesson 5: Create Relationships](lesson-4-create-relationships.md).</span></span>  
  
## <a name="create-calculated-columns"></a><span data-ttu-id="12142-113">계산 열 만들기</span><span class="sxs-lookup"><span data-stu-id="12142-113">Create Calculated Columns</span></span>  
  
#### <a name="create-a-month-calendar-calculated-column-in-the-date-table"></a><span data-ttu-id="12142-114">Date 테이블에서 Month Calendar 계산 열 만들기</span><span class="sxs-lookup"><span data-stu-id="12142-114">Create a Month Calendar calculated column in the Date table</span></span>  
  
1.  <span data-ttu-id="12142-115">[!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]에서 **모델** 메뉴를 클릭하고 **모델 뷰**를 가리킨 다음 **데이터 보기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="12142-115">In [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], click the **Model** menu, then point to **Model View**, and then click **Data View**.</span></span>  
  
     <span data-ttu-id="12142-116">데이터 뷰에서는 모델 디자이너를 사용하여 계산 열만 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="12142-116">Calculated columns can only be created by using the model designer in Data View.</span></span>  
  
2.  <span data-ttu-id="12142-117">모델 디자이너에서 **Date** 테이블(탭)을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="12142-117">In the model designer, click the **Date** table (tab).</span></span>  
  
3.  <span data-ttu-id="12142-118">**Calendar Quarter** 열을 마우스 오른쪽 단추로 클릭 한 다음 **열 삽입**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="12142-118">Right-click the **Calendar Quarter** column, and then click **Insert Column**.</span></span>  
  
     <span data-ttu-id="12142-119">**CalculatedColumn1** 라는 새 열이 **Calendar Quarter** 열의 왼쪽에 삽입 됩니다.</span><span class="sxs-lookup"><span data-stu-id="12142-119">A new column named **CalculatedColumn1** is inserted to the left of the **Calendar Quarter** column.</span></span>  
  
4.  <span data-ttu-id="12142-120">테이블 위의 수식 입력줄에 다음 수식을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="12142-120">In the formula bar above the table, type the following formula.</span></span> <span data-ttu-id="12142-121">자동 완성을 통해 열 및 테이블의 정규화된 이름을 입력하고 사용 가능한 함수 목록을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="12142-121">AutoComplete helps you type the fully qualified names of columns and tables, and lists the functions that are available.</span></span>  
  
     `=RIGHT(" " & FORMAT([Month],"#0"), 2) & " - " & [Month Name]`  
  
     <span data-ttu-id="12142-122">수식 작성을 마쳤으면 Enter 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="12142-122">When you have finished building the formula, press ENTER.</span></span>  
  
     <span data-ttu-id="12142-123">그러면 계산된 열의 모든 행에 대한 값이 채워집니다.</span><span class="sxs-lookup"><span data-stu-id="12142-123">Values are then populated for all the rows in the calculated column.</span></span> <span data-ttu-id="12142-124">테이블을 아래로 스크롤하면, 각 행의 데이터에 따라 행이 이 열에 대해 서로 다른 값을 포함할 수 있는 것을 알게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="12142-124">If you scroll down through the table, you will see that rows can have different values for this column, based on the data that is in each row.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="12142-125">오류 메시지가 표시되면 수식의 열 이름이 [3단원: 열 이름 바꾸기](rename-columns.md)에서 변경한 열 이름과 일치하는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="12142-125">If you receive an error, verify the column names in the formula match the column names you changed in [Lesson 3: Rename Columns](rename-columns.md).</span></span>  
  
5.  <span data-ttu-id="12142-126">이 열의 이름을으로 바꿉니다 `Month Calendar` .</span><span class="sxs-lookup"><span data-stu-id="12142-126">Rename this column to `Month Calendar`.</span></span>  
  
 <span data-ttu-id="12142-127">Month Calendar 계산 열은 월에 대해 정렬 가능한 이름을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="12142-127">The Month Calendar calculated column provides a sortable name for Month.</span></span>  
  
#### <a name="create-a-day-of-week-calculated-column-in-the-date-table"></a><span data-ttu-id="12142-128">Date 테이블에서 Day of Week 계산 열 만들기</span><span class="sxs-lookup"><span data-stu-id="12142-128">Create a Day of Week calculated column in the Date table</span></span>  
  
1.  <span data-ttu-id="12142-129">**Date** 테이블을 활성화한 상태로 **열** 메뉴를 클릭한 다음 **열 추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="12142-129">With the **Date** table still active, click on the **Column** menu, and then click **Add Column**.</span></span>  
  
     <span data-ttu-id="12142-130">새 열이 테이블의 맨 오른쪽에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="12142-130">A new column is added to the far right of the table</span></span>  
  
2.  <span data-ttu-id="12142-131">수식 입력줄에 다음 수식을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="12142-131">In the formula bar, type the following formula:</span></span>  
  
     `=RIGHT(" " & FORMAT([Day Number Of Week],"#0"), 2) & " - " & [Day Name]`  
  
     <span data-ttu-id="12142-132">수식 작성을 마쳤으면 Enter 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="12142-132">When you have finished building the formula, press ENTER.</span></span>  
  
3.  <span data-ttu-id="12142-133">열의 이름을으로 바꿉니다 `Day of Week` .</span><span class="sxs-lookup"><span data-stu-id="12142-133">Rename the column to `Day of Week`.</span></span>  
  
4.  <span data-ttu-id="12142-134">열 제목을 클릭한 다음 열을 **Day Name** 열과 **Day of Month** 열 사이로 끕니다.</span><span class="sxs-lookup"><span data-stu-id="12142-134">Click on the column heading, and then drag the column between the **Day Name** column and the **Day of Month** column.</span></span>  
  
    > [!TIP]  
    >  <span data-ttu-id="12142-135">테이블에서 열을 이동하여 쉽게 탐색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="12142-135">Moving columns in your table makes it easier to navigate.</span></span>  
  
 <span data-ttu-id="12142-136">Day of Week 계산 열은 요일에 대해 정렬 가능한 이름을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="12142-136">The Day of Week calculated column provides a sortable name for the day of week.</span></span>  
  
#### <a name="create-a-product-subcategory-name-calculated-column-in-the-product-table"></a><span data-ttu-id="12142-137">Product 테이블에서 Product Subcategory Name 계산 열 만들기</span><span class="sxs-lookup"><span data-stu-id="12142-137">Create a Product Subcategory Name calculated column in the Product table</span></span>  
  
1.  <span data-ttu-id="12142-138">모델 디자이너에서 **Product** 테이블을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="12142-138">In the model designer, select the **Product** table.</span></span>  
  
2.  <span data-ttu-id="12142-139">테이블의 맨 오른쪽으로 스크롤합니다.</span><span class="sxs-lookup"><span data-stu-id="12142-139">Scroll to the far right of the table.</span></span> <span data-ttu-id="12142-140">맨 오른쪽 열 이름이 **열 추가**(기울임꼴)인 것을 확인하고 열 머리글을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="12142-140">Notice the right-most column is named **Add Column** (italicized), click the column heading.</span></span>  
  
3.  <span data-ttu-id="12142-141">수식 입력줄에 다음 수식을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="12142-141">In the formula bar, type the following formula.</span></span>  
  
     `=RELATED('Product Subcategory'[Product Subcategory Name])`  
  
     <span data-ttu-id="12142-142">수식 작성을 마쳤으면 Enter 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="12142-142">When you have finished building the formula, press ENTER.</span></span>  
  
4.  <span data-ttu-id="12142-143">열의 이름을으로 바꿉니다 `Product Subcategory Name` .</span><span class="sxs-lookup"><span data-stu-id="12142-143">Rename the column to `Product Subcategory Name`.</span></span>  
  
 <span data-ttu-id="12142-144">Product Subcategory Name 계산 열은 Product 테이블에서 Product Subcategory 테이블의 Product Subcategory Name 열에 있는 데이터가 포함된 계층을 만드는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="12142-144">The Product Subcategory Name calculated column is used to create a hierarchy in the Product table which includes data from the Product Subcategory Name column in the Product Subcategory table.</span></span> <span data-ttu-id="12142-145">계층 구조는 둘 이상의 테이블에 걸쳐 있을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="12142-145">Hierarchies cannot span more than one table.</span></span> <span data-ttu-id="12142-146">계층은 나중에 7단원에서 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="12142-146">You will create hierarchies later in Lesson 7.</span></span>  
  
#### <a name="create-a-product-category-name-calculated-column-in-the-product-table"></a><span data-ttu-id="12142-147">Product 테이블에서 Product Category Name 계산 열 만들기</span><span class="sxs-lookup"><span data-stu-id="12142-147">Create a Product Category Name calculated column in the Product table</span></span>  
  
1.  <span data-ttu-id="12142-148">**Product** 테이블을 활성화한 상태로 **열** 메뉴를 클릭한 다음 **열 추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="12142-148">With the **Product** table still active, click the **Column** menu, and then click **Add Column**.</span></span>  
  
2.  <span data-ttu-id="12142-149">수식 입력줄에 다음 수식을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="12142-149">In the formula bar, type the following formula:</span></span>  
  
     `=RELATED('Product Category'[Product Category Name])`  
  
     <span data-ttu-id="12142-150">수식 작성을 마쳤으면 Enter 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="12142-150">When you have finished building the formula, press ENTER.</span></span>  
  
3.  <span data-ttu-id="12142-151">열의 이름을으로 바꿉니다 `Product Category Name` .</span><span class="sxs-lookup"><span data-stu-id="12142-151">Rename the column to `Product Category Name`.</span></span>  
  
 <span data-ttu-id="12142-152">Product Category Name 계산 열은 Product 테이블에서 Product Category 테이블의 Product Category Name 열에 있는 데이터가 포함된 계층을 만드는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="12142-152">The Product Category Name calculated column is used to create a hierarchy in the Product table which includes data from the Product Category Name column in the Product Category table.</span></span> <span data-ttu-id="12142-153">계층 구조는 둘 이상의 테이블에 걸쳐 있을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="12142-153">Hierarchies cannot span more than one table.</span></span>  
  
#### <a name="create-a-margin-calculated-column-in-the-internet-sales-table"></a><span data-ttu-id="12142-154">Internet Sales 테이블에서 Margin 계산 열 만들기</span><span class="sxs-lookup"><span data-stu-id="12142-154">Create a Margin calculated column in the Internet Sales table</span></span>  
  
1.  <span data-ttu-id="12142-155">모델 디자이너에서 **Internet Sales** 테이블을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="12142-155">In the model designer, select the **Internet Sales** table.</span></span>  
  
2.  <span data-ttu-id="12142-156">새 열을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="12142-156">Add a new column.</span></span>  
  
3.  <span data-ttu-id="12142-157">수식 입력줄에 다음 수식을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="12142-157">In the formula bar, type the following formula:</span></span>  
  
     `=[Sales Amount]-[Total Product Cost]`  
  
     <span data-ttu-id="12142-158">수식 작성을 마쳤으면 Enter 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="12142-158">When you have finished building the formula, press ENTER.</span></span>  
  
4.  <span data-ttu-id="12142-159">열의 이름을으로 바꿉니다 `Margin` .</span><span class="sxs-lookup"><span data-stu-id="12142-159">Rename the column to `Margin`.</span></span>  
  
5.  <span data-ttu-id="12142-160">열을 **Sales Amount** 열과 **Tax Amt** 열 사이로 끕니다.</span><span class="sxs-lookup"><span data-stu-id="12142-160">Drag the column between the **Sales Amount** column and the **Tax Amt** column.</span></span>  
  
 <span data-ttu-id="12142-161">Margin 계산 열은 각(제품) 행의 매출이익률을 분석하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="12142-161">The Margin calculated column is used to analyze profit margins for each (product) row.</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="12142-162">다음 단계</span><span class="sxs-lookup"><span data-stu-id="12142-162">Next Step</span></span>  
 <span data-ttu-id="12142-163">이 단원을 계속하려면 다음 단원인 [7단원: 측정값 만들기](lesson-6-create-measures.md)로 이동하세요.</span><span class="sxs-lookup"><span data-stu-id="12142-163">To continue this lesson, go to the next lesson: [Lesson 7: Create Measures](lesson-6-create-measures.md).</span></span>  
  
  
