---
title: AlwaysOn 가용성 그룹 (SQL Server) 사용 및 사용 안 함 Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], server instance
- Availability Groups [SQL Server], deploying
- Availability Groups [SQL Server], disabling
- Availability Groups [SQL Server], enabling
ms.assetid: 7c326958-5ae9-4761-9c57-905972276a8f
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 585f1d86d328b7c5027241310108d102b56ca327
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647249"
---
# <a name="enable-and-disable-alwayson-availability-groups-sql-server"></a><span data-ttu-id="6e150-102">AlwaysOn 가용성 그룹 활성화 및 비활성화(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="6e150-102">Enable and Disable AlwaysOn Availability Groups (SQL Server)</span></span>
  <span data-ttu-id="6e150-103">먼저 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 을 사용하도록 설정해야만 서버 인스턴스에서 가용성 그룹을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6e150-103">Enabling [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] is a prerequisite for a server instance to use availability groups.</span></span> <span data-ttu-id="6e150-104">가용성 그룹을 만들고 구성하려면 먼저 하나 이상의 가용성 그룹에 대한 가용성 복제본을 호스팅할 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 의 각 인스턴스에서 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 기능을 사용하도록 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6e150-104">Before you can create and configure any availability group, the [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] feature must have been enabled on the each instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] that will host an availability replica for one or more availability groups.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="6e150-105">WSFC 클러스터를 삭제한 다음 다시 만들려는 경우 원본 WSFC 클러스터에서 가용성 복제본을 호스팅한 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 의 각 인스턴스에서 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 기능을 사용하지 않도록 설정한 후 다시 사용하도록 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6e150-105">If you delete and re-create a WSFC cluster, you must disable and re-enable the [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] feature on each instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] that hosted an availability replica on the original WSFC cluster.</span></span>  
  
