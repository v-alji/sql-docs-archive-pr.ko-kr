---
title: 파티션 처리 대상 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.partitionprocessingdest.f1
helpviewer_keywords:
- partitions [Analysis Services], processing
- Partition Processing destination [Integration Services]
- destinations [Integration Services], Partition Processing
ms.assetid: 36c592ff-3f78-4a58-b496-31c1c8eee131
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d32306328f7a0575e55397d5209b4767d0cf1bd6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648469"
---
# <a name="partition-processing-destination"></a><span data-ttu-id="a9769-102">파티션 처리 대상</span><span class="sxs-lookup"><span data-stu-id="a9769-102">Partition Processing Destination</span></span>
  <span data-ttu-id="a9769-103">파티션 처리 대상은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 파티션을 로드하고 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="a9769-103">The Partition Processing destination loads and processes an [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] partition.</span></span> <span data-ttu-id="a9769-104">파티션에 대한 자세한 내용은 [파티션&#40;Analysis Services - 다차원 데이터&#41;](https://docs.microsoft.com/analysis-services/multidimensional-models-olap-logical-cube-objects/partitions-analysis-services-multidimensional-data)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a9769-104">For more information about partitions, see [Partitions &#40;Analysis Services - Multidimensional Data&#41;](https://docs.microsoft.com/analysis-services/multidimensional-models-olap-logical-cube-objects/partitions-analysis-services-multidimensional-data).</span></span>  
  
 <span data-ttu-id="a9769-105">파티션 처리 대상에는 다음 기능이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="a9769-105">The Partition Processing destination includes the following features:</span></span>  
  
-   <span data-ttu-id="a9769-106">증분, 전체 또는 업데이트 처리를 수행하기 위한 옵션</span><span class="sxs-lookup"><span data-stu-id="a9769-106">Options to perform incremental, full, or update processing.</span></span>  
  
-   <span data-ttu-id="a9769-107">처리 중에 오류를 무시하거나 지정된 오류 개수 이후에 프로세스가 중지되는지 여부를 지정하기 위한 오류 구성</span><span class="sxs-lookup"><span data-stu-id="a9769-107">Error configuration, to specify whether processing ignores errors or stops after a specified number of errors.</span></span>  
  
-   <span data-ttu-id="a9769-108">입력 열을 파티션 열에 매핑</span><span class="sxs-lookup"><span data-stu-id="a9769-108">Mapping of input columns to partition columns.</span></span>  
  
 <span data-ttu-id="a9769-109">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 개체를 처리하는 방법에 대한 자세한 내용은 [처리 옵션 및 설정&#40;Analysis Services&#41;](https://docs.microsoft.com/analysis-services/multidimensional-models/processing-options-and-settings-analysis-services)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a9769-109">For more information about processing [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] objects, see [Processing Options and Settings &#40;Analysis Services&#41;](https://docs.microsoft.com/analysis-services/multidimensional-models/processing-options-and-settings-analysis-services).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a9769-110">여기에서 설명하는 태스크는 Analysis Services 테이블 형식 모델에 적용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a9769-110">Tasks described here do not apply to Analysis Services tabular models.</span></span>  <span data-ttu-id="a9769-111">테이블 형식 모델의 경우 입력 열을 파티션 열에 매핑할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a9769-111">You cannot map input columns to partition columns for tabular models.</span></span> <span data-ttu-id="a9769-112">대신 [Analysis Services Execute DDL Task](../control-flow/analysis-services-execute-ddl-task.md) 를 사용하여 파티션을 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a9769-112">You can instead use the Analysis Services Execute DDL task [Analysis Services Execute DDL Task](../control-flow/analysis-services-execute-ddl-task.md) to process the partition.</span></span>  
  
## <a name="configuration-of-the-partition-processing-destination"></a><span data-ttu-id="a9769-113">파티션 처리 대상 구성</span><span class="sxs-lookup"><span data-stu-id="a9769-113">Configuration of the Partition Processing Destination</span></span>  
 <span data-ttu-id="a9769-114">파티션 처리 대상은 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 연결 관리자를 사용하여 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 프로젝트에 연결하거나 대상에서 처리되는 큐브 및 파티션이 포함된 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="a9769-114">The Partition Processing destination uses an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] connection manager to connect to the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project or the instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] that contains the cubes and partitions the destination processes.</span></span> <span data-ttu-id="a9769-115">자세한 내용은 [Analysis Services Connection Manager](../connection-manager/analysis-services-connection-manager.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a9769-115">For more information, see [Analysis Services Connection Manager](../connection-manager/analysis-services-connection-manager.md).</span></span>  
  
 <span data-ttu-id="a9769-116">이 대상은 하나의 입력을 갖습니다.</span><span class="sxs-lookup"><span data-stu-id="a9769-116">This destination has one input.</span></span> <span data-ttu-id="a9769-117">오류 출력은 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a9769-117">It does not support an error output.</span></span>  
  
 <span data-ttu-id="a9769-118">[!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너를 사용하거나 프로그래밍 방식으로 속성을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a9769-118">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="a9769-119">**파티션 처리 대상 편집기** 대화 상자에서 설정할 수 있는 속성에 대한 자세한 내용을 보려면 다음 항목 중 하나를 클릭하십시오.</span><span class="sxs-lookup"><span data-stu-id="a9769-119">For more information about the properties that you can set in the Partition Processing **Destination Editor** dialog box, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="a9769-120">파티션 처리 대상 편집기&#40;연결 관리자 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="a9769-120">Partition Processing Destination Editor &#40;Connection Manager Page&#41;</span></span>](../partition-processing-destination-editor-connection-manager-page.md)  
  
-   [<span data-ttu-id="a9769-121">파티션 처리 대상 편집기&#40;매핑 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="a9769-121">Partition Processing Destination Editor &#40;Mappings Page&#41;</span></span>](../partition-processing-destination-editor-mappings-page.md)  
  
-   [<span data-ttu-id="a9769-122">파티션 처리 대상 편집기&#40;고급 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="a9769-122">Partition Processing Destination Editor &#40;Advanced Page&#41;</span></span>](../partition-processing-destination-editor-advanced-page.md)  
  
 <span data-ttu-id="a9769-123">**고급 편집기** 대화 상자에는 프로그래밍 방식으로 설정할 수 있는 속성이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="a9769-123">The **Advanced Editor** dialog box reflects the properties that can be set programmatically.</span></span> <span data-ttu-id="a9769-124">**고급 편집기** 대화 상자를 사용하거나 프로그래밍 방식으로 설정할 수 있는 속성에 대한 자세한 내용을 보려면 다음 항목 중 하나를 클릭하세요.</span><span class="sxs-lookup"><span data-stu-id="a9769-124">For more information about the properties that you can set in the **Advanced Editor** dialog box or programmatically, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="a9769-125">Common Properties</span><span class="sxs-lookup"><span data-stu-id="a9769-125">Common Properties</span></span>](../common-properties.md)  
  
-   [<span data-ttu-id="a9769-126">파티션 처리 대상 사용자 지정 속성</span><span class="sxs-lookup"><span data-stu-id="a9769-126">Partition Processing Destination Custom Properties</span></span>](partition-processing-destination-custom-properties.md)  
  
 <span data-ttu-id="a9769-127">속성을 설정하는 방법에 대한 자세한 내용은 [데이터 흐름 구성 요소의 속성 설정](set-the-properties-of-a-data-flow-component.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a9769-127">For more information about how to set the properties, see [Set the Properties of a Data Flow Component](set-the-properties-of-a-data-flow-component.md).</span></span>  
  
  
