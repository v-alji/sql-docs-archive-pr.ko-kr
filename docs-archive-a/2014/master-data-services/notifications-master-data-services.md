---
title: 알림(Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- notifications [Master Data Services]
- notifications [Master Data Services], about notifications
- e-mail [Master Data Services]
- e-mail [Master Data Services], about e-mail notifications
ms.assetid: d7ad32d5-9fe5-48fd-8c61-0b00c0aff082
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: a61825f9450dd5b708aff8c3fc72f0f12732337b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660638"
---
# <a name="notifications-master-data-services"></a><span data-ttu-id="d479c-102">알림(Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="d479c-102">Notifications (Master Data Services)</span></span>
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]<span data-ttu-id="d479c-103">비즈니스 규칙 유효성 검사에 실패 하거나 모델 버전의 상태가 변경 될 때 전자 메일 알림을 보내도록 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d479c-103">can be configured to send an email notification when business rule validation fails or the status of a model version changes.</span></span>  
  
## <a name="how-notifications-are-sent"></a><span data-ttu-id="d479c-104">알림 전송 방법</span><span class="sxs-lookup"><span data-stu-id="d479c-104">How Notifications Are Sent</span></span>  
 <span data-ttu-id="d479c-105">[!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)]에서 알림을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="d479c-105">You configure notifications in [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)].</span></span> <span data-ttu-id="d479c-106">알림은 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../includes/ssde-md.md)] 데이터베이스를 호스팅하는 인스턴스에서 데이터베이스 메일를 사용 하 여 전자 메일 메시지를 보냅니다 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="d479c-106">Notifications send email messages by using Database Mail on the instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../includes/ssde-md.md)] that hosts the [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] database.</span></span> <span data-ttu-id="d479c-107">데이터베이스 메일에 대한 자세한 내용은 [온라인 설명서에서](../relational-databases/database-mail/database-mail-configuration-objects.md) 데이터베이스 메일 구성 개체 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d479c-107">For more information about Database Mail, see [Database Mail Configuration Objects](../relational-databases/database-mail/database-mail-configuration-objects.md) in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="when-notifications-are-sent"></a><span data-ttu-id="d479c-108">알림을 보내는 경우</span><span class="sxs-lookup"><span data-stu-id="d479c-108">When Notifications Are Sent</span></span>  
 <span data-ttu-id="d479c-109">알림이 구성된 후 다음 인스턴스에 자동화된 전자 메일 알림을 보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d479c-109">After notifications are configured, automated email notifications can be sent in the following instances.</span></span>  
  
|<span data-ttu-id="d479c-110">인스턴스</span><span class="sxs-lookup"><span data-stu-id="d479c-110">Instance</span></span>|<span data-ttu-id="d479c-111">Description</span><span class="sxs-lookup"><span data-stu-id="d479c-111">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="d479c-112">데이터가 비즈니스 규칙 유효성 검사를 통과하지 못할 경우</span><span class="sxs-lookup"><span data-stu-id="d479c-112">Data fails business rule validation</span></span>|<span data-ttu-id="d479c-113">특성 값이 비즈니스 규칙 유효성 검사를 통과하지 못하는 경우 전자 메일을 보내도록 개별 비즈니스 규칙을 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d479c-113">Individual business rules must be configured to send email when an attribute value fails business rule validation.</span></span> <span data-ttu-id="d479c-114">자세한 내용은 [알림을 보내도록 비즈니스 규칙 구성&#40;Master Data Services&#41;](configure-business-rules-to-send-notifications-master-data-services.md)에서 알림을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="d479c-114">For more information, see [Configure Business Rules to Send Notifications &#40;Master Data Services&#41;](configure-business-rules-to-send-notifications-master-data-services.md).</span></span>|  
|<span data-ttu-id="d479c-115">모델 버전 상태가 변경될 경우</span><span class="sxs-lookup"><span data-stu-id="d479c-115">Model version status changes</span></span>|<span data-ttu-id="d479c-116">모델 버전의 상태가 변경될 때마다 모델 관리자인 사용자가 알림을 자동으로 받습니다.</span><span class="sxs-lookup"><span data-stu-id="d479c-116">Each time a model version's status changes, users that are model administrators receive notifications automatically.</span></span> <span data-ttu-id="d479c-117">자세한 내용은 [관리자 &#40;MDS(Master Data Services)&#41;](../../2014/master-data-services/administrators-master-data-services.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="d479c-117">For more information, see [Administrators &#40;Master Data Services&#41;](../../2014/master-data-services/administrators-master-data-services.md).</span></span>|  
  
## <a name="system-settings"></a><span data-ttu-id="d479c-118">시스템 설정</span><span class="sxs-lookup"><span data-stu-id="d479c-118">System Settings</span></span>  
 <span data-ttu-id="d479c-119">[!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] 에는 알림에 영향을 주는 설정이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d479c-119">There are settings in [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] that affect notifications.</span></span> <span data-ttu-id="d479c-120">이러한 설정은 [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] 에서 조정하거나 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 데이터베이스의 시스템 설정 테이블에서 직접 조정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d479c-120">You can adjust these settings in [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] or directly in the System Settings table in the [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] database.</span></span> <span data-ttu-id="d479c-121">자세한 내용은 [시스템 설정&#40;Master Data Services&#41;](../../2014/master-data-services/system-settings-master-data-services.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d479c-121">For more information, see [System Settings &#40;Master Data Services&#41;](../../2014/master-data-services/system-settings-master-data-services.md).</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="d479c-122">관련 작업</span><span class="sxs-lookup"><span data-stu-id="d479c-122">Related Tasks</span></span>  
  
|<span data-ttu-id="d479c-123">태스크 설명</span><span class="sxs-lookup"><span data-stu-id="d479c-123">Task Description</span></span>|<span data-ttu-id="d479c-124">항목</span><span class="sxs-lookup"><span data-stu-id="d479c-124">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="d479c-125">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 에서 전자 메일을 알림을 보내도록 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="d479c-125">Configure [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] to send email notifications.</span></span>|[<span data-ttu-id="d479c-126">메일 알림 구성&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="d479c-126">Configure Email Notifications &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/configure-email-notifications-master-data-services.md)|  
|<span data-ttu-id="d479c-127">특성 값 변경 시 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 에서 알림을 보내도록 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="d479c-127">Configure [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] to send notifications when attribute values change.</span></span>|[<span data-ttu-id="d479c-128">알림을 보내도록 비즈니스 규칙 구성&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="d479c-128">Configure Business Rules to Send Notifications &#40;Master Data Services&#41;</span></span>](configure-business-rules-to-send-notifications-master-data-services.md)|  
  
## <a name="related-content"></a><span data-ttu-id="d479c-129">관련 내용</span><span class="sxs-lookup"><span data-stu-id="d479c-129">Related Content</span></span>  
  
-   [<span data-ttu-id="d479c-130">비즈니스 규칙&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="d479c-130">Business Rules &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/business-rules-master-data-services.md)  
  
-   [<span data-ttu-id="d479c-131">버전&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="d479c-131">Versions &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/versions-master-data-services.md)  
  
-   [<span data-ttu-id="d479c-132">전자 메일 알림 문제 해결(Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="d479c-132">Troubleshooting Email Notifications (Master Data Services)</span></span>](https://social.technet.microsoft.com/wiki/contents/articles/troubleshooting-email-notifications-master-data-services.aspx)  
  
  
