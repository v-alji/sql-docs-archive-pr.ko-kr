---
title: 역할 조인 | Microsoft 문서
ms.custom: ''
ms.date: 07/14/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
f1_keywords:
- SQL12.SWB.DATABASEUSER.MEMBERSHIP.F1
helpviewer_keywords:
- adding a member to a role
- join a role
ms.assetid: 05c8d10d-5823-46c6-8b1a-81722da6a42b
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 58e8c071672c8c3afba8d6c424488899dcf76be7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647562"
---
# <a name="join-a-role"></a><span data-ttu-id="73434-102">역할 조인</span><span class="sxs-lookup"><span data-stu-id="73434-102">Join a Role</span></span>
  <span data-ttu-id="73434-103">이 항목에서는 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 또는 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 을 사용하여 [!INCLUDE[tsql](../../../includes/tsql-md.md)]에서 로그인 및 데이터베이스 사용자에 역할을 할당하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="73434-103">This topic describes how to assign roles to logins and database users in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span> <span data-ttu-id="73434-104">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 의 역할을 사용하면 사용 권한을 효율적으로 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73434-104">Use roles in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] to efficiently manage permissions.</span></span> <span data-ttu-id="73434-105">역할에 사용 권한을 할당하고 사용자와 로그인을 역할에 추가하거나 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="73434-105">Assign permissions to roles, and then add and remove users and logins to the roles.</span></span> <span data-ttu-id="73434-106">역할을 사용하면 각 사용자의 사용 권한을 개별적으로 유지 관리할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="73434-106">By using roles, permissions do not have to be individually maintained for each user.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="73434-107">에서는 다음과 같은 네 가지 역할 유형을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="73434-107">supports four types of roles.</span></span>  
  
-   <span data-ttu-id="73434-108">고정 서버 역할</span><span class="sxs-lookup"><span data-stu-id="73434-108">Fixed server roles</span></span>  
  
-   <span data-ttu-id="73434-109">사용자 정의 서버 역할</span><span class="sxs-lookup"><span data-stu-id="73434-109">User-defined server roles</span></span>  
  
-   <span data-ttu-id="73434-110">고정 데이터베이스 역할</span><span class="sxs-lookup"><span data-stu-id="73434-110">Fixed database roles</span></span>  
  
-   <span data-ttu-id="73434-111">사용자 정의 데이터베이스 역할</span><span class="sxs-lookup"><span data-stu-id="73434-111">User-defined database roles</span></span>  
  
 <span data-ttu-id="73434-112">고정 역할은 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]에서 자동으로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73434-112">The fixed roles are automatically available in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="73434-113">고정 역할은 일반적인 태스크를 수행하는 데 필요한 사용 권한을 가집니다.</span><span class="sxs-lookup"><span data-stu-id="73434-113">Fixed roles have the necessary permissions to accomplish common tasks.</span></span> <span data-ttu-id="73434-114">고정 역할에 대한 자세한 내용은 다음 링크를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="73434-114">For more information about fixed roles, see the following links.</span></span> <span data-ttu-id="73434-115">사용자 정의 역할은 사용자가 만들며 사용자가 선택한 사용 권한으로 사용자 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73434-115">User-defined roles are created by you, and can be customized with the permissions that you select.</span></span> <span data-ttu-id="73434-116">사용자 정의 역할에 대한 자세한 내용은 다음 링크를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="73434-116">For more information about user-defined roles, see the following links.</span></span>  
  
 <span data-ttu-id="73434-117">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="73434-117">**In This Topic**</span></span>  
  
