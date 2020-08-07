---
title: 보고서 서버 간에 콘텐츠를 마이그레이션하는 샘플 Reporting Services rs.exe 스크립트 | Microsoft Docs
ms.custom: ''
ms.date: 07/27/2015
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: d81bb03a-a89e-4fc1-a62b-886fb5338150
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 9dece153485e4c683df42a04b9301cf3a47c869c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731396"
---
# <a name="sample-reporting-services-rsexe-script-to-migrate-content-between-report-servers"></a><span data-ttu-id="10961-102">보고서 서버 간 콘텐츠 마이그레이션을 위한 예제 Reporting Services rs.exe</span><span class="sxs-lookup"><span data-stu-id="10961-102">Sample Reporting Services rs.exe Script to Migrate Content between Report Servers</span></span>
  <span data-ttu-id="10961-103">이 항목에는 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] RS.exe [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] report server to another report server, using the **RS.exe** utility.</span><span class="sxs-lookup"><span data-stu-id="10961-103">This topic includes and describes a sample [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] RSS script that copies content items and settings from one [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] report server to another report server, using the **RS.exe** utility.</span></span> <span data-ttu-id="10961-104">RS.exe는 기본 및 SharePoint 모드에서 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]와 함께 설치됩니다.</span><span class="sxs-lookup"><span data-stu-id="10961-104">RS.exe is installed with [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)], both native and SharePoint mode.</span></span> <span data-ttu-id="10961-105">이 스크립트는 보고서 및 구독과 같은 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 항목을 한 서버에서 다른 서버로 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="10961-105">The script copies [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] items, for example reports and subscriptions, from server to another server.</span></span> <span data-ttu-id="10961-106">스크립트에서는 SharePoint 모드 및 기본 모드 보고서 서버가 모두 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="10961-106">The script supports both SharePoint mode and Native mode report servers.</span></span>  
  
||  
|-|  
|<span data-ttu-id="10961-107">**[!INCLUDE[applies](../../includes/applies-md.md)]** [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] SharePoint 모드 &#124; [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 기본 모드</span><span class="sxs-lookup"><span data-stu-id="10961-107">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] SharePoint mode &#124; [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] Native mode</span></span>|  
  
##  <a name="in-this-topic"></a><a name="bkmk_top"></a><span data-ttu-id="10961-108">항목 내용</span><span class="sxs-lookup"><span data-stu-id="10961-108">In this Topic:</span></span>  
  
