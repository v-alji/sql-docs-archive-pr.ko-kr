---
title: 업그레이드 하면 메시지 큐를 사용 하는 지연 업데이트 구독이 수정 됩니다. | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- subscriptions [SQL Server replication]
- MSMQ [SQL Server replication]
- queues [SQL Server replication]
- queued updating subscriptions [SQL Server replication]
ms.assetid: 97944de3-fbad-4db1-939a-dcd550bf5893
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: d44cbad43d75634cbf8660110cc879522265c54d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742768"
---
# <a name="upgrading-will-modify-queued-updating-subscriptions-that-use-message-queuing"></a><span data-ttu-id="08803-102">업그레이드하면 메시지 큐를 사용하는 지연 업데이트 구독이 수정됩니다.</span><span class="sxs-lookup"><span data-stu-id="08803-102">Upgrading will modify queued updating subscriptions that use Message Queuing</span></span>
  <span data-ttu-id="08803-103">업그레이드 관리자가 MSMQ( [!INCLUDE[msCoName](../../includes/msconame-md.md)] Message Queuing)를 사용하는 지연 업데이트 구독이 하나 이상 있을 수 있음을 감지했습니다.</span><span class="sxs-lookup"><span data-stu-id="08803-103">Upgrade Advisor detected that you might have one or more queued updating subscriptions that use [!INCLUDE[msCoName](../../includes/msconame-md.md)] Message Queuing (also known as MSMQ).</span></span> <span data-ttu-id="08803-104">복제는 메시지 큐를 더 이상 지원하지 않습니다. 따라서 구독은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 큐를 사용하도록 수정됩니다.</span><span class="sxs-lookup"><span data-stu-id="08803-104">Replication no longer supports Message Queuing; therefore, the subscriptions will be modified to use a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] queue.</span></span>  
  
 <span data-ttu-id="08803-105">**sql** 의 값만 허용됩니다.</span><span class="sxs-lookup"><span data-stu-id="08803-105">Only a value of **sql** is allowed.</span></span> <span data-ttu-id="08803-106">메시지 큐를 사용하는 기존 게시는 업그레이드 중에 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 큐를 사용하도록 수정됩니다.</span><span class="sxs-lookup"><span data-stu-id="08803-106">Existing publications that use Message Queuing are modified during upgrade to use a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] queue.</span></span> <span data-ttu-id="08803-107">메시지 큐를 사용하는 지연 업데이트에 종속된 애플리케이션의 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 큐를 허용하도록 다시 작성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="08803-107">If you have applications that depend on queued updating using Message Queuing, these applications will have to be rewritten to accommodate a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] queue.</span></span> <span data-ttu-id="08803-108">지연 업데이트 구독에 대한 자세한 내용은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 온라인 설명서에서 "트랜잭션 복제를 위한 업데이트 가능 구독"을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="08803-108">For more information about queued updating subscriptions, see "Updatable Subscriptions for Transactional Replication" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
 <span data-ttu-id="08803-109">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 가 업그레이드되는 동안 메시지 큐 서비스가 실행 중이면 업그레이드 후에 기존 메시지 큐 구독 큐가 제거됩니다.</span><span class="sxs-lookup"><span data-stu-id="08803-109">Upgrade will remove the existing Message Queuing subscription queues if the Message Queuing service is running while [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is being upgraded.</span></span>  
  
 <span data-ttu-id="08803-110">메시지 큐 서비스가 실행되고 있지 않은 경우에는 업그레이드가 완료된 후에 큐를 수동으로 제거하십시오.</span><span class="sxs-lookup"><span data-stu-id="08803-110">If the Message Queuing service is not running, remove the queues manually after upgrade is complete.</span></span> <span data-ttu-id="08803-111">큐를 제거하는 방법은 Windows 설명서를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="08803-111">For more information about how to remove queues, see the Windows documentation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08803-112">참고 항목</span><span class="sxs-lookup"><span data-stu-id="08803-112">See Also</span></span>  
 [<span data-ttu-id="08803-113">복제 업그레이드 문제</span><span class="sxs-lookup"><span data-stu-id="08803-113">Replication Upgrade Issues</span></span>](../../../2014/sql-server/install/replication-upgrade-issues.md)  
  
  
