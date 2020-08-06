---
title: Product 차원 수정 | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 8e3ffecd-7f40-41a8-8735-bc9858a310cb
author: minewiskan
ms.author: owend
ms.openlocfilehash: 04c0a778a73371dada92c9ff207a17366a2fbc7f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652431"
---
# <a name="modifying-the-product-dimension"></a><span data-ttu-id="1c8a4-102">Product 차원 수정</span><span class="sxs-lookup"><span data-stu-id="1c8a4-102">Modifying the Product Dimension</span></span>
  <span data-ttu-id="1c8a4-103">이 항목의 태스크에서는 명명된 계산을 사용하여 제품 라인에 대해 보다 설명적인 이름을 제공하고 Product 차원에 계층을 정의하고 계층에 대해 (All) 멤버 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="1c8a4-103">In the tasks in this topic, you use a named calculation to provide more descriptive names for the product lines, define a hierarchy in the Product dimension, and specify the (All) member name for the hierarchy.</span></span> <span data-ttu-id="1c8a4-104">또한 특성을 표시 폴더로 그룹화합니다.</span><span class="sxs-lookup"><span data-stu-id="1c8a4-104">You also group attributes into display folders.</span></span>  
  
## <a name="adding-a-named-calculation"></a><span data-ttu-id="1c8a4-105">명명된 계산 추가</span><span class="sxs-lookup"><span data-stu-id="1c8a4-105">Adding a Named Calculation</span></span>  
 <span data-ttu-id="1c8a4-106">데이터 원본 뷰에서 테이블에 명명된 계산을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1c8a4-106">You can add a named calculation to a table in a data source view.</span></span> <span data-ttu-id="1c8a4-107">다음 태스크에서는 전체 제품 라인 이름을 표시하는 명명된 계산을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="1c8a4-107">In the following task, you create a named calculation that displays the full product line name.</span></span>  
  
#### <a name="to-add-a-named-calculation"></a><span data-ttu-id="1c8a4-108">명명된 계산을 추가하려면</span><span class="sxs-lookup"><span data-stu-id="1c8a4-108">To add a named calculation</span></span>  
  
1.  <span data-ttu-id="1c8a4-109">**Adventure Works DW 2012** 데이터 원본 뷰를 열려면 솔루션 탐색기의 **데이터 원본 뷰** 폴더에서 **Adventure Works DW 2012** 를 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1c8a4-109">To open the **Adventure Works DW 2012** data source view, double-click **Adventure Works DW 2012** in the **Data Source Views** folder in Solution Explorer.</span></span>  
  
2.  <span data-ttu-id="1c8a4-110">다이어그램 창의 맨 아래에서 **Product** 테이블 머리글을 마우스 오른쪽 단추로 클릭한 다음 **새 명명된 계산**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1c8a4-110">In the bottom of the diagram pane, right-click the **Product** table header, and then click **New Named Calculation**.</span></span>  
  
3.  <span data-ttu-id="1c8a4-111">**명명 된 계산 만들기** 대화 상자에서 `ProductLineName` **열 이름** 상자에을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c8a4-111">In the **Create Named Calculation** dialog box, type `ProductLineName` in the **Column name** box.</span></span>  
  
4.  <span data-ttu-id="1c8a4-112">**식** 상자에 다음 **CASE** 문을 입력하거나 복사하여 붙여넣습니다.</span><span class="sxs-lookup"><span data-stu-id="1c8a4-112">In the **Expression** box, type or copy and paste the following **CASE** statement:</span></span>  
  
    ```  
    CASE ProductLine  
       WHEN 'M' THEN 'Mountain'  
       WHEN 'R' THEN 'Road'  
       WHEN 'S' THEN 'Accessory'  
       WHEN 'T' THEN 'Touring'  
       ELSE 'Components'  
    END  
    ```  
  
     <span data-ttu-id="1c8a4-113">이 **CASE** 문은 큐브의 각 제품 라인에 대해 알기 쉬운 이름을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="1c8a4-113">This **CASE** statement creates user-friendly names for each product line in the cube.</span></span>  
  
5.  <span data-ttu-id="1c8a4-114">**확인** 을 클릭 하 여 `ProductLineName` 명명 된 계산을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="1c8a4-114">Click **OK** to create the `ProductLineName` named calculation.</span></span> <span data-ttu-id="1c8a4-115">기다려야 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1c8a4-115">You might need to wait.</span></span>  
  
