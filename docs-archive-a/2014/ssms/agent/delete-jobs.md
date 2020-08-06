---
title: 작업 삭제 | Microsoft 문서
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- delete jobs
ms.assetid: bffb915e-bc84-4417-aa35-183243ca3312
author: stevestein
ms.author: sstein
ms.openlocfilehash: f66387a1334f91c29b8edddad293d76064430b39
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737456"
---
# <a name="delete-jobs"></a><span data-ttu-id="fda70-102">작업 삭제</span><span class="sxs-lookup"><span data-stu-id="fda70-102">Delete Jobs</span></span>
  <span data-ttu-id="fda70-103">작업이란 SQL Server 에이전트가 순차적으로 수행하는 일련의 지정된 작업입니다.</span><span class="sxs-lookup"><span data-stu-id="fda70-103">A job is a specified series of operations performed sequentially by SQL Server Agent.</span></span> <span data-ttu-id="fda70-104">기본적으로 실행이 완료되어도 작업은 삭제되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="fda70-104">By default, jobs are not deleted when execution finishes.</span></span> <span data-ttu-id="fda70-105">작업의 성공 또는 실패에 관계없이 하나 이상의 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 작업을 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fda70-105">You can delete one or more [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent jobs regardless of success or failure of the job.</span></span> <span data-ttu-id="fda70-106">작업이 성공, 실패 또는 완료되었을 때 자동으로 삭제하도록 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트를 구성할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fda70-106">You can also configure [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent to automatically delete jobs when they succeed, fail, or complete.</span></span>  
  
 <span data-ttu-id="fda70-107">기본적으로 **sysadmin** 고정 서버 역할의 멤버는 [sp_delete_job &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-delete-job-transact-sql) 시스템 저장 프로시저를 실행 하 여 작업을 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fda70-107">By default, members of the **sysadmin** fixed server role can execute the [sp_delete_job &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-delete-job-transact-sql) system stored procedure to delete a job.</span></span> <span data-ttu-id="fda70-108">다른 사용자는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] msdb **데이터베이스의 다음** 에이전트 고정 데이터베이스 역할 중 하나를 부여 받아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fda70-108">Other users must be granted one of the following [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent fixed database roles in the **msdb** database:</span></span>  
  
-   <span data-ttu-id="fda70-109">**SQLAgentUserRole**</span><span class="sxs-lookup"><span data-stu-id="fda70-109">**SQLAgentUserRole**</span></span>  
  
-   <span data-ttu-id="fda70-110">**SQLAgentReaderRole**</span><span class="sxs-lookup"><span data-stu-id="fda70-110">**SQLAgentReaderRole**</span></span>  
  
-   <span data-ttu-id="fda70-111">**SQLAgentOperatorRole**</span><span class="sxs-lookup"><span data-stu-id="fda70-111">**SQLAgentOperatorRole**</span></span>  
  
 <span data-ttu-id="fda70-112">이러한 역할의 사용 권한에 대한 자세한 내용은 [SQL Server 에이전트 고정 데이터베이스 역할](sql-server-agent-fixed-database-roles.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fda70-112">For details about the permissions of these roles, see [SQL Server Agent Fixed Database Roles](sql-server-agent-fixed-database-roles.md).</span></span>  
  
 <span data-ttu-id="fda70-113">**sysadmin** 고정 서버 역할의 멤버만 **sp_delete_job** 을 실행하여 모든 작업을 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fda70-113">Members of the **sysadmin** fixed server role can execute **sp_delete_job** to delete any job.</span></span> <span data-ttu-id="fda70-114">**sysadmin** 고정 서버 역할의 멤버가 아닌 사용자는 해당 사용자가 소유한 작업만 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fda70-114">A user that is not a member of the **sysadmin** fixed server role can only delete jobs owned by that user.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="fda70-115">관련 작업</span><span class="sxs-lookup"><span data-stu-id="fda70-115">Related Tasks</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="fda70-116">**설명**</span><span class="sxs-lookup"><span data-stu-id="fda70-116">**Description**</span></span>|<span data-ttu-id="fda70-117">**항목**</span><span class="sxs-lookup"><span data-stu-id="fda70-117">**Topic**</span></span>|  
|<span data-ttu-id="fda70-118">하나 이상의 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 작업을 삭제하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="fda70-118">Describes how to delete one or more [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent jobs.</span></span>|[<span data-ttu-id="fda70-119">하나 이상의 작업 삭제</span><span class="sxs-lookup"><span data-stu-id="fda70-119">Delete One or More Jobs</span></span>](delete-one-or-more-jobs.md)|  
|<span data-ttu-id="fda70-120">작업이 성공, 실패 또는 완료되었을 때 자동으로 삭제하도록 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트를 구성하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="fda70-120">Describes how to configure [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent to automatically delete jobs when they succeed, fail, or complete.</span></span>|[<span data-ttu-id="fda70-121">Automatically Delete a Job</span><span class="sxs-lookup"><span data-stu-id="fda70-121">Automatically Delete a Job</span></span>](automatically-delete-a-job.md)|  
  
  
