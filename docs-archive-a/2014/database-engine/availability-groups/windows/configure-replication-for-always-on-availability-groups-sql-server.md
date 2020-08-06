---
title: Always On 가용성 그룹에 대한 복제 구성(SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], interoperability
- replication [SQL Server], AlwaysOn Availability Groups
ms.assetid: 4e001426-5ae0-4876-85ef-088d6e3fb61c
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 916458d2d6b8fbba81940257ee85ffe014d1f12e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87729831"
---
# <a name="configure-replication-for-always-on-availability-groups-sql-server"></a><span data-ttu-id="b9ac0-102">Always On 가용성 그룹에 대한 복제 구성(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="b9ac0-102">Configure Replication for Always On Availability Groups (SQL Server)</span></span>
  <span data-ttu-id="b9ac0-103">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 복제 및 AlwaysOn 가용성 그룹을 구성하는 과정은 7단계로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="b9ac0-103">Configuring [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] replication and AlwaysOn availability groups involves seven steps.</span></span> <span data-ttu-id="b9ac0-104">각 단계에 대해서는 다음 섹션에서 자세하게 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="b9ac0-104">Each step is described in more detail in the following sections.</span></span>  

##  <a name="1-configure-the-database-publications-and-subscriptions"></a><a name="step1"></a> <span data-ttu-id="b9ac0-105">1. 데이터베이스 게시 및 구독 구성</span><span class="sxs-lookup"><span data-stu-id="b9ac0-105">1. Configure the Database Publications and Subscriptions</span></span>  

### <a name="configure-the-distributor"></a><span data-ttu-id="b9ac0-106">배포자 구성</span><span class="sxs-lookup"><span data-stu-id="b9ac0-106">Configure the distributor</span></span>
  
 <span data-ttu-id="b9ac0-107">배포자는 게시 데이터베이스가 멤버로 속해 있거나 속하게 될 가용성 그룹의 현재 또는 의도된 복제본에 대한 호스트가 아니어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b9ac0-107">The distributor should not be a host for any of the current (or intended) replicas of the availability group that the publishing database is (or will become) a member of.</span></span>  
  
1.  <span data-ttu-id="b9ac0-108">배포자에서 배포를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="b9ac0-108">Configure distribution at the distributor.</span></span> <span data-ttu-id="b9ac0-109">구성에 저장 프로시저를 사용하는 경우 `sp_adddistributor`를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="b9ac0-109">If stored procedures are being used for configuration, run `sp_adddistributor`.</span></span> <span data-ttu-id="b9ac0-110">*@password*매개 변수를 사용 하 여 원격 게시자가 배포자에 연결할 때 사용 되는 암호를 식별 합니다.</span><span class="sxs-lookup"><span data-stu-id="b9ac0-110">Use the *@password* parameter to identify the password that will be used when a remote publisher connects to the distributor.</span></span> <span data-ttu-id="b9ac0-111">암호는 원격 배포자를 설정할 때 각 원격 게시자에서도 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="b9ac0-111">The password will also be needed at each remote publisher when the remote distributor is set up.</span></span>  
  
    ```sql
    USE master;  
    GO  
    EXEC sys.sp_adddistributor  
        @distributor = 'MyDistributor',  
        @password = '**Strong password for distributor**';  
    ```  
  
2.  <span data-ttu-id="b9ac0-112">배포자에서 배포 데이터베이스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b9ac0-112">Create the distribution database at the distributor.</span></span> <span data-ttu-id="b9ac0-113">구성에 저장 프로시저를 사용하는 경우 `sp_adddistributiondb`를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="b9ac0-113">If stored procedures are being used for configuration, run `sp_adddistributiondb`.</span></span>  
  
    ```  
    USE master;  
    GO  
    EXEC sys.sp_adddistributiondb  
        @database = 'distribution',  
        @security_mode = 1;  
    ```  
  
