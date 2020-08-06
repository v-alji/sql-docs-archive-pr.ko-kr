---
title: Date 차원 수정 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 4689d780-4bf6-4cf8-8fde-eb3f15dd668a
author: minewiskan
ms.author: owend
ms.openlocfilehash: b4978e9fe3acd93ddfdca707d2c2353bf171ba12
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652432"
---
# <a name="modifying-the-date-dimension"></a><span data-ttu-id="ea0ee-102">Date 차원 수정</span><span class="sxs-lookup"><span data-stu-id="ea0ee-102">Modifying the Date Dimension</span></span>
  <span data-ttu-id="ea0ee-103">이 항목의 태스크에서는 사용자 정의 계층을 만들고 Date, Month, Calendar Quarter 및 Calendar Semester 특성에 대해 표시되는 멤버 이름을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="ea0ee-103">In the tasks in this topic, you create a user-defined hierarchy and change the member names that are displayed for the Date, Month, Calendar Quarter, and Calendar Semester attributes.</span></span> <span data-ttu-id="ea0ee-104">또한 특성에 대한 복합 키를 정의하고 차원 멤버의 정렬 순서를 제어하고 특성 관계도 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="ea0ee-104">You also define composite keys for attributes, control the sort order of dimension members, and define attribute relationships.</span></span>  
  
