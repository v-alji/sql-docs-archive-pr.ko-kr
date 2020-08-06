---
title: Broker 이벤트 범주 | Microsoft 문서
ms.custom: ''
ms.date: 07/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- SQL Server event classes, Broker event category
- Broker event category [SQL Server]
- event classes [SQL Server], Broker event category
ms.assetid: 470dc93c-0dda-4d89-829b-937738d59b31
author: stevestein
ms.author: sstein
ms.openlocfilehash: 23f839416e3404bfdf0a7e61d1b1e8dbbb90ec95
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647063"
---
# <a name="broker-event-category"></a><span data-ttu-id="cc058-102">Broker 이벤트 범주</span><span class="sxs-lookup"><span data-stu-id="cc058-102">Broker Event Category</span></span>
  <span data-ttu-id="cc058-103">**Broker** 이벤트 범주에는 일반적인 Service Broker 이벤트가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="cc058-103">The **Broker** event category contains general Service Broker events.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="cc058-104">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="cc058-104">In This Section</span></span>  
  
|<span data-ttu-id="cc058-105">항목</span><span class="sxs-lookup"><span data-stu-id="cc058-105">Topic</span></span>|<span data-ttu-id="cc058-106">Description</span><span class="sxs-lookup"><span data-stu-id="cc058-106">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="cc058-107">Broker:Activation 이벤트 클래스</span><span class="sxs-lookup"><span data-stu-id="cc058-107">Broker:Activation Event Class</span></span>](broker-activation-event-class.md)|<span data-ttu-id="cc058-108">큐 모니터가 활성화 저장 프로시저를 시작하는 경우에 생성되는 이벤트입니다.</span><span class="sxs-lookup"><span data-stu-id="cc058-108">An event generated when a queue monitor starts an activation stored procedure.</span></span>|  
|[<span data-ttu-id="cc058-109">Broker:Connection 이벤트 클래스</span><span class="sxs-lookup"><span data-stu-id="cc058-109">Broker:Connection Event Class</span></span>](broker-connection-event-class.md)|<span data-ttu-id="cc058-110">Service Broker에서 관리하는 전송 연결 상태를 보고하기 위해 생성되는 이벤트입니다.</span><span class="sxs-lookup"><span data-stu-id="cc058-110">An event generated to report the status of a transport connection managed by Service Broker.</span></span>|  
|[<span data-ttu-id="cc058-111">Broker:Conversation 이벤트 클래스</span><span class="sxs-lookup"><span data-stu-id="cc058-111">Broker:Conversation Event Class</span></span>](broker-conversation-event-class.md)|<span data-ttu-id="cc058-112">대화 진행률을 보고하기 위해 생성되는 이벤트입니다.</span><span class="sxs-lookup"><span data-stu-id="cc058-112">An event generated to report the progress of a conversation.</span></span>|  
|[<span data-ttu-id="cc058-113">Broker:Conversation Group 이벤트 클래스</span><span class="sxs-lookup"><span data-stu-id="cc058-113">Broker:Conversation Group Event Class</span></span>](broker-conversation-group-event-class.md)|<span data-ttu-id="cc058-114">데이터베이스에서 대화 그룹을 만들거나 삭제하는 경우에 생성되는 이벤트입니다.</span><span class="sxs-lookup"><span data-stu-id="cc058-114">An event generated when the database creates or drops a conversation group.</span></span>|  
|[<span data-ttu-id="cc058-115">Broker:Corrupted Message 이벤트 클래스</span><span class="sxs-lookup"><span data-stu-id="cc058-115">Broker:Corrupted Message Event Class</span></span>](broker-corrupted-message-event-class.md)|<span data-ttu-id="cc058-116">데이터베이스에서 손상된 메시지를 받았음을 보고하기 위해 생성되는 이벤트입니다.</span><span class="sxs-lookup"><span data-stu-id="cc058-116">An event generated to report that the database has received a corrupt message.</span></span>|  
|[<span data-ttu-id="cc058-117">Broker:Forwarded Message Dropped 이벤트 클래스</span><span class="sxs-lookup"><span data-stu-id="cc058-117">Broker:Forwarded Message Dropped Event Class</span></span>](broker-forwarded-message-dropped-event-class.md)|<span data-ttu-id="cc058-118">전달되어야 하는 Service Broker 메시지가 SQL Server에서 삭제된 경우 생성되는 이벤트입니다.</span><span class="sxs-lookup"><span data-stu-id="cc058-118">An event generated when SQL Server drops a Service Broker message that was to have been forwarded.</span></span>|  
|[<span data-ttu-id="cc058-119">Broker:Forwarded Message Sent 이벤트 클래스</span><span class="sxs-lookup"><span data-stu-id="cc058-119">Broker:Forwarded Message Sent Event Class</span></span>](broker-forwarded-message-sent-event-class.md)|<span data-ttu-id="cc058-120">SQL Server가 Service Broker 메시지를 전달할 때 생성되는 이벤트입니다.</span><span class="sxs-lookup"><span data-stu-id="cc058-120">An event generated when SQL Server forwards a Service Broker message.</span></span>|  
|[<span data-ttu-id="cc058-121">Broker:Message Classify 이벤트 클래스</span><span class="sxs-lookup"><span data-stu-id="cc058-121">Broker:Message Classify Event Class</span></span>](broker-message-classify-event-class.md)|<span data-ttu-id="cc058-122">Service Broker가 메시지 라우팅을 지정하는 경우에 생성되는 이벤트입니다.</span><span class="sxs-lookup"><span data-stu-id="cc058-122">An event generated when Service Broker determines the routing for a message.</span></span>|  
|[<span data-ttu-id="cc058-123">Broker:Message Drop 이벤트 클래스</span><span class="sxs-lookup"><span data-stu-id="cc058-123">Broker:Message Drop Event Class</span></span>](broker-message-drop-event-class.md)|<span data-ttu-id="cc058-124">Service Broker가 받은 메시지를 유지할 수 없는 경우에 생성되는 이벤트입니다. 이 메시지는 이 인스턴스의 서비스로 배달되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cc058-124">An event generated when Service Broker is unable to retain a received message that should have been delivered to a service in this instance</span></span>|  
|[<span data-ttu-id="cc058-125">Broker:Remote Message Ack 이벤트 클래스</span><span class="sxs-lookup"><span data-stu-id="cc058-125">Broker:Remote Message Ack Event Class</span></span>](broker-remote-message-ack-event-class.md)|<span data-ttu-id="cc058-126">Service Broker가 메시지 승인을 보내거나 받는 경우에 생성되는 이벤트입니다.</span><span class="sxs-lookup"><span data-stu-id="cc058-126">An event generated when Service Broker sends or receives a message acknowledgement.</span></span>|  
  
 <span data-ttu-id="cc058-127">두 개의 보안 감사 이벤트도 Service Broker에 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="cc058-127">Two security audit events are also provided for Service Broker.</span></span> <span data-ttu-id="cc058-128">이러한 이벤트에 대한 자세한 내용은 [Audit Broker Login 이벤트 클래스](audit-broker-login-event-class.md) 및 [Audit Broker Conversation 이벤트 클래스](audit-broker-conversation-event-class.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="cc058-128">For more information on those events, see [Audit Broker Login Event Class](audit-broker-login-event-class.md) and [Audit Broker Conversation Event Class](audit-broker-conversation-event-class.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc058-129">참고 항목</span><span class="sxs-lookup"><span data-stu-id="cc058-129">See Also</span></span>  
 [<span data-ttu-id="cc058-130">Security Audit 이벤트 범주</span><span class="sxs-lookup"><span data-stu-id="cc058-130">Security Audit Event Category</span></span>](https://docs.microsoft.com/bi-reference/trace-events/security-audit-event-category)  
  
  
