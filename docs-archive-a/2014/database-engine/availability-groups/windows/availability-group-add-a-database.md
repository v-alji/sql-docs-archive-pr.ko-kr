---
title: 가용성 그룹에 데이터베이스 추가(SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- primary databases [SQL Server], in availability group
- Availability Groups [SQL Server], configuring
- Availability Groups [SQL Server], databases
ms.assetid: 2a54eef8-9e8e-4e04-909c-6970112d55cc
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 0907cf711cac65ad77a8948841d92705fdc1eac9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646676"
---
# <a name="add-a-database-to-an-availability-group-sql-server"></a><span data-ttu-id="99796-102">가용성 그룹에 데이터베이스 추가(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="99796-102">Add a Database to an Availability Group (SQL Server)</span></span>
  <span data-ttu-id="99796-103">이 항목에서는 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)]또는 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]의 PowerShell을 사용하여 AlwaysOn 가용성 그룹에 데이터베이스를 추가하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="99796-103">This topic describes how to add a database to an AlwaysOn availability group by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)], or PowerShell in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span>  
  
-   <span data-ttu-id="99796-104">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="99796-104">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="99796-105">사전 요구 사항 및 제한 사항</span><span class="sxs-lookup"><span data-stu-id="99796-105">Prerequisites and Restrictions</span></span>](#Prerequisites)  
  
     [<span data-ttu-id="99796-106">권한</span><span class="sxs-lookup"><span data-stu-id="99796-106">Permissions</span></span>](#Permissions)  
  
-   <span data-ttu-id="99796-107">**가용성 그룹에 데이터베이스를 추가하려면:**</span><span class="sxs-lookup"><span data-stu-id="99796-107">**To add a database to an availability group, using:**</span></span>  
  
     [<span data-ttu-id="99796-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="99796-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="99796-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="99796-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
     [<span data-ttu-id="99796-110">PowerShell</span><span class="sxs-lookup"><span data-stu-id="99796-110">PowerShell</span></span>](#PowerShellProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="99796-111">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="99796-111">Before You Begin</span></span>  
  
###  <a name="prerequisites-and-restrictions"></a><a name="Prerequisites"></a> <span data-ttu-id="99796-112">사전 요구 사항 및 제한 사항</span><span class="sxs-lookup"><span data-stu-id="99796-112">Prerequisites and Restrictions</span></span>  
  
-   <span data-ttu-id="99796-113">주 복제본을 호스팅하는 서버 인스턴스에 연결되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="99796-113">You must be connected to the server instance that hosts the primary replica.</span></span>  
  
-   <span data-ttu-id="99796-114">데이터베이스는 주 복제본을 호스팅하는 서버 인스턴스에 있어야 하며 가용성 데이터베이스에 대한 사전 요구 사항과 제한 사항을 준수해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="99796-114">The database must reside on the server instance that hosts the primary replica and comply with the prerequisites and restrictions for availability databases.</span></span> <span data-ttu-id="99796-115">자세한 내용은 [AlwaysOn 가용성 그룹에 대한 필수 조건, 제한 사항 및 권장 사항&#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="99796-115">For more information, see [Prerequisites, Restrictions, and Recommendations for AlwaysOn Availability Groups &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="99796-116">보안</span><span class="sxs-lookup"><span data-stu-id="99796-116">Security</span></span>  
  
###  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="99796-117">권한</span><span class="sxs-lookup"><span data-stu-id="99796-117">Permissions</span></span>  
 <span data-ttu-id="99796-118">가용성 그룹에 대한 ALTER AVAILABILITY GROUP 권한, CONTROL AVAILABILITY GROUP 권한, ALTER ANY AVAILABILITY GROUP 권한 또는 CONTROL SERVER 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="99796-118">Requires ALTER AVAILABILITY GROUP permission on the availability group, CONTROL AVAILABILITY GROUP permission, ALTER ANY AVAILABILITY GROUP permission, or CONTROL SERVER permission.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="99796-119">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="99796-119">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="99796-120">**가용성 그룹에 데이터베이스를 추가하려면**</span><span class="sxs-lookup"><span data-stu-id="99796-120">**To add a database to an availability group**</span></span>  
  
1.  <span data-ttu-id="99796-121">개체 탐색기에서 주 복제본을 호스팅하는 서버 인스턴스에 연결하고 서버 트리를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="99796-121">In Object Explorer, connect to the server instance that hosts the primary replica, and expand the server tree.</span></span>  
  
2.  <span data-ttu-id="99796-122">**AlwaysOn 고가용성** 및 **가용성 그룹** 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="99796-122">Expand the **AlwaysOn High Availability** node and the **Availability Groups** node.</span></span>  
  
3.  <span data-ttu-id="99796-123">가용성 그룹을 마우스 오른쪽 단추로 클릭하고 다음 명령 중 하나를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="99796-123">Right-click the availability group, and select one of the following commands:</span></span>  
  
    -   <span data-ttu-id="99796-124">가용성 그룹에 데이터베이스 추가 마법사를 시작하려면 **데이터베이스 추가** 명령을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="99796-124">To launch the Add Database to Availability Group Wizard, select the **Add Database** command.</span></span> <span data-ttu-id="99796-125">자세한 내용은 [가용성 그룹에 데이터베이스 추가 마법사 사용&#40;SQL Server Management Studio&#41;](availability-group-add-database-to-group-wizard.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="99796-125">For more information, see [Use the Add Database to Availability Group Wizard &#40;SQL Server Management Studio&#41;](availability-group-add-database-to-group-wizard.md).</span></span>  
  
    -   <span data-ttu-id="99796-126">**가용성 그룹 속성** 대화 상자에서 데이터베이스를 지정하여 하나 이상의 데이터베이스를 추가하려면 **속성** 명령을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="99796-126">To add one or more databases by specifying them in the **Availability Group Properties** dialog box, select the **Properties** command.</span></span> <span data-ttu-id="99796-127">데이터베이스를 추가하는 단계는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="99796-127">The steps for adding a database are as follows:</span></span>  
  
        1.  <span data-ttu-id="99796-128">**가용성 데이터베이스** 창에서 **추가** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="99796-128">In the **Availability Databases** pane, click the **Add** button.</span></span> <span data-ttu-id="99796-129">그러면 빈 데이터베이스 필드가 만들어지고 선택됩니다.</span><span class="sxs-lookup"><span data-stu-id="99796-129">This creates and selects a blank database field.</span></span>  
  
        2.  <span data-ttu-id="99796-130">가용성 데이터베이스 선행 조건을 충족하는 데이터베이스의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="99796-130">Enter the name of a database that meets the availability-databases prerequisites.</span></span>  
  
         <span data-ttu-id="99796-131">다른 데이터베이스를 추가하려면 위의 단계를 반복합니다.</span><span class="sxs-lookup"><span data-stu-id="99796-131">To add another database, repeat the preceding steps.</span></span> <span data-ttu-id="99796-132">데이터베이스 지정을 마치면 **확인** 을 클릭하여 작업을 완료합니다.</span><span class="sxs-lookup"><span data-stu-id="99796-132">When you are done specifying databases, click **OK** to complete the operation.</span></span>  
  
         <span data-ttu-id="99796-133">**가용성 그룹 속성** 대화 상자를 사용하여 가용성 그룹에 데이터베이스를 추가한 후에는 보조 복제본을 호스팅하는 각 서버 인스턴스에서 해당 보조 데이터베이스를 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="99796-133">After you use the **Availability Group Properties** dialog box to add a database to an availability group, you need to configure the corresponding secondary database on each server instance that hosts a secondary replica.</span></span> <span data-ttu-id="99796-134">자세한 내용은 [AlwaysOn 보조 데이터베이스에서 데이터 이동 시작&#40;SQL Server&#41;](start-data-movement-on-an-always-on-secondary-database-sql-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="99796-134">For more information, see [Start Data Movement on an AlwaysOn Secondary Database &#40;SQL Server&#41;](start-data-movement-on-an-always-on-secondary-database-sql-server.md).</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="99796-135">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="99796-135">Using Transact-SQL</span></span>  
 <span data-ttu-id="99796-136">**가용성 그룹에 데이터베이스를 추가하려면**</span><span class="sxs-lookup"><span data-stu-id="99796-136">**To add a database to an availability group**</span></span>  
  
1.  <span data-ttu-id="99796-137">주 복제본을 호스팅하는 서버 인스턴스를 호스팅하는 서버 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="99796-137">Connect to the server instance that hosts the server instance that hosts the primary replica.</span></span>  
  
2.  <span data-ttu-id="99796-138">다음과 같은 [ALTER AVAILABILITY GROUP](/sql/t-sql/statements/alter-availability-group-transact-sql) 문을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="99796-138">Use the [ALTER AVAILABILITY GROUP](/sql/t-sql/statements/alter-availability-group-transact-sql) statement, as follows:</span></span>  
  
     <span data-ttu-id="99796-139">ALTER AVAILABILITY GROUP *group_name* ADD DATABASE *database_name* [,...*n*]</span><span class="sxs-lookup"><span data-stu-id="99796-139">ALTER AVAILABILITY GROUP *group_name* ADD DATABASE *database_name* [,...*n*]</span></span>  
  
     <span data-ttu-id="99796-140">여기서 *group_name* 은 가용성 그룹의 이름이고, *database_name* 은 그룹에 추가할 데이터베이스의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="99796-140">where *group_name* is the name of the availability group and *database_name* is the name of a database to be added to the group.</span></span>  
  
     <span data-ttu-id="99796-141">다음 예에서는 *MyDb3* 데이터베이스를 *MyAG* 가용성 그룹에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="99796-141">The following example adds the *MyDb3* database to the *MyAG* availability group.</span></span>  
  
    ```  
    -- Connect to the server instance that hosts the primary replica.  
    -- Add an existing database to the availability group.  
    ALTER AVAILABILITY GROUP MyAG ADD DATABASE MyDb3;  
    GO  
    ```  
  
3.  <span data-ttu-id="99796-142">가용성 그룹에 데이터베이스를 추가한 후에는 보조 복제본을 호스팅하는 각 서버 인스턴스에서 해당 보조 데이터베이스를 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="99796-142">After you add a database to an availability group, you need to configure the corresponding secondary database on each server instance that hosts a secondary replica.</span></span> <span data-ttu-id="99796-143">자세한 내용은 [AlwaysOn 보조 데이터베이스에서 데이터 이동 시작&#40;SQL Server&#41;](start-data-movement-on-an-always-on-secondary-database-sql-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="99796-143">For more information, see [Start Data Movement on an AlwaysOn Secondary Database &#40;SQL Server&#41;](start-data-movement-on-an-always-on-secondary-database-sql-server.md).</span></span>  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a> <span data-ttu-id="99796-144">PowerShell 사용</span><span class="sxs-lookup"><span data-stu-id="99796-144">Using PowerShell</span></span>  
 <span data-ttu-id="99796-145">**가용성 그룹에 데이터베이스를 추가하려면**</span><span class="sxs-lookup"><span data-stu-id="99796-145">**To add a database to an availability group**</span></span>  
  
1.  <span data-ttu-id="99796-146">주 복제본을 호스팅하는 서버 인스턴스로 디렉터리를 변경(`cd`)합니다.</span><span class="sxs-lookup"><span data-stu-id="99796-146">Change directory (`cd`) to the server instance that hosts the primary replica.</span></span>  
  
2.  <span data-ttu-id="99796-147">`Add-SqlAvailabilityDatabase` cmdlet을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="99796-147">Use the `Add-SqlAvailabilityDatabase` cmdlet.</span></span>  
  
     <span data-ttu-id="99796-148">예를 들어 다음 명령은 보조 데이터베이스 `MyDd` 을(를) `MyAG` 가용성 그룹에 추가합니다. 이 가용성 그룹의 주 복제본은 `PrimaryServer\InstanceName`에 의해 호스트됩니다.</span><span class="sxs-lookup"><span data-stu-id="99796-148">For example, the following command adds the secondary database `MyDd` to the `MyAG` availability group, whose primary replica is hosted by `PrimaryServer\InstanceName`.</span></span>  
  
    ```powershell
    Add-SqlAvailabilityDatabase `   
     -Path SQLSERVER:\SQL\PrimaryServer\InstanceName\AvailabilityGroups\MyAG `   
     -Database "MyDb"  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="99796-149">cmdlet의 구문을 보려면 `Get-Help` PowerShell 환경에서 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] cmdlet을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="99796-149">To view the syntax of a cmdlet, use the `Get-Help` cmdlet in the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell environment.</span></span> <span data-ttu-id="99796-150">자세한 내용은 [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="99796-150">For more information, see [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).</span></span>  
  
3.  <span data-ttu-id="99796-151">가용성 그룹에 데이터베이스를 추가한 후에는 보조 복제본을 호스팅하는 각 서버 인스턴스에서 해당 보조 데이터베이스를 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="99796-151">After you add a database to an availability group, you need to configure the corresponding secondary database on each server instance that hosts a secondary replica.</span></span> <span data-ttu-id="99796-152">자세한 내용은 [AlwaysOn 보조 데이터베이스에서 데이터 이동 시작&#40;SQL Server&#41;](start-data-movement-on-an-always-on-secondary-database-sql-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="99796-152">For more information, see [Start Data Movement on an AlwaysOn Secondary Database &#40;SQL Server&#41;](start-data-movement-on-an-always-on-secondary-database-sql-server.md).</span></span>  
  
 <span data-ttu-id="99796-153">SQL Server PowerShell 공급자를 설정 하 고 사용 하려면 [SQL Server PowerShell 공급자](../../../powershell/sql-server-powershell-provider.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="99796-153">To set up and use the SQL Server PowerShell provider, see [SQL Server PowerShell Provider](../../../powershell/sql-server-powershell-provider.md).</span></span>

 <span data-ttu-id="99796-154">다음 예는 가용성 그룹의 주 복제본을 호스팅하는 서버 인스턴스에 있는 데이터베이스에서 보조 데이터베이스를 준비하고, 이 데이터베이스를 가용성 그룹에 주 데이터베이스로 추가한 다음, 보조 데이터베이스를 가용성 그룹에 조인하는 전체 과정을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="99796-154">The following example shows the full process for preparing a secondary database from a database on the server instance that hosts the primary replica of an availability group, adding the database to an availability group (as a primary database), and then joining the secondary database to the availability group.</span></span> <span data-ttu-id="99796-155">가장 먼저, 이 예에서는 데이터베이스와 해당 트랜잭션 로그를 백업합니다.</span><span class="sxs-lookup"><span data-stu-id="99796-155">First, the example backs up the database and its transaction log.</span></span> <span data-ttu-id="99796-156">그런 다음 보조 복제본을 호스팅하는 서버 인스턴스로 데이터베이스 및 로그 백업을 복원합니다.</span><span class="sxs-lookup"><span data-stu-id="99796-156">Then the example restores the database and log backups to the server instances that host a secondary replica.</span></span>  
  
 <span data-ttu-id="99796-157">이 예에서는 `Add-SqlAvailabilityDatabase`를 두 번 호출합니다. 먼저 주 복제본에서 호출해서 데이터베이스를 가용성 그룹에 추가한 다음 보조 복제본에서 호출해서 해당 복제본에 있는 보조 데이터베이스를 가용성 그룹에 조인합니다.</span><span class="sxs-lookup"><span data-stu-id="99796-157">The example calls `Add-SqlAvailabilityDatabase` twice: first on the primary replica to add the database to the availability group, and then on the secondary replica to join the secondary database on that replica to the availability group.</span></span> <span data-ttu-id="99796-158">보조 복제본이 두 개 이상인 경우 각 보조 복제본에서 보조 데이터베이스를 복원 및 조인합니다.</span><span class="sxs-lookup"><span data-stu-id="99796-158">If you have more than one secondary replica, restore and join the secondary database on each of them.</span></span>  
  
```powershell
$DatabaseBackupFile = "\\share\backups\MyDatabase.bak"  
$LogBackupFile = "\\share\backups\MyDatabase.trn"  
$MyAgPrimaryPath = "SQLSERVER:\SQL\PrimaryServer\InstanceName\AvailabilityGroups\MyAg"  
$MyAgSecondaryPath = "SQLSERVER:\SQL\SecondaryServer\InstanceName\AvailabilityGroups\MyAg"  
  
Backup-SqlDatabase -Database "MyDatabase" -BackupFile $DatabaseBackupFile -ServerInstance "PrimaryServer\InstanceName"  
Backup-SqlDatabase -Database "MyDatabase" -BackupFile $LogBackupFile -ServerInstance "PrimaryServer\InstanceName" -BackupAction 'Log'  
  
Restore-SqlDatabase -Database "MyDatabase" -BackupFile $DatabaseBackupFile -ServerInstance "SecondaryServer\InstanceName" -NoRecovery  
Restore-SqlDatabase -Database "MyDatabase" -BackupFile $LogBackupFile -ServerInstance "SecondaryServer\InstanceName" -RestoreAction 'Log' -NoRecovery  
  
Add-SqlAvailabilityDatabase -Path $MyAgPrimaryPath -Database "MyDatabase"  
Add-SqlAvailabilityDatabase -Path $MyAgSecondaryPath -Database "MyDatabase"
```  
  
## <a name="see-also"></a><span data-ttu-id="99796-159">참고 항목</span><span class="sxs-lookup"><span data-stu-id="99796-159">See Also</span></span>  
 <span data-ttu-id="99796-160">[AlwaysOn 가용성 그룹 &#40;SQL Server 개요&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="99796-160">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="99796-161">[가용성 그룹의 생성 및 구성&#40;SQL Server&#41;](creation-and-configuration-of-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="99796-161">[Creation and Configuration of Availability Groups &#40;SQL Server&#41;](creation-and-configuration-of-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="99796-162">[AlwaysOn 대시보드 &#40;SQL Server Management Studio를 사용&#41;](use-the-always-on-dashboard-sql-server-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="99796-162">[Use the AlwaysOn Dashboard &#40;SQL Server Management Studio&#41;](use-the-always-on-dashboard-sql-server-management-studio.md) </span></span>  
 [<span data-ttu-id="99796-163">가용성 그룹 모니터링&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="99796-163">Monitor Availability Groups &#40;Transact-SQL&#41;</span></span>](monitor-availability-groups-transact-sql.md)  
