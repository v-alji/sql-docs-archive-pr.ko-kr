---
title: 예외 강조 표시 (Excel 용 테이블 분석 도구) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Table Analysis tools
- highlight exceptions
ms.assetid: d90a12f8-7bc3-4fdb-95a1-7c89058f0d9a
author: minewiskan
ms.author: owend
ms.openlocfilehash: 97e8197fc76f431cf9740c5c6fbd7ac44d8204a5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740593"
---
# <a name="highlight-exceptions-table-analysis-tools-for-excel"></a><span data-ttu-id="05f5d-102">예외 강조 표시(Excel용 테이블 분석 도구)</span><span class="sxs-lookup"><span data-stu-id="05f5d-102">Highlight Exceptions (Table Analysis Tools for Excel)</span></span>
  <span data-ttu-id="05f5d-103">![리본의 예외 강조 표시 단추](media/tat-highlightex.gif "리본의 예외 강조 표시 단추")</span><span class="sxs-lookup"><span data-stu-id="05f5d-103">![Highlight Exceptions button in ribbon](media/tat-highlightex.gif "Highlight Exceptions button in ribbon")</span></span>  
  
 <span data-ttu-id="05f5d-104">경우에 따라 데이터에 특이 한 값이 포함 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05f5d-104">Sometimes your data might contain peculiar values.</span></span> <span data-ttu-id="05f5d-105">주택 소유자의 나이가 5세로 나타나는 것이 이러한 예입니다.</span><span class="sxs-lookup"><span data-stu-id="05f5d-105">For example, a homeowner's age might be listed as five years old.</span></span> <span data-ttu-id="05f5d-106">이러한 값 (일반적으로 이상 값 이라고 함)은 데이터 입력 오류로 인해 잘못 되었거나 비정상적인 *추세를 나타낼*수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05f5d-106">These values, often called *outliers*, might be wrong because of a data input error, or they might indicate unusual trends.</span></span> <span data-ttu-id="05f5d-107">어느 쪽이든 이러한 예외는 분석 품질에 영향을 미칩니다.</span><span class="sxs-lookup"><span data-stu-id="05f5d-107">Either way, exceptions can affect the quality of your analysis.</span></span> <span data-ttu-id="05f5d-108">**예외 강조 표시** 도구를 사용 하면 이러한 값을 찾아 추가 작업을 위해 검토할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05f5d-108">The **Highlight Exceptions** tool helps you find these values and review them for further action.</span></span>  
  
 <span data-ttu-id="05f5d-109">**예외 강조 표시** 도구는 Excel 데이터 테이블의 전체 데이터 범위에서 사용할 수 있습니다. 또는 몇 개의 열만 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05f5d-109">The **Highlight Exceptions** tool can work with the entire range of data in an Excel data table, or you can select only a few columns.</span></span> <span data-ttu-id="05f5d-110">또한 데이터의 변동성을 제어하는 임계값을 조정하여 예외 범위를 넓히거나 좁힐 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05f5d-110">You can also adjust a threshold that controls the variability of data, to find more or fewer exceptions.</span></span>  
  
 <span data-ttu-id="05f5d-111">도구가 분석을 완료하면 분석한 각 열에 몇 개의 이상값이 있는지에 대한 요약 보고서가 포함된 새 워크시트가 만들어지며</span><span class="sxs-lookup"><span data-stu-id="05f5d-111">When the tool completes its analysis, it creates a new worksheet that contains a summary report of how many outliers were found in each of the columns that you analyzed.</span></span> <span data-ttu-id="05f5d-112">원래 데이터 테이블의 예외도 강조 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="05f5d-112">The tool also highlights the exceptions in the original data table.</span></span> <span data-ttu-id="05f5d-113">이 도구는 전체적인 추세를 분석하므로 한 행에 있는 대부분의 값이 정상임을 확인하고 해당 행에서 하나의 셀만 강조 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05f5d-113">Because the tool analyzes overall trends, it might find that most of the values in a row are normal, and highlight only one cell in that row.</span></span> <span data-ttu-id="05f5d-114">위의 주택 소유자 예에서는 **Age** 열만 강조 표시 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05f5d-114">In the homeowner example above, only the **Age** column might be highlighted.</span></span>  
  
 <span data-ttu-id="05f5d-115">**요약 보고서**에서 **예외 임계값** 을 변경할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05f5d-115">You can also change the **Exception threshold** value in the **Summary Report**.</span></span> <span data-ttu-id="05f5d-116">이 값은 특정 셀에 비정상 값이 포함 될 확률을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="05f5d-116">This value indicates the probability that a particular cell contains an abnormal value.</span></span> <span data-ttu-id="05f5d-117">따라서 값을 늘리면 이상 값이 더 작은 값으로 강조 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="05f5d-117">Therefore, if you increase the value, fewer values will be highlighted as outliers.</span></span> <span data-ttu-id="05f5d-118">반대로 값을 낮추면 강조 표시되는 셀이 증가하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="05f5d-118">Conversely, when you decrease the value, you will see more highlighted cells.</span></span>  
  
