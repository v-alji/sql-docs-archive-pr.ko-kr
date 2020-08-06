---
title: DQS 데이터베이스 분리 및 연결 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 830e33bc-dd15-4f8e-a4ac-d8634b78fe45
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 3bcac9d1f53b10cf6356b878ce4006f66c198d99
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647859"
---
# <a name="detaching-and-attaching-dqs-databases"></a><span data-ttu-id="27ebd-102">DQS 데이터베이스 분리 및 연결</span><span class="sxs-lookup"><span data-stu-id="27ebd-102">Detaching and Attaching DQS Databases</span></span>
  <span data-ttu-id="27ebd-103">이 항목에서는 DQS 데이터베이스를 분리 및 연결하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="27ebd-103">This topic describes how to detach and attach the DQS databases.</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="27ebd-104">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="27ebd-104">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Limitations"></a> <span data-ttu-id="27ebd-105">제한 사항</span><span class="sxs-lookup"><span data-stu-id="27ebd-105">Limitations and Restrictions</span></span>  
 <span data-ttu-id="27ebd-106">제한 사항 목록은 [데이터베이스 분리 및 연결&#40;SQL Server&#41;](../relational-databases/databases/database-detach-and-attach-sql-server.md)의 데이터베이스를 분리하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="27ebd-106">For a list of limitations and restrictions, see [Database Detach and Attach &#40;SQL Server&#41;](../relational-databases/databases/database-detach-and-attach-sql-server.md).</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="27ebd-107">필수 조건</span><span class="sxs-lookup"><span data-stu-id="27ebd-107">Prerequisites</span></span>  
  
-   <span data-ttu-id="27ebd-108">DQS에서 실행 중인 작업이나 프로세스가 없는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="27ebd-108">Ensure that there are no running activities or processes in DQS.</span></span> <span data-ttu-id="27ebd-109">이는 **작업 모니터링** 화면을 사용하여 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="27ebd-109">This can be verified using the **Activity Monitoring** screen.</span></span> <span data-ttu-id="27ebd-110">이 화면을 사용하는 방법은 [Monitor DQS Activities](../../2014/data-quality-services/monitor-dqs-activities.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="27ebd-110">For detailed information about working in this screen, see [Monitor DQS Activities](../../2014/data-quality-services/monitor-dqs-activities.md).</span></span>  
  
-   <span data-ttu-id="27ebd-111">[!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)]에 로그온한 사용자가 없는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="27ebd-111">Ensure that there are no users logged on the [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)].</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="27ebd-112">보안</span><span class="sxs-lookup"><span data-stu-id="27ebd-112">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="27ebd-113">권한</span><span class="sxs-lookup"><span data-stu-id="27ebd-113">Permissions</span></span>  
  
-   <span data-ttu-id="27ebd-114">DQS 데이터베이스를 분리하려면 Windows 사용자 계정은 SQL Server 인스턴스에서 db_owner 고정 서버 역할의 멤버여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="27ebd-114">Your Windows user account must be a member of the db_owner fixed server role in the SQL Server instance to detach DQS databases.</span></span>  
  
-   <span data-ttu-id="27ebd-115">데이터베이스를 연결하려면 Windows 사용자 계정에 CREATE DATABASE, CREATE ANY DATABASE 또는 ALTER ANY DATABASE 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="27ebd-115">Your Windows user account must have CREATE DATABASE, CREATE ANY DATABASE, or ALTER ANY DATABASE permission to attach a database.</span></span>  
  
-   <span data-ttu-id="27ebd-116">DQS에서 실행 중인 작업을 종료하거나 실행 중인 프로세스를 중지하려면 DQS_MAIN 데이터베이스에 대한 dqs_administrator 역할이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="27ebd-116">You must have the dqs_administrator role on the DQS_MAIN database to terminate any running activities or stop any running processes in DQS.</span></span>  
  
