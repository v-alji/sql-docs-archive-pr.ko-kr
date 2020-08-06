---
title: Reporting Services 쿼리 디자이너 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- query designers [Reporting Services]
ms.assetid: 07efd3f1-804f-45f7-b62a-3e727a3d9835
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 4febd0b0e0bf028d16aa3ef13ce4294feb930072
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734951"
---
# <a name="reporting-services-query-designers"></a><span data-ttu-id="778d5-102">Reporting Services 쿼리 디자이너</span><span class="sxs-lookup"><span data-stu-id="778d5-102">Reporting Services Query Designers</span></span>
  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]<span data-ttu-id="778d5-103">는 보고서의 각 데이터 원본 유형에 대 한 쿼리를 작성 하는 데 도움이 되는 그래픽 및 텍스트 기반 쿼리 디자이너를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="778d5-103">provides graphical and text-based query designers to help you build queries for each data source type in your report.</span></span>  
  
 <span data-ttu-id="778d5-104">일부 데이터 원본은 쿼리를 대화형으로 작성하는 데 도움이 되는 그래픽 디자이너를 지원하고</span><span class="sxs-lookup"><span data-stu-id="778d5-104">Some data sources support graphical designers that help you build a query interactively.</span></span> <span data-ttu-id="778d5-105">다른 데이터 원본은 텍스트 기반 쿼리 디자이너를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="778d5-105">Other data sources use a text-based query designer.</span></span> <span data-ttu-id="778d5-106">그래픽 쿼리 디자이너를 사용하면 데이터 원본에서 기본 데이터를 나타내는 메타데이터 항목을 쿼리 디자인 화면으로 끌 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="778d5-106">By using a graphical query designer, you can drag metadata items that represent the underlying data on a data source to the query design surface.</span></span> <span data-ttu-id="778d5-107">텍스트 기반 쿼리 디자이너를 사용하면 쿼리 창에 명령 텍스트를 입력할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="778d5-107">By using a text-based query designer, you can type command text into a query pane.</span></span> <span data-ttu-id="778d5-108">도구 모음의 텍스트 기반 쿼리 디자이너 아이콘을 클릭하여 그래픽 쿼리 디자이너에서 텍스트 기반 쿼리 디자이너로 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="778d5-108">You can change from a graphical query designer to a text-based query designer by clicking the text-based query designer icon on the toolbar.</span></span>  
  
 <span data-ttu-id="778d5-109">보고서에 사용할 수 있는 데이터 원본 유형은 클라이언트 또는 보고서 서버에 설치된 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 데이터 확장 프로그램에 따라 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="778d5-109">The data source types that are available in your report are determined by the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] data extensions installed on your client or report server.</span></span> <span data-ttu-id="778d5-110">자세한 내용은 [RSReportDesigner Configuration File](report-server/rsreportdesigner-configuration-file.md) 및 [RSReportServer Configuration File](report-server/rsreportserver-config-configuration-file.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="778d5-110">For more information, see [RSReportDesigner Configuration File](report-server/rsreportdesigner-configuration-file.md) and [RSReportServer Configuration File](report-server/rsreportserver-config-configuration-file.md).</span></span>  
  
 <span data-ttu-id="778d5-111">데이터 처리 확장 프로그램 및 연결된 쿼리 디자이너는 데이터 원본에 대한 지원이 다음과 같이 서로 다를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="778d5-111">A data processing extension and its associated query designer can differ in support for data sources in the following ways:</span></span>  
  
-   <span data-ttu-id="778d5-112">**쿼리 디자이너 유형별.**</span><span class="sxs-lookup"><span data-stu-id="778d5-112">**By query designer type.**</span></span> <span data-ttu-id="778d5-113">예를 들어 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 데이터 원본은 그래픽 기반 쿼리 디자이너와 텍스트 기반 쿼리 디자이너를 모두 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="778d5-113">For example, a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] data source supports both the graphical and text-based query designers.</span></span>  
  
