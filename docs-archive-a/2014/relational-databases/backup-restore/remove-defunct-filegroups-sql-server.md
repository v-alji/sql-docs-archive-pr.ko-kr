---
title: 존재하지 않는 파일 그룹 제거(SQL Server) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- piecemeal restores [SQL Server], defunct filegroups
- defunct filegroups
- restoring filegroups [SQL Server]
- deferred transactions
- filegroups [SQL Server], defunct
- unrestored filegroups
ms.assetid: 055f9c6a-5c18-4942-98e7-ec918f0ff975
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: a2bcba095d668c5c1ab317269a18af4dc996f63b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736430"
---
# <a name="remove-defunct-filegroups-sql-server"></a><span data-ttu-id="5a83c-102">존재하지 않는 파일 그룹 제거(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="5a83c-102">Remove Defunct Filegroups (SQL Server)</span></span>
  <span data-ttu-id="5a83c-103">이 항목에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 또는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 을 사용하여 [!INCLUDE[tsql](../../includes/tsql-md.md)]에서 존재하지 않는 파일 그룹을 제거하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="5a83c-103">This topic describes how to remove defunct filegroups in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="5a83c-104">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="5a83c-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="5a83c-105">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="5a83c-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="5a83c-106">제한 사항</span><span class="sxs-lookup"><span data-stu-id="5a83c-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
