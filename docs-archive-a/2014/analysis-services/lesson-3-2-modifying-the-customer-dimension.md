---
title: Customer 차원 수정 | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 5b5aed99-1760-4bc7-b248-52ecb0b97ebc
author: minewiskan
ms.author: owend
ms.openlocfilehash: bd5c5c47205a89f8429b0b6f0ba55da266d5e811
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653031"
---
# <a name="modifying-the-customer-dimension"></a><span data-ttu-id="24d20-102">Customer 차원 수정</span><span class="sxs-lookup"><span data-stu-id="24d20-102">Modifying the Customer Dimension</span></span>
  <span data-ttu-id="24d20-103">다양한 방법을 통해 큐브에서 차원의 유용성과 기능을 향상시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="24d20-103">There are many different ways that you can increase the usability and functionality of the dimensions in a cube.</span></span> <span data-ttu-id="24d20-104">이 항목의 태스크에서는 Customer 차원을 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="24d20-104">In the tasks in this topic, you modify the Customer dimension.</span></span>  
  
## <a name="renaming-attributes"></a><span data-ttu-id="24d20-105">특성 이름 바꾸기</span><span class="sxs-lookup"><span data-stu-id="24d20-105">Renaming Attributes</span></span>  
 <span data-ttu-id="24d20-106">차원 디자이너의 **차원 구조** 탭을 사용하여 특성 이름을 바꿀 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="24d20-106">You can change attribute names with the **Dimension Structure** tab of Dimension Designer.</span></span>  
  
#### <a name="to-rename-an-attribute"></a><span data-ttu-id="24d20-107">특성 이름을 바꾸려면</span><span class="sxs-lookup"><span data-stu-id="24d20-107">To rename an attribute</span></span>  
  
1.  <span data-ttu-id="24d20-108">**에서 Customer 차원에 대한** 차원 디자이너 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]로 전환합니다.</span><span class="sxs-lookup"><span data-stu-id="24d20-108">Switch to **Dimension Designer** for the Customer dimension in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="24d20-109">이렇게 하려면 솔루션 탐색기의 **차원** 노드에서 **Customer** 차원을 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="24d20-109">To do this, double-click the **Customer** dimension in the **Dimensions** node of Solution Explorer.</span></span>  
  
2.  <span data-ttu-id="24d20-110">**특성** 창에서 **English Country Region Name**을 마우스 오른쪽 단추로 클릭하고 **이름 바꾸기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="24d20-110">In the **Attributes** pane, right-click **English Country Region Name**, and then click **Rename**.</span></span> <span data-ttu-id="24d20-111">특성의 이름을로 변경 `Country-Region` 합니다.</span><span class="sxs-lookup"><span data-stu-id="24d20-111">Change the name of the attribute to `Country-Region`.</span></span>  
  
3.  <span data-ttu-id="24d20-112">같은 방법으로 다음 특성 이름을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="24d20-112">Change the names of the following attributes in the same manner:</span></span>  
  
    -   <span data-ttu-id="24d20-113">**영어 교육** 특성-변경`Education`</span><span class="sxs-lookup"><span data-stu-id="24d20-113">**English Education** attribute - change to `Education`</span></span>  
  
    -   <span data-ttu-id="24d20-114">**영어 직업** 특성-변경`Occupation`</span><span class="sxs-lookup"><span data-stu-id="24d20-114">**English Occupation** attribute - change to `Occupation`</span></span>  
  
    -   <span data-ttu-id="24d20-115">**시/도 이름** 특성-변경`State-Province`</span><span class="sxs-lookup"><span data-stu-id="24d20-115">**State Province Name** attribute - change to `State-Province`</span></span>  
  
4.  <span data-ttu-id="24d20-116">**파일** 메뉴에서 **모두 저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="24d20-116">On the **File** menu, click **Save All**.</span></span>  
  
## <a name="creating-a-hierarchy"></a><span data-ttu-id="24d20-117">계층 만들기</span><span class="sxs-lookup"><span data-stu-id="24d20-117">Creating a Hierarchy</span></span>  
 <span data-ttu-id="24d20-118">**특성** 창에서 **계층** 창으로 특성을 끌어 새 계층을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="24d20-118">You can create a new hierarchy by dragging an attribute from the **Attributes** pane to the **Hierarchies** pane.</span></span>  
  
#### <a name="to-create-a-hierarchy"></a><span data-ttu-id="24d20-119">계층을 만들려면</span><span class="sxs-lookup"><span data-stu-id="24d20-119">To create a hierarchy</span></span>  
  
1.  <span data-ttu-id="24d20-120">특성 `Country-Region` 창에서 **계층** 창 **Attributes** 으로 특성을 끌어 옵니다.</span><span class="sxs-lookup"><span data-stu-id="24d20-120">Drag the `Country-Region` attribute from the **Attributes** pane into the **Hierarchies** pane.</span></span>  
  
