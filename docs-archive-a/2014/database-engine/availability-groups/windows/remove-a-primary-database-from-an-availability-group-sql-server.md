---
title: 가용성 그룹에서 주 데이터베이스 제거(SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.availabilitygroup.removeprimarydb.f1
helpviewer_keywords:
- primary databases [SQL Server], in availability group
- Availability Groups [SQL Server], removing
- Availability Groups [SQL Server], configuring
- Availability Groups [SQL Server], databases
ms.assetid: 6d4ca31e-ddf0-44bf-be5e-a5da060bf096
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 6b6fafaf6464431d68f8cfdf9dc9d8fa844a42a7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648602"
---
# <a name="remove-a-primary-database-from-an-availability-group-sql-server"></a><span data-ttu-id="87c9e-102">가용성 그룹에서 주 데이터베이스 제거(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="87c9e-102">Remove a Primary Database from an Availability Group (SQL Server)</span></span>
  <span data-ttu-id="87c9e-103">이 항목에서는 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)] 또는 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]의 PowerShell을 사용하여 AlwaysOn 가용성 그룹에서 주 데이터베이스와 해당 보조 데이터베이스를 모두 제거하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="87c9e-103">This topic describes how to remove both the primary database and the corresponding secondary database(s) from an AlwaysOn availability group by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)], or PowerShell in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span>  
  
