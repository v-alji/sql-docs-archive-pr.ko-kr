---
title: SQL Server 에이전트 속성(기록 페이지) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.ag.agent.history.f1
ms.assetid: dc73734c-b3c3-407f-bbd1-8714b4fa47b0
author: stevestein
ms.author: sstein
ms.openlocfilehash: d67ff3da97e11292abcac03958fe1e423b35d7d1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659773"
---
# <a name="sql-server-agent-properties-history-page"></a><span data-ttu-id="f613b-102">SQL Server 에이전트 속성(기록 페이지)</span><span class="sxs-lookup"><span data-stu-id="f613b-102">SQL Server Agent Properties (History Page)</span></span>
  <span data-ttu-id="f613b-103">이 페이지를 사용 하 여 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 에이전트 서비스 기록 로그 관리에 대 한 설정을 확인 하 고 수정할 수 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f613b-103">Use this page to view and modify settings for managing the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service history log.</span></span>  
  
## <a name="options"></a><span data-ttu-id="f613b-104">옵션</span><span class="sxs-lookup"><span data-stu-id="f613b-104">Options</span></span>  
 <span data-ttu-id="f613b-105">**작업 기록 로그 크기 제한**</span><span class="sxs-lookup"><span data-stu-id="f613b-105">**Limit size of job history log**</span></span>  
 <span data-ttu-id="f613b-106">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트에서 로그에 보존할 작업 기록 정보의 크기 제한을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="f613b-106">Sets limits for the amount of job history information that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent retains in the log.</span></span>  
  
 <span data-ttu-id="f613b-107">**작업 기록 로그의 최대 크기(행 수)**</span><span class="sxs-lookup"><span data-stu-id="f613b-107">**Maximum job history log size (in rows)**</span></span>  
 <span data-ttu-id="f613b-108">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트에서 보존할 최대 행 수를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="f613b-108">Sets the maximum number of rows that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent retains.</span></span> <span data-ttu-id="f613b-109">로그의 행 수가 이 수에 도달한 경우 새 행을 입력하면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트가 가장 오래된 행을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="f613b-109">When the log grows to contain this number of rows, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent removes the oldest rows in the log as new rows are entered.</span></span>  
  
 <span data-ttu-id="f613b-110">**작업당 작업 기록의 최대 행 수**</span><span class="sxs-lookup"><span data-stu-id="f613b-110">**Maximum job history rows per job**</span></span>  
 <span data-ttu-id="f613b-111">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트에서 작업당 보존할 최대 행 수를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="f613b-111">Sets the maximum number of rows that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent retains per job.</span></span> <span data-ttu-id="f613b-112">특정 작업 기록의 행 수가 이 수에 도달한 경우 새 행을 입력하면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트가 로그에서 가장 오래된 행을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="f613b-112">When the history for a particular job grows to contain this number of rows, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent removes the oldest rows in the log as new rows are entered.</span></span>  
  
 <span data-ttu-id="f613b-113">**에이전트 기록 제거**</span><span class="sxs-lookup"><span data-stu-id="f613b-113">**Remove agent history**</span></span>  
 <span data-ttu-id="f613b-114">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트가 지정된 기간보다 오래된 항목을 로그에서 제거하도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f613b-114">Specifies that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent will remove entries that have been in the log longer than a specified length of time.</span></span> <span data-ttu-id="f613b-115">이 작업은 기록을 제거하는 일회 실행 작업입니다.</span><span class="sxs-lookup"><span data-stu-id="f613b-115">This is a one-time execution to remove the history.</span></span> <span data-ttu-id="f613b-116">작업을 되풀이해야 하는 경우에는 정리 작업을 사용하여 유지 관리 계획을 만들고 예약하십시오.</span><span class="sxs-lookup"><span data-stu-id="f613b-116">If a reoccurring job is needed, create and schedule a maintenance plan with a cleanup job.</span></span>  
  
 <span data-ttu-id="f613b-117">**다음보다 오래된 항목**</span><span class="sxs-lookup"><span data-stu-id="f613b-117">**Older than**</span></span>  
 <span data-ttu-id="f613b-118">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트에서 항목을 보존하는 기간을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="f613b-118">Sets the amount of time that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent will retain entries.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f613b-119">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f613b-119">See Also</span></span>  
 [<span data-ttu-id="f613b-120">SQL Server 에이전트 오류 로그</span><span class="sxs-lookup"><span data-stu-id="f613b-120">SQL Server Agent Error Log</span></span>](sql-server-agent-error-log.md)  
  
  
