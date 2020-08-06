---
title: 지도 뷰포트 속성 대화 상자, 가운데 맞춤 및 확대/축소 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptdesigner.mapviewport.centerandzoom.f1
- "10506"
ms.assetid: 642a06f5-293f-48e0-97a6-1489dbefa719
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 913c00773abf71ca627b8cc2a94a873484e8ab30
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648851"
---
# <a name="map-viewport-properties-dialog-box-center-and-zoom"></a><span data-ttu-id="4d8a7-102">지도 뷰포트 속성 대화 상자, 중심 및 확대/축소</span><span class="sxs-lookup"><span data-stu-id="4d8a7-102">Map Viewport Properties Dialog Box, Center and Zoom</span></span>
  <span data-ttu-id="4d8a7-103">**지도 뷰포트 속성** 대화 상자의 **중심 및 확대/축소** 를 선택하여 지도의 중심 보기와 확대/축소 비율을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4d8a7-103">Select **Center and Zoom** for the **Map Viewport Properties** dialog box to set the center view and zoom factor for a map.</span></span> <span data-ttu-id="4d8a7-104">지도 데이터 원본과 보고서에 포함할 지도의 경계를 지정한 후 보기 중심과 확대/축소 비율을 지정하여 지도 표시를 세부적으로 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4d8a7-104">After you specify a map data source and the boundaries of the map that you want to include in your report, you can specify the view center and the zoom factor to further control the map display.</span></span> <span data-ttu-id="4d8a7-105">옵션은 중심 및 확대/축소 값을 지정하는 데 사용하는 방법에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="4d8a7-105">Options change depending on which method you use to specify the center and zoom values.</span></span> <span data-ttu-id="4d8a7-106">옵션의 값을 설정하는 식을 편집하려면 **식** 단추(*fx*)를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4d8a7-106">Click the **Expression** (*fx*) button to edit an expression that sets the value of the option.</span></span>  
  
