---
title: blocked process threshold 서버 구성 옵션 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- thresholds [SQL Server]
- blocked process threshold option
ms.assetid: 3d46d143-bc6a-4220-8b55-6baa37547c25
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 9d5b61aaf23a8e74cb11afbf4e8bdb958fde6abe
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736783"
---
# <a name="blocked-process-threshold-server-configuration-option"></a><span data-ttu-id="a0025-102">blocked process threshold 서버 구성 옵션</span><span class="sxs-lookup"><span data-stu-id="a0025-102">blocked process threshold Server Configuration Option</span></span>
  <span data-ttu-id="a0025-103">**blocked process threshold** 옵션을 사용하여 차단된 프로세스 보고서가 생성되는 임계값을 초 단위로 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a0025-103">Use the **blocked process threshold** option to specify the threshold, in seconds, at which blocked process reports are generated.</span></span> <span data-ttu-id="a0025-104">0에서 86,400 사이의 임계값을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a0025-104">The threshold can be set from 0 to 86,400.</span></span> <span data-ttu-id="a0025-105">기본적으로 차단된 프로세스 보고서는 생성되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a0025-105">By default, no blocked process reports are produced.</span></span> <span data-ttu-id="a0025-106">시스템 태스크 또는 검색할 수 있는 교착 상태를 생성하지 않는 리소스를 기다리는 태스크의 경우 이 이벤트가 생성되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a0025-106">This event is not generated for system tasks or for tasks that are waiting on resources that do not generate detectable deadlocks.</span></span>  
  
 <span data-ttu-id="a0025-107">이 이벤트가 생성되면 실행할 [경고](../../ssms/agent/alerts.md) 를 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a0025-107">You can define an [alert](../../ssms/agent/alerts.md) to be executed when this event is generated.</span></span> <span data-ttu-id="a0025-108">예를 들어 적절한 동작을 수행하여 차단 상황을 처리하도록 관리자를 페이징할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a0025-108">So for example, you can choose to page the administrator to take appropriate action to handle the blocking situation.</span></span>  
  
 <span data-ttu-id="a0025-109">차단된 프로세스 임계값은 교착 상태 모니터 백그라운드 스레드를 사용하여 구성된 임계값보다 길거나 이 임계값의 배수인 시간 동안 대기하는 태스크 목록을 검토합니다.</span><span class="sxs-lookup"><span data-stu-id="a0025-109">Blocked process threshold uses the deadlock monitor background thread to walk through the list of tasks waiting for a time greater than or multiples of the configured threshold.</span></span> <span data-ttu-id="a0025-110">차단된 각 태스크의 보고 간격마다 한 번씩 이벤트가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="a0025-110">The event is generated once per reporting interval for each of the blocked tasks.</span></span>  
  
 <span data-ttu-id="a0025-111">차단된 프로세스 보고서는 최상의 노력을 기반으로 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="a0025-111">The blocked process report is done on a best effort basis.</span></span> <span data-ttu-id="a0025-112">반드시 실시간으로 보고하거나 거의 실시간으로 보고하는 것은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="a0025-112">There is no guarantee of any real-time or even close to real-time reporting.</span></span>  
  
 <span data-ttu-id="a0025-113">이 설정은 서버를 중지했다가 다시 시작하지 않아도 즉시 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="a0025-113">The setting takes effect immediately without a server stop and restart.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="a0025-114">예제</span><span class="sxs-lookup"><span data-stu-id="a0025-114">Examples</span></span>  
 <span data-ttu-id="a0025-115">다음 예에서는 `blocked process threshold` 를 `20` 초로 설정하여 차단된 태스크마다 차단된 프로세스 보고서가 생성되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="a0025-115">The following example sets the `blocked process threshold` to `20` seconds, generating a blocked process report for each task that is blocked.</span></span>  
  
```  
sp_configure 'show advanced options', 1 ;  
GO  
RECONFIGURE ;  
GO  
sp_configure 'blocked process threshold', 20 ;  
GO  
RECONFIGURE ;  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="a0025-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a0025-116">See Also</span></span>  
 <span data-ttu-id="a0025-117">[sp_trace_setevent&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="a0025-117">[sp_trace_setevent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql) </span></span>  
 [<span data-ttu-id="a0025-118">Blocked Process Report 이벤트 클래스</span><span class="sxs-lookup"><span data-stu-id="a0025-118">Blocked Process Report Event Class</span></span>](../../relational-databases/event-classes/blocked-process-report-event-class.md)  
  
  
