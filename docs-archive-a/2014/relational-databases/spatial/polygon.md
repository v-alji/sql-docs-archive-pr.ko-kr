---
title: Polygon | Microsoft 문서
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- geometry subtypes [SQL Server]
- Polygon geometry subtype [SQL Server]
ms.assetid: b6a21c3c-fdb8-4187-8229-1c488454fdfb
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 040bb8a2558cc57b1b99a3ce984bec3c8925bc0d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660424"
---
# <a name="polygon"></a><span data-ttu-id="5f6ef-102">Polygon</span><span class="sxs-lookup"><span data-stu-id="5f6ef-102">Polygon</span></span>
  <span data-ttu-id="5f6ef-103">`Polygon`은 외부 경계 링과 0개 이상의 내부 링을 정의하는 일련의 점으로 저장되는 2차원 표면입니다.</span><span class="sxs-lookup"><span data-stu-id="5f6ef-103">A `Polygon` is a two-dimensional surface stored as a sequence of points defining an exterior bounding ring and zero or more interior rings.</span></span>

## <a name="polygon-instances"></a><span data-ttu-id="5f6ef-104">Polygon 인스턴스</span><span class="sxs-lookup"><span data-stu-id="5f6ef-104">Polygon instances</span></span>
 <span data-ttu-id="5f6ef-105">`Polygon` 인스턴스는 서로 다른 점이 3개 이상 있는 링에서 구성될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5f6ef-105">A `Polygon` instance can be formed from a ring that has at least three distinct points.</span></span> <span data-ttu-id="5f6ef-106">`Polygon` 인스턴스가 비어 있을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5f6ef-106">A `Polygon` instance can also be empty.</span></span>

 <span data-ttu-id="5f6ef-107">`Polygon`의 외부 및 내부 링은 해당 경계를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="5f6ef-107">The exterior and any interior rings of a `Polygon` define its boundary.</span></span> <span data-ttu-id="5f6ef-108">링 내부 공간은 `Polygon`의 내부를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="5f6ef-108">The space within the rings defines the interior of the `Polygon`.</span></span>

 <span data-ttu-id="5f6ef-109">다음 그림에서는 `Polygon` 인스턴스의 예를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="5f6ef-109">The illustration below shows examples of `Polygon` instances.</span></span>

 <span data-ttu-id="5f6ef-110">![기하 도형 Polygon 인스턴스의 예](../../database-engine/media/polygon.gif "기하 도형 Polygon 인스턴스의 예")</span><span class="sxs-lookup"><span data-stu-id="5f6ef-110">![Examples of geometry Polygon instances](../../database-engine/media/polygon.gif "Examples of geometry Polygon instances")</span></span>

 <span data-ttu-id="5f6ef-111">그림에 대한 설명:</span><span class="sxs-lookup"><span data-stu-id="5f6ef-111">As shown in the illustration:</span></span>

1.  <span data-ttu-id="5f6ef-112">그림 1은 외부 링에서 정의한 경계가 있는 `Polygon` 인스턴스입니다.</span><span class="sxs-lookup"><span data-stu-id="5f6ef-112">Figure 1 is a `Polygon` instance whose boundary is defined by an exterior ring.</span></span>

2.  <span data-ttu-id="5f6ef-113">그림 2는 외부 링 및 두 개의 내부 링에서 정의한 경계가 있는 `Polygon` 인스턴스입니다.</span><span class="sxs-lookup"><span data-stu-id="5f6ef-113">Figure 2 is a `Polygon` instance whose boundary is defined by an exterior ring and two interior rings.</span></span> <span data-ttu-id="5f6ef-114">내부 링 내의 영역이 `Polygon` 인스턴스 외부의 일부분입니다.</span><span class="sxs-lookup"><span data-stu-id="5f6ef-114">The area inside the interior rings is part of the exterior of the `Polygon` instance.</span></span>

