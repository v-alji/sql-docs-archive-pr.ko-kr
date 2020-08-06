---
title: 데이터베이스 삭제 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- database removal [SQL Server], SQL Server Management Studio
- removing databases
- deleting databases
- dropping databases
- databases [SQL Server], dropping
- database removal [SQL Server]
ms.assetid: 1fd8c0f5-03e1-449a-af45-b8cacb479d9c
author: stevestein
ms.author: sstein
ms.openlocfilehash: 633d97815cf69da12f1aa67fd8ef626a2d46e0b0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742199"
---
# <a name="delete-a-database"></a><span data-ttu-id="7b563-102">데이터베이스 삭제</span><span class="sxs-lookup"><span data-stu-id="7b563-102">Delete a Database</span></span>
  <span data-ttu-id="7b563-103">이 항목에서는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 또는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 을 사용하여 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 의 [!INCLUDE[tsql](../../includes/tsql-md.md)]에서 사용자 정의 데이터베이스를 삭제하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="7b563-103">This topic describes how to delete a user-defined database in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="7b563-104">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="7b563-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="7b563-105">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="7b563-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="7b563-106">제한 사항</span><span class="sxs-lookup"><span data-stu-id="7b563-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="7b563-107">필수 구성 요소</span><span class="sxs-lookup"><span data-stu-id="7b563-107">Prerequisites</span></span>](#Prerequisites)  
  
     [<span data-ttu-id="7b563-108">권장 사항</span><span class="sxs-lookup"><span data-stu-id="7b563-108">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="7b563-109">보안</span><span class="sxs-lookup"><span data-stu-id="7b563-109">Security</span></span>](#Security)  
  
-   <span data-ttu-id="7b563-110">**데이터베이스를 삭제하려면:**</span><span class="sxs-lookup"><span data-stu-id="7b563-110">**To delete a database, using:**</span></span>  
  
     [<span data-ttu-id="7b563-111">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="7b563-111">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="7b563-112">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="7b563-112">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   <span data-ttu-id="7b563-113">**후속 작업:**  [데이터베이스를 삭제한 후](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="7b563-113">**Follow Up:**  [After deleting a database](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="7b563-114">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="7b563-114">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="7b563-115">제한 사항</span><span class="sxs-lookup"><span data-stu-id="7b563-115">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="7b563-116">시스템 데이터베이스는 삭제할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7b563-116">System databases cannot be deleted.</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="7b563-117">필수 조건</span><span class="sxs-lookup"><span data-stu-id="7b563-117">Prerequisites</span></span>  
  
-   <span data-ttu-id="7b563-118">데이터베이스에 있는 모든 데이터베이스 스냅샷을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="7b563-118">Delete any database snapshots that exist on the database.</span></span> <span data-ttu-id="7b563-119">자세한 내용은 [Drop a Database Snapshot &#40;Transact-SQL&#41;](drop-a-database-snapshot-transact-sql.md).</span><span class="sxs-lookup"><span data-stu-id="7b563-119">For more information, see [Drop a Database Snapshot &#40;Transact-SQL&#41;](drop-a-database-snapshot-transact-sql.md).</span></span>  
  
-   <span data-ttu-id="7b563-120">데이터베이스가 로그 전달과 관련되어 있으면 로그 전달을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="7b563-120">If the database is involved in log shipping, remove log shipping.</span></span>  
  
-   <span data-ttu-id="7b563-121">데이터베이스가 트랜잭션 복제용으로 게시되거나 복제를 병합하기 위해 게시 또는 구독되는 경우 데이터베이스에서 복제를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="7b563-121">If the database is published for transactional replication, or published or subscribed to merge replication, remove replication from the database.</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="7b563-122">권장 사항</span><span class="sxs-lookup"><span data-stu-id="7b563-122">Recommendations</span></span>  
  
-   <span data-ttu-id="7b563-123">데이터베이스 전체 백업을 고려합니다.</span><span class="sxs-lookup"><span data-stu-id="7b563-123">Consider taking a full backup of the database.</span></span> <span data-ttu-id="7b563-124">삭제된 데이터베이스는 백업 복원을 통해서만 다시 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7b563-124">A deleted database can be re-created only by restoring a backup.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="7b563-125">보안</span><span class="sxs-lookup"><span data-stu-id="7b563-125">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="7b563-126">권한</span><span class="sxs-lookup"><span data-stu-id="7b563-126">Permissions</span></span>  
 <span data-ttu-id="7b563-127">DROP DATABASE를 실행하려면 최소한 데이터베이스에 대한 CONTROL 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="7b563-127">To execute DROP DATABASE, at a minimum, a user must have CONTROL permission on the database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="7b563-128">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="7b563-128">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-delete-a-database"></a><span data-ttu-id="7b563-129">데이터베이스를 삭제하려면</span><span class="sxs-lookup"><span data-stu-id="7b563-129">To delete a database</span></span>  
  
1.  <span data-ttu-id="7b563-130">**개체 탐색기**에서 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]의 인스턴스에 연결한 다음 해당 인스턴스를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="7b563-130">In **Object Explorer**, connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="7b563-131">**데이터베이스**를 확장하고 삭제할 데이터베이스를 마우스 오른쪽 단추로 클릭한 다음 **삭제**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7b563-131">Expand **Databases**, right-click the database to delete, and then click **Delete**.</span></span>  
  
3.  <span data-ttu-id="7b563-132">올바른 데이터베이스가 선택되었는지 확인하고 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7b563-132">Confirm the correct database is selected, and then click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="7b563-133">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="7b563-133">Using Transact-SQL</span></span>  
  
#### <a name="to-delete-a-database"></a><span data-ttu-id="7b563-134">데이터베이스를 삭제하려면</span><span class="sxs-lookup"><span data-stu-id="7b563-134">To delete a database</span></span>  
  
1.  <span data-ttu-id="7b563-135">[!INCLUDE[ssDE](../../includes/ssde-md.md)]에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="7b563-135">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="7b563-136">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7b563-136">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="7b563-137">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7b563-137">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="7b563-138">다음 예에서는 `Sales` 및 `NewSales` 데이터베이스를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="7b563-138">The example removes the `Sales` and `NewSales` databases.</span></span>  
  
```sql  
USE master ;  
GO  
DROP DATABASE Sales, NewSales ;  
GO  
```  
  
##  <a name="follow-up-after-deleting-a-database"></a><a name="FollowUp"></a> <span data-ttu-id="7b563-139">후속 작업: 데이터베이스를 삭제한 후</span><span class="sxs-lookup"><span data-stu-id="7b563-139">Follow Up: After deleting a database</span></span>  
 <span data-ttu-id="7b563-140">**master** 데이터베이스를 백업합니다.</span><span class="sxs-lookup"><span data-stu-id="7b563-140">Back up the **master** database.</span></span> <span data-ttu-id="7b563-141">**master** 를 복원해야 할 경우 마지막 **master** 백업 이후 삭제된 모든 데이터베이스의 참조가 시스템 카탈로그 뷰에 아직 있어서 오류 메시지가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7b563-141">If **master** must be restored, any database that has been deleted since the last backup of **master** will still have references in the system catalog views and may cause error messages to be raised.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b563-142">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7b563-142">See Also</span></span>  
 <span data-ttu-id="7b563-143">[CREATE DATABASE&#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="7b563-143">[CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql) </span></span>  
 [<span data-ttu-id="7b563-144">ALTER DATABASE&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="7b563-144">ALTER DATABASE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-database-transact-sql)  
  
  
