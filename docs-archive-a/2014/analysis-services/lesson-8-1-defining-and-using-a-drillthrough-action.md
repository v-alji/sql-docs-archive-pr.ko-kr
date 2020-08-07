---
title: 드릴스루 동작 정의 및 사용 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 3765f865-2b93-44be-b290-28e3815d5ecb
author: minewiskan
ms.author: owend
ms.openlocfilehash: ea19a9721d87936bc88b5401c71ee550a47bc1ce
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731024"
---
# <a name="defining-and-using-a-drillthrough-action"></a><span data-ttu-id="e2fa1-102">드릴스루 동작 정의 및 사용</span><span class="sxs-lookup"><span data-stu-id="e2fa1-102">Defining and Using a Drillthrough Action</span></span>
  <span data-ttu-id="e2fa1-103">쿼리가 반환하는 데이터를 올바르게 필터링하지 않고 팩트 차원별로 팩트 데이터의 차원을 지정하면 쿼리 성능이 느려집니다.</span><span class="sxs-lookup"><span data-stu-id="e2fa1-103">Dimensioning fact data by a fact dimension without correctly filtering the data that the query returns can cause slow query performance.</span></span> <span data-ttu-id="e2fa1-104">이 문제를 방지하려면 반환되는 전체 행 수를 제한하는 드릴스루 동작을 정의하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e2fa1-104">To avoid this, you can define a drillthrough action that restricts the total number of rows that are returned.</span></span> <span data-ttu-id="e2fa1-105">이렇게 하면 쿼리 성능이 대폭 향상됩니다.</span><span class="sxs-lookup"><span data-stu-id="e2fa1-105">This will significantly improve query performance.</span></span>  
  
 <span data-ttu-id="e2fa1-106">이 항목의 태스크에서는 인터넷을 통한 판매에 대한 세부 주문 정보를 반환하는 드릴스루 동작을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="e2fa1-106">In the tasks in this topic, you define a drillthrough action to return order detail information for sales to customers over the Internet.</span></span>  
  
## <a name="defining-the-drillthrough-action-properties"></a><span data-ttu-id="e2fa1-107">드릴스루 동작 속성 정의</span><span class="sxs-lookup"><span data-stu-id="e2fa1-107">Defining the Drillthrough Action Properties</span></span>  
  
