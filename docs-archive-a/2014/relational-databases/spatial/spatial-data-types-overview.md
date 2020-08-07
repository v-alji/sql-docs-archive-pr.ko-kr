---
title: 공간 데이터 형식 개요 | Microsoft 문서
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- geometry data type [SQL Server], understanding
- geography data type [SQL Server], spatial data
- planar spatial data [SQL Server], geometry data type
- spatial data types [SQL Server]
ms.assetid: 1615db50-69de-4778-8be6-4e058c00ccd4
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: c0548d974e83bfe2b1e103d4458b17078fba8014
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87735148"
---
# <a name="spatial-data-types-overview"></a><span data-ttu-id="2b80f-102">공간 데이터 형식 개요</span><span class="sxs-lookup"><span data-stu-id="2b80f-102">Spatial Data Types Overview</span></span>
  <span data-ttu-id="2b80f-103">공간 데이터 형식은 두 가지가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2b80f-103">There are two types of spatial data.</span></span> <span data-ttu-id="2b80f-104">`geometry` 데이터 형식은 평면, 즉 유클리드(평평한 표면) 데이터를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="2b80f-104">The `geometry` data type supports planar, or Euclidean (flat-earth), data.</span></span> <span data-ttu-id="2b80f-105">`geometry` 데이터 형식은 OGC(Open Geospatial Consortium)의 Simple Features for SQL Specification 버전 1.1.0을 따르며 SQL MM(ISO 표준)과 호환됩니다.</span><span class="sxs-lookup"><span data-stu-id="2b80f-105">The `geometry` data type both conforms to the Open Geospatial Consortium (OGC) Simple Features for SQL Specification version 1.1.0 and is compliant with SQL MM (ISO standard).</span></span>

 <span data-ttu-id="2b80f-106">또한 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]에서는 GPS 위도 및 경도 좌표 등의 타원(둥근 표면) 데이터를 저장하는 `geography` 데이터 형식을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="2b80f-106">In addition, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] supports the `geography` data type, which stores ellipsoidal (round-earth) data, such as GPS latitude and longitude coordinates.</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="2b80f-107">향상된 공간 데이터 형식을 비롯한 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]의 공간 기능에 대한 자세한 설명 및 예제를 보려면 [SQL Server 코드 이름 "Denali"의 새로운 공간 기능](https://go.microsoft.com/fwlink/?LinkId=226407)백서를 다운로드하세요.</span><span class="sxs-lookup"><span data-stu-id="2b80f-107">For a detailed description and examples of spatial features introduced in [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], including enhancements to the spatial data types, download the white paper, [New Spatial Features in SQL Server Code-Named "Denali"](https://go.microsoft.com/fwlink/?LinkId=226407).</span></span>

##  <a name="spatial-data-objects"></a><a name="objects"></a> <span data-ttu-id="2b80f-108">공간 데이터 개체</span><span class="sxs-lookup"><span data-stu-id="2b80f-108">Spatial Data Objects</span></span>
 <span data-ttu-id="2b80f-109">`geometry` 및 `geography` 데이터 형식은 16개의 공간 데이터 개체 또는 인스턴스 유형을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="2b80f-109">The `geometry` and `geography` data types support sixteen spatial data objects, or instance types.</span></span> <span data-ttu-id="2b80f-110">그러나 이러한 인스턴스 유형 중 11개만 *인스턴스화할 수 있고*데이터베이스에서 이러한 인스턴스를 만들고 작업(인스턴스화)할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2b80f-110">However, only eleven of these instance types are *instantiable*; you can create and work with these instances (or instantiate them) in a database.</span></span> <span data-ttu-id="2b80f-111">이러한 인스턴스는 `Points` , **linestrings, circularstring**, `CompoundCurves` , `Polygons` `CurvePolygons` 또는 `geometry` 에서 여러 또는 `geography` 인스턴스로 `GeometryCollection` 구분 하는 부모 데이터 형식에서 특정 속성을 파생 시킵니다.</span><span class="sxs-lookup"><span data-stu-id="2b80f-111">These instances derive certain properties from their parent data types that distinguish them as `Points`, **LineStrings, CircularStrings**, `CompoundCurves`, `Polygons`, `CurvePolygons` or as multiple `geometry` or `geography` instances in a `GeometryCollection`.</span></span> <span data-ttu-id="2b80f-112">`Geography` 형식에는 `FullGlobe`라는 추가 인스턴스 유형이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2b80f-112">`Geography` type has an additional instance type, `FullGlobe`.</span></span>

 <span data-ttu-id="2b80f-113">아래 그림에서는 `geometry` 및 `geometry` 데이터 형식의 기반인 `geography` 계층을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="2b80f-113">The figure below depicts the `geometry` hierarchy upon which the `geometry` and `geography` data types are based.</span></span> <span data-ttu-id="2b80f-114">및의 인스턴스화할 수 있는 형식은 `geometry` `geography` 파란색으로 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2b80f-114">The instantiable types of `geometry` and `geography` are indicated in blue.</span></span>

 <span data-ttu-id="2b80f-115">![geometry 유형의 계층](../../database-engine/media/geom-hierarchy.gif "geometry 유형의 계층")</span><span class="sxs-lookup"><span data-stu-id="2b80f-115">![Hierarchy of the geometry type](../../database-engine/media/geom-hierarchy.gif "Hierarchy of the geometry type")</span></span>

 <span data-ttu-id="2b80f-116">그림에서 알 수 있듯이 및 데이터 형식의 인스턴스화할 수 있는 10 개의 형식은,,,,,,,, `geometry` `geography` `Point` `MultiPoint` `LineString` `CircularString` `MultiLineString` `CompoundCurve` `Polygon` `CurvePolygon` `MultiPolygon` 및 `GeometryCollection` 입니다.</span><span class="sxs-lookup"><span data-stu-id="2b80f-116">As the figure indicates, the ten instantiable types of the `geometry` and `geography` data types are `Point`, `MultiPoint`, `LineString`, `CircularString`, `MultiLineString`, `CompoundCurve`, `Polygon`, `CurvePolygon`, `MultiPolygon`, and `GeometryCollection`.</span></span> <span data-ttu-id="2b80f-117">geography 데이터 형식의 경우 인스턴스화할 수 있는 추가 형식이 하나( `FullGlobe`) 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2b80f-117">There is one additional instantiable type for the geography data type: `FullGlobe`.</span></span> <span data-ttu-id="2b80f-118">`geometry`및 `geography` 형식은 인스턴스가 명시적으로 정의 되지 않은 경우에도 올바른 형식의 인스턴스인 경우 특정 인스턴스를 인식할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2b80f-118">The `geometry` and `geography` types can recognize a specific instance as long as it is a well-formed instance, even if the instance is not defined explicitly.</span></span> <span data-ttu-id="2b80f-119">예를 들어, `Point` STPointFromText () 메서드를 사용 하 여 인스턴스를 명시적으로 정의 하 `geometry` 고, `geography` `Point` 메서드 입력의 형식이 올바른 경우에는 인스턴스를으로 인식 합니다.</span><span class="sxs-lookup"><span data-stu-id="2b80f-119">For example, if you define a `Point` instance explicitly using the STPointFromText() method, `geometry` and `geography` recognize the instance as a `Point`, as long as the method input is well-formed.</span></span> <span data-ttu-id="2b80f-120">`STGeomFromText()` 메서드를 사용하여 동일한 인스턴스를 정의할 경우 `geometry` 및 `geography` 데이터 형식은 해당 인스턴스를 `Point`로 인식합니다.</span><span class="sxs-lookup"><span data-stu-id="2b80f-120">If you define the same instance using the `STGeomFromText()` method, both the `geometry` and `geography` data types recognize the instance as a `Point`.</span></span>

 <span data-ttu-id="2b80f-121">geometry 및 geography 형식의 하위 형식은 단순 형식과 컬렉션 형식으로 나뉩니다.</span><span class="sxs-lookup"><span data-stu-id="2b80f-121">The subtypes for geometry and geography types are divided into simple and collection types.</span></span>  <span data-ttu-id="2b80f-122">`STNumCurves()` 와 같은 일부 메서드는 단순 형식에서만 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="2b80f-122">Some methods like `STNumCurves()` work only with simple types.</span></span>

 <span data-ttu-id="2b80f-123">단순 형식에는 다음이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="2b80f-123">Simple types include:</span></span>

-   [<span data-ttu-id="2b80f-124">Point</span><span class="sxs-lookup"><span data-stu-id="2b80f-124">Point</span></span>](../spatial/point.md)

-   [<span data-ttu-id="2b80f-125">LineString</span><span class="sxs-lookup"><span data-stu-id="2b80f-125">LineString</span></span>](../spatial/linestring.md)

-   [<span data-ttu-id="2b80f-126">CircularString</span><span class="sxs-lookup"><span data-stu-id="2b80f-126">CircularString</span></span>](../spatial/circularstring.md)

-   [<span data-ttu-id="2b80f-127">CompoundCurve</span><span class="sxs-lookup"><span data-stu-id="2b80f-127">CompoundCurve</span></span>](../spatial/compoundcurve.md)

-   [<span data-ttu-id="2b80f-128">Polygon</span><span class="sxs-lookup"><span data-stu-id="2b80f-128">Polygon</span></span>](../spatial/polygon.md)

-   [<span data-ttu-id="2b80f-129">CurvePolygon</span><span class="sxs-lookup"><span data-stu-id="2b80f-129">CurvePolygon</span></span>](../spatial/curvepolygon.md)

 <span data-ttu-id="2b80f-130">컬렉션 형식에는 다음이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="2b80f-130">Collection types include:</span></span>

-   [<span data-ttu-id="2b80f-131">MultiPoint</span><span class="sxs-lookup"><span data-stu-id="2b80f-131">MultiPoint</span></span>](../spatial/multipoint.md)

-   [<span data-ttu-id="2b80f-132">MultiLineString</span><span class="sxs-lookup"><span data-stu-id="2b80f-132">MultiLineString</span></span>](../spatial/multilinestring.md)

-   [<span data-ttu-id="2b80f-133">MultiPolygon</span><span class="sxs-lookup"><span data-stu-id="2b80f-133">MultiPolygon</span></span>](../spatial/multipolygon.md)

-   [<span data-ttu-id="2b80f-134">GeometryCollection</span><span class="sxs-lookup"><span data-stu-id="2b80f-134">GeometryCollection</span></span>](../spatial/geometrycollection.md)


##  <a name="differences-between-the-geometry-and-geography-data-types"></a><a name="differences"></a> <span data-ttu-id="2b80f-135">geometry 데이터 형식과 geography 데이터 형식의 차이점</span><span class="sxs-lookup"><span data-stu-id="2b80f-135">Differences Between the geometry and geography Data Types</span></span>
 <span data-ttu-id="2b80f-136">공간 데이터의 두 가지 형식은 종종 매우 비슷하게 작동하지만 데이터가 저장되고 조작되는 방식에서 몇 가지 주요 차이점이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2b80f-136">The two types of spatial data often behave quite similarly, but there are some key differences in how the data is stored and manipulated.</span></span>

### <a name="how-connecting-edges-are-defined"></a><span data-ttu-id="2b80f-137">연결 가장자리가 정의되는 방식</span><span class="sxs-lookup"><span data-stu-id="2b80f-137">How connecting edges are defined</span></span>
 <span data-ttu-id="2b80f-138">`LineString` 및 `Polygon` 형식을 정의하는 데이터는 꼭지점뿐입니다.</span><span class="sxs-lookup"><span data-stu-id="2b80f-138">The defining data for `LineString` and `Polygon` types are vertices only.</span></span>  <span data-ttu-id="2b80f-139">geometry 형식에서 두 꼭지점을 잇는 연결 가장자리는 직선입니다.</span><span class="sxs-lookup"><span data-stu-id="2b80f-139">The connecting edge between two vertices in a geometry type is a straight line.</span></span>  <span data-ttu-id="2b80f-140">그러나 geography 형식에서는 두 꼭지점을 잇는 연결 가장자리가 두 꼭지점 사이의 짧고 큰 타원 호입니다.</span><span class="sxs-lookup"><span data-stu-id="2b80f-140">However, the connecting edge between two vertices in a geography type is a short great elliptic arc between the two vertices.</span></span>  <span data-ttu-id="2b80f-141">큰 타원은 타원면과 타원면의 중심을 관통하는 평면이 교차하는 지점이고 큰 타원 호는 큰 타원의 호 세그먼트입니다.</span><span class="sxs-lookup"><span data-stu-id="2b80f-141">A great ellipse is the intersection of the ellipsoid with a plane through its center and a great elliptic arc is an arc segment on the great ellipse.</span></span>

### <a name="how-circular-arc-segments-are-defined"></a><span data-ttu-id="2b80f-142">원호 세그먼트가 정의되는 방식</span><span class="sxs-lookup"><span data-stu-id="2b80f-142">How circular arc segments are defined</span></span>
 <span data-ttu-id="2b80f-143">geometry 형식의 원호 세그먼트는 XY 데카르트 좌표 평면(Z 값은 무시됨)에 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="2b80f-143">Circular arc segments for geometry types are defined on the XY Cartesian coordinate plane (Z values are ignored).</span></span> <span data-ttu-id="2b80f-144">geography 형식의 원호 세그먼트는 참조 구의 곡선 세그먼트로 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="2b80f-144">Circular arc segments for geography types are defined by curve segments on a reference sphere.</span></span> <span data-ttu-id="2b80f-145">참조 구의 위도선은 두 호의 점이 일정한 위도를 갖는 두 개의 보완 원호로 정의될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2b80f-145">Any parallel on the reference sphere can be defined by two complementary circular arcs where the points for both arcs have a constant latitude angle.</span></span>

### <a name="measurements-in-spatial-data-types"></a><span data-ttu-id="2b80f-146">공간 데이터 형식의 측정</span><span class="sxs-lookup"><span data-stu-id="2b80f-146">Measurements in spatial data types</span></span>
 <span data-ttu-id="2b80f-147">평면(또는 평평한 표면) 시스템에서 거리와 영역의 측정은 좌표와 동일한 측정 단위로 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="2b80f-147">In the planar, or flat-earth, system, measurements of distances and areas are given in the same unit of measurement as coordinates.</span></span> <span data-ttu-id="2b80f-148">`geometry` 데이터 형식을 이용하면 사용한 단위에 상관없이 (2, 2)와 (5, 6) 사이의 거리는 5단위입니다.</span><span class="sxs-lookup"><span data-stu-id="2b80f-148">Using the `geometry` data type, the distance between (2, 2) and (5, 6) is 5 units, regardless of the units used.</span></span>

 <span data-ttu-id="2b80f-149">타원 또는 둥근 지구 시스템에서 좌표는 위도와 경도의 도 단위로 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="2b80f-149">In the ellipsoidal, or round-earth system, coordinates are given in degrees of latitude and longitude.</span></span> <span data-ttu-id="2b80f-150">그러나 `geography` 인스턴스의 SRID(spatial reference identifier)에 따라 측정이 달라지더라도 길이 및 영역은 일반적으로 미터와 제곱미터로 측정됩니다.</span><span class="sxs-lookup"><span data-stu-id="2b80f-150">However, lengths and areas are usually measured in meters and square meters, though the measurement may depend on the spatial reference identifier (SRID) of the `geography` instance.</span></span> <span data-ttu-id="2b80f-151">가장 일반적인 `geography` 데이터 형식의 측정 단위는 미터입니다.</span><span class="sxs-lookup"><span data-stu-id="2b80f-151">The most common unit of measurement for the `geography` data type is meters.</span></span>

### <a name="orientation-of-spatial-data"></a><span data-ttu-id="2b80f-152">공간 데이터의 방향</span><span class="sxs-lookup"><span data-stu-id="2b80f-152">Orientation of spatial data</span></span>
 <span data-ttu-id="2b80f-153">평면 시스템에서 다각형의 링 방향은 중요한 요소가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="2b80f-153">In the planar system, the ring orientation of a polygon is not an important factor.</span></span> <span data-ttu-id="2b80f-154">예를 들어 ((0, 0), (10, 0), (0, 20), (0, 0))로 나타내는 다각형은 ((0, 0), (0, 20), (10, 0), (0, 0))로 나타내는 다각형과 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="2b80f-154">For example, a polygon described by ((0, 0), (10, 0), (0, 20), (0, 0)) is the same as a polygon described by ((0, 0), (0, 20), (10, 0), (0, 0)).</span></span> <span data-ttu-id="2b80f-155">OGC Simple Features for SQL Specification에서는 링 순서를 지정하지 않으며 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 에서는 링 순서를 강제로 지정하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2b80f-155">The OGC Simple Features for SQL Specification does not dictate a ring ordering, and [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] does not enforce ring ordering.</span></span>

 <span data-ttu-id="2b80f-156">타원 시스템에서 방향이 없는 다각형은 아무 의미가 없거나 모호합니다.</span><span class="sxs-lookup"><span data-stu-id="2b80f-156">In an ellipsoidal system, a polygon has no meaning, or is ambiguous, without an orientation.</span></span> <span data-ttu-id="2b80f-157">적도 주변 링이 남반구 또는 북반구를 나타내는지 여부를 예로 들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2b80f-157">For example, does a ring around the equator describe the northern or southern hemisphere?</span></span> <span data-ttu-id="2b80f-158">`geography` 데이터 형식을 사용하여 공간 인스턴스를 저장할 경우 링의 방향을 지정하고 인스턴스의 위치를 정확하게 나타내야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2b80f-158">If we use the `geography` data type to store the spatial instance, we must specify the orientation of the ring and accurately describe the location of the instance.</span></span> <span data-ttu-id="2b80f-159">타원 시스템의 다각형 내부는 왼쪽 규칙으로 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="2b80f-159">The interior of the polygon in an ellipsoidal system is defined by the left-hand rule.</span></span>

 <span data-ttu-id="2b80f-160">호환성 수준이 100 이하인 경우 데이터 형식에는 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] `geography` 다음과 같은 제한 사항이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2b80f-160">When the compatibility level is 100 or below in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] then the `geography` data type has the following restrictions:</span></span>

