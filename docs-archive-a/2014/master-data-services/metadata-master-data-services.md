---
title: 메타 데이터 (MDS(Master Data Services)) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2019
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- user-defined metadata [Master Data Services], about user-defined metadata
- metadata [Master Data Services], about metadata
- metadata [Master Data Services]
- user-defined metadata [Master Data Services]
ms.assetid: ac1aabe3-d8d4-4d7a-8954-50ee3c185d81
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 39ab95b7925306febb551962495da7ec9751589b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730811"
---
# <a name="metadata-master-data-services"></a><span data-ttu-id="af738-102">메타데이터(MDS(Master Data Services))</span><span class="sxs-lookup"><span data-stu-id="af738-102">Metadata (Master Data Services)</span></span>
  <span data-ttu-id="af738-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]에서 사용자 정의 메타데이터는 모델 개체를 설명하는 데 사용되는 정보입니다.</span><span class="sxs-lookup"><span data-stu-id="af738-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], user-defined metadata is information that you use to describe model objects.</span></span> <span data-ttu-id="af738-104">예를 들어 특정 모델이나 엔터티의 소유자를 추적하거나 엔터티에 데이터를 제공하는 원본 시스템을 추적해야 하는 경우가 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="af738-104">For example, you may want to track the owners of a particular model or entity, or track the source systems that supply data to an entity.</span></span>  
  
 <span data-ttu-id="af738-105">사용자 정의 메타 데이터는 **메타 데이터**라는 모델로 관리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="af738-105">User-defined metadata is managed by a model called **Metadata**.</span></span> <span data-ttu-id="af738-106">이 모델은가 설치 될 때 자동으로 포함 되며,이 모델 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 의 버전을 만들 수 없다는 점을 제외 하 고 다른 모든 MDS 모델과 유사 합니다.</span><span class="sxs-lookup"><span data-stu-id="af738-106">This model is automatically included when [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] is installed, and it is similar to all other MDS models, except that you cannot create versions of it.</span></span>  
  
 <span data-ttu-id="af738-107">메타데이터 모델을 사용자 정의 메타데이터로 채운 후 구독 시스템에서 사용할 수 있도록 구독 뷰에 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="af738-107">After you populate the Metadata model with user-defined metadata, you can include it in subscription views, so it can be consumed by subscribing systems.</span></span>  
  
## <a name="metadata-entities"></a><span data-ttu-id="af738-108">메타데이터 엔터티</span><span class="sxs-lookup"><span data-stu-id="af738-108">Metadata Entities</span></span>  
 <span data-ttu-id="af738-109">메타데이터 모델에는 5개의 엔터티가 포함되며, 각각 사용자 정의 메타데이터를 지원하는 마스터 데이터 모델 개체의 유형을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="af738-109">The Metadata model includes five entities, each of which represents a type of master data model object that supports user-defined metadata.</span></span> <span data-ttu-id="af738-110">예를 들어 **모델 메타 데이터 정의** 엔터티에는 모델을 나타내는 멤버가 포함 되 고, **특성 메타 데이터 정의** 엔터티에는 모든 모델의 모든 특성을 나타내는 멤버가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="af738-110">For example, the **Model Metadata Definition** entity contains members that represent models, and the **Attribute Metadata Definition** entity has members that represent all attributes in all models.</span></span>  
  
 <span data-ttu-id="af738-111">모델 개체에 대한 메타데이터를 정의하려면 이러한 멤버의 특성 중 하나를 채웁니다.</span><span class="sxs-lookup"><span data-stu-id="af738-111">To define metadata for a model object, you populate one of these member's attributes.</span></span> <span data-ttu-id="af738-112">예를 들어 **엔터티 메타 데이터 정의** 엔터티에서 Price 멤버의 Description 특성을 **고객에 게 판매 될 때의 제품 가격**텍스트로 채울 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="af738-112">For example, in the **Entity Metadata Definition** entity, you can populate the Price member's Description attribute with the text: **The product price when sold to a customer**.</span></span>  
  
 <span data-ttu-id="af738-113">메타데이터 모델의 멤버는 사용자 정의 메타데이터를 지원하는 모델 개체가 추가되거나 삭제될 때마다 자동으로 업데이트됩니다.</span><span class="sxs-lookup"><span data-stu-id="af738-113">The members in the Metadata model are automatically updated whenever model objects that support user-defined metadata are added or deleted.</span></span>  
  
 <span data-ttu-id="af738-114">메타데이터 모델은 버전을 지정하거나 버전 플래그를 추가 또는 변경하거나 모델 배포 패키지로 저장할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="af738-114">The Metadata model cannot be versioned, have version flags added or changed, or be saved as a model deployment package.</span></span> <span data-ttu-id="af738-115">그러나 메타데이터 모델은 다른 마스터 데이터 모델의 모든 기능을 갖추고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="af738-115">However, it has all the same other functionality available to other master data models.</span></span> <span data-ttu-id="af738-116">예를 들어 메타데이터 모델에 대한 비즈니스 규칙 집합을 구현하여 데이터 정책을 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="af738-116">For example, you might implement a set of business rules on the Metadata model to enforce data policies.</span></span>  
  