-   <span data-ttu-id="6e150-106">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="6e150-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="6e150-107">필수 구성 요소</span><span class="sxs-lookup"><span data-stu-id="6e150-107">Prerequisites</span></span>](#Prerequisites)  
  
     [<span data-ttu-id="6e150-108">보안</span><span class="sxs-lookup"><span data-stu-id="6e150-108">Security</span></span>](#Security)  
  
-   <span data-ttu-id="6e150-109">**어떻게:**</span><span class="sxs-lookup"><span data-stu-id="6e150-109">**How To:**</span></span>  
  
    -   [<span data-ttu-id="6e150-110">AlwaysOn 가용성 그룹을 사용할 수 있는지 여부 확인</span><span class="sxs-lookup"><span data-stu-id="6e150-110">Determine Whether AlwaysOn Availability Groups is Enabled</span></span>](#IsEnabled)  
  
    -   [<span data-ttu-id="6e150-111">AlwaysOn 가용성 그룹 사용</span><span class="sxs-lookup"><span data-stu-id="6e150-111">Enable AlwaysOn Availability Groups</span></span>](#EnableAOAG)  
  
    -   [<span data-ttu-id="6e150-112">AlwaysOn 가용성 그룹을 사용하지 않도록 설정</span><span class="sxs-lookup"><span data-stu-id="6e150-112">Disable AlwaysOn Availability Groups</span></span>](#DisableAOAG)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="6e150-113">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="6e150-113">Before You Begin</span></span>  
  
###  <a name="prerequisites-for-enabling-alwayson-availability-groups"></a><a name="Prerequisites"></a><span data-ttu-id="6e150-114">AlwaysOn 가용성 그룹 사용을 위한 필수 구성 요소</span><span class="sxs-lookup"><span data-stu-id="6e150-114">Prerequisites for Enabling AlwaysOn Availability Groups</span></span>  
  
-   <span data-ttu-id="6e150-115">서버 인스턴스는 WSFC(Windows Server 장애 조치(failover) 클러스터링) 노드에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6e150-115">The server instance must reside on a Windows Server Failover Clustering (WSFC) node.</span></span>  
  
-   <span data-ttu-id="6e150-116">서버 인스턴스는 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]을 지원하는 SQL Server 버전을 실행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6e150-116">The server instance must be running an edition of SQL Server that supports [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)].</span></span> <span data-ttu-id="6e150-117">자세한 내용은 [Features Supported by the Editions of SQL Server 2014](../../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6e150-117">For more information, see [Features Supported by the Editions of SQL Server 2014](../../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span>  
  
-   <span data-ttu-id="6e150-118">한 번에 한 서버 인스턴스에서만 AlwaysOn 가용성 그룹을 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="6e150-118">Enable AlwaysOn Availability Groups on only one server instance at a time.</span></span> <span data-ttu-id="6e150-119">AlwaysOn 가용성 그룹을 사용하도록 설정한 후에는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 서비스가 다시 시작될 때까지 기다렸다가 다음 서버 인스턴스로 진행하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="6e150-119">After enabling AlwaysOn Availability Groups, wait until the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] service has restarted before you proceed to another server instance.</span></span>  
  
 <span data-ttu-id="6e150-120">가용성 그룹을 만들고 구성 하기 위한 추가 필수 구성 요소에 대 한 자세한 내용은 [AlwaysOn 가용성 그룹 &#40;SQL Server&#41;에 대 한 필수 조건, 제한 사항 및 권장 사항 ](prereqs-restrictions-recommendations-always-on-availability.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="6e150-120">For information about additional prerequisites for creating and configuring availability groups, see [Prerequisites, Restrictions, and Recommendations for AlwaysOn Availability Groups &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="6e150-121">보안</span><span class="sxs-lookup"><span data-stu-id="6e150-121">Security</span></span>  
 <span data-ttu-id="6e150-122">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]의 한 인스턴스에서 AlwaysOn 가용성 그룹을 사용할 수 있는 동안에는 서버 인스턴스가 WSFC 클러스터에 대한 모든 권한을 가집니다.</span><span class="sxs-lookup"><span data-stu-id="6e150-122">While AlwaysOn Availability Groups is enabled on an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], the server instance has full control on the WSFC cluster.</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="6e150-123">권한</span><span class="sxs-lookup"><span data-stu-id="6e150-123">Permissions</span></span>  
 <span data-ttu-id="6e150-124">로컬 컴퓨터 **관리자** 그룹의 멤버 자격과 WSFC 클러스터에 대한 모든 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="6e150-124">Requires membership in the **Administrator** group on the local computer and full control on the WSFC cluster.</span></span> <span data-ttu-id="6e150-125">Powershell을 사용하여 AlwaysOn을 사용하도록 설정하는 경우 **관리자 권한으로 실행** 옵션을 사용하여 명령 프롬프트 창을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="6e150-125">When enabling AlwaysOn by using PowerShell, open the Command Prompt window using the **Run as administrator** option.</span></span>  
  
 <span data-ttu-id="6e150-126">Active Directory 개체 만들기 및 개체 관리 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="6e150-126">Requires Active Directory Create Objects and Manage Objects permissions.</span></span>  
  
##  <a name="determine-whether-alwayson-availability-groups-is-enabled"></a><a name="IsEnabled"></a><span data-ttu-id="6e150-127">AlwaysOn 가용성 그룹 사용 여부 확인</span><span class="sxs-lookup"><span data-stu-id="6e150-127">Determine Whether AlwaysOn Availability Groups is Enabled</span></span>  
  
-   [<span data-ttu-id="6e150-128">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="6e150-128">SQL Server Management Studio</span></span>](#SSMS1Procedure)  
  
-   [<span data-ttu-id="6e150-129">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="6e150-129">Transact-SQL</span></span>](#Tsql1Procedure)  
  
-   [<span data-ttu-id="6e150-130">PowerShell</span><span class="sxs-lookup"><span data-stu-id="6e150-130">PowerShell</span></span>](#PowerShell1Procedure)  
  
###  <a name="using-sql-server-management-studio"></a><a name="SSMS1Procedure"></a> <span data-ttu-id="6e150-131">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="6e150-131">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="6e150-132">**AlwaysOn 가용성 그룹을 사용할 수 있는지 여부를 확인하려면**</span><span class="sxs-lookup"><span data-stu-id="6e150-132">**To determine whether AlwaysOn Availability Groups is enabled**</span></span>  
  
1.  <span data-ttu-id="6e150-133">개체 탐색기에서 서버 인스턴스를 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6e150-133">In Object Explorer, right-click the server instance, and  click **Properties**.</span></span>  
  
2.  <span data-ttu-id="6e150-134">**서버 속성** 대화 상자에서 **일반** 페이지를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6e150-134">In the **Server Properties** dialog box, click the **General** page.</span></span> <span data-ttu-id="6e150-135">**HADR 사용** 속성이 다음 값 중 하나로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="6e150-135">The **Is HADR Enabled** property displays one of the following values:</span></span>  
  
    -   <span data-ttu-id="6e150-136">**True**, AlwaysOn 가용성 그룹을 사용할 수 있는 경우</span><span class="sxs-lookup"><span data-stu-id="6e150-136">**True**, if AlwaysOn Availability Groups is enabled</span></span>  
  
    -   <span data-ttu-id="6e150-137">**False**, AlwaysOn 가용성 그룹을 사용할 수 없는 경우</span><span class="sxs-lookup"><span data-stu-id="6e150-137">**False**, if AlwaysOn Availability Groups is disabled.</span></span>  
  
###  <a name="using-transact-sql"></a><a name="Tsql1Procedure"></a> <span data-ttu-id="6e150-138">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="6e150-138">Using Transact-SQL</span></span>  
 <span data-ttu-id="6e150-139">**AlwaysOn 가용성 그룹을 사용할 수 있는지 여부를 확인하려면**</span><span class="sxs-lookup"><span data-stu-id="6e150-139">**To determine whether AlwaysOn Availability Groups is enabled**</span></span>  
  
1.  <span data-ttu-id="6e150-140">다음 [SERVERPROPERTY](/sql/t-sql/functions/serverproperty-transact-sql) 문을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="6e150-140">Use the following [SERVERPROPERTY](/sql/t-sql/functions/serverproperty-transact-sql) statement:</span></span>  
  
    ```sql
    SELECT SERVERPROPERTY ('IsHadrEnabled');  
    ```  
  
     <span data-ttu-id="6e150-141">`IsHadrEnabled` 서버 속성의 설정은 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인스턴스에서 AlwaysOn 가용성 그룹을 사용할 수 있는지 여부를 다음과 같이 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="6e150-141">The setting of the `IsHadrEnabled` server property indicates whether an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] is enabled for AlwaysOn Availability Groups, as follows:</span></span>  
  
    -   <span data-ttu-id="6e150-142">`IsHadrEnabled` = 1인 경우 AlwaysOn 가용성 그룹을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6e150-142">If `IsHadrEnabled` = 1, AlwaysOn Availability Groups is enabled.</span></span>  
  
    -   <span data-ttu-id="6e150-143">`IsHadrEnabled` = 0인 경우 AlwaysOn 가용성 그룹을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6e150-143">If `IsHadrEnabled` = 0, AlwaysOn Availability Groups is disabled.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="6e150-144">서버 속성에 대 한 자세한 내용은 `IsHadrEnabled` [SERVERPROPERTY &#40;transact-sql&#41;](/sql/t-sql/functions/serverproperty-transact-sql)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="6e150-144">For more information about the `IsHadrEnabled` server property, see [SERVERPROPERTY &#40;Transact-SQL&#41;](/sql/t-sql/functions/serverproperty-transact-sql).</span></span>  
  
###  <a name="using-powershell"></a><a name="PowerShell1Procedure"></a> <span data-ttu-id="6e150-145">PowerShell 사용</span><span class="sxs-lookup"><span data-stu-id="6e150-145">Using PowerShell</span></span>  
 <span data-ttu-id="6e150-146">**AlwaysOn 가용성 그룹을 사용할 수 있는지 여부를 확인하려면**</span><span class="sxs-lookup"><span data-stu-id="6e150-146">**To determine whether AlwaysOn Availability Groups is enabled**</span></span>  
  
1.  <span data-ttu-id="6e150-147">기본값 ( `cd` )을 사용 하도록 설정할지 여부를 결정 하려는 서버 인스턴스 (예: `\SQL\NODE1\DEFAULT` )로 설정 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 합니다.</span><span class="sxs-lookup"><span data-stu-id="6e150-147">Set default (`cd`) to the server instance (e.g. `\SQL\NODE1\DEFAULT`) on which you want to determine whether [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] is enabled.</span></span>  
  
2.  <span data-ttu-id="6e150-148">다음 PowerShell `Get-Item` 명령을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="6e150-148">Enter the following PowerShell `Get-Item` command:</span></span>  
  
    ```powershell
    Get-Item . | Select IsHadrEnabled  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="6e150-149">cmdlet의 구문을 보려면 `Get-Help` PowerShell 환경에서 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] cmdlet을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="6e150-149">To view the syntax of a cmdlet, use the `Get-Help` cmdlet in the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell environment.</span></span> <span data-ttu-id="6e150-150">자세한 내용은 [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6e150-150">For more information, see [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).</span></span>  
  
 <span data-ttu-id="6e150-151">**SQL Server PowerShell 공급자를 설정하고 사용하려면**</span><span class="sxs-lookup"><span data-stu-id="6e150-151">**To set up and use the SQL Server PowerShell provider**</span></span>  
  
-   [<span data-ttu-id="6e150-152">SQL Server PowerShell 공급자</span><span class="sxs-lookup"><span data-stu-id="6e150-152">SQL Server PowerShell Provider</span></span>](../../../powershell/sql-server-powershell-provider.md)  
  
##  <a name="enable-alwayson-availability-groups"></a><a name="EnableAOAG"></a> <span data-ttu-id="6e150-153">AlwaysOn 가용성 그룹 사용</span><span class="sxs-lookup"><span data-stu-id="6e150-153">Enable AlwaysOn Availability Groups</span></span>  
 <span data-ttu-id="6e150-154">**AlwaysOn을 사용하도록 설정하려면:**</span><span class="sxs-lookup"><span data-stu-id="6e150-154">**To enable AlwaysOn, using:**</span></span>  
  
-   [<span data-ttu-id="6e150-155">SQL Server 구성 관리자</span><span class="sxs-lookup"><span data-stu-id="6e150-155">SQL Server Configuration Manager</span></span>](#SQLCM2Procedure)  
  
-   [<span data-ttu-id="6e150-156">PowerShell</span><span class="sxs-lookup"><span data-stu-id="6e150-156">PowerShell</span></span>](#PScmd2Procedure)  
  
###  <a name="using-sql-server-configuration-manager"></a><a name="SQLCM2Procedure"></a> <span data-ttu-id="6e150-157">SQL Server 구성 관리자 사용</span><span class="sxs-lookup"><span data-stu-id="6e150-157">Using SQL Server Configuration Manager</span></span>  
 <span data-ttu-id="6e150-158">**AlwaysOn 가용성 그룹을 사용하도록 설정하려면**</span><span class="sxs-lookup"><span data-stu-id="6e150-158">**To enable AlwaysOn Availability Groups**</span></span>  
  
1.  <span data-ttu-id="6e150-159">AlwaysOn 가용성 그룹을 사용하도록 설정할 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인스턴스를 호스팅하는 WSFC(Windows Server 장애 조치(failover) 클러스터링) 노드에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="6e150-159">Connect to the Windows Server Failover Clustering (WSFC) node that hosts the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instance where you want to enable AlwaysOn Availability Groups.</span></span>  
  
2.  <span data-ttu-id="6e150-160">**시작** 메뉴에서 **모든 프로그램**, [!INCLUDE[ssCurrentUI](../../../includes/sscurrentui-md.md)], **구성 도구**를 차례로 가리킨 다음 **SQL Server 구성 관리자**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6e150-160">On the **Start** menu, point to **All Programs**, point to [!INCLUDE[ssCurrentUI](../../../includes/sscurrentui-md.md)], point to **Configuration Tools**, and  click **SQL Server Configuration Manager**.</span></span>  
  
3.  <span data-ttu-id="6e150-161">**SQL Server 구성 관리자**에서 **SQL Server Services**를 클릭 하 고 SQL Server (\*\* < *`instance name`*>)\*\* 을 마우스 오른쪽 단추로 클릭 **<*`instance name`*>** 한 다음 속성을 클릭 **합니다.** 여기서은 AlwaysOn 가용성 그룹를 사용 하도록 설정할 로컬 서버 인스턴스의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="6e150-161">In **SQL Server Configuration Manager**, click **SQL Server Services**, right-click SQL Server (**<*`instance name`*>)**, where **<*`instance name`*>** is the name of a local server instance for which you want to enable AlwaysOn Availability Groups, and click **Properties.**</span></span>  
  
4.  <span data-ttu-id="6e150-162">**AlwaysOn 고가용성** 탭을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6e150-162">Select the **AlwaysOn High Availability** tab.</span></span>  
  
5.  <span data-ttu-id="6e150-163">**Windows 장애 조치(failover) 클러스터 이름** 필드에 로컬 장애 조치(failover) 클러스터의 이름이 포함되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="6e150-163">Verify that **Windows failover cluster name** field contains the name of the local failover cluster.</span></span> <span data-ttu-id="6e150-164">이 필드가 비어 있으면 이 서버 인스턴스에서 현재 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]을 지원하지 않는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="6e150-164">If this field is blank, this server instance currently does not support [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)].</span></span> <span data-ttu-id="6e150-165">로컬 컴퓨터가 클러스터 노드가 아니거나 WSFC 클러스터가 종료되었거나 이 버전의 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 에서 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6e150-165">Either the local computer is not a cluster node, the WSFC cluster has been shut down, or this edition of [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] that does not support [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)].</span></span>  
  
6.  <span data-ttu-id="6e150-166">**AlwaysOn 가용성 그룹 사용** 확인란을 선택 하 고 **확인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="6e150-166">Select the **Enable AlwaysOn Availability Groups** check box, and click **OK**.</span></span>  
  
     [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="6e150-167">구성 관리자가 변경 내용을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="6e150-167">Configuration Manager saves your change.</span></span> <span data-ttu-id="6e150-168">그런 다음 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 서비스를 수동으로 다시 시작해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6e150-168">Then, you must manually restart the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] service.</span></span> <span data-ttu-id="6e150-169">이렇게 하면 비즈니스 요구 사항에 가장 적합한 다시 시작 시간을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6e150-169">This enables you to choose a restart time that is best for your business requirements.</span></span> <span data-ttu-id="6e150-170">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 서비스를 다시 시작하면 AlwaysOn을 사용할 수 있으며 `IsHadrEnabled` 서버 속성이 1로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="6e150-170">When the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] service restarts, AlwaysOn will be enabled, and the `IsHadrEnabled` server property will be set to 1.</span></span>  
  
###  <a name="using-sql-server-powershell"></a><a name="PScmd2Procedure"></a> <span data-ttu-id="6e150-171">SQL Server PowerShell 사용</span><span class="sxs-lookup"><span data-stu-id="6e150-171">Using SQL Server PowerShell</span></span>  
 <span data-ttu-id="6e150-172">**AlwaysOn을 사용하도록 설정하려면**</span><span class="sxs-lookup"><span data-stu-id="6e150-172">**To enable AlwaysOn**</span></span>  
  
1.  <span data-ttu-id="6e150-173">디렉터리를 AlwaysOn 가용성 그룹을 사용하도록 설정할 서버 인스턴스로 변경합니다(`cd`).</span><span class="sxs-lookup"><span data-stu-id="6e150-173">Change directory (`cd`) to a server instance that you want to enable for AlwaysOn Availability Groups.</span></span>  
  
2.  <span data-ttu-id="6e150-174">`Enable-SqlAlwaysOn` cmdlet을 사용하여 AlwaysOn 가용성 그룹을 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="6e150-174">Use the `Enable-SqlAlwaysOn` cmdlet to enable AlwaysOn Availability Groups.</span></span>  
  
     <span data-ttu-id="6e150-175">cmdlet의 구문을 보려면 `Get-Help` PowerShell 환경에서 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] cmdlet을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="6e150-175">To view the syntax of a cmdlet, use the `Get-Help` cmdlet in the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell environment.</span></span> <span data-ttu-id="6e150-176">자세한 내용은 [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6e150-176">For more information, see [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="6e150-177">Cmdlet에서 서비스를 다시 시작할지 여부를 제어 하는 방법에 대 한 자세한 내용은 `Enable-SqlAlwaysOn` [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 이 항목의 뒷부분에 나오는 [Cmdlet이 SQL Server 서비스를 다시 시작 하는 경우](#WhenCmdletRestartsSQL)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="6e150-177">For information about how to control whether the `Enable-SqlAlwaysOn` cmdlet restarts the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] service, see [When Does a Cmdlet Restart the SQL Server Service?](#WhenCmdletRestartsSQL), later in this topic.</span></span>  
  
 <span data-ttu-id="6e150-178">**SQL Server PowerShell 공급자를 설정하고 사용하려면**</span><span class="sxs-lookup"><span data-stu-id="6e150-178">**To set up and use the SQL Server PowerShell provider**</span></span>  
  
-   [<span data-ttu-id="6e150-179">SQL Server PowerShell 공급자</span><span class="sxs-lookup"><span data-stu-id="6e150-179">SQL Server PowerShell Provider</span></span>](../../../powershell/sql-server-powershell-provider.md)  
  
####  <a name="example-enable-sqlalwayson"></a><a name="ExmplEnable-SqlHadrServic"></a> <span data-ttu-id="6e150-180">예제: Enable-SqlAlwaysOn</span><span class="sxs-lookup"><span data-stu-id="6e150-180">Example: Enable-SqlAlwaysOn</span></span>  
 <span data-ttu-id="6e150-181">다음 PowerShell 명령을 사용하면 SQL Server 인스턴스( [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] Computer*Instance*\\ *)에서*을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6e150-181">The following PowerShell command enables [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] on an instance of SQL Server (*Computer*\\*Instance*).</span></span>  
  
```powershell
Enable-SqlAlwaysOn -Path SQLSERVER:\SQL\Computer\Instance  
```  
  
##  <a name="disable-alwayson-availability-groups"></a><a name="DisableAOAG"></a><span data-ttu-id="6e150-182">AlwaysOn 가용성 그룹 사용 안 함</span><span class="sxs-lookup"><span data-stu-id="6e150-182">Disable AlwaysOn Availability Groups</span></span>  
  
-   <span data-ttu-id="6e150-183">**AlwaysOn을 사용하지 않도록 설정하기 전에:**</span><span class="sxs-lookup"><span data-stu-id="6e150-183">**Before you disable AlwaysOn:**</span></span>  
  
     [<span data-ttu-id="6e150-184">권장 사항</span><span class="sxs-lookup"><span data-stu-id="6e150-184">Recommendations</span></span>](#Recommendations)  
  
-   <span data-ttu-id="6e150-185">**AlwaysOn을 사용하지 않도록 설정하려면:**</span><span class="sxs-lookup"><span data-stu-id="6e150-185">**To disable AlwaysOn, using:**</span></span>  
  
    -   [<span data-ttu-id="6e150-186">SQL Server 구성 관리자</span><span class="sxs-lookup"><span data-stu-id="6e150-186">SQL Server Configuration Manager</span></span>](#SQLCM3Procedure)  
  
    -   [<span data-ttu-id="6e150-187">PowerShell</span><span class="sxs-lookup"><span data-stu-id="6e150-187">PowerShell</span></span>](#PScmd3Procedure)  
  
-   <span data-ttu-id="6e150-188">**후속 작업:**  [AlwaysOn을 사용하지 않도록 설정한 후](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="6e150-188">**Follow Up:**  [After Disabling AlwaysOn](#FollowUp)</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="6e150-189">한 번에 하나의 서버에서만 AlwaysOn을 사용하지 않도록 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6e150-189">Disable AlwaysOn on only one server instance at a time.</span></span> <span data-ttu-id="6e150-190">AlwaysOn 가용성 그룹을 사용하지 않도록 설정한 후에는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 서비스가 다시 시작될 때까지 기다렸다가 다음 서버 인스턴스로 진행하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="6e150-190">After disabling AlwaysOn Availability Groups, wait until the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] service has restarted before you proceed to another server instance.</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="6e150-191">권장 사항</span><span class="sxs-lookup"><span data-stu-id="6e150-191">Recommendations</span></span>  
 <span data-ttu-id="6e150-192">서버 인스턴스에서 AlwaysOn을 해제하기 전 다음을 수행하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="6e150-192">Before you disable AlwaysOn on a server instance, we recommend that you do the following:</span></span>  
  
1.  <span data-ttu-id="6e150-193">서버 인스턴스가 사용자가 보관하려는 가용성 그룹의 주 복제본을 호스팅 중인 경우 가능한 한 가용성 그룹을 동기화된 보조 복제본으로 수동으로 장애 조치(failover)하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="6e150-193">If the server instance is currently hosting the primary replica of an availability group that you want to keep, we recommend that you manually fail over the availability group to a synchronized secondary replica, if possible.</span></span> <span data-ttu-id="6e150-194">자세한 내용은 [가용성 그룹의 계획된 수동 장애 조치(failover) 수행&#40;SQL Server&#41;](perform-a-planned-manual-failover-of-an-availability-group-sql-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6e150-194">For more information, see [Perform a Planned Manual Failover of an Availability Group &#40;SQL Server&#41;](perform-a-planned-manual-failover-of-an-availability-group-sql-server.md).</span></span>  
  
2.  <span data-ttu-id="6e150-195">모든 로컬 보조 복제본을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="6e150-195">Remove all local secondary replicas.</span></span> <span data-ttu-id="6e150-196">자세한 내용은 [가용성 그룹에서 보조 복제본 제거&#40;SQL Server&#41;](remove-a-secondary-replica-from-an-availability-group-sql-server.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6e150-196">For more information, see [Remove a Secondary Replica from an Availability Group &#40;SQL Server&#41;](remove-a-secondary-replica-from-an-availability-group-sql-server.md).</span></span>  
  
###  <a name="using-sql-server-configuration-manager"></a><a name="SQLCM3Procedure"></a> <span data-ttu-id="6e150-197">SQL Server 구성 관리자 사용</span><span class="sxs-lookup"><span data-stu-id="6e150-197">Using SQL Server Configuration Manager</span></span>  
 <span data-ttu-id="6e150-198">**AlwaysOn을 사용하지 않도록 설정하려면**</span><span class="sxs-lookup"><span data-stu-id="6e150-198">**To disable AlwaysOn**</span></span>  
  
1.  <span data-ttu-id="6e150-199">AlwaysOn 가용성 그룹을 사용하지 않도록 설정할 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인스턴스를 호스팅하는 WSFC(Windows Server 장애 조치(failover) 클러스터링) 노드에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="6e150-199">Connect to the Windows Server Failover Clustering (WSFC) node that hosts the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instance where you want to disable AlwaysOn Availability Groups.</span></span>  
  
2.  <span data-ttu-id="6e150-200">**시작** 메뉴에서 **모든 프로그램**, [!INCLUDE[ssCurrentUI](../../../includes/sscurrentui-md.md)], **구성 도구**를 차례로 가리킨 다음 **SQL Server 구성 관리자**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6e150-200">On the **Start** menu, point to **All Programs**, point to [!INCLUDE[ssCurrentUI](../../../includes/sscurrentui-md.md)], point to **Configuration Tools**, and click **SQL Server Configuration Manager**.</span></span>  
  
3.  <span data-ttu-id="6e150-201">**SQL Server 구성 관리자**에서 **SQL Server Services**를 클릭 하 고 SQL Server (\*\* < *`instance name`*>)\*\* 을 마우스 오른쪽 단추로 클릭 **<*`instance name`*>** 한 다음 **속성**을 클릭 합니다. 여기서은 AlwaysOn 가용성 그룹를 사용 하지 않도록 설정할 로컬 서버 인스턴스의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="6e150-201">In **SQL Server Configuration Manager**, click **SQL Server Services**, right-click SQL Server (**<*`instance name`*>)**, where **<*`instance name`*>** is the name of a local server instance for which you want to disable AlwaysOn Availability Groups, and click **Properties**.</span></span>  
  
4.  <span data-ttu-id="6e150-202">**AlwaysOn 고가용성**탭에서 **AlwaysOn 가용성 그룹 사용** 확인란의 선택을 취소하고 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6e150-202">On the**AlwaysOn High Availability**tab, deselect the **Enable AlwaysOn Availability Groups** check box, and click **OK**.</span></span>  
  
     [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="6e150-203">구성 관리자가 변경 내용을 저장하고 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 서비스를 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="6e150-203">Configuration Manager saves your change and restarts the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] service.</span></span> <span data-ttu-id="6e150-204">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 서비스를 시작하면 AlwaysOn을 사용할 수 없고 `IsHadrEnabled` 서버 속성이 0으로 설정되어 AlwaysOn 가용성 그룹을 사용할 수 없음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="6e150-204">When the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] service restarts, AlwaysOn will be disabled, and the `IsHadrEnabled` server property will be set to 0, to indicate that AlwaysOn Availability Groups is disabled.</span></span>  
  
5.  <span data-ttu-id="6e150-205">이 항목의 뒷부분에 나오는 [후속 작업: AlwaysOn을 사용하지 않도록 설정한 후](#FollowUp)의 정보를 읽어보는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="6e150-205">We recommend that you read the information in [Follow Up: After Disabling AlwaysOn](#FollowUp), later in this topic.</span></span>  
  
###  <a name="using-sql-server-powershell"></a><a name="PScmd3Procedure"></a> <span data-ttu-id="6e150-206">SQL Server PowerShell 사용</span><span class="sxs-lookup"><span data-stu-id="6e150-206">Using SQL Server PowerShell</span></span>  
 <span data-ttu-id="6e150-207">**AlwaysOn을 사용하지 않도록 설정하려면**</span><span class="sxs-lookup"><span data-stu-id="6e150-207">**To disable AlwaysOn**</span></span>  
  
1.  <span data-ttu-id="6e150-208">`cd`AlwaysOn 가용성 그룹에 사용 하지 않도록 설정할 현재 사용 하도록 설정 된 서버 인스턴스로 디렉터리를 변경 합니다 ().</span><span class="sxs-lookup"><span data-stu-id="6e150-208">Change directory (`cd`) to a currently-enabled server instance that you want to disenable for AlwaysOn Availability Groups.</span></span>  
  
2.  <span data-ttu-id="6e150-209">`Disable-SqlAlwaysOn` cmdlet을 사용하여 AlwaysOn 가용성 그룹을 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="6e150-209">Use the `Disable-SqlAlwaysOn` cmdlet to enable AlwaysOn Availability Groups.</span></span>  
  
     <span data-ttu-id="6e150-210">예를 들어 다음 명령은 SQL Server (*컴퓨터*인스턴스) 인스턴스에서 AlwaysOn 가용성 그룹를 사용 하지 않도록 설정 \\ *Instance*합니다.</span><span class="sxs-lookup"><span data-stu-id="6e150-210">For example, the following command disables AlwaysOn Availability Groups on an instance of SQL Server (*Computer*\\*Instance*).</span></span>  <span data-ttu-id="6e150-211">이 명령을 사용할 경우 인스턴스를 다시 시작해야 하며, 다시 시작을 확인하는 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="6e150-211">This command requires restarting the instance, and you will be prompted to confirm this restart.</span></span>  
  
    ```powershell
    Disable-SqlAlwaysOn -Path SQLSERVER:\SQL\Computer\Instance  
    ```  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="6e150-212">Cmdlet에서 서비스를 다시 시작할지 여부를 제어 하는 방법에 대 한 자세한 내용은 `Disable-SqlAlwaysOn` [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 이 항목의 뒷부분에 나오는 [Cmdlet이 SQL Server 서비스를 다시 시작 하는 경우](#WhenCmdletRestartsSQL)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="6e150-212">For information about how to control whether the `Disable-SqlAlwaysOn` cmdlet restarts the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] service, see [When Does a Cmdlet Restart the SQL Server Service?](#WhenCmdletRestartsSQL), later in this topic.</span></span>  
  
     <span data-ttu-id="6e150-213">cmdlet의 구문을 보려면 `Get-Help` PowerShell 환경에서 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] cmdlet을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="6e150-213">To view the syntax of a cmdlet, use the `Get-Help` cmdlet in the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell environment.</span></span> <span data-ttu-id="6e150-214">자세한 내용은 [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6e150-214">For more information, see [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).</span></span>  
  
 <span data-ttu-id="6e150-215">**SQL Server PowerShell 공급자를 설정하고 사용하려면**</span><span class="sxs-lookup"><span data-stu-id="6e150-215">**To set up and use the SQL Server PowerShell provider**</span></span>  
  
-   [<span data-ttu-id="6e150-216">SQL Server PowerShell 공급자</span><span class="sxs-lookup"><span data-stu-id="6e150-216">SQL Server PowerShell Provider</span></span>](../../../powershell/sql-server-powershell-provider.md)  
  
###  <a name="follow-up-after-disabling-alwayson"></a><a name="FollowUp"></a><span data-ttu-id="6e150-217">후속 작업: AlwaysOn을 사용 하지 않도록 설정한 후</span><span class="sxs-lookup"><span data-stu-id="6e150-217">Follow Up: After Disabling AlwaysOn</span></span>  
 <span data-ttu-id="6e150-218">AlwaysOn 가용성 그룹을 해제한 후 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인스턴스를 다시 시작해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6e150-218">After you disable AlwaysOn Availability Groups, the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] must be restarted.</span></span> <span data-ttu-id="6e150-219">SQL 구성 관리자는 서버 인스턴스를 자동으로 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="6e150-219">SQL Configuration Manager restarts the server instance automatically.</span></span> <span data-ttu-id="6e150-220">그러나 `Disable-SqlAlwaysOn` cmdlet을 사용한 경우 서버 인스턴스를 수동으로 다시 시작해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6e150-220">However, if you used the `Disable-SqlAlwaysOn` cmdlet, you will need to restart the server instance manually.</span></span> <span data-ttu-id="6e150-221">자세한 내용은 [sqlservr Application](../../../tools/sqlservr-application.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6e150-221">For more information, see [sqlservr Application](../../../tools/sqlservr-application.md).</span></span>  
  
 <span data-ttu-id="6e150-222">다시 시작된 서버 인스턴스에서 다음 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="6e150-222">On the restarted server instance:</span></span>  
  
-   <span data-ttu-id="6e150-223">가용성 데이터베이스는 SQL Server 시작 기능을 시작하지 않으므로 해당 시작 기능에 액세스할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6e150-223">Availability databases do not start up at SQL Server startup, making them inaccessible.</span></span>  
  
-   <span data-ttu-id="6e150-224">유일하게 지원되는 AlwaysOn [!INCLUDE[tsql](../../../includes/tsql-md.md)] 문은 [DROP AVAILABILITY GROUP](/sql/t-sql/statements/drop-availability-group-transact-sql)입니다.</span><span class="sxs-lookup"><span data-stu-id="6e150-224">The only supported AlwaysOn [!INCLUDE[tsql](../../../includes/tsql-md.md)] statement is [DROP AVAILABILITY GROUP](/sql/t-sql/statements/drop-availability-group-transact-sql).</span></span> <span data-ttu-id="6e150-225">ALTER DATABASE의 CREATE AVAILABILITY GROUP, ALTER AVAILABILITY GROUP 및 SET HADR 옵션은 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6e150-225">CREATE AVAILABILITY GROUP, ALTER AVAILABILITY GROUP, and the SET HADR options of ALTER DATABASE are not supported.</span></span>  
  
-   <span data-ttu-id="6e150-226">AlwaysOn 가용성 그룹을 사용하지 않도록 설정해도 WSFC의 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 구성과 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 메타데이터는 영향을 받지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6e150-226">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] metadata and [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] configuration data in WSFC are unaffected by disabling AlwaysOn Availability Groups.</span></span>  
  
 <span data-ttu-id="6e150-227">하나 이상의 가용성 그룹에 대한 가용성 복제본을 호스팅하는 모든 서버 인스턴스에서 AlwaysOn 가용성 그룹을 영구적으로 해제한 경우 다음 단계를 완료하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="6e150-227">If you permanently disable AlwaysOn Availability Groups on every server instance that hosts an availability replica for one or more availability groups, we recommend that you complete the following steps:</span></span>  
  
1.  <span data-ttu-id="6e150-228">AlwaysOn을 해제하기 전에 로컬 가용성 복제본을 제거하지 않은 경우 서버 인스턴스가 가용성 복제본을 호스팅 중인 각 가용성 그룹을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="6e150-228">If you did not remove the local availability replicas before disabling AlwaysOn, delete (drop) each availability group for which the server instance is hosting an availability replica.</span></span> <span data-ttu-id="6e150-229">가용성 그룹 삭제에 대한 자세한 내용은 [가용성 그룹 제거&#40;SQL Server&#41;](remove-an-availability-group-sql-server.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6e150-229">For information about deleting an availability group, see [Remove an Availability Group &#40;SQL Server&#41;](remove-an-availability-group-sql-server.md).</span></span>  
  
2.  <span data-ttu-id="6e150-230">뒤에 남은 메타데이터를 제거하려면 원본 WSFC 클러스터의 일부인 서버 인스턴스에서 각각의 해당 가용성 그룹을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="6e150-230">To remove the metadata left behind, delete (drop) each affected availability group on a server instance that is part of the original WSFC cluster.</span></span>  
  
3.  <span data-ttu-id="6e150-231">모든 주 데이터베이스가 계속해서 모든 연결에 액세스 가능하지만 주 데이터베이스와 보조 데이터베이스 간 데이터 동기화는 중지됩니다.</span><span class="sxs-lookup"><span data-stu-id="6e150-231">Any primary databases continue to be accessible to all connections but the data synchronization between the primary and secondary databases stops.</span></span>  
  
4.  <span data-ttu-id="6e150-232">보조 데이터베이스가 RESTORING 상태가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6e150-232">The secondary databases enter the RESTORING state.</span></span> <span data-ttu-id="6e150-233">이를 삭제하거나 RESTORE WITH RECOVERY를 사용하여 복원할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6e150-233">You can delete them, or you can restore them by using RESTORE WITH RECOVERY.</span></span> <span data-ttu-id="6e150-234">그러나 복원된 데이터베이스는 더 이상 가용성 그룹 데이터 동기화에 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6e150-234">However, restored databases are no longer participating in availability-group data synchronization.</span></span>  
  
##  <a name="when-does-a-cmdlet-restart-the-sql-server-service"></a><a name="WhenCmdletRestartsSQL"></a> <span data-ttu-id="6e150-235">Cmdlet이 SQL Server 서비스를 다시 시작하는 경우</span><span class="sxs-lookup"><span data-stu-id="6e150-235">When Does a Cmdlet Restart the SQL Server Service?</span></span>  
 <span data-ttu-id="6e150-236">현재 실행 중인 서버 인스턴스에서 `Enable-SqlAlwaysOn` 또는 `Disable-SqlAlwaysOn`을 사용하여 현재 AlwaysOn 설정을 변경하면 SQL Server 서비스가 다시 시작될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6e150-236">On a server instance that is currently running, using `Enable-SqlAlwaysOn` or `Disable-SqlAlwaysOn` to change the current AlwaysOn setting could cause the SQL Server service to restart.</span></span> <span data-ttu-id="6e150-237">다시 시작 동작은 다음 조건에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="6e150-237">The restart behavior on depends on the following conditions:</span></span>  
  
|<span data-ttu-id="6e150-238">-NoServiceRestart 매개 변수가 지정되었는지 여부</span><span class="sxs-lookup"><span data-stu-id="6e150-238">-NoServiceRestart parameter specified</span></span>|<span data-ttu-id="6e150-239">-Force 매개 변수가 지정되었는지 여부</span><span class="sxs-lookup"><span data-stu-id="6e150-239">-Force parameter specified</span></span>|<span data-ttu-id="6e150-240">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 서비스가 다시 시작되었는지 여부</span><span class="sxs-lookup"><span data-stu-id="6e150-240">Is the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] service restarted?</span></span>|  
|--------------------------------------------|---------------------------------|---------------------------------------------------------|  
|<span data-ttu-id="6e150-241">예</span><span class="sxs-lookup"><span data-stu-id="6e150-241">No</span></span>|<span data-ttu-id="6e150-242">예</span><span class="sxs-lookup"><span data-stu-id="6e150-242">No</span></span>|<span data-ttu-id="6e150-243">기본적으로 선택되어 있지만</span><span class="sxs-lookup"><span data-stu-id="6e150-243">By default.</span></span> <span data-ttu-id="6e150-244">cmdlet에서 다음과 같이 묻는 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="6e150-244">But the cmdlet prompts you as follows:</span></span><br /><br /> <span data-ttu-id="6e150-245">**이 작업을 완료하려면 '<instance_name>' 서버 인스턴스에 대한 SQL Server 서비스를 다시 시작해야 합니다. 계속하시겠습니까?**</span><span class="sxs-lookup"><span data-stu-id="6e150-245">**To complete this action, we must restart the SQL Server service for server instance '<instance_name>'. Do you want to continue?**</span></span><br /><br /> <span data-ttu-id="6e150-246">**[Y] 예  [N] 아니요  [S] 일시 중단  [?] 도움말(기본값 "Y"):**</span><span class="sxs-lookup"><span data-stu-id="6e150-246">**[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"):**</span></span><br /><br /> <span data-ttu-id="6e150-247">**N** 또는 **S**를 지정하면 서비스가 다시 시작되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6e150-247">If you specify **N** or **S**, the service is not restarted.</span></span>|  
|<span data-ttu-id="6e150-248">예</span><span class="sxs-lookup"><span data-stu-id="6e150-248">No</span></span>|<span data-ttu-id="6e150-249">예</span><span class="sxs-lookup"><span data-stu-id="6e150-249">Yes</span></span>|<span data-ttu-id="6e150-250">서비스가 다시 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="6e150-250">Service is restarted.</span></span>|  
|<span data-ttu-id="6e150-251">예</span><span class="sxs-lookup"><span data-stu-id="6e150-251">Yes</span></span>|<span data-ttu-id="6e150-252">예</span><span class="sxs-lookup"><span data-stu-id="6e150-252">No</span></span>|<span data-ttu-id="6e150-253">서비스가 다시 시작되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6e150-253">Service is not restarted.</span></span>|  
|<span data-ttu-id="6e150-254">예</span><span class="sxs-lookup"><span data-stu-id="6e150-254">Yes</span></span>|<span data-ttu-id="6e150-255">예</span><span class="sxs-lookup"><span data-stu-id="6e150-255">Yes</span></span>|<span data-ttu-id="6e150-256">서비스가 다시 시작되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6e150-256">Service is not restarted.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6e150-257">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6e150-257">See Also</span></span>  
 <span data-ttu-id="6e150-258">[AlwaysOn 가용성 그룹 &#40;SQL Server 개요&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="6e150-258">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 [<span data-ttu-id="6e150-259">SERVERPROPERTY&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="6e150-259">SERVERPROPERTY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/serverproperty-transact-sql)  
