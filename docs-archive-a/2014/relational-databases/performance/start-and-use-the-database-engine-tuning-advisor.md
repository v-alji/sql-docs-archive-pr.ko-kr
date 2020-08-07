---
title: 데이터베이스 엔진 튜닝 관리자 시작 및 사용 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
f1_keywords:
- sql12.dta.advancedtuningoptions.f1
- sql12.dta.general.f1
- sql12.dta.tuningoptions.f1
- sql12.dta.workload.f1
- sql12.dta.progress.f1
- sql12.dta.options.f1
helpviewer_keywords:
- Database Engine Tuning Advisor [SQL Server], starting
ms.assetid: a4e3226a-3917-4ec8-bdf0-472879d231c9
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 46f8e49de657d7021d846c7e57022a580b877f8e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87732604"
---
# <a name="start-and-use-the-database-engine-tuning-advisor"></a><span data-ttu-id="17536-102">데이터베이스 엔진 튜닝 관리자 시작 및 사용</span><span class="sxs-lookup"><span data-stu-id="17536-102">Start and Use the Database Engine Tuning Advisor</span></span>
  <span data-ttu-id="17536-103">이 항목에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]에서 데이터베이스 엔진 튜닝 관리자를 시작 및 사용하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="17536-103">This topic describes how to start and use Database Engine Tuning Advisor in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="17536-104">데이터베이스 튜닝 후 결과를 보고 작업하는 방법은 [데이터베이스 엔진 튜닝 관리자의 출력 보기 및 작업](database-engine-tuning-advisor.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="17536-104">For information about how to view and work with the results after you tune a database, see [View and Work with the Output from the Database Engine Tuning Advisor](database-engine-tuning-advisor.md).</span></span>  
  
##  <a name="initialize-the-database-engine-tuning-advisor"></a><a name="Initialize"></a> <span data-ttu-id="17536-105">데이터베이스 엔진 튜닝 관리자 초기화</span><span class="sxs-lookup"><span data-stu-id="17536-105">Initialize the Database Engine Tuning Advisor</span></span>  
 <span data-ttu-id="17536-106">처음 사용할 때는 **sysadmin** 고정 서버 역할의 멤버인 사용자가 데이터베이스 엔진 튜닝 관리자를 초기화해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="17536-106">On first use, a user who is member of the **sysadmin** fixed server role must initialize the Database Engine Tuning Advisor.</span></span> <span data-ttu-id="17536-107">튜닝 작업을 지원하려면 `msdb` 데이터베이스에서 여러 시스템 테이블을 만들어야 하기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="17536-107">This is because several system tables must be created in the `msdb` database to support tuning operations.</span></span> <span data-ttu-id="17536-108">**db_owner** 고정 데이터베이스 역할의 멤버인 사용자는 초기화를 통해 자신이 소유한 데이터베이스의 테이블에 대한 작업을 튜닝할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="17536-108">Initialization also enables users that are members of the **db_owner** fixed database role to tune workloads on tables in databases that they own.</span></span>  
  
 <span data-ttu-id="17536-109">시스템 관리자 권한을 가진 사용자가 다음 동작 중 하나를 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="17536-109">A user that has system administrator permissions must perform either of the following actions:</span></span>  
  
-   <span data-ttu-id="17536-110">데이터베이스 엔진 튜닝 관리자 그래픽 사용자 인터페이스를 사용하여 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]의 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="17536-110">Use the Database Engine Tuning Advisor graphical user interface to connect to an instance of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="17536-111">자세한 내용은 이 항목의 뒷부분에 나오는 [데이터베이스 엔진 튜닝 관리자 시작](#Start) 을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="17536-111">For more information, see [Start the Database Engine Tuning Advisor](#Start) later in this topic.</span></span>  
  
-   <span data-ttu-id="17536-112">**dta** 유틸리티를 사용하여 첫 번째 작업을 튜닝합니다.</span><span class="sxs-lookup"><span data-stu-id="17536-112">Use the **dta** utility to tune the first workload.</span></span> <span data-ttu-id="17536-113">자세한 내용은 이 항목의 뒷부분에 나오는 [dta 유틸리티 사용](#dta) 을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="17536-113">For more information, see [Use the dta Utility](#dta) later in this topic.</span></span>  
  
##  <a name="start-the-database-engine-tuning-advisor"></a><a name="Start"></a> <span data-ttu-id="17536-114">데이터베이스 엔진 튜닝 관리자 시작</span><span class="sxs-lookup"><span data-stu-id="17536-114">Start the Database Engine Tuning Advisor</span></span>  
 <span data-ttu-id="17536-115">여러 다른 방법으로 데이터베이스 엔진 튜닝 관리자 GUI(그래픽 사용자 인터페이스)를 시작하여 다양한 시나리오에서 데이터베이스 튜닝을 지원할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="17536-115">You can start the Database Engine Tuning Advisor graphical user interface (GUI) in several different ways to support database tuning in a variety of scenarios.</span></span> <span data-ttu-id="17536-116">데이터베이스 엔진 튜닝 관리자는 **시작** 메뉴, **의** 도구 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]메뉴, [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]의 쿼리 편집기, **의** 도구 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]메뉴 등과 같은 다양한 방법으로 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="17536-116">The different ways to start Database Engine Tuning Advisor include: from the **Start** menu, from the **Tools** menu in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], from the Query Editor in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], and from the **Tools** menu in [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span> <span data-ttu-id="17536-117">데이터베이스 엔진 튜닝 관리자를 처음 시작하면 연결할 **인스턴스를 지정할 수 있는** 서버에 연결 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 대화 상자가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="17536-117">When you first start Database Engine Tuning Advisor, the application displays a **Connect to Server** dialog box where you can specify the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance to which you want to connect.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="17536-118">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 가 단일 사용자 모드에서 실행 중이면 데이터베이스 엔진 튜닝 관리자를 시작하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="17536-118">Do not start Database Engine Tuning Advisor when [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is running in single-user mode.</span></span> <span data-ttu-id="17536-119">서버가 단일 사용자 모드일 때 데이터베이스 엔진 튜닝 관리자를 시작하려고 시도하면 오류가 반환되고 데이터베이스 엔진 튜닝 관리자가 시작되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="17536-119">If you attempt to start it while the server is in single-user mode, an error will be returned and Database Engine Tuning Advisor will not start.</span></span> <span data-ttu-id="17536-120">단일 사용자 모드에 대한 자세한 내용은 [단일 사용자 모드로 SQL Server 시작](../../database-engine/configure-windows/start-sql-server-in-single-user-mode.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="17536-120">For more information about single-user mode, see [Start SQL Server in Single-User Mode](../../database-engine/configure-windows/start-sql-server-in-single-user-mode.md).</span></span>  
  
#### <a name="to-start-database-engine-tuning-advisor-from-the-windows-start-menu"></a><span data-ttu-id="17536-121">Windows 시작 메뉴에서 데이터베이스 엔진 튜닝 관리자를 시작하려면</span><span class="sxs-lookup"><span data-stu-id="17536-121">To start Database Engine Tuning Advisor from the Windows Start menu</span></span>  
  
1.  <span data-ttu-id="17536-122">**시작** 메뉴에서 **모든 프로그램**, **Microsoft SQL Server**, **성능 도구**를 차례로 가리킨 다음 **데이터베이스 엔진 튜닝 관리자**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="17536-122">On the **Start** menu, point to **All Programs**, point to **Microsoft SQL Server**, point to **Performance Tools**, and then click **Database Engine Tuning Advisor**.</span></span>  
  
#### <a name="to-start-the-database-engine-tuning-advisor-in-sql-server-management-studio"></a><span data-ttu-id="17536-123">SQL Server Management Studio에서 데이터베이스 엔진 튜닝 관리자를 시작하려면</span><span class="sxs-lookup"><span data-stu-id="17536-123">To start the Database Engine Tuning Advisor in SQL Server Management Studio</span></span>  
  
1.  <span data-ttu-id="17536-124">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] **도구** 메뉴에서 **데이터베이스 엔진 튜닝 관리자**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="17536-124">On the [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] **Tools** menu, click **Database Engine Tuning Advisor**.</span></span>  
  
#### <a name="to-start-the-database-engine-tuning-advisor-from-the-sql-server-management-studio-query-editor"></a><span data-ttu-id="17536-125">SQL Server Management Studio 쿼리 편집기에서 데이터베이스 엔진 튜닝 관리자를 시작하려면</span><span class="sxs-lookup"><span data-stu-id="17536-125">To start the Database Engine Tuning Advisor from the SQL Server Management Studio Query Editor</span></span>  
  
1.  <span data-ttu-id="17536-126">[!INCLUDE[tsql](../../includes/tsql-md.md)] 에서 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]스크립트 파일을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="17536-126">Open a [!INCLUDE[tsql](../../includes/tsql-md.md)] script file in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="17536-127">자세한 내용은 [쿼리 및 텍스트 편집기&#40;SQL Server Management Studio&#41;](../scripting/query-and-text-editors-sql-server-management-studio.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="17536-127">For more information, see [Query and Text Editors &#40;SQL Server Management Studio&#41;](../scripting/query-and-text-editors-sql-server-management-studio.md).</span></span>  
  
2.  <span data-ttu-id="17536-128">[!INCLUDE[tsql](../../includes/tsql-md.md)] 스크립트에서 쿼리를 선택하거나 전체 스크립트를 선택하고 선택 영역을 마우스 오른쪽 단추를 클릭한 다음 **데이터베이스 엔진 튜닝 관리자의 쿼리 분석**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="17536-128">Select a query in the [!INCLUDE[tsql](../../includes/tsql-md.md)] script, or select the entire script, right-click the selection, and choose **Analyze Query in Database Engine Tuning Advisor**.</span></span> <span data-ttu-id="17536-129">데이터베이스 엔진 튜닝 관리자 GUI가 열리고 스크립트를 XML 파일 작업으로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="17536-129">The Database Engine Tuning Advisor GUI opens and imports the script as an XML file workload.</span></span> <span data-ttu-id="17536-130">세션 이름과 튜닝 옵션을 지정하여 선택한 [!INCLUDE[tsql](../../includes/tsql-md.md)] 쿼리를 작업으로 튜닝할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="17536-130">You can specify a session name and tuning options to tune the selected [!INCLUDE[tsql](../../includes/tsql-md.md)] queries as your workload.</span></span>  
  
#### <a name="to-start-the-database-engine-tuning-advisor-in-sql-server-profiler"></a><span data-ttu-id="17536-131">SQL Server Profiler에서 데이터베이스 엔진 튜닝 관리자를 시작하려면</span><span class="sxs-lookup"><span data-stu-id="17536-131">To start the Database Engine Tuning Advisor in SQL Server Profiler</span></span>  
  
1.  <span data-ttu-id="17536-132">SQL Server Profiler **도구** 메뉴에서 **데이터베이스 엔진 튜닝 관리자**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="17536-132">On the SQL Server Profiler **Tools** menu, click **Database Engine Tuning Advisor**.</span></span>  
  
##  <a name="create-a-workload"></a><a name="Create"></a> <span data-ttu-id="17536-133">작업 만들기</span><span class="sxs-lookup"><span data-stu-id="17536-133">Create a Workload</span></span>  
 <span data-ttu-id="17536-134">작업은 튜닝하려는 데이터베이스에 대해 실행되는 일련의 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문입니다.</span><span class="sxs-lookup"><span data-stu-id="17536-134">A workload is a set of [!INCLUDE[tsql](../../includes/tsql-md.md)] statements that execute against a database or databases that you want to tune.</span></span> <span data-ttu-id="17536-135">데이터베이스 엔진 튜닝 관리자는 이러한 작업을 분석하여 서버의 쿼리 성능을 향상시키는 인덱스 또는 분할 전략을 권장합니다.</span><span class="sxs-lookup"><span data-stu-id="17536-135">Database Engine Tuning Advisor analyzes these workloads to recommend indexes or partitioning strategies that will improve your server's query performance.</span></span>  
  
 <span data-ttu-id="17536-136">다음 방법 중 하나를 사용하여 작업을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="17536-136">You can create a workload by using one of the following methods.</span></span>  
  
-   <span data-ttu-id="17536-137">계획 캐시를 작업으로 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="17536-137">Use the plan cache as a workload.</span></span> <span data-ttu-id="17536-138">이렇게 하면 작업을 수동으로 만들 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="17536-138">By doing this, you can avoid having to manually create a workload.</span></span> <span data-ttu-id="17536-139">자세한 내용은 이 항목의 뒷부분에 나오는 [데이터베이스 튜닝](#Tune) 을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="17536-139">For more information, see [Tune a Database](#Tune) later in this topic.</span></span>  
  
-   <span data-ttu-id="17536-140">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 의 쿼리 편집기나 선호하는 텍스트 편집기를 사용하여 [!INCLUDE[tsql](../../includes/tsql-md.md)] 스크립트 작업을 수동으로 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="17536-140">Use the Query Editor in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or your favorite text editor to manually create [!INCLUDE[tsql](../../includes/tsql-md.md)] script workloads.</span></span>  
  
-   <span data-ttu-id="17536-141">[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 를 사용하여 추적 파일이나 추적 테이블 작업을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="17536-141">Use [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] to create trace file or trace table workloads</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="17536-142">추적 테이블을 작업 테이블로 사용하는 경우 해당 테이블은 데이터베이스 엔진 튜닝 관리자가 튜닝 중인 서버와 동일한 서버에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="17536-142">When using a trace table as a workload, that table must exist on the same server where Database Engine Tuning Advisor is tuning.</span></span> <span data-ttu-id="17536-143">다른 서버에 추적 테이블을 만든 경우에는 해당 테이블을 데이터베이스 엔진 튜닝 관리자가 튜닝하는 서버로 이동하세요.</span><span class="sxs-lookup"><span data-stu-id="17536-143">If you create the trace table on a different server, then move it to the server where Database Engine Tuning Advisor is tuning.</span></span>  
  
-   <span data-ttu-id="17536-144">작업은 각 이벤트에 대한 가중치를 지정할 수 있는 XML 입력 파일에도 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="17536-144">Workloads can also be embedded in an XML input file, where you can also specify a weight for each event.</span></span> <span data-ttu-id="17536-145">포함된 작업을 지정하는 방법은 이 항목의 뒷부분에 나오는 [XML 입력 파일 만들기](#XMLInput) 를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="17536-145">For more information about specifying embedded workloads, see [Create an XML Input File](#XMLInput) later in this topic.</span></span>  
  
###  <a name="to-create-transact-sql-script-workloads"></a><a name="SSMS"></a> <span data-ttu-id="17536-146">Transact-SQL 스크립트 작업을 만들려면</span><span class="sxs-lookup"><span data-stu-id="17536-146">To create Transact-SQL script workloads</span></span>  
  
1.  <span data-ttu-id="17536-147">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서 쿼리 편집기를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="17536-147">Launch the Query Editor in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="17536-148">자세한 내용은 [쿼리 및 텍스트 편집기&#40;SQL Server Management Studio&#41;](../scripting/query-and-text-editors-sql-server-management-studio.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="17536-148">For more information, see [Query and Text Editors &#40;SQL Server Management Studio&#41;](../scripting/query-and-text-editors-sql-server-management-studio.md).</span></span>  
  
2.  <span data-ttu-id="17536-149">쿼리 편집기에 [!INCLUDE[tsql](../../includes/tsql-md.md)] 스크립트를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="17536-149">Type your [!INCLUDE[tsql](../../includes/tsql-md.md)] script into the Query Editor.</span></span> <span data-ttu-id="17536-150">이 스크립트는 튜닝하려는 데이터베이스에 대해 실행되는 일련의 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문을 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="17536-150">This script should contain a set of [!INCLUDE[tsql](../../includes/tsql-md.md)] statements that execute against the database or databases that you want to tune.</span></span>  
  
3.  <span data-ttu-id="17536-151">파일을 **.sql** 확장명으로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="17536-151">Save the file with a **.sql** extension.</span></span> <span data-ttu-id="17536-152">데이터베이스 엔진 튜닝 관리자 GUI 및 명령줄 **dta** 유틸리티에서 이 [!INCLUDE[tsql](../../includes/tsql-md.md)] 스크립트를 작업으로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="17536-152">The Database Engine Tuning Advisor GUI and the command-line **dta** utility can use this [!INCLUDE[tsql](../../includes/tsql-md.md)] script as a workload.</span></span>  
  
###  <a name="to-create-trace-file-and-trace-table-workloads"></a><a name="Profiler"></a> <span data-ttu-id="17536-153">추적 파일 및 추적 테이블 작업을 만들려면</span><span class="sxs-lookup"><span data-stu-id="17536-153">To create trace file and trace table workloads</span></span>  
  
1.  <span data-ttu-id="17536-154">다음 중 한 가지 방법을 사용하여 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="17536-154">Launch [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] by using one of the following methods:</span></span>  
  
    -   <span data-ttu-id="17536-155">**시작** 메뉴에서 **모든 프로그램**, **Microsoft SQL Server**, **성능 도구**를 차례로 가리킨 다음 **SQL Server Profiler**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="17536-155">On the **Start** menu, point to **All Programs**, **Microsoft SQL Server**, **Performance Tools**, and then click **SQL Server Profiler**.</span></span>  
  
    -   <span data-ttu-id="17536-156">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서 **도구** 메뉴를 클릭한 다음 **SQL Server Profiler**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="17536-156">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], click the **Tools** menu, and then click **SQL Server Profiler**.</span></span>  
  
2.  <span data-ttu-id="17536-157">[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] **Tuning** 템플릿을 사용하는 다음 절차에 따라 추적 파일 또는 테이블을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="17536-157">Create a trace file or table as described in the following procedures that uses the [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] **Tuning** template:</span></span>  
  
    -   [<span data-ttu-id="17536-158">추적 만들기&#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="17536-158">Create a Trace &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/create-a-trace-sql-server-profiler.md)  
  
    -   [<span data-ttu-id="17536-159">추적 결과를 파일에 저장&#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="17536-159">Save Trace Results to a File &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/save-trace-results-to-a-file-sql-server-profiler.md)  
  
         <span data-ttu-id="17536-160">데이터베이스 엔진 튜닝 관리자에서는 작업 추적 파일이 롤오버 파일이라고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="17536-160">Database Engine Tuning Advisor assumes that the workload trace file is a rollover file.</span></span> <span data-ttu-id="17536-161">롤오버 파일에 대한 자세한 내용은 [Limit Trace File and Table Sizes](../sql-trace/limit-trace-file-and-table-sizes.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="17536-161">For more information about rollover files, see [Limit Trace File and Table Sizes](../sql-trace/limit-trace-file-and-table-sizes.md).</span></span>  
  
    -   [<span data-ttu-id="17536-162">테이블에 추적 결과 저장&#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="17536-162">Save Trace Results to a Table &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/save-trace-results-to-a-table-sql-server-profiler.md)  
  
         <span data-ttu-id="17536-163">추적 테이블을 작업 테이블로 사용하기 전에 추적이 중지되어 있는지 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="17536-163">Make sure that tracing has stopped before using a trace table as a workload.</span></span>  
  
 <span data-ttu-id="17536-164">SQL Server Profiler Tuning 템플릿을 사용하여 데이터베이스 엔진 튜닝 관리자의 작업을 캡처하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="17536-164">We recommend that you use the SQL Server Profiler Tuning template for capturing workloads for Database Engine Tuning Advisor.</span></span>  
  
 <span data-ttu-id="17536-165">사용자 고유의 템플릿을 사용하려면 다음 추적 이벤트가 캡처되는지 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="17536-165">If you want to use your own template, ensure that the following trace events are captured:</span></span>  
  
-   <span data-ttu-id="17536-166">**RPC:Completed**</span><span class="sxs-lookup"><span data-stu-id="17536-166">**RPC:Completed**</span></span>  
  
-   <span data-ttu-id="17536-167">**SQL:BatchCompleted**</span><span class="sxs-lookup"><span data-stu-id="17536-167">**SQL:BatchCompleted**</span></span>  
  
-   <span data-ttu-id="17536-168">**SP:StmtCompleted**</span><span class="sxs-lookup"><span data-stu-id="17536-168">**SP:StmtCompleted**</span></span>  
  
 <span data-ttu-id="17536-169">이러한 추적 이벤트의 **Starting** 버전을 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="17536-169">You can also use the **Starting** versions of these trace events.</span></span> <span data-ttu-id="17536-170">**SQL:BatchStarting**을 예로 들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="17536-170">For example, **SQL:BatchStarting**.</span></span> <span data-ttu-id="17536-171">한편 이러한 추적 이벤트의 **Completed** 버전에는 데이터베이스 엔진 튜닝 관리자의 작업 튜닝 효율을 높일 수 있도록 **Duration** 열이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="17536-171">However, the **Completed** versions of these trace events include the **Duration** column, which allows Database Engine Tuning Advisor to more effectively tune the workload.</span></span> <span data-ttu-id="17536-172">데이터베이스 엔진 튜닝 관리자는 다른 유형의 추적 이벤트는 튜닝하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="17536-172">Database Engine Tuning Advisor does not tune other types of trace events.</span></span> <span data-ttu-id="17536-173">이러한 추적 이벤트에 대한 자세한 내용은 [Stored Procedures Event Category](../event-classes/stored-procedures-event-category.md) 및 [TSQL Event Category](../event-classes/tsql-event-category.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="17536-173">For more information about these trace events, see [Stored Procedures Event Category](../event-classes/stored-procedures-event-category.md) and [TSQL Event Category](../event-classes/tsql-event-category.md).</span></span> <span data-ttu-id="17536-174">SQL 추적 저장 프로시저를 사용하여 추적 파일 작업을 만드는 방법은 [추적 만들기&#40;Transact-SQL&#41;](../sql-trace/create-a-trace-transact-sql.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="17536-174">For information about using the SQL Trace stored procedures to create a trace file workload, see [Create a Trace &#40;Transact-SQL&#41;](../sql-trace/create-a-trace-transact-sql.md).</span></span>  
  
### <a name="trace-file-or-trace-table-workloads-that-contain-the-loginname-data-column"></a><span data-ttu-id="17536-175">LoginName 데이터 열이 포함된 추적 파일 또는 추적 테이블 작업</span><span class="sxs-lookup"><span data-stu-id="17536-175">Trace File or Trace Table Workloads That Contain the LoginName Data Column</span></span>  
 <span data-ttu-id="17536-176">데이터베이스 엔진 튜닝 관리자는 튜닝 프로세스의 일부로 실행 계획 요청을 제출합니다.</span><span class="sxs-lookup"><span data-stu-id="17536-176">Database Engine Tuning Advisor submits Showplan requests as part of the tuning process.</span></span> <span data-ttu-id="17536-177">**LoginName** 데이터 열이 포함된 추적 테이블이나 파일이 작업으로 사용되면 데이터베이스 엔진 튜닝 관리자는 **LoginName**에 지정된 사용자를 가장합니다.</span><span class="sxs-lookup"><span data-stu-id="17536-177">When a trace table or file that contains the **LoginName** data column is consumed as a workload, Database Engine Tuning Advisor impersonates the user specified in **LoginName**.</span></span> <span data-ttu-id="17536-178">이 사용자에게 추적에 포함된 문의 실행 계획을 실행하고 생성할 수 있는 SHOWPLAN 권한이 없으면 데이터베이스 엔진 튜닝 관리자는 해당 문을 튜닝하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="17536-178">If this user has not been granted the SHOWPLAN permission, which enables the user to execute and produce Showplans for the statements contained in the trace, Database Engine Tuning Advisor will not tune those statements.</span></span>  
  
##### <a name="to-avoid-granting-the-showplan-permission-to-each-user-specified-in-the-loginname-column-of-the-trace"></a><span data-ttu-id="17536-179">추적의 LoginName 열에 지정된 각 사용자에게 SHOWPLAN 권한을 부여하지 않으려면</span><span class="sxs-lookup"><span data-stu-id="17536-179">To avoid granting the SHOWPLAN permission to each user specified in the LoginName column of the trace</span></span>  
  
1.  <span data-ttu-id="17536-180">추적 파일 또는 테이블 작업을 튜닝합니다.</span><span class="sxs-lookup"><span data-stu-id="17536-180">Tune the trace file or table workload.</span></span> <span data-ttu-id="17536-181">자세한 내용은 이 항목의 뒷부분에 나오는 [데이터베이스 튜닝](#Tune) 을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="17536-181">For more information, see [Tune a Database](#Tune) later in this topic.</span></span>  
  
2.  <span data-ttu-id="17536-182">튜닝 로그에서 부적절한 권한 때문에 튜닝되지 않은 문을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="17536-182">Check the tuning log for statements that were not tuned due to inadequate permissions.</span></span> <span data-ttu-id="17536-183">자세한 내용은 [데이터베이스 엔진 튜닝 관리자의 출력 보기 및 작업](database-engine-tuning-advisor.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="17536-183">For more information, see [View and Work with the Output from the Database Engine Tuning Advisor](database-engine-tuning-advisor.md).</span></span>  
  
3.  <span data-ttu-id="17536-184">튜닝되지 않은 이벤트에서 **LoginName** 열을 삭제하여 새 작업을 만든 다음 튜닝되지 않은 이벤트만 새 추적 파일이나 테이블에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="17536-184">Create a new workload by deleting the **LoginName** column from the events that were not tuned, and then save only the untuned events in a new trace file or table.</span></span> <span data-ttu-id="17536-185">추적에서 데이터 열을 삭제하는 방법은 [추적 파일에 대해 이벤트 및 데이터 열 지정&#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/specify-events-and-data-columns-for-a-trace-file-sql-server-profiler.md) 또는 [기존 추적 수정&#40;Transact-SQL&#41;](../sql-trace/modify-an-existing-trace-transact-sql.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="17536-185">For more information about deleting data columns from a trace, see [Specify Events and Data Columns for a Trace File &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/specify-events-and-data-columns-for-a-trace-file-sql-server-profiler.md) or [Modify an Existing Trace &#40;Transact-SQL&#41;](../sql-trace/modify-an-existing-trace-transact-sql.md).</span></span>  
  
4.  <span data-ttu-id="17536-186">**LoginName** 열이 없는 새 작업을 데이터베이스 엔진 튜닝 관리자에 다시 제출합니다.</span><span class="sxs-lookup"><span data-stu-id="17536-186">Resubmit the new workload without the **LoginName** column to Database Engine Tuning Advisor.</span></span>  
  
 <span data-ttu-id="17536-187">추적에 로그인 정보가 지정되어 있지 않으므로 데이터베이스 엔진 튜닝 관리자에서 새 작업을 튜닝합니다.</span><span class="sxs-lookup"><span data-stu-id="17536-187">Database Engine Tuning Advisor will tune the new workload because login information is not specified in the trace.</span></span> <span data-ttu-id="17536-188">문에 대한 **LoginName** 이 없으면 데이터베이스 엔진 튜닝 관리자는 튜닝 세션을 시작한 사용자( **sysadmin** 고정 서버 역할이나 **db_owner** 고정 데이터베이스 역할의 멤버)를 가장하여 해당 문을 튜닝합니다.</span><span class="sxs-lookup"><span data-stu-id="17536-188">If the **LoginName** does not exist for a statement, Database Engine Tuning Advisor tunes that statement by impersonating the user who started the tuning session (a member of either the **sysadmin** fixed server role or the **db_owner** fixed database role).</span></span>  
  
##  <a name="tune-a-database"></a><a name="Tune"></a> <span data-ttu-id="17536-189">데이터베이스 튜닝</span><span class="sxs-lookup"><span data-stu-id="17536-189">Tune a Database</span></span>  
 <span data-ttu-id="17536-190">데이터베이스를 튜닝하기 위해서는 데이터베이스 엔진 튜닝 관리자 GUI 또는 **dta** 명령줄 유틸리티를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="17536-190">To tune a database, you can use the Database Engine Tuning Advisor GUI or the **dta** utility.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="17536-191">추적 테이블을 데이터베이스 엔진 튜닝 관리자의 작업으로 사용하기 전에 추적이 중지되었는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="17536-191">Make sure that tracing has stopped before using a trace table as a workload for Database Engine Tuning Advisor.</span></span> <span data-ttu-id="17536-192">데이터베이스 엔진 튜닝 관리자에서는 추적 이벤트가 계속 작업으로 기록되는 추적 테이블을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="17536-192">Database Engine Tuning Advisor does not support using a trace table to which trace events are still being written as a workload.</span></span>  
  
### <a name="use-the-database-engine-tuning-advisor-graphical-user-interface"></a><span data-ttu-id="17536-193">데이터베이스 엔진 튜닝 관리자 그래픽 사용자 인터페이스 사용</span><span class="sxs-lookup"><span data-stu-id="17536-193">Use the Database Engine Tuning Advisor Graphical User Interface</span></span>  
 <span data-ttu-id="17536-194">데이터베이스 엔진 튜닝 관리자 GUI에서 계획 캐시, 작업 파일 또는 작업 테이블을 사용하여 데이터베이스를 튜닝할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="17536-194">On the Database Engine Tuning Advisor GUI, you can tune a database by using the plan cache, workload files, or workload tables.</span></span> <span data-ttu-id="17536-195">데이터베이스 엔진 튜닝 관리자 GUI를 사용하여 현재 튜닝 세션의 결과와 이전 튜닝 세션의 결과를 쉽게 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="17536-195">You can use the Database Engine Tuning Advisor GUI to easily view the results of your current tuning session and results of previous tuning sessions.</span></span> <span data-ttu-id="17536-196">사용자 인터페이스 옵션에 대한 자세한 내용은 이 항목의 뒷부분에 나오는 [사용자 인터페이스 설명](#UI) 을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="17536-196">For information about user interface options, see [User Interface Descriptions](#UI) later in this topic.</span></span> <span data-ttu-id="17536-197">데이터베이스 튜닝 후 출력 작업에 대한 자세한 내용은 [데이터베이스 엔진 튜닝 관리자의 출력 보기 및 작업](database-engine-tuning-advisor.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="17536-197">For more information about working with the output after you tune a database, see [View and Work with the Output from the Database Engine Tuning Advisor](database-engine-tuning-advisor.md).</span></span>  
  
####  <a name="to-tune-a-database-by-using-the-plan-cache"></a><a name="PlanCache"></a> <span data-ttu-id="17536-198">계획 캐시를 사용하여 데이터베이스를 튜닝하려면</span><span class="sxs-lookup"><span data-stu-id="17536-198">To tune a database by using the plan cache</span></span>  
  
1.  <span data-ttu-id="17536-199">데이터베이스 엔진 튜닝 관리자를 실행한 다음 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스에 로그인합니다.</span><span class="sxs-lookup"><span data-stu-id="17536-199">Launch Database Engine Tuning Advisor, and log into an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="17536-200">자세한 내용은 이 항목의 앞부분에 나오는 [데이터베이스 엔진 튜닝 관리자 시작](#Start) 을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="17536-200">For more information, see [Start the Database Engine Tuning Advisor](#Start) earlier in this topic.</span></span>  
  
2.  <span data-ttu-id="17536-201">**일반** 탭의 **세션 이름** 에 이름을 입력하여 새 튜닝 세션을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="17536-201">On the **General** tab, type a name in **Session name** to create a new tuning session.</span></span> <span data-ttu-id="17536-202">튜닝 세션을 시작하려면 먼저 **일반** 탭에서 필드를 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="17536-202">You must configure the fields in the **General** tab before starting a tuning session.</span></span> <span data-ttu-id="17536-203">튜닝 세션을 시작하기 전에 **튜닝 옵션** 탭의 설정을 수정할 필요는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="17536-203">It is not necessary to modify the settings of the **Tuning Options** tab before starting a tuning session.</span></span>  
  
3.  <span data-ttu-id="17536-204">**계획 캐시** 를 작업 옵션으로 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="17536-204">Select **Plan Cache** as the workload option.</span></span> <span data-ttu-id="17536-205">데이터베이스 엔진 튜닝 관리자가 계획 캐시에서 분석에 사용할 상위 1,000개의 이벤트를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="17536-205">Database Engine Tuning Advisor selects the top 1,000 events from the plan cache to use for analysis.</span></span>  
  
4.  <span data-ttu-id="17536-206">튜닝할 데이터베이스를 선택하고 필요에 따라 **선택한 테이블**의 각 데이터베이스에서 하나 이상의 테이블을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="17536-206">Select the database or databases that you want to tune, and optionally from **Selected Tables**, choose one or more tables from each database.</span></span> <span data-ttu-id="17536-207">모든 데이터베이스에 대한 캐시 항목을 포함하려면 **튜닝 옵션**에서 **고급 옵션** 을 클릭한 다음 **모든 데이터베이스의 계획 캐시 이벤트 포함**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="17536-207">To include cache entries for all databases, from **Tuning Options**, click **Advanced Options** and then check **Include plan cache events from all databases**.</span></span>  
  
5.  <span data-ttu-id="17536-208">**튜닝 로그 저장** 을 선택하여 튜닝 로그 복사본을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="17536-208">Check **Save tuning log** to save a copy of the tuning log.</span></span> <span data-ttu-id="17536-209">튜닝 로그 복사본을 저장하지 않으려면 이 확인란의 선택을 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="17536-209">Clear the check box if you do not want to save a copy of the tuning log.</span></span>  
  
     <span data-ttu-id="17536-210">세션을 열고 **진행률** 탭을 선택하여 분석한 후의 튜닝 로그를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="17536-210">You can view the tuning log after analysis by opening the session and selecting the **Progress** tab.</span></span>  
  
6.  <span data-ttu-id="17536-211">**튜닝 옵션** 탭을 클릭한 다음 나열된 옵션 중에서 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="17536-211">Click the **Tuning Options** tab and select from the options listed there.</span></span>  
  
7.  <span data-ttu-id="17536-212">**분석 시작**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="17536-212">Click **Start Analysis**.</span></span>  
  
     <span data-ttu-id="17536-213">튜닝 세션이 시작된 후에 이를 중지하려면 **동작** 메뉴에서 다음 옵션 중 하나를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="17536-213">If you want to stop the tuning session after it has started, choose one of the following options on the **Actions** menu:</span></span>  
  
    -   <span data-ttu-id="17536-214">**분석 중지(권장 구성)** 는 튜닝 세션을 중지하고 데이터베이스 엔진 튜닝 관리자에서 중지 전 시점까지 수행된 분석을 기반하여 권장 구성을 생성할지 여부를 묻는 메시지를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="17536-214">**Stop Analysis (With Recommendations)** stops the tuning session and prompts you to decide whether you want Database Engine Tuning Advisor to generate recommendations based on the analysis done up to this point.</span></span>  
  
    -   <span data-ttu-id="17536-215">**분석 중지** 는 권장 구성을 생성하지 않고 튜닝 세션을 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="17536-215">**Stop Analysis** stops the tuning session without generating any recommendations.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="17536-216">데이터베이스 엔진 튜닝 관리자의 일시 중지 기능은 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="17536-216">Pausing Database Engine Tuning Advisor is not supported.</span></span> <span data-ttu-id="17536-217">**분석 중지** 또는 **분석 중지(권장 구성)** 도구 모음 단추를 클릭한 후 **분석 시작** 도구 모음 단추를 클릭하면 데이터베이스 엔진 튜닝 관리자가 새 튜닝 세션을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="17536-217">If you click the **Start Analysis** toolbar button after clicking either the **Stop Analysis** or **Stop Analysis (With Recommendations)** toolbar buttons, Database Engine Tuning Advisor starts a new tuning session.</span></span>  
  
##### <a name="to-tune-a-database-using-a-workload-file-or-table-as-input"></a><span data-ttu-id="17536-218">작업 파일이나 테이블을 입력으로 사용하여 데이터베이스를 튜닝하려면</span><span class="sxs-lookup"><span data-stu-id="17536-218">To tune a database using a workload file or table as input</span></span>  
  
1.  <span data-ttu-id="17536-219">데이터베이스 엔진 튜닝 관리자가 분석 중에 추가, 제거 또는 유지해야 할 데이터베이스 기능(인덱스, 인덱싱된 뷰, 분할)을 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="17536-219">Determine the database features (indexes, indexed views, partitioning) you want Database Engine Tuning Advisor to consider adding, removing, or retaining during analysis.</span></span>  
  
2.  <span data-ttu-id="17536-220">작업을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="17536-220">Create a workload.</span></span> <span data-ttu-id="17536-221">자세한 내용은 이 항목의 앞부분에 나오는 [작업 만들기](#Create) 를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="17536-221">For more information, see [Create a Workload](#Create) earlier in this topic.</span></span>  
  
3.  <span data-ttu-id="17536-222">데이터베이스 엔진 튜닝 관리자를 실행한 다음 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에 로그인합니다.</span><span class="sxs-lookup"><span data-stu-id="17536-222">Launch Database Engine Tuning Advisor, and log into an instance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="17536-223">자세한 내용은 이 항목의 앞부분에 나오는 [데이터베이스 엔진 튜닝 관리자 시작](#Start) 을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="17536-223">For more information, see [Start the Database Engine Tuning Advisor](#Start) earlier in this topic.</span></span>  
  
4.  <span data-ttu-id="17536-224">**일반** 탭의 **세션 이름** 에 이름을 입력하여 새 튜닝 세션을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="17536-224">On the **General** tab, type a name in **Session name** to create a new tuning session.</span></span>  
  
5.  <span data-ttu-id="17536-225">**작업 파일** 또는 **테이블** 을 선택하고 파일 경로 또는 인접한 입력란에 테이블 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="17536-225">Choose either a **Workload File** or **Table** and type either the path to the file, or the name of the table in the adjacent text box.</span></span>  
  
     <span data-ttu-id="17536-226">테이블을 지정하는 형식</span><span class="sxs-lookup"><span data-stu-id="17536-226">The format for specifying a table is</span></span>  
  
    ```  
  
    database_name.schema_name.table_name  
    ```  
  
     <span data-ttu-id="17536-227">작업 파일이나 테이블을 검색하려면 **찾아보기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="17536-227">To search for a workload file or table, click **Browse**.</span></span> <span data-ttu-id="17536-228">데이터베이스 엔진 튜닝 관리자는 작업 파일을 롤오버 파일로 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="17536-228">Database Engine Tuning Advisor assumes that workload files are rollover files.</span></span> <span data-ttu-id="17536-229">롤오버 파일에 대한 자세한 내용은 [Limit Trace File and Table Sizes](../sql-trace/limit-trace-file-and-table-sizes.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="17536-229">For more information about rollover files, see [Limit Trace File and Table Sizes](../sql-trace/limit-trace-file-and-table-sizes.md).</span></span>  
  
     <span data-ttu-id="17536-230">추적 테이블을 작업으로 사용하는 경우 데이터베이스 엔진 튜닝 관리자가 튜닝 중인 서버와 같은 서버에 해당 테이블이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="17536-230">When using a trace table as a workload, that table must exist on the same server that Database Engine Tuning Advisor is tuning.</span></span> <span data-ttu-id="17536-231">다른 서버에 추적 테이블을 만든 경우에는 이 테이블을 데이터베이스 엔진 튜닝 관리자가 튜닝하는 서버로 이동한 다음 작업으로 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="17536-231">If you create the trace table on a different server, move it to the server that Database Engine Tuning Advisor is tuning before using it as your workload.</span></span>  
  
6.  <span data-ttu-id="17536-232">5단계에서 선택한 작업을 실행할 데이터베이스 및 테이블을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="17536-232">Select the databases and tables against which you wish to run the workload that you selected in step 5.</span></span> <span data-ttu-id="17536-233">테이블을 선택하려면 **선택한 테이블** 화살표를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="17536-233">To select the tables, click the **Selected Tables** arrow.</span></span>  
  
7.  <span data-ttu-id="17536-234">**튜닝 로그 저장** 을 선택하여 튜닝 로그 복사본을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="17536-234">Check **Save tuning log** to save a copy of the tuning log.</span></span> <span data-ttu-id="17536-235">튜닝 로그 복사본을 저장하지 않으려면 이 확인란의 선택을 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="17536-235">Clear the check box if you do not want to save a copy of the tuning log.</span></span>  
  
     <span data-ttu-id="17536-236">세션을 열고 **진행률** 탭을 선택하여 분석한 후의 튜닝 로그를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="17536-236">You can view the tuning log after analysis by opening the session and selecting the **Progress** tab.</span></span>  
  
8.  <span data-ttu-id="17536-237">**튜닝 옵션** 탭을 클릭한 다음 나열된 옵션 중에서 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="17536-237">Click the **Tuning Options** tab and select from the options listed there.</span></span>  
  
9. <span data-ttu-id="17536-238">도구 모음에서 **분석 시작** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="17536-238">Click the **Start Analysis** button in the toolbar.</span></span>  
  
     <span data-ttu-id="17536-239">튜닝 세션이 시작된 후에 이를 중지하려면 **동작** 메뉴에서 다음 옵션 중 하나를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="17536-239">If you want to stop the tuning session after it has started, choose one of the following options on the **Actions** menu:</span></span>  
  
    -   <span data-ttu-id="17536-240">**분석 중지(권장 구성)** 는 튜닝 세션을 중지하고 데이터베이스 엔진 튜닝 관리자에서 중지 전 시점까지 수행된 분석을 기반하여 권장 구성을 생성할지 여부를 묻는 메시지를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="17536-240">**Stop Analysis (With Recommendations)** stops the tuning session and prompts you to decide whether you want Database Engine Tuning Advisor to generate recommendations based on the analysis done up to this point.</span></span>  
  
    -   <span data-ttu-id="17536-241">**분석 중지** 는 권장 구성을 생성하지 않고 튜닝 세션을 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="17536-241">**Stop Analysis** stops the tuning session without generating any recommendations.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="17536-242">데이터베이스 엔진 튜닝 관리자의 일시 중지 기능은 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="17536-242">Pausing Database Engine Tuning Advisor is not supported.</span></span> <span data-ttu-id="17536-243">**분석 중지** 또는 **분석 중지(권장 구성)** 도구 모음 단추를 클릭한 후 **분석 시작** 도구 모음 단추를 클릭하면 데이터베이스 엔진 튜닝 관리자가 새 튜닝 세션을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="17536-243">If you click the **Start Analysis** toolbar button after clicking either the **Stop Analysis** or **Stop Analysis (With Recommendations)** toolbar buttons, Database Engine Tuning Advisor starts a new tuning session.</span></span>  
  
###  <a name="use-the-dta-utility"></a><a name="dta"></a> <span data-ttu-id="17536-244">dta 유틸리티 사용</span><span class="sxs-lookup"><span data-stu-id="17536-244">Use the dta Utility</span></span>  
 <span data-ttu-id="17536-245">[dta 유틸리티](../../tools/dta/dta-utility.md) 는 데이터베이스를 튜닝하기 위해 사용할 수 있는 명령 프롬프트 실행 파일을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="17536-245">The [dta utility](../../tools/dta/dta-utility.md) provides a command prompt executable file that you can use to tune databases.</span></span> <span data-ttu-id="17536-246">이 유틸리티를 사용하면 일괄 처리 파일이나 스크립트에 데이터베이스 엔진 튜닝 관리자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="17536-246">It enables you to use Database Engine Tuning Advisor functionality in batch files and scripts.</span></span> <span data-ttu-id="17536-247">**dta** 유틸리티는 계획 캐시 항목, 추적 파일, 추적 테이블 및 [!INCLUDE[tsql](../../includes/tsql-md.md)] 스크립트를 작업으로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="17536-247">The **dta** utility takes plan cache entries, trace files, trace tables, and [!INCLUDE[tsql](../../includes/tsql-md.md)] scripts as workloads.</span></span> <span data-ttu-id="17536-248">또한 다음 [Microsoft 웹 사이트](https://go.microsoft.com/fwlink/?linkid=43100)에서 사용 가능한 데이터베이스 엔진 튜닝 관리자 XML 스키마를 따르는 XML 입력을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="17536-248">It also takes XML input that conforms to the Database Engine Tuning Advisor XML schema, which is available at this [Microsoft Web site](https://go.microsoft.com/fwlink/?linkid=43100).</span></span>  
  
 <span data-ttu-id="17536-249">**dta** 유틸리티에서 작업을 튜닝하기 전에 다음 사항을 고려하세요.</span><span class="sxs-lookup"><span data-stu-id="17536-249">Consider the following before you begin tuning a workload with the **dta** utility:</span></span>  
  
-   <span data-ttu-id="17536-250">추적 테이블을 작업으로 사용하는 경우 데이터베이스 엔진 튜닝 관리자가 튜닝 중인 서버와 같은 서버에 해당 테이블이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="17536-250">When using a trace table as a workload, that table must exist on the same server that Database Engine Tuning Advisor is tuning.</span></span> <span data-ttu-id="17536-251">다른 서버에 추적 테이블을 만든 경우에는 이 테이블을 데이터베이스 엔진 튜닝 관리자가 튜닝하는 서버로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="17536-251">If you create the trace table on a different server, then move it to the server that Database Engine Tuning Advisor is tuning.</span></span>  
  
-   <span data-ttu-id="17536-252">추적 테이블을 데이터베이스 엔진 튜닝 관리자의 작업으로 사용하기 전에 추적이 중지되었는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="17536-252">Make sure that tracing has stopped before using a trace table as a workload for Database Engine Tuning Advisor.</span></span> <span data-ttu-id="17536-253">데이터베이스 엔진 튜닝 관리자에서는 추적 이벤트가 계속 작업으로 기록되는 추적 테이블을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="17536-253">Database Engine Tuning Advisor does not support using a trace table to which trace events are still being written as a workload.</span></span>  
  
-   <span data-ttu-id="17536-254">튜닝 세션이 예상보다 오랜 시간 계속 실행되는 경우 Ctrl+C를 눌러 튜닝 세션을 중지하고 **dta** 에서 현재까지 완료한 분석에 따라 권장 사항을 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="17536-254">If a tuning session continues running longer than you had anticipated it would run, you can press CTRL+C to stop the tuning session and generate recommendations based on the analysis **dta** has completed up to this point.</span></span> <span data-ttu-id="17536-255">권장 구성을 생성할지 여부를 결정하라는 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="17536-255">You will be prompted to decide whether you want to generate recommendations or not.</span></span> <span data-ttu-id="17536-256">Ctrl+C를 다시 누르면 권장 구성을 생성하지 않고 튜닝 세션이 중지됩니다.</span><span class="sxs-lookup"><span data-stu-id="17536-256">Press CTRL+C again to stop the tuning session without generating recommendations.</span></span>  
  
 <span data-ttu-id="17536-257">**dta** 유틸리티 구문에 대한 자세한 내용 및 예제는 [dta Utility](../../tools/dta/dta-utility.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="17536-257">For more information about **dta** utility syntax and examples, see [dta Utility](../../tools/dta/dta-utility.md).</span></span>  
  
##### <a name="to-tune-a-database-by-using-the-plan-cache"></a><span data-ttu-id="17536-258">계획 캐시를 사용하여 데이터베이스를 튜닝하려면</span><span class="sxs-lookup"><span data-stu-id="17536-258">To tune a database by using the plan cache</span></span>  
  
1.  <span data-ttu-id="17536-259">**-ip** 옵션을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="17536-259">Specify the **-ip** option.</span></span> <span data-ttu-id="17536-260">선택한 데이터베이스에 대한 상위 1,000개의 계획 캐시 이벤트가 분석됩니다.</span><span class="sxs-lookup"><span data-stu-id="17536-260">The top 1,000 plan cache events for the selected databases are analyzed.</span></span>  
  
     <span data-ttu-id="17536-261">명령 프롬프트에서 다음을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="17536-261">From a command prompt, enter the following:</span></span>  
  
    ```  
    dta -E -D DatabaseName -ip -s SessionName  
    ```  
  
2.  <span data-ttu-id="17536-262">분석에 사용할 이벤트 수를 수정하려면 **–n** 옵션을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="17536-262">To modify the number of events to use for analysis, specify the **-n** option.</span></span> <span data-ttu-id="17536-263">다음 예에서는 캐시 항목 수를 2,000개로 증가시킵니다.</span><span class="sxs-lookup"><span data-stu-id="17536-263">The following example increases the number of cache entries to 2,000.</span></span>  
  
    ```  
    dta -E -D DatabaseName -ip -n 2000-s SessionName1  
    ```  
  
3.  <span data-ttu-id="17536-264">인스턴스에 있는 모든 데이터베이스의 이벤트를 분석하려면 **-ipf** 옵션을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="17536-264">To analyze events for all databases in the instance, specify the **-ipf** option.</span></span>  
  
    ```  
    dta -E -D DatabaseName -ip -ipf -n 2000 -s SessionName2  
    ```  
  
##### <a name="to-tune-a-database-by-using-a-workload-and-dta-utility-default-settings"></a><span data-ttu-id="17536-265">작업 및 dta 유틸리티 기본 설정을 사용하여 데이터베이스를 튜닝하려면</span><span class="sxs-lookup"><span data-stu-id="17536-265">To tune a database by using a workload and dta utility default settings</span></span>  
  
1.  <span data-ttu-id="17536-266">데이터베이스 엔진 튜닝 관리자가 분석 중에 추가, 제거 또는 유지해야 할 데이터베이스 기능(인덱스, 인덱싱된 뷰, 분할)을 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="17536-266">Determine the database features (indexes, indexed views, partitioning) you want Database Engine Tuning Advisor to consider adding, removing, or retaining during analysis.</span></span>  
  
2.  <span data-ttu-id="17536-267">작업을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="17536-267">Create a workload.</span></span> <span data-ttu-id="17536-268">자세한 내용은 이 항목의 앞부분에 나오는 [작업 만들기](#Create) 를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="17536-268">For more information, see [Create a Workload](#Create) earlier in this topic.</span></span>  
  
3.  <span data-ttu-id="17536-269">명령 프롬프트에서 다음을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="17536-269">From a command prompt, enter the following:</span></span>  
  
    ```  
    dta -E -D DatabaseName -if WorkloadFile -s SessionName  
    ```  
  
     <span data-ttu-id="17536-270">여기에서 `-E` 는 튜닝 세션이 로그인 ID와 암호 대신에 트러스트된 연결을 사용하도록 지정하고 `-D` 는 튜닝할 데이터베이스의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="17536-270">where `-E` specifies that your tuning session uses a trusted connection (instead of a login ID and password), `-D` specifies the name of the database you want to tune.</span></span> <span data-ttu-id="17536-271">기본적으로 이 유틸리티는 로컬 컴퓨터에 있는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 의 기본 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="17536-271">By default, the utility connects to the default instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on the local computer.</span></span> <span data-ttu-id="17536-272">다음 절차에 표시된 대로 원격 데이터베이스를 지정하거나 명명된 인스턴스를 지정하려면 `-S` 옵션을 사용합니다. `-if` 옵션은 작업 파일( [!INCLUDE[tsql](../../includes/tsql-md.md)] 스크립트 또는 추적 파일)의 이름과 경로를 지정하고 `-s` 옵션은 튜닝 세션의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="17536-272">(Use the `-S` option to specify a remote database as shown in the following procedure, or to specify a named instance.) The `-if` option specifies the name and path to a workload file (which can be a [!INCLUDE[tsql](../../includes/tsql-md.md)] script or a trace file), and `-s` specifies a name for your tuning session.</span></span>  
  
     <span data-ttu-id="17536-273">여기에 표시된 네 가지 옵션(데이터베이스 이름, 작업, 연결 유형, 세션 이름)은 필수 항목입니다.</span><span class="sxs-lookup"><span data-stu-id="17536-273">The four options shown here (database name, workload, connection type, and session name) are mandatory.</span></span>  
  
##### <a name="to-tune-a-remote-database-or-a-named-instance-for-a-specific-duration"></a><span data-ttu-id="17536-274">원격 데이터베이스 또는 특정 기간 동안 명명된 인스턴스를 튜닝하려면</span><span class="sxs-lookup"><span data-stu-id="17536-274">To tune a remote database or a named instance for a specific duration</span></span>  
  
1.  <span data-ttu-id="17536-275">데이터베이스 엔진 튜닝 관리자가 분석 중에 추가, 제거 또는 유지해야 할 데이터베이스 기능(인덱스, 인덱싱된 뷰, 분할)을 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="17536-275">Determine the database features (indexes, indexed views, partitioning) you want Database Engine Tuning Advisor to consider adding, removing, or retaining during analysis.</span></span>  
  
2.  <span data-ttu-id="17536-276">작업을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="17536-276">Create a workload.</span></span> <span data-ttu-id="17536-277">자세한 내용은 이 항목의 앞부분에 나오는 [작업 만들기](#Create) 를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="17536-277">For more information, see [Create a Workload](#Create) earlier in this topic.</span></span>  
  
3.  <span data-ttu-id="17536-278">명령 프롬프트에서 다음을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="17536-278">From a command prompt, enter the following:</span></span>  
  
    ```  
    dta -S ServerName\Instance -D DatabaseName -it WorkloadTableName   
    -U LoginID -P Password -s SessionName -A TuningTimeInMinutes  
    ```  
  
     <span data-ttu-id="17536-279">여기에서 `-S` 는 원격 서버 이름과 인스턴스(또는 로컬 서버에서 명명된 인스턴스)를 지정하고 `-D` 는 튜닝할 데이터베이스의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="17536-279">where `-S` specifies a remote server name and instance (or a named instance on the local server) and `-D` specifies the name of the database you want to tune.</span></span> <span data-ttu-id="17536-280">`-it` 옵션은 작업 테이블의 이름을 지정하고, `-U` 및 `-P` 는 원격 데이터베이스에 대한 로그인 ID와 암호를 지정하고, `-s` 는 튜닝 세션 이름을 지정하고, `-A` 는 튜닝 세션 기간(단위 분)을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="17536-280">The `-it` option specifies the name of the workload table, `-U` and `-P` specify the login ID and password to the remote database, `-s` specifies the tuning session name, and `-A` specifies the tuning session duration in minutes.</span></span> <span data-ttu-id="17536-281">기본적으로 **dta** 유틸리티는 8시간 튜닝 기간을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="17536-281">By default, the **dta** utility uses an 8-hour tuning duration.</span></span> <span data-ttu-id="17536-282">데이터베이스 엔진 튜닝 관리자가 시간 제한 없이 작업을 튜닝하도록 하려면 **옵션에** 0 `-A` (영)을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="17536-282">If you would like Database Engine Tuning Advisor to tune a workload for an unlimited amount of time, specify **0** (zero) with the `-A` option.</span></span>  
  
##### <a name="to-tune-a-database-using-an-xml-input-file"></a><span data-ttu-id="17536-283">XML 입력 파일로 데이터베이스를 튜닝하려면</span><span class="sxs-lookup"><span data-stu-id="17536-283">To tune a database using an XML input file</span></span>  
  
1.  <span data-ttu-id="17536-284">데이터베이스 엔진 튜닝 관리자가 분석 중에 추가, 제거 또는 유지해야 할 데이터베이스 기능(인덱스, 인덱싱된 뷰, 분할)을 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="17536-284">Determine the database features (indexes, indexed views, partitioning) you want Database Engine Tuning Advisor to consider adding, removing, or retaining during analysis.</span></span>  
  
2.  <span data-ttu-id="17536-285">작업을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="17536-285">Create a workload.</span></span> <span data-ttu-id="17536-286">자세한 내용은 이 항목의 앞부분에 나오는 [작업 만들기](#Create) 를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="17536-286">For more information, see [Create a Workload](#Create) earlier in this topic.</span></span>  
  
3.  <span data-ttu-id="17536-287">XML 입력 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="17536-287">Create an XML input file.</span></span> <span data-ttu-id="17536-288">자세한 내용은 이 항목의 뒷부분에 나오는 [XML 입력 파일 만들기](#XMLInput) 를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="17536-288">For more information, see [Create XML Input Files](#XMLInput) later in this topic.</span></span>  
  
4.  <span data-ttu-id="17536-289">명령 프롬프트에서 다음을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="17536-289">From a command prompt, enter the following:</span></span>  
  
    ```  
    dta -E -S ServerName\Instance -s SessionName -ix PathToXMLInputFile  
    ```  
  
     <span data-ttu-id="17536-290">여기에서 `-E` 는 트러스트된 연결을 지정하고, `-S` 는 원격 서버와 인스턴스 또는 로컬 서버에서 명명된 인스턴스를 지정하고, `-s` 는 튜닝 세션 이름을 지정하고, `-ix` 는 튜닝 세션에 사용할 XML 입력 파일을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="17536-290">where `-E` specifies a trusted connection, `-S` specifies a remote server and instance, or a named instance on the local server, `-s` specifies a tuning session name, and `-ix` specifies the XML input file to use for the tuning session.</span></span>  
  
5.  <span data-ttu-id="17536-291">유틸리티가 작업 튜닝을 마친 후에는 데이터베이스 엔진 튜닝 관리자 GUI를 사용하여 튜닝 세션의 결과를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="17536-291">After the utility finishes tuning the workload, you can view the results of tuning sessions with the Database Engine Tuning Advisor GUI.</span></span> <span data-ttu-id="17536-292">다른 방법으로 **-ox** 옵션을 사용하여 튜닝 권장 구성이 XML 파일에 기록되도록 지정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="17536-292">As an alternative, you can also specify that the tuning recommendations be written to an XML file with the **-ox** option.</span></span> <span data-ttu-id="17536-293">자세한 내용은 [dta Utility](../../tools/dta/dta-utility.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="17536-293">For more information, see [dta Utility](../../tools/dta/dta-utility.md).</span></span>  
  
##  <a name="create-an-xml-input-file"></a><a name="XMLInput"></a> <span data-ttu-id="17536-294">XML 입력 파일 만들기</span><span class="sxs-lookup"><span data-stu-id="17536-294">Create an XML Input File</span></span>  
 <span data-ttu-id="17536-295">숙련된 XML 개발자인 경우 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 튜닝 관리자에서 작업을 튜닝할 때 사용하는 XML 형식의 파일을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="17536-295">If you are an experienced XML developer, you can create XML-formatted files that [!INCLUDE[ssDE](../../includes/ssde-md.md)] Tuning Advisor can use to tune workloads.</span></span> <span data-ttu-id="17536-296">이러한 XML 파일을 만들려면 선호하는 XML 도구를 사용하여 예제 파일을 편집하거나 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 튜닝 관리자 XML 스키마에서 인스턴스를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="17536-296">To create these XML files, use your favorite XML tools to edit a sample file or to generate an instance from the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Tuning Advisor XML schema.</span></span>  
  
 <span data-ttu-id="17536-297">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 튜닝 관리자 XML 스키마는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 설치의 다음 위치에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="17536-297">The [!INCLUDE[ssDE](../../includes/ssde-md.md)] Tuning Advisor XML schema is available in your [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installation in the following location:</span></span>  
  
 <span data-ttu-id="17536-298">C:\Program Files\Microsoft SQL Server\100\Tools\Binn\schemas\sqlserver\2004\07\dta\dtaschema.xsd</span><span class="sxs-lookup"><span data-stu-id="17536-298">C:\Program Files\Microsoft SQL Server\100\Tools\Binn\schemas\sqlserver\2004\07\dta\dtaschema.xsd</span></span>  
  
 <span data-ttu-id="17536-299">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 튜닝 관리자 XML 스키마는 [Microsoft 웹 사이트](https://go.microsoft.com/fwlink/?linkid=43100&clcid=0x409)에서 온라인으로도 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="17536-299">The [!INCLUDE[ssDE](../../includes/ssde-md.md)] Tuning Advisor XML schema is also available online at this [Microsoft Web site](https://go.microsoft.com/fwlink/?linkid=43100&clcid=0x409).</span></span>  
  
 <span data-ttu-id="17536-300">이 페이지에서는 많은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] XML 스키마를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="17536-300">This URL takes you to a page where many [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] XML schemas are available.</span></span> <span data-ttu-id="17536-301">페이지 아래로 스크롤하여 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 튜닝 관리자 행을 찾으세요.</span><span class="sxs-lookup"><span data-stu-id="17536-301">Scroll down the page until you reach the row for [!INCLUDE[ssDE](../../includes/ssde-md.md)] Tuning Advisor.</span></span>  
  
#### <a name="to-create-an-xml-input-file-to-tune-workloads"></a><span data-ttu-id="17536-302">작업을 튜닝할 XML 입력 파일을 만들려면</span><span class="sxs-lookup"><span data-stu-id="17536-302">To create an XML input file to tune workloads</span></span>  
  
1.  <span data-ttu-id="17536-303">작업을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="17536-303">Create a workload.</span></span> <span data-ttu-id="17536-304">[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]의 튜닝 템플릿으로 추적 파일 또는 테이블을 사용하거나 [!INCLUDE[tsql](../../includes/tsql-md.md)] 스크립트를 만들어 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 대표적인 작업을 재현할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="17536-304">You can use a trace file or table by using the tuning template in [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)], or create a [!INCLUDE[tsql](../../includes/tsql-md.md)] script that reproduces a representative workload for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="17536-305">자세한 내용은 이 항목의 앞부분에 나오는 [작업 만들기](#Create) 를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="17536-305">For more information, see [Create a Workload](#Create) earlier in this topic.</span></span>  
  
2.  <span data-ttu-id="17536-306">다음 중 한 가지 방법으로 XML 입력 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="17536-306">Create an XML input file by one of the following methods:</span></span>  
  
    -   <span data-ttu-id="17536-307">[XML 입력 파일 샘플&#40;DTA&#41;](../../tools/dta/xml-input-file-samples-dta.md) 중 하나를 복사하여 선호하는 XML 편집기에 붙여넣습니다.</span><span class="sxs-lookup"><span data-stu-id="17536-307">Copy and paste one of the [XML Input File Samples &#40;DTA&#41;](../../tools/dta/xml-input-file-samples-dta.md) into your favorite XML editor.</span></span> <span data-ttu-id="17536-308">값을 변경하여 사용자의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 설치에 적절한 인수를 지정한 다음 XML 파일을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="17536-308">Change the values to specify the appropriate arguments for your [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installation, and save the XML file.</span></span>  
  
    -   <span data-ttu-id="17536-309">선호하는 XML 도구를 사용하여 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 튜닝 관리자 XML 스키마에서 인스턴스를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="17536-309">Using your favorite XML tool, generate an instance from the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Tuning Advisor XML schema.</span></span>  
  
3.  <span data-ttu-id="17536-310">만든 XML 입력 파일을 **dta** 명령줄 유틸리티의 입력으로 사용하여 작업을 튜닝합니다.</span><span class="sxs-lookup"><span data-stu-id="17536-310">After creating the XML input file, use it as input to the **dta** command-line utility to tune the workload.</span></span> <span data-ttu-id="17536-311">이 유틸리티에서 XML 입력 파일을 사용하는 방법은 이 항목의 앞부분에 나오는 [dta 유틸리티 사용](#dta) 섹션을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="17536-311">For information about using XML input files with this utility, see the section [Use the dta Utililty](#dta) earlier in this topic.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="17536-312">XML 입력 파일에 직접 지정되는 작업인 인라인 작업을 사용하려면 [인라인 작업이 포함된 XML 입력 파일 예제&#40;DTA&#41;](../../tools/dta/xml-input-file-sample-with-inline-workload-dta.md) 샘플을 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="17536-312">If you want to use an inline workload, which is a workload that is specified directly in the XML input file, use the sample [XML Input File Sample with Inline Workload &#40;DTA&#41;](../../tools/dta/xml-input-file-sample-with-inline-workload-dta.md).</span></span>  
  
##  <a name="user-interface-descriptions"></a><a name="UI"></a> <span data-ttu-id="17536-313">사용자 인터페이스 설명</span><span class="sxs-lookup"><span data-stu-id="17536-313">User Interface Descriptions</span></span>  
  
### <a name="tools-menuoptions-page"></a><span data-ttu-id="17536-314">도구 메뉴/옵션 페이지</span><span class="sxs-lookup"><span data-stu-id="17536-314">Tools Menu/Options Page</span></span>  
 <span data-ttu-id="17536-315">이 대화 상자를 사용하여 데이터베이스 엔진 튜닝 관리자에 대한 일반 구성 매개 변수를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="17536-315">Use this dialog box to specify general configuration parameters for the Database Engine Tuning Advisor.</span></span>  
  
 <span data-ttu-id="17536-316">**시작 시**</span><span class="sxs-lookup"><span data-stu-id="17536-316">**On startup**</span></span>  
 <span data-ttu-id="17536-317">데이터베이스 엔진 튜닝 관리자 시작 시 수행할 작업을 데이터베이스 연결 없이 열기, **새 연결** 대화 상자 표시, 새 세션 표시 또는 마지막으로 로드된 세션 로드 중에서 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="17536-317">Specify what Database Engine Tuning Advisor should do when it is started: open without a database connection, show a **New Connection** dialog box, show a new session, or load the last loaded session.</span></span>  
  
 <span data-ttu-id="17536-318">**글꼴 변경**</span><span class="sxs-lookup"><span data-stu-id="17536-318">**Change font**</span></span>  
 <span data-ttu-id="17536-319">데이터베이스 엔진 튜닝 관리자 테이블에 사용되는 글꼴을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="17536-319">Specify the display font used by Database Engine Tuning Advisor tables.</span></span>  
  
 <span data-ttu-id="17536-320">**가장 최근에 사용한 목록의 항목 수**</span><span class="sxs-lookup"><span data-stu-id="17536-320">**Number of items in most recently used lists**</span></span>  
 <span data-ttu-id="17536-321">**파일** 메뉴의 **최근에 사용한 세션** 또는 **최근에 사용한 파일** 에 표시될 세션 또는 파일의 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="17536-321">Specify the number of sessions or files to display under **Recent Sessions** or **Recent Files** in the **File** menu.</span></span>  
  
 <span data-ttu-id="17536-322">**마지막 튜닝 옵션 저장**</span><span class="sxs-lookup"><span data-stu-id="17536-322">**Remember my last tuning options**</span></span>  
 <span data-ttu-id="17536-323">여러 세션에서 튜닝 옵션을 유지합니다.</span><span class="sxs-lookup"><span data-stu-id="17536-323">Retain tuning options between sessions.</span></span> <span data-ttu-id="17536-324">기본적으로 선택되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="17536-324">Selected by default.</span></span> <span data-ttu-id="17536-325">항상 데이터베이스 엔진 튜닝 관리자 기본값으로 시작하려면 이 확인란의 선택을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="17536-325">Clear this check box to always start with the Database Engine Tuning Advisor defaults.</span></span>  
  
 <span data-ttu-id="17536-326">**세션을 영구적으로 삭제하기 전에 확인**</span><span class="sxs-lookup"><span data-stu-id="17536-326">**Ask before permanently deleting sessions**</span></span>  
 <span data-ttu-id="17536-327">세션을 삭제하기 전에 확인 대화 상자를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="17536-327">Display a confirmation dialog box before deleting sessions.</span></span>  
  
 <span data-ttu-id="17536-328">**세션 분석을 중지하기 전에 확인**</span><span class="sxs-lookup"><span data-stu-id="17536-328">**Ask before stopping session analysis**</span></span>  
 <span data-ttu-id="17536-329">작업 분석을 중지하기 전에 확인 대화 상자를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="17536-329">Display a confirmation dialog box before stopping analysis of a workload.</span></span>  
  
#### <a name="general-tab-options"></a><span data-ttu-id="17536-330">일반 탭 옵션</span><span class="sxs-lookup"><span data-stu-id="17536-330">General Tab Options</span></span>  
 <span data-ttu-id="17536-331">튜닝 세션을 시작하려면 먼저 **일반** 탭에서 필드를 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="17536-331">You must configure the fields in the **General** tab before starting a tuning session.</span></span> <span data-ttu-id="17536-332">튜닝 세션을 시작하기 전에 **튜닝 옵션** 탭의 설정을 수정할 필요는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="17536-332">You do not have to modify the settings of the **Tuning Options** tab before starting a tuning session.</span></span>  
  
 <span data-ttu-id="17536-333">**세션 이름**</span><span class="sxs-lookup"><span data-stu-id="17536-333">**Session name**</span></span>  
 <span data-ttu-id="17536-334">세션의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="17536-334">Specify a name for the session.</span></span> <span data-ttu-id="17536-335">세션 이름 옵션은 세션의 이름을 튜닝 세션과 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="17536-335">The session name associates a name with a tuning session.</span></span> <span data-ttu-id="17536-336">이 이름을 참조하여 나중에 튜닝 세션을 검토할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="17536-336">You can refer to this name to review the tuning session later.</span></span>  
  
 <span data-ttu-id="17536-337">**최근에 사용한 파일**</span><span class="sxs-lookup"><span data-stu-id="17536-337">**File**</span></span>  
 <span data-ttu-id="17536-338">작업에 사용할 .sql 스크립트 또는 추적 파일을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="17536-338">Specify a .sql script or trace file for a workload.</span></span> <span data-ttu-id="17536-339">이 입력란에 경로와 파일 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="17536-339">Specify the path and filename in the associated text box.</span></span> <span data-ttu-id="17536-340">데이터베이스 엔진 튜닝 관리자에서는 작업 추적 파일이 롤오버 파일이라고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="17536-340">Database Engine Tuning Advisor assumes that the workload trace file is a rollover file.</span></span> <span data-ttu-id="17536-341">롤오버 파일에 대한 자세한 내용은 [Limit Trace File and Table Sizes](../sql-trace/limit-trace-file-and-table-sizes.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="17536-341">For more information about rollover files, see [Limit Trace File and Table Sizes](../sql-trace/limit-trace-file-and-table-sizes.md).</span></span>  
  
 <span data-ttu-id="17536-342">**테이블**</span><span class="sxs-lookup"><span data-stu-id="17536-342">**Table**</span></span>  
 <span data-ttu-id="17536-343">작업에 사용할 추적 테이블을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="17536-343">Specify a trace table for a workload.</span></span> <span data-ttu-id="17536-344">해당 입력란에 다음과 같이 추적 테이블의 정규화된 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="17536-344">Specify the fully qualified name of the trace table in the associated text box as follows:</span></span>  
  
```  
database_name.owner_name.table_name  
```  
  
-   <span data-ttu-id="17536-345">추적 테이블을 작업 테이블로 사용하기 전에 추적이 중지되어 있는지 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="17536-345">Make sure that tracing has stopped before using a trace table as a workload.</span></span>  
  
-   <span data-ttu-id="17536-346">추적 테이블은 데이터베이스 엔진 튜닝 관리자가 튜닝하는 서버와 같은 서버에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="17536-346">The trace table must exist on the same server that Database Engine Tuning Advisor is tuning.</span></span> <span data-ttu-id="17536-347">다른 서버에 추적 테이블을 만든 경우에는 이 테이블을 데이터베이스 엔진 튜닝 관리자가 튜닝하는 서버로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="17536-347">If you create the trace table on a different server, then move it to the server that Database Engine Tuning Advisor is tuning.</span></span>  
  
 <span data-ttu-id="17536-348">**계획 캐시**</span><span class="sxs-lookup"><span data-stu-id="17536-348">**Plan Cache**</span></span>  
 <span data-ttu-id="17536-349">계획 캐시를 작업으로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="17536-349">Specify the plan cache as a workload.</span></span> <span data-ttu-id="17536-350">이렇게 하면 작업을 수동으로 만들 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="17536-350">By doing this, you can avoid having to manually create a workload.</span></span> <span data-ttu-id="17536-351">데이터베이스 엔진 튜닝 관리자는 분석에 사용할 상위 1,000개의 이벤트를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="17536-351">Database Engine Tuning Advisor selects the top 1,000 events to use for analysis.</span></span>  
  
 <span data-ttu-id="17536-352">**Xml**</span><span class="sxs-lookup"><span data-stu-id="17536-352">**Xml**</span></span>  
 <span data-ttu-id="17536-353">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서 작업 쿼리를 가져오지 않은 경우에는 이 옵션이 나타나지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="17536-353">This does not appear unless you import a workload query from [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="17536-354">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서 작업 쿼리를 가져오려면</span><span class="sxs-lookup"><span data-stu-id="17536-354">To import a workload query from [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]:</span></span>  
  
1.  <span data-ttu-id="17536-355">쿼리 편집기에 쿼리를 입력한 다음 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="17536-355">Type a query into Query Editor and highlight it.</span></span>  
  
2.  <span data-ttu-id="17536-356">선택한 쿼리를 마우스 오른쪽 단추로 클릭하고 **데이터베이스 엔진 튜닝 관리자의 쿼리 분석**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="17536-356">Right-click the highlighted query and click **Analyze Query in Database Engine Tuning Advisor**.</span></span>  
  
 <span data-ttu-id="17536-357">**작업 파일(또는 테이블)을 찾습니다.**</span><span class="sxs-lookup"><span data-stu-id="17536-357">**Browse for a workload [file or table]**</span></span>  
 <span data-ttu-id="17536-358">작업 원본으로 **파일** 이나 **테이블** 을 선택한 경우 대상을 선택하려면 이 찾아보기 단추를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="17536-358">When **File** or **Table** is selected as the workload source, use this browse button to select the target.</span></span>  
  
 <span data-ttu-id="17536-359">**XML 작업을 미리 봅니다.**</span><span class="sxs-lookup"><span data-stu-id="17536-359">**Preview the XML workload**</span></span>  
 <span data-ttu-id="17536-360">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서 가져온 XML 형식 작업을 봅니다.</span><span class="sxs-lookup"><span data-stu-id="17536-360">View an XML-formatted workload that has been imported from [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="17536-361">**작업 분석용 데이터베이스**</span><span class="sxs-lookup"><span data-stu-id="17536-361">**Database for workload analysis**</span></span>  
 <span data-ttu-id="17536-362">작업 튜닝 시 데이터베이스 엔진 튜닝 관리자가 연결하는 첫 번째 데이터베이스를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="17536-362">Specify the first database to which Database Engine Tuning Advisor connects when tuning a workload.</span></span> <span data-ttu-id="17536-363">튜닝이 시작된 후 데이터베이스 엔진 튜닝 관리자는 작업에 포함된 `USE DATABASE` 문으로 지정한 데이터베이스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="17536-363">After tuning begins, Database Engine Tuning Advisor connects to the databases specified by the `USE DATABASE` statements contained in the workload.</span></span>  
  
 <span data-ttu-id="17536-364">**튜닝할 데이터베이스 및 테이블 선택**</span><span class="sxs-lookup"><span data-stu-id="17536-364">**Select databases and tables to tune**</span></span>  
 <span data-ttu-id="17536-365">튜닝할 데이터베이스와 테이블을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="17536-365">Specify the databases and tables to be tuned.</span></span> <span data-ttu-id="17536-366">모든 데이터베이스를 지정하려면 **이름** 열 머리글의 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="17536-366">To specify all of the databases, select the check box in the **Name** column heading.</span></span> <span data-ttu-id="17536-367">특정 데이터베이스를 지정하려면 데이터베이스 이름 옆의 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="17536-367">To specify certain databases, select the check box next to the database name.</span></span> <span data-ttu-id="17536-368">기본적으로 선택한 데이터베이스에 있는 모든 테이블이 자동으로 튜닝 세션에 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="17536-368">By default, all of the tables for selected databases are automatically included in the tuning session.</span></span> <span data-ttu-id="17536-369">특정 테이블을 제외하려면 **선택한 테이블** 열의 화살표를 클릭한 다음 튜닝하지 않을 테이블 옆에 있는 확인란의 선택을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="17536-369">To exclude tables, click the arrow in the **Selected Tables** column, and then clear the check boxes next to the tables that you do not want to tune.</span></span>  
  
 <span data-ttu-id="17536-370">**선택한 테이블** 아래쪽 화살표</span><span class="sxs-lookup"><span data-stu-id="17536-370">**Selected Tables** down arrow</span></span>  
 <span data-ttu-id="17536-371">테이블 목록을 확장하여 튜닝할 테이블을 선택할 수 있도록 해 줍니다.</span><span class="sxs-lookup"><span data-stu-id="17536-371">Expand the tables list to allow selecting individual tables for tuning.</span></span>  
  
 <span data-ttu-id="17536-372">**튜닝 로그 저장**</span><span class="sxs-lookup"><span data-stu-id="17536-372">**Save tuning log**</span></span>  
 <span data-ttu-id="17536-373">로그를 만들어 세션 중 발생한 오류를 기록합니다.</span><span class="sxs-lookup"><span data-stu-id="17536-373">Create a log and record errors during the session.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="17536-374">데이터베이스 엔진 튜닝 관리자는 **일반** 탭에 표시되는 테이블의 행 정보를 자동으로 업데이트하지 않습니다. 대신 데이터베이스의 메타데이터를 참조합니다.</span><span class="sxs-lookup"><span data-stu-id="17536-374">Database Engine Tuning Advisor does not automatically update the rows information for the tables displayed on the **General** tab. Instead it relies upon the metadata in the database.</span></span> <span data-ttu-id="17536-375">행 정보가 최신 정보가 아니라고 생각되는 경우에는 관련 개체에 대해 DBCC UPDATEUSAGE 명령을 실행하세요.</span><span class="sxs-lookup"><span data-stu-id="17536-375">If you suspect that the rows information is outdated, run the DBCC UPDATEUSAGE command for the relevant objects.</span></span>  
  
##### <a name="tuning-tab-options"></a><span data-ttu-id="17536-376">튜닝 탭 옵션</span><span class="sxs-lookup"><span data-stu-id="17536-376">Tuning Tab Options</span></span>  
 <span data-ttu-id="17536-377">**튜닝 옵션** 탭을 사용하여 일반 튜닝 옵션의 기본 설정을 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="17536-377">Use the **Tuning Options** tab to modify default settings of general tuning options.</span></span> <span data-ttu-id="17536-378">튜닝 세션을 시작하기 전에 **튜닝 옵션** 탭의 설정을 수정할 필요는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="17536-378">You do not have to modify the settings of the **Tuning Options** tab before starting a tuning session.</span></span>  
  
 <span data-ttu-id="17536-379">**튜닝 시간 제한**</span><span class="sxs-lookup"><span data-stu-id="17536-379">**Limit tuning time**</span></span>  
 <span data-ttu-id="17536-380">현재 튜닝 세션의 시간을 제한합니다.</span><span class="sxs-lookup"><span data-stu-id="17536-380">Limits the time for the current tuning session.</span></span> <span data-ttu-id="17536-381">이 시간을 늘일수록 보다 정확한 권장 구성이 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="17536-381">Providing more time for turning improves the quality of the recommendations.</span></span> <span data-ttu-id="17536-382">최적의 권장 구성을 생성하려면 이 옵션을 선택하지 않도록 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="17536-382">To ensure the best recommendations, do not select this option.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssDE](../../includes/ssde-md.md)] <span data-ttu-id="17536-383">튜닝 관리자를 사용하면 분석하는 동안 시스템 리소스가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="17536-383">Tuning Advisor consumes system resources during analysis.</span></span> <span data-ttu-id="17536-384">튜닝 중인 서버에서 작업량이 많을 것으로 예상되는 기간 전에 튜닝을 중지하려면 **튜닝 시간 제한** 을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="17536-384">Use **Limit tuning time** to stop tuning before periods of anticipated heavy workload on the server being tuned.</span></span>  
  
 <span data-ttu-id="17536-385">**고급 옵션**</span><span class="sxs-lookup"><span data-stu-id="17536-385">**Advanced Options**</span></span>  
 <span data-ttu-id="17536-386">**고급 튜닝 옵션** 대화 상자를 사용하여 최대 공간, 최대 키 열 수, 온라인 인덱스 등에 대한 권장 설정을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="17536-386">Use the **Advanced Tuning Options** dialog box to configure the maximum space, maximum key columns, and online index recommendations.</span></span>  
  
 <span data-ttu-id="17536-387">**권장 구성에 필요한 최대 공간 정의(MB)**</span><span class="sxs-lookup"><span data-stu-id="17536-387">**Define max. space for recommendations (MB)**</span></span>  
 <span data-ttu-id="17536-388">데이터베이스 엔진 튜닝 관리자에서 권장하는 물리적 디자인 구조에 사용할 최대 공간의 크기를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="17536-388">Type the maximum amount of space to be used by physical design structures recommended by Database Engine Tuning Advisor.</span></span>  
  
 <span data-ttu-id="17536-389">값을 입력하지 않으면 데이터베이스 엔진 튜닝 관리자에서 다음 공간 값 중에 작은 값을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="17536-389">If no value is entered here, Database Engine Tuning Advisor assumes the smaller of the following space limits:</span></span>  
  
-   <span data-ttu-id="17536-390">현재 원시 데이터 크기의 3배이며 데이터베이스의 테이블에 있는 힙과 클러스터형 인덱스의 전체 크기를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="17536-390">Three times the current raw data size, which includes the total size of heaps and clustered indexes on tables in the database.</span></span>  
  
-   <span data-ttu-id="17536-391">연결된 모든 디스크 드라이브의 여유 공간과 원시 데이터 크기를 더한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="17536-391">The free space on all attached disk drives plus the raw data size.</span></span>  
  
 <span data-ttu-id="17536-392">**모든 데이터베이스의 계획 캐시 이벤트 포함**</span><span class="sxs-lookup"><span data-stu-id="17536-392">**Include plan cache events from all databases**</span></span>  
 <span data-ttu-id="17536-393">모든 데이터베이스의 계획 캐시 이벤트를 분석하도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="17536-393">Specify that plan cache events from all databases are analyzed.</span></span>  
  
 <span data-ttu-id="17536-394">**인덱스당 최대 열 개수**</span><span class="sxs-lookup"><span data-stu-id="17536-394">**Max. columns per index**</span></span>  
 <span data-ttu-id="17536-395">인덱스에 포함할 최대 열 개수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="17536-395">Specify the maximum number of columns to include in any index.</span></span> <span data-ttu-id="17536-396">기본값은 1023입니다.</span><span class="sxs-lookup"><span data-stu-id="17536-396">The default is 1023.</span></span>  
  
 <span data-ttu-id="17536-397">**모든 권장 구성이 오프라인임**</span><span class="sxs-lookup"><span data-stu-id="17536-397">**All recommendations are offline**</span></span>  
 <span data-ttu-id="17536-398">최적의 권장 구성을 생성하지만 온라인에서 물리적 디자인 구조를 생성하는 것은 권장하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="17536-398">Generate the best recommendations possible, but do not recommend that any physical design structures be created online.</span></span>  
  
 <span data-ttu-id="17536-399">**가능한 경우 온라인 권장 구성 생성**</span><span class="sxs-lookup"><span data-stu-id="17536-399">**Generate online recommendations where possible**</span></span>  
 <span data-ttu-id="17536-400">[!INCLUDE[tsql](../../includes/tsql-md.md)] 문을 만들어 권장 구성을 구현하는 경우 오프라인으로 더 빨리 구현할 수 있는 방법이 있더라도 서버에서 온라인으로 구현할 수 있는 방법을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="17536-400">When creating [!INCLUDE[tsql](../../includes/tsql-md.md)] statements to implement the recommendations, choose methods that can be implemented with the server online, even if a faster offline method is available.</span></span>  
  
 <span data-ttu-id="17536-401">**온라인 권장 구성만 생성**</span><span class="sxs-lookup"><span data-stu-id="17536-401">**Generate only online recommendations**</span></span>  
 <span data-ttu-id="17536-402">서버를 온라인 상태로 유지할 수 있는 권장 구성만 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="17536-402">Only make recommendations that allow the server to stay online.</span></span>  
  
 <span data-ttu-id="17536-403">**중지 시간**</span><span class="sxs-lookup"><span data-stu-id="17536-403">**Stop at**</span></span>  
 <span data-ttu-id="17536-404">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 튜닝 관리자를 중지할 날짜 및 시간을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="17536-404">Provide the date and time when [!INCLUDE[ssDE](../../includes/ssde-md.md)] Tuning Advisor should stop.</span></span>  
  
 <span data-ttu-id="17536-405">**인덱스와 인덱싱된 뷰**</span><span class="sxs-lookup"><span data-stu-id="17536-405">**Indexes and indexed views**</span></span>  
 <span data-ttu-id="17536-406">클러스터형 인덱스, 비클러스터형 인덱스 및 인덱싱된 뷰 추가에 대한 권장 구성을 포함하려면 이 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="17536-406">Check this box to include recommendations for adding clustered indexes, nonclustered indexes, and indexed views.</span></span>  
  
 <span data-ttu-id="17536-407">**인덱싱된 뷰**</span><span class="sxs-lookup"><span data-stu-id="17536-407">**Indexed views**</span></span>  
 <span data-ttu-id="17536-408">인덱싱된 뷰 추가에 대한 권장 구성만 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="17536-408">Only include recommendations for adding indexed views.</span></span> <span data-ttu-id="17536-409">클러스터형 인덱스와 비클러스터형 인덱스에 대한 권장 구성은 생성되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="17536-409">Clustered and nonclustered indexes will not be recommended.</span></span>  
  
 <span data-ttu-id="17536-410">**필터링된 인덱스 포함**</span><span class="sxs-lookup"><span data-stu-id="17536-410">**Include filtered indexes**</span></span>  
 <span data-ttu-id="17536-411">필터링된 인덱스 추가에 대한 권장 구성을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="17536-411">Include recommendations for adding filtered indexes.</span></span> <span data-ttu-id="17536-412">실제 디자인 구조인 **인덱스 및 인덱싱된 보기**, **인덱스** 또는 **비클러스터형 인덱스** 옵션을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="17536-412">This option is available if you select one of these physical design structures: **Indexes and indexed views**, **Indexes**, or **Nonclustered indexes**.</span></span>  
  
 <span data-ttu-id="17536-413">**인덱스**</span><span class="sxs-lookup"><span data-stu-id="17536-413">**Indexes**</span></span>  
 <span data-ttu-id="17536-414">클러스터형 인덱스 및 비클러스터형 인덱스 추가에 대한 권장 구성만 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="17536-414">Only include recommendations for adding clustered and nonclustered indexes.</span></span> <span data-ttu-id="17536-415">인덱싱된 뷰에 대한 권장 구성은 생성되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="17536-415">Indexed views will not be recommended.</span></span>  
  
 <span data-ttu-id="17536-416">**비클러스터형 인덱스**</span><span class="sxs-lookup"><span data-stu-id="17536-416">**Nonclustered indexes**</span></span>  
 <span data-ttu-id="17536-417">비클러스터형 인덱스에 대한 권장 구성만 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="17536-417">Include recommendations for only nonclustered indexes.</span></span> <span data-ttu-id="17536-418">클러스터형 인덱스와 인덱싱된 뷰에 대한 권장 구성은 생성되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="17536-418">Clustered indexes and indexed views will not be recommended.</span></span>  
  
 <span data-ttu-id="17536-419">**기존 PDS의 사용률만 평가**</span><span class="sxs-lookup"><span data-stu-id="17536-419">**Evaluate utilization of existing PDS only**</span></span>  
 <span data-ttu-id="17536-420">현재 인덱스의 효율성만 평가되며 추가 인덱스 또는 인덱싱된 뷰에 대한 권장 구성은 생성되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="17536-420">Evaluate the effectiveness of the current indexes but do not recommend additional indexes or indexed views.</span></span>  
  
 <span data-ttu-id="17536-421">**분할 안 함**</span><span class="sxs-lookup"><span data-stu-id="17536-421">**No partitioning**</span></span>  
 <span data-ttu-id="17536-422">분할에 대한 권장 구성이 생성되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="17536-422">Do not recommend partitioning.</span></span>  
  
 <span data-ttu-id="17536-423">**전체 분할**</span><span class="sxs-lookup"><span data-stu-id="17536-423">**Full partitioning**</span></span>  
 <span data-ttu-id="17536-424">분할에 대한 권장 구성이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="17536-424">Include recommendations for partitioning.</span></span>  
  
 <span data-ttu-id="17536-425">**정렬된 분할**</span><span class="sxs-lookup"><span data-stu-id="17536-425">**Aligned partitioning**</span></span>  
 <span data-ttu-id="17536-426">파티션을 쉽게 관리할 수 있도록 새로운 권장 파티션이 정렬됩니다.</span><span class="sxs-lookup"><span data-stu-id="17536-426">New recommended partitions will be aligned to make partitions easy to maintain.</span></span>  
  
 <span data-ttu-id="17536-427">**기존 PDS 유지 안 함**</span><span class="sxs-lookup"><span data-stu-id="17536-427">**Do not keep any existing PDS**</span></span>  
 <span data-ttu-id="17536-428">불필요한 기존 인덱스, 뷰 및 분할 삭제에 대한 권장 구성이 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="17536-428">Recommend dropping unnecessary existing indexes, views, and partitioning.</span></span> <span data-ttu-id="17536-429">기존 PDS(실제 디자인 구조)가 작업을 처리하는 데 효율적인 경우 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 튜닝 관리자에서 PDS 삭제가 권장되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="17536-429">If an existing physical design structure (PDS) is useful to the workload, [!INCLUDE[ssDE](../../includes/ssde-md.md)] Tuning Advisor does not recommend dropping it.</span></span>  
  
 <span data-ttu-id="17536-430">**인덱스만 유지**</span><span class="sxs-lookup"><span data-stu-id="17536-430">**Keep indexes only**</span></span>  
 <span data-ttu-id="17536-431">기존 인덱스가 모두 유지되지만 불필요한 인덱싱된 뷰 및 분할의 삭제에 대한 권장 구성이 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="17536-431">Keep all existing indexes but recommend dropping unnecessary indexed views, and partitioning.</span></span>  
  
 <span data-ttu-id="17536-432">**기존 PDS 모두 유지**</span><span class="sxs-lookup"><span data-stu-id="17536-432">**Keep all existing PDS**</span></span>  
 <span data-ttu-id="17536-433">기존 인덱스, 인덱싱된 뷰 및 분할이 모두 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="17536-433">Keep all existing indexes, indexed views, and partitioning.</span></span>  
  
 <span data-ttu-id="17536-434">**클러스터형 인덱스만 유지**</span><span class="sxs-lookup"><span data-stu-id="17536-434">**Keep clustered indexes only**</span></span>  
 <span data-ttu-id="17536-435">기존 클러스터형 인덱스가 모두 유지되지만 불필요한 인덱싱된 뷰, 분할 및 비클러스터형 인덱스의 삭제에 대한 권장 구성이 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="17536-435">Keep all existing clustered indexes but recommend dropping unnecessary indexed views, partitions, and nonclustered indexes.</span></span>  
  
 <span data-ttu-id="17536-436">**정렬된 분할 유지**</span><span class="sxs-lookup"><span data-stu-id="17536-436">**Keep aligned partitioning**</span></span>  
 <span data-ttu-id="17536-437">현재 정렬된 상태로 분할 구조가 유지되지만 불필요한 인덱싱된 뷰, 인덱스 및 정렬되지 않은 분할의 삭제에 대한 권장 구성이 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="17536-437">Keep partitioning structures that are currently aligned, but recommend dropping unnecessary indexed views, indexes, and non-aligned partitioning.</span></span> <span data-ttu-id="17536-438">권장 구성에 따른 모든 추가 분할은 현재 파티션 구성표에 맞춰 정렬됩니다.</span><span class="sxs-lookup"><span data-stu-id="17536-438">Any additional partitioning recommended will align with the current partitioning scheme.</span></span>  
  
###### <a name="progress-tab-options"></a><span data-ttu-id="17536-439">진행률 탭 옵션</span><span class="sxs-lookup"><span data-stu-id="17536-439">Progress Tab Options</span></span>  
 <span data-ttu-id="17536-440">데이터베이스 엔진 튜닝 관리자에서 작업 분석이 시작되면 데이터베이스 엔진 튜닝 관리자의 **진행** 탭이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="17536-440">The **Progress** tab of Database Engine Tuning Advisor appears after Database Engine Tuning Advisor begins analyzing a workload.</span></span>  
  
 <span data-ttu-id="17536-441">튜닝 세션이 시작된 후에 이를 중지하려면 **동작** 메뉴에서 다음 옵션 중 하나를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="17536-441">If you want to stop the tuning session after it has started, choose one of the following options on the **Actions** menu:</span></span>  
  
-   <span data-ttu-id="17536-442">**분석 중지(권장 구성)** 는 튜닝 세션을 중지하고 데이터베이스 엔진 튜닝 관리자에서 중지 전 시점까지 수행된 분석을 기반하여 권장 구성을 생성할지 여부를 묻는 메시지를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="17536-442">**Stop Analysis (With Recommendations)** stops the tuning session and prompts you to decide whether you want Database Engine Tuning Advisor to generate recommendations based on the analysis done up to this point.</span></span>  
  
-   <span data-ttu-id="17536-443">**분석 중지** 는 권장 구성을 생성하지 않고 튜닝 세션을 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="17536-443">**Stop Analysis** stops the tuning session without generating any recommendations.</span></span>  
  
 <span data-ttu-id="17536-444">**튜닝 진행률**</span><span class="sxs-lookup"><span data-stu-id="17536-444">**Tuning Progress**</span></span>  
 <span data-ttu-id="17536-445">현재 진행 상태를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="17536-445">Indicates the current status of the progress.</span></span> <span data-ttu-id="17536-446">완료한 동작 수와 수신된 오류, 성공 및 경고 메시지 수를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="17536-446">Contains the number of actions performed, and the number of error, success, and warning messages received.</span></span>  
  
 <span data-ttu-id="17536-447">**세부 정보**</span><span class="sxs-lookup"><span data-stu-id="17536-447">**Details**</span></span>  
 <span data-ttu-id="17536-448">상태를 나타내는 아이콘이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="17536-448">Contains an icon indicating status.</span></span>  
  
 <span data-ttu-id="17536-449">**동작**</span><span class="sxs-lookup"><span data-stu-id="17536-449">**Action**</span></span>  
 <span data-ttu-id="17536-450">수행 중인 단계를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="17536-450">Displays the steps being performed.</span></span>  
  
 <span data-ttu-id="17536-451">**상태**</span><span class="sxs-lookup"><span data-stu-id="17536-451">**Status**</span></span>  
 <span data-ttu-id="17536-452">동작 단계의 상태를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="17536-452">Displays the status of the action step.</span></span>  
  
 <span data-ttu-id="17536-453">**메시지**</span><span class="sxs-lookup"><span data-stu-id="17536-453">**Message**</span></span>  
 <span data-ttu-id="17536-454">동작 단계에서 반환된 모든 메시지가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="17536-454">Contains any messages returned by the action steps.</span></span>  
  
 <span data-ttu-id="17536-455">**튜닝 로그**</span><span class="sxs-lookup"><span data-stu-id="17536-455">**Tuning Log**</span></span>  
 <span data-ttu-id="17536-456">이 튜닝 세션에 관한 정보가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="17536-456">Contains information regarding this tuning session.</span></span> <span data-ttu-id="17536-457">이 로그를 인쇄하려면 로그를 마우스 오른쪽 단추로 클릭한 다음 **인쇄**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="17536-457">To print this log, right-click the log, and then click **Print**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17536-458">참고 항목</span><span class="sxs-lookup"><span data-stu-id="17536-458">See Also</span></span>  
 <span data-ttu-id="17536-459">[데이터베이스 엔진 튜닝 관리자의 출력 보기 및 작업](database-engine-tuning-advisor.md) </span><span class="sxs-lookup"><span data-stu-id="17536-459">[View and Work with the Output from the Database Engine Tuning Advisor](database-engine-tuning-advisor.md) </span></span>  
 [<span data-ttu-id="17536-460">dta 유틸리티</span><span class="sxs-lookup"><span data-stu-id="17536-460">dta Utility</span></span>](../../tools/dta/dta-utility.md)  
  
  
