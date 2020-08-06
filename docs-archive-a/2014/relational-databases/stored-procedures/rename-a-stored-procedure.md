---
title: 저장 프로시저 이름 바꾸기 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.technology: stored-procedures
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- stored procedures [SQL Server], renaming
- renaming stored procedures
ms.assetid: 5d2e4c68-7e0b-4405-8919-f5b203e46770
author: stevestein
ms.author: sstein
ms.openlocfilehash: 02e1acb528a32ef242e160e0ce5dd0267237c876
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661620"
---
# <a name="rename-a-stored-procedure"></a><span data-ttu-id="91a15-102">저장 프로시저 이름 바꾸기</span><span class="sxs-lookup"><span data-stu-id="91a15-102">Rename a Stored Procedure</span></span>
  <span data-ttu-id="91a15-103">이 항목에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 에서 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 또는 [!INCLUDE[tsql](../../includes/tsql-md.md)]을 사용하여 저장 프로시저의 이름을 바꾸는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="91a15-103">This topic describes how to rename a stored procedure in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="91a15-104">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="91a15-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="91a15-105">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="91a15-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="91a15-106">제한 사항</span><span class="sxs-lookup"><span data-stu-id="91a15-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="91a15-107">보안</span><span class="sxs-lookup"><span data-stu-id="91a15-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="91a15-108">**저장 프로시저의 이름을 바꾸려면:**</span><span class="sxs-lookup"><span data-stu-id="91a15-108">**To rename a stored procedure, using:**</span></span>  
  
     [<span data-ttu-id="91a15-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="91a15-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="91a15-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="91a15-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="91a15-111">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="91a15-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="91a15-112">제한 사항</span><span class="sxs-lookup"><span data-stu-id="91a15-112">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="91a15-113">프로시저 이름은 [식별자](../databases/database-identifiers.md)에 대한 규칙을 따라야 합니다.</span><span class="sxs-lookup"><span data-stu-id="91a15-113">Procedure names must comply with the rules for [identifiers](../databases/database-identifiers.md).</span></span>  
  
-   <span data-ttu-id="91a15-114">저장 프로시저의 이름을 변경해도 **sys.sql_modules** 카탈로그 뷰의 정의 열에 있는 해당 개체 이름은 변경되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="91a15-114">Renaming a stored procedure will not change the name of the corresponding object name in the definition column of the **sys.sql_modules** catalog view.</span></span> <span data-ttu-id="91a15-115">따라서 이 개체 유형의 이름을 바꾸지 않는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="91a15-115">Therefore, we recommend that you do not rename this object type.</span></span> <span data-ttu-id="91a15-116">대신 저장 프로시저를 삭제하고 새로운 이름으로 다시 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="91a15-116">Instead, drop and re-create the stored procedure with its new name.</span></span>  
  
-   <span data-ttu-id="91a15-117">프로시저의 이름 또는 정의를 변경할 때 프로시저의 변경 내용이 적용되도록 개체를 업데이트하지 않으면 종속 개체가 실패할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="91a15-117">Changing the name or definition of a procedure can cause dependent objects to fail when the objects are not updated to reflect the changes that have been made to the procedure.</span></span> <span data-ttu-id="91a15-118">자세한 내용은 [저장 프로시저의 종속성 보기](view-the-dependencies-of-a-stored-procedure.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="91a15-118">For more information, see [View the Dependencies of a Stored Procedure](view-the-dependencies-of-a-stored-procedure.md).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="91a15-119">보안</span><span class="sxs-lookup"><span data-stu-id="91a15-119">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="91a15-120">권한</span><span class="sxs-lookup"><span data-stu-id="91a15-120">Permissions</span></span>  
 <span data-ttu-id="91a15-121">CREATE PROCEDURE</span><span class="sxs-lookup"><span data-stu-id="91a15-121">CREATE PROCEDURE</span></span>  
 <span data-ttu-id="91a15-122">데이터베이스에 대한 CREATE PROCEDURE 권한과 프로시저를 만들고 있는 스키마에 대한 ALTER 권한이 필요하거나 **db_ddladmin** 고정 데이터베이스 역할의 멤버 자격이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="91a15-122">Requires CREATE PROCEDURE permission in the database and ALTER permission on the schema in which the procedure is being created, or requires membership in the **db_ddladmin** fixed database role.</span></span>  
  
 <span data-ttu-id="91a15-123">ALTER PROCEDURE</span><span class="sxs-lookup"><span data-stu-id="91a15-123">ALTER PROCEDURE</span></span>  
 <span data-ttu-id="91a15-124">프로시저에 대한 ALTER 권한이나 **db_ddladmin** 고정 데이터베이스 역할의 멤버 자격이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="91a15-124">Requires ALTER permission on the procedure or requires membership in the **db_ddladmin** fixed database role.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="91a15-125">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="91a15-125">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-rename-a-stored-procedure"></a><span data-ttu-id="91a15-126">저장 프로시저의 이름을 바꾸려면</span><span class="sxs-lookup"><span data-stu-id="91a15-126">To rename a stored procedure</span></span>  
  
1.  <span data-ttu-id="91a15-127">개체 탐색기에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 의 인스턴스에 연결한 다음 해당 인스턴스를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="91a15-127">In Object Explorer, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)] and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="91a15-128">**데이터베이스**를 확장하고 해당 프로시저가 속한 데이터베이스를 확장한 다음 **프로그래밍 기능**을 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="91a15-128">Expand **Databases**, expand the database in which the procedure belongs, and then expand **Programmability**.</span></span>  
  
