---
title: 가용성 그룹에 보조 데이터베이스 조인(SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.availabilitygroup.joindbs.f1
helpviewer_keywords:
- secondary databases [SQL Server], in availability group
- secondary databases [SQL Server]
- Availability Groups [SQL Server], joining
- Availability Groups [SQL Server], configuring
- Availability Groups [SQL Server], databases
ms.assetid: fd7efe79-c1f9-497d-bfe7-b2a2b2321cf5
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b0d79325bcde33d13688003de079a42a9601cc41
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650265"
---
# <a name="join-a-secondary-database-to-an-availability-group-sql-server"></a><span data-ttu-id="cec72-102">가용성 그룹에 보조 데이터베이스 조인(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="cec72-102">Join a Secondary Database to an Availability Group (SQL Server)</span></span>
  <span data-ttu-id="cec72-103">이 항목에서는 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)]또는 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]의 PowerShell을 사용하여 AlwaysOn 가용성 그룹에 보조 데이터베이스를 조인하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="cec72-103">This topic explains how to join a secondary database to an AlwaysOn availability group by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)], or PowerShell in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="cec72-104">보조 복제본용 보조 데이터베이스를 준비한 후에는 가능한 한 빨리 해당 데이터베이스를 가용성 그룹에 조인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cec72-104">After you prepare a secondary database for a secondary replica, you need to join the database to the availability group as soon as possible.</span></span> <span data-ttu-id="cec72-105">그러면 해당 주 데이터베이스에서 보조 데이터베이스로 데이터 이동이 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="cec72-105">This will start data movement from the corresponding primary database to the secondary database.</span></span>  
  
