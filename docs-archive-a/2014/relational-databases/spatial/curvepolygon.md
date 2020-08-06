---
title: CurvePolygon | Microsoft 문서
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
ms.assetid: e000a1d8-a049-4542-bfeb-943fd6ab3969
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: b90fdbd9a0bc80dfc6a82416d0193b2951fe13ef
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646853"
---
# <a name="curvepolygon"></a><span data-ttu-id="20369-102">CurvePolygon</span><span class="sxs-lookup"><span data-stu-id="20369-102">CurvePolygon</span></span>
  <span data-ttu-id="20369-103">`CurvePolygon`은 외부 경계 링과 0개 이상의 내부 링에서 정의하는 토폴로지 방식으로 닫힌 표면입니다.</span><span class="sxs-lookup"><span data-stu-id="20369-103">A `CurvePolygon` is a topologically closed surface defined by an exterior bounding ring and zero or more interior rings</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="20369-104">하위 유형을 포함 하 여에 도입 된 공간 기능에 대 한 자세한 설명 및 예를 보려면 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] `CurvePolygon` [SQL Server 2012의 새로운 공간 기능](https://go.microsoft.com/fwlink/?LinkId=226407)백서를 다운로드 하세요.</span><span class="sxs-lookup"><span data-stu-id="20369-104">For a detailed description and examples of spatial features introduced in [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], including the `CurvePolygon` subtype, download the white paper, [New Spatial Features in SQL Server 2012](https://go.microsoft.com/fwlink/?LinkId=226407).</span></span>  
  
 <span data-ttu-id="20369-105">다음 조건은 인스턴스의 특성을 정의 합니다 `CurvePolygon` .</span><span class="sxs-lookup"><span data-stu-id="20369-105">The following criteria define attributes of a `CurvePolygon` instance:</span></span>  
  
-   <span data-ttu-id="20369-106">`CurvePolygon` 인스턴스의 경계는 외부 링과 모든 내부 링으로 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="20369-106">The boundary of the `CurvePolygon` instance is defined by the exterior ring and all interior rings.</span></span>  
  
-   <span data-ttu-id="20369-107">`CurvePolygon` 인스턴스의 내부는 외부 링과 모든 내부 링 사이의 공간입니다.</span><span class="sxs-lookup"><span data-stu-id="20369-107">The interior of the `CurvePolygon` instance is the space between the exterior ring and all of the interior rings.</span></span>  
  
 <span data-ttu-id="20369-108">`CurvePolygon` 인스턴스는 `Polygon` 인스턴스와 다릅니다. `CurvePolygon` 인스턴스에는 원호 세그먼트인 `CircularString` 및 `CompoundCurve`가 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="20369-108">A `CurvePolygon` instance differs from a `Polygon` instance in that a `CurvePolygon` instance may contain the following circular arc segments: `CircularString` and `CompoundCurve`.</span></span>  
  
## <a name="compoundcurve-instances"></a><span data-ttu-id="20369-109">CompoundCurve 인스턴스</span><span class="sxs-lookup"><span data-stu-id="20369-109">CompoundCurve instances</span></span>  
 <span data-ttu-id="20369-110">다음 그림에서는 유효한 `CurvePolygon` 그림을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="20369-110">Illustration below shows valid `CurvePolygon` figures:</span></span>  
  
### <a name="accepted-instances"></a><span data-ttu-id="20369-111">허용되는 인스턴스</span><span class="sxs-lookup"><span data-stu-id="20369-111">Accepted instances</span></span>  
 <span data-ttu-id="20369-112">`CurvePolygon` 인스턴스가 허용되려면 해당 인스턴스가 비어 있거나 허용된 원호 링만 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="20369-112">For a `CurvePolygon` instance to be accepted, it needs to be either empty or contain only circular arc rings that are accepted.</span></span> <span data-ttu-id="20369-113">허용되는 원호 링은 다음 요구 사항을 충족합니다.</span><span class="sxs-lookup"><span data-stu-id="20369-113">An accepted circular arc ring meets the following requirements.</span></span>  
  
1.  <span data-ttu-id="20369-114">허용되는 `LineString`, `CircularString` 또는 `CompoundCurve` 인스턴스여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="20369-114">Is an accepted `LineString`, `CircularString`, or `CompoundCurve` instance.</span></span> <span data-ttu-id="20369-115">허용되는 인스턴스에 대한 자세한 내용은 [LineString](linestring.md), [CircularString](circularstring.md)및 [CompoundCurve](compoundcurve.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="20369-115">For more information on accepted instances, see [LineString](linestring.md), [CircularString](circularstring.md), and [CompoundCurve](compoundcurve.md).</span></span>  
  
2.  <span data-ttu-id="20369-116">4개 이상의 점이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="20369-116">Has at least four points.</span></span>  
  
3.  <span data-ttu-id="20369-117">시작점과 끝점의 X 및 Y 좌표가 동일해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="20369-117">The start and end point have the same X and Y coordinates.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="20369-118">Z 및 M 값이 무시되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="20369-118">Z and M values are ignored.</span></span>  
  
 <span data-ttu-id="20369-119">다음 예에서는 허용되는 `CurvePolygon` 인스턴스를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="20369-119">The following example shows accepted `CurvePolygon` instances.</span></span>  
  
```  
DECLARE @g1 geometry = 'CURVEPOLYGON EMPTY';  
DECLARE @g2 geometry = 'CURVEPOLYGON((0 0, 0 0, 0 0, 0 0))';  
DECLARE @g3 geometry = 'CURVEPOLYGON((0 0 1, 0 0 2, 0 0 3, 0 0 3))'  
DECLARE @g4 geometry = 'CURVEPOLYGON(CIRCULARSTRING(1 3, 3 5, 4 7, 7 3, 1 3))';  
DECLARE @g5 geography = 'CURVEPOLYGON((-122.3 47, 122.3 -47, 125.7 -49, 121 -38, -122.3 47))';  
```  
  
 <span data-ttu-id="20369-120">`@g3` 이 허용됩니다.</span><span class="sxs-lookup"><span data-stu-id="20369-120">`@g3` is accepted even though the start and end points have different Z values because Z values are ignored.</span></span> <span data-ttu-id="20369-121">`geography` 유형 인스턴스가 유효하지 않아도 `@g5`가 허용됩니다.</span><span class="sxs-lookup"><span data-stu-id="20369-121">`@g5` is accepted even though the `geography` type instance is not valid.</span></span>  
  
 <span data-ttu-id="20369-122">다음 예에서는 `System.FormatException`이 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="20369-122">The following examples throw `System.FormatException`.</span></span>  
  
```  
DECLARE @g1 geometry = 'CURVEPOLYGON((0 5, 0 0, 0 0, 0 0))';  
DECLARE @g2 geometry = 'CURVEPOLYGON((0 0, 0 0, 0 0))';  
```  
  
 <span data-ttu-id="20369-123">`@g1` 이 허용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="20369-123">`@g1` is not accepted because the start and end points do not have the same Y value.</span></span> <span data-ttu-id="20369-124">`@g2` 가 허용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="20369-124">`@g2` is not accepted because the ring does not have enough points.</span></span>  
  
### <a name="valid-instances"></a><span data-ttu-id="20369-125">유효한 인스턴스</span><span class="sxs-lookup"><span data-stu-id="20369-125">Valid instances</span></span>  
 <span data-ttu-id="20369-126">`CurvePolygon` 인스턴스가 유효하려면 외부 링과 내부 링이 모두 다음 조건을 충족해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="20369-126">For a `CurvePolygon` instance to be valid both exterior and interior rings must meet the following criteria:</span></span>  
  
1.  <span data-ttu-id="20369-127">이 두 링은 단일 탄젠트 점에서만 접할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="20369-127">They may only touch at single tangent points.</span></span>  
  
2.  <span data-ttu-id="20369-128">이 두 링은 서로 교차할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="20369-128">They cannot cross each other.</span></span>  
  
3.  <span data-ttu-id="20369-129">각 링에 4개 이상의 점이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="20369-129">Each ring must contain at least four points.</span></span>  
  
4.  <span data-ttu-id="20369-130">각 링이 허용 가능한 곡선 유형이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="20369-130">Each ring must be an acceptable curve type.</span></span>  
  
 <span data-ttu-id="20369-131">또한 `CurvePolygon` 인스턴스는 `geometry` 또는 `geography` 데이터 형식인지에 따라 특정 조건을 충족해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="20369-131">`CurvePolygon` instances also need to meet specific criteria depending on whether they are `geometry` or `geography` data types.</span></span>  
  
#### <a name="geometry-data-type"></a><span data-ttu-id="20369-132">Geometry 데이터 형식</span><span class="sxs-lookup"><span data-stu-id="20369-132">Geometry data type</span></span>  
 <span data-ttu-id="20369-133">유효한 **geometryCurvePolygon** 인스턴스는 다음 특성을 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="20369-133">A valid **geometryCurvePolygon** instance must have the following attributes:</span></span>  
  
1.  <span data-ttu-id="20369-134">모든 내부 링은 외부 링에 포함되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="20369-134">All the interior rings must be contained within the exterior ring.</span></span>  
  
2.  <span data-ttu-id="20369-135">내부 링이 여러 개일 수 있지만 내부 링은 다른 내부 링을 포함할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="20369-135">May have multiple interior rings, but an interior ring cannot contain another interior ring.</span></span>  
  
3.  <span data-ttu-id="20369-136">링은 자체적으로 또는 다른 링을 교차할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="20369-136">No ring can cross itself or another ring.</span></span>  
  
4.  <span data-ttu-id="20369-137">링은 단일 탄젠트 점(링 접촉이 한정된 점 수)에서만 접할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="20369-137">Rings can only touch at single tangent points (number of points where rings touch must be finite).</span></span>  
  
5.  <span data-ttu-id="20369-138">다각형 내부는 연결되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="20369-138">The interior of the polygon must be connected.</span></span>  
  
 <span data-ttu-id="20369-139">다음 예에서는 유효한 **geometryCurvePolygon** 인스턴스를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="20369-139">The following example shows valid **geometryCurvePolygon** instances.</span></span>  
  
```  
DECLARE @g1 geometry = 'CURVEPOLYGON EMPTY';  
DECLARE @g2 geometry = 'CURVEPOLYGON(CIRCULARSTRING(1 3, 3 5, 4 7, 7 3, 1 3))';  
SELECT @g1.STIsValid(), @g2.STIsValid();  
```  
  
 <span data-ttu-id="20369-140">CurvePolygon 인스턴스의 유효성 규칙은 Polygon 인스턴스의 유효성 규칙과 동일합니다. 단, CurvePolygon 인스턴스는 새 원호 세그먼트 유형을 허용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="20369-140">CurvePolygon instances have the same validity rules as Polygon instances with the exception that CurvePolygon instances may accept the new circular arc segment types.</span></span> <span data-ttu-id="20369-141">유효하거나 유효하지 않은 인스턴스에 대한 다른 예는 [Polygon](polygon.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="20369-141">For more examples of instances that are valid or not valid, see [Polygon](polygon.md).</span></span>  
  
#### <a name="geography-data-type"></a><span data-ttu-id="20369-142">Geography 데이터 형식</span><span class="sxs-lookup"><span data-stu-id="20369-142">Geography data type</span></span>  
 <span data-ttu-id="20369-143">유효한 **geographyCurvePolygon** 인스턴스는 다음 특성을 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="20369-143">A valid **geographyCurvePolygon** instance must have the following attributes:</span></span>  
  
1.  <span data-ttu-id="20369-144">다각형 내부는 왼쪽 규칙을 사용하여 연결됩니다.</span><span class="sxs-lookup"><span data-stu-id="20369-144">The interior of the polygon is connected using the left-hand rule.</span></span>  
  
2.  <span data-ttu-id="20369-145">링은 자체적으로 또는 다른 링을 교차할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="20369-145">No ring can cross itself or another ring.</span></span>  
  
3.  <span data-ttu-id="20369-146">링은 단일 탄젠트 점(링 접촉이 한정된 점 수)에서만 접할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="20369-146">Rings can only touch at single tangent points (number of points where rings touch must be finite).</span></span>  
  
4.  <span data-ttu-id="20369-147">다각형 내부는 연결되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="20369-147">The interior of the polygon must be connected.</span></span>  
  
 <span data-ttu-id="20369-148">다음 예에서는 유효한 geography CurvePolygon 인스턴스를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="20369-148">The following example shows a valid geography CurvePolygon instance.</span></span>  
  
```  
DECLARE @g geography = 'CURVEPOLYGON((-122.3 47, 122.3 47, 125.7 49, 121 38, -122.3 47))';  
SELECT @g.STIsValid();  
```  
  
## <a name="examples"></a><span data-ttu-id="20369-149">예</span><span class="sxs-lookup"><span data-stu-id="20369-149">Examples</span></span>  
  
### <a name="a-instantiating-a-geometry-instance-with-an-empty-curvepolygon"></a><span data-ttu-id="20369-150">A.</span><span class="sxs-lookup"><span data-stu-id="20369-150">A.</span></span> <span data-ttu-id="20369-151">빈 CurvePolygon을 사용하여 Geometry 인스턴스 인스턴스화</span><span class="sxs-lookup"><span data-stu-id="20369-151">Instantiating a Geometry Instance with an Empty CurvePolygon</span></span>  
 <span data-ttu-id="20369-152">이 예에서는 빈 `CurvePolygon` 인스턴스를 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="20369-152">This example shows how to create an empty `CurvePolygon` instance:</span></span>  
  
```sql  
DECLARE @g geometry;  
SET @g = geometry::Parse('CURVEPOLYGON EMPTY');  
```  
  
### <a name="b-declaring-and-instantiating-a-geometry-instance-with-a-curvepolygon-in-the-same-statement"></a><span data-ttu-id="20369-153">B.</span><span class="sxs-lookup"><span data-stu-id="20369-153">B.</span></span> <span data-ttu-id="20369-154">동일한 문에서 CurvePolygon을 사용하여 Geometry 인스턴스 선언 및 인스턴스화</span><span class="sxs-lookup"><span data-stu-id="20369-154">Declaring and Instantiating a Geometry Instance with a CurvePolygon in the Same Statement</span></span>  
 <span data-ttu-id="20369-155">이 코드 조각은 동일한 문에서 `CurvePolygon`을 사용하여 geography 인스턴스를 선언하고 초기화하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="20369-155">This code snippet shows how to declare and initialize a geometry instance with a `CurvePolygon` in the same statement:</span></span>  
  
```sql  
DECLARE @g geometry = 'CURVEPOLYGON(CIRCULARSTRING(2 4, 4 2, 6 4, 4 6, 2 4))'  
```  
  
### <a name="c-instantiating-a-geography-instance-with-a-curvepolygon"></a><span data-ttu-id="20369-156">C.</span><span class="sxs-lookup"><span data-stu-id="20369-156">C.</span></span> <span data-ttu-id="20369-157">CurvePolygon을 사용하여 Geography 인스턴스 인스턴스화</span><span class="sxs-lookup"><span data-stu-id="20369-157">Instantiating a Geography Instance with a CurvePolygon</span></span>  
 <span data-ttu-id="20369-158">이 코드 조각은 `geography`을 사용하여 `CurvePolygon` 인스턴스를 선언하고 초기화하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="20369-158">This code snippet shows how to declare and initialize a `geography` instance with a `CurvePolygon`:</span></span>  
  
```sql  
DECLARE @g geography = 'CURVEPOLYGON(CIRCULARSTRING(-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653))';  
```  
  
### <a name="d-storing-a-curvepolygon-with-only-an-exterior-bounding-ring"></a><span data-ttu-id="20369-159">D.</span><span class="sxs-lookup"><span data-stu-id="20369-159">D.</span></span> <span data-ttu-id="20369-160">외부 경계 링만 사용하여 CurvePolygon 저장</span><span class="sxs-lookup"><span data-stu-id="20369-160">Storing a CurvePolygon with Only an Exterior Bounding Ring</span></span>  
 <span data-ttu-id="20369-161">이 예에서는 단순 원을 `CurvePolygon` 인스턴스에 저장하는 방법을 보여 줍니다. 외부 경계 링만 사용하여 원을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="20369-161">This example shows how to store a simple circle in a `CurvePolygon` instance (only an exterior bounding ring is used to define the circle):</span></span>  
  
```sql  
DECLARE @g geometry;  
SET @g = geometry::Parse('CURVEPOLYGON(CIRCULARSTRING(2 4, 4 2, 6 4, 4 6, 2 4))');  
SELECT @g.STArea() AS Area;  
```  
  
### <a name="e-storing-a-curvepolygon-containing-interior-rings"></a><span data-ttu-id="20369-162">E.</span><span class="sxs-lookup"><span data-stu-id="20369-162">E.</span></span> <span data-ttu-id="20369-163">내부 링을 포함하는 CurvePolygon 저장</span><span class="sxs-lookup"><span data-stu-id="20369-163">Storing a CurvePolygon Containing Interior Rings</span></span>  
 <span data-ttu-id="20369-164">이 예에서는 `CurvePolygon` 인스턴스에서 도넛형을 만듭니다. 외부 경계 링과 내부 링을 모두 사용하여 도넛형을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="20369-164">This example creates a donut in a `CurvePolygon` instance (both an exterior bounding ring and an interior ring is used to define the donut):</span></span>  
  
```sql  
DECLARE @g geometry;  
SET @g = geometry::Parse('CURVEPOLYGON(CIRCULARSTRING(0 4, 4 0, 8 4, 4 8, 0 4), CIRCULARSTRING(2 4, 4 2, 6 4, 4 6, 2 4))');  
SELECT @g.STArea() AS Area;  
```  
  
 <span data-ttu-id="20369-165">이 예에서는 내부 링을 사용할 때 유효하지 않은 인스턴스 및 유효한 `CurvePolygon` 인스턴스를 모두 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="20369-165">This example shows both a valid `CurvePolygon` instance and an invalid instance when using interior rings:</span></span>  
  
```sql  
DECLARE @g1 geometry, @g2 geometry;  
SET @g1 = geometry::Parse('CURVEPOLYGON(CIRCULARSTRING(0 5, 5 0, 0 -5, -5 0, 0 5), (-2 2, 2 2, 2 -2, -2 -2, -2 2))');  
IF @g1.STIsValid() = 1  
  BEGIN  
     SELECT @g1.STArea();  
  END  
SET @g2 = geometry::Parse('CURVEPOLYGON(CIRCULARSTRING(0 5, 5 0, 0 -5, -5 0, 0 5), (0 5, 5 0, 0 -5, -5 0, 0 5))');  
IF @g2.STIsValid() = 1  
  BEGIN  
     SELECT @g2.STArea();  
  END  
SELECT @g1.STIsValid() AS G1, @g2.STIsValid() AS G2;  
```  
  
 <span data-ttu-id="20369-166">@g1과 @g2 모두 동일한 외부 경계 링을 사용합니다. 이 원의 반지름은 5이고 둘 다 내부 링에 대해 사각형을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="20369-166">Both @g1 and @g2 use the same exterior bounding ring: a circle with a radius of 5 and they both use a square for an interior ring.</span></span>  <span data-ttu-id="20369-167">그러나 @g1 인스턴스는 유효하고 @g2 인스턴스는 유효하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="20369-167">However, the instance @g1 is valid, but the instance @g2 is invalid.</span></span>  <span data-ttu-id="20369-168">@g2가 유효하지 않은 이유는 내부 링이 외부 링에 의해 경계가 지정된 내부 공간을 4개의 개별 영역으로 분할하기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="20369-168">The reason that @g2 is invalid is that the interior ring splits the interior space bounded by the exterior ring into four separate regions.</span></span>  <span data-ttu-id="20369-169">다음 그림에서는 이를 실행한 결과를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="20369-169">The following drawing shows what occurred:</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20369-170">참고 항목</span><span class="sxs-lookup"><span data-stu-id="20369-170">See Also</span></span>  
 <span data-ttu-id="20369-171">[Polygon](polygon.md) </span><span class="sxs-lookup"><span data-stu-id="20369-171">[Polygon](polygon.md) </span></span>  
 <span data-ttu-id="20369-172">[CircularString](circularstring.md) </span><span class="sxs-lookup"><span data-stu-id="20369-172">[CircularString](circularstring.md) </span></span>  
 <span data-ttu-id="20369-173">[CompoundCurve](compoundcurve.md) </span><span class="sxs-lookup"><span data-stu-id="20369-173">[CompoundCurve](compoundcurve.md) </span></span>  
 <span data-ttu-id="20369-174">[geometry 데이터 형식 메서드 참조](/sql/t-sql/spatial-geometry/spatial-types-geometry-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="20369-174">[geometry Data Type Method Reference](/sql/t-sql/spatial-geometry/spatial-types-geometry-transact-sql) </span></span>  
 <span data-ttu-id="20369-175">[geography 데이터 형식 메서드 참조](/sql/t-sql/spatial-geography/spatial-types-geography) </span><span class="sxs-lookup"><span data-stu-id="20369-175">[geography Data Type Method Reference](/sql/t-sql/spatial-geography/spatial-types-geography) </span></span>  
 [<span data-ttu-id="20369-176">공간 데이터 형식 개요</span><span class="sxs-lookup"><span data-stu-id="20369-176">Spatial Data Types Overview</span></span>](spatial-data-types-overview.md)  
  
  
