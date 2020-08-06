---
title: 복제 시스템 저장 프로시저 개념 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: reference
dev_langs:
- TSQL
helpviewer_keywords:
- stored procedures [SQL Server replication], programming
- programming [SQL Server replication], system stored procedures
- programming interfaces [SQL Server replication]
- system stored procedures [SQL Server replication]
- replication [SQL Server], how-to topics
ms.assetid: 816d2bda-ed72-43ec-aa4d-7ee3dc25fd8a
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 50536e5b6816c84dff26c9c9f99c46d02272b7de
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741852"
---
# <a name="replication-system-stored-procedures-concepts"></a><span data-ttu-id="54f9e-102">Replication System Stored Procedures Concepts</span><span class="sxs-lookup"><span data-stu-id="54f9e-102">Replication System Stored Procedures Concepts</span></span>
  <span data-ttu-id="54f9e-103">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]에서 복제 토폴로지의 사용자 구성 가능한 모든 기능에 대한 프로그래밍 방식 액세스는 시스템 저장 프로시저를 통해 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="54f9e-103">In [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], programmatic access to all of the user-configurable functionality in a replication topology is provided by system stored procedures.</span></span> <span data-ttu-id="54f9e-104">저장 프로시저는 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]나 sqlcmd 명령줄 유틸리티를 사용하여 개별적으로 실행할 수 있지만 복제 태스크의 논리적 시퀀스를 수행하기 위해 실행할 수 있는 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 스크립트 파일을 작성하는 것이 효율적일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="54f9e-104">While stored procedures may be executed individually using the [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] or the sqlcmd command-line utility, it may be beneficial to write [!INCLUDE[tsql](../../../includes/tsql-md.md)] script files that can be executed to perform a logical sequence of replication tasks.</span></span>  
  
 <span data-ttu-id="54f9e-105">복제 태스크 스크립트를 작성하면 다음과 같은 이점이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="54f9e-105">Scripting replication tasks provides the following benefits:</span></span>  
  
-   <span data-ttu-id="54f9e-106">복제 토폴로지 배포에 사용한 단계의 영구 복사본을 유지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="54f9e-106">Keeps a permanent copy of the steps used to deploy your replication topology.</span></span>  
  
-   <span data-ttu-id="54f9e-107">스크립트 하나로 여러 구독자를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="54f9e-107">Uses a single script to configure multiple Subscribers.</span></span>  
  
-   <span data-ttu-id="54f9e-108">코드를 평가하고 이해하고 변경하거나 문제를 해결할 수 있게 하여 새로운 데이터베이스 관리자를 신속하게 교육할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="54f9e-108">Quickly educates new database administrators by enabling them to evaluate, understand, change, or troubleshoot the code.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="54f9e-109">스크립트는 보안상 위험할 수 있습니다. 사용자 몰래 또는 사용자 개입 없이 시스템 함수를 호출할 수 있으며 보안 자격 증명을 일반 텍스트로 포함할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="54f9e-109">Scripts can be the source of security vulnerabilities; they can invoke system functions without user knowledge or intervention and may contain security credentials in plain text.</span></span> <span data-ttu-id="54f9e-110">스크립트를 사용하기 전에 스크립트에 보안 문제가 있는지 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="54f9e-110">Review scripts for security issues before you use them.</span></span>  
  
## <a name="creating-replication-scripts"></a><span data-ttu-id="54f9e-111">복제 스크립트 만들기</span><span class="sxs-lookup"><span data-stu-id="54f9e-111">Creating Replication Scripts</span></span>  
 <span data-ttu-id="54f9e-112">복제의 관점에서 스크립트는 각 문이 복제 저장 프로시저를 실행하는 일련의 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 문입니다.</span><span class="sxs-lookup"><span data-stu-id="54f9e-112">From the standpoint of replication, a script is a series of one or more [!INCLUDE[tsql](../../../includes/tsql-md.md)] statements where each statement executes a replication stored procedure.</span></span> <span data-ttu-id="54f9e-113">스크립트는 sqlcmd 유틸리티를 사용하여 실행할 수 있는 텍스트 파일로, 주로 .sql 파일 확장명을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="54f9e-113">Scripts are text files, often with a .sql file extension, that can be run using the sqlcmd utility.</span></span> <span data-ttu-id="54f9e-114">스크립트 파일을 실행하면 sqlcmd 유틸리티는 파일에 저장된 SQL 문을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="54f9e-114">When a script file is run, the utility executes the SQL statements stored in the file.</span></span> <span data-ttu-id="54f9e-115">마찬가지로 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 프로젝트의 쿼리 개체로 스크립트를 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="54f9e-115">Similarly, a script can be stored as a query object in a [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] project.</span></span>  
  
 <span data-ttu-id="54f9e-116">복제 스크립트는 다음과 같은 방법으로 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="54f9e-116">Replication scripts can be created in the following ways:</span></span>  
  
