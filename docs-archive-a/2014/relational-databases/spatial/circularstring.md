---
title: CircularString | Microsoft 문서
ms.custom: ''
ms.date: 10/18/2019
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
ms.assetid: 9fe06b03-d98c-4337-9f89-54da98f49f9f
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: c701cdc2e8538a5b91093e17714fd9f6508d1c4c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646860"
---
# <a name="circularstring"></a><span data-ttu-id="a6c16-102">CircularString</span><span class="sxs-lookup"><span data-stu-id="a6c16-102">CircularString</span></span>
  <span data-ttu-id="a6c16-103">`CircularString`은 0개 이상의 연속 원호 세그먼트 컬렉션입니다.</span><span class="sxs-lookup"><span data-stu-id="a6c16-103">A `CircularString` is a collection of zero or more continuous circular arc segments.</span></span> <span data-ttu-id="a6c16-104">원호 세그먼트는 2차원 평면에서 3개의 점으로 정의되는 곡선 세그먼트입니다. 첫 번째 점은 세 번째 점과 같을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a6c16-104">A circular arc segment is a curved segment defined by three points in a two-dimensional plane; the first point cannot be the same as the third point.</span></span> <span data-ttu-id="a6c16-105">원호 세그먼트의 세 점 모두가 공선상에 있는 경우 원호 세그먼트가 선분으로 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="a6c16-105">If all three points of a circular arc segment are collinear, the arc segment is treated as a line segment.</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="a6c16-106">하위 유형을 포함 하 여에 도입 된 새로운 공간 기능에 대 한 자세한 설명 및 예를 보려면 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] `CircularString` [SQL Server 2012의 새로운 공간 기능](https://go.microsoft.com/fwlink/?LinkId=226407)백서를 다운로드 하세요.</span><span class="sxs-lookup"><span data-stu-id="a6c16-106">For a detailed description and examples of the new spatial features introduced in [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], including the `CircularString` subtype, download the white paper, [New Spatial Features in SQL Server 2012](https://go.microsoft.com/fwlink/?LinkId=226407).</span></span>

## <a name="circularstring-instances"></a><span data-ttu-id="a6c16-107">CircularString 인스턴스</span><span class="sxs-lookup"><span data-stu-id="a6c16-107">CircularString instances</span></span>
 <span data-ttu-id="a6c16-108">다음 그림에서는 유효한 `CircularString` 인스턴스를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="a6c16-108">The drawing below shows valid `CircularString` instances:</span></span>

 ![](../../database-engine/media/5ff17e34-b578-4873-9d33-79500940d0bc.png "5ff17e34-b578-4873-9d33-79500940d0bc")

### <a name="accepted-instances"></a><span data-ttu-id="a6c16-109">허용되는 인스턴스</span><span class="sxs-lookup"><span data-stu-id="a6c16-109">Accepted instances</span></span>
 <span data-ttu-id="a6c16-110">`CircularString`인스턴스는 비어 있거나 홀수의 지점 수 n을 포함 하는 경우에 허용 됩니다. 여기서 n > 1입니다.</span><span class="sxs-lookup"><span data-stu-id="a6c16-110">A `CircularString` instance is accepted if it is either empty or contains an odd number of points, n, where n > 1.</span></span> <span data-ttu-id="a6c16-111">다음 `CircularString` 인스턴스가 허용됩니다.</span><span class="sxs-lookup"><span data-stu-id="a6c16-111">The following `CircularString` instances are accepted.</span></span>

```sql
DECLARE @g1 geometry = 'CIRCULARSTRING EMPTY';
DECLARE @g2 geometry = 'CIRCULARSTRING(1 1, 2 0, -1 1)';
DECLARE @g3 geometry = 'CIRCULARSTRING(1 1, 2 0, 2 0, 2 0, 1 1)';
```

 <span data-ttu-id="a6c16-112">`@g3`에서는 `CircularString` 인스턴스를 허용할 수 있지만 유효하지 않음을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="a6c16-112">`@g3` shows that `CircularString` instance may be accepted, but not valid.</span></span> <span data-ttu-id="a6c16-113">다음 CircularString 인스턴스 선언은 허용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a6c16-113">The following CircularString instance declaration is not accepted.</span></span> <span data-ttu-id="a6c16-114">이 선언에서는 `System.FormatException`이 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="a6c16-114">This declaration throws a `System.FormatException`.</span></span>

