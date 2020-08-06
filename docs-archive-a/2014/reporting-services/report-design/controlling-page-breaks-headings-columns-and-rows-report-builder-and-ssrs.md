---
title: 페이지 나누기, 머리글, 열 및 행 제어(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 4b8fa41f-a727-4f23-8efb-fd9bb0d4cd1d
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 7dae06129ee5dc9962538e8d025dca9966325f5d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653206"
---
# <a name="controlling-page-breaks-headings-columns-and-rows-report-builder-and-ssrs"></a><span data-ttu-id="d332a-102">페이지 나누기, 머리글, 열 및 행 제어(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="d332a-102">Controlling Page Breaks, Headings, Columns, and Rows (Report Builder and SSRS)</span></span>
  <span data-ttu-id="d332a-103">페이지 나누기를 사용하여 보고서를 개별 페이지로 나누어 보고 인쇄할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d332a-103">A page break divides a report into separate pages for viewing and printing.</span></span> <span data-ttu-id="d332a-104">페이지 나누기는 보고서를 미리 볼 때나 다른 파일 형식으로 내보낼 때 최적의 상태로 표시하기 위해 내용을 보고서 페이지에 맞추는 방식을 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="d332a-104">Page breaks determine how the content is fitted to a report page for optimal viewing when you preview a report or export it to a different file format.</span></span>  
  
 <span data-ttu-id="d332a-105">또한 페이지 나누기를 추가하면 큰 보고서를 처리할 때 성능이 향상됩니다.</span><span class="sxs-lookup"><span data-stu-id="d332a-105">Adding page breaks also improves the performance of large reports when the are processed.</span></span> <span data-ttu-id="d332a-106">렌더링된 페이지가 표시되는 동안 나머지 페이지는 백그라운드에서 렌더링됩니다.</span><span class="sxs-lookup"><span data-stu-id="d332a-106">A rendered page is displayed while the rest of the pages are rendered in the background.</span></span> <span data-ttu-id="d332a-107">이렇게 하면 다른 페이지를 렌더링하는 동안 사용자는 초기 페이지를 보면서 기다릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d332a-107">This allows you to begin viewing the initial pages of the report while waiting for additional pages to become available.</span></span>  
  
 <span data-ttu-id="d332a-108">페이지 나누기는 테이블, 행렬, 목록, 차트, 계기 또는 이미지와 같은 보고서 항목에 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d332a-108">Page breaks can be added to report items such as a table, matrix, list, chart, gauge, or image.</span></span> <span data-ttu-id="d332a-109">또한 테이블, 행렬 또는 목록의 그룹에도 페이지 나누기를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d332a-109">You can also add page breaks to groups in a table, matrix, or list.</span></span> <span data-ttu-id="d332a-110">페이지 나누기는 그룹 전, 후, 사이에 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d332a-110">Page breaks can be added before, after, and between groups.</span></span> <span data-ttu-id="d332a-111">그룹 간 페이지 나누기는 기본적으로 보고서에 추가되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d332a-111">Page breaks between groups are not added to the report by default.</span></span>  
  
 <span data-ttu-id="d332a-112">자세한 내용은 [여러 페이지에 행 및 열 머리글 표시&#40;보고서 작성기 및 SSRS&#41;](display-row-and-column-headers-on-multiple-pages-report-builder-and-ssrs.md) 및 [보고서를 스크롤할 때 머리글 계속 표시&#40;보고서 작성기 및 SSRS&#41;](keep-headers-visible-when-scrolling-through-a-report-report-builder-and-ssrs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d332a-112">For more information, see [Display Row and Column Headers on Multiple Pages &#40;Report Builder and SSRS&#41;](display-row-and-column-headers-on-multiple-pages-report-builder-and-ssrs.md) and [Keep Headers Visible When Scrolling Through a Report &#40;Report Builder and SSRS&#41;](keep-headers-visible-when-scrolling-through-a-report-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="d332a-113">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d332a-113">See Also</span></span>  
 <span data-ttu-id="d332a-114">[&#40;보고서 작성기 및 SSRS를 나열&#41;](tables-matrices-and-lists-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="d332a-114">[Lists &#40;Report Builder and SSRS&#41;](tables-matrices-and-lists-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="d332a-115">[보고서 페이지에서 테이블릭스 데이터 영역 표시 제어&#40;보고서 작성기 및 SSRS&#41;](controlling-the-tablix-data-region-display-on-a-report-page.md) </span><span class="sxs-lookup"><span data-stu-id="d332a-115">[Controlling the Tablix Data Region Display on a Report Page &#40;Report Builder and SSRS&#41;](controlling-the-tablix-data-region-display-on-a-report-page.md) </span></span>  
 <span data-ttu-id="d332a-116">[그룹화 창&#40;보고서 작성기&#41;](grouping-pane-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="d332a-116">[Grouping Pane &#40;Report Builder&#41;](grouping-pane-report-builder.md) </span></span>  
 [<span data-ttu-id="d332a-117">그룹과 함께 머리글 및 바닥글 표시&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="d332a-117">Display Headers and Footers with a Group &#40;Report Builder and SSRS&#41;</span></span>](display-headers-and-footers-with-a-group-report-builder-and-ssrs.md)  
  
  
