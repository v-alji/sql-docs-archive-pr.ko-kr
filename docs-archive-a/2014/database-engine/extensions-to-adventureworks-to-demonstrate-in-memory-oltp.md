---
title: 메모리 내 OLTP를 보여 주는 AdventureWorks 확장 Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 0186b7f2-cead-4203-8360-b6890f37cde8
author: stevestein
ms.author: sstein
ms.openlocfilehash: 73a87751aa6cd4734f81b60cdd87a62939ba4ead
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740317"
---
# <a name="extensions-to-adventureworks-to-demonstrate-in-memory-oltp"></a><span data-ttu-id="e0949-102">메모리 내 OLTP를 보여주기 위한 AdventureWorks 확장</span><span class="sxs-lookup"><span data-stu-id="e0949-102">Extensions to AdventureWorks to Demonstrate In-Memory OLTP</span></span>
    
## <a name="overview"></a><span data-ttu-id="e0949-103">개요</span><span class="sxs-lookup"><span data-stu-id="e0949-103">Overview</span></span>  
 <span data-ttu-id="e0949-104">이 예제에서는 [!INCLUDE[hek_2](../includes/hek-2-md.md)] 의 일부인 새로운 [!INCLUDE[ssSQL14](../includes/sssql14-md.md)]기능을 소개합니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-104">This sample showcases the new [!INCLUDE[hek_2](../includes/hek-2-md.md)] feature, which is part of [!INCLUDE[ssSQL14](../includes/sssql14-md.md)].</span></span> <span data-ttu-id="e0949-105">이 예제는 새로운 메모리 최적화 테이블과 고유하게 컴파일된 저장 프로시저를 보여주며, [!INCLUDE[hek_2](../includes/hek-2-md.md)]의 성능 이점을 설명하는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-105">It shows the new memory-optimized tables and natively-compiled stored procedures, and can be used to demonstrate performance benefits of [!INCLUDE[hek_2](../includes/hek-2-md.md)].</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e0949-106">SQL Server 2016에 대한 이 항목을 보려면 [메모리 내 OLTP를 보여주기 위한 AdventureWorks 확장](https://msdn.microsoft.com/library/mt465764.aspx)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e0949-106">To view this topic for SQL Server 2016, see [Extensions to AdventureWorks to Demonstrate In-Memory OLTP](https://msdn.microsoft.com/library/mt465764.aspx)</span></span>  
  
 <span data-ttu-id="e0949-107">또한 AdventureWorks 데이터베이스의 5개 테이블을 메모리 최적화 테이블로 마이그레이션하며, 판매 주문 처리용 데모 작업을 포함하고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-107">The sample migrates 5 tables in the AdventureWorks database to memory-optimized, and it includes a demo workload for sales order processing.</span></span> <span data-ttu-id="e0949-108">이 데모 작업을 사용하여 서버에서 [!INCLUDE[hek_2](../includes/hek-2-md.md)] 를 사용하는 경우의 성능 이점을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-108">You can use this demo workload to see the performance benefit of using [!INCLUDE[hek_2](../includes/hek-2-md.md)] on your server.</span></span>  
  
 <span data-ttu-id="e0949-109">샘플에 대한 설명에서는 테이블을 [!INCLUDE[hek_2](../includes/hek-2-md.md)]로 마이그레이션할 때 [!INCLUDE[ssSQL14](../includes/sssql14-md.md)]에서 메모리 최적화 테이블에 아직 지원되지 않는 기능을 보완하기 위해 수행한 절충 작업에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-109">In the description of the sample we discuss the tradeoffs that were made in migrating the tables to [!INCLUDE[hek_2](../includes/hek-2-md.md)] to account for the features that are not (yet) supported for memory-optimized tables in [!INCLUDE[ssSQL14](../includes/sssql14-md.md)].</span></span>  
  
 <span data-ttu-id="e0949-110">이 샘플에 대한 설명서는 다음과 같이 구성되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-110">The documentation of this sample is structured as follows:</span></span>  
  
-   <span data-ttu-id="e0949-111">샘플을 설치하고 데모 워크로드를 실행하기 위한[필수 조건](#Prerequisites)</span><span class="sxs-lookup"><span data-stu-id="e0949-111">[Prerequisites](#Prerequisites) for installing the sample and running the demo workload</span></span>  
  
-   <span data-ttu-id="e0949-112">[AdventureWorks 기반의 메모리 내 OLTP 샘플 설치](#InstallingtheIn-MemoryOLTPsamplebasedonAdventureWorks)지침</span><span class="sxs-lookup"><span data-stu-id="e0949-112">Instructions for [Installing the In-Memory OLTP sample based on AdventureWorks](#InstallingtheIn-MemoryOLTPsamplebasedonAdventureWorks)</span></span>  
  
-   <span data-ttu-id="e0949-113">예제 [테이블 및 프로시저](#Descriptionofthesampletablesandprocedures) 에 대 한 설명-샘플에서 AdventureWorks에 추가한 테이블 및 프로시저에 대 한 설명 뿐만 아니라 [!INCLUDE[hek_2](../includes/hek-2-md.md)] 원래 adventureworks 테이블 일부를 메모리 최적화로 마이그레이션하기 위한 고려 사항도 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-113">[Description of the sample tables and procedures](#Descriptionofthesampletablesandprocedures) - this includes descriptions of the tables and procedures added to AdventureWorks by the [!INCLUDE[hek_2](../includes/hek-2-md.md)] sample, as well as considerations for migrating some of the original AdventureWorks tables to memory-optimized</span></span>  
  
-   <span data-ttu-id="e0949-114">[데모 작업을 사용한 성능 측정](#PerformanceMeasurementsusingtheDemoWorkload)을 수행하기 위한 지침 – 데모 작업 자체를 실행하기 위한 지침뿐 아니라 작업을 추진하는 데 사용되는 도구인 ostress를 설치하고 실행하기 위한 지침이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-114">Instructions for performing [Performance Measurements using the Demo Workload](#PerformanceMeasurementsusingtheDemoWorkload) - this includes instructions for installing and running ostress, a tool using for driving the workload, as well as running the demo workload itself</span></span>  
  
-   [<span data-ttu-id="e0949-115">샘플의 메모리 및 디스크 공간 사용률</span><span class="sxs-lookup"><span data-stu-id="e0949-115">Memory and Disk Space Utilization in the Sample</span></span>](#MemoryandDiskSpaceUtilizationintheSample)  
  
##  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="e0949-116">필수 조건</span><span class="sxs-lookup"><span data-stu-id="e0949-116">Prerequisites</span></span>  
  
-   [!INCLUDE[ssSQL14](../includes/sssql14-md.md)]<span data-ttu-id="e0949-117">RTM-Evaluation, Developer 또는 Enterprise edition</span><span class="sxs-lookup"><span data-stu-id="e0949-117">RTM - Evaluation, Developer, or Enterprise edition</span></span>  
  
-   <span data-ttu-id="e0949-118">성능 테스트에 사용할, 프로덕션 환경과 유사한 사양을 가진 서버</span><span class="sxs-lookup"><span data-stu-id="e0949-118">For performance testing, a server with specifications similar to your production environment.</span></span> <span data-ttu-id="e0949-119">이 특정 샘플의 경우 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]에 사용할 수 있는 메모리가 16GB 이상 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-119">For this particular sample you should have at least 16GB of memory available to [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="e0949-120">의 하드웨어에 대 한 일반적인 지침은 [!INCLUDE[hek_2](../includes/hek-2-md.md)] 다음 블로그 게시물을 참조 하세요.[https://cloudblogs.microsoft.com/sqlserver/2013/08/01/hardware-considerations-for-in-memory-oltp-in-sql-server-2014/](https://cloudblogs.microsoft.com/sqlserver/2013/08/01/hardware-considerations-for-in-memory-oltp-in-sql-server-2014/)</span><span class="sxs-lookup"><span data-stu-id="e0949-120">For general guidelines on hardware for [!INCLUDE[hek_2](../includes/hek-2-md.md)], see the following blog post:[https://cloudblogs.microsoft.com/sqlserver/2013/08/01/hardware-considerations-for-in-memory-oltp-in-sql-server-2014/](https://cloudblogs.microsoft.com/sqlserver/2013/08/01/hardware-considerations-for-in-memory-oltp-in-sql-server-2014/)</span></span>  
  
##  <a name="installing-the-hek_2-sample-based-on-adventureworks"></a><a name="InstallingtheIn-MemoryOLTPsamplebasedonAdventureWorks"></a><span data-ttu-id="e0949-121">[!INCLUDE[hek_2](../includes/hek-2-md.md)]AdventureWorks에 따라 샘플 설치</span><span class="sxs-lookup"><span data-stu-id="e0949-121">Installing the [!INCLUDE[hek_2](../includes/hek-2-md.md)] sample based on AdventureWorks</span></span>  
 <span data-ttu-id="e0949-122">다음 단계를 수행하여 예제를 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-122">Follow these steps to install the sample:</span></span>  
  
1.  <span data-ttu-id="e0949-123">AdventureWorks2014 데이터베이스의 전체 백업에 대한 보관 파일을 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-123">Download the archive for the full backup of the AdventureWorks2014 database:</span></span>  
  
    1.  <span data-ttu-id="e0949-124">다음을 엽니다 [https://msftdbprodsamples.codeplex.com/downloads/get/880661](https://msftdbprodsamples.codeplex.com/downloads/get/880661) .</span><span class="sxs-lookup"><span data-stu-id="e0949-124">Open the following: [https://msftdbprodsamples.codeplex.com/downloads/get/880661](https://msftdbprodsamples.codeplex.com/downloads/get/880661).</span></span>  
  
    2.  <span data-ttu-id="e0949-125">파일을 로컬 폴더에 저장하라는 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-125">When prompted to save the file to a local folder.</span></span>  
  
2.  <span data-ttu-id="e0949-126">로컬 폴더(예: 'c:\temp')에 **AdventureWorks2014.bak** 파일의 압축을 풉니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-126">Extract the **AdventureWorks2014.bak** file to a local folder, for example 'c:\temp'.</span></span>  
  
3.  <span data-ttu-id="e0949-127">[!INCLUDE[tsql](../includes/tsql-md.md)] 또는 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]를 사용하여 데이터베이스 백업을 복원합니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-127">Restore the database backup using [!INCLUDE[tsql](../includes/tsql-md.md)] or [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]:</span></span>  
  
    1.  <span data-ttu-id="e0949-128">다음 예와 같은 데이터 파일의 대상 폴더와 파일 이름을 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-128">Identify the target folder and filename for the data file, for example</span></span>  
  
         <span data-ttu-id="e0949-129">'h:\DATA\AdventureWorks2014_Data.mdf'</span><span class="sxs-lookup"><span data-stu-id="e0949-129">'h:\DATA\AdventureWorks2014_Data.mdf'</span></span>  
  
    2.  <span data-ttu-id="e0949-130">다음 예와 같은 로그 파일의 대상 폴더와 파일 이름을 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-130">Identify the target folder and filename for the log file, for example</span></span>  
  
         <span data-ttu-id="e0949-131">'i:\DATA\AdventureWorks2014_log.ldf'</span><span class="sxs-lookup"><span data-stu-id="e0949-131">'i:\DATA\AdventureWorks2014_log.ldf'</span></span>  
  
        1.  <span data-ttu-id="e0949-132">로그 파일은 데이터 파일과 다른 드라이브에 배치되어야 합니다. 최상의 성능을 위해 SSD 또는 PCIe 스토리지와 같이 대기 시간이 적은 드라이브가 이상적입니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-132">The log file should be placed on a different drive than the data file, ideally a low latency drive such as an SSD or PCIe storage, for maximum performance.</span></span>  
  
     <span data-ttu-id="e0949-133">T-SQL 스크립트 예:</span><span class="sxs-lookup"><span data-stu-id="e0949-133">Example T-SQL script:</span></span>  
  
    ```  
    RESTORE DATABASE [AdventureWorks2014]   
      FROM DISK = N'C:\temp\AdventureWorks2014.bak'   
        WITH FILE = 1,    
      MOVE N'AdventureWorks2014_Data' TO N'h:\DATA\AdventureWorks2014_Data.mdf',    
      MOVE N'AdventureWorks2014_Log' TO N'i:\DATA\AdventureWorks2014_log.ldf'  
     GO  
    ```  
  
4.  <span data-ttu-id="e0949-134">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]의 쿼리 창에서 다음 명령을 실행하여 데이터베이스 소유자를 서버의 로그인 계정으로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-134">Change the database owner to a login on your server, by running the following command in the query window of [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]:</span></span>  
  
    ```  
    ALTER AUTHORIZATION ON DATABASE::AdventureWorks2014 TO [<NewLogin>]  
    ```  
  
5.  <span data-ttu-id="e0949-135">[!INCLUDE[ssSQL14](../includes/sssql14-md.md)] [!INCLUDE[hek_2](../includes/hek-2-md.md)] [SQL Server 2014 RTM 메모리 내 OLTP 샘플](https://go.microsoft.com/fwlink/?LinkID=396372) 의 ' RTM sample .sql ' 샘플 스크립트를 로컬 폴더로 다운로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-135">Download the sample script '[!INCLUDE[ssSQL14](../includes/sssql14-md.md)] RTM [!INCLUDE[hek_2](../includes/hek-2-md.md)] Sample.sql' from [SQL Server 2014 RTM In-Memory OLTP Sample](https://go.microsoft.com/fwlink/?LinkID=396372) to a local folder.</span></span>  
  
6.  <span data-ttu-id="e0949-136">' RTM Sample .sql ' 스크립트의 ' checkpoint_files_location ' 변수 값을 [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] [!INCLUDE[hek_2](../includes/hek-2-md.md)] 검사점 파일의 대상 위치를 가리키도록 업데이트 합니다 [!INCLUDE[hek_2](../includes/hek-2-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="e0949-136">Update the value for the variable 'checkpoint_files_location' in the script '[!INCLUDE[ssSQL14](../includes/sssql14-md.md)] RTM [!INCLUDE[hek_2](../includes/hek-2-md.md)] Sample.sql', to point to the target location for the [!INCLUDE[hek_2](../includes/hek-2-md.md)] checkpoint files.</span></span> <span data-ttu-id="e0949-137">검사점 파일은 순차 IO 성능이 좋은 드라이브에 배치되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-137">The checkpoint files should be placed on a drive with good sequential IO performance.</span></span>  
  
     <span data-ttu-id="e0949-138">변수 'database_name'의 값을 업데이트하여 AdventureWorks2014 데이터베이스를 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-138">Update the value for the variable 'database_name' to point to the AdventureWorks2014 database.</span></span>  
  
    1.  <span data-ttu-id="e0949-139">백슬래시를 \' 경로 이름의 일부로 포함 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-139">Be sure to include the backslash '\' as part of the path name</span></span>  
  
    2.  <span data-ttu-id="e0949-140">예제:</span><span class="sxs-lookup"><span data-stu-id="e0949-140">Example:</span></span>  
  
        ```  
        :setvar checkpoint_files_location "d:\DBData\"  
        ...  
        :setvar database_name "AdventureWorks2014"  
        ```  
  
7.  <span data-ttu-id="e0949-141">두 가지 방법 중 하나로 예제 스크립트를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-141">Execute the sample script, in one of two ways:</span></span>  
  
    1.  <span data-ttu-id="e0949-142">sqlcmd 명령줄 유틸리티 사용.</span><span class="sxs-lookup"><span data-stu-id="e0949-142">Using the sqlcmd command-line utility.</span></span> <span data-ttu-id="e0949-143">예를 들어 명령줄 프롬프트에서 스크립트가 포함된 폴더에서 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-143">For example, for example by running the following command from the command-line prompt in the folder containing the script:</span></span>  
  
        ```  
        sqlcmd -S . -E -i "ssSQL14 RTM hek_2 Sample.sql"  
        ```  
  
    2.  <span data-ttu-id="e0949-144">Management Studio 사용:</span><span class="sxs-lookup"><span data-stu-id="e0949-144">Using Management Studio:</span></span>  
  
        1.  <span data-ttu-id="e0949-145">[!INCLUDE[ssSQL14](../includes/sssql14-md.md)] [!INCLUDE[hek_2](../includes/hek-2-md.md)] 쿼리 창에서 ' RTM Sample. s q l ' 스크립트를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-145">Open the script '[!INCLUDE[ssSQL14](../includes/sssql14-md.md)] RTM [!INCLUDE[hek_2](../includes/hek-2-md.md)] Sample.sql' in a query window</span></span>  
  
        2.  <span data-ttu-id="e0949-146">AdventureWorks2014 데이터베이스가 포함된 대상 서버에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-146">Connect to the target server that contains the database AdventureWorks2014</span></span>  
  
        3.  <span data-ttu-id="e0949-147">' 쿼리-> SQLCMD 모드 '를 클릭 하 여 SQLCMD 모드를 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-147">Enable SQLCMD Mode, by clicking on 'Query -> SQLCMD Mode'</span></span>  
  
        4.  <span data-ttu-id="e0949-148">' 실행 ' 단추를 클릭 하 여 스크립트를 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-148">Click the button 'Execute' to run the script</span></span>  
  
##  <a name="description-of-the-sample-tables-and-procedures"></a><a name="Descriptionofthesampletablesandprocedures"></a> <span data-ttu-id="e0949-149">예제 테이블 및 프로시저에 대한 설명</span><span class="sxs-lookup"><span data-stu-id="e0949-149">Description of the sample tables and procedures</span></span>  
 <span data-ttu-id="e0949-150">예제에서는 AdventureWorks의 기존 테이블을 기반으로 제품과 판매 주문에 대한 새 테이블을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-150">The sample creates new tables for products and sales orders, based on existing tables in AdventureWorks.</span></span> <span data-ttu-id="e0949-151">새 테이블의 스키마는 아래에 설명된 대로 몇 가지 차이점이 있지만 기존 테이블과 유사합니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-151">The schema of the new tables is similar to the existing tables, with a few differences, as explained below.</span></span>  
  
 <span data-ttu-id="e0949-152">새로운 메모리 최적화 테이블에는 ‘_inmem’ 접미사가 붙습니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-152">The new memory-optimized tables carry the suffix '_inmem'.</span></span> <span data-ttu-id="e0949-153">예제에는 '_ondisk' 접미사가 붙는 해당 테이블도 포함되어 있습니다. 이러한 테이블을 사용하여 시스템에서 메모리 최적화 테이블과 디스크 기반 테이블의 성능을 일 대 일로 비교할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-153">The sample also includes corresponding tables carrying the suffix '_ondisk' - these tables can be used to make a one-to-one comparison between the performance of memory-optimized tables and disk-based tables on your system..</span></span>  
  
 <span data-ttu-id="e0949-154">성능 비교를 위한 작업에서 사용되는 메모리 최적화 테이블은 완전한 내구성을 가지며 모두 기록됩니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-154">Note that the memory-optimized tables used in the workload for performance comparison are fully durable and fully logged.</span></span> <span data-ttu-id="e0949-155">이러한 테이블은 성능 이점을 얻기 위해 내구성이나 안정성을 희생하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-155">They do not sacrifice durability or reliability to attain the performance gain.</span></span>  
  
 <span data-ttu-id="e0949-156">이 예제의 대상 작업은 판매 주문 처리이므로 제품 및 할인에 대한 정보도 고려하며,</span><span class="sxs-lookup"><span data-stu-id="e0949-156">The target workload for this sample is sales order processing, where we consider also information about products and discounts.</span></span> <span data-ttu-id="e0949-157">이를 위해 SalesOrderHeader, SalesOrderDetail, Product, SpecialOffer 및 SpecialOfferProduct 테이블이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-157">To this end, the table SalesOrderHeader, SalesOrderDetail, Product, SpecialOffer, and SpecialOfferProduct.</span></span>  
  
 <span data-ttu-id="e0949-158">두 가지 새로운 저장 프로시저 Sales.usp_InsertSalesOrder_inmem 및 Sales.usp_UpdateSalesOrderShipInfo_inmem은 판매 주문을 삽입하고 지정된 판매 주문의 배송 정보를 업데이트하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-158">Two new stored procedures, Sales.usp_InsertSalesOrder_inmem and Sales.usp_UpdateSalesOrderShipInfo_inmem, are used to insert sales orders and to update the shipping information of a given sales order.</span></span>  
  
 <span data-ttu-id="e0949-159">새로운 스키마 'Demo'에는 데모 작업을 실행하기 위한 도우미 테이블과 저장 프로시저가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-159">The new schema 'Demo' contains helper tables and stored procedures to execute a demo workload.</span></span>  
  
 <span data-ttu-id="e0949-160">구체적으로 설명하자면 [!INCLUDE[hek_2](../includes/hek-2-md.md)] 예제에서는 다음 개체를 AdventureWorks에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-160">Concretely, the [!INCLUDE[hek_2](../includes/hek-2-md.md)] sample adds the following objects to AdventureWorks:</span></span>  
  
### <a name="tables-added-by-the-sample"></a><span data-ttu-id="e0949-161">예제에서 추가된 테이블</span><span class="sxs-lookup"><span data-stu-id="e0949-161">Tables added by the sample</span></span>  
  
#### <a name="the-new-tables"></a><span data-ttu-id="e0949-162">새로운 테이블</span><span class="sxs-lookup"><span data-stu-id="e0949-162">The New Tables</span></span>  
 <span data-ttu-id="e0949-163">Sales.SalesOrderHeader_inmem</span><span class="sxs-lookup"><span data-stu-id="e0949-163">Sales.SalesOrderHeader_inmem</span></span>  
  
-   <span data-ttu-id="e0949-164">판매 주문에 대한 머리글 정보.</span><span class="sxs-lookup"><span data-stu-id="e0949-164">Header information about sales orders.</span></span> <span data-ttu-id="e0949-165">각 판매 주문에 해당하는 행이 이 테이블에 하나씩 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-165">Each sales order has one row in this table.</span></span>  
  
 <span data-ttu-id="e0949-166">Sales.SalesOrderDetail_inmem</span><span class="sxs-lookup"><span data-stu-id="e0949-166">Sales.SalesOrderDetail_inmem</span></span>  
  
-   <span data-ttu-id="e0949-167">판매 주문에 대한 세부 정보.</span><span class="sxs-lookup"><span data-stu-id="e0949-167">Details of sales orders.</span></span> <span data-ttu-id="e0949-168">판매 주문의 각 품목에 해당하는 행이 이 테이블에 하나씩 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-168">Each line item of a sales order has one row in this table.</span></span>  
  
 <span data-ttu-id="e0949-169">Sales.SpecialOffer_inmem</span><span class="sxs-lookup"><span data-stu-id="e0949-169">Sales.SpecialOffer_inmem</span></span>  
  
-   <span data-ttu-id="e0949-170">각 특별 행사와 관련된 할인율을 비롯한 특별 행사에 대한 정보.</span><span class="sxs-lookup"><span data-stu-id="e0949-170">Information about special offers, including the discount percentage associated with each special offer.</span></span>  
  
 <span data-ttu-id="e0949-171">Sales.SpecialOfferProduct_inmem</span><span class="sxs-lookup"><span data-stu-id="e0949-171">Sales.SpecialOfferProduct_inmem</span></span>  
  
-   <span data-ttu-id="e0949-172">특별 행상 및 제품 간의 참조 테이블.</span><span class="sxs-lookup"><span data-stu-id="e0949-172">Reference table between special offers and products.</span></span> <span data-ttu-id="e0949-173">각 특별 행사에는 제품이 0개 이상 있을 수 있으며 각 제품은 0개 이상의 특별 행사에 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-173">Each special offer can feature zero or more products, and each product can be featured in zero or more special offers.</span></span>  
  
 <span data-ttu-id="e0949-174">Production.Product_inmem</span><span class="sxs-lookup"><span data-stu-id="e0949-174">Production.Product_inmem</span></span>  
  
-   <span data-ttu-id="e0949-175">가격을 비롯한 제품에 대한 정보</span><span class="sxs-lookup"><span data-stu-id="e0949-175">Information about products, including their list price.</span></span>  
  
 <span data-ttu-id="e0949-176">Demo.DemoSalesOrderDetailSeed</span><span class="sxs-lookup"><span data-stu-id="e0949-176">Demo.DemoSalesOrderDetailSeed</span></span>  
  
-   <span data-ttu-id="e0949-177">예제 판매 주문을 생성하기 위해 데모 작업에서 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-177">Used in the demo workload to construct sample sales orders.</span></span>  
  
 <span data-ttu-id="e0949-178">테이블의 디스크 기반 변형:</span><span class="sxs-lookup"><span data-stu-id="e0949-178">Disk-based variations of the tables:</span></span>  
  
-   <span data-ttu-id="e0949-179">Sales.SalesOrderHeader_ondisk</span><span class="sxs-lookup"><span data-stu-id="e0949-179">Sales.SalesOrderHeader_ondisk</span></span>  
  
-   <span data-ttu-id="e0949-180">Sales.SalesOrderDetail_ondisk</span><span class="sxs-lookup"><span data-stu-id="e0949-180">Sales.SalesOrderDetail_ondisk</span></span>  
  
-   <span data-ttu-id="e0949-181">Sales.SpecialOffer_ondisk</span><span class="sxs-lookup"><span data-stu-id="e0949-181">Sales.SpecialOffer_ondisk</span></span>  
  
-   <span data-ttu-id="e0949-182">Sales.SpecialOfferProduct_ondisk</span><span class="sxs-lookup"><span data-stu-id="e0949-182">Sales.SpecialOfferProduct_ondisk</span></span>  
  
-   <span data-ttu-id="e0949-183">Production.Product_ondisk</span><span class="sxs-lookup"><span data-stu-id="e0949-183">Production.Product_ondisk</span></span>  
  
#### <a name="differences-between-original-disk-based-and-the-and-new-memory-optimized-tables"></a><span data-ttu-id="e0949-184">원래 디스크 기반 테이블과 새로운 메모리 최적화 테이블 간의 차이점</span><span class="sxs-lookup"><span data-stu-id="e0949-184">Differences between original disk-based and the and new memory-optimized tables</span></span>  
 <span data-ttu-id="e0949-185">대부분의 경우 이 예제에서 도입한 새로운 테이블은 원래 테이블과 동일한 열 및 동일한 데이터 형식을 사용하지만</span><span class="sxs-lookup"><span data-stu-id="e0949-185">For the most part, the new tables introduced by this sample use the same columns and the same data types as the original tables.</span></span> <span data-ttu-id="e0949-186">몇 가지 차이점이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-186">However, there are a few differences.</span></span> <span data-ttu-id="e0949-187">이러한 차이점과 변경에 대한 이유는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-187">We list the differences below, along with a rationale for the changes.</span></span>  
  
 <span data-ttu-id="e0949-188">Sales.SalesOrderHeader_inmem</span><span class="sxs-lookup"><span data-stu-id="e0949-188">Sales.SalesOrderHeader_inmem</span></span>  
  
-   <span data-ttu-id="e0949-189">*기본 제약 조건* 은 메모리 최적화 테이블에 지원되며 대부분의 기본 제약 조건은 있는 그대로 마이그레이션되었습니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-189">*Default constraints* are supported for memory-optimized tables, and most default constraints we migrated as is.</span></span> <span data-ttu-id="e0949-190">그러나 원래 테이블 Sales.SalesOrderHeader에는 OrderDate 및 ModifiedDate 열에 대한 현재 날짜를 검색하는 두 가지 기본 제약 조건이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-190">However, the original table Sales.SalesOrderHeader contains two default constraints that retrieve the current date, for the columns OrderDate and ModifiedDate.</span></span> <span data-ttu-id="e0949-191">동시 작업과 처리량이 많은 주문 처리 작업에서 전역 리소스는 경합 지점이 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-191">In a high throughput order processing workload with a lot of concurrency, any global resource can become a point of contention.</span></span> <span data-ttu-id="e0949-192">시스템 시간은 이러한 전역 리소스이며 판매 주문을 삽입하는 [!INCLUDE[hek_2](../includes/hek-2-md.md)] 작업을 실행할 때 병목 현상을 발생시킬 수 있다는 사실이 관찰되었습니다. 이는 판매 주문 정보뿐만 아니라 판매 주문 머리글의 여러 열에 대해 시스템 시간을 검색해야 하는 경우 특히 해당하는 사실입니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-192">System time is such a global resource, and we have observed that it can become a bottleneck when running an [!INCLUDE[hek_2](../includes/hek-2-md.md)] workload that inserts sales orders, in particular if the system time needs to be retrieved for multiple columns in the sales order header, as well as the sales order details.</span></span> <span data-ttu-id="e0949-193">이러한 문제는 이 예제에서 삽입되는 각 판매 주문에 대해 시스템 시간을 한 번만 검색하고 Sales.usp_InsertSalesOrder_inmem 저장 프로시저에서 SalesOrderHeader_inmem 및 SalesOrderDetail_inmem의 datetime 열에 이 값을 사용하여 해결되었습니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-193">The problem is addressed in this sample by retrieving the system time only once for each sales order that is inserted, and use that value for the datetime columns in SalesOrderHeader_inmem and SalesOrderDetail_inmem, in the stored procedure Sales.usp_InsertSalesOrder_inmem.</span></span>  
  
-   <span data-ttu-id="e0949-194">*별칭 UDT* - 원래 테이블은 PurchaseOrderNumber 및 AccountNumber 열에 대해 두 가지 별칭 UDT(사용자 정의 데이터 형식)인 dbo.OrderNumber 및 dbo.AccountNumber를 각각 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-194">*Alias UDTs* - The original table uses two alias user-defined data types (UDTs) dbo.OrderNumber and dbo.AccountNumber, for the columns PurchaseOrderNumber and AccountNumber, respectively.</span></span> [!INCLUDE[ssSQL14](../includes/sssql14-md.md)]<span data-ttu-id="e0949-195">에서는 메모리 최적화 테이블에 대한 별칭 UDT를 지원하지 않으므로 새 테이블은 시스템 데이터 형식 nvarchar(25) 및 nvarchar(15)을 각각 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-195">does not support alias UDT for memory-optimized tables, thus the new tables use system data types nvarchar(25) and nvarchar(15), respectively.</span></span>  
  
-   <span data-ttu-id="e0949-196">*인덱스 키의 Null 허용 열* - 원래 테이블에서 SalesPersonID 열은 Null을 허용하지만 새 테이블에서 이 열은 Null을 허용하지 않으며 값(-1)을 사용하는 기본 제약 조건을 갖습니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-196">*Nullable columns in index keys* - In the original table, the column SalesPersonID is nullable, while in the new tables the column is not nullable and has a default constraint with value (-1).</span></span> <span data-ttu-id="e0949-197">이는 메모리 최적화 테이블에 대한 인덱스의 경우 인덱스 키에 Null 허용 열이 있을 수 없기 때문이며, 이 경우 -1은 NULL의 대리 값입니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-197">This is because indexes on memory-optimized tables cannot have nullable columns in the index key; -1 is a surrogate for NULL in this case.</span></span>  
  
-   <span data-ttu-id="e0949-198">*계산 열* - [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] 에서는 메모리 최적화 테이블에서 계산 열을 지원하지 않기 때문에 계산 열 SalesOrderNumber 및 TotalDue가 생략되었습니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-198">*Computed columns* - The computed columns SalesOrderNumber and TotalDue are omitted, as [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] does not support computed columns in memory-optimized tables.</span></span> <span data-ttu-id="e0949-199">새로운 뷰 Sales.vSalesOrderHeader_extended_inmem이 SalesOrderNumber 및 TotalDue 열을 반영하므로</span><span class="sxs-lookup"><span data-stu-id="e0949-199">The new view Sales.vSalesOrderHeader_extended_inmem reflects the columns SalesOrderNumber and TotalDue.</span></span> <span data-ttu-id="e0949-200">이러한 열이 필요한 경우 이 뷰를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-200">Therefore, you can use this view if these columns are needed.</span></span>  
  
-   <span data-ttu-id="e0949-201">*FOREIGN KEY 제약 조건* 은 [!INCLUDE[ssSQL14](../includes/sssql14-md.md)]에서 메모리 최적화 테이블에 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-201">*Foreign key constraints* are not supported for memory-optimized tables in [!INCLUDE[ssSQL14](../includes/sssql14-md.md)].</span></span> <span data-ttu-id="e0949-202">또한 SalesOrderHeader_inmem은 예제 작업에서 핫 테이블이며, FOREIGN KEY 제약 조건을 지정하려면 모든 DML 작업에 대한 추가 처리가 필요합니다. 이는 이러한 제약 조건에서 참조된 다른 모든 테이블에서 조회가 필요하기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-202">In addition, SalesOrderHeader_inmem is a hot table in the example workload, and foreign keys constraints require additional processing for all DML operations, as it requires lookups in all the other tables referenced in these constraints.</span></span> <span data-ttu-id="e0949-203">따라서 응용 프로그램에서 참조 무결성을 보장하며 참조 무결성은 행이 삽입될 때 확인되지 않는다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-203">Therefore, the assumption is that the app ensures referential integrity, and referential integrity is not validated when rows are inserted.</span></span> <span data-ttu-id="e0949-204">이 테이블의 데이터에 대한 참조 무결성은 다음 스크립트를 사용하여 dbo.usp_ValidateIntegrity 저장 프로시저를 통해 확인될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-204">Referential integrity for the data in this table can be verified using the stored procedure dbo.usp_ValidateIntegrity, using the following script:</span></span>  
  
    ```  
    DECLARE @o int = object_id(N'Sales.SalesOrderHeader_inmem')  
    EXEC dbo.usp_ValidateIntegrity @o  
    ```  
  
-   <span data-ttu-id="e0949-205">*CHECK 제약 조건* 은 SQL Server 2014에서 메모리 최적화 테이블에 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-205">*Check constraints* are not supported for memory-optimized tables in SQ Server 2014.</span></span> <span data-ttu-id="e0949-206">도메인 무결성은 이 스크립트를 사용하여 참조 무결성과 함께 확인됩니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-206">Domain integrity is validated along with referential integrity using this script:</span></span>  
  
    ```  
    DECLARE @o int = object_id(N'Sales.SalesOrderHeader_inmem')  
    EXEC dbo.usp_ValidateIntegrity @o  
    ```  
  
-   <span data-ttu-id="e0949-207">*Rowguid* - rowguid 열이 생략되었습니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-207">*Rowguid* - The rowguid column is omitted.</span></span> <span data-ttu-id="e0949-208">uniqueidentifier가 메모리 최적화 테이블에 지원되지만 ROWGUIDCOL 옵션은 [!INCLUDE[ssSQL14](../includes/sssql14-md.md)]에서 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-208">While uniqueidentifier is support for memory-optimized tables, the option ROWGUIDCOL is not supported in [!INCLUDE[ssSQL14](../includes/sssql14-md.md)].</span></span> <span data-ttu-id="e0949-209">이러한 종류의 열은 일반적으로 병합 복제나 filestream 열이 있는 테이블에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-209">Columns of this kind are typically used for either merge replication or tables that have filestream columns.</span></span> <span data-ttu-id="e0949-210">이 예제에는 둘 다 포함되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-210">This sample includes neither.</span></span>  
  
 <span data-ttu-id="e0949-211">Sales.SalesOrderDetail</span><span class="sxs-lookup"><span data-stu-id="e0949-211">Sales.SalesOrderDetail</span></span>  
  
-   <span data-ttu-id="e0949-212">*기본 제약 조건* - SalesOrderHeader와 유사하게 시스템 날짜/시간을 필요로 하는 기본 제약 조건은 마이그레이션되지 않으며, 대신 판매 주문을 삽입하는 저장 프로시저가 첫 번째 삽입 시 현재 시스템 날짜/시간을 삽입하는 작업을 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-212">*Default constraints* - similar to SalesOrderHeader, the default constraint requiring the system date/time is not migrated, instead the stored procedure inserting sales orders takes care of inserting the current system date/time on first insert.</span></span>  
  
-   <span data-ttu-id="e0949-213">*계산 열* - 계산 열이 [!INCLUDE[ssSQL14](../includes/sssql14-md.md)]에서 메모리 최적화 테이블에 지원되지 않기 때문에 계산 열 LineTotal이 마이그레이션되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-213">*Computed columns* - the computed column LineTotal was not migrated as computed columns are not supported with memory-optimized tables in [!INCLUDE[ssSQL14](../includes/sssql14-md.md)].</span></span> <span data-ttu-id="e0949-214">이 열에 액세스하려면 Sales.vSalesOrderDetail_extended_inmem 뷰를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-214">To access this column use the view Sales.vSalesOrderDetail_extended_inmem.</span></span>  
  
-   <span data-ttu-id="e0949-215">*Rowguid* - rowguid 열이 생략되었습니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-215">*Rowguid* - The rowguid column is omitted.</span></span> <span data-ttu-id="e0949-216">자세한 내용은 SalesOrderHeader 테이블에 대한 설명을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e0949-216">For details see the description for the table SalesOrderHeader.</span></span>  
  
-   <span data-ttu-id="e0949-217">*CHECK* 및 *FOREIGN KEY* 제약 조건의 경우 SalesOrderHeader에 대한 설명을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e0949-217">For *check* and *foreign key* constraints see the description of SalesOrderHeader.</span></span> <span data-ttu-id="e0949-218">다음 스크립트를 사용하여 이 테이블에 대한 도메인 및 참조 무결성을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-218">The following script can be used to verify domain and referential integrity for this table:</span></span>  
  
    ```  
    DECLARE @o int = object_id(N'Sales.SalesOrderHeader_inmem')  
    EXEC dbo.usp_ValidateIntegrity @o  
    ```  
  
 <span data-ttu-id="e0949-219">Production.Product</span><span class="sxs-lookup"><span data-stu-id="e0949-219">Production.Product</span></span>  
  
-   <span data-ttu-id="e0949-220">*별칭 UDT* - 원래 테이블은 시스템 데이터 형식 bit와 동일한 사용자 정의 데이터 형식 dbo.Flag를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-220">*Alias UDTs* - the original table uses the user-defined data type dbo.Flag, which is equivalent to the system data type bit.</span></span> <span data-ttu-id="e0949-221">마이그레이션된 테이블은 bit 데이터 형식을 대신 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-221">The migrated table uses the bit data type instead.</span></span>  
  
-   <span data-ttu-id="e0949-222">*BIN2 데이터 정렬* -열 이름 및 제품 번호는 인덱스 키에 포함 되어 있으므로에서 BIN2 데이터 정렬을 포함 해야 합니다 [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="e0949-222">*BIN2 collation* - The columns Name and ProductNumber are included in index keys, and must thus have BIN2 collations in [!INCLUDE[ssSQL14](../includes/sssql14-md.md)].</span></span> <span data-ttu-id="e0949-223">여기에서는 응용 프로그램이 대/소문자 구분 안 함과 같은 데이터 정렬 사항에 의존하지 않는다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-223">Here, the assumption is that the app does not rely on collation specifics, like case insensitivity.</span></span>  
  
-   <span data-ttu-id="e0949-224">*Rowguid* - rowguid 열이 생략되었습니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-224">*Rowguid* - The rowguid column is omitted.</span></span> <span data-ttu-id="e0949-225">자세한 내용은 SalesOrderHeader 테이블에 대한 설명을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e0949-225">For details see the description for the table SalesOrderHeader.</span></span>  
  
-   <span data-ttu-id="e0949-226">*UNIQUE*, *CHECK* 및 *외래 키 제약 조건* 은 두 가지 방식으로 처리됩니다. 저장 프로시저 Product.usp_InsertProduct_inmem 및 Product.usp_DeleteProduct_inmem을 사용하여 제품을 삽입하고 삭제할 수 있습니다. 이러한 프로시저는 도메인 및 참조 무결성을 확인하며 무결성이 위반되는 경우 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-226">*Unique*, *Check* and *Foreign Key constraints* are accounted for in two ways: the stored procedures Product.usp_InsertProduct_inmem and Product.usp_DeleteProduct_inmem can be used to insert and delete products; these procedures validate domain and referential integrity, and will fail if integrity is violated.</span></span> <span data-ttu-id="e0949-227">또한 다음 스크립트를 사용하여 도메인 및 참조 무결성을 있는 그대로 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-227">In addition, the follow script can be used to validate domain and referential integrity as is:</span></span>  
  
    ```  
    DECLARE @o int = object_id(N'Production.Product')  
    EXEC dbo.usp_ValidateIntegrity @o  
    ```  
  
    -   <span data-ttu-id="e0949-228">저장 프로시저 usp_InsertProduct_inmem 및 usp_DeleteProduct_inmem은 마이그레이션된 테이블 간의 외래 키만 고려합니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-228">Note that the store procedures usp_InsertProduct_inmem and usp_DeleteProduct_inmem consider only foreign keys between the migrated tables.</span></span> <span data-ttu-id="e0949-229">다른 테이블 ProductModel, ProductSubcategory 및 UnitMeasure에 대한 참조는 고려되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-229">References to other tables ProductModel, ProductSubcategory, and UnitMeasure are not considered.</span></span>  
  
 <span data-ttu-id="e0949-230">Sales.SpecialOffer</span><span class="sxs-lookup"><span data-stu-id="e0949-230">Sales.SpecialOffer</span></span>  
  
-   <span data-ttu-id="e0949-231">*CHECK* 및 *외래 키 제약 조건* 은 두 가지 방식으로 처리됩니다. 저장 프로시저 Sales.usp_InsertSpecialOffer_inmem 및 Sales.usp_DeleteSpecialOffer_inmem을 사용하여 특별 행사를 삽입하고 삭제할 수 있습니다. 이러한 프로시저는 도메인 및 참조 무결성을 확인하며 무결성이 위반되는 경우 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-231">*Check* and *Foreign Key constraints* are accounted for in two ways: the stored procedures Sales.usp_InsertSpecialOffer_inmem and Sales.usp_DeleteSpecialOffer_inmem can be used to insert and delete special offers; these procedures validate domain and referential integrity, and will fail if integrity is violated.</span></span> <span data-ttu-id="e0949-232">또한 다음 스크립트를 사용하여 도메인 및 참조 무결성을 있는 그대로 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-232">In addition, the follow script can be used to validate domain and referential integrity as is:</span></span>  
  
    ```  
    DECLARE @o int = object_id(N'Sales.SpecialOffer_inmem')  
    EXEC dbo.usp_ValidateIntegrity @o  
    ```  
  
-   <span data-ttu-id="e0949-233">*Rowguid* - rowguid 열이 생략되었습니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-233">*Rowguid* - The rowguid column is omitted.</span></span> <span data-ttu-id="e0949-234">자세한 내용은 SalesOrderHeader 테이블에 대한 설명을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e0949-234">For details see the description for the table SalesOrderHeader.</span></span>  
  
 <span data-ttu-id="e0949-235">Sales.SpecialOfferProduct</span><span class="sxs-lookup"><span data-stu-id="e0949-235">Sales.SpecialOfferProduct</span></span>  
  
-   <span data-ttu-id="e0949-236">*외래 키 제약 조건* 은 두 가지 방식으로 처리됩니다. 저장 프로시저 Sales.usp_InsertSpecialOfferProduct_inmem을 사용하여 특별 행사와 제품 간의 관계를 삽입할 수 있습니다. 이 프로시저는 참조 무결성을 확인하며 무결성이 위반되는 경우 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-236">*Foreign Key constraints* are accounted for in two ways: the stored procedure Sales.usp_InsertSpecialOfferProduct_inmem can be used to insert relationships between special offers and products; this procedures validates referential integrity, and will fail if integrity is violated.</span></span> <span data-ttu-id="e0949-237">또한 다음 스크립트를 사용하여 참조 무결성을 있는 그대로 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-237">In addition, the follow script can be used to validate referential integrity as is:</span></span>  
  
    ```  
    DECLARE @o int = object_id(N'Sales.SpecialOfferProduct_inmem')  
    EXEC dbo.usp_ValidateIntegrity @o  
    ```  
  
-   <span data-ttu-id="e0949-238">*Rowguid* - rowguid 열이 생략되었습니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-238">*Rowguid* - The rowguid column is omitted.</span></span> <span data-ttu-id="e0949-239">자세한 내용은 SalesOrderHeader 테이블에 대한 설명을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e0949-239">For details see the description for the table SalesOrderHeader.</span></span>  
  
#### <a name="considerations-for-indexes-on-memory-optimized-tables"></a><span data-ttu-id="e0949-240">메모리 최적화 테이블의 인덱스에 대한 고려 사항</span><span class="sxs-lookup"><span data-stu-id="e0949-240">Considerations for indexes on memory-optimized tables</span></span>  
 <span data-ttu-id="e0949-241">메모리 최적화 테이블의 기준 인덱스는 포인트 조회(같음 조건자의 인덱스 검색), 범위 검색(같지 않음 조건자의 인덱스 검색), 전체 인덱스 검색 및 정렬된 검색을 지원하는 비클러스터형 인덱스입니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-241">The baseline index for memory-optimized tables is the NONCLUSTERED index, which supports point lookups (index seek on equality predicate), range scans (index seek in inequality predicate), full index scans, and ordered scans.</span></span> <span data-ttu-id="e0949-242">또한 비클러스터형 인덱스는 인덱스 키의 선행 열에 대한 검색을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-242">In addition, NONCLUSTERED indexes support searching on leading columns of the index key.</span></span> <span data-ttu-id="e0949-243">메모리 최적화 비클러스터형 인덱스는 역방향 검색만 제외하고 디스크 기반 비클러스터형 인덱스가 지원하는 모든 작업을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-243">In fact memory-optimized NONCLUSTERED indexes support all the operations supported by disk-based NONCLUSTERED indexes, with the only exception being backward scans.</span></span> <span data-ttu-id="e0949-244">따라서 비클러스터형 인덱스의 사용은 인덱스에 선택할 수 있는 안전한 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-244">Therefore, using NONCLUSTERED indexes is a safe choice for your indexes.</span></span>  
  
 <span data-ttu-id="e0949-245">해시 인덱스를 사용하여 작업을 추가로 최적화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-245">HASH indexes are can be used to further optimize the workload.</span></span> <span data-ttu-id="e0949-246">해시 인덱스는 포인트 조회와 행 삽입에 대해 특히 최적화됩니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-246">They are particularly optimized for point lookups and row inserts.</span></span> <span data-ttu-id="e0949-247">그러나 해시 인덱스가 범위 검색, 정렬된 검색 또는 선행 인덱스 키 열에 대한 검색을 지원하지 않는다는 점을 고려해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-247">However, one must consider that they do not support range scans, ordered scans, or search on leading index key columns.</span></span> <span data-ttu-id="e0949-248">따라서 이러한 인덱스를 사용할 때는 주의를 기울여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-248">Therefore, care needs to be taken when using these indexes.</span></span> <span data-ttu-id="e0949-249">또한 만들 때 bucket_count를 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-249">In addition, it is necessary to specify the bucket_count at create time.</span></span> <span data-ttu-id="e0949-250">bucket_count는 일반적으로 인덱스 키 값의 수와 그 두 배 사이에서 설정되어야 하지만 더 많이 추정해도 대개 문제가 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-250">It should usually be set at between one and two times the number of index key values, but overestimating is usually not a problem.</span></span>  
  
 <span data-ttu-id="e0949-251">[인덱스 지침](https://technet.microsoft.com/library/dn133166\(v=sql.120\).aspx) 과 [올바른 bucket_count 선택](https://technet.microsoft.com/library/dn494956\(v=sql.120\).aspx)지침에 대한 자세한 내용은 온라인 설명서를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e0949-251">See Books Online for more details about [index guidelines](https://technet.microsoft.com/library/dn133166\(v=sql.120\).aspx) and guidelines for [choosing the right bucket_count](https://technet.microsoft.com/library/dn494956\(v=sql.120\).aspx).</span></span>  
  
 <span data-ttu-id="e0949-252">마이그레이션된 테이블의 인덱스는 데모 판매 주문 처리 작업에 맞게 조정되었습니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-252">The indexes on the migrated tables have been tuned for the demo sales order processing workload.</span></span> <span data-ttu-id="e0949-253">작업은 Sales.SalesOrderHeader_inmem 및 Sales.SalesOrderDetail_inmem 테이블의 삽입 및 포인트 조회에 의존하며 Production.Product_inmem 및 Sales.SpecialOffer_inmem 테이블에서 기본 키 열에 대한 포인트 조회에도 의존합니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-253">The workload relies on inserts and point lookups in the tables Sales.SalesOrderHeader_inmem and Sales.SalesOrderDetail_inmem, and it also relies on point lookups on the primary key columns in the tables Production.Product_inmem and Sales.SpecialOffer_inmem.</span></span>  
  
 <span data-ttu-id="e0949-254">Sales.SalesOrderHeader_inmem에는 세 가지 인덱스가 있는데 정렬된 검색이나 범위 검색이 작업에 필요하지 않기 때문에 모두 성능상의 이유로 해시 인덱스입니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-254">Sales.SalesOrderHeader_inmem has three indexes, which are all HASH indexes for performance reasons, and because no ordered or range scans are needed for the workload.</span></span>  
  
-   <span data-ttu-id="e0949-255">(SalesOrderID)의 해시 인덱스: 예상된 판매 주문 수가 1,000만 개이기 때문에 bucket_count의 크기는 1,000만(1,600만으로 반올림됨)으로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-255">HASH index on (SalesOrderID): bucket_count is sized at 10 million (rounded up to 16 million), because the expected number of sales orders is 10 million</span></span>  
  
-   <span data-ttu-id="e0949-256">(SalesPersonID)의 해시 인덱스: bucket_count가 100만입니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-256">HASH index on (SalesPersonID): bucket_count is 1 million.</span></span> <span data-ttu-id="e0949-257">제공된 데이터 세트에는 많은 영업 사원이 없지만, 이후 성장을 허용할 수 있으며 bucket_count의 크기가 과도하게 설정된 경우 포인트 조회에 대한 성능 저하가 발생하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-257">The data set provided does not have a lot of sales persons, but this allows for future growth, plus you don't pay a performance penalty for point lookups if the bucket_count is oversized.</span></span>  
  
-   <span data-ttu-id="e0949-258">(CustomerID)의 해시 인덱스: bucket_count가 100만입니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-258">HASH index on (CustomerID): bucket_count is 1 million.</span></span> <span data-ttu-id="e0949-259">제공된 데이터 집합에는 많은 고객이 없지만 이후 성장을 허용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-259">The data set provided does not have a lot of customers, but this allows for future growth.</span></span>  
  
 <span data-ttu-id="e0949-260">Sales.SalesOrderDetail_inmem에는 세 가지 인덱스가 있는데 정렬된 검색이나 범위 검색이 작업에 필요하지 않기 때문에 모두 성능상의 이유로 해시 인덱스입니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-260">Sales.SalesOrderDetail_inmem has three indexes, which are all HASH indexes for performance reasons, and because no ordered or range scans are needed for the workload.</span></span>  
  
-   <span data-ttu-id="e0949-261">(SalesOrderID, SalesOrderDetailID)의 해시 인덱스: 기본 키 인덱스이며 (SalesOrderID, SalesOrderDetailID)의 조회가 빈번하지는 않지만 키에 해시 인덱스를 사용하면 행 삽입이 빨라집니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-261">HASH index on (SalesOrderID, SalesOrderDetailID): this is the primary key index, and even though lookups on (SalesOrderID, SalesOrderDetailID) will be infrequent, using a hash index for the key speeds up row inserts.</span></span> <span data-ttu-id="e0949-262">bucket_count 크기 5,000만(6,700만으로 반올림됨): 예상 판매 주문 수가 1,000만 개이므로 이 크기에는 주문당 평균 5개 품목이 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-262">The bucket_count is sized at 50 million (rounded up to 67 million): the expected number of sales orders is 10 million, and this is sized to have an average of 5 items per order</span></span>  
  
-   <span data-ttu-id="e0949-263">(SalesOrderID)의 해시 인덱스: 단일 주문에 해당하는 모든 품목을 찾으려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-263">HASH index on (SalesOrderID): lookups by sales order are frequent: you will want to find all the line items corresponding to a single order.</span></span>  <span data-ttu-id="e0949-264">예상된 판매 주문 수가 1,000만 개이기 때문에 bucket_count의 크기는 1,000만(1,600만으로 반올림됨)으로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-264">bucket_count is sized at 10 million (rounded up to 16 million), because the expected number of sales orders is 10 million</span></span>  
  
-   <span data-ttu-id="e0949-265">(ProductID)의 해시 인덱스: bucket_count가 100만입니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-265">HASH index on (ProductID): bucket_count is 1 million.</span></span> <span data-ttu-id="e0949-266">제공된 데이터 집합에는 많은 제품이 없지만 이후 성장을 허용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-266">The data set provided does not have a lot of product, but this allows for future growth.</span></span>  
  
 <span data-ttu-id="e0949-267">Production.Product_inmem에는 세 가지 인덱스가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-267">Production.Product_inmem has three indexes</span></span>  
  
-   <span data-ttu-id="e0949-268">(ProductID)의 해시 인덱스: ProductID의 조회가 데모 작업의 중요 경로에 있으므로 해시 인덱스가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-268">HASH index on (ProductID): lookups on ProductID are in the critical path for the demo workload, therefore this is a hash index</span></span>  
  
-   <span data-ttu-id="e0949-269">(Name)의 비클러스터형 인덱스: 제품 이름의 정렬된 검색을 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-269">NONCLUSTERED index on (Name): this will allow ordered scans of product names</span></span>  
  
-   <span data-ttu-id="e0949-270">(ProductNumber)의 비클러스터형 인덱스: 제품 번호의 정렬된 검색을 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-270">NONCLUSTERED index on (ProductNumber): this will allow ordered scans of product numbers</span></span>  
  
 <span data-ttu-id="e0949-271">Sales.SpecialOffer_inmem에는 (SpecialOfferID)의 해시 인덱스가 하나 있습니다. 특별 행사의 포인트 조회는 데모 작업의 중요한 부분에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-271">Sales.SpecialOffer_inmem has one HASH index on (SpecialOfferID): point lookups of special offers are in the critical part of the demo workload.</span></span> <span data-ttu-id="e0949-272">bucket_count의 크기는 이후 성장을 허용하기 위해 100만으로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-272">The bucket_count is sized at 1 million to allow for future growth.</span></span>  
  
 <span data-ttu-id="e0949-273">Sales.SpecialOfferProduct_inmem은 데모 작업에서 참조되지 않으므로 작업을 최적화하기 위해 이 테이블에 해시 인덱스를 사용할 명확한 이유가 없습니다. (SpecialOfferID, ProductID) 및 (ProductID)의 인덱스는 비클러스터형 인덱스입니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-273">Sales.SpecialOfferProduct_inmem is not referenced in the demo workload, and thus there is no apparent need to use hash indexes on this table to optimize the workload - the indexes on (SpecialOfferID, ProductID) and (ProductID) are NONCLUSTERED.</span></span>  
  
 <span data-ttu-id="e0949-274">위에서 일부 bucket_counts의 크기는 과도하게 설정되었지만 SalesOrderHeader_inmem 및 SalesOrderDetail_inmem의 인덱스에 대한 bucket_counts의 크기는 1,000만 개의 판매 주문에 대해서만 설정되었습니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-274">Notice that in the above some of the bucket_counts are over-sized, but not the bucket_counts for the indexes on SalesOrderHeader_inmem and SalesOrderDetail_inmem: they are sized for just 10 million sales orders.</span></span> <span data-ttu-id="e0949-275">이는 사용할 수 있는 메모리가 적은 시스템에 예제를 설치할 수 있도록 하기 위해서입니다. 하지만 이러한 경우에 데모 작업은 메모리 부족으로 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-275">This was done to allow installing the sample on systems with low memory availability, although in those cases the demo workload will fail with out-of-memory.</span></span> <span data-ttu-id="e0949-276">1,000만 개가 훨씬 넘는 판매 주문으로 확장하려는 경우 bucket_counts를 그에 맞게 늘리면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-276">If you do want to scale well beyond 10 million sales orders, feel free to increase the bucket counts accordingly.</span></span>  
  
#### <a name="considerations-for-memory-utilization"></a><span data-ttu-id="e0949-277">메모리 사용률에 대한 고려 사항</span><span class="sxs-lookup"><span data-stu-id="e0949-277">Considerations for memory utilization</span></span>  
 <span data-ttu-id="e0949-278">데모 작업을 실행하기 전후에 샘플 데이터베이스의 메모리 사용률은 [메모리 최적화 테이블의 메모리 사용률](#Memoryutilizationforthememory-optimizedtables)섹션에 설명되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-278">Memory utilization in the sample database, both before and after running the demo workload, is discussed in the Section [Memory utilization for the memory-optimized tables](#Memoryutilizationforthememory-optimizedtables).</span></span>  
  
### <a name="stored-procedures-added-by-the-sample"></a><span data-ttu-id="e0949-279">예제에서 추가된 저장 프로시저</span><span class="sxs-lookup"><span data-stu-id="e0949-279">Stored Procedures added by the sample</span></span>  
 <span data-ttu-id="e0949-280">판매 주문을 삽입하고 배송 정보를 업데이트하기 위한 두 가지 주요 저장 프로시저는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-280">The two key stored procedures for inserting sales order and updating shipping details are as follows:</span></span>  
  
-   <span data-ttu-id="e0949-281">Sales.usp_InsertSalesOrder_inmem</span><span class="sxs-lookup"><span data-stu-id="e0949-281">Sales.usp_InsertSalesOrder_inmem</span></span>  
  
    -   <span data-ttu-id="e0949-282">데이터베이스에 새로운 판매 주문을 삽입하고 해당 판매 주문의 SalesOrderID를 출력합니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-282">Inserts a new sales order in the database and outputs the SalesOrderID for that sales order.</span></span> <span data-ttu-id="e0949-283">입력 매개 변수로 판매 주문 머리글의 정보뿐만 아니라 주문의 품목을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-283">As input parameters it takes details for the sales order header, as well as the line items in the order.</span></span>  
  
    -   <span data-ttu-id="e0949-284">출력 매개 변수:</span><span class="sxs-lookup"><span data-stu-id="e0949-284">Output parameter:</span></span>  
  
        -   <span data-ttu-id="e0949-285">@SalesOrderID int – 방금 삽입된 판매 주문의 SalesOrderID</span><span class="sxs-lookup"><span data-stu-id="e0949-285">@SalesOrderID int - the SalesOrderID for the sales order that was just inserted</span></span>  
  
    -   <span data-ttu-id="e0949-286">입력 매개 변수(필수):</span><span class="sxs-lookup"><span data-stu-id="e0949-286">Input parameters (required):</span></span>  
  
        -   <span data-ttu-id="e0949-287">@DueDate datetime2</span><span class="sxs-lookup"><span data-stu-id="e0949-287">@DueDate datetime2</span></span>  
  
        -   <span data-ttu-id="e0949-288">@CustomerID int</span><span class="sxs-lookup"><span data-stu-id="e0949-288">@CustomerID int</span></span>  
  
        -   <span data-ttu-id="e0949-289">@BillToAddressID [int]</span><span class="sxs-lookup"><span data-stu-id="e0949-289">@BillToAddressID [int]</span></span>  
  
        -   <span data-ttu-id="e0949-290">@ShipToAddressID [int]</span><span class="sxs-lookup"><span data-stu-id="e0949-290">@ShipToAddressID [int]</span></span>  
  
        -   <span data-ttu-id="e0949-291">@ShipMethodID [int]</span><span class="sxs-lookup"><span data-stu-id="e0949-291">@ShipMethodID [int]</span></span>  
  
        -   <span data-ttu-id="e0949-292">@SalesOrderDetails Sales.SalesOrderDetailType_inmem – 주문의 품목이 포함된 TVP</span><span class="sxs-lookup"><span data-stu-id="e0949-292">@SalesOrderDetails Sales.SalesOrderDetailType_inmem - TVP that contains the line items of the order</span></span>  
  
    -   <span data-ttu-id="e0949-293">입력 매개 변수(선택적):</span><span class="sxs-lookup"><span data-stu-id="e0949-293">Input parameters (optional):</span></span>  
  
        -   <span data-ttu-id="e0949-294">@Status [tinyint]</span><span class="sxs-lookup"><span data-stu-id="e0949-294">@Status [tinyint]</span></span>  
  
        -   <span data-ttu-id="e0949-295">@OnlineOrderFlag [bit]</span><span class="sxs-lookup"><span data-stu-id="e0949-295">@OnlineOrderFlag [bit]</span></span>  
  
        -   <span data-ttu-id="e0949-296">@PurchaseOrderNumber [nvarchar](25\)</span><span class="sxs-lookup"><span data-stu-id="e0949-296">@PurchaseOrderNumber [nvarchar](25\)</span></span>  
  
        -   <span data-ttu-id="e0949-297">@AccountNumber [nvarchar](15\)</span><span class="sxs-lookup"><span data-stu-id="e0949-297">@AccountNumber [nvarchar](15\)</span></span>  
  
        -   <span data-ttu-id="e0949-298">@SalesPersonID [int]</span><span class="sxs-lookup"><span data-stu-id="e0949-298">@SalesPersonID [int]</span></span>  
  
        -   <span data-ttu-id="e0949-299">@TerritoryID [int]</span><span class="sxs-lookup"><span data-stu-id="e0949-299">@TerritoryID [int]</span></span>  
  
        -   <span data-ttu-id="e0949-300">@CreditCardID [int]</span><span class="sxs-lookup"><span data-stu-id="e0949-300">@CreditCardID [int]</span></span>  
  
        -   <span data-ttu-id="e0949-301">@CreditCardApprovalCode [varchar](15\)</span><span class="sxs-lookup"><span data-stu-id="e0949-301">@CreditCardApprovalCode [varchar](15\)</span></span>  
  
        -   <span data-ttu-id="e0949-302">@CurrencyRateID [int]</span><span class="sxs-lookup"><span data-stu-id="e0949-302">@CurrencyRateID [int]</span></span>  
  
        -   <span data-ttu-id="e0949-303">@Comment nvarchar(128)</span><span class="sxs-lookup"><span data-stu-id="e0949-303">@Comment nvarchar(128)</span></span>  
  
-   <span data-ttu-id="e0949-304">Sales.usp_UpdateSalesOrderShipInfo_inmem</span><span class="sxs-lookup"><span data-stu-id="e0949-304">Sales.usp_UpdateSalesOrderShipInfo_inmem</span></span>  
  
    -   <span data-ttu-id="e0949-305">지정된 판매 주문에 대한 배송 정보를 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-305">Update the shipping information for a given sales order.</span></span> <span data-ttu-id="e0949-306">또한 판매 주문의 모든 품목에 대한 배송 정보도 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-306">This will also update the shipping information for all line items of the sales order.</span></span>  
  
    -   <span data-ttu-id="e0949-307">이 저장 프로시저는 동일한 주문을 업데이트하는 동시 트랜잭션과의 예기치 않은 잠재적 충돌을 처리하는 재시도 논리가 포함된 고유하게 컴파일된 저장 프로시저 Sales.usp_UpdateSalesOrderShipInfo_native의 래퍼 프로시저입니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-307">This is a wrapper procedure for the natively compiled stored procedures Sales.usp_UpdateSalesOrderShipInfo_native with retry logic to deal with (unexpected) potential conflicts with concurrent transactions updating the same order.</span></span> <span data-ttu-id="e0949-308">재시도 논리에 대한 자세한 내용은 [여기](https://technet.microsoft.com/library/dn169141\(v=sql.120\).aspx)에서 온라인 설명서 항목을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e0949-308">For more information about retry logic see the Books Online topic [here](https://technet.microsoft.com/library/dn169141\(v=sql.120\).aspx).</span></span>  
  
-   <span data-ttu-id="e0949-309">Sales.usp_UpdateSalesOrderShipInfo_native</span><span class="sxs-lookup"><span data-stu-id="e0949-309">Sales.usp_UpdateSalesOrderShipInfo_native</span></span>  
  
    -   <span data-ttu-id="e0949-310">배송 정보 업데이트를 실제로 처리하는 고유하게 컴파일된 저장 프로시저입니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-310">This is the natively compiled stored procedure that actually processes the update to the shipping information.</span></span> <span data-ttu-id="e0949-311">래퍼 저장 프로시저 Sales.usp_UpdateSalesOrderShipInfo_inmem에서 호출되기 위한 수단입니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-311">It is means to be called from the wrapper stored procedure Sales.usp_UpdateSalesOrderShipInfo_inmem.</span></span> <span data-ttu-id="e0949-312">클라이언트가 오류를 처리하고 재시도 논리를 구현할 수 있는 경우 래퍼 저장 프로시저를 사용하지 않고 이 프로시저를 직접 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-312">If the client can deal with failures and implements retry logic, you can call this procedure directly, rather than using the wrapper stored procedure.</span></span>  
  
 <span data-ttu-id="e0949-313">다음 저장 프로시저는 데모 작업에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-313">The following stored procedure is used for the demo workload.</span></span>  
  
-   <span data-ttu-id="e0949-314">Demo.usp_DemoReset</span><span class="sxs-lookup"><span data-stu-id="e0949-314">Demo.usp_DemoReset</span></span>  
  
    -   <span data-ttu-id="e0949-315">SalesOrderHeader 및 SalesOrderDetail 테이블을 비우고 초기값을 다시 설정하여 데모를 다시 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-315">Resets the demo by emptying and reseeding the SalesOrderHeader and SalesOrderDetail tables.</span></span>  
  
 <span data-ttu-id="e0949-316">다음 저장 프로시저는 도메인 및 참조 무결성을 보장하면서 메모리 최적화 테이블에서 삽입하고 삭제하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-316">The following stored procedures are used for inserting in and deleting from memory-optimized tables while guaranteeing domain and referential integrity.</span></span>  
  
-   <span data-ttu-id="e0949-317">Production.usp_InsertProduct_inmem</span><span class="sxs-lookup"><span data-stu-id="e0949-317">Production.usp_InsertProduct_inmem</span></span>  
  
-   <span data-ttu-id="e0949-318">Production.usp_DeleteProduct_inmem</span><span class="sxs-lookup"><span data-stu-id="e0949-318">Production.usp_DeleteProduct_inmem</span></span>  
  
-   <span data-ttu-id="e0949-319">Sales.usp_InsertSpecialOffer_inmem</span><span class="sxs-lookup"><span data-stu-id="e0949-319">Sales.usp_InsertSpecialOffer_inmem</span></span>  
  
-   <span data-ttu-id="e0949-320">Sales.usp_DeleteSpecialOffer_inmem</span><span class="sxs-lookup"><span data-stu-id="e0949-320">Sales.usp_DeleteSpecialOffer_inmem</span></span>  
  
-   <span data-ttu-id="e0949-321">Sales.usp_InsertSpecialOfferProduct_inmem</span><span class="sxs-lookup"><span data-stu-id="e0949-321">Sales.usp_InsertSpecialOfferProduct_inmem</span></span>  
  
 <span data-ttu-id="e0949-322">마지막으로 다음 저장 프로시저는 도메인 및 참조 무결성을 확인하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-322">Finally the following stored procedure is used to verify domain and referential integrity.</span></span>  
  
1.  <span data-ttu-id="e0949-323">dbo.usp_ValidateIntegrity</span><span class="sxs-lookup"><span data-stu-id="e0949-323">dbo.usp_ValidateIntegrity</span></span>  
  
    -   <span data-ttu-id="e0949-324">선택적 매개 변수: @object_id – 무결성을 확인할 개체의 ID.</span><span class="sxs-lookup"><span data-stu-id="e0949-324">Optional parameter: @object_id - ID of the object to validate integrity for</span></span>  
  
    -   <span data-ttu-id="e0949-325">이 프로시저는 확인되어야 하는 무결성 규칙에 대해 dbo.DomainIntegrity, dbo.ReferentialIntegrity 및 dbo.UniqueIntegrity 테이블에 의존합니다. 예제에서는 이러한 테이블을 AdventureWorks 데이터베이스의 원래 테이블에 존재하는 CHECK, FOREIGN KEY 및 UNIQUE 제약 조건을 기반으로 채웁니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-325">This procedure relies on the tables dbo.DomainIntegrity, dbo.ReferentialIntegrity, and dbo.UniqueIntegrity for the integrity rules that need to be verified - the sample populates these tables based on the check, foreign key, and unique constraints that exist for the original tables in the AdventureWorks database.</span></span>  
  
    -   <span data-ttu-id="e0949-326">이 프로시저는 도우미 프로시저 dbo.usp_GenerateCKCheck, dbo.usp_GenerateFKCheck 및 dbo.GenerateUQCheck에 의존하여 무결성 검사를 수행하는 데 필요한 T-SQL을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-326">It relies on the helper procedures dbo.usp_GenerateCKCheck, dbo.usp_GenerateFKCheck, and dbo.GenerateUQCheck to generate the T-SQL needed for performing the integrity checks.</span></span>  
  
##  <a name="performance-measurements-using-the-demo-workload"></a><a name="PerformanceMeasurementsusingtheDemoWorkload"></a> <span data-ttu-id="e0949-327">데모 작업을 사용한 성능 측정</span><span class="sxs-lookup"><span data-stu-id="e0949-327">Performance Measurements using the Demo Workload</span></span>  
 <span data-ttu-id="e0949-328">ostress는 [!INCLUDE[msCoName](../includes/msconame-md.md)] CSS [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 지원 팀에서 개발한 명령줄 도구입니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-328">Ostress is a command-line tool that was developed by the [!INCLUDE[msCoName](../includes/msconame-md.md)] CSS [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] support team.</span></span> <span data-ttu-id="e0949-329">이 도구는 쿼리를 실행하거나 저장 프로시저를 병렬로 실행하는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-329">This tool can be used to execute queries or run stored procedures in parallel.</span></span> <span data-ttu-id="e0949-330">지정된 T-SQL 문을 병렬로 실행할 스레드 수를 구성할 수 있으며 해당 스레드에서 문이 실행될 횟수를 지정할 수 있습니다. ostress는 스레드를 시작하고 모든 스레드에서 문을 병렬로 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-330">You can configure the number of threads to run a given T-SQL statement in parallel, and you can specify how many times the statement should be executed on this thread; ostress will spin up the threads and execute the statement on all threads in parallel.</span></span> <span data-ttu-id="e0949-331">모든 스레드의 실행이 완료된 후 ostress는 모든 스레드의 실행이 완료되는 데 걸린 시간을 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-331">After execution finishes for all threads, ostress will report the time taken for all threads to finish execution.</span></span>  
  
### <a name="installing-ostress"></a><span data-ttu-id="e0949-332">ostress 설치</span><span class="sxs-lookup"><span data-stu-id="e0949-332">Installing ostress</span></span>  
 <span data-ttu-id="e0949-333">ostress는 RML 유틸리티의 일부로 설치되며 ostress의 독립 실행형 설치는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-333">Ostress is installed as part of the RML Utilities; there is no standalone installation for ostress.</span></span>  
  
 <span data-ttu-id="e0949-334">설치 단계:</span><span class="sxs-lookup"><span data-stu-id="e0949-334">Installation steps:</span></span>  
  
1.  <span data-ttu-id="e0949-335">다음 페이지에서 RML 유틸리티에 대 한 x64 설치 패키지를 다운로드 하 여 실행 합니다.[https://blogs.msdn.com/b/psssql/archive/2013/10/29/cumulative-update-2-to-the-rml-utilities-for-microsoft-sql-server-released.aspx](https://blogs.msdn.com/b/psssql/archive/2013/10/29/cumulative-update-2-to-the-rml-utilities-for-microsoft-sql-server-released.aspx)</span><span class="sxs-lookup"><span data-stu-id="e0949-335">Download and run the x64 installation package for the RML utilities from the following page: [https://blogs.msdn.com/b/psssql/archive/2013/10/29/cumulative-update-2-to-the-rml-utilities-for-microsoft-sql-server-released.aspx](https://blogs.msdn.com/b/psssql/archive/2013/10/29/cumulative-update-2-to-the-rml-utilities-for-microsoft-sql-server-released.aspx)</span></span>  
  
2.  <span data-ttu-id="e0949-336">특정 파일이 사용 중이라는 대화 상자가 나타나면 'Continue'를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-336">If there is a dialog box saying certain files are in use, click 'Continue'</span></span>  
  
### <a name="running-ostress"></a><span data-ttu-id="e0949-337">ostress 실행</span><span class="sxs-lookup"><span data-stu-id="e0949-337">Running ostress</span></span>  
 <span data-ttu-id="e0949-338">ostress는 명령줄 프롬프트에서 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-338">Ostress is run from the command-line prompt.</span></span> <span data-ttu-id="e0949-339">RML 유틸리티의 일부로 설치되는 "RML Cmd Prompt"에서 도구를 실행하는 것이 가장 간편합니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-339">It is most convenient to run the tool from the "RML Cmd Prompt", which is installed as part of the RML Utilities.</span></span>  
  
 <span data-ttu-id="e0949-340">RML Cmd Prompt를 열려면 다음 지침을 따르세요.</span><span class="sxs-lookup"><span data-stu-id="e0949-340">To open the RML Cmd Prompt follow these instructions:</span></span>  
  
 <span data-ttu-id="e0949-341">Windows Server 2012 [R2]와 Windows 8 및 8.1에서 Windows 키를 클릭하여 시작 메뉴를 열고 'rml'을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-341">In Windows Server 2012 [R2] and in Windows 8 and 8.1, open the start menu by clicking the Windows key, and type 'rml'.</span></span> <span data-ttu-id="e0949-342">검색 결과의 목록에 있는 “RML Cmd Prompt”를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-342">Click on "RML Cmd Prompt", which will be in the list of search results.</span></span>  
  
 <span data-ttu-id="e0949-343">명령 프롬프트가 RML 유틸리티 설치 폴더에 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-343">Ensure that the command prompt is located in the RML Utilities installation folder.</span></span> <span data-ttu-id="e0949-344">예:</span><span class="sxs-lookup"><span data-stu-id="e0949-344">For example:</span></span>  
  
 ![](../../2014/database-engine/media/SQLServer2014RTMIn-MemoryOLTP01.jpg)  
  
 <span data-ttu-id="e0949-345">ostress의 명령줄 옵션은 명령줄 옵션 없이 ostress.exe를 실행하기만 하면 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-345">The command-line options for ostress can be seen when simply running ostress.exe without any command-line options.</span></span> <span data-ttu-id="e0949-346">이 예제와 함께 ostress를 실행하기 위해 고려할 기본 옵션은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-346">The main options to consider for running ostress with this sample are:</span></span>  
  
-   <span data-ttu-id="e0949-347">-S 연결할 [!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 인스턴스의 이름</span><span class="sxs-lookup"><span data-stu-id="e0949-347">-S name of [!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] instance to connect to</span></span>  
  
-   <span data-ttu-id="e0949-348">-E Windows 인증을 사용 하 여 연결 (기본값); 인증을 사용 하는 경우에는 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 옵션과-P 옵션을 사용 하 여 사용자 이름과 암호를 각각 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-348">-E use Windows authentication to connect (default); if you use [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] authentication, use the options -U and -P to specify the username and password, respectively</span></span>  
  
-   <span data-ttu-id="e0949-349">-d 데이터베이스의 이름. 이 예의 경우 AdventureWorks2014입니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-349">-d name of the database, for this example AdventureWorks2014</span></span>  
  
-   <span data-ttu-id="e0949-350">-Q 실행될 T-SQL 문</span><span class="sxs-lookup"><span data-stu-id="e0949-350">-Q the T-SQL statement to be executed</span></span>  
  
-   <span data-ttu-id="e0949-351">-n 각 입력 파일/쿼리를 처리하는 연결의 수</span><span class="sxs-lookup"><span data-stu-id="e0949-351">-n number of connections processing each input file/query</span></span>  
  
-   <span data-ttu-id="e0949-352">-r 각 연결에서 각 입력 파일/쿼리를 실행할 반복 횟수</span><span class="sxs-lookup"><span data-stu-id="e0949-352">-r the number of iterations for each connection to execute each input file/query</span></span>  
  
### <a name="demo-workload"></a><span data-ttu-id="e0949-353">데모 작업</span><span class="sxs-lookup"><span data-stu-id="e0949-353">Demo Workload</span></span>  
 <span data-ttu-id="e0949-354">데모 작업에서 사용되는 기본 저장 프로시저는 Sales.usp_InsertSalesOrder_inmem/ondisk입니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-354">The main stored procedure used in the demo workload is Sales.usp_InsertSalesOrder_inmem/ondisk.</span></span> <span data-ttu-id="e0949-355">아래의 스크립트는 예제 데이터로 TVP(테이블 반환 매개 변수)를 생성하고 프로시저를 호출하여 품목이 5개인 판매 주문을 삽입합니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-355">The script in the below constructs a table-valued parameter (TVP) with sample data, and calls the procedure to insert a sales order with 5 line items.</span></span>  
  
 <span data-ttu-id="e0949-356">ostress 도구는 저장 프로시저 호출을 병렬로 실행하여 판매 주문을 동시에 삽입하는 클라이언트를 시뮬레이트하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-356">The ostress tool is used to execute the stored procedure calls in parallel, to simulate clients inserting sales orders concurrently.</span></span>  
  
 <span data-ttu-id="e0949-357">ostress 실행이 끝날 때마다 Demo.usp_DemoReset을 실행하여 데모를 다시 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-357">Reset the demo after each stress run executing Demo.usp_DemoReset.</span></span> <span data-ttu-id="e0949-358">이 프로시저는 메모리 최적화 테이블의 행을 삭제하고, 디스크 기반 테이블을 자르며, 데이터베이스 검사점을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-358">This procedure deletes the rows in the memory-optimized tables, truncates the disk-based tables, and executes a database checkpoint.</span></span>  
  
 <span data-ttu-id="e0949-359">다음 스크립트는 판매 주문 처리 작업을 시뮬레이트하기 위해 동시에 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-359">The following script is executed concurrently to simulate a sales order processing workload:</span></span>  
  
```  
DECLARE   
      @i int = 0,   
      @od Sales.SalesOrderDetailType_inmem,   
      @SalesOrderID int,   
      @DueDate datetime2 = sysdatetime(),   
      @CustomerID int = rand() * 8000,   
      @BillToAddressID int = rand() * 10000,   
      @ShipToAddressID int = rand() * 10000,   
      @ShipMethodID int = (rand() * 5) + 1;   
  
INSERT INTO @od   
SELECT OrderQty, ProductID, SpecialOfferID   
FROM Demo.DemoSalesOrderDetailSeed   
WHERE OrderID= cast((rand()*106) + 1 as int);   
  
WHILE (@i < 20)   
BEGIN;   
      EXEC Sales.usp_InsertSalesOrder_inmem @SalesOrderID OUTPUT, @DueDate, @CustomerID, @BillToAddressID, @ShipToAddressID, @ShipMethodID, @od;   
      SET @i += 1   
END  
  
```  
  
 <span data-ttu-id="e0949-360">이 스크립트를 사용하면 생성된 각 예제 주문이 WHILE 루프에서 실행되는 20개의 저장 프로시저를 통해 20회 삽입됩니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-360">With this script, each sample order that is constructed is inserted 20 times, through 20 stored procedures executed in a WHILE loop.</span></span> <span data-ttu-id="e0949-361">루프는 데이터베이스가 예제 주문을 생성하는 데 사용된다는 사실을 보완하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-361">The loop is used to account for the fact that the database is used to construct the sample order.</span></span> <span data-ttu-id="e0949-362">일반적인 프로덕션 환경에서는 중간 계층 애플리케이션이 삽입될 판매 주문을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-362">In typical production environments, the mid-tier application will construct the sales order to be inserted.</span></span>  
  
 <span data-ttu-id="e0949-363">위의 스크립트는 판매 주문을 메모리 최적화 테이블에 삽입합니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-363">The above script inserts sales orders into memory-optimized tables.</span></span> <span data-ttu-id="e0949-364">판매 주문을 디스크 기반 테이블에 삽입하는 스크립트는 두 ‘_inmem’을 ‘_ondisk’로 바꿔서 파생됩니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-364">The script to insert sales orders into disk-based tables is derived by replacing the two occurrences of '_inmem' with '_ondisk'.</span></span>  
  
 <span data-ttu-id="e0949-365">ostress 도구를 사용하여 여러 동시 연결을 통해 스크립트를 실행할 것입니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-365">We will use the ostress tool to execute the scripts using several concurrent connections.</span></span> <span data-ttu-id="e0949-366">‘-n’ 매개 변수를 사용하여 연결 수를 제어하고 ‘r’ 매개 변수를 사용하여 스크립트가 각 연결에서 실행되는 횟수를 제어하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-366">We will use the parameter '-n' to control the number of connections, and the parameter 'r' to control how many times the script is executed on each connection.</span></span>  
  
#### <a name="functional-validation-of-the-workload"></a><span data-ttu-id="e0949-367">작업의 기능 유효성 검사</span><span class="sxs-lookup"><span data-stu-id="e0949-367">Functional Validation of the Workload</span></span>  
 <span data-ttu-id="e0949-368">모든 것이 제대로 작동 하는지 확인 하기 위해 샘플 테스트를 시작 하 고, 10 개의 동시 연결 및 5 개의 반복을 사용 하 여 총 10 \* 5 \* 20 = 1000 판매 주문을 삽입 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-368">To verify everything works, we will start with a sample test, using 10 concurrent connects and 5 iterations, inserting a total of 10 \* 5 \* 20 = 1000 sales order.</span></span>  
  
 <span data-ttu-id="e0949-369">아래의 명령을 사용할 때 로컬 컴퓨터에서 기본 인스턴스를 사용한다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-369">With the below command we assume using the default instance on the local machine.</span></span> <span data-ttu-id="e0949-370">명명된 인스턴스나 원격 서버를 사용하는 경우 -S 매개 변수를 사용하여 서버 이름을 적절하게 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-370">If you are using a named instance or using a remote server, change the server name accordingly, using the parameter -S.</span></span>  
  
 <span data-ttu-id="e0949-371">RML Cmd Prompt에서 다음 명령을 사용하여 메모리 최적화 테이블에 1000개의 판매 주문을 삽입합니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-371">Insert 1000 sales orders in memory-optimized tables use the following command in the RML Cmd Prompt:</span></span>  
  
 <span data-ttu-id="e0949-372">복사 단추를 클릭하여 명령을 복사하고 RML 유틸리티 명령 프롬프트에 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-372">Click the Copy button to copy the command, and paste it into the RML Utilities command prompt.</span></span>  
  
```  
ostress.exe -n10 -r5 -S. -E -dAdventureWorks2014 -q -Q"DECLARE @i int = 0, @od Sales.SalesOrderDetailType_inmem, @SalesOrderID int, @DueDate datetime2 = sysdatetime(), @CustomerID int = rand() * 8000, @BillToAddressID int = rand() * 10000, @ShipToAddressID int = rand() * 10000, @ShipMethodID int = (rand() * 5) + 1; INSERT INTO @od SELECT OrderQty, ProductID, SpecialOfferID FROM Demo.DemoSalesOrderDetailSeed WHERE OrderID= cast((rand()*106) + 1 as int); while (@i < 20) begin; EXEC Sales.usp_InsertSalesOrder_inmem @SalesOrderID OUTPUT, @DueDate, @CustomerID, @BillToAddressID, @ShipToAddressID, @ShipMethodID, @od; set @i += 1 end"  
```  
  
 <span data-ttu-id="e0949-373">모든 것이 예상대로 작동하는 경우 명령 창은 다음과 유사합니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-373">If everything works as expected, your command window will look similar to the following.</span></span> <span data-ttu-id="e0949-374">오류 메시지는 예상되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-374">Error messages are not expected.</span></span>  
  
 ![](../../2014/database-engine/media/SQLServer2014RTMIn-MemoryOLTP02.jpg)  
  
 <span data-ttu-id="e0949-375">RML Cmd Prompt에서 다음 명령을 실행하여 디스크 기반 테이블의 경우에도 작업이 예상대로 작동하는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-375">Validate that also the workload functions as expected for disk-based tables by running the following command in the RML Cmd Prompt:</span></span>  
  
 <span data-ttu-id="e0949-376">복사 단추를 클릭하여 명령을 복사하고 RML 유틸리티 명령 프롬프트에 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-376">Click the Copy button to copy the command, and paste it into the RML Utilities command prompt.</span></span>  
  
```  
ostress.exe -n10 -r5 -S. -E -dAdventureWorks2014 -q -Q"DECLARE @i int = 0, @od Sales.SalesOrderDetailType_ondisk, @SalesOrderID int, @DueDate datetime2 = sysdatetime(), @CustomerID int = rand() * 8000, @BillToAddressID int = rand() * 10000, @ShipToAddressID int = rand() * 10000, @ShipMethodID int = (rand() * 5) + 1; INSERT INTO @od SELECT OrderQty, ProductID, SpecialOfferID FROM Demo.DemoSalesOrderDetailSeed WHERE OrderID= cast((rand()*106) + 1 as int); while (@i < 20) begin; EXEC Sales.usp_InsertSalesOrder_ondisk @SalesOrderID OUTPUT, @DueDate, @CustomerID, @BillToAddressID, @ShipToAddressID, @ShipMethodID, @od; set @i += 1 end"  
```  
  
#### <a name="running-the-workload"></a><span data-ttu-id="e0949-377">작업 실행</span><span class="sxs-lookup"><span data-stu-id="e0949-377">Running the Workload</span></span>  
 <span data-ttu-id="e0949-378">최대 규모로 테스트하기 위해 100개의 연결을 사용하여 1,000만 개의 판매 주문을 삽입합니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-378">To test at scale we insert 10 million sales orders, using 100 connections.</span></span> <span data-ttu-id="e0949-379">이 테스트는 일반 서버(예: 물리적 코어 8개, 논리적 코어 16개)와 로그용 기본 SSD 스토리지에서 문제 없이 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-379">This test performs reasonably on a modest server (e.g., 8 physical, 16 logical cores), and basic SSD storage for the log.</span></span> <span data-ttu-id="e0949-380">테스트가 사용자의 하드웨어에서 제대로 실행되지 않는 경우 [느리게 실행되는 테스트 문제 해결](#Troubleshootingslow-runningtests) 섹션을 참조하세요. 이 테스트에 대한 스트레스 수준을 줄이려면 '-n' 매개 변수를 변경하여 연결 수를 줄입니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-380">If the test does not perform well on your hardware, take look at the Section [Troubleshooting slow-running tests](#Troubleshootingslow-runningtests).If you want to reduce the level of stress for this test, lower the number of connections by changing the parameter '-n'.</span></span> <span data-ttu-id="e0949-381">예를 들어 연결 수를 40으로 줄이려면 ‘-n100’ 매개 변수를 ‘-n40’으로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-381">For example to lower the connection count to 40, change the parameter '-n100' to '-n40'.</span></span>  
  
 <span data-ttu-id="e0949-382">작업에 대한 성능 측정으로 작업을 실행한 후 ostress.exe에서 보고하는 경과 시간을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-382">As a performance measure for the workload we use the elapsed time as reported by ostress.exe after running the workload.</span></span>  
  
##### <a name="memory-optimized-tables"></a><span data-ttu-id="e0949-383">메모리 최적화 테이블</span><span class="sxs-lookup"><span data-stu-id="e0949-383">Memory-optimized tables</span></span>  
 <span data-ttu-id="e0949-384">메모리 최적화 테이블에서 작업을 실행하는 것부터 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-384">We will start by running the workload on memory-optimized tables.</span></span> <span data-ttu-id="e0949-385">다음 명령은 각각 5,000회의 반복을 위해 실행되는 100개의 스레드를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-385">The following command opens 100 threads, each running for 5,000 iterations.</span></span>  <span data-ttu-id="e0949-386">각 반복에서는 별도의 트랜잭션에서 20개의 판매 주문을 삽입합니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-386">Each iteration inserts 20 sales orders in separate transactions.</span></span> <span data-ttu-id="e0949-387">데이터베이스가 삽입될 데이터를 생성하는 데 사용된다는 사실을 보완하기 위해 반복당 20개의 삽입이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-387">There are 20 inserts per iteration to compensate for the fact that the database is used to generate the data to be inserted.</span></span> <span data-ttu-id="e0949-388">이에 따라 총 20 \* 5,000 \* 100 = 10,000,000개의 판매 주문 삽입이 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-388">This yield a total of 20 \* 5,000 \* 100 = 10,000,000 sales order inserts.</span></span>  
  
 <span data-ttu-id="e0949-389">RML Cmd Prompt를 열고 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-389">Open the RML Cmd Prompt, and execute the following command:</span></span>  
  
 <span data-ttu-id="e0949-390">복사 단추를 클릭하여 명령을 복사하고 RML 유틸리티 명령 프롬프트에 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-390">Click the Copy button to copy the command, and paste it into the RML Utilities command prompt.</span></span>  
  
```  
ostress.exe -n100 -r5000 -S. -E -dAdventureWorks2014 -q -Q"DECLARE @i int = 0, @od Sales.SalesOrderDetailType_inmem, @SalesOrderID int, @DueDate datetime2 = sysdatetime(), @CustomerID int = rand() * 8000, @BillToAddressID int = rand() * 10000, @ShipToAddressID int = rand() * 10000, @ShipMethodID int = (rand() * 5) + 1; INSERT INTO @od SELECT OrderQty, ProductID, SpecialOfferID FROM Demo.DemoSalesOrderDetailSeed WHERE OrderID= cast((rand()*106) + 1 as int); while (@i < 20) begin; EXEC Sales.usp_InsertSalesOrder_inmem @SalesOrderID OUTPUT, @DueDate, @CustomerID, @BillToAddressID, @ShipToAddressID, @ShipMethodID, @od; set @i += 1 end"  
```  
  
 <span data-ttu-id="e0949-391">물리적 코어가 총 8개(논리적 코어 총 16개)인 테스트 서버에서 이 작업은 2분 5초가 소요되었고,</span><span class="sxs-lookup"><span data-stu-id="e0949-391">On one test server with a total number of 8 physical (16 logical) cores, this took 2 minutes and 5 seconds.</span></span> <span data-ttu-id="e0949-392">물리적 코어가 24개(논리적 코어 48개)인 두 번째 테스트 서버에서는 1분 0초가 소요되었습니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-392">On a second test server with 24 physical (48 logical) cores, this took 1 minute and 0 seconds.</span></span>  
  
 <span data-ttu-id="e0949-393">작업 관리자 등을 사용하여 작업이 실행되는 동안 CPU 사용률을 관찰합니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-393">Observe the CPU utilization while the workload is running, for example using task manager.</span></span> <span data-ttu-id="e0949-394">CPU 사용률이 100%에 가깝게 나타나는 것을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-394">You will see that CPU utilization is close to 100%.</span></span> <span data-ttu-id="e0949-395">그렇지 않은 경우에는 로그 IO 병목 상태가 발생한 것입니다. [느리게 실행되는 테스트 문제 해결](#Troubleshootingslow-runningtests)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e0949-395">If this is not the case, you have a log IO bottleneck see also [Troubleshooting slow-running tests](#Troubleshootingslow-runningtests).</span></span>  
  
##### <a name="disk-based-tables"></a><span data-ttu-id="e0949-396">디스크 기반 테이블</span><span class="sxs-lookup"><span data-stu-id="e0949-396">Disk-based tables</span></span>  
 <span data-ttu-id="e0949-397">다음 명령은 디스크 기반 테이블에서 작업을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-397">The following command will run the workload on disk-based tables.</span></span> <span data-ttu-id="e0949-398">이 작업은 실행되는 데 시간이 걸릴 수 있는데 그 이유는 대부분 시스템의 래치 경합 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-398">Note that this workload may take a while to execute, which is largely due to latch contention in the system.</span></span> <span data-ttu-id="e0949-399">메모리 액세스에 최적화된 테이블은 래치를 사용하지 않으므로 이 문제의 영향을 받지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-399">Memory-optimized table are latch-free and thus do not suffer from this problem.</span></span>  
  
 <span data-ttu-id="e0949-400">RML Cmd Prompt를 열고 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-400">Open the RML Cmd Prompt, and execute the following command:</span></span>  
  
 <span data-ttu-id="e0949-401">복사 단추를 클릭하여 명령을 복사하고 RML 유틸리티 명령 프롬프트에 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-401">Click the Copy button to copy the command, and paste it into the RML Utilities command prompt.</span></span>  
  
```  
ostress.exe -n100 -r5000 -S. -E -dAdventureWorks2014 -q -Q"DECLARE @i int = 0, @od Sales.SalesOrderDetailType_ondisk, @SalesOrderID int, @DueDate datetime2 = sysdatetime(), @CustomerID int = rand() * 8000, @BillToAddressID int = rand() * 10000, @ShipToAddressID int = rand() * 10000, @ShipMethodID int = (rand() * 5) + 1; INSERT INTO @od SELECT OrderQty, ProductID, SpecialOfferID FROM Demo.DemoSalesOrderDetailSeed WHERE OrderID= cast((rand()*106) + 1 as int); while (@i < 20) begin; EXEC Sales.usp_InsertSalesOrder_ondisk @SalesOrderID OUTPUT, @DueDate, @CustomerID, @BillToAddressID, @ShipToAddressID, @ShipMethodID, @od; set @i += 1 end"  
```  
  
 <span data-ttu-id="e0949-402">물리적 코어가 총 8개(논리적 코어 총 16개)인 테스트 서버에서 이 작업은 41분 25초가 소요되었고,</span><span class="sxs-lookup"><span data-stu-id="e0949-402">On one test server with a total number of 8 physical (16 logical) cores, this took 41 minutes and 25 seconds.</span></span> <span data-ttu-id="e0949-403">물리적 코어가 24개(논리적 코어 48개)인 두 번째 테스트 서버에서는 52분 16초가 소요되었습니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-403">On a second test server with 24 physical (48 logical) cores, this took 52 minutes and 16 seconds.</span></span>  
  
 <span data-ttu-id="e0949-404">이 테스트에서 메모리 최적화 테이블과 디스크 기반 테이블 간 성능 차이의 주요 요인은 디스크 기반 테이블을 사용하는 경우 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]에서 CPU를 완전히 활용할 수 없다는 사실입니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-404">The main factor in the performance difference between memory-optimized tables and disk-based tables in this test is the fact that when using disk-based tables, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] cannot not fully utilize the CPU.</span></span> <span data-ttu-id="e0949-405">그 이유는 래치 경합 때문입니다. 즉, 동시 트랜잭션이 동일한 데이터 페이지에 쓰려고 합니다. 래치는 한 번에 한 트랜잭션만 페이지에 쓸 수 있도록 하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-405">The reason is latch contention: concurrent transactions are attempting to write to the same data page; latches are used to ensure only one transaction at a time can write to a page.</span></span> <span data-ttu-id="e0949-406">[!INCLUDE[hek_2](../includes/hek-2-md.md)] 엔진은 래치를 사용하지 않으며 데이터 행이 페이지에 구성되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-406">The [!INCLUDE[hek_2](../includes/hek-2-md.md)] engine is latch-free, and data rows are not organized in pages.</span></span> <span data-ttu-id="e0949-407">따라서 동시 트랜잭션이 서로의 삽입을 차단 하지 않기 때문에에서 CPU를 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 완전히 활용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-407">Thus, concurrent transactions do not block each other's inserts, thus enabling [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] to fully utilize the CPU.</span></span>  
  
 <span data-ttu-id="e0949-408">작업 관리자 등을 사용하여 작업이 실행되는 동안 CPU 사용률을 관찰할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-408">You can observe the CPU utilization while the workload is running, for example using task manager.</span></span> <span data-ttu-id="e0949-409">디스크 기반 테이블을 사용하는 경우 CPU 사용률이 100%에 크게 못 미치는 것을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-409">You will see with disk-based tables the CPU utilization is far from 100%.</span></span> <span data-ttu-id="e0949-410">논리적 프로세서가 16개인 테스트 구성에서 사용률은 24% 정도입니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-410">On a test configuration with 16 logical processors, the utilization would hover around 24%.</span></span>  
  
 <span data-ttu-id="e0949-411">필요에 따라 성능 모니터를 사용하여 성능 카운터 ‘\SQL Server:Latches\Latch Waits/sec’를 통해 초당 래치 대기 수를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-411">Optionally, you can view the number of latch waits per second using Performance Monitor, with the performance counter '\SQL Server:Latches\Latch Waits/sec'.</span></span>  
  
#### <a name="resetting-the-demo"></a><span data-ttu-id="e0949-412">데모 다시 설정</span><span class="sxs-lookup"><span data-stu-id="e0949-412">Resetting the demo</span></span>  
 <span data-ttu-id="e0949-413">데모를 다시 설정하려면 RML Cmd Prompt를 열고 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-413">To reset the demo, open the RML Cmd Prompt, and execute the following command:</span></span>  
  
```  
ostress.exe -S. -E -dAdventureWorks2014 -Q"EXEC Demo.usp_DemoReset"  
```  
  
 <span data-ttu-id="e0949-414">하드웨어에 따라 이 명령이 실행되는 데 몇 분 정도 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-414">Depending on the hardware this may take a few minutes to run.</span></span>  
  
 <span data-ttu-id="e0949-415">데모 실행이 끝날 때마다 다시 설정하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-415">We recommend a reset after every demo run.</span></span> <span data-ttu-id="e0949-416">이 작업이 삽입만 수행하기 때문에 각 실행에서 더 많은 메모리가 사용되므로 메모리 부족을 방지하려면 다시 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-416">Because this workload is insert-only, each run will consume more memory, and thus a reset is required to prevent running out of memory.</span></span> <span data-ttu-id="e0949-417">실행 후 사용되는 메모리 양은 [작업 실행 후 메모리 사용률](#Memoryutilizationafterrunningtheworkload)섹션에 설명되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-417">The amount of memory consumed after a run is discussed in Section [Memory utilization after running the workload](#Memoryutilizationafterrunningtheworkload).</span></span>  
  
###  <a name="troubleshooting-slow-running-tests"></a><a name="Troubleshootingslow-runningtests"></a> <span data-ttu-id="e0949-418">느리게 실행되는 테스트 문제 해결</span><span class="sxs-lookup"><span data-stu-id="e0949-418">Troubleshooting slow-running tests</span></span>  
 <span data-ttu-id="e0949-419">테스트 결과는 일반적으로 하드웨어와 테스트 실행에서 사용되는 동시성 수준에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-419">Test results will typically vary with hardware, and also the level of concurrency used in the test run.</span></span> <span data-ttu-id="e0949-420">결과가 예상과 다른 경우 확인할 몇 가지 사항은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-420">A couple of things to look for if the results are not as expected:</span></span>  
  
-   <span data-ttu-id="e0949-421">동시 트랜잭션 수: 단일 스레드에서 작업을 실행할 때 [!INCLUDE[hek_2](../includes/hek-2-md.md)] 를 사용한 성능 이점은 두 배보다 적을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-421">Number of concurrent transactions: When running the workload on a single thread, performance gain with [!INCLUDE[hek_2](../includes/hek-2-md.md)] will likely be less than 2X.</span></span> <span data-ttu-id="e0949-422">래치 경합은 동시성 수준이 높은 경우에만 큰 문제가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-422">Latch contention is only a big problem if there is a high level of concurrency.</span></span>  
  
-   <span data-ttu-id="e0949-423">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]에서 사용할 수 있는 적은 코어 수: 즉, 동시에 실행되는 트랜잭션이 SQL에서 사용할 수 있는 코어 수만큼만 있을 수 있으므로 시스템에서 동시성 수준이 낮습니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-423">Low number of cores available to [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]: This means there will be a low level of concurrency in the system, as there can only be as many concurrently executing transactions as there are cores available to SQL.</span></span>  
  
    -   <span data-ttu-id="e0949-424">증상: 디스크 기반 테이블에서 작업을 실행할 때 CPU 사용률이 높은 경우 경합이 많다는 의미이며 동시성 부족을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-424">Symptom: if the CPU utilization is high when running the workload on disk-based tables, this means there is not a lot of contention, pointing to a lack of concurrency.</span></span>  
  
-   <span data-ttu-id="e0949-425">로그 드라이브의 속도: 로그 드라이브가 시스템의 트랜잭션 처리량 수준을 유지할 수 없는 경우 워크로드가 로그 IO에서 병목 상태가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-425">Speed of the log drive: If the log drive cannot keep up with the level of transaction throughput in the system, the workload becomes bottlenecked on log IO.</span></span> <span data-ttu-id="e0949-426">[!INCLUDE[hek_2](../includes/hek-2-md.md)]를 사용하는 경우 로깅이 보다 효율적이지만 로그 IO가 병목 상태인 경우 잠재적인 성능 이점이 제한됩니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-426">Although logging is more efficient with [!INCLUDE[hek_2](../includes/hek-2-md.md)], if log IO is a bottleneck, the potential performance gain is limited.</span></span>  
  
    -   <span data-ttu-id="e0949-427">증상: 메모리 최적화 테이블에서 작업을 실행할 때 CPU 사용률이 100%에 가깝지 않거나 변동이 심한 경우 로그 IO 병목 상태가 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-427">Symptom: if the CPU utilization is not close to 100% or is very spiky when running the workload on memory-optimized tables, it is possible there is a log IO bottleneck.</span></span> <span data-ttu-id="e0949-428">이는 리소스 모니터를 열고 로그 드라이브의 큐 길이를 살펴보고 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-428">This can be confirmed by opening Resource Monitor and looking at the queue length for the log drive.</span></span>  
  
##  <a name="memory-and-disk-space-utilization-in-the-sample"></a><a name="MemoryandDiskSpaceUtilizationintheSample"></a> <span data-ttu-id="e0949-429">샘플의 메모리 및 디스크 공간 사용률</span><span class="sxs-lookup"><span data-stu-id="e0949-429">Memory and Disk Space Utilization in the Sample</span></span>  
 <span data-ttu-id="e0949-430">아래에서는 예제 데이터베이스의 메모리 및 디스크 공간 사용률 측면에서 기대하는 것에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-430">In the below we describe what to expect in terms of memory and disk space utilization for the sample database.</span></span> <span data-ttu-id="e0949-431">또한 논리적 코어가 16개인 테스트 서버에서 관찰한 결과도 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-431">We also show the results we have seen in on a test server with 16 logical cores.</span></span>  
  
###  <a name="memory-utilization-for-the-memory-optimized-tables"></a><a name="Memoryutilizationforthememory-optimizedtables"></a> <span data-ttu-id="e0949-432">메모리 최적화 테이블의 메모리 사용률</span><span class="sxs-lookup"><span data-stu-id="e0949-432">Memory utilization for the memory-optimized tables</span></span>  
  
#### <a name="overall-utilization-of-the-database"></a><span data-ttu-id="e0949-433">데이터베이스의 전체 사용률</span><span class="sxs-lookup"><span data-stu-id="e0949-433">Overall utilization of the database</span></span>  
 <span data-ttu-id="e0949-434">다음 쿼리를 사용하여 시스템에서 [!INCLUDE[hek_2](../includes/hek-2-md.md)] 의 총 메모리 사용률을 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-434">The following query can be used to obtain the total memory utilization for [!INCLUDE[hek_2](../includes/hek-2-md.md)] in the system.</span></span>  
  
```  
SELECT type  
   , name  
, pages_kb/1024 AS pages_MB   
FROM sys.dm_os_memory_clerks WHERE type LIKE '%xtp%'  
```  
  
 <span data-ttu-id="e0949-435">데이터베이스를 만든 후의 스냅샷:</span><span class="sxs-lookup"><span data-stu-id="e0949-435">Snapshot after the database has just been created:</span></span>  
  
||||  
|-|-|-|  
|<span data-ttu-id="e0949-436">**type**</span><span class="sxs-lookup"><span data-stu-id="e0949-436">**type**</span></span>|<span data-ttu-id="e0949-437">**name**</span><span class="sxs-lookup"><span data-stu-id="e0949-437">**name**</span></span>|<span data-ttu-id="e0949-438">**pages_MB**</span><span class="sxs-lookup"><span data-stu-id="e0949-438">**pages_MB**</span></span>|  
|<span data-ttu-id="e0949-439">MEMORYCLERK_XTP</span><span class="sxs-lookup"><span data-stu-id="e0949-439">MEMORYCLERK_XTP</span></span>|<span data-ttu-id="e0949-440">기본값</span><span class="sxs-lookup"><span data-stu-id="e0949-440">Default</span></span>|<span data-ttu-id="e0949-441">94</span><span class="sxs-lookup"><span data-stu-id="e0949-441">94</span></span>|  
|<span data-ttu-id="e0949-442">MEMORYCLERK_XTP</span><span class="sxs-lookup"><span data-stu-id="e0949-442">MEMORYCLERK_XTP</span></span>|<span data-ttu-id="e0949-443">DB_ID_5</span><span class="sxs-lookup"><span data-stu-id="e0949-443">DB_ID_5</span></span>|<span data-ttu-id="e0949-444">877</span><span class="sxs-lookup"><span data-stu-id="e0949-444">877</span></span>|  
|<span data-ttu-id="e0949-445">MEMORYCLERK_XTP</span><span class="sxs-lookup"><span data-stu-id="e0949-445">MEMORYCLERK_XTP</span></span>|<span data-ttu-id="e0949-446">기본값</span><span class="sxs-lookup"><span data-stu-id="e0949-446">Default</span></span>|<span data-ttu-id="e0949-447">0</span><span class="sxs-lookup"><span data-stu-id="e0949-447">0</span></span>|  
|<span data-ttu-id="e0949-448">MEMORYCLERK_XTP</span><span class="sxs-lookup"><span data-stu-id="e0949-448">MEMORYCLERK_XTP</span></span>|<span data-ttu-id="e0949-449">기본값</span><span class="sxs-lookup"><span data-stu-id="e0949-449">Default</span></span>|<span data-ttu-id="e0949-450">0</span><span class="sxs-lookup"><span data-stu-id="e0949-450">0</span></span>|  
  
 <span data-ttu-id="e0949-451">기본 메모리 클럭은 시스템 차원의 메모리 구조를 포함하고 있으며 비교적 작습니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-451">The default memory clerks contain system-wide memory structures and are relatively small.</span></span> <span data-ttu-id="e0949-452">사용자 데이터베이스(이 경우 ID 5인 데이터베이스)의 메모리 클럭은 약 900MB입니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-452">The memory clerk for the user database, in this case database with ID 5, is about 900MB.</span></span>  
  
#### <a name="memory-utilization-per-table"></a><span data-ttu-id="e0949-453">테이블당 메모리 사용률</span><span class="sxs-lookup"><span data-stu-id="e0949-453">Memory utilization per table</span></span>  
 <span data-ttu-id="e0949-454">다음 쿼리를 사용하여 개별 테이블과 인덱스의 메모리 사용률을 세부적으로 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-454">The following query can be used to drill down into the memory utilization of the individual tables and their indexes:</span></span>  
  
```  
SELECT object_name(t.object_id) AS [Table Name]  
     , memory_allocated_for_table_kb  
 , memory_allocated_for_indexes_kb  
FROM sys.dm_db_xtp_table_memory_stats dms JOIN sys.tables t   
ON dms.object_id=t.object_id  
WHERE t.type='U'  
```  
  
 <span data-ttu-id="e0949-455">예제를 처음 설치한 경우 이 쿼리의 결과는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-455">The following shows the results of this query for a fresh installation of the sample:</span></span>  
  
||||  
|-|-|-|  
|<span data-ttu-id="e0949-456">**테이블 이름**</span><span class="sxs-lookup"><span data-stu-id="e0949-456">**Table Name**</span></span>|<span data-ttu-id="e0949-457">**memory_allocated_for_table_kb**</span><span class="sxs-lookup"><span data-stu-id="e0949-457">**memory_allocated_for_table_kb**</span></span>|<span data-ttu-id="e0949-458">**memory_allocated_for_indexes_kb**</span><span class="sxs-lookup"><span data-stu-id="e0949-458">**memory_allocated_for_indexes_kb**</span></span>|  
|<span data-ttu-id="e0949-459">SpecialOfferProduct_inmem</span><span class="sxs-lookup"><span data-stu-id="e0949-459">SpecialOfferProduct_inmem</span></span>|<span data-ttu-id="e0949-460">64</span><span class="sxs-lookup"><span data-stu-id="e0949-460">64</span></span>|<span data-ttu-id="e0949-461">3840</span><span class="sxs-lookup"><span data-stu-id="e0949-461">3840</span></span>|  
|<span data-ttu-id="e0949-462">DemoSalesOrderHeaderSeed</span><span class="sxs-lookup"><span data-stu-id="e0949-462">DemoSalesOrderHeaderSeed</span></span>|<span data-ttu-id="e0949-463">1984</span><span class="sxs-lookup"><span data-stu-id="e0949-463">1984</span></span>|<span data-ttu-id="e0949-464">5504</span><span class="sxs-lookup"><span data-stu-id="e0949-464">5504</span></span>|  
|<span data-ttu-id="e0949-465">SalesOrderDetail_inmem</span><span class="sxs-lookup"><span data-stu-id="e0949-465">SalesOrderDetail_inmem</span></span>|<span data-ttu-id="e0949-466">15316</span><span class="sxs-lookup"><span data-stu-id="e0949-466">15316</span></span>|<span data-ttu-id="e0949-467">663552</span><span class="sxs-lookup"><span data-stu-id="e0949-467">663552</span></span>|  
|<span data-ttu-id="e0949-468">DemoSalesOrderDetailSeed</span><span class="sxs-lookup"><span data-stu-id="e0949-468">DemoSalesOrderDetailSeed</span></span>|<span data-ttu-id="e0949-469">64</span><span class="sxs-lookup"><span data-stu-id="e0949-469">64</span></span>|<span data-ttu-id="e0949-470">10432</span><span class="sxs-lookup"><span data-stu-id="e0949-470">10432</span></span>|  
|<span data-ttu-id="e0949-471">SpecialOffer_inmem</span><span class="sxs-lookup"><span data-stu-id="e0949-471">SpecialOffer_inmem</span></span>|<span data-ttu-id="e0949-472">3</span><span class="sxs-lookup"><span data-stu-id="e0949-472">3</span></span>|<span data-ttu-id="e0949-473">8192</span><span class="sxs-lookup"><span data-stu-id="e0949-473">8192</span></span>|  
|<span data-ttu-id="e0949-474">SalesOrderHeader_inmem</span><span class="sxs-lookup"><span data-stu-id="e0949-474">SalesOrderHeader_inmem</span></span>|<span data-ttu-id="e0949-475">7168</span><span class="sxs-lookup"><span data-stu-id="e0949-475">7168</span></span>|<span data-ttu-id="e0949-476">147456</span><span class="sxs-lookup"><span data-stu-id="e0949-476">147456</span></span>|  
|<span data-ttu-id="e0949-477">Product_inmem</span><span class="sxs-lookup"><span data-stu-id="e0949-477">Product_inmem</span></span>|<span data-ttu-id="e0949-478">124</span><span class="sxs-lookup"><span data-stu-id="e0949-478">124</span></span>|<span data-ttu-id="e0949-479">12352</span><span class="sxs-lookup"><span data-stu-id="e0949-479">12352</span></span>|  
  
 <span data-ttu-id="e0949-480">보시다시피 테이블은 상당히 작습니다. SalesOrderHeader_inmem은 약 7MB이고, SalesOrderDetail_inmem은 약 15MB입니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-480">As you can see the tables are fairly small: SalesOrderHeader_inmem is about 7MB, and SalesOrderDetail_inmem is about 15MB in size.</span></span>  
  
 <span data-ttu-id="e0949-481">여기에서 눈에 띄는 것은 테이블 데이터의 크기와 비교할 때 인덱스에 할당된 메모리의 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-481">What is striking here is the size of the memory allocated for indexes, compared to the size of the table data.</span></span> <span data-ttu-id="e0949-482">이는 예제에서 해시 인덱스의 크기가 더 큰 데이터 크기에 대해 설정되었기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-482">That is because the hash indexes in the sample are pre-sized for a larger data size.</span></span> <span data-ttu-id="e0949-483">해시 인덱스의 크기는 고정되어 있으므로 테이블의 데이터 크기에 따라 커지지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-483">Note that hash indexes have a fixed size, and thus their size will not grow with the size of data in the table.</span></span>  
  
####  <a name="memory-utilization-after-running-the-workload"></a><a name="Memoryutilizationafterrunningtheworkload"></a> <span data-ttu-id="e0949-484">작업 실행 후 메모리 사용률</span><span class="sxs-lookup"><span data-stu-id="e0949-484">Memory utilization after running the workload</span></span>  
 <span data-ttu-id="e0949-485">1,000만 개의 판매 주문을 삽입한 후 총 메모리 사용률은 다음과 유사합니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-485">After insert 10 million sales orders, the all-up memory utilization looks similar to the following:</span></span>  
  
```  
SELECT type  
, name  
, pages_kb/1024 AS pages_MB   
FROM sys.dm_os_memory_clerks WHERE type LIKE '%xtp%'  
```  
  
||||  
|-|-|-|  
|<span data-ttu-id="e0949-486">**type**</span><span class="sxs-lookup"><span data-stu-id="e0949-486">**type**</span></span>|<span data-ttu-id="e0949-487">**name**</span><span class="sxs-lookup"><span data-stu-id="e0949-487">**name**</span></span>|<span data-ttu-id="e0949-488">**pages_MB**</span><span class="sxs-lookup"><span data-stu-id="e0949-488">**pages_MB**</span></span>|  
|<span data-ttu-id="e0949-489">MEMORYCLERK_XTP</span><span class="sxs-lookup"><span data-stu-id="e0949-489">MEMORYCLERK_XTP</span></span>|<span data-ttu-id="e0949-490">기본값</span><span class="sxs-lookup"><span data-stu-id="e0949-490">Default</span></span>|<span data-ttu-id="e0949-491">146</span><span class="sxs-lookup"><span data-stu-id="e0949-491">146</span></span>|  
|<span data-ttu-id="e0949-492">MEMORYCLERK_XTP</span><span class="sxs-lookup"><span data-stu-id="e0949-492">MEMORYCLERK_XTP</span></span>|<span data-ttu-id="e0949-493">DB_ID_5</span><span class="sxs-lookup"><span data-stu-id="e0949-493">DB_ID_5</span></span>|<span data-ttu-id="e0949-494">7374</span><span class="sxs-lookup"><span data-stu-id="e0949-494">7374</span></span>|  
|<span data-ttu-id="e0949-495">MEMORYCLERK_XTP</span><span class="sxs-lookup"><span data-stu-id="e0949-495">MEMORYCLERK_XTP</span></span>|<span data-ttu-id="e0949-496">기본값</span><span class="sxs-lookup"><span data-stu-id="e0949-496">Default</span></span>|<span data-ttu-id="e0949-497">0</span><span class="sxs-lookup"><span data-stu-id="e0949-497">0</span></span>|  
|<span data-ttu-id="e0949-498">MEMORYCLERK_XTP</span><span class="sxs-lookup"><span data-stu-id="e0949-498">MEMORYCLERK_XTP</span></span>|<span data-ttu-id="e0949-499">기본값</span><span class="sxs-lookup"><span data-stu-id="e0949-499">Default</span></span>|<span data-ttu-id="e0949-500">0</span><span class="sxs-lookup"><span data-stu-id="e0949-500">0</span></span>|  
  
 <span data-ttu-id="e0949-501">보시다시피 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]는 예제 데이터베이스에서 메모리 최적화 테이블과 인덱스에 8GB보다 조금 작은 크기를 사용하고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-501">As you can see, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] is using a bit under 8GB for the memory-optimized tables and indexes in the sample database.</span></span>  
  
 <span data-ttu-id="e0949-502">예제를 한 번 실행한 후 테이블당 자세한 메모리 사용률을 살펴보면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-502">Looking at the detailed memory usage per table after one example run:</span></span>  
  
```  
SELECT object_name(t.object_id) AS [Table Name]  
     , memory_allocated_for_table_kb  
 , memory_allocated_for_indexes_kb  
FROM sys.dm_db_xtp_table_memory_stats dms JOIN sys.tables t   
ON dms.object_id=t.object_id  
WHERE t.type='U'  
```  
  
||||  
|-|-|-|  
|<span data-ttu-id="e0949-503">**테이블 이름**</span><span class="sxs-lookup"><span data-stu-id="e0949-503">**Table Name**</span></span>|<span data-ttu-id="e0949-504">**memory_allocated_for_table_kb**</span><span class="sxs-lookup"><span data-stu-id="e0949-504">**memory_allocated_for_table_kb**</span></span>|<span data-ttu-id="e0949-505">**memory_allocated_for_indexes_kb**</span><span class="sxs-lookup"><span data-stu-id="e0949-505">**memory_allocated_for_indexes_kb**</span></span>|  
|<span data-ttu-id="e0949-506">SalesOrderDetail_inmem</span><span class="sxs-lookup"><span data-stu-id="e0949-506">SalesOrderDetail_inmem</span></span>|<span data-ttu-id="e0949-507">5113761</span><span class="sxs-lookup"><span data-stu-id="e0949-507">5113761</span></span>|<span data-ttu-id="e0949-508">663552</span><span class="sxs-lookup"><span data-stu-id="e0949-508">663552</span></span>|  
|<span data-ttu-id="e0949-509">DemoSalesOrderDetailSeed</span><span class="sxs-lookup"><span data-stu-id="e0949-509">DemoSalesOrderDetailSeed</span></span>|<span data-ttu-id="e0949-510">64</span><span class="sxs-lookup"><span data-stu-id="e0949-510">64</span></span>|<span data-ttu-id="e0949-511">10368</span><span class="sxs-lookup"><span data-stu-id="e0949-511">10368</span></span>|  
|<span data-ttu-id="e0949-512">SpecialOffer_inmem</span><span class="sxs-lookup"><span data-stu-id="e0949-512">SpecialOffer_inmem</span></span>|<span data-ttu-id="e0949-513">2</span><span class="sxs-lookup"><span data-stu-id="e0949-513">2</span></span>|<span data-ttu-id="e0949-514">8192</span><span class="sxs-lookup"><span data-stu-id="e0949-514">8192</span></span>|  
|<span data-ttu-id="e0949-515">SalesOrderHeader_inmem</span><span class="sxs-lookup"><span data-stu-id="e0949-515">SalesOrderHeader_inmem</span></span>|<span data-ttu-id="e0949-516">1575679</span><span class="sxs-lookup"><span data-stu-id="e0949-516">1575679</span></span>|<span data-ttu-id="e0949-517">147456</span><span class="sxs-lookup"><span data-stu-id="e0949-517">147456</span></span>|  
|<span data-ttu-id="e0949-518">Product_inmem</span><span class="sxs-lookup"><span data-stu-id="e0949-518">Product_inmem</span></span>|<span data-ttu-id="e0949-519">111</span><span class="sxs-lookup"><span data-stu-id="e0949-519">111</span></span>|<span data-ttu-id="e0949-520">12032</span><span class="sxs-lookup"><span data-stu-id="e0949-520">12032</span></span>|  
|<span data-ttu-id="e0949-521">SpecialOfferProduct_inmem</span><span class="sxs-lookup"><span data-stu-id="e0949-521">SpecialOfferProduct_inmem</span></span>|<span data-ttu-id="e0949-522">64</span><span class="sxs-lookup"><span data-stu-id="e0949-522">64</span></span>|<span data-ttu-id="e0949-523">3712</span><span class="sxs-lookup"><span data-stu-id="e0949-523">3712</span></span>|  
|<span data-ttu-id="e0949-524">DemoSalesOrderHeaderSeed</span><span class="sxs-lookup"><span data-stu-id="e0949-524">DemoSalesOrderHeaderSeed</span></span>|<span data-ttu-id="e0949-525">1984</span><span class="sxs-lookup"><span data-stu-id="e0949-525">1984</span></span>|<span data-ttu-id="e0949-526">5504</span><span class="sxs-lookup"><span data-stu-id="e0949-526">5504</span></span>|  
  
 <span data-ttu-id="e0949-527">총 6.5GB 정도의 데이터를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-527">We can see a total of about 6.5GB of data.</span></span> <span data-ttu-id="e0949-528">SalesOrderHeader_inmem 및 SalesOrderDetail_inmem 테이블의 인덱스 크기는 판매 주문을 삽입하기 전의 인덱스 크기와 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-528">Notice that the size of the indexes on the table SalesOrderHeader_inmem and SalesOrderDetail_inmem is the same as the size of the indexes before inserting the sales orders.</span></span> <span data-ttu-id="e0949-529">인덱스 크기는 두 테이블 모두 해시 인덱스를 사용하고 해시 인덱스가 고정되어 있기 때문에 변경되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-529">The index size did not change because both tables are using hash indexes, and hash indexes are static.</span></span>  
  
#### <a name="after-demo-reset"></a><span data-ttu-id="e0949-530">데모를 다시 설정한 후</span><span class="sxs-lookup"><span data-stu-id="e0949-530">After demo reset</span></span>  
 <span data-ttu-id="e0949-531">저장 프로시저 Demo.usp_DemoReset을 사용하여 데모를 다시 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-531">The stored procedure Demo.usp_DemoReset can be used to reset the demo.</span></span> <span data-ttu-id="e0949-532">이 프로시저는 SalesOrderHeader_inmem 및 SalesOrderDetail_inmem 테이블의 데이터를 삭제하고 원래 테이블 SalesOrderHeader 및 SalesOrderDetail의 데이터로 초기값을 다시 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-532">It deletes the data in the tables SalesOrderHeader_inmem and SalesOrderDetail_inmem, and re-seeds the data from the original tables SalesOrderHeader and SalesOrderDetail.</span></span>  
  
 <span data-ttu-id="e0949-533">테이블의 행이 삭제되었더라도 메모리가 즉시 회수되지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-533">Now, even though the rows in the tables have been deleted, this does not mean that memory is reclaimed immediately.</span></span> [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]<span data-ttu-id="e0949-534">는 필요에 따라 백그라운드에서 메모리 최적화 테이블의 삭제된 행에서 메모리를 회수합니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-534">reclaims memory from deleted rows in memory-optimized tables in the background, as needed.</span></span> <span data-ttu-id="e0949-535">데모가 다시 설정된 직후에는 시스템에 트랜잭션 작업이 없으므로 삭제된 행의 메모리가 아직 회수되지 않은 것을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-535">You will see that immediately after demo reset, with no transactional workload on the system, memory from deleted rows is not yet reclaimed:</span></span>  
  
```  
SELECT type  
, name  
, pages_kb/1024 AS pages_MB   
FROM sys.dm_os_memory_clerks WHERE type LIKE '%xtp%'  
```  
  
||||  
|-|-|-|  
|<span data-ttu-id="e0949-536">**type**</span><span class="sxs-lookup"><span data-stu-id="e0949-536">**type**</span></span>|<span data-ttu-id="e0949-537">**name**</span><span class="sxs-lookup"><span data-stu-id="e0949-537">**name**</span></span>|<span data-ttu-id="e0949-538">**pages_MB**</span><span class="sxs-lookup"><span data-stu-id="e0949-538">**pages_MB**</span></span>|  
|<span data-ttu-id="e0949-539">MEMORYCLERK_XTP</span><span class="sxs-lookup"><span data-stu-id="e0949-539">MEMORYCLERK_XTP</span></span>|<span data-ttu-id="e0949-540">기본값</span><span class="sxs-lookup"><span data-stu-id="e0949-540">Default</span></span>|<span data-ttu-id="e0949-541">2261</span><span class="sxs-lookup"><span data-stu-id="e0949-541">2261</span></span>|  
|<span data-ttu-id="e0949-542">MEMORYCLERK_XTP</span><span class="sxs-lookup"><span data-stu-id="e0949-542">MEMORYCLERK_XTP</span></span>|<span data-ttu-id="e0949-543">DB_ID_5</span><span class="sxs-lookup"><span data-stu-id="e0949-543">DB_ID_5</span></span>|<span data-ttu-id="e0949-544">7396</span><span class="sxs-lookup"><span data-stu-id="e0949-544">7396</span></span>|  
|<span data-ttu-id="e0949-545">MEMORYCLERK_XTP</span><span class="sxs-lookup"><span data-stu-id="e0949-545">MEMORYCLERK_XTP</span></span>|<span data-ttu-id="e0949-546">기본값</span><span class="sxs-lookup"><span data-stu-id="e0949-546">Default</span></span>|<span data-ttu-id="e0949-547">0</span><span class="sxs-lookup"><span data-stu-id="e0949-547">0</span></span>|  
|<span data-ttu-id="e0949-548">MEMORYCLERK_XTP</span><span class="sxs-lookup"><span data-stu-id="e0949-548">MEMORYCLERK_XTP</span></span>|<span data-ttu-id="e0949-549">기본값</span><span class="sxs-lookup"><span data-stu-id="e0949-549">Default</span></span>|<span data-ttu-id="e0949-550">0</span><span class="sxs-lookup"><span data-stu-id="e0949-550">0</span></span>|  
  
 <span data-ttu-id="e0949-551">이는 예상된 결과입니다. 트랜잭션 작업이 실행 중일 때 메모리가 회수됩니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-551">This is expected: memory will be reclaimed when the transactional workload is running.</span></span>  
  
 <span data-ttu-id="e0949-552">데모 작업의 두 번째 실행을 시작하는 경우 이전에 삭제된 행이 정리됨에 따라 메모리 사용률이 처음에는 줄어드는 것을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-552">If you start a second run of the demo workload you will see the memory utilization decrease initially, as the previously deleted rows are cleaned up.</span></span> <span data-ttu-id="e0949-553">특정 시점에서 메모리 크기가 다시 증가하고 작업이 완료될 때까지 증가합니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-553">At some point the memory size will increase again, until the workload finishes.</span></span> <span data-ttu-id="e0949-554">데모를 다시 설정하고 1,000만 개의 행을 삽입한 후 메모리 사용률은 처음 실행한 후의 사용률과 매우 유사합니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-554">After inserting 10 million rows after demo reset, the memory utilization will be very similar to the utilization after the first run.</span></span> <span data-ttu-id="e0949-555">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-555">For example:</span></span>  
  
```  
SELECT type  
, name  
, pages_kb/1024 AS pages_MB   
FROM sys.dm_os_memory_clerks WHERE type LIKE '%xtp%'  
```  
  
||||  
|-|-|-|  
|<span data-ttu-id="e0949-556">**type**</span><span class="sxs-lookup"><span data-stu-id="e0949-556">**type**</span></span>|<span data-ttu-id="e0949-557">**name**</span><span class="sxs-lookup"><span data-stu-id="e0949-557">**name**</span></span>|<span data-ttu-id="e0949-558">**pages_MB**</span><span class="sxs-lookup"><span data-stu-id="e0949-558">**pages_MB**</span></span>|  
|<span data-ttu-id="e0949-559">MEMORYCLERK_XTP</span><span class="sxs-lookup"><span data-stu-id="e0949-559">MEMORYCLERK_XTP</span></span>|<span data-ttu-id="e0949-560">기본값</span><span class="sxs-lookup"><span data-stu-id="e0949-560">Default</span></span>|<span data-ttu-id="e0949-561">1863</span><span class="sxs-lookup"><span data-stu-id="e0949-561">1863</span></span>|  
|<span data-ttu-id="e0949-562">MEMORYCLERK_XTP</span><span class="sxs-lookup"><span data-stu-id="e0949-562">MEMORYCLERK_XTP</span></span>|<span data-ttu-id="e0949-563">DB_ID_5</span><span class="sxs-lookup"><span data-stu-id="e0949-563">DB_ID_5</span></span>|<span data-ttu-id="e0949-564">7390</span><span class="sxs-lookup"><span data-stu-id="e0949-564">7390</span></span>|  
|<span data-ttu-id="e0949-565">MEMORYCLERK_XTP</span><span class="sxs-lookup"><span data-stu-id="e0949-565">MEMORYCLERK_XTP</span></span>|<span data-ttu-id="e0949-566">기본값</span><span class="sxs-lookup"><span data-stu-id="e0949-566">Default</span></span>|<span data-ttu-id="e0949-567">0</span><span class="sxs-lookup"><span data-stu-id="e0949-567">0</span></span>|  
|<span data-ttu-id="e0949-568">MEMORYCLERK_XTP</span><span class="sxs-lookup"><span data-stu-id="e0949-568">MEMORYCLERK_XTP</span></span>|<span data-ttu-id="e0949-569">기본값</span><span class="sxs-lookup"><span data-stu-id="e0949-569">Default</span></span>|<span data-ttu-id="e0949-570">0</span><span class="sxs-lookup"><span data-stu-id="e0949-570">0</span></span>|  
  
### <a name="disk-utilization-for-memory-optimized-tables"></a><span data-ttu-id="e0949-571">메모리 최적화 테이블의 디스크 사용률</span><span class="sxs-lookup"><span data-stu-id="e0949-571">Disk utilization for memory-optimized tables</span></span>  
 <span data-ttu-id="e0949-572">지정된 시점에서 데이터베이스의 검사점 파일에 대한 전체 디스크 크기는 다음 쿼리를 사용하여 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-572">The overall on-disk size for the checkpoint files of a database at a given time can be found using the query:</span></span>  
  
```  
SELECT SUM(df.size) * 8 / 1024 AS [On-disk size in MB]  
FROM sys.filegroups f JOIN sys.database_files df   
   ON f.data_space_id=df.data_space_id  
WHERE f.type=N'FX'  
  
```  
  
#### <a name="initial-state"></a><span data-ttu-id="e0949-573">초기 상태</span><span class="sxs-lookup"><span data-stu-id="e0949-573">Initial state</span></span>  
 <span data-ttu-id="e0949-574">예제 파일 그룹과 예제 메모리 최적화 테이블이 처음에 만들어질 때 많은 검사점 파일이 미리 만들어지고 시스템이 이러한 파일을 채우기 시작합니다. 미리 만들어지는 검사점 파일의 수는 시스템의 논리적 프로세서 수에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-574">When the sample filegroup and sample memory-optimized tables are created initially, a number of checkpoint files are pre-created and the system starts filling the files - the number of checkpoint files pre-created depends on the number of logical processors in the system.</span></span> <span data-ttu-id="e0949-575">예제는 처음에는 매우 작으므로 미리 만들어진 파일은 처음 만들어진 후 거의 비어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-575">As the sample is initially very small, the pre-created files will be mostly empty after initial create.</span></span>  
  
 <span data-ttu-id="e0949-576">논리적 프로세서가 16개인 컴퓨터에서 예제의 초기 디스크 크기는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-576">The following shows the initial on-disk size for the sample on a machine with 16 logical processors:</span></span>  
  
```  
SELECT SUM(df.size) * 8 / 1024 AS [On-disk size in MB]  
FROM sys.filegroups f JOIN sys.database_files df   
   ON f.data_space_id=df.data_space_id  
WHERE f.type=N'FX'  
```  
  
||  
|-|  
|<span data-ttu-id="e0949-577">**On-disk size in MB**</span><span class="sxs-lookup"><span data-stu-id="e0949-577">**On-disk size in MB**</span></span>|  
|<span data-ttu-id="e0949-578">2312</span><span class="sxs-lookup"><span data-stu-id="e0949-578">2312</span></span>|  
  
 <span data-ttu-id="e0949-579">보시다시피 검사점 파일의 디스크 크기(2.3GB)와 실제 데이터 크기(30MB에 가까움)에는 큰 차이가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-579">As you can see, there is a big discrepancy between the on-disk size of the checkpoint files, which is 2.3GB, and the actual data size, which is closer to 30MB.</span></span>  
  
 <span data-ttu-id="e0949-580">디스크 공간 사용의 출처를 자세히 살펴보려면 다음 쿼리를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-580">Looking closer at where the disk-space utilization comes from, you can use the following query.</span></span> <span data-ttu-id="e0949-581">이 쿼리에서 반환되는 디스크 크기는 상태가 5(REQUIRED FOR BACKUP/HA), 6(IN TRANSITION TO TOMBSTONE) 또는 7(TOMBSTONE)인 파일에 대해 대략적인 값입니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-581">The size on disk returned by this query is approximate for files with state in 5 (REQUIRED FOR BACKUP/HA), 6 (IN TRANSITION TO TOMBSTONE), or 7 (TOMBSTONE).</span></span>  
  
```  
SELECT state_desc  
 , file_type_desc  
 , COUNT(*) AS [count]  
 , SUM(CASE  
   WHEN state = 5 AND file_type=0 THEN 128*1024*1024  
   WHEN state = 5 AND file_type=1 THEN 8*1024*1024  
   WHEN state IN (6,7) THEN 68*1024*1024  
   ELSE file_size_in_bytes  
    END) / 1024 / 1024 AS [on-disk size MB]   
FROM sys.dm_db_xtp_checkpoint_files  
GROUP BY state, state_desc, file_type, file_type_desc  
ORDER BY state, file_type  
```  
  
 <span data-ttu-id="e0949-582">예제의 초기 상태에 대한 결과는 논리적 프로세서가 16개인 서버의 경우와 유사합니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-582">For the initial state of the sample, the result will look something like for a server with 16 logical processors:</span></span>  
  
|||||  
|-|-|-|-|  
|<span data-ttu-id="e0949-583">**state_desc**</span><span class="sxs-lookup"><span data-stu-id="e0949-583">**state_desc**</span></span>|<span data-ttu-id="e0949-584">**file_type_desc**</span><span class="sxs-lookup"><span data-stu-id="e0949-584">**file_type_desc**</span></span>|<span data-ttu-id="e0949-585">**count**</span><span class="sxs-lookup"><span data-stu-id="e0949-585">**count**</span></span>|<span data-ttu-id="e0949-586">**on-disk size MB**</span><span class="sxs-lookup"><span data-stu-id="e0949-586">**on-disk size MB**</span></span>|  
|<span data-ttu-id="e0949-587">PRECREATED</span><span class="sxs-lookup"><span data-stu-id="e0949-587">PRECREATED</span></span>|<span data-ttu-id="e0949-588">DATA</span><span class="sxs-lookup"><span data-stu-id="e0949-588">DATA</span></span>|<span data-ttu-id="e0949-589">16</span><span class="sxs-lookup"><span data-stu-id="e0949-589">16</span></span>|<span data-ttu-id="e0949-590">2048</span><span class="sxs-lookup"><span data-stu-id="e0949-590">2048</span></span>|  
|<span data-ttu-id="e0949-591">PRECREATED</span><span class="sxs-lookup"><span data-stu-id="e0949-591">PRECREATED</span></span>|<span data-ttu-id="e0949-592">DELTA</span><span class="sxs-lookup"><span data-stu-id="e0949-592">DELTA</span></span>|<span data-ttu-id="e0949-593">16</span><span class="sxs-lookup"><span data-stu-id="e0949-593">16</span></span>|<span data-ttu-id="e0949-594">128</span><span class="sxs-lookup"><span data-stu-id="e0949-594">128</span></span>|  
|<span data-ttu-id="e0949-595">UNDER CONSTRUCTION</span><span class="sxs-lookup"><span data-stu-id="e0949-595">UNDER CONSTRUCTION</span></span>|<span data-ttu-id="e0949-596">DATA</span><span class="sxs-lookup"><span data-stu-id="e0949-596">DATA</span></span>|<span data-ttu-id="e0949-597">1</span><span class="sxs-lookup"><span data-stu-id="e0949-597">1</span></span>|<span data-ttu-id="e0949-598">128</span><span class="sxs-lookup"><span data-stu-id="e0949-598">128</span></span>|  
|<span data-ttu-id="e0949-599">UNDER CONSTRUCTION</span><span class="sxs-lookup"><span data-stu-id="e0949-599">UNDER CONSTRUCTION</span></span>|<span data-ttu-id="e0949-600">DELTA</span><span class="sxs-lookup"><span data-stu-id="e0949-600">DELTA</span></span>|<span data-ttu-id="e0949-601">1</span><span class="sxs-lookup"><span data-stu-id="e0949-601">1</span></span>|<span data-ttu-id="e0949-602">8</span><span class="sxs-lookup"><span data-stu-id="e0949-602">8</span></span>|  
  
 <span data-ttu-id="e0949-603">보시다시피 대부분의 공간이 미리 만들어진 데이터 및 델타 파일에서 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-603">As you can see, most of the space is used by precreated data and delta files.</span></span> [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]<span data-ttu-id="e0949-604">는 논리적 프로세서당 하나의 (데이터, 델타) 파일 쌍을 미리 만들었습니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-604">pre-created one pair of (data, delta) files per logical processor.</span></span> <span data-ttu-id="e0949-605">또한 데이터 파일의 크기는 128MB로, 델타 파일의 크기는 8MB로 미리 지정되므로 이러한 파일에 더욱 효율적으로 데이터를 삽입할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-605">In addition, data files are pre-sized at 128MB, and delta files at 8MB, in order to make inserting data into these files more efficient.</span></span>  
  
 <span data-ttu-id="e0949-606">메모리 최적화 테이블의 실제 데이터는 단일 데이터 파일에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-606">The actual data in the memory-optimized tables is in the single data file.</span></span>  
  
#### <a name="after-running-the-workload"></a><span data-ttu-id="e0949-607">작업을 실행한 후</span><span class="sxs-lookup"><span data-stu-id="e0949-607">After running the workload</span></span>  
 <span data-ttu-id="e0949-608">1,000만 개의 판매 주문을 삽입하는 단일 테스트 실행 후 전체 디스크 크기는 다음과 같습니다(16코어 테스트 서버의 경우).</span><span class="sxs-lookup"><span data-stu-id="e0949-608">After a single test run that inserts 10 million sales orders, the overall on-disk size looks something like this (for a 16-core test server):</span></span>  
  
```  
SELECT SUM(df.size) * 8 / 1024 AS [On-disk size in MB]  
FROM sys.filegroups f JOIN sys.database_files df   
   ON f.data_space_id=df.data_space_id  
WHERE f.type=N'FX'  
```  
  
||  
|-|  
|<span data-ttu-id="e0949-609">**On-disk size in MB**</span><span class="sxs-lookup"><span data-stu-id="e0949-609">**On-disk size in MB**</span></span>|  
|<span data-ttu-id="e0949-610">8828</span><span class="sxs-lookup"><span data-stu-id="e0949-610">8828</span></span>|  
  
 <span data-ttu-id="e0949-611">디스크 크기는 데이터의 메모리 내 크기와 유사하게 9GB에 가깝습니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-611">The on-disk size is close to 9GB, which comes close to the in-memory size of the data.</span></span>  
  
 <span data-ttu-id="e0949-612">다양한 상태에 있는 검사점 파일의 크기를 좀더 자세히 살펴보면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-612">Looking more closely at the sizes of the checkpoint files across the various states:</span></span>  
  
```  
SELECT state_desc  
 , file_type_desc  
 , COUNT(*) AS [count]  
 , SUM(CASE  
   WHEN state = 5 AND file_type=0 THEN 128*1024*1024  
   WHEN state = 5 AND file_type=1 THEN 8*1024*1024  
   WHEN state IN (6,7) THEN 68*1024*1024  
   ELSE file_size_in_bytes  
    END) / 1024 / 1024 AS [on-disk size MB]   
FROM sys.dm_db_xtp_checkpoint_files  
GROUP BY state, state_desc, file_type, file_type_desc  
ORDER BY state, file_type  
```  
  
|||||  
|-|-|-|-|  
|<span data-ttu-id="e0949-613">**state_desc**</span><span class="sxs-lookup"><span data-stu-id="e0949-613">**state_desc**</span></span>|<span data-ttu-id="e0949-614">**file_type_desc**</span><span class="sxs-lookup"><span data-stu-id="e0949-614">**file_type_desc**</span></span>|<span data-ttu-id="e0949-615">**count**</span><span class="sxs-lookup"><span data-stu-id="e0949-615">**count**</span></span>|<span data-ttu-id="e0949-616">**on-disk size MB**</span><span class="sxs-lookup"><span data-stu-id="e0949-616">**on-disk size MB**</span></span>|  
|<span data-ttu-id="e0949-617">PRECREATED</span><span class="sxs-lookup"><span data-stu-id="e0949-617">PRECREATED</span></span>|<span data-ttu-id="e0949-618">DATA</span><span class="sxs-lookup"><span data-stu-id="e0949-618">DATA</span></span>|<span data-ttu-id="e0949-619">16</span><span class="sxs-lookup"><span data-stu-id="e0949-619">16</span></span>|<span data-ttu-id="e0949-620">2048</span><span class="sxs-lookup"><span data-stu-id="e0949-620">2048</span></span>|  
|<span data-ttu-id="e0949-621">PRECREATED</span><span class="sxs-lookup"><span data-stu-id="e0949-621">PRECREATED</span></span>|<span data-ttu-id="e0949-622">DELTA</span><span class="sxs-lookup"><span data-stu-id="e0949-622">DELTA</span></span>|<span data-ttu-id="e0949-623">16</span><span class="sxs-lookup"><span data-stu-id="e0949-623">16</span></span>|<span data-ttu-id="e0949-624">128</span><span class="sxs-lookup"><span data-stu-id="e0949-624">128</span></span>|  
|<span data-ttu-id="e0949-625">UNDER CONSTRUCTION</span><span class="sxs-lookup"><span data-stu-id="e0949-625">UNDER CONSTRUCTION</span></span>|<span data-ttu-id="e0949-626">DATA</span><span class="sxs-lookup"><span data-stu-id="e0949-626">DATA</span></span>|<span data-ttu-id="e0949-627">1</span><span class="sxs-lookup"><span data-stu-id="e0949-627">1</span></span>|<span data-ttu-id="e0949-628">128</span><span class="sxs-lookup"><span data-stu-id="e0949-628">128</span></span>|  
|<span data-ttu-id="e0949-629">UNDER CONSTRUCTION</span><span class="sxs-lookup"><span data-stu-id="e0949-629">UNDER CONSTRUCTION</span></span>|<span data-ttu-id="e0949-630">DELTA</span><span class="sxs-lookup"><span data-stu-id="e0949-630">DELTA</span></span>|<span data-ttu-id="e0949-631">1</span><span class="sxs-lookup"><span data-stu-id="e0949-631">1</span></span>|<span data-ttu-id="e0949-632">8</span><span class="sxs-lookup"><span data-stu-id="e0949-632">8</span></span>|  
  
 <span data-ttu-id="e0949-633">검사점이 닫힐 때 사용할 준비가 된 미리 만들어진 파일 쌍이 16개 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-633">We still have 16 pairs of pre-created files, ready to go as checkpoints are closed.</span></span>  
  
 <span data-ttu-id="e0949-634">현재 검사점이 닫힐 때까지 사용되는, 작성 중인 쌍이 하나 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-634">There is one pair under construction, which is used until the current checkpoint is closed.</span></span> <span data-ttu-id="e0949-635">활성 검사점 파일과 함께 메모리의 6.5GB 데이터에 대한 약 6.5GB의 디스크를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-635">Along with the active checkpoint files this gives about 6.5GB of disk utilization for 6.5GB of data in memory.</span></span> <span data-ttu-id="e0949-636">인덱스가 디스크에 유지되지 않으므로 이 경우 디스크의 전체 크기는 메모리의 크기보다 작습니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-636">Recall that indexes are not persisted on disk, and thus the overall size on disk is smaller than the size in memory in this case.</span></span>  
  
#### <a name="after-demo-reset"></a><span data-ttu-id="e0949-637">데모를 다시 설정한 후</span><span class="sxs-lookup"><span data-stu-id="e0949-637">After demo reset</span></span>  
 <span data-ttu-id="e0949-638">데모를 다시 설정한 후에는 데이터베이스 검사점이 없고 시스템에 트랜잭션 작업이 없는 경우 디스크 공간이 즉시 회수되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-638">After demo reset, disk space is not reclaimed immediately if there is no transactional workload on the system, and there are not database checkpoints.</span></span> <span data-ttu-id="e0949-639">검사점 파일이 다양한 상태를 이동하여 결국 삭제되려면 검사점 파일의 병합을 시작하고 가비지 수집을 시작하기 위해 많은 검사점 및 로그 잘림 이벤트가 발생해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-639">For checkpoint files to be moved through their various stages and eventually be discarded, a number of checkpoints and log truncation events need to happen, to initiate merge of checkpoint files, as well as to initiate garbage collection.</span></span> <span data-ttu-id="e0949-640">이러한 이벤트는 시스템에 트랜잭션 작업이 있으면(전체 복구 모델을 사용하는 경우에는 정기 로그 백업을 수행하면) 자동으로 발생하지만, 데모 시나리오와 같이 시스템이 유휴 상태일 때는 발생하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-640">These will happen automatically if you have a transactional workload in the system [and take regular log backups, in case you are using the FULL recovery model], but not when the system is idle, as in a demo scenario.</span></span>  
  
 <span data-ttu-id="e0949-641">예제에서는 데모를 다시 설정한 후 다음과 유사하게 나타날 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-641">In the example, after demo reset, you may see something like</span></span>  
  
```  
SELECT SUM(df.size) * 8 / 1024 AS [On-disk size in MB]  
FROM sys.filegroups f JOIN sys.database_files df   
   ON f.data_space_id=df.data_space_id  
WHERE f.type=N'FX'  
```  
  
||  
|-|  
|<span data-ttu-id="e0949-642">**On-disk size in MB**</span><span class="sxs-lookup"><span data-stu-id="e0949-642">**On-disk size in MB**</span></span>|  
|<span data-ttu-id="e0949-643">11839</span><span class="sxs-lookup"><span data-stu-id="e0949-643">11839</span></span>|  
  
 <span data-ttu-id="e0949-644">거의 12GB로, 데모를 다시 설정하기 전의 9GB보다 훨씬 큽니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-644">At nearly 12GB, this is significantly more than the 9GB we had before the demo reset.</span></span> <span data-ttu-id="e0949-645">이는 다음에서 확인할 수 있듯이 일부 검사점 파일 병합이 시작되었지만 일부 병합 대상이 아직 설치되지 않았으며 일부 병합 원본 파일이 아직 정리되지 않았기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-645">This is because some checkpoint file merges have been started, but some of the merge targets have not yet been installed, and some of the merge source files have not yet been cleaned up, as can be seen from the following:</span></span>  
  
```  
SELECT state_desc  
 , file_type_desc  
 , COUNT(*) AS [count]  
 , SUM(CASE  
   WHEN state = 5 AND file_type=0 THEN 128*1024*1024  
   WHEN state = 5 AND file_type=1 THEN 8*1024*1024  
   WHEN state IN (6,7) THEN 68*1024*1024  
   ELSE file_size_in_bytes  
    END) / 1024 / 1024 AS [on-disk size MB]   
FROM sys.dm_db_xtp_checkpoint_files  
GROUP BY state, state_desc, file_type, file_type_desc  
ORDER BY state, file_type  
```  
  
|||||  
|-|-|-|-|  
|<span data-ttu-id="e0949-646">**state_desc**</span><span class="sxs-lookup"><span data-stu-id="e0949-646">**state_desc**</span></span>|<span data-ttu-id="e0949-647">**file_type_desc**</span><span class="sxs-lookup"><span data-stu-id="e0949-647">**file_type_desc**</span></span>|<span data-ttu-id="e0949-648">**count**</span><span class="sxs-lookup"><span data-stu-id="e0949-648">**count**</span></span>|<span data-ttu-id="e0949-649">**on-disk size MB**</span><span class="sxs-lookup"><span data-stu-id="e0949-649">**on-disk size MB**</span></span>|  
|<span data-ttu-id="e0949-650">PRECREATED</span><span class="sxs-lookup"><span data-stu-id="e0949-650">PRECREATED</span></span>|<span data-ttu-id="e0949-651">DATA</span><span class="sxs-lookup"><span data-stu-id="e0949-651">DATA</span></span>|<span data-ttu-id="e0949-652">16</span><span class="sxs-lookup"><span data-stu-id="e0949-652">16</span></span>|<span data-ttu-id="e0949-653">2048</span><span class="sxs-lookup"><span data-stu-id="e0949-653">2048</span></span>|  
|<span data-ttu-id="e0949-654">PRECREATED</span><span class="sxs-lookup"><span data-stu-id="e0949-654">PRECREATED</span></span>|<span data-ttu-id="e0949-655">DELTA</span><span class="sxs-lookup"><span data-stu-id="e0949-655">DELTA</span></span>|<span data-ttu-id="e0949-656">16</span><span class="sxs-lookup"><span data-stu-id="e0949-656">16</span></span>|<span data-ttu-id="e0949-657">128</span><span class="sxs-lookup"><span data-stu-id="e0949-657">128</span></span>|  
|<span data-ttu-id="e0949-658">ACTIVE</span><span class="sxs-lookup"><span data-stu-id="e0949-658">ACTIVE</span></span>|<span data-ttu-id="e0949-659">DATA</span><span class="sxs-lookup"><span data-stu-id="e0949-659">DATA</span></span>|<span data-ttu-id="e0949-660">38</span><span class="sxs-lookup"><span data-stu-id="e0949-660">38</span></span>|<span data-ttu-id="e0949-661">5152</span><span class="sxs-lookup"><span data-stu-id="e0949-661">5152</span></span>|  
|<span data-ttu-id="e0949-662">ACTIVE</span><span class="sxs-lookup"><span data-stu-id="e0949-662">ACTIVE</span></span>|<span data-ttu-id="e0949-663">DELTA</span><span class="sxs-lookup"><span data-stu-id="e0949-663">DELTA</span></span>|<span data-ttu-id="e0949-664">38</span><span class="sxs-lookup"><span data-stu-id="e0949-664">38</span></span>|<span data-ttu-id="e0949-665">1331</span><span class="sxs-lookup"><span data-stu-id="e0949-665">1331</span></span>|  
|<span data-ttu-id="e0949-666">MERGE TARGET</span><span class="sxs-lookup"><span data-stu-id="e0949-666">MERGE TARGET</span></span>|<span data-ttu-id="e0949-667">DATA</span><span class="sxs-lookup"><span data-stu-id="e0949-667">DATA</span></span>|<span data-ttu-id="e0949-668">7</span><span class="sxs-lookup"><span data-stu-id="e0949-668">7</span></span>|<span data-ttu-id="e0949-669">896</span><span class="sxs-lookup"><span data-stu-id="e0949-669">896</span></span>|  
|<span data-ttu-id="e0949-670">MERGE TARGET</span><span class="sxs-lookup"><span data-stu-id="e0949-670">MERGE TARGET</span></span>|<span data-ttu-id="e0949-671">DELTA</span><span class="sxs-lookup"><span data-stu-id="e0949-671">DELTA</span></span>|<span data-ttu-id="e0949-672">7</span><span class="sxs-lookup"><span data-stu-id="e0949-672">7</span></span>|<span data-ttu-id="e0949-673">56</span><span class="sxs-lookup"><span data-stu-id="e0949-673">56</span></span>|  
|<span data-ttu-id="e0949-674">MERGED SOURCE</span><span class="sxs-lookup"><span data-stu-id="e0949-674">MERGED SOURCE</span></span>|<span data-ttu-id="e0949-675">DATA</span><span class="sxs-lookup"><span data-stu-id="e0949-675">DATA</span></span>|<span data-ttu-id="e0949-676">13</span><span class="sxs-lookup"><span data-stu-id="e0949-676">13</span></span>|<span data-ttu-id="e0949-677">1772</span><span class="sxs-lookup"><span data-stu-id="e0949-677">1772</span></span>|  
|<span data-ttu-id="e0949-678">MERGED SOURCE</span><span class="sxs-lookup"><span data-stu-id="e0949-678">MERGED SOURCE</span></span>|<span data-ttu-id="e0949-679">DELTA</span><span class="sxs-lookup"><span data-stu-id="e0949-679">DELTA</span></span>|<span data-ttu-id="e0949-680">13</span><span class="sxs-lookup"><span data-stu-id="e0949-680">13</span></span>|<span data-ttu-id="e0949-681">455</span><span class="sxs-lookup"><span data-stu-id="e0949-681">455</span></span>|  
  
 <span data-ttu-id="e0949-682">트랜잭션 작업이 시스템에서 발생하면 병합 대상이 설치되고 병합된 원본이 정리됩니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-682">Merge targets are installed and merged source are cleaned up as transactional activity happens in the system.</span></span>  
  
 <span data-ttu-id="e0949-683">데모를 다시 설정한 후 1,000만 개의 판매 주문을 삽입하는 데모 작업을 두 번째로 실행하면 작업을 처음 실행하는 동안 생성된 파일이 정리된 것을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-683">After a second run of the demo workload, inserting 10 million sales orders after the demo reset, you will see that the files constructed during the first run of the workload have been cleaned up.</span></span> <span data-ttu-id="e0949-684">작업이 실행되는 동안 위의 쿼리를 몇 차례 실행하는 경우 검사점 파일이 다양한 상태를 거치는 것을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-684">If you run the above query several times while the workload is running, you can see the checkpoint files make their way through the various stages.</span></span>  
  
 <span data-ttu-id="e0949-685">1,000만 개의 판매 주문을 삽입하는 작업을 두 번째로 실행한 후 디스크 사용률이 처음 실행한 후와 매우 유사한 것을 확인할 수 있습니다. 하지만 시스템이 특성상 동적이므로 반드시 같지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-685">After the second run of the workload insert 10 million sales orders you will see disk utilization very similar to, though not necessarily the same as after the first run, as the system is dynamic in nature.</span></span> <span data-ttu-id="e0949-686">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-686">For example:</span></span>  
  
```  
SELECT state_desc  
 , file_type_desc  
 , COUNT(*) AS [count]  
 , SUM(CASE  
   WHEN state = 5 AND file_type=0 THEN 128*1024*1024  
   WHEN state = 5 AND file_type=1 THEN 8*1024*1024  
   WHEN state IN (6,7) THEN 68*1024*1024  
   ELSE file_size_in_bytes  
    END) / 1024 / 1024 AS [on-disk size MB]   
FROM sys.dm_db_xtp_checkpoint_files  
GROUP BY state, state_desc, file_type, file_type_desc  
ORDER BY state, file_type  
```  
  
|||||  
|-|-|-|-|  
|<span data-ttu-id="e0949-687">**state_desc**</span><span class="sxs-lookup"><span data-stu-id="e0949-687">**state_desc**</span></span>|<span data-ttu-id="e0949-688">**file_type_desc**</span><span class="sxs-lookup"><span data-stu-id="e0949-688">**file_type_desc**</span></span>|<span data-ttu-id="e0949-689">**count**</span><span class="sxs-lookup"><span data-stu-id="e0949-689">**count**</span></span>|<span data-ttu-id="e0949-690">**on-disk size MB**</span><span class="sxs-lookup"><span data-stu-id="e0949-690">**on-disk size MB**</span></span>|  
|<span data-ttu-id="e0949-691">PRECREATED</span><span class="sxs-lookup"><span data-stu-id="e0949-691">PRECREATED</span></span>|<span data-ttu-id="e0949-692">DATA</span><span class="sxs-lookup"><span data-stu-id="e0949-692">DATA</span></span>|<span data-ttu-id="e0949-693">16</span><span class="sxs-lookup"><span data-stu-id="e0949-693">16</span></span>|<span data-ttu-id="e0949-694">2048</span><span class="sxs-lookup"><span data-stu-id="e0949-694">2048</span></span>|  
|<span data-ttu-id="e0949-695">PRECREATED</span><span class="sxs-lookup"><span data-stu-id="e0949-695">PRECREATED</span></span>|<span data-ttu-id="e0949-696">DELTA</span><span class="sxs-lookup"><span data-stu-id="e0949-696">DELTA</span></span>|<span data-ttu-id="e0949-697">16</span><span class="sxs-lookup"><span data-stu-id="e0949-697">16</span></span>|<span data-ttu-id="e0949-698">128</span><span class="sxs-lookup"><span data-stu-id="e0949-698">128</span></span>|  
|<span data-ttu-id="e0949-699">UNDER CONSTRUCTION</span><span class="sxs-lookup"><span data-stu-id="e0949-699">UNDER CONSTRUCTION</span></span>|<span data-ttu-id="e0949-700">DATA</span><span class="sxs-lookup"><span data-stu-id="e0949-700">DATA</span></span>|<span data-ttu-id="e0949-701">2</span><span class="sxs-lookup"><span data-stu-id="e0949-701">2</span></span>|<span data-ttu-id="e0949-702">268</span><span class="sxs-lookup"><span data-stu-id="e0949-702">268</span></span>|  
|<span data-ttu-id="e0949-703">UNDER CONSTRUCTION</span><span class="sxs-lookup"><span data-stu-id="e0949-703">UNDER CONSTRUCTION</span></span>|<span data-ttu-id="e0949-704">DELTA</span><span class="sxs-lookup"><span data-stu-id="e0949-704">DELTA</span></span>|<span data-ttu-id="e0949-705">2</span><span class="sxs-lookup"><span data-stu-id="e0949-705">2</span></span>|<span data-ttu-id="e0949-706">16</span><span class="sxs-lookup"><span data-stu-id="e0949-706">16</span></span>|  
|<span data-ttu-id="e0949-707">ACTIVE</span><span class="sxs-lookup"><span data-stu-id="e0949-707">ACTIVE</span></span>|<span data-ttu-id="e0949-708">DATA</span><span class="sxs-lookup"><span data-stu-id="e0949-708">DATA</span></span>|<span data-ttu-id="e0949-709">41</span><span class="sxs-lookup"><span data-stu-id="e0949-709">41</span></span>|<span data-ttu-id="e0949-710">5608</span><span class="sxs-lookup"><span data-stu-id="e0949-710">5608</span></span>|  
|<span data-ttu-id="e0949-711">ACTIVE</span><span class="sxs-lookup"><span data-stu-id="e0949-711">ACTIVE</span></span>|<span data-ttu-id="e0949-712">DELTA</span><span class="sxs-lookup"><span data-stu-id="e0949-712">DELTA</span></span>|<span data-ttu-id="e0949-713">41</span><span class="sxs-lookup"><span data-stu-id="e0949-713">41</span></span>|<span data-ttu-id="e0949-714">328</span><span class="sxs-lookup"><span data-stu-id="e0949-714">328</span></span>|  
  
 <span data-ttu-id="e0949-715">이 경우에는 'under construction' 상태의 검사점 파일 쌍이 두 개 있습니다. 즉, 작업의 높은 동시성 수준 때문에 여러 파일 쌍이 ‘under construction’ 상태로 이동했습니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-715">In this case, there are two checkpoint file pairs in the 'under construction' state, which means multiple file pairs were moved to the 'under construction' state, likely due to the high level of concurrency in the workload.</span></span> <span data-ttu-id="e0949-716">여러 동시 스레드에서 같은 시간에 새로운 파일 쌍을 필요로 했으므로 파일 쌍이 'precreated'에서 ‘under construction’으로 이동했습니다.</span><span class="sxs-lookup"><span data-stu-id="e0949-716">Multiple concurrent threads required a new file pair at the same time, and thus moved a pair from 'precreated' to 'under construction'.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0949-717">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e0949-717">See Also</span></span>  
 [<span data-ttu-id="e0949-718">메모리 내 OLTP&#40;메모리 내 최적화&#41;</span><span class="sxs-lookup"><span data-stu-id="e0949-718">In-Memory OLTP &#40;In-Memory Optimization&#41;</span></span>](../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