```sql
DECLARE @g geometry = 'CIRCULARSTRING(1 1, 2 0, 2 0, 1 1)';
```

### <a name="valid-instances"></a><span data-ttu-id="a6c16-115">유효한 인스턴스</span><span class="sxs-lookup"><span data-stu-id="a6c16-115">Valid instances</span></span>
 <span data-ttu-id="a6c16-116">유효한 `CircularString` 인스턴스는 비어 있거나 다음 특성을 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6c16-116">A valid `CircularString` instance must be empty or have the following attributes:</span></span>

-   <span data-ttu-id="a6c16-117">이러한 인스턴스는 하나 이상의 원호 세그먼트(즉, 최소 3개의 점)를 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6c16-117">It must contain at least one circular arc segment (that is, have a minimum of three points).</span></span>

-   <span data-ttu-id="a6c16-118">마지막 세그먼트를 제외하고 시퀀스에 있는 각 원호 세그먼트의 마지막 엔드포인트는 시퀀스에 있는 다음 세그먼트의 첫 번째 엔드포인트가어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6c16-118">The last endpoint for each circular arc segment in the sequence, except for the last segment, must be the first endpoint for the next segment in the sequence.</span></span>

-   <span data-ttu-id="a6c16-119">이 인스턴스에는 홀수 점이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6c16-119">It must have an odd number of points.</span></span>

-   <span data-ttu-id="a6c16-120">이 인스턴스는 일정 간격으로 겹치면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a6c16-120">It cannot overlap itself over an interval.</span></span>

-   <span data-ttu-id="a6c16-121">`CircularString` 인스턴스에 선분이 포함될 수 있지만 이러한 선분은 3개의 공선점으로 정의되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6c16-121">Although `CircularString` instances may contain line segments, these line segments must be defined by three collinear points.</span></span>

 <span data-ttu-id="a6c16-122">다음 예에서는 유효한 `CircularString` 인스턴스를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="a6c16-122">The following example shows valid `CircularString` instances.</span></span>

```sql
DECLARE @g1 geometry = 'CIRCULARSTRING EMPTY';
DECLARE @g2 geometry = 'CIRCULARSTRING(1 1, 2 0, -1 1)';
DECLARE @g3 geometry = 'CIRCULARSTRING(1 1, 2 0, 2 0, 1 1, 0 1)';
DECLARE @g4 geometry = 'CIRCULARSTRING(1 1, 2 2, 2 2)';
SELECT @g1.STIsValid(), @g2.STIsValid(), @g3.STIsValid(),@g4.STIsValid();
```

 <span data-ttu-id="a6c16-123">`CircularString` 인스턴스는 하나의 완전한 원을 정의하기 위해 두 개 이상의 원호 세그먼트를 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6c16-123">A `CircularString` instance must contain at least two circular arc segments to define a complete circle.</span></span> <span data-ttu-id="a6c16-124">`CircularString` 인스턴스는 (1 1, 3 1, 1 1)과 같은 하나의 원호 세그먼트를 사용하여 하나의 완전한 원을 정의할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a6c16-124">A `CircularString` instance cannot use a single circular arc segment (such as (1 1, 3 1, 1 1)) to define a complete circle.</span></span> <span data-ttu-id="a6c16-125">(1 1, 2 2, 3 1, 2 0, 1 1)을 사용하여 원을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="a6c16-125">Use (1 1, 2 2, 3 1, 2 0, 1 1) to define the circle.</span></span>

 <span data-ttu-id="a6c16-126">다음 예에서는 유효하지 않은 CircularString 인스턴스를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="a6c16-126">The following example shows CircularString instances that are not valid.</span></span>