3.  <span data-ttu-id="b9ac0-114">원격 게시자를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="b9ac0-114">Configure the remote publisher.</span></span> <span data-ttu-id="b9ac0-115">배포자 구성에 저장 프로시저를 사용하는 경우 `sp_adddistpublisher`를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="b9ac0-115">If stored procedures are being used to configure the distributor, run `sp_adddistpublisher`.</span></span> <span data-ttu-id="b9ac0-116">*@security_mode*매개 변수는 복제 에이전트에서 실행 되는 게시자 유효성 검사 저장 프로시저가 현재 주 복제본에 연결 하는 방법을 결정 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b9ac0-116">The *@security_mode* parameter is used to determine how the publisher validation stored procedure that is run from the replication agents, connects to the current primary.</span></span> <span data-ttu-id="b9ac0-117">1로 설정하면 Windows 인증을 사용하여 현재 주 복제본에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="b9ac0-117">If set to 1 Windows authentication is used to connect to the current primary.</span></span> <span data-ttu-id="b9ac0-118">0으로 설정 되 면 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 지정 된 및 값과 함께 인증을 사용 *@login* *@password* 합니다.</span><span class="sxs-lookup"><span data-stu-id="b9ac0-118">If set to 0, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] authentication is used with the specified *@login* and *@password* values.</span></span> <span data-ttu-id="b9ac0-119">지정된 로그인 및 암호가 각 보조 복제본에서 유효해야만 유효성 검사 저장 프로시저가 해당 복제본에 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b9ac0-119">The login and password specified must be valid at each secondary replica for the validation stored procedure to successfully connect to that replica.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="b9ac0-120">수정된 복제 에이전트가 배포자와는 다른 컴퓨터에서 실행될 경우 Windows 인증으로 주 복제본에 연결하려면 복제본 호스트 컴퓨터 간 통신에 대해 Kerberos 인증이 구성되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b9ac0-120">If any modified replication agents run on a computer other than the distributor, use of Windows authentication for the connection to the primary will require Kerberos authentication to be configured for the communication between the replica host computers.</span></span> <span data-ttu-id="b9ac0-121">현재 주 복제본 연결에 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 로그인을 사용하는 경우에는 Kerberos 인증이 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b9ac0-121">Use of a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] login for the connection to the current primary will not require Kerberos authentication.</span></span>  
  
    ```sql
    USE master;  
    GO  
    EXEC sys.sp_adddistpublisher  
        @publisher = 'AGPrimaryReplicaHost',  
        @distribution_db = 'distribution',  
        @working_directory = '\\MyReplShare\WorkingDir',  
        @login = 'MyPubLogin',  
        @password = '**Strong password for publisher**';  
    ```  
  
 <span data-ttu-id="b9ac0-122">자세한 내용은 [sp_adddistpublisher&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-adddistpublisher-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b9ac0-122">For more information, see [sp_adddistpublisher &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-adddistpublisher-transact-sql).</span></span>  
  
### <a name="configure-the-publisher-at-the-original-publisher"></a><span data-ttu-id="b9ac0-123">원래 게시자에서 게시자 구성</span><span class="sxs-lookup"><span data-stu-id="b9ac0-123">Configure the publisher at the original publisher</span></span>
  
1.  <span data-ttu-id="b9ac0-124">원격 배포를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="b9ac0-124">Configure remote distribution.</span></span> <span data-ttu-id="b9ac0-125">게시자 구성에 저장 프로시저를 사용하는 경우 `sp_adddistributor`을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="b9ac0-125">If stored procedures are being used to configure the publisher, run `sp_adddistributor`.</span></span> <span data-ttu-id="b9ac0-126">*@password* `sp_adddistrbutor` 배포를 설정 하기 위해 배포자에서가 실행 될 때 사용 되는 것과 동일한 값을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b9ac0-126">Specify the same value for *@password* as that used when `sp_adddistrbutor` was run at the distributor to set up distribution.</span></span>  
  
    ```sql
    exec sys.sp_adddistributor  
        @distributor = 'MyDistributor',  
        @password = 'MyDistPass'  
    ```  
  
2.  <span data-ttu-id="b9ac0-127">데이터베이스를 복제할 수 있도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="b9ac0-127">Enable the database for replication.</span></span> <span data-ttu-id="b9ac0-128">게시자 구성에 저장 프로시저를 사용하는 경우 `sp_replicationdboption`을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="b9ac0-128">If stored procedures are being used to configure the publisher, run `sp_replicationdboption`.</span></span> <span data-ttu-id="b9ac0-129">데이터베이스에 대해 트랜잭션 복제와 병합 복제를 모두 구성하려는 경우 각각을 따로 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b9ac0-129">If both transactional and merge replication are to be configured for the database, each must be enabled.</span></span>  
  
    ```sql
    USE master;  
    GO  
    EXEC sys.sp_replicationdboption  
        @dbname = 'MyDBName',  
        @optname = 'publish',  
        @value = 'true';  
  
    EXEC sys.sp_replicationdboption  
        @dbname = 'MyDBName',  
        @optname = 'merge publish',  
        @value = 'true';  
    ```  
  
3.  <span data-ttu-id="b9ac0-130">복제 게시, 아티클 및 구독을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b9ac0-130">Create the replication publication, articles, and subscriptions.</span></span> <span data-ttu-id="b9ac0-131">복제 구성 방법은 데이터 및 데이터베이스 개체 게시를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b9ac0-131">For more information about how to configure replication, see Publishing Data and Database objects.</span></span>  
  
##  <a name="2-configure-the-alwayson-availability-group"></a><a name="step2"></a><span data-ttu-id="b9ac0-132">2. AlwaysOn 가용성 그룹 구성</span><span class="sxs-lookup"><span data-stu-id="b9ac0-132">2. Configure the AlwaysOn Availability Group</span></span>  
 <span data-ttu-id="b9ac0-133">의도한 주 복제본에서 게시되거나 게시할 데이터베이스를 멤버 데이터베이스로 추가하여 가용성 그룹을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b9ac0-133">At the intended primary, create the availability group with the published (or to be published) database as a member database.</span></span> <span data-ttu-id="b9ac0-134">가용성 그룹 마법사를 사용하는 경우 마법사가 초기에 보조 복제본 데이터베이스를 동기화하도록 할 수 있습니다. 또는 백업 및 복원을 사용하여 직접 초기화를 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b9ac0-134">If using the Availability Group Wizard, you can either allow the wizard to initially synchronize the secondary replica databases or you can perform the initialization manually by using backup and restore.</span></span>  
  
 <span data-ttu-id="b9ac0-135">가용성 그룹에 대해 복제 에이전트가 현재 주 복제본에 연결할 때 사용할 DNS 수신기를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b9ac0-135">Create a DNS listener for the availability group that will be used by the replication agents to connect to the current primary.</span></span> <span data-ttu-id="b9ac0-136">지정한 수신기 이름은 원래 게시자/게시된 데이터베이스 쌍의 리디렉션 대상으로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="b9ac0-136">The listener name that is specified will be used as the target of redirection for the original publisher/published database pair.</span></span> <span data-ttu-id="b9ac0-137">예를 들어 DDL을 사용하여 가용성 그룹을 구성하는 경우 다음 코드 예제를 사용하여 `MyAG`라는 기존 가용성 그룹에 대한 가용성 그룹 수신기를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b9ac0-137">For example, if you are using DDL to configure the availability group, the following code example can be used to specify an availability group listener for an existing availability group named `MyAG`:</span></span>  
  
```sql
ALTER AVAILABILITY GROUP 'MyAG'   
    ADD LISTENER 'MyAGListenerName' (WITH IP (('10.120.19.155', '255.255.254.0')));  
```  
  
 <span data-ttu-id="b9ac0-138">자세한 내용은 [가용성 그룹의 생성 및 구성&#40;SQL Server&#41;](creation-and-configuration-of-availability-groups-sql-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b9ac0-138">For more information, see [Creation and Configuration of Availability Groups &#40;SQL Server&#41;](creation-and-configuration-of-availability-groups-sql-server.md).</span></span>  
  
##  <a name="3-insure-that-all-of-the-secondary-replica-hosts-are-configured-for-replication"></a><a name="step3"></a><span data-ttu-id="b9ac0-139">3. 모든 보조 복제본 호스트에 대해 복제가 구성 되었는지</span><span class="sxs-lookup"><span data-stu-id="b9ac0-139">3. Insure that all of the Secondary Replica Hosts are Configured for Replication</span></span>  
 <span data-ttu-id="b9ac0-140">각 보조 복제본 호스트에서 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]가 복제를 지원하도록 구성되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="b9ac0-140">At each secondary replica host, verify that [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] has been configured to support replication.</span></span> <span data-ttu-id="b9ac0-141">각 보조 복제본 호스트에서 다음 쿼리를 실행하여 복제가 설치되었는지 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b9ac0-141">The following query can be run at each secondary replica host to determine whether replication is installed:</span></span>  
  
```sql
USE master;  
GO  
DECLARE @installed int;  
EXEC @installed = sys.sp_MS_replication_installed;  
SELECT @installed;  
```  
  
 <span data-ttu-id="b9ac0-142">*@installed*가 0 이면 설치에 복제를 추가 해야 합니다 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="b9ac0-142">If *@installed* is 0, replication must be added to the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] installation.</span></span>  
  
