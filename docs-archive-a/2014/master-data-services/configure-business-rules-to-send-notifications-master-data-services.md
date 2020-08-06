---
title: 알림을 보내도록 비즈니스 규칙 구성(Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- business rules [Master Data Services], configuring notifications
- e-mail [Master Data Services], configuring business rules
- notifications [Master Data Services], configuring business rules
ms.assetid: b24f7b11-ab53-4642-999c-e17b543b3558
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: cb1a12167dffe123e55760f031e21499fe22a945
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661708"
---
# <a name="configure-business-rules-to-send-notifications-master-data-services"></a><span data-ttu-id="f20a0-102">알림을 보내도록 비즈니스 규칙 구성(Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="f20a0-102">Configure Business Rules to Send Notifications (Master Data Services)</span></span>
  <span data-ttu-id="f20a0-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]에서는 특성 값 변경 내용을 사용자에게 알리려는 경우 알림을 보내도록 비즈니스 규칙을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f20a0-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], configure business rules to send notifications when you want to notify users about attribute value changes.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="f20a0-104">사전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="f20a0-104">Prerequisites</span></span>  
 <span data-ttu-id="f20a0-105">이 절차를 수행하려면</span><span class="sxs-lookup"><span data-stu-id="f20a0-105">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="f20a0-106">**시스템 관리** 와 **사용자 및 그룹 권한** 기능 영역에 액세스할 수 있는 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f20a0-106">You must have permission to access the **System Administration** and **User and Group Permissions** functional areas.</span></span> <span data-ttu-id="f20a0-107">**사용자 및 그룹 권한** 기능 영역에 대한 권한이 없으면 알림을 보낼 사용자 및 그룹 목록을 볼 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f20a0-107">If you do not have permission to the **User and Group Permissions** functional area, you cannot view the list of users and groups to send notifications to.</span></span>  
  
-   <span data-ttu-id="f20a0-108">모델 관리자여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f20a0-108">You must be a model administrator.</span></span> <span data-ttu-id="f20a0-109">자세한 내용은 [관리자 &#40;MDS(Master Data Services)&#41;](administrators-master-data-services.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f20a0-109">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="f20a0-110">유효성 검사 동작을 사용하는 비즈니스 규칙이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f20a0-110">A business rule that uses a validation action must already exist.</span></span> <span data-ttu-id="f20a0-111">자세한 내용은 [비즈니스 규칙 만들기 및 게시&#40;Master Data Services&#41;](../../2014/master-data-services/create-and-publish-a-business-rule-master-data-services.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f20a0-111">For more information, see [Create and Publish a Business Rule &#40;Master Data Services&#41;](../../2014/master-data-services/create-and-publish-a-business-rule-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="f20a0-112">알림을 받는 사용자 또는 그룹에게 유효성 검사를 통과하지 못한 특성에 대한 **읽기 전용** 이상의 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f20a0-112">The user or group that receives the notification must have at least **Read-only** permission to the attribute that fails validation.</span></span> <span data-ttu-id="f20a0-113">특성에 대한 사용 권한이 명시적 또는 암시적으로 거부된 사용자나 그룹의 경우 전자 메일을 받을 수는 있지만 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]에서 특성에 액세스할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f20a0-113">Users or groups that are explicitly or implicitly denied permission to the attribute will receive the email but will not be able to access the attribute in [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)].</span></span>  
  
-   <span data-ttu-id="f20a0-114">메일을 그룹에게 보내는 경우에는 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 에 액세스한 적이 있는 그룹의 멤버만 전자 메일을 받습니다.</span><span class="sxs-lookup"><span data-stu-id="f20a0-114">If mail is sent to a group, only members of the group that have accessed [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] will get the email.</span></span>  
  
### <a name="to-configure-business-rules-to-send-notifications"></a><span data-ttu-id="f20a0-115">알림을 보내도록 비즈니스 규칙을 구성하려면</span><span class="sxs-lookup"><span data-stu-id="f20a0-115">To configure business rules to send notifications</span></span>  
  
1.  <span data-ttu-id="f20a0-116">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]에서 **시스템 관리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f20a0-116">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **System Administration**.</span></span>  
  
2.  <span data-ttu-id="f20a0-117">메뉴 모음에서 **관리** 를 가리키고 **비즈니스 규칙**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f20a0-117">From the menu bar, point to **Manage** and click **Business Rules**.</span></span>  
  
3.  <span data-ttu-id="f20a0-118">**비즈니스 규칙 유지 관리** 페이지의 **모델** 목록에서 모델을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f20a0-118">On the **Business Rule Maintenance** page, from the **Model** list, select a model.</span></span>  
  
4.  <span data-ttu-id="f20a0-119">**엔터티** 목록에서 엔터티를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f20a0-119">From the **Entity** list, select an entity.</span></span>  
  
5.  <span data-ttu-id="f20a0-120">**멤버 유형** 목록에서 멤버 유형을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="f20a0-120">From the **Member Type** list, select a type of member.</span></span>  
  
6.  <span data-ttu-id="f20a0-121">**특성** 목록에서 특성을 선택하거나 기본값인 **모두**를 그대로 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="f20a0-121">From the **Attribute** list, select an attribute or leave the default of **All**.</span></span>  
  
7.  <span data-ttu-id="f20a0-122">표 형태의 비즈니스 규칙 행에서 **알림** 필드를 두 번 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="f20a0-122">In the grid, in the row for the business rule, double-click the **Notification** field.</span></span>  
  
8.  <span data-ttu-id="f20a0-123">하위 메뉴에서 전자 메일 알림을 보낼 사용자 또는 그룹을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f20a0-123">From the sub-menu, click a user or group to send the email notification to.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="f20a0-124">다음 단계</span><span class="sxs-lookup"><span data-stu-id="f20a0-124">Next Steps</span></span>  
  
-   <span data-ttu-id="f20a0-125">다음 절차 중 하나를 수행하여 비즈니스 규칙을 데이터에 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="f20a0-125">Apply business rules to data by following one of these procedures:</span></span>  
  
    -   [<span data-ttu-id="f20a0-126">비즈니스 규칙에 대해 특정 멤버 유효성 검사&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="f20a0-126">Validate Specific Members against Business Rules &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/validate-specific-members-against-business-rules-master-data-services.md)  
  
    -   [<span data-ttu-id="f20a0-127">비즈니스 규칙에 대해 버전 유효성 검사&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="f20a0-127">Validate a Version against Business Rules &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/validate-a-version-against-business-rules-master-data-services.md)  
  
-   <span data-ttu-id="f20a0-128">다음과 같이 전자 메일 프로토콜을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="f20a0-128">Configure the email protocol as follows:</span></span>  
  
    -   [<span data-ttu-id="f20a0-129">메일 알림 구성&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="f20a0-129">Configure Email Notifications &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/configure-email-notifications-master-data-services.md)  
  
## <a name="see-also"></a><span data-ttu-id="f20a0-130">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f20a0-130">See Also</span></span>  
 <span data-ttu-id="f20a0-131">[알림 &#40;MDS(Master Data Services)&#41;](../../2014/master-data-services/notifications-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="f20a0-131">[Notifications &#40;Master Data Services&#41;](../../2014/master-data-services/notifications-master-data-services.md) </span></span>  
 [<span data-ttu-id="f20a0-132">메일 알림 구성&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="f20a0-132">Configure Email Notifications &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/configure-email-notifications-master-data-services.md)  
  
  
