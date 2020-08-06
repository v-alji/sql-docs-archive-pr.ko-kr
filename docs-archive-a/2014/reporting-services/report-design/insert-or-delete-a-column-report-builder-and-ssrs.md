---
title: 열 삽입 또는 삭제(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: e9db79e2-7e7d-4359-a706-cb746c94182a
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 9a6f782dbb6cc1024583926aafe4bab1cfe2d042
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739303"
---
# <a name="insert-or-delete-a-column-report-builder-and-ssrs"></a><span data-ttu-id="fc7c3-102">열 삽입 또는 삭제(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="fc7c3-102">Insert or Delete a Column (Report Builder and SSRS)</span></span>
  <span data-ttu-id="fc7c3-103">테이블릭스 데이터 영역의 열을 추가하거나 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fc7c3-103">You can add or delete columns in a tablix data region.</span></span> <span data-ttu-id="fc7c3-104">테이블릭스 데이터 영역은 테이블, 행렬 또는 목록일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fc7c3-104">The tablix data region can be a table, a matrix, or a list.</span></span> <span data-ttu-id="fc7c3-105">차트 및 계기 데이터 영역에는 다음 절차가 적용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="fc7c3-105">The following procedures do not apply to the chart and gauge data regions.</span></span>  
  
 <span data-ttu-id="fc7c3-106">테이블릭스 데이터 영역에서는 그룹과 연결되어 있는 열(그룹 내부의 열)이나 연결되지 않은 열(그룹 외부의 열)을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fc7c3-106">In a tablix data region, you can add columns that are associated with a group (inside a group) or that are not associated with a group (outside a group).</span></span> <span data-ttu-id="fc7c3-107">그룹 내부의 열은 고유 그룹 값마다 한 번씩 반복됩니다.</span><span class="sxs-lookup"><span data-stu-id="fc7c3-107">A column that is inside a group repeats once per unique group value.</span></span> <span data-ttu-id="fc7c3-108">예를 들어 색 이름이 들어 있는 데이터 열의 값을 기반으로 하는 그룹 내부의 열은 고유한 색 이름마다 한 번씩 반복됩니다.</span><span class="sxs-lookup"><span data-stu-id="fc7c3-108">For example, a column inside a group based the value in a data column that contains color names, repeats once per distinct color name.</span></span> <span data-ttu-id="fc7c3-109">중첩된 그룹의 경우 열은 자식 그룹의 외부에 있으면서 부모 그룹의 내부에 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fc7c3-109">For nested groups, a column can be outside the child group but inside the parent group.</span></span> <span data-ttu-id="fc7c3-110">이 경우 행은 부모 그룹의 각 고유 값에 대해 한 번씩 반복됩니다.</span><span class="sxs-lookup"><span data-stu-id="fc7c3-110">In this case, the row repeats once for each unique value in the parent group.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-select-a-data-region-so-that-the-row-and-column-handles-appear"></a><span data-ttu-id="fc7c3-111">데이터 영역을 선택하여 행 및 열 핸들을 표시하려면</span><span class="sxs-lookup"><span data-stu-id="fc7c3-111">To select a data region so that the row and column handles appear</span></span>  
  
-   <span data-ttu-id="fc7c3-112">디자인 뷰에서 테이블릭스 데이터 영역의 왼쪽 위 모퉁이를 클릭하여 해당 데이터 영역의 위쪽과 옆쪽에 열 및 행 핸들을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="fc7c3-112">In Design view, click the upper left corner of the tablix data region, so that column and row handles appear above and next to it.</span></span>  
  
     <span data-ttu-id="fc7c3-113">데이터 영역 영역에 대 한 자세한 내용은 [목록 &#40;보고서 작성기 및 SSRS&#41;](tables-matrices-and-lists-report-builder-and-ssrs.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="fc7c3-113">For more information about data region areas, see [Lists &#40;Report Builder and SSRS&#41;](tables-matrices-and-lists-report-builder-and-ssrs.md).</span></span>  
  
### <a name="to-insert-a-column-in-a-selected-data-region"></a><span data-ttu-id="fc7c3-114">선택한 데이터 영역에 열을 삽입하려면</span><span class="sxs-lookup"><span data-stu-id="fc7c3-114">To insert a column in a selected data region</span></span>  
  
-   <span data-ttu-id="fc7c3-115">열을 삽입할 위치의 열 핸들을 마우스 오른쪽 단추로 클릭하고 **열 삽입**을 클릭한 다음 **왼쪽** 또는 **오른쪽**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="fc7c3-115">Right-click a column handle where you want to insert a column, click **Insert Column**, and then click **Left** or **Right**.</span></span>  
  
     <span data-ttu-id="fc7c3-116">-- 또는 --</span><span class="sxs-lookup"><span data-stu-id="fc7c3-116">-- or --</span></span>  
  
-   <span data-ttu-id="fc7c3-117">데이터 영역에서 열을 삽입할 위치의 셀을 마우스 오른쪽 단추로 클릭하고 **열 삽입**을 클릭한 다음 **왼쪽** 또는 **오른쪽**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="fc7c3-117">Right-click a cell in the data region where you want to insert a row, click **Insert Column**, and then click **Left** or **Right**.</span></span>  
  
### <a name="to-delete-a-column-from-a-selected-data-region"></a><span data-ttu-id="fc7c3-118">선택한 데이터 영역에서 열을 삭제하려면</span><span class="sxs-lookup"><span data-stu-id="fc7c3-118">To delete a column from a selected data region</span></span>  
  
-   <span data-ttu-id="fc7c3-119">삭제할 열을 하나 이상 선택하고 그중 하나의 핸들을 마우스 오른쪽 단추로 클릭한 다음 **열 삭제**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="fc7c3-119">Select the column or columns that you want to delete, right-click the handle for one of the columns you selected, and then click **Delete Columns**.</span></span>  
  
     <span data-ttu-id="fc7c3-120">-- 또는 --</span><span class="sxs-lookup"><span data-stu-id="fc7c3-120">-- or --</span></span>  
  
-   <span data-ttu-id="fc7c3-121">데이터 영역에서 열을 삭제할 위치의 셀을 마우스 오른쪽 단추로 클릭한 다음 **열 삭제**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="fc7c3-121">Right-click a cell in the data region where you want to delete a column, and then click **Delete Columns**.</span></span>  
  
### <a name="to-insert-a-column-in-a-group-in-a-selected-data-region"></a><span data-ttu-id="fc7c3-122">선택한 데이터 영역의 그룹에 열을 삽입하려면</span><span class="sxs-lookup"><span data-stu-id="fc7c3-122">To insert a column in a group in a selected data region</span></span>  
  
-   <span data-ttu-id="fc7c3-123">테이블릭스 데이터 영역의 열 그룹 영역에서 열을 삽입할 위치의 열 그룹 셀을 마우스 오른쪽 단추로 클릭하고 **열 삽입**을 클릭한 다음 **왼쪽 - 외부 그룹**, **왼쪽 - 내부 그룹**, **오른쪽 - 내부 그룹**또는 **오른쪽 - 외부 그룹**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="fc7c3-123">Right-click a column group cell in the column group area of a tablix data region where you want to insert a column, click **Insert Column**, and then click **Left - Outside Group**, **Left - Inside Group**, **Right - Inside Group**, or **Right - Outside Group**.</span></span>  
  
     <span data-ttu-id="fc7c3-124">클릭한 열 그룹 셀이 나타내는 그룹의 내부나 외부에 열이 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="fc7c3-124">A column is added either inside or outside the group represented by the column group cell you clicked on.</span></span>  
  
### <a name="to-delete-a-column-from-a-group-in-a-selected-data-region"></a><span data-ttu-id="fc7c3-125">선택한 데이터 영역의 그룹에서 열을 삭제하려면</span><span class="sxs-lookup"><span data-stu-id="fc7c3-125">To delete a column from a group in a selected data region</span></span>  
  
-   <span data-ttu-id="fc7c3-126">테이블릭스 데이터 영역의 열 그룹 영역에서 열을 삭제할 위치의 열 그룹 셀을 마우스 오른쪽 단추로 클릭한 다음 **열 삭제**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="fc7c3-126">Right-click a column group cell in the column group area of a tablix data region where you want to delete a column, and then click **Delete Columns**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc7c3-127">참고 항목</span><span class="sxs-lookup"><span data-stu-id="fc7c3-127">See Also</span></span>  
 <span data-ttu-id="fc7c3-128">[그룹 이해&#40;보고서 작성기 및 SSRS&#41;](understanding-groups-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="fc7c3-128">[Understanding Groups &#40;Report Builder and SSRS&#41;](understanding-groups-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="fc7c3-129">[테이블릭스 데이터 영역&#40;보고서 작성기 및 SSRS&#41;](../tablix-data-region-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="fc7c3-129">[Tablix Data Region &#40;Report Builder and SSRS&#41;](../tablix-data-region-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="fc7c3-130">[테이블&#40;보고서 작성기 및 SSRS&#41;](tables-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="fc7c3-130">[Tables &#40;Report Builder  and SSRS&#41;](tables-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="fc7c3-131">[행렬&#40;보고서 작성기 및 SSRS&#41;](create-a-matrix-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="fc7c3-131">[Matrices &#40;Report Builder and SSRS&#41;](create-a-matrix-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="fc7c3-132">[목록&#40;보고서 작성기 및 SSRS&#41;](create-invoices-and-forms-with-lists-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="fc7c3-132">[Lists &#40;Report Builder and SSRS&#41;](create-invoices-and-forms-with-lists-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="fc7c3-133">목록&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="fc7c3-133">Lists &#40;Report Builder and SSRS&#41;</span></span>](tables-matrices-and-lists-report-builder-and-ssrs.md)  
  
  
