---
title: 보고서 서버(Reporting Services 기본 모드) 구성 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- report server configuration
- report servers [Reporting Services], configuring
ms.assetid: ef84ce9d-9156-48e9-8073-7e0535476932
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 64c63f52c373e034f0242101de0a27ee775920ad
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652595"
---
# <a name="configure-a-report-server-reporting-services-native-mode"></a><span data-ttu-id="febcb-102">보고서 서버(Reporting Services 기본 모드) 구성</span><span class="sxs-lookup"><span data-stu-id="febcb-102">Configure a Report Server (Reporting Services Native Mode)</span></span>
  <span data-ttu-id="febcb-103">설치 중에 선택한 옵션에 따라 보고서 서버를 사용하기 전에 추가 구성이 필요할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="febcb-103">Depending on options you selected during installation, the Report Server might require additional configuration before you can use it.</span></span> <span data-ttu-id="febcb-104">보고서 서버 구성은 최소한 다음과 같은 요소로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="febcb-104">At a minimum, a report server configuration consists of the following:</span></span>  
  
-   <span data-ttu-id="febcb-105">보고서 서버 서비스 계정(설치 중 구성됨)</span><span class="sxs-lookup"><span data-stu-id="febcb-105">A Report Server service account (configured during installation).</span></span>  
  
-   <span data-ttu-id="febcb-106">보고서 서버에 대한 액세스를 제공하는 웹 서비스 URL</span><span class="sxs-lookup"><span data-stu-id="febcb-106">A Web service URL that provides access to the report server.</span></span>  
  
