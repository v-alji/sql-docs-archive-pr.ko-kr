---
title: 차트에 테두리 프레임 추가(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: ca0c5040-40bb-4cb7-bc2b-5bcbe73858bb
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 4c91d3de00caa4eab6ed1894042b2214b7dcf4b9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739387"
---
# <a name="add-a-border-frame-to-a-chart-report-builder-and-ssrs"></a><span data-ttu-id="ef84d-102">차트에 테두리 프레임 추가(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="ef84d-102">Add a Border Frame to a Chart (Report Builder and SSRS)</span></span>
  <span data-ttu-id="ef84d-103">차트에 시각적 효과를 주려면 차트 바깥쪽 둘레에 테두리 프레임을 사용해 보십시오.</span><span class="sxs-lookup"><span data-stu-id="ef84d-103">To give a chart more visual impact, consider using a border frame around the outside of the chart.</span></span> <span data-ttu-id="ef84d-104">**차트 속성** 대화 상자를 사용하거나 속성 창을 사용하여 테두리 프레임을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ef84d-104">You can select a border frame by using the **Chart Properties** dialog box or by using the Properties pane.</span></span> <span data-ttu-id="ef84d-105">차트 테두리 프레임은 다른 데이터 영역에 적용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ef84d-105">The chart border frames cannot be applied to any other data region.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-apply-a-border-to-a-chart"></a><span data-ttu-id="ef84d-106">차트에 테두리를 적용하려면</span><span class="sxs-lookup"><span data-stu-id="ef84d-106">To apply a border to a chart</span></span>  
  
1.  <span data-ttu-id="ef84d-107">차트의 아무 곳이나 마우스 오른쪽 단추로 클릭하고 **차트 속성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ef84d-107">Right-click anywhere on the chart and select **Chart Properties**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="ef84d-108">**차트 속성**이 표시되지 않는 경우 바로 가기 메뉴에서 **차트** 를 가리키고 **차트 속성**을 선택하세요.</span><span class="sxs-lookup"><span data-stu-id="ef84d-108">If you do not see the **Chart Properties**, point to **Chart** on the shortcut menu and select **Chart Properties**.</span></span>  
  
2.  <span data-ttu-id="ef84d-109">**테두리**를 선택하고 차트에 적용할 테두리 유형을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ef84d-109">Select **Border**, and click the type of border to apply to the chart.</span></span>  
  
3.  <span data-ttu-id="ef84d-110">테두리 스타일을 나타내는 식을 입력하거나 값을 선택합니다(옵션).</span><span class="sxs-lookup"><span data-stu-id="ef84d-110">(Optional) Select a value or type an expression that represents the style of the border.</span></span>  
  
4.  <span data-ttu-id="ef84d-111">차트 둘레에 테두리로 그려질 선의 색을 지정합니다(옵션).</span><span class="sxs-lookup"><span data-stu-id="ef84d-111">(Optional) Specify the color of the line that will be drawn around the chart as the border.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="ef84d-112">**선 색** 목록에는 일반적이 색이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ef84d-112">The **Line color** list contains common colors.</span></span> <span data-ttu-id="ef84d-113">다른 색 목록에서 선택하려면 목록에서 **다른 색** 을 클릭하거나 목록 옆의 식 단추 (**fx**)를 클릭하여 **식** 편집기를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="ef84d-113">If you want to select from a list of more colors, click **More colors** in the list or click the expression (**fx**) button next to the list to bring up the **Expression** editor.</span></span>  
  
5.  <span data-ttu-id="ef84d-114">테두리의 두께를 지정합니다(옵션).</span><span class="sxs-lookup"><span data-stu-id="ef84d-114">(Optional) Specify the width of the border.</span></span> <span data-ttu-id="ef84d-115">유효한 값은 0.25-20pt입니다.</span><span class="sxs-lookup"><span data-stu-id="ef84d-115">Valid values are between 0.25pt and 20pt.</span></span> <span data-ttu-id="ef84d-116">최상의 시각 효과를 위해 테두리 크기를 1-3pt로 유지하십시오.</span><span class="sxs-lookup"><span data-stu-id="ef84d-116">Consider keeping the size of your border to between 1 and 3pt for the best visual effect.</span></span>  
  
6.  <span data-ttu-id="ef84d-117">보고서에 흰색 이외의 배경색이 포함된 경우 같은 색의 페이지 색을 정의해 봅니다(옵션).</span><span class="sxs-lookup"><span data-stu-id="ef84d-117">(Optional) If your report contains a background color other than white, consider defining a page color that is the same color.</span></span> <span data-ttu-id="ef84d-118">페이지 색은 테두리 선 바깥쪽의 배경색입니다.</span><span class="sxs-lookup"><span data-stu-id="ef84d-118">The page color is the background color outside of the border line.</span></span>  
  
7.  <span data-ttu-id="ef84d-119">프레임 유형을 선택한 경우 프레임의 스타일 및 색을 지정합니다(옵션).</span><span class="sxs-lookup"><span data-stu-id="ef84d-119">(Optional) If you choose a Frame type, specify a style and color for the frame.</span></span> <span data-ttu-id="ef84d-120">**프레임 채우기 색** 목록에는 일반적인 색이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ef84d-120">The **Frame fill color** list contains common colors.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef84d-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ef84d-121">See Also</span></span>  
 <span data-ttu-id="ef84d-122">[차트&#40;보고서 작성기 및 SSRS&#41;](charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="ef84d-122">[Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="ef84d-123">[차트 서식 지정&#40;보고서 작성기 및 SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="ef84d-123">[Formatting a Chart &#40;Report Builder and SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="ef84d-124">차트에 3D 가장자리, 볼록 및 질감 스타일 추가&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="ef84d-124">Add Bevel, Emboss, and Texture Styles to a Chart &#40;Report Builder and SSRS&#41;</span></span>](chart-effects-add-bevel-emboss-or-texture-report-builder.md)  
  
  
