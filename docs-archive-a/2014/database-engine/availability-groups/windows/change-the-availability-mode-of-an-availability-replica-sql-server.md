---
title: 가용성 복제본의 가용성 모드 변경(SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], deploying
- Availability Groups [SQL Server], configuring
- Availability Groups [SQL Server], availability modes
ms.assetid: c4da8f25-fb1b-45a4-8bf2-195df6df634c
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 1636f3ea86e083e47276423b120dbc8d3744d387
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741328"
---
# <a name="change-the-availability-mode-of-an-availability-replica-sql-server"></a><span data-ttu-id="ce5f9-102">가용성 복제본의 가용성 모드 변경(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="ce5f9-102">Change the Availability Mode of an Availability Replica (SQL Server)</span></span>
  <span data-ttu-id="ce5f9-103">이 항목에서는 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 에서 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)]또는 PowerShell을 사용하여 AlwaysOn 가용성 그룹의 가용성 복제본에 대한 가용성 모드를 변경하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="ce5f9-103">This topic describes how to change the availability mode of an availability replica in an AlwaysOn availability group in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)], or PowerShell.</span></span> <span data-ttu-id="ce5f9-104">가용성 모드는 복제본이 비동기적 또는 동기적으로 커밋되는지 여부를 제어하는 복제본 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="ce5f9-104">The availability mode is a replica property that controls the whether the replica commits asynchronously or synchronously.</span></span> <span data-ttu-id="ce5f9-105">*비동기-커밋 모드* 는 성능을 극대화하지만 가용성이 저하되며 *강제 장애 조치(failover)* 라고 하는 강제 수동 장애 조치(failover)만 지원하여 데이터가 손실될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ce5f9-105">*Asynchronous-commit mode* maximizes performance at the expense of high availability and supports only forced manual failover (with possible data loss), typically called *forced failover*.</span></span> <span data-ttu-id="ce5f9-106">*동기-커밋 모드* 는 성능에 비해 고가용성을 강조하고 보조 복제본이 동기화되면 수동 장애 조치(failover)를 지원하고 자동 장애 조치(failover)를 선택적으로 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="ce5f9-106">*Synchronous-commit mode* emphasizes high availability over performance and, once the secondary replica is synchronized, supports manual failover and, optionally, automatic failover.</span></span>  
  

  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="ce5f9-107">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="ce5f9-107">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="ce5f9-108">필수 조건</span><span class="sxs-lookup"><span data-stu-id="ce5f9-108">Prerequisites</span></span>  
  
-   <span data-ttu-id="ce5f9-109">주 복제본을 호스팅하는 서버 인스턴스에 연결되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce5f9-109">You must be connected to the server instance that hosts the primary replica.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="ce5f9-110">보안</span><span class="sxs-lookup"><span data-stu-id="ce5f9-110">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="ce5f9-111">권한</span><span class="sxs-lookup"><span data-stu-id="ce5f9-111">Permissions</span></span>  
 <span data-ttu-id="ce5f9-112">가용성 그룹에 대한 ALTER AVAILABILITY GROUP 권한, CONTROL AVAILABILITY GROUP 권한, ALTER ANY AVAILABILITY GROUP 권한 또는 CONTROL SERVER 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="ce5f9-112">Requires ALTER AVAILABILITY GROUP permission on the availability group, CONTROL AVAILABILITY GROUP permission, ALTER ANY AVAILABILITY GROUP permission, or CONTROL SERVER permission.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="ce5f9-113">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="ce5f9-113">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="ce5f9-114">**가용성 그룹의 가용성 모드를 변경하려면**</span><span class="sxs-lookup"><span data-stu-id="ce5f9-114">**To change the availability mode of an availability group**</span></span>  
  
1.  <span data-ttu-id="ce5f9-115">개체 탐색기에서 주 복제본을 호스팅하는 서버 인스턴스에 연결하고 서버 트리를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="ce5f9-115">In Object Explorer, connect to the server instance that hosts the primary replica, and expand the server tree.</span></span>  
  
2.  <span data-ttu-id="ce5f9-116">**AlwaysOn 고가용성** 및 **가용성 그룹** 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="ce5f9-116">Expand the **AlwaysOn High Availability** node and the **Availability Groups** node.</span></span>  
  
