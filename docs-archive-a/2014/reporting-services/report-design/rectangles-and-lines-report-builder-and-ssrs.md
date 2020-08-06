---
title: 사각형 및 선(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: d6226b0c-0398-4185-8565-96099876fc21
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 96b795c3edeabb938e836be3486e28e08737a8e9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659817"
---
# <a name="rectangles-and-lines-report-builder-and-ssrs"></a><span data-ttu-id="2dfb9-102">사각형 및 선(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="2dfb9-102">Rectangles and Lines (Report Builder and SSRS)</span></span>
  <span data-ttu-id="2dfb9-103">사각형과 선을 사용하여 보고서에서 시각 효과를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2dfb9-103">Rectangles and lines can create visual effects within a report.</span></span> <span data-ttu-id="2dfb9-104">이러한 보고서 항목에 대한 표시 속성은 홈 탭의 테두리 섹션에서 설정할 수 있으며 다른 속성은 속성 창을 사용하여 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2dfb9-104">You can set display properties on these report items from the Border section of the Home tab, and set other properties by using the Properties pane.</span></span> <span data-ttu-id="2dfb9-105">사각형에는 배경색, 이미지, 도구 설명 또는 책갈피와 같은 기능을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2dfb9-105">You can add features like a background color or image, a tooltip, or a bookmark to a rectangle.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
##  <a name="rectangles-and-lines-as-report-parts"></a><a name="RectanglesLinesReportParts"></a> <span data-ttu-id="2dfb9-106">보고서 파트인 사각형 및 선</span><span class="sxs-lookup"><span data-stu-id="2dfb9-106">Rectangles and Lines as Report Parts</span></span>  
 <span data-ttu-id="2dfb9-107">사각형과 그에 포함된 항목을 보고서와는 별도로 보고서 파트로 게시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2dfb9-107">You can publish rectangles with the items that they contain separately from the report as report parts.</span></span> [!INCLUDE[ssRBrptparts](../../includes/ssrbrptparts-md.md)]  
  
 <span data-ttu-id="2dfb9-108">사각형 내의 보고서 항목은 보고서 파트로 게시할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2dfb9-108">You cannot publish the report items within the rectangle as report parts.</span></span> <span data-ttu-id="2dfb9-109">사용자가 사각형을 보고서에 추가하면 보고서에는 사각형과 함께 사각형에 포함된 항목도 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="2dfb9-109">When people add the rectangle to a report, they get the rectangle and the items it contains.</span></span>  
  

  
##  <a name="using-a-rectangle-as-a-container"></a><a name="RectangleAsContainer"></a> <span data-ttu-id="2dfb9-110">사각형을 컨테이너로 사용</span><span class="sxs-lookup"><span data-stu-id="2dfb9-110">Using a Rectangle as a Container</span></span>  
 <span data-ttu-id="2dfb9-111">사각형을 다른 항목의 컨테이너로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2dfb9-111">You can use a rectangle as a container for other items.</span></span> <span data-ttu-id="2dfb9-112">사각형을 이동하면 사각형 내의 항목도 함께 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="2dfb9-112">When you move the rectangle, the items that are contained within the rectangle move along with it.</span></span> <span data-ttu-id="2dfb9-113">사각형에 포함된 항목의 **Parent** 속성에는 사각형 이름이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="2dfb9-113">An item within the rectangle shows the name of the rectangle in its **Parent** property.</span></span> <span data-ttu-id="2dfb9-114">사각형을 컨테이너로 사용하는 방법은 [사각형 또는 컨테이너 추가&#40;보고서 작성기 및 SSRS&#41;](add-a-rectangle-or-container-report-builder-and-ssrs.md) 및 [행렬 및 차트에 같은 데이터 표시&#40;보고서 작성기&#41;](display-the-same-data-on-a-matrix-and-a-chart-report-builder.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2dfb9-114">For more information about using a rectangle as a container, see [Add a Rectangle or Container &#40;Report Builder and SSRS&#41;](add-a-rectangle-or-container-report-builder-and-ssrs.md) and [Display the Same Data on a Matrix and a Chart &#40;Report Builder&#41;](display-the-same-data-on-a-matrix-and-a-chart-report-builder.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2dfb9-115">사각형은 사각형 안에서 만들거나 사각형 안으로 끌어 놓은 항목에 대한 컨테이너입니다.</span><span class="sxs-lookup"><span data-stu-id="2dfb9-115">A rectangle is only a container for items that you either create in the rectangle or drag into the rectangle.</span></span> <span data-ttu-id="2dfb9-116">디자인 화면에서 기존 항목을 포함하도록 사각형을 그려도 사각형이 기존 항목의 컨테이너로 동작하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2dfb9-116">If you draw a rectangle around an item that already exists on the design surface, the rectangle will not act as its container.</span></span> <span data-ttu-id="2dfb9-117">이 사각형은 기존 항목의 Parent 속성에 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2dfb9-117">The rectangle will not be listed in the item's Parent property.</span></span>  
  
 <span data-ttu-id="2dfb9-118">사각형을 사용하여 보고서 항목을 포함할 때는 보고서 렌더링이 전체적으로 항목에 미치는 영향을 고려해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2dfb9-118">When using rectangles to contain report items, consider how the items will be affected as a whole during report rendering.</span></span> <span data-ttu-id="2dfb9-119">테이블과 같이 반복되는 데이터 행을 포함하는 보고서 항목은 쿼리에서 반환한 데이터를 수용하도록 확장되며 이는 사각형 내 다른 항목의 위치에 영향을 미칩니다.</span><span class="sxs-lookup"><span data-stu-id="2dfb9-119">Report items that contain repeated rows of data (for example, tables) will expand to accommodate the data that is returned by a query, and this affects the positioning of other items in the rectangle.</span></span> <span data-ttu-id="2dfb9-120">항목이 데이터 영역 아래에 배치되어 있는 경우 테이블에서는 해당 항목을 아래로 밀어냅니다.</span><span class="sxs-lookup"><span data-stu-id="2dfb9-120">A table will push items down if they are positioned below the data region.</span></span> <span data-ttu-id="2dfb9-121">항목을 제자리에 고정하려면 테이블의 아래쪽 가장자리 위에 위쪽 가장자리가 있는 사각형의 내부에 보고서 항목을 배치합니다.</span><span class="sxs-lookup"><span data-stu-id="2dfb9-121">To anchor an item in place, you can place the report item inside of a rectangle that has an upper edge above the lower edge of the table.</span></span> <span data-ttu-id="2dfb9-122">자세한 내용은 [렌더링 동작&#40;보고서 작성기 및 SSRS&#41;](rendering-behaviors-report-builder-and-ssrs.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2dfb9-122">For more information, see [Rendering Behaviors &#40;Report Builder  and SSRS&#41;](rendering-behaviors-report-builder-and-ssrs.md).</span></span>  
  

  
##  <a name="adding-a-report-border"></a><a name="ReportBorder"></a> <span data-ttu-id="2dfb9-123">보고서 테두리 추가</span><span class="sxs-lookup"><span data-stu-id="2dfb9-123">Adding a Report Border</span></span>  
 <span data-ttu-id="2dfb9-124">선이나 사각형을 추가하지 않고 머리글, 바닥글 및 보고서 본문 자체에 테두리를 추가하여 보고서에 테두리를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2dfb9-124">You can add a border to a report by adding borders to the headers, footers, and report body themselves, without adding lines or rectangles.</span></span> <span data-ttu-id="2dfb9-125">자세한 내용은 [보고서에 테두리 추가&#40;보고서 작성기 및 SSRS&#41;](add-a-border-to-a-report-report-builder-and-ssrs.md)에 대해 자세히 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="2dfb9-125">For more information, see [Add a Border to a Report &#40;Report Builder and SSRS&#41;](add-a-border-to-a-report-report-builder-and-ssrs.md).</span></span>  
  

  
##  <a name="how-to-topics"></a><a name="HowTo"></a><span data-ttu-id="2dfb9-126">방법 도움말 항목</span><span class="sxs-lookup"><span data-stu-id="2dfb9-126">How-To Topics</span></span>  
 [<span data-ttu-id="2dfb9-127">보고서에 테두리 추가&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="2dfb9-127">Add a Border to a Report &#40;Report Builder and SSRS&#41;</span></span>](add-a-border-to-a-report-report-builder-and-ssrs.md)  
  
 [<span data-ttu-id="2dfb9-128">사각형 또는 컨테이너 추가&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="2dfb9-128">Add a Rectangle or Container &#40;Report Builder and SSRS&#41;</span></span>](add-a-rectangle-or-container-report-builder-and-ssrs.md)  
  
 [<span data-ttu-id="2dfb9-129">선 추가 및 수정&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="2dfb9-129">Add and Modify a Line &#40;Report Builder and SSRS&#41;</span></span>](add-and-modify-a-line-report-builder-and-ssrs.md)  
  
## <a name="see-also"></a><span data-ttu-id="2dfb9-130">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2dfb9-130">See Also</span></span>  
 [<span data-ttu-id="2dfb9-131">사각형 또는 컨테이너 추가&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="2dfb9-131">Add a Rectangle or Container &#40;Report Builder and SSRS&#41;</span></span>](add-a-rectangle-or-container-report-builder-and-ssrs.md)  
  
  
