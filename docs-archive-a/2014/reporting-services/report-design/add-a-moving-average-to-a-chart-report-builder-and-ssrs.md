---
title: 차트에 이동 평균 추가(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 166cf9c1-0750-4866-8381-542e4fbfe65a
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 9bc16d0cb45a3240148f931009a836c231b442b5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639306"
---
# <a name="add-a-moving-average-to-a-chart-report-builder-and-ssrs"></a><span data-ttu-id="1a3c5-102">차트에 이동 평균 추가(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="1a3c5-102">Add a Moving Average to a Chart (Report Builder and SSRS)</span></span>
  <span data-ttu-id="1a3c5-103">이동 평균은 정의된 기간 동안 계산되는 계열 데이터의 평균입니다.</span><span class="sxs-lookup"><span data-stu-id="1a3c5-103">A moving average is an average of the data in your series, calculated over a defined period of time.</span></span> <span data-ttu-id="1a3c5-104">이동 평균은 차트에서 중요한 추세를 파악하는 데 사용될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1a3c5-104">The moving average can be shown on the chart to identify significant trends.</span></span>  
  
 <span data-ttu-id="1a3c5-105">이동 평균 수식은 기술 분석에서 사용되는 가장 일반적인 가격 표시기입니다.</span><span class="sxs-lookup"><span data-stu-id="1a3c5-105">The Moving Average formula is the most popular price indicator used in technical analyses.</span></span> <span data-ttu-id="1a3c5-106">평균값, 중앙값 및 표준 편차를 비롯한 다른 많은 수식들도 차트의 계열에서 파생될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1a3c5-106">Many other formulas, including mean, median and standard deviation, can also be derived from a series on the chart.</span></span> <span data-ttu-id="1a3c5-107">이동 평균을 지정할 때 각 수식은 하나 이상의 필수 매개 변수를 가질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1a3c5-107">When specifying a moving average, each formula may have one or more parameters that must be specified.</span></span>  
  
 <span data-ttu-id="1a3c5-108">디자인 모드에서 이동 평균 수식을 추가할 때 유일한 시각적 자리 표시자는 추가되는 선 계열입니다.</span><span class="sxs-lookup"><span data-stu-id="1a3c5-108">When a moving average formula is added in Design mode, the line series that is added is only a visual placeholder.</span></span> <span data-ttu-id="1a3c5-109">차트는 보고서 처리 중에 각 수식에 대한 데이터 요소를 계산합니다.</span><span class="sxs-lookup"><span data-stu-id="1a3c5-109">The chart will calculate the data points of each formula during report processing.</span></span>  
  
 <span data-ttu-id="1a3c5-110">추세 선에 대한 기본 지원은 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]에서 제공되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1a3c5-110">Built-in support for trend lines is not available in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-a-calculated-moving-average-to-a-series-on-the-chart"></a><span data-ttu-id="1a3c5-111">계산된 이동 평균을 차트의 계열에 추가하려면</span><span class="sxs-lookup"><span data-stu-id="1a3c5-111">To add a calculated moving average to a series on the chart</span></span>  
  
1.  <span data-ttu-id="1a3c5-112">**값** 영역에서 필드를 마우스 오른쪽 단추로 클릭하고 **계산된 계열 추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1a3c5-112">Right-click on a field in the **Values** area and click **Add Calculated Series**.</span></span> <span data-ttu-id="1a3c5-113">**계산된 계열 속성** 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="1a3c5-113">The **Calculated Series Properties** dialog box opens.</span></span>  
  
2.  <span data-ttu-id="1a3c5-114">**수식** 드롭다운 목록에서 **이동 평균** 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="1a3c5-114">Select the **Moving average** option from the **Formula** drop-down list.</span></span>  
  
3.  <span data-ttu-id="1a3c5-115">이동 평균의 기간을 나타내는 정수 값을 **기간** 에 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="1a3c5-115">Specify an integer value for the **Period** that represents the period of the moving average.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="1a3c5-116">기간은 이동 평균을 계산하는 데 사용되는 일 수입니다.</span><span class="sxs-lookup"><span data-stu-id="1a3c5-116">The period is the number of days used to calculate a moving average.</span></span> <span data-ttu-id="1a3c5-117">x축에 날짜/시간 값이 지정되지 않으면 이동 평균을 계산하는 데 사용되는 데이터 요소의 수에 따라 기간이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="1a3c5-117">If date/time values are not specified on the x-axis, the period is represented by the number of data points used to calculate a moving average.</span></span> <span data-ttu-id="1a3c5-118">데이터 요소가 한 개뿐이면 이동 평균 수식이 계산되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1a3c5-118">If there is only one data point, the moving average formula does not calculate.</span></span> <span data-ttu-id="1a3c5-119">이동 평균은 두 번째 요소부터 계산됩니다.</span><span class="sxs-lookup"><span data-stu-id="1a3c5-119">The moving average is calculated starting at the second point.</span></span> <span data-ttu-id="1a3c5-120">**첫 번째 요소에서 시작** 옵션을 지정할 경우 차트에서 이동 평균이 첫 번째 요소에서부터 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="1a3c5-120">If you specify the **Start from first point** option, the chart will start the moving average at the first point.</span></span> <span data-ttu-id="1a3c5-121">데이터 요소가 한 개뿐이면 계산된 이동 평균의 요소는 원본 계열의 첫 번째 요소와 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="1a3c5-121">If there is only one data point, the point in the calculated moving average will be identical to the first point in your original series.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a3c5-122">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1a3c5-122">See Also</span></span>  
 <span data-ttu-id="1a3c5-123">[보고서 작성기 및 SSRS&#41;&#40;차트 서식 지정](formatting-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="1a3c5-123">[Formatting a Chart &#40;Report Builder and SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="1a3c5-124">[차트 &#40;보고서 작성기 및 SSRS&#41;](charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="1a3c5-124">[Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="1a3c5-125">차트 &#40;보고서 작성기 및 SSRS에 빈 요소를 추가&#41;</span><span class="sxs-lookup"><span data-stu-id="1a3c5-125">Add Empty Points to the Chart &#40;Report Builder and SSRS&#41;</span></span>](add-empty-points-to-a-chart-report-builder-and-ssrs.md)  
  
  
