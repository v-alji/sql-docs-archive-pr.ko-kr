---
title: 원격 관리를 위한 보고서 서버 구성 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- Reporting Services Configuration tool
- WMI provider [Reporting Services], remote configuration
- configuration management [WMI]
- report servers [Reporting Services], configuring
- remote server administration [Reporting Services]
ms.assetid: 8c7f145f-3ac2-4203-8cd6-2a4694395d09
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 2c34db5299fc1b82a7896a41519e55466c3b3b79
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652600"
---
# <a name="configure-a-report-server-for-remote-administration"></a><span data-ttu-id="aef8e-102">원격 관리를 위한 보고서 서버 구성</span><span class="sxs-lookup"><span data-stu-id="aef8e-102">Configure a Report Server for Remote Administration</span></span>
  <span data-ttu-id="aef8e-103">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]에서는 보고서 서버 인스턴스를 로컬 또는 원격으로 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aef8e-103">In [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], you can configure report server instances locally or remotely.</span></span> <span data-ttu-id="aef8e-104">원격 보고서 서버 인스턴스를 구성하려면 Reporting Services 구성 도구를 사용하거나, [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] WMI(Windows Management Instrumentation) 공급자를 사용하는 사용자 지정 코드를 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aef8e-104">To configure a remote report server instance, you can use the Reporting Services Configuration tool or write custom code that uses the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Windows Management Instrumentation (WMI) provider.</span></span> <span data-ttu-id="aef8e-105">Reporting Services 구성 도구는 WMI 공급자에 대한 그래픽 인터페이스를 제공하므로 이 도구를 사용하면 코드를 작성하지 않고도 보고서 서버를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aef8e-105">The Reporting Services Configuration tool provides a graphical interface to the WMI provider so that you can configure a report server without having to write code.</span></span> <span data-ttu-id="aef8e-106">이 도구를 시작할 때 연결할 원격 서버를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aef8e-106">When you start the tool, you can specify a remote server to connect to.</span></span>  
  
 <span data-ttu-id="aef8e-107">구성 도구를 사용하여 원격 보고서 서버를 구성하기 전에 이 항목의 지침에 따라 Windows 방화벽에서 포트 설정, 원격 연결 설정 및 원격 WMI 요청 설정 작업을 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="aef8e-107">Before you can use the tool to configure a remote report server, you must follow the instructions in this topic to enable ports in Windows Firewall, enable remote connections, and enable remote WMI requests.</span></span>  
  
 <span data-ttu-id="aef8e-108">적절한 구성을 사용하면 다음 오류를 피할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aef8e-108">Proper configuration helps you avoid the following error:</span></span>  
  
 `The machine could not be found.`  
  
 `"The RPC server is unavailable. (Exception from HRESULT: 0x800706BA)".`  
  
