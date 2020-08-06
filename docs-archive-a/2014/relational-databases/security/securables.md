---
title: 보안 개체 | Microsoft 문서
ms.custom: ''
ms.date: 10/14/2015
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
f1_keywords:
- sql12.swb.roleproperties.selectobject.f1
helpviewer_keywords:
- securables [SQL Server]
- schemas [SQL Server], securables
- database securables [SQL Server]
- hierarchies [SQL Server], securables
- server securables [SQL Server]
ms.assetid: bfa748f0-70b0-453c-870a-04b7b205b9ff
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: ff2aaba72e2e5489694d31b35e594622c099acab
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730339"
---
# <a name="securables"></a><span data-ttu-id="09f83-102">보안 개체</span><span class="sxs-lookup"><span data-stu-id="09f83-102">Securables</span></span>
  <span data-ttu-id="09f83-103">보안 개체는 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 인증 시스템이 액세스를 조정하는 리소스입니다.</span><span class="sxs-lookup"><span data-stu-id="09f83-103">Securables are the resources to which the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] authorization system regulates access.</span></span> <span data-ttu-id="09f83-104">예를 들어, 테이블은 보안 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="09f83-104">For example, a table is a securable.</span></span> <span data-ttu-id="09f83-105">스스로 보호할 수 있는 "범위"라는 중첩된 계층을 만들면 일부 보안 개체를 다른 보안 개체에 포함시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="09f83-105">Some securables can be contained within others, creating nested hierarchies called "scopes" that can themselves be secured.</span></span> <span data-ttu-id="09f83-106">보안 개체 범위는 **서버**, **데이터베이스**및 **스키마**입니다.</span><span class="sxs-lookup"><span data-stu-id="09f83-106">The securable scopes are **server**, **database**, and **schema**.</span></span>  
  
## <a name="securable-scope-server"></a><span data-ttu-id="09f83-107">보안 개체 범위: 서버</span><span class="sxs-lookup"><span data-stu-id="09f83-107">Securable scope: Server</span></span>  
 <span data-ttu-id="09f83-108">**서버** 보안 개체 범위는 다음 보안 개체를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="09f83-108">The **server** securable scope contains the following securables:</span></span>  
  
-   <span data-ttu-id="09f83-109">가용성 그룹</span><span class="sxs-lookup"><span data-stu-id="09f83-109">Availability group</span></span>  
  
-   <span data-ttu-id="09f83-110">엔드포인트</span><span class="sxs-lookup"><span data-stu-id="09f83-110">Endpoint</span></span>  
  
-   <span data-ttu-id="09f83-111">로그인</span><span class="sxs-lookup"><span data-stu-id="09f83-111">Login</span></span>  
  
-   <span data-ttu-id="09f83-112">서버 역할</span><span class="sxs-lookup"><span data-stu-id="09f83-112">Server role</span></span>  
  
-   <span data-ttu-id="09f83-113">데이터베이스</span><span class="sxs-lookup"><span data-stu-id="09f83-113">Database</span></span>  
  
## <a name="securable-scope-database"></a><span data-ttu-id="09f83-114">보안 개체 범위: 데이터베이스</span><span class="sxs-lookup"><span data-stu-id="09f83-114">Securable scope: Database</span></span>  
 <span data-ttu-id="09f83-115">**데이터베이스** 보안 개체 범위는 다음 보안 개체를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="09f83-115">The **database** securable scope contains the following securables:</span></span>  
  
-   <span data-ttu-id="09f83-116">애플리케이션 역할</span><span class="sxs-lookup"><span data-stu-id="09f83-116">Application role</span></span>  
  
-   <span data-ttu-id="09f83-117">어셈블리</span><span class="sxs-lookup"><span data-stu-id="09f83-117">Assembly</span></span>  
  
-   <span data-ttu-id="09f83-118">비대칭 키</span><span class="sxs-lookup"><span data-stu-id="09f83-118">Asymmetric key</span></span>  
  
