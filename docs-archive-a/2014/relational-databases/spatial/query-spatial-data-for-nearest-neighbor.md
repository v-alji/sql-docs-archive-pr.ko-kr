---
title: 가장 인접한 항목의 공간 데이터 쿼리 | Microsoft 문서
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
ms.assetid: 7af4ad5d-484e-45b4-aa16-83c33b358bb6
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 644b3e5cfdaeff7457639bc2da77260b64011735
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660422"
---
# <a name="query-spatial-data-for-nearest-neighbor"></a><span data-ttu-id="8b5a2-102">가장 인접한 항목의 공간 데이터 쿼리</span><span class="sxs-lookup"><span data-stu-id="8b5a2-102">Query Spatial Data for Nearest Neighbor</span></span>
  <span data-ttu-id="8b5a2-103">공간 데이터에 사용되는 일반적인 쿼리는 가장 인접한 항목 쿼리입니다.</span><span class="sxs-lookup"><span data-stu-id="8b5a2-103">A common query used with spatial data is the Nearest Neighbor query.</span></span> <span data-ttu-id="8b5a2-104">가장 인접한 항목 쿼리는 특정 공간 개체에 가장 가까운 공간 개체를 찾는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="8b5a2-104">Nearest Neighbor queries are used to find the closest spatial objects to a specific spatial object.</span></span> <span data-ttu-id="8b5a2-105">예를 들어 웹 사이트에 대한 상점 로케이터는 고객 위치와 가장 가까운 상점 위치를 찾아야 하는 경우가 많습니다.</span><span class="sxs-lookup"><span data-stu-id="8b5a2-105">For example a store locater for a Web site often must find the closest store locations to a customer location.</span></span>  
  
 <span data-ttu-id="8b5a2-106">가장 인접한 항목 쿼리는 여러 가지의 유효한 쿼리 형식으로 작성할 수 있지만 가장 인접한 항목 쿼리에서 공간 인덱스를 사용하는 경우 다음 구문을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8b5a2-106">A Nearest Neighbor query can be written in a variety of valid query formats, but for the Nearest Neighbor query to use a spatial index the following syntax must be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8b5a2-107">구문</span><span class="sxs-lookup"><span data-stu-id="8b5a2-107">Syntax</span></span>  
  
```vb  
SELECT TOP ( number )  
        [ WITH TIES ]  
        [ * | expression ]   
        [, ...]  
    FROM spatial_table_reference, ...   
        [ WITH   
            (   
                [ INDEX ( index_ref ) ]   
                [ , SPATIAL_WINDOW_MAX_CELLS = <value>]   
                [ ,... ]   
            )   
        ]  
    WHERE   
        column_ref.STDistance ( @spatial_ object )   
            {   
                [ IS NOT NULL ] | [ < const ] | [ > const ]   
                | [ <= const ] | [ >= const ] | [ <> const ] ]   
            }  
            [ AND { other_predicate } ]   
    }  
    ORDER BY column_ref.STDistance ( @spatial_ object ) [ ,...n ]  
[ ; ]  
  
```  
  
## <a name="nearest-neighbor-query-and-spatial-indexes"></a><span data-ttu-id="8b5a2-108">가장 인접한 항목 쿼리 및 공간 인덱스</span><span class="sxs-lookup"><span data-stu-id="8b5a2-108">Nearest Neighbor Query and Spatial Indexes</span></span>  
 <span data-ttu-id="8b5a2-109">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 `TOP` 및 `ORDER BY` 절은 공간 데이터 열에서 가장 인접한 항목 쿼리를 수행하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="8b5a2-109">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], `TOP` and `ORDER BY` clauses are used to perform a Nearest Neighbor query on spatial data columns.</span></span> <span data-ttu-id="8b5a2-110">`ORDER BY` 절은 공간 열 데이터 형식의 `STDistance()` 메서드에 대한 호출을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="8b5a2-110">The `ORDER BY` clause contains a call to the `STDistance()` method for the spatial column data type.</span></span> <span data-ttu-id="8b5a2-111">`TOP` 절은 쿼리에 대해 반환하는 개체 수를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="8b5a2-111">The `TOP` clause indicates the number of objects to return for the query.</span></span>  
  
 <span data-ttu-id="8b5a2-112">가장 인접한 항목 쿼리에서 공간 인덱스를 사용하려면 다음 요구 사항을 충족해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8b5a2-112">The following requirements must be met for a Nearest Neighbor query to use a spatial index:</span></span>  
  
1.  <span data-ttu-id="8b5a2-113">공간 인덱스가 공간 열 중 하나에 있어야 하며 `STDistance()` 메서드가 해당 열을 `WHERE` 및 `ORDER BY` 절에 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8b5a2-113">A spatial index must be present on one of the spatial columns and the `STDistance()` method must use that column in the `WHERE` and `ORDER BY` clauses.</span></span>  
  
2.  <span data-ttu-id="8b5a2-114">`TOP` 절은 `PERCENT` 문을 포함할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8b5a2-114">The `TOP` clause cannot contain a `PERCENT` statement.</span></span>  
  
3.  <span data-ttu-id="8b5a2-115">`WHERE` 절은 `STDistance()` 메서드를 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8b5a2-115">The `WHERE` clause must contain a `STDistance()` method.</span></span>  
  