3.  <span data-ttu-id="ce5f9-117">복제본을 변경할 가용성 그룹을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ce5f9-117">Click the availability group whose replica you want to change.</span></span>  
  
4.  <span data-ttu-id="ce5f9-118">복제본을 마우스 오른쪽 단추로 클릭하고 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ce5f9-118">Right-click the replica, and click **Properties**.</span></span>  
  
5.  <span data-ttu-id="ce5f9-119">**가용성 복제본 속성** 대화 상자에서 **가용성 모드** 드롭 목록을 사용하여 이 복제본의 가용성 모드를 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="ce5f9-119">In the **Availability Replica Properties** dialog box, use the **Availability mode** drop list to change the availability mode of this replica.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="ce5f9-120">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="ce5f9-120">Using Transact-SQL</span></span>  
 <span data-ttu-id="ce5f9-121">**가용성 그룹의 가용성 모드를 변경하려면**</span><span class="sxs-lookup"><span data-stu-id="ce5f9-121">**To change the availability mode of an availability group**</span></span>  
  
1.  <span data-ttu-id="ce5f9-122">주 복제본을 호스팅하는 서버 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="ce5f9-122">Connect to the server instance that hosts the primary replica.</span></span>  
  
2.  <span data-ttu-id="ce5f9-123">다음과 같은 [ALTER AVAILABILITY GROUP](/sql/t-sql/statements/alter-availability-group-transact-sql) 문을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="ce5f9-123">Use the [ALTER AVAILABILITY GROUP](/sql/t-sql/statements/alter-availability-group-transact-sql) statement, as follows:</span></span>  
  
     <span data-ttu-id="ce5f9-124">ALTER AVAILABILITY GROUP *group_name* MODIFY REPLICA ON '*server_name*'</span><span class="sxs-lookup"><span data-stu-id="ce5f9-124">ALTER AVAILABILITY GROUP *group_name* MODIFY REPLICA ON '*server_name*'</span></span>  
  
     <span data-ttu-id="ce5f9-125">WITH ( {</span><span class="sxs-lookup"><span data-stu-id="ce5f9-125">WITH ( {</span></span>  
  
     <span data-ttu-id="ce5f9-126">AVAILABILITY_MODE = { SYNCHRONOUS_COMMIT | ASYNCHRONOUS_COMMIT }</span><span class="sxs-lookup"><span data-stu-id="ce5f9-126">AVAILABILITY_MODE = { SYNCHRONOUS_COMMIT | ASYNCHRONOUS_COMMIT }</span></span>  
  
     <span data-ttu-id="ce5f9-127">| FAILOVER_MODE = { AUTOMATIC | MANUAL }</span><span class="sxs-lookup"><span data-stu-id="ce5f9-127">| FAILOVER_MODE = { AUTOMATIC | MANUAL }</span></span>  
  
     <span data-ttu-id="ce5f9-128">} )</span><span class="sxs-lookup"><span data-stu-id="ce5f9-128">} )</span></span>  
  
     <span data-ttu-id="ce5f9-129">여기서 *group_name* 은 가용성 그룹의 이름이 고 *server_name* 은 수정할 복제본을 호스팅하는 서버 인스턴스의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="ce5f9-129">where *group_name* is the name of the availability group and *server_name* is the name of the server instance that hosts the replica to be modified.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="ce5f9-130">FAILOVER_MODE = AUTOMATIC은 AVAILABILITY_MODE = SYNCHRONOUS_COMMIT을 지정한 경우에만 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="ce5f9-130">FAILOVER_MODE = AUTOMATIC is supported only if you also specify AVAILABILITY_MODE = SYNCHRONOUS_COMMIT.</span></span>  
  
     <span data-ttu-id="ce5f9-131">`AccountsAG` 가용성 그룹의 주 복제본에 입력된 다음 예는 `INSTANCE09` 서버 인스턴스에 호스팅된 복제본에 대해 가용성 및 장애 조치(failover) 모드를 동기 커밋 및 자동 장애 조치(failover)로 각각 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="ce5f9-131">The following example, entered on the primary replica of the `AccountsAG` availability group, changes the availability and failover modes to synchronous commit and automatic failover, respectively, for the replica hosted by the `INSTANCE09` server instance.</span></span>  
  
    ```  
  
    ALTER AVAILABILITY GROUP AccountsAG MODIFY REPLICA ON 'INSTANCE09'  
       WITH (AVAILABILITY_MODE = SYNCHRONOUS_COMMIT);  
    ALTER AVAILABILITY GROUP AccountsAG MODIFY REPLICA ON 'INSTANCE09'  
       WITH (FAILOVER_MODE = AUTOMATIC);  
    ```  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a> <span data-ttu-id="ce5f9-132">PowerShell 사용</span><span class="sxs-lookup"><span data-stu-id="ce5f9-132">Using PowerShell</span></span>

