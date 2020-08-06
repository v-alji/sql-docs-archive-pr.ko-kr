---
title: 데이터베이스 미러링 끝점의 인바운드 연결에 대 한 인증서 사용 허용 (Transact-sql) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- certificates [SQL Server], database mirroring
- inbound connections
- database mirroring [SQL Server], security
ms.assetid: 5d48bb98-61f0-4b99-8f1a-b53f831d63d0
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: c05397dfbd1740293c4b154ace1ed5704cec11a9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647212"
---
# <a name="allow-a-database-mirroring-endpoint-to-use-certificates-for-inbound-connections-transact-sql"></a><span data-ttu-id="94dc2-102">데이터베이스 미러링 엔드포인트의 인바운드 연결에 대한 인증서 사용 허용(Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="94dc2-102">Allow a Database Mirroring Endpoint to Use Certificates for Inbound Connections (Transact-SQL)</span></span>
  <span data-ttu-id="94dc2-103">이 항목에서는 인증서를 사용하여 데이터베이스 미러링의 인바운드 연결을 인증하도록 서버 인스턴스를 구성하는 단계에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="94dc2-103">This topic describes the steps for configuring server instances to use certificates to authenticate inbound connections for database mirroring.</span></span> <span data-ttu-id="94dc2-104">인바운드 연결을 설정하려면 먼저 각 서버 인스턴스에서 아웃바운드 연결을 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="94dc2-104">Before you can set up inbound connections, you must configure outbound connections on each server instance.</span></span> <span data-ttu-id="94dc2-105">자세햔 내용은 [데이터베이스 미러링 엔드포인트의 아웃바운드 연결에 대한 인증서 사용 허용&#40;Transact-SQL&#41;](database-mirroring-use-certificates-for-outbound-connections.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="94dc2-105">For more information, see [Allow a Database Mirroring Endpoint to Use Certificates for Outbound Connections &#40;Transact-SQL&#41;](database-mirroring-use-certificates-for-outbound-connections.md).</span></span>  
  
 <span data-ttu-id="94dc2-106">인바운드 연결 구성은 대개 다음과 같은 단계로 진행됩니다.</span><span class="sxs-lookup"><span data-stu-id="94dc2-106">The process of configuring inbound connections, involves the following general steps:</span></span>  
  
1.  <span data-ttu-id="94dc2-107">다른 시스템에 대한 로그인을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="94dc2-107">Create a login for other system.</span></span>  
  
2.  <span data-ttu-id="94dc2-108">해당 로그인의 사용자를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="94dc2-108">Create a user for that login.</span></span>  
  
3.  <span data-ttu-id="94dc2-109">다른 서버 인스턴스의 미러링 엔드포인트에 대한 인증서를 얻습니다.</span><span class="sxs-lookup"><span data-stu-id="94dc2-109">Obtain the certificate for the mirroring endpoint of the other server instance.</span></span>  
  
4.  <span data-ttu-id="94dc2-110">2단계에서 만든 사용자에 인증서를 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="94dc2-110">Associate the certificate with the user created in step 2.</span></span>  
  
5.  <span data-ttu-id="94dc2-111">해당 미러링 엔드포인트에 대한 로그인에 CONNECT 권한을 부여합니다.</span><span class="sxs-lookup"><span data-stu-id="94dc2-111">Grant CONNECT permission on the login for that mirroring endpoint.</span></span>  
  
 <span data-ttu-id="94dc2-112">미러링 모니터가 있는 경우 그에 대한 인바운드 연결도 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="94dc2-112">If there is a witness, you must also set up inbound connections for it.</span></span> <span data-ttu-id="94dc2-113">이렇게 하려면 양쪽 파트너 모두에서 미러링 모니터에 대한 로그인, 사용자 및 인증서를 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="94dc2-113">This requires setting up logins, users, and certificates for the witness on both of the partners, and vice versa.</span></span>  
  
 <span data-ttu-id="94dc2-114">다음 절차에서 이러한 단계를 자세히 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="94dc2-114">The following procedure describes these steps in detail.</span></span> <span data-ttu-id="94dc2-115">각 단계에서는 HOST_A라는 시스템에서 서버 인스턴스를 구성하는 예를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="94dc2-115">For each step, the procedure provides an example for configuring a server instance on a system named HOST_A.</span></span> <span data-ttu-id="94dc2-116">예 섹션에서는 HOST_B라는 시스템에 또 다른 서버 인스턴스를 구성하는 동일한 단계를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="94dc2-116">The accompanying Example section demonstrates the same steps for another server instance on a system named HOST_B.</span></span>  
  
### <a name="to-configure-server-instances-for-inbound-mirroring-connections-on-host_a"></a><span data-ttu-id="94dc2-117">인바운드 미러링 연결을 위한 서버 인스턴스를 구성하려면(HOST_A)</span><span class="sxs-lookup"><span data-stu-id="94dc2-117">To configure server instances for inbound mirroring connections (on HOST_A)</span></span>  
  
1.  <span data-ttu-id="94dc2-118">다른 시스템에 대한 로그인을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="94dc2-118">Create a login for the other system.</span></span>  
  
     <span data-ttu-id="94dc2-119">다음 예에서는 HOST_A에 있는 서버 인스턴스의 **master** 데이터베이스에서 HOST_B 시스템에 대한 로그인을 만듭니다. 이 예에서 로그인 이름은 `HOST_B_login`입니다.</span><span class="sxs-lookup"><span data-stu-id="94dc2-119">The following example creates a login for the system, HOST_B, in the **master** database of the server instance on HOST_A; in this example, the login is named `HOST_B_login`.</span></span> <span data-ttu-id="94dc2-120">예제 암호를 자신의 암호로 대체합니다.</span><span class="sxs-lookup"><span data-stu-id="94dc2-120">Substitute a password of your own for the sample password.</span></span>  
  
    ```sql  
    USE master;  
    CREATE LOGIN HOST_B_login   
       WITH PASSWORD = '1Sample_Strong_Password!@#';  
    GO  
    ```  
  
     <span data-ttu-id="94dc2-121">자세한 내용은 [CREATE LOGIN&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-login-transact-sql)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="94dc2-121">For more information, see [CREATE LOGIN &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-login-transact-sql).</span></span>  
  
     <span data-ttu-id="94dc2-122">이 서버 인스턴스에서 사용자를 보려면 다음 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="94dc2-122">To view the logins on this server instance, you can use the following [!INCLUDE[tsql](../../includes/tsql-md.md)] statement:</span></span>  
  
    ```sql  
    SELECT * FROM sys.server_principals;  
    ```  
  
     <span data-ttu-id="94dc2-123">자세한 내용은 [sys.server_principals&#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-principals-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="94dc2-123">For more information, see [sys.server_principals &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-principals-transact-sql).</span></span>  
  
2.  <span data-ttu-id="94dc2-124">해당 로그인의 사용자를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="94dc2-124">Create a user for that login.</span></span>  
  
     <span data-ttu-id="94dc2-125">다음 예에서는 이전 단계에서 만든 로그인에 대해 사용자 `HOST_B_user`를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="94dc2-125">The following example creates a user, `HOST_B_user`, for the login created in the preceding step.</span></span>  
  
    ```sql  
    USE master;  
    CREATE USER HOST_B_user FOR LOGIN HOST_B_login;  
    GO  
    ```  
  
     <span data-ttu-id="94dc2-126">자세한 내용은 [CREATE USER&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-user-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="94dc2-126">For more information, see [CREATE USER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-user-transact-sql).</span></span>  
  
     <span data-ttu-id="94dc2-127">이 서버 인스턴스에서 로그인을 보려면 다음 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="94dc2-127">To view the users on this server instance, you can use the following [!INCLUDE[tsql](../../includes/tsql-md.md)] statement:</span></span>  
  
    ```sql  
    SELECT * FROM sys.sysusers;  
    ```  
  
     <span data-ttu-id="94dc2-128">자세한 내용은 [sys.sysusers&#40;Transact-SQL&#41;](/sql/relational-databases/system-compatibility-views/sys-sysusers-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="94dc2-128">For more information, see [sys.sysusers &#40;Transact-SQL&#41;](/sql/relational-databases/system-compatibility-views/sys-sysusers-transact-sql).</span></span>  
  
3.  <span data-ttu-id="94dc2-129">다른 서버 인스턴스의 미러링 엔드포인트에 대한 인증서를 얻습니다.</span><span class="sxs-lookup"><span data-stu-id="94dc2-129">Obtain the certificate for the mirroring endpoint of the other server instance.</span></span>  
  
     <span data-ttu-id="94dc2-130">아웃바운드 연결을 구성할 때 아직 인증서를 가져오지 못했으면 원격 서버 인스턴스의 미러링 엔드포인트에 대한 인증서 사본을 얻습니다.</span><span class="sxs-lookup"><span data-stu-id="94dc2-130">If you have not already done so when configuring outbound connections, obtain a copy of the certificate for the mirroring endpoint of the remote server instance.</span></span> <span data-ttu-id="94dc2-131">이렇게 하려면 [데이터베이스 미러링 엔드포인트의 아웃바운드 연결에 대한 인증서 사용 허용 &#40;Transact-SQL &#41;](database-mirroring-use-certificates-for-outbound-connections.md)에 설명된 대로 해당 서버 인스턴스의 인증서를 백업합니다.</span><span class="sxs-lookup"><span data-stu-id="94dc2-131">To do this, back up the certificate on that server instance as described in [Allow a Database Mirroring Endpoint to Use Certificates for Outbound Connections &#40;Transact-SQL&#41;](database-mirroring-use-certificates-for-outbound-connections.md).</span></span> <span data-ttu-id="94dc2-132">인증서를 다른 시스템으로 복사할 때는 안전한 복사 방법을 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="94dc2-132">When copying a certificate to another system, use a secure copy method.</span></span> <span data-ttu-id="94dc2-133">모든 인증서를 안전하게 보관하는 데 많은 주의를 기울여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="94dc2-133">Be extremely careful to keep all of your certificates secure.</span></span>  
  
     <span data-ttu-id="94dc2-134">자세한 내용은 [BACKUP CERTIFICATE&#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-certificate-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="94dc2-134">For more information, see [BACKUP CERTIFICATE &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-certificate-transact-sql).</span></span>  
  
4.  <span data-ttu-id="94dc2-135">2단계에서 만든 사용자에 인증서를 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="94dc2-135">Associate the certificate with the user created in step 2.</span></span>  
  
     <span data-ttu-id="94dc2-136">다음 예에서는 HOST_B의 인증서를 HOST_A에 있는 해당 사용자와 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="94dc2-136">The following example, associates the certificate of HOST_B with its user on HOST_A.</span></span>  
  
    ```sql  
    USE master;  
    CREATE CERTIFICATE HOST_B_cert  
       AUTHORIZATION HOST_B_user  
       FROM FILE = 'C:\HOST_B_cert.cer'  
    GO  
    ```  
  
     <span data-ttu-id="94dc2-137">자세한 내용은 [CREATE CERTIFICATE&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-certificate-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="94dc2-137">For more information, see [CREATE CERTIFICATE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-certificate-transact-sql).</span></span>  
  
     <span data-ttu-id="94dc2-138">이 서버 인스턴스에서 인증서를 보려면 다음 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="94dc2-138">To view the certificates on this server instance, use the following [!INCLUDE[tsql](../../includes/tsql-md.md)] statement:</span></span>  
  
    ```sql  
    SELECT * FROM sys.certificates;  
    ```  
  
     <span data-ttu-id="94dc2-139">자세한 내용은 [sys.certificates&#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-certificates-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="94dc2-139">For more information, see [sys.certificates &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-certificates-transact-sql).</span></span>  
  
5.  <span data-ttu-id="94dc2-140">해당 원격 미러링 엔드포인트에 대한 로그인에 CONNECT 권한을 부여합니다.</span><span class="sxs-lookup"><span data-stu-id="94dc2-140">Grant CONNECT permission on the login for the remote mirroring endpoint.</span></span>  
  
     <span data-ttu-id="94dc2-141">예를 들어 HOST_B에 있는 원격 서버 인스턴스에 대해 HOST_A에서 로컬 로그인에 연결할 권한을 부여하려면 즉, `HOST_B_login`에 연결하려면 다음 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="94dc2-141">For example, to grant permission on HOST_A to the remote server instance on HOST_B to connect to its local login-that is, to connect to `HOST_B_login`-use the following [!INCLUDE[tsql](../../includes/tsql-md.md)] statements:</span></span>  
  
    ```sql  
    USE master;  
    GRANT CONNECT ON ENDPOINT::Endpoint_Mirroring TO [HOST_B_login];  
    GO  
    ```  
  
     <span data-ttu-id="94dc2-142">자세한 내용은 [GRANT 엔드포인트 사용 권한&#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-endpoint-permissions-transact-sql)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="94dc2-142">For more information, see [GRANT Endpoint Permissions &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-endpoint-permissions-transact-sql).</span></span>  
  
 <span data-ttu-id="94dc2-143">이로써 HOST_B에서 HOST_A에 로그인하기 위한 인증서 인증 설정이 끝났습니다.</span><span class="sxs-lookup"><span data-stu-id="94dc2-143">This completes setting up certificate authentication for HOST_B to log in to HOST_A.</span></span>  
  
 <span data-ttu-id="94dc2-144">이제 HOST_B에서 HOST_A에 대한 같은 인바운드 단계를 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="94dc2-144">You now need to perform the equivalent inbound steps for HOST_A on HOST_B.</span></span> <span data-ttu-id="94dc2-145">이러한 단계는 아래에 있는 예 섹션의 인바운드 부분 예에 설명되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="94dc2-145">These steps are illustrated in the inbound portion of the example in the Example section, below.</span></span>  
  
## <a name="example"></a><span data-ttu-id="94dc2-146">예제</span><span class="sxs-lookup"><span data-stu-id="94dc2-146">Example</span></span>  
 <span data-ttu-id="94dc2-147">다음 예에서는 인바운드 연결을 위한 HOST_B 구성을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="94dc2-147">The following example demonstrates configuring HOST_B for inbound connections.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="94dc2-148">이 예제에서는 [데이터베이스 미러링 엔드포인트의 아웃바운드 연결에 대한 인증서 사용 허용 &#40;Transact-SQL &#41;](database-mirroring-use-certificates-for-outbound-connections.md)의 코드 조각으로 만든 HOST_A 인증서가 포함된 인증서 파일을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="94dc2-148">This example uses a certificate file containing the HOST_A certificate that is created by a code snippet in [Allow a Database Mirroring Endpoint to Use Certificates for Outbound Connections &#40;Transact-SQL&#41;](database-mirroring-use-certificates-for-outbound-connections.md).</span></span>  
  
```sql  
USE master;  
--On HOST_B, create a login for HOST_A.  
CREATE LOGIN HOST_A_login WITH PASSWORD = 'AStrongPassword!@#';  
GO  
--Create a user, HOST_A_user, for that login.  
CREATE USER HOST_A_user FOR LOGIN HOST_A_login;  
GO  
--Obtain HOST_A certificate. (See the note   
--   preceding this example.)  
--Asscociate this certificate with the user, HOST_A_user.  
CREATE CERTIFICATE HOST_A_cert  
   AUTHORIZATION HOST_A_user  
   FROM FILE = 'C:\HOST_A_cert.cer';  
GO  
--Grant CONNECT permission for the server instance on HOST_A.  
GRANT CONNECT ON ENDPOINT::Endpoint_Mirroring TO HOST_A_login;  
GO  
```  
  
 <span data-ttu-id="94dc2-149">자동 장애 조치(failover)를 지원하는 보호 우선 모드에서 실행하려는 경우 아웃바운드 및 인바운드 연결에 대한 미러링 모니터를 구성하기 위해 같은 설정 단계를 반복해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="94dc2-149">If you intend to run in high-safety mode with automatic failover, you must repeat the same set up steps to configure the witness for outbound and inbound connections.</span></span>  
  
 <span data-ttu-id="94dc2-150">Transact-SQL 예제를 포함하여 미러 데이터베이스를 만드는 방법은 [미러 데이터베이스의 미러링 준비&#40;SQL Server&#41;](prepare-a-mirror-database-for-mirroring-sql-server.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="94dc2-150">For information on creating a mirror database, including a Transact-SQL example, see [Prepare a Mirror Database for Mirroring &#40;SQL Server&#41;](prepare-a-mirror-database-for-mirroring-sql-server.md).</span></span>  
  
 <span data-ttu-id="94dc2-151">고성능 모드 세션을 설정하는 Transact-SQL 예는 [예제: 인증서를 사용하여 데이터베이스 미러링 설정&#40;Transact-SQL&#41;](example-setting-up-database-mirroring-using-certificates-transact-sql.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="94dc2-151">For a Transact-SQL example of establishing a high-performance mode session, see [Example: Setting Up Database Mirroring Using Certificates &#40;Transact-SQL&#41;](example-setting-up-database-mirroring-using-certificates-transact-sql.md).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="94dc2-152">.NET Framework 보안</span><span class="sxs-lookup"><span data-stu-id="94dc2-152">.NET Framework Security</span></span>  
 <span data-ttu-id="94dc2-153">인증서를 다른 시스템으로 복사할 때는 안전한 복사 방법을 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="94dc2-153">When copying a certificate to another system, use a secure copy method.</span></span> <span data-ttu-id="94dc2-154">모든 인증서를 안전하게 보관하는 데 많은 주의를 기울여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="94dc2-154">Be extremely careful to keep all of your certificates secure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94dc2-155">참고 항목</span><span class="sxs-lookup"><span data-stu-id="94dc2-155">See Also</span></span>  
 <span data-ttu-id="94dc2-156">[데이터베이스 미러링 및 AlwaysOn 가용성 그룹 &#40;SQL Server에 대 한 전송 보안&#41;](transport-security-database-mirroring-always-on-availability.md) </span><span class="sxs-lookup"><span data-stu-id="94dc2-156">[Transport Security for Database Mirroring and AlwaysOn Availability Groups &#40;SQL Server&#41;](transport-security-database-mirroring-always-on-availability.md) </span></span>  
 <span data-ttu-id="94dc2-157">[GRANT 엔드포인트 사용 권한&#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-endpoint-permissions-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="94dc2-157">[GRANT Endpoint Permissions &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-endpoint-permissions-transact-sql) </span></span>  
 <span data-ttu-id="94dc2-158">[암호화 된 미러 데이터베이스 설정](set-up-an-encrypted-mirror-database.md) </span><span class="sxs-lookup"><span data-stu-id="94dc2-158">[Set Up an Encrypted Mirror Database](set-up-an-encrypted-mirror-database.md) </span></span>  
 <span data-ttu-id="94dc2-159">[데이터베이스 미러링 엔드포인트&#40;SQL Server&#41;](the-database-mirroring-endpoint-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="94dc2-159">[The Database Mirroring Endpoint &#40;SQL Server&#41;](the-database-mirroring-endpoint-sql-server.md) </span></span>  
 [<span data-ttu-id="94dc2-160">데이터베이스 미러링 구성 문제 해결&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="94dc2-160">Troubleshoot Database Mirroring Configuration &#40;SQL Server&#41;</span></span>](troubleshoot-database-mirroring-configuration-sql-server.md)  
  
  