6.  <span data-ttu-id="1c8a4-116">**파일** 메뉴에서 **모두 저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1c8a4-116">On the **File** menu, click **Save All**.</span></span>  
  
## <a name="modifying-the-namecolumn-property-of-an-attribute"></a><span data-ttu-id="1c8a4-117">특성의 NameColumn 속성 수정</span><span class="sxs-lookup"><span data-stu-id="1c8a4-117">Modifying the NameColumn Property of an Attribute</span></span>  
  
#### <a name="to-modify-the-namecolumn-property-value-of-an-attribute"></a><span data-ttu-id="1c8a4-118">특성의 NameColumn 속성 값을 수정하려면</span><span class="sxs-lookup"><span data-stu-id="1c8a4-118">To modify the NameColumn property value of an attribute</span></span>  
  
1.  <span data-ttu-id="1c8a4-119">Product 차원에 대한 차원 디자이너로 전환합니다.</span><span class="sxs-lookup"><span data-stu-id="1c8a4-119">Switch to Dimension Designer for the Product dimension.</span></span> <span data-ttu-id="1c8a4-120">이렇게 하려면 솔루션 탐색기의 **차원** 노드에서 **Product** 차원을 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1c8a4-120">To do this, double-click the **Product** dimension in the **Dimensions** node of Solution Explorer.</span></span>  
  
2.  <span data-ttu-id="1c8a4-121">**차원 구조** 탭의 **특성** 창에서 **Product Line**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="1c8a4-121">In the **Attributes** pane of the **Dimension Structure** tab, select **Product Line**.</span></span>  
  
3.  <span data-ttu-id="1c8a4-122">화면 오른쪽에 있는 속성 창에서 창 맨 아래에 있는 **NameColumn** 속성 필드를 클릭 한 다음 찾아보기 (**...**) 단추를 클릭 하 여 **이름 열** 대화 상자를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="1c8a4-122">In the Properties window on the right side of the screen, click the **NameColumn** property field at the bottom of the window, and then click the browse (**...**) button to open the **Name Column** dialog box.</span></span> <span data-ttu-id="1c8a4-123">화면 오른쪽의 **속성** 탭을 클릭하여 속성 창을 열어야 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1c8a4-123">(You might need to click the **Properties** tab on the right side of the screen to open the Properties window.</span></span>  
  
4.  <span data-ttu-id="1c8a4-124">`ProductLineName` **원본 열** 목록의 맨 아래에서를 선택 하 고 **확인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c8a4-124">Select `ProductLineName` at the bottom of the **Source column** list, and then click **OK**.</span></span>  
  
     <span data-ttu-id="1c8a4-125">이제 NameColumn 필드에 **Product.ProductLineName (WChar)** 텍스트가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="1c8a4-125">The NameColumn field now contains the text, **Product.ProductLineName (WChar)**.</span></span> <span data-ttu-id="1c8a4-126">**Product Line** 특성 계층의 멤버가 약식 제품 라인 이름이 아니라 전체 제품 라인 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="1c8a4-126">The members of the **Product Line** attribute hierarchy now display the full name of the product line instead of an abbreviated product line name.</span></span>  
  
5.  <span data-ttu-id="1c8a4-127">**차원 구조** 탭의 **특성** 창에서 **Product Key**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="1c8a4-127">In the **Attributes** pane of the **Dimension Structure** tab, select **Product Key**.</span></span>  
  
6.  <span data-ttu-id="1c8a4-128">속성 창에서 **NameColumn** 속성 필드를 클릭 한 다음 줄임표 (**...**) 단추를 클릭 하 여 **이름 열** 대화 상자를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="1c8a4-128">In the Properties window, click the **NameColumn** property field, and then click the ellipsis browse (**...**) button to open the **Name Column** dialog box.</span></span>  
  
7.  <span data-ttu-id="1c8a4-129">**원본 열** 목록에서 **EnglishProductName** 을 선택하고 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1c8a4-129">Select **EnglishProductName** in the **Source column** list, and then click **OK**.</span></span>  
  
     <span data-ttu-id="1c8a4-130">이제 NameColumn 필드에 **Product.EnglishProductName (WChar)** 텍스트가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="1c8a4-130">The NameColumn field now contains the text, **Product.EnglishProductName (WChar)**.</span></span>  
  
8.  <span data-ttu-id="1c8a4-131">속성 창에서 위로 스크롤하여 **Name** 속성 필드를 클릭 한 다음를 입력 `Product Name` 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c8a4-131">In the Properties window, scroll up, click the **Name** property field, and then type `Product Name`.</span></span>  
  
