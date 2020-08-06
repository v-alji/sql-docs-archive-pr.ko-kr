---
title: SQL Server 2014 설치 Microsoft Docs
ms.custom: ''
ms.date: 09/09/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
f1_keywords:
- sql12.portal.Installation.f1
helpviewer_keywords:
- installing SQL Server, initial installation
- installation [SQL Server]
- initial installation [SQL Server]
ms.assetid: edd75f68-dc62-4479-a596-57ce8ad632e5
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 62630400f276b00de8acfa875244558cdb39e47b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87729748"
---
# <a name="installation-for-sql-server-2014"></a><span data-ttu-id="27126-102">SQL Server 2014 설치</span><span class="sxs-lookup"><span data-stu-id="27126-102">Installation for SQL Server 2014</span></span>
 ## <a name="download-sql-server-2014-express"></a>[<span data-ttu-id="27126-103">SQL Server 2014 Express 다운로드</span><span class="sxs-lookup"><span data-stu-id="27126-103">Download SQL Server 2014 Express</span></span>](http://www.hanselman.com/blog/DownloadSQLServerExpress.aspx)
  <span data-ttu-id="27126-104">**모든 설치 관리자 패키지 링크를 한 곳에서 수집 하기 위해 [Scott Hanselman](http://www.hanselman.com/) 주셔서 감사 합니다.**</span><span class="sxs-lookup"><span data-stu-id="27126-104">**Thank you to [Scott Hanselman](http://www.hanselman.com/) for collecting all of the installer package links in one place!**</span></span>
  
  <span data-ttu-id="27126-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 설치 마법사는 모든 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 구성 요소를 설치하는 하나의 기능 트리를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="27126-105">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Installation Wizard provides a single feature tree to install all [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] components:</span></span>  
  
-   [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
-   [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]  
  
-   [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
-   [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]  
  
-   [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)]  
  
-   [!INCLUDE[ssDQSnoversion](../../includes/ssdqsnoversion-md.md)]  
  
-   <span data-ttu-id="27126-106">관리 도구</span><span class="sxs-lookup"><span data-stu-id="27126-106">Management tools</span></span>  
  
-   <span data-ttu-id="27126-107">연결 구성 요소</span><span class="sxs-lookup"><span data-stu-id="27126-107">Connectivity components</span></span>  
  
 <span data-ttu-id="27126-108">각 구성 요소를 개별적으로 설치하거나 위에 나열된 구성 요소 조합을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="27126-108">You can install each component individually or select a combination of the components listed above.</span></span> <span data-ttu-id="27126-109">에서 사용할 수 있는 버전과 구성 요소 중에서 가장 적합 한 항목을 선택 하려면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [SQL Server 2014의 버전 및 구성 요소](../../sql-server/editions-and-components-of-sql-server-2016.md) 및 [SQL Server 2014 버전에서 지 원하는 기능](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="27126-109">To make the best choice among the editions and components available in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], see [Editions and Components of SQL Server 2014](../../sql-server/editions-and-components-of-sql-server-2016.md) and [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<span data-ttu-id="27126-110">는 32비트 및 64비트 버전으로 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="27126-110">is available in 32-bit and 64-bit editions.</span></span>
 
 <span data-ttu-id="27126-111">**사용해 보기:**</span><span class="sxs-lookup"><span data-stu-id="27126-111">**Try it out:**</span></span>  
  
-   <span data-ttu-id="27126-112">Azure 계정이 있으세요?</span><span class="sxs-lookup"><span data-stu-id="27126-112">Have an Azure account?</span></span>  <span data-ttu-id="27126-113">그런 다음 **[여기](https://ms.portal.azure.com/?flight=1#create/Microsoft.SQLServer2016RTMEnterpriseWindowsServer2012R2)** 로 이동 하 여 SQL SERVER 2014 SP1 (서비스 팩 1)이 이미 설치 되어 있는 가상 머신을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="27126-113">Then go **[Here](https://ms.portal.azure.com/?flight=1#create/Microsoft.SQLServer2016RTMEnterpriseWindowsServer2012R2)** to spin up a Virtual Machine with SQL Server 2014 Service Pack 1 (SP1) already installed.</span></span> <span data-ttu-id="27126-114">SQL Server 2014 (SP1)에 대 한 자세한 내용은 [SQL Server 2014 서비스 팩 1 릴리스 정보](https://support.microsoft.com/kb/3058865)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="27126-114">For more information on SQL Server 2014 (SP1), see [SQL Server 2014 Service Pack 1 release information](https://support.microsoft.com/kb/3058865).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="27126-115">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="27126-115">In This Section</span></span>  
 <span data-ttu-id="27126-116">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 설치 마법사와 명령 프롬프트 중 어느 쪽을 사용하는지에 관계없이 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]설치에는 다음 단계가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="27126-116">Regardless of whether you use the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Installation Wizard or the command prompt to install [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], Setup involves the following steps:</span></span>  
  
 [<span data-ttu-id="27126-117">SQL Server 설치 계획</span><span class="sxs-lookup"><span data-stu-id="27126-117">Planning a SQL Server Installation</span></span>](../../sql-server/install/planning-a-sql-server-installation.md)  
 <span data-ttu-id="27126-118">컴퓨터에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]설치를 준비하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="27126-118">Describes how to prepare your computer for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:</span></span>  
  
-   <span data-ttu-id="27126-119">하드웨어 및 소프트웨어 요구 사항</span><span class="sxs-lookup"><span data-stu-id="27126-119">Hardware and software requirements.</span></span>  
  
-   <span data-ttu-id="27126-120">시스템 구성 검사기 요구 사항 및 차단 문제</span><span class="sxs-lookup"><span data-stu-id="27126-120">System Configuration Checker requirements and blocking issues.</span></span>  
  
-   <span data-ttu-id="27126-121">보안 고려 사항</span><span class="sxs-lookup"><span data-stu-id="27126-121">Security considerations.</span></span>  
  
 [<span data-ttu-id="27126-122">SQL Server 2014 설치</span><span class="sxs-lookup"><span data-stu-id="27126-122">Install SQL Server 2014</span></span>](install-sql-server.md)  
 <span data-ttu-id="27126-123">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]설치 옵션에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="27126-123">Describes installation options for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 [<span data-ttu-id="27126-124">SQL Server 2014로 업그레이드</span><span class="sxs-lookup"><span data-stu-id="27126-124">Upgrade to SQL Server 2014</span></span>](upgrade-sql-server.md)  
 <span data-ttu-id="27126-125">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]로 업그레이드하기 위한 옵션에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="27126-125">Describes options for upgrading to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 [<span data-ttu-id="27126-126">SQL Server 2014 제거</span><span class="sxs-lookup"><span data-stu-id="27126-126">Uninstall SQL Server 2014</span></span>](../../sql-server/install/uninstall-sql-server.md)  
 <span data-ttu-id="27126-127">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 및 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)]를 제거하는 절차에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="27126-127">Describes procedures to uninstall [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)].</span></span>  
  
 [<span data-ttu-id="27126-128">SQL Server 장애 조치(Failover) 클러스터 설치</span><span class="sxs-lookup"><span data-stu-id="27126-128">SQL Server Failover Cluster Installation</span></span>](../../sql-server/failover-clusters/install/sql-server-failover-cluster-installation.md)  
 <span data-ttu-id="27126-129">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 설치 설명서 중 이 섹션에서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 장애 조치(failover) 클러스터를 설치 및 구성하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="27126-129">This section of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup documentation explains how to install, and configure [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] failover cluster.</span></span>  
  
 [<span data-ttu-id="27126-130">SQL Server 2014 BI 기능 설치</span><span class="sxs-lookup"><span data-stu-id="27126-130">Install SQL Server 2014 BI Features</span></span>](../../sql-server/install/install-sql-server-business-intelligence-features.md)  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="27126-131">기능(Microsoft BI 플랫폼에 속함)에는 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]및 분석 데이터를 만들거나 사용하는 데 사용되는 일부 클라이언트 애플리케이션이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="27126-131">features that are part of the Microsoft BI platform include [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], and several client applications used for creating or working with analytical data.</span></span> <span data-ttu-id="27126-132">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 설치 설명서 중 이 섹션에서는 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 및 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]설치 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="27126-132">This section of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup documentation explains how to install [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] and [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="27126-133">관련 단원</span><span class="sxs-lookup"><span data-stu-id="27126-133">Related Sections</span></span>  
 [<span data-ttu-id="27126-134">설치 방법 도움말 항목</span><span class="sxs-lookup"><span data-stu-id="27126-134">Installation How-to Topics</span></span>](../../sql-server/install/installation-how-to-topics.md)  
 <span data-ttu-id="27126-135">설치 마법사, 명령 프롬프트, 구성 파일 사용 및 SysPrep 사용 등의 방법으로 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]를 설치하는 절차 항목에 대한 링크를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="27126-135">Provides links to procedural topics for installing [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] from the installation wizard, from the command prompt, by using configuration files, and by using SysPrep.</span></span>  
  
 [<span data-ttu-id="27126-136">SharePoint &#40;PowerPivot 및 Reporting Services를 사용 하 여 SQL Server BI 기능 설치&#41;</span><span class="sxs-lookup"><span data-stu-id="27126-136">Install SQL Server BI Features with SharePoint &#40;PowerPivot and Reporting Services&#41;</span></span>](../../sql-server/install/install-sql-server-bi-features-sharepoint-powerpivot-reporting-services.md)  
 <span data-ttu-id="27126-137">이 섹션에서는 SharePoint 환경에 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 기능을 설치하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="27126-137">This section explains how to install [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] features in a SharePoint environment.</span></span> <span data-ttu-id="27126-138">여기에서는 SharePoint의 특정 버전 및 에디션에서 사용할 수 있는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 기능을 설명하고</span><span class="sxs-lookup"><span data-stu-id="27126-138">It identifies which [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] features are available given a specific version and edition of SharePoint.</span></span> <span data-ttu-id="27126-139">SharePoint용 PowerPivot 및 SharePoint 모드의 Reporting Services에 대한 설치 지침을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="27126-139">It also includes installation procedures for PowerPivot for SharePoint and Reporting Services in SharePoint mode.</span></span>  
  
 [<span data-ttu-id="27126-140">SQL Server 예제 및 예제 데이터베이스 설치</span><span class="sxs-lookup"><span data-stu-id="27126-140">Installing SQL Server Samples and Sample Databases</span></span>](https://sqlserversamples.codeplex.com/)  
 <span data-ttu-id="27126-141">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 예제 및 예제 데이터베이스를 설치 및 구성하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="27126-141">Describes how to install and configure [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] samples and sample databases.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27126-142">참고 항목</span><span class="sxs-lookup"><span data-stu-id="27126-142">See Also</span></span>  
 <span data-ttu-id="27126-143">[SQL Server 설치의 새로운 기능](../../sql-server/install/what-s-new-in-sql-server-installation.md) </span><span class="sxs-lookup"><span data-stu-id="27126-143">[What's New in SQL Server Installation](../../sql-server/install/what-s-new-in-sql-server-installation.md) </span></span>  
 [<span data-ttu-id="27126-144">SQL Server 2014 설치에 대한 하드웨어 및 소프트웨어 요구 사항</span><span class="sxs-lookup"><span data-stu-id="27126-144">Hardware and Software Requirements for Installing SQL Server 2014</span></span>](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md)  
  
