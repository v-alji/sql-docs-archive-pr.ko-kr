---
title: 차원 처리 대상 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.dimensionprocessingdest.f1
helpviewer_keywords:
- Dimension Processing destination
- loading dimensions
- destinations [Integration Services], Dimension Processing
- dimensions [Analysis Services], processing
ms.assetid: 4c49bb95-7259-42f4-a785-bb6aaf5f8566
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 61cde87ac4fa5fcb1352491d787674447dd404b3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648489"
---
# <a name="dimension-processing-destination"></a><span data-ttu-id="25c58-102">차원 처리 대상</span><span class="sxs-lookup"><span data-stu-id="25c58-102">Dimension Processing Destination</span></span>
  <span data-ttu-id="25c58-103">차원 처리 대상은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 차원을 로드하고 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="25c58-103">The Dimension Processing destination loads and processes an [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] dimension.</span></span> <span data-ttu-id="25c58-104">차원에 대한 자세한 내용은 [차원&#40;Analysis Services - 다차원 데이터&#41;](https://docs.microsoft.com/analysis-services/multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="25c58-104">For more information about dimensions, see [Dimensions &#40;Analysis Services - Multidimensional Data&#41;](https://docs.microsoft.com/analysis-services/multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data).</span></span>  
  
 <span data-ttu-id="25c58-105">차원 처리 대상에는 다음 기능이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="25c58-105">The Dimension Processing destination includes the following features:</span></span>  
  
-   <span data-ttu-id="25c58-106">증분, 전체 또는 업데이트 처리를 수행하기 위한 옵션</span><span class="sxs-lookup"><span data-stu-id="25c58-106">Options to perform incremental, full, or update processing.</span></span>  
  
-   <span data-ttu-id="25c58-107">차원 처리 중에 오류를 무시하거나 지정된 오류 개수 이후에 프로세스가 중지되는지 여부를 지정하기 위한 오류 구성</span><span class="sxs-lookup"><span data-stu-id="25c58-107">Error configuration, to specify whether dimension processing ignores errors or stops after a specified number of errors.</span></span>  
  
-   <span data-ttu-id="25c58-108">입력 열을 차원 테이블의 열로 매핑</span><span class="sxs-lookup"><span data-stu-id="25c58-108">Mapping of input columns to columns in dimension tables.</span></span>  
  
 <span data-ttu-id="25c58-109">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 개체를 처리하는 방법에 대한 자세한 내용은 [처리 옵션 및 설정&#40;Analysis Services&#41;](https://docs.microsoft.com/analysis-services/multidimensional-models/processing-options-and-settings-analysis-services)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="25c58-109">For more information about processing [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] objects, see [Processing Options and Settings &#40;Analysis Services&#41;](https://docs.microsoft.com/analysis-services/multidimensional-models/processing-options-and-settings-analysis-services).</span></span>  
  
## <a name="configuration-of-the-dimension-processing-destination"></a><span data-ttu-id="25c58-110">차원 처리 대상 구성</span><span class="sxs-lookup"><span data-stu-id="25c58-110">Configuration of the Dimension Processing Destination</span></span>  
 <span data-ttu-id="25c58-111">차원 처리 대상은 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 연결 관리자를 사용하여 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 프로젝트에 연결하거나 대상에서 처리되는 차원이 포함된 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="25c58-111">The Dimension Processing destination uses an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] connection manager to connect to the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project or the instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] that contains the dimensions the destination processes.</span></span> <span data-ttu-id="25c58-112">자세한 내용은 [Analysis Services Connection Manager](../connection-manager/analysis-services-connection-manager.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="25c58-112">For more information, see [Analysis Services Connection Manager](../connection-manager/analysis-services-connection-manager.md).</span></span>  
  
 <span data-ttu-id="25c58-113">이 대상은 하나의 입력을 갖습니다.</span><span class="sxs-lookup"><span data-stu-id="25c58-113">This destination has one input.</span></span> <span data-ttu-id="25c58-114">오류 출력은 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="25c58-114">It does not support an error output.</span></span>  
  
 <span data-ttu-id="25c58-115">[!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너를 사용하거나 프로그래밍 방식으로 속성을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="25c58-115">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="25c58-116">**차원 처리 대상 편집기** 대화 상자에서 설정할 수 있는 속성에 대한 자세한 내용을 보려면 다음 항목 중 하나를 클릭하십시오.</span><span class="sxs-lookup"><span data-stu-id="25c58-116">For more information about the properties that you can set in the **Dimension Processing Destination Editor** dialog box, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="25c58-117">차원 처리 대상 편집기&#40;연결 관리자 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="25c58-117">Dimension Processing Destination Editor &#40;Connection Manager Page&#41;</span></span>](../dimension-processing-destination-editor-connection-manager-page.md)  
  
-   [<span data-ttu-id="25c58-118">차원 처리 대상 편집기&#40;매핑 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="25c58-118">Dimension Processing Destination Editor &#40;Mappings Page&#41;</span></span>](../dimension-processing-destination-editor-mappings-page.md)  
  
-   [<span data-ttu-id="25c58-119">차원 처리 대상 편집기&#40;고급 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="25c58-119">Dimension Processing Destination Editor &#40;Advanced Page&#41;</span></span>](../dimension-processing-destination-editor-advanced-page.md)  
  
 <span data-ttu-id="25c58-120">**고급 편집기** 대화 상자에는 프로그래밍 방식으로 설정할 수 있는 속성이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="25c58-120">The **Advanced Editor** dialog box reflects the properties that can be set programmatically.</span></span> <span data-ttu-id="25c58-121">**고급 편집기** 대화 상자를 사용하거나 프로그래밍 방식으로 설정할 수 있는 속성에 대한 자세한 내용을 보려면 다음 항목 중 하나를 클릭하십시오.</span><span class="sxs-lookup"><span data-stu-id="25c58-121">For more information about the properties that you can set in the **Advanced Editor** dialog box or programmatically, click one of the following topic:</span></span>  
  
-   [<span data-ttu-id="25c58-122">Common Properties</span><span class="sxs-lookup"><span data-stu-id="25c58-122">Common Properties</span></span>](../common-properties.md)  
  
 <span data-ttu-id="25c58-123">속성을 설정하는 방법에 대한 자세한 내용은 [데이터 흐름 구성 요소의 속성 설정](set-the-properties-of-a-data-flow-component.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="25c58-123">For more information about how to set the properties, see [Set the Properties of a Data Flow Component](set-the-properties-of-a-data-flow-component.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25c58-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="25c58-124">See Also</span></span>  
 <span data-ttu-id="25c58-125">[데이터 흐름](data-flow.md) </span><span class="sxs-lookup"><span data-stu-id="25c58-125">[Data Flow](data-flow.md) </span></span>  
 [<span data-ttu-id="25c58-126">Integration Services 변환</span><span class="sxs-lookup"><span data-stu-id="25c58-126">Integration Services Transformations</span></span>](transformations/integration-services-transformations.md)  
  
  
