---
title: 표준 구독 만들기, 수정 및 삭제 (기본 모드의 Reporting Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- standard subscriptions [Reporting Services]
- subscriptions [Reporting Services], standard
ms.assetid: 5ab1c661-9bfa-434a-b315-faac34ed12b1
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 035462f53e91a0ac29c756f8fcfdef7ad65cb984
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648794"
---
# <a name="create-modify-and-delete-standard-subscriptions-reporting-services-in-native-mode"></a><span data-ttu-id="42f89-102">Create, Modify, and Delete Standard Subscriptions (Reporting Services in Native Mode)</span><span class="sxs-lookup"><span data-stu-id="42f89-102">Create, Modify, and Delete Standard Subscriptions (Reporting Services in Native Mode)</span></span>
  <span data-ttu-id="42f89-103">표준 구독은 전자 메일을 통해 또는 공유 폴더로 보고서를 배달하려는 개인이 만든 구독입니다.</span><span class="sxs-lookup"><span data-stu-id="42f89-103">A standard subscription is one that is created by individual users who want to have a report delivered through e-mail or to a shared folder.</span></span> <span data-ttu-id="42f89-104">표준 구독은 항상 구독의 기반이 되는 보고서를 통해 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="42f89-104">A standard subscription is always defined through the report on which it is based.</span></span>  
  
 <span data-ttu-id="42f89-105">구독을 만드는 사용자가 해당 구독을 소유합니다.</span><span class="sxs-lookup"><span data-stu-id="42f89-105">A user who creates a subscription owns that subscription.</span></span> <span data-ttu-id="42f89-106">각 사용자는 자신이 소유한 구독을 수정하거나 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="42f89-106">Each user can modify or delete the subscriptions that he or she owns.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="42f89-107">[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)][!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]부터는 구독 소유권을 프로그래밍 방식으로 전송할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="42f89-107">Starting with [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)][!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] you can transfer the ownership of a subscription programmatically.</span></span> <span data-ttu-id="42f89-108">구독 소유권을 전송하는 데 사용할 수 있는 사용자 인터페이스는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="42f89-108">There is no user interface you can use to transfer ownership of subscriptions.</span></span> <span data-ttu-id="42f89-109">자세한 내용은 <xref:ReportService2010.ReportingService2010.ChangeSubscriptionOwner%2A>를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="42f89-109">For more information, see <xref:ReportService2010.ReportingService2010.ChangeSubscriptionOwner%2A></span></span>  
  
 <span data-ttu-id="42f89-110">**RSReportServer.config** 구성 파일 설정에 따라 사용자는 구독에 더 많은 사용자를 추가할 수 있습니다. 예를 들어 관리자가 자신의 부하 직원에 대 한 전자 메일 주소를 추가 하 여 각 보고서의 복사본을 받을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="42f89-110">Depending on **RSReportServer.config** configuration file settings, users may be able to add more users to a subscription (for example, a manager adds the e-mail addresses of his or her direct reports so that they each receive a copy of the report).</span></span> <span data-ttu-id="42f89-111">이러한 기능의 지원 여부는 개별 구독을 정의할 때 받는 사람: 필드가 표시되는지 여부에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="42f89-111">Whether this is supported depends on whether the To: field is visible when defining individual subscriptions.</span></span> <span data-ttu-id="42f89-112">자세한 내용은 [SSRS Configuration Manager&#41;&#40;전자 메일 배달에 대 한 보고서 서버 구성 ](../../sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="42f89-112">For more information, see [Configure a Report Server for E-Mail Delivery &#40;SSRS Configuration Manager&#41;](../../sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md).</span></span>  
  
 <span data-ttu-id="42f89-113">이 항목에서는 개별 사용자가 만들고 관리하는 표준 구독에 대한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="42f89-113">This topic provides information about standard subscriptions that are created and managed by individual users.</span></span> <span data-ttu-id="42f89-114">데이터 기반 구독의 경우 다른 요구 사항과 단계가 필요하며 이에 대해서는 별도의 항목에 설명되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="42f89-114">Data-driven subscriptions have different requirements and steps, and are discussed in a separate topic.</span></span> <span data-ttu-id="42f89-115">자세한 내용은 [데이터 기반 구독 만들기, 수정 및 삭제](data-driven-subscriptions.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="42f89-115">For more information, see [Create, Modify, and Delete a Data-Driven Subscription](data-driven-subscriptions.md).</span></span>  
  
 <span data-ttu-id="42f89-116">이 항목의 내용:</span><span class="sxs-lookup"><span data-stu-id="42f89-116">In this topic:</span></span>  
  
-   [<span data-ttu-id="42f89-117">구독을 만들려면</span><span class="sxs-lookup"><span data-stu-id="42f89-117">To Create a Subscription</span></span>](#bkmk_create_subscription)  
  
-   [<span data-ttu-id="42f89-118">파일 공유 구독을 만들려면</span><span class="sxs-lookup"><span data-stu-id="42f89-118">To Create a File Share Subscription</span></span>](#bkmk_create_fileshare_subscription)  
  
-   [<span data-ttu-id="42f89-119">전자 메일 구독을 만들려면</span><span class="sxs-lookup"><span data-stu-id="42f89-119">To Create an E-mail Subscription</span></span>](#bkmk_create_email_subscription)  
  
-   [<span data-ttu-id="42f89-120">구독을 수정 하려면</span><span class="sxs-lookup"><span data-stu-id="42f89-120">To Modify a Subscription</span></span>](#bkmk_modify_subscription)  
  
-   [<span data-ttu-id="42f89-121">구독을 삭제 하려면</span><span class="sxs-lookup"><span data-stu-id="42f89-121">To Delete a Subscription</span></span>](#bkmk_delete_subscription)  
  
##  <a name="to-create-a-subscription"></a><a name="bkmk_create_subscription"></a><span data-ttu-id="42f89-122">구독을 만들려면</span><span class="sxs-lookup"><span data-stu-id="42f89-122">To Create a Subscription</span></span>  
 <span data-ttu-id="42f89-123">구독을 만들려면 보고서 서버 배포에 적합한 도구 및 방법을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="42f89-123">To create a subscription, choose the tool and approach that is valid for your report server deployment:</span></span>  
  
-   <span data-ttu-id="42f89-124">이 항목에서는 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 보고서 관리자를 사용하여 기본 모드 보고서 서버에서 구독을 만드는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="42f89-124">The content in this topic explains how to create subscriptions on a native mode report server using [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Report Manager.</span></span> <span data-ttu-id="42f89-125">구독을 정의한 후에는 보고서 관리자의 내 구독 페이지 또는 특정 보고서의 **구독** 탭을 통해 구독에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="42f89-125">After you define a subscription, you can access it in Report Manager through the My Subscriptions page or the **Subscriptions** tab of a specific report.</span></span>  
  
-   <span data-ttu-id="42f89-126">[Sharepoint 모드 보고서 서버에 대 한 구독 만들기 및 관리](create-and-manage-subscriptions-for-sharepoint-mode-report-servers.md) sharepoint 사이트의 응용 프로그램 페이지를 사용 하 여 sharepoint 통합 모드로 실행 되는 보고서 서버에서 보고서를 구독 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="42f89-126">[Create and Manage Subscriptions for SharePoint Mode Report Servers](create-and-manage-subscriptions-for-sharepoint-mode-report-servers.md) explains how to use the application pages in a SharePoint site to subscribe to reports on a report server that runs in SharePoint integrated mode.</span></span>  
  
 <span data-ttu-id="42f89-127">이 항목에서는 전자 메일 구독 및 파일 공유 배달 구독을 만드는 방법을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="42f89-127">This topic provides instructions for creating an e-mail subscription and a file share delivery subscription.</span></span>  
  
-   <span data-ttu-id="42f89-128">전자 메일 배달을 사용하려면 구독을 만들기 전에 SMTP 서버 또는 게이트웨이 연결에 대해 보고서 서버를 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="42f89-128">To use e-mail delivery, the report server must be configured for an SMTP server or gateway connection before you create the subscription.</span></span>  
  
-   <span data-ttu-id="42f89-129">파일 공유 배달을 이용하려면 먼저 대상 폴더를 정의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="42f89-129">To use file share delivery, you must have target folder already defined.</span></span> <span data-ttu-id="42f89-130">자세한 내용은 [SSRS Configuration Manager&#41;&#40;전자 메일 배달에 대 한 보고서 서버 구성 ](../../sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="42f89-130">For more information, see [Configure a Report Server for E-Mail Delivery &#40;SSRS Configuration Manager&#41;](../../sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md).</span></span>  
  
 <span data-ttu-id="42f89-131">보고서를 구독하려면 먼저 저장된 자격 증명을 사용하거나 자격 증명을 사용하지 않도록 보고서 데이터 원본을 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="42f89-131">Before you can subscribe to a report, the report data source must be configured to use stored credentials or no credentials.</span></span> <span data-ttu-id="42f89-132">자세한 내용은 [Reporting Services 데이터 원본에 자격 증명 저장](../report-data/store-credentials-in-a-reporting-services-data-source.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="42f89-132">For more information, see [Store Credentials in a Reporting Services Data Source](../report-data/store-credentials-in-a-reporting-services-data-source.md).</span></span> <span data-ttu-id="42f89-133">그렇지 않으면 **새 구독** 단추를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="42f89-133">If it does not, the **New Subscription** button is not available.</span></span>  
  
 <span data-ttu-id="42f89-134">이 항목에서는 데이터 기반 구독을 만드는 방법에 대해 설명하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="42f89-134">This topic does not explain how to create a data-driven subscription.</span></span> <span data-ttu-id="42f89-135">데이터 기반 구독을 만드는 방법에 대한 자세한 내용은 [데이터 기반 구독 만들기&#40;SSRS 자습서&#41;](../create-a-data-driven-subscription-ssrs-tutorial.md)를 참조하거나 보고서 관리자의 데이터 기반 구독 만들기 페이지에 대한 온라인 도움말을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="42f89-135">For instructions on how to create a data-driven subscription, see [Create a Data-Driven Subscription &#40;SSRS Tutorial&#41;](../create-a-data-driven-subscription-ssrs-tutorial.md) or the online help for the Create a Data-driven Subscription page in Report Manager.</span></span>  
  
###  <a name="to-create-a-file-share-subscription"></a><a name="bkmk_create_fileshare_subscription"></a><span data-ttu-id="42f89-136">파일 공유 구독을 만들려면</span><span class="sxs-lookup"><span data-stu-id="42f89-136">To Create a File Share Subscription</span></span>  
  
1.  <span data-ttu-id="42f89-137">[보고서 관리자&#40;SSRS 기본 모드&#41;](../report-manager-ssrs-native-mode.md)를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="42f89-137">Start [Report Manager  &#40;SSRS Native Mode&#41;](../report-manager-ssrs-native-mode.md).</span></span>  
  
2.  <span data-ttu-id="42f89-138">보고서 관리자의 **내용** 페이지에서 구독할 보고서로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="42f89-138">In Report Manager, on the **Contents** page, navigate to the report you want to subscribe to.</span></span> <span data-ttu-id="42f89-139">보고서를 클릭하여 엽니다.</span><span class="sxs-lookup"><span data-stu-id="42f89-139">Click the report to open it.</span></span>  
  
3.  <span data-ttu-id="42f89-140">**구독** 탭을 클릭한 후 **새 구독**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="42f89-140">Click the **Subscriptions** tab, and then click **New Subscription**.</span></span>  
  
4.  <span data-ttu-id="42f89-141">**배달 방법**에서 **Windows 파일 공유**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="42f89-141">In **Delivered by**, select **Windows File Share**.</span></span>  
  
5.  <span data-ttu-id="42f89-142">**파일 이름**에 보고서의 파일 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="42f89-142">In **File Name**, type a file name for the report.</span></span>  
  
6.  <span data-ttu-id="42f89-143">**파일을 만들 때 파일 확장명 추가**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="42f89-143">Select **Add a file extension when the file is created**.</span></span> <span data-ttu-id="42f89-144">이 옵션은 파일 이름에 3자로 된 파일 확장명을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="42f89-144">This option adds a three-character file extension to the file name.</span></span> <span data-ttu-id="42f89-145">파일 확장명은 선택하는 보고서 출력 형식에 따라 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="42f89-145">The file extension is determined by the report output format you select.</span></span>  
  
7.  <span data-ttu-id="42f89-146">**경로** 텍스트 상자에 보고서를 배달 하려는 기존 폴더에 대 한 UNC (범용 명명 규칙) 경로를 입력 합니다 (예: \\ \\<servername \> \\<myreports \> ).</span><span class="sxs-lookup"><span data-stu-id="42f89-146">In the **Path** text box, type a Universal Naming Convention (UNC) path to an existing folder where you want to deliver the reports (for example, \\\\<servername\>\\<myreports\>).</span></span> <span data-ttu-id="42f89-147">경로의 시작 부분에는 백슬래시 문자를 두 번 넣고</span><span class="sxs-lookup"><span data-stu-id="42f89-147">Include double backslash characters at the beginning of the path.</span></span> <span data-ttu-id="42f89-148">뒷부분에는 백슬래시를 지정하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="42f89-148">Do not specify a trailing backslash.</span></span>  
  
8.  <span data-ttu-id="42f89-149">렌더링 형식에서 파일 배달에 대한 보고서 출력 형식을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="42f89-149">In Render Format, select a report output format for file delivery.</span></span> <span data-ttu-id="42f89-150">보고서를 열 때 사용할 데스크톱 애플리케이션에 맞는 형식을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="42f89-150">Choose a format that corresponds to the desktop application that will be used to open the report.</span></span> <span data-ttu-id="42f89-151">보고서를 단일 스트림으로 렌더링하지 않거나 정적 파일(예: HTML 4.0)에서 지원될 수 없는 대화형 작업을 발생시키는 형식은 사용하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="42f89-151">Avoid formats that do not render a report in a single stream or that introduce interactivity that cannot be supported in a static file (for example, HTML 4.0).</span></span>  
  
9. <span data-ttu-id="42f89-152">사용자 **이름** 및 **암호** 텍스트 상자에서 *\<domain>* \\ 사용자 이름 형식을 사용 하 여 파일 공유에 액세스 하는 데 필요한 자격 증명을 지정 합니다 *\<user name>* .</span><span class="sxs-lookup"><span data-stu-id="42f89-152">In the **User name** and **Password** text boxes, specify the credentials required to access the file share, using the format *\<domain>*\\*\<user name>* for the user name.</span></span>  
  
10. <span data-ttu-id="42f89-153">덮어쓰기 옵션을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="42f89-153">Specify overwrite options.</span></span> <span data-ttu-id="42f89-154">**이전 버전이 있으면 파일을 덮어쓰지 않음**옵션을 클릭한 경우 기존 파일이 검색되면 배달이 수행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="42f89-154">If you click **Do not overwrite the file if a previous version exists**, the delivery will not occur if an existing file is detected.</span></span> <span data-ttu-id="42f89-155">**새 버전 추가 시 파일 이름 자동 증가**를 클릭한 경우 보고서 서버는 이름이 같은 기존 파일과 구분할 수 있도록 파일 이름에 번호를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="42f89-155">If you click **Increment file names as newer versions are added**, the report server appends a number to the file name to distinguish it from existing files of the same name.</span></span>  
  
11. <span data-ttu-id="42f89-156">보고서를 배달할 시기를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="42f89-156">Specify when you want the report delivered:</span></span>  
  
    -   <span data-ttu-id="42f89-157">배달 시간을 예약하려면 **예약된 보고서 실행이 완료되었을 때** 를 클릭하고 **일정 선택** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="42f89-157">To schedule a delivery time, click **When the scheduled report run is complete** and click the **Select Schedule** button.</span></span> <span data-ttu-id="42f89-158">일정 페이지가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="42f89-158">A schedule page opens.</span></span>  
  
    -   <span data-ttu-id="42f89-159">사용할 날짜, 시간 및 되풀이 정보가 이미 있는 미리 정의된 공유 일정을 선택하려면 **공유 일정**을 클릭한 다음 사용할 일정을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="42f89-159">To select a predefined shared schedule that already has the date, time, and recurrence information that you want to use, click **On a shared schedule**, and then select the schedule to use.</span></span>  
  
    -   <span data-ttu-id="42f89-160">보고서 스냅샷이 최신 버전으로 업데이트된 경우 보고서를 배달하려면**보고서 내용을 새로 고쳤을 때**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="42f89-160">To deliver the report when a report snapshot is updated with a newer version,click**When the report content is refreshed**.</span></span> <span data-ttu-id="42f89-161">예약된 간격으로 데이터를 검색하는 보고서를 구독하는 경우 데이터를 새로 고치는 데 사용되는 일정에 따라 구독이 처리되는 시기가 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="42f89-161">If you are subscribing to a report that retrieves data at scheduled intervals, the schedule used to refresh the data determines when your subscription is processed.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="42f89-162">이 옵션은 업데이트 일정과 이미 연결되어 있는 스냅샷에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="42f89-162">This option is available only for snapshots that are already associated with an update schedule.</span></span>  
  
12. <span data-ttu-id="42f89-163">매개 변수가 있는 보고서의 경우 이 구독에 대한 보고서에 사용할 매개 변수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="42f89-163">For parameterized reports, specify parameters to use for the report for this subscription.</span></span> <span data-ttu-id="42f89-164">이 매개 변수는 요청 시 실행 보고서나 다른 예약된 보고서를 실행하는 데 사용하는 매개 변수와 다를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="42f89-164">The parameters can be different from those used to run the report on demand or in other scheduled operations.</span></span>  
  
 <span data-ttu-id="42f89-165">보고서는 정적 파일로 배달됩니다.</span><span class="sxs-lookup"><span data-stu-id="42f89-165">The report is delivered as a static file.</span></span> <span data-ttu-id="42f89-166">보고서에 대화형 기능(예: 추가 행과 열에 대한 링크)이 있는 경우 해당 기능은 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="42f89-166">If the report includes interactive features (for example, links to additional rows and columns), those features are not available.</span></span>  
  
###  <a name="to-create-an-e-mail-subscription"></a><a name="bkmk_create_email_subscription"></a><span data-ttu-id="42f89-167">전자 메일 구독을 만들려면</span><span class="sxs-lookup"><span data-stu-id="42f89-167">To Create an E-mail Subscription</span></span>  
  
1.  <span data-ttu-id="42f89-168">보고서 관리자의 **내용** 페이지에서 구독할 보고서로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="42f89-168">In Report Manager, on the **Contents** page, navigate to the report you want to subscribe to.</span></span> <span data-ttu-id="42f89-169">보고서를 클릭하여 엽니다.</span><span class="sxs-lookup"><span data-stu-id="42f89-169">Click the report to open it.</span></span>  
  
2.  <span data-ttu-id="42f89-170">**구독** 탭을 클릭한 후 **새 구독**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="42f89-170">Click the **Subscriptions** tab, and then click **New Subscription**.</span></span>  
  
3.  <span data-ttu-id="42f89-171">**배달 방법**에서 **전자 메일**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="42f89-171">In **Delivered by**, select **E-Mail**.</span></span> <span data-ttu-id="42f89-172">이 배달 유형을 사용할 수 없는 경우 보고서 서버가 전자 메일 구독에 대해 구성되지 않은 것입니다.</span><span class="sxs-lookup"><span data-stu-id="42f89-172">If this delivery type is not available, your report server has not been configured for e-mail subscriptions.</span></span>  
  
4.  <span data-ttu-id="42f89-173">**받는 사람 텍스트 상자** 에서 받는 사람: 필드의 받는 사람 이름은 도메인 사용자 계정을 사용 하 여 자체 주소가 지정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="42f89-173">In the **To** text box, the recipient name in the To: field is self-addressed using your domain user account.</span></span> <span data-ttu-id="42f89-174">보고서 서버 구성 설정에 따라 **받는 사람** 필드가 사용자 계정을 사용하여 자동으로 지정되는지 여부가 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="42f89-174">Report server configuration settings determine whether the **To** field is self-addressed with your user account.</span></span> <span data-ttu-id="42f89-175">구성 설정 전자 메일 주소를 변경 하는 방법에 대 한 자세한 내용은 [SSRS Configuration Manager&#41;&#40;전자 메일 배달에 대 한 보고서 서버 구성 ](../../sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="42f89-175">For more information about changing the configuration settings e-mail addresses, see [Configure a Report Server for E-Mail Delivery &#40;SSRS Configuration Manager&#41;](../../sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="42f89-176">사용 권한에 따라 보고서를 배달할 전자 메일 주소를 입력할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="42f89-176">Depending on your permissions, you might be able to type the e-mail address you want the report delivered to.</span></span> <span data-ttu-id="42f89-177">전자 메일 주소를 여러 개 지정하려면 세미콜론(;)으로 구분합니다.</span><span class="sxs-lookup"><span data-stu-id="42f89-177">To specify multiple e-mail addresses, separate them with a semicolon (;).</span></span> <span data-ttu-id="42f89-178">**참조**, **숨은 참조**및 **회신** 입력란에 메일 주소를 추가로 입력할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="42f89-178">You can also type additional e-mail addresses in the **Cc**, **Bcc**, and **Reply-To** text boxes.</span></span> <span data-ttu-id="42f89-179">이 작업을 수행하려면 모든 구독을 관리할 수 있는 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="42f89-179">This requires that you have permission to manage all subscriptions.</span></span>  
  
5.  <span data-ttu-id="42f89-180">다음과 같이 배달 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="42f89-180">Select the delivery options as follows:</span></span>  
  
    -   <span data-ttu-id="42f89-181">보고서의 복사본을 포함시키거나 첨부하려면 **보고서 포함**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="42f89-181">To embed or attach a copy of the report, select **Include Report**.</span></span> <span data-ttu-id="42f89-182">보고서 형식은 선택하는 렌더링 형식에 따라 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="42f89-182">The format of the report is determined by the rendering format you select.</span></span> <span data-ttu-id="42f89-183">보고서 크기가 전자 메일 시스템에 정의된 크기를 넘을 경우에는 이 옵션을 선택하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="42f89-183">Do not choose this option if you think the report size will exceed the limit defined for your e-mail system.</span></span>  
  
    -   <span data-ttu-id="42f89-184">전자 메일 메시지 본문에 보고서에 대 한 URL 링크를 포함 하려면 **링크 포함**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="42f89-184">To include a URL link to the report in the body of the e-mail message, select **Include Link**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="42f89-185">이러한 옵션을 선택하지 않으면 제목 줄의 알림 텍스트만 전송됩니다.</span><span class="sxs-lookup"><span data-stu-id="42f89-185">If you clear both of these options, only the notification text in the Subject line is sent.</span></span>  
  
6.  <span data-ttu-id="42f89-186">**렌더링 형식** 목록 상자에서 렌더링 형식을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="42f89-186">Choose a rendering format from the **Render Format** list box.</span></span> <span data-ttu-id="42f89-187">이 옵션은 **보고서 포함** 을 선택하여 보고서 복사본을 포함시키거나 첨부한 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="42f89-187">This option is available if you select **Include Report** to embed or attach a copy of the report.</span></span>  
  
    -   <span data-ttu-id="42f89-188">메일 메시지 본문에 보고서를 포함하려면 **웹 보관 파일**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="42f89-188">To embed the report in the body of the e-mail message, select **Web archive**.</span></span>  
  
    -   <span data-ttu-id="42f89-189">보고서를 첨부 파일로 전송하려면 다른 렌더링 형식을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="42f89-189">To send the report as an attachment, choose any of the other rendering formats.</span></span>  
  
7.  <span data-ttu-id="42f89-190">**중요도** 목록 상자에서 중요도를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="42f89-190">Select a priority from the **Priority** list box.</span></span> <span data-ttu-id="42f89-191">[!INCLUDE[msCoName](../../includes/msconame-md.md)] Exchange에서는 이 설정에 따라 메일 메시지의 중요도 수준 플래그가 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="42f89-191">In [!INCLUDE[msCoName](../../includes/msconame-md.md)] Exchange, this setting sets a flag for the importance level of the e-mail message.</span></span>  
  
8.  <span data-ttu-id="42f89-192">보고서를 배달할 시기를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="42f89-192">Specify when you want the report delivered:</span></span>  
  
    -   <span data-ttu-id="42f89-193">배달 시간을 예약하려면 **예약된 보고서 실행이 완료되었을 때** , **일정 선택**을 차례로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="42f89-193">To schedule a delivery time, click **When the scheduled report run is complete** and click **Select Schedule**.</span></span> <span data-ttu-id="42f89-194">일정 페이지가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="42f89-194">A schedule page opens for you.</span></span>  
  
    -   <span data-ttu-id="42f89-195">사용할 날짜, 시간 및 되풀이 정보가 이미 있는 미리 정의된 공유 일정을 선택하려면 **공유 일정**을 클릭한 다음 사용할 일정을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="42f89-195">To select a predefined shared schedule that already has the date, time, and recurrence information that you want to use, click **On a shared schedule**, and then select the schedule to use.</span></span>  
  
    -   <span data-ttu-id="42f89-196">보고서 스냅샷이 최신 버전으로 업데이트된 경우 보고서를 배달하려면**보고서 내용을 새로 고쳤을 때**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="42f89-196">To deliver the report when a report snapshot is updated with a newer version,click**When the report content is refreshed**.</span></span> <span data-ttu-id="42f89-197">예약된 간격으로 데이터를 검색하는 보고서를 구독하는 경우 데이터를 새로 고치는 데 사용되는 일정에 따라 구독이 처리되는 시기가 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="42f89-197">If you are subscribing to a report that retrieves data at scheduled intervals, the schedule used to refresh the data determines when your subscription is processed.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="42f89-198">이 옵션은 업데이트 일정과 이미 연결되어 있는 스냅샷에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="42f89-198">This option is available only for snapshots that are already associated with an update schedule.</span></span>  
  
9. <span data-ttu-id="42f89-199">매개 변수가 있는 보고서의 경우 이 구독에 대한 보고서에 사용할 매개 변수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="42f89-199">For parameterized reports, specify parameters to use for the report for this subscription.</span></span> <span data-ttu-id="42f89-200">사용자가 지정한 매개 변수는 요청 시 실행 보고서나 다른 일정이 예약된 보고서를 실행하는 데 사용하는 매개 변수와 다를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="42f89-200">The parameters that you specify can be different from those used to run the report on demand or in other scheduled operations.</span></span>  
  
##  <a name="to-modify-a-subscription"></a><a name="bkmk_modify_subscription"></a><span data-ttu-id="42f89-201">구독을 수정 하려면</span><span class="sxs-lookup"><span data-stu-id="42f89-201">To Modify a Subscription</span></span>  
 <span data-ttu-id="42f89-202">언제든지 구독을 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="42f89-202">You can modify a subscription at any time.</span></span> <span data-ttu-id="42f89-203">처리 중인 구독을 수정한 경우 배달 확장 프로그램에서 구독 데이터를 받기 전에 구독이 보고서 서버 데이터베이스에 저장되면 업데이트된 설정이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="42f89-203">If you modify a subscription while it is being processed, the updated settings are used if they are saved to the report server database before the delivery extension receives the subscription data.</span></span> <span data-ttu-id="42f89-204">그렇지 않으면 기존 설정이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="42f89-204">Otherwise, the existing settings are used.</span></span>  
  
 <span data-ttu-id="42f89-205">구독을 찾으려면 **내 구독** 페이지를 사용하거나 보고서와 관련된 구독 정의를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="42f89-205">To locate a subscription, use the **My Subscriptions** page or view the subscription definitions that are associated with a report.</span></span> <span data-ttu-id="42f89-206">구독을 직접 검색하거나 소유자 이름, 트리거 정보, 상태 정보 등을 기반으로 구독을 검색할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="42f89-206">You cannot search for subscriptions directly, nor can you search for a subscription based on owner name, trigger information, status information, and so forth.</span></span>  
  
 <span data-ttu-id="42f89-207">보고서 서버 관리자도 구독을 수정하거나 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="42f89-207">Subscriptions can also be modified or deleted by report server administrators.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="42f89-208">보고서 서버 관리자라 하더라도 지정된 보고서 서버에서 사용 중인 각각의 구독을 한 장소에서 모두 관리할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="42f89-208">A report server administrator cannot manage from one place all the individual subscriptions that are in use on a given report server.</span></span> <span data-ttu-id="42f89-209">그러나 보고서 서버 관리자는 각 구독에 액세스하여 수정하거나 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="42f89-209">However, report server administrators can access each individual subscription to modify or delete it.</span></span>  
  
##  <a name="to-delete-a-subscription"></a><a name="bkmk_delete_subscription"></a><span data-ttu-id="42f89-210">구독을 삭제 하려면</span><span class="sxs-lookup"><span data-stu-id="42f89-210">To Delete a Subscription</span></span>  
 <span data-ttu-id="42f89-211">구독을 삭제하려면</span><span class="sxs-lookup"><span data-stu-id="42f89-211">To delete a subscription"</span></span>  
  
1.  <span data-ttu-id="42f89-212">[보고서 관리자&#40;SSRS 기본 모드&#41;](../report-manager-ssrs-native-mode.md)를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="42f89-212">Start [Report Manager  &#40;SSRS Native Mode&#41;](../report-manager-ssrs-native-mode.md).</span></span>  
  
2.  <span data-ttu-id="42f89-213">보고서 관리자의 일반 도구 모음에서 **내 구독** 을 클릭하고 수정하거나 삭제할 구독으로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="42f89-213">In Report Manager, click **My Subscriptions** on the global toolbar and navigate to the subscription you want to modify or delete.</span></span>  
  
3.  <span data-ttu-id="42f89-214">또는 열린 보고서의 **구독** 탭에서 수정하거나 삭제할 구독을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="42f89-214">Alternatively, on the **Subscriptions** tab of an open report, find the subscription that you want to modify or delete.</span></span> <span data-ttu-id="42f89-215">다음 중 하나를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="42f89-215">Perform one of the following:</span></span>  
  
    1.  <span data-ttu-id="42f89-216">구독을 수정하려면 **편집**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="42f89-216">To modify a subscription, click **Edit**.</span></span>  
  
    2.  <span data-ttu-id="42f89-217">구독을 삭제하려면 구독 옆의 확인란을 선택한 다음 **삭제**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="42f89-217">To delete a subscription, select the check box next to the subscription, and then click **Delete**.</span></span>  
  
 <span data-ttu-id="42f89-218">이 항목에서는 보고서 서버에서 현재 처리 중인 구독을 취소하는 방법은 설명하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="42f89-218">This topic does not explain how to cancel a subscription that is currently processing on the report server.</span></span> <span data-ttu-id="42f89-219">구독 취소에 대 한 자세한 내용은 [실행 중인 프로세스 관리](manage-a-running-process.md) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="42f89-219">For more information about canceling subscriptions, see [Manage a Running Process](manage-a-running-process.md)</span></span>  
  
 <span data-ttu-id="42f89-220">구독을 종료하려는 경우 해당 구독을 쉽게 찾을 수 없으면 받고 있는 보고서를 확인하여 이름으로 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="42f89-220">If you want to end a subscription and you cannot locate the subscription easily, make a note of the report you are receiving and search for it by name.</span></span> <span data-ttu-id="42f89-221">보고서에 액세스되면 구독에서 자신의 이름을 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="42f89-221">Once you access the report, you can remove yourself from the subscription.</span></span> <span data-ttu-id="42f89-222">구독을 찾을 수 없는 경우 해당 구독이 데이터 기반 구독일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="42f89-222">If you cannot locate the subscription, the subscription may be a data-driven subscription.</span></span> <span data-ttu-id="42f89-223">자세한 내용은 보고서 서버 관리자에게 문의하세요.</span><span class="sxs-lookup"><span data-stu-id="42f89-223">For more information, see your report server administrator.</span></span>  
  
 <span data-ttu-id="42f89-224">기본 보고서가 삭제되면 구독이 자동으로 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="42f89-224">A subscription is deleted automatically if the underlying report is deleted.</span></span> <span data-ttu-id="42f89-225">처리 중인 구독을 삭제하는 경우 배달 확장 프로그램에서 구독 데이터를 받기 전에 삭제 작업을 수행하면 구독이 중지됩니다.</span><span class="sxs-lookup"><span data-stu-id="42f89-225">If you delete a subscription while it is being processed, the subscription stops if the delete operation occurs before the delivery extension receives subscription data.</span></span> <span data-ttu-id="42f89-226">그렇지 않으면 구독이 계속해서 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="42f89-226">Otherwise, the subscription continues to be processed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42f89-227">참고 항목</span><span class="sxs-lookup"><span data-stu-id="42f89-227">See Also</span></span>  
 <span data-ttu-id="42f89-228">[태스크 및 권한](../security/tasks-and-permissions.md) </span><span class="sxs-lookup"><span data-stu-id="42f89-228">[Tasks and Permissions](../security/tasks-and-permissions.md) </span></span>  
 <span data-ttu-id="42f89-229">[SharePoint 모드 보고서 서버 구독 만들기 및 관리](create-and-manage-subscriptions-for-sharepoint-mode-report-servers.md) </span><span class="sxs-lookup"><span data-stu-id="42f89-229">[Create and Manage Subscriptions for SharePoint Mode Report Servers](create-and-manage-subscriptions-for-sharepoint-mode-report-servers.md) </span></span>  
 <span data-ttu-id="42f89-230">[기본 모드 보고서 서버 구독 만들기 및 관리](../create-manage-subscriptions-native-mode-report-servers.md) </span><span class="sxs-lookup"><span data-stu-id="42f89-230">[Create and Manage Subscriptions for Native Mode Report Servers](../create-manage-subscriptions-native-mode-report-servers.md) </span></span>  
 <span data-ttu-id="42f89-231">[Data-Driven Subscriptions](data-driven-subscriptions.md) </span><span class="sxs-lookup"><span data-stu-id="42f89-231">[Data-Driven Subscriptions](data-driven-subscriptions.md) </span></span>  
 <span data-ttu-id="42f89-232">[구독 및 배달&#40;Reporting Services&#41;](subscriptions-and-delivery-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="42f89-232">[Subscriptions and Delivery &#40;Reporting Services&#41;](subscriptions-and-delivery-reporting-services.md) </span></span>  
 <span data-ttu-id="42f89-233">[보고서 관리자&#40;SSRS 기본 모드&#41;](../report-manager-ssrs-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="42f89-233">[Report Manager  &#40;SSRS Native Mode&#41;](../report-manager-ssrs-native-mode.md) </span></span>  
 [<span data-ttu-id="42f89-234">내 구독 사용</span><span class="sxs-lookup"><span data-stu-id="42f89-234">Use My Subscriptions</span></span>](use-my-subscriptions-native-mode-report-server.md)  
  
  