## <a name="adding-a-named-calculation"></a><span data-ttu-id="ea0ee-105">명명된 계산 추가</span><span class="sxs-lookup"><span data-stu-id="ea0ee-105">Adding a Named Calculation</span></span>  
 <span data-ttu-id="ea0ee-106">계산 열로 표시되는 SQL 식인 명명된 계산을 데이터 원본 뷰의 테이블에 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ea0ee-106">You can add a named calculation, which is a SQL expression that is represented as a calculated column, to a table in a data source view.</span></span> <span data-ttu-id="ea0ee-107">이 식은 테이블의 열로 나타나고 동작합니다.</span><span class="sxs-lookup"><span data-stu-id="ea0ee-107">The expression appears and behaves as a column in the table.</span></span> <span data-ttu-id="ea0ee-108">명명된 계산을 사용하면 기본 데이터 원본의 테이블을 수정하지 않고 데이터 원본 뷰에서 기존 테이블의 관계형 스키마를 확장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ea0ee-108">Named calculations enable you to extend the relational schema of existing tables in a data source view without modifying the table in the underlying data source.</span></span> <span data-ttu-id="ea0ee-109">자세한 내용은 [데이터 원본 뷰에서 명명된 계산 정의&#40;Analysis Services&#41;](multidimensional-models/define-named-calculations-in-a-data-source-view-analysis-services.md)</span><span class="sxs-lookup"><span data-stu-id="ea0ee-109">For more information, see [Define Named Calculations in a Data Source View &#40;Analysis Services&#41;](multidimensional-models/define-named-calculations-in-a-data-source-view-analysis-services.md)</span></span>  
  
#### <a name="to-add-a-named-calculation"></a><span data-ttu-id="ea0ee-110">명명된 계산을 추가하려면</span><span class="sxs-lookup"><span data-stu-id="ea0ee-110">To add a named calculation</span></span>  
  
1.  <span data-ttu-id="ea0ee-111">**Adventure Works DW 2012** 데이터 원본 뷰를 열려면 솔루션 탐색기의 **데이터 원본 뷰** 폴더에서 해당 뷰를 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ea0ee-111">To open the **Adventure Works DW 2012** data source view, double-click it in the **Data Source Views** folder in Solution Explorer.</span></span>  
  
2.  <span data-ttu-id="ea0ee-112">**테이블** 창의 아래쪽 근처에서을 마우스 오른쪽 단추로 클릭 한 `Date` 다음 **새 명명 된 계산**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea0ee-112">Near the bottom of the **Tables** pane, right-click `Date`, and then click **New Named Calculation**.</span></span>  
  
3.  <span data-ttu-id="ea0ee-113">**명명 된 계산 만들기** 대화 상자에서 `SimpleDate` **열 이름** 상자에를 입력 하 고 `DATENAME` **식** 상자에 다음 문을 입력 하거나 복사 하 여 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="ea0ee-113">In the **Create Named Calculation** dialog box, type `SimpleDate` in the **Column name** box, and then type or copy and paste the following `DATENAME` statement in the **Expression** box:</span></span>  
  
    ```  
    DATENAME(mm, FullDateAlternateKey) + ' ' +  
    DATENAME(dd, FullDateAlternateKey) + ', ' +  
    DATENAME(yy, FullDateAlternateKey)  
    ```  
  
     <span data-ttu-id="ea0ee-114">`DATENAME` 문은 FullDateAlternateKey 열에서 연도, 월 및 날짜 값을 추출합니다.</span><span class="sxs-lookup"><span data-stu-id="ea0ee-114">The `DATENAME` statement extracts the year, month, and day values from the FullDateAlternateKey column.</span></span> <span data-ttu-id="ea0ee-115">이 새 열을 FullDateAlternateKey 특성에 대한 표시 이름으로 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="ea0ee-115">You will use this new column as the displayed name for the FullDateAlternateKey attribute.</span></span>  
  
4.  <span data-ttu-id="ea0ee-116">**확인**을 클릭 한 다음 `Date` **테이블** 창에서를 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea0ee-116">Click **OK**, and then expand `Date` in the **Tables** pane.</span></span>  
  
     <span data-ttu-id="ea0ee-117">명명 된 `SimpleDate` 계산은 명명 된 계산 임을 나타내는 아이콘과 함께 날짜 테이블의 열 목록에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="ea0ee-117">The `SimpleDate` named calculation appears in the list of columns in the Date table, with an icon that indicates that it is a named calculation.</span></span>  
  
5.  <span data-ttu-id="ea0ee-118">**파일** 메뉴에서 **모두 저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ea0ee-118">On the **File** menu, click **Save All**.</span></span>  
  
6.  <span data-ttu-id="ea0ee-119">**테이블** 창에서을 마우스 오른쪽 단추로 클릭 한 `Date` 다음 **데이터 탐색**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea0ee-119">In the **Tables** pane, right-click `Date`, and then click **Explore Data**.</span></span>  
  
7.  <span data-ttu-id="ea0ee-120">오른쪽으로 스크롤하여 **Date 테이블 탐색** 뷰의 마지막 열을 검토합니다.</span><span class="sxs-lookup"><span data-stu-id="ea0ee-120">Scroll to the right to review the last column in the **Explore Date Table** view.</span></span>  
  
     <span data-ttu-id="ea0ee-121">`SimpleDate`원래 데이터 원본을 수정 하지 않고 기본 데이터 원본에서 여러 열의 데이터를 올바르게 연결한 열이 데이터 원본 뷰에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="ea0ee-121">Notice that the `SimpleDate` column appears in the data source view, correctly concatenating data from several columns from the underlying data source, without modifying the original data source.</span></span>  
  
8.  <span data-ttu-id="ea0ee-122">**Date 테이블 탐색** 뷰를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="ea0ee-122">Close the **Explore Date Table** view.</span></span>  
  
## <a name="using-the-named-calculation-for-member-names"></a><span data-ttu-id="ea0ee-123">멤버 이름에 명명된 계산 사용</span><span class="sxs-lookup"><span data-stu-id="ea0ee-123">Using the Named Calculation for Member Names</span></span>  
 <span data-ttu-id="ea0ee-124">데이터 원본 뷰에서 명명된 계산을 만든 후에는 이 명명된 계산을 특성의 속성으로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ea0ee-124">After you create a named calculation in the data source view, you can use the named calculation as a property of an attribute.</span></span>  
  
#### <a name="to-use-the-named-calculation-for-member-names"></a><span data-ttu-id="ea0ee-125">멤버 이름에 명명된 계산을 사용하려면</span><span class="sxs-lookup"><span data-stu-id="ea0ee-125">To use the named calculation for member names</span></span>  
  
1.  <span data-ttu-id="ea0ee-126">**에서 Date 차원에 대한** 차원 디자이너 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="ea0ee-126">Open **Dimension Designer** for the Date dimension in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="ea0ee-127">이렇게 하려면 `Date` **솔루션 탐색기**차원 노드에서 차원을 두 번 클릭 합니다. **Dimensions**</span><span class="sxs-lookup"><span data-stu-id="ea0ee-127">To do this, double-click the `Date` dimension in the **Dimensions** node of **Solution Explorer**.</span></span>  
  
2.  <span data-ttu-id="ea0ee-128">**차원 구조** 탭의 **특성** 창에서 **Date Key** 특성을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ea0ee-128">In the **Attributes** pane of the **Dimension Structure** tab, click the **Date Key** attribute.</span></span>  
  
3.  <span data-ttu-id="ea0ee-129">속성 창이 열려 있지 않으면 속성 창을 열고 제목 표시줄의 **자동 숨기기** 단추를 클릭하여 열린 상태를 유지합니다.</span><span class="sxs-lookup"><span data-stu-id="ea0ee-129">If the Properties window is not open, open the Properties window, and then click the **Auto Hide** button on the title bar so that it stays open.</span></span>  
  
4.  <span data-ttu-id="ea0ee-130">창 아래쪽 근처의 **NameColumn** 속성 필드를 클릭 한 다음 줄임표 (**...**) 단추를 클릭 하 여 **이름 열** 대화 상자를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="ea0ee-130">Click the **NameColumn** property field near the bottom of the window, and then click the ellipsis browse (**...**) button to open the **Name Column** dialog box.</span></span>  
  
5.  <span data-ttu-id="ea0ee-131">`SimpleDate` **원본 열** 목록의 맨 아래에서를 선택 하 고 **확인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea0ee-131">Select `SimpleDate` at the bottom of the **Source column** list, and then click **OK**.</span></span>  
  
6.  <span data-ttu-id="ea0ee-132">**파일** 메뉴에서 **모두 저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ea0ee-132">On the **File** menu, click **Save All**.</span></span>  
  
## <a name="creating-a-hierarchy"></a><span data-ttu-id="ea0ee-133">계층 만들기</span><span class="sxs-lookup"><span data-stu-id="ea0ee-133">Creating a Hierarchy</span></span>  
 <span data-ttu-id="ea0ee-134">**특성** 창에서 **계층** 창으로 특성을 끌어 새 계층을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ea0ee-134">You can create a new hierarchy by dragging an attribute from the **Attributes** pane to the **Hierarchies** pane.</span></span>  
  
#### <a name="to-create-a-hierarchy"></a><span data-ttu-id="ea0ee-135">계층을 만들려면</span><span class="sxs-lookup"><span data-stu-id="ea0ee-135">To create a hierarchy</span></span>  
  
1.  <span data-ttu-id="ea0ee-136">차원에 대 한 차원 디자이너의 **차원 구조** 탭에서 `Date` **특성** 창의 **Calendar Year** 특성을 **계층** 창으로 끌어옵니다.</span><span class="sxs-lookup"><span data-stu-id="ea0ee-136">In **Dimension Structure** tab of the Dimension Designer for the `Date` dimension, drag the **Calendar Year** attribute from the **Attributes** pane into the **Hierarchies** pane.</span></span>  
  
2.  <span data-ttu-id="ea0ee-137">**특성** 창의 **Calendar Semester** 특성을 **\<new level>** 계층 **창의** Calendar Year **수준 아래** 셀에 끌어옵니다.</span><span class="sxs-lookup"><span data-stu-id="ea0ee-137">Drag the **Calendar Semester** attribute from the **Attributes** pane into the **\<new level>** cell in the **Hierarchies** pane, underneath the **Calendar Year** level.</span></span>  
  
3.  <span data-ttu-id="ea0ee-138">**특성** 창의 **Calendar Quarter** 특성을 **\<new level>** 계층 **창의** Calendar Semester **수준 아래** 셀에 끌어옵니다.</span><span class="sxs-lookup"><span data-stu-id="ea0ee-138">Drag the **Calendar Quarter** attribute from the **Attributes** pane into the **\<new level>** cell in the **Hierarchies** pane, underneath the **Calendar Semester** level.</span></span>  
  
4.  <span data-ttu-id="ea0ee-139">**특성** 창의 **English Month Name** 특성을 **\<new level>** 계층 **창의** Calendar Quarter **수준 아래** 셀에 끌어옵니다.</span><span class="sxs-lookup"><span data-stu-id="ea0ee-139">Drag the **English Month Name** attribute from the **Attributes** pane into the **\<new level>** cell in the **Hierarchies** pane, underneath the **Calendar Quarter** level.</span></span>  
  
5.  <span data-ttu-id="ea0ee-140">**특성** 창의 **Date Key** 특성을 **\<new level>** 계층 **창의** English Month Name **수준 아래** 셀에 끌어옵니다.</span><span class="sxs-lookup"><span data-stu-id="ea0ee-140">Drag the **Date Key** attribute from the **Attributes** pane into the **\<new level>** cell in the **Hierarchies** pane, underneath the **English Month Name** level.</span></span>  
  
6.  <span data-ttu-id="ea0ee-141">**계층 창에서** **계층** 구조 계층의 제목 표시줄을 마우스 오른쪽 단추로 클릭 하 고 **이름 바꾸기**를 클릭 한 다음를 입력 `Calendar Date` 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea0ee-141">In the **Hierarchies** pane, right-click the title bar of the **Hierarchy** hierarchy, click **Rename**, and then type `Calendar Date`.</span></span>  
  
7.  <span data-ttu-id="ea0ee-142">오른쪽 클릭 상황에 맞는 메뉴를 사용 하 여 `Calendar Date` 계층에서 **English Month Name** 수준의 이름을로 변경한 `Calendar Month` 다음 **Date Key** 수준의 이름을으로 바꿉니다 `Date` .</span><span class="sxs-lookup"><span data-stu-id="ea0ee-142">By using the right-click context menu, in the `Calendar Date` hierarchy, rename the **English Month Name** level to `Calendar Month`, and then rename the **Date Key** level to `Date`.</span></span>  
  
8.  <span data-ttu-id="ea0ee-143">**Full Date Alternate Key** 특성은 사용하지 않으므로 **특성** 창에서 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="ea0ee-143">Delete the **Full Date Alternate Key** attribute from the **Attributes** pane because you will not be using it.</span></span> <span data-ttu-id="ea0ee-144">**개체 삭제** 확인 창에서 **확인** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ea0ee-144">Click **OK** in the **Delete Objects** confirmation window.</span></span>  
  
9. <span data-ttu-id="ea0ee-145">**파일** 메뉴에서 **모두 저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ea0ee-145">On the **File** menu, click **Save All**.</span></span>  
  
## <a name="defining-attribute-relationships"></a><span data-ttu-id="ea0ee-146">특성 관계 정의</span><span class="sxs-lookup"><span data-stu-id="ea0ee-146">Defining Attribute Relationships</span></span>  
 <span data-ttu-id="ea0ee-147">기본 데이터가 특성 관계를 지원하는 경우 특성 간의 특성 관계를 정의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea0ee-147">If the underlying data supports it, you should define attribute relationships between attributes.</span></span> <span data-ttu-id="ea0ee-148">특성 관계를 정의하면 차원, 파티션 및 쿼리 처리가 빨라집니다.</span><span class="sxs-lookup"><span data-stu-id="ea0ee-148">Defining attribute relationships speeds up dimension, partition, and query processing.</span></span>  
  
#### <a name="to-define-attribute-relationships"></a><span data-ttu-id="ea0ee-149">특성 관계를 정의하려면</span><span class="sxs-lookup"><span data-stu-id="ea0ee-149">To define attribute relationships</span></span>  
  
1.  <span data-ttu-id="ea0ee-150">차원에 대 한 **차원 디자이너** 에서 `Date` **특성 관계** 탭을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea0ee-150">In the **Dimension Designer** for the `Date` dimension, click the **Attribute Relationships** tab.</span></span>  
  
2.  <span data-ttu-id="ea0ee-151">다이어그램에서 **English Month Name** 특성을 마우스 오른쪽 단추로 클릭한 다음 **새 특성 관계**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ea0ee-151">In the diagram, right-click the **English Month Name** attribute, and then click **New Attribute Relationship**.</span></span>  
  
3.  <span data-ttu-id="ea0ee-152">**특성 관계 만들기** 대화 상자에서 **원본 특성** 은 **English Month Name**입니다.</span><span class="sxs-lookup"><span data-stu-id="ea0ee-152">In the **Create Attribute Relationship** dialog box, the **Source Attribute** is **English Month Name**.</span></span> <span data-ttu-id="ea0ee-153">**관련 특성** 을 **Calendar Quarter**로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="ea0ee-153">Set the **Related Attribute** to **Calendar Quarter**.</span></span>  
  
4.  <span data-ttu-id="ea0ee-154">**관계 유형** 목록에서 관계 유형을 **고정**으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="ea0ee-154">In the **Relationship type** list, set the relationship type to **Rigid**.</span></span>  
  
     <span data-ttu-id="ea0ee-155">멤버 간의 관계는 시간이 지나도 변경되지 않으므로 관계 유형은 **고정** 입니다.</span><span class="sxs-lookup"><span data-stu-id="ea0ee-155">The relationship type is **Rigid** because relationships between the members will not change over time.</span></span>  
  
5.  <span data-ttu-id="ea0ee-156">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ea0ee-156">Click **OK**.</span></span>  
  
6.  <span data-ttu-id="ea0ee-157">다이어그램에서 **Calendar Quarter** 특성을 마우스 오른쪽 단추로 클릭한 다음 **새 특성 관계**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ea0ee-157">In the diagram, right-click the **Calendar Quarter** attribute, and then click **New Attribute Relationship**.</span></span>  
  
7.  <span data-ttu-id="ea0ee-158">**특성 관계 만들기** 대화 상자에서 **원본 특성** 은 **Calendar Quarter**입니다.</span><span class="sxs-lookup"><span data-stu-id="ea0ee-158">In the **Create Attribute Relationship** dialog box, the **Source Attribute** is **Calendar Quarter**.</span></span> <span data-ttu-id="ea0ee-159">**관련 특성** 을 **Calendar Semester**로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="ea0ee-159">Set the **Related Attribute** to **Calendar Semester**.</span></span>  
  
8.  <span data-ttu-id="ea0ee-160">**관계 유형** 목록에서 관계 유형을 **고정**으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="ea0ee-160">In the **Relationship type** list, set the relationship type to **Rigid**.</span></span>  
  
9. <span data-ttu-id="ea0ee-161">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ea0ee-161">Click **OK**.</span></span>  
  
10. <span data-ttu-id="ea0ee-162">다이어그램에서 **Calendar Semester** 특성을 마우스 오른쪽 단추로 클릭한 다음 **새 특성 관계**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ea0ee-162">In the diagram, right-click the **Calendar Semester** attribute, and then click **New Attribute Relationship**.</span></span>  
  
11. <span data-ttu-id="ea0ee-163">**특성 관계 만들기** 대화 상자에서 **원본 특성** 은 **Calendar Semester**입니다.</span><span class="sxs-lookup"><span data-stu-id="ea0ee-163">In the **Create Attribute Relationship** dialog box, the **Source Attribute** is **Calendar Semester**.</span></span> <span data-ttu-id="ea0ee-164">**관련 특성** 을 **Calendar Year**로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="ea0ee-164">Set the **Related Attribute** to **Calendar Year**.</span></span>  
  
12. <span data-ttu-id="ea0ee-165">**관계 유형** 목록에서 관계 유형을 **고정**으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="ea0ee-165">In the **Relationship type** list, set the relationship type to **Rigid**.</span></span>  
  
13. <span data-ttu-id="ea0ee-166">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ea0ee-166">Click **OK**.</span></span>  
  
14. <span data-ttu-id="ea0ee-167">**파일** 메뉴에서 **모두 저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ea0ee-167">On the **File** menu, click **Save All**.</span></span>  
  
## <a name="providing-unique-dimension-member-names"></a><span data-ttu-id="ea0ee-168">고유한 차원 멤버 이름 지정</span><span class="sxs-lookup"><span data-stu-id="ea0ee-168">Providing Unique Dimension Member Names</span></span>  
 <span data-ttu-id="ea0ee-169">이 태스크에서는 **EnglishMonthName**, **CalendarQuarter**, **CalendarSemester** 특성에서 사용되는 친숙한 이름 열을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ea0ee-169">In this task, you will create user-friendly name columns that will be used by the **EnglishMonthName**, **CalendarQuarter**, and **CalendarSemester** attributes.</span></span>  
  
#### <a name="to-provide-unique-dimension-member-names"></a><span data-ttu-id="ea0ee-170">고유한 차원 멤버 이름을 지정하려면</span><span class="sxs-lookup"><span data-stu-id="ea0ee-170">To provide unique dimension member names</span></span>  
  
1.  <span data-ttu-id="ea0ee-171">\*\* [!INCLUDE[ssSampleDBCoShort](../includes/sssampledbcoshort-md.md)] DW 2012\*\* 데이터 원본 뷰로 전환 하려면 솔루션 탐색기의 **데이터 원본 뷰** 폴더에서 해당 뷰를 두 번 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea0ee-171">To switch to the **[!INCLUDE[ssSampleDBCoShort](../includes/sssampledbcoshort-md.md)] DW 2012** data source view, double-click it in the **Data Source Views** folder in Solution Explorer.</span></span>  
  
2.  <span data-ttu-id="ea0ee-172">**테이블** 창에서을 마우스 오른쪽 단추로 클릭 한 `Date` 다음 **새 명명 된 계산**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea0ee-172">In the **Tables** pane, right-click `Date`, and then click **New Named Calculation**.</span></span>  
  
3.  <span data-ttu-id="ea0ee-173">**명명 된 계산 만들기** 대화 상자에서 `MonthName` **열 이름** 상자에를 입력 하 고 **식** 상자에 다음 문을 입력 하거나 복사 하 여 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="ea0ee-173">In the **Create Named Calculation** dialog box, type `MonthName` in the **Column name** box, and then type or copy and paste the following statement in the **Expression** box:</span></span>  
  
    ```  
    EnglishMonthName+' '+ CONVERT(CHAR (4), CalendarYear)  
    ```  
  
     <span data-ttu-id="ea0ee-174">이 문은 테이블에 있는 월 및 각 월의 연도를 새 열에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="ea0ee-174">The statement concatenates the month and year for each month in the table into a new column.</span></span>  
  
4.  <span data-ttu-id="ea0ee-175">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ea0ee-175">Click **OK**.</span></span>  
  
5.  <span data-ttu-id="ea0ee-176">**테이블** 창에서을 마우스 오른쪽 단추로 클릭 한 `Date` 다음 **새 명명 된 계산**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea0ee-176">In the **Tables** pane, right-click `Date`, and then click **New Named Calculation**.</span></span>  
  
6.  <span data-ttu-id="ea0ee-177">**명명 된 계산 만들기** 대화 상자에서 `CalendarQuarterDesc` **열 이름** 상자에를 입력 하 고 **식** 상자에 다음 SQL 스크립트를 입력 하거나 복사 하 여 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="ea0ee-177">In the **Create Named Calculation** dialog box, type `CalendarQuarterDesc` in the **Column name** box, and then type or copy and paste the following SQL script in the **Expression** box:</span></span>  
  
    ```  
    'Q' + CONVERT(CHAR (1), CalendarQuarter) +' '+ 'CY ' +  
    CONVERT(CHAR (4), CalendarYear)  
    ```  
  
     <span data-ttu-id="ea0ee-178">이 SQL 스크립트는 테이블에 있는 분기와 각 분기의 연도를 새 열에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="ea0ee-178">This SQL script concatenates the calendar quarter and year for each quarter in the table into a new column.</span></span>  
  
7.  <span data-ttu-id="ea0ee-179">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ea0ee-179">Click **OK**.</span></span>  
  
8.  <span data-ttu-id="ea0ee-180">**테이블** 창에서을 마우스 오른쪽 단추로 클릭 한 `Date` 다음 **새 명명 된 계산**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea0ee-180">In the **Tables** pane, right-click `Date`, and then click **New Named Calculation**.</span></span>  
  
9. <span data-ttu-id="ea0ee-181">**명명 된 계산 만들기** 대화 상자에서 `CalendarSemesterDesc` **열 이름** 상자에를 입력 하 고 **식** 상자에 다음 SQL 스크립트를 입력 하거나 복사 하 여 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="ea0ee-181">In the **Create Named Calculation** dialog box, type `CalendarSemesterDesc` in the **Column name** box, and then type or copy and paste the following SQL script in the **Expression** box:</span></span>  
  
    ```  
    CASE  
    WHEN CalendarSemester = 1 THEN 'H1' + ' ' + 'CY' + ' '   
           + CONVERT(CHAR(4), CalendarYear)  
    ELSE  
    'H2' + ' ' + 'CY' + ' ' + CONVERT(CHAR(4), CalendarYear)  
    END  
    ```  
  
     <span data-ttu-id="ea0ee-182">이 SQL 스크립트는 테이블에 있는 반기와 각 반기의 연도를 새 열에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="ea0ee-182">This SQL script concatenates the calendar semester and year for each semester in the table into a new column.</span></span>  
  
10. <span data-ttu-id="ea0ee-183">**확인.**</span><span class="sxs-lookup"><span data-stu-id="ea0ee-183">Click **OK.**</span></span>  
  
11. <span data-ttu-id="ea0ee-184">**파일** 메뉴에서 **모두 저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ea0ee-184">On the **File** menu, click **Save All**.</span></span>  
  
## <a name="defining-composite-keycolumns-and-setting-the-name-column"></a><span data-ttu-id="ea0ee-185">복합 KeyColumns 정의 및 이름 열 설정</span><span class="sxs-lookup"><span data-stu-id="ea0ee-185">Defining Composite KeyColumns and Setting the Name Column</span></span>  
 <span data-ttu-id="ea0ee-186">**KeyColumns** 속성에는 특성의 키를 나타내는 열이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="ea0ee-186">The **KeyColumns** property contains the column or columns that represent the key for the attribute.</span></span> <span data-ttu-id="ea0ee-187">이 태스크에서는 복합 **KeyColumns**를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="ea0ee-187">In this task, you will define composite **KeyColumns**.</span></span>  
  
#### <a name="to-define-composite-keycolumns-for-the-english-month-name-attribute"></a><span data-ttu-id="ea0ee-188">English Month Name 특성에 대한 복합 KeyColumns를 정의하려면</span><span class="sxs-lookup"><span data-stu-id="ea0ee-188">To define composite KeyColumns for the English Month Name attribute</span></span>  
  
1.  <span data-ttu-id="ea0ee-189">Date 차원에 대한 **차원 구조** 탭을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="ea0ee-189">Open the **Dimension Structure** tab for the Date dimension.</span></span>  
  
2.  <span data-ttu-id="ea0ee-190">**특성** 창에서 **English Month Name** 특성을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ea0ee-190">In the **Attributes** pane, click the **English Month Name** attribute.</span></span>  
  
3.  <span data-ttu-id="ea0ee-191">**속성** 창에서 **KeyColumns** 필드를 클릭한 후 찾아보기 단추(**...**)를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ea0ee-191">In the **Properties** window, click the **KeyColumns** field, and then click the browse (**...**) button.</span></span>  
  
4.  <span data-ttu-id="ea0ee-192">**키 열** 대화 상자의 **사용 가능한 열** 목록에서 **calendaryear**열을 선택한 후 단추를 클릭 합니다 **>** .</span><span class="sxs-lookup"><span data-stu-id="ea0ee-192">In the **Key Columns** dialog box, in the **Available Columns** list, select the column **CalendarYear**, and then click the **>** button.</span></span>  
  
5.  <span data-ttu-id="ea0ee-193">**EnglishMonthName** 및 **CalendarYear** 열이 **키 열** 목록에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="ea0ee-193">The **EnglishMonthName** and **CalendarYear** columns are now displayed in the **Key Columns** list.</span></span>  
  
6.  <span data-ttu-id="ea0ee-194">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ea0ee-194">Click **OK**.</span></span>  
  
7.  <span data-ttu-id="ea0ee-195">**EnglishMonthName** 특성의 **NameColumn** 속성을 설정하려면 속성 창에서 **NameColumn** 필드를 클릭한 후 찾아보기 단추(**...**)를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ea0ee-195">To set the **NameColumn** property of the **EnglishMonthName** attribute, click the **NameColumn** field in the Properties window, and then click the browse (**...**) button.</span></span>  
  
8.  <span data-ttu-id="ea0ee-196">**이름 열** 대화 상자의 **원본 열** 목록에서 `MonthName` 를 선택한 다음 **확인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea0ee-196">In the **Name Column** dialog box, in the **Source Column** list, select `MonthName`, and then click **OK**.</span></span>  
  
9. <span data-ttu-id="ea0ee-197">**파일** 메뉴에서 **모두 저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ea0ee-197">On the **File** menu, click **Save All**.</span></span>  
  
#### <a name="to-define-composite-keycolumns-for-the-calendar-quarter-attribute"></a><span data-ttu-id="ea0ee-198">Calendar Quarter 특성에 대한 복합 KeyColumns를 정의하려면</span><span class="sxs-lookup"><span data-stu-id="ea0ee-198">To define composite KeyColumns for the Calendar Quarter attribute</span></span>  
  
1.  <span data-ttu-id="ea0ee-199">**특성** 창에서 **Calendar Quarter** 특성을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ea0ee-199">In the **Attributes** pane, click the **Calendar Quarter** attribute.</span></span>  
  
2.  <span data-ttu-id="ea0ee-200">**속성** 창에서 **KeyColumns** 필드를 클릭한 후 찾아보기 단추(**...**)를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ea0ee-200">In the **Properties** window, click the **KeyColumns** field, and then click the browse (**...**) button.</span></span>  
  
3.  <span data-ttu-id="ea0ee-201">**키 열** 대화 상자의 **사용 가능한 열** 목록에서 **calendaryear**열을 선택한 후 단추를 클릭 합니다 **>** .</span><span class="sxs-lookup"><span data-stu-id="ea0ee-201">In the **Key Columns** dialog box, in the **Available Columns** list, select the column **CalendarYear**, and then click the **>** button.</span></span>  
  
     <span data-ttu-id="ea0ee-202">**CalendarQuarter** 및 **CalendarYear** 열이 **키 열** 목록에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="ea0ee-202">The **CalendarQuarter** and **CalendarYear** columns are now displayed in the **Key Columns** list.</span></span>  
  
4.  <span data-ttu-id="ea0ee-203">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ea0ee-203">Click **OK**.</span></span>  
  
5.  <span data-ttu-id="ea0ee-204">**Calendar Quarter** 특성의 **NameColumn** 속성을 설정하려면 속성 창에서 **NameColumn** 필드를 클릭한 후 찾아보기 단추(**...**)를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ea0ee-204">To set the **NameColumn** property of the **Calendar Quarter** attribute, click the **NameColumn** field in the Properties window, and then click the browse (**...**) button.</span></span>  
  
6.  <span data-ttu-id="ea0ee-205">**이름 열** 대화 상자의 **원본 열** 목록에서 `CalendarQuarterDesc` 를 선택한 다음 **확인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea0ee-205">In the **Name Column** dialog box, in the **Source Column** list, select `CalendarQuarterDesc`, and then click **OK**.</span></span>  
  
7.  <span data-ttu-id="ea0ee-206">**파일** 메뉴에서 **모두 저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ea0ee-206">On the **File** menu, click **Save All**.</span></span>  
  
#### <a name="to-define-composite-keycolumns-for-the-calendar-semester-attribute"></a><span data-ttu-id="ea0ee-207">Calendar Semester 특성에 대한 복합 KeyColumns를 정의하려면</span><span class="sxs-lookup"><span data-stu-id="ea0ee-207">To define composite KeyColumns for the Calendar Semester attribute</span></span>  
  
1.  <span data-ttu-id="ea0ee-208">**특성** 창에서 **Calendar Semester** 특성을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ea0ee-208">In the **Attributes** pane, click the **Calendar Semester** attribute.</span></span>  
  
2.  <span data-ttu-id="ea0ee-209">**속성** 창에서 **KeyColumns** 필드를 클릭한 후 찾아보기 단추(**...**)를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ea0ee-209">In the **Properties** window, click the **KeyColumns** field, and then click the browse (**...**) button.</span></span>  
  
3.  <span data-ttu-id="ea0ee-210">**키 열** 대화 상자의 **사용 가능한 열** 목록에서 **CalendarYear**열을 선택한 후 **>** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ea0ee-210">In the **Key Columns** dialog box, in the **Available Columns** list, select the column, **CalendarYear**, and then click the **>** button.</span></span>  
  
     <span data-ttu-id="ea0ee-211">**CalendarSemester** 및 **CalendarYear** 열이 **키 열** 목록에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="ea0ee-211">The **CalendarSemester** and **CalendarYear** columns are now displayed in the **Key Columns** list.</span></span>  
  
4.  <span data-ttu-id="ea0ee-212">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ea0ee-212">Click **OK**.</span></span>  
  
5.  <span data-ttu-id="ea0ee-213">**Calendar Semester** 특성의 **NameColumn** 속성을 설정하려면 속성 창에서 **NameColumn** 필드를 클릭한 후 찾아보기 단추(**...**)를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ea0ee-213">To set the **NameColumn** property of the **Calendar Semester** attribute, click the **NameColumn** field in the property window, and then click the browse (**...**) button.</span></span>  
  
6.  <span data-ttu-id="ea0ee-214">**이름 열** 대화 상자의 **원본 열** 목록에서 `CalendarSemesterDesc` 를 선택한 다음 **확인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea0ee-214">In the **Name Column** dialog box, in the **Source Column** list, select `CalendarSemesterDesc`, and then click **OK**.</span></span>  
  
7.  <span data-ttu-id="ea0ee-215">**파일** 메뉴에서 **모두 저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ea0ee-215">On the **File** menu, click **Save All**.</span></span>  
  
## <a name="deploying-and-viewing-the-changes"></a><span data-ttu-id="ea0ee-216">변경 내용 배포 및 표시</span><span class="sxs-lookup"><span data-stu-id="ea0ee-216">Deploying and Viewing the Changes</span></span>  
 <span data-ttu-id="ea0ee-217">특성과 계층을 변경한 후에 변경 내용을 표시하려면 먼저 변경 내용을 배포하고 관련 개체를 다시 처리해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea0ee-217">After you have changed attributes and hierarchies, you must deploy the changes and reprocess the related objects before you can view the changes.</span></span>  
  
#### <a name="to-deploy-and-view-the-changes"></a><span data-ttu-id="ea0ee-218">변경 내용을 배포하고 표시하려면</span><span class="sxs-lookup"><span data-stu-id="ea0ee-218">To deploy and view the changes</span></span>  
  
1.  <span data-ttu-id="ea0ee-219">**의** 빌드 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]메뉴에서 **Analysis Services Tutorial 배포**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ea0ee-219">On the **Build** menu of [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], click **Deploy Analysis Services Tutorial**.</span></span>  
  