-   <span data-ttu-id="778d5-114">**쿼리 언어 변형별.**</span><span class="sxs-lookup"><span data-stu-id="778d5-114">**By query language variation.**</span></span> <span data-ttu-id="778d5-115">예를 들어 [!INCLUDE[tsql](../includes/tsql-md.md)] 과 같은 쿼리 언어는 데이터 원본 유형에 따라 구문이 달라질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="778d5-115">For example, a query language such as [!INCLUDE[tsql](../includes/tsql-md.md)] can differ in syntax depending on the data source type.</span></span> <span data-ttu-id="778d5-116">[!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[tsql](../includes/tsql-md.md)] 언어 및 Oracle SQL 언어는 쿼리 명령 구문에 몇 가지 변형이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="778d5-116">The [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[tsql](../includes/tsql-md.md)] language and the Oracle SQL language have some variation in syntax for a query command.</span></span>  
  
-   <span data-ttu-id="778d5-117">**데이터베이스 개체 이름의 스키마 부분 지원별.**</span><span class="sxs-lookup"><span data-stu-id="778d5-117">**By support for the schema part of a database object name.**</span></span> <span data-ttu-id="778d5-118">데이터 원본에서 스키마를 데이터베이스 개체 식별자의 일부로 사용하는 경우 기본 스키마를 사용하지 않는 모든 이름에 대해 스키마 이름을 쿼리의 일부로 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="778d5-118">When a data source uses schemas as part of the database object identifier, the schema name must be supplied as part of the query for any names that do not use the default schema.</span></span> <span data-ttu-id="778d5-119">예들 들어 `SELECT FirstName, LastName FROM [Person].[Person]`입니다.</span><span class="sxs-lookup"><span data-stu-id="778d5-119">For example, `SELECT FirstName, LastName FROM [Person].[Person]`.</span></span>  
  
-   <span data-ttu-id="778d5-120">**쿼리 매개 변수 지원별.**</span><span class="sxs-lookup"><span data-stu-id="778d5-120">**By support for query parameters.**</span></span> <span data-ttu-id="778d5-121">데이터 공급자에 따라 매개 변수 지원이 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="778d5-121">Data providers differ in support for parameters.</span></span> <span data-ttu-id="778d5-122">일부 데이터 공급자는 명명된 매개 변수(예: `SELECT Col1, Col2 FROM Table WHERE <parameter identifier><parameter name> = <value>`)를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="778d5-122">Some data providers support named parameters; for example, `SELECT Col1, Col2 FROM Table WHERE <parameter identifier><parameter name> = <value>`.</span></span> <span data-ttu-id="778d5-123">다른 데이터 공급자는 명명되지 않은 매개 변수(예: `SELECT Col1, Col2 FROM Table WHERE <column name> = ?`)를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="778d5-123">Some data providers support unnamed parameters; for example, `SELECT Col1, Col2 FROM Table WHERE <column name> = ?`.</span></span> <span data-ttu-id="778d5-124">데이터 공급자에 따라 매개 변수 식별자가 달라질 수 있습니다. 예를 들어 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 는 @ 기호를 사용하고 Oracle은 콜론(:)을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="778d5-124">The parameter identifier might differ by data provider; for example, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] uses the "at" (@) symbol, Oracle uses the colon (:).</span></span> <span data-ttu-id="778d5-125">매개 변수를 지원하지 않는 데이터 공급자도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="778d5-125">Some data providers do not support parameters.</span></span>  
  
-   <span data-ttu-id="778d5-126">**쿼리 가져오기 기능별.**</span><span class="sxs-lookup"><span data-stu-id="778d5-126">**By ability to import queries.**</span></span> <span data-ttu-id="778d5-127">예를 들어 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 데이터 원본의 경우 보고서 정의 파일(.rdl) 또는 .sql 파일에서 쿼리를 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="778d5-127">For example, for a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] data source, you can import a query from a report definition file (.rdl) or from a .sql file.</span></span>  
  
## <a name="query-designers"></a><span data-ttu-id="778d5-128">쿼리 디자이너</span><span class="sxs-lookup"><span data-stu-id="778d5-128">Query Designers</span></span>  
 <span data-ttu-id="778d5-129">다음 항목에서는 각 쿼리 디자이너의 사용자 인터페이스에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="778d5-129">The following topics describe the user interface for each query designer.</span></span>  
  
