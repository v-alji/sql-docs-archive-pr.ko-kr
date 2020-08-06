---
title: '6단원: 그룹화 및 합계 추가(Reporting Services) | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: e3d61228-2aa4-42cc-955e-602dbf3406a7
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b98798005a984edf00aff469d4c1b09aa2e34d98
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660338"
---
# <a name="lesson-6-adding-grouping-and-totals-reporting-services"></a><span data-ttu-id="8fba2-102">6단원: 그룹화 및 합계 추가(Reporting Services)</span><span class="sxs-lookup"><span data-stu-id="8fba2-102">Lesson 6: Adding Grouping and Totals (Reporting Services)</span></span>
  <span data-ttu-id="8fba2-103">보고서에 그룹화 및 합계를 추가하여 데이터를 구성하고 요약할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8fba2-103">Add grouping and totals to your report to organize and summarize your data.</span></span>  
  
 <span data-ttu-id="8fba2-104">보고서에 누계를 추가 하는 방법에 대 한 자세한 내용은 [Reporting Services (SSRS) 보고서에 합계 추가](https://www.tutorialgateway.org/add-total-and-subtotal-to-ssrs-report/)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="8fba2-104">For information about adding running totals to reports, see: [Adding totals to Reporting Services (SSRS) reports](https://www.tutorialgateway.org/add-total-and-subtotal-to-ssrs-report/).</span></span>  
  
 <span data-ttu-id="8fba2-105">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="8fba2-105">**In this topic:**</span></span>  
  
-   [<span data-ttu-id="8fba2-106">보고서의 데이터를 그룹화 하려면</span><span class="sxs-lookup"><span data-stu-id="8fba2-106">To group data in a report</span></span>](#bkmk_groupdata)  
  
-   [<span data-ttu-id="8fba2-107">보고서에 합계를 추가 하려면</span><span class="sxs-lookup"><span data-stu-id="8fba2-107">To add totals to a report</span></span>](#bkmk_addtotals)  
  
-   [<span data-ttu-id="8fba2-108">보고서에 일일 합계를 추가하려면</span><span class="sxs-lookup"><span data-stu-id="8fba2-108">To add a daily total to a report</span></span>](#bkmk_adddailytotal)  
  
-   [<span data-ttu-id="8fba2-109">보고서에 총합계를 추가 하려면</span><span class="sxs-lookup"><span data-stu-id="8fba2-109">To add a grand total to a report</span></span>](#bkmk_addgrandtotal)  
  
-   [<span data-ttu-id="8fba2-110">보고서 서버에 보고서를 게시 하려면 (선택 사항)</span><span class="sxs-lookup"><span data-stu-id="8fba2-110">To Publish the Report to the Report Server (Optional)</span></span>](#bkmk_publishreport)  
  
##  <a name="to-group-data-in-a-report"></a><a name="bkmk_groupdata"></a><span data-ttu-id="8fba2-111">보고서의 데이터를 그룹화 하려면</span><span class="sxs-lookup"><span data-stu-id="8fba2-111">To group data in a report</span></span>  
  
1.  <span data-ttu-id="8fba2-112">**디자인** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8fba2-112">Click the **Design** tab.</span></span>  
  
2.  <span data-ttu-id="8fba2-113">**행 그룹** 창이 표시 되지 않으면 디자인 화면을 마우스 오른쪽 단추로 클릭 하 고 **보기** 를 클릭 한 다음 **그룹화**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="8fba2-113">If you do not see the **Row Groups** pane , right-click the design surface and click **view** and then click **Grouping**.</span></span>  
  
3.  <span data-ttu-id="8fba2-114">**보고서 데이터** 창에서 `Date` 필드를 **행 그룹** 창으로 끕니다.</span><span class="sxs-lookup"><span data-stu-id="8fba2-114">From the **Report Data** pane, drag the `Date` field to the **Row Groups** pane.</span></span> <span data-ttu-id="8fba2-115">**(자세히)** 라는 행 위에 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="8fba2-115">Place it above the row called **(Details)**.</span></span>  
  
     <span data-ttu-id="8fba2-116">행 핸들 안에 대괄호가 표시되어 그룹임을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="8fba2-116">Note that the row handle now has a bracket in it, to show a group.</span></span> <span data-ttu-id="8fba2-117">이제 테이블에 세로 점선의 양쪽에 하나씩 두 개의 Date 열이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8fba2-117">The table now also has two Date columns -- one on either side of a vertical dotted line.</span></span>  
  
     ![](../../2014/tutorials/media/rs-basictablegroups1design.gif "rs_BasicTableGroups1Design")  
  
4.  <span data-ttu-id="8fba2-118">**보고서 데이터** 창에서 `Order` 필드를 **행 그룹** 창으로 끕니다.</span><span class="sxs-lookup"><span data-stu-id="8fba2-118">From the **Report Data** pane, drag the `Order` field to the **Row Groups** pane.</span></span> <span data-ttu-id="8fba2-119">Date 아래, **(자세히)** 위에 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="8fba2-119">Place it below Date and above **(Details)**.</span></span>  
  
     <span data-ttu-id="8fba2-120">행 핸들 안에 두 개의 대괄호가 표시되어 두 개의 그룹임을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="8fba2-120">Note that the row handle now has two brackets in it, to show two groups.</span></span> <span data-ttu-id="8fba2-121">이제 테이블에 두 개의 `Order` 열이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8fba2-121">The table now has two `Order` columns, too.</span></span>  
  
5.  <span data-ttu-id="8fba2-122">이중선 오른쪽 에서 원래 Date 및 **Order** 열을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="8fba2-122">Delete the original Date and Order columns to the **right** of the double line.</span></span> <span data-ttu-id="8fba2-123">그러면 이 개인 레코드 값이 제거되고 그룹 값만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="8fba2-123">This removes this individual record values so that only the group value is displayed.</span></span> <span data-ttu-id="8fba2-124">두 열의 열 핸들을 선택하고 마우스 오른쪽 단추로 클릭한 다음 **열 삭제**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8fba2-124">Select the column handles for the two columns, right-click and click **Delete Columns**.</span></span>  
  
     <span data-ttu-id="8fba2-125">![삭제할 열 선택](../../2014/tutorials/media/rs-basictablegroupsdeletecols.gif "삭제할 열 선택")</span><span class="sxs-lookup"><span data-stu-id="8fba2-125">![Select columns to delete](../../2014/tutorials/media/rs-basictablegroupsdeletecols.gif "Select columns to delete")</span></span>  
  
     <span data-ttu-id="8fba2-126">열 머리글 및 날짜의 서식을 다시 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8fba2-126">You can format the column headers and date again.</span></span>  
  
6.  <span data-ttu-id="8fba2-127">**미리 보기** 탭으로 전환하여 보고서를 미리 봅니다.</span><span class="sxs-lookup"><span data-stu-id="8fba2-127">Switch to the **Preview** tab to preview the report.</span></span> <span data-ttu-id="8fba2-128">다음 그림과 비슷해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8fba2-128">It should look similar to the following illustration:</span></span>  
  
     <span data-ttu-id="8fba2-129">![Date 및 Order 기준으로 그룹화된 테이블](../../2014/tutorials/media/rs-basictablegroupspreview.gif "Date 및 Order 기준으로 그룹화된 테이블")</span><span class="sxs-lookup"><span data-stu-id="8fba2-129">![Table grouped by date and then order](../../2014/tutorials/media/rs-basictablegroupspreview.gif "Table grouped by date and then order")</span></span>  
  
##  <a name="to-add-totals-to-a-report"></a><a name="bkmk_addtotals"></a><span data-ttu-id="8fba2-130">보고서에 합계를 추가 하려면</span><span class="sxs-lookup"><span data-stu-id="8fba2-130">To add totals to a report</span></span>  
  
1.  <span data-ttu-id="8fba2-131">디자인 뷰로 전환합니다.</span><span class="sxs-lookup"><span data-stu-id="8fba2-131">Switch to Design view.</span></span>  
  
2.  <span data-ttu-id="8fba2-132">`[LineTotal]`필드가 들어 있는 데이터 영역 셀을 마우스 오른쪽 단추로 클릭하고 **합계 추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8fba2-132">Right-click the data region cell that contains the field `[LineTotal]`, and click **Add Total**.</span></span>  
  
     <span data-ttu-id="8fba2-133">그러면 각 주문의 금액 합계가 표시되는 행이 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="8fba2-133">This adds a row with a sum of the dollar amount for each order.</span></span>  
  
3.  <span data-ttu-id="8fba2-134">`[Qty]`필드가 들어 있는 셀을 마우스 오른쪽 단추로 클릭하고 **합계 추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8fba2-134">Right-click the cell that contains the field `[Qty]`, and click **Add Total**.</span></span>  
  
     <span data-ttu-id="8fba2-135">그러면 각 주문의 수량 합계가 합계 행에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="8fba2-135">This adds a sum of the quantity for each order to the totals row.</span></span>  
  
4.  <span data-ttu-id="8fba2-136">`Sum[Qty]`왼쪽의 빈 셀에 "**Order Total"** 이라는 레이블을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="8fba2-136">In the empty cell to the left of `Sum[Qty]`, type the label "**Order Total"**.</span></span>  
  
5.  <span data-ttu-id="8fba2-137">합계 행에 배경색을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8fba2-137">You can add a background color to the totals row.</span></span> <span data-ttu-id="8fba2-138">두 합계 셀과 레이블 셀을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8fba2-138">Select the two sum cells and the label cell.</span></span>  
  
6.  <span data-ttu-id="8fba2-139">**서식** 메뉴에서 **배경색**, **밝은 회색**, **확인**을 차례로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8fba2-139">On the **Format** menu, click **Background Color**, click **Light Gray**, and click **OK**.</span></span>  
  
     <span data-ttu-id="8fba2-140">![디자인 뷰: 주문 합계가 있는 기본 테이블](../../2014/tutorials/media/rs-basictablesumlinetotaldesign.gif "디자인 뷰: 주문 합계가 있는 기본 테이블")</span><span class="sxs-lookup"><span data-stu-id="8fba2-140">![Design view: Basic table with order total](../../2014/tutorials/media/rs-basictablesumlinetotaldesign.gif "Design view: Basic table with order total")</span></span>  
  
##  <a name="to-add-a-daily-total-to-a-report"></a><a name="bkmk_adddailytotal"></a><span data-ttu-id="8fba2-141">보고서에 일일 합계를 추가 하려면</span><span class="sxs-lookup"><span data-stu-id="8fba2-141">To add a daily total to a report</span></span>  
  
1.  <span data-ttu-id="8fba2-142">Order 셀을 마우스 오른쪽 단추로 클릭하고 **합계 추가**를 가리킨 후 **다음 이후**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8fba2-142">Right-click the Order cell, point to **Add Total**, and click **After**.</span></span>  
  
     <span data-ttu-id="8fba2-143">그러면 각 날짜에 대 한 수량과 금액의 합계가 포함 된 새 행과 Order 열에 "**Total**" 라는 레이블이 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8fba2-143">This adds a new row containing sums of the quantity and dollar amount for each day, and the label "**Total**" in the Order column.</span></span>  
  
2.  <span data-ttu-id="8fba2-144">같은 셀에서 **Daily** 라는 단어를 **Total** 이라는 단어 앞에 입력하여 **Daily Total**이라고 표시되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="8fba2-144">Type the word **Daily** before the word **Total** in the same cell, so it reads **Daily Total**.</span></span>  
  
3.  <span data-ttu-id="8fba2-145">**Daily Total** 셀, 두 개의 **Sum** 셀 및 이들 사이에 있는 빈 셀을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8fba2-145">Select the **Daily Total** cell, the two **Sum** cells and the empty cell between them.</span></span>  
  
4.  <span data-ttu-id="8fba2-146">**서식** 메뉴에서 **배경색**, **주황색**, **확인**을 차례로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8fba2-146">On the **Format** menu, click **Background Color**, click **Orange**, and click **OK**.</span></span>  
  
     ![](../../2014/tutorials/media/rs-basictablesumdaytotaldesign.gif "rs_BasicTableSumDayTotalDesign")  
  
##  <a name="to-add-a-grand-total-to-a-report"></a><a name="bkmk_addgrandtotal"></a><span data-ttu-id="8fba2-147">보고서에 총합계를 추가 하려면</span><span class="sxs-lookup"><span data-stu-id="8fba2-147">To add a grand total to a report</span></span>  
  
1.  <span data-ttu-id="8fba2-148">Date 셀을 마우스 오른쪽 단추로 클릭하고 **합계 추가**를 가리킨 후 **다음 이후**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8fba2-148">Right-click the Date cell, point to **Add Total**, and click **After**.</span></span>  
  
     <span data-ttu-id="8fba2-149">그러면 전체 보고서의 수량 및 금액의 합계가 포함 된 새 행과 열의 **전체** 레이블이 추가 `Date` 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8fba2-149">This adds a new row containing sums of the quantity and dollar amount for the entire report, and the **Total** label in the `Date` column.</span></span>  
  
2.  <span data-ttu-id="8fba2-150">같은 셀에서 **Grand** 라는 단어를 **Total** 이라는 단어 앞에 입력하여 **Grand Total**이라고 표시되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="8fba2-150">Type the word **Grand** before the word **Total** in the same cell, so it reads **Grand Total**.</span></span>  
  
3.  <span data-ttu-id="8fba2-151">**Grand Total** 셀, 두 개의 **Sum** 셀 및 이들 사이에 있는 빈 셀을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8fba2-151">Select the **Grand Total** cell, the two **Sum** cells and the empty cells between them.</span></span>  
  
4.  <span data-ttu-id="8fba2-152">**서식** 메뉴에서 **배경색**, **밝은 파란색**, **확인**을 차례로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8fba2-152">On the **Format** menu, click **Background Color**, click **Light Blue**, and click **OK**.</span></span>  
  
     <span data-ttu-id="8fba2-153">![디자인 뷰: 기본 테이블의 총합계](../../2014/tutorials/media/rs-basictablesumgrandtotaldesign.gif "디자인 뷰: 기본 테이블의 총합계")</span><span class="sxs-lookup"><span data-stu-id="8fba2-153">![Design view: Grand total in basic table](../../2014/tutorials/media/rs-basictablesumgrandtotaldesign.gif "Design view: Grand total in basic table")</span></span>  
  
5.  <span data-ttu-id="8fba2-154">미리 보기를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8fba2-154">Click Preview.</span></span>  
  
     <span data-ttu-id="8fba2-155">마지막 페이지는 다음과 같아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8fba2-155">The last page should look something like this:</span></span>  
  
     <span data-ttu-id="8fba2-156">![미리 보기: 총합계가 있는 기본 테이블](../../2014/tutorials/media/rs-basictablesumgrandtotalpreview.gif "미리 보기: 총합계가 있는 기본 테이블")</span><span class="sxs-lookup"><span data-stu-id="8fba2-156">![Preview: Basic table with grand total](../../2014/tutorials/media/rs-basictablesumgrandtotalpreview.gif "Preview: Basic table with grand total")</span></span>  
  
##  <a name="to-publish-the-report-to-the-report-server-optional"></a><a name="bkmk_publishreport"></a><span data-ttu-id="8fba2-157">보고서 서버에 보고서를 게시 하려면 (선택 사항)</span><span class="sxs-lookup"><span data-stu-id="8fba2-157">To Publish the Report to the Report Server (Optional)</span></span>  
  
1.  <span data-ttu-id="8fba2-158">선택 단계에서는 보고서 관리자에서 보고서를 볼 수 있도록 기본 모드 보고서 서버에 완료된 보고서를 게시합니다.</span><span class="sxs-lookup"><span data-stu-id="8fba2-158">An optional step is to publish the completed report to the native mode report server so you can view the report from Report Manager.</span></span>  
  
2.  <span data-ttu-id="8fba2-159">도구 모음에서 **프로젝트** 를 클릭한 후 **자습서 속성...** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8fba2-159">On the toolbar click **Project** and then click **tutorial Properties...**</span></span>  
  
3.  <span data-ttu-id="8fba2-160">**TargetServerURL** 에 보고서 서버의 이름 이름을 입력 합니다 (예: **http:// \<servername> /reportserver** ).</span><span class="sxs-lookup"><span data-stu-id="8fba2-160">In the **TargetServerURL** type the name of the name of your report server, for example **http://\<servername>/reportserver**</span></span>  
  
4.  <span data-ttu-id="8fba2-161">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8fba2-161">Click **OK**</span></span>  
  
5.  <span data-ttu-id="8fba2-162">도구 모음에서 **빌드** 를 클릭한 후 **자습서 배포**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8fba2-162">On the toolbar click **Build** and then click **Deploy tutorial**.</span></span>  
  
     <span data-ttu-id="8fba2-163">출력 창에 다음과 비슷한 메시지가 표시되면 배포가 성공한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="8fba2-163">If you see a message similar to the following in the output window, it indicates a successful deployment.</span></span>  
  
    > <span data-ttu-id="8fba2-164">------ 빌드 시작: 자습서, 구성: 디버그 ------'Sales Orders.rdl'을 건너 뛰는 중입니다.</span><span class="sxs-lookup"><span data-stu-id="8fba2-164">------ Build started: Project: tutorial, Configuration: Debug ------Skipping 'Sales Orders.rdl'.</span></span> <span data-ttu-id="8fba2-165">항목이 최신 상태입니다. 빌드 완료--0 개 오류, 0 개 경고------배포 시작: 프로젝트: 자습서, 구성: 디버그------http:// \<server name> /Reportserverdeploying 보고서 '/Tutorial/Sales Orders '에 배포 합니다. 배포 완료--0 개 오류, 0 개 경고 = = = = = = = = = = 빌드: 1 개 성공 또는 최신, 0 개 실패, 0 건너뜀 = = = = = = = = = = = = = = = = = = =</span><span class="sxs-lookup"><span data-stu-id="8fba2-165">Item is up to date.Build complete -- 0 errors, 0 warnings------ Deploy started: Project: tutorial, Configuration: Debug ------Deploying to http://\<server name>/reportserverDeploying report '/tutorial/Sales Orders'.Deploy complete -- 0 errors, 0 warnings========== Build: 1 succeeded or up-to-date, 0 failed, 0 skipped ==================== Deploy: 1 succeeded, 0 failed, 0 skipped ==========</span></span>  
  
     <span data-ttu-id="8fba2-166">다음과 비슷한 오류 메시지가 표시되면 보고서 서버에 대한 권한이 있는지 확인하고 관리자 권한으로 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] 를 시작했는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="8fba2-166">If you see an error message similar to the following, verify you have permissions on the report server and you have started [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] with administrator privileges.</span></span>  
  
    > <span data-ttu-id="8fba2-167">"사용자 이름 ' 사용자에 게 부여 된 사용 권한이 \\ \> 이 작업을 수행 하기에 충분 하지 않습니다."<</span><span class="sxs-lookup"><span data-stu-id="8fba2-167">"The permissions granted to user 'XXXXXXXX\\<your user name\>' are insufficient for performing this operation"</span></span>  
  
6.  <span data-ttu-id="8fba2-168">관리자 권한으로 보고서 관리자를 시작 합니다. 예를 들어 Internet Explorer 아이콘을 마우스 오른쪽 단추로 클릭 하 고 **관리자 권한으로 실행**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="8fba2-168">Start Report Manager with administrator privileges, for example, right-click the icon for Internet Explorer and click **Run as administrator**.</span></span>  
  
     <span data-ttu-id="8fba2-169">보고서 관리자 URL로 이동합니다. 예: `http://<server name>/reports`</span><span class="sxs-lookup"><span data-stu-id="8fba2-169">Browse to the Report Manager URL, for example: `http://<server name>/reports`.</span></span>  
  
7.  <span data-ttu-id="8fba2-170">보고서가 포함된 폴더로 이동하고 `Sales Orders` 보고서의 이름을 클릭하여 브라우저에서 렌더링된 보고서를 봅니다.</span><span class="sxs-lookup"><span data-stu-id="8fba2-170">Browse to the folder that contains the report and click the name of the report `Sales Orders` to view the rendered report in the browser.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="8fba2-171">다음 단계</span><span class="sxs-lookup"><span data-stu-id="8fba2-171">Next Steps</span></span>  
 <span data-ttu-id="8fba2-172">기본 테이블 보고서 만들기 자습서를 성공적으로 완료했습니다.</span><span class="sxs-lookup"><span data-stu-id="8fba2-172">You have successfully completed the Creating a Basic Table Report tutorial.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8fba2-173">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8fba2-173">See Also</span></span>  
 [<span data-ttu-id="8fba2-174">데이터 필터링, 그룹화 및 정렬&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="8fba2-174">Filter, Group, and Sort Data &#40;Report Builder and SSRS&#41;</span></span>](report-design/filter-group-and-sort-data-report-builder-and-ssrs.md)  
  
  
