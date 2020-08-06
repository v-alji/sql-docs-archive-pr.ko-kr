---
title: 가용성 그룹에서 보조 복제본 제거(SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.availabilitygroup.removesecondaryar.f1
helpviewer_keywords:
- Availability Groups [SQL Server], availability replicas
- Availability Groups [SQL Server], configuring
ms.assetid: 35ddc8b6-3e7c-4417-9a0a-d4987a09ddf7
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e3f2b35ec9cf27f2f7b23714a41665f2709837a5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648597"
---
# <a name="remove-a-secondary-replica-from-an-availability-group-sql-server"></a><span data-ttu-id="6d195-102">가용성 그룹에서 보조 복제본 제거(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="6d195-102">Remove a Secondary Replica from an Availability Group (SQL Server)</span></span>
  <span data-ttu-id="6d195-103">이 항목에서는 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]에서 [!INCLUDE[tsql](../../../includes/tsql-md.md)], [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]또는 PowerShell을 사용하여 AlwaysOn 가용성 그룹에서 보조 복제본을 제거하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="6d195-103">This topic describes how to remove a secondary replica from an AlwaysOn availability group by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)], or PowerShell in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span>  
  
-   <span data-ttu-id="6d195-104">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="6d195-104">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="6d195-105">제한 사항</span><span class="sxs-lookup"><span data-stu-id="6d195-105">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="6d195-106">필수 구성 요소</span><span class="sxs-lookup"><span data-stu-id="6d195-106">Prerequisites</span></span>](#Prerequisites)  
  
     [<span data-ttu-id="6d195-107">보안</span><span class="sxs-lookup"><span data-stu-id="6d195-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="6d195-108">**보조 복제본을 제거하려면:**</span><span class="sxs-lookup"><span data-stu-id="6d195-108">**To remove a secondary replica, using:**</span></span>  
  
     [<span data-ttu-id="6d195-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="6d195-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="6d195-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="6d195-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
     [<span data-ttu-id="6d195-111">PowerShell</span><span class="sxs-lookup"><span data-stu-id="6d195-111">PowerShell</span></span>](#PowerShellProcedure)  
  
-   <span data-ttu-id="6d195-112">**후속 작업:**  [보조 복제본을 제거한 후](#PostBestPractices)</span><span class="sxs-lookup"><span data-stu-id="6d195-112">**Follow Up:**  [After Removing a Secondary Replica](#PostBestPractices)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="6d195-113">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="6d195-113">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="6d195-114">제한 사항</span><span class="sxs-lookup"><span data-stu-id="6d195-114">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="6d195-115">이 태스크는 주 복제본에서만 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="6d195-115">This task is supported only on the primary replica.</span></span>  
  
-   <span data-ttu-id="6d195-116">가용성 그룹에서는 보조 복제본만 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6d195-116">Only a secondary replica can be removed from an availability group.</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="6d195-117">필수 조건</span><span class="sxs-lookup"><span data-stu-id="6d195-117">Prerequisites</span></span>  
  
-   <span data-ttu-id="6d195-118">가용성 그룹의 주 복제본을 호스팅하는 서버 인스턴스에 연결되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6d195-118">You must be connected to the server instance that hosts the primary replica of the availability group.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="6d195-119">보안</span><span class="sxs-lookup"><span data-stu-id="6d195-119">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="6d195-120">권한</span><span class="sxs-lookup"><span data-stu-id="6d195-120">Permissions</span></span>  
 <span data-ttu-id="6d195-121">가용성 그룹에 대한 ALTER AVAILABILITY GROUP 권한, CONTROL AVAILABILITY GROUP 권한, ALTER ANY AVAILABILITY GROUP 권한 또는 CONTROL SERVER 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="6d195-121">Requires ALTER AVAILABILITY GROUP permission on the availability group, CONTROL AVAILABILITY GROUP permission, ALTER ANY AVAILABILITY GROUP permission, or CONTROL SERVER permission.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="6d195-122">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="6d195-122">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="6d195-123">**보조 복제본을 제거하려면**</span><span class="sxs-lookup"><span data-stu-id="6d195-123">**To remove a secondary replica**</span></span>  
  
1.  <span data-ttu-id="6d195-124">개체 탐색기에서 주 복제본을 호스팅하는 서버 인스턴스에 연결하고 서버 트리를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="6d195-124">In Object Explorer, connect to the server instance that hosts the primary replica, and expand the server tree.</span></span>  
  
2.  <span data-ttu-id="6d195-125">**AlwaysOn 고가용성** 및 **가용성 그룹** 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="6d195-125">Expand the **AlwaysOn High Availability** node and the **Availability Groups** node.</span></span>  
  
3.  <span data-ttu-id="6d195-126">가용성 그룹을 선택하고 **가용성 복제본** 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="6d195-126">Select the availability group, and expand the **Availability Replicas** node.</span></span>  
  
4.  <span data-ttu-id="6d195-127">이 단계는 여러 복제본을 제거할지 아니면 복제본을 하나만 제거할지에 따라 다음과 같이 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="6d195-127">This step depends on whether you want to remove multiple replicas or only one replica, as follows:</span></span>  
  
    -   <span data-ttu-id="6d195-128">여러 복제본을 제거하려면 **개체 탐색기 정보** 창을 사용하여 제거할 모든 복제본을 표시하고 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6d195-128">To remove multiple replicas, use the **Object Explorer Details** pane to view and select all the replicas that you want to remove.</span></span> <span data-ttu-id="6d195-129">자세한 내용은 [개체 탐색기 정보를 사용하여 가용성 그룹 모니터링&#40;SQL Server Management Studio&#41;](use-object-explorer-details-to-monitor-availability-groups.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6d195-129">For more information, see [Use the Object Explorer Details to Monitor Availability Groups &#40;SQL Server Management Studio&#41;](use-object-explorer-details-to-monitor-availability-groups.md).</span></span>  
  
    -   <span data-ttu-id="6d195-130">단일 복제본을 제거하려면 **개체 탐색기** 창 또는 **개체 탐색기 정보** 창에서 복제본을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6d195-130">To remove a single replica, select it in either the **Object Explorer** pane or the **Object Explorer Details** pane.</span></span>  
  
5.  <span data-ttu-id="6d195-131">선택한 보조 복제본을 마우스 오른쪽 단추로 클릭하고 명령 메뉴에서 **가용성 그룹에서 제거** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6d195-131">Right-click the selected secondary replica or replicas, and select **Remove from Availability Group** in the command menu.</span></span>  
  
6.  <span data-ttu-id="6d195-132">**가용성 그룹에서 보조 복제본 제거** 대화 상자에서 나열된 보조 복제본을 모두 제거하려면 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6d195-132">In the **Remove Secondary Replicas from Availability Group** dialog box, to remove all the listed secondary replicas, click **OK**.</span></span> <span data-ttu-id="6d195-133">나열된 모든 복제본을 제거하지 않으려면 **취소**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6d195-133">If you do not want to remove all the listed replicas, click **Cancel**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="6d195-134">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="6d195-134">Using Transact-SQL</span></span>  
 <span data-ttu-id="6d195-135">**보조 복제본을 제거하려면**</span><span class="sxs-lookup"><span data-stu-id="6d195-135">**To remove a secondary replica**</span></span>  
  
1.  <span data-ttu-id="6d195-136">주 복제본을 호스팅하는 서버 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="6d195-136">Connect to the server instance that hosts the primary replica.</span></span>  
  
2.  <span data-ttu-id="6d195-137">다음과 같은 [ALTER AVAILABILITY GROUP](/sql/t-sql/statements/alter-availability-group-transact-sql) 문을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="6d195-137">Use the [ALTER AVAILABILITY GROUP](/sql/t-sql/statements/alter-availability-group-transact-sql) statement, as follows:</span></span>  
  
     <span data-ttu-id="6d195-138">ALTER AVAILABILITY GROUP *group_name* REMOVE REPLICA ON '*instance_name*' [,...*n*]</span><span class="sxs-lookup"><span data-stu-id="6d195-138">ALTER AVAILABILITY GROUP *group_name* REMOVE REPLICA ON '*instance_name*' [,...*n*]</span></span>  
  
     <span data-ttu-id="6d195-139">여기서 *group_name* 은 가용성 그룹의 이름이고 *instance_name* 은 보조 복제본이 있는 서버 인스턴스입니다.</span><span class="sxs-lookup"><span data-stu-id="6d195-139">where *group_name* is the name of the availability group and *instance_name* is the server instance where the secondary replica is located.</span></span>  
  
     <span data-ttu-id="6d195-140">다음 예에서는 *MyAG* 가용성 그룹에서 보조 복제본을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="6d195-140">The following example removes a secondary replica from the *MyAG* availability group.</span></span> <span data-ttu-id="6d195-141">대상 보조 복제본은 *COMPUTER02* 라는 컴퓨터에서 *HADR_INSTANCE*라는 서버 인스턴스에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6d195-141">The target secondary replica is located on a server instance named *HADR_INSTANCE* on a computer named *COMPUTER02*.</span></span>  
  
    ```sql
    ALTER AVAILABILITY GROUP MyAG REMOVE REPLICA ON 'COMPUTER02\HADR_INSTANCE';  
    ```  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a> <span data-ttu-id="6d195-142">PowerShell 사용</span><span class="sxs-lookup"><span data-stu-id="6d195-142">Using PowerShell</span></span>  
 <span data-ttu-id="6d195-143">**보조 복제본을 제거하려면**</span><span class="sxs-lookup"><span data-stu-id="6d195-143">**To remove a secondary replica**</span></span>  
  
1.  <span data-ttu-id="6d195-144">주 복제본을 호스팅하는 서버 인스턴스로 디렉터리를 변경(`cd`)합니다.</span><span class="sxs-lookup"><span data-stu-id="6d195-144">Change directory (`cd`) to the server instance that hosts the primary replica.</span></span>  
  
2.  <span data-ttu-id="6d195-145">**Remove-SqlAvailabilityReplica** cmdlet을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="6d195-145">Use the **Remove-SqlAvailabilityReplica** cmdlet.</span></span>  
  
     <span data-ttu-id="6d195-146">예를 들어 다음 명령은 `MyReplica` 라는 가용성 그룹에서 `MyAg`서버의 가용성 복제본을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="6d195-146">For example, the following command removes the availability replica on the server `MyReplica` from the availability group named `MyAg`.</span></span>  <span data-ttu-id="6d195-147">이 명령은 가용성 그룹의 주 복제본을 호스팅하는 서버 인스턴스에서 실행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6d195-147">This command must be run on the server instance that hosts the primary replica of the availability group.</span></span>  
  
    ```powershell
    Remove-SqlAvailabilityReplica -Path SQLSERVER:\SQL\PrimaryServer\InstanceName\AvailabilityGroups\MyAg\AvailabilityReplicas\MyReplica  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="6d195-148">cmdlet의 구문을 보려면 `Get-Help` PowerShell 환경에서 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] cmdlet을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="6d195-148">To view the syntax of a cmdlet, use the `Get-Help` cmdlet in the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell environment.</span></span> <span data-ttu-id="6d195-149">자세한 내용은 [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6d195-149">For more information, see [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).</span></span>  
  
 <span data-ttu-id="6d195-150">**SQL Server PowerShell 공급자를 설정하고 사용하려면**</span><span class="sxs-lookup"><span data-stu-id="6d195-150">**To set up and use the SQL Server PowerShell provider**</span></span>  
  
-   [<span data-ttu-id="6d195-151">SQL Server PowerShell 공급자</span><span class="sxs-lookup"><span data-stu-id="6d195-151">SQL Server PowerShell Provider</span></span>](../../../powershell/sql-server-powershell-provider.md)  
  
##  <a name="follow-up-after-removing-a-secondary-replica"></a><a name="PostBestPractices"></a> <span data-ttu-id="6d195-152">후속 작업: 보조 복제본을 제거한 후</span><span class="sxs-lookup"><span data-stu-id="6d195-152">Follow Up: After Removing a Secondary Replica</span></span>  
 <span data-ttu-id="6d195-153">현재 사용할 수 없는 복제본을 지정할 경우 복제본이 온라인 상태가 될 때 제거되었음을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6d195-153">If you specify a replica that is currently unavailable, when the replica comes online, it will discover that it has been removed.</span></span>  
  
 <span data-ttu-id="6d195-154">복제본을 제거하면 데이터 수신이 중지됩니다.</span><span class="sxs-lookup"><span data-stu-id="6d195-154">Removing a replica causes it to stop receiving data.</span></span> <span data-ttu-id="6d195-155">보조 복제본이 글로벌 상점에서 제거되었음을 확인한 후 이 복제본은 RECOVERING 상태에서 로컬 서버 인스턴스에 남아 있는 가용성 그룹 설정을 데이터베이스에서 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="6d195-155">After a secondary replica confirms that it has been removed from the global store, the replica removes the availability group settings from its databases, which remain on the local server instance in the RECOVERING state.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d195-156">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6d195-156">See Also</span></span>  
 <span data-ttu-id="6d195-157">[AlwaysOn 가용성 그룹 &#40;SQL Server 개요&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="6d195-157">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="6d195-158">[가용성 그룹 &#40;SQL Server에 보조 복제본을 추가&#41;](add-a-secondary-replica-to-an-availability-group-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="6d195-158">[Add a Secondary Replica to an Availability Group &#40;SQL Server&#41;](add-a-secondary-replica-to-an-availability-group-sql-server.md) </span></span>  
 [<span data-ttu-id="6d195-159">가용성 그룹 제거&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="6d195-159">Remove an Availability Group &#40;SQL Server&#41;</span></span>](remove-an-availability-group-sql-server.md)  