## <a name="options"></a><span data-ttu-id="4d8a7-107">옵션</span><span class="sxs-lookup"><span data-stu-id="4d8a7-107">Options</span></span>  
 <span data-ttu-id="4d8a7-108">**보기 중심 및 확대/축소 수준 설정**</span><span class="sxs-lookup"><span data-stu-id="4d8a7-108">**Set a view center and zoom level**</span></span>  
 <span data-ttu-id="4d8a7-109">보기 중심과 확대/축소 수준에 대한 사용자 지정 값을 지정하려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="4d8a7-109">Choose this option to specify custom values for the view center and the zoom level.</span></span>  
  
 <span data-ttu-id="4d8a7-110">**지도 계층을 표시하도록 지도 가운데 맞춤**</span><span class="sxs-lookup"><span data-stu-id="4d8a7-110">**Center map to show a map layer**</span></span>  
 <span data-ttu-id="4d8a7-111">계층을 지정하고 지도 데이터를 기준으로 보기를 자동으로 가운데에 맞추려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="4d8a7-111">Choose this option to specify a layer and automatically center the view on its map data.</span></span> <span data-ttu-id="4d8a7-112">예를 들어 LineLayer1을 기준으로 보기를 가운데에 맞춥니다.</span><span class="sxs-lookup"><span data-stu-id="4d8a7-112">For example, center the view on LineLayer1.</span></span>  
  
 <span data-ttu-id="4d8a7-113">**포함 지도 요소를 표시하도록 지도 가운데 맞춤**</span><span class="sxs-lookup"><span data-stu-id="4d8a7-113">**Center map to show an embedded map element**</span></span>  
 <span data-ttu-id="4d8a7-114">특정 데이터 바인딩된 지도 요소를 기준으로 보기를 가운데에 맞추려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="4d8a7-114">Choose this option to center the view on a specific data-bound map element.</span></span> <span data-ttu-id="4d8a7-115">이 옵션을 지정하려면 공간 데이터가 분석 데이터와 관계를 맺고 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4d8a7-115">The spatial data must have a relationship with analytical data to specify this option.</span></span>  
  
 <span data-ttu-id="4d8a7-116">예를 들어 일치 필드의 이름이 [City]이고 일치 값이 "Seattle"인 지도 요소를 기준으로 보기를 가운데에 맞춥니다.</span><span class="sxs-lookup"><span data-stu-id="4d8a7-116">For example, center the view on the map element where the name of the match field is [City] and the match value is "Seattle".</span></span>  
  
 <span data-ttu-id="4d8a7-117">**모든 데이터 바인딩 지도 요소를 표시하도록 지도 가운데 맞춤**</span><span class="sxs-lookup"><span data-stu-id="4d8a7-117">**Center map to show all data-bound map elements**</span></span>  
 <span data-ttu-id="4d8a7-118">계층의 모든 지도 요소를 기준으로 보기를 가운데에 맞추려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="4d8a7-118">Choose this option to center the view on all map elements in the layer.</span></span> <span data-ttu-id="4d8a7-119">이 옵션을 지정하려면 공간 데이터가 분석 데이터와 관계를 맺고 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4d8a7-119">The spatial data must have a relationship with analytical data to specify this option.</span></span>  
  
 <span data-ttu-id="4d8a7-120">예를 들어 도시를 표시하는 다각형 거품형 계층을 기준으로 보기를 가운데에 맞춥니다. 거품 크기는 인구와 관련되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4d8a7-120">For example, center the view on the polygon bubble layer that shows cities and the bubble size is related to population.</span></span> <span data-ttu-id="4d8a7-121">뷰포트의 중심을 계산할 때 일치하는 인구 값이 있는 도시만 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="4d8a7-121">Only those cities with a matching population value are included when calculating the center for the viewport.</span></span>  
  
 <span data-ttu-id="4d8a7-122">**중심 및 확대/축소 옵션**</span><span class="sxs-lookup"><span data-stu-id="4d8a7-122">**Center and zoom options**</span></span>  
 <span data-ttu-id="4d8a7-123">보기 중심과 확대/축소 수준을 지정하려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="4d8a7-123">Select an option to specify the view center and zoom level.</span></span>  
  
 <span data-ttu-id="4d8a7-124">**보기 중심(X) %**</span><span class="sxs-lookup"><span data-stu-id="4d8a7-124">**View center (X) %**</span></span>  
 <span data-ttu-id="4d8a7-125">가로 좌표입니다.</span><span class="sxs-lookup"><span data-stu-id="4d8a7-125">The horizontal coordinate.</span></span> <span data-ttu-id="4d8a7-126">기본값 50%는</span><span class="sxs-lookup"><span data-stu-id="4d8a7-126">The default value, 50%.</span></span> <span data-ttu-id="4d8a7-127">최소 가로 값과 최대 가로 값 사이의 중간점에서 보기를 가운데에 맞춥니다.</span><span class="sxs-lookup"><span data-stu-id="4d8a7-127">centers the view at the midpoint between the minimum and maximum horizontal values.</span></span>  
  
 <span data-ttu-id="4d8a7-128">**보기 중심(Y) %**</span><span class="sxs-lookup"><span data-stu-id="4d8a7-128">**View center (Y) %**</span></span>  
 <span data-ttu-id="4d8a7-129">세로 좌표입니다.</span><span class="sxs-lookup"><span data-stu-id="4d8a7-129">The vertical coordinate.</span></span> <span data-ttu-id="4d8a7-130">기본값 50%는 최소 세로 값과 최대 세로 값 사이의 중간점에서 보기를 가운데에 맞춥니다.</span><span class="sxs-lookup"><span data-stu-id="4d8a7-130">The default value, 50%, centers the view at the midpoint between the minimum and maximum vertical values.</span></span>  
  
 <span data-ttu-id="4d8a7-131">**확대/축소 수준(%)**</span><span class="sxs-lookup"><span data-stu-id="4d8a7-131">**Zoom level (%)**</span></span>  
 <span data-ttu-id="4d8a7-132">확대/축소 비율입니다.</span><span class="sxs-lookup"><span data-stu-id="4d8a7-132">The zoom factor.</span></span> <span data-ttu-id="4d8a7-133">기본값 100%는 확대하지 않음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="4d8a7-133">The default value, 100%, indicates no magnification.</span></span>  
  
 <span data-ttu-id="4d8a7-134">**다음 계층을 기준으로 보기 가운데 맞춤**</span><span class="sxs-lookup"><span data-stu-id="4d8a7-134">**Center view on this layer**</span></span>  
 <span data-ttu-id="4d8a7-135">계층의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="4d8a7-135">Specify the name of the layer.</span></span>  
  
 <span data-ttu-id="4d8a7-136">**다음 조건에 맞는 지도 요소로 보기 가운데 맞춤**</span><span class="sxs-lookup"><span data-stu-id="4d8a7-136">**Center view on the map element that matches this condition**</span></span>  
 <span data-ttu-id="4d8a7-137">표시되는 읽기 전용 필드는 지도 데이터와 분석 데이터를 일치시키는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="4d8a7-137">The read-only field that is displayed is used to match map data and analytical data.</span></span> <span data-ttu-id="4d8a7-138">일치시킬 값을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="4d8a7-138">Specify the value that you want to match on.</span></span> <span data-ttu-id="4d8a7-139">보기는 이 지도 요소를 기준으로 자동으로 가운데에 맞춤됩니다.</span><span class="sxs-lookup"><span data-stu-id="4d8a7-139">The view automatically centers on this map element.</span></span> <span data-ttu-id="4d8a7-140">예를 들어 NAME = TEXAS입니다.</span><span class="sxs-lookup"><span data-stu-id="4d8a7-140">For example, NAME = TEXAS.</span></span> <span data-ttu-id="4d8a7-141">기본적으로 조건의 데이터 형식은 문자열이고 대/소문자를 구분하여 일치시킵니다.</span><span class="sxs-lookup"><span data-stu-id="4d8a7-141">By default, the data type for the condition is String and the match is case-sensitive.</span></span>  
  
 <span data-ttu-id="4d8a7-142">데이터 형식이 다른 필드에서 일치시키려면 해당 데이터 형식으로 계산되는 식을 작성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4d8a7-142">To match on a field that has a different data type, you must write an expression that evaluates to that data type.</span></span> <span data-ttu-id="4d8a7-143">예를 들어 일치 필드가 정수로 저장된 5자리 우편 번호인 경우 우편 번호 98053을 지정하려면 식 =98053을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4d8a7-143">For example, if the match field is a 5 digit postal code that is stored as an integer, then to specify the postal code 98053, you must use the expression =98053.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d8a7-144">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4d8a7-144">See Also</span></span>  
 [<span data-ttu-id="4d8a7-145">지도&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="4d8a7-145">Maps &#40;Report Builder and SSRS&#41;</span></span>](report-design/maps-report-builder-and-ssrs.md)  
  
  
