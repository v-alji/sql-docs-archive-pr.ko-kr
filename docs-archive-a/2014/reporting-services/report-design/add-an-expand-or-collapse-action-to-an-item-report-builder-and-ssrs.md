---
title: 항목에 확장 또는 축소 작업 추가(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 49f07ad6-242b-4861-8fc1-91ca78c36d6c
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 331c6a14a4a898ffcdf86f274c00e7ad3c801ec7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87729063"
---
# <a name="add-an-expand-or-collapse-action-to-an-item-report-builder-and-ssrs"></a><span data-ttu-id="109c5-102">항목에 확장 또는 축소 동작 추가(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="109c5-102">Add an Expand or Collapse Action to an Item (Report Builder and SSRS)</span></span>
  <span data-ttu-id="109c5-103">사용자가 보고서 항목을 대화형으로 확장 또는 축소하거나, 테이블이나 행렬의 경우 그룹과 연결된 행과 열을 축소 또는 확장할 수 있도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="109c5-103">You can enable a user to interactively expand or collapse report items, or expand or collapse rows and columns associated with a group for a table or matrix.</span></span> <span data-ttu-id="109c5-104">사용자가 항목을 확장 또는 축소할 수 있도록 하려면 해당 항목에 표시 유형 속성을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="109c5-104">To allow users to expand or collapse an item, you set the visibility properties for that item.</span></span> <span data-ttu-id="109c5-105">표시 유형을 설정하면 HTML 보고서 뷰어에서 사용할 수 있으며 이를 *드릴다운* 동작이라고도 합니다.</span><span class="sxs-lookup"><span data-stu-id="109c5-105">Setting visibility works in an HTML report viewer, and is sometimes called a *drilldown* action.</span></span>  
  
 <span data-ttu-id="109c5-106">보고서 디자인 뷰에서 확장 및 축소 토글 아이콘을 표시할 입력란의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="109c5-106">In report design view, you specify the name of the text box where you want to display the expand and collapse toggle icons.</span></span> <span data-ttu-id="109c5-107">렌더링된 보고서에서 이 입력란에는 내용 이외에 더하기(+) 또는 빼기(-) 기호가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="109c5-107">In the rendered report, the text box displays a plus (+) or minus (-) sign in addition to its contents.</span></span> <span data-ttu-id="109c5-108">사용자가 이 토글을 클릭하면 보고서 화면이 새로 고쳐져 보고서 항목의 현재 표시 유형 설정에 따라 보고서 항목이 표시되거나 숨겨집니다.</span><span class="sxs-lookup"><span data-stu-id="109c5-108">When the user clicks the toggle, the report display is refreshed to show or hide the report item, based on the current visibility settings for items in the report.</span></span>  
  
 <span data-ttu-id="109c5-109">일반적으로 확장 및 축소 동작은 처음에는 요약 데이터만 표시하고 사용자가 더하기 기호를 클릭하면 상세 데이터가 표시될 수 있도록 하려는 경우에 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="109c5-109">Typically, the expand and collapse action is used to initially display only summary data and to enable the user to click the plus sign to show detail data.</span></span> <span data-ttu-id="109c5-110">예를 들어 처음에는 차트에 대한 값을 표시하는 테이블을 숨기거나 드릴다운 보고서처럼 중첩된 행이나 열 그룹이 있는 테이블의 자식 그룹을 숨길 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="109c5-110">For example, you can initially hide a table that displays values for a chart, or hide child groups for a table with nested row or column groups, as in a drilldown report.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-expand-and-collapse-action-to-a-group"></a><span data-ttu-id="109c5-111">확장 및 축소 동작을 그룹에 추가하려면</span><span class="sxs-lookup"><span data-stu-id="109c5-111">To add expand and collapse action to a group</span></span>  
  
1.  <span data-ttu-id="109c5-112">보고서 디자인 뷰에서 테이블 또는 행렬을 클릭하여 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="109c5-112">In report design view, click the table or matrix to select it.</span></span> <span data-ttu-id="109c5-113">그룹화 창에 행 및 열 그룹이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="109c5-113">The Grouping pane displays the row and column groups.</span></span>  
  
     <span data-ttu-id="109c5-114">![그룹화 창](../media/groupingpane.png "그룹화 창")</span><span class="sxs-lookup"><span data-stu-id="109c5-114">![Grouping Pane](../media/groupingpane.png "Grouping Pane")</span></span>  
  
     <span data-ttu-id="109c5-115">그룹화 창이 나타나지 않는 경우 **보기** 메뉴를 클릭한 다음 **그룹화**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="109c5-115">If the Grouping pane does not appear, click the **View** menu and then click **Grouping**.</span></span>  
  
2.  <span data-ttu-id="109c5-116">그룹화 창 제목 표시줄을 마우스 오른쪽 단추로 클릭한 다음 **고급**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="109c5-116">Right-click anywhere in the title bar of the Grouping pane, and then click **Advanced**.</span></span> <span data-ttu-id="109c5-117">그룹화 창 모드가 전환되어 디자인 화면에 행 및 열의 기본 표시 구조가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="109c5-117">The Grouping pane mode toggles to show the underlying display structure for rows and columns on the design surface.</span></span>  
  
     <span data-ttu-id="109c5-118">![고급 모드 메뉴가 있는 그룹화 창](../media/groupingpane-advancedmode.png "고급 모드 메뉴가 있는 그룹화 창")</span><span class="sxs-lookup"><span data-stu-id="109c5-118">![Grouping Pane with Advanced Mode menu](../media/groupingpane-advancedmode.png "Grouping Pane with Advanced Mode menu")</span></span>  
  
3.  <span data-ttu-id="109c5-119">해당 그룹 창에서 연결된 행 또는 열을 숨기려고 하는 행 그룹 또는 열 그룹의 이름을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="109c5-119">In the appropriate group pane, click the name of the row group or column group for which you want to hide the associated rows or columns.</span></span> <span data-ttu-id="109c5-120">그룹이 선택되고 속성 창에 **테이블릭스 멤버** 속성이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="109c5-120">The group is selected and the Properties pane shows the **Tablix Member** properties.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="109c5-121"> 속성 창이 표시되지 않으면 리본에서 **보기** 를 클릭한 다음 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="109c5-121">If you do not see the Properties pane, click **View** on the Ribbon and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="109c5-122">에서 `Hidden` 다음 옵션 중 하나를 선택 하 여 보고서를 처음 실행할 때이 보고서 항목의 표시 유형을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="109c5-122">In `Hidden`, choose one of the following options to set the visibility of this report item the first time you run a report:</span></span>  
  
    -   <span data-ttu-id="109c5-123">`False`보고서 항목을 표시 하려면 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="109c5-123">Select `False` to display the report item.</span></span>  
  
    -   <span data-ttu-id="109c5-124">`True`보고서 항목을 숨기려면 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="109c5-124">Select `True` to hide the report item.</span></span>  
  
    -   <span data-ttu-id="109c5-125">**\<Expression>** **식** 대화 상자를 열어 표시 유형을 결정 하기 위해 런타임에 계산 되는 식을 만들려면 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="109c5-125">Select **\<Expression>** to open the **Expression** dialog box to create an expression that is evaluated at run time to determine the visibility.</span></span>  
  
5.  <span data-ttu-id="109c5-126">**ToggleItem**의 드롭다운 상자에서 토글 이미지를 추가할 입력란의 이름을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="109c5-126">In **ToggleItem**, from the drop-down box, select the name of a text box to which to add the toggle image.</span></span>  
  
     <span data-ttu-id="109c5-127">다음 이미지에서 Color 행 그룹은 사용자가 연결된 행을 확장 및 축소할 수 있도록 구성되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="109c5-127">In the following image, the Color row group is configured enable users to expand and collapse associated rows.</span></span>  
  
     <span data-ttu-id="109c5-128">![확장할 행 그룹 구성](../media/expandcollapse-confighiddentoggleitemwithnumbers.png "확장할 행 그룹 구성")</span><span class="sxs-lookup"><span data-stu-id="109c5-128">![Configuring a row group to be expanded](../media/expandcollapse-confighiddentoggleitemwithnumbers.png "Configuring a row group to be expanded")</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="109c5-129">토글 이미지가 있는 입력란은 연결된 행 또는 열을 숨기려고 하는 행 또는 열 그룹일 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="109c5-129">The text box with the toggle image cannot be the row or column group for which you want to hide the associated rows or columns.</span></span> <span data-ttu-id="109c5-130">입력란은 숨기려는 항목과 같은 그룹에 있거나 상위 그룹에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="109c5-130">It must either be in the same group as the item that is being hidden or in an ancestor group.</span></span> <span data-ttu-id="109c5-131">예를 들어 자식 그룹과 연결된 행의 표시 유형을 전환하려면 부모 그룹과 연결된 행에 있는 입력란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="109c5-131">For example, to toggle visibility of rows associated with a child group, select a text box in a row associated with the parent group.</span></span>  
  
6.  <span data-ttu-id="109c5-132">토글을 테스트하려면 보고서를 실행하고 토글 이미지가 있는 입력란을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="109c5-132">To test the toggle, run the report and click the text box with the toggle image.</span></span> <span data-ttu-id="109c5-133">보고서 화면이 새로 고쳐져 전환된 표시 유형이 적용된 행 그룹 및 열 그룹이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="109c5-133">The report display refreshes to show row groups and column groups with their toggled visibility.</span></span>  
  
     <span data-ttu-id="109c5-134">![확장 가능한 행 그룹이 있는 실행 중인 보고서](../media/expandcollapse-runreport-rowgroup.png "확장 가능한 행 그룹이 있는 실행 중인 보고서")</span><span class="sxs-lookup"><span data-stu-id="109c5-134">![Running report with expandable row group](../media/expandcollapse-runreport-rowgroup.png "Running report with expandable row group")</span></span>  
  
### <a name="to-add-expand-and-collapse-action-to-a-report-item"></a><span data-ttu-id="109c5-135">확장 및 축소 동작을 보고서 항목에 추가하려면</span><span class="sxs-lookup"><span data-stu-id="109c5-135">To add expand and collapse action to a report item</span></span>  
  
1.  <span data-ttu-id="109c5-136">보고서 디자인 뷰에서 표시 하거나 숨길 보고서 항목을 마우스 오른쪽 단추로 클릭 한 다음 *\<report item>* **속성**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="109c5-136">In report design view, right-click the report item to show or hide, and then click *\<report item>* **Properties**.</span></span> <span data-ttu-id="109c5-137">*\<report item>* 보고서 항목에 대 한 **속성** 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="109c5-137">The *\<report item>* **Properties** dialog box for the report item opens.</span></span>  
  
2.  <span data-ttu-id="109c5-138">**표시 유형**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="109c5-138">Click **Visibility**.</span></span>  
  
3.  <span data-ttu-id="109c5-139">**보고서를 처음 실행할 때**에서 다음 옵션 중 하나를 선택하여 보고서를 처음 실행할 때 보고서 항목이 표시되는 방식을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="109c5-139">In **When the report is initially run**, choose one of the following options to set the visibility of this report item the first time you run a report:</span></span>  
  
    -   <span data-ttu-id="109c5-140">보고서 항목을 표시하려면 **표시** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="109c5-140">Select **Show** to display the report item.</span></span>  
  
    -   <span data-ttu-id="109c5-141">보고서 항목을 숨기려면 **숨기기** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="109c5-141">Select **Hide** to hide the report item.</span></span>  
  
    -   <span data-ttu-id="109c5-142">런타임에 식을 평가하여 표시 유형을 결정하려면 **식에 따라 표시 또는 숨기기** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="109c5-142">Select **Show or hide based on an expression** to use an expression evaluated at run time to determine the visibility.</span></span> <span data-ttu-id="109c5-143">(**fx**)를 클릭하여 **식** 대화 상자를 열고 식을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="109c5-143">Click (**fx**) to open the **Expression** dialog box to create an expression.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="109c5-144">표시 유형에 대한 식을 지정할 때는 보고서 항목의 Hidden 속성을 설정하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="109c5-144">When you specify an expression for visibility, you are setting the Hidden property of the report item.</span></span> <span data-ttu-id="109c5-145">식은 `Boolean`인 경우 항목을 숨기고 `True`인 경우 항목을 표시하는 `False` 값을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="109c5-145">The expression evaluates to a `Boolean` value of `True` to hide the item and `False` to show the item.</span></span>  
  
4.  <span data-ttu-id="109c5-146">**이 보고서 항목으로 표시 또는 숨기기 가능**의 드롭다운 상자에서 토글 이미지를 표시할 보고서 입력란의 이름(예: Textbox1)을 입력 또는 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="109c5-146">In **Display can be toggled by this report item**, from the drop-down box, type or select the name of a text box in the report in which to display a toggle image; for example, Textbox1.</span></span>  
  
     <span data-ttu-id="109c5-147">다음 이미지에서 테이블은 사용자가 확장 및 축소할 수 있도록 구성되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="109c5-147">In the following image, the table is configured to enable users to expand and collapse it.</span></span> <span data-ttu-id="109c5-148">테이블의 표시는 Products Table 텍스트 상자로 전환됩니다.</span><span class="sxs-lookup"><span data-stu-id="109c5-148">The display of the table is toggled by the Products Table text box.</span></span>  
  
     <span data-ttu-id="109c5-149">![확장할 보고서 테이블 구성](../media/expandcollapse-reporttable.png "확장할 보고서 테이블 구성")</span><span class="sxs-lookup"><span data-stu-id="109c5-149">![Configure a report table to be expanded](../media/expandcollapse-reporttable.png "Configure a report table to be expanded")</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="109c5-150">선택하는 입력란은 최신 상태이거나 이 보고서 항목에 대한 범위(최대 보고서 본문까지)를 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="109c5-150">The text box that you choose must be in the current or containing scope for this report item (up to and including the report body).</span></span> <span data-ttu-id="109c5-151">예를 들어 차트의 표시 유형을 전환하려면 차트와 동일한 포함 범위(예: 보고서 본문 또는 사각형)에 있는 입력란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="109c5-151">For example, to toggle visibility of a chart, select a text box that is in the same containing scope as the chart; for example, the report body or a rectangle.</span></span> <span data-ttu-id="109c5-152">입력란은 동일하거나 더 높은 컨테이너 계층에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="109c5-152">The text box must be in the same container hierarchy or higher.</span></span>  
  
5.  <span data-ttu-id="109c5-153">토글을 테스트하려면 보고서를 실행하고 토글 이미지가 있는 입력란을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="109c5-153">To test the toggle, run the report and click the text box with the toggle image.</span></span> <span data-ttu-id="109c5-154">보고서 화면이 새로 고쳐져 전환된 표시 유형이 적용된 보고서 항목이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="109c5-154">The report display refreshes to show report items with their toggled visibility.</span></span>  
  
     <span data-ttu-id="109c5-155">![확장하는 테이블이 있는 실행 중인 보고서](../media/expandcollapse-runreport-reporttable.png "확장하는 테이블이 있는 실행 중인 보고서")</span><span class="sxs-lookup"><span data-stu-id="109c5-155">![Running report with an expanding table](../media/expandcollapse-runreport-reporttable.png "Running report with an expanding table")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="109c5-156">참고 항목</span><span class="sxs-lookup"><span data-stu-id="109c5-156">See Also</span></span>  
 <span data-ttu-id="109c5-157">[드릴 다운 동작 &#40;보고서 작성기 및 SSRS&#41;](drilldown-action-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="109c5-157">[Drilldown Action &#40;Report Builder and SSRS&#41;](drilldown-action-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="109c5-158">항목 숨기기&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="109c5-158">Hide an Item &#40;Report Builder and SSRS&#41;</span></span>](../report-builder/hide-an-item-report-builder-and-ssrs.md)  
  
  
