---
title: 가용성 그룹 마법사 사용(SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.newagwizard.f1
- sql12.swb.newavgroupwiz.f1
helpviewer_keywords:
- New Availability Group Wizard, availability replicas
- Availability Groups [SQL Server], wizards
- Availability Groups [SQL Server], creating
ms.assetid: e1f1dccc-9e65-471d-8fd1-b45085c9484a
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c88bc60b4aeab12b3c55d23d1fe7b2b033a962f0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648587"
---
# <a name="use-the-availability-group-wizard-sql-server-management-studio"></a><span data-ttu-id="5355b-102">가용성 그룹 마법사 사용(SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="5355b-102">Use the Availability Group Wizard (SQL Server Management Studio)</span></span>
  <span data-ttu-id="5355b-103">이 항목에서는 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]의 새 가용성 그룹 마법사를 사용하여 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]에서 AlwaysOn 가용성 그룹을 만들고 구성하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="5355b-103">This topic describes how to use the New Availability Group Wizard (in [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]) to create and configure an AlwaysOn availability group in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="5355b-104">*가용성 그룹* 은 단일 단위로 장애 조치(Failover)될 사용자 데이터베이스 집합과 장애 조치(Failover)를 지원하는 장애 조치(Failover) 파트너 집합( *가용성 복제본*이라고 함)을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="5355b-104">An *availability group* defines a set of user databases that will fail over as a single unit and a set of failover partners, known as *availability replicas*, that support failover.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5355b-105">가용성 그룹에 대한 소개는 [AlwaysOn 가용성 그룹 개요&#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5355b-105">For an introduction to availability groups, see [Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md).</span></span>  
  
