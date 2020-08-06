---
title: 이상 값 (SQL Server 데이터 마이닝 추가 기능) | Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- exceptions [data mining]
- data preparation
- outliers [data mining]
- data cleaning
ms.assetid: e6fa7c62-4005-4792-9211-3b699377a517
author: minewiskan
ms.author: owend
ms.openlocfilehash: 92dddf3338d15e700576a13476ee364696bfd274
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743535"
---
# <a name="outliers-sql-server-data-mining-add-ins"></a><span data-ttu-id="a45a3-102">이상값(SQL Server 데이터 마이닝 추가 기능)</span><span class="sxs-lookup"><span data-stu-id="a45a3-102">Outliers (SQL Server Data Mining Add-ins)</span></span>
  <span data-ttu-id="a45a3-103">![데이터 마이닝 리본의 이상값 마법사](media/dmc-outliers.gif "데이터 마이닝 리본의 이상값 마법사")</span><span class="sxs-lookup"><span data-stu-id="a45a3-103">![Outliers wizard in Data Mining ribbon](media/dmc-outliers.gif "Outliers wizard in Data Mining ribbon")</span></span>  
  
 <span data-ttu-id="a45a3-104">이상 값은 다음 이유 중 하나로 인해 문제가 발생 하는 데이터 값 *을 의미 합니다* .</span><span class="sxs-lookup"><span data-stu-id="a45a3-104">An *outlier* means a data value that is problematic for any one of the following reasons:</span></span>  
  
-   <span data-ttu-id="a45a3-105">값이 예상 범위를 벗어납니다.</span><span class="sxs-lookup"><span data-stu-id="a45a3-105">Value is outside the expected range.</span></span>  
  
-   <span data-ttu-id="a45a3-106">데이터가 잘못 입력되었습니다.</span><span class="sxs-lookup"><span data-stu-id="a45a3-106">Data might have been entered incorrectly.</span></span>  
  
-   <span data-ttu-id="a45a3-107">값이 누락되었습니다.</span><span class="sxs-lookup"><span data-stu-id="a45a3-107">Value is missing.</span></span>  
  
-   <span data-ttu-id="a45a3-108">데이터가 공백 또는 다른 Null 문자열로 구성되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a45a3-108">Data consists of a space or other null string.</span></span>  
  
-   <span data-ttu-id="a45a3-109">값은 정확하지만 분포된 범위를 너무 벗어나서 모델에 심각한 영향을 줄 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a45a3-109">Value is accurate, but is so far outside the distribution that it can significantly affect the model.</span></span>  
  
 <span data-ttu-id="a45a3-110">Excel용 데이터 마이닝 클라이언트를 사용하여 이러한 데이터를 찾아낸 다음 값을 업데이트하거나 표시하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a45a3-110">The Data Mining Client for Excel helps you detect this data, and then update the values or suppress them.</span></span> <span data-ttu-id="a45a3-111">예를 들어 이상값을 산술 평균값으로 바꾸거나 잠재적으로 잘못된 값이 포함된 행을 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a45a3-111">For example, you can replace outliers with an arithmetic mean, or you can delete rows that contain potentially wrong values.</span></span>  
  
## <a name="handling-outliers"></a><span data-ttu-id="a45a3-112">이상값 처리</span><span class="sxs-lookup"><span data-stu-id="a45a3-112">Handling Outliers</span></span>  
 <span data-ttu-id="a45a3-113">이상 값 **제거** 마법사는 이상 값을 적절 하 게 처리할 수 있는 몇 가지 도구를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="a45a3-113">The **Remove Outliers** wizard gives you several tools to handle outliers appropriately:</span></span>  
  
-   <span data-ttu-id="a45a3-114">먼저 이상값과 다른 데이터 간의 관계 및 값 분포를 보다 잘 파악하기 위해 데이터를 탐색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a45a3-114">First, you can explore the data to better understand the distribution of values and the relationship of the outliers to other data.</span></span>  
  
     <span data-ttu-id="a45a3-115">예를 들어 **데이터 탐색** 태스크를 사용 하 여 값을 검토 하 고 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a45a3-115">For example, you can use the **Explore Data** task to review and fix the values.</span></span> <span data-ttu-id="a45a3-116">이상 값 **제거** 마법사는 모든 값의 분포를 이해 하는 데 도움이 되는 그래프나 가로 막대형 차트를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="a45a3-116">The **Remove Outliers** wizard also displays a graph, either a line or a bar chart, to help you understand the distribution of all values.</span></span>  
  
