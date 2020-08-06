---
title: 경로 속성 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- paths [Integration Services], properties
ms.assetid: 89b1e347-9579-4f6b-af74-c6519ea08eea
author: chugugrace
ms.author: chugu
ms.openlocfilehash: ca263b866fb6d5d7ceb6352f708f387d79cad4f7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647091"
---
# <a name="path-properties"></a><span data-ttu-id="68a13-102">경로 속성</span><span class="sxs-lookup"><span data-stu-id="68a13-102">Path Properties</span></span>
  <span data-ttu-id="68a13-103">개체 모델의 데이터 흐름 개체에는 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 구성 요소 수준, 입/출력, 입력 열 및 출력 열 수준에서 공통 속성과 사용자 지정 속성이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="68a13-103">The data flow objects in the [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] object model have common properties and custom properties at the level of the component, inputs and outputs, and input columns and output columns.</span></span> <span data-ttu-id="68a13-104">많은 속성은 데이터 흐름 엔진이 런타임에 할당하는 읽기 전용 값을 갖습니다.</span><span class="sxs-lookup"><span data-stu-id="68a13-104">Many properties have read-only values that are assigned at run time by the data flow engine.</span></span>  
  
 <span data-ttu-id="68a13-105">이 항목은 데이터 흐름 개체를 연결하는 경로의 사용자 지정 속성을 나열하고 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="68a13-105">This topic lists and describes the custom properties of the paths that connect data flow objects.</span></span>  
  
## <a name="path-properties"></a><span data-ttu-id="68a13-106">경로 속성</span><span class="sxs-lookup"><span data-stu-id="68a13-106">Path Properties</span></span>  
 <span data-ttu-id="68a13-107">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 개체 모델에서 데이터 흐름 구성 요소를 연결하는 경로는 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSPath100> 인터페이스를 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="68a13-107">In the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] object model, a path that connects components in the data flow implements the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSPath100> interface.</span></span>  
  
 <span data-ttu-id="68a13-108">다음 표에서는 데이터 흐름 경로의 구성 가능한 속성에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="68a13-108">The following table describes the configurable properties of the paths in a data flow.</span></span> <span data-ttu-id="68a13-109">데이터 흐름 엔진은 여기에 나열되지 않은 추가 읽기 전용 속성에도 값을 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="68a13-109">The data flow engine also assigns values to additional read-only properties that are not listed here.</span></span>  
  
|<span data-ttu-id="68a13-110">속성 이름</span><span class="sxs-lookup"><span data-stu-id="68a13-110">Property name</span></span>|<span data-ttu-id="68a13-111">데이터 형식</span><span class="sxs-lookup"><span data-stu-id="68a13-111">Data Type</span></span>|<span data-ttu-id="68a13-112">Description</span><span class="sxs-lookup"><span data-stu-id="68a13-112">Description</span></span>|  
|-------------------|---------------|-----------------|  
|<span data-ttu-id="68a13-113">PathAnnotation</span><span class="sxs-lookup"><span data-stu-id="68a13-113">PathAnnotation</span></span>|<span data-ttu-id="68a13-114">Integer(열거형)</span><span class="sxs-lookup"><span data-stu-id="68a13-114">Integer (enumeration)</span></span>|<span data-ttu-id="68a13-115">디자이너 화면에 주석을 경로와 함께 표시할지 여부를 나타내는 값입니다.</span><span class="sxs-lookup"><span data-stu-id="68a13-115">A value that indicates whether an annotation should be displayed with the path on the designer surface.</span></span> <span data-ttu-id="68a13-116">가능한 값은 `AsNeeded`, `SourceName`, `PathName` 및 `Never`입니다.</span><span class="sxs-lookup"><span data-stu-id="68a13-116">The possible values are `AsNeeded`, `SourceName`, `PathName`, and `Never`.</span></span> <span data-ttu-id="68a13-117">기본값은 `AsNeeded`입니다.</span><span class="sxs-lookup"><span data-stu-id="68a13-117">The default value is `AsNeeded`.</span></span>|  
|<span data-ttu-id="68a13-118">DestinationName</span><span class="sxs-lookup"><span data-stu-id="68a13-118">DestinationName</span></span>|<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSInput100>|<span data-ttu-id="68a13-119">경로에 연결된 입력입니다.</span><span class="sxs-lookup"><span data-stu-id="68a13-119">The input associated with the path.</span></span>|  
|<span data-ttu-id="68a13-120">SourceName</span><span class="sxs-lookup"><span data-stu-id="68a13-120">SourceName</span></span>|<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutput100>|<span data-ttu-id="68a13-121">경로에 연결된 출력입니다.</span><span class="sxs-lookup"><span data-stu-id="68a13-121">The output associated with the path.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="68a13-122">참고 항목</span><span class="sxs-lookup"><span data-stu-id="68a13-122">See Also</span></span>  
 <span data-ttu-id="68a13-123">[Integration Services 경로](data-flow/integration-services-paths.md) </span><span class="sxs-lookup"><span data-stu-id="68a13-123">[Integration Services Paths](data-flow/integration-services-paths.md) </span></span>  
 <span data-ttu-id="68a13-124">[공용 속성](../../2014/integration-services/common-properties.md) </span><span class="sxs-lookup"><span data-stu-id="68a13-124">[Common Properties](../../2014/integration-services/common-properties.md) </span></span>  
 <span data-ttu-id="68a13-125">[변환 사용자 지정 속성](data-flow/transformations/transformation-custom-properties.md) </span><span class="sxs-lookup"><span data-stu-id="68a13-125">[Transformation Custom Properties](data-flow/transformations/transformation-custom-properties.md) </span></span>  
 [<span data-ttu-id="68a13-126">식을 사용하여 설정할 수 있는 데이터 흐름 속성</span><span class="sxs-lookup"><span data-stu-id="68a13-126">Data Flow Properties that Can Be Set by Using Expressions</span></span>](../../2014/integration-services/data-flow-properties-that-can-be-set-by-using-expressions.md)  
  
  