```sql
DECLARE @g1 geometry = 'CIRCULARSTRING(1 1, 2 0, 1 1)';
DECLARE @g2 geometry = 'CIRCULARSTRING(0 0, 0 0, 0 0)';
SELECT @g1.STIsValid(), @g2.STIsValid();
```

### <a name="instances-with-collinear-points"></a><span data-ttu-id="a6c16-127">공선점을 포함하는 인스턴스</span><span class="sxs-lookup"><span data-stu-id="a6c16-127">Instances with collinear points</span></span>
 <span data-ttu-id="a6c16-128">다음 경우에는 원호 세그먼트가 선분으로 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="a6c16-128">In the following cases a circular arc segment will be treated as a line segment:</span></span>

-   <span data-ttu-id="a6c16-129">3개의 점이 모두 공선상에 있는 경우(예: (1 3, 4 4, 7 5))</span><span class="sxs-lookup"><span data-stu-id="a6c16-129">When all three points are collinear (for example, (1 3, 4 4, 7 5)).</span></span>

-   <span data-ttu-id="a6c16-130">첫 번째 및 중간 점이 동일하지만 세 번째 점이 다른 경우(예: (1 3, 1 3, 7 5))</span><span class="sxs-lookup"><span data-stu-id="a6c16-130">When the first and middle point are the same, but the third point is different (for example, (1 3, 1 3, 7 5)).</span></span>

-   <span data-ttu-id="a6c16-131">중간 및 마지막 점이 동일하지만 첫 번째 점이 다른 경우(예: (1 3, 4 4, 4 4))</span><span class="sxs-lookup"><span data-stu-id="a6c16-131">When the middle and last point are the same, but the first point is different (for example, (1 3, 4 4, 4 4)).</span></span>

## <a name="examples"></a><span data-ttu-id="a6c16-132">예</span><span class="sxs-lookup"><span data-stu-id="a6c16-132">Examples</span></span>

### <a name="a-instantiating-a-geometry-instance-with-an-empty-circularstring"></a><span data-ttu-id="a6c16-133">A.</span><span class="sxs-lookup"><span data-stu-id="a6c16-133">A.</span></span> <span data-ttu-id="a6c16-134">빈 CircularString을 사용하여 Geometry 인스턴스 인스턴스화</span><span class="sxs-lookup"><span data-stu-id="a6c16-134">Instantiating a Geometry Instance with an Empty CircularString</span></span>
 <span data-ttu-id="a6c16-135">이 예에서는 빈 `CircularString` 인스턴스를 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="a6c16-135">This example shows how to create an empty `CircularString` instance:</span></span>

```sql
DECLARE @g geometry;
SET @g = geometry::Parse('CIRCULARSTRING EMPTY');
```

### <a name="b-instantiating-a-geometry-instance-using-a-circularstring-with-one-circular-arc-segment"></a><span data-ttu-id="a6c16-136">B.</span><span class="sxs-lookup"><span data-stu-id="a6c16-136">B.</span></span> <span data-ttu-id="a6c16-137">원호 세그먼트가 하나인 경우 CircularString을 사용하여 Geometry 인스턴스 인스턴스화</span><span class="sxs-lookup"><span data-stu-id="a6c16-137">Instantiating a Geometry Instance Using a CircularString with One Circular Arc Segment</span></span>
 <span data-ttu-id="a6c16-138">다음 예에서는 단일 원호 세그먼트(반원)를 사용하여 `CircularString` 인스턴스를 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="a6c16-138">The following example shows how to create a `CircularString` instance with a single circular arc segment (half-circle):</span></span>

```sql
DECLARE @g geometry;
SET @g = geometry:: STGeomFromText('CIRCULARSTRING(2 0, 1 1, 0 0)', 0);
SELECT @g.ToString();
```

