---
title: 서버 역할 만들기 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
f1_keywords:
- sql12.swb.serverrole.members.f1
- SQL12.SWB.SERVERROLE.GENERAL.F1
- sql12.swb.serverrole.memberships.f1
helpviewer_keywords:
- SERVER ROLE, creating
ms.assetid: 74f19992-8082-4ed7-92a1-04fe676ee82d
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 45c3d5bb9c9c7fdae9abe18ab3cb808cae4c1fa1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653781"
---
# <a name="create-a-server-role"></a><span data-ttu-id="45e0e-102">서버 역할 만들기</span><span class="sxs-lookup"><span data-stu-id="45e0e-102">Create a Server Role</span></span>
  <span data-ttu-id="45e0e-103">이 항목에서는 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 또는 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 을 사용하여 [!INCLUDE[tsql](../../../includes/tsql-md.md)]에서 새 서버 역할을 만드는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="45e0e-103">This topic describes how to create a new server role in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="45e0e-104">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="45e0e-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="45e0e-105">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="45e0e-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="45e0e-106">제한 사항</span><span class="sxs-lookup"><span data-stu-id="45e0e-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="45e0e-107">보안</span><span class="sxs-lookup"><span data-stu-id="45e0e-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="45e0e-108">**다음을 사용하여 새 서버 역할을 만듭니다.**</span><span class="sxs-lookup"><span data-stu-id="45e0e-108">**To create a new server role, using:**</span></span>  
  
     [<span data-ttu-id="45e0e-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="45e0e-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="45e0e-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="45e0e-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="45e0e-111">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="45e0e-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="45e0e-112">제한 사항</span><span class="sxs-lookup"><span data-stu-id="45e0e-112">Limitations and Restrictions</span></span>  
 <span data-ttu-id="45e0e-113">데이터베이스 수준 보안 개체에서는 서버 역할에 사용 권한을 부여할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="45e0e-113">Server roles cannot be granted permission on database-level securables.</span></span> <span data-ttu-id="45e0e-114">데이터베이스 역할을 만들려면 [CREATE ROLE&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-role-transact-sql)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="45e0e-114">To create database roles, see [CREATE ROLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-role-transact-sql).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="45e0e-115">보안</span><span class="sxs-lookup"><span data-stu-id="45e0e-115">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="45e0e-116">권한</span><span class="sxs-lookup"><span data-stu-id="45e0e-116">Permissions</span></span>  
  
-   <span data-ttu-id="45e0e-117">CREATE SERVER ROLE 권한 또는 sysadmin 고정 서버 역할의 멤버 자격이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="45e0e-117">Requires CREATE SERVER ROLE permission or membership in the sysadmin fixed server role.</span></span>  
  
-   <span data-ttu-id="45e0e-118">로그인의 경우 *server_principal* 에 대한 IMPERSONATE이 필요하고 *server_principal*로 사용되는 서버 역할의 경우 ALTER 권한이 필요합니다. 또는 server_principal로 사용되는 Windows 그룹의 멤버 자격이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="45e0e-118">Also requires IMPERSONATE on the *server_principal* for logins, ALTER permission for server roles used as the *server_principal*, or membership in a Windows group that is used as the server_principal.</span></span>  
  
-   <span data-ttu-id="45e0e-119">AUTHORIZATION 옵션을 사용하여 서버 역할 소유권을 할당할 경우 다음 사용 권한도 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="45e0e-119">When you use the AUTHORIZATION option to assign server role ownership, the following permissions are also required:</span></span>  
  
    -   <span data-ttu-id="45e0e-120">다른 로그인에 서버 역할의 소유권을 할당하려면 해당 로그인에 대한 IMPERSONATE 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="45e0e-120">To assign ownership of a server role to another login, requires IMPERSONATE permission on that login.</span></span>  
  
    -   <span data-ttu-id="45e0e-121">다른 서버 역할에 서버 역할의 소유권을 할당하려면 받는 서버 역할의 멤버 자격이나 해당 서버 역할에 대한 ALTER 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="45e0e-121">To assign ownership of a server role to another server role, requires membership in the recipient server role or ALTER permission on that server role.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="45e0e-122">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="45e0e-122">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-create-a-new-server-role"></a><span data-ttu-id="45e0e-123">새 서버 역할을 만들려면</span><span class="sxs-lookup"><span data-stu-id="45e0e-123">To create a new server role</span></span>  
  
1.  <span data-ttu-id="45e0e-124">개체 탐색기에서 새 서버 역할을 만들 서버를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="45e0e-124">In Object Explorer, expand the server where you want to create the new server role.</span></span>  
  
2.  <span data-ttu-id="45e0e-125">**보안** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="45e0e-125">Expand the **Security** folder.</span></span>  
  
3.  <span data-ttu-id="45e0e-126">**서버 역할** 폴더를 마우스 오른쪽 단추로 클릭하고 **새 서버 역할...** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="45e0e-126">Right-click the **Server Roles** folder and select **New Server Role...**.</span></span>  
  
4.  <span data-ttu-id="45e0e-127">**새 서버 역할-**_Server_role_name_ 대화 상자의 **일반** 페이지에서 **서버 역할 이름** 상자에 새 서버 역할의 이름을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="45e0e-127">In the **New Server Role -**_server_role_name_ dialog box, on the **General** page, enter a name for the new server role in the **Server role name** box.</span></span>  
  
5.  <span data-ttu-id="45e0e-128">**소유자** 상자에 새 역할을 소유할 서버 보안 주체의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="45e0e-128">In the **Owner** box, enter the name of the server principal that will own the new role.</span></span> <span data-ttu-id="45e0e-129">또는 줄임표 **(...)** 를 클릭하여 **서버 로그인 또는 역할 선택** 대화 상자를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="45e0e-129">Alternately, click the ellipsis **(...)** to open the **Select Server Login or Role** dialog box.</span></span>  
  
6.  <span data-ttu-id="45e0e-130">**보안 개체**에서 서버 수준 보안 개체를 하나 이상 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="45e0e-130">Under **Securables**, select one or more server-level securables.</span></span> <span data-ttu-id="45e0e-131">보안 개체를 선택하면 해당 보안 개체에 대한 사용 권한을 이 서버 역할에 부여하거나 거부할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="45e0e-131">When a securable is selected, this server role can be granted or denied permissions on that securable.</span></span>  
  
7.  <span data-ttu-id="45e0e-132">**사용 권한: 명시적** 상자에서 이 서버 역할에 선택한 보안 개체에 대한 부여 권한, 권한 부여 권한 또는 거부 권한을 부여하는 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="45e0e-132">In the **Permissions: Explicit** box, select the check box to grant, grant with grant, or deny permission to this server role for the selected securables.</span></span> <span data-ttu-id="45e0e-133">선택한 보안 개체 중 일부에 대해 사용 권한을 부여하거나 거부할 수 없는 경우 해당 사용 권한은 부분적으로 선택된 것으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="45e0e-133">If a permission cannot be granted or denied to all of the selected securables, the permission is represented as a partial select.</span></span>  
  
8.  <span data-ttu-id="45e0e-134">**멤버** 페이지에서 **추가** 단추를 사용하여 개인이나 그룹을 나타내는 로그인을 새 서버 역할에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="45e0e-134">On the **Members** page, use the **Add** button to add logins that represent individuals or groups to the new server role.</span></span>  
  
9. <span data-ttu-id="45e0e-135">사용자 정의 서버 역할은 다른 서버 역할의 멤버가 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="45e0e-135">A user-defined server role can be a member of another server role.</span></span> <span data-ttu-id="45e0e-136">**멤버 자격** 페이지에서 현재 사용자 정의 서버 역할을 선택한 서버 역할의 멤버로 설정하는 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="45e0e-136">On the **Memberships** page, select a check box to make the current user-defined server role a member of a selected server role.</span></span>  
  
10. [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="45e0e-137">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="45e0e-137">Using Transact-SQL</span></span>  
  
#### <a name="to-create-a-new-server-role"></a><span data-ttu-id="45e0e-138">새 서버 역할을 만들려면</span><span class="sxs-lookup"><span data-stu-id="45e0e-138">To create a new server role</span></span>  
  
1.  <span data-ttu-id="45e0e-139">**개체 탐색기**에서 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="45e0e-139">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="45e0e-140">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="45e0e-140">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="45e0e-141">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="45e0e-141">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    --Creates the server role auditors that is owned the securityadmin fixed server role.  
    USE master;  
    CREATE SERVER ROLE auditors AUTHORIZATION securityadmin;  
    GO  
    ```  
  
 <span data-ttu-id="45e0e-142">자세한 내용은 [CREATE SERVER ROLE&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-server-role-transact-sql)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="45e0e-142">For more information, see [CREATE SERVER ROLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-server-role-transact-sql).</span></span>  
  
  