##  <a name="4-configure-the-secondary-replica-hosts-as-replication-publishers"></a><a name="step4"></a> <span data-ttu-id="b9ac0-143">4. 보조 복제본 호스트를 복제 게시자로 구성</span><span class="sxs-lookup"><span data-stu-id="b9ac0-143">4. Configure the Secondary Replica Hosts as Replication Publishers</span></span>  
 <span data-ttu-id="b9ac0-144">보조 복제본은 복제 게시자나 재게시자로 작동할 수 없지만 복제가 구성되어 있어야만 장애 조치(failover) 후 보조 복제본이 작업을 넘겨 받을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b9ac0-144">A secondary replica cannot act as a replication publisher or republisher but replication must be configured so that the secondary can take over after a failover.</span></span> <span data-ttu-id="b9ac0-145">배포자에서 각 보조 복제본 호스트에 대해 배포를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="b9ac0-145">At the distributor, configure distribution for each secondary replica host.</span></span> <span data-ttu-id="b9ac0-146">원래 게시자를 배포자에 추가할 때 지정한 것과 동일한 배포 데이터베이스 및 작업 디렉터리를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b9ac0-146">Specify the same distribution database and working directory as was specified when the original publisher was added to the distributor.</span></span> <span data-ttu-id="b9ac0-147">배포 구성에 저장 프로시저를 사용하는 경우 `sp_adddistpublisher`를 사용하여 원격 게시자를 배포자에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="b9ac0-147">If you are using stored procedures to configure distribution, use `sp_adddistpublisher` to associate the remote publishers with the distributor.</span></span> <span data-ttu-id="b9ac0-148">*@login*및가 *@password* 원래 게시자에 사용 된 경우 보조 복제본 호스트를 게시자로 추가할 때 각각에 대해 동일한 값을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b9ac0-148">If *@login* and *@password* were used for the original publisher, specify the same values for each when you add the secondary replica hosts as publishers.</span></span>  
  
