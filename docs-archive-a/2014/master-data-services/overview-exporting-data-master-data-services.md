---
title: 데이터 내보내기(Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- exporting data [Master Data Services]
- subscription views [Master Data Services]
- subscription views [Master Data Services], about subscription views
ms.assetid: 8b74409a-ea70-45f8-84c7-da6905e4901a
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: edae5b996c25a1b6053231ed2f69ef511b9fbfa6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651073"
---
# <a name="exporting-data-master-data-services"></a><span data-ttu-id="2db72-102">데이터 내보내기(Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="2db72-102">Exporting Data (Master Data Services)</span></span>
  <span data-ttu-id="2db72-103">구독 뷰를 만들어 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 데이터를 구독 시스템으로 내보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2db72-103">You can export [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] data to subscribing systems by creating subscriptions views.</span></span> <span data-ttu-id="2db72-104">그러면 임의의 구독 시스템에서 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 데이터베이스의 게시된 데이터를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2db72-104">Any subscribing system can then view the published data in the [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] database.</span></span> <span data-ttu-id="2db72-105">보기에 대한 자세한 내용은 [보기](../relational-databases/views/views.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="2db72-105">For more information about views, see [Views](../relational-databases/views/views.md).</span></span>  
  
## <a name="subscription-view-formats"></a><span data-ttu-id="2db72-106">구독 뷰 형식</span><span class="sxs-lookup"><span data-stu-id="2db72-106">Subscription View Formats</span></span>  
 <span data-ttu-id="2db72-107">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]에서 뷰를 만들 때 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 에서 제공하는 표준 뷰 형식 집합 중에서 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="2db72-107">When you create a view in [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], you choose from a set of standard view formats that [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] provides.</span></span> <span data-ttu-id="2db72-108">이러한 형식을 사용하여 다음을 표시하는 뷰를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2db72-108">You can use these formats to create views that show:</span></span>  
  
-   <span data-ttu-id="2db72-109">모든 리프 멤버와 해당 특성</span><span class="sxs-lookup"><span data-stu-id="2db72-109">All leaf members and their attributes.</span></span>  
  
-   <span data-ttu-id="2db72-110">모든 통합 멤버와 해당 특성</span><span class="sxs-lookup"><span data-stu-id="2db72-110">All consolidated members and their attributes.</span></span>  
  
-   <span data-ttu-id="2db72-111">모든 컬렉션과 해당 특성</span><span class="sxs-lookup"><span data-stu-id="2db72-111">All collections and their attributes.</span></span>  
  
-   <span data-ttu-id="2db72-112">명시적으로 컬렉션에 추가된 멤버</span><span class="sxs-lookup"><span data-stu-id="2db72-112">The members explicitly added to a collection.</span></span>  
  
-   <span data-ttu-id="2db72-113">부모-자식 또는 수준 형식인 파생 계층의 멤버</span><span class="sxs-lookup"><span data-stu-id="2db72-113">The members in a derived hierarchy, in either a parent child or level format.</span></span>  
  
-   <span data-ttu-id="2db72-114">부모-자식 또는 수준 형식인 엔터티에 대한 모든 명시적 계층의 멤버</span><span class="sxs-lookup"><span data-stu-id="2db72-114">The members in all explicit hierarchies for an entity, in either a parent child or level format.</span></span>  
  
## <a name="subscription-views-can-become-out-of-date"></a><span data-ttu-id="2db72-115">구독 뷰가 최신 내용을 반영하지 못할 수 있음</span><span class="sxs-lookup"><span data-stu-id="2db72-115">Subscription Views Can Become Out-of-Date</span></span>  
 <span data-ttu-id="2db72-116">엔터티 또는 계층에 대한 구독 뷰를 만든 후 연결된 모델 개체의 변경 사항이 뷰에 자동으로 반영되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2db72-116">After you create a subscription view for an entity or hierarchy, changes to the associated model objects are not automatically reflected in the view.</span></span> <span data-ttu-id="2db72-117">또한 모델 개체에 대한 변경 사항을 반영하기 위해 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 에서 구독 뷰를 다시 생성해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2db72-117">You might need to regenerate a subscription view in [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] to reflect changes to model objects.</span></span> <span data-ttu-id="2db72-118">모델 개체가 변경될 경우 **내보내기** 페이지의 **변경됨** 열이 **True** 로 업데이트됩니다.</span><span class="sxs-lookup"><span data-stu-id="2db72-118">The **Changed** column on the **Export** page is updated to **True** when model objects change.</span></span> <span data-ttu-id="2db72-119">**True** 는 구독 뷰를 편집하고 저장하여 뷰를 다시 생성해야 한다는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="2db72-119">**True** indicates that you should edit the subscription view and save it, which regenerates the view.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="2db72-120">관련 작업</span><span class="sxs-lookup"><span data-stu-id="2db72-120">Related Tasks</span></span>  
  
|<span data-ttu-id="2db72-121">태스크 설명</span><span class="sxs-lookup"><span data-stu-id="2db72-121">Task Description</span></span>|<span data-ttu-id="2db72-122">항목</span><span class="sxs-lookup"><span data-stu-id="2db72-122">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="2db72-123">마스터 데이터 구독 뷰를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="2db72-123">Create a subscription view of your master data.</span></span>|[<span data-ttu-id="2db72-124">MDS(Master Data Services) &#40;구독 뷰를 만듭니다&#41;</span><span class="sxs-lookup"><span data-stu-id="2db72-124">Create a Subscription View &#40;Master Data Services&#41;</span></span>](create-a-subscription-view-to-export-data-master-data-services.md)|  
|<span data-ttu-id="2db72-125">기존 구독 뷰를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="2db72-125">Delete an existing subscription view.</span></span>|[<span data-ttu-id="2db72-126">구독 뷰 삭제&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="2db72-126">Delete a Subscription View &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/delete-a-subscription-view-master-data-services.md)|  
  
## <a name="related-content"></a><span data-ttu-id="2db72-127">관련 내용</span><span class="sxs-lookup"><span data-stu-id="2db72-127">Related Content</span></span>  
  
-   [<span data-ttu-id="2db72-128">구독 뷰 형식&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="2db72-128">Subscription View Formats &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/subscription-view-formats-master-data-services.md)  
  
-   [<span data-ttu-id="2db72-129">뷰</span><span class="sxs-lookup"><span data-stu-id="2db72-129">Views</span></span>](../relational-databases/views/views.md)  
  
  
