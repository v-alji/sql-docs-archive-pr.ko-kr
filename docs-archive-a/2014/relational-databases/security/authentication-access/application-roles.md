---
title: 애플리케이션 역할 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- application roles [SQL Server], about application roles
- principals [SQL Server], application roles
- credentials [SQL Server], roles
- application roles [SQL Server]
- roles [SQL Server], application
- permissions [SQL Server], roles
- users [SQL Server], application roles
- authentication [SQL Server], roles
- groups [SQL Server], roles
ms.assetid: dca18b8a-ca03-4b7f-9a46-8474d5b66f76
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: f2fcc7b1e333bb42a00675da5bb9fd559d1c34f1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647566"
---
# <a name="application-roles"></a><span data-ttu-id="e174b-102">애플리케이션 역할</span><span class="sxs-lookup"><span data-stu-id="e174b-102">Application Roles</span></span>
  <span data-ttu-id="e174b-103">애플리케이션 역할은 애플리케이션이 사용자와 같은 자체 사용 권한으로 실행할 수 있도록 설정하는 데이터베이스 보안 주체입니다.</span><span class="sxs-lookup"><span data-stu-id="e174b-103">An application role is a database principal that enables an application to run with its own, user-like permissions.</span></span> <span data-ttu-id="e174b-104">애플리케이션 역할을 사용하면 특정 데이터에 대한 액세스를 특정 애플리케이션을 통해 연결하는 사용자에게만 허용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e174b-104">You can use application roles to enable access to specific data to only those users who connect through a particular application.</span></span> <span data-ttu-id="e174b-105">데이터베이스 역할과는 달리 애플리케이션 역할에는 멤버가 없으며 기본적으로 비활성화됩니다.</span><span class="sxs-lookup"><span data-stu-id="e174b-105">Unlike database roles, application roles contain no members and are inactive by default.</span></span> <span data-ttu-id="e174b-106">애플리케이션 역할은 두 인증 모드에서 모두 작동하며</span><span class="sxs-lookup"><span data-stu-id="e174b-106">Application roles work with both authentication modes.</span></span> <span data-ttu-id="e174b-107">**sp_setapprole**을 사용하여 활성화되고 암호가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="e174b-107">Application roles are enabled by using **sp_setapprole**, which requires a password.</span></span> <span data-ttu-id="e174b-108">애플리케이션 역할은 데이터베이스 수준의 보안 주체이기 때문에 다른 데이터베이스에서 **guest**에 부여한 사용 권한을 통해서만 해당 데이터베이스에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e174b-108">Because application roles are a database-level principal, they can access other databases only through permissions granted in those databases to **guest**.</span></span> <span data-ttu-id="e174b-109">따라서 다른 데이터베이스의 애플리케이션 역할은 **guest** 가 해제된 데이터베이스에 액세스할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e174b-109">Therefore, any database in which **guest** has been disabled will be inaccessible to application roles in other databases.</span></span>  
  
 <span data-ttu-id="e174b-110">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]에서 애플리케이션 역할은 서버 수준의 보안 주체와 연결되어 있지 않으므로 서버 수준 메타데이터에 액세스할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e174b-110">In [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], application roles cannot access server-level metadata because they are not associated with a server-level principal.</span></span> <span data-ttu-id="e174b-111">이 제한을 해제하여 애플리케이션 역할이 서버 수준 메타데이터에 액세스할 수 있도록 하려면 전역 플래그 4616을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="e174b-111">To disable this restriction and thereby allow application roles to access server-level metadata, set the global flag 4616.</span></span> <span data-ttu-id="e174b-112">자세한 내용은 [추적 플래그&#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql) 및 [DBCC TRACEON&#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-traceon-transact-sql)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e174b-112">For more information, see [Trace Flags &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql) and [DBCC TRACEON &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-traceon-transact-sql).</span></span>  
  
## <a name="connecting-with-an-application-role"></a><span data-ttu-id="e174b-113">애플리케이션 역할에 연결</span><span class="sxs-lookup"><span data-stu-id="e174b-113">Connecting with an Application Role</span></span>  
 <span data-ttu-id="e174b-114">다음은 애플리케이션 역할이 보안 컨텍스트를 전환하는 프로세스를 구성하는 단계입니다.</span><span class="sxs-lookup"><span data-stu-id="e174b-114">The following steps make up the process by which an application role switches security contexts:</span></span>  
  
1.  <span data-ttu-id="e174b-115">사용자가 클라이언트 애플리케이션을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="e174b-115">A user executes a client application.</span></span>  
  
2.  <span data-ttu-id="e174b-116">클라이언트 애플리케이션이 이 사용자로 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="e174b-116">The client application connects to an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] as the user.</span></span>  
  
3.  <span data-ttu-id="e174b-117">그런 다음 애플리케이션이 해당 애플리케이션에만 알려진 암호를 사용하여 **sp_setapprole** 저장 프로시저를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="e174b-117">The application then executes the **sp_setapprole** stored procedure with a password known only to the application.</span></span>  
  
4.  <span data-ttu-id="e174b-118">애플리케이션 역할 이름과 암호가 올바르면 애플리케이션 역할이 활성화됩니다.</span><span class="sxs-lookup"><span data-stu-id="e174b-118">If the application role name and password are valid, the application role is enabled.</span></span>  
  
