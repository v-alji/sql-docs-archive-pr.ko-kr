---
title: 서버 성능 및 작업 모니터링 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- activity monitoring [SQL Server]
- traces [SQL Server], how-to topics
- monitoring server performance [SQL Server], activity monitoring
- stored procedures [SQL Server], traces
- performance [SQL Server], servers
- servers [SQL Server], performance
- SQL Server Profiler, how-to topics
- SQL Server Management Studio [SQL Server], monitoring system
- Profiler [SQL Server Profiler], how-to topics
ms.assetid: f9abe48d-d6e9-4c38-a355-fc5eb5a95a25
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: a0fa7902d68c587a7733f07ceb8daccd3a6a98fd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661073"
---
# <a name="server-performance-and-activity-monitoring"></a><span data-ttu-id="6c814-102">서버 성능 및 작업 모니터링</span><span class="sxs-lookup"><span data-stu-id="6c814-102">Server Performance and Activity Monitoring</span></span>
  <span data-ttu-id="6c814-103">데이터베이스 모니터링의 목표는 서버의 성능을 평가하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="6c814-103">The goal of monitoring databases is to assess how a server is performing.</span></span> <span data-ttu-id="6c814-104">효과적인 모니터링을 위해서는 현재 성능에 대한 스냅샷을 정기적으로 만들어 문제를 일으키는 프로세스를 격리하고 데이터를 지속적으로 수집하여 성능 경향을 추적해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c814-104">Effective monitoring involves taking periodic snapshots of current performance to isolate processes that are causing problems, and gathering data continuously over time to track performance trends.</span></span> [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="6c814-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 및 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 운영 체제에서는 데이터베이스의 현재 상태를 확인하고 상태 변화에 따른 성능을 추적할 수 있는 유틸리티를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="6c814-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows operating system provide utilities that let you view the current condition of the database and to track performance as conditions change.</span></span>  
  
 <span data-ttu-id="6c814-106">다음 섹션에서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 와 Windows의 성능 및 작업 모니터링 도구 사용 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="6c814-106">The following section contains topics that describe how to use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and Windows performance and activity monitoring tools.</span></span> <span data-ttu-id="6c814-107">다음 항목이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="6c814-107">It contains the following topics:</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6c814-108">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="6c814-108">In This Section</span></span>  
 <span data-ttu-id="6c814-109">**Windows 도구로 모니터링 태스크를 수행**</span><span class="sxs-lookup"><span data-stu-id="6c814-109">**To perform monitoring tasks with Windows tools**</span></span>  
  
