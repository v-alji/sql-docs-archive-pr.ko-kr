---
title: '4단원: 보고서에 테이블 추가(Reporting Services) | Microsoft Docs'
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 5ddf2914-bcdd-427d-8cba-0ccb8342f819
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 52694168bd60b8e3807db6204f33a89815573093
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647514"
---
# <a name="lesson-4-adding-a-table-to-the-report-reporting-services"></a><span data-ttu-id="5bfdd-102">4단원: 보고서에 테이블 추가(Reporting Services)</span><span class="sxs-lookup"><span data-stu-id="5bfdd-102">Lesson 4: Adding a Table to the Report (Reporting Services)</span></span>
  <span data-ttu-id="5bfdd-103">데이터 세트가 정의되면 보고서 디자인을 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5bfdd-103">After the dataset is defined, you can start designing the report.</span></span> <span data-ttu-id="5bfdd-104">데이터 영역, 입력란, 이미지 및 보고서에 포함하려는 항목을 디자인 화면에 끌어다 놓는 방법으로 보고서 레이아웃을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="5bfdd-104">You create a report layout by dragging and dropping data regions, text boxes, images, and other items that you want to include in your report to the design surface.</span></span>  
  
 <span data-ttu-id="5bfdd-105">기본 데이터 세트의 반복되는 데이터 행이 포함된 항목을 *데이터 영역*이라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="5bfdd-105">Items that contain repeated rows of data from underlying datasets are called *data regions*.</span></span> <span data-ttu-id="5bfdd-106">기본 보고서에는 데이터 영역이 하나만 있지만 테이블 형식 보고서에 차트를 추가할 때처럼 필요한 경우에는 데이터 영역을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5bfdd-106">A basic report will have only one data region, but you can add more, for example, if you want to add a chart to your tabular report.</span></span> <span data-ttu-id="5bfdd-107">데이터 영역을 추가한 뒤에는 데이터 영역에 필드를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5bfdd-107">After you add a data region, you can add fields to the data region.</span></span>  
  
### <a name="to-add-a-table-data-region-and-fields-to-a-report-layout"></a><span data-ttu-id="5bfdd-108">보고서 레이아웃에 테이블 데이터 영역과 필드를 추가하려면</span><span class="sxs-lookup"><span data-stu-id="5bfdd-108">To add a Table data region and fields to a report layout</span></span>  
  
1.  <span data-ttu-id="5bfdd-109">**도구 상자**에서 **테이블**을 클릭하고 디자인 화면을 클릭하여 마우스를 끕니다.</span><span class="sxs-lookup"><span data-stu-id="5bfdd-109">In the **Toolbox**, click **Table**, and then click on the design surface and drag the mouse.</span></span> <span data-ttu-id="5bfdd-110">보고서 디자이너는 디자인 화면 가운데에 세 개의 열이 있는 테이블 데이터 영역을 그립니다.</span><span class="sxs-lookup"><span data-stu-id="5bfdd-110">Report Designer draws a table data region with three columns in the center of the design surface.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="5bfdd-111">**보고서 데이터** 창의 왼쪽에 **도구 상자** 가 탭으로 나타날 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5bfdd-111">The **Toolbox** may appear as a tab on the left side of the **Report Data** pane.</span></span> <span data-ttu-id="5bfdd-112">**도구 상자**를 열려면 포인터를 **도구 상자** 탭 위로 이동 합니다. **도구 상자가** 표시 되지 않으면 **보기** 메뉴에서 **도구 상자**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="5bfdd-112">To open the **Toolbox**, move the pointer over the **Toolbox** tab. If the **Toolbox** is not visible, from the **View** menu, click **Toolbox**.</span></span>  
  
2.  <span data-ttu-id="5bfdd-113">**보고서 데이터** 창에서 **AdventureWorksDataset** 데이터 집합을 확장 하 여 필드를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="5bfdd-113">In the **Report Data** pane, expand the **AdventureWorksDataset** dataset to display the fields.</span></span>  
  
