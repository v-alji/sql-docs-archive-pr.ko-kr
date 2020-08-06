---
title: 보고서 인쇄(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 4bad1b6e-7d94-4b17-9502-ccd3dce0fdd9
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 3004734226e67ec435e90a4e62895c94173b23d8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648323"
---
# <a name="print-reports-report-builder-and-ssrs"></a><span data-ttu-id="b0429-102">보고서 인쇄(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="b0429-102">Print Reports (Report Builder and SSRS)</span></span>
  <span data-ttu-id="b0429-103">보고서 서버에 보고서를 저장한 후에는 내보낸 보고서를 보는 데 사용되는 애플리케이션, 보고서 관리자 또는 브라우저에서 보고서를 보고 인쇄할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b0429-103">After you save a report to a report server, you can view and print the report from a browser, Report Manager, or any application that you use to view an exported report.</span></span> <span data-ttu-id="b0429-104">보고서를 저장하기 전 미리 볼 때 해당 보고서를 인쇄할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b0429-104">Before saving a report, you can print it when you preview it.</span></span>  
  
 <span data-ttu-id="b0429-105">모든 인쇄 작업은 요청 시 클라이언트 컴퓨터에서 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="b0429-105">All print processing is performed on demand and on the client computer.</span></span> <span data-ttu-id="b0429-106">보고서 서버에서 웹 서버에 연결되어 있는 프린터로 직접 인쇄 작업을 라우팅할 수 있는 서버 쪽 인쇄 기능은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b0429-106">There is no server-side print functionality that enables you to route a print job directly from a report server to a printer that is attached to the Web server.</span></span> <span data-ttu-id="b0429-107">프린터와 인쇄 옵션은 개별 보고서 사용자가 표준 **인쇄** 대화 상자를 사용하여 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b0429-107">Printers and print options are selected by individual report users by using a standard **Print** dialog box.</span></span>  
  
 <span data-ttu-id="b0429-108">인쇄 결과물에 맞게 보고서를 디자인하려는 보고서 작성자는 페이지 나누기, 페이지 머리글과 바닥글, 식 및 배경 이미지를 사용하여 인쇄 기반 디자인을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b0429-108">Report authors who design reports specifically for print output can use page breaks, page headers and footers, expressions, and background images to create a print-based design.</span></span> <span data-ttu-id="b0429-109">인쇄 결과물에 맞는 보고서 디자인 요소의 예에는 모든 보고서의 뒷면에 인쇄되는 "규정 및 내용"이나 레터헤드와 같은 그래픽 및 텍스트 요소가 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b0429-109">Examples of report design elements intended for print output might include terms and conditions that you print on the back of every report, or graphic and text elements that mimic letterhead.</span></span>  
  
 <span data-ttu-id="b0429-110">여러 렌더링 형식에 대해 페이지 매김이 구현되는 방식으로 인해 렌더링 형식에 따라 일부 보고서에서는 최적의 인쇄 결과물을 얻지 못할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b0429-110">Due to the way pagination is implemented for different rendering formats, you might not be able to achieve optimum print output results for every report in every rendering format.</span></span> <span data-ttu-id="b0429-111">다음 목록에서는 이에 대한 예를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="b0429-111">The following list provides examples:</span></span>  
  
1.  <span data-ttu-id="b0429-112">보고서 페이지는 데이터 양의 변화를 수용할 수 있도록 디자인됩니다.</span><span class="sxs-lookup"><span data-stu-id="b0429-112">Report pages are designed to accommodate variable amounts of data.</span></span> <span data-ttu-id="b0429-113">예를 들어 행렬을 포함하는 보고서에서 사용자가 행과 열을 대화형으로 토글하면 이에 맞게 페이지가 가로와 세로 방향으로 모두 늘어납니다.</span><span class="sxs-lookup"><span data-stu-id="b0429-113">Reports that include a matrix, for example, can cause a page to grow both horizontally and vertically depending on whether a user interactively toggles rows and columns.</span></span> <span data-ttu-id="b0429-114">행렬을 확장하지 않는 사용자에게는 행렬을 확장하는 사용자와는 다른 인쇄 결과가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="b0429-114">A user who does not expand a matrix will get different print results than a user who does.</span></span>  
  
2.  <span data-ttu-id="b0429-115">같은 보고서에 가로 모드와 세로 모드의 페이지를 함께 사용할 수 없으며 브라우저 또는 다른 애플리케이션에서 렌더링된 보고서 레이아웃과 함께 존재하거나 이를 대체하는 인쇄 기반 레이아웃을 만들 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b0429-115">You cannot combine landscape and portrait mode pages in the same report, nor is there a way to create a print-based layout that replaces or exists alongside the layout of a report as rendered in a browser or other application.</span></span>  
  
3.  <span data-ttu-id="b0429-116">내보낸 보고서 인쇄물에는 대부분 사용자가 컴퓨터 모니터에서 볼 때 보고서에 표시되는 항목이 모두 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="b0429-116">For most exported reports, report printouts include everything that is visible on the report, as viewed by the user on a computer monitor.</span></span> <span data-ttu-id="b0429-117">보고서 디자인 화면의 공백이 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="b0429-117">White space from the report design surface is preserved.</span></span> <span data-ttu-id="b0429-118">빈 페이지를 가로로 추가하거나 제거하려면 보고서 페이지 너비를 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="b0429-118">To add or remove extra blank pages horizontally, change the report page width.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b0429-119">브라우저의 인쇄 명령을 사용할 경우 HTML 보고서 인쇄물에는 첫 번째 페이지의 내용만 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="b0429-119">HTML report printouts may contain only the content on the first page if you are using the browser's Print command.</span></span> <span data-ttu-id="b0429-120">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 클라이언트 인쇄 기능을 사용하여 HTML 보고서를 인쇄하면 보다 나은 결과를 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b0429-120">You can achieve better results if you print HTML reports using the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] client printing functionality.</span></span> <span data-ttu-id="b0429-121">자세한 내용은 [인쇄 컨트롤을 사용하여 브라우저에서 보고서 인쇄&#40;보고서 작성기 및 SSRS&#41;](print-reports-from-a-browser-with-the-print-control-report-builder-and-ssrs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b0429-121">For more information, see [Print Reports from a Browser with the Print Control &#40;Report Builder and SSRS&#41;](print-reports-from-a-browser-with-the-print-control-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="in-this-section"></a><span data-ttu-id="b0429-122">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="b0429-122">In This Section</span></span>  
 [<span data-ttu-id="b0429-123">인쇄 컨트롤을 사용하여 브라우저에서 보고서 인쇄&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="b0429-123">Print Reports from a Browser with the Print Control &#40;Report Builder and SSRS&#41;</span></span>](print-reports-from-a-browser-with-the-print-control-report-builder-and-ssrs.md)  
 <span data-ttu-id="b0429-124">클라이언트 쪽 인쇄 기능을 사용하여 웹 브라우저나 보고서 관리자에서 보고서를 인쇄하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="b0429-124">Describes how to use client-side printing to print reports from your Web browser or Report Manager.</span></span>  
  
 [<span data-ttu-id="b0429-125">다른 애플리케이션에서 보고서 인쇄&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="b0429-125">Print Reports from Other Applications &#40;Report Builder and SSRS&#41;</span></span>](print-reports-from-other-applications-report-builder-and-ssrs.md)  
 <span data-ttu-id="b0429-126">다른 애플리케이션으로 내보낸 보고서를 인쇄하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="b0429-126">Describes how to print reports exported to another application.</span></span>  
  
 [<span data-ttu-id="b0429-127">보고서 인쇄&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="b0429-127">Print a Report &#40;Report Builder and SSRS&#41;</span></span>](print-a-report-report-builder-and-ssrs.md)  
 <span data-ttu-id="b0429-128">보고서를 인쇄하는 방법, 페이지 여백을 조절하는 방법, 하드 페이지 나누기 렌더러(PDF, 이미지 또는 인쇄)로 렌더링할 보고서의 용지 크기를 지정하는 방법에 대한 단계별 지침을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="b0429-128">Provides step-by-step instructions on how to print a report, how to control the margins on a page, and on how to specify the paper size for reports that will be rendered by hard-page break renderers: PDF, Image, or Print.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0429-129">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b0429-129">See Also</span></span>  
 <span data-ttu-id="b0429-130">[보고서 &#40;보고서 작성기 및 SSRS&#41;내보내기](export-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="b0429-130">[Exporting Reports &#40;Report Builder and SSRS&#41;](export-reports-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="b0429-131">[페이지 머리글 및 바닥글 &#40;보고서 작성기 및 SSRS&#41;](../report-design/page-headers-and-footers-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="b0429-131">[Page Headers and Footers &#40;Report Builder and SSRS&#41;](../report-design/page-headers-and-footers-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="b0429-132">[이미지 &#40;보고서 작성기 및 SSRS&#41;](../report-design/images-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="b0429-132">[Images &#40;Report Builder and SSRS&#41;](../report-design/images-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="b0429-133">Reporting Services의 페이지 매김&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="b0429-133">Pagination in Reporting Services &#40;Report Builder  and SSRS&#41;</span></span>](../report-design/pagination-in-reporting-services-report-builder-and-ssrs.md)  
  
  
