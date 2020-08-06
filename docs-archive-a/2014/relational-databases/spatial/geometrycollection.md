---
title: GeometryCollection | Microsoft 문서
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- GeomCollection geometry subtype [SQL Server]
- geometry subtypes [SQL Server]
ms.assetid: 4445c0d9-a66b-4d7c-88e4-a66fa6f7d9fd
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 71d2234a9b73b7647554e364fe3864f089a47a0b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660442"
---
# <a name="geometrycollection"></a><span data-ttu-id="579d9-102">GeometryCollection</span><span class="sxs-lookup"><span data-stu-id="579d9-102">GeometryCollection</span></span>
  <span data-ttu-id="579d9-103">`GeometryCollection`은 1개 이상의 `geometry` 또는 `geography` 인스턴스 컬렉션입니다.</span><span class="sxs-lookup"><span data-stu-id="579d9-103">A `GeometryCollection` is a collection of zero or more `geometry` or `geography` instances.</span></span> <span data-ttu-id="579d9-104">`GeometryCollection`은 비워 둘 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="579d9-104">A `GeometryCollection` can be empty.</span></span>  
  
## <a name="geometrycollection-instances"></a><span data-ttu-id="579d9-105">GeometryCollection 인스턴스</span><span class="sxs-lookup"><span data-stu-id="579d9-105">GeometryCollection Instances</span></span>  
  
### <a name="accepted-instances"></a><span data-ttu-id="579d9-106">허용되는 인스턴스</span><span class="sxs-lookup"><span data-stu-id="579d9-106">Accepted Instances</span></span>  
 <span data-ttu-id="579d9-107">`GeometryCollection` 인스턴스는 빈 `GeometryCollection` 인스턴스이거나 `GeometryCollection` 인스턴스를 구성하는 모든 인스턴스가 허용되는 인스턴스여야 허용됩니다.</span><span class="sxs-lookup"><span data-stu-id="579d9-107">For a `GeometryCollection` instance to be accepted, it must either be an empty `GeometryCollection` instance or all the instances comprising the `GeometryCollection` instance must be accepted instances.</span></span> <span data-ttu-id="579d9-108">다음 예에서는 허용되는 인스턴스를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="579d9-108">The following example shows accepted instances.</span></span>  
  
```  
DECLARE @g1 geometry = 'GEOMETRYCOLLECTION EMPTY';  
DECLARE @g2 geometry = 'GEOMETRYCOLLECTION(LINESTRING EMPTY,POLYGON((-1 -1, -1 -5, -5 -5, -5 -1, -1 -1)))';  
DECLARE @g3 geometry = 'GEOMETRYCOLLECTION(LINESTRING(1 1, 3 5),POLYGON((-1 -1, -1 -5, -5 -5, -5 -1, -1 -1)))';  
```  
  
 <span data-ttu-id="579d9-109">다음 예에서는 `LinesString` 인스턴스의 `GeometryCollection` 인스턴스가 허용되지 않으므로 `System.FormatException`이 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="579d9-109">The following example throws a `System.FormatException` because the `LinesString` instance in the `GeometryCollection` instance is not accepted.</span></span>  
  
```  
DECLARE @g geometry = 'GEOMETRYCOLLECTION(LINESTRING(1 1), POLYGON((-1 -1, -1 -5, -5 -5, -5 -1, -1 -1)))';  
```  
  
### <a name="valid-instances"></a><span data-ttu-id="579d9-110">유효한 인스턴스</span><span class="sxs-lookup"><span data-stu-id="579d9-110">Valid Instances</span></span>  
 <span data-ttu-id="579d9-111">`GeometryCollection` 인스턴스는 `GeometryCollection` 인스턴스를 구성하는 모든 인스턴스가 유효한 경우 유효합니다.</span><span class="sxs-lookup"><span data-stu-id="579d9-111">A `GeometryCollection` instance is valid when all instances that comprise the `GeometryCollection` instance are valid.</span></span> <span data-ttu-id="579d9-112">다음 예에서는 유효한 `GeometryCollection` 인스턴스 세 개와 유효하지 않은 인스턴스 하나를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="579d9-112">The following shows three valid `GeometryCollection` instances and one instance that is not valid.</span></span>  
  
```  
DECLARE @g1 geometry = 'GEOMETRYCOLLECTION EMPTY';  
DECLARE @g2 geometry = 'GEOMETRYCOLLECTION(LINESTRING EMPTY,POLYGON((-1 -1, -1 -5, -5 -5, -5 -1, -1 -1)))';  
DECLARE @g3 geometry = 'GEOMETRYCOLLECTION(LINESTRING(1 1, 3 5),POLYGON((-1 -1, -1 -5, -5 -5, -5 -1, -1 -1)))';  
DECLARE @g4 geometry = 'GEOMETRYCOLLECTION(LINESTRING(1 1, 3 5),POLYGON((-1 -1, 1 -5, -5 5, -5 -1, -1 -1)))';  
SELECT @g1.STIsValid(), @g2.STIsValid(), @g3.STIsValid(), @g4.STIsValid();  
```  
  
 <span data-ttu-id="579d9-113">`Polygon` 인스턴스의 `GeometryCollection` 인스턴스가 유효하지 않으므로 `@g4`는 유효하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="579d9-113">`@g4` is not valid because the `Polygon` instance in the `GeometryCollection` instance is not valid.</span></span>  
  
 <span data-ttu-id="579d9-114">허용되는 인스턴스와 유효한 인스턴스에 대한 자세한 내용은 [Point](point.md), [MultiPoint](multipoint.md), [LineString](linestring.md), [MultiLineString](multilinestring.md), [Polygon](polygon.md)및 [MultiPolygon](multipolygon.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="579d9-114">For more information on accepted and valid instances, see [Point](point.md), [MultiPoint](multipoint.md), [LineString](linestring.md), [MultiLineString](multilinestring.md), [Polygon](polygon.md), and [MultiPolygon](multipolygon.md).</span></span>  
  
## <a name="examples"></a><span data-ttu-id="579d9-115">예</span><span class="sxs-lookup"><span data-stu-id="579d9-115">Examples</span></span>  
 <span data-ttu-id="579d9-116">다음 예제에서는 `geometry``GeometryCollection` 인스턴스 및 `Point` 인스턴스가 들어 있는 SRID 1의 Z 값으로 `Polygon` 을 인스턴스화합니다.</span><span class="sxs-lookup"><span data-stu-id="579d9-116">The following example instantiates a `geometry``GeometryCollection` with Z values in SRID 1 containing a `Point` instance and a `Polygon` instance.</span></span>  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomCollFromText('GEOMETRYCOLLECTION(POINT(3 3 1), POLYGON((0 0 2, 1 10 3, 1 0 4, 0 0 2)))', 1);  
```  
  
## <a name="see-also"></a><span data-ttu-id="579d9-117">참고 항목</span><span class="sxs-lookup"><span data-stu-id="579d9-117">See Also</span></span>  
 [<span data-ttu-id="579d9-118">공간 데이터&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="579d9-118">Spatial Data &#40;SQL Server&#41;</span></span>](spatial-data-sql-server.md)  
  
  
