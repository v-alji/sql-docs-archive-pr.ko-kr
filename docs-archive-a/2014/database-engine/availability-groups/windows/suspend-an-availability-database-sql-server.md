---
title: 가용성 데이터베이스 일시 중단(SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.availabilitygroup.suspenddatamove.f1
helpviewer_keywords:
- secondary databases [SQL Server], in availability group
- primary databases [SQL Server], in availability group
- Availability Groups [SQL Server], suspending a database
- Availability Groups [SQL Server], databases
ms.assetid: 86858982-6af1-4e80-9a93-87451f0d7ee9
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 49afe868a509f84160fc1ad154135e8e67f6900a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741288"
---
# <a name="suspend-an-availability-database-sql-server"></a><span data-ttu-id="d4d41-102">가용성 데이터베이스 일시 중지(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="d4d41-102">Suspend an Availability Database (SQL Server)</span></span>
  <span data-ttu-id="d4d41-103">[!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 의 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)]또는 PowerShell을 사용하여 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]에서 가용성 데이터베이스를 일시 중지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d4d41-103">You can suspend an availability database in [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)], or PowerShell in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="d4d41-104">일시 중지하거나 재개할 데이터베이스를 호스팅하는 서버 인스턴스에서 일시 중지 명령을 실행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d4d41-104">Note that a suspend command needs to be issued on the server instance that hosts the database to be suspended or resumed.</span></span>  
  
 <span data-ttu-id="d4d41-105">일시 중지 명령의 효과는 일시 중지하는 데이터베이스가 보조 데이터베이스인지 주 데이터베이스인지에 따라 다음과 같이 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="d4d41-105">The effect of a suspend command depends on whether you suspend a secondary database or a primary database, as follows:</span></span>  
  
