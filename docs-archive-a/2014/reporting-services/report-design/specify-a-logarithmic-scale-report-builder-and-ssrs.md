---
title: 로그 눈금 간격 지정(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: f3092c1c-b128-433d-9a95-983508b2a8d4
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 2cc422a6f95a420445dc604d08a23e8f8e65c95d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639279"
---
# <a name="specify-a-logarithmic-scale-report-builder-and-ssrs"></a><span data-ttu-id="38451-102">로그 눈금 간격 지정(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="38451-102">Specify a Logarithmic Scale (Report Builder and SSRS)</span></span>
  <span data-ttu-id="38451-103">로그 비례하는 데이터가 있는 경우 차트에서 로그 눈금 간격을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38451-103">If you have data that is logarithmically proportional, you may want to consider using a logarithmic scale on the chart.</span></span> <span data-ttu-id="38451-104">이렇게 하면 데이터를 관리하기가 쉬워지므로 차트의 모양이 개선됩니다.</span><span class="sxs-lookup"><span data-stu-id="38451-104">This helps improve the appearance of the chart by making your data more manageable.</span></span> <span data-ttu-id="38451-105">대부분의 로그 눈금 간격은 기준으로 10을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="38451-105">Most logarithmic scales use a base of 10.</span></span>  
  
 <span data-ttu-id="38451-106">이 기능은 값 축에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38451-106">This feature is only available on the value axis.</span></span> <span data-ttu-id="38451-107">값 축은 일반적으로 세로 축 또는 Y축이지만</span><span class="sxs-lookup"><span data-stu-id="38451-107">The value axis is usually the vertical, or y-axis.</span></span> <span data-ttu-id="38451-108">가로 막대형 차트에서는 가로 축 또는 X축입니다.</span><span class="sxs-lookup"><span data-stu-id="38451-108">On bar charts, however, it is the horizontal, or x-axis.</span></span>  
  
 <span data-ttu-id="38451-109">축이 로그로 표현된 경우 해당 축과 관련된 다른 모든 속성에도 로그 눈금 간격이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="38451-109">If your axis is logarithmic, all other properties relating to the axis will be scaled logarithmically.</span></span> <span data-ttu-id="38451-110">예를 들어 축에 상용 로그 눈금 간격을 지정한 경우 축 간격을 2로 설정하면 10의 2제곱, 즉 100 크기로 간격이 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="38451-110">For example, if you specify a base-10 logarithmic scale on your axis, setting an axis interval of 2 will generate intervals in magnitudes of 10 to the power of 2, or 100.</span></span> <span data-ttu-id="38451-111">즉, 축 값은 기본 결과인 1, 10, 100, 1000, 10000 대신 1, 100, 10000으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="38451-111">This means your axis values will read 1, 100, 10000, instead of the default result of 1, 10, 100, 1000, 10000.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-specify-a-logarithmic-scale"></a><span data-ttu-id="38451-112">로그 눈금 간격을 지정하려면</span><span class="sxs-lookup"><span data-stu-id="38451-112">To specify a logarithmic scale</span></span>  
  
1.  <span data-ttu-id="38451-113">차트의 Y축을 마우스 오른쪽 단추로 클릭하고 **세로 축 속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="38451-113">Right-click the y-axis of your chart, and click **VerticalAxis Properties**.</span></span> <span data-ttu-id="38451-114">**VerticalAxis 속성** 대화 상자가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="38451-114">The **VerticalAxis Properties** dialog box appears.</span></span>  
  
2.  <span data-ttu-id="38451-115">**축 옵션**에서 **로그 눈금 간격 사용**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="38451-115">In **Axis Options**, select **Uselogarithmic scale**.</span></span>  
  
3.  <span data-ttu-id="38451-116">**로그 밑** 입력란에 로그 밑으로 사용할 양수 값을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="38451-116">In the **Logbase** text box, type a positive value for the logarithmic base.</span></span> <span data-ttu-id="38451-117">값을 지정하지 않으면 로그 밑에는 기본값인 10이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="38451-117">If no value is specified, the logarithmic base defaults to 10.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38451-118">참고 항목</span><span class="sxs-lookup"><span data-stu-id="38451-118">See Also</span></span>  
 <span data-ttu-id="38451-119">[차트의 축 레이블 서식 지정&#40;보고서 작성기 및 SSRS&#41;](formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="38451-119">[Formatting Axis Labels on a Chart &#40;Report Builder and SSRS&#41;](formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="38451-120">[차트 서식 지정&#40;보고서 작성기 및 SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="38451-120">[Formatting a Chart &#40;Report Builder and SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="38451-121">[축 레이블의 서식을 날짜 또는 통화로 지정&#40;보고서 작성기 및 SSRS&#41;](format-axis-labels-as-dates-or-currencies-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="38451-121">[Format Axis Labels as Dates or Currencies &#40;Report Builder and SSRS&#41;](format-axis-labels-as-dates-or-currencies-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="38451-122">차트&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="38451-122">Charts &#40;Report Builder and SSRS&#41;</span></span>](charts-report-builder-and-ssrs.md)  
  
  
