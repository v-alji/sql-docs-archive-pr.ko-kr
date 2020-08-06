---
title: MultiPoint | Microsoft 문서
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- MultiPoint geometry subtype [SQL Server]
ms.assetid: 2aaab211-3aba-4dbd-90b7-095d997b1f62
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: b741071b7986aceea4e49d4fde8293ef2c96fc2b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660429"
---
# <a name="multipoint"></a><span data-ttu-id="5c261-102">MultiPoint</span><span class="sxs-lookup"><span data-stu-id="5c261-102">MultiPoint</span></span>
  <span data-ttu-id="5c261-103">`MultiPoint`는 1개 이상의 점 컬렉션입니다.</span><span class="sxs-lookup"><span data-stu-id="5c261-103">A `MultiPoint` is a collection of zero or more points.</span></span> <span data-ttu-id="5c261-104">`MultiPoint` 인스턴스의 경계는 비어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5c261-104">The boundary of a `MultiPoint` instance is empty.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="5c261-105">예</span><span class="sxs-lookup"><span data-stu-id="5c261-105">Examples</span></span>  
 <span data-ttu-id="5c261-106">다음 예에서는 SRID가 23이며 두 개의 점이 있는 `geometry MultiPoint` 인스턴스를 만듭니다. 한 점의 좌표는 (2, 3)이고, 다른 한 점의 좌표는 (7, 8)이며, Z 값은 9.5입니다.</span><span class="sxs-lookup"><span data-stu-id="5c261-106">The following example creates a `geometry MultiPoint` instance with SRID 23 and two points: one point with the coordinates (2, 3), one point with the coordinates (7, 8), and a Z value of 9.5.</span></span>  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('MULTIPOINT((2 3), (7 8 9.5))', 23);  
```  
  
 <span data-ttu-id="5c261-107">이 `MultiPoint` 인스턴스는 아래에 표시된 대로 `STMPointFromText()` 를 사용하여 표현할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5c261-107">This `MultiPoint` instance can also be expressed using `STMPointFromText()` as shown below.</span></span>  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STMPointFromText('MULTIPOINT((2 3), (7 8 9.5))', 23);  
```  
  
 <span data-ttu-id="5c261-108">다음 예에서는 `STGeometryN()` 메서드를 사용하여 컬렉션에서 첫째 점의 설명을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="5c261-108">The following example uses the method `STGeometryN()` to retrieve a description of the first point in the collection.</span></span>  
  
```  
SELECT @g.STGeometryN(1).STAsText();  
```  
  
## <a name="see-also"></a><span data-ttu-id="5c261-109">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5c261-109">See Also</span></span>  
 <span data-ttu-id="5c261-110">[까지](point.md) </span><span class="sxs-lookup"><span data-stu-id="5c261-110">[Point](point.md) </span></span>  
 [<span data-ttu-id="5c261-111">공간 데이터&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="5c261-111">Spatial Data &#40;SQL Server&#41;</span></span>](spatial-data-sql-server.md)  
  
  
