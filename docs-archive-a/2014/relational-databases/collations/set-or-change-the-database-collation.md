---
title: 데이터베이스 데이터 정렬 설정 또는 변경 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- collations [SQL Server], database
- database collations [SQL Server]
ms.assetid: 1379605c-1242-4ac8-ab1b-e2a2b5b1f895
author: stevestein
ms.author: sstein
ms.openlocfilehash: 6d7f7c3e3ddba7ba0ea9701993dbe0fad3a8d975
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661164"
---
# <a name="set-or-change-the-database-collation"></a><span data-ttu-id="87b46-102">데이터베이스 데이터 정렬 설정 또는 변경</span><span class="sxs-lookup"><span data-stu-id="87b46-102">Set or Change the Database Collation</span></span>
  <span data-ttu-id="87b46-103">이 항목에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 또는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 을 사용하여 [!INCLUDE[tsql](../../includes/tsql-md.md)]에서 데이터베이스 데이터 정렬을 설정하고 변경하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="87b46-103">This topic describes how set and change the database collation in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="87b46-104">데이터 정렬을 지정하지 않으면 서버 데이터 정렬이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="87b46-104">If no collation is specified, the server collation is used.</span></span>  
  
 <span data-ttu-id="87b46-105">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="87b46-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="87b46-106">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="87b46-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="87b46-107">제한 사항</span><span class="sxs-lookup"><span data-stu-id="87b46-107">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="87b46-108">권장 사항</span><span class="sxs-lookup"><span data-stu-id="87b46-108">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="87b46-109">보안</span><span class="sxs-lookup"><span data-stu-id="87b46-109">Security</span></span>](#Security)  
  
-   <span data-ttu-id="87b46-110">**데이터베이스 데이터 정렬을 설정하거나 변경하려면:**</span><span class="sxs-lookup"><span data-stu-id="87b46-110">**To set or change the database collation, using:**</span></span>  
  
     [<span data-ttu-id="87b46-111">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="87b46-111">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="87b46-112">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="87b46-112">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="87b46-113">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="87b46-113">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="87b46-114">제한 사항</span><span class="sxs-lookup"><span data-stu-id="87b46-114">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="87b46-115">Windows 유니코드 전용 데이터 정렬은 COLLATE 절에서 열 수준 및 식 수준 데이터의 `nchar`, `nvarchar` 및 `ntext` 데이터 형식에 데이터 정렬을 적용하기 위해서만 사용할 수 있고</span><span class="sxs-lookup"><span data-stu-id="87b46-115">Windows Unicode-only collations can only be used with the COLLATE clause to apply collations to the `nchar`, `nvarchar`, and `ntext` data types on column level and expression-level data.</span></span> <span data-ttu-id="87b46-116">COLLATE 절에서 데이터베이스 또는 서버 인스턴스의 데이터 정렬을 변경하기 위해 사용할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="87b46-116">They cannot be used with the COLLATE clause to change the collation of a database or server instance.</span></span>  
  
-   <span data-ttu-id="87b46-117">지정된 데이터 정렬 또는 참조된 개체가 사용하는 데이터 정렬에서 Windows가 지원하지 않는 코드 페이지를 사용하는 경우에는 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 에서 오류가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="87b46-117">If the specified collation or the collation used by the referenced object uses a code page that is not supported by Windows, the [!INCLUDE[ssDE](../../includes/ssde-md.md)] displays an error.</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="87b46-118">권장 사항</span><span class="sxs-lookup"><span data-stu-id="87b46-118">Recommendations</span></span>  
  
-   <span data-ttu-id="87b46-119">지원되는 데이터 정렬 이름은 [Windows 데이터 정렬 이름&#40;Transact-SQL&#41;](/sql/t-sql/statements/windows-collation-name-transact-sql) 및 [SQL Server 데이터 정렬 이름&#40;Transact-SQL&#41;](/sql/t-sql/statements/sql-server-collation-name-transact-sql)에서 확인할 수 있거나 [sys.fn_helpcollations&#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/sys-fn-helpcollations-transact-sql) 시스템 함수를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="87b46-119">You can find the supported collation names in [Windows Collation Name &#40;Transact-SQL&#41;](/sql/t-sql/statements/windows-collation-name-transact-sql) and [SQL Server Collation Name &#40;Transact-SQL&#41;](/sql/t-sql/statements/sql-server-collation-name-transact-sql); or you can use the [sys.fn_helpcollations &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/sys-fn-helpcollations-transact-sql) system function.</span></span>  
  
-   <span data-ttu-id="87b46-120">데이터베이스 데이터 정렬을 변경하면 다음 사항이 변경됩니다.</span><span class="sxs-lookup"><span data-stu-id="87b46-120">When you change the database collation, you change the following:</span></span>  
  
    -   <span data-ttu-id="87b46-121">시스템 테이블의 `char`, `varchar`, `text`, `nchar`, `nvarchar` 또는 `ntext` 열이 새 데이터 정렬로 변경됩니다.</span><span class="sxs-lookup"><span data-stu-id="87b46-121">Any `char`, `varchar`, `text`, `nchar`, `nvarchar`, or `ntext` columns in system tables are changed to the new collation.</span></span>  
  
    -   <span data-ttu-id="87b46-122">저장 프로시저 및 사용자 정의 함수에 대한 모든 기존 `char`, `varchar`, `text`, `nchar`, `nvarchar` 또는 `ntext` 매개 변수와 스칼라 반환 값이 새 데이터 정렬로 변경됩니다.</span><span class="sxs-lookup"><span data-stu-id="87b46-122">All existing `char`, `varchar`, `text`, `nchar`, `nvarchar`, or `ntext` parameters and scalar return values for stored procedures and user-defined functions are changed to the new collation.</span></span>  
  
    -   <span data-ttu-id="87b46-123">`char`, `varchar`, `text`, `nchar`, `nvarchar` 또는 `ntext` 시스템 데이터 형식 및 이러한 시스템 데이터 형식에 기반을 두는 모든 사용자 정의 데이터 형식이 새 기본 데이터 정렬로 변경됩니다.</span><span class="sxs-lookup"><span data-stu-id="87b46-123">The `char`, `varchar`, `text`, `nchar`, `nvarchar`, or `ntext` system data types, and all user-defined data types based on these system data types, are changed to the new default collation.</span></span>  
  
-   <span data-ttu-id="87b46-124">사용자 데이터베이스에서 새로 만든 새 개체의 데이터 정렬은 [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql) 문의 COLLATE 절을 사용하여 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="87b46-124">You can change the collation of any new objects that are created in a user database by using the COLLATE clause of the [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql) statement.</span></span> <span data-ttu-id="87b46-125">이 문은 기존 사용자 정의 테이블에 있는 열의 데이터 정렬은 변경하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="87b46-125">This statement does not change the collation of the columns in any existing user-defined tables.</span></span> <span data-ttu-id="87b46-126">이러한 열은 [ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql)문의 COLLATE 절을 사용하여 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="87b46-126">These can be changed by using the COLLATE clause of [ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="87b46-127">보안</span><span class="sxs-lookup"><span data-stu-id="87b46-127">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="87b46-128">권한</span><span class="sxs-lookup"><span data-stu-id="87b46-128">Permissions</span></span>  
 <span data-ttu-id="87b46-129">CREATE DATABASE</span><span class="sxs-lookup"><span data-stu-id="87b46-129">CREATE DATABASE</span></span>  
 <span data-ttu-id="87b46-130">**Master** 데이터베이스에서 create database 권한이 있거나 create any DATABASE 또는 ALTER any database 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="87b46-130">Requires CREATE DATABASE permission in the **master** database, or requires CREATE ANY DATABASE, or ALTER ANY DATABASE permission.</span></span>  
  
 <span data-ttu-id="87b46-131">ALTER DATABASE</span><span class="sxs-lookup"><span data-stu-id="87b46-131">ALTER DATABASE</span></span>  
 <span data-ttu-id="87b46-132">데이터베이스에 대한 ALTER 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="87b46-132">Requires ALTER permission on the database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="87b46-133">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="87b46-133">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-set-or-change-the-database-collation"></a><span data-ttu-id="87b46-134">데이터베이스 데이터 정렬을 설정하거나 변경하려면</span><span class="sxs-lookup"><span data-stu-id="87b46-134">To set or change the database collation</span></span>  
  
1.  <span data-ttu-id="87b46-135">**개체 탐색기**에서 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]의 인스턴스에 연결하고 해당 인스턴스를 확장한 다음 **데이터베이스**를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="87b46-135">In **Object Explorer**, connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], expand that instance, and then expand **Databases**.</span></span>  
  
2.  <span data-ttu-id="87b46-136">새 데이터베이스를 만들려는 경우 **데이터베이스** 를 마우스 오른쪽 단추로 클릭한 다음 **새 데이터베이스**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="87b46-136">If you are creating a new database, right-click **Databases** and then click **New Database**.</span></span> <span data-ttu-id="87b46-137">기본 데이터 정렬을 원하지 않는 경우 **옵션** 페이지를 클릭하고 **데이터 정렬** 드롭다운 목록에서 데이터 정렬을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="87b46-137">If you do not want the default collation, click the **Options** page, and select a collation from the **Collation** drop-down list.</span></span>  
  
     <span data-ttu-id="87b46-138">또는 데이터베이스가 이미 있는 경우 원하는 데이터베이스를 마우스 오른쪽 단추로 클릭하고 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="87b46-138">Alternatively, if the database already exists, right-click the database that you want and click **Properties**.</span></span> <span data-ttu-id="87b46-139">**옵션** 페이지를 클릭하고 **데이터 정렬** 드롭다운 목록에서 데이터 정렬을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="87b46-139">Click the **Options** page, and select a collation from the **Collation** drop-down list.</span></span>  
  
3.  <span data-ttu-id="87b46-140">작업이 완료되면 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="87b46-140">After you are finished, click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="87b46-141">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="87b46-141">Using Transact-SQL</span></span>  
  
#### <a name="to-set-the-database-collation"></a><span data-ttu-id="87b46-142">데이터베이스 데이터 정렬을 설정하려면</span><span class="sxs-lookup"><span data-stu-id="87b46-142">To set the database collation</span></span>  
  
1.  <span data-ttu-id="87b46-143">[!INCLUDE[ssDE](../../includes/ssde-md.md)]에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="87b46-143">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="87b46-144">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="87b46-144">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="87b46-145">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="87b46-145">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="87b46-146">이 예에서는 [COLLATE](/sql/t-sql/statements/collations) 절을 사용하여 데이터 정렬 이름을 지정하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="87b46-146">This example shows how to use the [COLLATE](/sql/t-sql/statements/collations) clause to specify a collation name.</span></span> <span data-ttu-id="87b46-147">이 예에서는 `MyOptionsTest` 데이터 정렬을 사용하는 `Latin1_General_100_CS_AS_SC` 데이터베이스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="87b46-147">The example creates the database `MyOptionsTest` that uses the `Latin1_General_100_CS_AS_SC` collation.</span></span> <span data-ttu-id="87b46-148">데이터베이스를 만든 후 `SELECT` 문을 실행하여 설정을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="87b46-148">After you create the database, execute the `SELECT` statement to verify the setting.</span></span>  
  
```sql  
USE master;  
GO  
IF DB_ID (N'MyOptionsTest') IS NOT NULL  
DROP DATABASE MyOptionsTest;  
GO  
CREATE DATABASE MyOptionsTest  
COLLATE Latin1_General_100_CS_AS_SC;  
GO  
  
--Verify the collation setting.  
SELECT name, collation_name  
FROM sys.databases  
WHERE name = N'MyOptionsTest';  
GO  
  
```  
  
#### <a name="to-change-the-database-collation"></a><span data-ttu-id="87b46-149">데이터베이스 데이터 정렬을 변경하려면</span><span class="sxs-lookup"><span data-stu-id="87b46-149">To change the database collation</span></span>  
  
1.  <span data-ttu-id="87b46-150">[!INCLUDE[ssDE](../../includes/ssde-md.md)]에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="87b46-150">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="87b46-151">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="87b46-151">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="87b46-152">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="87b46-152">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="87b46-153">이 예에서는 [ALTER DATABASE](/sql/t-sql/statements/collations) 문에 [COLLATE](/sql/t-sql/statements/alter-database-transact-sql) 절을 사용하여 데이터 정렬 이름을 변경하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="87b46-153">This example shows how to use the [COLLATE](/sql/t-sql/statements/collations) clause in an [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql) statement to change the collation name.</span></span> <span data-ttu-id="87b46-154">`SELECT` 문을 실행하여 변경 내용을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="87b46-154">Execute the `SELECT` statement to verify the change.</span></span>  
  
```sql  
USE master;  
GO  
ALTER DATABASE MyOptionsTest  
COLLATE French_CI_AS ;  
GO  
  
--Verify the collation setting.  
SELECT name, collation_name  
FROM sys.databases  
WHERE name = N'MyOptionsTest';  
GO  
  
```  
  
## <a name="see-also"></a><span data-ttu-id="87b46-155">참고 항목</span><span class="sxs-lookup"><span data-stu-id="87b46-155">See Also</span></span>  
 <span data-ttu-id="87b46-156">[데이터 정렬 및 유니코드 지원](collation-and-unicode-support.md) </span><span class="sxs-lookup"><span data-stu-id="87b46-156">[Collation and Unicode Support](collation-and-unicode-support.md) </span></span>  
 <span data-ttu-id="87b46-157">[sys.fn_helpcollations&#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/sys-fn-helpcollations-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="87b46-157">[sys.fn_helpcollations &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/sys-fn-helpcollations-transact-sql) </span></span>  
 <span data-ttu-id="87b46-158">[sys.databases&#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="87b46-158">[sys.databases &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) </span></span>  
 <span data-ttu-id="87b46-159">[SQL Server 데이터 정렬 이름&#40;Transact-SQL&#41;](/sql/t-sql/statements/sql-server-collation-name-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="87b46-159">[SQL Server Collation Name &#40;Transact-SQL&#41;](/sql/t-sql/statements/sql-server-collation-name-transact-sql) </span></span>  
 <span data-ttu-id="87b46-160">[Windows 데이터 정렬 이름&#40;Transact-SQL&#41;](/sql/t-sql/statements/windows-collation-name-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="87b46-160">[Windows Collation Name &#40;Transact-SQL&#41;](/sql/t-sql/statements/windows-collation-name-transact-sql) </span></span>  
 <span data-ttu-id="87b46-161">[COLLATE&#40;Transact-SQL&#41;](/sql/t-sql/statements/collations) </span><span class="sxs-lookup"><span data-stu-id="87b46-161">[COLLATE &#40;Transact-SQL&#41;](/sql/t-sql/statements/collations) </span></span>  
 <span data-ttu-id="87b46-162">[데이터 정렬 선행 규칙&#40;Transact-SQL&#41;](/sql/t-sql/statements/collation-precedence-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="87b46-162">[Collation Precedence &#40;Transact-SQL&#41;](/sql/t-sql/statements/collation-precedence-transact-sql) </span></span>  
 <span data-ttu-id="87b46-163">[CREATE TABLE&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-table-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="87b46-163">[CREATE TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-table-transact-sql) </span></span>  
 <span data-ttu-id="87b46-164">[CREATE DATABASE&#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="87b46-164">[CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql) </span></span>  
 <span data-ttu-id="87b46-165">[ALTER TABLE&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="87b46-165">[ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql) </span></span>  
 [<span data-ttu-id="87b46-166">ALTER DATABASE&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="87b46-166">ALTER DATABASE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-database-transact-sql)  
  
  