4.  <span data-ttu-id="8b5a2-116">`WHERE` 절에 조건자가 여러 개 있는 경우 `STDistance()` 메서드를 포함하는 조건자는 다른 조건자와 `AND` 결합으로 연결되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8b5a2-116">If there are multiple predicates in the `WHERE` clause then the predicate containing `STDistance()` method must be connected by an `AND` conjunction to the other predicates.</span></span> <span data-ttu-id="8b5a2-117">`STDistance()` 메서드는 `WHERE` 절의 선택적 부분에 있을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8b5a2-117">The `STDistance()` method cannot be in an optional part of the `WHERE` clause.</span></span>  
  
5.  <span data-ttu-id="8b5a2-118">`ORDER BY` 절의 첫 번째 식은 `STDistance()` 메서드를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8b5a2-118">The first expression in the `ORDER BY` clause must use the `STDistance()` method.</span></span>  
  
6.  <span data-ttu-id="8b5a2-119">`ORDER BY` 절의 첫 번째 `STDistance()` 식에 대한 정렬 순서는 `ASC`여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8b5a2-119">Sort order for the first `STDistance()` expression in the `ORDER BY` clause must be `ASC`.</span></span>  
  
7.  <span data-ttu-id="8b5a2-120">`STDistance`에서 `NULL`을 반환하는 모든 행은 필터링되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8b5a2-120">All the rows for which `STDistance` returns `NULL` must be filtered out.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="8b5a2-121">`geography` 또는 `geometry` 데이터 형식을 인수로 사용하는 메서드는 이 두 데이터 형식의 SRID가 서로 동일하지 않는 경우 `NULL`을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="8b5a2-121">Methods that take `geography` or `geometry` data types as arguments will return `NULL` if the SRIDs are not the same for the types.</span></span>  
  
 <span data-ttu-id="8b5a2-122">가장 인접한 항목 쿼리에 사용되는 인덱스에는 새 공간 인덱스 공간 분할(tessellation)을 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="8b5a2-122">It is recommended that the new spatial index tessellations be used for indexes used in Nearest Neighbor queries.</span></span> <span data-ttu-id="8b5a2-123">공간 인덱스 공간 분할(tessellation)에 대한 자세한 내용은 [공간 데이터&#40;SQL Server&#41;](spatial-data-sql-server.md)여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8b5a2-123">For more information on spatial index tessellations, see [Spatial Data &#40;SQL Server&#41;](spatial-data-sql-server.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8b5a2-124">예제</span><span class="sxs-lookup"><span data-stu-id="8b5a2-124">Example</span></span>  
 <span data-ttu-id="8b5a2-125">다음 코드 예에서는 공간 인덱스를 사용할 수 있는 가장 인접한 항목 쿼리를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="8b5a2-125">The following code example shows a Nearest Neighbor query that can use a spatial index.</span></span> <span data-ttu-id="8b5a2-126">이 예에서는 `Person.Address` 데이터베이스의 `AdventureWorks2012` 테이블을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="8b5a2-126">The example uses the `Person.Address` table in `AdventureWorks2012` database.</span></span>  
  
```  
USE AdventureWorks2012  
GO  
DECLARE @g geography = 'POINT(-121.626 47.8315)';  
SELECT TOP(7) SpatialLocation.ToString(), City FROM Person.Address  
WHERE SpatialLocation.STDistance(@g) IS NOT NULL  
ORDER BY SpatialLocation.STDistance(@g);  
  
```  
  
 <span data-ttu-id="8b5a2-127">가장 인접한 항목 쿼리에서 공간 인덱스를 사용하는 방법을 확인하기 위해 SpatialLocation 열에 대한 공간 인덱스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="8b5a2-127">Create a spatial index on the column SpatialLocation to see how a Nearest Neighbor query uses a spatial index.</span></span> <span data-ttu-id="8b5a2-128">공간 인덱스를 만드는 방법은 [Create, Modify, and Drop Spatial Indexes](create-modify-and-drop-spatial-indexes.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="8b5a2-128">For more information on creating spatial indexes, see [Create, Modify, and Drop Spatial Indexes](create-modify-and-drop-spatial-indexes.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8b5a2-129">예제</span><span class="sxs-lookup"><span data-stu-id="8b5a2-129">Example</span></span>  
 <span data-ttu-id="8b5a2-130">다음 코드 예에서는 공간 인덱스를 사용할 수 없는 가장 인접한 항목 쿼리를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="8b5a2-130">The following code example shows a Nearest Neighbor query that cannot use a spatial index.</span></span>  
  
```  
USE AdventureWorks2012  
GO  
DECLARE @g geography = 'POINT(-121.626 47.8315)';  
SELECT TOP(7) SpatialLocation.ToString(), City FROM Person.Address  
ORDER BY SpatialLocation.STDistance(@g);  
  
```  
  
 <span data-ttu-id="8b5a2-131">이 쿼리에는 구문 섹션에서 지정한 형식의 `STDistance()`를 사용하는 `WHERE` 절이 부족하므로 쿼리에서 공간 인덱스를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8b5a2-131">The query lacks a `WHERE` clause that uses `STDistance()` in a form specified in the syntax section so the query cannot use a spatial index.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b5a2-132">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8b5a2-132">See Also</span></span>  
 [<span data-ttu-id="8b5a2-133">공간 데이터&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="8b5a2-133">Spatial Data &#40;SQL Server&#41;</span></span>](spatial-data-sql-server.md)  
  
  
