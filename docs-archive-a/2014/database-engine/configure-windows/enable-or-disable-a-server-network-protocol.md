---
title: 서버 네트워크 프로토콜 설정 또는 해제 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- network protocols [SQL Server], disabling
- remote connections [SQL Server], enabling using Configuration Manager
- protocols [SQL Server], enabling using Configuration Manager
- protocols [SQL Server], disabling using Configuration Manager
- disabling network protocols, Configuration Manager
- network protocols [SQL Server], enabling
- enabling network protocols, Configuration Manager
- surface area configuration [SQL Server], connection protocols
- connections [SQL Server], enabling remote using Configuration Manager
ms.assetid: ec5ccb69-61c9-4576-8843-014b976fd46e
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 737edae84ff284ed726ade69cb48e574b830611e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87732016"
---
# <a name="enable-or-disable-a-server-network-protocol"></a><span data-ttu-id="7bd45-102">서버 네트워크 프로토콜 설정 또는 해제</span><span class="sxs-lookup"><span data-stu-id="7bd45-102">Enable or Disable a Server Network Protocol</span></span>
  <span data-ttu-id="7bd45-103">기본적으로 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 설치 프로그램에서는 모든 네트워크 프로토콜이 설치되지만 일부 프로토콜이 설정되거나 설정되지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7bd45-103">All network protocols are installed by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup, but may or may not be enabled.</span></span> <span data-ttu-id="7bd45-104">이 항목에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 구성 관리자 또는 PowerShell을 사용하여 서버 네트워크 프로토콜을 설정하거나 해제하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="7bd45-104">This topic describes how to enable or disable a server network protocol in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager or PowerShell.</span></span> <span data-ttu-id="7bd45-105">변경 내용을 적용하려면 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 을 중지한 뒤 다시 시작해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7bd45-105">The [!INCLUDE[ssDE](../../includes/ssde-md.md)] must be stopped and restarted for the change to take effect.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="7bd45-106">[!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] 설치 중에 BUILTIN\Users 그룹에 대한 로그인이 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="7bd45-106">During setup of [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] a login is added for the BUILTIN\Users group.</span></span> <span data-ttu-id="7bd45-107">이 로그인을 사용하면 컴퓨터의 모든 인증된 사용자가 public 역할의 멤버로 [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] 인스턴스에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7bd45-107">This allows all authenticated users of the computer to access the instance of [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] as a member of the public role.</span></span> <span data-ttu-id="7bd45-108">BUILTIN\Users 로그인은 개별 로그인이 있거나 로그인이 있는 기타 Windows 그룹의 멤버인 컴퓨터 사용자에 대한 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 액세스를 제한하기 위해 안전하게 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7bd45-108">The BUILTIN\Users login can be safely removed to restrict [!INCLUDE[ssDE](../../includes/ssde-md.md)] access to computer users who have individual logins or are members of other Windows groups with logins.</span></span>  
  
> [!WARNING]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="7bd45-109">에 대한 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 및 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 데이터 공급자는 TLS 1.0 및 SSL 3.0을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="7bd45-109">and [!INCLUDE[msCoName](../../includes/msconame-md.md)] data providers for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] support TLS 1.0 and SSL 3.0.</span></span> <span data-ttu-id="7bd45-110">운영 체제 SChannel 계층을 변경하여 다른 프로토콜 (예: TLS 1.1 또는 TLS 1.2)를 적용하면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에 대한 연결이 실패할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7bd45-110">If you enforce a different protocol (such as TLS 1.1 or TLS 1.2) by making changes in the operating system SChannel layer, your connections to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] might fail.</span></span>  
  
 <span data-ttu-id="7bd45-111">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="7bd45-111">**In This Topic**</span></span>  
  