-   [<span data-ttu-id="10961-109">ssrs_migration.rss 스크립트를 다운로드하려면</span><span class="sxs-lookup"><span data-stu-id="10961-109">To Download the ssrs_migration.rss Script</span></span>](#bkmk_download_script)  
  
-   [<span data-ttu-id="10961-110">지원 되는 시나리오</span><span class="sxs-lookup"><span data-stu-id="10961-110">Supported Scenarios</span></span>](#bkmk_supported_scenarios)  
  
-   [<span data-ttu-id="10961-111">스크립트가 마이그레이션하는 항목 및 리소스</span><span class="sxs-lookup"><span data-stu-id="10961-111">Items and resources the script migrates</span></span>](#bkmk_what_is_migrated)  
  
-   [<span data-ttu-id="10961-112">필요한 권한</span><span class="sxs-lookup"><span data-stu-id="10961-112">Required Permissions</span></span>](#bkmk_required_permissions)  
  
-   [<span data-ttu-id="10961-113">스크립트를 사용하는 방법</span><span class="sxs-lookup"><span data-stu-id="10961-113">How to use the script</span></span>](#bkmk_how_to_use_the_script)  
  
-   [<span data-ttu-id="10961-114">매개 변수 설명</span><span class="sxs-lookup"><span data-stu-id="10961-114">Parameter Description</span></span>](#bkmk_parameter_description)  
  
-   [<span data-ttu-id="10961-115">추가 예제</span><span class="sxs-lookup"><span data-stu-id="10961-115">More Examples</span></span>](#bkmk_more_examples)  
  
    -   [<span data-ttu-id="10961-116">기본 모드 보고서 서버에서 기본 모드 보고서 서버로</span><span class="sxs-lookup"><span data-stu-id="10961-116">Native Mode Report Server to Native Mode Report Server</span></span>](#bkmk_native_2_native)  
  
    -   [<span data-ttu-id="10961-117">기본 모드에서 SharePoint 모드로-루트 사이트</span><span class="sxs-lookup"><span data-stu-id="10961-117">Native Mode to SharePoint Mode - root site</span></span>](#bkmk_native_2_sharepoint_root)  
  
    -   [<span data-ttu-id="10961-118">기본 모드에서 SharePoint 모드로-' bi ' 사이트 모음</span><span class="sxs-lookup"><span data-stu-id="10961-118">Native mode to SharePoint Mode -'bi' site collection</span></span>](#bkmk_native_2_sharepoint_with_site)  
  
    -   [<span data-ttu-id="10961-119">SharePoint 모드에서 SharePoint 모드로-' bi ' 사이트 모음</span><span class="sxs-lookup"><span data-stu-id="10961-119">SharePoint Mode to SharePoint Mode -'bi' site collection</span></span>](#bkmk_sharepoint_2_sharepoint)  
  
    -   [<span data-ttu-id="10961-120">기본 모드에서 기본 모드로-Azure 가상 컴퓨터</span><span class="sxs-lookup"><span data-stu-id="10961-120">Native Mode to Native Mode - Azure Virtual Machine</span></span>](#bkmk_native_to_native_Azure_vm)  
  
    -   [<span data-ttu-id="10961-121">SharePoint 모드-Azure 가상 컴퓨터의 기본 모드 서버에 대 한 ' bi ' 사이트 모음</span><span class="sxs-lookup"><span data-stu-id="10961-121">SharePoint Mode -'bi' site collection to a Native Mode Server on Azure Virtual Machine</span></span>](#bkmk_sharepoint_site_to_native_Azure_vm)  
  
-   [<span data-ttu-id="10961-122">확인</span><span class="sxs-lookup"><span data-stu-id="10961-122">Verification</span></span>](#bkmk_verification)  
  
-   [<span data-ttu-id="10961-123">문제 해결</span><span class="sxs-lookup"><span data-stu-id="10961-123">Troubleshooting</span></span>](#bkmk_troubleshoot)  
  
##  <a name="to-download-the-ssrs_migrationrss-script"></a><a name="bkmk_download_script"></a><span data-ttu-id="10961-124">Ssrs_migration rss 스크립트를 다운로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="10961-124">To Download the ssrs_migration.rss Script</span></span>  
 <span data-ttu-id="10961-125">스크립트를 CodePlex 사이트 [Reporting Services RS.exe 스크립트 마이그레이션 콘텐츠](https://azuresql.codeplex.com/releases/view/115207) 에서 로컬 폴더로 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="10961-125">Download the script from the CodePlex site [Reporting Services RS.exe script migrates content](https://azuresql.codeplex.com/releases/view/115207) to a local folder.</span></span> <span data-ttu-id="10961-126">자세한 내용은 이 항목의 [스크립트 사용 방법](#bkmk_how_to_use_the_script) 섹션을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="10961-126">See the section [How to use the script](#bkmk_how_to_use_the_script) in this topic for more information.</span></span>  
  
##  <a name="supported-scenarios"></a><a name="bkmk_supported_scenarios"></a><span data-ttu-id="10961-127">지원 되는 시나리오</span><span class="sxs-lookup"><span data-stu-id="10961-127">Supported Scenarios</span></span>  
 <span data-ttu-id="10961-128">스크립트에서는 SharePoint 모드 및 기본 모드 보고서 서버가 모두 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="10961-128">The script supports both SharePoint mode and Native mode report servers.</span></span> <span data-ttu-id="10961-129">스크립트에는 다음과 같은 서버 버전이 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="10961-129">The script supports the following report server versions:</span></span>  
  
-   [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]  
  
-   [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]  
  
-   [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)]  
  
 <span data-ttu-id="10961-130">스크립트를 사용하면 동일한 모드 또는 서로 다른 모드의 보고서 서버 사이에 콘텐츠를 복사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="10961-130">The script can be used to copy content between report servers of the same mode or different modes.</span></span> <span data-ttu-id="10961-131">예를 들어 스크립트를 실행해서 [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] 기본 모드 보고서 서버에서 [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)] SharePoint 모드 보고서 서버로 콘텐츠를 복사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="10961-131">For example, you can run the script to copy content from a [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] native mode report server to a [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)] SharePoint mode report server.</span></span> <span data-ttu-id="10961-132">스크립트는 RS.exe가 설치된 모든 서버에서 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="10961-132">You can run the script from any server where RS.exe is installed.</span></span> <span data-ttu-id="10961-133">예를 들어 배포에서 다음 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="10961-133">For example, in the following deployment, you can:</span></span>  
  
-   <span data-ttu-id="10961-134">서버 A **상에서** RS.exe 및 스크립트를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="10961-134">Run RS.exe and the script **ON** Server A.</span></span>  
  
-   <span data-ttu-id="10961-135">서버 B **로부터**</span><span class="sxs-lookup"><span data-stu-id="10961-135">To copy content **FROM** Server B</span></span>  
  
-   <span data-ttu-id="10961-136">서버 C**쪽으로** 콘텐츠를 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="10961-136">**TO** Server C</span></span>  
  
|<span data-ttu-id="10961-137">서버 이름</span><span class="sxs-lookup"><span data-stu-id="10961-137">Server name</span></span>|<span data-ttu-id="10961-138">보고서 서버 모드</span><span class="sxs-lookup"><span data-stu-id="10961-138">Report Server Mode</span></span>|  
|-----------------|------------------------|  
|<span data-ttu-id="10961-139">서버 A</span><span class="sxs-lookup"><span data-stu-id="10961-139">Server A</span></span>|<span data-ttu-id="10961-140">기본</span><span class="sxs-lookup"><span data-stu-id="10961-140">Native</span></span>|  
|<span data-ttu-id="10961-141">서버 B</span><span class="sxs-lookup"><span data-stu-id="10961-141">Server B</span></span>|<span data-ttu-id="10961-142">SharePoint</span><span class="sxs-lookup"><span data-stu-id="10961-142">SharePoint</span></span>|  
|<span data-ttu-id="10961-143">콘텐츠를 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="10961-143">Server C</span></span>|<span data-ttu-id="10961-144">SharePoint</span><span class="sxs-lookup"><span data-stu-id="10961-144">SharePoint</span></span>|  
  
 <span data-ttu-id="10961-145">RS.exe 유틸리티에 대한 자세한 내용은 [RS.exe 유틸리티&#40;SSRS&#41;](rs-exe-utility-ssrs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="10961-145">For more information on the RS.exe utility, see [RS.exe Utility &#40;SSRS&#41;](rs-exe-utility-ssrs.md).</span></span>  
  
###  <a name="items-and-resources-the-script-migrates"></a><a name="bkmk_what_is_migrated"></a><span data-ttu-id="10961-146">스크립트가 마이그레이션하는 항목 및 리소스</span><span class="sxs-lookup"><span data-stu-id="10961-146">Items and resources the script migrates</span></span>  
 <span data-ttu-id="10961-147">스크립트는 이름이 동일한 기존 콘텐츠 항목을 덮어쓰지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="10961-147">The script will not write over existing content items of the same name.</span></span>  <span data-ttu-id="10961-148">스크립트가 대상 서버에서 원본 서버와 동일한 이름의 항목을 검색하면 개별 항목에서 "오류" 메시지가 발생되고 스크립트는 계속 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="10961-148">If the script detects items with the same name on the destination server that are on the source server, the individual items will result in a "failure" message and the script will continue.</span></span> <span data-ttu-id="10961-149">다음 표에서는 스크립트가 대상 보고서 서버 모드로 마이그레이션할 수 있는 콘텐츠 및 리소스 유형을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="10961-149">The following table lists the types of content and resources the script can migrate to target report server modes.</span></span>  
  
|<span data-ttu-id="10961-150">항목</span><span class="sxs-lookup"><span data-stu-id="10961-150">Item</span></span>|<span data-ttu-id="10961-151">마이그레이션</span><span class="sxs-lookup"><span data-stu-id="10961-151">Migrated</span></span>|<span data-ttu-id="10961-152">SharePoint</span><span class="sxs-lookup"><span data-stu-id="10961-152">SharePoint</span></span>|<span data-ttu-id="10961-153">설명</span><span class="sxs-lookup"><span data-stu-id="10961-153">Description</span></span>|  
|----------|--------------|----------------|-----------------|  
|<span data-ttu-id="10961-154">암호</span><span class="sxs-lookup"><span data-stu-id="10961-154">Passwords</span></span>|<span data-ttu-id="10961-155">‘아니요’</span><span class="sxs-lookup"><span data-stu-id="10961-155">**No**</span></span>|<span data-ttu-id="10961-156">‘아니요’</span><span class="sxs-lookup"><span data-stu-id="10961-156">**No**</span></span>|<span data-ttu-id="10961-157">암호는 마이그레이션되지 **않습니다** .</span><span class="sxs-lookup"><span data-stu-id="10961-157">Passwords are **NOT** migrated.</span></span> <span data-ttu-id="10961-158">콘텐츠 항목이 마이그레이션된 다음에는 대상 서버에서 자격 증명 정보를 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="10961-158">After content items are migrated, update the credential information on the destination server.</span></span> <span data-ttu-id="10961-159">예: 저장된 자격 증명이 포함된 데이터 원본.</span><span class="sxs-lookup"><span data-stu-id="10961-159">For example, data sources with stored credentials.</span></span>|  
|<span data-ttu-id="10961-160">내 보고서</span><span class="sxs-lookup"><span data-stu-id="10961-160">My Reports</span></span>|<span data-ttu-id="10961-161">‘아니요’</span><span class="sxs-lookup"><span data-stu-id="10961-161">**No**</span></span>|<span data-ttu-id="10961-162">**아니요**</span><span class="sxs-lookup"><span data-stu-id="10961-162">**No**</span></span>|<span data-ttu-id="10961-163">기본 모드의 "내 보고서" 기능은 개별 사용자 로그인을 기반으로 하므로, 스크립팅 서비스에는 rss 스크립트를 실행하는 데 사용된 **–u** 매개 변수 외에 사용자에 대해 "내 보고서" 폴더의 콘텐츠에 대한 액세스 권한이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="10961-163">The Native mode "My Reports" feature is based on individual user logins therefore the scripting service does not have access to content in "My Reports" folders for users other than the **-u** parameter used to run the rss script.</span></span> <span data-ttu-id="10961-164">또한 "내 보고서"는 sharepoint 모드의 기능이 아니라 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 폴더의 항목을 sharepoint 환경으로 복사할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="10961-164">Also, "My Reports" is not a feature of [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] SharePoint mode and items in the folders cannot be copied to a SharePoint environment.</span></span> <span data-ttu-id="10961-165">따라서 스크립트는 원본 기본 모드 보고서 서버의 "내 보고서" 폴더에 있는 보고서 항목을 복사 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="10961-165">Therefore, the script does not copy report items that are in the "My Reports" folders on a source native mode report server.</span></span> <span data-ttu-id="10961-166">이 스크립트를 사용 하 여 "내 보고서" 폴더의 콘텐츠를 마이그레이션하려면 다음을 완료 합니다.</span><span class="sxs-lookup"><span data-stu-id="10961-166">To migrate the content in "My Reports" folders with this script, complete the following:</span></span><br /><br /> <span data-ttu-id="10961-167">1) 보고서 관리자에서 새 폴더를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="10961-167">1) Create new folder(s) in Report Manager.</span></span> <span data-ttu-id="10961-168">필요에 따라 각 사용자에 대해 폴더 또는 하위 폴더를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="10961-168">Optionally, you can create folders or subfolder for each user.</span></span><br /><br /> <span data-ttu-id="10961-169">2) "내 보고서" 콘텐츠가 있는 사용자 중 하나로 로그인 합니다.</span><span class="sxs-lookup"><span data-stu-id="10961-169">2) Login as one of the users with "My Reports" content.</span></span><br /><br /> <span data-ttu-id="10961-170">3) 보고서 관리자에서 **내 보고서** 폴더를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="10961-170">3) In Report Manager, click the **My Reports** folder.</span></span><br /><br /> <span data-ttu-id="10961-171">4) 폴더에 대 한 **세부 정보** 보기를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="10961-171">4) Click the **Details** view for the folder.</span></span><br /><br /> <span data-ttu-id="10961-172">5) 복사 하려는 각 보고서를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="10961-172">5) Select each report that you want to copy.</span></span><br /><br /> <span data-ttu-id="10961-173">6) 보고서 관리자 도구 모음에서 **이동** 을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="10961-173">6) Click **Move** in the Report Manager toolbar.</span></span><br /><br /> <span data-ttu-id="10961-174">7) 원하는 대상 폴더를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="10961-174">7) Select the desired destination folder.</span></span><br /><br /> <span data-ttu-id="10961-175">8) 각 사용자에 대해 2-7 단계를 반복 합니다.</span><span class="sxs-lookup"><span data-stu-id="10961-175">8) Repeat steps 2-7 for each user.</span></span><br /><br /> <span data-ttu-id="10961-176">9) 스크립트를 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="10961-176">9) Run the script.</span></span>|  
|<span data-ttu-id="10961-177">기록</span><span class="sxs-lookup"><span data-stu-id="10961-177">History</span></span>|<span data-ttu-id="10961-178">‘아니요’</span><span class="sxs-lookup"><span data-stu-id="10961-178">**No**</span></span>|<span data-ttu-id="10961-179">‘아니요’</span><span class="sxs-lookup"><span data-stu-id="10961-179">**No**</span></span>||  
|<span data-ttu-id="10961-180">기록 설정</span><span class="sxs-lookup"><span data-stu-id="10961-180">History settings</span></span>|<span data-ttu-id="10961-181">예</span><span class="sxs-lookup"><span data-stu-id="10961-181">Yes</span></span>|<span data-ttu-id="10961-182">예</span><span class="sxs-lookup"><span data-stu-id="10961-182">Yes</span></span>|<span data-ttu-id="10961-183">기록 설정이 마이그레이션되지만 기록 세부 정보는 마이그레이션되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="10961-183">The history settings are migrated however the history details are NOT migrated.</span></span>|  
|<span data-ttu-id="10961-184">일정</span><span class="sxs-lookup"><span data-stu-id="10961-184">Schedules</span></span>|<span data-ttu-id="10961-185">예</span><span class="sxs-lookup"><span data-stu-id="10961-185">yes</span></span>|<span data-ttu-id="10961-186">예</span><span class="sxs-lookup"><span data-stu-id="10961-186">yes</span></span>|<span data-ttu-id="10961-187">일정을 마이그레이션하려면 대상 서버에서 SQL Server 에이전트가 실행 중이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="10961-187">To migrate schedules, it is required that SQL Server Agent is running on the target server.</span></span> <span data-ttu-id="10961-188">SQL Server 에이전트가 대상에서 실행 중이 아니면 다음과 비슷한 오류 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="10961-188">If SQL Server Agent is not running on the target, you will see an error message similar to the following:</span></span><br /><br /> `Migrating schedules: 1 items found. Migrating schedule: theMondaySchedule ... FAILURE:  The SQL Agent service is not running. This operation requires the SQL Agent service. ---> Microsoft.ReportingServices.Diagnostics.Utilities.SchedulerNotResponding Exception: The SQL Agent service is not running. This operation requires the SQL Agent service.`|  
|<span data-ttu-id="10961-189">역할 및 시스템 정책</span><span class="sxs-lookup"><span data-stu-id="10961-189">Roles and system policies</span></span>|<span data-ttu-id="10961-190">예</span><span class="sxs-lookup"><span data-stu-id="10961-190">Yes</span></span>|<span data-ttu-id="10961-191">예</span><span class="sxs-lookup"><span data-stu-id="10961-191">Yes</span></span>|<span data-ttu-id="10961-192">기본적으로 스크립트에서는 서버 사이에 사용자 지정 권한 스키마가 복사되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="10961-192">By default the script will not copy custom permission schema between servers.</span></span> <span data-ttu-id="10961-193">기본 동작은 ' 부모 권한 상속 ' 플래그가 TRUE로 설정 된 대상 서버에 항목을 배치 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="10961-193">The default behavior is the items will be coied to the destination server with the 'inherit parent permissions' flag set to TRUE.</span></span> <span data-ttu-id="10961-194">스크립트가 개별 항목의 권한을 복사하도록 하려면 SECURITY 스위치를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="10961-194">If you want the script to copy permissions for individual items, use the SECURITY switch.</span></span><br /><br /> <span data-ttu-id="10961-195">원본 및 대상 서버가 **동일한 보고서 서버 모드가 아니고**(예: 기본 모드에서 SharePoint 모드로), SECURITY 스위치를 사용하는 경우, 스크립트는 [Reporting Services의 역할 및 작업과 SharePoint 그룹 및 사용 권한 비교](../reporting-services-roles-tasks-vs-sharepoint-groups-permissions.md)항목에 설명된 비교 방법을 기준으로 기본 역할 및 그룹을 매핑하려고 시도합니다.</span><span class="sxs-lookup"><span data-stu-id="10961-195">If the source and target servers are **not the same report server mode**, for example from native mode to SharePoint mode, and you use the SECURITY switch, the script will attempt to map default roles and groups based on the comparison in the following topic [Compare Roles and Tasks in Reporting Services to SharePoint Groups and Permissions](../reporting-services-roles-tasks-vs-sharepoint-groups-permissions.md).</span></span> <span data-ttu-id="10961-196">사용자 지정 역할 및 그룹은 대상 서버로 복사되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="10961-196">Custom roles and groups are not copied to the destination server.</span></span><br /><br /> <span data-ttu-id="10961-197">**동일한 모드**의 서버 사이에 스크립트를 복사하고 SECURITY 스위치를 사용하는 경우에는 스크립트가 새 역할(기본 모드) 또는 그룹(SharePoint 모드)을 대상 서버에 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="10961-197">When the script is copying between servers **that are the same mode**, and you use the SECURITY switch, the script will create new roles (native mode) or groups (SharePoint mode) on the destination server.</span></span><br /><br /> <span data-ttu-id="10961-198">역할이 대상 서버에 이미 있을 경우 스크립트는 다음과 비슷한 “오류” 메시지를 만들고 다른 항목을 계속 마이그레이션합니다.</span><span class="sxs-lookup"><span data-stu-id="10961-198">If a role already exists on the destination server, the script will create a "Failure" message similar to the following, and continue migrating other items.</span></span> <span data-ttu-id="10961-199">스크립트가 완료되면 대상 서버의 역할이 사용자 요구에 맞게 구성되었는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="10961-199">After the script completes, verify the roles on the destination server are configured to meet your needs.</span></span> <span data-ttu-id="10961-200">마이그레이션 역할: 8개 항목이 발견되었습니다.</span><span class="sxs-lookup"><span data-stu-id="10961-200">the Migrating roles: 8 items found.</span></span><br /><br /> `Migrating role: Browser ... FAILURE: The role 'Browser' already exists and cannot be created. ---> Microsoft.ReportingServices.Diagnostics.Utilities.RoleAlreadyExistsException: The role 'Browser' already exists and cannot be created.`<br /><br /> <span data-ttu-id="10961-201">자세한 내용은 [사용자에게 보고서 서버에 대한 액세스 권한 부여&#40;보고서 관리자&#41;](../security/grant-user-access-to-a-report-server.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="10961-201">For more information, see [Grant User Access to a Report Server &#40;Report Manager&#41;](../security/grant-user-access-to-a-report-server.md)</span></span><br /><br /> <span data-ttu-id="10961-202">**참고:** 원본 서버에 있는 사용자가 대상 서버에 없을 경우 스크립트가 역할 지정을 대상 서버에 적용할 수 없고, SECURITY 스위치가 사용되었어도 스크립트가 역할 지정을 적용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="10961-202">**Note:** if a user that exists on the source server does not exist on the destination server, the script cannot apply role assignments on the destination server, the script cannot apply role assignments, even if the SECURITY switch is used.</span></span>|  
|<span data-ttu-id="10961-203">공유 데이터 원본</span><span class="sxs-lookup"><span data-stu-id="10961-203">Shared data source</span></span>|<span data-ttu-id="10961-204">예</span><span class="sxs-lookup"><span data-stu-id="10961-204">Yes</span></span>|<span data-ttu-id="10961-205">예</span><span class="sxs-lookup"><span data-stu-id="10961-205">Yes</span></span>|<span data-ttu-id="10961-206">스크립트가 대상 서버에 있는 기존 항목을 덮어쓰지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="10961-206">The script will not overwrite existing items on the target server.</span></span> <span data-ttu-id="10961-207">대상 서버에 있는 항목이 동일한 이름으로 존재할 경우 다음과 비슷한 오류 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="10961-207">If an item on the target server already exists with the same name, you will see an error message similar to the following:</span></span><br /><br /> `Migrating DataSource: /Data Sources/Aworks2012_oltp ... FAILURE:The item '/Data Sources/Aworks2012_oltp' already exists. ---> Microsoft.ReportingServices.Diagnostics.Utilities.ItemAlreadyExistsException: The item '/Data Source s/Aworks2012_oltp' already exists.`<br /><br /> <span data-ttu-id="10961-208">자격 증명이 데이터 원본의 일부로서 복사되지 **않습니다** .</span><span class="sxs-lookup"><span data-stu-id="10961-208">Credentials are **NOT** copied over as part of the data source.</span></span> <span data-ttu-id="10961-209">콘텐츠 항목이 마이그레이션된 다음에는 대상 서버에서 자격 증명 정보를 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="10961-209">After content items are migrated, update the credential information on the destination server.</span></span>|  
|<span data-ttu-id="10961-210">공유 데이터 세트</span><span class="sxs-lookup"><span data-stu-id="10961-210">Shared dataset</span></span>|<span data-ttu-id="10961-211">예</span><span class="sxs-lookup"><span data-stu-id="10961-211">Yes</span></span>|<span data-ttu-id="10961-212">예</span><span class="sxs-lookup"><span data-stu-id="10961-212">Yes</span></span>||  
|<span data-ttu-id="10961-213">폴더</span><span class="sxs-lookup"><span data-stu-id="10961-213">Folder</span></span>|<span data-ttu-id="10961-214">예</span><span class="sxs-lookup"><span data-stu-id="10961-214">Yes</span></span>|<span data-ttu-id="10961-215">예</span><span class="sxs-lookup"><span data-stu-id="10961-215">Yes</span></span>|<span data-ttu-id="10961-216">스크립트가 대상 서버에 있는 기존 항목을 덮어쓰지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="10961-216">The script will not overwrite existing items on the target server.</span></span> <span data-ttu-id="10961-217">대상 서버에 있는 항목이 동일한 이름으로 존재할 경우 다음과 비슷한 오류 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="10961-217">If an item on the target server already exists with the same name, you will see an error message similar to the following:</span></span><br /><br /> `Migrating Folder: /Reports ... FAILURE: The item '/Reports' already exists. ---> Microsoft.ReportingServices.Diagnostics.Utilities.ItemAlreadyExistsException: The item '/Reports' already exists.`|  
|<span data-ttu-id="10961-218">보고서</span><span class="sxs-lookup"><span data-stu-id="10961-218">Report</span></span>|<span data-ttu-id="10961-219">예</span><span class="sxs-lookup"><span data-stu-id="10961-219">Yes</span></span>|<span data-ttu-id="10961-220">예</span><span class="sxs-lookup"><span data-stu-id="10961-220">Yes</span></span>|<span data-ttu-id="10961-221">스크립트가 대상 서버에 있는 기존 항목을 덮어쓰지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="10961-221">The script will not overwrite existing items on the target server.</span></span> <span data-ttu-id="10961-222">대상 서버에 있는 항목이 동일한 이름으로 존재할 경우 다음과 비슷한 오류 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="10961-222">If an item on the target server already exists with the same name, you will see an error message similar to the following:</span></span><br /><br /> `Migrating Report: /Reports/testThe item '/Reports/test' already exists. ---> Microsoft.ReportingServices.Diagnostics.Utilities.ItemAlreadyExistsException: The item '/Reports/test' already exists.`|  
|<span data-ttu-id="10961-223">매개 변수</span><span class="sxs-lookup"><span data-stu-id="10961-223">Parameters</span></span>|<span data-ttu-id="10961-224">예</span><span class="sxs-lookup"><span data-stu-id="10961-224">Yes</span></span>|<span data-ttu-id="10961-225">예</span><span class="sxs-lookup"><span data-stu-id="10961-225">Yes</span></span>||  
|<span data-ttu-id="10961-226">구독</span><span class="sxs-lookup"><span data-stu-id="10961-226">Subscriptions</span></span>|<span data-ttu-id="10961-227">예</span><span class="sxs-lookup"><span data-stu-id="10961-227">Yes</span></span>|<span data-ttu-id="10961-228">예</span><span class="sxs-lookup"><span data-stu-id="10961-228">Yes</span></span>||  
|<span data-ttu-id="10961-229">기록 설정</span><span class="sxs-lookup"><span data-stu-id="10961-229">History Settings</span></span>|<span data-ttu-id="10961-230">예</span><span class="sxs-lookup"><span data-stu-id="10961-230">Yes</span></span>|<span data-ttu-id="10961-231">예</span><span class="sxs-lookup"><span data-stu-id="10961-231">Yes</span></span>|<span data-ttu-id="10961-232">기록 설정이 마이그레이션되지만 기록 세부 정보는 마이그레이션되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="10961-232">The history settings are migrated however the history details are NOT migrated.</span></span>|  
|<span data-ttu-id="10961-233">처리 옵션</span><span class="sxs-lookup"><span data-stu-id="10961-233">processing options</span></span>|<span data-ttu-id="10961-234">예</span><span class="sxs-lookup"><span data-stu-id="10961-234">Yes</span></span>|<span data-ttu-id="10961-235">예</span><span class="sxs-lookup"><span data-stu-id="10961-235">Yes</span></span>||  
|<span data-ttu-id="10961-236">캐시 새로 고침 옵션</span><span class="sxs-lookup"><span data-stu-id="10961-236">cache refresh options</span></span>|<span data-ttu-id="10961-237">예</span><span class="sxs-lookup"><span data-stu-id="10961-237">Yes</span></span>|<span data-ttu-id="10961-238">예</span><span class="sxs-lookup"><span data-stu-id="10961-238">Yes</span></span>|<span data-ttu-id="10961-239">종속 설정은 카탈로그 항목의 일부로 마이그레이션됩니다.</span><span class="sxs-lookup"><span data-stu-id="10961-239">Dependent settings are migrated as part of a catalog item.</span></span> <span data-ttu-id="10961-240">다음은 보고서(.rdl) 및 캐시 새로 고침 옵션과 같은 관련 설정을 마이그레이션하는 스크립트의 예제입니다.</span><span class="sxs-lookup"><span data-stu-id="10961-240">The following is the sample out of the script as it migrates a report (.rdl) and related settings such as cache refresh options:</span></span><br /><br /> <span data-ttu-id="10961-241">TitleOnly.rdl 보고서에 대한 매개 변수를 마이그레이션하는 중: 0개 항목이 발견되었습니다.</span><span class="sxs-lookup"><span data-stu-id="10961-241">Migrating parameters for report TitleOnly.rdl 0 items found.</span></span><br /><br /> <span data-ttu-id="10961-242">TitleOnly.rdl 보고서에 대한 구독을 마이그레이션하는 중: 1개 항목이 발견되었습니다.</span><span class="sxs-lookup"><span data-stu-id="10961-242">Migrating subscriptions for report TitleOnly.rdl: 1 items found.</span></span><br /><br /> <span data-ttu-id="10961-243">구독을 마이그레이션하 \\ 는 중 \server\public\savedreports에서 titleonly에서 titleonly.rdl로 저장 하는 중 ... 성공할</span><span class="sxs-lookup"><span data-stu-id="10961-243">Migrating subscription Save in \\\server\public\savedreports as TitleOnly ... SUCCESS</span></span><br /><br /> <span data-ttu-id="10961-244">TitleOnly.rdl 보고서에 대한 기록 설정을 마이그레이션하는 중... SUCCESS</span><span class="sxs-lookup"><span data-stu-id="10961-244">Migrating history settings for report TitleOnly.rdl ... SUCCESS</span></span><br /><br /> <span data-ttu-id="10961-245">TitleOnly.rdl 보고서에 대한 처리 옵션을 마이그레이션하는 중... 0개 항목이 발견되었습니다.</span><span class="sxs-lookup"><span data-stu-id="10961-245">Migrating processing options for report TitleOnly.rdl ... 0 items found.</span></span><br /><br /> <span data-ttu-id="10961-246">TitleOnly.rdl 보고서에 대한 캐시 새로 고침 옵션을 마이그레이션하는 중... SUCCESS</span><span class="sxs-lookup"><span data-stu-id="10961-246">Migrating cache refresh options for report TitleOnly.rdl ... SUCCESS</span></span><br /><br /> <span data-ttu-id="10961-247">TitleOnly.rdl 보고서에 대한 캐시 새로 고침 계획을 마이그레이션하는 중: 1개 항목이 발견되었습니다.</span><span class="sxs-lookup"><span data-stu-id="10961-247">Migrating cache refresh plans for report TitleOnly.rdl: 1 items found.</span></span><br /><br /> <span data-ttu-id="10961-248">캐시 새로 고침 계획 titleonly_refresh735amM2F를 마이그레이션하는 중... SUCCESS</span><span class="sxs-lookup"><span data-stu-id="10961-248">Migrating cache refresh plan titleonly_refresh735amM2F ... SUCCESS</span></span>|  
|<span data-ttu-id="10961-249">캐시 새로 고침 계획</span><span class="sxs-lookup"><span data-stu-id="10961-249">Cache refresh plans</span></span>|<span data-ttu-id="10961-250">예</span><span class="sxs-lookup"><span data-stu-id="10961-250">Yes</span></span>|<span data-ttu-id="10961-251">예</span><span class="sxs-lookup"><span data-stu-id="10961-251">Yes</span></span>||  
|<span data-ttu-id="10961-252">이미지</span><span class="sxs-lookup"><span data-stu-id="10961-252">Images</span></span>|<span data-ttu-id="10961-253">예</span><span class="sxs-lookup"><span data-stu-id="10961-253">Yes</span></span>|<span data-ttu-id="10961-254">예</span><span class="sxs-lookup"><span data-stu-id="10961-254">Yes</span></span>||  
|<span data-ttu-id="10961-255">보고서 파트</span><span class="sxs-lookup"><span data-stu-id="10961-255">Report parts</span></span>|<span data-ttu-id="10961-256">예</span><span class="sxs-lookup"><span data-stu-id="10961-256">Yes</span></span>|<span data-ttu-id="10961-257">예</span><span class="sxs-lookup"><span data-stu-id="10961-257">Yes</span></span>||  
  
##  <a name="required-permissions"></a><a name="bkmk_required_permissions"></a> <span data-ttu-id="10961-258">필요한 권한</span><span class="sxs-lookup"><span data-stu-id="10961-258">Required Permissions</span></span>  
 <span data-ttu-id="10961-259">항목 및 리소스 읽기 또는 쓰기에 필요한 권한이 스크립트에 사용된 모든 메서드와 동일하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="10961-259">The permissions required to read or write items and resources is not the same for all of the methods used in the script.</span></span> <span data-ttu-id="10961-260">다음 표에서는 각 항목 또는 리소스에 사용된 메서드 및 관련 내용에 대한 링크를 요약해서 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="10961-260">The following table summarizes the methods used for each item or resource and links to related content.</span></span> <span data-ttu-id="10961-261">필요한 권한을 보려면 개별 항목으로 이동하세요.</span><span class="sxs-lookup"><span data-stu-id="10961-261">Navigate to the individual topic to see the required permissions.</span></span> <span data-ttu-id="10961-262">예를 들어 ListChildren 메서드 항목에는 다음과 같은 필요 권한이 설명됩니다.</span><span class="sxs-lookup"><span data-stu-id="10961-262">For example the ListChildren method topic notes the required permissions of:</span></span>  
  
-   <span data-ttu-id="10961-263">**기본 모드에 필요한 권한:** 항목의 ReadProperties</span><span class="sxs-lookup"><span data-stu-id="10961-263">**Native Mode Required Permissions:** ReadProperties on Item</span></span>  
  
-   <span data-ttu-id="10961-264">**SharePoint 모드에 필요한 권한:** ViewListItems</span><span class="sxs-lookup"><span data-stu-id="10961-264">**SharePoint Mode Required Permissions:** ViewListItems</span></span>  
  
|<span data-ttu-id="10961-265">항목 또는 리소스</span><span class="sxs-lookup"><span data-stu-id="10961-265">Item or Resource</span></span>|<span data-ttu-id="10961-266">원본</span><span class="sxs-lookup"><span data-stu-id="10961-266">Source</span></span>|<span data-ttu-id="10961-267">대상</span><span class="sxs-lookup"><span data-stu-id="10961-267">Target</span></span>|  
|----------------------|------------|------------|  
|<span data-ttu-id="10961-268">카탈로그 항목</span><span class="sxs-lookup"><span data-stu-id="10961-268">Catalog items</span></span>|<xref:ReportService2010.ReportingService2010.ListChildren%2A><br /><br /> <xref:ReportService2010.ReportingService2010.GetProperties%2A><br /><br /> <xref:ReportService2010.ReportingService2010.GetItemDataSources%2A><br /><br /> <xref:ReportService2010.ReportingService2010.GetItemReferences%2A><br /><br /> <xref:ReportService2010.ReportingService2010.GetDataSourceContents%2A><br /><br /> <xref:ReportService2010.ReportingService2010.GetItemLink%2A>|<xref:ReportService2010.ReportingService2010.CreateCatalogItem%2A><br /><br /> <xref:ReportService2010.ReportingService2010.SetItemDataSources%2A><br /><br /> <xref:ReportService2010.ReportingService2010.GetItemReferences%2A><br /><br /> <xref:ReportService2010.ReportingService2010.CreateDataSource%2A><br /><br /> <xref:ReportService2010.ReportingService2010.CreateLinkedItem%2A><br /><br /> <xref:ReportService2010.ReportingService2010.CreateFolder%2A>|  
|<span data-ttu-id="10961-269">역할</span><span class="sxs-lookup"><span data-stu-id="10961-269">Role</span></span>|<xref:ReportService2010.ReportingService2010.ListRoles%2A><br /><br /> <xref:ReportService2010.ReportingService2010.GetRoleProperties%2A>|<xref:ReportService2010.ReportingService2010.CreateRole%2A>|  
|<span data-ttu-id="10961-270">시스템 정책</span><span class="sxs-lookup"><span data-stu-id="10961-270">System Policy</span></span>|<xref:ReportService2010.ReportingService2010.GetSystemPolicies%2A>|<xref:ReportService2010.ReportingService2010.SetSystemPolicies%2A>|  
|<span data-ttu-id="10961-271">예약</span><span class="sxs-lookup"><span data-stu-id="10961-271">Schedule</span></span>|<xref:ReportService2010.ReportingService2010.ListSchedules%2A>|<xref:ReportService2010.ReportingService2010.CreateSchedule%2A>|  
|<span data-ttu-id="10961-272">구독</span><span class="sxs-lookup"><span data-stu-id="10961-272">Subscription</span></span>|<xref:ReportService2010.ReportingService2010.ListSubscriptions%2A><br /><br /> <xref:ReportService2010.ReportingService2010.GetSubscriptionProperties%2A><br /><br /> <xref:ReportService2010.ReportingService2010.GetDataDrivenSubscriptionProperties%2A>|<xref:ReportService2010.ReportingService2010.CreateSubscription%2A><br /><br /> <xref:ReportService2010.ReportingService2010.CreateDataDrivenSubscription%2A>|  
|<span data-ttu-id="10961-273">캐시 새로 고침 계획</span><span class="sxs-lookup"><span data-stu-id="10961-273">Cache refresh plan</span></span>|<xref:ReportService2010.ReportingService2010.ListCacheRefreshPlans%2A><br /><br /> <xref:ReportService2010.ReportingService2010.GetCacheRefreshPlanProperties%2A>|<xref:ReportService2010.ReportingService2010.CreateCacheRefreshPlan%2A>|  
|<span data-ttu-id="10961-274">매개 변수</span><span class="sxs-lookup"><span data-stu-id="10961-274">Parameters</span></span>|<xref:ReportService2010.ReportingService2010.GetItemParameters%2A>|<xref:ReportService2010.ReportingService2010.SetItemParameters%2A>|  
|<span data-ttu-id="10961-275">실행 옵션</span><span class="sxs-lookup"><span data-stu-id="10961-275">Execution options</span></span>|<xref:ReportService2010.ReportingService2010.GetExecutionOptions%2A>|<xref:ReportService2010.ReportingService2010.SetExecutionOptions%2A>|  
|<span data-ttu-id="10961-276">캐시 옵션</span><span class="sxs-lookup"><span data-stu-id="10961-276">Cache options</span></span>|<xref:ReportService2010.ReportingService2010.GetCacheOptions%2A>|<xref:ReportService2010.ReportingService2010.SetCacheOptions%2A>|  
|<span data-ttu-id="10961-277">기록 설정</span><span class="sxs-lookup"><span data-stu-id="10961-277">History settings</span></span>|<xref:ReportService2010.ReportingService2010.GetItemHistoryOptions%2A>|<xref:ReportService2010.ReportingService2010.SetItemHistoryOptions%2A>|  
|<span data-ttu-id="10961-278">항목 정책</span><span class="sxs-lookup"><span data-stu-id="10961-278">Item Policy</span></span>|<xref:ReportService2010.ReportingService2010.GetPolicies%2A>|<xref:ReportService2010.ReportingService2010.SetPolicies%2A>|  
  
 <span data-ttu-id="10961-279">자세한 내용은 [Reporting Services의 역할 및 작업과 SharePoint 그룹 및 사용 권한 비교](../reporting-services-roles-tasks-vs-sharepoint-groups-permissions.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="10961-279">For more information, see [Compare Roles and Tasks in Reporting Services to SharePoint Groups and Permissions](../reporting-services-roles-tasks-vs-sharepoint-groups-permissions.md).</span></span>  
  
##  <a name="how-to-use-the-script"></a><a name="bkmk_how_to_use_the_script"></a><span data-ttu-id="10961-280">스크립트를 사용 하는 방법</span><span class="sxs-lookup"><span data-stu-id="10961-280">How to use the script</span></span>  
  
1.  <span data-ttu-id="10961-281">스크립트 파일을 로컬 폴더에 다운로드합니다(예: **c:\rss\ssrs_migration.rss**).</span><span class="sxs-lookup"><span data-stu-id="10961-281">Download the script file to a local folder, for example **c:\rss\ssrs_migration.rss**.</span></span>  
  
2.  <span data-ttu-id="10961-282">**관리자 권한으로**명령 프롬프트를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="10961-282">Open a command prompt **with administrative privileges**.</span></span>  
  
3.  <span data-ttu-id="10961-283">ssrs_migration.rss 파일이 포함된 폴더로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="10961-283">Navigate to the folder containing the ssrs_migration.rss file.</span></span>  
  
4.  <span data-ttu-id="10961-284">시나리오에 적합한 매개 변수를 사용해서 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="10961-284">Run the command with the parameters appropriate for your scenario.</span></span>  
  
 <span data-ttu-id="10961-285">**기본 예제, 기본 모드 보고서 서버에서 기본 모드 보고서 서버로:**</span><span class="sxs-lookup"><span data-stu-id="10961-285">**Basic Example, native mode report server to native mode report server:**</span></span>  
  
 <span data-ttu-id="10961-286">다음 예제에서는 기본 모드 **Sourceserver** 에서 기본 모드 **Targetserver**로 콘텐츠를 마이그레이션합니다.</span><span class="sxs-lookup"><span data-stu-id="10961-286">The following example migrates content from the native mode **Sourceserver** to the native mode **Targetserver**.</span></span>  
  
 ```cmd
rs.exe -i ssrs_migration.rss -e Mgmt2010 -s http://SourceServer/ReportServer -u Domain\User -p password -v ts="http://TargetServer/reportserver" -v tu="Domain\Userser" -v tp="password"
```
  
 <span data-ttu-id="10961-287">**사용 정보:**</span><span class="sxs-lookup"><span data-stu-id="10961-287">**Usage notes:**</span></span>  
  
-   <span data-ttu-id="10961-288">스크립트는 두 단계로 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="10961-288">The script runs in two steps.</span></span>  
  
     <span data-ttu-id="10961-289">첫 번째 단계는 마이그레이션되는 항목 목록을 반환하는 감사 단계이고, 두 번째 단계는 마이그레이션 프로세스 단계입니다.</span><span class="sxs-lookup"><span data-stu-id="10961-289">The first step is an audit, to return a list of items that will be migrated and the second step is the migration process.</span></span>  
  
     <span data-ttu-id="10961-290">가능한 마이그레이션 목록만 보길 원하는 경우 또는 매개 변수를 수정하길 원하는 경우에는 **1단계 후에 스크립트를 취소** 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="10961-290">You can **cancel the script after step** one if you only want to see the possible migration list or you want to modify the parameters.</span></span> <span data-ttu-id="10961-291">종속 설정은 1단계에 나열되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="10961-291">Dependent settings are not listed in step one.</span></span> <span data-ttu-id="10961-292">예를 들어 보고서의 캐시 옵션이 나열되지 않지만 보고서 자체는 나열됩니다.</span><span class="sxs-lookup"><span data-stu-id="10961-292">For example, the cache options of a report are not listed but the report itself is.</span></span>  
  
    > [!TIP]  
    >  <span data-ttu-id="10961-293">단일 서버만 감사하려는 경우, 원본 및 대상에 대해 같은 서버를 사용하고 1단계 후 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="10961-293">If you want to just audit a single server, use the same server for source and destination and cancel after step 1</span></span>  
  
     <span data-ttu-id="10961-294">1단계 감사 정보를 올바르게 활용하는 방법은 원본 및 대상 기본 모드 서버 모두에서 기존 역할을 검토하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="10961-294">A good use of the step 1 audit information is to review existing roles on both the source and target Native mode server.</span></span> <span data-ttu-id="10961-295">다음은 1단계 감사 목록의 예입니다.</span><span class="sxs-lookup"><span data-stu-id="10961-295">The following is an example of the step one audit list.</span></span> <span data-ttu-id="10961-296">-v security="True" 스위치가 사용되었기 때문에 목록에 "역할" 섹션이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="10961-296">Notice the list includes a "roles" section because the switch-v security="True" was used:</span></span>  
  
    -   `Retrieve and report the list of items that will be migrated. You can cancel the script after step 1 if you do not want to start the actual migration.`  
  
         `Retrieving roles:`  
  
         `Role: Browser`  
  
         `Role: Content Manager`  
  
         `Role: Model Item Browser`  
  
         `Retrieve and report the list of items that will be migrated. You can cancel the script after step 1 if you do not want to start the actual migration.`  
  
         `Retrieving roles:`  
  
         `Role: Browser`  
  
         `Role: Content Manager`  
  
         `Role: CustomRole`  
  
         `Role: Model Item Browser`  
  
         `Role: My Reports`  
  
         `Role: Publisher`  
  
         `Role: Report Builder`  
  
         `Role: System Administrator`  
  
         `Role: System User`  
  
         `Retrieving system policies:`  
  
         `Retrieving system policies:`  
  
         `System policy: BUILTIN\Administrators`  
  
         `System policy: domain\user1`  
  
         `System policy: domain\ueser2`  
  
         `Retrieving schedules:`  
  
         `Schedule: theMondaySchedule`  
  
         `Retrieving catalog items. This may take a while.`  
  
         `Folder: /Data Sources`  
  
         `DataSource: /Data Sources/Aworks2012_oltp`  
  
         `Folder: /images`  
  
         `Resource: /images/Boba Fett.png`  
  
         `Resource: /images/R2-D2.png`  
  
         `Folder: /Reports`  
  
         `Report: /Reports/products`  
  
         `Report: /Reports/test`  
  
         `Report: /Reports/TitleOnly`  
  
-   <span data-ttu-id="10961-297">SOURCE_URL 및 TARGET_URL은 원본 및 대상 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 보고서 서버를 가리키는 올바른 보고서 서버 URL이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="10961-297">The SOURCE_URL and TARGET_URL must be valid report server URLs that point to the source and target [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] report server.</span></span> <span data-ttu-id="10961-298">기본 모드에서 보고서 서버 URL은 다음과 같이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="10961-298">In native mode, a report server URL looks like the following:</span></span>  
  
    -   `http://servername/reportserver`  
  
     <span data-ttu-id="10961-299">SharePoint 모드에서는 URL이 다음과 같이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="10961-299">In SharePoint mode the URL looks like the following:</span></span>  
  
    -   `http://servername/_vti_bin/reportserver`  
  
-   <span data-ttu-id="10961-300">SharePoint에서 사용자에게 제공되는 가상 폴더 구조는 기본 구조와 다를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="10961-300">The virtual folder structure presented to the user in SharePoint might be different than the underlying one.</span></span> <span data-ttu-id="10961-301">가상이 아닌 폴더 구조를 보려면 브라우저에서 `http://servername/_vti_bin/reportserver` 또는 `http://servername/sites/site_name/_vti_bin/reportserver` 를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="10961-301">Open `http://servername/_vti_bin/reportserver` or `http://servername/sites/site_name/_vti_bin/reportserver` in a browser to see the non-virtual folder structure.</span></span> <span data-ttu-id="10961-302">이렇게 하면 SharePoint 모드의 서버에 대해 원본 폴더 및 대상 폴더를 "/" 이외의 다른 위치로 설정하는 데 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="10961-302">This is helpful for setting source folder and target folder to something other than "/", for a server in SharePoint mode.</span></span>  
  
-   <span data-ttu-id="10961-303">저장된 자격 증명이 포함된 데이터 원본과 같은 경우 암호가 마이그레이션되지 않으며 다시 입력해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="10961-303">Passwords are not migrated, and must be re-entered, for example data sources with stored credentials.</span></span>  
  
##  <a name="parameter-description"></a><a name="bkmk_parameter_description"></a><span data-ttu-id="10961-304">매개 변수 설명</span><span class="sxs-lookup"><span data-stu-id="10961-304">Parameter Description</span></span>  
  
|<span data-ttu-id="10961-305">매개 변수</span><span class="sxs-lookup"><span data-stu-id="10961-305">Parameter</span></span>|<span data-ttu-id="10961-306">설명</span><span class="sxs-lookup"><span data-stu-id="10961-306">Description</span></span>|<span data-ttu-id="10961-307">필수</span><span class="sxs-lookup"><span data-stu-id="10961-307">Required</span></span>|  
|---------------|-----------------|--------------|  
|<span data-ttu-id="10961-308">**-s** Source_URL</span><span class="sxs-lookup"><span data-stu-id="10961-308">**-s** Source_URL</span></span>|<span data-ttu-id="10961-309">원본 보고서 서버의 URL</span><span class="sxs-lookup"><span data-stu-id="10961-309">URL of the source report server</span></span>|<span data-ttu-id="10961-310">Yes</span><span class="sxs-lookup"><span data-stu-id="10961-310">Yes</span></span>|  
|<span data-ttu-id="10961-311">**-u** Domain\password **–p** 암호</span><span class="sxs-lookup"><span data-stu-id="10961-311">**-u** Domain\password **-p** password</span></span>|<span data-ttu-id="10961-312">원본 서버의 자격 증명입니다.</span><span class="sxs-lookup"><span data-stu-id="10961-312">Credentials for source server.</span></span>|<span data-ttu-id="10961-313">선택 사항입니다. 누락된 경우 기본 자격 증명이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="10961-313">OPTIONAL, default credentials are used if missing</span></span>|  
|<span data-ttu-id="10961-314">**-v st**="SITE"</span><span class="sxs-lookup"><span data-stu-id="10961-314">**-v st**="SITE"</span></span>||<span data-ttu-id="10961-315">옵션.</span><span class="sxs-lookup"><span data-stu-id="10961-315">OPTIONAL.</span></span> <span data-ttu-id="10961-316">이 매개 변수는 SharePoint 모드 보고서 서버에서만 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="10961-316">This parameter is only used for SharePoint mode report servers.</span></span>|  
|<span data-ttu-id="10961-317">**- v f**="SOURCEFOLDER"</span><span class="sxs-lookup"><span data-stu-id="10961-317">**- v f**="SOURCEFOLDER"</span></span>|<span data-ttu-id="10961-318">모든 항목을 마이그레이션할 경우 "/"로 설정하고, 일부만 마이그레이션할 경우에는 "/folder/subfolder"와 같은 값으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="10961-318">Set to "/" for migrating everything, or to something like "/folder/subfolder" for partial migration.</span></span> <span data-ttu-id="10961-319">이 폴더 내의 모든 항목이 복사됩니다.</span><span class="sxs-lookup"><span data-stu-id="10961-319">Everything within this folder will be copied</span></span>|<span data-ttu-id="10961-320">선택 사항입니다. 기본값은 "/"입니다.</span><span class="sxs-lookup"><span data-stu-id="10961-320">OPTIONAL, default is "/".</span></span>|  
|<span data-ttu-id="10961-321">**-v ts**="TARGET_URL"</span><span class="sxs-lookup"><span data-stu-id="10961-321">**-v ts**="TARGET_URL"</span></span>|<span data-ttu-id="10961-322">'대상 RS 서버의 URL'</span><span class="sxs-lookup"><span data-stu-id="10961-322">'URL of the target RS server"</span></span>||  
|<span data-ttu-id="10961-323">**-v tu**="domain\username" **-v tp**="password"</span><span class="sxs-lookup"><span data-stu-id="10961-323">**-v tu**="domain\username" **-v tp**="password"</span></span>|<span data-ttu-id="10961-324">'대상 서버의 자격 증명입니다.'</span><span class="sxs-lookup"><span data-stu-id="10961-324">'Credentials for target server.</span></span>|<span data-ttu-id="10961-325">선택 사항입니다. 누락된 경우 기본 자격 증명이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="10961-325">OPTIONAL, default credentials are used if missing.</span></span> <span data-ttu-id="10961-326">**참고:** 사용자가 공유 일정의 "생성자"로 나열되고 대상 서버에서 보고서 항목의 계정에 따라 "수정"됩니다.</span><span class="sxs-lookup"><span data-stu-id="10961-326">**Note:** the user will be listed as the "creator" of shared schedules and "modified by" account for report items, in the target server.</span></span>|  
|<span data-ttu-id="10961-327">**-v tst**="SITE"</span><span class="sxs-lookup"><span data-stu-id="10961-327">**-v tst**="SITE"</span></span>||<span data-ttu-id="10961-328">옵션.</span><span class="sxs-lookup"><span data-stu-id="10961-328">OPTIONAL.</span></span> <span data-ttu-id="10961-329">이 매개 변수는 SharePoint 모드 보고서 서버에서만 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="10961-329">This parameter is only used for SharePoint mode report servers.</span></span>|  
|<span data-ttu-id="10961-330">**-v tf** ="TARGETFOLDER"</span><span class="sxs-lookup"><span data-stu-id="10961-330">**-v tf** ="TARGETFOLDER"</span></span>|<span data-ttu-id="10961-331">'루트 수준으로 마이그레이션하려면 "/"로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="10961-331">'Set to "/" for migrating into the root level.</span></span> <span data-ttu-id="10961-332">존재하는 항목으로 복사하려면 "/folder/subfolder"의 형식으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="10961-332">Set to "/folder/subfolder" to copy into a that already exists.</span></span> <span data-ttu-id="10961-333">"SOURCEFOLDER" 안의 모든 항목이 "TARGETFOLDER"에 복사됩니다.</span><span class="sxs-lookup"><span data-stu-id="10961-333">Everything within "SOURCEFOLDER" will be copied into "TARGETFOLDER.</span></span>|<span data-ttu-id="10961-334">선택 사항입니다. 기본값은 "/"입니다.</span><span class="sxs-lookup"><span data-stu-id="10961-334">OPTIONAL, default is "/".</span></span>|  
|<span data-ttu-id="10961-335">**-v security**= "True/False"</span><span class="sxs-lookup"><span data-stu-id="10961-335">**-v security**= "True/False"</span></span>|<span data-ttu-id="10961-336">“False”로 설정된 경우 대상 카탈로그 항목은 대상 시스템의 설정에 따라 보안 설정을 상속합니다.</span><span class="sxs-lookup"><span data-stu-id="10961-336">If set to "False", destination catalog items will inherit security setting according to the settings of the target system.</span></span> <span data-ttu-id="10961-337">이 설정은 기본 모드에서 SharePoint 모드로의 마이그레이션과 같이 서로 다른 보고서 서버 유형 사이의 마이그레이션에 대해 권장되는 설정입니다.</span><span class="sxs-lookup"><span data-stu-id="10961-337">This is the recommended setting for migrations between different report server types, for example native mode to SharePoint mode.</span></span> <span data-ttu-id="10961-338">“True”로 설정된 경우 스크립트가 보안 설정을 마이그레이션하려고 시도합니다.</span><span class="sxs-lookup"><span data-stu-id="10961-338">If set to "True", the script attempts to migrate security settings.</span></span>|<span data-ttu-id="10961-339">선택 사항입니다. 기본값은 "False"입니다.</span><span class="sxs-lookup"><span data-stu-id="10961-339">OPTIONAL, default is "False".</span></span>|  
  
##  <a name="more-examples"></a><a name="bkmk_more_examples"></a><span data-ttu-id="10961-340">추가 예제</span><span class="sxs-lookup"><span data-stu-id="10961-340">More Examples</span></span>  
  
###  <a name="native-mode-report-server-to-native-mode-report-server"></a><a name="bkmk_native_2_native"></a><span data-ttu-id="10961-341">기본 모드 보고서 서버에서 기본 모드 보고서 서버로</span><span class="sxs-lookup"><span data-stu-id="10961-341">Native Mode Report Server to Native Mode Report Server</span></span>  
 <span data-ttu-id="10961-342">다음 예제에서는 기본 모드 **Sourceserver** 에서 기본 모드 **Targetserver**로 콘텐츠를 마이그레이션합니다.</span><span class="sxs-lookup"><span data-stu-id="10961-342">The following example migrates content from the native mode **Sourceserver** to the native mode **Targetserver**.</span></span>  
  
```cmd
rs.exe -i ssrs_migration.rss -e Mgmt2010 -s http://SourceServer/ReportServer -u Domain\User -p password -v ts="http://TargetServer/reportserver" -v tu="Domain\Userser" -v tp="password"  
```  
  
 <span data-ttu-id="10961-343">다음 예제는 보안 스위치를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="10961-343">The following example adds the security switch:</span></span>  
  
```cmd
rs.exe -i ssrs_migration.rss -e Mgmt2010 -s http://SourceServer/ReportServer -u Domain\User -p password -v ts="http://TargetServer/reportserver" -v tu="Domain\Userser" -v tp="password" -v security="True"  
```  
  
###  <a name="native-mode-to-sharepoint-mode---root-site"></a><a name="bkmk_native_2_sharepoint_root"></a> <span data-ttu-id="10961-344">기본 모드에서 SharePoint 모드로 - 루트 사이트</span><span class="sxs-lookup"><span data-stu-id="10961-344">Native Mode to SharePoint Mode - root site</span></span>  
 <span data-ttu-id="10961-345">다음 예제에서는 기본 모드 **SourceServer**에서 SharePoint 모드 서버 **TargetServer**의 "루트 사이트"로 콘텐츠를 마이그레이션합니다.</span><span class="sxs-lookup"><span data-stu-id="10961-345">The following example migrates content from a native mode **SourceServer** to the "root site " on a SharePoint mode server **TargetServer**.</span></span> <span data-ttu-id="10961-346">기본 모드 서버의 "보고서" 및 "데이터 원본" 폴더는 SharePoint 배포에서 새 라이브러리로 마이그레이션됩니다.</span><span class="sxs-lookup"><span data-stu-id="10961-346">The "Reports" and "Data Sources" folders on the native mode server as migrated as new libraries on the SharePoint deployment.</span></span>  
  
 <span data-ttu-id="10961-347">![ssrs_rss_migrate_root_site](../media/ssrs-rss-migrate-root-site.gif "ssrs_rss_migrate_root_site")</span><span class="sxs-lookup"><span data-stu-id="10961-347">![ssrs_rss_migrate_root_site](../media/ssrs-rss-migrate-root-site.gif "ssrs_rss_migrate_root_site")</span></span>  
  
```cmd
rs.exe -i ssrs_migration.rss -e Mgmt2010 -s http://SourceServer/ReportServer -u Domain\User -p Password -v ts="http://TargetServer/_vti_bin/ReportServer" -v tu="Domain\User" -v tp="Password"  
```  
  
###  <a name="native-mode-to-sharepoint-mode--bi-site-collection"></a><a name="bkmk_native_2_sharepoint_with_site"></a> <span data-ttu-id="10961-348">기본 모드에서 SharePoint 모드로 - 'bi' 사이트 컬렉션</span><span class="sxs-lookup"><span data-stu-id="10961-348">Native mode to SharePoint Mode -'bi' site collection</span></span>  
 <span data-ttu-id="10961-349">다음 예제에서는 기본 모드 서버에서 "sites/bi"의 사이트 모음 및 공유 문서 라이브러리가 포함된 SharePoint 서버로 콘텐츠를 마이그레이션합니다.</span><span class="sxs-lookup"><span data-stu-id="10961-349">The following example migrates content from a native mode server to a SharePoint server that contains a site collection of "sites/bi" and a shared documents library.</span></span> <span data-ttu-id="10961-350">스크립트는 문서 및 대상 라이브러리에 폴더를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="10961-350">The script creates folders in document the destination library.</span></span> <span data-ttu-id="10961-351">예를 들어 스크립트는 대상 문서 라이브러리에서 "보고서" 및 "데이터 원본" 폴더를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="10961-351">For example, the script will create a "Reports" and "Data Sources" folders in the target document library.</span></span>  
  
```cmd
rs.exe -i ssrs_migration.rss -e Mgmt2010 -s http://SourceServer/ReportServer -u Domain\User -p Password -v ts="http://TargetServer/sites/bi/_vti_bin/reportserver" -v tst="sites/bi" -v tf="Shared Documents" -v tu="Domain\User" -v tp="Password"  
```  
  
###  <a name="sharepoint-mode-to-sharepoint-mode--bi-site-collection"></a><a name="bkmk_sharepoint_2_sharepoint"></a> <span data-ttu-id="10961-352">SharePoint 모드에서 SharePoint 모드로 - ‘bi’ 사이트 컬렉션</span><span class="sxs-lookup"><span data-stu-id="10961-352">SharePoint Mode to SharePoint Mode -'bi' site collection</span></span>  
 <span data-ttu-id="10961-353">다음 예제는 다음과 같이 콘텐츠를 마이그레이션합니다.</span><span class="sxs-lookup"><span data-stu-id="10961-353">The following example migrates content:</span></span>  
  
-   <span data-ttu-id="10961-354">"sites/bi" 사이트 모음 및 공유 문서 라이브러리가 포함된 SharePoint 서버 **SourceServer** 에서</span><span class="sxs-lookup"><span data-stu-id="10961-354">From a SharePoint server **SourceServer** that contains a site collection of "sites/bi" and a shared documents library.</span></span>  
  
-   <span data-ttu-id="10961-355">"sites/bi"의 사이트 모음 및 공유 문서 라이브러리가 포함된 **TargetServer** SharePoint 서버로</span><span class="sxs-lookup"><span data-stu-id="10961-355">To a **TargetServer** SharePoint server that contains a site collection of "sites/bi" and a shared documents library.</span></span>  
  
```cmd
rs.exe -i ssrs_migration.rss -e Mgmt2010 -s http://SourceServer/_vti_bin/reportserver -v st="sites/bi" -v f="Shared Documents" -u Domain\User1 -p Password -v ts="http://TargetServer/sites/bi/_vti_bin/reportserver" -v tst="sites/bi" -v tf="Shared Documents" -v tu="Domain\User" -v tp="Password"  
```  
  
###  <a name="native-mode-to-native-mode---azure-virtual-machine"></a><a name="bkmk_native_to_native_Azure_vm"></a><span data-ttu-id="10961-356">기본 모드에서 기본 모드로-Azure 가상 컴퓨터</span><span class="sxs-lookup"><span data-stu-id="10961-356">Native Mode to Native Mode - Azure Virtual Machine</span></span>  
 <span data-ttu-id="10961-357">다음 예제는 다음과 같이 콘텐츠를 마이그레이션합니다.</span><span class="sxs-lookup"><span data-stu-id="10961-357">The following example migrates content:</span></span>  
  
-   <span data-ttu-id="10961-358">기본 모드 보고서 서버 **SourceServer**에서</span><span class="sxs-lookup"><span data-stu-id="10961-358">From a Native mode report server **SourceServer**.</span></span>  
  
-   <span data-ttu-id="10961-359">Azure 가상 머신에서 실행 중인 **TargetServer** 기본 모드 보고서 서버로</span><span class="sxs-lookup"><span data-stu-id="10961-359">To a **TargetServer** Native mode report server running on an Azure virtual machine.</span></span> <span data-ttu-id="10961-360">**TargetServer** 는 **sourceerver** 의 도메인에 가입 되지 않으며, u s e r 2는 Azure virtual machine **TargetServer**의 **관리자입니다.**</span><span class="sxs-lookup"><span data-stu-id="10961-360">The **TargetServer** is not joined to the domain of the **SourceServer** and the **User2** is an administrator on the Azure virtual machine **TargetServer**.</span></span>  
  
```cmd
rs.exe -i ssrs_migration.rss -e Mgmt2010 -s http://SourceServer/ReportServer -u Domain\user1 -p Password -v ts="http://ssrsnativeazure.cloudapp.net/ReportServer" -v tu="user2" -v tp="Password2"  
```  
  
> [!TIP]  
>  <span data-ttu-id="10961-361">Azure 가상 머신에서 Windows PowerShell을 사용해서 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 보고서 서버를 만드는 방법에 대한 자세한 내용은 [PowerShell을 사용해서 기본 모드 보고서 서버로 Azure VM 만들기](https://msdn.microsoft.com/library/dn449661.aspx)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="10961-361">For information on how to use Windows PowerShell to create [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] report servers on Azure virtual machines, see [Use PowerShell to Create an Azure VM With a Native Mode Report Server](https://msdn.microsoft.com/library/dn449661.aspx).</span></span>  
  
##  <a name="sharepoint-mode--bi-site-collection-to-a-native-mode-server-on-azure-virtual-machine"></a><a name="bkmk_sharepoint_site_to_native_Azure_vm"></a><span data-ttu-id="10961-362">SharePoint 모드-Azure 가상 컴퓨터의 기본 모드 서버에 대 한 ' bi ' 사이트 모음</span><span class="sxs-lookup"><span data-stu-id="10961-362">SharePoint Mode -'bi' site collection to a Native Mode Server on Azure Virtual Machine</span></span>  
 <span data-ttu-id="10961-363">다음 예제는 다음과 같이 콘텐츠를 마이그레이션합니다.</span><span class="sxs-lookup"><span data-stu-id="10961-363">The following example migrates content:</span></span>  
  
-   <span data-ttu-id="10961-364">"sites/bi" 사이트 모음 및 공유 라이브러리가 포함된 SharePoint 모드 보고서 서버 **SourceServer** 에서</span><span class="sxs-lookup"><span data-stu-id="10961-364">From a SharePoint mode report server **SourceServer** that contains a site collection of "sites/bi" and a shared documents library.</span></span>  
  
-   <span data-ttu-id="10961-365">Azure 가상 머신에서 실행 중인 **TargetServer** 기본 모드 보고서 서버로</span><span class="sxs-lookup"><span data-stu-id="10961-365">To a **TargetServer** Native mode report server running on an Azure virtual machine.</span></span> <span data-ttu-id="10961-366">**TargetServer** 는 **sourceerver** 의 도메인에 가입 되지 않으며, u s e r 2는 Azure virtual machine **TargetServer**의 **관리자입니다.**</span><span class="sxs-lookup"><span data-stu-id="10961-366">The **TargetServer** is not joined to the domain of the **SourceServer** and the **User2** is an administrator on the Azure virtual machine **TargetServer**.</span></span>  
  
```cmd
rs.exe -i ssrs_migration.rss -e Mgmt2010 -s http://uetesta02/_vti_bin/reportserver -u user1 -p Password -v ts="http://ssrsnativeazure.cloudapp.net/ReportServer" -v tu="user2" -v tp="Passowrd2"  
```  
  
##  <a name="verification"></a><a name="bkmk_verification"></a><span data-ttu-id="10961-367">확인할</span><span class="sxs-lookup"><span data-stu-id="10961-367">Verification</span></span>  
 <span data-ttu-id="10961-368">이 섹션에서는 콘텐츠 및 정책이 마이그레이션되었는지 확인하기 위해 대상 서버에서 수행할 몇 가지 단계를 요약해서 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="10961-368">The section summarizes some of the steps to take on the destination server to verify content and policies were successfully migrated.</span></span>  
  
### <a name="schedules"></a><span data-ttu-id="10961-369">일정</span><span class="sxs-lookup"><span data-stu-id="10961-369">Schedules</span></span>  
 <span data-ttu-id="10961-370">대상 서버의 일정을 확인하려면</span><span class="sxs-lookup"><span data-stu-id="10961-370">To verify schedules on the target server:</span></span>  
  
 <span data-ttu-id="10961-371">**기본 모드**</span><span class="sxs-lookup"><span data-stu-id="10961-371">**Native Mode**</span></span>  
  
1.  <span data-ttu-id="10961-372">대상 서버에서 보고서 관리자를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="10961-372">Browse to Report Manager on the destination server.</span></span>  
  
2.  <span data-ttu-id="10961-373">최상위 메뉴에서 **사이트 설정** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="10961-373">Click **Site Settings** on the top menu.</span></span>  
  
3.  <span data-ttu-id="10961-374">왼쪽 창에서 **일정** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="10961-374">Click **Schedules** in the left pane.</span></span>  
  
 <span data-ttu-id="10961-375">**SharePoint 모드:**</span><span class="sxs-lookup"><span data-stu-id="10961-375">**SharePoint Mode:**</span></span>  
  
1.  <span data-ttu-id="10961-376">**사이트 설정**으로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="10961-376">Browse to **Site settings**.</span></span>  
  
2.  <span data-ttu-id="10961-377">**Reporting Services** 그룹에서 **공유 일정 관리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="10961-377">In the **Reporting Services** group, click **Manage Shared Schedules**.</span></span>  
  
### <a name="roles-and-groups"></a><span data-ttu-id="10961-378">역할 및 그룹</span><span class="sxs-lookup"><span data-stu-id="10961-378">Roles and Groups</span></span>  
 <span data-ttu-id="10961-379">**기본 모드**</span><span class="sxs-lookup"><span data-stu-id="10961-379">**Native Mode**</span></span>  
  
1.  <span data-ttu-id="10961-380">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 를 열고 기본 모드 보고서 서버에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="10961-380">Open [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] and connect to your native mode report server.</span></span>  
  
2.  <span data-ttu-id="10961-381">**개체 탐색기** **보안**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="10961-381">In **Object Explorer** click **Security**.</span></span>  
  
3.  <span data-ttu-id="10961-382">**역할**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="10961-382">Click **Roles**.</span></span>  
  
##  <a name="troubleshooting"></a><a name="bkmk_troubleshoot"></a> <span data-ttu-id="10961-383">문제 해결</span><span class="sxs-lookup"><span data-stu-id="10961-383">Troubleshooting</span></span>  
 <span data-ttu-id="10961-384">추적 플래그 **–t**를 사용해서 추가 정보를 받습니다.</span><span class="sxs-lookup"><span data-stu-id="10961-384">Use the trace flag **-t** to receive more information.</span></span> <span data-ttu-id="10961-385">예를 들어 스크립트를 실행하면 다음과 비슷한 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="10961-385">For example, if you run the script and see a message similar to the following</span></span>  
  
-   <span data-ttu-id="10961-386">서버에 연결할 수 없습니다. http:// \<servername> /Reportserver/reportservice2010.asmx</span><span class="sxs-lookup"><span data-stu-id="10961-386">Could not connect to server: http://\<servername>/ReportServer/ReportService2010.asmx</span></span>  
  
 <span data-ttu-id="10961-387">**-T** 플래그를 사용 하 여 스크립트를 다시 실행 하면 다음과 비슷한 메시지가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="10961-387">Run the script again with the **-t** flag, to see a message similar to the following:</span></span>  
  
-   <span data-ttu-id="10961-388">Http://: 서버에 연결할 수 없습니다. 예외: 서버에 연결할 수 없습니다. \<servername> >---10.WebException:: **http 상태 401: 권한이 없어 요청이 실패 했습니다**.</span><span class="sxs-lookup"><span data-stu-id="10961-388">System.Exception: Could not connect to server: http://\<servername>/ReportServer/ReportService2010.asmx ---> System.Net.WebException: **The request failed with HTTP status 401: Unauthorized**.</span></span>   <span data-ttu-id="10961-389">at System.Web.Services.Protocols.SoapHttpClientProtocol.ReadResponse (SoapClientMessage message, WebResponse response, Stream responseStream, Boolean asyncCall) at System.Web.Services.Protocols.SoapHttpClientProtocol.Invoke (String methodName, Object parameters) at Microsoft.sqlserver.reportingservices2010.reportingservice2010.issslrequired at Microsoft.ReportingServices.ScriptHost.Management2010Endpoint.PingService (String url, String userName, String password String domain, Int32 timeout) at Microsoft.reportingservices.scripthost.scripthost.determineserverurlsecurity---내부 예외 스택 추적 끝--</span><span class="sxs-lookup"><span data-stu-id="10961-389">at System.Web.Services.Protocols.SoapHttpClientProtocol.ReadResponse(SoapClientMessage message, WebResponse response, Stream responseStream, Boolean asyncCall)   at System.Web.Services.Protocols.SoapHttpClientProtocol.Invoke(String methodName, Object[] parameters)   at Microsoft.SqlServer.ReportingServices2010.ReportingService2010.IsSSLRequired()   at Microsoft.ReportingServices.ScriptHost.Management2010Endpoint.PingService(String url, String userName, String password, String domain, Int32 timeout)   at Microsoft.ReportingServices.ScriptHost.ScriptHost.DetermineServerUrlSecurity()   --- End of inner exception stack trace ---</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10961-390">참고 항목</span><span class="sxs-lookup"><span data-stu-id="10961-390">See Also</span></span>  
 <span data-ttu-id="10961-391">[RS.exe 유틸리티 &#40;SSRS&#41;](rs-exe-utility-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="10961-391">[RS.exe Utility &#40;SSRS&#41;](rs-exe-utility-ssrs.md) </span></span>  
 [<span data-ttu-id="10961-392">Reporting Services의 역할 및 태스크와 SharePoint 그룹 및 사용 권한 비교</span><span class="sxs-lookup"><span data-stu-id="10961-392">Compare Roles and Tasks in Reporting Services to SharePoint Groups and Permissions</span></span>](../reporting-services-roles-tasks-vs-sharepoint-groups-permissions.md)  