##  <a name="detach-dqs-databases"></a><a name="Detach"></a><span data-ttu-id="27ebd-117">DQS 데이터베이스 분리</span><span class="sxs-lookup"><span data-stu-id="27ebd-117">Detach DQS Databases</span></span>  
 <span data-ttu-id="27ebd-118">SQL Server Management Studio를 사용하여 DQS 데이터베이스를 분리하는 경우 분리된 파일은 컴퓨터에 남아 있으므로 동일한 SQL Server 인스턴스에 다시 연결되거나 다른 서버로 이동하여 거기에서 연결될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="27ebd-118">When you detach a DQS database using SQL Server Management Studio, the detached files remain on your computer, and can be reattached to the same SQL Server instance or can be can be moved to another server and attached there.</span></span> <span data-ttu-id="27ebd-119">DQS 데이터베이스 파일은 Data Quality Services 컴퓨터의 다음 위치에서 일반적으로 사용할 수 있습니다. C:\Program Files\Microsoft SQL Server\MSSQL12. *<Instance_Name>* \mssql\data</span><span class="sxs-lookup"><span data-stu-id="27ebd-119">The DQS database files are typically available at the following location on your Data Quality Services computer: C:\Program Files\Microsoft SQL Server\MSSQL12.*<Instance_Name>* \MSSQL\DATA.</span></span>  
  
1.  <span data-ttu-id="27ebd-120">Microsoft SQL Server Management Studio를 시작하고 적합한 SQL Server 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="27ebd-120">Start Microsoft SQL Server Management Studio, and connect to the appropriate SQL Server instance.</span></span>  
  
2.  <span data-ttu-id="27ebd-121">개체 탐색기에서 **데이터베이스** 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="27ebd-121">In Object Explorer, expand the **Databases** node.</span></span>  
  
3.  <span data-ttu-id="27ebd-122">**DQS_MAIN** 데이터베이스를 마우스 오른쪽 단추로 클릭하고 **태스크**를 가리킨 다음 **분리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="27ebd-122">Right-click the **DQS_MAIN** database, point to **Tasks**, and then click **Detach**.</span></span> <span data-ttu-id="27ebd-123">**데이터베이스 분리** 대화 상자가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="27ebd-123">The **Detach Database** dialog box appears.</span></span>  
  
4.  <span data-ttu-id="27ebd-124">**삭제** 열 아래 확인란을 선택하고 **확인** 을 클릭하여 DQS_MAIN 데이터베이스를 분리합니다.</span><span class="sxs-lookup"><span data-stu-id="27ebd-124">Select the check box under the **Drop** column, and click **OK** to detach the DQS_MAIN database.</span></span>  
  