|<span data-ttu-id="d4d41-106">일시 중지된 데이터베이스</span><span class="sxs-lookup"><span data-stu-id="d4d41-106">Suspended Database</span></span>|<span data-ttu-id="d4d41-107">일시 중지 명령의 효과</span><span class="sxs-lookup"><span data-stu-id="d4d41-107">Effect of Suspend Command</span></span>|  
|------------------------|-------------------------------|  
|<span data-ttu-id="d4d41-108">보조 데이터베이스</span><span class="sxs-lookup"><span data-stu-id="d4d41-108">Secondary database</span></span>|<span data-ttu-id="d4d41-109">로컬 보조 데이터베이스만 일시 중지되고 동기화 상태가 NOT SYNCHRONIZING이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d4d41-109">Only the local secondary database is suspended and its synchronization state becomes NOT SYNCHRONIZING.</span></span> <span data-ttu-id="d4d41-110">다른 보조 데이터베이스는 영향을 받지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d4d41-110">Other secondary databases are not affected.</span></span> <span data-ttu-id="d4d41-111">일시 중지된 데이터베이스는 데이터(로그 레코드)의 수신과 적용을 중지하고 주 데이터베이스보다 뒤처지기 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="d4d41-111">The suspended database stops receiving and applying data (log records) and begins to fall behind the primary database.</span></span> <span data-ttu-id="d4d41-112">읽기 가능한 보조 복제본에 대한 기존 연결은 계속 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d4d41-112">Existing connections on the readable secondary remain usable.</span></span> <span data-ttu-id="d4d41-113">읽기 가능한 보조 복제본의 일시 중단된 데이터베이스에 대한 새 연결은 데이터 이동이 다시 시작될 때까지 허용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d4d41-113">New connections to the suspended database on the readable secondary are not allowed until data movement is resumed.</span></span><br /><br /> <span data-ttu-id="d4d41-114">주 데이터베이스는 사용 가능한 상태로 남아 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d4d41-114">The primary database remains available.</span></span> <span data-ttu-id="d4d41-115">각각의 해당 보조 데이터베이스를 중지하면 주 데이터베이스가 노출된 상태로 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="d4d41-115">If you suspend each of the corresponding secondary databases, the primary database runs exposed.</span></span><br /><br /> <span data-ttu-id="d4d41-116">**\*\* 중요 \*\*** 보조 데이터베이스를 일시 중지하면 해당 주 데이터베이스의 큐 보내기에서 보내지 않은 트랜잭션 로그 레코드를 누적합니다.</span><span class="sxs-lookup"><span data-stu-id="d4d41-116">**\*\* Important \*\*** While a secondary database is suspended, the send queue of the corresponding primary database will accumulate unsent transaction log records.</span></span> <span data-ttu-id="d4d41-117">보조 복제본에 대한 연결은 데이터 이동이 일시 중단된 시간에 사용 가능했던 데이터를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="d4d41-117">Connections to the secondary replica return data that was available at the time the data movement was suspended.</span></span>|  
|<span data-ttu-id="d4d41-118">주 데이터베이스</span><span class="sxs-lookup"><span data-stu-id="d4d41-118">Primary database</span></span>|<span data-ttu-id="d4d41-119">주 데이터베이스는 연결된 모든 보조 데이터베이스로의 데이터 이동을 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="d4d41-119">The primary database stops data movement to every connected secondary database.</span></span> <span data-ttu-id="d4d41-120">주 데이터베이스는 계속해서 노출된 모드에서 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="d4d41-120">The primary database continues running, in an exposed mode.</span></span> <span data-ttu-id="d4d41-121">클라이언트에서 주 데이터베이스를 계속해서 사용할 수 있고 읽을 수 있는 보조 데이터베이스의 기존 연결을 계속해서 사용할 수 있으며 새로운 연결을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d4d41-121">The primary database remains available to clients, and existing connections on a readable secondary remain usable and new connections can be made.</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="d4d41-122">AlwaysOn 보조 데이터베이스를 일시 중지해도 주 데이터베이스의 가용성에 직접 영향을 주지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d4d41-122">Suspending an AlwaysOn secondary database does not directly affect the availability of the primary database.</span></span> <span data-ttu-id="d4d41-123">그러나 보조 데이터베이스를 일시 중지하면 주 데이터베이스의 중복 및 장애 조치(failover) 기능에 영향을 줄 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d4d41-123">However, suspending a secondary database can impact redundancy and failover capabilities for the primary database.</span></span> <span data-ttu-id="d4d41-124">이것은 데이터베이스 미러링과는 대조적입니다. 데이터베이스 미러링의 경우에는 미러 데이터베이스 및 주 데이터베이스에서 미러링 상태가 일시 중지됩니다.</span><span class="sxs-lookup"><span data-stu-id="d4d41-124">This is in contrast to database mirroring, where the mirroring state is suspended on both the mirror database and the principal database.</span></span> <span data-ttu-id="d4d41-125">AlwaysOn 주 데이터베이스를 일시 중지하면 모든 해당 보조 데이터베이스에서 데이터 이동이 일시 중지되고 주 데이터베이스를 재개할 때까지 해당 데이터베이스에 대한 중복 및 장애 조치(failover) 기능이 중단됩니다.</span><span class="sxs-lookup"><span data-stu-id="d4d41-125">Suspending an AlwaysOn primary database suspends data movement on all the corresponding secondary databases, and redundancy and failover capabilities cease for that database until the primary database is resumed.</span></span>  
  
