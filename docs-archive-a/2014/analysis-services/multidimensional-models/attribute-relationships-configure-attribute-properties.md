---
title: 특성 관계 속성 구성 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- flexible relationships (Analysis Services)
- attributes [Analysis Services], relationships
- relationships [Analysis Services], attributes
- properties [Analysis Services], attribute relationships
- rigid relationships (Analysis Services)
ms.assetid: fce511af-66d7-42fc-bb3a-6c516f16b10e
author: minewiskan
ms.author: owend
ms.openlocfilehash: 241fa2af16377fd2cacf657ec6f99c5ca4bd0c53
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646709"
---
# <a name="configure-attribute-relationship-properties"></a><span data-ttu-id="41216-102">특성 관계 속성 구성</span><span class="sxs-lookup"><span data-stu-id="41216-102">Configure Attribute Relationship Properties</span></span>
  <span data-ttu-id="41216-103">다음 표에서는 특성 관계 속성을 나열하고 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="41216-103">The following table lists and describes the properties of an attribute relationship.</span></span>  
  
|<span data-ttu-id="41216-104">속성</span><span class="sxs-lookup"><span data-stu-id="41216-104">Property</span></span>|<span data-ttu-id="41216-105">설명</span><span class="sxs-lookup"><span data-stu-id="41216-105">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="41216-106">특성</span><span class="sxs-lookup"><span data-stu-id="41216-106">Attribute</span></span>|<span data-ttu-id="41216-107">특성의 이름을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="41216-107">Contains the name of the attribute.</span></span>|  
|<span data-ttu-id="41216-108">카디널리티</span><span class="sxs-lookup"><span data-stu-id="41216-108">Cardinality</span></span>|<span data-ttu-id="41216-109">관계의 카디널리티를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="41216-109">Indicates the cardinality of the relationship.</span></span> <span data-ttu-id="41216-110">사용 가능한 값은 Many(다 대 일 관계의 경우) 또는 One(일 대 일 관계의 경우)입니다.</span><span class="sxs-lookup"><span data-stu-id="41216-110">Values are Many, for a many to one relationship, or One, for a one to one relationship.</span></span> <span data-ttu-id="41216-111">기본값은 Many입니다.</span><span class="sxs-lookup"><span data-stu-id="41216-111">Default value is Many.</span></span> <span data-ttu-id="41216-112">에서 카디널리티 속성은 아무런 영향을 주지 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 않습니다 .이 속성의 용도는 나중에 구현할 수 있도록 예약 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="41216-112">In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], the cardinality property has no effect - its use is reserved for a future implementation.</span></span>|  
|<span data-ttu-id="41216-113">이름</span><span class="sxs-lookup"><span data-stu-id="41216-113">Name</span></span>|<span data-ttu-id="41216-114">특성의 이름을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="41216-114">Contains the friendly name of the attribute.</span></span>|  
|<span data-ttu-id="41216-115">RelationshipType</span><span class="sxs-lookup"><span data-stu-id="41216-115">RelationshipType</span></span>|<span data-ttu-id="41216-116">멤버 관계가 시간에 따라 변경되는지 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="41216-116">Indicates whether member relationships change over time.</span></span> <span data-ttu-id="41216-117">사용 가능한 값은 Rigid(멤버 간의 관계가 시간에 따라 변경되지 않는 경우) 또는 Flexible(멤버 간의 관계가 시간에 따라 변경되는 경우)입니다.</span><span class="sxs-lookup"><span data-stu-id="41216-117">Values are Rigid, which means that relationships between members do not change over time, or Flexible, which means that relationships between members change over time.</span></span> <span data-ttu-id="41216-118">기본값은 Flexible입니다.</span><span class="sxs-lookup"><span data-stu-id="41216-118">Default is Flexible.</span></span> <span data-ttu-id="41216-119">유연한 관계(Flexible)로 정의하면 증분 업데이트의 일부로서 집계가 삭제되고 다시 계산됩니다. 집계는 새 멤버가 추가된 경우에만 삭제되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="41216-119">If you define a relationship as flexible, aggregations are dropped and recomputed as part of an incremental update (they will not be dropped if only new members are added).</span></span> <span data-ttu-id="41216-120">고정된 관계로 정의할 경우 차원이 증분 업데이트되면 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 가 집계를 보유합니다.</span><span class="sxs-lookup"><span data-stu-id="41216-120">If you define a relationship as rigid, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] retains aggregations when the dimension is incrementally updated.</span></span> <span data-ttu-id="41216-121">고정된 관계로 정의한 관계가 실제로 변경되면 증분 처리 중에 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 에서 오류를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="41216-121">If a relationship that is defined as rigid actually changes, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] generates an error during incremental processing.</span></span> <span data-ttu-id="41216-122">관계와 관계 속성을 적절히 지정하면 쿼리와 처리 성능이 향상됩니다.</span><span class="sxs-lookup"><span data-stu-id="41216-122">Specifying the appropriate relationships and relationship properties increases query and processing performance.</span></span>|  
|<span data-ttu-id="41216-123">표시</span><span class="sxs-lookup"><span data-stu-id="41216-123">Visible</span></span>|<span data-ttu-id="41216-124">특성 관계의 표시 유형을 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="41216-124">Determines the visibility of the attribute relationship.</span></span> <span data-ttu-id="41216-125">사용 가능한 값은 True 또는 False입니다.</span><span class="sxs-lookup"><span data-stu-id="41216-125">Values are True or False.</span></span> <span data-ttu-id="41216-126">기본값은 True입니다.</span><span class="sxs-lookup"><span data-stu-id="41216-126">Default is True.</span></span>|  
  
  
