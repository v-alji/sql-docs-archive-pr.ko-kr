---
title: 엔터티 이름 변경 (MDS(Master Data Services)) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- entities [Master Data Services], changing name
ms.assetid: 6a5b9f14-6dfc-49d7-a771-e96461d4feae
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 9690fde44b0d56d790f4340779167fb55b400223
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728403"
---
# <a name="change-an-entity-name-master-data-services"></a><span data-ttu-id="3ae4d-102">엔터티 이름 변경(Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="3ae4d-102">Change an Entity Name (Master Data Services)</span></span>
  <span data-ttu-id="3ae4d-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]에서 엔터티의 이름을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3ae4d-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], you can change the name of an entity.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3ae4d-104">연결된 준비 테이블의 이름은 업데이트되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3ae4d-104">The names of the associated staging tables will not be updated.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="3ae4d-105">사전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="3ae4d-105">Prerequisites</span></span>  
 <span data-ttu-id="3ae4d-106">이 절차를 수행하려면</span><span class="sxs-lookup"><span data-stu-id="3ae4d-106">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="3ae4d-107">**시스템 관리** 기능 영역에 액세스할 수 있는 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3ae4d-107">You must have permission to access the **System Administration** functional area.</span></span>  
  
-   <span data-ttu-id="3ae4d-108">모델 관리자여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3ae4d-108">You must be a model administrator.</span></span> <span data-ttu-id="3ae4d-109">자세한 내용은 [관리자 &#40;MDS(Master Data Services)&#41;](administrators-master-data-services.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="3ae4d-109">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
### <a name="to-change-an-entity-name"></a><span data-ttu-id="3ae4d-110">엔터티 이름을 변경하려면</span><span class="sxs-lookup"><span data-stu-id="3ae4d-110">To change an entity name</span></span>  
  
1.  <span data-ttu-id="3ae4d-111">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]에서 **시스템 관리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3ae4d-111">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **System Administration**.</span></span>  
  
2.  <span data-ttu-id="3ae4d-112">**모델 뷰** 페이지의 메뉴 모음에서 **관리** 를 가리키고 **엔터티**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3ae4d-112">On the **Model View** page, from the menu bar, point to **Manage** and click **Entities**.</span></span>  
  
3.  <span data-ttu-id="3ae4d-113">**엔터티 유지 관리** 페이지의 **모델** 목록에서 모델을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3ae4d-113">On the **Entity Maintenance** page, from the **Model** list, select a model.</span></span>  
  
4.  <span data-ttu-id="3ae4d-114">이름을 변경할 엔터티의 행을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3ae4d-114">Click the row for the entity with the name you want to change.</span></span>  
  
5.  <span data-ttu-id="3ae4d-115">**선택한 엔터티 편집**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3ae4d-115">Click **Edit selected entity**.</span></span>  
  
6.  <span data-ttu-id="3ae4d-116">**엔터티 이름** 상자에 엔터티의 업데이트 된 이름을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="3ae4d-116">In the **Entity name** box, type the updated name of the entity.</span></span>  
  
7.  <span data-ttu-id="3ae4d-117">**엔터티 저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3ae4d-117">Click **Save entity**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ae4d-118">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3ae4d-118">See Also</span></span>  
 <span data-ttu-id="3ae4d-119">[엔터티 &#40;MDS(Master Data Services)를 만듭니다&#41;](create-an-entity-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="3ae4d-119">[Create an Entity &#40;Master Data Services&#41;](create-an-entity-master-data-services.md) </span></span>  
 <span data-ttu-id="3ae4d-120">[엔터티 &#40;MDS(Master Data Services) 삭제&#41;](delete-an-entity-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="3ae4d-120">[Delete an Entity &#40;Master Data Services&#41;](delete-an-entity-master-data-services.md) </span></span>  
 [<span data-ttu-id="3ae4d-121">엔터티&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="3ae4d-121">Entities &#40;Master Data Services&#41;</span></span>](entities-master-data-services.md)  
  
  
