---
title: SharePoint 라이브러리에 보고서 게시 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- deploying [Reporting Services], reports in SharePoint integrated mode
- SharePoint integration [Reporting Services], publishing to a library
- publishing reports [Reporting Services], to a SharePoint library
ms.assetid: 3f6dfc28-50d8-4231-bd25-871b5f77cce6
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 23b74ffb04bf1e13523dcf6ec5d774089d80f73b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87729047"
---
# <a name="publish-a-report-to-a-sharepoint-library"></a><span data-ttu-id="e4c6d-102">SharePoint 라이브러리에 보고서 게시</span><span class="sxs-lookup"><span data-stu-id="e4c6d-102">Publish a Report to a SharePoint Library</span></span>
  <span data-ttu-id="e4c6d-103">SharePoint 통합용으로 구성된 SharePoint 사이트에 보고서를 게시하려면 보고서 디자이너에서 프로젝트 속성을 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e4c6d-103">To publish a report to a SharePoint site configured for SharePoint integration, you must set the project properties in Report Designer.</span></span> <span data-ttu-id="e4c6d-104">프로젝트 속성에서 서버, 보고서 및 공유 데이터 원본에 대한 모든 참조는 정규화된 URL이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e4c6d-104">In the project properties, all references to servers, reports, and shared data sources must be fully qualified URLs.</span></span> <span data-ttu-id="e4c6d-105">보고서 정의에서 하위 보고서, 드릴스루 보고서 및 리소스(예: 웹 기반 이미지)에 대한 모든 참조는 정규화된 URL이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e4c6d-105">In the report definition, all references to subreports, drillthrough reports, and resources such as Web-based images, must be fully qualified URLS.</span></span>  
  
 <span data-ttu-id="e4c6d-106">프로젝트의 속성을 설정하려면 SharePoint 사이트에 대한 **멤버** 또는 **소유자** 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e4c6d-106">You must have **Member** or **Owner** permission on the SharePoint site to set the properties on the project.</span></span> <span data-ttu-id="e4c6d-107">자세한 내용은 [SharePoint 모드의 보고서 서버에 게시된 보고서 항목에 대한 URL 예&#40;SSRS&#41;](../tools/url-examples-for-items-on-a-report-server-sharepoint-mode.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e4c6d-107">For more information, see [URL Examples for Published Report Items on a Report Server in SharePoint Mode &#40;SSRS&#41;](../tools/url-examples-for-items-on-a-report-server-sharepoint-mode.md).</span></span>  
  
### <a name="to-publish-a-report-to-a-sharepoint-site"></a><span data-ttu-id="e4c6d-108">보고서를 SharePoint 사이트에 게시하려면</span><span class="sxs-lookup"><span data-stu-id="e4c6d-108">To publish a report to a SharePoint site</span></span>  
  
1.  <span data-ttu-id="e4c6d-109">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]에서 기존 또는 새로운 보고서 서버 프로젝트를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="e4c6d-109">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open an existing or new Report Server project.</span></span>  
  
2.  <span data-ttu-id="e4c6d-110">**프로젝트** 메뉴에서 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e4c6d-110">From the **Project** menu, click **Properties**.</span></span> <span data-ttu-id="e4c6d-111">_\<project>_ **속성 페이지** 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="e4c6d-111">The _\<project>_**Property Pages** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="e4c6d-112">**구성** 목록에서 보고서를 작성 및 게시하는 데 사용할 솔루션 빌드 구성의 이름을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e4c6d-112">In the **Configuration** list, select the name of a solution build configuration to use to build and publish your report.</span></span> <span data-ttu-id="e4c6d-113">현재 구성이 **활성**()으로 나열 됩니다 *\<configuration>* .</span><span class="sxs-lookup"><span data-stu-id="e4c6d-113">The current configuration is listed as **Active**(*\<configuration>*).</span></span>  
  
4.  <span data-ttu-id="e4c6d-114">프로젝트의 공유 데이터 원본을 게시하고 이전에 게시된 공유 데이터 원본을 덮어쓰려면 **OverwriteDataSources** 를 **True**로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="e4c6d-114">If you want to publish the shared data sources in your project and overwrite previously published shared data sources, set **OverwriteDataSources** to **True**.</span></span>  
  
