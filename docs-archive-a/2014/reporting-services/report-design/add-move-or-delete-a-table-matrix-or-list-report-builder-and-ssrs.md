---
title: 테이블, 행렬 또는 목록 추가, 이동 또는 삭제(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 4b97c470-cde0-4bb1-a46e-5f5f5553feaa
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 43941639a41c897a49cd34662b74de26a27e3f07
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739352"
---
# <a name="add-move-or-delete-a-table-matrix-or-list-report-builder-and-ssrs"></a><span data-ttu-id="ecbd2-102">테이블, 행렬 또는 목록 추가, 이동 또는 삭제(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="ecbd2-102">Add, Move, or Delete a Table, Matrix, or List (Report Builder and SSRS)</span></span>
  <span data-ttu-id="ecbd2-103">데이터 영역은 보고서 데이터 세트의 데이터를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="ecbd2-103">A data region displays data from a report dataset.</span></span> <span data-ttu-id="ecbd2-104">데이터 영역에는 테이블, 행렬, 목록, 차트 및 계기가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ecbd2-104">Data regions include table, matrix, list, chart, and gauge.</span></span> <span data-ttu-id="ecbd2-105">한 데이터 영역을 다른 데이터 영역 안에 중첩시키려면 각 데이터 영역을 개별적으로 추가한 다음 자식 데이터 영역을 부모 데이터 영역 안으로 끕니다.</span><span class="sxs-lookup"><span data-stu-id="ecbd2-105">To nest one data region inside another, add each data region separately, and then drag the child data region onto the parent data region.</span></span>  
  
 <span data-ttu-id="ecbd2-106">보고서에 테이블 또는 행렬 데이터 영역을 추가하는 가장 간단한 방법은 새 테이블 또는 새 행렬 마법사를 실행하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="ecbd2-106">The simplest way to add a table or matrix data region to your report is to run the New Table or New Matrix Wizard.</span></span> <span data-ttu-id="ecbd2-107">이러한 마법사는 데이터 원본 연결을 선택하고, 필드를 정렬하고, 레이아웃과 스타일을 선택하는 과정을 안내합니다.</span><span class="sxs-lookup"><span data-stu-id="ecbd2-107">These wizards will guide you through the process of choosing a connection to a data source, arranging fields, and choosing the layout and style.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ecbd2-108">마법사는 보고서 작성기에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ecbd2-108">The wizard is available only in Report Builder.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-a-table-or-matrix-to-a-report-by-using-the-new-table-or-new-matrix-wizard"></a><span data-ttu-id="ecbd2-109">새 테이블 또는 새 행렬 마법사를 사용하여 보고서에 테이블 또는 행렬을 추가하려면</span><span class="sxs-lookup"><span data-stu-id="ecbd2-109">To add a table or matrix to a report by using the New Table or New Matrix Wizard</span></span>  
  
1.  <span data-ttu-id="ecbd2-110">**삽입** 탭에서 **테이블** 또는 **행렬**을 클릭한 다음 **테이블 마법사** 또는 **행렬 마법사**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ecbd2-110">On the **Insert** tab, click **Table** or **Matrix**, and then click **Table Wizard** or **Matrix Wizard**.</span></span>  
  
2.  <span data-ttu-id="ecbd2-111">**NewTable** 또는 **새 행렬** 마법사의 단계를 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="ecbd2-111">Follow the steps in the **NewTable** or **New Matrix** wizard.</span></span>  
  
3.  <span data-ttu-id="ecbd2-112">**홈** 탭에서 **실행** 을 클릭하여 렌더링된 보고서를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="ecbd2-112">On the **Home** tab, click **Run** to see the rendered report.</span></span>  
  
4.  <span data-ttu-id="ecbd2-113">**실행** 탭에서 **디자인** 을 클릭하여 보고서에 대한 작업을 진행합니다.</span><span class="sxs-lookup"><span data-stu-id="ecbd2-113">On the **Run** tab, click **Design** to continue working on the report.</span></span>  
  
### <a name="to-add-a-data-region"></a><span data-ttu-id="ecbd2-114">데이터 영역을 추가하려면</span><span class="sxs-lookup"><span data-stu-id="ecbd2-114">To add a data region</span></span>  
  
1.  <span data-ttu-id="ecbd2-115">**리본**의 **데이터 영역** 그룹에서 추가할 데이터 영역을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ecbd2-115">On the **Ribbon**, in the **Data Regions** group, click the data region to add.</span></span>  
  
2.  <span data-ttu-id="ecbd2-116">디자인 화면을 클릭한 다음 끌어 원하는 크기의 데이터 영역 상자를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ecbd2-116">Click the design surface, and then drag to create a box that is the desired size of the data region.</span></span>  
  
3.  <span data-ttu-id="ecbd2-117">보고서 데이터 창에서 데이터 영역 셀로 보고서 데이터 세트 필드를 끕니다.</span><span class="sxs-lookup"><span data-stu-id="ecbd2-117">Drag a report dataset field from the Report Data pane onto a data region cell.</span></span> <span data-ttu-id="ecbd2-118">이제 데이터 영역이 보고서 데이터 세트의 데이터에 바인딩됩니다.</span><span class="sxs-lookup"><span data-stu-id="ecbd2-118">The data region is now bound to data from the report dataset.</span></span>  
  
### <a name="to-select-a-data-region"></a><span data-ttu-id="ecbd2-119">데이터 영역을 선택하려면</span><span class="sxs-lookup"><span data-stu-id="ecbd2-119">To select a data region</span></span>  
  
-   <span data-ttu-id="ecbd2-120">테이블릭스 데이터 영역의 경우 모퉁이 핸들을 마우스 오른쪽 단추로 클릭하고</span><span class="sxs-lookup"><span data-stu-id="ecbd2-120">For a tablix data region, right-click the corner handle.</span></span> <span data-ttu-id="ecbd2-121">차트 또는 계기 데이터 영역의 경우 데이터 영역을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ecbd2-121">For a chart or gauge data region, click in the data region.</span></span>  
  
     <span data-ttu-id="ecbd2-122">선택 핸들 및 8개의 크기 조정 핸들이 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="ecbd2-122">A selection handle and eight resizing handles appear.</span></span>  
  
     <span data-ttu-id="ecbd2-123">중첩된 데이터 영역의 경우 중첩된 데이터 영역을 마우스 오른쪽 단추로 클릭하고 **선택**을 클릭한 다음 원하는 보고서 항목을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ecbd2-123">For nested data regions, right-click in the nested data region, click **Select**, and then select the report item you want.</span></span> <span data-ttu-id="ecbd2-124">선택된 보고서 항목을 확인하려면 속성 창을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="ecbd2-124">To verify which report item is selected, use the Properties pane.</span></span> <span data-ttu-id="ecbd2-125">디자인 화면에서 선택한 항목의 이름이 속성 창의 도구 모음에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="ecbd2-125">The name of the selected item on the design surface appears in the toolbar of the Properties pane.</span></span>  
  
### <a name="to-move-a-data-region"></a><span data-ttu-id="ecbd2-126">데이터 영역을 이동하려면</span><span class="sxs-lookup"><span data-stu-id="ecbd2-126">To move a data region</span></span>  
  
-   <span data-ttu-id="ecbd2-127">데이터 영역을 이동하려면 데이터 영역의 선택 핸들을 클릭하여 끕니다.</span><span class="sxs-lookup"><span data-stu-id="ecbd2-127">To move a data region, click the selection handle of the data region and drag it.</span></span> <span data-ttu-id="ecbd2-128">맞춤선을 사용하여 데이터 영역을 기존 보고서 항목에 맞춥니다.</span><span class="sxs-lookup"><span data-stu-id="ecbd2-128">Use snaplines to align it to existing report items.</span></span>  
  
     <span data-ttu-id="ecbd2-129">눈금자가 표시되지 않으면 보기 탭을 클릭하고 **눈금자** 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ecbd2-129">If the ruler is not visible, click the View tab and select the **Ruler** option.</span></span>  
  
     <span data-ttu-id="ecbd2-130">또는 화살표 키를 사용하여 디자인 화면에서 선택한 데이터 영역을 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="ecbd2-130">Alternatively, use the arrow keys to move the selected data region on the design surface.</span></span>  
  
### <a name="to-delete-a-data-region"></a><span data-ttu-id="ecbd2-131">데이터 영역을 삭제하려면</span><span class="sxs-lookup"><span data-stu-id="ecbd2-131">To delete a data region</span></span>  
  
-   <span data-ttu-id="ecbd2-132">데이터 영역을 선택하고 데이터 영역을 마우스 오른쪽 단추로 클릭한 다음 **삭제**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ecbd2-132">Select the data region, right-click in the data region, and then click **Delete**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ecbd2-133">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ecbd2-133">See Also</span></span>  
 <span data-ttu-id="ecbd2-134">[테이블릭스 데이터 영역&#40;보고서 작성기 및 SSRS&#41;](../tablix-data-region-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="ecbd2-134">[Tablix Data Region &#40;Report Builder and SSRS&#41;](../tablix-data-region-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="ecbd2-135">[테이블 &#40;보고서 작성기 및 SSRS&#41;](tables-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="ecbd2-135">[Tables &#40;Report Builder  and SSRS&#41;](tables-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="ecbd2-136">[행렬 &#40;보고서 작성기 및 SSRS&#41;](create-a-matrix-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="ecbd2-136">[Matrices &#40;Report Builder and SSRS&#41;](create-a-matrix-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="ecbd2-137">[&#40;보고서 작성기 및 SSRS를 나열&#41;](create-invoices-and-forms-with-lists-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="ecbd2-137">[Lists &#40;Report Builder and SSRS&#41;](create-invoices-and-forms-with-lists-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="ecbd2-138">테이블, 행렬 및 목록&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="ecbd2-138">Tables, Matrices, and Lists &#40;Report Builder and SSRS&#41;</span></span>](tables-matrices-and-lists-report-builder-and-ssrs.md)  
  
  
