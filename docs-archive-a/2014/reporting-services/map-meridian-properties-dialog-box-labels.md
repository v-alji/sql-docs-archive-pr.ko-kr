---
title: 지도 자오선 속성 대화 상자, 레이블 | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptdesigner.mapmeridianproperties.labels.f1
- "10518"
ms.assetid: 47650a82-3b0c-4e32-8565-e9332bdcf4d6
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 146e2062185b4b4cd07ab791bd7552e9fd0064cc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741552"
---
# <a name="map-meridian-properties-dialog-box-labels"></a><span data-ttu-id="21837-102">지도 자오선 속성 대화 상자, 레이블</span><span class="sxs-lookup"><span data-stu-id="21837-102">Map Meridian Properties Dialog Box, Labels</span></span>
  <span data-ttu-id="21837-103">**MapMeridian 속성** 대화 상자를 사용 하 여 지도 뷰포트의 세로 눈금에 대 한 레이블 옵션을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="21837-103">Use the **MapMeridian Properties** dialog box to change label options for the vertical grid in the map viewport.</span></span> <span data-ttu-id="21837-104">자오선은 뷰포트에 지정된 좌표계에 따라 다음 값을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="21837-104">A meridian represents the following value depending on the specified coordinate system for the viewport:</span></span>  
  
-   <span data-ttu-id="21837-105">**평면**.</span><span class="sxs-lookup"><span data-stu-id="21837-105">**Planar**.</span></span> <span data-ttu-id="21837-106">Y 좌표입니다.</span><span class="sxs-lookup"><span data-stu-id="21837-106">The Y coordinate.</span></span>  
  
-   <span data-ttu-id="21837-107">**지리적**위치.</span><span class="sxs-lookup"><span data-stu-id="21837-107">**Geographic**.</span></span> <span data-ttu-id="21837-108">현재 도법의 경도입니다.</span><span class="sxs-lookup"><span data-stu-id="21837-108">The longitude for the current projection.</span></span>  
  
 <span data-ttu-id="21837-109">옵션의 값을 설정하는 식을 편집하려면 **식** 단추(*fx*)를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="21837-109">Click the **Expression** (*fx*) button to edit an expression that sets the value of the option.</span></span>  
  
## <a name="options"></a><span data-ttu-id="21837-110">옵션</span><span class="sxs-lookup"><span data-stu-id="21837-110">Options</span></span>  
 <span data-ttu-id="21837-111">**간격**</span><span class="sxs-lookup"><span data-stu-id="21837-111">**Interval**</span></span>  
 <span data-ttu-id="21837-112">자오선 간의 간격을 지정하는 정수 값(도)을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="21837-112">Type an integer value in degrees that specifies the interval between meridians.</span></span> <span data-ttu-id="21837-113">기본적으로 **자동** 이 선택되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="21837-113">By default, **Auto** is selected.</span></span> <span data-ttu-id="21837-114">**자동** 은 공간 데이터에 따라 값이 자동으로 결정됨을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="21837-114">**Auto** indicates that value is automatically determined by spatial data.</span></span>  
  
 <span data-ttu-id="21837-115">**레이블 표시**</span><span class="sxs-lookup"><span data-stu-id="21837-115">**Show labels**</span></span>  
 <span data-ttu-id="21837-116">자오선에 대한 레이블을 표시하려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="21837-116">Select this option to display labels for the meridians.</span></span>  
  
 <span data-ttu-id="21837-117">**배치**</span><span class="sxs-lookup"><span data-stu-id="21837-117">**Placement**</span></span>  
 <span data-ttu-id="21837-118">뷰포트의 위쪽, 가운데 및 아래쪽과 상대적으로 레이블을 표시할 위치를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="21837-118">Select a location to display the labels relative to the top, center, and bottom of the viewport.</span></span> <span data-ttu-id="21837-119">기본 배치는 **가까이**입니다.</span><span class="sxs-lookup"><span data-stu-id="21837-119">The default placement is **Near**.</span></span>  
  
-   <span data-ttu-id="21837-120">**가까이** 왼쪽 가장자리에 레이블을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="21837-120">**Near** Display labels at the left edge.</span></span>  
  
-   <span data-ttu-id="21837-121">**1/4** 왼쪽 가장자리와 가운데의 중간에 레이블을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="21837-121">**One Quarter** Display labels half way between the left edge and the center.</span></span>  
  
-   <span data-ttu-id="21837-122">**가운데** 가운데에 레이블을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="21837-122">**Center** Display labels at the center.</span></span>  
  
-   <span data-ttu-id="21837-123">**3/4** 가운데와 오른쪽 가장자리의 중간에 레이블을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="21837-123">**Three Quarters** Display labels half way between the center and the right edge.</span></span>  
  
-   <span data-ttu-id="21837-124">**멀리** 오른쪽 가장자리에 레이블을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="21837-124">**Far** Display labels at the right edge.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21837-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="21837-125">See Also</span></span>  
 [<span data-ttu-id="21837-126">지도&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="21837-126">Maps &#40;Report Builder and SSRS&#41;</span></span>](report-design/maps-report-builder-and-ssrs.md)  
  
  
