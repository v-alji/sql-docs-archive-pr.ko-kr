---
title: SQL Server 유틸리티 문제 해결 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
ms.assetid: f5f47c2a-38ea-40f8-9767-9bc138d14453
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 3c139f9f084374aeb711e905ac0c315acc25c6ac
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87735535"
---
# <a name="troubleshoot-the-sql-server-utility"></a><span data-ttu-id="83700-102">SQL Server 유틸리티 문제 해결</span><span class="sxs-lookup"><span data-stu-id="83700-102">Troubleshoot the SQL Server Utility</span></span>
  <span data-ttu-id="83700-103">ph x="1" /&gt; 유틸리티 문제 해결에는 SQL Server 인스턴스를 UCP에 등록하는 작업의 실패 해결, UCP에서 관리되는 인스턴스 목록 뷰에 회색 아이콘으로 표시되는 실패한 데이터 수집 문제 해결, 성능 병목 현상 완화, 리소스 상태 문제 해결 등이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="83700-103">Troubleshooting [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Utility issues might include resolving a failed operation to enroll an instance of SQL Server with a UCP, troubleshooting failed data collection resulting in gray icons in the managed instance list view on a UCP, mitigating performance bottlenecks, or resolving resource health issues.</span></span> <span data-ttu-id="83700-104">UCP에서 식별 하는 리소스 상태 문제를 완화 하는 방법에 대 한 자세한 내용은 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [SQL Server 문제 해결 Resource Health &#40;SQL Server 유틸리티&#41;](../relational-databases/manage/troubleshoot-sql-server-resource-health-sql-server-utility.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="83700-104">For more information about mitigating resource health issues identified by a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] UCP, see [Troubleshoot SQL Server Resource Health &#40;SQL Server Utility&#41;](../relational-databases/manage/troubleshoot-sql-server-resource-health-sql-server-utility.md).</span></span>  
  
## <a name="failed-operation-to-enroll-an-instance-of-sql-server-into-a-sql-server-utility"></a><span data-ttu-id="83700-105">SQL Server 유틸리티에 SQL Server 인스턴스를 등록하는 작업 실패</span><span class="sxs-lookup"><span data-stu-id="83700-105">Failed Operation to Enroll an Instance of SQL Server into a SQL Server Utility</span></span>  
 <span data-ttu-id="83700-106">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 인증을 사용하여 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 인스턴스에 연결하여 등록할 경우 UCP가 위치한 도메인이 아닌 다른 Active Directory 도메인에 속하는 프록시 계정을 지정하면 인스턴스 유효성 검사는 성공하지만 다음 오류 메시지와 함께 등록 작업이 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="83700-106">If you connect to the instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] to enroll using [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication, and you specify a proxy account that belongs to a different Active Directory domain than the domain where the UCP is located, instance validation succeeds, but the enrollment operation fails with the following error message:</span></span>  
  
 <span data-ttu-id="83700-107">Transact-SQL 문 또는 일괄 처리를 실행하는 동안 예외가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="83700-107">An exception occurred while executing a Transact-SQL statement or batch.</span></span> <span data-ttu-id="83700-108">(Microsoft.SqlServer.ConnectionInfo)</span><span class="sxs-lookup"><span data-stu-id="83700-108">(Microsoft.SqlServer.ConnectionInfo)</span></span>  
  
 <span data-ttu-id="83700-109">추가 정보:  Windows NT 그룹/사용자 '\<DomainName\AccountName>'에 대한 정보를 가져올 수 없습니다. 오류 코드 0x5.</span><span class="sxs-lookup"><span data-stu-id="83700-109">Additional information:  Could not obtain information about Windows NT group/user '\<DomainName\AccountName>', error code 0x5.</span></span> <span data-ttu-id="83700-110">(Microsoft SQL Server, 오류: 15404)</span><span class="sxs-lookup"><span data-stu-id="83700-110">(Microsoft SQL Server, Error: 15404)</span></span>  
  
 <span data-ttu-id="83700-111">이 문제는 다음과 같은 예제 시나리오에서 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="83700-111">This issue occurs in the following example scenario:</span></span>  
  
1.  <span data-ttu-id="83700-112">UCP가 "Domain_1"의 멤버입니다.</span><span class="sxs-lookup"><span data-stu-id="83700-112">The UCP is a member of "Domain_1."</span></span>  
  
2.  <span data-ttu-id="83700-113">단방향 도메인 트러스트 관계가 설정되어 있습니다. 즉, "Domain_2"는 "Domain_1"을 트러스트하지 않지만 "Domain_1"은 "Domain_2"를 트러스트합니다.</span><span class="sxs-lookup"><span data-stu-id="83700-113">A one-way domain trust relationship is in place: that is, "Domain_1" is not trusted by "Domain_2" but "Domain_2" is trusted by "Domain_1."</span></span>  
  
3.  <span data-ttu-id="83700-114">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 유틸리티에 등록할 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 인스턴스도 "Domain_1"의 멤버입니다.</span><span class="sxs-lookup"><span data-stu-id="83700-114">The instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] to enroll into the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Utility is also a member of "Domain_1."</span></span>  
  
4.  <span data-ttu-id="83700-115">등록 작업 중 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] "sa"를 사용 하 여 등록 하려면 인스턴스에 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="83700-115">During the enroll operation, connect to the instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] to enroll using "sa".</span></span> <span data-ttu-id="83700-116">"Domain_2"의 프록시 계정을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="83700-116">Specify a proxy account from "Domain_2."</span></span>  
  
