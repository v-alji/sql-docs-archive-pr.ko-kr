---
title: 스키마 생성 마법사 (Analysis Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- relational schema [Analysis Services]
ms.assetid: 68bf7ba3-d0cb-437f-9a3e-9edc0999af19
author: minewiskan
ms.author: owend
ms.openlocfilehash: 2cd58ada8ea4c2dd17ba4427578ac1336a6bd353
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653021"
---
# <a name="schema-generation-wizard-analysis-services"></a><span data-ttu-id="37c6d-102">스키마 생성 마법사(Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="37c6d-102">Schema Generation Wizard (Analysis Services)</span></span>
  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] <span data-ttu-id="37c6d-103">에서는 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 프로젝트나 데이터베이스 내의 OLAP 개체를 정의할 때 두 가지 관계형 스키마 작업 방법을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="37c6d-103">supports two methods of working with relational schemas when defining OLAP objects within an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project or database.</span></span> <span data-ttu-id="37c6d-104">일반적으로 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 프로젝트나 데이터베이스 내의 데이터 원본 뷰에 생성된 논리적 데이터 모델을 기반으로 OLAP 개체를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="37c6d-104">Generally, you will define OLAP objects based on a logical data model constructed in a data source view within an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project or database.</span></span> <span data-ttu-id="37c6d-105">이 데이터 원본 뷰는 데이터 원본 뷰에 사용자 지정된 대로 하나 이상의 관계형 데이터 원본의 스키마 요소를 기반으로 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="37c6d-105">This data source view is defined based on schema elements from one or more relational data sources, as customized in the data source view.</span></span>  
  
 <span data-ttu-id="37c6d-106">또는 OLAP 개체를 먼저 정의한 다음 데이터 원본 뷰 및 데이터 원본과, 해당 OLAP 개체를 지원하는 기본 관계형 데이터베이스 스키마를 생성할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="37c6d-106">Alternatively, you can define OLAP objects first, and then generate a data source view, a data source, and the underlying relational database schema that supports these OLAP objects.</span></span> <span data-ttu-id="37c6d-107">이러한 관계형 데이터베이스를 주제 영역 데이터베이스라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="37c6d-107">This relational database is referred to as the subject area database.</span></span>  
  
 <span data-ttu-id="37c6d-108">때로는 이 방법을 하향식 디자인이라고 하며 프로토타입 및 분석 모델링에 자주 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="37c6d-108">This approach is sometimes called top-down design and is frequently used for prototyping and analysis modeling.</span></span> <span data-ttu-id="37c6d-109">이 방법을 사용할 경우 스키마 생성 마법사를 사용하여 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 프로젝트나 데이터베이스에서 정의한 OLAP 개체를 기반으로 기본 데이터 원본과 데이터 원본 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="37c6d-109">When you use this approach, you use the Schema Generation Wizard to create the underlying data source view and data source objects based on the OLAP objects defined in an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project or database.</span></span>  
  
 <span data-ttu-id="37c6d-110">이 방법은 반복적인 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="37c6d-110">This is an iterative approach.</span></span> <span data-ttu-id="37c6d-111">즉, 차원과 큐브의 디자인을 변경할 때마다 마법사를 다시 실행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="37c6d-111">You will most likely rerun the wizard multiple times as you change the design of the dimensions and cubes.</span></span> <span data-ttu-id="37c6d-112">마법사를 실행할 때마다 마법사는 변경 내용을 원본 개체에 통합하여 기본 데이터베이스에 포함된 데이터를 최대한 유지합니다.</span><span class="sxs-lookup"><span data-stu-id="37c6d-112">Each time you run the wizard, it incorporates the changes into the underlying objects and, as much as is possible, preserves the data contained in the underlying databases.</span></span>  
  
 <span data-ttu-id="37c6d-113">생성된 스키마는 SQL Server 관계형 데이터베이스 엔진 스키마입니다.</span><span class="sxs-lookup"><span data-stu-id="37c6d-113">The schema that is generated is a SQL Server relational database engine schema.</span></span> <span data-ttu-id="37c6d-114">마법사는 다른 관계형 데이터베이스 제품에 대한 스키마를 생성하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="37c6d-114">The wizard does not generate schemas for other relational database products.</span></span>  
  
 <span data-ttu-id="37c6d-115">주제 영역 데이터베이스에 채워진 데이터는 SQL Server 관계형 데이터베이스를 채우는 데 사용하는 도구 및 기법을 통해 별도로 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="37c6d-115">The data that is populated in the subject area database is added separately, using whatever tools and techniques you use to populate a SQL Server relational database.</span></span> <span data-ttu-id="37c6d-116">대부분의 경우 마법사를 다시 실행할 때 데이터가 유지되지만 예외가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="37c6d-116">In most cases, the data is preserved when you rerun the wizard, but there are exceptions.</span></span> <span data-ttu-id="37c6d-117">예를 들어 데이터가 포함된 차원이나 특성을 삭제하면 일부 데이터가 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="37c6d-117">For example, some data must be dropped if you delete a dimension or an attribute that contains data.</span></span> <span data-ttu-id="37c6d-118">스키마 변경으로 인해 스키마 생성 마법사가 일부 데이터를 삭제해야 하는 경우에는 데이터를 삭제하기 전에 경고 메시지를 표시하므로 재생성을 취소할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="37c6d-118">If the Schema Generation Wizard must drop some data because of a schema change, you receive a warning before the data is dropped and can then cancel the regeneration.</span></span>  
  
 <span data-ttu-id="37c6d-119">일반적으로, 스키마 생성 마법사가 원래 생성했던 개체에서 변경된 내용은 이후에 스키마 생성 마법사가 해당 개체를 다시 생성할 때 덮어쓰게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="37c6d-119">As a general rule, any change that you make to an object that was originally generated by the Schema Generation Wizard is overwritten when the Schema Generation Wizard subsequently regenerates that object.</span></span> <span data-ttu-id="37c6d-120">단, 스키마 생성 마법사가 생성한 테이블에 열을 추가하는 경우는 예외입니다.</span><span class="sxs-lookup"><span data-stu-id="37c6d-120">The primary exception to this rule is when you add columns to a table that the Schema Generation Wizard generated.</span></span> <span data-ttu-id="37c6d-121">이와 같은 경우에는 스키마 생성 마법사가 테이블에 추가된 열 및 해당 열의 데이터를 그대로 유지합니다.</span><span class="sxs-lookup"><span data-stu-id="37c6d-121">In this case, the Schema Generation Wizard preserves the columns that you added to the table, as well as the data in these columns.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="37c6d-122">단원 내용</span><span class="sxs-lookup"><span data-stu-id="37c6d-122">In this section</span></span>  
 <span data-ttu-id="37c6d-123">다음 표에는 스키마 생성 마법사의 작업 방법을 설명하는 추가 항목이 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="37c6d-123">The following table lists additional topics that explain how to work with the Schema Generation Wizard.</span></span>  
  