1.  <span data-ttu-id="e2fa1-108">[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial 큐브에 대한 큐브 디자이너에서 **동작** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e2fa1-108">In Cube Designer for the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube, click the **Actions** tab.</span></span>  
  
     <span data-ttu-id="e2fa1-109">**동작** 탭에는 여러 개의 창이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e2fa1-109">The **Actions** tab includes several panes.</span></span> <span data-ttu-id="e2fa1-110">이 탭 왼쪽에는 **동작 구성 도우미** 창과 **계산 도구** 창이 있고</span><span class="sxs-lookup"><span data-stu-id="e2fa1-110">On the left side of the tab are the **Action Organizer** pane and the **Calculation Tools** pane.</span></span> <span data-ttu-id="e2fa1-111">이러한 두 창의 오른쪽에는 **동작 구성 도우미** 창에서 선택한 동작의 세부 정보가 표시되는 **표시** 창이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e2fa1-111">The pane to the right of these two panes is the **Display** pane, which contains the details of the action that is selected in the **Action Organizer** pane.</span></span>  
  
     <span data-ttu-id="e2fa1-112">다음 그림에서는 큐브 디자이너의 **동작** 탭을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="e2fa1-112">The following image shows the **Actions** tab of Cube Designer.</span></span>  
  
     <span data-ttu-id="e2fa1-113">![큐브 디자이너의 동작 탭](../../2014/tutorials/media/l8-action1.gif "큐브 디자이너의 동작 탭")</span><span class="sxs-lookup"><span data-stu-id="e2fa1-113">![Actions tab of Cube Designer](../../2014/tutorials/media/l8-action1.gif "Actions tab of Cube Designer")</span></span>  
  
2.  <span data-ttu-id="e2fa1-114">**동작** 탭의 도구 모음에서 **새 드릴스루 동작** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e2fa1-114">On the toolbar of the **Actions** tab, click the **New Drillthrough Action** button.</span></span>  
  
     <span data-ttu-id="e2fa1-115">표시 창에 빈 동작 템플릿이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="e2fa1-115">A blank action template appears in the display pane.</span></span>  
  
     <span data-ttu-id="e2fa1-116">![표시 창의 빈 동작 템플릿](../../2014/tutorials/media/l8-action2.gif "표시 창의 빈 동작 템플릿")</span><span class="sxs-lookup"><span data-stu-id="e2fa1-116">![Blank Action template in the display pane](../../2014/tutorials/media/l8-action2.gif "Blank Action template in the display pane")</span></span>  
  
3.  <span data-ttu-id="e2fa1-117">**이름** 상자에서이 작업의 이름을로 변경 `Internet Sales Details Drillthrough Action` 합니다.</span><span class="sxs-lookup"><span data-stu-id="e2fa1-117">In the **Name** box, change the name of this action to `Internet Sales Details Drillthrough Action`.</span></span>  
  
4.  <span data-ttu-id="e2fa1-118">**측정값 그룹 멤버** 목록에서 **Internet Sales**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e2fa1-118">In the **Measure group members** list, select **Internet Sales**.</span></span>  
  
5.  <span data-ttu-id="e2fa1-119">**드릴스루 열** 상자의 **차원** 목록에서 **Internet Sales Order Details** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e2fa1-119">In the **Drillthrough Columns** box, select **Internet Sales Order Details** in the **Dimensions** list.</span></span>  
  
6.  <span data-ttu-id="e2fa1-120">**반환 열** 목록에서 **Item Description** 및 **Order Number** 확인란을 선택하고 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e2fa1-120">In the **Return Columns** list, select the **Item Description** and the **Order Number** check boxes, and then click **OK**.</span></span> <span data-ttu-id="e2fa1-121">다음 그림에서는 이 절차의 현재 시점에 표시되어야 하는 동작 템플릿의 모습을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="e2fa1-121">The following image shows the Action template as it should appear at this point in this procedure.</span></span>  
  
     <span data-ttu-id="e2fa1-122">![드릴스루 열 상자](../../2014/tutorials/media/l8-action3.gif "드릴스루 열 상자")</span><span class="sxs-lookup"><span data-stu-id="e2fa1-122">![Drillthrough Columns box](../../2014/tutorials/media/l8-action3.gif "Drillthrough Columns box")</span></span>  
  
7.  <span data-ttu-id="e2fa1-123">다음 그림에 표시된 것처럼 **추가 속성** 상자를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="e2fa1-123">Expand the **Additional Properties** box, as shown in the following image.</span></span>  
  
     <span data-ttu-id="e2fa1-124">![추가 속성 상자](../../2014/tutorials/media/l8-action4.gif "추가 속성 상자")</span><span class="sxs-lookup"><span data-stu-id="e2fa1-124">![Additional Properties box](../../2014/tutorials/media/l8-action4.gif "Additional Properties box")</span></span>  
  
8.  <span data-ttu-id="e2fa1-125">**최대 행** 상자에를 입력 `10` 합니다.</span><span class="sxs-lookup"><span data-stu-id="e2fa1-125">In the **Maximum Rows** box, type `10`.</span></span>  
  
9. <span data-ttu-id="e2fa1-126">**캡션** 상자에를 입력 `Drillthrough to Order Details...` 합니다.</span><span class="sxs-lookup"><span data-stu-id="e2fa1-126">In the **Caption** box, type `Drillthrough to Order Details...`.</span></span>  
  
     <span data-ttu-id="e2fa1-127">이렇게 설정하면 반환되는 행 수가 제한되며 클라이언트 애플리케이션 메뉴에 표시되는 캡션이 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="e2fa1-127">These settings limit the number of rows returned and specify the caption that appears in the client application menu.</span></span> <span data-ttu-id="e2fa1-128">다음 그림에서는 **추가 속성** 상자에서 지정하는 이러한 설정을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="e2fa1-128">The following image shows these settings in the **AdditionalProperties** box.</span></span>  
  
     <span data-ttu-id="e2fa1-129">![추가 속성 상자](../../2014/tutorials/media/l8-action5.gif "추가 속성 상자")</span><span class="sxs-lookup"><span data-stu-id="e2fa1-129">![Additional Properties box](../../2014/tutorials/media/l8-action5.gif "Additional Properties box")</span></span>  
  
## <a name="using-the-drillthrough-action"></a><span data-ttu-id="e2fa1-130">드릴스루 동작 사용</span><span class="sxs-lookup"><span data-stu-id="e2fa1-130">Using the Drillthrough Action</span></span>  
  
1.  <span data-ttu-id="e2fa1-131">**빌드** 메뉴에서 **Analysis Services Tutorial 배포**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e2fa1-131">On the **Build** menu, click **Deploy Analysis Services Tutorial**.</span></span>  
  
2.  <span data-ttu-id="e2fa1-132">배포가 성공적으로 완료되면 **Tutorial 큐브에 대한 큐브 디자이너에서** 브라우저 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 탭을 클릭한 다음 **다시 연결** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e2fa1-132">When deployment has successfully completed, click the **Browser** tab in Cube Designer for the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube, and then click the **Reconnect** button.</span></span>  
  
3.  <span data-ttu-id="e2fa1-133">Excel을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="e2fa1-133">Start Excel.</span></span>  
  
4.  <span data-ttu-id="e2fa1-134">값 영역에 **Internet Sales-Sales Amount** 측정값을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="e2fa1-134">Add the **Internet Sales-Sales Amount** measure to the Values area.</span></span>  
  
5.  <span data-ttu-id="e2fa1-135">**Customer** 차원의 **Location** 폴더에서 **Customer Geography** 사용자 정의 계층을 **보고서 필터** 영역에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="e2fa1-135">Add the **Customer Geography** user-defined hierarchy from the **Location** folder in the **Customer** dimension to the **Report Filter** area.</span></span>  
  
6.  <span data-ttu-id="e2fa1-136">피벗 테이블의 **Customer Geography**에 단일 고객을 선택하는 필터를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="e2fa1-136">On the PivotTable, in **Customer Geography**, add a filter that selects a single customer.</span></span> <span data-ttu-id="e2fa1-137">**All Customers**, **Australia**, **Queensland**, **Brisbane**및 **4000**을 차례로 확장한 후 **Adam Powell**에 대한 확인란을 선택하고 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e2fa1-137">Expand **All Customers**, expand **Australia**, expand **Queensland**, expand **Brisbane**, expand **4000**, select the check box for **Adam Powell**, and then click **OK**.</span></span>  
  
     <span data-ttu-id="e2fa1-138">[!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] 에서 Adam Powell에게 판매한 총 제품 판매액이 데이터 영역에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="e2fa1-138">The total sales of products by [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] to Adam Powell are displayed in the data area.</span></span>  
  
7.  <span data-ttu-id="e2fa1-139">판매액을 마우스 오른쪽 단추로 클릭하고 **추가 동작**을 가리킨 다음 **Drillthrough to Order Details**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e2fa1-139">Right-click on the sales amount, point to **Additional Actions**, and then click **Drillthrough to Order Details**.</span></span>  
  
     <span data-ttu-id="e2fa1-140">다음 그림에 표시된 것처럼 Adam Powell에게 운송된 주문에 대한 세부 정보가 **데이터 샘플 뷰어**에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="e2fa1-140">The details of the orders that were shipped to Adam Powell are displayed in the **Data Sample Viewer**, as shown in the following image.</span></span> <span data-ttu-id="e2fa1-141">그러나 주문일, 기한 및 운송일과 같은 일부 추가 세부 정보가 도움이 될 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e2fa1-141">However, some additional details would also be useful, such as the order date, due date, and ship date.</span></span> <span data-ttu-id="e2fa1-142">다음 절차에서는 이러한 세부 정보를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="e2fa1-142">In the next procedure, you will add these additional details.</span></span>  
  
     <span data-ttu-id="e2fa1-143">![Adam Powell로 운송되는 주문](../../2014/tutorials/media/l8-action6.gif "Adam Powell로 운송되는 주문")</span><span class="sxs-lookup"><span data-stu-id="e2fa1-143">![Orders shipped to Adam Powell](../../2014/tutorials/media/l8-action6.gif "Orders shipped to Adam Powell")</span></span>  
  
8.  <span data-ttu-id="e2fa1-144">Excel 닫기</span><span class="sxs-lookup"><span data-stu-id="e2fa1-144">Close Excel/</span></span>  
  
## <a name="modifying-the-drillthrough-action"></a><span data-ttu-id="e2fa1-145">드릴스루 동작 수정</span><span class="sxs-lookup"><span data-stu-id="e2fa1-145">Modifying the Drillthrough Action</span></span>  
  
1.  <span data-ttu-id="e2fa1-146">**Internet Sales Order Details** 차원에 대한 차원 디자이너를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="e2fa1-146">Open Dimension Designer for the **Internet Sales Order Details** dimension.</span></span>  
  
     <span data-ttu-id="e2fa1-147">이 차원에 대해 특성이 세 개만 정의되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e2fa1-147">Notice that only three attributes have been defined for this dimension.</span></span>  
  
2.  <span data-ttu-id="e2fa1-148">**데이터 원본 뷰** 창에서 열린 영역을 마우스 오른쪽 단추로 클릭한 다음 **모든 테이블 표시**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e2fa1-148">In the **Data Source View** pane, right-click an open area, and then click **Show All Tables**.</span></span>  
  
3.  <span data-ttu-id="e2fa1-149">**서식** 메뉴에서 **자동 레이아웃** 을 가리킨 다음 **다이어그램**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e2fa1-149">On the **Format** menu, point to **Autolayout** and then click **Diagram**.</span></span>  
  
4.  <span data-ttu-id="e2fa1-150">**데이터 원본 뷰** 창의 열린 영역을 마우스 오른쪽 단추로 클릭하여 **InternetSales (dbo.FactInternetSales)** 테이블을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="e2fa1-150">Locate the **InternetSales (dbo.FactInternetSales)** table by right-clicking in an open area of the **Data Source View** pane.</span></span> <span data-ttu-id="e2fa1-151">그런 다음 **테이블 찾기** , **InternetSales** , **확인**을 차례로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e2fa1-151">Then click **Find Table,** click **InternetSales,** and click **OK**.</span></span>  
  
5.  <span data-ttu-id="e2fa1-152">다음 열을 기반으로 새 특성을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e2fa1-152">Create new attributes based on the following columns:</span></span>  
  
    -   <span data-ttu-id="e2fa1-153">OrderDateKey</span><span class="sxs-lookup"><span data-stu-id="e2fa1-153">OrderDateKey</span></span>  
  
    -   <span data-ttu-id="e2fa1-154">DueDateKey</span><span class="sxs-lookup"><span data-stu-id="e2fa1-154">DueDateKey</span></span>  
  
    -   <span data-ttu-id="e2fa1-155">ShipDateKey</span><span class="sxs-lookup"><span data-stu-id="e2fa1-155">ShipDateKey</span></span>  
  
6.  <span data-ttu-id="e2fa1-156">**Order Date Key** 특성의 **name** 속성을로 변경한 `Order Date` 다음 **name column** 속성의 찾아보기 단추를 클릭 하 고 **이름 열** 대화 상자에서 원본 테이블로 **Date** 를 선택 하 고 원본 열로 SimpleDate를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="e2fa1-156">Change the **Name** property for the **Order Date Key** attribute to `Order Date` Then, click the browse button for the **Name Column** property, and in the **Name Column** dialog box, select **Date** as the source table and select SimpleDate as the source column.</span></span> [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
7.  <span data-ttu-id="e2fa1-157">**기한 키** 특성의 **이름** 속성을로 변경 하 `Due Date` 고 **Order date key** 특성과 동일한 메서드를 사용 하 여이 특성의 **name Column** 속성을 **SimpleDate (WChar)** 로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="e2fa1-157">Change the **Name** property for the **Due Date Key** attribute to `Due Date`, and then, by using the same method as the **Order Date Key** attribute, change the **Name Column** property for this attribute to **Date.SimpleDate (WChar)**.</span></span>  
  
8.  <span data-ttu-id="e2fa1-158">**운송 날짜 키** 특성의 **이름** 속성을로 변경 하 `Ship Date` 고이 특성의 **Name Column** 속성을 **SimpleDate (WChar)** 로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="e2fa1-158">Change the **Name** property for the **Ship Date Key** attribute to `Ship Date`, and then change the **Name Column** property for this attribute to **Date.SimpleDate (WChar)**.</span></span>  
  
9. <span data-ttu-id="e2fa1-159">**Tutorial 큐브에 대한 큐브 디자이너의** 동작 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 탭으로 전환합니다.</span><span class="sxs-lookup"><span data-stu-id="e2fa1-159">Switch to the **Actions** tab of Cube Designer for the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube.</span></span>  
  
10. <span data-ttu-id="e2fa1-160">**드릴스루 열** 상자에서 확인란을 선택하여 **반환 열** 목록에 다음 열을 추가한 후 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e2fa1-160">In the **Drillthrough Columns** box, select the check boxes to add the following columns to the **Return Columns** list, and then click **OK**:</span></span>  
  
    -   <span data-ttu-id="e2fa1-161">Order Date</span><span class="sxs-lookup"><span data-stu-id="e2fa1-161">Order Date</span></span>  
  
    -   <span data-ttu-id="e2fa1-162">Due Date</span><span class="sxs-lookup"><span data-stu-id="e2fa1-162">Due Date</span></span>  
  
    -   <span data-ttu-id="e2fa1-163">Ship Date</span><span class="sxs-lookup"><span data-stu-id="e2fa1-163">Ship Date</span></span>  
  
     <span data-ttu-id="e2fa1-164">다음 그림에서는 이러한 열이 선택된 모습을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="e2fa1-164">The following image shows these columns selected.</span></span>  
  
     <span data-ttu-id="e2fa1-165">![드릴스루 열 상자](../../2014/tutorials/media/l8-action7.gif "드릴스루 열 상자")</span><span class="sxs-lookup"><span data-stu-id="e2fa1-165">![Drillthrough Columns box](../../2014/tutorials/media/l8-action7.gif "Drillthrough Columns box")</span></span>  
  
## <a name="reviewing-the-modified-drillthrough-action"></a><span data-ttu-id="e2fa1-166">수정된 드릴스루 동작 검토</span><span class="sxs-lookup"><span data-stu-id="e2fa1-166">Reviewing the Modified Drillthrough Action</span></span>  
  
1.  <span data-ttu-id="e2fa1-167">**빌드** 메뉴에서 **Analysis Services Tutorial 배포**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e2fa1-167">On the **Build** menu, click **Deploy Analysis Services Tutorial**.</span></span>  
  
2.  <span data-ttu-id="e2fa1-168">배포가 성공적으로 완료되면 **Tutorial 큐브에 대한 큐브 디자이너에서** 브라우저 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 탭으로 전환한 다음 **다시 연결** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e2fa1-168">When deployment has successfully completed, switch to the **Browser** tab in Cube Designer for the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube, and then click the **Reconnect** button.</span></span>  
  
3.  <span data-ttu-id="e2fa1-169">Excel을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="e2fa1-169">Start Excel.</span></span>  
  
4.  <span data-ttu-id="e2fa1-170">값 영역의 **Internet Sales-Sales Amount** 와 보고서 필터의 **Customer Geography** 를 사용하여 피벗 테이블을 다시 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e2fa1-170">Recreate the PivotTable using **Internet Sales-Sales Amount** in the Values area and **Customer Geography** in the Report Filter.</span></span>  
  
     <span data-ttu-id="e2fa1-171">**All Customers**, **Australia**, **Queensland**, **Brisbane**, **4000**, **Adam Powell**에서 선택하는 필터를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="e2fa1-171">Add a filter that selects from **All Customers**, **Australia**, **Queensland**, **Brisbane**, **4000**, **Adam Powell**.</span></span>  
  
5.  <span data-ttu-id="e2fa1-172">**Internet Sales-Sales Amount** 데이터 셀을 클릭하고 **추가 동작**을 가리킨 다음 **Drillthrough to Order Details**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e2fa1-172">Click the **Internet Sales-Sales Amount** data cell, point to **Additional Actions**, and then click **Drillthrough to Order Details**.</span></span>  
  
     <span data-ttu-id="e2fa1-173">Adam Powell에게 운송된 이 주문에 대한 세부 정보가 임시 워크시트에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="e2fa1-173">The details of these orders shipped to Adam Powell are displayed in a temporary worksheet.</span></span> <span data-ttu-id="e2fa1-174">다음 그림에 표시된 것처럼 여기에는 항목에 대한 설명, 주문 번호, 주문 날짜, 기한 및 운송 날짜 정보가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="e2fa1-174">This includes item description, order number, order date, due date, and ship date information, as shown in the following image.</span></span>  
  
     <span data-ttu-id="e2fa1-175">![Adam Powell로 운송되는 주문](../../2014/tutorials/media/l8-action8.gif "Adam Powell로 운송되는 주문")</span><span class="sxs-lookup"><span data-stu-id="e2fa1-175">![Orders shipped to Adam Powell](../../2014/tutorials/media/l8-action8.gif "Orders shipped to Adam Powell")</span></span>  
  
## <a name="next-lesson"></a><span data-ttu-id="e2fa1-176">다음 단원</span><span class="sxs-lookup"><span data-stu-id="e2fa1-176">Next Lesson</span></span>  
 [<span data-ttu-id="e2fa1-177">9단원: 큐브 뷰 및 번역 정의</span><span class="sxs-lookup"><span data-stu-id="e2fa1-177">Lesson 9: Defining Perspectives and Translations</span></span>](lesson-9-defining-perspectives-and-translations.md)  
  
## <a name="see-also"></a><span data-ttu-id="e2fa1-178">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e2fa1-178">See Also</span></span>  
 <span data-ttu-id="e2fa1-179">[작업 &#40;Analysis Services 다차원 데이터&#41;](multidimensional-models/actions-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="e2fa1-179">[Actions &#40;Analysis Services - Multidimensional Data&#41;](multidimensional-models/actions-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="e2fa1-180">[다차원 모델의 동작](multidimensional-models/actions-in-multidimensional-models.md) </span><span class="sxs-lookup"><span data-stu-id="e2fa1-180">[Actions in Multidimensional Models](multidimensional-models/actions-in-multidimensional-models.md) </span></span>  
 <span data-ttu-id="e2fa1-181">[차원 관계](multidimensional-models-olap-logical-cube-objects/dimension-relationships.md) </span><span class="sxs-lookup"><span data-stu-id="e2fa1-181">[Dimension Relationships](multidimensional-models-olap-logical-cube-objects/dimension-relationships.md) </span></span>  
 <span data-ttu-id="e2fa1-182">[팩트 관계 정의](lesson-5-2-defining-a-fact-relationship.md) </span><span class="sxs-lookup"><span data-stu-id="e2fa1-182">[Defining a Fact Relationship](lesson-5-2-defining-a-fact-relationship.md) </span></span>  
 [<span data-ttu-id="e2fa1-183">팩트 관계 및 팩트 관계 속성 정의</span><span class="sxs-lookup"><span data-stu-id="e2fa1-183">Define a Fact Relationship and Fact Relationship Properties</span></span>](multidimensional-models/define-a-fact-relationship-and-fact-relationship-properties.md)  
  
  
