---
title: 원형 차트 값을 원형의 위쪽에서 시작(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: d0e6fb59-ca4e-4d70-97cb-0ad183da21d3
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: ed010eeaf3e4d581cce2f7242144c4f73ec2895b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639271"
---
# <a name="start-pie-chart-values-at-the-top-of-the-pie-report-builder-and-ssrs"></a><span data-ttu-id="7445e-102">원형 차트를 원형의 위쪽에서 시작(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="7445e-102">Start Pie Chart Values at the Top of the Pie (Report Builder and SSRS)</span></span>
  <span data-ttu-id="7445e-103">기본적으로 원형 차트에서는 데이터 세트의 첫 번째 값이 원형의 위쪽으로부터 90도가 되는 지점에서 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="7445e-103">By default in pie charts, the first value in the dataset starts at 90 degrees from the top of the pie.</span></span> <span data-ttu-id="7445e-104">첫 번째 값이 위쪽에서 시작되게 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7445e-104">You may prefer that the first value start from the top.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-start-the-pie-chart-at-the-top-of-the-pie"></a><span data-ttu-id="7445e-105">원형 차트가 원형의 위쪽에서 시작되게 하려면</span><span class="sxs-lookup"><span data-stu-id="7445e-105">To Start the Pie Chart at the Top of the Pie</span></span>  
  
1.  <span data-ttu-id="7445e-106">원형 자체를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7445e-106">Click the pie itself.</span></span>  
  
2.  <span data-ttu-id="7445e-107">**속성** 창이 열려 있지 않으면 **보기** 탭에서 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7445e-107">If the **Properties** pane is not open, on the **View** tab, click **Properties**.</span></span>  
  
3.  <span data-ttu-id="7445e-108">**속성** 창의 **사용자 지정 특성**에서 **PieStartAngle** 을 **0** 에서 **270**으로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="7445e-108">In the **Properties** pane, under **Custom Attributes**, change **PieStartAngle** from **0** to **270**.</span></span>  
  
4.  <span data-ttu-id="7445e-109">**실행** 을 클릭하여 보고서를 미리 봅니다.</span><span class="sxs-lookup"><span data-stu-id="7445e-109">Click **Run** to preview your report.</span></span>  
  
 <span data-ttu-id="7445e-110">이제 첫 번째 값이 원형 차트의 위쪽에서 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="7445e-110">The first value now starts at the top of the pie chart.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7445e-111">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7445e-111">See Also</span></span>  
 <span data-ttu-id="7445e-112">[보고서 작성기 및 SSRS&#41;&#40;차트 서식 지정](formatting-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="7445e-112">[Formatting a Chart &#40;Report Builder and SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="7445e-113">원형 차트&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="7445e-113">Pie Charts &#40;Report Builder and SSRS&#41;</span></span>](charts-report-builder-and-ssrs.md)  
  
  
