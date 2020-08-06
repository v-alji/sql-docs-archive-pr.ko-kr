---
title: 여러 페이지에 행 및 열 머리글 표시(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 2422b1e2-822f-4379-9d7f-9afebb350e3f
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 2e3b38aa0faab267a0cd71feafe600829237b55c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736091"
---
# <a name="display-row-and-column-headers-on-multiple-pages-report-builder-and-ssrs"></a><span data-ttu-id="0af53-102">여러 페이지에 행 및 열 머리글 표시(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="0af53-102">Display Row and Column Headers on Multiple Pages (Report Builder and SSRS)</span></span>
  <span data-ttu-id="0af53-103">여러 페이지에 걸쳐 있는 테이블릭스 데이터 영역에 대해 페이지마다 행 및 열 머리글을 반복할지 여부를 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0af53-103">You can control whether to repeat row and column headers on every page for a tablix data region that spans multiple pages.</span></span> <span data-ttu-id="0af53-104">테이블릭스 데이터 영역은 테이블, 행렬 또는 목록일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0af53-104">A tablix data region can be a table, matrix, or list.</span></span>  
  
 <span data-ttu-id="0af53-105">행과 열을 제어하는 방법은 테이블릭스 데이터 영역에 그룹 머리글이 있는지 여부에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="0af53-105">How you control the rows and columns depends on whether the tablix data region has group headers.</span></span> <span data-ttu-id="0af53-106">그룹 머리글이 있는 테이블릭스 데이터 영역을 클릭하면 다음 그림에서처럼 테이블릭스 영역이 점선으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="0af53-106">When you click in a tablix data region that has group headers, a dotted line shows the tablix areas, as shown in the following figure:</span></span>  
  
 <span data-ttu-id="0af53-107">![테이블릭스 데이터 영역](../media/rs-tablixareas.gif "테이블릭스 데이터 영역")</span><span class="sxs-lookup"><span data-stu-id="0af53-107">![Tablix data region areas](../media/rs-tablixareas.gif "Tablix data region areas")</span></span>  
  
 <span data-ttu-id="0af53-108">새 테이블 또는 행렬 마법사나 새 차트 마법사를 사용하거나, 그룹화 창에 필드를 추가하거나, 상황에 맞는 메뉴를 사용하여 그룹을 추가하면 행 및 열 그룹 머리글이 자동으로 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="0af53-108">Row and column group headers are created automatically when you add groups by using the New Table or Matrix wizard or the New Chart wizard, by adding fields to the Grouping pane, or by using context menus.</span></span> <span data-ttu-id="0af53-109">테이블릭스 데이터 영역에 테이블릭스 본문 영역만 있고 그룹 머리글은 없는 경우 행과 열은 테이블릭스 멤버입니다.</span><span class="sxs-lookup"><span data-stu-id="0af53-109">If the tablix data region has only a tablix body area and no group headers, the rows and columns are tablix members.</span></span>  
  
 <span data-ttu-id="0af53-110">정적 멤버의 경우에는 상단 인접 행 또는 측면 인접 열을 여러 페이지에 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0af53-110">For static members, you can display the top adjacent rows or the side adjacent columns on multiple pages.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-display-row-headers-on-multiple-pages"></a><span data-ttu-id="0af53-111">여러 페이지에 행 머리글을 표시하려면</span><span class="sxs-lookup"><span data-stu-id="0af53-111">To display row headers on multiple pages</span></span>  
  
1.  <span data-ttu-id="0af53-112">테이블릭스 데이터 영역에서 행, 열 또는 모퉁이 핸들을 마우스 오른쪽 단추로 클릭한 다음 **테이블릭스 속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0af53-112">Right-click the row, column, or corner handle of a tablix data region, and then click **Tablix Properties**.</span></span>  
  
2.  <span data-ttu-id="0af53-113">**행 머리글**에서 **각 페이지에서 머리글 행 반복**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="0af53-113">In **Row Headers**, select **Repeat header rows on each page**.</span></span>  
  
3.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
### <a name="to-display-column-headers-on-multiple-pages"></a><span data-ttu-id="0af53-114">여러 페이지에 열 머리글을 표시하려면</span><span class="sxs-lookup"><span data-stu-id="0af53-114">To display column headers on multiple pages</span></span>  
  
1.  <span data-ttu-id="0af53-115">테이블릭스 데이터 영역에서 행, 열 또는 모퉁이 핸들을 마우스 오른쪽 단추로 클릭한 다음 **테이블릭스 속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0af53-115">Right-click the row, column, or corner handle of a tablix data region, and then click **Tablix Properties**.</span></span>  
  
2.  <span data-ttu-id="0af53-116">**열 머리글**에서 **각 페이지에서 머리글 열 반복**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="0af53-116">In **Column Headers**, select **Repeat header columns on each page**.</span></span>  
  
3.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
### <a name="to-display-a-static-tablix-member-row-or-column-on-multiple-pages"></a><span data-ttu-id="0af53-117">정적 테이블릭스 멤버(행 또는 열)를 여러 페이지에 표시하려면</span><span class="sxs-lookup"><span data-stu-id="0af53-117">To display a static tablix member (row or column) on multiple pages</span></span>  
  
1.  <span data-ttu-id="0af53-118">디자인 화면에서 테이블릭스 데이터 영역의 행 또는 열 핸들을 클릭하여 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="0af53-118">On the design surface, click the row or column handle of the tablix data region to select it.</span></span> <span data-ttu-id="0af53-119">그룹화 창에 행 및 열 그룹이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="0af53-119">The Grouping pane displays the row and column groups.</span></span>  
  
2.  <span data-ttu-id="0af53-120">그룹화 창의 오른쪽에서 아래쪽 화살표를 클릭한 다음 **고급 모드**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0af53-120">On the right side of the Grouping pane, click the down arrow, and then click **Advanced Mode**.</span></span> <span data-ttu-id="0af53-121">행 그룹 창에 행 그룹 계층 구조의 정적 및 동적 멤버 계층이 표시되고 열 그룹 창에 열 그룹 계층 구조의 비슷한 정적 및 동적 멤버 계층이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="0af53-121">The Row Groups pane displays the hierarchical static and dynamic members for the row groups hierarchy and the Column groups pane shows a similar display for the column groups hierarchy.</span></span>  
  
3.  <span data-ttu-id="0af53-122">스크롤할 때 계속 표시할 정적 멤버(행 또는 열)에 해당하는 정적 멤버를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0af53-122">Click the static member that corresponds to the static member (row or column) that you want to remain visible while scrolling.</span></span> <span data-ttu-id="0af53-123">속성 창에 **테이블릭스 멤버** 속성이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="0af53-123">The Properties pane displays the **Tablix Member** properties.</span></span>  
  
     <span data-ttu-id="0af53-124">속성 창이 표시되지 않는 경우 보고서 작성기 창의 맨 위에서 **보기** 탭을 클릭한 다음, **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0af53-124">If you don't see the Properties pane, click the **View** tab at the top of the Report Builder window and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="0af53-125">속성 창에서 **RepeatOnNewPage** 를 True로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="0af53-125">In the Properties pane, set **RepeatOnNewPage** to True.</span></span>  
  
5.  <span data-ttu-id="0af53-126">**KeepWithGroup** 을 이후로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="0af53-126">Set **KeepWithGroup** to After.</span></span>  
  
6.  <span data-ttu-id="0af53-127">반복할 인접 멤버의 수만큼 이 과정을 반복합니다.</span><span class="sxs-lookup"><span data-stu-id="0af53-127">Repeat this for as many adjacent members as you want to repeat.</span></span>  
  
7.  <span data-ttu-id="0af53-128">보고서를 미리 봅니다.</span><span class="sxs-lookup"><span data-stu-id="0af53-128">Preview the report.</span></span>  
  
 <span data-ttu-id="0af53-129">테이블릭스 데이터 영역이 걸쳐 있는 보고서의 각 페이지를 볼 때 정적 테이블릭스 멤버가 각 페이지에서 반복됩니다.</span><span class="sxs-lookup"><span data-stu-id="0af53-129">As you view each page of the report that the tablix data region spans, the static tablix members repeat on each page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0af53-130">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0af53-130">See Also</span></span>  
 <span data-ttu-id="0af53-131">[보고서 찾기, 보기 및 관리&#40;보고서 작성기 및 SSRS&#41;](../report-builder/finding-viewing-and-managing-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="0af53-131">[Finding, Viewing, and Managing Reports &#40;Report Builder and SSRS &#41;](../report-builder/finding-viewing-and-managing-reports-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="0af53-132">[보고서 &#40;보고서 작성기 및 SSRS&#41;내보내기](../report-builder/export-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="0af53-132">[Exporting Reports &#40;Report Builder and SSRS&#41;](../report-builder/export-reports-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="0af53-133">[페이지 나누기, 머리글, 열 및 행 제어&#40;보고서 작성기 및 SSRS&#41;](controlling-page-breaks-headings-columns-and-rows-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="0af53-133">[Controlling Page Breaks, Headings, Columns, and Rows &#40;Report Builder and SSRS&#41;](controlling-page-breaks-headings-columns-and-rows-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="0af53-134">[그룹과 함께 머리글 및 바닥글 표시&#40;보고서 작성기 및 SSRS&#41;](display-headers-and-footers-with-a-group-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="0af53-134">[Display Headers and Footers with a Group &#40;Report Builder and SSRS&#41;](display-headers-and-footers-with-a-group-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="0af53-135">보고서를 스크롤할 때 머리글 계속 표시&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="0af53-135">Keep Headers Visible When Scrolling Through a Report &#40;Report Builder and SSRS&#41;</span></span>](keep-headers-visible-when-scrolling-through-a-report-report-builder-and-ssrs.md)  
  
  
