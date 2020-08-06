---
title: 가용성 그룹에서 보조 데이터베이스 제거(SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.availabilitygroup.unjoindb.f1
helpviewer_keywords:
- secondary databases [SQL Server], in availability group
- Availability Groups [SQL Server], removing
- Availability Groups [SQL Server], databases
ms.assetid: 4e51a570-58d7-4f01-9390-4198f3602576
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 1c3de0afd73b46ae5594d26d1763f5bd78483efd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648600"
---
# <a name="remove-a-secondary-database-from-an-availability-group-sql-server"></a><span data-ttu-id="7509a-102">가용성 그룹에서 보조 데이터베이스 제거(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="7509a-102">Remove a Secondary Database from an Availability Group (SQL Server)</span></span>
  <span data-ttu-id="7509a-103">이 항목에서는 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]에서 [!INCLUDE[tsql](../../../includes/tsql-md.md)], [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]또는 PowerShell을 사용하여 AlwaysOn 가용성 그룹에서 보조 데이터베이스를 제거하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="7509a-103">This topic describes how to remove a secondary database from an AlwaysOn availability group by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)], or PowerShell in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span>  
  
-   <span data-ttu-id="7509a-104">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="7509a-104">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="7509a-105">필수 구성 요소</span><span class="sxs-lookup"><span data-stu-id="7509a-105">Prerequisites</span></span>](#Prerequisites)  
  
     [<span data-ttu-id="7509a-106">보안</span><span class="sxs-lookup"><span data-stu-id="7509a-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="7509a-107">**보조 데이터베이스를 제거하려면:**</span><span class="sxs-lookup"><span data-stu-id="7509a-107">**To remove a secondary database, using:**</span></span>  
  
     [<span data-ttu-id="7509a-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="7509a-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="7509a-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="7509a-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
     [<span data-ttu-id="7509a-110">PowerShell</span><span class="sxs-lookup"><span data-stu-id="7509a-110">PowerShell</span></span>](#PowerShellProcedure)  
  
-   <span data-ttu-id="7509a-111">**후속 작업:**  [가용성 그룹에서 보조 데이터베이스를 제거한 후](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="7509a-111">**Follow Up:**  [After Removing a Secondary Database from an Availability Group](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="7509a-112">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="7509a-112">Before You Begin</span></span>  
  
###  <a name="Restrictions"></a>   
###  <a name="prerequisites-and-restrictions"></a><a name="Prerequisites"></a> <span data-ttu-id="7509a-113">사전 요구 사항 및 제한 사항</span><span class="sxs-lookup"><span data-stu-id="7509a-113">Prerequisites and Restrictions</span></span>  
  
-   <span data-ttu-id="7509a-114">이 태스크는 보조 복제본에서만 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="7509a-114">This task is supported only on secondary replicas.</span></span> <span data-ttu-id="7509a-115">데이터베이스를 제거할 보조 복제본을 호스팅하는 서버 인스턴스에 연결되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7509a-115">You must be connected to the server instance that hosts the secondary replica from which the database is to be removed.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="7509a-116">보안</span><span class="sxs-lookup"><span data-stu-id="7509a-116">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="7509a-117">권한</span><span class="sxs-lookup"><span data-stu-id="7509a-117">Permissions</span></span>  
 <span data-ttu-id="7509a-118">데이터베이스에 대한 ALTER 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="7509a-118">Requires ALTER permission on the database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="7509a-119">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="7509a-119">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="7509a-120">**가용성 그룹에서 보조 데이터베이스를 제거하려면**</span><span class="sxs-lookup"><span data-stu-id="7509a-120">**To remove a secondary database from an availability group**</span></span>  
  
1.  <span data-ttu-id="7509a-121">개체 탐색기에서 하나 이상의 보조 데이터베이스를 제거할 보조 복제본을 호스팅하는 서버 인스턴스에 연결하고 서버 트리를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="7509a-121">In Object Explorer, connect to the server instance that hosts the secondary replica from which you want to remove one or more secondary databases, and expand the server tree.</span></span>  
  
2.  <span data-ttu-id="7509a-122">**AlwaysOn 고가용성** 및 **가용성 그룹** 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="7509a-122">Expand the **AlwaysOn High Availability** node and the **Availability Groups** node.</span></span>  
  
3.  <span data-ttu-id="7509a-123">가용성 그룹을 선택하고 **가용성 데이터베이스** 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="7509a-123">Select the availability group, and expand the **Availability Databases** node.</span></span>  
  
4.  <span data-ttu-id="7509a-124">이 단계는 여러 데이터베이스 그룹을 제거할지 아니면 데이터베이스를 하나만 제거할지에 따라 다음과 같이 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="7509a-124">This step depends on whether you want to remove multiple databases groups or only one database, as follows:</span></span>  
  
    -   <span data-ttu-id="7509a-125">여러 데이터베이스를 제거하려면 **개체 탐색기 정보** 창을 사용하여 제거할 모든 데이터베이스를 표시하고 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="7509a-125">To remove multiple databases, use the **Object Explorer Details** pane to view and select all the databases that you want to remove.</span></span> <span data-ttu-id="7509a-126">자세한 내용은 [개체 탐색기 정보를 사용하여 가용성 그룹 모니터링&#40;SQL Server Management Studio&#41;](use-object-explorer-details-to-monitor-availability-groups.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7509a-126">For more information, see [Use the Object Explorer Details to Monitor Availability Groups &#40;SQL Server Management Studio&#41;](use-object-explorer-details-to-monitor-availability-groups.md).</span></span>  
  
    -   <span data-ttu-id="7509a-127">단일 데이터베이스를 제거하려면 **개체 탐색기** 창 또는 **개체 탐색기 정보** 창에서 데이터베이스를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="7509a-127">To remove a single database, select it in either the **Object Explorer** pane or the **Object Explorer Details** pane.</span></span>  
  
5.  <span data-ttu-id="7509a-128">선택한 데이터베이스를 마우스 오른쪽 단추로 클릭하고 명령 메뉴에서 **보조 데이터베이스 제거** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="7509a-128">Right-click the selected database or databases, and select **Remove Secondary Database** in the command menu.</span></span>  
  
6.  <span data-ttu-id="7509a-129">**가용성 그룹에서 데이터베이스 제거** 대화 상자에서 나열된 데이터베이스를 모두 제거하려면 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7509a-129">In the **Remove Database from Availability Group** dialog box, to remove all the listed databases, click **OK**.</span></span> <span data-ttu-id="7509a-130">나열된 모든 데이터베이스를 제거하지 않으려면 **취소**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7509a-130">If you do not want to remove all the listed databases, click **Cancel**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="7509a-131">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="7509a-131">Using Transact-SQL</span></span>  
 <span data-ttu-id="7509a-132">**가용성 그룹에서 보조 데이터베이스를 제거하려면**</span><span class="sxs-lookup"><span data-stu-id="7509a-132">**To remove a secondary database from an availability group**</span></span>  
  
1.  <span data-ttu-id="7509a-133">보조 복제본을 호스팅하는 서버 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="7509a-133">Connect to the server instance that hosts the secondary replica.</span></span>  
  
2.  <span data-ttu-id="7509a-134">다음과 같이 [ALTER DATABASE 문의 SET HADR 절](/sql/t-sql/statements/alter-database-transact-sql-set-hadr) 을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="7509a-134">Use the [SET HADR clause of the ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql-set-hadr) statement, as follows:</span></span>  
  
     <span data-ttu-id="7509a-135">ALTER DATABASE *database_name* SET HADR OFF</span><span class="sxs-lookup"><span data-stu-id="7509a-135">ALTER DATABASE *database_name* SET HADR OFF</span></span>  
  
     <span data-ttu-id="7509a-136">여기서 *database_name* 은 해당 데이터베이스가 속한 가용성 그룹에서 제거할 보조 데이터베이스의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="7509a-136">where *database_name* is the name of a secondary database to be removed from the availability group to which it belongs.</span></span>  
  
     <span data-ttu-id="7509a-137">다음 예에서는 가용성 그룹에서 *MyDb2* 라는 로컬 보조 데이터베이스를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="7509a-137">The following example removes the local secondary database *MyDb2* from its availability group.</span></span>  
  
    ```sql
    ALTER DATABASE MyDb2 SET HADR OFF;  
    GO  
    ```  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a> <span data-ttu-id="7509a-138">PowerShell 사용</span><span class="sxs-lookup"><span data-stu-id="7509a-138">Using PowerShell</span></span>  
 <span data-ttu-id="7509a-139">**가용성 그룹에서 보조 데이터베이스를 제거하려면**</span><span class="sxs-lookup"><span data-stu-id="7509a-139">**To remove a secondary database from an availability group**</span></span>  
  
1.  <span data-ttu-id="7509a-140">보조 복제본을 호스팅하는 서버 인스턴스로 디렉터리를 변경(`cd`)합니다.</span><span class="sxs-lookup"><span data-stu-id="7509a-140">Change directory (`cd`) to the server instance that hosts the secondary replica.</span></span>  
  
2.  <span data-ttu-id="7509a-141">**Remove-SqlAvailabilityDatabase** cmdlet을 사용하여 가용성 그룹에서 제거할 가용성 데이터베이스의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="7509a-141">Use the **Remove-SqlAvailabilityDatabase** cmdlet, specifying the name of the availability database to be removed from the availability group.</span></span> <span data-ttu-id="7509a-142">보조 복제본을 호스팅하는 서버 인스턴스에 연결된 경우 가용성 그룹에서 로컬 보조 데이터베이스만 제거됩니다.</span><span class="sxs-lookup"><span data-stu-id="7509a-142">When you are connected to a server instance that hosts a secondary replica, only the local secondary database is removed from the availability group.</span></span>  
  
     <span data-ttu-id="7509a-143">예를 들어 다음 명령은 `MyDb8` 서버 인스턴스가 호스팅하는 보조 복제본에서 보조 데이터베이스 `SecondaryComputer\Instance`을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="7509a-143">For example, the following command removes the secondary database `MyDb8` from the secondary replica hosted by the server instance named `SecondaryComputer\Instance`.</span></span> <span data-ttu-id="7509a-144">제거된 보조 데이터베이스에 대한 데이터 동기화가 중단됩니다.</span><span class="sxs-lookup"><span data-stu-id="7509a-144">Data synchronization to the removed secondary databases ceases.</span></span> <span data-ttu-id="7509a-145">이 명령은 주 데이터베이스 또는 다른 보조 데이터베이스에 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7509a-145">This command does not affect the primary database or any other secondary databases.</span></span>  
  
    ```powershell
    Remove-SqlAvailabilityDatabase -Path SQLSERVER:\Sql\SecondaryComputer\InstanceName\AvailabilityGroups\MyAg\Databases\MyDb8  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="7509a-146">cmdlet의 구문을 보려면 `Get-Help` PowerShell 환경에서 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] cmdlet을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="7509a-146">To view the syntax of a cmdlet, use the `Get-Help` cmdlet in the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell environment.</span></span> <span data-ttu-id="7509a-147">자세한 내용은 [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7509a-147">For more information, see [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).</span></span>  
  
 <span data-ttu-id="7509a-148">**SQL Server PowerShell 공급자를 설정하고 사용하려면**</span><span class="sxs-lookup"><span data-stu-id="7509a-148">**To set up and use the SQL Server PowerShell provider**</span></span>  
  
-   [<span data-ttu-id="7509a-149">SQL Server PowerShell 공급자</span><span class="sxs-lookup"><span data-stu-id="7509a-149">SQL Server PowerShell Provider</span></span>](../../../powershell/sql-server-powershell-provider.md)  
  
##  <a name="follow-up-after-removing-a-secondary-database-from-an-availability-group"></a><a name="FollowUp"></a><span data-ttu-id="7509a-150">후속 작업: 가용성 그룹에서 보조 데이터베이스를 제거한 후</span><span class="sxs-lookup"><span data-stu-id="7509a-150">Follow Up: After Removing a Secondary Database from an Availability Group</span></span>  
 <span data-ttu-id="7509a-151">보조 데이터베이스가 제거되면 이 보조 데이터베이스는 더 이상 가용성 그룹에 조인되지 않으며 제거된 보조 데이터베이스에 대한 모든 정보가 가용성 그룹에서 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="7509a-151">When a secondary database is removed, it is no longer joined to the availability group and all information about the removed secondary database is discarded by the availability group.</span></span> <span data-ttu-id="7509a-152">제거된 보조 데이터베이스는 RESTORING 상태가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7509a-152">The removed secondary database is placed in the RESTORING state.</span></span>  
  
> [!TIP]  
>  <span data-ttu-id="7509a-153">보조 데이터베이스를 제거한 후에는 짧은 기간 동안 이를 다시 가용성 그룹에 조인하여 데이터베이스에서 AlwaysOn 데이터 동기화를 다시 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7509a-153">For a short time after removing a secondary database, you might be able to restart AlwaysOn data synchronization on the database by re-joining it to the availability group.</span></span> <span data-ttu-id="7509a-154">자세한 내용은 [가용성 그룹에 보조 데이터베이스 조인&#40;SQL Server&#41;](join-a-secondary-database-to-an-availability-group-sql-server.md)인스턴스에 AlwaysOn 가용성 그룹을 만드는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="7509a-154">For more information, see [Join a Secondary Database to an Availability Group &#40;SQL Server&#41;](join-a-secondary-database-to-an-availability-group-sql-server.md).</span></span>  
  
 <span data-ttu-id="7509a-155">여기서 제거된 보조 데이터베이스를 다음과 같은 다른 방법으로 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7509a-155">At this point there are alternative ways of dealing with a removed secondary database:</span></span>  
  
-   <span data-ttu-id="7509a-156">보조 데이터베이스가 더 이상 필요하지 않은 경우 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7509a-156">If you no longer need the secondary database, you can drop it.</span></span>  
  
     <span data-ttu-id="7509a-157">자세한 내용은 [DROP DATABASE&#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-database-audit-specification-transact-sql) 또는 [데이터베이스 삭제](../../../relational-databases/databases/delete-a-database.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7509a-157">For more information, see [DROP DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-database-audit-specification-transact-sql) or [Delete a Database](../../../relational-databases/databases/delete-a-database.md).</span></span>  
  
-   <span data-ttu-id="7509a-158">가용성 그룹에서 제거된 보조 데이터베이스에 액세스하려면 데이터베이스를 복구할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7509a-158">If you want to access a removed secondary database after it has been removed from the availability group, you can recover the database.</span></span> <span data-ttu-id="7509a-159">그러나 제거된 보조 데이터베이스를 복구하면 같은 이름의 독립적인 두 분기 데이터베이스가 온라인 상태가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7509a-159">However, if you recover a removed secondary database, two divergent, independent databases that have the same name are online.</span></span> <span data-ttu-id="7509a-160">클라이언트가 현재 주 데이터베이스에만 액세스할 수 있는지 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7509a-160">You must make sure that clients can access only the current primary database.</span></span>  
  
     <span data-ttu-id="7509a-161">자세한 내용은 [데이터를 복원하지 않고 데이터베이스 복구&#40;Transact-SQL&#41;](../../../relational-databases/backup-restore/recover-a-database-without-restoring-data-transact-sql.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7509a-161">For more information, see [Recover a Database Without Restoring Data &#40;Transact-SQL&#41;](../../../relational-databases/backup-restore/recover-a-database-without-restoring-data-transact-sql.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7509a-162">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7509a-162">See Also</span></span>  
 <span data-ttu-id="7509a-163">[AlwaysOn 가용성 그룹 &#40;SQL Server 개요&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="7509a-163">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 [<span data-ttu-id="7509a-164">가용성 그룹에서 주 데이터베이스 제거&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="7509a-164">Remove a Primary Database from an Availability Group &#40;SQL Server&#41;</span></span>](remove-a-primary-database-from-an-availability-group-sql-server.md)  
