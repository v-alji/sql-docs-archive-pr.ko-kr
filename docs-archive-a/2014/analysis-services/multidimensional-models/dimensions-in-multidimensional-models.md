---
title: 다차원 모델의 차원 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- OLAP [Analysis Services], dimensions
- dimensions [Analysis Services], about dimensions
- OLAP objects [Analysis Services], dimensions
ms.assetid: 2b62b05c-00fd-4e60-b77f-f707ba83a19b
author: minewiskan
ms.author: owend
ms.openlocfilehash: b9e452453b80de3656abf62cdcd90519cf4a6c99
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741396"
---
# <a name="dimensions-in-multidimensional-models"></a><span data-ttu-id="0cdd7-102">다차원 모델의 차원</span><span class="sxs-lookup"><span data-stu-id="0cdd7-102">Dimensions in Multidimensional Models</span></span>
  <span data-ttu-id="0cdd7-103">데이터베이스 차원은 하나 이상의 큐브 내 팩트 데이터에 대한 정보를 제공하는 데 사용할 수 있는 특성이라는 관련 개체의 모음입니다.</span><span class="sxs-lookup"><span data-stu-id="0cdd7-103">A database dimension is a collection of related objects, called attributes, which can be used to provide information about fact data in one or more cubes.</span></span> <span data-ttu-id="0cdd7-104">예를 들어 제품 차원의 일반적인 특성은 제품 이름, 제품 범주, 제품 라인, 제품 크기 및 제품 가격이 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0cdd7-104">For example, typical attributes in a product dimension might be product name, product category, product line, product size, and product price.</span></span> <span data-ttu-id="0cdd7-105">이러한 개체는 데이터 원본 뷰에 있는 하나 이상의 테이블의 하나 이상의 열에 바인딩됩니다.</span><span class="sxs-lookup"><span data-stu-id="0cdd7-105">These objects are bound to one or more columns in one or more tables in a data source view.</span></span> <span data-ttu-id="0cdd7-106">기본적으로 이러한 특성은 특성 계층으로 표시되며 큐브의 팩트 데이터를 확인하는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0cdd7-106">By default, these attributes are visible as attribute hierarchies and can be used to understand the fact data in a cube.</span></span> <span data-ttu-id="0cdd7-107">특성은 큐브의 데이터를 검색할 때 사용자를 지원할 탐색 경로를 제공하는 사용자 정의 계층으로 구성될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0cdd7-107">Attributes can be organized into user-defined hierarchies that provide navigational paths to assist users when browsing the data in a cube.</span></span>  
  
 <span data-ttu-id="0cdd7-108">큐브에는 사용자가 팩트 데이터 분석을 기반으로 사용하는 모든 차원이 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0cdd7-108">Cubes contain all the dimensions on which users base their analyses of fact data.</span></span> <span data-ttu-id="0cdd7-109">큐브의 데이터베이스 차원 인스턴스를 큐브 차원이라고 하며 이 인스턴스는 큐브에 있는 하나 이상의 측정값 그룹과 관련되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0cdd7-109">An instance of a database dimension in a cube is called a cube dimension and relates to one or more measure groups in the cube.</span></span> <span data-ttu-id="0cdd7-110">데이터베이스 차원은 큐브에서 여러 번 사용될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0cdd7-110">A database dimension can be used multiple times in a cube.</span></span> <span data-ttu-id="0cdd7-111">예를 들어 팩트 테이블에 여러 개의 시간 관련 팩트가 있을 수 있고 각 시간 관련 팩트 분석을 지원하기 위해 별도의 큐브 차원을 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0cdd7-111">For example, a fact table can have multiple time-related facts, and a separate cube dimension can be defined to assist in analyzing each time-related fact.</span></span> <span data-ttu-id="0cdd7-112">그러나 시간 관련 데이터베이스 차원은 한 개만 있어야 하므로 여러 개의 시간 기반 큐브 차원을 지원하는 시간 관련 관계형 데이터베이스 테이블도 한 개만 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdd7-112">However, only one time-related database dimension needs to exist, which also means that only one time-related relational database table needs to exist to support multiple cube dimensions based on time.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0cdd7-113">차원 디자인과 관련된 성능 문제에 대한 자세한 내용은 [SQL Server 2008 R2 Analysis Services Performance Guide](https://go.microsoft.com/fwlink/?LinkId=306717)(SQL Server 2008 R2 Analysis Services 성능 가이드)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0cdd7-113">For performance issues related to dimension design, see the [SQL Server 2008 R2 Analysis Services Performance Guide](https://go.microsoft.com/fwlink/?LinkId=306717).</span></span>  
  
## <a name="defining-dimensions-attributes-and-hierarchies"></a><span data-ttu-id="0cdd7-114">차원, 특성 및 계층 정의</span><span class="sxs-lookup"><span data-stu-id="0cdd7-114">Defining Dimensions, Attributes, and Hierarchies</span></span>  
 <span data-ttu-id="0cdd7-115">데이터베이스 및 큐브 차원, 특성 및 계층을 정의하는 가장 간단한 방법은 큐브 마법사를 사용하여 큐브를 정의할 때 이러한 차원을 만드는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="0cdd7-115">The simplest method for defining database and cube dimensions, attributes, and hierarchies is to use the Cube Wizard to create dimensions at the same time that you define the cube.</span></span> <span data-ttu-id="0cdd7-116">큐브 마법사는 마법사가 식별하거나 사용자가 큐브에서 사용하도록 지정한 데이터 원본 뷰의 차원 테이블을 기반으로 차원을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="0cdd7-116">The Cube Wizard will create dimensions based on the dimension tables in the data source view that the wizard identifies or that you specify for use in the cube.</span></span> <span data-ttu-id="0cdd7-117">그러면 마법사를 통해 만든 데이터베이스 차원이 새 큐브에 추가되어 큐브 차원이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0cdd7-117">The wizard then creates the database dimensions and adds them to the new cube, creating cube dimensions.</span></span>  
  
 <span data-ttu-id="0cdd7-118">큐브를 만들 때 데이터베이스에 이미 있는 차원을 새 큐브에 추가할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0cdd7-118">When you create a cube, you can also add to the new cube any dimensions that already exist in the database.</span></span> <span data-ttu-id="0cdd7-119">이러한 차원은 다른 큐브에 대해 또는 차원 마법사를 통해 이전에 정의된 것일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0cdd7-119">These dimensions may have been previously defined for another cube or by the Dimension Wizard.</span></span> <span data-ttu-id="0cdd7-120">데이터베이스 차원을 정의한 후에는 차원 디자이너에서 해당 데이터베이스 차원을 수정하고 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0cdd7-120">After a database dimension has been defined, you can modify and configure the database dimension in Dimension Designer.</span></span> <span data-ttu-id="0cdd7-121">그리고 큐브 디자이너에서 제한된 범위까지 큐브 차원을 사용자 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0cdd7-121">You can also customize the cube dimension, to a limited extent, in Cube Designer.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0cdd7-122">또한 XMLA 또는 AMO(Analysis Management Objects)를 사용하여 차원, 특성 및 계층을 프로그래밍 방식으로 디자인하고 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0cdd7-122">You can also design and configure dimensions, attributes, and hierarchies programmatically by using either XMLA or Analysis Management Objects (AMO).</span></span> <span data-ttu-id="0cdd7-123">자세한 내용은 [AMO(Analysis Management Object) &#40;AMO&#41;를 사용 하 여 ](https://docs.microsoft.com/bi-reference/amo/developing-with-analysis-management-objects-amo) [Analysis Services 스크립팅 언어 &#40;&#41; 참조](https://docs.microsoft.com/bi-reference/assl/analysis-services-scripting-language-assl-for-xmla) 및 개발을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="0cdd7-123">For more information, see [Analysis Services Scripting Language &#40;ASSL&#41; Reference](https://docs.microsoft.com/bi-reference/assl/analysis-services-scripting-language-assl-for-xmla) and [Developing with Analysis Management Objects &#40;AMO&#41;](https://docs.microsoft.com/bi-reference/amo/developing-with-analysis-management-objects-amo).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0cdd7-124">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="0cdd7-124">In This Section</span></span>  
 <span data-ttu-id="0cdd7-125">다음 표에서는 이 섹션에서 다루는 항목에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdd7-125">The following table describes the topics in this section.</span></span>  
  
 [<span data-ttu-id="0cdd7-126">데이터베이스 차원 정의</span><span class="sxs-lookup"><span data-stu-id="0cdd7-126">Define Database Dimensions</span></span>](define-database-dimensions.md)  
 <span data-ttu-id="0cdd7-127">차원 디자이너를 사용하여 데이터베이스 차원을 수정하고 구성하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdd7-127">Describes how to modify and configure a database dimension by using Dimension Designer.</span></span>  
  
 [<span data-ttu-id="0cdd7-128">차원 특성 속성 참조</span><span class="sxs-lookup"><span data-stu-id="0cdd7-128">Dimension Attribute Properties Reference</span></span>](dimension-attribute-properties-reference.md)  
 <span data-ttu-id="0cdd7-129">차원 디자이너를 사용하여 데이터베이스 차원 특성을 정의, 수정 및 구성하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdd7-129">Describes how to define, modify, and configure a database dimension attribute by using Dimension Designer.</span></span>  
  
 [<span data-ttu-id="0cdd7-130">특성 관계 정의</span><span class="sxs-lookup"><span data-stu-id="0cdd7-130">Define Attribute Relationships</span></span>](attribute-relationships-define.md)  
 <span data-ttu-id="0cdd7-131">차원 디자이너를 사용하여 특성 관계를 정의, 수정 및 구성하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdd7-131">Describes how to define, modify, and configure an attribute relationship by using Dimension Designer.</span></span>  
  
 [<span data-ttu-id="0cdd7-132">사용자 정의 계층 만들기</span><span class="sxs-lookup"><span data-stu-id="0cdd7-132">Create User-Defined Hierarchies</span></span>](user-defined-hierarchies-create.md)  
 <span data-ttu-id="0cdd7-133">차원 디자이너를 사용하여 차원 특성의 사용자 정의 계층을 정의, 수정 및 구성하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdd7-133">Describes how to define, modify, and configure a user-defined hierarchy of dimension attributes by using Dimension Designer.</span></span>  
  
 [<span data-ttu-id="0cdd7-134">비즈니스 인텔리전스 마법사를 사용하여 차원 향상</span><span class="sxs-lookup"><span data-stu-id="0cdd7-134">Use the Business Intelligence Wizard to Enhance Dimensions</span></span>](../use-the-business-intelligence-wizard-to-enhance-dimensions.md)  
 <span data-ttu-id="0cdd7-135">비즈니스 인텔리전스 마법사를 사용하여 데이터베이스 차원을 향상시키는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdd7-135">Describes how to enhance a database dimension by using the Business Intelligence Wizard.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0cdd7-136">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0cdd7-136">See Also</span></span>  
 [<span data-ttu-id="0cdd7-137">다차원 모델의 큐브</span><span class="sxs-lookup"><span data-stu-id="0cdd7-137">Cubes in Multidimensional Models</span></span>](cubes-in-multidimensional-models.md)  
  
  
