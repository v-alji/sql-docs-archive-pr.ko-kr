---
title: 계기 패널에 표시기 및 계기 포함(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 4dff9b67-b483-4c51-a822-6dbe706a6840
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b1107745f54cd94abd7507a3e9b5a706ca5402de
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739369"
---
# <a name="include-indicators-and-gauges-in-a-gauge-panel-report-builder-and-ssrs"></a><span data-ttu-id="916f5-102">계기 패널에 표시기 및 계기 포함(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="916f5-102">Include Indicators and Gauges in a Gauge Panel (Report Builder and SSRS)</span></span>
  <span data-ttu-id="916f5-103">계기 패널은 하나 이상의 계기 및 표시기가 포함되는 최상위 컨테이너입니다.</span><span class="sxs-lookup"><span data-stu-id="916f5-103">The gauge panel is the top-level container that holds one or more gauges and indicators.</span></span> <span data-ttu-id="916f5-104">표시기는 계기 패널에서 계기에 포함하거나 계기 옆에 배치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="916f5-104">Indicators can be embedded in gauges or placed next to them in the gauge panel.</span></span>  
  
 <span data-ttu-id="916f5-105">표시기와 계기가 계기 패널에서 인접해 있으며 서로 다른 필드의 데이터를 표시하는 경우 계기와 표시기가 각각 나타내는 데이터를 명확하게 파악할 수 있도록 레이블을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="916f5-105">If the indicator and gauge are adjacent in the gauge panel and show data from different fields, you might want to add labels to make it clear what data the gauge and indicator convey.</span></span>  
  
 <span data-ttu-id="916f5-106">식을 사용하여 계기 및 표시기 옵션을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="916f5-106">Gauge and indicator options can be set by using expressions.</span></span> <span data-ttu-id="916f5-107">자세한 내용은 [식&#40;보고서 작성기 및 SSRS&#41;](expressions-report-builder-and-ssrs.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="916f5-107">For more information, see [Expressions &#40;Report Builder and SSRS&#41;](expressions-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-embed-an-indicator-in-a-gauge"></a><span data-ttu-id="916f5-108">계기에 표시기를 포함하려면</span><span class="sxs-lookup"><span data-stu-id="916f5-108">To embed an indicator in a gauge</span></span>  
  
1.  <span data-ttu-id="916f5-109">기존 보고서를 열거나 표시할 데이터가 있는 테이블 및 행렬을 포함하는 새 보고서를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="916f5-109">Open an existing report or create a new report that contains a table and matrix with the data you want to display.</span></span> <span data-ttu-id="916f5-110">자세한 내용은 [테이블&#40;보고서 작성기 및 SSRS&#41;](tables-report-builder-and-ssrs.md) 또는 [행렬&#40;보고서 작성기 및 SSRS&#41;](create-a-matrix-report-builder-and-ssrs.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="916f5-110">For more information, see [Tables &#40;Report Builder  and SSRS&#41;](tables-report-builder-and-ssrs.md) or [Matrices &#40;Report Builder and SSRS&#41;](create-a-matrix-report-builder-and-ssrs.md).</span></span>  
  
2.  <span data-ttu-id="916f5-111">테이블이나 행렬에 열을 삽입합니다.</span><span class="sxs-lookup"><span data-stu-id="916f5-111">Insert a column in your table or matrix.</span></span> <span data-ttu-id="916f5-112">자세한 내용은 [열 삽입 또는 삭제&#40;보고서 작성기 및 SSRS&#41;](insert-or-delete-a-column-report-builder-and-ssrs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="916f5-112">For more information, see [Insert or Delete a Column &#40;Report Builder and SSRS&#41;](insert-or-delete-a-column-report-builder-and-ssrs.md).</span></span>  
  
3.  <span data-ttu-id="916f5-113">**삽입** 탭의 **데이터 영역** 그룹에서 **계기**를 클릭한 다음 새 열의 셀을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="916f5-113">On the **Insert** tab, in the **Data Regions** group, click **Gauge**, and then, and then click a cell in the new column.</span></span> <span data-ttu-id="916f5-114">**계기 유형 선택** 대화 상자가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="916f5-114">The **Select Gauge Type** dialog box appears.</span></span>  
  
4.  <span data-ttu-id="916f5-115">**방사형**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="916f5-115">Click **Radial**.</span></span> <span data-ttu-id="916f5-116">그러면 첫 번째 방사형 계기가 선택됩니다.</span><span class="sxs-lookup"><span data-stu-id="916f5-116">The first radial gauge is selected.</span></span>  
  
5.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
6.  <span data-ttu-id="916f5-117">계기를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="916f5-117">Click the gauge.</span></span> <span data-ttu-id="916f5-118">**계기 데이터** 창이 열립니다.</span><span class="sxs-lookup"><span data-stu-id="916f5-118">The **Gauge Data** pane opens.</span></span>  
  
7.  <span data-ttu-id="916f5-119">**값** 영역의 **(지정하지 않음)** 목록 상자에서 계기에 표시할 값이 포함된 필드를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="916f5-119">In the **Values** area, in the **(Unspecified)** list box, click the field whose values you want to display in the gauge.</span></span> <span data-ttu-id="916f5-120">보고서 데이터 세트에서 사용할 필드를 끌어다 놓을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="916f5-120">Alternatively, drag the field to use from the report dataset.</span></span>  
  
8.  <span data-ttu-id="916f5-121">계기를 마우스 오른쪽 단추로 클릭하고 **표시기 추가**를 클릭한 다음 **자식**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="916f5-121">Right-click the gauge, click **Add Indicator**, and then click **Child**.</span></span> <span data-ttu-id="916f5-122">**표시기 스타일 선택** 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="916f5-122">The **Select Indicator Style** dialog box opens.</span></span>  
  
9. <span data-ttu-id="916f5-123">**표시기 스타일 선택** 대화 상자의 왼쪽 창에서 원하는 표시기 유형을 클릭한 다음 표시기 집합을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="916f5-123">In the **Select Indicator Style** dialog box, in the left pane, click the indicator type you want, and then click the indicator set.</span></span>  
  
10. [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
11. <span data-ttu-id="916f5-124">표시기를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="916f5-124">Click the indicator.</span></span> <span data-ttu-id="916f5-125">**계기 데이터** 창이 열립니다.</span><span class="sxs-lookup"><span data-stu-id="916f5-125">The **Gauge Data** pane opens.</span></span>  
  
12. <span data-ttu-id="916f5-126">**값** 영역의 **(지정하지 않음)** 드롭다운 상자에서 표시기로 표시할 값이 포함된 필드를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="916f5-126">In the **Values** area, in the **(Unspecified)** list box, click the field whose values you want to display as an indicator.</span></span> <span data-ttu-id="916f5-127">보고서 데이터 세트에서 사용할 필드를 끌어다 놓을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="916f5-127">Alternatively, drag the field to use from the report dataset.</span></span>  
  
     <span data-ttu-id="916f5-128">이 필드는 계기에 사용하는 필드와 같아도 되고 달라도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="916f5-128">The field can be the same or a different field from the one you use in the gauge.</span></span>  
  
13. [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
### <a name="to-show-an-indicator-and-gauge-side-by-side"></a><span data-ttu-id="916f5-129">표시기와 계기를 나란히 표시하려면</span><span class="sxs-lookup"><span data-stu-id="916f5-129">To show an indicator and gauge side by side</span></span>  
  
1.  <span data-ttu-id="916f5-130">기존 보고서를 열거나 표시할 데이터가 있는 테이블 및 행렬을 포함하는 새 보고서를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="916f5-130">Open an existing report or create a new report that contains a table and matrix with the data you want to display.</span></span> <span data-ttu-id="916f5-131">자세한 내용은 [테이블&#40;보고서 작성기 및 SSRS&#41;](tables-report-builder-and-ssrs.md) 또는 [행렬&#40;보고서 작성기 및 SSRS&#41;](create-a-matrix-report-builder-and-ssrs.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="916f5-131">For more information, see [Tables &#40;Report Builder  and SSRS&#41;](tables-report-builder-and-ssrs.md) or [Matrices &#40;Report Builder and SSRS&#41;](create-a-matrix-report-builder-and-ssrs.md).</span></span>  
  
2.  <span data-ttu-id="916f5-132">테이블이나 행렬에 열을 삽입합니다.</span><span class="sxs-lookup"><span data-stu-id="916f5-132">Insert a column in your table or matrix.</span></span> <span data-ttu-id="916f5-133">자세한 내용은 [열 삽입 또는 삭제&#40;보고서 작성기 및 SSRS&#41;](insert-or-delete-a-column-report-builder-and-ssrs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="916f5-133">For more information, see [Insert or Delete a Column &#40;Report Builder and SSRS&#41;](insert-or-delete-a-column-report-builder-and-ssrs.md).</span></span>  
  
3.  <span data-ttu-id="916f5-134">**삽입** 탭의 **데이터 영역** 그룹에서 **계기**를 클릭한 다음 삽입한 열의 셀을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="916f5-134">On the **Insert** tab, in the **Data Regions** group, click **Gauge**, and then click a cell in the column you inserted.</span></span> <span data-ttu-id="916f5-135">**계기 유형 선택** 대화 상자가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="916f5-135">The **Select Gauge Type** dialog appears.</span></span>  
  
4.  <span data-ttu-id="916f5-136">**방사형**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="916f5-136">Click **Radial**.</span></span> <span data-ttu-id="916f5-137">그러면 첫 번째 방사형 계기가 선택됩니다.</span><span class="sxs-lookup"><span data-stu-id="916f5-137">The first radial gauge is selected.</span></span>  
  
5.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
6.  <span data-ttu-id="916f5-138">계기를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="916f5-138">Click the gauge.</span></span> <span data-ttu-id="916f5-139">**계기 데이터** 창이 열립니다.</span><span class="sxs-lookup"><span data-stu-id="916f5-139">The **Gauge Data** pane opens.</span></span>  
  
7.  <span data-ttu-id="916f5-140">**값** 영역의 **(지정하지 않음)** 목록 상자에서 계기에 표시할 값이 포함된 필드를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="916f5-140">In the **Values** area, in the **(Unspecified)** list box, click the field whose values you want to display in the gauge.</span></span> <span data-ttu-id="916f5-141">보고서 데이터 세트에서 사용할 필드를 끌어다 놓을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="916f5-141">Alternatively, drag the field to use from the report dataset.</span></span>  
  
8.  <span data-ttu-id="916f5-142">계기를 마우스 오른쪽 단추로 클릭하고 **표시기 추가**를 클릭한 다음 **인접**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="916f5-142">Right-click the gauge, click **Add Indicator**, and then click **Adjacent**.</span></span> <span data-ttu-id="916f5-143">**표시기 스타일 선택** 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="916f5-143">The **Select Indicator Style** dialog box opens.</span></span>  
  
9. <span data-ttu-id="916f5-144">**표시기 스타일 선택** 대화 상자의 왼쪽 창에서 원하는 표시기 유형을 클릭한 다음 표시기 집합을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="916f5-144">In the **Select Indicator Style** dialog box, in the left pane, click the indicator type you want, and then click the indicator set.</span></span>  
  
10. [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
11. <span data-ttu-id="916f5-145">표시기를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="916f5-145">Click the indicator.</span></span> <span data-ttu-id="916f5-146">**계기 데이터** 창이 열립니다.</span><span class="sxs-lookup"><span data-stu-id="916f5-146">The **Gauge Data** pane opens.</span></span>  
  
12. <span data-ttu-id="916f5-147">**값** 영역의 **(지정하지 않음)** 드롭다운 상자에서 표시기로 표시할 값이 포함된 필드를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="916f5-147">In the **Values** area, in the **(Unspecified)** list box, click the field whose values you want to display as an indicator.</span></span> <span data-ttu-id="916f5-148">보고서 데이터 세트에서 사용할 필드를 끌어다 놓을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="916f5-148">Alternatively, drag the field to use from the report dataset.</span></span>  
  
     <span data-ttu-id="916f5-149">이 필드는 계기에 사용하는 필드와 같아도 되고 달라도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="916f5-149">The field can be the same or a different field from the one you use in the gauge.</span></span>  
  
13. [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
14. <span data-ttu-id="916f5-150">계기 패널을 마우스 오른쪽 단추로 클릭하고 **레이블 추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="916f5-150">Right-click the gauge panel and click **Add Label**.</span></span> <span data-ttu-id="916f5-151">레이블이 계기 패널에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="916f5-151">A label is added to the gauge panel.</span></span> <span data-ttu-id="916f5-152">같은 작업을 한 번 더 반복합니다.</span><span class="sxs-lookup"><span data-stu-id="916f5-152">Repeat one more time.</span></span>  
  
     <span data-ttu-id="916f5-153">이제 계기 패널에는 두 개의 레이블이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="916f5-153">The gauge panel has two labels.</span></span>  
  
15. <span data-ttu-id="916f5-154">각 레이블을 계기 또는 표시기 근처의 위치로 끕니다.</span><span class="sxs-lookup"><span data-stu-id="916f5-154">Drag each label to a location near the gauge or indicator.</span></span>  
  
16. <span data-ttu-id="916f5-155">계기 근처의 레이블을 마우스 오른쪽 단추로 클릭하고 **레이블 속성**을 클릭한 다음 **텍스트** 상자에 원하는 텍스트를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="916f5-155">Right-click the label near the gauge, click **Label Properties**,and type the text you want in the **Text** box.</span></span>  
  
17. <span data-ttu-id="916f5-156">표시기 옆의 레이블을 마우스 오른쪽 단추로 클릭하고 **레이블**속성을 클릭한 다음 **텍스트** 상자에 원하는 텍스트를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="916f5-156">Right-click the label near the indicator, click **Label Properties**,and type the text you want in the **Text** box.</span></span>  
  
18. [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="916f5-157">참고 항목</span><span class="sxs-lookup"><span data-stu-id="916f5-157">See Also</span></span>  
 [<span data-ttu-id="916f5-158">표시기&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="916f5-158">Indicators &#40;Report Builder and SSRS&#41;</span></span>](indicators-report-builder-and-ssrs.md)  
  
  
