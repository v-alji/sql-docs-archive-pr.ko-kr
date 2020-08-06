---
title: 행 표시 유형 대화 상자 (보고서 작성기) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10126"
ms.assetid: 117fb20c-2fda-437e-bcc5-9010d6d4b53b
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 748cf1612f04e02a90a5d8579b56d3856dea0388
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648276"
---
# <a name="row-visibility-dialog-box-report-builder"></a><span data-ttu-id="e7280-102">행 표시 유형 대화 상자(보고서 작성기)</span><span class="sxs-lookup"><span data-stu-id="e7280-102">Row Visibility Dialog Box (Report Builder)</span></span>
  <span data-ttu-id="e7280-103">**행 표시 유형** 대화 상자를 사용하면 보고서를 처음 실행할 때 선택된 행을 표시하거나 숨길 수 있고 다른 보고서 항목을 사용하여 행의 표시 유형을 전환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e7280-103">Use the **Row Visibility** dialog box to show or hide the selected row when the report is first run or to use another report item to toggle the visibility of the row.</span></span>  
  
## <a name="options"></a><span data-ttu-id="e7280-104">옵션</span><span class="sxs-lookup"><span data-stu-id="e7280-104">Options</span></span>  
 <span data-ttu-id="e7280-105">**보고서를 처음 실행할 때**</span><span class="sxs-lookup"><span data-stu-id="e7280-105">**When the report is initially run**</span></span>  
 <span data-ttu-id="e7280-106">보고서에 행이 처음 표시되는 방식을 나타내는 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e7280-106">Select an option to indicate how the row is initially displayed in the report.</span></span>  
  
 <span data-ttu-id="e7280-107">**표시**</span><span class="sxs-lookup"><span data-stu-id="e7280-107">**Show**</span></span>  
 <span data-ttu-id="e7280-108">행을 표시하려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e7280-108">Select this option to show the row.</span></span>  
  
 <span data-ttu-id="e7280-109">**숨기기**</span><span class="sxs-lookup"><span data-stu-id="e7280-109">**Hide**</span></span>  
 <span data-ttu-id="e7280-110">행을 숨기려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e7280-110">Select this option to hide the row.</span></span>  
  
 <span data-ttu-id="e7280-111">**식에 따라 표시 또는 숨기기**</span><span class="sxs-lookup"><span data-stu-id="e7280-111">**Show or hide based on an expression**</span></span>  
 <span data-ttu-id="e7280-112">식을 사용하여 초기 표시 유형을 변경하려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e7280-112">Select this option to vary the initial visibility using an expression.</span></span>  
  
 <span data-ttu-id="e7280-113">`Boolean` 값을 반환하는 식을 입력합니다. `True`는 항목을 숨기고 `False`는 항목을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="e7280-113">Type an expression that evaluates to a `Boolean` value of `True` to hide the item and `False` to show the item.</span></span> <span data-ttu-id="e7280-114">식을 편집 하려면 **식** 단추 (*fx*)를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="e7280-114">Click the **Expression** (*fx*) button to edit the expression.</span></span>  
  
 <span data-ttu-id="e7280-115">**이 보고서 항목으로 표시 또는 숨기기 가능**</span><span class="sxs-lookup"><span data-stu-id="e7280-115">**Display can be toggled by this report item**</span></span>  
 <span data-ttu-id="e7280-116">사용자가 이 행을 HTML 보고서 뷰어에 표시하거나 숨길 수 있도록 토글 이미지를 표시하려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e7280-116">Choose this option to display a toggle image that enables the user to show or hide this row in an HTML report viewer.</span></span>  
  
 <span data-ttu-id="e7280-117">보고서에서 토글 이미지를 표시할 입력란 이름(예: Textbox1)을 입력하거나 선택해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e7280-117">Type or select the name of a text box in the report in which to display a toggle image; for example, Textbox1.</span></span> <span data-ttu-id="e7280-118">선택한 입력란은 현재 보고서 항목과 동일한 범위 또는 포함 범위에 있는 입력란이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e7280-118">The text box that you choose must be in the current or containing scope for this report item.</span></span> <span data-ttu-id="e7280-119">예를 들어 자식 그룹과 연결된 행의 표시 유형을 전환하려면 부모 그룹과 연결된 행에 있는 입력란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e7280-119">For example, to toggle visibility of rows associated with a child group, select a text box in a row associated with the parent group.</span></span> <span data-ttu-id="e7280-120">차트의 표시 유형을 전환하려면 차트와 동일한 포함 범위(예: 보고서 본문 또는 사각형)에 있는 입력란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e7280-120">To toggle visibility of a chart, select a text box that is in the same containing scope as the chart; for example, the report body or a rectangle.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7280-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e7280-121">See Also</span></span>  
 <span data-ttu-id="e7280-122">[식 예&#40;보고서 작성기 및 SSRS&#41;](report-design/expression-examples-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="e7280-122">[Expression Examples &#40;Report Builder and SSRS&#41;](report-design/expression-examples-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="e7280-123">[항목 &#40;보고서 작성기 및 SSRS에 확장 또는 축소 작업을 추가&#41;](report-design/add-an-expand-or-collapse-action-to-an-item-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="e7280-123">[Add an Expand or Collapse Action to an Item &#40;Report Builder and SSRS&#41;](report-design/add-an-expand-or-collapse-action-to-an-item-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="e7280-124">[이미지 &#40;보고서 작성기 및 SSRS&#41;](report-design/images-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="e7280-124">[Images &#40;Report Builder and SSRS&#41;](report-design/images-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="e7280-125">[대화 상자, 창 및 마법사에 대 한 보고서 작성기 도움말](../../2014/reporting-services/report-builder-help-for-dialog-boxes-panes-and-wizards.md) </span><span class="sxs-lookup"><span data-stu-id="e7280-125">[Report Builder Help for Dialog Boxes, Panes, and Wizards](../../2014/reporting-services/report-builder-help-for-dialog-boxes-panes-and-wizards.md) </span></span>  
 [<span data-ttu-id="e7280-126">이미지 속성 대화 상자, 일반&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="e7280-126">Image Properties Dialog Box, General &#40;Report Builder and SSRS&#41;</span></span>](../../2014/reporting-services/image-properties-dialog-box-general-report-builder-and-ssrs.md)  
  
  