-   <span data-ttu-id="d4d41-126">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="d4d41-126">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="d4d41-127">제한 사항</span><span class="sxs-lookup"><span data-stu-id="d4d41-127">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="d4d41-128">필수 구성 요소</span><span class="sxs-lookup"><span data-stu-id="d4d41-128">Prerequisites</span></span>](#Prerequisites)  
  
     [<span data-ttu-id="d4d41-129">권장 사항</span><span class="sxs-lookup"><span data-stu-id="d4d41-129">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="d4d41-130">보안</span><span class="sxs-lookup"><span data-stu-id="d4d41-130">Security</span></span>](#Security)  
  
-   <span data-ttu-id="d4d41-131">**데이터베이스를 일시 중지하려면:**</span><span class="sxs-lookup"><span data-stu-id="d4d41-131">**To suspend a database, using:**</span></span>  
  
-   [<span data-ttu-id="d4d41-132">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="d4d41-132">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="d4d41-133">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="d4d41-133">Transact-SQL</span></span>](#TsqlProcedure)  
  
     [<span data-ttu-id="d4d41-134">PowerShell</span><span class="sxs-lookup"><span data-stu-id="d4d41-134">PowerShell</span></span>](#PowerShellProcedure)  
  
-   <span data-ttu-id="d4d41-135">**후속 작업:** [꽉 찬 트랜잭션 로그 방지](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="d4d41-135">**Follow up:** [Avoiding a Full Transaction Log](#FollowUp)</span></span>  
  
-   [<span data-ttu-id="d4d41-136">관련 작업</span><span class="sxs-lookup"><span data-stu-id="d4d41-136">Related Tasks</span></span>](#RelatedTasks)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="d4d41-137">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="d4d41-137">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="d4d41-138">제한 사항</span><span class="sxs-lookup"><span data-stu-id="d4d41-138">Limitations and Restrictions</span></span>  
 <span data-ttu-id="d4d41-139">SUSPEND 명령은 대상 데이터베이스를 호스팅하는 복제본에서 수락되는 즉시 반환하지만 실제로 데이터베이스 일시 중지는 비동기식으로 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="d4d41-139">A SUSPEND command returns as soon as it has been accepted by the replica that hosts the target database, but actually suspending the database occurs asynchronously.</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="d4d41-140">필수 조건</span><span class="sxs-lookup"><span data-stu-id="d4d41-140">Prerequisites</span></span>  
 <span data-ttu-id="d4d41-141">일시 중지할 데이터베이스를 호스팅하는 서버 인스턴스에 연결되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d4d41-141">You must be connected to the server instance that hosts the database that you want to suspend.</span></span> <span data-ttu-id="d4d41-142">주 데이터베이스와 해당 보조 데이터베이스를 일시 중지하려면 주 복제본을 호스팅하는 서버 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="d4d41-142">To suspend a primary database and the corresponding secondary databases, connect to the server instance that hosts the primary replica.</span></span> <span data-ttu-id="d4d41-143">주 데이터베이스는 사용 가능한 상태로 두고 보조 데이터베이스를 일시 중지하려면 보조 복제본에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="d4d41-143">To suspend a secondary database while leaving the primary database available, connect to the secondary replica.</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="d4d41-144">권장 사항</span><span class="sxs-lookup"><span data-stu-id="d4d41-144">Recommendations</span></span>  
 <span data-ttu-id="d4d41-145">병목 현상 중에 하나 이상의 보조 데이터베이스를 잠시 중단하면 주 복제본의 성능을 일시적으로 향상됩니다.</span><span class="sxs-lookup"><span data-stu-id="d4d41-145">During bottlenecks, suspending one or more secondary databases briefly might be useful to improve performance temporarily on the primary replica.</span></span> <span data-ttu-id="d4d41-146">보조 데이터베이스가 일시 중지된 상태인 동안에는 해당 주 데이터베이스의 트랜잭션 로그를 자를 수 없으므로</span><span class="sxs-lookup"><span data-stu-id="d4d41-146">As long as a secondary database remains suspended, the transaction log of the corresponding primary database cannot be truncated.</span></span> <span data-ttu-id="d4d41-147">로그 레코드가 주 데이터베이스에 누적됩니다.</span><span class="sxs-lookup"><span data-stu-id="d4d41-147">This causes log records to accumulate on the primary database.</span></span> <span data-ttu-id="d4d41-148">따라서 일시 중지된 보조 데이터베이스를 신속하게 다시 시작하거나 제거하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="d4d41-148">Therefore, we recommend that you resume, or remove, a suspended secondary database quickly.</span></span> <span data-ttu-id="d4d41-149">자세한 내용은 이 항목 뒷부분에 있는 [후속 작업: 꽉 찬 트랜잭션 로그 방지](#FollowUp)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d4d41-149">For more information, see [Follow up: Avoiding a Full Transaction Log](#FollowUp), later in this topic.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="d4d41-150">보안</span><span class="sxs-lookup"><span data-stu-id="d4d41-150">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="d4d41-151">권한</span><span class="sxs-lookup"><span data-stu-id="d4d41-151">Permissions</span></span>  
 <span data-ttu-id="d4d41-152">데이터베이스에 대한 ALTER 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="d4d41-152">Requires ALTER permission on the database.</span></span>  
  
 <span data-ttu-id="d4d41-153">가용성 그룹에 대한 ALTER AVAILABILITY GROUP 권한, CONTROL AVAILABILITY GROUP 권한, ALTER ANY AVAILABILITY GROUP 권한 또는 CONTROL SERVER 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="d4d41-153">Requires ALTER AVAILABILITY GROUP permission on the availability group, CONTROL AVAILABILITY GROUP permission, ALTER ANY AVAILABILITY GROUP permission, or CONTROL SERVER permission.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="d4d41-154">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="d4d41-154">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="d4d41-155">**데이터베이스를 일시 중지하려면**</span><span class="sxs-lookup"><span data-stu-id="d4d41-155">**To suspend a database**</span></span>  
  
1.  <span data-ttu-id="d4d41-156">개체 탐색기에서 데이터베이스를 일시 중지할 가용성 복제본을 호스팅하는 서버 인스턴스에 연결하고 서버 트리를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="d4d41-156">In Object Explorer, connect to the server instance that hosts the availability replica on which you want to suspend a database, and expand the server tree.</span></span> <span data-ttu-id="d4d41-157">자세한 내용은 이 항목의 앞부분에 나오는 [필수 구성 요소](#Prerequisites)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d4d41-157">For more information, see [Prerequisites](#Prerequisites), earlier in this topic.</span></span>  
  
2.  <span data-ttu-id="d4d41-158">**AlwaysOn 고가용성** 및 **가용성 그룹** 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="d4d41-158">Expand the **AlwaysOn High Availability** node and the **Availability Groups** node.</span></span>  
  
3.  <span data-ttu-id="d4d41-159">가용성 그룹을 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="d4d41-159">Expand the availability group.</span></span>  
  
4.  <span data-ttu-id="d4d41-160">**가용성 데이터베이스** 노드를 확장하고 데이터베이스를 마우스 오른쪽 단추로 누른 다음 **데이터 이동 일시 중지**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d4d41-160">Expand the **Availability Databases** node, right-click the database, and click **Suspend Data Movement**.</span></span>  
  
5.  <span data-ttu-id="d4d41-161">**데이터 이동 일시 중지** 대화 상자에서 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d4d41-161">In the **Suspend Data Movement** dialog box, click **OK**.</span></span>  
  
     <span data-ttu-id="d4d41-162">개체 탐색기에서 데이터베이스 아이콘이 일시 중지 표시기로 변경되어 데이터베이스가 일시 중지되었음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="d4d41-162">Object Explorer indicates that the database is suspended by changing  the database icon to display a pause indicator.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d4d41-163">이 복제본 위치에서 다른 데이터베이스를 일시 중지하려면 각 데이터베이스에 대해 4단계와 5단계를 반복합니다.</span><span class="sxs-lookup"><span data-stu-id="d4d41-163">To suspend additional databases on this replica location, repeat steps 4 and 5  for each database.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="d4d41-164">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="d4d41-164">Using Transact-SQL</span></span>  
 <span data-ttu-id="d4d41-165">**데이터베이스를 일시 중지하려면**</span><span class="sxs-lookup"><span data-stu-id="d4d41-165">**To suspend a database**</span></span>  
  
1.  <span data-ttu-id="d4d41-166">데이터베이스를 일시 중지할 복제본을 호스팅하는 서버 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="d4d41-166">Connect to the server instance that hosts the replica whose database you want to suspend.</span></span> <span data-ttu-id="d4d41-167">자세한 내용은 이 항목의 앞부분에 나오는 [필수 구성 요소](#Prerequisites)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d4d41-167">For more information, see [Prerequisites](#Prerequisites), earlier in this topic.</span></span>  
  
2.  <span data-ttu-id="d4d41-168">다음의 [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql-set-hadr)문을 사용하여 데이터베이스를 일시 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="d4d41-168">Suspend the database by using the following [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql-set-hadr)statement:</span></span>  
  
     <span data-ttu-id="d4d41-169">ALTER DATABASE *database_name* SET HADR SUSPEND</span><span class="sxs-lookup"><span data-stu-id="d4d41-169">ALTER DATABASE *database_name* SET HADR SUSPEND</span></span>  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a> <span data-ttu-id="d4d41-170">PowerShell 사용</span><span class="sxs-lookup"><span data-stu-id="d4d41-170">Using PowerShell</span></span>  
 <span data-ttu-id="d4d41-171">**데이터베이스를 일시 중지하려면**</span><span class="sxs-lookup"><span data-stu-id="d4d41-171">**To suspend a database**</span></span>  
  
1.  <span data-ttu-id="d4d41-172">데이터베이스를 일시 중지할 복제본을 호스팅하는 서버 인스턴스로 디렉터리를 변경합니다(`cd`).</span><span class="sxs-lookup"><span data-stu-id="d4d41-172">Change directory (`cd`) to the server instance that hosts the replica whose database you want to suspend.</span></span> <span data-ttu-id="d4d41-173">자세한 내용은 이 항목의 앞부분에 나오는 [필수 구성 요소](#Prerequisites)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d4d41-173">For more information, see [Prerequisites](#Prerequisites), earlier in this topic.</span></span>  
  
2.  <span data-ttu-id="d4d41-174">`Suspend-SqlAvailabilityDatabase` cmdlet을 사용하여 가용성 그룹을 일시 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="d4d41-174">Use the `Suspend-SqlAvailabilityDatabase` cmdlet to suspend the availability group.</span></span>  
  
     <span data-ttu-id="d4d41-175">예를 들어 다음 명령은 서버 인스턴스 `MyDb3` 에서 가용성 그룹 `MyAg` 에 있는 가용성 데이터베이스 `Computer\Instance`에 대한 데이터 동기화를 일시 중단합니다.</span><span class="sxs-lookup"><span data-stu-id="d4d41-175">For example, the following command suspends data synchronization for the availability database `MyDb3` in the availability group `MyAg` on the server instance named `Computer\Instance`.</span></span>  
  
    ```powershell
    Suspend-SqlAvailabilityDatabase -Path SQLSERVER:\Sql\Computer\Instance\AvailabilityGroups\MyAg\Databases\MyDb3  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="d4d41-176">cmdlet의 구문을 보려면 `Get-Help` PowerShell 환경에서 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] cmdlet을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="d4d41-176">To view the syntax of a cmdlet, use the `Get-Help` cmdlet in the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell environment.</span></span> <span data-ttu-id="d4d41-177">자세한 내용은 [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d4d41-177">For more information, see [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).</span></span>  
  
 <span data-ttu-id="d4d41-178">**SQL Server PowerShell 공급자를 설정하고 사용하려면**</span><span class="sxs-lookup"><span data-stu-id="d4d41-178">**To set up and use the SQL Server PowerShell provider**</span></span>  
  
-   [<span data-ttu-id="d4d41-179">SQL Server PowerShell 공급자</span><span class="sxs-lookup"><span data-stu-id="d4d41-179">SQL Server PowerShell Provider</span></span>](../../../powershell/sql-server-powershell-provider.md)  
  
##  <a name="follow-up-avoiding-a-full-transaction-log"></a><a name="FollowUp"></a> <span data-ttu-id="d4d41-180">후속 작업: 꽉 찬 트랜잭션 로그 방지</span><span class="sxs-lookup"><span data-stu-id="d4d41-180">Follow Up: Avoiding a Full Transaction Log</span></span>  
 <span data-ttu-id="d4d41-181">일반적으로 데이터베이스에서 자동 검사점을 수행하면 다음 로그 백업 이후 해당 트랜잭션 로그가 이 검사점까지 잘립니다.</span><span class="sxs-lookup"><span data-stu-id="d4d41-181">Normally, when an automatic checkpoint is performed on a database, its transaction log is truncated to that checkpoint after the next log backup.</span></span> <span data-ttu-id="d4d41-182">그러나 보조 데이터베이스를 일시 중지하는 동안 모든 현재 로그 레코드가 주 데이터베이스에서 활성 상태로 남아 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d4d41-182">However, while a secondary database is suspended, all of the current log records remain active on the primary database.</span></span> <span data-ttu-id="d4d41-183">서버 인스턴스의 공간이 부족하거나 최대 크기에 도달하여 트랜잭션 로그가 가득 차면 데이터베이스는 더 이상 업데이트를 수행할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d4d41-183">If the transaction log fills up (either because it reaches its maximum size or the server instance runs out of space), the database cannot perform any more updates.</span></span>  
  
 <span data-ttu-id="d4d41-184">이 문제를 방지하려면 다음 중 하나를 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d4d41-184">To avoid this problem, you should do one of the following:</span></span>  
  
-   <span data-ttu-id="d4d41-185">주 데이터베이스에 대한 로그 공간을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="d4d41-185">Add more log space for the primary database.</span></span>  
  
-   <span data-ttu-id="d4d41-186">로그가 꽉 차기 전에 보조 데이터베이스를 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="d4d41-186">Resume the secondary database before the log fills up.</span></span> <span data-ttu-id="d4d41-187">자세한 내용은 이 항목 뒷부분에 나오는 [가용성 데이터베이스 재개&#40;SQL Server&#41;](resume-an-availability-database-sql-server.md)에서 가용성 데이터베이스를 일시 중지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d4d41-187">For more information, see [Resume an Availability Database &#40;SQL Server&#41;](resume-an-availability-database-sql-server.md).</span></span>  
  
-   <span data-ttu-id="d4d41-188">보조 데이터베이스를 제거하려면</span><span class="sxs-lookup"><span data-stu-id="d4d41-188">Remove the secondary database.</span></span> <span data-ttu-id="d4d41-189">자세한 내용은 [가용성 그룹에서 보조 데이터베이스 제거&#40;SQL Server&#41;](remove-a-secondary-database-from-an-availability-group-sql-server.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d4d41-189">For more information, see [Remove a Secondary Database from an Availability Group &#40;SQL Server&#41;](remove-a-secondary-database-from-an-availability-group-sql-server.md).</span></span>  
  
 <span data-ttu-id="d4d41-190">**꽉 찬 트랜잭션 로그 문제를 해결하려면**</span><span class="sxs-lookup"><span data-stu-id="d4d41-190">**To troubleshoot a full transaction log**</span></span>  
  
-   [<span data-ttu-id="d4d41-191">꽉 찬 트랜잭션 로그 문제 해결&#40;SQL Server 오류 9002&#41;</span><span class="sxs-lookup"><span data-stu-id="d4d41-191">Troubleshoot a Full Transaction Log &#40;SQL Server Error 9002&#41;</span></span>](../../../relational-databases/logs/troubleshoot-a-full-transaction-log-sql-server-error-9002.md)  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="d4d41-192">관련 작업</span><span class="sxs-lookup"><span data-stu-id="d4d41-192">Related Tasks</span></span>  
  
-   [<span data-ttu-id="d4d41-193">가용성 데이터베이스 재개&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="d4d41-193">Resume an Availability Database &#40;SQL Server&#41;</span></span>](resume-an-availability-database-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="d4d41-194">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d4d41-194">See Also</span></span>  
 <span data-ttu-id="d4d41-195">[AlwaysOn 가용성 그룹 &#40;SQL Server 개요&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="d4d41-195">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 [<span data-ttu-id="d4d41-196">가용성 데이터베이스 재개&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="d4d41-196">Resume an Availability Database &#40;SQL Server&#41;</span></span>](resume-an-availability-database-sql-server.md)  
