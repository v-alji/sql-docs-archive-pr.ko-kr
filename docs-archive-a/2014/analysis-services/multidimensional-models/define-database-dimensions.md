---
title: 데이터베이스 차원 정의 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- dimensions [Analysis Services], defining
ms.assetid: fe84588b-66a3-4100-a1cf-59b21b7adf01
author: minewiskan
ms.author: owend
ms.openlocfilehash: ad5334e71b0f133f80933a7d1702d8ada7565501
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728887"
---
# <a name="define-database-dimensions"></a><span data-ttu-id="af05f-102">데이터베이스 차원 정의</span><span class="sxs-lookup"><span data-stu-id="af05f-102">Define Database Dimensions</span></span>
  <span data-ttu-id="af05f-103">의 차원 디자이너 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 를 사용 하 여 프로젝트나 데이터베이스의 기존 데이터베이스 차원을 구성할 수 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 있습니다.</span><span class="sxs-lookup"><span data-stu-id="af05f-103">Use Dimension Designer in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] to configure an existing database dimension in a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project or database.</span></span> <span data-ttu-id="af05f-104">차원 디자이너를 사용하여 수행할 수 있는 작업은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="af05f-104">You can use Dimension Designer to do the following:</span></span>  
  
-   <span data-ttu-id="af05f-105">차원 수준 속성 구성</span><span class="sxs-lookup"><span data-stu-id="af05f-105">Configure the dimension-level properties.</span></span>  
  
-   <span data-ttu-id="af05f-106">차원 특성 추가 및 구성</span><span class="sxs-lookup"><span data-stu-id="af05f-106">Add and configure dimension attributes.</span></span>  
  
-   <span data-ttu-id="af05f-107">사용자 정의 계층 정의 및 구성</span><span class="sxs-lookup"><span data-stu-id="af05f-107">Define and configure user-defined hierarchies.</span></span>  
  
-   <span data-ttu-id="af05f-108">특성 간 관계 정의 및 구성</span><span class="sxs-lookup"><span data-stu-id="af05f-108">Define and configure relationships between attributes.</span></span>  
  
-   <span data-ttu-id="af05f-109">차원 번역 정의</span><span class="sxs-lookup"><span data-stu-id="af05f-109">Define dimension translations.</span></span>  
  