```sql
EXEC sys.sp_adddistpublisher  
    @publisher = 'AGSecondaryReplicaHost',  
    @distribution_db = 'distribution',  
    @working_directory = '\\MyReplShare\WorkingDir',  
    @login = 'MyPubLogin',  
    @password = '**Strong password for publisher**';  
```  
  
 <span data-ttu-id="b9ac0-149">각 보조 복제본 호스트에서 배포를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="b9ac0-149">At each secondary replica host, configure distribution.</span></span> <span data-ttu-id="b9ac0-150">원래 게시자의 배포자를 원격 배포자로 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="b9ac0-150">Identify the distributor of the original publisher as the remote distributor.</span></span> <span data-ttu-id="b9ac0-151">배포자에서 원래 `sp_adddistributor`를 실행했을 때와 동일한 암호를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="b9ac0-151">Use the same password as that used when `sp_adddistributor` was run originally at the distributor.</span></span> <span data-ttu-id="b9ac0-152">배포를 구성 하는 데 저장 프로시저를 사용 하는 경우 *@password* 의 매개 변수를 `sp_adddistributor` 사용 하 여 암호를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b9ac0-152">If stored procedures are being used to configure distribution, the *@password* parameter of `sp_adddistributor` is used to specify the password.</span></span>  
  
```sql
EXEC sp_adddistributor   
    @distributor = 'MyDistributor',  
    @password = '**Strong password for distributor**';  
```  
  
 <span data-ttu-id="b9ac0-153">각 보조 복제본 호스트에서 데이터베이스 게시의 밀어넣기 구독자가 연결된 서버로 표시되는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="b9ac0-153">At each secondary replica host, make sure that the push subscribers of the database publications appear as linked servers.</span></span> <span data-ttu-id="b9ac0-154">원격 게시자 구성에 저장 프로시저를 사용하는 경우 `sp_addlinkedserver`를 사용하여 구독자(아직 없는 경우)를 게시자에 연결된 서버로 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="b9ac0-154">If stored procedures are being used to configure the remote publishers, use `sp_addlinkedserver` to add the subscribers (if not already present) as linked servers to the publishers.</span></span>  
  