-   <span data-ttu-id="a45a3-117">다음으로 이상 **값 마법사를** 사용 하 여 이상 값을 제거 하거나 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a45a3-117">Next, you can use the **Outliers** wizard to remove or change outliers.</span></span> <span data-ttu-id="a45a3-118">사용자가 사용하는 방법은 불연속 값인지 아니면 연속 값인지에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="a45a3-118">The method that you use depends on whether the values are discrete or continuous.</span></span>  
  
     <span data-ttu-id="a45a3-119">이 마법사는 불연속 값을 막대형 차트로 표시하는데 각 막대는 데이터의 특정 값을 나타내며 막대의 높이는 각 값에 대한 사례 수를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="a45a3-119">The wizard displays discrete values in a bar chart, where each bar represents a specific value, and the height of the bar indicates the number of cases for each value.</span></span> <span data-ttu-id="a45a3-120">차트의 임계값 컨트롤을 이동하여 극단적이거나 잠재적으로 잘못된 값 그룹을 나타내는 막대를 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a45a3-120">By sliding the threshold control on the chart, you can cut off bars that represent groups of extreme or potentially bad values.</span></span>  
  
-   <span data-ttu-id="a45a3-121">이 마법사는 연속 값을 막대형 차트 또는 꺾은선형 차트로 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="a45a3-121">The wizard displays continuous values either on a bar chart or line chart.</span></span> <span data-ttu-id="a45a3-122">꺾은선형 차트에서 값은 X축에 표시되며 값의 개수는 Y축에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="a45a3-122">On the line chart, the value is represented on the x-axis and the count of values on the y-axis.</span></span>  
  
     <span data-ttu-id="a45a3-123">**최소값** 및 **최대값** 을 변경 하거나 막대를 이동 하 여 차트의 낮은 쪽 및 상위 쪽에서 값을 제거할지 또는 유지할지 여부를 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a45a3-123">You can control whether to remove or keep values at the low and high ends of the chart by changing the **Minimum** and **Maximum** values, or sliding the bars.</span></span> <span data-ttu-id="a45a3-124">최소값 및 최대값 설정을 변경하면 그래프에서 표시되지 않을 데이터가 음영으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="a45a3-124">As you change the minimum and maximum value settings, the data that will be suppressed is shown by shading in the graph.</span></span>  
  
 <span data-ttu-id="a45a3-125">처리할 이상값을 선택한 후에는 이러한 이상값을 처리하는 방법을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a45a3-125">After you have selected which outliers to work with, you tell the wizard how to handle the outliers.</span></span> <span data-ttu-id="a45a3-126">이상값을 포함하고 있는 행을 삭제하거나 평균, null 또는 다른 선택 사항 값과 같은 대체 값을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a45a3-126">You can either delete the rows that contain the outlier values, or you can specify a replacement value, such as a mean, a null, or another value of your choice.</span></span>  
  
 <span data-ttu-id="a45a3-127">끝으로 마법사는 새 데이터를 표시하는 몇 가지 동기화 옵션을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="a45a3-127">Finally, the wizard gives you some options for displaying the new data.</span></span> <span data-ttu-id="a45a3-128">원래 데이터를 새 값으로 바꾸거나 새 값을 포함하는 테이블에 새 열을 추가하거나 업데이트된 데이터를 포함하는 새 워크시트를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a45a3-128">You can replace the original data with the new values, add a new column to the table that contains the new values, or create a new worksheet that contains the updated data.</span></span>  
  
### <a name="using-the-outlier-wizard"></a><span data-ttu-id="a45a3-129">이상값 마법사 사용</span><span class="sxs-lookup"><span data-stu-id="a45a3-129">Using the Outlier Wizard</span></span>  
  
1.  <span data-ttu-id="a45a3-130">**데이터 마이닝** 리본에서 **데이터 정리**를 클릭 하 고 이상 값 **을 선택 합니다**.</span><span class="sxs-lookup"><span data-stu-id="a45a3-130">In the **Data Mining** ribbon, click **Clean Data**, and select **Outliers**.</span></span>  
  
2.  <span data-ttu-id="a45a3-131">**원본 데이터 선택** 대화 상자에서 Excel 데이터 테이블 또는 셀 범위를 선택 하 고 **다음**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="a45a3-131">In the **Select Source Data** dialog box, select an Excel data table, or a range of cells, and click **Next**.</span></span>  
  
    > [!WARNING]  
    >  <span data-ttu-id="a45a3-132">먼저 Excel로 복사 하지 않는 한 외부 **데이터의 이상 값 마법사를** 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a45a3-132">You cannot use the **Outliers** wizard on external data, unless you copy it to Excel first.</span></span>  
  
3.  <span data-ttu-id="a45a3-133">**열 선택** 대화 상자에서 **단일** 열을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="a45a3-133">In the **Select Column** dialog box, select a **single** column.</span></span>  
  
     <span data-ttu-id="a45a3-134">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a45a3-134">Click **Next**.</span></span>  
  