## <a name="creating-a-hierarchy"></a><span data-ttu-id="1c8a4-132">계층 만들기</span><span class="sxs-lookup"><span data-stu-id="1c8a4-132">Creating a Hierarchy</span></span>  
  
#### <a name="to-create-a-hierarchy"></a><span data-ttu-id="1c8a4-133">계층을 만들려면</span><span class="sxs-lookup"><span data-stu-id="1c8a4-133">To create a hierarchy</span></span>  
  
1.  <span data-ttu-id="1c8a4-134">**특성** 창의 **Product Line** 특성을 **계층** 창으로 끌어옵니다.</span><span class="sxs-lookup"><span data-stu-id="1c8a4-134">Drag the **Product Line** attribute from the **Attributes** pane into the **Hierarchies** pane.</span></span>  
  
2.  <span data-ttu-id="1c8a4-135">**특성** 창의 **Model Name** 특성을 **\<new level>** 계층 **창의** Product Line **수준 아래** 셀에 끌어옵니다.</span><span class="sxs-lookup"><span data-stu-id="1c8a4-135">Drag the **Model Name** attribute from the **Attributes** pane into the **\<new level>** cell in the **Hierarchies** pane, underneath the **Product Line** level.</span></span>  
  
3.  <span data-ttu-id="1c8a4-136">특성 `Product Name` 창의 특성을 **Attributes** **\<new level>** **계층** 창의 **모델 이름** 수준 아래 셀에 끌어옵니다.</span><span class="sxs-lookup"><span data-stu-id="1c8a4-136">Drag the `Product Name` attribute from the **Attributes** pane into the **\<new level>** cell in the **Hierarchies** pane, underneath the **Model Name** level.</span></span> <span data-ttu-id="1c8a4-137">이전 단원에서 Product Key를 Product Name으로 바꿨습니다.</span><span class="sxs-lookup"><span data-stu-id="1c8a4-137">(You renamed Product Key to Product Name in the previous section.)</span></span>  
  
4.  <span data-ttu-id="1c8a4-138">**차원 구조** 탭의 **계층** 창에서 **hierarchy** 계층의 제목 표시줄을 마우스 오른쪽 단추로 클릭 하 고 **이름 바꾸기**를 클릭 한 다음를 입력 `Product Model Lines` 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c8a4-138">In the **Hierarchies** pane of the **Dimension Structure** tab, right-click the title bar of the **Hierarchy** hierarchy, click **Rename**, and then type `Product Model Lines`.</span></span>  
  
     <span data-ttu-id="1c8a4-139">계층 이름이 이제입니다 `Product Model Lines` .</span><span class="sxs-lookup"><span data-stu-id="1c8a4-139">The name of the hierarchy is now `Product Model Lines`.</span></span>  
  
5.  <span data-ttu-id="1c8a4-140">**파일** 메뉴에서 **모두 저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1c8a4-140">On the **File** menu, click **Save All**.</span></span>  
  
## <a name="specifying-folder-names-and-all-member-names"></a><span data-ttu-id="1c8a4-141">폴더 이름 및 모든 멤버 이름 지정</span><span class="sxs-lookup"><span data-stu-id="1c8a4-141">Specifying Folder Names and All Member Names</span></span>  
  
#### <a name="to-specify-the-folder-and-member-names"></a><span data-ttu-id="1c8a4-142">폴더 이름 및 멤버 이름을 지정하려면</span><span class="sxs-lookup"><span data-stu-id="1c8a4-142">To specify the folder and member names</span></span>  
  
