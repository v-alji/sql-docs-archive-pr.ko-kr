---
title: 가용성 복제본의 장애 조치 모드 변경(SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- failover modes [SQL Server]
- Availability Groups [SQL Server], deploying
- Availability Groups [SQL Server], failover modes
- Availability Groups [SQL Server], configuring
ms.assetid: 619a826f-8e65-48eb-8c34-39497d238279
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: d946440e2950192299c42652babb4082790dbd03
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741319"
---
# <a name="change-the-failover-mode-of-an-availability-replica-sql-server"></a><span data-ttu-id="e89b4-102">가용성 복제본의 장애 조치(failover) 모드 변경(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="e89b4-102">Change the Failover Mode of an Availability Replica (SQL Server)</span></span>
  <span data-ttu-id="e89b4-103">이 항목에서는 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 에서 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)]또는 PowerShell을 사용하여 AlwaysOn 가용성 그룹의 가용성 복제본에 대한 장애 조치(failover) 모드를 변경하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="e89b4-103">This topic describes how to change the failover mode of an availability replica in an AlwaysOn availability group in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)], or PowerShell.</span></span> <span data-ttu-id="e89b4-104">장애 조치(failover) 모드는 동기-커밋 가용성 모드에서 실행되는 복제본에 대한 장애 조치(failover) 모드를 결정하는 복제본 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="e89b4-104">The failover mode is a replica property that determines the failover mode for replicas that run under synchronous-commit availability mode.</span></span> <span data-ttu-id="e89b4-105">자세한 내용은 [장애 조치(Failover) 및 장애 조치(Failover) 모드&#40;AlwaysOn 가용성 그룹&#41;](failover-and-failover-modes-always-on-availability-groups.md) 및 [가용성 모드&#40;AlwaysOn 가용성 그룹&#41;](availability-modes-always-on-availability-groups.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e89b4-105">For more information, see [Failover and Failover Modes &#40;AlwaysOn Availability Groups&#41;](failover-and-failover-modes-always-on-availability-groups.md) and [Availability Modes &#40;AlwaysOn Availability Groups&#41;](availability-modes-always-on-availability-groups.md).</span></span>  
  

  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="e89b4-106">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="e89b4-106">Before You Begin</span></span>  
  
###  <a name="prerequisites-and-restrictions"></a><a name="Prerequisites"></a> <span data-ttu-id="e89b4-107">사전 요구 사항 및 제한 사항</span><span class="sxs-lookup"><span data-stu-id="e89b4-107">Prerequisites and Restrictions</span></span>  
  
-   <span data-ttu-id="e89b4-108">이 태스크는 주 복제본에서만 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="e89b4-108">This task is supported only on primary replicas.</span></span> <span data-ttu-id="e89b4-109">주 복제본을 호스팅하는 서버 인스턴스에 연결되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e89b4-109">You must be connected to the server instance that hosts the primary replica.</span></span>  
  
-   <span data-ttu-id="e89b4-110">SQL Server FCI(장애 조치(Failover) 클러스터 인스턴스)는 가용성 그룹에 따라 AlwaysOn 자동 장애 조치(Failover)를 지원하지 않으므로 FCI에서 호스팅하는 모든 가용성 복제본은 수동 장애 조치(Failover)에 대해서만 구성될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e89b4-110">SQL Server Failover Cluster Instances (FCIs) do not support automatic failover by availability groups, so any availability replica that is hosted by an FCI can only be configured for manual failover.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="e89b4-111">보안</span><span class="sxs-lookup"><span data-stu-id="e89b4-111">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="e89b4-112">권한</span><span class="sxs-lookup"><span data-stu-id="e89b4-112">Permissions</span></span>  
 <span data-ttu-id="e89b4-113">가용성 그룹에 대한 ALTER AVAILABILITY GROUP 권한, CONTROL AVAILABILITY GROUP 권한, ALTER ANY AVAILABILITY GROUP 권한 또는 CONTROL SERVER 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="e89b4-113">Requires ALTER AVAILABILITY GROUP permission on the availability group, CONTROL AVAILABILITY GROUP permission, ALTER ANY AVAILABILITY GROUP permission, or CONTROL SERVER permission.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="e89b4-114">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="e89b4-114">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="e89b4-115">**가용성 복제본의 장애 조치(failover) 모드를 변경하려면**</span><span class="sxs-lookup"><span data-stu-id="e89b4-115">**To change the failover mode of an availability replica**</span></span>  
  
1.  <span data-ttu-id="e89b4-116">개체 탐색기에서 주 복제본을 호스팅하는 서버 인스턴스에 연결하고 서버 트리를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="e89b4-116">In Object Explorer, connect to the server instance that hosts the primary replica, and expand the server tree.</span></span>  
  
2.  <span data-ttu-id="e89b4-117">**AlwaysOn 고가용성** 및 **가용성 그룹** 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="e89b4-117">Expand the **AlwaysOn High Availability** node and the **Availability Groups** node.</span></span>  
  
3.  <span data-ttu-id="e89b4-118">복제본을 변경할 가용성 그룹을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e89b4-118">Click the availability group whose replica you want to change.</span></span>  
  
4.  <span data-ttu-id="e89b4-119">복제본을 마우스 오른쪽 단추로 클릭하고 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e89b4-119">Right-click the replica, and click **Properties**.</span></span>  
  
5.  <span data-ttu-id="e89b4-120">**가용성 복제본 속성** 대화 상자에서 **장애 조치(failover) 모드** 드롭 목록을 사용하여 이 복제본의 장애 조치(failover) 모드를 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="e89b4-120">In the **Availability Replica Properties** dialog box, use the **Failover mode** drop list to change the failover mode of this replica.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="e89b4-121">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="e89b4-121">Using Transact-SQL</span></span>  
 <span data-ttu-id="e89b4-122">**가용성 복제본의 장애 조치(failover) 모드를 변경하려면**</span><span class="sxs-lookup"><span data-stu-id="e89b4-122">**To change the failover mode of an availability replica**</span></span>  
  
1.  <span data-ttu-id="e89b4-123">주 복제본을 호스팅하는 서버 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="e89b4-123">Connect to the server instance that hosts the primary replica.</span></span>  
  
2.  <span data-ttu-id="e89b4-124">다음과 같은 [ALTER AVAILABILITY GROUP](/sql/t-sql/statements/alter-availability-group-transact-sql) 문을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="e89b4-124">Use the [ALTER AVAILABILITY GROUP](/sql/t-sql/statements/alter-availability-group-transact-sql) statement, as follows:</span></span>  
  
     <span data-ttu-id="e89b4-125">ALTER AVAILABILITY GROUP *group_name* MODIFY REPLICA ON '*server_name*'</span><span class="sxs-lookup"><span data-stu-id="e89b4-125">ALTER AVAILABILITY GROUP *group_name* MODIFY REPLICA ON '*server_name*'</span></span>  
  
     <span data-ttu-id="e89b4-126">WITH ( {</span><span class="sxs-lookup"><span data-stu-id="e89b4-126">WITH ( {</span></span>  
  
     <span data-ttu-id="e89b4-127">AVAILABILITY_MODE = { SYNCHRONOUS_COMMIT | ASYNCHRONOUS_COMMIT }</span><span class="sxs-lookup"><span data-stu-id="e89b4-127">AVAILABILITY_MODE = { SYNCHRONOUS_COMMIT | ASYNCHRONOUS_COMMIT }</span></span>  
  
     <span data-ttu-id="e89b4-128">| FAILOVER_MODE = { AUTOMATIC | MANUAL }</span><span class="sxs-lookup"><span data-stu-id="e89b4-128">| FAILOVER_MODE = { AUTOMATIC | MANUAL }</span></span>  
  
     <span data-ttu-id="e89b4-129">}  )</span><span class="sxs-lookup"><span data-stu-id="e89b4-129">}  )</span></span>  
  
     <span data-ttu-id="e89b4-130">라는 설치 관리자 실행 파일에 포함됩니다. 여기서</span><span class="sxs-lookup"><span data-stu-id="e89b4-130">where</span></span>  
  
    -   <span data-ttu-id="e89b4-131">*group_name* 은 가용성 그룹의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="e89b4-131">*group_name* is the name of the availability group.</span></span>  
  
    -   <span data-ttu-id="e89b4-132">{ '*system_name*[\\*instance_name*]' | '*FCI_network_name*[\\*instance_name*]' }</span><span class="sxs-lookup"><span data-stu-id="e89b4-132">{ '*system_name*[\\*instance_name*]' | '*FCI_network_name*[\\*instance_name*]' }</span></span>  
  
         <span data-ttu-id="e89b4-133">변경할 가용성 그룹을 호스팅하는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 의 인스턴스 주소를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e89b4-133">Specifies the address of the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] that hosts the availability replica to be altered.</span></span> <span data-ttu-id="e89b4-134">이 주소의 구성 요소는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="e89b4-134">The components of this address are as follows:</span></span>  
  
         <span data-ttu-id="e89b4-135">*system_name*</span><span class="sxs-lookup"><span data-stu-id="e89b4-135">*system_name*</span></span>  
         <span data-ttu-id="e89b4-136">독립 실행형 서버 인스턴스가 있는 컴퓨터 시스템의 NetBIOS 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="e89b4-136">Is the NetBIOS name of the computer system on which a stand-alone server instance resides.</span></span>  
  
         <span data-ttu-id="e89b4-137">*FCI_network_name*</span><span class="sxs-lookup"><span data-stu-id="e89b4-137">*FCI_network_name*</span></span>  
         <span data-ttu-id="e89b4-138">대상 서버 인스턴스가 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 장애 조치(Failover) 파트너(FCI)인 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 장애 조치(Failover) 클러스터에 액세스하는 데 사용되는 네트워크 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="e89b4-138">Is the network name that is used to access a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] failover cluster in which a target server instance is a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] failover partner (an FCI).</span></span>  
  
         <span data-ttu-id="e89b4-139">*instance_name*</span><span class="sxs-lookup"><span data-stu-id="e89b4-139">*instance_name*</span></span>  
         <span data-ttu-id="e89b4-140">대상 가용성 복제본을 호스팅하는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 의 인스턴스 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="e89b4-140">Is the name of the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] that hosts the target availability replica.</span></span> <span data-ttu-id="e89b4-141">기본 서버 인스턴스의 경우 *instance_name* 은 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="e89b4-141">For a default server instance, *instance_name* is optional.</span></span>  
  
     <span data-ttu-id="e89b4-142">이러한 매개 변수에 대한 자세한 내용은 [ALTER AVAILABILITY GROUP&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-availability-group-transact-sql)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e89b4-142">For more information about these parameters, see [ALTER AVAILABILITY GROUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-availability-group-transact-sql).</span></span>  
  
     <span data-ttu-id="e89b4-143">*MyAG* 가용성 그룹의 주 복제본에 입력된 다음 예는 *COMPUTER01*컴퓨터의 기본 서버 인스턴스에 있는 가용성 복제본에서 장애 조치(failover) 모드를 자동 장애 조치(failover)로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="e89b4-143">The following example, entered on the primary replica of the *MyAG* availability group, changes the failover mode to automatic failover on the availability replica that is located on the default server instance on a computer named *COMPUTER01*.</span></span>  
  
    ```  
    ALTER AVAILABILITY GROUP MyAG MODIFY REPLICA ON 'COMPUTER01' WITH  
       (FAILOVER_MODE = AUTOMATIC);  
    ```  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a> <span data-ttu-id="e89b4-144">PowerShell 사용</span><span class="sxs-lookup"><span data-stu-id="e89b4-144">Using PowerShell</span></span>  