5.  <span data-ttu-id="83700-117">유효성 검사는 성공하지만 등록이 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="83700-117">Validation succeeds but enrollment fails.</span></span>  
  
 <span data-ttu-id="83700-118">위의 예제를 사용 하 여이 문제에 대 한 해결 방법은 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] "sa"를 사용 하 고 "Domain_1"의 프록시 계정을 제공 하 여 인스턴스에 연결 하 여 유틸리티에 등록 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="83700-118">The workaround for this issue, using the example above, is to connect to the instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] to enroll into the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Utility using "sa" and provide a proxy account from "Domain_1."</span></span>  
  
## <a name="failed-wmi-validation"></a><span data-ttu-id="83700-119">WMI 유효성 검사 실패</span><span class="sxs-lookup"><span data-stu-id="83700-119">Failed WMI Validation</span></span>  
 <span data-ttu-id="83700-120">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]인스턴스에서 WMI가 올바르게 구성되지 않을 경우 UCP 만들기 및 관리되는 인스턴스 등록 작업 시 경고가 표시되지만 작업이 중지되지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="83700-120">If WMI is not properly configured on an instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], the Create UCP and Enroll Managed Instance operations display a warning, but the operation is not blocked.</span></span> <span data-ttu-id="83700-121">또한 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 에이전트 계정 구성을 변경하여 그로 인해 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 에이전트가 필요한 WMI 클래스에 대한 사용 권한을 갖지 못하게 되면 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 의 해당 관리되는 인스턴스에 대한 데이터 수집을 UCP에 업로드하는 작업이 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="83700-121">Additionally, if you change the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent account configuration so that [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent does not have permission to required WMI classes, data collection on the affected managed instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] fails to upload to the UCP.</span></span> <span data-ttu-id="83700-122">그러면 UCP에 회색 아이콘이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="83700-122">This results in gray icons in the UCP.</span></span>  
  
 <span data-ttu-id="83700-123">데이터 수집이 실패하면 해당 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]관리되는 인스턴스의 UCP 목록 뷰에 회색 상태 아이콘이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="83700-123">Failed data collection results in gray status icons in the UCP list view for affected managed instances of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="83700-124">ph x="1" /&gt; 관리되는 인스턴스의 작업 기록에는 sysutility_mi_collect_and_upload가 2단계(PowerShell 스크립트에서 수집된 단계 데이터)에서 실패했다고 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="83700-124">The job history on the managed instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] shows that sysutility_mi_collect_and_upload fails on step 2 (Stage Data Collected from PowerShell Script).</span></span>  
  
 <span data-ttu-id="83700-125">이 경우 다음과 같은 오류 메시지만 출력됩니다.</span><span class="sxs-lookup"><span data-stu-id="83700-125">The simplified error messages are:</span></span>  
  
 <span data-ttu-id="83700-126">셸 변수 "ErrorActionPreference"가 Stop: Access denied로 설정되어 있으므로 명령 실행이 중지되었습니다.</span><span class="sxs-lookup"><span data-stu-id="83700-126">Command execution stopped because the shell variable "ErrorActionPreference" is set to Stop: Access denied.</span></span>  
  
 <span data-ttu-id="83700-127">오류: \<Date-time (MM/DD/YYYY HH:MM:SS)> : cpu 속성을 수집 하는 동안 예외를 CATCH 했습니다.</span><span class="sxs-lookup"><span data-stu-id="83700-127">ERROR: \<Date-time (MM/DD/YYYY HH:MM:SS)>: Caught exception while collecting cpu properties.</span></span>  <span data-ttu-id="83700-128">WMI 쿼리가 실패했을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83700-128">A WMI query might have failed.</span></span>  <span data-ttu-id="83700-129">경고.</span><span class="sxs-lookup"><span data-stu-id="83700-129">WARNING.</span></span>  
  
 <span data-ttu-id="83700-130">이 문제를 해결하려면 다음 구성 설정을 확인하십시오.///</span><span class="sxs-lookup"><span data-stu-id="83700-130">To resolve this issue, verify the following configuration settings:</span></span>  
  