3.  <span data-ttu-id="5f6ef-115">그림 3은 `Polygon` 인스턴스의 내부 링이 하나의 탄젠트 점에서 교차하므로 올바른 인스턴스입니다.</span><span class="sxs-lookup"><span data-stu-id="5f6ef-115">Figure 3 is a valid `Polygon` instance because its interior rings intersect at a single tangent point.</span></span>

### <a name="accepted-instances"></a><span data-ttu-id="5f6ef-116">허용되는 인스턴스</span><span class="sxs-lookup"><span data-stu-id="5f6ef-116">Accepted instances</span></span>
 <span data-ttu-id="5f6ef-117">허용되는 `Polygon` 인스턴스는 예외를 발생시키지 않고 `geometry` 또는 `geography` 변수에 저장할 수 있는 인스턴스입니다.</span><span class="sxs-lookup"><span data-stu-id="5f6ef-117">Accepted `Polygon` instances are instances that can be stored in a `geometry` or `geography` variable without throwing an exception.</span></span> <span data-ttu-id="5f6ef-118">다음 `Polygon` 인스턴스가 허용됩니다.</span><span class="sxs-lookup"><span data-stu-id="5f6ef-118">The following are accepted `Polygon` instances:</span></span>

-   <span data-ttu-id="5f6ef-119">빈 `Polygon` 인스턴스</span><span class="sxs-lookup"><span data-stu-id="5f6ef-119">An Empty `Polygon` instance</span></span>

-   <span data-ttu-id="5f6ef-120">허용 가능 외부 링 및 0개 이상의 허용 가능 내부 링을 포함하는 `Polygon` 인스턴스</span><span class="sxs-lookup"><span data-stu-id="5f6ef-120">A `Polygon` instance that has an acceptable exterior ring and zero or more acceptable interior rings</span></span>

 <span data-ttu-id="5f6ef-121">링이 허용되려면 다음 조건을 충족해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5f6ef-121">The following criteria are needed for a ring to be acceptable.</span></span>

-   <span data-ttu-id="5f6ef-122">`LineString` 인스턴스가 허용되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5f6ef-122">The `LineString` instance must be accepted.</span></span>

-   <span data-ttu-id="5f6ef-123">`LineString` 인스턴스에 4개 이상의 점이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5f6ef-123">The `LineString` instance must have at least four points.</span></span>

-   <span data-ttu-id="5f6ef-124">`LineString` 인스턴스의 시작점 및 끝점이 같아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5f6ef-124">The starting and ending points of the `LineString` instance must be the same.</span></span>

 <span data-ttu-id="5f6ef-125">다음 예에서는 허용되는 `Polygon` 인스턴스를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="5f6ef-125">The following example shows accepted `Polygon` instances.</span></span>

```
DECLARE @g1 geometry = 'POLYGON EMPTY';
DECLARE @g2 geometry = 'POLYGON((1 1, 3 3, 3 1, 1 1))';
DECLARE @g3 geometry = 'POLYGON((-5 -5, -5 5, 5 5, 5 -5, -5 -5),(0 0, 3 0, 3 3, 0 3, 0 0))';
DECLARE @g4 geometry = 'POLYGON((-5 -5, -5 5, 5 5, 5 -5, -5 -5),(3 0, 6 0, 6 3, 3 3, 3 0))';
DECLARE @g5 geometry = 'POLYGON((1 1, 1 1, 1 1, 1 1))';
```

 <span data-ttu-id="5f6ef-126">`@g4` 및 `@g5`가 보여 주듯이 허용된 `Polygon` 인스턴스는 유효한 `Polygon` 인스턴스가 아닐 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5f6ef-126">As `@g4` and `@g5` show an accepted `Polygon` instance may not be a valid `Polygon` instance.</span></span> <span data-ttu-id="5f6ef-127">`@g5` 도 Polygon 인스턴스가 허용될 4개의 점이 있는 링만 포함해야 함을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="5f6ef-127">`@g5` also shows that a Polygon instance needs to only contain a ring with any four points to be accepted.</span></span>

 <span data-ttu-id="5f6ef-128">다음 예에서는 `Polygon` 인스턴스가 허용되지 않으므로 `System.FormatException`이 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="5f6ef-128">The following examples throw a `System.FormatException` because the `Polygon` instances are not accepted.</span></span>

