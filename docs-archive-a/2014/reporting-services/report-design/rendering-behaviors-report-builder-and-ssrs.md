---
title: 렌더링 동작(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 8f873ef9-27a3-40e5-b58b-6774f8027a58
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 1d6a6aa91c547f4739b172f9303ac9e61bde5771
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736072"
---
# <a name="rendering-behaviors-report-builder--and-ssrs"></a><span data-ttu-id="84b69-102">렌더링 동작(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="84b69-102">Rendering Behaviors (Report Builder  and SSRS)</span></span>
  <span data-ttu-id="84b69-103">보고서를 렌더링하는 경우 선택한 렌더러에 따라 보고서 본문 및 해당 내용에 특정 규칙이 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="84b69-103">Depending on the renderer you select, certain rules are applied to the report body and its contents when rendering a report.</span></span> <span data-ttu-id="84b69-104">여러 보고서 항목이 한 페이지에 함께 포함되는 방식은 다음과 같은 요소의 조합에 따라 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="84b69-104">How report items fit together on a page is determined by the combination of these factors:</span></span>  
  
-   <span data-ttu-id="84b69-105">렌더링 규칙</span><span class="sxs-lookup"><span data-stu-id="84b69-105">Rendering rules.</span></span>  
  
-   <span data-ttu-id="84b69-106">보고서 항목의 너비와 높이</span><span class="sxs-lookup"><span data-stu-id="84b69-106">The width and height of report items.</span></span>  
  
-   <span data-ttu-id="84b69-107">보고서 본문의 크기</span><span class="sxs-lookup"><span data-stu-id="84b69-107">The size of the report body.</span></span>  
  
-   <span data-ttu-id="84b69-108">페이지의 너비와 높이</span><span class="sxs-lookup"><span data-stu-id="84b69-108">The width and height of the page.</span></span>  
  
-   <span data-ttu-id="84b69-109">렌더러별 페이징 지원</span><span class="sxs-lookup"><span data-stu-id="84b69-109">Renderer-specific support for paging.</span></span>  
  
 <span data-ttu-id="84b69-110">이 항목에서는 Reporting Services에서 적용하는 일반적인 규칙에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="84b69-110">This topic discusses the general rules that are applied by Reporting Services.</span></span> <span data-ttu-id="84b69-111">자세한 내용은 [보고서 항목 렌더링&#40;보고서 작성기 및 SSRS&#41;](rendering-report-items-report-builder-and-ssrs.md), [데이터 영역 렌더링&#40;보고서 작성기 및 SSRS&#41;](rendering-data-regions-report-builder-and-ssrs.md) 및 [데이터 렌더링&#40;보고서 작성기 및 SSRS&#41;](rendering-data-report-builder-and-ssrs.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="84b69-111">For more information, see [Rendering Report Items &#40;Report Builder and SSRS&#41;](rendering-report-items-report-builder-and-ssrs.md), [Rendering Data Regions &#40;Report Builder and SSRS&#41;](rendering-data-regions-report-builder-and-ssrs.md), and [Rendering Data &#40;Report Builder and SSRS&#41;](rendering-data-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="general-behaviors-for-html-mhtml-word-and-excel-soft-page-break-renderers"></a><span data-ttu-id="84b69-112">HTML, MHTML, Word 및 Excel 등 소프트 페이지 나누기 렌더러의 일반적인 동작</span><span class="sxs-lookup"><span data-stu-id="84b69-112">General Behaviors for HTML, MHTML, Word, and Excel (Soft Page-Break Renderers)</span></span>  
 <span data-ttu-id="84b69-113">HTML 및 MHTML 형식을 사용하여 내보낸 보고서는 다양한 길이의 페이지가 표시되는 컴퓨터 화면 기반 환경에 최적화됩니다.</span><span class="sxs-lookup"><span data-stu-id="84b69-113">Reports exported using HTML and MHTML formats are optimized for a computer screen-based experience where pages can be various lengths.</span></span> <span data-ttu-id="84b69-114">페이지 나누기는 보고서 본문 내의 근사 위치에서만 세로로 삽입됩니다.</span><span class="sxs-lookup"><span data-stu-id="84b69-114">Page breaks are inserted vertically only at approximate locations within the report body.</span></span> <span data-ttu-id="84b69-115">이러한 근사 위치는 속성 창에서 설정하는 대화형 높이를 통해 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="84b69-115">These approximate locations are determined by the interactive height setting in the Properties pane.</span></span> <span data-ttu-id="84b69-116">예를 들어 대화형 높이가 5인치로 설정된 경우를 가정해 봅니다.</span><span class="sxs-lookup"><span data-stu-id="84b69-116">For example, suppose the interactive height is set to 5 inches.</span></span> <span data-ttu-id="84b69-117">보고서가 렌더링되면 페이지 높이는 대략 5인치가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="84b69-117">When the report is rendered, the page height is approximately 5 inches in length.</span></span> <span data-ttu-id="84b69-118">Word 및 Excel에서는 논리적 페이지 나누기에 기반하여 페이지를 매기며 대화형 높이 설정을 무시합니다.</span><span class="sxs-lookup"><span data-stu-id="84b69-118">Word and Excel paginate based on logical page breaks and ignore the interactive height setting.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="84b69-119">소프트 페이지 나누기 렌더러에서 보고서가 표시되는 방식을 결정하려면 보고서 미리 보기를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="84b69-119">To determine how a report will appear in a soft page-break renderer, use Report Preview.</span></span> <span data-ttu-id="84b69-120">이 미리 보기에서 보고서는 HTML, MHTML, Word 또는 Excel 형식으로 렌더링된 보고서와 동일하게 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="84b69-120">The report appears as it would in a HTML, MHTML, Word, or Excel format.</span></span>  
  
 <span data-ttu-id="84b69-121">HTML, MHTML, Word 또는 Excel로 보고서를 내보내는 경우 다음과 같은 일반적인 규칙이 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="84b69-121">When exporting a report to HTML, MHTML, Word, or Excel, the following general rules are followed:</span></span>  
  
-   <span data-ttu-id="84b69-122">사용자가 명시적으로 삽입한 논리적 페이지 나누기가 보고서 항목에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="84b69-122">Logical page breaks, the page breaks that you explicitly insert, are applied to report items.</span></span> <span data-ttu-id="84b69-123">예를 들어 각 그룹 사이에 페이지 나누기를 삽입한 경우 보고서가 렌더링될 때 해당 페이지 나누기가 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="84b69-123">For example, if you insert a page break between each group, they are applied when the report is rendered.</span></span>  
  
-   <span data-ttu-id="84b69-124">근사 레이아웃은 페이지 높이 및 보고서 항목이 나타나는 횟수를 기반으로 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="84b69-124">An approximate layout is created using the page height and the number of times that the report item appears.</span></span> <span data-ttu-id="84b69-125">예를 들어 높이 .5인치의 입력란이 보고서에 5번 나타나면 2.5인치가 예약됩니다.</span><span class="sxs-lookup"><span data-stu-id="84b69-125">For example, if a text box is .5 inches in height and repeats five times in the report, 2.5 inches are reserved.</span></span>  
  
-   <span data-ttu-id="84b69-126">소프트 페이지 나누기가 여러 개인 경우 대화형 높이 설정에 기반하여 삽입됩니다.</span><span class="sxs-lookup"><span data-stu-id="84b69-126">Multiple soft page breaks are inserted based on the interactive height setting.</span></span> <span data-ttu-id="84b69-127">HTML 및 ReportViewer 컨트롤에서 소프트 페이지 나누기를 표시하지 않고 명시적 페이지 나누기만을 사용하여 페이지 매김을 제어하려면 **interactive height** 값을 0 또는 매우 큰 숫자로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="84b69-127">To suppress in HTML and the ReportViewer controls, and control pagination only with explicit page breaks, set the **interactive height** value to 0 or an extremely large number.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="84b69-128">대화형 너비 설정은 소프트 페이지 나누기 렌더러에서 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="84b69-128">The interactive width setting is not used in the soft page break renderers.</span></span>  
  
-   <span data-ttu-id="84b69-129">한 페이지에 함께 유지해야 하는 보고서 항목, 분리된 항목 및 창을 한 페이지에 포함하기 위해 보고서 페이지의 크기가 늘어날 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="84b69-129">Report pages can grow to accommodate widows, orphans and report items that need to be kept together.</span></span> <span data-ttu-id="84b69-130">따라서 보고서가 화면 너비보다 커질 수 있으며 이에 따라 슬라이더 막대를 사용하여 보고서를 보아야 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="84b69-130">This means that the report can extend beyond the screen width and can be viewed by using slider bars.</span></span>  
  
-   <span data-ttu-id="84b69-131">페이지 매김은 세로로만 보고서에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="84b69-131">Pagination is applied to reports vertically only.</span></span>  
  
-   <span data-ttu-id="84b69-132">페이지 여백은 적용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="84b69-132">Page margins are not applied.</span></span>  
  
## <a name="general-behaviors-for-pdf-image-and-print-hard-page-break-renderers"></a><span data-ttu-id="84b69-133">PDF, 이미지 및 인쇄 등 하드 페이지 나누기 렌더러의 일반적인 동작</span><span class="sxs-lookup"><span data-stu-id="84b69-133">General Behaviors for PDF, Image, and Print (Hard Page-Break Renderers)</span></span>  
 <span data-ttu-id="84b69-134">PDF 및 이미지를 사용하여 내보낸 보고서는 페이지 크기가 일정한 책 또는 인쇄물 환경에 최적화됩니다.</span><span class="sxs-lookup"><span data-stu-id="84b69-134">Reports exported using PDF and Image are optimized for a book-like or printed experience where pages are a consistent size.</span></span> <span data-ttu-id="84b69-135">페이지 나누기는 보고서 본문 내의 특정 위치에 세로 및 가로로 삽입됩니다.</span><span class="sxs-lookup"><span data-stu-id="84b69-135">Page breaks are inserted vertically and horizontally at specific locations within the report body.</span></span> <span data-ttu-id="84b69-136">이러한 특정 위치는 페이지 너비 및 페이지 높이 설정을 통해 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="84b69-136">These specific locations are determined by the page width and page height settings.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="84b69-137">하드 페이지 나누기 렌더러에서 보고서가 표시되는 방식을 결정하려면 인쇄 미리 보기를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="84b69-137">To determine how a report will appear in a hard page-break renderer, use Print Preview.</span></span> <span data-ttu-id="84b69-138">이 미리 보기에서 보고서는 PDF, 이미지 형식으로 렌더링된 보고서와 동일하게 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="84b69-138">The report appears as it would in a PDF or Image format.</span></span>  
  
-   <span data-ttu-id="84b69-139">페이지 번호는 왼쪽에서 오른쪽으로 매겨진 다음 위에서 아래로 매겨집니다.</span><span class="sxs-lookup"><span data-stu-id="84b69-139">Pages are numbered sequentially from left to right, then top to bottom.</span></span>  
  
-   <span data-ttu-id="84b69-140">사용자가 명시적으로 삽입한 논리적 페이지 나누기가 보고서 항목에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="84b69-140">Logical page breaks, the page breaks that you explicitly insert, are applied to report items.</span></span> <span data-ttu-id="84b69-141">이러한 페이지 나누기로 인해 특정 보고서 항목에 의해 다른 보고서 항목이 다음 페이지에서 시작할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="84b69-141">These page breaks can cause report items to push other items to the next page.</span></span>  
  
-   <span data-ttu-id="84b69-142">한 페이지에 유지해야 하는 여러 보고서 항목에서 물리적 페이지 나누기가 발생하면 해당 항목 모두가 다음 페이지로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="84b69-142">If a physical page break occurs through report items that must be kept together, the items that must be kept together are moved to the next page.</span></span>  
  
-   <span data-ttu-id="84b69-143">페이지 크기 제약 조건으로 인해 모든 항목을 한 페이지에 유지하지 못하거나 여러 항목을 반복하지 못할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="84b69-143">Because of page size constraints, it may not be possible to keep all the items together or to repeat items.</span></span> <span data-ttu-id="84b69-144">이러한 경우 렌더러에서는 다른 항목과 함께 반복하는 규칙을 무시하여 해당 보고서 항목이 페이지 크기에 맞도록 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="84b69-144">If that occurs, the renderer might ignore certain rules for repeating with another item in order to allow the report item to fit on the page.</span></span>  
  
-   <span data-ttu-id="84b69-145">입력란이 너무 커져 사용 가능한 세로 페이지 영역을 벗어나는 경우처럼 특정 항목을 한 페이지에 함께 유지할 수 없는 경우에는 해당 항목이 물리적 페이지 경계에서 잘리고 다음 페이지에서 계속됩니다.</span><span class="sxs-lookup"><span data-stu-id="84b69-145">If an item cannot be kept together, for example a text box that grows too large to fit within the vertical usable page area, then the item will be clipped at the physical page boundary and will continue on the next page.</span></span>  
  
-   <span data-ttu-id="84b69-146">페이지 매김은 세로 및 가로로 보고서에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="84b69-146">Pagination is applied to reports vertically and horizontally.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="84b69-147">대화형 너비 설정은 하드 페이지 나누기 렌더러에서 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="84b69-147">The interactive width setting is not used in the hard page break renderers.</span></span>  
  
## <a name="minimum-spacing-between-report-items"></a><span data-ttu-id="84b69-148">보고서 항목 간의 최소 간격</span><span class="sxs-lookup"><span data-stu-id="84b69-148">Minimum Spacing Between Report Items</span></span>  
 <span data-ttu-id="84b69-149">보고서 항목은 해당 내용을 포함하기 위해 보고서 본문 내에서 크기가 늘어납니다.</span><span class="sxs-lookup"><span data-stu-id="84b69-149">Report items grow within the report body to accommodate their contents.</span></span> <span data-ttu-id="84b69-150">예를 들어 행렬 데이터 영역은 일반적으로 보고서 렌더링 시 페이지에서 가로 및 아래쪽으로 확대되고, 입력란의 높이는 식에서 반환하는 데이터에 따라 조정됩니다.</span><span class="sxs-lookup"><span data-stu-id="84b69-150">For example, a matrix data region typically expands across and down the page when the report is rendered, and the height of a text box adjusts depending on the data returned from an expression.</span></span>  
  
 <span data-ttu-id="84b69-151">렌더러에서는 사용자가 보고서 레이아웃에 정의한 보고서 항목 간의 최소 간격을 유지합니다.</span><span class="sxs-lookup"><span data-stu-id="84b69-151">Renderers maintain the minimum space between report items that you define in the report layout.</span></span> <span data-ttu-id="84b69-152">보고서 레이아웃에서 특정 보고서 항목을 다른 보고서 항목 근처에 배치하는 경우 두 보고서 항목 간의 거리는 보고서가 가로 또는 세로 방향으로 확장될 때 유지해야 하는 최소 거리가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="84b69-152">When you place a report item adjacent to another on the report layout, the distance between the report items becomes the minimum distance that must be maintained as the report grows horizontally or vertically.</span></span> <span data-ttu-id="84b69-153">예를 들어 보고서에 행렬 데이터 영역을 추가한 다음 해당 행렬로부터 .25인치 오른쪽에 사각형을 추가하면 행렬이 확장될 때 행렬과 사각형 간의 간격이 .25인치로 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="84b69-153">For example, if you add a matrix data region to a report and then add a rectangle .25 inches to the right of the matrix, that space is maintained as the matrix grows.</span></span> <span data-ttu-id="84b69-154">각 항목은 오른쪽으로 이동하여 해당 항목과 그 왼쪽에 있는 항목 사이에 최소 거리를 유지합니다.</span><span class="sxs-lookup"><span data-stu-id="84b69-154">Each item moves to the right to maintain the minimum distance from items that end to the left of it.</span></span>  
  
## <a name="page-headers-and-footers"></a><span data-ttu-id="84b69-155">페이지 머리글 및 바닥글</span><span class="sxs-lookup"><span data-stu-id="84b69-155">Page Headers and Footers</span></span>  
 <span data-ttu-id="84b69-156">페이지 머리글 및 바닥글은 렌더링되는 각 페이지의 맨 위와 맨 아래에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="84b69-156">Page headers and footers appear at the top and bottom of each rendered page.</span></span> <span data-ttu-id="84b69-157">페이지 머리글 및 바닥글의 서식을 지정하여 테두리 색, 테두리 스타일 및 테두리 두께를 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="84b69-157">You can format the page header and footer so that there is a border color, border style, and border width.</span></span> <span data-ttu-id="84b69-158">배경색 또는 배경 이미지를 추가할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="84b69-158">You can also add a background color or background image.</span></span> <span data-ttu-id="84b69-159">이러한 서식 옵션은 사용자가 선택한 서식에 따라 모두 렌더링됩니다.</span><span class="sxs-lookup"><span data-stu-id="84b69-159">These formatting options are all rendered, depending on the format that you choose.</span></span>  
  
 <span data-ttu-id="84b69-160">HTML 또는 MHTML 렌더링 형식으로 렌더링되는 경우 페이지 머리글 및 바닥글에는 다음과 같은 규칙이 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="84b69-160">The following rules apply to page headers and footers when rendered in the HTML or MHTML rendering format:</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="84b69-161">Excel에서 머리글 및 바닥글을 렌더링하는 방법에 대한 자세한 내용은 [Microsoft Excel로 내보내기&#40;보고서 작성기 및 SSRS&#41;](../report-builder/exporting-to-microsoft-excel-report-builder-and-ssrs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="84b69-161">For information about how Excel renders headers and footers, see [Exporting to Microsoft Excel &#40;Report Builder and SSRS&#41;](../report-builder/exporting-to-microsoft-excel-report-builder-and-ssrs.md).</span></span> <span data-ttu-id="84b69-162">Word에서 머리글 및 바닥글을 렌더링하는 방법에 대한 자세한 내용은 [Microsoft Word로 내보내기&#40;보고서 작성기 및 SSRS&#41;](../report-builder/exporting-to-microsoft-word-report-builder-and-ssrs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="84b69-162">For information about how Word renders headers and footers, see [Exporting to Microsoft Word &#40;Report Builder and SSRS&#41;](../report-builder/exporting-to-microsoft-word-report-builder-and-ssrs.md).</span></span>  
  
-   <span data-ttu-id="84b69-163">머리글 및 바닥글은 사용 가능한 페이지 영역 내의 모든 페이지에서 맨 위와 맨 아래에 렌더링되어 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="84b69-163">When present, the header and footer is rendered at the top and bottom of every page within the usable page area.</span></span>  
  
-   <span data-ttu-id="84b69-164">머리글 또는 바닥글이 숨겨져 있는 페이지의 경우 머리글 또는 바닥글이 렌더링되지는 않지만 사용 가능한 페이지 영역 내에서 머리글 또는 바닥글의 높이는 계속 예약되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="84b69-164">On pages where the header or footer is hidden, the height of the header or footer is still reserved within the usable page area, even though the header or footer is not rendered.</span></span>  
  
-   <span data-ttu-id="84b69-165">머리글 또는 바닥글의 내용이 커져 머리글 또는 바닥글의 경계를 벗어나면 해당 내용을 포함할 수 있도록 머리글 또는 바닥글의 크기가 늘어납니다.</span><span class="sxs-lookup"><span data-stu-id="84b69-165">If the contents of the header or footer grows beyond the boundaries of the header or footer, the header or footer increases in size to accommodate the contents.</span></span>  
  
 <span data-ttu-id="84b69-166">PDF 또는 이미지 렌더링 형식으로 렌더링되는 경우 페이지 머리글 및 바닥글에는 다음과 같은 규칙이 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="84b69-166">The following rules apply to page headers and footers when rendered in the PDF or Image rendering format:</span></span>  
  
-   <span data-ttu-id="84b69-167">머리글 또는 바닥글은 사용 가능한 페이지 영역 내의 모든 페이지에서 맨 위와 맨 아래에 렌더링됩니다.</span><span class="sxs-lookup"><span data-stu-id="84b69-167">The header or footer is rendered at the top and bottom of every page within the usable page area.</span></span>  
  
-   <span data-ttu-id="84b69-168">머리글 또는 바닥글이 숨겨져 있는 페이지의 경우 머리글 또는 바닥글이 렌더링되지는 않지만 사용 가능한 페이지 영역 내에서 머리글 또는 바닥글의 높이는 계속 예약되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="84b69-168">On pages where the header or footer is hidden, the height of the header or footer is still reserved within the usable page area, even though the header or footer is not rendered.</span></span>  
  
-   <span data-ttu-id="84b69-169">머리글 및 바닥글의 크기가 늘어나거나 줄어들지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="84b69-169">The header and footer do not grow or shrink.</span></span> <span data-ttu-id="84b69-170">머리글 또는 바닥글은 모든 페이지에서 지정된 높이에 렌더링되며 이 높이는 사용자가 머리글 또는 바닥글을 만들 때 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="84b69-170">They are rendered on every page at the height specified when you created the header or footer.</span></span>  
  
-   <span data-ttu-id="84b69-171">보고서 내에 있는 열의 수와 상관없이 페이지당 하나의 머리글과 바닥글만 있습니다.</span><span class="sxs-lookup"><span data-stu-id="84b69-171">Regardless of the number of columns within the report, there is only one header and footer per page.</span></span>  
  
-   <span data-ttu-id="84b69-172">머리글 또는 바닥글의 내용이 커져 머리글 또는 바닥글의 경계를 벗어나는 경우 해당 내용이 잘립니다.</span><span class="sxs-lookup"><span data-stu-id="84b69-172">If the contents of the header or footer grow beyond the boundaries of the header or footer, the contents are clipped.</span></span>  
  
-   <span data-ttu-id="84b69-173">하위 보고서로 보고서가 렌더링되는 경우 원본 .rdl 파일에 정의된 머리글 및 바닥글은 렌더링되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="84b69-173">Headers and footers that are defined in the original RDL file are not rendered when the report is rendered as a subreport.</span></span>  
  
## <a name="logical-page-breaks"></a><span data-ttu-id="84b69-174">논리적 페이지 나누기</span><span class="sxs-lookup"><span data-stu-id="84b69-174">Logical Page Breaks</span></span>  
 <span data-ttu-id="84b69-175">논리적 페이지 나누기는 보고서 항목 또는 그룹의 앞이나 뒤에 사용자가 삽입하는 페이지 나누기입니다.</span><span class="sxs-lookup"><span data-stu-id="84b69-175">Logical page breaks are page breaks that you insert before or after report items or groups.</span></span> <span data-ttu-id="84b69-176">페이지 나누기는 보고서를 렌더링하거나 내보낼 때 보고서를 최적의 상태로 보기 위해 보고서 내용을 보고서 페이지에 맞추는 방식을 결정하는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="84b69-176">Page breaks help to determine how the content is fitted to a report page for optimal viewing when rendering or exporting the report.</span></span>  
  
 <span data-ttu-id="84b69-177">논리적 페이지 나누기를 렌더링하는 경우 다음과 같은 규칙이 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="84b69-177">The following rules apply when rendering logical page breaks:</span></span>  
  
-   <span data-ttu-id="84b69-178">항상 숨겨져 있는 보고서 항목 및 다른 보고서 항목을 클릭하여 표시 유형이 제어되는 보고서 항목에 대해서는 논리적 페이지 나누기가 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="84b69-178">Logical page breaks are ignored for report items that are constantly hidden and for report items where the visibility is controlled by clicking another report item.</span></span>  
  
-   <span data-ttu-id="84b69-179">조건부로 표시되는 항목을 보고서 렌더링 시점에서 볼 수 있는 경우 해당 항목에 논리적 페이지 나누기가 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="84b69-179">Logical page breaks are applied on conditionally visible items if they are currently visible at the time the report is rendered.</span></span>  
  
-   <span data-ttu-id="84b69-180">논리적 페이지 나누기가 적용되는 보고서 항목과 피어 보고서 항목 간의 간격은 그대로 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="84b69-180">Space is preserved between the report item with the logical page break and its peer report items.</span></span>  
  
-   <span data-ttu-id="84b69-181">보고서 항목 앞에 논리적 페이지 나누기를 삽입하면 해당 보고서 항목이 다음 페이지에서 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="84b69-181">Logical page breaks that are inserted before a report item push the report item down to the next page.</span></span> <span data-ttu-id="84b69-182">해당 보고서 항목은 다음 페이지의 맨 위에 렌더링됩니다.</span><span class="sxs-lookup"><span data-stu-id="84b69-182">The report item is rendered at the top of the next page.</span></span>  
  
-   <span data-ttu-id="84b69-183">테이블 또는 행렬 셀의 항목에 대해 정의한 논리적 페이지 나누기는 유지되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="84b69-183">Logical page breaks defined on items in table or matrix cells are not kept.</span></span> <span data-ttu-id="84b69-184">목록의 항목은 이 규칙에서 예외입니다.</span><span class="sxs-lookup"><span data-stu-id="84b69-184">This does not apply to items in lists.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84b69-185">참고 항목</span><span class="sxs-lookup"><span data-stu-id="84b69-185">See Also</span></span>  
 <span data-ttu-id="84b69-186">[여러 보고서 렌더링 확장 프로그램의 대화형 기능&#40;보고서 작성기 및 SSRS&#41;](../report-builder/interactive-functionality-different-report-rendering-extensions.md) </span><span class="sxs-lookup"><span data-stu-id="84b69-186">[Interactive Functionality for Different Report Rendering Extensions &#40;Report Builder and SSRS&#41;](../report-builder/interactive-functionality-different-report-rendering-extensions.md) </span></span>  
 <span data-ttu-id="84b69-187">[HTML로 렌더링&#40;보고서 작성기 및 SSRS&#41;](../report-builder/rendering-to-html-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="84b69-187">[Rendering to HTML &#40;Report Builder and SSRS&#41;](../report-builder/rendering-to-html-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="84b69-188">페이지 레이아웃 및 렌더링&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="84b69-188">Page Layout and Rendering &#40;Report Builder and SSRS&#41;</span></span>](page-layout-and-rendering-report-builder-and-ssrs.md)  
  
  
