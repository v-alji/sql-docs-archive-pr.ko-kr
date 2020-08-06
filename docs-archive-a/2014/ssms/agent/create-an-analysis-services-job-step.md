---
title: Analysis Services 작업 단계 만들기 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- job steps [Analysis Services]
ms.assetid: 03d4bb86-514b-4a55-97b9-c2c0fa08b428
author: stevestein
ms.author: sstein
ms.openlocfilehash: ed0e63c22d4cad270bcb544b03decba269e4f43a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731383"
---
# <a name="create-an-analysis-services-job-step"></a><span data-ttu-id="f0c3c-102">Create an Analysis Services Job Step</span><span class="sxs-lookup"><span data-stu-id="f0c3c-102">Create an Analysis Services Job Step</span></span>
  <span data-ttu-id="f0c3c-103">이 항목에서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 또는 SQL Server 관리 개체를 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]Analysis Services 명령 및 쿼리를 실행하는 [!INCLUDE[tsql](../../includes/tsql-md.md)] 에이전트 작업 단계를 만들고 정의하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="f0c3c-103">This topic describes how to create and define [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job steps in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] that execute [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Analysis Services commands and queries by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)] or SQL Server Management Objects.</span></span>  
  
-   <span data-ttu-id="f0c3c-104">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="f0c3c-104">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="f0c3c-105">제한 사항</span><span class="sxs-lookup"><span data-stu-id="f0c3c-105">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="f0c3c-106">보안</span><span class="sxs-lookup"><span data-stu-id="f0c3c-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="f0c3c-107">**Analysis Services 명령 및/또는 쿼리를 사용하여 SQL Server 작업 단계를 만들려면:**</span><span class="sxs-lookup"><span data-stu-id="f0c3c-107">**To create a SQL Server job steps using Analysis Services commands and/or queries, with:**</span></span>  
  
     [<span data-ttu-id="f0c3c-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="f0c3c-108">SQL Server Management Studio</span></span>](#SSMS)  
  
     [<span data-ttu-id="f0c3c-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="f0c3c-109">Transact-SQL</span></span>](#TSQL)  
  
     [<span data-ttu-id="f0c3c-110">SQL Server 관리 개체</span><span class="sxs-lookup"><span data-stu-id="f0c3c-110">SQL Server Management Objects</span></span>](#SMO)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="f0c3c-111">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="f0c3c-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="f0c3c-112">제한 사항</span><span class="sxs-lookup"><span data-stu-id="f0c3c-112">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="f0c3c-113">작업 단계에서 Analysis Services 명령을 사용하는 경우 명령 문은 XML for Analysis Services **Execute** 메서드여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f0c3c-113">If the job step uses an Analysis Services command, the command statement must be an XML for Analysis Services **Execute** method.</span></span> <span data-ttu-id="f0c3c-114">문에 전체 SOAP(Simple Object Access Protocol) Envelope 또는 XML for Analysis **Discover** 메서드를 포함할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f0c3c-114">The statement may not contain a complete Simple Object Access Protocol (SOAP) envelope or an XML for Analysis **Discover** method.</span></span> <span data-ttu-id="f0c3c-115">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 에서는 전체 SOAP Envelope와 **Discover** 메서드를 지원하지만 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 작업 단계에서는 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f0c3c-115">While [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] supports complete SOAP envelopes and the **Discover** method, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job steps do not.</span></span> <span data-ttu-id="f0c3c-116">XML for Analysis Services에 대한 자세한 내용은 [XML for Analysis 개요(XMLA)](https://msdn.microsoft.com/library/ms187190.aspx)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f0c3c-116">For more information about XML for Analysis Services, see [XML for Analysis Overview (XMLA)](https://msdn.microsoft.com/library/ms187190.aspx).</span></span>  
  
-   <span data-ttu-id="f0c3c-117">작업 단계에서 Analysis Services 쿼리를 사용하는 경우 쿼리 문은 MDX(Multidimensional Expressions) 쿼리여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f0c3c-117">If the job step uses an Analysis Services query, the query statement must be a multidimensional expressions (MDX) query.</span></span> <span data-ttu-id="f0c3c-118">MDX에 대 한 자세한 내용은 [Mdx 쿼리 기본 사항 &#40;Analysis Services&#41;](https://docs.microsoft.com/analysis-services/multidimensional-models/mdx/mdx-query-fundamentals-analysis-services)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f0c3c-118">For more information about MDX, see [MDX Query Fundamentals &#40;Analysis Services&#41;](https://docs.microsoft.com/analysis-services/multidimensional-models/mdx/mdx-query-fundamentals-analysis-services).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="f0c3c-119">보안</span><span class="sxs-lookup"><span data-stu-id="f0c3c-119">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="f0c3c-120">권한</span><span class="sxs-lookup"><span data-stu-id="f0c3c-120">Permissions</span></span>  
  
-   <span data-ttu-id="f0c3c-121">Analysis Services 하위 시스템을 사용하는 작업 단계를 실행하려면 사용자가 **sysadmin** 고정 서버 역할의 멤버이거나 이 하위 시스템을 사용하도록 정의된 올바른 프록시 계정에 액세스할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f0c3c-121">To run a job step that uses the Analysis Services subsystem, a user must be a member of the **sysadmin** fixed server role or have access to a valid proxy account defined to use this subsystem.</span></span> <span data-ttu-id="f0c3c-122">또한 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 서비스 계정이나 프록시가 Analysis Services 관리자이고 올바른 Windows 도메인 계정이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f0c3c-122">In addition, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service account or the proxy must be an Analysis Services administrator and a valid Windows domain account.</span></span>  
  
-   <span data-ttu-id="f0c3c-123">**sysadmin** 고정 서버 역할의 멤버만 작업 단계 출력을 파일에 쓸 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f0c3c-123">Only members of the **sysadmin** fixed server role can write job step output to a file.</span></span> <span data-ttu-id="f0c3c-124">**msdb** 데이터베이스에서 **SQLAgentUserRole** 데이터베이스 역할 멤버인 사용자가 작업 단계를 실행하면 테이블에만 출력을 쓸 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f0c3c-124">If the job step is run by users who are members of the **SQLAgentUserRole** database role in the **msdb** database, then the output can be written only to a table.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="f0c3c-125">에이전트에서 **msdb** 데이터베이스의 **sysjobstepslog** 테이블에 작업 단계 출력을 씁니다.</span><span class="sxs-lookup"><span data-stu-id="f0c3c-125">Agent writes job step output to the **sysjobstepslog** table in the **msdb** database.</span></span>  
  
-   <span data-ttu-id="f0c3c-126">자세한 내용은 [SQL Server 에이전트 보안 구현](implement-sql-server-agent-security.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f0c3c-126">For detailed information, see [Implement SQL Server Agent Security](implement-sql-server-agent-security.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> <span data-ttu-id="f0c3c-127">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="f0c3c-127">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-create-an-analysis-services-command-job-step"></a><span data-ttu-id="f0c3c-128">Analysis Services 명령 작업 단계를 만들려면</span><span class="sxs-lookup"><span data-stu-id="f0c3c-128">To create an Analysis Services command job step</span></span>  
  
1.  <span data-ttu-id="f0c3c-129">**개체 탐색기** 에서 인스턴스에 연결한 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 다음 해당 인스턴스를 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="f0c3c-129">In **Object Explorer,** connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="f0c3c-130">**SQL Server 에이전트**를 확장하고 새 작업을 만들거나 기존 작업을 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f0c3c-130">Expand **SQL Server Agent**, create a new job or right-click an existing job, and then click **Properties**.</span></span> <span data-ttu-id="f0c3c-131">작업을 만드는 방법은 [작업 만들기](create-jobs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f0c3c-131">For more information on creating a job, see [Create Jobs](create-jobs.md).</span></span>  
  
3.  <span data-ttu-id="f0c3c-132">**작업 속성** 대화 상자에서 **단계** 페이지를 클릭한 다음 **새로 만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f0c3c-132">In the **Job Properties** dialog box, click the **Steps** page, and then click **New**.</span></span>  
  
4.  <span data-ttu-id="f0c3c-133">**새 작업 단계** 대화 상자에서 작업 **단계 이름**을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="f0c3c-133">In the **New Job Step** dialog box, type a job **Step name**.</span></span>  
  
5.  <span data-ttu-id="f0c3c-134">**유형** 목록에서 **SQL Server Analysis Services 명령**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f0c3c-134">In the **Type** list, click **SQL Server Analysis Services Command**.</span></span>  
  
6.  <span data-ttu-id="f0c3c-135">**다음 계정으로 실행** 목록에서 Analysis Services 명령 하위 시스템을 사용하도록 정의된 프록시를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f0c3c-135">In the **Run as** list, select a proxy that has been defined to use the Analysis Services Command subsystem.</span></span> <span data-ttu-id="f0c3c-136">**sysadmin** 고정 서버 역할의 멤버인 사용자는 **SQL 에이전트 서비스 계정** 을 선택하여 이 작업 단계를 실행할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f0c3c-136">A user who is a member of the **sysadmin** fixed server role can also select **SQL Agent Service Account** to run this job step.</span></span>  
  
7.  <span data-ttu-id="f0c3c-137">작업 단계를 실행할 **서버** 를 선택하거나 서버 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="f0c3c-137">Select the **Server** where the job step will run, or type the server name.</span></span>  
  
8.  <span data-ttu-id="f0c3c-138">**명령** 입력란에 실행할 문을 입력하거나 **열기** 를 클릭하여 문을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f0c3c-138">In the **Command** box, type the statement to execute, or click **Open** to select a statement.</span></span>  
  
9. <span data-ttu-id="f0c3c-139">작업 단계가 성공하거나 실패할 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트가 수행할 동작으로 작업 단계를 시도할 횟수 및 작업 단계 출력이 쓸 위치와 같은 작업 단계에 대한 옵션을 정의하려면 **고급** 페이지를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f0c3c-139">Click the **Advanced** page to define options for this job step, such as what action [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent should take if the job step succeeds or fails, how many times the job step should be attempted, and where the job step output should be written.</span></span>  
  
#### <a name="to-create-an-analysis-services-query-job-step"></a><span data-ttu-id="f0c3c-140">Analysis Services 쿼리 작업 단계를 만들려면</span><span class="sxs-lookup"><span data-stu-id="f0c3c-140">To create an Analysis Services query job step</span></span>  
  
1.  <span data-ttu-id="f0c3c-141">**개체 탐색기** 에서 인스턴스에 연결한 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 다음 해당 인스턴스를 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="f0c3c-141">In **Object Explorer,** connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="f0c3c-142">**SQL Server 에이전트**를 확장하고 새 작업을 만들거나 기존 작업을 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f0c3c-142">Expand **SQL Server Agent**, create a new job or right-click an existing job, and then click **Properties**.</span></span> <span data-ttu-id="f0c3c-143">작업을 만드는 방법은 [작업 만들기](create-jobs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f0c3c-143">For more information on creating a job, see [Create Jobs](create-jobs.md).</span></span>  
  
3.  <span data-ttu-id="f0c3c-144">**작업 속성** 대화 상자에서 **단계** 페이지를 클릭한 다음 **새로 만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f0c3c-144">In the **Job Properties** dialog, click the **Steps** page, and then click **New**.</span></span>  
  
4.  <span data-ttu-id="f0c3c-145">**새 작업 단계** 대화 상자에서 작업 **단계 이름**을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="f0c3c-145">In the **New Job Step** dialog, type a job **Step name**.</span></span>  
  
5.  <span data-ttu-id="f0c3c-146">**유형** 목록에서 **SQL Server Analysis Services 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f0c3c-146">In the **Type** list, click **SQL Server Analysis Services Query**.</span></span>  
  
6.  <span data-ttu-id="f0c3c-147">**다음 계정으로 실행** 목록에서 Analysis Services 쿼리 하위 시스템을 사용하도록 정의된 프록시를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f0c3c-147">In the **Run as** list, select a proxy that has been defined to use the Analysis Services Query subsystem.</span></span> <span data-ttu-id="f0c3c-148">**sysadmin** 고정 서버 역할의 멤버인 사용자는 **SQL 에이전트 서비스 계정** 을 선택하여 이 작업 단계를 실행할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f0c3c-148">A user who is a member of the **sysadmin** fixed server role can also select **SQL Agent Service Account** to run this job step.</span></span>  
  
7.  <span data-ttu-id="f0c3c-149">작업 단계를 실행할 **서버** 와 **데이터베이스** 를 선택하거나 서버 또는 데이터베이스 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="f0c3c-149">Select the **Server** and the **Database** where the job step will run, or type the server or database name.</span></span>  
  
8.  <span data-ttu-id="f0c3c-150">**명령** 입력란에 실행할 문을 입력하거나 **열기** 를 클릭하여 문을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f0c3c-150">In the **Command** box, type the statement to execute, or click **Open** to select a statement.</span></span>  
  
9. <span data-ttu-id="f0c3c-151">작업 단계가 성공하거나 실패할 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트가 수행할 동작으로 작업 단계를 시도할 횟수 및 작업 단계 출력이 쓸 위치와 같은 작업 단계에 대한 옵션을 정의하려면 **고급** 페이지를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f0c3c-151">Click the **Advanced** page to define options for this job step, such as what action [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent should take if the job step succeeds or fails, how many times the job step should be attempted, and where the job step output should be written.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TSQL"></a> <span data-ttu-id="f0c3c-152">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="f0c3c-152">Using Transact-SQL</span></span>  
  
#### <a name="to-create-an-analysis-services-command-job-step"></a><span data-ttu-id="f0c3c-153">Analysis Services 명령 작업 단계를 만들려면</span><span class="sxs-lookup"><span data-stu-id="f0c3c-153">To create an Analysis Services command job step</span></span>  
  
1.  <span data-ttu-id="f0c3c-154">**개체 탐색기**에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="f0c3c-154">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="f0c3c-155">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f0c3c-155">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="f0c3c-156">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f0c3c-156">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```sql
    -- Creates a job step that uses XMLA to create a relational data source that references the AdventureWorks2012 Microsoft SQL Server database  
    USE msdb;  
    GO  
    EXEC sp_add_jobstep  
        @job_name = N'Weekly Sales Data Backup',  
        @step_name = N'Create a relational data source that references the AdventureWorks2012 Microsoft SQL Server database ',  
        @subsystem = N'ANALYSISCOMMAND',  
        @command = N' <Create xmlns="https://schemas.microsoft.com/analysisservices/2003/engine">  
        <ParentObject>  
            <DatabaseID>AdventureWorks2012</DatabaseID>  
        </ParentObject>  
        <ObjectDefinition>  
            <DataSource xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:type="RelationalDataSource">  
                <ID>AdventureWorks2012</ID>  
                <Name>Adventure Works 2012</Name>  
                <ConnectionString>Data Source=localhost;Initial Catalog=AdventureWorks2012;Integrated Security=True</ConnectionString>  
                <ImpersonationInfo>  
                    <ImpersonationMode>ImpersonateServiceAccount</ImpersonationMode>  
                </ImpersonationInfo>  
                <ManagedProvider>System.Data.SqlClient</ManagedProvider>  
                <Timeout>PT0S</Timeout>  
            </DataSource>  
        </ObjectDefinition>  
    </Create>', ;  
    GO  
    ```  
  
 <span data-ttu-id="f0c3c-157">자세한 내용은 [sp_add_jobstep &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f0c3c-157">For more information, see [sp_add_jobstep &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql).</span></span>  
  
#### <a name="to-create-an-analysis-services-query-job-step"></a><span data-ttu-id="f0c3c-158">Analysis Services 쿼리 작업 단계를 만들려면</span><span class="sxs-lookup"><span data-stu-id="f0c3c-158">To create an Analysis Services query job step</span></span>  
  
1.  <span data-ttu-id="f0c3c-159">**개체 탐색기**에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="f0c3c-159">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="f0c3c-160">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f0c3c-160">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="f0c3c-161">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f0c3c-161">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```sql
    -- Creates a job step that uses MDX to return data  
    USE msdb;  
    GO  
    EXEC sp_add_jobstep  
        @job_name = N'Weekly Sales Data Backup',  
        @step_name = N'Returns the Internet sales amount by state',  
        @subsystem = N'ANALYSISQUERY',  
        @command = N' SELECT  
       [Measures].[Internet Sales Amount] ON COLUMNS,  
       [Customer].[State-Province].Members ON ROWS  
    FROM [AdventureWorks2012]',   
        @retry_attempts = 5,  
        @retry_interval = 5 ;  
    GO  
    ```  
  
 <span data-ttu-id="f0c3c-162">자세한 내용은 [sp_add_jobstep &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f0c3c-162">For more information, see [sp_add_jobstep &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql).</span></span>  
  
##  <a name="using-sql-server-management-objects"></a><a name="SMO"></a><span data-ttu-id="f0c3c-163">SQL Server 관리 개체 사용</span><span class="sxs-lookup"><span data-stu-id="f0c3c-163">Using SQL Server Management Objects</span></span>  
 <span data-ttu-id="f0c3c-164">**PowerShell 스크립트 작업 단계를 만들려면**</span><span class="sxs-lookup"><span data-stu-id="f0c3c-164">**To create a PowerShell Script job step**</span></span>  
  
 <span data-ttu-id="f0c3c-165">선택한 프로그래밍 언어(예: XMLA 또는 MDX)를 사용하여 `JobStep` 클래스를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="f0c3c-165">Use the `JobStep` class by using a programming language that you choose, such as XMLA or MDX.</span></span> <span data-ttu-id="f0c3c-166">자세한 내용은 [SMO(SQL Server 관리 개체)](https://msdn.microsoft.com/library/ms162169.aspx)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f0c3c-166">For more information, see [SQL Server Management Objects (SMO)](https://msdn.microsoft.com/library/ms162169.aspx).</span></span>  
