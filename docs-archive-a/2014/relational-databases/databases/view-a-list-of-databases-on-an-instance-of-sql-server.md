---
title: SQL Server 인스턴스에서 데이터베이스의 목록 보기 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- current databases
- databases currently on server [SQL Server]
- database list [SQL Server]
- viewing database list
- displaying database list
- databases [SQL Server], viewing
- servers [SQL Server], databases listed on
- listing databases
ms.assetid: 7ee7a789-db36-4be9-8a0e-0362a1e152dd
author: stevestein
ms.author: sstein
ms.openlocfilehash: 47283fa9065a0b9d6238dab804094d9a65d17897
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741072"
---
# <a name="view-a-list-of-databases-on-an-instance-of-sql-server"></a><span data-ttu-id="0971c-102">SQL Server 인스턴스에서 데이터베이스의 목록 보기</span><span class="sxs-lookup"><span data-stu-id="0971c-102">View a List of Databases on an Instance of SQL Server</span></span>
  <span data-ttu-id="0971c-103">이 항목에서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 또는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 을 사용하여 [!INCLUDE[tsql](../../includes/tsql-md.md)]인스턴스에서 데이터베이스 목록을 보는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="0971c-103">This topic describes how to view a list of databases on an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="0971c-104">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="0971c-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="0971c-105">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="0971c-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="0971c-106">보안</span><span class="sxs-lookup"><span data-stu-id="0971c-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="0971c-107">**SQL Server 인스턴스에서 데이터베이스의 목록을 보려면:**</span><span class="sxs-lookup"><span data-stu-id="0971c-107">**To view a list of databases on an instance of SQL Server, using:**</span></span>  
  
     [<span data-ttu-id="0971c-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="0971c-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="0971c-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="0971c-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="0971c-110">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="0971c-110">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="0971c-111">보안</span><span class="sxs-lookup"><span data-stu-id="0971c-111">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="0971c-112">권한</span><span class="sxs-lookup"><span data-stu-id="0971c-112">Permissions</span></span>  
 <span data-ttu-id="0971c-113">**sys.databases** 의 호출자가 데이터베이스의 소유자가 아니고 데이터베이스가 **master** 또는 **tempdb**가 아닐 경우 해당 행을 보려면 최소한 서버 수준의 ALTER ANY DATABASE 또는 VIEW ANY DATABASE 권한이 있거나 **master** 데이터베이스에서 CREATE DATABASE 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0971c-113">If the caller of **sys.databases** is not the owner of the database and the database is not **master** or **tempdb**, the minimum permissions required to see the corresponding row are ALTER ANY DATABASE or VIEW ANY DATABASE server-level permission, or CREATE DATABASE permission in the **master** database.</span></span> <span data-ttu-id="0971c-114">호출자가 연결된 데이터베이스는 항상 **sys.databases**에서 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0971c-114">The database to which the caller is connected can always be viewed in **sys.databases**.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="0971c-115">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="0971c-115">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-view-a-list-of-databases-on-an-instance-of-sql-server"></a><span data-ttu-id="0971c-116">SQL Server 인스턴스에서 데이터베이스의 목록을 보려면</span><span class="sxs-lookup"><span data-stu-id="0971c-116">To view a list of databases on an instance of SQL Server</span></span>  
  
1.  <span data-ttu-id="0971c-117">**개체 탐색기**에서 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]의 인스턴스에 연결한 다음 해당 인스턴스를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="0971c-117">In **Object Explorer**, connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="0971c-118">인스턴스에 있는 모든 데이터베이스 목록을 확인하려면 **데이터베이스**를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="0971c-118">To see a list of all databases on the instance, expand **Databases**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="0971c-119">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="0971c-119">Using Transact-SQL</span></span>  
  
#### <a name="to-view-a-list-of-databases-on-an-instance-of-sql-server"></a><span data-ttu-id="0971c-120">SQL Server 인스턴스에서 데이터베이스의 목록을 보려면</span><span class="sxs-lookup"><span data-stu-id="0971c-120">To view a list of databases on an instance of SQL Server</span></span>  
  
1.  <span data-ttu-id="0971c-121">[!INCLUDE[ssDE](../../includes/ssde-md.md)]에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="0971c-121">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="0971c-122">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0971c-122">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="0971c-123">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0971c-123">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="0971c-124">이 예에서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스의 데이터베이스 목록을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="0971c-124">This example returns a list of databases on the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="0971c-125">목록에는 데이터베이스 이름, 데이터베이스 ID 및 데이터베이스를 만든 날짜가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="0971c-125">The list includes the names of the databases, their database IDs, and the dates when the databases were created.</span></span>  
  
```sql  
USE AdventureWorks2012;  
GO  
SELECT name, database_id, create_date  
FROM sys.databases ;  
GO  
  
```  
  
## <a name="see-also"></a><span data-ttu-id="0971c-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0971c-126">See Also</span></span>  
 <span data-ttu-id="0971c-127">[데이터베이스 및 파일 카탈로그 뷰&#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/databases-and-files-catalog-views-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="0971c-127">[Databases and Files Catalog Views &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/databases-and-files-catalog-views-transact-sql) </span></span>  
 [<span data-ttu-id="0971c-128">sys.databases&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="0971c-128">sys.databases &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql)  
  
  
