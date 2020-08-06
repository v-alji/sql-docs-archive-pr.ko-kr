---
title: SharePoint 라이브러리에 공유 데이터 원본 게시 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- data sources [Reporting Services], publishing to a SharePoint library
- SharePoint integration [Reporting Services], publishing to a library
- publishing reports [Reporting Services], to a SharePoint library
ms.assetid: 966ed425-3ce2-4e76-8237-3c1c977954ae
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 77ee25535ccb98638ae02ca64e3bcbfc88291c12
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87729043"
---
# <a name="publish-a-shared-data-source-to-a-sharepoint-library"></a><span data-ttu-id="cd33a-102">SharePoint 라이브러리에 공유 데이터 원본 게시</span><span class="sxs-lookup"><span data-stu-id="cd33a-102">Publish a Shared Data Source to a SharePoint Library</span></span>
  <span data-ttu-id="cd33a-103">SharePoint 통합 모드에서 실행 중인 보고서 서버에 공유 데이터 원본을 게시하려면 보고서 디자이너에서 보고서 프로젝트 속성을 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd33a-103">To publish a shared data source to a report server that is running in SharePoint integrated mode, you must set the report project properties in Report Designer.</span></span> <span data-ttu-id="cd33a-104">프로젝트 속성에서 서버, 보고서 및 공유 데이터 원본에 대한 모든 참조는 정규화된 URL이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd33a-104">In the project properties, all references to servers, reports, and shared data sources must be fully qualified URLs.</span></span>  
  
 <span data-ttu-id="cd33a-105">SharePoint 사이트에 대한 **멤버** 또는 **소유자** 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd33a-105">You must have **Member** or **Owner** permission on the SharePoint site.</span></span> <span data-ttu-id="cd33a-106">자세한 내용은 [SharePoint 모드의 보고서 서버에 게시된 보고서 항목에 대한 URL 예&#40;SSRS&#41;](../tools/url-examples-for-items-on-a-report-server-sharepoint-mode.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="cd33a-106">For more information, see [URL Examples for Published Report Items on a Report Server in SharePoint Mode &#40;SSRS&#41;](../tools/url-examples-for-items-on-a-report-server-sharepoint-mode.md).</span></span>  
  
### <a name="to-publish-a-shared-data-source-to-a-sharepoint-site"></a><span data-ttu-id="cd33a-107">SharePoint 사이트에 공유 데이터 원본을 게시하려면</span><span class="sxs-lookup"><span data-stu-id="cd33a-107">To publish a shared data source to a SharePoint site</span></span>  
  
1.  <span data-ttu-id="cd33a-108">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]에서 기존 또는 새로운 보고서 서버 프로젝트를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="cd33a-108">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open your existing or new Report Server project.</span></span>  
  
2.  <span data-ttu-id="cd33a-109">**프로젝트** 메뉴에서 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cd33a-109">On the **Project** menu, click **Properties**.</span></span> <span data-ttu-id="cd33a-110">_\<project>_ **속성 페이지** 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="cd33a-110">The _\<project>_**Property Pages** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="cd33a-111">SharePoint 사이트에 게시하는 데 사용할 **구성** 을 선택합니다(예:</span><span class="sxs-lookup"><span data-stu-id="cd33a-111">Choose the **Configuration** you use to publish to a SharePoint site.</span></span>  
  
4.  <span data-ttu-id="cd33a-112">프로젝트의 공유 데이터 원본을 게시하고 이전에 게시된 공유 데이터 원본을 덮어쓰려면 **OverwriteDataSources** 를 **True**로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="cd33a-112">If you want to publish the shared data sources in your project and overwrite previously published shared data sources, set **OverwriteDataSources** to **True**.</span></span>  
  
5.  <span data-ttu-id="cd33a-113">(옵션) **TargetDataSourceFolder**에 SharePoint 라이브러리 또는 라이브러리 폴더에 대한 URL을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="cd33a-113">(Optional) For **TargetDataSourceFolder**, type a URL to a SharePoint library or library folder.</span></span> <span data-ttu-id="cd33a-114">예를 들어 *http://TestServer/TestSite/Documents/DataSources* 와 같습니다.</span><span class="sxs-lookup"><span data-stu-id="cd33a-114">For example, *http://TestServer/TestSite/Documents/DataSources*.</span></span>  
  
     <span data-ttu-id="cd33a-115">값을 지정하지 않으면 **TargetReportFolder** 값이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="cd33a-115">If you do not specify a value, the **TargetReportFolder** value is used.</span></span>  
  
6.  <span data-ttu-id="cd33a-116">**TargetReportFolder**에 라이브러리 또는 라이브러리 폴더에 대한 URL을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="cd33a-116">For **TargetReportFolder**, type a URL to a library or library folder.</span></span> <span data-ttu-id="cd33a-117">예를 들어 http:*//TestServer/TestSite/Documents/Reports*입니다.</span><span class="sxs-lookup"><span data-stu-id="cd33a-117">For example, http:*//TestServer/TestSite/Documents/Reports*.</span></span>  
  
