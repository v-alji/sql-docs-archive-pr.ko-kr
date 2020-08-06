---
title: 데이터베이스 미러링 또는 AlwaysOn 가용성 그룹에 대 한 로그인 계정 설정 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- database mirroring [SQL Server], deployment
- logins [SQL Server], database mirroring
ms.assetid: e9f5287b-1325-4cda-88a6-19eaaa52a652
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: d149016dabd0239bd76eadc8655b6752afd916d9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87733052"
---
# <a name="set-up-login-accounts-for-database-mirroring-or-alwayson-availability-groups-sql-server"></a><span data-ttu-id="126e7-102">데이터베이스 미러링 또는 AlwaysOn 가용성 그룹에 대한 로그인 계정 설정(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="126e7-102">Set Up Login Accounts for Database Mirroring or AlwaysOn Availability Groups (SQL Server)</span></span>
  <span data-ttu-id="126e7-103">두 서버 인스턴스가 서로의 [데이터베이스 미러링 엔드포인트](the-database-mirroring-endpoint-sql-server.md) 포인트에 연결할 수 있으려면 각 인스턴스의 로그인 계정에 다른 인스턴스에 대한 액세스가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="126e7-103">For two server instances to connect to each other's [database mirroring endpoint](the-database-mirroring-endpoint-sql-server.md) point, the login account of each instance requires access to the other instance.</span></span> <span data-ttu-id="126e7-104">또한 각 로그인 계정에는 다른 인스턴스의 데이터베이스 미러링 엔드포인트에 대한 CONNECT 권한도 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="126e7-104">Also, each login account requires connect permission to the Database Mirroring endpoint of the other instance.</span></span>  
  
 <span data-ttu-id="126e7-105">이 요구 사항의 영향은 서버 인스턴스가 동일한 도메인 사용자 계정으로 실행되는지 여부에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="126e7-105">The impact of this requirement depends on whether the server instances run as the same domain user account:</span></span>  
  
-   <span data-ttu-id="126e7-106">서버 인스턴스가 동일한 도메인 사용자 계정으로 실행되는 경우에는 두 **master** 데이터베이스 모두에 올바른 사용자 로그인이 자동으로 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="126e7-106">If the server instances run as the same domain user account, the correct user logins exist automatically in both **master** databases.</span></span> <span data-ttu-id="126e7-107">이 경우 데이터베이스 미러링 및 AlwaysOn 가용성 그룹에 대한 보안 구성이 단순해집니다.</span><span class="sxs-lookup"><span data-stu-id="126e7-107">This simplifies the security configuration for Database Mirroring and AlwaysOn Availability Groups.</span></span>  
  
