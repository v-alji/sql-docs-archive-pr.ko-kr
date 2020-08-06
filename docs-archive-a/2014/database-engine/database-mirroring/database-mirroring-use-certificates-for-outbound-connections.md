---
title: 데이터베이스 미러링 끝점의 아웃 바운드 연결에 대 한 인증서 사용 허용 (Transact-sql) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- certificates [SQL Server], database mirroring
- outbound connections [SQL Server]
- database mirroring [SQL Server], security
ms.assetid: 464c9096-10d6-4c5e-8bb1-19acba27ad9e
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: f380f268f8d0f8d033db9c28f83d066d3f134571
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647211"
---
# <a name="allow-a-database-mirroring-endpoint-to-use-certificates-for-outbound-connections-transact-sql"></a><span data-ttu-id="c39fb-102">데이터베이스 미러링 엔드포인트의 아웃바운드 연결에 대한 인증서 사용 허용(Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="c39fb-102">Allow a Database Mirroring Endpoint to Use Certificates for Outbound Connections (Transact-SQL)</span></span>
  <span data-ttu-id="c39fb-103">이 항목에서는 인증서를 사용하여 데이터베이스 미러링의 아웃바운드 연결을 인증하도록 서버 인스턴스를 구성하는 단계를 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="c39fb-103">This topic describes the steps for configuring server instances to use certificates to authenticate outbound connections for database mirroring.</span></span> <span data-ttu-id="c39fb-104">아웃바운드 연결을 구성한 후 인바운드 연결을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c39fb-104">Outbound connection configuration must be done before you can set up inbound connections.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c39fb-105">서버 인스턴스의 모든 미러링 연결은 단일 데이터베이스 미러링 엔드포인트를 사용하며 이러한 엔드포인트를 만들 때는 서버 인스턴스의 인증 방법을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c39fb-105">All mirroring connections on a server instance use a single database mirroring endpoint, and you must specify the authentication method of the server instance when you create the endpoint.</span></span>  
  
 <span data-ttu-id="c39fb-106">아웃바운드 연결 구성은 대개 다음과 같은 단계로 진행됩니다.</span><span class="sxs-lookup"><span data-stu-id="c39fb-106">The process of configuring outbound connections, involves the following general steps:</span></span>  
  
1.  <span data-ttu-id="c39fb-107">**master** 데이터베이스에서 데이터베이스 마스터 키를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c39fb-107">In the **master** database, create a database Master Key.</span></span>  
  
2.  <span data-ttu-id="c39fb-108">**master** 데이터베이스에서 서버 인스턴스의 암호화된 인증서를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c39fb-108">In the **master** database, create an encrypted certificate on the server instance.</span></span>  
  
3.  <span data-ttu-id="c39fb-109">서버 인스턴스의 인증서를 사용하여 해당 인스턴스의 엔드포인트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c39fb-109">Create an endpoint for the server instance using its certificate.</span></span>  
  
4.  <span data-ttu-id="c39fb-110">인증서를 파일에 백업한 다음 안전한 다른 시스템으로 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="c39fb-110">Back up the certificate to a file and securely copy it to the other system or systems.</span></span>  
  
 <span data-ttu-id="c39fb-111">파트너와 미러링 모니터 각각에 대해 이러한 단계를 완료해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c39fb-111">You must complete these steps for each partner and the witness, if there is one.</span></span>  
  
 <span data-ttu-id="c39fb-112">다음 절차에서 이러한 단계를 자세히 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="c39fb-112">The following procedure describes these steps in detail.</span></span> <span data-ttu-id="c39fb-113">각 단계에서는 HOST_A라는 시스템에서 서버 인스턴스를 구성하는 예를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="c39fb-113">For each step, the procedure provides an example for configuring a server instance on a system named HOST_A.</span></span> <span data-ttu-id="c39fb-114">예 섹션에서는 HOST_B라는 시스템에 또 다른 서버 인스턴스를 구성하는 동일한 단계를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="c39fb-114">The accompanying Example section demonstrates the same steps for another server instance on a system named HOST_B.</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="c39fb-115">절차</span><span class="sxs-lookup"><span data-stu-id="c39fb-115">Procedure</span></span>  
  