## <a name="using-the-highlight-exceptions-tool"></a><span data-ttu-id="05f5d-119">예외 강조 표시 도구 사용</span><span class="sxs-lookup"><span data-stu-id="05f5d-119">Using the Highlight Exceptions Tool</span></span>  
  
1.  <span data-ttu-id="05f5d-120">Excel 테이블을 열고 **예외 강조 표시**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="05f5d-120">Open an Excel table and click **Highlight Exceptions**.</span></span>  
  
2.  <span data-ttu-id="05f5d-121">분석할 열을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="05f5d-121">Specify the columns to analyze.</span></span>  
  
3.  <span data-ttu-id="05f5d-122">**실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="05f5d-122">Click **Run**.</span></span>  
  
4.  <span data-ttu-id="05f5d-123">이상 값 이라는 제목의 워크시트를 열어 찾은 이상 값 \<table name> 의 요약을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="05f5d-123">Open the worksheet titled \<table name> Outliers to view a summary of the outliers that were found.</span></span>  
  
5.  <span data-ttu-id="05f5d-124">강조 표시 수를 변경 하려면 **예외 강조 표시 보고서**의 **예외 임계값** 행에서 위쪽 및 아래쪽 화살표를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="05f5d-124">To change the number of highlights, click the up and down arrows in the **Exception Threshold** row of the **Highlight Exceptions Report**.</span></span>  
  
### <a name="requirements"></a><span data-ttu-id="05f5d-125">요구 사항</span><span class="sxs-lookup"><span data-stu-id="05f5d-125">Requirements</span></span>  
 <span data-ttu-id="05f5d-126">다른 행을 예측하는 데 유용한 정보가 있는 열 값의 경우 잘못된 값이 포함되지 않았다면 해당 열을 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05f5d-126">You can include columns that do not contain bad values if these values contain information that might be useful in predicting other rows.</span></span> <span data-ttu-id="05f5d-127">그러나 누락된 값이 많거나 0 값이 많은 열은 선택 취소해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="05f5d-127">However, you should deselect columns that have many missing or zero values.</span></span>  
  
 <span data-ttu-id="05f5d-128">선택한 모든 열은 일반 패턴을 만드는 데 사용되므로 다음과 같이 정보가 부족한 입력 열을 사용해서는 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="05f5d-128">Because all of the selected columns are used to create a general pattern, you should avoid using input columns that you know to have poor information, such as the following:</span></span>  
  
-   <span data-ttu-id="05f5d-129">ID와 같은 고유한 값이 들어 있는 열</span><span class="sxs-lookup"><span data-stu-id="05f5d-129">Columns that contain unique values such as IDs.</span></span>  
  
-   <span data-ttu-id="05f5d-130">잘못된 값이 들어 있을 가능성이 높은 열</span><span class="sxs-lookup"><span data-stu-id="05f5d-130">Columns that contain a high percentage of wrong values.</span></span>  
  