-   <span data-ttu-id="cec72-106">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="cec72-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="cec72-107">필수 구성 요소</span><span class="sxs-lookup"><span data-stu-id="cec72-107">Prerequisites</span></span>](#Prerequisites)  
  
     [<span data-ttu-id="cec72-108">보안</span><span class="sxs-lookup"><span data-stu-id="cec72-108">Security</span></span>](#Security)  
  
-   <span data-ttu-id="cec72-109">**보조 데이터베이스를 준비하려면:**</span><span class="sxs-lookup"><span data-stu-id="cec72-109">**To prepare a secondary database, using:**</span></span>  
  
     [<span data-ttu-id="cec72-110">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="cec72-110">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="cec72-111">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="cec72-111">Transact-SQL</span></span>](#TsqlProcedure)  
  
     [<span data-ttu-id="cec72-112">PowerShell</span><span class="sxs-lookup"><span data-stu-id="cec72-112">PowerShell</span></span>](#PowerShellProcedure)  
  
> [!NOTE]  
>  <span data-ttu-id="cec72-113">보조 데이터베이스가 그룹에 조인 된 후에 발생 하는 상황에 대 한 자세한 내용은 [AlwaysOn 가용성 그룹 &#40;SQL Server&#41;개요 ](overview-of-always-on-availability-groups-sql-server.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="cec72-113">For information about what happens after a secondary database joins the group, see [Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md).</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="cec72-114">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="cec72-114">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="cec72-115">필수 조건</span><span class="sxs-lookup"><span data-stu-id="cec72-115">Prerequisites</span></span>  
  
-   <span data-ttu-id="cec72-116">보조 복제본을 호스팅하는 서버 인스턴스에 연결되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cec72-116">You must be connected to the server instance that hosts the secondary replica.</span></span>  
  
-   <span data-ttu-id="cec72-117">보조 복제본은 이미 가용성 그룹에 조인되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cec72-117">The secondary replica must already be joined to the availability group.</span></span> <span data-ttu-id="cec72-118">자세한 내용은 [가용성 그룹에 보조 복제본 조인&#40;SQL Server&#41;](join-a-secondary-replica-to-an-availability-group-sql-server.md)또는 PowerShell을 사용하여 Always On 가용성 그룹에 보조 데이터베이스를 조인하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="cec72-118">For more information, see [Join a Secondary Replica to an Availability Group &#40;SQL Server&#41;](join-a-secondary-replica-to-an-availability-group-sql-server.md).</span></span>  
  
-   <span data-ttu-id="cec72-119">보조 데이터베이스는 최근에 준비된 것이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cec72-119">The secondary database must have been prepared recently.</span></span> <span data-ttu-id="cec72-120">자세한 내용은 [가용성 그룹에 대한 보조 데이터베이스 수동 준비&#40;SQL Server&#41;](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md)또는 PowerShell을 사용하여 Always On 가용성 그룹에 보조 데이터베이스를 조인하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="cec72-120">For more information, see [Manually Prepare a Secondary Database for an Availability Group &#40;SQL Server&#41;](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="cec72-121">보안</span><span class="sxs-lookup"><span data-stu-id="cec72-121">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="cec72-122">권한</span><span class="sxs-lookup"><span data-stu-id="cec72-122">Permissions</span></span>  
 <span data-ttu-id="cec72-123">가용성 그룹에 대한 ALTER AVAILABILITY GROUP 권한, CONTROL AVAILABILITY GROUP 권한, ALTER ANY AVAILABILITY GROUP 권한 또는 CONTROL SERVER 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="cec72-123">Requires ALTER AVAILABILITY GROUP permission on the availability group, CONTROL AVAILABILITY GROUP permission, ALTER ANY AVAILABILITY GROUP permission, or CONTROL SERVER permission.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="cec72-124">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="cec72-124">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="cec72-125">**가용성 그룹에 보조 데이터베이스를 조인하려면**</span><span class="sxs-lookup"><span data-stu-id="cec72-125">**To join a secondary database to an availability group**</span></span>  
  
1.  <span data-ttu-id="cec72-126">개체 탐색기에서 보조 복제본을 호스팅하는 서버 인스턴스에 연결하고 서버 트리를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="cec72-126">In Object Explorer, connect to the server instance that hosts the secondary replica, and expand the server tree.</span></span>  
  
2.  <span data-ttu-id="cec72-127">**AlwaysOn 고가용성** 및 **가용성 그룹** 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="cec72-127">Expand the **AlwaysOn High Availability** node and the **Availability Groups** node.</span></span>  
  
3.  <span data-ttu-id="cec72-128">변경할 가용성 그룹을 확장하고 **가용성 데이터베이스** 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="cec72-128">Expand the availability group that you want to change, and expand the **Availability Databases** node.</span></span>  
  
4.  <span data-ttu-id="cec72-129">마우스 오른쪽 단추로 데이터베이스를 클릭하고 **가용성 그룹에 조인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cec72-129">Right-click the database, and click **Join to Availability Group**.</span></span>  
  
5.  <span data-ttu-id="cec72-130">**가용성 그룹에 데이터베이스 조인** 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="cec72-130">This opens the **Join Databases to Availability Group** dialog box.</span></span> <span data-ttu-id="cec72-131">제목 표시줄에 표시된 가용성 그룹 이름과 표에 표시된 데이터베이스 이름을 확인하고 **확인**이나 **취소**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cec72-131">Verify the availability group name, which is displayed on the title bar, and database name or names displayed in the grid, and click **OK**, or click **Cancel**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="cec72-132">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="cec72-132">Using Transact-SQL</span></span>  
 <span data-ttu-id="cec72-133">**가용성 그룹에 보조 데이터베이스를 조인하려면**</span><span class="sxs-lookup"><span data-stu-id="cec72-133">**To join a secondary database to an availability group**</span></span>  
  
1.  <span data-ttu-id="cec72-134">보조 복제본을 호스팅하는 서버 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="cec72-134">Connect to the server instance that hosts the secondary replica.</span></span>  
  
2.  <span data-ttu-id="cec72-135">다음과 같이 [ALTER DATABASE 문의 SET HADR 절](/sql/t-sql/statements/alter-database-transact-sql-set-hadr) 을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="cec72-135">Use the [SET HADR clause of the ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql-set-hadr) statement, as follows:</span></span>  
  
     <span data-ttu-id="cec72-136">ALTER DATABASE *database_name* SET HADR AVAILABILITY GROUP = *group_name*</span><span class="sxs-lookup"><span data-stu-id="cec72-136">ALTER DATABASE *database_name* SET HADR AVAILABILITY GROUP = *group_name*</span></span>  
  
     <span data-ttu-id="cec72-137">여기서 *database_name* 은 조인할 데이터베이스의 이름이고 *group_name* 은 가용성 그룹의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="cec72-137">where *database_name* is the name of a database to be joined and *group_name* is the name of the availability group.</span></span>  
  
     <span data-ttu-id="cec72-138">다음 예에서는 `Db1`이라는 보조 데이터베이스를 `MyAG` 가용성 그룹의 로컬 보조 복제본에 조인합니다.</span><span class="sxs-lookup"><span data-stu-id="cec72-138">The following example joins the secondary database, `Db1`, to the local secondary replica of the `MyAG` availability group.</span></span>  
  
    ```sql
    ALTER DATABASE Db1 SET HADR AVAILABILITY GROUP = MyAG;  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="cec72-139">컨텍스트에서 사용되는 이 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 문을 보려면 [가용성 그룹 만들기&#40;Transact-SQL&#41;](create-an-availability-group-transact-sql.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="cec72-139">To see this [!INCLUDE[tsql](../../../includes/tsql-md.md)] statement used in context, see [Create an Availability Group &#40;Transact-SQL&#41;](create-an-availability-group-transact-sql.md).</span></span>  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a> <span data-ttu-id="cec72-140">PowerShell 사용</span><span class="sxs-lookup"><span data-stu-id="cec72-140">Using PowerShell</span></span>  
 <span data-ttu-id="cec72-141">**가용성 그룹에 보조 데이터베이스를 조인하려면**</span><span class="sxs-lookup"><span data-stu-id="cec72-141">**To join a secondary database to an availability group**</span></span>  
  
1.  <span data-ttu-id="cec72-142">보조 복제본을 호스팅하는 서버 인스턴스로 디렉터리를 변경(`cd`)합니다.</span><span class="sxs-lookup"><span data-stu-id="cec72-142">Change directory (`cd`) to the server instance that hosts the secondary replica.</span></span>  
  
2.  <span data-ttu-id="cec72-143">`Add-SqlAvailabilityDatabase` cmdlet을 사용하여 하나 이상의 보조 데이터베이스를 가용성 그룹에 조인합니다.</span><span class="sxs-lookup"><span data-stu-id="cec72-143">Use the `Add-SqlAvailabilityDatabase` cmdlet to join one or more secondary databases to the availability group.</span></span>  
  
     <span data-ttu-id="cec72-144">예를 들어 다음 명령은 보조 데이터베이스 `Db1`을 보조 복제본을 호스팅하는 서버 인스턴스 중 하나의 가용성 그룹 `MyAG` 에 조인합니다.</span><span class="sxs-lookup"><span data-stu-id="cec72-144">For example, the following command joins a secondary database, `Db1`, to the availability group `MyAG` on one of the server instances that hosts a secondary replica.</span></span>  
  
    ```powershell
    Add-SqlAvailabilityDatabase -Path SQLSERVER:\SQL\SecondaryServer\InstanceName\AvailabilityGroups\MyAG -Database "Db1"  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="cec72-145">cmdlet의 구문을 보려면 `Get-Help` PowerShell 환경에서 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] cmdlet을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="cec72-145">To view the syntax of a cmdlet, use the `Get-Help` cmdlet in the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell environment.</span></span> <span data-ttu-id="cec72-146">자세한 내용은 [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="cec72-146">For more information, see [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).</span></span>  
  
 <span data-ttu-id="cec72-147">**SQL Server PowerShell 공급자를 설정하고 사용하려면**</span><span class="sxs-lookup"><span data-stu-id="cec72-147">**To set up and use the SQL Server PowerShell provider**</span></span>  
  
-   [<span data-ttu-id="cec72-148">SQL Server PowerShell 공급자</span><span class="sxs-lookup"><span data-stu-id="cec72-148">SQL Server PowerShell Provider</span></span>](../../../powershell/sql-server-powershell-provider.md)  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="cec72-149">관련 작업</span><span class="sxs-lookup"><span data-stu-id="cec72-149">Related Tasks</span></span>  
  
-   [<span data-ttu-id="cec72-150">가용성 그룹에 보조 복제본 조인&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="cec72-150">Join a Secondary Replica to an Availability Group &#40;SQL Server&#41;</span></span>](join-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="cec72-151">가용성 그룹에 대한 보조 데이터베이스 준비&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="cec72-151">Manually Prepare a Secondary Database for an Availability Group &#40;SQL Server&#41;</span></span>](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="cec72-152">참고 항목</span><span class="sxs-lookup"><span data-stu-id="cec72-152">See Also</span></span>  
 <span data-ttu-id="cec72-153">[ALTER AVAILABILITY GROUP&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-availability-group-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="cec72-153">[ALTER AVAILABILITY GROUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-availability-group-transact-sql) </span></span>  
 <span data-ttu-id="cec72-154">[AlwaysOn 가용성 그룹 &#40;SQL Server 개요&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="cec72-154">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 [<span data-ttu-id="cec72-155">삭제&#41;SQL Server AlwaysOn 가용성 그룹 구성 &#40;문제 해결</span><span class="sxs-lookup"><span data-stu-id="cec72-155">Troubleshoot AlwaysOn Availability Groups Configuration &#40;SQL Server&#41;deleted</span></span>](troubleshoot-always-on-availability-groups-configuration-sql-server.md)  