2.  <span data-ttu-id="ea0ee-220">**배포가 완료 되었습니다** . 메시지를 받은 후 차원에 대 한 **차원 디자이너** 의 **브라우저** 탭을 클릭 한 `Date` 다음 디자이너 도구 모음에서 다시 연결 단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea0ee-220">After you have received the **Deployment Completed Successfully** message, click the **Browser** tab of **Dimension Designer** for the `Date` dimension, and then click the Reconnect button on the toolbar of the designer.</span></span>  
  
3.  <span data-ttu-id="ea0ee-221">**계층** 목록에서 **Calendar Quarter** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ea0ee-221">Select **Calendar Quarter** from the **Hierarchy** list.</span></span> <span data-ttu-id="ea0ee-222">**Calendar Quarter** 특성 계층의 멤버를 검토합니다.</span><span class="sxs-lookup"><span data-stu-id="ea0ee-222">Review the members in the **Calendar Quarter** attribute hierarchy.</span></span>  
  
     <span data-ttu-id="ea0ee-223">이름으로 사용할 명명된 계산을 만든 덕분에 **Calendar Quarter** 특성 계층의 멤버 이름이 보다 명확하고 알아보기 쉬움을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ea0ee-223">Notice that the names of the members of the **Calendar Quarter** attribute hierarchy are clearer and easier to use because you created a named calculation to use as the name.</span></span> <span data-ttu-id="ea0ee-224">이제 **Calendar Quarter** 특성 계층에 각 연도의 각 분기에 대한 멤버가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ea0ee-224">Members now exist in the **Calendar Quarter** attribute hierarchy for each quarter in each year.</span></span> <span data-ttu-id="ea0ee-225">멤버는 시간순으로 정렬되지 않고</span><span class="sxs-lookup"><span data-stu-id="ea0ee-225">The members are not sorted in chronological order.</span></span> <span data-ttu-id="ea0ee-226">분기순으로 정렬된 다음 연도순으로 정렬됩니다.</span><span class="sxs-lookup"><span data-stu-id="ea0ee-226">Instead they are sorted by quarter and then by year.</span></span> <span data-ttu-id="ea0ee-227">이 항목의 다음 태스크에서는 이 동작을 수정하여 이 특성 계층의 멤버를 연도순으로 정렬한 다음 분기순으로 정렬합니다.</span><span class="sxs-lookup"><span data-stu-id="ea0ee-227">In the next task in this topic, you will modify this behavior to sort the members of this attribute hierarchy by year and then by quarter.</span></span>  
  
