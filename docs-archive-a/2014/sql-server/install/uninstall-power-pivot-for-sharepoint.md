---
title: SharePoint용 PowerPivot 제거 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
ms.assetid: 3941a2f0-0d0c-4d1a-8618-7a6a7751beac
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 8ca65a04578cbce2ed7eb2831068260d9f0e445a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650432"
---
# <a name="uninstall-powerpivot-for-sharepoint"></a><span data-ttu-id="35102-102">Uninstall PowerPivot for SharePoint</span><span class="sxs-lookup"><span data-stu-id="35102-102">Uninstall PowerPivot for SharePoint</span></span>
  <span data-ttu-id="35102-103">[!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 설치 제거는 제거를 준비하고, 팜에서 기능과 솔루션을 제거하고, 프로그램 파일과 레지스트리 설정을 제거하는 작업으로 구성된 다단계 작업입니다.</span><span class="sxs-lookup"><span data-stu-id="35102-103">Uninstalling a [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] installation is a multi-step operation that includes preparing for uninstall, removing features and solutions from the farm, and removing program files and registry settings.</span></span>  
  
 <span data-ttu-id="35102-104">**[!INCLUDE[applies](../../includes/applies-md.md)]**  SharePoint 2013 | SharePoint 2010</span><span class="sxs-lookup"><span data-stu-id="35102-104">**[!INCLUDE[applies](../../includes/applies-md.md)]**  SharePoint 2013 | SharePoint 2010</span></span>  
  
 <span data-ttu-id="35102-105">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="35102-105">**In this topic:**</span></span>  
  
-   [<span data-ttu-id="35102-106">필수 구성 요소</span><span class="sxs-lookup"><span data-stu-id="35102-106">Prerequisites</span></span>](#prereq)  
  
-   [<span data-ttu-id="35102-107">1단계: 제거 전 검사 목록</span><span class="sxs-lookup"><span data-stu-id="35102-107">Step 1: Pre-Uninstall Checklist</span></span>](#bkmk_before)  
  
-   [<span data-ttu-id="35102-108">2단계: SharePoint에서 기능 및 솔루션 제거</span><span class="sxs-lookup"><span data-stu-id="35102-108">Step 2: Remove Features and Solutions from SharePoint</span></span>](#bkmk_remove)  
  
-   [<span data-ttu-id="35102-109">3단계: SQL Server 설치 프로그램을 실행하여 로컬 컴퓨터에서 프로그램 제거</span><span class="sxs-lookup"><span data-stu-id="35102-109">Step 3: Run SQL Server Setup to Remove Programs from the Local Computer</span></span>](#bkmk_uninstall)  
  
-   [<span data-ttu-id="35102-110">4단계: SharePoint용 PowerPivot 추가 기능 제거</span><span class="sxs-lookup"><span data-stu-id="35102-110">Step 4: Uninstall the PowerPivot for SharePoint add-in</span></span>](#bkmk_addin)  
  
-   [<span data-ttu-id="35102-111">5단계: 제거 확인</span><span class="sxs-lookup"><span data-stu-id="35102-111">Step 5: Verify Uninstall</span></span>](#verify)  
  
-   [<span data-ttu-id="35102-112">6단계: 제거 후 검사 목록</span><span class="sxs-lookup"><span data-stu-id="35102-112">Step 6: Post-Uninstall Checklist</span></span>](#bkmk_post)  
  
##  <a name="prerequisites"></a><a name="prereq"></a> <span data-ttu-id="35102-113">필수 조건</span><span class="sxs-lookup"><span data-stu-id="35102-113">Prerequisites</span></span>  
  
-   <span data-ttu-id="35102-114">팜의 기능과 솔루션을 제거하려면 SharePoint 팜 관리자 또는 서비스 애플리케이션 관리자여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="35102-114">You must be a SharePoint farm administrator or service application administrator to uninstall features and solutions in the farm.</span></span>  
  
-   <span data-ttu-id="35102-115">데이터베이스 엔진도 제거할 경우 SQL Server 시스템 관리자 및 로컬 Administrators 그룹의 구성원이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="35102-115">You must be a SQL Server System Administrator and a member of the local Administrators group if you are also uninstalling the Database Engine.</span></span>  
  
-   <span data-ttu-id="35102-116">Analysis Services 및 [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)]를 제거하려면 Analysis Services 시스템 관리자 및 로컬 Administrators 그룹의 구성원이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="35102-116">You must be an Analysis Services System Administrator and a member of the local Administrators group to uninstall Analysis Services and [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)].</span></span>  
  
##  <a name="step-1-pre-uninstall-checklist"></a><a name="bkmk_before"></a> <span data-ttu-id="35102-117">1단계: 제거 전 검사 목록</span><span class="sxs-lookup"><span data-stu-id="35102-117">Step 1: Pre-Uninstall Checklist</span></span>  
 <span data-ttu-id="35102-118">쿼리 및 데이터 처리를 지원하는 소프트웨어가 팜에서 제거된 경우에는 PowerPivot 데이터에 액세스할 수 없게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="35102-118">PowerPivot data access will be disabled once the software that supports query and data processing is removed from the farm.</span></span> <span data-ttu-id="35102-119">맨 먼저 더 이상 작동되지 않는 파일 및 라이브러리를 삭제해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="35102-119">As a first step, you should preemptively delete files and libraries that will no longer be operational.</span></span> <span data-ttu-id="35102-120">이렇게 하면 소프트웨어를 제거하기 전에 '누락된 데이터'에 대한 질문이나 문제를 해결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="35102-120">This lets you address any questions or concerns about 'missing data' before you uninstall the software.</span></span>  
  
1.  <span data-ttu-id="35102-121">SharePoint용 PowerPivot 설치와 연결된 모든 PowerPivot 통합 문서, 문서 및 라이브러리를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="35102-121">Delete all PowerPivot workbooks, documents, and libraries that are associated with a PowerPivot for SharePoint installation.</span></span> <span data-ttu-id="35102-122">소프트웨어가 제거되면 라이브러리와 문서가 작동하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="35102-122">Neither the libraries nor the documents will function once the software is uninstalled.</span></span>  
  
    -   [<span data-ttu-id="35102-123">PowerPivot 갤러리 삭제</span><span class="sxs-lookup"><span data-stu-id="35102-123">Delete PowerPivot Gallery</span></span>](https://docs.microsoft.com/analysis-services/power-pivot-sharepoint/delete-power-pivot-gallery)  
  
    -   [<span data-ttu-id="35102-124">PowerPivot 데이터 피드 라이브러리 삭제</span><span class="sxs-lookup"><span data-stu-id="35102-124">Delete a PowerPivot Data Feed Library</span></span>](https://docs.microsoft.com/analysis-services/power-pivot-sharepoint/delete-a-power-pivot-data-feed-library)  
  
2.  <span data-ttu-id="35102-125">다른 라이브러리에서 PowerPivot 데이터를 포함하거나 참조하는 Excel 통합 문서 또는 Reporting Services 보고서를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="35102-125">Delete Excel workbooks or Reporting Services reports in other libraries that contain or reference PowerPivot data.</span></span>  
  
3.  <span data-ttu-id="35102-126">PerformancePoint 대시보드에서 PowerPivot 데이터를 참조하는 모든 웹 파트를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="35102-126">Remove any web part in a PerformancePoint dashboard that references PowerPivot data.</span></span>  
  
4.  <span data-ttu-id="35102-127">기존 사이트 및 라이브러리에서 SharePoint 사용 권한을 검토하여 이러한 권한을 변경해야 하는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="35102-127">Review SharePoint permissions on existing sites and libraries to determine whether you need to change them.</span></span> <span data-ttu-id="35102-128">일부 PowerPivot 데이터 액세스 시나리오, 특히 URL 연결 문자열을 통해 다른 통합 문서의 PowerPivot 데이터에 액세스하는 보조 데이터 액세스에는 일반적으로 사이트를 방문하기만 하는 SharePoint 사용자에게 할당되는 보기 권한보다 높은 읽기 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="35102-128">Some PowerPivot data access scenarios, particularly secondary data access via a URL connection string to PowerPivot data in another workbook, require Read permissions, which is higher than the View permissions that are typically assigned to SharePoint users who only visit a site.</span></span> <span data-ttu-id="35102-129">읽기 권한이 더 이상 필요하지 않은 경우에는 사용 권한을 적절히 축소할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="35102-129">If you no longer require Read permissions, you can reduce permissions accordingly.</span></span>  
  
5.  <span data-ttu-id="35102-130">필요한 경우 서비스를 중지하고 소프트웨어를 제거하기 전에 며칠 정도 기다립니다.</span><span class="sxs-lookup"><span data-stu-id="35102-130">Optionally, stop the services and wait several days before uninstalling the software.</span></span> <span data-ttu-id="35102-131">이 단계는 제거에 반드시 필요한 것은 아니지만 데이터 마이그레이션 또는 기술 대체 문제가 발생한 경우 서비스를 일시적으로 재개할 수 있는 기회를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="35102-131">This step is not necessary for uninstall, but it gives you the option of temporarily resuming the service while you work out any data migration or technology substitution issues that you might have missed.</span></span>  
  
##  <a name="step-2-remove-features-and-solutions-from-sharepoint"></a><a name="bkmk_remove"></a> <span data-ttu-id="35102-132">2단계: SharePoint에서 기능 및 솔루션 제거</span><span class="sxs-lookup"><span data-stu-id="35102-132">Step 2: Remove Features and Solutions from SharePoint</span></span>  
 <span data-ttu-id="35102-133">PowerPivot 구성 도구를 사용하여 SharePoint에서 PowerPivot 서비스 및 애플리케이션을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="35102-133">Use the PowerPivot Configuration Tool to remove PowerPivot services and applications from SharePoint.</span></span>  
  
-   <span data-ttu-id="35102-134">팜 관리자, Analysis Services 인스턴스의 서버 관리자 및 팜의 구성 데이터베이스의 **db_owner**여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="35102-134">You must be a farm administrator, a server administrator on the Analysis Services instance, and **db_owner** on the farm's configuration database.</span></span>  
  
-   <span data-ttu-id="35102-135">SharePoint 버전에 대한 구성 도구의 해당 버전을 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="35102-135">Use the appropriate version of the configuration tool for the version of SharePoint.</span></span> <span data-ttu-id="35102-136">[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] 설치에는 이러한 도구를 사용하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="35102-136">Do not use either tool with [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] installations.</span></span>  
  
-   <span data-ttu-id="35102-137">SharePoint 관리 서비스가 실행되고 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="35102-137">Verify that the SharePoint Administration service is running.</span></span>  
  
1.  <span data-ttu-id="35102-138">**구성 도구 실행:** 구성 도구는 [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 가 로컬 서버에 설치되어 있을 때만 나열됩니다. **시작** 메뉴에서 **모든 프로그램**을 가리키고 [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)]를 클릭하고 **구성 도구**를 클릭한 후 다음 중 하나를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="35102-138">**Run the Configuration tool:** Note the configuration tools are only listed only when [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] is installed on the local server.On the **Start** menu, point to **All Programs**, click [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)], click **Configuration Tools**, and then click one of the following:</span></span>  
  
    -   <span data-ttu-id="35102-139">**SharePoint용 PowerPivot 2013 구성**</span><span class="sxs-lookup"><span data-stu-id="35102-139">**PowerPivot for SharePoint 2013 Configuration**</span></span>  
  
    -   <span data-ttu-id="35102-140">**PowerPivot 구성 도구**</span><span class="sxs-lookup"><span data-stu-id="35102-140">**PowerPivot Configuration Tool**</span></span>  
  
2.  <span data-ttu-id="35102-141">**기능, 서비스, 애플리케이션 및 솔루션 제거** 를 선택한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="35102-141">Select **Remove Features, Services, Applications, and Solutions** and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="35102-142">필요한 경우 창을 전체 크기로 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="35102-142">Optionally, expand the window to full size.</span></span> <span data-ttu-id="35102-143">창 아래쪽에 **유효성 검사**, **실행**및 **끝내기** 명령이 포함된 단추 모음이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="35102-143">You should see a button bar at the bottom of the window that includes **Validate**, **Run**, and **Exit** commands.</span></span>  
  
4.  <span data-ttu-id="35102-144">태스크 목록의 각 동작을 검토하여 각 동작이 수행하는 작업을 이해합니다.</span><span class="sxs-lookup"><span data-stu-id="35102-144">Review each action in the task list to understand what each one does.</span></span>  
  
     <span data-ttu-id="35102-145">**PowerPivot 서비스 애플리케이션 제거**에는 서비스 애플리케이션과 관련된 애플리케이션 데이터를 삭제할 수 있는 옵션이 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="35102-145">In **Remove PowerPivot Service Applications**, you are given the option of deleting application data associated with the service application.</span></span> <span data-ttu-id="35102-146">애플리케이션 데이터는 SharePoint용 PowerPivot에서 사용되는 데이터 새로 고침 일정, 데이터베이스 인스턴스 정보, 사용량 현황 데이터 및 기타 데이터를 저장하기 위해 서비스 애플리케이션에서 만드는 SQL Server 데이터베이스입니다.</span><span class="sxs-lookup"><span data-stu-id="35102-146">The application data is a SQL Server database that was created with the service application for the purpose of storing data refresh schedules, database instance information, usage data, and other data used by PowerPivot for SharePoint.</span></span> <span data-ttu-id="35102-147">PowerPivot 통합 문서와 같은 사용자 파일은 저장되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="35102-147">It does not store user files, such as PowerPivot workbooks.</span></span> <span data-ttu-id="35102-148">애플리케이션 데이터를 보관할 특정 이유가 있는 경우(예: 데이터 새로 고침 또는 데이터 액세스와 관련된 데이터 보존 정책이 있는 경우)가 아니면 SharePoint 사용자가 만들거나 저장한 파일을 제거하지 않고 애플리케이션 데이터베이스를 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="35102-148">Unless you have a specific reason to keep the application data (for example, if you have data retention policies related to data refresh or data access) you can delete the application database without removing any files that were created or saved by SharePoint users.</span></span>  
  
     <span data-ttu-id="35102-149">데이터베이스를 삭제하려면 **PowerPivot 서비스 애플리케이션 제거** 를 선택한 다음 **이 서비스 애플리케이션에 연결된 애플리케이션 데이터를 삭제합니다.** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="35102-149">To delete the database, select **Remove PowerPivot Service Applications** and then select the **Delete application data associated with this service application**.</span></span>  
  
5.  <span data-ttu-id="35102-150">필요한 경우 **출력** 탭 또는 **스크립트** 탭에서 자세한 정보를 검토합니다.</span><span class="sxs-lookup"><span data-stu-id="35102-150">Optionally, review detailed information in the **Output** tab or **Script** tab.</span></span>  
  
     <span data-ttu-id="35102-151">출력 탭은 도구에서 수행되는 동작의 요약입니다.</span><span class="sxs-lookup"><span data-stu-id="35102-151">The Output tab is a summary of the actions that will be performed by the tool.</span></span> <span data-ttu-id="35102-152">이 정보는 다음 위치의 로그 파일에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="35102-152">This information is saved in log files at:</span></span>  
  
     `C:\Program Files\Microsoft SQL Server\120\Tools\PowerPivotTools\SPAddinConfiguration\Log`  
  
     <span data-ttu-id="35102-153">스크립트 탭은 PowerShell cmdlet을 표시하거나 도구에서 실행할 PowerShell 스크립트 파일을 참조합니다.</span><span class="sxs-lookup"><span data-stu-id="35102-153">The Script tab shows the PowerShell cmdlets or references the PowerShell script files that the tool will run.</span></span>  
  
6.  <span data-ttu-id="35102-154">**유효성 검사** 를 클릭하여 각 동작이 유효한지 여부를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="35102-154">Click **Validate** to check whether each action is valid.</span></span> <span data-ttu-id="35102-155">**유효성 검사** 를 사용할 수 없는 경우 모든 동작이 시스템에 유효한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="35102-155">If **Validate** is not available, it means that all of the actions are valid for your system.</span></span>  
  
7.  <span data-ttu-id="35102-156">**실행** 을 클릭하여 이 태스크에 유효한 모든 동작을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="35102-156">Click **Run** to perform all of the actions that are valid for this task.</span></span> <span data-ttu-id="35102-157">**실행** 은 유효성 검사를 통과한 후에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="35102-157">**Run** is available only after the validation check is passed.</span></span> <span data-ttu-id="35102-158">**실행**을 클릭하면 동작이 일괄 처리 모드로 처리됨을 알리는 다음 경고가 나타납니다. “도구에서 유효한 것으로 플래그가 지정되는 모든 구성 설정이 SharePoint 팜에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="35102-158">When you click **Run**, the following warning appears, reminding you that actions are processed in batch mode: "All of the configuration settings that are flagged as valid in the tool will be applied to the SharePoint farm.</span></span> <span data-ttu-id="35102-159">계속하시겠습니까?”</span><span class="sxs-lookup"><span data-stu-id="35102-159">Do you want to continue?"</span></span>  
  
8.  <span data-ttu-id="35102-160">계속하려면 **예** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="35102-160">Click **Yes** to continue.</span></span>  
  
 <span data-ttu-id="35102-161">**오류 문제 해결:**</span><span class="sxs-lookup"><span data-stu-id="35102-161">**Troubleshooting errors:**</span></span>  
  
 <span data-ttu-id="35102-162">구성 도구의 각 동작에 대한 매개 변수 창에서 오류 정보를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="35102-162">In the Configuration Tool, you can view error information in the Parameters pane for each action.</span></span> <span data-ttu-id="35102-163">솔루션 배포 또는 취소와 관련된 문제의 경우 SharePoint 관리 서비스가 시작되었는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="35102-163">For problems related to solution deployment or retraction, verify the SharePoint Administration service is started.</span></span> <span data-ttu-id="35102-164">이 서비스는 팜에서 구성 변경 내용을 트리거하는 타이머 작업을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="35102-164">This service runs the timer jobs that trigger configuration changes in a farm.</span></span> <span data-ttu-id="35102-165">서비스가 실행되고 있지 않은 경우 솔루션 배포 또는 취소가 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="35102-165">If the service is not running, solution deployment or retraction will fail.</span></span> <span data-ttu-id="35102-166">오류가 지속되면 기존 배포 또는 취소 작업이 큐에 이미 있으며 구성 도구의 추가 동작을 차단하고 있는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="35102-166">Persistent errors indicate that an existing deployment or retraction job is already in the queue and blocking further action from the configuration tool.</span></span> <span data-ttu-id="35102-167">다음 PowerShell 명령을 사용하여 서비스가 실행되고 있는지 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="35102-167">You can use the following PowerShell command to verify the service is running.</span></span>  
  
```powershell
Get-Service | Where {$_.displayname -like "*sharepoint* administration*"}  
```  
  
 <span data-ttu-id="35102-168">큐에 이미 있는 배포 또는 취소 작업을 찾아서 제거하려면 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="35102-168">To find and remove a deployment or retraction job that is already in the queue, do the following:</span></span>  
  
1.  <span data-ttu-id="35102-169">다른 모든 오류에 대해서는 ULS 로그를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="35102-169">For all other errors, check the ULS logs.</span></span> <span data-ttu-id="35102-170">자세한 내용은 [SharePoint 로그 파일 구성 및 보기&#41;SharePoint용 PowerPivot &#40;진단 로깅 ](https://docs.microsoft.com/analysis-services/power-pivot-sharepoint/configure-and-view-sharepoint-and-diagnostic-logging)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="35102-170">For more information, see [Configure and View SharePoint Log Files  and Diagnostic Logging &#40;PowerPivot for SharePoint&#41;](https://docs.microsoft.com/analysis-services/power-pivot-sharepoint/configure-and-view-sharepoint-and-diagnostic-logging).</span></span>  
  
2.  <span data-ttu-id="35102-171">SharePoint 관리 셸을 관리자 권한으로 시작하고 다음 명령을 실행하여 큐에 있는 작업을 봅니다.</span><span class="sxs-lookup"><span data-stu-id="35102-171">Start the SharePoint Management Shell as an administrator and then run the following command to view jobs in the queue:</span></span>  
  
    ```cmd
    stsadm -o enumdeployments  
    ```  
  
3.  <span data-ttu-id="35102-172">기존 배포에서 **유형** 이 취소 또는 배포인지, **파일** 이 powerpivotwebapp.wsp 또는 powerpivotfarm.wsp인지 검토합니다.</span><span class="sxs-lookup"><span data-stu-id="35102-172">Review existing deployments for the following information: **Type** is Retraction or Deployment, **File** is powerpivotwebapp.wsp or powerpivotfarm.wsp.</span></span>  
  
4.  <span data-ttu-id="35102-173">PowerPivot 솔루션과 관련 된 배포 또는 취소의 경우 **JobId** 의 guid 값을 복사 하 여 다음 명령에 붙여 넣습니다 (셸의 편집 메뉴에서 표시, 복사 및 붙여넣기 명령을 사용 하 여 guid 복사).</span><span class="sxs-lookup"><span data-stu-id="35102-173">For deployments or retractions related to PowerPivot solutions, copy the GUID value for **JobId** and then paste it into the following command (use the Mark, Copy, and Paste commands on the Shell's Edit menu to copy the GUID):</span></span>  
  
    ```cmd
    stsadm -o canceldeployment -id "<GUID>"  
    ```  
  
5.  <span data-ttu-id="35102-174">**유효성 검사** 를 클릭한 다음 **실행**을 클릭하여 구성 도구에서 태스크를 다시 시도합니다.</span><span class="sxs-lookup"><span data-stu-id="35102-174">Retry the task in the configuration tool by clicking **Validate** followed by **Run**.</span></span>  
  
 <span data-ttu-id="35102-175">PowerShell을 사용하여 팜에서 기능과 솔루션을 제거할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="35102-175">Alternatively, you can use PowerShell to remove features and solutions from the farm.</span></span> <span data-ttu-id="35102-176">자세한 내용은 [SharePoint용 PowerPivot에 대 한 PowerShell 참조](/sql/analysis-services/powershell/powershell-reference-for-power-pivot-for-sharepoint)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="35102-176">For more information, see [PowerShell Reference for PowerPivot for SharePoint](/sql/analysis-services/powershell/powershell-reference-for-power-pivot-for-sharepoint).</span></span>  
  
##  <a name="step-3-run-sql-server-setup-to-remove-programs-from-the-local-computer"></a><a name="bkmk_uninstall"></a> <span data-ttu-id="35102-177">3단계: SQL Server 설치 프로그램을 실행하여 로컬 컴퓨터에서 프로그램 제거</span><span class="sxs-lookup"><span data-stu-id="35102-177">Step 3: Run SQL Server Setup to Remove Programs from the Local Computer</span></span>  
 <span data-ttu-id="35102-178">프로그램 파일을 삭제하려면 소프트웨어를 제거하기 위해 SQL Server 설치 프로그램을 실행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="35102-178">Deleting program files requires that you run SQL Server Setup to uninstall the software.</span></span> <span data-ttu-id="35102-179">제거하면 설치 프로그램에서 생성된 파일과 레지스트리 항목이 모두 제거됩니다.</span><span class="sxs-lookup"><span data-stu-id="35102-179">Uninstall removes both files and the registry entries that were created by Setup.</span></span> <span data-ttu-id="35102-180">프로그램 및 기능 페이지를 사용하여 소프트웨어를 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="35102-180">You can use the Programs and Features page to uninstall the software.</span></span> <span data-ttu-id="35102-181">[!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 은 SQL Server를 설치할 때 함께 설치됩니다.</span><span class="sxs-lookup"><span data-stu-id="35102-181">An installation of [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] is part of a SQL Server installation.</span></span>  
  
 <span data-ttu-id="35102-182">이미 설치된 다른 SQL Server 인스턴스(또는 동일한 인스턴스의 기능)에 영향을 주지 않고 설치 일부를 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="35102-182">You can uninstall part of an installation without impacting other SQL Server instances (or features in the same instance) that are already installed.</span></span> <span data-ttu-id="35102-183">예를 들어 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , 데이터베이스 엔진 등의 다른 인스턴스는 설치된 상태로 두고 SharePoint용 PowerPivot을 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="35102-183">For example, you can uninstall PowerPivot for SharePoint while leaving other components, such as [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] or the Database Engine, installed.</span></span>  
  
1.  <span data-ttu-id="35102-184">프로그램 목록에서 **Microsoft SQL Server 2014(64비트)** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="35102-184">Select **Microsoft SQL Server 2014 (64-bit)** from the program list.</span></span>  
  
2.  <span data-ttu-id="35102-185">**제거/변경**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="35102-185">Click **Uninstall/Change**.</span></span>  
  
3.  <span data-ttu-id="35102-186">**제거**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="35102-186">Click **Remove**.</span></span> <span data-ttu-id="35102-187">SQL Server 설치 프로그램이 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="35102-187">This starts SQL Server Setup.</span></span>  
  
     <span data-ttu-id="35102-188">설치 프로그램에서 **PowerPivot** 인스턴스를 선택한 다음 **Analysis Services** 및 **Analysis Services SharePoint 통합** 을 선택하여 해당 기능만 제거하고 나머지 모든 기능을 그대로 둘 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="35102-188">From Setup, you can select the **PowerPivot** instance, and then select **Analysis Services** and **Analysis Services SharePoint Integration** to remove just that feature, leaving everything else in place.</span></span>  
  
##  <a name="step-4-uninstall-the-powerpivot-for-sharepoint-add-in"></a><a name="bkmk_addin"></a><span data-ttu-id="35102-189">4 단계: SharePoint용 PowerPivot 추가 기능 제거</span><span class="sxs-lookup"><span data-stu-id="35102-189">Step 4: Uninstall the PowerPivot for SharePoint add-in</span></span>  
 <span data-ttu-id="35102-190">[!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 배포에 두 개 이상의 서버가 포함되었고 [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 추가 기능이 설치된 경우 모든 [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 파일을 완전히 제거하려면 [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 추가 기능이 설치된 각 서버에서 이 추가 기능을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="35102-190">If your [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] deployment has two or more servers and you installed the [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] Add-in, then uninstall the [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] add-in from each server where it was installed to completely uninstall all [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] files.</span></span> <span data-ttu-id="35102-191">자세한 내용은 [SharePoint 2013&#41;&#40;SharePoint용 PowerPivot 추가 기능 설치 또는 제거 ](https://docs.microsoft.com/analysis-services/instances/install-windows/install-or-uninstall-the-power-pivot-for-sharepoint-add-in-sharepoint-2013)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="35102-191">For more information, see [Install or Uninstall the PowerPivot for SharePoint Add-in &#40;SharePoint 2013&#41;](https://docs.microsoft.com/analysis-services/instances/install-windows/install-or-uninstall-the-power-pivot-for-sharepoint-add-in-sharepoint-2013).</span></span>  
  
##  <a name="step-5-verify-uninstall"></a><a name="verify"></a> <span data-ttu-id="35102-192">5단계: 제거 확인</span><span class="sxs-lookup"><span data-stu-id="35102-192">Step 5: Verify Uninstall</span></span>  
  
1.  <span data-ttu-id="35102-193">중앙 관리의 **서버의 서비스 관리**에서 SharePoint용 PowerPivot을 제거한 서버에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="35102-193">In Central Administration, in **Manage services on server**, connect to the server from which you uninstalled PowerPivot for SharePoint.</span></span>  
  
2.  -   <span data-ttu-id="35102-194">[!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 2013을 제거한 경우 **SQL Server PowerPivot 시스템 서비스** 가 더 이상 목록에 표시되지 않는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="35102-194">If you uninstalled [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 2013, verify that **SQL Server PowerPivot System Service** no longer appear in the list.</span></span>  
  
    -   <span data-ttu-id="35102-195">[!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 2010을 제거한 경우, **SQL Server Analysis Services** 및 **SQL Server PowerPivot 시스템 서비스** 가 목록에 더 이상 표시되지 않는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="35102-195">If you uninstalled [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 2010, verify that **SQL Server Analysis Services** and **SQL Server PowerPivot System Service** no longer appear in the list.</span></span>  
  
3.  <span data-ttu-id="35102-196">팜에서 마지막 SharePoint용 PowerPivot 서버를 제거한 후 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="35102-196">After you uninstall the last PowerPivot for SharePoint server in the farm, do the following:</span></span>  
  
    1.  <span data-ttu-id="35102-197">애플리케이션 관리의 **서비스 애플리케이션 관리**에서 PowerPivot 서비스 애플리케이션이 목록에 더 이상 표시되지 않는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="35102-197">In Application Management, in **Manage service applications**, verify that PowerPivot Service Application no longer appears in the list.</span></span>  
  
    2.  <span data-ttu-id="35102-198">시스템 설정의 **팜 기능 관리**에서 PowerPivot 통합 기능이 페이지에 더 이상 없는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="35102-198">In System Settings, in **Manage farm features**, verify that PowerPivot Integration Feature is no longer on the page.</span></span> <span data-ttu-id="35102-199">**팜 솔루션 관리**에서 PowerPivot 솔루션이 페이지에 더 이상 표시되지 않는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="35102-199">In **Manage farm solutions**, verify that the PowerPivot solutions no longer appear on the page.</span></span>  
  
    3.  <span data-ttu-id="35102-200">모니터링의 **진단 로깅 구성** 및 **사용 현황 및 상태 데이터 수집 구성**에서 PowerPivot 이벤트 및 이벤트 범주가 더 이상 표시되지 않는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="35102-200">In Monitoring, in **Configure diagnostic logging** and in **Configure usage and health data collection**, verify that PowerPivot events and event categories no longer appear.</span></span>  
  
    4.  <span data-ttu-id="35102-201">일반 애플리케이션 설정에서 **PowerPivot 관리 대시보드** 가 페이지에 더 이상 없는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="35102-201">In General Application Settings, verify that **PowerPivot Management Dashboard** is no longer on the page.</span></span>  
  
##  <a name="step-6-post-uninstall-checklist"></a><a name="bkmk_post"></a> <span data-ttu-id="35102-202">6단계: 제거 후 검사 목록</span><span class="sxs-lookup"><span data-stu-id="35102-202">Step 6: Post-Uninstall Checklist</span></span>  
 <span data-ttu-id="35102-203">다음 목록을 사용하여 제거 중에 삭제되지 않은 소프트웨어 및 파일을 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="35102-203">Use the following list to remove software and files that were not deleted during uninstall.</span></span>  
  
1.  <span data-ttu-id="35102-204">`C:\Program Files\Microsoft SQL Server\MSAS12.PowerPivot`에서 모든 데이터 파일과 하위 폴더를 삭제한 다음 폴더를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="35102-204">Delete all data files and subfolders from `C:\Program Files\Microsoft SQL Server\MSAS12.PowerPivot`, and then delete the folder.</span></span> <span data-ttu-id="35102-205">이 단계는 DATA 디렉터리에서 이전에 캐시된 파일도 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="35102-205">This step also deletes previously cached files in the DATA directory.</span></span>  
  
2.  <span data-ttu-id="35102-206">모든 PowerPivot 통합 문서, 문서 및 라이브러리를 삭제합니다(아직 삭제하지 않은 경우).</span><span class="sxs-lookup"><span data-stu-id="35102-206">Delete all PowerPivot workbooks, documents, and libraries if you have not already done so.</span></span>  
  
    -   [<span data-ttu-id="35102-207">PowerPivot 갤러리 삭제</span><span class="sxs-lookup"><span data-stu-id="35102-207">Delete PowerPivot Gallery</span></span>](https://docs.microsoft.com/analysis-services/power-pivot-sharepoint/delete-power-pivot-gallery)  
  
    -   [<span data-ttu-id="35102-208">PowerPivot 데이터 피드 라이브러리 삭제</span><span class="sxs-lookup"><span data-stu-id="35102-208">Delete a PowerPivot Data Feed Library</span></span>](https://docs.microsoft.com/analysis-services/power-pivot-sharepoint/delete-a-power-pivot-data-feed-library)  
  
3.  <span data-ttu-id="35102-209">보안 저장소 서비스에서 SharePoint용 PowerPivot에 사용되는 저장된 자격 증명이 있는 모든 대상 애플리케이션을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="35102-209">In Secure Store Service, delete any target applications that contain stored credentials used by PowerPivot for SharePoint.</span></span> <span data-ttu-id="35102-210">보안 저장소 서비스의 일부 항목은 SharePoint용 PowerPivot을 제거할 때 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="35102-210">Some, but not all, entries in Secure Store Service are deleted when you uninstall PowerPivot for SharePoint.</span></span> <span data-ttu-id="35102-211">PowerPivot 무인 데이터 새로 고침 계정에 대해 만든 대상 애플리케이션 및 데이터 새로 고침을 위해 만든 모든 대상 애플리케이션은 아직 삭제되지 않으므로 수동으로 삭제해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="35102-211">Target applications created for the PowerPivot unattended data refresh account plus any target applications you created for data refresh still exist and must be deleted manually.</span></span>  
  
     <span data-ttu-id="35102-212">반면, PowerPivot 시스템 서비스에 의해 자동 생성된 개별 대상 애플리케이션은 PowerPivot을 제거할 때 자동으로 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="35102-212">In contrast, individual target applications that were auto-generated by the PowerPivot System Service are deleted automatically when PowerPivot is uninstalled.</span></span>  
  
4.  <span data-ttu-id="35102-213">제어판에서 **프로그램**, **프로그램 제거**</span><span class="sxs-lookup"><span data-stu-id="35102-213">In Control Panel, click **Programs**, and then click **Uninstall a program.**</span></span> <span data-ttu-id="35102-214">를 차례로 클릭합니다. 더 이상 사용되지 않는 모든 Analysis Services 클라이언트 라이브러리를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="35102-214">Uninstall any Analysis Services client libraries that are no longer used.</span></span> <span data-ttu-id="35102-215">Analysis Services ADOMD.NET 및 Microsoft SQL Server Analysis Management Objects는 SharePoint용 PowerPivot을 제거할 때 제거되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="35102-215">Analysis Services ADOMD.NET and Microsoft SQL Server Analysis Management Objects are not removed when you uninstall PowerPivot for SharePoint.</span></span> <span data-ttu-id="35102-216">이러한 라이브러리는 Analysis Services 데이터를 사용하는 다른 프로그램에서 사용할 수 있으므로 SQL Server 설치 프로그램이 자동으로 제거하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="35102-216">Because the libraries might be used by other programs that use Analysis Services data, SQL Server Setup does not uninstall them automatically.</span></span> <span data-ttu-id="35102-217">더 이상 필요하지 않은 경우 클라이언트 라이브러리를 개별적으로 제거해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="35102-217">You must uninstall these client libraries individually if you no longer need them.</span></span>  
  
     <span data-ttu-id="35102-218">SQL Server Reporting Services SharePoint 2010 추가 기능은 제거와 관련하여 특별히 안내된 다음 문제 해결 또는 설치 지침에 따라서만 제거해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="35102-218">Do not uninstall the SQL Server Reporting Services SharePoint 2010 Add-in unless you are following troubleshooting or installation instructions that specifically direct you to uninstall it.</span></span> <span data-ttu-id="35102-219">Reporting Services 추가 기능은 Access 서비스에서 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="35102-219">The Reporting Services Add-in is used by Access Services.</span></span> <span data-ttu-id="35102-220">또한 SharePoint 2010 제품 준비 도구에 의해 설치되므로 SharePoint에 필요한 기능을 지원하려면 시스템에 그대로 유지되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="35102-220">It is installed by the SharePoint Products Preparation tool and should remain on the system to support functionality required by SharePoint.</span></span>  
  
     <span data-ttu-id="35102-221">Analysis Services OLE DB 공급자를 제거하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="35102-221">Do not uninstall the Analysis Services OLE DB provider.</span></span> <span data-ttu-id="35102-222">SharePoint는 OLE DB 공급자를 Analysis Services 데이터베이스에 연결하는 Excel 통합 문서의 필수 구성 요소로 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="35102-222">SharePoint installs the OLE DB provider as a prerequisite for Excel workbooks that connect to Analysis Services databases.</span></span> [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] <span data-ttu-id="35102-223">에서 최신 버전을 설치하지만 이 버전은 이전 버전과 호환되므로 나중에 데이터 연결 문제를 피하려면 OLE DB 공급자를 시스템에 그대로 두어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="35102-223">installs a newer version, but this version is backwards compatible so you should leave it on the system to avoid data connection problems later.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35102-224">참고 항목</span><span class="sxs-lookup"><span data-stu-id="35102-224">See Also</span></span>  
 <span data-ttu-id="35102-225">[SharePoint 2013 &#40;SharePoint용 PowerPivot 추가 기능 설치 또는 제거&#41;](https://docs.microsoft.com/analysis-services/instances/install-windows/install-or-uninstall-the-power-pivot-for-sharepoint-add-in-sharepoint-2013) </span><span class="sxs-lookup"><span data-stu-id="35102-225">[Install or Uninstall the PowerPivot for SharePoint Add-in &#40;SharePoint 2013&#41;](https://docs.microsoft.com/analysis-services/instances/install-windows/install-or-uninstall-the-power-pivot-for-sharepoint-add-in-sharepoint-2013) </span></span>  
 [<span data-ttu-id="35102-226">PowerPivot Configuration Tools</span><span class="sxs-lookup"><span data-stu-id="35102-226">PowerPivot Configuration Tools</span></span>](https://docs.microsoft.com/analysis-services/power-pivot-sharepoint/power-pivot-configuration-tools)  
