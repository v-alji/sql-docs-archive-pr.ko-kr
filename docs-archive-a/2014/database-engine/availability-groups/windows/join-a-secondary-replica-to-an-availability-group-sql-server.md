---
title: 가용성 그룹에 보조 복제본 조인(SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.availabilitygroup.joinreplica.f1
helpviewer_keywords:
- Availability Groups [SQL Server], availability replicas
- Availability Groups [SQL Server], joining
- Availability Groups [SQL Server], configuring
ms.assetid: e5bd2489-097a-490e-8ea1-34fe48378ad1
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c38c2d59a46b15fc9a1dca77ae6a67e8e59e1b80
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650264"
---
# <a name="join-a-secondary-replica-to-an-availability-group-sql-server"></a><span data-ttu-id="cb63e-102">가용성 그룹에 보조 복제본 조인(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="cb63e-102">Join a Secondary Replica to an Availability Group (SQL Server)</span></span>
  <span data-ttu-id="cb63e-103">이 항목에서는 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)]또는 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]의 PowerShell을 사용하여 AlwaysOn 가용성 그룹에 보조 복제본을 조인하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="cb63e-103">This topic describes how to join a secondary replica to an AlwaysOn availability group by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)], or PowerShell in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="cb63e-104">AlwaysOn 가용성 그룹에 보조 복제본을 추가한 후에는 보조 복제본을 가용성 그룹에 조인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cb63e-104">After a secondary replica is added to an AlwaysOn availability group, the secondary replica must be joined to the availability group.</span></span> <span data-ttu-id="cb63e-105">복제본 조인 작업은 보조 복제본을 호스팅하는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인스턴스에서 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cb63e-105">The join-replica operation must be performed on the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] that is hosting the secondary replica.</span></span>  
  
