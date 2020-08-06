---
title: 지도에 사용자 지정 위치 추가(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- MICROSOFT.REPORTDESIGNER.MAPPOINT.POINTTEMPLATE
ms.assetid: 7d36faae-5bcc-446a-9eba-f42349cafacb
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 167558534280f08d576205b5ff1b94d0588fcb78
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738002"
---
# <a name="add-custom-locations-to-a-map-report-builder-and-ssrs"></a><span data-ttu-id="f0fc3-102">지도에 사용자 지정 위치 추가(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="f0fc3-102">Add Custom Locations to a Map (Report Builder and SSRS)</span></span>
  <span data-ttu-id="f0fc3-103">보고서에 지도를 추가한 후 점 위치를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f0fc3-103">After you add a map to a report, you can add your own point locations.</span></span>  
  
 <span data-ttu-id="f0fc3-104">계층의 모든 점에 대한 표시 속성은 계층의 점 속성에 대한 옵션을 설정하여 제어됩니다.</span><span class="sxs-lookup"><span data-stu-id="f0fc3-104">Display properties for all points on a layer are controlled by setting options for the point properties for the layer.</span></span> <span data-ttu-id="f0fc3-105">선택한 포함된 점의 경우 표시 속성을 무시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f0fc3-105">For a selected embedded point, you can override the display properties.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f0fc3-106">포함된 점에 대한 계층 표시 속성을 무시할 때 변경한 내용은 되돌릴 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f0fc3-106">When you override the layer display properties for the embedded point, the changes that you make are not reversible.</span></span>  
  
 <span data-ttu-id="f0fc3-107">자세한 내용은 [규칙 및 분석 데이터를 사용하여 다각형, 선 및 점 표시 변경&#40;보고서 작성기 및 SSRS&#41;](vary-polygon-line-and-point-display-by-rules-and-analytical-data.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f0fc3-107">For more information, see [Vary Polygon, Line, and Point Display by Rules and Analytical Data &#40;Report Builder and SSRS&#41;](vary-polygon-line-and-point-display-by-rules-and-analytical-data.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-a-point-layer"></a><span data-ttu-id="f0fc3-108">점 계층을 추가하려면</span><span class="sxs-lookup"><span data-stu-id="f0fc3-108">To add a point layer</span></span>  
  
1.  <span data-ttu-id="f0fc3-109">보고서 디자인 화면에서 지도를 클릭해 선택하여 지도 창을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="f0fc3-109">On the report design surface, click the map to select it and display the Map pane.</span></span>  
  
2.  <span data-ttu-id="f0fc3-110">도구 모음에서 **계층 추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f0fc3-110">On the toolbar, click **Add Layer**.</span></span>  
  
3.  <span data-ttu-id="f0fc3-111">드롭다운 목록에서 **점 계층 추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f0fc3-111">From the drop-down list, click **Add Point Layer**.</span></span> <span data-ttu-id="f0fc3-112">점이 포함되지 않은 점 계층이 지도에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="f0fc3-112">A point layer with no points is added to the map.</span></span> <span data-ttu-id="f0fc3-113">기본적으로 이 점 계층은 포함된 점을 사용할 준비가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f0fc3-113">By default, the point layer is ready for embedded points.</span></span>  
  
### <a name="to-add-a-custom-point"></a><span data-ttu-id="f0fc3-114">사용자 지정 점을 추가하려면</span><span class="sxs-lookup"><span data-stu-id="f0fc3-114">To add a custom point</span></span>  
  
1.  <span data-ttu-id="f0fc3-115">보고서 디자인 화면에서 지도를 클릭해 선택하여 지도 창을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="f0fc3-115">On the report design surface, click the map to select it and display the Map pane.</span></span>  
  
2.  <span data-ttu-id="f0fc3-116">지도 창에서 **포함**유형인 점 계층을 마우스 오른쪽 단추로 클릭한 다음 **점 추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f0fc3-116">In the Map pane, right-click a point layer that has type **Embedded**, and then click **Add Point**.</span></span> <span data-ttu-id="f0fc3-117">커서는 십자 기호로 변경됩니다.</span><span class="sxs-lookup"><span data-stu-id="f0fc3-117">The cursor changes to crosshairs.</span></span>  
  
3.  <span data-ttu-id="f0fc3-118">점을 추가하려면 지도에서 위치를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f0fc3-118">To add a point, click a location on the map.</span></span> <span data-ttu-id="f0fc3-119">포함된 점이 클릭한 위치의 선택한 계층에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="f0fc3-119">An embedded point is added to the selected layer at the location where you click.</span></span>  
  
### <a name="to-customize-the-display-for-an-embedded-point"></a><span data-ttu-id="f0fc3-120">포함된 점의 표시를 사용자 지정하려면</span><span class="sxs-lookup"><span data-stu-id="f0fc3-120">To customize the display for an embedded point</span></span>  
  
1.  <span data-ttu-id="f0fc3-121">점을 마우스 오른쪽 단추로 클릭한 다음 **점 속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f0fc3-121">Right-click the point, and then click **Point Properties**.</span></span> <span data-ttu-id="f0fc3-122">**지도 포함 점 속성** 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="f0fc3-122">The **Map Embedded Point Properties** dialog box opens.</span></span>  
  
2.  <span data-ttu-id="f0fc3-123">**이 계층의 점 옵션 무시**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f0fc3-123">Click **Override point options for this layer**.</span></span> <span data-ttu-id="f0fc3-124">여러 속성 페이지가 왼쪽 창에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="f0fc3-124">Multiple property pages appear in the left pane.</span></span>  
  
3.  <span data-ttu-id="f0fc3-125">페이지를 클릭하고 이 점에 적용할 표시 속성을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="f0fc3-125">Click the pages and set the display properties that you want to apply to this point.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0fc3-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f0fc3-126">See Also</span></span>  
 <span data-ttu-id="f0fc3-127">[지도&#40;보고서 작성기 및 SSRS&#41;](maps-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="f0fc3-127">[Maps &#40;Report Builder and SSRS&#41;](maps-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="f0fc3-128">규칙 및 분석 데이터를 사용하여 다각형, 선 및 점 표시 변경&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="f0fc3-128">Vary Polygon, Line, and Point Display by Rules and Analytical Data &#40;Report Builder and SSRS&#41;</span></span>](vary-polygon-line-and-point-display-by-rules-and-analytical-data.md)  
  
  
