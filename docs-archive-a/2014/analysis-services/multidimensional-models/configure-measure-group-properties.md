---
title: 측정값 그룹 속성 구성 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- properties [Analysis Services], measure groups
ms.assetid: fa66bdb6-60b8-413c-ac2a-00e4d09f60a2
author: minewiskan
ms.author: owend
ms.openlocfilehash: 03dad3d8ee33ea8a78b08f9a354d0db3d177198c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737113"
---
# <a name="configure-measure-group-properties"></a><span data-ttu-id="da343-102">측정값 그룹 속성 구성</span><span class="sxs-lookup"><span data-stu-id="da343-102">Configure Measure Group Properties</span></span>
  <span data-ttu-id="da343-103">측정값 그룹에는 측정값 그룹의 작동 방법을 정의할 수 있는 속성이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="da343-103">Measures groups have properties that enable you to define how measure groups function.</span></span>  
  
## <a name="measure-group-properties"></a><span data-ttu-id="da343-104">측정값 그룹 속성</span><span class="sxs-lookup"><span data-stu-id="da343-104">Measure Group Properties</span></span>  
 <span data-ttu-id="da343-105">측정값 그룹 속성은 전체 측정값 그룹의 동작을 결정하고 측정값 그룹에 있는 측정값의 특정 속성에 대한 기본 동작을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="da343-105">Measure group properties determine behaviors for the entire measure group and set the default behaviors for certain properties of measures within a measure group.</span></span>  
  
