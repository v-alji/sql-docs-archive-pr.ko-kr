---
title: 모델 개체 권한(Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- permissions [Master Data Services], model objects
- models [Master Data Services], object permissions
ms.assetid: fab6335b-4cae-47de-ae7c-6c4743e0680f
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 4cc64d753b680cfabc3707a29c6d9de631708c20
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660010"
---
# <a name="model-object-permissions-master-data-services"></a><span data-ttu-id="dd90e-102">모델 개체 권한(Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="dd90e-102">Model Object Permissions (Master Data Services)</span></span>
  <span data-ttu-id="dd90e-103">모델 개체 권한은 필수 항목입니다.</span><span class="sxs-lookup"><span data-stu-id="dd90e-103">Model object permissions are mandatory.</span></span> <span data-ttu-id="dd90e-104">이 사용 권한은 사용자가 UI의 **탐색기** 기능 영역에서 액세스할 수 있는 특성을 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="dd90e-104">They determine the attributes a user can access in the **Explorer** functional area of the UI.</span></span>  
  
 <span data-ttu-id="dd90e-105">예를 들어 사용자에게 Product 엔터티에 대한 **업데이트** 권한을 할당하는 경우 사용자는 Product 엔터티의 모든 특성을 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dd90e-105">For example, if you assign a user **Update** permission to the Product entity, the user can update all of the attributes of the Product entity.</span></span> <span data-ttu-id="dd90e-106">단일 특성에 대해 **업데이트** 권한을 할당하는 경우 사용자는 해당 특성만 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dd90e-106">If you assign **Update** permission to a single attribute, the user can update that attribute only.</span></span>  
  
 <span data-ttu-id="dd90e-107">각 개별 특성 값에 할당된 보안을 확인하기 위해 모델 개체 사용 권한과 계층 멤버 사용 권한을 결합합니다. 이에 따라 사용자가 액세스할 수 있는 멤버가 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="dd90e-107">To determine security assigned on each individual attribute value, model object permissions are combined with hierarchy member permissions, which determine the members a user can access.</span></span>  
  
 <span data-ttu-id="dd90e-108">사용자에 게 **탐색기**외의 기능 영역에 대 한 액세스 권한을 부여 하려면 모델 관리자 여야 합니다. 여기에는 모델 개체 사용 권한 할당도 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="dd90e-108">To give a user access to a functional area other than **Explorer**, the user must be a model administrator, which also involves assigning model object permissions.</span></span> <span data-ttu-id="dd90e-109">자세한 내용은 [관리자 &#40;MDS(Master Data Services)&#41;](administrators-master-data-services.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="dd90e-109">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
 <span data-ttu-id="dd90e-110">모델 개체 사용 권한은 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] UI (사용자 인터페이스)의 **모델** 탭에 있는 **사용자 및 그룹 권한** 기능 영역에서 할당 됩니다. 이 탭에서 모델은 트리 구조로 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="dd90e-110">Model object permissions are assigned in the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] user interface (UI), in the **User and Group Permissions** functional area on the **Models** tab. On this tab, the model is represented as a tree structure.</span></span> <span data-ttu-id="dd90e-111">트리의 개체에 사용 권한을 할당하면 모든 하위 개체가 해당 권한을 상속합니다.</span><span class="sxs-lookup"><span data-stu-id="dd90e-111">When you assign permission to an object in the tree, all objects below inherit that permission.</span></span> <span data-ttu-id="dd90e-112">개별 개체에 사용 권한을 할당하면 이 상속을 재정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dd90e-112">You can override that inheritance by assigning permission to individual objects.</span></span>  
  
 <span data-ttu-id="dd90e-113">모델 개체에 **읽기**전용, **업데이트**또는 **거부** 권한을 할당할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dd90e-113">You can assign **Read-only**, **Update**, or **Deny** permission to model objects.</span></span> <span data-ttu-id="dd90e-114">**모델** 탭에서 사용 권한을 할당하지 않은 경우 사용자는 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]에서 모델이나 데이터를 볼 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="dd90e-114">If you do not assign any permissions on the **Models** tab, the user cannot view any models or data in [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)].</span></span>  
  
## <a name="best-practice"></a><span data-ttu-id="dd90e-115">모범 사례</span><span class="sxs-lookup"><span data-stu-id="dd90e-115">Best Practice</span></span>  
 <span data-ttu-id="dd90e-116">일반적으로 모델 개체에 대 한 **업데이트** 권한을 할당 한 다음 아래의 개체에 대 한 사용 권한을 명시적으로 할당 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd90e-116">In general, you should assign **Update** permission to the model object, and then explicitly assign permission to objects underneath.</span></span> <span data-ttu-id="dd90e-117">그 아래 개체에 대한 사용 권한을 할당하지 않는 경우 사용 권한이 상속되고 사용자는 관리자가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="dd90e-117">If you do not assign permission to objects underneath, the permissions are inherited and the user is an administrator.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd90e-118">참고 항목</span><span class="sxs-lookup"><span data-stu-id="dd90e-118">See Also</span></span>  
 <span data-ttu-id="dd90e-119">[모델 개체 사용 권한 할당 &#40;MDS(Master Data Services)&#41;](../../2014/master-data-services/assign-model-object-permissions-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="dd90e-119">[Assign Model Object Permissions &#40;Master Data Services&#41;](../../2014/master-data-services/assign-model-object-permissions-master-data-services.md) </span></span>  
 <span data-ttu-id="dd90e-120">[모델 권한 &#40;MDS(Master Data Services)&#41;](../../2014/master-data-services/model-permissions-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="dd90e-120">[Model Permissions &#40;Master Data Services&#41;](../../2014/master-data-services/model-permissions-master-data-services.md) </span></span>  
 <span data-ttu-id="dd90e-121">[기능 영역 권한 &#40;MDS(Master Data Services)&#41;](../../2014/master-data-services/functional-area-permissions-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="dd90e-121">[Functional Area Permissions &#40;Master Data Services&#41;](../../2014/master-data-services/functional-area-permissions-master-data-services.md) </span></span>  
 <span data-ttu-id="dd90e-122">[계층 멤버 권한 &#40;MDS(Master Data Services)&#41;](../../2014/master-data-services/hierarchy-member-permissions-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="dd90e-122">[Hierarchy Member Permissions &#40;Master Data Services&#41;](../../2014/master-data-services/hierarchy-member-permissions-master-data-services.md) </span></span>  
 [<span data-ttu-id="dd90e-123">사용 권한이 결정되는 방식&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="dd90e-123">How Permissions Are Determined &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/how-permissions-are-determined-master-data-services.md)  
  
  
