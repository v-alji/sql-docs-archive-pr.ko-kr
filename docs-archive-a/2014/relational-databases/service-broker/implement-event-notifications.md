---
title: 이벤트 알림 구현 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- event notifications [SQL Server], target service
- target service [SQL Server]
- event notifications [SQL Server], creating
ms.assetid: 29ac8f68-a28a-4a77-b67b-a8663001308c
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 6a89c66ca5c3b420fff14c087bd604b16c641369
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651603"
---
# <a name="implement-event-notifications"></a><span data-ttu-id="b8a10-102">이벤트 알림 구현</span><span class="sxs-lookup"><span data-stu-id="b8a10-102">Implement Event Notifications</span></span>
  <span data-ttu-id="b8a10-103">이벤트 알림을 구현하려면 먼저 이벤트 알림을 받을 대상 서비스를 만든 다음 이벤트 알림을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8a10-103">To implement an event notification, you must first create a target service to receive event notifications, and then create the event notification.</span></span>  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssSB](../../includes/sssb-md.md)] <span data-ttu-id="b8a10-104">대화 보안을 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8a10-104">dialog security should be configured for event notifications that send messages to a service broker on a remote server.</span></span> <span data-ttu-id="b8a10-105">대화 보안은 전체 보안 모델에 따라 수동으로 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8a10-105">Dialog security must be configured manually according to the full security model.</span></span>  
  
## <a name="creating-the-target-service"></a><span data-ttu-id="b8a10-106">대상 서비스 만들기</span><span class="sxs-lookup"><span data-stu-id="b8a10-106">Creating the Target Service</span></span>  
 <span data-ttu-id="b8a10-107">[!INCLUDE[ssSB](../../includes/sssb-md.md)]에는 다음 특정 메시지 유형과 이벤트 알림에 대한 계약이 포함되어 있으므로 [!INCLUDE[ssSB](../../includes/sssb-md.md)] 를 시작하는 서비스를 만들지 않아도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b8a10-107">You do not have to create a [!INCLUDE[ssSB](../../includes/sssb-md.md)]-initiating service because [!INCLUDE[ssSB](../../includes/sssb-md.md)] includes the following specific message type and contract for event notifications:</span></span>  
  
```  
https://schemas.microsoft.com/SQL/Notifications/PostEventNotification  
```  
  
 <span data-ttu-id="b8a10-108">이벤트 알림을 받는 대상 서비스는 이러한 기존 계약을 인식해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8a10-108">The target service that receives event notifications must honor this preexisting contract.</span></span>  
  
 <span data-ttu-id="b8a10-109">**대상 서비스를 만들려면**</span><span class="sxs-lookup"><span data-stu-id="b8a10-109">**To create a target service**:</span></span>  
  
1.  <span data-ttu-id="b8a10-110">메시지를 받을 큐를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b8a10-110">Create a queue to receive messages.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="b8a10-111">큐에서 `https://schemas.microsoft.com/SQL/Notifications/QueryNotification`의 메시지 유형을 받습니다.</span><span class="sxs-lookup"><span data-stu-id="b8a10-111">The queue receives the following message type: `https://schemas.microsoft.com/SQL/Notifications/QueryNotification`.</span></span>  
  
2.  <span data-ttu-id="b8a10-112">이벤트 알림 계약을 참조하는 큐에 서비스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b8a10-112">Create a service on the queue that references the event notifications contract.</span></span>  
  
3.  <span data-ttu-id="b8a10-113">서비스에 경로를 만들어 [!INCLUDE[ssSB](../../includes/sssb-md.md)] 에서 서비스에 대한 메시지를 보낼 주소를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="b8a10-113">Create a route on the service to define the address to which [!INCLUDE[ssSB](../../includes/sssb-md.md)] sends messages for the service.</span></span> <span data-ttu-id="b8a10-114">같은 데이터베이스의 서비스를 대상으로 하는 이벤트 알림의 경우 `ADDRESS = 'LOCAL'`을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b8a10-114">For event notifications that target a service in the same database, specify `ADDRESS = 'LOCAL'`.</span></span>  
  
    > [!NOTE]  
    >  [!INCLUDE[ssSB](../../includes/sssb-md.md)] <span data-ttu-id="b8a10-115">라우팅에 의해 알림 메시지를 받는 서비스가 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="b8a10-115">routing determines the service that receives the notification messages.</span></span> <span data-ttu-id="b8a10-116">이벤트 알림 대상이 원격 서버의 서비스일 경우 양방향 통신을 위해 원본 서버와 대상 서버에 모두 경로가 정의되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8a10-116">If the event notification targets a service on a remote server, both the source server and the target server must have routes defined on them to make sure that two-way communication occurs.</span></span>  
  
 <span data-ttu-id="b8a10-117">다음 예에서는 이벤트 알림 계약의 메시지를 처리하기 위해 큐, 큐의 서비스 및 서비스의 경로를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b8a10-117">The following example creates a queue, a service on the queue, and a route on the service to handle messages from the event notification contract.</span></span>  
  
```  
CREATE QUEUE NotifyQueue ;  
GO  
CREATE SERVICE NotifyService  
ON QUEUE NotifyQueue  
(  
[https://schemas.microsoft.com/SQL/Notifications/PostEventNotification]  
);  
GO  
CREATE ROUTE NotifyRoute  
WITH SERVICE_NAME = 'NotifyService',  
ADDRESS = 'LOCAL';  
GO  
```  
  
