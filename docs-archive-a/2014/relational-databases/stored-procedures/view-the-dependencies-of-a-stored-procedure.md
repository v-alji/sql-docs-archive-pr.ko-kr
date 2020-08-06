---
title: 저장 프로시저의 종속성 보기 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.technology: stored-procedures
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- stored procedures [SQL Server], dependencies
- displaying stored procedure dependencies
- viewing stored procedure dependencies
ms.assetid: 6ae0a369-1bc7-4ae4-be89-2b483697cd1f
author: stevestein
ms.author: sstein
ms.openlocfilehash: 790684035d2db3b697fb8b718c96182eda8f1186
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661615"
---
# <a name="view-the-dependencies-of-a-stored-procedure"></a><span data-ttu-id="e50fd-102">저장 프로시저의 종속성 보기</span><span class="sxs-lookup"><span data-stu-id="e50fd-102">View the Dependencies of a Stored Procedure</span></span>
    
##  <a name="this-topic-describes-how-to-view-stored-procedure-dependencies-in-sscurrent-by-using-ssmanstudiofull-or-tsql"></a><a name="Top"></a><span data-ttu-id="e50fd-103">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 또는 [!INCLUDE[tsql](../../includes/tsql-md.md)]을 사용하여 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]의 저장 프로시저 종속성을 보는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="e50fd-103">This topic describes how to view stored procedure dependencies in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
-   <span data-ttu-id="e50fd-104">**시작하기 전 주의 사항:**  [보안](#Security)</span><span class="sxs-lookup"><span data-stu-id="e50fd-104">**Before you begin:**  [Security](#Security)</span></span>  
  
-   <span data-ttu-id="e50fd-105">**저장 프로시저의 종속성을 보려면 다음을 사용합니다.**  [SQL Server Management Studio](#SSMSProcedure), [Transact-SQL](#TsqlProcedure)</span><span class="sxs-lookup"><span data-stu-id="e50fd-105">**To view the dependencies of a procedure, using:**  [SQL Server Management Studio](#SSMSProcedure), [Transact-SQL](#TsqlProcedure)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="e50fd-106">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="e50fd-106">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="e50fd-107">보안</span><span class="sxs-lookup"><span data-stu-id="e50fd-107">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="e50fd-108">권한</span><span class="sxs-lookup"><span data-stu-id="e50fd-108">Permissions</span></span>  
 <span data-ttu-id="e50fd-109">시스템 함수: `sys.dm_sql_referencing_entities`</span><span class="sxs-lookup"><span data-stu-id="e50fd-109">System Function: `sys.dm_sql_referencing_entities`</span></span>  
 <span data-ttu-id="e50fd-110">참조된 엔터티에 대한 CONTROL 권한과 sys.dm_sql_referencing_entities에 대한 SELECT 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="e50fd-110">Requires CONTROL permission on the referenced entity and SELECT permission on sys.dm_sql_referencing_entities.</span></span> <span data-ttu-id="e50fd-111">참조된 엔터티가 파티션 함수인 경우 데이터베이스에 대한 CONTROL 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="e50fd-111">When the referenced entity is a partition function, CONTROL permission on the database is required.</span></span> <span data-ttu-id="e50fd-112">기본적으로 SELECT 권한은 public에 부여됩니다.</span><span class="sxs-lookup"><span data-stu-id="e50fd-112">By default, SELECT permission is granted to public.</span></span>  
  
 <span data-ttu-id="e50fd-113">시스템 함수: `sys.dm_sql_referenced_entities`</span><span class="sxs-lookup"><span data-stu-id="e50fd-113">System Function: `sys.dm_sql_referenced_entities`</span></span>  
 <span data-ttu-id="e50fd-114">sys.dm_sql_referenced_entities에 대한 SELECT 권한 및 참조 엔터티에 대한 VIEW DEFINITION 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="e50fd-114">Requires SELECT permission on sys.dm_sql_referenced_entities and VIEW DEFINITION permission on the referencing entity.</span></span> <span data-ttu-id="e50fd-115">기본적으로 SELECT 권한은 public에 부여됩니다.</span><span class="sxs-lookup"><span data-stu-id="e50fd-115">By default, SELECT permission is granted to public.</span></span> <span data-ttu-id="e50fd-116">참조 엔터티가 데이터 수준 DDL 트리거인 경우 데이터베이스에 대한 ALTER DATABASE DDL TRIGGER 권한 또는 데이터베이스에 대한 VIEW DEFINITION 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="e50fd-116">Requires VIEW DEFINITION permission on the database or ALTER DATABASE DDL TRIGGER permission on the database when the referencing entity is a database-level DDL trigger.</span></span> <span data-ttu-id="e50fd-117">참조 엔터티가 서버 수준 DDL 트리거인 경우 서버에 대한 VIEW ANY DEFINITION 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="e50fd-117">Requires VIEW ANY DEFINITION permission on the server when the referencing entity is a server-level DDL trigger.</span></span>  
  
 <span data-ttu-id="e50fd-118">개체 카탈로그 뷰: `sys.sql_expression_dependencies`</span><span class="sxs-lookup"><span data-stu-id="e50fd-118">Object Catalog View: `sys.sql_expression_dependencies`</span></span>  
 <span data-ttu-id="e50fd-119">데이터베이스에 대한 VIEW DEFINITION 권한과 데이터베이스의 sys.sql_expression_dependencies에 대한 SELECT 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="e50fd-119">Requires VIEW DEFINITION permission on the database and SELECT permission on sys.sql_expression_dependencies for the database.</span></span> <span data-ttu-id="e50fd-120">기본적으로 SELECT 권한은 db_owner 고정 데이터베이스 역할의 멤버에게만 부여됩니다.</span><span class="sxs-lookup"><span data-stu-id="e50fd-120">By default, SELECT permission is granted only to members of the db_owner fixed database role.</span></span> <span data-ttu-id="e50fd-121">SELECT와 VIEW DEFINITION 권한을 다른 사용자에게 부여하면 피부여자는 데이터베이스의 모든 종속성을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e50fd-121">When SELECT and VIEW DEFINITION permissions are granted to another user, the grantee can view all dependencies in the database.</span></span>  
  
##  <a name="how-to-view-the-dependencies-of-a-stored-procedure"></a><a name="Procedures"></a> <span data-ttu-id="e50fd-122">저장 프로시저의 종속성을 보는 방법</span><span class="sxs-lookup"><span data-stu-id="e50fd-122">How to View the Dependencies of a Stored Procedure</span></span>  
 <span data-ttu-id="e50fd-123">다음 중 하나를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e50fd-123">You can use one of the following:</span></span>  
  
-   [<span data-ttu-id="e50fd-124">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="e50fd-124">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
-   [<span data-ttu-id="e50fd-125">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="e50fd-125">Transact-SQL</span></span>](#TsqlProcedure)  
  
###  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="e50fd-126">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="e50fd-126">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="e50fd-127">**개체 탐색기에서 프로시저 종속성을 보려면**</span><span class="sxs-lookup"><span data-stu-id="e50fd-127">**To view the dependencies of a procedure in Object Explorer**</span></span>  
  
1.  <span data-ttu-id="e50fd-128">개체 탐색기에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 의 인스턴스에 연결한 다음 해당 인스턴스를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="e50fd-128">In Object Explorer, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)] and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="e50fd-129">**데이터베이스**를 확장하고 해당 프로시저가 속한 데이터베이스를 확장한 다음 **프로그래밍 기능**을 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="e50fd-129">Expand **Databases**, expand the database in which the procedure belongs, and then expand **Programmability**.</span></span>  
  
3.  <span data-ttu-id="e50fd-130">**저장 프로시저**를 확장하고 프로시저를 마우스 오른쪽 단추로 클릭한 다음 **종속성 보기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e50fd-130">Expand **Stored Procedures**, right-click the procedure and then click **View Dependencies**.</span></span>  
  
4.  <span data-ttu-id="e50fd-131">프로시저에 종속된 개체 목록을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="e50fd-131">View the list of objects that depend on the procedure.</span></span>  
  
5.  <span data-ttu-id="e50fd-132">프로시저가 종속된 개체 목록을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="e50fd-132">View the list of objects on which the procedure depends.</span></span>  
  
6.  <span data-ttu-id="e50fd-133">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e50fd-133">Click **OK**.</span></span>  
  
###  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="e50fd-134">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="e50fd-134">Using Transact-SQL</span></span>  
 <span data-ttu-id="e50fd-135">**쿼리 편집기에서 프로시저의 종속성을 보려면**</span><span class="sxs-lookup"><span data-stu-id="e50fd-135">**To view the dependencies of a procedure in Query Editor**</span></span>  
  
 <span data-ttu-id="e50fd-136">시스템 함수: `sys.dm_sql_referencing_entities`</span><span class="sxs-lookup"><span data-stu-id="e50fd-136">System Function: `sys.dm_sql_referencing_entities`</span></span>  
 <span data-ttu-id="e50fd-137">이 함수는 프로시저에 종속된 개체를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="e50fd-137">This function is used to display the objects that depend on a procedure.</span></span>  
  
1.  <span data-ttu-id="e50fd-138">**개체 탐색기**에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 의 인스턴스에 연결한 다음 해당 인스턴스를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="e50fd-138">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)] and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="e50fd-139">**데이터베이스**를 확장하고 프로시저가 속한 데이터베이스를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="e50fd-139">Expand **Databases**, expand the database in which the procedure belongs.</span></span>  
  
