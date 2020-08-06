---
title: 자동 장애 조치 (Failover)의 조건 (Always On 가용성 그룹)을 제어 하는 유연한 장애 조치 (Failover) 정책을 구성 합니다. Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], flexible failover policy
- Availability Groups [SQL Server], failover
- failover [SQL Server], AlwaysOn Availability Groups
ms.assetid: 1ed564b4-9835-4245-ae35-9ba67419a4ce
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c938624a3ed39fe2d41f21a21af5231aa76a8c17
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740504"
---
# <a name="configure-the-flexible-failover-policy-to-control-conditions-for-automatic-failover-always-on-availability-groups"></a><span data-ttu-id="49eef-102">유연한 장애 조치(failover) 정책을 구성하여 자동 장애 조치(failover)의 상태 제어(Always On 가용성 그룹)</span><span class="sxs-lookup"><span data-stu-id="49eef-102">Configure the Flexible Failover Policy to Control Conditions for Automatic Failover (Always On Availability Groups)</span></span>
  <span data-ttu-id="49eef-103">이 항목에서는 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 에서 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]또는 PowerShell을 사용하여 AlwaysOn 가용성 그룹에 대해 유연한 장애 조치(failover) 정책을 구성하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="49eef-103">This topic describes how to configure the flexible failover policy for an AlwaysOn availability group by using [!INCLUDE[tsql](../../../includes/tsql-md.md)] or PowerShell in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="49eef-104">유연한 장애 조치(failover) 정책을 통해 가용성 그룹에 대해 자동 장애 조치를 수행해야 하는 상태를 세부적으로 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="49eef-104">A flexible failover policy provides granular control over the conditions that cause automatic failover for an availability group.</span></span> <span data-ttu-id="49eef-105">자동 장애 조치를 트리거하는 오류 상태 및 상태 확인 빈도를 변경하여 자동 장애 조치가 수행될 가능성을 높이거나 줄임으로써 고가용성에 대한 SLA를 지원할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="49eef-105">By changing the failure conditions that trigger an automatic failover and the frequency of health checks, you can increase or decrease the likelihood of an automatic failover to support your SLA for high availability.</span></span>  
  
  
  
    > [!NOTE]  
    >  The flexible failover policy of an availability group cannot be configured by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)].  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="49eef-106">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="49eef-106">Before You Begin</span></span>  
  
###  <a name="limitations-on-automatic-failovers"></a><a name="Limitations"></a><span data-ttu-id="49eef-107">자동 장애 조치에 대 한 제한 사항</span><span class="sxs-lookup"><span data-stu-id="49eef-107">Limitations on Automatic Failovers</span></span>  
  
-   <span data-ttu-id="49eef-108">자동 장애 조치가 발생하려면 현재 주 복제본과 하나의 보조 복제본을 자동 장애 조치를 사용하는 동기-커밋 가용성 모드용으로 구성하고 보조 복제본을 주 복제본과 동기화해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="49eef-108">For an automatic failover to occur, the current primary replica and one secondary replica must be configured for synchronous-commit availability mode with automatic failover and the secondary replica must be synchronized with the primary replica.</span></span>  
  