-   <span data-ttu-id="83700-131">Windows Server 2003에서 SQL Server 에이전트 서비스 계정은 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]관리되는 인스턴스에서 Windows Performance Monitor User 그룹에 속해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="83700-131">On Windows Server 2003, the SQL Server Agent service must be part of the Windows Performance Monitoring group on the managed instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="83700-132">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]관리되는 인스턴스에서 WMI 서비스가 설정되고 구성되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="83700-132">The WMI service must be enabled and configured on the managed instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="83700-133">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]관리되는 인스턴스에서 WMI 리포지토리가 손상되었을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83700-133">The WMI repository might be corrupt on the managed instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="83700-134">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]관리되는 인스턴스에서 성능 라이브러리가 없거나 손상되었을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83700-134">The performance library might be missing or corrupt on the managed instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="83700-135">지정된 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 인스턴스가 UCP에 데이터를 보고하도록 올바르게 구성되어 있는지 확인하려면 다음 클래스를 지정된 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]인스턴스에서 사용할 수 있으며 SQL Server 에이전트 서비스 계정에서 액세스할 수 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="83700-135">To verify that the specified instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] is configured properly to report data to the UCP, verify that the following classes are available on the specified instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], and that they are accessible to SQL Server Agent service account:</span></span>  
  
-   <span data-ttu-id="83700-136">Win32_MountPoint</span><span class="sxs-lookup"><span data-stu-id="83700-136">Win32_MountPoint</span></span>  
  
-   <span data-ttu-id="83700-137">Win32_PerfRawData_PerfProc_Process</span><span class="sxs-lookup"><span data-stu-id="83700-137">Win32_PerfRawData_PerfProc_Process</span></span>  
  
-   <span data-ttu-id="83700-138">Win32_PerfRawData_PerfOS_Processor</span><span class="sxs-lookup"><span data-stu-id="83700-138">Win32_PerfRawData_PerfOS_Processor</span></span>  
  
-   <span data-ttu-id="83700-139">Win32_Processor</span><span class="sxs-lookup"><span data-stu-id="83700-139">Win32_Processor</span></span>  
  
-   <span data-ttu-id="83700-140">Win32_Volume</span><span class="sxs-lookup"><span data-stu-id="83700-140">Win32_Volume</span></span>  
  
