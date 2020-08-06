---
title: 데이터베이스 차원 속성 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- metadata [Analysis Services]
- dimensions [Analysis Services], characteristics
- properties [Analysis Services], dimensions
ms.assetid: 075548ef-08a3-413c-8ee0-4a074c276fcc
author: minewiskan
ms.author: owend
ms.openlocfilehash: 504e190f4c513a8c999c4d7d7ab9eaabb83298c3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653027"
---
# <a name="database-dimension-properties"></a><span data-ttu-id="8f31d-102">데이터베이스 차원 속성</span><span class="sxs-lookup"><span data-stu-id="8f31d-102">Database Dimension Properties</span></span>
  <span data-ttu-id="8f31d-103">에서 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 차원의 특성은 다양 한 차원 속성의 설정 및 차원에 포함 된 특성이 나 계층에 따라 차원의 메타 데이터에 의해 정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8f31d-103">In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], the characteristics of a dimension are defined by the metadata for the dimension, based on the settings of various dimension properties, and on the attributes or hierarchies that are contained by the dimension.</span></span> <span data-ttu-id="8f31d-104">다음 표에서는 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]의 차원 속성을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="8f31d-104">The following table describes the dimension properties in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span>  
  
|<span data-ttu-id="8f31d-105">속성</span><span class="sxs-lookup"><span data-stu-id="8f31d-105">Property</span></span>|<span data-ttu-id="8f31d-106">Description</span><span class="sxs-lookup"><span data-stu-id="8f31d-106">Description</span></span>|  
|--------------|-----------------|  
|`AttributeAllMemberName`|<span data-ttu-id="8f31d-107">차원의 특성에 대한 All 멤버의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8f31d-107">Specifies the name of the All member for attributes in a dimension.</span></span>|  
|`Collation`|<span data-ttu-id="8f31d-108">차원에 사용되는 데이터 정렬을 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="8f31d-108">Determines the collation used by the dimension.</span></span>|  
|`CurrentStorageMode`|<span data-ttu-id="8f31d-109">차원의 현재 스토리지 모드를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="8f31d-109">Contains the current storage mode for the dimension.</span></span>|  
|`DependsOnDimension`|<span data-ttu-id="8f31d-110">차원이 종속되는 다른 차원이 있는 경우 이 차원의 ID를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="8f31d-110">Contains the ID of another dimension on which the dimension depends, if any.</span></span>|  
|`Description`|<span data-ttu-id="8f31d-111">차원에 대한 설명을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="8f31d-111">Contains the description of the dimension.</span></span>|  
|`ErrorConfiguration`|<span data-ttu-id="8f31d-112">중복 키, 알 수 없는 키, 오류 제한, 오류 감지 시 수행 동작, 오류 로그 파일 및 Null 키 등에 대한 구성 가능한 오류 처리 설정을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="8f31d-112">Configurable error handling settings for handling of duplicate keys, unknown keys, error limits, action upon error detection, error log file, and null key handling.</span></span>|  
|`ID`|<span data-ttu-id="8f31d-113">차원의 고유 ID를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="8f31d-113">Contains the unique identifier (ID) of the dimension.</span></span>|  
|`Language`|<span data-ttu-id="8f31d-114">차원의 기본 언어를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8f31d-114">Specifies the default language for the dimension.</span></span>|  
|`MdxMissingMemberMode`|<span data-ttu-id="8f31d-115">MDX(Multidimensional Expressions) 문에 대해 누락된 멤버가 처리되는 방식을 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="8f31d-115">Determines how missing members are handled for Multidimensional Expressions (MDX) statements.</span></span>|  
|`MiningModelID`|<span data-ttu-id="8f31d-116">데이터 마이닝 차원이 연결된 마이닝 모델의 ID를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="8f31d-116">Contains the ID of the mining model with which the data mining dimension is associated.</span></span> <span data-ttu-id="8f31d-117">차원이 마이닝 모델 차원인 경우에만 이 속성을 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8f31d-117">This property is applicable only if the dimension is a mining model dimension.</span></span>|  
|`Name`|<span data-ttu-id="8f31d-118">차원의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8f31d-118">Specifies the name of the dimension.</span></span>|  
|`ProactiveCaching`|<span data-ttu-id="8f31d-119">차원의 자동 관리 캐싱 설정을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="8f31d-119">Defines the proactive cache settings for the dimension.</span></span>|  
|`ProcessingGroup`|<span data-ttu-id="8f31d-120">처리 그룹을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8f31d-120">Specifies the processing group.</span></span> <span data-ttu-id="8f31d-121">ByAttribute 또는 ByTable 값을 지정할 수 있으며</span><span class="sxs-lookup"><span data-stu-id="8f31d-121">Values are ByAttribute or ByTable.</span></span> <span data-ttu-id="8f31d-122">기본값은 `ByAttribute`입니다.</span><span class="sxs-lookup"><span data-stu-id="8f31d-122">Default is `ByAttribute`.</span></span>|  
|`ProcessingMode`|<span data-ttu-id="8f31d-123">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]에서 인덱싱 및 집계를 처리 중에 수행할지 아니면 처리 후에 수행할지를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="8f31d-123">Indicates whether [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] should index and aggregate during or after processing.</span></span>|  
|`ProcessingPriority`|<span data-ttu-id="8f31d-124">지연 집계, 인덱싱 또는 클러스터링과 같은 백그라운드 작업을 수행하는 동안 차원의 처리 우선 순위를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="8f31d-124">Determines the processing priority of the dimension during background operations such as lazy aggregation, indexing, or clustering.</span></span>|  
|`Source`|<span data-ttu-id="8f31d-125">차원이 바인딩되는 데이터 원본 뷰를 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="8f31d-125">Identifies the data source view to which the dimension is bound.</span></span>|  
|`StorageMode`|<span data-ttu-id="8f31d-126">차원의 스토리지 모드를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="8f31d-126">Determines the storage mode for the dimension.</span></span>|  
|`Type`|<span data-ttu-id="8f31d-127">차원의 유형을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8f31d-127">Specifies the type of the dimension.</span></span>|  
|`UnknownMember`|<span data-ttu-id="8f31d-128">알 수 없는 멤버의 표시 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="8f31d-128">Indicates whether the unknown member is visible.</span></span>|  
|`UnknownMemberName`|<span data-ttu-id="8f31d-129">차원의 알 수 없는 멤버에 대한 캡션을 차원의 기본 언어로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8f31d-129">Specifies the caption, in the default language of the dimension, for the unknown member of the dimension.</span></span>|  
|`WriteEnabled`|<span data-ttu-id="8f31d-130">보안 권한에 따라 차원 쓰기 저장(writeback)을 사용할 수 있는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="8f31d-130">Indicates whether dimension writebacks are available (subject to security permissions).</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="8f31d-131">Null 값 및 다른 데이터 무결성 문제를 처리할 때 ErrorConfiguration 및 UnknownMember 속성에 대 한 값을 설정 하는 방법에 대 한 자세한 내용은 [Analysis Services 2005에서 데이터 무결성 문제 처리](https://go.microsoft.com/fwlink/?LinkId=81891)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="8f31d-131">For more information about setting values for the ErrorConfiguration and UnknownMember properties when working with null values and other data integrity issues, see [Handling Data Integrity Issues in Analysis Services 2005](https://go.microsoft.com/fwlink/?LinkId=81891).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f31d-132">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8f31d-132">See Also</span></span>  
 <span data-ttu-id="8f31d-133">[특성 및 특성 계층](attributes-and-attribute-hierarchies.md) </span><span class="sxs-lookup"><span data-stu-id="8f31d-133">[Attributes and Attribute Hierarchies](attributes-and-attribute-hierarchies.md) </span></span>  
 <span data-ttu-id="8f31d-134">[사용자 계층](user-hierarchies.md) </span><span class="sxs-lookup"><span data-stu-id="8f31d-134">[User Hierarchies](user-hierarchies.md) </span></span>  
 <span data-ttu-id="8f31d-135">[차원 관계](../multidimensional-models-olap-logical-cube-objects/dimension-relationships.md) </span><span class="sxs-lookup"><span data-stu-id="8f31d-135">[Dimension Relationships](../multidimensional-models-olap-logical-cube-objects/dimension-relationships.md) </span></span>  
 [<span data-ttu-id="8f31d-136">차원&#40;Analysis Services - 다차원 데이터&#41;</span><span class="sxs-lookup"><span data-stu-id="8f31d-136">Dimensions &#40;Analysis Services - Multidimensional Data&#41;</span></span>](dimensions-analysis-services-multidimensional-data.md)  
  
  