1.  <span data-ttu-id="1c8a4-143">**특성** 창에서 Ctrl 키를 누른 채 각 항목을 클릭하여 다음 특성을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="1c8a4-143">In the **Attributes** pane, select the following attributes by holding down the CTRL key while clicking each of them:</span></span>  
  
    -   <span data-ttu-id="1c8a4-144">**클래스**</span><span class="sxs-lookup"><span data-stu-id="1c8a4-144">**Class**</span></span>  
  
    -   <span data-ttu-id="1c8a4-145">**색상**</span><span class="sxs-lookup"><span data-stu-id="1c8a4-145">**Color**</span></span>  
  
    -   <span data-ttu-id="1c8a4-146">**Days To Manufacture**</span><span class="sxs-lookup"><span data-stu-id="1c8a4-146">**Days To Manufacture**</span></span>  
  
    -   <span data-ttu-id="1c8a4-147">**Reorder Point**</span><span class="sxs-lookup"><span data-stu-id="1c8a4-147">**Reorder Point**</span></span>  
  
    -   <span data-ttu-id="1c8a4-148">**Safety Stock Level**</span><span class="sxs-lookup"><span data-stu-id="1c8a4-148">**Safety Stock Level**</span></span>  
  
    -   <span data-ttu-id="1c8a4-149">**크기**</span><span class="sxs-lookup"><span data-stu-id="1c8a4-149">**Size**</span></span>  
  
    -   <span data-ttu-id="1c8a4-150">**Size Range**</span><span class="sxs-lookup"><span data-stu-id="1c8a4-150">**Size Range**</span></span>  
  
    -   <span data-ttu-id="1c8a4-151">**Style**</span><span class="sxs-lookup"><span data-stu-id="1c8a4-151">**Style**</span></span>  
  
    -   <span data-ttu-id="1c8a4-152">**Weight**</span><span class="sxs-lookup"><span data-stu-id="1c8a4-152">**Weight**</span></span>  
  
2.  <span data-ttu-id="1c8a4-153">속성 창의 **AttributeHierarchyDisplayFolder** 속성 필드에을 (를) 입력 `Stocking` 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c8a4-153">In the **AttributeHierarchyDisplayFolder** property field in the Properties window, type `Stocking`.</span></span>  
  
     <span data-ttu-id="1c8a4-154">이제 이러한 특성을 단일 표시 폴더로 그룹화했습니다.</span><span class="sxs-lookup"><span data-stu-id="1c8a4-154">You have now grouped these attributes into a single display folder.</span></span>  
  
3.  <span data-ttu-id="1c8a4-155">**특성** 창에서 다음 특성을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="1c8a4-155">In the **Attributes** pane, select the following attributes:</span></span>  
  
    -   <span data-ttu-id="1c8a4-156">**Dealer Price**</span><span class="sxs-lookup"><span data-stu-id="1c8a4-156">**Dealer Price**</span></span>  
  
    -   <span data-ttu-id="1c8a4-157">**List Price**</span><span class="sxs-lookup"><span data-stu-id="1c8a4-157">**List Price**</span></span>  
  
    -   <span data-ttu-id="1c8a4-158">**Standard Cost**</span><span class="sxs-lookup"><span data-stu-id="1c8a4-158">**Standard Cost**</span></span>  
  
4.  <span data-ttu-id="1c8a4-159">속성 창의 **AttributeHierarchyDisplayFolder** 속성 셀에를 입력 `Financial` 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c8a4-159">In the **AttributeHierarchyDisplayFolder** property cell in the Properties window, type `Financial`.</span></span>  
  
     <span data-ttu-id="1c8a4-160">이제 이러한 특성을 두 번째 표시 폴더로 그룹화했습니다.</span><span class="sxs-lookup"><span data-stu-id="1c8a4-160">You have now grouped these attributes into a second display folder.</span></span>  
  
5.  <span data-ttu-id="1c8a4-161">**특성** 창에서 다음 특성을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="1c8a4-161">In the **Attributes** pane, select the following attributes:</span></span>  
  
    -   <span data-ttu-id="1c8a4-162">**종료 날짜**</span><span class="sxs-lookup"><span data-stu-id="1c8a4-162">**End Date**</span></span>  
  
    -   <span data-ttu-id="1c8a4-163">**Start Date**</span><span class="sxs-lookup"><span data-stu-id="1c8a4-163">**Start Date**</span></span>  
  
    -   <span data-ttu-id="1c8a4-164">**상태**</span><span class="sxs-lookup"><span data-stu-id="1c8a4-164">**Status**</span></span>  
  
6.  <span data-ttu-id="1c8a4-165">속성 창의 **AttributeHierarchyDisplayFolder** 속성 셀에를 입력 `History` 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c8a4-165">In the **AttributeHierarchyDisplayFolder** property cell in the Properties window, type `History`.</span></span>  
  
     <span data-ttu-id="1c8a4-166">이제 이러한 특성을 세 번째 표시 폴더로 그룹화했습니다.</span><span class="sxs-lookup"><span data-stu-id="1c8a4-166">You have now grouped these attributes into a third display folder.</span></span>  
  
7.  <span data-ttu-id="1c8a4-167">계층 `Product Model Lines` 창에서 계층을 **Hierarchies** 선택 하 고 속성 창 **AllMemberName** 속성을로 변경 합니다 `All Products` .</span><span class="sxs-lookup"><span data-stu-id="1c8a4-167">Select the `Product Model Lines` hierarchy in the **Hierarchies** pane, and then change the **AllMemberName** property in the Properties window to `All Products`.</span></span>  
  
