---
title: 로컬 관리에 대해 기본 모드 보고서 서버 구성(SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- UAC
- installing Reporting Services
- Windows Vista
- Localhost
- windows server 2008
- Vista
ms.assetid: 312c6bb8-b3f7-4142-a55f-c69ee15bbf52
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: ad53f293ef825a382d9e39b58527a36ef291687a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652603"
---
# <a name="configure-a-native-mode-report-server-for-local-administration-ssrs"></a><span data-ttu-id="da79f-102">로컬 관리에 대해 기본 모드 보고서 서버 구성(SSRS)</span><span class="sxs-lookup"><span data-stu-id="da79f-102">Configure a Native Mode Report Server for Local Administration (SSRS)</span></span>
  <span data-ttu-id="da79f-103">보고서 서버 인스턴스를 로컬로 관리하려는 경우 다음 운영 체제 중 하나에 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 보고서 서버를 배포하려면 추가 구성 단계가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="da79f-103">Deploying a [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] report server on one of the following operating systems requires more configuration steps if you want to administer the report server instance locally.</span></span> <span data-ttu-id="da79f-104">이 항목에서는 로컬 관리를 위한 보고서 서버를 구성하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="da79f-104">This topic explains how to configure the report server for local administration.</span></span> <span data-ttu-id="da79f-105">보고서 서버를 아직 설치 하거나 구성 하지 않은 경우 설치 [마법사에서 SQL Server 2014 설치 &#40;설정&#41;](../../database-engine/install-windows/install-sql-server-from-the-installation-wizard-setup.md) 하 고 [Reporting Services 기본 모드 보고서 서버 관리](manage-a-reporting-services-native-mode-report-server.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="da79f-105">If you have not yet installed or configured the report server, see [Install SQL Server 2014 from the Installation Wizard &#40;Setup&#41;](../../database-engine/install-windows/install-sql-server-from-the-installation-wizard-setup.md) and [Manage a Reporting Services Native Mode Report Server](manage-a-reporting-services-native-mode-report-server.md).</span></span>  
  
||  
|-|  
|<span data-ttu-id="da79f-106">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 기본 모드</span><span class="sxs-lookup"><span data-stu-id="da79f-106">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Native mode</span></span>|  
  
-   [!INCLUDE[winblue_server_2](../../includes/winblue-server-2-md.md)]  
  
-   [!INCLUDE[winblue_client_2](../../includes/winblue-client-2-md.md)]  
  
-   [!INCLUDE[win8](../../includes/win8-md.md)]  
  
-   [!INCLUDE[win8srv](../../includes/win8srv-md.md)]  
  
-   [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)]  
  
-   [!INCLUDE[win7](../../includes/win7-md.md)]  
  
-   [!INCLUDE[firstref_longhorn](../../includes/firstref-longhorn-md.md)]  
  
 <span data-ttu-id="da79f-107">위에 나와 있는 운영 체제는 권한을 제한하므로 로컬 Administrators 그룹의 멤버는 대부분의 애플리케이션을 표준 사용자 계정을 사용할 때처럼 실행하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="da79f-107">Because the noted operating systems limit permissions, members of the local Administrators group run most applications as if they are using the Standard User account.</span></span>  
  
 <span data-ttu-id="da79f-108">이를 통해 전반적인 시스템 보안이 개선되지만 Reporting Services에서 로컬 관리자용으로 만드는 미리 정의된 기본 제공 역할 할당은 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="da79f-108">While this practice improves the overall security of your system, it prevents you from using the predefined, built-in role assignments that Reporting Services creates for local administrators.</span></span>  
  
-   [<span data-ttu-id="da79f-109">구성 변경 개요</span><span class="sxs-lookup"><span data-stu-id="da79f-109">Overview of Configuration Changes</span></span>](#bkmk_configuraiton_overview)  
  
-   [<span data-ttu-id="da79f-110">로컬 보고서 서버 및 보고서 관리자 관리를 구성하려면</span><span class="sxs-lookup"><span data-stu-id="da79f-110">To Configure Local Report Server and Report Manager Administration</span></span>](#bkmk_configure_local_server)  
  
-   [<span data-ttu-id="da79f-111">로컬 보고서 서버 관리에 대해 SSMS(SQL Server Management Studio)를 구성하려면</span><span class="sxs-lookup"><span data-stu-id="da79f-111">To Configure SQL Server Management Studio (SSMS) for local report server administration</span></span>](#bkmk_configure_ssms)  
  
-   [<span data-ttu-id="da79f-112">로컬 보고서 서버에 게시하도록 SSDT(SQL Server Data Tools) BI를 구성하려면</span><span class="sxs-lookup"><span data-stu-id="da79f-112">To Configure SQL Server Data Tools BI (SSDT) to Publish to a Local Report Server</span></span>](#bkmk_configure_ssdt)  
  
-   [<span data-ttu-id="da79f-113">추가 정보</span><span class="sxs-lookup"><span data-stu-id="da79f-113">Additional Information</span></span>](#bkmk_addiitonal_informaiton)  
  
##  <a name="overview-of-configuration-changes"></a><a name="bkmk_configuraiton_overview"></a><span data-ttu-id="da79f-114">구성 변경 개요</span><span class="sxs-lookup"><span data-stu-id="da79f-114">Overview of Configuration Changes</span></span>  
 <span data-ttu-id="da79f-115">다음 구성 변경은 표준 사용자 권한을 사용하여 보고서 서버 내용 및 작업을 관리할 수 있도록 서버를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="da79f-115">The following configuration changes configure the server so that you can use standard user permissions to manage report server content and operations:</span></span>  
  
-   <span data-ttu-id="da79f-116">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] URL을 신뢰할 수 있는 사이트에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="da79f-116">Add [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] URLs to trusted sites.</span></span> <span data-ttu-id="da79f-117">기본적으로 위에 나와 있는 운영 체제에서 실행되는 Internet Explorer는 **보호 모드**로 실행됩니다. 이 모드는 같은 컴퓨터에서 실행되는 높은 수준의 프로세스에 브라우저 요청이 도달하지 못하도록 차단하는 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="da79f-117">By default, Internet Explorer running on the listed operating systems runs in **Protected Mode**, a feature that blocks browser requests from reaching high-level processes that run on the same computer.</span></span> <span data-ttu-id="da79f-118">이 URL을 신뢰할 수 있는 사이트에 추가하면 보고서 서버 애플리케이션에 대한 보호 모드를 해제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="da79f-118">You can disable protected mode for the report server applications by adding them as Trusted Sites.</span></span>  
  
-   <span data-ttu-id="da79f-119">Internet Explorer에서 **관리자 권한으로 실행** 기능을 사용하지 않고도 보고서 서버 관리자에게 내용 및 작업을 관리하는 권한을 부여하는 역할 할당을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="da79f-119">Create role assignments that grant you, the report server administrator, permission to manage content and operations without having to use the **Run as administrator** feature on Internet Explorer.</span></span> <span data-ttu-id="da79f-120">Windows 사용자 계정에 대한 역할 할당을 만들면 Reporting Services에서 만드는 미리 정의된 기본 제공 역할 할당을 대체하는 명시적인 역할 할당을 통해 내용 관리자 및 시스템 관리자 권한으로 보고서 서버에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="da79f-120">By creating role assignments for your Windows user account, you gain access to a report server with Content Manager and System Administrator permissions through explicit role assignments that replace the predefined, built-in role assignments that Reporting Services creates.</span></span>  
  
##  <a name="to-configure-local-report-server-and-report-manager-administration"></a><a name="bkmk_configure_local_server"></a><span data-ttu-id="da79f-121">로컬 보고서 서버 및 보고서 관리자 관리를 구성 하려면</span><span class="sxs-lookup"><span data-stu-id="da79f-121">To Configure Local Report Server and Report Manager Administration</span></span>  
 <span data-ttu-id="da79f-122">로컬 보고서 서버로 이동하는 동안 다음과 유사한 오류가 나타나면 이 섹션의 구성 단계를 완료합니다.</span><span class="sxs-lookup"><span data-stu-id="da79f-122">Complete the configuration steps in this section if you are browsing to a local report server and you see errors similar to the following:</span></span>  
  
-   <span data-ttu-id="da79f-123">사용자 `'Domain\[user name]`'에게 필요한 권한이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="da79f-123">User `'Domain\[user name]`' does not have required permissions.</span></span> <span data-ttu-id="da79f-124">충분한 권한이 부여되고 Windows UAC(사용자 계정 컨트롤) 제한이 해결되었는지 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="da79f-124">Verify that sufficient permissions have been granted and Windows User Account Control (UAC) restrictions have been addressed.</span></span>  
  
###  <a name="trusted-site-settings-in-the-browser"></a><a name="bkmk_site_settings"></a><span data-ttu-id="da79f-125">브라우저의 신뢰할 수 있는 사이트 설정</span><span class="sxs-lookup"><span data-stu-id="da79f-125">Trusted Site Settings in the Browser</span></span>  
  
1.  <span data-ttu-id="da79f-126">관리자 권한으로 실행 권한을 사용하여 브라우저 창을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="da79f-126">Open a browser window with Run as administrator permissions.</span></span> <span data-ttu-id="da79f-127">**시작** 메뉴에서 **모든 프로그램**을 클릭하고 **Internet Explorer**를 마우스 오른쪽 단추로 클릭한 다음 **관리자 권한으로 실행**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="da79f-127">From the **Start** menu, click **All Programs**, right-click **Internet Explorer**, and select **Run as administrator**.</span></span>  
  
2.  <span data-ttu-id="da79f-128">**허용** 을 클릭하여 계속합니다.</span><span class="sxs-lookup"><span data-stu-id="da79f-128">Click **Allow** to continue.</span></span>  
  
3.  <span data-ttu-id="da79f-129">URL 주소에 보고서 관리자 URL을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="da79f-129">In the URL address, enter the Report Manager URL.</span></span> <span data-ttu-id="da79f-130">자세한 내용은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 온라인 설명서에서 [보고서 관리자&#40;SSRS 기본 모드&#41;](../report-manager-ssrs-native-mode.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="da79f-130">For instructions, see [Report Manager  &#40;SSRS Native Mode&#41;](../report-manager-ssrs-native-mode.md) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
4.  <span data-ttu-id="da79f-131">**도구**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="da79f-131">Click **Tools**.</span></span>  
  
5.  <span data-ttu-id="da79f-132">**인터넷 옵션**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="da79f-132">Click **Internet Options**.</span></span>  
  
6.  <span data-ttu-id="da79f-133">**보안**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="da79f-133">Click **Security**.</span></span>  
  
7.  <span data-ttu-id="da79f-134">**신뢰할 수 있는 사이트**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="da79f-134">Click **Trusted Sites**.</span></span>  
  
8.  <span data-ttu-id="da79f-135">**사이트**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="da79f-135">Click **Sites**.</span></span>  
  
9. <span data-ttu-id="da79f-136">`http://<your-server-name>`를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="da79f-136">Add `http://<your-server-name>`.</span></span>  
  
10. <span data-ttu-id="da79f-137">기본 사이트에 HTTPS를 사용하지 않으면 **이 영역이 있는 모든 사이트에 대해 서버 확인(https:) 필요** 확인란의 선택을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="da79f-137">Clear the check box **Require server certification (https:) for all sites in this zone** if you are not using HTTPS for the default site.</span></span>  
  
11. <span data-ttu-id="da79f-138">**추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="da79f-138">Click **Add**.</span></span>  
  
12. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
###  <a name="report-manager-folder-settings"></a><a name="bkmk_configure_folder_settings"></a> <span data-ttu-id="da79f-139">보고서 관리자 폴더 설정</span><span class="sxs-lookup"><span data-stu-id="da79f-139">Report Manager Folder Settings</span></span>  
  
1.  <span data-ttu-id="da79f-140">보고서 관리자의 홈 페이지에서 **폴더 설정**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="da79f-140">In Report Manager, on the Home page, click **Folder Settings**.</span></span>  
  
2.  <span data-ttu-id="da79f-141">폴더 설정 페이지에서 **보안**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="da79f-141">In the Folder Settings page, click **Security**.</span></span>  
  
3.  <span data-ttu-id="da79f-142">**새 역할 할당**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="da79f-142">Click **New Role Assignment**.</span></span>  
  
4.  <span data-ttu-id="da79f-143">**그룹 또는 사용자 이름** 필드에 `<domain>\<user>`형식으로 Windows 사용자 계정을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="da79f-143">In the **Group or user name** field, type your Windows user account in this format: `<domain>\<user>`.</span></span>  
  
5.  <span data-ttu-id="da79f-144">**내용 관리자**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="da79f-144">Select **Content Manager**.</span></span>  
  
6.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
###  <a name="report-manager-site-settings"></a><a name="bkmk_configure_site_settings"></a> <span data-ttu-id="da79f-145">보고서 관리자 사이트 설정</span><span class="sxs-lookup"><span data-stu-id="da79f-145">Report Manager Site Settings</span></span>  
  
1.  <span data-ttu-id="da79f-146">관리자 권한을 가진 브라우저를 열고 보고서 관리자 `http://<server name>/reports`로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="da79f-146">Open your browser with administrative privileges and browse to report manager, `http://<server name>/reports`.</span></span>  
  
2.  <span data-ttu-id="da79f-147">홈 페이지의 위쪽 모퉁이에 있는 **사이트 설정** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="da79f-147">Click **Site Settings** in the upper corner of the Home page.</span></span>  
  
    > [!TIP]  
    >  <span data-ttu-id="da79f-148">**참고:\*\*\*\*사이트 설정** 옵션이 표시되지 않으면 브라우저를 닫았다가 다시 열고 관리자 권한으로 보고서 관리자로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="da79f-148">**Note:** If you do not see the **Site Settings** option, close and reopen your browser and browse to report manager with administrative privileges.</span></span>  
  
3.  <span data-ttu-id="da79f-149">**보안**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="da79f-149">Click **security**.</span></span>  
  
4.  <span data-ttu-id="da79f-150">**새 역할 할당**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="da79f-150">Click **New Role Assignment**.</span></span>  
  
5.  <span data-ttu-id="da79f-151">**그룹 또는 사용자 이름** 필드에 `<domain>\<user>`형식으로 Windows 사용자 계정을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="da79f-151">In the **Group or user name** field, type your Windows user account in this format: `<domain>\<user>`.</span></span>  
  
6.  <span data-ttu-id="da79f-152">**시스템 관리자**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="da79f-152">Select **System Administrator**.</span></span>  
  
7.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
8.  <span data-ttu-id="da79f-153">보고서 관리자를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="da79f-153">Close Report Manager.</span></span>  
  
9. <span data-ttu-id="da79f-154">**관리자 권한으로 실행**을 사용하지 않고 Internet Explorer에서 보고서 관리자를 다시 엽니다.</span><span class="sxs-lookup"><span data-stu-id="da79f-154">Re-open Report Manager in Internet Explorer, without using **Run as administrator**.</span></span>  
  
##  <a name="to-configure-sql-server-management-studio-ssms-for-local-report-server-administration"></a><a name="bkmk_configure_ssms"></a><span data-ttu-id="da79f-155">로컬 보고서 서버 관리를 위해 SSMS (SQL Server Management Studio)를 구성 하려면</span><span class="sxs-lookup"><span data-stu-id="da79f-155">To Configure SQL Server Management Studio (SSMS) for local report server administration</span></span>  
 <span data-ttu-id="da79f-156">기본적으로 관리자 권한으로 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 를 시작해야 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 에서 사용할 수 있는 모든 보고서 서버 속성에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="da79f-156">By default, you cannot access all of the report server properties available in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] unless you start [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] with administrative privileges.</span></span>  
  
 <span data-ttu-id="da79f-157">**매번 승격된 권한으로 SSDT를 시작할 필요가 없도록 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]** 를 시작할 필요가 없도록 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 역할 속성 및 역할 할당을 구성하려면</span><span class="sxs-lookup"><span data-stu-id="da79f-157">**To configure [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]** role properties and role assignments so you do not need to start [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] with elevated permissions each time:</span></span>  
  
-   <span data-ttu-id="da79f-158">**시작** 메뉴에서 **모든 프로그램**, **SQL Server 2014**를 차례로 클릭하고 **[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]** 를 마우스 오른쪽 단추로 클릭한 다음 **관리자 권한으로 실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="da79f-158">From the **Start** menu, click **All Programs**, click **SQL Server 2014**, right-click **[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]**, and then click **Run as administrator**.</span></span>  
  
-   <span data-ttu-id="da79f-159">로컬 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 서버에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="da79f-159">Connect to your local [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] server.</span></span>  
  
-   <span data-ttu-id="da79f-160">**보안** 노드에서 **시스템 역할**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="da79f-160">In the **Security** node, click **System Roles**.</span></span>  
  
-   <span data-ttu-id="da79f-161">**시스템 관리자** 를 마우스 오른쪽 단추로 클릭하고 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="da79f-161">Right-click **System Administrator** and then click **Properties**.</span></span>  
  
-   <span data-ttu-id="da79f-162">**시스템 역할 속성** 페이지에서 **보고서 서버 속성 보기**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="da79f-162">In the **System Role Properties** page, select **View report server properties**.</span></span> <span data-ttu-id="da79f-163">시스템 관리자 역할의 멤버와 연결할 다른 속성을 모두 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="da79f-163">Select any other properties you want associated with members of the system administrators role.</span></span>  
  
-   <span data-ttu-id="da79f-164">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="da79f-164">Click **OK**.</span></span>  
  
-   <span data-ttu-id="da79f-165">닫기 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]</span><span class="sxs-lookup"><span data-stu-id="da79f-165">Close [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]</span></span>  
  
-   <span data-ttu-id="da79f-166">사용자를 "시스템 관리자" 시스템 역할에 추가하려면 이 항목의 앞부분에 나오는 [보고서 관리자 사이트 설정](#bkmk_configure_site_settings) 섹션을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="da79f-166">To add a user to the system role "system administrator", see the [Report Manager Site Settings](#bkmk_configure_site_settings) section earlier in this topic.</span></span>  
  
 <span data-ttu-id="da79f-167">이제 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 를 열 때 **관리자 권한으로 실행** 을 명시적으로 선택하지 않아도 보고서 서버 속성에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="da79f-167">Now when you open [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] and do not explicitly select **Run as administrator** you have access to the report server properties.</span></span>  
  
##  <a name="to-configure-sql-server-data-tools-bi-ssdt-to-publish-to-a-local-report-server"></a><a name="bkmk_configure_ssdt"></a><span data-ttu-id="da79f-168">로컬 보고서 서버에 게시 하도록 SSDT (SQL Server Data Tools BI)를 구성 하려면</span><span class="sxs-lookup"><span data-stu-id="da79f-168">To Configure SQL Server Data Tools BI (SSDT) to Publish to a Local Report Server</span></span>  
 <span data-ttu-id="da79f-169">이 항목의 첫 번째 섹션에 나와 있는 운영 체제 중 하나에 [!INCLUDE[SSDTDev11](../../includes/ssdtdev11-md.md)] 를 설치했고 SSDT가 로컬 기본 모드 보고서 서버와 상호 작용하도록 하려는 경우 승격된 권한으로 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 를 열지 않거나 Reporting Services 역할을 구성하지 않으면 권한 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="da79f-169">If you installed [!INCLUDE[SSDTDev11](../../includes/ssdtdev11-md.md)] on one of the operating systems listed in the first section of this topic, and you want SSDT to interact with a local Native mode report server, you will experiences permission errors unless you open [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] with elevated permissions or configure reporting services roles.</span></span> <span data-ttu-id="da79f-170">예를 들어 충분한 권한이 없으면 다음과 유사한 문제가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="da79f-170">For example, if you do not have sufficient permissions, you experience issues similar to the following:</span></span>  
  
-   <span data-ttu-id="da79f-171">보고서 항목을 로컬 보고서 서버에 배포하려고 하면 **오류 목록** 창에 다음과 유사한 오류 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="da79f-171">When you attempt to deploy report items to the local report server, you see an error message similar to the following in the **Error List** window:</span></span>  
  
    -   <span data-ttu-id="da79f-172">‘Domain\\<user name\>’ 사용자에게 부여된 권한으로는 이 작업을 수행할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="da79f-172">The permissions granted to user 'Domain\\<user name\>' are insufficient for performing this operation.</span></span>  
  
 <span data-ttu-id="da79f-173">**SSDT를 열 때마다 승격된 권한으로 실행하려면**</span><span class="sxs-lookup"><span data-stu-id="da79f-173">**To run with elevated permissions each time you open SSDT:**</span></span>  
  
1.  <span data-ttu-id="da79f-174">시작 화면에서를 입력 `sql server` 하 고 **Visual Studio SQL Server Data Tools를**마우스 오른쪽 단추로 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="da79f-174">From the start screen, type `sql server` and then right-click **SQL Server Data Tools for Visual Studio**.</span></span> <span data-ttu-id="da79f-175">**관리자 권한으로 실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="da79f-175">Click **Run as administrator**</span></span>  
  
     <span data-ttu-id="da79f-176">**또는**이전 운영 체제에서 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="da79f-176">**Or**, on older operating systems:</span></span>  
  
     <span data-ttu-id="da79f-177">**시작** 메뉴에서 **모든 프로그램**, **SQL Server 2014**를 차례로 클릭하고 **SQL Server Data Tools**를 마우스 오른쪽 단추로 클릭한 다음 **다음 계정으로 실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="da79f-177">From the **Start** menu, click **All Programs**, click **SQL Server 2014**, right-click **SQL Server Data Tools**, and then click **Run as administrator**.</span></span>  
  
2.  <span data-ttu-id="da79f-178">**계속**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="da79f-178">Click **Continue**.</span></span>  
  
3.  <span data-ttu-id="da79f-179">**프로그램 실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="da79f-179">Click **Run Program**.</span></span>  
  
 <span data-ttu-id="da79f-180">이제 로컬 보고서 서버에 보고서 및 기타 항목을 배포할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="da79f-180">You should now be able to deploy reports and other items to a local report server.</span></span>  
  
 <span data-ttu-id="da79f-181">**매번 승격된 권한으로 SSDT를 시작할 필요가 없도록 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 역할 할당을 구성하려면**</span><span class="sxs-lookup"><span data-stu-id="da79f-181">**To configure [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] role assignments so you do not need to start SSDT with elevated permissions each time:**</span></span>  
  
-   <span data-ttu-id="da79f-182">이 항목의 앞부분에 있는 [보고서 관리자 폴더 설정](#bkmk_configure_folder_settings) 및 [보고서 관리자 사이트 설정](#bkmk_configure_site_settings) 섹션을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="da79f-182">See the [Report Manager Folder Settings](#bkmk_configure_folder_settings) and [Report Manager Site Settings](#bkmk_configure_site_settings) sections earlier in this topic.</span></span>  
  
##  <a name="additional-information"></a><a name="bkmk_addiitonal_informaiton"></a><span data-ttu-id="da79f-183">추가 정보</span><span class="sxs-lookup"><span data-stu-id="da79f-183">Additional Information</span></span>  
 <span data-ttu-id="da79f-184">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 관리와 관련된 일반적인 추가 구성 단계는 보고서 서버 컴퓨터에 대한 액세스를 허용하도록 Windows 방화벽에서 포트 80을 여는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="da79f-184">An additional and common configuration step related to [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] administration is to open port 80 in Windows Firewall to allow access to the report server computer.</span></span> <span data-ttu-id="da79f-185">자세한 내용은 [Configure a Firewall for Report Server Access](configure-a-firewall-for-report-server-access.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="da79f-185">For instructions, see [Configure a Firewall for Report Server Access](configure-a-firewall-for-report-server-access.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da79f-186">참고 항목</span><span class="sxs-lookup"><span data-stu-id="da79f-186">See Also</span></span>  
 [<span data-ttu-id="da79f-187">Reporting Services 기본 모드 보고서 서버 관리</span><span class="sxs-lookup"><span data-stu-id="da79f-187">Manage a Reporting Services Native Mode Report Server</span></span>](manage-a-reporting-services-native-mode-report-server.md)  
  
  
