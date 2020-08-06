---
title: 지도 뷰포트 속성 대화 상자, 일반 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptdesigner.mapviewport.general.f1
- "10505"
ms.assetid: 6c9c773e-5c56-4571-95ed-8a157cfdfe52
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d760d6a0572cbbd1bd948eab382c0727eb276c4c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639392"
---
# <a name="map-viewport-properties-dialog-box-general"></a><span data-ttu-id="e196b-102">지도 뷰포트 속성 대화 상자, 일반</span><span class="sxs-lookup"><span data-stu-id="e196b-102">Map Viewport Properties Dialog Box, General</span></span>
  <span data-ttu-id="e196b-103">**지도 뷰포트 속성** 대화 상자에서 **일반** 을 선택하여 좌표계, 도법 및 경계 옵션을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e196b-103">Select **General** on the **Map Viewport Properties** dialog box to change the coordinate system, the projection, and the boundary options.</span></span>  
  
## <a name="options"></a><span data-ttu-id="e196b-104">옵션</span><span class="sxs-lookup"><span data-stu-id="e196b-104">Options</span></span>  
 <span data-ttu-id="e196b-105">**좌표계**</span><span class="sxs-lookup"><span data-stu-id="e196b-105">**Coordinate system**</span></span>  
 <span data-ttu-id="e196b-106">지도 데이터가 사용하는 좌표계의 유형을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e196b-106">Indicate the type of coordinate system that the map data uses.</span></span>  
  
-   <span data-ttu-id="e196b-107">**평면** 건물 계획과 같이 지도 데이터가 X 및 Y 좌표에 있는 경우 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e196b-107">**Planar** Choose this option when map data is in X and Y coordinates, for example, for building plans.</span></span>  
  
-   <span data-ttu-id="e196b-108">**지리** 도시 위치와 같이 지도 데이터가 경도 및 위도 좌표에 있는 경우 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e196b-108">**Geographic** Choose this option when map data is in longitude and latitude coordinates, for example, for city locations.</span></span>  
  
 <span data-ttu-id="e196b-109">**프로젝션**</span><span class="sxs-lookup"><span data-stu-id="e196b-109">**Projection**</span></span>  
 <span data-ttu-id="e196b-110">지리 좌표를 2차원 표면에 투영하는 데 사용할 방법을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e196b-110">Specify the method to use to project geographic coordinates onto a two-dimensional surface.</span></span> <span data-ttu-id="e196b-111">시각화하는 데이터와 호환되는 도법을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e196b-111">Choose a projection that is compatible with the data that you are visualizing.</span></span> <span data-ttu-id="e196b-112">도법의 영향을 받는 4가지 공간 속성은 영역, 모양, 거리 및 방향입니다.</span><span class="sxs-lookup"><span data-stu-id="e196b-112">The four spatial properties that are affected by projection are area, shape, distance, and direction.</span></span> <span data-ttu-id="e196b-113">지구를 보는 경우 도법에 적합한 선택은 보기 중심, 지도 경계 및 확대/축소 비율에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="e196b-113">For views of the earth, a good choice of projection depends on the center view, the map boundaries, and the zoom factor.</span></span>  
  
 <span data-ttu-id="e196b-114">아래에 있는 각 도법은 이러한 공간 속성 중 하나 이상을 유지합니다.</span><span class="sxs-lookup"><span data-stu-id="e196b-114">Each of the following projections preserves one or more of these spatial properties:</span></span>  
  
-   <span data-ttu-id="e196b-115">**등장방형** 경도와 위도를 사각형 좌표로 사용하려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e196b-115">**Equirectangular** Choose this option to use longitude and latitude as rectangular coordinates.</span></span>  
  
-   <span data-ttu-id="e196b-116">**메르카토르** 작은 지역의 경우, 적도 주위의 왜곡을 줄이려는 경우 또는 메르카토르 도법을 사용하는 기존 타일 계층이 포함된 지도 계층을 추가하려는 경우 널리 사용되는 이 도법을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e196b-116">**Mercator** Choose this popular projection for smaller areas, for less distortion around the equator, or when you want to add a map layer with an existing tile layer that uses the Mercator projection.</span></span>  
  
-   <span data-ttu-id="e196b-117">**로빈슨** 적도에서 극지방까지 걸쳐 있는 큰 지역의 왜곡을 줄이려는 경우 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e196b-117">**Robinson** Choose this option for less distortion of large areas that span from the equator to the poles.</span></span> <span data-ttu-id="e196b-118">1963년에 Arthur H. Robinson이 개발했습니다.</span><span class="sxs-lookup"><span data-stu-id="e196b-118">Developed by Arthur H. Robinson in 1963.</span></span>  
  
-   <span data-ttu-id="e196b-119">**파헤이** 적도에서 극지방까지 걸쳐 있는 큰 지역의 왜곡을 줄이려는 경우 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e196b-119">**Fahey** Choose this option for less distortion of large areas that span from the equator to the poles.</span></span> <span data-ttu-id="e196b-120">1975년에 Lawrence Fahey가 개발했습니다.</span><span class="sxs-lookup"><span data-stu-id="e196b-120">Developed by Lawrence Fahey in 1975.</span></span>  
  
-   <span data-ttu-id="e196b-121">**에케르트1** 위도에서 간격이 동일한 위도선을 사용하고 경도의 자오선에 직선을 사용하려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e196b-121">**Eckert1** Choose this option to use equally spaced parallels in latitude and straight lines for meridians in longitude.</span></span>  
  