8.  <span data-ttu-id="1c8a4-168">**계층** 창의 열린 영역을 클릭 한 다음 속성 창 맨 위에 있는 **AttributeAllMemberName** 속성을로 변경 `All Products` 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c8a4-168">Click an open area of the **Hierarchies** pane, and then change the **AttributeAllMemberName** property at the top of the Properties window to `All Products`.</span></span>  
  
     <span data-ttu-id="1c8a4-169">열린 영역을 클릭하면 Product 차원 자체의 속성을 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1c8a4-169">Clicking an open area lets you modify properties of the Product dimension itself.</span></span> <span data-ttu-id="1c8a4-170">**특성** 창의 특성 목록 맨 위에 있는 **Product** 를 클릭해도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1c8a4-170">You could also click **Product** at the top of the attributes list in the **Attributes** pane.</span></span>  
  
9. <span data-ttu-id="1c8a4-171">**파일** 메뉴에서 **모두 저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1c8a4-171">On the **File** menu, click **Save All**.</span></span>  
  
## <a name="defining-attribute-relationships"></a><span data-ttu-id="1c8a4-172">특성 관계 정의</span><span class="sxs-lookup"><span data-stu-id="1c8a4-172">Defining Attribute Relationships</span></span>  
 <span data-ttu-id="1c8a4-173">기본 데이터가 특성 관계를 지원하는 경우 특성 간의 특성 관계를 정의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c8a4-173">If the underlying data supports it, you should define attribute relationships between attributes.</span></span> <span data-ttu-id="1c8a4-174">특성 관계를 정의하면 차원, 파티션 및 쿼리 처리가 빨라집니다.</span><span class="sxs-lookup"><span data-stu-id="1c8a4-174">Defining attribute relationships speeds up dimension, partition, and query processing.</span></span> <span data-ttu-id="1c8a4-175">자세한 내용은 [특성 관계 정의](multidimensional-models/attribute-relationships-define.md) 및 [특성 관계](multidimensional-models-olap-logical-dimension-objects/attribute-relationships.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1c8a4-175">For more information, see [Define Attribute Relationships](multidimensional-models/attribute-relationships-define.md) and [Attribute Relationships](multidimensional-models-olap-logical-dimension-objects/attribute-relationships.md).</span></span>  
  
#### <a name="to-define-attribute-relationships"></a><span data-ttu-id="1c8a4-176">특성 관계를 정의하려면</span><span class="sxs-lookup"><span data-stu-id="1c8a4-176">To define attribute relationships</span></span>  
  
1.  <span data-ttu-id="1c8a4-177">Product 차원의 **차원 디자이너** 에서 **특성 관계** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1c8a4-177">In the **Dimension Designer** for the Product dimension, click the **Attribute Relationships** tab.</span></span>  
  
2.  <span data-ttu-id="1c8a4-178">다이어그램에서 **Model Name** 특성을 마우스 오른쪽 단추로 클릭한 다음 **새 특성 관계**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1c8a4-178">In the diagram, right-click the **Model Name** attribute, and then click **New Attribute Relationship**.</span></span>  
  
3.  <span data-ttu-id="1c8a4-179">**특성 관계 만들기** 대화 상자에서 **원본 특성** 은 **Model Name**입니다.</span><span class="sxs-lookup"><span data-stu-id="1c8a4-179">In the **Create Attribute Relationship** dialog box, the **Source Attribute** is **Model Name**.</span></span> <span data-ttu-id="1c8a4-180">**관련 특성** 을 **Product Line**으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="1c8a4-180">Set the **Related Attribute** to **Product Line**.</span></span>  
  
     <span data-ttu-id="1c8a4-181">멤버 간의 관계는 시간이 지나면 변경될 수 있으므로 **관계 유형** 목록에서 관계 유형을 **유동** 으로 설정된 상태로 둡니다.</span><span class="sxs-lookup"><span data-stu-id="1c8a4-181">In the **Relationship type** list, leave the relationship type set to **Flexible** because relationships between the members might change over time.</span></span> <span data-ttu-id="1c8a4-182">예를 들어 제품 모델은 나중에 다른 제품 라인으로 이전될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1c8a4-182">For example, a product model might eventually be moved to a different product line.</span></span>  
  
