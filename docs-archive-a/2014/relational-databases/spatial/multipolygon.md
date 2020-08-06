---
title: MultiPolygon | Microsoft 문서
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- MultiPolygon geometry subtype [SQL Server]
- geometry subtypes [SQL Server]
ms.assetid: 2c5db358-2a16-49d9-aac5-a74e86813932
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: f18fd2485c9b2e62586d9f3e81f76f6cf680dbfc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660428"
---
# <a name="multipolygon"></a><span data-ttu-id="ed536-102">MultiPolygon</span><span class="sxs-lookup"><span data-stu-id="ed536-102">MultiPolygon</span></span>
  <span data-ttu-id="ed536-103">`MultiPolygon` 인스턴스는 1개 이상의 `Polygon` 인스턴스 컬렉션입니다.</span><span class="sxs-lookup"><span data-stu-id="ed536-103">A `MultiPolygon` instance is a collection of zero or more `Polygon` instances.</span></span>

## <a name="polygon-instances"></a><span data-ttu-id="ed536-104">Polygon 인스턴스</span><span class="sxs-lookup"><span data-stu-id="ed536-104">Polygon Instances</span></span>
 <span data-ttu-id="ed536-105">다음 그림에서는 `MultiPolygon` 인스턴스의 예를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ed536-105">The illustration below shows examples of `MultiPolygon` instances.</span></span>

 <span data-ttu-id="ed536-106">![기하 도형 MultiPolygon 인스턴스의 예](../../database-engine/media/multipolygon.gif "기하 도형 MultiPolygon 인스턴스의 예")</span><span class="sxs-lookup"><span data-stu-id="ed536-106">![Examples of geometry MultiPolygon instances](../../database-engine/media/multipolygon.gif "Examples of geometry MultiPolygon instances")</span></span>

 <span data-ttu-id="ed536-107">그림에 대한 설명:</span><span class="sxs-lookup"><span data-stu-id="ed536-107">As shown in the illustration:</span></span>

-   <span data-ttu-id="ed536-108">그림 1은 두 개의 `Polygon` 요소가 있는 `MultiPolygon` 인스턴스입니다.</span><span class="sxs-lookup"><span data-stu-id="ed536-108">Figure 1 is a `MultiPolygon` instance with two `Polygon` elements.</span></span> <span data-ttu-id="ed536-109">경계는 두 개의 외부 링과 세 개의 내부 링으로 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="ed536-109">The boundary is defined by the two exterior rings and the three interior rings.</span></span>

-   <span data-ttu-id="ed536-110">그림 2는 두 개의 `MultiPolygon` 요소가 있는 `Polygon` 인스턴스입니다.</span><span class="sxs-lookup"><span data-stu-id="ed536-110">Figure 2 is a `MultiPolygon` instance with two `Polygon` elements.</span></span> <span data-ttu-id="ed536-111">경계는 두 개의 외부 링과 세 개의 내부 링으로 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="ed536-111">The boundary is defined by the two exterior rings and the three interior rings.</span></span> <span data-ttu-id="ed536-112">두 개의 `Polygon` 요소는 탄젠트 점에서 교차합니다.</span><span class="sxs-lookup"><span data-stu-id="ed536-112">The two `Polygon` elements intersect at a tangent point.</span></span>

### <a name="accepted-instances"></a><span data-ttu-id="ed536-113">허용되는 인스턴스</span><span class="sxs-lookup"><span data-stu-id="ed536-113">Accepted Instances</span></span>
 <span data-ttu-id="ed536-114">다음 조건 중 하나가 만족되면 `MultiPolygon` 인스턴스는 허용됩니다.</span><span class="sxs-lookup"><span data-stu-id="ed536-114">A `MultiPolygon` instance is accepted one of the following conditions is met.</span></span>

-   <span data-ttu-id="ed536-115">빈 `MultiPolygon` 인스턴스인 경우</span><span class="sxs-lookup"><span data-stu-id="ed536-115">It is an empty `MultiPolygon` instance.</span></span>

-   <span data-ttu-id="ed536-116">`MultiPolygon` 인스턴스를 구성하는 모든 인스턴스가 허용되는 `Polygon` 인스턴스인 경우.</span><span class="sxs-lookup"><span data-stu-id="ed536-116">All instances comprising the `MultiPolygon` instance are accepted `Polygon` instances.</span></span> <span data-ttu-id="ed536-117">허용 `Polygon` 되는 인스턴스에 대 한 자세한 내용은 [Polygon](../spatial/polygon.md)을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="ed536-117">For more information on accepted `Polygon` instances, see [Polygon](../spatial/polygon.md).</span></span>

 <span data-ttu-id="ed536-118">다음 예에서는 허용되는 `MultiPolygon` 인스턴스를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ed536-118">The following examples show accepted `MultiPolygon` instances.</span></span>

```
DECLARE @g1 geometry = 'MULTIPOLYGON EMPTY';
DECLARE @g2 geometry = 'MULTIPOLYGON(((1 1, 1 -1, -1 -1, -1 1, 1 1)),((1 1, 3 1, 3 3, 1 3, 1 1)))';
DECLARE @g3 geometry = 'MULTIPOLYGON(((2 2, 2 -2, -2 -2, -2 2, 2 2)),((1 1, 3 1, 3 3, 1 3, 1 1)))';
```

 <span data-ttu-id="ed536-119">다음 예에서는 `System.FormatException`을 발생시키는 MultiPolygon 인스턴스를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ed536-119">The following example shows a MultiPolygon instance that will throw a `System.FormatException`.</span></span>

