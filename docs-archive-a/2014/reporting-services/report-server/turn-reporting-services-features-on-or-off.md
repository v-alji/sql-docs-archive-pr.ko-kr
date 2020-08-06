---
title: Reporting Services 기능 설정 또는 해제 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- Reporting Services, configuration
- security [Reporting Services], strategies
ms.assetid: b69db02a-43a7-4fdc-ad9b-438d817a7f83
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f56f9984b5b02431db23b782652e5575af557bdb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650617"
---
# <a name="turn-reporting-services-features-on-or-off"></a><span data-ttu-id="e6702-102">Reporting Services 기능 설정 또는 해제</span><span class="sxs-lookup"><span data-stu-id="e6702-102">Turn Reporting Services Features On or Off</span></span>
  <span data-ttu-id="e6702-103">프로덕션 보고서 서버의 공격 노출 영역을 줄이기 위한 잠금 전략의 일환으로 사용하지 않는 보고서 서버 기능을 해제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e6702-103">You can turn off report server features that you do not use as part of a lockdown strategy for reducing the attack surface of a production report server.</span></span> <span data-ttu-id="e6702-104">대부분의 경우에는 여러 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 기능을 동시에 실행하여 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]에서 제공하는 모든 기능을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6702-104">In most cases, you will want to run [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] features concurrently to use all of the functionality provided in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="e6702-105">그러나 배포 모델에 따라서는 필요하지 않은 기능을 비활성화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e6702-105">However, depending on your deployment model, you can disable the features that you do not require.</span></span> <span data-ttu-id="e6702-106">예를 들어 모든 보고서 처리가 예약된 작업으로 구성된 경우 백그라운드 처리만 활성화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e6702-106">For example, you can enable only the background processing if all report processing is configured as scheduled operations.</span></span> <span data-ttu-id="e6702-107">마찬가지로 요청 시 실행되는 대화형 보고서만 원하는 경우에는 보고서 서버 웹 서비스만 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e6702-107">Similarly, you can run just the Report Server Web service if you only want interactive, on-demand reporting.</span></span>  
  
 <span data-ttu-id="e6702-108">이 항목의 절차에서는 기본 모드 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 기능을 해제하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="e6702-108">The procedures in this topic show you how to turn off native mode [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] features.</span></span> <span data-ttu-id="e6702-109">`RsReportServer.config` 파일을 직접 편집하거나 **에서 정책 기반 관리의** Reporting Services에 대한 노출 영역 구성 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]패싯을 사용하는 등의 다양한 방법으로 기능을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e6702-109">Features can be configured in different ways, such as by editing the `RsReportServer.config` file directly or by using the **Surface Area Configuration for Reporting Services** facet of Policy-Based Management in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="e6702-110">해당 링크를 사용하여 기능을 설정하거나 해제하는 방법을 설명하는 절차를 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e6702-110">Use the links to locate the procedure or procedures that explain how to turn a feature on or off:</span></span>  
  
