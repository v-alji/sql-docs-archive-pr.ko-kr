---
title: 축 레이블의 서식을 날짜 또는 통화로 지정(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: e9a01a74-2f51-4b35-be3a-a6138568f6cf
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: ffe9d903a2271db95d4b1c2ef6201d2b0f3edab3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649383"
---
# <a name="format-axis-labels-as-dates-or-currencies-report-builder-and-ssrs"></a><span data-ttu-id="5e65c-102">축 레이블의 서식을 날짜 또는 통화로 지정(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="5e65c-102">Format Axis Labels as Dates or Currencies (Report Builder and SSRS)</span></span>
  <span data-ttu-id="5e65c-103">올바른 형식의 DateTime 값을 축에 표시하면 차트에 이러한 값이 일로 자동 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="5e65c-103">When you show properly formatted DateTime values on an axis, a chart will automatically display these values as days.</span></span> <span data-ttu-id="5e65c-104">X축에 대해 월 또는 시간 간격과 같은 날짜/시간 간격을 지정하려면 축 레이블의 서식을 지정하고 축 간격 유형을 올바른 날짜 또는 시간 간격으로 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e65c-104">To specify a date/time interval for the x-axis, such as an interval of months or an interval of hours, you must format the axis labels and set the type of axis interval to a valid date or time interval.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5e65c-105">세로 막대형 차트와 분산형 차트에서는 가로 축 또는 X축이 범주 축이고</span><span class="sxs-lookup"><span data-stu-id="5e65c-105">In column and scatter charts, the horizontal, or x-axis, is the category axis.</span></span> <span data-ttu-id="5e65c-106">가로 막대형 차트에서는 세로 축 또는 Y축이 범주 축입니다.</span><span class="sxs-lookup"><span data-stu-id="5e65c-106">In bar charts, the vertical, or y-axis, is the category axis.</span></span>  
  
 <span data-ttu-id="5e65c-107">시간 간격의 서식을 올바르게 지정하려면 X축에 표시되는 값이 <xref:System.DateTime> 데이터 형식이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e65c-107">In order to format time intervals correctly, the values displayed on the x-axis must evaluate to a <xref:System.DateTime> data type.</span></span> <span data-ttu-id="5e65c-108">필드에 <xref:System.String>데이터 형식이 있는 경우 차트에서 간격이 날짜 또는 시간으로 계산되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5e65c-108">If your field has a data type of <xref:System.String>, the chart will not calculate intervals as dates or times.</span></span> <span data-ttu-id="5e65c-109">자세한 내용은 [차트&#40;보고서 작성기 및 SSRS&#41;](charts-report-builder-and-ssrs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5e65c-109">For more information, see [Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="5e65c-110">Y축에 숫자 값을 추가하면 기본적으로 차트에 숫자가 표시되기 전에 해당 숫자에 형식이 지정되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5e65c-110">When a numeric value is added to the y-axis, by default, the chart does not format the number before displaying it.</span></span> <span data-ttu-id="5e65c-111">숫자 필드가 매출 수치인 경우 차트의 가독성을 높이기 위해 숫자의 형식을 통화로 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5e65c-111">If your numeric field is a sales figure, consider formatting the numbers as currencies to increase the readability of the chart.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-format-x-axis-labels-as-monthly-intervals"></a><span data-ttu-id="5e65c-112">X축 레이블의 서식을 월 간격으로 지정하려면</span><span class="sxs-lookup"><span data-stu-id="5e65c-112">To format x-axis labels as monthly intervals</span></span>  
  
1.  <span data-ttu-id="5e65c-113">차트의 가로 축 또는 X축을 마우스 오른쪽 단추로 클릭하고 **HorizontalAxis 속성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="5e65c-113">Right-click the horizontal, or x-axis, of the chart, and select **HorizontalAxis Properties**.</span></span>  
  
2.  <span data-ttu-id="5e65c-114">**HorizontalAxis 속성** 대화 상자에서 **숫자**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="5e65c-114">In the **HorizontalAxis Properties** dialog box, select **Number**.</span></span>  
  
3.  <span data-ttu-id="5e65c-115">**범주** 목록에서 **날짜**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="5e65c-115">From the **Category** list, select **Date**.</span></span> <span data-ttu-id="5e65c-116">**유형** 목록에서 x축 레이블에 적용할 날짜 형식을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="5e65c-116">From the **Type** list, select a date format to apply to the x-axis labels.</span></span>  
  
4.  <span data-ttu-id="5e65c-117">**축 옵션**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="5e65c-117">Select **Axis Options.**</span></span>  
  
5.  <span data-ttu-id="5e65c-118">**간격**에 **1**을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="5e65c-118">In **Interval**, type **1**.</span></span> <span data-ttu-id="5e65c-119">**간격 유형** 속성에서 **월**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="5e65c-119">In **Interval type** property, select **Months**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="5e65c-120">간격 유형을 지정하지 않으면 차트에서 간격이 날의 개념으로 계산됩니다.</span><span class="sxs-lookup"><span data-stu-id="5e65c-120">If you do not specify an interval type, the chart will calculate intervals in terms of days.</span></span>  
  
6.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-format-y-axis-labels-using-a-currency-format"></a><span data-ttu-id="5e65c-121">통화 형식을 사용하여 Y축 레이블의 서식을 지정하려면</span><span class="sxs-lookup"><span data-stu-id="5e65c-121">To format y-axis labels using a currency format</span></span>  
  
1.  <span data-ttu-id="5e65c-122">차트의 세로 축 또는 Y축을 마우스 오른쪽 단추로 클릭하고 **VerticalAxis 속성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="5e65c-122">Right-click the vertical, or y-axis, of the chart, and select **VerticalAxis Properties**.</span></span>  
  
2.  <span data-ttu-id="5e65c-123">**VerticalAxis 속성** 대화 상자에서 **숫자**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="5e65c-123">In the **VerticalAxis Properties** dialog box, select **Number**.</span></span>  
  
3.  <span data-ttu-id="5e65c-124">**범주** 목록에서 **통화**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="5e65c-124">From the **Category** list, select **Currency**.</span></span> <span data-ttu-id="5e65c-125">**기호** 목록에서 y축 레이블에 적용할 통화 형식을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="5e65c-125">From the **Symbol** list, select a currency format to apply to the y-axis labels.</span></span>  
  
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="5e65c-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5e65c-126">See Also</span></span>  
 <span data-ttu-id="5e65c-127">[차트의 축 레이블 서식 지정&#40;보고서 작성기 및 SSRS&#41;](formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="5e65c-127">[Formatting Axis Labels on a Chart &#40;Report Builder and SSRS&#41;](formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="5e65c-128">[차트 서식 지정&#40;보고서 작성기 및 SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="5e65c-128">[Formatting a Chart &#40;Report Builder and SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="5e65c-129">[로그 눈금 간격 지정&#40;보고서 작성기 및 SSRS&#41;](specify-a-logarithmic-scale-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="5e65c-129">[Specify a Logarithmic Scale &#40;Report Builder and SSRS&#41;](specify-a-logarithmic-scale-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="5e65c-130">축 간격 지정&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="5e65c-130">Specify an Axis Interval &#40;Report Builder and SSRS&#41;</span></span>](specify-an-axis-interval-report-builder-and-ssrs.md)  
  
  