-   <span data-ttu-id="87c9e-104">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="87c9e-104">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="87c9e-105">사전 요구 사항 및 제한 사항</span><span class="sxs-lookup"><span data-stu-id="87c9e-105">Prerequisites and Restrictions</span></span>](#Prerequisites)  
  
     [<span data-ttu-id="87c9e-106">보안</span><span class="sxs-lookup"><span data-stu-id="87c9e-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="87c9e-107">**가용성 데이터베이스를 제거하려면:**</span><span class="sxs-lookup"><span data-stu-id="87c9e-107">**To remove an availability database, using:**</span></span>  
  
     [<span data-ttu-id="87c9e-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="87c9e-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="87c9e-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="87c9e-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
     [<span data-ttu-id="87c9e-110">PowerShell</span><span class="sxs-lookup"><span data-stu-id="87c9e-110">PowerShell</span></span>](#PowerShellProcedure)  
  
-   <span data-ttu-id="87c9e-111">**후속 작업:**  [가용성 그룹에서 가용성 데이터베이스를 제거한 후](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="87c9e-111">**Follow Up:**  [After Removing an Availability Database from an Availability Group](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="87c9e-112">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="87c9e-112">Before You Begin</span></span>  
  
###  <a name="prerequisites-and-restrictions"></a><a name="Prerequisites"></a> <span data-ttu-id="87c9e-113">사전 요구 사항 및 제한 사항</span><span class="sxs-lookup"><span data-stu-id="87c9e-113">Prerequisites and Restrictions</span></span>  
  
-   <span data-ttu-id="87c9e-114">이 태스크는 주 복제본에서만 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="87c9e-114">This task is supported only on primary replicas.</span></span> <span data-ttu-id="87c9e-115">주 복제본을 호스팅하는 서버 인스턴스에 연결되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="87c9e-115">You must be connected to the server instance that hosts the primary replica.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="87c9e-116">보안</span><span class="sxs-lookup"><span data-stu-id="87c9e-116">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="87c9e-117">권한</span><span class="sxs-lookup"><span data-stu-id="87c9e-117">Permissions</span></span>  
 <span data-ttu-id="87c9e-118">가용성 그룹에 대한 ALTER AVAILABILITY GROUP 권한, CONTROL AVAILABILITY GROUP 권한, ALTER ANY AVAILABILITY GROUP 권한 또는 CONTROL SERVER 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="87c9e-118">Requires ALTER AVAILABILITY GROUP permission on the availability group, CONTROL AVAILABILITY GROUP permission, ALTER ANY AVAILABILITY GROUP permission, or CONTROL SERVER permission.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="87c9e-119">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="87c9e-119">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="87c9e-120">**가용성 데이터베이스를 제거하려면**</span><span class="sxs-lookup"><span data-stu-id="87c9e-120">**To remove an availability database**</span></span>  
  
1.  <span data-ttu-id="87c9e-121">개체 탐색기에서 제거할 데이터베이스의 주 복제본을 호스팅하는 서버 인스턴스에 연결하고 서버 트리를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="87c9e-121">In Object Explorer, connect to the server instance that hosts the primary replica of the database or databases to be removed, and expand the server tree.</span></span>  
  
2.  <span data-ttu-id="87c9e-122">**AlwaysOn 고가용성** 및 **가용성 그룹** 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="87c9e-122">Expand the **AlwaysOn High Availability** node and the **Availability Groups** node.</span></span>  
  
3.  <span data-ttu-id="87c9e-123">가용성 그룹을 선택하고 **가용성 데이터베이스** 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="87c9e-123">Select the availability group, and expand the **Availability Databases** node.</span></span>  
  
4.  <span data-ttu-id="87c9e-124">이 단계는 여러 데이터베이스 그룹을 제거할지 아니면 데이터베이스를 하나만 제거할지에 따라 다음과 같이 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="87c9e-124">This step depends on whether you want to remove multiple databases groups or only one database, as follows:</span></span>  
  
    -   <span data-ttu-id="87c9e-125">여러 데이터베이스를 제거하려면 **개체 탐색기 정보** 창을 사용하여 제거할 모든 데이터베이스를 표시하고 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="87c9e-125">To remove multiple databases, use the **Object Explorer Details** pane to view and select all the databases that you want to remove.</span></span> <span data-ttu-id="87c9e-126">자세한 내용은 [개체 탐색기 정보를 사용하여 가용성 그룹 모니터링&#40;SQL Server Management Studio&#41;](use-object-explorer-details-to-monitor-availability-groups.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="87c9e-126">For more information, see [Use the Object Explorer Details to Monitor Availability Groups &#40;SQL Server Management Studio&#41;](use-object-explorer-details-to-monitor-availability-groups.md).</span></span>  
  
    -   <span data-ttu-id="87c9e-127">단일 데이터베이스를 제거하려면 **개체 탐색기** 창 또는 **개체 탐색기 정보** 창에서 데이터베이스를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="87c9e-127">To remove a single database, select it in either the **Object Explorer** pane or the **Object Explorer Details** pane.</span></span>  
  
5.  <span data-ttu-id="87c9e-128">선택한 데이터베이스를 마우스 오른쪽 단추로 클릭하고 명령 메뉴에서 **가용성 그룹에서 데이터베이스 제거** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="87c9e-128">Right-click the selected database or databases, and select **Remove Database from Availability Group** in the command menu.</span></span>  
  
6.  <span data-ttu-id="87c9e-129">**가용성 그룹에서 데이터베이스 제거** 대화 상자에서 나열된 데이터베이스를 모두 제거하려면 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="87c9e-129">In the **Remove Databases from Availability Group** dialog box, to remove all the listed databases, click **OK**.</span></span> <span data-ttu-id="87c9e-130">모든 데이터베이스를 제거하지 않으려면 **취소**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="87c9e-130">If you do not want to remove all them, click **Cancel**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="87c9e-131">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="87c9e-131">Using Transact-SQL</span></span>  
 <span data-ttu-id="87c9e-132">**가용성 데이터베이스를 제거하려면**</span><span class="sxs-lookup"><span data-stu-id="87c9e-132">**To remove an availability database**</span></span>  
  
1.  <span data-ttu-id="87c9e-133">주 복제본을 호스팅하는 서버 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="87c9e-133">Connect to the server instance that hosts the primary replica.</span></span>  
  
2.  <span data-ttu-id="87c9e-134">다음과 같은 [ALTER AVAILABILITY GROUP](/sql/t-sql/statements/alter-availability-group-transact-sql) 문을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="87c9e-134">Use the [ALTER AVAILABILITY GROUP](/sql/t-sql/statements/alter-availability-group-transact-sql) statement, as follows:</span></span>  
  
     <span data-ttu-id="87c9e-135">ALTER AVAILABILITY GROUP *group_name* REMOVE DATABASE *availability_database_name*</span><span class="sxs-lookup"><span data-stu-id="87c9e-135">ALTER AVAILABILITY GROUP *group_name* REMOVE DATABASE *availability_database_name*</span></span>  
  
     <span data-ttu-id="87c9e-136">여기서 *group_name* 은 가용성 그룹의 이름이고, *database_name* 은 제거할 데이터베이스의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="87c9e-136">where *group_name* is the name of the availability group and *database_name* is the name of the database to be removed.</span></span>  
  
     <span data-ttu-id="87c9e-137">다음 예에서는 `Db6` 가용성 그룹에서 `MyAG` 이라는 데이터베이스를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="87c9e-137">The following example removes a databases named `Db6` from the `MyAG` availability group.</span></span>  
  
    ```sql
    ALTER AVAILABILITY GROUP MyAG REMOVE DATABASE Db6;  
    ```  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a> <span data-ttu-id="87c9e-138">PowerShell 사용</span><span class="sxs-lookup"><span data-stu-id="87c9e-138">Using PowerShell</span></span>  
 <span data-ttu-id="87c9e-139">**가용성 데이터베이스를 제거하려면**</span><span class="sxs-lookup"><span data-stu-id="87c9e-139">**To remove an availability database**</span></span>  
  
1.  <span data-ttu-id="87c9e-140">주 복제본을 호스팅하는 서버 인스턴스로 디렉터리를 변경(`cd`)합니다.</span><span class="sxs-lookup"><span data-stu-id="87c9e-140">Change directory (`cd`) to the server instance that hosts the primary replica.</span></span>  
  
2.  <span data-ttu-id="87c9e-141">`Remove-SqlAvailabilityDatabase` cmdlet을 사용하여 가용성 그룹에서 제거할 가용성 데이터베이스의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="87c9e-141">Use the `Remove-SqlAvailabilityDatabase` cmdlet, specifying the name of the availability database to be removed from the availability group.</span></span> <span data-ttu-id="87c9e-142">주 복제본을 호스팅하는 서버 인스턴스에 연결되어 있는 경우 주 데이터베이스와 해당 보조 데이터베이스가 모두 가용성 그룹에서 제거됩니다.</span><span class="sxs-lookup"><span data-stu-id="87c9e-142">When you are connected to the server instance that hosts the primary replica, the primary database and its corresponding secondary databases are all removed from the availability group.</span></span>  
  
     <span data-ttu-id="87c9e-143">예를 들어 다음 명령은 `MyDb9` 라는 가용성 그룹에서 `MyAg`가용성 데이터베이스를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="87c9e-143">For example, the following command removes the availability database `MyDb9` from the availability group named `MyAg`.</span></span> <span data-ttu-id="87c9e-144">명령이 주 복제본을 호스팅하는 서버 인스턴스에서 실행되므로 주 데이터베이스와 모든 보조 데이터베이스가 모두 가용성 그룹에서 제거됩니다.</span><span class="sxs-lookup"><span data-stu-id="87c9e-144">Because the command is executed on the server instance that hosts the primary replica, the primary database and all its corresponding secondary databases are removed from the availability group.</span></span> <span data-ttu-id="87c9e-145">보조 복제본에서 더 이상 이 데이터베이스에 대한 데이터 동기화가 발생하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="87c9e-145">Data synchronization will no longer occur for this database on any secondary replica.</span></span>  
  
    ```powershell
    Remove-SqlAvailabilityDatabase -Path SQLSERVER:\Sql\PrimaryComputer\InstanceName\AvailabilityGroups\MyAg\Databases\MyDb9  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="87c9e-146">cmdlet의 구문을 보려면 `Get-Help` PowerShell 환경에서 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] cmdlet을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="87c9e-146">To view the syntax of a cmdlet, use the `Get-Help` cmdlet in the [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] PowerShell environment.</span></span> <span data-ttu-id="87c9e-147">자세한 내용은 [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="87c9e-147">For more information, see [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).</span></span>  
  
 <span data-ttu-id="87c9e-148">**SQL Server PowerShell 공급자를 설정하고 사용하려면**</span><span class="sxs-lookup"><span data-stu-id="87c9e-148">**To set up and use the SQL Server PowerShell provider**</span></span>  
  
-   [<span data-ttu-id="87c9e-149">SQL Server PowerShell 공급자</span><span class="sxs-lookup"><span data-stu-id="87c9e-149">SQL Server PowerShell Provider</span></span>](../../../powershell/sql-server-powershell-provider.md)  
  
##  <a name="follow-up-after-removing-an-availability-database-from-an-availability-group"></a><a name="FollowUp"></a><span data-ttu-id="87c9e-150">후속 작업: 가용성 그룹에서 가용성 데이터베이스를 제거한 후</span><span class="sxs-lookup"><span data-stu-id="87c9e-150">Follow Up: After Removing an Availability Database from an Availability Group</span></span>  
 <span data-ttu-id="87c9e-151">가용성 데이터베이스를 가용성 그룹에서 제거하면 이전 주 데이터베이스와 해당 보조 데이터베이스 사이의 데이터 동기화가 해제됩니다.</span><span class="sxs-lookup"><span data-stu-id="87c9e-151">Removing an availability database from its availability group ends data synchronization between the former primary database and the corresponding secondary databases.</span></span> <span data-ttu-id="87c9e-152">이전 주 데이터베이스는 온라인 상태로 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="87c9e-152">The former primary database remains online.</span></span> <span data-ttu-id="87c9e-153">모든 해당 보조 데이터베이스는 복원 중 상태가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="87c9e-153">Every corresponding secondary database is placed in the RESTORING state.</span></span>  
  
 <span data-ttu-id="87c9e-154">여기서 제거된 보조 데이터베이스를 다음과 같은 다른 방법으로 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="87c9e-154">At this point there are alternative ways of dealing with a removed secondary database:</span></span>  
  
-   <span data-ttu-id="87c9e-155">해당 보조 데이터베이스가 더 이상 필요하지 않은 경우 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="87c9e-155">If you no longer need a given secondary database, you can drop it.</span></span>  
  
     <span data-ttu-id="87c9e-156">자세한 내용은 [데이터베이스 삭제](../../../relational-databases/databases/delete-a-database.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="87c9e-156">For more information, see [Delete a Database](../../../relational-databases/databases/delete-a-database.md).</span></span>  
  
-   <span data-ttu-id="87c9e-157">가용성 그룹에서 제거된 보조 데이터베이스에 액세스하려면 데이터베이스를 복구할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="87c9e-157">If you want to access a removed secondary database after it has been removed from the availability group, you can recover the database.</span></span> <span data-ttu-id="87c9e-158">그러나 제거된 보조 데이터베이스를 복구하면 같은 이름의 독립적인 두 분기 데이터베이스가 온라인 상태가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="87c9e-158">However, if you recover a removed secondary database, two divergent, independent databases that have the same name are online.</span></span> <span data-ttu-id="87c9e-159">클라이언트가 이 두 데이터베이스 중 하나(일반적으로 가장 최근의 주 데이터베이스)에만 액세스할 수 있는지 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="87c9e-159">You must make sure that clients can access only one of them, typically the most recent primary database.</span></span>  
  
     <span data-ttu-id="87c9e-160">자세한 내용은 [데이터를 복원하지 않고 데이터베이스 복구&#40;Transact-SQL&#41;](../../../relational-databases/backup-restore/recover-a-database-without-restoring-data-transact-sql.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="87c9e-160">For more information, see [Recover a Database Without Restoring Data &#40;Transact-SQL&#41;](../../../relational-databases/backup-restore/recover-a-database-without-restoring-data-transact-sql.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87c9e-161">참고 항목</span><span class="sxs-lookup"><span data-stu-id="87c9e-161">See Also</span></span>  
 <span data-ttu-id="87c9e-162">[AlwaysOn 가용성 그룹 &#40;SQL Server 개요&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="87c9e-162">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 [<span data-ttu-id="87c9e-163">가용성 그룹에서 보조 데이터베이스 제거&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="87c9e-163">Remove a Secondary Database from an Availability Group &#40;SQL Server&#41;</span></span>](remove-a-secondary-database-from-an-availability-group-sql-server.md)  
