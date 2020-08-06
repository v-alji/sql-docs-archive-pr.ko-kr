---
title: MultiLineString | Microsoft 문서
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- MultiLineString geometry subtype [SQL Server]
- geometry subtypes [SQL Server]
ms.assetid: 95deeefe-d6c5-4a11-b347-379e4486e7b7
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: fdd093d99d055df8e15fc22e3e570e6805e35d6e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660432"
---
# <a name="multilinestring"></a><span data-ttu-id="a8ee2-102">MultiLineString</span><span class="sxs-lookup"><span data-stu-id="a8ee2-102">MultiLineString</span></span>
  <span data-ttu-id="a8ee2-103">는 `MultiLineString` 0 개 이상의 `geometry` 또는 **geographyLineString** 인스턴스의 컬렉션입니다.</span><span class="sxs-lookup"><span data-stu-id="a8ee2-103">A `MultiLineString` is a collection of zero or more `geometry` or **geographyLineString** instances.</span></span>  
  
## <a name="multilinestring-instances"></a><span data-ttu-id="a8ee2-104">MultiLineString 인스턴스</span><span class="sxs-lookup"><span data-stu-id="a8ee2-104">MultiLineString instances</span></span>  
 <span data-ttu-id="a8ee2-105">다음 그림에서는 `MultiLineString` 인스턴스의 예를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="a8ee2-105">The illustration below shows examples of `MultiLineString` instances.</span></span>  
  
 <span data-ttu-id="a8ee2-106">![기하 도형 MultiLineString 인스턴스의 예](../../database-engine/media/multilinestring.gif "기하 도형 MultiLineString 인스턴스의 예")</span><span class="sxs-lookup"><span data-stu-id="a8ee2-106">![Examples of geometry MultiLineString instances](../../database-engine/media/multilinestring.gif "Examples of geometry MultiLineString instances")</span></span>  
  
 <span data-ttu-id="a8ee2-107">그림에 대한 설명:</span><span class="sxs-lookup"><span data-stu-id="a8ee2-107">As shown in the illustration:</span></span>  
  
-   <span data-ttu-id="a8ee2-108">그림 1은 `MultiLineString` 경계가 두 요소의 네 끝점 인 단순 인스턴스입니다 `LineString` .</span><span class="sxs-lookup"><span data-stu-id="a8ee2-108">Figure 1 is a simple `MultiLineString` instance whose boundary is the four endpoints of its two `LineString` elements.</span></span>  
  
-   <span data-ttu-id="a8ee2-109">그림 2는 `MultiLineString` 요소의 엔드포인트만 교차하므로 단순한 `LineString` 인스턴스입니다.</span><span class="sxs-lookup"><span data-stu-id="a8ee2-109">Figure 2 is a simple `MultiLineString` instance because only the endpoints of the `LineString` elements intersect.</span></span> <span data-ttu-id="a8ee2-110">경계는 두 개의 겹치지 않는 엔드포인트입니다.</span><span class="sxs-lookup"><span data-stu-id="a8ee2-110">The boundary is the two non-overlapping endpoints.</span></span>  
  
-   <span data-ttu-id="a8ee2-111">그림 3은 해당 `MultiLineString` 요소 중 하나의 내부가 교차하므로 단순하지 않은 `LineString` 인스턴스입니다.</span><span class="sxs-lookup"><span data-stu-id="a8ee2-111">Figure 3 is a nonsimple `MultiLineString` instance because the interior of one of its `LineString` elements is intersected.</span></span> <span data-ttu-id="a8ee2-112">이 `MultiLineString` 인스턴스의 경계는 4개의 엔드포인트입니다.</span><span class="sxs-lookup"><span data-stu-id="a8ee2-112">The boundary of this `MultiLineString` instance is the four endpoints.</span></span>  
  
-   <span data-ttu-id="a8ee2-113">그림 4는 단순하지 않고 닫혀 있지 않은 `MultiLineString` 인스턴스입니다.</span><span class="sxs-lookup"><span data-stu-id="a8ee2-113">Figure 4 is a nonsimple, nonclosed `MultiLineString` instance.</span></span>  
  