2.  <span data-ttu-id="24d20-121">특성 `State-Province` 창의 특성을 **Attributes** **\<new level>** **계층** 창의 수준 아래 셀에 끌어옵니다 `Country-Region` .</span><span class="sxs-lookup"><span data-stu-id="24d20-121">Drag the `State-Province` attribute from the **Attributes** pane into the **\<new level>** cell in the **Hierarchies** pane, underneath the `Country-Region` level.</span></span>  
  
3.  <span data-ttu-id="24d20-122">**특성** 창에서 **City** 특성 **\<new level>** 을 **계층** 창의 수준 아래 셀에 끌어옵니다 `State-Province` .</span><span class="sxs-lookup"><span data-stu-id="24d20-122">Drag the **City** attribute from the **Attributes** pane into the **\<new level>** cell in the **Hierarchies** pane, underneath the `State-Province` level.</span></span>  
  
4.  <span data-ttu-id="24d20-123">**차원 구조** 탭의 **계층** 창에서 **hierarchy** 계층의 제목 표시줄을 마우스 오른쪽 단추로 클릭 하 고 **이름 바꾸기**를 선택한 다음을 입력 `Customer Geography` 합니다.</span><span class="sxs-lookup"><span data-stu-id="24d20-123">In the **Hierarchies** pane of the **Dimension Structure** tab, right-click the title bar of the **Hierarchy** hierarchy, select **Rename**, and then type `Customer Geography`.</span></span>  
  
     <span data-ttu-id="24d20-124">계층 이름이 이제입니다 `Customer Geography` .</span><span class="sxs-lookup"><span data-stu-id="24d20-124">The name of the hierarchy is now `Customer Geography`.</span></span>  
  
5.  <span data-ttu-id="24d20-125">**파일** 메뉴에서 **모두 저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="24d20-125">On the **File** menu, click **Save All**.</span></span>  
  
