---
title: 가용성 그룹 제거(SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.availabilitygroup.deleteag.f1
helpviewer_keywords:
- Availability Groups [SQL Server], removing
- Availability Groups [SQL Server], dropping
ms.assetid: 4b7f7f62-43a3-49db-a72e-22d4d7c2ddbb
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c17b7d5b362d8b4030d66ebf7ba0e425495410e7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648595"
---
# <a name="remove-an-availability-group-sql-server"></a><span data-ttu-id="5a481-102">가용성 그룹 제거(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="5a481-102">Remove an Availability Group (SQL Server)</span></span>
  <span data-ttu-id="5a481-103">이 항목에서는 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)] 또는 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]의 PowerShell을 사용하여 AlwaysOn 가용성 그룹을 삭제하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="5a481-103">This topic describes how to delete (drop) an AlwaysOn availability group by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)], or PowerShell in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="5a481-104">가용성 복제본 중 하나를 호스팅하는 서버 인스턴스가 오프라인 상태일 때 가용성 그룹을 삭제하면 나중에 서버 인스턴스가 온라인 상태가 되었을 때 서버 인스턴스에서 로컬 가용성 복제본을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="5a481-104">If a server instance that hosts one of the availability replicas is offline when you delete an availability group, after coming online, the server instance will drop the local availability replica.</span></span> <span data-ttu-id="5a481-105">가용성 그룹을 삭제하면 관련 가용성 그룹 수신기도 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="5a481-105">Dropping an availability group deletes any associated availability group listener.</span></span>  
  
 <span data-ttu-id="5a481-106">필요한 경우 가용성 그룹에 대한 올바른 보안 자격 증명이 있는 WSFC(Windows Server 장애 조치(Failover) 클러스터링) 노드에서 가용성 그룹을 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5a481-106">Note that, if necessary, you can drop an availability group from any Windows Server Failover Clustering (WSFC) node that possesses the correct security credentials for the availability group.</span></span> <span data-ttu-id="5a481-107">이렇게 하면 가용성 복제본이 더 이상 없을 때 가용성 그룹을 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5a481-107">This enables you to delete an availability group when none of its availability replicas remain.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="5a481-108">가능하면 주 복제본을 호스팅하는 서버 인스턴스에 연결되어 있는 동안에만 가용성 그룹을 제거하세요.</span><span class="sxs-lookup"><span data-stu-id="5a481-108">If possible, remove the availability group only while connected to the server instance that hosts the primary replica.</span></span> <span data-ttu-id="5a481-109">주 복제본에서 가용성 그룹을 제거하면 이전 주 데이터베이스에서 변경이 허용됩니다(고가용성 보호 없이).</span><span class="sxs-lookup"><span data-stu-id="5a481-109">When the availability group is dropped from the primary replica, changes are allowed in the former primary databases (without high availability protection).</span></span> <span data-ttu-id="5a481-110">보조 복제본에서 가용성 그룹을 삭제하면 주 복제본이 RESTORING 상태로 유지되고 데이터베이스에서 변경이 허용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5a481-110">Deleting an availability group from a secondary replica leaves the primary replica in the RESTORING state, and changes are not allowed on the databases.</span></span>  
  
