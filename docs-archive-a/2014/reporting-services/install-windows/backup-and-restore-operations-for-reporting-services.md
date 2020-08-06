---
title: Reporting Services 백업 및 복원 작업 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- databases [Reporting Services], backing up
- databases [Reporting Services], restoring
- databases [Reporting Services], moving
- backing up databases [Reporting Services]
- moving databases
- restoring databases [Reporting Services]
- files [Reporting Services], restoring
- files [Reporting Services], backing up
ms.assetid: 157bc376-ab72-4c99-8bde-7b12db70843a
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: e895733457fe0c8892294540bbe8345cb121f2a7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653746"
---
# <a name="backup-and-restore-operations-for-reporting-services"></a><span data-ttu-id="e00e4-102">Reporting Services 백업 및 복원 작업</span><span class="sxs-lookup"><span data-stu-id="e00e4-102">Backup and Restore Operations for Reporting Services</span></span>
  <span data-ttu-id="e00e4-103">이 항목에서는 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 설치에 사용되는 모든 데이터 파일에 대해 간략히 설명하고 이러한 파일을 백업하는 시기와 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="e00e4-103">This topic provides an overview of all data files used in a [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] installation and describes when and how you should back up the files.</span></span> <span data-ttu-id="e00e4-104">보고서 서버 데이터베이스 파일에 대한 백업 및 복원 계획을 세우는 것이 복구 전략에서 가장 중요한 부분입니다.</span><span class="sxs-lookup"><span data-stu-id="e00e4-104">Developing a backup and restore plan for the report server database files is the most important part of a recovery strategy.</span></span> <span data-ttu-id="e00e4-105">그러나 복구 전략이 복잡할수록 보고서 암호화 키, 사용자 지정 어셈블리 또는 확장 프로그램, 구성 파일, 보고서 및 모델 원본 파일 등의 백업이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="e00e4-105">However, a more comprehensive recovery strategy would include backups of the encryption keys, custom assemblies or extensions, configuration files, and source files for reports and models.</span></span>  
  
 <span data-ttu-id="e00e4-106">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 기본 모드 | [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint 모드</span><span class="sxs-lookup"><span data-stu-id="e00e4-106">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Native Mode | [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint Mode</span></span>  
  
 <span data-ttu-id="e00e4-107">백업 및 복원 작업은 주로 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 설치 전체나 일부를 이동하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="e00e4-107">Backup and restore operations are often used to move all or part of a [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] installation:</span></span>  
  
-   <span data-ttu-id="e00e4-108">보고서 서버 데이터베이스만 이동하는 경우에는 백업 후 복원이나 분리 후 연결 방법으로 다른 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에 데이터베이스를 재배치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e00e4-108">If you are moving just the report server databases, you can use backup and restore or attach and detach to relocate the databases on a different [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span> <span data-ttu-id="e00e4-109">자세한 내용은 [다른 컴퓨터로 보고서 서버 데이터베이스 이동&#40;SSRS 기본 모드&#41;](../report-server/moving-the-report-server-databases-to-another-computer-ssrs-native-mode.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e00e4-109">For more information, see [Moving the Report Server Databases to Another Computer &#40;SSRS Native Mode&#41;](../report-server/moving-the-report-server-databases-to-another-computer-ssrs-native-mode.md).</span></span>  
  
-   <span data-ttu-id="e00e4-110">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 설치를 새 컴퓨터로 이동하는 것을 마이그레이션이라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="e00e4-110">Moving a [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] installation to a new computer is called a migration.</span></span> <span data-ttu-id="e00e4-111">설치를 마이그레이션할 때는 설치 프로그램을 실행하여 새 보고서 서버 인스턴스를 설치한 후 인스턴스 데이터를 새 컴퓨터로 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="e00e4-111">When you migrate an installation, you run Setup to install a new report server instance and then copy instance data to the new computer.</span></span> <span data-ttu-id="e00e4-112">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 설치를 마이그레이션하는 방법은 다음 항목을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="e00e4-112">For more information about migrating a [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] installation, see the following topics:</span></span>  
  
    -   [<span data-ttu-id="e00e4-113">Reporting Services 업그레이드 및 마이그레이션</span><span class="sxs-lookup"><span data-stu-id="e00e4-113">Upgrade and Migrate Reporting Services</span></span>](upgrade-and-migrate-reporting-services.md)  
  
    -   [<span data-ttu-id="e00e4-114">Reporting Services 설치 마이그레이션&#40;SharePoint 모드&#41;</span><span class="sxs-lookup"><span data-stu-id="e00e4-114">Migrate a Reporting Services Installation &#40;SharePoint Mode&#41;</span></span>](migrate-a-reporting-services-installation-sharepoint-mode.md)  
  
    -   [<span data-ttu-id="e00e4-115">Reporting Services 설치 마이그레이션&#40;기본 모드&#41;</span><span class="sxs-lookup"><span data-stu-id="e00e4-115">Migrate a Reporting Services Installation &#40;Native Mode&#41;</span></span>](migrate-a-reporting-services-installation-native-mode.md)  
  
## <a name="backing-up-the-report-server-databases"></a><span data-ttu-id="e00e4-116">보고서 서버 데이터베이스 백업</span><span class="sxs-lookup"><span data-stu-id="e00e4-116">Backing Up the Report Server Databases</span></span>  
 <span data-ttu-id="e00e4-117">보고서 서버는 상태 비저장 서버이므로 애플리케이션 데이터는 모두 **인스턴스에서 실행되는** reportserver **및** reportservertempdb [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 데이터베이스에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="e00e4-117">Because a report server is a stateless server, all application data is stored in the **reportserver** and **reportservertempdb** databases that run on a [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] instance.</span></span> <span data-ttu-id="e00e4-118">지원되는 **데이터베이스 백업 방법 중 하나를 사용하여** reportserver **및** reportservertempdb [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스를 백업할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e00e4-118">You can backup the **reportserver** and **reportservertempdb** databases using one of the supported methods for backing up [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases.</span></span> <span data-ttu-id="e00e4-119">보고서 서버 데이터베이스에 특정한 권장 사항은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="e00e4-119">Recommendations that are specific to the report server databases include the following:</span></span>  
  
-   <span data-ttu-id="e00e4-120">**reportserver** 데이터베이스를 백업하려면 전체 복구 모델을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="e00e4-120">Use the full recovery model to backup the **reportserver** database.</span></span>  
  
-   <span data-ttu-id="e00e4-121">**reportservertempdb** 데이터베이스를 백업하려면 단순 복구 모델을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="e00e4-121">Use the simple recovery model to backup the **reportservertempdb** database.</span></span>  
  
-   <span data-ttu-id="e00e4-122">데이터베이스마다 다른 백업 일정을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e00e4-122">You can use different backup schedules for each database.</span></span> <span data-ttu-id="e00e4-123">**reportservertempdb** 를 백업하는 유일한 이유는 하드웨어 오류가 있을 때 데이터베이스를 다시 만들지 않아도 되게 하기 위해서입니다.</span><span class="sxs-lookup"><span data-stu-id="e00e4-123">The only reason to backup the **reportservertempdb** is to avoid having to recreate it if there is a hardware failure.</span></span> <span data-ttu-id="e00e4-124">하드웨어 오류가 발생할 경우 **reportservertempdb**의 데이터를 복구할 필요는 없지만 테이블 구조는 복구해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e00e4-124">In the event of hardware failure, it is not necessary to recover the data in **reportservertempdb**, but you do need the table structure.</span></span> <span data-ttu-id="e00e4-125">**reportservertempdb**가 손실된 경우 보고서 서버 데이터베이스를 다시 만들어야만 복구가 가능합니다.</span><span class="sxs-lookup"><span data-stu-id="e00e4-125">If you lose **reportservertempdb**, the only way to get it back is to recreate the report server database.</span></span> <span data-ttu-id="e00e4-126">**reportservertempdb**를 다시 만드는 경우에는 기본 보고서 서버 데이터베이스와 같은 이름을 지정하는 것이 중요합니다.</span><span class="sxs-lookup"><span data-stu-id="e00e4-126">If you recreate the **reportservertempdb**, it is important that it have the same name as the primary report server database.</span></span>  
  
 <span data-ttu-id="e00e4-127">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 관계형 데이터베이스 백업 및 복구에 대한 자세한 내용은 [SQL Server 데이터베이스 백업 및 복원](../../relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e00e4-127">For more information about backup and recovery of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] relational databases, see [Back Up and Restore of SQL Server Databases](../../relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="e00e4-128">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 보고서 서버가 SharePoint 모드에 있는 경우에는 SharePoint 구성 데이터베이스 및 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 경고 데이터베이스 등 추가 데이터베이스를 고려해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e00e4-128">If your [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] report server is in SharePoint mode, there are additional databases to be concerned with, including SharePoint configuration databases and the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] alerting database.</span></span> <span data-ttu-id="e00e4-129">SharePoint 모드에서는 각 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 서비스 애플리케이션에 대해 3개의</span><span class="sxs-lookup"><span data-stu-id="e00e4-129">In SharePoint mode, three databases are created for each [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service application.</span></span> <span data-ttu-id="e00e4-130">데이터베이스( **Reportserver**, **reportservertempdb**및 **dataalerting** 데이터베이스)가 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="e00e4-130">The **reportserver**, **reportservertempdb**, and **dataalerting** databases.</span></span> <span data-ttu-id="e00e4-131">자세한 내용은 [Reporting Services SharePoint 서비스 애플리케이션 백업 및 복원](../backup-and-restore-reporting-services-sharepoint-service-applications.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e00e4-131">For more information see [Backup and Restore Reporting Services SharePoint Service Applications](../backup-and-restore-reporting-services-sharepoint-service-applications.md)</span></span>  
  
## <a name="backing-up-the-encryption-keys"></a><span data-ttu-id="e00e4-132">암호화 키 백업</span><span class="sxs-lookup"><span data-stu-id="e00e4-132">Backing Up the Encryption Keys</span></span>  
 <span data-ttu-id="e00e4-133">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 설치를 처음으로 구성하는 경우에는 암호화 키를 백업해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e00e4-133">You should backup the encryption keys when you configure a [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] installation for the first time.</span></span> <span data-ttu-id="e00e4-134">서비스 계정의 ID를 변경하거나 컴퓨터 이름을 바꾸는 경우에도 항상 키를 백업해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e00e4-134">You should also backup the keys any time you change the identity of the service accounts or rename the computer.</span></span> <span data-ttu-id="e00e4-135">자세한 내용은 [Back Up and Restore Reporting Services Encryption Keys](ssrs-encryption-keys-back-up-and-restore-encryption-keys.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e00e4-135">For more information, see [Back Up and Restore Reporting Services Encryption Keys](ssrs-encryption-keys-back-up-and-restore-encryption-keys.md).</span></span> <span data-ttu-id="e00e4-136">SharePoint 모드 보고서 서버의 경우 [Sharepoint 서비스 응용 프로그램 Reporting Services 관리](../manage-a-reporting-services-sharepoint-service-application.md)의 "키 관리" 섹션을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="e00e4-136">For SharePoint mode report servers, see the "Key Management" section of [Manage a Reporting Services SharePoint Service Application](../manage-a-reporting-services-sharepoint-service-application.md).</span></span>  
  
## <a name="backing-up-the-configuration-files"></a><span data-ttu-id="e00e4-137">구성 파일 백업</span><span class="sxs-lookup"><span data-stu-id="e00e4-137">Backing Up the Configuration Files</span></span>  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="e00e4-138">에서는 구성 파일을 사용하여 애플리케이션 설정을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="e00e4-138">uses configuration files to store application settings.</span></span> <span data-ttu-id="e00e4-139">서버를 처음 구성할 때와 사용자 지정 확장 프로그램을 배포한 후에 파일을 백업해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e00e4-139">You should backup the files when you first configure the server and after you deploy any custom extensions.</span></span> <span data-ttu-id="e00e4-140">백업할 파일에는 다음이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="e00e4-140">Files to back up include:</span></span>  
  
-   <span data-ttu-id="e00e4-141">RSReportServer.config</span><span class="sxs-lookup"><span data-stu-id="e00e4-141">Rsreportserver.config</span></span>  
  
-   <span data-ttu-id="e00e4-142">Rssvrpolicy.config</span><span class="sxs-lookup"><span data-stu-id="e00e4-142">Rssvrpolicy.config</span></span>  
  
-   <span data-ttu-id="e00e4-143">Rsmgrpolicy.config</span><span class="sxs-lookup"><span data-stu-id="e00e4-143">Rsmgrpolicy.config</span></span>  
  
-   <span data-ttu-id="e00e4-144">Reportingservicesservice.exe.config</span><span class="sxs-lookup"><span data-stu-id="e00e4-144">Reportingservicesservice.exe.config</span></span>  
  
-   <span data-ttu-id="e00e4-145">보고서 서버 및 보고서 관리자 [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] 애플리케이션용 Web.config</span><span class="sxs-lookup"><span data-stu-id="e00e4-145">Web.config for both the Report Server and Report Manager [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] applications</span></span>  
  
-   <span data-ttu-id="e00e4-146">Machine.config: [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e00e4-146">Machine.config for [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)]</span></span>  
  
## <a name="backing-up-data-files"></a><span data-ttu-id="e00e4-147">데이터 파일 백업</span><span class="sxs-lookup"><span data-stu-id="e00e4-147">Backing Up Data Files</span></span>  
 <span data-ttu-id="e00e4-148">보고서 디자이너와 모델 디자이너에서 만들어 유지 관리하는 파일을 백업합니다.</span><span class="sxs-lookup"><span data-stu-id="e00e4-148">Backup the files that you create and maintain in Report Designer and Model Designer.</span></span> <span data-ttu-id="e00e4-149">여기에는 보고서 정의 파일(.rdl), 보고서 모델 파일(.smdl), 공유 데이터 원본 파일(.rds), 데이터 뷰 파일(.dv), 데이터 원본 파일(.ds), 보고서 서버 프로젝트 파일(.rptproj) 및 보고서 솔루션 파일(.sln)이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="e00e4-149">These include report definition (.rdl) files, report model (.smdl) files, shared data source (.rds) files, data view (.dv) files, data source (.ds) files, report server project (.rptproj) files, and report solution (.sln) files.</span></span>  
  
 <span data-ttu-id="e00e4-150">관리 또는 배포 태스크를 위해 만든 스크립트 파일(.rss)은 반드시 백업합니다.</span><span class="sxs-lookup"><span data-stu-id="e00e4-150">Remember to backup any script files (.rss) that you created for administration or deployment tasks.</span></span>  
  
 <span data-ttu-id="e00e4-151">사용 중인 사용자 지정 확장 프로그램 및 사용자 지정 어셈블리의 백업 복사본이 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="e00e4-151">Verify that you have a backup copy of any custom extensions and custom assemblies you are using.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e00e4-152">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e00e4-152">See Also</span></span>  
 <span data-ttu-id="e00e4-153">[SSRS 기본 모드의 보고서 서버 데이터베이스 &#40;&#41;](../report-server/report-server-database-ssrs-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="e00e4-153">[Report Server Database &#40;SSRS Native Mode&#41;](../report-server/report-server-database-ssrs-native-mode.md) </span></span>  
 <span data-ttu-id="e00e4-154">[Reporting Services 구성 파일](../report-server/reporting-services-configuration-files.md) </span><span class="sxs-lookup"><span data-stu-id="e00e4-154">[Reporting Services Configuration Files](../report-server/reporting-services-configuration-files.md) </span></span>  
 <span data-ttu-id="e00e4-155">[rskeymgmt 유틸리티 &#40;SSRS&#41;](../tools/rskeymgmt-utility-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="e00e4-155">[rskeymgmt Utility &#40;SSRS&#41;](../tools/rskeymgmt-utility-ssrs.md) </span></span>  
 <span data-ttu-id="e00e4-156">[백업 및 복원으로 데이터베이스 복사](../../relational-databases/databases/copy-databases-with-backup-and-restore.md) </span><span class="sxs-lookup"><span data-stu-id="e00e4-156">[Copy Databases with Backup and Restore](../../relational-databases/databases/copy-databases-with-backup-and-restore.md) </span></span>  
 <span data-ttu-id="e00e4-157">[SSRS 기본 모드에서 보고서 서버 데이터베이스 &#40;관리&#41;](../report-server/administer-a-report-server-database-ssrs-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="e00e4-157">[Administer a Report Server Database &#40;SSRS Native Mode&#41;](../report-server/administer-a-report-server-database-ssrs-native-mode.md) </span></span>  
 [<span data-ttu-id="e00e4-158">암호화 키 구성 및 관리&#40;SSRS 구성 관리자&#41;</span><span class="sxs-lookup"><span data-stu-id="e00e4-158">Configure and Manage Encryption Keys &#40;SSRS Configuration Manager&#41;</span></span>](ssrs-encryption-keys-manage-encryption-keys.md)  
  
  
