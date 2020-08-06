---
title: '예제: 인증서를 사용하여 데이터베이스 미러링 설정(Transact-SQL) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- database mirroring [SQL Server], deployment
- certificates [SQL Server], database mirroring
- authentication [SQL Server], database mirroring
- database mirroring [SQL Server], security
ms.assetid: df489ecd-deee-465c-a26a-6d1bef6d7b66
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: ea87e2de984107c5a0fda6eb2629ee5cfd197841
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742571"
---
# <a name="example-setting-up-database-mirroring-using-certificates-transact-sql"></a><span data-ttu-id="297da-102">예제: 인증서를 사용하여 데이터베이스 미러링 설정(Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="297da-102">Example: Setting Up Database Mirroring Using Certificates (Transact-SQL)</span></span>
  <span data-ttu-id="297da-103">이 예에서는 인증서 기반 인증을 사용하여 데이터베이스 미러링 세션을 만드는 데 필요한 모든 단계를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="297da-103">This example shows all the stages required to create a database mirroring session using certificate-based authentication.</span></span> <span data-ttu-id="297da-104">이 항목의 예에서는 [!INCLUDE[tsql](../../includes/tsql-md.md)]을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="297da-104">The examples in this topic use [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="297da-105">네트워크 보안을 보장할 수 없는 경우 데이터베이스 미러링 연결에 암호화를 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="297da-105">Unless you can guarantee that your network is secure, we recommend that you use encryption for database mirroring connections.</span></span>  
  
 <span data-ttu-id="297da-106">인증서를 다른 시스템으로 복사할 때는 안전한 복사 방법을 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="297da-106">When copying a certificate to another system, use a secure copy method.</span></span> <span data-ttu-id="297da-107">모든 인증서를 안전하게 보관하는 데 많은 주의를 기울여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="297da-107">Be extremely careful to keep all of your certificates secure.</span></span>  
  
##  <a name="example"></a><a name="ExampleH2"></a> <span data-ttu-id="297da-108">예제</span><span class="sxs-lookup"><span data-stu-id="297da-108">Example</span></span>  
 <span data-ttu-id="297da-109">다음 예에서는 HOST_A에 있는 한 파트너에서 실행되어야 하는 단계를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="297da-109">The following example demonstrates what must be done on one partner that resides on HOST_A.</span></span> <span data-ttu-id="297da-110">이 예에서 파트너 2개는 컴퓨터 시스템 3대의 기본 서버 인스턴스입니다.</span><span class="sxs-lookup"><span data-stu-id="297da-110">In this example, the two partners are the default server instances on three computer systems.</span></span> <span data-ttu-id="297da-111">이 중 두 서버 인스턴스는 트러스트되지 않은 Windows 도메인에서 실행되므로 인증서 기반 인증이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="297da-111">The two server instances run in nontrusted Windows domains, so certificate-based authentication is required.</span></span>  
  
 <span data-ttu-id="297da-112">HOST_A는 초기 주 역할을 맡고 HOST_B는 미러 역할을 맡습니다.</span><span class="sxs-lookup"><span data-stu-id="297da-112">The initial principal role is taken by HOST_A, and the mirror role is taken by HOST_B.</span></span>  
  
 <span data-ttu-id="297da-113">인증서를 사용하여 데이터베이스 미러링을 설정하는 작업은 4개의 일반적인 단계로 이루어지며, 이 예제에서는 이 중 3개, 즉 1, 2, 4단계를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="297da-113">Setting up database mirroring using certificates involves four general stages, of which three stages-1, 2, and 4-are demonstrated by this example.</span></span> <span data-ttu-id="297da-114">이러한 단계는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="297da-114">These stages are as follows:</span></span>  
  
1.  [<span data-ttu-id="297da-115">아웃바운드 연결 구성</span><span class="sxs-lookup"><span data-stu-id="297da-115">Configuring Outbound Connections</span></span>](#ConfiguringOutboundConnections)  
  
     <span data-ttu-id="297da-116">이 예에서는 다음 작업을 위한 단계를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="297da-116">This example shows the steps for:</span></span>  
  
    1.  <span data-ttu-id="297da-117">아웃바운드 연결에 대한 Host_A 구성</span><span class="sxs-lookup"><span data-stu-id="297da-117">Configuring Host_A for outbound connections.</span></span>  
  
    2.  <span data-ttu-id="297da-118">아웃바운드 연결에 대한 Host_B 구성</span><span class="sxs-lookup"><span data-stu-id="297da-118">Configuring Host_B for outbound connections.</span></span>  
  
     <span data-ttu-id="297da-119">이 데이터베이스 미러링 설정 단계에 대한 자세한 내용은 [데이터베이스 미러링 엔드포인트의 아웃바운드 연결에 대한 인증서 사용 허용&#40;Transact-SQL&#41;](database-mirroring-use-certificates-for-outbound-connections.md)을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="297da-119">For information about this stage of setting up database mirroring, see [Allow a Database Mirroring Endpoint to Use Certificates for Outbound Connections &#40;Transact-SQL&#41;](database-mirroring-use-certificates-for-outbound-connections.md).</span></span>  
  
2.  [<span data-ttu-id="297da-120">인바운드 연결 구성</span><span class="sxs-lookup"><span data-stu-id="297da-120">Configuring Inbound Connections</span></span>](#ConfigureInboundConnections)  
  
     <span data-ttu-id="297da-121">이 예에서는 다음 작업을 위한 단계를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="297da-121">This example shows the steps for:</span></span>  
  
    1.  <span data-ttu-id="297da-122">인바운드 연결에 대한 Host_A 구성</span><span class="sxs-lookup"><span data-stu-id="297da-122">Configuring Host_A for inbound connections.</span></span>  
  
    2.  <span data-ttu-id="297da-123">인바운드 연결에 대한 Host_B 구성</span><span class="sxs-lookup"><span data-stu-id="297da-123">Configuring Host_B for inbound connections.</span></span>  
  
     <span data-ttu-id="297da-124">이 데이터베이스 미러링 설정 단계에 대한 자세한 내용은 [데이터베이스 미러링 엔드포인트의 인바운드 연결에 대한 인증서 사용 허용&#40;Transact-SQL&#41;](database-mirroring-use-certificates-for-inbound-connections.md)을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="297da-124">For information about this stage of setting up database mirroring, see [Allow a Database Mirroring Endpoint to Use Certificates for Inbound Connections &#40;Transact-SQL&#41;](database-mirroring-use-certificates-for-inbound-connections.md).</span></span>  
  
3.  <span data-ttu-id="297da-125">미러 데이터베이스 만들기</span><span class="sxs-lookup"><span data-stu-id="297da-125">Creating the Mirror Database</span></span>  
  
     <span data-ttu-id="297da-126">미러 데이터베이스를 만드는 방법에 대한 자세한 내용은 [미러 데이터베이스의 미러링 준비&#40;SQL Server&#41;](prepare-a-mirror-database-for-mirroring-sql-server.md)을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="297da-126">For information on how to create a mirror database, see [Prepare a Mirror Database for Mirroring &#40;SQL Server&#41;](prepare-a-mirror-database-for-mirroring-sql-server.md).</span></span>  
  
4.  [<span data-ttu-id="297da-127">미러링 파트너 구성</span><span class="sxs-lookup"><span data-stu-id="297da-127">Configuring the Mirroring Partners</span></span>](#ConfigureMirroringPartners)  
  
###  <a name="configuring-outbound-connections"></a><a name="ConfiguringOutboundConnections"></a> <span data-ttu-id="297da-128">아웃바운드 연결 구성</span><span class="sxs-lookup"><span data-stu-id="297da-128">Configuring Outbound Connections</span></span>  
 <span data-ttu-id="297da-129">**아웃바운드 연결에 대한 Host_A를 구성하려면**</span><span class="sxs-lookup"><span data-stu-id="297da-129">**To configure Host_A for outbound connections**</span></span>  
  
1.  <span data-ttu-id="297da-130">필요한 경우 master 데이터베이스에 데이터베이스 마스터 키를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="297da-130">On the master database, create the database master key, if needed.</span></span>  
  
    ```  
    USE master;  
    CREATE MASTER KEY ENCRYPTION BY PASSWORD = '<1_Strong_Password!>';  
    GO  
    ```  
  
2.  <span data-ttu-id="297da-131">이 서버 인스턴스에 대한 인증서를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="297da-131">Make a certificate for this server instance.</span></span>  
  
    ```  
    USE master;  
    CREATE CERTIFICATE HOST_A_cert   
       WITH SUBJECT = 'HOST_A certificate';  
    GO  
    ```  
  
3.  <span data-ttu-id="297da-132">인증서를 사용하여 서버 인스턴스에 대한 미러링 엔드포인트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="297da-132">Create a mirroring endpoint for server instance using the certificate.</span></span>  
  
    ```  
    CREATE ENDPOINT Endpoint_Mirroring  
       STATE = STARTED  
       AS TCP (  
          LISTENER_PORT=7024  
          , LISTENER_IP = ALL  
       )   
       FOR DATABASE_MIRRORING (   
          AUTHENTICATION = CERTIFICATE HOST_A_cert  
          , ENCRYPTION = REQUIRED ALGORITHM AES  
          , ROLE = ALL  
       );  
    GO  
    ```  
  
4.  <span data-ttu-id="297da-133">HOST_A 인증서를 백업하여 HOST_B 시스템에 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="297da-133">Back up the HOST_A certificate, and copy it to other system, HOST_B.</span></span>  
  
    ```  
    BACKUP CERTIFICATE HOST_A_cert TO FILE = 'C:\HOST_A_cert.cer';  
    GO  
    ```  
  
5.  <span data-ttu-id="297da-134">안전한 복사 방법을 사용하여 C:\HOST_A_cert.cer을 HOST_B로 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="297da-134">Using any secure copy method, copy C:\HOST_A_cert.cer to HOST_B.</span></span>  
  
 <span data-ttu-id="297da-135">**아웃바운드 연결에 대한 Host_B를 구성하려면**</span><span class="sxs-lookup"><span data-stu-id="297da-135">**To configure Host_B for outbound connections**</span></span>  
  
1.  <span data-ttu-id="297da-136">필요한 경우 master 데이터베이스에 데이터베이스 마스터 키를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="297da-136">On the master database, create the database master key, if needed.</span></span>  
  
    ```  
    USE master;  
    CREATE MASTER KEY ENCRYPTION BY PASSWORD = '<Strong_Password_#2>';  
    GO  
    ```  
  
2.  <span data-ttu-id="297da-137">HOST_B 서버 인스턴스에 대한 인증서를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="297da-137">Make a certificate on the HOST_B server instance.</span></span>  
  
    ```  
    CREATE CERTIFICATE HOST_B_cert   
       WITH SUBJECT = 'HOST_B certificate for database mirroring';  
    GO  
    ```  
  
3.  <span data-ttu-id="297da-138">HOST_B 서버 인스턴스에 대한 미러링 엔드포인트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="297da-138">Create a mirroring endpoint for the server instance on HOST_B.</span></span>  
  
    ```  
    CREATE ENDPOINT Endpoint_Mirroring  
       STATE = STARTED  
       AS TCP (  
          LISTENER_PORT=7024  
          , LISTENER_IP = ALL  
       )   
       FOR DATABASE_MIRRORING (   
          AUTHENTICATION = CERTIFICATE HOST_B_cert  
          , ENCRYPTION = REQUIRED ALGORITHM AES  
          , ROLE = ALL  
       );  
    GO  
    ```  
  
4.  <span data-ttu-id="297da-139">HOST_B 인증서를 백업합니다.</span><span class="sxs-lookup"><span data-stu-id="297da-139">Back up HOST_B certificate.</span></span>  
  
    ```  
    BACKUP CERTIFICATE HOST_B_cert TO FILE = 'C:\HOST_B_cert.cer';  
    GO   
    ```  
  
5.  <span data-ttu-id="297da-140">안전한 복사 방법을 사용하여 C:\HOST_B_cert.cer을 HOST_A로 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="297da-140">Using any secure copy method, copy C:\HOST_B_cert.cer to HOST_A.</span></span>  
  
 <span data-ttu-id="297da-141">자세햔 내용은 [데이터베이스 미러링 엔드포인트의 아웃바운드 연결에 대한 인증서 사용 허용&#40;Transact-SQL&#41;](database-mirroring-use-certificates-for-outbound-connections.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="297da-141">For more information, see [Allow a Database Mirroring Endpoint to Use Certificates for Outbound Connections &#40;Transact-SQL&#41;](database-mirroring-use-certificates-for-outbound-connections.md).</span></span>  
  
###  <a name="configuring-inbound-connections"></a><a name="ConfigureInboundConnections"></a> <span data-ttu-id="297da-142">인바운드 연결 구성</span><span class="sxs-lookup"><span data-stu-id="297da-142">Configuring Inbound Connections</span></span>  
 <span data-ttu-id="297da-143">**인바운드 연결에 대한 Host_A를 구성하려면**</span><span class="sxs-lookup"><span data-stu-id="297da-143">**To configure Host_A for inbound connections**</span></span>  
  
1.  <span data-ttu-id="297da-144">HOST_A에서 HOST_B에 대한 로그인을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="297da-144">Create a login on HOST_A for HOST_B.</span></span>  
  
    ```  
    USE master;  
    CREATE LOGIN HOST_B_login WITH PASSWORD = '1Sample_Strong_Password!@#';  
    GO  
    ```  
  
2.  <span data-ttu-id="297da-145">--해당 로그인의 사용자를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="297da-145">--Create a user for that login.</span></span>  
  
    ```  
    CREATE USER HOST_B_user FOR LOGIN HOST_B_login;  
    GO  
    ```  
  
3.  <span data-ttu-id="297da-146">--인증서를 사용자와 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="297da-146">--Associate the certificate with the user.</span></span>  
  
    ```  
    CREATE CERTIFICATE HOST_B_cert  
       AUTHORIZATION HOST_B_user  
       FROM FILE = 'C:\HOST_B_cert.cer'  
    GO  
    ```  
  
4.  <span data-ttu-id="297da-147">해당 원격 미러링 엔드포인트에 대한 로그인에 CONNECT 권한을 부여합니다.</span><span class="sxs-lookup"><span data-stu-id="297da-147">Grant CONNECT permission on the login for the remote mirroring endpoint.</span></span>  
  
    ```  
    GRANT CONNECT ON ENDPOINT::Endpoint_Mirroring TO [HOST_B_login];  
    GO  
    ```  
  
 <span data-ttu-id="297da-148">**인바운드 연결에 대한 Host_B를 구성하려면**</span><span class="sxs-lookup"><span data-stu-id="297da-148">**To configure Host_B for inbound connections**</span></span>  
  
1.  <span data-ttu-id="297da-149">HOST_B에서 HOST_A에 대한 로그인을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="297da-149">Create a login on HOST_B for HOST_A.</span></span>  
  
    ```  
    USE master;  
    CREATE LOGIN HOST_A_login WITH PASSWORD = '=Sample#2_Strong_Password2';  
    GO  
    ```  
  
2.  <span data-ttu-id="297da-150">해당 로그인의 사용자를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="297da-150">Create a user for that login.</span></span>  
  
    ```  
    CREATE USER HOST_A_user FOR LOGIN HOST_A_login;  
    GO  
    ```  
  
3.  <span data-ttu-id="297da-151">인증서를 사용자와 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="297da-151">Associate the certificate with the user.</span></span>  
  
    ```  
    CREATE CERTIFICATE HOST_A_cert  
       AUTHORIZATION HOST_A_user  
       FROM FILE = 'C:\HOST_A_cert.cer'  
    GO  
    ```  
  
4.  <span data-ttu-id="297da-152">해당 원격 미러링 엔드포인트에 대한 로그인에 CONNECT 권한을 부여합니다.</span><span class="sxs-lookup"><span data-stu-id="297da-152">Grant CONNECT permission on the login for the remote mirroring endpoint.</span></span>  
  
    ```  
    GRANT CONNECT ON ENDPOINT::Endpoint_Mirroring TO [HOST_A_login];  
    GO  
    ```  
  
> [!IMPORTANT]  
>  <span data-ttu-id="297da-153">자동 장애 조치(Failover)를 지원하는 보호 우선 모드에서 실행하려는 경우 아웃바운드 및 인바운드 연결에 대한 미러링 모니터를 구성하기 위해 같은 설정 단계를 반복해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="297da-153">If you intend to run in high-safety mode with automatic failover, you must repeat the same setup steps to configure the witness for outbound and inbound connections.</span></span> <span data-ttu-id="297da-154">미러링 모니터를 사용하는 경우 인바운드 연결을 설정하려면 두 파트너 모두에서 미러링 모니터에 대해 그리고 미러링 모니터에서 두 파트너 모두에 대해 로그인과 사용자를 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="297da-154">Setting up the inbound connections when a witness is involved requires that you set up logins and users for the witness on both of the partners and for both partners on the witness.</span></span>  
  
 <span data-ttu-id="297da-155">자세햔 내용은 [데이터베이스 미러링 엔드포인트의 인바운드 연결에 대한 인증서 사용 허용&#40;Transact-SQL&#41;](database-mirroring-use-certificates-for-inbound-connections.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="297da-155">For more information, see [Allow a Database Mirroring Endpoint to Use Certificates for Inbound Connections &#40;Transact-SQL&#41;](database-mirroring-use-certificates-for-inbound-connections.md).</span></span>  
  
### <a name="creating-the-mirror-database"></a><span data-ttu-id="297da-156">미러 데이터베이스 만들기</span><span class="sxs-lookup"><span data-stu-id="297da-156">Creating the Mirror Database</span></span>  
 <span data-ttu-id="297da-157">미러 데이터베이스를 만드는 방법에 대한 자세한 내용은 [미러 데이터베이스의 미러링 준비&#40;SQL Server&#41;](prepare-a-mirror-database-for-mirroring-sql-server.md)을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="297da-157">For information on how to create a mirror database, see [Prepare a Mirror Database for Mirroring &#40;SQL Server&#41;](prepare-a-mirror-database-for-mirroring-sql-server.md).</span></span>  
  
###  <a name="configuring-the-mirroring-partners"></a><a name="ConfigureMirroringPartners"></a> <span data-ttu-id="297da-158">미러링 파트너 구성</span><span class="sxs-lookup"><span data-stu-id="297da-158">Configuring the Mirroring Partners</span></span>  
  
1.  <span data-ttu-id="297da-159">HOST_B의 미러 서버 인스턴스에서 HOST_A의 서버 인스턴스를 초기 주 서버 인스턴스로 만들어 파트너로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="297da-159">On the mirror server instance on HOST_B, set the server instance on HOST_A as the partner (making it the initial principal server instance).</span></span> <span data-ttu-id="297da-160">`TCP://HOST_A.Mydomain.Corp.Adventure-Works``.com:7024`를 유효한 네트워크 주소로 대체합니다.</span><span class="sxs-lookup"><span data-stu-id="297da-160">Substitute a valid network address for `TCP://HOST_A.Mydomain.Corp.Adventure-Works``.com:7024`.</span></span> <span data-ttu-id="297da-161">자세햔 내용은 [서버 네트워크 주소 지정&#40;데이터베이스 미러링&#41;](specify-a-server-network-address-database-mirroring.md)을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="297da-161">For more information, see [Specify a Server Network Address &#40;Database Mirroring&#41;](specify-a-server-network-address-database-mirroring.md).</span></span>  
  
    ```  
    --At HOST_B, set server instance on HOST_A as partner (principal server):  
    ALTER DATABASE AdventureWorks   
        SET PARTNER = 'TCP://HOST_A.Mydomain.Corp.Adventure-Works.com:7024';  
    GO  
    ```  
  
2.  <span data-ttu-id="297da-162">HOST_A의 주 서버 인스턴스에서 HOST_B의 서버 인스턴스를 초기 미러 서버 인스턴스로 만들어 파트너로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="297da-162">On the principal server instance on HOST_A, set the server instance on HOST_B as the partner (making it the initial mirror server instance).</span></span> <span data-ttu-id="297da-163">`TCP://HOST_B.Mydomain.Corp.Adventure-Works.com:7024`를 유효한 네트워크 주소로 대체합니다.</span><span class="sxs-lookup"><span data-stu-id="297da-163">Substitute a valid network address for `TCP://HOST_B.Mydomain.Corp.Adventure-Works.com:7024`.</span></span>  
  
    ```  
    --At HOST_A, set server instance on HOST_B as partner (mirror server).  
    ALTER DATABASE AdventureWorks   
        SET PARTNER = 'TCP://HOST_B.Mydomain.Corp.Adventure-Works.com:7024';  
    GO  
    ```  
  
3.  <span data-ttu-id="297da-164">이 예에서는 세션이 고성능 모드에서 실행될 것으로 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="297da-164">This example assumes that the session will be running in high-performance mode.</span></span> <span data-ttu-id="297da-165">고성능 모드에 맞게 이 세션을 구성하려면 HOST_A의 주 서버 인스턴스에서 트랜잭션 보안을 OFF로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="297da-165">To configure this session for high-performance mode, on the principal server instance (on HOST_A), set transaction safety to OFF.</span></span>  
  
    ```  
    --Change to high-performance mode by turning off transacton safety.  
    ALTER DATABASE AdventureWorks   
        SET PARTNER SAFETY OFF  
    GO  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="297da-166">자동 장애 조치 (failover)가 있는 보호 우선 모드에서 실행 하려면 트랜잭션 보안을 FULL (기본 설정)으로 설정 된 채로 두고 두 번째 set PARTNER **' *`partner_server`* '** 문을 실행 한 후 가능한 한 빨리 미러링 모니터 서버를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="297da-166">If you intend to run in high-safety mode with automatic failover, leave transaction safety set to FULL (the default setting) and add the witness as soon as possible after executing the second SET PARTNER **'*`partner_server`*'** statement.</span></span> <span data-ttu-id="297da-167">먼저 아웃바운드 및 인바운드 연결에 대한 미러링 모니터를 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="297da-167">Note that the witness must first be configured for outbound and inbound connections.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="297da-168">관련 작업</span><span class="sxs-lookup"><span data-stu-id="297da-168">Related Tasks</span></span>  
  
-   [<span data-ttu-id="297da-169">미러 데이터베이스의 미러링 준비&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="297da-169">Prepare a Mirror Database for Mirroring &#40;SQL Server&#41;</span></span>](prepare-a-mirror-database-for-mirroring-sql-server.md)  
  
-   [<span data-ttu-id="297da-170">데이터베이스 미러링 엔드포인트의 인바운드 연결에 대한 인증서 사용 허용&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="297da-170">Allow a Database Mirroring Endpoint to Use Certificates for Inbound Connections &#40;Transact-SQL&#41;</span></span>](database-mirroring-use-certificates-for-inbound-connections.md)  
  
-   [<span data-ttu-id="297da-171">데이터베이스 미러링 엔드포인트의 아웃바운드 연결에 대한 인증서 사용 허용&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="297da-171">Allow a Database Mirroring Endpoint to Use Certificates for Outbound Connections &#40;Transact-SQL&#41;</span></span>](database-mirroring-use-certificates-for-outbound-connections.md)  
  
-   [<span data-ttu-id="297da-172">역할 전환 후 로그인 및 작업 관리&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="297da-172">Management of Logins and Jobs After Role Switching &#40;SQL Server&#41;</span></span>](../../sql-server/failover-clusters/management-of-logins-and-jobs-after-role-switching-sql-server.md)  
  
-   <span data-ttu-id="297da-173">[다른 서버 인스턴스에서 데이터베이스를 사용할 수 있도록 할 때 메타데이터 관리&#40;SQL Server&#41;](../../relational-databases/databases/manage-metadata-when-making-a-database-available-on-another-server.md)(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="297da-173">[Manage Metadata When Making a Database Available on Another Server Instance &#40;SQL Server&#41;](../../relational-databases/databases/manage-metadata-when-making-a-database-available-on-another-server.md) (SQL Server)</span></span>  
  
-   [<span data-ttu-id="297da-174">데이터베이스 미러링 구성 문제 해결&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="297da-174">Troubleshoot Database Mirroring Configuration &#40;SQL Server&#41;</span></span>](troubleshoot-database-mirroring-configuration-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="297da-175">참고 항목</span><span class="sxs-lookup"><span data-stu-id="297da-175">See Also</span></span>  
 <span data-ttu-id="297da-176">[데이터베이스 미러링 및 AlwaysOn 가용성 그룹 &#40;SQL Server에 대 한 전송 보안&#41;](transport-security-database-mirroring-always-on-availability.md) </span><span class="sxs-lookup"><span data-stu-id="297da-176">[Transport Security for Database Mirroring and AlwaysOn Availability Groups &#40;SQL Server&#41;](transport-security-database-mirroring-always-on-availability.md) </span></span>  
 <span data-ttu-id="297da-177">[서버 네트워크 주소 지정&#40;데이터베이스 미러링&#41;](specify-a-server-network-address-database-mirroring.md) </span><span class="sxs-lookup"><span data-stu-id="297da-177">[Specify a Server Network Address &#40;Database Mirroring&#41;](specify-a-server-network-address-database-mirroring.md) </span></span>  
 <span data-ttu-id="297da-178">[데이터베이스 미러링 엔드포인트&#40;SQL Server&#41;](the-database-mirroring-endpoint-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="297da-178">[The Database Mirroring Endpoint &#40;SQL Server&#41;](the-database-mirroring-endpoint-sql-server.md) </span></span>  
 <span data-ttu-id="297da-179">[데이터베이스 미러링 엔드포인트에 대한 인증서 사용&#40;Transact-SQL&#41;](use-certificates-for-a-database-mirroring-endpoint-transact-sql.md) </span><span class="sxs-lookup"><span data-stu-id="297da-179">[Use Certificates for a Database Mirroring Endpoint &#40;Transact-SQL&#41;](use-certificates-for-a-database-mirroring-endpoint-transact-sql.md) </span></span>  
 <span data-ttu-id="297da-180">[ALTER DATABASE &#40;Transact-SQL &#41;](/sql/t-sql/statements/alter-database-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="297da-180">[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) </span></span>  
 [<span data-ttu-id="297da-181">SQL Server 데이터베이스 엔진 및 Azure SQL Database 보안 센터</span><span class="sxs-lookup"><span data-stu-id="297da-181">Security Center for SQL Server Database Engine and Azure SQL Database</span></span>](../../relational-databases/security/security-center-for-sql-server-database-engine-and-azure-sql-database.md)  
  
  