-   [<span data-ttu-id="778d5-130">Analysis Services MDX 쿼리 디자이너 사용자 인터페이스</span><span class="sxs-lookup"><span data-stu-id="778d5-130">Analysis Services MDX Query Designer User Interface</span></span>](report-data/analysis-services-mdx-query-designer-user-interface.md)  
  
-   [<span data-ttu-id="778d5-131">Analysis Services DMX 쿼리 디자이너 사용자 인터페이스</span><span class="sxs-lookup"><span data-stu-id="778d5-131">Analysis Services DMX Query Designer User Interface</span></span>](report-data/analysis-services-dmx-query-designer-user-interface.md)  
  
-   [<span data-ttu-id="778d5-132">그래픽 쿼리 디자이너 사용자 인터페이스</span><span class="sxs-lookup"><span data-stu-id="778d5-132">Graphical Query Designer User Interface</span></span>](report-data/graphical-query-designer-user-interface.md)  
  
-   [<span data-ttu-id="778d5-133">관계형 쿼리 디자이너 사용자 인터페이스</span><span class="sxs-lookup"><span data-stu-id="778d5-133">Relational Query Designer User Interface</span></span>](../../2014/reporting-services/relational-query-designer-user-interface.md)  
  
-   [<span data-ttu-id="778d5-134">Hyperion Essbase 쿼리 디자이너 사용자 인터페이스</span><span class="sxs-lookup"><span data-stu-id="778d5-134">Hyperion Essbase Query Designer User Interface</span></span>](report-data/hyperion-essbase-query-designer-user-interface.md)  
  
-   [<span data-ttu-id="778d5-135">보고서 모델 쿼리 디자이너 사용자 인터페이스</span><span class="sxs-lookup"><span data-stu-id="778d5-135">Report Model Query Designer User Interface</span></span>](report-data/report-model-query-designer-user-interface.md)  
  
-   [<span data-ttu-id="778d5-136">SAP NetWeaver BI 쿼리 디자이너 사용자 인터페이스</span><span class="sxs-lookup"><span data-stu-id="778d5-136">SAP NetWeaver BI Query Designer User Interface</span></span>](report-data/sap-netweaver-bi-query-designer-user-interface.md)  
  
-   [<span data-ttu-id="778d5-137">SharePoint 목록 쿼리 디자이너</span><span class="sxs-lookup"><span data-stu-id="778d5-137">SharePoint List Query Designer</span></span>](../../2014/reporting-services/sharepoint-list-query-designer.md)  
  
-   [<span data-ttu-id="778d5-138">텍스트 기반 쿼리 디자이너 사용자 인터페이스</span><span class="sxs-lookup"><span data-stu-id="778d5-138">Text-based Query Designer User Interface</span></span>](../../2014/reporting-services/text-based-query-designer-user-interface.md)  
  
## <a name="see-also"></a><span data-ttu-id="778d5-139">참고 항목</span><span class="sxs-lookup"><span data-stu-id="778d5-139">See Also</span></span>  
 <span data-ttu-id="778d5-140">[Reporting Services &#40;SSRS&#41;에서 지 원하는 데이터 원본](create-deploy-and-manage-mobile-and-paginated-reports.md) </span><span class="sxs-lookup"><span data-stu-id="778d5-140">[Data Sources Supported by Reporting Services &#40;SSRS&#41;](create-deploy-and-manage-mobile-and-paginated-reports.md) </span></span>  
 <span data-ttu-id="778d5-141">[SSRS&#41;&#40;외부 데이터 원본의 데이터 추가](report-data/add-data-from-external-data-sources-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="778d5-141">[Add Data from External Data Sources &#40;SSRS&#41;](report-data/add-data-from-external-data-sources-ssrs.md) </span></span>  
 <span data-ttu-id="778d5-142">[데이터 처리 확장 프로그램 및 .NET Framework 데이터 공급자 &#40;SSRS&#41;](report-data/data-processing-extensions-and-net-framework-data-providers-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="778d5-142">[Data Processing Extensions and .NET Framework Data Providers &#40;SSRS&#41;](report-data/data-processing-extensions-and-net-framework-data-providers-ssrs.md) </span></span>  
 [<span data-ttu-id="778d5-143">확장 프로그램&#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="778d5-143">Extensions &#40;SSRS&#41;</span></span>](extensions-ssrs.md)  
  
  