4.  <span data-ttu-id="ea0ee-228">**English Month Name** 및 **Calendar Semester** 특성 계층의 멤버를 검토합니다.</span><span class="sxs-lookup"><span data-stu-id="ea0ee-228">Review the members of the **English Month Name** and **Calendar Semester** attribute hierarchies.</span></span>  
  
     <span data-ttu-id="ea0ee-229">이 계층의 멤버도 시간순으로 정렬되지 않고</span><span class="sxs-lookup"><span data-stu-id="ea0ee-229">Notice that the members of these hierarchies are also not sorted in chronological order.</span></span> <span data-ttu-id="ea0ee-230">각각 월이나 반기순으로 정렬된 다음 연도순으로 정렬됩니다.</span><span class="sxs-lookup"><span data-stu-id="ea0ee-230">Instead, they are sorted by month or semester, respectively, and then by year.</span></span> <span data-ttu-id="ea0ee-231">이 항목의 다음 태스크에서는 이 동작을 수정하여 이 정렬 순서를 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="ea0ee-231">In the next task in this topic, you will modify this behavior to change this sort order.</span></span>  
  
## <a name="changing-the-sort-order-by-modifying-composite-key-member-order"></a><span data-ttu-id="ea0ee-232">복합 키 멤버 순서를 수정하여 정렬 순서 변경</span><span class="sxs-lookup"><span data-stu-id="ea0ee-232">Changing the Sort Order by Modifying Composite Key Member Order</span></span>  
 <span data-ttu-id="ea0ee-233">이 태스크에서는 복합 키를 구성하는 키의 순서를 변경하여 정렬 순서를 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="ea0ee-233">In this task, you will change the sort order by changing the order of the keys that make up the composite key.</span></span>  
  
