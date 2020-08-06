---
title: Reporting Services 설치 확인 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- checking report server installations
- verifying report server installations
- Report Designer [Reporting Services], verifying installations
- installing Reporting Services, verifying installations
- Report Manager [Reporting Services], verifying installations
- report servers [Reporting Services], verifying installations
- Setup [Reporting Services], verifying installations
ms.assetid: 82a51a99-66f0-4b0c-b05b-07d22387adb0
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 5b90f997f99cfc9d3f8625eb4e08d193af52d7f6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639394"
---
# <a name="verify-a-reporting-services-installation"></a><span data-ttu-id="5801d-102">Reporting Services 설치 확인</span><span class="sxs-lookup"><span data-stu-id="5801d-102">Verify a Reporting Services Installation</span></span>
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="5801d-103">보고서 서버는 기본 모드 또는 SharePoint 모드 중 하나로 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5801d-103">report servers can be installed in one of two modes, Native or SharePoint.</span></span> <span data-ttu-id="5801d-104">설치를 확인하기 위해 수행해야 하는 단계는 보고서 서버 모드에 따라 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="5801d-104">The steps you should follow for verifying the installation depend on the report server mode.</span></span>  
  
 <span data-ttu-id="5801d-105">이 항목에는 다음과 같은 정보가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5801d-105">This topic contains the following information:</span></span>  
  
