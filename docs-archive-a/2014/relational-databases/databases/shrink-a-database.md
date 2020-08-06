---
title: 데이터베이스 축소 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- sql12.swb.shrinkdatabase.f1
helpviewer_keywords:
- shrinking databases
- databases [SQL Server], shrinking
- decreasing database size
- database shrinking [SQL Server]
- reducing database size
ms.assetid: 83afbf74-fd50-4c39-831c-b1f473a50620
author: stevestein
ms.author: sstein
ms.openlocfilehash: 246036bfea6dc8431f878165330f7f0571949897
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728331"
---
# <a name="shrink-a-database"></a><span data-ttu-id="62e05-102">데이터베이스 축소</span><span class="sxs-lookup"><span data-stu-id="62e05-102">Shrink a Database</span></span>
  <span data-ttu-id="62e05-103">이 항목에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 또는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 과 [!INCLUDE[tsql](../../includes/tsql-md.md)]의 개체를 사용하여 데이터베이스를 축소하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="62e05-103">This topic describes how to shrink a database by using Object in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="62e05-104">파일 끝에 있는 데이터 페이지를 파일 앞의 사용되지 않은 공간으로 이동하여 데이터 파일을 축소하면 공간이 복구됩니다.</span><span class="sxs-lookup"><span data-stu-id="62e05-104">Shrinking data files recovers space by moving pages of data from the end of the file to unoccupied space closer to the front of the file.</span></span> <span data-ttu-id="62e05-105">파일 끝에 사용 가능한 공간을 충분히 확보한 다음 파일 끝에 있는 데이터 페이지를 할당 해제하고 파일 시스템에 반환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="62e05-105">When enough free space is created at the end of the file, data pages at end of the file can be deallocated and returned to the file system.</span></span>  
  

  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="62e05-106">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="62e05-106">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="62e05-107">제한 사항</span><span class="sxs-lookup"><span data-stu-id="62e05-107">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="62e05-108">데이터베이스를 최소 데이터베이스 크기보다 작게 축소할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="62e05-108">The database cannot be made smaller than the minimum size of the database.</span></span> <span data-ttu-id="62e05-109">최소 크기는 데이터베이스를 처음 만들 때 지정된 크기나 DBCC SHRINKFILE과 같은 파일 크기 변경 작업을 사용하여 명시적으로 설정한 최종 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="62e05-109">The minimum size is the size specified when the database was originally created, or the last explicit size set by using a file-size-changing operation, such as DBCC SHRINKFILE.</span></span> <span data-ttu-id="62e05-110">예를 들어 원래 10MB로 생성된 데이터베이스가 100MB까지 증가한 경우 포함된 모든 데이터를 삭제하더라도 데이터베이스를 10MB 이하로는 축소할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="62e05-110">For example, if a database was originally created with a size of 10 MB and grew to 100 MB, the smallest size the database could be reduced to is 10 MB, even if all the data in the database has been deleted.</span></span>  
  
-   <span data-ttu-id="62e05-111">데이터베이스가 백업되는 동안에는 데이터베이스를 축소할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="62e05-111">You cannot shrink a database while the database is being backed up.</span></span> <span data-ttu-id="62e05-112">반대로 데이터베이스에 대한 축소 작업이 처리되는 동안에는 데이터베이스를 백업할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="62e05-112">Conversely, you cannot backup a database while a shrink operation on the database is in process.</span></span>  
  