#### <a name="to-modify-the-composite-key-member-order"></a><span data-ttu-id="ea0ee-234">복합 키 멤버 순서를 수정하려면</span><span class="sxs-lookup"><span data-stu-id="ea0ee-234">To modify the composite key member order</span></span>  
  
1.  <span data-ttu-id="ea0ee-235">차원에 대 한 차원 디자이너의 **차원 구조** 탭을 연 `Date` 다음 **특성** 창에서 **Calendar 반기** 를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea0ee-235">Open the **Dimension Structure** tab of Dimension Designer for the `Date` dimension, and then select **Calendar Semester** in the **Attributes** pane.</span></span>  
  
2.  <span data-ttu-id="ea0ee-236">속성 창에서 **OrderBy** 속성 값을 검토합니다.</span><span class="sxs-lookup"><span data-stu-id="ea0ee-236">In the Properties window, review the value for the **OrderBy** property.</span></span> <span data-ttu-id="ea0ee-237">**키**로 설정되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ea0ee-237">It is set to **Key**.</span></span>  
  
     <span data-ttu-id="ea0ee-238">**Calendar Semester** 특성 계층의 멤버는 키 값을 기준으로 정렬됩니다.</span><span class="sxs-lookup"><span data-stu-id="ea0ee-238">The members of the **Calendar Semester** attribute hierarchy are sorted by their key value.</span></span> <span data-ttu-id="ea0ee-239">복합 키를 사용하면 멤버 키가 먼저 첫 번째 멤버 키의 값을 기준으로 정렬된 다음 두 번째 멤버 키 값을 기준으로 정렬됩니다.</span><span class="sxs-lookup"><span data-stu-id="ea0ee-239">With a composite key, the ordering of the member keys is based first on the value of the first member key, and then on the value of the second member key.</span></span> <span data-ttu-id="ea0ee-240">즉 **Calendar Semester** 특성 계층의 멤버는 먼저 반기순으로 정렬된 다음 연도순으로 정렬됩니다.</span><span class="sxs-lookup"><span data-stu-id="ea0ee-240">In other words, the members of the **Calendar Semester** attribute hierarchy are sorted first by semester and then by year.</span></span>  
  