```
DECLARE @g1 geometry = 'POLYGON((1 1, 3 3, 1 1))';
DECLARE @g2 geometry = 'POLYGON((1 1, 3 3, 3 1, 1 5))';
```

 <span data-ttu-id="5f6ef-129">외부 링에 대한 `LineString` 인스턴스에 점이 부족하기 때문에 `@g1`이 허용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5f6ef-129">`@g1` is not accepted because the `LineString` instance for the exterior ring does not contain enough points.</span></span> <span data-ttu-id="5f6ef-130">외부 링 `LineString` 인스턴스의 시작 점이 끝 점과 같지 않기 때문에 `@g2`가 허용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5f6ef-130">`@g2` is not accepted because the starting point of the exterior ring `LineString` instance is not the same as the ending point.</span></span> <span data-ttu-id="5f6ef-131">다음 예에는 허용 가능한 외부 링이 있지만 내부 링은 허용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5f6ef-131">The following example has an acceptable exterior ring, but the interior ring is not acceptable.</span></span> <span data-ttu-id="5f6ef-132">여기서도 `System.FormatException`이 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="5f6ef-132">This also throws a `System.FormatException`.</span></span>

```
DECLARE @g geometry = 'POLYGON((-5 -5, -5 5, 5 5, 5 -5, -5 -5),(0 0, 3 0, 0 0))';
```

### <a name="valid-instances"></a><span data-ttu-id="5f6ef-133">유효한 인스턴스</span><span class="sxs-lookup"><span data-stu-id="5f6ef-133">Valid instances</span></span>
 <span data-ttu-id="5f6ef-134">`Polygon`의 내부 링은 자신들과 서로 다른 링 모두 하나의 탄젠트 점에서 인접할 수 있지만 `Polygon`의 내부 링이 교차할 경우 해당 인스턴스가 유효하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5f6ef-134">The interior rings of a `Polygon` can touch both themselves and each other at single tangent points, but if the interior rings of a `Polygon` cross, the instance is not valid.</span></span>

 <span data-ttu-id="5f6ef-135">다음 예에서는 유효한 `Polygon` 인스턴스를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="5f6ef-135">The following example shows valid `Polygon` instances.</span></span>

```
DECLARE @g1 geometry = 'POLYGON((-20 -20, -20 20, 20 20, 20 -20, -20 -20))';
DECLARE @g2 geometry = 'POLYGON((-20 -20, -20 20, 20 20, 20 -20, -20 -20), (10 0, 0 10, 0 -10, 10 0))';
DECLARE @g3 geometry = 'POLYGON((-20 -20, -20 20, 20 20, 20 -20, -20 -20), (10 0, 0 10, 0 -10, 10 0), (-10 0, 0 10, -5 -10, -10 0))';
SELECT @g1.STIsValid(), @g2.STIsValid(), @g3.STIsValid();
```

 <span data-ttu-id="5f6ef-136">`@g3` 이 유효합니다.</span><span class="sxs-lookup"><span data-stu-id="5f6ef-136">`@g3` is valid because the two interior rings touch at a single point and do not cross each other.</span></span> <span data-ttu-id="5f6ef-137">다음 예에서는 유효하지 않은 `Polygon` 인스턴스를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="5f6ef-137">The following example shows `Polygon` instances that are not valid.</span></span>