-   <span data-ttu-id="83700-141">Win32_LogicalDisk</span><span class="sxs-lookup"><span data-stu-id="83700-141">Win32_LogicalDisk</span></span>  
  
 <span data-ttu-id="83700-142">각 클래스의 Get-WmiObject PowerShell cmdlet을 사용하여 해당 클래스에 액세스할 수 있는지 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83700-142">You can use the Get-WmiObject PowerShell cmdlet on each of the classes to verify that each class is accessible.</span></span> <span data-ttu-id="83700-143">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]관리되는 인스턴스에서 다음 cmdlet을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="83700-143">Run the following cmdlets on the managed instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]:</span></span>  
  
```  
Get-WmiObject Win32_MountPoint -ErrorAction Stop | Out-Null  
Get-WmiObject Win32_PerfRawData_PerfProc_Process -ErrorAction Stop| Out-Null  
Get-WmiObject Win32_PerfRawData_PerfOS_Processor -ErrorAction Stop | Out-Null  
Get-WmiObject Win32_Processor -ErrorAction Stop | Out-Null  
Get-WmiObject Win32_Volume -ErrorAction Stop | Out-Null  
Get-WmiObject Win32_LogicalDisk -ErrorAction Stop | Out-Null  
```  
  
 <span data-ttu-id="83700-144">WMI 문제 해결에 대 한 자세한 내용은 [Wmi 문제 해결](https://go.microsoft.com/fwlink/?LinkId=178250)을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="83700-144">For more information about troubleshooting WMI, see [Troubleshooting WMI](https://go.microsoft.com/fwlink/?LinkId=178250).</span></span> <span data-ttu-id="83700-145">이러한 SQL Server 유틸리티 작업의 쿼리는 로컬로 실행할 수 있으므로 DCOM 및 원격 문제 해결 정보에는 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="83700-145">Note that queries in these SQL Server Utility operations are running locally, so the DCOM and remote troubleshooting content does not apply.</span></span>  
  
## <a name="failed-data-collection"></a><span data-ttu-id="83700-146">데이터 수집 실패</span><span class="sxs-lookup"><span data-stu-id="83700-146">Failed Data Collection</span></span>  
 <span data-ttu-id="83700-147">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 유틸리티 데이터 수집 이벤트가 실패하면 다음 가능성을 고려하십시오.</span><span class="sxs-lookup"><span data-stu-id="83700-147">If [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Utility data collection events fail, consider the following possibilities:</span></span>  
  
-   <span data-ttu-id="83700-148">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]의 관리형 인스턴스에 있는 “유틸리티 정보” 컬렉션 세트의 속성은 변경해서는 안 되며, 데이터 컬렉션은 유틸리티 에이전트 작업에 의해 제어되므로 데이터 컬렉션을 수동으로 설정/해제하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="83700-148">Do not change any properties of the "Utility Information" collection set on a managed instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], and do not turn data collection on/off manually, as data collection is controlled by a Utility agent job.</span></span>  
  
-   <span data-ttu-id="83700-149">WMI 유효성 검사가 실패했거나 지원되지 않는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="83700-149">Failed or unsupported WMI validation.</span></span> <span data-ttu-id="83700-150">자세한 내용은 이 항목 앞부분의 "WMI 유효성 검사 실패" 섹션을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="83700-150">For more information, see the Failed WMI Validation section earlier in this topic.</span></span>  
  
-   <span data-ttu-id="83700-151">ph x="1" /&gt; 유틸리티 뷰포인트는 자동으로 새로 고치지지 않으므로 관리되는 인스턴스 목록 뷰의 데이터를 새로 고쳐 봅니다.</span><span class="sxs-lookup"><span data-stu-id="83700-151">Refresh data in the managed instance list view, as data in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Utility viewpoints does not refresh automatically.</span></span> <span data-ttu-id="83700-152">데이터를 새로 고치려면 **유틸리티 탐색기 탐색** 창의 **관리되는 인스턴스** 노드를 마우스 오른쪽 단추로 클릭한 다음 **새로 고침**을 선택하거나 목록 뷰에서 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 인스턴스 이름을 마우스 오른쪽 단추로 클릭한 다음 **새로 고침**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="83700-152">To refresh data, right-click the **Managed Instances** node in the **Utility Explorer Navigation** pane, then select **Refresh**, or right-click on the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] instance name in the list view, then select **Refresh**.</span></span> <span data-ttu-id="83700-153">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 인스턴스에 UCP를 등록한 후에 최대 30분이 지나야 유틸리티 탐색기 내용 창의 대시보드와 뷰포인트에 데이터가 표시되기 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="83700-153">Note that after an instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] has been enrolled with a UCP, it can take up to 30 minutes for data to first appear in the dashboard and viewpoints in the Utility Explorer content pane.</span></span>  
  
