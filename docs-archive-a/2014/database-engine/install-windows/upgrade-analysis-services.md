---
title: Analysis Services 업그레이드 | Microsoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- upgrading databases
- databases [Analysis Services], upgrading
- installing Analysis Services, side-by-side installations
- Analysis Services upgrades
- Analysis Services upgrades, about upgrading Analysis Services
- SSAS, database migration
- upgrading Analysis Services
- installing Analysis Services, upgrading
- SSAS, upgrading
ms.assetid: a131d329-386e-4470-aaa9-ffcde4e5ec0c
author: Minewiskan
ms.author: owend
ms.openlocfilehash: 78bf7f27233bcfd46bc1f189324eddc72adcc961
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649161"
---
# <a name="upgrade-analysis-services"></a><span data-ttu-id="dc6dc-102">Analysis Services 업그레이드</span><span class="sxs-lookup"><span data-stu-id="dc6dc-102">Upgrade Analysis Services</span></span>
  <span data-ttu-id="dc6dc-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 설치 프로그램을 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]를 업그레이드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc6dc-103">Use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup to upgrade [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="dc6dc-104">SharePoint 모드에서 업그레이드 하는 방법에 대 한 자세한 내용은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [SharePoint용 PowerPivot 업그레이드](upgrade-power-pivot-for-sharepoint.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="dc6dc-104">For detailed information on upgrading [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in SharePoint mode, see [Upgrade PowerPivot for SharePoint](upgrade-power-pivot-for-sharepoint.md).</span></span> <span data-ttu-id="dc6dc-105">기존 SQL Server 인스턴스를 업그레이드 하는 방법에 대 한 자세한 내용은 [설치 마법사를 사용 하 여 SQL Server 2014로 업그레이드 &#40;설치&#41;](upgrade-sql-server-using-the-installation-wizard-setup.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="dc6dc-105">For more information about upgrading an existing SQL Server instance, see [Upgrade to SQL Server 2014 Using the Installation Wizard &#40;Setup&#41;](upgrade-sql-server-using-the-installation-wizard-setup.md).</span></span>  
  
## <a name="known-upgrade-issues"></a><span data-ttu-id="dc6dc-106">알려진 업그레이드 문제</span><span class="sxs-lookup"><span data-stu-id="dc6dc-106">Known Upgrade Issues</span></span>  
 <span data-ttu-id="dc6dc-107">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]으로 업그레이드하기 전에 다음을 검토하십시오.</span><span class="sxs-lookup"><span data-stu-id="dc6dc-107">Before upgrading to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], review the following:</span></span>  
  
-   <span data-ttu-id="dc6dc-108">[SQL Server 2014 릴리스 정보](https://go.microsoft.com/fwlink/?LinkID=296445)</span><span class="sxs-lookup"><span data-stu-id="dc6dc-108">[SQL Server 2014 Release Notes](https://go.microsoft.com/fwlink/?LinkID=296445).</span></span>  
  
-   <span data-ttu-id="dc6dc-109">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]더 이상 사용 되지 않거나 사용 되지 않거나 변경 된 기능에 대 한 자세한 내용은 [Analysis Services 이전 버전과의 호환성](https://docs.microsoft.com/analysis-services/analysis-services-backward-compatibility)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="dc6dc-109">To learn which [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] features and functionality have been discontinued, deprecated, or changed see [Analysis Services Backward Compatibility](https://docs.microsoft.com/analysis-services/analysis-services-backward-compatibility).</span></span>  
  
## <a name="pre-upgrade-checklist"></a><span data-ttu-id="dc6dc-110">업그레이드 전 검사 목록</span><span class="sxs-lookup"><span data-stu-id="dc6dc-110">Pre-Upgrade Checklist</span></span>  
 <span data-ttu-id="dc6dc-111">업그레이드 전에 다음 정보를 검토하십시오.</span><span class="sxs-lookup"><span data-stu-id="dc6dc-111">Before upgrading, review the following information:</span></span>  
  
-   [<span data-ttu-id="dc6dc-112">지원되는 버전 및 에디션 업그레이드</span><span class="sxs-lookup"><span data-stu-id="dc6dc-112">Supported Version and Edition Upgrades</span></span>](supported-version-and-edition-upgrades.md)  
  
-   [<span data-ttu-id="dc6dc-113">SQL Server 2014 설치에 대한 하드웨어 및 소프트웨어 요구 사항</span><span class="sxs-lookup"><span data-stu-id="dc6dc-113">Hardware and Software Requirements for Installing SQL Server 2014</span></span>](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md)  
  
-   [<span data-ttu-id="dc6dc-114">시스템 구성 검사기의 검사 매개 변수</span><span class="sxs-lookup"><span data-stu-id="dc6dc-114">Check Parameters for the System Configuration Checker</span></span>](check-parameters-for-the-system-configuration-checker.md)  
  
-   [<span data-ttu-id="dc6dc-115">SQL Server 설치에 대한 보안 고려 사항</span><span class="sxs-lookup"><span data-stu-id="dc6dc-115">Security Considerations for a SQL Server Installation</span></span>](../../sql-server/install/security-considerations-for-a-sql-server-installation.md)  
  
-   [<span data-ttu-id="dc6dc-116">Analysis Services 데이터베이스 백업 및 복원</span><span class="sxs-lookup"><span data-stu-id="dc6dc-116">Backup and Restore of Analysis Services Databases</span></span>](https://docs.microsoft.com/analysis-services/multidimensional-models/backup-and-restore-of-analysis-services-databases)  
  
-   [<span data-ttu-id="dc6dc-117">업그레이드 관리자를 사용하여 업그레이드 준비</span><span class="sxs-lookup"><span data-stu-id="dc6dc-117">Use Upgrade Advisor to Prepare for Upgrades</span></span>](../../sql-server/install/use-upgrade-advisor-to-prepare-for-upgrades.md)  
  
## <a name="upgrading-analysis-services"></a><span data-ttu-id="dc6dc-118">Analysis Services 업그레이드</span><span class="sxs-lookup"><span data-stu-id="dc6dc-118">Upgrading Analysis Services</span></span>  
 <span data-ttu-id="dc6dc-119">다음의 여러 방법 중에서 선택하여 서버 및 데이터를 업그레이드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc6dc-119">You can choose from several approaches to upgrade server and data:</span></span>  
  
-   <span data-ttu-id="dc6dc-120">**내부 업그레이드** 는 기존 프로그램 파일을 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 프로그램 파일로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="dc6dc-120">An **in-place upgrade** replaces the existing program files with [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] program files.</span></span> <span data-ttu-id="dc6dc-121">데이터베이스 위치는 동일하게 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="dc6dc-121">Databases remain in the same location.</span></span> <span data-ttu-id="dc6dc-122">프로그램 폴더는 새 이름을 반영하여 업데이트됩니다.</span><span class="sxs-lookup"><span data-stu-id="dc6dc-122">Program folders are updated to reflect the new name.</span></span>  
  
-   <span data-ttu-id="dc6dc-123">**Side-by-side 업그레이드** 는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 기존 Analysis Services 인스턴스가 있는 동일한 컴퓨터에를 새로 설치 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="dc6dc-123">A **side-by-side upgrade** is a new installation of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] on the same computer that has an existing Analysis Services instance.</span></span> <span data-ttu-id="dc6dc-124">같은 컴퓨터의 새 인스턴스로 데이터베이스를 이동한 후에 더 이상 사용하지 않는 이전 버전을 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc6dc-124">You can move databases over to the new instance on the same computer, and then uninstall the old version if you no longer use it.</span></span>  
  
-   <span data-ttu-id="dc6dc-125">새 하드웨어에 Analysis Services를 설치한 후에 기존 데이터베이스를 해당 서버로 마이그레이션할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc6dc-125">You can also install Analysis Services on new hardware and then migrate existing databases to that server.</span></span>  
  
## <a name="in-place-upgrade"></a><span data-ttu-id="dc6dc-126">내부 업그레이드</span><span class="sxs-lookup"><span data-stu-id="dc6dc-126">In-place Upgrade</span></span>  
 <span data-ttu-id="dc6dc-127">기존 인스턴스를로 업그레이드 하 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 고, [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 업그레이드 프로세스의 일부로 기존 인스턴스에서 기존 데이터베이스를 새 인스턴스로 자동 마이그레이션할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc6dc-127">You can upgrade an existing instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] and, as part of the upgrade process, automatically migrate existing databases from the old instance to the new instance.</span></span> <span data-ttu-id="dc6dc-128">메타데이터와 이진 데이터는 두 버전 간에 호환되므로 업그레이드 후 이 데이터를 보존하면 수동으로 마이그레이션할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="dc6dc-128">Because the metadata and binary data is compatible between the two versions, you will retain the data after you upgrade and you do not have to manually migrate the data.</span></span>  
  
 <span data-ttu-id="dc6dc-129">기존 인스턴스를 업그레이드하려면 설치 프로그램을 실행하고 기존 인스턴스의 이름을 새 인스턴스의 이름으로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="dc6dc-129">To upgrade an existing instance, run Setup and specify the name of the existing instance as the name of the new instance.</span></span>  
  
## <a name="upgrading-databases"></a><span data-ttu-id="dc6dc-130">데이터베이스 업그레이드</span><span class="sxs-lookup"><span data-stu-id="dc6dc-130">Upgrading Databases</span></span>  
 <span data-ttu-id="dc6dc-131">이전 버전 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 에서 작성된 데이터베이스는 이전 데이터베이스 호환성 수준 설정을 사용하여 업그레이드된 서버에서 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="dc6dc-131">Databases that were created in previous versions of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] run on the upgraded server under an older database compatibility level setting.</span></span> <span data-ttu-id="dc6dc-132">다음 버전에서 만든 데이터베이스의 데이터베이스 호환성 수준은 105입니다.</span><span class="sxs-lookup"><span data-stu-id="dc6dc-132">Databases created in the following versions, have a database compatibility level of 105.</span></span> <span data-ttu-id="dc6dc-133">새로운 데이터베이스 호환성 수준을 필요로 하는 기능을 사용하려면 호환성 수준을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc6dc-133">You can change the compatibility level if you want to use features that require a newer database compatibility level.</span></span> <span data-ttu-id="dc6dc-134">그렇지 않은 경우에는 원래 설정을 사용하여 업그레이드된 서버에서 데이터베이스를 실행하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="dc6dc-134">Otherwise, you can run the databases on the upgraded server using the original settings.</span></span> <span data-ttu-id="dc6dc-135">자세한 내용은 [다차원 데이터베이스의 호환성 수준 설정 &#40;Analysis Services&#41;](https://docs.microsoft.com/analysis-services/multidimensional-models/compatibility-level-of-a-multidimensional-database-analysis-services)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="dc6dc-135">For more information, see [Set the Compatibility Level of a Multidimensional Database &#40;Analysis Services&#41;](https://docs.microsoft.com/analysis-services/multidimensional-models/compatibility-level-of-a-multidimensional-database-analysis-services).</span></span>  
  
-   [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]  
  
-   [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]  
  
-   [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]  
  
-   [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="dc6dc-136">참고 항목</span><span class="sxs-lookup"><span data-stu-id="dc6dc-136">See Also</span></span>  
 <span data-ttu-id="dc6dc-137">[SQL Server 2014 버전에서 지 원하는 기능](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md) </span><span class="sxs-lookup"><span data-stu-id="dc6dc-137">[Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md) </span></span>  
 <span data-ttu-id="dc6dc-138">[SQL Server 설치 계획](../../sql-server/install/planning-a-sql-server-installation.md) </span><span class="sxs-lookup"><span data-stu-id="dc6dc-138">[Planning a SQL Server Installation](../../sql-server/install/planning-a-sql-server-installation.md) </span></span>  
 <span data-ttu-id="dc6dc-139">[Microsoft OLAP 아키텍처 이해](https://docs.microsoft.com/analysis-services/multidimensional-models/olap-physical/understanding-microsoft-olap-architecture) </span><span class="sxs-lookup"><span data-stu-id="dc6dc-139">[Understanding Microsoft OLAP Architecture](https://docs.microsoft.com/analysis-services/multidimensional-models/olap-physical/understanding-microsoft-olap-architecture) </span></span>  
 <span data-ttu-id="dc6dc-140">[업그레이드 SharePoint용 PowerPivot](upgrade-power-pivot-for-sharepoint.md) </span><span class="sxs-lookup"><span data-stu-id="dc6dc-140">[Upgrade PowerPivot for SharePoint](upgrade-power-pivot-for-sharepoint.md) </span></span>  
 <span data-ttu-id="dc6dc-141">[다차원 및 데이터 마이닝 모드에서 Analysis Services 설치](../../sql-server/install/install-analysis-services-in-multidimensional-and-data-mining-mode.md) </span><span class="sxs-lookup"><span data-stu-id="dc6dc-141">[Install Analysis Services in Multidimensional and Data Mining Mode](../../sql-server/install/install-analysis-services-in-multidimensional-and-data-mining-mode.md) </span></span>  
 [<span data-ttu-id="dc6dc-142">SharePoint 2010용 PowerPivot 설치</span><span class="sxs-lookup"><span data-stu-id="dc6dc-142">PowerPivot for SharePoint 2010 Installation</span></span>](../../sql-server/install/powerpivot-for-sharepoint-2010-installation.md)  
  
  
