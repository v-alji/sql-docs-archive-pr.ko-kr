---
title: 공간 데이터(SQL Server) | Microsoft 문서
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- geography data type [SQL Server], spatial storage design
- planar spatial data [SQL Server], designing
- spatial data types [SQL Server]
- geodetic spatial data [SQL Server]
- geometry data type [SQL Server], spatial storage design
- spatial storage [SQL Server]
- geodetic spatial data [SQL Server], designing
ms.assetid: 41a132a1-09e2-4426-b9df-225270cb8e15
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 4d491420a9eca7c35b89b254a03381c6467c834c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660420"
---
# <a name="spatial-data-sql-server"></a><span data-ttu-id="638b5-102">공간 데이터(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="638b5-102">Spatial Data (SQL Server)</span></span>
  <span data-ttu-id="638b5-103">공간 데이터는 기하학적 개체의 물리적 위치 및 모양 정보를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="638b5-103">Spatial data represents information about the physical location and shape of geometric objects.</span></span> <span data-ttu-id="638b5-104">이러한 개체는 지점 위치이거나 국가, 도로 또는 호수와 같은 더 복잡한 개체일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="638b5-104">These objects can be point locations or more complex objects such as countries, roads, or lakes.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="638b5-105">에서는: the `geometry` 데이터 형식 및 `geography` 데이터 형식의 두 가지 공간 데이터 형식을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="638b5-105">supports two spatial data types: the `geometry` data type and the `geography` data type.</span></span>  
  
-   <span data-ttu-id="638b5-106">`geometry` 유형은 유클리드(평면) 좌표계의 데이터를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="638b5-106">The `geometry` type represents data in a Euclidean (flat) coordinate system.</span></span>  
  
