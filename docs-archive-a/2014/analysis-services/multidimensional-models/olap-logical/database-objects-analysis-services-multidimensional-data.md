---
title: 데이터베이스 개체 (Analysis Services 다차원 데이터) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- objects [Analysis Services], about objects
- SQL Server Analysis Services, objects
- Analysis Services objects, about Analysis Services objects
- SSAS, objects
- Analysis Services objects
- objects [Analysis Services]
ms.assetid: f76d869b-fc1d-4807-9f28-da09c7be382d
author: minewiskan
ms.author: owend
ms.openlocfilehash: d61e3213356146e1cf9e452e0b62e02c96bd4902
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743567"
---
# <a name="database-objects-analysis-services---multidimensional-data"></a><span data-ttu-id="4a2c1-102">데이터베이스 개체(Analysis Services - 다차원 데이터)</span><span class="sxs-lookup"><span data-stu-id="4a2c1-102">Database Objects (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="4a2c1-103">[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 인스턴스는 OLAP (온라인 분석 처리) 및 데이터 마이닝에 사용할 데이터베이스 개체와 어셈블리를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="4a2c1-103">A [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] instance contains database objects and assemblies for use with online analytical processing (OLAP) and data mining.</span></span>  
  
-   <span data-ttu-id="4a2c1-104">데이터베이스에는 OLAP와 데이터 원본, 데이터 원본 뷰, 큐브, 측정값, 측정값 그룹, 차원, 특성, 계층, 마이닝 구조, 마이닝 모델 및 역할과 같은 데이터 마이닝 개체가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="4a2c1-104">Databases contain OLAP and data mining objects, such as data sources, data source views, cubes, measures, measure groups, dimensions, attributes, hierarchies, mining structures, mining models and roles.</span></span>  
  
-   <span data-ttu-id="4a2c1-105">어셈블리에는 MDX(Multidimensional Expressions) 및 DMX(Data Mining Extensions) 언어와 함께 제공된 기본 함수의 기능을 확장하는 사용자 정의 함수가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="4a2c1-105">Assemblies contain user-defined functions that extend the functionality of the intrinsic functions provided with the Multidimensional Expressions (MDX) and Data Mining Extensions (DMX) languages.</span></span>  
  
 <span data-ttu-id="4a2c1-106"><xref:Microsoft.AnalysisServices.Database> 개체는 비즈니스 인텔리전스 프로젝트(예: OLAP 큐브, 차원 및 데이터 마이닝 구조) 및 해당 지원 개체(예: <xref:Microsoft.AnalysisServices.DataSource>, <xref:Microsoft.AnalysisServices.Account> 및 <xref:Microsoft.AnalysisServices.Role>)에 필요한 모든 데이터 개체의 컨테이너입니다.</span><span class="sxs-lookup"><span data-stu-id="4a2c1-106">The <xref:Microsoft.AnalysisServices.Database> object is the container for all data objects that are needed for a business intelligence project (such as OLAP cubes, dimensions, and data mining structures), and their supporting objects (such as <xref:Microsoft.AnalysisServices.DataSource>, <xref:Microsoft.AnalysisServices.Account>, and <xref:Microsoft.AnalysisServices.Role>).</span></span>  
  
 <span data-ttu-id="4a2c1-107"><xref:Microsoft.AnalysisServices.Database> 개체는 다음을 포함하는 개체와 특성에 대한 액세스 권한을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="4a2c1-107">A <xref:Microsoft.AnalysisServices.Database> object provides access to objects and attributes that include the following:</span></span>  
  
-   <span data-ttu-id="4a2c1-108">액세스할 수 있는 모든 큐브(컬렉션)</span><span class="sxs-lookup"><span data-stu-id="4a2c1-108">All cubes that you can access, as a collection.</span></span>  
  
-   <span data-ttu-id="4a2c1-109">액세스할 수 있는 모든 차원(컬렉션)</span><span class="sxs-lookup"><span data-stu-id="4a2c1-109">All dimensions that you can access, as a collection.</span></span>  
  
-   <span data-ttu-id="4a2c1-110">액세스할 수 있는 모든 마이닝 구조(컬렉션)</span><span class="sxs-lookup"><span data-stu-id="4a2c1-110">All mining structures that you can access, as a collection.</span></span>  
  
-   <span data-ttu-id="4a2c1-111">모든 데이터 원본과 데이터 원본 뷰(두 개의 컬렉션)</span><span class="sxs-lookup"><span data-stu-id="4a2c1-111">All data sources and data source views, as two collections.</span></span>  
  
-   <span data-ttu-id="4a2c1-112">모든 역할과 데이터베이스 권한(두 개의 컬렉션)</span><span class="sxs-lookup"><span data-stu-id="4a2c1-112">All roles and database permissions, as two collections.</span></span>  
  
-   <span data-ttu-id="4a2c1-113">데이터베이스에 대한 데이터 정렬 값</span><span class="sxs-lookup"><span data-stu-id="4a2c1-113">The collation value for the database.</span></span>  
  
-   <span data-ttu-id="4a2c1-114">데이터베이스의 예상 크기</span><span class="sxs-lookup"><span data-stu-id="4a2c1-114">The estimated size of the database.</span></span>  
  
-   <span data-ttu-id="4a2c1-115">데이터베이스의 언어 값</span><span class="sxs-lookup"><span data-stu-id="4a2c1-115">The language value of the database.</span></span>  
  
-   <span data-ttu-id="4a2c1-116">데이터베이스의 표시 설정</span><span class="sxs-lookup"><span data-stu-id="4a2c1-116">The visible setting for the database.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4a2c1-117">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="4a2c1-117">In This Section</span></span>  
 <span data-ttu-id="4a2c1-118">다음 항목에서는 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]의 OLAP 및 데이터 마이닝 기능이 공유하는 개체에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="4a2c1-118">The following topics describe objects shared by both OLAP and data mining features in [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].</span></span>  
  