3.  <span data-ttu-id="e50fd-140">**파일** 메뉴에서 **새 쿼리** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e50fd-140">Click on **New Query** under the **File** menu.</span></span>  
  
4.  <span data-ttu-id="e50fd-141">다음 예를 복사하여 쿼리 편집기에 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="e50fd-141">Copy and paste the following examples into the query editor.</span></span> <span data-ttu-id="e50fd-142">첫 번째 예에서는 `uspVendorAllInfo` 데이터베이스의 모든 공급업체 이름, 해당 공급업체가 공급하는 제품, 신용 등급 및 사용 가능성을 반환하는 [!INCLUDE[ssSampleDBCoFull](../../includes/sssampledbcofull-md.md)] 프로시저를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e50fd-142">The first example creates the `uspVendorAllInfo` procedure, which returns the names of all the vendors in the [!INCLUDE[ssSampleDBCoFull](../../includes/sssampledbcofull-md.md)] database, the products they supply, their credit ratings, and their availability.</span></span>  
  
     [!code-sql[ProcedureDDL#CreateProc8](../../snippets/tsql/SQL14/tsql/procedureddl/transact-sql/createproc.sql#createproc8)]  
  
5.  <span data-ttu-id="e50fd-143">프로시저가 생성된 후 두 번째 예에서는 sys.dm_sql_referencing_entities 함수를 사용하여 프로시저에 종속된 개체를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="e50fd-143">After the procedure is created, the second example uses the sys.dm_sql_referencing_entities function to display the objects that depend on the procedure.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SELECT referencing_schema_name, referencing_entity_name, referencing_id, referencing_class_desc, is_caller_dependent  
    FROM sys.dm_sql_referencing_entities ('Purchasing.uspVendorAllInfo', 'OBJECT');   
    GO  
  
    ```  
  
 <span data-ttu-id="e50fd-144">시스템 함수: `sys.dm_sql_referenced_entities`</span><span class="sxs-lookup"><span data-stu-id="e50fd-144">System Function: `sys.dm_sql_referenced_entities`</span></span>  
 <span data-ttu-id="e50fd-145">이 함수는 프로시저에 종속된 개체를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="e50fd-145">This function is used to display the objects a procedure depends on.</span></span>  
  
1.  <span data-ttu-id="e50fd-146">**개체 탐색기**에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 의 인스턴스에 연결한 다음 해당 인스턴스를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="e50fd-146">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)] and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="e50fd-147">**데이터베이스**를 확장하고 프로시저가 속한 데이터베이스를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="e50fd-147">Expand **Databases**, expand the database in which the procedure belongs.</span></span>  
  
3.  <span data-ttu-id="e50fd-148">**파일** 메뉴에서 **새 쿼리** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e50fd-148">Click on **New Query** under the **File** menu.</span></span>  
  
4.  <span data-ttu-id="e50fd-149">다음 예를 복사하여 쿼리 편집기에 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="e50fd-149">Copy and paste the following examples into the query editor.</span></span> <span data-ttu-id="e50fd-150">첫 번째 예에서는 `uspVendorAllInfo` 데이터베이스의 모든 공급업체 이름, 해당 공급업체가 공급하는 제품, 신용 등급 및 사용 가능성을 반환하는 [!INCLUDE[ssSampleDBCoFull](../../includes/sssampledbcofull-md.md)] 프로시저를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e50fd-150">The first example creates the `uspVendorAllInfo` procedure, which returns the names of all the vendors in the [!INCLUDE[ssSampleDBCoFull](../../includes/sssampledbcofull-md.md)] database, the products they supply, their credit ratings, and their availability.</span></span>  
  
     [!code-sql[ProcedureDDL#CreateProc8](../../snippets/tsql/SQL14/tsql/procedureddl/transact-sql/createproc.sql#createproc8)]  
  
5.  <span data-ttu-id="e50fd-151">프로시저가 생성된 후 두 번째 예에서는 sys.dm_sql_referenced_entities 함수를 사용하여 프로시저가 종속된 개체를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="e50fd-151">After the procedure is created, the second example uses the sys.dm_sql_referenced_entities function to display the objects that the procedure depends on.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SELECT referenced_schema_name, referenced_entity_name,  
    referenced_minor_name,referenced_minor_id, referenced_class_desc,  
    is_caller_dependent, is_ambiguous  
    FROM sys.dm_sql_referencing_entities ('Purchasing.uspVendorAllInfo', 'OBJECT');  
    GO  
    ```  
  
 <span data-ttu-id="e50fd-152">개체 카탈로그 뷰: `sys.sql_expression_dependencies`</span><span class="sxs-lookup"><span data-stu-id="e50fd-152">Object Catalog View: `sys.sql_expression_dependencies`</span></span>  
 <span data-ttu-id="e50fd-153">이 뷰는 프로시저가 종속된 개체 또는 프로시저에 종속된 개체를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="e50fd-153">This view can be used to display objects that a procedure depends on or that depend on a procedure.</span></span>  
  
 <span data-ttu-id="e50fd-154">프로시저에 종속된 개체를 표시</span><span class="sxs-lookup"><span data-stu-id="e50fd-154">Displaying the objects that depend on a procedure.</span></span>  
 1.  <span data-ttu-id="e50fd-155">**개체 탐색기**에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 의 인스턴스에 연결한 다음 해당 인스턴스를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="e50fd-155">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)] and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="e50fd-156">**데이터베이스**를 확장하고 프로시저가 속한 데이터베이스를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="e50fd-156">Expand **Databases**, expand the database in which the procedure belongs.</span></span>  
  
