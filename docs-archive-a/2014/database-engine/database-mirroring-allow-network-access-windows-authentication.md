---
title: 데이터베이스 미러링 끝점에 대 한 네트워크 액세스
description: SQL Server에 대 한 데이터베이스 미러링 끝점에 대 한 windows authenticatino 네트워크 액세스를 허용 하는 방법에 대해 알아봅니다.
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Windows authentication [SQL Server]
- database mirroring [SQL Server], security
ms.assetid: 28c8fec5-5feb-4c84-8d72-f2bd1ae3b40d
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 0d1d8786d128ef2cc99fe571e33f89c4c4e7699c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653508"
---
# <a name="allow-network-access-to-a-database-mirroring-endpoint-using-windows-authentication-sql-server"></a><span data-ttu-id="e7bf6-103">Windows 인증을 사용하여 데이터베이스 미러링 엔드포인트에 대한 네트워크 액세스 허용(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="e7bf6-103">Allow Network Access to a Database Mirroring Endpoint Using Windows Authentication (SQL Server)</span></span>
  <span data-ttu-id="e7bf6-104">Windows 인증을 사용하여 두 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 인스턴스의 데이터베이스 미러링 엔드포인트를 연결하려면 다음과 같은 조건에서 로그인 계정의 수동 구성이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="e7bf6-104">Using Windows Authentication for connecting the database mirroring endpoints of two instances of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] requires manual configuration of login accounts under the following conditions:</span></span>  
  
-   <span data-ttu-id="e7bf6-105">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 인스턴스가 동일 도메인 또는 신뢰할 수 있는 도메인에서 다른 도메인 계정을 사용하여 서비스로 실행될 경우 각 계정의 로그인을 각 원격 서버 인스턴스에서 **마스터** 로 만들어야 하며, 해당 로그인에는 해당 엔드포인트에 대한 CONNECT 권한이 부여되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e7bf6-105">If the instances of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] run as services under different domain accounts (in the same or trusted domains), the login of each account must be created in **master** on each of the remote server instances and that login must be granted CONNECT permissions on the endpoint.</span></span>  
  
