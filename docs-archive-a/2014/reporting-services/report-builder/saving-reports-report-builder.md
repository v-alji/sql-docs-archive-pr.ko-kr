---
title: 보고서 저장(보고서 작성기) | Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 59ddc4b8-9517-4d3f-9c88-a07e9907cecb
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 9210eafb65ee7adced8d0cd821d88b5f0cbcb9c5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639367"
---
# <a name="saving-reports-report-builder"></a><span data-ttu-id="4ac6f-102">보고서 저장(보고서 작성기)</span><span class="sxs-lookup"><span data-stu-id="4ac6f-102">Saving Reports (Report Builder)</span></span>
  <span data-ttu-id="4ac6f-103">보고서 작성기에서 보고서 서버, SharePoint 라이브러리, 쓰기 권한이 있는 파일 공유 또는 컴퓨터에 보고서를 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4ac6f-103">In Report Builder you can save a report to a report server, SharePoint library, file share on which you have write permission, or your computer.</span></span> <span data-ttu-id="4ac6f-104">보고서를 연 동일한 위치에 보고서를 저장하거나, 다른 위치에 보고서를 저장하거나, 동일한 위치나 다른 위치에 새 이름으로 보고서를 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4ac6f-104">You can save a report to the same location from which you opened it, save it to a different location, or save it with a new name to the same or different location.</span></span> <span data-ttu-id="4ac6f-105">기본적으로 보고서는 보고서를 연 위치에 다시 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="4ac6f-105">By default, a report is resaved to the location from which you opened it.</span></span> <span data-ttu-id="4ac6f-106">보고서를 저장할 때 실제로 저장하는 것은 보고서 레이아웃을 설명하는 보고서 정의이며,</span><span class="sxs-lookup"><span data-stu-id="4ac6f-106">When you save the report, what you are really saving is the report definition, which describes the report layout.</span></span> <span data-ttu-id="4ac6f-107">데이터를 저장하지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4ac6f-107">You are not saving the data.</span></span> <span data-ttu-id="4ac6f-108">보고서를 실행할 때마다 보고서 데이터는 새로 고쳐지고 보고서를 이전에 실행했을 때와 다를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4ac6f-108">Every time you run the report, the report data is refreshed and is likely to be different than the previous time you ran the report.</span></span>  
  
 <span data-ttu-id="4ac6f-109">보고서를 다른 형식으로 저장하거나 데이터와 함께 보고서 정의를 저장하려면 다음 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 기능 중 하나를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="4ac6f-109">If you want to save the report to a different format or save the report definition with the data, use one of the following [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] features:</span></span>  
  
-   <span data-ttu-id="4ac6f-110">렌더링된 보고서를 CSV(쉼표로 구분된 파일), Excel 통합 문서 등의 다른 파일 형식으로 내보내고 해당 형식으로 보고서를 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="4ac6f-110">Export a rendered report to a different file format such as comma separated files (CSV) or Excel workbooks and save the report in that format.</span></span> <span data-ttu-id="4ac6f-111">보고서에서 데이터 피드를 생성하고 보고서 데이터를 저장할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4ac6f-111">You can also generate data feeds from reports and save the report data.</span></span>  
  
-   <span data-ttu-id="4ac6f-112">보고서 구독을 만들어 파일 공유에 보고서를 배달하고 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="4ac6f-112">Create report subscriptions to deliver and save reports to a file share.</span></span>  
  
