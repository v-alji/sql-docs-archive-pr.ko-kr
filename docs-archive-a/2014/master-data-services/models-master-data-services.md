---
title: 모델(Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- models [Master Data Services], about models
- models [Master Data Services]
ms.assetid: 9f862a3d-25ab-41e9-b833-1db99959e825
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 1d5a4a431d3ca7b6fa499de68a2bc4c5033cd086
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660641"
---
# <a name="models-master-data-services"></a><span data-ttu-id="aabde-102">모델(Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="aabde-102">Models (Master Data Services)</span></span>
  <span data-ttu-id="aabde-103">모델은 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]의 최상위 데이터 구성 수준입니다.</span><span class="sxs-lookup"><span data-stu-id="aabde-103">Models are the highest level of data organization in [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)].</span></span> <span data-ttu-id="aabde-104">모델은 마스터 데이터 관리 솔루션의 데이터 구조를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="aabde-104">A model defines the structure of data in your master data management solution.</span></span> <span data-ttu-id="aabde-105">모델은 다음 개체를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="aabde-105">A model contains the following objects:</span></span>  
  
-   <span data-ttu-id="aabde-106">엔터티</span><span class="sxs-lookup"><span data-stu-id="aabde-106">Entities</span></span>  
  
-   <span data-ttu-id="aabde-107">특성 및 특성 그룹</span><span class="sxs-lookup"><span data-stu-id="aabde-107">Attributes and attribute groups</span></span>  
  
-   <span data-ttu-id="aabde-108">명시적 계층 및 파생 계층</span><span class="sxs-lookup"><span data-stu-id="aabde-108">Explicit and derived hierarchies</span></span>  
  
-   <span data-ttu-id="aabde-109">컬렉션</span><span class="sxs-lookup"><span data-stu-id="aabde-109">Collections</span></span>  
  
 <span data-ttu-id="aabde-110">모델은 마스터 데이터의 구조를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="aabde-110">Models organize the structure of your master data.</span></span> <span data-ttu-id="aabde-111">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 를 구현하면 그룹이 각각 비슷한 종류의 데이터를 가진 하나 이상의 모델이 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aabde-111">Your [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] implementation can have one or many models that each group similar kinds of data.</span></span> <span data-ttu-id="aabde-112">일반적으로 마스터 데이터는 사용자, 장소, 사물 및 개념의 네 가지 범주 중 하나에 속합니다.</span><span class="sxs-lookup"><span data-stu-id="aabde-112">In general, master data can be categorized in one of four ways: people, places, things, or concepts.</span></span> <span data-ttu-id="aabde-113">예를 들어 Product 모델을 만들어 제품 관련 데이터를 포함하거나 Customer 모델을 만들어 고객 관련 데이터를 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aabde-113">For example, you can create a Product model to contain product-related data or a Customer model to contain customer-related data.</span></span>  
  
 <span data-ttu-id="aabde-114">사용자 및 그룹에 모델 내의 개체를 보고 업데이트할 수 있는 권한을 할당할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aabde-114">You can assign users and groups permission to view and update objects within the model.</span></span> <span data-ttu-id="aabde-115">모델에 사용 권한을 부여하지 않으면 해당 모델이 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="aabde-115">If you do not give permission to the model, it is not displayed.</span></span>  
  
 <span data-ttu-id="aabde-116">언제든지 모델 내에 마스터 데이터의 복사본을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aabde-116">At any given time, you can create copies of the master data within a model.</span></span> <span data-ttu-id="aabde-117">이러한 복사본을 버전이라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="aabde-117">These copies are called versions.</span></span>  
  
 <span data-ttu-id="aabde-118">테스트 환경에서 모델을 정의한 경우 해당 데이터를 포함하거나 포함하지 않은 상태로 테스트 환경에서 프로덕션 환경으로 모델을 배포할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aabde-118">When you have defined a model in a test environment, you can deploy it, with or without the corresponding data, from the test environment to a production environment.</span></span> <span data-ttu-id="aabde-119">이렇게 하면 프로덕션 환경에서 모델을 다시 만들 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="aabde-119">This eliminates the need to recreate your models in your production environment.</span></span>  
  
## <a name="how-models-relate-to-other-objects"></a><span data-ttu-id="aabde-120">다른 개체와 모델의 관계</span><span class="sxs-lookup"><span data-stu-id="aabde-120">How Models Relate to Other Objects</span></span>  
 <span data-ttu-id="aabde-121">모델에는 엔터티가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="aabde-121">A model contains entities.</span></span> <span data-ttu-id="aabde-122">엔터티에는 특성, 명시적 계층 및 컬렉션이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="aabde-122">Entities contain attributes, explicit hierarchies, and collections.</span></span> <span data-ttu-id="aabde-123">특성은 특성 그룹에 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aabde-123">Attributes can be contained in attribute groups.</span></span> <span data-ttu-id="aabde-124">DBA(도메인 기반 특성)는 엔터티를 다른 엔터티의 특성으로 사용할 때 존재합니다.</span><span class="sxs-lookup"><span data-stu-id="aabde-124">Domain-based attributes exist when an entity is used as an attribute for another entity.</span></span>  
  
 <span data-ttu-id="aabde-125">이 이미지는 모델 개체 간의 관계를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="aabde-125">This image shows the relationships among the objects in a model.</span></span>  
  
 <span data-ttu-id="aabde-126">![MDS(Master Data Services) 모델의 개체](../../2014/master-data-services/media/mds-conc-model-circles.gif "MDS(Master Data Services) 모델의 개체")</span><span class="sxs-lookup"><span data-stu-id="aabde-126">![Objects in a Master Data Services Model](../../2014/master-data-services/media/mds-conc-model-circles.gif "Objects in a Master Data Services Model")</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="aabde-127">파생 계층도 모델 개체지만 이미지에 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="aabde-127">Derived hierarchies are also model objects, but they are not shown in the image.</span></span> <span data-ttu-id="aabde-128">파생 계층은 엔터티 간에 존재하는 도메인 기반 특성 관계에서 파생됩니다.</span><span class="sxs-lookup"><span data-stu-id="aabde-128">Derived hierarchies are derived from the domain-based attribute relationships that exist between entities.</span></span> <span data-ttu-id="aabde-129">자세한 내용은 [파생 계층&#40;Master Data Services&#41;](derived-hierarchies-master-data-services.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="aabde-129">See [Derived Hierarchies &#40;Master Data Services&#41;](derived-hierarchies-master-data-services.md) for more information.</span></span>  
  
 <span data-ttu-id="aabde-130">마스터 데이터는 모델 개체에 포함되는 데이터입니다.</span><span class="sxs-lookup"><span data-stu-id="aabde-130">Master data is the data that is contained in the model objects.</span></span> <span data-ttu-id="aabde-131">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]에서는 마스터 데이터가 엔터티의 멤버로 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="aabde-131">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], master data is stored as members in an entity.</span></span>  
  
 <span data-ttu-id="aabde-132">모델 개체는 **사용자 인터페이스의** 시스템 관리 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 기능 영역에서 유지 관리됩니다.</span><span class="sxs-lookup"><span data-stu-id="aabde-132">Model objects are maintained in the **System Administration** functional area of the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] user interface.</span></span>  
  
