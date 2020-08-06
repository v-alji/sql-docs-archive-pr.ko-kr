---
title: SharePoint 라이브러리에 문서 업로드 (SharePoint 모드의 Reporting Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- SharePoint integration [Reporting Services], viewing reports
- SharePoint integration [Reporting Services], content management
- uploading reports [Reporting Services]
ms.assetid: 93bd1b19-061b-409f-8dc2-ec416b2f4b39
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 74b39f90cd90dc8a92a5f10168d98f165c211c51
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737785"
---
# <a name="upload-documents-to-a-sharepoint-library-reporting-services-in-sharepoint-mode"></a><span data-ttu-id="7ce21-102">SharePoint 라이브러리에 문서 업로드(SharePoint 모드의 Reporting Services)</span><span class="sxs-lookup"><span data-stu-id="7ce21-102">Upload Documents to a SharePoint Library (Reporting Services in SharePoint Mode)</span></span>
  <span data-ttu-id="7ce21-103">SharePoint 라이브러리에 보고서 정의 및 보고서 모델을 업로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ce21-103">You can upload report definitions and report models to a SharePoint library.</span></span> <span data-ttu-id="7ce21-104">보고서 서버 항목을 업로드하는 경우 라이브러리 또는 라이브러리 내의 폴더를 선택해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ce21-104">When uploading a report server item, you must select a library or a folder within a library.</span></span> <span data-ttu-id="7ce21-105">보고서 서버 항목을 목록 또는 페이지에 업로드할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7ce21-105">You cannot upload a report server item to a list or page.</span></span>  
  
 <span data-ttu-id="7ce21-106">데이터 원본 파일(.rds)을 업로드할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7ce21-106">You cannot upload a data source (.rds) file.</span></span> <span data-ttu-id="7ce21-107">그러나 보고서 디자이너와 같은 디자인 도구에서 SharePoint 라이브러리로 .rds 파일을 게시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ce21-107">However, you can publish .rds files from a design tool, such as Report Designer, to a SharePoint library.</span></span> <span data-ttu-id="7ce21-108">게시하는 동안 솔루션의 원래 .rds 파일에서 새 .rsds 파일이 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="7ce21-108">During publication, a new .rsds file is created from the original .rds file in the solution.</span></span> <span data-ttu-id="7ce21-109">SharePoint 라이브러리에서 새 .rsds 파일을 만든 다음 업로드된 보고서 및 모델의 데이터 원본 연결 속성을 설정하여 새 연결을 사용하도록 만들 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ce21-109">You can also create a new .rsds file in a SharePoint library and then set data source connection properties in the uploaded reports and models to use the new connection.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7ce21-110">보고서 서버는 SharePoint 모드로 구성해야 하며 SharePoint 제품 인스턴스에는 SharePoint 사이트의 보고서 서버 항목을 저장 및 액세스하기 위한 프로그램 파일을 제공하는 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 추가 기능이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ce21-110">The report server must be configured for SharePoint mode, and the instance of the SharePoint product must have the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] Add-in that provides program files for storing and accessing report server items from a SharePoint site.</span></span>  
  
 <span data-ttu-id="7ce21-111">라이브러리에 문서를 업로드하려면 사이트 수준의 "항목 추가" 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ce21-111">To upload a document to a library, you must have the "Add Items" permission at the site level.</span></span> <span data-ttu-id="7ce21-112">기본 보안 설정을 사용하는 경우 이 권한은 모든 권한 수준의 사용 권한이 있는 **Owners** 그룹의 멤버와 참가 수준의 사용 권한이 있는 **Members** 그룹의 멤버에게 부여됩니다.</span><span class="sxs-lookup"><span data-stu-id="7ce21-112">If you are using default security settings, this permission is granted to members of the **Owners** group who have the Full Control level of permission and to the **Members** group who have the Contribute level of permission.</span></span>  
  
### <a name="to-add-a-report-definition-or-report-model-to-a-library"></a><span data-ttu-id="7ce21-113">라이브러리에 보고서 정의 또는 보고서 모델을 추가하려면</span><span class="sxs-lookup"><span data-stu-id="7ce21-113">To add a report definition or report model to a library</span></span>  
  
1.  <span data-ttu-id="7ce21-114">라이브러리 또는 라이브러리 내의 폴더를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="7ce21-114">Open the library or a folder within a library.</span></span> <span data-ttu-id="7ce21-115">라이브러리가 열려 있지 않으면 빠른 실행에서 해당 이름을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7ce21-115">If the library is not already open, click its name on the Quick Launch.</span></span> <span data-ttu-id="7ce21-116">라이브러리 이름이 나타나지 않으면 **모든 사이트 콘텐츠 보기**를 클릭한 다음 라이브러리 이름을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7ce21-116">If the name of your library does not appear, click **View All Site Content**, and then click the name of your library.</span></span>  
  
2.  <span data-ttu-id="7ce21-117">**업로드** 메뉴에서 **문서 업로드**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7ce21-117">On the **Upload** menu, click **Upload document**.</span></span>  
  
3.  <span data-ttu-id="7ce21-118">단일 보고서 또는 보고서 모델 파일을 업로드하려면 보고서 정의 파일(.rdl) 또는 보고서 모델 파일(.smdl)을 선택한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7ce21-118">To upload a single report or report model file, select a report definition (.rdl) or report model (.smdl) file and then click **OK**.</span></span>  
  
     <span data-ttu-id="7ce21-119">보고서 정의가 공유 데이터 원본 파일(.rsds)을 사용하여 외부 데이터 원본에 대한 연결 정보를 저장하는 경우 .rdl 파일 및 .rsds 파일을 동시에 업로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ce21-119">If the report definition uses a shared data source (.rsds) file to store connection information to an external data source, you can upload the .rdl and the .rsds file at the same time.</span></span> <span data-ttu-id="7ce21-120">이렇게 하려면 **여러 문서 업로드**를 클릭하고 두 파일을 모두 지정한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7ce21-120">To do this, click **Upload Multiple Documents**, specify both files, and then click **OK**.</span></span>  
  
 <span data-ttu-id="7ce21-121">공유 데이터 원본, 보고서 모델 또는 보고서에 대한 참조를 포함하는 보고서를 업로드하는 경우 파일을 업로드하면 해당 참조가 손상됩니다.</span><span class="sxs-lookup"><span data-stu-id="7ce21-121">If you upload a report that contains references to shared data sources, report models, or subreports, the references will be broken in the report when the files are uploaded.</span></span> <span data-ttu-id="7ce21-122">참조를 다시 설정하는 방법은 [공유 데이터 원본 만들기 및 관리&#40;SharePoint 통합 모드의 Reporting Services&#41;](../../2014/reporting-services/create-manage-shared-data-sources-reporting-services-sharepoint-integrated-mode.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7ce21-122">For more information about how to reset the references, see [Create and Manage Shared Data Sources &#40;Reporting Services in SharePoint Integrated Mode&#41;](../../2014/reporting-services/create-manage-shared-data-sources-reporting-services-sharepoint-integrated-mode.md).</span></span>  
  
 <span data-ttu-id="7ce21-123">보고서를 업로드하면 사용자가 열 때 해당 보고서가 요청 시 실행되어 데이터 원본의 라이브 데이터가 검색됩니다.</span><span class="sxs-lookup"><span data-stu-id="7ce21-123">When you upload a report, it runs on demand when you open it, retrieving live data from the data source.</span></span> <span data-ttu-id="7ce21-124">일정에 따라 데이터를 검색하거나 캐시된 데이터를 사용하도록 보고서를 구성할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ce21-124">You can configure the report to retrieve data on a schedule or use cached data.</span></span> <span data-ttu-id="7ce21-125">자세한 내용은 [처리 옵션 설정&#40;SharePoint 통합 모드의 Reporting Services&#41;](../../2014/reporting-services/set-processing-options-reporting-services-in-sharepoint-integrated-mode.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7ce21-125">For more information, see [Set Processing Options &#40;Reporting Services in SharePoint Integrated Mode&#41;](../../2014/reporting-services/set-processing-options-reporting-services-in-sharepoint-integrated-mode.md).</span></span>  
  
 <span data-ttu-id="7ce21-126">사용자가 데이터를 필터링할 수 있도록 보고서에 매개 변수를 포함할 수 있으며</span><span class="sxs-lookup"><span data-stu-id="7ce21-126">A report can contain parameters so that users can filter data.</span></span> <span data-ttu-id="7ce21-127">이러한 매개 변수에 특정 값을 지정하거나 사용자에게 매개 변수가 표시되는 방식을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ce21-127">You can configure the parameters to use specific values or change how they appear to the user.</span></span> <span data-ttu-id="7ce21-128">자세한 내용은 [게시된 보고서에 매개 변수 설정&#40;SharePoint 통합 모드의 Reporting Services&#41;](report-design/set-parameters-on-a-published-report-sharepoint-integrated-mode.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7ce21-128">For more information, see [Set Parameters on a Published Report &#40;Reporting Services in SharePoint Integrated Mode&#41;](report-design/set-parameters-on-a-published-report-sharepoint-integrated-mode.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ce21-129">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7ce21-129">See Also</span></span>  
 <span data-ttu-id="7ce21-130">[SharePoint 라이브러리에 보고서 게시](reports/publish-a-report-to-a-sharepoint-library.md) </span><span class="sxs-lookup"><span data-stu-id="7ce21-130">[Publish a Report to a SharePoint Library](reports/publish-a-report-to-a-sharepoint-library.md) </span></span>  
 <span data-ttu-id="7ce21-131">[SharePoint 라이브러리에 공유 데이터 원본 게시](reports/publish-a-shared-data-source-to-a-sharepoint-library.md) </span><span class="sxs-lookup"><span data-stu-id="7ce21-131">[Publish a Shared Data Source to a SharePoint Library](reports/publish-a-shared-data-source-to-a-sharepoint-library.md) </span></span>  
 [<span data-ttu-id="7ce21-132">SharePoint 사이트의 보고서 서버 항목에 대한 사용 권한 부여</span><span class="sxs-lookup"><span data-stu-id="7ce21-132">Granting Permissions on Report Server Items on a SharePoint Site</span></span>](security/granting-permissions-on-report-server-items-on-a-sharepoint-site.md)  
  
  
