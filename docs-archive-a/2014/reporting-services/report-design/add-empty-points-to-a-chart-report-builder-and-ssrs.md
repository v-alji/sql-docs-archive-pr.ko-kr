---
title: 차트에 빈 요소 추가 (보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 2b056119-439f-494f-83cf-ee0c05dc6487
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 53d891c58210bcd51cd4e49f2f9a691a7729c884
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737960"
---
# <a name="add-empty-points-to-the-chart-report-builder-and-ssrs"></a><span data-ttu-id="ec2ab-102">차트에 빈 요소 추가(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="ec2ab-102">Add Empty Points to the Chart (Report Builder and SSRS)</span></span>
  <span data-ttu-id="ec2ab-103">Null 값은 차트에서 계열의 데이터 요소 사이에 있는 빈 공간 또는 간격으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="ec2ab-103">Null values are shown on the chart as empty spaces or gaps between data points in a series.</span></span> <span data-ttu-id="ec2ab-104">빈 요소는 Null 값에 의해 만들어진 빈 공간에 삽입될 수 있는 데이터 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="ec2ab-104">Empty points are data points that can be inserted in the empty space created by null values.</span></span>  
  
 <span data-ttu-id="ec2ab-105">기본적으로 빈 요소는 값을 포함하는 이전 및 다음 데이터 요소의 평균을 사용하여 계산됩니다.</span><span class="sxs-lookup"><span data-stu-id="ec2ab-105">By default, empty points are calculated by taking the average of the previous and next data points that contain a value.</span></span> <span data-ttu-id="ec2ab-106">모든 빈 요소가 0 지점에서 삽입되도록 이를 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ec2ab-106">You can change this so that all empty points are inserted at zero.</span></span>  
  
 <span data-ttu-id="ec2ab-107">자세한 내용은 [차트의 빈 데이터 요소 및 Null 데이터 요소&#40;보고서 작성기 및 SSRS&#41;](charts-report-builder-and-ssrs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ec2ab-107">For more information, see [Empty and Null Data Points in Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-specify-empty-points-on-a-chart"></a><span data-ttu-id="ec2ab-108">차트에 빈 요소를 지정하려면</span><span class="sxs-lookup"><span data-stu-id="ec2ab-108">To specify empty points on a chart</span></span>  
  
1.  <span data-ttu-id="ec2ab-109">속성 창을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="ec2ab-109">Open the Properties pane.</span></span>  
  
2.  <span data-ttu-id="ec2ab-110">디자인 화면에서 Null 값을 포함하는 계열을 마우스 오른쪽 단추로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ec2ab-110">On the design surface, right-click the series that contains null values.</span></span> <span data-ttu-id="ec2ab-111">계열의 속성이 속성 창에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="ec2ab-111">The properties for the series are displayed in the Properties pane.</span></span>  
  
3.  <span data-ttu-id="ec2ab-112">**EmptyPoint** 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="ec2ab-112">Expand the **EmptyPoint** node.</span></span>  
  
4.  <span data-ttu-id="ec2ab-113">Color 속성의 색 값을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ec2ab-113">Select a color value for the Color property.</span></span>  
  
5.  <span data-ttu-id="ec2ab-114">**EmptyPoint** 노드에서 Marker 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="ec2ab-114">In the **EmptyPoint** node, expand the Marker node.</span></span>  
  
6.  <span data-ttu-id="ec2ab-115">MarkerType 속성의 표식 유형을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ec2ab-115">Select a marker type for the MarkerType property.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="ec2ab-116">가로 막대형 차트, 세로 막대형 차트 또는 분산형 차트에 빈 요소를 추가하려면 표식 유형을 선택해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ec2ab-116">You must select a marker type to add empty points to a bar, column or scatter chart.</span></span> <span data-ttu-id="ec2ab-117">그러나 영역형 차트, 꺾은선형 차트 및 방사형 차트의 경우 표식을 지정하지 않아도 차트에서 빈 공간 또는 간격이 자동으로 채워지므로 표식 유형을 선택하지 않아도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ec2ab-117">However, for area, line and radar charts, selecting a marker type is optional because the chart fills in the empty space or gap without requiring a marker to be specified.</span></span>  
  
7.  <span data-ttu-id="ec2ab-118">빈 요소의 값을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="ec2ab-118">Set the value of the empty point.</span></span>  
  
    1.  <span data-ttu-id="ec2ab-119">속성 창에서 **CustomAttributes** 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="ec2ab-119">In the Properties pane, expand the **CustomAttributes** node.</span></span>  
  
    2.  <span data-ttu-id="ec2ab-120">EmptyPointValue 속성을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="ec2ab-120">Set the EmptyPointValue property.</span></span> <span data-ttu-id="ec2ab-121">이전 및 다음 데이터 요소의 평균 지점에서 빈 요소를 삽입하려면 **Average**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ec2ab-121">To insert empty points at an average of the previous and next data points, select **Average**.</span></span> <span data-ttu-id="ec2ab-122">0 지점에서 빈 요소를 삽입하려면 **Zero**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ec2ab-122">To insert empty points at zero, select **Zero**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec2ab-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ec2ab-123">See Also</span></span>  
 <span data-ttu-id="ec2ab-124">[데이터 세트 필터, 데이터 영역 필터 및 그룹 필터 추가&#40;보고서 작성기 및 SSRS&#41;](add-dataset-filters-data-region-filters-and-group-filters.md) </span><span class="sxs-lookup"><span data-stu-id="ec2ab-124">[Add Dataset Filters, Data Region Filters, and Group Filters &#40;Report Builder and SSRS&#41;](add-dataset-filters-data-region-filters-and-group-filters.md) </span></span>  
 <span data-ttu-id="ec2ab-125">[차트 종류&#40;보고서 작성기 및 SSRS&#41;](chart-types-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="ec2ab-125">[Chart Types &#40;Report Builder and SSRS&#41;](chart-types-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="ec2ab-126">[차트에 배율 구분선 추가&#40;보고서 작성기 및 SSRS&#41;](add-scale-breaks-to-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="ec2ab-126">[Add Scale Breaks to a Chart &#40;Report Builder and SSRS&#41;](add-scale-breaks-to-a-chart-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="ec2ab-127">차트&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="ec2ab-127">Charts &#40;Report Builder and SSRS&#41;</span></span>](charts-report-builder-and-ssrs.md)  
  
  
