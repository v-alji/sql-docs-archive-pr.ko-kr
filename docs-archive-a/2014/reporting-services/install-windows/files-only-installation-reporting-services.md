---
title: 파일만 설치(Reporting Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- files-only installation [Reporting Services]
- installation options [Reporting Services]
ms.assetid: bdc74a8f-046c-4aa0-bfbd-4f1711dfb9ce
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 3ec5c595dce3e292d37117453ccbbc6d19f8b87d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87732428"
---
# <a name="files-only-installation-reporting-services"></a><span data-ttu-id="92eef-102">파일만 설치(Reporting Services)</span><span class="sxs-lookup"><span data-stu-id="92eef-102">Files-Only Installation (Reporting Services)</span></span>
  <span data-ttu-id="92eef-103">*파일만 설치* 는 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 프로그램 파일에 대한 폴더 구조 만들기, 디스크로 파일 복사, 로컬 컴퓨터에 보고서 서버 서비스 등록, 서비스 계정 구성, 서비스 계정에 파일 권한 부여 및 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] WMI 공급자 등록 등의 작업을 설치 프로그램에서 수행하는 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 설치를 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="92eef-103">*Files-only installation* refers to a [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] installation where Setup creates the folder structure for [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] program files, copies the files to disk, registers the Report Server service on the local computer, configures the service account, grants files permissions to the service account, and registers the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] WMI provider.</span></span>  
  
 <span data-ttu-id="92eef-104">파일만 설치에는 보고서 서버 서비스(보고서 서버 웹 서비스, 백그라운드 처리 애플리케이션 및 보고서 관리자를 호스트함), 보고서 작성기, [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 구성 도구 및 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 명령줄 유틸리티(rsconfig.exe, rskeymgmt.exe 및 rs.exe)와 같은 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 기능이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="92eef-104">A files-only installation includes the following [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] features: Report Server service (which hosts the Report Server Web service, background processing application, and Report Manager), Report Builder, the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration tool, and the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] command line utilities (rsconfig.exe, rskeymgmt.exe and rs.exe).</span></span> <span data-ttu-id="92eef-105">이 옵션은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 또는 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]와 같은 공유 기능에는 적용되지 않습니다. 따라서 공유 기능을 설치하려면 별도의 항목으로 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="92eef-105">It does not apply to shared features such as [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] or [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], which must be specified as separate items if you want to install them.</span></span>  
  
 <span data-ttu-id="92eef-106">다른 설치 모드와는 반대로 파일만 모드에서 설치되는 보고서 서버는 설치 후 작동하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="92eef-106">In contrast with other installation modes, a report server that is installed in files-only mode is not operational when Setup is finished.</span></span> <span data-ttu-id="92eef-107">보고서 서버를 온라인 상태로 만들려면 [Reporting Services 구성 관리자&#40;기본 모드&#41;](../../sql-server/install/reporting-services-configuration-manager-native-mode.md)를 사용한 추가 구성이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="92eef-107">Additional configuration will be required to bring the report server online by using the [Reporting Services Configuration Manager &#40;Native Mode&#41;](../../sql-server/install/reporting-services-configuration-manager-native-mode.md).</span></span>  
  
## <a name="when-to-select-files-only-installation-mode"></a><span data-ttu-id="92eef-108">파일만 설치 모드를 선택하는 경우</span><span class="sxs-lookup"><span data-stu-id="92eef-108">When to Select Files-Only Installation Mode</span></span>  
 <span data-ttu-id="92eef-109">다음과 같은 경우 파일만 설치를 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="92eef-109">A files-only installation must be performed when:</span></span>  
  
-   <span data-ttu-id="92eef-110">원격 보고서 서버 데이터베이스에 보고서 서버를 연결하려는 경우</span><span class="sxs-lookup"><span data-stu-id="92eef-110">You want to connect the report server to a remote report server database.</span></span>  
  
-   <span data-ttu-id="92eef-111">보고서 서버를 명명된 인스턴스로 설치하려는 경우</span><span class="sxs-lookup"><span data-stu-id="92eef-111">You want to install the report server as a named instance.</span></span>  
  
-   <span data-ttu-id="92eef-112">사용자 지정 설정 또는 기능 사용을 비롯한 배포 요구 사항이 있으며 서버 구성 시기와 방법을 완전히 제어하려는 경우</span><span class="sxs-lookup"><span data-stu-id="92eef-112">You have deployment requirements that include using custom settings or functionality, and you want full control over when and how the server is configured.</span></span>  
  
-   <span data-ttu-id="92eef-113">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 를 포함하는 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]장애 조치(Failover) 클러스터를 설치하려는 경우</span><span class="sxs-lookup"><span data-stu-id="92eef-113">Installing a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] failover cluster that includes [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span>  
  
## <a name="how-to-perform-a-files-only-installation"></a><span data-ttu-id="92eef-114">파일만 설치를 수행하는 방법</span><span class="sxs-lookup"><span data-stu-id="92eef-114">How to Perform a Files-Only Installation</span></span>  
 <span data-ttu-id="92eef-115">파일만 설치는 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]의 기본값입니다.</span><span class="sxs-lookup"><span data-stu-id="92eef-115">Files-only installation is the default for [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="92eef-116">파일만 설치는 명령줄 또는 설치 마법사를 통해 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="92eef-116">You can specify a files-only installation through the command line or in the Installation wizard.</span></span> <span data-ttu-id="92eef-117">다음 항목에서는 단계별 지침을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="92eef-117">The following topics provide step-by-step instructions:</span></span>  
  
-   <span data-ttu-id="92eef-118">설치 [마법사 &#40;설치&#41;에서 SQL Server 2014을 설치 ](../../database-engine/install-windows/install-sql-server-from-the-installation-wizard-setup.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="92eef-118">[Install SQL Server 2014 from the Installation Wizard &#40;Setup&#41;](../../database-engine/install-windows/install-sql-server-from-the-installation-wizard-setup.md).</span></span>  
  
-   <span data-ttu-id="92eef-119">[명령 프롬프트에서 SQL Server 2014을 설치](../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="92eef-119">[Install SQL Server 2014 from the Command Prompt](../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md).</span></span>  
  
#### <a name="example-command-line-script"></a><span data-ttu-id="92eef-120">명령줄 스크립트 예</span><span class="sxs-lookup"><span data-stu-id="92eef-120">Example Command Line Script</span></span>  
 <span data-ttu-id="92eef-121">의미를 명확하게 전달하기 위해 이 예에는 /RSINSTALLMODE="FilesOnlyMode"가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="92eef-121">For clarity, the example includes /RSINSTALLMODE="FilesOnlyMode".</span></span> <span data-ttu-id="92eef-122">그러나 파일만 모드는 기본값이므로 생략해도 파일만 모드 설치를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="92eef-122">However, because files-only mode is the default, you can omit this and still get a files-only mode installation.</span></span>  
  
```  
setup /q /ACTION=install /FEATURES=RS /InstanceName=MSSQLSERVER /RSSVCACCOUNT="NT AUTHORITY\NETWORK SERVICE" /RSINSTALLMODE="FilesOnlyMode"  
```  
  
#### <a name="installation-wizard"></a><span data-ttu-id="92eef-123">설치 마법사</span><span class="sxs-lookup"><span data-stu-id="92eef-123">Installation Wizard</span></span>  
 <span data-ttu-id="92eef-124">기능 선택 페이지에서 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 를 선택하면 설치 모드를 지정할 수 있는 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 구성 페이지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="92eef-124">When you select [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] in the Feature Selection page, Setup provides a [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration page that enables you to specify the installation mode.</span></span> <span data-ttu-id="92eef-125">파일만 설치를 지정하려면 **구성 페이지에서** 보고서 서버를 설치하지만 구성하지는 않습니다. [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="92eef-125">To specify a files-only installation, select **Install but do not configure the report server** on the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92eef-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="92eef-126">See Also</span></span>  
 <span data-ttu-id="92eef-127">[Reporting Services 설치 확인](verify-a-reporting-services-installation.md) </span><span class="sxs-lookup"><span data-stu-id="92eef-127">[Verify a Reporting Services Installation](verify-a-reporting-services-installation.md) </span></span>  
 <span data-ttu-id="92eef-128">[보고서 서버 서비스 계정 구성&#40;SSRS 구성 관리자&#41;](configure-the-report-server-service-account-ssrs-configuration-manager.md) </span><span class="sxs-lookup"><span data-stu-id="92eef-128">[Configure the Report Server Service Account &#40;SSRS Configuration Manager&#41;](configure-the-report-server-service-account-ssrs-configuration-manager.md) </span></span>  
 <span data-ttu-id="92eef-129">[보고서 서버 URL 구성&#40;SSRS 구성 관리자&#41;](configure-report-server-urls-ssrs-configuration-manager.md) </span><span class="sxs-lookup"><span data-stu-id="92eef-129">[Configure Report Server URLs  &#40;SSRS Configuration Manager&#41;](configure-report-server-urls-ssrs-configuration-manager.md) </span></span>  
 <span data-ttu-id="92eef-130">[SSRS Configuration Manager &#40;보고서 서버 데이터베이스 연결 구성&#41;](../../sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md) </span><span class="sxs-lookup"><span data-stu-id="92eef-130">[Configure a Report Server Database Connection  &#40;SSRS Configuration Manager&#41;](../../sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md) </span></span>  
 <span data-ttu-id="92eef-131">[Sharepoint 2010 및 sharepoint 2013 &#40;SharePoint 모드 설치 Reporting Services&#41;](install-reporting-services-sharepoint-mode.md) </span><span class="sxs-lookup"><span data-stu-id="92eef-131">[Reporting Services SharePoint Mode Installation &#40;SharePoint 2010 and SharePoint 2013&#41;](install-reporting-services-sharepoint-mode.md) </span></span>  
 <span data-ttu-id="92eef-132">[Reporting Services 기본 모드 보고서 서버 설치](install-reporting-services-native-mode-report-server.md) </span><span class="sxs-lookup"><span data-stu-id="92eef-132">[Install Reporting Services Native Mode Report Server](install-reporting-services-native-mode-report-server.md) </span></span>  
 [<span data-ttu-id="92eef-133">Reporting Services 도구</span><span class="sxs-lookup"><span data-stu-id="92eef-133">Reporting Services Tools</span></span>](../tools/reporting-services-tools.md)  
  
  