#### <a name="to-configure-server-instances-for-outbound-mirroring-connections-on-host_a"></a><span data-ttu-id="c39fb-116">아웃바운드 미러링 연결을 위한 서버 인스턴스를 구성하려면(HOST_A)</span><span class="sxs-lookup"><span data-stu-id="c39fb-116">To configure server instances for outbound mirroring connections (On HOST_A)</span></span>  
  
1.  <span data-ttu-id="c39fb-117">**master** 데이터베이스에 데이터베이스 마스터 키가 없으면 새로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c39fb-117">On the **master** database, create the database Master Key, if none exists.</span></span> <span data-ttu-id="c39fb-118">데이터베이스의 기존 키를 보려면 [sys.symmetric_keys](/sql/relational-databases/system-catalog-views/sys-symmetric-keys-transact-sql) 카탈로그 뷰를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="c39fb-118">To view the existing keys for a database, use the [sys.symmetric_keys](/sql/relational-databases/system-catalog-views/sys-symmetric-keys-transact-sql) catalog view.</span></span>  
  
     <span data-ttu-id="c39fb-119">데이터베이스 마스터 키를 만들려면 다음 [!INCLUDE[tsql](../../includes/tsql-md.md)] 명령을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="c39fb-119">To create the database Master Key, use the following [!INCLUDE[tsql](../../includes/tsql-md.md)] command:</span></span>  
  
    ```  
    CREATE MASTER KEY ENCRYPTION BY PASSWORD = '<1_Strong_Password!>';  
    GO  
    ```  
  
     <span data-ttu-id="c39fb-120">고유하고 강력한 암호를 사용하고 암호를 기록하여 안전한 곳에 보관합니다.</span><span class="sxs-lookup"><span data-stu-id="c39fb-120">Use a unique, strong password, and record it in a safe place.</span></span>  
  
     <span data-ttu-id="c39fb-121">자세한 내용은 [CREATE MASTER KEY&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-master-key-transact-sql) 및 [데이터베이스 마스터 키 만들기](../../relational-databases/security/encryption/create-a-database-master-key.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c39fb-121">For more information, see [CREATE MASTER KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-master-key-transact-sql) and [Create a Database Master Key](../../relational-databases/security/encryption/create-a-database-master-key.md).</span></span>  
  
2.  <span data-ttu-id="c39fb-122">**master** 데이터베이스에서 데이터베이스 미러링을 위한 아웃바운드 연결에 사용할 암호화된 인증서를 서버 인스턴스에 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c39fb-122">In the **master** database, create an encrypted certificate on the server instance to use for its outbound connections for database mirroring.</span></span>  
  
     <span data-ttu-id="c39fb-123">예를 들어 HOST_A 시스템의 인증서를 만들려면 다음 코드를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="c39fb-123">For example, to create a certificate for the HOST_A system.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="c39fb-124">인증서를 1년 이상 사용하려는 경우 CREATE CERTIFICATE 문에 EXPIRY_DATE 옵션을 사용하여 UTC 시간으로 만료 날짜를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c39fb-124">If you intend to use the certificate for more than one year, specify the expiry date in UTC time by using the EXPIRY_DATE option in your CREATE CERTIFICATE statement.</span></span> <span data-ttu-id="c39fb-125">또한 SQL Server Management Studio를 사용하여 인증서 만료 시 경고를 표시하는 정책 기반 관리 규칙을 만드는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="c39fb-125">Also, we recommend that you use SQL Server Management Studio to create a Policy-Based Management rule to alert you when your certificates are expiring.</span></span> <span data-ttu-id="c39fb-126">정책 관리의 **새 조건 만들기** 대화 상자를 사용하여 **@ExpirationDate** 패싯의 **@ExpirationDate** 필드에 이 규칙을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c39fb-126">Using the Policy Management **Create New Condition** dialog box, create this rule on the **@ExpirationDate** field of the **Certificate** facet.</span></span> <span data-ttu-id="c39fb-127">자세한 내용은 [정책 기반 관리를 사용하여 서버 관리](../../relational-databases/policy-based-management/administer-servers-by-using-policy-based-management.md) 및 [SQL Server 보안 설정](../../relational-databases/security/securing-sql-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c39fb-127">For more information, see [Administer Servers by Using Policy-Based Management](../../relational-databases/policy-based-management/administer-servers-by-using-policy-based-management.md) and [Securing SQL Server](../../relational-databases/security/securing-sql-server.md).</span></span>  
  
    ```  
    USE master;  
    CREATE CERTIFICATE HOST_A_cert   
       WITH SUBJECT = 'HOST_A certificate for database mirroring',   
       EXPIRY_DATE = '11/30/2013';  
    GO  
    ```  
  
     <span data-ttu-id="c39fb-128">자세한 내용은 [CREATE CERTIFICATE&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-certificate-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c39fb-128">For more information, see [CREATE CERTIFICATE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-certificate-transact-sql).</span></span>  
  
     <span data-ttu-id="c39fb-129">**master** 데이터베이스에 있는 인증서를 보려면 다음 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="c39fb-129">To view the certificates in the **master** database, you can use the following [!INCLUDE[tsql](../../includes/tsql-md.md)] statements:</span></span>  
  
    ```  
    USE master;  
    SELECT * FROM sys.certificates;  
    ```  
  
     <span data-ttu-id="c39fb-130">자세한 내용은 [sys.certificates&#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-certificates-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c39fb-130">For more information, see [sys.certificates &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-certificates-transact-sql).</span></span>  
  
3.  <span data-ttu-id="c39fb-131">서버 인스턴스마다 데이터베이스 미러링 엔드포인트가 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="c39fb-131">Ensure that the database mirroring endpoint exist on each of the server instances.</span></span>  
  
     <span data-ttu-id="c39fb-132">서버 인스턴스의 데이터베이스 미러링 엔드포인트가 이미 있으면 서버 인스턴스에서 설정하는 다른 모든 세션에 해당 엔드포인트를 다시 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c39fb-132">If a database mirroring endpoint already exists for the server instance, you should reuse that endpoint for any other sessions you establish on the server instance.</span></span> <span data-ttu-id="c39fb-133">서버 인스턴스에 데이터베이스 미러링 엔드포인트가 있는지 확인하고 해당 구성을 보려면 다음 문을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="c39fb-133">To determine whether a database mirroring endpoint exists on a server instance and to view its configuration, use the following statement:</span></span>  
  
    ```  
    SELECT name, role_desc, state_desc, connection_auth_desc, encryption_algorithm_desc   
       FROM sys.database_mirroring_endpoints;  
    ```  
  
     <span data-ttu-id="c39fb-134">엔드포인트가 없으면 아웃바운드 연결에는 이 인증서를 사용하고 다른 시스템의 확인에는 이 인증서의 자격 증명을 사용하는 엔드포인트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c39fb-134">If no endpoint exists, create an endpoint that uses this certificate for outbound connections and that uses the certificate's credentials for verification on the other system.</span></span> <span data-ttu-id="c39fb-135">이 엔드포인트는 서버 인스턴스가 참여하는 모든 미러링 세션에 사용되는 서버 차원의 엔드포인트입니다.</span><span class="sxs-lookup"><span data-stu-id="c39fb-135">This is a server-wide endpoint that is used by all mirroring sessions in which the server instance participates.</span></span>  
  
     <span data-ttu-id="c39fb-136">예를 들어 HOST_A에 예제 서버 인스턴스의 미러링 엔드포인트를 만들려면 다음 코드를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="c39fb-136">For example, to create a mirroring endpoint for the example server instance on HOST_A.</span></span>  
  
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
  
     <span data-ttu-id="c39fb-137">자세한 내용은 [CREATE ENDPOINT&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-endpoint-transact-sql)과 함께 작동하도록 Service Broker를 구성하는 방법에 대한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="c39fb-137">For more information, see [CREATE ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-endpoint-transact-sql).</span></span>  
  
4.  <span data-ttu-id="c39fb-138">인증서를 백업하고 다른 시스템에 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="c39fb-138">Back up the certificate and copy it to the other system or systems.</span></span> <span data-ttu-id="c39fb-139">다른 시스템에서 인바운드 연결을 구성하는 데 이 인증서가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="c39fb-139">This is necessary in order to configure inbound connections on the other system.</span></span>  
  
    ```  
    BACKUP CERTIFICATE HOST_A_cert TO FILE = 'C:\HOST_A_cert.cer';  
    GO  
    ```  
  
     <span data-ttu-id="c39fb-140">자세한 내용은 [BACKUP CERTIFICATE&#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-certificate-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c39fb-140">For more information, see [BACKUP CERTIFICATE &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-certificate-transact-sql).</span></span>  
  
     <span data-ttu-id="c39fb-141">안전한 방법으로 이 인증서를 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="c39fb-141">Copy this certificate using any secure method you choose.</span></span> <span data-ttu-id="c39fb-142">모든 인증서를 안전하게 보관하는 데 많은 주의를 기울여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c39fb-142">Be extremely careful to keep all of your certificates secure.</span></span>  
  
 <span data-ttu-id="c39fb-143">앞 단계의 예제 코드에서는 HOST_A에 아웃바운드 연결을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="c39fb-143">The example code in the preceding steps configure outbound connections on HOST_A.</span></span>  
  
 <span data-ttu-id="c39fb-144">이제 HOST_B에 대해 동일한 아웃바운드 단계를 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c39fb-144">You now need to perform the equivalent outbound steps for HOST_B.</span></span> <span data-ttu-id="c39fb-145">이러한 단계는 다음 예 섹션에 설명되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c39fb-145">These steps are illustrated in the following Example section.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c39fb-146">예제</span><span class="sxs-lookup"><span data-stu-id="c39fb-146">Example</span></span>  
 <span data-ttu-id="c39fb-147">다음 예에서는 아웃바운드 연결을 위한 HOST_B 구성을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="c39fb-147">The following example demonstrates configuring HOST_B for outbound connections.</span></span>  
  
```  
USE master;  
--Create the database Master Key, if needed.  
CREATE MASTER KEY ENCRYPTION BY PASSWORD = '<Strong_Password_#2>';  
GO  
-- Make a certifcate on HOST_B server instance.  
CREATE CERTIFICATE HOST_B_cert   
   WITH SUBJECT = 'HOST_B certificate for database mirroring',   
   EXPIRY_DATE = '11/30/2013';  
GO  
--Create a mirroring endpoint for the server instance on HOST_B.  
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
--Backup HOST_B certificate.  
BACKUP CERTIFICATE HOST_B_cert TO FILE = 'C:\HOST_B_cert.cer';  
GO   
--Using any secure copy method, copy C:\HOST_B_cert.cer to HOST_A.  
```  
  
 <span data-ttu-id="c39fb-148">원하는 안전한 방법으로 인증서를 다른 시스템에 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="c39fb-148">Copy the certificate to the other system using any secure method you choose.</span></span> <span data-ttu-id="c39fb-149">모든 인증서를 안전하게 보관하는 데 많은 주의를 기울여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c39fb-149">Be extremely careful to keep all of your certificates secure.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="c39fb-150">아웃바운드 연결을 설정한 후에는 다른 서버 인스턴스에 대해 각 서버 인스턴스에서 인바운드 연결을 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c39fb-150">After you set up outbound connections, you must configure inbound connections on each server instance for the other server instance or instances.</span></span> <span data-ttu-id="c39fb-151">자세햔 내용은 [데이터베이스 미러링 엔드포인트의 인바운드 연결에 대한 인증서 사용 허용&#40;Transact-SQL&#41;](database-mirroring-use-certificates-for-inbound-connections.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c39fb-151">For more information, see [Allow a Database Mirroring Endpoint to Use Certificates for Inbound Connections &#40;Transact-SQL&#41;](database-mirroring-use-certificates-for-inbound-connections.md).</span></span>  
  
 <span data-ttu-id="c39fb-152">Transact-SQL 예제를 포함하여 미러 데이터베이스를 만드는 방법은 [미러 데이터베이스의 미러링 준비&#40;SQL Server&#41;](prepare-a-mirror-database-for-mirroring-sql-server.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c39fb-152">For information on creating a mirror database, including a Transact-SQL example, see [Prepare a Mirror Database for Mirroring &#40;SQL Server&#41;](prepare-a-mirror-database-for-mirroring-sql-server.md).</span></span>  
  
 <span data-ttu-id="c39fb-153">고성능 모드 세션을 설정하는 Transact-SQL 예는 [예제: 인증서를 사용하여 데이터베이스 미러링 설정&#40;Transact-SQL&#41;](example-setting-up-database-mirroring-using-certificates-transact-sql.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c39fb-153">For a Transact-SQL example of establishing a high-performance mode session, see [Example: Setting Up Database Mirroring Using Certificates &#40;Transact-SQL&#41;](example-setting-up-database-mirroring-using-certificates-transact-sql.md).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="c39fb-154">.NET Framework 보안</span><span class="sxs-lookup"><span data-stu-id="c39fb-154">.NET Framework Security</span></span>  
 <span data-ttu-id="c39fb-155">네트워크 보안을 보장할 수 없는 경우 데이터베이스 미러링 연결에 암호화를 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="c39fb-155">Unless you can guarantee that your network is secure, we recommend that you use encryption for database mirroring connections.</span></span>  
  
 <span data-ttu-id="c39fb-156">인증서를 다른 시스템으로 복사할 때는 안전한 복사 방법을 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="c39fb-156">When copying a certificate to another system, use a secure copy method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c39fb-157">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c39fb-157">See Also</span></span>  
 <span data-ttu-id="c39fb-158">[암호화 알고리즘 선택](../../relational-databases/security/encryption/choose-an-encryption-algorithm.md) </span><span class="sxs-lookup"><span data-stu-id="c39fb-158">[Choose an Encryption Algorithm](../../relational-databases/security/encryption/choose-an-encryption-algorithm.md) </span></span>  
 <span data-ttu-id="c39fb-159">[미러 데이터베이스의 미러링 준비&#40;SQL Server&#41;](prepare-a-mirror-database-for-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="c39fb-159">[Prepare a Mirror Database for Mirroring &#40;SQL Server&#41;](prepare-a-mirror-database-for-mirroring-sql-server.md) </span></span>  
 <span data-ttu-id="c39fb-160">[ALTER ENDPOINT&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-endpoint-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c39fb-160">[ALTER ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-endpoint-transact-sql) </span></span>  
 <span data-ttu-id="c39fb-161">[예: 인증서를 사용하여 데이터베이스 미러링 설정&#40;Transact-SQL&#41;](example-setting-up-database-mirroring-using-certificates-transact-sql.md) </span><span class="sxs-lookup"><span data-stu-id="c39fb-161">[Example: Setting Up Database Mirroring Using Certificates &#40;Transact-SQL&#41;](example-setting-up-database-mirroring-using-certificates-transact-sql.md) </span></span>  
 <span data-ttu-id="c39fb-162">[데이터베이스 미러링 엔드포인트&#40;SQL Server&#41;](the-database-mirroring-endpoint-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="c39fb-162">[The Database Mirroring Endpoint &#40;SQL Server&#41;](the-database-mirroring-endpoint-sql-server.md) </span></span>  
 <span data-ttu-id="c39fb-163">[데이터베이스 미러링 구성 문제 해결&#40;SQL Server&#41;](troubleshoot-database-mirroring-configuration-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="c39fb-163">[Troubleshoot Database Mirroring Configuration &#40;SQL Server&#41;](troubleshoot-database-mirroring-configuration-sql-server.md) </span></span>  
 [<span data-ttu-id="c39fb-164">암호화된 미러 데이터베이스 설정</span><span class="sxs-lookup"><span data-stu-id="c39fb-164">Set Up an Encrypted Mirror Database</span></span>](set-up-an-encrypted-mirror-database.md)  
  
  