## <a name="prerequisites"></a><span data-ttu-id="aef8e-109">사전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="aef8e-109">Prerequisites</span></span>  
 <span data-ttu-id="aef8e-110">방화벽 설정을 수정하려면 로컬 Administrators 그룹의 멤버여야 하며 로컬로 로그온해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="aef8e-110">To modify firewall settings, you must be logged on locally and you must be a member of the local Administrators group.</span></span> <span data-ttu-id="aef8e-111">원격 컴퓨터의 Windows 방화벽 설정을 원격 연결을 통해 수정할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="aef8e-111">You cannot modify the Windows firewall settings of a remote computer over a remote connection.</span></span>  
  
 <span data-ttu-id="aef8e-112">관리자가 아닌 사용자가 원격 관리를 사용할 수 있도록 하려면 DCOM(Distributed Component Object Model) 원격 활성화 권한을 해당 계정에 부여해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="aef8e-112">If you want to enable remote administration for a non-administrator user, you must grant the account Distributed Component Object Model (DCOM) Remote Activation permissions.</span></span> <span data-ttu-id="aef8e-113">관리자가 아닌 사용자가 액세스할 수 있도록 서버를 구성하는 방법은 이 항목에 설명되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aef8e-113">Instructions for configuring the server for non-administrator access are provided in this topic.</span></span>  
  
 <span data-ttu-id="aef8e-114">일부 조직에는 특정 운영 체제나 사용자에 대해 원격 서버 관리를 사용할 수 없도록 하는 그룹 정책이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aef8e-114">Some organizations have group policies that prevent remote server administration for certain operating systems or users.</span></span> <span data-ttu-id="aef8e-115">따라서 방화벽 설정을 수정하기 전에 네트워크 관리자에게 문의하여 원격 관리에 대한 제한이 있는지 여부를 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="aef8e-115">Before you begin modifying firewall settings, check with your network administrator to verify whether there are restrictions on remote administration.</span></span>  
  
 <span data-ttu-id="aef8e-116">자세한 내용은 MSDN에 있는 Platform SDK 설명서에서 [Windows 방화벽을 통한 연결](https://go.microsoft.com/fwlink/?LinkId=63615) 을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="aef8e-116">For more information, see [Connecting Through Windows Firewall](https://go.microsoft.com/fwlink/?LinkId=63615) in the Platform SDK documentation on MSDN.</span></span>  
  
## <a name="tasks"></a><span data-ttu-id="aef8e-117">작업</span><span class="sxs-lookup"><span data-stu-id="aef8e-117">Tasks</span></span>  
 <span data-ttu-id="aef8e-118">원격 보고서 서버 구성을 활성화하는 태스크는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="aef8e-118">Tasks that enable remote report server configuration include the following:</span></span>  
  
-   <span data-ttu-id="aef8e-119">Windows 방화벽에서 포트를 설정하여 보고서 서버와 SQL Server 데이터베이스 엔진 인스턴스에서 사용하는 포트에 대한 요청을 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="aef8e-119">Enable ports in Windows Firewall to allow requests on ports used by the report server and by the SQL Server Database Engine instance.</span></span>  
  
-   <span data-ttu-id="aef8e-120">보고서 서버 데이터베이스를 호스팅하는 데이터베이스 엔진 인스턴스에 대한 원격 연결을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="aef8e-120">Enable remote connections to the instance of the Database Engine instance that hosts the report server database.</span></span> <span data-ttu-id="aef8e-121">원격 연결은 보고서 서버 데이터베이스 연결을 구성하고 암호화 키를 관리하는 데 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="aef8e-121">A remote connection is necessary for configuring the report server database connection and managing the encryption keys.</span></span>  
  
-   <span data-ttu-id="aef8e-122">원격 WMI 요청이 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 방화벽을 통과하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="aef8e-122">Enable remote WMI requests to pass through the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows firewall.</span></span>  
  
-   <span data-ttu-id="aef8e-123">관리 권한이 없는 사용자가 관리할 수 있도록 원격 보고서 서버를 구성하는 경우 표준 Windows 사용자 계정에 대한 원격 WMI 액세스가 가능하도록 DCOM 권한을 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="aef8e-123">If you are configuring a remote report server for administration by a non-administrative user, you must set DCOM permissions to enable remote WMI access to a standard Windows user account.</span></span> <span data-ttu-id="aef8e-124">WMI에서는 원격 호출을 전송하는 데 DCOM을 사용하므로 로컬 관리자로 로그온하지 않은 사용자가 서버를 구성할 수 있도록 하려면 DCOM 권한을 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="aef8e-124">Because WMI uses DCOM as transport for remote calls, you must set the DCOM permissions so that users who are not logged on as the local administrator can configure the server.</span></span>  
  
-   <span data-ttu-id="aef8e-125">관리 권한이 없는 사용자가 관리할 수 있도록 원격 보고서 서버를 구성하는 경우 보고서 서버 WMI 네임스페이스에 대한 WMI 권한도 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="aef8e-125">If you are configuring a remote report server for administration by a non-administrative user, you must also set WMI permissions on the report server WMI namespace.</span></span> <span data-ttu-id="aef8e-126">기본적으로 로컬 Administrators 그룹의 모든 멤버는 보고서 서버 WMI 네임스페이스에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aef8e-126">By default, all members of the local Administrator group have access to the report server WMI namespace.</span></span> <span data-ttu-id="aef8e-127">관리자가 아닌 사용자에게 액세스 권한을 부여하려면 권한을 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="aef8e-127">If you want to grant access to non-administrators, you must set permissions.</span></span>  
  
 <span data-ttu-id="aef8e-128">이러한 태스크를 수행하는 방법은 이 항목에 설명되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aef8e-128">Instructions on how to perform these tasks are provided in this topic.</span></span>  
  
### <a name="to-open-ports-in-windows-firewall"></a><span data-ttu-id="aef8e-129">Windows 방화벽에서 포트를 열려면</span><span class="sxs-lookup"><span data-stu-id="aef8e-129">To open ports in Windows Firewall</span></span>  
  
1.  <span data-ttu-id="aef8e-130">[데이터베이스 엔진 액세스에 대 한 Windows 방화벽을 구성](../../database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="aef8e-130">[Configure a Windows Firewall for Database Engine Access](../../database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access.md).</span></span>  
  
2.  <span data-ttu-id="aef8e-131">[보고서 서버 액세스를 위한 방화벽을 구성](configure-a-firewall-for-report-server-access.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="aef8e-131">[Configure a Firewall for Report Server Access](configure-a-firewall-for-report-server-access.md).</span></span>  
  
### <a name="to-configure-remote-connections-to-the-report-server-database"></a><span data-ttu-id="aef8e-132">보고서 서버 데이터베이스에 대한 원격 연결을 구성하려면</span><span class="sxs-lookup"><span data-stu-id="aef8e-132">To configure remote connections to the report server database</span></span>  
  
1.  <span data-ttu-id="aef8e-133">**시작**을 클릭하고 **프로그램**, [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)], **구성 도구**를 차례로 가리킨 다음 **SQL Server 구성 관리자**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="aef8e-133">Click **Start**, point to **Programs**, point to [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)], point to **Configuration Tools**, and click **SQL Server Configuration Manager**.</span></span>  
  
2.  <span data-ttu-id="aef8e-134">왼쪽 창에서 **SQL Server 네트워크 구성**을 확장한 다음 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에 대한 **프로토콜**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="aef8e-134">In the left pane, expand **SQL Server Network Configuration**, and then click **Protocols** for the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
3.  <span data-ttu-id="aef8e-135">세부 정보 창에서 TCP/IP 및 명명된 파이프 프로토콜을 설정한 다음 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 서비스를 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="aef8e-135">In the details pane, enable the TCP/IP and Named Pipes protocols, and then restart the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service.</span></span>  
  
### <a name="to-enable-remote-administration-in-windows-firewall"></a><span data-ttu-id="aef8e-136">Windows 방화벽에서 원격 관리를 활성화하려면</span><span class="sxs-lookup"><span data-stu-id="aef8e-136">To enable remote administration in Windows Firewall</span></span>  
  
1.  <span data-ttu-id="aef8e-137">원격 관리를 활성화할 컴퓨터에 로컬 관리자로 로그온합니다.</span><span class="sxs-lookup"><span data-stu-id="aef8e-137">Log on as a local administrator to the computer for which you want to enable remote administration.</span></span>  
  
2.  <span data-ttu-id="aef8e-138">보고서 서버가 Windows Vista에서 실행 되는 경우 **명령 프롬프트** 를 마우스 오른쪽 단추로 클릭 하 고 **관리자 권한으로 실행**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="aef8e-138">If the report server is running on Windows Vista, right-click **Command Prompt** and select **Run as administrator**.</span></span> <span data-ttu-id="aef8e-139">다른 운영 체제의 경우 명령 프롬프트 창을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="aef8e-139">For other operating systems, open a command prompt window.</span></span>  
  
3.  <span data-ttu-id="aef8e-140">다음 명령 실행:</span><span class="sxs-lookup"><span data-stu-id="aef8e-140">Run the following command:</span></span>  
  
    ```  
    netsh.exe firewall set service type=REMOTEADMIN mode=ENABLE scope=ALL  
    ```  
  
     <span data-ttu-id="aef8e-141">scope에는 다른 옵션을 지정해도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="aef8e-141">You can specify different options for Scope.</span></span> <span data-ttu-id="aef8e-142">자세한 내용은 Windows 방화벽 제품 설명서를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="aef8e-142">For more information, see the Windows Firewall product documentation.</span></span>  
  
4.  <span data-ttu-id="aef8e-143">원격 관리가 활성화되었는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="aef8e-143">Verify that remote administration is enabled.</span></span> <span data-ttu-id="aef8e-144">다음 명령을 실행하여 상태를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aef8e-144">You can run the following command to show the status:</span></span>  
  
    ```  
    netsh.exe firewall show state  
    ```  
  
5.  <span data-ttu-id="aef8e-145">컴퓨터를 다시 부팅합니다.</span><span class="sxs-lookup"><span data-stu-id="aef8e-145">Reboot the computer.</span></span>  
  
### <a name="to-set-dcom-permissions-to-enable-remote-wmi-access-for-non-administrators"></a><span data-ttu-id="aef8e-146">관리자가 아닌 사용자가 원격 WMI에 액세스할 수 있도록 DCOM 권한을 설정하려면</span><span class="sxs-lookup"><span data-stu-id="aef8e-146">To set DCOM permissions to enable remote WMI access for non-administrators</span></span>  
  
1.  <span data-ttu-id="aef8e-147">시작 메뉴에서 **관리 도구**를 가리키고 **구성 요소 서비스**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="aef8e-147">On the Start menu, point to **Administrative Tools**, click **Component Services**.</span></span>  
  
     <span data-ttu-id="aef8e-148">Windows Vista의 경우 시작 메뉴에서 **모든 프로그램**, **실행**을 차례로 클릭 한 다음를 입력 `mmc comexp.msc` 합니다.</span><span class="sxs-lookup"><span data-stu-id="aef8e-148">For Windows Vista, on the Start menu, click **All Programs**, click **Run**, and then enter `mmc comexp.msc`.</span></span>  
  
2.  <span data-ttu-id="aef8e-149">구성 요소 서비스 폴더를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="aef8e-149">Open the Component Services folder.</span></span>  
  
3.  <span data-ttu-id="aef8e-150">컴퓨터 폴더를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="aef8e-150">Open the Computers folder.</span></span>  
  
4.  <span data-ttu-id="aef8e-151">내 컴퓨터를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="aef8e-151">Select My Computer.</span></span>  
  
5.  <span data-ttu-id="aef8e-152">**동작** 메뉴에서 **속성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="aef8e-152">On the **Action** menu, and select **Properties**.</span></span>  
  
6.  <span data-ttu-id="aef8e-153">**COM 보안**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="aef8e-153">Click **COM Security**.</span></span>  
  
7.  <span data-ttu-id="aef8e-154">**시작 및 활성화 권한**에서 **제한값 편집**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="aef8e-154">In **Launch and Activation Permissions**, click **Edit Limits**.</span></span>  
  
8.  <span data-ttu-id="aef8e-155">**시작 및 활성화 권한**에 사용자의 이름이 표시되어 있지 않으면 **추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="aef8e-155">If you do not see your name in **Launch Permission**, click **Add**.</span></span>  
  
9. <span data-ttu-id="aef8e-156">사용자 계정 이름을 입력하고 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="aef8e-156">Type the name of your user account, and then click **OK**.</span></span>  
  
10. <span data-ttu-id="aef8e-157">\*\* \<User or Group> 의 사용 권한 \*\*에서 **허용** 열에서 **원격 시작** 및 **원격 활성화**를 선택한 다음 **확인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="aef8e-157">In **Permissions for \<User or Group>**, in the **Allow** column, select **Remote Launch** and **Remote Activation**, and then click **OK**.</span></span>  
  
### <a name="to-set-permissions-on-the-report-server-wmi-namespace-for-non-administrators"></a><span data-ttu-id="aef8e-158">관리자가 아닌 사용자가 액세스할 수 있도록 보고서 서버 WMI 네임스페이스에 대한 권한을 설정하려면</span><span class="sxs-lookup"><span data-stu-id="aef8e-158">To set permissions on the report server WMI namespace for non-administrators</span></span>  
  
1.  <span data-ttu-id="aef8e-159">시작 메뉴에서 **관리 도구**를 가리키고 **컴퓨터 관리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="aef8e-159">On the Start menu, point to **Administrative Tools**, click **Computer Management**.</span></span>  
  
2.  <span data-ttu-id="aef8e-160">서비스 및 애플리케이션 폴더를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="aef8e-160">Open the Services and Applications folder.</span></span>  
  
3.  <span data-ttu-id="aef8e-161">**WMI 컨트롤**을 마우스 오른쪽 단추로 클릭하고 **속성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="aef8e-161">Right-click **WMI Control**, and select **Properties**.</span></span>  
  
4.  <span data-ttu-id="aef8e-162">**보안**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="aef8e-162">Click **Security**.</span></span>  
  
5.  <span data-ttu-id="aef8e-163">Root 폴더를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="aef8e-163">Open the Root folder.</span></span>  
  
6.  <span data-ttu-id="aef8e-164">Microsoft 폴더를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="aef8e-164">Open the Microsoft folder.</span></span>  
  
7.  <span data-ttu-id="aef8e-165">SQLServer 폴더를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="aef8e-165">Open the SQLServer folder.</span></span>  
  
8.  <span data-ttu-id="aef8e-166">ReportServer 폴더를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="aef8e-166">Open the ReportServer folder.</span></span>  
  
9. <span data-ttu-id="aef8e-167">인스턴스 폴더를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="aef8e-167">Open instance folder.</span></span> <span data-ttu-id="aef8e-168">기본 인스턴스를 설치한 경우 폴더는 MSSQLSERVER입니다.</span><span class="sxs-lookup"><span data-stu-id="aef8e-168">If you installed the default instance, the folder is MSSQLSERVER.</span></span>  
  
10. <span data-ttu-id="aef8e-169">v10 폴더를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="aef8e-169">Open the v10 folder.</span></span>  
  
11. <span data-ttu-id="aef8e-170">Admin 폴더를 선택한 다음 **보안**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="aef8e-170">Select the Admin folder, and then click **Security**.</span></span>  
  
12. <span data-ttu-id="aef8e-171">**추가**를 클릭한 다음 서버를 관리하는 데 사용할 사용자 계정을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="aef8e-171">Click **Add**, and then type the user account you will use to manage the server.</span></span>  
  
13. <span data-ttu-id="aef8e-172">**허용** 열에서 **계정 사용**, **원격으로부터 사용 가능**및 **보안 읽기**를 선택한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="aef8e-172">In the **Allow** column, select **Enable Account**, **Remote Enable**, and **Read Security**, and then click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aef8e-173">참고 항목</span><span class="sxs-lookup"><span data-stu-id="aef8e-173">See Also</span></span>  
 [<span data-ttu-id="aef8e-174">Reporting Services 구성 관리자&#40;기본 모드&#41;</span><span class="sxs-lookup"><span data-stu-id="aef8e-174">Reporting Services Configuration Manager &#40;Native Mode&#41;</span></span>](../../sql-server/install/reporting-services-configuration-manager-native-mode.md)  
  
  