5.  <span data-ttu-id="e4c6d-115">필드 **Targetdatasourcefolder**에 SharePoint 라이브러리 또는 라이브러리 폴더에 대 한 URL을 입력 합니다 (예:) *http://TestServer/TestSite/Documents/DataSources)* .</span><span class="sxs-lookup"><span data-stu-id="e4c6d-115">(Optional) For **TargetDataSourceFolder**, type a URL to a SharePoint library or library folder (for example, *http://TestServer/TestSite/Documents/DataSources)*.</span></span>  
  
     <span data-ttu-id="e4c6d-116">값을 지정하지 않으면 **TargetReportFolder** 값이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="e4c6d-116">If you do not specify a value, the **TargetReportFolder** value is used.</span></span>  
  
6.  <span data-ttu-id="e4c6d-117">**Targetreportfolder**에 라이브러리 또는 라이브러리 폴더에 대 한 URL을 입력 합니다 (예:) *http://TestServer/TestSite/Documents/Reports)* .</span><span class="sxs-lookup"><span data-stu-id="e4c6d-117">For **TargetReportFolder**, type a URL to a library or library folder (for example, *http://TestServer/TestSite/Documents/Reports)*.</span></span>  
  
7.  <span data-ttu-id="e4c6d-118">**TargetServerURL**에 SharePoint 최상위 사이트 또는 하위 사이트에 대한 URL을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="e4c6d-118">For **TargetServerURL**, type a URL to a SharePoint top-level site or subsite.</span></span> <span data-ttu-id="e4c6d-119">사이트를 지정 하지 않으면 기본 최상위 사이트 (예: *http://servername* , 또는)가 사용 됩니다 *http://servername/site* *http://servername/site/subsite* .</span><span class="sxs-lookup"><span data-stu-id="e4c6d-119">If you do not specify a site, the default top-level site is used (for example, *http://servername*, *http://servername/site*, or *http://servername/site/subsite*).</span></span>  
  
8.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
9. <span data-ttu-id="e4c6d-120">솔루션 탐색기에서 게시하려는 보고서를 마우스 오른쪽 단추로 클릭하고 **배포**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e4c6d-120">In Solution Explorer, right-click the report you want to publish, and click **Deploy**.</span></span> <span data-ttu-id="e4c6d-121">보고서가 **TargetReportFolder**에 지정된 위치에 게시됩니다.</span><span class="sxs-lookup"><span data-stu-id="e4c6d-121">The report is published to the location specified in **TargetReportFolder**.</span></span> <span data-ttu-id="e4c6d-122">출력 창에 배포 오류가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="e4c6d-122">Deployment errors appear in the Output window.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4c6d-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e4c6d-123">See Also</span></span>  
 <span data-ttu-id="e4c6d-124">[프로젝트 속성 페이지 대화 상자](../tools/project-property-pages-dialog-box.md) </span><span class="sxs-lookup"><span data-stu-id="e4c6d-124">[Project Property Pages Dialog Box](../tools/project-property-pages-dialog-box.md) </span></span>  
 <span data-ttu-id="e4c6d-125">[배포 속성 &#40;Reporting Services&#41;설정](../tools/set-deployment-properties-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="e4c6d-125">[Set Deployment Properties &#40;Reporting Services&#41;](../tools/set-deployment-properties-reporting-services.md) </span></span>  
 <span data-ttu-id="e4c6d-126">[보고서 서버에 보고서 게시](publishing-reports-to-a-report-server.md) </span><span class="sxs-lookup"><span data-stu-id="e4c6d-126">[Publishing Reports to a Report Server](publishing-reports-to-a-report-server.md) </span></span>  
 <span data-ttu-id="e4c6d-127">[SharePoint 모드의 보고서 서버에 게시 된 보고서 항목에 대 한 URL 예 &#40;SSRS&#41;](../tools/url-examples-for-items-on-a-report-server-sharepoint-mode.md) </span><span class="sxs-lookup"><span data-stu-id="e4c6d-127">[URL Examples for Published Report Items on a Report Server in SharePoint Mode &#40;SSRS&#41;](../tools/url-examples-for-items-on-a-report-server-sharepoint-mode.md) </span></span>  
 [<span data-ttu-id="e4c6d-128">보고서에 Office 데이터 연결&#40;.odc&#41; 사용&#40;SharePoint 통합 모드의 Reporting Services&#41;</span><span class="sxs-lookup"><span data-stu-id="e4c6d-128">Use an Office Data Connection &#40;.odc&#41; with Reports &#40;Reporting Services in SharePoint Integrated Mode&#41;</span></span>](../report-data/use-an-office-data-connection-odc-with-reports.md)  
  
  
