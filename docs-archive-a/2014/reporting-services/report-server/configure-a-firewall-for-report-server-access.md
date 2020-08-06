---
title: 보고서 서버 액세스를 위한 방화벽 구성 | Microsoft Docs
ms.custom: ''
ms.date: 08/10/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- firewall systems [Reporting Services]
- configuring servers [Reporting Services]
ms.assetid: 04dae07a-a3a4-424c-9bcb-a8000e20dc93
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b578c980522d24f5a24a73fdfd080ec425335aac
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652604"
---
# <a name="configure-a-firewall-for-report-server-access"></a><span data-ttu-id="c14fa-102">보고서 서버에 액세스할 수 있도록 방화벽 구성</span><span class="sxs-lookup"><span data-stu-id="c14fa-102">Configure a Firewall for Report Server Access</span></span>
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="c14fa-103">보고서 서버 애플리케이션과 게시된 보고서는 IP 주소, 포트 및 가상 디렉터리를 지정하는 URL을 통해 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c14fa-103">Report server applications and published reports are accessed through URLs that specify an IP address, port, and virtual directory.</span></span> <span data-ttu-id="c14fa-104">Windows 방화벽을 켜면 보고서 서버에서 사용하도록 구성된 포트는 대부분 닫혀 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c14fa-104">If Windows Firewall is turned on, the port that the report server is configured to use is most likely closed.</span></span> <span data-ttu-id="c14fa-105">보고서를 요청한 후 빈 웹 페이지가 나타나거나 원격 클라이언트 컴퓨터에서 보고서 관리자를 열었을 때 빈 페이지가 나타나면 포트가 닫힌 것입니다.</span><span class="sxs-lookup"><span data-stu-id="c14fa-105">Indications that a port might be closed are the appearance of a blank Web page after requesting a report, or a blank page when you attempt to open Report Manager from a remote client computer.</span></span>  
  
 <span data-ttu-id="c14fa-106">이 경우 포트를 열려면 보고서 서버 컴퓨터에서 Windows 방화벽 유틸리티를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c14fa-106">To open a port, you must use the Windows Firewall utility on the report server computer.</span></span> <span data-ttu-id="c14fa-107">Reporting Services에서 자동으로 포트를 열지 않기 때문에 이 단계는 수동으로 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c14fa-107">Reporting Services will not open ports for you; you must perform this step manually.</span></span>  
  
 <span data-ttu-id="c14fa-108">기본적으로 보고서 서버는 포트 80에서 HTTP 요청을 수신합니다.</span><span class="sxs-lookup"><span data-stu-id="c14fa-108">By default, the report server listens for HTTP requests on port 80.</span></span> <span data-ttu-id="c14fa-109">따라서 아래 지침에는 이 포트를 지정하는 단계를 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="c14fa-109">As such, the following instructions include steps that specify that port.</span></span> <span data-ttu-id="c14fa-110">다른 포트를 사용하도록 보고서 서버 URL을 구성한 경우 아래 지침에 따라 해당 포트 번호를 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c14fa-110">If you configured the report server URLs to use a different port, you must specify that port number when following the instructions below.</span></span>  
  
 <span data-ttu-id="c14fa-111">외부 컴퓨터에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 관계형 데이터베이스에 액세스하거나 보고서 서버 데이터베이스가 외부 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에 있는 경우 외부 컴퓨터에서 포트 1433 및 1434를 열어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c14fa-111">If you are accessing [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] relational databases on external computers, or if the report server database is on an external [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance, you must open port 1433 and 1434 on the external computer.</span></span> <span data-ttu-id="c14fa-112">자세한 내용은 [온라인 설명서의](../../database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access.md) 데이터베이스 엔진 액세스에 대한 Windows 방화벽 구성 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c14fa-112">For more information, see [Configure a Windows Firewall for Database Engine Access](../../database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access.md) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span> <span data-ttu-id="c14fa-113">기본 Windows 방화벽 설정 방법과 [!INCLUDE[ssDE](../../includes/ssde-md.md)], [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]및 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]에 영향을 주는 TCP 포트에 대한 자세한 내용은 [온라인 설명서에서](../../sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md) SQL Server 액세스를 허용하도록 Windows 방화벽 구성 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c14fa-113">For more information about the default Windows firewall settings, and a description of the TCP ports that affect the [!INCLUDE[ssDE](../../includes/ssde-md.md)], [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], and [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], see [Configure the Windows Firewall to Allow SQL Server Access](../../sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="c14fa-114">사전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="c14fa-114">Prerequisites</span></span>  
 <span data-ttu-id="c14fa-115">이 지침에서는 사용자가 이미 서비스 계정을 구성했고 보고서 서버 데이터베이스를 만들었으며 보고서 서버 웹 서비스 및 보고서 관리자에 대한 URL을 구성했다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="c14fa-115">These instructions assume that you already configured the service account, created the report server database, and configured URLs for the Report Server Web service and Report Manager.</span></span> <span data-ttu-id="c14fa-116">자세한 내용은 [Reporting Services 기본 모드 보고서 서버 관리](manage-a-reporting-services-native-mode-report-server.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c14fa-116">For more information, see [Manage a Reporting Services Native Mode Report Server](manage-a-reporting-services-native-mode-report-server.md).</span></span>  
  
 <span data-ttu-id="c14fa-117">로컬 웹 브라우저에서 로컬 보고서 서버 인스턴스에 연결하여 보고서 서버에 액세스할 수 있는지도 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c14fa-117">You should also have verified that the report server is accessible over a local Web browser connection to the local report server instance.</span></span> <span data-ttu-id="c14fa-118">이 단계에서는 사용 가능한 설치가 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="c14fa-118">This step establishes that you have a working installation.</span></span> <span data-ttu-id="c14fa-119">포트를 열기 전에 설치가 올바르게 구성되어 있는지 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c14fa-119">You should verify that the installation is configured correctly before you begin opening ports.</span></span> <span data-ttu-id="c14fa-120">Windows Server에서 이 단계를 완료하려면 보고서 서버 사이트를 신뢰할 수 있는 사이트에 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c14fa-120">To complete this step on  Windows Server, you must have also added the report server site to Trusted Sites.</span></span> <span data-ttu-id="c14fa-121">자세한 내용은 [로컬 관리에 대해 기본 모드 보고서 서버 구성&#40;SSRS&#41;](configure-a-native-mode-report-server-for-local-administration-ssrs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c14fa-121">For more information, see [Configure a Native Mode Report Server for Local Administration &#40;SSRS&#41;](configure-a-native-mode-report-server-for-local-administration-ssrs.md).</span></span>  
  
## <a name="opening-ports-in-windows-firewall"></a><span data-ttu-id="c14fa-122">Windows 방화벽에서 포트 열기</span><span class="sxs-lookup"><span data-stu-id="c14fa-122">Opening Ports in Windows Firewall</span></span>  
 <span data-ttu-id="c14fa-123">Windows 방화벽 버전마다 다른 지침이 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="c14fa-123">There are separate instructions for different versions of Windows Firewall.</span></span>  
  
#### <a name="to-open-port-80-on-windows-7-windows-server-2008-r2-windows-server-2012-and-2012-r2"></a><span data-ttu-id="c14fa-124">Windows 7, Windows Server 2008 R2, Windows Server 2012 및 2012 R2에서 포트 80을 열려면</span><span class="sxs-lookup"><span data-stu-id="c14fa-124">To open port 80 on Windows 7, Windows Server 2008 R2, Windows Server 2012 and 2012 R2</span></span>  
  
1.  <span data-ttu-id="c14fa-125">**시작** 메뉴에서 **제어판**을 클릭한 다음 **시스템 및 보안**, **Windows 방화벽**을 차례로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c14fa-125">From the **Start** menu, click **Control Panel**, click **System and Security**, and then click **Windows Firewall**.</span></span> <span data-ttu-id="c14fa-126">제어판이 '범주' 보기로 구성되지 않은 경우에는 **Windows 방화벽**을 바로 선택하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c14fa-126">Control Panel is not configured for 'Category' view, you only need to select **Windows Firewall.**</span></span>  
  
2.  <span data-ttu-id="c14fa-127">**고급 설정**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c14fa-127">Click **Advanced Settings**.</span></span>  
  
3.  <span data-ttu-id="c14fa-128">**인바운드 규칙**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c14fa-128">Click **Inbound Rules.**</span></span>  
  
4.  <span data-ttu-id="c14fa-129">**동작** 창의 **새 규칙** 을 클릭합니다 **.**</span><span class="sxs-lookup"><span data-stu-id="c14fa-129">Click **New Rule** in the **Actions** window **.**</span></span>  
  
5.  <span data-ttu-id="c14fa-130">**포트** 의 **규칙 종류**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c14fa-130">Click **Rule Type** of **Port.**</span></span>  
  
6.  <span data-ttu-id="c14fa-131">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c14fa-131">Click **Next**.</span></span>  
  
7.  <span data-ttu-id="c14fa-132">**프로토콜 및 포트** 페이지에서 **TCP**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c14fa-132">On the **Protocol and Ports** page click **TCP**.</span></span>  
  
8.  <span data-ttu-id="c14fa-133">**특정 로컬 포트** 를 선택하고 값으로 **80**을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="c14fa-133">Select **Specific Local Ports** and type a value of **80**.</span></span>  
  
9. <span data-ttu-id="c14fa-134">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c14fa-134">Click **Next**.</span></span>  
  
10. <span data-ttu-id="c14fa-135">**동작** 페이지에서 **연결 허용**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c14fa-135">On the **Action** page click **Allow the connection**.</span></span>  
  
11. <span data-ttu-id="c14fa-136">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c14fa-136">Click **Next**.</span></span>  
  
12. <span data-ttu-id="c14fa-137">**프로필** 페이지에서 사용자 환경에 적합한 옵션을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c14fa-137">On the **Profile** page click the appropriate options for your environment.</span></span>  
  
13. <span data-ttu-id="c14fa-138">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c14fa-138">Click **Next**.</span></span>  
  
14. <span data-ttu-id="c14fa-139">**이름** 페이지에서 이름으로**ReportServer (TCP on port 80)** 를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="c14fa-139">On the **Name** page enter a name of**ReportServer (TCP on port 80)**</span></span>  
  
15. <span data-ttu-id="c14fa-140">**Finish**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c14fa-140">Click **Finish**.</span></span>  
  
16. <span data-ttu-id="c14fa-141">컴퓨터를 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="c14fa-141">Restart the computer.</span></span>  
  
#### <a name="to-open-port-80-on-windows-vista-or-windows-server-2008"></a><span data-ttu-id="c14fa-142">Windows Vista 또는 Windows Server 2008에서 포트 80을 열려면</span><span class="sxs-lookup"><span data-stu-id="c14fa-142">To open port 80 on Windows Vista or Windows Server 2008</span></span>  
  
1.  <span data-ttu-id="c14fa-143">**시작** 메뉴에서 **제어판**을 클릭 하 고 **보안**을 클릭 한 다음 **Windows 방화벽**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c14fa-143">From the **Start** menu, click **Control Panel**, click **Security**, and then click **Windows Firewall**.</span></span>  
  
2.  <span data-ttu-id="c14fa-144">**Windows 방화벽을 통한 프로그램 실행 허용**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c14fa-144">Click **Allow a program through Windows Firewall**.</span></span>  
  
3.  <span data-ttu-id="c14fa-145">**계속**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c14fa-145">Click **Continue**.</span></span>  
  
4.  <span data-ttu-id="c14fa-146">예외 탭에서 **포트 추가**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c14fa-146">On the Exceptions tab, click **Add Port**.</span></span>  
  
5.  <span data-ttu-id="c14fa-147">이름에 **ReportServer (TCP on port 80)** 을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="c14fa-147">In Name, type **ReportServer (TCP on port 80)**.</span></span>  
  
6.  <span data-ttu-id="c14fa-148">포트 번호에 **80**을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="c14fa-148">In Port number, type **80**.</span></span>  
  
7.  <span data-ttu-id="c14fa-149">**TCP** 가 선택 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="c14fa-149">Verify that **TCP** is selected.</span></span>  
  
8.  <span data-ttu-id="c14fa-150">**범위 변경**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c14fa-150">Click **Change Scope**.</span></span>  
  
9. <span data-ttu-id="c14fa-151">**내 네트워크 (서브넷)만**을 클릭 한 다음 **확인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c14fa-151">Click **My network (subnet) only**, and then click **OK**.</span></span>  
  
10. <span data-ttu-id="c14fa-152">**확인** 을 클릭하여 대화 상자를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="c14fa-152">Click **OK** to close the dialog box.</span></span>  
  
11. <span data-ttu-id="c14fa-153">컴퓨터를 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="c14fa-153">Restart the computer.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="c14fa-154">다음 단계</span><span class="sxs-lookup"><span data-stu-id="c14fa-154">Next Steps</span></span>  
 <span data-ttu-id="c14fa-155">포트를 연 다음 원격 사용자가 이 포트에서 보고서 서버에 액세스할 수 있는지 확인하기 전에 홈 및 사이트 수준에서 역할 할당을 통해 사용자에게 보고서 서버에 대한 액세스 권한을 부여해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c14fa-155">After you open the port and before you confirm whether remote users can access the report server on the port that you open, you must grant user access to the report server through role assignments on Home and at the site level.</span></span> <span data-ttu-id="c14fa-156">사용자에게 충분한 권한이 없는 경우 포트는 제대로 열리지만 보고서 서버에는 연결할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c14fa-156">You can open a port correctly and still have report server connections fail if users do not have sufficient permissions.</span></span> <span data-ttu-id="c14fa-157">자세한 내용은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 온라인 설명서에서 [사용자에게 보고서 서버에 대한 액세스 권한 부여&#40;보고서 관리자&#41;](../security/grant-user-access-to-a-report-server.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c14fa-157">For more information, see [Grant User Access to a Report Server &#40;Report Manager&#41;](../security/grant-user-access-to-a-report-server.md) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
 <span data-ttu-id="c14fa-158">다른 컴퓨터에서 보고서 관리자를 시작하여 포트가 제대로 열리는지 확인할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c14fa-158">You can also verify that the port is opened correctly by starting Report Manager on a different computer.</span></span> <span data-ttu-id="c14fa-159">자세한 내용은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 온라인 설명서에서 [보고서 관리자&#40;SSRS 기본 모드&#41;](../report-manager-ssrs-native-mode.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c14fa-159">For more information, see [Report Manager  &#40;SSRS Native Mode&#41;](../report-manager-ssrs-native-mode.md) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c14fa-160">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c14fa-160">See Also</span></span>  
 <span data-ttu-id="c14fa-161">[보고서 서버 서비스 계정 구성&#40;SSRS 구성 관리자&#41;](../install-windows/configure-the-report-server-service-account-ssrs-configuration-manager.md) </span><span class="sxs-lookup"><span data-stu-id="c14fa-161">[Configure the Report Server Service Account &#40;SSRS Configuration Manager&#41;](../install-windows/configure-the-report-server-service-account-ssrs-configuration-manager.md) </span></span>  
 <span data-ttu-id="c14fa-162">[보고서 서버 URL 구성&#40;SSRS 구성 관리자&#41;](../install-windows/configure-report-server-urls-ssrs-configuration-manager.md) </span><span class="sxs-lookup"><span data-stu-id="c14fa-162">[Configure Report Server URLs  &#40;SSRS Configuration Manager&#41;](../install-windows/configure-report-server-urls-ssrs-configuration-manager.md) </span></span>  
 <span data-ttu-id="c14fa-163">[SSRS Configuration Manager &#40;보고서 서버 데이터베이스를 만듭니다&#41;](../../sql-server/install/create-a-report-server-database-ssrs-configuration-manager.md) </span><span class="sxs-lookup"><span data-stu-id="c14fa-163">[Create a Report Server Database  &#40;SSRS Configuration Manager&#41;](../../sql-server/install/create-a-report-server-database-ssrs-configuration-manager.md) </span></span>  
 <span data-ttu-id="c14fa-164">[보고서 서버 서비스 계정 구성&#40;SSRS 구성 관리자&#41;](../install-windows/configure-the-report-server-service-account-ssrs-configuration-manager.md) </span><span class="sxs-lookup"><span data-stu-id="c14fa-164">[Configure the Report Server Service Account &#40;SSRS Configuration Manager&#41;](../install-windows/configure-the-report-server-service-account-ssrs-configuration-manager.md) </span></span>  
 [<span data-ttu-id="c14fa-165">Reporting Services 기본 모드 보고서 서버 관리</span><span class="sxs-lookup"><span data-stu-id="c14fa-165">Manage a Reporting Services Native Mode Report Server</span></span>](manage-a-reporting-services-native-mode-report-server.md)  
  
  
