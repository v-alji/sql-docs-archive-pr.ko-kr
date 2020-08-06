---
title: 관리자(Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- administrators [Master Data Services], about administrators
- administrators [Master Data Services]
- models [Master Data Services], administrators
ms.assetid: d330aa4e-6ade-4b09-b376-1b15d6c78f7d
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 52e16d4e77acc0a6b50b87e00184918cb9ce64b1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734240"
---
# <a name="administrators-master-data-services"></a><span data-ttu-id="56d45-102">관리자(Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="56d45-102">Administrators (Master Data Services)</span></span>
  <span data-ttu-id="56d45-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]에는 모델 관리자와 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 시스템 관리자의 두 가지 관리자 유형이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="56d45-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], there are two types of administrators: model administrators, and the [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] system administrator.</span></span>  
  
## <a name="model-administrators"></a><span data-ttu-id="56d45-104">모델 관리자</span><span class="sxs-lookup"><span data-stu-id="56d45-104">Model Administrators</span></span>  
 <span data-ttu-id="56d45-105">에서 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 모델 관리자는 **모델 개체** 탭의 최상위 모델 개체에 할당 된 **업데이트** 권한이 있고 다른 할당 된 권한은 없는 사용자입니다.</span><span class="sxs-lookup"><span data-stu-id="56d45-105">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], a model administrator is a user who has **Update** permission assigned to the top-level model object on the **Model Objects** tab and no other assigned permissions.</span></span>  
  
-   <span data-ttu-id="56d45-106">**탐색기** 기능 영역에 대한 액세스 권한을 가진 사용자는 이 영역에서 모든 마스터 데이터를 추가하고, 삭제하고, 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="56d45-106">If the user has access to the **Explorer** functional area, the user can add, delete, and update all master data in this area.</span></span>  
  