-   <span data-ttu-id="a8ee2-114">그림 5는 단순하고 닫혀 있지 않은 `MultiLineString` 인스턴스입니다.</span><span class="sxs-lookup"><span data-stu-id="a8ee2-114">Figure 5 is a simple, nonclosed `MultiLineString`.</span></span> <span data-ttu-id="a8ee2-115">해당 요소가 닫혀 있지 않으므로 닫혀 있지 않습니다 `LineStrings` .</span><span class="sxs-lookup"><span data-stu-id="a8ee2-115">It is not closed because its `LineStrings` elements are not closed.</span></span> <span data-ttu-id="a8ee2-116">`LineStrings` 인스턴스의 내부에 교차하는 것이 없으므로 단순합니다.</span><span class="sxs-lookup"><span data-stu-id="a8ee2-116">It is simple because none of the interiors of any of the `LineStrings` instances intersect.</span></span>  
  
-   <span data-ttu-id="a8ee2-117">그림 6은 단순하고 닫혀 있는 `MultiLineString` 인스턴스입니다.</span><span class="sxs-lookup"><span data-stu-id="a8ee2-117">Figure 6 is a simple, closed `MultiLineString` instance.</span></span> <span data-ttu-id="a8ee2-118">이 인스턴스는 해당 요소가 모두 닫혀 있으므로 닫혀 있고,</span><span class="sxs-lookup"><span data-stu-id="a8ee2-118">It is closed because all its elements are closed.</span></span> <span data-ttu-id="a8ee2-119">해당 요소 중 교차하는 것이 없으므로 단순합니다.</span><span class="sxs-lookup"><span data-stu-id="a8ee2-119">It is simple because none of its elements intersect at the interiors.</span></span>  
  