### <a name="c-instantiating-a-geometry-instance-using-a-circularstring-with-multiple-circular-arc-segments"></a><span data-ttu-id="a6c16-139">C.</span><span class="sxs-lookup"><span data-stu-id="a6c16-139">C.</span></span> <span data-ttu-id="a6c16-140">원호 세그먼트가 여러 개인 경우 CircularString을 사용하여 Geometry 인스턴스 인스턴스화</span><span class="sxs-lookup"><span data-stu-id="a6c16-140">Instantiating a Geometry Instance Using a CircularString with Multiple Circular Arc Segments</span></span>
 <span data-ttu-id="a6c16-141">다음 예에서는 두 개 이상의 원호 세그먼트(완전한 원)를 사용하여 `CircularString` 인스턴스를 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="a6c16-141">The following example shows how to create a `CircularString` instance with more than one circular arc segment (full circle):</span></span>

```sql
DECLARE @g geometry;
SET @g = geometry::Parse('CIRCULARSTRING(2 1, 1 2, 0 1, 1 0, 2 1)');
SELECT 'Circumference = ' + CAST(@g.STLength() AS NVARCHAR(10));  
```

 <span data-ttu-id="a6c16-142">이 코드의 결과는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="a6c16-142">This produces the following output:</span></span>

```
Circumference = 6.28319
```

 <span data-ttu-id="a6c16-143">`LineString` 대신 `CircularString`을 사용하는 경우의 출력과 비교합니다.</span><span class="sxs-lookup"><span data-stu-id="a6c16-143">Compare the output when `LineString` is used instead of `CircularString`:</span></span>

```sql
DECLARE @g geometry;
SET @g = geometry::STGeomFromText('LINESTRING(2 1, 1 2, 0 1, 1 0, 2 1)', 0);
SELECT 'Perimeter = ' + CAST(@g.STLength() AS NVARCHAR(10));
```

 <span data-ttu-id="a6c16-144">이 코드의 결과는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="a6c16-144">This produces the following output:</span></span>

```
Perimeter = 5.65685
```

 <span data-ttu-id="a6c16-145">예제의 값은 `CircularString` 원의 실제 원주 인 2&#x03c0; (2 \* pi)에 가깝습니다.</span><span class="sxs-lookup"><span data-stu-id="a6c16-145">Notice that the value for the `CircularString` example is close to 2&#x03c0; (2 \* pi), which is the actual circumference of the circle.</span></span>

### <a name="d-declaring-and-instantiating-a-geometry-instance-with-a-circularstring-in-the-same-statement"></a><span data-ttu-id="a6c16-146">D.</span><span class="sxs-lookup"><span data-stu-id="a6c16-146">D.</span></span> <span data-ttu-id="a6c16-147">동일한 문에서 CircularString을 사용하여 Geometry 인스턴스 선언 및 인스턴스화</span><span class="sxs-lookup"><span data-stu-id="a6c16-147">Declaring and Instantiating a Geometry Instance with a CircularString in the Same Statement</span></span>
 <span data-ttu-id="a6c16-148">이 조각은 동일한 문에서 `geometry`을 사용하여 `CircularString` 인스턴스를 선언하고 인스턴스화하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="a6c16-148">This snippet shows how to declare and instantiate a `geometry` instance with a `CircularString` in the same statement:</span></span>

```sql
DECLARE @g geometry = 'CIRCULARSTRING(0 0, 1 2.1082, 3 6.3246, 0 7, -3 6.3246, -1 2.1082, 0 0)';
```

### <a name="e-instantiating-a-geography-instance-with-a-circularstring"></a><span data-ttu-id="a6c16-149">E.</span><span class="sxs-lookup"><span data-stu-id="a6c16-149">E.</span></span> <span data-ttu-id="a6c16-150">CircularString을 사용하여 Geography 인스턴스 인스턴스화</span><span class="sxs-lookup"><span data-stu-id="a6c16-150">Instantiating a Geography Instance with a CircularString</span></span>
 <span data-ttu-id="a6c16-151">다음 예에서는 `geography`을 사용하여 `CircularString` 인스턴스를 선언하고 인스턴스화하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="a6c16-151">The following example shows how to declare and instantiate a `geography` instance with a `CircularString`:</span></span>

