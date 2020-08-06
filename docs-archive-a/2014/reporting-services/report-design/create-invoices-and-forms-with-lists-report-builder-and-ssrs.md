---
title: 목록 (보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: c33231a5-b3a8-42e4-95bc-d05bdf2222f5
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c9afb0dfabe5ccc3962d43eef30031a728514135
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649414"
---
# <a name="lists-report-builder-and-ssrs"></a><span data-ttu-id="82a62-102">목록(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="82a62-102">Lists (Report Builder and SSRS)</span></span>
  <span data-ttu-id="82a62-103">목록 데이터 영역은 보고서 데이터 세트의 각 그룹 또는 행에서 반복됩니다.</span><span class="sxs-lookup"><span data-stu-id="82a62-103">A list data region repeats with each group or row in the report dataset.</span></span> <span data-ttu-id="82a62-104">목록은 자유 형식 보고서나 송장 등의 양식을 만드는 데 사용하거나 다른 데이터 영역과 함께 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="82a62-104">A list can be used to create free-form reports or forms, such as invoices, or in conjunction with other data regions.</span></span> <span data-ttu-id="82a62-105">여러 보고서 항목을 포함하는 목록을 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="82a62-105">You can define lists that contain any number of report items.</span></span> <span data-ttu-id="82a62-106">목록을 다른 목록 안에 중첩하여 여러 그룹의 데이터를 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="82a62-106">A list can be nested within another list to provide multiple groups of data.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="82a62-107">목록을 보고서와는 별도로 보고서 파트로 게시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="82a62-107">You can publish lists separately from a report as report parts.</span></span> [!INCLUDE[ssRBrptparts](../../includes/ssrbrptparts-md.md)]  
  
 <span data-ttu-id="82a62-108">목록을 사용하여 빠르게 시작하려면 [자습서: 자유 형식 보고서 만들기&#40;보고서 작성기&#41;](../tutorial-creating-a-free-form-report-report-builder.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="82a62-108">To quickly get started with lists, see [Tutorial: Creating a Free Form Report &#40;Report Builder&#41;](../tutorial-creating-a-free-form-report-report-builder.md).</span></span>  
  
 <span data-ttu-id="82a62-109">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 예제 보고서에는 목록을 사용하는 보고서가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="82a62-109">The [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] sample reports include a report that uses a list.</span></span> <span data-ttu-id="82a62-110">보고서 작성기 또는 보고서 디자이너에서 예제 보고서의 보고서 정의를 탐색하거나 보고서 작성기 또는 보고서 디자이너에서 렌더링된 보고서를 검토하여 목록에 대해 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="82a62-110">You can learn about lists by exploring the report definition of the sample report in Report Builder or Report Designer or by previewing the rendered report in Report Builder or Report Designer.</span></span> <span data-ttu-id="82a62-111">예제 보고서를 다운로드하는 방법은 [(SSRS) Reporting Services 예제](https://go.microsoft.com/fwlink/?LinkID=198283)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="82a62-111">For more information about downloading the sample reports, see [(SSRS) Reporting Services Samples](https://go.microsoft.com/fwlink/?LinkID=198283).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
##  <a name="adding-a-list-to-your-report"></a><a name="AddingList"></a><span data-ttu-id="82a62-112">보고서에 목록 추가</span><span class="sxs-lookup"><span data-stu-id="82a62-112">Adding a List to Your Report</span></span>  
 <span data-ttu-id="82a62-113">리본 메뉴의 삽입 탭에서 디자인 화면에 목록을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="82a62-113">Add a list to the design surface from the Insert tab on ribbon.</span></span> <span data-ttu-id="82a62-114">기본적으로 초기 목록에는 세부 정보 그룹과 연결된 행의 단일 셀이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="82a62-114">By default, the list initially has a single cell in a row associated with the detail group.</span></span>  
  
 <span data-ttu-id="82a62-115">![디자인 화면의 새 목록 보고서 항목](../media/rs-listtemplatenew.gif "디자인 화면의 새 목록 보고서 항목")</span><span class="sxs-lookup"><span data-stu-id="82a62-115">![New List report item on the design surface](../media/rs-listtemplatenew.gif "New List report item on the design surface")</span></span>  
  
 <span data-ttu-id="82a62-116">디자인 화면에서 목록을 선택하면 다음 그림과 같이 행 및 열 핸들이 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="82a62-116">When you select a list on the design surface, row and column handles appear, as shown in the following figure.</span></span>  
  
 <span data-ttu-id="82a62-117">![도구 상자에서 추가된 새 목록이 선택됨](../media/rs-listtemplatenewselected.gif "도구 상자에서 추가된 새 목록이 선택됨")</span><span class="sxs-lookup"><span data-stu-id="82a62-117">![New List added from Toolbox, selected](../media/rs-listtemplatenewselected.gif "New List added from Toolbox, selected")</span></span>  
  
 <span data-ttu-id="82a62-118">시작 목록은 테이블릭스 데이터 영역을 기반으로 하는 템플릿입니다.</span><span class="sxs-lookup"><span data-stu-id="82a62-118">The list you start with is a template based on the tablix data region.</span></span> <span data-ttu-id="82a62-119">목록을 추가한 후 필터, 정렬 또는 그룹 식을 지정하거나 목록이 보고서 페이지에 표시되는 방법을 변경하여 목록의 콘텐츠나 모양을 변경하는 등 디자인을 계속 향상시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="82a62-119">After you add a list, you can continue to enhance the design by changing the content or appearance of the list by specifying filter, sort, or group expressions, or changing the way the list displays across report pages.</span></span> <span data-ttu-id="82a62-120">자세한 내용은 [보고서 페이지에서 테이블릭스 데이터 영역 표시 제어&#40;보고서 작성기 및 SSRS&#41;](controlling-the-tablix-data-region-display-on-a-report-page.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="82a62-120">For more information, see [Controlling the Tablix Data Region Display on a Report Page &#40;Report Builder and SSRS&#41;](controlling-the-tablix-data-region-display-on-a-report-page.md).</span></span> <span data-ttu-id="82a62-121">목록이 단일 행 및 열로 시작하는 경우에도 중첩 또는 인접 행 그룹이나 열 그룹을 추가하거나 정보 행을 더 추가하여 끊임없이 목록 디자인을 개발할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="82a62-121">Although the list starts with a single column and row, you can further continue to develop your list design by adding nested or adjacent row groups or column groups, or adding additional detail rows.</span></span> <span data-ttu-id="82a62-122">자세한 내용은 [테이블릭스 데이터 영역의 유연성 살펴보기&#40;보고서 작성기 및 SSRS&#41;](exploring-the-flexibility-of-a-tablix-data-region-report-builder-and-ssrs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="82a62-122">For more information, see [Exploring the Flexibility of a Tablix Data Region &#40;Report Builder and SSRS&#41;](exploring-the-flexibility-of-a-tablix-data-region-report-builder-and-ssrs.md).</span></span>  
  

  
##  <a name="displaying-data-in-a-free-form-layout"></a><a name="DisplayingLayout"></a> <span data-ttu-id="82a62-123">자유 형식 레이아웃으로 데이터 표시</span><span class="sxs-lookup"><span data-stu-id="82a62-123">Displaying Data in a Free-form Layout</span></span>  
 <span data-ttu-id="82a62-124">보고서 데이터를 표 대신 자유 형식 레이아웃으로 구성하려면 디자인 화면에 목록을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="82a62-124">To organize report data in a free-form layout instead of a grid, you can add a list to the design surface.</span></span> <span data-ttu-id="82a62-125">보고서 데이터 창의 필드를 셀로 끌어옵니다.</span><span class="sxs-lookup"><span data-stu-id="82a62-125">Drag fields from the Report Data pane to the cell.</span></span> <span data-ttu-id="82a62-126">기본적으로 셀에는 컨테이너 역할을 수행하는 사각형이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="82a62-126">By default, the cell contains a rectangle that acts as a container.</span></span> <span data-ttu-id="82a62-127">원하는 디자인이 될 때까지 컨테이너의 각 필드를 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="82a62-127">Move each field in the container until you have the design you want.</span></span> <span data-ttu-id="82a62-128">사각형 컨테이너의 입력란을 끌 때 표시되는 맞춤선을 사용하면 가로 및 세로로 가장자리를 맞추는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="82a62-128">Use the snaplines that appear when you drag text boxes in the rectangle container to help you align edges vertically and horizontally.</span></span> <span data-ttu-id="82a62-129">셀의 크기를 조정하여 불필요한 공백을 제거합니다</span><span class="sxs-lookup"><span data-stu-id="82a62-129">Remove unwanted white space by adjusting the size of the cell.</span></span> <span data-ttu-id="82a62-130">자세한 내용은 [행 높이 또는 열 너비 변경&#40;보고서 작성기 및 SSRS&#41;](change-row-height-or-column-width-report-builder-and-ssrs.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="82a62-130">For more information, see [Change Row Height or Column Width &#40;Report Builder and SSRS&#41;](change-row-height-or-column-width-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="82a62-131">다음 그림에서는 Date, Order, Qty, Product, LineTotal 및 이미지 필드를 포함한 주문에 대한 정보를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="82a62-131">The following figure shows a list that displays information about an order, including these fields: Date, Order, Qty, Product, LineTotal, and an image.</span></span>  
  
 <span data-ttu-id="82a62-132">![4개의 필드와 1개의 이미지가 있는 디자인 뷰의 목록](../media/rs-basiclistformdesign.gif "4개의 필드와 1개의 이미지가 있는 디자인 뷰의 목록")</span><span class="sxs-lookup"><span data-stu-id="82a62-132">![List in design view, 4 fields and an image](../media/rs-basiclistformdesign.gif "List in design view, 4 fields and an image")</span></span>  
  
 <span data-ttu-id="82a62-133">다음 그림과 같이 미리 보기에서 목록에 자유 형식으로 필드 데이터가 반복되어 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="82a62-133">In Preview, the list repeats to display the field data in the free-form format, as shown in the following figure:</span></span>  
  
 <span data-ttu-id="82a62-134">![4개의 필드와 1개의 이미지가 있는 목록의 미리 보기](../media/rs-basiclistformpreview.gif "4개의 필드와 1개의 이미지가 있는 목록의 미리 보기")</span><span class="sxs-lookup"><span data-stu-id="82a62-134">![Preview for List with 4 fields and one image](../media/rs-basiclistformpreview.gif "Preview for List with 4 fields and one image")</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="82a62-135">이 그림에서는 각 필드 값에 대한 자유 형식 레이아웃을 보여 주는 점선이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="82a62-135">The dotted lines displays in these figures are included to show the free-form layout for each field value.</span></span> <span data-ttu-id="82a62-136">일반적으로 프로덕션 보고서에는 점선을 사용하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="82a62-136">Typically, you would not use dotted lines in a production report.</span></span>  
  

  
##  <a name="displaying-data-with-one-level-of-grouping"></a><a name="DisplayingGrouping"></a> <span data-ttu-id="82a62-137">한 가지 수준의 그룹화를 이용하여 데이터 표시</span><span class="sxs-lookup"><span data-stu-id="82a62-137">Displaying Data with One Level of Grouping</span></span>  
 <span data-ttu-id="82a62-138">목록에서 컨테이너를 자동으로 제공하므로 목록을 사용하여 그룹화된 데이터를 여러 뷰로 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="82a62-138">Because a list automatically provides a container, you can use a list to display grouped data with multiple views.</span></span> <span data-ttu-id="82a62-139">기본 목록을 변경하여 그룹을 지정하려면 세부 정보 그룹을 편집하고, 새 이름을 지정하고, 그룹 식을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="82a62-139">To change the default list to specify a group, edit the Details group, specify a new name, and specify a group expression.</span></span>  
  
 <span data-ttu-id="82a62-140">예를 들어 동일한 데이터 세트에 대해 다양한 뷰를 보여 주는 테이블과 차트를 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="82a62-140">For example, you can embed a table and a chart that show different views of the same dataset.</span></span> <span data-ttu-id="82a62-141">목록에 그룹을 추가하여 중첩된 보고서 항목이 그룹 값마다 한 번씩 반복되도록 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="82a62-141">You can add a group to the list so that the nested report items will repeat once for every group value.</span></span> <span data-ttu-id="82a62-142">다음 그림에서는 제품 범주별로 그룹화된 목록을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="82a62-142">The following figure shows a list grouped by product category.</span></span> <span data-ttu-id="82a62-143">정보 행이 없음을 주목하십시오.</span><span class="sxs-lookup"><span data-stu-id="82a62-143">Notice that there is no detail row.</span></span> <span data-ttu-id="82a62-144">목록에서 두 개의 테이블이 함께 중첩되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="82a62-144">Two tables are nested side by side in the list.</span></span> <span data-ttu-id="82a62-145">첫 번째 테이블에는 총 판매액과 함께 하위 범주가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="82a62-145">The first table displays the subcategories with total sales.</span></span> <span data-ttu-id="82a62-146">두 번째 테이블에는 하위 범주의 배포를 보여 주는 차트와 함께 지리적 영역을 기준으로 그룹화된 범주가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="82a62-146">The second table displays the category grouped by geographical area, with a chart that shows the distribution of subcategories.</span></span>  
  
 <span data-ttu-id="82a62-147">![2개의 테이블이 있는 목록(한 테이블에는 중첩된 차트가 포함됨)](../media/rs-basiclistgroupdesign.gif "2개의 테이블이 있는 목록(한 테이블에는 중첩된 차트가 포함됨)")</span><span class="sxs-lookup"><span data-stu-id="82a62-147">![A list with 2 tables, one with nested chart](../media/rs-basiclistgroupdesign.gif "A list with 2 tables, one with nested chart")</span></span>  
  
 <span data-ttu-id="82a62-148">미리 보기에서는 테이블에 자전거의 모든 하위 범주에 대한 총 판매액이 표시되며 중첩 테이블에 지리적 영역별 매출액 명세가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="82a62-148">In Preview, the table displays total sales for all subcategories of bicycles, and the table beside it displays the breakdown of sales per geographical area.</span></span> <span data-ttu-id="82a62-149">테이블에 대한 배경색 및 차트에 대한 사용자 지정 색상표를 지정하는 식을 사용하여 첫 번째 테이블에서 차트 색에 대한 범례를 제공할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="82a62-149">By using an expression to specify the background color for the table and a custom palette for the chart, the first table also provides the legend for the chart colors.</span></span>  
  
 <span data-ttu-id="82a62-150">![미리 보기, 2개의 테이블, 한 테이블에는 중첩된 차트가 포함됨](../media/rs-basiclistgrouppreview.gif "미리 보기, 2개의 테이블, 한 테이블에는 중첩된 차트가 포함됨")</span><span class="sxs-lookup"><span data-stu-id="82a62-150">![Preview, 2 tables, one with nested chart](../media/rs-basiclistgrouppreview.gif "Preview, 2 tables, one with nested chart")</span></span>  
  

  
## <a name="see-also"></a><span data-ttu-id="82a62-151">참고 항목</span><span class="sxs-lookup"><span data-stu-id="82a62-151">See Also</span></span>  
 <span data-ttu-id="82a62-152">[집계 함수 참조&#40;보고서 작성기 및 SSRS&#41;](report-builder-functions-aggregate-functions-reference.md) </span><span class="sxs-lookup"><span data-stu-id="82a62-152">[Aggregate Functions Reference &#40;Report Builder and SSRS&#41;](report-builder-functions-aggregate-functions-reference.md) </span></span>  
 [<span data-ttu-id="82a62-153">식 예&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="82a62-153">Expression Examples &#40;Report Builder and SSRS&#41;</span></span>](expression-examples-report-builder-and-ssrs.md)  
  
  
