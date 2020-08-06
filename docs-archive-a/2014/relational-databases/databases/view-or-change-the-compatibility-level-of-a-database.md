---
title: 데이터베이스의 호환성 수준 보기 또는 변경 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- compatibility levels [SQL Server], viewing
- compatibility [SQL Server], databases
- compatibility levels [SQL Server], changing
ms.assetid: 579867ec-57cb-4cb8-af35-9688c1e9e15d
author: stevestein
ms.author: sstein
ms.openlocfilehash: 35cf7af50eba333440c42a1bac428df1fff156b4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741080"
---
# <a name="view-or-change-the-compatibility-level-of-a-database"></a><span data-ttu-id="cf151-102">데이터베이스의 호환성 수준 보기 또는 변경</span><span class="sxs-lookup"><span data-stu-id="cf151-102">View or Change the Compatibility Level of a Database</span></span>
  <span data-ttu-id="cf151-103">이 항목에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 또는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 을 사용하여 [!INCLUDE[tsql](../../includes/tsql-md.md)]데이터베이스의 호환성 수준을 보거나 변경하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="cf151-103">This topic describes how to view or change the compatibility level of a database in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="cf151-104">데이터베이스의 호환성 수준을 변경하기 전에 변경 사항이 애플리케이션에 미치는 영향에 대해 이해하고 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cf151-104">Before you change the compatibility level of a database, you should understand the impact of the change on your applications.</span></span> <span data-ttu-id="cf151-105">자세한 내용은 [ALTER DATABASE 호환성 수준&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-compatibility-level)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="cf151-105">For more information, see [ALTER DATABASE Compatibility Level &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-compatibility-level).</span></span>  
  
 <span data-ttu-id="cf151-106">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="cf151-106">**In This Topic**</span></span>  
  
-   <span data-ttu-id="cf151-107">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="cf151-107">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="cf151-108">보안</span><span class="sxs-lookup"><span data-stu-id="cf151-108">Security</span></span>](#Security)  
  
-   <span data-ttu-id="cf151-109">**데이터베이스의 호환성 수준을 보거나 변경하려면:**</span><span class="sxs-lookup"><span data-stu-id="cf151-109">**To view or change the compatibility level of a database, using:**</span></span>  
  
     [<span data-ttu-id="cf151-110">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="cf151-110">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="cf151-111">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="cf151-111">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="cf151-112">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="cf151-112">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="cf151-113">보안</span><span class="sxs-lookup"><span data-stu-id="cf151-113">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="cf151-114">권한</span><span class="sxs-lookup"><span data-stu-id="cf151-114">Permissions</span></span>  
 <span data-ttu-id="cf151-115">데이터베이스에 대한 ALTER 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="cf151-115">Requires ALTER permission on the database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="cf151-116">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="cf151-116">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-view-or-change-the-compatibility-level-of-a-database"></a><span data-ttu-id="cf151-117">데이터베이스의 호환성 수준을 보거나 변경하려면</span><span class="sxs-lookup"><span data-stu-id="cf151-117">To view or change the compatibility level of a database</span></span>  
  
1.  <span data-ttu-id="cf151-118">[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]의 해당 인스턴스에 연결한 다음 개체 탐색기에서 서버 이름을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cf151-118">After connecting to the appropriate instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], in Object Explorer, click the server name.</span></span>  
  
2.  <span data-ttu-id="cf151-119">**데이터베이스**를 확장하고 해당 데이터베이스에 따라 사용자 데이터베이스를 선택하거나 **시스템 데이터베이스** 를 확장한 다음 시스템 데이터베이스를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="cf151-119">Expand **Databases**, and, depending on the database, either select a user database or expand **System Databases** and select a system database.</span></span>  
  
3.  <span data-ttu-id="cf151-120">데이터베이스를 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cf151-120">Right-click the database, and then click **Properties**.</span></span>  
  
     <span data-ttu-id="cf151-121">**데이터베이스 속성** 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="cf151-121">The **Database Properties** dialog box opens.</span></span>  
  
4.  <span data-ttu-id="cf151-122">**페이지 선택** 창에서 **옵션**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cf151-122">In the **Select a page** pane, click **Options**.</span></span>  
  
     <span data-ttu-id="cf151-123">현재 호환성 수준이 **호환성 수준** 목록 상자에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="cf151-123">The current compatibility level is displayed in the **Compatibility level** list box.</span></span>  
  
5.  <span data-ttu-id="cf151-124">호환성 수준을 변경하려면 목록에서 다른 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="cf151-124">To change the compatibility level, select a different option from the list.</span></span> <span data-ttu-id="cf151-125">**SQL Server 2008(100)**, **SQL Server 2012(110)** 또는 **SQL Server 2014(120)** 중에서 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cf151-125">The choices are **SQL Server 2008 (100)**, **SQL Server 2012 (110)**, or **SQL Server 2014 (120)**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="cf151-126">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="cf151-126">Using Transact-SQL</span></span>  
  
#### <a name="to-view-the-compatibility-level-of-a-database"></a><span data-ttu-id="cf151-127">데이터베이스의 호환성 수준을 보려면</span><span class="sxs-lookup"><span data-stu-id="cf151-127">To view the compatibility level of a database</span></span>  
  
1.  <span data-ttu-id="cf151-128">[!INCLUDE[ssDE](../../includes/ssde-md.md)]에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="cf151-128">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="cf151-129">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cf151-129">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="cf151-130">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cf151-130">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="cf151-131">다음 예에서는 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 데이터베이스의 호환성 수준을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="cf151-131">This example returns the compatibility level of the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database.</span></span>  
  
```sql  
USE AdventureWorks2012;  
GO  
SELECT compatibility_level  
FROM sys.databases WHERE name = 'AdventureWorks2012';  
GO  
  
```  
  
#### <a name="to-change-the-compatibility-level-of-a-database"></a><span data-ttu-id="cf151-132">데이터베이스의 호환성 수준을 변경하려면</span><span class="sxs-lookup"><span data-stu-id="cf151-132">To change the compatibility level of a database</span></span>  
  
1.  <span data-ttu-id="cf151-133">[!INCLUDE[ssDE](../../includes/ssde-md.md)]에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="cf151-133">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="cf151-134">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cf151-134">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="cf151-135">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cf151-135">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="cf151-136">이 예에서는의 호환성 수준을 변경 합니다 [!INCLUDE[ssSampleDBobject](../../includes/sssql14-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="cf151-136">This example changes the compatibility level of the [!INCLUDE[ssSampleDBobject](../../includes/sssql14-md.md)].</span></span>  
  
```sql  
ALTER DATABASE AdventureWorks2012  
SET COMPATIBILITY_LEVEL = 120;  
GO  
```  
  
  