```sql
DECLARE @g geography = 'CIRCULARSTRING(-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653)';
```

### <a name="f-instantiating-a-geometry-instance-with-a-circularstring-that-is-a-straight-line"></a><span data-ttu-id="a6c16-152">F.</span><span class="sxs-lookup"><span data-stu-id="a6c16-152">F.</span></span> <span data-ttu-id="a6c16-153">직선인 CircularString을 사용하여 Geometry 인스턴스 인스턴스화</span><span class="sxs-lookup"><span data-stu-id="a6c16-153">Instantiating a Geometry Instance with a CircularString that is a Straight Line</span></span>
 <span data-ttu-id="a6c16-154">다음 예에서는 직선인 `CircularString` 인스턴스를 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="a6c16-154">The following example shows how to create a `CircularString` instance that is a straight line:</span></span>

```sql
DECLARE @g geometry;
SET @g = geometry::STGeomFromText('CIRCULARSTRING(0 0, 1 2, 2 4)', 0);
```

## <a name="see-also"></a><span data-ttu-id="a6c16-155">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a6c16-155">See Also</span></span>
 <span data-ttu-id="a6c16-156">[공간 데이터 형식 개요](spatial-data-types-overview.md) [CompoundCurve](compoundcurve.md) [makevalid &#40;geography 데이터 형식&#41;](/sql/t-sql/spatial-geography/makevalid-geography-data-type) [makevalid &#40;geometry 데이터 형식&#41;](/sql/t-sql/spatial-geometry/makevalid-geometry-data-type) [stisvalid &#40;geometry](/sql/t-sql/spatial-geometry/stisvalid-geometry-data-type) 데이터 형식&#41;[stisvalid &#40;geography](/sql/t-sql/spatial-geography/stisvalid-geography-data-type) 데이터 형식&#41;[stisvalid](/sql/t-sql/spatial-geometry/stlength-geometry-data-type) &#40;Geometry 데이터 형식&#41;stisvalid [&#40;geometry 데이터](/sql/t-sql/spatial-geometry/ststartpoint-geometry-data-type) 형식&#41;[endpoint &#40;geometry 데이터 형식&#41;](/sql/t-sql/spatial-geometry/stendpoint-geometry-data-type) [stpointn &#40;geometry 데이터 형식&#41;](/sql/t-sql/spatial-geometry/stpointn-geometry-data-type) [stnumpoints](/sql/t-sql/spatial-geometry/stnumpoints-geometry-data-type) &#40;geometry 데이터 형식&#41;[stisring &#40;geometry](/sql/t-sql/spatial-geometry/stisring-geometry-data-type) 데이터 형식&#41;[STIsClosed &#40;geometry 데이터 형식](/sql/t-sql/spatial-geometry/stisclosed-geometry-data-type)&#41;[stpointonsurface &#40;geometry 데이터 형식](/sql/t-sql/spatial-geometry/stpointonsurface-geometry-data-type)&#41;[LineString](linestring.md)</span><span class="sxs-lookup"><span data-stu-id="a6c16-156">[Spatial Data Types Overview](spatial-data-types-overview.md) [CompoundCurve](compoundcurve.md) [MakeValid &#40;geography Data Type&#41;](/sql/t-sql/spatial-geography/makevalid-geography-data-type) [MakeValid &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/makevalid-geometry-data-type) [STIsValid &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/stisvalid-geometry-data-type) [STIsValid &#40;geography Data Type&#41;](/sql/t-sql/spatial-geography/stisvalid-geography-data-type) [STLength &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/stlength-geometry-data-type) [STStartPoint &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/ststartpoint-geometry-data-type) [STEndpoint &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/stendpoint-geometry-data-type) [STPointN &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/stpointn-geometry-data-type) [STNumPoints &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/stnumpoints-geometry-data-type) [STIsRing &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/stisring-geometry-data-type) [STIsClosed &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/stisclosed-geometry-data-type) [STPointOnSurface &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/stpointonsurface-geometry-data-type) [LineString](linestring.md)</span></span>


