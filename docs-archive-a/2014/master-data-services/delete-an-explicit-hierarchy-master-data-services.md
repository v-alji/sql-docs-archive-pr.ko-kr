---
title: 명시적 계층 삭제(Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- explicit hierarchies, deleting
- deleting explicit hierarchies [Master Data Services]
ms.assetid: 4ce177b0-9884-47a2-9cea-212e845dd762
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 744f96a2705a3abbc2318ecd3c9b0c7fffb7605e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661700"
---
# <a name="delete-an-explicit-hierarchy-master-data-services"></a><span data-ttu-id="c76f1-102">명시적 계층 삭제(Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="c76f1-102">Delete an Explicit Hierarchy (Master Data Services)</span></span>
  <span data-ttu-id="c76f1-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]에서는 명시적 계층이 더 이상 필요하지 않으면 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c76f1-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], delete an explicit hierarchy when you no longer need it.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="c76f1-104">명시적 계층을 삭제하면 해당 계층의 모든 통합 멤버도 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="c76f1-104">When you delete an explicit hierarchy, all consolidated members in the hierarchy are deleted also.</span></span> <span data-ttu-id="c76f1-105">엔터티에 대한 모든 명시적 계층을 삭제하면 해당 엔터티의 모든 컬렉션도 삭제되며 명시적 계층과 컬렉션에 대해 엔터티를 더 이상 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c76f1-105">If you delete all explicit hierarchies for an entity, all collections for the entity are also deleted and the entity is no longer enabled for explicit hierarchies and collections.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="c76f1-106">사전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="c76f1-106">Prerequisites</span></span>  
 <span data-ttu-id="c76f1-107">이 절차를 수행하려면</span><span class="sxs-lookup"><span data-stu-id="c76f1-107">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="c76f1-108">**시스템 관리** 기능 영역에 액세스할 수 있는 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c76f1-108">You must have permission to access the **System Administration** functional area.</span></span>  
  
-   <span data-ttu-id="c76f1-109">모델 관리자여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c76f1-109">You must be a model administrator.</span></span> <span data-ttu-id="c76f1-110">자세한 내용은 [관리자 &#40;MDS(Master Data Services)&#41;](administrators-master-data-services.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="c76f1-110">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
### <a name="to-delete-an-explicit-hierarchy"></a><span data-ttu-id="c76f1-111">명시적 계층을 삭제하려면</span><span class="sxs-lookup"><span data-stu-id="c76f1-111">To delete an explicit hierarchy</span></span>  
  
1.  <span data-ttu-id="c76f1-112">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]에서 **시스템 관리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c76f1-112">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **System Administration**.</span></span>  
  
2.  <span data-ttu-id="c76f1-113">**모델 뷰** 페이지의 메뉴 모음에서 **관리** 를 가리키고 **엔터티**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c76f1-113">On the **Model View** page, from the menu bar, point to **Manage** and click **Entities**.</span></span>  
  
3.  <span data-ttu-id="c76f1-114">**엔터티 유지 관리** 페이지의 **모델** 목록에서 모델을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c76f1-114">On the **Entity Maintenance** page, from the **Model** list, select a model.</span></span>  
  
4.  <span data-ttu-id="c76f1-115">삭제할 명시적 계층이 포함된 엔터티의 행을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c76f1-115">Select the row for the entity that contains the explicit hierarchy you want to delete.</span></span>  
  
5.  <span data-ttu-id="c76f1-116">**선택한 엔터티 편집**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c76f1-116">Click **Edit selected entity**.</span></span>  
  
6.  <span data-ttu-id="c76f1-117">**엔터티 편집** 페이지의 **명시적 계층** 창에서 삭제 하려는 명시적 계층을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c76f1-117">On the **Edit Entity** page, in the **Explicit Hierarchies** pane, click the explicit hierarchy you want to delete.</span></span>  
  
7.  <span data-ttu-id="c76f1-118">**선택한 계층 삭제**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c76f1-118">Click **Delete selected hierarchy**.</span></span>  
  
8.  <span data-ttu-id="c76f1-119">확인 대화 상자에서 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c76f1-119">In the confirmation dialog box, click **OK**.</span></span>  
  
9. <span data-ttu-id="c76f1-120">추가 확인 대화 상자에서 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c76f1-120">In the additional confirmation dialog box, click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c76f1-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c76f1-121">See Also</span></span>  
 <span data-ttu-id="c76f1-122">[명시적 계층 &#40;MDS(Master Data Services)를 만듭니다&#41;](../../2014/master-data-services/create-an-explicit-hierarchy-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="c76f1-122">[Create an Explicit Hierarchy &#40;Master Data Services&#41;](../../2014/master-data-services/create-an-explicit-hierarchy-master-data-services.md) </span></span>  
 [<span data-ttu-id="c76f1-123">명시적 계층&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="c76f1-123">Explicit Hierarchies &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/explicit-hierarchies-master-data-services.md)  
  
  
