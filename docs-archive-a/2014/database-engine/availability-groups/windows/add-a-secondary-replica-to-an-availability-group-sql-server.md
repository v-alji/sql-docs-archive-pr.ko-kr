---
title: 가용성 그룹에 보조 복제본 추가(SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], availability replicas
- Availability Groups [SQL Server], configuring
ms.assetid: 6669dcce-85f9-495f-aadf-7f62cff4a9da
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 498103a781641c72e166c6b11663f5248ae5ccfc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647257"
---
# <a name="add-a-secondary-replica-to-an-availability-group-sql-server"></a><span data-ttu-id="563e8-102">가용성 그룹에 보조 복제본 추가(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="563e8-102">Add a Secondary Replica to an Availability Group (SQL Server)</span></span>
  <span data-ttu-id="563e8-103">이 항목에서는 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)]또는 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]의 PowerShell을 사용하여 기존 AlwaysOn 가용성 그룹에 보조 복제본을 추가하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="563e8-103">This topic describes how to add a secondary replica to an existing AlwaysOn availability group by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)], or PowerShell in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span>  
  
-   <span data-ttu-id="563e8-104">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="563e8-104">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="563e8-105">사전 요구 사항 및 제한 사항</span><span class="sxs-lookup"><span data-stu-id="563e8-105">Prerequisites and Restrictions</span></span>](#PrerequisitesRestrictions)  
  
     [<span data-ttu-id="563e8-106">보안</span><span class="sxs-lookup"><span data-stu-id="563e8-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="563e8-107">**복제본을 추가하려면:**</span><span class="sxs-lookup"><span data-stu-id="563e8-107">**To add a replica, using:**</span></span>  
  
     [<span data-ttu-id="563e8-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="563e8-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="563e8-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="563e8-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
     [<span data-ttu-id="563e8-110">PowerShell</span><span class="sxs-lookup"><span data-stu-id="563e8-110">PowerShell</span></span>](#PowerShellProcedure)  
  
-   <span data-ttu-id="563e8-111">**후속 작업:**  [복제본을 추가한 후](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="563e8-111">**Follow Up:**  [After Adding a Secondary Replica](#FollowUp)</span></span>  
  
## <a name="before-you-begin"></a><span data-ttu-id="563e8-112">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="563e8-112">Before You Begin</span></span>  
 <span data-ttu-id="563e8-113">가용성 그룹을 처음 만들어 보는 경우 이 섹션을 먼저 읽는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="563e8-113">We strongly recommend that you read this section before attempting to create your first availability group.</span></span>  
  
##  <a name="prerequisites-and-restrictions"></a><a name="PrerequisitesRestrictions"></a> <span data-ttu-id="563e8-114">사전 요구 사항 및 제한 사항</span><span class="sxs-lookup"><span data-stu-id="563e8-114">Prerequisites and Restrictions</span></span>  
  
-   <span data-ttu-id="563e8-115">주 복제본을 호스팅하는 서버 인스턴스에 연결되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="563e8-115">You must be connected to the server instance that hosts the primary replica.</span></span>  
  
 <span data-ttu-id="563e8-116">자세한 내용은 [AlwaysOn 가용성 그룹에 대한 필수 조건, 제한 사항 및 권장 사항&#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="563e8-116">For more information, see [Prerequisites, Restrictions, and Recommendations for AlwaysOn Availability Groups &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md).</span></span>  
  
##  <a name="security"></a><a name="Security"></a> <span data-ttu-id="563e8-117">보안</span><span class="sxs-lookup"><span data-stu-id="563e8-117">Security</span></span>  
  
###  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="563e8-118">권한</span><span class="sxs-lookup"><span data-stu-id="563e8-118">Permissions</span></span>  
 <span data-ttu-id="563e8-119">가용성 그룹에 대한 ALTER AVAILABILITY GROUP 권한, CONTROL AVAILABILITY GROUP 권한, ALTER ANY AVAILABILITY GROUP 권한 또는 CONTROL SERVER 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="563e8-119">Requires ALTER AVAILABILITY GROUP permission on the availability group, CONTROL AVAILABILITY GROUP permission, ALTER ANY AVAILABILITY GROUP permission, or CONTROL SERVER permission.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="563e8-120">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="563e8-120">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="563e8-121">**복제본을 추가하려면**</span><span class="sxs-lookup"><span data-stu-id="563e8-121">**To add a replica**</span></span>  
  
1.  <span data-ttu-id="563e8-122">개체 탐색기에서 주 복제본을 호스팅하는 서버 인스턴스에 연결하고 서버 트리를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="563e8-122">In Object Explorer, connect to the server instance that hosts the primary replica, and expand the server tree.</span></span>  
  
2.  <span data-ttu-id="563e8-123">**AlwaysOn 고가용성** 및 **가용성 그룹** 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="563e8-123">Expand the **AlwaysOn High Availability** node and the **Availability Groups** node.</span></span>  
  
3.  <span data-ttu-id="563e8-124">가용성 그룹을 마우스 오른쪽 단추로 클릭하고 다음 명령 중 하나를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="563e8-124">Right-click the availability group, and select one of the following commands:</span></span>  
  
    -   <span data-ttu-id="563e8-125">가용성 그룹에 복제본 추가 마법사를 실행하려면 **복제본 추가** 명령을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="563e8-125">Select the **Add Replica** command to launch the Add Replica to Availability Group Wizard.</span></span> <span data-ttu-id="563e8-126">자세한 내용은 [가용성 그룹에 복제본 추가 마법사 사용&#40;SQL Server Management Studio&#41;](use-the-add-replica-to-availability-group-wizard-sql-server-management-studio.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="563e8-126">For more information, see [Use the Add Replica to Availability Group Wizard &#40;SQL Server Management Studio&#41;](use-the-add-replica-to-availability-group-wizard-sql-server-management-studio.md).</span></span>  
  
    -   <span data-ttu-id="563e8-127">또는 **속성** 명령을 선택하여 **가용성 그룹 속성** 대화 상자를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="563e8-127">Alternatively, select the **Properties** command to open the **Availability Group Properties** dialog box.</span></span> <span data-ttu-id="563e8-128">이 대화 상자에서 복제본을 추가하는 단계는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="563e8-128">The steps for adding a replica in this dialog box are as follows:</span></span>  
  
        1.  <span data-ttu-id="563e8-129">대화 상자의 **가용성 복제본** 창에서 **추가** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="563e8-129">In the **Availability Replicas** pane of the dialog box, click the **Add** button.</span></span> <span data-ttu-id="563e8-130">그러면 빈 서버 인스턴스 필드가 선택된 상태로 복제본 항목이 만들어지고 선택됩니다.</span><span class="sxs-lookup"><span data-stu-id="563e8-130">This creates and selects a replica entry in which the blank Server Instance field is selected.</span></span>  
  
        2.  <span data-ttu-id="563e8-131">가용성 복제본 호스팅을 위한 사전 요구 사항을 충족하는 서버 인스턴스의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="563e8-131">Enter the name of a server instance that meets the prerequisites for hosting an availability replica.</span></span>  
  
         <span data-ttu-id="563e8-132">다른 복제본을 추가하려면 위의 단계를 반복합니다.</span><span class="sxs-lookup"><span data-stu-id="563e8-132">To add an additional replicas, repeat the preceding steps.</span></span> <span data-ttu-id="563e8-133">복제본 지정을 마치면 **확인** 을 클릭하여 작업을 완료합니다.</span><span class="sxs-lookup"><span data-stu-id="563e8-133">When you are done specifying replicas, click **OK** to complete the operation.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="563e8-134">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="563e8-134">Using Transact-SQL</span></span>  
 <span data-ttu-id="563e8-135">**복제본을 추가하려면**</span><span class="sxs-lookup"><span data-stu-id="563e8-135">**To add a replica**</span></span>  
  
1.  <span data-ttu-id="563e8-136">주 복제본을 호스팅하는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="563e8-136">Connect to the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] that hosts the primary replica.</span></span>  
  
2.  <span data-ttu-id="563e8-137">ALTER AVAILABILITY GROUP 문의 ADD REPLICA ON 절을 사용하여 가용성 그룹에 새 보조 복제본을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="563e8-137">Add the new secondary replica to the availability group by using the ADD REPLICA ON clause of the ALTER AVAILABILITY GROUP statement.</span></span> <span data-ttu-id="563e8-138">ENDPOINT_URL, AVAILABILITY_MODE 및 FAILOVER_MODE 옵션은 ADD REPLICA ON 절에 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="563e8-138">The ENDPOINT_URL, AVAILABILITY_MODE, and FAILOVER_MODE options are required in an ADD REPLICA ON clause.</span></span> <span data-ttu-id="563e8-139">다른 복제본 옵션 BACKUP_PRIORITY, SECONDARY_ROLE, PRIMARY_ROLE 및 SESSION_TIMEOUT은 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="563e8-139">The other replica options- BACKUP_PRIORITY, SECONDARY_ROLE, PRIMARY_ROLE, and SESSION_TIMEOUT-are optional.</span></span> <span data-ttu-id="563e8-140">자세한 내용은 [ALTER AVAILABILITY GROUP&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-availability-group-transact-sql)또는 PowerShell을 사용하여 기존 Always On 가용성 그룹에 보조 복제본을 추가하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="563e8-140">For more information, see [ALTER AVAILABILITY GROUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-availability-group-transact-sql).</span></span>  
  
     <span data-ttu-id="563e8-141">예를 들어 다음 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 문은 엔드포인트 URL이 `MyAG`인 `COMPUTER04`에서 호스팅되는 기본 서버 인스턴스의 `TCP://COMPUTER04.Adventure-Works.com:5022'`라는 가용성 그룹에 새 복제본을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="563e8-141">For example, the following [!INCLUDE[tsql](../../../includes/tsql-md.md)] statement creates a new replica to an availability group named `MyAG` on the default server instance hosted by `COMPUTER04`, whose endpoint URL is `TCP://COMPUTER04.Adventure-Works.com:5022'`.</span></span> <span data-ttu-id="563e8-142">이 복제본은 수동 장애 조치(Failover) 및 비동기 커밋 가용성 모드를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="563e8-142">This replica supports manual failover and asynchronous-commit availability mode.</span></span>  
  
    ```sql
    ALTER AVAILABILITY GROUP MyAG ADD REPLICA ON 'COMPUTER04'   
       WITH (  
             ENDPOINT_URL = 'TCP://COMPUTER04.Adventure-Works.com:5022',  
             AVAILABILITY_MODE = ASYNCHRONOUS_COMMIT,  
             FAILOVER_MODE = MANUAL  
             );  
    ```  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a> <span data-ttu-id="563e8-143">PowerShell 사용</span><span class="sxs-lookup"><span data-stu-id="563e8-143">Using PowerShell</span></span>  
 <span data-ttu-id="563e8-144">**복제본을 추가하려면**</span><span class="sxs-lookup"><span data-stu-id="563e8-144">**To add a replica**</span></span>  
  
1.  <span data-ttu-id="563e8-145">주 복제본을 호스팅하는 서버 인스턴스로 디렉터리를 변경(`cd`)합니다.</span><span class="sxs-lookup"><span data-stu-id="563e8-145">Change directory (`cd`) to the server instance that hosts the primary replica.</span></span>  
  
2.  <span data-ttu-id="563e8-146">**New-SqlAvailabilityReplica** cmdlet을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="563e8-146">Use the **New-SqlAvailabilityReplica** cmdlet.</span></span>  
  
     <span data-ttu-id="563e8-147">예를 들어 다음 명령은 `MyAg`라는 기존 가용성 그룹에 가용성 복제본을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="563e8-147">For example, the following command adds an availability replica to an existing availability group named `MyAg`.</span></span> <span data-ttu-id="563e8-148">이 복제본은 수동 장애 조치(Failover) 및 비동기 커밋 가용성 모드를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="563e8-148">This replica supports manual failover and asynchronous-commit availability mode.</span></span> <span data-ttu-id="563e8-149">이 복제본은 이 보조 역할에서 읽기 액세스 연결을 지원하므로 읽기 전용 프로세싱을 이 복제본으로 오프로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="563e8-149">In the secondary role, this replica will support read access connections, allowing you to offload read-only processing to this replica.</span></span>  
  
    ```powershell
    $agPath = "SQLSERVER:\Sql\PrimaryServer\InstanceName\AvailabilityGroups\MyAg"  
    $endpointURL = "TCP://PrimaryServerName.domain.com:5022"  
    $failoverMode = "Manual"  
    $availabilityMode = "AsynchronousCommit"  
    $secondaryReadMode = "AllowAllConnections"  
  
    New-SqlAvailabilityReplica -Name SecondaryServer\Instance `   
    -EndpointUrl $endpointURL `   
    -FailoverMode $failoverMode `   
    -AvailabilityMode $availabilityMode `   
    -ConnectionModeInSecondaryRole $secondaryReadMode `   
    -Path $agPath  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="563e8-150">cmdlet의 구문을 보려면 `Get-Help` PowerShell 환경에서 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] cmdlet을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="563e8-150">To view the syntax of a cmdlet, use the `Get-Help` cmdlet in the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell environment.</span></span> <span data-ttu-id="563e8-151">자세한 내용은 [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="563e8-151">For more information, see [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).</span></span>  
  
 <span data-ttu-id="563e8-152">**SQL Server PowerShell 공급자를 설정하고 사용하려면**</span><span class="sxs-lookup"><span data-stu-id="563e8-152">**To set up and use the SQL Server PowerShell provider**</span></span>  
  
-   [<span data-ttu-id="563e8-153">SQL Server PowerShell 공급자</span><span class="sxs-lookup"><span data-stu-id="563e8-153">SQL Server PowerShell Provider</span></span>](../../../powershell/sql-server-powershell-provider.md)  
  
##  <a name="follow-up-after-adding-a-secondary-replica"></a><a name="FollowUp"></a><span data-ttu-id="563e8-154">후속 작업: 보조 복제본을 추가한 후</span><span class="sxs-lookup"><span data-stu-id="563e8-154">Follow Up: After Adding a Secondary Replica</span></span>  
 <span data-ttu-id="563e8-155">기존 가용성 그룹에 대한 복제본을 추가하려면 다음 단계를 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="563e8-155">To add a replica for an existing availability group, you must perform the following steps:</span></span>  
  
1.  <span data-ttu-id="563e8-156">새 보조 복제본을 호스팅할 서버 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="563e8-156">Connect to the server instance that is going to host the new secondary replica.</span></span>  
  
2.  <span data-ttu-id="563e8-157">새 보조 복제본을 가용성 그룹에 조인합니다.</span><span class="sxs-lookup"><span data-stu-id="563e8-157">Join the new secondary replica to the availability group.</span></span> <span data-ttu-id="563e8-158">자세한 내용은 [가용성 그룹에 보조 복제본 조인&#40;SQL Server&#41;](join-a-secondary-replica-to-an-availability-group-sql-server.md)또는 PowerShell을 사용하여 Always On 가용성 그룹에 보조 데이터베이스를 조인하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="563e8-158">For more information, see [Join a Secondary Replica to an Availability Group &#40;SQL Server&#41;](join-a-secondary-replica-to-an-availability-group-sql-server.md).</span></span>  
  
3.  <span data-ttu-id="563e8-159">가용성 그룹의 각 데이터베이스에 대해 보조 복제본을 호스팅하는 서버 인스턴스에 보조 데이터베이스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="563e8-159">For each database in the availability group, create a secondary database on the server instance that is hosting the secondary replica.</span></span> <span data-ttu-id="563e8-160">자세한 내용은 [가용성 그룹에 대한 보조 데이터베이스 수동 준비&#40;SQL Server&#41;](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md)또는 PowerShell을 사용하여 Always On 가용성 그룹에 보조 데이터베이스를 조인하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="563e8-160">For more information, see [Manually Prepare a Secondary Database for an Availability Group &#40;SQL Server&#41;](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md).</span></span>  
  
4.  <span data-ttu-id="563e8-161">각각의 새로운 보조 데이터베이스를 가용성 그룹에 조인합니다.</span><span class="sxs-lookup"><span data-stu-id="563e8-161">Join each of the new secondary databases to the availability group.</span></span> <span data-ttu-id="563e8-162">자세한 내용은 [가용성 그룹에 보조 데이터베이스 조인&#40;SQL Server&#41;](join-a-secondary-database-to-an-availability-group-sql-server.md)인스턴스에 AlwaysOn 가용성 그룹을 만드는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="563e8-162">For more information, see [Join a Secondary Database to an Availability Group &#40;SQL Server&#41;](join-a-secondary-database-to-an-availability-group-sql-server.md).</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="563e8-163">관련 작업</span><span class="sxs-lookup"><span data-stu-id="563e8-163">Related Tasks</span></span>  
 <span data-ttu-id="563e8-164">**가용성 복제본을 관리하려면**</span><span class="sxs-lookup"><span data-stu-id="563e8-164">**To manage an availability replica**</span></span>  
  
-   [<span data-ttu-id="563e8-165">가용성 그룹에 보조 복제본 조인&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="563e8-165">Join a Secondary Replica to an Availability Group &#40;SQL Server&#41;</span></span>](join-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="563e8-166">가용성 그룹에서 보조 복제본 제거&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="563e8-166">Remove a Secondary Replica from an Availability Group &#40;SQL Server&#41;</span></span>](remove-a-secondary-replica-from-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="563e8-167">가용성 복제본에 대한 읽기 전용 액세스 구성&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="563e8-167">Configure Read-Only Access on an Availability Replica &#40;SQL Server&#41;</span></span>](configure-read-only-access-on-an-availability-replica-sql-server.md)  
  
-   [<span data-ttu-id="563e8-168">가용성 복제본의 가용성 모드 변경&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="563e8-168">Change the Availability Mode of an Availability Replica &#40;SQL Server&#41;</span></span>](change-the-availability-mode-of-an-availability-replica-sql-server.md)  
  
-   [<span data-ttu-id="563e8-169">가용성 복제본의 장애 조치(failover) 모드 변경&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="563e8-169">Change the Failover Mode of an Availability Replica &#40;SQL Server&#41;</span></span>](change-the-failover-mode-of-an-availability-replica-sql-server.md)  
  
-   [<span data-ttu-id="563e8-170">가용성 복제본에 대한 세션 제한 시간 변경&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="563e8-170">Change the Session-Timeout Period for an Availability Replica &#40;SQL Server&#41;</span></span>](change-the-session-timeout-period-for-an-availability-replica-sql-server.md)  
  
-   [<span data-ttu-id="563e8-171">가용성 복제본에 대한 세션 제한 시간 변경&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="563e8-171">Change the Session-Timeout Period for an Availability Replica &#40;SQL Server&#41;</span></span>](change-the-session-timeout-period-for-an-availability-replica-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="563e8-172">참고 항목</span><span class="sxs-lookup"><span data-stu-id="563e8-172">See Also</span></span>  
 <span data-ttu-id="563e8-173">[ALTER AVAILABILITY GROUP&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-availability-group-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="563e8-173">[ALTER AVAILABILITY GROUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-availability-group-transact-sql) </span></span>  
 <span data-ttu-id="563e8-174">[AlwaysOn 가용성 그룹 &#40;SQL Server 개요&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="563e8-174">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="563e8-175">[가용성 그룹의 생성 및 구성&#40;SQL Server&#41;](creation-and-configuration-of-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="563e8-175">[Creation and Configuration of Availability Groups &#40;SQL Server&#41;](creation-and-configuration-of-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="563e8-176">[AlwaysOn 대시보드 &#40;SQL Server Management Studio를 사용&#41;](use-the-always-on-dashboard-sql-server-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="563e8-176">[Use the AlwaysOn Dashboard &#40;SQL Server Management Studio&#41;](use-the-always-on-dashboard-sql-server-management-studio.md) </span></span>  
 [<span data-ttu-id="563e8-177">가용성 그룹 모니터링&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="563e8-177">Monitor Availability Groups &#40;Transact-SQL&#41;</span></span>](monitor-availability-groups-transact-sql.md)  
  
  
