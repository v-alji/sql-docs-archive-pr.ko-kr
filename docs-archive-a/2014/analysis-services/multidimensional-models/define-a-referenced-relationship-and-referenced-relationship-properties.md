---
title: 참조 관계 및 참조 관계 속성 정의 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- referenced dimension relationship
- relationships [Analysis Services], referenced dimensions
ms.assetid: 5bb44b41-635b-4398-8fe9-0bfbb142553e
author: minewiskan
ms.author: owend
ms.openlocfilehash: a84cf2ed95ab3660c5a6b3c039dc58351dc43264
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87732128"
---
# <a name="define-a-referenced-relationship-and-referenced-relationship-properties"></a><span data-ttu-id="4bc34-102">참조 관계 및 참조 관계 속성 정의</span><span class="sxs-lookup"><span data-stu-id="4bc34-102">Define a Referenced Relationship and Referenced Relationship Properties</span></span>
  <span data-ttu-id="4bc34-103">참조 차원 관계는 큐브 디자이너의 **차원 용도** 탭에서</span><span class="sxs-lookup"><span data-stu-id="4bc34-103">A reference dimension relationship is defined on the **Dimension Usage** tab of Cube Designer.</span></span> <span data-ttu-id="4bc34-104">다음을 지정하여 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="4bc34-104">The reference dimension relationship is defined by specifying the following:</span></span>  
  
-   <span data-ttu-id="4bc34-105">조인할 중간 차원.</span><span class="sxs-lookup"><span data-stu-id="4bc34-105">The intermediate dimension to which to join.</span></span> <span data-ttu-id="4bc34-106">일반 차원이나 다른 참조 차원이 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4bc34-106">This can be a regular dimension or another reference dimension.</span></span>  
  
-   <span data-ttu-id="4bc34-107">측정값 그룹에 대해 차원을 집계에 사용할 수 있는 최하위 수준을 정의하는 참조 차원 특성입니다.</span><span class="sxs-lookup"><span data-stu-id="4bc34-107">A reference dimension attribute that defines the lowest level that the dimension is available for aggregation with regard to the measure group.</span></span>  
  
-   <span data-ttu-id="4bc34-108">참조 차원 특성에 해당되는 중간 차원의 (외래 키) 특성</span><span class="sxs-lookup"><span data-stu-id="4bc34-108">The (foreign key) attribute in the intermediate dimension that corresponds to the reference dimension attribute.</span></span>  
  
 <span data-ttu-id="4bc34-109">일반적으로 참조 차원을 팩트 테이블에 연결하는 열(참조 차원에서 키 특성에 해당) 또한 중간 차원에서 특성으로 정의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4bc34-109">Notice that the column that links the reference dimension to the fact table, which is generally the key attribute in the reference dimension, must also be defined as an attribute in the intermediate dimension.</span></span> <span data-ttu-id="4bc34-110">참조 차원 체인을 만들 때는 먼저 체인의 첫 번째 차원과 측정값 그룹 간의 일반 관계를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="4bc34-110">When you create a chain of reference dimensions, start by creating the regular relationship between the first dimension in the chain and the measure group.</span></span> <span data-ttu-id="4bc34-111">그런 다음 각각의 추가 참조된 관계를 순서대로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="4bc34-111">Then create each additional referenced relationship in order.</span></span> <span data-ttu-id="4bc34-112">참조된 관계는 측정값 그룹에 대한 기존 관계가 있는 차원에 대해서만 가능합니다.</span><span class="sxs-lookup"><span data-stu-id="4bc34-112">A referenced relationship can only be made to a dimension that has an existing relationship to the measure group.</span></span>  
  
 <span data-ttu-id="4bc34-113">참조 차원 관계를 만들 때는 기본적으로 차원 특성 링크가 구체화됩니다.</span><span class="sxs-lookup"><span data-stu-id="4bc34-113">When you create a reference dimension relationship, the dimension attribute link is materialized by default.</span></span> <span data-ttu-id="4bc34-114">차원의 MOLAP 구조에서 차원 특성 링크를 구체화하면 처리하는 동안 팩트 테이블과 각 행의 참조 차원 간 링크 값이 구체화되거나 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="4bc34-114">Materializing a dimension attribute link causes the value of the link between the fact table and the reference dimension for each row to be materialized, or stored, in the MOLAP structure for the dimension during processing.</span></span> <span data-ttu-id="4bc34-115">이렇게 해도 처리 성능과 스토리지 요구 사항에는 거의 영향을 주지 않지만 쿼리 성능은 향상됩니다.</span><span class="sxs-lookup"><span data-stu-id="4bc34-115">This will have a minor effect on processing performance and storage requirements, but will improve query performance.</span></span>  
  
 <span data-ttu-id="4bc34-116">참조 차원에서 세분성은 참조 차원과 주 차원 테이블에 해당되는 측정값 그룹 간의 관계를 정의하는 특성을 식별하여 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="4bc34-116">In a reference dimension, granularity is specified by identifying the attribute that defines the relationship between a reference dimension and the measure group corresponding to the main table of the dimension.</span></span> <span data-ttu-id="4bc34-117">여러 참조 차원이 함께 연결될 때는 참조가 가장 바깥쪽 차원에서 측정값 그룹까지의 관계를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="4bc34-117">When multiple reference dimensions are chained together, the references define the relationship from the outermost dimension to the measure group.</span></span>  
  
  
