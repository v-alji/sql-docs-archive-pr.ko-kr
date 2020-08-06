---
title: geometry 인스턴스 만들기, 구성 및 쿼리 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- planar spatial data [SQL Server], getting started
- geometry data type [SQL Server], getting started
ms.assetid: c6b5c852-37d2-48d0-a8ad-e43bb80d6514
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 539f3f8bb1d9a1c277d6317cc571cf8bcb281833
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646854"
---
# <a name="create-construct-and-query-geometry-instances"></a><span data-ttu-id="52f6e-102">geometry 인스턴스 만들기, 구성 및 쿼리</span><span class="sxs-lookup"><span data-stu-id="52f6e-102">Create, Construct, and Query geometry Instances</span></span>
  <span data-ttu-id="52f6e-103">평면 공간 데이터 형식 `geometry`는 유클리드(평면) 좌표계의 데이터를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="52f6e-103">The planar spatial data type, `geometry`, represents data in a Euclidean (flat) coordinate system.</span></span> <span data-ttu-id="52f6e-104">이 형식은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 CLR(공용 언어 런타임) 데이터 형식으로 구현됩니다.</span><span class="sxs-lookup"><span data-stu-id="52f6e-104">This type is implemented as a common language runtime (CLR) data type in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="52f6e-105">`geometry` 형식은 각 데이터베이스에서 미리 정의되고 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52f6e-105">The `geometry` type is predefined and available in each database.</span></span> <span data-ttu-id="52f6e-106">다른 CLR 형식을 사용할 때와 동일한 방식으로 `geometry` 형식의 테이블 열을 만들고 `geometry` 데이터에 대한 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52f6e-106">You can create table columns of type `geometry` and operate on `geometry` data in the same manner as you would use other CLR types.</span></span>  
  
 <span data-ttu-id="52f6e-107">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 지원되는 `geometry` 데이터 형식(평면)은 Open Geospatial Consortium (OGC) Simple Features for SQL Specification 버전 1.1.0을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="52f6e-107">The `geometry` data type (planar) supported by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] conforms to the Open Geospatial Consortium (OGC) Simple Features for SQL Specification version 1.1.0.</span></span>  
  
 <span data-ttu-id="52f6e-108">OGC 사양에 대한 자세한 내용은 다음을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="52f6e-108">For more information on OGC specifications, see the following:</span></span>  
  
