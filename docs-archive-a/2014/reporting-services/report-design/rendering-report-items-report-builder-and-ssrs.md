---
title: 보고서 항목 렌더링(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 99ebb4dc-41cc-42ac-82dd-a2b0e31155a0
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f4e0b1dabee096cfbaab53227926633f8d7a3697
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650727"
---
# <a name="rendering-report-items-report-builder-and-ssrs"></a><span data-ttu-id="3865d-102">보고서 항목 렌더링(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="3865d-102">Rendering Report Items (Report Builder and SSRS)</span></span>
  <span data-ttu-id="3865d-103">보고서 항목의 숫자, 크기 및 위치는 렌더러에서 보고서 본문에 페이지를 매기는 방식에 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="3865d-103">The number, size, and location of report items affect how the renderers paginate the report body.</span></span> <span data-ttu-id="3865d-104">아래에는 다양한 보고서 항목이 렌더링되는 방식에 대해 설명되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3865d-104">Below is a description of how various report items are rendered.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="overlapping-report-items"></a><span data-ttu-id="3865d-105">겹치는 보고서 항목</span><span class="sxs-lookup"><span data-stu-id="3865d-105">Overlapping Report Items</span></span>  
 <span data-ttu-id="3865d-106">겹치는 보고서 항목은 HTML, MHTML, Word, Excel에서 미리 보기로 지원되지 않으며 보고서 뷰어에서도 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3865d-106">Overlapping report items are not supported in HTML, MHTML, Word, Excel, in Preview, or the Report Viewer.</span></span> <span data-ttu-id="3865d-107">겹치는 항목이 있는 경우 해당 항목은 이동됩니다.</span><span class="sxs-lookup"><span data-stu-id="3865d-107">If overlapping items exist, they are moved.</span></span> <span data-ttu-id="3865d-108">겹치는 보고서 항목에는 다음과 같은 규칙이 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="3865d-108">The following rules are applied to overlapping report items:</span></span>  
  
-   <span data-ttu-id="3865d-109">보고서 항목 간에 세로로 겹치는 부분이 더 많은 경우 겹치는 항목 중 하나가 오른쪽으로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="3865d-109">If the vertical overlap of report items is greater, one of the overlapping items is moved to the right.</span></span> <span data-ttu-id="3865d-110">가장 왼쪽에 있는 항목은 원래 위치에 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="3865d-110">The left-most item remains where it is positioned.</span></span>  
  
-   <span data-ttu-id="3865d-111">보고서 항목 간에 가로로 겹치는 부분이 더 많은 경우 겹치는 항목 중 하나가 아래쪽으로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="3865d-111">If the horizontal overlap of report items is greater, one of the overlapping items is moved down.</span></span> <span data-ttu-id="3865d-112">가장 위쪽에 있는 항목은 원래 위치에 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="3865d-112">The top-most item remains where it is positioned.</span></span>  
  
-   <span data-ttu-id="3865d-113">보고서 항목 간에 세로로 겹치는 부분과 가로로 겹치는 부분의 크기가 동일한 경우 겹치는 항목 중 하나가 오른쪽으로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="3865d-113">If the vertical and horizontal overlap is equal, one of the overlapping items is moved to the right.</span></span> <span data-ttu-id="3865d-114">가장 왼쪽에 있는 항목은 원래 위치에 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="3865d-114">The left-most item remains where it is positioned.</span></span>  
  
-   <span data-ttu-id="3865d-115">겹치지 않도록 하기 위해 항목을 이동해야 하는 경우 해당 항목 위쪽 및/또는 왼쪽에 있는 인접 보고서 항목과 해당 항목 간의 간격이 최소로 유지되도록 인접 보고서 항목이 아래쪽 및/또는 오른쪽으로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="3865d-115">If an item must be moved to correct overlapping, adjacent report items move down and/or to the right to maintain a minimum amount of spacing between the item and the report items that end above it and/or to the left of it.</span></span> <span data-ttu-id="3865d-116">예를 들어 세로로 겹치는 두 보고서 항목이 있고 이들 항목으로부터 오른쪽으로 2인치 떨어진 곳에 세 번째 보고서 항목이 있는 경우를 가정해 봅니다.</span><span class="sxs-lookup"><span data-stu-id="3865d-116">For example, suppose two report items overlap vertically and a third report item is 2 inches to the right of them.</span></span> <span data-ttu-id="3865d-117">겹치는 보고서 항목이 오른쪽으로 이동하면 세 번째 보고서 항목도 오른쪽으로 이동하여 해당 항목과 해당 항목의 왼쪽에 있는 항목 간의 간격이 2인치로 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="3865d-117">When the overlapping report item is moved to the right, the third report item moves to the right as well in order to maintain the 2 inches between itself and the report item to its left.</span></span>  
  
 <span data-ttu-id="3865d-118">겹치는 보고서 항목은 인쇄를 비롯한 하드 페이지 나누기 형식에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="3865d-118">Overlapping report items are supported in hard page-break formats, including print.</span></span>  
  
## <a name="visibility-and-report-items"></a><span data-ttu-id="3865d-119">표시 유형 및 보고서 항목</span><span class="sxs-lookup"><span data-stu-id="3865d-119">Visibility and Report Items</span></span>  
 <span data-ttu-id="3865d-120">보고서 항목이 기본적으로 숨겨지거나 표시되도록 할 수 있으며 식을 사용하는 경우 조건부로 숨겨지거나 표시되도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3865d-120">Report items can be hidden or displayed by default, or hidden or displayed conditionally using expressions.</span></span> <span data-ttu-id="3865d-121">또는 다른 보고서 항목을 클릭하여 표시 유형을 전환할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3865d-121">Optionally, the visibility can be switched by clicking another report item.</span></span>  
  
 <span data-ttu-id="3865d-122">보고서 항목을 렌더링하는 경우 다음과 같은 표시 유형 규칙이 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="3865d-122">The following visibility rules apply when rendering report items:</span></span>  
  
-   <span data-ttu-id="3865d-123">보고서 항목과 해당 내용이 항상  숨겨져 있는 경우, 즉 식에 의해 숨겨진 경우 또는 다른 보고서 항목을 클릭하여 표시 유형을 전환할 수 있는 경우가 아닐 때, 해당 항목의 오른쪽 또는 아래쪽에 있는 다른 보고서 항목은 이러한 빈 공간을 채우기 위해 이동하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3865d-123">If a report item and its contents are always hidden (it is not hidden based on an expression or its visibility cannot be switched by clicking another report item), then other report items to the right or below it do not move to fill the empty space.</span></span> <span data-ttu-id="3865d-124">예를 들어 사각형 및 사각형에 포함된 이미지가 숨겨져 있는 경우 사각형 오른쪽에서 시작되는 보고서 항목이 왼쪽으로 이동하여 빈 공간을 채우지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3865d-124">For example, if a rectangle and the image contained within it are hidden, the report item that starts to the right of the rectangle does not move to the left to fill what appears to be empty space.</span></span> <span data-ttu-id="3865d-125">사각형이 차지하는 공간은 그대로 보존됩니다.</span><span class="sxs-lookup"><span data-stu-id="3865d-125">The space occupied by the rectangle is preserved.</span></span>  
  
-   <span data-ttu-id="3865d-126">보고서 항목과 해당 내용이 조건부로 숨겨져 있는 경우, 즉 식에 의해 조건부로 숨겨진 경우 또는 다른 보고서 항목을 클릭하여 표시 유형을 전환할 수 있는 경우, 항목이 숨겨지면 해당 항목의 오른쪽 또는 아래쪽에 있는 다른 보고서 항목이 왼쪽으로 이동하여 공간을 채웁니다.</span><span class="sxs-lookup"><span data-stu-id="3865d-126">If a report item and its contents are hidden conditionally (it is hidden based on an expression or its visibility is switched by clicking another report item), then report items to the right or below it move to the left to fill in the space when the item is hidden.</span></span>  
  
-   <span data-ttu-id="3865d-127">다른 보고서 항목을 클릭하여 보고서 항목 및 해당 내용의 표시 유형을 전환할 수 있는 경우 보고서 항목이 처음 표시될 때만 해당 보고서 항목과 내용을 포함하도록 페이지 매김이 변경됩니다.</span><span class="sxs-lookup"><span data-stu-id="3865d-127">If the visibility of a report item and its contents can be switched by clicking another report item, then pagination changes to accommodate the report item and its contents only when it is initially displayed.</span></span>  
  
## <a name="keeping-report-items-together-on-a-single-page"></a><span data-ttu-id="3865d-128">여러 보고서 항목을 단일 페이지에 함께 유지</span><span class="sxs-lookup"><span data-stu-id="3865d-128">Keeping Report Items Together on a Single Page</span></span>  
 <span data-ttu-id="3865d-129">그룹으로 유지 또는 함께 연결 속성을 설정하여 보고서 내의 여러 보고서 항목을 암시적 또는 명시적으로 단일 페이지에 유지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3865d-129">Many report items within a report can be kept together on a single page implicitly or explicitly by setting the keep with group or keep together properties.</span></span> <span data-ttu-id="3865d-130">보고서 항목에 논리적 페이지 나누기가 없고 사용 가능한 페이지 영역보다 보고서 항목이 작은 경우 해당 보고서 항목은 항상 동일한 페이지에 렌더링됩니다.</span><span class="sxs-lookup"><span data-stu-id="3865d-130">Report items are always rendered on the same page if the report item does not have any logical page breaks and is smaller in size than the usable page area.</span></span> <span data-ttu-id="3865d-131">보고서 항목이 시작되는 페이지 안에 보고서 항목의 모든 부분이 포함되지 않는 경우 해당 보고서 항목 앞에 하드 페이지 나누기가 삽입되어 해당 보고서 항목이 다음 페이지에서 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="3865d-131">If a report item does not fit completely on the page on which it would usually start, a hard page break is inserted before the report item, forcing it to the next page.</span></span> <span data-ttu-id="3865d-132">소프트 페이지 나누기 렌더러의 경우 보고서 항목이 포함되도록 페이지 크기가 증가합니다.</span><span class="sxs-lookup"><span data-stu-id="3865d-132">For soft page-break renderers, the page grows to accommodate the report item.</span></span>  
  
 <span data-ttu-id="3865d-133">보고서 항목이 항상 숨겨져 있으면 여러 항목을 같은 페이지에 유지하는 규칙이 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="3865d-133">When the report item is always hidden, the rules for keeping items together are ignored.</span></span>  
  
 <span data-ttu-id="3865d-134">다음과 같은 항목은 항상 같은 페이지에 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="3865d-134">The following items are always kept together:</span></span>  
  
-   <span data-ttu-id="3865d-135">이미지</span><span class="sxs-lookup"><span data-stu-id="3865d-135">Images.</span></span>  
  
-   <span data-ttu-id="3865d-136">선.</span><span class="sxs-lookup"><span data-stu-id="3865d-136">Lines.</span></span>  
  
-   <span data-ttu-id="3865d-137">차트, 계기 및 지도</span><span class="sxs-lookup"><span data-stu-id="3865d-137">Charts, gauges, and maps.</span></span>  
  
-   <span data-ttu-id="3865d-138">그룹으로 유지 옵션을 선택하여 다른 페이지에 별도로 표시되는 데이터 영역의 단일 행.</span><span class="sxs-lookup"><span data-stu-id="3865d-138">A single row in a data region that appears separately on another page, by selecting the keep with group option.</span></span> <span data-ttu-id="3865d-139">이 옵션을 선택하면 별도로 설정하지 않아도 하나 이상의 그룹 인스턴스와 함께 단일 행이 함께 연결되므로 해당 행이 분리되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3865d-139">This will implicitly keep together the single row with at least one instance of the group so that the row is not orphaned.</span></span> <span data-ttu-id="3865d-140">이 옵션은 데이터 영역 또는 그룹에 대해 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3865d-140">You can set this option on a data region or a group.</span></span>  
  
-   <span data-ttu-id="3865d-141">데이터 영역의 머리글 영역</span><span class="sxs-lookup"><span data-stu-id="3865d-141">Header area of a data region.</span></span>  
  
-   <span data-ttu-id="3865d-142">데이터 영역 및 첫 번째 데이터 행의 머리글 영역</span><span class="sxs-lookup"><span data-stu-id="3865d-142">Header area of a data region and the first row of data.</span></span>  
  
-   <span data-ttu-id="3865d-143">테이블릭스 데이터 영역에서 표시 유형을 전환할 수 있는 보고서 항목</span><span class="sxs-lookup"><span data-stu-id="3865d-143">Report items that can be toggled in a tablix data region.</span></span>  
  
### <a name="priority-order"></a><span data-ttu-id="3865d-144">우선 순위 순서</span><span class="sxs-lookup"><span data-stu-id="3865d-144">Priority Order</span></span>  
 <span data-ttu-id="3865d-145">페이지 크기 제한으로 인해 여러 보고서 항목을 같은 페이지에 유지하려는 규칙 간에 충돌이 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3865d-145">Due to page size limitations, conflicts can arise between the rules for keeping report items together.</span></span> <span data-ttu-id="3865d-146">충돌이 발생하는 경우 다음과 같은 우선 순위 순서를 사용하여 렌더링되는 여러 항목을 같은 페이지에 유지합니다.</span><span class="sxs-lookup"><span data-stu-id="3865d-146">When conflicts occur, the following priority order is used to keep items together when rendering:</span></span>  
  
-   <span data-ttu-id="3865d-147">선, 차트 및 이미지</span><span class="sxs-lookup"><span data-stu-id="3865d-147">Lines, charts, and images.</span></span>  
  
-   <span data-ttu-id="3865d-148">창 및 분리된 컨트롤</span><span class="sxs-lookup"><span data-stu-id="3865d-148">Widow and orphan control.</span></span>  
  
-   <span data-ttu-id="3865d-149">반복되는 열 머리글 및 행 머리글</span><span class="sxs-lookup"><span data-stu-id="3865d-149">Repeated column headers and row headers.</span></span>  
  
     <span data-ttu-id="3865d-150">머리글이 바닥글보다 우선 순위가 높습니다.</span><span class="sxs-lookup"><span data-stu-id="3865d-150">Headers take precedence over footers.</span></span> <span data-ttu-id="3865d-151">반복되는 내부 그룹이 외부 그룹보다 우선 순위가 높습니다.</span><span class="sxs-lookup"><span data-stu-id="3865d-151">Inner repeated groups have priority over outer groups.</span></span> <span data-ttu-id="3865d-152">`RepeatWith` 속성이 설정되어 있고 대상 데이터 영역에 보다 가까이 있는 항목이 데이터 영역에서 멀리 떨어져 있는 항목보다 우선 순위가 높습니다.</span><span class="sxs-lookup"><span data-stu-id="3865d-152">Items where the `RepeatWith` property is set that are closer to the target data region have priority over items that are farther away from the data region.</span></span>  
  
-   <span data-ttu-id="3865d-153">명시적 KeepTogether 속성이로 설정 된 입력란 또는 사각형 등의 작은 보고서 항목 `true`</span><span class="sxs-lookup"><span data-stu-id="3865d-153">Small report items, such as text boxes or rectangles, with an explicit KeepTogether property set to `true`.</span></span>  
  
-   <span data-ttu-id="3865d-154">명시적 KeepTogether 속성이로 설정 된 하위 보고서 또는 가장 안쪽에 있지 않은 테이블 릭 스 멤버 등의 많은 보고서 항목 `true`</span><span class="sxs-lookup"><span data-stu-id="3865d-154">Large report items, such as subreports or a non-innermost tablix member, with an explicit KeepTogether property set to `true`.</span></span>  
  
-   <span data-ttu-id="3865d-155">명시적 KeepTogether 속성이로 설정 된 테이블 릭 스 데이터 영역 `true`</span><span class="sxs-lookup"><span data-stu-id="3865d-155">Tablix data regions with an explicit KeepTogether property set to `true`.</span></span>  
  
### <a name="subreports"></a><span data-ttu-id="3865d-156">하위 보고서</span><span class="sxs-lookup"><span data-stu-id="3865d-156">Subreports</span></span>  
 <span data-ttu-id="3865d-157">하위 보고서는 별도의 보고서 .rdl 파일에 정의된 다른 보고서를 포함하는 사각형으로 렌더링됩니다.</span><span class="sxs-lookup"><span data-stu-id="3865d-157">A subreport renders as a rectangle that contains another report that is defined in a separate report .rdl file.</span></span> <span data-ttu-id="3865d-158">하위 보고서 파일을 부모 보고서에서 액세스할 수 있도록 하려면 먼저 해당 파일을 보고서 서버에 게시해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3865d-158">The subreport file must be published to a report server before it can be accessed by the parent report.</span></span>  
  
 <span data-ttu-id="3865d-159">하위 보고서를 렌더링하는 경우 다음과 같은 규칙이 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="3865d-159">The following rules apply when rendering subreports:</span></span>  
  
-   <span data-ttu-id="3865d-160">하위 보고서의 크기는 해당 보고서를 정의하는 .rdl 파일에 정의된 본문 크기에 맞춰 늘어날 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3865d-160">Subreports can grow to the size of the body defined in the .rdl file that defines the subreport.</span></span> <span data-ttu-id="3865d-161">예를 들어 하위 보고서에 대한 RDL에 보고서 본문의 너비가 5인치로 지정되어 있는 경우 부모 보고서 내에서 하위 보고서의 너비는 5인치가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3865d-161">For example, if the RDL for the subreport states that the subreport body is 5 inches wide, then the subreport will be 5 inches wide within the parent report.</span></span>  
  
-   <span data-ttu-id="3865d-162">하위 보고서는 부모 보고서의 열 설정을 상속합니다.</span><span class="sxs-lookup"><span data-stu-id="3865d-162">Subreports inherit column settings from the parent report.</span></span> <span data-ttu-id="3865d-163">원본 RDL에 정의된 열 설정은 항상 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="3865d-163">Column settings that are defined in the original RDL are always ignored.</span></span>  
  
-   <span data-ttu-id="3865d-164">하위 보고서의 본문만 렌더링됩니다.</span><span class="sxs-lookup"><span data-stu-id="3865d-164">Only the body of the subreport is rendered.</span></span> <span data-ttu-id="3865d-165">하위 보고서가 렌더링되는 경우 하위 보고서의 .rdl 파일에 정의된 머리글 및 바닥글 섹션은 부모 보고서에서 렌더링되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3865d-165">Header and footer sections that are defined in the subreport's .rdl file are not rendered when the subreport is rendered in the parent report.</span></span>  
  
-   <span data-ttu-id="3865d-166">하위 보고서에는 명시적인 KeepTogether 속성이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3865d-166">Subreports have an explicit KeepTogether property.</span></span> <span data-ttu-id="3865d-167">이 속성이 `true`로 설정된 경우 하위 보고서의 모든 항목은 가능한 경우 한 페이지에 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="3865d-167">When it is set to `true`, all the items in the subreport are kept together on one page when possible.</span></span>  
  
-   <span data-ttu-id="3865d-168">하위 보고서를 실행할 수 없는 경우 하위 보고서는 보고서에서 입력란으로 나타나며 이 입력란 안에 오류 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="3865d-168">If a subreport cannot run, it is displayed in the report as a text box with an error message.</span></span> <span data-ttu-id="3865d-169">하위 보고서에 적용되는 스타일 속성은 하위 보고서 대신 이 입력란에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="3865d-169">The style properties applied to the subreport are applied to the text box instead.</span></span>  
  
-   <span data-ttu-id="3865d-170">하위 보고서가 페이지 나누기로 인해 분할된 경우 **페이지 나누기에 테두리 생략** 설정을 통해 하위 보고서의 테두리가 닫히거나 열리도록 제어됩니다.</span><span class="sxs-lookup"><span data-stu-id="3865d-170">If the subreport is split by a page break, the **Omit border on page break** setting controls whether or not the borders on the subreport are closed or open.</span></span>  
  
 <span data-ttu-id="3865d-171">하위 보고서에 대한 자세한 내용은 [하위 보고서&#40;보고서 작성기 및 SSRS&#41;](subreports-report-builder-and-ssrs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3865d-171">For more information about subreports, see [Subreports &#40;Report Builder and SSRS&#41;](subreports-report-builder-and-ssrs.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3865d-172">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3865d-172">See Also</span></span>  
 <span data-ttu-id="3865d-173">[Reporting Services의 페이지 매김&#40;보고서 작성기 및 SSRS&#41;](pagination-in-reporting-services-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="3865d-173">[Pagination in Reporting Services &#40;Report Builder  and SSRS&#41;](pagination-in-reporting-services-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="3865d-174">[렌더링 동작&#40;보고서 작성기 및 SSRS&#41;](rendering-behaviors-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="3865d-174">[Rendering Behaviors &#40;Report Builder  and SSRS&#41;](rendering-behaviors-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="3865d-175">[여러 보고서 렌더링 확장 프로그램의 대화형 기능&#40;보고서 작성기 및 SSRS&#41;](../report-builder/interactive-functionality-different-report-rendering-extensions.md) </span><span class="sxs-lookup"><span data-stu-id="3865d-175">[Interactive Functionality for Different Report Rendering Extensions &#40;Report Builder and SSRS&#41;](../report-builder/interactive-functionality-different-report-rendering-extensions.md) </span></span>  
 [<span data-ttu-id="3865d-176">목록&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="3865d-176">Lists &#40;Report Builder and SSRS&#41;</span></span>](tables-matrices-and-lists-report-builder-and-ssrs.md)  
  
  
