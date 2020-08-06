---
title: 저장 프로시저에 대한 사용 권한 부여 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.technology: stored-procedures
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- stored procedures [SQL Server], permissions
ms.assetid: a7d15816-a788-4099-ad91-dc4b26618299
author: stevestein
ms.author: sstein
ms.openlocfilehash: 23ea130b9d2033128adc99413c053d66936e3ccc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651565"
---
# <a name="grant-permissions-on-a-stored-procedure"></a><span data-ttu-id="e31a6-102">저장 프로시저에 대한 사용 권한 부여</span><span class="sxs-lookup"><span data-stu-id="e31a6-102">Grant Permissions on a Stored Procedure</span></span>
  <span data-ttu-id="e31a6-103">이 항목에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 에서 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 또는 [!INCLUDE[tsql](../../includes/tsql-md.md)]을 사용하여 저장 프로시저에 대한 사용 권한을 부여하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="e31a6-103">This topic describes how to grant permissions on a stored procedure in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="e31a6-104">데이터베이스의 기존 사용자, 데이터베이스 역할 또는 애플리케이션 역할에 사용 권한을 부여할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e31a6-104">Permissions can be granted to an existing user, database role, or application role in the database.</span></span>  
  
 <span data-ttu-id="e31a6-105">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="e31a6-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="e31a6-106">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="e31a6-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="e31a6-107">제한 사항</span><span class="sxs-lookup"><span data-stu-id="e31a6-107">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="e31a6-108">보안</span><span class="sxs-lookup"><span data-stu-id="e31a6-108">Security</span></span>](#Security)  
  
-   <span data-ttu-id="e31a6-109">**저장 프로시저에 대한 사용 권한을 부여하려면:**</span><span class="sxs-lookup"><span data-stu-id="e31a6-109">**To grant permissions on a stored procedure, using:**</span></span>  
  
     [<span data-ttu-id="e31a6-110">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="e31a6-110">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="e31a6-111">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="e31a6-111">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="e31a6-112">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="e31a6-112">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="e31a6-113">제한 사항</span><span class="sxs-lookup"><span data-stu-id="e31a6-113">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="e31a6-114">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 를 사용하여 시스템 프로시저나 시스템 함수에 대한 사용 권한을 부여할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e31a6-114">You cannot use [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to grant permissions on system procedures or system functions.</span></span> <span data-ttu-id="e31a6-115">이 경우 [GRANT Object Permissions](/sql/t-sql/statements/grant-object-permissions-transact-sql) 를 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="e31a6-115">Use [GRANT Object Permissions](/sql/t-sql/statements/grant-object-permissions-transact-sql) instead.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="e31a6-116">보안</span><span class="sxs-lookup"><span data-stu-id="e31a6-116">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="e31a6-117">권한</span><span class="sxs-lookup"><span data-stu-id="e31a6-117">Permissions</span></span>  
 <span data-ttu-id="e31a6-118">사용 권한을 부여한 사용자 또는 AS 옵션으로 지정한 보안 주체에게 GRANT OPTION을 통한 사용 권한이 있거나 부여할 사용 권한을 포함하는 상위 사용 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e31a6-118">The grantor (or the principal specified with the AS option) must have either the permission itself with GRANT OPTION, or a higher permission that implies the permission being granted.</span></span> <span data-ttu-id="e31a6-119">프로시저가 속한 스키마에 대한 ALTER 권한 또는 프로시저에 대한 CONTROL 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="e31a6-119">Requires ALTER permission on the schema to which the procedure belongs, or CONTROL permission on the procedure.</span></span> <span data-ttu-id="e31a6-120">자세한 내용은 [GRANT 개체 사용 권한&#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-object-permissions-transact-sql)을 사용하여 저장 프로시저에 대한 사용 권한을 부여하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="e31a6-120">For more information, see [GRANT Object Permissions &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-object-permissions-transact-sql).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="e31a6-121">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="e31a6-121">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-grant-permissions-on-a-stored-procedure"></a><span data-ttu-id="e31a6-122">저장 프로시저에 대한 사용 권한을 부여하려면</span><span class="sxs-lookup"><span data-stu-id="e31a6-122">To grant permissions on a stored procedure</span></span>  
  
1.  <span data-ttu-id="e31a6-123">개체 탐색기에서 [!INCLUDE[ssDE](../../../includes/ssde-md.md)] 의 인스턴스에 연결한 다음 해당 인스턴스를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="e31a6-123">In Object Explorer, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)] and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="e31a6-124">**데이터베이스**를 확장하고 해당 프로시저가 속한 데이터베이스를 확장한 다음 **프로그래밍 기능**을 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="e31a6-124">Expand **Databases**, expand the database in which the procedure belongs, and then expand **Programmability**.</span></span>  
  
3.  <span data-ttu-id="e31a6-125">**저장 프로시저**를 확장하고 사용 권한을 부여할 프로시저를 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e31a6-125">Expand **Stored Procedures**, right-click the procedure to grant permissions on, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="e31a6-126">**저장 프로시저 속성**에서 **사용 권한** 페이지를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e31a6-126">From **Stored Procedure Properties**, select the **Permissions** page.</span></span>  
  
