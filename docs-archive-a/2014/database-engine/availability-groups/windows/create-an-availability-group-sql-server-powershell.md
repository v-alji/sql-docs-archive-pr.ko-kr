---
title: 가용성 그룹 만들기(SQL Server PowerShell) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], creating
ms.assetid: bc69a7df-20fa-41e1-9301-11317c5270d2
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 3af9bf896b954e6849c0d491f9ed267655369ccb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743459"
---
# <a name="create-an-availability-group-sql-server-powershell"></a><span data-ttu-id="c90f8-102">가용성 그룹 만들기(SQL Server PowerShell)</span><span class="sxs-lookup"><span data-stu-id="c90f8-102">Create an Availability Group (SQL Server PowerShell)</span></span>
  <span data-ttu-id="c90f8-103">이 항목에서는 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]에서 PowerShell cmdlet을 사용하여 AlwaysOn 가용성 그룹을 만들고 구성하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="c90f8-103">This topic describes how to use PowerShell cmdlets to create and configure an AlwaysOn availability group by using PowerShell in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="c90f8-104">*가용성 그룹* 은 단일 단위로 장애 조치(Failover)될 사용자 데이터베이스 집합과 장애 조치(Failover)를 지원하는 장애 조치(Failover) 파트너 집합( *가용성 복제본*이라고 함)을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="c90f8-104">An *availability group* defines a set of user databases that will fail over as a single unit and a set of failover partners, known as *availability replicas*, which support failover.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c90f8-105">가용성 그룹에 대한 소개는 [AlwaysOn 가용성 그룹 개요&#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c90f8-105">For an introduction to availability groups, see [Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md).</span></span>  

> [!NOTE]  
>  <span data-ttu-id="c90f8-106">PowerShell cmdlet을 사용하는 대신 가용성 그룹 만들기 마법사나 [!INCLUDE[tsql](../../../includes/tsql-md.md)]을 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c90f8-106">As an alternative to using PowerShell cmdlets, you can use the Create Availability Group wizard or [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span> <span data-ttu-id="c90f8-107">자세한 내용은 [새 가용성 그룹 대화 상자 사용&#40;SQL Server Management Studio&#41;](use-the-new-availability-group-dialog-box-sql-server-management-studio.md) 또는 [가용성 그룹 만들기&#40;Transact-SQL&#41;](create-an-availability-group-transact-sql.md)에서 PowerShell cmdlet을 사용하여 Always On 가용성 그룹을 만들고 구성하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="c90f8-107">For more information, see [Use the New Availability Group Dialog Box &#40;SQL Server Management Studio&#41;](use-the-new-availability-group-dialog-box-sql-server-management-studio.md) or [Create an Availability Group &#40;Transact-SQL&#41;](create-an-availability-group-transact-sql.md).</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="c90f8-108">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="c90f8-108">Before You Begin</span></span>  
 <span data-ttu-id="c90f8-109">가용성 그룹을 처음 만들어 보는 경우 이 섹션을 먼저 읽는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="c90f8-109">We strongly recommend that you read this section before attempting to create your first availability group.</span></span>  
  
###  <a name="prerequisites-restrictions-and-recommendations"></a><a name="PrerequisitesRestrictions"></a> <span data-ttu-id="c90f8-110">필수 구성 요소, 제한 사항 및 권장 사항</span><span class="sxs-lookup"><span data-stu-id="c90f8-110">Prerequisites, Restrictions, and Recommendations</span></span>  
  