-   <span data-ttu-id="2b80f-161">각 `geography` 인스턴스가 단일 반구 내에 포함되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2b80f-161">Each `geography` instance must fit inside a single hemisphere.</span></span> <span data-ttu-id="2b80f-162">반구보다 큰 공간 개체는 저장할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2b80f-162">No spatial objects larger than a hemisphere can be stored.</span></span>

-   <span data-ttu-id="2b80f-163">반구보다 큰 개체를 생성하는 OGC(Open Geospatial Consortium) WKT(Well-Known Text) 또는 WKB(Well-Known Binary) 표현의 모든 `geography` 인스턴스에서 `ArgumentException`이 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="2b80f-163">Any `geography` instance from an Open Geospatial Consortium (OGC) Well-Known Text (WKT) or Well-Known Binary (WKB) representation that produces an object larger than a hemisphere throws an `ArgumentException`.</span></span>

-   <span data-ttu-id="2b80f-164">`geography` `geography` Stintersection (), stintersection (), stintersection () 및 Stsym차집합을 ()와 같이 두 개의 인스턴스를 입력 해야 하는 데이터 형식 메서드는 메서드의 결과가 단일 반구 내에 포함 되지 않는 경우 null을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="2b80f-164">The `geography` data type methods that require the input of two `geography` instances, such as STIntersection(), STUnion(), STDifference(), and STSymDifference(), will return null if the results from the methods do not fit inside a single hemisphere.</span></span> <span data-ttu-id="2b80f-165">STBuffer()도 결과가 단일 반구를 초과할 경우 null을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="2b80f-165">STBuffer() will also return null if the output exceeds a single hemisphere.</span></span>

 <span data-ttu-id="2b80f-166">[!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]에서 `FullGlobe`는 전체 구형을 포함하는 특수한 유형의 다각형입니다.</span><span class="sxs-lookup"><span data-stu-id="2b80f-166">In [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)], `FullGlobe` is a special type of Polygon that covers the entire globe.</span></span> <span data-ttu-id="2b80f-167">`FullGlobe`에는 영역이 있지만 테두리나 꼭지점은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2b80f-167">`FullGlobe` has an area, but no borders or vertices.</span></span>

