---
title: 가용성 복제본에 백업 구성(SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- backup priority
- backup on secondary replicas
- Availability Groups [SQL Server], availability replicas
- Availability Groups [SQL Server], backup on secondary replicas
- active secondary replicas [SQL Server], backup on
- automated backup preference
- Availability Groups [SQL Server], active secondary replicas
ms.assetid: 74bc40bb-9f57-44e4-8988-1d69c0585eb6
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 91a781d957eb2f5a81d323fc3c65c93e34945c12
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741308"
---
# <a name="configure-backup-on-availability-replicas-sql-server"></a><span data-ttu-id="72c6c-102">가용성 복제본에 백업 구성(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="72c6c-102">Configure Backup on Availability Replicas (SQL Server)</span></span>
  <span data-ttu-id="72c6c-103">이 항목에서는 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]에서 [!INCLUDE[tsql](../../../includes/tsql-md.md)], [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]또는 PowerShell을 사용하여 AlwaysOn 가용성 그룹의 보조 복제본에 백업을 구성하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="72c6c-103">This topic describes how to configure backup on secondary replicas for an AlwaysOn availability group by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)], or PowerShell in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="72c6c-104">보조 복제본에 대 한 백업에 대 한 소개는 [활성 보조: 보조 복제본에 백업 (AlwaysOn 가용성 그룹)](active-secondaries-backup-on-secondary-replicas-always-on-availability-groups.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="72c6c-104">For an introduction to backup on secondary replicas, see [Active Secondaries: Backup on Secondary Replicas (AlwaysOn Availability Groups)](active-secondaries-backup-on-secondary-replicas-always-on-availability-groups.md).</span></span>  
  
 
  

  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="72c6c-105">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="72c6c-105">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="72c6c-106">필수 조건</span><span class="sxs-lookup"><span data-stu-id="72c6c-106">Prerequisites</span></span>  
 <span data-ttu-id="72c6c-107">주 복제본을 호스팅하는 서버 인스턴스에 연결되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="72c6c-107">You must be connected to the server instance that hosts the primary replica.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="72c6c-108">보안</span><span class="sxs-lookup"><span data-stu-id="72c6c-108">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="72c6c-109">권한</span><span class="sxs-lookup"><span data-stu-id="72c6c-109">Permissions</span></span>  
  
|<span data-ttu-id="72c6c-110">Task</span><span class="sxs-lookup"><span data-stu-id="72c6c-110">Task</span></span>|<span data-ttu-id="72c6c-111">사용 권한</span><span class="sxs-lookup"><span data-stu-id="72c6c-111">Permissions</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="72c6c-112">가용성 그룹을 만들 때 보조 복제본에 백업을 구성하려면</span><span class="sxs-lookup"><span data-stu-id="72c6c-112">To configure backup on secondary replicas when creating an availability group</span></span>|<span data-ttu-id="72c6c-113">CREATE AVAILABILITY GROUP 서버 권한, ALTER ANY AVAILABILITY GROUP 권한, CONTROL SERVER 권한 중 하나와 **sysadmin** 고정 서버 역할의 멤버 자격이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="72c6c-113">Requires membership in the **sysadmin** fixed server role and either CREATE AVAILABILITY GROUP server permission, ALTER ANY AVAILABILITY GROUP permission, or CONTROL SERVER permission.</span></span>|  
|<span data-ttu-id="72c6c-114">가용성 그룹 또는 가용성 복제본을 수정하려면</span><span class="sxs-lookup"><span data-stu-id="72c6c-114">To modify an availability group or availability replica</span></span>|<span data-ttu-id="72c6c-115">가용성 그룹에 대한 ALTER AVAILABILITY GROUP 권한, CONTROL AVAILABILITY GROUP 권한, ALTER ANY AVAILABILITY GROUP 권한 또는 CONTROL SERVER 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="72c6c-115">Requires ALTER AVAILABILITY GROUP permission on the availability group, CONTROL AVAILABILITY GROUP permission, ALTER ANY AVAILABILITY GROUP permission, or CONTROL SERVER permission.</span></span>|  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="72c6c-116">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="72c6c-116">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="72c6c-117">**보조 복제본에 백업을 구성하려면**</span><span class="sxs-lookup"><span data-stu-id="72c6c-117">**To configure backup on secondary replicas**</span></span>  
  
1.  <span data-ttu-id="72c6c-118">개체 탐색기에서 주 복제본을 호스팅하는 서버 인스턴스에 연결하고 서버 트리를 확장할 서버 이름을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="72c6c-118">In Object Explorer, connect to the server instance that hosts the primary replica, and click the server name to expand the server tree.</span></span>  
  
2.  <span data-ttu-id="72c6c-119">**AlwaysOn 고가용성** 및 **가용성 그룹** 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="72c6c-119">Expand the **AlwaysOn High Availability** node and the **Availability Groups** node.</span></span>  
  
3.  <span data-ttu-id="72c6c-120">백업 기본 설정을 구성할 가용성 그룹을 클릭하고 **속성** 명령을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="72c6c-120">Click the availability group whose backup preferences you want to configure, and select the **Properties** command.</span></span>  
  
4.  <span data-ttu-id="72c6c-121">**가용성 그룹 속성** 대화 상자에서 **백업 기본 설정** 페이지를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="72c6c-121">In the **Availability Group Properties** dialog box, select **Backup Preferences** page.</span></span>  
  
5.  <span data-ttu-id="72c6c-122">**백업 수행 위치** 패널에서 가용성 그룹의 자동화된 백업 기본 설정을 다음 옵션 중 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="72c6c-122">On the **Where should backups occur?** panel, select the automated backup preference for the availability group, one of:</span></span>  
  
     <span data-ttu-id="72c6c-123">**보조 사용**</span><span class="sxs-lookup"><span data-stu-id="72c6c-123">**Prefer Secondary**</span></span>  
     <span data-ttu-id="72c6c-124">백업이 보조 복제본에서 수행되도록 지정합니다. 주 복제본이 유일한 온라인 복제본인 경우는 예외로,</span><span class="sxs-lookup"><span data-stu-id="72c6c-124">Specifies that backups should occur on a secondary replica except when the primary replica is the only replica online.</span></span> <span data-ttu-id="72c6c-125">이 경우에는 백업이 주 복제본에서 수행되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="72c6c-125">In that case, the backup should occur on the primary replica.</span></span> <span data-ttu-id="72c6c-126">기본 옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="72c6c-126">This is the default option.</span></span>  
  
     <span data-ttu-id="72c6c-127">**보조만**</span><span class="sxs-lookup"><span data-stu-id="72c6c-127">**Secondary only**</span></span>  
     <span data-ttu-id="72c6c-128">백업이 주 복제본에서 수행되지 않도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="72c6c-128">Specifies that backups should never be performed on the primary replica.</span></span> <span data-ttu-id="72c6c-129">주 복제본이 유일한 온라인 복제본인 경우에는 백업이 수행되지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="72c6c-129">If the primary replica is the only replica online, the backup should not occur.</span></span>  
  
     `Primary`  
     <span data-ttu-id="72c6c-130">백업이 항상 주 복제본에서 수행되도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="72c6c-130">Specifies that the backups should always occur on the primary replica.</span></span> <span data-ttu-id="72c6c-131">이 옵션은 백업이 보조 복제본에서 실행될 때 지원되지 않는 차등 백업 만들기와 같은 백업 기능이 필요한 경우에 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="72c6c-131">This option is useful if you need backup features, such as creating differential backups, that are not supported when backup is run on a secondary replica.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="72c6c-132">로그 전달을 사용하여 가용성 그룹의 보조 데이터베이스를 준비하려는 경우 모든 보조 데이터베이스가 준비되고 가용성 그룹에 조인될 때까지 자동화된 백업 기본 설정을 `Primary`로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="72c6c-132">If you plan to use log shipping to prepare any secondary databases for an availability group, set the automated backup preference to `Primary` until all the secondary databases have been prepared and joined to the availability group.</span></span>  
  
     <span data-ttu-id="72c6c-133">**임의의 복제본**</span><span class="sxs-lookup"><span data-stu-id="72c6c-133">**Any Replica**</span></span>  
     <span data-ttu-id="72c6c-134">백업을 수행할 복제본을 선택할 때 백업 작업에서 가용성 복제본의 역할을 무시하도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="72c6c-134">Specifies that you prefer that backup jobs ignore the role of the availability replicas when choosing the replica to perform backups.</span></span> <span data-ttu-id="72c6c-135">백업 작업에서는 각 가용성 복제본의 작동 상태 및 연결 상태와 함께 백업 우선 순위 등의 기타 요인을 평가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="72c6c-135">Note backup jobs might evaluate other factors such as backup priority of each availability replica in combination with its operational state and connected state.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="72c6c-136">자동화된 백업 기본 설정은 적용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="72c6c-136">There is no enforcement of the automated backup preference setting.</span></span> <span data-ttu-id="72c6c-137">이 기본 설정의 해석은 지정된 가용성 그룹의 데이터베이스에 대한 백업 작업으로 스크립팅하는 논리(있는 경우)에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="72c6c-137">The interpretation of this preference depends on the logic, if any, that you script into backup jobs for the databases in a given availability group.</span></span> <span data-ttu-id="72c6c-138">자동화된 백업 기본 설정은 임시 백업에는 영향을 미치지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="72c6c-138">The automated backup preference setting has no impact on ad-hoc backups.</span></span> <span data-ttu-id="72c6c-139">자세한 내용은 이 항목 뒷부분에 있는 [후속 작업: 보조 복제본에 백업을 구성한 후](#FollowUp) 을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="72c6c-139">For more information, see [Follow Up: After Configuring Backup on Secondary Replicas](#FollowUp) later in this topic.</span></span>  
  
6.  <span data-ttu-id="72c6c-140">**복제본 백업 우선 순위** 표를 사용하여 가용성 복제본의 백업 우선 순위를 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="72c6c-140">Use the **Replica backup priorities** grid to change the backup priority of the availability replicas.</span></span> <span data-ttu-id="72c6c-141">이 표는 가용성 그룹에 대한 복제본을 호스팅하는 각 서버 인스턴스의 현재 백업 우선 순위를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="72c6c-141">This grid displays the current backup priority of each server instance that hosts a replica for the availability group.</span></span> <span data-ttu-id="72c6c-142">표 열은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="72c6c-142">The grid columns are as follows:</span></span>  
  
     <span data-ttu-id="72c6c-143">**서버 인스턴스**</span><span class="sxs-lookup"><span data-stu-id="72c6c-143">**Server Instance**</span></span>  
     <span data-ttu-id="72c6c-144">가용성 복제본을 호스팅하는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 의 인스턴스 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="72c6c-144">The name of the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] that hosts the availability replica.</span></span>  
  
     <span data-ttu-id="72c6c-145">**백업 우선 순위(최저 = 1, 최고 = 100)**</span><span class="sxs-lookup"><span data-stu-id="72c6c-145">**Backup Priority (Lowest=1, Highest=100)**</span></span>  
     <span data-ttu-id="72c6c-146">이 복제본에 대한 백업을 수행하기 위한 우선 순위를 지정하며 동일한 가용성 그룹의 다른 복제본을 기준으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="72c6c-146">Specifies your priority for performing backups on this replica relative to the other replicas in the same availability group.</span></span> <span data-ttu-id="72c6c-147">이 값은 0에서 100  사이의 정수입니다.</span><span class="sxs-lookup"><span data-stu-id="72c6c-147">The value is an integer in the range of 0..100.</span></span> <span data-ttu-id="72c6c-148">1은 가장 낮은 우선 순위를 나타내고 100은 가장 높은 우선 순위를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="72c6c-148">1 indicates the lowest priority, and 100 indicates the highest priority.</span></span> <span data-ttu-id="72c6c-149">**백업 우선 순위**가 1이면 현재 사용 가능한 더 높은 우선 순위의 가용성 복제본이 없는 경우에만 해당 가용성 복제본이 백업 수행을 위해 선택됩니다.</span><span class="sxs-lookup"><span data-stu-id="72c6c-149">If **Backup Priority** = 1, the availability replica would be chosen for performing backups only if no higher priority availability replicas are currently available.</span></span>  
  
     <span data-ttu-id="72c6c-150">**복제본 제외**</span><span class="sxs-lookup"><span data-stu-id="72c6c-150">**Exclude Replica**</span></span>  
     <span data-ttu-id="72c6c-151">백업 수행을 위해 이 가용성 백업을 선택하지 않으려는 경우에 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="72c6c-151">Select if you never want this availability replica to be chosen for performing backups.</span></span> <span data-ttu-id="72c6c-152">이 값은 예를 들어 백업을 장애 조치할 대상으로 사용하지 않을 원격 가용성 복제본의 경우에 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="72c6c-152">This is useful, for example, for a remote availability replica to which you never want backups to fail over.</span></span>  
  
7.  <span data-ttu-id="72c6c-153">변경 내용을 커밋하려면 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="72c6c-153">To commit your changes, click **OK**.</span></span>  
  
 <span data-ttu-id="72c6c-154">**백업 기본 설정 페이지에 액세스하는 다른 방법**</span><span class="sxs-lookup"><span data-stu-id="72c6c-154">**Alternative ways to access the Backup Preferences page**</span></span>  
  
-   [<span data-ttu-id="72c6c-155">새 가용성 그룹 대화 상자 사용&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="72c6c-155">Use the New Availability Group Dialog Box &#40;SQL Server Management Studio&#41;</span></span>](use-the-new-availability-group-dialog-box-sql-server-management-studio.md)  
  
-   [<span data-ttu-id="72c6c-156">가용성 그룹에 복제본 추가 마법사 사용&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="72c6c-156">Use the Add Replica to Availability Group Wizard &#40;SQL Server Management Studio&#41;</span></span>](use-the-add-replica-to-availability-group-wizard-sql-server-management-studio.md)  
  
-   [<span data-ttu-id="72c6c-157">새 가용성 그룹 대화 상자 사용&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="72c6c-157">Use the New Availability Group Dialog Box &#40;SQL Server Management Studio&#41;</span></span>](use-the-new-availability-group-dialog-box-sql-server-management-studio.md)  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="72c6c-158">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="72c6c-158">Using Transact-SQL</span></span>  
 <span data-ttu-id="72c6c-159">**보조 복제본에 백업을 구성하려면**</span><span class="sxs-lookup"><span data-stu-id="72c6c-159">**To configure backup on secondary replicas**</span></span>  
  
1.  <span data-ttu-id="72c6c-160">주 복제본을 호스팅하는 서버 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="72c6c-160">Connect to the server instance that hosts the primary replica.</span></span>  
  
2.  <span data-ttu-id="72c6c-161">새 가용성 그룹을 만들려는 경우 [CREATE AVAILABILITY GROUP&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-availability-group-transact-sql)을 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="72c6c-161">For a new availability group, use the [CREATE AVAILABILITY GROUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-availability-group-transact-sql) statement.</span></span> <span data-ttu-id="72c6c-162">기존 가용성 그룹을 수정하려는 경우 [ALTER AVAILABILITY GROUP&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-availability-group-transact-sql) 문을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="72c6c-162">If you are modifying an existing availability group, use the [ALTER AVAILABILITY GROUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-availability-group-transact-sql) statement.</span></span>  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a> <span data-ttu-id="72c6c-163">PowerShell 사용</span><span class="sxs-lookup"><span data-stu-id="72c6c-163">Using PowerShell</span></span>  

### <a name="to-configure-backup-on-secondary-replicas"></a><span data-ttu-id="72c6c-164">보조 복제본에 백업을 구성하려면</span><span class="sxs-lookup"><span data-stu-id="72c6c-164">To configure backup on secondary replicas</span></span>
  
1.  <span data-ttu-id="72c6c-165">기본값(`cd`)을 주 복제본을 호스팅하는 서버 인스턴스로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="72c6c-165">Set default (`cd`) to the server instance that hosts the primary replica.</span></span>  
  
2.  <span data-ttu-id="72c6c-166">필요한 경우 추가하거나 수정할 각 가용성 복제본의 백업 우선 순위를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="72c6c-166">Optionally, configure the backup priority of each availability replica that you are adding or modifying.</span></span> <span data-ttu-id="72c6c-167">이 우선 순위는 어느 복제본이 가용성 그룹의 데이터베이스에서 자동 백업 요청을 지원해야 하는지를 결정하기 위해(우선 순위가 가장 높은 복제본이 선택됨) 주 복제본을 호스팅하는 서버 인스턴스가 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="72c6c-167">This priority is used by the server instance that hosts the primary replica to decide which replica should service an automated backup request on a database in the availability group (the replica with highest priority is chosen).</span></span> <span data-ttu-id="72c6c-168">이 우선 순위는 1부터 100까지의 임의의 숫자일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="72c6c-168">This priority can be any number between 0 and 100, inclusive.</span></span> <span data-ttu-id="72c6c-169">우선 순위 0은 백업 요청 지원을 위한 후보로 해당 복제본을 고려하지 않아야 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="72c6c-169">A priority of 0 indicates that the replica should not be considered as a candidate for servicing backup requests.</span></span>  <span data-ttu-id="72c6c-170">기본 설정은 50입니다.</span><span class="sxs-lookup"><span data-stu-id="72c6c-170">The default setting is 50.</span></span>  
  
     <span data-ttu-id="72c6c-171">가용성 그룹에 가용성 복제본을 추가하는 경우 `New-SqlAvailabilityReplica` cmdlet을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="72c6c-171">When adding an availability replica to an availability group, use the `New-SqlAvailabilityReplica` cmdlet.</span></span> <span data-ttu-id="72c6c-172">기존 가용성 복제본을 수정하는 경우 `Set-SqlAvailabilityReplica` cmdlet을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="72c6c-172">When modifying an existing availability replica, use the `Set-SqlAvailabilityReplica` cmdlet.</span></span> <span data-ttu-id="72c6c-173">두 경우 모두 `BackupPriority` *n* 매개 변수를 지정 합니다. 여기서 *n* 은 0에서 100 사이의 값입니다.</span><span class="sxs-lookup"><span data-stu-id="72c6c-173">In either case, specify the `BackupPriority`*n* parameter, where *n* is a value from 0 to 100.</span></span>  
  
     <span data-ttu-id="72c6c-174">예를 들어 다음 명령은 가용성 복제본 `MyReplica`의 백업 우선 순위를 `60`으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="72c6c-174">For example, the following command sets the backup priority of the availability replica `MyReplica` to `60`.</span></span>  
  
    ```powershell
    Set-SqlAvailabilityReplica -BackupPriority 60 -Path SQLSERVER:\Sql\Computer\Instance\AvailabilityGroups\MyAg\AvailabilityReplicas\MyReplica  
    ```  
  
3.  <span data-ttu-id="72c6c-175">필요한 경우 만들거나 수정하는 가용성 그룹에 대해 자동화된 백업 기본 설정을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="72c6c-175">Optionally, configure the automated backup preference for the availability group that you are creating  or modifying.</span></span> <span data-ttu-id="72c6c-176">이 기본 설정은 백업을 수행할 위치를 선택할 때 백업 작업에서 주 복제본을 평가하는 방식을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="72c6c-176">This preference indicates how a backup job should evaluate the primary replica when choosing where to perform backups.</span></span> <span data-ttu-id="72c6c-177">기본 설정은 보조 복제본을 사용하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="72c6c-177">The default setting is to prefer secondary replicas.</span></span>  
  
     <span data-ttu-id="72c6c-178">가용성 그룹을 만드는 경우 `New-SqlAvailabilityGroup` cmdlet을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="72c6c-178">When creating an availability group, use the `New-SqlAvailabilityGroup` cmdlet.</span></span> <span data-ttu-id="72c6c-179">기존 가용성 그룹을 수정하는 경우 `Set-SqlAvailabilityGroup` cmdlet을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="72c6c-179">When modifying an existing availability group, use the `Set-SqlAvailabilityGroup` cmdlet.</span></span> <span data-ttu-id="72c6c-180">두 경우 모두 `AutomatedBackupPreference` 매개 변수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="72c6c-180">In either case, specify the `AutomatedBackupPreference` parameter.</span></span>  
  
     <span data-ttu-id="72c6c-181">각 항목이 나타내는 의미는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="72c6c-181">where,</span></span>  
  
     `Primary`  
     <span data-ttu-id="72c6c-182">백업이 항상 주 복제본에서 수행되도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="72c6c-182">Specifies that the backups should always occur on the primary replica.</span></span> <span data-ttu-id="72c6c-183">이 옵션은 백업이 보조 복제본에서 실행될 때 지원되지 않는 차등 백업 만들기와 같은 백업 기능이 필요한 경우에 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="72c6c-183">This option is useful if you need backup features, such as creating differential backups, that are not supported when backup is run on a secondary replica.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="72c6c-184">로그 전달을 사용하여 가용성 그룹의 보조 데이터베이스를 준비하려는 경우 모든 보조 데이터베이스가 준비되고 가용성 그룹에 조인될 때까지 자동화된 백업 기본 설정을 `Primary`로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="72c6c-184">If you plan to use log shipping to prepare any secondary databases for an availability group, set the automated backup preference to `Primary` until all the secondary databases have been prepared and joined to the availability group.</span></span>  
  
     `SecondaryOnly`  
     <span data-ttu-id="72c6c-185">백업이 주 복제본에서 수행되지 않도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="72c6c-185">Specifies that backups should never be performed on the primary replica.</span></span> <span data-ttu-id="72c6c-186">주 복제본이 유일한 온라인 복제본인 경우에는 백업이 수행되지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="72c6c-186">If the primary replica is the only replica online, the backup should not occur.</span></span>  
  
     `Secondary`  
     <span data-ttu-id="72c6c-187">백업이 보조 복제본에서 수행되도록 지정합니다. 주 복제본이 유일한 온라인 복제본인 경우는 예외로,</span><span class="sxs-lookup"><span data-stu-id="72c6c-187">Specifies that backups should occur on a secondary replica except when the primary replica is the only replica online.</span></span> <span data-ttu-id="72c6c-188">이 경우에는 백업이 주 복제본에서 수행되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="72c6c-188">In that case, the backup should occur on the primary replica.</span></span> <span data-ttu-id="72c6c-189">기본 동작입니다.</span><span class="sxs-lookup"><span data-stu-id="72c6c-189">This is the default behavior.</span></span>  
  
     `None`  
     <span data-ttu-id="72c6c-190">백업을 수행할 복제본을 선택할 때 백업 작업에서 가용성 복제본의 역할을 무시하도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="72c6c-190">Specifies that you prefer that backup jobs ignore the role of the availability replicas when choosing the replica to perform backups.</span></span> <span data-ttu-id="72c6c-191">백업 작업에서는 각 가용성 복제본의 작동 상태 및 연결 상태와 함께 백업 우선 순위 등의 기타 요인을 평가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="72c6c-191">Note backup jobs might evaluate other factors such as backup priority of each availability replica in combination with its operational state and  connected state.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="72c6c-192">`AutomatedBackupPreference`는 적용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="72c6c-192">There is no enforcement of `AutomatedBackupPreference`.</span></span> <span data-ttu-id="72c6c-193">이 기본 설정의 해석은 지정된 가용성 그룹의 데이터베이스에 대한 백업 작업으로 스크립팅하는 논리(있는 경우)에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="72c6c-193">The interpretation of this preference depends on the logic, if any, that you script into backup jobs for the databases in a given availability group.</span></span> <span data-ttu-id="72c6c-194">자동화된 백업 기본 설정은 임시 백업에는 영향을 미치지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="72c6c-194">The automated backup preference setting has no impact on ad-hoc backups.</span></span> <span data-ttu-id="72c6c-195">자세한 내용은 이 항목 뒷부분에 있는 [후속 작업: 보조 복제본에 백업을 구성한 후](#FollowUp) 을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="72c6c-195">For more information, see [Follow Up: After Configuring Backup on Secondary Replicas](#FollowUp) later in this topic.</span></span>  
  
     <span data-ttu-id="72c6c-196">예를 들어 다음 명령은 가용성 그룹 `MyAg`의 `AutomatedBackupPreference` 속성을 `SecondaryOnly`로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="72c6c-196">For example, the following command sets the `AutomatedBackupPreference` property on the availability group `MyAg` to `SecondaryOnly`.</span></span> <span data-ttu-id="72c6c-197">주 복제본에서는 이 가용성 그룹의 데이터베이스 자동 백업이 절대 발생하지 않으며 대신 백업 우선 순위 설정 값이 가장 높은 보조 복제본으로 백업이 리디렉션됩니다.</span><span class="sxs-lookup"><span data-stu-id="72c6c-197">Automated backups of databases in this availability group will never occur on the primary replica, but will be redirected to the secondary replica with the highest backup priority setting.</span></span>  
  
    ```powershell
    Set-SqlAvailabilityGroup -Path SQLSERVER:\Sql\PrimaryServer\InstanceName\AvailabilityGroups\MyAg `  
     -AutomatedBackupPreference SecondaryOnly  
    ```  
  
> [!NOTE]  
>  <span data-ttu-id="72c6c-198">cmdlet의 구문을 보려면 `Get-Help` PowerShell 환경에서 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] cmdlet을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="72c6c-198">To view the syntax of a cmdlet, use the `Get-Help` cmdlet in the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell environment.</span></span> <span data-ttu-id="72c6c-199">자세한 내용은 [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="72c6c-199">For more information, see [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).</span></span>  
  
<span data-ttu-id="72c6c-200">SQL Server PowerShell 공급자를 설정 하 고 사용 하려면 [SQL Server PowerShell 공급자](../../../powershell/sql-server-powershell-provider.md) 를 참조 하 고 [SQL Server PowerShell 도움을 받으세요](../../../powershell/sql-server-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="72c6c-200">To set up and use the SQL Server PowerShell provider, see [SQL Server PowerShell Provider](../../../powershell/sql-server-powershell-provider.md) and [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).</span></span>
  
##  <a name="follow-up-after-configuring-backup-on-secondary-replicas"></a><a name="FollowUp"></a><span data-ttu-id="72c6c-201">후속 작업: 보조 복제본에 백업을 구성한 후</span><span class="sxs-lookup"><span data-stu-id="72c6c-201">Follow Up: After Configuring Backup on Secondary Replicas</span></span>  
 <span data-ttu-id="72c6c-202">지정된 가용성 그룹에 대해 자동화된 백업 기본 설정을 고려하도록 하려면 백업 우선 순위가 0보다 큰(>0) 가용성 복제본을 호스팅하는 각 서버 인스턴스에서 가용성 그룹의 데이터베이스에 대한 백업 작업을 스크립팅해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="72c6c-202">To take the automated backup preference into account for a given availability group, on each server instance that hosts an availability replica whose backup priority is greater than zero (>0), you need to script backup jobs for the databases in the availability group.</span></span> <span data-ttu-id="72c6c-203">현재 복제본이 기본 백업 복제본인지 여부를 확인하려면 백업 스크립트에서 [sys.fn_hadr_backup_is_preferred_replica](/sql/relational-databases/system-functions/sys-fn-hadr-backup-is-preferred-replica-transact-sql) 함수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="72c6c-203">To determine whether the current replica is the preferred backup replica, use the [sys.fn_hadr_backup_is_preferred_replica](/sql/relational-databases/system-functions/sys-fn-hadr-backup-is-preferred-replica-transact-sql) function in your backup script.</span></span> <span data-ttu-id="72c6c-204">현재 서버 인스턴스가 호스팅하는 가용성 복제본이 백업에 대한 선호 복제본인 경우 이 함수가 1을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="72c6c-204">If the availability replica that is hosted by the current server instance is the preferred replica for backups, this function returns 1.</span></span> <span data-ttu-id="72c6c-205">그렇지 않으면 함수가 0을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="72c6c-205">If not, the function returns 0.</span></span> <span data-ttu-id="72c6c-206">각 가용성 복제본에서 이 함수를 쿼리하는 간단한 스크립트를 실행하여 지정된 백업 작업을 실행할 복제본을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="72c6c-206">By running a simple script on each availability replica that queries this function, you can determine which replica should run a given backup job.</span></span> <span data-ttu-id="72c6c-207">예를 들어 백업 작업 스크립트의 일반적인 코드 조각은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="72c6c-207">For example, a typical snippet of a backup-job script would look like:</span></span>  
  
```  
IF (NOT sys.fn_hadr_backup_is_preferred_replica(@DBNAME))  
BEGIN  
      Select 'This is not the preferred replica, exiting with success';  
      RETURN 0 - This is a normal, expected condition, so the script returns success  
END  
BACKUP DATABASE @DBNAME TO DISK=<disk>  
   WITH COPY_ONLY;  
```  
  
 <span data-ttu-id="72c6c-208">이 논리를 사용하여 백업 작업을 스크립팅하면 동일한 일정으로 모든 가용성 복제본에 대해 실행할 작업을 예약할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="72c6c-208">Scripting a backup job with this logic enables you to schedule the job to run on every availability replica on the same schedule.</span></span> <span data-ttu-id="72c6c-209">이러한 각 작업은 동일한 데이터를 조사하여 실행해야 하는 작업을 확인하므로 예약된 작업 중 하나만이 실제로 백업 단계로 진행됩니다.</span><span class="sxs-lookup"><span data-stu-id="72c6c-209">Each of these jobs looks at the same data to determine which job should run, so only one of the scheduled job actually proceeds to the backup stage.</span></span>  <span data-ttu-id="72c6c-210">장애 조치(Failover)의 경우 스크립트나 작업을 수정할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="72c6c-210">In the event of a failover, none of the scripts or jobs needs to be modified.</span></span> <span data-ttu-id="72c6c-211">가용성 복제본을 추가하도록 가용성 그룹을 다시 구성한 경우 백업 작업을 관리하려면 백업 작업을 복사하거나 예약하기만 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="72c6c-211">Also, if you reconfigure an availability group to add an availability replica, managing the backup job requires simply copying or scheduling the backup job.</span></span> <span data-ttu-id="72c6c-212">가용성 복제본을 제거한 경우 해당 복제본을 호스팅하는 서버 인스턴스에서 백업 작업을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="72c6c-212">If you remove an availability replica, simply delete the backup job from the server instance that hosted that replica.</span></span>  
  
> [!TIP]  
>  <span data-ttu-id="72c6c-213">[유지 관리 계획 마법사](../../../relational-databases/maintenance-plans/use-the-maintenance-plan-wizard.md)를 사용하여 지정된 백업 작업을 만드는 경우 해당 작업에는 **sys.fn_hadr_backup_is_preferred_replica** 함수를 호출하고 확인하는 스크립팅 논리가 자동으로 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="72c6c-213">If you use the[Maintenance Plan Wizard](../../../relational-databases/maintenance-plans/use-the-maintenance-plan-wizard.md)to create a given backup job, the job will automatically include the scripting logic that calls and checks the **sys.fn_hadr_backup_is_preferred_replica** function.</span></span> <span data-ttu-id="72c6c-214">그러나 백업 작업은 “선호 복제본이 아닙니다...”라는 메시지를 반환하지 않습니다. 가용성 그룹의 가용성 복제본을 호스트하는 각 서버 인스턴스에서 각 가용성 데이터베이스에 대한 작업을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="72c6c-214">However, the backup job will not return the "This is not the preferred replica..." message.Be sure to create the job(s) for each availability database on every server instance that hosts an availability replica for the availability group.</span></span>  
  
##  <a name="to-obtain-information-about-backup-preference-settings"></a><a name="ForInfoAboutBuPref"></a><span data-ttu-id="72c6c-215">백업 기본 설정에 대 한 정보를 가져오려면</span><span class="sxs-lookup"><span data-stu-id="72c6c-215">To Obtain Information About Backup Preference Settings</span></span>  
 <span data-ttu-id="72c6c-216">다음은 보조 복제본에서의 백업과 관련된 정보를 가져오는 데 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="72c6c-216">The following are useful for obtaining information that is relevant for backup on secondary.</span></span>  
  
|<span data-ttu-id="72c6c-217">View</span><span class="sxs-lookup"><span data-stu-id="72c6c-217">View</span></span>|<span data-ttu-id="72c6c-218">정보</span><span class="sxs-lookup"><span data-stu-id="72c6c-218">Information</span></span>|<span data-ttu-id="72c6c-219">관련 열</span><span class="sxs-lookup"><span data-stu-id="72c6c-219">Relevant Columns</span></span>|  
|----------|-----------------|----------------------|  
|[<span data-ttu-id="72c6c-220">sys.fn_hadr_backup_is_preferred_replica</span><span class="sxs-lookup"><span data-stu-id="72c6c-220">sys.fn_hadr_backup_is_preferred_replica</span></span>](/sql/relational-databases/system-functions/sys-fn-hadr-backup-is-preferred-replica-transact-sql)|<span data-ttu-id="72c6c-221">현재 복제본이 기본 백업 복제본인지 여부</span><span class="sxs-lookup"><span data-stu-id="72c6c-221">Is the current replica the preferred backup replica?</span></span>|<span data-ttu-id="72c6c-222">해당 사항 없음.</span><span class="sxs-lookup"><span data-stu-id="72c6c-222">Not applicable.</span></span>|  
|[<span data-ttu-id="72c6c-223">sys.availability_groups</span><span class="sxs-lookup"><span data-stu-id="72c6c-223">sys.availability_groups</span></span>](/sql/relational-databases/system-catalog-views/sys-availability-groups-transact-sql)|<span data-ttu-id="72c6c-224">자동화된 백업 기본 설정</span><span class="sxs-lookup"><span data-stu-id="72c6c-224">Automated backup preference</span></span>|<span data-ttu-id="72c6c-225">**automated_backup_preference**</span><span class="sxs-lookup"><span data-stu-id="72c6c-225">**automated_backup_preference**</span></span><br /><br /> <span data-ttu-id="72c6c-226">**automated_backup_preference_desc**</span><span class="sxs-lookup"><span data-stu-id="72c6c-226">**automated_backup_preference_desc**</span></span>|  
|[<span data-ttu-id="72c6c-227">sys.availability_replicas</span><span class="sxs-lookup"><span data-stu-id="72c6c-227">sys.availability_replicas</span></span>](/sql/relational-databases/system-catalog-views/sys-availability-replicas-transact-sql)|<span data-ttu-id="72c6c-228">지정된 가용성 복제본의 백업 우선 순위</span><span class="sxs-lookup"><span data-stu-id="72c6c-228">Backup priority of a given availability replica</span></span>|<span data-ttu-id="72c6c-229">**backup_priority**</span><span class="sxs-lookup"><span data-stu-id="72c6c-229">**backup_priority**</span></span>|  
|[<span data-ttu-id="72c6c-230">sys.dm_hadr_availability_replica_states</span><span class="sxs-lookup"><span data-stu-id="72c6c-230">sys.dm_hadr_availability_replica_states</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-availability-replica-states-transact-sql)|<span data-ttu-id="72c6c-231">복제본이 서버 인스턴스의 로컬 복제본인지 여부</span><span class="sxs-lookup"><span data-stu-id="72c6c-231">Is replica local to the server instance?</span></span><br /><br /> <span data-ttu-id="72c6c-232">현재 역할</span><span class="sxs-lookup"><span data-stu-id="72c6c-232">Current role</span></span><br /><br /> <span data-ttu-id="72c6c-233">작동 상태</span><span class="sxs-lookup"><span data-stu-id="72c6c-233">Operational state</span></span><br /><br /> <span data-ttu-id="72c6c-234">연결 상태</span><span class="sxs-lookup"><span data-stu-id="72c6c-234">Connected state</span></span><br /><br /> <span data-ttu-id="72c6c-235">가용성 복제본의 동기화 상태</span><span class="sxs-lookup"><span data-stu-id="72c6c-235">Synchronization health of an availability replica</span></span>|<span data-ttu-id="72c6c-236">**is_local**</span><span class="sxs-lookup"><span data-stu-id="72c6c-236">**is_local**</span></span><br /><br /> <span data-ttu-id="72c6c-237">**role**, **role_desc**</span><span class="sxs-lookup"><span data-stu-id="72c6c-237">**role**, **role_desc**</span></span><br /><br /> <span data-ttu-id="72c6c-238">**operational_state**, **operational_state_desc**</span><span class="sxs-lookup"><span data-stu-id="72c6c-238">**operational_state**, **operational_state_desc**</span></span><br /><br /> <span data-ttu-id="72c6c-239">**connected_state**, **connected_state_desc**</span><span class="sxs-lookup"><span data-stu-id="72c6c-239">**connected_state**, **connected_state_desc**</span></span><br /><br /> <span data-ttu-id="72c6c-240">**synchronization_health**, **synchronization_health_desc**</span><span class="sxs-lookup"><span data-stu-id="72c6c-240">**synchronization_health**, **synchronization_health_desc**</span></span>|  
  
##  <a name="related-content"></a><a name="RelatedContent"></a> <span data-ttu-id="72c6c-241">관련 내용</span><span class="sxs-lookup"><span data-stu-id="72c6c-241">Related Content</span></span>  
  
-   [<span data-ttu-id="72c6c-242">고가용성 및 재해 복구를 위한 Microsoft SQL Server AlwaysOn 솔루션 가이드</span><span class="sxs-lookup"><span data-stu-id="72c6c-242">Microsoft SQL Server AlwaysOn Solutions Guide for High Availability and Disaster Recovery</span></span>](https://go.microsoft.com/fwlink/?LinkId=227600)  
  
-   [<span data-ttu-id="72c6c-243">SQL Server AlwaysOn 팀 블로그: 공식 SQL Server AlwaysOn 팀 블로그</span><span class="sxs-lookup"><span data-stu-id="72c6c-243">SQL Server AlwaysOn Team Blog: The official SQL Server AlwaysOn Team Blog</span></span>](https://blogs.msdn.com/b/sqlalwayson/)  
  
## <a name="see-also"></a><span data-ttu-id="72c6c-244">참고 항목</span><span class="sxs-lookup"><span data-stu-id="72c6c-244">See Also</span></span>  
 <span data-ttu-id="72c6c-245">[AlwaysOn 가용성 그룹 &#40;SQL Server 개요&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="72c6c-245">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 [<span data-ttu-id="72c6c-246">활성 보조: 보조 복제본에 백업(AlwaysOn 가용성 그룹)</span><span class="sxs-lookup"><span data-stu-id="72c6c-246">Active Secondaries: Backup on Secondary Replicas (AlwaysOn Availability Groups)</span></span>](active-secondaries-backup-on-secondary-replicas-always-on-availability-groups.md) 
