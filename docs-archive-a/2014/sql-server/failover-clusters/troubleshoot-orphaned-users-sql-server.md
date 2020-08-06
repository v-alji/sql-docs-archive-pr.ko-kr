---
title: 분리된 사용자 문제 해결(SQL Server) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- orphaned users [SQL Server]
- logins [SQL Server], orphaned users
- troubleshooting [SQL Server], user accounts
- user accounts [SQL Server], orphaned users
- failover [SQL Server], managing metadata
- database mirroring [SQL Server], metadata
- users [SQL Server], orphaned
ms.assetid: 11eefa97-a31f-4359-ba5b-e92328224133
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 5df714d818949b921ff2236e50d58913eab0e0db
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650575"
---
# <a name="troubleshoot-orphaned-users-sql-server"></a><span data-ttu-id="c235a-102">분리된 사용자 문제 해결(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="c235a-102">Troubleshoot Orphaned Users (SQL Server)</span></span>
  <span data-ttu-id="c235a-103">Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에 로그인하려면 유효한 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 로그인이 사용자에게 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c235a-103">To log into an instance of Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], a principal must have a valid [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login.</span></span> <span data-ttu-id="c235a-104">이 로그인은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에 대한 사용자 연결이 허용되는지 여부를 확인하는 인증 프로세스에서 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="c235a-104">This login is used in the authentication process that verifies whether the principal is allowed to connect to the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="c235a-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]서버 인스턴스의 로그인은 **sys. server_principals** 카탈로그 뷰와 **sys.sys로그인** 호환성 보기에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c235a-105">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] logins on a server instance are visible in the **sys.server_principals** catalog view and the **sys.syslogins** compatibility view.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="c235a-106">로그인은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 로그인에 매핑된 데이터베이스 사용자를 사용하여 개별 데이터베이스에 액세스합니다.</span><span class="sxs-lookup"><span data-stu-id="c235a-106">logins access individual databases using a database user that is mapped to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login.</span></span> <span data-ttu-id="c235a-107">이 규칙에는 두 가지 예외가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c235a-107">There are two exceptions to this rule:</span></span>  
  
-   <span data-ttu-id="c235a-108">게스트 계정</span><span class="sxs-lookup"><span data-stu-id="c235a-108">The guest account.</span></span>  
  
     <span data-ttu-id="c235a-109">게스트 계정은 데이터베이스에서 사용 가능한 경우 데이터베이스 사용자에 매핑되지 않은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 로그인이 게스트 사용자로 데이터베이스에 액세스할 수 있도록 하는 계정입니다.</span><span class="sxs-lookup"><span data-stu-id="c235a-109">This is an account that, when enabled in the database, enables [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] logins that are not mapped to a database user to enter the database as the guest user.</span></span>  
  
