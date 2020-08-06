---
title: 그룹 또는 테이블릭스 데이터 영역에 합계 추가(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: cf1b96c3-7f0f-4c94-ad08-5239c77ccfe4
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f626621a37a327ae32664ab9444e72ce4931ac0e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639299"
---
# <a name="add-a-total-to-a-group-or-tablix-data-region-report-builder-and-ssrs"></a><span data-ttu-id="2c55e-102">그룹 또는 테이블릭스 데이터 영역에 합계 추가(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="2c55e-102">Add a Total to a Group or Tablix Data Region (Report Builder and SSRS)</span></span>
  <span data-ttu-id="2c55e-103">그룹 또는 전체 데이터 영역에 대한 테이블릭스 데이터 영역에 합계를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2c55e-103">You can add totals in a tablix data region for a group or for the entire data region.</span></span> <span data-ttu-id="2c55e-104">기본적으로 합계는 필터가 적용된 후 그룹 또는 데이터 영역의 Null이 아닌 숫자 데이터의 합계입니다.</span><span class="sxs-lookup"><span data-stu-id="2c55e-104">By default, a total is the sum of the numeric, non-null data in a group or in the data region, after filters are applied.</span></span> <span data-ttu-id="2c55e-105">그룹에 대한 합계를 추가하려면 그룹화 창의 그룹에 대한 바로 가기 메뉴에서 **합계 추가** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2c55e-105">To add totals for a group, click **Add Total** on the shortcut menu for the group in the Grouping pane.</span></span> <span data-ttu-id="2c55e-106">테이블릭스 본문 영역에서 개별 셀에 대한 합계를 추가하려면 셀에 대한 바로 가기 메뉴에서 **합계 추가** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2c55e-106">To add totals for an individual cell in the tablix body area, click **Add Total** on the shortcut menu for the cell.</span></span> <span data-ttu-id="2c55e-107">**합계 추가** 명령은 상황에 맞게 작동하며 숫자 필드에 대해서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2c55e-107">The **Add Total** command is context-sensitive and enabled only for numeric fields.</span></span> <span data-ttu-id="2c55e-108">선택한 테이블릭스 셀에 따라 테이블릭스 본문 영역에서 셀을 선택하여 단일 셀에 대한 합계를 추가하거나 테이블릭스 행 그룹 영역 또는 열 그룹 영역에서 셀을 선택하여 전체 그룹에 대한 합계를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2c55e-108">Depending on the tablix cell that you select, you can add a total for a single cell by selecting a cell in the tablix body area or for the entire group by selecting a cell in the tablix row group area or the tablix column group area.</span></span> <span data-ttu-id="2c55e-109">테이블릭스 영역에 대한 자세한 내용은 [테이블릭스 데이터 영역&#40;보고서 작성기 및 SSRS&#41;](../tablix-data-region-report-builder-and-ssrs.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2c55e-109">For more information about tablix areas, see [Tablix Data Region &#40;Report Builder and SSRS&#41;](../tablix-data-region-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="2c55e-110">합계를 추가한 후에는 기본 함수 Sum을 기본 제공 보고서 함수 목록의 다른 집계 함수로 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2c55e-110">After you add a total, you can change the default function Sum to a different aggregate function from the list of built-in report functions.</span></span> <span data-ttu-id="2c55e-111">자세한 내용은 [집계 함수 참조 &#40;보고서 작성기 및 SSRS&#41;](report-builder-functions-aggregate-functions-reference.md)를 참조 하세요.[!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2c55e-111">For more information, see [Aggregate Functions Reference &#40;Report Builder and SSRS&#41;](report-builder-functions-aggregate-functions-reference.md).[!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]</span></span>  
  
### <a name="to-add-a-total-for-an-individual-value-in-the-tablix-body-area"></a><span data-ttu-id="2c55e-112">테이블릭스 본문 영역의 개별 값에 대한 합계를 추가하려면</span><span class="sxs-lookup"><span data-stu-id="2c55e-112">To add a total for an individual value in the tablix body area</span></span>  
  
-   <span data-ttu-id="2c55e-113">테이블릭스 데이터 영역 본문 영역에서 합계를 추가할 셀을 마우스 오른쪽 단추로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2c55e-113">In the tablix data region body area, right-click the cell where you want to add the total.</span></span> <span data-ttu-id="2c55e-114">셀은 숫자 필드를 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2c55e-114">The cell must contain a numeric field.</span></span> <span data-ttu-id="2c55e-115">**합계 추가**를 가리킨 다음 **행** 또는 **열**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2c55e-115">Point to **Add Total**, and then click **Row** or **Column**.</span></span>  
  
     <span data-ttu-id="2c55e-116">새 행 또는 열이 클릭한 셀의 필드에 대한 기본 합계와 함께 현재 그룹 외부 데이터 영역에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="2c55e-116">A new row or column outside the current group is added to the data region, with a default total for the field in the cell you clicked.</span></span>  
  
     <span data-ttu-id="2c55e-117">테이블릭스 데이터 영역이 테이블이면 행이 자동으로 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="2c55e-117">If the tablix data region is a table, a row is automatically added.</span></span>  
  
### <a name="to-add-totals-for-a-row-group"></a><span data-ttu-id="2c55e-118">행 그룹에 대한 합계를 추가하려면</span><span class="sxs-lookup"><span data-stu-id="2c55e-118">To add totals for a row group</span></span>  
  
-   <span data-ttu-id="2c55e-119">테이블릭스 데이터 영역 행 그룹 영역에서 합계를 구할 행 그룹 영역의 셀을 마우스 오른쪽 단추로 클릭한 다음 **합계 추가**를 가리키고 **이전** 또는 **이후**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2c55e-119">In the tablix data region row group area, right-click a cell in the row group area for which you want totals, point to **Add Total**, and then click **Before** or **After**.</span></span>  
  
     <span data-ttu-id="2c55e-120">새 행이 현재 그룹 외부 데이터 영역에 추가되고 해당 행의 각 숫자 필드에 대한 기본 합계가 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="2c55e-120">A new row outside the current group is added to the data region, and then a default total is added for each numeric field in the row.</span></span>  
  
### <a name="to-add-totals-for-a-column-group"></a><span data-ttu-id="2c55e-121">열 그룹에 대한 합계를 추가하려면</span><span class="sxs-lookup"><span data-stu-id="2c55e-121">To add totals for a column group</span></span>  
  
-   <span data-ttu-id="2c55e-122">테이블릭스 데이터 영역 행 그룹 영역에서 합계를 구할 열 그룹 영역의 셀을 마우스 오른쪽 단추로 클릭한 다음 **합계 추가**를 가리키고 **이전** 또는 **이후**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2c55e-122">In the tablix data region row group area, right-click a cell in the column group area for which you want totals, then point to **Add Total**, and click **Before** or **After**.</span></span>  
  
     <span data-ttu-id="2c55e-123">새 열이 현재 그룹 외부 데이터 영역에 추가되고 해당 열의 각 숫자 필드에 대한 기본 합계가 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="2c55e-123">A new column outside the current group is added to the data region, and then a default total is added for each numeric field in the column.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c55e-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2c55e-124">See Also</span></span>  
 <span data-ttu-id="2c55e-125">[합계, 집계 및 기본 제공 컬렉션에 대 한 식 범위 보고서 작성기 및 SSRS &#40;&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md) </span><span class="sxs-lookup"><span data-stu-id="2c55e-125">[Expression Scope for Totals, Aggregates, and Built-in Collections &#40;Report Builder and SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md) </span></span>  
 <span data-ttu-id="2c55e-126">[테이블 릭 스 데이터 영역 &#40;보고서 작성기 및 SSRS&#41;](../tablix-data-region-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="2c55e-126">[Tablix Data Region &#40;Report Builder and SSRS&#41;](../tablix-data-region-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="2c55e-127">[테이블 &#40;보고서 작성기 및 SSRS&#41;](tables-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="2c55e-127">[Tables &#40;Report Builder  and SSRS&#41;](tables-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="2c55e-128">[행렬 &#40;보고서 작성기 및 SSRS&#41;](create-a-matrix-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="2c55e-128">[Matrices &#40;Report Builder and SSRS&#41;](create-a-matrix-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="2c55e-129">[&#40;보고서 작성기 및 SSRS를 나열&#41;](create-invoices-and-forms-with-lists-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="2c55e-129">[Lists &#40;Report Builder and SSRS&#41;](create-invoices-and-forms-with-lists-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="2c55e-130">테이블, 행렬 및 목록&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="2c55e-130">Tables, Matrices, and Lists &#40;Report Builder and SSRS&#41;</span></span>](tables-matrices-and-lists-report-builder-and-ssrs.md)  
  
  
