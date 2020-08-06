---
title: 전자 메일 알림 구성(Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- e-mail [Master Data Services], configuring
- notifications [Master Data Services], configuring notifications
ms.assetid: 4241a6ab-7465-471b-9890-57c6b572037e
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: baf60677435122af00f5ee5492e47bafaa45a3ac
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661707"
---
# <a name="configure-email-notifications-master-data-services"></a><span data-ttu-id="89ca3-102">전자 메일 알림 구성(Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="89ca3-102">Configure Email Notifications (Master Data Services)</span></span>
  <span data-ttu-id="89ca3-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 에서 전자 메일 메시지를 자동으로 보내도록 하려면 알림 전자 메일을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="89ca3-103">Configure notification emails when you want [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] to send email messages automatically.</span></span>  
  
### <a name="to-configure-notifications"></a><span data-ttu-id="89ca3-104">알림을 구성하려면</span><span class="sxs-lookup"><span data-stu-id="89ca3-104">To configure notifications</span></span>  
  
1.  <span data-ttu-id="89ca3-105">[!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)]의 **데이터베이스** 페이지에서 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 데이터베이스를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="89ca3-105">In [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)], on the **Database** page, select your [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] database.</span></span>  
  
2.  <span data-ttu-id="89ca3-106">**시스템 설정** 섹션에서 **프로필 만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="89ca3-106">In the **System Settings** section, click **Create Profile**.</span></span>  
  
3.  <span data-ttu-id="89ca3-107">모든 필수 필드에 내용을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="89ca3-107">Complete all required fields.</span></span> <span data-ttu-id="89ca3-108">자세한 내용은 [데이터베이스 메일 프로필 및 계정 만들기 대화 상자&#40;Master Data Services 구성 관리자&#41;](../../2014/master-data-services/create-database-mail-profile-and-account-dialog-box.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="89ca3-108">For more information, see [Create Database Mail Profile and Account Dialog Box &#40;Master Data Services Configuration Manager&#41;](../../2014/master-data-services/create-database-mail-profile-and-account-dialog-box.md).</span></span>  
  
4.  <span data-ttu-id="89ca3-109">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="89ca3-109">Click **OK**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="89ca3-110">알림을 구성한 후에는 [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] 를 사용하여 변경할 수 없으며</span><span class="sxs-lookup"><span data-stu-id="89ca3-110">After you configure notifications, you cannot use [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] to make changes.</span></span> <span data-ttu-id="89ca3-111">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 데이터베이스를 직접 변경해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="89ca3-111">You must make changes directly in the [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] database.</span></span> <span data-ttu-id="89ca3-112">자세한 내용은 [Database Mail Configuration Objects](../relational-databases/database-mail/database-mail-configuration-objects.md)을(를) 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="89ca3-112">For more information, see [Database Mail Configuration Objects](../relational-databases/database-mail/database-mail-configuration-objects.md).</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="89ca3-113">다음 단계</span><span class="sxs-lookup"><span data-stu-id="89ca3-113">Next Steps</span></span>  
  
-   <span data-ttu-id="89ca3-114">[!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] 에는 알림에 영향을 주는 설정이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="89ca3-114">There are settings in [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] that affect notifications.</span></span> <span data-ttu-id="89ca3-115">이러한 설정은 [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] 에서 조정하거나 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 데이터베이스의 시스템 설정 테이블에서 직접 조정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="89ca3-115">You can adjust these settings in [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] or directly in the System Settings table in the [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] database.</span></span> <span data-ttu-id="89ca3-116">자세한 내용은 [시스템 설정&#40;Master Data Services&#41;](system-settings-master-data-services.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="89ca3-116">For more information, see [System Settings &#40;Master Data Services&#41;](system-settings-master-data-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89ca3-117">참고 항목</span><span class="sxs-lookup"><span data-stu-id="89ca3-117">See Also</span></span>  
 <span data-ttu-id="89ca3-118">[알림 &#40;MDS(Master Data Services)&#41;](../../2014/master-data-services/notifications-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="89ca3-118">[Notifications &#40;Master Data Services&#41;](../../2014/master-data-services/notifications-master-data-services.md) </span></span>  
 <span data-ttu-id="89ca3-119">[전자 메일 알림 문제 해결 (MDS(Master Data Services))](https://social.technet.microsoft.com/wiki/contents/articles/troubleshooting-email-notifications-master-data-services.aspx) </span><span class="sxs-lookup"><span data-stu-id="89ca3-119">[Troubleshooting Email Notifications (Master Data Services)](https://social.technet.microsoft.com/wiki/contents/articles/troubleshooting-email-notifications-master-data-services.aspx) </span></span>  
 [<span data-ttu-id="89ca3-120">알림을 보내도록 비즈니스 규칙 구성&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="89ca3-120">Configure Business Rules to Send Notifications &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/configure-business-rules-to-send-notifications-master-data-services.md)  
  
  