-   <span data-ttu-id="5a481-111">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="5a481-111">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="5a481-112">제한 사항 및 권장 사항</span><span class="sxs-lookup"><span data-stu-id="5a481-112">Limitations and Recommendations</span></span>](#Restrictions)  
  
     [<span data-ttu-id="5a481-113">보안</span><span class="sxs-lookup"><span data-stu-id="5a481-113">Security</span></span>](#Security)  
  
-   <span data-ttu-id="5a481-114">**가용성 그룹을 삭제하려면:**</span><span class="sxs-lookup"><span data-stu-id="5a481-114">**To delete an availability group, using:**</span></span>  
  
     [<span data-ttu-id="5a481-115">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="5a481-115">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="5a481-116">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="5a481-116">Transact-SQL</span></span>](#TsqlProcedure)  
  
     [<span data-ttu-id="5a481-117">PowerShell</span><span class="sxs-lookup"><span data-stu-id="5a481-117">PowerShell</span></span>](#PowerShellProcedure)  
  
-   [<span data-ttu-id="5a481-118">관련 내용</span><span class="sxs-lookup"><span data-stu-id="5a481-118">Related Content</span></span>](#RelatedContent)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="5a481-119">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="5a481-119">Before You Begin</span></span>  
  
###  <a name="limitations-and-recommendations"></a><a name="Restrictions"></a><span data-ttu-id="5a481-120">제한 사항 및 권장 사항</span><span class="sxs-lookup"><span data-stu-id="5a481-120">Limitations and Recommendations</span></span>  
  
-   <span data-ttu-id="5a481-121">가용성 그룹이 온라인일 때 보조 복제본에서 이 그룹을 삭제하면 주 복제본이 RESTORING 상태로 전환됩니다.</span><span class="sxs-lookup"><span data-stu-id="5a481-121">When the availability group is online, deleting it from a secondary replica causes the primary replica to transition to the RESTORING state.</span></span> <span data-ttu-id="5a481-122">따라서 가능하면 주 복제본을 호스팅하는 서비스 인스턴스에서만 가용성 그룹을 제거하세요.</span><span class="sxs-lookup"><span data-stu-id="5a481-122">Therefore, if possible, remove the availability group only from the server instance that hosts the primary replica.</span></span>  
  
-   <span data-ttu-id="5a481-123">WSFC 장애 조치(failover) 클러스터에서 삭제되었거나 제거된 컴퓨터에서 가용성 그룹을 삭제하는 경우 가용성 그룹은 로컬 위치에서만 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="5a481-123">If you delete an availability group from a computer that has been removed or evicted from the WSFC failover cluster, the availability group is only deleted locally.</span></span>  
  
-   <span data-ttu-id="5a481-124">WSFC(Windows Server 장애 조치(Failover) 클러스터링) 클러스터에 쿼럼이 없을 때 가용성 그룹이 삭제되지 않도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="5a481-124">Avoid dropping an availability group when the Windows Server Failover Clustering (WSFC) cluster has no quorum.</span></span> <span data-ttu-id="5a481-125">클러스터에 쿼럼이 부족할 때 가용성 그룹을 삭제해야 하는 경우 클러스터에 저장된 메타데이터 가용성 그룹은 제거되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5a481-125">If you must drop an availability group while the cluster lacks quorum, the metadata availability group that is stored in the cluster is not removed.</span></span> <span data-ttu-id="5a481-126">클러스터가 쿼럼을 다시 얻은 후에는 가용성 그룹을 다시 삭제하여 WSFC 클러스터에서 제거해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5a481-126">After the cluster regains quorum, you will need to drop the availability group again to remove it from the WSFC cluster.</span></span>  
  
-   <span data-ttu-id="5a481-127">보조 복제본에서 DROP AVAILABILITY GROUP은 응급용으로만 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5a481-127">On a secondary replica, DROP AVAILABILITY GROUP should only be used only for emergency purposes.</span></span> <span data-ttu-id="5a481-128">이는 가용성 그룹을 삭제하면 가용성 그룹이 오프라인 상태로 전환되기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="5a481-128">This is because dropping an availability group takes the availability group offline.</span></span> <span data-ttu-id="5a481-129">보조 복제본에서 가용성 그룹을 삭제하면 주 복제본에서 쿼럼 손실, 강제 장애 조치(failover) 또는 DROP AVAILABILITY GROUP 명령으로 인해 OFFLINE 상태가 발생했는지 여부를 확인할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5a481-129">If you drop the availability group from a secondary replica, the primary replica cannot determine whether the OFFLINE state occurred because of quorum loss, a forced failover, or a DROP AVAILABILITY GROUP command.</span></span> <span data-ttu-id="5a481-130">주 복제본은 분리 장애(split-brain)가 발생하는 것을 방지하기 위해 RESTORING 상태로 전환됩니다.</span><span class="sxs-lookup"><span data-stu-id="5a481-130">The primary replica transitions to the RESTORING state to prevent a possible split-brain situation.</span></span> <span data-ttu-id="5a481-131">자세한 내용은 [작동 방식: DROP AVAILABILITY GROUP 동작](https://blogs.msdn.com/b/psssql/archive/2012/06/13/how-it-works-drop-availability-group-behaviors.aspx) (CSS SQL Server 엔지니어 블로그)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5a481-131">For more information, see [How It Works: DROP AVAILABILITY GROUP Behaviors](https://blogs.msdn.com/b/psssql/archive/2012/06/13/how-it-works-drop-availability-group-behaviors.aspx) (CSS SQL Server Engineers blog).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="5a481-132">보안</span><span class="sxs-lookup"><span data-stu-id="5a481-132">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="5a481-133">권한</span><span class="sxs-lookup"><span data-stu-id="5a481-133">Permissions</span></span>  
 <span data-ttu-id="5a481-134">가용성 그룹에 대한 ALTER AVAILABILITY GROUP 권한, CONTROL AVAILABILITY GROUP 권한, ALTER ANY AVAILABILITY GROUP 권한 또는 CONTROL SERVER 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="5a481-134">Requires ALTER AVAILABILITY GROUP permission on the availability group, CONTROL AVAILABILITY GROUP permission, ALTER ANY AVAILABILITY GROUP permission, or CONTROL SERVER permission.</span></span> <span data-ttu-id="5a481-135">로컬 서버 인스턴스에서 호스팅되지 않는 가용성 그룹을 삭제하려면 해당 가용성 그룹에 대한 CONTROL SERVER 권한이나 CONTROL 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="5a481-135">To drop an availability group that is not hosted by the local server instance you need CONTROL SERVER permission or CONTROL permission on that Availability Group.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="5a481-136">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="5a481-136">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="5a481-137">**가용성 그룹을 삭제하려면**</span><span class="sxs-lookup"><span data-stu-id="5a481-137">**To delete an availability group**</span></span>  
  
1.  <span data-ttu-id="5a481-138">개체 탐색기에서 주 복제본을 호스팅하는 서버 인스턴스에 연결하거나(가능한 경우) 가용성 그룹에 대한 올바른 보안 자격 증명을 소유한 WSFC 노드에 있으며 AlwaysOn 가용성 그룹을 사용하도록 설정된 다른 서버 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="5a481-138">In Object Explorer, connect to the server instance that hosts primary replica, if possible, or connect to another server instance that is enabled for AlwaysOn Availability Groups on a WSFC node that possess the correct security credentials for the availability group.</span></span> <span data-ttu-id="5a481-139">서버 트리를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="5a481-139">Expand the server tree.</span></span>  
  
2.  <span data-ttu-id="5a481-140">**AlwaysOn 고가용성** 및 **가용성 그룹** 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="5a481-140">Expand the **AlwaysOn High Availability** node and the **Availability Groups** node.</span></span>  
  
3.  <span data-ttu-id="5a481-141">이 단계는 여러 가용성 그룹을 삭제할지 아니면 가용성 그룹을 하나만 삭제할지에 따라 다음과 같이 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="5a481-141">This step depends on whether you want to delete multiple availability groups or only one availability group, as follows:</span></span>  
  
    -   <span data-ttu-id="5a481-142">주 복제본이 연결된 서버 인스턴스에 있는 가용성 그룹을 여러 개 삭제하려면 **개체 탐색기 정보** 창을 사용하여 삭제할 모든 가용성 그룹을 확인하고 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="5a481-142">To delete multiple availability groups (whose primary replicas are on the connected server instance), use the **Object Explorer Details** pane to view and select all the availability groups that you want to delete.</span></span> <span data-ttu-id="5a481-143">자세한 내용은 [개체 탐색기 정보를 사용하여 가용성 그룹 모니터링&#40;SQL Server Management Studio&#41;](use-object-explorer-details-to-monitor-availability-groups.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5a481-143">For more information, see [Use the Object Explorer Details to Monitor Availability Groups &#40;SQL Server Management Studio&#41;](use-object-explorer-details-to-monitor-availability-groups.md).</span></span>  
  
    -   <span data-ttu-id="5a481-144">단일 가용성 그룹을 삭제하려면 **개체 탐색기** 창 또는 **개체 탐색기 정보** 창에서 해당 가용성 그룹을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="5a481-144">To delete a single availability group, select it in either the **Object Explorer** pane or the **Object Explorer Details** pane.</span></span>  
  
4.  <span data-ttu-id="5a481-145">선택한 가용성 그룹을 마우스 오른쪽 단추로 클릭하고 **삭제** 명령을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="5a481-145">Right-click the selected availability group or groups, and select the **Delete** command.</span></span>  
  
5.  <span data-ttu-id="5a481-146">**가용성 그룹 제거** 대화 상자에서 나열된 가용성 그룹을 모두 삭제하려면 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5a481-146">In the **Remove Availability Group** dialog box, to delete all the listed availability groups, click **OK**.</span></span> <span data-ttu-id="5a481-147">나열된 모든 가용성 그룹을 제거하지 않으려면 **취소**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5a481-147">If you do not want to remove all the listed availability groups, click **Cancel**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="5a481-148">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="5a481-148">Using Transact-SQL</span></span>  
 <span data-ttu-id="5a481-149">**가용성 그룹을 삭제하려면**</span><span class="sxs-lookup"><span data-stu-id="5a481-149">**To delete an availability group**</span></span>  
  
1.  <span data-ttu-id="5a481-150">주 복제본을 호스팅하는 서버 인스턴스에 연결하거나(가능한 경우) 가용성 그룹에 대한 올바른 보안 자격 증명을 소유한 WSFC 노드에 있으며 AlwaysOn 가용성 그룹을 사용하도록 설정된 다른 서버 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="5a481-150">Connect to the server instance that hosts the primary replica, if possible, or connect to another server instance that is enabled for AlwaysOn Availability Groups on a WSFC node that possess the correct security credentials for the availability group.</span></span>  
  
2.  <span data-ttu-id="5a481-151">다음과 같이 [DROP AVAILABILITY GROUP](/sql/t-sql/statements/drop-availability-group-transact-sql) 문을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="5a481-151">Use the [DROP AVAILABILITY GROUP](/sql/t-sql/statements/drop-availability-group-transact-sql) statement, as follows</span></span>  
  
     <span data-ttu-id="5a481-152">DROP AVAILABILITY GROUP *group_name*</span><span class="sxs-lookup"><span data-stu-id="5a481-152">DROP AVAILABILITY GROUP *group_name*</span></span>  
  
     <span data-ttu-id="5a481-153">여기서 *group_name* 은 삭제할 가용성 그룹의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="5a481-153">where *group_name* is the name of the availability group to be dropped.</span></span>  
  
     <span data-ttu-id="5a481-154">다음 예에서는 `MyAG` 가용성 그룹을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="5a481-154">The following example deletes the `MyAG` availability group.</span></span>  
  
    ```sql
    DROP AVAILABILITY GROUP MyAG;  
    ```  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a> <span data-ttu-id="5a481-155">PowerShell 사용</span><span class="sxs-lookup"><span data-stu-id="5a481-155">Using PowerShell</span></span>  
 <span data-ttu-id="5a481-156">**가용성 그룹을 삭제하려면**</span><span class="sxs-lookup"><span data-stu-id="5a481-156">**To delete an availability group**</span></span>  
  
 <span data-ttu-id="5a481-157">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell 공급자에서 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="5a481-157">In the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell provider:</span></span>  
  
1.  <span data-ttu-id="5a481-158">디렉터리를 변경하여(`cd`) 주 복제본을 호스팅하는 서버 인스턴스에 연결하거나(가능한 경우) 가용성 그룹에 대한 올바른 보안 자격 증명을 소유한 WSFC 노드에 있으며 AlwaysOn 가용성 그룹을 사용하도록 설정된 다른 서버 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="5a481-158">Change directory (`cd`) to the server instance that hosts the primary replica, if possible, or connect to another server instance that is enabled for AlwaysOn Availability Groups on a WSFC node that possess the correct security credentials for the availability group.</span></span>  
  
2.  <span data-ttu-id="5a481-159">**Remove-SqlAvailabilityGroup** cmdlet을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="5a481-159">Use the **Remove-SqlAvailabilityGroup** cmdlet.</span></span>  
  
     <span data-ttu-id="5a481-160">예를 들어 다음 명령은 `MyAg`라는 가용성 그룹을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="5a481-160">For example, the following command removes the availability group named `MyAg`.</span></span> <span data-ttu-id="5a481-161">이 명령은 가용성 그룹에 대한 가용성 복제본을 호스팅하는 모든 서버 인스턴스에서 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5a481-161">This command can be executed on any server instance that hosts an availability replica for the availability group.</span></span>  
  
    ```powershell
    Remove-SqlAvailabilityGroup -Path SQLSERVER:\Sql\Computer\Instance\AvailabilityGroups\MyAg  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="5a481-162">cmdlet의 구문을 보려면 `Get-Help` PowerShell 환경에서 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] cmdlet을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="5a481-162">To view the syntax of a cmdlet, use the `Get-Help` cmdlet in the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell environment.</span></span> <span data-ttu-id="5a481-163">자세한 내용은 [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5a481-163">For more information, see [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).</span></span>  
  
 <span data-ttu-id="5a481-164">**SQL Server PowerShell 공급자를 설정하고 사용하려면**</span><span class="sxs-lookup"><span data-stu-id="5a481-164">**To set up and use the SQL Server PowerShell provider**</span></span>  
  
-   [<span data-ttu-id="5a481-165">SQL Server PowerShell 공급자</span><span class="sxs-lookup"><span data-stu-id="5a481-165">SQL Server PowerShell Provider</span></span>](../../../powershell/sql-server-powershell-provider.md)  
  
##  <a name="related-content"></a><a name="RelatedContent"></a> <span data-ttu-id="5a481-166">관련 내용</span><span class="sxs-lookup"><span data-stu-id="5a481-166">Related Content</span></span>  
  
-   <span data-ttu-id="5a481-167">[작동 방식: DROP AVAILABILITY GROUP 동작](https://blogs.msdn.com/b/psssql/archive/2012/06/13/how-it-works-drop-availability-group-behaviors.aspx) (CSS SQL Server 엔지니어 블로그)</span><span class="sxs-lookup"><span data-stu-id="5a481-167">[How It Works: DROP AVAILABILITY GROUP Behaviors](https://blogs.msdn.com/b/psssql/archive/2012/06/13/how-it-works-drop-availability-group-behaviors.aspx) (CSS SQL Server Engineers blog)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a481-168">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5a481-168">See Also</span></span>  
 <span data-ttu-id="5a481-169">[AlwaysOn 가용성 그룹 &#40;SQL Server 개요&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="5a481-169">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 [<span data-ttu-id="5a481-170">가용성 그룹의 생성 및 구성&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="5a481-170">Creation and Configuration of Availability Groups &#40;SQL Server&#41;</span></span>](creation-and-configuration-of-availability-groups-sql-server.md)  
