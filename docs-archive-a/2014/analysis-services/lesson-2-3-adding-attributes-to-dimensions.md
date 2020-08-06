---
title: 차원에 특성 추가 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 80551dad-97ac-40d0-90af-b810780321ce
author: minewiskan
ms.author: owend
ms.openlocfilehash: 76a04c42cc501fdca3e5ceb6481452052966796b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639038"
---
# <a name="adding-attributes-to-dimensions"></a><span data-ttu-id="bb2c7-102">차원에 특성 추가</span><span class="sxs-lookup"><span data-stu-id="bb2c7-102">Adding Attributes to Dimensions</span></span>
  <span data-ttu-id="bb2c7-103">이제 차원을 정의했으므로 차원의 각 데이터 요소를 나타내는 특성으로 차원을 채울 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bb2c7-103">Now that you have defined dimensions, you can populate them with attributes that represent each data element in the dimension.</span></span> <span data-ttu-id="bb2c7-104">일반적으로 특성은 데이터 원본 뷰의 필드를 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb2c7-104">Attributes are commonly based on fields from a data source view.</span></span> <span data-ttu-id="bb2c7-105">차원에 특성을 추가할 때 데이터 원본 뷰에 있는 테이블의 필드를 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bb2c7-105">When adding attributes to a dimension, you can include fields from any table in the data source view.</span></span>  
  
 <span data-ttu-id="bb2c7-106">이 태스크에서는 차원 디자이너를 사용하여 Customer 및 Product 차원에 특성을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="bb2c7-106">In this task, you will use Dimension Designer to add attributes to the Customer and Product dimensions.</span></span> <span data-ttu-id="bb2c7-107">Customer 차원에는 Customer 및 Geography 테이블의 필드를 기반으로 하는 특성이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="bb2c7-107">The Customer dimension will include attributes based on fields from both the Customer and Geography tables.</span></span>  
  
## <a name="adding-attributes-to-the-customer-dimension"></a><span data-ttu-id="bb2c7-108">Customer 차원에 특성 추가</span><span class="sxs-lookup"><span data-stu-id="bb2c7-108">Adding Attributes to the Customer Dimension</span></span>  
  
#### <a name="to-add-attributes"></a><span data-ttu-id="bb2c7-109">특성을 추가하려면</span><span class="sxs-lookup"><span data-stu-id="bb2c7-109">To add attributes</span></span>  
  
1.  <span data-ttu-id="bb2c7-110">Customer 차원에 대한 차원 디자이너를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="bb2c7-110">Open Dimension Designer for the Customer dimension.</span></span> <span data-ttu-id="bb2c7-111">이렇게 하려면 솔루션 탐색기의 **차원** 노드에서 **Customer** 차원을 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="bb2c7-111">To do this, double-click the **Customer** dimension in the **Dimensions** node of Solution Explorer.</span></span>  
  
2.  <span data-ttu-id="bb2c7-112">**특성** 창에서 큐브 마법사에 의해 만들어진 Customer Key 및 Geography Key 특성을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="bb2c7-112">In the **Attributes** pane, notice the Customer Key and Geography Key attributes that were created by the Cube Wizard.</span></span>  
  
3.  <span data-ttu-id="bb2c7-113">**차원 구조** 탭의 도구 모음에서 확대/축소 아이콘을 사용하여 **데이터 원본 뷰** 창의 테이블을 100%로 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bb2c7-113">On the toolbar of the **Dimension Structure** tab, make sure the Zoom icon to view the tables in the **Data Source View** pane is set at 100 percent.</span></span>  
  