-   <span data-ttu-id="e7bf6-106">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 인스턴스가 네트워크 서비스 계정으로 실행될 경우 각 호스트 컴퓨터 계정(*DomainName***\\***ComputerName$* )의 로그인은 각 원격 서버 인스턴스에서 **마스터**로 만들어야 하며, 해당 로그인에는 해당 엔드포인트에 대한 CONNECT 권한이 부여되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e7bf6-106">If the instances of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] run as the Network Service account, the login of the each host computer account (*DomainName***\\***ComputerName$*) must be created in **master** on each of the remote server instances and that login must be granted CONNECT permissions on the endpoint.</span></span> <span data-ttu-id="e7bf6-107">네트워크 서비스 계정을 사용하여 서버 인스턴스를 실행할 경우 호스트 컴퓨터의 도메인 계정을 사용하여 인증이 수행되기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="e7bf6-107">This is because a server instance running under the Network Service account authenticates using the domain account of the host computer.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e7bf6-108">서버 인스턴스마다 엔드포인트가 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="e7bf6-108">Ensure that an endpoint exists for each of the server instances.</span></span> <span data-ttu-id="e7bf6-109">자세한 내용은 [Windows 인증에 대한 데이터베이스 미러링 엔드포인트 만들기&#40;Transact-SQL&#41;](database-mirroring/create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e7bf6-109">For more information, see [Create a Database Mirroring Endpoint for Windows Authentication &#40;Transact-SQL&#41;](database-mirroring/create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md).</span></span>  
  
### <a name="to-configure-logins-for-windows-authentication"></a><span data-ttu-id="e7bf6-110">Windows 인증에 대한 로그인을 구성하려면</span><span class="sxs-lookup"><span data-stu-id="e7bf6-110">To configure logins for Windows Authentication</span></span>  
  
1.  <span data-ttu-id="e7bf6-111">각 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]인스턴스의 사용자 계정에 대해 다른 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]인스턴스에 로그인을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e7bf6-111">For the user account of each instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], create a login on the other instances of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="e7bf6-112">FROM WINDOWS 절을 사용하여 [CREATE LOGIN](/sql/t-sql/statements/create-login-transact-sql) 문을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="e7bf6-112">Use a [CREATE LOGIN](/sql/t-sql/statements/create-login-transact-sql) statement with the FROM WINDOWS clause.</span></span>  
  
     <span data-ttu-id="e7bf6-113">자세한 내용은 [로그인 만들기](../relational-databases/security/authentication-access/create-a-login.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e7bf6-113">For more information, see [Create a Login](../relational-databases/security/authentication-access/create-a-login.md).</span></span>  
  
2.  <span data-ttu-id="e7bf6-114">또한 로그인 사용자가 엔드포인트에 액세스할 수 있도록 하려면 [GRANT](/sql/t-sql/statements/grant-transact-sql) 문을 사용하여 로그인에 엔드포인트에 대한 연결 권한을 부여합니다.</span><span class="sxs-lookup"><span data-stu-id="e7bf6-114">Also, to ensure that the login user has access to the endpoint, use the [GRANT](/sql/t-sql/statements/grant-transact-sql) statement to grant connect permissions on the endpoint to the login.</span></span> <span data-ttu-id="e7bf6-115">사용자가 관리자인 경우 엔드포인트에 대한 연결 권한을 부여할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e7bf6-115">Note that granting connect permissions to the endpoint is unnecessary if the user is an Administrator.</span></span>  
  
     <span data-ttu-id="e7bf6-116">자세한 내용은 [Grant a Permission to a Principal](../relational-databases/security/authentication-access/grant-a-permission-to-a-principal.md)을(를) 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e7bf6-116">For more information, see [Grant a Permission to a Principal](../relational-databases/security/authentication-access/grant-a-permission-to-a-principal.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e7bf6-117">예제</span><span class="sxs-lookup"><span data-stu-id="e7bf6-117">Example</span></span>  
 <span data-ttu-id="e7bf6-118">다음 [!INCLUDE[tsql](../includes/tsql-md.md)] 예에서는 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 도메인에 속하는 `Otheruser` 사용자 계정에 대해 `Adomain`로그인을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e7bf6-118">The following [!INCLUDE[tsql](../includes/tsql-md.md)] example creates a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] login for a user account named `Otheruser` that belongs to a domain called `Adomain`.</span></span> <span data-ttu-id="e7bf6-119">그런 다음 `Mirroring_Endpoint`라는 미리 작성된 데이터베이스 미러링 엔드포인트에 연결할 수 있는 권한을 이 사용자에게 부여합니다.</span><span class="sxs-lookup"><span data-stu-id="e7bf6-119">The example then grants this user connect permissions to a pre-existing database mirroring endpoint named `Mirroring_Endpoint`.</span></span>  
  
```  
USE master;  
GO  
CREATE LOGIN [Adomain\Otheruser] FROM WINDOWS;  
GO  
GRANT CONNECT on ENDPOINT::Mirroring_Endpoint TO [Adomain\Otheruser];  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="e7bf6-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e7bf6-120">See Also</span></span>  
 <span data-ttu-id="e7bf6-121">[AlwaysOn 가용성 그룹 &#40;SQL Server 개요&#41;](availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="e7bf6-121">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="e7bf6-122">[데이터베이스 미러링&#40;SQL Server&#41;](database-mirroring/database-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="e7bf6-122">[Database Mirroring &#40;SQL Server&#41;](database-mirroring/database-mirroring-sql-server.md) </span></span>  
 <span data-ttu-id="e7bf6-123">[데이터베이스 미러링 및 AlwaysOn 가용성 그룹 &#40;SQL Server에 대 한 전송 보안&#41;](database-mirroring/transport-security-database-mirroring-always-on-availability.md) </span><span class="sxs-lookup"><span data-stu-id="e7bf6-123">[Transport Security for Database Mirroring and AlwaysOn Availability Groups &#40;SQL Server&#41;](database-mirroring/transport-security-database-mirroring-always-on-availability.md) </span></span>  
 [<span data-ttu-id="e7bf6-124">데이터베이스 미러링 엔드포인트&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="e7bf6-124">The Database Mirroring Endpoint &#40;SQL Server&#41;</span></span>](database-mirroring/the-database-mirroring-endpoint-sql-server.md)  
  
  
