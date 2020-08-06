---
title: 컬렉션 만들기(Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- creating collections [Master Data Services]
- collections [Master Data Services], creating
ms.assetid: 3d4f152c-863c-4385-bca9-a9fcd0402e1f
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: f76171b4fd9b07f751d4f919011a443253fbe31b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734219"
---
# <a name="create-a-collection-master-data-services"></a><span data-ttu-id="3862d-102">컬렉션 만들기(Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="3862d-102">Create a Collection (Master Data Services)</span></span>
  <span data-ttu-id="3862d-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]에서 리프 멤버 및 통합 멤버의 기본 목록을 만들려는 경우 컬렉션을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="3862d-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], create a collection when you want to create flat lists of leaf and consolidated members.</span></span> <span data-ttu-id="3862d-104">엔터티의 모든 멤버를 컬렉션에 포함할 필요는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3862d-104">Collections do not need to include all members from the entity.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="3862d-105">사전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="3862d-105">Prerequisites</span></span>  
 <span data-ttu-id="3862d-106">이 절차를 수행하려면</span><span class="sxs-lookup"><span data-stu-id="3862d-106">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="3862d-107">**탐색기** 기능 영역에 액세스할 수 있는 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3862d-107">You must have permission to access the **Explorer** functional area.</span></span>  
  
-   <span data-ttu-id="3862d-108">엔터티의 컬렉션 모델 개체에 대한 **업데이트** 이상의 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3862d-108">You must have a minimum of **Update** permission to the collection model object for the entity.</span></span>  
  
-   <span data-ttu-id="3862d-109">명시적 계층 및 컬렉션에 엔터티가 사용되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3862d-109">The entity must be enabled for explicit hierarchies and collections.</span></span> <span data-ttu-id="3862d-110">자세한 내용은 [&#41;MDS(Master Data Services) &#40;명시적 계층 및 컬렉션에 엔터티 사용 ](enable-an-entity-for-explicit-hierarchies-and-collections-master-data-services.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="3862d-110">For more information, see [Enable an Entity for Explicit Hierarchies and Collections &#40;Master Data Services&#41;](enable-an-entity-for-explicit-hierarchies-and-collections-master-data-services.md).</span></span>  
  
### <a name="to-create-a-collection"></a><span data-ttu-id="3862d-111">컬렉션을 만들려면</span><span class="sxs-lookup"><span data-stu-id="3862d-111">To create a collection</span></span>  
  
1.  <span data-ttu-id="3862d-112">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 홈 페이지의 **모델** 목록에서 모델을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3862d-112">On the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] home page, from the **Model** list, select a model.</span></span>  
  
2.  <span data-ttu-id="3862d-113">**버전** 목록에서 버전을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3862d-113">From the **Version** list, select a version.</span></span>  
  
3.  <span data-ttu-id="3862d-114">**탐색기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3862d-114">Click **Explorer**.</span></span>  
  
4.  <span data-ttu-id="3862d-115">메뉴 모음에서 **컬렉션** 을 가리키고 *entity_name*을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3862d-115">From the menu bar, point to **Collections** and click *entity_name*.</span></span>  
  
5.  <span data-ttu-id="3862d-116">**컬렉션 추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3862d-116">Click **Add collection**.</span></span>  
  
6.  <span data-ttu-id="3862d-117">**자세히** 탭의 **이름** 상자에 컬렉션의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="3862d-117">On the **Details** tab, in the **Name** box, type a name for the collection.</span></span>  
  
7.  <span data-ttu-id="3862d-118">**코드** 상자에 컬렉션의 고유 코드를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="3862d-118">In the **Code** box, type a unique code for the collection.</span></span>  
  
8.  <span data-ttu-id="3862d-119">필요에 따라 **설명** 상자에 컬렉션에 대한 설명을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="3862d-119">Optionally, in the **Description** box, type a description for the collection.</span></span>  
  
9. <span data-ttu-id="3862d-120">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3862d-120">Click **OK**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="3862d-121">다음 단계</span><span class="sxs-lookup"><span data-stu-id="3862d-121">Next Steps</span></span>  
  
-   [<span data-ttu-id="3862d-122">컬렉션에 멤버 추가&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="3862d-122">Add Members to a Collection &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/add-members-to-a-collection-master-data-services.md)  
  
## <a name="see-also"></a><span data-ttu-id="3862d-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3862d-123">See Also</span></span>  
 <span data-ttu-id="3862d-124">[컬렉션 &#40;MDS(Master Data Services)&#41;](../../2014/master-data-services/collections-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="3862d-124">[Collections &#40;Master Data Services&#41;](../../2014/master-data-services/collections-master-data-services.md) </span></span>  
 <span data-ttu-id="3862d-125">[MDS(Master Data Services) &#40;멤버 또는 컬렉션을 삭제&#41;](../../2014/master-data-services/delete-a-member-or-collection-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="3862d-125">[Delete a Member or Collection &#40;Master Data Services&#41;](../../2014/master-data-services/delete-a-member-or-collection-master-data-services.md) </span></span>  
 [<span data-ttu-id="3862d-126">명시적 계층 만들기&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="3862d-126">Create an Explicit Hierarchy &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-an-explicit-hierarchy-master-data-services.md)  
  
  