-   [<span data-ttu-id="52f6e-109">OGC Specifications, Simple Feature Access Part 1 - Common Architecture</span><span class="sxs-lookup"><span data-stu-id="52f6e-109">OGC Specifications, Simple Feature Access Part 1 - Common Architecture</span></span>](https://go.microsoft.com/fwlink/?LinkId=93628)  
  
-   [<span data-ttu-id="52f6e-110">OGC Specifications, Simple Feature Access Part 2 - SQL Options</span><span class="sxs-lookup"><span data-stu-id="52f6e-110">OGC Specifications, Simple Feature Access Part 2 - SQL Options</span></span>](https://go.microsoft.com/fwlink/?LinkId=93629)  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="52f6e-111">에서는 [https://schemas.microsoft.com/sqlserver/profiles/gml/SpatialGML.xsd](https://go.microsoft.com/fwlink/?LinkId=230959) 스키마에 정의된 기존 GML 3.1 표준의 하위 집합을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="52f6e-111">supports a subset of the existing GML 3.1 standard which is defined in the following schema: [https://schemas.microsoft.com/sqlserver/profiles/gml/SpatialGML.xsd](https://go.microsoft.com/fwlink/?LinkId=230959).</span></span>  
  
##  <a name="creating-or-constructing-a-new-geometry-instance"></a><a name="creating"></a> <span data-ttu-id="52f6e-112">새 geometry 인스턴스 만들기 또는 구성</span><span class="sxs-lookup"><span data-stu-id="52f6e-112">Creating or constructing a new geometry instance</span></span>  
  
###  <a name="creating-a-new-geometry-instance-from-an-existing-instance"></a><a name="existing"></a> <span data-ttu-id="52f6e-113">기존 인스턴스에서 새 geometry 인스턴스 만들기</span><span class="sxs-lookup"><span data-stu-id="52f6e-113">Creating a New geometry Instance from an Existing Instance</span></span>  
 <span data-ttu-id="52f6e-114">`geometry` 데이터 형식은 수많은 기본 메서드를 제공합니다. 이러한 메서드를 사용하여 기존 인스턴스에 기반하여 새 `geometry` 인스턴스를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52f6e-114">The `geometry` data type provides numerous built-in methods you can use to create new `geometry` instances based on existing instances.</span></span>  
  
 <span data-ttu-id="52f6e-115">**geometry 버퍼를 만들려면**</span><span class="sxs-lookup"><span data-stu-id="52f6e-115">**To create a buffer around a geometry**</span></span>  
 [<span data-ttu-id="52f6e-116">STBuffer&#40;geometry 데이터 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="52f6e-116">STBuffer &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/stbuffer-geometry-data-type)  
  
 [<span data-ttu-id="52f6e-117">BufferWithTolerance&#40;geometry 데이터 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="52f6e-117">BufferWithTolerance &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/bufferwithtolerance-geometry-data-type)  
  
 <span data-ttu-id="52f6e-118">**간단한 geometry 버전을 만들려면**</span><span class="sxs-lookup"><span data-stu-id="52f6e-118">**To create a simplified version of a geometry**</span></span>  
 [<span data-ttu-id="52f6e-119">Reduce&#40;geometry 데이터 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="52f6e-119">Reduce &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/reduce-geometry-data-type)  
  
 <span data-ttu-id="52f6e-120">**geometry의 네 점을 만들려면**</span><span class="sxs-lookup"><span data-stu-id="52f6e-120">**To create the convex hull of a geometry**</span></span>  
 [<span data-ttu-id="52f6e-121">STConvexHull&#40;geometry 데이터 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="52f6e-121">STConvexHull &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/stconvexhull-geometry-data-type)  
  
 <span data-ttu-id="52f6e-122">**두 geometry의 교집합에서 geometry를 만들려면**</span><span class="sxs-lookup"><span data-stu-id="52f6e-122">**To create a geometry from the intersection of two geometries**</span></span>  
 [<span data-ttu-id="52f6e-123">STIntersection&#40;geometry 데이터 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="52f6e-123">STIntersection &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/stintersection-geometry-data-type)  
  
 <span data-ttu-id="52f6e-124">**두 geometry의 합집합에서 geometry를 만들려면**</span><span class="sxs-lookup"><span data-stu-id="52f6e-124">**To create a geometry from the union of two geometries**</span></span>  
 [<span data-ttu-id="52f6e-125">STUnion&#40;geometry 데이터 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="52f6e-125">STUnion &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/stunion-geometry-data-type)  
  
 <span data-ttu-id="52f6e-126">**한 geometry가 다른 geometry와 겹치지 않는 점에서 geometry를 만들려면**</span><span class="sxs-lookup"><span data-stu-id="52f6e-126">**To create a geometry from the points where one geometry does not overlap another**</span></span>  
 [<span data-ttu-id="52f6e-127">STDifference&#40;geometry 데이터 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="52f6e-127">STDifference &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/stdifference-geometry-data-type)  
  
 <span data-ttu-id="52f6e-128">**두 geometry가 겹치지 않는 점에서 geometry를 만들려면**</span><span class="sxs-lookup"><span data-stu-id="52f6e-128">**To create a geometry from the points where two geometries do not overlap**</span></span>  
 [<span data-ttu-id="52f6e-129">STSymDifference&#40;geometry 데이터 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="52f6e-129">STSymDifference &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/stsymdifference-geometry-data-type)  
  
 <span data-ttu-id="52f6e-130">**기존 geometry에 있는 임의의 Point 인스턴스를 만들려면**</span><span class="sxs-lookup"><span data-stu-id="52f6e-130">**To create an arbitrary Point instance that lies on an existing geometry**</span></span>  
 [<span data-ttu-id="52f6e-131">STPointOnSurface&#40;geometry 데이터 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="52f6e-131">STPointOnSurface &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/stpointonsurface-geometry-data-type)  
  
  
  
###  <a name="constructing-a-geometry-instance-from-well-known-text-input"></a><a name="wkt"></a> <span data-ttu-id="52f6e-132">WKT 입력에서 geometry 인스턴스 구성</span><span class="sxs-lookup"><span data-stu-id="52f6e-132">Constructing a geometry Instance from Well-Known Text Input</span></span>  
 <span data-ttu-id="52f6e-133">`geometry` 데이터 형식은 OGC(Open Geospatial Consortium) WKT 표현에서 기하 도형을 생성하는 여러 가지 기본 메서드를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="52f6e-133">The `geometry` data type provides several built-in methods that generate a geometry from the Open Geospatial Consortium (OGC) WKT representation.</span></span> <span data-ttu-id="52f6e-134">WKT 표준은 기하 도형 데이터를 텍스트 형식으로 교환할 수 있는 텍스트 문자열입니다.</span><span class="sxs-lookup"><span data-stu-id="52f6e-134">The WKT standard is a text string that allows geometry data to be exchanged in textual form.</span></span>  
  
 <span data-ttu-id="52f6e-135">**WKT 입력에서 모든 유형의 geometry 인스턴스를 생성하려면**</span><span class="sxs-lookup"><span data-stu-id="52f6e-135">**To construct any type of geometry instance from WKT input**</span></span>  
 [<span data-ttu-id="52f6e-136">STGeomFromText&#40;geometry 데이터 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="52f6e-136">STGeomFromText &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/stgeomfromtext-geometry-data-type)  
  
 [<span data-ttu-id="52f6e-137">Parse&#40;geometry 데이터 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="52f6e-137">Parse &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/parse-geometry-data-type)  
  
 <span data-ttu-id="52f6e-138">**WKT 입력에서 기하 도형 Point 인스턴스를 생성하려면**</span><span class="sxs-lookup"><span data-stu-id="52f6e-138">**To construct a geometry Point instance from WKT input**</span></span>  
 [<span data-ttu-id="52f6e-139">STPointFromText&#40;geometry 데이터 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="52f6e-139">STPointFromText &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/stpointfromtext-geometry-data-type)  
  
 <span data-ttu-id="52f6e-140">**WKT 입력에서 기하 도형 MultiPoint 인스턴스를 생성하려면**</span><span class="sxs-lookup"><span data-stu-id="52f6e-140">**To construct a geometry MultiPoint instance from WKT input**</span></span>  
 [<span data-ttu-id="52f6e-141">STMPointFromText&#40;geometry 데이터 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="52f6e-141">STMPointFromText &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/stmpointfromtext-geometry-data-type)  
  
 <span data-ttu-id="52f6e-142">**WKT 입력에서 기하 도형 LineString 인스턴스를 생성하려면**</span><span class="sxs-lookup"><span data-stu-id="52f6e-142">**To construct a geometry LineString instance from WKT input**</span></span>  
 [<span data-ttu-id="52f6e-143">STLineFromText&#40;geometry 데이터 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="52f6e-143">STLineFromText &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/stlinefromtext-geometry-data-type)  
  
 <span data-ttu-id="52f6e-144">**WKT 입력에서 기하 도형 MultiLineString 인스턴스를 생성하려면**</span><span class="sxs-lookup"><span data-stu-id="52f6e-144">**To construct a geometry MultiLineString instance from WKT input**</span></span>  
 [<span data-ttu-id="52f6e-145">STMLineFromText&#40;geometry 데이터 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="52f6e-145">STMLineFromText &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/stmlinefromtext-geometry-data-type)  
  
 <span data-ttu-id="52f6e-146">**WKT 입력에서 기하 도형 Polygon 인스턴스를 생성하려면**</span><span class="sxs-lookup"><span data-stu-id="52f6e-146">**To construct a geometry Polygon instance from WKT input**</span></span>  
 [<span data-ttu-id="52f6e-147">STPolyFromText&#40;geometry 데이터 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="52f6e-147">STPolyFromText &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/stpolyfromtext-geometry-data-type)  
  
 <span data-ttu-id="52f6e-148">**WKT 입력에서 기하 도형 MultiPolygon 인스턴스를 생성하려면**</span><span class="sxs-lookup"><span data-stu-id="52f6e-148">**To construct a geometry MultiPolygon instance from WKT input**</span></span>  
 [<span data-ttu-id="52f6e-149">STMPolyFromText&#40;geometry 데이터 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="52f6e-149">STMPolyFromText &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/stmpolyfromtext-geometry-data-type)  
  
 <span data-ttu-id="52f6e-150">**WKT 입력에서 기하 도형 GeometryCollection 인스턴스를 생성하려면**</span><span class="sxs-lookup"><span data-stu-id="52f6e-150">**To construct a geometry GeometryCollection instance from WKT input**</span></span>  
 [<span data-ttu-id="52f6e-151">STGeomCollFromText&#40;geometry 데이터 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="52f6e-151">STGeomCollFromText &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/stgeomcollfromtext-geometry-data-type)  
  
  
  
###  <a name="constructing-a-geometry-instance-from-well-known-binary-input"></a><a name="wkb"></a> <span data-ttu-id="52f6e-152">WKB 입력에서 geometry 인스턴스 구성</span><span class="sxs-lookup"><span data-stu-id="52f6e-152">Constructing a geometry Instance from Well-Known Binary Input</span></span>  
 <span data-ttu-id="52f6e-153">WKB는 OGC(Open Geospatial Consortium)에서 지정한 이진 형식으로, 클라이언트 애플리케이션과 SQL 데이터베이스 간에 `geometry` 데이터를 교환하도록 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="52f6e-153">WKB is a binary format specified by the Open Geospatial Consortium (OGC) that permits `geometry` data to be exchanged between a client application and an SQL database.</span></span> <span data-ttu-id="52f6e-154">다음 함수는 WKB 입력을 사용하여 기하 도형을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="52f6e-154">The following functions accept WKB input to construct geometries:</span></span>  
  
 <span data-ttu-id="52f6e-155">**WKB 입력에서 모든 유형의 geometry 인스턴스를 생성하려면**</span><span class="sxs-lookup"><span data-stu-id="52f6e-155">**To construct any type of geometry instance from WKB input**</span></span>  
 [<span data-ttu-id="52f6e-156">STGeomFromWKB&#40;geometry 데이터 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="52f6e-156">STGeomFromWKB &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/stgeomfromwkb-geometry-data-type)  
  
 <span data-ttu-id="52f6e-157">**WKB 입력에서 기하 도형 Point 인스턴스를 생성하려면**</span><span class="sxs-lookup"><span data-stu-id="52f6e-157">**To construct a geometry Point instance from WKB input**</span></span>  
 [<span data-ttu-id="52f6e-158">STPointFromWKB&#40;geometry 데이터 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="52f6e-158">STPointFromWKB &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/stpointfromwkb-geometry-data-type)  
  
 <span data-ttu-id="52f6e-159">**WKB 입력에서 기하 도형 MultiPoint 인스턴스를 생성하려면**</span><span class="sxs-lookup"><span data-stu-id="52f6e-159">**To construct a geometry MultiPoint instance from WKB input**</span></span>  
 [<span data-ttu-id="52f6e-160">STMPointFromWKB&#40;geometry 데이터 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="52f6e-160">STMPointFromWKB &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/stmpointfromwkb-geometry-data-type)  
  
 <span data-ttu-id="52f6e-161">**WKB 입력에서 기하 도형 LineString 인스턴스를 생성하려면**</span><span class="sxs-lookup"><span data-stu-id="52f6e-161">**To construct a geometry LineString instance from WKB input**</span></span>  
 [<span data-ttu-id="52f6e-162">STLineFromWKB&#40;geometry 데이터 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="52f6e-162">STLineFromWKB &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/stlinefromwkb-geometry-data-type)  
  
 <span data-ttu-id="52f6e-163">**WKB 입력에서 기하 도형 MultiLineString 인스턴스를 생성하려면**</span><span class="sxs-lookup"><span data-stu-id="52f6e-163">**To construct a geometry MultiLineString instance from WKB input**</span></span>  
 [<span data-ttu-id="52f6e-164">STMLineFromWKB&#40;geometry 데이터 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="52f6e-164">STMLineFromWKB &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/stmlinefromwkb-geometry-data-type)  
  
 <span data-ttu-id="52f6e-165">**WKB 입력에서 기하 도형 Polygon 인스턴스를 생성하려면**</span><span class="sxs-lookup"><span data-stu-id="52f6e-165">**To construct a geometry Polygon instance from WKB input**</span></span>  
 [<span data-ttu-id="52f6e-166">STPolyFromWKB&#40;geometry 데이터 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="52f6e-166">STPolyFromWKB &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/stpolyfromwkb-geometry-data-type)  
  
 <span data-ttu-id="52f6e-167">**WKB 입력에서 기하 도형 MultiPolygon 인스턴스를 생성하려면**</span><span class="sxs-lookup"><span data-stu-id="52f6e-167">**To construct a geometry MultiPolygon instance from WKB input**</span></span>  
 [<span data-ttu-id="52f6e-168">STMPolyFromWKB&#40;geometry 데이터 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="52f6e-168">STMPolyFromWKB &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/stmpolyfromwkb-geometry-data-type)  
  
 <span data-ttu-id="52f6e-169">**WKB 입력에서 기하 도형 GeometryCollection 인스턴스를 생성하려면**</span><span class="sxs-lookup"><span data-stu-id="52f6e-169">**To construct a geometry GeometryCollection instance from WKB input**</span></span>  
 [<span data-ttu-id="52f6e-170">STGeomCollFromWKB&#40;geometry 데이터 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="52f6e-170">STGeomCollFromWKB &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/stgeomcollfromwkb-geometry-data-type)  
  
  
  
###  <a name="constructing-a-geometry-instance-from-gml-text-input"></a><a name="gml"></a> <span data-ttu-id="52f6e-171">GML 텍스트 입력에서 geometry 인스턴스 구성</span><span class="sxs-lookup"><span data-stu-id="52f6e-171">Constructing a geometry Instance from GML Text Input</span></span>  
 <span data-ttu-id="52f6e-172">`geometry`데이터 형식은 `geometry` 기하학적 개체의 XML 표현인 GML에서 인스턴스를 생성 하는 메서드를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="52f6e-172">The `geometry` data type provides a method that generates a `geometry` instance from GML, an XML representation of geometric objects.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="52f6e-173">는 GML 하위 집합을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="52f6e-173">supports a subset of GML.</span></span>  
  
 <span data-ttu-id="52f6e-174">**GML 입력에서 모든 유형의 geometry 인스턴스를 생성하려면**</span><span class="sxs-lookup"><span data-stu-id="52f6e-174">**To construct any type of geometry instance from GML input**</span></span>  
 [<span data-ttu-id="52f6e-175">GeomFromGml&#40;geometry 데이터 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="52f6e-175">GeomFromGml &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/geomfromgml-geometry-data-type)  
  
  
  
##  <a name="returning-well-known-text-and-well-known-binary-from-a-geometry-instance"></a><a name="returning"></a> <span data-ttu-id="52f6e-176">geometry 인스턴스에서 WKT 및 WKB 반환</span><span class="sxs-lookup"><span data-stu-id="52f6e-176">Returning Well-Known Text and Well-Known Binary from a geometry Instance</span></span>  
 <span data-ttu-id="52f6e-177">다음 메서드를 사용하여 `geometry` 인스턴스의 WKT 또는 WKB 형식을 반환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52f6e-177">You can use the following methods to return either the WKT or WKB format of a `geometry` instance:</span></span>  
  
 <span data-ttu-id="52f6e-178">**geometry 인스턴스의 WKT 표현을 반환하려면**</span><span class="sxs-lookup"><span data-stu-id="52f6e-178">**To return the WKT representation of a geometry instance**</span></span>  
 [<span data-ttu-id="52f6e-179">STAsText&#40;geometry 데이터 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="52f6e-179">STAsText &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/stastext-geometry-data-type)  
  
 [<span data-ttu-id="52f6e-180">ToString&#40;geometry 데이터 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="52f6e-180">ToString &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/tostring-geometry-data-type)  
  
 <span data-ttu-id="52f6e-181">**Z 및 M 값을 포함하여 geometry 인스턴스의 WKT 표현을 반환하려면**</span><span class="sxs-lookup"><span data-stu-id="52f6e-181">**To return the WKT representation of a geometry instance including any Z and M values**</span></span>  
 [<span data-ttu-id="52f6e-182">AsTextZM&#40;geometry 데이터 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="52f6e-182">AsTextZM &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/astextzm-geometry-data-type)  
  
 <span data-ttu-id="52f6e-183">**geometry 인스턴스의 WKB 표현을 반환하려면**</span><span class="sxs-lookup"><span data-stu-id="52f6e-183">**To return the WKB representation of a geometry instance**</span></span>  
 [<span data-ttu-id="52f6e-184">STAsBinary&#40;geometry 데이터 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="52f6e-184">STAsBinary &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/stasbinary-geometry-data-type)  
  
 <span data-ttu-id="52f6e-185">**geometry 인스턴스의 GML 표현을 반환하려면**</span><span class="sxs-lookup"><span data-stu-id="52f6e-185">**To return a GML representation of a geometry instance**</span></span>  
 [<span data-ttu-id="52f6e-186">AsGml&#40;geometry 데이터 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="52f6e-186">AsGml &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/asgml-geometry-data-type)  
  
  
  
##  <a name="querying-the-properties-and-behaviors-of-geometry-instances"></a><a name="querying"></a> <span data-ttu-id="52f6e-187">geometry 인스턴스의 속성 및 동작 쿼리</span><span class="sxs-lookup"><span data-stu-id="52f6e-187">Querying the Properties and Behaviors of geometry Instances</span></span>  
 <span data-ttu-id="52f6e-188">모든 `geometry` 인스턴스에는에서 제공 하는 메서드를 통해 검색할 수 있는 여러 속성이 있습니다 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="52f6e-188">All `geometry` instances have a number of properties that can be retrieved through methods that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provides.</span></span> <span data-ttu-id="52f6e-189">다음 항목에서는 기하 도형 형식의 속성과 동작 및 각각을 쿼리하는 메서드를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="52f6e-189">The following topics define the properties and behaviors of geometry types, and the methods for querying each one.</span></span>  
  
###  <a name="validity-instance-type-and-geometrycollection-information"></a><a name="valid"></a> <span data-ttu-id="52f6e-190">유효성, 인스턴스 유형 및 GeometryCollection 정보</span><span class="sxs-lookup"><span data-stu-id="52f6e-190">Validity, Instance Type, and GeometryCollection Information</span></span>  
 <span data-ttu-id="52f6e-191">`geometry` 인스턴스가 생성되면 다음 메서드를 사용하여 이 인스턴스가 올바른 형식일 경우 인스턴스 유형을 반환하는지 또는 컬렉션 인스턴스일 경우 특정 `geometry` 인스턴스를 반환하는지를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52f6e-191">Once a `geometry` instance is constructed, you can use the following methods to determine if it is well-formed, return the instance type, or, if it is a collection instance, return a specific `geometry` instance.</span></span>  
  
 <span data-ttu-id="52f6e-192">**geometry 인스턴스 유형을 반환하려면**</span><span class="sxs-lookup"><span data-stu-id="52f6e-192">**To return the instance type of a geometry**</span></span>  
 [<span data-ttu-id="52f6e-193">STGeometryType&#40;geometry 데이터 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="52f6e-193">STGeometryType &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/stgeometrytype-geometry-data-type)  
  
 <span data-ttu-id="52f6e-194">**기하 도형이 지정된 인스턴스 유형인지 확인하려면**</span><span class="sxs-lookup"><span data-stu-id="52f6e-194">**To determine if a geometry is a given instance type**</span></span>  
 [<span data-ttu-id="52f6e-195">InstanceOf&#40;geometry 데이터 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="52f6e-195">InstanceOf &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/instanceof-geometry-data-type)  
  
 <span data-ttu-id="52f6e-196">**geometry 인스턴스가 해당 인스턴스 유형에 대해 형식이 올바른지 확인하려면**</span><span class="sxs-lookup"><span data-stu-id="52f6e-196">**To determine if a geometry instance is well-formed for its instance type**</span></span>  
 [<span data-ttu-id="52f6e-197">STIsValid&#40;geometry 데이터 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="52f6e-197">STIsValid &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/stisvalid-geometry-data-type)  
  
 <span data-ttu-id="52f6e-198">**geometry 인스턴스를 인스턴스 유형이 있는 올바른 형식의 geometry 인스턴스로 변환하려면**</span><span class="sxs-lookup"><span data-stu-id="52f6e-198">**To convert a geometry instance to a well-formed geometry instance with an instance type**</span></span>  
 [<span data-ttu-id="52f6e-199">MakeValid&#40;geometry 데이터 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="52f6e-199">MakeValid &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/makevalid-geometry-data-type)  
  
 <span data-ttu-id="52f6e-200">**기하 도형 컬렉션 인스턴스에 있는 기하 도형의 개수를 반환하려면**</span><span class="sxs-lookup"><span data-stu-id="52f6e-200">**To return the number of geometries in a geometry collection instance**</span></span>  
 [<span data-ttu-id="52f6e-201">STNumGeometries&#40;geometry 데이터 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="52f6e-201">STNumGeometries &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/stnumgeometries-geometry-data-type)  
  
 <span data-ttu-id="52f6e-202">기하 도형 컬렉션 인스턴스에서 특정 기하 도형을 반환하려면</span><span class="sxs-lookup"><span data-stu-id="52f6e-202">To return a specific geometry in a geometry collection instance</span></span>  
 <span data-ttu-id="52f6e-203">[STGeometryN&#40;geometry 데이터 형식&#41;](/sql/t-sql/spatial-geometry/stgeometryn-geometry-data-type)STGeometryN(geometry 데이터 형식)</span><span class="sxs-lookup"><span data-stu-id="52f6e-203">[STGeometryN &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/stgeometryn-geometry-data-type)STGeometryN (geometry Data type)</span></span>  
  
  
  
###  <a name="number-of-points"></a><a name="number"></a> <span data-ttu-id="52f6e-204">점 수</span><span class="sxs-lookup"><span data-stu-id="52f6e-204">Number of Points</span></span>  
 <span data-ttu-id="52f6e-205">비어 있지 `geometry` 않은 모든 인스턴스는 *점으로*구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="52f6e-205">All nonempty `geometry` instances are comprised of *points*.</span></span> <span data-ttu-id="52f6e-206">이러한 점은 기하 도형이 그려지는 평면의 X 및 Y 좌표를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="52f6e-206">These points represent the X- and Y-coordinates of the plane on which the geometries are drawn.</span></span> <span data-ttu-id="52f6e-207">`geometry`는 인스턴스의 점을 쿼리하는 데 필요한 수많은 기본 메서드를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="52f6e-207">`geometry` provides numerous built-in methods for querying the points of an instance.</span></span>  
  
 <span data-ttu-id="52f6e-208">**인스턴스를 구성하는 점 개수를 반환하려면**</span><span class="sxs-lookup"><span data-stu-id="52f6e-208">**To return the number of points that comprise an instance**</span></span>  
 [<span data-ttu-id="52f6e-209">STNumPoints&#40;geometry 데이터 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="52f6e-209">STNumPoints &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/stnumpoints-geometry-data-type)  
  
 <span data-ttu-id="52f6e-210">**인스턴스의 특정 점을 반환하려면**</span><span class="sxs-lookup"><span data-stu-id="52f6e-210">**To return a specific point in an instance**</span></span>  
 [<span data-ttu-id="52f6e-211">STPointN</span><span class="sxs-lookup"><span data-stu-id="52f6e-211">STPointN</span></span>](/sql/t-sql/spatial-geometry/stpointn-geometry-data-type)  
  
 <span data-ttu-id="52f6e-212">**인스턴스에 있는 임의의 점을 반환하려면**</span><span class="sxs-lookup"><span data-stu-id="52f6e-212">**To return an arbitrary point that lies on an instance**</span></span>  
 [<span data-ttu-id="52f6e-213">STPointOnSurface</span><span class="sxs-lookup"><span data-stu-id="52f6e-213">STPointOnSurface</span></span>](/sql/t-sql/spatial-geometry/stpointonsurface-geometry-data-type)  
  
 <span data-ttu-id="52f6e-214">**인스턴스의 시작점을 반환하려면**</span><span class="sxs-lookup"><span data-stu-id="52f6e-214">**To return the start point of an instance**</span></span>  
 [<span data-ttu-id="52f6e-215">STStartPoint</span><span class="sxs-lookup"><span data-stu-id="52f6e-215">STStartPoint</span></span>](/sql/t-sql/spatial-geometry/ststartpoint-geometry-data-type)  
  
 <span data-ttu-id="52f6e-216">**인스턴스의 끝점을 반환하려면**</span><span class="sxs-lookup"><span data-stu-id="52f6e-216">**To return the end point of an instance**</span></span>  
 [<span data-ttu-id="52f6e-217">STEndpoint</span><span class="sxs-lookup"><span data-stu-id="52f6e-217">STEndpoint</span></span>](/sql/t-sql/spatial-geometry/stendpoint-geometry-data-type)  
  
 <span data-ttu-id="52f6e-218">**Point 인스턴스의 X 좌표를 반환하려면**</span><span class="sxs-lookup"><span data-stu-id="52f6e-218">**To return the X-coordinate of a Point instance**</span></span>  
 [<span data-ttu-id="52f6e-219">STX&#40;geometry 데이터 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="52f6e-219">STX &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/stx-geometry-data-type)  
  
 <span data-ttu-id="52f6e-220">**Point 인스턴스의 Y 좌표를 반환하려면**</span><span class="sxs-lookup"><span data-stu-id="52f6e-220">**To return the Y-coordinate of a Point instance**</span></span>  
 [<span data-ttu-id="52f6e-221">STY</span><span class="sxs-lookup"><span data-stu-id="52f6e-221">STY</span></span>](/sql/t-sql/spatial-geometry/sty-geometry-data-type)  
  
 <span data-ttu-id="52f6e-222">**Polygon, CurvePolygon 또는 MultiPolygon 인스턴스의 기하학적 중심점을 반환하려면**</span><span class="sxs-lookup"><span data-stu-id="52f6e-222">**To return the geometric center point of a Polygon, CurvePolygon, or MultiPolygon instance**</span></span>  
 [<span data-ttu-id="52f6e-223">STCentroid</span><span class="sxs-lookup"><span data-stu-id="52f6e-223">STCentroid</span></span>](/sql/t-sql/spatial-geometry/stcentroid-geometry-data-type)  
  
  
  
###  <a name="dimension"></a><a name="dimension"></a> <span data-ttu-id="52f6e-224">차원</span><span class="sxs-lookup"><span data-stu-id="52f6e-224">Dimension</span></span>  
 <span data-ttu-id="52f6e-225">비어 있지 않은 `geometry` 인스턴스는 0, 1 또는 2차원이 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52f6e-225">A nonempty `geometry` instance can be 0-, 1-, or 2-dimensional.</span></span> <span data-ttu-id="52f6e-226">`geometries` 및 `Point`와 같은 0차원 `MultiPoint`에는 길이 또는 영역이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="52f6e-226">Zero-dimensional `geometries`, such as `Point` and `MultiPoint`, have no length or area.</span></span> <span data-ttu-id="52f6e-227">`LineString, CircularString, CompoundCurve` 및 `MultiLineString`과 같은 1차원 개체에는 길이가 있고,</span><span class="sxs-lookup"><span data-stu-id="52f6e-227">One-dimensional objects, such as `LineString, CircularString, CompoundCurve`, and `MultiLineString`, have length.</span></span> <span data-ttu-id="52f6e-228">`Polygon`, `CurvePolygon` 및 `MultiPolygon`과 같은 2차원 인스턴스에는 영역과 길이가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52f6e-228">Two-dimensional instances, such as `Polygon`, `CurvePolygon`, and `MultiPolygon`, have area and length.</span></span> <span data-ttu-id="52f6e-229">비어 있는 인스턴스에서는 -1차원을 보고하고 `GeometryCollection`에서는 해당 내용의 유형에 따라 다른 영역을 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="52f6e-229">Empty instances will report a dimension of -1, and a `GeometryCollection` will report an area dependent on the types of its contents.</span></span>  
  
 <span data-ttu-id="52f6e-230">**인스턴스의 차원을 반환하려면**</span><span class="sxs-lookup"><span data-stu-id="52f6e-230">**To return the dimension of an instance**</span></span>  
 [<span data-ttu-id="52f6e-231">STDimension</span><span class="sxs-lookup"><span data-stu-id="52f6e-231">STDimension</span></span>](/sql/t-sql/spatial-geometry/stdimension-geometry-data-type)  
  
 <span data-ttu-id="52f6e-232">**인스턴스의 길이를 반환하려면**</span><span class="sxs-lookup"><span data-stu-id="52f6e-232">**To return the length of an instance**</span></span>  
 [<span data-ttu-id="52f6e-233">STLength</span><span class="sxs-lookup"><span data-stu-id="52f6e-233">STLength</span></span>](/sql/t-sql/spatial-geometry/stlength-geometry-data-type)  
  
 <span data-ttu-id="52f6e-234">**인스턴스의 영역을 반환하려면**</span><span class="sxs-lookup"><span data-stu-id="52f6e-234">**To return the area of an instance**</span></span>  
 [<span data-ttu-id="52f6e-235">STArea</span><span class="sxs-lookup"><span data-stu-id="52f6e-235">STArea</span></span>](/sql/t-sql/spatial-geometry/starea-geometry-data-type)  
  
  
  
###  <a name="empty"></a><a name="empty"></a> <span data-ttu-id="52f6e-236">비어 있음</span><span class="sxs-lookup"><span data-stu-id="52f6e-236">Empty</span></span>  
 <span data-ttu-id="52f6e-237">*빈* `geometry` 인스턴스에는 점이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="52f6e-237">An *empty*`geometry` instance does not have any points.</span></span> <span data-ttu-id="52f6e-238">비어 있는 `LineString, CircularString`, `CompoundCurve` 및 `MultiLineString` 인스턴스의 길이는 0입니다.</span><span class="sxs-lookup"><span data-stu-id="52f6e-238">The length of empty `LineString, CircularString`, `CompoundCurve`, and `MultiLineString` instances is zero.</span></span> <span data-ttu-id="52f6e-239">비어 있는 `Polygon`, `CurvePolygon` 및 `MultiPolygon` 인스턴스의 영역은 0입니다.</span><span class="sxs-lookup"><span data-stu-id="52f6e-239">The area of empty `Polygon`, `CurvePolygon`, and `MultiPolygon` instances is 0.</span></span>  
  
 <span data-ttu-id="52f6e-240">**인스턴스가 비어 있는지 확인하려면**</span><span class="sxs-lookup"><span data-stu-id="52f6e-240">**To determine if an instance is empty**</span></span>  
 <span data-ttu-id="52f6e-241">[STIsEmpty](/sql/t-sql/spatial-geometry/stisempty-geometry-data-type).</span><span class="sxs-lookup"><span data-stu-id="52f6e-241">[STIsEmpty](/sql/t-sql/spatial-geometry/stisempty-geometry-data-type).</span></span>  
  
  
  
###  <a name="simple"></a><a name="simple"></a> <span data-ttu-id="52f6e-242">간단</span><span class="sxs-lookup"><span data-stu-id="52f6e-242">Simple</span></span>  
 <span data-ttu-id="52f6e-243">인스턴스의를 `geometry` *간단*하 게 만들려면 다음 요구 사항을 모두 충족 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="52f6e-243">For a `geometry` of the instance to be *simple*, it must meet both of these requirements:</span></span>  
  
-   <span data-ttu-id="52f6e-244">인스턴스의 각 도형은 엔드포인트를 제외하고 자체 교차해서는 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="52f6e-244">Each figure of the instance must not intersect itself, except at its endpoints.</span></span>  
  
-   <span data-ttu-id="52f6e-245">인스턴스의 도형 두 개가 양쪽의 경계가 아닌 점에서는 서로 교차하지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="52f6e-245">No two figures of the instance can intersect each other at a point that is not in both of their boundaries.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="52f6e-246">비어 있는 기하 도형은 항상 단순합니다.</span><span class="sxs-lookup"><span data-stu-id="52f6e-246">Empty geometries are always simple.</span></span>  
  
 <span data-ttu-id="52f6e-247">**인스턴스가 단순한지 확인하려면**</span><span class="sxs-lookup"><span data-stu-id="52f6e-247">**To determine if an instance is simple**</span></span>  
 <span data-ttu-id="52f6e-248">[STIsEmpty](/sql/t-sql/spatial-geometry/stissimple-geometry-data-type).</span><span class="sxs-lookup"><span data-stu-id="52f6e-248">[STIsSimple](/sql/t-sql/spatial-geometry/stissimple-geometry-data-type).</span></span>  
  
  
  
###  <a name="boundary-interior-and-exterior"></a><a name="boundary"></a> <span data-ttu-id="52f6e-249">경계, 내부 및 외부</span><span class="sxs-lookup"><span data-stu-id="52f6e-249">Boundary, Interior, and Exterior</span></span>  
 <span data-ttu-id="52f6e-250">인스턴스의 *내부* 는 `geometry` 인스턴스가 차지 하는 공간이 고 *외부* 는 해당 인스턴스가 차지 하지 않는 공간입니다.</span><span class="sxs-lookup"><span data-stu-id="52f6e-250">The *interior* of a `geometry` instance is the space occupied by the instance, and the *exterior* is the space not occupied it.</span></span>  
  
 <span data-ttu-id="52f6e-251">*경계* 는 다음과 같이 OGC에 의해 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="52f6e-251">*Boundary* is defined by the OGC as follows:</span></span>  
  
-   <span data-ttu-id="52f6e-252">`Point` 및 `MultiPoint` 인스턴스에는 경계가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="52f6e-252">`Point` and `MultiPoint` instances do not have a boundary.</span></span>  
  
-   <span data-ttu-id="52f6e-253">`LineString` 및 `MultiLineString` 경계는 시작점과 끝점으로 구성되며 짝수 횟수에 발생하는 시작점과 끝점은 제거됩니다.</span><span class="sxs-lookup"><span data-stu-id="52f6e-253">`LineString` and `MultiLineString` boundaries are formed by the start points and end points, removing those that occur an even number of times.</span></span>  
  
```  
DECLARE @g geometry;  
SET @g = geometry::Parse('MULTILINESTRING((0 1, 0 0, 1 0, 0 1), (1 1, 1 0))');  
SELECT @g.STBoundary().ToString();  
```  
  
 <span data-ttu-id="52f6e-254">`Polygon` 또는 `MultiPolygon` 인스턴스의 경계는 해당 인스턴스 링의 집합입니다.</span><span class="sxs-lookup"><span data-stu-id="52f6e-254">The boundary of a `Polygon` or `MultiPolygon` instance is the set of its rings.</span></span>  
  
```  
DECLARE @g geometry;  
SET @g = geometry::Parse('POLYGON((0 0, 3 0, 3 3, 0 3, 0 0), (1 1, 1 2, 2 2, 2 1, 1 1))');  
SELECT @g.STBoundary().ToString();  
```  
  
 <span data-ttu-id="52f6e-255">**인스턴스의 경계를 반환하려면**</span><span class="sxs-lookup"><span data-stu-id="52f6e-255">**To return the boundary of an instance**</span></span>  
 [<span data-ttu-id="52f6e-256">STBoundary</span><span class="sxs-lookup"><span data-stu-id="52f6e-256">STBoundary</span></span>](/sql/t-sql/spatial-geometry/stboundary-geometry-data-type)  
  
  
  
###  <a name="envelope"></a><a name="envelope"></a> <span data-ttu-id="52f6e-257">봉투</span><span class="sxs-lookup"><span data-stu-id="52f6e-257">Envelope</span></span>  
 <span data-ttu-id="52f6e-258">*envelope* `geometry` *경계 상자*라고도 하는 인스턴스의 봉투 (envelope)는 인스턴스의 최소 및 최대 (X, Y) 좌표로 구성 되는 축에 맞춰진 사각형입니다.</span><span class="sxs-lookup"><span data-stu-id="52f6e-258">The *envelope* of a `geometry` instance, also known as the *bounding box*, is the axis-aligned rectangle formed by the minimum and maximum (X,Y) coordinates of the instance.</span></span>  
  
 <span data-ttu-id="52f6e-259">**인스턴스의 봉투를 반환하려면**</span><span class="sxs-lookup"><span data-stu-id="52f6e-259">**To return the envelope of an instance**</span></span>  
 [<span data-ttu-id="52f6e-260">STEnvelope</span><span class="sxs-lookup"><span data-stu-id="52f6e-260">STEnvelope</span></span>](/sql/t-sql/spatial-geometry/stenvelope-geometry-data-type)  
  
  
  
###  <a name="closure"></a><a name="closure"></a> <span data-ttu-id="52f6e-261">닫힘</span><span class="sxs-lookup"><span data-stu-id="52f6e-261">Closure</span></span>  
 <span data-ttu-id="52f6e-262">*폐쇄형* `geometry` 인스턴스는 시작점과 끝점이 같은 도형입니다.</span><span class="sxs-lookup"><span data-stu-id="52f6e-262">A *closed*`geometry` instance is a figure whose start points and end points are the same.</span></span> <span data-ttu-id="52f6e-263">`Polygon` 인스턴스는 닫혀 있다고 간주되며,</span><span class="sxs-lookup"><span data-stu-id="52f6e-263">`Polygon` instances are considered closed.</span></span> <span data-ttu-id="52f6e-264">`Point` 인스턴스는 닫혀 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="52f6e-264">`Point` instances are not closed.</span></span>  
  
 <span data-ttu-id="52f6e-265">링은 단순하고 닫혀 있는 `LineString` 인스턴스입니다.</span><span class="sxs-lookup"><span data-stu-id="52f6e-265">A ring is a simple, closed `LineString` instance.</span></span>  
  
 <span data-ttu-id="52f6e-266">**인스턴스가 닫혀 있는지 확인하려면**</span><span class="sxs-lookup"><span data-stu-id="52f6e-266">**To determine if an instance is closed**</span></span>  
 [<span data-ttu-id="52f6e-267">STIsClosed</span><span class="sxs-lookup"><span data-stu-id="52f6e-267">STIsClosed</span></span>](/sql/t-sql/spatial-geometry/stisclosed-geometry-data-type)  
  
 <span data-ttu-id="52f6e-268">**인스턴스가 링인지 확인하려면**</span><span class="sxs-lookup"><span data-stu-id="52f6e-268">**To determine if an instance is a ring**</span></span>  
 [<span data-ttu-id="52f6e-269">STIsRing</span><span class="sxs-lookup"><span data-stu-id="52f6e-269">STIsRing</span></span>](/sql/t-sql/spatial-geometry/stisring-geometry-data-type)  
  
 <span data-ttu-id="52f6e-270">**Polygon 인스턴스의 외부 링을 반환하려면**</span><span class="sxs-lookup"><span data-stu-id="52f6e-270">**To return the exterior ring of a Polygon instance**</span></span>  
 [<span data-ttu-id="52f6e-271">STExteriorRing</span><span class="sxs-lookup"><span data-stu-id="52f6e-271">STExteriorRing</span></span>](/sql/t-sql/spatial-geometry/stexteriorring-geometry-data-type)  
  
 <span data-ttu-id="52f6e-272">**Polygon에 있는 내부 링의 개수를 반환하려면**</span><span class="sxs-lookup"><span data-stu-id="52f6e-272">**To return the number of interior rings in a Polygon**</span></span>  
 [<span data-ttu-id="52f6e-273">STNumInteriorRing</span><span class="sxs-lookup"><span data-stu-id="52f6e-273">STNumInteriorRing</span></span>](/sql/t-sql/spatial-geometry/stnuminteriorring-geometry-data-type)  
  
 <span data-ttu-id="52f6e-274">**Polygon에 지정된 내부 링을 반환하려면**</span><span class="sxs-lookup"><span data-stu-id="52f6e-274">**To return a specified interior ring of a Polygon**</span></span>  
 [<span data-ttu-id="52f6e-275">STInteriorRingN</span><span class="sxs-lookup"><span data-stu-id="52f6e-275">STInteriorRingN</span></span>](/sql/t-sql/spatial-geometry/stinteriorringn-geometry-data-type)  
  
  
  
###  <a name="spatial-reference-id-srid"></a><a name="srid"></a> <span data-ttu-id="52f6e-276">SRID(Spatial Reference ID)</span><span class="sxs-lookup"><span data-stu-id="52f6e-276">Spatial Reference ID (SRID)</span></span>  
 <span data-ttu-id="52f6e-277">SRID는 `geometry` 인스턴스를 나타내는 좌표계를 지정하는 식별자입니다.</span><span class="sxs-lookup"><span data-stu-id="52f6e-277">The spatial reference ID (SRID) is an identifier specifying which coordinate system the `geometry` instance is represented in.</span></span> <span data-ttu-id="52f6e-278">다른 SRID를 사용하는 두 인스턴스는 서로 비교할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="52f6e-278">Two instances with different SRIDs are incomparable.</span></span>  
  
 <span data-ttu-id="52f6e-279">**인스턴스의 SRID를 설정하거나 반환하려면**</span><span class="sxs-lookup"><span data-stu-id="52f6e-279">**To set or return the SRID of an instance**</span></span>  
 [<span data-ttu-id="52f6e-280">STSrid</span><span class="sxs-lookup"><span data-stu-id="52f6e-280">STSrid</span></span>](/sql/t-sql/spatial-geometry/stsrid-geometry-data-type)  
  
 <span data-ttu-id="52f6e-281">이 속성은 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52f6e-281">This property can be modified.</span></span>  
  
  
  
##  <a name="determining-relationships-between-geometry-instances"></a><a name="rel"></a> <span data-ttu-id="52f6e-282">geometry 인스턴스 간 관계 확인</span><span class="sxs-lookup"><span data-stu-id="52f6e-282">Determining Relationships between geometry Instances</span></span>  
 <span data-ttu-id="52f6e-283">`geometry` 데이터 형식은 수많은 기본 메서드를 제공합니다. 이러한 메서드를 사용하여 두 개의 `geometry` 인스턴스 간 관계를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52f6e-283">The `geometry` data type provides many built-in methods you can use to determine relationships between two `geometry` instances.</span></span>  
  
 <span data-ttu-id="52f6e-284">**두 인스턴스가 동일한 점 집합으로 구성되었는지 확인하려면**</span><span class="sxs-lookup"><span data-stu-id="52f6e-284">**To determine if two instances comprise the same point set**</span></span>  
 [<span data-ttu-id="52f6e-285">STEquals</span><span class="sxs-lookup"><span data-stu-id="52f6e-285">STEquals</span></span>](/sql/t-sql/spatial-geometry/stequals-geometry-data-type)  
  
 <span data-ttu-id="52f6e-286">**두 인스턴스가 결합되지 않았는지 확인하려면**</span><span class="sxs-lookup"><span data-stu-id="52f6e-286">**To determine if two instances are disjoint**</span></span>  
 [<span data-ttu-id="52f6e-287">STDisjoint</span><span class="sxs-lookup"><span data-stu-id="52f6e-287">STDisjoint</span></span>](/sql/t-sql/spatial-geometry/stdisjoint-geometry-data-type)  
  
 <span data-ttu-id="52f6e-288">**두 인스턴스가 교차하는지 확인하려면**</span><span class="sxs-lookup"><span data-stu-id="52f6e-288">**To determine if two instances intersect**</span></span>  
 [<span data-ttu-id="52f6e-289">STIntersects</span><span class="sxs-lookup"><span data-stu-id="52f6e-289">STIntersects</span></span>](/sql/t-sql/spatial-geometry/stintersects-geometry-data-type)  
  
 <span data-ttu-id="52f6e-290">**두 인스턴스가 액세스하는지 확인하려면**</span><span class="sxs-lookup"><span data-stu-id="52f6e-290">**To determine if two instances touch**</span></span>  
 [<span data-ttu-id="52f6e-291">STTouches</span><span class="sxs-lookup"><span data-stu-id="52f6e-291">STTouches</span></span>](/sql/t-sql/spatial-geometry/sttouches-geometry-data-type)  
  
 <span data-ttu-id="52f6e-292">**두 인스턴스가 겹치는지 확인하려면**</span><span class="sxs-lookup"><span data-stu-id="52f6e-292">**To determine if two instances overlap**</span></span>  
 [<span data-ttu-id="52f6e-293">STOverlaps</span><span class="sxs-lookup"><span data-stu-id="52f6e-293">STOverlaps</span></span>](/sql/t-sql/spatial-geometry/stoverlaps-geometry-data-type)  
  
 <span data-ttu-id="52f6e-294">**두 인스턴스가 상호 교차하는지 확인하려면**</span><span class="sxs-lookup"><span data-stu-id="52f6e-294">**To determine if two instances cross**</span></span>  
 [<span data-ttu-id="52f6e-295">STCrosses</span><span class="sxs-lookup"><span data-stu-id="52f6e-295">STCrosses</span></span>](/sql/t-sql/spatial-geometry/stcrosses-geometry-data-type)  
  
 <span data-ttu-id="52f6e-296">**한 인스턴스가 다른 인스턴스 내에 있는지 확인하려면**</span><span class="sxs-lookup"><span data-stu-id="52f6e-296">**To determine if one instance is within another**</span></span>  
 [<span data-ttu-id="52f6e-297">STWithin</span><span class="sxs-lookup"><span data-stu-id="52f6e-297">STWithin</span></span>](/sql/t-sql/spatial-geometry/stwithin-geometry-data-type)  
  
 <span data-ttu-id="52f6e-298">**한 인스턴스에 다른 인스턴스가 있는지 확인하려면**</span><span class="sxs-lookup"><span data-stu-id="52f6e-298">**To determine if one instance contains another**</span></span>  
 [<span data-ttu-id="52f6e-299">STContains</span><span class="sxs-lookup"><span data-stu-id="52f6e-299">STContains</span></span>](/sql/t-sql/spatial-geometry/stcontains-geometry-data-type)  
  
 <span data-ttu-id="52f6e-300">**한 인스턴스가 다른 인스턴스를 겹치는지 확인하려면**</span><span class="sxs-lookup"><span data-stu-id="52f6e-300">**To determine if one instance overlaps another**</span></span>  
 [<span data-ttu-id="52f6e-301">STOverlaps</span><span class="sxs-lookup"><span data-stu-id="52f6e-301">STOverlaps</span></span>](/sql/t-sql/spatial-geometry/stoverlaps-geometry-data-type)  
  
 <span data-ttu-id="52f6e-302">**두 인스턴스가 공간적으로 관련되어 있는지 확인하려면**</span><span class="sxs-lookup"><span data-stu-id="52f6e-302">**To determine if two instances are spatially related**</span></span>  
 [<span data-ttu-id="52f6e-303">STRelate</span><span class="sxs-lookup"><span data-stu-id="52f6e-303">STRelate</span></span>](/sql/t-sql/spatial-geometry/strelate-geometry-data-type)  
  
 <span data-ttu-id="52f6e-304">**두 geometry의 점 간 최단 길이를 확인하려면**</span><span class="sxs-lookup"><span data-stu-id="52f6e-304">**To determine the shortest distance between points in two geometries**</span></span>  
 [<span data-ttu-id="52f6e-305">STDistance</span><span class="sxs-lookup"><span data-stu-id="52f6e-305">STDistance</span></span>](/sql/t-sql/spatial-geometry/stdistance-geometry-data-type)  
  
  
  
##  <a name="geometry-instances-default-to-zero-srid"></a><a name="defaultsrid"></a> <span data-ttu-id="52f6e-306">geometry 인스턴스의 기본값을 SRID 0으로 설정</span><span class="sxs-lookup"><span data-stu-id="52f6e-306">geometry Instances Default to Zero SRID</span></span>  
 <span data-ttu-id="52f6e-307">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 `geometry` 인스턴스의 기본 SRID는 0입니다.</span><span class="sxs-lookup"><span data-stu-id="52f6e-307">The default SRID for `geometry` instances in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is 0.</span></span> <span data-ttu-id="52f6e-308">`geometry` 공간 데이터를 사용하면 계산을 수행하는 데 공간 인스턴스의 특정 SRID가 필요하지 않으므로 인스턴스가 정의되지 않은 평면 공간에 존재할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52f6e-308">With `geometry` spatial data, the specific SRID of the spatial instance is not required to perform calculations; thus, instances can reside in undefined planar space.</span></span> <span data-ttu-id="52f6e-309">`geometry` 데이터 형식 메서드의 계산에서 정의되지 않은 평면 공간을 나타내려면 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]에서는 SRID 0을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="52f6e-309">To indicate undefined planar space in the calculations of `geometry` data type methods, the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] uses SRID 0.</span></span>  
  
##  <a name="examples"></a><a name="examples"></a> <span data-ttu-id="52f6e-310">예</span><span class="sxs-lookup"><span data-stu-id="52f6e-310">Examples</span></span>  
 <span data-ttu-id="52f6e-311">다음 두 예에서는 geometry 데이터를 추가하고 쿼리하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="52f6e-311">The following two examples show how to add and query geometry data.</span></span>  
  
-   <span data-ttu-id="52f6e-312">첫 번째 예에서는 ID 열과 `geometry` 열 `GeomCol1`이 있는 테이블을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="52f6e-312">The first example creates a table with an identity column and a `geometry` column `GeomCol1`.</span></span> <span data-ttu-id="52f6e-313">세 번째 열에서는 `geometry` 열을 OGC(Open Geospatial Consortium) WKT(Well-Known Text) 표현으로 렌더링하고 `STAsText()` 메서드를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="52f6e-313">A third column renders the `geometry` column into its Open Geospatial Consortium (OGC) Well-Known Text (WKT) representation, and uses the `STAsText()` method.</span></span> <span data-ttu-id="52f6e-314">그러고 나면 두 개의 행이 삽입됩니다. 이 중 한 행에는 `LineString` 의 `geometry`인스턴스가 들어 있고, 다른 행에는 `Polygon` 인스턴스가 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52f6e-314">Two rows are then inserted: one row contains a `LineString` instance of `geometry`, and one row contains a `Polygon` instance.</span></span>  
  
    ```  
    IF OBJECT_ID ( 'dbo.SpatialTable', 'U' ) IS NOT NULL   
        DROP TABLE dbo.SpatialTable;  
    GO  
  
    CREATE TABLE SpatialTable   
        ( id int IDENTITY (1,1),  
        GeomCol1 geometry,   
        GeomCol2 AS GeomCol1.STAsText() );  
    GO  
  
    INSERT INTO SpatialTable (GeomCol1)  
    VALUES (geometry::STGeomFromText('LINESTRING (100 100, 20 180, 180 180)', 0));  
  
    INSERT INTO SpatialTable (GeomCol1)  
    VALUES (geometry::STGeomFromText('POLYGON ((0 0, 150 0, 150 150, 0 150, 0 0))', 0));  
    GO  
    ```  
  
-   <span data-ttu-id="52f6e-315">두 번째 예에서는 `STIntersection()` 메서드를 사용하여 앞서 삽입한 두 `geometry` 인스턴스가 교차하는 지점을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="52f6e-315">The second example uses the `STIntersection()` method to return the points where the two previously inserted `geometry` instances intersect.</span></span>  
  
    ```  
    DECLARE @geom1 geometry;  
    DECLARE @geom2 geometry;  
    DECLARE @result geometry;  
  
    SELECT @geom1 = GeomCol1 FROM SpatialTable WHERE id = 1;  
    SELECT @geom2 = GeomCol1 FROM SpatialTable WHERE id = 2;  
    SELECT @result = @geom1.STIntersection(@geom2);  
    SELECT @result.STAsText();  
    ```  
  
  
  
## <a name="see-also"></a><span data-ttu-id="52f6e-316">참고 항목</span><span class="sxs-lookup"><span data-stu-id="52f6e-316">See Also</span></span>  
 [<span data-ttu-id="52f6e-317">공간 데이터&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="52f6e-317">Spatial Data &#40;SQL Server&#41;</span></span>](spatial-data-sql-server.md)  
  
  
