---
title: 엔터티 권한(Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- entities [Master Data Services], permissions
- permissions [Master Data Services], entities
ms.assetid: 22785062-4faf-46ee-bffa-01cbd6d5a5b3
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: eaec809cb0f9dea3f760958bcf95015edd5a490e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728384"
---
# <a name="entity-permissions-master-data-services"></a><span data-ttu-id="33121-102">엔터티 권한(Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="33121-102">Entity Permissions (Master Data Services)</span></span>
  <span data-ttu-id="33121-103">엔터티 권한은 다음에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="33121-103">Entity permissions apply to:</span></span>  
  
-   <span data-ttu-id="33121-104">리프 멤버 및 통합 멤버 둘 다의 **이름** 및 **코드**를 포함하여 엔터티의 모든 특성</span><span class="sxs-lookup"><span data-stu-id="33121-104">All of the entity's attributes, including **Name** and **Code**, for both leaf and consolidated members.</span></span>  
  
-   <span data-ttu-id="33121-105">엔터티의 모든 컬렉션</span><span class="sxs-lookup"><span data-stu-id="33121-105">All of the entity's collections.</span></span>  
  
-   <span data-ttu-id="33121-106">명시적 계층 멤버 자격 및 관계</span><span class="sxs-lookup"><span data-stu-id="33121-106">Explicit hierarchy memberships and relationships.</span></span>  
  
 <span data-ttu-id="33121-107">엔터티에 대한 사용 권한이 있는 경우 해당 엔터티, 명시적 계층 및 컬렉션에서 멤버를 추가하거나 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="33121-107">When you have permission to an entity, you can add and remove members from the entity, its explicit hierarchies, and its collections.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="33121-108">이러한 사용 권한은 사용자 인터페이스의 **탐색기** 기능 영역에만 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="33121-108">These permissions apply to the **Explorer** functional area of the user interface only.</span></span>  
  
|<span data-ttu-id="33121-109">사용 권한</span><span class="sxs-lookup"><span data-stu-id="33121-109">Permission</span></span>|<span data-ttu-id="33121-110">Description</span><span class="sxs-lookup"><span data-stu-id="33121-110">Description</span></span>|  
|----------------|-----------------|  
|<span data-ttu-id="33121-111">**읽기 전용**</span><span class="sxs-lookup"><span data-stu-id="33121-111">**Read-only**</span></span>|<span data-ttu-id="33121-112">엔터티가 표시되지만 사용자가 멤버를 추가, 제거 또는 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="33121-112">The entity is displayed but the user cannot add, remove, or change members.</span></span>|  
|<span data-ttu-id="33121-113">**Update**</span><span class="sxs-lookup"><span data-stu-id="33121-113">**Update**</span></span>|<span data-ttu-id="33121-114">엔터티가 표시되고 사용자가 멤버를 추가, 제거 및 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="33121-114">The entity is displayed and the user can add, remove, and change members.</span></span>|  
|<span data-ttu-id="33121-115">**Deny**</span><span class="sxs-lookup"><span data-stu-id="33121-115">**Deny**</span></span>|<span data-ttu-id="33121-116">엔터티가 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="33121-116">The entity is not displayed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="33121-117">참고 항목</span><span class="sxs-lookup"><span data-stu-id="33121-117">See Also</span></span>  
 <span data-ttu-id="33121-118">[모델 개체 사용 권한 할당 &#40;MDS(Master Data Services)&#41;](assign-model-object-permissions-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="33121-118">[Assign Model Object Permissions &#40;Master Data Services&#41;](assign-model-object-permissions-master-data-services.md) </span></span>  
 <span data-ttu-id="33121-119">[모델 개체 사용 권한 &#40;MDS(Master Data Services)&#41;](../../2014/master-data-services/model-object-permissions-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="33121-119">[Model Object Permissions &#40;Master Data Services&#41;](../../2014/master-data-services/model-object-permissions-master-data-services.md) </span></span>  
 [<span data-ttu-id="33121-120">엔터티&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="33121-120">Entities &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/entities-master-data-services.md)  
  
  