3.  <span data-ttu-id="ea0ee-241">속성 창에서 줄임표 단추(**...**)를 클릭하여 **KeyColumns** 속성 값을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="ea0ee-241">In the Properties window, click the ellipsis browse button (**...**) to change the **KeyColumns** property value.</span></span>  
  
4.  <span data-ttu-id="ea0ee-242">**키 열** 대화 상자의 **키 열** 목록에서 **CalendarSemester** 가 선택되어 있는지 확인한 후 아래쪽 화살표를 클릭하여 이 복합 키 멤버의 순서를 반대로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="ea0ee-242">In the **Key Columns** list of the **Key Columns** dialog box, verify that **CalendarSemester** is selected, and then click the down arrow to reverse the order of the members of this composite key.</span></span> <span data-ttu-id="ea0ee-243">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ea0ee-243">Click **OK**.</span></span>  
  
     <span data-ttu-id="ea0ee-244">이제 특성 계층의 멤버가 연도순으로 정렬된 다음 반기순으로 정렬됩니다.</span><span class="sxs-lookup"><span data-stu-id="ea0ee-244">The members of the attribute hierarchy are now sorted first by year and then by semester.</span></span>  
  
5.  <span data-ttu-id="ea0ee-245">**특성** 창에서 **Calendar Quarter** 를 선택하고 속성 창에서**KeyColumns**속성의 줄임표 단추( **...** )를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ea0ee-245">Select **Calendar Quarter** in the **Attributes** pane, and then click the ellipsis browse button (**...**) for the **KeyColumns** property in the Properties window.</span></span>  
  
