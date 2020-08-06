---
title: 보고서를 스크롤할 때 머리글 계속 표시(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 6d9192a4-fd5c-41ad-b9ef-f88f9496afed
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d37fcd38a402dc0f88ac002c679c1046d5b0b583
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739280"
---
# <a name="keep-headers-visible-when-scrolling-through-a-report-report-builder-and-ssrs"></a><span data-ttu-id="93b9b-102">보고서를 스크롤할 때 머리글 계속 표시(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="93b9b-102">Keep Headers Visible When Scrolling Through a Report (Report Builder and SSRS)</span></span>
  <span data-ttu-id="93b9b-103">보고서를 렌더링한 다음 스크롤할 때 행 및 열 레이블이 화면에서 사라지지 않도록 하려면 행 또는 열 머리글을 고정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="93b9b-103">To prevent row and column labels from scrolling out of view after rendering a report, you can freeze the row or column headings.</span></span>  
  
 <span data-ttu-id="93b9b-104">행과 열을 제어하는 방법은 테이블 또는 행렬이 있는지 여부에 따라 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="93b9b-104">How you control the rows and columns depends on whether you have a table or a matrix.</span></span> <span data-ttu-id="93b9b-105">테이블이 있는 경우 정적 멤버(행 및 열 머리글)가 계속 표시되도록 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="93b9b-105">If you have a table, you configure static members (row and column headings) to remain visible.</span></span> <span data-ttu-id="93b9b-106">행렬이 있는 경우 행 및 열 그룹 머리글이 계속 표시되도록 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="93b9b-106">If you have a matrix, you configure row and column group headers to remain visible.</span></span>  
  
 <span data-ttu-id="93b9b-107">Excel로 보고서를 내보내는 경우 머리글이 자동으로 고정되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="93b9b-107">If you export the report to Excel, the header will not be frozen automatically.</span></span> <span data-ttu-id="93b9b-108">Excel에서 창을 고정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="93b9b-108">You can freeze the pane in Excel.</span></span> <span data-ttu-id="93b9b-109">자세한 내용은 [Microsoft Excel로 내보내기&#40;보고서 작성기 및 SSRS&#41;](../report-builder/exporting-to-microsoft-excel-report-builder-and-ssrs.md)의 **페이지 머리글 및 바닥글** 섹션을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="93b9b-109">For more information see the **Page Headers and Footers** section of [Exporting to Microsoft Excel &#40;Report Builder and SSRS&#41;](../report-builder/exporting-to-microsoft-excel-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="93b9b-110">테이블에 행 및 열 그룹이 있는 경우에도 스크롤하는 동안 이러한 그룹 머리글이 계속 표시되도록 할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="93b9b-110">Even if a table has row and column groups, you cannot keep those group headers visible while scrolling</span></span>  
  
 <span data-ttu-id="93b9b-111">다음 이미지에서는 표를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="93b9b-111">The following image shows a table.</span></span>  
  
 <span data-ttu-id="93b9b-112">![테이블](../media/table.png "테이블")</span><span class="sxs-lookup"><span data-stu-id="93b9b-112">![Table](../media/table.png "Table")</span></span>  
  
 <span data-ttu-id="93b9b-113">다음 이미지에서는 행렬을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="93b9b-113">The following image shows a matrix.</span></span>  
  
 <span data-ttu-id="93b9b-114">![행렬](../media/matrix.png "행렬")</span><span class="sxs-lookup"><span data-stu-id="93b9b-114">![Matrix](../media/matrix.png "Matrix")</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-keep-matrix-group-headers-visible-while-scrolling"></a><span data-ttu-id="93b9b-115">스크롤하는 동안 행렬 그룹 머리글을 계속 표시하려면</span><span class="sxs-lookup"><span data-stu-id="93b9b-115">To keep matrix group headers visible while scrolling</span></span>  
  
1.  <span data-ttu-id="93b9b-116">테이블릭스 데이터 영역에서 행, 열 또는 모퉁이 핸들을 마우스 오른쪽 단추로 클릭한 다음 **테이블릭스 속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="93b9b-116">Right-click the row, column, or corner handle of a tablix data region, and then click **Tablix Properties**.</span></span>  
  
2.  <span data-ttu-id="93b9b-117">**일반** 탭의 **행 머리글** 또는 **열 머리글**아래에서 **스크롤하는 동안 머리글 계속 표시**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="93b9b-117">On the **General** tab, under **Row Headers** or **Column Headers**, select **Header should remain visible while scrolling**.</span></span>  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-keep-a-static-tablix-member-row-or-column-visible-while-scrolling"></a><span data-ttu-id="93b9b-118">스크롤하는 동안 정적 테이블릭스 멤버(행 또는 열)를 계속 표시하려면</span><span class="sxs-lookup"><span data-stu-id="93b9b-118">To keep a static tablix member (row or column) visible while scrolling</span></span>  
  
1.  <span data-ttu-id="93b9b-119">디자인 화면에서 테이블의 아무 곳이나 클릭하여 그룹 창에 그룹과 함께 정적 멤버를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="93b9b-119">On the design surface, click anywhere in the table to display static members, as well as groups, in the grouping pane.</span></span>  
  
     <span data-ttu-id="93b9b-120">![그룹화 창](../media/grouppane-updated.png "그룹화 창")</span><span class="sxs-lookup"><span data-stu-id="93b9b-120">![Grouping pane](../media/grouppane-updated.png "Grouping pane")</span></span>  
  
     <span data-ttu-id="93b9b-121">행 그룹 창에 행 그룹 계층 구조의 정적 및 동적 멤버 계층이 표시되고 열 그룹 창에 열 그룹 계층 구조의 비슷한 정적 및 동적 멤버 계층이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="93b9b-121">The Row Groups pane displays the hierarchical static and dynamic members for the row groups hierarchy, and the Column groups pane shows a similar display for the column groups hierarchy.</span></span>  
  
2.  <span data-ttu-id="93b9b-122">그룹화 창의 오른쪽에서 아래쪽 화살표를 클릭한 다음 **고급 모드**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="93b9b-122">On the right side of the grouping pane, click the down arrow, and then click **Advanced Mode**.</span></span>  
  
3.  <span data-ttu-id="93b9b-123">스크롤하는 동안 계속 표시할 정적 멤버(행 또는 열)를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="93b9b-123">Click the static member (row or column) that you want to remain visible while scrolling.</span></span> <span data-ttu-id="93b9b-124">속성 창에 **테이블릭스 멤버** 속성이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="93b9b-124">The Properties pane displays the **Tablix Member** properties.</span></span>  
  
     <span data-ttu-id="93b9b-125">![테이블릭스 멤버 속성](../media/grouppane-tablixmember-updated.png "테이블릭스 멤버 속성")</span><span class="sxs-lookup"><span data-stu-id="93b9b-125">![Tablix Member properties](../media/grouppane-tablixmember-updated.png "Tablix Member properties")</span></span>  
  
4.  <span data-ttu-id="93b9b-126">속성 창에서 **Fixeddata** 를로 설정 `True` 합니다.</span><span class="sxs-lookup"><span data-stu-id="93b9b-126">In the Properties pane, set **FixedData** to `True`.</span></span>  
  
5.  <span data-ttu-id="93b9b-127">스크롤하는 동안 계속 표시할 인접 멤버의 수만큼 이 과정을 반복합니다.</span><span class="sxs-lookup"><span data-stu-id="93b9b-127">Repeat this for as many adjacent members as you want to keep visible while scrolling.</span></span>  
  
6.  <span data-ttu-id="93b9b-128">보고서를 미리 봅니다.</span><span class="sxs-lookup"><span data-stu-id="93b9b-128">Preview the report.</span></span>  
  
 <span data-ttu-id="93b9b-129">보고서 페이지를 아래로 또는 옆으로 이동할 때 정적 테이블릭스 멤버가 계속 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="93b9b-129">As you page down or across the report, the static tablix members remain in view.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93b9b-130">참고 항목</span><span class="sxs-lookup"><span data-stu-id="93b9b-130">See Also</span></span>  
 <span data-ttu-id="93b9b-131">[테이블릭스 데이터 영역&#40;보고서 작성기 및 SSRS&#41;](../tablix-data-region-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="93b9b-131">[Tablix Data Region &#40;Report Builder and SSRS&#41;](../tablix-data-region-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="93b9b-132">[보고서 찾기, 보기 및 관리&#40;보고서 작성기 및 SSRS&#41;](../report-builder/finding-viewing-and-managing-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="93b9b-132">[Finding, Viewing, and Managing Reports &#40;Report Builder and SSRS &#41;](../report-builder/finding-viewing-and-managing-reports-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="93b9b-133">[보고서 &#40;보고서 작성기 및 SSRS&#41;내보내기](../report-builder/export-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="93b9b-133">[Exporting Reports &#40;Report Builder and SSRS&#41;](../report-builder/export-reports-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="93b9b-134">[그룹과 함께 머리글 및 바닥글 표시&#40;보고서 작성기 및 SSRS&#41;](display-headers-and-footers-with-a-group-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="93b9b-134">[Display Headers and Footers with a Group &#40;Report Builder and SSRS&#41;](display-headers-and-footers-with-a-group-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="93b9b-135">[여러 페이지에 행 및 열 머리글 표시&#40;보고서 작성기 및 SSRS&#41;](display-row-and-column-headers-on-multiple-pages-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="93b9b-135">[Display Row and Column Headers on Multiple Pages &#40;Report Builder and SSRS&#41;](display-row-and-column-headers-on-multiple-pages-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="93b9b-136">그룹화 창&#40;보고서 작성기&#41;</span><span class="sxs-lookup"><span data-stu-id="93b9b-136">Grouping Pane &#40;Report Builder&#41;</span></span>](grouping-pane-report-builder.md)  
  
  