|<span data-ttu-id="37c6d-124">항목</span><span class="sxs-lookup"><span data-stu-id="37c6d-124">Topic</span></span>|<span data-ttu-id="37c6d-125">Description</span><span class="sxs-lookup"><span data-stu-id="37c6d-125">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="37c6d-126">스키마 생성 마법사 사용&#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="37c6d-126">Use the Schema Generation Wizard &#40;Analysis Services&#41;</span></span>](schema-generation-wizard-analysis-services.md)|<span data-ttu-id="37c6d-127">주제 영역 데이터베이스와 준비 영역 데이터베이스의 스키마를 생성하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="37c6d-127">Describes how to generate the schema for the subject area and staging area databases.</span></span>|  
|[<span data-ttu-id="37c6d-128">데이터베이스 스키마 이해</span><span class="sxs-lookup"><span data-stu-id="37c6d-128">Understanding the Database Schemas</span></span>](understanding-the-database-schemas.md)|<span data-ttu-id="37c6d-129">주제 영역 데이터베이스와 준비 영역 데이터베이스에 대해 생성되는 스키마에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="37c6d-129">Describes the schema that is generated for the subject area and staging area databases.</span></span>|  
|[<span data-ttu-id="37c6d-130">증분 생성 이해</span><span class="sxs-lookup"><span data-stu-id="37c6d-130">Understanding Incremental Generation</span></span>](understanding-incremental-generation.md)|<span data-ttu-id="37c6d-131">스키마 생성 마법사의 증분 생성 기능에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="37c6d-131">Describes the incremental generation capabilities of the Schema Generation Wizard.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="37c6d-132">참고 항목</span><span class="sxs-lookup"><span data-stu-id="37c6d-132">See Also</span></span>  
 <span data-ttu-id="37c6d-133">[다차원 모델의 데이터 원본 뷰](data-source-views-in-multidimensional-models.md) </span><span class="sxs-lookup"><span data-stu-id="37c6d-133">[Data Source Views in Multidimensional Models](data-source-views-in-multidimensional-models.md) </span></span>  
 <span data-ttu-id="37c6d-134">[다차원 모델의 데이터 원본](data-sources-in-multidimensional-models.md) </span><span class="sxs-lookup"><span data-stu-id="37c6d-134">[Data Sources in Multidimensional Models](data-sources-in-multidimensional-models.md) </span></span>  
 [<span data-ttu-id="37c6d-135">SSAS 다차원&#41;&#40;지원 되는 데이터 원본</span><span class="sxs-lookup"><span data-stu-id="37c6d-135">Data Sources Supported &#40;SSAS Multidimensional&#41;</span></span>](supported-data-sources-ssas-multidimensional.md)  
  
  