-   <span data-ttu-id="af05f-110">처리된 차원의 경우 차원 구조를 탐색하고 데이터를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="af05f-110">For processed dimensions, you can browse the dimension structure and view data.</span></span>  
  
 <span data-ttu-id="af05f-111">차원, 특성 또는 계층을 수정한 후 변경 내용을 보려면 해당 차원을 처리해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="af05f-111">After you modify a dimension, attribute, or hierarchy, you must process that dimension to view the changes.</span></span> <span data-ttu-id="af05f-112">프로젝트 모드에서 작업하는 경우에는 처리하기 전에 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 인스턴스에 변경 내용을 배포합니다.</span><span class="sxs-lookup"><span data-stu-id="af05f-112">When working in project mode, you deploy the changes to the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance before processing.</span></span>  
  
 <span data-ttu-id="af05f-113">차원 디자이너에서 차원을 여는 방법은 [솔루션 탐색기에서 데이터베이스 차원 수정 또는 삭제](database-dimensions-modify-or-delete-a-database-dimension-in-solution-explorer.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="af05f-113">For more information about how to open a dimension in Dimension Designer, see [Modify or Delete a Database Dimension in Solution Explorer](database-dimensions-modify-or-delete-a-database-dimension-in-solution-explorer.md).</span></span>  
  
 <span data-ttu-id="af05f-114">차원 디자이너에는 다음 표에 설명된 3개의 탭이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="af05f-114">Dimension Designer has three different tabs, which are described in the following table.</span></span>  
  
|<span data-ttu-id="af05f-115">탭</span><span class="sxs-lookup"><span data-stu-id="af05f-115">Tab</span></span>|<span data-ttu-id="af05f-116">Description</span><span class="sxs-lookup"><span data-stu-id="af05f-116">Description</span></span>|  
|---------|-----------------|  
|<span data-ttu-id="af05f-117">**차원 구조**</span><span class="sxs-lookup"><span data-stu-id="af05f-117">**Dimension Structure**</span></span>|<span data-ttu-id="af05f-118">이 탭을 사용 하 여 차원의 데이터 원본 뷰 스키마를 검토 하거나 만들고 특성 작업을 수행 하 고 사용자 정의 계층의 특성을 구성 하는 등의 차원 구조 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="af05f-118">Use this tab to work with the structure of a dimension-to examine or create the data source view schema for a dimension, to work with attributes, and to organize attributes in user-defined hierarchies.</span></span>|  
|<span data-ttu-id="af05f-119">**의 차원 디자이너에 있는 차원 구조 뷰의**</span><span class="sxs-lookup"><span data-stu-id="af05f-119">**Attribute Relationships**</span></span>|<span data-ttu-id="af05f-120">이 탭을 사용하여 차원의 특성 관계를 만들거나 수정하거나 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="af05f-120">Use this tab to create, modify, or delete the attribute relationships of a dimension.</span></span>|  
|<span data-ttu-id="af05f-121">**Translations**</span><span class="sxs-lookup"><span data-stu-id="af05f-121">**Translations**</span></span>|<span data-ttu-id="af05f-122">이 탭을 사용하여 여러 언어로 차원 메타데이터의 번역을 추가하고 편집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="af05f-122">Use this tab to add and edit translations of dimension metadata in different languages.</span></span>|  
|<span data-ttu-id="af05f-123">**브라우저**</span><span class="sxs-lookup"><span data-stu-id="af05f-123">**Browser**</span></span>|<span data-ttu-id="af05f-124">이 탭을 사용하여 처리된 차원의 멤버를 확인하고 차원 메타데이터의 번역을 검토할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="af05f-124">Use this tab to examine the members of a processed dimension and to review translations of dimension metadata.</span></span>|  
  
 <span data-ttu-id="af05f-125">다음 항목에서는 차원 디자이너에서 수행할 수 있는 태스크를 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="af05f-125">The following topics describe the tasks that you can perform in Dimension Designer.</span></span>  
  
 [<span data-ttu-id="af05f-126">차원 특성 속성 참조</span><span class="sxs-lookup"><span data-stu-id="af05f-126">Dimension Attribute Properties Reference</span></span>](dimension-attribute-properties-reference.md)  
 <span data-ttu-id="af05f-127">차원 특성을 정의 및 구성하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="af05f-127">Describes how to define and configure a dimension attribute.</span></span>  
  
 [<span data-ttu-id="af05f-128">사용자 정의 계층 만들기</span><span class="sxs-lookup"><span data-stu-id="af05f-128">Create User-Defined Hierarchies</span></span>](user-defined-hierarchies-create.md)  
 <span data-ttu-id="af05f-129">사용자 정의 계층을 정의 및 구성하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="af05f-129">Describes how to define and configure a user-defined hierarchy.</span></span>  
  
 [<span data-ttu-id="af05f-130">특성 관계 정의</span><span class="sxs-lookup"><span data-stu-id="af05f-130">Define Attribute Relationships</span></span>](attribute-relationships-define.md)  
 <span data-ttu-id="af05f-131">특성 관계를 정의 및 구성하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="af05f-131">Describes how to define and configure an attribute relationship.</span></span>  
  
 [<span data-ttu-id="af05f-132">비즈니스 인텔리전스 마법사를 사용하여 차원 향상</span><span class="sxs-lookup"><span data-stu-id="af05f-132">Use the Business Intelligence Wizard to Enhance Dimensions</span></span>](../use-the-business-intelligence-wizard-to-enhance-dimensions.md)  
 <span data-ttu-id="af05f-133">비즈니스 인텔리전스 마법사를 사용하여 차원을 향상시키는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="af05f-133">Describes how to use the Business Intelligence Wizard to enhance a dimension.</span></span>  
  
  
