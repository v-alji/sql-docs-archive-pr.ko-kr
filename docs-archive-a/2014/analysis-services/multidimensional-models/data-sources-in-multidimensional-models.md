---
title: 다차원 모델의 데이터 원본 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- metadata [Analysis Services]
- Analysis Services objects, data sources
- storing data [Analysis Services], data sources
- data sources [Analysis Services], about data sources
- security [Analysis Services], data sources
- data sources [Analysis Services]
- storage [Analysis Services], data sources
ms.assetid: a16469d9-9d53-4e35-9982-fc06327a9d33
author: minewiskan
ms.author: owend
ms.openlocfilehash: 41386c1c7abb0324aa17df24b3c427ca8cbb5615
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659694"
---
# <a name="data-sources-in-multidimensional-models"></a><span data-ttu-id="f2e09-102">다차원 모델의 데이터 원본</span><span class="sxs-lookup"><span data-stu-id="f2e09-102">Data Sources in Multidimensional Models</span></span>
  <span data-ttu-id="f2e09-103">다차원 모델로 가져오거나 로드하는 모든 데이터는 외부 데이터 원본에서 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="f2e09-103">All data that you import or load into a multidimensional model originates from an external data source.</span></span> <span data-ttu-id="f2e09-104">일반적으로 원본 데이터는 보고용으로 디자인된 데이터 웨어하우스의 데이터이지만 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 패키지와 같은 매개자를 통해 직접 또는 간접으로 액세스되는 관계형 데이터베이스의 데이터일 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f2e09-104">Typically, source data is from a data warehouse designed for reporting purposes, but it could come from any relational database that is accessed directly or indirectly through an intermediary, such as an [!INCLUDE[ssIS](../../includes/ssis-md.md)] package.</span></span>  
  
 <span data-ttu-id="f2e09-105">**의** 데이터 원본 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 개체는 외부 데이터 원본에 대한 직접 연결을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f2e09-105">A **data source** object in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] specifies a direct connection to an external data source.</span></span> <span data-ttu-id="f2e09-106">물리적 위치 외에 데이터 원본 개체는 연결 문자열, 데이터 공급자, 자격 증명 및 연결 동작을 제어하는 기타 속성도 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f2e09-106">In addition to physical location, a data source object specifies the connection string, data provider, credentials, and other properties that control connection behavior.</span></span>  
  
 <span data-ttu-id="f2e09-107">데이터 원본 개체에서 제공되는 정보는 다음과 같은 작업 중에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="f2e09-107">Information provided by the data source object is used during the following operations:</span></span>  
  
-   <span data-ttu-id="f2e09-108">데이터 원본 뷰를 모델에 생성하기 위해 사용되는 스키마 정보 및 기타 메타데이터를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="f2e09-108">Get schema information and other metadata used to generate data source views into a model.</span></span>  
  
-   <span data-ttu-id="f2e09-109">처리 중 데이터를 쿼리하거나 모델에 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="f2e09-109">Query or load data into a model during processing.</span></span>  
  
-   <span data-ttu-id="f2e09-110">ROLAP 스토리지 모드를 사용하는 다차원 또는 데이터 마이닝 모델에 대해 쿼리를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="f2e09-110">Run queries against multidimensional or data mining models that use ROLAP storage mode.</span></span>  
  
-   <span data-ttu-id="f2e09-111">원격 파티션을 읽거나 씁니다.</span><span class="sxs-lookup"><span data-stu-id="f2e09-111">Read or write to remote partitions.</span></span>  
  
-   <span data-ttu-id="f2e09-112">연결된 개체에 연결하고 대상과 원본 간에 동기화합니다.</span><span class="sxs-lookup"><span data-stu-id="f2e09-112">Connect to linked objects, as well as synchronize from target to source.</span></span>  
  
-   <span data-ttu-id="f2e09-113">관계형 데이터베이스에 저장된 팩트 테이블 데이터를 업데이트하는 쓰기 저장(write back) 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="f2e09-113">Perform write back operations that update fact table data stored in a relational database.</span></span>  
  
 <span data-ttu-id="f2e09-114">다차원 모델을 아래쪽에서 위쪽으로 작성할 때 데이터 원본 개체를 만들어 시작한 다음 이 개체를 사용하여 다음 개체인 **데이터 원본 뷰**를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="f2e09-114">When building a multidimensional model from the bottom up, you start by creating the data source object, and then use it to generate the next object, a **data source view**.</span></span> <span data-ttu-id="f2e09-115">데이터 원본 뷰는 모델의 데이터 추상화 계층입니다.</span><span class="sxs-lookup"><span data-stu-id="f2e09-115">A data source view is the data abstraction layer in the model.</span></span> <span data-ttu-id="f2e09-116">일반적으로 원본 데이터베이스의 스키마를 기본으로 사용하여 데이터 원본 개체 이후에 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="f2e09-116">It is typically created after the data source object, using the schema of the source database as the basis.</span></span> <span data-ttu-id="f2e09-117">그러나 큐브 및 차원으로 시작하여 디자인을 가장 잘 지원하는 스키마를 생성하는 것을 비롯하여 모델을 생성하는 다른 방법을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f2e09-117">However, you can choose other ways to build a model, including starting with cubes and dimensions, and generating the schema that best supports your design.</span></span>  
  
 <span data-ttu-id="f2e09-118">모델 생성 방법에 관계없이 각 모델에는 원본 데이터에 대한 연결을 지정하는 적어도 하나 이상의 데이터 원본 개체가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="f2e09-118">Regardless of how you build it, each model requires at least one data source object that specifies a connection to source data.</span></span> <span data-ttu-id="f2e09-119">여러 데이터 원본 개체를 하나의 모델로 생성하여 다른 원본에서 데이터를 사용하거나 특정 개체에 대한 연결 속성을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f2e09-119">You can create multiple data source objects in a single model to use data from different sources or vary connection properties for specific objects.</span></span>  
  
 <span data-ttu-id="f2e09-120">데이터 원본 개체는 모델의 다른 개체에 관계없이 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f2e09-120">Data source objects can be managed independently of other objects in your model.</span></span> <span data-ttu-id="f2e09-121">데이터 원본을 만든 후 해당 속성을 나중에 변경할 수 있으며 그 후 데이터가 제대로 검색되는지 확인하기 위해 모델을 전처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f2e09-121">After you create a data source, you can change its properties later, and then preprocess the model to ensure the data is retrieved correctly.</span></span>  
  