-   [<span data-ttu-id="e6702-111">보고서 서버 웹 서비스</span><span class="sxs-lookup"><span data-stu-id="e6702-111">Report Server Web service</span></span>](#RSWebSvc)  
  
-   [<span data-ttu-id="e6702-112">예약된 이벤트 및 처리</span><span class="sxs-lookup"><span data-stu-id="e6702-112">Scheduled events and processing</span></span>](#Sched)  
  
-   [<span data-ttu-id="e6702-113">보고서 관리자</span><span class="sxs-lookup"><span data-stu-id="e6702-113">Report Manager</span></span>](#ReportManager)  
  
-   [<span data-ttu-id="e6702-114">보고서 작성기</span><span class="sxs-lookup"><span data-stu-id="e6702-114">Report Builder</span></span>](#ReportBuilder)  
  
-   [<span data-ttu-id="e6702-115">보고서 데이터 원본에 대 한 Windows 통합 보안</span><span class="sxs-lookup"><span data-stu-id="e6702-115">Windows Integrated security for report data sources</span></span>](#WinIntSec)  
  
##  <a name="report-server-web-service"></a><a name="RSWebSvc"></a><span data-ttu-id="e6702-116">보고서 서버 웹 서비스</span><span class="sxs-lookup"><span data-stu-id="e6702-116">Report Server Web Service</span></span>  
  
#### <a name="to-turn-on-or-off-the-report-server-web-service-by-editing-configuration"></a><span data-ttu-id="e6702-117">구성을 편집하여 보고서 서버 웹 서비스를 설정하거나 해제하려면</span><span class="sxs-lookup"><span data-stu-id="e6702-117">To turn on or off the Report Server Web service by editing configuration</span></span>  
  
1.  <span data-ttu-id="e6702-118">텍스트 편집기에서 `RsReportServer.config` 파일을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="e6702-118">Open the `RsReportServer.config` file in a text editor.</span></span> <span data-ttu-id="e6702-119">자세한 내용은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 온라인 설명서의 [Reporting Services 구성 파일 수정&#40;RSreportserver.config&#41;](modify-a-reporting-services-configuration-file-rsreportserver-config.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e6702-119">For more information, see [Modify a Reporting Services Configuration File &#40;RSreportserver.config&#41;](modify-a-reporting-services-configuration-file-rsreportserver-config.md) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
2.  <span data-ttu-id="e6702-120">보고서 서버 웹 서비스를 활성화하려면 `IsWebServiceEnabled`를 `true`로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="e6702-120">To turn on the Report Server Web service, set `IsWebServiceEnabled` to `true`:</span></span>  
  
    ```  
    <IsWebServiceEnabled>true</IsWebServiceEnabled>  
    ```  
  
3.  <span data-ttu-id="e6702-121">보고서 서버 웹 서비스를 해제하려면 `IsWebServiceEnabled`를 `false`로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="e6702-121">To turn off the Report Server Web service, set `IsWebServiceEnabled` to `false`:</span></span>  
  
    ```  
    <IsWebServiceEnabled>false</IsWebServiceEnabled>  
    ```  
  
4.  <span data-ttu-id="e6702-122">변경 내용을 저장한 다음 파일을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="e6702-122">Save your changes and then close the file.</span></span>  
  
#### <a name="to-turn-on-or-off-the-report-server-web-service-by-using-sql-server-management-studio"></a><span data-ttu-id="e6702-123">SQL Server Management Studio를 사용하여 보고서 서버 웹 서비스를 설정하거나 해제하려면</span><span class="sxs-lookup"><span data-stu-id="e6702-123">To turn on or off the Report Server Web service by using SQL Server Management Studio</span></span>  
  
1.  <span data-ttu-id="e6702-124">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 를 열고 구성할 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="e6702-124">Open [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] and connect to the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] instance that you want to configure.</span></span>  
  
2.  <span data-ttu-id="e6702-125">개체 탐색기에서 노드를 마우스 오른쪽 단추로 클릭 하 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 고 **정책**을 가리킨 다음 **패싯**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6702-125">In Object Explorer, right-click the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] node, point to **Policies**, and click **Facets**.</span></span>  
  
3.  <span data-ttu-id="e6702-126">**패싯** 목록에서 **Reporting Services에 대한 노출 영역**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e6702-126">In the **Facet** list, select **Surface Area Configuration for Reporting Services**.</span></span>  
  
4.  <span data-ttu-id="e6702-127">**패싯 속성**아래에서 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="e6702-127">Under **Facet Properties**:</span></span>  
  
    -   <span data-ttu-id="e6702-128">보고서 서버 웹 서비스를 활성화 하려면 **Webserviceandhttpaccessenabled** 를로 설정 `True` 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6702-128">To turn on the Report Server Web service, set **WebServiceAndHTTPAccessEnabled** to `True`.</span></span>  
  
    -   <span data-ttu-id="e6702-129">보고서 서버 웹 서비스를 해제 하려면 **Webserviceandhttpaccessenabled** 를로 설정 `False` 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6702-129">To turn off the Report Server Web service, set **WebServiceAndHTTPAccessEnabled** to `False`.</span></span>  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
##  <a name="scheduled-events-and-delivery"></a><a name="Sched"></a> <span data-ttu-id="e6702-130">예약된 이벤트 및 배달</span><span class="sxs-lookup"><span data-stu-id="e6702-130">Scheduled Events and Delivery</span></span>  
  
#### <a name="to-turn-on-or-off-scheduled-events-and-delivery-by-editing-configuration"></a><span data-ttu-id="e6702-131">구성을 편집하여 예약된 이벤트 및 배달을 설정하거나 해제하려면</span><span class="sxs-lookup"><span data-stu-id="e6702-131">To turn on or off scheduled events and delivery by editing configuration</span></span>  
  
1.  <span data-ttu-id="e6702-132">텍스트 편집기에서 RsReportServer.config 파일을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="e6702-132">Open the RsReportServer.config file in a text editor.</span></span> <span data-ttu-id="e6702-133">자세한 내용은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 온라인 설명서의 [Reporting Services 구성 파일 수정&#40;RSreportserver.config&#41;](modify-a-reporting-services-configuration-file-rsreportserver-config.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e6702-133">For more information, see [Modify a Reporting Services Configuration File &#40;RSreportserver.config&#41;](modify-a-reporting-services-configuration-file-rsreportserver-config.md) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
2.  <span data-ttu-id="e6702-134">예약된 보고서 처리 및 배달을 활성화하려면 `IsSchedulingService`, `IsNotificationService` 및 `IsEventService`를 `true`로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="e6702-134">To turn on scheduled report processing and delivery, set `IsSchedulingService`, `IsNotificationService`, and `IsEventService` to `true`:</span></span>  
  
    ```  
    <IsSchedulingService>true</IsSchedulingService>  
    <IsNotificationService>true</IsNotificationService>  
    <IsEventService>true</IsEventService>  
    ```  
  
3.  <span data-ttu-id="e6702-135">예약된 보고서 처리 및 배달을 해제하려면 `IsSchedulingService`, `IsNotificationService` 및 `IsEventService`를 `false`로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="e6702-135">To turn off scheduled report processing and delivery, set `IsSchedulingService`, `IsNotificationService`, and `IsEventService` to `false`:</span></span>  
  
    ```  
    <IsSchedulingService>false</IsSchedulingService>  
    <IsNotificationService>false</IsNotificationService>  
    <IsEventService>false</IsEventService>  
    ```  
  
4.  <span data-ttu-id="e6702-136">변경 내용을 저장한 다음 파일을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="e6702-136">Save your changes and then close the file.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e6702-137">백그라운드 처리는 서버 작업에 필요한 유지 관리 기능을 제공하므로 완전히 해제할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e6702-137">You cannot turn off background processing completely because it provides database maintenance functionality that is required for server operations.</span></span>  
  
#### <a name="to-turn-on-or-off-scheduled-events-and-delivery-by-using-sql-server-management-studio"></a><span data-ttu-id="e6702-138">SQL Server Management Studio를 사용하여 예약된 이벤트 및 배달을 설정하거나 해제하려면</span><span class="sxs-lookup"><span data-stu-id="e6702-138">To turn on or off scheduled events and delivery by using SQL Server Management Studio</span></span>  
  
1.  <span data-ttu-id="e6702-139">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 를 열고 구성할 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="e6702-139">Open [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] and connect to the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] instance that you want to configure.</span></span>  
  
2.  <span data-ttu-id="e6702-140">개체 탐색기에서 노드를 마우스 오른쪽 단추로 클릭 하 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 고 **정책**을 가리킨 다음 **패싯**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6702-140">In Object Explorer, right-click the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] node, point to **Policies**, and click **Facets**.</span></span>  
  
3.  <span data-ttu-id="e6702-141">**패싯** 목록에서 **Reporting Services에 대한 노출 영역**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e6702-141">In the **Facet** list, select **Surface Area Configuration for Reporting Services**.</span></span>  
  
4.  <span data-ttu-id="e6702-142">**패싯 속성**아래에서 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="e6702-142">Under **Facet Properties**:</span></span>  
  
    -   <span data-ttu-id="e6702-143">예약 된 이벤트 및 배달을 설정 하려면 **ScheduleEventsAndReportDeliveryEnabled** 을로 설정 `True` 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6702-143">To turn on scheduled events and delivery, set **ScheduleEventsAndReportDeliveryEnabled** to `True`.</span></span>  
  
    -   <span data-ttu-id="e6702-144">예약 된 이벤트 및 배달을 해제 하려면 **ScheduleEventsAndReportDeliveryEnabled** 을로 설정 `False` 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6702-144">To turn off scheduled events and delivery, set **ScheduleEventsAndReportDeliveryEnabled** to `False`.</span></span>  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
> [!NOTE]  
>  <span data-ttu-id="e6702-145">백그라운드 처리는 서버 작업에 필요한 유지 관리 기능을 제공하므로 완전히 해제할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e6702-145">You cannot turn off background processing completely because it provides database maintenance functionality that is required for server operations.</span></span>  
  
##  <a name="report-manager"></a><a name="ReportManager"></a><span data-ttu-id="e6702-146">보고서 관리자</span><span class="sxs-lookup"><span data-stu-id="e6702-146">Report Manager</span></span>  
  
#### <a name="to-turn-on-or-off-report-manager-by-editing-configuration"></a><span data-ttu-id="e6702-147">구성을 편집하여 보고서 관리자를 설정하거나 해제하려면</span><span class="sxs-lookup"><span data-stu-id="e6702-147">To turn on or off Report Manager by editing configuration</span></span>  
  
1.  <span data-ttu-id="e6702-148">텍스트 편집기에서 RsReportServer.config 파일을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="e6702-148">Open the RsReportServer.config file in a text editor.</span></span> <span data-ttu-id="e6702-149">자세한 내용은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 온라인 설명서의 [Reporting Services 구성 파일 수정&#40;RSreportserver.config&#41;](modify-a-reporting-services-configuration-file-rsreportserver-config.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e6702-149">For instructions, see [Modify a Reporting Services Configuration File &#40;RSreportserver.config&#41;](modify-a-reporting-services-configuration-file-rsreportserver-config.md) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
2.  <span data-ttu-id="e6702-150">보고서 관리자를 활성화하려면 `IsReportManagerEnabled`를 `true`로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="e6702-150">To turn on Report Manager, set `IsReportManagerEnabled` to `true`:</span></span>  
  
    ```  
    <IsReportManagerEnabled>true</IsReportManagerEnabled>  
    ```  
  
3.  <span data-ttu-id="e6702-151">보고서 관리자를 해제하려면 `IsReportManagerEnabled`를 `false`로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="e6702-151">To turn off Report Manager, set `IsReportManagerEnabled` to `false`:</span></span>  
  
    ```  
    <IsReportManagerEnabled>false</IsReportManagerEnabled>  
    ```  
  
4.  <span data-ttu-id="e6702-152">변경 내용을 저장한 다음 파일을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="e6702-152">Save your changes and then close the file.</span></span>  
  
#### <a name="to-turn-on-or-off-report-manager-by-using-sql-server-management-studio"></a><span data-ttu-id="e6702-153">SQL Server Management Studio를 사용하여 보고서 관리자를 설정하거나 해제하려면</span><span class="sxs-lookup"><span data-stu-id="e6702-153">To turn on or off Report Manager by using SQL Server Management Studio</span></span>  
  
1.  <span data-ttu-id="e6702-154">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 를 열고 구성할 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="e6702-154">Open [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] and connect to the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] instance that you want to configure.</span></span>  
  
2.  <span data-ttu-id="e6702-155">**개체 탐색기**에서 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 노드를 마우스 오른쪽 단추로 클릭하고 **정책**을 가리킨 다음 **패싯**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e6702-155">In **Object Explorer**, right-click the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] node, point to **Policies**, and click **Facets**.</span></span>  
  
3.  <span data-ttu-id="e6702-156">**패싯** 목록에서 **Reporting Services에 대한 노출 영역**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e6702-156">In the **Facet** list, select **Surface Area Configuration for Reporting Services**.</span></span>  
  
4.  <span data-ttu-id="e6702-157">**패싯 속성**아래에서 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="e6702-157">Under **Facet Properties**:</span></span>  
  
    -   <span data-ttu-id="e6702-158">보고서 관리자 설정 하려면 **Reportmanagerenabled** 를로 설정 `True` 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6702-158">To turn on Report Manager, set **ReportManagerEnabled** to `True`.</span></span>  
  
    -   <span data-ttu-id="e6702-159">보고서 관리자 해제 하려면 **Reportmanagerenabled** 를로 설정 `False` 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6702-159">To turn off Report Manager, set **ReportManagerEnabled** to `False`.</span></span>  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
##  <a name="report-builder"></a><a name="ReportBuilder"></a> <span data-ttu-id="e6702-160">보고서 작성기</span><span class="sxs-lookup"><span data-stu-id="e6702-160">Report Builder</span></span>  
  
#### <a name="to-turn-on-or-off-report-builder-by-using-sql-server-management-studio"></a><span data-ttu-id="e6702-161">SQL Server Management Studio를 사용하여 보고서 작성기를 설정하거나 해제하려면</span><span class="sxs-lookup"><span data-stu-id="e6702-161">To turn on or off Report Builder by using SQL Server Management Studio</span></span>  
  
1.  <span data-ttu-id="e6702-162">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 를 열고 구성할 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="e6702-162">Open [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] and connect to the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] instance that you want to configure.</span></span>  
  
2.  <span data-ttu-id="e6702-163">개체 탐색기에서 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 노드를 마우스 오른쪽 단추로 클릭하고 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e6702-163">In Object Explorer, right-click the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] node, and click **Properties**.</span></span>  
  
3.  <span data-ttu-id="e6702-164">**서버 속성** 대화 상자의 **페이지 선택**아래에서 **보안**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e6702-164">In the **Server Properties** dialog box, under **Select a page**, click **Security**.</span></span>  
  
    -   <span data-ttu-id="e6702-165">보고서 작성기를 활성화하려면 **임시 보고서 실행 사용** 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e6702-165">To turn on Report Builder, select the **Enable ad hoc report executions** option.</span></span>  
  
    -   <span data-ttu-id="e6702-166">보고서 작성기를 해제하려면 **임시 보고서 실행 사용** 옵션의 선택을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="e6702-166">To turn off Report Builder, unselect the **Enable ad hoc report executions** option.</span></span>  
  
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
##  <a name="windows-integrated-security"></a><a name="WinIntSec"></a> <span data-ttu-id="e6702-167">Windows 통합 보안</span><span class="sxs-lookup"><span data-stu-id="e6702-167">Windows Integrated Security</span></span>  
  
#### <a name="to-turn-on-or-off-windows-integrated-security-by-using-sql-server-management-studio"></a><span data-ttu-id="e6702-168">SQL Server Management Studio를 사용하여 Windows 통합 보안을 설정하거나 해제하려면</span><span class="sxs-lookup"><span data-stu-id="e6702-168">To turn on or off Windows Integrated security by using SQL Server Management Studio</span></span>  
  
1.  <span data-ttu-id="e6702-169">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 를 열고 구성할 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="e6702-169">Open [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] and connect to the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] instance that you want to configure.</span></span>  
  
2.  <span data-ttu-id="e6702-170">개체 탐색기에서 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 노드를 마우스 오른쪽 단추로 클릭하고 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e6702-170">In Object Explorer, right-click the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] node, and click **Properties**.</span></span>  
  
3.  <span data-ttu-id="e6702-171">**서버 속성** 대화 상자의 **페이지 선택**아래에서 **보안**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e6702-171">In the **Server Properties** dialog box, under **Select a page**, click **Security**.</span></span>  
  
    -   <span data-ttu-id="e6702-172">Windows 통합 보안을 활성화하려면 **보고서 데이터 원본에 대한 Windows 통합 보안 사용** 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e6702-172">To turn on Windows Integrated security, select the **Enable Windows Integrated security for report data sources** option.</span></span>  
  
    -   <span data-ttu-id="e6702-173">Windows 통합 보안을 해제하려면 **보고서 데이터 원본에 대한 Windows 통합 보안 사용** 옵션의 선택을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="e6702-173">To turn off Windows integrated security, unselect the **Enable Windows Integrated security for report data sources** option.</span></span>  
  
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="e6702-174">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e6702-174">See Also</span></span>  
 [<span data-ttu-id="e6702-175">Reporting Services 구성 관리자&#40;기본 모드&#41;</span><span class="sxs-lookup"><span data-stu-id="e6702-175">Reporting Services Configuration Manager &#40;Native Mode&#41;</span></span>](../../sql-server/install/reporting-services-configuration-manager-native-mode.md)  
  
  
