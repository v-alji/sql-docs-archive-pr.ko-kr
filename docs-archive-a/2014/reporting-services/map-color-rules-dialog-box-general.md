---
title: 지도 색 규칙 대화 상자, 일반 | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10541"
- sql12.rtp.rptdesigner.shared.mapcolorrulesgeneral.f1
ms.assetid: 14ff5fc1-4cf8-4a45-9d98-47a1bf1c52c4
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 0dffc6c0b31400cb4eb9cecbbada1a52f8f41443
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660334"
---
# <a name="map-color-rules-dialog-box-general"></a><span data-ttu-id="9fc94-102">지도 색 규칙 대화 상자, 일반</span><span class="sxs-lookup"><span data-stu-id="9fc94-102">Map Color Rules Dialog Box, General</span></span>
  <span data-ttu-id="9fc94-103">**색 규칙 속성** 대화 상자에서 **일반** 을 선택하여 이 계층의 지도 요소에 대한 색 옵션을 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9fc94-103">Select **General** on the **Color Rules Properties** dialog box to define color options for map elements on this layer.</span></span> <span data-ttu-id="9fc94-104">지도 요소에는 다각형, 선 및 점이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="9fc94-104">Map elements include polygons, lines, and points.</span></span> <span data-ttu-id="9fc94-105">공간 데이터 기반의 지도 요소와 데이터 세트 필드 또는 공간 데이터 원본 필드의 분석 데이터 간 관계를 만든 경우 색 규칙을 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9fc94-105">Color rules can be applied when you have created a relationship between map elements based on spatial data and analytical data from a dataset field or from a spatial data source field.</span></span>  
  
 <span data-ttu-id="9fc94-106">서로 다른 기본 색과 보조 색으로 장식 그라데이션을 지정하여 계층의 모든 지도 요소를 표시하려면 지도 다각형 속성 대화 상자의 **채우기** 페이지를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="9fc94-106">To display all map elements on a layer by specifying a decorative gradient with different primary and secondary colors, use the **Fill** page of the Map Polygon Properties Dialog Box.</span></span> <span data-ttu-id="9fc94-107">색 규칙은 계층의 표시 속성보다 우선합니다.</span><span class="sxs-lookup"><span data-stu-id="9fc94-107">Color rules take precedence over display properties for a layer.</span></span> <span data-ttu-id="9fc94-108">자세한 내용은 [지도 또는 지도 계층의 데이터 및 표시 사용자 지정&#40;보고서 작성기 및 SSRS&#41;](report-design/customize-the-data-and-display-of-a-map-or-map-layer-report-builder-and-ssrs.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9fc94-108">For more information, see [Customize the Data and Display of a Map or Map Layer &#40;Report Builder and SSRS&#41;](report-design/customize-the-data-and-display-of-a-map-or-map-layer-report-builder-and-ssrs.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="9fc94-109">옵션</span><span class="sxs-lookup"><span data-stu-id="9fc94-109">Options</span></span>  
 <span data-ttu-id="9fc94-110">**템플릿 스타일 적용**</span><span class="sxs-lookup"><span data-stu-id="9fc94-110">**Apply template style**</span></span>  
 <span data-ttu-id="9fc94-111">마법사에서 선택하거나 다각형, 선 또는 점 계층 속성에서 설정한 테마에 따라 색을 사용하려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="9fc94-111">Select this option to use color based on the theme that was chosen in the wizard or set in the Polygon, Line, or Point layer properties.</span></span> <span data-ttu-id="9fc94-112">테마에 따라 지도의 색, 글꼴 및 테두리에 대한 기본 옵션이 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="9fc94-112">A theme sets default options for color, font, and borders for the map.</span></span> <span data-ttu-id="9fc94-113">이 옵션의 경우 각 지도 요소에 색을 할당하기 위해 규칙이 적용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9fc94-113">For this option, no rule is applied to assign colors to each map element.</span></span>  
  
 <span data-ttu-id="9fc94-114">**색상표를 사용하여 데이터 시각화**</span><span class="sxs-lookup"><span data-stu-id="9fc94-114">**Visualize data by using color palette**</span></span>  
 <span data-ttu-id="9fc94-115">특정 색상표에서 색을 사용하여 분석 데이터를 시각화하려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="9fc94-115">Select this option to visualize analytical data by using colors from a specific color palette.</span></span>  
  
 <span data-ttu-id="9fc94-116">**색 범위를 사용하여 데이터 시각화**</span><span class="sxs-lookup"><span data-stu-id="9fc94-116">**Visualize data by using color ranges**</span></span>  
 <span data-ttu-id="9fc94-117">각 지도 요소에 색 범위를 사용하여 분석 데이터를 시각화하려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="9fc94-117">Select this option to visualize analytical data by using a range of colors for each map element.</span></span> <span data-ttu-id="9fc94-118">예를 들어 빨강을 시작 색으로, 노랑을 중간 색으로, 녹색을 마지막 색으로 지정하는 경우 하위 범위의 값은 빨강이고, 중간 범위의 값은 노랑이고, 상위 범위의 값은 녹색입니다.</span><span class="sxs-lookup"><span data-stu-id="9fc94-118">For example, when you specify Red as a start color, Yellow as a middle color, and Green as an end color, values in the low range are Red, values in the middle range are Yellow, and values in the top range are Green.</span></span>  
  
 <span data-ttu-id="9fc94-119">**사용자 지정 색을 사용하여 데이터 시각화**</span><span class="sxs-lookup"><span data-stu-id="9fc94-119">**Visualize data by using custom colors**</span></span>  
 <span data-ttu-id="9fc94-120">색 목록을 직접 지정하여 분석 데이터를 시각화하려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="9fc94-120">Select this option to visualize analytical data by specifying your own list of colors.</span></span>  
  
 <span data-ttu-id="9fc94-121">**데이터 필드**</span><span class="sxs-lookup"><span data-stu-id="9fc94-121">**Data field**</span></span>  
 <span data-ttu-id="9fc94-122">이 옵션은 **데이터 시각화** 옵션 중 하나를 선택하면 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="9fc94-122">This option appears when you select one of the **Visualize data** options.</span></span>  
  
 <span data-ttu-id="9fc94-123">드롭다운 목록에서 사용할 분석 데이터 필드를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="9fc94-123">Select the analytical data field to use from the drop-down list.</span></span> <span data-ttu-id="9fc94-124">공간 데이터의 원본에 따라 목록에는 공간 데이터 원본의 필드와 공간 데이터와 분석 데이터 간의 관계가 있는 보고서 데이터 세트의 필드가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="9fc94-124">Depending on the source of spatial data, the list displays fields from the spatial data source and from a report dataset that has a relationship between the spatial data and analytical data.</span></span> <span data-ttu-id="9fc94-125">이러한 관계를 만들려면 선택된 지도 계층에 대한 분석 데이터 페이지에서 데이터 옵션을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="9fc94-125">To create such a relationship, set the data options on the Analytical Data page for the selected map layer.</span></span>  
  
 <span data-ttu-id="9fc94-126">**색**</span><span class="sxs-lookup"><span data-stu-id="9fc94-126">**Palette**</span></span>  
 <span data-ttu-id="9fc94-127">색상표의 이름을 입력하거나 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="9fc94-127">Type or select the name of the color palette.</span></span>  
  
 <span data-ttu-id="9fc94-128">**시작 색**</span><span class="sxs-lookup"><span data-stu-id="9fc94-128">**Start color**</span></span>  
 <span data-ttu-id="9fc94-129">데이터 범위의 하위에 있는 데이터에 사용할 색을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="9fc94-129">Specify the color to use for data at the low end of the data range.</span></span>  
  
 <span data-ttu-id="9fc94-130">**중간 색**</span><span class="sxs-lookup"><span data-stu-id="9fc94-130">**Middle color**</span></span>  
 <span data-ttu-id="9fc94-131">데이터 범위의 중간에 있는 데이터에 사용할 색을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="9fc94-131">Specify the color to use for data in the middle of the data range.</span></span> <span data-ttu-id="9fc94-132">이 범위를 제거하려면 **색 없음** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="9fc94-132">Select **No Color** to remove this range.</span></span>  
  
 <span data-ttu-id="9fc94-133">**마지막 색**</span><span class="sxs-lookup"><span data-stu-id="9fc94-133">**End color**</span></span>  
 <span data-ttu-id="9fc94-134">데이터 범위의 상위에 있는 데이터에 사용할 색을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="9fc94-134">Specify the color to use for data at the high end of the data range.</span></span>  
  
 <span data-ttu-id="9fc94-135">**추가**</span><span class="sxs-lookup"><span data-stu-id="9fc94-135">**Add**</span></span>  
 <span data-ttu-id="9fc94-136">색 규칙의 색을 직접 지정하려면 **추가** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9fc94-136">Click **Add** to specify your own colors for the color rule.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9fc94-137">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9fc94-137">See Also</span></span>  
 <span data-ttu-id="9fc94-138">[지도&#40;보고서 작성기 및 SSRS&#41;](report-design/maps-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="9fc94-138">[Maps &#40;Report Builder and SSRS&#41;](report-design/maps-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="9fc94-139">지도 범례, 색 눈금 및 관련 규칙 변경&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="9fc94-139">Change Map Legends, Color Scale, and Associated Rules &#40;Report Builder and SSRS&#41;</span></span>](report-design/change-map-legends-color-scale-and-associated-rules-report-builder-and-ssrs.md)  
  
  
