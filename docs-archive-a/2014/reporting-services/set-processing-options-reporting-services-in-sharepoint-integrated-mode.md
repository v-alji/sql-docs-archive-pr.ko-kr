---
title: 처리 옵션 설정 (SharePoint 통합 모드의 Reporting Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- SharePoint integration [Reporting Services], content management
- snapshots [Reporting Services], creating
ms.assetid: 453b19a1-739a-4b67-aeea-2069b52204e1
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 8c33b205a702d4ab77abf74154232990da9840b6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87732387"
---
# <a name="set-processing-options-reporting-services-in-sharepoint-integrated-mode"></a><span data-ttu-id="b55b8-102">처리 옵션 설정(SharePoint 통합 모드의 Reporting Services)</span><span class="sxs-lookup"><span data-stu-id="b55b8-102">Set Processing Options (Reporting Services in SharePoint Integrated Mode)</span></span>
  <span data-ttu-id="b55b8-103">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 보고서 처리 옵션을 설정하여 데이터 처리 시기를 결정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b55b8-103">You can set processing options on a [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] report to determine when data processing occurs.</span></span> <span data-ttu-id="b55b8-104">현재 보고서에 대해 보고서 기록을 사용할지 여부를 결정하는 옵션과 보고서 처리의 제한 시간 값을 설정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b55b8-104">You can also set a time-out value for report processing, and options that determine whether report history is enabled for the current report.</span></span>  
  
-   <span data-ttu-id="b55b8-105">보고서를 보고서 스냅샷으로 실행하면 임의의 시간에(예: 예약된 백업 시간 동안) 보고서가 실행되지 않도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b55b8-105">You can run a report as a report snapshot to prevent the report from being run at arbitrary times (for example, during a scheduled backup).</span></span> <span data-ttu-id="b55b8-106">보고서 스냅샷은 일반적으로 일정에 따라 생성되고 이후에 새로 고쳐지므로 보고서 및 데이터 처리 시간을 정확하게 예약할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b55b8-106">A report snapshot is usually created and subsequently refreshed on a schedule, allowing you to time exactly when report and data processing will occur.</span></span> <span data-ttu-id="b55b8-107">실행하는 데 시간이 오래 걸리는 쿼리 또는 특정 시간 동안 누구도 액세스할 수 없는 데이터 원본의 데이터를 사용하는 쿼리를 기반으로 하는 보고서의 경우 보고서를 스냅샷으로 실행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b55b8-107">If a report is based on queries that take a long time to run, or on queries that use data from a data source that you prefer no one access during certain hours, you should run the report as a snapshot.</span></span>  
  
-   <span data-ttu-id="b55b8-108">보고서 서버는 처리된 보고서의 복사본을 캐시했다가 사용자가 보고서를 열면 해당 복사본을 반환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b55b8-108">A report server can cache a copy of a processed report and return that copy when a user opens the report.</span></span> <span data-ttu-id="b55b8-109">캐싱은 성능을 향상시키는 기술입니다.</span><span class="sxs-lookup"><span data-stu-id="b55b8-109">Caching is a performance-enhancement technique.</span></span> <span data-ttu-id="b55b8-110">캐싱은 보고서가 크거나 자주 액세스되는 경우 보고서를 검색하는 데 필요한 시간을 단축시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b55b8-110">Caching can shorten the time required to retrieve a report if the report is large or accessed frequently.</span></span>  
  
-   <span data-ttu-id="b55b8-111">보고서 기록은 이전에 실행한 보고서 복사본의 모음입니다.</span><span class="sxs-lookup"><span data-stu-id="b55b8-111">Report history is a collection of previously run copies of a report.</span></span> <span data-ttu-id="b55b8-112">보고서 기록을 사용하여 시간에 따른 보고서 기록을 유지 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b55b8-112">You can use report history to maintain a record of a report over time.</span></span> <span data-ttu-id="b55b8-113">보고서 기록은 기밀이나 개인 데이터가 포함된 보고서에 대해서는 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b55b8-113">Report history is not intended for reports that contain confidential or personal data.</span></span> <span data-ttu-id="b55b8-114">따라서 보고서 기록에는 보고서를 실행하는 모든 사용자가 사용할 수 있는 단일 자격 증명 집합(저장된 자격 증명 또는 무인 모드의 보고서 실행에 사용되는 자격 증명)을 사용하여 데이터 원본을 쿼리하는 보고서만 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b55b8-114">For this reason, report history can include only those reports that query a data source using a single set of credentials (either stored credentials or credentials used for unattended report execution) that are available to all users who run a report.</span></span>  
  
    > [!NOTE]  
    >  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] <span data-ttu-id="b55b8-115">통합에서는 SharePoint의 체크 아웃 및 체크인 콘텐츠 관리 기능을 사용하여 업데이트를 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 콘텐츠 형식에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="b55b8-115">integration with SharePoint uses the check out and check in content management features of SharePoint to save updates to [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] content types.</span></span> <span data-ttu-id="b55b8-116">여기에는 보고서 스냅샷 만들기도 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="b55b8-116">This includes the creation of report snapshots.</span></span> <span data-ttu-id="b55b8-117">따라서 문서 라이브러리에 대한 버전 관리를 사용하는 경우 새 보고서 기록 스냅샷이 만들어질 때 보고서 버전이 업데이트되는 것을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b55b8-117">Therefore if you have enabled versioning on a document library, you will see the report version updated when a new report history snapshot is created.</span></span> <span data-ttu-id="b55b8-118">이것은 스냅샷 업데이트로 인해 파생되는 작업입니다.</span><span class="sxs-lookup"><span data-stu-id="b55b8-118">This is a side-effect of updating snapshots.</span></span> <span data-ttu-id="b55b8-119">스냅샷이 업데이트될 때 보고서의 LastExecution 속성이 변경되므로 보고서 버전이 변경되는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="b55b8-119">When a snapshot is updated it causes the LastExecution property of the report to change and that will cause a change in the version of the report.</span></span>  
  
