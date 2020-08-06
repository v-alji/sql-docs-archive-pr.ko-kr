---
title: 점 | Microsoft 문서
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- Point geometry subtype [SQL Server]
- geometry data type [SQL Server], spatial data
ms.assetid: 2a596ec4-8b2f-4962-bcb4-e5c8f77edad5
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 4b12069d84e00738e3ddac8c414f33903f4f0999
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660425"
---
# <a name="point"></a><span data-ttu-id="96025-102">Point</span><span class="sxs-lookup"><span data-stu-id="96025-102">Point</span></span>
  <span data-ttu-id="96025-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 공간 데이터에서 `Point`는 단일 위치를 나타내는 0차원 개체 이며 Z(높이) 및 M(측정값) 값을 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="96025-103">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] spatial data, a `Point` is a 0-dimensional object representing a single location and may contain Z (elevation) and M (measure) values.</span></span>  
  
## <a name="geography-data-type"></a><span data-ttu-id="96025-104">geography 데이터 형식</span><span class="sxs-lookup"><span data-stu-id="96025-104">Geography Data Type</span></span>  
 <span data-ttu-id="96025-105">Geography 데이터 형식의 점 유형은 *Lat* 와 *Long* 가 각각 경도와 위도를 나타내는 단일 위치를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="96025-105">The Point type for the geography data type represents a single location where *Lat* represents latitude and *Long* represents longitude.</span></span> <span data-ttu-id="96025-106">경도와 위도 값은 각도로 측정됩니다.</span><span class="sxs-lookup"><span data-stu-id="96025-106">The values for latitude and longitude are measured in degrees.</span></span> <span data-ttu-id="96025-107">위도 값은 항상 [-90, 90] 사이에 있고 이 범위를 벗어난 값을 입력하면 예외를 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="96025-107">Values for latitude always lie in the interval [-90, 90], and values that are inputted outside this range will throw an exception.</span></span> <span data-ttu-id="96025-108">경도 값은 항상 [-180, 180] 사이에 있고 이 범위를 벗어나서 입력된 값은 이 범위 안에 있는 값으로 랩 어라운드(wrap-around)됩니다.</span><span class="sxs-lookup"><span data-stu-id="96025-108">Values for longitude always lie in the interval (-180, 180], and values inputted outside this range are wrapped around to fit in this range.</span></span> <span data-ttu-id="96025-109">예를 들어 경도 값에 190을 입력하면 그 값은 -170으로 래핑됩니다.</span><span class="sxs-lookup"><span data-stu-id="96025-109">For example, if 190 is inputted for longitude, then it will be wrapped to the value -170.</span></span> <span data-ttu-id="96025-110">*SRID* 는 반환할 **geography** 인스턴스의 Spatial Reference ID를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="96025-110">*SRID* represents the spatial reference ID of the **geography** instance that you wish to return.</span></span>  
  
## <a name="geometry-data-type"></a><span data-ttu-id="96025-111">Geometry 데이터 형식</span><span class="sxs-lookup"><span data-stu-id="96025-111">Geometry Data Type</span></span>  
 <span data-ttu-id="96025-112">Geometry 데이터 형식의 점 유형은 *X* 와 *Y* 가 각각 생성 중인 지점의 X 및 Y 좌표를 나타내는 단일 위치를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="96025-112">The Point type for the geometry data type represents a single location where *X* represents the X-coordinate of the Point being generated and *Y* represents the Y-coordinate of the Point being generated.</span></span> <span data-ttu-id="96025-113">*SRID* 는 반환할 **geometry** 인스턴스의 Spatial Reference ID를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="96025-113">*SRID* represents the spatial reference ID of the **geometry** instance that you wish to return.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="96025-114">예</span><span class="sxs-lookup"><span data-stu-id="96025-114">Examples</span></span>  
 <span data-ttu-id="96025-115">다음 예제에서는 SRID가 0인 점(3, 4)을 나타내는 `geometry Point`인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="96025-115">The following example creates a `geometry Point`instance representing the point (3, 4) with an SRID of 0.</span></span>  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('POINT (3 4)', 0);  
```  
  
 <span data-ttu-id="96025-116">다음 예제에서는 Z(높이) 값이 7이고 M(측정값) 값이 2.5이며 기본 SRID가 0인 점(3, 4)을 나타내는 `geometry``Point` 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="96025-116">The next example creates a `geometry``Point` instance representing the point (3, 4) with a Z (elevation) value of 7, an M (measure) value of 2.5, and the default SRID of 0.</span></span>  
  
```  
DECLARE @g geometry;  
SET @g = geometry::Parse('POINT(3 4 7 2.5)');  
```  
  
 <span data-ttu-id="96025-117">마지막 예에서는 `geometry``Point` 인스턴스에 대한 X, Y, Z, M 값을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="96025-117">The final example returns the X, Y, Z, and M values for the `geometry``Point` instance.</span></span>  
  
```  
SELECT @g.STX;  
SELECT @g.STY;  
SELECT @g.Z;  
SELECT @g.M;  
```  
  
 <span data-ttu-id="96025-118">Z 및 M 값은 다음 예에 표시된 대로 명시적으로 NULL로 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="96025-118">Z and M values may be explicitly specified as NULL, as shown in the following example.</span></span>  
  
```  
DECLARE @g geometry;  
SET @g = geometry::Parse('POINT(3 4 NULL NULL)');  
```  
  
## <a name="see-also"></a><span data-ttu-id="96025-119">참고 항목</span><span class="sxs-lookup"><span data-stu-id="96025-119">See Also</span></span>  
 <span data-ttu-id="96025-120">[다](multipoint.md) </span><span class="sxs-lookup"><span data-stu-id="96025-120">[MultiPoint](multipoint.md) </span></span>  
 <span data-ttu-id="96025-121">[STX &#40;geometry 데이터 형식&#41;](/sql/t-sql/spatial-geometry/stx-geometry-data-type) </span><span class="sxs-lookup"><span data-stu-id="96025-121">[STX &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/stx-geometry-data-type) </span></span>  
 <span data-ttu-id="96025-122">[STY&#40;geometry 데이터 형식&#41;](/sql/t-sql/spatial-geometry/sty-geometry-data-type) </span><span class="sxs-lookup"><span data-stu-id="96025-122">[STY &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/sty-geometry-data-type) </span></span>  
 [<span data-ttu-id="96025-123">공간 데이터&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="96025-123">Spatial Data &#40;SQL Server&#41;</span></span>](spatial-data-sql-server.md)  
  
  