-   <span data-ttu-id="4ac6f-113">보고서 기록을 사용하여 렌더링된 보고서의 버전을 기록 복사본으로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="4ac6f-113">Use report history to save versions of rendered reports as historical copies.</span></span>  
  
 <span data-ttu-id="4ac6f-114">보고서 서버에서 보고서를 직접 보고 관리하는 방법에 대한 자세한 내용은 msdn.microsoft.com의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [온라인 설명서](https://go.microsoft.com/fwlink/?LinkId=154888)에서 [보고서 찾기, 보기 및 관리&#40;보고서 작성기 및 SSRS&#41;](finding-viewing-and-managing-reports-report-builder-and-ssrs.md) 및 [Reporting Services 보고서 서버&#40;기본 모드&#41;](../report-server/reporting-services-report-server-native-mode.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4ac6f-114">To learn more about viewing and managing reports directly on the report server, see [Finding, Viewing, and Managing Reports &#40;Report Builder and SSRS &#41;](finding-viewing-and-managing-reports-report-builder-and-ssrs.md) and [Reporting Services Report Server &#40;Native Mode&#41;](../report-server/reporting-services-report-server-native-mode.md) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [Books Online](https://go.microsoft.com/fwlink/?LinkId=154888) on msdn.microsoft.com.</span></span>  
  
##  <a name="saving-report-definitions"></a><a name="SavingReportDefinitions"></a><span data-ttu-id="4ac6f-115">보고서 정의 저장</span><span class="sxs-lookup"><span data-stu-id="4ac6f-115">Saving Report Definitions</span></span>  
 <span data-ttu-id="4ac6f-116">컴퓨터에 보고서를 저장할 수 있지만 보고서 서버에 보고서를 저장하면 많은 이점이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4ac6f-116">Although you can save reports to your computer, saving reports to a report server offers many advantages.</span></span>  
  
 <span data-ttu-id="4ac6f-117">보고서 서버에 보고서를 저장하면 다음과 같은 이점이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4ac6f-117">Saving a report to a report server offers the following advantages:</span></span>  
  
-   <span data-ttu-id="4ac6f-118">보고서를 저장한 폴더에 액세스할 수 있는 권한이 있는 다른 사용자가 보고서를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4ac6f-118">Reports become available to others who have permission to access the folder in which you saved the report.</span></span>  
  
-   <span data-ttu-id="4ac6f-119">보고서 관리자에서 보고서를 관리하고 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4ac6f-119">Reports can be managed and viewed from Report Manager.</span></span>  
  
-   <span data-ttu-id="4ac6f-120">데이터 원본, 이미지 및 하위 보고서와 같은 보고서 리소스가 쉽게 액세스할 수 있도록 한 곳에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="4ac6f-120">Report resources such as data sources, images, and subreports are stored in one place for easier access.</span></span>  
  
-   <span data-ttu-id="4ac6f-121">구독을 통해 다른 사용자에게 보고서를 배달할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4ac6f-121">Reports can be delivered to others by subscriptions.</span></span>  
  
-   <span data-ttu-id="4ac6f-122">보고서가 보고서 서버 데이터베이스에 안전하게 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="4ac6f-122">Reports are securely stored in the report server database.</span></span>  
  
-   <span data-ttu-id="4ac6f-123">보고서 실행이 기록되어 성능 및 감사 정보를 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4ac6f-123">Report runs can be logged and provide performance and auditing information.</span></span>  
  
 <span data-ttu-id="4ac6f-124">보고서 서버에 보고서를 저장하는 것을 보고서 게시라고도 합니다.</span><span class="sxs-lookup"><span data-stu-id="4ac6f-124">Saving a report to a report server is also known as publishing a report.</span></span> <span data-ttu-id="4ac6f-125">보고서를 저장할 때 보고서 정의만 저장하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4ac6f-125">When you save the report you save the report definition only.</span></span> <span data-ttu-id="4ac6f-126">보고서를 실행할 때마다 보고서 데이터는 새로 고쳐지고 보고서를 이전에 실행했을 때와 다를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4ac6f-126">Every time you run the report, the report data is refreshed and likely different that the previous time you ran the report.</span></span> <span data-ttu-id="4ac6f-127">데이터와 함께 보고서 정의를 저장하려면 보고서 기록 기능을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4ac6f-127">If you want to save the report definition with the data you should use the report history feature.</span></span> <span data-ttu-id="4ac6f-128">이 기능을 사용하여 데이터와 함께 보고서의 복사본을 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4ac6f-128">Using this feature, you save a copy of the report with its data.</span></span>  
  

  
##  <a name="exporting-and-saving-reports"></a><a name="ExportingAndSavingReports"></a> <span data-ttu-id="4ac6f-129">보고서 내보내기 및 저장</span><span class="sxs-lookup"><span data-stu-id="4ac6f-129">Exporting and Saving Reports</span></span>  
 <span data-ttu-id="4ac6f-130">보관할 보고서가 적으면 보고서를 파일로 내보내고 저장하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="4ac6f-130">If you have a small number of reports to archive, consider exporting a report and saving it as a file.</span></span> <span data-ttu-id="4ac6f-131">PDF나 Excel 등의 애플리케이션으로 보고서를 내보내면 보고서를 파일로 저장하여 네트워크의 보호된 공유 디렉터리에 보관할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4ac6f-131">After you export a report to an application (such as PDF or Excel), you can save it as a file and place it in a protected shared directory on the network.</span></span> <span data-ttu-id="4ac6f-132">또는 보고서의 모든 복사본을 형식에 관계없이 보고서 서버 데이터베이스에 보관하려는 경우 저장된 PDF나 Excel 파일을 리소스 항목으로 업로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4ac6f-132">Alternatively, you can upload a saved PDF or Excel file as a resource item if you want to keep all copies of a report, regardless of the format, in the report server database.</span></span> <span data-ttu-id="4ac6f-133">보고서를 내보내는 방법에 대 한 자세한 내용은 [보고서 작성기 및 SSRS&#41;&#40;보고서 내보내기](export-reports-report-builder-and-ssrs.md) 및 [파일 또는 보고서 업로드 &#40;보고서 관리자&#41;](../reports/upload-a-file-or-report-report-manager.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="4ac6f-133">For more information about exporting a report, see [Exporting Reports &#40;Report Builder and SSRS&#41;](export-reports-report-builder-and-ssrs.md) and [Upload a File or Report &#40;Report Manager&#41;](../reports/upload-a-file-or-report-report-manager.md).</span></span>  
  

  
##  <a name="using-file-share-delivery"></a><a name="UsingFileShareDelivery"></a> <span data-ttu-id="4ac6f-134">파일 공유 배달 사용</span><span class="sxs-lookup"><span data-stu-id="4ac6f-134">Using File-Share Delivery</span></span>  
 <span data-ttu-id="4ac6f-135">보관할 보고서가 많으면 보고서를 파일 시스템으로 직접 배달하는 구독을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="4ac6f-135">If you have a large number of reports to archive, create a subscription that delivers the report directly to the file system.</span></span> <span data-ttu-id="4ac6f-136">이 방식을 사용하려면 각 보고서에 대한 구독을 만들고 보고서를 저장할 공유 폴더를 선택하고 파일 작성 시간을 결정하는 일정을 정의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4ac6f-136">For this approach, you must create a subscription for each report, choose a shared folder to store the reports, and define a schedule that determines when the file is created.</span></span> <span data-ttu-id="4ac6f-137">구독을 정의하면 보고서 서버는 무인 모드에서 보고서를 실행하고 제공한 일정에 따라 보고서 파일을 보관 위치에 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4ac6f-137">Once you define a subscription, the report server can run the report unattended and add report files to the archive using the schedule that you provide.</span></span> <span data-ttu-id="4ac6f-138">또한 일회 일정을 만들어 필요한 경우에만 보고서를 보관할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4ac6f-138">You can also create single-use schedules if you want to archive reports on an occasional basis.</span></span> <span data-ttu-id="4ac6f-139">구독 및 파일 공유 배달에 대한 자세한 내용은 SQL Server 온라인 설명서의 [Reporting Services 설명서](https://go.microsoft.com/fwlink/?linkid=121312) 에 있는 "Reporting Services의 파일 배달"을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="4ac6f-139">For more information about subscriptions and file share delivery, see "File Delivery in Reporting Services" in the [Reporting Services documentation](https://go.microsoft.com/fwlink/?linkid=121312) in SQL Server Books Online.</span></span>  
  

  
##  <a name="using-report-history"></a><a name="UsingReportHistory"></a> <span data-ttu-id="4ac6f-140">보고서 기록 사용</span><span class="sxs-lookup"><span data-stu-id="4ac6f-140">Using Report History</span></span>  
 <span data-ttu-id="4ac6f-141">보고서 기록 기능을 사용하여 기록 복사본을 만들 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4ac6f-141">You can also use the report history feature to create historical copies.</span></span> <span data-ttu-id="4ac6f-142">그런 다음 나중에 사용할 수 있도록 보고서 서버 데이터베이스를 백업하고 안전한 위치에 백업을 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4ac6f-142">You can then back up the report server database and store the backup in a safe location for future use.</span></span> <span data-ttu-id="4ac6f-143">모든 보고서 기록은 보고서, 공유 데이터 원본 항목, 폴더, 구독 및 공유 일정과 함께 보고서 서버 데이터베이스에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="4ac6f-143">All report history (along with reports, shared data source items, folders, subscriptions, and shared schedules) is stored in the report server database.</span></span> <span data-ttu-id="4ac6f-144">백업을 만들어 보고서 기록의 영구 복사본과 보고서를 받는 사람을 나타내는 구독 정보 등의 메타데이터를 유지 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4ac6f-144">You can create a backup to maintain a permanent copy of report history and metadata such as subscription information that indicates the recipients of a report.</span></span> <span data-ttu-id="4ac6f-145">자세한 내용은 SQL Server 온라인 설명서의 [Reporting Services 설명서](https://go.microsoft.com/fwlink/?linkid=121312) 에 있는 "보고서 기록 관리"를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="4ac6f-145">For more information, see "Managing Report History" in the [Reporting Services documentation](https://go.microsoft.com/fwlink/?linkid=121312) in SQL Server Books Online.</span></span>  
  

  
##  <a name="how-to-topics"></a><a name="HowTo"></a><span data-ttu-id="4ac6f-146">방법 도움말 항목</span><span class="sxs-lookup"><span data-stu-id="4ac6f-146">How-To Topics</span></span>  
  
-   [<span data-ttu-id="4ac6f-147">보고서 서버에 보고서 저장&#40;보고서 작성기&#41;</span><span class="sxs-lookup"><span data-stu-id="4ac6f-147">Save Reports to a Report Server &#40;Report Builder&#41;</span></span>](save-reports-to-a-report-server-report-builder.md)  
  
-   [<span data-ttu-id="4ac6f-148">SharePoint 라이브러리에 보고서 저장&#40;보고서 작성기&#41;</span><span class="sxs-lookup"><span data-stu-id="4ac6f-148">Save a Report to a SharePoint Library &#40;Report Builder&#41;</span></span>](save-a-report-to-a-sharepoint-library-report-builder.md)  
  
-   [<span data-ttu-id="4ac6f-149">컴퓨터에 보고서 저장 &#40;보고서 작성기&#41;</span><span class="sxs-lookup"><span data-stu-id="4ac6f-149">Save Reports to Your Computer &#40;Report Builder&#41;</span></span>](../save-reports-to-your-computer-report-builder.md)  
  

  
## <a name="see-also"></a><span data-ttu-id="4ac6f-150">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4ac6f-150">See Also</span></span>  
 <span data-ttu-id="4ac6f-151">[보고서, 보고서 파트 및 보고서 정의 &#40;보고서 작성기 및 SSRS&#41;](../report-design/reports-report-parts-and-report-definitions-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="4ac6f-151">[Reports, Report Parts, and Report Definitions &#40;Report Builder and SSRS&#41;](../report-design/reports-report-parts-and-report-definitions-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="4ac6f-152">[설치, 제거 및 보고서 작성기 지원](../install-uninstall-and-report-builder-support.md) </span><span class="sxs-lookup"><span data-stu-id="4ac6f-152">[Install, Uninstall, and Report Builder Support](../install-uninstall-and-report-builder-support.md) </span></span>  
 <span data-ttu-id="4ac6f-153">[보고서 작성기 및 SSRS &#40;보고서 찾기, 보기 및 관리 &#41;](finding-viewing-and-managing-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="4ac6f-153">[Finding, Viewing, and Managing Reports &#40;Report Builder and SSRS &#41;](finding-viewing-and-managing-reports-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="4ac6f-154">[보고서 &#40;보고서 작성기 및 SSRS&#41;내보내기](export-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="4ac6f-154">[Exporting Reports &#40;Report Builder and SSRS&#41;](export-reports-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="4ac6f-155">보고서 인쇄&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="4ac6f-155">Print Reports &#40;Report Builder and SSRS&#41;</span></span>](print-reports-report-builder-and-ssrs.md)  
  
  
