---
title: 다차원 및 데이터 마이닝 모드에서 Analysis Services 설치 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- installing Analysis Services, about installing Analysis Services
- installing Analysis Services
- SSAS, installing
- Analysis Services, installing
- SQL Server Analysis Services, installing
ms.assetid: 8a1f33e8-2bd6-4fb8-bd46-c86f2a067f60
author: heidisteen
ms.author: heidist
ms.openlocfilehash: e88d4440a65392b4f6351fa2503ea7819cf528b1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646827"
---
# <a name="install-analysis-services-in-multidimensional-and-data-mining-mode"></a><span data-ttu-id="d3393-102">다차원 및 데이터 마이닝 모드에서 Analysis Services 설치</span><span class="sxs-lookup"><span data-stu-id="d3393-102">Install Analysis Services in Multidimensional and Data Mining Mode</span></span>
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]<span data-ttu-id="d3393-103">는 비즈니스 인텔리전스 애플리케이션을 위한 OLAP(온라인 분석 처리) 및 데이터 마이닝 기능을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="d3393-103">provides online analytical processing (OLAP) and data mining functionality for business intelligence applications.</span></span> <span data-ttu-id="d3393-104">이 릴리스에서는 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] *다차원 모드로*를 설치할 때 OLAP 데이터베이스 및 데이터 마이닝 모델에 대 한 지원을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d3393-104">In this release, support for OLAP databases and data mining models is available when you install [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] in *Multidimensional mode*.</span></span> <span data-ttu-id="d3393-105">다차원 모드는 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]가 실행되는 세 가지 서버 모드 중 하나이며</span><span class="sxs-lookup"><span data-stu-id="d3393-105">Multidimensional mode is one of three server modes that [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] runs in.</span></span> <span data-ttu-id="d3393-106">기본 모드입니다.</span><span class="sxs-lookup"><span data-stu-id="d3393-106">It is the default mode.</span></span> <span data-ttu-id="d3393-107">기본값을 사용하여 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]를 설치하면 다차원 데이터베이스 및 데이터 마이닝 모델을 실행하는 인스턴스를 얻게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d3393-107">If you install [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] using default values, you will get an instance that runs multidimensional databases and data mining models.</span></span>  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]<span data-ttu-id="d3393-108">는 여러 인스턴스를 지원하므로 한 컴퓨터에 여러 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 인스턴스를 설치하거나 새 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 인스턴스를 이전 버전과 함께 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d3393-108">is a multi-instance feature, which means that you can install more than one instance [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] on a single computer, or run a new instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] side-by-side an earlier version.</span></span> <span data-ttu-id="d3393-109">서버 모드는 인스턴스에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="d3393-109">Server mode is specific to an instance.</span></span> <span data-ttu-id="d3393-110">다른 모드를 사용하려면 서버 인스턴스를 추가로 설치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d3393-110">Using other modes requires that you install additional instances of the server.</span></span>  
  
 <span data-ttu-id="d3393-111">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]를 단독으로 설치하거나 다른 구성 요소와 함께 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d3393-111">You can install [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] by itself or with other components.</span></span> <span data-ttu-id="d3393-112">만 설치 하는 경우 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 설치 마법사의 기능 선택 페이지에서 **Analysis Services** 를 선택 하면 다음 기능이 설치 됩니다 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="d3393-112">If you install just [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], the following features are installed when you select **Analysis Services** on the Feature Selection page of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Installation Wizard:</span></span>  
  
