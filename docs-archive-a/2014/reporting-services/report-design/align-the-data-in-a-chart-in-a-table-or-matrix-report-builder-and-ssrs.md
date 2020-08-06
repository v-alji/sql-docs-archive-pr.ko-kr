---
title: 테이블 또는 행렬에서 차트의 데이터 정렬(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 75137575-d1bf-46d6-8527-5afc85eea5e1
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 3e4278cd9f0dd5526770b43d2c6d94a8b87158cc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659848"
---
# <a name="align-the-data-in-a-chart-in-a-table-or-matrix-report-builder-and-ssrs"></a><span data-ttu-id="99609-102">테이블 또는 행렬에서 차트의 데이터 정렬(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="99609-102">Align the Data in a Chart in a Table or Matrix (Report Builder and SSRS)</span></span>
  <span data-ttu-id="99609-103">스파크라인과 데이터 막대는 불필요한 정보는 거의 없이 많은 정보를 제공하는 작고 단순한 차트입니다.</span><span class="sxs-lookup"><span data-stu-id="99609-103">Sparklines and data bars are small, simple charts that convey a lot of information with little extraneous detail.</span></span> <span data-ttu-id="99609-104">이 옵션을 선택하면 스파크라인과 데이터 막대의 값이 테이블 또는 행렬의 전체 셀에서 정렬됩니다. 이는 기반 데이터에서 누락된 값이 있어도 마찬가지입니다.</span><span class="sxs-lookup"><span data-stu-id="99609-104">When you check this option, the values in your sparklines and data bars will align across the different cells in the table or matrix, even if there are missing values in the data they are based on.</span></span>  
  
 <span data-ttu-id="99609-105">![rs_SparklineAlignData](../media/rs-sparklinealigndata.gif "rs_SparklineAlignData")</span><span class="sxs-lookup"><span data-stu-id="99609-105">![rs_SparklineAlignData](../media/rs-sparklinealigndata.gif "rs_SparklineAlignData")</span></span>  
  
 <span data-ttu-id="99609-106">이 이미지에서 세로 막대형 차트에는 각 직원의 일일 판매량이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="99609-106">In this image, the column chart shows daily sales for each employee.</span></span> <span data-ttu-id="99609-107">직원의 판매량이 없는 일의 경우 차트에서 공백으로 표시되고 이후의 일이 가로로 정렬됩니다.</span><span class="sxs-lookup"><span data-stu-id="99609-107">Note that for days that an employee has no sales, the chart leaves a blank and aligns subsequent days horizontally.</span></span> <span data-ttu-id="99609-108">또한 각 차트의 크기를 상대적으로 지정하여 차트를 세로로 맞춥니다.</span><span class="sxs-lookup"><span data-stu-id="99609-108">It also aligns the charts vertically by making the sizes of the different charts relative to each other.</span></span> <span data-ttu-id="99609-109">자세한 내용은 [스파크라인 및 데이터 막대&#40;보고서 작성기 및 SSRS&#41;](sparklines-and-data-bars-report-builder-and-ssrs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="99609-109">For more information, see [Sparklines and Data Bars &#40;Report Builder and SSRS&#41;](sparklines-and-data-bars-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="align-the-data-in-a-sparkline-or-data-bar"></a><span data-ttu-id="99609-110">스파크라인이나 데이터 막대의 데이터 정렬</span><span class="sxs-lookup"><span data-stu-id="99609-110">Align the data in a sparkline or data bar</span></span>  
  
1.  <span data-ttu-id="99609-111">스파크라인이나 데이터 막대를 클릭한 다음 **가로 축 속성** 또는 **세로 축 속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="99609-111">Click in the sparkline or data bar, and then click **Horizontal Axis Properties** or **Vertical Axis Properties**.</span></span>  
  
2.  <span data-ttu-id="99609-112">**축 옵션** 탭에서 **축 정렬 기준** 상자를 선택한 다음 드롭다운 상자에서 축을 정렬할 그룹을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="99609-112">On the **Axis Options** tab, check the **Align axes in** box, and then in the dropdown box, select the group on which to align the axis.</span></span>  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="99609-113">참고 항목</span><span class="sxs-lookup"><span data-stu-id="99609-113">See Also</span></span>  
 <span data-ttu-id="99609-114">[차트 &#40;보고서 작성기 및 SSRS&#41;](charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="99609-114">[Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="99609-115">스파크라인 및 데이터 막대 추가&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="99609-115">Add Sparklines and Data Bars &#40;Report Builder and SSRS&#41;</span></span>](add-sparklines-and-data-bars-report-builder-and-ssrs.md)  
  
  
