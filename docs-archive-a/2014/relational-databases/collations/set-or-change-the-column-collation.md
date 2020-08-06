---
title: 열 데이터 정렬 설정 또는 변경 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- tempdb database [SQL Server], collations
- collations [SQL Server], column
ms.assetid: d7a9638b-717c-4680-9b98-8849081e08be
author: stevestein
ms.author: sstein
ms.openlocfilehash: 05b8211569b6ce83faaec043e5eb527a60f0ddab
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661165"
---
# <a name="set-or-change-the-column-collation"></a><span data-ttu-id="4a5e1-102">열 데이터 정렬 설정 또는 변경</span><span class="sxs-lookup"><span data-stu-id="4a5e1-102">Set or Change the Column Collation</span></span>
  <span data-ttu-id="4a5e1-103">특정 테이블의 열에 대해 다른 데이터 정렬을 지정하고 다음 중 하나를 사용하여 `char`, `varchar`, `text`, `nchar`, `nvarchar` 및 `ntext` 데이터의 데이터베이스 데이터 정렬을 재정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4a5e1-103">You can override the database collation for `char`, `varchar`, `text`, `nchar`, `nvarchar`, and `ntext` data by specifying a different collation for a specific column of a table and using one of the following:</span></span>  
  
-   <span data-ttu-id="4a5e1-104">[CREATE TABLE](/sql/t-sql/statements/create-table-transact-sql) 및 [ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql)의 COLLATE 절</span><span class="sxs-lookup"><span data-stu-id="4a5e1-104">The COLLATE clause of [CREATE TABLE](/sql/t-sql/statements/create-table-transact-sql) and [ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql).</span></span> <span data-ttu-id="4a5e1-105">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="4a5e1-105">For example:</span></span>  
  
    ```  
    CREATE TABLE dbo.MyTable  
      (PrimaryKey   int PRIMARY KEY,  
       CharCol      varchar(10) COLLATE French_CI_AS NOT NULL  
      );  
    GO  
    ALTER TABLE dbo.MyTable ALTER COLUMN CharCol  
                varchar(10)COLLATE Latin1_General_CI_AS NOT NULL;  
    GO  
    ```  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]<span data-ttu-id="4a5e1-106">.</span><span class="sxs-lookup"><span data-stu-id="4a5e1-106">.</span></span> <span data-ttu-id="4a5e1-107">자세한 내용은 [Collation and Unicode Support](collation-and-unicode-support.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="4a5e1-107">For more information, [Collation and Unicode Support](collation-and-unicode-support.md).</span></span>  
  
-   <span data-ttu-id="4a5e1-108">`Column.Collation` [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SMO (Management Objects)에서 속성 사용.</span><span class="sxs-lookup"><span data-stu-id="4a5e1-108">Using the `Column.Collation` property in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Objects (SMO).</span></span>  
  
 <span data-ttu-id="4a5e1-109">다음 중 하나가 현재 참조하고 있는 열의 데이터 정렬은 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4a5e1-109">You cannot change the collation of a column that is currently referenced by any one of the following:</span></span>  
  
-   <span data-ttu-id="4a5e1-110">계산 열</span><span class="sxs-lookup"><span data-stu-id="4a5e1-110">A computed column</span></span>  
  
-   <span data-ttu-id="4a5e1-111">인덱스</span><span class="sxs-lookup"><span data-stu-id="4a5e1-111">An index</span></span>  
  
-   <span data-ttu-id="4a5e1-112">자동으로 또는 CREATE STATISTICS 문에 의해 생성된 배포 통계</span><span class="sxs-lookup"><span data-stu-id="4a5e1-112">Distribution statistics, either generated automatically or by the CREATE STATISTICS statement</span></span>  
  
-   <span data-ttu-id="4a5e1-113">CHECK 제약 조건</span><span class="sxs-lookup"><span data-stu-id="4a5e1-113">A CHECK constraint</span></span>  
  
-   <span data-ttu-id="4a5e1-114">FOREIGN KEY 제약 조건</span><span class="sxs-lookup"><span data-stu-id="4a5e1-114">A FOREIGN KEY constraint</span></span>  
  
 <span data-ttu-id="4a5e1-115">**tempdb**를 사용할 때 [COLLATE](/sql/t-sql/statements/collations) 절은 *database_default* 옵션을 포함하여 임시 테이블에 있는 열이 **tempdb**의 데이터 정렬 대신 현재 사용자 데이터베이스의 데이터 정렬 기본값을 연결에 사용하도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="4a5e1-115">When you work with **tempdb**, the [COLLATE](/sql/t-sql/statements/collations) clause includes a *database_default* option to specify that a column in a temporary table uses the collation default of the current user database for the connection instead of the collation of **tempdb**.</span></span>  
  
## <a name="collations-and-text-columns"></a><span data-ttu-id="4a5e1-116">데이터 정렬 및 텍스트 열</span><span class="sxs-lookup"><span data-stu-id="4a5e1-116">Collations and text Columns</span></span>  
 <span data-ttu-id="4a5e1-117">`text` 열에는 데이터 정렬이 데이터베이스 기본 데이터 정렬의 코드 페이지와 다른 값을 삽입하거나 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4a5e1-117">You can insert or update values in a `text` column whose collation is different from the code page of the default collation of the database.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="4a5e1-118">에서는 값을 열의 데이터 정렬로 암시적으로 변환합니다.</span><span class="sxs-lookup"><span data-stu-id="4a5e1-118">implicitly converts the values to the collation of the column.</span></span>  
  
## <a name="collations-and-tempdb"></a><span data-ttu-id="4a5e1-119">데이터 정렬 및 tempdb</span><span class="sxs-lookup"><span data-stu-id="4a5e1-119">Collations and tempdb</span></span>  
 <span data-ttu-id="4a5e1-120">**tempdb** 데이터베이스는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 가 시작될 때마다 작성되며 **model** 데이터베이스와 같은 기본 데이터 정렬을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="4a5e1-120">The **tempdb** database is built every time [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is started and has the same default collation as the **model** database.</span></span> <span data-ttu-id="4a5e1-121">이는 일반적으로 인스턴스의 기본 데이터 정렬과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="4a5e1-121">This is typically the same as the default collation of the instance.</span></span> <span data-ttu-id="4a5e1-122">사용자 데이터베이스를 만들고 **model**과 다른 기본 데이터 정렬을 지정하면 사용자 데이터베이스는 **tempdb**와 다른 기본 데이터 정렬을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="4a5e1-122">If you create a user database and specify a different default collation than **model**, the user database has a different default collation than **tempdb**.</span></span> <span data-ttu-id="4a5e1-123">모든 임시 저장 프로시저나 임시 테이블은 **tempdb**에서 생성되고 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="4a5e1-123">All temporary stored procedures or temporary tables are created and stored in **tempdb**.</span></span> <span data-ttu-id="4a5e1-124">즉, 임시 테이블의 모든 암시적 열과 임시 저장 프로시저의 모든 강제 기본 상수, 변수 및 매개 변수는 영구 테이블 및 저장 프로시저에서 만들어진 유사 개체와는 다른 데이터 정렬을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="4a5e1-124">This means that all implicit columns in temporary tables and all coercible-default constants, variables, and parameters in temporary stored procedures have collations that are different from comparable objects created in permanent tables and stored procedures.</span></span>  
  
 <span data-ttu-id="4a5e1-125">이로 인해 사용자 정의 데이터베이스와 시스템 데이터베이스 개체 간에 데이터 정렬 불일치 문제가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4a5e1-125">This could lead to problems with a mismatch in collations between user-defined databases and system database objects.</span></span> <span data-ttu-id="4a5e1-126">예를 들어 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에서는 Latin1_General_CS_AS 데이터 정렬을 사용하는데 다음 문을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="4a5e1-126">For example, an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] uses the Latin1_General_CS_AS collation and you execute the following statements:</span></span>  
  
```  
CREATE DATABASE TestDB COLLATE Estonian_CS_AS;  
USE TestDB;  
CREATE TABLE TestPermTab (PrimaryKey int PRIMARY KEY, Col1 nchar );  
```  
  
 <span data-ttu-id="4a5e1-127">이 시스템에서 **tempdb** 데이터베이스는 코드 페이지 1252를 포함하는 Latin1_General_CS_AS 데이터 정렬을 사용하고 `TestDB` 및 `TestPermTab.Col1` 은 코드 페이지 1257을 포함하는 `Estonian_CS_AS` 데이터 정렬을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="4a5e1-127">In this system, the **tempdb** database uses the Latin1_General_CS_AS collation with code page 1252, and `TestDB` and `TestPermTab.Col1` use the `Estonian_CS_AS` collation with code page 1257.</span></span> <span data-ttu-id="4a5e1-128">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="4a5e1-128">For example:</span></span>  
  
```  
USE TestDB;  
GO  
-- Create a temporary table with the same column declarations  
-- as TestPermTab  
CREATE TABLE #TestTempTab (PrimaryKey int PRIMARY KEY, Col1 nchar );  
INSERT INTO #TestTempTab  
         SELECT * FROM TestPermTab;  
GO  
```  
  
 <span data-ttu-id="4a5e1-129">이전 예에서 **tempdb** 데이터베이스는 Latin1_General_CS_AS 데이터 정렬을 사용하고 `TestDB` 및 `TestTab.Col1` 은 `Estonian_CS_AS` 데이터 정렬을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="4a5e1-129">With the previous example, the **tempdb** database uses the Latin1_General_CS_AS collation, and `TestDB` and `TestTab.Col1` use the `Estonian_CS_AS` collation.</span></span> <span data-ttu-id="4a5e1-130">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="4a5e1-130">For example:</span></span>  
  
```  
SELECT * FROM TestPermTab AS a INNER JOIN #TestTempTab on a.Col1 = #TestTempTab.Col1;  
```  
  
 <span data-ttu-id="4a5e1-131">**tempdb** 는 기본 서버 데이터 정렬을 사용하고 `TestPermTab.Col1` 은 다른 데이터 정렬을 사용하므로 SQL Server는 "같음 작업에서 'Latin1_General_CI_AS_KS_WS'과(와) 'Estonian_CS_AS' 간의 데이터 정렬 충돌을 해결할 수 없습니다"라는 오류를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="4a5e1-131">Because **tempdb** uses the default server collation and `TestPermTab.Col1` uses a different collation, SQL Server returns this error: "Cannot resolve collation conflict between 'Latin1_General_CI_AS_KS_WS' and 'Estonian_CS_AS' in equal to operation."</span></span>  
  
 <span data-ttu-id="4a5e1-132">이 오류를 방지하는 데 사용할 수 있는 방법은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="4a5e1-132">To prevent the error, you can use one of the following alternatives:</span></span>  
  
-   <span data-ttu-id="4a5e1-133">임시 테이블 열이 **tempdb**가 아닌 사용자 데이터베이스의 기본 데이터 정렬을 사용하도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="4a5e1-133">Specify that the temporary table column use the default collation of the user database, not **tempdb**.</span></span> <span data-ttu-id="4a5e1-134">이렇게 하면 시스템에서 요구할 경우 임시 테이블은 여러 데이터베이스에 있는 유사한 형식의 테이블로 작업할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4a5e1-134">This enables the temporary table to work with similarly formatted tables in multiple databases, if that is required of your system.</span></span>  
  
    ```  
    CREATE TABLE #TestTempTab  
       (PrimaryKey int PRIMARY KEY,  
        Col1 nchar COLLATE database_default  
       );  
    ```  
  
-   <span data-ttu-id="4a5e1-135">`#TestTempTab` 열에 대해 올바른 데이터 정렬을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="4a5e1-135">Specify the correct collation for the `#TestTempTab` column:</span></span>  
  
    ```  
    CREATE TABLE #TestTempTab  
       (PrimaryKey int PRIMARY KEY,  
        Col1 nchar COLLATE Estonian_CS_AS  
       );  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="4a5e1-136">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4a5e1-136">See Also</span></span>  
 <span data-ttu-id="4a5e1-137">[서버 데이터 정렬 설정 또는 변경](set-or-change-the-server-collation.md) </span><span class="sxs-lookup"><span data-stu-id="4a5e1-137">[Set or Change the Server Collation](set-or-change-the-server-collation.md) </span></span>  
 <span data-ttu-id="4a5e1-138">[데이터베이스 데이터 정렬 설정 또는 변경](set-or-change-the-database-collation.md) </span><span class="sxs-lookup"><span data-stu-id="4a5e1-138">[Set or Change the Database Collation](set-or-change-the-database-collation.md) </span></span>  
 [<span data-ttu-id="4a5e1-139">데이터 정렬 및 유니코드 지원</span><span class="sxs-lookup"><span data-stu-id="4a5e1-139">Collation and Unicode Support</span></span>](collation-and-unicode-support.md)  
  
  
