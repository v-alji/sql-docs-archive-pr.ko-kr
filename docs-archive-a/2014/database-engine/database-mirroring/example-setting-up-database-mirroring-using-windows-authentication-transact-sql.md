---
title: '예제: Windows 인증을 사용 하 여 데이터베이스 미러링 설정 (Transact-sql) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- database mirroring [SQL Server], deployment
- Windows authentication [SQL Server]
- authentication [SQL Server], database mirroring
- database mirroring [SQL Server], security
ms.assetid: 35800769-aede-4aac-b077-0e0e487e302f
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 95df855e8e41c5937aae02884c71792537eb2bfc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647194"
---
# <a name="example-setting-up-database-mirroring-using-windows-authentication-transact-sql"></a><span data-ttu-id="46e6a-102">예제: Windows 인증을 사용하여 데이터베이스 미러링 설정(Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="46e6a-102">Example: Setting Up Database Mirroring Using Windows Authentication (Transact-SQL)</span></span>
  <span data-ttu-id="46e6a-103">이 예에서는 Windows 인증을 사용하는 미러링 모니터 서버가 있는 데이터베이스 미러링 세션을 만드는 데 필요한 모든 단계를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="46e6a-103">This example shows all the stages required to create a database mirroring session with a witness using Windows Authentication.</span></span> <span data-ttu-id="46e6a-104">이 항목의 예에서는 [!INCLUDE[tsql](../../includes/tsql-md.md)]을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="46e6a-104">The examples in this topic use [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="46e6a-105">[!INCLUDE[tsql](../../includes/tsql-md.md)] 단계를 사용하는 대신 데이터베이스 미러링 보안 구성 마법사를 데이터베이스 미러링 설치에 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="46e6a-105">Note that as an alternative to using [!INCLUDE[tsql](../../includes/tsql-md.md)] steps, you can use the Configure Database Mirroring Security Wizard for database mirroring setup.</span></span> <span data-ttu-id="46e6a-106">자세한 내용은 이 항목의 뒷부분에 나오는 [Windows 인증을 사용하여 데이터베이스 미러링 세션 구성&#40;SQL Server Management Studio&#41;](establish-database-mirroring-session-windows-authentication.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="46e6a-106">For more information, see [Establish a Database Mirroring Session Using Windows Authentication &#40;SQL Server Management Studio&#41;](establish-database-mirroring-session-windows-authentication.md).</span></span>  
  
## <a name="prerequisite"></a><span data-ttu-id="46e6a-107">필수 요소</span><span class="sxs-lookup"><span data-stu-id="46e6a-107">Prerequisite</span></span>  
 <span data-ttu-id="46e6a-108">예에서는 기본적으로 단순 복구 모델을 사용하는 **AdventureWorks** 예제 데이터베이스를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="46e6a-108">The example uses the **AdventureWorks** sample database, which uses the simple recovery model by default.</span></span> <span data-ttu-id="46e6a-109">데이터베이스 미러링을 이 데이터베이스에 사용하려면 전체 복구 모델을 사용하도록 변경해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="46e6a-109">To use database mirroring with this database, you must alter it to use the full recovery model.</span></span> <span data-ttu-id="46e6a-110">[!INCLUDE[tsql](../../includes/tsql-md.md)]에서 복구 모델을 변경하려면 다음과 같이 ALTER DATABASE 문을 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="46e6a-110">To do this in [!INCLUDE[tsql](../../includes/tsql-md.md)], use the ALTER DATABASE statement, as follows:</span></span>  
  
```  
USE master;  
GO  
ALTER DATABASE AdventureWorks   
SET RECOVERY FULL;  
GO  
```  
  
 <span data-ttu-id="46e6a-111">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서 복구 모델을 변경하는 방법에 대한 자세한 내용은 [데이터베이스 복구 모델 보기 또는 변경&#40;SQL Server&#41;](../../relational-databases/backup-restore/view-or-change-the-recovery-model-of-a-database-sql-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="46e6a-111">For information on changing the recovery model in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], see [View or Change the Recovery Model of a Database &#40;SQL Server&#41;](../../relational-databases/backup-restore/view-or-change-the-recovery-model-of-a-database-sql-server.md).</span></span>  
  
### <a name="permissions"></a><span data-ttu-id="46e6a-112">사용 권한</span><span class="sxs-lookup"><span data-stu-id="46e6a-112">Permissions</span></span>  
 <span data-ttu-id="46e6a-113">데이터베이스에 대한 ALTER 권한과 CREATE ENDPOINT 권한 또는 **sysadmin** 고정 서버 역할의 멤버 자격이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="46e6a-113">Requires ALTER permission on the database and CREATE ENDPOINT permission, or membership in the **sysadmin** fixed server role.</span></span>  
  
## <a name="example"></a><span data-ttu-id="46e6a-114">예제</span><span class="sxs-lookup"><span data-stu-id="46e6a-114">Example</span></span>  
 <span data-ttu-id="46e6a-115">이 예에서는 파트너 2개와 미러링 모니터 서버가 컴퓨터 시스템 3대의 기본 서버 인스턴스입니다.</span><span class="sxs-lookup"><span data-stu-id="46e6a-115">In this example, the two partners and the witness are the default server instances on three computer systems.</span></span> <span data-ttu-id="46e6a-116">3개의 서버 인스턴스에서는 같은 Windows 도메인을 실행하지만 예에 나오는 미러링 모니터 서버 인스턴스에는 다른 사용자 계정(시작 서비스 계정으로 사용)이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="46e6a-116">The three server instances run the same Windows domain, but the user account (used as the startup service account) is different for the example's witness server instance.</span></span>  
  
 <span data-ttu-id="46e6a-117">다음 표에서는 이 예에 사용된 값을 요약합니다.</span><span class="sxs-lookup"><span data-stu-id="46e6a-117">The following table summarizes the values used in this example.</span></span>  
  
|<span data-ttu-id="46e6a-118">초기 미러링 역할</span><span class="sxs-lookup"><span data-stu-id="46e6a-118">Initial mirroring role</span></span>|<span data-ttu-id="46e6a-119">호스트 시스템</span><span class="sxs-lookup"><span data-stu-id="46e6a-119">Host system</span></span>|<span data-ttu-id="46e6a-120">도메인 사용자 계정</span><span class="sxs-lookup"><span data-stu-id="46e6a-120">Domain user account</span></span>|  
|----------------------------|-----------------|-------------------------|  
|<span data-ttu-id="46e6a-121">주 서버</span><span class="sxs-lookup"><span data-stu-id="46e6a-121">Principal</span></span>|<span data-ttu-id="46e6a-122">PARTNERHOST1</span><span class="sxs-lookup"><span data-stu-id="46e6a-122">PARTNERHOST1</span></span>|<span data-ttu-id="46e6a-123">*\<Mydomain>\\<dbousername\>*</span><span class="sxs-lookup"><span data-stu-id="46e6a-123">*\<Mydomain>\\<dbousername\>*</span></span>|  
|<span data-ttu-id="46e6a-124">미러</span><span class="sxs-lookup"><span data-stu-id="46e6a-124">Mirror</span></span>|<span data-ttu-id="46e6a-125">PARTNERHOST5</span><span class="sxs-lookup"><span data-stu-id="46e6a-125">PARTNERHOST5</span></span>|<span data-ttu-id="46e6a-126">*\<Mydomain>\\<dbousername\>*</span><span class="sxs-lookup"><span data-stu-id="46e6a-126">*\<Mydomain>\\<dbousername\>*</span></span>|  
|<span data-ttu-id="46e6a-127">미러링 모니터</span><span class="sxs-lookup"><span data-stu-id="46e6a-127">Witness</span></span>|<span data-ttu-id="46e6a-128">WITNESSHOST4</span><span class="sxs-lookup"><span data-stu-id="46e6a-128">WITNESSHOST4</span></span>|<span data-ttu-id="46e6a-129">*\<Somedomain>\\<witnessuser\>*</span><span class="sxs-lookup"><span data-stu-id="46e6a-129">*\<Somedomain>\\<witnessuser\>*</span></span>|  
  
1.  <span data-ttu-id="46e6a-130">주 서버 인스턴스(PARTNERHOST1의 기본 인스턴스)에 엔드포인트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="46e6a-130">Create an endpoint on the principal server instance (default instance on PARTNERHOST1).</span></span>  
  
    ```  
    CREATE ENDPOINT Endpoint_Mirroring  
        STATE=STARTED   
        AS TCP (LISTENER_PORT=7022)   
        FOR DATABASE_MIRRORING (ROLE=PARTNER)  
    GO  
    --Partners under same domain user; login already exists in master.  
    --Create a login for the witness server instance,  
    --which is running as Somedomain\witnessuser:  
    USE master ;  
    GO  
    CREATE LOGIN [Somedomain\witnessuser] FROM WINDOWS ;  
    GO  
    -- Grant connect permissions on endpoint to login account of witness.  
    GRANT CONNECT ON ENDPOINT::Endpoint_Mirroring TO [Somedomain\witnessuser];  
    --Grant connect permissions on endpoint to login account of partners.  
    GRANT CONNECT ON ENDPOINT::Endpoint_Mirroring TO [Mydomain\dbousername];  
    GO  
    ```  
  
2.  <span data-ttu-id="46e6a-131">미러 서버 인스턴스(PARTNERHOST5의 기본 인스턴스)에 엔드포인트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="46e6a-131">Create an endpoint on the mirror server instance (default instance on PARTNERHOST5).</span></span>  
  
    ```  
    CREATE ENDPOINT Endpoint_Mirroring  
        STATE=STARTED   
        AS TCP (LISTENER_PORT=7022)   
        FOR DATABASE_MIRRORING (ROLE=ALL)  
    GO  
    --Partners under same domain user; login already exists in master.  
    --Create a login for the witness server instance,  
    --which is running as Somedomain\witnessuser:  
    USE master ;  
    GO  
    CREATE LOGIN [Somedomain\witnessuser] FROM WINDOWS ;  
    GO  
    --Grant connect permissions on endpoint to login account of witness.  
    GRANT CONNECT ON ENDPOINT::Endpoint_Mirroring TO [Somedomain\witnessuser];  
    --Grant connect permissions on endpoint to login account of partners.  
    GRANT CONNECT ON ENDPOINT::Endpoint_Mirroring TO [Mydomain\dbousername];  
    GO  
    ```  
  
3.  <span data-ttu-id="46e6a-132">미러링 모니터 서버 인스턴스(WITNESSHOST4의 기본 인스턴스)에 엔드포인트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="46e6a-132">Create an endpoint on the witness server instance (default instance on WITNESSHOST4).</span></span>  
  
    ```  
    CREATE ENDPOINT Endpoint_Mirroring  
        STATE=STARTED   
        AS TCP (LISTENER_PORT=7022)   
        FOR DATABASE_MIRRORING (ROLE=WITNESS)  
    GO  
    --Create a login for the partner server instances,  
    --which are both running as Mydomain\dbousername:  
    USE master ;  
    GO  
    CREATE LOGIN [Mydomain\dbousername] FROM WINDOWS ;  
    GO  
    --Grant connect permissions on endpoint to login account of partners.  
    GRANT CONNECT ON ENDPOINT::Endpoint_Mirroring TO [Mydomain\dbousername];  
    GO  
    ```  
  
4.  <span data-ttu-id="46e6a-133">미러 데이터베이스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="46e6a-133">Create the mirror database.</span></span> <span data-ttu-id="46e6a-134">자세한 내용은 [미러 데이터베이스의 미러링 준비&#40;SQL Server&#41;](prepare-a-mirror-database-for-mirroring-sql-server.md)을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="46e6a-134">For more information, see [Prepare a Mirror Database for Mirroring &#40;SQL Server&#41;](prepare-a-mirror-database-for-mirroring-sql-server.md).</span></span>  
  
5.  <span data-ttu-id="46e6a-135">PARTNERHOST5의 미러 서버 인스턴스에서 PARTNERHOST1의 서버 인스턴스를 초기 주 서버 인스턴스로 만들어 파트너로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="46e6a-135">On the mirror server instance on PARTNERHOST5, set the server instance on PARTNERHOST1 as the partner (making it the initial principal server instance).</span></span>  
  
    ```  
    ALTER DATABASE AdventureWorks   
        SET PARTNER =   
        'TCP://PARTNERHOST1.COM:7022'  
    GO  
    ```  
  
6.  <span data-ttu-id="46e6a-136">PARTNERHOST1의 주 서버 인스턴스에서 PARTNERHOST5의 서버 인스턴스를 초기 미러 서버 인스턴스로 만들어 파트너로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="46e6a-136">On the principal server instance on PARTNERHOST1, set the server instance on PARTNERHOST5 as the partner (making it the initial mirror server instance).</span></span>  
  
    ```  
    ALTER DATABASE AdventureWorks   
        SET PARTNER = 'TCP://PARTNERHOST5.COM:7022'  
    GO  
    ```  
  
7.  <span data-ttu-id="46e6a-137">주 서버에서 WITNESSHOST4에 있는 미러링 모니터 서버를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="46e6a-137">On the principal server, set the witness (which is on WITNESSHOST4).</span></span>  
  
    ```  
    ALTER DATABASE AdventureWorks   
        SET WITNESS =   
        'TCP://WITNESSHOST4.COM:7022'  
    GO  
    ```  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="46e6a-138">관련 작업</span><span class="sxs-lookup"><span data-stu-id="46e6a-138">Related Tasks</span></span>  
  
-   [<span data-ttu-id="46e6a-139">미러 데이터베이스의 미러링 준비&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="46e6a-139">Prepare a Mirror Database for Mirroring &#40;SQL Server&#41;</span></span>](prepare-a-mirror-database-for-mirroring-sql-server.md)  
  
-   [<span data-ttu-id="46e6a-140">데이터베이스 미러링 보안 구성 마법사 시작&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="46e6a-140">Start the Configuring Database Mirroring Security Wizard &#40;SQL Server Management Studio&#41;</span></span>](start-the-configuring-database-mirroring-security-wizard.md)  
  
-   [<span data-ttu-id="46e6a-141">Trustworthy 속성을 사용하도록 미러 데이터베이스 설정&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="46e6a-141">Set Up a Mirror Database to Use the Trustworthy Property &#40;Transact-SQL&#41;</span></span>](set-up-a-mirror-database-to-use-the-trustworthy-property-transact-sql.md)  
  
-   [<span data-ttu-id="46e6a-142">데이터베이스 미러링 엔드포인트의 아웃바운드 연결에 대한 인증서 사용 허용&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="46e6a-142">Allow a Database Mirroring Endpoint to Use Certificates for Outbound Connections &#40;Transact-SQL&#41;</span></span>](database-mirroring-use-certificates-for-outbound-connections.md)  
  
-   [<span data-ttu-id="46e6a-143">데이터베이스 미러링 엔드포인트의 인바운드 연결에 대한 인증서 사용 허용&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="46e6a-143">Allow a Database Mirroring Endpoint to Use Certificates for Inbound Connections &#40;Transact-SQL&#41;</span></span>](database-mirroring-use-certificates-for-inbound-connections.md)  
  
-   [<span data-ttu-id="46e6a-144">예: 인증서를 사용하여 데이터베이스 미러링 설정&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="46e6a-144">Example: Setting Up Database Mirroring Using Certificates &#40;Transact-SQL&#41;</span></span>](example-setting-up-database-mirroring-using-certificates-transact-sql.md)  
  
## <a name="see-also"></a><span data-ttu-id="46e6a-145">참고 항목</span><span class="sxs-lookup"><span data-stu-id="46e6a-145">See Also</span></span>  
 <span data-ttu-id="46e6a-146">[ALTER DATABASE &#40;Transact-SQL &#41;](/sql/t-sql/statements/alter-database-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="46e6a-146">[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) </span></span>  
 <span data-ttu-id="46e6a-147">[데이터베이스 미러링 엔드포인트&#40;SQL Server&#41;](the-database-mirroring-endpoint-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="46e6a-147">[The Database Mirroring Endpoint &#40;SQL Server&#41;](the-database-mirroring-endpoint-sql-server.md) </span></span>  
 <span data-ttu-id="46e6a-148">[데이터베이스 미러링 및 AlwaysOn 가용성 그룹 &#40;SQL Server에 대 한 전송 보안&#41;](transport-security-database-mirroring-always-on-availability.md) </span><span class="sxs-lookup"><span data-stu-id="46e6a-148">[Transport Security for Database Mirroring and AlwaysOn Availability Groups &#40;SQL Server&#41;](transport-security-database-mirroring-always-on-availability.md) </span></span>  
 <span data-ttu-id="46e6a-149">[다른 서버 인스턴스에서 데이터베이스를 사용할 수 있도록 할 때 메타데이터 관리&#40;SQL Server&#41;](../../relational-databases/databases/manage-metadata-when-making-a-database-available-on-another-server.md) </span><span class="sxs-lookup"><span data-stu-id="46e6a-149">[Manage Metadata When Making a Database Available on Another Server Instance &#40;SQL Server&#41;](../../relational-databases/databases/manage-metadata-when-making-a-database-available-on-another-server.md) </span></span>  
 [<span data-ttu-id="46e6a-150">SQL Server 데이터베이스 엔진 및 Azure SQL Database 보안 센터</span><span class="sxs-lookup"><span data-stu-id="46e6a-150">Security Center for SQL Server Database Engine and Azure SQL Database</span></span>](../../relational-databases/security/security-center-for-sql-server-database-engine-and-azure-sql-database.md)  
  
  
