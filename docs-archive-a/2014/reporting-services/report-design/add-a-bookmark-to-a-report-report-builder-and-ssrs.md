---
title: 보고서에 책갈피 추가(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: f130562e-5673-40e3-8e01-de7227a21d41
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: fae543dd1b071ff38853637a3da57ffd2410c3a0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739376"
---
# <a name="add-a-bookmark-to-a-report-report-builder-and-ssrs"></a><span data-ttu-id="716f8-102">보고서에 책갈피 추가(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="716f8-102">Add a Bookmark to a Report (Report Builder and SSRS)</span></span>
  <span data-ttu-id="716f8-103">사용자 지정된 목차를 제공하거나 보고서의 사용자 지정된 내부 탐색 링크를 제공하려는 경우 보고서에 책갈피 또는 책갈피 링크를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="716f8-103">Add bookmarks and bookmark links to a report when you want to provide a customized table of contents or to provide customized internal navigation links in the report.</span></span> <span data-ttu-id="716f8-104">일반적으로 각 테이블 또는 차트나 테이블 또는 행렬에 표시된 고유한 그룹 값 등 사용자를 안내하려는 보고서 위치에 책갈피를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="716f8-104">Typically, you add bookmarks to locations in the report to which you want to direct users, such as to each table or chart or to the unique group values displayed in a table or matrix.</span></span> <span data-ttu-id="716f8-105">사용자 고유의 문자열을 만들어 책갈피로 사용하거나 그룹의 경우 책갈피를 그룹 식으로 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="716f8-105">You can create your own strings to use as bookmarks, or, for groups, you can set the bookmark to the group expression.</span></span>  
  
 <span data-ttu-id="716f8-106">책갈피를 만든 후에는 사용자가 클릭하면 각 책갈피로 이동되는 보고서 항목을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="716f8-106">After you create bookmarks, you can add report items that the user can click to go to each bookmark.</span></span> <span data-ttu-id="716f8-107">이러한 항목은 일반적으로 입력란 또는 이미지입니다.</span><span class="sxs-lookup"><span data-stu-id="716f8-107">These items are typically text boxes or images.</span></span>  
  
 <span data-ttu-id="716f8-108">예를 들어 보고서에 색상별로 그룹화된 테이블이 표시되는 경우 그룹 식을 기반으로 책갈피를 그룹 머리글에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="716f8-108">For example, if your report displays a table grouped by color, you would add a bookmark based on the group expression to the group header.</span></span> <span data-ttu-id="716f8-109">그런 다음 색 값을 표시한 보고서의 시작 부분에 단일 입력란이 있는 테이블을 추가하고 해당 입력란에 책갈피 링크를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="716f8-109">Then you would add a table with a single text box at the beginning of the report that displayed the color values, and set the bookmark link on that text box.</span></span> <span data-ttu-id="716f8-110">색을 클릭하면 보고서가 해당 색의 그룹 머리글 행을 표시하는 페이지로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="716f8-110">When you click the color, the report jumps to the page that displays the group header row for that color.</span></span>  
  
 <span data-ttu-id="716f8-111">모든 보고서 항목에 책갈피를 추가하고 입력란, 이미지 또는 차트의 계산된 계열과 같이 **동작** 속성이 있는 모든 항목에 책갈피 링크를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="716f8-111">You can add a bookmark to any report item and add a bookmark link to any item that has an **Action** property, for example, a text box, an image, or a calculated series in a chart.</span></span> <span data-ttu-id="716f8-112">자세한 내용은 [동작 속성 대화 상자&#40;보고서 작성기 및 SSRS&#41;](../action-properties-dialog-box-report-builder-and-ssrs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="716f8-112">For more information, see the [Action Properties Dialog Box &#40;Report Builder and SSRS&#41;](../action-properties-dialog-box-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-a-bookmark"></a><span data-ttu-id="716f8-113">책갈피를 추가하려면</span><span class="sxs-lookup"><span data-stu-id="716f8-113">To add a bookmark</span></span>  
  
1.  <span data-ttu-id="716f8-114">보고서 디자인 뷰에서 책갈피를 추가할 입력란, 이미지, 차트 또는 기타 보고서 항목을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="716f8-114">In report design view, select the text box, image, chart, or other report item to which you want to add a bookmark.</span></span> <span data-ttu-id="716f8-115">선택한 항목의 속성이 속성 창에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="716f8-115">The properties for the selected item appear in the Properties pane.</span></span>  
  
2.  <span data-ttu-id="716f8-116">**책갈피**옆의 입력란에 이 책갈피의 레이블인 문자열을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="716f8-116">In the text box next to **Bookmark**, type a string that is the label for this bookmark.</span></span> <span data-ttu-id="716f8-117">예를 들어 **BikePhoto** 를 보고서의 이미지에 대한 책갈피로 입력할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="716f8-117">For example, you could type **BikePhoto** as the bookmark for an image in your report.</span></span> <span data-ttu-id="716f8-118">또는 식(**fx**) 단추를 클릭하여 열리는 **식** 대화 상자에서 레이블을 반환하는 식을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="716f8-118">Alternatively, click the Expression (**fx**) button to open the **Expression** dialog box to specify an expression that evaluates to a label.</span></span> <span data-ttu-id="716f8-119">그룹의 경우 입력하는 식이 그룹 식이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="716f8-119">For a group, the expression you type should be the group expression.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="716f8-120">책갈피는 모든 문자열일 수 있지만 보고서에서 고유해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="716f8-120">The bookmark can be any string, but it must be unique in the report.</span></span> <span data-ttu-id="716f8-121">책갈피가 고유하지 않으면 해당 책갈피 링크 클릭 시 일치하는 첫 번째 책갈피가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="716f8-121">If the bookmark is not unique, a link to the bookmark finds the first matching bookmark.</span></span>  
  
### <a name="to-add-a-bookmark-link"></a><span data-ttu-id="716f8-122">책갈피 링크를 추가하려면</span><span class="sxs-lookup"><span data-stu-id="716f8-122">To add a bookmark link</span></span>  
  
1.  <span data-ttu-id="716f8-123">디자인 뷰에서 링크를 추가할 입력란, 이미지, 차트를 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="716f8-123">In Design view, right-click the text box, image, chart, to which you want to add a link and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="716f8-124">해당 보고서 항목에 대한 **속성** 대화 상자에서 **동작**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="716f8-124">In The **Properties** dialog box for that report item, click **Action**.</span></span>  
  
3.  <span data-ttu-id="716f8-125">**책갈피로 이동**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="716f8-125">Select **Go to bookmark**.</span></span> <span data-ttu-id="716f8-126">이 옵션에 대한 추가 섹션이 대화 상자에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="716f8-126">An additional section appears in the dialog box for this option.</span></span>  
  
4.  <span data-ttu-id="716f8-127">**책갈피 선택** 상자에서 책갈피 또는 책갈피를 반환하는 식을 입력하거나 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="716f8-127">In the **Select bookmark** box, type or select a bookmark or an expression that evaluates to a bookmark.</span></span> <span data-ttu-id="716f8-128">앞의 예제를 사용할 경우 **BikePhoto** 를 입력하여 보고서의 이미지에 대한 링크를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="716f8-128">Using the previous example, type **BikePhoto** to create a link to the image in your report.</span></span>  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
6.  <span data-ttu-id="716f8-129">(옵션) 텍스트가 자동으로 링크와 비슷하게 서식이 지정되지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="716f8-129">(Optional) The text is not automatically formatted like a link.</span></span> <span data-ttu-id="716f8-130">텍스트의 경우 텍스트가 링크임을 나타내기 위해 텍스트 색과 효과를 변경하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="716f8-130">For text, it is helpful to change the color and effect of the text to indicate that the text is a link.</span></span> <span data-ttu-id="716f8-131">예를 들어 리본 메뉴의 홈 탭에 있는 **글꼴** 섹션에서 색을 파란색으로 변경하고 효과를 밑줄로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="716f8-131">For example, change the color to blue and the effect to underline in the **Font** section in the Home tab of the Ribbon.</span></span>  
  
7.  <span data-ttu-id="716f8-132">링크를 테스트하려면 **실행** 을 클릭하여 보고서를 미리 본 다음, 이 링크를 설정한 보고서 항목을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="716f8-132">To test the link, click **Run** to preview the report, and then click the report item that you set this link on..</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="716f8-133">참고 항목</span><span class="sxs-lookup"><span data-stu-id="716f8-133">See Also</span></span>  
 <span data-ttu-id="716f8-134">[대화형 정렬, 문서 구조 및 링크&#40;보고서 작성기 및 SSRS&#41;](interactive-sort-document-maps-and-links-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="716f8-134">[Interactive Sort, Document Maps, and Links &#40;Report Builder and SSRS&#41;](interactive-sort-document-maps-and-links-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="716f8-135">[식&#40;보고서 작성기 및 SSRS&#41;](expressions-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="716f8-135">[Expressions &#40;Report Builder and SSRS&#41;](expressions-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="716f8-136">데이터 필터링, 그룹화 및 정렬&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="716f8-136">Filter, Group, and Sort Data &#40;Report Builder and SSRS&#41;</span></span>](filter-group-and-sort-data-report-builder-and-ssrs.md)  
  
  