-   <span data-ttu-id="62e05-113">xVelocity 메모리 최적화 Columnstore 인덱스가 발생할 경우 DBCC SHRINKDATABASE는 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="62e05-113">DBCC SHRINKDATABASE will fail when it encounters an xVelocity memory optimized columnstore index.</span></span> <span data-ttu-id="62e05-114">Columnstore 인덱스가 발생하기 전에 완료된 작업은 성공하므로 데이터베이스 크기가 작아질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="62e05-114">Work completed before encountering the columnstore index will succeed so the database might be smaller.</span></span> <span data-ttu-id="62e05-115">DBCC SHRINKDATABASE를 완료하려면 DBCC SHRINKDATABASE를 실행하기 전에 모든 columnstore 인덱스를 사용하지 않도록 설정한 다음 columnstore 인덱스를 다시 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="62e05-115">To complete DBCC SHRINKDATABASE, disable all columnstore indexes before executing DBCC SHRINKDATABASE, and then rebuild the columnstore indexes.</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="62e05-116">권장 사항</span><span class="sxs-lookup"><span data-stu-id="62e05-116">Recommendations</span></span>  
  
-   <span data-ttu-id="62e05-117">현재 데이터베이스에 있는 여유(할당되지 않은) 공간의 양을 보려면</span><span class="sxs-lookup"><span data-stu-id="62e05-117">To view the current amount of free (unallocated) space in the database.</span></span> <span data-ttu-id="62e05-118">자세한 내용은 [데이터베이스의 데이터 및 로그 공간 정보 표시](display-data-and-log-space-information-for-a-database.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="62e05-118">For more information, see [Display Data and Log Space Information for a Database](display-data-and-log-space-information-for-a-database.md)</span></span>  
  
-   <span data-ttu-id="62e05-119">데이터베이스를 축소할 때는 다음을 고려하세요.</span><span class="sxs-lookup"><span data-stu-id="62e05-119">Consider the following information when you plan to shrink a database:</span></span>  
  
    -   <span data-ttu-id="62e05-120">축소 작업은 테이블 잘라내기 또는 테이블 삭제 작업과 같이 사용되지 않는 공간이 많이 생기는 작업을 수행한 후에 가장 효과적입니다.</span><span class="sxs-lookup"><span data-stu-id="62e05-120">A shrink operation is most effective after an operation that creates lots of unused space, such as a truncate table or a drop table operation.</span></span>  
  
    -   <span data-ttu-id="62e05-121">대부분의 데이터베이스에는 정기적인 일상 작업에 사용 가능한 일정 여유 공간이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="62e05-121">Most databases require some free space to be available for regular day-to-day operations.</span></span> <span data-ttu-id="62e05-122">데이터베이스를 반복해서 축소했지만 데이터베이스 크기가 다시 늘어나는 경우 일반 작업을 위해 축소된 공간이 필요한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="62e05-122">If you shrink a database repeatedly and notice that the database size grows again, this indicates that the space that was shrunk is required for regular operations.</span></span> <span data-ttu-id="62e05-123">이러한 경우 데이터베이스를 반복해서 축소하는 것은 불필요한 작업입니다.</span><span class="sxs-lookup"><span data-stu-id="62e05-123">In these cases, repeatedly shrinking the database is a wasted operation.</span></span>  
  
    -   <span data-ttu-id="62e05-124">축소 작업은 데이터베이스 인덱스의 조각화 상태를 보존하지 않으며 일반적으로 조각화 정도를 어느 정도까지 늘리기도 합니다.</span><span class="sxs-lookup"><span data-stu-id="62e05-124">A shrink operation does not preserve the fragmentation state of indexes in the database, and generally increases fragmentation to a degree.</span></span> <span data-ttu-id="62e05-125">이것은 데이터베이스를 반복해서 축소하지 않아야 하는 또 다른 이유입니다.</span><span class="sxs-lookup"><span data-stu-id="62e05-125">This is another reason not to repeatedly shrink the database.</span></span>  
  
    -   <span data-ttu-id="62e05-126">특정 요구 사항이 없을 경우 AUTO_SHRINK 데이터베이스 옵션을 ON으로 설정하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="62e05-126">Unless you have a specific requirement, do not set the AUTO_SHRINK database option to ON.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="62e05-127">보안</span><span class="sxs-lookup"><span data-stu-id="62e05-127">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="62e05-128">권한</span><span class="sxs-lookup"><span data-stu-id="62e05-128">Permissions</span></span>  
 <span data-ttu-id="62e05-129">**sysadmin** 고정 서버 역할의 멤버 또는 **db_owner** 고정 데이터베이스 역할의 멤버여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="62e05-129">Requires membership in the **sysadmin** fixed server role or the **db_owner** fixed database role.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="62e05-130">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="62e05-130">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-shrink-a-database"></a><span data-ttu-id="62e05-131">데이터베이스를 축소하려면</span><span class="sxs-lookup"><span data-stu-id="62e05-131">To shrink a database</span></span>  
  
1.  <span data-ttu-id="62e05-132">**개체 탐색기**에서 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]의 인스턴스에 연결한 다음 해당 인스턴스를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="62e05-132">In **Object Explorer**, connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="62e05-133">**데이터베이스**를 확장한 다음 축소할 데이터베이스를 마우스 오른쪽 단추로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="62e05-133">Expand **Databases**, and then right-click the database that you want to shrink.</span></span>  
  
