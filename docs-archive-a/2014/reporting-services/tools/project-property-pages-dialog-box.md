---
title: 프로젝트 속성 페이지 대화 상자 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rpt.rptdesigner.projectpropertypages.general.f1
helpviewer_keywords:
- Project Property Pages dialog box
ms.assetid: 209d9e22-37fc-418f-8739-83adcf447d3f
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 6ae5ab7c68c9a95759d27ca2785f99377c98942a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87732327"
---
# <a name="project-property-pages-dialog-box"></a><span data-ttu-id="13e7b-102">프로젝트 속성 페이지 대화 상자</span><span class="sxs-lookup"><span data-stu-id="13e7b-102">Project Property Pages Dialog Box</span></span>
  <span data-ttu-id="13e7b-103">프로젝트 속성 페이지를 사용하여 보고서 서버 프로젝트의 배포 속성을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="13e7b-103">Use the project property pages to configure deployment properties for a Report Server project.</span></span> <span data-ttu-id="13e7b-104">이 대화 상자를 열려면 **프로젝트** 메뉴에서 _\<Report Project Name>_ **속성**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="13e7b-104">To open this dialog box, from the **Project** menu, click _\<Report Project Name>_**Properties**.</span></span>  
  
 <span data-ttu-id="13e7b-105">구성 속성을 정의한 후 도구 모음의 **솔루션 구성** 드롭다운 목록에서 구성을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="13e7b-105">After you define configuration properties, you can select a configuration from the **Solution Configurations** drop-down list on the toolbar.</span></span>  
  
