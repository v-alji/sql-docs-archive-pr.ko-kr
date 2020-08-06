---
title: 작업 구현 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent]
- SQL Server Agent jobs
- SQL Server Agent jobs, about jobs
- jobs [SQL Server Agent], about jobs
ms.assetid: 69e06724-25c7-4fb3-8a5b-3d4596f21756
author: stevestein
ms.author: sstein
ms.openlocfilehash: 1925b3113db8d7c57ac4344958c0247763cfd1b1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639215"
---
# <a name="implement-jobs"></a><span data-ttu-id="48e37-102">작업 구현</span><span class="sxs-lookup"><span data-stu-id="48e37-102">Implement Jobs</span></span>
  <span data-ttu-id="48e37-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 작업을 사용하여 일상적인 관리 태스크를 자동화하고 정기적으로 실행함으로써 좀 더 효율적인 관리를 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="48e37-103">You can use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent jobs to automate routine administrative tasks and run them on a recurring basis, making administration more efficient.</span></span>  
  
 <span data-ttu-id="48e37-104">작업이란 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트가 순차적으로 수행하는 일련의 지정된 작업입니다.</span><span class="sxs-lookup"><span data-stu-id="48e37-104">A job is a specified series of operations performed sequentially by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.</span></span> <span data-ttu-id="48e37-105">작업은 [!INCLUDE[tsql](../../includes/tsql-md.md)] 스크립트, 명령줄 애플리케이션, Microsoft ActiveX 스크립트, Integration Services 패키지, Analysis Services 명령 및 쿼리 또는 복제 태스크를 실행하는 등 광범위한 활동을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="48e37-105">A job can perform a wide range of activities, including running [!INCLUDE[tsql](../../includes/tsql-md.md)] scripts, command-line applications, Microsoft ActiveX scripts, Integration Services packages, Analysis Services commands and queries, or Replication tasks.</span></span> <span data-ttu-id="48e37-106">작업은 반복적인 태스크나 예약 가능한 작업을 실행하고, 경고를 생성하여 작업 상태를 사용자에게 자동으로 알림으로써 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 관리를 간단하게 만들어 줍니다.</span><span class="sxs-lookup"><span data-stu-id="48e37-106">Jobs can run repetitive tasks or those that can be scheduled, and they can automatically notify users of job status by generating alerts, thereby greatly simplifying [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] administration.</span></span>  
  
 <span data-ttu-id="48e37-107">작업을 수동으로 실행하거나 일정에 따라 또는 경고에 응답하여 실행되도록 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="48e37-107">You can run a job manually, or you can configure it to run according to a schedule or in response to alerts.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="48e37-108">관련 작업</span><span class="sxs-lookup"><span data-stu-id="48e37-108">Related Tasks</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="48e37-109">**설명**</span><span class="sxs-lookup"><span data-stu-id="48e37-109">**Description**</span></span>|<span data-ttu-id="48e37-110">**항목**</span><span class="sxs-lookup"><span data-stu-id="48e37-110">**Topic**</span></span>|  
|<span data-ttu-id="48e37-111">작업을 만들고 소유권을 할당하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="48e37-111">Contains information about creating jobs and assigning ownership.</span></span>|[<span data-ttu-id="48e37-112">작업 만들기</span><span class="sxs-lookup"><span data-stu-id="48e37-112">Create Jobs</span></span>](create-jobs.md)|  
|<span data-ttu-id="48e37-113">범주에 작업을 구성하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="48e37-113">Contains information about organizing jobs into categories.</span></span>|[<span data-ttu-id="48e37-114">작업 구성</span><span class="sxs-lookup"><span data-stu-id="48e37-114">Organize Jobs</span></span>](organize-jobs.md)|  
|<span data-ttu-id="48e37-115">사용자가 만들 수 있는 작업 단계의 여러 가지 종류와 관리하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="48e37-115">Contains information about the different kinds of job steps you can create and how to manage them.</span></span>|[<span data-ttu-id="48e37-116">작업 단계 관리</span><span class="sxs-lookup"><span data-stu-id="48e37-116">Manage Job Steps</span></span>](manage-job-steps.md)|  
|<span data-ttu-id="48e37-117">작업의 실행 시작 시간 및 실행 빈도를 정의하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="48e37-117">Contains information about how to define when jobs start running and how often they should run.</span></span>|[<span data-ttu-id="48e37-118">일정을 만들고 작업에 연결</span><span class="sxs-lookup"><span data-stu-id="48e37-118">Create and Attach Schedules to Jobs</span></span>](create-and-attach-schedules-to-jobs.md)|  
|<span data-ttu-id="48e37-119">예약 없이 작업을 수동으로 실행하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="48e37-119">Contains information about manually running jobs (without a schedule).</span></span>|[<span data-ttu-id="48e37-120">작업 실행</span><span class="sxs-lookup"><span data-stu-id="48e37-120">Run Jobs</span></span>](run-jobs.md)|  
|<span data-ttu-id="48e37-121">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트가 작업에 응답하도록 구성하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="48e37-121">Contains information about how you can configure [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent to respond to jobs.</span></span> <span data-ttu-id="48e37-122">예를 들어 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트를 구성하여 작업이 끝났을 때 관리자에게 통보하도록 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="48e37-122">For example, you can configure [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent to notify administrators when jobs are finished.</span></span>|[<span data-ttu-id="48e37-123">작업 응답 지정</span><span class="sxs-lookup"><span data-stu-id="48e37-123">Specify Job Responses</span></span>](specify-job-responses.md)|  
|<span data-ttu-id="48e37-124">기존 작업을 보거나 실행 시 작업 기록을 보거나 작업을 수정하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="48e37-124">Contains information about how to view existing jobs, their history once executes, and how to modify them.</span></span>|[<span data-ttu-id="48e37-125">작업 보기 또는 수정</span><span class="sxs-lookup"><span data-stu-id="48e37-125">View or Modify Jobs</span></span>](view-or-modify-jobs.md)|  
|<span data-ttu-id="48e37-126">작업을 삭제하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="48e37-126">Contains information about how to delete jobs.</span></span>|[<span data-ttu-id="48e37-127">작업 삭제</span><span class="sxs-lookup"><span data-stu-id="48e37-127">Delete Jobs</span></span>](delete-jobs.md)|  
  
## <a name="see-also"></a><span data-ttu-id="48e37-128">참고 항목</span><span class="sxs-lookup"><span data-stu-id="48e37-128">See Also</span></span>  
 [<span data-ttu-id="48e37-129">SQL Server 에이전트 보안 구현</span><span class="sxs-lookup"><span data-stu-id="48e37-129">Implement SQL Server Agent Security</span></span>](implement-sql-server-agent-security.md)  
  
  
