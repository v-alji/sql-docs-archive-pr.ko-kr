---
title: SRID(Spatial Reference Identifier) | Microsoft 문서
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- Spatial Reference Identifiers (SRIDs)
- geodetic spatial data [SQL Server], identifiers
- SRID
ms.assetid: 0612658a-7d1b-4178-bdc2-42b914ea31a7
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 15db59b43731b9a39ff4bef78e3a6cb6929e9b47
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652052"
---
# <a name="spatial-reference-identifiers-srids"></a><span data-ttu-id="c05c7-102">SRID(Spatial Reference Identifier)</span><span class="sxs-lookup"><span data-stu-id="c05c7-102">Spatial Reference Identifiers (SRIDs)</span></span>
  <span data-ttu-id="c05c7-103">각 공간 인스턴스에는 SRID(spatial reference identifier)가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c05c7-103">Each spatial instance has a spatial reference identifier (SRID).</span></span> <span data-ttu-id="c05c7-104">SRID는 평면 지구 매핑 또는 둥근 지구 매핑에 사용되는 특정 타원면을 기준으로 하는 공간 참조 시스템에 해당합니다.</span><span class="sxs-lookup"><span data-stu-id="c05c7-104">The SRID corresponds to a spatial reference system based on the specific ellipsoid used for either flat-earth mapping or round-earth mapping.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="c05c7-105">새 SRID를 포함하여 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]에 도입된 새로운 공간 기능에 대한 자세한 설명 및 예제를 보려면 [SQL Server 2012의 새로운 공간 기능](https://go.microsoft.com/fwlink/?LinkId=226407)백서를 다운로드하세요.</span><span class="sxs-lookup"><span data-stu-id="c05c7-105">For a detailed description and examples of spatial features introduced in [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], including a new SRID, download the white paper, [New Spatial Features in SQL Server 2012](https://go.microsoft.com/fwlink/?LinkId=226407).</span></span>  
  
 <span data-ttu-id="c05c7-106">공간 열은 SRID가 다른 개체를 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c05c7-106">A spatial column can contain objects with different SRIDs.</span></span> <span data-ttu-id="c05c7-107">그러나 SRID가 같은 단일 공간 인스턴스만 데이터에 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 공간 데이터 메서드를 사용하는 작업을 수행할 때 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c05c7-107">However, only spatial instances with the same SRID can be used when performing operations with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] spatial data methods on your data.</span></span> <span data-ttu-id="c05c7-108">두 공간 데이터 인스턴스에서 파생되는 모든 공간 메서드의 결과는 이러한 인스턴스에 동일한 SRID가 있을 경우에만 유효합니다. 이 SRID는 인스턴스의 좌표를 결정하는 데 사용되는 동일한 측정 단위, 데이터 및 프로젝션을 기준으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="c05c7-108">The result of any spatial method derived from two spatial data instances is valid only if those instances have the same SRID that is based on the same unit of measurement, datum, and projection used to determine the coordinates of the instances.</span></span> <span data-ttu-id="c05c7-109">가장 일반적인 SRID의 측정 단위는 미터 또는 제곱미터입니다.</span><span class="sxs-lookup"><span data-stu-id="c05c7-109">The most common units of measurement of a SRID are meters or square meters.</span></span>  
  
 <span data-ttu-id="c05c7-110">두 공간 인스턴스의 SRID가 같지 않을 경우 이 인스턴스에서 사용되는 `geometry` 또는 `geography` 데이터 형식 메서드의 결과로 NULL이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="c05c7-110">If two spatial instances do not have the same SRID, the results from a `geometry` or `geography` Data Type method used on the instances will return NULL.</span></span> <span data-ttu-id="c05c7-111">예를 들어 NULL이 아닌 결과를 반환하는 다음 조건자 조건의 경우 `geometry1` 및 `geometry2`의 두 `geometry` 인스턴스의 SRID가 같아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c05c7-111">For example, for the following predicate term to return a non-NULL result, the two `geometry` instances, `geometry1` and `geometry2`, must have the same SRID:</span></span>  
  
 `geometry1.STIntersects(geometry2) = 1`  
  
> [!NOTE]  
>  <span data-ttu-id="c05c7-112">공간 참조 확인 시스템은 지도 제작, 측량 및 측지 데이터 스토리지를 위해 개발된 표준 집합인 [EPSG(European Petroleum Survey Group)](https://go.microsoft.com/fwlink/?LinkId=99349) 표준에 따라 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="c05c7-112">The spatial reference identification system is defined by the [European Petroleum Survey Group (EPSG)](https://go.microsoft.com/fwlink/?LinkId=99349) standard, which is a set of standards developed for cartography, surveying, and geodetic data storage.</span></span> <span data-ttu-id="c05c7-113">이 표준은 OGP(Oil and Gas Producers) Surveying and Positioning Committee에서 소유하고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c05c7-113">This standard is owned by the Oil and Gas Producers (OGP) Surveying and Positioning Committee.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c05c7-114">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c05c7-114">See Also</span></span>  
 [<span data-ttu-id="c05c7-115">공간 데이터 형식 개요</span><span class="sxs-lookup"><span data-stu-id="c05c7-115">Spatial Data Types Overview</span></span>](spatial-data-types-overview.md)  
  
  
