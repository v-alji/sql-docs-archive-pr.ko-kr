---
title: 스파크라인 및 데이터 막대 추가(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 0b297c2e-d48b-41b0-aabd-29680cdcdb05
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 55ec15354cdc78dd9678b9466f30d2fca0a73adc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647450"
---
# <a name="add-sparklines-and-data-bars-report-builder-and-ssrs"></a><span data-ttu-id="543f3-102">스파크라인 및 데이터 막대 추가(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="543f3-102">Add Sparklines and Data Bars (Report Builder and SSRS)</span></span>
  <span data-ttu-id="543f3-103">스파크라인과 데이터 막대는 불필요한 정보는 거의 없이 많은 정보를 제공하는 작은 여분의 차트입니다.</span><span class="sxs-lookup"><span data-stu-id="543f3-103">Sparklines and data bars are small, spare charts that convey a lot of information with little extraneous detail.</span></span> <span data-ttu-id="543f3-104">자세한 내용은 [스파크라인 및 데이터 막대 추가&#40;보고서 작성기 및 SSRS&#41;](sparklines-and-data-bars-report-builder-and-ssrs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="543f3-104">For more information about them, see [Sparklines and Data Bars &#40;Report Builder and SSRS&#41;](sparklines-and-data-bars-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="543f3-105">스파크라인과 데이터 막대는 가장 일반적으로 테이블이나 행렬의 셀에 배치됩니다.</span><span class="sxs-lookup"><span data-stu-id="543f3-105">Sparklines and data bars are most commonly placed in cells in a table or matrix.</span></span> <span data-ttu-id="543f3-106">일반적으로 스파크라인은 각각 한 계열만 표시하며</span><span class="sxs-lookup"><span data-stu-id="543f3-106">Sparklines usually display only one series each.</span></span> <span data-ttu-id="543f3-107">데이터 막대는 하나 이상의 데이터 요소를 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="543f3-107">Data bars can contain one or more data points.</span></span> <span data-ttu-id="543f3-108">스파크라인과 데이터 막대는 모두 테이블이나 행렬의 각 행에 대한 계열 정보를 반복하여 효과를 끌어냅니다.</span><span class="sxs-lookup"><span data-stu-id="543f3-108">Both sparklines and data bars derive their impact from repeating the series information for each row in the table or matrix.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-a-sparkline-or-data-bar-to-a-table-or-matrix"></a><span data-ttu-id="543f3-109">테이블이나 행렬에 스파크라인 또는 데이터 막대를 추가하려면</span><span class="sxs-lookup"><span data-stu-id="543f3-109">To add a sparkline or data bar to a table or matrix</span></span>  
  
1.  <span data-ttu-id="543f3-110">테이블이나 행렬을 아직 만들지 않은 경우 표시할 데이터가 포함된 테이블이나 행렬을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="543f3-110">If you have not done so already, create a table or matrix with the data you want to display.</span></span> <span data-ttu-id="543f3-111">자세한 내용은 [테이블&#40;보고서 작성기 및 SSRS&#41;](tables-report-builder-and-ssrs.md) 또는 [행렬&#40;보고서 작성기 및 SSRS&#41;](create-a-matrix-report-builder-and-ssrs.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="543f3-111">For more information, see [Tables &#40;Report Builder  and SSRS&#41;](tables-report-builder-and-ssrs.md) or [Matrices &#40;Report Builder and SSRS&#41;](create-a-matrix-report-builder-and-ssrs.md).</span></span>  
  
2.  <span data-ttu-id="543f3-112">테이블이나 행렬에 열을 삽입합니다.</span><span class="sxs-lookup"><span data-stu-id="543f3-112">Insert a column in your table or matrix.</span></span> <span data-ttu-id="543f3-113">자세한 내용은 [열 삽입 또는 삭제&#40;보고서 작성기 및 SSRS&#41;](insert-or-delete-a-column-report-builder-and-ssrs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="543f3-113">For more information, see [Insert or Delete a Column &#40;Report Builder and SSRS&#41;](insert-or-delete-a-column-report-builder-and-ssrs.md).</span></span>  
  
3.  <span data-ttu-id="543f3-114">**삽입** 탭에서 **스파크라인** 또는 **데이터 막대**를 클릭한 다음 새 열의 셀을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="543f3-114">On the **Insert** tab, click **Sparkline** or **Data Bar**, and then click in a cell in the new column.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="543f3-115">스파크라인은 테이블의 세부 그룹에는 배치할 수 없으며</span><span class="sxs-lookup"><span data-stu-id="543f3-115">You cannot place sparklines in a detail group in a table.</span></span> <span data-ttu-id="543f3-116">그룹과 연결된 셀에 배치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="543f3-116">They must go in a cell associated with a group.</span></span>  
  
4.  <span data-ttu-id="543f3-117">**스파크라인/데이터 막대 유형 변경** 대화 상자에서 원하는 스파크라인이나 데이터 막대의 유형을 클릭한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="543f3-117">In the **Change Sparkline/Data Bar Type** dialog box, click the kind of sparkline or data bar you want, and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="543f3-118">스파크라인이나 데이터 막대를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="543f3-118">Click the sparkline or data bar.</span></span>  
  
     <span data-ttu-id="543f3-119">**차트 데이터** 창이 열립니다.</span><span class="sxs-lookup"><span data-stu-id="543f3-119">The **Chart Data** pane opens.</span></span>  
  
6.  <span data-ttu-id="543f3-120">**값** 영역에서 **필드 추가** 더하기 기호(**+**)를 클릭한 다음 차트에 표시할 값이 포함된 필드를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="543f3-120">In the **Values** area, click the **Add Fields** plus sign (**+**), and then click the field whose values you want charted.</span></span>  
  
7.  <span data-ttu-id="543f3-121">**범주 그룹** 영역에서 **필드 추가** 더하기 기호(**+**)를 클릭한 다음 그룹화할 값이 포함된 필드를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="543f3-121">In the **Category Groups** area, click the **Add Fields** plus sign (**+**), and then click the field whose values you want to group by.</span></span>  
  
     <span data-ttu-id="543f3-122">일반적으로 스파크라인과 데이터 막대의 경우 각 행에 한 계열만 필요하기 때문에 **계열 그룹** 영역에 필드를 추가하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="543f3-122">Typically for sparklines and data bars, you will not add a field to the **Series Group** area because you only want one series for each row.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="543f3-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="543f3-123">See Also</span></span>  
 <span data-ttu-id="543f3-124">[차트 &#40;보고서 작성기 및 SSRS&#41;](charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="543f3-124">[Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="543f3-125">테이블 또는 행렬에서 차트의 데이터 정렬&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="543f3-125">Align the Data in a Chart in a Table or Matrix &#40;Report Builder and SSRS&#41;</span></span>](align-the-data-in-a-chart-in-a-table-or-matrix-report-builder-and-ssrs.md)  
  
  