3.  <span data-ttu-id="5bfdd-114">보고서 데이터 창에서 **Date** 필드를 테이블의 첫 번째 열로 끕니다.</span><span class="sxs-lookup"><span data-stu-id="5bfdd-114">Drag the Date field from the **Report Data** pane to the first column in the table.</span></span>  
  
     <span data-ttu-id="5bfdd-115">필드를 첫 번째 열에 놓으면 두 가지 동작이 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="5bfdd-115">When you drop the field into the first column, two things happen.</span></span> <span data-ttu-id="5bfdd-116">먼저 데이터 셀에는 *필드 식*이라는 필드 이름이 대괄호 안에 표시됩니다. 이 경우 `[Date]`와 같이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="5bfdd-116">First, the data cell will display the field name, known as the *field expression*, in brackets: `[Date]`.</span></span> <span data-ttu-id="5bfdd-117">두 번째로 열 머리글 값이 자동으로 필드 식 바로 위의 머리글 행에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="5bfdd-117">Second, a column header value is automatically added to Header row, just above the field expression.</span></span> <span data-ttu-id="5bfdd-118">기본적으로 열은 필드 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="5bfdd-118">By default, the column is the name of the field.</span></span> <span data-ttu-id="5bfdd-119">머리글 행 텍스트를 선택한 다음 새 이름을 입력할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5bfdd-119">You can select the Header row text and type a new name.</span></span>  
  
4.  <span data-ttu-id="5bfdd-120">보고서 데이터 창에서 **Order** 필드를 테이블의 두 번째 열로 끕니다.</span><span class="sxs-lookup"><span data-stu-id="5bfdd-120">Drag the Order field from the **Report Data** pane to the second column in the table.</span></span>  
  
5.  <span data-ttu-id="5bfdd-121">보고서 데이터 창에서 **Product** 필드를 테이블의 세 번째 열로 끕니다.</span><span class="sxs-lookup"><span data-stu-id="5bfdd-121">Drag the Product field from the **Report Data** pane to the third column in the table.</span></span>  
  
6.  <span data-ttu-id="5bfdd-122">세로 커서가 나타나고 포인터가 더하기 기호(+)로 바뀔 때까지 Qty 필드를 세 번째 열의 오른쪽 가장자리로 끕니다.</span><span class="sxs-lookup"><span data-stu-id="5bfdd-122">Drag the Qty field to the right edge of the third column until you get a vertical cursor and the mouse pointer has a plus sign [+].</span></span> <span data-ttu-id="5bfdd-123">마우스 단추를 놓으면 네 번째 열이 `[Qty]`에 대해 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="5bfdd-123">When you release the mouse button, a fourth column is created for `[Qty]`.</span></span>  
  
7.  <span data-ttu-id="5bfdd-124">같은 방법으로 LineTotal 필드를 추가하여 다섯 번째 열을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="5bfdd-124">Add the LineTotal field in the same way, creating a fifth column.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="5bfdd-125">열 머리글은 Line Total입니다.</span><span class="sxs-lookup"><span data-stu-id="5bfdd-125">The column header is Line Total.</span></span> <span data-ttu-id="5bfdd-126">보고서 디자이너가 자동으로 LineTotal을 두 단어로 분리하여 열의 이름을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="5bfdd-126">Report Designer automatically creates a friendly name for the column by splitting LineTotal into two words.</span></span>  
  
     <span data-ttu-id="5bfdd-127">다음 다이어그램은 Date, Order, Product, Qty 및 Line Total 필드가 있는 테이블 데이터 영역을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="5bfdd-127">The following diagram shows a table data region that has been populated with these fields: Date, Order, Product, Qty, and Line Total.</span></span>  
  
     <span data-ttu-id="5bfdd-128">![디자인, 머리글 행과 정보 행이 있는 테이블](../../2014/tutorials/media/rs-basictabledetailsdesign.gif "디자인, 머리글 행과 정보 행이 있는 테이블")</span><span class="sxs-lookup"><span data-stu-id="5bfdd-128">![Design, Table with header row and detail row](../../2014/tutorials/media/rs-basictabledetailsdesign.gif "Design, Table with header row and detail row")</span></span>  
  
