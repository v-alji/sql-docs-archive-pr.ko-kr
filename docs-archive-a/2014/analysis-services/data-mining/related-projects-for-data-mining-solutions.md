---
title: 데이터 마이닝 솔루션에 대 한 관련 프로젝트 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: dc26489a-4c27-4b89-8215-6d245427c350
author: minewiskan
ms.author: owend
ms.openlocfilehash: fc0f235871607363b436867d44affd561876bf1e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660761"
---
# <a name="related-projects-for-data-mining-solutions"></a><span data-ttu-id="e2057-102">데이터 마이닝 솔루션 관련 프로젝트</span><span class="sxs-lookup"><span data-stu-id="e2057-102">Related Projects for Data Mining Solutions</span></span>
  <span data-ttu-id="e2057-103">데이터 마이닝 솔루션에 필요한 최소 사항은 데이터 원본, 데이터 원본 뷰, 마이닝 구조 및 마이닝 모델을 정의하는 데이터 마이닝 프로젝트입니다.</span><span class="sxs-lookup"><span data-stu-id="e2057-103">The minimum that is required for a data mining solution is the data mining project, which defines data sources, data source views, mining structures and mining models.</span></span> <span data-ttu-id="e2057-104">하지만 일상적인 의사 결정 과정에서 데이터 마이닝 모델을 사용하는 경우 데이터 마이닝이 예측 분석 솔루션의 다른 부분과 통합되어야 하는데 여기에는 다음과 같은 프로세스와 구성 요소가 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e2057-104">However, when data mining models are used in daily decision making, it is important that data mining be integrated with other part of a predictive analytics solution, which can include these processes and components:</span></span>  
  
-   <span data-ttu-id="e2057-105">데이터 및 변수 준비 및 선택.</span><span class="sxs-lookup"><span data-stu-id="e2057-105">Preparation and selection of data and of variables.</span></span> <span data-ttu-id="e2057-106">데이터 정리, 여러 데이터 원본의 통합 및 메타데이터 관리, 데이터를 데이터 웨어하우스로 변환, 병합 및 업로드하는 작업이 여기에 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="e2057-106">Includes data cleansing, metadata management and integration of multiple data sources, and the conversion, merging, and uploading of data into a data warehouse.</span></span>  
  
-   <span data-ttu-id="e2057-107">분석 보고, 예측 제시 및 데이터 마이닝 동작의 감사/추적</span><span class="sxs-lookup"><span data-stu-id="e2057-107">Reporting of analysis, presentation of predictions, and auditing/tracking of data mining activities.</span></span>  
  
-   <span data-ttu-id="e2057-108">다차원 모델 및 테이블 형식 모델을 사용하여 찾은 내용 살펴보기</span><span class="sxs-lookup"><span data-stu-id="e2057-108">Using multidimensional models or tabular models to explore findings.</span></span>  
  
