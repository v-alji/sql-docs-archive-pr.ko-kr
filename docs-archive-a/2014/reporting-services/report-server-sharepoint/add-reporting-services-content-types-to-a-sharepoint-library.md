---
title: 웹 페이지에 보고서 뷰어 웹 파트 추가 (SharePoint 통합 모드의 Reporting Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- SharePoint integration [Reporting Services], viewing reports
- Web Parts [Reporting Services]
- SharePoint integration [Reporting Services], Web Parts
- Report Viewer Web Part [Reporting Services]
ms.assetid: cac75345-2380-467d-a394-0a2140908a5a
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d9b933fad8bc566b3cb0ef04303a85c5f034e620
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736044"
---
# <a name="add-the-report-viewer-web-part-to-a-web-page-reporting-services-in-sharepoint-integrated-mode"></a><span data-ttu-id="34b7a-102">웹 페이지에 보고서 뷰어 웹 파트 추가(SharePoint 통합 모드의 Reporting Services)</span><span class="sxs-lookup"><span data-stu-id="34b7a-102">Add the Report Viewer Web Part to a Web Page (Reporting Services in SharePoint Integrated Mode)</span></span>
  <span data-ttu-id="34b7a-103">보고서 뷰어 웹 파트를 사용하여 SharePoint 통합 모드로 구성된 보고서 서버에서 실행되는 보고서를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34b7a-103">You can use the Report Viewer Web Part to view reports that run on report server that is configured to run in SharePoint integrated mode.</span></span> <span data-ttu-id="34b7a-104">또한 이 웹 파트를 사용하여 보고서 작성기나 보고서 디자이너에서 만들어 라이브러리에 업로드한 보고서 정의 파일(.rdl)을 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34b7a-104">You can use the Web Part to display report definition (.rdl) files that you created in Report Builder or Report Designer and uploaded to a library.</span></span>  
  
 <span data-ttu-id="34b7a-105">웹 페이지에 보고서를 포함하려는 경우 보고서 뷰어 웹 파트를 해당 페이지에 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34b7a-105">You can add the Report Viewer Web Part to a Web page if you want to embed a report on that page.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="34b7a-106">이름은 같지만 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 추가 기능을 통해 설치된 보고서 뷰어 웹 파트는 RSWebParts.cab 파일에 포함된 보고서 뷰어 웹 파트와 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="34b7a-106">Although they have identical names, the Report Viewer Web Part that is installed through the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Add-in is different from the Report Viewer Web Part that is included in the RSWebParts.cab file.</span></span> <span data-ttu-id="34b7a-107">이 항목의 지침은 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 추가 기능을 통해 설치되는 보고서 뷰어 웹 파트에만 해당됩니다.</span><span class="sxs-lookup"><span data-stu-id="34b7a-107">The instructions in this topic are specifically for the Report Viewer Web Part that is installed through the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Add-in.</span></span>  
  
 <span data-ttu-id="34b7a-108">웹 페이지에 웹 파트를 추가하려면 사이트 수준에서 페이지 추가 및 사용자 지정 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="34b7a-108">To add a Web Part to a Web page, you must have the Add and Customize Pages permission at the site level.</span></span> <span data-ttu-id="34b7a-109">기본 보안 설정을 사용하는 경우 이 권한은 모든 권한 수준의 사용 권한이 있는 **소유자** 그룹의 멤버에게 부여됩니다.</span><span class="sxs-lookup"><span data-stu-id="34b7a-109">If you are using default security settings, this permission is granted to members of the **Owners** group who have the Full Control level of permission.</span></span>  
  
### <a name="to-embed-a-report-in-a-web-page"></a><span data-ttu-id="34b7a-110">웹 페이지에 보고서를 포함하려면</span><span class="sxs-lookup"><span data-stu-id="34b7a-110">To embed a report in a Web page</span></span>  
  
1.  <span data-ttu-id="34b7a-111">웹 파트 페이지 또는 대시보드를 열거나 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="34b7a-111">Open or create the Web Part page or dashboard.</span></span>  
  
2.  <span data-ttu-id="34b7a-112">**사이트 동작**에서 **페이지 편집**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="34b7a-112">On **Site Actions**, click **Edit Page**.</span></span>  
  
3.  <span data-ttu-id="34b7a-113">**웹 파트 추가를**클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="34b7a-113">Click **Add a Web Part**.</span></span>  
  
4.  <span data-ttu-id="34b7a-114">웹 파트 범주 목록에서 **기타** 범주를 선택한 다음 **SQL Server Reporting Services 보고서 뷰어**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="34b7a-114">In the list of web part categories, select the **Miscellaneous** category, and then select **SQL Server Reporting Services Report Viewer**.</span></span>  
  
5.  <span data-ttu-id="34b7a-115">**추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="34b7a-115">Click **Add**.</span></span> <span data-ttu-id="34b7a-116">영역의 맨 위에 웹 파트가 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="34b7a-116">The Web Part is added at the top of the zone.</span></span> <span data-ttu-id="34b7a-117">해당 웹 파트를 영역의 다른 위치로 끌어 놓을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34b7a-117">You can drag it to a different location in the zone.</span></span>  
  
6.  <span data-ttu-id="34b7a-118">뷰어에서 **도구 창을 열려면 여기를 클릭하십시오**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="34b7a-118">Within the viewer, click **Click here to open the tool pane**.</span></span>  
  
7.  <span data-ttu-id="34b7a-119">찾아보기 (**...**) 단추를 클릭하여 현재 사이트 모음의 임의 라이브러리에 있는 보고서를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="34b7a-119">Select a report from any library in the current site collection by clicking the browse (**...**) button.</span></span> <span data-ttu-id="34b7a-120">보고서 URL을 입력할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34b7a-120">You can also type the report URL.</span></span> <span data-ttu-id="34b7a-121">보고서의 URL을 확인하려면 해당 보고서를 마우스 오른쪽 단추로 클릭하고 **속성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="34b7a-121">To determine the URL for any report, right-click the report and select **Properties**.</span></span> <span data-ttu-id="34b7a-122">보고서 옆의 아래쪽 화살표는 클릭하지 마십시오. 보고서 URL은 항목의 속성 보기 페이지에 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="34b7a-122">Do not click the down arrow next to the report; the report URL is not indicated in the View Properties page of the item.</span></span> <span data-ttu-id="34b7a-123">**속성** 대화 상자에서 URL을 복사하여 붙여넣는 경우 "%20" URL 인코딩을 공백으로 바꿉니다. 예를 들어 "Company%20Sales"는 "Company Sales"가 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="34b7a-123">If you copy and paste the URL from the **Properties** dialog box, replace the "%20" URL encoding with a space (for example, "Company%20Sales" should be "Company Sales").</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="34b7a-124">각 보고서 뷰어 웹 파트에는 단일 보고서가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34b7a-124">Each Report Viewer Web Part contains a single report.</span></span> <span data-ttu-id="34b7a-125">URL은 동일한 웹 애플리케이션 또는 팜 내의 사이트나 현재 SharePoint 사이트에 있는 보고서에 대한 정규화된 경로여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="34b7a-125">The URL must be the fully qualified path to a report that is on the current SharePoint site, or on a site within the same Web application or farm.</span></span> <span data-ttu-id="34b7a-126">URL은 문서 라이브러리나 보고서가 포함된 문서 라이브러리 내의 폴더로 확인되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="34b7a-126">The URL must resolve to a document library or to a folder within a document library that contains the report.</span></span> <span data-ttu-id="34b7a-127">보고서 URL은 .rdl 파일 확장명을 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="34b7a-127">The report URL must include the .rdl file extension.</span></span> <span data-ttu-id="34b7a-128">보고서가 모델 또는 공유 데이터 원본 파일에 종속되어 있는 경우 URL에 이러한 파일을 지정할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="34b7a-128">If the report depends on a model or shared data source files, you do not need to specify those files in the URL.</span></span> <span data-ttu-id="34b7a-129">보고서에 필요한 파일에 대한 참조가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34b7a-129">The report contains references to the files it needs.</span></span>  
  
8.  <span data-ttu-id="34b7a-130">도구 창이 열려 있는 동안 속성을 설정하여 기본 모양과 레이아웃을 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34b7a-130">While the tool pane is open, you can set properties to modify the default appearance and layout.</span></span>  
  
9. <span data-ttu-id="34b7a-131">도구 창의 아래쪽에서 **적용** 을 클릭한 다음 **확인** 을 클릭하여 창을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="34b7a-131">Click **Apply** at the bottom of the tool pane, and then click **OK** to close the pane.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34b7a-132">참고 항목</span><span class="sxs-lookup"><span data-stu-id="34b7a-132">See Also</span></span>  
 <span data-ttu-id="34b7a-133">[SharePoint 사이트의 보고서 뷰어 웹 파트](../report-viewer-web-part-on-a-sharepoint-site.md) </span><span class="sxs-lookup"><span data-stu-id="34b7a-133">[Report Viewer Web Part on a SharePoint Site](../report-viewer-web-part-on-a-sharepoint-site.md) </span></span>  
 <span data-ttu-id="34b7a-134">[보고서 뷰어 웹 파트 사용자 지정](../customize-the-report-viewer-web-part.md) </span><span class="sxs-lookup"><span data-stu-id="34b7a-134">[Customize the Report Viewer Web Part](../customize-the-report-viewer-web-part.md) </span></span>  
 <span data-ttu-id="34b7a-135">[SharePoint 사이트의 보고서 서버 항목에 대 한 사용 권한 부여](../security/granting-permissions-on-report-server-items-on-a-sharepoint-site.md) </span><span class="sxs-lookup"><span data-stu-id="34b7a-135">[Granting Permissions on Report Server Items on a SharePoint Site](../security/granting-permissions-on-report-server-items-on-a-sharepoint-site.md) </span></span>  
 [<span data-ttu-id="34b7a-136">Sharepoint 2010 및 SharePoint 2013 &#40;Reporting Services 추가 기능을 설치 하거나 제거&#41;</span><span class="sxs-lookup"><span data-stu-id="34b7a-136">Install or Uninstall the Reporting Services Add-in for SharePoint &#40;SharePoint 2010 and SharePoint 2013&#41;</span></span>](../install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md)  
  
  