-   <span data-ttu-id="09f83-119">인증서</span><span class="sxs-lookup"><span data-stu-id="09f83-119">Certificate</span></span>  
  
-   <span data-ttu-id="09f83-120">계약</span><span class="sxs-lookup"><span data-stu-id="09f83-120">Contract</span></span>  
  
-   <span data-ttu-id="09f83-121">전체 텍스트 카탈로그</span><span class="sxs-lookup"><span data-stu-id="09f83-121">Fulltext catalog</span></span>  
  
-   <span data-ttu-id="09f83-122">전체 텍스트 중지 목록</span><span class="sxs-lookup"><span data-stu-id="09f83-122">Fulltext stoplist</span></span>  
  
-   <span data-ttu-id="09f83-123">메시지 유형</span><span class="sxs-lookup"><span data-stu-id="09f83-123">Message type</span></span>  
  
-   <span data-ttu-id="09f83-124">원격 서비스 바인딩</span><span class="sxs-lookup"><span data-stu-id="09f83-124">Remote Service Binding</span></span>  
  
-   <span data-ttu-id="09f83-125">(데이터베이스) 역할</span><span class="sxs-lookup"><span data-stu-id="09f83-125">(Database) Role</span></span>  
  
-   <span data-ttu-id="09f83-126">라우팅</span><span class="sxs-lookup"><span data-stu-id="09f83-126">Route</span></span>  
  
-   <span data-ttu-id="09f83-127">스키마</span><span class="sxs-lookup"><span data-stu-id="09f83-127">Schema</span></span>  
  
-   <span data-ttu-id="09f83-128">검색 속성 목록</span><span class="sxs-lookup"><span data-stu-id="09f83-128">Search property list</span></span>  
  
-   <span data-ttu-id="09f83-129">서비스</span><span class="sxs-lookup"><span data-stu-id="09f83-129">Service</span></span>  
  
-   <span data-ttu-id="09f83-130">대칭 키</span><span class="sxs-lookup"><span data-stu-id="09f83-130">Symmetric key</span></span>  
  
-   <span data-ttu-id="09f83-131">사용자</span><span class="sxs-lookup"><span data-stu-id="09f83-131">User</span></span>  
  
## <a name="securable-scope-schema"></a><span data-ttu-id="09f83-132">보안 개체 범위: 스키마</span><span class="sxs-lookup"><span data-stu-id="09f83-132">Securable scope: Schema</span></span>  
 <span data-ttu-id="09f83-133">**스키마** 보안 개체 범위는 다음 보안 개체를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="09f83-133">The **schema** securable scope contains the following securables:</span></span>  
  
-   <span data-ttu-id="09f83-134">Type</span><span class="sxs-lookup"><span data-stu-id="09f83-134">Type</span></span>  
  
-   <span data-ttu-id="09f83-135">XML 스키마 컬렉션</span><span class="sxs-lookup"><span data-stu-id="09f83-135">XML schema collection</span></span>  
  
-   <span data-ttu-id="09f83-136">개체 - 개체 클래스 멤버는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="09f83-136">Object - The object class has the following members:</span></span>  
  
    -   <span data-ttu-id="09f83-137">집계</span><span class="sxs-lookup"><span data-stu-id="09f83-137">Aggregate</span></span>  
  
    -   <span data-ttu-id="09f83-138">함수</span><span class="sxs-lookup"><span data-stu-id="09f83-138">Function</span></span>  
  
    -   <span data-ttu-id="09f83-139">절차</span><span class="sxs-lookup"><span data-stu-id="09f83-139">Procedure</span></span>  
  
    -   <span data-ttu-id="09f83-140">큐</span><span class="sxs-lookup"><span data-stu-id="09f83-140">Queue</span></span>  
  
    -   <span data-ttu-id="09f83-141">동의어</span><span class="sxs-lookup"><span data-stu-id="09f83-141">Synonym</span></span>  
  
    -   <span data-ttu-id="09f83-142">테이블</span><span class="sxs-lookup"><span data-stu-id="09f83-142">Table</span></span>  
  
    -   <span data-ttu-id="09f83-143">보기</span><span class="sxs-lookup"><span data-stu-id="09f83-143">View</span></span>  
  