-   <span data-ttu-id="05f5d-131">누락된 값이 많은 열</span><span class="sxs-lookup"><span data-stu-id="05f5d-131">Columns with many missing values.</span></span>  
  
     <span data-ttu-id="05f5d-132">누락된 값이 많은 입력 열을 포함하는 것이 유용한 경우도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05f5d-132">Note that there are some cases where it is useful to include input columns that have many missing values.</span></span> <span data-ttu-id="05f5d-133">예를 들어 고객이 소매점을 통해 구매 하는 경우 address 필드 값이 항상 누락 되는 경우 데이터 마이닝 알고리즘은이 정보를 사용 하 여 다른 유사한 고객을 식별할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05f5d-133">For example, if the value of the address field is always missing when the customer buys through a retailer, the data mining algorithm can use this information to identify other similar customers.</span></span> <span data-ttu-id="05f5d-134">데이터가 누락 된 경우 또는 누락 된 상태에 의미가 있는지 여부를 사례별로 결정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="05f5d-134">You must determine on a case-by-case basis whether data is missing by omission or because the Missing state is meaningful.</span></span>  
  
-   <span data-ttu-id="05f5d-135">패턴을 만드는 데 유용하게 사용될 가능성이 낮은 열.</span><span class="sxs-lookup"><span data-stu-id="05f5d-135">Columns that are unlikely to be useful in creating a pattern.</span></span> <span data-ttu-id="05f5d-136">예를 들어 모든 행의 값이 같은 열은 패턴을 작성하는 데 유용한 정보를 제공하지 못합니다.</span><span class="sxs-lookup"><span data-stu-id="05f5d-136">For example, a column that has the same value in every row adds no information that would be useful in building patterns.</span></span>  
  
## <a name="understanding-the-highlight-exceptions-report"></a><span data-ttu-id="05f5d-137">예외 강조 표시 보고서 이해</span><span class="sxs-lookup"><span data-stu-id="05f5d-137">Understanding the Highlight Exceptions Report</span></span>  
 <span data-ttu-id="05f5d-138">**실행**을 클릭 하면 도구는 다음 세 가지 작업을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="05f5d-138">When you click **Run**, the tool does three things:</span></span>  
  
-   <span data-ttu-id="05f5d-139">테이블의 현재 데이터를 기반으로 데이터 마이닝 구조를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="05f5d-139">Creates a data mining structure based on the current data in the table.</span></span>  
  
-   <span data-ttu-id="05f5d-140">[!INCLUDE[msCoName](../includes/msconame-md.md)] 클러스터링 알고리즘을 사용하여 새 데이터 마이닝 모델을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="05f5d-140">Creates a new data mining model by using the [!INCLUDE[msCoName](../includes/msconame-md.md)] Clustering algorithm.</span></span>  
  
-   <span data-ttu-id="05f5d-141">패턴을 기반으로 워크시트에 비정상적인 값이 있는지 확인하는 예측 쿼리를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="05f5d-141">Creates a prediction query based on the patterns to determine whether any values in the worksheet are improbable.</span></span>  
  
 <span data-ttu-id="05f5d-142">예외 임계값의 초기 값은 항상 75이며 이는 계산된 알고리즘에서 강조 표시된 데이터가 잘못될 확률이 75%임을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="05f5d-142">The initial value for the exception threshold is always 75, meaning that the algorithm calculated there is a 75% chance that the highlighted data is wrong.</span></span> <span data-ttu-id="05f5d-143">이 값은 초기 분석 시도를 위해 도구에서 자동으로 설정되지만 사용자가 보고서에서 이 값을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05f5d-143">The tool automatically sets this threshold for the initial analysis pass, but you can change the value in the report.</span></span>  
  
 <span data-ttu-id="05f5d-144">**예외 강조 표시** 도구는 원래 데이터 테이블에서 의심 스러운 셀을 강조 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="05f5d-144">The **Highlight Exceptions** tool highlights cells in the original data table that are suspicious.</span></span> <span data-ttu-id="05f5d-145">어두운 강조 표시는 해당 행을 주의해야 함을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="05f5d-145">Dark highlighting means the row needs attention.</span></span> <span data-ttu-id="05f5d-146">밝은 강조 표시는 특정 셀의 값이 의심스러운 항목으로 식별되었음을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="05f5d-146">Bright highlighting means the value in that particular cell was identified as suspect.</span></span> <span data-ttu-id="05f5d-147">예외 임계값을 변경하면 강조 표시된 값도 그에 맞게 변경됩니다.</span><span class="sxs-lookup"><span data-stu-id="05f5d-147">If you change the threshold for the exceptions, the highlighted values will change accordingly.</span></span>  
  
 <span data-ttu-id="05f5d-148">요약 차트에서는 각 열에서 임계값을 초과하는 셀의 수를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="05f5d-148">The summary chart shows the number of cells in each column that were above the exception threshold.</span></span>  
  