-   <span data-ttu-id="49eef-109">가용성 그룹이 해당 WSFC 오류 임계값을 초과하면 WSFC 클러스터가 가용성 그룹에 대해 자동 장애 조치를 시도하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="49eef-109">If an availability group exceeds its WSFC failure threshold, the WSFC cluster will not attempt an automatic failover for the availability group.</span></span> <span data-ttu-id="49eef-110">또한 클러스터 관리자가 실패한 리소스 그룹을 수동으로 온라인 상태로 만들거나 데이터베이스 관리자가 가용성 그룹의 수동 장애 조치를 수행할 때까지 가용성 그룹의 WSFC 리소스 그룹이 실패한 상태로 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="49eef-110">Furthermore, the WSFC resource group of the availability group remains in a failed state until either the cluster administrator manually brings the failed resource group online or the database administrator performs a manual failover of the availability group.</span></span> <span data-ttu-id="49eef-111">*WSFC 오류 임계값* 은 특정 기간 동안 가용성 그룹에 대해 지원되는 최대 오류 수로 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="49eef-111">The *WSFC failure threshold* is defined as the maximum number of failures supported for the availability group during a given time period.</span></span> <span data-ttu-id="49eef-112">기본 기간은 6시간이며, 이 기간 동안의 최대 오류 수에 대한 기본값은 *n*-1입니다. 여기서 *n* 은 WSFC 노드의 수입니다.</span><span class="sxs-lookup"><span data-stu-id="49eef-112">The default time period is six hours, and the default value for the maximum number of failures during this period is *n*-1, where *n* is the number of WSFC nodes.</span></span> <span data-ttu-id="49eef-113">지정된 가용성 그룹에 대한 오류-임계값 값을 변경하려면 WSFC 장애 조치(Failover) 관리자 콘솔을 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="49eef-113">To change the failure-threshold values for a given availability group, use the WSFC Failover Manager Console.</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="49eef-114">필수 조건</span><span class="sxs-lookup"><span data-stu-id="49eef-114">Prerequisites</span></span>  
  
-   <span data-ttu-id="49eef-115">주 복제본을 호스팅하는 서버 인스턴스에 연결되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="49eef-115">You must be connected to the server instance that hosts the primary replica.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="49eef-116">보안</span><span class="sxs-lookup"><span data-stu-id="49eef-116">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="49eef-117">권한</span><span class="sxs-lookup"><span data-stu-id="49eef-117">Permissions</span></span>  
  
|<span data-ttu-id="49eef-118">Task</span><span class="sxs-lookup"><span data-stu-id="49eef-118">Task</span></span>|<span data-ttu-id="49eef-119">사용 권한</span><span class="sxs-lookup"><span data-stu-id="49eef-119">Permissions</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="49eef-120">새로운 가용성 그룹에 대해 유연한 장애 조치(failover) 정책을 구성하려면</span><span class="sxs-lookup"><span data-stu-id="49eef-120">To configure the flexible failover policy for a new availability group</span></span>|<span data-ttu-id="49eef-121">CREATE AVAILABILITY GROUP 서버 권한, ALTER ANY AVAILABILITY GROUP 권한, CONTROL SERVER 권한 중 하나와 **sysadmin** 고정 서버 역할의 멤버 자격이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="49eef-121">Requires membership in the **sysadmin** fixed server role and either CREATE AVAILABILITY GROUP server permission, ALTER ANY AVAILABILITY GROUP permission, or CONTROL SERVER permission.</span></span>|  
|<span data-ttu-id="49eef-122">기존 가용성 그룹의 정책을 수정하려면</span><span class="sxs-lookup"><span data-stu-id="49eef-122">To modify the policy of an existing availability group</span></span>|<span data-ttu-id="49eef-123">가용성 그룹에 대한 ALTER AVAILABILITY GROUP 권한, CONTROL AVAILABILITY GROUP 권한, ALTER ANY AVAILABILITY GROUP 권한 또는 CONTROL SERVER 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="49eef-123">Requires ALTER AVAILABILITY GROUP permission on the availability group, CONTROL AVAILABILITY GROUP permission, ALTER ANY AVAILABILITY GROUP permission, or CONTROL SERVER permission.</span></span>|  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="49eef-124">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="49eef-124">Using Transact-SQL</span></span>  
 <span data-ttu-id="49eef-125">**유연한 장애 조치(failover) 정책을 구성하려면**</span><span class="sxs-lookup"><span data-stu-id="49eef-125">**To configure the flexible failover policy**</span></span>  
  
1.  <span data-ttu-id="49eef-126">주 복제본을 호스팅하는 서버 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="49eef-126">Connect to the server instance that hosts the primary replica.</span></span>  
  