4.  <span data-ttu-id="bb2c7-114">**데이터 원본 뷰** 창의 **Customer** 테이블에서 다음 열을 **특성** 창으로 끕니다.</span><span class="sxs-lookup"><span data-stu-id="bb2c7-114">Drag the following columns from the **Customer** table in the **Data Source View** pane to the **Attributes** pane:</span></span>  
  
    -   <span data-ttu-id="bb2c7-115">**BirthDate**</span><span class="sxs-lookup"><span data-stu-id="bb2c7-115">**BirthDate**</span></span>  
  
    -   <span data-ttu-id="bb2c7-116">**MaritalStatus**</span><span class="sxs-lookup"><span data-stu-id="bb2c7-116">**MaritalStatus**</span></span>  
  
    -   <span data-ttu-id="bb2c7-117">**성별**</span><span class="sxs-lookup"><span data-stu-id="bb2c7-117">**Gender**</span></span>  
  
    -   <span data-ttu-id="bb2c7-118">**EmailAddress**</span><span class="sxs-lookup"><span data-stu-id="bb2c7-118">**EmailAddress**</span></span>  
  
    -   <span data-ttu-id="bb2c7-119">**YearlyIncome**</span><span class="sxs-lookup"><span data-stu-id="bb2c7-119">**YearlyIncome**</span></span>  
  
    -   <span data-ttu-id="bb2c7-120">**TotalChildren**</span><span class="sxs-lookup"><span data-stu-id="bb2c7-120">**TotalChildren**</span></span>  
  
    -   <span data-ttu-id="bb2c7-121">**NumberChildrenAtHome**</span><span class="sxs-lookup"><span data-stu-id="bb2c7-121">**NumberChildrenAtHome**</span></span>  
  
    -   <span data-ttu-id="bb2c7-122">**EnglishEducation**</span><span class="sxs-lookup"><span data-stu-id="bb2c7-122">**EnglishEducation**</span></span>  
  
    -   <span data-ttu-id="bb2c7-123">**EnglishOccupation**</span><span class="sxs-lookup"><span data-stu-id="bb2c7-123">**EnglishOccupation**</span></span>  
  
    -   <span data-ttu-id="bb2c7-124">**HouseOwnerFlag**</span><span class="sxs-lookup"><span data-stu-id="bb2c7-124">**HouseOwnerFlag**</span></span>  
  
    -   <span data-ttu-id="bb2c7-125">**NumberCarsOwned**</span><span class="sxs-lookup"><span data-stu-id="bb2c7-125">**NumberCarsOwned**</span></span>  
  
    -   <span data-ttu-id="bb2c7-126">**내선**</span><span class="sxs-lookup"><span data-stu-id="bb2c7-126">**Phone**</span></span>  
  
    -   <span data-ttu-id="bb2c7-127">**DateFirstPurchase**</span><span class="sxs-lookup"><span data-stu-id="bb2c7-127">**DateFirstPurchase**</span></span>  
  
    -   <span data-ttu-id="bb2c7-128">**CommuteDistance**</span><span class="sxs-lookup"><span data-stu-id="bb2c7-128">**CommuteDistance**</span></span>  
  
5.  <span data-ttu-id="bb2c7-129">**데이터 원본 뷰** 창의 **Geography** 테이블에서 다음 열을 **특성** 창으로 끕니다.</span><span class="sxs-lookup"><span data-stu-id="bb2c7-129">Drag the following columns from the **Geography** table in the **Data Source View** pane to the **Attributes** pane:</span></span>  
  
    -   <span data-ttu-id="bb2c7-130">**도시**</span><span class="sxs-lookup"><span data-stu-id="bb2c7-130">**City**</span></span>  
  
    -   <span data-ttu-id="bb2c7-131">**StateProvinceName**</span><span class="sxs-lookup"><span data-stu-id="bb2c7-131">**StateProvinceName**</span></span>  
  
    -   <span data-ttu-id="bb2c7-132">**EnglishCountryRegionName**</span><span class="sxs-lookup"><span data-stu-id="bb2c7-132">**EnglishCountryRegionName**</span></span>  
  
    -   <span data-ttu-id="bb2c7-133">**PostalCode**</span><span class="sxs-lookup"><span data-stu-id="bb2c7-133">**PostalCode**</span></span>  
  
6.  <span data-ttu-id="bb2c7-134">파일 메뉴에서 **모두 저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="bb2c7-134">On the File menu, click **Save All**.</span></span>  
  
## <a name="adding-attributes-to-the-product-dimension"></a><span data-ttu-id="bb2c7-135">Product 차원에 특성 추가</span><span class="sxs-lookup"><span data-stu-id="bb2c7-135">Adding Attributes to the Product Dimension</span></span>  
  
#### <a name="to-add-attributes"></a><span data-ttu-id="bb2c7-136">특성을 추가하려면</span><span class="sxs-lookup"><span data-stu-id="bb2c7-136">To add attributes</span></span>  
  
1.  <span data-ttu-id="bb2c7-137">Product 차원에 대한 차원 디자이너를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="bb2c7-137">Open Dimension Designer for the Product dimension.</span></span> <span data-ttu-id="bb2c7-138">솔루션 탐색기에서 **Product** 차원을 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="bb2c7-138">Double-click the **Product** dimension in Solution Explorer.</span></span>  
  
2.  <span data-ttu-id="bb2c7-139">**특성** 창에서 큐브 마법사에 의해 만들어진 Product Key 특성을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="bb2c7-139">In the **Attributes** pane, notice the Product Key attribute that was created by the Cube Wizard.</span></span>  
  
3.  <span data-ttu-id="bb2c7-140">**차원 구조** 탭의 도구 모음에서 확대/축소 아이콘을 사용하여 **데이터 원본 뷰** 창의 테이블을 100%로 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bb2c7-140">On the toolbar of the **Dimension Structure** tab, make sure the Zoom icon to view the tables in the **Data Source View** pane is set at 100 percent.</span></span>  
  
