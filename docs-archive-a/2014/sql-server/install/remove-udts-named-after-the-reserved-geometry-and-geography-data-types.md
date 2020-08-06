---
title: 예약 된 GEOMETRY 및 GEOGRAPHY 데이터 형식으로 이름이 지정 된 Udt를 제거 합니다. Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- geometry data type [SQL Server], UDTs
- geography data type [SQL Server], UDTs
ms.assetid: a167ce3a-50b4-4e77-a884-adb23b586c72
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 4977d45d53e1114edc8e04ad504963bae0b9eb9d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742800"
---
# <a name="remove-udts-named-after-the-reserved-geometry-and-geography-data-types"></a><span data-ttu-id="9342b-102">예약된 GEOMETRY 및 GEOGRAPHY 데이터 형식의 이름을 따서 명명된 UDT를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="9342b-102">Remove UDTs named after the reserved GEOMETRY and GEOGRAPHY data types</span></span>
  <span data-ttu-id="9342b-103">업그레이드 관리자가 `geometry` 또는 `geography` 데이터 형식용으로 예약된 용어를 따서 명명된 UDT(사용자 정의 형식)를 발견했습니다.</span><span class="sxs-lookup"><span data-stu-id="9342b-103">Upgrade Advisor detected a user-defined type (UDT) that is named after a term reserved for either the `geometry` or the `geography` data types.</span></span> <span data-ttu-id="9342b-104">`geometry` 및 `geography` 데이터 형식은 공간 데이터 기능의 일부입니다.</span><span class="sxs-lookup"><span data-stu-id="9342b-104">The `geometry` and `geography` data types are part of the spatial data feature.</span></span>  
  
## <a name="component"></a><span data-ttu-id="9342b-105">구성 요소</span><span class="sxs-lookup"><span data-stu-id="9342b-105">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a><span data-ttu-id="9342b-106">설명</span><span class="sxs-lookup"><span data-stu-id="9342b-106">Description</span></span>  
 <span data-ttu-id="9342b-107">공간 데이터 형식에 사용되는 용어는 CLR(공용 언어 런타임) 또는 별칭 UDT의 이름으로 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9342b-107">The terms used for spatial data types should not be used as names for either common language runtime (CLR) or alias UDTs.</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="9342b-108">수정 동작</span><span class="sxs-lookup"><span data-stu-id="9342b-108">Corrective Action</span></span>  
 <span data-ttu-id="9342b-109">데이터 형식의 이름을 따서 명명된 UDT를 제거하고 예약되지 않은 이름을 사용하여 UDT를 다시 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="9342b-109">Remove the UDT that is named after the data type and recreate the UDT with an unreserved name.</span></span>  
  
## <a name="external-resources"></a><span data-ttu-id="9342b-110">외부 리소스</span><span class="sxs-lookup"><span data-stu-id="9342b-110">External Resources</span></span>  
 [<span data-ttu-id="9342b-111">사용자 정의 형식 만들기</span><span class="sxs-lookup"><span data-stu-id="9342b-111">Creating a User-Defined Type</span></span>](../../relational-databases/clr-integration-database-objects-user-defined-types/creating-user-defined-types.md)  
  
 [<span data-ttu-id="9342b-112">공간 데이터 형식 개요</span><span class="sxs-lookup"><span data-stu-id="9342b-112">Spatial Data Types Overview</span></span>](../../relational-databases/spatial/spatial-data-types-overview.md)  
  
  