4.  <span data-ttu-id="1c8a4-183">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1c8a4-183">Click **OK**.</span></span>  
  
5.  <span data-ttu-id="1c8a4-184">**파일** 메뉴에서 **모두 저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1c8a4-184">On the **File** menu, click **Save All**.</span></span>  
  
## <a name="reviewing-product-dimension-changes"></a><span data-ttu-id="1c8a4-185">Product 차원 변경 내용 검토</span><span class="sxs-lookup"><span data-stu-id="1c8a4-185">Reviewing Product Dimension Changes</span></span>  
  
#### <a name="to-review-the-product-dimension-changes"></a><span data-ttu-id="1c8a4-186">Product 차원 변경 내용을 검토하려면</span><span class="sxs-lookup"><span data-stu-id="1c8a4-186">To review the Product dimension changes</span></span>  
  
1.  <span data-ttu-id="1c8a4-187">**의** 빌드 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]메뉴에서 **Analysis Services Tutorial 배포**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1c8a4-187">On the **Build** menu of [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], click **Deploy Analysis Services Tutorial**.</span></span>  
  
2.  <span data-ttu-id="1c8a4-188">**배포가 완료되었습니다.** 메시지를 받은 후 **Product** 차원에 대한 **차원 디자이너** 의 **브라우저** 탭을 클릭한 다음 디자이너의 도구 모음에 있는 다시 연결 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1c8a4-188">After you have received the **Deployment Completed Successfully** message, click the **Browser** tab of **Dimension Designer** for the **Product** dimension, and then click the Reconnect button on the toolbar of the designer.</span></span>  
  
3.  <span data-ttu-id="1c8a4-189">`Product Model Lines` **계층** 목록에서가 선택 되어 있는지 확인 한 다음를 확장 `All Products` 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c8a4-189">Verify that `Product Model Lines` is selected in the **Hierarchy** list, and then expand `All Products`.</span></span>  
  
     <span data-ttu-id="1c8a4-190">**All** 멤버의 이름이로 표시 됩니다 `All Products` .</span><span class="sxs-lookup"><span data-stu-id="1c8a4-190">Notice that the name of the **All** member appears as `All Products`.</span></span> <span data-ttu-id="1c8a4-191">이는 이전 단원에서 계층의 **AllMemberName** 속성을로 변경 했기 때문입니다 `All Products` .</span><span class="sxs-lookup"><span data-stu-id="1c8a4-191">This is because you changed the **AllMemberName** property for the hierarchy to `All Products` earlier in the lesson.</span></span> <span data-ttu-id="1c8a4-192">또한 **Product Line** 수준의 멤버는 이제 한 자로 된 약어가 아니라 알아보기 쉬운 이름을 갖게 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="1c8a4-192">Also, the members of the **Product Line** level now have user-friendly names, instead of single-letter abbreviations.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="1c8a4-193">단원의 다음 태스크</span><span class="sxs-lookup"><span data-stu-id="1c8a4-193">Next Task in Lesson</span></span>  
 [<span data-ttu-id="1c8a4-194">Date 차원 수정</span><span class="sxs-lookup"><span data-stu-id="1c8a4-194">Modifying the Date Dimension</span></span>](lesson-3-4-modifying-the-date-dimension.md)  
  
## <a name="see-also"></a><span data-ttu-id="1c8a4-195">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1c8a4-195">See Also</span></span>  
 <span data-ttu-id="1c8a4-196">[데이터 원본 뷰에서 명명 된 계산을 정의 하 여 Analysis Services &#40;&#41;](multidimensional-models/define-named-calculations-in-a-data-source-view-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="1c8a4-196">[Define Named Calculations in a Data Source View &#40;Analysis Services&#41;](multidimensional-models/define-named-calculations-in-a-data-source-view-analysis-services.md) </span></span>  
 <span data-ttu-id="1c8a4-197">[사용자 정의 계층 만들기](multidimensional-models/user-defined-hierarchies-create.md) </span><span class="sxs-lookup"><span data-stu-id="1c8a4-197">[Create User-Defined Hierarchies](multidimensional-models/user-defined-hierarchies-create.md) </span></span>  
 [<span data-ttu-id="1c8a4-198">특성 계층에 대해 &#40;All&#41; 수준 구성</span><span class="sxs-lookup"><span data-stu-id="1c8a4-198">Configure the &#40;All&#41; Level for Attribute Hierarchies</span></span>](multidimensional-models/database-dimensions-configure-the-all-level-for-attribute-hierarchies.md)  
  
  