-   <span data-ttu-id="5355b-106">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="5355b-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="5355b-107">필수 구성 요소, 제한 사항 및 권장 사항</span><span class="sxs-lookup"><span data-stu-id="5355b-107">Prerequisites, Restrictions, and Recommendations</span></span>](#PrerequisitesRestrictions)  
  
     [<span data-ttu-id="5355b-108">보안</span><span class="sxs-lookup"><span data-stu-id="5355b-108">Security</span></span>](#Security)  
  
-   <span data-ttu-id="5355b-109">**가용성 그룹을 만들고 구성하려면**  [새 가용성 그룹 마법사(SQL Server Management Studio)](#RunAGwiz)</span><span class="sxs-lookup"><span data-stu-id="5355b-109">**To create and configure an availability group, using:**  [New Availability Group Wizard (SQL Server Management Studio)](#RunAGwiz)</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5355b-110">새 가용성 그룹 마법사 대신 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 또는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell cmdlet을 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5355b-110">As an alternative to using the New Availability Group Wizard, you can use [!INCLUDE[tsql](../../../includes/tsql-md.md)] or [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell cmdlets.</span></span> <span data-ttu-id="5355b-111">자세한 내용은 [가용성 그룹 만들기&#40;Transact-SQL&#41;](create-an-availability-group-transact-sql.md) 또는 [가용성 그룹 만들기&#40;SQL Server PowerShell&#41;](../../../powershell/sql-server-powershell.md)에서 AlwaysOn 가용성 그룹을 만들고 구성하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="5355b-111">For more information, see [Create an Availability Group &#40;Transact-SQL&#41;](create-an-availability-group-transact-sql.md) or [Create an Availability Group &#40;SQL Server PowerShell&#41;](../../../powershell/sql-server-powershell.md).</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="5355b-112">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="5355b-112">Before You Begin</span></span>  
 <span data-ttu-id="5355b-113">가용성 그룹을 처음 만들어 보는 경우 이 섹션을 먼저 읽는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="5355b-113">We strongly recommend that you read this section before attempting to create your first availability group.</span></span>  
  
###  <a name="prerequisites-restrictions-and-recommendations"></a><a name="PrerequisitesRestrictions"></a><span data-ttu-id="5355b-114">사전 요구 사항, 제한 사항 및 권장 사항</span><span class="sxs-lookup"><span data-stu-id="5355b-114">Prerequisites, Restrictions, and Recommendations</span></span>  
 <span data-ttu-id="5355b-115">대부분의 경우 새 가용성 그룹 마법사를 사용하여 가용성 그룹을 만들고 구성하는 데 필요한 모든 태스크를 완료할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5355b-115">In most cases, you can use the New Availability Group Wizard to complete all of the tasks require to create and configure an availability group.</span></span> <span data-ttu-id="5355b-116">그러나 일부 태스크를 수동으로 완료해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5355b-116">However, you might need to complete some of the tasks manually.</span></span>  
  
-   <span data-ttu-id="5355b-117">가용성 그룹을 만들기 전에 가용성 복제본을 호스팅하는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인스턴스가 동일한 WSFC 장애 조치(Failover) 클러스터 내의 다른 WSFC(Windows Server 장애 조치(Failover) 클러스터링) 노드에 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="5355b-117">Before creating an availability group, verify that the instances of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] that host availability replicas reside on different Windows Server Failover Clustering (WSFC) node within the same WSFC failover cluster.</span></span> <span data-ttu-id="5355b-118">또한 각 서버 인스턴스가 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 의 기타 모든 필수 구성 요소를 충족하는지도 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="5355b-118">Also, verify that each of the server instance meets all other [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] prerequisites.</span></span> <span data-ttu-id="5355b-119">자세한 내용은 [AlwaysOn 가용성 그룹에 대한 필수 조건, 제한 사항 및 권장 사항&#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5355b-119">For more information, we strongly recommend that you read [Prerequisites, Restrictions, and Recommendations for AlwaysOn Availability Groups &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md).</span></span>  
  
-   <span data-ttu-id="5355b-120">가용성 복제본을 호스팅하도록 선택한 서버 인스턴스가 도메인 사용자 계정으로 실행되고 있고 아직 데이터베이스 미러링 엔드포인트를 가지고 있지 않은 경우, 마법사가 엔드포인트를 만들고 서버 인스턴스 서비스 계정에 CONNECT 권한을 부여할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5355b-120">If a server instance that you select to host an availability replica is running under a domain user account and does not yet have a database mirroring endpoint, the wizard can create the endpoint and grant CONNECT permission to the server instance service account.</span></span> <span data-ttu-id="5355b-121">그러나 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 서비스가 로컬 시스템, 로컬 서비스 또는 네트워크 서비스와 같은 기본 제공 계정이나 비도메인 계정으로 실행 중인 경우에는 사용자가 엔드포인트 인증을 위한 인증서를 사용해야 하며 마법사를 통해 서버 인스턴스에 대한 데이터베이스 미러링 엔드포인트를 만들 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5355b-121">However, if the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] service is running as a built-in account, such as Local System, Local Service, or Network Service, or a nondomain account, you must use certificates for endpoint authentication, and the wizard will be unable to create a database mirroring endpoint on the server instance.</span></span> <span data-ttu-id="5355b-122">이 경우 새 가용성 그룹 마법사를 시작하기 전에 수동으로 데이터 미러링 엔드포인트를 만드는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="5355b-122">In this case, we recommend that you create the database mirroring endpoints manually before you launch the New Availability Group Wizard.</span></span>  
  
     `To use certificates for a database mirroring endpoint:`  
  
     [<span data-ttu-id="5355b-123">CREATE ENDPOINT&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="5355b-123">CREATE ENDPOINT &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-endpoint-transact-sql)  
  
     [<span data-ttu-id="5355b-124">데이터베이스 미러링 엔드포인트에 대한 인증서 사용&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="5355b-124">Use Certificates for a Database Mirroring Endpoint &#40;Transact-SQL&#41;</span></span>](../../database-mirroring/use-certificates-for-a-database-mirroring-endpoint-transact-sql.md)  
  
-   <span data-ttu-id="5355b-125">SQL Server FCI(장애 조치(Failover) 클러스터 인스턴스)는 가용성 그룹에 따라 AlwaysOn 자동 장애 조치(Failover)를 지원하지 않으므로 FCI에서 호스팅하는 모든 가용성 복제본은 수동 장애 조치(Failover)에 대해서만 구성될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5355b-125">SQL Server Failover Cluster Instances (FCIs) do not support automatic failover by availability groups, so any availability replica that is hosted by an FCI can only be configured for manual failover.</span></span>  
  
-   <span data-ttu-id="5355b-126">데이터가 암호화되었거나 심지어 DEK(데이터베이스 암호화 키)를 포함하는 경우 [!INCLUDE[ssAoNewAgWiz](../../../includes/ssaonewagwiz-md.md)] 또는 [!INCLUDE[ssAoAddDbWiz](../../../includes/ssaoadddbwiz-md.md)] 를 사용하여 데이터베이스를 가용성 그룹에 추가할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5355b-126">If a database is encrypted or even contains a Database Encryption Key (DEK), you cannot use the [!INCLUDE[ssAoNewAgWiz](../../../includes/ssaonewagwiz-md.md)] or [!INCLUDE[ssAoAddDbWiz](../../../includes/ssaoadddbwiz-md.md)] to add the database to an availability group.</span></span> <span data-ttu-id="5355b-127">암호화된 데이터베이스가 암호 해독된 경우라도 해당 로그 백업에는 암호화된 데이터가 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5355b-127">Even if an encrypted database has been decrypted, its log backups might contain encrypted data.</span></span> <span data-ttu-id="5355b-128">이 경우 데이터베이스에서 전체 초기 데이터 동기화를 수행하면 작업이 실패할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5355b-128">In this case, full initial data synchronization could fail on the database.</span></span> <span data-ttu-id="5355b-129">로그 복원 작업에는 DEK(데이터베이스 암호화 키)에서 사용된 인증서가 필요한데 이 인증서를 사용할 수 없기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="5355b-129">This is because the restore log operation might require the certificate that was used by the database encryption keys (DEKs), and that certificate might be unavailable.</span></span>  
  
     <span data-ttu-id="5355b-130">마법사를 사용하여 암호 해독된 데이터베이스를 가용성 그룹에 추가하기에 적합하도록 만들려면</span><span class="sxs-lookup"><span data-stu-id="5355b-130">To make a decrypted database eligible to add to an availability group using the wizard:</span></span>  
  
    1.  <span data-ttu-id="5355b-131">주 데이터베이스의 로그 백업을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="5355b-131">Create a log backup of the primary database.</span></span>  
  
    2.  <span data-ttu-id="5355b-132">주 데이터베이스의 전체 데이터베이스 백업을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="5355b-132">Create a full database backup of the primary database.</span></span>  
  
    3.  <span data-ttu-id="5355b-133">보조 복제본을 호스팅하는 서버 인스턴스에서 데이터베이스 백업을 복원합니다.</span><span class="sxs-lookup"><span data-stu-id="5355b-133">Restore the database backup on the server instance that hosts the secondary replica.</span></span>  
  
    4.  <span data-ttu-id="5355b-134">주 데이터베이스에서 새 로그 백업을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="5355b-134">Create a new log backup from primary database.</span></span>  
  
    5.  <span data-ttu-id="5355b-135">보조 데이터베이스에서 이 로그 백업을 복원합니다.</span><span class="sxs-lookup"><span data-stu-id="5355b-135">Restore this log backup on the secondary database.</span></span>  
  
-   <span data-ttu-id="5355b-136">**마법사를 사용하여 전체 초기 데이터 동기화를 수행하기 위한 필수 구성 요소**</span><span class="sxs-lookup"><span data-stu-id="5355b-136">**Prerequisites for the wizard to perform full initial data synchronization**</span></span>  
  
    -   <span data-ttu-id="5355b-137">모든 데이터베이스 파일 경로는 가용성 그룹에 대한 복제본을 호스팅하는 모든 서버 인스턴스에서 동일해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5355b-137">All the database-file paths must be identical on every server instance that hosts a replica for the availability group.</span></span>  
  
    -   <span data-ttu-id="5355b-138">보조 복제본을 호스팅하는 서버 인스턴스에 주 데이터베이스 이름이 없을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5355b-138">No primary database name can exist on any server instance that hosts a secondary replica.</span></span> <span data-ttu-id="5355b-139">즉, 새 보조 데이터베이스가 아직 없을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5355b-139">This means that none of the new secondary databases can exist yet.</span></span>  
  
    -   <span data-ttu-id="5355b-140">마법사에서 백업을 만들고 액세스하려면 네트워크 공유를 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5355b-140">You will need to specify a network share in order for the wizard to create and access backups.</span></span> <span data-ttu-id="5355b-141">주 복제본의 경우 [!INCLUDE[ssDE](../../../includes/ssde-md.md)] 을 시작하는 데 사용되는 계정은 네트워크 공유에 대한 읽기 및 쓰기 파일 시스템 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5355b-141">For the primary replica, the account used to start the [!INCLUDE[ssDE](../../../includes/ssde-md.md)] must have read and write file-system permissions on a network share.</span></span> <span data-ttu-id="5355b-142">보조 복제본에 대한 계정은 네트워크 공유에 대한 읽기 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5355b-142">For secondary replicas, the account must have read permission on the network share.</span></span>  
  
        > [!IMPORTANT]  
        >  <span data-ttu-id="5355b-143">로그 백업이 로그 백업 체인의 일부입니다.</span><span class="sxs-lookup"><span data-stu-id="5355b-143">The log backups will be part of your log backup chain.</span></span> <span data-ttu-id="5355b-144">로그 백업 파일을 적절히 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="5355b-144">Store the log backup files appropriately.</span></span>  
  
     <span data-ttu-id="5355b-145">마법사를 사용하여 전체 초기 데이터 동기화를 수행할 수 없는 경우에는 보조 데이터베이스를 수동으로 준비해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5355b-145">If you are unable to use the wizard to perform full initial data synchronization, you need to prepare your secondary databases manually.</span></span> <span data-ttu-id="5355b-146">마법사를 실행하기 전이나 후에 이 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5355b-146">You can do this before or after running the wizard.</span></span> <span data-ttu-id="5355b-147">자세한 내용은 [가용성 그룹에 대한 보조 데이터베이스 수동 준비&#40;SQL Server&#41;](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md)또는 PowerShell을 사용하여 Always On 가용성 그룹에 보조 데이터베이스를 조인하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="5355b-147">For more information, see [Manually Prepare a Secondary Database for an Availability Group &#40;SQL Server&#41;](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="5355b-148">보안</span><span class="sxs-lookup"><span data-stu-id="5355b-148">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="5355b-149">권한</span><span class="sxs-lookup"><span data-stu-id="5355b-149">Permissions</span></span>  
 <span data-ttu-id="5355b-150">CREATE AVAILABILITY GROUP 서버 권한, ALTER ANY AVAILABILITY GROUP 권한, CONTROL SERVER 권한 중 하나와 **sysadmin** 고정 서버 역할의 멤버 자격이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="5355b-150">Requires membership in the **sysadmin** fixed server role and either CREATE AVAILABILITY GROUP server permission, ALTER ANY AVAILABILITY GROUP permission, or CONTROL SERVER permission.</span></span>  
  
 <span data-ttu-id="5355b-151">가용성 그룹 마법사에서 데이터베이스 미러링 엔드포인트를 관리할 수 있도록 하려면 CONTROL ON ENDPOINT 권한도 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="5355b-151">Also requires CONTROL ON ENDPOINT permission if you want to allow Availability Group Wizard to manage the database mirroring endpoint.</span></span>  
  
##  <a name="using-the-new-availability-group-wizard"></a><a name="RunAGwiz"></a> <span data-ttu-id="5355b-152">새 가용성 그룹 마법사 사용</span><span class="sxs-lookup"><span data-stu-id="5355b-152">Using the New Availability Group Wizard</span></span>  
  
1.  <span data-ttu-id="5355b-153">개체 탐색기에서 주 복제본을 호스팅하는 서버 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="5355b-153">In Object Explorer, connect to the server instance that hosts the primary replica.</span></span>  
  
2.  <span data-ttu-id="5355b-154">**AlwaysOn 고가용성** 및 **가용성 그룹** 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="5355b-154">Expand the **AlwaysOn High Availability** node and the **Availability Groups** node.</span></span>  
  
3.  <span data-ttu-id="5355b-155">새 가용성 그룹 마법사를 시작하려면 **새 가용성 그룹 마법사** 명령을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="5355b-155">To launch the New Availability Group Wizard, select the **New Availability Group Wizard** command.</span></span>  
  
4.  <span data-ttu-id="5355b-156">이 마법사를 처음 실행하는 경우 **소개** 페이지가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="5355b-156">The first time you run this wizard, an **Introduction** page appears.</span></span> <span data-ttu-id="5355b-157">다음부터 이 페이지를 건너뛰려면 **이 페이지를 다시 표시 안 함**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5355b-157">To bypass this page in the future, you can click **Do not show this page again**.</span></span> <span data-ttu-id="5355b-158">이 페이지를 읽은 후 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5355b-158">After reading this page, click **Next**.</span></span>  
  
5.  <span data-ttu-id="5355b-159">**가용성 그룹 이름 지정** 페이지에서 **가용성 그룹 이름** 필드에 새 가용성 그룹의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="5355b-159">On the **Specify Availability Group Name** page, enter the name of the new availability group in the **Availability group name** field.</span></span> <span data-ttu-id="5355b-160">이 이름은 WSFC 장애 조치(Failover) 클러스터와 도메인 전체에서 고유하고 유효한 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 식별자여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5355b-160">This name must be a valid [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] identifier that is unique on the WSFC failover cluster and in your domain as a whole.</span></span> <span data-ttu-id="5355b-161">가용성 그룹 이름의 최대 길이는 128자입니다.</span><span class="sxs-lookup"><span data-stu-id="5355b-161">The maximum length for an availability group name is 128 characters.</span></span>  
  
6.  <span data-ttu-id="5355b-162">**데이터베이스 선택** 페이지의 표에 *가용성 데이터베이스*로 적합한 연결된 서버 인스턴스의 사용자 데이터베이스가 나열됩니다.</span><span class="sxs-lookup"><span data-stu-id="5355b-162">On the **Select Databases** page, the grid lists user databases on the connected server instance that are eligible to become the *availability databases*.</span></span> <span data-ttu-id="5355b-163">나열된 데이터베이스 중 새 가용성 그룹에 참여할 데이터베이스를 하나 이상 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="5355b-163">Select one or more of the listed databases to participate in the new availability group.</span></span> <span data-ttu-id="5355b-164">이러한 데이터베이스가 초기 *주 데이터베이스*가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5355b-164">These databases will initially be the initial *primary databases*.</span></span>  
  
     <span data-ttu-id="5355b-165">나열된 각 데이터베이스의 **크기** 열에 데이터베이스 크기(알려진 경우)가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="5355b-165">For each listed database, the **Size** column displays the database size, if known.</span></span> <span data-ttu-id="5355b-166">**상태** 열에는 지정된 데이터베이스가 가용성 데이터베이스에 대한 [필수 구성 요소](prereqs-restrictions-recommendations-always-on-availability.md)를 충족하는지 여부가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="5355b-166">The **Status** column indicates whether a given database meets the [prerequisites](prereqs-restrictions-recommendations-always-on-availability.md)for availability databases.</span></span> <span data-ttu-id="5355b-167">필수 구성 요소가 충족되지 않는 경우 데이터베이스가 부적합한 이유(예: 전체 복구 모델을 사용하지 않는 경우)를 설명하는 간략한 상태 설명이 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="5355b-167">It the prerequisites are not met, a brief status description indicates the reason that the database is ineligible; for example, if it does not use the full recovery model.</span></span> <span data-ttu-id="5355b-168">자세한 내용을 보려면 상태 설명을 클릭하세요.</span><span class="sxs-lookup"><span data-stu-id="5355b-168">For more information, click the status description.</span></span>  
  
     <span data-ttu-id="5355b-169">데이터베이스를 적합하도록 변경한 경우 **새로 고침** 을 클릭하여 데이터베이스 표를 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="5355b-169">If you change a database to make it eligible, click **Refresh** to update the databases grid.</span></span>  
  
7.  <span data-ttu-id="5355b-170">**복제본 선택** 페이지에서 새 가용성 그룹에 대해 하나 이상의 복제본을 지정하고 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="5355b-170">On the **Specify Replicas** page, specify and configure one or more replicas for the new availability group.</span></span> <span data-ttu-id="5355b-171">이 페이지에는 네 개의 탭이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5355b-171">This page contains four tabs.</span></span> <span data-ttu-id="5355b-172">다음 표에서는 이러한 탭을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="5355b-172">The following table introduces these tabs.</span></span> <span data-ttu-id="5355b-173">자세한 내용은 [복제본 지정 페이지&#40;새 가용성 그룹 마법사: 복제본 추가 마법사&#41;](specify-replicas-page-new-availability-group-wizard-add-replica-wizard.md) 항목을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5355b-173">For more information, see the [Specify Replicas Page &#40;New Availability Group Wizard: Add Replica Wizard&#41;](specify-replicas-page-new-availability-group-wizard-add-replica-wizard.md) topic.</span></span>  
  
    |<span data-ttu-id="5355b-174">탭</span><span class="sxs-lookup"><span data-stu-id="5355b-174">Tab</span></span>|<span data-ttu-id="5355b-175">간략한 설명</span><span class="sxs-lookup"><span data-stu-id="5355b-175">Brief Description</span></span>|  
    |---------|-----------------------|  
    |<span data-ttu-id="5355b-176">**복제본**</span><span class="sxs-lookup"><span data-stu-id="5355b-176">**Replicas**</span></span>|<span data-ttu-id="5355b-177">이 탭에서는 보조 복제본을 호스팅할 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 의 각 인스턴스를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5355b-177">Use this tab to specify each instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] that will host a secondary replica.</span></span> <span data-ttu-id="5355b-178">현재 연결된 서버 인스턴스가 주 복제본을 호스팅해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5355b-178">Note that the server instance to which you are currently connected must host the primary replica.</span></span>|  
    |<span data-ttu-id="5355b-179">**엔드포인트**</span><span class="sxs-lookup"><span data-stu-id="5355b-179">**Endpoints**</span></span>|<span data-ttu-id="5355b-180">기존 데이터베이스 미러링 엔드포인트를 확인하고, 서비스 계정에서 Windows 인증을 사용하는 서버 인스턴스에 이 엔드포인트가 없는 경우 엔드포인트를 자동으로 만들려면 이 탭을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="5355b-180">Use this tab to verify any existing database mirroring endpoints and also, if this endpoint is lacking on a server instance whose service accounts use Windows Authentication, to create the endpoint automatically.</span></span> <span data-ttu-id="5355b-181">**참고:**  서버 인스턴스가 도메인 사용자 계정이 아닌 계정으로 실행 중인 경우 마법사를 계속 하려면 먼저 서버 인스턴스를 수동으로 변경 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5355b-181">**Note:**  If any server instance is running under a non-domain user account, you need to do make a manual change to your server instance before you can proceed in the wizard.</span></span> <span data-ttu-id="5355b-182">자세한 내용은 이 항목의 앞부분에 나오는 [필수 구성 요소](#PrerequisitesRestrictions)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5355b-182">For more information, see [Prerequisites](#PrerequisitesRestrictions), earlier in this topic.</span></span>|  
    |<span data-ttu-id="5355b-183">**백업 기본 설정**</span><span class="sxs-lookup"><span data-stu-id="5355b-183">**Backup Preferences**</span></span>|<span data-ttu-id="5355b-184">가용성 그룹 전체에 대한 백업 기본 설정과 개별 가용성 복제본에 대한 백업 우선 순위를 지정하려면 이 탭을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="5355b-184">Use this tab to specify your backup preference for the availability group as a whole and your backup priorities for the individual availability replicas.</span></span>|  
    |<span data-ttu-id="5355b-185">**수신기**</span><span class="sxs-lookup"><span data-stu-id="5355b-185">**Listener**</span></span>|<span data-ttu-id="5355b-186">이 탭을 사용하여 가용성 그룹 수신기를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5355b-186">Use this tab to create an availability group listener.</span></span> <span data-ttu-id="5355b-187">기본적으로 마법사는 수신기를 만들지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5355b-187">By default, the wizard does not create a listener.</span></span>|  
  
8.  <span data-ttu-id="5355b-188">**초기 데이터 동기화 선택** 페이지에서 새 보조 복제본을 만들고 가용성 그룹에 조인할 방법을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="5355b-188">On the **Select Initial Data Synchronization** page, choose how you want your new secondary databases to be created and joined to the availability group.</span></span> <span data-ttu-id="5355b-189">다음 옵션 중 하나를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="5355b-189">Choose one of the following options:</span></span>  
  
    -   <span data-ttu-id="5355b-190">**전체**</span><span class="sxs-lookup"><span data-stu-id="5355b-190">**Full**</span></span>  
  
         <span data-ttu-id="5355b-191">현재 환경이 초기 데이터 동기화 자동 시작을 위한 요구 사항을 충족하는 경우에 이 옵션을 선택합니다. 자세한 내용은 이 항목의 앞부분에 나오는 [필수 구성 요소, 제한 사항 및 권장 사항](#PrerequisitesRestrictions)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5355b-191">Select this option if your environment meets the requirements for automatically starting initial data synchronization (for more information, see [Prerequisites, Restrictions, and Recommendations](#PrerequisitesRestrictions), earlier in this topic).</span></span>  
  
         <span data-ttu-id="5355b-192">**전체**를 선택한 후 가용성 그룹을 만들면 마법사에서 모든 주 데이터베이스와 해당 트랜잭션 로그를 네트워크 공유에 백업하고 보조 복제본을 호스팅하는 모든 서버 인스턴스에서 백업을 복원합니다.</span><span class="sxs-lookup"><span data-stu-id="5355b-192">If you select **Full**, after creating the availability group, the wizard will back up every primary database and its transaction log to a network share and restore the backups on every server instance that hosts an secondary replica.</span></span> <span data-ttu-id="5355b-193">그런 다음 모든 보조 데이터베이스를 가용성 그룹에 조인합니다.</span><span class="sxs-lookup"><span data-stu-id="5355b-193">The wizard will then join every secondary database to the availability group.</span></span>  
  
         <span data-ttu-id="5355b-194">**모든 복제본에서 액세스할 수 있는 공유 네트워크 위치 지정:** 필드에서 복제본을 호스팅하는 모든 서버 인스턴스에 읽기/쓰기 액세스 권한이 있는 백업 공유를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="5355b-194">In the **Specify a shared network location accessible by all replicas:** field, specify a backup share to which all of the server instance that host replicas have read-write access.</span></span> <span data-ttu-id="5355b-195">자세한 내용은 이 항목의 앞부분에 나오는 [필수 구성 요소](#PrerequisitesRestrictions)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5355b-195">For more information, see [Prerequisites](#PrerequisitesRestrictions), earlier in this topic.</span></span>  
  
    -   <span data-ttu-id="5355b-196">**조인만**</span><span class="sxs-lookup"><span data-stu-id="5355b-196">**Join only**</span></span>  
  
         <span data-ttu-id="5355b-197">보조 복제본을 호스팅할 서버 인스턴스에서 보조 데이터베이스를 수동으로 준비하는 경우 이 옵션을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5355b-197">If you have manually prepared secondary databases on the server instances that will host the secondary replicas, you can select this option.</span></span> <span data-ttu-id="5355b-198">마법사에서 기존 보조 데이터베이스를 가용성 그룹에 조인합니다.</span><span class="sxs-lookup"><span data-stu-id="5355b-198">The wizard will join the existing secondary databases to the availability group.</span></span>  
  
    -   <span data-ttu-id="5355b-199">**초기 데이터 동기화 건너뛰기**</span><span class="sxs-lookup"><span data-stu-id="5355b-199">**Skip initial data synchronization**</span></span>  
  
         <span data-ttu-id="5355b-200">주 데이터베이스의 로그 백업과 사용자 데이터베이스를 사용하려는 경우 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="5355b-200">Select this option if you want to use your own database and log backups of your primary databases.</span></span> <span data-ttu-id="5355b-201">자세한 내용은 [AlwaysOn 보조 데이터베이스에서 데이터 이동 시작&#40;SQL Server&#41;](start-data-movement-on-an-always-on-secondary-database-sql-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5355b-201">For more information, see [Start Data Movement on an AlwaysOn Secondary Database &#40;SQL Server&#41;](start-data-movement-on-an-always-on-secondary-database-sql-server.md).</span></span>  
  
9. <span data-ttu-id="5355b-202">**유효성 검사** 페이지에서는 이 마법사에서 지정한 값이 새 가용성 그룹 마법사의 요구 사항을 충족하는지 여부를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="5355b-202">The **Validation** page verifies whether the values you specified in this Wizard meet the requirements of the New Availability Group Wizard.</span></span> <span data-ttu-id="5355b-203">변경하려면 **이전** 을 클릭하여 이전 마법사 페이지로 돌아가서 하나 이상의 값을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="5355b-203">To make a change, click **Previous** to return to an earlier wizard page to change one or more values.</span></span> <span data-ttu-id="5355b-204">**다음** 을 클릭하여 **유효성 검사** 페이지로 돌아가서 **유효성 검사 다시 실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5355b-204">The click **Next** to return to the **Validation** page, and click **Re-run Validation**.</span></span>  
  
10. <span data-ttu-id="5355b-205">**요약** 페이지에서 새 가용성 그룹에 대한 선택 사항을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="5355b-205">On the **Summary** page, review your choices for the new availability group.</span></span> <span data-ttu-id="5355b-206">변경하려면 **이전** 을 클릭하여 관련 페이지로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="5355b-206">To make a change, click **Previous** to return to the relevant page.</span></span> <span data-ttu-id="5355b-207">변경 후에는 **다음** 을 클릭하여 **요약** 페이지로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="5355b-207">After making the change, click **Next** to return to the **Summary** page.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="5355b-208">새 가용성 복제본을 호스팅할 서버 인스턴스의 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 서비스 계정이 로그인으로 존재하지 않는 경우 새 가용성 그룹 마법사에서 로그인을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5355b-208">When the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] service account of a server instance that will host a new availability replica does not already exist as a login, the New Availability Group Wizard needs to create the login.</span></span> <span data-ttu-id="5355b-209">**요약** 페이지에 만들 로그인에 대한 정보가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="5355b-209">On the **Summary** page, the wizard displays the information for the login that is to be created.</span></span> <span data-ttu-id="5355b-210">**마침**을 클릭하면 SQL Server 서비스 계정에 대해 이 로그인이 만들어지고 로그인에 CONNECT 권한이 부여됩니다.</span><span class="sxs-lookup"><span data-stu-id="5355b-210">If you click **Finish**, the wizard creates this login for the SQL Server service account and grants the login CONNECT permission.</span></span>  
  
     <span data-ttu-id="5355b-211">선택이 완료되었으면 필요에 따라 **스크립트** 를 클릭하여 마법사에서 실행할 단계에 대한 스크립트를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5355b-211">If you are satisfied with your selections, optionally click **Script** to create a script of the steps the wizard will execute.</span></span> <span data-ttu-id="5355b-212">새 가용성 그룹을 만들어 구성하려면 **마침**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5355b-212">Then, to create and configure the new availability group, click **Finish**.</span></span>  
  
11. <span data-ttu-id="5355b-213">**진행률** 페이지에 가용성 그룹을 만들기 위한 단계(엔드포인트 구성, 가용성 그룹 만들기 및 가용성 그룹에 보조 복제본 조인)의 진행 상태가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="5355b-213">The **Progress** page displays the progress of the steps for creating the availability group (configuring endpoints, creating the availability group, and joining the secondary replica to the group).</span></span>  
  
12. <span data-ttu-id="5355b-214">이러한 단계가 완료되면 **결과** 페이지에 각 단계의 결과가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="5355b-214">When these steps complete, the **Results** page displays the result of each step.</span></span> <span data-ttu-id="5355b-215">단계가 모두 성공하면 새 가용성 그룹이 완전히 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="5355b-215">If all these steps succeed, the new availability group is completely configured.</span></span> <span data-ttu-id="5355b-216">어느 단계에서라도 오류가 발생하는 경우 수동으로 구성을 완료하거나 실패한 단계에 대해 마법사를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5355b-216">If any of the steps result in an error, you might need to manually complete the configuration or use a wizard for the failed step.</span></span> <span data-ttu-id="5355b-217">주어진 오류의 원인에 대한 자세한 내용을 보려면 **결과** 열에서 연결된 "오류" 링크를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5355b-217">For information about the cause of a given error, click the associated "Error" link in the **Result** column.</span></span>  
  
     <span data-ttu-id="5355b-218">마법사가 완료되면 **닫기** 를 클릭하여 종료합니다.</span><span class="sxs-lookup"><span data-stu-id="5355b-218">When the wizard completes, click **Close** to exit.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="5355b-219">관련 작업</span><span class="sxs-lookup"><span data-stu-id="5355b-219">Related Tasks</span></span>  
 <span data-ttu-id="5355b-220">**가용성 그룹 구성을 완료하려면**</span><span class="sxs-lookup"><span data-stu-id="5355b-220">**To complete availability group configuration**</span></span>  
  
-   [<span data-ttu-id="5355b-221">가용성 그룹에 보조 복제본 조인&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="5355b-221">Join a Secondary Replica to an Availability Group &#40;SQL Server&#41;</span></span>](join-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="5355b-222">가용성 그룹에 대한 보조 데이터베이스 준비&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="5355b-222">Manually Prepare a Secondary Database for an Availability Group &#40;SQL Server&#41;</span></span>](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="5355b-223">가용성 그룹에 보조 데이터베이스 조인&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="5355b-223">Join a Secondary Database to an Availability Group &#40;SQL Server&#41;</span></span>](join-a-secondary-database-to-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="5355b-224">가용성 그룹 수신기 만들기 또는 구성&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="5355b-224">Create or Configure an Availability Group Listener &#40;SQL Server&#41;</span></span>](create-or-configure-an-availability-group-listener-sql-server.md)  
  
 <span data-ttu-id="5355b-225">**가용성 그룹을 만드는 다른 방법**</span><span class="sxs-lookup"><span data-stu-id="5355b-225">**Alternative ways to create an availability group**</span></span>  
  
-   [<span data-ttu-id="5355b-226">새 가용성 그룹 대화 상자 사용&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="5355b-226">Use the New Availability Group Dialog Box &#40;SQL Server Management Studio&#41;</span></span>](use-the-new-availability-group-dialog-box-sql-server-management-studio.md)  
  
-   [<span data-ttu-id="5355b-227">가용성 그룹 만들기&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="5355b-227">Create an Availability Group &#40;Transact-SQL&#41;</span></span>](create-an-availability-group-transact-sql.md)  
  
-   [<span data-ttu-id="5355b-228">가용성 그룹 만들기&#40;SQL Server PowerShell&#41;</span><span class="sxs-lookup"><span data-stu-id="5355b-228">Create an Availability Group &#40;SQL Server PowerShell&#41;</span></span>](../../../powershell/sql-server-powershell.md)  
  
 <span data-ttu-id="5355b-229">**AlwaysOn 가용성 그룹을 사용하도록 설정하려면**</span><span class="sxs-lookup"><span data-stu-id="5355b-229">**To enable AlwaysOn Availability Groups**</span></span>  
  
-   [<span data-ttu-id="5355b-230">AlwaysOn 가용성 그룹 활성화 및 비활성화&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="5355b-230">Enable and Disable AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](enable-and-disable-always-on-availability-groups-sql-server.md)  
  
 <span data-ttu-id="5355b-231">**데이터베이스 미러링 엔드포인트를 구성하려면**</span><span class="sxs-lookup"><span data-stu-id="5355b-231">**To configure a database mirroring endpoint**</span></span>  
  
-   [<span data-ttu-id="5355b-232">AlwaysOn 가용성 그룹 &#40;SQL Server PowerShell에 대 한 데이터베이스 미러링 끝점을 만듭니다&#41;</span><span class="sxs-lookup"><span data-stu-id="5355b-232">Create a Database Mirroring Endpoint for AlwaysOn Availability Groups &#40;SQL Server PowerShell&#41;</span></span>](database-mirroring-always-on-availability-groups-powershell.md)  
  
-   [<span data-ttu-id="5355b-233">Windows 인증에 대한 데이터베이스 미러링 엔드포인트 만들기&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="5355b-233">Create a Database Mirroring Endpoint for Windows Authentication &#40;Transact-SQL&#41;</span></span>](../../database-mirroring/create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md)  
  
-   [<span data-ttu-id="5355b-234">데이터베이스 미러링 엔드포인트에 대한 인증서 사용&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="5355b-234">Use Certificates for a Database Mirroring Endpoint &#40;Transact-SQL&#41;</span></span>](../../database-mirroring/use-certificates-for-a-database-mirroring-endpoint-transact-sql.md)  
  
-   [<span data-ttu-id="5355b-235">가용성 복제본 추가 또는 수정 시 엔드포인트 URL 지정&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="5355b-235">Specify the Endpoint URL When Adding or Modifying an Availability Replica &#40;SQL Server&#41;</span></span>](specify-endpoint-url-adding-or-modifying-availability-replica.md)  
  
 <span data-ttu-id="5355b-236">**AlwaysOn 가용성 그룹 구성 문제를 해결하려면**</span><span class="sxs-lookup"><span data-stu-id="5355b-236">**To troubleshoot AlwaysOn Availability Groups configuration**</span></span>  
  
-   [<span data-ttu-id="5355b-237">삭제&#41;SQL Server AlwaysOn 가용성 그룹 구성 &#40;문제 해결</span><span class="sxs-lookup"><span data-stu-id="5355b-237">Troubleshoot AlwaysOn Availability Groups Configuration &#40;SQL Server&#41;deleted</span></span>](troubleshoot-always-on-availability-groups-configuration-sql-server.md)  
  
-   [<span data-ttu-id="5355b-238">실패 한 파일 추가 작업 문제 해결 AlwaysOn 가용성 그룹 &#40;&#41;</span><span class="sxs-lookup"><span data-stu-id="5355b-238">Troubleshoot a Failed Add-File Operation &#40;AlwaysOn Availability Groups&#41;</span></span>](troubleshoot-a-failed-add-file-operation-always-on-availability-groups.md)  
  
##  <a name="related-content"></a><a name="RelatedContent"></a> <span data-ttu-id="5355b-239">관련 내용</span><span class="sxs-lookup"><span data-stu-id="5355b-239">Related Content</span></span>  
  
-   <span data-ttu-id="5355b-240">**블로그:**</span><span class="sxs-lookup"><span data-stu-id="5355b-240">**Blogs:**</span></span>  
  
     [<span data-ttu-id="5355b-241">AlwaysON - HADRON 학습 시리즈: HADRON 지원 데이터베이스에 대한 작업자 풀 사용</span><span class="sxs-lookup"><span data-stu-id="5355b-241">AlwaysON - HADRON Learning Series: Worker Pool Usage for HADRON Enabled Databases</span></span>](https://blogs.msdn.com/b/psssql/archive/2012/05/17/alwayson-hadron-learning-series-worker-pool-usage-for-hadron-enabled-databases.aspx)  
  
     [<span data-ttu-id="5355b-242">SQL Server AlwaysOn 팀 블로그: 공식 SQL Server AlwaysOn 팀 블로그</span><span class="sxs-lookup"><span data-stu-id="5355b-242">SQL Server AlwaysOn Team Blogs: The official SQL Server AlwaysOn Team Blog</span></span>](https://blogs.msdn.com/b/sqlalwayson/)  
  
     [<span data-ttu-id="5355b-243">CSS SQL Server 엔지니어 블로그</span><span class="sxs-lookup"><span data-stu-id="5355b-243">CSS SQL Server Engineers Blogs</span></span>](https://blogs.msdn.com/b/psssql/)  
  
-   <span data-ttu-id="5355b-244">**비디오:**</span><span class="sxs-lookup"><span data-stu-id="5355b-244">**Videos:**</span></span>  
  
     [<span data-ttu-id="5355b-245">Microsoft SQL Server 코드 이름 "Denali" AlwaysOn 시리즈, 1부: 차세대 고가용성 솔루션 소개</span><span class="sxs-lookup"><span data-stu-id="5355b-245">Microsoft SQL Server Code-Named "Denali" AlwaysOn Series,Part 1: Introducing the Next Generation High Availability Solution</span></span>](https://channel9.msdn.com/Events/TechEd/NorthAmerica/2011/DBI302)  
  
     [<span data-ttu-id="5355b-246">Microsoft SQL Server 코드 이름 "Denali" AlwaysOn 시리즈, 파트 2: AlwaysOn을 사용하여 중요 환경 고가용성 솔루션 빌드</span><span class="sxs-lookup"><span data-stu-id="5355b-246">Microsoft SQL Server Code-Named "Denali" AlwaysOn Series,Part 2: Building a Mission-Critical High Availability Solution Using AlwaysOn</span></span>](https://channel9.msdn.com/Events/TechEd/NorthAmerica/2011/DBI404)  
  
-   <span data-ttu-id="5355b-247">**백서:**</span><span class="sxs-lookup"><span data-stu-id="5355b-247">**Whitepapers:**</span></span>  
  
     [<span data-ttu-id="5355b-248">고가용성 및 재해 복구를 위한 Microsoft SQL Server AlwaysOn 솔루션 가이드</span><span class="sxs-lookup"><span data-stu-id="5355b-248">Microsoft SQL Server AlwaysOn Solutions Guide for High Availability and Disaster Recovery</span></span>](https://go.microsoft.com/fwlink/?LinkId=227600)  
  
     [<span data-ttu-id="5355b-249">SQL Server 2012에 대한 Microsoft 백서</span><span class="sxs-lookup"><span data-stu-id="5355b-249">Microsoft White Papers for SQL Server 2012</span></span>](https://msdn.microsoft.com/library/hh403491.aspx)  
  
     [<span data-ttu-id="5355b-250">SQL Server 고객 자문 팀 백서</span><span class="sxs-lookup"><span data-stu-id="5355b-250">SQL Server Customer Advisory Team Whitepapers</span></span>](http://sqlcat.com/)  
  
## <a name="see-also"></a><span data-ttu-id="5355b-251">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5355b-251">See Also</span></span>  
 <span data-ttu-id="5355b-252">[데이터베이스 미러링 엔드포인트&#40;SQL Server&#41;](../../database-mirroring/the-database-mirroring-endpoint-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="5355b-252">[The Database Mirroring Endpoint &#40;SQL Server&#41;](../../database-mirroring/the-database-mirroring-endpoint-sql-server.md) </span></span>  
 <span data-ttu-id="5355b-253">[AlwaysOn 가용성 그룹 &#40;SQL Server 개요&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="5355b-253">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 [<span data-ttu-id="5355b-254">AlwaysOn 가용성 그룹 &#40;SQL Server에 대 한 필수 조건, 제한 사항 및 권장 사항&#41;</span><span class="sxs-lookup"><span data-stu-id="5355b-254">Prerequisites, Restrictions, and Recommendations for AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](prereqs-restrictions-recommendations-always-on-availability.md)  
  
