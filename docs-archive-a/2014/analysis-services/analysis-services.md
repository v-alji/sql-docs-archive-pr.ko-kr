---
title: SQL Server 2014 Analysis Services | Microsoft Docs
ms.custom: ''
ms.date: 04/06/2020
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Analysis Services, about Analysis Services - Multidimensional Data
- SSAS
- Analysis Services
- SQL Server Analysis Services, about Analysis Services - Multidimensional Data
- SQL Server Analysis Services
- multidimensional data [Analysis Services]
- SSAS, about Analysis Services - Multidimensional Data
ms.assetid: 49d186f4-4b4d-4a5a-bb1a-e2699c64a731
author: minewiskan
ms.author: owend
ms.openlocfilehash: c111bdadefeb508897538089ecb9d9a7b583d410
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648184"
---
# <a name="sql-server-2014-analysis-services"></a><span data-ttu-id="98eac-102">SQL Server 2014 Analysis Services</span><span class="sxs-lookup"><span data-stu-id="98eac-102">SQL Server 2014 Analysis Services</span></span>

  <span data-ttu-id="98eac-103">SQL Server 2014 Analysis Services는 의사 결정 지원 및 BI (비즈니스 인텔리전스) 솔루션에서 사용 되는 분석 데이터 엔진으로, Excel, Reporting Services 보고서 및 기타 타사 BI 도구와 같은 클라이언트 응용 프로그램 및 비즈니스 보고서에 대 한 분석 데이터를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="98eac-103">SQL Server 2014 Analysis Services is an analytical data engine used in decision support and business intelligence (BI) solutions, providing the analytical data for business reports and client applications such as Excel, Reporting Services reports, and other third-party BI tools.</span></span> 

## <a name="about-sql-server-analysis-services-documentation"></a><span data-ttu-id="98eac-104">SQL Server Analysis Services 설명서 정보</span><span class="sxs-lookup"><span data-stu-id="98eac-104">About SQL Server Analysis Services documentation</span></span>

<span data-ttu-id="98eac-105">설명서는 버전으로 구분 됩니다.</span><span class="sxs-lookup"><span data-stu-id="98eac-105">Documentation is separated by version.</span></span> <span data-ttu-id="98eac-106">현재 SQL Server 2014 Analysis Services 설명서입니다.</span><span class="sxs-lookup"><span data-stu-id="98eac-106">You are currently in SQL Server 2014 Analysis Services documentation.</span></span>

