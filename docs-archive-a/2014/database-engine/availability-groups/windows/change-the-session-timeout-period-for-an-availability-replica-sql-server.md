---
title: 가용성 복제본에 대한 세션 제한 시간 변경(SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], configuring
- Availability Groups [SQL Server], session timeout
- session timeout [SQL Server]
ms.assetid: e23c6e06-1cd1-4d4a-9bc2-e3e06ab2933d
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 302ba4a2b0b72a70b05e563eb4085913074469eb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741312"
---
# <a name="change-the-session-timeout-period-for-an-availability-replica-sql-server"></a><span data-ttu-id="b5d6b-102">가용성 복제본에 대한 세션 제한 시간 변경(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="b5d6b-102">Change the Session-Timeout Period for an Availability Replica (SQL Server)</span></span>
  <span data-ttu-id="b5d6b-103">이 항목에서는 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)]또는 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]의 PowerShell을 사용하여 AlwaysOn 가용성 복제본의 세션 제한 시간을 구성하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="b5d6b-103">This topic describes how to configure the session-timeout period of an AlwaysOn availability replica by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)], or PowerShell in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="b5d6b-104">세션 제한 시간은 가용성 복제본이 연결이 실패한 것으로 간주되기 전에 연결된 복제본에서 ping 응답을 받기 위해 기다리는 최대 시간(초)을 제어하는 복제본 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="b5d6b-104">The session-timeout period is a replica property that controls how many seconds (in seconds) that an availability replica waits for a ping response from a connected replica before considering the connection to have failed.</span></span> <span data-ttu-id="b5d6b-105">기본적으로 복제본은 ping 응답을 받기 위해 10초 동안 기다립니다.</span><span class="sxs-lookup"><span data-stu-id="b5d6b-105">By default, a replica waits 10 seconds for a ping response.</span></span> <span data-ttu-id="b5d6b-106">이 복제본 속성은 지정된 보조 복제본과 가용성 그룹의 주 복제본 사이의 연결에만 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="b5d6b-106">This replica property applies only the connection between a given secondary replica and the primary replica of the availability group.</span></span> <span data-ttu-id="b5d6b-107">세션 제한 시간에 대한 자세한 내용은 [AlwaysOn 가용성 그룹 개요&#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b5d6b-107">For more information about the session-timeout period, see [Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md).</span></span>  
  
-   <span data-ttu-id="b5d6b-108">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="b5d6b-108">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="b5d6b-109">필수 구성 요소</span><span class="sxs-lookup"><span data-stu-id="b5d6b-109">Prerequisites</span></span>](#Prerequisites)  
  
     [<span data-ttu-id="b5d6b-110">권장 사항</span><span class="sxs-lookup"><span data-stu-id="b5d6b-110">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="b5d6b-111">보안</span><span class="sxs-lookup"><span data-stu-id="b5d6b-111">Security</span></span>](#Security)  
  
-   <span data-ttu-id="b5d6b-112">**세션 제한 시간을 변경하려면:**</span><span class="sxs-lookup"><span data-stu-id="b5d6b-112">**To change the session-timeout period, using:**</span></span>  
  
     [<span data-ttu-id="b5d6b-113">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="b5d6b-113">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="b5d6b-114">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="b5d6b-114">Transact-SQL</span></span>](#TsqlProcedure)  
  
     [<span data-ttu-id="b5d6b-115">PowerShell</span><span class="sxs-lookup"><span data-stu-id="b5d6b-115">PowerShell</span></span>](#PowerShellProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="b5d6b-116">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="b5d6b-116">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="b5d6b-117">필수 조건</span><span class="sxs-lookup"><span data-stu-id="b5d6b-117">Prerequisites</span></span>  
  
-   <span data-ttu-id="b5d6b-118">주 복제본을 호스팅하는 서버 인스턴스에 연결되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b5d6b-118">You must be connected to the server instance that hosts the primary replica.</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="b5d6b-119">권장 사항</span><span class="sxs-lookup"><span data-stu-id="b5d6b-119">Recommendations</span></span>  
 <span data-ttu-id="b5d6b-120">제한 시간을 10초 이상으로 유지하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="b5d6b-120">We recommend that you keep the time-out period at 10 seconds or greater.</span></span> <span data-ttu-id="b5d6b-121">10초 미만의 값을 설정하면 로드가 많은 시스템에서 PING을 누락하여 잘못된 실패를 선언할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b5d6b-121">Setting the value to less than 10 seconds creates the possibility of a heavily loaded system missing PINGs and declaring a false failure.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="b5d6b-122">보안</span><span class="sxs-lookup"><span data-stu-id="b5d6b-122">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="b5d6b-123">권한</span><span class="sxs-lookup"><span data-stu-id="b5d6b-123">Permissions</span></span>  
 <span data-ttu-id="b5d6b-124">가용성 그룹에 대한 ALTER AVAILABILITY GROUP 권한, CONTROL AVAILABILITY GROUP 권한, ALTER ANY AVAILABILITY GROUP 권한 또는 CONTROL SERVER 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="b5d6b-124">Requires ALTER AVAILABILITY GROUP permission on the availability group, CONTROL AVAILABILITY GROUP permission, ALTER ANY AVAILABILITY GROUP permission, or CONTROL SERVER permission.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="b5d6b-125">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="b5d6b-125">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="b5d6b-126">**가용성 복제본에 대한 세션 제한 시간을 변경하려면**</span><span class="sxs-lookup"><span data-stu-id="b5d6b-126">**To change the session-timeout period for an availability replica**</span></span>  
  
1.  <span data-ttu-id="b5d6b-127">개체 탐색기에서 주 복제본을 호스팅하는 서버 인스턴스에 연결하고 서버 트리를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="b5d6b-127">In Object Explorer, connect to the server instance that hosts the primary replica, and expand the server tree.</span></span>  
  
2.  <span data-ttu-id="b5d6b-128">**AlwaysOn 고가용성** 및 **가용성 그룹** 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="b5d6b-128">Expand the **AlwaysOn High Availability** node and the **Availability Groups** node.</span></span>  
  
3.  <span data-ttu-id="b5d6b-129">가용성 복제본을 구성할 가용성 그룹을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b5d6b-129">Click the availability group whose availability replica you want to configure.</span></span>  
  
4.  <span data-ttu-id="b5d6b-130">구성할 복제본을 마우스 오른쪽 단추로 클릭하고 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b5d6b-130">Right-click the replica to be configured, and click **Properties**.</span></span>  
  
5.  <span data-ttu-id="b5d6b-131">**가용성 복제본 속성** 대화 상자에서 **세션 제한 시간(초)** 필드를 사용하여 이 복제본에 대한 세션 제한 시간(초)을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="b5d6b-131">In the **Availability Replica Properties** dialog box, use the **Session timeout (seconds)** field to change the number of seconds for the session-timeout period on this replica.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="b5d6b-132">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="b5d6b-132">Using Transact-SQL</span></span>  
 <span data-ttu-id="b5d6b-133">**가용성 복제본에 대한 세션 제한 시간을 변경하려면**</span><span class="sxs-lookup"><span data-stu-id="b5d6b-133">**To change the session-timeout period for an availability replica**</span></span>  
  
1.  <span data-ttu-id="b5d6b-134">주 복제본을 호스팅하는 서버 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="b5d6b-134">Connect to the server instance that hosts the primary replica.</span></span>  
  
2.  <span data-ttu-id="b5d6b-135">다음과 같은 [ALTER AVAILABILITY GROUP](/sql/t-sql/statements/alter-availability-group-transact-sql) 문을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="b5d6b-135">Use the [ALTER AVAILABILITY GROUP](/sql/t-sql/statements/alter-availability-group-transact-sql) statement, as follows:</span></span>  
  
     <span data-ttu-id="b5d6b-136">ALTER AVAILABILITY GROUP *group_name*</span><span class="sxs-lookup"><span data-stu-id="b5d6b-136">ALTER AVAILABILITY GROUP *group_name*</span></span>  
  
     <span data-ttu-id="b5d6b-137">MODIFY REPLICA ON '*instance_name*' WITH ( SESSION_TIMEOUT =*seconds* )</span><span class="sxs-lookup"><span data-stu-id="b5d6b-137">MODIFY REPLICA ON '*instance_name*' WITH ( SESSION_TIMEOUT =*seconds* )</span></span>  
  
     <span data-ttu-id="b5d6b-138">여기서 *group_name* 은 가용성 그룹의 이름이고, *instance_name* 은 수정할 가용성 복제본을 호스팅하는 서버 인스턴스의 이름이고, *seconds* 는 복제본이 보조 복제본 역할을 할 때 데이터베이스에 로그를 적용하기 전에 기다리는 최소 시간(초)을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b5d6b-138">where *group_name* is the name of the availability group, *instance_name* is the name of the server instance that hosts the availability replica to be modified, and *seconds* specifies the minimum number of seconds that the replica must wait before applying log to databases when acting as a secondary replica.</span></span> <span data-ttu-id="b5d6b-139">기본값은 0초이며 지연 적용이 없음을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="b5d6b-139">The default is 0 seconds, which indicates that there is no apply delay.</span></span>  
  
     <span data-ttu-id="b5d6b-140">`AccountsAG` 가용성 그룹의 주 복제본에 입력된 다음 예는 `15` 서버 인스턴스에 있는 복제본에 대한 세션 제한 시간 값을 `INSTANCE09` 초로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="b5d6b-140">The following example, entered on the primary replica of the `AccountsAG` availability group, changes the session-timeout value to `15` seconds for the replica located on the `INSTANCE09` server instance.</span></span>  
  
    ```  
    ALTER AVAILABILITY GROUP AccountsAG   
       MODIFY REPLICA ON 'INSTANCE09' WITH (SESSION_TIMEOUT = 15);  
    ```  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a> <span data-ttu-id="b5d6b-141">PowerShell 사용</span><span class="sxs-lookup"><span data-stu-id="b5d6b-141">Using PowerShell</span></span>  

### <a name="to-change-the-session-timeout-period-for-an-availability-replica"></a><span data-ttu-id="b5d6b-142">가용성 복제본에 대한 세션 제한 시간을 변경하려면</span><span class="sxs-lookup"><span data-stu-id="b5d6b-142">To change the session-timeout period for an availability replica</span></span>
  
1.  <span data-ttu-id="b5d6b-143">주 복제본을 호스팅하는 서버 인스턴스로 디렉터리를 변경(`cd`)합니다.</span><span class="sxs-lookup"><span data-stu-id="b5d6b-143">Change directory (`cd`) to the server instance that hosts the primary replica.</span></span>  
  
2.  <span data-ttu-id="b5d6b-144">`Set-SqlAvailabilityReplica` cmdlet을 `SessionTimeout` 매개 변수와 함께 사용하여 지정된 가용성 복제본에 대한 세션 제한 시간(초)을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b5d6b-144">Use the `Set-SqlAvailabilityReplica` cmdlet with the `SessionTimeout` parameter to change the number of seconds for the session-timeout period on a specified availability replica.</span></span>  
  
     <span data-ttu-id="b5d6b-145">예를 들어 다음 명령은 세션 제한 시간을 15초로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="b5d6b-145">For example, the following command sets the session-timeout period to 15 seconds.</span></span>  
  
    ```powershell
    Set-SqlAvailabilityReplica -SessionTimeout 15 -Path SQLSERVER:\Sql\PrimaryServer\InstanceName\AvailabilityGroups\MyAg\AvailabilityReplicas\MyReplica  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="b5d6b-146">cmdlet의 구문을 보려면 `Get-Help` PowerShell 환경에서 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] cmdlet을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="b5d6b-146">To view the syntax of a cmdlet, use the `Get-Help` cmdlet in the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell environment.</span></span> <span data-ttu-id="b5d6b-147">자세한 내용은 [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b5d6b-147">For more information, see [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).</span></span>  
  
<span data-ttu-id="b5d6b-148">SQL Server PowerShell 공급자를 설정 하 고 사용 하려면 [SQL Server PowerShell 공급자](../../../powershell/sql-server-powershell-provider.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="b5d6b-148">To set up and use the SQL Server PowerShell provider, see [SQL Server PowerShell Provider](../../../powershell/sql-server-powershell-provider.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="b5d6b-149">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b5d6b-149">See Also</span></span>  
 [<span data-ttu-id="b5d6b-150">AlwaysOn 가용성 그룹 &#40;SQL Server 개요&#41;</span><span class="sxs-lookup"><span data-stu-id="b5d6b-150">Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](overview-of-always-on-availability-groups-sql-server.md)  