-   <span data-ttu-id="b55b8-120">제한 시간 값을 지정하여 시스템 리소스 사용 방식에 대해 제한을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b55b8-120">You can specify time-out values to set limits on how system resources are used.</span></span>  
  
||  
|-|  
|<span data-ttu-id="b55b8-121">**[!INCLUDE[applies](../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]SharePoint 모드</span><span class="sxs-lookup"><span data-stu-id="b55b8-121">**[!INCLUDE[applies](../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] SharePoint mode</span></span>|  
  
 <span data-ttu-id="b55b8-122">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="b55b8-122">**In this topic:**</span></span>  
  
-   [<span data-ttu-id="b55b8-123">데이터 새로 고침 옵션을 설정하려면</span><span class="sxs-lookup"><span data-stu-id="b55b8-123">To set data refresh options</span></span>](#bkmk_set_data_refresh)  
  
-   [<span data-ttu-id="b55b8-124">보고서 캐시 옵션을 설정하려면</span><span class="sxs-lookup"><span data-stu-id="b55b8-124">To set report caching options</span></span>](#bkmk_set_report_caching)  
  
-   [<span data-ttu-id="b55b8-125">처리 제한 시간 값을 설정하려면</span><span class="sxs-lookup"><span data-stu-id="b55b8-125">To set processing time-out values</span></span>](#bkmk_set_processing)  
  
-   [<span data-ttu-id="b55b8-126">보고서 기록 옵션 및 제한을 설정하려면</span><span class="sxs-lookup"><span data-stu-id="b55b8-126">To set report history options and limits</span></span>](#bkmk_set_report_history)  
  
-   [<span data-ttu-id="b55b8-127">데이터베이스 제한 시간 설정</span><span class="sxs-lookup"><span data-stu-id="b55b8-127">Set database timeout</span></span>](#bkmk_set_database_timeout)  
  
##  <a name="to-set-data-refresh-options"></a><a name="bkmk_set_data_refresh"></a><span data-ttu-id="b55b8-128">데이터 새로 고침 옵션을 설정 하려면</span><span class="sxs-lookup"><span data-stu-id="b55b8-128">To set data refresh options</span></span>  
  
1.  <span data-ttu-id="b55b8-129">라이브러리의 보고서를 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="b55b8-129">Point to a report in the library.</span></span>  
  
2.  <span data-ttu-id="b55b8-130">아래쪽 화살표를 클릭하고 **처리 옵션 관리**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b55b8-130">Click the down arrow, and select **Manage processing options**.</span></span>  
  
3.  <span data-ttu-id="b55b8-131">**데이터 새로 고침 옵션**에서 **스냅샷 데이터 사용**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b55b8-131">In **Data Refresh Options**, click **Use snapshot data**.</span></span> <span data-ttu-id="b55b8-132">"데이터 원본 자격 증명 중 하나 이상이 저장되어 있지 않으므로 스냅샷에서 이 보고서를 실행할 수 없습니다"가 표시되는 경우 보고서가 무인 모드로 실행되도록 구성되어 있지 않으며 이 옵션을 설정하기 전에 저장된 자격 증명을 사용하도록 데이터 원본을 수정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b55b8-132">If you see "This report can not run from a snapshot because one or more of the data sources credentials are not stored", the report is not configured to run unattended and you must modify the data sources to use stored credentials before setting this option.</span></span>  
  
4.  <span data-ttu-id="b55b8-133">**데이터 스냅샷 옵션**에서 **데이터 처리 예약**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b55b8-133">In **Data Snapshot Options**, select **Schedule data processing**.</span></span>  
  
5.  <span data-ttu-id="b55b8-134">사용할 기존 공유 일정이 있는 경우 **공유 일정** 을 선택하고, 없으면 **사용자 지정 일정**을 클릭한 다음 **구성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b55b8-134">Select **On a shared schedule** if you have an existing shared schedule that you want to use, otherwise click **On a custom schedule**, and then click **Configure**.</span></span>  
  
6.  <span data-ttu-id="b55b8-135">빈도, 일정, 시작 날짜 및 종료 날짜를 선택하고 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b55b8-135">Select frequency, schedule, and start and end dates, and then click **OK**.</span></span>  
  
7.  <span data-ttu-id="b55b8-136">예약된 데이터 처리가 수행될 때까지 기다리지 않고 보고서에 사용할 스냅샷 데이터를 즉시 만들려면 **데이터 스냅샷 옵션**에서 **이 페이지를 저장할 때 스냅샷 만들기 또는 업데이트** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b55b8-136">In **Data Snapshot Options**, select **Create or update the snapshot when this page is saved** if you want to immediately create snapshot data to use with the report, without waiting for the scheduled data processing to occur.</span></span>  
  
##  <a name="to-set-report-caching-options"></a><a name="bkmk_set_report_caching"></a><span data-ttu-id="b55b8-137">보고서 캐싱 옵션을 설정 하려면</span><span class="sxs-lookup"><span data-stu-id="b55b8-137">To set report caching options</span></span>  
  
1.  <span data-ttu-id="b55b8-138">라이브러리의 보고서를 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="b55b8-138">Point to a report in the library.</span></span>  
  
2.  <span data-ttu-id="b55b8-139">아래쪽 화살표를 클릭하고 **처리 옵션 관리**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b55b8-139">Click the down arrow, and select **Manage processing options**.</span></span>  
  
3.  <span data-ttu-id="b55b8-140">**데이터 새로 고침 옵션**에서 **캐시된 데이터 사용**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b55b8-140">In **Data Refresh Options**, click **Use cached data**.</span></span> <span data-ttu-id="b55b8-141">"데이터 원본 자격 증명 중 하나 이상이 저장되어 있지 않으므로 이 보고서를 캐시할 수 없습니다"가 표시되는 경우 보고서가 무인 모드로 실행되도록 구성되어 있지 않으며 이 옵션을 설정하기 전에 저장된 자격 증명을 사용하도록 데이터 원본을 수정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b55b8-141">If you see "This report can not be cached because one or more of the data sources credentials are not stored", the report is not configured to run unattended and you must modify the data sources to use stored credentials before setting this option.</span></span>  
  
4.  <span data-ttu-id="b55b8-142">**캐시 옵션**에서 캐시 만료 방식을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b55b8-142">In **Cache Options**, specify how the cache will expire:</span></span>  
  
    -   <span data-ttu-id="b55b8-143">캐시가 만료되기까지의 시간(분)을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="b55b8-143">Enter a number of minutes after which the cache will expire.</span></span>  
  
    -   <span data-ttu-id="b55b8-144">일정에 지정된 시간에 캐시를 지우려면 공유 일정을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="b55b8-144">Use a shared schedule to clear the cache at times specified in the schedule.</span></span>  
  
    -   <span data-ttu-id="b55b8-145">사용자가 지정한 시간에 캐시를 지우려면 사용자 지정 일정을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b55b8-145">Create a custom schedule to clear the cache at a time that you specify.</span></span>  
  
##  <a name="to-set-processing-time-out-values"></a><a name="bkmk_set_processing"></a><span data-ttu-id="b55b8-146">처리 제한 시간 값을 설정 하려면</span><span class="sxs-lookup"><span data-stu-id="b55b8-146">To set processing time-out values</span></span>  
  
1.  <span data-ttu-id="b55b8-147">라이브러리의 보고서를 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="b55b8-147">Point to a report in the library.</span></span>  
  
2.  <span data-ttu-id="b55b8-148">아래쪽 화살표를 클릭하고 **처리 옵션 관리**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b55b8-148">Click the down arrow, and select **Manage processing options**.</span></span>  
  
3.  <span data-ttu-id="b55b8-149">보고서 서버 수준에서 지정된 값을 사용하려면 **처리 제한 시간**에서 **사이트 기본 설정 사용** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b55b8-149">In **Processing Time-out**, select **Use site default setting** if you want to use the value specified at the report server level.</span></span> <span data-ttu-id="b55b8-150">제한 시간 없음이나 다른 제한 시간 값으로 해당 값을 재정의하려면 **보고서 처리 시간 제한 없음** 또는 **보고서 처리 제한 시간(초)** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b55b8-150">Otherwise, select **Do not time out report processing** or **Limit report processing in seconds** if you want to override that value with no time-out or different time-out values.</span></span>  
  
##  <a name="to-set-report-history-options-and-limits"></a><a name="bkmk_set_report_history"></a><span data-ttu-id="b55b8-151">보고서 기록 옵션 및 제한을 설정 하려면</span><span class="sxs-lookup"><span data-stu-id="b55b8-151">To set report history options and limits</span></span>  
  
1.  <span data-ttu-id="b55b8-152">라이브러리의 보고서를 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="b55b8-152">Point to a report in the library.</span></span>  
  
2.  <span data-ttu-id="b55b8-153">아래쪽 화살표를 클릭하고 **처리 옵션 관리**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b55b8-153">Click the down arrow, and select **Manage processing options**.</span></span>  
  
3.  <span data-ttu-id="b55b8-154">**기록 스냅샷 옵션**에서 데이터 처리 및 저장 방법과 시기를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b55b8-154">In **History Snapshot Options**, specify how and when data processing occurs and is saved.</span></span>  
  
4.  <span data-ttu-id="b55b8-155">보고서 서버 수준에서 지정된 값을 사용하려면 **기록 스냅샷 제한**에서 **사이트 기본 설정 사용** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b55b8-155">In **History Snapshot Limits**, select **Use site default setting** if you want to use the value specified at the report server level.</span></span> <span data-ttu-id="b55b8-156">지정된 값을 사용하지 않으려면 **스냅샷 수를 제한하지 않음** 또는 **스냅샷 수 제한** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b55b8-156">Otherwise, select **Do not limit the number of snapshots** or **Limit number of snapshots** to specify a custom value.</span></span>  
  
##  <a name="set-database-timeout"></a><a name="bkmk_set_database_timeout"></a><span data-ttu-id="b55b8-157">데이터베이스 제한 시간 설정</span><span class="sxs-lookup"><span data-stu-id="b55b8-157">Set database timeout</span></span>  
  
1.  <span data-ttu-id="b55b8-158">Windows PowerShell을 사용하여 SharePoint 보고서 서버의 데이터베이스 제한 시간을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="b55b8-158">Use Windows PowerShell to set the database timeout of a SharePoint report server.</span></span> <span data-ttu-id="b55b8-159">자세한 내용은 [PowerShell cmdlets for Reporting Services SharePoint Mode](../../2014/reporting-services/powershell-cmdlets-for-reporting-services-sharepoint-mode.md)의 "보고 서비스 애플리케이션 데이터베이스의 속성 가져오기 및 설정" 섹션을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b55b8-159">For more information, see the "Get and set Properties of the Reporting Service Application Database" section of [PowerShell cmdlets for Reporting Services SharePoint Mode](../../2014/reporting-services/powershell-cmdlets-for-reporting-services-sharepoint-mode.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b55b8-160">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b55b8-160">See Also</span></span>  
 <span data-ttu-id="b55b8-161">[보고서 처리 속성 설정](report-server/set-report-processing-properties.md) </span><span class="sxs-lookup"><span data-stu-id="b55b8-161">[Set Report Processing Properties](report-server/set-report-processing-properties.md) </span></span>  
 <span data-ttu-id="b55b8-162">[보고서 캐시&#40;SSRS&#41;](report-server/caching-reports-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="b55b8-162">[Caching Reports &#40;SSRS&#41;](report-server/caching-reports-ssrs.md) </span></span>  
 [<span data-ttu-id="b55b8-163">보고서 및 공유 데이터 세트 처리에 대한 제한 시간 값 설정&#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="b55b8-163">Setting Time-out Values for Report and Shared Dataset Processing &#40;SSRS&#41;</span></span>](report-server/setting-time-out-values-for-report-and-shared-dataset-processing-ssrs.md)  
  
  