```
DECLARE @g geometry = 'MULTIPOLYGON(((1 1, 1 -1, -1 -1, -1 1, 1 1)),((1 1, 3 1, 3 3)))';
```

 <span data-ttu-id="ed536-120">MultiPolygon의 두 번째 인스턴스는 허용되는 Polygon 인스턴스가 아닌 LineString 인스턴스입니다.</span><span class="sxs-lookup"><span data-stu-id="ed536-120">The second instance in the MultiPolygon is a LineString instance and not an accepted Polygon instance.</span></span>

### <a name="valid-instances"></a><span data-ttu-id="ed536-121">유효한 인스턴스</span><span class="sxs-lookup"><span data-stu-id="ed536-121">Valid Instances</span></span>
 <span data-ttu-id="ed536-122">`MultiPolygon` 인스턴스는 빈 `MultiPolygon` 인스턴스이거나 다음 조건이 만족되는 경우 유효합니다.</span><span class="sxs-lookup"><span data-stu-id="ed536-122">A `MultiPolygon` instance is valid if it is an empty `MultiPolygon` instance or if it meets the following criteria.</span></span>

1.  <span data-ttu-id="ed536-123">`MultiPolygon` 인스턴스를 구성하는 모든 인스턴스가 유효한 `Polygon` 인스턴스인 경우.</span><span class="sxs-lookup"><span data-stu-id="ed536-123">All of the instances comprising the `MultiPolygon` instance are valid `Polygon` instances.</span></span> <span data-ttu-id="ed536-124">유효한 `Polygon` 인스턴스는 [Polygon](../spatial/polygon.md)을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="ed536-124">For valid `Polygon` instances, see [Polygon](../spatial/polygon.md).</span></span>

2.  <span data-ttu-id="ed536-125">`Polygon` 인스턴스를 구성하는 어떤 `MultiPolygon` 인스턴스도 겹치지 않는 경우</span><span class="sxs-lookup"><span data-stu-id="ed536-125">None of the `Polygon` instances comprising the `MultiPolygon` instance overlap.</span></span>

 <span data-ttu-id="ed536-126">다음 예에서는 유효한 `MultiPolygon` 인스턴스 두 개와 유효하지 않은 `MultiPolygon` 인스턴스 하나를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ed536-126">The following example shows two valid `MultiPolygon` instances and one invalid `MultiPolygon` instance.</span></span>

```
DECLARE @g1 geometry = 'MULTIPOLYGON EMPTY';
DECLARE @g2 geometry = 'MULTIPOLYGON(((1 1, 1 -1, -1 -1, -1 1, 1 1)),((1 1, 3 1, 3 3, 1 3, 1 1)))';
DECLARE @g3 geometry = 'MULTIPOLYGON(((2 2, 2 -2, -2 -2, -2 2, 2 2)),((1 1, 3 1, 3 3, 1 3, 1 1)))';
SELECT @g1.STIsValid(), @g2.STIsValid(), @g3.STIsValid();
```

 <span data-ttu-id="ed536-127">`@g2`는 두 `Polygon` 인스턴스가 탄젠트 점에서만 접하므로 유효합니다.</span><span class="sxs-lookup"><span data-stu-id="ed536-127">`@g2` is valid because the two `Polygon` instances touch only at a tangent point.</span></span> <span data-ttu-id="ed536-128">`@g3`은 두 `Polygon` 인스턴스의 내부가 서로 겹치므로 유효하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ed536-128">`@g3` is not valid because the interiors of the two `Polygon` instances overlap each other.</span></span>

## <a name="examples"></a><span data-ttu-id="ed536-129">예</span><span class="sxs-lookup"><span data-stu-id="ed536-129">Examples</span></span>
 <span data-ttu-id="ed536-130">다음 예제에서는 `geometry``MultiPolygon` 인스턴스를 만드는 방법을 보여 주고 두 번째 구성 요소의 WKT(Well-Known Text)를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="ed536-130">The following example shows the creation of a `geometry``MultiPolygon` instance and returns the Well-Known Text (WKT) of the second component.</span></span>

```
DECLARE @g geometry;
SET @g = geometry::Parse('MULTIPOLYGON(((0 0, 0 3, 3 3, 3 0, 0 0), (1 1, 1 2, 2 1, 1 1)), ((9 9, 9 10, 10 9, 9 9)))');
SELECT @g.STGeometryN(2).STAsText();
```

 <span data-ttu-id="ed536-131">이 예에서는 빈 `MultiPolygon` 인스턴스를 인스턴스화합니다.</span><span class="sxs-lookup"><span data-stu-id="ed536-131">This example instantiates an empty `MultiPolygon` instance.</span></span>

```
DECLARE @g geometry;
SET @g = geometry::Parse('MULTIPOLYGON EMPTY');
```

## <a name="see-also"></a><span data-ttu-id="ed536-132">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ed536-132">See Also</span></span>
 <span data-ttu-id="ed536-133">[Polygon](../spatial/polygon.md) [starea &#40;geometry 데이터 형식&#41;](/sql/t-sql/spatial-geometry/starea-geometry-data-type) [STCentroid &#40;geometry 데이터 형식&#41;](/sql/t-sql/spatial-geometry/stcentroid-geometry-data-type) [stpointonsurface &#40;geometry 데이터 형식의](/sql/t-sql/spatial-geometry/stpointonsurface-geometry-data-type) [공간 데이터&#41;](../spatial/spatial-data-sql-server.md) &#40;SQL Server</span><span class="sxs-lookup"><span data-stu-id="ed536-133">[Polygon](../spatial/polygon.md) [STArea &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/starea-geometry-data-type) [STCentroid &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/stcentroid-geometry-data-type) [STPointOnSurface &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/stpointonsurface-geometry-data-type) [Spatial Data &#40;SQL Server&#41;](../spatial/spatial-data-sql-server.md)</span></span>


