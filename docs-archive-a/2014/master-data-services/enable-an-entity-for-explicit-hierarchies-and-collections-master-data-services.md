---
title: 명시적 계층 및 컬렉션에 엔터티 사용 (MDS(Master Data Services)) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- entities [Master Data Services], enabling for collections
- entities [Master Data Services], enabling for explicit hierarchies
ms.assetid: 380e77e5-ad60-43d4-9605-34a84525f5dd
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: a8129b3f67f050603f85ffb782a9dd209cb303fc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728396"
---
# <a name="enable-an-entity-for-explicit-hierarchies-and-collections-master-data-services"></a><span data-ttu-id="5a1f6-102">명시적 계층 및 컬렉션에 엔터티 사용(Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="5a1f6-102">Enable an Entity for Explicit Hierarchies and Collections (Master Data Services)</span></span>
  <span data-ttu-id="5a1f6-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]에서 엔터티에 대한 명시적 계층 및 컬렉션을 만들 수 있도록 명시적 계층 및 컬렉션에 엔터티를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="5a1f6-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], enable an entity for explicit hierarchies and collections so that you can create explicit hierarchies and collections for the entity.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="5a1f6-104">사전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="5a1f6-104">Prerequisites</span></span>  
 <span data-ttu-id="5a1f6-105">이 절차를 수행하려면</span><span class="sxs-lookup"><span data-stu-id="5a1f6-105">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="5a1f6-106">**시스템 관리** 기능 영역에 액세스할 수 있는 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5a1f6-106">You must have permission to access the **System Administration** functional area.</span></span>  
  
-   <span data-ttu-id="5a1f6-107">모델 관리자여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5a1f6-107">You must be a model administrator.</span></span> <span data-ttu-id="5a1f6-108">자세한 내용은 [관리자 &#40;MDS(Master Data Services)&#41;](administrators-master-data-services.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="5a1f6-108">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="5a1f6-109">엔터티가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5a1f6-109">An entity must exist.</span></span> <span data-ttu-id="5a1f6-110">자세한 내용은 [&#41;MDS(Master Data Services) 엔터티 &#40;만들기 ](../../2014/master-data-services/create-an-entity-master-data-services.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="5a1f6-110">For more information, see [Create an Entity &#40;Master Data Services&#41;](../../2014/master-data-services/create-an-entity-master-data-services.md).</span></span>  
  
### <a name="to-enable-an-entity-for-explicit-hierarchies-and-collections"></a><span data-ttu-id="5a1f6-111">명시적 계층 및 컬렉션에 대해 엔터티를 사용하려면</span><span class="sxs-lookup"><span data-stu-id="5a1f6-111">To enable an entity for explicit hierarchies and collections</span></span>  
  
1.  <span data-ttu-id="5a1f6-112">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]에서 **시스템 관리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5a1f6-112">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **System Administration**.</span></span>  
  
2.  <span data-ttu-id="5a1f6-113">**모델 뷰** 페이지의 메뉴 모음에서 **관리** 를 가리키고 **엔터티**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5a1f6-113">On the **Model View** page, from the menu bar, point to **Manage** and click **Entities**.</span></span>  
  
3.  <span data-ttu-id="5a1f6-114">**엔터티 유지 관리** 페이지의 **모델** 목록에서 모델을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="5a1f6-114">On the **Entity Maintenance** page, from the **Model** list, select a model.</span></span>  
  
4.  <span data-ttu-id="5a1f6-115">업데이트하려는 엔터티의 행을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="5a1f6-115">Select the row for the entity that you want to update.</span></span>  
  
5.  <span data-ttu-id="5a1f6-116">**선택한 엔터티 편집**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5a1f6-116">Click **Edit selected entity**.</span></span>  
  
6.  <span data-ttu-id="5a1f6-117">**명시적 계층 및 컬렉션 사용** 목록에서 **예**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="5a1f6-117">From the **Enable explicit hierarchies and collections** list, select **Yes**.</span></span>  
  
7.  <span data-ttu-id="5a1f6-118">**명시적 계층 이름** 상자에 명시적 계층의 이름을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="5a1f6-118">In the **Explicit hierarchy name** box, type a name for an explicit hierarchy.</span></span>  
  
8.  <span data-ttu-id="5a1f6-119">또는 **필수 계층** 확인란의 선택을 취소하여 계층을 필수가 아닌 계층으로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="5a1f6-119">Optionally, clear the **Mandatory hierarchy** check box to create the hierarchy as a non-mandatory hierarchy.</span></span>  
  
9. <span data-ttu-id="5a1f6-120">**엔터티 저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5a1f6-120">Click **Save entity**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="5a1f6-121">다음 단계</span><span class="sxs-lookup"><span data-stu-id="5a1f6-121">Next Steps</span></span>  
  
-   [<span data-ttu-id="5a1f6-122">명시적 계층 만들기&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="5a1f6-122">Create an Explicit Hierarchy &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-an-explicit-hierarchy-master-data-services.md)  
  
-   [<span data-ttu-id="5a1f6-123">컬렉션 만들기&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="5a1f6-123">Create a Collection &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-a-collection-master-data-services.md)  
  
## <a name="see-also"></a><span data-ttu-id="5a1f6-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5a1f6-124">See Also</span></span>  
 <span data-ttu-id="5a1f6-125">[엔터티 &#40;MDS(Master Data Services)&#41;](../../2014/master-data-services/entities-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="5a1f6-125">[Entities &#40;Master Data Services&#41;](../../2014/master-data-services/entities-master-data-services.md) </span></span>  
 <span data-ttu-id="5a1f6-126">[명시적 계층 &#40;MDS(Master Data Services)&#41;](../../2014/master-data-services/explicit-hierarchies-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="5a1f6-126">[Explicit Hierarchies &#40;Master Data Services&#41;](../../2014/master-data-services/explicit-hierarchies-master-data-services.md) </span></span>  
 [<span data-ttu-id="5a1f6-127">컬렉션&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="5a1f6-127">Collections &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/collections-master-data-services.md)  
  
  