```sql
EXEC sys.sp_addlinkedserver   
    @server = 'MySubscriber';  
```  
  
##  <a name="5-redirect-the-original-publisher-to-the-ag-listener-name"></a><a name="step5"></a> <span data-ttu-id="b9ac0-155">5. 원래 게시자를 AG 수신기 이름으로 리디렉션</span><span class="sxs-lookup"><span data-stu-id="b9ac0-155">5. Redirect the Original Publisher to the AG Listener Name</span></span>  
 <span data-ttu-id="b9ac0-156">배포자의 배포 데이터베이스에서 `sp_redirect_publisher` 저장 프로시저를 실행하여 원래 게시자와 게시된 데이터베이스를 가용성 그룹의 가용성 그룹 수신기 이름에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="b9ac0-156">At the distributor, in the distribution database, run the stored procedure `sp_redirect_publisher` to associate the original publisher and the published database with the availability group listener name of the availability group.</span></span>  
  
```sql
USE distribution;  
GO  
EXEC sys.sp_redirect_publisher   
@original_publisher = 'MyPublisher',  
    @publisher_db = 'MyPublishedDB',  
    @redirected_publisher = 'MyAGListenerName';  
```  
  
##  <a name="6-run-the-replication-validation-stored-procedure-to-verify-the-configuration"></a><a name="step6"></a> <span data-ttu-id="b9ac0-157">6. 복제 유효성 검사 저장 프로시저를 실행하여 구성 확인</span><span class="sxs-lookup"><span data-stu-id="b9ac0-157">6. Run the Replication Validation Stored Procedure to Verify the Configuration</span></span>  
 <span data-ttu-id="b9ac0-158">배포자의 배포 데이터베이스에서 `sp_validate_replica_hosts_as_publishers` 저장 프로시저를 실행하여 이제 모든 복제본 호스트가 게시된 데이터베이스의 게시자로 작동하도록 구성되었는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="b9ac0-158">At the distributor, in the distribution database, run the stored procedure `sp_validate_replica_hosts_as_publishers` to verify that all replica hosts are now configured to serve as publishers for the published database.</span></span>  
  
```sql
USE distribution;  
GO  
DECLARE @redirected_publisher sysname;  
EXEC sys.sp_validate_replica_hosts_as_publishers  
    @original_publisher = 'MyPublisher',  
    @publisher_db = 'MyPublishedDB',  
    @redirected_publisher = @redirected_publisher output;  
```  
  
 <span data-ttu-id="b9ac0-159">가용성 그룹에 대한 정보를 쿼리하려면 각 가용성 그룹 복제본 호스트에서 충분한 권한이 있는 로그인으로 `sp_validate_replica_hosts_as_publishers` 저장 프로시저를 실행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b9ac0-159">The stored procedure `sp_validate_replica_hosts_as_publishers` should be run from a login with sufficient authorization at each availability group replica host to query for information about the availability group.</span></span> <span data-ttu-id="b9ac0-160">와 달리 `sp_validate_redirected_publisher` 이 메서드는 호출자의 자격 증명을 사용 하며, msdb. m a. m. m a. m. m a. m a. m.</span><span class="sxs-lookup"><span data-stu-id="b9ac0-160">Unlike `sp_validate_redirected_publisher`, it uses the credentials of the caller and does not use the login retained in msdb.dbo.MSdistpublishers to connect to the availability group replicas.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b9ac0-161">읽기 액세스를 허용하지 않거나 읽기 전용으로 지정해야 하는 보조 복제본 호스트의 유효성을 검사할 경우에는 다음 오류와 함께 `sp_validate_replica_hosts_as_publishers`가 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="b9ac0-161">`sp_validate_replica_hosts_as_publishers` will fail with the following error when validating secondary replica hosts that do not allow read access, or require read intent to be specified.</span></span>  
