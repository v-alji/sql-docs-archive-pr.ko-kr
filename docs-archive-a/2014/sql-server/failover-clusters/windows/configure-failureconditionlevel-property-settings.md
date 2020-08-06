---
title: FailureConditionLevel 속성 설정 구성 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
ms.assetid: 513dd179-9a46-46da-9fdd-7632cf6d0816
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 8924b864d7cc8be078b370e3182713114f54ff6c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650569"
---
# <a name="configure-failureconditionlevel-property-settings"></a><span data-ttu-id="31618-102">FailureConditionLevel 속성 설정 구성</span><span class="sxs-lookup"><span data-stu-id="31618-102">Configure FailureConditionLevel Property Settings</span></span>
  <span data-ttu-id="31618-103">FailureConditionLevel 속성을 사용하여 AlwaysOn FCI(장애 조치(Failover) 클러스터 인스턴스)가 장애 조치(Failover)되거나 다시 시작되는 조건을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="31618-103">Use the FailureConditionLevel property to set the conditions for the AlwaysOn Failover Cluster Instance (FCI) to fail over or restart.</span></span> <span data-ttu-id="31618-104">이 속성에 대한 변경 내용은 WSFC(Windows Server 장애 조치(Failover) 클러스터) 서비스 또는 FCI 리소스를 다시 시작할 필요 없이 즉시 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="31618-104">Changes to this property are applied immediately without requiring a restart of the Windows Server Failover Cluster (WSFC) service or the FCI resource.</span></span>  
  
-   <span data-ttu-id="31618-105">**시작하기 전 주의 사항:**  [FailureConditionLevel 속성 설정](#Restrictions), [보안](#Security)</span><span class="sxs-lookup"><span data-stu-id="31618-105">**Before you begin:**  [FailureConditionLevel Property Settings](#Restrictions), [Security](#Security)</span></span>  
  
-   <span data-ttu-id="31618-106">**FailureConditionLevel 속성 설정에 사용되는 도구:** [PowerShell](#PowerShellProcedure), [장애 조치(Failover) 클러스터 관리자](#WSFC), [Transact-SQL](#TsqlProcedure)</span><span class="sxs-lookup"><span data-stu-id="31618-106">**To configure the FailureConditionLevel property settings using,** [PowerShell](#PowerShellProcedure), [Failover Cluster Manager](#WSFC), [Transact-SQL](#TsqlProcedure)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="31618-107">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="31618-107">Before You Begin</span></span>  
  
###  <a name="failureconditionlevel-property-settings"></a><a name="Restrictions"></a> <span data-ttu-id="31618-108">FailureConditionLevel 속성 설정</span><span class="sxs-lookup"><span data-stu-id="31618-108">FailureConditionLevel Property Settings</span></span>  
 <span data-ttu-id="31618-109">실패 조건은 증가하는 범위로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="31618-109">The failure conditions are set on an increasing scale.</span></span> <span data-ttu-id="31618-110">수준 1-5의 경우 각 수준에는 자체 조건과 함께 이전 수준의 모든 조건이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="31618-110">For levels 1-5, each level includes all the conditions from the previous levels in addition to its own conditions.</span></span> <span data-ttu-id="31618-111">이는 수준이 높을수록 장애 조치(Failover) 또는 다시 시작 확률이 증가함을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="31618-111">This means that with each level, there is an increased probability of a failover or restart.</span></span>  <span data-ttu-id="31618-112">자세한 내용은 [Failover Policy for Failover Cluster Instances](failover-policy-for-failover-cluster-instances.md) 항목의 "실패 확정" 섹션을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="31618-112">For more information, see the "Determining Failures" section of the [Failover Policy for Failover Cluster Instances](failover-policy-for-failover-cluster-instances.md) topic.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="31618-113">보안</span><span class="sxs-lookup"><span data-stu-id="31618-113">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="31618-114">권한</span><span class="sxs-lookup"><span data-stu-id="31618-114">Permissions</span></span>  
 <span data-ttu-id="31618-115">ALTER SETTINGS 및 VIEW SERVER STATE 사용 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="31618-115">Requires ALTER SETTINGS and VIEW SERVER STATE permissions.</span></span>  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a> <span data-ttu-id="31618-116">PowerShell 사용</span><span class="sxs-lookup"><span data-stu-id="31618-116">Using PowerShell</span></span>  
  
### <a name="to-configure-failureconditionlevel-settings"></a><span data-ttu-id="31618-117">FailureConditionLevel 설정을 구성하려면</span><span class="sxs-lookup"><span data-stu-id="31618-117">To configure FailureConditionLevel settings</span></span>  
  
1.  <span data-ttu-id="31618-118">**관리자 권한으로 실행**을 통해 승격된 Windows PowerShell을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="31618-118">Start an elevated Windows PowerShell via **Run as Administrator**.</span></span>  
  
2.  <span data-ttu-id="31618-119">클러스터 Cmdlet을 사용할 수 있도록 `FailoverClusters` 모듈을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="31618-119">Import the `FailoverClusters` module to enable cluster cmdlets.</span></span>  
  
3.  <span data-ttu-id="31618-120">Cmdlet을 사용 `Get-ClusterResource` 하 여 리소스를 찾은 다음 cmdlet을 사용 하 여 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] `Set-ClusterParameter` 장애 조치 (Failover) 클러스터 인스턴스에 대 한 **FailureConditionLevel** 속성을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="31618-120">Use the `Get-ClusterResource` cmdlet to find the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] resource, then use `Set-ClusterParameter` cmdlet to set the **FailureConditionLevel** property for a Failover Cluster Instance.</span></span>  
  
