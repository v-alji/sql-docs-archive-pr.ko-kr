---
title: 페이지 나누기 추가(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 3846cd48-2787-47e9-b13b-7fc45a205f68
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 55d6be3ae47827c5a8ff4a5b36e3ff2ce80e1034
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639305"
---
# <a name="add-a-page-break-report-builder-and-ssrs"></a><span data-ttu-id="d4790-102">페이지 나누기 추가(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="d4790-102">Add a Page Break (Report Builder and SSRS)</span></span>
  <span data-ttu-id="d4790-103">사각형, 데이터 영역 또는 데이터 영역 내의 그룹에 페이지 나누기를 추가하여 각 페이지의 정보 양을 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d4790-103">You can add a page break to rectangles, data regions, or groups within data regions to control the amount of information on each page.</span></span> <span data-ttu-id="d4790-104">페이지 나누기를 추가하면 보고서를 볼 때 각 페이지에 있는 항목만 처리하면 되기 때문에 게시된 보고서의 성능이 향상될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d4790-104">Adding page breaks can improve the performance of published reports because only the items on each page have to be processed as you view the report.</span></span> <span data-ttu-id="d4790-105">전체 보고서가 단일 페이지로 이뤄진 경우에는 모든 항목이 처리된 후에 보고서를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d4790-105">When the whole report is a single page, all items must be processed before you can view the report.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-a-page-break-to-a-data-region"></a><span data-ttu-id="d4790-106">데이터 영역에 페이지 나누기를 추가하려면</span><span class="sxs-lookup"><span data-stu-id="d4790-106">To add a page break to a data region</span></span>  
  
1.  <span data-ttu-id="d4790-107">디자인 화면에서 데이터 영역의 모퉁이 핸들을 마우스 오른쪽 단추로 클릭한 다음 **테이블릭스 속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d4790-107">On the design surface, right-click the corner handle of the data region and then click **Tablix Properties**.</span></span>  
  
2.  <span data-ttu-id="d4790-108">**일반** 탭의 **페이지 나누기 옵션**에서 다음 옵션 중 하나를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d4790-108">On the **General** tab, under **Page break options**, select one of the following options:</span></span>  
  
    -   <span data-ttu-id="d4790-109">**앞에 페이지 나누기 추가**.</span><span class="sxs-lookup"><span data-stu-id="d4790-109">**Add a page break before**.</span></span> <span data-ttu-id="d4790-110">테이블 앞에 페이지 나누기를 추가하려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d4790-110">Select this option when you want to add a page break before the table.</span></span>  
  
    -   <span data-ttu-id="d4790-111">**뒤에 페이지 나누기 추가**.</span><span class="sxs-lookup"><span data-stu-id="d4790-111">**Add a page break after**.</span></span> <span data-ttu-id="d4790-112">테이블 뒤에 페이지 나누기를 추가하려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d4790-112">Select this option when you want to add a page break after the table.</span></span>  
  
    -   <span data-ttu-id="d4790-113">**가능하면 테이블을 한 페이지에 표시**.</span><span class="sxs-lookup"><span data-stu-id="d4790-113">**Fit table on one page if possible**.</span></span> <span data-ttu-id="d4790-114">데이터를 한 페이지에 표시하려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d4790-114">Select this option when you want the data to stay on one page.</span></span>  
  
### <a name="to-add-a-page-break-to-a-rectangle"></a><span data-ttu-id="d4790-115">사각형에 페이지 나누기를 추가하려면</span><span class="sxs-lookup"><span data-stu-id="d4790-115">To add a page break to a rectangle</span></span>  
  
1.  <span data-ttu-id="d4790-116">디자인 화면에서 페이지 나누기를 추가하려는 사각형을 마우스 오른쪽 단추로 클릭한 다음 **사각형 속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d4790-116">On the design surface, right-click the rectangle where you want to add a page break, and then click **Rectangle Properties**.</span></span>  
  
2.  <span data-ttu-id="d4790-117">**일반** 탭의 **페이지 나누기 옵션**에서 다음 옵션 중 하나를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d4790-117">On the **General** tab, under **Page break options**, select one of the following options:</span></span>  
  
    -   <span data-ttu-id="d4790-118">**앞에 페이지 나누기 추가**.</span><span class="sxs-lookup"><span data-stu-id="d4790-118">**Add a page break before**.</span></span> <span data-ttu-id="d4790-119">사각형 앞에 페이지 나누기를 추가하려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d4790-119">Select this option when you want to add a page break before the rectangle.</span></span>  
  
    -   <span data-ttu-id="d4790-120">**뒤에 페이지 나누기 추가**.</span><span class="sxs-lookup"><span data-stu-id="d4790-120">**Add a page break after**.</span></span> <span data-ttu-id="d4790-121">사각형 뒤에 페이지 나누기를 추가하려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d4790-121">Select this option when you want to add a page break after the rectangle.</span></span>  
  
    -   <span data-ttu-id="d4790-122">**페이지 나누기에 테두리 생략**.</span><span class="sxs-lookup"><span data-stu-id="d4790-122">**Omit border on page break**.</span></span> <span data-ttu-id="d4790-123">페이지 나누기에 테두리를 표시하지 않으려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d4790-123">Select this option when you do not want a border on the page break.</span></span>  
  
    -   <span data-ttu-id="d4790-124">**가능하면 내용을 단일 페이지에 유지**.</span><span class="sxs-lookup"><span data-stu-id="d4790-124">**Keep contents together on a single page, if possible**.</span></span> <span data-ttu-id="d4790-125">사각형 내의 내용을 한 페이지에 표시하려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d4790-125">Select this option when you want contents inside the rectangle to stay on one page.</span></span>  
  
### <a name="to-add-a-page-break-to-a-row-group-in-a-table-matrix-or-list"></a><span data-ttu-id="d4790-126">테이블, 행렬, 또는 목록의 행 그룹에 페이지 나누기를 추가하려면</span><span class="sxs-lookup"><span data-stu-id="d4790-126">To add a page break to a row group in a table, matrix, or list</span></span>  
  
1.  <span data-ttu-id="d4790-127">그룹화 창에서 행 그룹을 마우스 오른쪽 단추로 클릭한 다음 **그룹 속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d4790-127">In the Grouping pane, right-click a row group, and then click **Group Properties**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="d4790-128">열 그룹에서는 페이지 나누기가 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="d4790-128">Page breaks are ignored on column groups.</span></span>  
  
2.  <span data-ttu-id="d4790-129">테이블에 있는 그룹의 각 인스턴스 사이에 페이지 나누기를 추가하려면 **페이지 나누기** 탭에서 **각 그룹 인스턴스 사이** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d4790-129">On the **Page Breaks** tab, select **Between each instance of a group** to add a page break between each instance of a group in the table.</span></span>  
  
3.  <span data-ttu-id="d4790-130">필요에 따라 **그룹 시작 부분에도** 또는 **그룹 끝 부분에도** 를 선택하여 그룹이 테이블에서 시작하거나 끝날 때 페이지 나누기가 추가되도록 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d4790-130">Optionally, select **Also at the start of a group** or **Also at the end of a group** to specify that a page break be added when a group starts or ends in the table.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4790-131">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d4790-131">See Also</span></span>  
 <span data-ttu-id="d4790-132">[Reporting Services의 페이지 매김&#40;보고서 작성기 및 SSRS&#41;](pagination-in-reporting-services-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="d4790-132">[Pagination in Reporting Services &#40;Report Builder  and SSRS&#41;](pagination-in-reporting-services-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="d4790-133">[렌더링 동작&#40;보고서 작성기 및 SSRS&#41;](rendering-behaviors-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="d4790-133">[Rendering Behaviors &#40;Report Builder  and SSRS&#41;](rendering-behaviors-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="d4790-134">페이지 머리글 및 바닥글&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="d4790-134">Page Headers and Footers &#40;Report Builder and SSRS&#41;</span></span>](page-headers-and-footers-report-builder-and-ssrs.md)  
  
  
