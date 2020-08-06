---
title: geography 인스턴스 만들기, 구성 및 쿼리 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- geography data type [SQL Server]
- geodetic data type [SQL Server]
- geography data type [SQL Server], about geography data type
ms.assetid: b585851e-d15b-411f-adeb-aeabeb777c0b
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: d744457cc517a6172cca96b27eae1f456deca24e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646856"
---
# <a name="create-construct-and-query-geography-instances"></a><span data-ttu-id="59fbb-102">geography 인스턴스 만들기, 구성 및 쿼리</span><span class="sxs-lookup"><span data-stu-id="59fbb-102">Create, Construct, and Query geography Instances</span></span>
  <span data-ttu-id="59fbb-103">지리 공간 데이터 형식인 `geography`는 둥근 표면 좌표계로 데이터를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="59fbb-103">The geography spatial data type, `geography`, represents data in a round-earth coordinate system.</span></span> <span data-ttu-id="59fbb-104">이 형식은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 .NET CLR(공용 언어 런타임) 데이터 형식으로 구현됩니다.</span><span class="sxs-lookup"><span data-stu-id="59fbb-104">This type is implemented as a .NET common language runtime (CLR) data type in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="59fbb-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `geography` 데이터 형식은 GPS 위도 및 경도 좌표와 같은 타원(둥근 표면) 데이터를 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="59fbb-105">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `geography` data type stores ellipsoidal (round-earth) data, such as GPS latitude and longitude coordinates.</span></span>  
  
 <span data-ttu-id="59fbb-106">`geography` 형식은 각 데이터베이스에서 미리 정의되고 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="59fbb-106">The `geography` type is predefined and available in each database.</span></span> <span data-ttu-id="59fbb-107">다른 시스템 제공 형식을 사용할 때와 동일한 방식으로 `geography` 형식의 테이블 열을 만들고 `geography` 데이터에 대한 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="59fbb-107">You can create table columns of type `geography` and operate on `geography` data in the same manner as you would use other system-supplied types.</span></span>  
  
##  <a name="creating-or-constructing-a-new-geography-instance"></a><a name="creating"></a> <span data-ttu-id="59fbb-108">새 지리 인스턴스 만들기 또는 구성</span><span class="sxs-lookup"><span data-stu-id="59fbb-108">Creating or constructing a new geography instance</span></span>  
  