-   <span data-ttu-id="56d45-107">다른 기능 영역에 대한 액세스 권한을 가진 사용자는 해당 영역에서 사용할 수 있는 모든 관리 태스크를 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="56d45-107">If the user has access to other functional areas, the user can perform all administrative tasks available in the functional area.</span></span>  
  
 <span data-ttu-id="56d45-108">각 모델은 여러 관리자를 가질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="56d45-108">Each model can have multiple administrators.</span></span> <span data-ttu-id="56d45-109">각 사용자는 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 배포에서 한 개, 여러 개 또는 모든 모델에 대한 모델 관리자일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="56d45-109">Each user can be a model administrator for one, several, or all models in the [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] deployment.</span></span>  
  
 <span data-ttu-id="56d45-110">사용자는 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 에서 또는 프로그래밍 방식으로 모델 관리자로 구성될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="56d45-110">A user can be configured as a model administrator either in [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] or programmatically.</span></span> <span data-ttu-id="56d45-111">자세한 내용은 [모델 관리자 만들기&#40;Master Data Services&#41;](create-a-model-administrator-master-data-services.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="56d45-111">For more information, see [Create a Model Administrator &#40;Master Data Services&#41;](create-a-model-administrator-master-data-services.md).</span></span>  
  
## <a name="master-data-services-system-administrator"></a><span data-ttu-id="56d45-112">Master Data Services 시스템 관리자</span><span class="sxs-lookup"><span data-stu-id="56d45-112">Master Data Services System Administrator</span></span>  
 <span data-ttu-id="56d45-113">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 시스템 관리자는 한 명뿐입니다.</span><span class="sxs-lookup"><span data-stu-id="56d45-113">There is only one [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] system administrator.</span></span> <span data-ttu-id="56d45-114">시스템 관리자는 데이터베이스를 만들 때 **관리자 계정** 에 대해 지정 된 사용자입니다 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="56d45-114">The system administrator is the user specified for the **Administrator Account** when you create the [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] database.</span></span>  
  
 <span data-ttu-id="56d45-115">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 시스템 관리자:</span><span class="sxs-lookup"><span data-stu-id="56d45-115">The [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] system administrator:</span></span>  
  
-   <span data-ttu-id="56d45-116">모든 기능 영역에 대한 액세스 권한을 자동으로 가집니다.</span><span class="sxs-lookup"><span data-stu-id="56d45-116">Automatically has access to all functional areas.</span></span>  
  
-   <span data-ttu-id="56d45-117">**탐색기** 기능 영역에서 모든 모델에 대 한 모든 마스터 데이터를 추가, 삭제 및 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="56d45-117">Can add, delete, and update all master data for all models in the **Explorer** functional area.</span></span>  
  
 <span data-ttu-id="56d45-118">시스템 관리자로 할당된 사용자는 변경이 가능합니다.</span><span class="sxs-lookup"><span data-stu-id="56d45-118">You can change the user who is assigned as the system administrator.</span></span> <span data-ttu-id="56d45-119">자세한 내용은 [MDS(Master Data Services)&#41;&#40;시스템 관리자 계정 변경 ](../../2014/master-data-services/change-the-system-administrator-account-master-data-services.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="56d45-119">For more information, see [Change the System Administrator Account &#40;Master Data Services&#41;](../../2014/master-data-services/change-the-system-administrator-account-master-data-services.md).</span></span>  
  
## <a name="comparing-administrator-types"></a><span data-ttu-id="56d45-120">관리자 유형 비교</span><span class="sxs-lookup"><span data-stu-id="56d45-120">Comparing Administrator Types</span></span>  
  
|<span data-ttu-id="56d45-121">관리자 유형</span><span class="sxs-lookup"><span data-stu-id="56d45-121">Administrator Type</span></span>|<span data-ttu-id="56d45-122">Description</span><span class="sxs-lookup"><span data-stu-id="56d45-122">Description</span></span>|  
|------------------------|-----------------|  
|[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] <span data-ttu-id="56d45-123">시스템 관리자</span><span class="sxs-lookup"><span data-stu-id="56d45-123">system administrator</span></span>|<span data-ttu-id="56d45-124">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]에서 할당된 사용 권한은 관리자의 액세스 권한 아무런 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="56d45-124">Permissions assigned in [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] have no effect on the administrator's access.</span></span><br /><br /> <span data-ttu-id="56d45-125">모든 모델에 대 한 **업데이트** 권한이 자동으로 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="56d45-125">Automatically has **Update** permission to all models.</span></span><br /><br /> <span data-ttu-id="56d45-126">모든 기능 영역에 대한 액세스 권한을 자동으로 가집니다.</span><span class="sxs-lookup"><span data-stu-id="56d45-126">Automatically has access to all functional areas.</span></span><br /><br /> <span data-ttu-id="56d45-127">Mdm. tblUser에서 **ID** 열의 값은 **1**입니다.</span><span class="sxs-lookup"><span data-stu-id="56d45-127">In mdm.tblUser, the value in the **ID** column is **1**.</span></span>|  
|<span data-ttu-id="56d45-128">모델 관리자</span><span class="sxs-lookup"><span data-stu-id="56d45-128">Model administrator</span></span>|<span data-ttu-id="56d45-129">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]에서 할당된 권한에 따라 사용자가 모델 관리자인지 여부가 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="56d45-129">Permissions assigned in [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] determine whether or not the user is a model administrator.</span></span><br /><br /> <span data-ttu-id="56d45-130">명시적으로 할당된 사용 권한이나 그룹에서 상속된 사용 권한을 기반으로 하는 모델 관리자일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="56d45-130">Can be a model administrator based on permissions assigned explicitly or permissions inherited from a group.</span></span><br /><br /> <span data-ttu-id="56d45-131">는 최상위 모델 개체에 할당 된 **업데이트** 권한이 있고 다른 사용 권한은 없는 모델에 대 한 관리자만 해당 합니다.</span><span class="sxs-lookup"><span data-stu-id="56d45-131">Is an administrator only for models that have **Update** permission assigned to top-level model object, and no other permissions.</span></span><br /><br /> <span data-ttu-id="56d45-132">액세스 권한이 부여된 기능 영역에 대해서만 액세스 권한을 가집니다.</span><span class="sxs-lookup"><span data-stu-id="56d45-132">Has access only to functional areas that access is granted to.</span></span><br /><br /> <span data-ttu-id="56d45-133">Mdm. tblUser에서 **ID** 열의 값은 **1**이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="56d45-133">In mdm.tblUser, the value in the **ID** column is not **1**.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="56d45-134">참고 항목</span><span class="sxs-lookup"><span data-stu-id="56d45-134">See Also</span></span>  
 <span data-ttu-id="56d45-135">[모델 관리자 &#40;MDS(Master Data Services)를 만듭니다&#41;](create-a-model-administrator-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="56d45-135">[Create a Model Administrator &#40;Master Data Services&#41;](create-a-model-administrator-master-data-services.md) </span></span>  
 <span data-ttu-id="56d45-136">[시스템 관리자 계정 변경 &#40;MDS(Master Data Services)&#41;](../../2014/master-data-services/change-the-system-administrator-account-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="56d45-136">[Change the System Administrator Account &#40;Master Data Services&#41;](../../2014/master-data-services/change-the-system-administrator-account-master-data-services.md) </span></span>  
 <span data-ttu-id="56d45-137">[MDS(Master Data Services) 데이터베이스 만들기](install-windows/create-a-master-data-services-database.md) </span><span class="sxs-lookup"><span data-stu-id="56d45-137">[Create a Master Data Services Database](install-windows/create-a-master-data-services-database.md) </span></span>  
 [<span data-ttu-id="56d45-138">알림&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="56d45-138">Notifications &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/notifications-master-data-services.md)  
  
  
