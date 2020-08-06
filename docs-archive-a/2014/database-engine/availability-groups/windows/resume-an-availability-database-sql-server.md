---
title: 가용성 데이터베이스 재개(SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.availabilitygroup.resumedatamove.f1
helpviewer_keywords:
- Availability Groups [SQL Server], resuming a database
- secondary databases [SQL Server], in availability group
- primary databases [SQL Server], in availability group
- Availability Groups [SQL Server], databases
ms.assetid: 20e9147b-e985-4caa-910e-fc4b38dbf9a1
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 6a2279940c2502a310e9dac4448bd6029b6e13dc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740480"
---
# <a name="resume-an-availability-database-sql-server"></a><span data-ttu-id="ec65d-102">가용성 데이터베이스 재개(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="ec65d-102">Resume an Availability Database (SQL Server)</span></span>
  <span data-ttu-id="ec65d-103">[!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 의 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)]또는 PowerShell을 사용하여 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]에서 일시 중지된 가용성 데이터베이스를 재개할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ec65d-103">You can resume a suspended availability database in [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)], or PowerShell in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="ec65d-104">일시 중지된 데이터베이스를 재개하면 데이터베이스는 SYNCHRONIZING 상태가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ec65d-104">Resuming a suspended database puts the database into the SYNCHRONIZING state.</span></span> <span data-ttu-id="ec65d-105">주 데이터베이스를 재개하면 주 데이터베이스를 일시 중지함에 따라 함께 일시 중지된 보조 데이터베이스도 재개됩니다.</span><span class="sxs-lookup"><span data-stu-id="ec65d-105">Resuming the primary database also resumes any of its secondary databases that were suspended as the result of suspending the primary database.</span></span> <span data-ttu-id="ec65d-106">보조 데이터베이스가 보조 복제본을 호스팅하는 서버 인스턴스에서 로컬로 일시 중지된 경우 해당 보조 데이터베이스를 로컬로 재개해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ec65d-106">If any secondary database was suspended locally, from the server instance that hosts the secondary replica, that secondary database must be resumed locally.</span></span> <span data-ttu-id="ec65d-107">지정된 보조 데이터베이스와 해당 주 데이터베이스가 SYNCHRONIZING 상태이면 보조 데이터베이스에서 데이터 동기화가 재개됩니다.</span><span class="sxs-lookup"><span data-stu-id="ec65d-107">Once a given secondary database and the corresponding primary database are in the SYNCHRONIZING state, data synchronization resumes on the secondary database.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ec65d-108">AlwaysOn 보조 데이터베이스를 일시 중지하고 재개해도 주 데이터베이스의 가용성에 직접 영향을 주지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ec65d-108">Suspending and resuming an AlwaysOn secondary database does not directly affect the availability of the primary database.</span></span> <span data-ttu-id="ec65d-109">그러나 보조 데이터베이스를 일시 중지하면 일시 중지된 보조 데이터베이스가 재개될 때까지 주 데이터베이스의 중복 및 장애 조치(failover) 기능에 영향을 줄 수는 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ec65d-109">However, suspending a secondary database can impact redundancy and failover capabilities for the primary database, until the suspended secondary database is resumed.</span></span> <span data-ttu-id="ec65d-110">이것은 데이터베이스 미러링과는 대조적입니다. 데이터베이스 미러링의 경우에는 미러링을 재개할 때까지 미러 데이터베이스 및 주 데이터베이스에서 미러링 상태가 일시 중지됩니다.</span><span class="sxs-lookup"><span data-stu-id="ec65d-110">This is in contrast to database mirroring, where the mirroring state is suspended on both the mirror database and the principal database until mirroring is resumed.</span></span> <span data-ttu-id="ec65d-111">AlwaysOn 주 데이터베이스를 일시 중지하면 모든 해당 보조 데이터베이스에서 데이터 이동이 일시 중지되고 주 데이터베이스를 재개할 때까지 해당 데이터베이스에 대한 중복 및 장애 조치(failover) 기능이 중단됩니다.</span><span class="sxs-lookup"><span data-stu-id="ec65d-111">Suspending an AlwaysOn primary database suspends data movement on all the corresponding secondary databases, and redundancy and failover capabilities cease for that database until the primary database is resumed.</span></span>  
  
