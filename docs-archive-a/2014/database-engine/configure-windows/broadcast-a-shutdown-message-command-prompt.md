---
title: 종료 메시지 브로드캐스트(명령 프롬프트) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- SQL Server, stopping
- named instances [SQL Server], broadcasting shutdown messages
- shutdown message broadcast
- broadcasting shutdown message
- command prompt [SQL Server], broadcasting shutdown messages
- default instances [SQL Server], broadcasting shutdown messages
- stopping SQL Server
ms.assetid: 9f20ccd5-d952-431d-ba12-339911af9430
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 540baada4a78d7b5caf54cbabb9196ce5a79780e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87733128"
---
# <a name="broadcast-a-shutdown-message-command-prompt"></a><span data-ttu-id="3ef4c-102">종료 메시지 브로드캐스트(명령 프롬프트)</span><span class="sxs-lookup"><span data-stu-id="3ef4c-102">Broadcast a Shutdown Message (Command Prompt)</span></span>
  <span data-ttu-id="3ef4c-103">이 항목에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 에서 **net send** 명령을 사용하여 종료 메시지를 브로드캐스팅하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="3ef4c-103">This topic describes how to broadcast a shutdown message in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using the **net send** command.</span></span> <span data-ttu-id="3ef4c-104">사용자가 제시간에 태스크를 완료할 수 있도록 메시지에 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스 중지 시간을 포함시키세요.</span><span class="sxs-lookup"><span data-stu-id="3ef4c-104">In the message, include the time the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] will be stopped so that users can finish their tasks.</span></span>  
  
##  <a name="SSMSProcedure"></a>  
  
#### <a name="to-broadcast-a-shutdown-message"></a><span data-ttu-id="3ef4c-105">종료 메시지를 브로드캐스팅하려면</span><span class="sxs-lookup"><span data-stu-id="3ef4c-105">To broadcast a shutdown message</span></span>  
  
1.  <span data-ttu-id="3ef4c-106">명령 프롬프트에서 다음을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="3ef4c-106">From a command prompt, enter:</span></span>  
  
     <span data-ttu-id="3ef4c-107">**net send /users "message"**</span><span class="sxs-lookup"><span data-stu-id="3ef4c-107">**net send /users "message"**</span></span>  
  
     <span data-ttu-id="3ef4c-108">**/users** 옵션은 서버에 연결된 모든 사용자에게 메시지를 보내도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3ef4c-108">The **/users** option specifies that the message be sent to all users connected to the server</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3ef4c-109">**net send** 명령을 사용하려면 보내는 컴퓨터와 받는 컴퓨터 모두에서 메신저 서비스가 실행되고 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3ef4c-109">The **net send** command requires the messenger service to be running on both the sending and the receiving computers.</span></span> <span data-ttu-id="3ef4c-110">메신저 서비스는 Windows Server 2003에서 기본적으로 해제되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3ef4c-110">The messenger service is disabled by default on Windows Server 2003.</span></span> <span data-ttu-id="3ef4c-111">**net send**에 대한 자세한 내용은 Windows 설명서를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3ef4c-111">For information about **net send**, see the Windows documentation.</span></span>  
  
 <span data-ttu-id="3ef4c-112">네트워크에서는 전자 메일이나 전화로 사용자에게 연락하는 것이 더 적절합니다.</span><span class="sxs-lookup"><span data-stu-id="3ef4c-112">On your network, it may be more appropriate to contact users by e-mail or the telephone.</span></span> <span data-ttu-id="3ef4c-113">현재 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에 연결된 사용자를 확인하려면 작업 모니터를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="3ef4c-113">To determine which users are currently connected to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], use the Activity Monitor.</span></span> <span data-ttu-id="3ef4c-114">작업 모니터에 대한 자세한 내용은 [작업 모니터](../../relational-databases/performance-monitor/activity-monitor.md) 및 [작업 모니터 열기&#40;SQL Server Management Studio&#41;](../../relational-databases/performance-monitor/open-activity-monitor-sql-server-management-studio.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3ef4c-114">For information on the Activity Monitor, see [Activity Monitor](../../relational-databases/performance-monitor/activity-monitor.md) and [Open Activity Monitor &#40;SQL Server Management Studio&#41;](../../relational-databases/performance-monitor/open-activity-monitor-sql-server-management-studio.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ef4c-115">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3ef4c-115">See Also</span></span>  
 [<span data-ttu-id="3ef4c-116">데이터베이스 엔진, SQL Server 에이전트 또는 SQL Server Browser 서비스 시작, 중지, 일시 중지, 재개 및 다시 시작</span><span class="sxs-lookup"><span data-stu-id="3ef4c-116">Start, Stop, Pause, Resume, Restart the Database Engine, SQL Server Agent, or SQL Server Browser Service</span></span>](start-stop-pause-resume-restart-sql-server-services.md)  
  
  