-   <span data-ttu-id="73434-118">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="73434-118">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="73434-119">제한 사항</span><span class="sxs-lookup"><span data-stu-id="73434-119">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="73434-120">보안</span><span class="sxs-lookup"><span data-stu-id="73434-120">Security</span></span>](#Security)  
  
-   <span data-ttu-id="73434-121">**로그인 및 데이터베이스 사용자에 역할을 할당하려면:**</span><span class="sxs-lookup"><span data-stu-id="73434-121">**To assign roles to logins and database users, using:**</span></span>  
  
     [<span data-ttu-id="73434-122">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="73434-122">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="73434-123">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="73434-123">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="73434-124">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="73434-124">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="73434-125">제한 사항</span><span class="sxs-lookup"><span data-stu-id="73434-125">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="73434-126">데이터베이스 역할의 이름을 변경하더라도 역할의 ID 번호, 소유자 또는 사용 권한은 변경되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="73434-126">Changing the name of a database role does not change ID number, owner, or permissions of the role.</span></span>  
  
-   <span data-ttu-id="73434-127">데이터베이스 역할은 sys.database_role_members 및 sys.database_principals 카탈로그 뷰에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="73434-127">Database roles are visible in the sys.database_role_members and sys.database_principals catalog views.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="73434-128">보안</span><span class="sxs-lookup"><span data-stu-id="73434-128">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="73434-129">권한</span><span class="sxs-lookup"><span data-stu-id="73434-129">Permissions</span></span>  
 <span data-ttu-id="73434-130">`ALTER ANY ROLE`데이터베이스에 대 한 사용 권한, `ALTER` 역할에 대 한 사용 권한 또는 **db_securityadmin**의 멤버 자격이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="73434-130">Requires `ALTER ANY ROLE` permission on the database, `ALTER` permission on the role, or membership in **db_securityadmin**.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="73434-131">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="73434-131">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-add-a-member-to-a-fixed-server-role"></a><span data-ttu-id="73434-132">고정 서버 역할에 멤버를 추가하려면</span><span class="sxs-lookup"><span data-stu-id="73434-132">To add a member to a fixed server role</span></span>  
  
1.  <span data-ttu-id="73434-133">개체 탐색기에서 고정 서버 역할을 편집할 서버를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="73434-133">In Object Explorer, expand the server in which you want to edit a fixed server role.</span></span>  
  
2.  <span data-ttu-id="73434-134">**보안** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="73434-134">Expand the **Security** folder.</span></span>  
  
3.  <span data-ttu-id="73434-135">**서버 역할** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="73434-135">Expand the **Server Roles** folder</span></span>  
  
4.  <span data-ttu-id="73434-136">편집할 역할을 마우스 오른쪽 단추로 클릭한 다음 **속성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="73434-136">Right-click the role you want to edit and select **Properties**.</span></span>  
  
5.  <span data-ttu-id="73434-137">**서버 역할 속성-**_Server_role_name_ 대화 상자의 **멤버** 페이지에서 **추가**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="73434-137">In the **Server Role Properties -**_server_role_name_ dialog box, on the **Members** page, click **Add**.</span></span>  
  
6.  <span data-ttu-id="73434-138">**서버 로그인 또는 역할 선택** 대화 상자의 **선택할 개체 이름을 입력하십시오. (예)** 에 이 서버 역할에 추가할 로그인 또는 서버 역할을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="73434-138">In the **Select Server Login or Role** dialog box, under **Enter the object names to select (examples)**, enter the login or server role to add to this server role.</span></span> <span data-ttu-id="73434-139">또는 **찾아보기…** 를 클릭하고 **개체 찾아보기** 대화 상자에서 사용 가능한 모든 개체를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="73434-139">Alternately, click **Browse...** and select any or all of the available objects in the **Browse for Objects** dialog box.</span></span> <span data-ttu-id="73434-140">**확인** 을 클릭 하 여 **서버 역할 속성-**_server_role_name_ 대화 상자로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="73434-140">Click **OK** to return to the **Server Role Properties -**_server_role_name_ dialog box.</span></span>  
  
7.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
#### <a name="to-add-a-member-to-a-user-defined-database-role"></a><span data-ttu-id="73434-141">사용자 정의 데이터베이스 역할에 멤버를 추가하려면</span><span class="sxs-lookup"><span data-stu-id="73434-141">To add a member to a user-defined database role</span></span>  
  
1.  <span data-ttu-id="73434-142">개체 탐색기에서 사용자 정의 데이터베이스 역할을 편집할 서버를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="73434-142">In Object Explorer, expand the server in which you want to edit a user-defined database role.</span></span>  
  
2.  <span data-ttu-id="73434-143">**데이터베이스** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="73434-143">Expand the **Databases** folder.</span></span>  
  
3.  <span data-ttu-id="73434-144">사용자 정의 데이터베이스 역할을 편집할 데이터베이스 서버를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="73434-144">Expand the database in which you want to edit a user-defined database role.</span></span>  
  
4.  <span data-ttu-id="73434-145">**보안** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="73434-145">Expand the **Security** folder.</span></span>  
  
5.  <span data-ttu-id="73434-146">**역할** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="73434-146">Expand the **Roles** folder.</span></span>  
  
6.  <span data-ttu-id="73434-147">**서버 역할** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="73434-147">Expand the **Server Roles** folder.</span></span>  
  
7.  <span data-ttu-id="73434-148">편집할 역할을 마우스 오른쪽 단추로 클릭한 다음 **속성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="73434-148">Right-click the role you want to edit and select **Properties**.</span></span>  
  
8.  <span data-ttu-id="73434-149">**데이터베이스 역할 속성-**_Database_role_name_ 대화 상자의 **일반** 페이지에서 **추가**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="73434-149">In the **Database Role Properties -**_database_role_name_ dialog box, in the **General** page, click **Add**.</span></span>  
  
9. <span data-ttu-id="73434-150">**데이터베이스 사용자 또는 역할 선택** 대화 상자의 **선택할 개체 이름을 입력하십시오. (예)** 에 이 데이터베이스 역할에 추가할 로그인 또는 데이터베이스 역할을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="73434-150">In the **Select Database User or Role** dialog box, under **Enter the object names to select (examples)**, enter the login or database role to add to this database role.</span></span> <span data-ttu-id="73434-151">또는 **찾아보기…** 를 클릭하고 **개체 찾아보기** 대화 상자에서 사용 가능한 모든 개체를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="73434-151">Alternately, click **Browse...** and select any or all of the available objects in the **Browse for Objects** dialog box.</span></span> <span data-ttu-id="73434-152">**확인** 을 클릭 하 여 **데이터베이스 역할 속성-**_database_role_name_ 대화 상자로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="73434-152">Click **OK** to return to the **Database Role Properties -**_database_role_name_ dialog box.</span></span>  
  
10. [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="73434-153">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="73434-153">Using Transact-SQL</span></span>  
  
#### <a name="to-add-a-member-to-a-fixed-server-role"></a><span data-ttu-id="73434-154">고정 서버 역할에 멤버를 추가하려면</span><span class="sxs-lookup"><span data-stu-id="73434-154">To add a member to a fixed server role</span></span>  
  
1.  <span data-ttu-id="73434-155">**개체 탐색기**에서 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="73434-155">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="73434-156">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="73434-156">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="73434-157">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="73434-157">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    ALTER SERVER ROLE diskadmin ADD MEMBER [Domain\Juan] ;  
    GO  
    ```  
  
 <span data-ttu-id="73434-158">자세한 내용은 [ALTER ROLE&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-role-transact-sql)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="73434-158">For more information, see [ALTER ROLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-role-transact-sql).</span></span>  
  
#### <a name="to-add-a-member-to-a-user-defined-database-role"></a><span data-ttu-id="73434-159">사용자 정의 데이터베이스 역할에 멤버를 추가하려면</span><span class="sxs-lookup"><span data-stu-id="73434-159">To add a member to a user-defined database role</span></span>  
  
1.  <span data-ttu-id="73434-160">**개체 탐색기**에서 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="73434-160">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="73434-161">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="73434-161">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="73434-162">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="73434-162">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    ALTER ROLE Marketing ADD MEMBER [Domain\Juan] ;  
    GO  
    ```  
  
 <span data-ttu-id="73434-163">자세한 내용은 [sp_addrolemember&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addrolemember-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="73434-163">For more information, see [sp_addrolemember &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addrolemember-transact-sql).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73434-164">참고 항목</span><span class="sxs-lookup"><span data-stu-id="73434-164">See Also</span></span>  
 <span data-ttu-id="73434-165">[서버 수준 역할](server-level-roles.md) </span><span class="sxs-lookup"><span data-stu-id="73434-165">[Server-Level Roles](server-level-roles.md) </span></span>  
 <span data-ttu-id="73434-166">[데이터베이스 수준 역할](../authentication-access/database-level-roles.md) </span><span class="sxs-lookup"><span data-stu-id="73434-166">[Database-Level Roles](../authentication-access/database-level-roles.md) </span></span>  
 [<span data-ttu-id="73434-167">애플리케이션 역할</span><span class="sxs-lookup"><span data-stu-id="73434-167">Application Roles</span></span>](../authentication-access/application-roles.md)  
  
  