-   <span data-ttu-id="ec65d-112">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="ec65d-112">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="ec65d-113">제한 사항</span><span class="sxs-lookup"><span data-stu-id="ec65d-113">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="ec65d-114">필수 구성 요소</span><span class="sxs-lookup"><span data-stu-id="ec65d-114">Prerequisites</span></span>](#Prerequisites)  
  
     [<span data-ttu-id="ec65d-115">보안</span><span class="sxs-lookup"><span data-stu-id="ec65d-115">Security</span></span>](#Security)  
  
-   <span data-ttu-id="ec65d-116">**보조 데이터베이스를 재개하려면:**</span><span class="sxs-lookup"><span data-stu-id="ec65d-116">**To resume a secondary database, using:**</span></span>  
  
     [<span data-ttu-id="ec65d-117">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="ec65d-117">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="ec65d-118">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="ec65d-118">Transact-SQL</span></span>](#TsqlProcedure)  
  
     [<span data-ttu-id="ec65d-119">PowerShell</span><span class="sxs-lookup"><span data-stu-id="ec65d-119">PowerShell</span></span>](#PowerShellProcedure)  
  
-   [<span data-ttu-id="ec65d-120">관련 작업</span><span class="sxs-lookup"><span data-stu-id="ec65d-120">Related Tasks</span></span>](#RelatedTasks)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="ec65d-121">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="ec65d-121">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="ec65d-122">제한 사항</span><span class="sxs-lookup"><span data-stu-id="ec65d-122">Limitations and Restrictions</span></span>  
 <span data-ttu-id="ec65d-123">RESUME 명령은 대상 데이터베이스를 호스팅하는 복제본에서 수락되는 즉시 반환하지만 실제로 데이터베이스 재개는 비동기식으로 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="ec65d-123">A RESUME command returns as soon as it has been accepted by the replica that hosts the target database, but actually resuming the database occurs asynchronously.</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="ec65d-124">필수 조건</span><span class="sxs-lookup"><span data-stu-id="ec65d-124">Prerequisites</span></span>  
  
-   <span data-ttu-id="ec65d-125">재개할 데이터베이스를 호스팅하는 서버 인스턴스에 연결되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ec65d-125">You must be connected to the server instance that hosts the database to be resumed.</span></span>  
  
-   <span data-ttu-id="ec65d-126">가용성 그룹이 온라인 상태여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ec65d-126">The availability group must be online.</span></span>  
  
-   <span data-ttu-id="ec65d-127">주 데이터베이스가 온라인이고 사용 가능한 상태여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ec65d-127">The primary database must be online and available.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="ec65d-128">보안</span><span class="sxs-lookup"><span data-stu-id="ec65d-128">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="ec65d-129">권한</span><span class="sxs-lookup"><span data-stu-id="ec65d-129">Permissions</span></span>  
 <span data-ttu-id="ec65d-130">데이터베이스에 대한 ALTER 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="ec65d-130">Requires ALTER permission on the database.</span></span>  
  
 <span data-ttu-id="ec65d-131">가용성 그룹에 대한 ALTER AVAILABILITY GROUP 권한, CONTROL AVAILABILITY GROUP 권한, ALTER ANY AVAILABILITY GROUP 권한 또는 CONTROL SERVER 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="ec65d-131">Requires ALTER AVAILABILITY GROUP permission on the availability group, CONTROL AVAILABILITY GROUP permission, ALTER ANY AVAILABILITY GROUP permission, or CONTROL SERVER permission.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="ec65d-132">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="ec65d-132">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="ec65d-133">**보조 데이터베이스를 재개하려면**</span><span class="sxs-lookup"><span data-stu-id="ec65d-133">**To resume a secondary database**</span></span>  
  
1.  <span data-ttu-id="ec65d-134">개체 탐색기에서 데이터베이스를 재개할 가용성 복제본을 호스팅하는 서버 인스턴스에 연결하고 서버 트리를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="ec65d-134">In Object Explorer, connect to the server instance that hosts the availability replica on which you want to resume a database, and expand the server tree.</span></span>  
  
2.  <span data-ttu-id="ec65d-135">**AlwaysOn 고가용성** 및 **가용성 그룹** 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="ec65d-135">Expand the **AlwaysOn High Availability** node and the **Availability Groups** node.</span></span>  
  
3.  <span data-ttu-id="ec65d-136">가용성 그룹을 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="ec65d-136">Expand the availability group.</span></span>  
  
4.  <span data-ttu-id="ec65d-137">**가용성 데이터베이스** 노드를 확장하고 데이터베이스를 마우스 오른쪽 단추로 누른 다음 **데이터 이동 재개**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ec65d-137">Expand the **Availability Databases** node, right-click the database, and click **Resume Data Movement**.</span></span>  
  
5.  <span data-ttu-id="ec65d-138">**데이터 이동 재개** 대화 상자에서 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ec65d-138">In the **Resume Data Movement** dialog box, click **OK**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ec65d-139">이 복제본 위치에서 추가 데이터베이스를 재개하려면 각 데이터베이스에 대해 4-5단계를 반복합니다.</span><span class="sxs-lookup"><span data-stu-id="ec65d-139">To resume additional databases on this replica location, repeat steps 4 and 5 for each database.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="ec65d-140">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="ec65d-140">Using Transact-SQL</span></span>  
 <span data-ttu-id="ec65d-141">**로컬로 일시 중지된 보조 데이터베이스를 재개하려면**</span><span class="sxs-lookup"><span data-stu-id="ec65d-141">**To resume a secondary database that was suspended locally**</span></span>  
  
1.  <span data-ttu-id="ec65d-142">데이터베이스를 재개할 보조 복제본을 호스팅하는 서버 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="ec65d-142">Connect to the server instance that hosts the secondary replica whose database you want to resume.</span></span>  
  
2.  <span data-ttu-id="ec65d-143">다음 [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql-set-hadr)문을 사용하여 보조 데이터베이스를 재개합니다.</span><span class="sxs-lookup"><span data-stu-id="ec65d-143">Resume the secondary database by using the following [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql-set-hadr)statement:</span></span>  
  
     <span data-ttu-id="ec65d-144">ALTER DATABASE *database_name* SET HADR RESUME</span><span class="sxs-lookup"><span data-stu-id="ec65d-144">ALTER DATABASE *database_name* SET HADR RESUME</span></span>  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a> <span data-ttu-id="ec65d-145">PowerShell 사용</span><span class="sxs-lookup"><span data-stu-id="ec65d-145">Using PowerShell</span></span>  

### <a name="to-resume-a-secondary-database"></a><span data-ttu-id="ec65d-146">보조 데이터베이스를 재개하려면</span><span class="sxs-lookup"><span data-stu-id="ec65d-146">To resume a secondary database</span></span>
  
1.  <span data-ttu-id="ec65d-147">데이터베이스를 재개할 복제본을 호스팅하는 서버 인스턴스로 디렉터리를 변경(`cd`)합니다.</span><span class="sxs-lookup"><span data-stu-id="ec65d-147">Change directory (`cd`) to the server instance that hosts the replica whose database you want to resume.</span></span> <span data-ttu-id="ec65d-148">자세한 내용은 이 항목의 앞부분에 나오는 [필수 구성 요소](#Prerequisites)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ec65d-148">For more information, see [Prerequisites](#Prerequisites), earlier in this topic.</span></span>  
  
2.  <span data-ttu-id="ec65d-149">**Resume-SqlAvailabilityDatabase** cmdlet을 사용하여 가용성 그룹을 재개합니다.</span><span class="sxs-lookup"><span data-stu-id="ec65d-149">Use the **Resume-SqlAvailabilityDatabase** cmdlet to resume the availability group.</span></span>  
  
     <span data-ttu-id="ec65d-150">예를 들어 다음 명령은 `MyDb3` 가용성 그룹의 `MyAg`가용성 데이터베이스에 대한 데이터 동기화를 재개합니다.</span><span class="sxs-lookup"><span data-stu-id="ec65d-150">For example, the following command resumes data synchronization for the availability database `MyDb3` in the availability group `MyAg`.</span></span>  
  
    ```powershell
    Resume-SqlAvailabilityDatabase -Path SQLSERVER:\Sql\Computer\Instance\AvailabilityGroups\MyAg\Databases\MyDb3  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="ec65d-151">cmdlet의 구문을 보려면 `Get-Help` PowerShell 환경에서 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] cmdlet을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="ec65d-151">To view the syntax of a cmdlet, use the `Get-Help` cmdlet in the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell environment.</span></span> <span data-ttu-id="ec65d-152">자세한 내용은 [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ec65d-152">For more information, see [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).</span></span>  
  
 <span data-ttu-id="ec65d-153">**SQL Server PowerShell 공급자를 설정하고 사용하려면**</span><span class="sxs-lookup"><span data-stu-id="ec65d-153">**To set up and use the SQL Server PowerShell provider**</span></span>  
  
-   [<span data-ttu-id="ec65d-154">SQL Server PowerShell 공급자</span><span class="sxs-lookup"><span data-stu-id="ec65d-154">SQL Server PowerShell Provider</span></span>](../../../powershell/sql-server-powershell-provider.md)  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="ec65d-155">관련 작업</span><span class="sxs-lookup"><span data-stu-id="ec65d-155">Related Tasks</span></span>  
  
-   [<span data-ttu-id="ec65d-156">가용성 데이터베이스 일시 중지&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="ec65d-156">Suspend an Availability Database &#40;SQL Server&#41;</span></span>](suspend-an-availability-database-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="ec65d-157">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ec65d-157">See Also</span></span>  
 [<span data-ttu-id="ec65d-158">AlwaysOn 가용성 그룹 &#40;SQL Server 개요&#41;</span><span class="sxs-lookup"><span data-stu-id="ec65d-158">Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](overview-of-always-on-availability-groups-sql-server.md)  
