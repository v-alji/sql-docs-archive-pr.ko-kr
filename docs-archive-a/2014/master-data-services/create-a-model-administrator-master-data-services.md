---
title: 모델 관리자 만들기(Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- administrators [Master Data Services], creating
ms.assetid: dae17afc-3b39-490e-b51f-2d8da26d429e
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 24efc3961e6ed5b9f41b2321dfcc4fbf16632270
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661221"
---
# <a name="create-a-model-administrator-master-data-services"></a><span data-ttu-id="cd606-102">모델 관리자 만들기(Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="cd606-102">Create a Model Administrator (Master Data Services)</span></span>
  <span data-ttu-id="cd606-103">에서 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 그룹이 나 사용자에 게 하나 이상의 모델에 있는 모든 개체에 대 한 **업데이트** 권한을 부여 하려면 모델 관리자를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="cd606-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], create a model administrator when you want a group or user to have **Update** permission to all objects in one or more models.</span></span>  
  
> [!TIP]  
>  <span data-ttu-id="cd606-104">관리를 간소화 하려면 Windows 또는 로컬 그룹을 만들고이를 모델 관리자로 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd606-104">To simplify administration, create a Windows or local group and configure it as a model administrator.</span></span> <span data-ttu-id="cd606-105">그러면 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]에 액세스하지 않고 그룹에서 사용자를 추가하고 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cd606-105">You can then add and remove users from the group without accessing [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)].</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="cd606-106">사전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="cd606-106">Prerequisites</span></span>  
 <span data-ttu-id="cd606-107">이 절차를 수행하려면</span><span class="sxs-lookup"><span data-stu-id="cd606-107">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="cd606-108">**사용자 및 그룹 권한** 기능 영역에 액세스할 수 있는 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd606-108">You must have permission to access the **User and Group Permissions** functional area.</span></span>  
  
-   <span data-ttu-id="cd606-109">모델 관리자여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd606-109">You must be a model administrator.</span></span> <span data-ttu-id="cd606-110">자세한 내용은 [관리자 &#40;MDS(Master Data Services)&#41;](administrators-master-data-services.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="cd606-110">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
### <a name="to-create-a-model-administrator"></a><span data-ttu-id="cd606-111">모델 관리자를 만들려면</span><span class="sxs-lookup"><span data-stu-id="cd606-111">To create a model administrator</span></span>  
  
1.  <span data-ttu-id="cd606-112">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]에서 **사용자 및 그룹 권한**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cd606-112">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **User and Group Permissions**.</span></span>  
  
2.  <span data-ttu-id="cd606-113">**사용자** 또는 **그룹** 페이지에서 편집하려는 사용자나 그룹의 행을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="cd606-113">On the **Users** or **Groups** page, select the row for the user or group that you want to edit.</span></span>  
  
3.  <span data-ttu-id="cd606-114">**선택한 사용자 편집**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cd606-114">Click **Edit selected user**.</span></span>  
  
4.  <span data-ttu-id="cd606-115">**모델** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cd606-115">Click the **Models** tab.</span></span>  
  
5.  <span data-ttu-id="cd606-116">또는 **모델** 목록에서 모델을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="cd606-116">Optionally, select a model from the **Model** list.</span></span>  
  
6.  <span data-ttu-id="cd606-117">**편집**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cd606-117">Click **Edit**.</span></span>  
  
7.  <span data-ttu-id="cd606-118">사용 권한을 부여할 모델을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cd606-118">Click the model you want to grant permission to.</span></span>  
  
8.  <span data-ttu-id="cd606-119">메뉴에서 **업데이트**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd606-119">From the menu, select **Update**.</span></span>  
  
9. <span data-ttu-id="cd606-120">그룹 또는 사용자를 관리자로 만들 각 모델에 대해 7단계와 8단계를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="cd606-120">Complete steps 7 and 8 for each model you want the group or user to be an administrator for.</span></span>  
  
10. <span data-ttu-id="cd606-121">**저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cd606-121">Click **Save**.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cd606-122">설명</span><span class="sxs-lookup"><span data-stu-id="cd606-122">Remarks</span></span>  
 <span data-ttu-id="cd606-123">모델 개체 또는 계층 멤버에 다른 사용 권한을 할당하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="cd606-123">Do not assign any other permissions to model objects or hierarchy members.</span></span> <span data-ttu-id="cd606-124">이렇게 하면 사용자가 더 이상 관리자가 아니므로 **탐색기**외의 모든 기능 영역에서 모델을 볼 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="cd606-124">If you do, the user is no longer an administrator and cannot view the model in any functional area other than **Explorer**.</span></span>  
  
 <span data-ttu-id="cd606-125">한 가지 예외가 있습니다. 사용자가 **계층 멤버** 탭의 계층 **루트** 에 할당 된 **업데이트** 권한이 있는 경우 사용자는 여전히 모델 관리자로 간주 됩니다.</span><span class="sxs-lookup"><span data-stu-id="cd606-125">There is one exception: if the user has **Update** permission assigned to a hierarchy **Root** on the **Hierarchy Members** tab, the user is still considered a model administrator.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd606-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="cd606-126">See Also</span></span>  
 <span data-ttu-id="cd606-127">[관리자는 MDS(Master Data Services) &#40;&#41;](administrators-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="cd606-127">[Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md) </span></span>  
 <span data-ttu-id="cd606-128">[모델 개체 사용 권한 할당 &#40;MDS(Master Data Services)&#41;](../../2014/master-data-services/assign-model-object-permissions-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="cd606-128">[Assign Model Object Permissions &#40;Master Data Services&#41;](../../2014/master-data-services/assign-model-object-permissions-master-data-services.md) </span></span>  
 <span data-ttu-id="cd606-129">[계층 멤버 권한 할당 &#40;MDS(Master Data Services)&#41;](../../2014/master-data-services/assign-hierarchy-member-permissions-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="cd606-129">[Assign Hierarchy Member Permissions &#40;Master Data Services&#41;](../../2014/master-data-services/assign-hierarchy-member-permissions-master-data-services.md) </span></span>  
 <span data-ttu-id="cd606-130">[모델 개체 사용 권한 &#40;MDS(Master Data Services)&#41;](../../2014/master-data-services/model-object-permissions-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="cd606-130">[Model Object Permissions &#40;Master Data Services&#41;](../../2014/master-data-services/model-object-permissions-master-data-services.md) </span></span>  
 [<span data-ttu-id="cd606-131">계층 멤버 권한&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="cd606-131">Hierarchy Member Permissions &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/hierarchy-member-permissions-master-data-services.md)  
  
  