### <a name="accepted-instances"></a><span data-ttu-id="a8ee2-120">허용되는 인스턴스</span><span class="sxs-lookup"><span data-stu-id="a8ee2-120">Accepted instances</span></span>  
 <span data-ttu-id="a8ee2-121">`MultiLineString` 인스턴스는 비어 있거나 허용되는 `LineString` 인스턴스로만 구성되어 있어야 허용됩니다.</span><span class="sxs-lookup"><span data-stu-id="a8ee2-121">For a `MultiLineString` instance to be accepted it must either be empty or comprised of only `LineString` intances that are accepted.</span></span> <span data-ttu-id="a8ee2-122">허용 `LineString` 되는 인스턴스에 대 한 자세한 내용은 [LineString](../spatial/linestring.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="a8ee2-122">For more information on accepted `LineString` instances, see [LineString](../spatial/linestring.md).</span></span> <span data-ttu-id="a8ee2-123">다음은 허용되는 `MultiLineString` 인스턴스의 예입니다.</span><span class="sxs-lookup"><span data-stu-id="a8ee2-123">The following are examples of accepted `MultiLineString` instances.</span></span>  
  
```  
DECLARE @g1 geometry = 'MULTILINESTRING EMPTY';  
DECLARE @g2 geometry = 'MULTILINESTRING((1 1, 3 5), (-5 3, -8 -2))';  
DECLARE @g3 geometry = 'MULTILINESTRING((1 1, 5 5), (1 3, 3 1))';  
DECLARE @g4 geometry = 'MULTILINESTRING((1 1, 3 3, 5 5),(3 3, 5 5, 7 7))';  
```  
  
 <span data-ttu-id="a8ee2-124">다음 예에서는 두 번째 `LineString` 인스턴스가 유효하지 않으므로 `System.FormatException`이 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="a8ee2-124">The following example throws a `System.FormatException` because the second `LineString` instance is not valid.</span></span>  
  
```  
DECLARE @g geometry = 'MULTILINESTRING((1 1, 3 5),(-5 3))';  
```  
  
### <a name="valid-instances"></a><span data-ttu-id="a8ee2-125">유효한 인스턴스</span><span class="sxs-lookup"><span data-stu-id="a8ee2-125">Valid instances</span></span>  
 <span data-ttu-id="a8ee2-126">`MultiLineString` 인스턴스는 다음 조건을 충족해야 유효합니다.</span><span class="sxs-lookup"><span data-stu-id="a8ee2-126">For a `MultiLineString` instance to be valid it must meet the following criteria:</span></span>  
  
1.  <span data-ttu-id="a8ee2-127">`MultiLineString` 인스턴스를 구성하는 모든 인스턴스가 유효한 `LineString` 인스턴스여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8ee2-127">All instances comprising the `MultiLineString` instance must be valid `LineString` instances.</span></span>  
  
2.  <span data-ttu-id="a8ee2-128">`LineString` 인스턴스를 구성하는 두 `MultiLineString` 인스턴스가 일정 간격으로 겹치면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a8ee2-128">No two `LineString` instances comprising the `MultiLineString` instance may overlap over an interval.</span></span> <span data-ttu-id="a8ee2-129">`LineString` 인스턴스는 제한된 수의 점에서 자체적으로 또는 다른 `LineString` 인스턴스와 교차하는 것만 가능합니다.</span><span class="sxs-lookup"><span data-stu-id="a8ee2-129">The `LineString` instances can only intersect or touch themselves or other `LineString` instances at a finite number of points.</span></span>  
  
 <span data-ttu-id="a8ee2-130">다음 예에서는 유효한 `MultiLineString` 인스턴스 세 개와 유효하지 않은 `MultiLineString` 인스턴스 하나를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="a8ee2-130">The following example shows three valid `MultiLineString` instances and one `MultiLineString` instance that is not valid.</span></span>  
  
```  
DECLARE @g1 geometry = 'MULTILINESTRING EMPTY';  
DECLARE @g2 geometry = 'MULTILINESTRING((1 1, 3 5), (-5 3, -8 -2))';  
DECLARE @g3 geometry = 'MULTILINESTRING((1 1, 5 5), (1 3, 3 1))';  
DECLARE @g4 geometry = 'MULTILINESTRING((1 1, 3 3, 5 5),(3 3, 5 5, 7 7))';  
SELECT @g1.STIsValid(), @g2.STIsValid(), @g3.STIsValid(), @g4.STIsValid();  
```  
  
 <span data-ttu-id="a8ee2-131">`@g4`는 두 번째 `LineString` 인스턴스가 일정 간격으로 첫 번째 `LineString` 인스턴스와 겹치므로 유효하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a8ee2-131">`@g4` is not valid because the second `LineString` instance overlaps the first `LineString` instance at an interval.</span></span> <span data-ttu-id="a8ee2-132">즉, 이 두 인스턴스는 무한한 점에서 접합니다.</span><span class="sxs-lookup"><span data-stu-id="a8ee2-132">They touch at an infinite number of points.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="a8ee2-133">예</span><span class="sxs-lookup"><span data-stu-id="a8ee2-133">Examples</span></span>  
 <span data-ttu-id="a8ee2-134">다음 예제에서는 SRID 0으로 두 개의 `geometry``MultiLineString` 요소를 포함하는 단순한 `LineString` 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="a8ee2-134">The following example creates a simple `geometry``MultiLineString` instance containing two `LineString` elements with the SRID 0.</span></span>  
  
```  
DECLARE @g geometry;  
SET @g = geometry::Parse('MULTILINESTRING((0 2, 1 1), (1 0, 1 1))');  
```  
  
 <span data-ttu-id="a8ee2-135">다른 SRID로 이 인스턴스를 인스턴스화하려면 `STGeomFromText()` 또는 `STMLineStringFromText()`를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="a8ee2-135">To instantiate this instance with a different SRID, use `STGeomFromText()` or `STMLineStringFromText()`.</span></span> <span data-ttu-id="a8ee2-136">또는 다음 예와 같이 `Parse()` 를 사용한 다음 SRID를 수정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8ee2-136">You can also use `Parse()` and then modify the SRID, as shown in the following example.</span></span>  
  
```  
DECLARE @g geometry;  
SET @g = geometry::Parse('MULTILINESTRING((0 2, 1 1), (1 0, 1 1))');  
SET @g.STSrid = 13;  
```  
  
## <a name="see-also"></a><span data-ttu-id="a8ee2-137">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a8ee2-137">See Also</span></span>  
 <span data-ttu-id="a8ee2-138">[STLength&#40;geometry 데이터 형식&#41;](/sql/t-sql/spatial-geometry/stlength-geometry-data-type) </span><span class="sxs-lookup"><span data-stu-id="a8ee2-138">[STLength &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/stlength-geometry-data-type) </span></span>  
 <span data-ttu-id="a8ee2-139">[STIsClosed&#40;geometry 데이터 형식&#41;](/sql/t-sql/spatial-geometry/stisclosed-geometry-data-type) </span><span class="sxs-lookup"><span data-stu-id="a8ee2-139">[STIsClosed &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/stisclosed-geometry-data-type) </span></span>  
 <span data-ttu-id="a8ee2-140">[LineString](../spatial/linestring.md) </span><span class="sxs-lookup"><span data-stu-id="a8ee2-140">[LineString](../spatial/linestring.md) </span></span>  
 [<span data-ttu-id="a8ee2-141">공간 데이터&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="a8ee2-141">Spatial Data &#40;SQL Server&#41;</span></span>](../spatial/spatial-data-sql-server.md)  
  
  
