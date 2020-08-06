---
title: 줄무늬 선을 추가하여 차트 데이터 강조 표시(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: addd6137-4b6e-4e88-a7e8-9600fcd1ccce
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 01b0bb41a71daf9ac558ce8d8bb84480426870c1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647436"
---
# <a name="highlight-chart-data-by-adding-strip-lines-report-builder-and-ssrs"></a><span data-ttu-id="705c7-102">줄무늬 선을 추가하여 차트 데이터 강조 표시(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="705c7-102">Highlight Chart Data by Adding Strip Lines (Report Builder and SSRS)</span></span>
  <span data-ttu-id="705c7-103">간단히 줄무늬라고도 하는 줄무늬 선은 차트의 배경에 일정한 간격 또는 사용자 지정 간격으로 음영을 적용하는 수평 또는 수직 범위입니다.</span><span class="sxs-lookup"><span data-stu-id="705c7-103">Strip lines, or strips, are horizontal or vertical ranges that shade the background of the chart in regular or custom intervals.</span></span> <span data-ttu-id="705c7-104">다음과 같은 용도에 줄무늬 선을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="705c7-104">You can use strip lines to:</span></span>  
  
-   <span data-ttu-id="705c7-105">차트에서 개별 값을 조회하기 위한 가독성을 개선합니다.</span><span class="sxs-lookup"><span data-stu-id="705c7-105">Improve readability for looking up individual values on the chart.</span></span> <span data-ttu-id="705c7-106">일정한 간격으로 줄무늬 선을 지정하면 차트를 볼 때 데이터 요소를 구분하는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="705c7-106">Specify strip lines at regular intervals to help separate data points when reading the chart.</span></span>  
  
-   <span data-ttu-id="705c7-107">일정한 간격으로 발생하는 날짜를 강조 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="705c7-107">Highlight dates that occur at regular intervals.</span></span> <span data-ttu-id="705c7-108">예를 들어 판매 보고서에서 줄무늬 선을 사용하여 주말 데이터 요소를 식별할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="705c7-108">For example, in a sales report you might use strip lines to identify weekend data points.</span></span>  
  
-   <span data-ttu-id="705c7-109">특정 주요 범위를 강조 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="705c7-109">Highlight a specific key range.</span></span> <span data-ttu-id="705c7-110">앞의 판매 보고서 예에서 줄무늬 선을 사용하여 판매량이 가장 높은 80~100달러 범위를 강조 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="705c7-110">Using the previous example, you can use one strip line to highlight the highest range of sales that is between $80-100.</span></span>  
  
 <span data-ttu-id="705c7-111">줄무늬 선은 셰이프 차트나 극좌표형 차트에는 적용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="705c7-111">Strip lines are not applicable to Shape or Polar chart types.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-display-interlaced-strip-lines-at-regular-intervals-on-a-chart"></a><span data-ttu-id="705c7-112">차트에 인터레이스된 줄무늬 선을 일정한 간격으로 표시하려면</span><span class="sxs-lookup"><span data-stu-id="705c7-112">To display interlaced strip lines at regular intervals on a chart</span></span>  
  
1.  <span data-ttu-id="705c7-113">가로 줄무늬 선을 표시하려면 세로 차트 축을 마우스 오른쪽 단추로 클릭하고 **세로 축 속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="705c7-113">To show horizontal strip lines, right-click the vertical chart axis and click **VerticalAxis Properties**.</span></span>  
  
     <span data-ttu-id="705c7-114">세로 줄무늬 선을 표시하려면 가로 차트 축을 마우스 오른쪽 단추로 클릭하고 **가로 축 속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="705c7-114">To show vertical strip lines, right-click the horizontal chart axis and click **Horizontal Axis Properties**.</span></span>  
  
2.  <span data-ttu-id="705c7-115">**인터레이스 사용** 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="705c7-115">Select the **Use interlacing** option.</span></span> <span data-ttu-id="705c7-116">차트에 회색 줄무늬 선이 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="705c7-116">Grey strip lines will appear on your chart.</span></span>  
  
3.  <span data-ttu-id="705c7-117">(옵션) 인접한 **색** 드롭다운 목록을 사용하여 줄무늬 선의 색을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="705c7-117">(Optional) Specify a color for the strip lines using the adjacent **Color** drop-down list.</span></span>  
  
### <a name="to-display-interlaced-strip-lines-at-custom-intervals-on-a-chart"></a><span data-ttu-id="705c7-118">차트에 인터레이스된 줄무늬 선을 사용자 지정 간격으로 표시하려면</span><span class="sxs-lookup"><span data-stu-id="705c7-118">To display interlaced strip lines at custom intervals on a chart</span></span>  
  
1.  <span data-ttu-id="705c7-119">가로 줄무늬 선을 표시하려면 세로 차트 축을 마우스 오른쪽 단추로 클릭하고 **세로 축 속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="705c7-119">To show horizontal strip lines, right-click the vertical chart axis and click **VerticalAxis Properties**.</span></span>  
  
     <span data-ttu-id="705c7-120">세로 줄무늬 선을 표시하려면 가로 차트 축을 마우스 오른쪽 단추로 클릭하고 **가로 축 속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="705c7-120">To show vertical strip lines, right-click the horizontal chart axis and click **Horizontal Axis Properties**.</span></span>  
  
     <span data-ttu-id="705c7-121">축 속성이 속성 창에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="705c7-121">The axis properties are displayed in the Properties window.</span></span>  
  
2.  <span data-ttu-id="705c7-122">속성 창의 **모양** 섹션에서 StripLines 속성에 대한 컬렉션 편집(…) 단추를 클릭하여 **ChartStripLine 컬렉션 편집기**를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="705c7-122">In the **Appearance** section of the Properties pane, for the StripLines property, click the Edit Collection (...) button to open the **ChartStripLine Collection Editor**.</span></span>  
  
3.  <span data-ttu-id="705c7-123">**추가** 를 클릭하여 컬렉션에 새 줄무늬 선을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="705c7-123">Click **Add** to add a new strip line to the collection.</span></span>  
  
4.  <span data-ttu-id="705c7-124">StripWidth를 클릭하여 보고서에서 인치 단위로 측정되는 줄무늬 선의 너비를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="705c7-124">Click StripWidth to specify the width of the strip line, measured in inches on the report.</span></span> <span data-ttu-id="705c7-125">날짜나 시간을 강조 표시하는 경우 StripWidthType을 클릭하고 시간 간격을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="705c7-125">If you are highlighting dates or times, click StripWidthType and select a time interval.</span></span>  
  
5.  <span data-ttu-id="705c7-126">에 줄무늬 선이 반복되는 빈도를 지정하려면 Interval에 값 또는 식을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="705c7-126">Type a value or expression for the Interval to specify how often the strip line will repeat.</span></span>  <span data-ttu-id="705c7-127">예를 들어 간격을 10으로 지정하고 줄무늬 선 너비가 5인 경우 줄무늬 선은 0~5, 15~20, 30~35 값에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="705c7-127">For example, if you specify an interval of 10, and your strip line width is 5, strip lines will display at values of 0 to 5, 15 to 20, 30 to 35, and so on.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="705c7-128">기본적으로 Interval은 Auto로 설정되며 이는 차트가 사용자 지정 줄무늬 선에 대한 간격을 계산하지 않음을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="705c7-128">By default, Interval is set to Auto, which means the chart will not calculate an interval for custom strip lines.</span></span> <span data-ttu-id="705c7-129">차트는 간격 값이 설정된 경우에만 줄무늬 선의 간격을 계산합니다.</span><span class="sxs-lookup"><span data-stu-id="705c7-129">The chart only calculates intervals for strip lines if an interval value is set.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="705c7-130">참고 항목</span><span class="sxs-lookup"><span data-stu-id="705c7-130">See Also</span></span>  
 <span data-ttu-id="705c7-131">[차트의 축 레이블 서식 지정&#40;보고서 작성기 및 SSRS&#41;](formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="705c7-131">[Formatting Axis Labels on a Chart &#40;Report Builder and SSRS&#41;](formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="705c7-132">[차트 서식 지정&#40;보고서 작성기 및 SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="705c7-132">[Formatting a Chart &#40;Report Builder and SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="705c7-133">차트에 이동 평균 추가&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="705c7-133">Add a Moving Average to a Chart &#40;Report Builder and SSRS&#41;</span></span>](add-a-moving-average-to-a-chart-report-builder-and-ssrs.md)  
  
  
