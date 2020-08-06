---
title: 주식형 차트(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: f75ca11e-b7f5-4ac0-ba17-fe6f82742dad
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: a0f8c9c7dbc750bdb477f2ea1d96aa03f7ad022f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639270"
---
# <a name="stock-charts-report-builder-and-ssrs"></a><span data-ttu-id="ecfff-102">주식형 차트(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="ecfff-102">Stock Charts (Report Builder and SSRS)</span></span>
  <span data-ttu-id="ecfff-103">주식형 차트는 데이터 요소당 최대 4개의 값을 사용하는 재무 데이터 또는 과학적 데이터에 적합하도록 특별히 디자인되었습니다.</span><span class="sxs-lookup"><span data-stu-id="ecfff-103">A stock chart is specifically designed for financial or scientific data that uses up to four values per data point.</span></span> <span data-ttu-id="ecfff-104">이러한 값은 고가, 저가, 시가, 종가 값으로 정렬되어 재무 주식 데이터를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="ecfff-104">These values align with the high, low, open and close values that are used to plot financial stock data.</span></span> <span data-ttu-id="ecfff-105">이러한 종류의 차트에서는 일반적으로 선 또는 삼각형 표식을 사용하여 시가 및 종가 값을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="ecfff-105">This chart type displays opening and closing values by using markers, which are typically lines or triangles.</span></span> <span data-ttu-id="ecfff-106">다음 예에서 시가 값은 왼쪽에 표식으로 표시되어 있고 종가 값은 오른쪽에 표식으로 표시되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ecfff-106">In the following example, the opening values are shown by the markers on the left, and the closing values are shown by the markers on the right.</span></span>  
  
 <span data-ttu-id="ecfff-107">![주식형 차트](../media/rs-stockchart.gif "주식형 차트")</span><span class="sxs-lookup"><span data-stu-id="ecfff-107">![Stock chart](../media/rs-stockchart.gif "Stock chart")</span></span>  
  
 <span data-ttu-id="ecfff-108">주식형 차트의 예는 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 보고서 작성기의 예제 보고서로 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="ecfff-108">An example of a stock chart is available as a sample [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] Report Builder report.</span></span> <span data-ttu-id="ecfff-109">이 예제 보고서 및 기타 보고서를 다운로드 하는 방법에 대 한 자세한 내용은 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] [보고서 작성기 및 보고서 디자이너 샘플 보고서](https://go.microsoft.com/fwlink/?LinkId=198283)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ecfff-109">For more information about downloading this sample report and others, see [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)][Report Builder and Report Designer sample reports](https://go.microsoft.com/fwlink/?LinkId=198283).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="variations"></a><span data-ttu-id="ecfff-110">변형</span><span class="sxs-lookup"><span data-stu-id="ecfff-110">Variations</span></span>  
  
-   <span data-ttu-id="ecfff-111">**원통형**.</span><span class="sxs-lookup"><span data-stu-id="ecfff-111">**Candlestick**.</span></span> <span data-ttu-id="ecfff-112">원통형 차트는 시가와 종가 사이의 범위를 표시하는 상자가 사용되는 특수한 형태의 주식형 차트입니다.</span><span class="sxs-lookup"><span data-stu-id="ecfff-112">The candlestick chart is a specialized form of the stock chart, wherein boxes are used to show the range between the open and close values.</span></span> <span data-ttu-id="ecfff-113">주식형 차트와 마찬가지로 원통형 차트에서도 데이터 요소당 최대 4개의 값을 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ecfff-113">Like the stock chart, the candlestick chart can display up to four values per data point.</span></span>  
  
## <a name="data-considerations-for-stock-charts"></a><span data-ttu-id="ecfff-114">주식형 차트의 데이터 고려 사항</span><span class="sxs-lookup"><span data-stu-id="ecfff-114">Data Considerations for Stock Charts</span></span>  
  
-   <span data-ttu-id="ecfff-115">연간 주가 동향을 나타내는 경우처럼 여러 주식 데이터 요소를 나타내는 경우 각 데이터 요소의 시가, 종가, 고가 및 저가 값을 각각 구분하기는 어렵습니다.</span><span class="sxs-lookup"><span data-stu-id="ecfff-115">When presenting many stock data points, such as annual stock price trend, it is difficult to distinguish each open, close, high and low value of each data point.</span></span> <span data-ttu-id="ecfff-116">이 시나리오에서는 주식형 차트 대신 꺾은선형 차트를 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="ecfff-116">In this scenario, consider using a line chart instead of a stock chart.</span></span>  
  
-   <span data-ttu-id="ecfff-117">일반적으로 축 레이블은 생성 시 0에서부터 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="ecfff-117">When axis labels are generated, labeling usually begins at zero.</span></span>  <span data-ttu-id="ecfff-118">주가의 변동 폭은 일반적으로 다른 데이터 집합의 변동 폭과 차이가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ecfff-118">In general, stock prices do not fluctuate to the same degree as other data sets.</span></span> <span data-ttu-id="ecfff-119">따라서 데이터를 보다 수월하게 파악하기 위해 축 레이블이 0부터 시작하지 않도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ecfff-119">For this reason, you may want to disable the axis labels from starting at zero, in order to get a better view of your data.</span></span> <span data-ttu-id="ecfff-120">이렇게 하려면 **축 속성** 대화 상자 또는 속성 창에서 **IncludeZero** 를 **false** 로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="ecfff-120">To do this, set **IncludeZero** to **false** in the **Axis Properties** dialog box or the Properties window.</span></span> <span data-ttu-id="ecfff-121">차트가 축 레이블을 생성하는 방법은 [차트의 축 레이블 서식 지정&#40;보고서 작성기 및 SSRS&#41;](formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ecfff-121">For more information about how the chart generates axis labels, see [Formatting Axis Labels on a Chart &#40;Report Builder and SSRS&#41;](formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md).</span></span>  
  
-   [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="ecfff-122">에서는 주식형 차트에서 사용할 수 있는 가격 표시기, 상대 강도 지수, MACD 등의 여러 계산된 수식을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="ecfff-122">provides many calculated formulas for use with stock charts, including Price Indicator, Relative Strength Index, MACD and more.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ecfff-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ecfff-123">See Also</span></span>  
 <span data-ttu-id="ecfff-124">[범위 형 차트 &#40;보고서 작성기 및 SSRS&#41;](charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="ecfff-124">[Range Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="ecfff-125">[차트 &#40;보고서 작성기 및 SSRS&#41;](charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="ecfff-125">[Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="ecfff-126">[보고서 작성기 및 SSRS&#41;&#40;차트 서식 지정](formatting-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="ecfff-126">[Formatting a Chart &#40;Report Builder and SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="ecfff-127">축 속성 대화 상자, 축 옵션&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="ecfff-127">Axis Properties Dialog Box, Axis Options &#40;Report Builder and SSRS&#41;</span></span>](../axis-properties-dialog-box-axis-options-report-builder-and-ssrs.md)  
  
  