## <a name="controlling-access-to-a-securable"></a><span data-ttu-id="09f83-144">보안 개체에 대한 액세스 제어</span><span class="sxs-lookup"><span data-stu-id="09f83-144">Controlling Access to a Securable</span></span>  
 <span data-ttu-id="09f83-145">보안 개체에 대한 사용 권한을 받는 엔터티를 주체라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="09f83-145">The entity that receives permission to a securable is called a principal.</span></span> <span data-ttu-id="09f83-146">가장 일반적인 보안 주체는 로그인 및 데이터베이스 사용자입니다.</span><span class="sxs-lookup"><span data-stu-id="09f83-146">The most common principals are logins and database users.</span></span> <span data-ttu-id="09f83-147">사용 권한을 부여 또는 거부하거나, 액세스 권한이 있는 역할에 로그인 및 사용자를 추가하여 보안 개체에 대한 액세스를 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="09f83-147">Access to securables is controlled by granting or denying permissions, or by adding logins and user to roles which have access.</span></span> <span data-ttu-id="09f83-148">사용 권한을 제어하는 방법은 [GRANT&#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-transact-sql), [REVOKE&#40;Transact-SQL&#41;](/sql/t-sql/statements/revoke-transact-sql), [DENY&#40;Transact-SQL&#41;](/sql/t-sql/statements/deny-transact-sql), [sp_addrolemember&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addrolemember-transact-sql) 및 [sp_droprolemember&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-droprolemember-transact-sql)입니다.</span><span class="sxs-lookup"><span data-stu-id="09f83-148">For information about controlling permissions, see [GRANT &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-transact-sql), [REVOKE &#40;Transact-SQL&#41;](/sql/t-sql/statements/revoke-transact-sql), [DENY &#40;Transact-SQL&#41;](/sql/t-sql/statements/deny-transact-sql), [sp_addrolemember &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addrolemember-transact-sql), and [sp_droprolemember &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-droprolemember-transact-sql).</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="09f83-149">설치 시 시스템 개체에 부여되는 기본 사용 권한은 발생할 수 있는 위협이 있는지 신중하게 평가되며 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 설치 보안 강화의 일환으로 변경할 필요는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="09f83-149">The default permissions that are granted to system objects at the time of setup are carefully evaluated against possible threats and need not be altered as part of hardening the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] installation.</span></span> <span data-ttu-id="09f83-150">시스템 개체에 대한 사용 권한을 변경하면 기능이 제한 또는 중단될 수 있으며 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 설치가 지원되지 않는 상태가 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="09f83-150">Any changes to the permissions on the system objects could limit or break the functionality and could potentially leave your [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] installation in an unsupported state.</span></span>  
  
## <a name="related-content"></a><span data-ttu-id="09f83-151">관련 내용</span><span class="sxs-lookup"><span data-stu-id="09f83-151">Related Content</span></span>  
 [<span data-ttu-id="09f83-152">SQL Server 보안 설정</span><span class="sxs-lookup"><span data-stu-id="09f83-152">Securing SQL Server</span></span>](securing-sql-server.md)  
  
 [<span data-ttu-id="09f83-153">sys.database_principals&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="09f83-153">sys.database_principals &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-database-principals-transact-sql)  
  
 [<span data-ttu-id="09f83-154">sys.database_role_members&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="09f83-154">sys.database_role_members &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-database-role-members-transact-sql)  
  
 [<span data-ttu-id="09f83-155">sys.server_principals&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="09f83-155">sys.server_principals &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-server-principals-transact-sql)  
  
 [<span data-ttu-id="09f83-156">sys.server_role_members&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="09f83-156">sys.server_role_members &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-server-role-members-transact-sql)  
  
 [<span data-ttu-id="09f83-157">sys.sql_logins&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="09f83-157">sys.sql_logins &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-sql-logins-transact-sql)  
  
  