-   [<span data-ttu-id="5801d-106">SharePoint 모드 설치 확인</span><span class="sxs-lookup"><span data-stu-id="5801d-106">Verify SharePoint Mode Installation</span></span>](#bkmk_sharepointmode)  
  
-   [<span data-ttu-id="5801d-107">기본 모드 설치 확인</span><span class="sxs-lookup"><span data-stu-id="5801d-107">Verify a Native Mode Installation</span></span>](#bkmk_nativemode)  
  
##  <a name="verify-sharepoint-mode-installation"></a><a name="bkmk_sharepointmode"></a> <span data-ttu-id="5801d-108">SharePoint 모드 설치 확인</span><span class="sxs-lookup"><span data-stu-id="5801d-108">Verify SharePoint Mode Installation</span></span>  
  
#### <a name="to-verify-the-reporting-services-service"></a><span data-ttu-id="5801d-109">Reporting Services 서비스를 확인하려면</span><span class="sxs-lookup"><span data-stu-id="5801d-109">To verify the Reporting Services Service</span></span>  
  
1.  <span data-ttu-id="5801d-110">SharePoint 중앙 관리의 **시스템 설정** 그룹에서 **서버의 서비스 관리** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5801d-110">From SharePoint central administration, click **Manage services on server** in the **System Settings** group.</span></span>  
  
2.  <span data-ttu-id="5801d-111">**SQL Server Reporting Services 서비스** 가 설치되어 있고 **실행 중** 상태인지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="5801d-111">Verify the **SQL Server Reporting Services Service** is installed and in the **Running** state.</span></span>  
  
     <span data-ttu-id="5801d-112">목록에 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 서비스가 표시되지 않으면 해당 서비스가 설치되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="5801d-112">If you do not see the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service in the list, verify the service is installed.</span></span> <span data-ttu-id="5801d-113">자세한 내용은 sharepoint [2010에 대 한 Reporting Services Sharepoint 모드 설치](../../sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md)의 "Reporting Services Sharepoint 서비스 설치 및 시작" 섹션을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="5801d-113">For more information, see the "Install and start the Reporting Services SharePoint Service" section of [Install Reporting Services SharePoint Mode for SharePoint 2010](../../sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md).</span></span>  
  
#### <a name="to-verify-the-service-application"></a><span data-ttu-id="5801d-114">서비스 애플리케이션을 확인하려면</span><span class="sxs-lookup"><span data-stu-id="5801d-114">To verify the Service Application</span></span>  
  
1.  <span data-ttu-id="5801d-115">중앙 관리에서 적어도 하나의 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 서비스 애플리케이션이 있는지 확인하려면 **애플리케이션 관리** 그룹에서 **서비스 애플리케이션 관리** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5801d-115">To verify from Central Administration you have at least one [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service application, click **Manage Service Applications** in the **Application Management** group.</span></span>  
  
2.  <span data-ttu-id="5801d-116">**SQL Server Reporting Services 서비스 애플리케이션** 유형의 서비스 애플리케이션과 해당 애플리케이션 프록시가 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="5801d-116">Verify there is a service application of type **SQL Server Reporting Services Service Application** and a corresponding application proxy.</span></span>  
  
3.  <span data-ttu-id="5801d-117">서비스 애플리케이션 이름 **근처** 를 클릭한 다음 SharePoint 도구 모음에서 **속성** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5801d-117">Click **near** the name of the service application and then click **Properties** in the SharePoint toolbar.</span></span>  <span data-ttu-id="5801d-118">서비스 애플리케이션 이름을 클릭하면 서비스 애플리케이션의 속성 페이지가 아닌 관리 페이지가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="5801d-118">If you click the name of the service application it will open the Management pages of the service application, not the properties page.</span></span>  
  
4.  <span data-ttu-id="5801d-119">원하는 웹 애플리케이션을 가리키기 위해 **웹 애플리케이션 연결** 이 구성되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="5801d-119">Verify the **Web Application Association** is configured to point to the desired web application.</span></span>  
  
#### <a name="to-verify-the-site-collection-feature"></a><span data-ttu-id="5801d-120">사이트 모음 기능을 확인하려면</span><span class="sxs-lookup"><span data-stu-id="5801d-120">To verify the Site collection Feature</span></span>  
  
1.  <span data-ttu-id="5801d-121">사이트 설정의 **사이트 모음 관리** 그룹에서 **사이트 모음 기능** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5801d-121">In site settings, click **Site collection Features** in the **Site Collection Administration** group.</span></span>  
  
2.  <span data-ttu-id="5801d-122">**보고서 서버 통합 기능** 이 활성 상태인지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="5801d-122">Verify the **Report Server Integration Feature** is active.</span></span>  
  
#### <a name="to-verify-reporting-server-content-types"></a><span data-ttu-id="5801d-123">보고 서버 내용 유형을 확인하려면</span><span class="sxs-lookup"><span data-stu-id="5801d-123">To Verify Reporting Server content types</span></span>  
  
1.  <span data-ttu-id="5801d-124">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]보고서 서버 콘텐츠 형식을 확인 하거나 추가 하려면 [SharePoint 통합 모드&#41;에서 &#40;Reporting Services 라이브러리에 보고서 서버 콘텐츠 형식 추가 ](../add-reporting-services-content-types-to-a-sharepoint-library.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="5801d-124">To verify or add [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] report server content types, see [Add Report Server Content Types to a Library &#40;Reporting Services in SharePoint Integrated Mode&#41;](../add-reporting-services-content-types-to-a-sharepoint-library.md).</span></span>  
  
#### <a name="to-verify-you-can-launch-report-builder"></a><span data-ttu-id="5801d-125">보고서 작성기를 실행할 수 있는지 확인하려면</span><span class="sxs-lookup"><span data-stu-id="5801d-125">To verify you can launch Report Builder</span></span>  
  
1.  <span data-ttu-id="5801d-126">문서 라이브러리의 SharePoint 리본에서 **문서** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5801d-126">From a document library, click **Documents** in the SharePoint ribbon.</span></span>  
  
2.  <span data-ttu-id="5801d-127">**새 문서** 를 클릭하고 **보고서 작성기 보고서**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5801d-127">Click **New Document** and click **Report Builder Report**.</span></span> <span data-ttu-id="5801d-128">이 옵션이 표시되지 않으면 라이브러리에 보고서 서버 내용 유형을 추가하는 방법에 대한 이전 절차를 검토하세요.</span><span class="sxs-lookup"><span data-stu-id="5801d-128">If you do not see this option, review the previous procedure on adding the report server content types to a library.</span></span>  
  
#### <a name="create-a-basic-report"></a><span data-ttu-id="5801d-129">기본 보고서 만들기</span><span class="sxs-lookup"><span data-stu-id="5801d-129">Create a basic report</span></span>  
  
1.  <span data-ttu-id="5801d-130">SharePoint 문서 라이브러리에서 텍스트 상자(예: 제목)만 포함된 기본 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 보고서를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="5801d-130">In a SharePoint document library, create a basic [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] report that only contains a text box, for example a title.</span></span> <span data-ttu-id="5801d-131">이 보고서에는 어떠한 데이터 원본 또는 데이터 세트도 포함되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5801d-131">The report does not contain any data sources or datasets.</span></span> <span data-ttu-id="5801d-132">이 보고서의 목적은 보고서 작성기를 열고 기본 보고서를 미리 볼 수 있는지 확인하기 위한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="5801d-132">The goal is to verify you can open Report Builder and a basic report will preview.</span></span>  
  
2.  <span data-ttu-id="5801d-133">보고서를 문서 라이브러리에 저장하고 라이브러리에서 보고서를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="5801d-133">Save the report to the document library and the run the report from the library.</span></span> <span data-ttu-id="5801d-134">보고서 작성기로 보고서를 만드는 방법은 [보고서 작성기 시작(보고서 작성기)](https://technet.microsoft.com/library/ms159221.aspx)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5801d-134">For more information on creating reports with Report Builder, see [Start Report Builder (Report Builder)](https://technet.microsoft.com/library/ms159221.aspx).</span></span>  
  
#### <a name="reporting-services-samples"></a><span data-ttu-id="5801d-135">Reporting Services 예제</span><span class="sxs-lookup"><span data-stu-id="5801d-135">Reporting Services samples</span></span>  
  
1.  <span data-ttu-id="5801d-136">Reporting Services 자습서 중 하나를 완료합니다.</span><span class="sxs-lookup"><span data-stu-id="5801d-136">Complete one of the Reporting Services tutorials.</span></span> <span data-ttu-id="5801d-137">자세한 내용은 [Reporting Services 자습서&#40;SSRS&#41;](../reporting-services-tutorials-ssrs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5801d-137">For more information, see [Reporting Services Tutorials &#40;SSRS&#41;](../reporting-services-tutorials-ssrs.md).</span></span>  
  
2.  <span data-ttu-id="5801d-138">Adventure Works 예제 데이터베이스 및 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 예제 보고서를 CodePlex에서 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="5801d-138">Download the Adventure works sample database and the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] sample reports from CodePlex.</span></span> <span data-ttu-id="5801d-139">자세한 내용은 [AdventureWorks 보고서 예제](https://msftrsprodsamples.codeplex.com/wikipage?title=SS2012!AdventureWorks2012%20Report%20Samples&referringTitle=Home)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5801d-139">For more information, see [AdventureWorks Report Samples](https://msftrsprodsamples.codeplex.com/wikipage?title=SS2012!AdventureWorks2012%20Report%20Samples&referringTitle=Home).</span></span>  
  
##  <a name="verify-a-native-mode-installation"></a><a name="bkmk_nativemode"></a> <span data-ttu-id="5801d-140">기본 모드 설치 확인</span><span class="sxs-lookup"><span data-stu-id="5801d-140">Verify a Native Mode Installation</span></span>  
 <span data-ttu-id="5801d-141">기본 구성을 사용하여 기본 모드 보고서 서버를 설치하는 경우 설치 프로그램은 서버를 설치하고 배포합니다.</span><span class="sxs-lookup"><span data-stu-id="5801d-141">When you install a Native mode report server using the default configuration, Setup installs and deploys the server.</span></span> <span data-ttu-id="5801d-142">몇 가지 간단한 테스트를 수행하여 보고서 서버의 배포 여부를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5801d-142">You can verify whether Setup deployed the report server by performing a few simple tests.</span></span> <span data-ttu-id="5801d-143">이러한 단계를 수행하기 위해서는 로컬 관리자여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5801d-143">You must be a local administrator to perform these steps.</span></span> <span data-ttu-id="5801d-144">다른 사용자가 테스트를 수행할 수 있도록 하려면 해당 사용자에 대한 보고서 서버 액세스 권한을 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5801d-144">To enable other users to perform testing, you must configure report server access for those users.</span></span>  
  
#### <a name="to-verify-that-the-report-server-is-installed-and-running"></a><span data-ttu-id="5801d-145">보고서 서버가 설치되어 실행 중인지 확인하려면</span><span class="sxs-lookup"><span data-stu-id="5801d-145">To verify that the report server is installed and running</span></span>  
  
1.  <span data-ttu-id="5801d-146">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 구성 도구를 실행하고 방금 설치한 보고서 서버 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="5801d-146">Run the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration tool and connect to the report server instance you just installed.</span></span> <span data-ttu-id="5801d-147">웹 서비스 URL 페이지에는 보고서 서버 웹 서비스에 대한 링크가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5801d-147">The Web Service URL page includes a link to the Report Server Web service.</span></span> <span data-ttu-id="5801d-148">이 링크를 클릭하면 서버에 액세스할 수 있는지 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5801d-148">Click the link to verify you can access the server.</span></span> <span data-ttu-id="5801d-149">보고서 서버 데이터베이스가 구성되어 있지 않으면 링크를 클릭하기 전에 먼저 보고서 서버 데이터베이스를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="5801d-149">If the report server database is not configured, do that first before clicking the link.</span></span>  
  
2.  <span data-ttu-id="5801d-150">서비스 콘솔 애플리케이션을 열고 보고서 서버 서비스가 실행 중인지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="5801d-150">Open the Services console applications and verify that the Report Server service is running.</span></span> <span data-ttu-id="5801d-151">보고서 서버 서비스의 상태를 확인하려면 **시작**을 클릭하고 **제어판**을 가리킨 후 **관리 도구**를 두 번 클릭하고 **서비스**를 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5801d-151">To view the status of the Report Server service, click **Start**, point to **Control Panel**, double-click **Administrative Tools**, and then double-click **Services**.</span></span> <span data-ttu-id="5801d-152">서비스 목록이 나타나면 **보고서 서버(MSSQLSERVER)** 로 스크롤합니다.</span><span class="sxs-lookup"><span data-stu-id="5801d-152">When the list of services appears, scroll to **Report Server (MSSQLSERVER)**.</span></span> <span data-ttu-id="5801d-153">상태가 **시작됨**으로 바뀝니다.</span><span class="sxs-lookup"><span data-stu-id="5801d-153">The status should be **Started**.</span></span>  
  
3.  <span data-ttu-id="5801d-154">브라우저를 열고 주소 표시줄에 보고서 서버 URL을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="5801d-154">Open a browser and type the report server URL in the address bar.</span></span> <span data-ttu-id="5801d-155">주소는 설치 중에 보고서 서버에 지정한 서버 이름과 가상 디렉터리 이름으로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="5801d-155">The address consists of the server name and the virtual directory name that you specified for the report server during setup.</span></span> <span data-ttu-id="5801d-156">기본적으로 보고서 서버 가상 디렉터리 이름은 **ReportServer**입니다.</span><span class="sxs-lookup"><span data-stu-id="5801d-156">By default, the report server virtual directory is named **ReportServer**.</span></span> <span data-ttu-id="5801d-157">다음 URL을 사용 하 여 보고서 서버 설치를 확인할 수 있습니다. http:// *\<computer name>* /Reportserver *\<_instance name>*</span><span class="sxs-lookup"><span data-stu-id="5801d-157">You can use the following URL to verify report server installation: http://*\<computer name>*/ReportServer*\<_instance name>*.</span></span> <span data-ttu-id="5801d-158">보고서 서버를 명명된 인스턴스로 설치한 경우 URL이 달라질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5801d-158">The URL will be different if you installed the report server as a named instance.</span></span> <span data-ttu-id="5801d-159">URL 형식에 대한 자세한 내용은 [보고서 서버 URL 구성&#40;SSRS 구성 관리자&#41;](configure-report-server-urls-ssrs-configuration-manager.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5801d-159">For more information about the URL format, see [Configure Report Server URLs  &#40;SSRS Configuration Manager&#41;](configure-report-server-urls-ssrs-configuration-manager.md).</span></span> <span data-ttu-id="5801d-160">Windows Vista 또는 Windows Server 2008의 로컬 관리자인 경우 [로컬 관리에 대해 기본 모드 보고서 서버 구성&#40;SSRS&#41;](../report-server/configure-a-native-mode-report-server-for-local-administration-ssrs.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5801d-160">If you are a local administrator on Windows Vista or Windows Server 2008, see [Configure a Native Mode Report Server for Local Administration &#40;SSRS&#41;](../report-server/configure-a-native-mode-report-server-for-local-administration-ssrs.md).</span></span>  
  
4.  <span data-ttu-id="5801d-161">보고서를 실행하여 보고서 서버 작동을 테스트합니다.</span><span class="sxs-lookup"><span data-stu-id="5801d-161">Run reports to test report server operations.</span></span> <span data-ttu-id="5801d-162">이 단계에서는 자습서에서 샘플 보고서를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5801d-162">For this step, you can create a sample report from a tutorial.</span></span> <span data-ttu-id="5801d-163">자세한 내용은 [기본 테이블 보고서 만들기&#40;SSRS 자습서&#41;](../create-a-basic-table-report-ssrs-tutorial.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5801d-163">For more information, see [Create a Basic Table Report &#40;SSRS Tutorial&#41;](../create-a-basic-table-report-ssrs-tutorial.md).</span></span>  
  
#### <a name="to-verify-that-report-manager-is-installed-and-running"></a><span data-ttu-id="5801d-164">보고서 관리자가 설치되어 실행 중인지 확인하려면</span><span class="sxs-lookup"><span data-stu-id="5801d-164">To verify that Report Manager is installed and running</span></span>  
  
1.  <span data-ttu-id="5801d-165">브라우저를 열고 주소 표시줄에 보고서 관리자 URL을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="5801d-165">Open a browser and type the Report Manager URL in the address bar.</span></span> <span data-ttu-id="5801d-166">주소는 설치 중에 또는 Reporting Services 구성 도구의 보고서 관리자 URL 페이지에서 보고서 관리자에 대해 지정한 서버 이름과 가상 디렉터리 이름으로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="5801d-166">The address consists of the server name and the virtual directory name that you specified for the Report Manager during setup or in the Report Manager URL page in the Reporting Services Configuration tool.</span></span> <span data-ttu-id="5801d-167">기본적으로 보고서 관리자 가상 디렉터리는 **Reports**입니다.</span><span class="sxs-lookup"><span data-stu-id="5801d-167">By default, the Report Manager virtual directory is **Reports**.</span></span> <span data-ttu-id="5801d-168">URL</span><span class="sxs-lookup"><span data-stu-id="5801d-168">You can use the following URL to verify Report Manager installation:</span></span>  
  
     <span data-ttu-id="5801d-169">http:// *\<computer name>* /Reports *\<_instance name>* .</span><span class="sxs-lookup"><span data-stu-id="5801d-169">http://*\<computer name>*/Reports*\<_instance name>*.</span></span>  
  
2.  <span data-ttu-id="5801d-170">보고서 관리자에서 새 폴더를 만들거나 파일을 업로드하여 보고서 서버 데이터베이스로 정의가 다시 전달되었는지 여부를 테스트합니다.</span><span class="sxs-lookup"><span data-stu-id="5801d-170">Use Report Manager to create a new folder or upload a file to test whether definitions are passed back to the report server database.</span></span> <span data-ttu-id="5801d-171">이런 작업이 성공적으로 수행되면 연결 기능이 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="5801d-171">If these operations are successful, the connection is functional.</span></span>  
  
     <span data-ttu-id="5801d-172">자세한 내용은 [보고서 관리자&#40;SSRS 기본 모드&#41;](../report-manager-ssrs-native-mode.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5801d-172">For more information, see [Report Manager  &#40;SSRS Native Mode&#41;](../report-manager-ssrs-native-mode.md).</span></span>  
  
#### <a name="to-verify-that-report-designer-is-installed-and-running"></a><span data-ttu-id="5801d-173">보고서 디자이너가 설치되어 실행 중인지 확인하려면</span><span class="sxs-lookup"><span data-stu-id="5801d-173">To verify that Report Designer is installed and running</span></span>  
  
1.  <span data-ttu-id="5801d-174">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]를 열고 보고서 서버 프로젝트 유형을 기반으로 새 프로젝트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="5801d-174">Open [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], and create a new project based on a Report Server project type.</span></span> <span data-ttu-id="5801d-175">보고서 서버 프로젝트 마법사를 사용하는 방법은 SQL Server 온라인 설명서의 [SQL Server Data Tools의 Reporting Services&#40;SSDT&#41;](../tools/reporting-services-in-sql-server-data-tools-ssdt.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5801d-175">For more information on using the Report Server Project Wizard, see [Reporting Services in SQL Server Data Tools &#40;SSDT&#41;](../tools/reporting-services-in-sql-server-data-tools-ssdt.md) in SQL Server Books Online.</span></span>  
  
2.  <span data-ttu-id="5801d-176">보고서 예제를 설치한 경우 예제 보고서 프로젝트 파일을 열고 해당 보고서를 보고서 서버에 게시합니다.</span><span class="sxs-lookup"><span data-stu-id="5801d-176">If you installed report samples, open the sample report project files and publish the reports to a report server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5801d-177">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5801d-177">See Also</span></span>  
 <span data-ttu-id="5801d-178">[Reporting Services 설치 문제 해결](troubleshoot-a-reporting-services-installation.md) </span><span class="sxs-lookup"><span data-stu-id="5801d-178">[Troubleshoot a Reporting Services Installation](troubleshoot-a-reporting-services-installation.md) </span></span>  
 [<span data-ttu-id="5801d-179">Reporting Services 오류의 원인 및 해결 방법</span><span class="sxs-lookup"><span data-stu-id="5801d-179">Cause and Resolution of Reporting Services Errors</span></span>](../troubleshooting/cause-and-resolution-of-reporting-services-errors.md)  
  
  