## <a name="preview-your-report"></a><span data-ttu-id="5bfdd-129">보고서 미리 보기</span><span class="sxs-lookup"><span data-stu-id="5bfdd-129">Preview Your Report</span></span>  
 <span data-ttu-id="5bfdd-130">보고서 미리 보기 기능을 사용하면 보고서 서버에 보고서를 게시하지 않고도 렌더링된 보고서를 볼 수 있으므로</span><span class="sxs-lookup"><span data-stu-id="5bfdd-130">Previewing a report enables you to view the rendered report without having to first publish it to a report server.</span></span> <span data-ttu-id="5bfdd-131">디자인 타임에 보고서를 자주 미리 보면서 작업할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5bfdd-131">You will probably want to preview your report frequently during design time.</span></span> <span data-ttu-id="5bfdd-132">보고서를 미리 보면 디자인 및 데이터 연결에 대한 유효성 검사를 실행할 수 있으므로 보고서를 보고서 서버에 게시하기 전에 오류 및 문제를 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5bfdd-132">Previewing the report will also run validation on the design and data connections so you can correct errors and issues before publishing the report to a report server.</span></span>  
  
#### <a name="to-preview-a-report"></a><span data-ttu-id="5bfdd-133">보고서를 미리 보려면</span><span class="sxs-lookup"><span data-stu-id="5bfdd-133">To preview a report</span></span>  
  
-   <span data-ttu-id="5bfdd-134">**미리 보기** 탭을 클릭 합니다. 보고서 디자이너 보고서를 실행 하 고 미리 보기 보기에 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="5bfdd-134">Click the **Preview** tab. Report Designer runs the report and displays it in Preview view.</span></span>  
  
     <span data-ttu-id="5bfdd-135">다음 다이어그램은 미리 보기 뷰에 표시된 보고서의 일부를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="5bfdd-135">The following diagram shows part of the report in Preview view.</span></span>  
  
     <span data-ttu-id="5bfdd-136">![미리 보기, 5개의 열이 있는 테이블의 정보 행](../../2014/tutorials/media/rs-basictabledetailspreview.gif "미리 보기, 5개의 열이 있는 테이블의 정보 행")</span><span class="sxs-lookup"><span data-stu-id="5bfdd-136">![Preview, Detail rows of table with 5 columns](../../2014/tutorials/media/rs-basictabledetailspreview.gif "Preview, Detail rows of table with 5 columns")</span></span>  
  
     <span data-ttu-id="5bfdd-137">통화(Line Total 열)의 소수점 뒤에 6자리가 있고 날짜에는 타임스탬프가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5bfdd-137">Notice that the currency (in the Line Total column) has six places after the decimal, and the date has includes a time stamp.</span></span> <span data-ttu-id="5bfdd-138">다음 단원에서는 이러한 서식을 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="5bfdd-138">You're going to fix that formatting in the next lesson.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5bfdd-139">**파일** 메뉴에서 **모두 저장** 을 클릭하여 보고서를 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="5bfdd-139">On the **File** menu, click **Save All** to save the report.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="5bfdd-140">다음 단계</span><span class="sxs-lookup"><span data-stu-id="5bfdd-140">Next Steps</span></span>  
 <span data-ttu-id="5bfdd-141">보고서에 테이블 데이터 영역을 추가하고, 데이터 영역에 필드를 추가하고, 보고서를 미리 보는 방법을 배웠습니다.</span><span class="sxs-lookup"><span data-stu-id="5bfdd-141">You have successfully added a Table data region to your report, added fields to the data region, and previewed your report.</span></span> <span data-ttu-id="5bfdd-142">다음 단원에서는 열 머리글과 날짜 및 통화 값에 서식을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="5bfdd-142">Next, you will format column headers and date and currency values.</span></span> <span data-ttu-id="5bfdd-143">[5단원: 보고서 서식 지정&#40;Reporting Services&#41;](../reporting-services/lesson-5-formatting-a-report-reporting-services.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5bfdd-143">See [Lesson 5: Formatting a Report &#40;Reporting Services&#41;](../reporting-services/lesson-5-formatting-a-report-reporting-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5bfdd-144">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5bfdd-144">See Also</span></span>  
 <span data-ttu-id="5bfdd-145">[테이블 &#40;보고서 작성기 및 SSRS&#41;](report-design/tables-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="5bfdd-145">[Tables &#40;Report Builder  and SSRS&#41;](report-design/tables-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="5bfdd-146">데이터 세트 필드 컬렉션&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="5bfdd-146">Dataset Fields Collection &#40;Report Builder and SSRS&#41;</span></span>](report-data/dataset-fields-collection-report-builder-and-ssrs.md)  
  
  