3.  <span data-ttu-id="e50fd-157">**파일** 메뉴에서 **새 쿼리** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e50fd-157">Click on **New Query** under the **File** menu.</span></span>  
  
4.  <span data-ttu-id="e50fd-158">다음 예를 복사하여 쿼리 편집기에 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="e50fd-158">Copy and paste the following examples into the query editor.</span></span> <span data-ttu-id="e50fd-159">첫 번째 예에서는 `uspVendorAllInfo` 데이터베이스의 모든 공급업체 이름, 해당 공급업체가 공급하는 제품, 신용 등급 및 사용 가능성을 반환하는 [!INCLUDE[ssSampleDBCoFull](../../includes/sssampledbcofull-md.md)] 프로시저를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e50fd-159">The first example creates the `uspVendorAllInfo` procedure, which returns the names of all the vendors in the [!INCLUDE[ssSampleDBCoFull](../../includes/sssampledbcofull-md.md)] database, the products they supply, their credit ratings, and their availability.</span></span>  
  
     [!code-sql[ProcedureDDL#CreateProc8](../../snippets/tsql/SQL14/tsql/procedureddl/transact-sql/createproc.sql#createproc8)]  
  
5.  <span data-ttu-id="e50fd-160">프로시저가 생성된 후 두 번째 예에서는 sys.sql_expression_dependencies 뷰를 사용하여 프로시저에 종속된 개체를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="e50fd-160">After the procedure is created, the second example uses the sys.sql_expression_dependencies view to display the objects that depend on the procedure.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SELECT OBJECT_SCHEMA_NAME ( referencing_id ) AS referencing_schema_name,  
        OBJECT_NAME(referencing_id) AS referencing_entity_name,   
        o.type_desc AS referencing_desciption,   
        COALESCE(COL_NAME(referencing_id, referencing_minor_id), '(n/a)') AS referencing_minor_id,   
        referencing_class_desc, referenced_class_desc,  
        referenced_server_name, referenced_database_name, referenced_schema_name,  
        referenced_entity_name,   
        COALESCE(COL_NAME(referenced_id, referenced_minor_id), '(n/a)') AS referenced_column_name,  
        is_caller_dependent, is_ambiguous  
    FROM sys.sql_expression_dependencies AS sed  
    INNER JOIN sys.objects AS o ON sed.referencing_id = o.object_id  
    WHERE referenced_id = OBJECT_ID(N'Purchasing.uspVendorAllInfo')  
    GO  
    ```  
  
 <span data-ttu-id="e50fd-161">프로시저가 종속된 개체 목록을 표시</span><span class="sxs-lookup"><span data-stu-id="e50fd-161">Displaying the objects a procedure depends on.</span></span>  
 1.  <span data-ttu-id="e50fd-162">**개체 탐색기**에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 의 인스턴스에 연결한 다음 해당 인스턴스를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="e50fd-162">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)] and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="e50fd-163">**데이터베이스**를 확장하고 프로시저가 속한 데이터베이스를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="e50fd-163">Expand **Databases**, expand the database in which the procedure belongs.</span></span>  
  
3.  <span data-ttu-id="e50fd-164">**파일** 메뉴에서 **새 쿼리** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e50fd-164">Click on **New Query** under the **File** menu.</span></span>  
  
4.  <span data-ttu-id="e50fd-165">다음 예를 복사하여 쿼리 편집기에 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="e50fd-165">Copy and paste the following examples into the query editor.</span></span> <span data-ttu-id="e50fd-166">첫 번째 예에서는 `uspVendorAllInfo` 데이터베이스의 모든 공급업체 이름, 해당 공급업체가 공급하는 제품, 신용 등급 및 사용 가능성을 반환하는 [!INCLUDE[ssSampleDBCoFull](../../includes/sssampledbcofull-md.md)] 프로시저를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e50fd-166">The first example creates the `uspVendorAllInfo` procedure, which returns the names of all the vendors in the [!INCLUDE[ssSampleDBCoFull](../../includes/sssampledbcofull-md.md)] database, the products they supply, their credit ratings, and their availability.</span></span>  
  
     [!code-sql[ProcedureDDL#CreateProc8](../../snippets/tsql/SQL14/tsql/procedureddl/transact-sql/createproc.sql#createproc8)]  
  
5.  <span data-ttu-id="e50fd-167">프로시저가 생성된 후 두 번째 예에서는 sys.sql_expression_dependencies 뷰를 사용하여 프로시저가 종속된 개체를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="e50fd-167">After the procedure is created, the second example uses the sys.sql_expression_dependencies view to display the objects the procedure depends on.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SELECT OBJECT_NAME(referencing_id) AS referencing_entity_name,   
        o.type_desc AS referencing_desciption,   
        COALESCE(COL_NAME(referencing_id, referencing_minor_id), '(n/a)') AS referencing_minor_id,   
        referencing_class_desc, referenced_class_desc,  
        referenced_server_name, referenced_database_name, referenced_schema_name,  
        referenced_entity_name,   
        COALESCE(COL_NAME(referenced_id, referenced_minor_id), '(n/a)') AS referenced_column_name,  
        is_caller_dependent, is_ambiguous  
    FROM sys.sql_expression_dependencies AS sed  
    INNER JOIN sys.objects AS o ON sed.referencing_id = o.object_id  
    WHERE referencing_id = OBJECT_ID(N'Purchasing.uspVendorAllInfo')  
    GO  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="e50fd-168">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e50fd-168">See Also</span></span>  
 <span data-ttu-id="e50fd-169">[저장 프로시저 이름 바꾸기](rename-a-stored-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="e50fd-169">[Rename a Stored Procedure](rename-a-stored-procedure.md) </span></span>  
 <span data-ttu-id="e50fd-170">[sys.dm_sql_referencing_entities&#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-sql-referencing-entities-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="e50fd-170">[sys.dm_sql_referencing_entities &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-sql-referencing-entities-transact-sql) </span></span>  
 <span data-ttu-id="e50fd-171">[sys.dm_sql_referenced_entities&#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-sql-referenced-entities-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="e50fd-171">[sys.dm_sql_referenced_entities &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-sql-referenced-entities-transact-sql) </span></span>  
 [<span data-ttu-id="e50fd-172">sys.sql_expression_dependencies&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="e50fd-172">sys.sql_expression_dependencies &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql)  
  
  
