---
title: 작업 만들기 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent], creating
- SQL Server Agent jobs, creating
ms.assetid: 465fb7fc-7622-4252-a178-ea51691c935b
author: stevestein
ms.author: sstein
ms.openlocfilehash: 706b9348eed5b190f99543a74e7019dc1bde5978
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731368"
---
# <a name="create-jobs"></a><span data-ttu-id="48914-102">작업 만들기</span><span class="sxs-lookup"><span data-stu-id="48914-102">Create Jobs</span></span>
  <span data-ttu-id="48914-103">작업이란 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트가 순차적으로 수행하는 일련의 지정된 작업입니다.</span><span class="sxs-lookup"><span data-stu-id="48914-103">A job is a specified series of operations performed sequentially by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.</span></span> <span data-ttu-id="48914-104">작업은 [!INCLUDE[tsql](../../includes/tsql-md.md)] 스크립트, 명령 프롬프트 애플리케이션, Microsoft ActiveX 스크립트, Integration Services 패키지, Analysis Services 명령 및 쿼리 또는 복제 태스크를 실행하는 등 광범위한 활동을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="48914-104">A job can perform a wide range of activities, including running [!INCLUDE[tsql](../../includes/tsql-md.md)] scripts, command prompt applications, Microsoft ActiveX scripts, Integration Services packages, Analysis Services commands and queries, or Replication tasks.</span></span> <span data-ttu-id="48914-105">작업은 반복적인 태스크나 예약 가능한 태스크를 실행하고 경고를 발생시켜 작업 상태를 사용자에게 자동으로 알리므로 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 관리를 매우 단순하게 만들어 줍니다.</span><span class="sxs-lookup"><span data-stu-id="48914-105">Jobs can run repetitive or schedulable tasks, and they can automatically notify users of job status by generating alerts, thereby greatly simplifying [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] administration.</span></span>  
  
 <span data-ttu-id="48914-106">작업을 만들려면 사용자가 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 고정 데이터베이스 역할이나 **sysadmin** 고정 서버 역할 중 하나의 멤버여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="48914-106">To create a job, a user must be a member of one of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent fixed database roles or the **sysadmin** fixed server role.</span></span> <span data-ttu-id="48914-107">작업은 소유자나 **sysadmin** 역할의 멤버만 편집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="48914-107">A job can be edited only by its owner or members of the **sysadmin** role.</span></span> <span data-ttu-id="48914-108">**sysadmin** 역할의 멤버는 작업 소유권을 다른 사용자에게 할당할 수 있으며 작업 소유자가 아니어도 모든 작업을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="48914-108">Members of the **sysadmin** role can assign job ownership to other users, and they can run any job, regardless of the job owner.</span></span> <span data-ttu-id="48914-109">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 고정 데이터베이스 역할에 대한 자세한 내용은 [SQL Server 에이전트 고정 데이터베이스 역할](sql-server-agent-fixed-database-roles.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="48914-109">For more information about the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent fixed database roles, see [SQL Server Agent Fixed Database Roles](sql-server-agent-fixed-database-roles.md).</span></span>  
  
 <span data-ttu-id="48914-110">작업은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 의 로컬 인스턴스나 엔터프라이즈 내의 다중 인스턴스에서 실행되도록 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="48914-110">Jobs can be written to run on the local instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] or on multiple instances across an enterprise.</span></span> <span data-ttu-id="48914-111">다중 서버에서 작업을 실행하려면 적어도 마스터 서버 한 대와 대상 서버 한 대 이상을 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="48914-111">To run jobs on multiple servers, you must set up at least one master server and one or more target servers.</span></span> <span data-ttu-id="48914-112">마스터 및 대상 서버에 대한 자세한 내용은 [기업 내 관리 자동화](automated-administration-across-an-enterprise.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="48914-112">For more information about master and target servers, see [Automated Administration Across an Enterprise](automated-administration-across-an-enterprise.md)</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="48914-113">에이전트에서 작업과 작업 단계 정보를 작업 기록에 기록합니다.</span><span class="sxs-lookup"><span data-stu-id="48914-113">Agent records job and job step information in the job history.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="48914-114">관련 작업</span><span class="sxs-lookup"><span data-stu-id="48914-114">Related Tasks</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="48914-115">**설명**</span><span class="sxs-lookup"><span data-stu-id="48914-115">**Description**</span></span>|<span data-ttu-id="48914-116">**항목**</span><span class="sxs-lookup"><span data-stu-id="48914-116">**Topic**</span></span>|  
|<span data-ttu-id="48914-117">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 작업을 만드는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="48914-117">Describes how to create a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job.</span></span>|[<span data-ttu-id="48914-118">작업 만들기</span><span class="sxs-lookup"><span data-stu-id="48914-118">Create a Job</span></span>](create-a-job.md)|  
|<span data-ttu-id="48914-119">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 작업의 소유권을 다른 사용자에게 다시 할당하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="48914-119">Describes how to reassign ownership of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent jobs to another user.</span></span>|[<span data-ttu-id="48914-120">Give Others Ownership of a Job</span><span class="sxs-lookup"><span data-stu-id="48914-120">Give Others Ownership of a Job</span></span>](give-others-ownership-of-a-job.md)|  
|<span data-ttu-id="48914-121">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 작업 기록 로그를 설정하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="48914-121">Describes how to set up the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job history log.</span></span>|[<span data-ttu-id="48914-122">Set Up the Job History Log</span><span class="sxs-lookup"><span data-stu-id="48914-122">Set Up the Job History Log</span></span>](set-up-the-job-history-log.md)|  
  
## <a name="see-also"></a><span data-ttu-id="48914-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="48914-123">See Also</span></span>  
 <span data-ttu-id="48914-124">[작업 단계 관리](manage-job-steps.md) </span><span class="sxs-lookup"><span data-stu-id="48914-124">[Manage Job Steps](manage-job-steps.md) </span></span>  
 <span data-ttu-id="48914-125">[기업 내 관리 자동화](automated-administration-across-an-enterprise.md) </span><span class="sxs-lookup"><span data-stu-id="48914-125">[Automated Administration Across an Enterprise](automated-administration-across-an-enterprise.md) </span></span>  
 <span data-ttu-id="48914-126">[일정을 만들고 작업에 연결](create-and-attach-schedules-to-jobs.md) </span><span class="sxs-lookup"><span data-stu-id="48914-126">[Create and Attach Schedules to Jobs](create-and-attach-schedules-to-jobs.md) </span></span>  
 <span data-ttu-id="48914-127">[작업 실행](run-jobs.md) </span><span class="sxs-lookup"><span data-stu-id="48914-127">[Run Jobs](run-jobs.md) </span></span>  
 [<span data-ttu-id="48914-128">작업 보기 또는 수정</span><span class="sxs-lookup"><span data-stu-id="48914-128">View or Modify Jobs</span></span>](view-or-modify-jobs.md)  
  
  
