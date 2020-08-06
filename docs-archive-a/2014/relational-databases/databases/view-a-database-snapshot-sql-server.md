---
title: 데이터베이스 스냅샷 보기(SQL Server) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- database snapshots [SQL Server], viewing
- displaying database snapshots
- viewing database snapshots
ms.assetid: 123f19b2-0850-4033-8507-59ebdfb368ee
author: stevestein
ms.author: sstein
ms.openlocfilehash: 92c5c557656e87be562e9d5477f14f66b2c39e7b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741075"
---
# <a name="view-a-database-snapshot-sql-server"></a><span data-ttu-id="07ad8-102">데이터베이스 스냅샷 보기(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="07ad8-102">View a Database Snapshot (SQL Server)</span></span>
  <span data-ttu-id="07ad8-103">이 항목에서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 를 사용하여 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]데이터베이스 스냅샷을 표시하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="07ad8-103">This topic explains how to view a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database snapshot using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="07ad8-104">데이터베이스 스냅샷을 만들거나, 되돌리거나, 삭제하려면 [!INCLUDE[tsql](../../includes/tsql-md.md)]을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="07ad8-104">To create, revert to, or delete a database snapshot, you must use [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="07ad8-105">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="07ad8-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="07ad8-106">**데이터베이스 스냅샷을 보려면:**</span><span class="sxs-lookup"><span data-stu-id="07ad8-106">**To view a database snapshot, using:**</span></span>  
  
     [<span data-ttu-id="07ad8-107">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="07ad8-107">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="07ad8-108">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="07ad8-108">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="07ad8-109">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="07ad8-109">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="07ad8-110">**데이터베이스 스냅샷을 보려면**</span><span class="sxs-lookup"><span data-stu-id="07ad8-110">**To view a database snapshot**</span></span>  
  
1.  <span data-ttu-id="07ad8-111">개체 탐색기에서 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 인스턴스에 연결한 다음 해당 인스턴스를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="07ad8-111">In Object Explorer, connect to the instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="07ad8-112">**데이터베이스**를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="07ad8-112">Expand **Databases.**</span></span>  
  
3.  <span data-ttu-id="07ad8-113">**데이터베이스 스냅샷**을 확장한 후 표시할 스냅샷을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="07ad8-113">Expand **Database Snapshots**, and select the snapshot you want to view.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="07ad8-114">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="07ad8-114">Using Transact-SQL</span></span>  
 <span data-ttu-id="07ad8-115">**데이터베이스 스냅샷을 보려면**</span><span class="sxs-lookup"><span data-stu-id="07ad8-115">**To view a database snapshot**</span></span>  
  
1.  <span data-ttu-id="07ad8-116">[!INCLUDE[ssDE](../../includes/ssde-md.md)]에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="07ad8-116">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="07ad8-117">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="07ad8-117">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="07ad8-118">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스의 데이터베이스 스냅샷을 나열하려면 NULL이 아닌 값에 대해 **sys.databases** 카탈로그 뷰의 [source_database_id](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) 열을 쿼리합니다.</span><span class="sxs-lookup"><span data-stu-id="07ad8-118">To list the database snapshots of the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], query the **source_database_id** column of the [sys.databases](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) catalog view for non-NULL values.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="07ad8-119">관련 작업</span><span class="sxs-lookup"><span data-stu-id="07ad8-119">Related Tasks</span></span>  
  
-   [<span data-ttu-id="07ad8-120">데이터베이스 스냅샷 만들기&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="07ad8-120">Create a Database Snapshot &#40;Transact-SQL&#41;</span></span>](create-a-database-snapshot-transact-sql.md)  
  
-   [<span data-ttu-id="07ad8-121">데이터베이스를 데이터베이스 스냅샷으로 되돌리기</span><span class="sxs-lookup"><span data-stu-id="07ad8-121">Revert a Database to a Database Snapshot</span></span>](revert-a-database-to-a-database-snapshot.md)  
  
-   [<span data-ttu-id="07ad8-122">데이터베이스 스냅샷 삭제&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="07ad8-122">Drop a Database Snapshot &#40;Transact-SQL&#41;</span></span>](drop-a-database-snapshot-transact-sql.md)  
  
## <a name="see-also"></a><span data-ttu-id="07ad8-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="07ad8-123">See Also</span></span>  
 [<span data-ttu-id="07ad8-124">데이터베이스 스냅샷&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="07ad8-124">Database Snapshots &#40;SQL Server&#41;</span></span>](database-snapshots-sql-server.md)  
  
  