-   <span data-ttu-id="54f9e-117">스크립트를 직접 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="54f9e-117">Manually create the script.</span></span>  
  
-   <span data-ttu-id="54f9e-118">복제 마법사에 제공되는 스크립트 생성 기능을 사용하거나</span><span class="sxs-lookup"><span data-stu-id="54f9e-118">Use the script generation features that are provided in the replication wizards or</span></span>  
  
-   [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]<span data-ttu-id="54f9e-119">입니다.</span><span class="sxs-lookup"><span data-stu-id="54f9e-119">.</span></span> <span data-ttu-id="54f9e-120">자세한 내용은 [Scripting Replication](../scripting-replication.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="54f9e-120">For more information, see [Scripting Replication](../scripting-replication.md).</span></span>  
  
-   <span data-ttu-id="54f9e-121">RMO(복제 관리 개체)를 사용하여 RMO 개체를 만드는 스크립트를 프로그래밍 방식으로 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="54f9e-121">Use Replication Management Objects (RMOs) to programmatically generate the script to create an RMO object.</span></span>  
  
 <span data-ttu-id="54f9e-122">복제 스크립트를 직접 만들 경우에는 다음과 같은 사항을 고려해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="54f9e-122">When you manually create replication scripts, keep the following considerations in mind:</span></span>  
  
-   [!INCLUDE[tsql](../../../includes/tsql-md.md)] <span data-ttu-id="54f9e-123">스크립트에는 일괄 처리가 하나 이상 있습니다.</span><span class="sxs-lookup"><span data-stu-id="54f9e-123">scripts have one or more batches.</span></span> <span data-ttu-id="54f9e-124">GO 명령은 일괄 처리의 끝을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="54f9e-124">The GO command signals the end of a batch.</span></span> <span data-ttu-id="54f9e-125">[!INCLUDE[tsql](../../../includes/tsql-md.md)] 스크립트에 GO 명령이 없으면 스크립트가 단일 일괄 처리로 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="54f9e-125">If a [!INCLUDE[tsql](../../../includes/tsql-md.md)] script does not have any GO commands, it is executed as a single batch.</span></span>  
  
-   <span data-ttu-id="54f9e-126">일괄 처리 하나에 복제 저장 프로시저를 여러 개 실행할 경우에는 첫 번째 프로시저 이후의 모든 프로시저 앞에 EXECUTE 키워드를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="54f9e-126">When executing multiple replication stored procedures in a single batch, after the first procedure, all subsequent procedures in the batch must be preceded by the EXECUTE keyword.</span></span>  
  
-   <span data-ttu-id="54f9e-127">일괄 처리에 포함된 모든 저장 프로시저가 컴파일되어야 일괄 처리가 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="54f9e-127">All stored procedures in a batch must compile before a batch will execute.</span></span> <span data-ttu-id="54f9e-128">그러나 일괄 처리가 컴파일되고 실행 계획이 작성된 후에는 런타임 오류가 발생하거나 발생하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="54f9e-128">However, once the batch has been compiled, and an execution plan has been created, a run-time error may or may not occur.</span></span>  
  
-   <span data-ttu-id="54f9e-129">복제를 구성하는 스크립트를 만들 때는 스크립트 파일에 보안 자격 증명이 저장되지 않도록 Windows 인증을 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="54f9e-129">When creating scripts to configure replication, you should use Windows Authentication to avoid storing security credentials in the script file.</span></span> <span data-ttu-id="54f9e-130">자격 증명을 스크립트 파일에 저장해야 하는 경우에는 파일에 무단으로 액세스하지 못하도록 보안을 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="54f9e-130">If you must store credentials in a script file, you must secure the file to prevent unauthorized access.</span></span>  
  
## <a name="sample-replication-script"></a><span data-ttu-id="54f9e-131">복제 스크립트 예제</span><span class="sxs-lookup"><span data-stu-id="54f9e-131">Sample Replication Script</span></span>  
 <span data-ttu-id="54f9e-132">다음 스크립트를 실행하여 서버에 게시 및 배포를 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="54f9e-132">The following script can be executed to setup publishing and distribution on a server.</span></span>  
  
```  
-- This script uses sqlcmd scripting variables. They are in the form  
-- $(MyVariable). For information about how to use scripting variables    
-- on the command line and in SQL Server Management Studio, see the   
-- "Executing Replication Scripts" section in the topic  
-- "Programming Replication Using System Stored Procedures".  
  
-- Install the Distributor and the distribution database.  
DECLARE @distributor AS sysname;  
DECLARE @distributionDB AS sysname;  
DECLARE @publisher AS sysname;  
DECLARE @directory AS nvarchar(500);  
DECLARE @publicationDB AS sysname;  
-- Specify the Distributor name.  
SET @distributor = $(DistPubServer);  
-- Specify the distribution database.  
SET @distributionDB = N'distribution';  
-- Specify the Publisher name.  
SET @publisher = $(DistPubServer);  
-- Specify the replication working directory.  
SET @directory = N'\\' + $(DistPubServer) + '\repldata';  
-- Specify the publication database.  
SET @publicationDB = N'AdventureWorks2012';   
  
-- Install the server MYDISTPUB as a Distributor using the defaults,  
-- including autogenerating the distributor password.  
USE master  
EXEC sp_adddistributor @distributor = @distributor;  
  
-- Create a new distribution database using the defaults, including  
-- using Windows Authentication.  
USE master  
EXEC sp_adddistributiondb @database = @distributionDB,   
    @security_mode = 1;  
GO  
  
-- Create a Publisher and enable AdventureWorks2012 for replication.  
-- Add MYDISTPUB as a publisher with MYDISTPUB as a local distributor  
-- and use Windows Authentication.  
DECLARE @distributionDB AS sysname;  
DECLARE @publisher AS sysname;  
-- Specify the distribution database.  
SET @distributionDB = N'distribution';  
-- Specify the Publisher name.  
SET @publisher = $(DistPubServer);  
  
USE [distribution]  
EXEC sp_adddistpublisher @publisher=@publisher,   
    @distribution_db=@distributionDB,   
    @security_mode = 1;  
GO  
  
```  
  
 <span data-ttu-id="54f9e-133">그런 다음 이 스크립트를 로컬에 `instdistpub.sql`로 저장하여 필요할 때 실행하거나 다시 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="54f9e-133">This script can then be saved locally as `instdistpub.sql` so that it can be run or rerun when needed.</span></span>  
  
 <span data-ttu-id="54f9e-134">위 스크립트에는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 온라인 설명서의 여러 복제 코드 예제에 사용된 **sqlcmd** 스크립팅 변수가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="54f9e-134">The previous script includes **sqlcmd** scripting variables, which are used in many of the replication code samples in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Books Online.</span></span> <span data-ttu-id="54f9e-135">스크립팅 변수는 `$(MyVariable)` 구문을 사용하여 정의되며</span><span class="sxs-lookup"><span data-stu-id="54f9e-135">Scripting variables are defined by using `$(MyVariable)` syntax.</span></span> <span data-ttu-id="54f9e-136">변수 값은 명령줄이나 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]에서 스크립트에 전달할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="54f9e-136">Values for variables can be passed to a script at the command line or in [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="54f9e-137">자세한 내용은 이 항목의 다음 섹션인 "복제 스크립트 실행"을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="54f9e-137">For more information, see the next section in this topic, "Executing Replication Scripts."</span></span>  
  
## <a name="executing-replication-scripts"></a><span data-ttu-id="54f9e-138">복제 스크립트 실행</span><span class="sxs-lookup"><span data-stu-id="54f9e-138">Executing Replication Scripts</span></span>  
 <span data-ttu-id="54f9e-139">복제 스크립트를 만든 후에는 다음 방법 중 하나로 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="54f9e-139">Once created, a replication script can be executed in one of the following ways:</span></span>  
  
### <a name="creating-a-sql-query-file-in-sql-server-management-studio"></a><span data-ttu-id="54f9e-140">SQL Server Management Studio에서 SQL 쿼리 파일 만들기</span><span class="sxs-lookup"><span data-stu-id="54f9e-140">Creating a SQL Query File in SQL Server Management Studio</span></span>  
 <span data-ttu-id="54f9e-141">[!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 프로젝트에서 SQL 쿼리 파일로 복제 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 스크립트 파일을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="54f9e-141">A replication [!INCLUDE[tsql](../../../includes/tsql-md.md)] script file can be created as a SQL Query file in a [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] project.</span></span> <span data-ttu-id="54f9e-142">스크립트를 작성하면 이 쿼리 파일에 대한 데이터베이스에 연결하여 스크립트를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="54f9e-142">After the script is written, a connection can be made to the database for this query file and the script can be executed.</span></span> <span data-ttu-id="54f9e-143">를 사용 하 여 스크립트를 만드는 방법에 대 한 자세한 내용은 [!INCLUDE[tsql](../../../includes/tsql-md.md)] [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] [쿼리 및 텍스트 편집기 &#40;SQL Server Management Studio&#41;](../../scripting/query-and-text-editors-sql-server-management-studio.md))를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="54f9e-143">For more information about how to create [!INCLUDE[tsql](../../../includes/tsql-md.md)] scripts by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], see [Query and Text Editors &#40;SQL Server Management Studio&#41;](../../scripting/query-and-text-editors-sql-server-management-studio.md)).</span></span>  
  
 <span data-ttu-id="54f9e-144">스크립팅 변수가 포함된 스크립트를 사용하려면 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]가 **sqlcmd** 모드에서 실행 중이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="54f9e-144">To use a script that includes scripting variables, [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] must be running in **sqlcmd** mode.</span></span> <span data-ttu-id="54f9e-145">**sqlcmd** 모드에서는 쿼리 편집기에서 **sqlcmd**와 관련된 추가적인 구문(예: 변수 값에 사용되는 `:setvar`)을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="54f9e-145">In **sqlcmd** mode, the Query Editor accepts additional syntax specific to **sqlcmd**, such as `:setvar`, which is used to a value for a variable.</span></span> <span data-ttu-id="54f9e-146">**sqlcmd** 모드에 대한 자세한 내용은 [쿼리 편집기로 SQLCMD 스크립트 편집](../../scripting/edit-sqlcmd-scripts-with-query-editor.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="54f9e-146">For more information about **sqlcmd** mode, see [Edit SQLCMD Scripts with Query Editor](../../scripting/edit-sqlcmd-scripts-with-query-editor.md).</span></span> <span data-ttu-id="54f9e-147">다음 스크립트에서는 `:setvar`를 사용하여 `$(DistPubServer)` 변수의 값을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="54f9e-147">In the following script, `:setvar` is used to provide a value for the `$(DistPubServer)` variable.</span></span>  
  
```  
:setvar DistPubServer N'MyPublisherAndDistributor';  
  
-- Install the Distributor and the distribution database.  
DECLARE @distributor AS sysname;  
DECLARE @distributionDB AS sysname;  
DECLARE @publisher AS sysname;  
DECLARE @directory AS nvarchar(500);  
DECLARE @publicationDB AS sysname;  
-- Specify the Distributor name.  
SET @distributor = $(DistPubServer);  
-- Specify the distribution database.  
SET @distributionDB = N'distribution';  
-- Specify the Publisher name.  
SET @publisher = $(DistPubServer);  
  
--  
-- Additional code goes here  
--  
```  
  
### <a name="using-the-sqlcmd-utility-from-the-command-line"></a><span data-ttu-id="54f9e-148">명령줄에서 sqlcmd 유틸리티 사용</span><span class="sxs-lookup"><span data-stu-id="54f9e-148">Using the sqlcmd Utility from the Command Line</span></span>  
 <span data-ttu-id="54f9e-149">다음 예제에서는 명령줄에서 [sqlcmd 유틸리티](../../../tools/sqlcmd-utility.md)를 사용하여 `instdistpub.sql` 스크립트 파일을 실행하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="54f9e-149">The following example shows how the command line is used to execute the `instdistpub.sql` script file using the [sqlcmd utility](../../../tools/sqlcmd-utility.md):</span></span>  
  
```  
sqlcmd.exe -E -S sqlserverinstance -i C:\instdistpub.sql -o C:\output.log -v DistPubServer="N'MyDistributorAndPublisher'"  
```  
  
 <span data-ttu-id="54f9e-150">이 예에서 `-E` 스위치는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]에 연결할 때 Windows 인증을 사용함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="54f9e-150">In this example, the `-E` switch indicates that Windows Authentication is used when connecting to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="54f9e-151">Windows 인증을 사용하면 스크립트 파일에 사용자 이름과 암호를 저장하지 않아도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="54f9e-151">When using Windows Authentication, there is no need to store a username and password in the script file.</span></span> <span data-ttu-id="54f9e-152">스크립트 파일의 경로와 이름은 `-i` 스위치로 지정하고 출력 파일의 이름은 `-o` 스위치(이 스위치를 사용하면 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]의 출력이 콘솔 대신 이 파일에 작성됨)로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="54f9e-152">The name and path of the script file is specified by the `-i` switch and the name of the output file is specified by the `-o` switch (output from [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] is written to this file instead of the console when this switch is used).</span></span> <span data-ttu-id="54f9e-153">`sqlcmd` 유틸리티를 사용하면 `-v` 스위치를 사용하여 런타임에 스크립팅 변수를 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 스크립트에 전달할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="54f9e-153">The `sqlcmd` utility enables you to pass scripting variables to a [!INCLUDE[tsql](../../../includes/tsql-md.md)] script at runtime using the `-v` switch.</span></span> <span data-ttu-id="54f9e-154">이 예제에서 `sqlcmd`는 실행되기 전에 스크립트에서 `$(DistPubServer)`의 모든 인스턴스를 `N'MyDistributorAndPublisher'` 값으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="54f9e-154">In this example, `sqlcmd` replaces every instance of `$(DistPubServer)` in the script with the value `N'MyDistributorAndPublisher'` before execution.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="54f9e-155">`-X` 스위치는 스크립팅 변수를 사용하지 않도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="54f9e-155">The `-X` switch disables scripting variables.</span></span>  
  
### <a name="automating-tasks-in-a-batch-file"></a><span data-ttu-id="54f9e-156">배치 파일로 태스크 자동화</span><span class="sxs-lookup"><span data-stu-id="54f9e-156">Automating Tasks in a Batch File</span></span>  
 <span data-ttu-id="54f9e-157">배치 파일을 사용하면 복제 관리 태스크, 복제 동기화 태스크 및 기타 태스크를 이 배치 파일에서 자동화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="54f9e-157">By using a batch file, replication administration tasks, replication synchronization tasks, and other tasks can be automated in the same batch file.</span></span> <span data-ttu-id="54f9e-158">다음 배치 파일은 **sqlcmd** 유틸리티를 사용하여 구독 데이터베이스를 삭제한 후 다시 만들고 병합 끌어오기 구독을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="54f9e-158">The following batch file uses the **sqlcmd** utility to drop and recreate the subscription database and add a merge pull subscription.</span></span> <span data-ttu-id="54f9e-159">그런 다음 이 파일은 병합 에이전트를 호출하여 새 구독을 동기화합니다.</span><span class="sxs-lookup"><span data-stu-id="54f9e-159">Then the file invokes the merge agent to synchronize the new subscription:</span></span>  
  
```  
REM ----------------------Script to synchronize merge subscription ----------------------  
REM -- Creates subscription database and   
REM -- synchronizes the subscription to MergeSalesPerson.  
REM -- Current computer acts as both Publisher and Subscriber.  
REM -------------------------------------------------------------------------------------  
  
SET Publisher=%computername%  
SET Subscriber=%computername%  
SET PubDb=AdventureWorks  
SET SubDb=AdventureWorksReplica  
SET PubName=AdvWorksSalesOrdersMerge  
  
REM -- Drop and recreate the subscription database at the Subscriber  
sqlcmd /S%Subscriber% /E /Q"USE master IF EXISTS (SELECT * FROM sysdatabases WHERE name='%SubDb%' ) DROP DATABASE %SubDb%"  
sqlcmd /S%Subscriber% /E /Q"USE master CREATE DATABASE %SubDb%"  
  
REM -- Add a pull subscription at the Subscriber  
sqlcmd /S%Subscriber% /E /Q"USE %SubDb% EXEC sp_addmergepullsubscription @publisher = %Publisher%, @publication = %PubName%, @publisher_db = %PubDb%"  
sqlcmd /S%Subscriber% /E /Q"USE %SubDb%  EXEC sp_addmergepullsubscription_agent @publisher = %Publisher%, @publisher_db = %PubDb%, @publication = %PubName%, @subscriber = %Subscriber%, @subscriber_db = %SubDb%, @distributor = %Publisher%"  
  
REM -- This batch file starts the merge agent at the Subscriber to   
REM -- synchronize a pull subscription to a merge publication.  
REM -- The following must be supplied on one line.  
"\Program Files\Microsoft SQL Server\120\COM\REPLMERG.EXE"  -Publisher  %Publisher% -Subscriber  %Subscriber%  -Distributor %Publisher%  -PublisherDB  %PubDb% -SubscriberDB %SubDb% -Publication %PubName% -PublisherSecurityMode 1 -OutputVerboseLevel 1  -Output  -SubscriberSecurityMode 1  -SubscriptionType 1 -DistributorSecurityMode 1 -Validate 3  
  
```  
  
## <a name="scripting-common-replication-tasks"></a><span data-ttu-id="54f9e-160">일반적인 복제 태스크 스크립팅</span><span class="sxs-lookup"><span data-stu-id="54f9e-160">Scripting Common Replication Tasks</span></span>  
 <span data-ttu-id="54f9e-161">다음은 시스템 저장 프로시저를 사용하여 스크립트로 작성할 수 있는 가장 일반적인 복제 태스크입니다.</span><span class="sxs-lookup"><span data-stu-id="54f9e-161">The following are some of the most common replication tasks can be scripted using system stored procedures:</span></span>  
  
-   <span data-ttu-id="54f9e-162">게시 및 배포 구성</span><span class="sxs-lookup"><span data-stu-id="54f9e-162">Configuring publishing and distribution</span></span>  
  
-   <span data-ttu-id="54f9e-163">게시자 및 배포자 속성 수정</span><span class="sxs-lookup"><span data-stu-id="54f9e-163">Modifying Publisher and Distributor properties</span></span>  
  
-   <span data-ttu-id="54f9e-164">게시 및 배포 해제</span><span class="sxs-lookup"><span data-stu-id="54f9e-164">Disabling publishing and distribution</span></span>  
  
-   <span data-ttu-id="54f9e-165">게시 만들기 및 아티클 정의</span><span class="sxs-lookup"><span data-stu-id="54f9e-165">Creating publications and defining articles</span></span>  
  
-   <span data-ttu-id="54f9e-166">게시 및 아티클 삭제</span><span class="sxs-lookup"><span data-stu-id="54f9e-166">Deleting publications and articles</span></span>  
  
-   <span data-ttu-id="54f9e-167">끌어오기 구독 만들기</span><span class="sxs-lookup"><span data-stu-id="54f9e-167">Creating a pull subscription</span></span>  
  
-   <span data-ttu-id="54f9e-168">끌어오기 구독 수정</span><span class="sxs-lookup"><span data-stu-id="54f9e-168">Modifying a pull subscription</span></span>  
  
-   <span data-ttu-id="54f9e-169">끌어오기 구독 삭제</span><span class="sxs-lookup"><span data-stu-id="54f9e-169">Deleting a pull subscription</span></span>  
  
-   <span data-ttu-id="54f9e-170">밀어넣기 구독 만들기</span><span class="sxs-lookup"><span data-stu-id="54f9e-170">Creating a push subscription</span></span>  
  
-   <span data-ttu-id="54f9e-171">밀어넣기 구독 수정</span><span class="sxs-lookup"><span data-stu-id="54f9e-171">Modifying a push subscription</span></span>  
  
-   <span data-ttu-id="54f9e-172">밀어넣기 구독 삭제</span><span class="sxs-lookup"><span data-stu-id="54f9e-172">Deleting a push subscription</span></span>  
  
-   <span data-ttu-id="54f9e-173">끌어오기 구독 동기화</span><span class="sxs-lookup"><span data-stu-id="54f9e-173">Synchronizing a pull subscription</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54f9e-174">참고 항목</span><span class="sxs-lookup"><span data-stu-id="54f9e-174">See Also</span></span>  
 <span data-ttu-id="54f9e-175">[복제 프로그래밍 개념](replication-programming-concepts.md) </span><span class="sxs-lookup"><span data-stu-id="54f9e-175">[Replication Programming Concepts](replication-programming-concepts.md) </span></span>  
 <span data-ttu-id="54f9e-176">[복제 저장 프로시저&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="54f9e-176">[Replication Stored Procedures &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql) </span></span>  
 [<span data-ttu-id="54f9e-177">복제 스크립팅</span><span class="sxs-lookup"><span data-stu-id="54f9e-177">Scripting Replication</span></span>](../scripting-replication.md)  
  
  