4.  <span data-ttu-id="bb2c7-141">**데이터 원본 뷰** 창의 **Product** 테이블에서 다음 열을 **특성** 창으로 끕니다.</span><span class="sxs-lookup"><span data-stu-id="bb2c7-141">Drag the following columns from the **Product** table in the **Data Source View** pane to the **Attributes** pane:</span></span>  
  
    -   <span data-ttu-id="bb2c7-142">**StandardCost**</span><span class="sxs-lookup"><span data-stu-id="bb2c7-142">**StandardCost**</span></span>  
  
    -   <span data-ttu-id="bb2c7-143">**색상**</span><span class="sxs-lookup"><span data-stu-id="bb2c7-143">**Color**</span></span>  
  
    -   <span data-ttu-id="bb2c7-144">**SafetyStockLevel**</span><span class="sxs-lookup"><span data-stu-id="bb2c7-144">**SafetyStockLevel**</span></span>  
  
    -   <span data-ttu-id="bb2c7-145">**ReorderPoint**</span><span class="sxs-lookup"><span data-stu-id="bb2c7-145">**ReorderPoint**</span></span>  
  
    -   <span data-ttu-id="bb2c7-146">**ListPrice**</span><span class="sxs-lookup"><span data-stu-id="bb2c7-146">**ListPrice**</span></span>  
  
    -   <span data-ttu-id="bb2c7-147">**크기**</span><span class="sxs-lookup"><span data-stu-id="bb2c7-147">**Size**</span></span>  
  
    -   <span data-ttu-id="bb2c7-148">**SizeRange**</span><span class="sxs-lookup"><span data-stu-id="bb2c7-148">**SizeRange**</span></span>  
  
    -   <span data-ttu-id="bb2c7-149">**Weight**</span><span class="sxs-lookup"><span data-stu-id="bb2c7-149">**Weight**</span></span>  
  
    -   <span data-ttu-id="bb2c7-150">**DaysToManufacture**</span><span class="sxs-lookup"><span data-stu-id="bb2c7-150">**DaysToManufacture**</span></span>  
  
    -   <span data-ttu-id="bb2c7-151">**ProductLine**</span><span class="sxs-lookup"><span data-stu-id="bb2c7-151">**ProductLine**</span></span>  
  
    -   <span data-ttu-id="bb2c7-152">**DealerPrice**</span><span class="sxs-lookup"><span data-stu-id="bb2c7-152">**DealerPrice**</span></span>  
  
    -   <span data-ttu-id="bb2c7-153">**클래스**</span><span class="sxs-lookup"><span data-stu-id="bb2c7-153">**Class**</span></span>  
  
    -   <span data-ttu-id="bb2c7-154">**Style**</span><span class="sxs-lookup"><span data-stu-id="bb2c7-154">**Style**</span></span>  
  
    -   <span data-ttu-id="bb2c7-155">**ModelName**</span><span class="sxs-lookup"><span data-stu-id="bb2c7-155">**ModelName**</span></span>  
  
    -   <span data-ttu-id="bb2c7-156">**StartDate**</span><span class="sxs-lookup"><span data-stu-id="bb2c7-156">**StartDate**</span></span>  
  
    -   <span data-ttu-id="bb2c7-157">**EndDate**</span><span class="sxs-lookup"><span data-stu-id="bb2c7-157">**EndDate**</span></span>  
  
    -   <span data-ttu-id="bb2c7-158">**상태**</span><span class="sxs-lookup"><span data-stu-id="bb2c7-158">**Status**</span></span>  
  
5.  <span data-ttu-id="bb2c7-159">파일 메뉴에서 **모두 저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="bb2c7-159">On the File menu, click **Save All**.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="bb2c7-160">단원의 다음 태스크</span><span class="sxs-lookup"><span data-stu-id="bb2c7-160">Next Task in Lesson</span></span>  
 [<span data-ttu-id="bb2c7-161">큐브 및 차원 속성 검토</span><span class="sxs-lookup"><span data-stu-id="bb2c7-161">Reviewing Cube and Dimension Properties</span></span>](lesson-2-4-reviewing-cube-and-dimension-properties.md)  
  
## <a name="see-also"></a><span data-ttu-id="bb2c7-162">참고 항목</span><span class="sxs-lookup"><span data-stu-id="bb2c7-162">See Also</span></span>  
 [<span data-ttu-id="bb2c7-163">차원 특성 속성 참조</span><span class="sxs-lookup"><span data-stu-id="bb2c7-163">Dimension Attribute Properties Reference</span></span>](multidimensional-models/dimension-attribute-properties-reference.md)  
  
  
