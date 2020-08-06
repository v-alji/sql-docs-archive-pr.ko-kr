---
title: 데이터 영역의 셀 병합(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 43551300-89b2-4f4e-af09-69084324afaf
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c69ce8182bda3e0b644893e97b69280a003f5732
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87735011"
---
# <a name="merge-cells-in-a-data-region-report-builder-and-ssrs"></a><span data-ttu-id="6265e-102">데이터 영역의 셀 병합(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="6265e-102">Merge Cells in a Data Region (Report Builder and SSRS)</span></span>
  <span data-ttu-id="6265e-103">데이터 영역의 셀을 병합하여 셀을 결합하거나 데이터 영역 모양을 개선하거나 열 그룹 및 행 그룹에 대한 확장 레이블을 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6265e-103">You can merge cells in a data region to combine cells, improve data region appearance, or provide spanning labels for column groups and row groups.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6265e-104">데이터 영역의 각 영역(모퉁이, 열 머리글, 그룹 정의 또는 행 머리글) 내에서만 셀을 병합할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6265e-104">Cells can only be merged within each area of a data region: corner, column headers, group definition (or row headers), and body.</span></span> <span data-ttu-id="6265e-105">영역의 경계를 넘어서 셀을 병합할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6265e-105">You cannot merge cells that cross area boundaries.</span></span> <span data-ttu-id="6265e-106">예를 들어 데이터 영역 모퉁이 영역의 셀을 행 그룹 영역의 셀과 병합할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6265e-106">For example, you cannot merge a cell in the data region corner area with a cell in the row group area.</span></span> <span data-ttu-id="6265e-107">테이블 릭 스 영역에 대 한 자세한 내용은 [목록 &#40;보고서 작성기 및 SSRS&#41;](tables-matrices-and-lists-report-builder-and-ssrs.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="6265e-107">For more information about tablix areas, see [Lists &#40;Report Builder and SSRS&#41;](tables-matrices-and-lists-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-merge-cells-in-a-data-region"></a><span data-ttu-id="6265e-108">데이터 영역에서 셀을 병합하려면</span><span class="sxs-lookup"><span data-stu-id="6265e-108">To merge cells in a data region</span></span>  
  
1.  <span data-ttu-id="6265e-109">보고서 디자인 화면의 데이터 영역에서 병합할 첫 번째 셀을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6265e-109">In the data region on the report design surface, click the first cell to merge.</span></span> <span data-ttu-id="6265e-110">왼쪽 마우스 단추를 누른 상태로 가로 또는 세로로 끌어 인접한 셀을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6265e-110">Holding the left mouse button down, drag vertically or horizontally to select adjacent cells.</span></span> <span data-ttu-id="6265e-111">선택한 셀은 강조 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="6265e-111">The selected cells are highlighted.</span></span>  
  
2.  <span data-ttu-id="6265e-112">선택한 셀을 마우스 오른쪽 단추로 클릭하고 **셀 병합**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6265e-112">Right-click the selected cells and select **Merge Cells**.</span></span> <span data-ttu-id="6265e-113">선택한 셀이 단일 셀로 결합됩니다.</span><span class="sxs-lookup"><span data-stu-id="6265e-113">The selected cells are combined into a single cell.</span></span>  
  
3.  <span data-ttu-id="6265e-114">1단계 및 2단계를 반복하여 데이터 영역의 다른 인접 셀을 병합합니다.</span><span class="sxs-lookup"><span data-stu-id="6265e-114">Repeat steps 1 and 2 to merge other adjacent cells in a data region.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6265e-115">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6265e-115">See Also</span></span>  
 <span data-ttu-id="6265e-116">[테이블 릭 스 데이터 영역 &#40;보고서 작성기 및 SSRS&#41;](../tablix-data-region-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="6265e-116">[Tablix Data Region &#40;Report Builder and SSRS&#41;](../tablix-data-region-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="6265e-117">[테이블&#40;보고서 작성기 및 SSRS&#41;](tables-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="6265e-117">[Tables &#40;Report Builder  and SSRS&#41;](tables-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="6265e-118">[행렬 &#40;보고서 작성기 및 SSRS&#41;](create-a-matrix-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="6265e-118">[Matrices &#40;Report Builder and SSRS&#41;](create-a-matrix-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="6265e-119">[&#40;보고서 작성기 및 SSRS를 나열&#41;](create-invoices-and-forms-with-lists-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="6265e-119">[Lists &#40;Report Builder and SSRS&#41;](create-invoices-and-forms-with-lists-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="6265e-120">목록&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="6265e-120">Lists &#40;Report Builder and SSRS&#41;</span></span>](tables-matrices-and-lists-report-builder-and-ssrs.md)  
  
  