### <a name="to-change-the-failover-mode-of-an-availability-replica"></a><span data-ttu-id="e89b4-145">가용성 복제본의 장애 조치(failover) 모드를 변경하려면</span><span class="sxs-lookup"><span data-stu-id="e89b4-145">To change the failover mode of an availability replica</span></span>
  
1.  <span data-ttu-id="e89b4-146">주 복제본을 호스팅하는 서버 인스턴스로 디렉터리를 변경(`cd`)합니다.</span><span class="sxs-lookup"><span data-stu-id="e89b4-146">Change directory (`cd`) to the server instance that hosts the primary replica.</span></span>  
  
2.  <span data-ttu-id="e89b4-147">`Set-SqlAvailabilityReplica` cmdlet을 `FailoverMode` 매개 변수와 함께 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="e89b4-147">Use the `Set-SqlAvailabilityReplica` cmdlet with the `FailoverMode` parameter.</span></span> <span data-ttu-id="e89b4-148">복제본을 자동 장애 조치(failover)로 설정할 때는 `AvailabilityMode` 매개 변수를 사용하여 복제본을 동기-커밋 가용성 모드로 변경해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e89b4-148">When setting a replica to automatic failover, you might need to use the `AvailabilityMode` parameter to change the replica to synchronous-commit availability mode.</span></span>  
  
     <span data-ttu-id="e89b4-149">예를 들어 다음 명령은 `MyReplica` 가용성 그룹의 `MyAg` 복제본이 동기-커밋 가용성 모드를 사용하고 자동 장애 조치(failover)를 지원하도록 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="e89b4-149">For example, the following command modifies the replica `MyReplica` in the availability group `MyAg` to use synchronous-commit availability mode and to support automatic failover.</span></span>  
  
    ```powershell
    Set-SqlAvailabilityReplica -AvailabilityMode "SynchronousCommit" -FailoverMode "Automatic" `
     -Path SQLSERVER:\Sql\PrimaryServer\InstanceName\AvailabilityGroups\MyAg\Replicas\MyReplica  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="e89b4-150">cmdlet의 구문을 보려면 `Get-Help` PowerShell 환경에서 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] cmdlet을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="e89b4-150">To view the syntax of a cmdlet, use the `Get-Help` cmdlet in the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell environment.</span></span> <span data-ttu-id="e89b4-151">자세한 내용은 [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e89b4-151">For more information, see [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).</span></span>  
  
<span data-ttu-id="e89b4-152">SQL Server PowerShell 공급자를 설정 하 고 사용 하려면 [SQL Server PowerShell 공급자](../../../powershell/sql-server-powershell-provider.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="e89b4-152">To set up and use the SQL Server PowerShell provider, see [SQL Server PowerShell Provider](../../../powershell/sql-server-powershell-provider.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="e89b4-153">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e89b4-153">See Also</span></span>  
 [<span data-ttu-id="e89b4-154">AlwaysOn 가용성 그룹 &#40;SQL Server 개요&#41;</span><span class="sxs-lookup"><span data-stu-id="e89b4-154">Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](overview-of-always-on-availability-groups-sql-server.md)  
 <span data-ttu-id="e89b4-155">[가용성 모드 &#40;AlwaysOn 가용성 그룹&#41;](availability-modes-always-on-availability-groups.md) </span><span class="sxs-lookup"><span data-stu-id="e89b4-155">[Availability Modes &#40;AlwaysOn Availability Groups&#41;](availability-modes-always-on-availability-groups.md) </span></span>  
 [<span data-ttu-id="e89b4-156">장애 조치 (failover) 및 장애 조치 (failover) 모드 &#40;AlwaysOn 가용성 그룹&#41;</span><span class="sxs-lookup"><span data-stu-id="e89b4-156">Failover and Failover Modes &#40;AlwaysOn Availability Groups&#41;</span></span>](failover-and-failover-modes-always-on-availability-groups.md) 