## <a name="related-topics-and-tasks"></a><span data-ttu-id="f2e09-122">관련 항목 및 태스크</span><span class="sxs-lookup"><span data-stu-id="f2e09-122">Related Topics and Tasks</span></span>  
  
|<span data-ttu-id="f2e09-123">항목</span><span class="sxs-lookup"><span data-stu-id="f2e09-123">Topic</span></span>|<span data-ttu-id="f2e09-124">Description</span><span class="sxs-lookup"><span data-stu-id="f2e09-124">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="f2e09-125">SSAS 다차원&#41;&#40;지원 되는 데이터 원본</span><span class="sxs-lookup"><span data-stu-id="f2e09-125">Data Sources Supported &#40;SSAS Multidimensional&#41;</span></span>](supported-data-sources-ssas-multidimensional.md)|<span data-ttu-id="f2e09-126">다차원 모델에서 사용할 수 있는 데이터 원본 유형에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="f2e09-126">Describes the types of data sources that can be used in a multidimensional model.</span></span>|  
|[<span data-ttu-id="f2e09-127">데이터 원본 만들기&#40;SSAS 다차원&#41;</span><span class="sxs-lookup"><span data-stu-id="f2e09-127">Create a Data Source &#40;SSAS Multidimensional&#41;</span></span>](create-a-data-source-ssas-multidimensional.md)|<span data-ttu-id="f2e09-128">다차원 모델에 데이터 원본 개체를 추가하는 방법에 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="f2e09-128">Explains how to add a data source object to a multidimensional model.</span></span>|  
|[<span data-ttu-id="f2e09-129">솔루션 탐색기에서 데이터 원본 삭제&#40;SSAS 다차원&#41;</span><span class="sxs-lookup"><span data-stu-id="f2e09-129">Delete a Data Source in Solution Explorer &#40;SSAS Multidimensional&#41;</span></span>](delete-a-data-source-in-solution-explorer-ssas-multidimensional.md)|<span data-ttu-id="f2e09-130">이 절차를 사용하여 다차원 모델에서 데이터 원본 개체를 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f2e09-130">Use this procedure to delete a data source object from a multidimensional model.</span></span>|  
|[<span data-ttu-id="f2e09-131">데이터 원본 속성 설정&#40;SSAS 다차원&#41;</span><span class="sxs-lookup"><span data-stu-id="f2e09-131">Set Data Source Properties &#40;SSAS Multidimensional&#41;</span></span>](set-data-source-properties-ssas-multidimensional.md)|<span data-ttu-id="f2e09-132">각 속성과 각 속성을 설정하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="f2e09-132">Describes each property and explains how to set each one.</span></span>|  
|[<span data-ttu-id="f2e09-133">가장 옵션 설정&#40;SSAS - 다차원&#41;</span><span class="sxs-lookup"><span data-stu-id="f2e09-133">Set Impersonation Options &#40;SSAS - Multidimensional&#41;</span></span>](set-impersonation-options-ssas-multidimensional.md)|<span data-ttu-id="f2e09-134">가장 정보 대화 상자에서 옵션을 구성하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="f2e09-134">Explains how to configure options in the Impersonation Information dialog box.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f2e09-135">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f2e09-135">See Also</span></span>  
 <span data-ttu-id="f2e09-136">[데이터베이스 개체 &#40;Analysis Services 다차원 데이터&#41;](olap-logical/database-objects-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="f2e09-136">[Database Objects &#40;Analysis Services - Multidimensional Data&#41;](olap-logical/database-objects-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="f2e09-137">[논리적 아키텍처 &#40;Analysis Services 다차원 데이터&#41;](olap-logical/understanding-microsoft-olap-logical-architecture.md) </span><span class="sxs-lookup"><span data-stu-id="f2e09-137">[Logical Architecture &#40;Analysis Services - Multidimensional Data&#41;](olap-logical/understanding-microsoft-olap-logical-architecture.md) </span></span>  
 <span data-ttu-id="f2e09-138">[다차원 모델의 데이터 원본 뷰](data-source-views-in-multidimensional-models.md) </span><span class="sxs-lookup"><span data-stu-id="f2e09-138">[Data Source Views in Multidimensional Models](data-source-views-in-multidimensional-models.md) </span></span>  
 [<span data-ttu-id="f2e09-139">데이터 원본 및 바인딩&#40;SSAS 다차원&#41;</span><span class="sxs-lookup"><span data-stu-id="f2e09-139">Data Sources and Bindings &#40;SSAS Multidimensional&#41;</span></span>](data-sources-and-bindings-ssas-multidimensional.md)  
  
  
