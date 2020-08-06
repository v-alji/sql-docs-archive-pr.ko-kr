---
title: 단계별 보고서 만들기(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 5933c4f0-c713-4ecb-b521-ff46c9c63fff
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d845993ac1462cef2d39638101e5c7b9fc314b94
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649419"
---
# <a name="create-a-stepped-report-report-builder-and-ssrs"></a><span data-ttu-id="780a8-102">단계별 보고서 만들기(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="780a8-102">Create a Stepped Report (Report Builder and SSRS)</span></span>
  <span data-ttu-id="780a8-103">단계별 보고서에는 아래 예에서와 같이 동일한 열의 부모 그룹 아래에 들여쓴 정보 행 또는 자식 그룹이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="780a8-103">A stepped report shows detail rows or child groups indented under a parent group in the same column, as shown in the example below:</span></span>  
  
 <span data-ttu-id="780a8-104">![렌더링된 단계별 보고서](../media/steppedreportrendered.gif "렌더링된 단계별 보고서")</span><span class="sxs-lookup"><span data-stu-id="780a8-104">![Rendered stepped report](../media/steppedreportrendered.gif "Rendered stepped report")</span></span>  
  
 <span data-ttu-id="780a8-105">기존 테이블 보고서에서는 부모 그룹이 보고서의 인접 열에 배치됩니다.</span><span class="sxs-lookup"><span data-stu-id="780a8-105">Traditional table reports place the parent group in an adjacent column on the report.</span></span> <span data-ttu-id="780a8-106">새로운 테이블릭스 데이터 영역을 사용하면 그룹과 정보 행 또는 자식 그룹을 동일한 열에 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="780a8-106">The new tablix data region enables you to add a group and detail rows or child groups to the same column.</span></span> <span data-ttu-id="780a8-107">그룹 행을 정보 행 또는 자식 그룹 행과 구별하기 위해 글꼴 색과 같은 서식을 적용하거나 정보 행을 들여쓸 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="780a8-107">To differentiate the group rows from the detail or child group rows, you can apply formatting such as font color, or you can indent the detail rows.</span></span>  
  
 <span data-ttu-id="780a8-108">이 항목의 절차에서는 단계별 보고서를 수동으로 만드는 방법을 보여 줍니다. 여기서 설명하는 방법 대신 새 테이블 또는 행렬 마법사를 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="780a8-108">The procedures in this topic show you how to manually create a stepped report, but you can also use the New Table and Matrix Wizard.</span></span> <span data-ttu-id="780a8-109">이 마법사를 사용하면 단계별 보고서의 레이아웃이 기본 제공되므로 보고서를 쉽게 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="780a8-109">It provides the layout for stepped reports, making it easy to create them.</span></span> <span data-ttu-id="780a8-110">마법사를 완료한 후 보고서의 레이아웃을 추가로 조정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="780a8-110">After you complete the wizard, you can further enhance the report.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="780a8-111">마법사는 보고서 작성기에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="780a8-111">The wizard is available only in Report Builder.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-create-a-stepped-report"></a><span data-ttu-id="780a8-112">단계별 보고서를 만들려면</span><span class="sxs-lookup"><span data-stu-id="780a8-112">To create a stepped report</span></span>  
  
1.  <span data-ttu-id="780a8-113">테이블 보고서를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="780a8-113">Create a table report.</span></span> <span data-ttu-id="780a8-114">예를 들어 테이블릭스 데이터 영역을 삽입하고 데이터 행에 필드를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="780a8-114">For example, insert a tablix data region and add fields to the Data row.</span></span>  
  
2.  <span data-ttu-id="780a8-115">보고서에 부모 그룹을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="780a8-115">Add a parent group to your report.</span></span>  
  
    1.  <span data-ttu-id="780a8-116">테이블의 아무 곳이나 클릭하여 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="780a8-116">Click anywhere in the table to select it.</span></span> <span data-ttu-id="780a8-117">그룹화 창의 행 그룹 창에 그룹 세부 정보가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="780a8-117">The Grouping pane displays the Details group in the Row Groups pane.</span></span>  
  
    2.  <span data-ttu-id="780a8-118">그룹화 창에서 그룹 세부 정보를 마우스 오른쪽 단추로 클릭하고 **그룹 추가**를 가리킨 다음 **부모 그룹**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="780a8-118">In the Grouping Pane, right-click the Details Group, point to **Add Group**, and then click **Parent Group**.</span></span>  
  
    3.  <span data-ttu-id="780a8-119">**테이블릭스 그룹** 대화 상자에서 그룹의 이름을 제공하고 그룹 식을 드롭다운 목록에서 선택하거나 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="780a8-119">In the **Tablix Group** dialog box, provide a name for the group and type or select a group expression from the drop-down list.</span></span> <span data-ttu-id="780a8-120">드롭다운 목록에는 보고서 데이터 창에서 사용할 수 있는 간단한 필드 식이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="780a8-120">The drop-down list displays the simple field expressions that are available in the Report Data pane.</span></span> <span data-ttu-id="780a8-121">예를 들어 [PostalCode]는 데이터 세트의 PostalCode 필드에 대한 간단한 필드 식입니다.</span><span class="sxs-lookup"><span data-stu-id="780a8-121">For example, [PostalCode] is a simple field expression for the PostalCode field in a dataset.</span></span>  
  
    4.  <span data-ttu-id="780a8-122">**그룹 머리글 추가**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="780a8-122">Select **Add group header**.</span></span> <span data-ttu-id="780a8-123">이 옵션은 그룹 위에 그룹 레이블과 그룹 합계를 위한 정적 행을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="780a8-123">This option adds a static row above the group for the group label and group totals.</span></span> <span data-ttu-id="780a8-124">이와 마찬가지로 **그룹 바닥글 추가** 를 선택하여 그룹 아래에 정적 행을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="780a8-124">Likewise, you can select **Add group footer** to add a static row below the group.</span></span> [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
     <span data-ttu-id="780a8-125">이제 기본적인 테이블 형식 보고서가 준비되었습니다.</span><span class="sxs-lookup"><span data-stu-id="780a8-125">You now have a basic tabular report.</span></span> <span data-ttu-id="780a8-126">이 보고서를 렌더링하면 그룹 인스턴스 값이 들어 있는 한 개의 열과 그룹으로 묶은 정보 데이터가 들어 있는 한 개 이상의 열이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="780a8-126">When it is rendered, you see one column with the group instance value, and one or more columns with grouped detail data.</span></span> <span data-ttu-id="780a8-127">다음 그림에서는 디자인 화면의 데이터 영역을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="780a8-127">The following figure shows what the data region might look like on the design surface.</span></span>  
  
     <span data-ttu-id="780a8-128">![그룹이 있는 테이블 데이터 영역](../media/tabledataregionwithgroup.gif "그룹이 있는 테이블 데이터 영역")</span><span class="sxs-lookup"><span data-stu-id="780a8-128">![Table data region with group](../media/tabledataregionwithgroup.gif "Table data region with group")</span></span>  
  
     <span data-ttu-id="780a8-129">다음 그림에서는 보고서를 볼 때의 렌더링된 데이터 영역을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="780a8-129">The following figure shows how the rendered data region might look when you view the report.</span></span>  
  
     <span data-ttu-id="780a8-130">![렌더링된 그룹화된 보고서](../media/tablereportrendered.gif "렌더링된 그룹화된 보고서")</span><span class="sxs-lookup"><span data-stu-id="780a8-130">![Rendered grouped report](../media/tablereportrendered.gif "Rendered grouped report")</span></span>  
  
3.  <span data-ttu-id="780a8-131">단계별 보고서의 경우 그룹 인스턴스를 표시하는 첫 번째 열이 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="780a8-131">For a stepped report, you do not need the first column that shows the group instance.</span></span> <span data-ttu-id="780a8-132">대신 그룹 머리글 셀의 값을 복사하고 그룹 열을 삭제한 다음 그룹 머리글 행의 첫 번째 입력란에 붙여넣습니다.</span><span class="sxs-lookup"><span data-stu-id="780a8-132">Instead, copy the value in the group header cell, delete the group column, and paste in the first text box in the group header row.</span></span> <span data-ttu-id="780a8-133">그룹 열을 제거하려면 그룹 열 또는 셀을 마우스 오른쪽 단추로 클릭하고 **열 삭제**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="780a8-133">To remove the group column, right-click the group column or cell, and click **Delete Columns**.</span></span> <span data-ttu-id="780a8-134">다음 그림에서는 디자인 화면의 데이터 영역을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="780a8-134">The following figure shows what the data region might look like on the design surface.</span></span>  
  
     <span data-ttu-id="780a8-135">![그룹 헤더 행이 있는 데이터 영역](../media/tabledataregiongroupheader.gif "그룹 헤더 행이 있는 데이터 영역")</span><span class="sxs-lookup"><span data-stu-id="780a8-135">![Data region with group header row](../media/tabledataregiongroupheader.gif "Data region with group header row")</span></span>  
  
4.  <span data-ttu-id="780a8-136">정보 행을 동일한 열의 그룹 머리글 행 아래 들여 쓰려면 정보 데이터 셀의 안쪽 여백을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="780a8-136">To indent the detail rows under the group header row in the same column, change the padding of the detail data cell.</span></span>  
  
    1.  <span data-ttu-id="780a8-137">들여 쓰려는 정보 필드가 포함된 셀을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="780a8-137">Select the cell with the detail field that you want to indent.</span></span> <span data-ttu-id="780a8-138">해당 셀의 입력란 속성이 속성 창에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="780a8-138">The text box properties for that cell appear in the Properties pane.</span></span>  
  
    2.  <span data-ttu-id="780a8-139">속성 창의 **맞춤**에서 **안쪽 여백**의 속성을 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="780a8-139">In the Properties pane, under **Alignment**, expand the properties for **Padding**.</span></span>  
  
    3.  <span data-ttu-id="780a8-140">**왼쪽**에 새 패딩 값 (예:)을 입력 `.5in` 합니다.</span><span class="sxs-lookup"><span data-stu-id="780a8-140">For **Left**, type a new padding value, such as `.5in`.</span></span> <span data-ttu-id="780a8-141">안쪽 여백은 지정된 값만큼 셀의 텍스트를 들여씁니다.</span><span class="sxs-lookup"><span data-stu-id="780a8-141">Padding indents the text in the cell by the value you specify.</span></span> <span data-ttu-id="780a8-142">기본 안쪽 여백은 2포인트입니다.</span><span class="sxs-lookup"><span data-stu-id="780a8-142">The default padding is 2 points.</span></span> <span data-ttu-id="780a8-143">안쪽 여백 속성의 올바른 값은 0 또는 양수를 입력하고 그 뒤에 크기 단위 지정자를 입력한 값입니다.</span><span class="sxs-lookup"><span data-stu-id="780a8-143">Valid values for the Padding properties are zero or a positive number, followed by a size designator.</span></span>  
  
         <span data-ttu-id="780a8-144">사용할 수 있는 크기 단위 지정자는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="780a8-144">Size designators are:</span></span>  
  
        |||  
        |-|-|  
        |`in`|<span data-ttu-id="780a8-145">인치(1인치 = 2.54센티미터)</span><span class="sxs-lookup"><span data-stu-id="780a8-145">Inches (1 inch = 2.54 centimeters)</span></span>|  
        |`cm`|<span data-ttu-id="780a8-146">센티미터</span><span class="sxs-lookup"><span data-stu-id="780a8-146">Centimeters</span></span>|  
        |`mm`|<span data-ttu-id="780a8-147">밀리미터</span><span class="sxs-lookup"><span data-stu-id="780a8-147">Millimeters</span></span>|  
        |`pt`|<span data-ttu-id="780a8-148">포인트(1포인트 = 1/72인치)</span><span class="sxs-lookup"><span data-stu-id="780a8-148">Points (1 point = 1/72 inch)</span></span>|  
        |`pc`|<span data-ttu-id="780a8-149">파이카(1파이카 = 12포인트)</span><span class="sxs-lookup"><span data-stu-id="780a8-149">Picas (1 pica = 12 points)</span></span>|  
  
     <span data-ttu-id="780a8-150">데이터 영역은 다음 예와 비슷한 모양이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="780a8-150">Your data region will look similar to the following example.</span></span>  
  
     <span data-ttu-id="780a8-151">![단계별 보고서의 데이터 영역](../media/steppedreportdataregion.gif "단계별 보고서의 데이터 영역")</span><span class="sxs-lookup"><span data-stu-id="780a8-151">![Data region for stepped report](../media/steppedreportdataregion.gif "Data region for stepped report")</span></span>  
  
     <span data-ttu-id="780a8-152">**단계별 보고서 레이아웃의 데이터 영역**</span><span class="sxs-lookup"><span data-stu-id="780a8-152">**Data Region for Stepped Report Layout**</span></span>  
  
     <span data-ttu-id="780a8-153">**홈** 탭에서 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="780a8-153">On the **Home** tab Click **Run**.</span></span> <span data-ttu-id="780a8-154">보고서에 자식 그룹 값에 대해 들여쓴 수준으로 그룹이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="780a8-154">The report displays the group with indented levels for the child group values.</span></span>  
  
### <a name="to-create-a-stepped-report-with-multiple-groups"></a><span data-ttu-id="780a8-155">그룹이 여러 개인 단계별 보고서를 만들려면</span><span class="sxs-lookup"><span data-stu-id="780a8-155">To create a stepped report with multiple groups</span></span>  
  
1.  <span data-ttu-id="780a8-156">이전 절차에 설명된 대로 보고서를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="780a8-156">Create a report as described in the previous procedure.</span></span>  
  
2.  <span data-ttu-id="780a8-157">보고서에 다른 그룹을 더 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="780a8-157">Add additional groups to your report.</span></span>  
  
    1.  <span data-ttu-id="780a8-158">행 그룹 창에서 그룹을 마우스 오른쪽 단추로 클릭하고 **그룹 추가**를 클릭한 다음 추가할 그룹 유형을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="780a8-158">In the Row Groups pane, right-click the group, click **Add Group**, and then choose the type of group you want to add.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="780a8-159">데이터 영역에 그룹을 추가하는 데는 여러 가지 방법이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="780a8-159">There are several ways to add groups to a data region.</span></span> <span data-ttu-id="780a8-160">자세한 내용은 [데이터 영역에서 그룹 추가 또는 삭제 &#40;보고서 작성기 및 SSRS&#41;](add-or-delete-a-group-in-a-data-region-report-builder-and-ssrs.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="780a8-160">For more information, see [Add or Delete a Group in a Data Region &#40;Report Builder and SSRS&#41;](add-or-delete-a-group-in-a-data-region-report-builder-and-ssrs.md).</span></span>  
  
    2.  <span data-ttu-id="780a8-161">**테이블릭스 그룹** 대화 상자에서 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="780a8-161">In the **Tablix Group** dialog box, type a name.</span></span>  
  
    3.  <span data-ttu-id="780a8-162">**그룹 식**에서 식을 입력하거나 그룹화할 데이터 세트 필드를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="780a8-162">In **Group expression**, type an expression or select a dataset field to group on.</span></span> <span data-ttu-id="780a8-163">식을 만들려면 식 단추(**fx**)를 클릭하여 **식** 대화 상자를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="780a8-163">To create an expression, click the expression (**fx**) button to open the **Expression** dialog box.</span></span>  
  
    4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
3.  <span data-ttu-id="780a8-164">그룹 데이터를 표시하는 셀의 안쪽 여백을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="780a8-164">Change the padding for the cell that displays the group data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="780a8-165">참고 항목</span><span class="sxs-lookup"><span data-stu-id="780a8-165">See Also</span></span>  
 <span data-ttu-id="780a8-166">[페이지 머리글 및 바닥글 &#40;보고서 작성기 및 SSRS&#41;](page-headers-and-footers-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="780a8-166">[Page Headers and Footers &#40;Report Builder and SSRS&#41;](page-headers-and-footers-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="780a8-167">[보고서 항목 서식 지정 &#40;보고서 작성기 및 SSRS&#41;](formatting-report-items-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="780a8-167">[Formatting Report Items &#40;Report Builder and SSRS&#41;](formatting-report-items-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="780a8-168">[테이블 릭 스 데이터 영역 &#40;보고서 작성기 및 SSRS&#41;](../tablix-data-region-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="780a8-168">[Tablix Data Region &#40;Report Builder and SSRS&#41;](../tablix-data-region-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="780a8-169">[테이블 &#40;보고서 작성기 및 SSRS&#41;](tables-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="780a8-169">[Tables &#40;Report Builder  and SSRS&#41;](tables-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="780a8-170">[행렬 &#40;보고서 작성기 및 SSRS&#41;](create-a-matrix-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="780a8-170">[Matrices &#40;Report Builder and SSRS&#41;](create-a-matrix-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="780a8-171">[&#40;보고서 작성기 및 SSRS를 나열&#41;](create-invoices-and-forms-with-lists-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="780a8-171">[Lists &#40;Report Builder and SSRS&#41;](create-invoices-and-forms-with-lists-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="780a8-172">테이블, 행렬 및 목록&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="780a8-172">Tables, Matrices, and Lists &#40;Report Builder and SSRS&#41;</span></span>](tables-matrices-and-lists-report-builder-and-ssrs.md)  
  
  