-   [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="d3393-113">데이터베이스 및 데이터 마이닝 모델을 실행하기 위한 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 서버</span><span class="sxs-lookup"><span data-stu-id="d3393-113">server for running [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] databases and data mining models</span></span>  
  
-   <span data-ttu-id="d3393-114">원본 데이터베이스에 대한 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 데이터 액세스에 사용되는 데이터 공급자</span><span class="sxs-lookup"><span data-stu-id="d3393-114">Data providers used for [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] data access to source databases</span></span>  
  
-   <span data-ttu-id="d3393-115">SQL Server 구성 관리자</span><span class="sxs-lookup"><span data-stu-id="d3393-115">SQL Server Configuration Manager</span></span>  
  
## <a name="choosing-additional-features"></a><span data-ttu-id="d3393-116">추가 기능 선택</span><span class="sxs-lookup"><span data-stu-id="d3393-116">Choosing additional features</span></span>  
 <span data-ttu-id="d3393-117">Analysis Services OLAP 및 데이터 웨어하우스 솔루션의 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스의 개발, 배포 및 관리를 수행하려면 추가 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 구성 요소를 설치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d3393-117">Analysis Services OLAP and data warehouse solutions will require the installation of additional [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] components to enable the development, deployment, and administration of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] databases.</span></span> <span data-ttu-id="d3393-118">일반적인 여러 사용자 시나리오에서 다음과 같은 추가 기능이 옵션으로 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="d3393-118">The following additional features are options for many typical user scenarios:</span></span>  
  
-   <span data-ttu-id="d3393-119">Analysis Services 데이터 구조 및 데이터 마이닝 모델을 만들고 보는 데 사용되는 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d3393-119">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], used to create and view Analysis Services data structures and data mining models.</span></span>  
  
-   <span data-ttu-id="d3393-120">OLE DB, ODBC 및 DB-Library용 네트워크 라이브러리를 비롯한 클라이언트와 서버 간 통신에 사용되는 클라이언트 도구 연결 구성 요소</span><span class="sxs-lookup"><span data-stu-id="d3393-120">Client tools connectivity components, used for communication between clients and servers, including network libraries for DB-Library, ODBC, and OLE DB.</span></span>  
  
-   <span data-ttu-id="d3393-121">데이터 이동, 복사 및 변환을 위한 그래픽 및 프로그래밍 가능 개체 모음인 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d3393-121">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], a set of graphical and programmable objects for moving, copying, and transforming data.</span></span>  
  
-   <span data-ttu-id="d3393-122">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 구성 관리자, [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 및 복제 모니터를 비롯한 관리 도구</span><span class="sxs-lookup"><span data-stu-id="d3393-122">Management tools, including [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)], and Replication Monitor.</span></span>  
  
## <a name="installation-tasks"></a><span data-ttu-id="d3393-123">설치 태스크</span><span class="sxs-lookup"><span data-stu-id="d3393-123">Installation Tasks</span></span>  
 <span data-ttu-id="d3393-124">설치할 때는 다음 태스크를 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d3393-124">Installation tasks include the following:</span></span>  
  
|<span data-ttu-id="d3393-125">링크</span><span class="sxs-lookup"><span data-stu-id="d3393-125">Links</span></span>|<span data-ttu-id="d3393-126">작업</span><span class="sxs-lookup"><span data-stu-id="d3393-126">Tasks</span></span>|  
|-----------|-----------|  
|<span data-ttu-id="d3393-127">SQL Server 2014을 설치 하 고 [Windows 서비스 계정 및 사용 권한을 구성](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md) [하기 위한 하드웨어 및 소프트웨어 요구 사항](hardware-and-software-requirements-for-installing-sql-server.md) 입니다.</span><span class="sxs-lookup"><span data-stu-id="d3393-127">[Hardware and Software Requirements for Installing SQL Server 2014](hardware-and-software-requirements-for-installing-sql-server.md) and [Configure Windows Service Accounts and Permissions](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md).</span></span>|<span data-ttu-id="d3393-128">설치 프로그램을 실행하기 전에 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 설치에 필요한 필수 구성 요소를 확인하고 서버 프로비전에 사용할 계정을 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="d3393-128">Before you run Setup, check prerequisites for installing [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] and determine which account you will use to provision the server.</span></span>|  
|<span data-ttu-id="d3393-129">설치 [마법사 &#40;설치&#41;에서 SQL Server 2014을 설치 ](../../database-engine/install-windows/install-sql-server-from-the-installation-wizard-setup.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="d3393-129">[Install SQL Server 2014 from the Installation Wizard &#40;Setup&#41;](../../database-engine/install-windows/install-sql-server-from-the-installation-wizard-setup.md).</span></span>|<span data-ttu-id="d3393-130">SQL Server 설치 프로그램을 실행하여 소프트웨어를 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="d3393-130">Run SQL Server Setup to install the software.</span></span>|  
|[<span data-ttu-id="d3393-131">Analysis Services 액세스를 허용하도록 Windows 방화벽 구성</span><span class="sxs-lookup"><span data-stu-id="d3393-131">Configure the Windows Firewall to Allow Analysis Services Access</span></span>](https://docs.microsoft.com/analysis-services/instances/configure-the-windows-firewall-to-allow-analysis-services-access)|<span data-ttu-id="d3393-132">설치가 완료되면 서버로의 원격 연결을 허용하도록 방화벽 설정을 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d3393-132">After Setup is finished, you must configure firewall settings to allow remote connections to the server.</span></span>|  
|[<span data-ttu-id="d3393-133">개체 및 작업에 대한 액세스 승인&#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="d3393-133">Authorizing access to objects and operations &#40;Analysis Services&#41;</span></span>](https://docs.microsoft.com/analysis-services/multidimensional-models/authorizing-access-to-objects-and-operations-analysis-services)|<span data-ttu-id="d3393-134">Analysis Services 데이터베이스에 액세스하는 사용자는 서버에 있는 데이터베이스 하나 이상에 대해 읽기 권한을 가지고 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d3393-134">Users who access Analysis Services databases must have Read permission on at least one database on the server.</span></span>|  
  
## <a name="related-content"></a><span data-ttu-id="d3393-135">관련 내용</span><span class="sxs-lookup"><span data-stu-id="d3393-135">Related Content</span></span>  
 <span data-ttu-id="d3393-136">설치와 관련된 추가적인 내용은 다음 항목을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="d3393-136">Additional setup content can be found in the following topics:</span></span>  
  
 [<span data-ttu-id="d3393-137">테이블 형식 모드에서 Analysis Services 설치</span><span class="sxs-lookup"><span data-stu-id="d3393-137">Install Analysis Services in Tabular Mode</span></span>](https://docs.microsoft.com/analysis-services/instances/install-windows/install-analysis-services)  
  
 [<span data-ttu-id="d3393-138">SharePoint 2010용 PowerPivot 설치</span><span class="sxs-lookup"><span data-stu-id="d3393-138">PowerPivot for SharePoint 2010 Installation</span></span>](../../../2014/sql-server/install/powerpivot-for-sharepoint-2010-installation.md)  
  
 [<span data-ttu-id="d3393-139">Analysis Services 인스턴스의 서버 모드 확인</span><span class="sxs-lookup"><span data-stu-id="d3393-139">Determine the Server Mode of an Analysis Services Instance</span></span>](https://docs.microsoft.com/analysis-services/instances/determine-the-server-mode-of-an-analysis-services-instance)  
  
 [<span data-ttu-id="d3393-140">SQL Server 데이터 마이닝 추가 기능</span><span class="sxs-lookup"><span data-stu-id="d3393-140">SQL Server Data Mining Add-ins</span></span>](https://www.microsoft.com/download/details.aspx?id=35578)  
  
 <span data-ttu-id="d3393-141">기본적으로 예제 데이터베이스, 예제 코드 및 클라이언트 애플리케이션 추가 기능은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]를 설치할 때 설치되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d3393-141">By default, sample databases, sample code, and client application add-ins are not installed as part of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup.</span></span> <span data-ttu-id="d3393-142">예제 데이터베이스와 예제 코드를 설치하려면 [CodePlex 웹 사이트](https://go.microsoft.com/fwlink/?LinkId=87843)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="d3393-142">To install sample databases and sample code, see the [CodePlex Web site](https://go.microsoft.com/fwlink/?LinkId=87843).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3393-143">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d3393-143">See Also</span></span>  
 <span data-ttu-id="d3393-144">[SQL Server 2012 버전에서 지 원하는 기능](https://go.microsoft.com/fwlink/?linkid=232473) </span><span class="sxs-lookup"><span data-stu-id="d3393-144">[Features Supported by the Editions of SQL Server 2012](https://go.microsoft.com/fwlink/?linkid=232473) </span></span>  
 <span data-ttu-id="d3393-145">[언어 및 데이터 정렬 &#40;Analysis Services&#41;](../../../2014/analysis-services/languages-and-collations-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="d3393-145">[Languages and Collations &#40;Analysis Services&#41;](../../../2014/analysis-services/languages-and-collations-analysis-services.md) </span></span>  
 [<span data-ttu-id="d3393-146">Analysis Services 업그레이드</span><span class="sxs-lookup"><span data-stu-id="d3393-146">Upgrade Analysis Services</span></span>](../../database-engine/install-windows/upgrade-analysis-services.md)  
  
  