```
DECLARE @g1 geometry = 'POLYGON((-20 -20, -20 20, 20 20, 20 -20, -20 -20), (20 0, 0 10, 0 -20, 20 0))';
DECLARE @g2 geometry = 'POLYGON((-20 -20, -20 20, 20 20, 20 -20, -20 -20), (10 0, 0 10, 0 -10, 10 0), (5 0, 1 5, 1 -5, 5 0))';
DECLARE @g3 geometry = 'POLYGON((-20 -20, -20 20, 20 20, 20 -20, -20 -20), (10 0, 0 10, 0 -10, 10 0), (-10 0, 0 10, 0 -10, -10 0))';
DECLARE @g4 geometry = 'POLYGON((-20 -20, -20 20, 20 20, 20 -20, -20 -20), (10 0, 0 10, 0 -10, 10 0), (-10 0, 1 5, 0 -10, -10 0))';
DECLARE @g5 geometry = 'POLYGON((10 0, 0 10, 0 -10, 10 0), (-20 -20, -20 20, 20 20, 20 -20, -20 -20) )';
DECLARE @g6 geometry = 'POLYGON((1 1, 1 1, 1 1, 1 1))';
SELECT @g1.STIsValid(), @g2.STIsValid(), @g3.STIsValid(), @g4.STIsValid(), @g5.STIsValid(), @g6.STIsValid();
```

 <span data-ttu-id="5f6ef-138">`@g1` 이 유효하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5f6ef-138">`@g1` is not valid because the inner ring touches the exterior ring in two places.</span></span> <span data-ttu-id="5f6ef-139">`@g2` 가 유효하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5f6ef-139">`@g2` is not valid because the second inner ring in within the interior of the first inner ring.</span></span> <span data-ttu-id="5f6ef-140">`@g3` 이 두 내부 링이 여러 연속 점에서 접하기 때문에 유효하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5f6ef-140">`@g3` is not valid because the two inner rings touch at multiple consecutive points.</span></span> <span data-ttu-id="5f6ef-141">`@g4` 가 유효하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5f6ef-141">`@g4` is not valid because the interiors of the two inner rings overlap.</span></span> <span data-ttu-id="5f6ef-142">`@g5` 가 유효하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5f6ef-142">`@g5` is not valid because the exterior ring is not the first ring.</span></span> <span data-ttu-id="5f6ef-143">`@g6` 이 유효하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5f6ef-143">`@g6` is not valid because the ring does not have at least three distinct points.</span></span>

## <a name="examples"></a><span data-ttu-id="5f6ef-144">예</span><span class="sxs-lookup"><span data-stu-id="5f6ef-144">Examples</span></span>
 <span data-ttu-id="5f6ef-145">다음 예에서는 구멍이 있고 SRID가 10인 단순한 `geometry``Polygon` 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="5f6ef-145">The following example creates a simple `geometry``Polygon` instance with a hole and SRID 10.</span></span>

```
DECLARE @g geometry;
SET @g = geometry::STPolyFromText('POLYGON((0 0, 0 3, 3 3, 3 0, 0 0), (1 1, 1 2, 2 1, 1 1))', 10);
```

 <span data-ttu-id="5f6ef-146">유효하지 않은 인스턴스는 유효한 `geometry` 인스턴스에 입력되고 변환될 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5f6ef-146">Aninstance that is not valid may be entered and converted to a valid `geometry` instance.</span></span> <span data-ttu-id="5f6ef-147">다음 `Polygon`의 예에서는 내부 및 외부 링이 겹치고 인스턴스가 유효하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5f6ef-147">In the following example of a `Polygon`, the interior and exterior rings overlap and the instance is not valid.</span></span>

```
DECLARE @g geometry;
SET @g = geometry::Parse('POLYGON((1 0, 0 1, 1 2, 2 1, 1 0), (2 0, 1 1, 2 2, 3 1, 2 0))');
```

 <span data-ttu-id="5f6ef-148">다음 예에서는 유효하지 않은 인스턴스가 `MakeValid()`를 사용하여 유효하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5f6ef-148">In the following example, the invalid instance is made valid with `MakeValid()`.</span></span>

```
SET @g = @g.MakeValid();
SELECT @g.ToString();
```

 <span data-ttu-id="5f6ef-149">위의 예에서 반환된 `geometry` 인스턴스는 `MultiPolygon`입니다.</span><span class="sxs-lookup"><span data-stu-id="5f6ef-149">The `geometry` instance returned from the above example is a `MultiPolygon`.</span></span>