-   <span data-ttu-id="febcb-107">애플리케이션 데이터, 보고서 및 기타 항목을 저장하는 보고서 서버 데이터베이스</span><span class="sxs-lookup"><span data-stu-id="febcb-107">A report server database that stores application data, reports, and other items.</span></span>  
  
 <span data-ttu-id="febcb-108">기본 모드 기본 구성 또는 SharePoint 통합 모드 기본 구성 설치 옵션 중 하나를 선택한 경우 설치 프로그램은 최소 설정을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="febcb-108">Setup configures the minimum settings if you select either of the following installation options: Native mode default configuration or SharePoint integrated mode default configuration.</span></span> <span data-ttu-id="febcb-109">파일만 모드로 보고서 서버를 설치한 경우(설치 마법사의 **구성 없이 설치** 옵션) 서비스 계정만 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="febcb-109">If you installed the report server in files-only mode (this is the **Install but do not configure** option in the Installation wizard), only the service account is configured.</span></span> <span data-ttu-id="febcb-110">설치가 완료된 후 웹 서비스 URL과 보고서 서버 데이터베이스를 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="febcb-110">The Web service URL and report server database must be configured after Setup is finished.</span></span>  
  
 <span data-ttu-id="febcb-111">보고서 관리자는 기본 모드 보고서 서버의 선택적 기능이지만 사용자에게 보고서 서버에 대한 액세스 권한을 부여하고 보고서 서버 콘텐츠를 관리할 수 있도록 보고서 관리자를 구성하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="febcb-111">Report Manager is an optional feature for a native mode report server, but it is recommended that you configure Report Manager so that you can grant user access to the report server and manage report server content.</span></span> <span data-ttu-id="febcb-112">보고서 서버를 SharePoint 통합 모드로 배포하는 경우 SharePoint 서버의 웹 프런트 엔드를 사용하여 액세스 권한을 부여할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="febcb-112">If you deploy a report server in SharePoint integrated mode, use the Web front-end of a SharePoint server to grant access.</span></span>  
  
 <span data-ttu-id="febcb-113">필요한 경우 보고서 서버 전자 메일 및 무인 실행 계정과 같은 추가 기능을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="febcb-113">Additional features, such as report server e-mail and the unattended execution account, can be configured as needed.</span></span> <span data-ttu-id="febcb-114">자세한 내용은 [Reporting Services 기본 모드 보고서 서버 관리](manage-a-reporting-services-native-mode-report-server.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="febcb-114">For more information, see [Manage a Reporting Services Native Mode Report Server](manage-a-reporting-services-native-mode-report-server.md).</span></span>  
  
 <span data-ttu-id="febcb-115">보고서 서버를 구성하려면 Reporting Services 구성 도구를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="febcb-115">To configure a report server, use the Reporting Services Configuration tool.</span></span>  
  
### <a name="to-minimally-configure-a-report-server-installation"></a><span data-ttu-id="febcb-116">보고서 서버 설치를 최소한으로 구성하려면</span><span class="sxs-lookup"><span data-stu-id="febcb-116">To minimally configure a report server installation</span></span>  
  
1.  <span data-ttu-id="febcb-117">Reporting Services 구성 관리자를 시작한 후 보고서 서버 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="febcb-117">Start the Reporting Services Configuration Manager and connect to the report server instance.</span></span> <span data-ttu-id="febcb-118">자세한 내용은 [Reporting Services 구성 관리자&#40;기본 모드&#41;](../../sql-server/install/reporting-services-configuration-manager-native-mode.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="febcb-118">For instructions, see [Reporting Services Configuration Manager &#40;Native Mode&#41;](../../sql-server/install/reporting-services-configuration-manager-native-mode.md).</span></span>  
  
2.  <span data-ttu-id="febcb-119">**웹 서비스 URL** 을 클릭하여 보고서 서버에 대한 URL을 구성하는 페이지를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="febcb-119">Click **Web Service URL** to open the page for configuring a URL for the report server.</span></span> <span data-ttu-id="febcb-120">URL을 정의하는 방법은 [URL 구성&#40;SSRS 구성 관리자&#41;](../install-windows/configure-a-url-ssrs-configuration-manager.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="febcb-120">For instructions on how to define the URL, see [Configure a URL  &#40;SSRS Configuration Manager&#41;](../install-windows/configure-a-url-ssrs-configuration-manager.md).</span></span>  
  
3.  <span data-ttu-id="febcb-121">**데이터베이스** 를 클릭하여 보고서 서버 데이터베이스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="febcb-121">Click **Database** to create the report server database.</span></span> <span data-ttu-id="febcb-122">자세한 내용은 [기본 모드 보고서 서버 데이터베이스 만들기&#40;SSRS 구성 관리자&#41;](../install-windows/ssrs-report-server-create-a-native-mode-report-server-database.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="febcb-122">For instructions, see [Create a Native Mode Report Server Database  &#40;SSRS Configuration Manager&#41;](../install-windows/ssrs-report-server-create-a-native-mode-report-server-database.md).</span></span>  
  
4.  <span data-ttu-id="febcb-123">**웹 서비스 URL** 페이지로 돌아가 URL을 클릭하여 작동하는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="febcb-123">Go back to the **Web Service URL** page and click the URL to verify it works.</span></span>  
  
5.  <span data-ttu-id="febcb-124">"다음 단계"의 지침에 따라 배포를 완료합니다.</span><span class="sxs-lookup"><span data-stu-id="febcb-124">Follow the instructions in "Next Steps" to complete your deployment.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="febcb-125">다음 단계</span><span class="sxs-lookup"><span data-stu-id="febcb-125">Next Steps</span></span>  
 <span data-ttu-id="febcb-126">배포를 완료하려면 보고서 관리자 또는 SharePoint 통합을 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="febcb-126">To complete your deployment, you should configure Report Manager or SharePoint integration.</span></span> <span data-ttu-id="febcb-127">자세한 내용은 [보고서 관리자 구성&#40;기본 모드&#41;](configure-web-portal.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="febcb-127">For more information, see [Configure Report Manager &#40;Native Mode&#41;](configure-web-portal.md).</span></span>  
  
 <span data-ttu-id="febcb-128">Windows 방화벽을 켜면 보고서 서버에서 사용하도록 구성된 포트는 대부분 닫혀 있습니다.</span><span class="sxs-lookup"><span data-stu-id="febcb-128">If Windows Firewall is turned on, the port that the report server is configured to use is most likely closed.</span></span> <span data-ttu-id="febcb-129">원격 클라이언트 컴퓨터에서 보고서 관리자를 열 때 빈 페이지가 표시되면 포트가 닫혀 있기 때문일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="febcb-129">One indication that a port might be closed is a blank page when you attempt to open Report Manager from a remote client computer.</span></span> <span data-ttu-id="febcb-130">방화벽을 구성하는 방법은 [Configure a Firewall for Report Server Access](configure-a-firewall-for-report-server-access.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="febcb-130">For information on configuring the firewall, see [Configure a Firewall for Report Server Access](configure-a-firewall-for-report-server-access.md).</span></span>  
  
 <span data-ttu-id="febcb-131">Windows Vista 또는 Windows Server 2008을 사용 중인 경우 보고서 관리자를 로컬로 열려면 추가 단계를 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="febcb-131">If you are using Windows Vista or Windows Server 2008, additional steps are required before you can open Report Manager locally.</span></span> <span data-ttu-id="febcb-132">자세한 내용은 [로컬 관리에 대해 기본 모드 보고서 서버 구성&#40;SSRS&#41;](configure-a-native-mode-report-server-for-local-administration-ssrs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="febcb-132">For more information, see [Configure a Native Mode Report Server for Local Administration &#40;SSRS&#41;](configure-a-native-mode-report-server-for-local-administration-ssrs.md).</span></span>  
  
 <span data-ttu-id="febcb-133">폴더를 만들고 항목을 업로드하고 보고서를 실행하여 설치가 제대로 되었는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="febcb-133">Verify your installation by creating folders, uploading items, and running reports.</span></span> <span data-ttu-id="febcb-134">[Reporting Services 설치 확인](../install-windows/verify-a-reporting-services-installation.md) 의 지침에 따라 설치를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="febcb-134">Follow the instructions in [Verify a Reporting Services Installation](../install-windows/verify-a-reporting-services-installation.md) to verify your installation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="febcb-135">참고 항목</span><span class="sxs-lookup"><span data-stu-id="febcb-135">See Also</span></span>  
 <span data-ttu-id="febcb-136">[Reporting Services 기본 모드 보고서 서버 관리](manage-a-reporting-services-native-mode-report-server.md) </span><span class="sxs-lookup"><span data-stu-id="febcb-136">[Manage a Reporting Services Native Mode Report Server](manage-a-reporting-services-native-mode-report-server.md) </span></span>  
 <span data-ttu-id="febcb-137">[보고서 서버 액세스를 위한 방화벽 구성](configure-a-firewall-for-report-server-access.md) </span><span class="sxs-lookup"><span data-stu-id="febcb-137">[Configure a Firewall for Report Server Access](configure-a-firewall-for-report-server-access.md) </span></span>  
 <span data-ttu-id="febcb-138">[로컬 관리에 대해 기본 모드 보고서 서버 구성&#40;SSRS&#41;](configure-a-native-mode-report-server-for-local-administration-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="febcb-138">[Configure a Native Mode Report Server for Local Administration &#40;SSRS&#41;](configure-a-native-mode-report-server-for-local-administration-ssrs.md) </span></span>  
 <span data-ttu-id="febcb-139">[원격 관리를 위한 보고서 서버 구성](configure-a-report-server-for-remote-administration.md) </span><span class="sxs-lookup"><span data-stu-id="febcb-139">[Configure a Report Server for Remote Administration](configure-a-report-server-for-remote-administration.md) </span></span>  
 [<span data-ttu-id="febcb-140">Reporting Services 구성 관리자&#40;기본 모드&#41;</span><span class="sxs-lookup"><span data-stu-id="febcb-140">Reporting Services Configuration Manager &#40;Native Mode&#41;</span></span>](../../sql-server/install/reporting-services-configuration-manager-native-mode.md)  
  
  