7.  <span data-ttu-id="cd33a-118">**TargetServerURL**에 SharePoint 최상위 사이트 또는 하위 사이트에 대한 URL을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="cd33a-118">For **TargetServerURL**, type a URL to a SharePoint top-level site or subsite.</span></span> <span data-ttu-id="cd33a-119">사이트를 지정하지 않으면 기본 최상위 사이트가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="cd33a-119">If you do not specify a site, the default top-level site is used.</span></span> <span data-ttu-id="cd33a-120">예를 들어 http://*servername*, http://*servername*/*site*또는 http://*servername*/*site*/*subsite*입니다.</span><span class="sxs-lookup"><span data-stu-id="cd33a-120">For example, http://*servername*, http://*servername*/*site*, or http://*servername*/*site*/*subsite*.</span></span>  
  
8.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
9. <span data-ttu-id="cd33a-121">솔루션 탐색기에서 게시하려는 공유 데이터 원본을 마우스 오른쪽 단추로 클릭한 다음 **배포**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cd33a-121">In Solution Explorer, right-click the shared data source you want to publish, and click **Deploy**.</span></span> <span data-ttu-id="cd33a-122">데이터 원본이 **TargetDataSourceFolder**에 지정된 위치에 게시됩니다.</span><span class="sxs-lookup"><span data-stu-id="cd33a-122">The data source is published to the location specified in **TargetDataSourceFolder**.</span></span> <span data-ttu-id="cd33a-123">출력 창에 배포 오류가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="cd33a-123">Deployment errors appear in the Output window.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="cd33a-124">SharePoint 사이트에 공유 데이터 원본을 게시하면 파일 확장명이 .rsds로 변경됩니다.</span><span class="sxs-lookup"><span data-stu-id="cd33a-124">After you publish a shared data source to a SharePoint site, the file name extension is changed to .rsds.</span></span> <span data-ttu-id="cd33a-125">SharePoint 사이트에서 공유 데이터 원본을 직접 편집 및 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cd33a-125">You can edit and manage a shared data source directly on the SharePoint site.</span></span> <span data-ttu-id="cd33a-126">자세한 내용은 [공유 데이터 원본 만들기 및 관리&#40;SharePoint 통합 모드의 Reporting Services&#41;](../create-manage-shared-data-sources-reporting-services-sharepoint-integrated-mode.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="cd33a-126">For more information, see [Create and Manage Shared Data Sources &#40;Reporting Services in SharePoint Integrated Mode&#41;](../create-manage-shared-data-sources-reporting-services-sharepoint-integrated-mode.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd33a-127">참고 항목</span><span class="sxs-lookup"><span data-stu-id="cd33a-127">See Also</span></span>  
 <span data-ttu-id="cd33a-128">[SharePoint 라이브러리에 보고서 게시](publish-a-report-to-a-sharepoint-library.md) </span><span class="sxs-lookup"><span data-stu-id="cd33a-128">[Publish a Report to a SharePoint Library](publish-a-report-to-a-sharepoint-library.md) </span></span>  
 <span data-ttu-id="cd33a-129">[SharePoint 모드의 보고서 서버에 게시 된 보고서 항목에 대 한 URL 예 &#40;SSRS&#41;](../tools/url-examples-for-items-on-a-report-server-sharepoint-mode.md) </span><span class="sxs-lookup"><span data-stu-id="cd33a-129">[URL Examples for Published Report Items on a Report Server in SharePoint Mode &#40;SSRS&#41;](../tools/url-examples-for-items-on-a-report-server-sharepoint-mode.md) </span></span>  
 <span data-ttu-id="cd33a-130">[프로젝트 속성 페이지 대화 상자](../tools/project-property-pages-dialog-box.md) </span><span class="sxs-lookup"><span data-stu-id="cd33a-130">[Project Property Pages Dialog Box](../tools/project-property-pages-dialog-box.md) </span></span>  
 <span data-ttu-id="cd33a-131">[배포 속성 &#40;Reporting Services&#41;설정](../tools/set-deployment-properties-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="cd33a-131">[Set Deployment Properties &#40;Reporting Services&#41;](../tools/set-deployment-properties-reporting-services.md) </span></span>  
 <span data-ttu-id="cd33a-132">[보고서 서버에 보고서 게시](publishing-reports-to-a-report-server.md) </span><span class="sxs-lookup"><span data-stu-id="cd33a-132">[Publishing Reports to a Report Server](publishing-reports-to-a-report-server.md) </span></span>  
 [<span data-ttu-id="cd33a-133">보고서에 Office 데이터 연결&#40;.odc&#41; 사용&#40;SharePoint 통합 모드의 Reporting Services&#41;</span><span class="sxs-lookup"><span data-stu-id="cd33a-133">Use an Office Data Connection &#40;.odc&#41; with Reports &#40;Reporting Services in SharePoint Integrated Mode&#41;</span></span>](../report-data/use-an-office-data-connection-odc-with-reports.md)  
  
  
