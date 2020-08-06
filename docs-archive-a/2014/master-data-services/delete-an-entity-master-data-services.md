---
title: 엔터티 삭제(Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- entities [Master Data Services], deleting
- deleting entities [Master Data Services]
ms.assetid: 71fffb03-38fd-46f0-9e10-6ec75da19ab2
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: f1920b9b77a8d46035308eed9ce251b9fbc8228f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661217"
---
# <a name="delete-an-entity-master-data-services"></a><span data-ttu-id="9b855-102">엔터티 삭제(Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="9b855-102">Delete an Entity (Master Data Services)</span></span>
  <span data-ttu-id="9b855-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]에서 엔터티를 삭제하여 엔터티의 모든 멤버와 특성을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="9b855-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], delete an entity to delete all members and attributes for the entity.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9b855-104">모든 버전의 엔터티의 멤버가 영구적으로 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="9b855-104">The entity's members from all versions will be permanently deleted.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="9b855-105">사전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="9b855-105">Prerequisites</span></span>  
 <span data-ttu-id="9b855-106">이 절차를 수행하려면</span><span class="sxs-lookup"><span data-stu-id="9b855-106">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="9b855-107">**시스템 관리** 기능 영역에 액세스할 수 있는 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b855-107">You must have permission to access the **System Administration** functional area.</span></span>  
  
-   <span data-ttu-id="9b855-108">모델 관리자여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b855-108">You must be a model administrator.</span></span> <span data-ttu-id="9b855-109">자세한 내용은 [관리자 &#40;MDS(Master Data Services)&#41;](administrators-master-data-services.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="9b855-109">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
### <a name="to-delete-an-entity"></a><span data-ttu-id="9b855-110">엔터티를 삭제하려면</span><span class="sxs-lookup"><span data-stu-id="9b855-110">To delete an entity</span></span>  
  
1.  <span data-ttu-id="9b855-111">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]에서 **시스템 관리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9b855-111">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **System Administration**.</span></span>  
  
2.  <span data-ttu-id="9b855-112">**모델 뷰** 페이지의 메뉴 모음에서 **관리** 를 가리키고 **엔터티**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9b855-112">On the **Model View** page, from the menu bar, point to **Manage** and click **Entities**.</span></span>  
  
3.  <span data-ttu-id="9b855-113">**엔터티 유지 관리** 페이지의 **모델** 목록에서 모델을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="9b855-113">On the **Entity Maintenance** page, from the **Model** list, select a model.</span></span>  
  
4.  <span data-ttu-id="9b855-114">삭제하려는 엔터티의 행을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="9b855-114">Select the row for the entity that you want to delete.</span></span>  
  
5.  <span data-ttu-id="9b855-115">**선택한 엔터티 삭제**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b855-115">Click **Delete selected entity**.</span></span>  
  
6.  <span data-ttu-id="9b855-116">확인 대화 상자에서 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9b855-116">In the confirmation dialog box, click **OK**.</span></span>  
  
7.  <span data-ttu-id="9b855-117">추가 확인 대화 상자에서 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9b855-117">In the additional confirmation dialog box, click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b855-118">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9b855-118">See Also</span></span>  
 <span data-ttu-id="9b855-119">[엔터티 &#40;MDS(Master Data Services)&#41;](../../2014/master-data-services/entities-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="9b855-119">[Entities &#40;Master Data Services&#41;](../../2014/master-data-services/entities-master-data-services.md) </span></span>  
 [<span data-ttu-id="9b855-120">엔터티 만들기&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="9b855-120">Create an Entity &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-an-entity-master-data-services.md)  
  
  