-   <span data-ttu-id="638b5-107">`geography` 형식은 둥근 표면 좌표 시스템의 데이터를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="638b5-107">The `geography` type represents data in a round-earth coordinate system.</span></span>  
  
 <span data-ttu-id="638b5-108">두 가지 데이터 형식 모두 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 .NET CLR(공용 언어 런타임) 데이터 형식으로 구현됩니다.</span><span class="sxs-lookup"><span data-stu-id="638b5-108">Both data types are implemented as .NET common language runtime (CLR) data types in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="638b5-109">[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]의 새로운 공간 기능에 대한 자세한 설명 및 예제를 보려면 [SQL Server 2012의 새로운 공간 기능](https://go.microsoft.com/fwlink/?LinkId=226407)백서를 다운로드하세요.</span><span class="sxs-lookup"><span data-stu-id="638b5-109">For a detailed description and examples of spatial features introduced in [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], download the white paper, [New Spatial Features in SQL Server 2012](https://go.microsoft.com/fwlink/?LinkId=226407).</span></span>  
  
##  <a name="related-tasks"></a><a name="reltasks"></a> <span data-ttu-id="638b5-110">관련 작업</span><span class="sxs-lookup"><span data-stu-id="638b5-110">Related Tasks</span></span>  
 [<span data-ttu-id="638b5-111">geometry 인스턴스 만들기, 구성 및 쿼리</span><span class="sxs-lookup"><span data-stu-id="638b5-111">Create, Construct, and Query geometry Instances</span></span>](create-construct-and-query-geometry-instances.md)  
 <span data-ttu-id="638b5-112">geometry 데이터 형식의 인스턴스를 사용하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="638b5-112">Describes the methods that you can use with instances of the geometry data type.</span></span>  
  
 [<span data-ttu-id="638b5-113">geography 인스턴스 만들기, 구성 및 쿼리</span><span class="sxs-lookup"><span data-stu-id="638b5-113">Create, Construct, and Query geography Instances</span></span>](create-construct-and-query-geography-instances.md)  
 <span data-ttu-id="638b5-114">geography 데이터 형식의 인스턴스를 사용하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="638b5-114">Describes the methods that you can use with instances of the geography data type.</span></span>  
  
 [<span data-ttu-id="638b5-115">가장 인접한 항목의 공간 데이터 쿼리</span><span class="sxs-lookup"><span data-stu-id="638b5-115">Query Spatial Data for Nearest Neighbor</span></span>](query-spatial-data-for-nearest-neighbor.md)  
 <span data-ttu-id="638b5-116">특정 공간 개체에 가장 가까운 공간 개체를 찾는 데 사용되는 일반 쿼리 패턴에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="638b5-116">Describes the common query pattern that is used to find the closest spatial objects to a specific spatial object.</span></span>  
  
 [<span data-ttu-id="638b5-117">공간 인덱스 만들기, 수정 및 삭제</span><span class="sxs-lookup"><span data-stu-id="638b5-117">Create, Modify, and Drop Spatial Indexes</span></span>](create-modify-and-drop-spatial-indexes.md)  
 <span data-ttu-id="638b5-118">공간 인덱스를 생성, 변경 및 삭제하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="638b5-118">Provides information about creating, altering, and dropping a spatial index.</span></span>  
  
## <a name="related-content"></a><span data-ttu-id="638b5-119">관련 내용</span><span class="sxs-lookup"><span data-stu-id="638b5-119">Related Content</span></span>  
 [<span data-ttu-id="638b5-120">공간 데이터 형식 개요</span><span class="sxs-lookup"><span data-stu-id="638b5-120">Spatial Data Types Overview</span></span>](spatial-data-types-overview.md)  
 <span data-ttu-id="638b5-121">공간 데이터 형식을 소개합니다.</span><span class="sxs-lookup"><span data-stu-id="638b5-121">Introduces the spatial data types.</span></span>  
  
-   [<span data-ttu-id="638b5-122">Point</span><span class="sxs-lookup"><span data-stu-id="638b5-122">Point</span></span>](point.md)  
  
-   [<span data-ttu-id="638b5-123">LineString</span><span class="sxs-lookup"><span data-stu-id="638b5-123">LineString</span></span>](linestring.md)  
  
-   [<span data-ttu-id="638b5-124">CircularString</span><span class="sxs-lookup"><span data-stu-id="638b5-124">CircularString</span></span>](circularstring.md)  
  
-   [<span data-ttu-id="638b5-125">CompoundCurve</span><span class="sxs-lookup"><span data-stu-id="638b5-125">CompoundCurve</span></span>](compoundcurve.md)  
  
-   [<span data-ttu-id="638b5-126">Polygon</span><span class="sxs-lookup"><span data-stu-id="638b5-126">Polygon</span></span>](polygon.md)  
  
-   [<span data-ttu-id="638b5-127">CurvePolygon</span><span class="sxs-lookup"><span data-stu-id="638b5-127">CurvePolygon</span></span>](curvepolygon.md)  
  
-   [<span data-ttu-id="638b5-128">MultiPoint</span><span class="sxs-lookup"><span data-stu-id="638b5-128">MultiPoint</span></span>](multipoint.md)  
  
-   [<span data-ttu-id="638b5-129">MultiLineString</span><span class="sxs-lookup"><span data-stu-id="638b5-129">MultiLineString</span></span>](multilinestring.md)  
  
-   [<span data-ttu-id="638b5-130">MultiPolygon</span><span class="sxs-lookup"><span data-stu-id="638b5-130">MultiPolygon</span></span>](multipolygon.md)  
  
-   [<span data-ttu-id="638b5-131">GeometryCollection</span><span class="sxs-lookup"><span data-stu-id="638b5-131">GeometryCollection</span></span>](geometrycollection.md)  
  
 [<span data-ttu-id="638b5-132">공간 인덱스 개요</span><span class="sxs-lookup"><span data-stu-id="638b5-132">Spatial Indexes Overview</span></span>](spatial-indexes-overview.md)  
 <span data-ttu-id="638b5-133">공간 인덱스를 소개하고 공간 분할 및 공간 분할 구성표에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="638b5-133">Introduces spatial indexes and describes tessellation and tessellation schemes.</span></span>  
  
  
