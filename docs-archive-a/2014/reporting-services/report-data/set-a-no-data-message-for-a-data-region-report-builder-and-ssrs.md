---
title: 데이터 영역에 대한 데이터 없음 메시지 설정(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 4b194714-46f7-4f0e-9632-7f89d9600762
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 9ed38ef14eb8f89753b4b3d7af3324ef0e88fa52
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730188"
---
# <a name="set-a-no-data-message-for-a-data-region-report-builder-and-ssrs"></a><span data-ttu-id="d14ab-102">데이터 영역에 대한 데이터 없음 메시지 설정(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="d14ab-102">Set a No Data Message for a Data Region (Report Builder and SSRS)</span></span>
  <span data-ttu-id="d14ab-103">렌더링된 보고서에서 데이터가 없는 데이터 영역의 자리에 텍스트가 표시되도록 지정하려면 테이블, 행렬 또는 목록 데이터 영역에 대해 NoRowsMessage 속성을 설정하거나 차트 데이터 영역에 대해 NoDataMessage를 설정하거나, 지도의 색 눈금에 대해 NoDataText를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="d14ab-103">When you want to specify text to show in the rendered report in place of a data region that has no data, set the NoRowsMessage property for a table, matrix, or list data region, the NoDataMessage for a chart data region, and the NoDataText for the color scale for a map.</span></span> <span data-ttu-id="d14ab-104">보고서 처리기는 런타임에 보고서의 각 데이터 세트에 대한 쿼리를 실행하며 해당 데이터 세트 쿼리에서 결과 집합이 생성되지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d14ab-104">At run time, the report processor runs the query for each dataset in a report and the dataset query may produce no result set.</span></span> <span data-ttu-id="d14ab-105">빈 데이터 세트에 바인딩된 데이터 영역의 경우 빈 데이터 영역을 표시하는 대신 텍스트를 지정하여 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d14ab-105">For a data region bound to an empty dataset, you can specify text to display instead of displaying an empty data region.</span></span> <span data-ttu-id="d14ab-106">또한 런타임에, 하위 보고서의 데이터 세트에 데이터가 없는 경우 하위 보고서의 NoRowsMessage 속성을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d14ab-106">You can also set the NoRowsMessage property for a subreport when no datasets in the subreport have data at run time.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-set-the-norowsmessage-property-for-a-table-matrix-or-list"></a><span data-ttu-id="d14ab-107">테이블, 행렬 또는 목록에 대해 NoRowsMessage 속성을 설정하려면</span><span class="sxs-lookup"><span data-stu-id="d14ab-107">To set the NoRowsMessage property for a table, matrix, or list</span></span>  
  
1.  <span data-ttu-id="d14ab-108">디자인 뷰에서 디자인 화면의 테이블, 행렬 또는 목록 데이터 영역이나 하위 보고서를 클릭하여 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d14ab-108">In Design view, click the table, matrix, or list data region or subreport on the design surface to select it.</span></span> <span data-ttu-id="d14ab-109">선택한 항목의 속성이 속성 창에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="d14ab-109">The Properties pane displays the properties for the selected item.</span></span>  
  
2.  <span data-ttu-id="d14ab-110">속성 창의 속성 필드에 메시지로 표시할 텍스트를 입력 합니다 `NoRowsMessage` .</span><span class="sxs-lookup"><span data-stu-id="d14ab-110">In the Properties pane, type the text that you want to display as a message in `NoRowsMessage` property field.</span></span>  
  
     <span data-ttu-id="d14ab-111">또는 드롭다운 목록에서 **식** 을 클릭하여 **식** 대화 상자를 열고 식을 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="d14ab-111">Alternatively, from the drop-down list, click **Expression** to open the **Expression** dialog box and create an expression.</span></span>  
  
### <a name="to-set-the-nodatamessage-property-for-a-chart"></a><span data-ttu-id="d14ab-112">차트에 대해 NoDataMessage 속성을 설정하려면</span><span class="sxs-lookup"><span data-stu-id="d14ab-112">To set the NoDataMessage property for a chart</span></span>  
  
1.  <span data-ttu-id="d14ab-113">디자인 뷰에서 디자인 화면에 있는 차트를 클릭하여 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d14ab-113">In Design view, click the chart on the design surface to select it.</span></span> <span data-ttu-id="d14ab-114">선택한 항목의 속성이 속성 창에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="d14ab-114">The Properties pane displays the properties for the selected item.</span></span>  
  
2.  <span data-ttu-id="d14ab-115">속성 창에서 노드를 확장 `NoDataMessage` 합니다.</span><span class="sxs-lookup"><span data-stu-id="d14ab-115">In the Properties pane, expand the node for `NoDataMessage`.</span></span>  
  
3.  <span data-ttu-id="d14ab-116">속성 필드에 메시지로 표시할 텍스트를 **캡션**에 입력 합니다 `NoDataMessage` .</span><span class="sxs-lookup"><span data-stu-id="d14ab-116">In **Caption**, type the text that you want to display as a message in `NoDataMessage` property field.</span></span>  
  
     <span data-ttu-id="d14ab-117">또는 드롭다운 목록에서 **식** 을 클릭하여 **식** 대화 상자를 열고 식을 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="d14ab-117">Alternatively, from the drop-down list, click **Expression** to open the **Expression** dialog box and create an expression.</span></span>  
  
### <a name="to-set-the-norowsmessage-for-a-subreport"></a><span data-ttu-id="d14ab-118">하위 보고서에 대해 NoRowsMessage를 설정하려면</span><span class="sxs-lookup"><span data-stu-id="d14ab-118">To set the NoRowsMessage for a subreport</span></span>  
  
1.  <span data-ttu-id="d14ab-119">디자인 뷰에서 디자인 화면에 있는 하위 보고서를 클릭하여 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d14ab-119">In Design view, click the subreport on the design surface to select it.</span></span> <span data-ttu-id="d14ab-120">선택한 항목의 속성이 속성 창에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="d14ab-120">The Properties pane displays the properties for the selected item.</span></span>  
  
2.  <span data-ttu-id="d14ab-121">속성 창의 속성 필드에 메시지로 표시할 텍스트를 입력 합니다 `NoRowsMessage` .</span><span class="sxs-lookup"><span data-stu-id="d14ab-121">In the Properties pane, type the text that you want to display as a message in `NoRowsMessage` property field.</span></span>  
  
     <span data-ttu-id="d14ab-122">또는 드롭다운 목록에서 **식** 을 클릭하여 **식** 대화 상자를 열고 식을 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="d14ab-122">Alternatively, from the drop-down list, click **Expression** to open the **Expression** dialog box and create an expression.</span></span>  
  
### <a name="to-set-the-nodatatext-property-for-a-color-scale-for-a-map"></a><span data-ttu-id="d14ab-123">지도의 색 눈금에 NoDataText 속성을 설정하려면</span><span class="sxs-lookup"><span data-stu-id="d14ab-123">To set the NoDataText property for a color scale for a map</span></span>  
  
1.  <span data-ttu-id="d14ab-124">디자인 뷰에서 지도에 있는 색 눈금을 클릭하여 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d14ab-124">In Design view, click the color scale on the map to select it.</span></span> <span data-ttu-id="d14ab-125">선택한 항목의 속성이 속성 창에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="d14ab-125">The Properties pane displays the properties for the selected item.</span></span>  
  
2.  <span data-ttu-id="d14ab-126">속성 창의에서 `NoDataText` 데이터 값이 없는 색의 레이블로 표시할 텍스트를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="d14ab-126">In the Properties pane, in `NoDataText`, type the text that you want to display as a label for colors with no data value.</span></span>  
  
     <span data-ttu-id="d14ab-127">또는 드롭다운 목록에서 **식** 을 클릭하여 **식** 대화 상자를 열고 식을 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="d14ab-127">Alternatively, from the drop-down list, click **Expression** to open the **Expression** dialog box and create an expression.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d14ab-128">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d14ab-128">See Also</span></span>  
 <span data-ttu-id="d14ab-129">[하위 보고서&#40;보고서 작성기 및 SSRS&#41;](../report-design/subreports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="d14ab-129">[Subreports &#40;Report Builder and SSRS&#41;](../report-design/subreports-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="d14ab-130">[테이블, 행렬 및 목록&#40;보고서 작성기 및 SSRS&#41;](../report-design/create-invoices-and-forms-with-lists-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="d14ab-130">[Tables, Matrices, and Lists &#40;Report Builder and SSRS&#41;](../report-design/create-invoices-and-forms-with-lists-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="d14ab-131">[차트&#40;보고서 작성기 및 SSRS&#41;](../report-design/charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="d14ab-131">[Charts &#40;Report Builder and SSRS&#41;](../report-design/charts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="d14ab-132">[지도&#40;보고서 작성기 및 SSRS&#41;](../report-design/maps-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="d14ab-132">[Maps &#40;Report Builder and SSRS&#41;](../report-design/maps-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="d14ab-133">하위 보고서&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="d14ab-133">Subreports &#40;Report Builder and SSRS&#41;</span></span>](../report-design/subreports-report-builder-and-ssrs.md)  
  
  