-   <span data-ttu-id="126e7-108">서버 인스턴스가 다른 사용자 계정으로 실행되는 경우 주 서버 인스턴스 또는 주 복제본을 호스팅하는 서버 인스턴스의 사용자 로그인을 미러 서버를 호스팅하는 서버 인스턴스 또는 보조 복제본을 호스팅하는 모든 서버 인스턴스에서 수동으로 재현해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="126e7-108">If the server instances run as different user accounts, user logins on the server instance that hosts the principal server or primary replica must be manually reproduced on the server instance that hosts the mirror server or on every server instance that hosts a secondary replica.</span></span> <span data-ttu-id="126e7-109">자세한 내용은 이 항목의 뒷부분에 나오는 [다른 계정에 대해 로그인 만들기](#CreateLogin) 및 [현재 권한 부여](#GrantConnect)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="126e7-109">For more information, see [Create a Login for a Different Account](#CreateLogin) and [Grant Connect Permission](#GrantConnect), later in this topic.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="126e7-110">보다 안전한 환경을 만들려면 각 서버 인스턴스에 대해 별도의 도메인 계정을 사용해 보십시오.</span><span class="sxs-lookup"><span data-stu-id="126e7-110">To create a more secure environment, consider using separate domain accounts for each server instance.</span></span>  
  
##  <a name="create-a-login-for-a-different-account"></a><a name="CreateLogin"></a><span data-ttu-id="126e7-111">다른 계정에 대 한 로그인 만들기</span><span class="sxs-lookup"><span data-stu-id="126e7-111">Create a Login for a Different Account</span></span>  
 <span data-ttu-id="126e7-112">두 서버 인스턴스가 다른 계정으로 실행되는 경우 시스템 관리자는 CREATE LOGIN [!INCLUDE[tsql](../../includes/tsql-md.md)] 문을 사용하여 서버 인스턴스마다 원격 인스턴스의 시작 서비스 계정에 대한 로그인을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="126e7-112">If two server instances run as different accounts, the system administrator must use the CREATE LOGIN [!INCLUDE[tsql](../../includes/tsql-md.md)] statement to create a login for the startup service account of the remote instance for each server instance.</span></span> <span data-ttu-id="126e7-113">자세한 내용은 [CREATE LOGIN&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-login-transact-sql)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="126e7-113">For more information, see [CREATE LOGIN &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-login-transact-sql).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="126e7-114">도메인이 아닌 계정에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]를 실행하는 경우 인증서를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="126e7-114">If you run [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] under a non-domain account, you must use certificates.</span></span> <span data-ttu-id="126e7-115">자세한 내용은 [데이터베이스 미러링 엔드포인트에 대한 인증서 사용&#40;Transact-SQL&#41;](use-certificates-for-a-database-mirroring-endpoint-transact-sql.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="126e7-115">For more information, see [Use Certificates for a Database Mirroring Endpoint &#40;Transact-SQL&#41;](use-certificates-for-a-database-mirroring-endpoint-transact-sql.md).</span></span>  
  
 <span data-ttu-id="126e7-116">예를 들어 loginA에서 실행되는 sqlA 서버 인스턴스의 경우 loginB에서 실행되는 sqlB 서버 인스턴스에 연결하려면 loginA는 sqlB에 있어야 하고 loginB는 sqlA에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="126e7-116">For example, for the server instance sqlA, which runs under loginA, to connect to the server instance sqlB, which runs under loginB, loginA must exist on sqlB, and loginB must exist on sqlA.</span></span> <span data-ttu-id="126e7-117">또한 미러링 모니터 서버 인스턴스(sqlC)가 있고 서버 인스턴스 3개가 서로 다른 도메인 계정으로 실행되는 데이터베이스 미러링 세션의 경우 다음 로그인을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="126e7-117">In addition, for a database mirroring session that includes a witness server instance (sqlC) and in which the three server instances run under different domain accounts, the following logins must be created:</span></span>  
  
|<span data-ttu-id="126e7-118">인스턴스</span><span class="sxs-lookup"><span data-stu-id="126e7-118">On instance...</span></span>|<span data-ttu-id="126e7-119">로그인을 만들고 CONNECT 권한 부여할 대상</span><span class="sxs-lookup"><span data-stu-id="126e7-119">Create logins for and grant connection permission to ...</span></span>|  
|--------------------|--------------------------------------------------------------|  
|<span data-ttu-id="126e7-120">sqlA</span><span class="sxs-lookup"><span data-stu-id="126e7-120">sqlA</span></span>|<span data-ttu-id="126e7-121">sqlB 및 sqlC</span><span class="sxs-lookup"><span data-stu-id="126e7-121">sqlB and sqlC</span></span>|  
|<span data-ttu-id="126e7-122">sqlB</span><span class="sxs-lookup"><span data-stu-id="126e7-122">sqlB</span></span>|<span data-ttu-id="126e7-123">sqlA 및 sqlC</span><span class="sxs-lookup"><span data-stu-id="126e7-123">sqlA and sqlC</span></span>|  
|<span data-ttu-id="126e7-124">sqlC</span><span class="sxs-lookup"><span data-stu-id="126e7-124">sqlC</span></span>|<span data-ttu-id="126e7-125">sqlA 및 sqlB</span><span class="sxs-lookup"><span data-stu-id="126e7-125">sqlA and sqlB</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="126e7-126">도메인 사용자 대신 컴퓨터 계정을 사용하여 네트워크 서비스 계정과 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="126e7-126">It is possible to connect with the network service account by using the machine account instead of a domain user.</span></span> <span data-ttu-id="126e7-127">컴퓨터 계정을 사용하는 경우 다른 서버 인스턴스의 사용자로 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="126e7-127">If the machine account is used, it must be added as a user on the other server instance.</span></span>  
  
##  <a name="grant-connect-permission"></a><a name="GrantConnect"></a><span data-ttu-id="126e7-128">Connect 권한 부여</span><span class="sxs-lookup"><span data-stu-id="126e7-128">Grant Connect Permission</span></span>  
 <span data-ttu-id="126e7-129">서버 인스턴스에 로그인을 만든 후에는 해당 로그인에 서버 인스턴스의 데이터베이스 미러링 엔드포인트에 연결할 권한을 부여해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="126e7-129">Once a login has been created on a server instance, the login must be granted permission to connect to the database mirroring endpoint of the server instance.</span></span> <span data-ttu-id="126e7-130">시스템 관리자는 GRANT [!INCLUDE[tsql](../../includes/tsql-md.md)] 문을 사용하여 CONNECT 권한을 부여합니다.</span><span class="sxs-lookup"><span data-stu-id="126e7-130">The system administrator grants the connect permission using a GRANT [!INCLUDE[tsql](../../includes/tsql-md.md)] statement.</span></span> <span data-ttu-id="126e7-131">자세한 내용은 [GRANT&#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-transact-sql)과 함께 작동하도록 Service Broker를 구성하는 방법에 대한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="126e7-131">For more information, see [GRANT &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-transact-sql).</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="126e7-132">관련 작업</span><span class="sxs-lookup"><span data-stu-id="126e7-132">Related Tasks</span></span>  
  
-   [<span data-ttu-id="126e7-133">로그인 만들기</span><span class="sxs-lookup"><span data-stu-id="126e7-133">Create a Login</span></span>](../../relational-databases/security/authentication-access/create-a-login.md)  
  
-   <span data-ttu-id="126e7-134">[Windows 인증 &#40;SQL Server&#41;를 사용 하 여 데이터베이스 미러링 끝점에 대 한 네트워크 액세스를 허용 ](../database-mirroring-allow-network-access-windows-authentication.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="126e7-134">[Allow Network Access to a Database Mirroring Endpoint Using Windows Authentication &#40;SQL Server&#41;](../database-mirroring-allow-network-access-windows-authentication.md).</span></span>  
  
-   [<span data-ttu-id="126e7-135">데이터베이스 미러링 엔드포인트에 대한 인증서 사용&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="126e7-135">Use Certificates for a Database Mirroring Endpoint &#40;Transact-SQL&#41;</span></span>](use-certificates-for-a-database-mirroring-endpoint-transact-sql.md)  
  
## <a name="see-also"></a><span data-ttu-id="126e7-136">참고 항목</span><span class="sxs-lookup"><span data-stu-id="126e7-136">See Also</span></span>  
 <span data-ttu-id="126e7-137">[데이터베이스 미러링 엔드포인트&#40;SQL Server&#41;](the-database-mirroring-endpoint-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="126e7-137">[The Database Mirroring Endpoint &#40;SQL Server&#41;](the-database-mirroring-endpoint-sql-server.md) </span></span>  
 <span data-ttu-id="126e7-138">[데이터베이스 미러링 구성 문제 해결&#40;SQL Server&#41;](troubleshoot-database-mirroring-configuration-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="126e7-138">[Troubleshoot Database Mirroring Configuration &#40;SQL Server&#41;](troubleshoot-database-mirroring-configuration-sql-server.md) </span></span>  
 [<span data-ttu-id="126e7-139">AlwaysOn 가용성 그룹 구성 &#40;SQL Server에 대 한 문제 해결&#41;</span><span class="sxs-lookup"><span data-stu-id="126e7-139">Troubleshoot AlwaysOn Availability Groups Configuration &#40;SQL Server&#41;</span></span>](../availability-groups/windows/troubleshoot-always-on-availability-groups-configuration-sql-server.md)  
  
  
