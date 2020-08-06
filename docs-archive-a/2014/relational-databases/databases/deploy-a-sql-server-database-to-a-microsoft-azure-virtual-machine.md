---
title: Microsoft Azure 가상 머신에 SQL Server 데이터베이스 배포 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- sql12.swb.deploymentwizard.deploymentsettings.f1
- sql12.swb.deploymentwizard.progress.f1
- sql11.swb.usevmdialog.f1
- sql11.swb.deploymentwizard.f1
- sql12.swb.deploymentwizard.azuresignin.f1
- sql11.swb.deploymentwizard.summary.f1
- sql11.swb.deploymentwizard.azuresignin.f1
- sql12.swb.deploymentwizard.f1
- sql12.swb.sqlvmdialog.f1
- sql11.swb.newvmdialog.f1
- sql12.swb.deploymentwizard.results.f1
- sql11.swb.deploymentwizard.progress.f1
- sql12.swb.newvmdialog.f1
- sql12.swb.deploymentwizard.sourcesettings.f1
- sql12.swb.usevmdialog.f1
- sql11.swb.deploymentwizard.sourcesettings.f1
- sql11.swb.deploymentwizard.results.f1
- sql12.swb.deploymentwizard.summary.f1
- sql11.swb.deploymentwizard.deploymentsettings.f1
helpviewer_keywords:
- Deploy a database
- Deploy to Azure VM
- Migrate to Azure
- Azure virtual machine
- Migrate to Azure VM
- Migrate to the cloud
- SQL Server Management Studio
- SSMS
- Deploy database wizard
- Deploy a SQL Server database to Azure
- Azure VM
ms.assetid: 5e82e66a-262e-4d4f-aa89-39cb62696d06
author: stevestein
ms.author: sstein
ms.openlocfilehash: d48c06db038a775811cba6705fbaf1d97a960f6c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736387"
---
# <a name="deploy-a-sql-server-database-to-a-microsoft-azure-virtual-machine"></a><span data-ttu-id="1c869-102">Microsoft Azure 가상 머신에 SQL Server 데이터베이스 배포</span><span class="sxs-lookup"><span data-stu-id="1c869-102">Deploy a SQL Server Database to a Microsoft Azure Virtual Machine</span></span>
  <span data-ttu-id="1c869-103">**AZURE vm에 SQL Server 데이터베이스 배포** 마법사를 사용 하 여 [!INCLUDE[ssDE](../../includes/ssde-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Azure vm (가상 머신)의 인스턴스에서로 데이터베이스를 배포 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c869-103">Use the **Deploy a SQL Server Database to an Azure VM** wizard to deploy a database from an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in an Azure Virtual Machine (VM).</span></span> <span data-ttu-id="1c869-104">마법사는 전체 데이터베이스 백업 작업을 사용하므로 SQL Server 사용자 데이터베이스에서 전체 데이터베이스 스키마 및 데이터를 항상 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="1c869-104">The wizard utilizes a full database backup operation, so it always copies the complete database schema and the data from a SQL Server user database.</span></span> <span data-ttu-id="1c869-105">마법사에서는 사용자의 편의를 위해 모든 Azure VM 구성을 실행하므로 VM을 미리 구성할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1c869-105">The wizard also does all of the Azure VM configuration for you, so no pre-configuration of the VM is required.</span></span>  
  
 <span data-ttu-id="1c869-106">마법사는 같은 데이터베이스 이름을 가진 기존 데이터베이스를 덮어쓰지 않으므로 차등 백업을 위해 마법사를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1c869-106">You cannot use the wizard for differential backups because the wizard will not overwrite an existing database that has the same database name.</span></span> <span data-ttu-id="1c869-107">VM에서 기존 데이터베이스를 바꾸려면 먼저 기존 데이터베이스를 삭제하거나 데이터베이스 이름을 변경해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c869-107">To replace an existing database on the VM, you must first drop the existing database or change the database name.</span></span> <span data-ttu-id="1c869-108">진행 중인 배포 작업의 데이터베이스 이름과 VM의 기존 데이터베이스 간에 이름 충돌이 발생할 경우 마법사에서는 작업을 완료할 수 있도록 진행 중인 데이터베이스에 대해 추가된 데이터베이스 이름을 제안합니다.</span><span class="sxs-lookup"><span data-stu-id="1c869-108">If there is a naming conflict between the database name for an in-flight deploy operation and an existing database on the VM, the wizard will suggest an appended database name for the in-flight database to enable you to complete the operation.</span></span>  
  
##  <a name="before-you-begin"></a><a name="before_you_begin"></a> <span data-ttu-id="1c869-109">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="1c869-109">Before You Begin</span></span>  
 <span data-ttu-id="1c869-110">이 마법사를 완료하려면 다음 정보를 제공하고 이러한 구성 설정을 마련해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c869-110">To complete this wizard, you must be able to provide the following information and have these configuration settings in place:</span></span>  
  
-   <span data-ttu-id="1c869-111">Azure 구독과 관련 된 Microsoft 계정 세부 정보입니다.</span><span class="sxs-lookup"><span data-stu-id="1c869-111">The Microsoft account details associated with your Azure subscription.</span></span>  
  
-   <span data-ttu-id="1c869-112">Azure 게시 프로필.</span><span class="sxs-lookup"><span data-stu-id="1c869-112">Your Azure publishing profile.</span></span>  
  
    > [!CAUTION]  
    >  <span data-ttu-id="1c869-113">SQL Server는 현재 프로필 버전 2.0 게시를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="1c869-113">SQL Server currently supports publishing profile version 2.0.</span></span> <span data-ttu-id="1c869-114">게시 프로필의 지원되는 버전을 다운로드하려면 [게시 프로필 2.0 다운로드](https://go.microsoft.com/fwlink/?LinkId=396421)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1c869-114">To download the supported version of the publishing profile, see [Download Publishing Profile 2.0](https://go.microsoft.com/fwlink/?LinkId=396421).</span></span>  
  
-   <span data-ttu-id="1c869-115">Azure 구독에 업로드 된 관리 인증서입니다.</span><span class="sxs-lookup"><span data-stu-id="1c869-115">The management certificate uploaded to your Azure subscription.</span></span>  
  
-   <span data-ttu-id="1c869-116">마법사가 실행 중인 컴퓨터에서 개인 인증서 저장소에 저장된 관리 인증서입니다.</span><span class="sxs-lookup"><span data-stu-id="1c869-116">The management certificate saved into the personal certificate store on the computer where the wizard is running.</span></span>  
  
-   <span data-ttu-id="1c869-117">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스가 호스팅되는 컴퓨터에서 사용할 수 있는 임시 스토리지 위치가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c869-117">You must have a temporary storage location that is available to the computer where the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database is hosted.</span></span> <span data-ttu-id="1c869-118">임시 스토리지 위치는 마법사를 실행 중인 컴퓨터에서도 사용할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c869-118">The temporary storage location must also be available to the computer where the wizard is running.</span></span>  
  
-   <span data-ttu-id="1c869-119">데이터베이스를 기존의 VM에 배포하는 경우 TCP/IP 포트를 수신하도록 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 의 인스턴스를 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c869-119">If you are deploying the database to an existing VM, the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] must be configured to listen on a TCP/IP port.</span></span>  
  
-   <span data-ttu-id="1c869-120">VM을 생성 하는 데 사용할 Azure VM 또는 갤러리 이미지에 SQL Server 클라우드 어댑터 구성 되 고 실행 중 이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c869-120">Either an Azure VM or Gallery image you plan to use for creation of the VM must have the SQL Server Cloud Adapter configured and running.</span></span>  
  
-   <span data-ttu-id="1c869-121">개인 포트 11435을 사용 하 여 Azure 게이트웨이에서 SQL Server 클라우드 어댑터에 대해 열린 끝점을 구성 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c869-121">You must configure an open endpoint for your SQL Server Cloud Adapter on the Azure gateway with private port 11435.</span></span>  
  
 <span data-ttu-id="1c869-122">또한 데이터베이스를 기존 Azure VM에 배포 하려는 경우 다음을 제공할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c869-122">In addition, if you plan to deploy your database into an existing Azure VM, you must also be able to provide:</span></span>  
  
-   <span data-ttu-id="1c869-123">VM을 호스팅하는 클라우드 서비스의 DNS 이름.</span><span class="sxs-lookup"><span data-stu-id="1c869-123">The DNS name of the cloud service that hosts your VM.</span></span>  
  
-   <span data-ttu-id="1c869-124">VM에 대한 관리자 자격 증명.</span><span class="sxs-lookup"><span data-stu-id="1c869-124">Administrator credentials for the VM.</span></span>  
  
-   <span data-ttu-id="1c869-125">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 원본 인스턴스에서 배포할 데이터베이스에 대한 백업 운영자 권한의 자격 증명.</span><span class="sxs-lookup"><span data-stu-id="1c869-125">Credentials with Backup operator privileges on the database you plan to deploy, from the source instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="1c869-126">Azure 가상 컴퓨터에서 SQL Server를 실행 하는 방법에 대 한 자세한 내용은 [azure Virtual Machines에서 SQL Server로 마이그레이션 준비](https://msdn.microsoft.com/library/dn133142.aspx)하기를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1c869-126">For more information about running SQL Server in Azure virtual machines, see [Getting Ready to Migrate to SQL Server in Azure Virtual Machines](https://msdn.microsoft.com/library/dn133142.aspx).</span></span>  
  
 <span data-ttu-id="1c869-127">Windows Server 운영 체제를 실행 중인 컴퓨터에서 다음 구성 설정을 사용하여 이 마법사를 실행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c869-127">On computers running Windows Server operating systems, you must use the following configuration settings to run this wizard:</span></span>  
  
-   <span data-ttu-id="1c869-128">보안 강화 구성 해제: 서버 관리자 사용 > Internet Explorer ESC(보안 강화 구성)를 설정할 로컬 서버 **해제**</span><span class="sxs-lookup"><span data-stu-id="1c869-128">Turn off Enhanced Security Configuration:  Use Server Manager > Local Server to set Internet Explorer Enhanced Security Configuration (ESC) to **OFF**.</span></span>  
  
-   <span data-ttu-id="1c869-129">JavaScript 사용:  Internet Explorer > 인터넷 옵션 > 보안 > 사용자 지정 수준 > 스크립팅 > 액티브 스크립팅: **사용**</span><span class="sxs-lookup"><span data-stu-id="1c869-129">Enable JavaScript:  Internet Explorer > Internet Options > Security > Customer Level > Scripting > Active Scripting: **Enable**.</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="limitations"></a> <span data-ttu-id="1c869-130">제한 사항</span><span class="sxs-lookup"><span data-stu-id="1c869-130">Limitations and Restrictions</span></span>  
 <span data-ttu-id="1c869-131">이 작업에 대한 데이터베이스 크기 제한은 1TB입니다.</span><span class="sxs-lookup"><span data-stu-id="1c869-131">The database size limitation for this operation is 1 TB.</span></span>  
  
 <span data-ttu-id="1c869-132">이 배포 기능은 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]용 SQL Server Management Studio에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1c869-132">This deployment feature is available in SQL Server Management Studio for [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)].</span></span>  
  
 <span data-ttu-id="1c869-133">이 배포 기능은 사용자 데이터베이스에서만 사용할 수 있습니다. 시스템 데이터베이스 배포는 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1c869-133">This deployment feature is for use only with user databases; deploying system databases is not supported.</span></span>  
  
 <span data-ttu-id="1c869-134">배포 기능은 선호도 그룹이 연관되어 있는 호스팅된 서비스를 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1c869-134">The deployment feature does not support hosted services that are associated with an Affinity Group.</span></span> <span data-ttu-id="1c869-135">예를 들어, 선호도 그룹과 연관된 스토리지 계정은 이 마법사의 **배포 설정** 페이지에서 사용하도록 선택할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1c869-135">For example, storage accounts associated with an Affinity Group cannot be selected for use on the **Deployment Settings** page of this wizard.</span></span>  
  
 <span data-ttu-id="1c869-136">VM의 SQL Server 버전이 원본 SQL Server 버전과 동일하거나 최신 버전이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c869-136">The SQL Server version in the VM must be the same or later than the source SQL Server version.</span></span> <span data-ttu-id="1c869-137">이 마법사를 사용 하 여 Azure VM에 배포할 수 있는 데이터베이스 버전을 SQL Server 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c869-137">SQL Server database versions that can be deployed to an Azure VM using this wizard:</span></span>  
  
-   <span data-ttu-id="1c869-138">SQL Server 2008</span><span class="sxs-lookup"><span data-stu-id="1c869-138">SQL Server 2008</span></span>  
  
-   <span data-ttu-id="1c869-139">SQL Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="1c869-139">SQL Server 2008 R2</span></span>  
  
-   <span data-ttu-id="1c869-140">SQL Server 2012</span><span class="sxs-lookup"><span data-stu-id="1c869-140">SQL Server 2012</span></span>  
  
-   [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]  
  
 <span data-ttu-id="1c869-141">Azure VM 데이터베이스에서 실행 되는 SQL Server 데이터베이스 버전은 다음에 배포할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1c869-141">SQL Server database versions running in an Azure VM database can be deployed to:</span></span>  
  
-   <span data-ttu-id="1c869-142">SQL Server 2012</span><span class="sxs-lookup"><span data-stu-id="1c869-142">SQL Server 2012</span></span>  
  
-   [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]  
  
 <span data-ttu-id="1c869-143">진행 중인 배포 작업의 데이터베이스 이름과 VM의 기존 데이터베이스 간에 이름 충돌이 발생할 경우 마법사에서는 작업을 완료할 수 있도록 진행 중인 데이터베이스에 대해 추가된 데이터베이스 이름을 제안합니다.</span><span class="sxs-lookup"><span data-stu-id="1c869-143">If there is a naming conflict between the database name for an in-flight deploy operation and an existing database on the VM, the wizard will suggest an appended database name for the in-flight database to enable you to complete the operation.</span></span>  
  
###  <a name="considerations-for-deploying-a-filestream-enabled-database-to-an-azure-vm"></a><a name="filestream"></a> <span data-ttu-id="1c869-144">Azure VM에 FILESTREAM 사용 데이터베이스를 배포하기 위한 고려 사항</span><span class="sxs-lookup"><span data-stu-id="1c869-144">Considerations for Deploying a FILESTREAM-enabled Database to an Azure VM</span></span>  
 <span data-ttu-id="1c869-145">FILESTREAM 개체에 BLOB이 저장된 데이터베이스 배포 시 다음 지침 및 제한 사항을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1c869-145">Note the following guidelines and restrictions when deploying databases that have BLOBS stored in FILESTREAM objects:</span></span>  
  
-   <span data-ttu-id="1c869-146">배포 기능을 통해 새 VM으로 FILESTREAM 사용 데이터베이스를 배포할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1c869-146">The deployment feature cannot deploy a FILESTREAM-enabled database into a new VM.</span></span> <span data-ttu-id="1c869-147">마법사를 실행하기 전에는 VM에서 FILESTREAM을 사용할 수 없는 경우 데이터베이스 복원 작업이 실패하고 마법사 작업을 성공적으로 완료할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1c869-147">If FILESTREAM is not enabled in the VM before you run the wizard, the database restore operation will fail and the wizard operation will not be able to complete successfully.</span></span> <span data-ttu-id="1c869-148">FILESTREAM을 사용하는 데이터베이스를 성공적으로 배포하려면 마법사를 실행하기 전에 호스트 VM의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에서 FILESTREAM을 사용하도록 설정하세요.</span><span class="sxs-lookup"><span data-stu-id="1c869-148">To successfully deploy a database that uses FILESTREAM, enable FILESTREAM in the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on the host VM before launching the wizard.</span></span> <span data-ttu-id="1c869-149">자세한 내용은 [FILESTREAM(SQL Server)](https://msdn.microsoft.com/library/gg471497.aspx)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1c869-149">For more information, see [FILESTREAM (SQL Server)](https://msdn.microsoft.com/library/gg471497.aspx).</span></span>  
  
-   <span data-ttu-id="1c869-150">데이터베이스에서 메모리 내 OLTP를 활용하는 경우 데이터베이스를 수정하지 않고도 Azure VM에 데이터베이스를 배포할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1c869-150">If your database utilizes In-Memory OLTP, you can deploy the database to an Azure VM without any modifications to the database.</span></span> <span data-ttu-id="1c869-151">자세한 내용은 [메모리 내 OLTP(메모리 내 최적화)](https://msdn.microsoft.com/library/dn133186\(SQL.120\).aspx)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1c869-151">For more information, see [In-Memory OLTP (In-Memory Optimization)](https://msdn.microsoft.com/library/dn133186\(SQL.120\).aspx).</span></span>  
  
###  <a name="considerations-for-geographic-distribution-of-assets"></a><a name="geography"></a><span data-ttu-id="1c869-152">자산의 지리적 분포에 대 한 고려 사항</span><span class="sxs-lookup"><span data-stu-id="1c869-152">Considerations for Geographic Distribution of Assets</span></span>  
 <span data-ttu-id="1c869-153">다음 자산은 동일한 지역에 위치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c869-153">Note that the following assets must be located in the same geographic region:</span></span>  
  
-   <span data-ttu-id="1c869-154">클라우드 서비스</span><span class="sxs-lookup"><span data-stu-id="1c869-154">Cloud Service</span></span>  
  
-   <span data-ttu-id="1c869-155">VM 위치</span><span class="sxs-lookup"><span data-stu-id="1c869-155">VM Location</span></span>  
  
-   <span data-ttu-id="1c869-156">데이터 디스크 스토리지 서비스</span><span class="sxs-lookup"><span data-stu-id="1c869-156">Data Disk Storage Service</span></span>  
  
 <span data-ttu-id="1c869-157">위에 나열된 자산이 동일한 위치에 없으면 마법사를 성공적으로 완료할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1c869-157">If the assets listed above are not co-located, the wizard will not be able to complete successfully.</span></span>  
  
###  <a name="wizard-configuration-settings"></a><a name="configuration_settings"></a> <span data-ttu-id="1c869-158">마법사 구성 설정</span><span class="sxs-lookup"><span data-stu-id="1c869-158">Wizard Configuration Settings</span></span>  
 <span data-ttu-id="1c869-159">다음 구성 정보를 사용하여 Azure VM에 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스 배포 설정을 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="1c869-159">Use the following configuration details to modify settings for a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database deployment to an Azure VM.</span></span>  
  
-   <span data-ttu-id="1c869-160">**구성 파일 기본 경로** - %LOCALAPPDATA%\SQL Server\Deploy to SQL in WA VM\DeploymentSettings.xml</span><span class="sxs-lookup"><span data-stu-id="1c869-160">**Default path for the configuration file** - %LOCALAPPDATA%\SQL Server\Deploy to SQL in WA VM\DeploymentSettings.xml</span></span>  
  
-   <span data-ttu-id="1c869-161">**구성 파일 구조**</span><span class="sxs-lookup"><span data-stu-id="1c869-161">**Configuration file structure**</span></span>  
  
    -   \<DeploymentSettings>  
  
        -   <span data-ttu-id="1c869-162"><OtherSettings</span><span class="sxs-lookup"><span data-stu-id="1c869-162"><OtherSettings</span></span>  
  
            -   <span data-ttu-id="1c869-163">TraceLevel = "Debug"\<!-- Logging level --></span><span class="sxs-lookup"><span data-stu-id="1c869-163">TraceLevel="Debug" \<!-- Logging level --></span></span>  
  
            -   <span data-ttu-id="1c869-164">BackupPath = " \\ \\ [server name] \\ [volume] \\ "\<!-- The last used path for backup. Used as default in the wizard. --></span><span class="sxs-lookup"><span data-stu-id="1c869-164">BackupPath="\\\\[server name]\\[volume]\\" \<!-- The last used path for backup. Used as default in the wizard. --></span></span>  
  
            -   <span data-ttu-id="1c869-165">CleanupDisabled = False/>\<!-- Wizard will not delete intermediate files and Azure objects (VM, CS, SA). --></span><span class="sxs-lookup"><span data-stu-id="1c869-165">CleanupDisabled = False /> \<!-- Wizard will not delete intermediate files and Azure objects (VM, CS, SA). --></span></span>  
  
        -   <span data-ttu-id="1c869-166"><PublishProfile\<!-- The last used publish profile information. --></span><span class="sxs-lookup"><span data-stu-id="1c869-166"><PublishProfile \<!-- The last used publish profile information. --></span></span>  
  
            -   <span data-ttu-id="1c869-167">Certificate = "12A34B567890123ABCD4EF567A8"\<!-- The certificate for use in the wizard. --></span><span class="sxs-lookup"><span data-stu-id="1c869-167">Certificate="12A34B567890123ABCD4EF567A8" \<!-- The certificate for use in the wizard. --></span></span>  
  
            -   <span data-ttu-id="1c869-168">Subscription = "1a2b34c5-67d8-90ef-ab12-xxxxxxxxxxxxx-67d8-ab12-xxxxxxxxxxxxx"\<!-- The subscription for use in the wizard. --></span><span class="sxs-lookup"><span data-stu-id="1c869-168">Subscription="1a2b34c5-67d8-90ef-ab12-xxxxxxxxxxxxx" \<!-- The subscription for use in the wizard. --></span></span>  
  
            -   <span data-ttu-id="1c869-169">Name = "My Subscription"\<!-- The name of the subscription. --></span><span class="sxs-lookup"><span data-stu-id="1c869-169">Name="My Subscription" \<!-- The name of the subscription. --></span></span>  
  
            -   <span data-ttu-id="1c869-170">Publisher="" /></span><span class="sxs-lookup"><span data-stu-id="1c869-170">Publisher="" /></span></span>  
  
    -   \</DeploymentSettings>  
  
 <span data-ttu-id="1c869-171">**구성 파일 값**</span><span class="sxs-lookup"><span data-stu-id="1c869-171">**Configuration file values**</span></span>  
  
###  <a name="permissions"></a><a name="permissions"></a> <span data-ttu-id="1c869-172">권한</span><span class="sxs-lookup"><span data-stu-id="1c869-172">Permissions</span></span>  
 <span data-ttu-id="1c869-173">배포 중인 데이터베이스는 정상 상태에 있어야 하고 데이터베이스는 마법사를 실행 중인 사용자 계정에 액세스할 수 있어야 하며 사용자 계정은 백업 작업을 수행할 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c869-173">The database being deployed must be in a normal state, the database must be accessible to the user account running the wizard, and the user account must have permissions to perform a backup operation.</span></span>  
  
##  <a name="using-the-deploy-database-to-azure-vm-wizard"></a><a name="launch_wizard"></a><span data-ttu-id="1c869-174">Azure VM에 데이터베이스 배포 마법사 사용</span><span class="sxs-lookup"><span data-stu-id="1c869-174">Using the Deploy Database to Azure VM Wizard</span></span>  
 <span data-ttu-id="1c869-175">**마법사를 시작하려면 다음 단계를 따르십시오.**</span><span class="sxs-lookup"><span data-stu-id="1c869-175">**To launch the wizard, use the following steps:**</span></span>  
  
1.  <span data-ttu-id="1c869-176">SQL Server Management Studio를 사용하여 배포하려는 데이터베이스가 있는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 의 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="1c869-176">Use SQL Server Management Studio to connect to the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] with the database you want to deploy.</span></span>  
  
2.  <span data-ttu-id="1c869-177">**개체 탐색기**에서 인스턴스 이름을 확장한 다음 **데이터베이스** 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="1c869-177">In **Object Explorer**, expand the instance name, then expand the **Databases** node.</span></span>  
  
3.  <span data-ttu-id="1c869-178">배포 하려는 데이터베이스를 마우스 오른쪽 단추로 클릭 하 고 **작업**을 선택한 다음 **Azure VM에 데이터베이스 배포 ...를** 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c869-178">Right-click the database you want to deploy, select **Tasks**, and then select **Deploy Database to Azure VM...**</span></span>  
  

  
##  <a name="introduction-page"></a><a name="Introduction"></a> <span data-ttu-id="1c869-179">소개 페이지</span><span class="sxs-lookup"><span data-stu-id="1c869-179">Introduction Page</span></span>  
 <span data-ttu-id="1c869-180">이 페이지에서는 **AZURE VM에 SQL Server 데이터베이스 배포** 마법사에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c869-180">This page describes the **Deploy a SQL Server Database to an Azure VM** wizard.</span></span>  
  
 <span data-ttu-id="1c869-181">**Options**</span><span class="sxs-lookup"><span data-stu-id="1c869-181">**Options**</span></span>  
  
-   <span data-ttu-id="1c869-182">**이 페이지를 다시 표시 안 함**</span><span class="sxs-lookup"><span data-stu-id="1c869-182">**Do not show this page again.**</span></span> <span data-ttu-id="1c869-183">- 앞으로 소개 페이지가 표시되지 않도록 하려면 이 확인란을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1c869-183">- Click this check box to stop the Introduction page from being displayed in the future.</span></span>  
  
-   <span data-ttu-id="1c869-184">**다음** - **소스 설정** 페이지로 진행합니다.</span><span class="sxs-lookup"><span data-stu-id="1c869-184">**Next** - Proceeds to the **Source Settings** page.</span></span>  
  
-   <span data-ttu-id="1c869-185">**취소** -작업을 취소 하 고 마법사를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="1c869-185">**Cancel** - Cancels the operation and closes the wizard.</span></span>  
  
-   <span data-ttu-id="1c869-186">**도움말** -마법사에 대 한 MSDN 도움말 항목을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c869-186">**Help** - Launches the MSDN Help topic for the wizard.</span></span>  
  
##  <a name="source-settings"></a><a name="Source_settings"></a><span data-ttu-id="1c869-187">원본 설정</span><span class="sxs-lookup"><span data-stu-id="1c869-187">Source Settings</span></span>  
 <span data-ttu-id="1c869-188">이 페이지를 사용 하 여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] AZURE VM에 배포 하려는 데이터베이스를 호스팅하는 인스턴스에 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c869-188">Use this page to connect to the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that hosts the database you want to deploy to the Azure VM.</span></span> <span data-ttu-id="1c869-189">또한 파일을 Azure로 전송 하기 전에 로컬 컴퓨터에서 저장할 파일의 임시 위치를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c869-189">You will also specify a temporary location for files to be saved from the local machine before they are transferred to Azure.</span></span> <span data-ttu-id="1c869-190">이 위치는 공유 네트워크 위치일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1c869-190">This can be a shared, network location.</span></span>  
  
 <span data-ttu-id="1c869-191">**Options**</span><span class="sxs-lookup"><span data-stu-id="1c869-191">**Options**</span></span>  
  
-   <span data-ttu-id="1c869-192">**연결 ...** 을 클릭 한 다음 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 배포할 데이터베이스를 호스팅하는 인스턴스에 대 한 연결 세부 정보를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c869-192">Click **Connect...** and then specify connection details for the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that hosts the database to deploy.</span></span>  
  
-   <span data-ttu-id="1c869-193">**데이터베이스 선택** 드롭다운 목록을 사용하여 배포할 데이터베이스를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="1c869-193">Use the **Select Database** drop-down list to specify the database to deploy.</span></span>  
  
-   <span data-ttu-id="1c869-194">**기타 설정** 필드에서 Azure VM 서비스에 액세스할 수 있는 공유 폴더를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c869-194">In the **Other Settings** field, specify a shared folder that will be accessible to the Azure VM service.</span></span>  
  
##  <a name="azure-sign-in"></a><a name="Azure_sign-in"></a><span data-ttu-id="1c869-195">Azure 로그인</span><span class="sxs-lookup"><span data-stu-id="1c869-195">Azure Sign-in</span></span>  
 <span data-ttu-id="1c869-196">이 페이지를 사용 하 여 Azure에 연결 하 고 관리 인증서 또는 게시 프로필 세부 정보를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c869-196">Use this page to connect to Azure and provide management certificate or publishing profile details.</span></span>  
  
 <span data-ttu-id="1c869-197">**Options**</span><span class="sxs-lookup"><span data-stu-id="1c869-197">**Options**</span></span>  
  
-   <span data-ttu-id="1c869-198">**관리 인증서** -이 옵션을 사용 하 여 Azure의 관리 인증서와 일치 하는 로컬 인증서 저장소의 인증서를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c869-198">**Management Certificate** - Use this option to specify a certificate from the local certificate store that matches the management certificate from Azure.</span></span>  
  
-   <span data-ttu-id="1c869-199">**게시 프로필** -이미 게시 프로필을 컴퓨터에 다운로드 한 경우이 옵션을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c869-199">**Publishing Profile** - Use this option if you already have a publishing profile downloaded to your computer.</span></span>  
  
-   <span data-ttu-id="1c869-200">**로그인** -이 옵션을 사용 하 여 Microsoft 계정 (예: Live ID 또는 Hotmail 계정)를 사용 하 여 Azure에 로그인 하 고 새 관리 인증서를 생성 하 고 다운로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c869-200">**Sign In** - Use this option to sign in to Azure using a Microsoft account - for example, a Live ID or Hotmail account - to generate and download a new management certificate.</span></span> <span data-ttu-id="1c869-201">구독당 인증서 수는 제한됩니다.</span><span class="sxs-lookup"><span data-stu-id="1c869-201">Note that the number of certificates per subscription is limited.</span></span>  
  
-   <span data-ttu-id="1c869-202">**구독** -로컬 인증서 저장소 또는 게시 프로필의 관리 인증서와 일치 하는 AZURE 구독 ID를 선택, 입력 또는 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="1c869-202">**Subscription** - Select, type, or paste your Azure subscription ID that matches the management certificate from the local certificate store or a publishing profile.</span></span>  
  
##  <a name="deployment-settings-page"></a><a name="Deployment_settings"></a><span data-ttu-id="1c869-203">배포 설정 페이지</span><span class="sxs-lookup"><span data-stu-id="1c869-203">Deployment Settings Page</span></span>  
 <span data-ttu-id="1c869-204">이 페이지에서는 대상 서버를 지정하고 새 데이터베이스에 대한 세부 정보를 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1c869-204">Use this page to specify the destination server and to provide details about your new database.</span></span>  
  
 <span data-ttu-id="1c869-205">**Options**</span><span class="sxs-lookup"><span data-stu-id="1c869-205">**Options**</span></span>  
  
-   <span data-ttu-id="1c869-206">**Azure 가상 머신** -SQL Server 데이터베이스를 호스팅할 VM에 대 한 세부 정보를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c869-206">**Azure Virtual Machine** - Specify details for the VM that will host the SQL Server database:</span></span>  
  
-   <span data-ttu-id="1c869-207">**클라우드 서비스 이름** -VM을 호스트 하는 서비스의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c869-207">**Cloud Service name** - Specify the name of the service that hosts the VM.</span></span> <span data-ttu-id="1c869-208">새 클라우드 서비스를 만들려면 새 클라우드 서비스의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="1c869-208">To create a new Cloud Service, specify a name for the new Cloud Service.</span></span>  
  
-   <span data-ttu-id="1c869-209">**가상 컴퓨터 이름** -SQL Server 데이터베이스를 호스팅할 VM의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c869-209">**Virtual Machine name** - Specify the name of the VM that will host the SQL Server database.</span></span> <span data-ttu-id="1c869-210">새 Azure VM을 만들려면 새 VM의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c869-210">To create a new Azure VM, specify a name for the new VM.</span></span>  
  
-   <span data-ttu-id="1c869-211">**설정** -설정 단추를 사용 하 여 SQL Server 데이터베이스를 호스트할 새 VM을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="1c869-211">**Settings** - Use the Settings button to create a new VM to host the SQL Server database.</span></span> <span data-ttu-id="1c869-212">기존 VM을 사용하는 경우 사용자가 제공하는 정보를 사용하여 자격 증명을 인증합니다.</span><span class="sxs-lookup"><span data-stu-id="1c869-212">If you are using an existing VM, the information you provide will be used to authenticate your credentials.</span></span>  
  
-   <span data-ttu-id="1c869-213">**저장소 계정** -드롭다운 목록에서 저장소 계정을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c869-213">**Storage account** - Select the storage account from the drop-down list.</span></span> <span data-ttu-id="1c869-214">새 스토리지 계정을 만들려면 새 계정의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="1c869-214">To create a new storage account, specify a name for the new account.</span></span> <span data-ttu-id="1c869-215">선호도 그룹과 연관된 스토리지 계정은 드롭다운 목록에서 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1c869-215">Note that storage accounts associated with an Affinity Group will not be available in the drop-down list.</span></span>  
  
-   <span data-ttu-id="1c869-216">**대상 데이터베이스** -대상 데이터베이스에 대 한 세부 정보를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c869-216">**Target Database** - Specify details for the target database.</span></span>  
  
-   <span data-ttu-id="1c869-217">**서버 연결** -서버에 대 한 연결 정보입니다.</span><span class="sxs-lookup"><span data-stu-id="1c869-217">**Server Connection** - Connection details for the server.</span></span>  
  
-   <span data-ttu-id="1c869-218">**데이터베이스** -새 데이터베이스의 이름을 지정 하거나 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c869-218">**Database** - Specify or confirm the name of a new database.</span></span> <span data-ttu-id="1c869-219">데이터베이스 이름이 대상 SQL Server 인스턴스에 이미 있는 경우 수정된 데이터베이스 이름을 지정하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="1c869-219">If the database name already exists on the destination SQL Server instance, we suggest that you specify a modified database name.</span></span>  
  
##  <a name="summary-page"></a><a name="Summary"></a> <span data-ttu-id="1c869-220">요약 페이지</span><span class="sxs-lookup"><span data-stu-id="1c869-220">Summary Page</span></span>  
 <span data-ttu-id="1c869-221">이 페이지에서 작업에 대해 지정한 설정을 검토할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1c869-221">Use this page to review the specified settings for the operation.</span></span> <span data-ttu-id="1c869-222">지정한 설정을 사용하여 배포 작업을 완료하려면 **마침**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1c869-222">To complete the deploy operation using the specified settings, click **Finish**.</span></span> <span data-ttu-id="1c869-223">배포 작업을 취소 하 고 마법사를 종료 하려면 **취소**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c869-223">To cancel the deploy operation and exit the wizard, click **Cancel**.</span></span>  
  
 <span data-ttu-id="1c869-224">Azure VM의 SQL Server 데이터베이스에 데이터베이스 세부 정보를 배포 하는 데 필요한 수동 단계가 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1c869-224">There may be manual steps required to deploy database details to the SQL Server database on the Azure VM.</span></span> <span data-ttu-id="1c869-225">이러한 단계를 자세히 설명하겠습니다.</span><span class="sxs-lookup"><span data-stu-id="1c869-225">These steps will be outlined in detail for you.</span></span>  
  
##  <a name="results-page"></a><a name="Results"></a><span data-ttu-id="1c869-226">결과 페이지</span><span class="sxs-lookup"><span data-stu-id="1c869-226">Results Page</span></span>  
 <span data-ttu-id="1c869-227">이 페이지에서는 배포 작업의 성공 또는 실패를 보고하고 각 작업의 결과를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="1c869-227">This page reports the success or failure of the deploy operation, showing the results of each action.</span></span> <span data-ttu-id="1c869-228">오류가 발생한 동작에는 모두 **결과** 열에 표시가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1c869-228">Any action that encountered an error will have an indication in the **Result** column.</span></span> <span data-ttu-id="1c869-229">링크를 클릭하면 해당 동작의 오류에 대한 보고서가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="1c869-229">Click the link to view a report of the error for that action.</span></span>  
  
 <span data-ttu-id="1c869-230">**마침** 을 클릭하여 마법사를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="1c869-230">Click **Finish** to close the wizard.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c869-231">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1c869-231">See Also</span></span>  
 <span data-ttu-id="1c869-232">[SQL Server에 대 한 클라우드 어댑터](../../database-engine/cloud-adapter-for-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="1c869-232">[Cloud Adapter for SQL Server](../../database-engine/cloud-adapter-for-sql-server.md) </span></span>  
 <span data-ttu-id="1c869-233">[데이터베이스 수명 주기 관리](../database-lifecycle-management.md) </span><span class="sxs-lookup"><span data-stu-id="1c869-233">[Database Lifecycle Management](../database-lifecycle-management.md) </span></span>  
 <span data-ttu-id="1c869-234">[데이터 계층 응용 프로그램 내보내기](../data-tier-applications/export-a-data-tier-application.md) </span><span class="sxs-lookup"><span data-stu-id="1c869-234">[Export a Data-tier Application](../data-tier-applications/export-a-data-tier-application.md) </span></span>  
 <span data-ttu-id="1c869-235">[BACPAC 파일을 가져와 새 사용자 데이터베이스 만들기](../data-tier-applications/import-a-bacpac-file-to-create-a-new-user-database.md) </span><span class="sxs-lookup"><span data-stu-id="1c869-235">[Import a BACPAC File to Create a New User Database](../data-tier-applications/import-a-bacpac-file-to-create-a-new-user-database.md) </span></span>  
 <span data-ttu-id="1c869-236">[Azure SQL Database 백업 및 복원](https://msdn.microsoft.com/library/azure/jj650016.aspx) </span><span class="sxs-lookup"><span data-stu-id="1c869-236">[Azure SQL Database Backup and Restore](https://msdn.microsoft.com/library/azure/jj650016.aspx) </span></span>  
 <span data-ttu-id="1c869-237">[Azure Virtual Machines에서 SQL Server 배포](https://msdn.microsoft.com/library/dn133141.aspx) </span><span class="sxs-lookup"><span data-stu-id="1c869-237">[SQL Server Deployment in Azure Virtual Machines](https://msdn.microsoft.com/library/dn133141.aspx) </span></span>  
 [<span data-ttu-id="1c869-238">Azure Virtual Machines의 SQL Server로 마이그레이션할 준비하기</span><span class="sxs-lookup"><span data-stu-id="1c869-238">Getting Ready to Migrate to SQL Server in Azure Virtual Machines</span></span>](https://msdn.microsoft.com/library/dn133142.aspx)  
  
  