## <a name="adding-a-named-calculation"></a><span data-ttu-id="24d20-126">명명된 계산 추가</span><span class="sxs-lookup"><span data-stu-id="24d20-126">Adding a Named Calculation</span></span>  
 <span data-ttu-id="24d20-127">계산 열로 표시되는 SQL 식인 명명된 계산을 데이터 원본 뷰의 테이블에 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="24d20-127">You can add a named calculation, which is a SQL expression that is represented as a calculated column, to a table in a data source view.</span></span> <span data-ttu-id="24d20-128">이 식은 테이블의 열로 나타나고 동작합니다.</span><span class="sxs-lookup"><span data-stu-id="24d20-128">The expression appears and behaves as a column in the table.</span></span> <span data-ttu-id="24d20-129">명명된 계산을 사용하면 기본 데이터 원본의 테이블을 수정하지 않고 데이터 원본 뷰에서 기존 테이블의 관계형 스키마를 확장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="24d20-129">Named calculations let you extend the relational schema of existing tables in a data source view without modifying the table in the underlying data source.</span></span> <span data-ttu-id="24d20-130">자세한 내용은 [데이터 원본 뷰에서 명명된 계산 정의&#40;Analysis Services&#41;](multidimensional-models/define-named-calculations-in-a-data-source-view-analysis-services.md)</span><span class="sxs-lookup"><span data-stu-id="24d20-130">For more information, see [Define Named Calculations in a Data Source View &#40;Analysis Services&#41;](multidimensional-models/define-named-calculations-in-a-data-source-view-analysis-services.md)</span></span>  
  
#### <a name="to-add-a-named-calculation"></a><span data-ttu-id="24d20-131">명명된 계산을 추가하려면</span><span class="sxs-lookup"><span data-stu-id="24d20-131">To add a named calculation</span></span>  
  
1.  <span data-ttu-id="24d20-132">솔루션 탐색기의 **데이터 원본 뷰** 폴더에서 \*\* [!INCLUDE[ssSampleDBCoShort](../includes/sssampledbcoshort-md.md)] DW 2012\*\* 데이터 원본 뷰를 두 번 클릭 하 여 엽니다.</span><span class="sxs-lookup"><span data-stu-id="24d20-132">Open the **[!INCLUDE[ssSampleDBCoShort](../includes/sssampledbcoshort-md.md)] DW 2012** data source view by double-clicking it in the **Data Source Views** folder in Solution Explorer.</span></span>  
  
2.  <span data-ttu-id="24d20-133">왼쪽의 **테이블** 창에서 **Customer**를 마우스 오른쪽 단추로 클릭한 다음 **새 명명된 계산**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="24d20-133">In the **Tables** pane on the left, right-click **Customer**, and then click **New Named Calculation**.</span></span>  
  
3.  <span data-ttu-id="24d20-134">**명명 된 계산 만들기** 대화 상자에서 `FullName` **열 이름** 상자에를 입력 하 고 `CASE` **식** 상자에 다음 문을 입력 하거나 복사 하 여 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="24d20-134">In the **Create Named Calculation** dialog box, type `FullName` in the **Column name** box, and then type or copy and paste the following `CASE` statement in the **Expression** box:</span></span>  
  
    ```  
    CASE  
       WHEN MiddleName IS NULL THEN  
       FirstName + ' ' + LastName  
       ELSE  
       FirstName + ' ' + MiddleName + ' ' + LastName  
    END  
    ```  
  
     <span data-ttu-id="24d20-135">`CASE`문은 **FirstName**, **MiddleName**및 **LastName** 열을 customer 차원에서 **customer** 특성의 표시 이름으로 사용할 단일 열로 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="24d20-135">The `CASE` statement concatenates the **FirstName**, **MiddleName**, and **LastName** columns into a single column that you will use in the Customer dimension as the displayed name for the **Customer** attribute.</span></span>  
  
4.  <span data-ttu-id="24d20-136">**확인**을 클릭한 다음 **테이블** 창에서 **Customer** 를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="24d20-136">Click **OK**, and then expand **Customer** in the **Tables** pane.</span></span>  
  
     <span data-ttu-id="24d20-137">명명 된 `FullName` 계산은 명명 된 계산 임을 나타내는 아이콘과 함께 Customer 테이블의 열 목록에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="24d20-137">The `FullName` named calculation appears in the list of columns in the Customer table, with an icon that indicates that it is a named calculation.</span></span>  
  
5.  <span data-ttu-id="24d20-138">**파일** 메뉴에서 **모두 저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="24d20-138">On the **File** menu, click **Save All**.</span></span>  
  
6.  <span data-ttu-id="24d20-139">**테이블** 창에서 **Customer**를 마우스 오른쪽 단추로 클릭하고 **데이터 탐색**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="24d20-139">In the **Tables** pane, right-click **Customer**, and then click **Explore Data**.</span></span>  
  
7.  <span data-ttu-id="24d20-140">**Customer 테이블 탐색** 뷰의 마지막 열을 검토합니다.</span><span class="sxs-lookup"><span data-stu-id="24d20-140">Review the last column in the **Explore Customer Table** view.</span></span>  
  
     <span data-ttu-id="24d20-141">`FullName`열이 데이터 원본 뷰에 표시 되 고 원본 데이터 원본을 수정 하지 않고 기본 데이터 원본에서 여러 열의 데이터를 올바르게 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="24d20-141">Notice that the `FullName` column appears in the data source view, correctly concatenating data from several columns from the underlying data source and without modifying the original data source.</span></span>  
  
8.  <span data-ttu-id="24d20-142">**Customer 테이블 탐색** 탭을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="24d20-142">Close the **Explore Customer Table** tab.</span></span>  
  
## <a name="using-the-named-calculation-for-member-names"></a><span data-ttu-id="24d20-143">멤버 이름에 명명된 계산 사용</span><span class="sxs-lookup"><span data-stu-id="24d20-143">Using the Named Calculation for Member Names</span></span>  
 <span data-ttu-id="24d20-144">데이터 원본 뷰에서 명명된 계산을 만든 후에는 이 명명된 계산을 특성의 속성으로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="24d20-144">After you have created a named calculation in the data source view, you can use the named calculation as a property of an attribute.</span></span>  
  
#### <a name="to-use-the-named-calculation-for-member-names"></a><span data-ttu-id="24d20-145">멤버 이름에 명명된 계산을 사용하려면</span><span class="sxs-lookup"><span data-stu-id="24d20-145">To use the named calculation for member names</span></span>  
  
1.  <span data-ttu-id="24d20-146">Customer 차원에 대한 차원 디자이너로 전환합니다.</span><span class="sxs-lookup"><span data-stu-id="24d20-146">Switch to Dimension Designer for the Customer dimension.</span></span>  
  
2.  <span data-ttu-id="24d20-147">**차원 구조** 탭의 **특성** 창에서 **Customer Key** 특성을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="24d20-147">In the **Attributes** pane of the **Dimension Structure** tab, click the **Customer Key** attribute.</span></span>  
  
3.  <span data-ttu-id="24d20-148">속성 창을 열고 제목 표시줄의 **자동 숨기기** 단추를 클릭하여 열린 상태를 유지하도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="24d20-148">Open the Properties window and click the **Auto Hide** button on the title bar so that it stays open.</span></span>  
  
4.  <span data-ttu-id="24d20-149">**이름** 속성 필드에를 입력 `Full Name` 합니다.</span><span class="sxs-lookup"><span data-stu-id="24d20-149">In the **Name** property field, type `Full Name`.</span></span>  
  
5.  <span data-ttu-id="24d20-150">아래쪽의 **NameColumn** 속성 필드를 클릭 한 다음 찾아보기 (**...**) 단추를 클릭 하 여 **이름 열** 대화 상자를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="24d20-150">Click in the **NameColumn** property field at the bottom, and then click the browse (**...**) button to open the **Name Column** dialog box.</span></span>  
  
6.  <span data-ttu-id="24d20-151">`FullName` **원본 열** 목록의 맨 아래에서를 선택 하 고 **확인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="24d20-151">Select `FullName` at the bottom of the **Source column** list, and then click **OK**.</span></span>  
  
7.  <span data-ttu-id="24d20-152">차원 구조 탭에서 특성 `Full Name` 창의 특성을 **Attributes** **\<new level>** **계층** 창의 **City** 수준 아래 셀에 끌어옵니다.</span><span class="sxs-lookup"><span data-stu-id="24d20-152">In the Dimensions Structure tab, drag the `Full Name` attribute from the **Attributes** pane into the **\<new level>** cell in the **Hierarchies** pane, underneath the **City** level.</span></span>  
  
8.  <span data-ttu-id="24d20-153">**파일** 메뉴에서 **모두 저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="24d20-153">On the **File** menu, click **Save All**.</span></span>  
  
## <a name="defining-display-folders"></a><span data-ttu-id="24d20-154">표시 폴더 정의</span><span class="sxs-lookup"><span data-stu-id="24d20-154">Defining Display Folders</span></span>  
 <span data-ttu-id="24d20-155">사용자가 좀 더 쉽게 사용할 수 있도록 표시 폴더를 사용하여 사용자와 특성 계층을 폴더 구조로 그룹화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="24d20-155">You can use display folders to group user and attribute hierarchies into folder structures to increase usability.</span></span>  
  
#### <a name="to-define-display-folders"></a><span data-ttu-id="24d20-156">표시 폴더를 정의하려면</span><span class="sxs-lookup"><span data-stu-id="24d20-156">To define display folders</span></span>  
  
1.  <span data-ttu-id="24d20-157">Customer 차원에 대한 **차원 구조** 탭을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="24d20-157">Open the **Dimension Structure** tab for the Customer dimension.</span></span>  
  
2.  <span data-ttu-id="24d20-158">**특성** 창에서 Ctrl 키를 누른 채 각 항목을 클릭하여 다음 특성을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="24d20-158">In the **Attributes** pane, select the following attributes by holding down the CTRL key while clicking each of them:</span></span>  
  
    -   <span data-ttu-id="24d20-159">**도시**</span><span class="sxs-lookup"><span data-stu-id="24d20-159">**City**</span></span>  
  
    -   `Country-Region`  
  
    -   <span data-ttu-id="24d20-160">**우편 번호**</span><span class="sxs-lookup"><span data-stu-id="24d20-160">**Postal Code**</span></span>  
  
    -   `State-Province`  
  
3.  <span data-ttu-id="24d20-161">속성 창에서 맨 위에 있는 **AttributeHierarchyDisplayFolder** 속성 필드를 클릭 한 다음를 입력 하 여 전체 이름을 확인 해야 할 수 있습니다 `Location` .</span><span class="sxs-lookup"><span data-stu-id="24d20-161">In the Properties window, click the **AttributeHierarchyDisplayFolder** property field at the top (you might need to point to it to see the full name), and then type `Location`.</span></span>  
  
4.  <span data-ttu-id="24d20-162">**계층** 창에서를 클릭 한 `Customer Geography` 다음 오른쪽에 있는 속성 창에서 `Location` **displayfolder** 속성 값으로를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="24d20-162">In the **Hierarchies** pane, click `Customer Geography`, and then in the Properties window on the right, select `Location` as the value of the **DisplayFolder** property.</span></span>  
  
5.  <span data-ttu-id="24d20-163">**특성** 창에서 Ctrl 키를 누른 채 각 항목을 클릭하여 다음 특성을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="24d20-163">In the **Attributes** pane, select the following attributes by holding down the CTRL key while clicking each of them:</span></span>  
  
    -   <span data-ttu-id="24d20-164">**Commute Distance**</span><span class="sxs-lookup"><span data-stu-id="24d20-164">**Commute Distance**</span></span>  
  
    -   `Education`  
  
    -   <span data-ttu-id="24d20-165">**성별**</span><span class="sxs-lookup"><span data-stu-id="24d20-165">**Gender**</span></span>  
  
    -   <span data-ttu-id="24d20-166">**House Owner Flag**</span><span class="sxs-lookup"><span data-stu-id="24d20-166">**House Owner Flag**</span></span>  
  
    -   <span data-ttu-id="24d20-167">**Marital Status**</span><span class="sxs-lookup"><span data-stu-id="24d20-167">**Marital Status**</span></span>  
  
    -   <span data-ttu-id="24d20-168">**Number Cars Owned**</span><span class="sxs-lookup"><span data-stu-id="24d20-168">**Number Cars Owned**</span></span>  
  
    -   <span data-ttu-id="24d20-169">**Number Children At Home**</span><span class="sxs-lookup"><span data-stu-id="24d20-169">**Number Children At Home**</span></span>  
  
    -   `Occupation`  
  
    -   <span data-ttu-id="24d20-170">**Total Children**</span><span class="sxs-lookup"><span data-stu-id="24d20-170">**Total Children**</span></span>  
  
    -   <span data-ttu-id="24d20-171">**Yearly Income**</span><span class="sxs-lookup"><span data-stu-id="24d20-171">**Yearly Income**</span></span>  
  
6.  <span data-ttu-id="24d20-172">속성 창에서 맨 위에 있는 **AttributeHierarchyDisplayFolder** 속성 필드를 클릭 한 다음를 입력 `Demographic` 합니다.</span><span class="sxs-lookup"><span data-stu-id="24d20-172">In the Properties window, click the **AttributeHierarchyDisplayFolder** property field at the top, and then type `Demographic`.</span></span>  
  
7.  <span data-ttu-id="24d20-173">**특성** 창에서 Ctrl 키를 누른 채 각 항목을 클릭하여 다음 특성을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="24d20-173">In the **Attributes** pane, select the following attributes by holding down the CTRL key while clicking each of them:</span></span>  
  
    -   <span data-ttu-id="24d20-174">**이메일 주소**</span><span class="sxs-lookup"><span data-stu-id="24d20-174">**Email Address**</span></span>  
  
    -   <span data-ttu-id="24d20-175">**내선**</span><span class="sxs-lookup"><span data-stu-id="24d20-175">**Phone**</span></span>  
  
8.  <span data-ttu-id="24d20-176">속성 창에서 **AttributeHierarchyDisplayFolder** 속성 필드를 클릭 하 고을 입력 `Contacts` 합니다.</span><span class="sxs-lookup"><span data-stu-id="24d20-176">In the Properties window, click the **AttributeHierarchyDisplayFolder** property field and type `Contacts`.</span></span>  
  
9. <span data-ttu-id="24d20-177">**파일** 메뉴에서 **모두 저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="24d20-177">On the **File** menu, click **Save All**.</span></span>  
  
## <a name="defining-composite-keycolumns"></a><span data-ttu-id="24d20-178">복합 KeyColumns 정의</span><span class="sxs-lookup"><span data-stu-id="24d20-178">Defining Composite KeyColumns</span></span>  
 <span data-ttu-id="24d20-179">**KeyColumns** 속성에는 특성의 키를 나타내는 열이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="24d20-179">The **KeyColumns** property contains the column or columns that represent the key for the attribute.</span></span> <span data-ttu-id="24d20-180">이 단원에서는 **도시** 와 특성에 대 한 복합 키를 만듭니다 `State-Province` .</span><span class="sxs-lookup"><span data-stu-id="24d20-180">In this lesson, you create a composite key for the **City** and `State-Province` attributes.</span></span> <span data-ttu-id="24d20-181">복합 키는 특성을 고유하게 식별해야 하는 경우 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="24d20-181">Composite keys can be helpful when you need to uniquely identify an attribute.</span></span> <span data-ttu-id="24d20-182">예를 들어이 자습서의 뒷부분에서 특성 관계를 정의할 때 **City** 특성은 특성을 고유 하 게 식별 해야 합니다 `State-Province` .</span><span class="sxs-lookup"><span data-stu-id="24d20-182">For example, when you define attribute relationships later in this tutorial, a **City** attribute must uniquely identify a `State-Province` attribute.</span></span> <span data-ttu-id="24d20-183">그런데 서로 다른 시/도에 같은 이름의 도시가 여러 개 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="24d20-183">However, there could be several cities with the same name in different states.</span></span> <span data-ttu-id="24d20-184">이러한 이유로 **City** 특성에 대해 **StateProvinceName** 및 **City** 열로 구성된 복합 키를 만드는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="24d20-184">For this reason, you will create a composite key that is composed of the **StateProvinceName** and **City** columns for the **City** attribute.</span></span> <span data-ttu-id="24d20-185">자세한 내용은 [특성의 KeyColumn 속성 수정](multidimensional-models/attribute-properties-modify-the-keycolumn-property.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="24d20-185">For more information, see [Modify the KeyColumn Property of an Attribute](multidimensional-models/attribute-properties-modify-the-keycolumn-property.md).</span></span>  
  
#### <a name="to-define-composite-keycolumns-for-the-city-attribute"></a><span data-ttu-id="24d20-186">City 특성에 대한 복합 KeyColumns를 정의하려면</span><span class="sxs-lookup"><span data-stu-id="24d20-186">To define composite KeyColumns for the City attribute</span></span>  
  
1.  <span data-ttu-id="24d20-187">Customer 차원에 대한 **차원 구조** 탭을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="24d20-187">Open the **Dimension Structure** tab for the Customer dimension.</span></span>  
  
2.  <span data-ttu-id="24d20-188">**특성** 창에서 **City** 특성을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="24d20-188">In the **Attributes** pane, click the **City** attribute.</span></span>  
  
3.  <span data-ttu-id="24d20-189">**속성** 창의 아래쪽에서 **KeyColumns** 필드를 클릭한 다음 찾아보기 단추(**...**)를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="24d20-189">In the **Properties** window, click in the **KeyColumns** field near the bottom, and then click the browse (**...**) button.</span></span>  
  
4.  <span data-ttu-id="24d20-190">**키 열** 대화 상자의 **사용 가능한 열** 목록에서 **StateProvinceName**열을 선택한 후 **>** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="24d20-190">In the **Key Columns** dialog box, in the **Available Columns** list, select the column **StateProvinceName**, and then click the **>** button.</span></span>  
  
     <span data-ttu-id="24d20-191">이제 **City** 및 **StateProvinceName** 열이 **키 열** 목록에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="24d20-191">The **City** and **StateProvinceName** columns are now displayed in the **Key Columns** list.</span></span>  
  
5.  <span data-ttu-id="24d20-192">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="24d20-192">Click **OK**.</span></span>  
  
6.  <span data-ttu-id="24d20-193">**City** 특성의 **NameColumn** 속성을 설정하려면 속성 창에서 **NameColumn** 필드를 클릭한 다음 찾아보기 단추(**...**)를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="24d20-193">To set the **NameColumn** property of the **City** attribute, click the **NameColumn** field in the Properties window, and then click the browse (**...**) button.</span></span>  
  
7.  <span data-ttu-id="24d20-194">**이름 열** 대화 상자의 **원본 열** 목록에서 **City**를 선택한 후 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="24d20-194">In the **Name Column** dialog box, in the **Source column** list, select **City**, and then click **OK**.</span></span>  
  
8.  <span data-ttu-id="24d20-195">**파일** 메뉴에서 **모두 저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="24d20-195">On the **File** menu, click **Save All**.</span></span>  
  
#### <a name="to-define-composite-keycolumns-for-the-state-province-attribute"></a><span data-ttu-id="24d20-196">State-Province 특성에 대한 복합 KeyColumns를 정의하려면</span><span class="sxs-lookup"><span data-stu-id="24d20-196">To define composite KeyColumns for the State-Province attribute</span></span>  
  
1.  <span data-ttu-id="24d20-197">Customer 차원에 대한 **차원 구조** 탭을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="24d20-197">Make sure the **Dimension Structure** tab for the Customer dimension is open.</span></span>  
  
2.  <span data-ttu-id="24d20-198">**특성** 창에서 특성을 클릭 `State-Province` 합니다.</span><span class="sxs-lookup"><span data-stu-id="24d20-198">In the **Attributes** pane, click the `State-Province` attribute.</span></span>  
  
3.  <span data-ttu-id="24d20-199">**속성** 창에서 **KeyColumns** 필드를 클릭한 후 찾아보기 단추(**...**)를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="24d20-199">In the **Properties** window, click in the **KeyColumns** field, and then click the browse (**...**) button.</span></span>  
  
4.  <span data-ttu-id="24d20-200">**키 열** 대화 상자의 **사용 가능한 열** 목록에서 **EnglishCountryRegionName**열을 선택한 후 **>** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="24d20-200">In the **Key Columns** dialog box, in the **Available Columns** list, select the column **EnglishCountryRegionName**, and then click the **>** button.</span></span>  
  
     <span data-ttu-id="24d20-201">이제 **EnglishCountryRegionName** 및 **StateProvinceName** 열이 **키 열** 목록에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="24d20-201">The **EnglishCountryRegionName** and **StateProvinceName** columns are now displayed in the **Key Columns** list.</span></span>  
  
5.  <span data-ttu-id="24d20-202">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="24d20-202">Click **OK**.</span></span>  
  
6.  <span data-ttu-id="24d20-203">특성의 **NameColumn** 속성을 설정 하려면 `State-Province` 속성 창 **NameColumn** 필드를 클릭 한 다음 찾아보기 (**...**) 단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="24d20-203">To set the **NameColumn** property of the `State-Province` attribute, click the **NameColumn** field in the Properties window, and then click the browse (**...**) button.</span></span>  
  
7.  <span data-ttu-id="24d20-204">**이름 열** 대화 상자의 **원본 열** 목록에서 **StateProvinceName**을 선택한 후 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="24d20-204">In the **Name Column** dialog box, in the **Source column** list, select **StateProvinceName**, and then click **OK**.</span></span>  
  
8.  <span data-ttu-id="24d20-205">**파일** 메뉴에서 **모두 저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="24d20-205">On the **File** menu, click **Save All**.</span></span>  
  
## <a name="defining-attribute-relationships"></a><span data-ttu-id="24d20-206">특성 관계 정의</span><span class="sxs-lookup"><span data-stu-id="24d20-206">Defining Attribute Relationships</span></span>  
 <span data-ttu-id="24d20-207">기본 데이터가 특성 관계를 지원하는 경우 특성 간의 특성 관계를 정의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="24d20-207">If the underlying data supports it, you should define attribute relationships between attributes.</span></span> <span data-ttu-id="24d20-208">특성 관계를 정의하면 차원, 파티션 및 쿼리 처리가 빨라집니다.</span><span class="sxs-lookup"><span data-stu-id="24d20-208">Defining attribute relationships speeds up dimension, partition, and query processing.</span></span> <span data-ttu-id="24d20-209">자세한 내용은 [특성 관계 정의](multidimensional-models/attribute-relationships-define.md) 및 [특성 관계](multidimensional-models-olap-logical-dimension-objects/attribute-relationships.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="24d20-209">For more information, see [Define Attribute Relationships](multidimensional-models/attribute-relationships-define.md) and [Attribute Relationships](multidimensional-models-olap-logical-dimension-objects/attribute-relationships.md).</span></span>  
  
#### <a name="to-define-attribute-relationships"></a><span data-ttu-id="24d20-210">특성 관계를 정의하려면</span><span class="sxs-lookup"><span data-stu-id="24d20-210">To define attribute relationships</span></span>  
  
1.  <span data-ttu-id="24d20-211">Customer 차원에 대 한 **차원 디자이너** 에서 **특성 관계** 탭을 클릭 합니다. 기다려야 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="24d20-211">In the **Dimension Designer** for the Customer dimension, click the **Attribute Relationships** tab. You might need to wait.</span></span>  
  
2.  <span data-ttu-id="24d20-212">다이어그램에서 **City** 특성을 마우스 오른쪽 단추로 클릭한 다음 **새 특성 관계**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="24d20-212">In the diagram, right-click the **City** attribute, and then click **New Attribute Relationship**.</span></span>  
  
3.  <span data-ttu-id="24d20-213">**특성 관계 만들기** 대화 상자에서 **원본 특성** 은 **City**입니다.</span><span class="sxs-lookup"><span data-stu-id="24d20-213">In the **Create Attribute Relationship** dialog box, the **Source Attribute** is **City**.</span></span> <span data-ttu-id="24d20-214">**관련 특성** 을로 설정 `State-Province` 합니다.</span><span class="sxs-lookup"><span data-stu-id="24d20-214">Set the **Related Attribute** to `State-Province`.</span></span>  
  
4.  <span data-ttu-id="24d20-215">**관계 유형** 목록에서 관계 유형을 **고정**으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="24d20-215">In the **Relationship type** list, set the relationship type to **Rigid**.</span></span>  
  
     <span data-ttu-id="24d20-216">멤버 간의 관계는 시간이 지나도 변경되지 않으므로 관계 유형은 **고정** 입니다.</span><span class="sxs-lookup"><span data-stu-id="24d20-216">The relationship type is **Rigid** because relationships between the members will not change over time.</span></span> <span data-ttu-id="24d20-217">예를 들어 도시가 다른 시/도 소속으로 변경될 가능성은 거의 없습니다.</span><span class="sxs-lookup"><span data-stu-id="24d20-217">For example, it would be unusual for a city to become part of a different state or province.</span></span>  
  
5.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
6.  <span data-ttu-id="24d20-218">다이어그램에서 특성을 마우스 오른쪽 단추로 클릭 `State-Province` 한 다음 **새 특성 관계**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="24d20-218">In the diagram, right-click the `State-Province` attribute and then select **New Attribute Relationship**.</span></span>  
  
7.  <span data-ttu-id="24d20-219">**특성 관계 만들기** 대화 상자에서 **원본 특성** 은 `State-Province` 입니다.</span><span class="sxs-lookup"><span data-stu-id="24d20-219">In the **Create Attribute Relationship** dialog box, the **Source Attribute** is `State-Province`.</span></span> <span data-ttu-id="24d20-220">**관련 특성** 을로 설정 `Country-Region` 합니다.</span><span class="sxs-lookup"><span data-stu-id="24d20-220">Set the **Related Attribute** to `Country-Region`.</span></span>  
  
8.  <span data-ttu-id="24d20-221">**관계 유형** 목록에서 관계 유형을 **고정**으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="24d20-221">In the **Relationship type** list, set the relationship type to **Rigid**.</span></span>  
  
9. <span data-ttu-id="24d20-222">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="24d20-222">Click **OK**.</span></span>  
  
10. <span data-ttu-id="24d20-223">**파일** 메뉴에서 **모두 저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="24d20-223">On the **File** menu, click **Save All**.</span></span>  
  
## <a name="deploying-changes-processing-the-objects-and-viewing-the-changes"></a><span data-ttu-id="24d20-224">변경 내용 배포, 개체 처리 및 변경 내용 표시</span><span class="sxs-lookup"><span data-stu-id="24d20-224">Deploying Changes, Processing the Objects, and Viewing the Changes</span></span>  
 <span data-ttu-id="24d20-225">특성과 계층을 변경한 후에 변경 내용을 표시하려면 먼저 변경 내용을 배포하고 관련 개체를 다시 처리해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="24d20-225">After you have changed attributes and hierarchies, you must deploy the changes and reprocess the related objects before you can view the changes.</span></span>  
  
#### <a name="to-deploy-the-changes-process-the-objects-and-view-the-changes"></a><span data-ttu-id="24d20-226">변경 내용을 배포하고 개체를 처리한 다음 변경 내용을 표시하려면</span><span class="sxs-lookup"><span data-stu-id="24d20-226">To deploy the changes, process the objects, and view the changes</span></span>  
  
1.  <span data-ttu-id="24d20-227">**의** 빌드 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]메뉴에서 **Analysis Services Tutorial 배포**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="24d20-227">On the **Build** menu of [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], click **Deploy Analysis Services Tutorial**.</span></span>  
  
2.  <span data-ttu-id="24d20-228">**배포가 완료되었습니다.** 메시지를 받은 후 Customer 차원에 대한 차원 디자이너의 **브라우저** 탭을 클릭한 다음 디자이너 도구 모음의 왼쪽에 있는 다시 연결 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="24d20-228">After you receive the **Deployment Completed Successfully** message, click the **Browser** tab of Dimension Designer for the Customer dimension, and then click the Reconnect button on the left side of the toolbar of the designer.</span></span>  
  
3.  <span data-ttu-id="24d20-229">`Customer Geography` **계층** 목록에서가 선택 되어 있는지 확인 한 다음 브라우저 창에서 **모두**를 확장 하 고 **오스트레일리아**, **새 남부 Wales**을 차례로 확장 한 다음 **Coffs 차례로**를 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="24d20-229">Verify that `Customer Geography` is selected in the **Hierarchy** list, and then in the browser pane, expand **All**, expand **Australia**, expand **New South Wales**, and then expand **Coffs Harbour**.</span></span>  
  
     <span data-ttu-id="24d20-230">브라우저에 해당 도시의 고객이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="24d20-230">The browser displays the customers in the city.</span></span>  
  
4.  <span data-ttu-id="24d20-231">**Tutorial 큐브에 대한** 큐브 디자이너 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 로 전환합니다.</span><span class="sxs-lookup"><span data-stu-id="24d20-231">Switch to **Cube Designer** for the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube.</span></span> <span data-ttu-id="24d20-232">이렇게 하려면 **솔루션 탐색기**의 **큐브** 노드에서 **Analysis Services Tutorial** 큐브를 두 번 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="24d20-232">To do this, double-click the **Analysis Services Tutorial** cube in the **Cubes** node of **Solution Explorer**.</span></span>  
  
5.  <span data-ttu-id="24d20-233">**브라우저** 탭을 클릭한 다음 디자이너 도구 모음에서 다시 연결 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="24d20-233">Click the **Browser** tab, and then click the Reconnect button on the toolbar of the designer.</span></span>  
  
6.  <span data-ttu-id="24d20-234">**측정값 그룹** 창에서 **Customer**를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="24d20-234">In the **Measure Group** pane, expand **Customer**.</span></span>  
  
     <span data-ttu-id="24d20-235">긴 특성 목록이 아니라 표시 폴더와 표시 폴더 값이 포함되지 않은 특성만 Customer 아래에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="24d20-235">Notice that instead of a long list of attributes, only the display folders and the attributes that do not have display folder values appear underneath Customer.</span></span>  
  
7.  <span data-ttu-id="24d20-236">**파일** 메뉴에서 **모두 저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="24d20-236">On the **File** menu, click **Save All**.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="24d20-237">단원의 다음 태스크</span><span class="sxs-lookup"><span data-stu-id="24d20-237">Next Task in Lesson</span></span>  
 [<span data-ttu-id="24d20-238">Product 차원 수정</span><span class="sxs-lookup"><span data-stu-id="24d20-238">Modifying the Product Dimension</span></span>](lesson-3-3-modifying-the-product-dimension.md)  
  
## <a name="see-also"></a><span data-ttu-id="24d20-239">참고 항목</span><span class="sxs-lookup"><span data-stu-id="24d20-239">See Also</span></span>  
 <span data-ttu-id="24d20-240">[차원 특성 속성 참조](multidimensional-models/dimension-attribute-properties-reference.md) </span><span class="sxs-lookup"><span data-stu-id="24d20-240">[Dimension Attribute Properties Reference](multidimensional-models/dimension-attribute-properties-reference.md) </span></span>  
 <span data-ttu-id="24d20-241">[차원에서 특성 제거](multidimensional-models/attribute-properties-remove-an-attribute-from-a-dimension.md) </span><span class="sxs-lookup"><span data-stu-id="24d20-241">[Remove an Attribute from a Dimension](multidimensional-models/attribute-properties-remove-an-attribute-from-a-dimension.md) </span></span>  
 <span data-ttu-id="24d20-242">[특성 이름 바꾸기](multidimensional-models/attribute-properties-rename-an-attribute.md) </span><span class="sxs-lookup"><span data-stu-id="24d20-242">[Rename an Attribute](multidimensional-models/attribute-properties-rename-an-attribute.md) </span></span>  
 [<span data-ttu-id="24d20-243">데이터 원본 뷰에서 명명된 계산 정의&#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="24d20-243">Define Named Calculations in a Data Source View &#40;Analysis Services&#41;</span></span>](multidimensional-models/define-named-calculations-in-a-data-source-view-analysis-services.md)  
  
  