-   <span data-ttu-id="83700-154">SQL Server 구성 관리자를 사용하여 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 인스턴스가 실행 중인지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="83700-154">Use SQL Server Configuration Manager to verify that the instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] is running.</span></span>  
  
-   <span data-ttu-id="83700-155">데이터 수집 또는 데이터 업로드 작업이 제한 시간 문제로 인해 실패하면 MSDB 데이터베이스에서 dbo.fn_sysutility_mi_get_collect_script() 함수를 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="83700-155">If data collection or data upload fail due to timeout issues, update the function dbo.fn_sysutility_mi_get_collect_script() in the MSDB database.</span></span> <span data-ttu-id="83700-156">특히 "Invoke-BulkCopyCommand()" 함수에 아래 줄을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="83700-156">Specifically, in the function "Invoke-BulkCopyCommand()" add line:</span></span>  
  
    ```
    $bulkCopy.BulkCopyTimeout=180  
    ```  
  
     <span data-ttu-id="83700-157">기본 제한 시간 값은 30초입니다.</span><span class="sxs-lookup"><span data-stu-id="83700-157">The default timeout value is 30 seconds.</span></span>  
  
-   <span data-ttu-id="83700-158">ph x="1" /&gt; 인스턴스가 클러스터링되지 않은 경우 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 에이전트 서비스가 실행 중이고 이 서비스가 UCP와 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]의 관리되는 인스턴스에서 자동으로 시작되도록 설정되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="83700-158">If the instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] is not clustered, verify that the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent service is running and that the service is set to start automatically on the UCP and on the managed instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="83700-159">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]의 관리되는 인스턴스에서 데이터 수집을 실행하는 데 유효한 계정이 사용되는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="83700-159">Verify that a valid account is being used to run data collection on the managed instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="83700-160">예를 들어 암호가 만료되었을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83700-160">For example, the password may have expired.</span></span> <span data-ttu-id="83700-161">프록시 암호가 만료된 경우 다음과 같이 SSMS에서 암호 자격 증명을 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="83700-161">If the proxy password has expired, update password credentials in SSMS, as follows:</span></span>  
  
    1.  <span data-ttu-id="83700-162">SSMS **개체 탐색기**에서 **보안** 노드를 확장한 다음 **자격 증명** 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="83700-162">In SSMS **Object Explorer**, expand the **Security** node, then expand the **Credentials** node.</span></span>  
  
    2.  <span data-ttu-id="83700-163">\*\*UtilityAgentProxyCredential_ \<GUID> \*\* 를 마우스 오른쪽 단추로 클릭 하 고 **속성**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="83700-163">Right-click on **UtilityAgentProxyCredential_\<GUID>** and select **Properties**.</span></span>  
  
    3.  <span data-ttu-id="83700-164">자격 증명 속성 대화 상자에서 \*\*UtilityAgentProxyCredential_ \<GUID> \*\* 자격 증명에 필요한 자격 증명을 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="83700-164">On the Credential Properties dialog, update credentials as necessary for the **UtilityAgentProxyCredential_\<GUID>** credential.</span></span>  
  
    4.  <span data-ttu-id="83700-165">**확인**을 클릭하여 변경 내용을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="83700-165">Click **OK** to confirm the change.</span></span>  
  