###  <a name="creating-a-new-geography-instance-from-an-existing-instance"></a><a name="existing"></a> <span data-ttu-id="59fbb-109">기존 인스턴스에서 새 지리 인스턴스 만들기</span><span class="sxs-lookup"><span data-stu-id="59fbb-109">Creating a New geography Instance from an Existing Instance</span></span>  
 <span data-ttu-id="59fbb-110">`geography` 데이터 형식은 수많은 기본 메서드를 제공합니다. 이러한 메서드를 사용하여 기존 인스턴스에 기반하여 새 `geography` 인스턴스를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="59fbb-110">The `geography` data type provides numerous built-in methods you can use to create new `geography` instances based on existing instances.</span></span>  
  
 <span data-ttu-id="59fbb-111">**지리의 버퍼를 만들려면**</span><span class="sxs-lookup"><span data-stu-id="59fbb-111">**To create a buffer around a geography**</span></span>  
 [<span data-ttu-id="59fbb-112">STBuffer&#40;geography 데이터 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="59fbb-112">STBuffer &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/stbuffer-geography-data-type)  
  
 <span data-ttu-id="59fbb-113">**허용 오차를 허용하는 지리의 버퍼를 만들려면**</span><span class="sxs-lookup"><span data-stu-id="59fbb-113">**To create a buffer around a geography, allowing for a tolerance**</span></span>  
 [<span data-ttu-id="59fbb-114">BufferWithTolerance&#40;geography 데이터 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="59fbb-114">BufferWithTolerance &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/bufferwithtolerance-geography-data-type)  
  
 <span data-ttu-id="59fbb-115">**두 geography 인스턴스의 교집합에서 지리를 만들려면**</span><span class="sxs-lookup"><span data-stu-id="59fbb-115">**To create a geography from the intersection of two geography instances**</span></span>  
 [<span data-ttu-id="59fbb-116">STIntersection&#40;geography 데이터 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="59fbb-116">STIntersection &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/stintersection-geography-data-type)  
  
 <span data-ttu-id="59fbb-117">**두 geography 인스턴스의 합집합에서 지리를 만들려면**</span><span class="sxs-lookup"><span data-stu-id="59fbb-117">**To create a geography from the union of two geography instances**</span></span>  
 [<span data-ttu-id="59fbb-118">STUnion&#40;geography 데이터 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="59fbb-118">STUnion &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/stunion-geography-data-type)  
  
 <span data-ttu-id="59fbb-119">**한 지리가 다른 지리와 겹치지 않는 점에서 지리를 만들려면**</span><span class="sxs-lookup"><span data-stu-id="59fbb-119">**To create a geography from the points where one geography does not overlap another**</span></span>  
 [<span data-ttu-id="59fbb-120">STDifference&#40;geography 데이터 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="59fbb-120">STDifference &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/stdifference-geography-data-type)  
  
###  <a name="constructing-a-geography-instance-from-well-known-text-input"></a><a name="wkt"></a> <span data-ttu-id="59fbb-121">WKT 입력으로부터 지리 인스턴스 구성</span><span class="sxs-lookup"><span data-stu-id="59fbb-121">Constructing a geography Instance from Well-Known Text Input</span></span>  
 <span data-ttu-id="59fbb-122">`geography` 데이터 형식은 OGC(Open Geospatial Consortium) WKT 표현에서 지리를 생성하는 여러 가지 기본 메서드를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="59fbb-122">The `geography` data type provides several built-in methods that generate a geography from the Open Geospatial Consortium (OGC) WKT representation.</span></span> <span data-ttu-id="59fbb-123">WKT 표준은 지리 데이터를 텍스트 형식으로 교환할 수 있는 텍스트 문자열입니다.</span><span class="sxs-lookup"><span data-stu-id="59fbb-123">The WKT standard is a text string that allows geography data to be exchanged in textual form.</span></span>  
  
 <span data-ttu-id="59fbb-124">**WKT 입력으로부터 지리 인스턴스 유형을 구성하려면**</span><span class="sxs-lookup"><span data-stu-id="59fbb-124">**To construct any type of geography instance from WKT input**</span></span>  
 [<span data-ttu-id="59fbb-125">STGeomFromText&#40;geography 데이터 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="59fbb-125">STGeomFromText &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/stgeomfromtext-geography-data-type)  
  
 [<span data-ttu-id="59fbb-126">Parse&#40;geography 데이터 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="59fbb-126">Parse &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/parse-geography-data-type)  
  
 <span data-ttu-id="59fbb-127">**WKT 입력으로부터 지리 Point 인스턴스를 구성하려면**</span><span class="sxs-lookup"><span data-stu-id="59fbb-127">**To construct a geography Point instance from WKT input**</span></span>  
 [<span data-ttu-id="59fbb-128">STPointFromText&#40;geography 데이터 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="59fbb-128">STPointFromText &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/stpointfromtext-geography-data-type)  
  
 <span data-ttu-id="59fbb-129">**WKT 입력으로부터 지리 MultiPoint 인스턴스를 구성하려면**</span><span class="sxs-lookup"><span data-stu-id="59fbb-129">**To construct a geography MultiPoint instance from WKT input**</span></span>  
 [<span data-ttu-id="59fbb-130">STMPointFromText&#40;geography 데이터 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="59fbb-130">STMPointFromText &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/stmpointfromtext-geography-data-type)  
  
 <span data-ttu-id="59fbb-131">**WKT 입력으로부터 지리 LineString 인스턴스를 구성하려면**</span><span class="sxs-lookup"><span data-stu-id="59fbb-131">**To construct a geography LineString instance from WKT input**</span></span>  
 <span data-ttu-id="59fbb-132">STLineFromText(geography 데이터 형식)</span><span class="sxs-lookup"><span data-stu-id="59fbb-132">STLineFromText (geography Data Type)</span></span>  
  
 <span data-ttu-id="59fbb-133">**WKT 입력으로부터 지리 MultiLineString 인스턴스를 구성하려면**</span><span class="sxs-lookup"><span data-stu-id="59fbb-133">**To construct a geography MultiLineString instance from WKT input**</span></span>  
 [<span data-ttu-id="59fbb-134">STMLineFromText&#40;geography 데이터 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="59fbb-134">STMLineFromText &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/stmlinefromtext-geography-data-type)  
  
 <span data-ttu-id="59fbb-135">**WKT 입력으로부터 지리 Polygon 인스턴스를 구성하려면**</span><span class="sxs-lookup"><span data-stu-id="59fbb-135">**To construct a geography Polygon instance from WKT input**</span></span>  
 [<span data-ttu-id="59fbb-136">STPolyFromText&#40;geography 데이터 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="59fbb-136">STPolyFromText &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/stpolyfromtext-geography-data-type)  
  
 <span data-ttu-id="59fbb-137">**WKT 입력으로부터 지리 MultiPolygon 인스턴스를 구성하려면**</span><span class="sxs-lookup"><span data-stu-id="59fbb-137">**To construct a geography MultiPolygon instance from WKT input**</span></span>  
 [<span data-ttu-id="59fbb-138">STMPolyFromText&#40;geography 데이터 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="59fbb-138">STMPolyFromText &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/stmpolyfromtext-geography-data-type)  
  
 <span data-ttu-id="59fbb-139">**WKT 입력으로부터 지리 GeometryCollection 인스턴스를 구성하려면**</span><span class="sxs-lookup"><span data-stu-id="59fbb-139">**To construct a geography GeometryCollection instance from WKT input**</span></span>  
 [<span data-ttu-id="59fbb-140">STGeomCollFromText&#40;geography 데이터 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="59fbb-140">STGeomCollFromText &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/stgeomcollfromtext-geography-data-type)  
  
###  <a name="constructing-a-geography-instance-from-well-known-binary-input"></a><a name="wkb"></a> <span data-ttu-id="59fbb-141">WKB 입력으로부터 지리 인스턴스 구성</span><span class="sxs-lookup"><span data-stu-id="59fbb-141">Constructing a geography Instance from Well-Known Binary Input</span></span>  
 <span data-ttu-id="59fbb-142">WKB는 클라이언트 애플리케이션과 SQL 데이터베이스 간에 `Geography` 데이터를 교환할 수 있도록 OGC에서 지정하는 이진 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="59fbb-142">WKB is a binary format specified by the OGC that permits `Geography` data to be exchanged between a client application and an SQL database.</span></span> <span data-ttu-id="59fbb-143">다음 함수는 WKB 입력을 사용하여 geography 인스턴스를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="59fbb-143">The following functions accept WKB input to construct geography instances:</span></span>  
  
 <span data-ttu-id="59fbb-144">**WKB 입력으로부터 지리 인스턴스 유형을 구성하려면**</span><span class="sxs-lookup"><span data-stu-id="59fbb-144">**To construct any type of geography instance from WKB input**</span></span>  
 [<span data-ttu-id="59fbb-145">STGeomFromWKB&#40;geography 데이터 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="59fbb-145">STGeomFromWKB &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/stgeomfromwkb-geography-data-type)  
  
 <span data-ttu-id="59fbb-146">**WKB 입력으로부터 지리 Point 인스턴스를 구성하려면**</span><span class="sxs-lookup"><span data-stu-id="59fbb-146">**To construct a geography Point instance from WKB input**</span></span>  
 [<span data-ttu-id="59fbb-147">STPointFromWKB&#40;geography 데이터 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="59fbb-147">STPointFromWKB &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/stpointfromwkb-geography-data-type)  
  
 <span data-ttu-id="59fbb-148">**WKB 입력으로부터 지리 MultiPoint 인스턴스를 구성하려면**</span><span class="sxs-lookup"><span data-stu-id="59fbb-148">**To construct a geography MultiPoint instance from WKB input**</span></span>  
 [<span data-ttu-id="59fbb-149">STMPointFromWKB&#40;geography 데이터 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="59fbb-149">STMPointFromWKB &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/stmpointfromwkb-geography-data-type)  
  
 <span data-ttu-id="59fbb-150">**WKB 입력으로부터 지리 LineString 인스턴스를 구성하려면**</span><span class="sxs-lookup"><span data-stu-id="59fbb-150">**To construct a geography LineString instance from WKB input**</span></span>  
 [<span data-ttu-id="59fbb-151">STLineFromWKB&#40;geography 데이터 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="59fbb-151">STLineFromWKB &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/stlinefromwkb-geography-data-type)  
  
 <span data-ttu-id="59fbb-152">**WKB 입력으로부터 지리 MultiLineString 인스턴스를 구성하려면**</span><span class="sxs-lookup"><span data-stu-id="59fbb-152">**To construct a geography MultiLineString instance from WKB input**</span></span>  
 [<span data-ttu-id="59fbb-153">STMLineFromWKB&#40;geography 데이터 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="59fbb-153">STMLineFromWKB &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/stmlinefromwkb-geography-data-type)  
  
 <span data-ttu-id="59fbb-154">**WKB 입력으로부터 지리 Polygon 인스턴스를 구성하려면**</span><span class="sxs-lookup"><span data-stu-id="59fbb-154">**To construct a geography Polygon instance from WKB input**</span></span>  
 [<span data-ttu-id="59fbb-155">STPolyFromWKB&#40;geography 데이터 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="59fbb-155">STPolyFromWKB &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/stpolyfromwkb-geography-data-type)  
  
 <span data-ttu-id="59fbb-156">**WKB 입력으로부터 지리 MultiPolygon 인스턴스를 구성하려면**</span><span class="sxs-lookup"><span data-stu-id="59fbb-156">**To construct a geography MultiPolygon instance from WKB input**</span></span>  
 [<span data-ttu-id="59fbb-157">STMPolyFromWKB&#40;geography 데이터 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="59fbb-157">STMPolyFromWKB &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/stmpolyfromwkb-geography-data-type)  
  
 <span data-ttu-id="59fbb-158">**WKB 입력으로부터 지리 GeometryCollection 인스턴스를 구성하려면**</span><span class="sxs-lookup"><span data-stu-id="59fbb-158">**To construct a geography GeometryCollection instance from WKB input**</span></span>  
 <span data-ttu-id="59fbb-159">[STGeomCollFromWKB&#40;geography 데이터 형식&#41;](/sql/t-sql/spatial-geography/stgeomcollfromwkb-geography-data-type)STGeomCollFromWKB(geography 데이터 형식)</span><span class="sxs-lookup"><span data-stu-id="59fbb-159">[STGeomCollFromWKB &#40;geography Data Type&#41;](/sql/t-sql/spatial-geography/stgeomcollfromwkb-geography-data-type)STGeomCollFromWKB (geography Data Type)</span></span>  
  
###  <a name="constructing-a-geography-instance-from-gml-text-input"></a><a name="gml"></a> <span data-ttu-id="59fbb-160">GML 텍스트 입력으로부터 지리 인스턴스 구성</span><span class="sxs-lookup"><span data-stu-id="59fbb-160">Constructing a geography Instance from GML Text Input</span></span>  
 <span data-ttu-id="59fbb-161">`geography`데이터 형식은 `geography` 인스턴스의 XML 표현인 GML에서 인스턴스를 생성 하는 메서드를 제공 합니다 `geography` .</span><span class="sxs-lookup"><span data-stu-id="59fbb-161">The `geography` data type provides a method that generates a `geography` instance from GML, an XML representation of a `geography` instance.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="59fbb-162">는 GML 하위 집합을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="59fbb-162">supports a subset of GML.</span></span>  
  
 <span data-ttu-id="59fbb-163">Geography Markup Language에 대한 자세한 내용은 OGC 사양: [OGC 사양, Geography Markup Language](https://go.microsoft.com/fwlink/?LinkId=93629)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="59fbb-163">For more information on Geography Markup Language, see the OGC Specification: [OGC Specifications, Geography Markup Language.](https://go.microsoft.com/fwlink/?LinkId=93629)</span></span>  
  
 <span data-ttu-id="59fbb-164">**GML 입력으로부터 지리 인스턴스 유형을 구성하려면**</span><span class="sxs-lookup"><span data-stu-id="59fbb-164">**To construct any type of geography instance from GML input**</span></span>  
 [<span data-ttu-id="59fbb-165">GeomFromGML&#40;geography 데이터 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="59fbb-165">GeomFromGML &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/geomfromgml-geography-data-type)  
  
##  <a name="returning-well-known-text-and-well-known-binary-from-a-geography-instance"></a><a name="returning"></a> <span data-ttu-id="59fbb-166">지리 인스턴스에서 WKT 및 WKB 반환</span><span class="sxs-lookup"><span data-stu-id="59fbb-166">Returning Well-Known Text and Well-Known Binary from a geography Instance</span></span>  
 <span data-ttu-id="59fbb-167">다음 메서드를 사용하여 `geography` 인스턴스의 WKT 또는 WKB 형식을 반환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="59fbb-167">You can use the following methods to return either the WKT or WKB format of a `geography` instance:</span></span>  
  
 <span data-ttu-id="59fbb-168">**지리 인스턴스의 WKT 표현을 반환하려면**</span><span class="sxs-lookup"><span data-stu-id="59fbb-168">**To return the WKT representation of a geography instance**</span></span>  
 [<span data-ttu-id="59fbb-169">STAsText&#40;geography 데이터 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="59fbb-169">STAsText &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/stastext-geography-data-type)  
  
 [<span data-ttu-id="59fbb-170">ToString&#40;geography 데이터 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="59fbb-170">ToString &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/tostring-geography-data-type)  
  
 <span data-ttu-id="59fbb-171">**Z 및 M 값을 포함하여 지리 인스턴스의 WKT 표현을 반환하려면**</span><span class="sxs-lookup"><span data-stu-id="59fbb-171">**To return the WKT representation of a geography instance including any Z and M values**</span></span>  
 [<span data-ttu-id="59fbb-172">AsTextZM&#40;geography 데이터 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="59fbb-172">AsTextZM &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/astextzm-geography-data-type)  
  
 <span data-ttu-id="59fbb-173">**지리 인스턴스의 WKB 표현을 반환하려면**</span><span class="sxs-lookup"><span data-stu-id="59fbb-173">**To return the WKB representation of a geography instance**</span></span>  
 [<span data-ttu-id="59fbb-174">STAsBinary&#40;geography 데이터 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="59fbb-174">STAsBinary &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/stasbinary-geography-data-type)  
  
 <span data-ttu-id="59fbb-175">**지리 인스턴스의 GML 표현을 반환하려면**</span><span class="sxs-lookup"><span data-stu-id="59fbb-175">**To return a GML representation of a geography instance**</span></span>  
 [<span data-ttu-id="59fbb-176">AsGml&#40;geography 데이터 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="59fbb-176">AsGml &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/asgml-geography-data-type)  
  
##  <a name="querying-the-properties-and-behaviors-of-geography-instances"></a><a name="query"></a> <span data-ttu-id="59fbb-177">지리 인스턴스의 속성 및 동작 쿼리</span><span class="sxs-lookup"><span data-stu-id="59fbb-177">Querying the Properties and Behaviors of geography Instances</span></span>  
 <span data-ttu-id="59fbb-178">모든 `geography` 인스턴스에는에서 제공 하는 메서드를 통해 검색할 수 있는 여러 속성이 있습니다 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="59fbb-178">All `geography` instances have a number of properties that can be retrieved through methods that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provides.</span></span> <span data-ttu-id="59fbb-179">다음 항목에서는 geography 형식의 속성과 동작 및 각각을 쿼리하는 메서드를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="59fbb-179">The following topics define the properties and behaviors of geography types, and the methods for querying each one.</span></span>  
  
###  <a name="validity-instance-type-and-geometrycollection-information"></a><a name="valid"></a> <span data-ttu-id="59fbb-180">유효성, 인스턴스 유형 및 GeometryCollection 정보</span><span class="sxs-lookup"><span data-stu-id="59fbb-180">Validity, Instance Type, and GeometryCollection Information</span></span>  
 <span data-ttu-id="59fbb-181">`geography` 인스턴스를 구성한 후 다음과 같은 방법으로 인스턴스 유형을 반환할 수 있습니다. `GeometryCollection` 인스턴스인 경우 특정 `geography` 인스턴스를 반환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="59fbb-181">After a `geography` instance is constructed, you can use the following methods to return the instance type, or if it is a `GeometryCollection` instance, return a specific `geography` instance.</span></span>  
  
 <span data-ttu-id="59fbb-182">**geography 인스턴스 유형을 반환하려면**</span><span class="sxs-lookup"><span data-stu-id="59fbb-182">**To return the instance type of a geography**</span></span>  
 [<span data-ttu-id="59fbb-183">STGeometryType&#40;geography 데이터 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="59fbb-183">STGeometryType &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/stgeometrytype-geography-data-type)  
  
 <span data-ttu-id="59fbb-184">**지리가 지정된 인스턴스 유형인지 확인하려면**</span><span class="sxs-lookup"><span data-stu-id="59fbb-184">**To determine if a geography is a given instance type**</span></span>  
 [<span data-ttu-id="59fbb-185">InstanceOf&#40;geography 데이터 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="59fbb-185">InstanceOf &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/instanceof-geography-data-type)  
  
 <span data-ttu-id="59fbb-186">**geography 인스턴스가 해당 인스턴스 유형에 대해 형식이 올바른지 확인하려면**</span><span class="sxs-lookup"><span data-stu-id="59fbb-186">**To determine if a geography instance is well-formed for its instance type**</span></span>  
 [<span data-ttu-id="59fbb-187">STNumGeometries&#40;geography 데이터 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="59fbb-187">STNumGeometries &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/stnumgeometries-geography-data-type)  
  
 <span data-ttu-id="59fbb-188">**GeometryCollection 인스턴스에서 특정 지리를 반환하려면**</span><span class="sxs-lookup"><span data-stu-id="59fbb-188">**To return a specific geography in a GeometryCollection instance**</span></span>  
 <span data-ttu-id="59fbb-189">[STGeometryN&#40;geography 데이터 형식&#41;](/sql/t-sql/spatial-geography/stgeometryn-geography-data-type)STGeometryN(geography 데이터 형식)</span><span class="sxs-lookup"><span data-stu-id="59fbb-189">[STGeometryN &#40;geography Data Type&#41;](/sql/t-sql/spatial-geography/stgeometryn-geography-data-type)STGeometryN (geography Data Type)</span></span>  
  
###  <a name="number-of-points"></a><a name="number"></a> <span data-ttu-id="59fbb-190">점 수</span><span class="sxs-lookup"><span data-stu-id="59fbb-190">Number of Points</span></span>  
 <span data-ttu-id="59fbb-191">비어 있지 `geography` 않은 모든 인스턴스는 *점으로*구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="59fbb-191">All nonempty `geography` instances are comprised of *points*.</span></span> <span data-ttu-id="59fbb-192">이러한 점은 `geography` 인스턴스가 그려지는 지구의 위도 및 경도 좌표를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="59fbb-192">These points represent the latitude and longitude coordinates of the earth on which the `geography` instances are drawn.</span></span> <span data-ttu-id="59fbb-193">`geography` 데이터 형식은 인스턴스의 점을 쿼리하는 데 필요한 수많은 기본 메서드를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="59fbb-193">The data type `geography` provides numerous built-in methods for querying the points of an instance.</span></span>  
  
 <span data-ttu-id="59fbb-194">**인스턴스를 구성하는 점 개수를 반환하려면**</span><span class="sxs-lookup"><span data-stu-id="59fbb-194">**To return the number of points that comprise an instance**</span></span>  
 [<span data-ttu-id="59fbb-195">STNumPoints&#40;geography 데이터 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="59fbb-195">STNumPoints &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/stnumpoints-geography-data-type)  
  
 <span data-ttu-id="59fbb-196">**인스턴스의 특정 점을 반환하려면**</span><span class="sxs-lookup"><span data-stu-id="59fbb-196">**To return a specific point in an instance**</span></span>  
 [<span data-ttu-id="59fbb-197">STPointN&#40;geometry 데이터 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="59fbb-197">STPointN &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/stpointn-geometry-data-type)  
  
 <span data-ttu-id="59fbb-198">**인스턴스의 시작점을 반환하려면**</span><span class="sxs-lookup"><span data-stu-id="59fbb-198">**To return the start point of an instance**</span></span>  
 [<span data-ttu-id="59fbb-199">STStartPoint&#40;geography 데이터 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="59fbb-199">STStartPoint &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/ststartpoint-geography-data-type)  
  
 <span data-ttu-id="59fbb-200">**인스턴스의 끝점을 반환하려면**</span><span class="sxs-lookup"><span data-stu-id="59fbb-200">**To return the end point of an instance**</span></span>  
 [<span data-ttu-id="59fbb-201">STEndpoint&#40;geography 데이터 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="59fbb-201">STEndpoint &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/stendpoint-geography-data-type)  
  
###  <a name="dimension"></a><a name="dimension"></a> <span data-ttu-id="59fbb-202">차원</span><span class="sxs-lookup"><span data-stu-id="59fbb-202">Dimension</span></span>  
 <span data-ttu-id="59fbb-203">비어 있지 않은 `geography` 인스턴스는 0, 1 또는 2차원이 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="59fbb-203">A nonempty `geography` instance can be 0-, 1-, or 2-dimensional.</span></span> <span data-ttu-id="59fbb-204">`geography`및와 같은 0 차원 인스턴스 `Point` `MultiPoint` 는 길이 또는 영역이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="59fbb-204">Zero-dimensional `geography` instances, such as `Point` and `MultiPoint`, have no length or area.</span></span> <span data-ttu-id="59fbb-205">`LineString, CircularString`, `CompoundCurve` 및 `MultiLineString`과 같은 1차원 개체에는 길이가 있고,</span><span class="sxs-lookup"><span data-stu-id="59fbb-205">One-dimensional objects, such as `LineString, CircularString`, `CompoundCurve`, and `MultiLineString`, have length.</span></span> <span data-ttu-id="59fbb-206">`Polygon, CurvePolygon` 및 `MultiPolygon`과 같은 2차원 인스턴스에는 영역과 길이가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="59fbb-206">Two-dimensional instances, such as `Polygon, CurvePolygon`, and `MultiPolygon`, have area and length.</span></span> <span data-ttu-id="59fbb-207">비어 있는 인스턴스에서는 -1차원을 보고하고 `GeometryCollection`에서는 해당 내용의 최대 차원을 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="59fbb-207">Empty instances report a dimension of -1, and a `GeometryCollection` reports the maximum dimension of its contents.</span></span>  
  
 <span data-ttu-id="59fbb-208">**인스턴스의 차원을 반환하려면**</span><span class="sxs-lookup"><span data-stu-id="59fbb-208">**To return the dimension of an instance**</span></span>  
 [<span data-ttu-id="59fbb-209">STDimension&#40;geography 데이터 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="59fbb-209">STDimension &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/stdimension-geography-data-type)  
  
 <span data-ttu-id="59fbb-210">**인스턴스의 길이를 반환하려면**</span><span class="sxs-lookup"><span data-stu-id="59fbb-210">**To return the length of an instance**</span></span>  
 [<span data-ttu-id="59fbb-211">STLength&#40;geography 데이터 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="59fbb-211">STLength &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/stlength-geography-data-type)  
  
 <span data-ttu-id="59fbb-212">**인스턴스의 영역을 반환하려면**</span><span class="sxs-lookup"><span data-stu-id="59fbb-212">**To return the area of an instance**</span></span>  
 [<span data-ttu-id="59fbb-213">STArea&#40;geography 데이터 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="59fbb-213">STArea &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/starea-geography-data-type)  
  
###  <a name="empty"></a><a name="empty"></a> <span data-ttu-id="59fbb-214">비어 있음</span><span class="sxs-lookup"><span data-stu-id="59fbb-214">Empty</span></span>  
 <span data-ttu-id="59fbb-215">*빈* `geography` 인스턴스에는 점이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="59fbb-215">An *empty*`geography` instance does not have any points.</span></span> <span data-ttu-id="59fbb-216">비어 있는 `LineString, CircularString`, `CompoundCurve` 및 `MultiLineString` 인스턴스의 길이는 0입니다.</span><span class="sxs-lookup"><span data-stu-id="59fbb-216">The length of empty `LineString, CircularString`, `CompoundCurve`, and `MultiLineString` instances is 0.</span></span> <span data-ttu-id="59fbb-217">비어 있는 `Polygon, CurvePolygon` 및 `MultiPolygon` 인스턴스의 영역은 0입니다.</span><span class="sxs-lookup"><span data-stu-id="59fbb-217">The area of empty `Polygon, CurvePolygon` and `MultiPolygon` instances is 0.</span></span>  
  
 <span data-ttu-id="59fbb-218">**인스턴스가 비어 있는지 확인하려면**</span><span class="sxs-lookup"><span data-stu-id="59fbb-218">**To determine if an instance is empty**</span></span>  
 [<span data-ttu-id="59fbb-219">STIsEmpty&#40;geography 데이터 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="59fbb-219">STIsEmpty &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/stisempty-geography-data-type)  
  
###  <a name="closure"></a><a name="closure"></a> <span data-ttu-id="59fbb-220">닫힘</span><span class="sxs-lookup"><span data-stu-id="59fbb-220">Closure</span></span>  
 <span data-ttu-id="59fbb-221">*폐쇄형* `geography` 인스턴스는 시작점과 끝점이 같은 도형입니다.</span><span class="sxs-lookup"><span data-stu-id="59fbb-221">A *closed*`geography` instance is a figure whose start points and end points are the same.</span></span> <span data-ttu-id="59fbb-222">`Polygon` 인스턴스는 닫혀 있다고 간주되며,</span><span class="sxs-lookup"><span data-stu-id="59fbb-222">`Polygon` instances are considered closed.</span></span> <span data-ttu-id="59fbb-223">`Point` 인스턴스는 닫혀 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="59fbb-223">`Point` instances are not closed.</span></span>  
  
 <span data-ttu-id="59fbb-224">링은 단순하고 닫혀 있는 `LineString` 인스턴스입니다.</span><span class="sxs-lookup"><span data-stu-id="59fbb-224">A ring is a simple, closed `LineString` instance.</span></span>  
  
 <span data-ttu-id="59fbb-225">**인스턴스가 닫혀 있는지 확인하려면**</span><span class="sxs-lookup"><span data-stu-id="59fbb-225">**To determine if an instance is closed**</span></span>  
 [<span data-ttu-id="59fbb-226">STIsClosed&#40;geography 데이터 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="59fbb-226">STIsClosed &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/stisclosed-geography-data-type)  
  
 <span data-ttu-id="59fbb-227">**Polygon 인스턴스에 있는 내부 링의 개수를 반환하려면**</span><span class="sxs-lookup"><span data-stu-id="59fbb-227">**To return the number of rings in a Polygon instance**</span></span>  
 [<span data-ttu-id="59fbb-228">NumRings&#40;geography 데이터 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="59fbb-228">NumRings &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/numrings-geography-data-type)  
  
 <span data-ttu-id="59fbb-229">**geography 인스턴스에 지정된 링을 반환하려면**</span><span class="sxs-lookup"><span data-stu-id="59fbb-229">**To return a specified ring of a geography instance**</span></span>  
 [<span data-ttu-id="59fbb-230">RingN&#40;geography 데이터 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="59fbb-230">RingN &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/ringn-geography-data-type)  
  
###  <a name="spatial-reference-id-srid"></a><a name="srid"></a> <span data-ttu-id="59fbb-231">SRID(Spatial Reference ID)</span><span class="sxs-lookup"><span data-stu-id="59fbb-231">Spatial Reference ID (SRID)</span></span>  
 <span data-ttu-id="59fbb-232">SRID는 `geography` 인스턴스를 나타내는 타원 좌표계를 지정하는 식별자입니다.</span><span class="sxs-lookup"><span data-stu-id="59fbb-232">The spatial reference ID (SRID) is an identifier specifying which ellipsoidal coordinate system the `geography` instance is represented in.</span></span> <span data-ttu-id="59fbb-233">다른 SRID를 사용하는 두 `geography` 인스턴스는 서로 비교할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="59fbb-233">Two `geography` instances with different SRIDs cannot be compared.</span></span>  
  
 <span data-ttu-id="59fbb-234">**인스턴스의 SRID를 설정하거나 반환하려면**</span><span class="sxs-lookup"><span data-stu-id="59fbb-234">**To set or return the SRID of an instance**</span></span>  
 [<span data-ttu-id="59fbb-235">STSrid&#40;geography 데이터 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="59fbb-235">STSrid &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/stsrid-geography-data-type)  
  
 <span data-ttu-id="59fbb-236">이 속성은 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="59fbb-236">This property can be modified.</span></span>  
  
##  <a name="determining-relationships-between-geography-instances"></a><a name="rel"></a> <span data-ttu-id="59fbb-237">지리 인스턴스 간 관계 확인</span><span class="sxs-lookup"><span data-stu-id="59fbb-237">Determining Relationships between geography Instances</span></span>  
 <span data-ttu-id="59fbb-238">`geography` 데이터 형식은 수많은 기본 메서드를 제공합니다. 이러한 메서드를 사용하여 두 개의 `geography` 인스턴스 간 관계를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="59fbb-238">The `geography` data type provides many built-in methods you can use to determine relationships between two `geography` instances.</span></span>  
  
 <span data-ttu-id="59fbb-239">**두 인스턴스가 동일한 점 집합으로 구성되었는지 확인하려면**</span><span class="sxs-lookup"><span data-stu-id="59fbb-239">**To determine if two instances comprise the same point set**</span></span>  
 [<span data-ttu-id="59fbb-240">STEquals&#40;geometry 데이터 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="59fbb-240">STEquals &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/stequals-geometry-data-type)  
  
 <span data-ttu-id="59fbb-241">**두 인스턴스가 결합되지 않았는지 확인하려면**</span><span class="sxs-lookup"><span data-stu-id="59fbb-241">**To determine if two instances are disjoint**</span></span>  
 [<span data-ttu-id="59fbb-242">STDisjoint&#40;geometry 데이터 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="59fbb-242">STDisjoint &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/stdisjoint-geometry-data-type)  
  
 <span data-ttu-id="59fbb-243">**두 인스턴스가 교차하는지 확인하려면**</span><span class="sxs-lookup"><span data-stu-id="59fbb-243">**To determine if two instances intersect**</span></span>  
 [<span data-ttu-id="59fbb-244">STIntersects&#40;geometry 데이터 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="59fbb-244">STIntersects &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/stintersects-geometry-data-type)  
  
 <span data-ttu-id="59fbb-245">**두 인스턴스가 교차하는 점을 확인하려면**</span><span class="sxs-lookup"><span data-stu-id="59fbb-245">**To determine the point or points where two instances intersect**</span></span>  
 [<span data-ttu-id="59fbb-246">STIntersection&#40;geography 데이터 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="59fbb-246">STIntersection &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/stintersection-geography-data-type)  
  
 <span data-ttu-id="59fbb-247">**두 geography 인스턴스의 점 간 최단 길이를 확인하려면**</span><span class="sxs-lookup"><span data-stu-id="59fbb-247">**To determine the shortest distance between points in two geography instances**</span></span>  
 [<span data-ttu-id="59fbb-248">STDistance&#40;geometry 데이터 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="59fbb-248">STDistance &#40;geometry Data Type&#41;</span></span>](/sql/t-sql/spatial-geometry/stdistance-geometry-data-type)  
  
 <span data-ttu-id="59fbb-249">**두 geography 인스턴스 간 점의 차이를 확인하려면**</span><span class="sxs-lookup"><span data-stu-id="59fbb-249">**To determine the difference in points between two geography instances**</span></span>  
 [<span data-ttu-id="59fbb-250">STDifference&#40;geography 데이터 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="59fbb-250">STDifference &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/stdifference-geography-data-type)  
  
 <span data-ttu-id="59fbb-251">**한 개의 지리 인스턴스를 다른 인스턴스와 비교하여 대칭 차이 또는 고유 점을 파생하려면**</span><span class="sxs-lookup"><span data-stu-id="59fbb-251">**To derive the symmetric difference, or unique points, of one geography instance compared with another instance**</span></span>  
 [<span data-ttu-id="59fbb-252">STSymDifference&#40;geography 데이터 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="59fbb-252">STSymDifference &#40;geography Data Type&#41;</span></span>](/sql/t-sql/spatial-geography/stsymdifference-geography-data-type)  
  
##  <a name="geography-instances-must-use-supported-srid"></a><a name="supportedsrid"></a> <span data-ttu-id="59fbb-253">지원되는 SRID를 사용해야 하는 geography 인스턴스</span><span class="sxs-lookup"><span data-stu-id="59fbb-253">geography Instances Must Use Supported SRID</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="59fbb-254">에서는 EPSG 표준을 기준으로 하는 SRID를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="59fbb-254">supports SRIDs based on the EPSG standards.</span></span> <span data-ttu-id="59fbb-255">계산을 수행하거나 지리 공간 데이터가 있는 메서드를 사용할 경우 `geography` 인스턴스에 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 지원 SRID가 사용되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="59fbb-255">A [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-supported SRID for `geography` instances must be used when performing calculations or using methods with geography spatial data.</span></span> <span data-ttu-id="59fbb-256">SRID는 **sys.spatial_reference_systems** 카탈로그 뷰에 표시된 SRID 중 하나와 일치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="59fbb-256">The SRID must match one of the SRIDs displayed in the **sys.spatial_reference_systems** catalog view.</span></span> <span data-ttu-id="59fbb-257">앞에서 설명한 대로 각 타원면에는 특정 SRID가 지정되므로 `geography` 데이터 형식을 사용하여 공간 데이터에서 계산을 수행할 경우 데이터를 만드는 데 사용된 타원면에 따라 결과가 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="59fbb-257">As mentioned previously, when you perform calculations on your spatial data using the `geography` data type, your results will depend on which ellipsoid was used in the creation of your data, as each ellipsoid is assigned a specific spatial reference identifier (SRID).</span></span>  
  
 <span data-ttu-id="59fbb-258">`geography` 인스턴스의 메서드를 사용할 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서는 WGS 84 공간 참조 시스템에 매핑되는 기본 SRID 4326을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="59fbb-258">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] uses the default SRID of 4326, which maps to the WGS 84 spatial reference system, when using methods on `geography` instances.</span></span> <span data-ttu-id="59fbb-259">WGS 84(또는 SRID 4326)가 아닌 공간 참조 시스템의 데이터를 사용할 경우 지리 공간 데이터에 대해 특정 SRID를 결정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="59fbb-259">If you use data from a spatial reference system other than WGS 84 (or SRID 4326), you will need to determine the specific SRID for your geography spatial data.</span></span>  
  
##  <a name="examples"></a><a name="examples"></a> <span data-ttu-id="59fbb-260">예</span><span class="sxs-lookup"><span data-stu-id="59fbb-260">Examples</span></span>  
 <span data-ttu-id="59fbb-261">다음 예에서는 geography 데이터를 추가하고 쿼리하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="59fbb-261">The following examples show how to add and query geography data.</span></span>  
  
-   <span data-ttu-id="59fbb-262">첫 번째 예에서는 ID 열과 `geography` 열 `GeogCol1`이 있는 테이블을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="59fbb-262">The first example creates a table with an identity column and a `geography` column `GeogCol1`.</span></span> <span data-ttu-id="59fbb-263">세 번째 열에서는 `geography` 열을 OGC(Open Geospatial Consortium) WKT(Well-Known Text) 표현으로 렌더링하고 `STAsText()` 메서드를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="59fbb-263">A third column renders the `geography` column into its Open Geospatial Consortium (OGC) Well-Known Text (WKT) representation, and uses the `STAsText()` method.</span></span> <span data-ttu-id="59fbb-264">그러고 나면 두 개의 행이 삽입됩니다. 이 중 한 행에는 `LineString` 의 `geography`인스턴스가 들어 있고, 다른 행에는 `Polygon` 인스턴스가 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="59fbb-264">Two rows are then inserted: one row contains a `LineString` instance of `geography`, and one row contains a `Polygon` instance.</span></span>  
  
    ```  
    IF OBJECT_ID ( 'dbo.SpatialTable', 'U' ) IS NOT NULL   
        DROP TABLE dbo.SpatialTable;  
    GO  
  
    CREATE TABLE SpatialTable   
        ( id int IDENTITY (1,1),  
        GeogCol1 geography,   
        GeogCol2 AS GeogCol1.STAsText() );  
    GO  
  
    INSERT INTO SpatialTable (GeogCol1)  
    VALUES (geography::STGeomFromText('LINESTRING(-122.360 47.656, -122.343 47.656)', 4326));  
  
    INSERT INTO SpatialTable (GeogCol1)  
    VALUES (geography::STGeomFromText('POLYGON((-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653))', 4326));  
    GO  
    ```  
  
-   <span data-ttu-id="59fbb-265">두 번째 예에서는 `STIntersection()` 메서드를 사용하여 앞서 삽입한 두 `geography` 인스턴스가 교차하는 지점을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="59fbb-265">The second example uses the `STIntersection()` method to return the points where the two previously inserted `geography` instances intersect.</span></span>  
  
    ```  
    DECLARE @geog1 geography;  
    DECLARE @geog2 geography;  
    DECLARE @result geography;  
  
    SELECT @geog1 = GeogCol1 FROM SpatialTable WHERE id = 1;  
    SELECT @geog2 = GeogCol1 FROM SpatialTable WHERE id = 2;  
    SELECT @result = @geog1.STIntersection(@geog2);  
    SELECT @result.STAsText();  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="59fbb-266">참고 항목</span><span class="sxs-lookup"><span data-stu-id="59fbb-266">See Also</span></span>  
 [<span data-ttu-id="59fbb-267">공간 데이터&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="59fbb-267">Spatial Data &#40;SQL Server&#41;</span></span>](spatial-data-sql-server.md)  
  
  
