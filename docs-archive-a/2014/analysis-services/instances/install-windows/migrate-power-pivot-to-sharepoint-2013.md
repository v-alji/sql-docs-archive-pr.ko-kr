---
title: PowerPivot을 SharePoint 2013로 마이그레이션 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: f698ceb1-d53e-4717-a3a0-225b346760d0
author: minewiskan
ms.author: owend
ms.openlocfilehash: 1e59c6d6553cc9c43155b059fedf4eb6e124ca55
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87729919"
---
# <a name="migrate-powerpivot-to-sharepoint-2013"></a><span data-ttu-id="7cd4d-102">Migrate PowerPivot to SharePoint 2013</span><span class="sxs-lookup"><span data-stu-id="7cd4d-102">Migrate PowerPivot to SharePoint 2013</span></span>


 <span data-ttu-id="7cd4d-103">SharePoint 2013에서는 전체 업그레이드를 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7cd4d-103">SharePoint 2013 does not support in-place upgrade.</span></span> <span data-ttu-id="7cd4d-104">그러나 **데이터베이스 연결 업그레이드 절차는 지원 됩니다**.</span><span class="sxs-lookup"><span data-stu-id="7cd4d-104">However the procedure of **database-attach upgrade is supported**.</span></span> <span data-ttu-id="7cd4d-105">동작은 전체 업그레이드 및 데이터베이스 연결 업그레이드의 두 가지 기본 업그레이드 방법 중 고객이 선택할 수 있는 SharePoint 2010으로 업그레이드와 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="7cd4d-105">The behavior is different from upgrading to SharePoint 2010, where a customer could choose between the two basic upgrade approaches, in-place upgrade and database-attach upgrade.</span></span>

 <span data-ttu-id="7cd4d-106">[!INCLUDE[ssGeminiShort](../../../includes/ssgeminishort-md.md)] 설치가 SharePoint 2010에 통합되어 있는 경우에는 SharePoint 서버를 전체 업그레이드할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7cd4d-106">If you have a [!INCLUDE[ssGeminiShort](../../../includes/ssgeminishort-md.md)] installation integrated with SharePoint 2010, you cannot upgrade in-place the SharePoint server.</span></span> <span data-ttu-id="7cd4d-107">그러나 SharePoint 2010 팜에서 콘텐츠 데이터베이스 및 서비스 애플리케이션 데이터베이스를 SharePoint 2013 팜으로 마이그레이션할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7cd4d-107">However you can migrate content databases and service application databases from the SharePoint 2010 farm to a SharePoint 2013 farm.</span></span> <span data-ttu-id="7cd4d-108">이 항목은 데이터베이스 연결 업그레이드를 완료하고 PowerPivot 관련 마이그레이션을 완료하는 데 필요한 단계에 대한 개요입니다.</span><span class="sxs-lookup"><span data-stu-id="7cd4d-108">This topic is an overview of the steps required to complete a database-attach upgrade and complete a migration related to PowerPivot:</span></span>

 <span data-ttu-id="7cd4d-109">**[!INCLUDE[applies](../../../includes/applies-md.md)]** SharePoint 2013</span><span class="sxs-lookup"><span data-stu-id="7cd4d-109">**[!INCLUDE[applies](../../../includes/applies-md.md)]**  SharePoint 2013</span></span>

### <a name="migration-overview"></a><span data-ttu-id="7cd4d-110">마이그레이션 개요</span><span class="sxs-lookup"><span data-stu-id="7cd4d-110">Migration Overview</span></span>

|<span data-ttu-id="7cd4d-111">1</span><span class="sxs-lookup"><span data-stu-id="7cd4d-111">1</span></span>|<span data-ttu-id="7cd4d-112">2</span><span class="sxs-lookup"><span data-stu-id="7cd4d-112">2</span></span>|<span data-ttu-id="7cd4d-113">3</span><span class="sxs-lookup"><span data-stu-id="7cd4d-113">3</span></span>|<span data-ttu-id="7cd4d-114">4</span><span class="sxs-lookup"><span data-stu-id="7cd4d-114">4</span></span>|
|-------|-------|-------|-------|
|<span data-ttu-id="7cd4d-115">SharePoint 2013 팜 준비</span><span class="sxs-lookup"><span data-stu-id="7cd4d-115">Prepare the SharePoint 2013 farm</span></span>|<span data-ttu-id="7cd4d-116">데이터베이스 백업, 복사 및 복원</span><span class="sxs-lookup"><span data-stu-id="7cd4d-116">Backup, copy, restore databases.</span></span>|<span data-ttu-id="7cd4d-117">콘텐츠 데이터베이스 탑재</span><span class="sxs-lookup"><span data-stu-id="7cd4d-117">Mount content databases</span></span>|<span data-ttu-id="7cd4d-118">[!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] 일정 마이그레이션</span><span class="sxs-lookup"><span data-stu-id="7cd4d-118">Migrate [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] Schedules</span></span>|
||[!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]|<span data-ttu-id="7cd4d-119">SharePoint 중앙 관리</span><span class="sxs-lookup"><span data-stu-id="7cd4d-119">SharePoint Central Administration</span></span><br /><br /> <span data-ttu-id="7cd4d-120">Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="7cd4d-120">Windows PowerShell</span></span>|<span data-ttu-id="7cd4d-121">SharePoint 애플리케이션 페이지</span><span class="sxs-lookup"><span data-stu-id="7cd4d-121">SharePoint application Pages</span></span><br /><br /> <span data-ttu-id="7cd4d-122">Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="7cd4d-122">Windows PowerShell</span></span>|

 <span data-ttu-id="7cd4d-123">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="7cd4d-123">**In this topic:**</span></span>

