---
title: 행 높이 또는 열 너비 변경(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: f061c204-5cd5-4467-9a9c-8a12803d93ba
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b5d75a8101d07d7d6e81c624d08cd951277936eb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653211"
---
# <a name="change-row-height-or-column-width-report-builder-and-ssrs"></a><span data-ttu-id="a4e13-102">행 높이 또는 열 너비 변경(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="a4e13-102">Change Row Height or Column Width (Report Builder and SSRS)</span></span>
  <span data-ttu-id="a4e13-103">행 높이를 설정하면 렌더링되는 보고서의 최대 행 높이가 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="a4e13-103">When you set a row height, you are specifying the maximum height for the row in the rendered report.</span></span> <span data-ttu-id="a4e13-104">하지만 기본적으로 행의 입력란은 런타임에 행의 데이터 크기에 맞게 세로로 늘어나도록 설정되어 있으므로 행 높이가 지정한 높이를 초과할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a4e13-104">However, by default, text boxes in the row are set to grow vertically to accommodate their data at run-time, and this can cause a row to expand beyond the height that you specify.</span></span> <span data-ttu-id="a4e13-105">고정 행 높이를 설정하려면 입력란 속성을 변경하여 입력란이 자동으로 늘어나지 않도록 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a4e13-105">To set a fixed row height, you must change the text box properties so they do not automatically expand.</span></span>  
  
 <span data-ttu-id="a4e13-106">열 너비를 설정하면 렌더링되는 보고서의 최대 열 너비가 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="a4e13-106">When you set a column width, you are specifying the maximum width for the column in the rendered report.</span></span> <span data-ttu-id="a4e13-107">열은 텍스트 크기에 맞게 너비가 자동으로 변경되지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a4e13-107">Columns do not automatically adjust horizontally to accommodate text.</span></span>  
  
 <span data-ttu-id="a4e13-108">행 또는 열의 셀에 사각형 또는 데이터 영역이 들어 있는 경우 셀의 최소 높이 및 너비는 포함된 항목의 높이 및 너비에 따라 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="a4e13-108">If a cell in a row or column contains a rectangle or data region, the minimum height and width of the cell is determined by the height and width of the contained item.</span></span> <span data-ttu-id="a4e13-109">자세한 내용은 [렌더링 동작&#40;보고서 작성기 및 SSRS&#41;](rendering-behaviors-report-builder-and-ssrs.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a4e13-109">For more information, see [Rendering Behaviors &#40;Report Builder  and SSRS&#41;](rendering-behaviors-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-change-row-height-by-moving-row-handles"></a><span data-ttu-id="a4e13-110">행 핸들을 이동하여 행 높이를 변경하려면</span><span class="sxs-lookup"><span data-stu-id="a4e13-110">To change row height by moving row handles</span></span>  
  
1.  <span data-ttu-id="a4e13-111">디자인 뷰에서 테이블릭스 데이터 영역의 아무 곳이나 클릭하여 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="a4e13-111">In Design view, click anywhere in the tablix data region to select it.</span></span> <span data-ttu-id="a4e13-112">테이블릭스 데이터 영역의 바깥쪽 테두리에 회색 행 핸들이 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="a4e13-112">Gray row handles appear on the outside border of the tablix data region.</span></span>  
  
2.  <span data-ttu-id="a4e13-113">늘리려는 쪽의 행 핸들을 포인터로 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="a4e13-113">Hover over the row handle edge that you want to expand.</span></span> <span data-ttu-id="a4e13-114">양방향 화살표가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="a4e13-114">A double-headed arrow appears.</span></span>  
  
3.  <span data-ttu-id="a4e13-115">행의 가장자리를 클릭한 상태로 위쪽 또는 아래쪽으로 이동하여 행 높이를 조정합니다.</span><span class="sxs-lookup"><span data-stu-id="a4e13-115">Click to grab the edge of the row and move it higher or lower to adjust the row height.</span></span>  
  
### <a name="to-change-row-height-by-setting-cell-properties"></a><span data-ttu-id="a4e13-116">셀 속성을 설정하여 행 높이를 변경하려면</span><span class="sxs-lookup"><span data-stu-id="a4e13-116">To change row height by setting cell properties</span></span>  
  
1.  <span data-ttu-id="a4e13-117">디자인 뷰에서 테이블 행의 셀을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a4e13-117">In Design view, click a cell in the table row.</span></span>  
  
     <span data-ttu-id="a4e13-118">![테이블의 선택된 셀](../media/table-selectcell.png "테이블의 선택된 셀")</span><span class="sxs-lookup"><span data-stu-id="a4e13-118">![Selected Cell in a Table](../media/table-selectcell.png "Selected Cell in a Table")</span></span>  
  
2.  <span data-ttu-id="a4e13-119">표시되는 **속성** 창에서 **높이** 속성을 수정한 다음 **속성** 창 외부 아무 곳이나 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a4e13-119">In the **Properties** pane that displays, modify the **Height** property, and then click anywhere outside the **Properties** pane.</span></span>  
  
     <span data-ttu-id="a4e13-120">![선택한 테이블 셀의 속성 창](../media/cell-propertiespane.png "선택한 테이블 셀의 속성 창")</span><span class="sxs-lookup"><span data-stu-id="a4e13-120">![Properties Pane for selected table cell](../media/cell-propertiespane.png "Properties Pane for selected table cell")</span></span>  
  
### <a name="to-prevent-a-row-from-automatically-expanding-vertically"></a><span data-ttu-id="a4e13-121">행 높이가 자동으로 늘어나지 않도록 하려면</span><span class="sxs-lookup"><span data-stu-id="a4e13-121">To prevent a row from automatically expanding vertically</span></span>  
  
1.  <span data-ttu-id="a4e13-122">디자인 뷰에서 테이블릭스 데이터 영역의 아무 곳이나 클릭하여 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="a4e13-122">In Design view, click anywhere in the tablix data region to select it.</span></span> <span data-ttu-id="a4e13-123">테이블릭스 데이터 영역의 바깥쪽 테두리에 회색 행 핸들이 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="a4e13-123">Gray row handles appear on the outside border of the tablix data region.</span></span>  
  
2.  <span data-ttu-id="a4e13-124">행 핸들을 클릭하여 행을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="a4e13-124">Click the row handle to select the row.</span></span>  
  
3.  <span data-ttu-id="a4e13-125">속성 창에서 CanGrow를 **False**로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="a4e13-125">In the Properties pane, set CanGrow to **False**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="a4e13-126">속성 창이 표시되지 않는 경우 **보기** 메뉴에서 **속성**을 클릭하세요.</span><span class="sxs-lookup"><span data-stu-id="a4e13-126">If you cannot see the Properties pane, from the **View** menu, click **Properties**.</span></span>  
  
### <a name="to-change-column-width"></a><span data-ttu-id="a4e13-127">열 너비를 변경하려면</span><span class="sxs-lookup"><span data-stu-id="a4e13-127">To change column width</span></span>  
  
1.  <span data-ttu-id="a4e13-128">디자인 뷰에서 테이블릭스 데이터 영역의 아무 곳이나 클릭하여 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="a4e13-128">In Design view, click anywhere in the tablix data region to select it.</span></span> <span data-ttu-id="a4e13-129">테이블릭스 데이터 영역의 바깥쪽 테두리에 회색 열 핸들이 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="a4e13-129">Gray column handles appear on the outside border of the tablix data region.</span></span>  
  
2.  <span data-ttu-id="a4e13-130">늘리려는 쪽의 열 핸들을 포인터로 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="a4e13-130">Hover over the column handle edge that you want to expand.</span></span> <span data-ttu-id="a4e13-131">양방향 화살표가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="a4e13-131">A double-headed arrow appears.</span></span>  
  
3.  <span data-ttu-id="a4e13-132">열의 가장자리를 클릭한 상태로 왼쪽 또는 오른쪽으로 이동하여 열 너비를 조정합니다.</span><span class="sxs-lookup"><span data-stu-id="a4e13-132">Click to grab the edge of the column and move it left or right to adjust the column width.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4e13-133">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a4e13-133">See Also</span></span>  
 <span data-ttu-id="a4e13-134">[테이블 릭 스 데이터 영역 &#40;보고서 작성기 및 SSRS&#41;](../tablix-data-region-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="a4e13-134">[Tablix Data Region &#40;Report Builder and SSRS&#41;](../tablix-data-region-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="a4e13-135">[테이블 릭 스 데이터 영역 셀, 행 및 열 &#40;보고서 작성기&#41; 및 SSRS](tablix-data-region-cells-rows-and-columns-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="a4e13-135">[Tablix Data Region Cells, Rows, and Columns &#40;Report Builder&#41; and SSRS](tablix-data-region-cells-rows-and-columns-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="a4e13-136">[테이블 &#40;보고서 작성기 및 SSRS&#41;](tables-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="a4e13-136">[Tables &#40;Report Builder  and SSRS&#41;](tables-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="a4e13-137">[행렬 &#40;보고서 작성기 및 SSRS&#41;](create-a-matrix-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="a4e13-137">[Matrices &#40;Report Builder and SSRS&#41;](create-a-matrix-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="a4e13-138">[&#40;보고서 작성기 및 SSRS를 나열&#41;](create-invoices-and-forms-with-lists-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="a4e13-138">[Lists &#40;Report Builder and SSRS&#41;](create-invoices-and-forms-with-lists-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="a4e13-139">테이블, 행렬 및 목록&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="a4e13-139">Tables, Matrices, and Lists &#40;Report Builder and SSRS&#41;</span></span>](tables-matrices-and-lists-report-builder-and-ssrs.md)  
  
  