-   [<span data-ttu-id="5a83c-107">권장 사항</span><span class="sxs-lookup"><span data-stu-id="5a83c-107">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="5a83c-108">보안</span><span class="sxs-lookup"><span data-stu-id="5a83c-108">Security</span></span>](#Security)  
  
-   <span data-ttu-id="5a83c-109">**존재하지 않는 파일 그룹을 제거하려면:**</span><span class="sxs-lookup"><span data-stu-id="5a83c-109">**To remove defunct filegroups, using:**</span></span>  
  
     [<span data-ttu-id="5a83c-110">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="5a83c-110">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="5a83c-111">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="5a83c-111">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="5a83c-112">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="5a83c-112">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="5a83c-113">제한 사항</span><span class="sxs-lookup"><span data-stu-id="5a83c-113">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="5a83c-114">이 항목에서는 여러 개의 파일 또는 파일 그룹이 있는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스와 관련된 내용 및 단순 모델의 경우 읽기 전용 파일 그룹과 관련된 내용을 다룹니다.</span><span class="sxs-lookup"><span data-stu-id="5a83c-114">This topic is relevant for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases that contain multiple files or filegroups; and, under the simple model, only for read-only filegroups.</span></span>  
  
-   <span data-ttu-id="5a83c-115">오프라인 파일 그룹이 제거되면 파일 그룹의 모든 파일이 존재하지 않음 상태가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5a83c-115">All files in a filegroup become defunct when an offline filegroup is removed.</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="5a83c-116">권장 사항</span><span class="sxs-lookup"><span data-stu-id="5a83c-116">Recommendations</span></span>  
  
-   <span data-ttu-id="5a83c-117">복원되지 않은 파일 그룹을 복원할 필요가 없는 경우 데이터베이스에서 해당 파일 그룹을 제거하여 *존재하지 않는* 파일 그룹으로 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5a83c-117">If an unrestored filegroup will never have to be restored, you can make the filegroup *defunct* by removing it from the database.</span></span> <span data-ttu-id="5a83c-118">존재하지 않는 파일 그룹은 이 데이터베이스로 복원될 수 없지만 해당 메타데이터는 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="5a83c-118">The defunct filegroup can never be restored to this database, but its metadata remains.</span></span> <span data-ttu-id="5a83c-119">파일 그룹이 존재하지 않는 상태가 된 후 데이터베이스를 다시 시작할 수 있으며 복원된 파일 그룹 간에 데이터베이스의 일관성을 복구를 통해 유지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5a83c-119">After the filegroup is defunct, the database can be restarted, and recovery will make the database consistent across the restored filegroups.</span></span>  
  
     <span data-ttu-id="5a83c-120">예를 들어 데이터베이스에서 더 이상 필요하지 않은 오프라인 파일 그룹으로 인해 트랜잭션이 지연되는 문제를 해결하기 위한 한 가지 방법으로 파일 그룹을 존재하지 않는 상태로 만드는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="5a83c-120">For example, making a filegroup defunct is an option for resolving deferred transactions that were caused by an offline filegroup that you no longer want in the database.</span></span> <span data-ttu-id="5a83c-121">파일 그룹이 오프라인 상태이므로 지연된 트랜잭션은 이 파일 그룹이 존재하지 않게 된 후에 지연된 상태에서 벗어납니다.</span><span class="sxs-lookup"><span data-stu-id="5a83c-121">Transactions that were deferred because the filegroup was offline are moved out of the deferred state after the filegroup becomes defunct.</span></span> <span data-ttu-id="5a83c-122">자세한 내용은 [지연된 트랜잭션&#40;SQL Server&#41;](deferred-transactions-sql-server.md)에서 존재하지 않는 파일 그룹을 제거하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="5a83c-122">For more information, see [Deferred Transactions &#40;SQL Server&#41;](deferred-transactions-sql-server.md).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="5a83c-123">보안</span><span class="sxs-lookup"><span data-stu-id="5a83c-123">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="5a83c-124">권한</span><span class="sxs-lookup"><span data-stu-id="5a83c-124">Permissions</span></span>  
 <span data-ttu-id="5a83c-125">데이터베이스에 대한 ALTER 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="5a83c-125">Requires ALTER permission on the database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="5a83c-126">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="5a83c-126">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-remove-defunct-filegroups"></a><span data-ttu-id="5a83c-127">존재하지 않는 파일 그룹을 제거하려면</span><span class="sxs-lookup"><span data-stu-id="5a83c-127">To remove defunct filegroups</span></span>  
  
1.  <span data-ttu-id="5a83c-128">**개체 탐색기**에서 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 의 인스턴스에 연결한 다음 해당 인스턴스를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="5a83c-128">In **Object Explorer**, connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="5a83c-129">**데이터베이스**를 확장하고 파일을 삭제할 데이터베이스를 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5a83c-129">Expand **Databases**, right-click the database from which to delete the file, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="5a83c-130">**파일** 페이지를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="5a83c-130">Select the **Files** page.</span></span>  
  
4.  <span data-ttu-id="5a83c-131">**데이터베이스 파일** 표에서 삭제할 파일을 선택하고 **제거**를 클릭한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5a83c-131">In the **Database files** grid, select the files to delete, click **Remove**, and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="5a83c-132">**파일 그룹** 페이지를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="5a83c-132">Select the **Filegroups** page.</span></span>  
  
6.  <span data-ttu-id="5a83c-133">**행** 표에서 삭제할 파일 그룹을 선택하고 **제거**를 클릭한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5a83c-133">In the **Rows** grid, select the filegroup to delete, click **Remove**, and then click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="5a83c-134">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="5a83c-134">Using Transact-SQL</span></span>  
  
#### <a name="to-remove-defunct-filegroups"></a><span data-ttu-id="5a83c-135">존재하지 않는 파일 그룹을 제거하려면</span><span class="sxs-lookup"><span data-stu-id="5a83c-135">To remove defunct filegroups</span></span>  
  
1.  <span data-ttu-id="5a83c-136">[!INCLUDE[ssDE](../../includes/ssde-md.md)]에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="5a83c-136">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="5a83c-137">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5a83c-137">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="5a83c-138">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5a83c-138">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="5a83c-139">(**참고:** 이 예제에서는 파일과 파일 그룹이 이미 있다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="5a83c-139">(**Note:** This example assumes that the files and filegroup already exist.</span></span> <span data-ttu-id="5a83c-140">이러한 개체를 만들려면 [ALTER DATABASE 파일 및 파일 그룹 옵션](/sql/t-sql/statements/alter-database-transact-sql-file-and-filegroup-options) 항목의 예제 B를 참조하세요. 첫 번째 예에서는 `test1dat3` 절과 함께 `test1dat4` 문을 사용하여 존재하지 않는 파일 그룹에서 `ALTER DATABASE` 및 `REMOVE FILE` 파일을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="5a83c-140">To create these objects, see example B in the [ALTER DATABASE File and Filegroup Options](/sql/t-sql/statements/alter-database-transact-sql-file-and-filegroup-options) topic.) The first example removes the `test1dat3` and `test1dat4` files from the defunct filegroup by using the `ALTER DATABASE` statement with the `REMOVE FILE` clause.</span></span> <span data-ttu-id="5a83c-141">두 번째 예에서는 `Test1FG1`절을 사용하여 존재하지 않는 파일 그룹 `REMOVE FILEGROUP` 을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="5a83c-141">The second example removes the defunct filegroup `Test1FG1`by using the `REMOVE FILEGROUP` clause.</span></span>  
  
```sql  
USE master;  
GO  
ALTER DATABASE AdventureWorks2012  
REMOVE FILE test1dat3 ;  
ALTER DATABASE AdventureWorks2012  
REMOVE FILE test1dat4 ;  
GO  
  
```  
  
```sql  
USE master;  
GO  
ALTER DATABASE AdventureWorks2012  
REMOVE FILEGROUP Test1FG1 ;  
GO  
  
```  
  
## <a name="see-also"></a><span data-ttu-id="5a83c-142">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5a83c-142">See Also</span></span>  
 <span data-ttu-id="5a83c-143">[ALTER DATABASE 파일 및 파일 그룹 옵션&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-file-and-filegroup-options) </span><span class="sxs-lookup"><span data-stu-id="5a83c-143">[ALTER DATABASE File and Filegroup Options &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-file-and-filegroup-options) </span></span>  
 <span data-ttu-id="5a83c-144">[지연된 트랜잭션&#40;SQL Server&#41;](deferred-transactions-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="5a83c-144">[Deferred Transactions &#40;SQL Server&#41;](deferred-transactions-sql-server.md) </span></span>  
 <span data-ttu-id="5a83c-145">[파일 복원&#40;전체 복구 모델&#41;](file-restores-full-recovery-model.md) </span><span class="sxs-lookup"><span data-stu-id="5a83c-145">[File Restores &#40;Full Recovery Model&#41;](file-restores-full-recovery-model.md) </span></span>  
 <span data-ttu-id="5a83c-146">[파일 복원&#40;단순 복구 모델&#41;](file-restores-simple-recovery-model.md) </span><span class="sxs-lookup"><span data-stu-id="5a83c-146">[File Restores &#40;Simple Recovery Model&#41;](file-restores-simple-recovery-model.md) </span></span>  
 <span data-ttu-id="5a83c-147">[온라인 복원&#40;SQL Server&#41;](online-restore-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="5a83c-147">[Online Restore &#40;SQL Server&#41;](online-restore-sql-server.md) </span></span>  
 <span data-ttu-id="5a83c-148">[페이지 복원&#40;SQL Server&#41;](restore-pages-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="5a83c-148">[Restore Pages &#40;SQL Server&#41;](restore-pages-sql-server.md) </span></span>  
 [<span data-ttu-id="5a83c-149">증분 복원&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="5a83c-149">Piecemeal Restores &#40;SQL Server&#41;</span></span>](piecemeal-restores-sql-server.md)  
  
  