-   [<span data-ttu-id="6c814-110">시스템 모니터 시작&#40;Windows&#41;</span><span class="sxs-lookup"><span data-stu-id="6c814-110">Start System Monitor &#40;Windows&#41;</span></span>](start-system-monitor-windows.md)  
  
-   [<span data-ttu-id="6c814-111">Windows 애플리케이션 로그 보기&#40;Windows&#41;</span><span class="sxs-lookup"><span data-stu-id="6c814-111">View the Windows Application Log &#40;Windows&#41;</span></span>](view-the-windows-application-log-windows-10.md)  
  
 <span data-ttu-id="6c814-112">**Windows 도구로 SQL Server 데이터베이스 경고 만들기**</span><span class="sxs-lookup"><span data-stu-id="6c814-112">**To create SQL Server database alerts with Windows tools**</span></span>  
  
-   [<span data-ttu-id="6c814-113">SQL Server 데이터베이스 경고 설정&#40;Windows&#41;</span><span class="sxs-lookup"><span data-stu-id="6c814-113">Set Up a SQL Server Database Alert &#40;Windows&#41;</span></span>](set-up-a-sql-server-database-alert-windows.md)  
  
 <span data-ttu-id="6c814-114">**SQL Server Management Studio로 모니터링 태스크를 수행**</span><span class="sxs-lookup"><span data-stu-id="6c814-114">**To perform monitoring tasks with SQL Server Management Studio**</span></span>  
  
-   [<span data-ttu-id="6c814-115">SQL Server 오류 로그 보기&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="6c814-115">View the SQL Server Error Log &#40;SQL Server Management Studio&#41;</span></span>](../../ssms/sql-server-management-studio-ssms.md)  
  
-   [<span data-ttu-id="6c814-116">작업 모니터 열기&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="6c814-116">Open Activity Monitor &#40;SQL Server Management Studio&#41;</span></span>](../performance-monitor/open-activity-monitor-sql-server-management-studio.md)  
  
 <span data-ttu-id="6c814-117">**Transact-SQL 저장 프로시저를 사용하여 SQL 추적으로 모니터링 태스크를 수행**</span><span class="sxs-lookup"><span data-stu-id="6c814-117">**To perform monitoring tasks with SQL Trace by using Transact-SQL stored procedures**</span></span>  
  
-   [<span data-ttu-id="6c814-118">추적 만들기&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="6c814-118">Create a Trace &#40;Transact-SQL&#41;</span></span>](../sql-trace/create-a-trace-transact-sql.md)  
  
-   [<span data-ttu-id="6c814-119">추적 필터 설정&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="6c814-119">Set a Trace Filter &#40;Transact-SQL&#41;</span></span>](../../ssms/agent/set-sql-server-alias-for-sql-server-agent-service-ssms.md)  
  
-   [<span data-ttu-id="6c814-120">기존 추적 수정&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="6c814-120">Modify an Existing Trace &#40;Transact-SQL&#41;</span></span>](../sql-trace/modify-an-existing-trace-transact-sql.md)  
  
-   [<span data-ttu-id="6c814-121">저장된 추적 보기&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="6c814-121">View a Saved Trace &#40;Transact-SQL&#41;</span></span>](../sql-trace/view-a-saved-trace-transact-sql.md)  
  
-   [<span data-ttu-id="6c814-122">필터 정보 보기&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="6c814-122">View Filter Information &#40;Transact-SQL&#41;</span></span>](../sql-trace/view-filter-information-transact-sql.md)  
  
-   [<span data-ttu-id="6c814-123">추적 삭제&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="6c814-123">Delete a Trace &#40;Transact-SQL&#41;</span></span>](../sql-trace/delete-a-trace-transact-sql.md)  
  
 <span data-ttu-id="6c814-124">**SQL Server Profiler를 사용하여 추적을 만들고 수정**</span><span class="sxs-lookup"><span data-stu-id="6c814-124">**To create and modify traces by using SQL Server Profiler**</span></span>  
  
-   [<span data-ttu-id="6c814-125">추적 만들기&#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="6c814-125">Create a Trace &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/create-a-trace-sql-server-profiler.md)  
  
-   [<span data-ttu-id="6c814-126">전역 추적 옵션 설정&#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="6c814-126">Set Global Trace Options &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/set-global-trace-options-sql-server-profiler.md)  
  
-   [<span data-ttu-id="6c814-127">추적 파일에 대해 이벤트 및 데이터 열 지정&#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="6c814-127">Specify Events and Data Columns for a Trace File &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/specify-events-and-data-columns-for-a-trace-file-sql-server-profiler.md)  
  
-   [<span data-ttu-id="6c814-128">추적 실행을 위한 Transact-SQL 스크립트 만들기&#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="6c814-128">Create a Transact-SQL Script for Running a Trace &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/create-a-transact-sql-script-for-running-a-trace-sql-server-profiler.md)  
  
-   [<span data-ttu-id="6c814-129">추적 결과를 파일에 저장&#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="6c814-129">Save Trace Results to a File &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/save-trace-results-to-a-file-sql-server-profiler.md)  
  
-   [<span data-ttu-id="6c814-130">추적 파일에 최대 파일 크기 설정&#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="6c814-130">Set a Maximum File Size for a Trace File &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/set-a-maximum-file-size-for-a-trace-file-sql-server-profiler.md)  
  
-   [<span data-ttu-id="6c814-131">테이블에 추적 결과 저장&#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="6c814-131">Save Trace Results to a Table &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/save-trace-results-to-a-table-sql-server-profiler.md)  
  
-   [<span data-ttu-id="6c814-132">추적 테이블에 최대 테이블 크기 설정&#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="6c814-132">Set a Maximum Table Size for a Trace Table &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/set-a-maximum-table-size-for-a-trace-table-sql-server-profiler.md)  
  
-   [<span data-ttu-id="6c814-133">추적에서의 이벤트 필터링&#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="6c814-133">Filter Events in a Trace &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/filter-events-in-a-trace-sql-server-profiler.md)  
  
-   [<span data-ttu-id="6c814-134">필터 정보 보기&#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="6c814-134">View Filter Information &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/view-filter-information-sql-server-profiler.md)  
  
-   [<span data-ttu-id="6c814-135">필터 수정&#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="6c814-135">Modify a Filter &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/modify-a-filter-sql-server-profiler.md)  
  
-   [<span data-ttu-id="6c814-136">이벤트 시작 시간을 기준으로 이벤트 필터링&#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="6c814-136">Filter Events Based on the Event Start Time &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/filter-events-based-on-the-event-start-time-sql-server-profiler.md)  
  
-   [<span data-ttu-id="6c814-137">이벤트 종료 시간 기반의 이벤트 필터링&#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="6c814-137">Filter Events Based on the Event End Time &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/filter-events-based-on-the-event-end-time-sql-server-profiler.md)  
  
-   [<span data-ttu-id="6c814-138">추적의 SPID&#40;서버 프로세스 ID&#41; 필터링&#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="6c814-138">Filter Server Process IDs &#40;SPIDs&#41; in a Trace &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/filter-server-process-ids-spids-in-a-trace-sql-server-profiler.md)  
  
-   [<span data-ttu-id="6c814-139">표시된 열 추적으로 구성&#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="6c814-139">Organize Columns Displayed in a Trace &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/organize-columns-displayed-in-a-trace-sql-server-profiler.md)  
  
 <span data-ttu-id="6c814-140">**SQL Server Profiler를 사용하여 추적을 시작, 일시 중지 및 중지**</span><span class="sxs-lookup"><span data-stu-id="6c814-140">**To start, pause, and stop traces by using SQL Server Profiler**</span></span>  
  
-   [<span data-ttu-id="6c814-141">서버 연결 후 자동으로 추적 시작&#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="6c814-141">Start a Trace Automatically after Connecting to a Server &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/start-a-trace-automatically-after-connecting-to-a-server-sql-server-profiler.md)  
  
-   [<span data-ttu-id="6c814-142">추적 일시 중지&#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="6c814-142">Pause a Trace &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/pause-a-trace-sql-server-profiler.md)  
  
-   [<span data-ttu-id="6c814-143">추적 중지&#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="6c814-143">Stop a Trace &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/stop-a-trace-sql-server-profiler.md)  
  
-   [<span data-ttu-id="6c814-144">일시 중지 또는 중지 후 추적 실행&#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="6c814-144">Run a Trace After It Has Been Paused or Stopped &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/run-a-trace-after-it-has-been-paused-or-stopped-sql-server-profiler.md)  
  
 <span data-ttu-id="6c814-145">**SQL Server Profiler를 사용하여 추적을 열거나 추적 표시 방법을 구성**</span><span class="sxs-lookup"><span data-stu-id="6c814-145">**To open traces and configure how traces are displayed by using SQL Server Profiler**</span></span>  
  
-   [<span data-ttu-id="6c814-146">추적 파일 열기&#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="6c814-146">Open a Trace File &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/open-a-trace-file-sql-server-profiler.md)  
  
-   [<span data-ttu-id="6c814-147">추적 테이블 열기&#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="6c814-147">Open a Trace Table &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/open-a-trace-table-sql-server-profiler.md)  
  
-   [<span data-ttu-id="6c814-148">추적 창 지우기&#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="6c814-148">Clear a Trace Window &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/clear-a-trace-window-sql-server-profiler.md)  
  
-   [<span data-ttu-id="6c814-149">추적 창 닫기&#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="6c814-149">Close a Trace Window &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/close-a-trace-window-sql-server-profiler.md)  
  
-   [<span data-ttu-id="6c814-150">추적 정의 기본값 설정&#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="6c814-150">Set Trace Definition Defaults &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/set-trace-definition-defaults-sql-server-profiler.md)  
  
-   [<span data-ttu-id="6c814-151">추적 표시 기본값 설정&#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="6c814-151">Set Trace Display Defaults &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/set-trace-display-defaults-sql-server-profiler.md)  
  
 <span data-ttu-id="6c814-152">**SQL Server Profiler를 사용하여 추적 재생**</span><span class="sxs-lookup"><span data-stu-id="6c814-152">**To replay traces by using SQL Server Profiler**</span></span>  
  
-   [<span data-ttu-id="6c814-153">추적 파일 재생&#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="6c814-153">Replay a Trace File &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/replay-a-trace-file-sql-server-profiler.md)  
  
-   [<span data-ttu-id="6c814-154">추적 테이블 재생&#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="6c814-154">Replay a Trace Table &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/replay-a-trace-table-sql-server-profiler.md)  
  
-   [<span data-ttu-id="6c814-155">단일 이벤트를 한 번에 하나씩 재생&#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="6c814-155">Replay a Single Event at a Time &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/replay-a-single-event-at-a-time-sql-server-profiler.md)  
  
-   [<span data-ttu-id="6c814-156">중단점까지 재생&#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="6c814-156">Replay to a Breakpoint &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/replay-to-a-breakpoint-sql-server-profiler.md)  
  
-   [<span data-ttu-id="6c814-157">커서까지 재생&#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="6c814-157">Replay to a Cursor &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/replay-to-a-cursor-sql-server-profiler.md)  
  
-   [<span data-ttu-id="6c814-158">Transact-SQL 스크립트 재생&#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="6c814-158">Replay a Transact-SQL Script &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/replay-a-transact-sql-script-sql-server-profiler.md)  
  
 <span data-ttu-id="6c814-159">**SQL Server Profiler를 사용하여 추적 템플릿을 생성, 수정 및 사용**</span><span class="sxs-lookup"><span data-stu-id="6c814-159">**To create, modify, and use trace templates by using SQL Server Profiler**</span></span>  
  
-   [<span data-ttu-id="6c814-160">추적 템플릿 만들기&#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="6c814-160">Create a Trace Template &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/create-a-trace-template-sql-server-profiler.md)  
  
-   [<span data-ttu-id="6c814-161">추적 템플릿 수정&#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="6c814-161">Modify a Trace Template &#40;SQL Server Profiler&#41;</span></span>](../../database-engine/modify-a-trace-template-sql-server-profiler.md)  
  
-   [<span data-ttu-id="6c814-162">실행 중인 추적으로부터 템플릿 파생&#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="6c814-162">Derive a Template from a Running Trace &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/derive-a-template-from-a-running-trace-sql-server-profiler.md)  
  
-   [<span data-ttu-id="6c814-163">추적 파일 또는 추적 테이블에서 템플릿 파생&#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="6c814-163">Derive a Template from a Trace File or Trace Table &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/derive-a-template-from-a-trace-file-or-trace-table-sql-server-profiler.md)  
  
-   [<span data-ttu-id="6c814-164">추적 템플릿 내보내기&#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="6c814-164">Export a Trace Template &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/export-a-trace-template-sql-server-profiler.md)  
  
-   [<span data-ttu-id="6c814-165">추적 템플릿 가져오기&#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="6c814-165">Import a Trace Template &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/import-a-trace-template-sql-server-profiler.md)  
  
 <span data-ttu-id="6c814-166">**SQL Server Profiler 추적을 사용하여 서버 성능을 수집 및 모니터링**</span><span class="sxs-lookup"><span data-stu-id="6c814-166">**To use SQL Server Profiler traces to collect and monitor server performance**</span></span>  
  
-   [<span data-ttu-id="6c814-167">추적 중 값 또는 데이터 열 찾기&#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="6c814-167">Find a Value or Data Column While Tracing &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/find-a-value-or-data-column-while-tracing-sql-server-profiler.md)  
  
-   [<span data-ttu-id="6c814-168">교착 상태 그래프 저장&#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="6c814-168">Save Deadlock Graphs &#40;SQL Server Profiler&#41;</span></span>](save-deadlock-graphs-sql-server-profiler.md)  
  
-   [<span data-ttu-id="6c814-169">Showplan XML 이벤트를 개별적으로 저장&#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="6c814-169">Save Showplan XML Events Separately &#40;SQL Server Profiler&#41;</span></span>](save-showplan-xml-events-separately-sql-server-profiler.md)  
  
-   [<span data-ttu-id="6c814-170">Showplan XML Statistics Profile 이벤트를 개별적으로 저장&#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="6c814-170">Save Showplan XML Statistics Profile Events Separately &#40;SQL Server Profiler&#41;</span></span>](save-showplan-xml-statistics-profile-events-separately-sql-server-profiler.md)  
  
-   [<span data-ttu-id="6c814-171">추적에서 스크립트 추출&#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="6c814-171">Extract a Script from a Trace &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/extract-a-script-from-a-trace-sql-server-profiler.md)  
  
-   [<span data-ttu-id="6c814-172">추적과 Windows 성능 로그 데이터의 상관 관계 지정&#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="6c814-172">Correlate a Trace with Windows Performance Log Data &#40;SQL Server Profiler&#41;</span></span>](../../database-engine/correlate-a-trace-with-windows-performance-log-data-sql-server-profiler.md)  
  
  