-   <span data-ttu-id="7bd45-112">**다음을 사용하여 서버 네트워크 프로토콜을 설정하거나 해제합니다.**</span><span class="sxs-lookup"><span data-stu-id="7bd45-112">**To enable or disable a server network protocol using:**</span></span>  
  
     [<span data-ttu-id="7bd45-113">SQL Server 구성 관리자</span><span class="sxs-lookup"><span data-stu-id="7bd45-113">SQL Server Configuration Manager</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="7bd45-114">PowerShell</span><span class="sxs-lookup"><span data-stu-id="7bd45-114">PowerShell</span></span>](#PowerShellProcedure)  
  
##  <a name="using-sql-server-configuration-manager"></a><a name="SSMSProcedure"></a> <span data-ttu-id="7bd45-115">SQL Server 구성 관리자 사용</span><span class="sxs-lookup"><span data-stu-id="7bd45-115">Using SQL Server Configuration Manager</span></span>  
  
#### <a name="to-enable-a-server-network-protocol"></a><span data-ttu-id="7bd45-116">서버 네트워크 프로토콜을 설정하려면</span><span class="sxs-lookup"><span data-stu-id="7bd45-116">To enable a server network protocol</span></span>  
  
1.  <span data-ttu-id="7bd45-117">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 구성 관리자의 콘솔 창에서 **SQL Server 네트워크 구성**을 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="7bd45-117">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, in the console pane, expand **SQL Server  Network Configuration**.</span></span>  
  
2.  <span data-ttu-id="7bd45-118">콘솔 창에서 *\<instance name>* 에 대한 **프로토콜**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7bd45-118">In the console pane, click **Protocols for** *\<instance name>*.</span></span>  
  
3.  <span data-ttu-id="7bd45-119">세부 정보 창에서 변경할 프로토콜을 마우스 오른쪽 단추로 클릭한 다음 **사용** 또는 **사용 안 함**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7bd45-119">In the details pane, right-click the protocol you want to change, and then click **Enable** or **Disable**.</span></span>  
  
4.  <span data-ttu-id="7bd45-120">콘솔 창에서 **SQL Server 서비스**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7bd45-120">In the console pane, click **SQL Server Services**.</span></span>  
  
5.  <span data-ttu-id="7bd45-121">세부 정보 창에서 **SQL Server ( ***\<instance name>*** )** 를 마우스 오른쪽 단추로 클릭 한 다음 **다시 시작**을 클릭 하 여 서비스를 중지 하 고 다시 시작 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 합니다.</span><span class="sxs-lookup"><span data-stu-id="7bd45-121">In the details pane, right-click **SQL Server (***\<instance name>***)**, and then click **Restart**, to stop and restart the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service.</span></span>  
  
##  <a name="using-sql-server-powershell"></a><a name="PowerShellProcedure"></a> <span data-ttu-id="7bd45-122">SQL Server PowerShell 사용</span><span class="sxs-lookup"><span data-stu-id="7bd45-122">Using SQL Server PowerShell</span></span>  
  
#### <a name="to-enable-a-server-network-protocol-using-powershell"></a><span data-ttu-id="7bd45-123">PowerShell을 사용하여 서버 네트워크 프로토콜을 설정하려면</span><span class="sxs-lookup"><span data-stu-id="7bd45-123">To Enable a Server Network Protocol Using PowerShell</span></span>  
  
1.  <span data-ttu-id="7bd45-124">관리자 권한으로 명령 프롬프트를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="7bd45-124">Using administrator permissions open a command prompt.</span></span>  
  
2.  <span data-ttu-id="7bd45-125">작업 표시줄에서 Windows PowerShell 2.0을 시작하거나, 시작, 모든 프로그램, 보조프로그램, Windows PowerShell, Windows PowerShell을 차례로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7bd45-125">Start Windows PowerShell 2.0 from the taskbar, or click Start, then All Programs, then Accessories, then Windows PowerShell, then Windows PowerShell.</span></span>  
  
3.  <span data-ttu-id="7bd45-126">다음을 입력 하 여 **sqlps** 모듈을 가져옵니다.`Import-Module "sqlps"`</span><span class="sxs-lookup"><span data-stu-id="7bd45-126">Import the **sqlps** module by entering `Import-Module "sqlps"`</span></span>  
  
4.  <span data-ttu-id="7bd45-127">다음 문을 실행하여 TCP 및 명명된 파이프 프로토콜을 모두 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="7bd45-127">Execute the following statements to enable both the TCP and named pipes protocols.</span></span> <span data-ttu-id="7bd45-128">`<computer_name>` 을 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]가 실행 중인 컴퓨터의 이름으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="7bd45-128">Replace `<computer_name>` with the name of the computer that is running [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="7bd45-129">명명된 인스턴스를 구성할 경우 `MSSQLSERVER` 를 인스턴스의 이름으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="7bd45-129">If you are configuring a named instance, replace `MSSQLSERVER` with the instance name.</span></span>  
  
     <span data-ttu-id="7bd45-130">프로토콜을 해제하려면 `IsEnabled` 속성을 `$false`로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="7bd45-130">To disable protocols, set the `IsEnabled` properties to `$false`.</span></span>  
  
    ```powershell
    $smo = 'Microsoft.SqlServer.Management.Smo.'  
    $wmi = new-object ($smo + 'Wmi.ManagedComputer').  
  
    # List the object properties, including the instance names.  
    $Wmi  
  
    # Enable the TCP protocol on the default instance.  
    $uri = "ManagedComputer[@Name='<computer_name>']/ ServerInstance[@Name='MSSQLSERVER']/ServerProtocol[@Name='Tcp']"  
    $Tcp = $wmi.GetSmoObject($uri)  
    $Tcp.IsEnabled = $true  
    $Tcp.Alter()  
    $Tcp  
  
    # Enable the named pipes protocol for the default instance.  
    $uri = "ManagedComputer[@Name='<computer_name>']/ ServerInstance[@Name='MSSQLSERVER']/ServerProtocol[@Name='Np']"  
    $Np = $wmi.GetSmoObject($uri)  
    $Np.IsEnabled = $true  
    $Np.Alter()  
    $Np  
    ```  
  
#### <a name="to-configure-the-protocols-for-the-local-computer"></a><span data-ttu-id="7bd45-131">로컬 컴퓨터의 프로토콜을 구성하려면</span><span class="sxs-lookup"><span data-stu-id="7bd45-131">To configure the protocols for the local computer</span></span>  
  
-   <span data-ttu-id="7bd45-132">스크립트가 로컬로 실행되고 로컬 컴퓨터를 구성할 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell은 로컬 컴퓨터의 이름을 동적으로 확인하여 보다 유연한 스크립트를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7bd45-132">When the script is run locally and configures the local computer, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell can make the script more flexible by dynamically determining the local computer name.</span></span> <span data-ttu-id="7bd45-133">로컬 컴퓨터 이름을 가져오려면 `$uri` 변수 설정 행을 다음 행으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="7bd45-133">To retrieve the local computer name, replace the line setting the `$uri` variable with the following line.</span></span>  
  
    ```powershell
    $uri = "ManagedComputer[@Name='" + (Get-Item env:\computername).Value + "']/ServerInstance[@Name='MSSQLSERVER']/ServerProtocol[@Name='Tcp']"  
    ```  
  
#### <a name="to-restart-the-database-engine-by-using-sql-server-powershell"></a><span data-ttu-id="7bd45-134">SQL Server PowerShell을 사용하여 데이터베이스 엔진을 다시 시작하려면</span><span class="sxs-lookup"><span data-stu-id="7bd45-134">To restart the Database Engine by using SQL Server PowerShell</span></span>  
  
-   <span data-ttu-id="7bd45-135">프로토콜을 설정하거나 해제한 후에는 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 을 중지하고 다시 시작해야만 변경 내용이 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="7bd45-135">After you enable or disable protocols, you must stop and restart the [!INCLUDE[ssDE](../../includes/ssde-md.md)] for the change to take effect.</span></span> <span data-ttu-id="7bd45-136">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell을 사용하여 다음 문을 실행함으로써 기본 인스턴스를 중지한 후 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="7bd45-136">Execute the following statements to stop and start the default instance by using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell.</span></span> <span data-ttu-id="7bd45-137">명명된 인스턴스를 중지한 후 다시 시작하려면 `'MSSQLSERVER'` 를 `'MSSQL$<instance_name>'`으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="7bd45-137">To stop and start a named instance replace `'MSSQLSERVER'` with `'MSSQL$<instance_name>'`.</span></span>  
  
    ```powershell
    # Get a reference to the ManagedComputer class.  
    CD SQLSERVER:\SQL\<computer_name>  
    $Wmi = (Get-Item .).ManagedComputer  
    # Get a reference to the default instance of the Database Engine.  
    $DfltInstance = $Wmi.Services['MSSQLSERVER']  
    # Display the state of the service.  
    $DfltInstance  
    # Stop the service.  
    $DfltInstance.Stop();  
    # Wait until the service has time to stop.  
    # Refresh the cache.  
    $DfltInstance.Refresh();   
    # Display the state of the service.  
    $DfltInstance  
    # Start the service again.  
    $DfltInstance.Start();  
    # Wait until the service has time to start.  
    # Refresh the cache and display the state of the service.  
    $DfltInstance.Refresh(); $DfltInstance  
    ```  