3.  <span data-ttu-id="91a15-129">[저장 프로시저의 종속성을 결정합니다](view-the-dependencies-of-a-stored-procedure.md).</span><span class="sxs-lookup"><span data-stu-id="91a15-129">[Determine the dependencies of the stored procedure](view-the-dependencies-of-a-stored-procedure.md).</span></span>  
  
4.  <span data-ttu-id="91a15-130">**저장 프로시저**를 확장하고 이름을 바꿀 프로시저를 마우스 오른쪽 단추로 클릭한 다음 **이름 바꾸기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="91a15-130">Expand **Stored Procedures**, right-click the procedure to rename, and then click **Rename**.</span></span>  
  
5.  <span data-ttu-id="91a15-131">프로시저 이름을 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="91a15-131">Modify the procedure name.</span></span>  
  
6.  <span data-ttu-id="91a15-132">종속 개체 또는 스크립트에서 참조된 프로시저 이름을 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="91a15-132">Modify the procedure name referenced in any dependent objects or scripts.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="91a15-133">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="91a15-133">Using Transact-SQL</span></span>  
  
#### <a name="to-rename-a-stored-procedure"></a><span data-ttu-id="91a15-134">저장 프로시저의 이름을 바꾸려면</span><span class="sxs-lookup"><span data-stu-id="91a15-134">To rename a stored procedure</span></span>  
  
1.  <span data-ttu-id="91a15-135">[!INCLUDE[ssDE](../../includes/ssde-md.md)]에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="91a15-135">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="91a15-136">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="91a15-136">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="91a15-137">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="91a15-137">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="91a15-138">이 예에서는 프로시저를 삭제하고 새 이름으로 다시 만들어 프로시저의 이름을 바꾸는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="91a15-138">This example shows how to rename a procedure by dropping the procedure and re-creating the procedure with a new name.</span></span> <span data-ttu-id="91a15-139">첫 번째 예에서는 `'HumanResources.uspGetAllEmployeesTest`저장 프로시저를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="91a15-139">The first example creates the stored procedure `'HumanResources.uspGetAllEmployeesTest`.</span></span> <span data-ttu-id="91a15-140">두 번째 예에서는 `HumanResources.uspEveryEmployeeTest`저장 프로시저의 이름을 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="91a15-140">The second example renames the stored procedure to `HumanResources.uspEveryEmployeeTest`.</span></span>  
  
```sql  
--Create the stored procedure.  
USE AdventureWorks2012;  
GO  
IF OBJECT_ID ( 'HumanResources.uspGetAllEmployeesTest', 'P' ) IS NOT NULL   
    DROP PROCEDURE HumanResources.uspGetAllEmployeesTest;  
GO  
CREATE PROCEDURE HumanResources.uspGetAllEmployeesTest  
AS  
    SET NOCOUNT ON;  
    SELECT LastName, FirstName, Department  
    FROM HumanResources.vEmployeeDepartmentHistory;  
GO  
  
--Rename the stored procedure.  
USE AdventureWorks2012;  
GO  
IF OBJECT_ID ( 'HumanResources.uspGetAllEmployeesTest', 'P' ) IS NOT NULL   
    DROP PROCEDURE HumanResources.uspGetAllEmployeesTest;  
GO  
CREATE PROCEDURE HumanResources.uspEveryEmployeeTest  
AS  
    SET NOCOUNT ON;  
    SELECT LastName, FirstName, Department  
    FROM HumanResources.vEmployeeDepartmentHistory;  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="91a15-141">참고 항목</span><span class="sxs-lookup"><span data-stu-id="91a15-141">See Also</span></span>  
 <span data-ttu-id="91a15-142">[ALTER PROCEDURE&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-procedure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="91a15-142">[ALTER PROCEDURE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-procedure-transact-sql) </span></span>  
 <span data-ttu-id="91a15-143">[CREATE PROCEDURE&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-procedure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="91a15-143">[CREATE PROCEDURE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-procedure-transact-sql) </span></span>  
 <span data-ttu-id="91a15-144">[저장 프로시저 만들기](../stored-procedures/create-a-stored-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="91a15-144">[Create a Stored Procedure](../stored-procedures/create-a-stored-procedure.md) </span></span>  
 <span data-ttu-id="91a15-145">[저장 프로시저 수정](../stored-procedures/modify-a-stored-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="91a15-145">[Modify a Stored Procedure](../stored-procedures/modify-a-stored-procedure.md) </span></span>  
 <span data-ttu-id="91a15-146">[저장 프로시저 삭제](../stored-procedures/delete-a-stored-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="91a15-146">[Delete a Stored Procedure](../stored-procedures/delete-a-stored-procedure.md) </span></span>  
 <span data-ttu-id="91a15-147">[저장 프로시저의 정의 보기](view-the-definition-of-a-stored-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="91a15-147">[View the Definition of a Stored Procedure](view-the-definition-of-a-stored-procedure.md) </span></span>  
 [<span data-ttu-id="91a15-148">저장 프로시저의 종속성 보기</span><span class="sxs-lookup"><span data-stu-id="91a15-148">View the Dependencies of a Stored Procedure</span></span>](view-the-dependencies-of-a-stored-procedure.md)  
  
  
