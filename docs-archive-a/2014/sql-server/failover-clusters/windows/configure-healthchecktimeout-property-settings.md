---
title: HealthCheckTimeout 속성 설정 구성 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
ms.assetid: 3bbeb979-e6fc-4184-ad6e-cca62108de74
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: a38cd6e9e4718a2f1c136e5412cde340e92f14c1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650567"
---
# <a name="configure-healthchecktimeout-property-settings"></a><span data-ttu-id="3c6cc-102">HealthCheckTimeout 속성 설정 구성</span><span class="sxs-lookup"><span data-stu-id="3c6cc-102">Configure HealthCheckTimeout Property Settings</span></span>
  <span data-ttu-id="3c6cc-103">HealthCheckTimeout 설정은 SQL Server 리소스 DLL이 AlwaysOn FCI (장애 조치 (Failover) 클러스터 인스턴스)를 응답 하지 않는 것으로 보고 하기 전에 [sp_server_diagnostics](/sql/relational-databases/system-stored-procedures/sp-server-diagnostics-transact-sql) 저장 프로시저에서 반환 되는 정보를 대기 해야 하는 시간 (밀리초)을 지정 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3c6cc-103">The HealthCheckTimeout setting is used to specify the length of time, in milliseconds, that the SQL Server resource DLL should wait for information returned by the [sp_server_diagnostics](/sql/relational-databases/system-stored-procedures/sp-server-diagnostics-transact-sql) stored procedure before reporting the AlwaysOn Failover Cluster Instance (FCI) as unresponsive.</span></span> <span data-ttu-id="3c6cc-104">제한 시간 설정에 대한 변경 내용은 즉시 적용되며 SQL Server 리소스를 다시 시작하지 않아도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3c6cc-104">Changes that are made to the timeout settings are effective immediately and do not require a restart of the SQL Server resource.</span></span>  
  
-   <span data-ttu-id="3c6cc-105">**시작하기 전 주의 사항:**  [제한 사항](#Limits), [보안](#Security)</span><span class="sxs-lookup"><span data-stu-id="3c6cc-105">**Before you begin:**  [Limitations and Restrictions](#Limits), [Security](#Security)</span></span>  
  
-   <span data-ttu-id="3c6cc-106">**HeathCheckTimeout 설정을 구성하려면:**  [PowerShell](#PowerShellProcedure), [장애 조치(failover) 클러스터 관리자](#WSFC), [Transact-SQL](#TsqlProcedure)</span><span class="sxs-lookup"><span data-stu-id="3c6cc-106">**To Configure the HeathCheckTimeout setting, using:**  [PowerShell](#PowerShellProcedure), [Failover Cluster Manager](#WSFC), [Transact-SQL](#TsqlProcedure)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="3c6cc-107">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="3c6cc-107">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Limits"></a> <span data-ttu-id="3c6cc-108">제한 사항</span><span class="sxs-lookup"><span data-stu-id="3c6cc-108">Limitations and Restrictions</span></span>  
 <span data-ttu-id="3c6cc-109">이 속성의 기본값은 60,000밀리초(60초)이고,</span><span class="sxs-lookup"><span data-stu-id="3c6cc-109">The default value for this property is 60,000 milliseconds (60 seconds).</span></span> <span data-ttu-id="3c6cc-110">최소값은 15,000밀리초(15초)입니다.</span><span class="sxs-lookup"><span data-stu-id="3c6cc-110">The minimum value is 15,000 milliseconds (15 seconds).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="3c6cc-111">보안</span><span class="sxs-lookup"><span data-stu-id="3c6cc-111">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="3c6cc-112">권한</span><span class="sxs-lookup"><span data-stu-id="3c6cc-112">Permissions</span></span>  
 <span data-ttu-id="3c6cc-113">ALTER SETTINGS 및 VIEW SERVER STATE 사용 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="3c6cc-113">Requires ALTER SETTINGS and VIEW SERVER STATE permissions.</span></span>  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a> <span data-ttu-id="3c6cc-114">PowerShell 사용</span><span class="sxs-lookup"><span data-stu-id="3c6cc-114">Using PowerShell</span></span>  
  
### <a name="to-configure-healthchecktimeout-settings"></a><span data-ttu-id="3c6cc-115">HealthCheckTimeout 설정을 구성하려면</span><span class="sxs-lookup"><span data-stu-id="3c6cc-115">To configure HealthCheckTimeout settings</span></span>  
  
1.  <span data-ttu-id="3c6cc-116">**관리자 권한으로 실행**을 통해 승격된 Windows PowerShell을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="3c6cc-116">Start an elevated Windows PowerShell via **Run as Administrator**.</span></span>  
  
2.  <span data-ttu-id="3c6cc-117">클러스터 Cmdlet을 사용할 수 있도록 `FailoverClusters` 모듈을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="3c6cc-117">Import the `FailoverClusters` module to enable cluster cmdlets.</span></span>  
  
3.  <span data-ttu-id="3c6cc-118">Cmdlet을 사용 `Get-ClusterResource` 하 여 리소스를 찾은 다음 cmdlet을 사용 하 여 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] `Set-ClusterParameter` 장애 조치 (failover) 클러스터 인스턴스에 대 한 **HealthCheckTimeout** 속성을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3c6cc-118">Use the `Get-ClusterResource` cmdlet to find the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] resource, then use `Set-ClusterParameter` cmdlet to set the **HealthCheckTimeout** property for the failover cluster instance.</span></span>  
  
> [!TIP]  
>  <span data-ttu-id="3c6cc-119">새 PowerShell 창을 열 때마다 `FailoverClusters` 모듈을 가져와야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3c6cc-119">Every time you open a new PowerShell window, you need to import the `FailoverClusters` module.</span></span>  

 <span data-ttu-id="3c6cc-120">다음 예에서는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 리소스 "`SQL Server (INST1)`"의 HealthCheckTimeout 설정을 60000밀리초로 번경합니다.</span><span class="sxs-lookup"><span data-stu-id="3c6cc-120">The following example changes the HealthCheckTimeout setting on the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] resource "`SQL Server (INST1)`" to 60000 milliseconds.</span></span>  
  