### <a name="outer-and-inner-rings-not-important-in-geography-data-type"></a><span data-ttu-id="2b80f-168">geography 데이터 형식에서 중요하지 않은 외부 및 내부 링</span><span class="sxs-lookup"><span data-stu-id="2b80f-168">Outer and inner rings not important in geography data type</span></span>
 <span data-ttu-id="2b80f-169">OGC Simple Features for SQL Specification에서는 외부 링 및 내부 링에 대해 설명 하지만 이러한 구분은 데이터 형식에 대해 거의 의미가 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] `geography` 없습니다. 다각형의 링은 외부 링으로 사용 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2b80f-169">The OGC Simple Features for SQL Specification discusses outer rings and inner rings, but this distinction makes little sense for the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] `geography` data type; any ring of a polygon can be taken to be the outer ring.</span></span>

 <span data-ttu-id="2b80f-170">OGC 사양에 대한 자세한 내용은 다음을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="2b80f-170">For more information on OGC specifications, see the following:</span></span>

-   [<span data-ttu-id="2b80f-171">OGC Specifications, Simple Feature Access Part 1 - Common Architecture</span><span class="sxs-lookup"><span data-stu-id="2b80f-171">OGC Specifications, Simple Feature Access Part 1 - Common Architecture</span></span>](https://go.microsoft.com/fwlink/?LinkId=93627)

-   [<span data-ttu-id="2b80f-172">OGC Specifications, Simple Feature Access Part 2 - SQL Options</span><span class="sxs-lookup"><span data-stu-id="2b80f-172">OGC Specifications, Simple Feature Access Part 2 - SQL Options</span></span>](https://go.microsoft.com/fwlink/?LinkId=93628)


##  <a name="circular-arc-segments"></a><a name="circular"></a> <span data-ttu-id="2b80f-173">원호 세그먼트</span><span class="sxs-lookup"><span data-stu-id="2b80f-173">Circular Arc Segments</span></span>
 <span data-ttu-id="2b80f-174">인스턴스화할 수 있는 세 가지 형식은 원호 세그먼트 `CircularString`, `CompoundCurve` 및 `CurvePolygon`을 취할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2b80f-174">Three instantiable types can take circular arc segments: `CircularString`, `CompoundCurve`, and `CurvePolygon`.</span></span>  <span data-ttu-id="2b80f-175">원호 세그먼트는 2차원 평면에서 3개의 점으로 정의되며 세 번째 점은 첫 번째 점과 같을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2b80f-175">A circular arc segment is defined by three points in a two dimensional plane and the third point cannot be the same as the first point.</span></span>

 <span data-ttu-id="2b80f-176">그림 A와 B에서는 일반적인 원호 세그먼트를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="2b80f-176">Figures A and B show typical circular arc segments.</span></span> <span data-ttu-id="2b80f-177">세 개의 각 점이 원의 둘레에 어떻게 놓이는지 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="2b80f-177">Note how each of the three points lie on the perimeter of a circle.</span></span>

 <span data-ttu-id="2b80f-178">그림 C와 D에서는 선 세그먼트를 원호 세그먼트로 정의할 수 있는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="2b80f-178">Figures C and D show how a line segment can be defined as a circular arc segment.</span></span>  <span data-ttu-id="2b80f-179">두 개의 점으로만 정의할 수 있는 일반적인 선 세그먼트와 달리 원호 세그먼트를 정의하려면 세 개의 점이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="2b80f-179">Note that three points are still needed to define the circular arc segment unlike a regular line segment which can be defined by just two points.</span></span>

 <span data-ttu-id="2b80f-180">원호 세그먼트 형식에서 작동하는 메서드는 직선 세그먼트를 사용하여 원호를 대략적으로 나타냅니다. 호를 대략적으로 나타내는 데 사용되는 선 세그먼트의 수는 호의 길이와 곡률에 따라 달라집니다. 각 원호 세그먼트 형식에 대해 Z 값을 저장할 수 있지만 메서드는 계산에 Z 값을 사용하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2b80f-180">Methods operating on circular arc segment types use straight line segments to approximate the circular arc. The number of line segments used to approximate the arc will depend on the length and curvature of the arc. Z values can be stored for each of the circular arc segment types; however, methods will not use the Z values in their calculations.</span></span>

> [!NOTE]
>  <span data-ttu-id="2b80f-181">원호 세그먼트에 Z 값이 지정된 경우 원호 세그먼트의 모든 점에 대해 Z 값이 동일해야만 해당 원호 세그먼트를 입력할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2b80f-181">If Z values are given for circular arc segments then they must be the same for all points in the circular arc segment for it to be accepted for input.</span></span> <span data-ttu-id="2b80f-182">예: `CIRCULARSTRING(0 0 1, 2 2 1, 4 0 1)` 은 허용되지만 `CIRCULARSTRING(0 0 1, 2 2 2, 4 0 1)` 은 허용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2b80f-182">For example: `CIRCULARSTRING(0 0 1, 2 2 1, 4 0 1)` is accepted, but `CIRCULARSTRING(0 0 1, 2 2 2, 4 0 1)` is not accepted.</span></span>

### <a name="linestring-and-circularstring-comparison"></a><span data-ttu-id="2b80f-183">LineString 및 CircularString 비교</span><span class="sxs-lookup"><span data-stu-id="2b80f-183">LineString and CircularString comparison</span></span>
 <span data-ttu-id="2b80f-184">다음 다이어그램에서는 동일한 이등변 삼각형을 보여 줍니다. 삼각형 A는 선 세그먼트를 사용하여 삼각형을 정의하고 삼각형 B는 원호 세그먼트를 사용하여 삼각형을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="2b80f-184">The following diagram shows identical isosceles triangles (triangle A uses line segments to define the triangle and triangle B uses circular arc segments to defined the triangle):</span></span>

 ![](../../database-engine/media/7e382f76-59da-4b62-80dc-caf93e637c14.png "7e382f76-59da-4b62-80dc-caf93e637c14")

 <span data-ttu-id="2b80f-185">이 예에서는 `LineString` 인스턴스와 `CircularString`인스턴스를 모두 사용하여 위의 이등변 삼각형을 저장하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="2b80f-185">This example shows how to store the above isosceles triangles using both a `LineString` instance and `CircularString` instance:</span></span>

```sql
DECLARE @g1 geometry;
DECLARE @g2 geometry;
SET @g1 = geometry::STGeomFromText('LINESTRING(1 1, 5 1, 3 5, 1 1)', 0);
SET @g2 = geometry::STGeomFromText('CIRCULARSTRING(1 1, 3 1, 5 1, 4 3, 3 5, 2 3, 1 1)', 0);
IF @g1.STIsValid() = 1 AND @g2.STIsValid() = 1
  BEGIN
      SELECT @g1.ToString(), @g2.ToString()
      SELECT @g1.STLength() AS [LS Length], @g2.STLength() AS [CS Length]
  END
```

 <span data-ttu-id="2b80f-186">삼각형을 정의하는 데 `CircularString` 인스턴스에는 7개의 점이 필요하지만 `LineString` 인스턴스에는 4개의 점만 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="2b80f-186">Notice that a `CircularString` instance requires seven points to define the triangle, but a `LineString` instance requires only four points to define the triangle.</span></span> <span data-ttu-id="2b80f-187">이는 `CircularString` 인스턴스가 원호 세그먼트만 저장하고 선 세그먼트는 저장하지 않기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="2b80f-187">The reason for this is that a `CircularString` instance stores circular arc segments and not line segments.</span></span> <span data-ttu-id="2b80f-188">따라서 `CircularString` 인스턴스에 저장된 삼각형의 면은 ABC, CDE 및 EFA이지만 `LineString` 인스턴스에 저장된 삼각형의 면은 AC, CE 및 EA입니다.</span><span class="sxs-lookup"><span data-stu-id="2b80f-188">So the sides of the triangle stored in the `CircularString` instance are ABC, CDE, and EFA whereas the sides of the triangle stored in the `LineString` instance are AC, CE, and EA.</span></span>

 <span data-ttu-id="2b80f-189">다음 코드 조각을 살펴봅니다.</span><span class="sxs-lookup"><span data-stu-id="2b80f-189">Consider the following code snippet:</span></span>

```sql
SET @g1 = geometry::STGeomFromText('LINESTRING(0 0, 2 2, 4 0)', 0);
SET @g2 = geometry::STGeomFromText('CIRCULARSTRING(0 0, 2 2, 4 0)', 0);
SELECT @g1.STLength() AS [LS Length], @g2.STLength() AS [CS Length];
```

 <span data-ttu-id="2b80f-190">이 조각은 다음 결과를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="2b80f-190">This snippet will produce the following results:</span></span>

```
LS LengthCS Length
5.65685...6.28318...
```

 <span data-ttu-id="2b80f-191">다음 그림에서는 각 형식이 저장 되는 방법을 보여 줍니다. 빨간색 선은 `LineString``@g1` 를 나타내고 파란색 선은를 나타냅니다 `CircularString``@g2` .</span><span class="sxs-lookup"><span data-stu-id="2b80f-191">The following illustration shows how each type is stored (red line shows `LineString``@g1`, blue line shows `CircularString``@g2`):</span></span>

 ![](../../database-engine/media/e52157b5-5160-4a4b-8560-50cdcf905b76.png "e52157b5-5160-4a4b-8560-50cdcf905b76")

 <span data-ttu-id="2b80f-192">위의 그림과 같이 `CircularString` 인스턴스는 보다 적은 수의 점을 사용하여 `LineString` 인스턴스보다 정확도가 높은 곡선 경계를 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="2b80f-192">As the illustration above shows, `CircularString` instances use fewer points to store curve boundaries with greater precision than `LineString` instances.</span></span> <span data-ttu-id="2b80f-193">`CircularString` 인스턴스는 특정 지점에서 반경 32km 이내 검색과 같이 원 경계를 저장하는 데 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="2b80f-193">`CircularString` instances are useful for storing circular boundaries like a twenty-mile search radius from a specific point.</span></span> <span data-ttu-id="2b80f-194">`LineString` 인스턴스는 사각형 도시 블록과 같이 선형인 경계를 저장하는 데 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="2b80f-194">`LineString` instances are good for storing boundaries that are linear like a square city block.</span></span>

### <a name="linestring-and-compoundcurve-comparison"></a><span data-ttu-id="2b80f-195">LineString 및 CompoundCurve 비교</span><span class="sxs-lookup"><span data-stu-id="2b80f-195">LineString and CompoundCurve comparison</span></span>
 <span data-ttu-id="2b80f-196">다음 코드 예제에서는 `LineString` 및 `CompoundCurve` 인스턴스를 사용하여 동일한 그림을 저장하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="2b80f-196">The following code examples show how to store the same figure using `LineString` and `CompoundCurve` instances:</span></span>

```sql
SET @g = geometry::Parse('LINESTRING(2 2, 4 2, 4 4, 2 4, 2 2)');
SET @g = geometry::Parse('COMPOUNDCURVE((2 2, 4 2), (4 2, 4 4), (4 4, 2 4), (2 4, 2 2))');
SET @g = geometry::Parse('COMPOUNDCURVE((2 2, 4 2, 4 4, 2 4, 2 2))');
```

 <span data-ttu-id="2b80f-197">또는</span><span class="sxs-lookup"><span data-stu-id="2b80f-197">or</span></span>

 <span data-ttu-id="2b80f-198">위 예제에서 `LineString` 인스턴스나 `CompoundCurve` 인스턴스는 그림을 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2b80f-198">In the examples above, either a `LineString` instance or a `CompoundCurve` instance could store the figure.</span></span>  <span data-ttu-id="2b80f-199">다음 예제에서는 `CompoundCurve`를 사용하여 원형 조각을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="2b80f-199">This next example uses a `CompoundCurve` to store a pie slice:</span></span>

```sql
SET @g = geometry::Parse('COMPOUNDCURVE(CIRCULARSTRING(2 2, 1 3, 0 2),(0 2, 1 0, 2 2))');
```

 <span data-ttu-id="2b80f-200">`CompoundCurve` 인스턴스는 원호 세그먼트(2 2, 1 3, 0 2)를 직접 저장할 수 있지만 `LineString` 인스턴스는 곡선을 몇 개의 작은 선 세그먼트로 변환해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2b80f-200">A `CompoundCurve` instance can store the circular arc segment (2 2, 1 3, 0 2) directly whereas a `LineString` instance would have to convert the curve into several smaller line segments.</span></span>

### <a name="circularstring-and-compoundcurve-comparison"></a><span data-ttu-id="2b80f-201">CircularString 및 CompoundCurve 비교</span><span class="sxs-lookup"><span data-stu-id="2b80f-201">CircularString and CompoundCurve comparison</span></span>
 <span data-ttu-id="2b80f-202">다음 코드 예제에서는 `CircularString` 인스턴스에 원형 조각을 저장하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="2b80f-202">The following code example shows how the pie slice can be stored in a `CircularString` instance:</span></span>

```sql
DECLARE @g geometry;
SET @g = geometry::Parse('CIRCULARSTRING( 0 0, 1 2.1082, 3 6.3246, 0 7, -3 6.3246, -1 2.1082, 0 0)');
SELECT @g.ToString(), @g.STLength();
```

 <span data-ttu-id="2b80f-203">`CircularString` 인스턴스를 사용하여 원형 조각을 저장하려면 각 선 세그먼트에 세 개의 점을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2b80f-203">To store the pie slice using a `CircularString` instance requires that three points be used for each line segment.</span></span>  <span data-ttu-id="2b80f-204">중간 점을 알 수 없으면 다음 조각과 같이 선 세그먼트의 엔드포인트를 계산하거나 따옴표로 묶어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2b80f-204">If an intermediate point is not known, it either has to be calculated or the endpoint of the line segment has to be doubled as the following snippet shows:</span></span>

```sql
SET @g = geometry::Parse('CIRCULARSTRING( 0 0, 3 6.3246, 3 6.3246, 0 7, -3 6.3246, 0 0, 0 0)');
```

 <span data-ttu-id="2b80f-205">`CompoundCurve`인스턴스는 `LineString` 및 `CircularString` 구성 요소를 모두 허용 하므로 원형 조각의 선 세그먼트에 대 한 두 개의 지점만 알고 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2b80f-205">`CompoundCurve` instances allow both `LineString` and `CircularString` components so that only two points to the line segments of the pie slice need to be known.</span></span>  <span data-ttu-id="2b80f-206">이 코드 예제에서는 `CompoundCurve`를 사용하여 동일한 그림을 저장하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="2b80f-206">This code example shows how to use a `CompoundCurve` to store the same figure:</span></span>

```sql
DECLARE @g geometry;
SET @g = geometry::Parse('COMPOUNDCURVE(CIRCULARSTRING( 3 6.3246, 0 7, -3 6.3246), (-3 6.3246, 0 0, 3 6.3246))');
SELECT @g.ToString(), @g.STLength();
```

### <a name="polygon-and-curvepolygon-comparison"></a><span data-ttu-id="2b80f-207">Polygon 및 CurvePolygon 비교</span><span class="sxs-lookup"><span data-stu-id="2b80f-207">Polygon and CurvePolygon comparison</span></span>
 <span data-ttu-id="2b80f-208">`CurvePolygon` 인스턴스는 외부 및 내부 링을 정의할 때 `CircularString` 및 `CompoundCurve` 인스턴스를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2b80f-208">`CurvePolygon` instances can use `CircularString` and `CompoundCurve` instances when defining their exterior and interior rings.</span></span>  <span data-ttu-id="2b80f-209">`Polygon` 인스턴스는 원호 세그먼트 형식인 `CircularString` 및 `CompoundCurve`를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="2b80f-209">`Polygon` instances cannot use the circular arc segment types: `CircularString` and `CompoundCurve`.</span></span>


## <a name="see-also"></a><span data-ttu-id="2b80f-210">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2b80f-210">See Also</span></span>
 <span data-ttu-id="2b80f-211">[공간 데이터 &#40;SQL Server&#41;](../spatial/spatial-data-sql-server.md) [Geometry 데이터 형식 메서드 참조](/sql/t-sql/spatial-geometry/spatial-types-geometry-transact-sql) [geography 데이터 형식 메서드 참조](/sql/t-sql/spatial-geography/spatial-types-geography) [stnumcurves &#40;geometry 데이터](/sql/t-sql/spatial-geometry/stnumcurves-geometry-data-type) 형식&#41;[geography 데이터 형식](/sql/t-sql/spatial-geography/stnumcurves-geography-data-type) &#40;[STGeomFromText&#41;geometry 데이터 형식 &#40;](/sql/t-sql/spatial-geometry/stgeomfromtext-geometry-data-type) [STGeomFromText&#41;geography 데이터 형식 &#40;](/sql/t-sql/spatial-geography/stgeomfromtext-geography-data-type)</span><span class="sxs-lookup"><span data-stu-id="2b80f-211">[Spatial Data &#40;SQL Server&#41;](../spatial/spatial-data-sql-server.md) [geometry Data Type Method Reference](/sql/t-sql/spatial-geometry/spatial-types-geometry-transact-sql) [geography Data Type Method Reference](/sql/t-sql/spatial-geography/spatial-types-geography) [STNumCurves &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/stnumcurves-geometry-data-type) [STNumCurves &#40;geography Data Type&#41;](/sql/t-sql/spatial-geography/stnumcurves-geography-data-type) [STGeomFromText &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/stgeomfromtext-geometry-data-type) [STGeomFromText &#40;geography Data Type&#41;](/sql/t-sql/spatial-geography/stgeomfromtext-geography-data-type)</span></span>


