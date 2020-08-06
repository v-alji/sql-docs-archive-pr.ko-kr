---
title: 큐브 속성 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- Collation property
- ID property
- ErrorConfiguration property
- cubes [Analysis Services], properties
- Description property
- DefaultMeasure property
- ProcessingMode property
- AggregationPrefix property
- EstimatedRows property
- Visible property
- StorageLocation property
- StorageMode property
- ScriptErrorHandlingMode property
- Source property
- ScriptCacheProcessingMode property
- Language property
- Name property
- properties [Analysis Services], cubes
- ProcessingPriority property
- ProactiveCaching property
ms.assetid: 72ca3387-620d-4473-8e23-7fe1f2b3d5bf
author: minewiskan
ms.author: owend
ms.openlocfilehash: 27d4202774107795eaddf76c27e21010d534d977
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647307"
---
# <a name="cube-properties"></a><span data-ttu-id="b1873-102">큐브 속성</span><span class="sxs-lookup"><span data-stu-id="b1873-102">Cube Properties</span></span>
  <span data-ttu-id="b1873-103">큐브에는 큐브 차원 동작에 영향을 주기 위해 설정할 수 있는 많은 속성이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b1873-103">Cubes have a number of properties that you can set to affect cube-wide behavior.</span></span> <span data-ttu-id="b1873-104">다음 표에서는 이러한 속성을 요약하여 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="b1873-104">These properties are summarized in the following table.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b1873-105">일부 속성은 큐브를 만들 때 자동으로 설정되며 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b1873-105">Some properties are set automatically when the cube is created and cannot be changed.</span></span>  
  
 <span data-ttu-id="b1873-106">큐브 속성을 설정 하는 방법에 대 한 자세한 내용은 [큐브 디자이너 &#40;Analysis Services 다차원 데이터&#41;](../cube-designer-analysis-services-multidimensional-data.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="b1873-106">For more information about how to set cube properties, see [Cube Designer &#40;Analysis Services - Multidimensional Data&#41;](../cube-designer-analysis-services-multidimensional-data.md).</span></span>  
  
|<span data-ttu-id="b1873-107">속성</span><span class="sxs-lookup"><span data-stu-id="b1873-107">Property</span></span>|<span data-ttu-id="b1873-108">Description</span><span class="sxs-lookup"><span data-stu-id="b1873-108">Description</span></span>|  
|--------------|-----------------|  
|`AggregationPrefix`|<span data-ttu-id="b1873-109">집계 이름에 사용되는 공통 접두사를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b1873-109">Specifies the common prefix that is used for aggregation names.</span></span>|  
|`Collation`|<span data-ttu-id="b1873-110">LCID(로캘 ID)와 비교 플래그를 밑줄로 구분하여 지정합니다(예: Latin1_General_C1_AS).</span><span class="sxs-lookup"><span data-stu-id="b1873-110">Specifies the locale identifier (LCID) and the comparison flag, separated by an underscore: for example, Latin1_General_C1_AS.</span></span>|  
|`DefaultMeasure`|<span data-ttu-id="b1873-111">큐브의 기본 측정값을 정의하는 MDX(Multidimensional Expressions) 식을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="b1873-111">Contains a Multidimensional Expressions (MDX) expression that defines the default measure for the cube.</span></span>|  
|`Description`|<span data-ttu-id="b1873-112">큐브에 대한 설명을 제공합니다. 이 설명은 클라이언트 애플리케이션에 노출될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b1873-112">Provides a description of the cube, which may be exposed in client applications.</span></span>|  
|`ErrorConfiguration`|<span data-ttu-id="b1873-113">중복 키, 알 수 없는 키, 오류 제한, 오류 감지 시 수행 동작, 오류 로그 파일 및 Null 키 처리 등에 대한 구성 가능한 오류 처리 설정을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="b1873-113">Contains configurable error handling settings for handling of duplicate keys, unknown keys, error limits, action upon error detection, error log file, and null key handling.</span></span>|  
|`EstimatedRows`|<span data-ttu-id="b1873-114">큐브의 예상 행 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b1873-114">Specifies the number of estimated rows in the cube.</span></span>|  
|`ID`|<span data-ttu-id="b1873-115">큐브의 ID(고유 식별자)를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="b1873-115">Contains the unique identifier (ID) of the cube.</span></span>|  
|`Language`|<span data-ttu-id="b1873-116">큐브의 기본 언어 식별자를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b1873-116">Specifies the default language identifier of the cube.</span></span>|  
|`Name`|<span data-ttu-id="b1873-117">큐브의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b1873-117">Specifies the user-friendly name of the cube.</span></span>|  
|`ProactiveCaching`|<span data-ttu-id="b1873-118">큐브에 대한 자동 관리 캐싱 설정을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="b1873-118">Defines proactive cache settings for the cube.</span></span>|  
|`ProcessingMode`|<span data-ttu-id="b1873-119">인덱싱 및 집계를 처리 중에 수행할지 아니면 처리 후에 수행할지를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="b1873-119">Indicates whether indexing and aggregating should occur during or after processing.</span></span> <span data-ttu-id="b1873-120">옵션은 **regular** 또는 `lazy` 입니다.</span><span class="sxs-lookup"><span data-stu-id="b1873-120">Options are **regular** or `lazy`.</span></span>|  
|`ProcessingPriority`|<span data-ttu-id="b1873-121">지연 집계 및 지연 인덱싱과 같이 백그라운드 작업 중의 큐브 처리 우선 순위를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="b1873-121">Determines the processing priority of the cube during background operations, such as lazy aggregations and indexing.</span></span> <span data-ttu-id="b1873-122">기본값은 **0**입니다.</span><span class="sxs-lookup"><span data-stu-id="b1873-122">The default value is **0**.</span></span>|  
|`ScriptCacheProcessingMode`|<span data-ttu-id="b1873-123">스크립트 캐시를 처리 중에 작성할지, 아니면 처리 후에 작성할지를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="b1873-123">Indicates whether the script cache should be built during or after processing.</span></span> <span data-ttu-id="b1873-124">옵션은 **일반** 및 `lazy` 입니다.</span><span class="sxs-lookup"><span data-stu-id="b1873-124">Options are **regular** and `lazy`.</span></span>|  
|`ScriptErrorHandlingMode`|<span data-ttu-id="b1873-125">오류 처리를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="b1873-125">Determines error handling.</span></span> <span data-ttu-id="b1873-126">사용할 수 있는 옵션은 `IgnoreNone` 또는 `IgnoreAll`입니다.</span><span class="sxs-lookup"><span data-stu-id="b1873-126">Options are `IgnoreNone` or `IgnoreAll`</span></span>|  
|`Source`|<span data-ttu-id="b1873-127">큐브에 사용된 데이터 원본 뷰를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="b1873-127">Displays the data source view used for the cube.</span></span>|  
|`StorageLocation`|<span data-ttu-id="b1873-128">큐브의 파일 시스템 스토리지 위치를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b1873-128">Specifies the file system storage location for the cube.</span></span> <span data-ttu-id="b1873-129">아무 위치도 지정하지 않으면 큐브 개체를 포함하는 데이터베이스에서 위치를 상속받습니다.</span><span class="sxs-lookup"><span data-stu-id="b1873-129">If none is specified, the location is inherited from the database that contains the cube object.</span></span>|  
|`StorageMode`|<span data-ttu-id="b1873-130">큐브의 스토리지 모드를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b1873-130">Specifies the storage mode for the cube.</span></span> <span data-ttu-id="b1873-131">값은 `MOLAP` , `ROLAP` 또는입니다.`HOLAP``.`</span><span class="sxs-lookup"><span data-stu-id="b1873-131">Values are `MOLAP`, `ROLAP`, or `HOLAP``.`</span></span>|  
|`Visible`|<span data-ttu-id="b1873-132">큐브의 표시 여부를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="b1873-132">Determines the visibility of the cube.</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="b1873-133">Null 값 및 다른 데이터 무결성 문제를 처리할 때 ErrorConfiguration 속성의 값을 설정 하는 방법에 대 한 자세한 내용은 [Analysis Services 2005에서 데이터 무결성 문제 처리](https://go.microsoft.com/fwlink/?LinkId=81891)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="b1873-133">For more information about setting values for the ErrorConfiguration property when working with null values and other data integrity issues, see [Handling Data Integrity Issues in Analysis Services 2005](https://go.microsoft.com/fwlink/?LinkId=81891).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1873-134">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b1873-134">See Also</span></span>  
 [<span data-ttu-id="b1873-135">자동 관리 캐싱 &#40;파티션&#41;</span><span class="sxs-lookup"><span data-stu-id="b1873-135">Proactive Caching &#40;Partitions&#41;</span></span>](partitions-proactive-caching.md)  
  
  