## <a name="options"></a><span data-ttu-id="13e7b-106">옵션</span><span class="sxs-lookup"><span data-stu-id="13e7b-106">Options</span></span>  
 <span data-ttu-id="13e7b-107">**Configuration**</span><span class="sxs-lookup"><span data-stu-id="13e7b-107">**Configuration**</span></span>  
 <span data-ttu-id="13e7b-108">편집할 구성을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="13e7b-108">Select the configuration to edit.</span></span> <span data-ttu-id="13e7b-109">처음에는 **Debug**, **DebugLocal**및 **Release**의 3가지 구성을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="13e7b-109">Initially, the following configurations are available: **Debug**, **DebugLocal**, and **Release**.</span></span> <span data-ttu-id="13e7b-110">활성 구성이 첫 번째로 표시됩니다(예: **활성(디버그)**).</span><span class="sxs-lookup"><span data-stu-id="13e7b-110">The active configuration appears first, for example, **Active(Debug)**.</span></span>  
  
 <span data-ttu-id="13e7b-111">두 개 이상의 구성에 대한 속성을 동시에 보려면 **모든 구성** 또는 **여러 구성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="13e7b-111">To see properties for more than one configuration at the same time, select **All Configurations** or **Multiple Configurations**.</span></span>  
  
 <span data-ttu-id="13e7b-112">추가 구성을 만들려면 도구 모음의 **구성 관리자** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="13e7b-112">To create additional configurations, click **Configuration Manager** on the toolbar.</span></span>  
  
 <span data-ttu-id="13e7b-113">**Configuration Manager**</span><span class="sxs-lookup"><span data-stu-id="13e7b-113">**Configuration Manager**</span></span>  
 <span data-ttu-id="13e7b-114">다른 구성을 추가하거나 전체 솔루션의 구성을 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="13e7b-114">Manage configurations for the entire solution or to add additional configurations.</span></span> <span data-ttu-id="13e7b-115">자세한 내용은 설명서를 참조 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 하세요.</span><span class="sxs-lookup"><span data-stu-id="13e7b-115">For more information, see the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] documentation.</span></span>  
  
 <span data-ttu-id="13e7b-116">**OutputPath**</span><span class="sxs-lookup"><span data-stu-id="13e7b-116">**OutputPath**</span></span>  
 <span data-ttu-id="13e7b-117">보고서의 빌드 확인, 배포 및 미리 보기에 사용되는 보고서 정의를 저장할 경로를 입력하거나 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="13e7b-117">Type or paste the path to store the report definition used in build verification, deployment, and preview of reports.</span></span> <span data-ttu-id="13e7b-118">이 경로는 프로젝트에 사용하는 경로 및 프로젝트 경로 아래의 자식 폴더인 상대 경로와 달라야 합니다.</span><span class="sxs-lookup"><span data-stu-id="13e7b-118">The path must be different than the path that you use for the project and a relative path that is a child folder under the path of the project.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="13e7b-119">여러 구성을 사용하여 수행하는 태스크에 따라 경로 간을 전환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="13e7b-119">You can use multiple configurations to switch among paths depending on the task you perform.</span></span>  
  
 <span data-ttu-id="13e7b-120">**ErrorLevel**</span><span class="sxs-lookup"><span data-stu-id="13e7b-120">**ErrorLevel**</span></span>  
 <span data-ttu-id="13e7b-121">오류로 보고되는 빌드 문제의 심각도를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="13e7b-121">Type the severity of the build issues that are reported as errors.</span></span> <span data-ttu-id="13e7b-122">**ErrorLevel** 값보다 작거나 같은 심각도 수준을 가진 문제는 오류로 보고되고 그렇지 않은 문제는 경고로 보고됩니다.</span><span class="sxs-lookup"><span data-stu-id="13e7b-122">Issues with severity levels less than or equal to the value of **ErrorLevel** are reported as errors; otherwise, the issues are reported as warnings.</span></span> <span data-ttu-id="13e7b-123">오류가 발생하면 빌드 태스크가 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="13e7b-123">Any error will cause the build task to fail.</span></span> <span data-ttu-id="13e7b-124">유효한 심각도 수준은 0에서 4까지입니다.</span><span class="sxs-lookup"><span data-stu-id="13e7b-124">The valid severity levels are 0 through 4 inclusively.</span></span> <span data-ttu-id="13e7b-125">기본값은 2입니다.</span><span class="sxs-lookup"><span data-stu-id="13e7b-125">The default value is 2.</span></span>  
  
 <span data-ttu-id="13e7b-126">**StartItem**</span><span class="sxs-lookup"><span data-stu-id="13e7b-126">**StartItem**</span></span>  
 <span data-ttu-id="13e7b-127">프로젝트가 보고서 서버에 게시된 후 웹 브라우저에 표시될 보고서를 선택하거나 프로젝트를 로컬로 실행하는 경우 미리 보기 창에 표시될 보고서를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="13e7b-127">Select the report that is displayed in the Web browser after the project is published to the report server or in the preview window when the project is run locally.</span></span> <span data-ttu-id="13e7b-128">시작 항목은 프로젝트를 배포하지 않고 빌드하는 구성과 **디버그** 명령(**F5**)을 사용하는 경우 반드시 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="13e7b-128">A start item is required for configurations that build but do not deploy the project and for using the **Debug** command (**F5**).</span></span> <span data-ttu-id="13e7b-129">프로젝트를 배포하는 구성에서는 필수입니다.</span><span class="sxs-lookup"><span data-stu-id="13e7b-129">It is required for configurations that deploy the project.</span></span>  
  
 <span data-ttu-id="13e7b-130">**OverwriteDataSources**</span><span class="sxs-lookup"><span data-stu-id="13e7b-130">**OverwriteDataSources**</span></span>  
 <span data-ttu-id="13e7b-131">보고서가 게시될 때 서버의 데이터 원본을 프로젝트의 데이터 원본으로 덮어쓰려면 **True** 를 선택하고,</span><span class="sxs-lookup"><span data-stu-id="13e7b-131">Select **True** to overwrite the data source on the server with the data source in the project when the reports are published.</span></span> <span data-ttu-id="13e7b-132">서버의 기존 데이터 원본을 그대로 두려면 **False** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="13e7b-132">Select **False** to leave the existing data source on the server.</span></span>  
  
 <span data-ttu-id="13e7b-133">**TargetServerVersion**</span><span class="sxs-lookup"><span data-stu-id="13e7b-133">**TargetServerVersion**</span></span>  
 <span data-ttu-id="13e7b-134">[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]또는 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] 버전의를 선택 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 하거나 **버전 검색** 을 선택 하 여 **TargetServer URL** 속성으로 식별 되는 서버에 설치 된 버전을 자동으로 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="13e7b-134">Select either the [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] or [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] version of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] or select **Detect Version** to automatically determine the version installed on the server identified by the **TargetServer URL** property.</span></span> <span data-ttu-id="13e7b-135">기본값은 **SQL Server 2008 R2**입니다.</span><span class="sxs-lookup"><span data-stu-id="13e7b-135">The default value is **SQL Server 2008 R2**.</span></span>  
  
 <span data-ttu-id="13e7b-136">**TargetDataSourceFolder**</span><span class="sxs-lookup"><span data-stu-id="13e7b-136">**TargetDataSourceFolder**</span></span>  
 <span data-ttu-id="13e7b-137">게시된 공유 데이터 원본을 저장할 폴더의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="13e7b-137">The name of the folder in which to store the published shared data sources.</span></span> <span data-ttu-id="13e7b-138">폴더를 지정하지 않는 경우 데이터 원본은 보고서와 같은 폴더에 게시됩니다.</span><span class="sxs-lookup"><span data-stu-id="13e7b-138">If you do not specify a folder, the data source is published to the same folder as the report.</span></span> <span data-ttu-id="13e7b-139">보고서 서버에 폴더가 없는 경우 보고서가 게시될 때 보고서 디자이너에서 폴더를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="13e7b-139">If the folder does not exist on the report server, Report Designer creates the folder when the reports are published.</span></span>  
  
 <span data-ttu-id="13e7b-140">기본 모드로 실행 중인 보고서 서버에 게시하는 경우 루트로 시작되는 폴더 계층의 전체 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="13e7b-140">When publishing to a report server running in native mode, specify the full path of the folder hierarchy starting at the root.</span></span> <span data-ttu-id="13e7b-141">Folder1/Folder2/Folder3).</span><span class="sxs-lookup"><span data-stu-id="13e7b-141">For example, Folder1/Folder2/Folder3.</span></span>  
  
 <span data-ttu-id="13e7b-142">SharePoint 통합 모드로 실행 중인 보고서 서버에 게시하는 경우 SharePoint 라이브러리에 대한 URL을 사용합니다(예:</span><span class="sxs-lookup"><span data-stu-id="13e7b-142">When publishing to a report server running in SharePoint integrated mode, use a URL to the SharePoint library.</span></span> <span data-ttu-id="13e7b-143">예를 들어 http:// *\<servername>/\<site>* /Documents/myfolder.</span><span class="sxs-lookup"><span data-stu-id="13e7b-143">For example, http://*\<servername>/\<site>*/Documents/MyFolder.</span></span>  
  
 <span data-ttu-id="13e7b-144">**TargetReportFolder**</span><span class="sxs-lookup"><span data-stu-id="13e7b-144">**TargetReportFolder**</span></span>  
 <span data-ttu-id="13e7b-145">게시된 보고서를 저장할 폴더의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="13e7b-145">The name of the folder in which to store the published reports.</span></span> <span data-ttu-id="13e7b-146">기본적으로 보고서 프로젝트의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="13e7b-146">By default, this is the name of the report project.</span></span> <span data-ttu-id="13e7b-147">보고서 서버에 폴더가 없는 경우 보고서가 게시될 때 보고서 디자이너에서 폴더를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="13e7b-147">If the folder does not exist on the report server, Report Designer creates the folder when the reports are published.</span></span>  
  
 <span data-ttu-id="13e7b-148">기본 모드로 실행 중인 보고서 서버에 게시하는 경우 루트로 시작되는 폴더 계층의 전체 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="13e7b-148">When publishing to a report server running in native mode, specify the full path of the folder hierarchy starting at the root.</span></span> <span data-ttu-id="13e7b-149">폴더가 다른 폴더 안에 있는 경우 루트로 시작되는 폴더 경로를 입력합니다(예: Folder1/Folder2/Folder3).</span><span class="sxs-lookup"><span data-stu-id="13e7b-149">If a folder is located within another folder, include a path to the folder starting at the root, such as Folder1/Folder2/Folder3.</span></span>  
  
 <span data-ttu-id="13e7b-150">SharePoint 통합 모드로 실행 중인 보고서 서버에 게시하는 경우 SharePoint 라이브러리에 대한 URL을 사용합니다(예:</span><span class="sxs-lookup"><span data-stu-id="13e7b-150">When publishing to a report server running in SharePoint integrated mode, use a URL to SharePoint library.</span></span> <span data-ttu-id="13e7b-151">예를 들어 http:// *\<servername>* / *\<site>* /documents/myfolder.</span><span class="sxs-lookup"><span data-stu-id="13e7b-151">For example, http://*\<servername>*/*\<site>*/Documents/MyFolder.</span></span>  
  
 <span data-ttu-id="13e7b-152">**TargetServerURL**</span><span class="sxs-lookup"><span data-stu-id="13e7b-152">**TargetServerURL**</span></span>  
 <span data-ttu-id="13e7b-153">대상 보고서 서버의 URL입니다.</span><span class="sxs-lookup"><span data-stu-id="13e7b-153">The URL of the target report server.</span></span> <span data-ttu-id="13e7b-154">보고서를 게시하기 전에 이 속성을 유효한 보고서 서버 URL로 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="13e7b-154">Before you publish a report, you must set this property to a valid report server URL.</span></span>  
  
 <span data-ttu-id="13e7b-155">기본 모드로 실행 중인 보고서 서버에 게시하는 경우 보고서 서버의 가상 디렉터리 URL을 사용합니다(예:</span><span class="sxs-lookup"><span data-stu-id="13e7b-155">When publishing to a report server running in native mode, use the URL of the virtual directory of the report server.</span></span> <span data-ttu-id="13e7b-156">예: http:// \<server> /reportserver</span><span class="sxs-lookup"><span data-stu-id="13e7b-156">For example, http://\<server>/reportserver.</span></span> <span data-ttu-id="13e7b-157">이는 보고서 관리자가 아닌 보고서 서버의 가상 디렉터리입니다.</span><span class="sxs-lookup"><span data-stu-id="13e7b-157">This is the virtual directory of the report server, not Report Manager.</span></span> <span data-ttu-id="13e7b-158">기본적으로 보고서 서버는 "reportserver"라는 가상 디렉터리에 설치되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="13e7b-158">By default, the report server is installed in a virtual directory named "reportserver".</span></span>  
  
 <span data-ttu-id="13e7b-159">SharePoint 통합 모드로 실행 중인 보고서 서버에 게시하는 경우 SharePoint 최상위 사이트나 하위 사이트에 대한 URL을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="13e7b-159">When publishing to a report server running in SharePoint integrated mode, use a URL to a SharePoint top-level site or subsite.</span></span> <span data-ttu-id="13e7b-160">사이트를 지정하지 않으면 기본 최상위 사이트가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="13e7b-160">If you do not specify a site, the default top-level site is used.</span></span> <span data-ttu-id="13e7b-161">예: http:// \<*servername> *, http://<* servername */\<*site>* 또는 http:// \<*servername> */\<*site>* / \<*subsite> \*.</span><span class="sxs-lookup"><span data-stu-id="13e7b-161">For example, http://\<*servername>*, http://<* servername*/\<*site>* or http://\<*servername>*/\<*site>*/\<*subsite>\*.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13e7b-162">참고 항목</span><span class="sxs-lookup"><span data-stu-id="13e7b-162">See Also</span></span>  
 <span data-ttu-id="13e7b-163">[보고서 게시](../publish-reports.md) </span><span class="sxs-lookup"><span data-stu-id="13e7b-163">[Publish Reports](../publish-reports.md) </span></span>  
 <span data-ttu-id="13e7b-164">[SharePoint 라이브러리에 보고서 게시](../reports/publish-a-report-to-a-sharepoint-library.md) </span><span class="sxs-lookup"><span data-stu-id="13e7b-164">[Publish a Report to a SharePoint Library](../reports/publish-a-report-to-a-sharepoint-library.md) </span></span>  
 <span data-ttu-id="13e7b-165">[배포 속성 &#40;Reporting Services&#41;설정](set-deployment-properties-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="13e7b-165">[Set Deployment Properties &#40;Reporting Services&#41;](set-deployment-properties-reporting-services.md) </span></span>  
 [<span data-ttu-id="13e7b-166">보고서 디자이너 F1 도움말</span><span class="sxs-lookup"><span data-stu-id="13e7b-166">Report Designer F1 Help</span></span>](report-designer-f1-help.md)  
  
  
