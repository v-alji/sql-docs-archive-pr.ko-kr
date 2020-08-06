---
title: 데이터 마이닝 (SSAS) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- data mining [Analysis Services], about data mining
ms.assetid: b1c912da-72f6-4d96-89c8-55a2c4f19e88
author: minewiskan
ms.author: owend
ms.openlocfilehash: 7044ee397d457f7924d0db99dbec6659f969f104
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653671"
---
# <a name="data-mining-ssas"></a><span data-ttu-id="ab306-102">데이터 마이닝(SSAS)</span><span class="sxs-lookup"><span data-stu-id="ab306-102">Data Mining (SSAS)</span></span>
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]<span data-ttu-id="ab306-103">에서는 데이터 마이닝을 통합하는 솔루션을 위한 통합 플랫폼을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="ab306-103">provides an integrated platform for solutions that incorporate data mining.</span></span> <span data-ttu-id="ab306-104">관계형 또는 큐브 데이터를 사용하여 예측 분석이 포함된 비즈니스 인텔리전스 솔루션을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ab306-104">You can use either relational or cube data to create business intelligence solutions with predictive analytics.</span></span>  
  
## <a name="benefits-of-data-mining"></a><span data-ttu-id="ab306-105">데이터 마이닝의 장점</span><span class="sxs-lookup"><span data-stu-id="ab306-105">Benefits of Data Mining</span></span>  
 <span data-ttu-id="ab306-106">데이터 마이닝은 다양한 연구 결과를 기반으로 하는 통계 원칙을 사용하여 데이터에서 패턴을 검색하므로 복잡한 문제에 대해 지능형 의사 결정을 수행하는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ab306-106">Data mining uses well-researched statistical principles to discover patterns in your data, helping you make intelligent decisions about complex problems.</span></span> <span data-ttu-id="ab306-107">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 의 데이터 마이닝 알고리즘을 데이터에 적용하면 추세를 예측하고 패턴을 식별하여 규칙과 권장 사항을 만들 수 있으며 복잡한 데이터 집합에서 이벤트의 시퀀스를 분석하여 새로운 통찰력을 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ab306-107">By applying the data mining algorithms in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] to your data, you can forecast trends, identify patterns, create rules and recommendations, analyze the sequence of events in complex data sets, and gain new insights.</span></span>  
  
 <span data-ttu-id="ab306-108">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]의 데이터 마이닝은 강력하고도 사용하기 쉬우며, 많은 사용자들이 분석 및 보고에 자주 사용하는 도구와 통합되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ab306-108">In [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], data mining is powerful, accessible, and integrated with the tools that many people prefer to use for analysis and reporting.</span></span> <span data-ttu-id="ab306-109">데이터 마이닝을 시작하기에 앞서 포괄적인 배경 지식을 얻으려면 이 섹션의 링크를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="ab306-109">See the links in this section to get the broad background about data mining that you need to get started.</span></span>  
  
## <a name="key-data-mining-features"></a><span data-ttu-id="ab306-110">주요 데이터 마이닝 기능</span><span class="sxs-lookup"><span data-stu-id="ab306-110">Key Data Mining Features</span></span>  
 <span data-ttu-id="ab306-111">SQL 서버는 통합 데이터 마이닝 솔루션을 지원하여 다음과 같은 기능을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="ab306-111">SQL Server provides the following features in support of integrated data mining solutions:</span></span>  
  
-   <span data-ttu-id="ab306-112">여러 데이터 원본: 데이터 마이닝을 수행하기 위해 데이터 웨어하우스나 OLAP 큐브를 만들 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ab306-112">Multiple data sources: You do not have to create a data warehouse or an OLAP cube to do data mining.</span></span> <span data-ttu-id="ab306-113">외부 공급자, 스프레드시트 및 텍스트 파일에서도 테이블 형식 데이터를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ab306-113">You can use tabular data from external providers, spreadsheets, and even text files.</span></span> <span data-ttu-id="ab306-114">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]에서 만든 OLAP 큐브를 쉽게 마이닝할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ab306-114">You can also easily mine OLAP cubes created in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="ab306-115">그러나 메모리 내 데이터베이스에서 데이터를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ab306-115">However, you cannot use data from an in-memory database.</span></span>  
  
-   <span data-ttu-id="ab306-116">통합 데이터 정리, 데이터 관리 및 ETL: Data Quality Services는 데이터 프로파일링 및 정리를 위한 고급 도구를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="ab306-116">Integrated data cleansing, data management, and ETL: Data Quality Services provides advanced tools for profiling and cleansing data.</span></span> <span data-ttu-id="ab306-117">Integration Services는 데이터 정리와 모델 작성, 처리, 학습 및 업데이트를 위한 ETL 프로세스를 작성하는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ab306-117">Integration Services can be used to build ETL processes for cleaning data, and also for building, processing, training, and updating models.</span></span>  
  
-   <span data-ttu-id="ab306-118">사용자 지정 가능한 다양한 알고리즘: 클러스터링, 신경망 및 의사 결정 트리와 같은 알고리즘 제공 외에도 플랫폼은 고유의 사용자 지정 플러그인 알고리즘의 개발을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="ab306-118">Multiple customizable algorithms: In addition to providing algorithms such as clustering, neural networks, and decisions trees, the platform supports development of your own custom plug-in algorithms.</span></span>  
  
-   <span data-ttu-id="ab306-119">모델 테스트 인프라: 교차 유효성 검사, 분류표, 리프트 차트 및 산점도와 같은 중요한 통계 도구를 사용하여 모델과 데이터 집합을 테스트합니다.</span><span class="sxs-lookup"><span data-stu-id="ab306-119">Model testing infrastructure: Test your models and data sets using important statistical tools as cross-validation, classification matrices, lift charts, and scatter plots.</span></span> <span data-ttu-id="ab306-120">테스트 및 학습 집합을 간편하게 만들고 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="ab306-120">Easily create and manage testing and training sets.</span></span>  
  