3.  <span data-ttu-id="62e05-134">**태스크**, **축소**를 차례로 가리킨 다음 **데이터베이스**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="62e05-134">Point to **Tasks**, point to **Shrink**, and then click **Database**.</span></span>  
  
     <span data-ttu-id="62e05-135">**Database**</span><span class="sxs-lookup"><span data-stu-id="62e05-135">**Database**</span></span>  
     <span data-ttu-id="62e05-136">선택한 데이터베이스의 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="62e05-136">Displays the name of the selected database.</span></span>  
  
     <span data-ttu-id="62e05-137">**현재 할당된 공간**</span><span class="sxs-lookup"><span data-stu-id="62e05-137">**Current allocated space**</span></span>  
     <span data-ttu-id="62e05-138">선택한 데이터베이스의 총 사용 공간 및 사용되지 않은 공간을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="62e05-138">Displays the total used and unused space for the selected database.</span></span>  
  
     <span data-ttu-id="62e05-139">**사용 가능한 공간**</span><span class="sxs-lookup"><span data-stu-id="62e05-139">**Available free space**</span></span>  
     <span data-ttu-id="62e05-140">선택한 데이터베이스의 로그 및 데이터 파일의 총 사용 가능한 공간을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="62e05-140">Displays the sum of free space in the log and data files of the selected database.</span></span>  
  
     <span data-ttu-id="62e05-141">**사용하지 않은 공간을 해제하기 전에 파일을 다시 구성합니다.**</span><span class="sxs-lookup"><span data-stu-id="62e05-141">**Reorganize files before releasing unused space**</span></span>  
     <span data-ttu-id="62e05-142">이 옵션을 선택하는 것은 목표 백분율 옵션을 지정하여 DBCC SHRINKDATABASE를 실행하는 것과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="62e05-142">Selecting this option is equivalent to executing DBCC SHRINKDATABASE specifying a target percent option.</span></span> <span data-ttu-id="62e05-143">또한 이 옵션의 선택을 취소하는 것은 TRUNCATEONLY 옵션을 사용하여 DBCC SHRINKDATABASE를 실행하는 것과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="62e05-143">Clearing this option is equivalent to executing DBCC SHRINKDATABASE with TRUNCATEONLY option.</span></span> <span data-ttu-id="62e05-144">기본적으로 대화 상자를 열 때 이 옵션은 선택되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="62e05-144">By default, this option is not selected when the dialog is opened.</span></span> <span data-ttu-id="62e05-145">이 옵션을 선택하면 목표 백분율 옵션을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="62e05-145">If this option is selected, the user must specify a target percent option.</span></span>  
  
     <span data-ttu-id="62e05-146">**축소 후 파일에 남는 최대 여유 공간**</span><span class="sxs-lookup"><span data-stu-id="62e05-146">**Maximum free space in files after shrinking**</span></span>  
     <span data-ttu-id="62e05-147">데이터베이스를 축소한 후 데이터베이스 파일에 남겨둘 여유 공간의 최대 비율을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="62e05-147">Enter the maximum percentage of free space to be left in the database files after the database has been shrunk.</span></span> <span data-ttu-id="62e05-148">허용되는 값은 0에서 99까지입니다.</span><span class="sxs-lookup"><span data-stu-id="62e05-148">Permissible values are between 0 and 99.</span></span>  
  