-   <span data-ttu-id="e2057-109">데이터 마이닝 솔루션을 조정하여 새 데이터 지원 또는 현재 분석을 기반으로 지원 인프라 변경</span><span class="sxs-lookup"><span data-stu-id="e2057-109">Refinement of the data mining solution to support new data, or changes in the support infrastructure driven by current analysis.</span></span>  
  
 <span data-ttu-id="e2057-110">이 항목에서는 예측 분석 솔루션에 속해 있는 경우가 많은 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 의 다른 기능에 대해 설명합니다. 이러한 기능은 데이터 준비 및 데이터 마이닝 프로세스를 지원하거나 분석 및 동작을 위한 도구를 제공하여 사용자를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="e2057-110">This topic describes the other features of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] that are often part of a predictive analytics solution, either to support the processes of data preparation and data mining, or to support users by providing tools for analysis and action.</span></span>  
  
 [<span data-ttu-id="e2057-111">Integration Services</span><span class="sxs-lookup"><span data-stu-id="e2057-111">Integration Services</span></span>](#bkmk_SSIS)  
  
 [<span data-ttu-id="e2057-112">Reporting Services</span><span class="sxs-lookup"><span data-stu-id="e2057-112">Reporting Services</span></span>](#bkmk_SSRS)  
  
 [<span data-ttu-id="e2057-113">Data Quality Service</span><span class="sxs-lookup"><span data-stu-id="e2057-113">Data Quality Service</span></span>](#bkmk_DQSetc)  
  
 [<span data-ttu-id="e2057-114">전체 텍스트 검색</span><span class="sxs-lookup"><span data-stu-id="e2057-114">Full-Text Search</span></span>](#bkmk_FTSetc)  
  
 [<span data-ttu-id="e2057-115">의미 체계 인덱싱</span><span class="sxs-lookup"><span data-stu-id="e2057-115">Semantic Indexing</span></span>](#bkmk_SemSearch)  
  
##  <a name="sql-server-integration-services"></a><a name="bkmk_SSIS"></a> <span data-ttu-id="e2057-116">SQL Server Integration Services</span><span class="sxs-lookup"><span data-stu-id="e2057-116">SQL Server Integration Services</span></span>  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] <span data-ttu-id="e2057-117">는 데이터 마이닝 프로젝트의 데이터 준비 및 학습 단계에 필요한 구성 요소 및 기능을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="e2057-117">provides components and features that are required for the data preparation and training phases of a data mining project.</span></span> <span data-ttu-id="e2057-118">스크립트와 같은 다른 도구를 사용하여 데이터 정리 및 준비 태스크를 수행할 수도 있지만 데이터 마이닝에서 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 를 사용하면 다음과 같은 이점이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e2057-118">Although you can perform many data cleansing or preparation tasks by using other tools, such as scripts, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] has numerous advantages for data mining:</span></span>  
  
-   <span data-ttu-id="e2057-119">태스크를 반복, 자동화, 분기 및 확장이 가능한 워크플로의 일부로 표현할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e2057-119">Represents tasks as part of a workflow, which can be repeated, automated, branched, and extended.</span></span>  
  
-   <span data-ttu-id="e2057-120">감사에 대한 지원이 확장되며 다양한 방법으로 오류를 캡처하고 이벤트를 기록할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e2057-120">Provides extensive support for auditing and multiple ways of capturing errors and logging events.</span></span>  
  
     <span data-ttu-id="e2057-121">데이터 계보를 캡처할 뿐만 아니라 데이터 변환 파이프라인을 통해 데이터에 대한 변경 내용을 모니터링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e2057-121">In addition to capturing data lineage, you can monitor changes to the data throughout the data transformation pipeline.</span></span>  
  
     <span data-ttu-id="e2057-122">SSIS 워크플로를 SQL Server의 데이터 변경 캡처 기능을 지원하는 기능과 통합할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e2057-122">You can also integrate your SSIS workflows with the features that support Change Data Capture functionality in SQL Server.</span></span>  
  
-   <span data-ttu-id="e2057-123">데이터 마이닝을 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 워크플로에 통합하여 들어오는 데이터를 여러 테이블에 논리적으로 분리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e2057-123">Data mining can be incorporated in the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] workflow, to intelligently separate incoming data into multiple tables.</span></span> <span data-ttu-id="e2057-124">예를 들어 예측 쿼리를 사용하여 새 고객을 메일 캠페인의 대상으로 사용하는 여러 그룹에 분리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e2057-124">For example, you could use a prediction query to split new customers into different groups for targeting in a mailing campaign.</span></span>  
  
 <span data-ttu-id="e2057-125">다음 목록에서는 데이터 마이닝 지원에 가장 많이 사용되는 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 구성 요소에 대한 링크를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="e2057-125">The following lists provide links to the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] components that are most widely used in support of data mining.</span></span>  
  
 <span data-ttu-id="e2057-126">**제어 흐름 구성 요소**</span><span class="sxs-lookup"><span data-stu-id="e2057-126">**Control Flow Components**</span></span>  
  
-   [<span data-ttu-id="e2057-127">Analysis Services DDL 실행 태스크</span><span class="sxs-lookup"><span data-stu-id="e2057-127">Analysis Services Execute DDL Task</span></span>](../../integration-services/control-flow/analysis-services-execute-ddl-task.md)  
  
-   [<span data-ttu-id="e2057-128">Analysis Services 처리 태스크</span><span class="sxs-lookup"><span data-stu-id="e2057-128">Analysis Services Processing Task</span></span>](../../integration-services/control-flow/analysis-services-processing-task.md)  
  
-   [<span data-ttu-id="e2057-129">CDC Control Task</span><span class="sxs-lookup"><span data-stu-id="e2057-129">CDC Control Task</span></span>](../../integration-services/control-flow/cdc-control-task.md)  
  
-   [<span data-ttu-id="e2057-130">데이터 정리</span><span class="sxs-lookup"><span data-stu-id="e2057-130">Data Cleansing</span></span>](../../data-quality-services/data-cleansing.md)  
  
-   [<span data-ttu-id="e2057-131">데이터 마이닝 쿼리 태스크</span><span class="sxs-lookup"><span data-stu-id="e2057-131">Data Mining Query Task</span></span>](../../integration-services/control-flow/data-mining-query-task.md)  
  
-   [<span data-ttu-id="e2057-132">데이터 프로파일링 태스크</span><span class="sxs-lookup"><span data-stu-id="e2057-132">Data Profiling Task</span></span>](../../integration-services/control-flow/data-profiling-task.md)  
  
 <span data-ttu-id="e2057-133">**데이터 흐름 구성 요소**</span><span class="sxs-lookup"><span data-stu-id="e2057-133">**Data Flow Components**</span></span>  
  
-   [<span data-ttu-id="e2057-134">CDC 흐름 구성 요소</span><span class="sxs-lookup"><span data-stu-id="e2057-134">CDC Flow Components</span></span>](../../integration-services/data-flow/cdc-flow-components.md)  
  
-   [<span data-ttu-id="e2057-135">조건부 분할 변환</span><span class="sxs-lookup"><span data-stu-id="e2057-135">Conditional Split Transformation</span></span>](../../integration-services/data-flow/transformations/conditional-split-transformation.md)  
  
-   [<span data-ttu-id="e2057-136">데이터 변환</span><span class="sxs-lookup"><span data-stu-id="e2057-136">Data Conversion Transformation</span></span>](../../integration-services/data-flow/transformations/data-conversion-transformation.md)  
  
-   [<span data-ttu-id="e2057-137">데이터 마이닝 모델 학습 대상</span><span class="sxs-lookup"><span data-stu-id="e2057-137">Data Mining Model Training Destination</span></span>](../../integration-services/data-flow/data-mining-model-training-destination.md)  
  
-   [<span data-ttu-id="e2057-138">데이터 마이닝 쿼리 변환</span><span class="sxs-lookup"><span data-stu-id="e2057-138">Data Mining Query Transformation</span></span>](../../integration-services/data-flow/transformations/data-mining-query-transformation.md)  
  
-   [<span data-ttu-id="e2057-139">파생 열 변환</span><span class="sxs-lookup"><span data-stu-id="e2057-139">Derived Column Transformation</span></span>](../../integration-services/data-flow/transformations/derived-column-transformation.md)  
  
-   [<span data-ttu-id="e2057-140">비율 샘플링 변환</span><span class="sxs-lookup"><span data-stu-id="e2057-140">Percentage Sampling Transformation</span></span>](../../integration-services/data-flow/transformations/percentage-sampling-transformation.md)  
  
-   [<span data-ttu-id="e2057-141">용어 추출 변환</span><span class="sxs-lookup"><span data-stu-id="e2057-141">Term Extraction Transformation</span></span>](../../integration-services/data-flow/transformations/term-extraction-transformation.md)  
  
-   [<span data-ttu-id="e2057-142">용어 조회 변환</span><span class="sxs-lookup"><span data-stu-id="e2057-142">Term Lookup Transformation</span></span>](../../integration-services/data-flow/transformations/lookup-transformation.md)  
  
##  <a name="sql-server-reporting-services"></a><a name="bkmk_SSRS"></a> <span data-ttu-id="e2057-143">SQL Server Reporting Services</span><span class="sxs-lookup"><span data-stu-id="e2057-143">SQL Server Reporting Services</span></span>  
 <span data-ttu-id="e2057-144">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 는 대개 데이터 마이닝 솔루션의 중요 구성 요소로 간주되지 않지만 데이터 마이닝 솔루션의 표시에 유용한 다음 기능을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="e2057-144">Although [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] is typically not seen as a critical component of data mining solutions, it provides the following features that are useful for presentation of data mining solutions.</span></span>  
  
-   <span data-ttu-id="e2057-145">여러 원본의 데이터를 복잡한 보고서에 통합합니다.</span><span class="sxs-lookup"><span data-stu-id="e2057-145">Integration of data from multiple sources in complex reports.</span></span> <span data-ttu-id="e2057-146">분석가를 위해 모델 콘텐츠에 대한 쿼리를 만들고 최종 사용자를 위해 예측 및 추세를 보여 주는 보고서를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e2057-146">Create queries against the model content for analysts, and reports that show predictions and trends for end users.</span></span>  
  
-   <span data-ttu-id="e2057-147">사용자가 기존 마이닝 모델을 직접 쿼리할 수 있도록 해 주는 보고서를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e2057-147">The ability to create a report that lets users directly query against an existing mining model.</span></span>  
  
-   <span data-ttu-id="e2057-148">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]와 통합하여 OLAP 모델에서 만든 데이터 마이닝 차원 및 데이터 마이닝 큐브를 드릴스루하고 탐색할 수 있도록 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="e2057-148">Integration with [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], to support drillthrough and exploration of data mining dimensions and data mining cubes created from OLAP models.</span></span>  
  
-   <span data-ttu-id="e2057-149">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]에서 사용할 수 있는 매개 변수화 및 서식 지정 기능을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="e2057-149">parameterization and formatting features that are available in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="e2057-150">DMX 쿼리가 데이터 원본인 경우 Reporting Services를 사용하는 방법은 다음 링크를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e2057-150">For more information about how to use Reporting Services with DMX queries as a data source, see these links:</span></span>  
  
 [<span data-ttu-id="e2057-151">데이터 마이닝 모델에서 데이터 검색&#40;DMX&#41;&#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="e2057-151">Retrieve Data from a Data Mining Model &#40;DMX&#41; &#40;SSRS&#41;</span></span>](../../reporting-services/report-data/retrieve-data-from-a-data-mining-model-dmx-ssrs.md)  
  
 [<span data-ttu-id="e2057-152">Analysis Services DMX 쿼리 디자이너 사용자 인터페이스</span><span class="sxs-lookup"><span data-stu-id="e2057-152">Analysis Services DMX Query Designer User Interface</span></span>](../../reporting-services/report-data/analysis-services-dmx-query-designer-user-interface.md)  
  
 [<span data-ttu-id="e2057-153">DMX용 Analysis Services 연결 형식&#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="e2057-153">Analysis Services Connection Type for DMX &#40;SSRS&#41;</span></span>](../../reporting-services/report-data/analysis-services-connection-type-for-dmx-ssrs.md)  
  
 <span data-ttu-id="e2057-154">DMX를 데이터 원본으로 사용할 필요는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e2057-154">However, it is not necessary to use DMX as the data source.</span></span> <span data-ttu-id="e2057-155">데이터 마이닝용 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 구성 요소는 예측 쿼리의 결과를 관계형 데이터베이스에 저장할 수 있도록 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="e2057-155">The [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] components for data mining also support saving the results of a prediction query to a relational database.</span></span> <span data-ttu-id="e2057-156">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]를 사용하여 모델을 업데이트하는 워크플로를 설정한 경우 예측 및 기타 데이터 마이닝 쿼리 결과를 SQL Server에 저장하면 보고를 위해 [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] 또는 DMX와 인터페이스하지 않는 다른 도구를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e2057-156">If you have an established workflow for updating models using [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], persisting predictions and other data mining query results to SQL Server enable you to use [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] for reporting, as well as other tools that do not interface with DMX.</span></span>  
  
 <span data-ttu-id="e2057-157">Reporting Services를 데이터 원본에 대한 프레젠테이션 계층으로 사용하는 방법에 대한 자세한 내용은 [Integrating Reporting Services into Applications](../../reporting-services/application-integration/integrating-reporting-services-into-applications.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e2057-157">For more information about using Reporting Services as the presentation layer for data sources, see [Integrating Reporting Services into Applications](../../reporting-services/application-integration/integrating-reporting-services-into-applications.md).</span></span>  
  
##  <a name="data-quality-services"></a><a name="bkmk_DQSetc"></a><span data-ttu-id="e2057-158">Data Quality Services</span><span class="sxs-lookup"><span data-stu-id="e2057-158">Data Quality Services</span></span>  
 <span data-ttu-id="e2057-159">DQS(Data Quality Services)는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]에 새로 도입되었습니다.</span><span class="sxs-lookup"><span data-stu-id="e2057-159">Data Quality Services (DQS) is new in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="e2057-160">데이터 문제로 인해 데이터 마이닝을 수행할 수 없을 수도 있기 때문에 반복되는 분석을 수행하거나 데이터 원본이 복잡한 대규모 조직에서 작업하는 데이터 마이닝 담당자는 DQS를 사용하는 잘 계획된 데이터 프로젝트가 [!INCLUDE[tsql](../../includes/tsql-md.md)] 또는 다른 스크립트를 사용하는 데이터 임시 정리보다 데이터 마이닝 지원에 더 안정적인 솔루션이라는 것을 알게 될 것입니다.</span><span class="sxs-lookup"><span data-stu-id="e2057-160">Because data problems can make data mining impossible, data miners who perform repeated analysis or who work in large organizations with complex data sources are expected to find that a well-planned data project using DQS is a more reliable solution for support of data mining than ad hoc cleansing of data using [!INCLUDE[tsql](../../includes/tsql-md.md)] or other scripts.</span></span>  
  
 <span data-ttu-id="e2057-161">데이터 마이닝 솔루션에서 데이터 준비 및 데이터 무결성을 위해 다음과 같은 DQS 기능을 고려해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e2057-161">The following features of DQS should be considered for data preparation and data integrity in a data mining solution.</span></span>  
  
 <span data-ttu-id="e2057-162">**원본 데이터를 분석하고 변경 내용을 제시하는 컴퓨터 기반 데이터 정리 프로세스**</span><span class="sxs-lookup"><span data-stu-id="e2057-162">**A computer-assisted data cleansing process that analyzes source data and proposes changes.**</span></span>  
 <span data-ttu-id="e2057-163">DQS는 원본 데이터를 데이터 품질 공급자가 유지 관리하고 보증하는 클라우드 기반 참조 데이터와 비교할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e2057-163">DQS can compare source data with cloud-based reference data maintained and guaranteed by data quality providers.</span></span>  
  
 <span data-ttu-id="e2057-164">DQS는 원시 원본 데이터를 분석하고 사용자 데이터에서 기술 자료를 만들 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e2057-164">DQS can also analyze raw source data and create a knowledge base from user data.</span></span> <span data-ttu-id="e2057-165">처리된 데이터는 분류되어 추가로 처리할 수 있도록 사용자에게 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="e2057-165">The processed data is categorized and then displayed to the user for further processing.</span></span> <span data-ttu-id="e2057-166">정리 프로세스는 대화형이므로 데이터 관리자는 컴퓨터 기반 데이터 정리 프로세스가 제공하는 데이터를 승인, 거부 또는 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e2057-166">The cleansing process is interactive, meaning the data steward can approve, reject, or modify the data proposed by the computer-assisted data cleansing process.</span></span>  
  
 <span data-ttu-id="e2057-167">이 프로세스를 통해 지속적으로 개선하거나 여러 데이터 개선 단계에서 다시 사용할 수 있는 기술 자료가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="e2057-167">The outcome of the process is a knowledge base that you can continuously improve, or reuse in multiple data-enhancement phases.</span></span>  
  
 <span data-ttu-id="e2057-168">자세한 내용은 [Data Cleansing](../../data-quality-services/data-cleansing.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e2057-168">For more information, see [Data Cleansing](../../data-quality-services/data-cleansing.md).</span></span>  
  
 <span data-ttu-id="e2057-169">**원본 데이터를 분석하고 변경 내용을 제시하는 컴퓨터 기반 일치 과정**</span><span class="sxs-lookup"><span data-stu-id="e2057-169">**A computer-assisted matching process that analyzes source data and proposes changes.**</span></span>  
 <span data-ttu-id="e2057-170">데이터 중복을 막기 위해 데이터 원본의 추가 정리를 수행하여 정확하게 일치하는 항목 및 근사하게 일치하는 항목을 식별할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e2057-170">To prevent data duplication, you can perform addition cleansing of the data source, to identify exact and approximate matches.</span></span> <span data-ttu-id="e2057-171">이 구성 요소를 통해 일치 규칙 및 이 규칙을 적용할 임계값을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e2057-171">These components let you specify the matching rules, and the thresholds at which to apply them.</span></span>  
  
 <span data-ttu-id="e2057-172">일치하는 데이터를 찾음으로써 데이터 마이닝에 문제가 될 수 있는 중복 항목을 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e2057-172">By finding data matches, you can remove duplicates, which can be a problem for data mining.</span></span> <span data-ttu-id="e2057-173">데이터 중복 제거는 자동으로 실행되지 않으므로 데이터 관리자 또는 IT 전문가는 기술 자료에 있는 정보와 해당 데이터에 대한 변경 내용을 모두 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e2057-173">Data de-duplication is not automatic; the data steward or IT professional must verify both the knowledge in the knowledge base and the changes to be made to the data.</span></span>  
  
 <span data-ttu-id="e2057-174">초기 DQS 프로젝트를 만든 후 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 구성 요소를 사용하여 여러 태스크를 자동화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e2057-174">After you have created the initial DQS project, you can automate many of the tasks by using [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] components.</span></span>  
  
 <span data-ttu-id="e2057-175">자세한 내용은 [Data Matching](../../data-quality-services/data-matching.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e2057-175">For more information, see [Data Matching](../../data-quality-services/data-matching.md).</span></span>  
  
 <span data-ttu-id="e2057-176">데이터 품질 프로젝트에서 정리 및 일치 동작을 수행하는 동안 DQS에 의해 처리되는 데이터의 실시간 통계 및 정보를 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e2057-176">While performing cleansing and matching activities in a data quality project, you can get real-time statistics and information about the data that is being processed by DQS.</span></span> <span data-ttu-id="e2057-177">데이터 프로파일링을 통해 데이터 정리 또는 일치 작업으로 데이터 품질이 개선된 정도를 평가하고 변경된 내용을 이해할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e2057-177">Data profiling helps you assess the extent to which data cleansing or matching helped improve the data quality, and understand the changes that were made.</span></span> <span data-ttu-id="e2057-178">데이터 프로파일링 및 알림에 대한 자세한 내용은 [Data Profiling and Notifications in DQS](../../data-quality-services/data-profiling-and-notifications-in-dqs.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e2057-178">For information about data profiling and notifications, see [Data Profiling and Notifications in DQS](../../data-quality-services/data-profiling-and-notifications-in-dqs.md).</span></span>  
  
 <span data-ttu-id="e2057-179">**세 가지 유형의 정보(바로 사용할 수 있게 준비된 정보, DQS 서버가 생성한 정보 및 사용자가 생성한 정보)를 나타내는 기술 자료입니다.**</span><span class="sxs-lookup"><span data-stu-id="e2057-179">**A knowledge base that represents three types of knowledge: out-of-the-box knowledge, knowledge generated by the DQS server, and knowledge generated by the user.**</span></span>  
 <span data-ttu-id="e2057-180">기술 자료를 만들면 이 자료를 반복적으로 사용하여 다른 데이터를 정리 및 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e2057-180">Once you have created a knowledge base, you can use it iteratively to cleanse and verify other data.</span></span>  
  
 <span data-ttu-id="e2057-181">여러 원본에서 새 데이터를 기술 자료 데이터로 가져올 수 있습니다. 참조 공급자가 제공하는 알려진 정리된 데이터 또는 기술 자료의 기존 데이터와 일치하는 원시 데이터가 여기에 해당합니다.</span><span class="sxs-lookup"><span data-stu-id="e2057-181">You can import new data into the knowledge base data from multiple sources, either known clean data from reference providers, or raw data that is matched to existing data in the knowledge base.</span></span>  
  
 <span data-ttu-id="e2057-182">데이터 품질 프로젝트의 정리 동작에 대한 자세한 내용은 데이터 정리(DQS)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="e2057-182">For detailed information about the cleansing activity in a data quality project, see Data Cleansing (DQS).</span></span>  
  
 <span data-ttu-id="e2057-183">기술 자료의 정보를 다른 원본에 적용하여 다른 프로세스 내부에서 데이터 정리를 수행할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e2057-183">You can also apply the knowledge in the knowledge base to other sources, to perform data cleansing within other processes.</span></span> <span data-ttu-id="e2057-184">이러한 데이터 정리를 통해 사용자 입력 오류, 전송 또는 스토리지 과정의 손상 또는 일치하지 않는 데이터 사전 정의를 식별할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e2057-184">Such data cleansing can help identify user entry errors, corruption in transmission or storage, or mismatched data dictionary definitions.</span></span>  
  
 <span data-ttu-id="e2057-185">자세한 내용은 [DQS Knowledge Bases and Domains](../../data-quality-services/dqs-knowledge-bases-and-domains.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e2057-185">For more information, see [DQS Knowledge Bases and Domains](../../data-quality-services/dqs-knowledge-bases-and-domains.md).</span></span>  
  
##  <a name="full-text-search"></a><a name="bkmk_FTSetc"></a><span data-ttu-id="e2057-186">전체 텍스트 검색</span><span class="sxs-lookup"><span data-stu-id="e2057-186">Full-Text Search</span></span>  
 <span data-ttu-id="e2057-187">SQL Server의 전체 텍스트 검색을 사용하면 애플리케이션과 사용자가 SQL Server 테이블의 문자 기반 데이터에 대해 전체 텍스트 쿼리를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e2057-187">Full-Text Search in SQL Server lets applications and users run full-text queries against character-based data in SQL Server tables.</span></span> <span data-ttu-id="e2057-188">전체 텍스트 검색을 사용하면 여러 가지 형태의 단어 또는 구에 대한 언어별 규칙에 의해 개선된 텍스트 데이터에 대해 검색을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e2057-188">When full-text search is enabled, you can perform searches against text data that are enhanced by language-specific rules about the multiple forms of a word or phrase.</span></span> <span data-ttu-id="e2057-189">여러 용어 간 거리 등과 같은 검색 조건을 구성하고 가능성 순서로 반환된 결과를 제한하는 함수를 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e2057-189">You can also configure search conditions, such as the distance between multiple terms, and use functions to constrain the results that are returned in order of likelihood.</span></span>  
  
 <span data-ttu-id="e2057-190">전체 텍스트 쿼리는 SQL Server 엔진에서 제공하는 기능이기 때문에 매개 변수가 있는 쿼리를 만들고, 텍스트 데이터 원본에서 전체 텍스트 검색 기능을 사용하여 사용자 지정 데이터 집합 또는 용어 벡터를 생성하고, 데이터 마이닝에 이러한 원본을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e2057-190">Because full-text queries are a feature provided by the SQL Server engine, you can create parameterized queries, generate custom data sets or term vectors by using full-text search features on a text data source, and use these sources in data mining.</span></span>  
  
 <span data-ttu-id="e2057-191">전체 텍스트 쿼리가 전체 텍스트 인덱스와 상호 작용하는 방식은 [전체 텍스트 검색을 사용한 쿼리](../../relational-databases/search/query-with-full-text-search.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e2057-191">For more information about how full-text queries interact with the full-text index, see [Query with Full-Text Search](../../relational-databases/search/query-with-full-text-search.md).</span></span>  
  
 <span data-ttu-id="e2057-192">SQL Server의 전체 텍스트 검색 기능을 사용하면 모든 SQL Server 언어에 대해 제공되는 단어 분리기 및 형태소 분석기에 포함된 언어적 지능을 활용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e2057-192">An advantage of using the full-text search features of SQL Server is that you can leverage the linguistic intelligence that is contained in the word breakers and stemmers shipped for all SQL Server languages.</span></span> <span data-ttu-id="e2057-193">제공된 단어 분리기 및 형태소 분석기를 사용하면 단어가 각 언어에 적합한 문자를 사용하여 분리되고 분음 기호 또는 철자 변형 기준 동의어(예: 일본어의 다중 숫자 형식)가 무시되지 않도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e2057-193">By using the supplied word breakers and stemmers, you can ensure that words are separated using the characters appropriate for each language, and that synonyms based on diacritics or orthographic variations (such as the multiple number formats in Japanese) are not overlooked.</span></span>  
  
 <span data-ttu-id="e2057-194">단어의 경계를 제어하는 언어적 지능 외에도 각 언어의 형태소 분석기는 해당 언어의 활용 및 철자 변형 규칙에 대한 정보를 기반으로 다양한 단어 변형을 단일 용어로 축소할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e2057-194">In addition to linguistic intelligence that governs word boundaries, the stemmers for each language can reduce variants of a word to a single term, based on knowledge of the rules for conjugation and orthographic variation in that language.</span></span> <span data-ttu-id="e2057-195">언어 분석에 대한 규칙은 언어마다 다르며 실제 언어 자료에 대한 광범위한 연구를 기반으로 개발됩니다.</span><span class="sxs-lookup"><span data-stu-id="e2057-195">The rules for linguistic analysis differ for each language and are developed based on extensive research on real-life corpora.</span></span>  
  
 <span data-ttu-id="e2057-196">자세한 내용은 [검색을 위해 단어 분리기와 형태소 분석기 구성 및 관리](../../relational-databases/search/configure-and-manage-word-breakers-and-stemmers-for-search.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e2057-196">For more information, see [Configure and Manage Word Breakers and Stemmers for Search](../../relational-databases/search/configure-and-manage-word-breakers-and-stemmers-for-search.md).</span></span>  
  
 <span data-ttu-id="e2057-197">전체 텍스트 인덱싱 후 저장되는 단어의 버전은 압축된 형식의 토큰입니다.</span><span class="sxs-lookup"><span data-stu-id="e2057-197">The version of a word that is stored after full-text indexing is a token in compressed form.</span></span> <span data-ttu-id="e2057-198">전체 텍스트 인덱스에 대한 후속 쿼리가 수행됨에 따라 가능성 있는 모든 일치 항목을 찾을 수 있도록 해당 언어의 규칙에 따라 특정 단어의 여러 굴절형이 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="e2057-198">Subsequent queries to the full-text index generate multiple inflectional forms of a particular word based on the rules of that language, to ensure that all probable matches are made.</span></span> <span data-ttu-id="e2057-199">예를 들어 저장 된 토큰은 "run"이 될 수 있지만 쿼리 엔진은 "실행 중", "실행 됨" 및 "runner" 라는 용어를 검색 합니다 .이는 루트 단어 "형태학 상의 변형인"의 변형에 의해 정기적으로 파생 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e2057-199">For example, although the token that is stored might be "run", the query engine also looks for the terms "running", "ran", and "runner," because these are regularly derived morphological variations of the root word "run".</span></span>  
  
 <span data-ttu-id="e2057-200">사용자 동의어 사전을 만들어 검색 결과를 향상시키거나 용어 범주화를 작성할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e2057-200">You can also create and build a user thesaurus to store synonyms and enable better search results, or categorization of terms.</span></span> <span data-ttu-id="e2057-201">전체 텍스트 데이터에 맞게 동의어 사전을 개발하면 해당 데이터에 대한 전체 텍스트 쿼리의 범위를 효과적으로 넓힐 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e2057-201">By developing a thesaurus tailored to your full-text data, you can effectively broaden the scope of full-text queries on that data.</span></span> <span data-ttu-id="e2057-202">자세한 내용은 [전체 텍스트 검색에 사용할 동의어 사전 파일 구성 및 관리](../../relational-databases/search/configure-and-manage-thesaurus-files-for-full-text-search.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e2057-202">For more information, see [Configure and Manage Thesaurus Files for Full-Text Search](../../relational-databases/search/configure-and-manage-thesaurus-files-for-full-text-search.md).</span></span>  
  
 <span data-ttu-id="e2057-203">전체 텍스트 검색을 사용하는 데 필요한 요구 사항은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="e2057-203">Requirements for using full-text search include the following:</span></span>  
  
-   <span data-ttu-id="e2057-204">데이터베이스 관리자가 해당 테이블에 대한 전체 텍스트 인덱스를 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e2057-204">The database administrator must create a full-text index on the table.</span></span>  
  
-   <span data-ttu-id="e2057-205">테이블당 한 개의 전체 텍스트 인덱스만 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="e2057-205">Only one full-text index is allowed per table.</span></span>  
  
-   <span data-ttu-id="e2057-206">인덱스에 포함되는 각 열은 고유 키를 가지고 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e2057-206">Each column that you index must have a unique key.</span></span>  
  
-   <span data-ttu-id="e2057-207">데이터 형식이 char, varchar, nchar, nvarchar, text, ntext, image, xml, varbinary, varbinary(max) 등인 열에 대해서만 전체 텍스트 인덱싱이 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="e2057-207">Full-text indexing is supported only for columns with these data types: char, varchar, nchar, nvarchar, text, ntext, image, xml, varbinary, and varbinary(max).</span></span> <span data-ttu-id="e2057-208">열이 varbinary, varbinary(max), image 또는 xml이면 별도의 유형 열에 인덱싱 가능한 문서의 파일 확장명(.doc, .pdf, .xls 등)을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e2057-208">If the column is varbinary, varbinary(max), image, or xml, you must specify the file extension of the indexable document (.doc, .pdf, .xls, and so forth), in a separate type column.</span></span>  
  
##  <a name="semantic-indexing"></a><a name="bkmk_SemSearch"></a><span data-ttu-id="e2057-209">의미 체계 인덱싱</span><span class="sxs-lookup"><span data-stu-id="e2057-209">Semantic Indexing</span></span>  
 <span data-ttu-id="e2057-210">의미 체계 검색은 SQL Server의 기존 전체 텍스트 검색 기능을 기반으로 구축되지만 자동 키워드 추출 및 관련 문서 검색 등의 시나리오를 사용할 수 있도록 추가 기능 및 통계를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="e2057-210">Semantic search builds upon the existing full-text search features in SQL Server, but uses additional capabilities and statistics to enable scenarios such as automatic keyword extraction and discovery of related documents.</span></span> <span data-ttu-id="e2057-211">예를 들어 의미 체계 검색을 사용하여 조직에 대한 기본 분류를 작성하거나 문서 모음을 분류할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e2057-211">For example, you might use semantic search to build a base taxonomy for an organization, or classify a corpus of documents.</span></span> <span data-ttu-id="e2057-212">추출된 용어 및 문서 유사성 점수 조합을 클러스터링 또는 의사 결정 트리 모델에서 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e2057-212">Or, you could use the combination of extracted terms and document similarity scores in clustering or decision tree models.</span></span>  
  
 <span data-ttu-id="e2057-213">의미 체계 검색을 설정하고 데이터 열에 인덱스를 지정한 후 의미 체계 인덱싱에 기본적으로 제공되는 기능을 사용하여 다음과 같은 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e2057-213">After you have enabled semantic search successfully, and indexed your data columns, you can use the functions that are provided natively with semantic indexing to do the following:</span></span>  
  
-   <span data-ttu-id="e2057-214">단일 단어 키 구를 해당 점수와 함께 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="e2057-214">Return single-word key phrases with their score.</span></span>  
  
-   <span data-ttu-id="e2057-215">지정된 키 구가 포함된 문서를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="e2057-215">Return documents that contain a specified key phrase.</span></span>  
  
-   <span data-ttu-id="e2057-216">유사성 점수와 해당 점수에 기여하는 용어를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="e2057-216">Return similarity scores, and the terms that contribute to the score.</span></span>  
  
 <span data-ttu-id="e2057-217">자세한 내용은 [의미 체계 검색을 사용하여 문서의 키 구 찾기](../../relational-databases/search/find-key-phrases-in-documents-with-semantic-search.md) 및 [의미 체계 검색을 사용하여 유사하거나 관련된 문서 찾기](../../relational-databases/search/find-similar-and-related-documents-with-semantic-search.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e2057-217">For more information, see [Find Key Phrases in Documents with Semantic Search](../../relational-databases/search/find-key-phrases-in-documents-with-semantic-search.md) and [Find Similar and Related Documents with Semantic Search](../../relational-databases/search/find-similar-and-related-documents-with-semantic-search.md).</span></span>  
  
 <span data-ttu-id="e2057-218">의미 체계 인덱싱을 지원하는 데이터베이스 개체에 대한 자세한 내용은 [테이블 및 열에 대한 의미 체계 검색 사용](../../relational-databases/search/enable-semantic-search-on-tables-and-columns.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e2057-218">For more information about the database objects that support semantic indexing, see [Enable Semantic Search on Tables and Columns](../../relational-databases/search/enable-semantic-search-on-tables-and-columns.md).</span></span>  
  
 <span data-ttu-id="e2057-219">의미 체계 검색을 사용하는 데 필요한 요구 사항은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="e2057-219">Requirements for using semantic search include the following:</span></span>  
  
-   <span data-ttu-id="e2057-220">전체 텍스트 검색도 사용하도록 설정되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e2057-220">Full-text search also be enabled.</span></span>  
  
-   <span data-ttu-id="e2057-221">의미 체계 검색 구성 요소를 설치하면 이름을 바꾸거나 변경하거나 교체할 수 없는 특수 시스템 데이터베이스도 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="e2057-221">Installation of the semantic search components also creates a special system database, which cannot be renamed, altered, or replaced.</span></span>  
  
-   <span data-ttu-id="e2057-222">해당 서비스를 사용하여 인덱싱하는 문서는 SQL Server에서 테이블 및 인덱싱된 뷰와 같이 전체 텍스트 인덱싱이 지원되는 데이터베이스 개체에 저장되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e2057-222">Documents that you index using the service must be stored in SQL Server, in any of the database objects that are supported for full-text indexing, including tables and indexed views.</span></span>  
  
-   <span data-ttu-id="e2057-223">일부 전체 텍스트 언어는 의미 체계 인덱싱을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e2057-223">Not all of the full-text languages support semantic indexing.</span></span> <span data-ttu-id="e2057-224">지원되는 언어 목록을 보려면 [sys.fulltext_languages&#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-semantic-languages-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e2057-224">For a list of supported languages, see [sys.fulltext_semantic_languages &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-semantic-languages-transact-sql).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2057-225">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e2057-225">See Also</span></span>  
 <span data-ttu-id="e2057-226">[SSAS&#41;&#40;다차원 모델 솔루션](../multidimensional-models/multidimensional-model-solutions-ssas.md) </span><span class="sxs-lookup"><span data-stu-id="e2057-226">[Multidimensional Model Solutions &#40;SSAS&#41;](../multidimensional-models/multidimensional-model-solutions-ssas.md) </span></span>  
 [<span data-ttu-id="e2057-227">테이블 형식 모델 솔루션&#40;SSAS 테이블 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="e2057-227">Tabular Model Solutions &#40;SSAS Tabular&#41;</span></span>](../tabular-model-solutions-ssas-tabular.md)  
  
  
