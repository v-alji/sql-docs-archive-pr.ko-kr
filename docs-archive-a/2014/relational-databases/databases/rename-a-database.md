---
title: 데이터베이스 이름 바꾸기 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- databases [SQL Server], renaming
- renaming databases
ms.assetid: 44c69d35-abcb-4da3-9370-5e0bc9a28496
author: stevestein
ms.author: sstein
ms.openlocfilehash: dd25a78e3d3b9be2e7191ce6ed3d6bdcbb0f9606
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650092"
---
# <a name="rename-a-database"></a><span data-ttu-id="d1b00-102">데이터베이스 이름 바꾸기</span><span class="sxs-lookup"><span data-stu-id="d1b00-102">Rename a Database</span></span>
  <span data-ttu-id="d1b00-103">이 항목에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 또는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 을 사용하여 [!INCLUDE[tsql](../../includes/tsql-md.md)]에서 사용자 정의 데이터베이스의 이름을 바꾸는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="d1b00-103">This topic describes how to rename a user-defined database in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="d1b00-104">데이터베이스 이름에는 식별자 규칙에서 허용하는 모든 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d1b00-104">The name of the database can include any characters that follow the rules for identifiers.</span></span>  
  
 <span data-ttu-id="d1b00-105">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="d1b00-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="d1b00-106">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="d1b00-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="d1b00-107">제한 사항</span><span class="sxs-lookup"><span data-stu-id="d1b00-107">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="d1b00-108">보안</span><span class="sxs-lookup"><span data-stu-id="d1b00-108">Security</span></span>](#Security)  
  
-   <span data-ttu-id="d1b00-109">**데이터베이스의 이름을 바꾸려면:**</span><span class="sxs-lookup"><span data-stu-id="d1b00-109">**To rename a database, using:**</span></span>  
  
     [<span data-ttu-id="d1b00-110">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="d1b00-110">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="d1b00-111">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="d1b00-111">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   <span data-ttu-id="d1b00-112">**후속 작업:**  [데이터베이스의 이름을 바꾼 후](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="d1b00-112">**Follow Up:**  [After renaming a database](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="d1b00-113">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="d1b00-113">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="d1b00-114">제한 사항</span><span class="sxs-lookup"><span data-stu-id="d1b00-114">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="d1b00-115">시스템 데이터베이스 이름은 바꿀 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d1b00-115">System databases cannot be renamed.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="d1b00-116">보안</span><span class="sxs-lookup"><span data-stu-id="d1b00-116">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="d1b00-117">권한</span><span class="sxs-lookup"><span data-stu-id="d1b00-117">Permissions</span></span>  
 <span data-ttu-id="d1b00-118">데이터베이스에 대한 ALTER 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="d1b00-118">Requires ALTER permission on the database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="d1b00-119">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="d1b00-119">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-rename-a-database"></a><span data-ttu-id="d1b00-120">데이터베이스 이름을 바꾸려면</span><span class="sxs-lookup"><span data-stu-id="d1b00-120">To rename a database</span></span>  
  
1.  <span data-ttu-id="d1b00-121">**개체 탐색기**에서 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]의 인스턴스에 연결한 다음 해당 인스턴스를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="d1b00-121">In **Object Explorer**, connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="d1b00-122">데이터베이스를 사용하고 있지 않는지 확인하고 [데이터베이스를 단일 사용자 모드로 설정](set-a-database-to-single-user-mode.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="d1b00-122">Make sure that no one is using the database, and then [set the database to single-user mode](set-a-database-to-single-user-mode.md).</span></span>  
  
3.  <span data-ttu-id="d1b00-123">**데이터베이스**를 확장하고 이름을 바꿀 데이터베이스를 마우스 오른쪽 단추로 클릭한 다음 **이름 바꾸기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d1b00-123">Expand **Databases**, right-click the database to rename, and then click **Rename**.</span></span>  
  
4.  <span data-ttu-id="d1b00-124">새 데이터베이스 이름을 입력하고 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d1b00-124">Enter the new database name, and then click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="d1b00-125">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="d1b00-125">Using Transact-SQL</span></span>  
  
#### <a name="to-rename-a-database"></a><span data-ttu-id="d1b00-126">데이터베이스 이름을 바꾸려면</span><span class="sxs-lookup"><span data-stu-id="d1b00-126">To rename a database</span></span>  
  
1.  <span data-ttu-id="d1b00-127">[!INCLUDE[ssDE](../../includes/ssde-md.md)]에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="d1b00-127">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="d1b00-128">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d1b00-128">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="d1b00-129">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d1b00-129">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="d1b00-130">다음 예에서는 `AdventureWorks2012` 데이터베이스의 이름을 `Northwind`로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="d1b00-130">This example changes the name of the `AdventureWorks2012` database to `Northwind`.</span></span>  
  
```sql  
USE master;  
GO  
ALTER DATABASE AdventureWorks2012  
Modify Name = Northwind ;  
GO  
```  
  
###  <a name="TsqlExample"></a>   
##  <a name="follow-up-after-renaming-a-database"></a><a name="FollowUp"></a><span data-ttu-id="d1b00-131">후속 작업: 데이터베이스 이름을 바꾼 후</span><span class="sxs-lookup"><span data-stu-id="d1b00-131">Follow Up: After renaming a database</span></span>  
 <span data-ttu-id="d1b00-132">데이터베이스 이름을 바꾼 후 **master** 데이터베이스를 백업합니다.</span><span class="sxs-lookup"><span data-stu-id="d1b00-132">Back up the **master** database after you rename any database.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1b00-133">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d1b00-133">See Also</span></span>  
 <span data-ttu-id="d1b00-134">[ALTER DATABASE &#40;Transact-SQL &#41;](/sql/t-sql/statements/alter-database-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="d1b00-134">[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) </span></span>  
 [<span data-ttu-id="d1b00-135">데이터베이스 식별자</span><span class="sxs-lookup"><span data-stu-id="d1b00-135">Database Identifiers</span></span>](database-identifiers.md)  
  
  