-   <span data-ttu-id="ab306-121">쿼리 및 드릴스루: 예측 쿼리를 만들고 모델 패턴 및 통계를 검색하며 사례 데이터를 드릴스루합니다.</span><span class="sxs-lookup"><span data-stu-id="ab306-121">Querying and drillthrough: Create prediction queries, retrieve model patterns and statistics, and drill through to case data.</span></span>  
  
-   <span data-ttu-id="ab306-122">클라이언트 도구: SQL Server에서 제공하는 개발 및 디자인 스튜디오 외에도 Excel용 데이터 마이닝 추가 기능을 사용하여 모델을 만들고 쿼리하며 찾아볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ab306-122">Client tools: In addition to the development and design studios provided by SQL Server, you can use the Data Mining Add-ins for Excel to create, query, and browse models.</span></span> <span data-ttu-id="ab306-123">또한 웹 서비스를 포함한 사용자 지정 클라이언트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ab306-123">Or, create custom clients, including Web services.</span></span>  
  
-   <span data-ttu-id="ab306-124">스크립팅 언어 지원 및 관리되는 API: 모든 데이터 마이닝 개체는 완전히 프로그래밍할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ab306-124">Scripting language support and managed API: All data mining objects are fully programmable.</span></span> <span data-ttu-id="ab306-125">스크립팅은 MDX, XMLA, 또는 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]에 대한 PowerShell 확장을 통해 가능합니다.</span><span class="sxs-lookup"><span data-stu-id="ab306-125">Scripting is possible through MDX, XMLA, or the PowerShell extensions for [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="ab306-126">빠른 쿼리 및 스크립팅을 위해 DMX(Data Mining Extensions) 언어를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="ab306-126">Use the Data Mining Extensions (DMX) language for fast querying and scripting.</span></span>  
  
-   <span data-ttu-id="ab306-127">보안 및 배포: 모델 및 구조 데이터의 드릴스루에 대한 별도의 사용 권한을 포함하여 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]를 통해 역할 기반 보안을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="ab306-127">Security and deployment: Provides role-based security through [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], including separate permissions for drillthrough to model and structure data.</span></span> <span data-ttu-id="ab306-128">사용자가 패턴에 액세스하거나 예측을 수행할 수 있도록 다른 서버에 모델을 간편하게 배포</span><span class="sxs-lookup"><span data-stu-id="ab306-128">Easy deployment of models to other servers, so that users can access the patterns or perform predictions</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ab306-129">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="ab306-129">In This Section</span></span>  
 <span data-ttu-id="ab306-130">이 섹션의 항목에서는 SQL Server 데이터 마이닝의 주요 기능 및 관련 태스크를 소개합니다.</span><span class="sxs-lookup"><span data-stu-id="ab306-130">The topics in this section introduce the principal features of SQL Server Data Mining and related tasks.</span></span>  
  
-   [<span data-ttu-id="ab306-131">데이터 마이닝 개념</span><span class="sxs-lookup"><span data-stu-id="ab306-131">Data Mining Concepts</span></span>](data-mining-concepts.md)  
  
-   [<span data-ttu-id="ab306-132">데이터 마이닝 알고리즘&#40;Analysis Services - 데이터 마이닝&#41;</span><span class="sxs-lookup"><span data-stu-id="ab306-132">Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;</span></span>](data-mining-algorithms-analysis-services-data-mining.md)  
  
-   [<span data-ttu-id="ab306-133">마이닝 구조&#40;Analysis Services - 데이터 마이닝&#41;</span><span class="sxs-lookup"><span data-stu-id="ab306-133">Mining Structures &#40;Analysis Services - Data Mining&#41;</span></span>](mining-structures-analysis-services-data-mining.md)  
  
-   [<span data-ttu-id="ab306-134">마이닝 모델&#40;Analysis Services - 데이터 마이닝&#41;</span><span class="sxs-lookup"><span data-stu-id="ab306-134">Mining Models &#40;Analysis Services - Data Mining&#41;</span></span>](mining-models-analysis-services-data-mining.md)  
  
-   [<span data-ttu-id="ab306-135">테스트 및 유효성 검사&#40;데이터 마이닝&#41;</span><span class="sxs-lookup"><span data-stu-id="ab306-135">Testing and Validation &#40;Data Mining&#41;</span></span>](testing-and-validation-data-mining.md)  
  
-   [<span data-ttu-id="ab306-136">데이터 마이닝 쿼리</span><span class="sxs-lookup"><span data-stu-id="ab306-136">Data Mining Queries</span></span>](data-mining-queries.md)  
  
-   [<span data-ttu-id="ab306-137">데이터 마이닝 솔루션</span><span class="sxs-lookup"><span data-stu-id="ab306-137">Data Mining Solutions</span></span>](data-mining-solutions.md)  
  
-   [<span data-ttu-id="ab306-138">데이터 마이닝 도구</span><span class="sxs-lookup"><span data-stu-id="ab306-138">Data Mining Tools</span></span>](data-mining-tools.md)  
  
-   [<span data-ttu-id="ab306-139">데이터 마이닝 아키텍처</span><span class="sxs-lookup"><span data-stu-id="ab306-139">Data Mining Architecture</span></span>](data-mining-architecture.md)  
  
-   [<span data-ttu-id="ab306-140">보안 개요&#40;데이터 마이닝&#41;</span><span class="sxs-lookup"><span data-stu-id="ab306-140">Security Overview &#40;Data Mining&#41;</span></span>](security-overview-data-mining.md)  
  
  