-   <span data-ttu-id="83700-166">TCP/IP가 UCP 및 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]관리되는 인스턴스에서 설정되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="83700-166">TCP/IP should be enabled on the UCP and on the managed instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="83700-167">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 구성 관리자를 사용하여 TCP/IP를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="83700-167">Enable TCP/IP through [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Configuration Manager.</span></span>  
  
-   <span data-ttu-id="83700-168">UCP에서 SQL Server Browser 서비스가 시작되어야 하며 자동으로 시작하도록 구성되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="83700-168">The SQL Server Browser service on the UCP should be started and configured to start automatically.</span></span> <span data-ttu-id="83700-169">조직에서 SQL Server Browser 서비스 사용을 금지하는 경우 다음 단계를 사용하여 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 의 관리되는 인스턴스가 UCP에 연결하는 것을 허용하세요.</span><span class="sxs-lookup"><span data-stu-id="83700-169">If your organization prevents use of the SQL Server Browser service, use the following steps to allow a managed instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] to connect to the UCP:</span></span>  
  
    1.  <span data-ttu-id="83700-170">의 관리 되는 인스턴스의 Windows 작업 표시줄에서 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] **시작**, **실행**을 차례로 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="83700-170">On the Windows taskbar on the managed instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], click **Start**, then click **Run...**.</span></span>  
  
    2.  <span data-ttu-id="83700-171">입력란에 "cliconfg.exe"를 입력하고 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="83700-171">Type "cliconfg.exe" in the space provided, then click **OK**.</span></span>  
  
    3.  <span data-ttu-id="83700-172">"SQL 클라이언트 구성 유틸리티 EXE"를 시작하도록 허용하라는 메시지가 표시되면 "**계속**"을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="83700-172">If prompted to allow "SQL Client Configuration Utility EXE" to start, click "**Continue**."</span></span>  
  
    4.  <span data-ttu-id="83700-173">**SQL Server 클라이언트 네트워크 유틸리티** 대화 상자에서 **별칭** 탭을 선택 하 고 **추가 ...** 를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="83700-173">On the **SQL Server Client Network Utility** dialog box, select the **Alias** tab, then click **Add...**.</span></span>  
  
    5.  <span data-ttu-id="83700-174">**네트워크 라이브러리 구성 추가** 대화 상자에서 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="83700-174">On the **Add Network Library Configuration** dialog box:</span></span>  
  
    6.  <span data-ttu-id="83700-175">네트워크 라이브러리 목록에서 TCP/IP를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="83700-175">Specify TCP/IP from the list of network libraries.</span></span>  
  
    7.  <span data-ttu-id="83700-176">UCP의 **서버 별칭** 입력란에 ComputerName\InstanceName을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="83700-176">Specify the ComputerName\InstanceName of the UCP in the **Server Alias** text box.</span></span>  
  
    8.  <span data-ttu-id="83700-177">UCP의 **서버 이름** 입력란에 ComputerName을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="83700-177">Specify the ComputerName of the UCP in the **Server Name** text box.</span></span>  
  
    9. <span data-ttu-id="83700-178">**동적으로 포트 확인** 확인란의 선택을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="83700-178">Uncheck the **Dynamically determine port** checkbox.</span></span>  
  
    10. <span data-ttu-id="83700-179">**포트 번호** 입력란에 UCP가 수신하는 포트 번호를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="83700-179">Specify the port number that the UCP is listening on in the **Port number** text box.</span></span>  
  
    11. <span data-ttu-id="83700-180">**확인**을 클릭하여 변경 내용을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="83700-180">Click **OK** to save your changes.</span></span>  
  
    12. <span data-ttu-id="83700-181">SQL Server Browser 서비스가 해제되어 있는 UCP에 연결하는 각 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 의 관리되는 인스턴스에 대해 이 단계를 반복합니다.</span><span class="sxs-lookup"><span data-stu-id="83700-181">Repeat these steps for each managed instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] that connects to a UCP where the SQL Server Browser service is not enabled.</span></span>  
  
-   <span data-ttu-id="83700-182">ph x="1" /&gt; 의 관리되는 인스턴스가 네트워크에 연결되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="83700-182">Ensure that managed instances of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] are connected to the network.</span></span>  
  
