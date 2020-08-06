---
title: SQL Server 에이전트 오류 로그 재활용 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.ag.errorlog.recyclesqlagenterrorlogs.f1
ms.assetid: 10bc2dd1-0505-4527-8ec7-d3b4e5d6352b
author: stevestein
ms.author: sstein
ms.openlocfilehash: 2b30f0a2ba9a2d861d4a36a86489757cde512fea
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660827"
---
# <a name="recycle-sql-server-agent-error-logs"></a><span data-ttu-id="76b0c-102">SQL Server 에이전트 오류 로그 재활용</span><span class="sxs-lookup"><span data-stu-id="76b0c-102">Recycle SQL Server Agent Error Logs</span></span>
  <span data-ttu-id="76b0c-103">이 페이지를 사용 하 여 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 오류 로그를 재활용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="76b0c-103">Use this page to recycle the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent Error Logs.</span></span> <span data-ttu-id="76b0c-104">이 로그를 재활용하면 현재 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 오류 로그가 닫히고 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트가 다시 시작되지 않은 상태에서 새 오류 로그가 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="76b0c-104">Recycling the log closes the current [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent error log and starts a new error log without restarting the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service.</span></span> <span data-ttu-id="76b0c-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트는 최근 9개의 오류 로그를 유지 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="76b0c-105">Notice that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent maintains the nine most recent error logs.</span></span> <span data-ttu-id="76b0c-106">오류 로그가 9개 있는 경우에 오류 로그를 재활용하면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트에서 가장 오래된 오류 로그가 제거됩니다.</span><span class="sxs-lookup"><span data-stu-id="76b0c-106">If there are already nine error logs present, recycling the error log causes [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent to remove the oldest error log.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76b0c-107">참고 항목</span><span class="sxs-lookup"><span data-stu-id="76b0c-107">See Also</span></span>  
 [<span data-ttu-id="76b0c-108">SQL Server 에이전트 오류 로그</span><span class="sxs-lookup"><span data-stu-id="76b0c-108">SQL Server Agent Error Log</span></span>](sql-server-agent-error-log.md)  
  
  
