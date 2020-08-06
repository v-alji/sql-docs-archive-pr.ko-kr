---
title: 차트에서 여백 추가 또는 제거(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 91c43f58-5771-4d33-a54d-0e802d2f5cba
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 9d8bad99591964540bcd14fc5609560a3d324515
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87735039"
---
# <a name="add-or-remove-margins-from-a-chart-report-builder-and-ssrs"></a><span data-ttu-id="7d262-102">차트에서 여백 추가 또는 제거(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="7d262-102">Add or Remove Margins from a Chart (Report Builder and SSRS)</span></span>
  <span data-ttu-id="7d262-103">세로 막대형 및 분산형 차트 종류의 경우 X축의 끝에 자동으로 양쪽 여백이 추가되고,</span><span class="sxs-lookup"><span data-stu-id="7d262-103">In Column and Scatter chart types, the chart automatically adds side margins on the ends of the x-axis.</span></span> <span data-ttu-id="7d262-104">가로 막대형 차트 종류의 경우 y축의 끝에 자동으로 양쪽 여백이 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="7d262-104">In Bar chart types, the chart automatically adds side margins on the ends of the y-axis.</span></span> <span data-ttu-id="7d262-105">다른 모든 차트 종류에서는 양쪽 여백이 추가되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7d262-105">In all other chart types, the chart does not add side margins.</span></span> <span data-ttu-id="7d262-106">여백의 크기는 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7d262-106">You cannot change the size of the margin.</span></span>  
  
 <span data-ttu-id="7d262-107">이 항목은 원형, 도넛형, 깔때기형 또는 피라미드형 차트 종류에는 적용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7d262-107">This topic does not apply to pie, doughnut, funnel, or pyramid chart types.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-enable-or-disable-side-margins"></a><span data-ttu-id="7d262-108">양쪽 여백을 사용하거나 사용하지 않으려면</span><span class="sxs-lookup"><span data-stu-id="7d262-108">To enable or disable side margins</span></span>  
  
1.  <span data-ttu-id="7d262-109">축을 마우스 오른쪽 단추로 클릭하고 **축 속성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="7d262-109">Right-click the axis and select **Axis Properties**.</span></span> <span data-ttu-id="7d262-110">**세로** 또는 **가로 축 속성** 대화 상자가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="7d262-110">The **Vertical** or **HorizontalAxis Properties** dialog box appears.</span></span>  
  
2.  <span data-ttu-id="7d262-111">**축 옵션** 페이지에서 다음과 같은 **양쪽 여백** 속성을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="7d262-111">On the **Axis Options** page, set the **Side margins** property:</span></span>  
  
    -   <span data-ttu-id="7d262-112">**자동** 차트 종류에 따라 양쪽 여백 추가 여부가 자동으로 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="7d262-112">**Auto** The chart will determine whether to add a side margin based on the chart type.</span></span>  
  
    -   <span data-ttu-id="7d262-113">**사용 안 함** 가로 막대형, 세로 막대형 및 분산형 차트에 양쪽 여백이 추가되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7d262-113">**Disabled** Bar, column, and scatter charts will have no side margins.</span></span>  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="7d262-114">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7d262-114">See Also</span></span>  
 <span data-ttu-id="7d262-115">[차트의 축 레이블 서식 지정&#40;보고서 작성기 및 SSRS&#41;](formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="7d262-115">[Formatting Axis Labels on a Chart &#40;Report Builder and SSRS&#41;](formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="7d262-116">[축 속성 대화 상자, 축 옵션&#40;보고서 작성기 및 SSRS&#41;](../axis-properties-dialog-box-axis-options-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="7d262-116">[Axis Properties Dialog Box, Axis Options &#40;Report Builder and SSRS&#41;](../axis-properties-dialog-box-axis-options-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="7d262-117">[축 간격 지정&#40;보고서 작성기 및 SSRS&#41;](specify-an-axis-interval-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="7d262-117">[Specify an Axis Interval &#40;Report Builder and SSRS&#41;](specify-an-axis-interval-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="7d262-118">[축 레이블의 서식을 날짜 또는 통화로 지정&#40;보고서 작성기 및 SSRS&#41;](format-axis-labels-as-dates-or-currencies-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="7d262-118">[Format Axis Labels as Dates or Currencies &#40;Report Builder and SSRS&#41;](format-axis-labels-as-dates-or-currencies-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="7d262-119">차트&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="7d262-119">Charts &#40;Report Builder and SSRS&#41;</span></span>](charts-report-builder-and-ssrs.md)  
  
  