-   <span data-ttu-id="c235a-110">Microsoft Windows 그룹 멤버 자격</span><span class="sxs-lookup"><span data-stu-id="c235a-110">Microsoft Windows group memberships.</span></span>  
  
     <span data-ttu-id="c235a-111">Windows 사용자로부터 생성된 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 로그인은 해당 Windows 사용자가 Windows 그룹의 멤버인 동시에 데이터베이스의 사용자인 경우 데이터베이스에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c235a-111">A [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login created from a Windows user can enter a database if the Windows user is a member of a Windows group that is also a user in the database.</span></span>  
  
 <span data-ttu-id="c235a-112">데이터베이스 사용자로의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 로그인 매핑에 대한 정보는 데이터베이스 내에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="c235a-112">Information about the mapping of a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login to a database user is stored within the database.</span></span> <span data-ttu-id="c235a-113">데이터베이스 사용자 이름과 해당 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 로그인의 SID가 여기에 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="c235a-113">It includes the name of the database user and the SID of the corresponding [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login.</span></span> <span data-ttu-id="c235a-114">이 데이터베이스 사용자의 사용 권한은 데이터베이스에서 권한 부여에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="c235a-114">The permissions of this database user are used for authorization in the database.</span></span>  
  
 <span data-ttu-id="c235a-115">해당 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 로그인이 서버 인스턴스에서 정의되지 않았거나 잘못 정의되어 있는 데이터베이스 사용자는 이 인스턴스에 로그인할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c235a-115">A database user for which the corresponding [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login is undefined or is incorrectly defined on a server instance cannot log in to the instance.</span></span> <span data-ttu-id="c235a-116">이러한 사용자는 해당 서버 인스턴스에 있는 데이터베이스의 *분리된 사용자* 라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="c235a-116">Such a user is said to be an *orphaned user* of the database on that server instance.</span></span> <span data-ttu-id="c235a-117">데이터베이스 사용자는 해당 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 로그인이 삭제되면 분리될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c235a-117">A database user can become orphaned if the corresponding [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login is dropped.</span></span> <span data-ttu-id="c235a-118">데이터베이스가 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 다른 인스턴스에 복원되거나 연결된 후에도 데이터베이스 사용자가 분리될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c235a-118">Also, a database user can become orphaned after a database is restored or attached to a different instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="c235a-119">데이터베이스 사용자가 새 서버 인스턴스에 없는 SID로 매핑되는 경우 사용자가 분리될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c235a-119">Orphaning can happen if the database user is mapped to a SID that is not present in the new server instance.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c235a-120">로그인은 해당 데이터베이스 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서 **게스트** 를 사용 하도록 설정 하지 않은 경우 해당 데이터베이스 사용자가 없는 데이터베이스에 액세스할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c235a-120">A [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login cannot access a database in which it lacks a corresponding database user unless **guest** is enabled in that database.</span></span> <span data-ttu-id="c235a-121">데이터베이스 사용자 계정을 만드는 방법에 대 한 자세한 내용은 [CREATE user &#40;transact-sql&#41;](/sql/t-sql/statements/create-user-transact-sql)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="c235a-121">For information about creating a database user account, see [CREATE USER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-user-transact-sql).</span></span>  
  
## <a name="to-detect-orphaned-users"></a><span data-ttu-id="c235a-122">분리된 사용자를 검색하려면</span><span class="sxs-lookup"><span data-stu-id="c235a-122">To Detect Orphaned Users</span></span>  
 <span data-ttu-id="c235a-123">분리된 사용자를 검색하려면 다음 Transact-SQL 문을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="c235a-123">To detect orphaned users, execute the following Transact-SQL statements:</span></span>  
  
```  
USE <database_name>;  
GO;   
sp_change_users_login @Action='Report';  
GO;  
```  
  
 <span data-ttu-id="c235a-124">현재 데이터베이스에 있으며 어떤 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 로그인에도 연결되지 않은 사용자와 이에 해당되는 SID(보안 ID)가 나열됩니다.</span><span class="sxs-lookup"><span data-stu-id="c235a-124">The output lists the users and corresponding security identifiers (SID) in the current database that are not linked to any [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login.</span></span> <span data-ttu-id="c235a-125">자세한 내용은 [sp_change_users_login &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-change-users-login-transact-sql)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="c235a-125">For more information, see [sp_change_users_login &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-change-users-login-transact-sql).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c235a-126">**sp_change_users_login** 는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Windows에서 만든 로그인과 함께 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c235a-126">**sp_change_users_login** cannot be used with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] logins that are created from Windows.</span></span>  
  
## <a name="to-resolve-an-orphaned-user"></a><span data-ttu-id="c235a-127">분리된 사용자를 확인하려면</span><span class="sxs-lookup"><span data-stu-id="c235a-127">To Resolve an Orphaned User</span></span>  
 <span data-ttu-id="c235a-128">분리된 사용자를 확인하려면 다음 절차를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="c235a-128">To resolve an orphaned user, use the following procedure:</span></span>  
  
1.  <span data-ttu-id="c235a-129">다음 명령은 *<login_name>* 에 지정 된 서버 로그인 계정을 *<database_user>* 에 지정 된 데이터베이스 사용자와 다시 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="c235a-129">The following command relinks the server login account specified by *<login_name>* with the database user specified by *<database_user>*.</span></span>  
  
    ```  
    USE <database_name>;  
    GO  
    sp_change_users_login @Action='update_one', @UserNamePattern='<database_user>', @LoginName='<login_name>';  
    GO  
  
    ```  
  
     <span data-ttu-id="c235a-130">자세한 내용은 [sp_change_users_login &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-change-users-login-transact-sql)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="c235a-130">For more information, see [sp_change_users_login &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-change-users-login-transact-sql).</span></span>  
  
2.  <span data-ttu-id="c235a-131">앞 단계에서 코드를 실행한 다음 사용자는 데이터베이스에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c235a-131">After you run the code in the preceding step, the user can access the database.</span></span> <span data-ttu-id="c235a-132">그러면 사용자가 **sp_password** 저장 프로시저를 사용 하 여 *<login_name>* 로그인 계정의 암호를 다음과 같이 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c235a-132">The user then can alter the password of the *<login_name>* login account by using the **sp_password** stored procedure, as follows:</span></span>  
  
    ```  
    USE master   
    GO  
    sp_password @old=NULL, @new='password', @loginame='<login_name>';  
    GO  
    ```  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="c235a-133">ALTER ANY LOGIN 사용 권한이 있는 로그인으로만 다른 사용자의 로그인 암호를 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c235a-133">Only logins with the ALTER ANY LOGIN permission can change the password of another user's login.</span></span> <span data-ttu-id="c235a-134">그러나 **sysadmin** 역할의 멤버만 **sysadmin** 역할 멤버의 암호를 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c235a-134">However, only members of the **sysadmin** role can modify passwords of **sysadmin** role members.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="c235a-135">Windows 계정에는 **sp_password** 를 사용할 수 없습니다 [!INCLUDE[msCoName](../../includes/msconame-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="c235a-135">**sp_password** cannot be used for [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows accounts.</span></span> <span data-ttu-id="c235a-136">Windows 네트워크 계정을 통해 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에 연결하는 사용자는 Windows에 의해 인증되므로 암호는 Windows에서만 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c235a-136">Users connecting to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] through their Windows network account are authenticated by Windows; therefore, their passwords can only be changed in Windows.</span></span>  
  
     <span data-ttu-id="c235a-137">자세한 내용은 [sp_password &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-password-transact-sql)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="c235a-137">For more information, see [sp_password &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-password-transact-sql).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c235a-138">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c235a-138">See Also</span></span>  
 <span data-ttu-id="c235a-139">[CREATE USER&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-user-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c235a-139">[CREATE USER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-user-transact-sql) </span></span>  
 <span data-ttu-id="c235a-140">[CREATE LOGIN &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-login-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c235a-140">[CREATE LOGIN &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-login-transact-sql) </span></span>  
 <span data-ttu-id="c235a-141">[Transact-sql&#41;sp_change_users_login &#40;](/sql/relational-databases/system-stored-procedures/sp-change-users-login-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c235a-141">[sp_change_users_login &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-change-users-login-transact-sql) </span></span>  
 <span data-ttu-id="c235a-142">[sp_addlogin&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addlogin-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c235a-142">[sp_addlogin &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addlogin-transact-sql) </span></span>  
 <span data-ttu-id="c235a-143">[Transact-sql&#41;sp_grantlogin &#40;](/sql/relational-databases/system-stored-procedures/sp-grantlogin-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c235a-143">[sp_grantlogin &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-grantlogin-transact-sql) </span></span>  
 <span data-ttu-id="c235a-144">[Transact-sql&#41;sp_password &#40;](/sql/relational-databases/system-stored-procedures/sp-password-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c235a-144">[sp_password &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-password-transact-sql) </span></span>  
 <span data-ttu-id="c235a-145">[Transact-sql&#41;사용자 &#40;sys.sys](/sql/relational-databases/system-compatibility-views/sys-sysusers-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c235a-145">[sys.sysusers &#40;Transact-SQL&#41;](/sql/relational-databases/system-compatibility-views/sys-sysusers-transact-sql) </span></span>  
 [<span data-ttu-id="c235a-146">Transact-sql&#41;&#40;로그인sys.sys</span><span class="sxs-lookup"><span data-stu-id="c235a-146">sys.syslogins &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-compatibility-views/sys-syslogins-transact-sql)  
  
  
