---
title: 데이터베이스의 데이터 및 로그 공간 정보 표시 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- logs [SQL Server], space
- status information [SQL Server], space
- displaying space information
- disk space [SQL Server], displaying
- databases [SQL Server], space used
- viewing space information
- space allocation [SQL Server], displaying
- data space [SQL Server]
ms.assetid: c7b99463-4bab-4e9b-9217-fcb0898dc757
author: stevestein
ms.author: sstein
ms.openlocfilehash: 1beb8cdedbc2b72eadeeb350ee1c3b6d16218205
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742195"
---
# <a name="display-data-and-log-space-information-for-a-database"></a><span data-ttu-id="d8967-102">데이터베이스의 데이터 및 로그 공간 정보 표시</span><span class="sxs-lookup"><span data-stu-id="d8967-102">Display Data and Log Space Information for a Database</span></span>
  <span data-ttu-id="d8967-103">이 항목에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 또는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 을 사용하여 [!INCLUDE[tsql](../../includes/tsql-md.md)]의 데이터베이스에 대한 데이터와 로그 공간 정보를 표시하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="d8967-103">This topic describes how to display the data and log space information for a database in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="d8967-104">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="d8967-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="d8967-105">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="d8967-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="d8967-106">보안</span><span class="sxs-lookup"><span data-stu-id="d8967-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="d8967-107">**데이터베이스에 대한 데이터 및 로그 공간 정보를 표시하려면:**</span><span class="sxs-lookup"><span data-stu-id="d8967-107">**To display data and log space information for a database, using:**</span></span>  
  
     [<span data-ttu-id="d8967-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="d8967-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="d8967-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="d8967-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="d8967-110">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="d8967-110">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="d8967-111">보안</span><span class="sxs-lookup"><span data-stu-id="d8967-111">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="d8967-112">권한</span><span class="sxs-lookup"><span data-stu-id="d8967-112">Permissions</span></span>  
 <span data-ttu-id="d8967-113">**sp_spaceused** 를 실행할 수 있는 사용 권한은 **public** 역할에 부여됩니다.</span><span class="sxs-lookup"><span data-stu-id="d8967-113">Permission to execute **sp_spaceused** is granted to the **public** role.</span></span> <span data-ttu-id="d8967-114">**db_owner** 고정 데이터베이스 역할의 멤버만 **@updateusage** 매개 변수를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d8967-114">Only members of the **db_owner** fixed database role can specify the **@updateusage** parameter.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="d8967-115">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="d8967-115">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-display-data-and-log-space-information-for-a-database"></a><span data-ttu-id="d8967-116">데이터베이스의 데이터 및 로그 공간 정보를 표시하려면</span><span class="sxs-lookup"><span data-stu-id="d8967-116">To display data and log space information for a database</span></span>  
  
1.  <span data-ttu-id="d8967-117">개체 탐색기에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 의 인스턴스에 연결한 다음 해당 인스턴스를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="d8967-117">In Object Explorer, connect to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="d8967-118">**데이터베이스**를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="d8967-118">Expand **Databases**.</span></span>  
  
3.  <span data-ttu-id="d8967-119">데이터베이스를 마우스 오른쪽 단추로 클릭하고 **보고서**, **표준 보고서**를 차례로 가리킨 다음 **디스크 사용량**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d8967-119">Right-click a database, point to **Reports**, point to **Standard Reports,**, and then click **Disk Usage**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="d8967-120">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="d8967-120">Using Transact-SQL</span></span>  
  
#### <a name="to-display-data-and-log-space-information-for-a-database-by-using-sp_spaceused"></a><span data-ttu-id="d8967-121">sp_spaceused를 사용하여 데이터베이스에 대한 데이터 및 로그 공간 정보를 표시하려면</span><span class="sxs-lookup"><span data-stu-id="d8967-121">To display data and log space information for a database by using sp_spaceused</span></span>  
  
1.  <span data-ttu-id="d8967-122">[!INCLUDE[ssDE](../../includes/ssde-md.md)]에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="d8967-122">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="d8967-123">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d8967-123">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="d8967-124">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d8967-124">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="d8967-125">이 예에서는 [sp_spaceused](/sql/relational-databases/system-stored-procedures/sp-spaceused-transact-sql) 시스템 저장 프로시저를 사용하여 `Vendor` 테이블 및 해당 인덱스에 대한 디스크 공간 정보를 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="d8967-125">This example uses the [sp_spaceused](/sql/relational-databases/system-stored-procedures/sp-spaceused-transact-sql) system stored procedure to report disk space information for the `Vendor` table and its indexes.</span></span>  
  
```sql  
USE AdventureWorks2012;  
GO  
EXEC sp_spaceused N'Purchasing.Vendor';  
GO  
```  
  
#### <a name="to-display-data-and-log-space-information-for-a-database-by-querying-sysdatabase_files"></a><span data-ttu-id="d8967-126">sys.database_files를 쿼리하여 데이터베이스에 대한 데이터 및 로그 공간 정보를 표시하려면</span><span class="sxs-lookup"><span data-stu-id="d8967-126">To display data and log space information for a database by querying sys.database_files</span></span>  
  
1.  <span data-ttu-id="d8967-127">[!INCLUDE[ssDE](../../includes/ssde-md.md)]에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="d8967-127">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="d8967-128">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d8967-128">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="d8967-129">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d8967-129">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="d8967-130">이 예에서는 [sys.database_files](/sql/relational-databases/system-catalog-views/sys-database-files-transact-sql) 카탈로그 뷰를 쿼리하여 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 데이터베이스의 데이터 및 로그 파일에 대한 특정 정보를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="d8967-130">This example queries the [sys.database_files](/sql/relational-databases/system-catalog-views/sys-database-files-transact-sql) catalog view to return specific information about the data and log files in the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database.</span></span>  
  
```sql  
USE AdventureWorks2012;  
GO  
SELECT file_id, name, type_desc, physical_name, size, max_size  
FROM sys.database_files ;  
GO  
  
```  
  
## <a name="see-also"></a><span data-ttu-id="d8967-131">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d8967-131">See Also</span></span>  
 <span data-ttu-id="d8967-132">[SELECT&#40;Transact-SQL&#41;](/sql/t-sql/queries/select-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="d8967-132">[SELECT &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-transact-sql) </span></span>  
 <span data-ttu-id="d8967-133">[sys.database_files&#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-files-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="d8967-133">[sys.database_files &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-files-transact-sql) </span></span>  
 <span data-ttu-id="d8967-134">[sp_spaceused&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-spaceused-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="d8967-134">[sp_spaceused &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-spaceused-transact-sql) </span></span>  
 <span data-ttu-id="d8967-135">[데이터베이스에 데이터 또는 로그 파일 추가](add-data-or-log-files-to-a-database.md) </span><span class="sxs-lookup"><span data-stu-id="d8967-135">[Add Data or Log Files to a Database](add-data-or-log-files-to-a-database.md) </span></span>  
 [<span data-ttu-id="d8967-136">데이터베이스에서 데이터 또는 로그 파일 삭제</span><span class="sxs-lookup"><span data-stu-id="d8967-136">Delete Data or Log Files from a Database</span></span>](delete-data-or-log-files-from-a-database.md)  
  
  