6.  <span data-ttu-id="ea0ee-246">**키 열** 대화 상자의 **키 열** 목록에서 **CalendarQuarter** 가 선택되어 있는지 확인한 후 아래쪽 화살표를 클릭하여 이 복합 키 멤버의 순서를 반대로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="ea0ee-246">In the **Key Columns** list of the **Key Columns** dialog box, verify that **CalendarQuarter** is selected, and then click the down arrow to reverse the order of the members of this composite key.</span></span> <span data-ttu-id="ea0ee-247">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ea0ee-247">Click **OK**.</span></span>  
  
     <span data-ttu-id="ea0ee-248">이제 특성 계층의 멤버가 연도순으로 정렬된 다음 분기순으로 정렬됩니다.</span><span class="sxs-lookup"><span data-stu-id="ea0ee-248">The members of the attribute hierarchy are now sorted first by year and then by quarter.</span></span>  
  
7.  <span data-ttu-id="ea0ee-249">**특성** 창에서 **English Month Name** 을 선택하고 속성 창에서**KeyColumns**속성의 줄임표 단추( **...** )를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ea0ee-249">Select **English Month Name** in the **Attributes** pane, and then click the ellipsis button (**...**) for the **KeyColumns** property in the Properties window.</span></span>  
  
8.  <span data-ttu-id="ea0ee-250">**키 열** 대화 상자의 **키 열** 목록에서 **EnglishMonthName** 이 선택되어 있는지 확인한 후 아래쪽 화살표를 클릭하여 이 복합 키 멤버의 순서를 반대로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="ea0ee-250">In the **Key Columns** list of the **Key Columns** dialog box, verify that **EnglishMonthName** is selected, and then click the down arrow to reverse the order of the members of this composite key.</span></span> <span data-ttu-id="ea0ee-251">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ea0ee-251">Click **OK**.</span></span>  
  
     <span data-ttu-id="ea0ee-252">이제 특성 계층의 멤버가 연도순으로 정렬된 다음 월순으로 정렬됩니다.</span><span class="sxs-lookup"><span data-stu-id="ea0ee-252">The members of the attribute hierarchy are now sorted first by year and then by month.</span></span>  
  