### <a name="to-change-the-availability-mode-of-an-availability-group"></a><span data-ttu-id="ce5f9-133">가용성 그룹의 가용성 모드를 변경하려면</span><span class="sxs-lookup"><span data-stu-id="ce5f9-133">To change the availability mode of an availability group</span></span>
  
1.  <span data-ttu-id="ce5f9-134">주 복제본을 호스팅하는 서버 인스턴스로 디렉터리를 변경(`cd`)합니다.</span><span class="sxs-lookup"><span data-stu-id="ce5f9-134">Change directory (`cd`) to the server instance that hosts the primary replica.</span></span>  
  
2.  <span data-ttu-id="ce5f9-135">`Set-SqlAvailabilityReplica` cmdlet을 `AvailabilityMode` 매개 변수 및 `FailoverMode` 매개 변수(옵션)와 함께 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="ce5f9-135">Use the `Set-SqlAvailabilityReplica` cmdlet with the `AvailabilityMode` parameter and, optionally, the `FailoverMode` parameter.</span></span>  
  
     <span data-ttu-id="ce5f9-136">예를 들어 다음 명령은 `MyReplica` 가용성 그룹의 `MyAg` 복제본이 동기-커밋 가용성 모드를 사용하고 자동 장애 조치(failover)를 지원하도록 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="ce5f9-136">For example, the following command modifies the replica `MyReplica` in the availability group `MyAg` to use synchronous-commit availability mode and to support automatic failover.</span></span>  
  
    ```powershell
    Set-SqlAvailabilityReplica -AvailabilityMode "SynchronousCommit" -FailoverMode "Automatic" `   
     -Path SQLSERVER:\Sql\PrimaryServer\InstanceName\AvailabilityGroups\MyAg\AvailabilityReplicas\MyReplica  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="ce5f9-137">cmdlet의 구문을 보려면 `Get-Help` PowerShell 환경에서 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] cmdlet을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="ce5f9-137">To view the syntax of a cmdlet, use the `Get-Help` cmdlet in the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell environment.</span></span> <span data-ttu-id="ce5f9-138">자세한 내용은 [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ce5f9-138">For more information, see [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).</span></span>  
  
<span data-ttu-id="ce5f9-139">SQL Server PowerShell 공급자를 설정 하 고 사용 하려면 [SQL Server PowerShell 공급자](../../../powershell/sql-server-powershell-provider.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ce5f9-139">To set up and use the SQL Server PowerShell provider, see [SQL Server PowerShell Provider](../../../powershell/sql-server-powershell-provider.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="ce5f9-140">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ce5f9-140">See Also</span></span>  
 <span data-ttu-id="ce5f9-141">[AlwaysOn 가용성 그룹 &#40;SQL Server 개요&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="ce5f9-141">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="ce5f9-142">[가용성 모드 (AlwaysOn 가용성 그룹)](availability-modes-always-on-availability-groups.md) </span><span class="sxs-lookup"><span data-stu-id="ce5f9-142">[Availability Modes (AlwaysOn Availability Groups)](availability-modes-always-on-availability-groups.md) </span></span>  
 [<span data-ttu-id="ce5f9-143">장애 조치 (failover) 및 장애 조치 (failover) 모드 &#40;AlwaysOn 가용성 그룹&#41;</span><span class="sxs-lookup"><span data-stu-id="ce5f9-143">Failover and Failover Modes &#40;AlwaysOn Availability Groups&#41;</span></span>](failover-and-failover-modes-always-on-availability-groups.md)  
