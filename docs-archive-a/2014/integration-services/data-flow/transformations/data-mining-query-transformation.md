---
title: 데이터 마이닝 쿼리 변환 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.dataminingquerytrans.f1
helpviewer_keywords:
- Data Mining Query transformation
- prediction queries [Integration Services]
ms.assetid: 7960133b-a3e1-48af-ba43-55ed78c38e71
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 278fdc3b1abd38b63f01e967e28d11983a09e682
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646567"
---
# <a name="data-mining-query-transformation"></a><span data-ttu-id="5c6ef-102">데이터 마이닝 쿼리 변환</span><span class="sxs-lookup"><span data-stu-id="5c6ef-102">Data Mining Query Transformation</span></span>
  <span data-ttu-id="5c6ef-103">데이터 마이닝 쿼리 변환은 데이터 마이닝 모델과 비교해서 예측 쿼리를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="5c6ef-103">The Data Mining Query transformation performs prediction queries against data mining models.</span></span> <span data-ttu-id="5c6ef-104">이 변환에는 DMX(Data Mining Extensions) 쿼리를 만들기 위한 쿼리 작성기가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5c6ef-104">This transformation contains a query builder for creating Data Mining Extensions (DMX) queries.</span></span> <span data-ttu-id="5c6ef-105">쿼리 작성기를 사용하면 DMX 언어를 사용하는 기존 마이닝 모델과 비교해서 변환 입력 데이터를 평가하는 사용자 지정 문을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5c6ef-105">The query builder lets you create custom statements for evaluating the transformation input data against an existing mining model using the DMX language.</span></span> <span data-ttu-id="5c6ef-106">자세한 내용은 [DMX&#40;Data Mining Extensions&#41; 참조](/sql/dmx/data-mining-extensions-dmx-reference)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5c6ef-106">For more information, see [Data Mining Extensions &#40;DMX&#41; Reference](/sql/dmx/data-mining-extensions-dmx-reference).</span></span>  
  
 <span data-ttu-id="5c6ef-107">모델이 동일한 데이터 마이닝 구조를 기반으로 하는 경우 하나의 변환에서 여러 개의 예측 쿼리를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5c6ef-107">One transformation can execute multiple prediction queries if the models are built on the same data mining structure.</span></span> <span data-ttu-id="5c6ef-108">자세한 내용은 [데이터 마이닝 쿼리 인터페이스](https://docs.microsoft.com/analysis-services/data-mining/data-mining-query-tools)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="5c6ef-108">For more information, see [Data Mining Query Interfaces](https://docs.microsoft.com/analysis-services/data-mining/data-mining-query-tools).</span></span>  
  
## <a name="configuration-of-the-data-mining-query-transformation"></a><span data-ttu-id="5c6ef-109">데이터 마이닝 쿼리 변환 구성</span><span class="sxs-lookup"><span data-stu-id="5c6ef-109">Configuration of the Data Mining Query Transformation</span></span>  
 <span data-ttu-id="5c6ef-110">데이터 마이닝 쿼리 변환은 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 연결 관리자를 사용하여 마이닝 구조와 마이닝 모델이 포함된 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 의 인스턴스나 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 프로젝트에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="5c6ef-110">The Data Mining Query transformation uses an [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] connection manager to connect to the [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] project or the instance of [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] that contains the mining structure and mining models.</span></span> <span data-ttu-id="5c6ef-111">자세한 내용은 [Analysis Services Connection Manager](../../connection-manager/analysis-services-connection-manager.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5c6ef-111">For more information, see [Analysis Services Connection Manager](../../connection-manager/analysis-services-connection-manager.md).</span></span>  
  
 <span data-ttu-id="5c6ef-112">이 변환은 하나의 입력과 하나의 출력을 가지며</span><span class="sxs-lookup"><span data-stu-id="5c6ef-112">This transformation has one input and one output.</span></span> <span data-ttu-id="5c6ef-113">오류 출력은 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5c6ef-113">It does not support an error output.</span></span>  
  
 <span data-ttu-id="5c6ef-114">[!INCLUDE[ssIS](../../../includes/ssis-md.md)] 디자이너를 사용하거나 프로그래밍 방식으로 속성을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5c6ef-114">You can set properties through [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="5c6ef-115">**데이터 마이닝 쿼리 변환 편집기** 대화 상자에서 설정할 수 있는 속성에 대한 자세한 내용을 보려면 다음 항목 중 하나를 클릭하십시오.</span><span class="sxs-lookup"><span data-stu-id="5c6ef-115">For more information about the properties that you can set in the **Data Mining Query Transformation Editor** dialog box, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="5c6ef-116">데이터 마이닝 쿼리 변환 편집기&#40;마이닝 모델 탭&#41;</span><span class="sxs-lookup"><span data-stu-id="5c6ef-116">Data Mining Query Transformation Editor &#40;Mining Model Tab&#41;</span></span>](../../data-mining-query-transformation-editor-mining-model-tab.md)  
  
-   [<span data-ttu-id="5c6ef-117">데이터 마이닝 쿼리 변환 편집기&#40;마이닝 모델 탭&#41;</span><span class="sxs-lookup"><span data-stu-id="5c6ef-117">Data Mining Query Transformation Editor &#40;Mining Model Tab&#41;</span></span>](../../data-mining-query-transformation-editor-mining-model-tab.md)  
  
 <span data-ttu-id="5c6ef-118">**고급 편집기** 대화 상자에는 프로그래밍 방식으로 설정할 수 있는 속성이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="5c6ef-118">The **Advanced Editor** dialog box reflects the properties that can be set programmatically.</span></span> <span data-ttu-id="5c6ef-119">**고급 편집기** 대화 상자를 사용하거나 프로그래밍 방식으로 설정할 수 있는 속성에 대한 자세한 내용을 보려면 다음 항목 중 하나를 클릭하세요.</span><span class="sxs-lookup"><span data-stu-id="5c6ef-119">For more information about the properties that you can set in the **Advanced Editor** dialog box or programmatically, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="5c6ef-120">Common Properties</span><span class="sxs-lookup"><span data-stu-id="5c6ef-120">Common Properties</span></span>](../../common-properties.md)  
  
-   [<span data-ttu-id="5c6ef-121">변환 사용자 지정 속성</span><span class="sxs-lookup"><span data-stu-id="5c6ef-121">Transformation Custom Properties</span></span>](transformation-custom-properties.md)  
  
 <span data-ttu-id="5c6ef-122">속성을 설정하는 방법에 대한 자세한 내용은 [데이터 흐름 구성 요소의 속성 설정](../set-the-properties-of-a-data-flow-component.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5c6ef-122">For more information about how to set properties, see [Set the Properties of a Data Flow Component](../set-the-properties-of-a-data-flow-component.md).</span></span>  
  
  
