---
title: 저장 프로시저의 정의 보기 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.technology: stored-procedures
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- stored procedures [SQL Server], viewing
- definition of stored procedure
- viewing stored procedures
- displaying stored procedures
ms.assetid: 93318587-a0c5-4788-946f-3b5dc8372ea9
author: stevestein
ms.author: sstein
ms.openlocfilehash: 4da455d38f984b08ee1f396f26cd4cc85411be92
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650875"
---
# <a name="view-the-definition-of-a-stored-procedure"></a><span data-ttu-id="3d48c-102">저장 프로시저의 정의 보기</span><span class="sxs-lookup"><span data-stu-id="3d48c-102">View the Definition of a Stored Procedure</span></span>
    
##  <a name="you-can-view-the-definition-of-a-stored-procedure-in-ssmanstudiofull-using-object-explorer-menu-options-or-in-the-query-editor-using-tsql-this-topic-describes-how-to-view-the-definition-of-procedure-in-object-explorer-and-by-using-a-system-stored-procedure-system-function-and-object-catalog-view-in-the-query-editor"></a><a name="Top"></a><span data-ttu-id="3d48c-103">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 에서 개체 탐색기 메뉴 옵션을 사용하거나 쿼리 편집기에서 [!INCLUDE[tsql](../../includes/tsql-md.md)]을 사용하여 저장 프로시저의 정의를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3d48c-103">You can view the definition of a stored procedure in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] using Object Explorer menu options or in the Query Editor using [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="3d48c-104">이 항목에서는 의 개체 탐색기를 사용하거나 시스템 저장 프로시저, 시스템 함수 및 쿼리 편집기의 개체 카탈로그 뷰를 사용하여 프로시저 정의를 보는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="3d48c-104">This topic describes how to view the definition of procedure in Object Explorer and by using a system stored procedure, system function, and object catalog view in the Query Editor.</span></span>  
  