-   <span data-ttu-id="cb63e-106">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="cb63e-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="cb63e-107">필수 구성 요소</span><span class="sxs-lookup"><span data-stu-id="cb63e-107">Prerequisites</span></span>](#Prerequisites)  
  
     [<span data-ttu-id="cb63e-108">보안</span><span class="sxs-lookup"><span data-stu-id="cb63e-108">Security</span></span>](#Security)  
  
-   <span data-ttu-id="cb63e-109">**보조 데이터베이스를 준비하려면:**</span><span class="sxs-lookup"><span data-stu-id="cb63e-109">**To prepare a secondary database, using:**</span></span>  
  
     [<span data-ttu-id="cb63e-110">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="cb63e-110">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="cb63e-111">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="cb63e-111">Transact-SQL</span></span>](#TsqlProcedure)  
  
     [<span data-ttu-id="cb63e-112">PowerShell</span><span class="sxs-lookup"><span data-stu-id="cb63e-112">PowerShell</span></span>](#PowerShellProcedure)  
  
-   <span data-ttu-id="cb63e-113">**후속 작업:** [보조 데이터베이스 구성](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="cb63e-113">**Follow Up:** [Configure Secondary Databases](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="cb63e-114">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="cb63e-114">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="cb63e-115">필수 조건</span><span class="sxs-lookup"><span data-stu-id="cb63e-115">Prerequisites</span></span>  
  
-   <span data-ttu-id="cb63e-116">가용성 그룹의 주 복제본은 현재 온라인 상태여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cb63e-116">The primary replica of the availability group must currently be online.</span></span>  
  
-   <span data-ttu-id="cb63e-117">아직 가용성 그룹에 조인되지 않은 보조 복제본을 호스팅하는 서버 인스턴스에 연결되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cb63e-117">You must be connected to the server instance that hosts a secondary replica that has not yet have been joined to the availability group.</span></span>  
  
-   <span data-ttu-id="cb63e-118">로컬 서버 인스턴스에서 주 복제본을 호스팅하는 서버 인스턴스의 데이터베이스 미러링 엔드포인트에 연결할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cb63e-118">The local server instance must be able to connect to the database mirroring endpoint of the server instance that is hosting the primary replica.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="cb63e-119">필수 구성 요소가 충족되지 않으면 조인 작업이 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="cb63e-119">If any prerequisite is not met, the join operation fails.</span></span> <span data-ttu-id="cb63e-120">조인 시도에 실패 후 가용성 그룹에 조인하기 전 보조 복제본을 제거하고 다시 추가하려면 주 복제본을 호스팅하는 서버 인스턴스에 연결해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cb63e-120">After a failed join attempt, you might need to connect to the server instance that hosts the primary replica to remove and re-add the secondary replica before you can join it to the availability group.</span></span> <span data-ttu-id="cb63e-121">자세한 내용은 [가용성 그룹에서 보조 복제본 제거&#40;SQL Server&#41;](remove-a-secondary-replica-from-an-availability-group-sql-server.md) 및 [가용성 그룹에 보조 복제본 추가&#40;SQL Server&#41;](add-a-secondary-replica-to-an-availability-group-sql-server.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="cb63e-121">For more information, see [Remove a Secondary Replica from an Availability Group &#40;SQL Server&#41;](remove-a-secondary-replica-from-an-availability-group-sql-server.md) and [Add a Secondary Replica to an Availability Group &#40;SQL Server&#41;](add-a-secondary-replica-to-an-availability-group-sql-server.md).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="cb63e-122">보안</span><span class="sxs-lookup"><span data-stu-id="cb63e-122">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="cb63e-123">권한</span><span class="sxs-lookup"><span data-stu-id="cb63e-123">Permissions</span></span>  
 <span data-ttu-id="cb63e-124">가용성 그룹에 대한 ALTER AVAILABILITY GROUP 권한, CONTROL AVAILABILITY GROUP 권한, ALTER ANY AVAILABILITY GROUP 권한 또는 CONTROL SERVER 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="cb63e-124">Requires ALTER AVAILABILITY GROUP permission on the availability group, CONTROL AVAILABILITY GROUP permission, ALTER ANY AVAILABILITY GROUP permission, or CONTROL SERVER permission.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="cb63e-125">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="cb63e-125">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="cb63e-126">**가용성 그룹에 가용성 복제본을 조인하려면**</span><span class="sxs-lookup"><span data-stu-id="cb63e-126">**To join an availability replica to an availability group**</span></span>  
  
1.  <span data-ttu-id="cb63e-127">개체 탐색기에서 보조 복제본을 호스팅하는 서버 인스턴스에 연결하고 서버 트리를 확장할 서버 이름을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cb63e-127">In Object Explorer, connect to the server instance that hosts the secondary replica, and click the server name to expand the server tree.</span></span>  
  
2.  <span data-ttu-id="cb63e-128">**AlwaysOn 고가용성** 및 **가용성 그룹** 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="cb63e-128">Expand the **AlwaysOn High Availability** node and the **Availability Groups** node.</span></span>  
  
3.  <span data-ttu-id="cb63e-129">연결된 보조 복제본의 가용성 그룹을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="cb63e-129">Select the availability group of the secondary replica to which you are connected.</span></span>  
  
4.  <span data-ttu-id="cb63e-130">보조 복제본을 마우스 오른쪽 단추로 클릭하고 **가용성 그룹에 조인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cb63e-130">Right-click the secondary replica, and click **Join to Availability Group**.</span></span>  
  
5.  <span data-ttu-id="cb63e-131">**가용성 그룹에 복제본 조인** 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="cb63e-131">This opens the **Join Replica to Availability Group** dialog box.</span></span>  
  
6.  <span data-ttu-id="cb63e-132">가용성 그룹에 보조 복제본을 조인하려면 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cb63e-132">To join the secondary replica to the availability group, click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="cb63e-133">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="cb63e-133">Using Transact-SQL</span></span>  
 <span data-ttu-id="cb63e-134">**가용성 그룹에 가용성 복제본을 조인하려면**</span><span class="sxs-lookup"><span data-stu-id="cb63e-134">**To join an availability replica to an availability group**</span></span>  
  
1.  <span data-ttu-id="cb63e-135">보조 복제본을 호스팅하는 서버 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="cb63e-135">Connect to the server instance that hosts the secondary replica.</span></span>  
  
2.  <span data-ttu-id="cb63e-136">다음과 같은 [ALTER AVAILABILITY GROUP](/sql/t-sql/statements/alter-availability-group-transact-sql) 문을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="cb63e-136">Use the [ALTER AVAILABILITY GROUP](/sql/t-sql/statements/alter-availability-group-transact-sql) statement, as follows:</span></span>  
  
     <span data-ttu-id="cb63e-137">ALTER AVAILABILITY GROUP *group_name* JOIN</span><span class="sxs-lookup"><span data-stu-id="cb63e-137">ALTER AVAILABILITY GROUP *group_name* JOIN</span></span>  
  
     <span data-ttu-id="cb63e-138">여기서 *group_name* 은 가용성 그룹의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="cb63e-138">where *group_name* is the name of the availability group.</span></span>  
  
     <span data-ttu-id="cb63e-139">다음 예에서는 보조 복제본을 `MyAG` 가용성 그룹에 조인합니다.</span><span class="sxs-lookup"><span data-stu-id="cb63e-139">The following example, joins the secondary replica to the `MyAG` availability group.</span></span>  
  
    ```sql
    ALTER AVAILABILITY GROUP MyAG JOIN;  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="cb63e-140">컨텍스트에서 사용되는 이 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 문을 보려면 [가용성 그룹 만들기&#40;Transact-SQL&#41;](create-an-availability-group-transact-sql.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="cb63e-140">To see this [!INCLUDE[tsql](../../../includes/tsql-md.md)] statement used in context, see [Create an Availability Group &#40;Transact-SQL&#41;](create-an-availability-group-transact-sql.md).</span></span>  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a> <span data-ttu-id="cb63e-141">PowerShell 사용</span><span class="sxs-lookup"><span data-stu-id="cb63e-141">Using PowerShell</span></span>  
 <span data-ttu-id="cb63e-142">**가용성 그룹에 가용성 복제본을 조인하려면**</span><span class="sxs-lookup"><span data-stu-id="cb63e-142">**To join an availability replica to an availability group**</span></span>  
  
 <span data-ttu-id="cb63e-143">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell 공급자에서 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="cb63e-143">In the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell provider:</span></span>  
  
1.  <span data-ttu-id="cb63e-144">보조 복제본을 호스팅하는 서버 인스턴스로 디렉터리를 변경(`cd`)합니다.</span><span class="sxs-lookup"><span data-stu-id="cb63e-144">Change directory (`cd`) to the server instance that hosts the secondary replica.</span></span>  
  
2.  <span data-ttu-id="cb63e-145">가용성 그룹의 이름으로 **Join-SqlAvailabilityGroup** cmdlet을 실행하여 보조 복제본을 가용성 그룹에 조인합니다.</span><span class="sxs-lookup"><span data-stu-id="cb63e-145">Join the secondary replica to the availability group by executing the **Join-SqlAvailabilityGroup** cmdlet with the name of the availability group.</span></span>  
  
     <span data-ttu-id="cb63e-146">예를 들어 다음 명령은 지정된 경로에 있는 서버 인스턴스가 호스팅하는 보조 복제본을 `MyAg`라는 가용성 그룹에 조인합니다.</span><span class="sxs-lookup"><span data-stu-id="cb63e-146">For example, the following command joins a secondary replica hosted by the server instance located at the specified path to the availability group named `MyAg`.</span></span>  <span data-ttu-id="cb63e-147">이 서버 인스턴스는 이 가용성 그룹에서 보조 복제본을 호스팅해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cb63e-147">This server instance must host a secondary replica in this availability group.</span></span>  
  
    ```powershell
    Join-SqlAvailabilityGroup -Path SQLSERVER:\SQL\SecondaryServer\InstanceName -Name 'MyAg'  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="cb63e-148">cmdlet의 구문을 보려면 `Get-Help` PowerShell 환경에서 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] cmdlet을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="cb63e-148">To view the syntax of a cmdlet, use the `Get-Help` cmdlet in the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell environment.</span></span> <span data-ttu-id="cb63e-149">자세한 내용은 [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="cb63e-149">For more information, see [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).</span></span>  
  
 <span data-ttu-id="cb63e-150">**SQL Server PowerShell 공급자를 설정하고 사용하려면**</span><span class="sxs-lookup"><span data-stu-id="cb63e-150">**To set up and use the SQL Server PowerShell provider**</span></span>  
  
-   [<span data-ttu-id="cb63e-151">SQL Server PowerShell 공급자</span><span class="sxs-lookup"><span data-stu-id="cb63e-151">SQL Server PowerShell Provider</span></span>](../../../powershell/sql-server-powershell-provider.md)  
  
##  <a name="follow-up-configure-secondary-databases"></a><a name="FollowUp"></a><span data-ttu-id="cb63e-152">후속 작업: 보조 데이터베이스 구성</span><span class="sxs-lookup"><span data-stu-id="cb63e-152">Follow Up: Configure Secondary Databases</span></span>  
 <span data-ttu-id="cb63e-153">가용성 그룹의 모든 데이터베이스에 대해, 보조 복제본을 호스팅하는 서버 인스턴스에 보조 데이터베이스를 두어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cb63e-153">For every database in the availability group, you need a secondary database on the server instance that is hosting the secondary replica.</span></span> <span data-ttu-id="cb63e-154">다음과 같이 보조 복제본을 가용성 그룹에 조인하기 전이나 후에 보조 데이터베이스를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cb63e-154">You can configure secondary databases either before or after you join a secondary replica to an availability group, as follows:</span></span>  
  
1.  <span data-ttu-id="cb63e-155">모든 복원 작업에는 RESTORE WITH NORECOVERY를 사용하여 각 주 데이터베이스의 최신 데이터베이스 및 로그 백업을 보조 복제본을 호스팅하는 서버 인스턴스에 복원합니다.</span><span class="sxs-lookup"><span data-stu-id="cb63e-155">Restore recent database and log backups of each primary database onto the server instance that hosts the secondary replica, using RESTORE WITH NORECOVERY for every restore operation.</span></span> <span data-ttu-id="cb63e-156">자세한 내용은 [가용성 그룹에 대한 보조 데이터베이스 수동 준비&#40;SQL Server&#41;](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md)또는 PowerShell을 사용하여 Always On 가용성 그룹에 보조 데이터베이스를 조인하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="cb63e-156">For more information, see [Manually Prepare a Secondary Database for an Availability Group &#40;SQL Server&#41;](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md).</span></span>  
  
2.  <span data-ttu-id="cb63e-157">가용성 그룹에 각 보조 데이터베이스를 조인합니다.</span><span class="sxs-lookup"><span data-stu-id="cb63e-157">Join each secondary database to the availability group.</span></span> <span data-ttu-id="cb63e-158">자세한 내용은 [가용성 그룹에 보조 데이터베이스 조인&#40;SQL Server&#41;](join-a-secondary-database-to-an-availability-group-sql-server.md)인스턴스에 AlwaysOn 가용성 그룹을 만드는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="cb63e-158">For more information, see [Join a Secondary Database to an Availability Group &#40;SQL Server&#41;](join-a-secondary-database-to-an-availability-group-sql-server.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb63e-159">참고 항목</span><span class="sxs-lookup"><span data-stu-id="cb63e-159">See Also</span></span>  
 <span data-ttu-id="cb63e-160">[가용성 그룹의 생성 및 구성&#40;SQL Server&#41;](creation-and-configuration-of-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="cb63e-160">[Creation and Configuration of Availability Groups &#40;SQL Server&#41;](creation-and-configuration-of-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="cb63e-161">[AlwaysOn 가용성 그룹 &#40;SQL Server 개요&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="cb63e-161">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 [<span data-ttu-id="cb63e-162">삭제&#41;SQL Server AlwaysOn 가용성 그룹 구성 &#40;문제 해결</span><span class="sxs-lookup"><span data-stu-id="cb63e-162">Troubleshoot AlwaysOn Availability Groups Configuration &#40;SQL Server&#41;deleted</span></span>](troubleshoot-always-on-availability-groups-configuration-sql-server.md)  
