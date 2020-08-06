---
title: SQL Server 유틸리티에서 SQL Server 인스턴스 제거 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
f1_keywords:
- sql12.swb.utility.remove.f1
ms.assetid: ae1d126a-46d2-47bf-b339-17c743df6491
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 6c09897fcd3ac6d82308288391cf54176eef49d9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661102"
---
# <a name="remove-an-instance-of-sql-server-from-the-sql-server-utility"></a><span data-ttu-id="7906d-102">SQL Server 유틸리티에서 SQL Server 인스턴스 제거</span><span class="sxs-lookup"><span data-stu-id="7906d-102">Remove an Instance of SQL Server from the SQL Server Utility</span></span>
  <span data-ttu-id="7906d-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 유틸리티에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 관리되는 인스턴스를 제거하려면 다음 단계를 수행하세요.</span><span class="sxs-lookup"><span data-stu-id="7906d-103">Use the following steps to remove a managed instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] from the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Utility.</span></span> <span data-ttu-id="7906d-104">이 절차를 수행하면 UCP 목록 뷰에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스가 제거되며 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 유틸리티 데이터 컬렉션이 중지됩니다.</span><span class="sxs-lookup"><span data-stu-id="7906d-104">This procedure removes the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] from the UCP list view and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Utility data collection stops.</span></span> <span data-ttu-id="7906d-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스가 제거되는 것은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="7906d-105">The instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is not uninstalled.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="7906d-106">이 절차를 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 유틸리티에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 의 관리되는 인스턴스를 제거하기 전에 제거할 인스턴스에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 및 SQL Server 에이전트 서비스가 실행 중인지 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="7906d-106">Before you use this procedure to remove an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] from the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Utility, make sure that the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and SQL Server Agent services are running on the instance to remove.</span></span>  
  
1.  <span data-ttu-id="7906d-107">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]의 유틸리티 탐색기에서 **관리되는 인스턴스**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7906d-107">From the Utility Explorer in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], click on **Managed Instances**.</span></span> <span data-ttu-id="7906d-108">유틸리티 탐색기 탐색 창에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 의 관리되는 인스턴스 목록 뷰를 살펴봅니다.</span><span class="sxs-lookup"><span data-stu-id="7906d-108">Observe the list view of managed instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in the Utility Explorer content pane.</span></span>  
  
2.  <span data-ttu-id="7906d-109">목록 뷰의 **SQL Server 인스턴스 이름** 열에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 유틸리티에서 제거할 인스턴스를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="7906d-109">In the **SQL Server Instance Name** column of the list view, select the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance to remove from the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Utility.</span></span> <span data-ttu-id="7906d-110">제거할 인스턴스를 마우스 오른쪽 단추로 클릭하고 **Managed Instance 제거...** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="7906d-110">Right-click on the instance to remove, and select **Remove Managed Instance...**.</span></span>  
  
3.  <span data-ttu-id="7906d-111">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에 대한 관리자 권한이 있는 자격 증명을 지정합니다. **연결…** 을 클릭하고 **서버에 연결** 대화 상자의 정보를 확인한 다음, **연결**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7906d-111">Specify credentials with administrator privileges for the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]: Click **Connect...**, verify the information in the **Connect to Server** dialog box, then click **Connect**.</span></span> <span data-ttu-id="7906d-112">**관리되는 인스턴스 제거** 대화 상자에 로그인 정보가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="7906d-112">You will see the login information on the **Remove Managed Instance** dialog.</span></span>  
  
4.  <span data-ttu-id="7906d-113">작업을 수행하려면 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7906d-113">To confirm the operation, click **OK**.</span></span> <span data-ttu-id="7906d-114">작업을 취소하려면 **취소**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7906d-114">To quit the operation, click **Cancel**.</span></span>  
  
## <a name="manually-remove-a-managed-instance-of-sql-server-from-a-sql-server-utility"></a><span data-ttu-id="7906d-115">SQL Server 유틸리티에서 수동으로 SQL Server의 관리되는 인스턴스 제거</span><span class="sxs-lookup"><span data-stu-id="7906d-115">Manually Remove a Managed Instance of SQL Server from a SQL Server Utility</span></span>  
 <span data-ttu-id="7906d-116">이 절차를 수행하면 UCP 목록 뷰에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스가 제거되며 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 유틸리티 데이터 컬렉션이 중지됩니다.</span><span class="sxs-lookup"><span data-stu-id="7906d-116">This procedure removes the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] from the UCP list view and stops [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Utility data collection.</span></span> <span data-ttu-id="7906d-117">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스가 제거되는 것은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="7906d-117">The instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is not uninstalled.</span></span>  
  
 <span data-ttu-id="7906d-118">PowerShell을 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 유틸리티에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 의 관리되는 인스턴스를 제거하려면 다음 단계를 수행하세요.</span><span class="sxs-lookup"><span data-stu-id="7906d-118">To use PowerShell to remove a managed instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] from the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Utility.</span></span> <span data-ttu-id="7906d-119">이 스크립트는 다음 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="7906d-119">This script performs the following operations:</span></span>  
  
