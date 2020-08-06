---
title: 공간 데이터 결과 창
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: c2d5a477-6496-4d01-adee-7322ebdfadf3
author: rothja
ms.author: jroth
ms.openlocfilehash: 5e018ec9f016dfc51ed1bb055ba94abf12bc878f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743184"
---
# <a name="spatial-results-window"></a><span data-ttu-id="56ca2-102">공간 데이터 결과 창</span><span class="sxs-lookup"><span data-stu-id="56ca2-102">Spatial Results Window</span></span>
  <span data-ttu-id="56ca2-103">**공간 데이터 결과** 창에서는 공간 데이터를 볼 수 있는 시각적인 매핑 도구를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="56ca2-103">The **Spatial results** window provides visual mapping tools for viewing spatial data.</span></span> <span data-ttu-id="56ca2-104">공간 데이터 결과를 보려면 쿼리 결과에 기하 도형 또는 지리 데이터가 포함된 공간 열이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="56ca2-104">To view spatial results, your query results must include a spatial column with either geometry or geography data.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="56ca2-105">**공간 데이터 결과** 창은 결과가 **결과** 창에 표 형식으로 반환되는 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="56ca2-105">The **Spatial results** window is only available if your results are returned to a grid in the **Results** window.</span></span> <span data-ttu-id="56ca2-106">결과가 텍스트로 반환되도록 지정한 경우에는 이 창을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="56ca2-106">If you specify that your results are returned as text, this window is not available.</span></span>  
  
## <a name="options"></a><span data-ttu-id="56ca2-107">옵션</span><span class="sxs-lookup"><span data-stu-id="56ca2-107">Options</span></span>  
 <span data-ttu-id="56ca2-108">**공간 열 선택**</span><span class="sxs-lookup"><span data-stu-id="56ca2-108">**Select spatial column**</span></span>  
 <span data-ttu-id="56ca2-109">쿼리 결과의 공간 열 중에서 보려는 공간 열을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="56ca2-109">Specify the spatial column you want to view from the spatial columns in the query results.</span></span> <span data-ttu-id="56ca2-110">열은 한 번에 하나씩만 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="56ca2-110">Only one column can be selected at a time.</span></span>  
  
 <span data-ttu-id="56ca2-111">**레이블 열 선택**</span><span class="sxs-lookup"><span data-stu-id="56ca2-111">**Select label column**</span></span>  
 <span data-ttu-id="56ca2-112">쿼리 결과에 반환된 열 중에서 공간이 아닌 열을 지정하여 공간 데이터에 레이블을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="56ca2-112">Specify the non-spatial column from the columns returned in the query results to label the spatial data.</span></span> <span data-ttu-id="56ca2-113">열은 한 번에 하나씩만 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="56ca2-113">Only one column can be selected at a time.</span></span>  
  
 <span data-ttu-id="56ca2-114">쿼리로 점만 반환된 경우 이 옵션을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="56ca2-114">This option is not available when only point instances are returned in a query.</span></span>  
  
 <span data-ttu-id="56ca2-115">**투영 선택**</span><span class="sxs-lookup"><span data-stu-id="56ca2-115">**Select projection**</span></span>  
 <span data-ttu-id="56ca2-116">등장방형(Equirectangular), 메르카토르(Mercator), 로빈슨(Robinson) 또는 본느(Bonne) 투영 모드 중 하나로 지리 데이터를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="56ca2-116">Display geography data in one of four projections: Equirectangular, Mercator, Robinson, or Bonne.</span></span>  
  
 <span data-ttu-id="56ca2-117">기하 도형 데이터에 대해서는 이 옵션을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="56ca2-117">This option is not available for geometry data.</span></span>  
  
 <span data-ttu-id="56ca2-118">**Zoom**</span><span class="sxs-lookup"><span data-stu-id="56ca2-118">**Zoom**</span></span>  
 <span data-ttu-id="56ca2-119">맵 표시를 지수 배율로 조정합니다.</span><span class="sxs-lookup"><span data-stu-id="56ca2-119">Adjust the map display on an exponential scale.</span></span>  
  
 <span data-ttu-id="56ca2-120">**눈금선 표시**</span><span class="sxs-lookup"><span data-stu-id="56ca2-120">**Show grid lines**</span></span>  
 <span data-ttu-id="56ca2-121">좌표 눈금선 표시를 설정하거나 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="56ca2-121">Toggle coordinate gridlines on or off.</span></span>  
  
 <span data-ttu-id="56ca2-122">다각형 모양의 경우 레이블 텍스트를 넣을 수 있을 만큼 큰 경우에만 레이블이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="56ca2-122">For polygon shapes, the label is displayed only when the shape is large enough to hold the label text.</span></span> <span data-ttu-id="56ca2-123">작은 모양에 레이블을 표시하려면 확대/축소를 조정하십시오.</span><span class="sxs-lookup"><span data-stu-id="56ca2-123">To display labels for small shapes, adjust the zoom.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="56ca2-124">점에는 레이블을 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="56ca2-124">Point instances cannot be labeled.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56ca2-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="56ca2-125">See Also</span></span>  
 <span data-ttu-id="56ca2-126">[개체 탐색기에서 공간 데이터 보기](view-spatial-data-in-object-explorer.md) </span><span class="sxs-lookup"><span data-stu-id="56ca2-126">[View Spatial Data in Object Explorer](view-spatial-data-in-object-explorer.md) </span></span>  
 <span data-ttu-id="56ca2-127">[공간 데이터&#40;SQL Server&#41;](../spatial/spatial-data-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="56ca2-127">[Spatial Data &#40;SQL Server&#41;](../spatial/spatial-data-sql-server.md) </span></span>  
 <span data-ttu-id="56ca2-128">[데이터베이스 엔진 쿼리 편집기&#40;SQL Server Management Studio&#41;](database-engine-query-editor-sql-server-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="56ca2-128">[Database Engine Query Editor &#40;SQL Server Management Studio&#41;](database-engine-query-editor-sql-server-management-studio.md) </span></span>  
 [<span data-ttu-id="56ca2-129">쿼리 및 텍스트 편집기&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="56ca2-129">Query and Text Editors &#40;SQL Server Management Studio&#41;</span></span>](query-and-text-editors-sql-server-management-studio.md)  
  
  
