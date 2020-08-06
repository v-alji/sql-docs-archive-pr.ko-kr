---
title: CompoundCurve | Microsoft 문서
ms.custom: ''
ms.date: 10/18/2019
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
ms.assetid: ae357f9b-e3e2-4cdf-af02-012acda2e466
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 6a899bbe9a17a64083592e1078e8cac93365f02b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646858"
---
# <a name="compoundcurve"></a><span data-ttu-id="5ec9f-102">CompoundCurve</span><span class="sxs-lookup"><span data-stu-id="5ec9f-102">CompoundCurve</span></span>
  <span data-ttu-id="5ec9f-103">`CompoundCurve`는 geometry 또는 geography 유형의 연속적인 `CircularString` 또는 `LineString` 인스턴스가 하나 이상 포함된 컬렉션입니다.</span><span class="sxs-lookup"><span data-stu-id="5ec9f-103">A `CompoundCurve` is a collection of zero or more continuous `CircularString` or `LineString` instances of either geometry or geography types.</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="5ec9f-104">하위 유형을 포함 하 여이 릴리스의 새로운 공간 기능에 대 한 자세한 설명 및 예를 보려면 `CompoundCurve` [SQL Server 2012의 새로운 공간 기능](https://go.microsoft.com/fwlink/?LinkId=226407)백서를 다운로드 하세요.</span><span class="sxs-lookup"><span data-stu-id="5ec9f-104">For a detailed description and examples of the new spatial features in this release, including the `CompoundCurve` subtype, download the white paper, [New Spatial Features in SQL Server 2012](https://go.microsoft.com/fwlink/?LinkId=226407).</span></span>

 <span data-ttu-id="5ec9f-105">빈 `CompoundCurve` 인스턴스를 인스턴스화할 수 있지만 `CompoundCurve`가 유효한 인스턴스가 되려면 다음 조건을 충족해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5ec9f-105">An empty `CompoundCurve` instance can be instantiated, but for a `CompoundCurve` to be valid it must meet the following criteria:</span></span>

1.  <span data-ttu-id="5ec9f-106">적어도 하나의 `CircularString` 또는 `LineString` 인스턴스를 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5ec9f-106">It must contain at least one `CircularString` or `LineString` instance.</span></span>

2.  <span data-ttu-id="5ec9f-107">`CircularString` 또는 `LineString` 인스턴스의 시퀀스는 연속적이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5ec9f-107">The sequence of `CircularString` or `LineString` instances must be continuous.</span></span>

 <span data-ttu-id="5ec9f-108">에 `CompoundCurve` 여러 및 인스턴스의 시퀀스가 포함 된 `CircularString` 경우 `LineString` 마지막 인스턴스를 제외한 모든 인스턴스의 종료 끝점은 시퀀스에서 다음 인스턴스의 시작 끝점 이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5ec9f-108">If a `CompoundCurve` contains a sequence of multiple `CircularString` and `LineString` instances, the ending endpoint for every instance except for the last instance must be the starting endpoint for the next instance in the sequence.</span></span> <span data-ttu-id="5ec9f-109">즉, 시퀀스에서 이전 인스턴스의 끝 점이 (4 3 7 2)인 경우 시퀀스에서 다음 인스턴스의 시작 점은 (4 3 7 2)여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5ec9f-109">This means that if the ending point of a prior instance in the sequence is (4 3 7 2), the starting point for the next instance in the sequence must be (4 3 7 2).</span></span> <span data-ttu-id="5ec9f-110">점의 Z(높이) 및 M(측정값) 값도 동일해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5ec9f-110">Note that Z(elevation) and M(measure) values for the point must also be the same.</span></span> <span data-ttu-id="5ec9f-111">두 점이 다른 경우 `System.FormatException` 이 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="5ec9f-111">If there is a difference in the two points, a `System.FormatException` is thrown.</span></span> <span data-ttu-id="5ec9f-112">`CircularString`의 점은 Z 또는 M 값을 가지고 있지 않아도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5ec9f-112">Points in a `CircularString` do not have to have a Z or M value.</span></span> <span data-ttu-id="5ec9f-113">이전 인스턴스의 종료 점에 대해 Z 또는 M 값이 지정되지 않은 경우 다음 인스턴스의 시작 점은 Z 또는 M 값을 포함할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5ec9f-113">If no Z or M values are given for the ending point of the prior instance, the starting point of the next instance cannot include Z or M values.</span></span> <span data-ttu-id="5ec9f-114">이전 시퀀스의 종료 점이 (4 3)이면 다음 시퀀스의 시작 점은 (4 3)이어야 하지 (4 3 7 2)일 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5ec9f-114">If the ending point for the prior sequence is (4 3), the starting point for the next sequence must be (4 3); it cannot be (4 3 7 2).</span></span> <span data-ttu-id="5ec9f-115">`CompoundCurve` 인스턴스의 모든 점은 Z 값을 가지고 있지 않거나 같은 Z 값을 가지고 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5ec9f-115">All points in a `CompoundCurve` instance must have either no Z value or the same Z value.</span></span>

## <a name="compoundcurve-instances"></a><span data-ttu-id="5ec9f-116">CompoundCurve 인스턴스</span><span class="sxs-lookup"><span data-stu-id="5ec9f-116">CompoundCurve instances</span></span>
 <span data-ttu-id="5ec9f-117">다음 그림에서는 유효한 `CompoundCurve` 형식을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="5ec9f-117">The following illustration shows valid `CompoundCurve` types.</span></span>

 ![](../../database-engine/media/f278742e-b861-4555-8b51-3d972b7602bf.png "f278742e-b861-4555-8b51-3d972b7602bf")

### <a name="accepted-instances"></a><span data-ttu-id="5ec9f-118">허용되는 인스턴스</span><span class="sxs-lookup"><span data-stu-id="5ec9f-118">Accepted instances</span></span>
 <span data-ttu-id="5ec9f-119">`CompoundCurve` 인스턴스는 빈 인스턴스이거나 다음 조건을 충족하는 경우 허용됩니다.</span><span class="sxs-lookup"><span data-stu-id="5ec9f-119">`CompoundCurve` instance is accepted if it is an empty instance or meets the following criteria.</span></span>

1.  <span data-ttu-id="5ec9f-120">`CompoundCurve` 인스턴스에 포함된 모든 인스턴스가 허용되는 원호 세그먼트 인스턴스인 경우.</span><span class="sxs-lookup"><span data-stu-id="5ec9f-120">All the instances contained by `CompoundCurve` instance are accepted circular arc segment instances.</span></span> <span data-ttu-id="5ec9f-121">허용되는 원호 세그먼트 인스턴스에 대한 자세한 내용은 [LineString](linestring.md) 및 [CircularString](circularstring.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5ec9f-121">For more information on accepted circular arc segment instances, see [LineString](linestring.md) and [CircularString](circularstring.md).</span></span>

2.  <span data-ttu-id="5ec9f-122">`CompoundCurve` 인스턴스의 모든 원호 세그먼트가 연결되어 있는 경우.</span><span class="sxs-lookup"><span data-stu-id="5ec9f-122">All of the circular arc segments in the `CompoundCurve` instance are connected.</span></span> <span data-ttu-id="5ec9f-123">즉, 이어지는 각 원호 세그먼트의 첫 번째 점이 앞에 있는 원호 세그먼트의 마지막 점과 같아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5ec9f-123">The first point for each succeeding circular arc segment is the same as the last point on the preceding circular arc segment.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="5ec9f-124">여기에는 Z와 M 좌표가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="5ec9f-124">This includes the Z and M coordinates.</span></span> <span data-ttu-id="5ec9f-125">따라서 네 후보 X, Y, Z 및 M이 모두 같아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5ec9f-125">So, all four coordinates X, Y, Z, and M must be the same.</span></span>

3.  <span data-ttu-id="5ec9f-126">포함된 인스턴스 중 비어 있는 인스턴스가 없는 경우</span><span class="sxs-lookup"><span data-stu-id="5ec9f-126">None of the contained instances are empty instances.</span></span>

 <span data-ttu-id="5ec9f-127">다음 예에서는 허용되는 `CompoundCurve` 인스턴스를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="5ec9f-127">The following example shows accepted `CompoundCurve` instances.</span></span>

```
DECLARE @g1 geometry = 'COMPOUNDCURVE EMPTY';
DECLARE @g2 geometry = 'COMPOUNDCURVE(CIRCULARSTRING(1 0, 0 1, -1 0), (-1 0, 2 0))';
```

 <span data-ttu-id="5ec9f-128">다음 예에서는 허용되지 않는 `CompoundCurve` 인스턴스를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="5ec9f-128">The following example shows `CompoundCurve` instances that are not accepted.</span></span> <span data-ttu-id="5ec9f-129">이 인스턴스에서는 `System.FormatException`이 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="5ec9f-129">These instances throw `System.FormatException`.</span></span>

```
DECLARE @g1 geometry = 'COMPOUNDCURVE(CIRCULARSTRING EMPTY)';
DECLARE @g2 geometry = 'COMPOUNDCURVE(CIRCULARSTRING(1 0, 0 1, -1 0), (1 0, 2 0))';
```

### <a name="valid-instances"></a><span data-ttu-id="5ec9f-130">유효한 인스턴스</span><span class="sxs-lookup"><span data-stu-id="5ec9f-130">Valid instances</span></span>
 <span data-ttu-id="5ec9f-131">`CompoundCurve` 인스턴스는 다음 조건을 충족하는 경우 유효합니다.</span><span class="sxs-lookup"><span data-stu-id="5ec9f-131">A `CompoundCurve` instance is valid if it meets the following criteria.</span></span>

1.  <span data-ttu-id="5ec9f-132">`CompoundCurve` 인스턴스가 허용되는 경우</span><span class="sxs-lookup"><span data-stu-id="5ec9f-132">The `CompoundCurve` instance is accepted.</span></span>

2.  <span data-ttu-id="5ec9f-133">`CompoundCurve` 인스턴스에 포함된 모든 원호 세그먼트 인스턴스가 유효한 인스턴스인 경우</span><span class="sxs-lookup"><span data-stu-id="5ec9f-133">All circular arc segment instances contained by the `CompoundCurve` instance are valid instances.</span></span>

 <span data-ttu-id="5ec9f-134">다음 예에서는 유효한 `CompoundCurve` 인스턴스를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="5ec9f-134">The following example shows valid `CompoundCurve` instances.</span></span>

```
DECLARE @g1 geometry = 'COMPOUNDCURVE EMPTY';
DECLARE @g2 geometry = 'COMPOUNDCURVE(CIRCULARSTRING(1 0, 0 1, -1 0), (-1 0, 2 0))';
DECLARE @g3 geometry = 'COMPOUNDCURVE(CIRCULARSTRING(1 1, 1 1, 1 1), (1 1, 3 5, 5 4))';
SELECT @g1.STIsValid(), @g2.STIsValid(), @g3.STIsValid();

```

 <span data-ttu-id="5ec9f-135">`CircularString` 인스턴스가 유효하므로 `@g3`은 유효합니다.</span><span class="sxs-lookup"><span data-stu-id="5ec9f-135">`@g3` is valid because the `CircularString` instance is valid.</span></span> <span data-ttu-id="5ec9f-136">인스턴스의 유효성에 대 한 자세한 내용은 `CircularString` [CircularString](circularstring.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="5ec9f-136">For more information on the validity of the `CircularString` instance, see [CircularString](circularstring.md).</span></span>

 <span data-ttu-id="5ec9f-137">다음 예에서는 유효하지 않은 `CompoundCurve` 인스턴스를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="5ec9f-137">The following example shows `CompoundCurve` instances that are not valid.</span></span>

```
DECLARE @g1 geometry = 'COMPOUNDCURVE(CIRCULARSTRING(1 1, 1 1, 1 1), (1 1, 3 5, 5 4, 3 5))';
DECLARE @g2 geometry = 'COMPOUNDCURVE((1 1, 1 1))';
DECLARE @g3 geometry = 'COMPOUNDCURVE(CIRCULARSTRING(1 1, 2 3, 1 1))';
SELECT @g1.STIsValid(), @g2.STIsValid(), @g3.STIsValid();
```

 <span data-ttu-id="5ec9f-138">`@g1` 은 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="5ec9f-138">`@g1` is not valid because the second instance is not a valid LineString instance.</span></span> <span data-ttu-id="5ec9f-139">`LineString` 인스턴스가 잘못되었기 때문에 `@g2`은 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="5ec9f-139">`@g2` is not valid because the `LineString` instance is not valid.</span></span> <span data-ttu-id="5ec9f-140">`CircularString` 인스턴스가 잘못되었기 때문에 `@g3`은 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="5ec9f-140">`@g3` is not valid because the `CircularString` instance is not valid.</span></span> <span data-ttu-id="5ec9f-141">유효한 및 인스턴스에 대 한 자세한 내용은 `CircularString` `LineString` [CircularString](circularstring.md) 및 [LineString](linestring.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="5ec9f-141">For more information on valid `CircularString` and `LineString` instances, see [CircularString](circularstring.md) and [LineString](linestring.md).</span></span>

## <a name="examples"></a><span data-ttu-id="5ec9f-142">예</span><span class="sxs-lookup"><span data-stu-id="5ec9f-142">Examples</span></span>

### <a name="a-instantiating-a-geometry-instance-with-an-empty-compooundcurve"></a><span data-ttu-id="5ec9f-143">A.</span><span class="sxs-lookup"><span data-stu-id="5ec9f-143">A.</span></span> <span data-ttu-id="5ec9f-144">빈 CompooundCurve를 사용하여 기하 도형 인스턴스 인스턴스화</span><span class="sxs-lookup"><span data-stu-id="5ec9f-144">Instantiating a geometry instance with an empty CompooundCurve</span></span>
 <span data-ttu-id="5ec9f-145">다음 예에서는 빈 `CompoundCurve` 인스턴스를 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="5ec9f-145">The following example shows how to create an empty `CompoundCurve` instance:</span></span>

```sql
DECLARE @g geometry;
SET @g = geometry::Parse('COMPOUNDCURVE EMPTY');
```

### <a name="b-declaring-and-instantiating-a-geometry-instance-using-a-compoundcurve-in-the-same-statement"></a><span data-ttu-id="5ec9f-146">B.</span><span class="sxs-lookup"><span data-stu-id="5ec9f-146">B.</span></span> <span data-ttu-id="5ec9f-147">동일한 문에서 CompoundCurve를 사용하여 기하 도형 인스턴스 선언 및 인스턴스화</span><span class="sxs-lookup"><span data-stu-id="5ec9f-147">Declaring and instantiating a geometry instance using a CompoundCurve in the same statement</span></span>
 <span data-ttu-id="5ec9f-148">다음 예에서는 동일한 문에서 `geometry` 을 사용하여 `CompoundCurve`인스턴스를 선언하고 초기화하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="5ec9f-148">The following example shows how to declare and initialize a `geometry` instance with a `CompoundCurve`in the same statement:</span></span>

```sql
DECLARE @g geometry = 'COMPOUNDCURVE ((2 2, 0 0),CIRCULARSTRING (0 0, 1 2.1082, 3 6.3246, 0 7, -3 6.3246, -1 2.1082, 0 0))';
```

### <a name="c-instantiating-a-geography-instance-with-a-compoundcurve"></a><span data-ttu-id="5ec9f-149">C.</span><span class="sxs-lookup"><span data-stu-id="5ec9f-149">C.</span></span> <span data-ttu-id="5ec9f-150">CompoundCurve를 사용하여 지리 인스턴스 인스턴스화</span><span class="sxs-lookup"><span data-stu-id="5ec9f-150">Instantiating a geography instance with a CompoundCurve</span></span>
 <span data-ttu-id="5ec9f-151">다음 예에서는 `CompoundCurve`를 사용하여 `geography` 인스턴스를 선언하고 초기화하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="5ec9f-151">The following example shows how to declare and initialize a `geography` instance with a `CompoundCurve`:</span></span>

```sql
DECLARE @g geography = 'COMPOUNDCURVE(CIRCULARSTRING(-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653))';
```

### <a name="d-storing-a-square-in-a-compoundcurve-instance"></a><span data-ttu-id="5ec9f-152">D.</span><span class="sxs-lookup"><span data-stu-id="5ec9f-152">D.</span></span> <span data-ttu-id="5ec9f-153">CompoundCurve 인스턴스에 사각형 저장</span><span class="sxs-lookup"><span data-stu-id="5ec9f-153">Storing a square in a CompoundCurve instance</span></span>
 <span data-ttu-id="5ec9f-154">다음 예에서는 `CompoundCurve` 인스턴스를 사용하여 사각형을 저장하는 두 가지 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="5ec9f-154">The following example uses two different ways to use a `CompoundCurve` instance to store a square.</span></span>

```sql
DECLARE @g1 geometry, @g2 geometry;
SET @g1 = geometry::Parse('COMPOUNDCURVE((1 1, 1 3), (1 3, 3 3),(3 3, 3 1), (3 1, 1 1))');
SET @g2 = geometry::Parse('COMPOUNDCURVE((1 1, 1 3, 3 3, 3 1, 1 1))');
SELECT @g1.STLength(), @g2.STLength();
```

 <span data-ttu-id="5ec9f-155">`@g1` 및 `@g2` 의 길이는 같습니다.</span><span class="sxs-lookup"><span data-stu-id="5ec9f-155">The lengths for both `@g1` and `@g2` are the same.</span></span> <span data-ttu-id="5ec9f-156">이 예에서는 `CompoundCurve` 인스턴스가 하나 이상의 `LineString` 인스턴스를 저장할 수 있음을 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ec9f-156">Notice from the example that a `CompoundCurve` instance can store one or more instances of `LineString`.</span></span>

### <a name="e-instantiating-a-geometry-instance-using-a-compoundcurve-with-multiple-circularstrings"></a><span data-ttu-id="5ec9f-157">E.</span><span class="sxs-lookup"><span data-stu-id="5ec9f-157">E.</span></span> <span data-ttu-id="5ec9f-158">여러 CircularString을 포함하는 CompoundCurve를 사용하여 기하 도형 인스턴스 인스턴스화</span><span class="sxs-lookup"><span data-stu-id="5ec9f-158">Instantiating a geometry instance using a CompoundCurve with multiple CircularStrings</span></span>
 <span data-ttu-id="5ec9f-159">다음 예에서는 서로 다른 두 `CircularString` 인스턴스를 사용하여 `CompoundCurve`를 초기화하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="5ec9f-159">The following example shows how to use two different `CircularString` instances to initialize a `CompoundCurve`.</span></span>

```sql
DECLARE @g geometry;
SET @g = geometry::Parse('COMPOUNDCURVE(CIRCULARSTRING(0 2, 2 0, 4 2), CIRCULARSTRING(4 2, 2 4, 0 2))');
SELECT @g.STLength();
```

 <span data-ttu-id="5ec9f-160">이렇게 하면 다음 출력이 생성 됩니다. 12.566370. 4&#x03c0; (4 \* pi)와 동일 합니다.</span><span class="sxs-lookup"><span data-stu-id="5ec9f-160">This produces the following output: 12.566370... which is the equivalent of 4&#x03c0; (4 \* pi).</span></span> <span data-ttu-id="5ec9f-161">예에서 `CompoundCurve` 인스턴스는 반지름이 2인 원을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="5ec9f-161">The `CompoundCurve` instance in the example stores a circle with a radius of 2.</span></span> <span data-ttu-id="5ec9f-162">앞의 두 코드 예에서는 `CompoundCurve`를 사용할 필요가 없었습니다.</span><span class="sxs-lookup"><span data-stu-id="5ec9f-162">Both of the previous code examples did not have to use a `CompoundCurve`.</span></span> <span data-ttu-id="5ec9f-163">첫 번째 예의 경우 `LineString` 인스턴스를 사용하면 더 간단했을 것이고 두 번째 예의 경우 `CircularString` 인스턴스를 사용하면 더 간단했을 것입니다.</span><span class="sxs-lookup"><span data-stu-id="5ec9f-163">For the first example a `LineString` instance would have been simpler, and a `CircularString` instance would have been simpler for the second example.</span></span> <span data-ttu-id="5ec9f-164">하지만 다음 예에서는 `CompoundCurve` 를 사용하는 것이 더 좋은 경우를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="5ec9f-164">However, the next example shows where a `CompoundCurve` provides a better alternative.</span></span>

### <a name="f-using-a-compoundcurve-to-store-a-semicircle"></a><span data-ttu-id="5ec9f-165">F.</span><span class="sxs-lookup"><span data-stu-id="5ec9f-165">F.</span></span> <span data-ttu-id="5ec9f-166">CompoundCurve를 사용하여 반원 저장</span><span class="sxs-lookup"><span data-stu-id="5ec9f-166">Using a CompoundCurve to store a semicircle</span></span>
 <span data-ttu-id="5ec9f-167">다음 예에서는 `CompoundCurve` 인스턴스를 사용하여 반원을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="5ec9f-167">The following example uses a `CompoundCurve` instance to store a semicircle.</span></span>

```sql
DECLARE @g geometry;
SET @g = geometry::Parse('COMPOUNDCURVE(CIRCULARSTRING(0 2, 2 0, 4 2), (4 2, 0 2))');
SELECT @g.STLength();
```

### <a name="g-storing-multiple-circularstring-and-linestring-instances-in-a-compoundcurve"></a><span data-ttu-id="5ec9f-168">G.</span><span class="sxs-lookup"><span data-stu-id="5ec9f-168">G.</span></span> <span data-ttu-id="5ec9f-169">CompoundCurve에 여러 개의 CircularString 및 LineString 인스턴스 저장</span><span class="sxs-lookup"><span data-stu-id="5ec9f-169">Storing multiple CircularString and LineString instances in a CompoundCurve</span></span>
 <span data-ttu-id="5ec9f-170">다음 예에서는 `CircularString` 를 사용하여 여러 개의 `LineString` 및 `CompoundCurve`인스턴스를 저장하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="5ec9f-170">The following example shows how multiple `CircularString` and `LineString` instances can be stored by using a `CompoundCurve`.</span></span>

```sql
DECLARE @g geometry
SET @g = geometry::Parse('COMPOUNDCURVE((3 5, 3 3), CIRCULARSTRING(3 3, 5 1, 7 3), (7 3, 7 5), CIRCULARSTRING(7 5, 5 7, 3 5))');
SELECT @g.STLength();
```

### <a name="h-storing-instances-with-z-and-m-values"></a><span data-ttu-id="5ec9f-171">H.</span><span class="sxs-lookup"><span data-stu-id="5ec9f-171">H.</span></span> <span data-ttu-id="5ec9f-172">Z 및 M 값이 있는 인스턴스 저장</span><span class="sxs-lookup"><span data-stu-id="5ec9f-172">Storing instances with Z and M values</span></span>
 <span data-ttu-id="5ec9f-173">다음 예에서는 `CompoundCurve` 인스턴스를 사용하여 Z 값과 M 값이 모두 있는 `CircularString` 및 `LineString` 인스턴스 시퀀스를 저장하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="5ec9f-173">The following example shows how to use a `CompoundCurve` instance to store a sequence of `CircularString` and `LineString` instances with both Z and M values.</span></span>

```sql
SET @g = geometry::Parse('COMPOUNDCURVE(CIRCULARSTRING(7 5 4 2, 5 7 4 2, 3 5 4 2), (3 5 4 2, 8 7 4 2))');
```

### <a name="i-illustrating-why-circularstring-instances-must-be-explicitly-declared"></a><span data-ttu-id="5ec9f-174">9\.</span><span class="sxs-lookup"><span data-stu-id="5ec9f-174">I.</span></span> <span data-ttu-id="5ec9f-175">CircularString 인스턴스를 명시적으로 선언해야 하는 이유에 대한 설명</span><span class="sxs-lookup"><span data-stu-id="5ec9f-175">Illustrating why CircularString instances must be explicitly declared</span></span>
 <span data-ttu-id="5ec9f-176">다음 예에서는 `CircularString` 인스턴스를 명시적으로 선언해야 하는 이유를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="5ec9f-176">The following example shows why `CircularString` instances must be explicitly declared.</span></span> <span data-ttu-id="5ec9f-177">프로그래머는 `CompoundCurve` 인스턴스에 원을 저장하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="5ec9f-177">The programmer is trying to store a circle in a `CompoundCurve` instance.</span></span>

```sql
DECLARE @g1 geometry;  
DECLARE @g2 geometry;
SET @g1 = geometry::Parse('COMPOUNDCURVE(CIRCULARSTRING(0 2, 2 0, 4 2), (4 2, 2 4, 0 2))');
SELECT 'Circle One', @g1.STLength() AS Perimeter;  -- gives an inaccurate amount
SET @g2 = geometry::Parse('COMPOUNDCURVE(CIRCULARSTRING(0 2, 2 0, 4 2), CIRCULARSTRING(4 2, 2 4, 0 2))');
SELECT 'Circle Two', @g2.STLength() AS Perimeter;  -- now we get an accurate amount
```

 <span data-ttu-id="5ec9f-178">출력은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="5ec9f-178">The output is as follows:</span></span>

```
Circle One11.940039...
Circle Two12.566370...
```

 <span data-ttu-id="5ec9f-179">원 2의 경계는 약 4&#x03c0; (4 \* pi) 이며,이 값은 경계의 실제 값입니다.</span><span class="sxs-lookup"><span data-stu-id="5ec9f-179">The perimeter for Circle Two is approximately 4&#x03c0; (4 \* pi), which is the actual value for the perimeter.</span></span> <span data-ttu-id="5ec9f-180">하지만 Circle One의 둘레는 매우 부정확합니다.</span><span class="sxs-lookup"><span data-stu-id="5ec9f-180">However, the perimeter for Circle One is significantly inaccurate.</span></span> <span data-ttu-id="5ec9f-181">Circle One의 `CompoundCurve` 인스턴스는 하나의 원호 세그먼트(ABC)와 두 개의 선분(CD, DA)을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="5ec9f-181">Circle One's `CompoundCurve` instance stores one circular arc segment (ABC) and two line segments (CD, DA).</span></span> <span data-ttu-id="5ec9f-182">원을 정의하려면 `CompoundCurve` 인스턴스는 두 개의 원호 세그먼트(ABC, CDA)를 저장해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5ec9f-182">The `CompoundCurve` instance has to store two circular arc segments (ABC, CDA) to define a circle.</span></span> <span data-ttu-id="5ec9f-183">1 `LineString` 인스턴스는 Circle One의 `CompoundCurve` 인스턴스에 두 번째 점 집합(4 2, 2 4, 0 2)을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="5ec9f-183">A `LineString` instance defines the second set of points (4 2, 2 4, 0 2) in Circle One's `CompoundCurve` instance.</span></span> <span data-ttu-id="5ec9f-184">`CircularString` 내부에서 `CompoundCurve`인스턴스를 명시적으로 선언해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5ec9f-184">You have to explicitly declare a `CircularString` instance inside a `CompoundCurve`.</span></span>

## <a name="see-also"></a><span data-ttu-id="5ec9f-185">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5ec9f-185">See Also</span></span>
 <span data-ttu-id="5ec9f-186">[Stisvalid &#40;Geometry 데이터 형식&#41;](/sql/t-sql/spatial-geometry/stisvalid-geometry-data-type) [stisvalid &#40;geometry 데이터 형식&#41;](/sql/t-sql/spatial-geometry/stlength-geometry-data-type) [stisvalid](/sql/t-sql/spatial-geometry/ststartpoint-geometry-data-type) &#40;geometry 데이터 형식&#41;[stisvalid &#40;Geometry 데이터](/sql/t-sql/spatial-geometry/stendpoint-geometry-data-type) 형식&#41;[LineString](linestring.md) [CircularString](circularstring.md) [공간 데이터 형식 개요](spatial-data-types-overview.md) [Point](point.md)</span><span class="sxs-lookup"><span data-stu-id="5ec9f-186">[STIsValid &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/stisvalid-geometry-data-type) [STLength &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/stlength-geometry-data-type) [STStartPoint &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/ststartpoint-geometry-data-type) [STEndpoint &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/stendpoint-geometry-data-type) [LineString](linestring.md) [CircularString](circularstring.md) [Spatial Data Types Overview](spatial-data-types-overview.md) [Point](point.md)</span></span>