-   <span data-ttu-id="3d48c-105">**시작하기 전 주의 사항:**  [보안](#Security)</span><span class="sxs-lookup"><span data-stu-id="3d48c-105">**Before you begin:**  [Security](#Security)</span></span>  
  
-   <span data-ttu-id="3d48c-106">**프로시저 정의를 볼 때 사용할 기능**  [SQL Server Management Studio](#SSMSProcedure), [Transact-SQL](#TsqlProcedure)</span><span class="sxs-lookup"><span data-stu-id="3d48c-106">**To view the definition of a procedure, using:**  [SQL Server Management Studio](#SSMSProcedure), [Transact-SQL](#TsqlProcedure)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="3d48c-107">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="3d48c-107">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="3d48c-108">보안</span><span class="sxs-lookup"><span data-stu-id="3d48c-108">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="3d48c-109">권한</span><span class="sxs-lookup"><span data-stu-id="3d48c-109">Permissions</span></span>  
 <span data-ttu-id="3d48c-110">시스템 저장 프로시저: `sp_helptext`</span><span class="sxs-lookup"><span data-stu-id="3d48c-110">System Stored Procedure: `sp_helptext`</span></span>  
 <span data-ttu-id="3d48c-111">**public** 역할의 멤버 자격이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="3d48c-111">Requires membership in the **public** role.</span></span> <span data-ttu-id="3d48c-112">시스템 개체 정의는 공개적으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="3d48c-112">System object definitions are publicly visible.</span></span> <span data-ttu-id="3d48c-113">개체 소유자나 ALTER, CONTROL, TAKE OWNERSHIP 또는 VIEW DEFINITION 권한 중 하나를 부여 받은 사람은 사용자 개체의 정의를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3d48c-113">The definition of user objects is visible to the object owner or grantees that have any one of the following permissions: ALTER, CONTROL, TAKE OWNERSHIP, or VIEW DEFINITION.</span></span>  
  
 <span data-ttu-id="3d48c-114">시스템 함수: `OBJECT_DEFINITION`</span><span class="sxs-lookup"><span data-stu-id="3d48c-114">System Function: `OBJECT_DEFINITION`</span></span>  
 <span data-ttu-id="3d48c-115">시스템 개체 정의는 공개적으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="3d48c-115">System object definitions are publicly visible.</span></span> <span data-ttu-id="3d48c-116">개체 소유자나 ALTER, CONTROL, TAKE OWNERSHIP 또는 VIEW DEFINITION 권한 중 하나를 부여 받은 사람은 사용자 개체의 정의를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3d48c-116">The definition of user objects is visible to the object owner or grantees that have any one of the following permissions: ALTER, CONTROL, TAKE OWNERSHIP, or VIEW DEFINITION.</span></span> <span data-ttu-id="3d48c-117">이 권한은 **db_owner**, **db_ddladmin**및 **db_securityadmin** 고정 데이터베이스 역할의 멤버가 암시적으로 보유합니다.</span><span class="sxs-lookup"><span data-stu-id="3d48c-117">These permissions are implicitly held by members of the **db_owner**, **db_ddladmin**, and **db_securityadmin** fixed database roles.</span></span>  
  
 <span data-ttu-id="3d48c-118">개체 카탈로그 뷰: `sys.sql_modules`</span><span class="sxs-lookup"><span data-stu-id="3d48c-118">Object Catalog View: `sys.sql_modules`</span></span>  
 <span data-ttu-id="3d48c-119">사용자가 소유하고 있거나 사용 권한을 부여 받은 보안 개체에 대해서만 카탈로그 뷰의 메타데이터를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3d48c-119">The visibility of the metadata in catalog views is limited to securables that a user either owns or on which the user has been granted some permission.</span></span> <span data-ttu-id="3d48c-120">자세한 내용은 [Metadata Visibility Configuration](../security/metadata-visibility-configuration.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3d48c-120">For more information, see [Metadata Visibility Configuration](../security/metadata-visibility-configuration.md).</span></span>  
  
##  <a name="how-to-view-the-definition-of-a-stored-procedure"></a><a name="Procedures"></a> <span data-ttu-id="3d48c-121">저장 프로시저의 정의를 보는 방법</span><span class="sxs-lookup"><span data-stu-id="3d48c-121">How to View the Definition of a Stored Procedure</span></span>  
 <span data-ttu-id="3d48c-122">다음 중 하나를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3d48c-122">You can use one of the following:</span></span>  
  
-   [<span data-ttu-id="3d48c-123">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="3d48c-123">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
-   [<span data-ttu-id="3d48c-124">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="3d48c-124">Transact-SQL</span></span>](#TsqlProcedure)  
  
###  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="3d48c-125">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="3d48c-125">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="3d48c-126">**개체 탐색기에서 프로시저 정의를 보려면**</span><span class="sxs-lookup"><span data-stu-id="3d48c-126">**To view the definition a procedure in Object Explorer**</span></span>  
  
1.  <span data-ttu-id="3d48c-127">개체 탐색기에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 의 인스턴스에 연결한 다음 해당 인스턴스를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="3d48c-127">In Object Explorer, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)] and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="3d48c-128">**데이터베이스**를 확장하고 해당 프로시저가 속한 데이터베이스를 확장한 다음 **프로그래밍 기능**을 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="3d48c-128">Expand **Databases**, expand the database in which the procedure belongs, and then expand **Programmability**.</span></span>  
  
3.  <span data-ttu-id="3d48c-129">**저장 프로시저**를 확장하고 프로시저를 마우스 오른쪽 단추로 클릭한 다음 **저장 프로시저 스크립팅**을 클릭하고 **Create To**, **Alter To**또는 **Drop and Create To**중 하나를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3d48c-129">Expand **Stored Procedures**, right-click the procedure and then click **Script Stored Procedure as**, and then click one of the following: **Create To**, **Alter To**, or **Drop and Create To**.</span></span>  
  
4.  <span data-ttu-id="3d48c-130">**새 쿼리 편집기 창**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3d48c-130">Select **New Query Editor Window**.</span></span> <span data-ttu-id="3d48c-131">프로시저 정의가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="3d48c-131">This will display the procedure definition.</span></span>  
  
###  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="3d48c-132">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="3d48c-132">Using Transact-SQL</span></span>  
 <span data-ttu-id="3d48c-133">**쿼리 편집기에서 저장 프로시저의 정의를 보려면**</span><span class="sxs-lookup"><span data-stu-id="3d48c-133">**To view the definition of a procedure in Query Editor**</span></span>  
  
 <span data-ttu-id="3d48c-134">시스템 저장 프로시저: `sp_helptext`</span><span class="sxs-lookup"><span data-stu-id="3d48c-134">System Stored Procedure: `sp_helptext`</span></span>  
 1.  <span data-ttu-id="3d48c-135">개체 탐색기에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)]의 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="3d48c-135">In Object Explorer, connect to an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="3d48c-136">도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3d48c-136">On the toolbar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="3d48c-137">쿼리 창에서 `sp_helptext` 시스템 저장 프로시저를 사용하는 다음 문을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="3d48c-137">In the query window, enter the following statement that uses the `sp_helptext` system stored procedure.</span></span> <span data-ttu-id="3d48c-138">원하는 데이터베이스와 저장 프로시저를 참조하도록 데이터베이스 이름과 저장 프로시저 이름을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="3d48c-138">Change the database name and stored procedure name to reference the database and stored procedure that you want.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    EXEC sp_helptext N'AdventureWorks2012.dbo.uspLogError';  
    ```  
  
 <span data-ttu-id="3d48c-139">시스템 함수: `OBJECT_DEFINITION`</span><span class="sxs-lookup"><span data-stu-id="3d48c-139">System Function: `OBJECT_DEFINITION`</span></span>  
 1.  <span data-ttu-id="3d48c-140">개체 탐색기에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)]의 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="3d48c-140">In Object Explorer, connect to an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="3d48c-141">도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3d48c-141">On the toolbar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="3d48c-142">쿼리 창에서 `OBJECT_DEFINITION` 시스템 함수를 사용하는 다음 문을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="3d48c-142">In the query window, enter the following statements that use the `OBJECT_DEFINITION` system function.</span></span> <span data-ttu-id="3d48c-143">원하는 데이터베이스와 저장 프로시저를 참조하도록 데이터베이스 이름과 저장 프로시저 이름을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="3d48c-143">Change the database name and stored procedure name to reference the database and stored procedure that you want.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SELECT OBJECT_DEFINITION (OBJECT_ID(N'AdventureWorks2012.dbo.uspLogError'));  
    ```  
  
 <span data-ttu-id="3d48c-144">개체 카탈로그 뷰: `sys.sql_modules`</span><span class="sxs-lookup"><span data-stu-id="3d48c-144">Object Catalog View: `sys.sql_modules`</span></span>  
 1.  <span data-ttu-id="3d48c-145">개체 탐색기에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)]의 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="3d48c-145">In Object Explorer, connect to an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="3d48c-146">도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3d48c-146">On the toolbar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="3d48c-147">쿼리 창에서 `sys.sql_modules` 카탈로그 뷰를 사용하는 다음 문을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="3d48c-147">In the query window, enter the following statements that use the `sys.sql_modules` catalog view.</span></span> <span data-ttu-id="3d48c-148">원하는 데이터베이스와 저장 프로시저를 참조하도록 데이터베이스 이름과 저장 프로시저 이름을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="3d48c-148">Change the database name and stored procedure name to reference the database and stored procedure that you want.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SELECT definition  
    FROM sys.sql_modules  
    WHERE object_id = (OBJECT_ID(N'AdventureWorks2012.dbo.uspLogError'));  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="3d48c-149">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3d48c-149">See Also</span></span>  
 <span data-ttu-id="3d48c-150">[저장 프로시저 만들기](create-a-stored-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="3d48c-150">[Create a Stored Procedure](create-a-stored-procedure.md) </span></span>  
 <span data-ttu-id="3d48c-151">[저장 프로시저 수정](modify-a-stored-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="3d48c-151">[Modify a Stored Procedure](modify-a-stored-procedure.md) </span></span>  
 <span data-ttu-id="3d48c-152">[저장 프로시저 삭제](delete-a-stored-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="3d48c-152">[Delete a Stored Procedure](delete-a-stored-procedure.md) </span></span>  
 <span data-ttu-id="3d48c-153">[저장 프로시저 이름 바꾸기](rename-a-stored-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="3d48c-153">[Rename a Stored Procedure](rename-a-stored-procedure.md) </span></span>  
 <span data-ttu-id="3d48c-154">[OBJECT_DEFINITION&#40;Transact-SQL&#41;](/sql/t-sql/functions/object-definition-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="3d48c-154">[OBJECT_DEFINITION &#40;Transact-SQL&#41;](/sql/t-sql/functions/object-definition-transact-sql) </span></span>  
 <span data-ttu-id="3d48c-155">[sys.sql_modules&#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-sql-modules-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="3d48c-155">[sys.sql_modules &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-sql-modules-transact-sql) </span></span>  
 <span data-ttu-id="3d48c-156">[sp_helptext&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helptext-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="3d48c-156">[sp_helptext &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helptext-transact-sql) </span></span>  
 [<span data-ttu-id="3d48c-157">OBJECT_ID&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="3d48c-157">OBJECT_ID &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/object-id-transact-sql)  
  
  