2.  <span data-ttu-id="49eef-127">새 가용성 그룹의 경우 [CREATE AVAILABILITY group](/sql/t-sql/statements/create-availability-group-transact-sql) [!INCLUDE[tsql](../../../includes/tsql-md.md)] 문을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="49eef-127">For a new availability group, use the [CREATE AVAILABILITY GROUP](/sql/t-sql/statements/create-availability-group-transact-sql)[!INCLUDE[tsql](../../../includes/tsql-md.md)] statement.</span></span> <span data-ttu-id="49eef-128">기존 가용성 그룹을 수정 하는 경우 [ALTER AVAILABILITY group](/sql/t-sql/statements/alter-availability-group-transact-sql) [!INCLUDE[tsql](../../../includes/tsql-md.md)] 문을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="49eef-128">If you are modifying an existing availability group, use the [ALTER AVAILABILITY GROUP](/sql/t-sql/statements/alter-availability-group-transact-sql)[!INCLUDE[tsql](../../../includes/tsql-md.md)] statement.</span></span>  
  
    -   <span data-ttu-id="49eef-129">장애 조치 상태 수준을 설정하려면 FAILURE_CONDITION_LEVEL = *n* 옵션을 사용합니다. 여기서 *n* 은 1부터 5까지의 정수입니다.</span><span class="sxs-lookup"><span data-stu-id="49eef-129">To set the failover condition level, use the FAILURE_CONDITION_LEVEL = *n* option, where, *n* is an integer from 1 to 5.</span></span>  
  
         <span data-ttu-id="49eef-130">예를 들어 다음 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 문은 기존 가용성 그룹 `AG1`의 오류 상태 수준을 수준 1로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="49eef-130">For example, the following [!INCLUDE[tsql](../../../includes/tsql-md.md)] statement changes the failure-condition level of an existing availability group, `AG1`, to level one:</span></span>  
  
        ```sql
        ALTER AVAILABILITY GROUP AG1 SET (FAILURE_CONDITION_LEVEL = 1);  
        ```  
  
         <span data-ttu-id="49eef-131">각 정수 값과 오류 상태 수준의 관계는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="49eef-131">The relationship of these integer values to the failure condition levels is as follows:</span></span>  
  
        |[!INCLUDE[tsql](../../../includes/tsql-md.md)] <span data-ttu-id="49eef-132">값</span><span class="sxs-lookup"><span data-stu-id="49eef-132">Value</span></span>|<span data-ttu-id="49eef-133">Level</span><span class="sxs-lookup"><span data-stu-id="49eef-133">Level</span></span>|<span data-ttu-id="49eef-134">자동 장애 조치가 시작되는 경우</span><span class="sxs-lookup"><span data-stu-id="49eef-134">Automatic Is Failover Initiated When...</span></span>|  
        |------------------------------|-----------|-------------------------------------------|  
        |<span data-ttu-id="49eef-135">1</span><span class="sxs-lookup"><span data-stu-id="49eef-135">1</span></span>|<span data-ttu-id="49eef-136">하나</span><span class="sxs-lookup"><span data-stu-id="49eef-136">One</span></span>|<span data-ttu-id="49eef-137">서버 작동 중지 시.</span><span class="sxs-lookup"><span data-stu-id="49eef-137">On server down.</span></span> <span data-ttu-id="49eef-138">장애 조치나 재시작으로 인해 SQL Server 서비스가 중지된 경우</span><span class="sxs-lookup"><span data-stu-id="49eef-138">The SQL Server service stops because of a failover or restart.</span></span>|  
        |<span data-ttu-id="49eef-139">2</span><span class="sxs-lookup"><span data-stu-id="49eef-139">2</span></span>|<span data-ttu-id="49eef-140">2</span><span class="sxs-lookup"><span data-stu-id="49eef-140">Two</span></span>|<span data-ttu-id="49eef-141">서버 응답 없음 발생 시.</span><span class="sxs-lookup"><span data-stu-id="49eef-141">On server unresponsive.</span></span> <span data-ttu-id="49eef-142">낮은 값의 조건이 모두 충족되거나, SQL Server 서비스가 클러스터에 연결되었지만 상태 확인 제한 시간 임계값을 초과했거나, 현재 주 복제본이 오류 상태인 경우</span><span class="sxs-lookup"><span data-stu-id="49eef-142">Any condition of lower value is satisfied, the SQL Server service is connected to the cluster and the health check timeout threshold is exceeded, or the current primary replica is in a failed state.</span></span>|  
        |<span data-ttu-id="49eef-143">3</span><span class="sxs-lookup"><span data-stu-id="49eef-143">3</span></span>|<span data-ttu-id="49eef-144">3</span><span class="sxs-lookup"><span data-stu-id="49eef-144">Three</span></span>|<span data-ttu-id="49eef-145">중대 서버 오류 발생 시.</span><span class="sxs-lookup"><span data-stu-id="49eef-145">On critical server error.</span></span> <span data-ttu-id="49eef-146">낮은 값의 조건이 모두 충족되거나 내부 중대 서버 오류가 발생한 경우</span><span class="sxs-lookup"><span data-stu-id="49eef-146">Any condition of lower value is satisfied or an internal critical server error occurs.</span></span><br /><br /> <span data-ttu-id="49eef-147">이 값은 기본 수준입니다.</span><span class="sxs-lookup"><span data-stu-id="49eef-147">This is the default level.</span></span>|  
        |<span data-ttu-id="49eef-148">4</span><span class="sxs-lookup"><span data-stu-id="49eef-148">4</span></span>|<span data-ttu-id="49eef-149">4</span><span class="sxs-lookup"><span data-stu-id="49eef-149">Four</span></span>|<span data-ttu-id="49eef-150">일반 서버 오류 발생 시.</span><span class="sxs-lookup"><span data-stu-id="49eef-150">On moderate server error.</span></span> <span data-ttu-id="49eef-151">낮은 값의 조건이 모두 충족되거나 일반 서버 오류가 발생한 경우</span><span class="sxs-lookup"><span data-stu-id="49eef-151">Any condition of lower value is satisfied or a moderate Server error occurs.</span></span>|  
        |<span data-ttu-id="49eef-152">5</span><span class="sxs-lookup"><span data-stu-id="49eef-152">5</span></span>|<span data-ttu-id="49eef-153">5</span><span class="sxs-lookup"><span data-stu-id="49eef-153">Five</span></span>|<span data-ttu-id="49eef-154">지정된 오류 상태 발생 시.</span><span class="sxs-lookup"><span data-stu-id="49eef-154">On any qualified failure conditions.</span></span> <span data-ttu-id="49eef-155">낮은 값의 조건이 모두 충족되거나 지정된 오류 상태가 발생한 경우</span><span class="sxs-lookup"><span data-stu-id="49eef-155">Any condition of lower value is satisfied or a qualifying failure condition occurs.</span></span>|  
  
         <span data-ttu-id="49eef-156">장애 조치 상태 수준에 대한 자세한 내용은 [가용성 그룹 자동 장애 조치에 대한 유연한 장애 조치(Failover) 정책&#40;SQL Server&#41;](flexible-automatic-failover-policy-availability-group.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="49eef-156">For more information about the failover condition levels, see [Flexible Failover Policy for Automatic Failover of an Availability Group &#40;SQL Server&#41;](flexible-automatic-failover-policy-availability-group.md).</span></span>  
  
    -   <span data-ttu-id="49eef-157">상태 확인 제한 시간 임계값을 구성하려면 HEALTH_CHECK_TIMEOUT = *n* 옵션을 사용합니다. 여기서 *n* 은 15000밀리초(15초)부터 4294967295밀리초까지의 정수입니다.</span><span class="sxs-lookup"><span data-stu-id="49eef-157">To configure the health check timeout threshold, use the HEALTH_CHECK_TIMEOUT = *n* option, where, *n* is an integer from 15000 milliseconds (15 seconds) to 4294967295 milliseconds.</span></span> <span data-ttu-id="49eef-158">기본값은 30000밀리초(30초)입니다.</span><span class="sxs-lookup"><span data-stu-id="49eef-158">The default value is 30000 milliseconds (30 seconds)</span></span>  
  
         <span data-ttu-id="49eef-159">예를 들어 다음 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 문은 기존 가용성 그룹 `AG1`의 상태 확인 제한 시간 임계값을 60,000밀리초(1분)로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="49eef-159">For example, the following [!INCLUDE[tsql](../../../includes/tsql-md.md)] statement changes the health-check timeout threshold of an existing availability group, `AG1`, to 60,000 milliseconds (one minute).</span></span>  
  
        ```sql
        ALTER AVAILABILITY GROUP AG1 SET (HEALTH_CHECK_TIMEOUT = 60000);  
        ```  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a> <span data-ttu-id="49eef-160">PowerShell 사용</span><span class="sxs-lookup"><span data-stu-id="49eef-160">Using PowerShell</span></span>  

### <a name="to-configure-the-flexible-failover-policy"></a><span data-ttu-id="49eef-161">유연한 장애 조치 (failover) 정책을 구성 하려면 \* \*</span><span class="sxs-lookup"><span data-stu-id="49eef-161">To configure the flexible failover policy\*\*</span></span>  
  
1.  <span data-ttu-id="49eef-162">기본값(`cd`)을 주 복제본을 호스팅하는 서버 인스턴스로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="49eef-162">Set default (`cd`) to the server instance that hosts the primary replica.</span></span>  
  
2.  <span data-ttu-id="49eef-163">가용성 그룹에 가용성 복제본을 추가하는 경우 `New-SqlAvailabilityGroup` cmdlet을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="49eef-163">When adding an availability replica to an availability group, use the `New-SqlAvailabilityGroup` cmdlet.</span></span> <span data-ttu-id="49eef-164">기존 가용성 복제본을 수정하는 경우 `Set-SqlAvailabilityGroup` cmdlet을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="49eef-164">When modifying an existing availability replica, use the `Set-SqlAvailabilityGroup` cmdlet.</span></span>  
  
    -   <span data-ttu-id="49eef-165">장애 조치 (failover) 상태 수준을 설정 하려면 `FailureConditionLevel` *level* 매개 변수를 사용 합니다. 여기서 *level* 은 다음 값 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="49eef-165">To set the failover condition level, use the `FailureConditionLevel`*level* parameter, where, *level* is one of the following values:</span></span>  
  
        |<span data-ttu-id="49eef-166">값</span><span class="sxs-lookup"><span data-stu-id="49eef-166">Value</span></span>|<span data-ttu-id="49eef-167">Level</span><span class="sxs-lookup"><span data-stu-id="49eef-167">Level</span></span>|<span data-ttu-id="49eef-168">자동 장애 조치가 시작되는 경우</span><span class="sxs-lookup"><span data-stu-id="49eef-168">Automatic Is Failover Initiated When...</span></span>|  
        |-----------|-----------|-------------------------------------------|  
        |`OnServerDown`|<span data-ttu-id="49eef-169">하나</span><span class="sxs-lookup"><span data-stu-id="49eef-169">One</span></span>|<span data-ttu-id="49eef-170">서버 작동 중지 시.</span><span class="sxs-lookup"><span data-stu-id="49eef-170">On server down.</span></span> <span data-ttu-id="49eef-171">장애 조치나 재시작으로 인해 SQL Server 서비스가 중지된 경우</span><span class="sxs-lookup"><span data-stu-id="49eef-171">The SQL Server service stops because of a failover or restart.</span></span>|  
        |`OnServerUnresponsive`|<span data-ttu-id="49eef-172">2</span><span class="sxs-lookup"><span data-stu-id="49eef-172">Two</span></span>|<span data-ttu-id="49eef-173">서버 응답 없음 발생 시.</span><span class="sxs-lookup"><span data-stu-id="49eef-173">On server unresponsive.</span></span> <span data-ttu-id="49eef-174">낮은 값의 조건이 모두 충족되거나, SQL Server 서비스가 클러스터에 연결되었지만 상태 확인 제한 시간 임계값을 초과했거나, 현재 주 복제본이 오류 상태인 경우</span><span class="sxs-lookup"><span data-stu-id="49eef-174">Any condition of lower value is satisfied, the SQL Server service is connected to the cluster and the health check timeout threshold is exceeded, or the current primary replica is in a failed state.</span></span>|  
        |`OnCriticalServerError`|<span data-ttu-id="49eef-175">3</span><span class="sxs-lookup"><span data-stu-id="49eef-175">Three</span></span>|<span data-ttu-id="49eef-176">중대 서버 오류 발생 시.</span><span class="sxs-lookup"><span data-stu-id="49eef-176">On critical server error.</span></span> <span data-ttu-id="49eef-177">낮은 값의 조건이 모두 충족되거나 내부 중대 서버 오류가 발생한 경우</span><span class="sxs-lookup"><span data-stu-id="49eef-177">Any condition of lower value is satisfied or an internal critical server error occurs.</span></span><br /><br /> <span data-ttu-id="49eef-178">이 값은 기본 수준입니다.</span><span class="sxs-lookup"><span data-stu-id="49eef-178">This is the default level.</span></span>|  
        |`OnModerateServerError`|<span data-ttu-id="49eef-179">4</span><span class="sxs-lookup"><span data-stu-id="49eef-179">Four</span></span>|<span data-ttu-id="49eef-180">일반 서버 오류 발생 시.</span><span class="sxs-lookup"><span data-stu-id="49eef-180">On moderate server error.</span></span> <span data-ttu-id="49eef-181">낮은 값의 조건이 모두 충족되거나 일반 서버 오류가 발생한 경우</span><span class="sxs-lookup"><span data-stu-id="49eef-181">Any condition of lower value is satisfied or a moderate Server error occurs.</span></span>|  
        |`OnAnyQualifiedFailureConditions`|<span data-ttu-id="49eef-182">5</span><span class="sxs-lookup"><span data-stu-id="49eef-182">Five</span></span>|<span data-ttu-id="49eef-183">지정된 오류 상태 발생 시.</span><span class="sxs-lookup"><span data-stu-id="49eef-183">On any qualified failure conditions.</span></span> <span data-ttu-id="49eef-184">낮은 값의 조건이 모두 충족되거나 지정된 오류 상태가 발생한 경우</span><span class="sxs-lookup"><span data-stu-id="49eef-184">Any condition of lower value is satisfied or a qualifying failure condition occurs.</span></span>|  
  
         <span data-ttu-id="49eef-185">장애 조치 상태 수준에 대한 자세한 내용은 [가용성 그룹 자동 장애 조치에 대한 유연한 장애 조치(Failover) 정책&#40;SQL Server&#41;](flexible-automatic-failover-policy-availability-group.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="49eef-185">For more information about the failover condition levels, see [Flexible Failover Policy for Automatic Failover of an Availability Group &#40;SQL Server&#41;](flexible-automatic-failover-policy-availability-group.md).</span></span>  
  
         <span data-ttu-id="49eef-186">예를 들어 다음 명령은 기존 가용성 그룹 `AG1`의 오류 상태 수준을 수준 1로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="49eef-186">For example, the following command changes the failure-condition level of an existing availability group, `AG1`, to level one.</span></span>  
  
        ```powershell
        Set-SqlAvailabilityGroup `
         -Path SQLSERVER:\Sql\PrimaryServer\InstanceName\AvailabilityGroups\MyAg `
         -FailureConditionLevel OnServerDown  
        ```  
  
    -   <span data-ttu-id="49eef-187">상태 확인 제한 시간 임계값을 설정 하려면 `HealthCheckTimeout` *n* 매개 변수를 사용 합니다. 여기서 *n* 은 15000 밀리초 (15 초)에서 4294967295 밀리초 사이의 정수입니다.</span><span class="sxs-lookup"><span data-stu-id="49eef-187">To set the health check timeout threshold, use the `HealthCheckTimeout`*n* parameter, where, *n* is an integer from 15000 milliseconds (15 seconds) to 4294967295 milliseconds.</span></span> <span data-ttu-id="49eef-188">기본값은 30000밀리초(30초)입니다.</span><span class="sxs-lookup"><span data-stu-id="49eef-188">The default value is 30000 milliseconds (30 seconds).</span></span>  
  
         <span data-ttu-id="49eef-189">예를 들어 다음 명령은 기존 가용성 그룹 `AG1`의 상태 확인 제한 시간 임계값을 120,000밀리초(2분)로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="49eef-189">For example, the following command changes the health-check timeout threshold of an existing availability group, `AG1`, to 120,000 milliseconds (two minutes).</span></span>  
  
        ```powershell
        Set-SqlAvailabilityGroup `
         -Path SQLSERVER:\Sql\PrimaryServer\InstanceName\AvailabilityGroups\MyAG `
         -HealthCheckTimeout 120000  
        ```  
  
> [!NOTE]  
>  <span data-ttu-id="49eef-190">cmdlet의 구문을 보려면 `Get-Help` PowerShell 환경에서 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] cmdlet을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="49eef-190">To view the syntax of a cmdlet, use the `Get-Help` cmdlet in the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell environment.</span></span> <span data-ttu-id="49eef-191">자세한 내용은 [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="49eef-191">For more information, see [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).</span></span>  
  
 <span data-ttu-id="49eef-192">**SQL Server PowerShell 공급자를 설정하고 사용하려면**</span><span class="sxs-lookup"><span data-stu-id="49eef-192">**To set up and use the SQL Server PowerShell provider**</span></span>  
  
-   [<span data-ttu-id="49eef-193">SQL Server PowerShell 공급자</span><span class="sxs-lookup"><span data-stu-id="49eef-193">SQL Server PowerShell Provider</span></span>](../../../powershell/sql-server-powershell-provider.md)  
  
-   [<span data-ttu-id="49eef-194">Get Help SQL Server PowerShell</span><span class="sxs-lookup"><span data-stu-id="49eef-194">Get Help SQL Server PowerShell</span></span>](../../../powershell/sql-server-powershell.md)  
  
## <a name="see-also"></a><span data-ttu-id="49eef-195">참고 항목</span><span class="sxs-lookup"><span data-stu-id="49eef-195">See Also</span></span>  
 <span data-ttu-id="49eef-196">[AlwaysOn 가용성 그룹 &#40;SQL Server 개요&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="49eef-196">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="49eef-197">[가용성 모드 (AlwaysOn 가용성 그룹)](availability-modes-always-on-availability-groups.md) </span><span class="sxs-lookup"><span data-stu-id="49eef-197">[Availability Modes (AlwaysOn Availability Groups)](availability-modes-always-on-availability-groups.md) </span></span>  
 <span data-ttu-id="49eef-198">[장애 조치 (failover) 및 장애 조치 (failover) 모드 &#40;AlwaysOn 가용성 그룹&#41;](failover-and-failover-modes-always-on-availability-groups.md) </span><span class="sxs-lookup"><span data-stu-id="49eef-198">[Failover and Failover Modes &#40;AlwaysOn Availability Groups&#41;](failover-and-failover-modes-always-on-availability-groups.md) </span></span>  
 <span data-ttu-id="49eef-199">[SQL Server의 WSFC&#40;Windows Server 장애 조치(failover) 클러스터링&#41;](../../../sql-server/failover-clusters/windows/windows-server-failover-clustering-wsfc-with-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="49eef-199">[Windows Server Failover Clustering &#40;WSFC&#41; with SQL Server](../../../sql-server/failover-clusters/windows/windows-server-failover-clustering-wsfc-with-sql-server.md) </span></span>  
 <span data-ttu-id="49eef-200">[장애 조치(failover) 클러스터 인스턴스용 장애 조치(failover) 정책](../../../sql-server/failover-clusters/windows/failover-policy-for-failover-cluster-instances.md) </span><span class="sxs-lookup"><span data-stu-id="49eef-200">[Failover Policy for Failover Cluster Instances](../../../sql-server/failover-clusters/windows/failover-policy-for-failover-cluster-instances.md) </span></span>  
 [<span data-ttu-id="49eef-201">sp_server_diagnostics&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="49eef-201">sp_server_diagnostics &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-server-diagnostics-transact-sql)  