9. <span data-ttu-id="ea0ee-253">**의** 빌드 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]메뉴에서 **Analysis Services Tutorial 배포**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ea0ee-253">On the **Build** menu of [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], click **Deploy Analysis Services Tutorial**.</span></span> <span data-ttu-id="ea0ee-254">배포가 성공적으로 완료 되 면 차원에 대 한 차원 디자이너에서 **브라우저** 탭을 클릭 합니다 `Date` .</span><span class="sxs-lookup"><span data-stu-id="ea0ee-254">When deployment has successfully completed, click the **Browser** tab in Dimension Designer for the `Date` dimension.</span></span>  
  
10. <span data-ttu-id="ea0ee-255">**브라우저** 탭의 도구 모음에서 다시 연결 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ea0ee-255">On the toolbar of the **Browser** tab, click the Reconnect button.</span></span>  
  
11. <span data-ttu-id="ea0ee-256">**Calendar Quarter** 및 **Calendar Semester** 특성 계층의 멤버를 검토합니다.</span><span class="sxs-lookup"><span data-stu-id="ea0ee-256">Review the members of the **Calendar Quarter** and **Calendar Semester** attribute hierarchies.</span></span>  
  
     <span data-ttu-id="ea0ee-257">이 계층의 멤버는 이제 시간순으로 정렬되고 연도순으로 정렬된 다음 각각 분기순이나 반기순으로 정렬됩니다.</span><span class="sxs-lookup"><span data-stu-id="ea0ee-257">Notice that the members of these hierarchies are now sorted in chronological order, by year and then by quarter or semester, respectively.</span></span>  
  
12. <span data-ttu-id="ea0ee-258">**English Month Name** 특성 계층의 멤버를 검토합니다.</span><span class="sxs-lookup"><span data-stu-id="ea0ee-258">Review the members of the **English Month Name** attribute hierarchy.</span></span>  
  
     <span data-ttu-id="ea0ee-259">이제 계층의 멤버가 연도순으로 정렬된 다음 월 이름의 사전순으로 정렬됩니다.</span><span class="sxs-lookup"><span data-stu-id="ea0ee-259">Notice that the members of the hierarchy are now sorted first by year and then alphabetically by month.</span></span> <span data-ttu-id="ea0ee-260">이는 기본 관계형 데이터베이스의 nvarchar 데이터 형식에 기초하여 데이터 원본 뷰의 EnglishCalendarMonth 열에 대한 데이터 형식이 문자열 열이기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="ea0ee-260">This is because the data type for the EnglishCalendarMonth column in the data source view is a string column, based on the nvarchar data type in the underlying relational database.</span></span> <span data-ttu-id="ea0ee-261">각 연도 내에서 월을 시간 순으로 정렬하는 방법에 대한 자세한 내용은 [보조 특성을 기준으로 특성 멤버 정렬](lesson-4-5-sorting-attribute-members-based-on-a-secondary-attribute.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ea0ee-261">For information about how to enable the months to be sorted chronologically within each year, see [Sorting Attribute Members Based on a Secondary Attribute](lesson-4-5-sorting-attribute-members-based-on-a-secondary-attribute.md).</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="ea0ee-262">단원의 다음 태스크</span><span class="sxs-lookup"><span data-stu-id="ea0ee-262">Next Task in Lesson</span></span>  
 [<span data-ttu-id="ea0ee-263">배포된 큐브 찾아보기</span><span class="sxs-lookup"><span data-stu-id="ea0ee-263">Browsing the Deployed Cube</span></span>](lesson-3-5-browsing-the-deployed-cube.md)  
  
## <a name="see-also"></a><span data-ttu-id="ea0ee-264">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ea0ee-264">See Also</span></span>  
 [<span data-ttu-id="ea0ee-265">다차원 모델의 차원</span><span class="sxs-lookup"><span data-stu-id="ea0ee-265">Dimensions in Multidimensional Models</span></span>](multidimensional-models/dimensions-in-multidimensional-models.md)  
  
  
