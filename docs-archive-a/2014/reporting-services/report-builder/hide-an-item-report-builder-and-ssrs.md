---
title: 항목 숨기기(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptdesigner.shared.visibility.f1
- "10503"
ms.assetid: 9d78f8de-959b-456f-8947-687fa6e2ba91
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 56e834204698369687528c622cf6167a492766f7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648833"
---
# <a name="hide-an-item-report-builder-and-ssrs"></a><span data-ttu-id="c7eb1-102">항목 숨기기(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="c7eb1-102">Hide an Item (Report Builder and SSRS)</span></span>
  <span data-ttu-id="c7eb1-103">지정하는 보고서 매개 변수 또는 기타 식에 따라 항목을 숨기려면 보고서 항목의 표시 유형을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="c7eb1-103">Set the visibility of a report item when you want to conditionally hide an item based on a report parameter or some other expression that you specify.</span></span>

 <span data-ttu-id="c7eb1-104">드릴다운 보고서와 같은 경우 보고서에서 입력란을 클릭할 때 보고서 항목의 표시 유형이 설정/해제되도록 보고서를 디자인할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c7eb1-104">You can also design a report to allow the user to toggle the visibility of report items based on clicking text boxes in the report, for example, for a drilldown report.</span></span> <span data-ttu-id="c7eb1-105">자세한 내용은 [항목에 확장 또는 축소 동작 추가&#40;보고서 작성기 및 SSRS&#41;](../report-design/add-an-expand-or-collapse-action-to-an-item-report-builder-and-ssrs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c7eb1-105">For more information, see [Add an Expand or Collapse Action to an Item &#40;Report Builder and SSRS&#41;](../report-design/add-an-expand-or-collapse-action-to-an-item-report-builder-and-ssrs.md).</span></span>

 <span data-ttu-id="c7eb1-106">다음 절차에서는 상수 또는 식을 기반으로 보고서 항목을 렌더링된 보고서에서 표시하거나 숨기는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="c7eb1-106">The following procedures describe how to show or hide a report item in a rendered report based on a constant or an expression.</span></span>

> [!NOTE]
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]

### <a name="to-hide-a-report-item"></a><span data-ttu-id="c7eb1-107">보고서 항목을 숨기려면</span><span class="sxs-lookup"><span data-stu-id="c7eb1-107">To hide a report item</span></span>

1.  <span data-ttu-id="c7eb1-108">보고서 디자인 뷰에서 보고서 항목을 마우스 오른쪽 단추로 클릭하고 해당 **속성** 페이지를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="c7eb1-108">In report design view, right-click the report item and open its **Properties** page.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="c7eb1-109">전체 테이블 또는 행렬 데이터 영역을 선택하려면 데이터 영역을 클릭하여 선택하고 행, 열 또는 모퉁이 핸들을 마우스 오른쪽 단추로 클릭한 다음 **테이블릭스 속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c7eb1-109">To select an entire table or matrix data region, click in the data region to select it, right-click a row, column, or corner handle, and then click **Tablix Properties**.</span></span>

2.  <span data-ttu-id="c7eb1-110">**표시 유형을 클릭 합니다.**</span><span class="sxs-lookup"><span data-stu-id="c7eb1-110">Click **Visibility.**</span></span>

3.  <span data-ttu-id="c7eb1-111">**보고서를 처음 실행할 때**에서 보고서를 처음으로 볼 때 항목을 숨길지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c7eb1-111">In **When the report is initially run**, specify whether to hide the item when you first view the report:</span></span>

    -   <span data-ttu-id="c7eb1-112">항목을 표시하려면 **표시**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c7eb1-112">To display the item, click **Show**.</span></span>

    -   <span data-ttu-id="c7eb1-113">항목을 숨기려면 **숨기기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c7eb1-113">To hide the item, click **Hide**.</span></span>

    -   <span data-ttu-id="c7eb1-114">런타임에 평가되는 식을 지정하려면 **식에 따라 표시 또는 숨기기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c7eb1-114">To specify an expression that is evaluated at run-time, click **Show or hide based on an expression**.</span></span> <span data-ttu-id="c7eb1-115">**식**대화 상자에서 식을 입력하거나 식( **fx** ) 단추를 클릭하여 식을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c7eb1-115">Type the expression or click the expression (**fx**) button to create the expression in the **Expression** dialog box.</span></span>

        > [!NOTE]
        >  <span data-ttu-id="c7eb1-116">표시 유형에 대한 식을 지정할 때는 다음 이미지와 같이 보고서 항목의 Hidden 속성을 설정하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c7eb1-116">When you specify an expression for visibility, you are setting the Hidden property of the report item, as shown in the following image.</span></span> <span data-ttu-id="c7eb1-117">평가 식은 값이 False일 때 보고서 항목을 표시하고 값이 True일 때 보고서 항목을 숨깁니다.</span><span class="sxs-lookup"><span data-stu-id="c7eb1-117">The evaluated expression shows the report item when the value is False, and hides the report item when the value is True.</span></span> 
        > <span data-ttu-id="c7eb1-118">![Properties_Visibility 대화 상자 및 Hidden 속성](../media/hiddenproperty-propertiesvisibility.png "Properties_Visibility 대화 상자 및 Hidden 속성")</span><span class="sxs-lookup"><span data-stu-id="c7eb1-118">![Properties_Visibility dialog and Hidden property](../media/hiddenproperty-propertiesvisibility.png "Properties_Visibility dialog and Hidden property")</span></span>

4.  <span data-ttu-id="c7eb1-119">**확인**을 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c7eb1-119">Click **OK** twice.</span></span>

### <a name="to-hide-static-rows-in-a-table-matrix-or-list"></a><span data-ttu-id="c7eb1-120">테이블, 행렬 또는 목록에서 정적 행을 숨기려면</span><span class="sxs-lookup"><span data-stu-id="c7eb1-120">To hide static rows in a table, matrix, or list</span></span>

1.  <span data-ttu-id="c7eb1-121">보고서 디자인 뷰에서 테이블, 행렬 또는 목록을 클릭하여 행 및 열 핸들을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="c7eb1-121">In report design view, click the table, matrix, or list to display the row and column handles.</span></span>

2.  <span data-ttu-id="c7eb1-122">행 핸들을 마우스 오른쪽 단추로 클릭한 다음 **행 표시 유형**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c7eb1-122">Right-click the row handle, and then click **Row Visibility**.</span></span> <span data-ttu-id="c7eb1-123">**행 표시 유형** 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="c7eb1-123">The **Row Visibility** dialog box opens.</span></span>

3.  <span data-ttu-id="c7eb1-124">표시 유형을 설정하려면 첫 번째 절차의 3-4단계를 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="c7eb1-124">To set the visibility, follow steps 3 and 4 in the first procedure.</span></span>

### <a name="to-hide-static-columns-in-a-table-matrix-or-list"></a><span data-ttu-id="c7eb1-125">테이블, 행렬 또는 목록에서 정적 열을 숨기려면</span><span class="sxs-lookup"><span data-stu-id="c7eb1-125">To hide static columns in a table, matrix, or list</span></span>

1.  <span data-ttu-id="c7eb1-126">디자인 뷰에서 테이블, 행렬 또는 목록을 선택하여 행 및 열 핸들을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="c7eb1-126">In Design view, select the table, matrix, or list to display the row and column handles.</span></span>

2.  <span data-ttu-id="c7eb1-127">열 핸들을 마우스 오른쪽 단추로 클릭한 다음 **열 표시 유형**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c7eb1-127">Right-click the column handle, and then click **Column Visibility**.</span></span>

3.  <span data-ttu-id="c7eb1-128">**열 표시 유형** 대화 상자에서 첫 번째 절차의 3-4단계를 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="c7eb1-128">In the **Column Visibility** dialog box, follow steps 3 and 4 in the first procedure.</span></span>

## <a name="see-also"></a><span data-ttu-id="c7eb1-129">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c7eb1-129">See Also</span></span>
 <span data-ttu-id="c7eb1-130">[드릴 다운 동작 &#40;보고서 작성기 및 ssrs&#41;](../report-design/drilldown-action-report-builder-and-ssrs.md) [항목에 확장 또는 축소 동작을 추가 &#40;보고서 작성기 및 Ssrs&#41;](../report-design/add-an-expand-or-collapse-action-to-an-item-report-builder-and-ssrs.md) [식 예제 &#40;보고서 작성기 및 ssrs](../report-design/expression-examples-report-builder-and-ssrs.md)&#41;</span><span class="sxs-lookup"><span data-stu-id="c7eb1-130">[Drilldown Action &#40;Report Builder and SSRS&#41;](../report-design/drilldown-action-report-builder-and-ssrs.md) [Add an Expand or Collapse Action to an Item &#40;Report Builder and SSRS&#41;](../report-design/add-an-expand-or-collapse-action-to-an-item-report-builder-and-ssrs.md) [Expression Examples &#40;Report Builder and SSRS&#41;](../report-design/expression-examples-report-builder-and-ssrs.md)</span></span>


