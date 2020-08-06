---
title: SQL Server 에이전트 오류 로그 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- logs [SQL Server], SQL Server Agent
- messages [SQL Server], SQL Server Agent
- errors [SQL Server], logs
- SQL Server Agent, errors
ms.assetid: 0b2d6e6e-cd2d-4b8b-9fa2-2bbd2fc0da41
author: stevestein
ms.author: sstein
ms.openlocfilehash: ea9a723695c6993f4f07897f49d8014a86ce78b5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731319"
---
# <a name="sql-server-agent-error-log"></a><span data-ttu-id="c6277-102">SQL Server 에이전트 오류 로그</span><span class="sxs-lookup"><span data-stu-id="c6277-102">SQL Server Agent Error Log</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="c6277-103">에이전트는 기본적으로 경고 및 오류를 기록하는 오류 로그를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c6277-103">Agent creates an error log that records warnings and errors by default.</span></span> <span data-ttu-id="c6277-104">이 로그에는 다음 경고 및 오류가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c6277-104">The following warnings and errors are displayed in the log:</span></span>  
  
-   <span data-ttu-id="c6277-105">"작업을 \<*job_name*> 실행 하는 동안 작업이 삭제 되었습니다."와 같은 잠재적 문제에 대 한 정보를 제공 하는 경고 메시지입니다.</span><span class="sxs-lookup"><span data-stu-id="c6277-105">Warning messages that provide information about potential problems, such as "Job \<*job_name*> was deleted while it was running."</span></span>  
  
-   <span data-ttu-id="c6277-106">"메일 세션을 시작할 수 없습니다"와 같이 대개 시스템 관리자의 조정이 필요한 오류 메시지.</span><span class="sxs-lookup"><span data-stu-id="c6277-106">Error messages that usually require intervention by a system administrator, such as "Unable to start mail session."</span></span> <span data-ttu-id="c6277-107">오류 메시지는 **net send**로 특정 사용자나 컴퓨터에 전달될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c6277-107">Error messages can be sent to a specific user or computer by **net send**.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="c6277-108">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 오류 로그를 최대 9개까지 유지 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="c6277-108">maintains up to nine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent error logs.</span></span> <span data-ttu-id="c6277-109">보관된 오류 로그에는 각각 오류 로그의 상대적 기간을 표시하는 확장명이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c6277-109">Each archived log has an extension that indicates the relative age of the log.</span></span> <span data-ttu-id="c6277-110">예를 들어 .1의 확장명은 최근에 보관된 오류 로그를 표시하고 .9의 확장명은 가장 오래된 오류 로그를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="c6277-110">For example, an extension of .1 indicates the newest archived error log and an extension of .9 indicates the oldest archived error log.</span></span>  
  
 <span data-ttu-id="c6277-111">기본적으로 실행 추적 메시지는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 오류 로그를 가득 채울 수 있으므로 이 로그에 기록되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c6277-111">By default, execution trace messages are not written to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent error log, because they can fill it.</span></span> <span data-ttu-id="c6277-112">오류 로그가 가득 차게 되면 좀 더 중요한 오류를 놓칠 수 있는 가능성이 높아집니다.</span><span class="sxs-lookup"><span data-stu-id="c6277-112">When the error log is full, your ability to select and analyze more difficult errors is reduced.</span></span> <span data-ttu-id="c6277-113">오류 로그는 서버의 처리 부하에도 영향을 주기 때문에 실행 추적 메시지를 오류 로그로 캡처할 경우 얻을 수 있는 가치에 대해 신중하게 고려해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6277-113">Because the log adds to the server's processing load, it is important to consider carefully what value you obtain by capturing execution trace messages to the error log.</span></span> <span data-ttu-id="c6277-114">일반적으로 특정 문제를 디버깅할 때만 모든 메시지를 캡처하는 것이 가장 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="c6277-114">Generally, it is best to capture all messages only when you are debugging a specific problem.</span></span>  
  
 <span data-ttu-id="c6277-115">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트가 중지되었을 때 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 오류 로그의 위치를 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c6277-115">When [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent is stopped, you can modify the location of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent error log.</span></span> <span data-ttu-id="c6277-116">오류 로그가 비어 있으면 로그를 열 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c6277-116">When the error log is empty, the log cannot be opened.</span></span> <span data-ttu-id="c6277-117">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트를 중단하지 않고 언제든지 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 로그를 반복할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c6277-117">You can cycle the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent log at any time without stopping [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.</span></span>  
  
 <span data-ttu-id="c6277-118">**SQL Server 에이전트 오류 로그를 보려면**</span><span class="sxs-lookup"><span data-stu-id="c6277-118">**To view the SQL Server Agent error log**</span></span>  
  
-   [<span data-ttu-id="c6277-119">SQL Server 에이전트 오류 로그 보기&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="c6277-119">View SQL Server Agent Error Log &#40;SQL Server Management Studio&#41;</span></span>](view-sql-server-agent-error-log-sql-server-management-studio.md) 
  
 <span data-ttu-id="c6277-120">**SQL Server 에이전트 오류 로그 이름을 바꾸려면**</span><span class="sxs-lookup"><span data-stu-id="c6277-120">**To rename a SQL Server Agent error log**</span></span>  
  
-   [<span data-ttu-id="c6277-121">SQL Server 에이전트 오류 로그 이름 바꾸기&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="c6277-121">Rename a SQL Server Agent Error Log &#40;SQL Server Management Studio&#41;</span></span>](rename-a-sql-server-agent-error-log-sql-server-management-studio.md)  
  
 <span data-ttu-id="c6277-122">**SQL Server 에이전트 오류 메시지를 보내려면**</span><span class="sxs-lookup"><span data-stu-id="c6277-122">**To send SQL Server Agent error messages**</span></span>  
  
-   [<span data-ttu-id="c6277-123">Send SQL Server Agent Error Messages</span><span class="sxs-lookup"><span data-stu-id="c6277-123">Send SQL Server Agent Error Messages</span></span>](send-sql-server-agent-error-messages.md)  
  
 <span data-ttu-id="c6277-124">**실행 추적 메시지를 SQL Server 에이전트 오류 로그에 쓰려면**</span><span class="sxs-lookup"><span data-stu-id="c6277-124">**To write execution trace messages to the SQL Server Agent error log**</span></span>  
  
-   [<span data-ttu-id="c6277-125">SQL Server 에이전트 오류 로그에 실행 추적 메시지 작성&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="c6277-125">Write Execution Trace Messages to the SQL Server Agent Error Log &#40;SQL Server Management Studio&#41;</span></span>](write-execution-trace-messages-to-sql-server-agent-log-ssms.md)  
  
  
