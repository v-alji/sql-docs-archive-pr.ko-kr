---
title: Server Core 설치 시 SQL Server 구성 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
helpviewer_keywords:
- IsHadrEnabled server property
- Server Core Installation [SQL Server]
ms.assetid: ed6e5e94-4b8d-422a-a17e-61b05a4df903
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e74307374e0d07d69107649b42e0bc2f0897e98c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734427"
---
# <a name="configure-sql-server-on-a-server-core-installation"></a><span data-ttu-id="9ba49-102">Server Core 설치 시 SQL Server 구성</span><span class="sxs-lookup"><span data-stu-id="9ba49-102">Configure SQL Server on a Server Core Installation</span></span>
  <span data-ttu-id="9ba49-103">이 항목에서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SP1의 Server Core 설치에서 [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] 를 구성하는 방법에 대한 자세한 내용을 다룹니다.</span><span class="sxs-lookup"><span data-stu-id="9ba49-103">This topic covers details about configuring [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on a Server Core installation of [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1.</span></span> 
  
##  <a name="configure-and-manage-server-core-on-windows-server"></a><span data-ttu-id="9ba49-104">Windows Server에서 Server Core 구성 및 관리</span><span class="sxs-lookup"><span data-stu-id="9ba49-104">Configure and Manage Server Core on Windows Server</span></span>  
 <span data-ttu-id="9ba49-105">이 섹션에서는 Server Core 설치를 구성 및 관리하는 항목에 대한 참조를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="9ba49-105">The section provides references to the topics that help configure and manage a Server Core installation.</span></span>  
  
 <span data-ttu-id="9ba49-106">Server Core 모드에서 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 의 일부 기능은 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9ba49-106">Not all features of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] are supported in Server Core mode.</span></span>  <span data-ttu-id="9ba49-107">일부 구성 요소는 클라이언트 컴퓨터 또는 Server Core를 실행하지 않는 다른 서버에 설치하거나 Server Core에 설치된 데이터베이스 엔진 서비스에 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9ba49-107">Some of these features can be installed on a client computer or a different server that is not running Server Core, and connected to the Database Engine services installed on Server Core.</span></span>  
  
 <span data-ttu-id="9ba49-108">Server Core 설치를 원격으로 구성하고 관리하는 방법에 대한 자세한 내용은 다음 항목을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="9ba49-108">For more information about configuring and managing a Server Core installation remotely, see the following topics:</span></span>  
  
-   <span data-ttu-id="9ba49-109">[Windows server 2008 R2: Server Core 배포에 대 한 모범 사례](https://go.microsoft.com/fwlink/?LinkID=245957) (https://go.microsoft.com/fwlink/?LinkID=245957)</span><span class="sxs-lookup"><span data-stu-id="9ba49-109">[Windows Server 2008 R2: Best Practices for Server Core Deployments](https://go.microsoft.com/fwlink/?LinkID=245957) (https://go.microsoft.com/fwlink/?LinkID=245957)</span></span>  
  
-   <span data-ttu-id="9ba49-110">[Server Core 설치 구성: 개요](https://go.microsoft.com/fwlink/?LinkId=245958) (https://go.microsoft.com/fwlink/?LinkId=245958)</span><span class="sxs-lookup"><span data-stu-id="9ba49-110">[Configuring a Server Core installation: Overview](https://go.microsoft.com/fwlink/?LinkId=245958) (https://go.microsoft.com/fwlink/?LinkId=245958)</span></span>  
  
-   <span data-ttu-id="9ba49-111">[Sconfig .cmd를 사용 하 여 Windows server 2008 r 2의 Server Core 설치 구성](https://go.microsoft.com/fwlink/?LinkId=245959) (https://go.microsoft.com/fwlink/?LinkId=245959)</span><span class="sxs-lookup"><span data-stu-id="9ba49-111">[Configuring a Server Core installation of Windows Server 2008 R2 with Sconfig.cmd](https://go.microsoft.com/fwlink/?LinkId=245959) (https://go.microsoft.com/fwlink/?LinkId=245959)</span></span>  
  
-   <span data-ttu-id="9ba49-112">[Windows server 2008 r 2의 Server Core 설치를 실행 하는 서버에 서버 역할 설치: 개요](https://go.microsoft.com/fwlink/?LinkId=245960) (https://go.microsoft.com/fwlink/?LinkId=245960)</span><span class="sxs-lookup"><span data-stu-id="9ba49-112">[Installing a server role on a server running a Server Core installation of Windows Server 2008 R2: Overview](https://go.microsoft.com/fwlink/?LinkId=245960) (https://go.microsoft.com/fwlink/?LinkId=245960)</span></span>  
  
-   <span data-ttu-id="9ba49-113">[Windows server 2008 r 2의 Server Core 설치를 실행 하는 서버에 Windows 기능 설치: 개요](https://go.microsoft.com/fwlink/?LinkId=245961) (https://go.microsoft.com/fwlink/?LinkId=245961)</span><span class="sxs-lookup"><span data-stu-id="9ba49-113">[Installing Windows Features on a server running a Server Core installation of Windows Server 2008 R2: Overview](https://go.microsoft.com/fwlink/?LinkId=245961) (https://go.microsoft.com/fwlink/?LinkId=245961)</span></span>  
  
-   <span data-ttu-id="9ba49-114">[Server Core 설치 관리: 개요](https://go.microsoft.com/fwlink/?LinkId=245962) (https://go.microsoft.com/fwlink/?LinkId=245962)</span><span class="sxs-lookup"><span data-stu-id="9ba49-114">[Managing a Server Core installation: Overview](https://go.microsoft.com/fwlink/?LinkId=245962) (https://go.microsoft.com/fwlink/?LinkId=245962)</span></span>  
  
-   <span data-ttu-id="9ba49-115">[Server Core 설치 관리](https://go.microsoft.com/fwlink/?LinkId=245963) (https://go.microsoft.com/fwlink/?LinkId=245963)</span><span class="sxs-lookup"><span data-stu-id="9ba49-115">[Administering a Server Core installation](https://go.microsoft.com/fwlink/?LinkId=245963) (https://go.microsoft.com/fwlink/?LinkId=245963)</span></span>  
  
##  <a name="install-updates"></a><span data-ttu-id="9ba49-116">업데이트 설치</span><span class="sxs-lookup"><span data-stu-id="9ba49-116">Install updates</span></span>  
 <span data-ttu-id="9ba49-117">이 섹션에서는 Windows Server Core 시스템에서 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 업데이트 설치에 대한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="9ba49-117">This section provides information about installing updates for [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] on a Windows Server Core machine.</span></span> <span data-ttu-id="9ba49-118">시스템이 최신 보안 업데이트로 업데이트되도록 고객이 적절한 시기에 최신 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 업데이트를 확인하고 설치하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="9ba49-118">We recommend that customers evaluate and install latest [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] updates in a timely manner to make sure that systems are up-to-date with the most recent security updates.</span></span> <span data-ttu-id="9ba49-119">Windows Server Core 컴퓨터에를 설치 하는 방법에 대 한 자세한 내용은 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [Server core에 SQL Server 2014 설치](install-sql-server-on-server-core.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="9ba49-119">For more information about installing [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] on a Windows Server Core machine, see [Install SQL Server 2014 on Server Core](install-sql-server-on-server-core.md).</span></span>  
  
 <span data-ttu-id="9ba49-120">제품 업데이트를 설치하기 위한 두 가지 시나리오는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="9ba49-120">The following are the two scenarios for installing product updates:</span></span>  
  
-   [<span data-ttu-id="9ba49-121">새로 설치 하는 동안 SQL Server 2014에 대 한 업데이트 설치</span><span class="sxs-lookup"><span data-stu-id="9ba49-121">Installing Updates for SQL Server 2014 During a New Installation</span></span>](#installing-updates-during-a-new-installation) 
  
-   [<span data-ttu-id="9ba49-122">설치 후 SQL Server 2014에 대 한 업데이트 설치</span><span class="sxs-lookup"><span data-stu-id="9ba49-122">Installing Updates for SQL Server 2014 After It Has Been Installed</span></span>](#installing-updates-after-installation) 
  
### <a name="installing-updates-during-a-new-installation"></a><span data-ttu-id="9ba49-123">새로 설치 하는 동안 업데이트 설치</span><span class="sxs-lookup"><span data-stu-id="9ba49-123">Installing updates during a new installation</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="9ba49-124">설치 프로그램은 Server Core 운영 체제에서 명령 프롬프트 설치만 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="9ba49-124">Setup supports only command prompt installations on Server Core operating system.</span></span> <span data-ttu-id="9ba49-125">자세한 내용은 [명령 프롬프트에서 SQL Server 2014 설치](install-sql-server-from-the-command-prompt.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9ba49-125">For more information, see [Install SQL Server 2014 from the Command Prompt](install-sql-server-from-the-command-prompt.md).</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="9ba49-126">설치 프로그램에서 최신 제품 업데이트를 주 제품 설치와 통합하여 주 제품과 해당 업데이트가 동시에 설치되게 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9ba49-126">setup integrates the latest product updates with the main product installation so that the main product and its applicable updates are installed at the same time.</span></span>  
  
 <span data-ttu-id="9ba49-127">설치 프로그램에서 최신 버전의 적용 가능한 업데이트를 찾으면 이를 다운로드하고 현재의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 설치 프로세스와 통합합니다.</span><span class="sxs-lookup"><span data-stu-id="9ba49-127">After Setup finds the latest versions of the applicable updates, it downloads and integrates them with the current [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] setup process.</span></span> <span data-ttu-id="9ba49-128">제품 업데이트에는 누적 업데이트, 서비스 팩 또는 서비스 팩과 누적 업데이트가 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9ba49-128">Product Update can pull in a cumulative update, service pack, or service pack plus cumulative update.</span></span>  
  
 <span data-ttu-id="9ba49-129">주 제품 설치에 최신 제품 업데이트를 포함하려면 UpdateEnabled 및 UpdateSource 매개 변수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="9ba49-129">Specify the UpdateEnabled, and UpdateSource parameters to include the latest product updates with the main product installation.</span></span> <span data-ttu-id="9ba49-130">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 설치 중에 제품 업데이트를 사용하려면 다음 예제를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="9ba49-130">Refer the following example to enable product updates during the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup:</span></span>  
  
```cmd 
Setup.exe /qs /ACTION=Install /FEATURES=SQLEngine,Replication /INSTANCENAME=MSSQLSERVER /SQLSVCACCOUNT="<DomainName\UserName>" /SQLSVCPASSWORD="<StrongPassword>" /SQLSYSADMINACCOUNTS="<DomainName\UserName>" /AGTSVCACCOUNT="NT AUTHORITY\Network Service" /UpdateEnabled=True /UpdateSource="<SourcePath>" /IACCEPTSQLSERVERLICENSETERMS  
```  
  
### <a name="installing-updates-after-installation"></a><span data-ttu-id="9ba49-131">설치 후 업데이트 설치</span><span class="sxs-lookup"><span data-stu-id="9ba49-131">Installing updates after installation</span></span> 
 <span data-ttu-id="9ba49-132">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]인스턴스가 설치된 경우 GDR(General Distribution Release) 및 SP(서비스 팩)를 포함한 최신 보안 업데이트와 중요 업데이트를 적용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="9ba49-132">On an installed instance of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], we recommend that you apply the latest security updates and critical updates including General Distribution Releases (GDRs), and Service Packs (SPs).</span></span> <span data-ttu-id="9ba49-133">개별 누적 업데이트와 보안 업데이트는 "필요할 때" 사례별로 채택해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ba49-133">Individual Cumulative updates and security updates should be adopted on a case-by-case, "as-needed" basis.</span></span> <span data-ttu-id="9ba49-134">업데이트를 확인하여 필요하면 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="9ba49-134">Evaluate the update; if it's needed, then apply it.</span></span>  
  
 <span data-ttu-id="9ba49-135">명령 프롬프트에서 <package_name>을 해당하는 업데이트 패키지 이름으로 바꾸어 업데이트를 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="9ba49-135">Apply an update at a command prompt, replacing <package_name> with the name of your update package:</span></span>  
  
-   <span data-ttu-id="9ba49-136">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 및 모든 구성 요소의 단일 인스턴스를 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="9ba49-136">Update a single instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and all shared components.</span></span> <span data-ttu-id="9ba49-137">InstanceName 매개 변수 또는 InstanceID 매개 변수를 사용하여 인스턴스를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9ba49-137">You can specify the instance either by using the InstanceName parameter or the InstanceID parameter.</span></span>  
  
    ```  
    <package_name>.exe /qs /IAcceptSQLServerLicenseTerms /Action=Patch /InstanceName=MyInstance  
    ```  
  
-   <span data-ttu-id="9ba49-138">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 공유 구성 요소만 업데이트:</span><span class="sxs-lookup"><span data-stu-id="9ba49-138">Update [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] shared components only:</span></span>  
  
    ```  
    <package_name>.exe /qs /IAcceptSQLServerLicenseTerms /Action=Patch  
    ```  
  
-   <span data-ttu-id="9ba49-139">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 컴퓨터의 모든 인스턴스 및 모든 공유 구성 요소 업데이트:</span><span class="sxs-lookup"><span data-stu-id="9ba49-139">Update all instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on the computer and all shared components:</span></span>  
  
    ```  
    <package_name>.exe /qs /IAcceptSQLServerLicenseTerms /Action=Patch /AllInstances  
    ```  
  
##  <a name="startstop-sql-server-service"></a><span data-ttu-id="9ba49-140">SQL Server 서비스 시작/중지</span><span class="sxs-lookup"><span data-stu-id="9ba49-140">Start/Stop SQL Server service</span></span>  
 <span data-ttu-id="9ba49-141">[sqlservr 애플리케이션](../../tools/sqlservr-application.md) 은 명령 프롬프트에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스를 시작, 중지, 일시 중지 및 계속합니다.</span><span class="sxs-lookup"><span data-stu-id="9ba49-141">The [sqlservr Application](../../tools/sqlservr-application.md) application starts, stops, pauses, and continues an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] from a command prompt.</span></span>  
  
 <span data-ttu-id="9ba49-142">Net 서비스를 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 서비스를 시작하고 중지할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9ba49-142">You can also use Net services to start and stop the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] services.</span></span>  
  
## <a name="enable-alwayson-availability-groups"></a><span data-ttu-id="9ba49-143">AlwaysOn 가용성 그룹 사용</span><span class="sxs-lookup"><span data-stu-id="9ba49-143">Enable AlwaysOn Availability Groups</span></span>  
 <span data-ttu-id="9ba49-144">서버 인스턴스에서 고가용성 및 재해 복구 솔루션으로 가용성 그룹을 사용하려면 먼저 AlwaysOn 가용성 그룹을 사용하도록 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ba49-144">Being enabled for AlwaysOn Availability Groups is a prerequisite for a server instance to use availability groups as a high availability and disaster recovery solution.</span></span> <span data-ttu-id="9ba49-145">AlwaysOn 가용성 그룹 관리에 대한 자세한 내용은 [AlwaysOn 가용성 그룹 활성화 및 비활성화&#40;SQL Server&#41;](../availability-groups/windows/enable-and-disable-always-on-availability-groups-sql-server.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9ba49-145">For more information about managing the AlwaysOn Availability Groups, see [Enable and Disable AlwaysOn Availability Groups &#40;SQL Server&#41;](../availability-groups/windows/enable-and-disable-always-on-availability-groups-sql-server.md).</span></span>  
  
### <a name="using-sql-server-configuration-manager-remotely"></a><span data-ttu-id="9ba49-146">원격으로 SQL Server 구성 관리자 사용</span><span class="sxs-lookup"><span data-stu-id="9ba49-146">Using SQL Server Configuration Manager Remotely</span></span>  
 <span data-ttu-id="9ba49-147">이러한 단계는 [!INCLUDE[win7](../../includes/win7-md.md)] 이상의 클라이언트 버전을 실행하는 PC 또는 서버 그래픽 셸이 설치된 다른 서버에서 수행됨을 의미합니다( [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] 전체 설치 또는 서버 그래픽 셸 기능이 활성화된 Windows Server 8 설치).</span><span class="sxs-lookup"><span data-stu-id="9ba49-147">These steps are meant to be performed on a PC running the client edition of [!INCLUDE[win7](../../includes/win7-md.md)] or later, or another server that has the Server Graphical Shell installed (i.e. a full installation of [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] or a Windows Server 8 installation with the Server Graphical Shell feature enabled).</span></span>  
  
1.  <span data-ttu-id="9ba49-148">컴퓨터 관리를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="9ba49-148">Open Computer Management.</span></span> <span data-ttu-id="9ba49-149">컴퓨터 관리를 열려면 다음 중 하나를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="9ba49-149">To open Computer Management do one of the following:</span></span>  
  
    1.  <span data-ttu-id="9ba49-150">[!INCLUDE[win7](../../includes/win7-md.md)], Windows Server 2008 또는 [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="9ba49-150">On [!INCLUDE[win7](../../includes/win7-md.md)], Windows Server 2008, or [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)]:</span></span>  
  
        1.  <span data-ttu-id="9ba49-151">시작, 모든 프로그램을 클릭하고 관리 도구를 클릭한 다음 컴퓨터 관리를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9ba49-151">Click Start, click All Programs, click Administrative Tools, and then click Computer Management.</span></span>  
  
        2.  <span data-ttu-id="9ba49-152">시작을 클릭하고 실행을 클릭한 다음 COMPMGMT를 입력하고 확인을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9ba49-152">Click Start, click Run, type COMPMGMT.MSC, and then click OK.</span></span>  
  
    2.  <span data-ttu-id="9ba49-153">서버 그래픽 셸이 활성화된 Windows 8:</span><span class="sxs-lookup"><span data-stu-id="9ba49-153">On Windows 8 with Server Graphical Shell enabled:</span></span>  
  
        1.  <span data-ttu-id="9ba49-154">화면의 왼쪽 아래 모서리에 마우스를 이동하고 시작 오버레이가 나타나면 마우스 오른쪽 단추로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9ba49-154">Move your mouse to the bottom-left corner of the screen and right-click when you see the Start overlay.</span></span>  
  
        2.  <span data-ttu-id="9ba49-155">상황에 맞는 메뉴에서 컴퓨터 관리를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="9ba49-155">Select Computer Management  from the context menu.</span></span>  
  
2.  <span data-ttu-id="9ba49-156">콘솔 트리에서 컴퓨터 관리를 마우스 오른쪽 단추로 클릭하고 다른 컴퓨터로 연결을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9ba49-156">In the console tree, right-click Computer Management, and then click Connect to another computer.</span></span>  
  
3.  <span data-ttu-id="9ba49-157">컴퓨터 선택 대화 상자에서 관리할 Server Core 컴퓨터의 이름을 입력하거나 찾아보기를 클릭하여 찾은 다음 확인을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9ba49-157">In the Select Computer dialog box, type the name of the Server Core machine that you want to manage, or click Browse to find it, and then click OK.</span></span>  
  
4.  <span data-ttu-id="9ba49-158">콘솔 트리에 있는 Server Core 컴퓨터의 컴퓨터 관리에서 서비스 및 애플리케이션을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9ba49-158">In the console tree, under Computer Management of the Server Core machine, click Services and Applications.</span></span>  
  
5.  <span data-ttu-id="9ba49-159">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 구성 관리자를 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9ba49-159">Double click [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager.</span></span>  
  
6.  <span data-ttu-id="9ba49-160">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Configuration Manager에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 서비스를 클릭 하 고 ()를 마우스 오른쪽 단추로 클릭 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \<instance name> \<instance name> 합니다. 여기서은 AlwaysOn 가용성 그룹를 사용 하도록 설정 하려는 로컬 서버 인스턴스의 이름이 고 속성을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ba49-160">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, click [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Services, right-click [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (\<instance name>), where \<instance name> is the name of a local server instance for which you want to enable AlwaysOn Availability Groups, and click Properties.</span></span>  
  
7.  <span data-ttu-id="9ba49-161">AlwaysOn 고가용성 탭을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="9ba49-161">Select the AlwaysOn High Availability tab.</span></span>  
  
8.  <span data-ttu-id="9ba49-162">Windows 장애 조치(failover) 클러스터 이름 필드에 로컬 장애 조치(failover) 클러스터 노드의 이름이 포함되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="9ba49-162">Verify that Windows failover cluster name field contains the name of the local failover cluster node.</span></span> <span data-ttu-id="9ba49-163">이 필드가 비어 있으면 이 서버 인스턴스는 현재 AlwaysOn 가용성 그룹을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9ba49-163">If this field is blank, this server instance currently does not support AlwaysOn Availability Groups.</span></span> <span data-ttu-id="9ba49-164">로컬 컴퓨터가 클러스터 노드가 아니거나 WSFC 클러스터가 종료되었거나 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 버전이 AlwaysOn 가용성 그룹을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9ba49-164">Either the local computer is not a cluster node, the WSFC cluster has been shut down, or this edition of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] that does not support AlwaysOn Availability Groups.</span></span>  
  
9. <span data-ttu-id="9ba49-165">AlwaysOn 가용성 그룹 사용 확인란을 선택하고 확인을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9ba49-165">Select the Enable AlwaysOn Availability Groups check box, and click OK.</span></span>  
  
10. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="9ba49-166">구성 관리자가 변경 내용을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="9ba49-166">Configuration Manager saves your change.</span></span> <span data-ttu-id="9ba49-167">그런 다음 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 서비스를 수동으로 다시 시작해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ba49-167">Then, you must manually restart the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service.</span></span> <span data-ttu-id="9ba49-168">이렇게 하면 비즈니스 요구 사항에 가장 적합한 다시 시작 시간을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9ba49-168">This enables you to choose a restart time that is best for your business requirements.</span></span> <span data-ttu-id="9ba49-169">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 서비스를 다시 시작하면 AlwaysOn을 사용할 수 있으며 IsHadrEnabled 서버 속성이 1로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="9ba49-169">When the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service restarts, AlwaysOn will be enabled, and the IsHadrEnabled server property will be set to 1.</span></span>  
  
> [!NOTE]
>  -   <span data-ttu-id="9ba49-170">적절한 사용자 권한이 있거나 해당 컴퓨터에 연결하기 위해 대상 컴퓨터에 대한 적절한 권한을 위임해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ba49-170">You must have the appropriate user rights or you must have been delegated the appropriate authority on the target computer to connect to that computer.</span></span>  
> -   <span data-ttu-id="9ba49-171">관리하는 컴퓨터의 이름이 콘솔 트리의 컴퓨터 관리 옆에 괄호로 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="9ba49-171">The name of the computer that you are managing appears in parentheses next to Computer Management in the console tree.</span></span>  
  
### <a name="using-powershell-cmdlets-to-enable-alwayson-availability-groups"></a><span data-ttu-id="9ba49-172">AlwaysOn 가용성 그룹 설정을 위해 PowerShell Cmdlet 사용</span><span class="sxs-lookup"><span data-stu-id="9ba49-172">Using PowerShell Cmdlets to Enable AlwaysOn Availability Groups</span></span>

 <span data-ttu-id="9ba49-173">PowerShell Cmdlet Enable-SqlAlwaysOn은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 인스턴스에서 AlwaysOn 가용성 그룹을 설정하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="9ba49-173">The PowerShell Cmdlet, Enable-SqlAlwaysOn, is used to enable AlwaysOn Availability Group on an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="9ba49-174">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 서비스가 실행되고 있을 때 AlwaysOn 가용성 그룹이 설정되면 데이터베이스 엔진 서비스를 다시 시작해야 변경이 완료됩니다.</span><span class="sxs-lookup"><span data-stu-id="9ba49-174">If AlwaysOn Availability Groups is enable while the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service is running, the Database Engine service must be restarted for the change to complete.</span></span> <span data-ttu-id="9ba49-175">-Force 매개 변수를 지정하지 않으면 cmdlet이 서비스를 다시 시작할 것인지를 묻는 메시지를 표시합니다. 취소할 경우 아무 작업도 발생하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9ba49-175">Unless you specify the -Force parameter, the cmdlet prompts you to ask whether you wish to restart the service; if cancelled, no operation occurs.</span></span>  
  
 <span data-ttu-id="9ba49-176">이 cmdlet을 실행하려면 관리자 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ba49-176">You must have Administrator permissions to execute this cmdlet.</span></span>  
  
 <span data-ttu-id="9ba49-177">다음 구문 중 하나를 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스에 대한 AlwaysOn 가용성 그룹을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9ba49-177">You can use one of the following syntaxes to enable AlwaysOn Availability Groups for an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:</span></span>  
  
```  
Enable-SqlAlwaysOn [-Path <string>] [-Credential <PSCredential>] [-Force] [-NoServiceRestart] [-Confirm] [-WhatIf] [<Commom Parameters>]  
```  
  
```  
Enable-SqlAlwaysOn -InputObject <Server> [-Credential <PSCredential>] [-Force] [-NoServiceRestart] [-Confirm] [-WhatIf] [<Commom Parameters>]  
```  
  
```  
Enable-SqlAlwaysOn [-ServerInstance <string>] [-Credential <PSCredential>] [-Force] [-NoServiceRestart] [-Confirm] [-WhatIf] [<Commom Parameters>]  
```  
  
 <span data-ttu-id="9ba49-178">다음 PowerShell 명령을 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스(Machine\Instance)에 대한 AlwaysOn 가용성 그룹을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9ba49-178">The following PowerShell command enables AlwaysOn Availability Groups on an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (Machine\Instance):</span></span>  
  
```powershell
Enable-SqlAlwaysOn -Path SQLSERVER:\SQL\Machine\Instance  
```  
  
## <a name="configuring-remote-access-of-sql-server-running-on-server-core"></a><span data-ttu-id="9ba49-179">Server Core에서 실행 되는 SQL Server의 원격 액세스 구성</span><span class="sxs-lookup"><span data-stu-id="9ba49-179">Configuring remote access of SQL Server running on Server Core</span></span>  
 <span data-ttu-id="9ba49-180">아래 설명된 작업을 수행하여 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Server Core SP1에서 실행하는 [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] 인스턴스의 원격 액세스를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="9ba49-180">Perform the actions described below to configure remote access of a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] instance that is running on [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] Server Core SP1.</span></span>  
  
### <a name="enable-remote-connections-on-an-instance-of-sql-server"></a><span data-ttu-id="9ba49-181">SQL Server의 인스턴스에서 원격 연결을 사용 하도록 설정</span><span class="sxs-lookup"><span data-stu-id="9ba49-181">Enable remote connections on an instance of SQL Server</span></span> 
 <span data-ttu-id="9ba49-182">원격 연결을 설정하려면 SQLCMD.exe를 로컬로 사용하고 Server Core 인스턴스에 대해 다음 문을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="9ba49-182">To enable remote connections, use SQLCMD.exe locally and execute the following statements against the Server Core instance:</span></span>  
  
-   `EXEC sys.sp_configure N'remote access', N'1'`  
  
     `GO`  
  
-   `RECONFIGURE WITH OVERRIDE`  
  
     `GO`  
  
### <a name="enable-and-start-the-sql-server-browser-service"></a><span data-ttu-id="9ba49-183">SQL  Server  Browser  서비스 설정 및 시작</span><span class="sxs-lookup"><span data-stu-id="9ba49-183">Enable and start the SQL Server Browser service</span></span>  
 <span data-ttu-id="9ba49-184">Browser 서비스는 기본적으로 해제되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9ba49-184">By default, the Browser service is disabled.</span></span>  <span data-ttu-id="9ba49-185">Server Core에서 실행 중인 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에서 해제된 경우 명령 프롬프트에서 다음 명령을 실행하여 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="9ba49-185">If it is disabled on an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] running on Server Core, run the following command from the command prompt to enable it:</span></span>  
  
 `sc config SQLBROWSER start= auto`  
  
 <span data-ttu-id="9ba49-186">설정한 후 명령 프롬프트에서 다음 명령을 실행하여 서비스를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="9ba49-186">After it is enabled, run the following command from the command prompt to start the service:</span></span>  
  
 `net start SQLBROWSER`  
  
### <a name="create-exceptions-in-windows-firewall"></a><span data-ttu-id="9ba49-187">Windows 방화벽에서 예외 생성</span><span class="sxs-lookup"><span data-stu-id="9ba49-187">Create exceptions in Windows Firewall</span></span>  
 <span data-ttu-id="9ba49-188">Windows 방화벽에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 액세스 관련 예외를 만들려면 [SQL Server 액세스를 허용하도록 Windows 방화벽 구성](../../sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md)에 지정된 단계를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9ba49-188">To create exceptions for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] access in Windows Firewall, follow the steps specified in [Configure the Windows Firewall to Allow SQL Server Access](../../sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md).</span></span>  
  
### <a name="enable-tcpip-on-an-instance-of-sql-server"></a><span data-ttu-id="9ba49-189">SQL Server 인스턴스에서 TCP/IP를 사용 하도록 설정</span><span class="sxs-lookup"><span data-stu-id="9ba49-189">Enable TCP/IP on an instance of SQL Server</span></span>
 <span data-ttu-id="9ba49-190">TCP/IP 프로토콜은 Server Core에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에 대해 Windows PowerShell을 통해 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9ba49-190">The TCP/IP protocol can be enabled through Windows PowerShell for an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on Server Core.</span></span> <span data-ttu-id="9ba49-191">다음 단계를 수행하세요.</span><span class="sxs-lookup"><span data-stu-id="9ba49-191">Follow these steps:</span></span>  
  
1.  <span data-ttu-id="9ba49-192">Windows Server 2008 R2 Server Core SP1을 실행하는 컴퓨터에서 작업 관리자를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="9ba49-192">On the computer that is running Windows Server 2008 R2 Server Core SP1, launch Task Manager.</span></span>  
  
2.  <span data-ttu-id="9ba49-193">**애플리케이션** 탭에서 **새 작업**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9ba49-193">On the **Applications** tab, click **New Task**.</span></span>  
  
3.  <span data-ttu-id="9ba49-194">**새 작업 만들기** 대화 상자에서 **열기** 필드에 **sqlps.exe** 를 입력하고 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9ba49-194">In the **Create New Task** dialog box, type **sqlps.exe** in the **Open** field and then click **OK**.</span></span> <span data-ttu-id="9ba49-195">이렇게 하면 **Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Powershell** 창이 열립니다.</span><span class="sxs-lookup"><span data-stu-id="9ba49-195">This opens the **Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Powershell** window.</span></span>  
  
4.  <span data-ttu-id="9ba49-196">**Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Powershell** 창에서 다음 스크립트를 실행하여 TCP/IP 프로토콜을 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="9ba49-196">In the **Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Powershell** window, run the following script to enable the TCP/IP protocol:</span></span>  
  
```powershell
$smo = 'Microsoft.SqlServer.Management.Smo.'  
$wmi = new-object ($smo + 'Wmi.ManagedComputer')  
# Enable the TCP protocol on the default instance.  If the instance is named, replace MSSQLSERVER with the instance name in the following line.  
$uri = "ManagedComputer[@Name='" + (get-item env:\computername).Value + "']/ServerInstance[@Name='MSSQLSERVER']/ServerProtocol[@Name='Tcp']"  
$Tcp = $wmi.GetSmoObject($uri)  
$Tcp.IsEnabled = $true  
$Tcp.Alter()  
$Tcp  
```  
  
##  <a name="sql-server-profiler"></a><span data-ttu-id="9ba49-197">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="9ba49-197">SQL Server Profiler</span></span>  
 <span data-ttu-id="9ba49-198">원격 컴퓨터에서 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 를 시작하고 파일 메뉴에서 새 추적을 선택하면 Server Core 시스템에 있는 연결할 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스를 지정할 수 있는 서버에 연결 대화 상자가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="9ba49-198">On a remote machine, start [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] and select New Trace from the File menu, the application displays a Connect to Server dialog box where you can specify the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance, residing on the Server Core machine, to which you want to connect.</span></span> <span data-ttu-id="9ba49-199">자세한 내용은 [Start SQL Server Profiler](../../tools/sql-server-profiler/start-sql-server-profiler.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9ba49-199">For more information, see [Start SQL Server Profiler](../../tools/sql-server-profiler/start-sql-server-profiler.md).</span></span>  
  
 <span data-ttu-id="9ba49-200">[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]실행에 필요한 권한에 대한 자세한 내용은 [SQL Server Profiler 실행에 필요한 권한](../../tools/sql-server-profiler/permissions-required-to-run-sql-server-profiler.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9ba49-200">For more information on the permissions required to run [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)], see [Permissions Required to Run SQL Server Profiler](../../tools/sql-server-profiler/permissions-required-to-run-sql-server-profiler.md).</span></span>  
  
 <span data-ttu-id="9ba49-201">[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]에 대한 자세한 내용은 [SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9ba49-201">For additional details about [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)], see [SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md).</span></span>  
  
##  <a name="sql-server-auditing"></a><span data-ttu-id="9ba49-202">SQL Server 감사</span><span class="sxs-lookup"><span data-stu-id="9ba49-202">SQL Server Auditing</span></span>  
 <span data-ttu-id="9ba49-203">원격으로 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)] 을 사용하여 감사를 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9ba49-203">You can use [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)] remotely to define an audit.</span></span> <span data-ttu-id="9ba49-204">감사가 생성되고 활성화되면 대상이 항목을 받습니다.</span><span class="sxs-lookup"><span data-stu-id="9ba49-204">After the audit is created and enabled, the target will receive entries.</span></span> <span data-ttu-id="9ba49-205">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 감사 만들기 및 관리에 대한 자세한 내용은 [SQL Server Audit&#40;데이터베이스 엔진&#41;](../../relational-databases/security/auditing/sql-server-audit-database-engine.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9ba49-205">For more information about creating and managing [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] audits, see [SQL Server Audit &#40;Database Engine&#41;](../../relational-databases/security/auditing/sql-server-audit-database-engine.md).</span></span>  
  
##  <a name="sql-servevr-command-prompt-utilities"></a><span data-ttu-id="9ba49-206">SQL server 명령 프롬프트 유틸리티</span><span class="sxs-lookup"><span data-stu-id="9ba49-206">SQL Servevr Command Prompt Utilities</span></span>  
 <span data-ttu-id="9ba49-207">Server Core 시스템에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 작업을 스크립팅할 수 있게 해 주는 다음과 같은 명령 프롬프트 유틸리티를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9ba49-207">You can use the following command prompt utilities that enable you to script [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] operations on a Server Core machine.</span></span> <span data-ttu-id="9ba49-208">다음 표에서는 Server Core용 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서 제공하는 명령 프롬프트 유틸리티를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="9ba49-208">The following table contains a list of command prompt utilities that ship with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] for Server Core:</span></span>  
  
|<span data-ttu-id="9ba49-209">**유틸리티**</span><span class="sxs-lookup"><span data-stu-id="9ba49-209">**Utility**</span></span>|<span data-ttu-id="9ba49-210">**설명**</span><span class="sxs-lookup"><span data-stu-id="9ba49-210">**Description**</span></span>|<span data-ttu-id="9ba49-211">**설치 위치**</span><span class="sxs-lookup"><span data-stu-id="9ba49-211">**Installed in**</span></span>|  
|-----------------|---------------------|----------------------|  
|[<span data-ttu-id="9ba49-212">bcp 유틸리티</span><span class="sxs-lookup"><span data-stu-id="9ba49-212">bcp Utility</span></span>](../../tools/bcp-utility.md)|<span data-ttu-id="9ba49-213">[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스와 사용자가 지정한 형식의 데이터 파일 간에 데이터를 복사하는 데 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="9ba49-213">Used to copy data between an instance of [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and a data file in a user-specified format.</span></span>|[!INCLUDE[ssInstallPathVar](../../includes/ssinstallpathvar-md.md)]<span data-ttu-id="9ba49-214">Tools\Binn</span><span class="sxs-lookup"><span data-stu-id="9ba49-214">Tools\Binn</span></span>|  
|[<span data-ttu-id="9ba49-215">dtexec 유틸리티</span><span class="sxs-lookup"><span data-stu-id="9ba49-215">dtexec Utility</span></span>](../../integration-services/packages/dtexec-utility.md)|<span data-ttu-id="9ba49-216">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 패키지를 구성 및 실행하는 데 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="9ba49-216">Used to configure and execute an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package.</span></span>|[!INCLUDE[ssInstallPathVar](../../includes/ssinstallpathvar-md.md)]<span data-ttu-id="9ba49-217">DTS\Binn</span><span class="sxs-lookup"><span data-stu-id="9ba49-217">DTS\Binn</span></span>|  
|[<span data-ttu-id="9ba49-218">dtutil 유틸리티</span><span class="sxs-lookup"><span data-stu-id="9ba49-218">dtutil Utility</span></span>](../../integration-services/dtutil-utility.md)|<span data-ttu-id="9ba49-219">SSIS 패키지를 관리하는 데 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="9ba49-219">Used to manage SSIS packages.</span></span>|[!INCLUDE[ssInstallPathVar](../../includes/ssinstallpathvar-md.md)]<span data-ttu-id="9ba49-220">DTS\Binn</span><span class="sxs-lookup"><span data-stu-id="9ba49-220">DTS\Binn</span></span>|  
|[<span data-ttu-id="9ba49-221">osql 유틸리티</span><span class="sxs-lookup"><span data-stu-id="9ba49-221">osql Utility</span></span>](../../tools/osql-utility.md)|<span data-ttu-id="9ba49-222">명령 프롬프트에서 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문, 시스템 프로시저 및 스크립트 파일을 입력할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9ba49-222">Allows you to enter [!INCLUDE[tsql](../../includes/tsql-md.md)] statements, system procedures, and script files at the command prompt.</span></span>|[!INCLUDE[ssInstallPathVar](../../includes/ssinstallpathvar-md.md)]<span data-ttu-id="9ba49-223">Tools\Binn</span><span class="sxs-lookup"><span data-stu-id="9ba49-223">Tools\Binn</span></span>|  
|[<span data-ttu-id="9ba49-224">sqlagent90 애플리케이션</span><span class="sxs-lookup"><span data-stu-id="9ba49-224">sqlagent90 Application</span></span>](../../tools/sqlagent90-application.md)|<span data-ttu-id="9ba49-225">명령 프롬프트에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트를 시작하는 데 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="9ba49-225">Used to start [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent from a command prompt.</span></span>|<span data-ttu-id="9ba49-226">\<drive>:\Program Files\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\\<*instance_name*>\MSSQL\Binn</span><span class="sxs-lookup"><span data-stu-id="9ba49-226">\<drive>:\Program Files\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\\<*instance_name*>\MSSQL\Binn</span></span>|  
|[<span data-ttu-id="9ba49-227">sqlcmd 유틸리티</span><span class="sxs-lookup"><span data-stu-id="9ba49-227">sqlcmd Utility</span></span>](../../tools/sqlcmd-utility.md)|<span data-ttu-id="9ba49-228">명령 프롬프트에서 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문, 시스템 프로시저 및 스크립트 파일을 입력할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9ba49-228">Allows you to enter [!INCLUDE[tsql](../../includes/tsql-md.md)] statements, system procedures, and script files at the command prompt.</span></span>|[!INCLUDE[ssInstallPathVar](../../includes/ssinstallpathvar-md.md)]<span data-ttu-id="9ba49-229">Tools\Binn</span><span class="sxs-lookup"><span data-stu-id="9ba49-229">Tools\Binn</span></span>|  
|[<span data-ttu-id="9ba49-230">SQLdiag 유틸리티</span><span class="sxs-lookup"><span data-stu-id="9ba49-230">SQLdiag Utility</span></span>](../../tools/sqldiag-utility.md)|<span data-ttu-id="9ba49-231">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 고객 서비스 지원 센터에 제공할 진단 정보를 수집하는 데 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="9ba49-231">Used to collect diagnostic information for [!INCLUDE[msCoName](../../includes/msconame-md.md)] Customer Service and Support.</span></span>|[!INCLUDE[ssInstallPathVar](../../includes/ssinstallpathvar-md.md)]<span data-ttu-id="9ba49-232">Tools\Binn</span><span class="sxs-lookup"><span data-stu-id="9ba49-232">Tools\Binn</span></span>|  
|[<span data-ttu-id="9ba49-233">sqlmaint 유틸리티</span><span class="sxs-lookup"><span data-stu-id="9ba49-233">sqlmaint Utility</span></span>](../../tools/sqlmaint-utility.md)|<span data-ttu-id="9ba49-234">이전 버전의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 만든 데이터베이스 유지 관리 계획을 실행하는 데 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="9ba49-234">Used to execute database maintenance plans created in previous versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>|<span data-ttu-id="9ba49-235">\<drive>: 파일 \ 파일 \\ [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \MSSQL12. MSSQLSERVER\MSSQL\Binn</span><span class="sxs-lookup"><span data-stu-id="9ba49-235">\<drive>:\Program Files\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\MSSQL12.MSSQLSERVER\MSSQL\Binn</span></span>|  
|[<span data-ttu-id="9ba49-236">sqlps 유틸리티</span><span class="sxs-lookup"><span data-stu-id="9ba49-236">sqlps Utility</span></span>](../../tools/sqlps-utility.md)|<span data-ttu-id="9ba49-237">PowerShell 명령 및 스크립트를 실행하는 데 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="9ba49-237">Used to run PowerShell commands and scripts.</span></span> <span data-ttu-id="9ba49-238">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell 공급자 및 cmdlet을 로드하고 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="9ba49-238">Loads and registers the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell provider and cmdlets.</span></span>|[!INCLUDE[ssInstallPathVar](../../includes/ssinstallpathvar-md.md)]<span data-ttu-id="9ba49-239">Tools\Binn</span><span class="sxs-lookup"><span data-stu-id="9ba49-239">Tools\Binn</span></span>|  
|[<span data-ttu-id="9ba49-240">sqlservr 애플리케이션</span><span class="sxs-lookup"><span data-stu-id="9ba49-240">sqlservr Application</span></span>](../../tools/sqlservr-application.md)|<span data-ttu-id="9ba49-241">문제 해결을 위해 명령 프롬프트에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 인스턴스를 시작 및 중지하는 데 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="9ba49-241">Used to start and stop an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)] from the command prompt for troubleshooting.</span></span>|<span data-ttu-id="9ba49-242">\<drive>: 파일 \ 파일 \\ [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \MSSQL12. MSSQLSERVER\MSSQL\Binn</span><span class="sxs-lookup"><span data-stu-id="9ba49-242">\<drive>:\Program Files\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\MSSQL12.MSSQLSERVER\MSSQL\Binn</span></span>|  
  
##  <a name="use-troubleshooting-tools"></a><span data-ttu-id="9ba49-243">문제 해결 도구 사용</span><span class="sxs-lookup"><span data-stu-id="9ba49-243">Use troubleshooting tools</span></span>  
 <span data-ttu-id="9ba49-244">[SQLdiag 유틸리티](../../tools/sqldiag-utility.md) 를 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 및 기타 서버 유형에서 로그 및 데이터 파일을 수집할 수 있으며 이러한 파일을 사용하여 지속적으로 서버를 모니터링하거나 특정 서버 문제를 해결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9ba49-244">You can use [SQLdiag Utility](../../tools/sqldiag-utility.md) to collect logs and data files from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and other types of servers, and use it to monitor your servers over time or troubleshoot specific problems with your servers.</span></span> <span data-ttu-id="9ba49-245">SQLdiag는 Microsoft 고객 지원 서비스에서 진단 정보를 빠르고 간편하게 수집할 수 있도록 지원하는 유틸리티입니다.</span><span class="sxs-lookup"><span data-stu-id="9ba49-245">SQLdiag is intended to expedite and simplify diagnostic information gathering for Microsoft Customer Support Services.</span></span>  
  
 <span data-ttu-id="9ba49-246">항목에 지정된 구문 [SQLdiag Utility](../../tools/sqldiag-utility.md)을(를) 사용하여 Server Core의 관리자 명령 프롬프트에서 유틸리티를 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9ba49-246">You can launch the utility on the administrator command prompt on the Server Core, using the syntax specified in the topic: [SQLdiag Utility](../../tools/sqldiag-utility.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ba49-247">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9ba49-247">See Also</span></span>  
 <span data-ttu-id="9ba49-248">[Server Core에 SQL Server 2014 설치](install-sql-server-on-server-core.md) </span><span class="sxs-lookup"><span data-stu-id="9ba49-248">[Install SQL Server 2014 on Server Core](install-sql-server-on-server-core.md) </span></span>  
 [<span data-ttu-id="9ba49-249">설치 방법 도움말 항목</span><span class="sxs-lookup"><span data-stu-id="9ba49-249">Installation How-to Topics</span></span>](../../sql-server/install/installation-how-to-topics.md)  