-   <span data-ttu-id="83700-183">이름은 같지만 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]관리되는 인스턴스의 대/소문자 설정이 다른 데이터베이스가 있는 경우 데이터베이스와 해당 뷰포인트 간의 식별이 잘못되어 데이터 수집이 실패할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83700-183">If there are databases with the same name but different case-sensitivity settings on a managed instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], the identification between the database and its viewpoints can be incorrect, resulting in failed data collection.</span></span> <span data-ttu-id="83700-184">예를 들어 "MYDATABASE"라는 데이터베이스가 "MyDatabase"라는 데이터베이스의 상태를 보여 줄 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83700-184">For example, a database named "MYDATABASE" might show health states for a database named "MyDatabase".</span></span> <span data-ttu-id="83700-185">이 시나리오에서는 오류가 발생하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="83700-185">No error is generated in this scenario.</span></span> <span data-ttu-id="83700-186">또한 UCP에 표시되는 다른 객체에서 데이터베이스 파일 및 파일 그룹 이름 등의 대/소문자가 일치하지 않아 데이터 수집이 실패할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83700-186">Failed data collection can also result from case-sensitivity mismatches in other objects displayed in the UCP, like database file and file group names.</span></span>  
  
-   <span data-ttu-id="83700-187">ph x="1" /&gt; 관리되는 인스턴스가 Windows Server 2003 컴퓨터에서 호스팅되는 경우 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 에이전트 서비스 계정이 성능 모니터 사용자 보안 그룹이나 로컬 관리자 그룹에 속해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="83700-187">If a managed instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] is hosted on a Windows Server 2003 computer, then the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent service account must belong to the Performance Monitor Users security group or the local Administrators group.</span></span> <span data-ttu-id="83700-188">그렇지 않으면 액세스 거부 오류가 발생하고 데이터베이스 수집이 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="83700-188">Otherwise, data collection will fail with an access denied error.</span></span> <span data-ttu-id="83700-189">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 에이전트 서비스 계정을 성능 모니터 사용자 보안 그룹에 추가하려면 다음 단계를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="83700-189">To add a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent service account to the Performance Monitor Users security group, use the following steps:</span></span>  
  
    1.  <span data-ttu-id="83700-190">**컴퓨터 관리**, **로컬 사용자 및 그룹**, **그룹**을 차례로 엽니다.</span><span class="sxs-lookup"><span data-stu-id="83700-190">Open **Computer Management**, then **Local Users and Groups**, then **Groups**.</span></span>  
  
    2.  <span data-ttu-id="83700-191">**성능 모니터 사용자** 를 마우스 오른쪽 단추로 클릭하고 **그룹에 추가**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="83700-191">Right-click **Performance Monitor Users** and select **Add to Group**.</span></span>  
  
    3.  <span data-ttu-id="83700-192">**추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="83700-192">Click **Add**.</span></span>  
  
    4.  <span data-ttu-id="83700-193">SQL Server 에이전트 서비스가 실행되고 있는 계정을 입력하고 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="83700-193">Enter the account that the SQL Server Agent service is running under, then click **OK**.</span></span>  
  
    5.  <span data-ttu-id="83700-194">사용자를 이 그룹에 추가하기 전에 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 인스턴스에 이미 UCP가 등록된 경우 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 에이전트 서비스를 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="83700-194">If the instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] was already enrolled with the UCP before adding the user to this group, restart the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83700-195">참고 항목</span><span class="sxs-lookup"><span data-stu-id="83700-195">See Also</span></span>  
 <span data-ttu-id="83700-196">[SQL Server 유틸리티 기능 및 태스크](../relational-databases/manage/sql-server-utility-features-and-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="83700-196">[SQL Server Utility Features and Tasks](../relational-databases/manage/sql-server-utility-features-and-tasks.md) </span></span>  
 [<span data-ttu-id="83700-197">SQL Server 리소스 상태 문제 해결&#40;SQL Server 유틸리티&#41;</span><span class="sxs-lookup"><span data-stu-id="83700-197">Troubleshoot SQL Server Resource Health &#40;SQL Server Utility&#41;</span></span>](../relational-databases/manage/troubleshoot-sql-server-resource-health-sql-server-utility.md)