- <span data-ttu-id="98eac-107">SQL Server 2012 및 이전 버전에 대 한 자세한 내용은 [이전 버전 SQL Server 설명서](https://docs.microsoft.com/previous-versions/sql/)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="98eac-107">To learn more about SQL Server 2012 and earlier, see [SQL Server previous versions documentation](https://docs.microsoft.com/previous-versions/sql/).</span></span>
- <span data-ttu-id="98eac-108">SQL Server 2014에 대 한 자세한 내용은 [SQL Server 2014 온라인 설명서](../index.yml) 를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="98eac-108">To learn more about SQL Server 2014, see [Books Online for SQL Server 2014](../index.yml)</span></span>
- <span data-ttu-id="98eac-109">SQL Server 2016 이상에 대해 자세히 알아보려면 [Analysis Services 설명서](https://docs.microsoft.com/analysis-services/)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="98eac-109">To learn more about SQL Server 2016 and later, see [Analysis Services documentation](https://docs.microsoft.com/analysis-services/).</span></span>
- <span data-ttu-id="98eac-110">Azure Analysis Services에 대 한 자세한 내용은 [Azure Analysis Services 설명서](https://docs.microsoft.com/azure/analysis-services/)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="98eac-110">To learn more about Azure Analysis Services, see [Azure Analysis Services Documentation](https://docs.microsoft.com/azure/analysis-services/).</span></span>

## <a name="analysis-services-workflow"></a><span data-ttu-id="98eac-111">Analysis Services 워크플로</span><span class="sxs-lookup"><span data-stu-id="98eac-111">Analysis Services workflow</span></span>

<span data-ttu-id="98eac-112">일반적인 워크플로에는 OLAP 또는 테이블 형식 데이터 모델 작성, 서버 인스턴스에 데이터베이스로 모델 배포, 데이터베이스를 처리 하 여 데이터를 로드 하 고, 데이터 액세스를 허용 하는 사용 권한을 할당 하는 작업이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="98eac-112">A typical workflow includes building an OLAP or tabular data model, deploy the model as a database to a server instance, process the database to load it with data, and then assign permissions to allow data access.</span></span> <span data-ttu-id="98eac-113">이 다목적 데이터 모델은 준비가 되면 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]를 데이터 원본으로 지원하는 클라이언트 애플리케이션에서 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="98eac-113">When it's ready to go, this multi-purpose data model can be accessed by any client application supporting [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] as a data source.</span></span>  
  
 <span data-ttu-id="98eac-114">모델을 만들려면 SQL Server Data Tools ( [Analysis Services에 사용 되는 도구 및 응용 프로그램](tools-and-applications-used-in-analysis-services.md)참조)를 사용 하 여 테이블 형식 또는 다차원 및 데이터 마이닝 프로젝트 템플릿을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="98eac-114">To create a model, use SQL Server Data Tools (see [Tools and applications used in Analysis Services](tools-and-applications-used-in-analysis-services.md)), choosing either a Tabular or Multidimensional and Data Mining project template.</span></span> <span data-ttu-id="98eac-115">프로젝트 템플릿에는 모델에 필요한 모든 개체에 대한 폴더가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="98eac-115">The project template contains folders for all of the objects needed in a model.</span></span> <span data-ttu-id="98eac-116">마법사를 사용하여 데이터 원본, 데이터 원본 뷰, 차원, 큐브 및 역할과 같은 모든 기본 요소를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="98eac-116">You can use wizards to create all of the basic elements, such as data sources, data source views, dimensions, cubes, and roles.</span></span>  
  
 <span data-ttu-id="98eac-117">모델은 주로 SQL Server 또는 Oracle 관계형 데이터베이스 엔진에서 호스팅되는 데이터 웨어하우스와 같은 외부 데이터 시스템의 데이터로 채워집니다(테이블 형식 모델은 추가 데이터 원본 유형을 지원함).</span><span class="sxs-lookup"><span data-stu-id="98eac-117">Models are populated with data from external data systems, usually data warehouses hosted on a SQL Server or Oracle relational database engine (Tabular models support additional data source types).</span></span> <span data-ttu-id="98eac-118">모델은 큐브와 같은 쿼리 개체를 지정할 뿐만 아니라 여러 큐브 및 계산과 비즈니스 논리와 탐색 및 드릴스루 동작과 같은 상호 작용을 캡슐화하는 KPI에서 사용할 수 있는 차원도 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="98eac-118">Models specify query objects, such as cubes, but also specify dimensions that can be used in multiple cubes, calculations and KPIs that encapsulate business logic, and interactions such as navigation and drill-through behaviors.</span></span>  
  
 <span data-ttu-id="98eac-119">모델을 사용 하기 위해이 모델은 특정 서버 모드에서 데이터베이스를 실행 하는 서버 인스턴스에 배포 되어 Excel 또는 다른 응용 프로그램을 통해 연결 하는 권한 있는 사용자가 데이터를 사용할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="98eac-119">To use a model, it's deployed to a server instance that runs databases in a particular server mode, making the data available to authorized users who connect through Excel or other applications.</span></span>  
  
 <span data-ttu-id="98eac-120">인스턴스는 세 가지 서버 모드 중 하나로 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="98eac-120">You can install an instance in one of three server modes:</span></span>  
  
-   <span data-ttu-id="98eac-121">테이블 형식 모델을 실행하는 테이블 형식 인스턴스로.</span><span class="sxs-lookup"><span data-stu-id="98eac-121">As a Tabular instance, running Tabular models.</span></span>  
  
-   <span data-ttu-id="98eac-122">OLAP 큐브 및 데이터 마이닝 모델(기본값임)을 실행하는 다차원 및 데이터 마이닝 인스턴스로.</span><span class="sxs-lookup"><span data-stu-id="98eac-122">As a Multidimensional and Data Mining instance, running OLAP cubes and data mining models (this is the default).</span></span>  
  
-   <span data-ttu-id="98eac-123">SharePoint에서 PowerPivot 및 Excel 데이터 모델을 실행하는 SharePoint용 PowerPivot으로(SharePoint용 PowerPivot은 SharePoint에서 호스팅되는 데이터 모델을 로드하고 쿼리하고 새로 고치는 중간 계층 데이터 엔진임).</span><span class="sxs-lookup"><span data-stu-id="98eac-123">As PowerPivot for SharePoint, running PowerPivot and Excel data models in SharePoint (PowerPivot for SharePoint is a middle-tier data engine that loads, queries, and refreshes data models hosted in SharePoint).</span></span>  
  
 <span data-ttu-id="98eac-124">같은 데이터 엔진. 사용할 수 있는 3개의 다른 방법이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="98eac-124">Same data engine; three different ways to use it.</span></span> <span data-ttu-id="98eac-125">서버 모드는 설치 과정에서 설정되고 나중에 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="98eac-125">Note that server modes are set during installation and cannot be changed later.</span></span> <span data-ttu-id="98eac-126">다른 모드로 변경하려면 새 인스턴스를 설치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="98eac-126">You should install a new instance if you require a different mode.</span></span>  
  
 <span data-ttu-id="98eac-127">Analysis Services에 대한 기본 설명서는 작성할 프로젝트 유형에 해당하는 여러 섹션으로 구성되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="98eac-127">Foundational documentation for Analysis Services is organized into sections that correspond to the type of project you are building.</span></span> <span data-ttu-id="98eac-128">다음 링크를 선택하면 각 모드 또는 기능 영역에 대한 자세한 내용을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="98eac-128">Choose from the following links to learn more about each mode or feature area.</span></span>  
  
 <span data-ttu-id="98eac-129">**영역별 내용 찾아보기**</span><span class="sxs-lookup"><span data-stu-id="98eac-129">**Browse Content by Area**</span></span>  
 <span data-ttu-id="98eac-130">[테이블 형식 및 다차원 솔루션을 비교 하](comparing-tabular-and-multidimensional-solutions-ssas.md) 는 ![작은 파일 폴더 아이콘](../../2014/integration-services/media/filefolder-small.gif "작은 파일 폴더 아이콘") SSAS&#41;&#40;</span><span class="sxs-lookup"><span data-stu-id="98eac-130">![Small File Folder Icon](../../2014/integration-services/media/filefolder-small.gif "Small File Folder Icon") [Comparing Tabular and Multidimensional Solutions &#40;SSAS&#41;](comparing-tabular-and-multidimensional-solutions-ssas.md)</span></span>  
  
 <span data-ttu-id="98eac-131">![작은 파일 폴더 아이콘](../../2014/integration-services/media/filefolder-small.gif "작은 파일 폴더 아이콘") [Analysis Services 인스턴스 관리](instances/analysis-services-instance-management.md)</span><span class="sxs-lookup"><span data-stu-id="98eac-131">![Small File Folder Icon](../../2014/integration-services/media/filefolder-small.gif "Small File Folder Icon") [Analysis Services Instance Management](instances/analysis-services-instance-management.md)</span></span>  
  
 <span data-ttu-id="98eac-132">![작은 파일 폴더 아이콘](../../2014/integration-services/media/filefolder-small.gif "작은 파일 폴더 아이콘") [테이블 형식 모델링 &#40;SSAS 테이블 형식&#41;](tabular-models/tabular-models-ssas.md)</span><span class="sxs-lookup"><span data-stu-id="98eac-132">![Small File Folder Icon](../../2014/integration-services/media/filefolder-small.gif "Small File Folder Icon") [Tabular Modeling &#40;SSAS Tabular&#41;](tabular-models/tabular-models-ssas.md)</span></span>  
  
 <span data-ttu-id="98eac-133">![작은 파일 폴더 아이콘](../../2014/integration-services/media/filefolder-small.gif "작은 파일 폴더 아이콘") [다차원 모델링 &#40;SSAS&#41;](multidimensional-models/multidimensional-models-ssas.md)</span><span class="sxs-lookup"><span data-stu-id="98eac-133">![Small File Folder Icon](../../2014/integration-services/media/filefolder-small.gif "Small File Folder Icon") [Multidimensional Modeling &#40;SSAS&#41;](multidimensional-models/multidimensional-models-ssas.md)</span></span>  
  
 <span data-ttu-id="98eac-134">![작은 파일 폴더 아이콘](../../2014/integration-services/media/filefolder-small.gif "작은 파일 폴더 아이콘") [데이터 마이닝 &#40;SSAS&#41;](data-mining/data-mining-ssas.md)</span><span class="sxs-lookup"><span data-stu-id="98eac-134">![Small File Folder Icon](../../2014/integration-services/media/filefolder-small.gif "Small File Folder Icon") [Data Mining &#40;SSAS&#41;](data-mining/data-mining-ssas.md)</span></span>  
  
 <span data-ttu-id="98eac-135">[&#40;SSAS&#41;SharePoint용 PowerPivot](power-pivot-sharepoint/power-pivot-for-sharepoint-ssas.md) ![작은 파일 폴더 아이콘](../../2014/integration-services/media/filefolder-small.gif "작은 파일 폴더 아이콘")</span><span class="sxs-lookup"><span data-stu-id="98eac-135">![Small File Folder Icon](../../2014/integration-services/media/filefolder-small.gif "Small File Folder Icon") [PowerPivot for SharePoint &#40;SSAS&#41;](power-pivot-sharepoint/power-pivot-for-sharepoint-ssas.md)</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] <span data-ttu-id="98eac-136">기능은 버전별로 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="98eac-136">features vary by edition.</span></span> <span data-ttu-id="98eac-137">다차원 및 데이터 마이닝 모델은 스탠더드 버전에서 사용할 수 있지만 상위 버전에 비해 기능이 제한됩니다.</span><span class="sxs-lookup"><span data-stu-id="98eac-137">Multidimensional and data mining models are available in standard edition, but with fewer features than higher editions.</span></span> <span data-ttu-id="98eac-138">테이블 형식 모델 및 SharePoint용 PowerPivot은 프리미엄 기능으로 스탠더드 버전 라이선스에서 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="98eac-138">Tabular models and PowerPivot for SharePoint are premium features and are not available in a standard edition license.</span></span> <span data-ttu-id="98eac-139">자세한 내용은 [Features Supported by the Editions of SQL Server 2014](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="98eac-139">For more information, see [Features Supported by the Editions of SQL Server 2014](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98eac-140">참고 항목</span><span class="sxs-lookup"><span data-stu-id="98eac-140">See Also</span></span>  
 <span data-ttu-id="98eac-141">[Analysis Services 자습서 &#40;SSAS&#41;](analysis-services-tutorials-ssas.md) </span><span class="sxs-lookup"><span data-stu-id="98eac-141">[Analysis Services Tutorials &#40;SSAS&#41;](analysis-services-tutorials-ssas.md) </span></span>  
 <span data-ttu-id="98eac-142">[SQL Server 2014 설치](../database-engine/install-windows/installation-for-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="98eac-142">[Installation for SQL Server 2014](../database-engine/install-windows/installation-for-sql-server.md) </span></span>  
 <span data-ttu-id="98eac-143">[개발자 가이드 &#40;Analysis Services&#41;](analysis-services-developer-documentation.md) </span><span class="sxs-lookup"><span data-stu-id="98eac-143">[Developer's Guide &#40;Analysis Services&#41;](analysis-services-developer-documentation.md) </span></span>  
 <span data-ttu-id="98eac-144">[리소스 센터 SQL Server](https://go.microsoft.com/fwlink/?linkID=219676) </span><span class="sxs-lookup"><span data-stu-id="98eac-144">[SQL Server Resource Center](https://go.microsoft.com/fwlink/?linkID=219676) </span></span>  
 [<span data-ttu-id="98eac-145">SQLCat.com</span><span class="sxs-lookup"><span data-stu-id="98eac-145">SQLCat.com</span></span>](https://go.microsoft.com/fwlink/?linkID=220963)  
  
  