```
MULTIPOLYGON (((2 0, 3 1, 2 2, 1.5 1.5, 2 1, 1.5 0.5, 2 0)), ((1 0, 1.5 0.5, 1 1, 1.5 1.5, 1 2, 0 1, 1 0)))
```

 <span data-ttu-id="5f6ef-150">다음은 유효하지 않은 인스턴스를 유효한 geometry 인스턴스로 변환하는 다른 예입니다.</span><span class="sxs-lookup"><span data-stu-id="5f6ef-150">Here is another example of converting an invalid instance to a valid geometry instance.</span></span> <span data-ttu-id="5f6ef-151">다음 예에서는 정확하게 서로 동일한 점 세 개를 사용하여 `Polygon` 인스턴스를 만들었습니다.</span><span class="sxs-lookup"><span data-stu-id="5f6ef-151">In the following example the `Polygon` instance has been created using three points that are exactly the same:</span></span>

```sql
DECLARE @g geometry
SET @g = geometry::Parse('POLYGON((1 3, 1 3, 1 3, 1 3))');
SET @g = @g.MakeValid();
SELECT @g.ToString()
```

 <span data-ttu-id="5f6ef-152">위에서 반환된 geometry 인스턴스는 `Point(1 3)`입니다.</span><span class="sxs-lookup"><span data-stu-id="5f6ef-152">The geometry instance returned above is a `Point(1 3)`.</span></span>  <span data-ttu-id="5f6ef-153">지정한 `Polygon` 이 `POLYGON((1 3, 1 5, 1 3, 1 3))` 이면 `MakeValid()` 에서 `LINESTRING(1 3, 1 5)`를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="5f6ef-153">If the `Polygon` given is `POLYGON((1 3, 1 5, 1 3, 1 3))` then `MakeValid()` would return `LINESTRING(1 3, 1 5)`.</span></span>

## <a name="see-also"></a><span data-ttu-id="5f6ef-154">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5f6ef-154">See Also</span></span>
 <span data-ttu-id="5f6ef-155">[Starea &#40;Geometry 데이터 형식&#41;](/sql/t-sql/spatial-geometry/starea-geometry-data-type) [STExteriorRing &#40;geometry 데이터 형식&#41;](/sql/t-sql/spatial-geometry/stexteriorring-geometry-data-type) [STNumInteriorRing &#40;](/sql/t-sql/spatial-geometry/stnuminteriorring-geometry-data-type) geometry 데이터 형식&#41;[STInteriorRingN &#40;](/sql/t-sql/spatial-geometry/stinteriorringn-geometry-data-type) geometry [데이터 형식&#41;](/sql/t-sql/spatial-geometry/stcentroid-geometry-data-type) [stpointonsurface &#40;geometry 데이터 형식](/sql/t-sql/spatial-geometry/stpointonsurface-geometry-data-type)&#41;[multipolygon](../spatial/polygon.md) [공간 데이터 &#40;&#41;&#40;](../spatial/spatial-data-sql-server.md) [starea SQL Server geography](/sql/t-sql/spatial-geography/stisvalid-geography-data-type) 데이터 형식&#41;[starea &#40;geometry 데이터 형식&#41;](/sql/t-sql/spatial-geometry/stisvalid-geometry-data-type)</span><span class="sxs-lookup"><span data-stu-id="5f6ef-155">[STArea &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/starea-geometry-data-type) [STExteriorRing &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/stexteriorring-geometry-data-type) [STNumInteriorRing &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/stnuminteriorring-geometry-data-type) [STInteriorRingN &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/stinteriorringn-geometry-data-type) [STCentroid &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/stcentroid-geometry-data-type) [STPointOnSurface &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/stpointonsurface-geometry-data-type) [MultiPolygon](../spatial/polygon.md) [Spatial Data &#40;SQL Server&#41;](../spatial/spatial-data-sql-server.md) [STIsValid &#40;geography Data Type&#41;](/sql/t-sql/spatial-geography/stisvalid-geography-data-type) [STIsValid &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/stisvalid-geometry-data-type)</span></span>


