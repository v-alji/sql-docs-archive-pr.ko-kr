---
title: 큐브 계층 속성 정의 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- hierarchies [Analysis Services], multilevel
- hierarchies [Analysis Services], cubes
ms.assetid: 819d0a4e-7815-4332-a605-b07ca2ade6ac
author: minewiskan
ms.author: owend
ms.openlocfilehash: 8903a49754357aad9cf24ee63fffa45fbf120e4d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728888"
---
# <a name="define-cube-hierarchy-properties"></a><span data-ttu-id="52e3e-102">큐브 계층 속성 정의</span><span class="sxs-lookup"><span data-stu-id="52e3e-102">Define Cube Hierarchy Properties</span></span>
  <span data-ttu-id="52e3e-103">큐브 계층 속성을 통해 동일한 데이터베이스 차원에 기반을 두는 큐브 차원의 사용자 정의 계층에 대해 고유한 설정을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52e3e-103">Cube hierarchy properties enable you to specify unique settings for user-defined hierarchies in cube dimensions based on the same database dimension.</span></span> <span data-ttu-id="52e3e-104">다음 표에서는 큐브 계층의 속성을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="52e3e-104">The following table describes the properties of a cube hierarchy.</span></span>  
  
|<span data-ttu-id="52e3e-105">속성</span><span class="sxs-lookup"><span data-stu-id="52e3e-105">Property</span></span>|<span data-ttu-id="52e3e-106">Description</span><span class="sxs-lookup"><span data-stu-id="52e3e-106">Description</span></span>|  
|--------------|-----------------|  
|`Enabled`|<span data-ttu-id="52e3e-107">큐브 차원에 대해 계층이 설정되는지 여부를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="52e3e-107">Determines whether the hierarchy is enabled for the cube dimension.</span></span>|  
|`HierarchyID`|<span data-ttu-id="52e3e-108">계층의 고유 ID를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="52e3e-108">Contains the unique identifier (ID) of the hierarchy.</span></span>|  
|`OptimizedState`|<span data-ttu-id="52e3e-109">계층에 적용되는 최적화 수준을 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="52e3e-109">Determines the level of optimization that is applied to the hierarchy.</span></span> <span data-ttu-id="52e3e-110">이 속성 값은 다음 중 하나일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52e3e-110">This property can have the following values:</span></span><br /><br /> <span data-ttu-id="52e3e-111">`FullyOptimized`: 인스턴스는 계층에 대해 인덱스를 작성하여 쿼리 성능을 향상시킵니다.</span><span class="sxs-lookup"><span data-stu-id="52e3e-111">`FullyOptimized`: The instance builds indexes for the hierarchy to improve query performance.</span></span> <span data-ttu-id="52e3e-112">기본값입니다.</span><span class="sxs-lookup"><span data-stu-id="52e3e-112">This is the default value.</span></span><br /><br /> <span data-ttu-id="52e3e-113">`NotOptimized`: 인스턴스는 추가 인덱스를 작성하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="52e3e-113">`NotOptimized`: The instance does not build additional indexes.</span></span>|  
|`Visible`|<span data-ttu-id="52e3e-114">큐브 계층의 표시 유형을 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="52e3e-114">Determines the visibility of the cube hierarchy.</span></span> <span data-ttu-id="52e3e-115">기본값은 `True`입니다.</span><span class="sxs-lookup"><span data-stu-id="52e3e-115">The default value is `True`.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="52e3e-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="52e3e-116">See Also</span></span>  
 [<span data-ttu-id="52e3e-117">사용자 계층</span><span class="sxs-lookup"><span data-stu-id="52e3e-117">User Hierarchies</span></span>](../multidimensional-models-olap-logical-dimension-objects/user-hierarchies.md)  
  
  
