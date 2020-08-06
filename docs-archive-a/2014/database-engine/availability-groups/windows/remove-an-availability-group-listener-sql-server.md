---
title: 가용성 그룹 수신기 제거(SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.availabilitygroup.removeaglistener.default.f1
helpviewer_keywords:
- Availability Groups [SQL Server], listeners
ms.assetid: fd9bba9a-d29f-4c23-8ecd-aaa049ed5f1b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 057b9c137cb4d8bbbdd03be61df600f7e59b264c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648601"
---
# <a name="remove-an-availability-group-listener-sql-server"></a><span data-ttu-id="e4a08-102">가용성 그룹 수신기 제거(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="e4a08-102">Remove an Availability Group Listener (SQL Server)</span></span>
  <span data-ttu-id="e4a08-103">이 항목에서는 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)]또는 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]의 PowerShell을 사용하여 AlwaysOn 가용성 그룹에서 가용성 그룹 수신기를 제거하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="e4a08-103">This topic describes how to remove an availability group listener from an AlwaysOn availability group by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)], or PowerShell in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span>  
  
-   <span data-ttu-id="e4a08-104">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="e4a08-104">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="e4a08-105">필수 구성 요소</span><span class="sxs-lookup"><span data-stu-id="e4a08-105">Prerequisites</span></span>](#Prerequisites)  
  
     [<span data-ttu-id="e4a08-106">권장 사항</span><span class="sxs-lookup"><span data-stu-id="e4a08-106">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="e4a08-107">보안</span><span class="sxs-lookup"><span data-stu-id="e4a08-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="e4a08-108">**수신기를 제거하려면:**</span><span class="sxs-lookup"><span data-stu-id="e4a08-108">**To remove a listener, using:**</span></span>  
  
     [<span data-ttu-id="e4a08-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="e4a08-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="e4a08-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="e4a08-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
     [<span data-ttu-id="e4a08-111">PowerShell</span><span class="sxs-lookup"><span data-stu-id="e4a08-111">PowerShell</span></span>](#PowerShellProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="e4a08-112">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="e4a08-112">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="e4a08-113">필수 조건</span><span class="sxs-lookup"><span data-stu-id="e4a08-113">Prerequisites</span></span>  
  
-   <span data-ttu-id="e4a08-114">주 복제본을 호스팅하는 서버 인스턴스에 연결되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e4a08-114">You must be connected to the server instance that hosts the primary replica.</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="e4a08-115">권장 사항</span><span class="sxs-lookup"><span data-stu-id="e4a08-115">Recommendations</span></span>  
 <span data-ttu-id="e4a08-116">가용성 그룹 수신기를 삭제하기 전에 해당 가용성 그룹 수신기를 사용 중인 애플리케이션이 없는지 확인하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="e4a08-116">Before you delete an availability group listener, we recommend that you ensure that no applications are using it.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="e4a08-117">보안</span><span class="sxs-lookup"><span data-stu-id="e4a08-117">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="e4a08-118">권한</span><span class="sxs-lookup"><span data-stu-id="e4a08-118">Permissions</span></span>  
 <span data-ttu-id="e4a08-119">가용성 그룹에 대한 ALTER AVAILABILITY GROUP 권한, CONTROL AVAILABILITY GROUP 권한, ALTER ANY AVAILABILITY GROUP 권한 또는 CONTROL SERVER 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="e4a08-119">Requires ALTER AVAILABILITY GROUP permission on the availability group, CONTROL AVAILABILITY GROUP permission, ALTER ANY AVAILABILITY GROUP permission, or CONTROL SERVER permission.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="e4a08-120">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="e4a08-120">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="e4a08-121">**가용성 그룹 수신기를 제거하려면**</span><span class="sxs-lookup"><span data-stu-id="e4a08-121">**To remove an availability group listener**</span></span>  
  
1.  <span data-ttu-id="e4a08-122">개체 탐색기에서 주 복제본을 호스팅하는 서버 인스턴스에 연결하고 서버 트리를 확장할 서버 이름을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e4a08-122">In Object Explorer, connect to the server instance that hosts the primary replica, and click the server name to expand the server tree.</span></span>  
  
2.  <span data-ttu-id="e4a08-123">**AlwaysOn 고가용성** 및 **가용성 그룹** 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="e4a08-123">Expand the **AlwaysOn High Availability** node and the **Availability Groups** node.</span></span>  
  
3.  <span data-ttu-id="e4a08-124">가용성 그룹의 노드를 확장하고 **가용성 그룹 수신기** 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="e4a08-124">Expand the node of the availability group, and expand the **Availability Groups Listeners** node.</span></span>  
  
4.  <span data-ttu-id="e4a08-125">제거할 수신기를 마우스 오른쪽 단추로 클릭한 다음 **삭제** 명령을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e4a08-125">Right-click the listener to be removed, and select the **Delete** command.</span></span>  
  
5.  <span data-ttu-id="e4a08-126">**가용성 그룹에서 수신기 제거** 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="e4a08-126">This opens the **Remove Listener from Availability Group** dialog box.</span></span> <span data-ttu-id="e4a08-127">자세한 내용은 이 항목의 뒷부분에 나와 있는 [가용성 그룹에서 수신기 제거](#AgListenerPropertiesDialog)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e4a08-127">For more information, see [Remove Listener from Availability Group](#AgListenerPropertiesDialog), later in this topic.</span></span>  
  
###  <a name="remove-listener-from-availability-group-dialog-box"></a><a name="AgListenerPropertiesDialog"></a><span data-ttu-id="e4a08-128">가용성 그룹에서 수신기 제거 (대화 상자)</span><span class="sxs-lookup"><span data-stu-id="e4a08-128">Remove Listener from Availability Group (Dialog Box)</span></span>  
 <span data-ttu-id="e4a08-129">**이름**</span><span class="sxs-lookup"><span data-stu-id="e4a08-129">**Name**</span></span>  
 <span data-ttu-id="e4a08-130">제거할 수신기의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="e4a08-130">The name of the listener to be removed.</span></span>  
  
 <span data-ttu-id="e4a08-131">**결과**</span><span class="sxs-lookup"><span data-stu-id="e4a08-131">**Result**</span></span>  
 <span data-ttu-id="e4a08-132">**성공** 또는 **오류**링크가 표시됩니다. 링크를 클릭하여 자세한 내용을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e4a08-132">Displays a link, either **Success** or **Error**, which you can click for more information.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="e4a08-133">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="e4a08-133">Using Transact-SQL</span></span>  
 <span data-ttu-id="e4a08-134">**가용성 그룹 수신기를 제거하려면**</span><span class="sxs-lookup"><span data-stu-id="e4a08-134">**To remove an availability group listener**</span></span>  
  
1.  <span data-ttu-id="e4a08-135">주 복제본을 호스팅하는 서버 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="e4a08-135">Connect to the server instance that hosts the primary replica.</span></span>  
  
2.  <span data-ttu-id="e4a08-136">다음과 같은 [ALTER AVAILABILITY GROUP](/sql/t-sql/statements/alter-availability-group-transact-sql) 문을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="e4a08-136">Use the [ALTER AVAILABILITY GROUP](/sql/t-sql/statements/alter-availability-group-transact-sql) statement, as follows:</span></span>  
  
     <span data-ttu-id="e4a08-137">ALTER AVAILABILITY GROUP *GROUP_NAME* LISTENER **' *`dns_name`* '** 제거</span><span class="sxs-lookup"><span data-stu-id="e4a08-137">ALTER AVAILABILITY GROUP *group_name* REMOVE LISTENER **'*`dns_name`*'**</span></span>  
  
     <span data-ttu-id="e4a08-138">여기서 *group_name* 은 가용성 그룹의 이름이고, *dns_name* 은 가용성 그룹 수신기의 DNS 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="e4a08-138">where *group_name* is the name of the availability group and *dns_name* is the DNS name of the availability group listener.</span></span>  
  
     <span data-ttu-id="e4a08-139">다음 예에서는 `AccountsAG` 가용성 그룹의 수신기를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="e4a08-139">The following example deletes the listener of the `AccountsAG` availability group.</span></span> <span data-ttu-id="e4a08-140">DNS 이름은 AccountsAG_Listener입니다.</span><span class="sxs-lookup"><span data-stu-id="e4a08-140">The DNS name is AccountsAG_Listener.</span></span>  
  
    ```sql
    ALTER AVAILABILITY GROUP AccountsAG REMOVE LISTENER 'AccountsAG_Listener';  
    ```  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a> <span data-ttu-id="e4a08-141">PowerShell 사용</span><span class="sxs-lookup"><span data-stu-id="e4a08-141">Using PowerShell</span></span>  
 <span data-ttu-id="e4a08-142">**가용성 그룹 수신기를 제거하려면**</span><span class="sxs-lookup"><span data-stu-id="e4a08-142">**To remove an availability group listener**</span></span>  
  
1.  <span data-ttu-id="e4a08-143">기본값(`cd`)을 주 복제본을 호스팅하는 서버 인스턴스로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="e4a08-143">Set default (`cd`) to the server instance that hosts the primary replica.</span></span>  
  
2.  <span data-ttu-id="e4a08-144">기본 제공 `Remove-Item`cmdlet을 사용하여 수신기를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="e4a08-144">Use the built in `Remove-Item` cmdlet to remove a listener.</span></span> <span data-ttu-id="e4a08-145">예를 들어 다음 명령은 `MyListener` 라는 가용성 그룹에서 `MyAg`라는 수신기를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="e4a08-145">For example, the following command removes a listener named `MyListener` from an availability group named `MyAg`.</span></span>  
  
    ```powershell
    Remove-Item SQLSERVER:\Sql\PrimaryServer\InstanceName\AvailabilityGroups\MyAg\AGListeners\MyListener  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="e4a08-146">cmdlet의 구문을 보려면 `Get-Help` PowerShell 환경에서 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] cmdlet을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="e4a08-146">To view the syntax of a cmdlet, use the `Get-Help` cmdlet in the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell environment.</span></span> <span data-ttu-id="e4a08-147">자세한 내용은 [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e4a08-147">For more information, see [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="e4a08-148">관련 작업</span><span class="sxs-lookup"><span data-stu-id="e4a08-148">Related Tasks</span></span>  
  
-   [<span data-ttu-id="e4a08-149">가용성 그룹 수신기 만들기 또는 구성&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="e4a08-149">Create or Configure an Availability Group Listener &#40;SQL Server&#41;</span></span>](create-or-configure-an-availability-group-listener-sql-server.md)  
  
-   [<span data-ttu-id="e4a08-150">가용성 그룹 수신기 속성 보기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="e4a08-150">View Availability Group Listener Properties &#40;SQL Server&#41;</span></span>](view-availability-group-listener-properties-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="e4a08-151">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e4a08-151">See Also</span></span>  
 <span data-ttu-id="e4a08-152">[AlwaysOn 가용성 그룹 &#40;SQL Server 개요&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="e4a08-152">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 [<span data-ttu-id="e4a08-153">가용성 그룹 수신기, 클라이언트 연결 및 애플리케이션 장애 조치(failover)&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="e4a08-153">Availability Group Listeners, Client Connectivity, and Application Failover &#40;SQL Server&#41;</span></span>](../../listeners-client-connectivity-application-failover.md)  
