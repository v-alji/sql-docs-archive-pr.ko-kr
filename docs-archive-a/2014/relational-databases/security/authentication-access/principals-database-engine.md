---
title: 보안 주체(데이터베이스 엔진) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
f1_keywords:
- sql12.swb.roleproperties.selectroll.f1
- sql12.swb.databaseuser.permissions.user.f1--May use common.permissions
helpviewer_keywords:
- certificates [SQL Server], principals
- roles [SQL Server], principals
- permissions [SQL Server], principals
- '##MS_SQLAuthenticatorCertificate##'
- principals [SQL Server]
- '##MS_SQLResourceSigningCertificate##'
- groups [SQL Server], principals
- '##MS_AgentSigningCertificate##'
- authentication [SQL Server], principals
- schemas [SQL Server], principals
- principals [SQL Server], about principals
- security [SQL Server], principals
- users [SQL Server], principals
- '##MS_SQLReplicationSigningCertificate##'
ms.assetid: 3f7adbf7-6e40-4396-a8ca-71cbb843b5c2
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 808c8516b3ed9e95ea4c724736461cb00923a7fb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660977"
---
# <a name="principals-database-engine"></a><span data-ttu-id="5a31d-102">보안 주체(데이터베이스 엔진)</span><span class="sxs-lookup"><span data-stu-id="5a31d-102">Principals (Database Engine)</span></span>
  <span data-ttu-id="5a31d-103">*보안 주체* 는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 리소스를 요청할 수 있는 엔터티입니다.</span><span class="sxs-lookup"><span data-stu-id="5a31d-103">*Principals* are entities that can request [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] resources.</span></span> <span data-ttu-id="5a31d-104">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 권한 부여 모델의 다른 구성 요소와 같이 보안 주체는 계층으로 정렬될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5a31d-104">Like other components of the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] authorization model, principals can be arranged in a hierarchy.</span></span> <span data-ttu-id="5a31d-105">보안 주체의 영향 범위는 보안 주체의 정의 범위인 Windows, 서버 및 데이터베이스와 보안 주체가 분해 불가능하거나 컬렉션인지 여부에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="5a31d-105">The scope of influence of a principal depends on the scope of the definition of the principal: Windows, server, database; and whether the principal is indivisible or a collection.</span></span> <span data-ttu-id="5a31d-106">분해 불가능한 보안 주체의 예로는 Windows 로그인을 들 수 있으며 Windows 그룹은 컬렉션인 보안 주체입니다.</span><span class="sxs-lookup"><span data-stu-id="5a31d-106">A Windows Login is an example of an indivisible principal, and a Windows Group is an example of a principal that is a collection.</span></span> <span data-ttu-id="5a31d-107">모든 보안 주체에는 SID(보안 식별자)가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5a31d-107">Every principal has a security identifier (SID).</span></span>  
  
 <span data-ttu-id="5a31d-108">**Windows 수준의 보안 주체**</span><span class="sxs-lookup"><span data-stu-id="5a31d-108">**Windows-level principals**</span></span>  
  
-   <span data-ttu-id="5a31d-109">Windows 도메인 로그인</span><span class="sxs-lookup"><span data-stu-id="5a31d-109">Windows Domain Login</span></span>  
  
-   <span data-ttu-id="5a31d-110">Windows 로컬 로그인</span><span class="sxs-lookup"><span data-stu-id="5a31d-110">Windows Local Login</span></span>  
  
 <span data-ttu-id="5a31d-111">**SQL Server** - **수준** **보안 주체**</span><span class="sxs-lookup"><span data-stu-id="5a31d-111">**SQL Server**-**level** **principals**</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="5a31d-112">로그인</span><span class="sxs-lookup"><span data-stu-id="5a31d-112">Login</span></span>  
  
-   <span data-ttu-id="5a31d-113">서버 역할</span><span class="sxs-lookup"><span data-stu-id="5a31d-113">Server Role</span></span>  
  
 <span data-ttu-id="5a31d-114">**데이터베이스 수준의 보안 주체**</span><span class="sxs-lookup"><span data-stu-id="5a31d-114">**Database-level principals**</span></span>  
  
-   <span data-ttu-id="5a31d-115">데이터베이스 사용자</span><span class="sxs-lookup"><span data-stu-id="5a31d-115">Database User</span></span>  
  
-   <span data-ttu-id="5a31d-116">데이터베이스 역할</span><span class="sxs-lookup"><span data-stu-id="5a31d-116">Database Role</span></span>  
  
-   <span data-ttu-id="5a31d-117">애플리케이션 역할</span><span class="sxs-lookup"><span data-stu-id="5a31d-117">Application Role</span></span>  
  