5.  <span data-ttu-id="e174b-119">그러면 연결에서 사용자의 사용 권한이 삭제되고 애플리케이션 역할의 사용 권한이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="e174b-119">At this point the connection loses the permissions of the user and assumes the permissions of the application role.</span></span>  
  
 <span data-ttu-id="e174b-120">애플리케이션 역할을 통해 얻은 사용 권한은 연결 기간 동안 유효한 상태로 남습니다.</span><span class="sxs-lookup"><span data-stu-id="e174b-120">The permissions acquired through the application role remain in effect for the duration of the connection.</span></span>  
  
 <span data-ttu-id="e174b-121">이전 버전의 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]에서 애플리케이션 역할을 시작한 후 사용자가 자신의 원래 보안 컨텍스트를 다시 얻으려면 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]에 대한 연결을 끊고 다시 연결해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e174b-121">In earlier versions of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], the only way for a user to reacquire its original security context after starting an application role is to disconnect and reconnect to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="e174b-122">[!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]부터는 **sp_setapprole** 에서 쿠키를 만들 수 있는 옵션을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="e174b-122">Beginning with [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], **sp_setapprole** has an option that creates a cookie.</span></span> <span data-ttu-id="e174b-123">이 쿠키에는 애플리케이션 역할을 활성화하기 전 컨텍스트 정보가 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e174b-123">The cookie contains context information before the application role is enabled.</span></span> <span data-ttu-id="e174b-124">이 쿠키를 **sp_unsetapprole** 에서 사용하여 원래 컨텍스트로 세션을 되돌릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e174b-124">The cookie can be used by **sp_unsetapprole** to revert the session to its original context.</span></span> <span data-ttu-id="e174b-125">이 새 옵션에 대한 자세한 내용과 예를 보려면 [sp_setapprole&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-setapprole-transact-sql)에 부여한 사용 권한을 통해서만 해당 데이터베이스에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e174b-125">For information about this new option and an example, see [sp_setapprole &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-setapprole-transact-sql).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="e174b-126">ODBC **encrypt** 옵션은 **SqlClient**에서 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e174b-126">The ODBC **encrypt** option is not supported by **SqlClient**.</span></span> <span data-ttu-id="e174b-127">네트워크로 기밀 정보를 전송하려면 SSL(Secure Sockets Layer) 또는 IPsec을 사용하여 채널을 암호화합니다.</span><span class="sxs-lookup"><span data-stu-id="e174b-127">When you are transmitting confidential information over a network, use Secure Sockets Layer (SSL) or IPsec to encrypt the channel.</span></span> <span data-ttu-id="e174b-128">클라이언트 애플리케이션의 자격 증명을 유지해야 하는 경우에는 crypto API 함수를 사용하여 자격 증명을 암호화하십시오.</span><span class="sxs-lookup"><span data-stu-id="e174b-128">If you must persist credentials in the client application, encrypt the credentials by using the crypto API functions.</span></span> <span data-ttu-id="e174b-129">[!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] 이상 버전에서 *password* 매개 변수는 단방향 해시로 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="e174b-129">In [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] and later versions, the parameter *password* is stored as a one-way hash.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="e174b-130">관련 작업</span><span class="sxs-lookup"><span data-stu-id="e174b-130">Related Tasks</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e174b-131">애플리케이션 역할 만들기</span><span class="sxs-lookup"><span data-stu-id="e174b-131">Create an application role.</span></span>|<span data-ttu-id="e174b-132">[애플리케이션 역할 만들기](create-an-application-role.md) 및 [CREATE APPLICATION ROLE&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-application-role-transact-sql)</span><span class="sxs-lookup"><span data-stu-id="e174b-132">[Create an Application Role](create-an-application-role.md) and [CREATE APPLICATION ROLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-application-role-transact-sql)</span></span>|  
|<span data-ttu-id="e174b-133">애플리케이션 역할 변경</span><span class="sxs-lookup"><span data-stu-id="e174b-133">Alter an application role.</span></span>|[<span data-ttu-id="e174b-134">ALTER APPLICATION ROLE&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="e174b-134">ALTER APPLICATION ROLE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-application-role-transact-sql)|  
|<span data-ttu-id="e174b-135">애플리케이션 역할 삭제</span><span class="sxs-lookup"><span data-stu-id="e174b-135">Delete an application role.</span></span>|[<span data-ttu-id="e174b-136">DROP APPLICATION ROLE&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="e174b-136">DROP APPLICATION ROLE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/drop-application-role-transact-sql)|  
|<span data-ttu-id="e174b-137">애플리케이션 역할 사용</span><span class="sxs-lookup"><span data-stu-id="e174b-137">Using an application role.</span></span>|[<span data-ttu-id="e174b-138">sp_setapprole&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="e174b-138">sp_setapprole &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-setapprole-transact-sql)|  
  
## <a name="see-also"></a><span data-ttu-id="e174b-139">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e174b-139">See Also</span></span>  
 [<span data-ttu-id="e174b-140">SQL Server 보안 설정</span><span class="sxs-lookup"><span data-stu-id="e174b-140">Securing SQL Server</span></span>](../securing-sql-server.md)  
  
  
