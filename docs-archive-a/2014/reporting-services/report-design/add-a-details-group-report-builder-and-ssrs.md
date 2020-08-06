---
title: 세부 정보 그룹 추가(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 5ef8efba-6d48-4aeb-a3b9-a02ba5a44614
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 24b1f6af1aaf336a69a0068636ced60c364e556d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650768"
---
# <a name="add-a-details-group-report-builder-and-ssrs"></a><span data-ttu-id="14b99-102">세부 정보 그룹 추가(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="14b99-102">Add a Details Group (Report Builder and SSRS)</span></span>
  <span data-ttu-id="14b99-103">보고서 데이터 세트의 세부 데이터는 그룹 식이 없는 그룹으로 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="14b99-103">The detail data from a report dataset is specified as a group with no group expression.</span></span> <span data-ttu-id="14b99-104">행렬에 대한 세부 데이터를 표시하거나, 테이블이나 목록에서 삭제한 세부 데이터를 다시 추가하거나, 추가적인 세부 정보 그룹을 추가하려면 기존 테이블릭스 데이터 영역에 세부 정보 그룹을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="14b99-104">Add a detail group to an existing tablix data region when you want to display the detail data for a matrix, add back detail data that you have deleted from a table or list, or to add additional detail groups.</span></span> <span data-ttu-id="14b99-105">그룹에 대한 자세한 내용은 [그룹 이해&#40;보고서 작성기 및 SSRS&#41;](understanding-groups-report-builder-and-ssrs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="14b99-105">For more information about groups, see [Understanding Groups &#40;Report Builder and SSRS&#41;](understanding-groups-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-a-details-group-to-a-tablix-data-region"></a><span data-ttu-id="14b99-106">테이블릭스 데이터 영역에 세부 정보 그룹을 추가하려면</span><span class="sxs-lookup"><span data-stu-id="14b99-106">To add a details group to a tablix data region</span></span>  
  
1.  <span data-ttu-id="14b99-107">디자인 화면에서 테이블릭스 데이터 영역의 아무 곳이나 클릭하여 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="14b99-107">On the design surface, click anywhere in a tablix data region to select it.</span></span> <span data-ttu-id="14b99-108">선택한 데이터 영역에 대한 행 및 열 그룹이 그룹화 창에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="14b99-108">The Grouping pane displays the row and column groups for the selected data region.</span></span>  
  
2.  <span data-ttu-id="14b99-109">그룹화 창에서 가장 안쪽 자식 그룹을 마우스 오른쪽 단추로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="14b99-109">In the Grouping pane, right-click a group that is an innermost child group.</span></span> <span data-ttu-id="14b99-110">**그룹 추가**를 클릭한 다음 **자식 그룹**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="14b99-110">Click **Add Group**, and then click **Child Group**.</span></span> <span data-ttu-id="14b99-111">**테이블릭스 그룹** 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="14b99-111">The **Tablix Group** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="14b99-112">**그룹 식**에서 식을 공백으로 둡니다.</span><span class="sxs-lookup"><span data-stu-id="14b99-112">In **Group expression**, leave the expression blank.</span></span> <span data-ttu-id="14b99-113">세부 정보 그룹에는 식이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="14b99-113">A details group has no expression.</span></span>  
  
4.  <span data-ttu-id="14b99-114">**세부 데이터 표시**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="14b99-114">Select **Show detail data**.</span></span>  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
     <span data-ttu-id="14b99-115">새로운 세부 정보 그룹이 그룹화 창에 자식 그룹으로 추가되고 1단계에서 선택한 그룹의 행 핸들에 세부 정보 그룹 아이콘이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="14b99-115">A new details group is added as a child group in the Grouping pane, and the row handle for the group you selected in step 1 displays the details group icon.</span></span> <span data-ttu-id="14b99-116">핸들에 대한 자세한 내용은 [테이블릭스 데이터 영역 셀, 행 및 열&#40;보고서 작성기 및 SSRS&#41;](tablix-data-region-cells-rows-and-columns-report-builder-and-ssrs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="14b99-116">For more information about handles, see [Tablix Data Region Cells, Rows, and Columns &#40;Report Builder&#41; and SSRS](tablix-data-region-cells-rows-and-columns-report-builder-and-ssrs.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14b99-117">참고 항목</span><span class="sxs-lookup"><span data-stu-id="14b99-117">See Also</span></span>  
 <span data-ttu-id="14b99-118">[데이터 영역에서 그룹 추가 또는 삭제&#40;보고서 작성기 및 SSRS&#41;](add-or-delete-a-group-in-a-data-region-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="14b99-118">[Add or Delete a Group in a Data Region &#40;Report Builder and SSRS&#41;](add-or-delete-a-group-in-a-data-region-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="14b99-119">[그룹 이해&#40;보고서 작성기 및 SSRS&#41;](understanding-groups-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="14b99-119">[Understanding Groups &#40;Report Builder and SSRS&#41;](understanding-groups-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="14b99-120">[테이블릭스 데이터 영역&#40;보고서 작성기 및 SSRS&#41;](../tablix-data-region-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="14b99-120">[Tablix Data Region &#40;Report Builder and SSRS&#41;](../tablix-data-region-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="14b99-121">[테이블 &#40;보고서 작성기 및 SSRS&#41;](tables-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="14b99-121">[Tables &#40;Report Builder  and SSRS&#41;](tables-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="14b99-122">[행렬 &#40;보고서 작성기 및 SSRS&#41;](create-a-matrix-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="14b99-122">[Matrices &#40;Report Builder and SSRS&#41;](create-a-matrix-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="14b99-123">[&#40;보고서 작성기 및 SSRS를 나열&#41;](create-invoices-and-forms-with-lists-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="14b99-123">[Lists &#40;Report Builder and SSRS&#41;](create-invoices-and-forms-with-lists-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="14b99-124">테이블, 행렬 및 목록&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="14b99-124">Tables, Matrices, and Lists &#40;Report Builder and SSRS&#41;</span></span>](tables-matrices-and-lists-report-builder-and-ssrs.md)  
  
  