>   
>  <span data-ttu-id="b9ac0-162">메시지 21899, 수준 11, 상태 1, 프로시저 `sp_hadr_verify_subscribers_at_publisher`, 줄 109</span><span class="sxs-lookup"><span data-stu-id="b9ac0-162">Msg 21899, Level 11, State 1, Procedure `sp_hadr_verify_subscribers_at_publisher`, Line 109</span></span>  
>   
>  <span data-ttu-id="b9ac0-163">원래 게시자 'MyOriginalPublisher'의 구독자에 대해 sysserver 항목이 있는지 확인하기 위한 리디렉션된 게시자 'MyReplicaHostName'의 쿼리가 실패하고 '976' 오류가 발생했습니다. 오류 메시지는 다음과 같습니다. '오류 976, 수준 14, 상태 1, 메시지: 대상 데이터베이스 'MyPublishedDB'가 가용성 그룹에 참여 중이며, 쿼리가 현재 이 대상 데이터베이스에 액세스할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b9ac0-163">The query at the redirected publisher 'MyReplicaHostName' to determine whether there were sysserver entries for the subscribers of the original publisher 'MyOriginalPublisher' failed with error '976', error message 'Error 976, Level 14, State 1, Message: The target database, 'MyPublishedDB', is participating in an availability group and is currently not accessible for queries.</span></span> <span data-ttu-id="b9ac0-164">데이터 이동이 일시 중지되었거나 가용성 복제본이 읽기 액세스로 설정되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="b9ac0-164">Either data movement is suspended or the availability replica is not enabled for read access.</span></span> <span data-ttu-id="b9ac0-165">이 데이터베이스 및 가용성 그룹 내 다른 데이터베이스에 읽기 전용 액세스를 허용하려면 그룹 내 하나 이상의 보조 가용성 복제본에 읽기 액세스를 설정하세요.</span><span class="sxs-lookup"><span data-stu-id="b9ac0-165">To allow read-only access to this and other databases in the availability group, enable read access to one or more secondary availability replicas in the group.</span></span>  <span data-ttu-id="b9ac0-166">자세한 내용은 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 온라인 설명서의 `ALTER AVAILABILITY GROUP` 문을 참조하십시오.').</span><span class="sxs-lookup"><span data-stu-id="b9ac0-166">For more information, see the `ALTER AVAILABILITY GROUP` statement in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Books Online.'.</span></span>  
>   
>  <span data-ttu-id="b9ac0-167">복제본 호스트 'MyReplicaHostName'에 대해 하나 이상의 게시자 유효성 검사 오류가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="b9ac0-167">One or more publisher validation errors were encountered for replica host 'MyReplicaHostName'.</span></span>  
  
 <span data-ttu-id="b9ac0-168">이는 정상적인 동작입니다.</span><span class="sxs-lookup"><span data-stu-id="b9ac0-168">This is expected behavior.</span></span> <span data-ttu-id="b9ac0-169">이러한 보조 복제본 호스트에서 직접 sysserver 항목을 쿼리하여 구독자 서버 항목이 있는지 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b9ac0-169">You must verify the presence of the subscriber server entries at these secondary replica hosts by querying for the sysserver entries directly at the host.</span></span>  
  
##  <a name="7-add-the-original-publisher-to-replication-monitor"></a><a name="step7"></a> <span data-ttu-id="b9ac0-170">7. 원래 게시자를 복제 모니터에 추가</span><span class="sxs-lookup"><span data-stu-id="b9ac0-170">7. Add the Original Publisher to Replication Monitor</span></span>  
 <span data-ttu-id="b9ac0-171">각 가용성 그룹 복제본에서 원래 게시자를 복제 모니터에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="b9ac0-171">At each availability group replica, add the original publisher to Replication Monitor.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="b9ac0-172">관련 작업</span><span class="sxs-lookup"><span data-stu-id="b9ac0-172">Related Tasks</span></span>  
 <span data-ttu-id="b9ac0-173">**복제**</span><span class="sxs-lookup"><span data-stu-id="b9ac0-173">**Replication**</span></span>  
  
