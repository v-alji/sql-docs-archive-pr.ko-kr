---
title: ReportItems 컬렉션 참조(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: edc0c75f-0530-4e6d-85aa-3385301bfd00
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 61c89002adafb030288535debfe72de061945640
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728048"
---
# <a name="reportitems-collection-references-report-builder-and-ssrs"></a><span data-ttu-id="3313d-102">ReportItems 컬렉션 참조(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="3313d-102">ReportItems Collection References (Report Builder and SSRS)</span></span>
  <span data-ttu-id="3313d-103">`ReportItems` 기본 제공 컬렉션은 데이터 영역의 행 또는 보고서 디자인 화면의 입력란과 같은 보고서 항목의 입력란 집합입니다.</span><span class="sxs-lookup"><span data-stu-id="3313d-103">The `ReportItems` built-in collection is the set of text boxes from report items such as rows of a data region or text boxes on the report design surface.</span></span> <span data-ttu-id="3313d-104">`ReportItems` 컬렉션에는 페이지 머리글, 페이지 바닥글 또는 보고서 본문의 현재 범위에 있는 입력란이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="3313d-104">The `ReportItems` collection includes text boxes that are in the current scope of a page header, page footer, or report body.</span></span> <span data-ttu-id="3313d-105">이 컬렉션은 보고서 처리기 및 보고서 렌더러에 의해 런타임에 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="3313d-105">This collection is determined at run time by the report processor and the report renderer.</span></span> <span data-ttu-id="3313d-106">현재 범위는 사용자가 보고서 페이지를 볼 때 보고서 처리기가 보고서 데이터 및 보고서 항목 레이아웃 요소를 연속적으로 조합함에 따라 변경됩니다.</span><span class="sxs-lookup"><span data-stu-id="3313d-106">The current scope changes as the report processor successively combines report data and the report item layout elements as the user views pages of a report.</span></span> <span data-ttu-id="3313d-107">`ReportItems` 기본 제공 컬렉션을 사용하여 각 페이지의 첫 번째 및 마지막 항목을 표시하는 사전 스타일의 페이지 머리글을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3313d-107">You can use the `ReportItems` built-in collection to produce dictionary-style page headers that show the first and last items on each page.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="using-the-reportitems-value-property"></a><span data-ttu-id="3313d-108">ReportItems 값 속성 사용</span><span class="sxs-lookup"><span data-stu-id="3313d-108">Using the ReportItems Value Property</span></span>  
 <span data-ttu-id="3313d-109">`ReportItems` 컬렉션 내의 항목에는 Value라는 하나의 속성만 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3313d-109">Items within the `ReportItems` collection have only one property: Value.</span></span> <span data-ttu-id="3313d-110">`ReportItems` 항목의 값을 사용하면 보고서에 있는 다른 필드의 데이터를 표시하거나 계산할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3313d-110">The value for a `ReportItems` item can be used to display or calculate data from another field in the report.</span></span> <span data-ttu-id="3313d-111">현재 입력란의 값에 액세스하려는 경우 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 기본 제공 전역 Me.Value를 사용하거나 그냥 Value만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3313d-111">To access the value of the current text box, you can use the [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] built-in global Me.Value or simply Value.</span></span> <span data-ttu-id="3313d-112">First와 같은 보고서 함수 및 집계 함수에서는 정규화된 구문을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3313d-112">In report functions such as First and aggregate functions, use the fully qualified syntax.</span></span>  
  
 <span data-ttu-id="3313d-113">다음은 그 예입니다.</span><span class="sxs-lookup"><span data-stu-id="3313d-113">For example:</span></span>  
  
-   <span data-ttu-id="3313d-114">이 식을 입력란에 배치하면 `Textbox1`이라는 `ReportItem` 입력란의 값이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="3313d-114">This expression, placed in a text box, displays the value of a `ReportItem` text box named `Textbox1`:</span></span>  
  
     `=ReportItems!Textbox1.Value`  
  
-   <span data-ttu-id="3313d-115">텍스트 상자 색 속성에 배치 되는이 식은 `ReportItem` 값이 0 > 때 텍스트를 검정으로 표시 하 고, 그렇지 않으면 값을 빨간색으로 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="3313d-115">This expression, placed in a `ReportItem` text box Color property, displays the text in black when the value is > 0; otherwise, the value is displayed in red:</span></span>  
  
     `=IIF(Me.Value > 0,"Black","Red")`  
  
-   <span data-ttu-id="3313d-116">이 식을 페이지 머리글 또는 페이지 바닥글의 입력란에 배치하면 `LastName`이라는 입력란에 대해 렌더링된 보고서의 페이지별 첫 번째 값이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="3313d-116">This expression, placed in a text box in the page header or page footer, displays the first value per page of the rendered report, for a text box named `LastName`:</span></span>  
  
     `=First(ReportItems("LastName").Value)`  
  
## <a name="dictionary-style-page-header-expressions"></a><span data-ttu-id="3313d-117">사전 스타일의 페이지 머리글 식</span><span class="sxs-lookup"><span data-stu-id="3313d-117">Dictionary-Style Page Header Expressions</span></span>  
 <span data-ttu-id="3313d-118">페이지의 첫 번째 고객과 마지막 고객을 표시하는 페이지 머리글을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3313d-118">You can create a page header to display the first customer on the page and the last customer on the page.</span></span> <span data-ttu-id="3313d-119">페이지 머리글의 입력란은 식에서 `ReportItems` 기본 제공 컬렉션을 한 번만 참조할 수 있으므로 페이지 머리글에 두 개의 입력란을 추가해야 합니다. 하나는 첫 번째 고객 이름에 대한 입력란(`=First(ReportItems!textboxLastName.Value`)이고 다른 하나는 마지막 고객 이름에 대한 입력란(`=Last(ReportItems!textboxLastName.Value`)입니다.</span><span class="sxs-lookup"><span data-stu-id="3313d-119">Because a text box in the page header can only refer to the `ReportItems` built-in collection once in an expression, you need to add two text boxes to the page header: one for the first customer name (`=First(ReportItems!textboxLastName.Value`) and one for the last customer name (`=Last(ReportItems!textboxLastName.Value`).</span></span>  
  
 <span data-ttu-id="3313d-120">페이지 머리글 또는 페이지 바닥글 섹션에서는 현재 페이지의 입력란만 `ReportItems` 컬렉션의 멤버로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3313d-120">In a page header or page footer section, only text boxes on the current page are available as a member of the `ReportItems` collection.</span></span> <span data-ttu-id="3313d-121">예를 들어 `ReportItems!textboxLastName.Value` 가 다중 페이지 데이터 영역에 대한 첫 번째 페이지에만 표시되는 입력란을 참조할 경우 첫 번째 페이지에 대한 값은 볼 수 있지만 다른 모든 페이지에는 식이 작성된 대로 계산될 수 없음을 나타내는 **#오류** 가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="3313d-121">For example, if `ReportItems!textboxLastName.Value` refers to a text box that only appears on the first page for a multipage data region, you see a value for the first page, but all other pages display **#Error** to show the expression could not be evaluated as written.</span></span>  
  
## <a name="scope-for-the-reportitems-collection"></a><span data-ttu-id="3313d-122">ReportItems 컬렉션의 범위</span><span class="sxs-lookup"><span data-stu-id="3313d-122">Scope for the ReportItems Collection</span></span>  
 <span data-ttu-id="3313d-123">보고서가 처리될 때 보고서 본문 또는 데이터 영역의 각 입력란은 해당 데이터 세트, 데이터 영역 및 그룹 연결의 컨텍스트에서 계산됩니다.</span><span class="sxs-lookup"><span data-stu-id="3313d-123">As the report is processed, each text box in the report body or in a data region is evaluated in the context of its dataset, data region, and group associations.</span></span> <span data-ttu-id="3313d-124">`ReportItems` 컬렉션에 대한 참조의 범위는 현재 범위 또는 현재 범위보다 높은 모든 지점입니다.</span><span class="sxs-lookup"><span data-stu-id="3313d-124">The scope for a reference to the `ReportItems` collection is the current scope or any point higher than the current scope.</span></span>  
  
 <span data-ttu-id="3313d-125">예를 들어 부모 그룹에 있는 행의 입력란은 자식 그룹 행에 있는 입력란의 이름을 참조하는 식을 포함하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3313d-125">For example, a text box in a row that is in a parent group must not contain an expression that refers to the name of a text box in a child group row.</span></span> <span data-ttu-id="3313d-126">이러한 식은 자식 행 입력란이 범위를 벗어나기 때문에 보고서의 값으로 확인되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3313d-126">Such an expression does not resolve to a value in the report because the child row text box is out of scope.</span></span> <span data-ttu-id="3313d-127">자세한 내용은 [집계 함수 참조&#40;보고서 작성기 및 SSRS&#41;](report-builder-functions-aggregate-functions-reference.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3313d-127">For more information, see [Aggregate Functions Reference &#40;Report Builder and SSRS&#41;](report-builder-functions-aggregate-functions-reference.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3313d-128">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3313d-128">See Also</span></span>  
 <span data-ttu-id="3313d-129">[식의 기본 제공 컬렉션&#40;보고서 작성기 및 SSRS&#41;](built-in-collections-in-expressions-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="3313d-129">[Built-in Collections in Expressions &#40;Report Builder and SSRS&#41;](built-in-collections-in-expressions-report-builder.md) </span></span>  
 <span data-ttu-id="3313d-130">[식 예&#40;보고서 작성기 및 SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="3313d-130">[Expression Examples &#40;Report Builder and SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="3313d-131">[Reporting Services의 페이지 매김&#40;보고서 작성기 및 SSRS&#41;](pagination-in-reporting-services-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="3313d-131">[Pagination in Reporting Services &#40;Report Builder  and SSRS&#41;](pagination-in-reporting-services-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="3313d-132">데이터 필터링, 그룹화 및 정렬&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="3313d-132">Filter, Group, and Sort Data &#40;Report Builder and SSRS&#41;</span></span>](filter-group-and-sort-data-report-builder-and-ssrs.md)  
  
  