> [!TIP]  
>  <span data-ttu-id="31618-121">새 PowerShell 창을 열 때마다 `FailoverClusters` 모듈을 가져와야 합니다.</span><span class="sxs-lookup"><span data-stu-id="31618-121">Every time you open a new PowerShell window, you need to import the `FailoverClusters` module.</span></span>  

 <span data-ttu-id="31618-122">다음 예에서는 심각한 서버 오류 시 장애 조치(failover) 또는 다시 시작이 수행되도록 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 리소스 "`SQL Server (INST1)`"의 FailureConditionLevel 설정을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="31618-122">The following example changes the FailureConditionLevel setting on the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] resource "`SQL Server (INST1)`" to fail over or restart on critical server errors.</span></span>  
  
```powershell  
Import-Module FailoverClusters  
  
$fci = "SQL Server (INST1)"  
Get-ClusterResource $fci | Set-ClusterParameter FailureConditionLevel 3
```  
  
### <a name="related-content-powershell"></a><span data-ttu-id="31618-123">관련 내용(PowerShell)</span><span class="sxs-lookup"><span data-stu-id="31618-123">Related Content (PowerShell)</span></span>  
  
-   <span data-ttu-id="31618-124">[클러스터링 및 고가용성](https://techcommunity.microsoft.com/t5/failover-clustering/bg-p/FailoverClustering) (장애 조치(failover) 클러스터링 및 네트워크 부하 분산 팀 블로그)</span><span class="sxs-lookup"><span data-stu-id="31618-124">[Clustering and High-Availability](https://techcommunity.microsoft.com/t5/failover-clustering/bg-p/FailoverClustering) (Failover Clustering and Network Load Balancing Team Blog)</span></span>  
  
-   <span data-ttu-id="31618-125">[장애 조치(Failover) 클러스터에서 Windows PowerShell 시작](https://technet.microsoft.com/library/ee619762\(WS.10\).aspx)</span><span class="sxs-lookup"><span data-stu-id="31618-125">[Getting Started with Windows PowerShell on a Failover Cluster](https://technet.microsoft.com/library/ee619762\(WS.10\).aspx)</span></span>  
  
-   [<span data-ttu-id="31618-126">클러스터 리소스 명령 및 해당 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="31618-126">Cluster resource commands and equivalent Windows PowerShell cmdlets</span></span>](https://msdn.microsoft.com/library/ee619744.aspx#BKMK_resource)  
  
##  <a name="using-the-failover-cluster-manager-snap-in"></a><a name="WSFC"></a> <span data-ttu-id="31618-127">장애 조치(Failover) 클러스터 관리자 스냅인 사용</span><span class="sxs-lookup"><span data-stu-id="31618-127">Using the Failover Cluster Manager Snap-in</span></span>  

### <a name="to-configure-failureconditionlevel-property-settings"></a><span data-ttu-id="31618-128">FailureConditionLevel 속성 설정을 구성 하려면</span><span class="sxs-lookup"><span data-stu-id="31618-128">To configure FailureConditionLevel property settings</span></span>
  
1.  <span data-ttu-id="31618-129">장애 조치(failover) 클러스터 관리자 스냅인을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="31618-129">Open the Failover Cluster Manager snap-in.</span></span>  
  
2.  <span data-ttu-id="31618-130">**서비스 및 애플리케이션** 을 확장하고 FCI를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="31618-130">Expand the **Services and Applications** and select the FCI.</span></span>  
  
3.  <span data-ttu-id="31618-131">**기타 리소스** 에서 **SQL Server 리소스**를 마우스 오른쪽 단추로 클릭한 다음 메뉴에서 **속성** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="31618-131">Right-click the **SQL Server resource** under **Other Resources**, and then select **Properties** from the menu.</span></span> <span data-ttu-id="31618-132">SQL Server 리소스 **속성** 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="31618-132">The SQL Server resource **Properties** dialog box opens.</span></span>  
  
4.  <span data-ttu-id="31618-133">**속성** 탭을 선택하고 **FaliureConditionLevel** 속성에 대해 원하는 값을 입력한 다음 **확인** 을 클릭하여 변경 내용을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="31618-133">Select the **Properties** tab, enter the desired value for the **FaliureConditionLevel** property, and then click **OK** to apply the change.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="31618-134">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="31618-134">Using Transact-SQL</span></span>  

### <a name="to-configure-failureconditionlevel-property-settings"></a><span data-ttu-id="31618-135">FailureConditionLevel 속성 설정을 구성 하려면</span><span class="sxs-lookup"><span data-stu-id="31618-135">To configure FailureConditionLevel property settings</span></span>
  
 <span data-ttu-id="31618-136">[ALTER SERVER CONFIGURATION](/sql/t-sql/statements/alter-server-configuration-transact-sql)[!INCLUDE[tsql](../../../includes/tsql-md.md)] 문을 사용하여 FailureConditionLevel 속성 값을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="31618-136">Using the [ALTER SERVER CONFIGURATION](/sql/t-sql/statements/alter-server-configuration-transact-sql)[!INCLUDE[tsql](../../../includes/tsql-md.md)] statement, you can specify the FailureConditionLevel property value.</span></span>  
  
###  <a name="example-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="31618-137">예(Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="31618-137">Example (Transact-SQL)</span></span>  
 <span data-ttu-id="31618-138">다음 예에서는 FailureConditionLevel 속성을 0으로 설정하여 어떤 실패 조건에서도 장애 조치(failover) 또는 다시 시작이 자동으로 트리거되지 않음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="31618-138">The following example sets the FailureConditionLevel property to 0, indicating that failover or restart will not be triggered automatically on any failure conditions.</span></span>  
  
```sql
ALTER SERVER CONFIGURATION SET FAILOVER CLUSTER PROPERTY FailureConditionLevel = 0;  
```  
  
## <a name="see-also"></a><span data-ttu-id="31618-139">참고 항목</span><span class="sxs-lookup"><span data-stu-id="31618-139">See Also</span></span>  
 <span data-ttu-id="31618-140">[sp_server_diagnostics&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-server-diagnostics-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="31618-140">[sp_server_diagnostics &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-server-diagnostics-transact-sql) </span></span>  
 [<span data-ttu-id="31618-141">Failover Policy for Failover Cluster Instances</span><span class="sxs-lookup"><span data-stu-id="31618-141">Failover Policy for Failover Cluster Instances</span></span>](failover-policy-for-failover-cluster-instances.md)  