4.  <span data-ttu-id="a45a3-135">**임계값 지정** 대화 상자에서 데이터 분포를 검토 합니다.</span><span class="sxs-lookup"><span data-stu-id="a45a3-135">In the **Specify Thresholds** dialog box, review the distribution of data.</span></span>  
  
    -   <span data-ttu-id="a45a3-136">열에 불연속 값이 포함되어 있는 경우 마법사는 각 불연속 값에 대한 개수가 포함된 히스토그램을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="a45a3-136">If the column contains discrete values, the wizard displays a histogram containing the count for each discrete value.</span></span>  
  
         <span data-ttu-id="a45a3-137">이상 값이 드물게 발생 하는 경우 **최소값** 을 변경 하 여 필터링 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a45a3-137">Assuming that outliers are rare values, you can filter them out by changing the **Minimum** value.</span></span>  
  
    -   <span data-ttu-id="a45a3-138">열에 숫자 데이터가 포함 되어 있는 경우 **불연속으로 보기** 단추 또는 **숫자로 보기** 단추를 클릭 하 여 가로 막대형 차트 또는 꺾은선형 차트에서 값을 볼 때 사이를 전환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a45a3-138">If the column contains numeric data, you can click the **View as Discrete** button or the **View as Numeric** button to toggle between viewing the values in a bar chart or line chart.</span></span>  
  
5.  <span data-ttu-id="a45a3-139">**임계값 지정** 대화 상자에서 최소값과 최대값을 입력 하거나 슬라이더 막대를 끌어 유지할 데이터 범위를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="a45a3-139">In the **Specify Thresholds** dialog box, choose the range of data you want to keep by typing a minimum and maximum value, or by dragging the slider bars.</span></span> <span data-ttu-id="a45a3-140">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a45a3-140">Click **Next**.</span></span>  
  
6.  <span data-ttu-id="a45a3-141">이상 값 **처리** 대화 상자에서 값을 삭제 하거나 바꿀 것인지를 지정 하 고 **다음**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="a45a3-141">In the **Outlier Handling** dialog box, specify whether you want the values to be deleted or replaced, and click **Next**.</span></span>  
  
7.  <span data-ttu-id="a45a3-142">**대상 선택** 대화 상자에서 새 데이터를 저장할 위치를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a45a3-142">In the **Select Destination** dialog box, specify where you want the new data to be saved.</span></span>  
  
### <a name="related-options"></a><span data-ttu-id="a45a3-143">관련 옵션</span><span class="sxs-lookup"><span data-stu-id="a45a3-143">Related Options</span></span>  
 <span data-ttu-id="a45a3-144">마법사는 다음과 같은 옵션을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="a45a3-144">The wizard provides these options:</span></span>  
  
|<span data-ttu-id="a45a3-145">**Options**</span><span class="sxs-lookup"><span data-stu-id="a45a3-145">**Options**</span></span>|<span data-ttu-id="a45a3-146">**설명**</span><span class="sxs-lookup"><span data-stu-id="a45a3-146">**Comment**</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="a45a3-147">**열 선택**</span><span class="sxs-lookup"><span data-stu-id="a45a3-147">**Select Column**</span></span>|<span data-ttu-id="a45a3-148">한 번에 하나의 열만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a45a3-148">You can work with only one column at a time.</span></span>|  
|<span data-ttu-id="a45a3-149">**임계값 처리 지정**</span><span class="sxs-lookup"><span data-stu-id="a45a3-149">**Specify Thresholds Handling**</span></span>|<span data-ttu-id="a45a3-150">임계값 보다 더 작은 행에 있는 값을 제외 하려면 **최소** 를 사용 하 여 임계값을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a45a3-150">Set a threshold using **Minimum** to exclude values that are found in fewer rows than the threshold value.</span></span><br /><br /> <span data-ttu-id="a45a3-151">처음에는 **최소값** 의 값이 가장 적은 행의 값과 같으며, 최소값은 해당 값 보다 낮게 설정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a45a3-151">Initially the value in **Minimum** is equal to the value with the fewest rows, and you cannot make the minimum lower than that value.</span></span>|  
|<span data-ttu-id="a45a3-152">**이상값 처리**</span><span class="sxs-lookup"><span data-stu-id="a45a3-152">**Outlier Handling**</span></span>|<span data-ttu-id="a45a3-153">이상값을 삭제하려는 경우 현재 워크시트에서 데이터를 변경하거나 새 워크시트에서 데이터의 복사본을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a45a3-153">If you decide to delete outliers, you can either change the data in the current worksheet, or create a copy of the data in a new worksheet.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a45a3-154">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a45a3-154">See Also</span></span>  
 [<span data-ttu-id="a45a3-155">데이터 마이닝 추가 기능 SQL Server 데이터 &#40;탐색&#41;</span><span class="sxs-lookup"><span data-stu-id="a45a3-155">Explore Data &#40;SQL Server Data Mining Add-ins&#41;</span></span>](explore-data-sql-server-data-mining-add-ins.md)  
  
  