|<span data-ttu-id="4a2c1-119">항목</span><span class="sxs-lookup"><span data-stu-id="4a2c1-119">Topic</span></span>|<span data-ttu-id="4a2c1-120">설명</span><span class="sxs-lookup"><span data-stu-id="4a2c1-120">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="4a2c1-121">다차원 모델의 데이터 원본</span><span class="sxs-lookup"><span data-stu-id="4a2c1-121">Data Sources in Multidimensional Models</span></span>](../data-sources-in-multidimensional-models.md)|<span data-ttu-id="4a2c1-122">[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]의 데이터 원본에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="4a2c1-122">Describes a data source in [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].</span></span>|  
|[<span data-ttu-id="4a2c1-123">다차원 모델의 데이터 원본 뷰</span><span class="sxs-lookup"><span data-stu-id="4a2c1-123">Data Source Views in Multidimensional Models</span></span>](../data-source-views-in-multidimensional-models.md)|<span data-ttu-id="4a2c1-124">[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]의 하나 이상의 데이터 원본을 기반으로 하는 논리 데이터 모델에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="4a2c1-124">Describes a logical data model based on one or more data sources, in [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].</span></span>|  
|[<span data-ttu-id="4a2c1-125">다차원 모델의 큐브</span><span class="sxs-lookup"><span data-stu-id="4a2c1-125">Cubes in Multidimensional Models</span></span>](../cubes-in-multidimensional-models.md)|<span data-ttu-id="4a2c1-126">큐브에 대해 설명하고 측정값, 측정값 그룹, 차원 용도 관계, 계산, 핵심 성과 지표, 동작, 번역, 파티션, 큐브 뷰 등의 큐브 개체를 살펴봅니다.</span><span class="sxs-lookup"><span data-stu-id="4a2c1-126">Describes cubes and cube objects, including measures, measure groups, dimension usage relationships, calculations, key performance indicators, actions, translations, partitions, and perspectives.</span></span>|  
|[<span data-ttu-id="4a2c1-127">차원&#40;Analysis Services - 다차원 데이터&#41;</span><span class="sxs-lookup"><span data-stu-id="4a2c1-127">Dimensions &#40;Analysis Services - Multidimensional Data&#41;</span></span>](../../multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md)|<span data-ttu-id="4a2c1-128">차원에 대해 설명하고 특성, 특성 관계, 계층, 수준 및 멤버 등의 차원 개체를 살펴봅니다.</span><span class="sxs-lookup"><span data-stu-id="4a2c1-128">Describes dimensions and dimension objects, including attributes, attribute relationships, hierarchies, levels, and members.</span></span>|  
|[<span data-ttu-id="4a2c1-129">마이닝 구조&#40;Analysis Services - 데이터 마이닝&#41;</span><span class="sxs-lookup"><span data-stu-id="4a2c1-129">Mining Structures &#40;Analysis Services - Data Mining&#41;</span></span>](../../data-mining/mining-structures-analysis-services-data-mining.md)|<span data-ttu-id="4a2c1-130">마이닝 구조와 마이닝 모델을 포함하는 마이닝 개체에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="4a2c1-130">Describes mining structures and mining objects, including mining models.</span></span>|  
|[<span data-ttu-id="4a2c1-131">보안 역할&#40;Analysis Services - 다차원 데이터&#41;</span><span class="sxs-lookup"><span data-stu-id="4a2c1-131">Security Roles  &#40;Analysis Services - Multidimensional Data&#41;</span></span>](security-roles-analysis-services-multidimensional-data.md)|<span data-ttu-id="4a2c1-132">[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]에서 개체에 대한 액세스를 제어하는 데 사용되는 보안 메커니즘인 역할에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="4a2c1-132">Describes a role, the security mechanism used to control access to objects in [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].</span></span>|  
|[<span data-ttu-id="4a2c1-133">다차원 모델 어셈블리 관리</span><span class="sxs-lookup"><span data-stu-id="4a2c1-133">Multidimensional Model Assemblies Management</span></span>](../multidimensional-model-assemblies-management.md)|<span data-ttu-id="4a2c1-134">[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]에서 MDX 및 DMX 언어를 확장하는 데 사용되는 사용자 정의 함수 모음인 어셈블리에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="4a2c1-134">Describes an assembly, a collection of user-defined functions used to extend the MDX and DMX languages, in [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4a2c1-135">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4a2c1-135">See Also</span></span>  
 <span data-ttu-id="4a2c1-136">[SSAS 다차원&#41;&#40;지원 되는 데이터 원본](../supported-data-sources-ssas-multidimensional.md) </span><span class="sxs-lookup"><span data-stu-id="4a2c1-136">[Data Sources Supported &#40;SSAS Multidimensional&#41;](../supported-data-sources-ssas-multidimensional.md) </span></span>  
 <span data-ttu-id="4a2c1-137">[SSAS&#41;&#40;다차원 모델 솔루션](../multidimensional-model-solutions-ssas.md) </span><span class="sxs-lookup"><span data-stu-id="4a2c1-137">[Multidimensional Model Solutions &#40;SSAS&#41;](../multidimensional-model-solutions-ssas.md) </span></span>  
 [<span data-ttu-id="4a2c1-138">데이터 마이닝 솔루션</span><span class="sxs-lookup"><span data-stu-id="4a2c1-138">Data Mining Solutions</span></span>](../../data-mining/data-mining-solutions.md)  
  
  