5.  <span data-ttu-id="e31a6-127">사용자, 데이터베이스 역할 또는 애플리케이션 역할에 사용 권한을 부여하려면 **검색**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e31a6-127">To grant permissions to a user, database role, or application role, click **Search**.</span></span>  
  
6.  <span data-ttu-id="e31a6-128">**사용자 또는 역할 선택**에서 **개체 유형** 을 클릭하여 원하는 사용자 및 역할을 추가하거나 지웁니다.</span><span class="sxs-lookup"><span data-stu-id="e31a6-128">In **Select Users or Roles**, click **Object Types** to add or clear the users and roles you want.</span></span>  
  
7.  <span data-ttu-id="e31a6-129">**찾아보기** 를 클릭하여 사용자 또는 역할의 목록을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="e31a6-129">Click **Browse** to display the list of users or roles.</span></span> <span data-ttu-id="e31a6-130">사용 권한을 부여할 사용자 또는 역할을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e31a6-130">Select the users or roles to whom permissions should be granted.</span></span>  
  
8.  <span data-ttu-id="e31a6-131">**명시적 사용 권한** 표에서 지정된 사용자 또는 역할에 부여할 사용 권한을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e31a6-131">In the **Explicit Permissions** grid, select the permissions to grant to the specified user or role.</span></span> <span data-ttu-id="e31a6-132">사용 권한에 대한 설명은 [사용 권한&#40;데이터베이스 엔진&#41;](../security/permissions-database-engine.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e31a6-132">For a description of the permissions, see [Permissions &#40;Database Engine&#41;](../security/permissions-database-engine.md).</span></span>  
  
 <span data-ttu-id="e31a6-133">**허용** 을 선택하면 지정된 사용 권한이 피부여자에게 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="e31a6-133">Selecting **Grant** indicates the grantee will be given the specified permission.</span></span> <span data-ttu-id="e31a6-134">**허용 권한 소유** 를 선택하면 피부여자가 지정된 사용 권한을 다른 보안 주체에 부여할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e31a6-134">Selecting **Grant With** indicates that the grantee will also be able to grant the specified permission to other principals.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="e31a6-135">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="e31a6-135">Using Transact-SQL</span></span>  
  
#### <a name="to-grant-permissions-on-a-stored-procedure"></a><span data-ttu-id="e31a6-136">저장 프로시저에 대한 사용 권한을 부여하려면</span><span class="sxs-lookup"><span data-stu-id="e31a6-136">To grant permissions on a stored procedure</span></span>  
  
1.  <span data-ttu-id="e31a6-137">[!INCLUDE[ssDE](../../../includes/ssde-md.md)]에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="e31a6-137">Connect to the [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="e31a6-138">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e31a6-138">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="e31a6-139">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e31a6-139">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="e31a6-140">이 예에서는 `EXECUTE` 이라는 애플리케이션 역할에 대해 저장 프로시저 `HumanResources.uspUpdateEmployeeHireInfo` 에 대한 `Recruiting11`권한을 부여합니다.</span><span class="sxs-lookup"><span data-stu-id="e31a6-140">This example grants `EXECUTE` permission on the stored procedure `HumanResources.uspUpdateEmployeeHireInfo` to an application role named `Recruiting11`.</span></span>  
  
```sql  
USE AdventureWorks2012;   
GRANT EXECUTE ON OBJECT::HumanResources.uspUpdateEmployeeHireInfo  
    TO Recruiting11;  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="e31a6-141">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e31a6-141">See Also</span></span>  
 <span data-ttu-id="e31a6-142">[sys.fn_builtin_permissions&#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/sys-fn-builtin-permissions-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="e31a6-142">[sys.fn_builtin_permissions &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/sys-fn-builtin-permissions-transact-sql) </span></span>  
 <span data-ttu-id="e31a6-143">[GRANT 개체 사용 권한&#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-object-permissions-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="e31a6-143">[GRANT Object Permissions &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-object-permissions-transact-sql) </span></span>  
 <span data-ttu-id="e31a6-144">[저장 프로시저 만들기](../stored-procedures/create-a-stored-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="e31a6-144">[Create a Stored Procedure](../stored-procedures/create-a-stored-procedure.md) </span></span>  
 <span data-ttu-id="e31a6-145">[저장 프로시저 수정](modify-a-stored-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="e31a6-145">[Modify a Stored Procedure](modify-a-stored-procedure.md) </span></span>  
 <span data-ttu-id="e31a6-146">[저장 프로시저 삭제](../stored-procedures/delete-a-stored-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="e31a6-146">[Delete a Stored Procedure](../stored-procedures/delete-a-stored-procedure.md) </span></span>  
 [<span data-ttu-id="e31a6-147">저장 프로시저 이름 바꾸기</span><span class="sxs-lookup"><span data-stu-id="e31a6-147">Rename a Stored Procedure</span></span>](rename-a-stored-procedure.md)  
  
  