-   <span data-ttu-id="e196b-122">**에케르트 3** 위도에서 간격이 동일한 위도선을 사용하고 경도의 자오선에 곡선을 사용하려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e196b-122">**Eckert3** Choose this option to use equally spaced parallels in latitude and curved lines for meridians in longitude.</span></span>  
  
-   <span data-ttu-id="e196b-123">**해머아이토프** 극지방 지도나 세계 지도의 경우 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e196b-123">**HammerAitoff** Choose this option for polar maps or world maps.</span></span>  
  
-   <span data-ttu-id="e196b-124">**바그너3** 세계 지도의 경우 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e196b-124">**Wagner3** Choose this option for world maps.</span></span>  
  
-   <span data-ttu-id="e196b-125">**본느** 지도책에 나타나는 대로 세계를 보려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e196b-125">**Bonne** Choose this option to view the world as it appears in an atlas.</span></span>  
  
 <span data-ttu-id="e196b-126">**페이지 나누기 옵션**</span><span class="sxs-lookup"><span data-stu-id="e196b-126">**Page break options**</span></span>  
 <span data-ttu-id="e196b-127">보고서 페이지에 내용을 맞추는 방법을 지정하는 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e196b-127">Select options to indicate how content is fitted to a report page.</span></span>  
  
 <span data-ttu-id="e196b-128">**경계 옵션**</span><span class="sxs-lookup"><span data-stu-id="e196b-128">**Boundary options**</span></span>  
 <span data-ttu-id="e196b-129">보고서에 표시되는 지도의 부분을 제어하려면 좌표의 하한과 상한을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e196b-129">Specify the lower and upper boundaries for coordinates to control which part of the map appears in the report.</span></span>  
  
 <span data-ttu-id="e196b-130">**최소 X**</span><span class="sxs-lookup"><span data-stu-id="e196b-130">**Minimum X**</span></span>  
 <span data-ttu-id="e196b-131">가장 작은 X 값입니다.</span><span class="sxs-lookup"><span data-stu-id="e196b-131">Lowest X value.</span></span> <span data-ttu-id="e196b-132">**평면** 에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e196b-132">Available for **Planar** only.</span></span>  
  
 <span data-ttu-id="e196b-133">**최대 X**</span><span class="sxs-lookup"><span data-stu-id="e196b-133">**Maximum X**</span></span>  
 <span data-ttu-id="e196b-134">가장 큰 X 값입니다.</span><span class="sxs-lookup"><span data-stu-id="e196b-134">Highest X value.</span></span> <span data-ttu-id="e196b-135">**평면** 에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e196b-135">Available for **Planar** only.</span></span>  
  
 <span data-ttu-id="e196b-136">**최소 Y**</span><span class="sxs-lookup"><span data-stu-id="e196b-136">**Minimum Y**</span></span>  
 <span data-ttu-id="e196b-137">가장 작은 Y 값입니다.</span><span class="sxs-lookup"><span data-stu-id="e196b-137">Lowest Y value.</span></span> <span data-ttu-id="e196b-138">**평면** 에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e196b-138">Available for **Planar** only.</span></span>  
  
 <span data-ttu-id="e196b-139">**최대 Y**</span><span class="sxs-lookup"><span data-stu-id="e196b-139">**Maximum Y**</span></span>  
 <span data-ttu-id="e196b-140">가장 큰 Y 값입니다.</span><span class="sxs-lookup"><span data-stu-id="e196b-140">Highest Y value.</span></span> <span data-ttu-id="e196b-141">**평면** 에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e196b-141">Available for **Planar** only.</span></span>  
  
 <span data-ttu-id="e196b-142">**최소 경도**</span><span class="sxs-lookup"><span data-stu-id="e196b-142">**Minimum Longitude**</span></span>  
 <span data-ttu-id="e196b-143">가장 작은 경도 값입니다.</span><span class="sxs-lookup"><span data-stu-id="e196b-143">Lowest longitude value.</span></span> <span data-ttu-id="e196b-144">**지리** 에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e196b-144">Available for **Geographic** only.</span></span>  
  
 <span data-ttu-id="e196b-145">**최대 경도**</span><span class="sxs-lookup"><span data-stu-id="e196b-145">**Maximum Longitude**</span></span>  
 <span data-ttu-id="e196b-146">가장 큰 경도 값입니다.</span><span class="sxs-lookup"><span data-stu-id="e196b-146">Highest longitude value.</span></span> <span data-ttu-id="e196b-147">**지리** 에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e196b-147">Available for **Geographic** only.</span></span>  
  
 <span data-ttu-id="e196b-148">**최소 위도**</span><span class="sxs-lookup"><span data-stu-id="e196b-148">**Minimum Latitude**</span></span>  
 <span data-ttu-id="e196b-149">가장 작은 위도 값입니다.</span><span class="sxs-lookup"><span data-stu-id="e196b-149">Lowest latitude value.</span></span> <span data-ttu-id="e196b-150">**지리** 에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e196b-150">Available for **Geographic** only.</span></span>  
  
 <span data-ttu-id="e196b-151">**최대 위도**</span><span class="sxs-lookup"><span data-stu-id="e196b-151">**Maximum Latitude**</span></span>  
 <span data-ttu-id="e196b-152">가장 큰 위도 값입니다.</span><span class="sxs-lookup"><span data-stu-id="e196b-152">Highest latitude value.</span></span> <span data-ttu-id="e196b-153">**지리** 에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e196b-153">Available for **Geographic** only.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e196b-154">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e196b-154">See Also</span></span>  
 [<span data-ttu-id="e196b-155">지도&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="e196b-155">Maps &#40;Report Builder and SSRS&#41;</span></span>](report-design/maps-report-builder-and-ssrs.md)  
  
  
