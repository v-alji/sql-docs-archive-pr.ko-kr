---
title: '자습서: Reporting Services 도구를 찾고 시작하는 방법(SSRS) | Microsoft Docs'
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- Report Builder 1.0, locating and starting tool
- Reporting Services, tutorials
- Reporting Services, tools
- Reporting Services Configuration tool
- Business Intelligence Development Studio, locating and starting tool
- Model Designer [Reporting Services], locating and starting tool
- Report Designer [Reporting Services], tutorials
- tools [Reporting Services]
- tutorials [Reporting Services]
- Report Manager [Reporting Services]
ms.assetid: 51ad69d8-fe92-4662-a7cd-d235692f0c03
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 2b7a981a53378ea6b37959e891cac8bd891c2578
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87735979"
---
# <a name="tutorial-how-to-locate-and-start-reporting-services-tools-ssrs"></a><span data-ttu-id="0b081-102">자습서: Reporting Services 도구를 찾고 시작하는 방법</span><span class="sxs-lookup"><span data-stu-id="0b081-102">Tutorial: How to Locate and Start Reporting Services Tools (SSRS)</span></span>
  <span data-ttu-id="0b081-103">이 자습서에서는 보고서 서버를 구성하고 보고서 서버 내용 및 작업을 관리하며 보고서를 만들어 게시하는 데 사용되는 도구를 소개합니다.</span><span class="sxs-lookup"><span data-stu-id="0b081-103">This tutorial introduces the tools used to configure a report server, manage report server content and operations, and create and publish reports.</span></span> <span data-ttu-id="0b081-104">이 자습서를 통해 새 사용자는 각 도구를 찾고 여는 방법을 이해할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b081-104">The purpose of this tutorial is to help new users understand how to find and open each tool.</span></span> <span data-ttu-id="0b081-105">이미 이 도구에 익숙한 경우 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]를 사용하는 데 중요한 기술을 배울 수 있는 다른 자습서로 이동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b081-105">If you are already familiar with the tools, you can move on to other tutorials that can help you learn important skills for using [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="0b081-106">다른 자습서에 대 한 자세한 내용은 [SSRS&#41;&#40;Reporting Services 자습서 ](../reporting-services-tutorials-ssrs.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="0b081-106">For more information about other tutorials, see [Reporting Services Tutorials &#40;SSRS&#41;](../reporting-services-tutorials-ssrs.md).</span></span>  
  
 <span data-ttu-id="0b081-107">이 항목의 내용:</span><span class="sxs-lookup"><span data-stu-id="0b081-107">In this topic:</span></span>  
  
-   [<span data-ttu-id="0b081-108">Reporting Services 구성 관리자(기본 모드)</span><span class="sxs-lookup"><span data-stu-id="0b081-108">Reporting Services Configuration Manager (Native Mode)</span></span>](#bkmk_configuration_manager)  
  
-   [<span data-ttu-id="0b081-109">보고서 관리자(기본 모드)</span><span class="sxs-lookup"><span data-stu-id="0b081-109">Report Manager (Native Mode)</span></span>](#bkmk_report_manager)  
  
-   [<span data-ttu-id="0b081-110">Management Studio</span><span class="sxs-lookup"><span data-stu-id="0b081-110">Management Studio</span></span>](#bkmk_managements_studio)  
  
-   [<span data-ttu-id="0b081-111">보고서 디자이너 및 보고서 마법사가 포함된 SQL Server Data Tools</span><span class="sxs-lookup"><span data-stu-id="0b081-111">SQL Server Data Tools with Report Designer and Report Wizard</span></span>](#bkmk_ssdt)  
  
-   [<span data-ttu-id="0b081-112">보고서 작성기</span><span class="sxs-lookup"><span data-stu-id="0b081-112">Report Builder</span></span>](#bkmk_report_builder)  
  
##  <a name="reporting-services-configuration-manager-native-mode"></a><a name="bkmk_configuration_manager"></a><span data-ttu-id="0b081-113">Reporting Services 구성 관리자 (기본 모드)</span><span class="sxs-lookup"><span data-stu-id="0b081-113">Reporting Services Configuration Manager (Native Mode)</span></span>  
 <span data-ttu-id="0b081-114">기본 모드 구성 관리자를 사용하여 다음을 완료합니다.</span><span class="sxs-lookup"><span data-stu-id="0b081-114">Use the Native mode configuration manager to complete the following:, , , , , and.</span></span>  
  
-   <span data-ttu-id="0b081-115">서비스 계정을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="0b081-115">Specify the service account.</span></span>  
  
-   <span data-ttu-id="0b081-116">보고서 서버 데이터베이스를 만들거나 업그레이드합니다.</span><span class="sxs-lookup"><span data-stu-id="0b081-116">Create or upgrade the report server database.</span></span>  
  
-   <span data-ttu-id="0b081-117">연결 속성을 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="0b081-117">Modify the connection properties.</span></span>  
  
-   <span data-ttu-id="0b081-118">URL을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="0b081-118">Specify URLs.</span></span>  
  
-   <span data-ttu-id="0b081-119">암호화 키를 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="0b081-119">Manage encryption keys.</span></span>  
  
-   <span data-ttu-id="0b081-120">무인 보고서 처리 및 전자 메일 보고서 배달을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="0b081-120">Configure unattended report processing and e-mail report delivery.</span></span>  
  
 <span data-ttu-id="0b081-121">**설치:** [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 구성 관리자는 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 기본 모드를 설치할 때 함께 설치됩니다.</span><span class="sxs-lookup"><span data-stu-id="0b081-121">**Installation:** [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] Configuration Manager is installed when you install [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] Native mode.</span></span> <span data-ttu-id="0b081-122">자세한 내용은 [Reporting Services 기본 모드 보고서 서버 설치](../install-windows/install-reporting-services-native-mode-report-server.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0b081-122">For more information, see [Install Reporting Services Native Mode Report Server](../install-windows/install-reporting-services-native-mode-report-server.md)</span></span>  
  
#### <a name="to-start-the-reporting-services-configuration-manager"></a><span data-ttu-id="0b081-123">Reporting Services 구성 관리자를 시작하려면</span><span class="sxs-lookup"><span data-stu-id="0b081-123">To start the Reporting Services Configuration Manager</span></span>  
  
1.  <span data-ttu-id="0b081-124">Windows 시작 화면에서를 입력 `reporting` 하 고 **앱** 검색 결과에서 **Reporting Services 구성 관리자**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b081-124">On the Windows start screen, type `reporting` and in the **Apps** search results, click **Reporting Services Configuration Manager**.</span></span>  
  
     <span data-ttu-id="0b081-125">![Reporting Services 구성 관리자 시작](../media/bi-ssrs-configmanager-win8-startscreen.gif "Reporting Services 구성 관리자 시작")</span><span class="sxs-lookup"><span data-stu-id="0b081-125">![reporting services configuration manager on start](../media/bi-ssrs-configmanager-win8-startscreen.gif "reporting services configuration manager on start")</span></span>  
  
     <span data-ttu-id="0b081-126">**디스크나**</span><span class="sxs-lookup"><span data-stu-id="0b081-126">**Or**</span></span>  
  
     <span data-ttu-id="0b081-127">**시작**, **프로그램**, [!INCLUDE[ssCurrentUI](../../../includes/sscurrentui-md.md)], **구성 도구**를 차례로 클릭한 다음 **Reporting Services 구성 관리자**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0b081-127">Click **Start**, then click **Programs**, then click [!INCLUDE[ssCurrentUI](../../../includes/sscurrentui-md.md)], then click **Configuration Tools**, and then click **Reporting Services Configuration Manager**.</span></span>  
  
     <span data-ttu-id="0b081-128">구성할 보고서 서버 인스턴스를 선택할 수 있도록 **보고서 서버 설치 인스턴스 선택** 대화 상자가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="0b081-128">The **Report Server Installation Instance Selection** dialog box appears so that you can select the report server instance you want to configure.</span></span>  
  
2.  <span data-ttu-id="0b081-129">**서버 이름**에 보고서 서버 인스턴스가 설치된 컴퓨터의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="0b081-129">In **Server Name**, specify the name of the computer on which the report server instance is installed.</span></span> <span data-ttu-id="0b081-130">기본적으로 로컬 컴퓨터의 이름이 지정되지만 원격 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인스턴스의 이름을 입력할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b081-130">The name of the local computer is specified by default, but you can also type the name of a remote [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instance.</span></span>  
  
     <span data-ttu-id="0b081-131">원격 컴퓨터를 지정하는 경우 **찾기** 를 클릭하여 연결을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="0b081-131">If you specify a remote computer, click **Find** to establish a connection.</span></span> <span data-ttu-id="0b081-132">미리 보고서 서버를 원격 관리용으로 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b081-132">The report server must be configured for remote administration in advance.</span></span> <span data-ttu-id="0b081-133">자세한 내용은 [원격 관리를 위한 보고서 서버 구성](../report-server/configure-a-report-server-for-remote-administration.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0b081-133">For more information, see [Configure a Report Server for Remote Administration](../report-server/configure-a-report-server-for-remote-administration.md).</span></span>  
  
3.  <span data-ttu-id="0b081-134">**인스턴스 이름**에서 구성할 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 인스턴스를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="0b081-134">In **Instance Name**, choose the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] instance that you want to configure.</span></span> <span data-ttu-id="0b081-135">[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]및 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 보고서 서버 인스턴스만 목록에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="0b081-135">Only [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], and [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] report server instances appear in the list.</span></span> <span data-ttu-id="0b081-136">이전 버전의 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]는 구성할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0b081-136">You cannot configure earlier versions of [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].</span></span>  
  
4.  <span data-ttu-id="0b081-137">**연결**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0b081-137">Click **Connect**.</span></span>  
  
5.  <span data-ttu-id="0b081-138">도구가 시작되었는지 확인하려면 결과를 다음 이미지와 비교합니다.</span><span class="sxs-lookup"><span data-stu-id="0b081-138">To verify that you launched the tool, compare your results to the following image:</span></span>  
  
     <span data-ttu-id="0b081-139">![Reporting Services 구성 도구](../media/rs-ui-reportserverconfigkatmai.gif "Reporting Services 구성 도구")</span><span class="sxs-lookup"><span data-stu-id="0b081-139">![Reporting Services Configuration tool](../media/rs-ui-reportserverconfigkatmai.gif "Reporting Services Configuration tool")</span></span>  
  
 <span data-ttu-id="0b081-140">**다음 단계:** [보고서 서버 구성 및 관리&#40;SSRS 기본 모드&#41;](../report-server/configure-and-administer-a-report-server-ssrs-native-mode.md) 및 [Reporting Services 구성 관리자&#40;기본 모드&#41;](../../sql-server/install/reporting-services-configuration-manager-native-mode.md)</span><span class="sxs-lookup"><span data-stu-id="0b081-140">**Next Steps:** [Configure and Administer a Report Server &#40;SSRS Native Mode&#41;](../report-server/configure-and-administer-a-report-server-ssrs-native-mode.md) and [Reporting Services Configuration Manager &#40;Native Mode&#41;](../../sql-server/install/reporting-services-configuration-manager-native-mode.md).</span></span>  
  
##  <a name="report-manager-native-mode"></a><a name="bkmk_report_manager"></a><span data-ttu-id="0b081-141">보고서 관리자 (기본 모드)</span><span class="sxs-lookup"><span data-stu-id="0b081-141">Report Manager (Native Mode)</span></span>  
 <span data-ttu-id="0b081-142">[보고서 관리자 &#40;SSRS 기본 모드&#41;](../report-manager-ssrs-native-mode.md) 사용 하 여 사용 권한을 설정 하 고, 구독 및 일정을 관리 하 고, 보고서 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b081-142">Use [Report Manager  &#40;SSRS Native Mode&#41;](../report-manager-ssrs-native-mode.md) to set permissions, manage subscriptions and schedules, and work with reports.</span></span> <span data-ttu-id="0b081-143">보고서 관리자를 사용하여 보고서를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b081-143">You can also use Report Manager to view reports.</span></span>  
  
 <span data-ttu-id="0b081-144">**설치:** 보고서 관리자는 기본 모드를 설치할 때 설치 됩니다 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] . [Reporting Services 기본 모드 보고서 서버 설치](../install-windows/install-reporting-services-native-mode-report-server.md)</span><span class="sxs-lookup"><span data-stu-id="0b081-144">**Installation:** Report Manager Is installed when you install [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] Native mode: [Install Reporting Services Native Mode Report Server](../install-windows/install-reporting-services-native-mode-report-server.md)</span></span>  
  
 <span data-ttu-id="0b081-145">보고서 관리자를 열려면 먼저 충분한 권한이 있어야 합니다. 처음에는 로컬 관리자 그룹의 멤버만 보고서 관리자 기능에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b081-145">Before you can open Report Manager, you must have sufficient permissions (initially, only members of the local Administrators group have permissions that provide access to Report Manager features).</span></span> <span data-ttu-id="0b081-146">보고서 관리자는 현재 사용자의 역할 할당에 따라 다양한 페이지와 옵션을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="0b081-146">Report Manager provides different pages and options depending on the role assignments of the current user.</span></span> <span data-ttu-id="0b081-147">사용 권한이 없는 사용자에게는 빈 페이지가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="0b081-147">Users who have no permissions will get an empty page.</span></span> <span data-ttu-id="0b081-148">보고서를 볼 권한이 있는 사용자에게는 클릭하여 보고서를 열 수 있는 링크가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="0b081-148">Users with permissions to view reports will get links that they can click to open the reports.</span></span> <span data-ttu-id="0b081-149">권한에 대한 자세한 내용은 [역할 및 권한&#40;Reporting Services&#41;](../security/roles-and-permissions-reporting-services.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0b081-149">To learn more about permissions, see [Roles and Permissions &#40;Reporting Services&#41;](../security/roles-and-permissions-reporting-services.md).</span></span>  
  
#### <a name="to-start-report-manager"></a><span data-ttu-id="0b081-150">보고서 관리자를 시작하려면</span><span class="sxs-lookup"><span data-stu-id="0b081-150">To start Report Manager</span></span>  
  
1.  <span data-ttu-id="0b081-151">브라우저를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="0b081-151">Open your browser.</span></span> <span data-ttu-id="0b081-152">지원 되는 브라우저 및 브라우저 버전에 대 한 자세한 내용은 [Reporting Services 계획 및 파워 뷰 브라우저 지원 &#40;Reporting Services 2014&#41;](../browser-support-for-reporting-services-and-power-view.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="0b081-152">For information on supported browsers and browser versions, see [Planning for Reporting Services and Power View Browser Support &#40;Reporting Services 2014&#41;](../browser-support-for-reporting-services-and-power-view.md).</span></span>  
  
2.  <span data-ttu-id="0b081-153">웹 브라우저의 주소 표시줄에 보고서 관리자 URL을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="0b081-153">In the address bar of the Web browser, type the Report Manager URL.</span></span> <span data-ttu-id="0b081-154">기본적으로 URL은 **http:// \<serverName> /reports**입니다.</span><span class="sxs-lookup"><span data-stu-id="0b081-154">By default, the URL is **http://\<serverName>/reports**.</span></span> <span data-ttu-id="0b081-155">Reporting Services 구성 도구를 사용하여 서버 이름과 URL을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b081-155">You can use the Reporting Services Configuration tool to confirm the server name and URL.</span></span> <span data-ttu-id="0b081-156">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]에서 사용되는 URL에 대한 자세한 내용은 [보고서 서버 URL 구성&#40;SSRS 구성 관리자&#41;](../install-windows/configure-report-server-urls-ssrs-configuration-manager.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0b081-156">For more information about URLs used in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)], see [Configure Report Server URLs  &#40;SSRS Configuration Manager&#41;](../install-windows/configure-report-server-urls-ssrs-configuration-manager.md).</span></span>  
  
3.  <span data-ttu-id="0b081-157">보고서 관리자가 브라우저 창에서 열립니다.</span><span class="sxs-lookup"><span data-stu-id="0b081-157">Report Manager opens in the browser window.</span></span> <span data-ttu-id="0b081-158">시작 페이지는 홈 폴더입니다.</span><span class="sxs-lookup"><span data-stu-id="0b081-158">The startup page is the Home folder.</span></span> <span data-ttu-id="0b081-159">사용 권한에 따라 추가 폴더, 보고서에 대한 하이퍼링크 및 시작 페이지 내의 리소스 파일을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b081-159">Depending on permissions, you might see additional folders, hyperlinks to reports, and resource files within the startup page.</span></span> <span data-ttu-id="0b081-160">또한 도구 모음에서 추가적인 단추와 명령을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b081-160">You might also see additional buttons and commands on the toolbar.</span></span>  
  
4.  <span data-ttu-id="0b081-161">로컬 보고서 서버에서 보고서 관리자를 실행 하는 경우 [로컬 관리에 대해 기본 모드 보고서 서버 구성 &#40;SSRS&#41;](../report-server/configure-a-native-mode-report-server-for-local-administration-ssrs.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="0b081-161">If you run Report Manager on the local report server, see [Configure a Native Mode Report Server for Local Administration &#40;SSRS&#41;](../report-server/configure-a-native-mode-report-server-for-local-administration-ssrs.md).</span></span>  
  
 <span data-ttu-id="0b081-162">**다음 단계:** [기본 모드&#41;&#40;보고서 관리자 구성 ](../report-server/configure-web-portal.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="0b081-162">**Next Steps:** [Configure Report Manager &#40;Native Mode&#41;](../report-server/configure-web-portal.md).</span></span>  
  
##  <a name="management-studio"></a><a name="bkmk_managements_studio"></a> <span data-ttu-id="0b081-163">Management Studio</span><span class="sxs-lookup"><span data-stu-id="0b081-163">Management Studio</span></span>  
 <span data-ttu-id="0b081-164">보고서 서버 관리자는 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 를 사용하여 다른 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 구성 요소 서버와 함께 보고서 서버를 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b081-164">Report server administrators can use [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] to manage a report server alongside other [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] component servers.</span></span> <span data-ttu-id="0b081-165">자세한 내용은 [Use SQL Server Management Studio](../../database-engine/use-sql-server-management-studio.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0b081-165">For more information, see [Use SQL Server Management Studio](../../database-engine/use-sql-server-management-studio.md).</span></span>  
  
#### <a name="to-start-sql-server-management-studio"></a><span data-ttu-id="0b081-166">SQL Server Management Studio를 시작하려면</span><span class="sxs-lookup"><span data-stu-id="0b081-166">To Start SQL Server Management Studio</span></span>  
  
1.  <span data-ttu-id="0b081-167">Windows 시작 화면에서를 입력 `sql server` 하 고 **앱** 검색 결과에서 **SQL Server Management Studio**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b081-167">From the Windows Start Screen type `sql server` and in the **Apps** search results, click **SQL Server Management Studio**.</span></span>  
  
     <span data-ttu-id="0b081-168">![Windows 시작 화면의 Management Studio](../media/bi-ssms-win8-startscreen.gif "Windows 시작 화면의 Management Studio")</span><span class="sxs-lookup"><span data-stu-id="0b081-168">![managment studio from windows start screen](../media/bi-ssms-win8-startscreen.gif "managment studio from windows start screen")</span></span>  
  
     <span data-ttu-id="0b081-169">**디스크나**</span><span class="sxs-lookup"><span data-stu-id="0b081-169">**Or**</span></span>  
  
     <span data-ttu-id="0b081-170">**시작**, **모든 프로그램**, [!INCLUDE[ssCurrentUI](../../../includes/sscurrentui-md.md)]를 차례로 클릭한 후 **SQL Server Management Studio**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0b081-170">Click **Start**, then click **All Programs**, then click [!INCLUDE[ssCurrentUI](../../../includes/sscurrentui-md.md)], and then click **SQL Server Management Studio**.</span></span> <span data-ttu-id="0b081-171">**서버에 연결** 대화 상자가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="0b081-171">The **Connect to Server** dialog box appears.</span></span>  
  
2.  <span data-ttu-id="0b081-172">**서버에 연결** 대화 상자가 표시되지 않는 경우 **개체 탐색기**에서 **연결** 을 클릭한 다음 **Reporting Services**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0b081-172">If the **Connect to Server** dialog box does not appear, in **Object Explorer**, click **Connect** and then select **Reporting Services**.</span></span>  
  
3.  <span data-ttu-id="0b081-173">**서버 유형** 목록에서 **Reporting Services**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="0b081-173">In the **Server type** list, select **Reporting Services**.</span></span> <span data-ttu-id="0b081-174">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 가 목록에 없다면 설치되지 않은 것입니다.</span><span class="sxs-lookup"><span data-stu-id="0b081-174">If [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] is not on the list, it is not installed.</span></span>  
  
4.  <span data-ttu-id="0b081-175">**서버 이름** 목록에서 보고서 서버 인스턴스를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="0b081-175">In the **Server name** list, select a report server instance.</span></span> <span data-ttu-id="0b081-176">목록에 로컬 인스턴스가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="0b081-176">Local instances appear in the list.</span></span> <span data-ttu-id="0b081-177">원격 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인스턴스의 이름을 입력할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b081-177">You can also type the name of a remote [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instance.</span></span>  
  
5.  <span data-ttu-id="0b081-178">**연결**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0b081-178">Click **Connect**.</span></span> <span data-ttu-id="0b081-179">루트 노드를 확장하여 서버 속성을 설정하거나 역할 정의를 수정하거나 보고서 서버 기능을 해제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b081-179">You can expand the root node to set server properties, modify role definitions, or turn off report server features.</span></span>  
  
##  <a name="sql-server-data-tools-with-report-designer-and-report-wizard"></a><a name="bkmk_ssdt"></a><span data-ttu-id="0b081-180">보고서 디자이너 및 보고서 마법사를 사용 하 여 SQL Server Data Tools</span><span class="sxs-lookup"><span data-stu-id="0b081-180">SQL Server Data Tools with Report Designer and Report Wizard</span></span>  
 <span data-ttu-id="0b081-181">보고서 디자이너는 [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] - Visual Studio 2012용 Business Intelligence에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b081-181">Report Designer is available within [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] - Business Intelligence for Visual Studio 2012.</span></span> <span data-ttu-id="0b081-182">이러한 도구의 디자인 화면에는 보고서 제작 기능에 액세스하는 데 사용되는 탭 창, 마법사 및 메뉴가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b081-182">The design surface in the tool includes tabbed windows, wizards, and menus used to access report authoring features.</span></span> <span data-ttu-id="0b081-183">보고서 서버 프로젝트 또는 보고서 서버 마법사 템플릿을 선택하면 보고서 디자이너 도구를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b081-183">The report designer tool becomes available when you choose a Report Server Project or a Report Server Wizard template.</span></span> <span data-ttu-id="0b081-184">자세한 내용은 [SQL Server Data Tools의 Reporting Services&#40;SSDT&#41;](reporting-services-in-sql-server-data-tools-ssdt.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0b081-184">To learn more, see [Reporting Services in SQL Server Data Tools &#40;SSDT&#41;](reporting-services-in-sql-server-data-tools-ssdt.md).</span></span>  
  
#### <a name="to-start-report-designer"></a><span data-ttu-id="0b081-185">보고서 디자이너를 시작하려면</span><span class="sxs-lookup"><span data-stu-id="0b081-185">To start Report Designer</span></span>  
  
1.  <span data-ttu-id="0b081-186">Windows 시작 화면에서 **data** 를 입력한 다음 **응용 프로그램** 검색 결과에서 **Visual Studio 2012용 SQL Server Data Tools**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0b081-186">From the Windows start screen, type **data** and in the **Apps** search results, click **SQL Server Data Tools for Visual Studio 2012**.</span></span>  
  
     <span data-ttu-id="0b081-187">**디스크나**</span><span class="sxs-lookup"><span data-stu-id="0b081-187">**Or**</span></span>  
  
     <span data-ttu-id="0b081-188">**시작**을 클릭 하 고 **모든 프로그램**,을 차례로 가리킨 [!INCLUDE[ssCurrentUI](../../../includes/sscurrentui-md.md)] 다음 **SQL Server Data Tools (SSDT)** 를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b081-188">Click **Start**, point to **All Programs**, point to [!INCLUDE[ssCurrentUI](../../../includes/sscurrentui-md.md)], and then click **SQL Server Data Tools (SSDT)**.</span></span>  
  
2.  <span data-ttu-id="0b081-189">**파일** 메뉴에서 **새로 만들기**를 가리킨 다음 **프로젝트**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0b081-189">On the **File** menu, point to **New**, and then click **Project**.</span></span>  
  
3.  <span data-ttu-id="0b081-190">**프로젝트 형식** 목록에서 **비즈니스 인텔리전스 프로젝트**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0b081-190">In the **Project Types** list, click **Business Intelligence Projects**.</span></span>  
  
4.  <span data-ttu-id="0b081-191">**템플릿** 목록에서 **보고서 서버 프로젝트**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0b081-191">In the **Templates** list, click **Report Server Project**.</span></span> <span data-ttu-id="0b081-192">다음 다이어그램에서는 프로젝트 템플릿이 대화 상자에 표시되는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="0b081-192">The following diagram shows how the project templates appear in the dialog box:</span></span>  
  
     <span data-ttu-id="0b081-193">![새 프로젝트 템플릿 대화 상자](../media/rs-ui-newrsproject.gif "새 프로젝트 템플릿 대화 상자")</span><span class="sxs-lookup"><span data-stu-id="0b081-193">![New Project template dialog box](../media/rs-ui-newrsproject.gif "New Project template dialog box")</span></span>  
  
5.  <span data-ttu-id="0b081-194">프로젝트의 이름과 위치를 입력하거나 **찾아보기** 를 클릭하여 위치를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="0b081-194">Type a name and location for the project, or click **Browse** and select a location.</span></span>  
  
6.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]<span data-ttu-id="0b081-195">[!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]시작 페이지와 함께 열립니다 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="0b081-195">[!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] opens with the [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] start page.</span></span> <span data-ttu-id="0b081-196">솔루션 탐색기는 보고서 및 데이터 원본을 만드는 범주를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="0b081-196">Solution Explorer provides categories for creating reports and data sources.</span></span> <span data-ttu-id="0b081-197">이러한 범주를 사용하여 새 보고서 및 데이터 원본을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b081-197">You can use these categories to create new reports and data sources.</span></span> <span data-ttu-id="0b081-198">보고서 정의를 만들면 탭 창이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="0b081-198">Tabbed windows appear when you create a report definition.</span></span> <span data-ttu-id="0b081-199">탭 창은 데이터, 레이아웃 및 미리 보기입니다.</span><span class="sxs-lookup"><span data-stu-id="0b081-199">The tabbed windows are Data, Layout, and Preview..</span></span>  
  
 <span data-ttu-id="0b081-200">첫 번째 보고서를 시작하려면 [기본 테이블 보고서 만들기&#40;SSRS 자습서&#41;](../create-a-basic-table-report-ssrs-tutorial.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0b081-200">To get started on your first report, see [Create a Basic Table Report &#40;SSRS Tutorial&#41;](../create-a-basic-table-report-ssrs-tutorial.md).</span></span> <span data-ttu-id="0b081-201">보고서 디자이너 내에서 사용할 수 있는 쿼리 디자이너에 대 한 자세한 내용은 [SSRS&#41;&#40;보고서 디자이너 SQL Server Data Tools 쿼리 디자인 도구 ](../report-data/query-design-tools-ssrs.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="0b081-201">To learn more about query designers you can use within Report Designer, see [Query Design Tools in Report Designer SQL Server Data Tools &#40;SSRS&#41;](../report-data/query-design-tools-ssrs.md).</span></span>  
  
##  <a name="report-builder"></a><a name="bkmk_report_builder"></a> <span data-ttu-id="0b081-202">보고서 작성기</span><span class="sxs-lookup"><span data-stu-id="0b081-202">Report Builder</span></span>  
 <span data-ttu-id="0b081-203">[보고서 작성기 &#40;SSRS&#41;](report-builder-authoring-environment-ssrs.md) 를 사용 하 여 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Office와 비슷한 제작 환경에서 보고서를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b081-203">Use [Report Builder &#40;SSRS&#41;](report-builder-authoring-environment-ssrs.md) to create reports in a [!INCLUDE[msCoName](../../includes/msconame-md.md)] Office-like authoring environment.</span></span> <span data-ttu-id="0b081-204">또한 보고서를 보고서 디자이너에서 만들었는지 이전 버전의 보고서 작성기에서 만들었는지에 상관없이 모든 기존 보고서를 사용자 지정하고 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b081-204">You can customize and update all existing reports, regardless of whether they were created in Report Designer or in the previous versions of Report Builder.</span></span> <span data-ttu-id="0b081-205">로컬 컴퓨터에 보고서 작성기를 설치하기 위해 실행하는 ReportBuilder3.msi 파일의 위치에 대해 관리자에게 문의하세요.</span><span class="sxs-lookup"><span data-stu-id="0b081-205">Contact your administrator for the location of the ReportBuilder3.msi file that you run to install Report Builder on your local computer.</span></span>  
  
 <span data-ttu-id="0b081-206">**설치:** 보고서 작성기의 한 번 클릭 버전은 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 기본 모드 또는 SharePoint 모드로 설치 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0b081-206">**Installation:** The click-once version of report builder is installed by either [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] Native mode or SharePoint mode.</span></span> <span data-ttu-id="0b081-207">독립 실행형 버전의 보고서 작성기는 별도로 다운로드해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b081-207">The Stand-alone version of Report Builder is a separate download.</span></span>  <span data-ttu-id="0b081-208">[보고서 작성기 &#40;보고서 작성기의 독립 실행형 버전 설치를](../install-windows/install-report-builder.md) 참조 하세요&#41;</span><span class="sxs-lookup"><span data-stu-id="0b081-208">See [Install the Stand-Alone Version of Report Builder &#40;Report Builder&#41;](../install-windows/install-report-builder.md)</span></span>  
  
#### <a name="to-start-report-builder-clickonce-from-report-manager-native-mode"></a><span data-ttu-id="0b081-209">보고서 관리자(기본 모드)에서 보고서 작성기 ClickOnce를 시작하려면</span><span class="sxs-lookup"><span data-stu-id="0b081-209">To start Report Builder ClickOnce from Report Manager (Native Mode)</span></span>  
  
1.  <span data-ttu-id="0b081-210">웹 브라우저에서 보고서 서버의 보고서 관리자 URL을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="0b081-210">In your Web browser, type the Report Manager URL for your report server.</span></span> <span data-ttu-id="0b081-211">기본적으로 URL은 http:///reports입니다. \<*servername*></span><span class="sxs-lookup"><span data-stu-id="0b081-211">By default, the URL is http://\<*servername*>/reports.</span></span> <span data-ttu-id="0b081-212">보고서 관리자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="0b081-212">Report Manager opens.</span></span>  
  
2.  <span data-ttu-id="0b081-213">**보고서 작성기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0b081-213">Click **Report Builder**.</span></span>  
  
     <span data-ttu-id="0b081-214">보고서 작성기가 열립니다. 이제 보고서를 작성하거나 보고서 서버의 보고서를 열 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b081-214">Report Builder opens and you can create a report or open a report on the report server.</span></span>  
  
#### <a name="to-start-report-builder-clickonce-using-a-url"></a><span data-ttu-id="0b081-215">URL을 사용하여 보고서 작성기 ClickOnce를 시작하려면</span><span class="sxs-lookup"><span data-stu-id="0b081-215">To start Report Builder ClickOnce using a URL</span></span>  
  
1.  <span data-ttu-id="0b081-216">웹 브라우저의 주소 표시줄에 다음 URL을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="0b081-216">In your Web browser, type the following URL in the address bar:</span></span>  
  
     <span data-ttu-id="0b081-217">**http:// \<servername> /reportserver/reportbuilder/ReportBuilder_3_0_0_0 응용 프로그램**</span><span class="sxs-lookup"><span data-stu-id="0b081-217">**http://\<servername>/reportserver/reportbuilder/ReportBuilder_3_0_0_0.application**</span></span>  
  
2.  <span data-ttu-id="0b081-218">Enter 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="0b081-218">Press ENTER.</span></span>  
  
     <span data-ttu-id="0b081-219">보고서 작성기가 열립니다. 이제 보고서를 작성하거나 보고서 서버의 보고서를 열 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b081-219">Report Builder opens and you can create a report or open a report on the report server.</span></span>  
  
#### <a name="to-start-report-builder-clickonce-in-reporting-services-sharepoint-mode"></a><span data-ttu-id="0b081-220">Reporting Services SharePoint 모드에서 보고서 작성기 ClickOnce를 시작하려면</span><span class="sxs-lookup"><span data-stu-id="0b081-220">To start Report Builder ClickOnce in Reporting Services SharePoint mode</span></span>  
  
1.  <span data-ttu-id="0b081-221">새 보고서를 만들 라이브러리가 포함된 사이트로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="0b081-221">Navigate to the site that contains the library where you want to create a new report.</span></span>  
  
2.  <span data-ttu-id="0b081-222">라이브러리를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="0b081-222">Open the library.</span></span>  
  
3.  <span data-ttu-id="0b081-223">**새로 만들기** 메뉴에서 **보고서 작성기 보고서**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0b081-223">On the **New** menu, click **Report Builder Report**.</span></span>  
  
     <span data-ttu-id="0b081-224">보고서 작성기가 열립니다. 이제 보고서를 작성하거나 보고서 서버의 보고서를 열 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b081-224">Report Builder opens and you can create a report or open a report on the report server.</span></span>  
  
#### <a name="to-start-report-builder-stand-alone"></a><span data-ttu-id="0b081-225">보고서 작성기 독립 실행형을 시작하려면</span><span class="sxs-lookup"><span data-stu-id="0b081-225">To start Report Builder Stand-alone</span></span>  
  
1.  <span data-ttu-id="0b081-226">Windows 시작 화면에서 **report builder** 를 입력한 다음 **보고서 작성기 3.0**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0b081-226">From the Windows start screen, type **report builder** and then click **Report Builder 3.0**.</span></span>  
  
     <span data-ttu-id="0b081-227">**디스크나**</span><span class="sxs-lookup"><span data-stu-id="0b081-227">**Or**</span></span>  
  
     <span data-ttu-id="0b081-228">시작 메뉴에서 **모든 프로그램**을 클릭한 다음 **Microsoft SQL Server 2014 보고서 작성기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0b081-228">On the Start menu, click **All Programs**, and then click **Microsoft SQL Server 2014 Report Builder**.</span></span>  
  
2.  <span data-ttu-id="0b081-229">**보고서 작성기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0b081-229">Click **Report Builder**.</span></span>  
  
     <span data-ttu-id="0b081-230">보고서 작성기가 열립니다. 이제 보고서를 작성하거나 열 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b081-230">Report Builder opens and you can create or open a report.</span></span>  
  
3.  <span data-ttu-id="0b081-231">보고서 작성기 설명서를 열려면 **보고서 작성기 도움말** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0b081-231">Click **Report Builder Help** to open the documentation for Report Builder.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b081-232">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0b081-232">See Also</span></span>  
 <span data-ttu-id="0b081-233">[설치, 제거 및 보고서 작성기 지원](../install-uninstall-and-report-builder-support.md) </span><span class="sxs-lookup"><span data-stu-id="0b081-233">[Install, Uninstall, and Report Builder Support](../install-uninstall-and-report-builder-support.md) </span></span>  
 <span data-ttu-id="0b081-234">[Sharepoint 2010 및 sharepoint 2013 &#40;SharePoint 모드 설치 Reporting Services&#41;](../install-windows/install-reporting-services-sharepoint-mode.md) </span><span class="sxs-lookup"><span data-stu-id="0b081-234">[Reporting Services SharePoint Mode Installation &#40;SharePoint 2010 and SharePoint 2013&#41;](../install-windows/install-reporting-services-sharepoint-mode.md) </span></span>  
 <span data-ttu-id="0b081-235">[Reporting Services 보고서 서버](../reporting-services-report-server.md) </span><span class="sxs-lookup"><span data-stu-id="0b081-235">[Reporting Services Report Server](../reporting-services-report-server.md) </span></span>  
 <span data-ttu-id="0b081-236">[SSRS&#41;&#40;보고서 디자이너 SQL Server Data Tools의 쿼리 디자인 도구](../report-data/query-design-tools-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="0b081-236">[Query Design Tools in Report Designer SQL Server Data Tools &#40;SSRS&#41;](../report-data/query-design-tools-ssrs.md) </span></span>  
 [<span data-ttu-id="0b081-237">Reporting Services&#40;SSRS&#41; 자습서</span><span class="sxs-lookup"><span data-stu-id="0b081-237">Reporting Services Tutorials &#40;SSRS&#41;</span></span>](../reporting-services-tutorials-ssrs.md)  
  
  