## <a name="the-sql-server-sa-login"></a><span data-ttu-id="5a31d-118">SQL Server sa 로그인</span><span class="sxs-lookup"><span data-stu-id="5a31d-118">The SQL Server sa Login</span></span>  
 <span data-ttu-id="5a31d-119">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sa 로그인은 서버 수준 보안 주체로서</span><span class="sxs-lookup"><span data-stu-id="5a31d-119">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sa log in is a server-level principal.</span></span> <span data-ttu-id="5a31d-120">인스턴스를 설치하면 기본적으로 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="5a31d-120">By default, it is created when an instance is installed.</span></span> <span data-ttu-id="5a31d-121">[!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]부터는 sa의 기본 데이터베이스가 master입니다.</span><span class="sxs-lookup"><span data-stu-id="5a31d-121">Beginning in [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], the default database of sa is master.</span></span> <span data-ttu-id="5a31d-122">이 동작은 이전 버전의 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]에서 변경되었습니다.</span><span class="sxs-lookup"><span data-stu-id="5a31d-122">This is a change of behavior from earlier versions of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="public-database-role"></a><span data-ttu-id="5a31d-123">public 데이터베이스 역할</span><span class="sxs-lookup"><span data-stu-id="5a31d-123">public Database Role</span></span>  
 <span data-ttu-id="5a31d-124">모든 데이터베이스 사용자는 public 데이터베이스 역할에 속합니다.</span><span class="sxs-lookup"><span data-stu-id="5a31d-124">Every database user belongs to the public database role.</span></span> <span data-ttu-id="5a31d-125">사용자에게 보안 개체에 대한 특정 사용 권한이 부여되지 않았거나 거부된 경우 사용자는 해당 보안 개체에 대해 public으로 부여된 사용 권한을 상속 받습니다.</span><span class="sxs-lookup"><span data-stu-id="5a31d-125">When a user has not been granted or denied specific permissions on a securable, the user inherits the permissions granted to public on that securable.</span></span>  
  
