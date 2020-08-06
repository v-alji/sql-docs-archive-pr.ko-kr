---
title: 여러 셰이프 차트에서 일관 된 색 지정 (보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: d52f68e9-2ba7-4bff-9053-4089e5164ab4
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c2c89f0f8cda3b7d6ef6b2acbd0de66c87170357
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639277"
---
# <a name="specify-consistent-colors-across-multiple-shape-charts-report-builder-and-ssrs"></a><span data-ttu-id="903df-102">여러 셰이프 차트에 일관된 색 지정(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="903df-102">Specify Consistent Colors across Multiple Shape Charts (Report Builder and SSRS)</span></span>
  <span data-ttu-id="903df-103">셰이프 차트가 아닌 차트에서 새로운 색은 차트 내 계열의 인덱스를 기반으로 색상표에서 선택됩니다.</span><span class="sxs-lookup"><span data-stu-id="903df-103">On non-shape charts, a new color is selected from the palette based on the index of series in the chart.</span></span> <span data-ttu-id="903df-104">예를 들어 차트의 첫 번째 계열은 색상표의 첫 번째 색에 매핑됩니다.</span><span class="sxs-lookup"><span data-stu-id="903df-104">For example, the first series on your chart will be mapped to the first color in the palette.</span></span> <span data-ttu-id="903df-105">그러나 셰이프 차트의 경우 다르게 동작합니다.</span><span class="sxs-lookup"><span data-stu-id="903df-105">However, this behavior differs for shape charts.</span></span> <span data-ttu-id="903df-106">셰이프 차트에서 색상표의 각 색은 데이터 세트의 데이터 요소와 매핑됩니다.</span><span class="sxs-lookup"><span data-stu-id="903df-106">On shape charts, each color in the palette is mapped to a data point in the dataset.</span></span> <span data-ttu-id="903df-107">즉 데이터 요소 1은 색상표의 첫 번째 색과 매핑되며 데이터 요소 2는 두 번째 색 등의 형태로 매핑됩니다.</span><span class="sxs-lookup"><span data-stu-id="903df-107">For example, data point 1 is mapped to the first color in the palette, data point 2 is mapped to the second color palette and so on.</span></span>  
  
 <span data-ttu-id="903df-108">데이터 요소에 값이 없는 경우 셰이프 차트에 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="903df-108">If a data point has no value, it is omitted from display on a shape chart.</span></span> <span data-ttu-id="903df-109">즉, 데이터 요소에 색이 지정되는 과정이 생략됩니다.</span><span class="sxs-lookup"><span data-stu-id="903df-109">This means that the data point is skipped from being colored.</span></span> <span data-ttu-id="903df-110">예를 들어 요소 2에 값 0이 있는 경우 요소 1은 색상표의 첫 번째 색에 매핑되고 요소 3은 색상표의 두 번째 색에 매핑됩니다.</span><span class="sxs-lookup"><span data-stu-id="903df-110">For example, if point 2 has a value of zero, point 1 will be mapped to the first color in the palette, and point 3 will be mapped to the second color in the palette.</span></span> <span data-ttu-id="903df-111">이러한 방법을 사용하면 원형 차트의 데이터 세트에서 비어 있는 요소에 대해 불필요하게 색상표 색을 사용하지 않아도 되므로 비어 있는 요소를 그리지 않아도 되는 경우 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="903df-111">This approach is useful because the empty points in the dataset of a pie chart do not unnecessarily use a palette color when the empty point does not need to be drawn.</span></span>  
  
 <span data-ttu-id="903df-112">그러나 여러 개의 원형 차트가 보고서에 표시되는 경우 동일한 범주 그룹에 있는 데이터 요소가 다른 색으로 표시될 수 있다는 단점이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="903df-112">As a side effect, when multiple pie charts are displayed in a report, the pie charts may display different colors for data points that have the same category grouping.</span></span> <span data-ttu-id="903df-113">이 문제를 해결하려면 개별 데이터 값 대신 범주 그룹에 매핑되는 색을 각각 정의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="903df-113">To resolve this, you need to define individual colors that map to a category group instead of individual data values.</span></span> <span data-ttu-id="903df-114">이 방법은 셰이프 차트가 테이블 또는 행렬의 스파크라인인지 아니면 보고서 자체의 셰이프 차트인지에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="903df-114">How you do this depends on if the shape charts are sparklines in a table or matrix, or if they are shape charts in the report itself.</span></span>  
  
 <span data-ttu-id="903df-115">범례는 계열과 연결되므로 계열에 대해 지정한 색이 범례에 자동으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="903df-115">The legend is connected to the series, so any color you specify for the series will automatically be shown on the legend.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-specify-consistent-colors-across-multiple-sparkline-shape-charts-in-a-table-or-matrix"></a><span data-ttu-id="903df-116">테이블 또는 행렬에서 여러 스파크라인 셰이프 차트에 일관된 색을 지정하려면</span><span class="sxs-lookup"><span data-stu-id="903df-116">To specify consistent colors across multiple sparkline shape charts in a table or matrix</span></span>  
  
1.  <span data-ttu-id="903df-117">차트를 클릭하여 차트 데이터 창을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="903df-117">Click the chart to display the Chart Data pane.</span></span>  
  
2.  <span data-ttu-id="903df-118">**범주 그룹** 영역에서 범주를 마우스 오른쪽 단추로 클릭한 다음 **범주 그룹 속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="903df-118">In the **Category Groups** area, right-click a category and click **Category Group Properties**.</span></span>  
  
3.  <span data-ttu-id="903df-119">일반 탭의 **다음 위치의 그룹 동기화** 상자에서 색을 동기화할 범주의 이름을 클릭하고 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="903df-119">On the General tab, in the **Synchronize groups in** box, click the name of the category for which you would like to synchronize colors, and then click **OK**.</span></span>  
  
### <a name="to-specify-consistent-colors-across-multiple-shape-charts"></a><span data-ttu-id="903df-120">여러 셰이프 차트에 일관된 색을 지정하려면</span><span class="sxs-lookup"><span data-stu-id="903df-120">To specify consistent colors across multiple shape charts</span></span>  
  
1.  <span data-ttu-id="903df-121">보고서 본문 바깥쪽을 마우스 오른쪽 단추로 클릭하고 **보고서 속성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="903df-121">Right-click outside the body of the report, and select **Report Properties**.</span></span>  
  
2.  <span data-ttu-id="903df-122">**코드**에서 입력란에 다음 코드를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="903df-122">In **Code**, type the following code into the textbox.</span></span>  
  
    ```  
    Private colorPalette As String() = {"Color1", "Color2", "Color3"}  
    Private count As Integer = 0  
    Private mapping As New System.Collections.Hashtable()  
    Public Function GetColor(ByVal groupingValue As String) As String  
        If mapping.ContainsKey(groupingValue) Then  
            Return mapping(groupingValue)  
        End If  
        Dim c As String = colorPalette(count Mod colorPalette.Length)  
        count = count + 1  
        mapping.Add(groupingValue, c)  
        Return c  
    End Function  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="903df-123">"Color1" 문자열을 원하는 식으로 바꾸어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="903df-123">You will need to replace the "Color1" strings with your own colors.</span></span> <span data-ttu-id="903df-124">"Red"와 같은 명명된 색을 사용하거나 색을 나타내는 6자리 16진수 값(예: 검정의 경우 "#FFFFFF")을 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="903df-124">You can use named colors, for example "Red", or you can use six-digit hexadecimal value that represent the color, such as "#FFFFFF" for black.</span></span> <span data-ttu-id="903df-125">4가지 이상의 색을 정의한 경우 배열에 있는 색 수가 셰이프 차트의 요소 수와 일치하도록 색 배열을 확장해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="903df-125">If you have more than three colors defined, you will need to extend the array of colors so that the number of colors in the array matches the number of points in your shape chart.</span></span> <span data-ttu-id="903df-126">명명된 색이나 16진수 색 표현이 포함된 쉼표로 구분된 문자열 값 목록을 지정하여 배열에 새로운 색을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="903df-126">You can add new colors to the array by specifying a comma-separated list of string values that contain named colors or hexadecimal representations of colors.</span></span>  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
4.  <span data-ttu-id="903df-127">셰이프 차트를 마우스 오른쪽 단추로 클릭하고 **계열 속성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="903df-127">Right-click on the shape chart and select **Series Properties**.</span></span>  
  
5.  <span data-ttu-id="903df-128">**채우기**에서 **식** (*fx*) 단추를 클릭하여 **색** 속성에 대한 식을 편집합니다.</span><span class="sxs-lookup"><span data-stu-id="903df-128">In **Fill**, click the **Expression** (*fx*) button to edit the expression for the **Color** property.</span></span>  
  
6.  <span data-ttu-id="903df-129">다음 식을 입력합니다. 여기서 "MyCategoryField"는 **범주 그룹** 영역에 표시되는 필드입니다.</span><span class="sxs-lookup"><span data-stu-id="903df-129">Type the following expression, where "MyCategoryField" is the field that is displayed in the **Category Groups** area:</span></span>  
  
    ```  
    =Code.GetColor(Fields!MyCategoryField)  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="903df-130">참고 항목</span><span class="sxs-lookup"><span data-stu-id="903df-130">See Also</span></span>  
 <span data-ttu-id="903df-131">[차트에서 계열 색 서식 지정&#40;보고서 작성기 및 SSRS&#41;](formatting-series-colors-on-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="903df-131">[Formatting Series Colors on a Chart &#40;Report Builder and SSRS&#41;](formatting-series-colors-on-a-chart-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="903df-132">[차트에 3D 가장자리, 볼록 및 질감 스타일 추가&#40;보고서 작성기 및 SSRS&#41;](chart-effects-add-bevel-emboss-or-texture-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="903df-132">[Add Bevel, Emboss, and Texture Styles to a Chart &#40;Report Builder and SSRS&#41;](chart-effects-add-bevel-emboss-or-texture-report-builder.md) </span></span>  
 <span data-ttu-id="903df-133">[색상표를 사용하여 차트에 대한 색 정의&#40;보고서 작성기 및 SSRS&#41;](define-colors-on-a-chart-using-a-palette-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="903df-133">[Define Colors on a Chart Using a Palette &#40;Report Builder and SSRS&#41;](define-colors-on-a-chart-using-a-palette-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="903df-134">[차트 &#40;보고서 작성기 및 SSRS에 빈 요소를 추가&#41;](add-empty-points-to-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="903df-134">[Add Empty Points to the Chart &#40;Report Builder and SSRS&#41;](add-empty-points-to-a-chart-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="903df-135">[셰이프 차트&#40;보고서 작성기 및 SSRS&#41;](charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="903df-135">[Shape Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="903df-136">[동일한 데이터 세트에 여러 데이터 영역 연결&#40;보고서 작성기 및 SSRS&#41;](linking-multiple-data-regions-to-the-same-dataset-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="903df-136">[Linking Multiple Data Regions to the Same Dataset &#40;Report Builder and SSRS&#41;](linking-multiple-data-regions-to-the-same-dataset-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="903df-137">[중첩된 데이터 영역&#40;보고서 작성기 및 SSRS&#41;](nested-data-regions-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="903df-137">[Nested Data Regions &#40;Report Builder and SSRS&#41;](nested-data-regions-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="903df-138">스파크라인 및 데이터 막대&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="903df-138">Sparklines and Data Bars &#40;Report Builder and SSRS&#41;</span></span>](sparklines-and-data-bars-report-builder-and-ssrs.md)  
  
  