## <a name="related-tools"></a><span data-ttu-id="05f5d-149">관련 도구</span><span class="sxs-lookup"><span data-stu-id="05f5d-149">Related Tools</span></span>  
 <span data-ttu-id="05f5d-150">데이터 마이닝을 위한 준비 과정에 데이터를 정리 또는 검토할 때 Excel용 데이터 마이닝 클라이언트의 데이터 탐색 기능을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05f5d-150">When you are cleaning or reviewing data in preparation for data mining, you might also try the data exploration features in the Data Mining Client for Excel.</span></span> <span data-ttu-id="05f5d-151">이 추가 기능은 이상값 검색, 데이터 레이블 재지정 또는 데이터 분포 확인을 지원하는 여러 고급 도구를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="05f5d-151">This add-in provides more advanced tools to help you find outliers, relabel data, or view the distribution of data.</span></span> <span data-ttu-id="05f5d-152">Excel 용 데이터 마이닝 클라이언트의 데이터 탐색 도구에 대 한 자세한 내용은 [데이터 탐색 및 정리](exploring-and-cleaning-data.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="05f5d-152">For more information about data exploration tools in the Data Mining Client for Excel, see [Exploring and Cleaning Data](exploring-and-cleaning-data.md).</span></span>  
  
 <span data-ttu-id="05f5d-153">**예외 강조 표시** 도구는 클러스터링 알고리즘을 사용 합니다 [!INCLUDE[msCoName](../includes/msconame-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="05f5d-153">The **Highlight Exceptions** tool uses the [!INCLUDE[msCoName](../includes/msconame-md.md)] Clustering algorithm.</span></span> <span data-ttu-id="05f5d-154">클러스터링 모델은 비슷한 특성을 공유하는 행 그룹을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="05f5d-154">A clustering model detects groups of rows that share similar characteristics.</span></span> <span data-ttu-id="05f5d-155">Excel 용 데이터 마이닝 클라이언트는 그래프 및 특성 프로필을 사용 하 여 클러스터링으로 만든 데이터 마이닝 모델을 탐색할 수 있는 **찾아보기** 창을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="05f5d-155">The Data Mining Client for Excel provides a **Browse** window that uses graphs and characteristic profiles to let you explore data mining models created by clustering.</span></span> <span data-ttu-id="05f5d-156">**예외 강조 표시** 도구에서 만든 클러스터링 모델을 검색 하는 방법에 대 한 자세한 내용은 [모델 찾아보기 (Excel 용 데이터 마이닝 클라이언트)](highlight-exceptions-table-analysis-tools-for-excel.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="05f5d-156">For information about how to browse the clustering model created by the **Highlight Exceptions** tool, see [Browse Models (Data Mining Client for Excel)](highlight-exceptions-table-analysis-tools-for-excel.md).</span></span>  
  
 <span data-ttu-id="05f5d-157">[!INCLUDE[msCoName](../includes/msconame-md.md)] 클러스터링 알고리즘에 대한 자세한 내용은 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 온라인 설명서의 "Microsoft 클러스터링 알고리즘" 항목을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="05f5d-157">For more information about the [!INCLUDE[msCoName](../includes/msconame-md.md)] Clustering algorithm, see the topic "Microsoft Clustering Algorithm" in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05f5d-158">참고 항목</span><span class="sxs-lookup"><span data-stu-id="05f5d-158">See Also</span></span>  
 [<span data-ttu-id="05f5d-159">Excel용 테이블 분석 도구</span><span class="sxs-lookup"><span data-stu-id="05f5d-159">Table Analysis Tools for Excel</span></span>](table-analysis-tools-for-excel.md)  
  
  