## <a name="creating-the-event-notification"></a><span data-ttu-id="b8a10-118">이벤트 알림 만들기</span><span class="sxs-lookup"><span data-stu-id="b8a10-118">Creating the Event Notification</span></span>  
 <span data-ttu-id="b8a10-119">이벤트 알림은 [!INCLUDE[tsql](../../includes/tsql-md.md)] CREATE EVENT NOTIFICATION 문으로 만들고 DROP EVENT NOTIFICATION 문으로 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="b8a10-119">Event notifications are created by using the [!INCLUDE[tsql](../../includes/tsql-md.md)] CREATE EVENT NOTIFICATION statement, and are dropped by using the DROP EVENT NOTIFICATION STATEMENT.</span></span> <span data-ttu-id="b8a10-120">이벤트 알림을 수정하려면 해당 이벤트 알림을 삭제하고 다시 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8a10-120">To modify an event notification, you must drop and re-create the event notification.</span></span>  
  
 <span data-ttu-id="b8a10-121">다음 예에서는 `CreateDatabaseNotification`이벤트 알림을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b8a10-121">The following example creates the event notification `CreateDatabaseNotification`.</span></span> <span data-ttu-id="b8a10-122">이 알림은 서버에서 발생하는 `CREATE_DATABASE` 이벤트에 대한 메시지를 이전에 만든 `NotifyService` 서비스로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="b8a10-122">This notification sends a message about any `CREATE_DATABASE` event that occurs on the server to the `NotifyService` service that was previously created.</span></span>  
  
```  
CREATE EVENT NOTIFICATION CreateDatabaseNotification  
ON SERVER  
FOR CREATE_DATABASE  
TO SERVICE 'NotifyService', '8140a771-3c4b-4479-8ac0-81008ab17984' ;  
```  
  
> [!CAUTION]  
>  <span data-ttu-id="b8a10-123">이벤트 알림은 CREATE_SCHEMA 이벤트와 CREATE SCHEMA 문의 <schema_element> 정의를 별도의 이벤트로 인식합니다.</span><span class="sxs-lookup"><span data-stu-id="b8a10-123">Event notifications recognize CREATE_SCHEMA events and the <schema_element> definitions of CREATE SCHEMA statements as separate events.</span></span> <span data-ttu-id="b8a10-124">예를 들어 CREATE_SCHEMA 및 CREATE_TABLE 이벤트에서 모두 이벤트 알림이 생성되며 다음 일괄 작업을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="b8a10-124">For example, an event notification is created on both the CREATE_SCHEMA and CREATE_TABLE events, and you run the following batch.</span></span>  
>   
>  `CREATE SCHEMA s`  
>   
>  `CREATE TABLE t1 (col1 int)`  
>   
>  <span data-ttu-id="b8a10-125">이 경우 이벤트 알림은 CREATE_SCHEMA 이벤트가 발생할 때와 CREATE_TABLE 이벤트가 발생할 때 각각 한 번씩, 두 번 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="b8a10-125">In this case, the event notification is raised two times: Onne time when the CREATE_SCHEMA event occurs, and again when the CREATE_TABLE event occurs.</span></span> <span data-ttu-id="b8a10-126">CREATE_SCHEMA 이벤트 및 해당하는 CREATE SCHEMA 정의의 &lt;schema_element&gt; 텍스트 둘 다에 대해 이벤트 알림이 생성되는 것을 방지하거나 필요 없는 이벤트 데이터의 캡처를 방지하는 논리를 애플리케이션에 구축하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="b8a10-126">We recommend that you either avoid creating event notifications on both the CREATE_SCHEMA events and the <schema_element> texts of any corresponding CREATE SCHEMA definitions, or build logic into your application to avoid capturing unwanted event data.</span></span>  
  
 <span data-ttu-id="b8a10-127">**이벤트 알림을 만들려면**</span><span class="sxs-lookup"><span data-stu-id="b8a10-127">**To create an event notification**</span></span>  
  
-   [<span data-ttu-id="b8a10-128">CREATE EVENT NOTIFICATION&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="b8a10-128">CREATE EVENT NOTIFICATION &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-event-notification-transact-sql)  
  
 <span data-ttu-id="b8a10-129">**이벤트 알림을 삭제하려면**</span><span class="sxs-lookup"><span data-stu-id="b8a10-129">**To drop an event notification**</span></span>  
  
-   [<span data-ttu-id="b8a10-130">DROP EVENT NOTIFICATION&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="b8a10-130">DROP EVENT NOTIFICATION &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/drop-event-notification-transact-sql)  
  
## <a name="see-also"></a><span data-ttu-id="b8a10-131">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b8a10-131">See Also</span></span>  
 <span data-ttu-id="b8a10-132">[이벤트 알림에 대한 정보 가져오기](event-notifications.md) </span><span class="sxs-lookup"><span data-stu-id="b8a10-132">[Get Information About Event Notifications](event-notifications.md) </span></span>  
 [<span data-ttu-id="b8a10-133">EVENTDATA&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="b8a10-133">EVENTDATA &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/eventdata-transact-sql)  
  
  
