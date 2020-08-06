---
title: 가용성 그룹 만들기(Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], creating
ms.assetid: 8b0a6301-8b79-4415-b608-b40876f30066
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 57a494af168a8f5572bafe93f8fb47b22a954a19
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743452"
---
# <a name="create-an-availability-group-transact-sql"></a><span data-ttu-id="980ed-102">가용성 그룹 만들기(Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="980ed-102">Create an Availability Group (Transact-SQL)</span></span>
  <span data-ttu-id="980ed-103">이 항목에서는 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 기능이 설정된 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 인스턴스에서 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 을 사용하여 가용성 그룹을 만들고 구성하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="980ed-103">This topic describes how to use [!INCLUDE[tsql](../../../includes/tsql-md.md)] to create and configure an availability group on instances of [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] on which the [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] feature is enabled.</span></span> <span data-ttu-id="980ed-104">*가용성 그룹* 은 단일 단위로 장애 조치(Failover)될 사용자 데이터베이스 집합과 장애 조치(Failover)를 지원하는 장애 조치(Failover) 파트너 집합( *가용성 복제본*이라고 함)을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="980ed-104">An *availability group* defines a set of user databases that will fail over as a single unit and a set of failover partners, known as *availability replicas*, that support failover.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="980ed-105">가용성 그룹에 대한 소개는 [AlwaysOn 가용성 그룹 개요&#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="980ed-105">For an introduction to availability groups, see [Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md).</span></span>  

> [!NOTE]  
>  <span data-ttu-id="980ed-106">[!INCLUDE[tsql](../../../includes/tsql-md.md)]을 사용하는 대신 가용성 그룹 만들기 마법사나 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell cmdlet을 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="980ed-106">As an alternative to using [!INCLUDE[tsql](../../../includes/tsql-md.md)], you can use the Create Availability Group wizard or [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell cmdlets.</span></span> <span data-ttu-id="980ed-107">자세한 내용은 [가용성 그룹 마법사 사용&#40;SQL Server Management Studio&#41;](use-the-availability-group-wizard-sql-server-management-studio.md), [새 가용성 그룹 대화 상자 사용&#40;SQL Server Management Studio&#41;](use-the-new-availability-group-dialog-box-sql-server-management-studio.md)또는 [가용성 그룹 만들기&#40;SQL Server PowerShell&#41;](../../../powershell/sql-server-powershell.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="980ed-107">For more information, see [Use the Availability Group Wizard &#40;SQL Server Management Studio&#41;](use-the-availability-group-wizard-sql-server-management-studio.md), [Use the New Availability Group Dialog Box &#40;SQL Server Management Studio&#41;](use-the-new-availability-group-dialog-box-sql-server-management-studio.md), or [Create an Availability Group &#40;SQL Server PowerShell&#41;](../../../powershell/sql-server-powershell.md).</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="980ed-108">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="980ed-108">Before You Begin</span></span>  
 <span data-ttu-id="980ed-109">가용성 그룹을 처음 만들어 보는 경우 이 섹션을 먼저 읽는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="980ed-109">We strongly recommend that you read this section before attempting to create your first availability group.</span></span>  
  
###  <a name="prerequisites-restrictions-and-recommendations"></a><a name="PrerequisitesRestrictions"></a><span data-ttu-id="980ed-110">사전 요구 사항, 제한 사항 및 권장 사항</span><span class="sxs-lookup"><span data-stu-id="980ed-110">Prerequisites, Restrictions, and Recommendations</span></span>  
  
-   <span data-ttu-id="980ed-111">가용성 그룹을 만들기 전에 가용성 복제본을 호스팅하는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인스턴스가 동일한 WSFC 장애 조치(Failover) 클러스터 내의 다른 WSFC(Windows Server 장애 조치(Failover) 클러스터링) 노드에 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="980ed-111">Before creating an availability group, verify that the instances of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] that host availability replicas reside on different Windows Server Failover Clustering (WSFC) node within the same WSFC failover cluster.</span></span> <span data-ttu-id="980ed-112">또한 각 서버 인스턴스가 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 의 기타 모든 필수 구성 요소를 충족하는지도 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="980ed-112">Also, verify that each of the server instance meets all other [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] prerequisites.</span></span> <span data-ttu-id="980ed-113">자세한 내용은 [AlwaysOn 가용성 그룹에 대한 필수 조건, 제한 사항 및 권장 사항&#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="980ed-113">For more information, we strongly recommend that you read [Prerequisites, Restrictions, and Recommendations for AlwaysOn Availability Groups &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="980ed-114">보안</span><span class="sxs-lookup"><span data-stu-id="980ed-114">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="980ed-115">권한</span><span class="sxs-lookup"><span data-stu-id="980ed-115">Permissions</span></span>  
 <span data-ttu-id="980ed-116">CREATE AVAILABILITY GROUP 서버 권한, ALTER ANY AVAILABILITY GROUP 권한, CONTROL SERVER 권한 중 하나와 **sysadmin** 고정 서버 역할의 멤버 자격이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="980ed-116">Requires membership in the **sysadmin** fixed server role and either CREATE AVAILABILITY GROUP server permission, ALTER ANY AVAILABILITY GROUP permission, or CONTROL SERVER permission.</span></span>  
  
###  <a name="summary-of-tasks-and-corresponding-transact-sql-statements"></a><a name="SummaryTsqlStatements"></a> <span data-ttu-id="980ed-117">태스크 및 해당 Transact-SQL 문 요약</span><span class="sxs-lookup"><span data-stu-id="980ed-117">Summary of Tasks and Corresponding Transact-SQL Statements</span></span>  
 <span data-ttu-id="980ed-118">다음 표에서는 가용성 그룹을 만들고 구성하는 데 필요한 기본 태스크와 이러한 태스크에 사용할 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 문을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="980ed-118">The following table lists the basic tasks involved in creating and configuring an availability group and indicates which [!INCLUDE[tsql](../../../includes/tsql-md.md)] statements to use for these tasks.</span></span> <span data-ttu-id="980ed-119">[!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 태스크는 표에 나오는 순서대로 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="980ed-119">The [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] tasks must be performed in the sequence in which they are presented in the table.</span></span>  
  
|<span data-ttu-id="980ed-120">Task</span><span class="sxs-lookup"><span data-stu-id="980ed-120">Task</span></span>|<span data-ttu-id="980ed-121">Transact-SQL 문</span><span class="sxs-lookup"><span data-stu-id="980ed-121">Transact-SQL Statement(s)</span></span>|<span data-ttu-id="980ed-122">태스크를 수행할 위치**<sup>\*</sup>**</span><span class="sxs-lookup"><span data-stu-id="980ed-122">Where to Perform Task**<sup>\*</sup>**</span></span>|  
|----------|----------------------------------|-------------------------------------------|  
|<span data-ttu-id="980ed-123">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인스턴스당 하나의 데이터베이스 미러링 엔드포인트 만들기</span><span class="sxs-lookup"><span data-stu-id="980ed-123">Create database mirroring endpoint (once per [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instance)</span></span>|<span data-ttu-id="980ed-124">[끝점 만들기](/sql/t-sql/statements/create-endpoint-transact-sql) *endpointName* ... DATABASE_MIRRORING</span><span class="sxs-lookup"><span data-stu-id="980ed-124">[CREATE ENDPOINT](/sql/t-sql/statements/create-endpoint-transact-sql) *endpointName* ... FOR DATABASE_MIRRORING</span></span>|<span data-ttu-id="980ed-125">데이터베이스 미러링 엔드포인트가 없는 각 서버 인스턴스에서 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="980ed-125">Execute on each server instance that lacks database mirroring endpoint.</span></span>|  
|<span data-ttu-id="980ed-126">가용성 그룹 만들기</span><span class="sxs-lookup"><span data-stu-id="980ed-126">Create availability group</span></span>|[<span data-ttu-id="980ed-127">CREATE AVAILABILITY GROUP</span><span class="sxs-lookup"><span data-stu-id="980ed-127">CREATE AVAILABILITY GROUP</span></span>](/sql/t-sql/statements/create-availability-group-transact-sql)|<span data-ttu-id="980ed-128">초기 주 복제본을 호스트할 서버 인스턴스에서 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="980ed-128">Execute on the server instance that is to host the initial primary replica.</span></span>|  
|<span data-ttu-id="980ed-129">가용성 그룹에 보조 복제본 조인</span><span class="sxs-lookup"><span data-stu-id="980ed-129">Join secondary replica to availability group</span></span>|<span data-ttu-id="980ed-130">[ALTER AVAILABILITY GROUP](join-a-secondary-replica-to-an-availability-group-sql-server.md) *group_name* JOIN</span><span class="sxs-lookup"><span data-stu-id="980ed-130">[ALTER AVAILABILITY GROUP](join-a-secondary-replica-to-an-availability-group-sql-server.md) *group_name* JOIN</span></span>|<span data-ttu-id="980ed-131">보조 복제본을 호스트하는 각 서버 인스턴스에서 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="980ed-131">Execute on each server instance that hosts a secondary replica.</span></span>|  
|<span data-ttu-id="980ed-132">보조 데이터베이스 준비</span><span class="sxs-lookup"><span data-stu-id="980ed-132">Prepare the secondary database</span></span>|<span data-ttu-id="980ed-133">[백업](/sql/t-sql/statements/backup-transact-sql) 및 [복원](/sql/t-sql/statements/restore-statements-transact-sql).</span><span class="sxs-lookup"><span data-stu-id="980ed-133">[BACKUP](/sql/t-sql/statements/backup-transact-sql) and [RESTORE](/sql/t-sql/statements/restore-statements-transact-sql).</span></span>|<span data-ttu-id="980ed-134">주 복제본을 호스트하는 서버 인스턴스에 백업을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="980ed-134">Create backups on the server instance that hosts the primary replica.</span></span><br /><br /> <span data-ttu-id="980ed-135">RESTORE WITH NORECOVERY를 사용하여 보조 복제본을 호스팅하는 각 서버 인스턴스에 백업을 복원합니다.</span><span class="sxs-lookup"><span data-stu-id="980ed-135">Restore backups on each server instance that hosts a secondary replica, using RESTORE WITH NORECOVERY.</span></span>|  
|<span data-ttu-id="980ed-136">가용성 그룹에 각 보조 데이터베이스를 조인하여 데이터 동기화 시작</span><span class="sxs-lookup"><span data-stu-id="980ed-136">Start data synchronization by joining each secondary database to availability group</span></span>|<span data-ttu-id="980ed-137">[ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql-set-hadr) *database_name* SET HADR AVAILABILITY GROUP = *group_name*</span><span class="sxs-lookup"><span data-stu-id="980ed-137">[ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql-set-hadr) *database_name* SET HADR AVAILABILITY GROUP = *group_name*</span></span>|<span data-ttu-id="980ed-138">보조 복제본을 호스트하는 각 서버 인스턴스에서 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="980ed-138">Execute on each server instance that hosts a secondary replica.</span></span>|  
  
 <span data-ttu-id="980ed-139">**<sup>\*</sup>** 지정 된 태스크를 수행 하려면 표시 된 서버 인스턴스에 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="980ed-139">**<sup>\*</sup>**  To perform a given task, connect to the indicated server instance or instances.</span></span>  
  
##  <a name="using-transact-sql-to-create-and-configure-an-availability-group"></a><a name="TsqlProcedure"></a> <span data-ttu-id="980ed-140">Transact-SQL을 사용하여 가용성 그룹 만들기 및 구성</span><span class="sxs-lookup"><span data-stu-id="980ed-140">Using Transact-SQL to Create and Configure an Availability Group</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="980ed-141"> 이러한 각 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 문의 코드 예가 포함된 샘플 구성 프로시저는 [예: Windows 인증을 사용하는 가용성 그룹 구성](#ExampleConfigAGWinAuth)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="980ed-141">For a sample configuration procedure containing code examples of each these [!INCLUDE[tsql](../../../includes/tsql-md.md)] statements, see [Example: Configuring an Availability Group that Uses Windows Authentication](#ExampleConfigAGWinAuth).</span></span>  
  
1.  <span data-ttu-id="980ed-142">주 복제본을 호스팅할 서버 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="980ed-142">Connect to the server instance that is to host the primary replica.</span></span>  
  
2.  <span data-ttu-id="980ed-143">[CREATE AVAILABILITY group](/sql/t-sql/statements/create-availability-group-transact-sql) 문을 사용 하 여 가용성 그룹을 만듭니다 [!INCLUDE[tsql](../../../includes/tsql-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="980ed-143">Create the availability group by using the [CREATE AVAILABILITY GROUP](/sql/t-sql/statements/create-availability-group-transact-sql)[!INCLUDE[tsql](../../../includes/tsql-md.md)] statement.</span></span>  
  
3.  <span data-ttu-id="980ed-144">새 보조 복제본을 가용성 그룹에 조인합니다.</span><span class="sxs-lookup"><span data-stu-id="980ed-144">Join the new secondary replica to the availability group.</span></span> <span data-ttu-id="980ed-145">자세한 내용은 [가용성 그룹에 보조 복제본 조인&#40;SQL Server&#41;](join-a-secondary-replica-to-an-availability-group-sql-server.md)또는 PowerShell을 사용하여 Always On 가용성 그룹에 보조 데이터베이스를 조인하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="980ed-145">For more information, see [Join a Secondary Replica to an Availability Group &#40;SQL Server&#41;](join-a-secondary-replica-to-an-availability-group-sql-server.md).</span></span>  
  
4.  <span data-ttu-id="980ed-146">가용성 그룹의 각 데이터베이스에 대해 RESTORE WITH NORECOVERY를 사용하여 주 데이터베이스의 최신 백업을 복원하는 방법으로 보조 데이터베이스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="980ed-146">For each database in the availability group, create a secondary database by restoring recent backups of the primary database, using RESTORE WITH NORECOVERY.</span></span> <span data-ttu-id="980ed-147">자세한 내용은 [예: Windows 인증을 사용하여 가용성 그룹 설정(Transact-SQL)](create-an-availability-group-transact-sql.md)에서 데이터베이스 백업을 복원하는 단계부터 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="980ed-147">For more information, see [Example: Setting Up an Availability Group Using Windows Authentication (Transact-SQL)](create-an-availability-group-transact-sql.md), starting with the step that restores the database backup.</span></span>  
  
5.  <span data-ttu-id="980ed-148">모든 새 보조 데이터베이스를 가용성 그룹에 조인합니다.</span><span class="sxs-lookup"><span data-stu-id="980ed-148">Join every new secondary database to the availability group.</span></span> <span data-ttu-id="980ed-149">자세한 내용은 [가용성 그룹에 보조 복제본 조인&#40;SQL Server&#41;](join-a-secondary-replica-to-an-availability-group-sql-server.md)또는 PowerShell을 사용하여 Always On 가용성 그룹에 보조 데이터베이스를 조인하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="980ed-149">For more information, see [Join a Secondary Replica to an Availability Group &#40;SQL Server&#41;](join-a-secondary-replica-to-an-availability-group-sql-server.md).</span></span>  
  
##  <a name="example-configuring-an-availability-group-that-uses-windows-authentication"></a><a name="ExampleConfigAGWinAuth"></a> <span data-ttu-id="980ed-150">예: Windows 인증을 사용하는 가용성 그룹 구성</span><span class="sxs-lookup"><span data-stu-id="980ed-150">Example: Configuring an Availability Group that Uses Windows Authentication</span></span>  
 <span data-ttu-id="980ed-151">이 예에서 만드는 예제 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 구성 프로시저는 [!INCLUDE[tsql](../../../includes/tsql-md.md)]을 사용하여 Windows 인증을 사용하는 데이터베이스 미러링 엔드포인트를 설정하고, 가용성 그룹과 해당 보조 데이터베이스를 만들고 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="980ed-151">This example creates a sample [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] configuration procedure that uses [!INCLUDE[tsql](../../../includes/tsql-md.md)] to set up database mirroring endpoints that use Windows Authentication and to create and configure an availability group and its secondary databases.</span></span>  
  
 <span data-ttu-id="980ed-152">이 예에는 다음과 같은 섹션이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="980ed-152">This example contains the following sections:</span></span>  
  
-   [<span data-ttu-id="980ed-153">샘플 구성 프로시저를 사용 하기 위한 필수 구성 요소</span><span class="sxs-lookup"><span data-stu-id="980ed-153">Prerequisites for Using the Sample Configuration Procedure</span></span>](#PrerequisitesForExample)  
  
-   [<span data-ttu-id="980ed-154">예제 구성 프로시저</span><span class="sxs-lookup"><span data-stu-id="980ed-154">Sample Configuration Procedure</span></span>](#SampleProcedure)  
  
-   [<span data-ttu-id="980ed-155">예제 구성 프로시저에 대한 전체 코드 예</span><span class="sxs-lookup"><span data-stu-id="980ed-155">Complete Code Example for Sample Configuration Procedure</span></span>](#CompleteCodeExample)  
  
###  <a name="prerequisites-for-using-the-sample-configuration-procedure"></a><a name="PrerequisitesForExample"></a> <span data-ttu-id="980ed-156">예제 구성 프로시저를 사용하기 위한 사전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="980ed-156">Prerequisites for Using the Sample Configuration Procedure</span></span>  
 <span data-ttu-id="980ed-157">이 예제 프로시저에 대한 요구 사항은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="980ed-157">This sample procedure has the following requirements:</span></span>  
  
-   <span data-ttu-id="980ed-158">서버 인스턴스에서는 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]을 지원해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="980ed-158">The server instances must support [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)].</span></span> <span data-ttu-id="980ed-159">자세한 내용은 [AlwaysOn 가용성 그룹에 대한 필수 조건, 제한 사항 및 권장 사항&#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="980ed-159">For more information, see [Prerequisites, Restrictions, and Recommendations for AlwaysOn Availability Groups &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md).</span></span>  
  
-   <span data-ttu-id="980ed-160">두 예제 데이터베이스 *MyDb1* 및 *MyDb2*는 주 복제본을 호스팅할 서버 인스턴스에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="980ed-160">Two sample databases, *MyDb1* and *MyDb2*, must exist on the server instance that will host the primary replica.</span></span> <span data-ttu-id="980ed-161">다음 코드 예에서는 이러한 두 데이터베이스를 만들고 구성하며 각 데이터베이스의 전체 백업을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="980ed-161">The following code examples create and configure these two databases and create a full backup of each.</span></span> <span data-ttu-id="980ed-162">예제 가용성 그룹을 만들려는 서버 인스턴스에서 이러한 코드 예를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="980ed-162">Execute these code examples on the server instance on which you intend to create the sample availability group.</span></span> <span data-ttu-id="980ed-163">이 서버 인스턴스는 예제 가용성 그룹의 초기 주 복제본을 호스팅합니다.</span><span class="sxs-lookup"><span data-stu-id="980ed-163">This server instance will host the initial primary replica of the sample availability group.</span></span>  
  
    1.  <span data-ttu-id="980ed-164">다음 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 예에서는 이러한 데이터베이스를 만든 다음 전체 복구 모델을 사용하도록 데이터베이스를 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="980ed-164">The following [!INCLUDE[tsql](../../../includes/tsql-md.md)] example creates these databases and alters them to use the full recovery model:</span></span>  
  
        ```sql
        -- Create sample databases:  
        CREATE DATABASE MyDb1;  
        GO  
        ALTER DATABASE MyDb1 SET RECOVERY FULL;  
        GO  
  
        CREATE DATABASE MyDb2;  
        GO  
        ALTER DATABASE MyDb2 SET RECOVERY FULL;  
        GO  
        ```  
  
    2.  <span data-ttu-id="980ed-165">다음 코드 예제에서는 *MyDb1* 및 *MyDb2*의 전체 데이터베이스 백업을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="980ed-165">The following code example creates a full database backup of *MyDb1* and *MyDb2*.</span></span> <span data-ttu-id="980ed-166">이 코드 예제에서는 가상의 백업 공유 \\ \\ *FILESERVER* \\ *sqlbackups*을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="980ed-166">This code example uses a fictional backup share, \\\\*FILESERVER*\\*SQLbackups*.</span></span>  
  
        ```sql
        -- Backup sample databases:  
        BACKUP DATABASE MyDb1   
        TO DISK = N'\\FILESERVER\SQLbackups\MyDb1.bak'   
            WITH FORMAT  
        GO  
  
        BACKUP DATABASE MyDb2   
        TO DISK = N'\\FILESERVER\SQLbackups\MyDb2.bak'   
            WITH FORMAT  
        GO
        ```  
  
###  <a name="sample-configuration-procedure"></a><a name="SampleProcedure"></a> <span data-ttu-id="980ed-167">예제 구성 프로시저</span><span class="sxs-lookup"><span data-stu-id="980ed-167">Sample Configuration Procedure</span></span>  
 <span data-ttu-id="980ed-168">이 예제 구성에서는 서비스 계정이 다르지만 트러스트된 도메인 계정(`DOMAIN1` 및 `DOMAIN2`)으로 실행되는 두 개의 독립 실행형 서버 인스턴스에 가용성 복제본이 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="980ed-168">In this sample configuration, the availability replica will be created on two stand-alone server instances whose service accounts run under different, but trusted, domains (`DOMAIN1` and `DOMAIN2`).</span></span>  
  
 <span data-ttu-id="980ed-169">다음 표에는 이 예제 구성에 사용된 값이 요약되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="980ed-169">The following table summarizes the values used in this sample configuration.</span></span>  
  
|<span data-ttu-id="980ed-170">초기 역할</span><span class="sxs-lookup"><span data-stu-id="980ed-170">Initial role</span></span>|<span data-ttu-id="980ed-171">시스템</span><span class="sxs-lookup"><span data-stu-id="980ed-171">System</span></span>|<span data-ttu-id="980ed-172">호스트 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인스턴스</span><span class="sxs-lookup"><span data-stu-id="980ed-172">Host [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Instance</span></span>|  
|------------------|------------|---------------------------------------------|  
|<span data-ttu-id="980ed-173">주</span><span class="sxs-lookup"><span data-stu-id="980ed-173">Primary</span></span>|`COMPUTER01`|`AgHostInstance`|  
|<span data-ttu-id="980ed-174">보조</span><span class="sxs-lookup"><span data-stu-id="980ed-174">Secondary</span></span>|`COMPUTER02`|<span data-ttu-id="980ed-175">기본 인스턴스입니다.</span><span class="sxs-lookup"><span data-stu-id="980ed-175">Default instance.</span></span>|  
  
1.  <span data-ttu-id="980ed-176">가용성 그룹을 만들 서버 인스턴스( *에 있는* 라는 인스턴스)에 `AgHostInstance` dbm_endpoint `COMPUTER01`라는 데이터베이스 미러링 엔드포인트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="980ed-176">Create a database mirroring endpoint named *dbm_endpoint* on the server instance on which you plan to create the availability group (this is an instance named `AgHostInstance` on `COMPUTER01`).</span></span> <span data-ttu-id="980ed-177">이 엔드포인트는 포트 7022를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="980ed-177">This endpoint uses port 7022.</span></span> <span data-ttu-id="980ed-178">가용성 그룹을 만드는 서버 인스턴스는 주 복제본을 호스팅합니다.</span><span class="sxs-lookup"><span data-stu-id="980ed-178">Note that the server instance on which you create the availability group will host the primary replica.</span></span>  
  
    ```sql
    -- Create endpoint on server instance that hosts the primary replica:  
    CREATE ENDPOINT dbm_endpoint  
        STATE=STARTED   
        AS TCP (LISTENER_PORT=7022)   
        FOR DATABASE_MIRRORING (ROLE=ALL)  
    GO
    ```  
  
2.  <span data-ttu-id="980ed-179">보조 복제본을 호스트할 서버 인스턴스( *에 있는 기본 서버 인스턴스)에* dbm_endpoint `COMPUTER02`라는 엔드포인트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="980ed-179">Create an endpoint *dbm_endpoint* on the server instance that will host the secondary replica (this is the default server instance on `COMPUTER02`).</span></span> <span data-ttu-id="980ed-180">이 엔드포인트는 포트 5022를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="980ed-180">This endpoint uses port 5022.</span></span>  
  
    ```sql
    -- Create endpoint on server instance that hosts the secondary replica:   
    CREATE ENDPOINT dbm_endpoint  
        STATE=STARTED   
        AS TCP (LISTENER_PORT=5022)   
        FOR DATABASE_MIRRORING (ROLE=ALL)  
    GO
    ```  
  
3.  > [!NOTE]  
    >  <span data-ttu-id="980ed-181">가용성 복제본을 호스팅할 서버 인스턴스의 서비스 계정이 동일한 도메인 계정으로 실행되는 경우에는 이 단계가 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="980ed-181">If the service accounts of the server instances that are to host your availability replicas run under the same domain account this step is unnecessary.</span></span> <span data-ttu-id="980ed-182">이 단계를 생략하고 다음 단계로 직접 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="980ed-182">Skip it and go directly to the next step.</span></span>  
  
     <span data-ttu-id="980ed-183">서버 인스턴스의 서비스 계정이 다른 도메인 사용자로 실행되는 경우에는 각 서버 인스턴스에서 다른 서버 인스턴스에 대한 로그인을 만들고 로컬 데이터베이스 미러링 엔드포인트에 액세스할 수 있는 권한을 이 로그인에 부여합니다.</span><span class="sxs-lookup"><span data-stu-id="980ed-183">If the service accounts of the server instances run under different domain users, on each server instance, create a login for the other server instance and grant this login permission to access the local database mirroring endpoint.</span></span>  
  
     <span data-ttu-id="980ed-184">다음 코드 예에서는 로그인을 만들고 이 로그인에 엔드포인트에 대한 사용 권한을 부여하기 위한 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 문을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="980ed-184">The following code example shows the [!INCLUDE[tsql](../../../includes/tsql-md.md)] statements for creating a login and granting it permission on an endpoint.</span></span> <span data-ttu-id="980ed-185">여기에서 원격 서버 인스턴스의 도메인 계정은 *domain_name*\\*user_name*으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="980ed-185">The domain account of the remote server instance is represented here as *domain_name*\\*user_name*.</span></span>  
  
    ```sql
    -- If necessary, create a login for the service account, domain_name\user_name  
    -- of the server instance that will host the other replica:  
    USE master;  
    GO  
    CREATE LOGIN [domain_name\user_name] FROM WINDOWS;  
    GO  
    -- And Grant this login connect permissions on the endpoint:  
    GRANT CONNECT ON ENDPOINT::dbm_endpoint   
       TO [domain_name\user_name];  
    GO  
    ```  
  
4.  <span data-ttu-id="980ed-186">사용자 데이터베이스가 있는 서버 인스턴스에서 가용성 그룹을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="980ed-186">On the server instance where the user databases reside, create the availability group.</span></span>  
  
     <span data-ttu-id="980ed-187">다음 코드 예제에서는 *MyDb1* 및 *MyDb2* 라는 샘플 데이터베이스가 만들어진 서버 인스턴스에 *MyAG*라는 가용성 그룹을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="980ed-187">The following code example creates an availability group named *MyAG* on the server instance on which the sample databases, *MyDb1* and *MyDb2*, were created.</span></span> <span data-ttu-id="980ed-188">`AgHostInstance`COMPUTER01 *에 있는 로컬 서버 인스턴스* 가 먼저 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="980ed-188">The local server instance, `AgHostInstance`, on *COMPUTER01* is specified first.</span></span> <span data-ttu-id="980ed-189">이 인스턴스는 초기 주 복제본을 호스팅합니다.</span><span class="sxs-lookup"><span data-stu-id="980ed-189">This instance will host the initial primary replica.</span></span> <span data-ttu-id="980ed-190">*COMPUTER02*에 기본 서버 인스턴스인 원격 서버 인스턴스가 보조 복제본을 호스트하도록 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="980ed-190">A remote server instance, the default server instance on *COMPUTER02*, is specified to host a secondary replica.</span></span> <span data-ttu-id="980ed-191">두 가용성 복제본 모두 수동 장애 조치와 함께 비동기 커밋 모드를 사용하도록 구성됩니다. 비동기 커밋 복제본에 대한 수동 장애 조치는 데이터 손실이 가능한 강제 장애 조치를 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="980ed-191">Both availability replica are configured to use asynchronous-commit mode with manual failover (for asynchronous-commit replicas manual failover means  forced failover with possible data loss).</span></span>  
  
    ```sql
    -- Create the availability group, MyAG:   
    CREATE AVAILABILITY GROUP MyAG   
       FOR   
          DATABASE MyDB1, MyDB2   
       REPLICA ON   
          'COMPUTER01\AgHostInstance' WITH   
             (  
             ENDPOINT_URL = 'TCP://COMPUTER01.Adventure-Works.com:7022',   
             AVAILABILITY_MODE = ASYNCHRONOUS_COMMIT,  
             FAILOVER_MODE = MANUAL  
             ),  
          'COMPUTER02' WITH   
             (  
             ENDPOINT_URL = 'TCP://COMPUTER02.Adventure-Works.com:5022',  
             AVAILABILITY_MODE = ASYNCHRONOUS_COMMIT,  
             FAILOVER_MODE = MANUAL  
             );   
    GO  
    ```  
  
     <span data-ttu-id="980ed-192">가용성 그룹을 만드는 다른 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 코드 샘플을 보려면 [CREATE AVAILABILITY GROUP&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-availability-group-transact-sql)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="980ed-192">For additional [!INCLUDE[tsql](../../../includes/tsql-md.md)] code examples of creating an availability group, see [CREATE AVAILABILITY GROUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-availability-group-transact-sql).</span></span>  
  
5.  <span data-ttu-id="980ed-193">보조 복제본을 호스팅하는 서버 인스턴스에서 보조 복제본을 가용성 그룹에 조인합니다.</span><span class="sxs-lookup"><span data-stu-id="980ed-193">On the server instance that hosts the secondary replica, join the secondary replica to the availability group.</span></span>  
  
     <span data-ttu-id="980ed-194">다음 코드 예에서는 `COMPUTER02` 의 보조 복제본을 `MyAG` 가용성 그룹에 조인합니다.</span><span class="sxs-lookup"><span data-stu-id="980ed-194">The following code example joins the secondary replica on `COMPUTER02` to the `MyAG` availability group.</span></span>  
  
    ```sql
    -- On the server instance that hosts the secondary replica,   
    -- join the secondary replica to the availability group:  
    ALTER AVAILABILITY GROUP MyAG JOIN;  
    GO  
    ```  
  
6.  <span data-ttu-id="980ed-195">보조 복제본을 호스팅하는 서버 인스턴스에서 보조 데이터베이스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="980ed-195">On the server instance that hosts the secondary replica, create the secondary databases.</span></span>  
  
     <span data-ttu-id="980ed-196">다음 코드 예제에서는 RESTORE WITH NORECOVERY를 사용하여 데이터베이스 백업을 복원하는 방법으로 *MyDb1* 및 *MyDb2* 보조 데이터베이스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="980ed-196">The following code example creates the *MyDb1* and *MyDb2* secondary databases by restoring database backups using RESTORE WITH NORECOVERY.</span></span>  
  
    ```sql
    -- On the server instance that hosts the secondary replica,   
    -- Restore database backups using the WITH NORECOVERY option:  
    RESTORE DATABASE MyDb1   
        FROM DISK = N'\\FILESERVER\SQLbackups\MyDb1.bak'   
        WITH NORECOVERY  
    GO  
  
    RESTORE DATABASE MyDb2   
        FROM DISK = N'\\FILESERVER\SQLbackups\MyDb2.bak'   
        WITH NORECOVERY  
    GO
    ```  
  
7.  <span data-ttu-id="980ed-197">주 복제본을 호스팅하는 서버 인스턴스에서 각 주 데이터베이스의 트랜잭션 로그를 백업합니다.</span><span class="sxs-lookup"><span data-stu-id="980ed-197">On the server instance that hosts the primary replica, back up the transaction log on each of the primary databases.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="980ed-198">실제 가용성 그룹을 구성할 때는 해당 보조 데이터베이스를 가용성 그룹에 조인한 후에 주 데이터베이스에 대한 로그 백업 태스크를 수행하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="980ed-198">When you are configuring a real availability group, we recommend that, before taking this log backup, you suspend log backup tasks for your primary databases until you have joined the corresponding secondary databases to the availability group.</span></span>  
  
     <span data-ttu-id="980ed-199">다음 코드 예에서는 MyDb1 및 MyDb2에 트랜잭션 로그 백업을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="980ed-199">The following code example creates a transaction log backup on MyDb1 and on MyDb2.</span></span>  
  
    ```sql
    -- On the server instance that hosts the primary replica,   
    -- Backup the transaction log on each primary database:  
    BACKUP LOG MyDb1   
    TO DISK = N'\\FILESERVER\SQLbackups\MyDb1.bak'   
        WITH NOFORMAT  
    GO  
  
    BACKUP LOG MyDb2   
    TO DISK = N'\\FILESERVER\SQLbackups\MyDb2.bak'   
        WITHNOFORMAT  
    GO
    ```  
  
    > [!TIP]  
    >  <span data-ttu-id="980ed-200">일반적으로 로그 백업은 각 주 데이터베이스에서 만든 다음 WITH NORECOVERY를 사용하여 해당하는 보조 데이터베이스에 복원해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="980ed-200">Typically, a log backup must be taken on each primary database and then restored on the corresponding secondary database (using WITH NORECOVERY).</span></span> <span data-ttu-id="980ed-201">그러나 데이터베이스를 방금 만들었으며 아직 로그 백업을 만들지 않았거나 복구 모델이 방금 SIMPLE에서 FULL로 변경된 경우에는 이 로그 백업이 필요하지 않을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="980ed-201">However, this log backup might be unnecessary if the database has just been created and no log backup has been taken yet or the recovery model has just been changed from SIMPLE to FULL.</span></span>  
  
8.  <span data-ttu-id="980ed-202">보조 복제본을 호스팅하는 서버 인스턴스에서 보조 데이터베이스에 로그 백업을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="980ed-202">On the server instance that hosts the secondary replica, apply log backups to the secondary databases.</span></span>  
  
     <span data-ttu-id="980ed-203">다음 코드 예제에서는 RESTORE WITH NORECOVERY를 사용하여 데이터베이스 백업을 복원하는 방법으로 *MyDb1* 및 *MyDb2* 보조 데이터베이스에 백업을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="980ed-203">The following code example applies backups to *MyDb1* and *MyDb2* secondary databases by restoring database backups using RESTORE WITH NORECOVERY.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="980ed-204">실제 보조 데이터베이스를 준비할 때는 처음부터 항상 RESTORE WITH NORECOVERY를 사용하여 보조 데이터베이스를 만들 때 사용한 데이터베이스 백업보다 나중에 만들어진 모든 로그 백업을 적용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="980ed-204">When you are preparing a real secondary database, you need to apply every log backup taken since the database backup from which you created the secondary database, starting with the earliest and always using RESTORE WITH NORECOVERY.</span></span> <span data-ttu-id="980ed-205">물론, 전체 데이터베이스 백업과 차등 데이터베이스 백업을 모두 복원하는 경우에는 차등 백업 이후에 만들어진 로그 백업만 적용하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="980ed-205">Of course, if you restore both full and differential database backups, you would only need to apply the log backups taken after the differential backup.</span></span>  
  
    ```sql
    -- Restore the transaction log on each secondary database,  
    -- using the WITH NORECOVERY option:  
    RESTORE LOG MyDb1   
        FROM DISK = N'\\FILESERVER\SQLbackups\MyDb1.bak'   
        WITH FILE=1, NORECOVERY  
    GO  
    RESTORE LOG MyDb2   
        FROM DISK = N'\\FILESERVER\SQLbackups\MyDb2.bak'   
        WITH FILE=1, NORECOVERY  
    GO  
    ```  
  
9. <span data-ttu-id="980ed-206">보조 복제본을 호스팅하는 서버 인스턴스에서 새 보조 데이터베이스를 가용성 그룹에 조인합니다.</span><span class="sxs-lookup"><span data-stu-id="980ed-206">On the server instance that hosts the secondary replica, join the new secondary databases to the availability group.</span></span>  
  
     <span data-ttu-id="980ed-207">다음 코드 예제에서는 *MyDb1* 보조 데이터베이스를 조인한 다음 *MyDb2* 보조 데이터베이스를 *MyAG* 가용성 그룹에 조인합니다.</span><span class="sxs-lookup"><span data-stu-id="980ed-207">The following code example, joins the *MyDb1* secondary database and then the *MyDb2* secondary databases to the *MyAG* availability group.</span></span>  
  
    ```sql
    -- On the server instance that hosts the secondary replica,   
    -- join each secondary database to the availability group:  
    ALTER DATABASE MyDb1 SET HADR AVAILABILITY GROUP = MyAG;  
    GO  
  
    ALTER DATABASE MyDb2 SET HADR AVAILABILITY GROUP = MyAG;  
    GO
    ```  
  
###  <a name="complete-code-example-for-sample-configuration-procedure"></a><a name="CompleteCodeExample"></a> <span data-ttu-id="980ed-208">예제 구성 프로시저에 대한 전체 코드 예</span><span class="sxs-lookup"><span data-stu-id="980ed-208">Complete Code Example for Sample Configuration Procedure</span></span>  
 <span data-ttu-id="980ed-209">다음 예에서는 예제 구성 프로시저의 모든 단계에 포함된 코드 예를 병합합니다.</span><span class="sxs-lookup"><span data-stu-id="980ed-209">The following example merges the code examples from all the steps of the sample configuration procedure.</span></span> <span data-ttu-id="980ed-210">다음 표에는 이 코드 예에 사용된 자리 표시자 값이 요약되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="980ed-210">The following table summarized the placeholder values used in this code example.</span></span> <span data-ttu-id="980ed-211">이 코드 예의 단계에 대한 자세한 내용은 이 항목 윗부분의 [예제 구성 프로시저를 사용하기 위한 사전 요구 사항](#PrerequisitesForExample) 및 [예제 구성 프로시저](#SampleProcedure)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="980ed-211">For more information about the steps in this code example, see [Prerequisites for Using the Sample Configuration Procedure](#PrerequisitesForExample) and [Sample Configuration Procedure](#SampleProcedure), earlier in this topic.</span></span>  
  
|<span data-ttu-id="980ed-212">자리 표시자</span><span class="sxs-lookup"><span data-stu-id="980ed-212">Placeholder</span></span>|<span data-ttu-id="980ed-213">Description</span><span class="sxs-lookup"><span data-stu-id="980ed-213">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="980ed-214">\\\\*FILESERVER*\\*SQLbackups*</span><span class="sxs-lookup"><span data-stu-id="980ed-214">\\\\*FILESERVER*\\*SQLbackups*</span></span>|<span data-ttu-id="980ed-215">가상의 백업 공유입니다.</span><span class="sxs-lookup"><span data-stu-id="980ed-215">Fictional backup share.</span></span>|  
|<span data-ttu-id="980ed-216">\\\\*FILESERVER*\\*SQLbackups\MyDb1.bak*</span><span class="sxs-lookup"><span data-stu-id="980ed-216">\\\\*FILESERVER*\\*SQLbackups\MyDb1.bak*</span></span>|<span data-ttu-id="980ed-217">MyDb1의 백업 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="980ed-217">Backup file for MyDb1.</span></span>|  
|<span data-ttu-id="980ed-218">\\\\*FILESERVER*\\*SQLbackups\MyDb2.bak*</span><span class="sxs-lookup"><span data-stu-id="980ed-218">\\\\*FILESERVER*\\*SQLbackups\MyDb2.bak*</span></span>|<span data-ttu-id="980ed-219">MyDb2의 백업 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="980ed-219">Backup file for MyDb2.</span></span>|  
|<span data-ttu-id="980ed-220">*7022*</span><span class="sxs-lookup"><span data-stu-id="980ed-220">*7022*</span></span>|<span data-ttu-id="980ed-221">각 데이터베이스 미러링 엔드포인트에 할당된 포트 번호입니다.</span><span class="sxs-lookup"><span data-stu-id="980ed-221">Port number assigned to each database mirroring endpoint.</span></span>|  
|<span data-ttu-id="980ed-222">*COMPUTER01\AgHostInstance*</span><span class="sxs-lookup"><span data-stu-id="980ed-222">*COMPUTER01\AgHostInstance*</span></span>|<span data-ttu-id="980ed-223">초기 주 복제본을 호스팅하는 서버 인스턴스입니다.</span><span class="sxs-lookup"><span data-stu-id="980ed-223">Server instance that hosts the initial primary replica.</span></span>|  
|<span data-ttu-id="980ed-224">*COMPUTER02*</span><span class="sxs-lookup"><span data-stu-id="980ed-224">*COMPUTER02*</span></span>|<span data-ttu-id="980ed-225">초기 보조 복제본을 호스팅하는 서버 인스턴스입니다.</span><span class="sxs-lookup"><span data-stu-id="980ed-225">Server instance that hosts the initial secondary replica.</span></span> <span data-ttu-id="980ed-226">이 인스턴스는 `COMPUTER02`의 기본 서버 인스턴스입니다.</span><span class="sxs-lookup"><span data-stu-id="980ed-226">This is the default server instance on `COMPUTER02`.</span></span>|  
|<span data-ttu-id="980ed-227">*에 있는*</span><span class="sxs-lookup"><span data-stu-id="980ed-227">*dbm_endpoint*</span></span>|<span data-ttu-id="980ed-228">각 데이터베이스 미러링 엔드포인트에 지정된 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="980ed-228">Name specified for each database mirroring endpoint.</span></span>|  
|<span data-ttu-id="980ed-229">*MyDb1*</span><span class="sxs-lookup"><span data-stu-id="980ed-229">*MyAG*</span></span>|<span data-ttu-id="980ed-230">예제 가용성 그룹의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="980ed-230">Name of sample availability group.</span></span>|  
|<span data-ttu-id="980ed-231">*MyDb1*</span><span class="sxs-lookup"><span data-stu-id="980ed-231">*MyDb1*</span></span>|<span data-ttu-id="980ed-232">첫 번째 예제 데이터베이스의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="980ed-232">Name of first sample database.</span></span>|  
|<span data-ttu-id="980ed-233">*MyDb2*</span><span class="sxs-lookup"><span data-stu-id="980ed-233">*MyDb2*</span></span>|<span data-ttu-id="980ed-234">두 번째 예제 데이터베이스의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="980ed-234">Name of second sample database.</span></span>|  
|<span data-ttu-id="980ed-235">*DOMAIN1\user1*</span><span class="sxs-lookup"><span data-stu-id="980ed-235">*DOMAIN1\user1*</span></span>|<span data-ttu-id="980ed-236">초기 주 복제본을 호스팅할 서버 인스턴스의 서비스 계정입니다.</span><span class="sxs-lookup"><span data-stu-id="980ed-236">Service account of the server instance that is to host the initial primary replica.</span></span>|  
|<span data-ttu-id="980ed-237">*DOMAIN2\user2*</span><span class="sxs-lookup"><span data-stu-id="980ed-237">*DOMAIN2\user2*</span></span>|<span data-ttu-id="980ed-238">초기 보조 복제본을 호스팅할 서버 인스턴스의 서비스 계정입니다.</span><span class="sxs-lookup"><span data-stu-id="980ed-238">Service account of the server instance that is to host the initial secondary replica.</span></span>|  
|<span data-ttu-id="980ed-239">TCP://*COMPUTER01.Adventure-Works.com*:*7022*</span><span class="sxs-lookup"><span data-stu-id="980ed-239">TCP://*COMPUTER01.Adventure-Works.com*:*7022*</span></span>|<span data-ttu-id="980ed-240">COMPUTER01에 있는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]의 AgHostInstance 인스턴스의 엔드포인트 URL입니다.</span><span class="sxs-lookup"><span data-stu-id="980ed-240">Endpoint URL of the AgHostInstance instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] on COMPUTER01.</span></span>|  
|<span data-ttu-id="980ed-241">TCP://*COMPUTER02.Adventure-Works.com*:*5022*</span><span class="sxs-lookup"><span data-stu-id="980ed-241">TCP://*COMPUTER02.Adventure-Works.com*:*5022*</span></span>|<span data-ttu-id="980ed-242">COMPUTER02에 있는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]의 기본 인스턴스의 엔드포인트 URL입니다.</span><span class="sxs-lookup"><span data-stu-id="980ed-242">Endpoint URL of the default instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] on COMPUTER02.</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="980ed-243">가용성 그룹을 만드는 다른 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 코드 샘플을 보려면 [CREATE AVAILABILITY GROUP&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-availability-group-transact-sql)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="980ed-243">For additional [!INCLUDE[tsql](../../../includes/tsql-md.md)] code examples of creating an availability group, see [CREATE AVAILABILITY GROUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-availability-group-transact-sql).</span></span>  
  
```sql
-- on the server instance that will host the primary replica,   
-- create sample databases:  
CREATE DATABASE MyDb1;  
GO  
ALTER DATABASE MyDb1 SET RECOVERY FULL;  
GO  
  
CREATE DATABASE MyDb2;  
GO  
ALTER DATABASE MyDb2 SET RECOVERY FULL;  
GO  
  
-- Backup sample databases:  
BACKUP DATABASE MyDb1   
TO DISK = N'\\FILESERVER\SQLbackups\MyDb1.bak'   
    WITH FORMAT  
GO  
  
BACKUP DATABASE MyDb2   
TO DISK = N'\\FILESERVER\SQLbackups\MyDb2.bak'   
    WITH FORMAT  
GO  
  
-- Create the endpoint on the server instance that will host the primary replica:  
CREATE ENDPOINT dbm_endpoint  
    STATE=STARTED   
    AS TCP (LISTENER_PORT=7022)   
    FOR DATABASE_MIRRORING (ROLE=ALL)  
GO  
  
-- Create the endpoint on the server instance that will host the secondary replica:   
CREATE ENDPOINT dbm_endpoint  
    STATE=STARTED   
    AS TCP (LISTENER_PORT=7022)   
    FOR DATABASE_MIRRORING (ROLE=ALL)  
GO  
  
-- If both service accounts run under the same domain account, skip this step. Otherwise,   
-- On the server instance that will host the primary replica,   
-- create a login for the service account   
-- of the server instance that will host the secondary replica, DOMAIN2\user2,   
-- and grant this login connect permissions on the endpoint:  
USE master;  
GO  
CREATE LOGIN [DOMAIN2\user2] FROM WINDOWS;  
GO  
GRANT CONNECT ON ENDPOINT::dbm_endpoint   
   TO [DOMAIN2\user2];  
GO  
  
-- If both service accounts run under the same domain account, skip this step. Otherwise,   
-- On the server instance that will host the secondary replica,  
-- create a login for the service account   
-- of the server instance that will host the primary replica, DOMAIN1\user1,   
-- and grant this login connect permissions on the endpoint:  
USE master;  
GO  
  
CREATE LOGIN [DOMAIN1\user1] FROM WINDOWS;  
GO  
GRANT CONNECT ON ENDPOINT::dbm_endpoint   
   TO [DOMAIN1\user1];  
GO  
  
-- On the server instance that will host the primary replica,   
-- create the availability group, MyAG:  
CREATE AVAILABILITY GROUP MyAG   
   FOR   
      DATABASE MyDB1, MyDB2   
   REPLICA ON   
      'COMPUTER01\AgHostInstance' WITH   
         (  
         ENDPOINT_URL = 'TCP://COMPUTER01.Adventure-Works.com:7022',  
         AVAILABILITY_MODE = SYNCHRONOUS_COMMIT,  
         FAILOVER_MODE = AUTOMATIC  
         ),  
      'COMPUTER02' WITH   
         (  
         ENDPOINT_URL = 'TCP://COMPUTER02.Adventure-Works.com:7022',  
         AVAILABILITY_MODE = SYNCHRONOUS_COMMIT,  
         FAILOVER_MODE = AUTOMATIC  
         );   
GO  
  
-- On the server instance that hosts the secondary replica,   
-- join the secondary replica to the availability group:  
ALTER AVAILABILITY GROUP MyAG JOIN;  
GO  
  
-- Restore database backups onto this server instance, using RESTORE WITH NORECOVERY:  
RESTORE DATABASE MyDb1   
    FROM DISK = N'\\FILESERVER\SQLbackups\MyDb1.bak'   
    WITH NORECOVERY  
GO  
  
RESTORE DATABASE MyDb2   
    FROM DISK = N'\\FILESERVER\SQLbackups\MyDb2.bak'   
    WITH NORECOVERY  
GO  
  
-- Back up the transaction log on each primary database:  
BACKUP LOG MyDb1   
TO DISK = N'\\FILESERVER\SQLbackups\MyDb1.bak'   
    WITH NOFORMAT  
GO  
  
BACKUP LOG MyDb2   
TO DISK = N'\\FILESERVER\SQLbackups\MyDb2.bak'   
    WITHNOFORMAT  
GO  
  
-- Restore the transaction log on each secondary database,  
-- using the WITH NORECOVERY option:  
RESTORE LOG MyDb1   
    FROM DISK = N'\\FILESERVER\SQLbackups\MyDb1.bak'   
    WITH FILE=1, NORECOVERY  
GO  
RESTORE LOG MyDb2   
    FROM DISK = N'\\FILESERVER\SQLbackups\MyDb2.bak'   
    WITH FILE=1, NORECOVERY  
GO  
  
-- On the server instance that hosts the secondary replica,   
-- join each secondary database to the availability group:  
ALTER DATABASE MyDb1 SET HADR AVAILABILITY GROUP = MyAG;  
GO  
  
ALTER DATABASE MyDb2 SET HADR AVAILABILITY GROUP = MyAG;  
GO
```  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="980ed-244">관련 작업</span><span class="sxs-lookup"><span data-stu-id="980ed-244">Related Tasks</span></span>  
 <span data-ttu-id="980ed-245">**가용성 그룹 및 복제본 속성을 구성하려면**</span><span class="sxs-lookup"><span data-stu-id="980ed-245">**To configure availability group and replica properties**</span></span>  
  
-   [<span data-ttu-id="980ed-246">가용성 복제본의 가용성 모드 변경&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="980ed-246">Change the Availability Mode of an Availability Replica &#40;SQL Server&#41;</span></span>](change-the-availability-mode-of-an-availability-replica-sql-server.md)  
  
-   [<span data-ttu-id="980ed-247">가용성 복제본의 장애 조치(failover) 모드 변경&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="980ed-247">Change the Failover Mode of an Availability Replica &#40;SQL Server&#41;</span></span>](change-the-failover-mode-of-an-availability-replica-sql-server.md)  
  
-   [<span data-ttu-id="980ed-248">가용성 그룹 수신기 만들기 또는 구성&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="980ed-248">Create or Configure an Availability Group Listener &#40;SQL Server&#41;</span></span>](create-or-configure-an-availability-group-listener-sql-server.md)  
  
-   [<span data-ttu-id="980ed-249">유연한 장애 조치(failover) 정책을 구성하여 자동 장애 조치의 상태 제어(AlwaysOn 가용성 그룹)</span><span class="sxs-lookup"><span data-stu-id="980ed-249">Configure the Flexible Failover Policy to Control Conditions for Automatic Failover (AlwaysOn Availability Groups)</span></span>](configure-flexible-automatic-failover-policy.md)  
  
-   [<span data-ttu-id="980ed-250">가용성 복제본 추가 또는 수정 시 엔드포인트 URL 지정&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="980ed-250">Specify the Endpoint URL When Adding or Modifying an Availability Replica &#40;SQL Server&#41;</span></span>](specify-endpoint-url-adding-or-modifying-availability-replica.md)  
  
-   [<span data-ttu-id="980ed-251">가용성 복제본에 백업 구성&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="980ed-251">Configure Backup on Availability Replicas &#40;SQL Server&#41;</span></span>](configure-backup-on-availability-replicas-sql-server.md)  
  
-   [<span data-ttu-id="980ed-252">가용성 복제본에 대한 읽기 전용 액세스 구성&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="980ed-252">Configure Read-Only Access on an Availability Replica &#40;SQL Server&#41;</span></span>](configure-read-only-access-on-an-availability-replica-sql-server.md)  
  
-   [<span data-ttu-id="980ed-253">가용성 그룹에 대한 읽기 전용 라우팅 구성&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="980ed-253">Configure Read-Only Routing for an Availability Group &#40;SQL Server&#41;</span></span>](configure-read-only-routing-for-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="980ed-254">가용성 복제본에 대한 세션 제한 시간 변경&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="980ed-254">Change the Session-Timeout Period for an Availability Replica &#40;SQL Server&#41;</span></span>](change-the-session-timeout-period-for-an-availability-replica-sql-server.md)  
  
 <span data-ttu-id="980ed-255">**가용성 그룹 구성을 완료하려면**</span><span class="sxs-lookup"><span data-stu-id="980ed-255">**To complete availability group configuration**</span></span>  
  
-   [<span data-ttu-id="980ed-256">가용성 그룹에 보조 복제본 조인&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="980ed-256">Join a Secondary Replica to an Availability Group &#40;SQL Server&#41;</span></span>](join-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="980ed-257">가용성 그룹에 대한 보조 데이터베이스 준비&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="980ed-257">Manually Prepare a Secondary Database for an Availability Group &#40;SQL Server&#41;</span></span>](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="980ed-258">가용성 그룹에 보조 데이터베이스 조인&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="980ed-258">Join a Secondary Database to an Availability Group &#40;SQL Server&#41;</span></span>](join-a-secondary-database-to-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="980ed-259">가용성 그룹 수신기 만들기 또는 구성&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="980ed-259">Create or Configure an Availability Group Listener &#40;SQL Server&#41;</span></span>](create-or-configure-an-availability-group-listener-sql-server.md)  
  
 <span data-ttu-id="980ed-260">**가용성 그룹을 만드는 다른 방법**</span><span class="sxs-lookup"><span data-stu-id="980ed-260">**Alternative ways to create an availability group**</span></span>  
  
-   [<span data-ttu-id="980ed-261">가용성 그룹 마법사 사용&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="980ed-261">Use the Availability Group Wizard &#40;SQL Server Management Studio&#41;</span></span>](use-the-availability-group-wizard-sql-server-management-studio.md)  
  
-   [<span data-ttu-id="980ed-262">새 가용성 그룹 대화 상자 사용&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="980ed-262">Use the New Availability Group Dialog Box &#40;SQL Server Management Studio&#41;</span></span>](use-the-new-availability-group-dialog-box-sql-server-management-studio.md)  
  
-   [<span data-ttu-id="980ed-263">가용성 그룹 만들기&#40;SQL Server PowerShell&#41;</span><span class="sxs-lookup"><span data-stu-id="980ed-263">Create an Availability Group &#40;SQL Server PowerShell&#41;</span></span>](../../../powershell/sql-server-powershell.md)  
  
 <span data-ttu-id="980ed-264">**AlwaysOn 가용성 그룹을 사용하도록 설정하려면**</span><span class="sxs-lookup"><span data-stu-id="980ed-264">**To enable AlwaysOn Availability Groups**</span></span>  
  
-   [<span data-ttu-id="980ed-265">AlwaysOn 가용성 그룹 활성화 및 비활성화&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="980ed-265">Enable and Disable AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](enable-and-disable-always-on-availability-groups-sql-server.md)  
  
 <span data-ttu-id="980ed-266">**데이터베이스 미러링 엔드포인트를 구성하려면**</span><span class="sxs-lookup"><span data-stu-id="980ed-266">**To configure a database mirroring endpoint**</span></span>  
  
-   [<span data-ttu-id="980ed-267">AlwaysOn 가용성 그룹 &#40;SQL Server PowerShell에 대 한 데이터베이스 미러링 끝점을 만듭니다&#41;</span><span class="sxs-lookup"><span data-stu-id="980ed-267">Create a Database Mirroring Endpoint for AlwaysOn Availability Groups &#40;SQL Server PowerShell&#41;</span></span>](database-mirroring-always-on-availability-groups-powershell.md)  
  
-   [<span data-ttu-id="980ed-268">Windows 인증에 대한 데이터베이스 미러링 엔드포인트 만들기&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="980ed-268">Create a Database Mirroring Endpoint for Windows Authentication &#40;Transact-SQL&#41;</span></span>](../../database-mirroring/create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md)  
  
-   [<span data-ttu-id="980ed-269">데이터베이스 미러링 엔드포인트에 대한 인증서 사용&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="980ed-269">Use Certificates for a Database Mirroring Endpoint &#40;Transact-SQL&#41;</span></span>](../../database-mirroring/use-certificates-for-a-database-mirroring-endpoint-transact-sql.md)  
  
-   [<span data-ttu-id="980ed-270">가용성 복제본 추가 또는 수정 시 엔드포인트 URL 지정&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="980ed-270">Specify the Endpoint URL When Adding or Modifying an Availability Replica &#40;SQL Server&#41;</span></span>](specify-endpoint-url-adding-or-modifying-availability-replica.md)  
  
 <span data-ttu-id="980ed-271">**AlwaysOn 가용성 그룹 구성 문제를 해결하려면**</span><span class="sxs-lookup"><span data-stu-id="980ed-271">**To troubleshoot AlwaysOn Availability Groups configuration**</span></span>  
  
-   [<span data-ttu-id="980ed-272">삭제 된 SQL Server (AlwaysOn 가용성 그룹 구성) 문제 해결</span><span class="sxs-lookup"><span data-stu-id="980ed-272">Troubleshoot AlwaysOn Availability Groups Configuration (SQL Server)deleted</span></span>](troubleshoot-always-on-availability-groups-configuration-sql-server.md)  
  
-   [<span data-ttu-id="980ed-273">실패 한 파일 추가 작업 문제 해결 AlwaysOn 가용성 그룹 &#40;&#41;</span><span class="sxs-lookup"><span data-stu-id="980ed-273">Troubleshoot a Failed Add-File Operation &#40;AlwaysOn Availability Groups&#41;</span></span>](troubleshoot-a-failed-add-file-operation-always-on-availability-groups.md)  
  
##  <a name="related-content"></a><a name="RelatedContent"></a> <span data-ttu-id="980ed-274">관련 내용</span><span class="sxs-lookup"><span data-stu-id="980ed-274">Related Content</span></span>  
  
-   <span data-ttu-id="980ed-275">**블로그:**</span><span class="sxs-lookup"><span data-stu-id="980ed-275">**Blogs:**</span></span>  
  
     [<span data-ttu-id="980ed-276">AlwaysON - HADRON 학습 시리즈: HADRON 지원 데이터베이스에 대한 작업자 풀 사용</span><span class="sxs-lookup"><span data-stu-id="980ed-276">AlwaysON - HADRON Learning Series: Worker Pool Usage for HADRON Enabled Databases</span></span>](https://blogs.msdn.com/b/psssql/archive/2012/05/17/alwayson-hadron-learning-series-worker-pool-usage-for-hadron-enabled-databases.aspx)  
  
     [<span data-ttu-id="980ed-277">SQL Server AlwaysOn 팀 블로그: 공식 SQL Server AlwaysOn 팀 블로그</span><span class="sxs-lookup"><span data-stu-id="980ed-277">SQL Server AlwaysOn Team Blogs: The official SQL Server AlwaysOn Team Blog</span></span>](https://blogs.msdn.com/b/sqlalwayson/)  
  
     [<span data-ttu-id="980ed-278">CSS SQL Server 엔지니어 블로그</span><span class="sxs-lookup"><span data-stu-id="980ed-278">CSS SQL Server Engineers Blogs</span></span>](https://blogs.msdn.com/b/psssql/)  
  
-   <span data-ttu-id="980ed-279">**비디오:**</span><span class="sxs-lookup"><span data-stu-id="980ed-279">**Videos:**</span></span>  
  
     [<span data-ttu-id="980ed-280">Microsoft SQL Server 코드 이름 "Denali" AlwaysOn 시리즈, 1부: 차세대 고가용성 솔루션 소개</span><span class="sxs-lookup"><span data-stu-id="980ed-280">Microsoft SQL Server Code-Named "Denali" AlwaysOn Series,Part 1: Introducing the Next Generation High Availability Solution</span></span>](https://channel9.msdn.com/Events/TechEd/NorthAmerica/2011/DBI302)  
  
     [<span data-ttu-id="980ed-281">Microsoft SQL Server 코드 이름 "Denali" AlwaysOn 시리즈, 파트 2: AlwaysOn을 사용하여 중요 환경 고가용성 솔루션 빌드</span><span class="sxs-lookup"><span data-stu-id="980ed-281">Microsoft SQL Server Code-Named "Denali" AlwaysOn Series,Part 2: Building a Mission-Critical High Availability Solution Using AlwaysOn</span></span>](https://channel9.msdn.com/Events/TechEd/NorthAmerica/2011/DBI404)  
  
-   <span data-ttu-id="980ed-282">**백서:**</span><span class="sxs-lookup"><span data-stu-id="980ed-282">**Whitepapers:**</span></span>  
  
     [<span data-ttu-id="980ed-283">고가용성 및 재해 복구를 위한 Microsoft SQL Server AlwaysOn 솔루션 가이드</span><span class="sxs-lookup"><span data-stu-id="980ed-283">Microsoft SQL Server AlwaysOn Solutions Guide for High Availability and Disaster Recovery</span></span>](https://go.microsoft.com/fwlink/?LinkId=227600)  
  
     [<span data-ttu-id="980ed-284">SQL Server 2012에 대한 Microsoft 백서</span><span class="sxs-lookup"><span data-stu-id="980ed-284">Microsoft White Papers for SQL Server 2012</span></span>](https://msdn.microsoft.com/library/hh403491.aspx)  
  
     [<span data-ttu-id="980ed-285">SQL Server 고객 자문 팀 백서</span><span class="sxs-lookup"><span data-stu-id="980ed-285">SQL Server Customer Advisory Team Whitepapers</span></span>](http://sqlcat.com/)  
  
## <a name="see-also"></a><span data-ttu-id="980ed-286">참고 항목</span><span class="sxs-lookup"><span data-stu-id="980ed-286">See Also</span></span>  
 <span data-ttu-id="980ed-287">[데이터베이스 미러링 엔드포인트&#40;SQL Server&#41;](../../database-mirroring/the-database-mirroring-endpoint-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="980ed-287">[The Database Mirroring Endpoint &#40;SQL Server&#41;](../../database-mirroring/the-database-mirroring-endpoint-sql-server.md) </span></span>  
 <span data-ttu-id="980ed-288">[AlwaysOn 가용성 그룹 &#40;SQL Server 개요&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="980ed-288">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 [<span data-ttu-id="980ed-289">가용성 그룹 수신기, 클라이언트 연결 및 애플리케이션 장애 조치(failover)&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="980ed-289">Availability Group Listeners, Client Connectivity, and Application Failover &#40;SQL Server&#41;</span></span>](../../listeners-client-connectivity-application-failover.md)   
