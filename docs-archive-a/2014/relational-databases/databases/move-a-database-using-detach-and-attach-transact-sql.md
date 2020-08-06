---
title: 분리 및 연결을 사용하여 데이터베이스 이동(Transact-SQL) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- database attaching [SQL Server]
- moving databases [SQL Server]
- database detaching [SQL Server]
- relocating databases [SQL Server]
- detaching databases [SQL Server]
- attaching databases [SQL Server]
ms.assetid: 6732a431-cdef-4f1e-9262-4ac3b77c275e
author: stevestein
ms.author: sstein
ms.openlocfilehash: 768a70dfe94af6f8d65f7c76fa08d3dff650fe7d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661131"
---
# <a name="move-a-database-using-detach-and-attach-transact-sql"></a><span data-ttu-id="9834d-102">분리 및 연결을 사용하여 데이터베이스 이동(Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="9834d-102">Move a Database Using Detach and Attach (Transact-SQL)</span></span>
  <span data-ttu-id="9834d-103">이 항목에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]에서 분리된 데이터베이스를 다른 위치로 이동하고 동일한 서버 인스턴스나 다른 서버 인스턴스에 다시 연결하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="9834d-103">This topic describes how to move a detached database to another location and re-attach it to the same or a different server instance in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="9834d-104">하지만 데이터베이스를 이동할 때는 분리 및 연결 작업 대신 계획된 ALTER DATABASE 재배치 프로시저를 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="9834d-104">However, we recommend that you move databases by using the ALTER DATABASE planned relocation procedure, instead of using detach and attach.</span></span> <span data-ttu-id="9834d-105">자세한 내용은 [Move User Databases](move-user-databases.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9834d-105">For more information, see [Move User Databases](move-user-databases.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="9834d-106">알 수 없거나 신뢰할 수 없는 출처의 데이터베이스는 연결 또는 복원하지 않는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="9834d-106">We recommend that you do not attach or restore databases from unknown or untrusted sources.</span></span> <span data-ttu-id="9834d-107">이러한 데이터베이스에 포함된 악성 코드가 의도하지 않은 [!INCLUDE[tsql](../../includes/tsql-md.md)] 코드를 실행하거나 스키마 또는 물리적 데이터베이스 구조를 수정하여 오류가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9834d-107">Such databases could contain malicious code that might execute unintended [!INCLUDE[tsql](../../includes/tsql-md.md)] code or cause errors by modifying the schema or the physical database structure.</span></span> <span data-ttu-id="9834d-108">알 수 없거나 신뢰할 수 없는 소스의 데이터베이스를 사용하기 전에 비프로덕션 서버의 데이터베이스에서 [DBCC CHECKDB](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) 를 실행하여 데이터베이스에서 코드(예: 저장 프로시저 또는 다른 사용자 정의 코드)를 시험해 보세요.</span><span class="sxs-lookup"><span data-stu-id="9834d-108">Before you use a database from an unknown or untrusted source, run [DBCC CHECKDB](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) on the database on a nonproduction server and also examine the code, such as stored procedures or other user-defined code, in the database.</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="9834d-109">절차</span><span class="sxs-lookup"><span data-stu-id="9834d-109">Procedure</span></span>  
  
#### <a name="to-move-a-database-by-using-detach-and-attach"></a><span data-ttu-id="9834d-110">분리 및 연결 작업을 사용하여 데이터베이스를 이동하려면</span><span class="sxs-lookup"><span data-stu-id="9834d-110">To move a database by using detach and attach</span></span>  
  
1.  <span data-ttu-id="9834d-111">데이터베이스를 분리합니다.</span><span class="sxs-lookup"><span data-stu-id="9834d-111">Detach the database.</span></span> <span data-ttu-id="9834d-112">자세한 내용은 [데이터베이스 분리](detach-a-database.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9834d-112">For more information, see [Detach a Database](detach-a-database.md).</span></span>  
  
2.  <span data-ttu-id="9834d-113">Windows 탐색기나 Windows 명령 프롬프트 창에서 분리된 데이터베이스 파일과 로그 파일을 새 위치로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="9834d-113">In a Windows Explorer or Windows Command Prompt window, move the detached database file or files and log file or files to the new location.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="9834d-114">전자 메일로 보낼 수 있을 정도로 파일 크기가 작으면 한 개의 파일로 구성된 데이터베이스를 이동하는 데 전자 메일을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9834d-114">To move a single-file database, you can use email if the file size is small enough for email to accommodate.</span></span>  
  
     <span data-ttu-id="9834d-115">새 로그 파일을 작성할 경우에도 로그 파일을 이동해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9834d-115">You should move the log files even if you intend to create new log files.</span></span> <span data-ttu-id="9834d-116">경우에 따라 데이터베이스를 다시 연결하려면 기존 로그 파일이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="9834d-116">In some cases, reattaching a database requires its existing log files.</span></span> <span data-ttu-id="9834d-117">따라서 데이터베이스가 분리된 로그 파일 없이도 성공적으로 연결될 때까지 모든 분리된 로그 파일을 항상 보존하세요.</span><span class="sxs-lookup"><span data-stu-id="9834d-117">Therefore, always keep all the detached log files until the database has been successfully attached without them.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="9834d-118">로그 파일을 지정하지 않고 데이터베이스를 연결할 경우 연결 작업은 원래 위치에서 로그 파일을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="9834d-118">If you try to attach the database without specifying the log file, the attach operation will look for the log file in its original location.</span></span> <span data-ttu-id="9834d-119">원래 위치에 로그 복사본이 있으면 해당 복사본이 연결됩니다.</span><span class="sxs-lookup"><span data-stu-id="9834d-119">If a copy of the log still exists in the original location, that copy is attached.</span></span> <span data-ttu-id="9834d-120">원래 로그 파일을 사용하지 않으려면 새 로그 파일의 경로를 지정하거나 로그 파일의 원본을 새 위치로 복사한 후 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="9834d-120">To avoid using the original log file, either specify the path of the new log file or remove the original copy of the log file (after copying it to the new location).</span></span>  
  
3.  <span data-ttu-id="9834d-121">복사된 파일을 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="9834d-121">Attach the copied files.</span></span> <span data-ttu-id="9834d-122">자세한 내용은 [Attach a Database](attach-a-database.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9834d-122">For more information, see [Attach a Database](attach-a-database.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9834d-123">예제</span><span class="sxs-lookup"><span data-stu-id="9834d-123">Example</span></span>  
 <span data-ttu-id="9834d-124">다음 예에서는 [!INCLUDE[ssSampleDBnormal](../../includes/tsql-md.md)] 가 연결 된 서버 인스턴스에 연결 된 쿼리 편집기 창에서 실행 되는 문의 복사본을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="9834d-124">The following example creates a copy of the [!INCLUDE[ssSampleDBnormal](../../includes/tsql-md.md)] statements are executed in a Query Editor window that is connected to the server instance to which is attached.</span></span>  
  
1.  <span data-ttu-id="9834d-125">문을 분리 합니다 [!INCLUDE[ssSampleDBnormal](../../includes/tsql-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="9834d-125">Detach the [!INCLUDE[ssSampleDBnormal](../../includes/tsql-md.md)] statements:</span></span>  
  
    ```  
    USE master;  
    GO  
    EXEC sp_detach_db @dbname = N'AdventureWorks2012';  
    GO  
    ```  
  
2.  <span data-ttu-id="9834d-126">선택한 방법을 사용하여 데이터베이스 파일(AdventureWorks208R2_Data.mdf 및 AdventureWorks208R2_log)을 각각 C:\MySQLServer\AdventureWorks208R2_Data.mdf 및 C:\MySQLServer\AdventureWorks208R2_Log.ldf로 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="9834d-126">Using the method of your choice, copy the database files (AdventureWorks208R2_Data.mdf and AdventureWorks208R2_log) to: C:\MySQLServer\AdventureWorks208R2_Data.mdf and C:\MySQLServer\AdventureWorks208R2_Log.ldf, respectively.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="9834d-127">프로덕션 데이터베이스의 경우 데이터베이스와 트랜잭션 로그를 별도의 디스크에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="9834d-127">For a production database, place the database and transaction log on separate disks.</span></span>  
  
     <span data-ttu-id="9834d-128">네트워크를 통해 원격 컴퓨터의 디스크로 파일을 복사하려면 원격 위치의 UNC(Universal Naming Convention) 이름을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="9834d-128">To copy files over the network to a disk on a remote computer, use the universal naming convention (UNC) name of the remote location.</span></span> <span data-ttu-id="9834d-129">UNC 이름의 형식은 **\\\\** _Servername_ **\\** _Sharename_ **\\** _Path_ **\\** _Filename_입니다.</span><span class="sxs-lookup"><span data-stu-id="9834d-129">A UNC name takes the form **\\\\**_Servername_**\\**_Sharename_**\\**_Path_**\\**_Filename_.</span></span> <span data-ttu-id="9834d-130">로컬 하드 디스크에 파일을 쓸 경우 원격 디스크의 파일을 읽거나 파일에 쓰는 데 필요한 해당 권한은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스에서 사용하는 사용자 계정에게 부여되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9834d-130">As with writing files to the local hard disk, the appropriate permissions that are required to read or write to a file on the remote disk must be granted to the user account used by the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
3.  <span data-ttu-id="9834d-131">다음 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문을 실행하여 이동된 데이터베이스와 필요에 따라 해당 로그를 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="9834d-131">Attach the moved database and, optionally, its log by executing the following [!INCLUDE[tsql](../../includes/tsql-md.md)] statements:</span></span>  
  
    ```  
    USE master;  
    GO  
    CREATE DATABASE MyAdventureWorks   
        ON (FILENAME = 'C:\MySQLServer\AdventureWorks2012_Data.mdf'),  
        (FILENAME = 'C:\MySQLServer\AdventureWorks2012_Log.ldf')  
        FOR ATTACH;  
    GO  
    ```  
  
     <span data-ttu-id="9834d-132">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서 새로 연결되는 데이터베이스는 개체 탐색기에 즉시 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9834d-132">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], a newly attached database is not immediately visible in Object Explorer.</span></span> <span data-ttu-id="9834d-133">데이터베이스를 보려면 개체 탐색기에서 **보기** , **새로 고침**을 차례로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9834d-133">To view the database, in Object Explorer, click **View,** and then **Refresh**.</span></span> <span data-ttu-id="9834d-134">개체 탐색기에서 **데이터베이스** 노드가 확장될 때 새로 연결된 데이터베이스가 데이터베이스 목록에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="9834d-134">When the **Databases** node is expanded in Object Explorer, the newly attached database now appears in the list of databases.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9834d-135">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9834d-135">See Also</span></span>  
 [<span data-ttu-id="9834d-136">데이터베이스 분리 및 연결&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="9834d-136">Database Detach and Attach &#40;SQL Server&#41;</span></span>](database-detach-and-attach-sql-server.md)  
  
  
