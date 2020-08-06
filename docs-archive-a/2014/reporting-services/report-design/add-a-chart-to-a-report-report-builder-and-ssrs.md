---
title: 보고서에 차트 추가(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: a6b595dc-f775-4a53-8554-74a0bf9335ec
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 789dd6cce10b0425833ea63f2f7941ea75970a25
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639314"
---
# <a name="add-a-chart-to-a-report-report-builder-and-ssrs"></a><span data-ttu-id="04e14-102">보고서에 차트 추가(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="04e14-102">Add a Chart to a Report (Report Builder and SSRS)</span></span>
  <span data-ttu-id="04e14-103">시각적 형식으로 데이터를 요약하려면 차트 데이터 영역을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="04e14-103">When you want to summarize data in a visual format, use a Chart data region.</span></span> <span data-ttu-id="04e14-104">표현하려는 데이터의 형식에 적합한 차트 종류를 선택하는 것이 중요합니다.</span><span class="sxs-lookup"><span data-stu-id="04e14-104">It is important to choose an appropriate chart type for the type of data that you are presenting.</span></span> <span data-ttu-id="04e14-105">선택한 차트 종류에 따라 데이터를 차트 형태로 만들었을 때 해당 데이터를 얼마나 잘 해석할 수 있는지가 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="04e14-105">This affects how well the data can be interpreted when put in chart form.</span></span> <span data-ttu-id="04e14-106">자세한 내용은 [차트&#40;보고서 작성기 및 SSRS&#41;](charts-report-builder-and-ssrs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="04e14-106">For more information, see [Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="04e14-107">보고서에 차트 데이터 영역을 추가하는 가장 간단한 방법은 새 차트 마법사를 실행하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="04e14-107">The simplest way to add a Chart data region to your report is to run the New Chart Wizard.</span></span> <span data-ttu-id="04e14-108">이 마법사는 세로 막대형 차트, 선형 차트, 원형 차트, 가로 막대형 차트 및 영역형 차트를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="04e14-108">The wizard offers column, line, pie, bar, and area charts.</span></span> <span data-ttu-id="04e14-109">또한 차트를 직접 추가할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04e14-109">For these and other chart types, you can also add a chart manually.</span></span>  
  
 <span data-ttu-id="04e14-110">디자인 화면에 차트 데이터 영역을 추가한 후에는 숫자 데이터 및 숫자가 아닌 데이터에 대한 보고서 데이터 세트 필드를 차트의 차트 데이터 창으로 끌 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04e14-110">After you add a Chart data region to the design surface, you can drag report dataset fields for numeric and non-numeric data to the Chart Data pane of the chart.</span></span> <span data-ttu-id="04e14-111">차트를 클릭하여 차트 데이터 창을 표시합니다. 이 창에는 계열 그룹, 범주 그룹 및 값의 세 영역이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04e14-111">Click the chart to display the Chart Data pane with its three areas: Series Groups, Category Groups, and Values.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-a-chart-to-a-report-by-using-the-chart-wizard"></a><span data-ttu-id="04e14-112">차트 마법사를 사용하여 보고서에 차트를 추가하려면</span><span class="sxs-lookup"><span data-stu-id="04e14-112">To add a chart to a report by using the Chart Wizard</span></span>  
  
1.  > [!NOTE]  
    >  <span data-ttu-id="04e14-113">차트 마법사는 보고서 작성기에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04e14-113">The Chart Wizard is only available in Report Builder.</span></span>  
  
     <span data-ttu-id="04e14-114">**삽입** 탭에서 **차트**를 클릭한 다음 **차트 마법사**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="04e14-114">On the **Insert** tab, click **Chart**, and then click **Chart Wizard**.</span></span>  
  
2.  <span data-ttu-id="04e14-115">**새 차트** 마법사의 단계별 지침을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="04e14-115">Follow the steps in the **New** Chart wizard.</span></span>  
  
3.  <span data-ttu-id="04e14-116">**홈** 탭에서 **실행** 을 클릭하여 렌더링된 보고서를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="04e14-116">On the **Home** tab, click **Run** to see the rendered report.</span></span>  
  
4.  <span data-ttu-id="04e14-117">**실행** 탭에서 **디자인** 을 클릭하여 보고서에 대한 작업을 진행합니다.</span><span class="sxs-lookup"><span data-stu-id="04e14-117">On the **Run** tab, click **Design** to continue working on the report.</span></span>  
  
### <a name="to-add-a-chart-to-a-report"></a><span data-ttu-id="04e14-118">보고서에 차트를 추가하려면</span><span class="sxs-lookup"><span data-stu-id="04e14-118">To add a chart to a report</span></span>  
  
1.  <span data-ttu-id="04e14-119">보고서를 만들고 데이터 세트를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="04e14-119">Create a report and define a dataset.</span></span> <span data-ttu-id="04e14-120">자세한 내용은 [보고서에 데이터 추가 &#40;보고서 작성기 및 SSRS&#41;](../report-data/report-datasets-ssrs.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="04e14-120">For more information, see [Add Data to a Report &#40;Report Builder and SSRS&#41;](../report-data/report-datasets-ssrs.md).</span></span>  
  
2.  <span data-ttu-id="04e14-121">**삽입** 탭에서 **차트**를 클릭한 다음 **차트 삽입**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="04e14-121">On the **Insert** tab, click **Chart**, and then click **Insert Chart**.</span></span>  
  
3.  <span data-ttu-id="04e14-122">디자인 화면에서 차트 왼쪽 위 모퉁이를 배치할 위치를 클릭한 다음 차트 오른쪽 아래 모퉁이로 지정할 위치까지 끕니다.</span><span class="sxs-lookup"><span data-stu-id="04e14-122">Click on the design surface where you want the upper-left corner of the chart, and then drag to where you want the lower-right corner of the chart.</span></span>  
  
     <span data-ttu-id="04e14-123">**차트 종류 선택** 대화 상자가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="04e14-123">The **Select Chart Type** dialog box appears.</span></span>  
  
4.  <span data-ttu-id="04e14-124">추가할 차트 종류를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="04e14-124">Select the type of chart you want to add.</span></span> [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
5.  <span data-ttu-id="04e14-125">차트를 클릭하여 **차트 데이터** 창을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="04e14-125">Click the chart to display the **Chart Data** pane.</span></span>  
  
6.  <span data-ttu-id="04e14-126">**값** 영역에 하나 이상의 필드를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="04e14-126">Add one or more fields to the **Values** area.</span></span> <span data-ttu-id="04e14-127">이 정보는 값 축에 점으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="04e14-127">This information will be plotted on the value axis.</span></span>  
  
7.  <span data-ttu-id="04e14-128">**범주 그룹** 영역에 그룹화 필드를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="04e14-128">Add a grouping field to the **Category Groups** area.</span></span> <span data-ttu-id="04e14-129">**범주 그룹** 영역에 이 필드를 추가하면 그룹화 필드가 자동으로 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="04e14-129">When you add this field to the **Category Groups** area, a grouping field is automatically created for you.</span></span> <span data-ttu-id="04e14-130">각 그룹은 계열의 데이터 요소를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="04e14-130">Each group represents a data point in your series.</span></span>  
  
8.  <span data-ttu-id="04e14-131">범주별로 데이터를 요약하려면 데이터 필드를 마우스 오른쪽 단추로 클릭하고 **계열 속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="04e14-131">To summarize the data by category, right-click the data field and click **Series Properties**.</span></span> <span data-ttu-id="04e14-132">**범주** 상자의 드롭다운 목록에서 범주 필드를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="04e14-132">In the **Category** box, select the category field from the drop-down list.</span></span> [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
9. <span data-ttu-id="04e14-133">**홈** 탭에서 **실행** 을 클릭하여 렌더링된 보고서를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="04e14-133">On the **Home** tab, click **Run** to see the rendered report.</span></span>  
  
10. <span data-ttu-id="04e14-134">**실행** 탭에서 **디자인** 을 클릭하여 보고서에 대한 작업을 진행합니다.</span><span class="sxs-lookup"><span data-stu-id="04e14-134">On the **Run** tab, click **Design** to continue working on the report.</span></span>  
  
 <span data-ttu-id="04e14-135">가로 막대형 차트 및 세로 막대형 차트와 같이 축이 있는 차트에서 범주 축에는 일부 범주 레이블이 표시되지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04e14-135">On charts with axes, such as bar and column charts, the category axis may not display all the category labels.</span></span> <span data-ttu-id="04e14-136">축 레이블을 변경하는 방법에 대한 자세한 내용은 [축 간격 지정&#40;보고서 작성기 및 SSRS&#41;](specify-an-axis-interval-report-builder-and-ssrs.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="04e14-136">For more information about how to change the axis labels, see [Specify an Axis Interval &#40;Report Builder and SSRS&#41;](specify-an-axis-interval-report-builder-and-ssrs.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04e14-137">참고 항목</span><span class="sxs-lookup"><span data-stu-id="04e14-137">See Also</span></span>  
 <span data-ttu-id="04e14-138">[차트&#40;보고서 작성기 및 SSRS&#41;](charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="04e14-138">[Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="04e14-139">[차트 종류&#40;보고서 작성기 및 SSRS&#41;](chart-types-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="04e14-139">[Chart Types &#40;Report Builder and SSRS&#41;](chart-types-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="04e14-140">[차트의 빈 데이터 요소 및 Null 데이터 요소&#40;보고서 작성기 및 SSRS&#41;](empty-and-null-data-points-in-charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="04e14-140">[Empty and Null Data Points in Charts &#40;Report Builder and SSRS&#41;](empty-and-null-data-points-in-charts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="04e14-141">[자습서: 보고서에 가로 막대형 차트 추가(보고서 작성기)](https://go.microsoft.com/fwlink/?LinkId=198052) </span><span class="sxs-lookup"><span data-stu-id="04e14-141">[Tutorial: Adding a Bar Chart to Your Report (Report Builder)](https://go.microsoft.com/fwlink/?LinkId=198052) </span></span>  
 <span data-ttu-id="04e14-142">[자습서: 보고서에 가로 막대형 차트 추가(보고서 디자이너)](https://go.microsoft.com/fwlink/?LinkId=198042) </span><span class="sxs-lookup"><span data-stu-id="04e14-142">[Tutorial: Adding a Bar Chart to a Report (Report Designer)](https://go.microsoft.com/fwlink/?LinkId=198042) </span></span>  
 <span data-ttu-id="04e14-143">[자습서: 보고서에 원형 차트 추가(보고서 작성기)](https://go.microsoft.com/fwlink/?LinkId=198051) </span><span class="sxs-lookup"><span data-stu-id="04e14-143">[Tutorial: Adding a Pie Chart to Your Report (Report Builder)](https://go.microsoft.com/fwlink/?LinkId=198051) </span></span>  
 [<span data-ttu-id="04e14-144">자습서: 보고서에 원형 차트 추가(보고서 디자이너)</span><span class="sxs-lookup"><span data-stu-id="04e14-144">Tutorial: Adding a Pie Chart to a Report (Report Designer)</span></span>](https://go.microsoft.com/fwlink/?LinkId=198041)  
  
  
