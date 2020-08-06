---
title: '10 단원: 계층 만들기 | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 1e2561d3-4890-4495-a9cd-84eb88508938
author: minewiskan
ms.author: owend
ms.openlocfilehash: 4d0982a05c37c28167e44e3f9f082ea5113b59bf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87732175"
---
# <a name="lesson-10-create-hierarchies"></a><span data-ttu-id="6541c-102">10단원: 계층 만들기</span><span class="sxs-lookup"><span data-stu-id="6541c-102">Lesson 10: Create Hierarchies</span></span>
  <span data-ttu-id="6541c-103">이 단원에서는 계층을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="6541c-103">In this lesson, you will create hierarchies.</span></span> <span data-ttu-id="6541c-104">계층은 수준별로 정렬된 열 그룹입니다. 예를 들어 Geography 계층에는 Country, State, County 및 City에 대한 하위 수준이 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6541c-104">Hierarchies are groups of columns arranged in levels; for example, a Geography hierarchy might have sub-levels for Country, State, County, and City.</span></span> <span data-ttu-id="6541c-105">계층은 보고 클라이언트 애플리케이션 필드 목록에서 다른 열과는 별도로 표시되므로 클라이언트 사용자가 손쉽게 탐색하여 보고서에 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6541c-105">Hierarchies can appear separate from other columns in a reporting client application field list, making them easier for client users to navigate and include in a report.</span></span> <span data-ttu-id="6541c-106">자세한 내용은 [계층 구조&#40;SSAS 테이블 형식&#41;](tabular-models/hierarchies-ssas-tabular.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6541c-106">To learn more, see [Hierarchies &#40;SSAS Tabular&#41;](tabular-models/hierarchies-ssas-tabular.md).</span></span>  
  
 <span data-ttu-id="6541c-107">계층을 만들려면 *다이어그램 뷰*에서 모델 디자이너를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="6541c-107">To create hierarchies, you will use the model designer in *Diagram View*.</span></span> <span data-ttu-id="6541c-108">계층 만들기 및 관리는 데이터 뷰의 모델 디자이너에서는 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6541c-108">Creating and managing hierarchies is not supported in the model designer in Data View.</span></span>  
  
 <span data-ttu-id="6541c-109">이 단원을 완료하기 위한 예상 시간: **20분**</span><span class="sxs-lookup"><span data-stu-id="6541c-109">Estimated time to complete this lesson: **20 minutes**</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="6541c-110">사전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="6541c-110">Prerequisites</span></span>  
 <span data-ttu-id="6541c-111">이 항목은 테이블 형식 모델링 자습서에 포함되며 순서대로 완료해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6541c-111">This topic is part of a tabular modeling tutorial, which should be completed in order.</span></span> <span data-ttu-id="6541c-112">이 단원의 태스크를 수행하려면 이전 단원인 [9단원: 큐브 뷰 만들기](lesson-8-create-perspectives.md)를 완료해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6541c-112">Before performing the tasks in this lesson, you should have completed the previous lesson: [Lesson 9: Create Perspectives](lesson-8-create-perspectives.md).</span></span>  
  
## <a name="create-hierarchies"></a><span data-ttu-id="6541c-113">계층 만들기</span><span class="sxs-lookup"><span data-stu-id="6541c-113">Create Hierarchies</span></span>  
  
#### <a name="to-create-a-category-hierarchy-in-the-product-table"></a><span data-ttu-id="6541c-114">Product 테이블에서 Category 계층을 만들려면</span><span class="sxs-lookup"><span data-stu-id="6541c-114">To create a Category hierarchy in the Product table</span></span>  
  
1.  <span data-ttu-id="6541c-115">모델 디자이너에서 메뉴를 클릭 하 고 `Model` **모델 뷰**를 가리킨 다음 **다이어그램 뷰**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="6541c-115">In the model designer, click on the `Model` menu, then point to **Model View**, and then click **Diagram View**.</span></span>  
  
    > [!TIP]  
    >  <span data-ttu-id="6541c-116">모델 디자이너 오른쪽 위 모퉁이에 있는 미니맵 컨트롤을 사용하여 다이어그램 뷰에서의 개체 표시 방식을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6541c-116">Use the Minimap controls at the top-right of the model designer to change how you can view objects in Diagram View.</span></span> <span data-ttu-id="6541c-117">다이어그램 뷰에서 개체 위치를 변경하면 프로젝트를 저장할 때 해당 뷰가 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="6541c-117">If you reposition objects in Diagram View, that view will be retained when you save the project.</span></span>  
  
2.  <span data-ttu-id="6541c-118">모델 디자이너에서 테이블을 마우스 오른쪽 단추로 클릭 한 `Product` 다음 **계층 만들기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="6541c-118">In the model designer, right-click the `Product` table, and then click **Create Hierarchy**.</span></span> <span data-ttu-id="6541c-119">새 계층이 테이블 창의 아래쪽에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="6541c-119">A new hierarchy appears at the bottom of the table window.</span></span>  
  
3.  <span data-ttu-id="6541c-120">계층 이름에서를 입력 하 여 계층 이름을 바꾸고 `Category` enter 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="6541c-120">In the hierarchy name, rename the hierarchy by typing `Category`, and then press ENTER.</span></span>  
  
4.  <span data-ttu-id="6541c-121">테이블에서 `Product` **Product Category Name** 열을 클릭 한 다음 계층으로 끌고 `Category` 이름 위에 놓습니다 `Category` .</span><span class="sxs-lookup"><span data-stu-id="6541c-121">In the `Product` table, click the **Product Category Name** column, then drag it to the `Category` hierarchy, and then release on top of the `Category` name.</span></span>  
  
5.  <span data-ttu-id="6541c-122">계층에서 `Category` **Product Category Name** 열을 마우스 오른쪽 단추로 클릭 한 다음 **이름 바꾸기**를 클릭 하 고을 입력 `Category` 합니다.</span><span class="sxs-lookup"><span data-stu-id="6541c-122">In the `Category` hierarchy, right-click the **Product Category Name** column, then click **Rename**, and then type `Category`.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="6541c-123">계층에서 열 이름을 바꿔도 테이블의 열 이름은 바뀌지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6541c-123">Renaming a column in a hierarchy does not rename that column in the table.</span></span> <span data-ttu-id="6541c-124">계층의 열은 테이블 열에 대한 표현일 뿐입니다.</span><span class="sxs-lookup"><span data-stu-id="6541c-124">A column in a hierarchy is just a representation of the column in the table.</span></span>  
  
6.  <span data-ttu-id="6541c-125">테이블에서 `Product` **Product 하위 범주 이름** 열을 마우스 오른쪽 단추로 클릭 하 고 상황에 맞는 메뉴에서 **계층에 추가**를 가리킨 다음를 클릭 `Category` 합니다.</span><span class="sxs-lookup"><span data-stu-id="6541c-125">In the `Product` table, right-click the **Product Subcategory Name** column, then in the context menu, point to **Add to Hierarchy**, and then click `Category`.</span></span>  
  
7.  <span data-ttu-id="6541c-126">**Product 하위 범주 이름을** 으로 바꿉니다 `Subcategory` .</span><span class="sxs-lookup"><span data-stu-id="6541c-126">Rename **Product Subcategory Name** to `Subcategory`.</span></span>  
  
8.  <span data-ttu-id="6541c-127">클릭 및 끌기를 사용 하거나 상황에 맞는 메뉴에서 **계층에 추가** 명령을 사용 하 여 **모델 이름** 및 **product name** 열을 순서 대로 추가 하 고 **product 하위 범주 이름** 열 아래에 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="6541c-127">By using click and drag, or by using the **Add to Hierarchy** command in the context menu, add the **Model Name** and **Product Name** columns (in order) and place them beneath the **Product Subcategory Name** column.</span></span> <span data-ttu-id="6541c-128">이러한 열의 이름을 `Model` `Product` 각각로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="6541c-128">Rename these columns `Model` and `Product`, respectively.</span></span>  
  
#### <a name="to-create-hierarchies-in-the-date-table"></a><span data-ttu-id="6541c-129">Date 테이블에서 계층을 만들려면</span><span class="sxs-lookup"><span data-stu-id="6541c-129">To create hierarchies in the Date table</span></span>  
  
1.  <span data-ttu-id="6541c-130">모델 디자이너에서 **Date** 테이블을 마우스 오른쪽 단추로 클릭한 다음 **계층 만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6541c-130">In the model designer, right-click the **Date** table, and then click **Create Hierarchy**.</span></span>  
  
2.  <span data-ttu-id="6541c-131">계층 이름을 **Calendar**로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="6541c-131">Rename the hierarchy to **Calendar**.</span></span>  
  
3.  <span data-ttu-id="6541c-132">다음 열을 순서대로 추가하고 이름을 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="6541c-132">Add the following columns, in-order, and then rename them:</span></span>  
  
    |<span data-ttu-id="6541c-133">열</span><span class="sxs-lookup"><span data-stu-id="6541c-133">Column</span></span>|<span data-ttu-id="6541c-134">바꾼 후 이름</span><span class="sxs-lookup"><span data-stu-id="6541c-134">Rename to:</span></span>|  
    |------------|----------------|  
    |<span data-ttu-id="6541c-135">Calendar Year</span><span class="sxs-lookup"><span data-stu-id="6541c-135">Calendar Year</span></span>|<span data-ttu-id="6541c-136">Year</span><span class="sxs-lookup"><span data-stu-id="6541c-136">Year</span></span>|  
    |<span data-ttu-id="6541c-137">Calendar Semester</span><span class="sxs-lookup"><span data-stu-id="6541c-137">Calendar Semester</span></span>|<span data-ttu-id="6541c-138">Semester</span><span class="sxs-lookup"><span data-stu-id="6541c-138">Semester</span></span>|  
    |<span data-ttu-id="6541c-139">Calendar Quarter</span><span class="sxs-lookup"><span data-stu-id="6541c-139">Calendar Quarter</span></span>|<span data-ttu-id="6541c-140">Quarter</span><span class="sxs-lookup"><span data-stu-id="6541c-140">Quarter</span></span>|  
    |<span data-ttu-id="6541c-141">Month Calendar</span><span class="sxs-lookup"><span data-stu-id="6541c-141">Month Calendar</span></span>|<span data-ttu-id="6541c-142">월</span><span class="sxs-lookup"><span data-stu-id="6541c-142">Month</span></span>|  
    |<span data-ttu-id="6541c-143">Day Of Month</span><span class="sxs-lookup"><span data-stu-id="6541c-143">Day Of Month</span></span>|<span data-ttu-id="6541c-144">일</span><span class="sxs-lookup"><span data-stu-id="6541c-144">Day</span></span>|  
  
4.  <span data-ttu-id="6541c-145">**Date** 테이블에서 위의 단계를 반복하여 다음 열이 포함된 **Fiscal** 계층을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="6541c-145">In the **Date** table, repeat the above steps, creating a **Fiscal** hierarchy, including the following columns:</span></span>  
  
    |<span data-ttu-id="6541c-146">열</span><span class="sxs-lookup"><span data-stu-id="6541c-146">Column</span></span>|<span data-ttu-id="6541c-147">바꾼 후 이름</span><span class="sxs-lookup"><span data-stu-id="6541c-147">Rename to:</span></span>|  
    |------------|----------------|  
    |<span data-ttu-id="6541c-148">Fiscal Year</span><span class="sxs-lookup"><span data-stu-id="6541c-148">Fiscal Year</span></span>|<span data-ttu-id="6541c-149">Year</span><span class="sxs-lookup"><span data-stu-id="6541c-149">Year</span></span>|  
    |<span data-ttu-id="6541c-150">Fiscal Semester</span><span class="sxs-lookup"><span data-stu-id="6541c-150">Fiscal Semester</span></span>|<span data-ttu-id="6541c-151">Semester</span><span class="sxs-lookup"><span data-stu-id="6541c-151">Semester</span></span>|  
    |<span data-ttu-id="6541c-152">Fiscal Quarter</span><span class="sxs-lookup"><span data-stu-id="6541c-152">Fiscal Quarter</span></span>|<span data-ttu-id="6541c-153">Quarter</span><span class="sxs-lookup"><span data-stu-id="6541c-153">Quarter</span></span>|  
    |<span data-ttu-id="6541c-154">Month Calendar</span><span class="sxs-lookup"><span data-stu-id="6541c-154">Month Calendar</span></span>|<span data-ttu-id="6541c-155">월</span><span class="sxs-lookup"><span data-stu-id="6541c-155">Month</span></span>|  
    |<span data-ttu-id="6541c-156">Day Of Month</span><span class="sxs-lookup"><span data-stu-id="6541c-156">Day Of Month</span></span>|<span data-ttu-id="6541c-157">일</span><span class="sxs-lookup"><span data-stu-id="6541c-157">Day</span></span>|  
  
5.  <span data-ttu-id="6541c-158">마지막으로 **Date** 테이블에서 위의 단계를 반복하여 다음 열이 포함된 **Production Calendar** 계층을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="6541c-158">Finally, in the **Date** table, repeat the above steps, creating a **Production Calendar** hierarchy, including the following columns:</span></span>  
  
    |<span data-ttu-id="6541c-159">열</span><span class="sxs-lookup"><span data-stu-id="6541c-159">Column</span></span>|<span data-ttu-id="6541c-160">바꾼 후 이름</span><span class="sxs-lookup"><span data-stu-id="6541c-160">Rename to:</span></span>|  
    |------------|----------------|  
    |<span data-ttu-id="6541c-161">Calendar Year</span><span class="sxs-lookup"><span data-stu-id="6541c-161">Calendar Year</span></span>|<span data-ttu-id="6541c-162">Year</span><span class="sxs-lookup"><span data-stu-id="6541c-162">Year</span></span>|  
    |<span data-ttu-id="6541c-163">Week Number Of Year</span><span class="sxs-lookup"><span data-stu-id="6541c-163">Week Number Of Year</span></span>|<span data-ttu-id="6541c-164">주</span><span class="sxs-lookup"><span data-stu-id="6541c-164">Week</span></span>|  
    |<span data-ttu-id="6541c-165">Day Of Week</span><span class="sxs-lookup"><span data-stu-id="6541c-165">Day Of Week</span></span>|<span data-ttu-id="6541c-166">일</span><span class="sxs-lookup"><span data-stu-id="6541c-166">Day</span></span>|  
  
## <a name="next-steps"></a><span data-ttu-id="6541c-167">다음 단계</span><span class="sxs-lookup"><span data-stu-id="6541c-167">Next Steps</span></span>  
 <span data-ttu-id="6541c-168">이 자습서를 계속하려면 다음 단원인 [11단원: 파티션 만들기](lesson-10-create-partitions.md)로 이동하세요.</span><span class="sxs-lookup"><span data-stu-id="6541c-168">To continue this tutorial, go to the next lesson: [Lesson 11: Create Partitions](lesson-10-create-partitions.md).</span></span>  
  
  