-   <span data-ttu-id="7906d-120">서버 인스턴스 이름으로 UCP를 얻습니다.</span><span class="sxs-lookup"><span data-stu-id="7906d-120">Gets the UCP by server instance name.</span></span>  
  
-   <span data-ttu-id="7906d-121">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 유틸리티에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 의 관리되는 인스턴스를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="7906d-121">Removes the managed instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] from the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Utility.</span></span>  
  
```powershell
# Get Ucp connection  
$UcpServerInstanceName = "ComputerName\InstanceName";  
$UtilityInstance = new-object -Type Microsoft.SqlServer.Management.Smo.Server $UcpServerInstanceName;  
$UcpConnection = new-object -Type Microsoft.SqlServer.Management.Sdk.Sfc.SqlStoreConnection $UtilityInstance.ConnectionContext.SqlConnectionObject;  
$Utility = [Microsoft.SqlServer.Management.Utility.Utility]::Connect($UcpConnection);  
  
# Now remove the ManagedInstance from the SQL Server Utility  
$ServerInstanceName = "ComputerName\InstanceName";  
$Instance = new-object -Type Microsoft.SqlServer.Management.Smo.Server $ServerInstanceName;  
$InstanceConnection = new-object -Type Microsoft.SqlServer.Management.Sdk.Sfc.SqlStoreConnection $Instance.ConnectionContext.SqlConnectionObject;  
$ManagedInstance = $Utility.ManagedInstances[$ServerInstanceName];  
$ManagedInstance.Remove($InstanceConnection);  
```  
  
<span data-ttu-id="7906d-122">에 저장 된 것과 동일 하 게 인스턴스 이름을 참조 하는 것이 중요 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 합니다.</span><span class="sxs-lookup"><span data-stu-id="7906d-122">It's important to refer to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance name exactly as it is stored in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="7906d-123">대/소문자를 구분하는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에서는 @@SERVERNAME으로 반환되는 것과 동일하게 대/소문자를 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7906d-123">On a case-sensitive instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], you must specify the instance name using the exact casing as returned by @@SERVERNAME.</span></span> 

<span data-ttu-id="7906d-124">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 관리되는 인스턴스의 인스턴스 이름을 얻으려면 관리되는 인스턴스에서 이 쿼리를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="7906d-124">To get the instance name for the managed instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], run this query on the managed instance:</span></span>  
  
```sql
select @@SERVERNAME AS instance_name  
```  
  
 <span data-ttu-id="7906d-125">이렇게 하면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 의 관리되는 인스턴스가 UCP에서 완전하게 제거됩니다.</span><span class="sxs-lookup"><span data-stu-id="7906d-125">At this point, the managed instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is fully removed from the UCP.</span></span> <span data-ttu-id="7906d-126">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 유틸리티에서 데이터를 다음번 새로 고치면 목록 뷰에 해당 인스턴스가 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7906d-126">It disappears from the list view the next time you refresh data for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Utility.</span></span> <span data-ttu-id="7906d-127">이 상태는 SSMS 사용자 인터페이스를 통해 관리되는 인스턴스 제거 작업을 성공적으로 수행한 것과 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="7906d-127">This state is identical to a user successfully going through the remove managed instance operation in the SSMS user interface.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7906d-128">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7906d-128">See Also</span></span>  
 <span data-ttu-id="7906d-129">[유틸리티 탐색기를 사용하여 SQL Server 유틸리티 관리](use-utility-explorer-to-manage-the-sql-server-utility.md) </span><span class="sxs-lookup"><span data-stu-id="7906d-129">[Use Utility Explorer to Manage the SQL Server Utility](use-utility-explorer-to-manage-the-sql-server-utility.md) </span></span>  
 [<span data-ttu-id="7906d-130">SQL Server 유틸리티 문제 해결</span><span class="sxs-lookup"><span data-stu-id="7906d-130">Troubleshoot the SQL Server Utility</span></span>](../../database-engine/troubleshoot-the-sql-server-utility.md)  
