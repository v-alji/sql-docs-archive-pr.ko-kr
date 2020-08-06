---
title: 모델 개체 사용 권한 할당(Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- models [Master Data Services], assigning object permissions
- permissions [Master Data Services], assigning model object permissions
ms.assetid: 4b80148d-2318-415c-9479-28c240e48bcd
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 92ac8ef3ac63b7128c4cbb7e9305ee6bd56ca010
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651760"
---
# <a name="assign-model-object-permissions-master-data-services"></a><span data-ttu-id="da776-102">모델 개체 사용 권한 할당(Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="da776-102">Assign Model Object Permissions (Master Data Services)</span></span>
  <span data-ttu-id="da776-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]에서 **의** 탐색기 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]기능 영역에 있는 데이터에 대해 사용자 또는 그룹 액세스 권한을 부여해야 하거나 사용자나 그룹을 관리자로 지정해야 할 경우 모델 개체에 사용 권한을 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="da776-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], assign permissions to model objects when you need to give a user or group access to data in the **Explorer** functional area of [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], or when you need to make a user or group an administrator.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="da776-104">모델에 사용 권한을 할당하면 다른 모든 모델에 대한 사용 권한이 암시적으로 거부됩니다.</span><span class="sxs-lookup"><span data-stu-id="da776-104">When you assign permission to a model, permission to all other models is implicitly denied.</span></span> <span data-ttu-id="da776-105">모델 개체 사용 권한을 할당하지 않으면 사용자나 그룹이 **탐색기**에서 데이터에 액세스할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="da776-105">If you do not assign model object permissions, the user or group cannot access any data in **Explorer**.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="da776-106">사전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="da776-106">Prerequisites</span></span>  
 <span data-ttu-id="da776-107">이 절차를 수행하려면</span><span class="sxs-lookup"><span data-stu-id="da776-107">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="da776-108">**사용자 및 그룹 권한** 기능 영역에 액세스할 수 있는 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="da776-108">You must have permission to access the **Users and Group Permissions** functional area.</span></span>  
  
-   <span data-ttu-id="da776-109">모델 관리자여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="da776-109">You must be a model administrator.</span></span> <span data-ttu-id="da776-110">자세한 내용은 [관리자 &#40;MDS(Master Data Services)&#41;](administrators-master-data-services.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="da776-110">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
### <a name="to-assign-model-object-permissions"></a><span data-ttu-id="da776-111">모델 개체 사용 권한을 할당하려면</span><span class="sxs-lookup"><span data-stu-id="da776-111">To assign model object permissions</span></span>  
  
1.  <span data-ttu-id="da776-112">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]에서 **사용자 및 그룹 권한**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="da776-112">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **User and Group Permissions**.</span></span>  
  
2.  <span data-ttu-id="da776-113">**사용자** 또는 **그룹** 페이지에서 편집하려는 사용자나 그룹의 행을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="da776-113">On the **Users** or **Groups** page, select the row for the user or group that you want to edit.</span></span>  
  
3.  <span data-ttu-id="da776-114">**선택한 사용자 편집**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="da776-114">Click **Edit selected user**.</span></span>  
  
4.  <span data-ttu-id="da776-115">**모델** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="da776-115">Click the **Models** tab.</span></span>  
  
5.  <span data-ttu-id="da776-116">또는 **모델** 목록에서 모델을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="da776-116">Optionally, select a model from the **Model** list.</span></span>  
  
6.  <span data-ttu-id="da776-117">**편집**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="da776-117">Click **Edit**.</span></span>  
  
7.  <span data-ttu-id="da776-118">트리를 확장하고 사용 권한을 할당하려는 모델 개체를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="da776-118">Expand the tree, and click the model object you want to assign permissions to.</span></span>  
  
8.  <span data-ttu-id="da776-119">메뉴에서 **읽기**전용, **업데이트**또는 **거부**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="da776-119">From the menu, select **Read-only**, **Update**, or **Deny**.</span></span>  
  
9. <span data-ttu-id="da776-120">**저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="da776-120">Click **Save**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="da776-121">다음 단계</span><span class="sxs-lookup"><span data-stu-id="da776-121">Next Steps</span></span>  
  
-   <span data-ttu-id="da776-122">(옵션) [계층 멤버 권한 할당&#40;Master Data Services&#41;](../../2014/master-data-services/assign-hierarchy-member-permissions-master-data-services.md)</span><span class="sxs-lookup"><span data-stu-id="da776-122">(Optional) [Assign Hierarchy Member Permissions &#40;Master Data Services&#41;](../../2014/master-data-services/assign-hierarchy-member-permissions-master-data-services.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da776-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="da776-123">See Also</span></span>  
 <span data-ttu-id="da776-124">[모델 개체 사용 권한 삭제 &#40;MDS(Master Data Services)&#41;](../../2014/master-data-services/delete-model-object-permissions-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="da776-124">[Delete Model Object Permissions &#40;Master Data Services&#41;](../../2014/master-data-services/delete-model-object-permissions-master-data-services.md) </span></span>  
 <span data-ttu-id="da776-125">[모델 개체 사용 권한 &#40;MDS(Master Data Services)&#41;](../../2014/master-data-services/model-object-permissions-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="da776-125">[Model Object Permissions &#40;Master Data Services&#41;](../../2014/master-data-services/model-object-permissions-master-data-services.md) </span></span>  
 [<span data-ttu-id="da776-126">모델 관리자 만들기&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="da776-126">Create a Model Administrator &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-a-model-administrator-master-data-services.md)  
  
  