4.  <span data-ttu-id="62e05-149">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="62e05-149">Click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="62e05-150">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="62e05-150">Using Transact-SQL</span></span>  
  
#### <a name="to-shrink-a-database"></a><span data-ttu-id="62e05-151">데이터베이스를 축소하려면</span><span class="sxs-lookup"><span data-stu-id="62e05-151">To shrink a database</span></span>  
  
1.  <span data-ttu-id="62e05-152">[!INCLUDE[ssDE](../../includes/ssde-md.md)]에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="62e05-152">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="62e05-153">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="62e05-153">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="62e05-154">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="62e05-154">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="62e05-155">이 예에서는 [DBCC SHRINKDATABASE](/sql/t-sql/database-console-commands/dbcc-shrinkdatabase-transact-sql) 를 사용하여 `UserDB` 데이터베이스의 데이터 및 로그 파일 크기를 줄이고 데이터베이스에 `10` 의 여유 공간이 남도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="62e05-155">This example uses [DBCC SHRINKDATABASE](/sql/t-sql/database-console-commands/dbcc-shrinkdatabase-transact-sql) to decreases the size of the data and log files in the `UserDB` database and to allow for `10` percent free space in the database.</span></span>  
  
 [!code-sql[DBCC#DBCC_SHRINKDB1](../../snippets/tsql/SQL14/tsql/dbcc/transact-sql/dbcc_other.sql#dbcc_shrinkdb1)]  
  
##  <a name="follow-up-after-you-shrink-a-database"></a><a name="FollowUp"></a> <span data-ttu-id="62e05-156">후속 작업: 데이터베이스를 축소한 후</span><span class="sxs-lookup"><span data-stu-id="62e05-156">Follow Up: After you shrink a database</span></span>  
 <span data-ttu-id="62e05-157">파일 축소를 위해 이동되는 데이터는 파일 내의 모든 사용 가능한 위치로 분산될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="62e05-157">Data that is moved to shrink a file can be scattered to any available location in the file.</span></span> <span data-ttu-id="62e05-158">이로 인해 인덱스 조각화가 발생하여 인덱스 범위를 검색하는 쿼리 성능이 저하될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="62e05-158">This causes index fragmentation and can slow the performance of queries that search a range of the index.</span></span> <span data-ttu-id="62e05-159">조각화를 방지하려면 축소 후 파일에 대한 인덱스를 다시 작성하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="62e05-159">To eliminate the fragmentation, consider rebuilding the indexes on the file after shrinking.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62e05-160">참고 항목</span><span class="sxs-lookup"><span data-stu-id="62e05-160">See Also</span></span>  
 <span data-ttu-id="62e05-161">[파일 축소](shrink-a-file.md) </span><span class="sxs-lookup"><span data-stu-id="62e05-161">[Shrink a File](shrink-a-file.md) </span></span>  
 <span data-ttu-id="62e05-162">[sys.databases&#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="62e05-162">[sys.databases &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) </span></span>  
 <span data-ttu-id="62e05-163">[sys.database_files&#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-files-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="62e05-163">[sys.database_files &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-files-transact-sql) </span></span>  
 <span data-ttu-id="62e05-164">[DBCC&#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="62e05-164">[DBCC &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-transact-sql) </span></span>  
 <span data-ttu-id="62e05-165">[DBCC SHRINKFILE&#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-shrinkfile-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="62e05-165">[DBCC SHRINKFILE &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-shrinkfile-transact-sql) </span></span>  
 [<span data-ttu-id="62e05-166">데이터베이스 파일 및 파일 그룹</span><span class="sxs-lookup"><span data-stu-id="62e05-166">Database Files and Filegroups</span></span>](database-files-and-filegroups.md)  
  
  