## <a name="model-example"></a><span data-ttu-id="aabde-133">모델 예</span><span class="sxs-lookup"><span data-stu-id="aabde-133">Model Example</span></span>  
 <span data-ttu-id="aabde-134">다음 예에서 Product 모델의 개체는 제품 관련 데이터를 논리적으로 그룹화합니다.</span><span class="sxs-lookup"><span data-stu-id="aabde-134">In the following example, the objects in the Product model logically group product-related data.</span></span>  
  
 <span data-ttu-id="aabde-135">![제품 모델 마스터 데이터 예제](../../2014/master-data-services/media/mds-conc-model.gif "제품 모델 마스터 데이터 예제")</span><span class="sxs-lookup"><span data-stu-id="aabde-135">![Product Model Master Data Example](../../2014/master-data-services/media/mds-conc-model.gif "Product Model Master Data Example")</span></span>  
  
 <span data-ttu-id="aabde-136">그밖에 일반적인 모델은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="aabde-136">Other common models are:</span></span>  
  
-   <span data-ttu-id="aabde-137">Accounts - 대차대조표 계정, 재무제표 계정, 통계, 계정 유형 등의 엔터티를 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aabde-137">Accounts, which could include entities such as balance sheet accounts, income statement accounts, statistics, and account type.</span></span>  
  
-   <span data-ttu-id="aabde-138">Customer - 성별, 교육 수준, 직업, 결혼 여부 등의 엔터티를 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aabde-138">Customer, which could include entities such as gender, education, occupation, and marital status.</span></span>  
  
-   <span data-ttu-id="aabde-139">Geography - 우편 번호, 도시, 군, 주, 지방, 지역, 영토, 국가, 대륙 등을 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aabde-139">Geography, which could include entities such as postal codes, cities, counties, states, provinces, regions, territories, countries, and continents.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="aabde-140">관련 작업</span><span class="sxs-lookup"><span data-stu-id="aabde-140">Related Tasks</span></span>  
  
|<span data-ttu-id="aabde-141">태스크 설명</span><span class="sxs-lookup"><span data-stu-id="aabde-141">Task Description</span></span>|<span data-ttu-id="aabde-142">항목</span><span class="sxs-lookup"><span data-stu-id="aabde-142">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="aabde-143">모델을 만들어 마스터 데이터를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="aabde-143">Create a model to organize your master data.</span></span>|[<span data-ttu-id="aabde-144">모델 만들기&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="aabde-144">Create a Model &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-a-model-master-data-services.md)|  
|<span data-ttu-id="aabde-145">기존 모델의 이름을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="aabde-145">Change the name of an existing model.</span></span>|[<span data-ttu-id="aabde-146">모델 이름 &#40;MDS(Master Data Services)&#41;변경</span><span class="sxs-lookup"><span data-stu-id="aabde-146">Change a Model Name &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/change-a-model-name-master-data-services.md)|  
|<span data-ttu-id="aabde-147">기존 모델을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="aabde-147">Delete an existing model.</span></span>|[<span data-ttu-id="aabde-148">모델 삭제&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="aabde-148">Delete a Model &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/delete-a-model-master-data-services.md)|  
  
## <a name="related-content"></a><span data-ttu-id="aabde-149">관련 내용</span><span class="sxs-lookup"><span data-stu-id="aabde-149">Related Content</span></span>  
  
-   [<span data-ttu-id="aabde-150">MDS(Master Data Services) 개요</span><span class="sxs-lookup"><span data-stu-id="aabde-150">Master Data Services Overview</span></span>](master-data-services-overview-mds.md)  
  
-   [<span data-ttu-id="aabde-151">엔터티&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="aabde-151">Entities &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/entities-master-data-services.md)  
  
-   [<span data-ttu-id="aabde-152">특성&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="aabde-152">Attributes &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/attributes-master-data-services.md)  
  
-   [<span data-ttu-id="aabde-153">모델 배포&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="aabde-153">Deploying Models &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/deploying-models-master-data-services.md)  
  
-   [<span data-ttu-id="aabde-154">모델 개체 권한&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="aabde-154">Model Object Permissions &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/model-object-permissions-master-data-services.md)  
  
  