```powershell  
Import-Module FailoverClusters  
  
$fci = "SQL Server (INST1)"  
Get-ClusterResource $fci | Set-ClusterParameter HealthCheckTimeout 60000  
```  
  
### <a name="related-content-powershell"></a><span data-ttu-id="3c6cc-121">관련 내용(PowerShell)</span><span class="sxs-lookup"><span data-stu-id="3c6cc-121">Related Content (PowerShell)</span></span>  
  
-   <span data-ttu-id="3c6cc-122">[클러스터링 및 고가용성](https://techcommunity.microsoft.com/t5/failover-clustering/bg-p/FailoverClustering) (장애 조치(failover) 클러스터링 및 네트워크 부하 분산 팀 블로그)</span><span class="sxs-lookup"><span data-stu-id="3c6cc-122">[Clustering and High-Availability](https://techcommunity.microsoft.com/t5/failover-clustering/bg-p/FailoverClustering) (Failover Clustering and Network Load Balancing Team Blog)</span></span>  
  
-   <span data-ttu-id="3c6cc-123">[장애 조치(Failover) 클러스터에서 Windows PowerShell 시작](https://technet.microsoft.com/library/ee619762\(WS.10\).aspx)</span><span class="sxs-lookup"><span data-stu-id="3c6cc-123">[Getting Started with Windows PowerShell on a Failover Cluster](https://technet.microsoft.com/library/ee619762\(WS.10\).aspx)</span></span>  
  
-   [<span data-ttu-id="3c6cc-124">클러스터 리소스 명령 및 해당 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="3c6cc-124">Cluster resource commands and equivalent Windows PowerShell cmdlets</span></span>](https://msdn.microsoft.com/library/ee619744.aspx#BKMK_resource)  
  
##  <a name="using-the-failover-cluster-manager-snap-in"></a><a name="WSFC"></a> <span data-ttu-id="3c6cc-125">장애 조치(Failover) 클러스터 관리자 스냅인 사용</span><span class="sxs-lookup"><span data-stu-id="3c6cc-125">Using the Failover Cluster Manager Snap-in</span></span>  
 <span data-ttu-id="3c6cc-126">**HealthCheckTimeout 설정을 구성하려면**</span><span class="sxs-lookup"><span data-stu-id="3c6cc-126">**To configure HealthCheckTimeout setting**</span></span>  
  
1.  <span data-ttu-id="3c6cc-127">장애 조치(failover) 클러스터 관리자 스냅인을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="3c6cc-127">Open the Failover Cluster Manager snap-in.</span></span>  
  
2.  <span data-ttu-id="3c6cc-128">**서비스 및 애플리케이션** 을 확장하고 FCI를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3c6cc-128">Expand **Services and Applications** and select the FCI.</span></span>  
  
3.  <span data-ttu-id="3c6cc-129">**기타 리소스** 에서 **SQL Server 리소스** 를 마우스 오른쪽 단추로 클릭한 다음 오른쪽 클릭 메뉴에서 **속성** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3c6cc-129">Right-click the **SQL Server resource** under **Other Resources** and select **Properties** from the right-click menu.</span></span> <span data-ttu-id="3c6cc-130">SQL Server 리소스 **속성** 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="3c6cc-130">The SQL Server resource **Properties** dialog box opens.</span></span>  
  
4.  <span data-ttu-id="3c6cc-131">**속성** 탭을 선택하고 **HealthCheckTimeout** 속성에 대해 원하는 값을 입력한 다음 **확인** 을 클릭하여 변경 내용을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="3c6cc-131">Select the **Properties** tab, enter the desired value for the **HealthCheckTimeout** property, and then click **OK** to apply the change.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="3c6cc-132">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="3c6cc-132">Using Transact-SQL</span></span>  
 <span data-ttu-id="3c6cc-133">[ALTER SERVER CONFIGURATION](/sql/t-sql/statements/alter-server-configuration-transact-sql) 문을 사용 하 여 [!INCLUDE[tsql](../../../includes/tsql-md.md)] HealthCheckTimeOut 속성 값을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3c6cc-133">Using the [ALTER SERVER CONFIGURATION](/sql/t-sql/statements/alter-server-configuration-transact-sql)[!INCLUDE[tsql](../../../includes/tsql-md.md)] statement, you can specify the HealthCheckTimeOut property value.</span></span>  
  
###  <a name="example-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="3c6cc-134">예(Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="3c6cc-134">Example (Transact-SQL)</span></span>  
 <span data-ttu-id="3c6cc-135">다음 예에서는 HealthCheckTimeout 옵션을 15,000밀리초(15초)로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="3c6cc-135">The following example sets the HealthCheckTimeout option to 15,000 milliseconds (15 seconds).</span></span>  
  
```sql
ALTER SERVER CONFIGURATION   
SET FAILOVER CLUSTER PROPERTY HealthCheckTimeout = 15000;  
```  
  
## <a name="see-also"></a><span data-ttu-id="3c6cc-136">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3c6cc-136">See Also</span></span>  
 [<span data-ttu-id="3c6cc-137">Failover Policy for Failover Cluster Instances</span><span class="sxs-lookup"><span data-stu-id="3c6cc-137">Failover Policy for Failover Cluster Instances</span></span>](failover-policy-for-failover-cluster-instances.md)  