|<span data-ttu-id="da343-106">속성</span><span class="sxs-lookup"><span data-stu-id="da343-106">Property</span></span>|<span data-ttu-id="da343-107">정의</span><span class="sxs-lookup"><span data-stu-id="da343-107">Definition</span></span>|  
|--------------|----------------|  
|`AggregationPrefix`|<span data-ttu-id="da343-108">ROLAP 스토리지에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="da343-108">Applies to ROLAP storage.</span></span> <span data-ttu-id="da343-109">SQL Server에서 이 측정값 그룹과 연관된 파티션에 대한 집계를 저장하는 데 사용되는 인덱싱된 뷰에 공통 접두사를 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="da343-109">Assigns a common prefix to the indexed views in SQL Server, used to store aggregations for the partitions associated with this measure group.</span></span>|  
|`DataAggregation`|<span data-ttu-id="da343-110">이 속성은 나중에 사용하도록 예약되어 있으며 현재 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="da343-110">This property is reserved for future use and currently has no effect.</span></span> <span data-ttu-id="da343-111">따라서 이 설정을 수정하지 않는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="da343-111">Therefore, it is recommended that you do not modify this setting.</span></span>|  
|`Description`|<span data-ttu-id="da343-112">이 속성을 사용하여 측정값 그룹을 문서화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="da343-112">You can use this property to document the measure group.</span></span>|  
|`ErrorConfiguration`|<span data-ttu-id="da343-113">중복 키, 알 수 없는 키, Null 키, 오류 제한, 오류 감지 시 수행 동작 및 오류 로그 파일을 처리할 때 구성 가능한 오류 처리 설정을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="da343-113">Configurable error handling settings for handling of duplicate keys, unknown keys, null keys, error limits, action upon error detection, and the error log file.</span></span> <span data-ttu-id="da343-114">[큐브, 파티션 및 차원 처리에 대한 오류 구성&#40;SSAS - 다차원&#41;](error-configuration-for-cube-partition-and-dimension-processing.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="da343-114">See [Error Configuration for Cube, Partition, and Dimension Processing &#40;SSAS - Multidimensional&#41;](error-configuration-for-cube-partition-and-dimension-processing.md).</span></span>|  
|`EstimatedRows`|<span data-ttu-id="da343-115">팩트 테이블의 예상 행 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="da343-115">Specifies the estimated number of rows in the fact table.</span></span>|  
|`EstimatedSize`|<span data-ttu-id="da343-116">측정값 그룹의 예상 크기(바이트)를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="da343-116">Specifies the estimated size (in bytes) of the measure group.</span></span>|  
|`ID`|<span data-ttu-id="da343-117">개체의 식별자를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="da343-117">Specifies the identifier of the object.</span></span>|  
|`IgnoreUnrelatedDimensions`|<span data-ttu-id="da343-118">측정값 그룹과 관련이 없는 차원의 멤버가 쿼리에 포함될 때 관련이 없는 차원이 최상위로 강제되는지 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="da343-118">Determines whether unrelated dimensions are forced to their top level when members of dimensions that are unrelated to the measure group are included in a query.</span></span> <span data-ttu-id="da343-119">기본 설정은 `True`입니다.</span><span class="sxs-lookup"><span data-stu-id="da343-119">Default setting is `True`.</span></span>|  
|`Name`|<span data-ttu-id="da343-120">측정값의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="da343-120">Name of the measure.</span></span> <span data-ttu-id="da343-121">이 속성은 읽기 전용입니다.</span><span class="sxs-lookup"><span data-stu-id="da343-121">This property is read-only.</span></span>|  
|`ProactiveCaching`|<span data-ttu-id="da343-122">중복 키, 알 수 없는 키, Null 키, 오류 제한, 오류 감지 시 수행 동작 및 오류 로그 파일을 처리할 때 구성 가능한 오류 처리 설정을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="da343-122">Configurable error handling settings for handling of duplicate keys, unknown keys, null keys, error limits, action upon error detection, and the error log file.</span></span>|  
|`ProcessingMode`|<span data-ttu-id="da343-123">인덱싱 및 집계를 처리 중에 수행할지 아니면 처리 후에 수행할지를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="da343-123">Indicates whether indexing and aggregating should occur during or after processing.</span></span> <span data-ttu-id="da343-124">사용할 수 있는 옵션은 Regular와 LazyAggregations입니다.</span><span class="sxs-lookup"><span data-stu-id="da343-124">Options are Regular and LazyAggregations.</span></span> <span data-ttu-id="da343-125">LazyAggregations를 사용하여 집계를 백그라운드 작업으로 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="da343-125">LazyAggregations can be used to run aggregation as a background task.</span></span>|  
|`ProcessingPriority`|<span data-ttu-id="da343-126">지연 집계 및 지연 인덱싱과 같이 백그라운드 작업 중의 큐브 처리 우선 순위를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="da343-126">Determines the processing priority of the cube during background operations, such as lazy aggregations and indexing.</span></span> <span data-ttu-id="da343-127">기본값은 **0**입니다.</span><span class="sxs-lookup"><span data-stu-id="da343-127">The default value is **0**.</span></span>|  
|`StorageLocation`|<span data-ttu-id="da343-128">측정값 그룹의 파일 시스템 스토리지 위치입니다.</span><span class="sxs-lookup"><span data-stu-id="da343-128">The file system storage location for the measure group.</span></span> <span data-ttu-id="da343-129">지정하지 않으면 측정값 그룹을 포함하는 큐브에서 위치가 상속됩니다.</span><span class="sxs-lookup"><span data-stu-id="da343-129">If none is specified, the location is inherited from the cube that contains the measure group.</span></span>|  
|`StorageMode`|<span data-ttu-id="da343-130">측정값 그룹에 대한 스토리지 모드입니다.</span><span class="sxs-lookup"><span data-stu-id="da343-130">The storage mode for the measure group.</span></span> <span data-ttu-id="da343-131">사용 가능한 값은 MOLAP, ROLAP 또는 HOLAP입니다.</span><span class="sxs-lookup"><span data-stu-id="da343-131">Available values are MOLAP, ROLAP, or HOLAP.</span></span>|  
|`Type`|<span data-ttu-id="da343-132">측정값 그룹의 유형을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="da343-132">Specifies the type of the measure group.</span></span>|  
  
  