5.  <span data-ttu-id="27ebd-125">DQS_PROJECTS 및 DQS_STAGING_DATA 데이터베이스에서 3단계와 4단계를 반복하여 해당 데이터베이스를 분리합니다.</span><span class="sxs-lookup"><span data-stu-id="27ebd-125">Repeat steps 3 and 4 with the DQS_PROJECTS and DQS_STAGING_DATA databases to detach them.</span></span>  
  
 <span data-ttu-id="27ebd-126">Transact-SQL 문에서 sp_detach_db 저장 프로시저를 사용하여 DQS 데이터베이스를 분리할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="27ebd-126">You can also detach DQS databases using the Transact-SQL statements by using the sp_detach_db stored procedure.</span></span> <span data-ttu-id="27ebd-127">Transact-SQL 문을 사용하여 데이터베이스를 분리하는 방법은 [Using Transact-SQL](../relational-databases/databases/detach-a-database.md#TsqlProcedure) 의 [Detach a Database](../relational-databases/databases/detach-a-database.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="27ebd-127">For more information about detaching databases using Transact-SQL statements, see [Using Transact-SQL](../relational-databases/databases/detach-a-database.md#TsqlProcedure) in [Detach a Database](../relational-databases/databases/detach-a-database.md).</span></span>  
  
##  <a name="attach-dqs-databases"></a><a name="Attach"></a><span data-ttu-id="27ebd-128">DQS 데이터베이스 연결</span><span class="sxs-lookup"><span data-stu-id="27ebd-128">Attach DQS Databases</span></span>  
 <span data-ttu-id="27ebd-129">다음 지침을 사용하여 DQS 데이터베이스를 [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] 가 설치된 다른 SQL Server 인스턴스에 연결하거나 분리되었던 SQL Server 인스턴스에 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="27ebd-129">Use the following instructions to attach a DQS database to the same SQL Server instance (from where you detached) or a different SQL Server instance where [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] is installed.</span></span>  
  
1.  <span data-ttu-id="27ebd-130">Microsoft SQL Server Management Studio를 시작하고 적합한 SQL Server 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="27ebd-130">Start Microsoft SQL Server Management Studio, and connect to the appropriate SQL Server instance.</span></span>  
  
2.  <span data-ttu-id="27ebd-131">개체 탐색기에서 **데이터베이스**를 마우스 오른쪽 단추로 클릭한 다음 **연결**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="27ebd-131">In Object Explorer, right-click **Databases**, and then click **Attach**.</span></span> <span data-ttu-id="27ebd-132">**데이터베이스 연결** 대화 상자가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="27ebd-132">The **Attach Databases** dialog box appears.</span></span>  
  
3.  <span data-ttu-id="27ebd-133">연결할 데이터베이스를 지정하려면 **추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="27ebd-133">To specify the database to be attached, click **Add**.</span></span> <span data-ttu-id="27ebd-134">**데이터베이스 파일 찾기** 대화 상자가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="27ebd-134">The **Locate Database Files** dialog box appears.</span></span>  
  
4.  <span data-ttu-id="27ebd-135">데이터베이스가 있는 디스크 드라이브를 선택하고 디렉터리 트리를 확장하여 데이터베이스의 .mdf 파일을 찾은 다음 이 파일을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="27ebd-135">Select the disk drive where the database resides and expand the directory tree to find and select the .mdf file of the database.</span></span> <span data-ttu-id="27ebd-136">예를 들어 DQS_MAIN 데이터베이스의 경우 다음 파일을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="27ebd-136">For example, for the DQS_MAIN database:</span></span>  
  
    ```  
    C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\DATA\DQS_MAIN.mdf  
    ```  
  
5.  <span data-ttu-id="27ebd-137">**데이터베이스 정보** (아래쪽) 창에 연결될 파일 이름이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="27ebd-137">The **database details** (lower) pane displays the names of the files to be attached.</span></span> <span data-ttu-id="27ebd-138">파일의 경로 이름을 확인하거나 변경하려면 **찾아보기** 단추( ... )를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="27ebd-138">To verify or change the pathname of a file, click the **Browse** button (...).</span></span>  
  
6.  <span data-ttu-id="27ebd-139">**확인** 을 클릭하여 DQS_MAIN 데이터베이스를 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="27ebd-139">Click **OK** to attach the DQS_MAIN database.</span></span>  
  
7.  <span data-ttu-id="27ebd-140">DQS_PROJECTS 및 DQS_STAGING_DATA 데이터베이스에서 2~6단계를 반복하여 해당 데이터베이스를 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="27ebd-140">Repeat steps 2-6 for the DQS_PROJECTS and DQS_STAGING_DATA databases to attach them.</span></span>  
  
8.  <span data-ttu-id="27ebd-141">또한 DQS_MAIN 데이터베이스를 복원한 후 다음 단계에서 Transact-SQL 문을 실행해야 합니다. 그렇지 않으면 Data Quality 클라이언트 애플리케이션을 사용하여 Data Quality Server에 연결할 때 오류 메시지가 표시되고 연결할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="27ebd-141">You must also run the Transact-SQL statements in the next step after restoring the DQS_MAIN database otherwise an error message is displayed when you try to connect to Data Quality Server by using the Data Quality Client application, and you cannot connect.</span></span> <span data-ttu-id="27ebd-142">하지만 DQS_PROJECTS 또는 DQS_STAGING_DATA 데이터베이스만 연결하고 DQS_MAIN은 연결하지 않은 경우에는 9단계와 10단계를 수행할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="27ebd-142">However, you do not need to perform steps 9 and 10 if you have just attached the DQS_PROJECTS or DQS_STAGING_DATA database, and not DQS_MAIN.</span></span>  
  
     <span data-ttu-id="27ebd-143">Transact-SQL 문을 실행하려면 개체 탐색기에서 서버를 마우스 오른쪽 단추로 클릭한 다음 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="27ebd-143">To run the Transact-SQL statements, in Object Explorer, right-click the server, and then click **New Query**.</span></span>  
  
9. <span data-ttu-id="27ebd-144">쿼리 편집기 창에서 다음 SQL 문을 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="27ebd-144">In the Query Editor window, copy the following SQL statements:</span></span>  
  
    ```sql  
    ALTER DATABASE [DQS_MAIN] SET TRUSTWORTHY ON;  
    EXEC sp_configure 'clr enabled', 1;  
    RECONFIGURE WITH OVERRIDE  
    ALTER DATABASE [DQS_MAIN] SET ENABLE_BROKER  
    ALTER AUTHORIZATION ON DATABASE::[DQS_MAIN] TO [##MS_dqs_db_owner_login##]  
    ALTER AUTHORIZATION ON DATABASE::[DQS_PROJECTS] TO [##MS_dqs_db_owner_login##]  
    ```  
  
10. <span data-ttu-id="27ebd-145">F5 키를 눌러 문을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="27ebd-145">Press F5 to execute the statements.</span></span> <span data-ttu-id="27ebd-146">결과 창에서 문이 성공적으로 실행되었는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="27ebd-146">Check the Results pane to verify that the statements have executed successfully.</span></span> <span data-ttu-id="27ebd-147">다음 메시지가 표시됩니다. `Configuration option 'clr enabled' changed from 1 to 1. Run the RECONFIGURE statement to install.`</span><span class="sxs-lookup"><span data-stu-id="27ebd-147">You will see the following message: `Configuration option 'clr enabled' changed from 1 to 1. Run the RECONFIGURE statement to install.`</span></span>  
  
11. <span data-ttu-id="27ebd-148">연결할 수 있는지 확인하기 위해 Data Quality 클라이언트를 사용하여 Data Quality Server에 연결해 봅니다.</span><span class="sxs-lookup"><span data-stu-id="27ebd-148">Connect to the Data Quality Server using the Data Quality Client to verify if you can connect successfully.</span></span>  
  
 <span data-ttu-id="27ebd-149">Transact-SQL 문을 사용하여 DQS 데이터베이스를 연결할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="27ebd-149">You can also attach DQS databases using the Transact-SQL statements.</span></span> <span data-ttu-id="27ebd-150">Transact-SQL 문을 사용하여 데이터베이스를 연결하는 방법은 [Using Transact-SQL](../relational-databases/databases/attach-a-database.md#TsqlProcedure) 의 [Attach a Database](../relational-databases/databases/attach-a-database.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="27ebd-150">For more information about attaching databases using Transact-SQL statements, see [Using Transact-SQL](../relational-databases/databases/attach-a-database.md#TsqlProcedure) in [Attach a Database](../relational-databases/databases/attach-a-database.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27ebd-151">참고 항목</span><span class="sxs-lookup"><span data-stu-id="27ebd-151">See Also</span></span>  
 [<span data-ttu-id="27ebd-152">Manage DQS Databases</span><span class="sxs-lookup"><span data-stu-id="27ebd-152">Manage DQS Databases</span></span>](../../2014/data-quality-services/manage-dqs-databases.md)  
  
  