## <a name="information_schema-and-sys"></a><span data-ttu-id="5a31d-126">INFORMATION_SCHEMA 및 sys</span><span class="sxs-lookup"><span data-stu-id="5a31d-126">INFORMATION_SCHEMA and sys</span></span>  
 <span data-ttu-id="5a31d-127">모든 데이터베이스에는 카탈로그 뷰에 사용자로 표시되는 두 엔터티인 INFORMATION_SCHEMA와 sys가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="5a31d-127">Every database includes two entities that appear as users in catalog views: INFORMATION_SCHEMA and sys.</span></span> <span data-ttu-id="5a31d-128">이러한 엔터티는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]에 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="5a31d-128">These entities are required by [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="5a31d-129">엔터티는 보안 주체가 아니며 수정 또는 삭제할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5a31d-129">They are not principals, and they cannot be modified or dropped.</span></span>  
  
## <a name="certificate-based-sql-server-logins"></a><span data-ttu-id="5a31d-130">인증서 기반 SQL Server 로그인</span><span class="sxs-lookup"><span data-stu-id="5a31d-130">Certificate-based SQL Server Logins</span></span>  
 <span data-ttu-id="5a31d-131">이름이 이중 해시 표시(##)로 묶인 서버 보안 주체는 내부 시스템 용도로만 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="5a31d-131">Server principals with names enclosed by double hash marks (##) are for internal system use only.</span></span> <span data-ttu-id="5a31d-132">다음 보안 주체는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 를 설치할 때 인증서에서 생성되며 삭제하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5a31d-132">The following principals are created from certificates when [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] is installed, and should not be deleted.</span></span>  
  
-   <span data-ttu-id="5a31d-133">\##MS_SQLResourceSigningCertificate##</span><span class="sxs-lookup"><span data-stu-id="5a31d-133">\##MS_SQLResourceSigningCertificate##</span></span>  
  
-   <span data-ttu-id="5a31d-134">\##MS_SQLReplicationSigningCertificate##</span><span class="sxs-lookup"><span data-stu-id="5a31d-134">\##MS_SQLReplicationSigningCertificate##</span></span>  
  
-   <span data-ttu-id="5a31d-135">\##MS_SQLAuthenticatorCertificate##</span><span class="sxs-lookup"><span data-stu-id="5a31d-135">\##MS_SQLAuthenticatorCertificate##</span></span>  
  
-   <span data-ttu-id="5a31d-136">\##MS_AgentSigningCertificate##</span><span class="sxs-lookup"><span data-stu-id="5a31d-136">\##MS_AgentSigningCertificate##</span></span>  
  
-   <span data-ttu-id="5a31d-137">\##MS_PolicyEventProcessingLogin##</span><span class="sxs-lookup"><span data-stu-id="5a31d-137">\##MS_PolicyEventProcessingLogin##</span></span>  
  
-   <span data-ttu-id="5a31d-138">\##MS_PolicySigningCertificate##</span><span class="sxs-lookup"><span data-stu-id="5a31d-138">\##MS_PolicySigningCertificate##</span></span>  
  
-   <span data-ttu-id="5a31d-139">\##MS_PolicyTsqlExecutionLogin##</span><span class="sxs-lookup"><span data-stu-id="5a31d-139">\##MS_PolicyTsqlExecutionLogin##</span></span>  
  
## <a name="the-guest-user"></a><span data-ttu-id="5a31d-140">guest 사용자</span><span class="sxs-lookup"><span data-stu-id="5a31d-140">The guest User</span></span>  
 <span data-ttu-id="5a31d-141">각 데이터베이스에는 **guest**가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5a31d-141">Each database includes a **guest**.</span></span> <span data-ttu-id="5a31d-142">**guest** 사용자에게 부여된 권한은 데이터베이스에 대한 액세스 권한이 있지만 데이터베이스에 사용자 계정이 없는 사용자가 상속합니다.</span><span class="sxs-lookup"><span data-stu-id="5a31d-142">Permissions granted to the **guest** user are inherited by users who have access to the database, but who do not have a user account in the database.</span></span> <span data-ttu-id="5a31d-143">**게스트** 사용자는 삭제할 수 없지만 사용 권한을 취소 하 여 사용 하지 않도록 설정할 수 있습니다 `CONNECT` .</span><span class="sxs-lookup"><span data-stu-id="5a31d-143">The **guest** user cannot be dropped, but it can be disabled by revoking it's `CONNECT` permission.</span></span> <span data-ttu-id="5a31d-144">`CONNECT` `REVOKE CONNECT FROM GUEST` Master 또는 tempdb 이외의 데이터베이스 내에서를 실행 하 여 사용 권한을 해지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5a31d-144">The `CONNECT` permission can be revoked by executing `REVOKE CONNECT FROM GUEST` within any database other than master or tempdb.</span></span>  
  
## <a name="client-and-database-server"></a><span data-ttu-id="5a31d-145">클라이언트 및 데이터베이스 서버</span><span class="sxs-lookup"><span data-stu-id="5a31d-145">Client and Database Server</span></span>  
 <span data-ttu-id="5a31d-146">정의에 따르면 클라이언트 및 데이터베이스 서버는 보안 주체이며 보안을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5a31d-146">By definition, a client and a database server are security principals and can be secured.</span></span> <span data-ttu-id="5a31d-147">이러한 항목은 보안 네트워크 연결이 설정되기 전에 상호 인증될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5a31d-147">These entities can be mutually authenticated before a secure network connection is established.</span></span> [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]<span data-ttu-id="5a31d-148">는 클라이언트가 네트워크 인증 서비스와 상호 작용 하는 방법을 정의 하는 [Kerberos](https://go.microsoft.com/fwlink/?LinkId=100758) 인증 프로토콜을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="5a31d-148">supports the [Kerberos](https://go.microsoft.com/fwlink/?LinkId=100758) authentication protocol, which defines how clients interact with a network authentication service.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="5a31d-149">관련 작업</span><span class="sxs-lookup"><span data-stu-id="5a31d-149">Related Tasks</span></span>  
 <span data-ttu-id="5a31d-150">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 온라인 설명서 섹션에는 다음과 같은 항목이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5a31d-150">The following topics are included in this section of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Books Online:</span></span>  
  
-   [<span data-ttu-id="5a31d-151">로그인, 사용자 및 스키마 관리 방법 도움말 항목</span><span class="sxs-lookup"><span data-stu-id="5a31d-151">Managing Logins, Users, and Schemas How-to Topics</span></span>](managing-logins-users-and-schemas-how-to-topics.md)  
  
-   [<span data-ttu-id="5a31d-152">서버 수준 역할</span><span class="sxs-lookup"><span data-stu-id="5a31d-152">Server-Level Roles</span></span>](server-level-roles.md)  
  
-   [<span data-ttu-id="5a31d-153">데이터베이스 수준 역할</span><span class="sxs-lookup"><span data-stu-id="5a31d-153">Database-Level Roles</span></span>](database-level-roles.md)  
  
-   [<span data-ttu-id="5a31d-154">애플리케이션 역할</span><span class="sxs-lookup"><span data-stu-id="5a31d-154">Application Roles</span></span>](application-roles.md)  
  
## <a name="see-also"></a><span data-ttu-id="5a31d-155">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5a31d-155">See Also</span></span>  
 <span data-ttu-id="5a31d-156">[SQL Server 보안 설정](../securing-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="5a31d-156">[Securing SQL Server](../securing-sql-server.md) </span></span>  
 <span data-ttu-id="5a31d-157">[sys.database_principals&#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-principals-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="5a31d-157">[sys.database_principals &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-principals-transact-sql) </span></span>  
 <span data-ttu-id="5a31d-158">[sys.server_principals&#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-principals-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="5a31d-158">[sys.server_principals &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-principals-transact-sql) </span></span>  
 <span data-ttu-id="5a31d-159">[sys.sql_logins&#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-sql-logins-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="5a31d-159">[sys.sql_logins &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-sql-logins-transact-sql) </span></span>  
 <span data-ttu-id="5a31d-160">[sys.database_role_members&#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-role-members-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="5a31d-160">[sys.database_role_members &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-role-members-transact-sql) </span></span>  
 <span data-ttu-id="5a31d-161">[서버 수준 역할](server-level-roles.md) </span><span class="sxs-lookup"><span data-stu-id="5a31d-161">[Server-Level Roles](server-level-roles.md) </span></span>  
 [<span data-ttu-id="5a31d-162">데이터베이스 수준 역할</span><span class="sxs-lookup"><span data-stu-id="5a31d-162">Database-Level Roles</span></span>](database-level-roles.md)  
  
  