-   <span data-ttu-id="c90f8-111">가용성 그룹을 만들기 전에 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 의 호스트 인스턴스가 각각 단일 WSFC 장애 조치(Failover) 클러스터 내의 다른 WSFC(Windows Server 장애 조치(Failover) 클러스터링) 노드에 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="c90f8-111">Before creating an availability group, verify that the host instances of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] each resides on a different Windows Server Failover Clustering (WSFC) node of a single WSFC failover cluster.</span></span> <span data-ttu-id="c90f8-112">또한 해당 서버 인스턴스가 다른 서버 인스턴스의 사전 요구 사항을 충족하는지와 다른 모든 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 요구 사항을 충족하는지, 그리고 현재 권장 사항을 알고 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="c90f8-112">Also, verify that your server instances met the other server-instance prerequisites and that all of the other [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] requirements are meet and that you are aware of the recommendations.</span></span> <span data-ttu-id="c90f8-113">자세한 내용은 [AlwaysOn 가용성 그룹에 대한 필수 조건, 제한 사항 및 권장 사항&#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c90f8-113">For more information, we strongly recommend that you read [Prerequisites, Restrictions, and Recommendations for AlwaysOn Availability Groups &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="c90f8-114">보안</span><span class="sxs-lookup"><span data-stu-id="c90f8-114">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="c90f8-115">권한</span><span class="sxs-lookup"><span data-stu-id="c90f8-115">Permissions</span></span>  
 <span data-ttu-id="c90f8-116">CREATE AVAILABILITY GROUP 서버 권한, ALTER ANY AVAILABILITY GROUP 권한, CONTROL SERVER 권한 중 하나와 **sysadmin** 고정 서버 역할의 멤버 자격이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="c90f8-116">Requires membership in the **sysadmin** fixed server role and either CREATE AVAILABILITY GROUP server permission, ALTER ANY AVAILABILITY GROUP permission, or CONTROL SERVER permission.</span></span>  
  
###  <a name="summary-of-tasks-and-corresponding-powershell-cmdlets"></a><a name="SummaryPSStatements"></a><span data-ttu-id="c90f8-117">태스크 및 해당 PowerShell Cmdlet 요약</span><span class="sxs-lookup"><span data-stu-id="c90f8-117">Summary of Tasks and Corresponding PowerShell Cmdlets</span></span>  
 <span data-ttu-id="c90f8-118">다음 표에서는 가용성 그룹을 구성하는 데 필요한 기본 태스크와 PowerShell cmdlet이 지원하는 기능을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="c90f8-118">The following table lists the basic tasks involved in configuring an availability group and indicates those that are supported by PowerShell cmdlets.</span></span> <span data-ttu-id="c90f8-119">[!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 태스크는 표에 나오는 순서대로 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c90f8-119">The [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] tasks must be performed in the sequence in which they are presented in the table.</span></span>  
  
|<span data-ttu-id="c90f8-120">Task</span><span class="sxs-lookup"><span data-stu-id="c90f8-120">Task</span></span>|<span data-ttu-id="c90f8-121">PowerShell cmdlet(사용 가능한 경우) 또는 Transact-SQL 문</span><span class="sxs-lookup"><span data-stu-id="c90f8-121">PowerShell Cmdlets (if Available) or Transact-SQL Statement</span></span>|<span data-ttu-id="c90f8-122">태스크를 수행할 위치**<sup>\*</sup>**</span><span class="sxs-lookup"><span data-stu-id="c90f8-122">Where to Perform Task**<sup>\*</sup>**</span></span>|  
|----------|--------------------------------------------------------------------|-------------------------------------------|  
|<span data-ttu-id="c90f8-123">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인스턴스당 하나의 데이터베이스 미러링 엔드포인트 만들기</span><span class="sxs-lookup"><span data-stu-id="c90f8-123">Create database mirroring endpoint (once per [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instance)</span></span>|`New-SqlHadrEndPoint`|<span data-ttu-id="c90f8-124">데이터베이스 미러링 엔드포인트가 없는 각 서버 인스턴스에서 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="c90f8-124">Execute on each server instance that lacks database mirroring endpoint.</span></span><br /><br /> <span data-ttu-id="c90f8-125">참고: 기존 데이터베이스 미러링 엔드포인트를 변경하려면 `Set-SqlHadrEndpoint`를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="c90f8-125">Note: To alter an existing database mirroring endpoint, use `Set-SqlHadrEndpoint`.</span></span>|  
|<span data-ttu-id="c90f8-126">가용성 그룹 만들기</span><span class="sxs-lookup"><span data-stu-id="c90f8-126">Create availability group</span></span>|<span data-ttu-id="c90f8-127">먼저 `New-SqlAvailabilityReplica` cmdlet과 `-AsTemplate` 매개 변수를 사용하여 가용성 그룹에 포함할 두 개의 각 가용성 복제본에 대한 메모리 내 가용성 복제본 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c90f8-127">First, use the `New-SqlAvailabilityReplica` cmdlet with the `-AsTemplate` parameter to create an in-memory availability-replica object for each of the two availability replicas that you plan to include in the availability group.</span></span><br /><br /> <span data-ttu-id="c90f8-128">그런 다음 `New-SqlAvailabilityGroup` cmdlet을 사용하고 가용성 복제본 개체를 참조하여 가용성 그룹을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c90f8-128">Then, create the availability group by using the `New-SqlAvailabilityGroup` cmdlet and referencing your availability-replica objects.</span></span>|<span data-ttu-id="c90f8-129">초기 주 복제본을 호스트할 서버 인스턴스에서 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="c90f8-129">Execute on the server instance that is to host the initial primary replica.</span></span>|  
|<span data-ttu-id="c90f8-130">가용성 그룹에 보조 복제본 조인</span><span class="sxs-lookup"><span data-stu-id="c90f8-130">Join secondary replica to availability group</span></span>|`Join-SqlAvailabilityGroup`|<span data-ttu-id="c90f8-131">보조 복제본을 호스트할 각 서버 인스턴스에서 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="c90f8-131">Execute on each server instance that is hosts a secondary replica.</span></span>|  
|<span data-ttu-id="c90f8-132">보조 데이터베이스 준비</span><span class="sxs-lookup"><span data-stu-id="c90f8-132">Prepare the secondary database</span></span>|<span data-ttu-id="c90f8-133">`Backup-SqlDatabase` 및 `Restore-SqlDatabase`</span><span class="sxs-lookup"><span data-stu-id="c90f8-133">`Backup-SqlDatabase` and `Restore-SqlDatabase`</span></span>|<span data-ttu-id="c90f8-134">주 복제본을 호스트하는 서버 인스턴스에 백업을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c90f8-134">Create backups on the server instance that hosts the primary replica.</span></span><br /><br /> <span data-ttu-id="c90f8-135">`NoRecovery` 복원 매개 변수를 사용하여 보조 복제본을 호스팅하는 각 서버 인스턴스에 백업을 복원합니다.</span><span class="sxs-lookup"><span data-stu-id="c90f8-135">Restore backups on each server instance that hosts a secondary replica, using the `NoRecovery` restore parameter.</span></span> <span data-ttu-id="c90f8-136">또한 주 복제본을 호스팅하는 컴퓨터와 대상 보조 복제본을 호스팅하는 컴퓨터의 파일 경로가 다른 경우 `RelocateFile` 복원 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="c90f8-136">If the file paths differ between the computers that host the primary replica and the target secondary replica, also use the `RelocateFile` restore parameter.</span></span>|  
|<span data-ttu-id="c90f8-137">가용성 그룹에 각 보조 데이터베이스를 조인하여 데이터 동기화 시작</span><span class="sxs-lookup"><span data-stu-id="c90f8-137">Start data synchronization by joining each secondary database to availability group</span></span>|`Add-SqlAvailabilityDatabase`|<span data-ttu-id="c90f8-138">보조 복제본을 호스트하는 각 서버 인스턴스에서 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="c90f8-138">Execute on each server instance that hosts a secondary replica.</span></span>|  
  
 <span data-ttu-id="c90f8-139">**<sup>\*</sup>** 지정 된 태스크를 수행 하려면 디렉터리를 `cd` 표시 된 서버 인스턴스로 변경 합니다 ().</span><span class="sxs-lookup"><span data-stu-id="c90f8-139">**<sup>\*</sup>**  To perform a given task, change directory (`cd`) to the indicated server instance or instances.</span></span>  
  
###  <a name="to-set-up-and-use-the-sql-server-powershell-provider"></a><a name="PsProviderLinks"></a><span data-ttu-id="c90f8-140">SQL Server PowerShell 공급자를 설정 하 고 사용 하려면</span><span class="sxs-lookup"><span data-stu-id="c90f8-140">To Set Up and Use the SQL Server PowerShell Provider</span></span>  
  
-   [<span data-ttu-id="c90f8-141">SQL Server PowerShell 공급자</span><span class="sxs-lookup"><span data-stu-id="c90f8-141">SQL Server PowerShell Provider</span></span>](../../../powershell/sql-server-powershell-provider.md)  
  
-   [<span data-ttu-id="c90f8-142">Get Help SQL Server PowerShell</span><span class="sxs-lookup"><span data-stu-id="c90f8-142">Get Help SQL Server PowerShell</span></span>](../../../powershell/sql-server-powershell.md)  
  
##  <a name="using-powershell-to-create-and-configure-an-availability-group"></a><a name="PowerShellProcedure"></a><span data-ttu-id="c90f8-143">PowerShell을 사용 하 여 가용성 그룹 만들기 및 구성</span><span class="sxs-lookup"><span data-stu-id="c90f8-143">Using PowerShell to Create and Configure an Availability Group</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c90f8-144">특정 cmdlet의 구문 및 예를 보려면 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell 환경에서 `Get-Help` cmdlet을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="c90f8-144">To view the syntax and an example of a given cmdlet, use the `Get-Help` cmdlet in the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell environment.</span></span> <span data-ttu-id="c90f8-145">자세한 내용은 [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c90f8-145">For more information, see [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).</span></span>  
  
1.  <span data-ttu-id="c90f8-146">주 복제본을 호스팅할 서버 인스턴스로 디렉터리를 변경(`cd`)합니다.</span><span class="sxs-lookup"><span data-stu-id="c90f8-146">Change directory (`cd`) to the server instance that is to host the primary replica.</span></span>  
  
2.  <span data-ttu-id="c90f8-147">주 복제본에 대한 메모리 내 가용성 복제본 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c90f8-147">Create an in-memory availability-replica object for the primary replica.</span></span>  
  
3.  <span data-ttu-id="c90f8-148">각 보조 복제본에 대한 메모리 내 가용성 복제본 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c90f8-148">Create an in-memory availability-replica object for each of the secondary replicas.</span></span>  
  
4.  <span data-ttu-id="c90f8-149">가용성 그룹을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c90f8-149">Create the availability group.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="c90f8-150">가용성 그룹 이름의 최대 길이는 128자입니다.</span><span class="sxs-lookup"><span data-stu-id="c90f8-150">The maximum length for an availability group name is 128 characters.</span></span>  
  
5.  <span data-ttu-id="c90f8-151">새 보조 복제본을 가용성 그룹에 조인합니다.</span><span class="sxs-lookup"><span data-stu-id="c90f8-151">Join the new secondary replica to the availability group.</span></span> <span data-ttu-id="c90f8-152">자세한 내용은 [가용성 그룹에 보조 복제본 조인&#40;SQL Server&#41;](join-a-secondary-replica-to-an-availability-group-sql-server.md)또는 PowerShell을 사용하여 Always On 가용성 그룹에 보조 데이터베이스를 조인하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="c90f8-152">For more information, see [Join a Secondary Replica to an Availability Group &#40;SQL Server&#41;](join-a-secondary-replica-to-an-availability-group-sql-server.md).</span></span>  
  
6.  <span data-ttu-id="c90f8-153">가용성 그룹의 각 데이터베이스에 대해 RESTORE WITH NORECOVERY를 사용하여 주 데이터베이스의 최신 백업을 복원하는 방법으로 보조 데이터베이스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c90f8-153">For each database in the availability group, create a secondary database by restoring recent backups of the primary database, using RESTORE WITH NORECOVERY.</span></span>  
  
7.  <span data-ttu-id="c90f8-154">모든 새 보조 데이터베이스를 가용성 그룹에 조인합니다.</span><span class="sxs-lookup"><span data-stu-id="c90f8-154">Join every new secondary database to the availability group.</span></span> <span data-ttu-id="c90f8-155">자세한 내용은 [가용성 그룹에 보조 복제본 조인&#40;SQL Server&#41;](join-a-secondary-replica-to-an-availability-group-sql-server.md)또는 PowerShell을 사용하여 Always On 가용성 그룹에 보조 데이터베이스를 조인하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="c90f8-155">For more information, see [Join a Secondary Replica to an Availability Group &#40;SQL Server&#41;](join-a-secondary-replica-to-an-availability-group-sql-server.md).</span></span>  
  
8.  <span data-ttu-id="c90f8-156">필요한 경우 Windows `dir` 명령을 사용하여 새 가용성 그룹의 내용을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="c90f8-156">Optionally, use the Windows `dir` command to verify the contents of the new availability group.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c90f8-157">서버 인스턴스의 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 서비스 계정이 다른 도메인 사용자 계정으로 실행되는 경우에는 각 서버 인스턴스에서 다른 서버 인스턴스에 대한 로그인을 만들고 로컬 데이터베이스 미러링 엔드포인트에 이 로그인 CONNECT 권한을 부여합니다.</span><span class="sxs-lookup"><span data-stu-id="c90f8-157">If the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] service accounts of the server instances run under different domain user accounts, on each server instance, create a login for the other server instance and grant this login CONNECT permission to the local database mirroring endpoint.</span></span>  
  
##  <a name="example-using-powershell-to-create-an-availability-group"></a><a name="ExampleConfigureGroup"></a><span data-ttu-id="c90f8-158">예: PowerShell을 사용 하 여 가용성 그룹 만들기</span><span class="sxs-lookup"><span data-stu-id="c90f8-158">Example: Using PowerShell to Create an Availability Group</span></span>  
 <span data-ttu-id="c90f8-159">다음 PowerShell 예에서는 가용성 복제본 두 개와 가용성 데이터베이스 한 개가 포함된 `MyAG` 라는 단순한 가용성 그룹을 만들고 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="c90f8-159">The following PowerShell example creates and configures a simple availability group named `MyAG` with two availability replicas and one availability database.</span></span> <span data-ttu-id="c90f8-160">예:</span><span class="sxs-lookup"><span data-stu-id="c90f8-160">The example:</span></span>  
  
1.  <span data-ttu-id="c90f8-161">`MyDatabase` 와 해당 트랜잭션 로그를 백업합니다.</span><span class="sxs-lookup"><span data-stu-id="c90f8-161">Backs up `MyDatabase` and its transaction log.</span></span>  
  
2.  <span data-ttu-id="c90f8-162">`-NoRecovery` 옵션을 사용하여 `MyDatabase` 및 해당 트랜잭션 로그를 복원합니다.</span><span class="sxs-lookup"><span data-stu-id="c90f8-162">Restores `MyDatabase` and its transaction log, using the `-NoRecovery` option.</span></span>  
  
3.  <span data-ttu-id="c90f8-163">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 의 로컬 인스턴스에 의해 호스트될 주 복제본의 메모리 내 표현을 만듭니다( `PrimaryComputer\Instance`).</span><span class="sxs-lookup"><span data-stu-id="c90f8-163">Creates an in-memory representation of the primary replica, which will be hosted by the local instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (named `PrimaryComputer\Instance`).</span></span>  
  
4.  <span data-ttu-id="c90f8-164">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인스턴스에 의해 호스트될 보조 복제본의 메모리 내 표현을 만듭니다( `SecondaryComputer\Instance`).</span><span class="sxs-lookup"><span data-stu-id="c90f8-164">Creates an in-memory representation of the secondary replica, which will be hosted by an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (named `SecondaryComputer\Instance`).</span></span>  
  
5.  <span data-ttu-id="c90f8-165">`MyAG`라는 가용성 그룹을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c90f8-165">Creates an availability group named `MyAG`.</span></span>  
  
6.  <span data-ttu-id="c90f8-166">보조 복제본을 가용성 그룹에 조인합니다.</span><span class="sxs-lookup"><span data-stu-id="c90f8-166">Joins the secondary replica to the availability group.</span></span>  
  
7.  <span data-ttu-id="c90f8-167">보조 데이터베이스를 가용성 그룹에 조인합니다.</span><span class="sxs-lookup"><span data-stu-id="c90f8-167">Joins the secondary database to the availability group.</span></span>  
  
```powershell
# Backup my database and its log on the primary  
Backup-SqlDatabase `  
    -Database "MyDatabase" `  
    -BackupFile "\\share\backups\MyDatabase.bak" `  
    -ServerInstance "PrimaryComputer\Instance"  
  
Backup-SqlDatabase `  
    -Database "MyDatabase" `  
    -BackupFile "\\share\backups\MyDatabase.log" `  
    -ServerInstance "PrimaryComputer\Instance" `  
    -BackupAction Log   
  
# Restore the database and log on the secondary (using NO RECOVERY)  
Restore-SqlDatabase `  
    -Database "MyDatabase" `  
    -BackupFile "\\share\backups\MyDatabase.bak" `  
    -ServerInstance "SecondaryComputer\Instance" `  
    -NoRecovery  
  
Restore-SqlDatabase `  
    -Database "MyDatabase" `  
    -BackupFile "\\share\backups\MyDatabase.log" `  
    -ServerInstance "SecondaryComputer\Instance" `  
    -RestoreAction Log `  
    -NoRecovery  
  
# Create an in-memory representation of the primary replica.  
$primaryReplica = New-SqlAvailabilityReplica `  
    -Name "PrimaryComputer\Instance" `  
    -EndpointURL "TCP://PrimaryComputer.domain.com:5022" `  
    -AvailabilityMode "SynchronousCommit" `  
    -FailoverMode "Automatic" `  
    -Version 12 `  
    -AsTemplate  
  
# Create an in-memory representation of the secondary replica.  
$secondaryReplica = New-SqlAvailabilityReplica `  
    -Name "SecondaryComputer\Instance" `  
    -EndpointURL "TCP://SecondaryComputer.domain.com:5022" `  
    -AvailabilityMode "SynchronousCommit" `  
    -FailoverMode "Automatic" `  
    -Version 12 `  
    -AsTemplate  
  
# Create the availability group  
New-SqlAvailabilityGroup `  
    -Name "MyAG" `  
    -Path "SQLSERVER:\SQL\PrimaryComputer\Instance" `  
    -AvailabilityReplica @($primaryReplica,$secondaryReplica) `  
    -Database "MyDatabase"  
  
# Join the secondary replica to the availability group.  
Join-SqlAvailabilityGroup -Path "SQLSERVER:\SQL\SecondaryComputer\Instance" -Name "MyAG"  
  
# Join the secondary database to the availability group.  
Add-SqlAvailabilityDatabase -Path "SQLSERVER:\SQL\SecondaryComputer\Instance\AvailabilityGroups\MyAG" -Database "MyDatabase"  
```  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="c90f8-168">관련 작업</span><span class="sxs-lookup"><span data-stu-id="c90f8-168">Related Tasks</span></span>  
 <span data-ttu-id="c90f8-169">**AlwaysOn 가용성 그룹에 대한 서버 인스턴스를 구성하려면**</span><span class="sxs-lookup"><span data-stu-id="c90f8-169">**To configure a server instance for AlwaysOn Availability Groups**</span></span>  
  
-   [<span data-ttu-id="c90f8-170">AlwaysOn 가용성 그룹 활성화 및 비활성화&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="c90f8-170">Enable and Disable AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](enable-and-disable-always-on-availability-groups-sql-server.md)  
  
-   [<span data-ttu-id="c90f8-171">AlwaysOn 가용성 그룹 &#40;SQL Server PowerShell에 대 한 데이터베이스 미러링 끝점을 만듭니다&#41;</span><span class="sxs-lookup"><span data-stu-id="c90f8-171">Create a Database Mirroring Endpoint for AlwaysOn Availability Groups &#40;SQL Server PowerShell&#41;</span></span>](database-mirroring-always-on-availability-groups-powershell.md)  
  
 <span data-ttu-id="c90f8-172">**가용성 그룹 및 복제본 속성을 구성하려면**</span><span class="sxs-lookup"><span data-stu-id="c90f8-172">**To configure availability group and replica properties**</span></span>  
  
-   [<span data-ttu-id="c90f8-173">가용성 복제본의 가용성 모드 변경&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="c90f8-173">Change the Availability Mode of an Availability Replica &#40;SQL Server&#41;</span></span>](change-the-availability-mode-of-an-availability-replica-sql-server.md)  
  
-   [<span data-ttu-id="c90f8-174">가용성 복제본의 장애 조치(failover) 모드 변경&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="c90f8-174">Change the Failover Mode of an Availability Replica &#40;SQL Server&#41;</span></span>](change-the-failover-mode-of-an-availability-replica-sql-server.md)  
  
-   [<span data-ttu-id="c90f8-175">가용성 그룹 수신기 만들기 또는 구성&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="c90f8-175">Create or Configure an Availability Group Listener &#40;SQL Server&#41;</span></span>](create-or-configure-an-availability-group-listener-sql-server.md)  
  
-   [<span data-ttu-id="c90f8-176">유연한 장애 조치(failover) 정책을 구성하여 자동 장애 조치의 상태 제어(AlwaysOn 가용성 그룹)</span><span class="sxs-lookup"><span data-stu-id="c90f8-176">Configure the Flexible Failover Policy to Control Conditions for Automatic Failover (AlwaysOn Availability Groups)</span></span>](configure-flexible-automatic-failover-policy.md)  
  
-   [<span data-ttu-id="c90f8-177">가용성 복제본 추가 또는 수정 시 엔드포인트 URL 지정&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="c90f8-177">Specify the Endpoint URL When Adding or Modifying an Availability Replica &#40;SQL Server&#41;</span></span>](specify-endpoint-url-adding-or-modifying-availability-replica.md)  
  
-   [<span data-ttu-id="c90f8-178">가용성 복제본에 백업 구성&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="c90f8-178">Configure Backup on Availability Replicas &#40;SQL Server&#41;</span></span>](configure-backup-on-availability-replicas-sql-server.md)  
  
-   [<span data-ttu-id="c90f8-179">가용성 복제본에 대한 읽기 전용 액세스 구성&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="c90f8-179">Configure Read-Only Access on an Availability Replica &#40;SQL Server&#41;</span></span>](configure-read-only-access-on-an-availability-replica-sql-server.md)  
  
-   [<span data-ttu-id="c90f8-180">가용성 그룹에 대한 읽기 전용 라우팅 구성&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="c90f8-180">Configure Read-Only Routing for an Availability Group &#40;SQL Server&#41;</span></span>](configure-read-only-routing-for-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="c90f8-181">가용성 복제본에 대한 세션 제한 시간 변경&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="c90f8-181">Change the Session-Timeout Period for an Availability Replica &#40;SQL Server&#41;</span></span>](change-the-session-timeout-period-for-an-availability-replica-sql-server.md)  
  
 <span data-ttu-id="c90f8-182">**가용성 그룹 구성을 완료하려면**</span><span class="sxs-lookup"><span data-stu-id="c90f8-182">**To complete availability group configuration**</span></span>  
  
-   [<span data-ttu-id="c90f8-183">가용성 그룹에 보조 복제본 조인&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="c90f8-183">Join a Secondary Replica to an Availability Group &#40;SQL Server&#41;</span></span>](join-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="c90f8-184">가용성 그룹에 대한 보조 데이터베이스 준비&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="c90f8-184">Manually Prepare a Secondary Database for an Availability Group &#40;SQL Server&#41;</span></span>](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="c90f8-185">가용성 그룹에 보조 데이터베이스 조인&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="c90f8-185">Join a Secondary Database to an Availability Group &#40;SQL Server&#41;</span></span>](join-a-secondary-database-to-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="c90f8-186">가용성 그룹 수신기 만들기 또는 구성&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="c90f8-186">Create or Configure an Availability Group Listener &#40;SQL Server&#41;</span></span>](create-or-configure-an-availability-group-listener-sql-server.md)  
  
 <span data-ttu-id="c90f8-187">**가용성 그룹을 만드는 다른 방법**</span><span class="sxs-lookup"><span data-stu-id="c90f8-187">**Alternative ways to create an availability group**</span></span>  
  
-   [<span data-ttu-id="c90f8-188">가용성 그룹 마법사 사용&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="c90f8-188">Use the Availability Group Wizard &#40;SQL Server Management Studio&#41;</span></span>](use-the-availability-group-wizard-sql-server-management-studio.md)  
  
-   [<span data-ttu-id="c90f8-189">새 가용성 그룹 대화 상자 사용&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="c90f8-189">Use the New Availability Group Dialog Box &#40;SQL Server Management Studio&#41;</span></span>](use-the-new-availability-group-dialog-box-sql-server-management-studio.md)  
  
-   [<span data-ttu-id="c90f8-190">가용성 그룹 만들기&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="c90f8-190">Create an Availability Group &#40;Transact-SQL&#41;</span></span>](create-an-availability-group-transact-sql.md)  
  
 <span data-ttu-id="c90f8-191">**AlwaysOn 가용성 그룹 구성 문제를 해결하려면**</span><span class="sxs-lookup"><span data-stu-id="c90f8-191">**To troubleshoot AlwaysOn Availability Groups configuration**</span></span>  
  
-   [<span data-ttu-id="c90f8-192">삭제 된 SQL Server (AlwaysOn 가용성 그룹 구성) 문제 해결</span><span class="sxs-lookup"><span data-stu-id="c90f8-192">Troubleshoot AlwaysOn Availability Groups Configuration (SQL Server)deleted</span></span>](troubleshoot-always-on-availability-groups-configuration-sql-server.md)  
  
-   [<span data-ttu-id="c90f8-193">실패 한 파일 추가 작업 문제 해결 AlwaysOn 가용성 그룹 &#40;&#41;</span><span class="sxs-lookup"><span data-stu-id="c90f8-193">Troubleshoot a Failed Add-File Operation &#40;AlwaysOn Availability Groups&#41;</span></span>](troubleshoot-a-failed-add-file-operation-always-on-availability-groups.md)  
  
##  <a name="related-content"></a><a name="RelatedContent"></a> <span data-ttu-id="c90f8-194">관련 내용</span><span class="sxs-lookup"><span data-stu-id="c90f8-194">Related Content</span></span>  
  
-   <span data-ttu-id="c90f8-195">**블로그:**</span><span class="sxs-lookup"><span data-stu-id="c90f8-195">**Blogs:**</span></span>  
  
     [<span data-ttu-id="c90f8-196">AlwaysON - HADRON 학습 시리즈: HADRON 지원 데이터베이스에 대한 작업자 풀 사용</span><span class="sxs-lookup"><span data-stu-id="c90f8-196">AlwaysON - HADRON Learning Series: Worker Pool Usage for HADRON Enabled Databases</span></span>](https://blogs.msdn.com/b/psssql/archive/2012/05/17/alwayson-hadron-learning-series-worker-pool-usage-for-hadron-enabled-databases.aspx)  
  
     [<span data-ttu-id="c90f8-197">SQL Server PowerShell을 사용하여 AlwaysOn 구성</span><span class="sxs-lookup"><span data-stu-id="c90f8-197">Configuring AlwaysOn with SQL Server PowerShell</span></span>](https://blogs.msdn.com/b/sqlalwayson/archive/2012/02/03/configuring-alwayson-with-sql-server-powershell.aspx)  
  
     [<span data-ttu-id="c90f8-198">SQL Server AlwaysOn 팀 블로그: 공식 SQL Server AlwaysOn 팀 블로그</span><span class="sxs-lookup"><span data-stu-id="c90f8-198">SQL Server AlwaysOn Team Blogs: The official SQL Server AlwaysOn Team Blog</span></span>](https://blogs.msdn.com/b/sqlalwayson/)  
  
     [<span data-ttu-id="c90f8-199">CSS SQL Server 엔지니어 블로그</span><span class="sxs-lookup"><span data-stu-id="c90f8-199">CSS SQL Server Engineers Blogs</span></span>](https://blogs.msdn.com/b/psssql/)  
  
-   <span data-ttu-id="c90f8-200">**비디오:**</span><span class="sxs-lookup"><span data-stu-id="c90f8-200">**Videos:**</span></span>  
  
     [<span data-ttu-id="c90f8-201">Microsoft SQL Server 코드 이름 "Denali" AlwaysOn 시리즈, 1부: 차세대 고가용성 솔루션 소개</span><span class="sxs-lookup"><span data-stu-id="c90f8-201">Microsoft SQL Server Code-Named "Denali" AlwaysOn Series,Part 1: Introducing the Next Generation High Availability Solution</span></span>](https://channel9.msdn.com/Events/TechEd/NorthAmerica/2011/DBI302)  
  
     [<span data-ttu-id="c90f8-202">Microsoft SQL Server 코드 이름 "Denali" AlwaysOn 시리즈, 파트 2: AlwaysOn을 사용하여 중요 환경 고가용성 솔루션 빌드</span><span class="sxs-lookup"><span data-stu-id="c90f8-202">Microsoft SQL Server Code-Named "Denali" AlwaysOn Series,Part 2: Building a Mission-Critical High Availability Solution Using AlwaysOn</span></span>](https://channel9.msdn.com/Events/TechEd/NorthAmerica/2011/DBI404)  
  
-   <span data-ttu-id="c90f8-203">**백서:**</span><span class="sxs-lookup"><span data-stu-id="c90f8-203">**Whitepapers:**</span></span>  
  
     [<span data-ttu-id="c90f8-204">고가용성 및 재해 복구를 위한 Microsoft SQL Server AlwaysOn 솔루션 가이드</span><span class="sxs-lookup"><span data-stu-id="c90f8-204">Microsoft SQL Server AlwaysOn Solutions Guide for High Availability and Disaster Recovery</span></span>](https://go.microsoft.com/fwlink/?LinkId=227600)  
  
     [<span data-ttu-id="c90f8-205">SQL Server 2012에 대한 Microsoft 백서</span><span class="sxs-lookup"><span data-stu-id="c90f8-205">Microsoft White Papers for SQL Server 2012</span></span>](https://msdn.microsoft.com/library/hh403491.aspx)  
  
     [<span data-ttu-id="c90f8-206">SQL Server 고객 자문 팀 백서</span><span class="sxs-lookup"><span data-stu-id="c90f8-206">SQL Server Customer Advisory Team Whitepapers</span></span>](http://sqlcat.com/)  
  
## <a name="see-also"></a><span data-ttu-id="c90f8-207">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c90f8-207">See Also</span></span>  
 [<span data-ttu-id="c90f8-208">데이터베이스 미러링 엔드포인트&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="c90f8-208">The Database Mirroring Endpoint &#40;SQL Server&#41;</span></span>](../../database-mirroring/the-database-mirroring-endpoint-sql-server.md)   
