---
title: 표시기 추가 또는 삭제(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: a8b1aac1-53ef-47a4-afc0-8fa866c6c480
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 186ed4f5b6cf7cb239dc7c33a11089c11bccae14
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87735043"
---
# <a name="add-or-delete-an-indicator-report-builder-and-ssrs"></a><span data-ttu-id="e8cab-102">표시기 추가 또는 삭제(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="e8cab-102">Add or Delete an Indicator (Report Builder and SSRS)</span></span>
  <span data-ttu-id="e8cab-103">표시기는 단일 데이터 값의 상태를 한 눈에 볼 수 있도록 제공하는 최소 계기입니다.</span><span class="sxs-lookup"><span data-stu-id="e8cab-103">Indicators are minimal gauges that convey the state of a single data value at a glance.</span></span> <span data-ttu-id="e8cab-104">자세한 내용은 [표시기&#40;보고서 작성기 및 SSRS&#41;](indicators-report-builder-and-ssrs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e8cab-104">For more information about them, see [Indicators &#40;Report Builder and SSRS&#41;](indicators-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="e8cab-105">표시기는 일반적으로 테이블이나 행렬의 셀에 배치되지만 계기와 함께 또는 계기에 포함하여 표시기를 독립적으로 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8cab-105">Indicators are commonly placed in cells in a table or matrix, but you can also use indicators by themselves, side-by-side with gauges, or embedded in gauges.</span></span>  
  
 <span data-ttu-id="e8cab-106">표시기를 처음 추가하면 기본적으로 백분율을 단위로 사용하도록 표시기가 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="e8cab-106">When you first add an indicator, it is by default configured to use percentages as measurement units.</span></span> <span data-ttu-id="e8cab-107">백분율 범위는 표시기 집합의 멤버 간에 균등하게 분포되며 표시기가 나타내는 값의 범위는 테이블이나 행렬과 같은 표시기의 부모입니다.</span><span class="sxs-lookup"><span data-stu-id="e8cab-107">The percentage ranges are evenly distributed across members of the indicator set, and the scope of values shown by the indicator is the parent of the indicator such as a table or matrix.</span></span>  
  
 <span data-ttu-id="e8cab-108">표시기의 값과 상태를 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8cab-108">You can update the values and states of indicators.</span></span> <span data-ttu-id="e8cab-109">자세한 내용은 아래 항목을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e8cab-109">For more information, see the following topics:</span></span>  
  
-   [<span data-ttu-id="e8cab-110">표시기 아이콘 및 표시기 집합 변경&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="e8cab-110">Change Indicator Icons and Indicator Sets &#40;Report Builder and SSRS&#41;</span></span>](change-indicator-icons-and-indicator-sets-report-builder-and-ssrs.md)  
  
-   [<span data-ttu-id="e8cab-111">단위 설정 및 구성&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="e8cab-111">Set and Configure Measurement Units &#40;Report Builder and SSRS&#41;</span></span>](set-and-configure-measurement-units-report-builder-and-ssrs.md)  
  
-   [<span data-ttu-id="e8cab-112">동기화 범위 설정&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="e8cab-112">Set Synchronization Scope &#40;Report Builder and SSRS&#41;</span></span>](set-synchronization-scope-report-builder-and-ssrs.md)  
  
 <span data-ttu-id="e8cab-113">표시기가 계기 패널 내부에 배치되기 때문에 **표시기 속성** 대화 상자나 **속성** 창을 사용하여 표시기를 구성할 때 패널 대신 표시기를 선택해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8cab-113">Because an indicator is positioned inside the gauge panel, you need to select the indicator instead of the panel when you want to configure the indicator by using the **Indicators Properties** dialog box or the **Properties** pane.</span></span> <span data-ttu-id="e8cab-114">다음 그림에서는 계기 패널에서 선택된 표시기를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="e8cab-114">The following picture shows a selected indicator in its gauge panel.</span></span>  
  
 <span data-ttu-id="e8cab-115">![rs_GaugePanelWithIndicator](../media/rs-gaugepanelwithindicator.gif "rs_GaugePanelWithIndicator")</span><span class="sxs-lookup"><span data-stu-id="e8cab-115">![rs_GaugePanelWithIndicator](../media/rs-gaugepanelwithindicator.gif "rs_GaugePanelWithIndicator")</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e8cab-116">열 너비와 데이터 값의 길이에 따라 테이블 또는 행렬 셀의 텍스트가 자동으로 줄이 바뀌고 여러 줄로 표시될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8cab-116">Depending on column width and the length of data values, the text in table or matrix cells might wrap and display text on multiple lines.</span></span> <span data-ttu-id="e8cab-117">이 경우 표시기 아이콘이 늘어나고 모양이 바뀔 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8cab-117">When this occurs, the indicator icon might be stretched and change shape.</span></span> <span data-ttu-id="e8cab-118">그러면 표시기 아이콘의 가독성이 떨어질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8cab-118">This can make the indicator icon less readable.</span></span> <span data-ttu-id="e8cab-119">표시기를 사각형 안에 배치하여 아이콘이 늘어나지 않도록 하십시오.</span><span class="sxs-lookup"><span data-stu-id="e8cab-119">Place the indicator inside a rectangle to ensure that the icon is never stretched.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-an-indicator-to-a-table-or-matrix"></a><span data-ttu-id="e8cab-120">테이블 또는 행렬에 표시기를 추가하려면</span><span class="sxs-lookup"><span data-stu-id="e8cab-120">To add an indicator to a table or matrix</span></span>  
  
1.  <span data-ttu-id="e8cab-121">기존 보고서를 열거나 표시할 데이터가 있는 테이블 및 행렬을 포함하는 새 보고서를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e8cab-121">Open an existing report or create a new report that contains a table and matrix with the data you want to display.</span></span> <span data-ttu-id="e8cab-122">자세한 내용은 [테이블&#40;보고서 작성기 및 SSRS&#41;](tables-report-builder-and-ssrs.md) 또는 [행렬&#40;보고서 작성기 및 SSRS&#41;](create-a-matrix-report-builder-and-ssrs.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e8cab-122">For more information, see [Tables &#40;Report Builder  and SSRS&#41;](tables-report-builder-and-ssrs.md) or [Matrices &#40;Report Builder and SSRS&#41;](create-a-matrix-report-builder-and-ssrs.md).</span></span>  
  
2.  <span data-ttu-id="e8cab-123">테이블이나 행렬에 열을 삽입합니다.</span><span class="sxs-lookup"><span data-stu-id="e8cab-123">Insert a column in your table or matrix.</span></span> <span data-ttu-id="e8cab-124">자세한 내용은 [열 삽입 또는 삭제&#40;보고서 작성기 및 SSRS&#41;](insert-or-delete-a-column-report-builder-and-ssrs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e8cab-124">For more information, see [Insert or Delete a Column &#40;Report Builder and SSRS&#41;](insert-or-delete-a-column-report-builder-and-ssrs.md).</span></span>  
  
3.  <span data-ttu-id="e8cab-125">필요한 경우 **삽입** 탭에서 **사각형**을 클릭한 다음 새 열의 셀을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e8cab-125">Optionally, on the **Insert** tab, click **Rectangle**, and then click a cell in the new column.</span></span>  
  
4.  <span data-ttu-id="e8cab-126">**삽입** 탭에서 **표시기**를 클릭한 다음 새 열의 셀을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e8cab-126">On the **Insert** tab, click **Indicator**, and then click a cell in the new column.</span></span>  
  
     <span data-ttu-id="e8cab-127">셀에 사각형을 추가한 경우 해당 셀을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e8cab-127">If you added a rectangle to a cell, click that cell.</span></span>  
  
5.  <span data-ttu-id="e8cab-128">**표시기 스타일 선택** 대화 상자의 왼쪽 창에서 원하는 표시기 유형을 클릭한 다음 표시기 집합을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e8cab-128">In the **Select Indicator Style** dialog box, in the left pane, click the indicator type you want, and then click the indicator set.</span></span>  
  
6.  <span data-ttu-id="e8cab-129">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e8cab-129">Click **OK**.</span></span>  
  
7.  <span data-ttu-id="e8cab-130">표시기를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e8cab-130">Click the indicator.</span></span> <span data-ttu-id="e8cab-131">**계기 데이터** 창이 열립니다.</span><span class="sxs-lookup"><span data-stu-id="e8cab-131">The **Gauge Data** pane opens.</span></span>  
  
8.  <span data-ttu-id="e8cab-132">**값** 영역의 **(지정되지 않음)** 드롭다운 목록에서 값을 표시기로 표시할 필드를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e8cab-132">In the **Values** area, in the **(Unspecified)** drop-down list, click the field whose values you want to display as an indicator.</span></span>  
  
     <span data-ttu-id="e8cab-133">표시기는 기본값을 사용하도록 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="e8cab-133">The indicator is configured to use default values.</span></span> <span data-ttu-id="e8cab-134">기본적으로 표시기는 백분율을 단위로 사용하도록 구성되며 백분율 범위는 표시기의 멤버 간에 균등하게 분포되고 표시기가 제공하는 값은 가장 가까운 그룹의 범위를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="e8cab-134">By default, indicators are configured use percentages as measurement units and the percentage ranges are evenly distributed across the members of the indicator and the value that the indicator conveys uses the scope of the nearest group.</span></span>  
  
### <a name="to-delete-an-indicator-to-a-table-or-matrix"></a><span data-ttu-id="e8cab-135">테이블 또는 행렬에서 표시기를 삭제하려면</span><span class="sxs-lookup"><span data-stu-id="e8cab-135">To delete an indicator to a table or matrix</span></span>  
  
1.  <span data-ttu-id="e8cab-136">삭제할 표시기를 마우스 오른쪽 단추로 클릭하고 **삭제**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e8cab-136">Right-click the indicator to delete and click **Delete**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="e8cab-137">표시기는 다른 표시기나 계기가 포함된 계기 패널 안에 배치될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8cab-137">An indicator might be positioned inside a gauge panel that contains other indicators or gauges.</span></span> <span data-ttu-id="e8cab-138">계기 패널에 여러 항목이 포함된 경우 표시기를 삭제하려면 계기 패널이 아니라 표시기를 클릭해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8cab-138">If the gauge panels contain multiple items, be sure to click the indicator to delete it, not the gauge panel.</span></span> <span data-ttu-id="e8cab-139">계기 패널을 클릭한 다음 삭제하면 계기 패널과 그 안의 모든 항목이 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="e8cab-139">If you click and then delete the gauge panel, the gauge panels and all the items in it are deleted.</span></span>  
  
2.  <span data-ttu-id="e8cab-140">**삭제**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e8cab-140">Click **Delete**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8cab-141">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e8cab-141">See Also</span></span>  
 [<span data-ttu-id="e8cab-142">표시기&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="e8cab-142">Indicators &#40;Report Builder and SSRS&#41;</span></span>](indicators-report-builder-and-ssrs.md)  
  
  