-   [<span data-ttu-id="7cd4d-124">1) SharePoint 2013 팜 준비</span><span class="sxs-lookup"><span data-stu-id="7cd4d-124">1) Prepare the SharePoint 2013 Farm</span></span>](#bkmk_prepare_sharepoint2013)

-   [<span data-ttu-id="7cd4d-125">2) 데이터베이스 백업, 복사 및 복원</span><span class="sxs-lookup"><span data-stu-id="7cd4d-125">2) Backup, Copy, Restore the Databases</span></span>](#bkmk_backup_restore)

-   [<span data-ttu-id="7cd4d-126">3) 웹 애플리케이션 준비 및 콘텐츠 데이터베이스 탑재</span><span class="sxs-lookup"><span data-stu-id="7cd4d-126">3) Prepare Web Applications and Mount Content Databases</span></span>](#bkmk_prepare_mount_databases)

-   [<span data-ttu-id="7cd4d-127">4) PowerPivot 일정 업그레이드</span><span class="sxs-lookup"><span data-stu-id="7cd4d-127">4) Upgrade PowerPivot Schedules</span></span>](#bkmk_upgrade_powerpivot_schedules)

-   [<span data-ttu-id="7cd4d-128">추가 리소스</span><span class="sxs-lookup"><span data-stu-id="7cd4d-128">Additional Resources</span></span>](#bkmk_additional_resources)

##  <a name="1-prepare-the-sharepoint-2013-farm"></a><a name="bkmk_prepare_sharepoint2013"></a><span data-ttu-id="7cd4d-129">1) SharePoint 2013 팜 준비</span><span class="sxs-lookup"><span data-stu-id="7cd4d-129">1) Prepare the SharePoint 2013 Farm</span></span>

1.  > [!TIP]
    >  <span data-ttu-id="7cd4d-130">기존 웹 애플리케이션을 구성한 인증 방법을 검토하세요.</span><span class="sxs-lookup"><span data-stu-id="7cd4d-130">Review the authentication method your existing web applications are configured for.</span></span> <span data-ttu-id="7cd4d-131">SharePoint 2013 웹 애플리케이션은 클레임 기반 인증을 기본적으로 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="7cd4d-131">SharePoint 2013 web applications default to claims-based authentication.</span></span> <span data-ttu-id="7cd4d-132">클래식 모드 인증에 대해 구성된 SharePoint 2010 웹 애플리케이션을 사용하려면 SharePoint 2010에서 SharePoint 2013으로 데이터베이스를 마이그레이션하는 추가 단계가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="7cd4d-132">SharePoint 2010 web applications configured for classic-mode authentication require additional steps to migrate databases from SharePoint 2010 to SharePoint 2013.</span></span> <span data-ttu-id="7cd4d-133">클래식 모드 인증에 대해 웹 애플리케이션이 구성된 경우 SharePoint 2013 설명서를 검토합니다.</span><span class="sxs-lookup"><span data-stu-id="7cd4d-133">If your web applications are configured for classic-mode authentication, review the SharePoint 2013 documentation.</span></span>

2.  <span data-ttu-id="7cd4d-134">새로 SharePoint Server 2013 팜을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="7cd4d-134">Install a new SharePoint Server 2013 farm.</span></span>

3.  <span data-ttu-id="7cd4d-135">[!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] SharePoint 모드에서 서버 인스턴스를 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="7cd4d-135">Install an instance of a [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] server in SharePoint mode.</span></span> <span data-ttu-id="7cd4d-136">자세한 내용은 [PowerPivot for SharePoint 2013 Installation](https://docs.microsoft.com/analysis-services/instances/install-windows/install-analysis-services-in-power-pivot-mode)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7cd4d-136">For more information, see [PowerPivot for SharePoint 2013 Installation](https://docs.microsoft.com/analysis-services/instances/install-windows/install-analysis-services-in-power-pivot-mode).</span></span>

4.  <span data-ttu-id="7cd4d-137">SharePoint 팜의 각 서버에서 [!INCLUDE[ssGeminiShort](../../../includes/ssgeminishort-md.md)] 2013 설치 패키지 **spPowerPivot.msi** 를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="7cd4d-137">Run the [!INCLUDE[ssGeminiShort](../../../includes/ssgeminishort-md.md)] 2013 installation package **spPowerPivot.msi** on each server in the SharePoint farm.</span></span> <span data-ttu-id="7cd4d-138">자세한 내용은 [SharePoint 2013&#41;&#40;SharePoint용 PowerPivot 추가 기능 설치 또는 제거 ](https://docs.microsoft.com/analysis-services/instances/install-windows/install-or-uninstall-the-power-pivot-for-sharepoint-add-in-sharepoint-2013)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="7cd4d-138">For more information, see [Install or Uninstall the PowerPivot for SharePoint Add-in &#40;SharePoint 2013&#41;](https://docs.microsoft.com/analysis-services/instances/install-windows/install-or-uninstall-the-power-pivot-for-sharepoint-add-in-sharepoint-2013).</span></span>

5.  <span data-ttu-id="7cd4d-139">SharePoint 2013 중앙 관리에서 이전 단계에서 만든 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] SharePoint 모드 서버를 사용하도록 Excel Services 서비스 애플리케이션을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="7cd4d-139">In SharePoint 2013 Central Administration, configure the Excel Services service application to use the [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] SharePoint mode server created in the previous step.</span></span> <span data-ttu-id="7cd4d-140">자세한 내용은 [SharePoint용 PowerPivot 2013 설치](https://docs.microsoft.com/analysis-services/instances/install-windows/install-analysis-services-in-power-pivot-mode)의 "기본 Analysis Services SharePoint 통합 구성" 섹션을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="7cd4d-140">For more information, see the "Configure Basic Analysis Services SharePoint Integration" section of [PowerPivot for SharePoint 2013 Installation](https://docs.microsoft.com/analysis-services/instances/install-windows/install-analysis-services-in-power-pivot-mode).</span></span>

##  <a name="2-backup-copy-restore-the-databases"></a><a name="bkmk_backup_restore"></a><span data-ttu-id="7cd4d-141">2) 데이터베이스 백업, 복사, 복원</span><span class="sxs-lookup"><span data-stu-id="7cd4d-141">2) Backup, Copy, Restore the Databases</span></span>
 <span data-ttu-id="7cd4d-142">"SharePoint 데이터베이스 연결 업그레이드" 프로세스는 PowerPivot 관련 콘텐츠 및 서비스 응용 프로그램 데이터베이스를 SharePoint 2013 팜에 백업, 복사 및 복원 하는 일련의 단계입니다.</span><span class="sxs-lookup"><span data-stu-id="7cd4d-142">The "SharePoint database-attach upgrade" process is a sequence of steps to back up, copy, and restore PowerPivot related content and service application databases to the SharePoint 2013 farm.</span></span>

1.  <span data-ttu-id="7cd4d-143">**데이터베이스를 읽기 전용으로 설정:**[!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]에서 데이터베이스 이름을 마우스 오른쪽 단추로 클릭하고 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7cd4d-143">**Set Database to read-only:** In [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], right-click the database name and click **Properties**.</span></span> <span data-ttu-id="7cd4d-144">**옵션** 페이지에서 **데이터베이스 읽기 전용** 속성을 **True**로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="7cd4d-144">On the **Options** page, set the **Database read-Only** property to **True**.</span></span>

2.  <span data-ttu-id="7cd4d-145">**백업:** SharePoint 2013 팜에 마이그레이션할 각 콘텐츠 데이터베이스 및 서비스 애플리케이션 데이터베이스를 백업합니다.</span><span class="sxs-lookup"><span data-stu-id="7cd4d-145">**Back up:** Back up each content database and service application database that you want to migrate to the SharePoint 2013 farm.</span></span> <span data-ttu-id="7cd4d-146">[!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]에서 데이터베이스를 마우스 오른쪽 단추로 클릭하고 **태스크**를 클릭한 다음 **백업**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7cd4d-146">In [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], right-click the database name, click **Tasks**, and click **Back up**.</span></span>

3.  <span data-ttu-id="7cd4d-147">원하는 대상 서버에 데이터베이스 백업 파일(.bak)을 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="7cd4d-147">File copy the database backup files (.bak) to the desired destination server.</span></span>

4.  <span data-ttu-id="7cd4d-148">**복원:** 대상 [!INCLUDE[ssDEnoversion](../../../includes/ssdenoversion-md.md)]에 데이터베이스를 복원합니다.</span><span class="sxs-lookup"><span data-stu-id="7cd4d-148">**Restore:** Restore the databases to the destination [!INCLUDE[ssDEnoversion](../../../includes/ssdenoversion-md.md)].</span></span> <span data-ttu-id="7cd4d-149">이 단계는 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]를 사용하여 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7cd4d-149">This step can be completed using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)].</span></span>

5.  <span data-ttu-id="7cd4d-150">**데이터베이스를 읽기/쓰기로 설정:\*\*\*\*데이터베이스가 읽기 전용** 을 **False**로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="7cd4d-150">**Set Database to read-write:** Set the **Database read-Only** to **False**.</span></span>

##  <a name="3-prepare-web-applications-and-mount-content-databases"></a><a name="bkmk_prepare_mount_databases"></a><span data-ttu-id="7cd4d-151">3) 웹 응용 프로그램 준비 및 콘텐츠 데이터베이스 탑재</span><span class="sxs-lookup"><span data-stu-id="7cd4d-151">3) Prepare Web Applications and Mount Content Databases</span></span>
 <span data-ttu-id="7cd4d-152">다음 절차에 대 한 자세한 설명은 [sharepoint 2010에서 sharepoint 2013으로 데이터베이스 업그레이드](https://go.microsoft.com/fwlink/p/?LinkId=256690) ()를 참조 하세요 https://go.microsoft.com/fwlink/p/?LinkId=256690) .</span><span class="sxs-lookup"><span data-stu-id="7cd4d-152">For a more detailed explanation of the following procedures, see [Upgrade databases from SharePoint 2010 to SharePoint 2013](https://go.microsoft.com/fwlink/p/?LinkId=256690) (https://go.microsoft.com/fwlink/p/?LinkId=256690).</span></span>

1.  <span data-ttu-id="7cd4d-153">**데이터베이스를 오프라인 상태로 만들기:**</span><span class="sxs-lookup"><span data-stu-id="7cd4d-153">**Take Databases Offline:**</span></span>

     <span data-ttu-id="7cd4d-154">각 SharePoint 2013 콘텐츠 데이터베이스를 오프라인 상태로 만들려면 SharePoint 중앙 관리를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="7cd4d-154">Take each SharePoint 2013 content database offline, using SharePoint Central Administration.</span></span> <span data-ttu-id="7cd4d-155">콘텐츠 데이터베이스는 복사한 데이터베이스로 대체됩니다.</span><span class="sxs-lookup"><span data-stu-id="7cd4d-155">The content databases are replaced by the databases you copied over.</span></span> <span data-ttu-id="7cd4d-156">환경에 가장 적합한 순서를 고려하세요.</span><span class="sxs-lookup"><span data-stu-id="7cd4d-156">Consider what is the best sequence for your environment.</span></span> <span data-ttu-id="7cd4d-157">각 데이터베이스를 오프라인 상태로 만들고 다음 콘텐츠 데이터베이스를 오프라인 상태로 만들기 전에 관련 교체 데이터베이스를 탑재합니다.</span><span class="sxs-lookup"><span data-stu-id="7cd4d-157">Consider taking each database offline and mount its relevant replacement database before taking the next content database offline.</span></span> <span data-ttu-id="7cd4d-158">다른 옵션은 모든 콘텐츠 데이터베이스를 그룹으로 오프라인 상태로 만드는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="7cd4d-158">Another option is to take all the content databases offline as a group.</span></span>

    1.  <span data-ttu-id="7cd4d-159">SharePoint 중앙 관리에서 **애플리케이션 관리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7cd4d-159">In SharePoint Central Administration, click **Application Management**.</span></span>

    2.  <span data-ttu-id="7cd4d-160">**콘텐츠 데이터베이스 관리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7cd4d-160">Click **Manage Content Databases**.</span></span>

    3.  <span data-ttu-id="7cd4d-161">데이터베이스 이름을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7cd4d-161">Click the name of the database.</span></span>

    4.  <span data-ttu-id="7cd4d-162">**콘텐츠 데이터베이스 설정 관리**에서 **데이터베이스 상태** 를 **오프라인**으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="7cd4d-162">On the **Manage Content Database Settings**, set **Database status** to **Offline**.</span></span>

    5.  <span data-ttu-id="7cd4d-163">**콘텐츠 데이터베이스 제거**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="7cd4d-163">Select **Remove Content Database**.</span></span> <span data-ttu-id="7cd4d-164">콘텐츠 데이터베이스에 저장된 사이트에 더 이상 액세스할 수 없다는 경고가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="7cd4d-164">Note the warning that sites stored in the content database will no longer be accessible.</span></span>

-   <span data-ttu-id="7cd4d-165">**콘텐츠 데이터베이스 탑재:**</span><span class="sxs-lookup"><span data-stu-id="7cd4d-165">**Mount content databases:**</span></span>

     <span data-ttu-id="7cd4d-166">SharePoint 2013 관리 셸에서 PowerShell cmdlet을 사용하여 마이그레이션된 콘텐츠 데이터베이스를 탑재합니다.</span><span class="sxs-lookup"><span data-stu-id="7cd4d-166">Use PowerShell cmdlets in the SharePoint 2013 Management shell to mount the migrated content database.</span></span> <span data-ttu-id="7cd4d-167">서비스 응용 프로그램 데이터베이스는 탑재 하지 않아도 되며, 콘텐츠 데이터베이스만 ![PowerShell 관련 콘텐츠](../../../reporting-services/media/rs-powershellicon.jpg "PowerShell 관련 콘텐츠") 입니다.</span><span class="sxs-lookup"><span data-stu-id="7cd4d-167">The service application database does not need to be mounted, only the content databases: ![PowerShell related content](../../../reporting-services/media/rs-powershellicon.jpg "PowerShell related content")</span></span>

    ```powershell
    Mount-SPContentDatabase "SharePoint_Content_O14-KJSP1" -DatabaseServer "[server name]\powerpivot" -WebApplication [web application URL]
    ```

     <span data-ttu-id="7cd4d-168">자세한 내용은 [콘텐츠 데이터베이스 연결 또는 분리 (SharePoint Server 2010) ()](https://technet.microsoft.com/library/ff628582.aspx) 를 참조 하세요 https://technet.microsoft.com/library/ff628582.aspx) .</span><span class="sxs-lookup"><span data-stu-id="7cd4d-168">For more information, see [Attach or detach content databases (SharePoint Server 2010)](https://technet.microsoft.com/library/ff628582.aspx) (https://technet.microsoft.com/library/ff628582.aspx).</span></span>

     <span data-ttu-id="7cd4d-169">**단계가 완료된 상태:**  탑재 작업이 완료되면 사용자가 이전 콘텐츠 데이터베이스에 있는 파일을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7cd4d-169">**Status when the step is complete:**  When the mount operation is complete, users can see files that were in the old content database.</span></span> <span data-ttu-id="7cd4d-170">따라서 사용자는 문서 라이브러리에서 통합 문서를 보고 열 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7cd4d-170">Therefore users can see and open the workbooks in the document library.</span></span>

    > [!TIP]
    >  <span data-ttu-id="7cd4d-171">마이그레이션 프로세스의 이 시점에서 마이그레이션된 통합 문서에 대한 새 일정을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7cd4d-171">It is possible at this point in the migration process to create new schedules for the migrated workbooks.</span></span> <span data-ttu-id="7cd4d-172">하지만 일정은 새 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] 서비스 애플리케이션 데이터베이스에서 만들어지고 기존 SharePoint 팜에서 복사한 데이터베이스에는 만들어지지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7cd4d-172">However, the schedules are created in the new [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] service application database, and not the database you copied from the old SharePoint farm.</span></span> <span data-ttu-id="7cd4d-173">따라서 새 일정에는 기존 일정이 포함되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7cd4d-173">Therefore it will not contain any of the old schedules.</span></span> <span data-ttu-id="7cd4d-174">다음 단계를 완료하여 기존 데이터베이스를 사용하고 기존 일정을 마이그레이션한 후에는 새 일정을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7cd4d-174">After you complete the following steps to use the old database and migrate the old schedules, the new schedules are not available.</span></span>

### <a name="troubleshoot-issues-when-you-attempt-to-mount-databases"></a><span data-ttu-id="7cd4d-175">데이터베이스 탑재 시 발생하는 문제 해결</span><span class="sxs-lookup"><span data-stu-id="7cd4d-175">Troubleshoot issues when you attempt to mount databases</span></span>
 <span data-ttu-id="7cd4d-176">이 섹션에서는 데이터베이스를 탑재할 때 발생할 수 있는 문제를 요약합니다.</span><span class="sxs-lookup"><span data-stu-id="7cd4d-176">This section summarizes possible issues encountered when mounting the database.</span></span>

1.  <span data-ttu-id="7cd4d-177">**인증 오류:** 인증 관련 오류가 표시되면 소스 웹 애플리케이션에서 사용하는 인증 모드를 검토합니다.</span><span class="sxs-lookup"><span data-stu-id="7cd4d-177">**Authentication errors:** If you see errors related to authentication, review what authentication mode the source web applications are using.</span></span> <span data-ttu-id="7cd4d-178">이 오류는 SharePoint 2013 웹 애플리케이션과 SharePoint 2010 웹 애플리케이션 간의 인증 불일치로 인해 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7cd4d-178">The error could be caused by a mismatch in authentication between the SharePoint 2013 web application and the SharePoint 2010 web application.</span></span> <span data-ttu-id="7cd4d-179">자세한 내용은 [1) SharePoint 2013 팜 준비](#bkmk_prepare_sharepoint2013) 를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7cd4d-179">See the [1) Prepare the SharePoint 2013 Farm](#bkmk_prepare_sharepoint2013) for more information.</span></span>

2.  <span data-ttu-id="7cd4d-180">**PowerPivot 파일 누락:** PowerPivot.dll 누락 관련 오류가 표시되면 **spPowerPivot.msi** 가 설치되지 않았거나 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] 구성 도구를 사용하여 PowerPivot을 구성하지 않은 것입니다.</span><span class="sxs-lookup"><span data-stu-id="7cd4d-180">**Missing PowerPivot.Files:** If you see errors related to missing PowerPivot .dlls, the **spPowerPivot.msi** has not been installed or the [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] Configuration Tool has not been used to configure PowerPivot.</span></span>

##  <a name="4-upgrade-powerpivot-schedules"></a><a name="bkmk_upgrade_powerpivot_schedules"></a><span data-ttu-id="7cd4d-181">4) PowerPivot 일정 업그레이드</span><span class="sxs-lookup"><span data-stu-id="7cd4d-181">4) Upgrade PowerPivot Schedules</span></span>
 <span data-ttu-id="7cd4d-182">이 섹션에서는 PowerPivot 일정 마이그레이션에 대한 세부 정보와 옵션을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="7cd4d-182">This section describes the details and options for migrating PowerPivot schedules.</span></span> <span data-ttu-id="7cd4d-183">일정 마이그레이션 프로세스는 두 단계로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="7cd4d-183">Schedule migration is a two-step process.</span></span> <span data-ttu-id="7cd4d-184">먼저 마이그레이션된 서비스 애플리케이션 데이터베이스를 사용하도록 PowerPivot 서비스 애플리케이션을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="7cd4d-184">First configure the PowerPivot service application to use the migrated service application database.</span></span> <span data-ttu-id="7cd4d-185">그런 다음, 일정 마이그레이션에 대한 두 가지 옵션 중 하나를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="7cd4d-185">Second, choose one of two options for schedule migration.</span></span>

 <span data-ttu-id="7cd4d-186">**마이그레이션된 서비스 애플리케이션 데이터베이스를 사용하도록 서비스 애플리케이션을 구성합니다.**</span><span class="sxs-lookup"><span data-stu-id="7cd4d-186">**Configure the service application to use the migrated service application database.**</span></span>

 <span data-ttu-id="7cd4d-187">SharePoint 중앙 관리에서 복사한 기존 서비스 애플리케이션 데이터베이스를 사용하도록 PowerPivot 서비스 애플리케이션을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="7cd4d-187">In SharePoint Central Administration to configure the PowerPivot services application to use the old service application database you copied over.</span></span> <span data-ttu-id="7cd4d-188">PowerPivot 서비스는 서비스 애플리케이션 데이터베이스를 새 스키마로 업그레이드합니다.</span><span class="sxs-lookup"><span data-stu-id="7cd4d-188">The PowerPivot Service upgrades the service application database to the new schema.</span></span>

1.  <span data-ttu-id="7cd4d-189">SharePoint 중앙 관리에서 **서비스 응용 프로그램 관리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7cd4d-189">In SharePoint Central Administration, click **Manage Service Applications**.</span></span>

2.  <span data-ttu-id="7cd4d-190">PowerPivot 서비스 응용 프로그램 (예: "기본 PowerPivot 서비스 응용 프로그램")을 찾고 서비스 응용 프로그램의 이름을 클릭 한 다음 SharePoint 리본에서 **속성** 을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="7cd4d-190">Find the PowerPivot service application, for example "Default PowerPivot Service Application", click the name of the service application and click **Properties** in the SharePoint ribbon.</span></span>

3.  <span data-ttu-id="7cd4d-191">데이터베이스 서버 이름-인스턴스 및 데이터베이스 이름을 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="7cd4d-191">Update the database server name-instance and the database name.</span></span> <span data-ttu-id="7cd4d-192">백업, 복사 및 복원한 데이터베이스에 대한 올바른 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="7cd4d-192">To the correct names for the database you backed up, copied, and restored.</span></span> <span data-ttu-id="7cd4d-193">**확인**을 클릭하면 서비스 애플리케이션 데이터베이스가 업그레이드됩니다.</span><span class="sxs-lookup"><span data-stu-id="7cd4d-193">Once you click **Ok**, the service application database is upgraded.</span></span> <span data-ttu-id="7cd4d-194">오류는 ULS 로그에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7cd4d-194">Errors will be in the ULS log.</span></span>

 <span data-ttu-id="7cd4d-195">**PowerPivot 일정 업그레이드**</span><span class="sxs-lookup"><span data-stu-id="7cd4d-195">**Upgrade PowerPivot schedules**</span></span>

 <span data-ttu-id="7cd4d-196">새로 고침 일정을 마이그레이션하도록 PowerPivot 서비스 애플리케이션을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="7cd4d-196">Configure the PowerPivot service application to migrate refresh schedules.</span></span>

-   <span data-ttu-id="7cd4d-197">**일정 옵션 1 마이그레이션: SharePoint 팜 관리자**</span><span class="sxs-lookup"><span data-stu-id="7cd4d-197">**Migrate Schedules option1: SharePoint farm administrator**</span></span>

    1.  <span data-ttu-id="7cd4d-198">SharePoint 2013 관리에서 `Set-PowerPivotServiceApplication` cmdlet을 스위치와 함께 실행 `-StartMigratingRefreshSchedules` 하 여 자동 주문형 일정 마이그레이션 ![PowerShell 관련 콘텐츠](../../../reporting-services/media/rs-powershellicon.jpg "PowerShell 관련 콘텐츠")를 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="7cd4d-198">In the SharePoint 2013 Management Run the `Set-PowerPivotServiceApplication` cmdlet with the `-StartMigratingRefreshSchedules` switch to enable automatic on demand schedule migration ![PowerShell related content](../../../reporting-services/media/rs-powershellicon.jpg "PowerShell related content").</span></span> <span data-ttu-id="7cd4d-199">다음 Windows PowerShell 스크립트는 PowerPivot 서비스 애플리케이션이 한 개만 있다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="7cd4d-199">The following Windows PowerShell script assumes that there is only one PowerPivot service application.</span></span>

        ```powershell
        $app = Get-PowerPivotServiceApplication
        Set-PowerPivotServiceApplication $app -StartMigratingRefreshSchedules
        ```

         <span data-ttu-id="7cd4d-200">Windows PowerShell 스크립트를 실행하면 일정이 활성화되고 일정이 적절한 다음 시간에 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="7cd4d-200">After the Windows PowerShell script is run, the schedules are active and the schedules will run at the next appropriate time.</span></span> <span data-ttu-id="7cd4d-201">하지만 일정 새로 고침 페이지 상태 1이 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7cd4d-201">However, the status one the schedule refresh page is not enabled.</span></span> <span data-ttu-id="7cd4d-202">일정이 처음 실행되면 일정이 마이그레이션되며 일정 새로 고침 페이지에서 **사용**  이 true가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7cd4d-202">When the schedule runs the first time it will be migrated and on the schedule refresh page, **Enabled**  will be true.</span></span>

    2.  <span data-ttu-id="7cd4d-203">StartMigratingRefreshSchedules 속성의 현재 값을 확인하려면 다음 PowerShell 스크립트를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="7cd4d-203">If you want to check the current value of the StartMigratingRefreshSchedules property, run the following PowerShell script.</span></span> <span data-ttu-id="7cd4d-204">스크립트는 모든 PowerPivot 서비스 애플리케이션 개체를 반복하며 이름 및 속성 값을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="7cd4d-204">The Script loops through all PowerPivot service application objects and display the name and property values:</span></span>

        ```powershell
        $apps = Get-PowerPivotServiceApplication
        foreach ($app in $apps){ Get-PowerPivotServiceApplication $app | Format-Table -Property displayname, id, StartMigratingRefreshSchedules }
        ```

     <span data-ttu-id="7cd4d-205">**일정 옵션 2 마이그레이션: 사용자가 각 통합 문서 업데이트**</span><span class="sxs-lookup"><span data-stu-id="7cd4d-205">**Migrate Schedules option2: User updates each workbook**</span></span>

    1.  <span data-ttu-id="7cd4d-206">일정을 마이그레이션하는 다른 옵션은 각 통합 문서에 대한 일정 새로 고침을 사용하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="7cd4d-206">Another option to migrate schedules is to enable the schedule refresh for each workbook.</span></span> <span data-ttu-id="7cd4d-207">통합 문서가 있는 문서 라이브러리로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="7cd4d-207">Navigate to the document library that contains the workbooks.</span></span>

    2.  <span data-ttu-id="7cd4d-208">상황에 맞는 메뉴를 열고 **PowerPivot 데이터 새로 고침 관리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7cd4d-208">Open the context menu and click **Manage PowerPivot Data Refresh**.</span></span>

    3.  <span data-ttu-id="7cd4d-209">**새로 고침 일정** 섹션에서 **사용**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7cd4d-209">In the **schedule refresh** section, click **Enable**.</span></span>

    4.  <span data-ttu-id="7cd4d-210">**가능한 빨리 새로 고치세요.** 를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7cd4d-210">You can select **Also refresh as soon as possible**.</span></span> <span data-ttu-id="7cd4d-211">이 옵션은 확인을 클릭하면 바로 새로 고침 인스턴스 한 개를 큐에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="7cd4d-211">This option adds one instance of the refresh to the queue as soon as you click ok.</span></span> <span data-ttu-id="7cd4d-212">정기적인 새로 고침 일정도 적절한 시간에 트리거됩니다.</span><span class="sxs-lookup"><span data-stu-id="7cd4d-212">The regular refresh schedule still triggers at the appropriate time.</span></span>

    5.  <span data-ttu-id="7cd4d-213">**Ok**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7cd4d-213">Click **Ok**.</span></span> <span data-ttu-id="7cd4d-214">새로 고침 기록은 이제 새로 고침 페이지에서 볼 수 있고 일정이 정상 시간에 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="7cd4d-214">The refresh history is now visible in the refresh page, the schedule will fire at the normal time.</span></span>

 <span data-ttu-id="7cd4d-215">**SQL Server 2008 R2 PowerPivot 통합 문서**</span><span class="sxs-lookup"><span data-stu-id="7cd4d-215">**SQL Server 2008 R2 PowerPivot workbooks**</span></span>

-   <span data-ttu-id="7cd4d-216">SQL Server 2008 R2 PowerPivot 통합 문서는 SQL Server 2012 SP1 SharePoint 2013용 PowerPivot에서 사용할 경우 자동으로 업그레이드되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7cd4d-216">SQL Server 2008 R2 PowerPivot workbooks do not automatically upgrade when they are used in SQL Server 2012 SP1 PowerPivot for SharePoint 2013.</span></span> <span data-ttu-id="7cd4d-217">2008 R2 통합 문서가 포함된 콘텐츠 데이터베이스를 마이그레이션한 후 통합 문서를 사용할 수 있지만 일정이 업그레이드되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7cd4d-217">After you migrate a content database containing the 2008 R2 workbooks, you can use the workbooks but the schedules do not upgrade.</span></span>

-   <span data-ttu-id="7cd4d-218">자세한 내용은 [통합 문서 업그레이드 및 예약된 데이터 새로 고침&#40;SharePoint 2013&#41;](https://docs.microsoft.com/analysis-services/instances/install-windows/upgrade-workbooks-and-scheduled-data-refresh-sharepoint-2013)을 검토하세요.</span><span class="sxs-lookup"><span data-stu-id="7cd4d-218">For more information, see [Upgrade Workbooks and Scheduled Data Refresh &#40;SharePoint 2013&#41;](https://docs.microsoft.com/analysis-services/instances/install-windows/upgrade-workbooks-and-scheduled-data-refresh-sharepoint-2013).</span></span>

##  <a name="additional-resources"></a><a name="bkmk_additional_resources"></a> <span data-ttu-id="7cd4d-219">추가 리소스</span><span class="sxs-lookup"><span data-stu-id="7cd4d-219">Additional Resources</span></span>

> [!NOTE]
>  <span data-ttu-id="7cd4d-220">[!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] 및 SharePoint 데이터베이스 연결 업그레이드에 대한 자세한 내용은 다음을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="7cd4d-220">For more information on [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] and SharePoint database-attach upgrade, see the following:</span></span>

-   <span data-ttu-id="7cd4d-221">[통합 문서 업그레이드 및 예약된 데이터 새로 고침&#40;SharePoint 2013&#41;](https://docs.microsoft.com/analysis-services/instances/install-windows/upgrade-workbooks-and-scheduled-data-refresh-sharepoint-2013).</span><span class="sxs-lookup"><span data-stu-id="7cd4d-221">[Upgrade Workbooks and Scheduled Data Refresh &#40;SharePoint 2013&#41;](https://docs.microsoft.com/analysis-services/instances/install-windows/upgrade-workbooks-and-scheduled-data-refresh-sharepoint-2013).</span></span>

-   <span data-ttu-id="7cd4d-222">[SharePoint 2013에 대 한 업그레이드 프로세스 개요](https://go.microsoft.com/fwlink/p/?LinkId=256688) ( https://go.microsoft.com/fwlink/p/?LinkId=256688) .</span><span class="sxs-lookup"><span data-stu-id="7cd4d-222">[Overview of the upgrade process to SharePoint 2013](https://go.microsoft.com/fwlink/p/?LinkId=256688) (https://go.microsoft.com/fwlink/p/?LinkId=256688).</span></span>

-   <span data-ttu-id="7cd4d-223">[SharePoint 2013로 업그레이드 하기 전에 정리 준비](https://go.microsoft.com/fwlink/p/?LinkId=256689) ( https://go.microsoft.com/fwlink/p/?LinkId=256689) .</span><span class="sxs-lookup"><span data-stu-id="7cd4d-223">[Clean up preparations before an upgrade to SharePoint 2013](https://go.microsoft.com/fwlink/p/?LinkId=256689) (https://go.microsoft.com/fwlink/p/?LinkId=256689).</span></span>

-   <span data-ttu-id="7cd4d-224">[Sharepoint 2010에서 sharepoint 2013로 데이터베이스 업그레이드](https://go.microsoft.com/fwlink/p/?LinkId=256690) ( https://go.microsoft.com/fwlink/p/?LinkId=256690) .</span><span class="sxs-lookup"><span data-stu-id="7cd4d-224">[Upgrade databases from SharePoint 2010 to SharePoint 2013](https://go.microsoft.com/fwlink/p/?LinkId=256690) (https://go.microsoft.com/fwlink/p/?LinkId=256690).</span></span>