-   [<span data-ttu-id="b9ac0-174">AlwaysOn 게시 데이터베이스를 유지 관리 하는 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="b9ac0-174">Maintaining an AlwaysOn Publication Database &#40;SQL Server&#41;</span></span>](maintaining-an-always-on-publication-database-sql-server.md)  
  
-   [<span data-ttu-id="b9ac0-175">복제, 변경 내용 추적, 변경 데이터 캡처 및 AlwaysOn 가용성 그룹 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="b9ac0-175">Replication, Change Tracking, Change Data Capture, and AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](replicate-track-change-data-capture-always-on-availability.md)  
  
-   [<span data-ttu-id="b9ac0-176">복제 관리 FAQ</span><span class="sxs-lookup"><span data-stu-id="b9ac0-176">Replication Administration FAQ</span></span>](../../../relational-databases/replication/administration/frequently-asked-questions-for-replication-administrators.md)  
  
 <span data-ttu-id="b9ac0-177">**가용성 그룹을 만들고 구성하려면**</span><span class="sxs-lookup"><span data-stu-id="b9ac0-177">**To create and configure an availability group**</span></span>  
  
-   [<span data-ttu-id="b9ac0-178">가용성 그룹 마법사 사용&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="b9ac0-178">Use the Availability Group Wizard &#40;SQL Server Management Studio&#41;</span></span>](use-the-availability-group-wizard-sql-server-management-studio.md)  
  
-   [<span data-ttu-id="b9ac0-179">새 가용성 그룹 대화 상자 사용&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="b9ac0-179">Use the New Availability Group Dialog Box &#40;SQL Server Management Studio&#41;</span></span>](use-the-new-availability-group-dialog-box-sql-server-management-studio.md)  
  
-   [<span data-ttu-id="b9ac0-180">가용성 그룹 만들기&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="b9ac0-180">Create an Availability Group &#40;Transact-SQL&#41;</span></span>](create-an-availability-group-transact-sql.md)  
  
-   [<span data-ttu-id="b9ac0-181">가용성 그룹 만들기&#40;SQL Server PowerShell&#41;</span><span class="sxs-lookup"><span data-stu-id="b9ac0-181">Create an Availability Group &#40;SQL Server PowerShell&#41;</span></span>](../../../powershell/sql-server-powershell.md)  
  
-   [<span data-ttu-id="b9ac0-182">가용성 복제본 추가 또는 수정 시 엔드포인트 URL 지정&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="b9ac0-182">Specify the Endpoint URL When Adding or Modifying an Availability Replica &#40;SQL Server&#41;</span></span>](specify-endpoint-url-adding-or-modifying-availability-replica.md)  
  
-   [<span data-ttu-id="b9ac0-183">AlwaysOn 가용성 그룹 &#40;SQL Server PowerShell에 대 한 데이터베이스 미러링 끝점을 만듭니다&#41;</span><span class="sxs-lookup"><span data-stu-id="b9ac0-183">Create a Database Mirroring Endpoint for AlwaysOn Availability Groups &#40;SQL Server PowerShell&#41;</span></span>](database-mirroring-always-on-availability-groups-powershell.md)  
  
-   [<span data-ttu-id="b9ac0-184">가용성 그룹에 보조 복제본 조인&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="b9ac0-184">Join a Secondary Replica to an Availability Group &#40;SQL Server&#41;</span></span>](join-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="b9ac0-185">가용성 그룹에 대한 보조 데이터베이스 준비&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="b9ac0-185">Manually Prepare a Secondary Database for an Availability Group &#40;SQL Server&#41;</span></span>](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="b9ac0-186">가용성 그룹에 보조 데이터베이스 조인&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="b9ac0-186">Join a Secondary Database to an Availability Group &#40;SQL Server&#41;</span></span>](join-a-secondary-database-to-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="b9ac0-187">가용성 그룹 수신기 만들기 또는 구성&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="b9ac0-187">Create or Configure an Availability Group Listener &#40;SQL Server&#41;</span></span>](create-or-configure-an-availability-group-listener-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="b9ac0-188">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b9ac0-188">See Also</span></span>  
 <span data-ttu-id="b9ac0-189">[AlwaysOn 가용성 그룹 &#40;SQL Server에 대 한 필수 조건, 제한 사항 및 권장 사항&#41;](prereqs-restrictions-recommendations-always-on-availability.md) </span><span class="sxs-lookup"><span data-stu-id="b9ac0-189">[Prerequisites, Restrictions, and Recommendations for AlwaysOn Availability Groups &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md) </span></span>  
 <span data-ttu-id="b9ac0-190">[AlwaysOn 가용성 그룹 &#40;SQL Server 개요&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="b9ac0-190">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="b9ac0-191">[AlwaysOn 가용성 그룹: 상호 운용성 (SQL Server)](always-on-availability-groups-interoperability-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="b9ac0-191">[AlwaysOn Availability Groups: Interoperability (SQL Server)](always-on-availability-groups-interoperability-sql-server.md) </span></span>  
 [<span data-ttu-id="b9ac0-192">SQL Server 복제</span><span class="sxs-lookup"><span data-stu-id="b9ac0-192">SQL Server Replication</span></span>](../../../relational-databases/replication/sql-server-replication.md)  