## <a name="customizing-your-metadata-model"></a><span data-ttu-id="af738-117">메타데이터 모델 사용자 지정</span><span class="sxs-lookup"><span data-stu-id="af738-117">Customizing Your Metadata Model</span></span>  
 <span data-ttu-id="af738-118">각 메타데이터 정의 엔터티에는 Name, Code 및 Description 특성이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="af738-118">Each metadata definition entity includes Name, Code, and Description attributes.</span></span> <span data-ttu-id="af738-119">모델 개체를 보다 자세히 설명하기 위해 추가 특성을 만들 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="af738-119">You may want to create additional attributes to further describe your model objects.</span></span>  
  
 <span data-ttu-id="af738-120">예를 들어 다음과 같은 특성을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="af738-120">For example, you might create:</span></span>  
  
-   <span data-ttu-id="af738-121">Owner라는 도메인 기반 특성 - 각 모델 개체의 소유자를 추적하는 데 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="af738-121">A domain-based attribute named Owner, which you use to track the owner of each model object.</span></span>  
  
-   <span data-ttu-id="af738-122">Last Review Date라는 자유 형식 특성 - 소유자가 개체를 마지막으로 검토한 날짜를 추적하는 데 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="af738-122">A free-form attribute named Last Review Date, which you use to track the date that an object was last reviewed by the owner.</span></span>  
  
-   <span data-ttu-id="af738-123">인스턴스와 상호 작용 하는 원본 시스템을 추적 하 고 관리 하는 데 사용 하는 원본 이라는 도메인 기반 특성 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 입니다.</span><span class="sxs-lookup"><span data-stu-id="af738-123">A domain-based attribute named Sources, which you use to track and manage the source systems that interact with the [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] instance.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="af738-124">관련 작업</span><span class="sxs-lookup"><span data-stu-id="af738-124">Related Tasks</span></span>  
  
|<span data-ttu-id="af738-125">태스크 설명</span><span class="sxs-lookup"><span data-stu-id="af738-125">Task Description</span></span>|<span data-ttu-id="af738-126">항목</span><span class="sxs-lookup"><span data-stu-id="af738-126">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="af738-127">모델 개체에 메타데이터를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="af738-127">Add metadata to a model object.</span></span>|[<span data-ttu-id="af738-128">메타 데이터 &#40;추가 MDS(Master Data Services)&#41;</span><span class="sxs-lookup"><span data-stu-id="af738-128">Add Metadata &#40;Master Data Services&#41;</span></span>](add-metadata-master-data-services.md)
|&nbsp;|&nbsp;|
  
## <a name="related-content"></a><span data-ttu-id="af738-129">관련 내용</span><span class="sxs-lookup"><span data-stu-id="af738-129">Related Content</span></span>  
  
-   [<span data-ttu-id="af738-130">데이터 &#40;MDS(Master Data Services)&#41;내보내기</span><span class="sxs-lookup"><span data-stu-id="af738-130">Exporting Data &#40;Master Data Services&#41;</span></span>](overview-exporting-data-master-data-services.md)  
  
  
