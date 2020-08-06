---
title: PowerPivot 연결 형식 (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: a104c3c7-f118-4d02-9a0f-6859f1469d11
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 08ce995afa7d458e8ce3ae50a9f572a086a3c697
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742860"
---
# <a name="powerpivot-connection-type-ssrs"></a><span data-ttu-id="95972-102">PowerPivot 연결 유형(SSRS)</span><span class="sxs-lookup"><span data-stu-id="95972-102">PowerPivot Connection Type (SSRS)</span></span>
  <span data-ttu-id="95972-103">SQL Server Analysis Services 데이터 처리 확장 프로그램을 사용하면 SharePoint PowerPivot 갤러리에 게시된 PowerPivot 통합 문서에서 데이터를 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="95972-103">You can use SQL Server Analysis Services data processing extension to retrieve data from a PowerPivot workbook that is published in a SharePoint PowerPivot Gallery.</span></span>  
  
 <span data-ttu-id="95972-104">이 항목의 정보를 사용하여 데이터 원본을 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="95972-104">Use the information in this topic to build a data source.</span></span> <span data-ttu-id="95972-105">단계별 지침은 [데이터 연결이 나 데이터 원본 &#40;추가 및 확인 보고서 작성기 및 SSRS&#41;](add-and-verify-a-data-connection-report-builder-and-ssrs.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="95972-105">For step-by-step instructions, see [Add and Verify a Data Connection or Data Source &#40;Report Builder and SSRS&#41;](add-and-verify-a-data-connection-report-builder-and-ssrs.md).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="95972-106">사전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="95972-106">Prerequisites</span></span>  
 <span data-ttu-id="95972-107">PowerPivot 데이터 원본은 SharePoint 사이트의 PowerPivot 갤러리에 게시되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="95972-107">The PowerPivot data source must be published in a PowerPivot Gallery on a SharePoint site.</span></span>  
  
 <span data-ttu-id="95972-108">보고서 작성기에서 PowerPivot 통합 문서로의 연결을 지원하려면 워크스테이션 컴퓨터에 SQL Server 2008 R2 ADOMD.NET이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="95972-108">To support connections from Report Builder to a PowerPivot workbook, you must have SQL Server 2008 R2 ADOMD.NET on your workstation computer.</span></span> <span data-ttu-id="95972-109">이 클라이언트 라이브러리는 PowerPivot for Excel과 함께 설치되지만 이 애플리케이션이 없는 컴퓨터를 사용하는 경우에는 [SQL Server 2008 R2 기능 팩](https://www.microsoft.com/download/details.aspx?id=44272)에서 ADOMD.NET을 다운로드하여 설치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="95972-109">This client library is installed with PowerPivot for Excel, but if you are using a computer that does not have this application, you must download and install ADOMD.NET from the [SQL Server 2008 R2 Feature Pack](https://www.microsoft.com/download/details.aspx?id=44272).</span></span>  
  
## <a name="data-source-type"></a><span data-ttu-id="95972-110">데이터 원본 유형</span><span class="sxs-lookup"><span data-stu-id="95972-110">Data Source Type</span></span>  
 <span data-ttu-id="95972-111">보고서 데이터 원본 유형 **Microsoft SQL Server Analysis Services**를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="95972-111">Use report data source type **Microsoft SQL Server Analysis Services**.</span></span>  
  
## <a name="connection-string"></a><span data-ttu-id="95972-112">연결 문자열</span><span class="sxs-lookup"><span data-stu-id="95972-112">Connection String</span></span>  
 <span data-ttu-id="95972-113">연결 문자열은 PowerPivot 갤러리 또는 다른 라이브러리의 SharePoint에 게시 된 PowerPivot 통합 문서에 대 한 URL입니다 (예:) http://contoso-srv/subsite/PowerPivotLibrary/ContosoSales.xlsx .</span><span class="sxs-lookup"><span data-stu-id="95972-113">The connection string is the URL to PowerPivot workbook published on SharePoint in the PowerPivot Gallery or other library, for example, http://contoso-srv/subsite/PowerPivotLibrary/ContosoSales.xlsx.</span></span>  
  
## <a name="credentials"></a><span data-ttu-id="95972-114">자격 증명</span><span class="sxs-lookup"><span data-stu-id="95972-114">Credentials</span></span>  
 <span data-ttu-id="95972-115">PowerPivot 통합 문서 및 SharePoint 사이트에 액세스하는 데 필요한 자격 증명을 지정합니다. 예를 들어 Windows 인증(통합 보안)을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="95972-115">Specify the credentials that you need to access the PowerPivot workbook and SharePoint site, for example, Windows Authentication (Integrated Security).</span></span> <span data-ttu-id="95972-116">자세한 내용은 [Reporting Services의 데이터 연결, 데이터 원본 및 연결 문자열](../data-connections-data-sources-and-connection-strings-in-reporting-services.md) 을 참조 하거나 [보고서 작성기에서 자격 증명을 지정](../specify-credentials-in-report-builder.md)하세요.</span><span class="sxs-lookup"><span data-stu-id="95972-116">For more information, see [Data Connections, Data Sources, and Connection Strings in Reporting Services](../data-connections-data-sources-and-connection-strings-in-reporting-services.md) or [Specify Credentials in Report Builder](../specify-credentials-in-report-builder.md).</span></span>  
  
## <a name="queries"></a><span data-ttu-id="95972-117">쿼리</span><span class="sxs-lookup"><span data-stu-id="95972-117">Queries</span></span>  
 <span data-ttu-id="95972-118">PowerPivot 데이터 원본에 연결한 후 MDX 그래픽 쿼리를 통해 기본 데이터 구조에서 찾아보고 선택하여 쿼리를 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="95972-118">After you connect to the PowerPivot data source, use the MDX graphical query to build a query by browsing and selecting from the underlying data structures.</span></span> <span data-ttu-id="95972-119">쿼리를 작성한 후에는 해당 쿼리를 실행하여 결과 창에서 예제 데이터를 봅니다.</span><span class="sxs-lookup"><span data-stu-id="95972-119">After you build a query, run the query to see sample data in the results pane.</span></span>  
  
 <span data-ttu-id="95972-120">쿼리 디자이너는 쿼리를 분석하여 데이터 세트 필드를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="95972-120">The query designer analyzes the query to determine the dataset fields.</span></span> <span data-ttu-id="95972-121">**보고서 데이터** 창에서 데이터 세트 필드 컬렉션을 수동으로 편집할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="95972-121">You can also manually edit the dataset field collection in the **Report Data** pane.</span></span> <span data-ttu-id="95972-122">자세한 내용은 [보고서 데이터 창에서 필드 추가, 편집, 새로 고침&#40;보고서 작성기 및 SSRS&#41;](add-edit-refresh-fields-in-the-report-data-pane-report-builder-and-ssrs.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="95972-122">For more information, see [Add, Edit, Refresh Fields in the Report Data Pane &#40;Report Builder and SSRS&#41;](add-edit-refresh-fields-in-the-report-data-pane-report-builder-and-ssrs.md).</span></span>  
  
## <a name="filters"></a><span data-ttu-id="95972-123">필터</span><span class="sxs-lookup"><span data-stu-id="95972-123">Filters</span></span>  
 <span data-ttu-id="95972-124">필터 창에서 쿼리 결과에 포함하거나 필터링하여 제외할 차원 및 멤버를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="95972-124">In the Filters pane, specify dimensions and members to filter out or to include in the query results.</span></span>  
  
## <a name="parameters"></a><span data-ttu-id="95972-125">매개 변수</span><span class="sxs-lookup"><span data-stu-id="95972-125">Parameters</span></span>  
 <span data-ttu-id="95972-126">필터 창에서 필터 선택 사항에 해당되는 사용 가능한 값을 사용하여 자동으로 보고서 매개 변수를 만드는 필터에 대한 **매개 변수** 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="95972-126">In the Filters pane, select the **Parameters** option for a filter to automatically create a report parameter with available values that correspond to the filter selections.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="95972-127">설명</span><span class="sxs-lookup"><span data-stu-id="95972-127">Remarks</span></span>  
 <span data-ttu-id="95972-128">PowerPivot 갤러리의 PowerPivot 통합 문서에서 보고서 작성기를 여는 경우 PowerPivot 통합 문서의 피벗 테이블, 피벗 차트, 슬라이서 및 기타 레이아웃과 분석 기능은 보고서에서 다시 생성되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="95972-128">If you open Report Builder from the PowerPivot workbook in a PowerPivot Gallery, the PivotTables, PivotCharts, slicers, and other layout and analytical features from the PowerPivot workbook are not re-created in the report.</span></span> <span data-ttu-id="95972-129">대신 빈 보고서는 PowerPivot 통합 문서의 데이터를 가리키는 미리 구성된 데이터 원본을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="95972-129">Instead, the blank report includes a preconfigured data source that points to the data in the PowerPivot workbook.</span></span> <span data-ttu-id="95972-130">PowerPivot 통합 문서를 기준으로 보고서를 디자인하는 작업은 보고서에서 다시 만들 슬라이서, 필터 및 테이블 또는 차트 수에 따라 복잡하고 시간이 많이 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="95972-130">Designing reports based on a PowerPivot workbook can be labor-intensive and time-consuming depending on the number of slicers, filters, and tables or charts that you want to re-create in the report.</span></span> <span data-ttu-id="95972-131">따라서 PowerPivot 디자인과 독립적으로 보고서에 포함하려는 데이터의 표현을 상상해 보는 것이 더 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="95972-131">A better approach is to envision the presentation of the data that you want in a report independently from the PowerPivot design.</span></span>  
  
 <span data-ttu-id="95972-132">PowerPivot 통합 문서의 데이터는 고도로 압축되어 있으며 보고서에 대해 PowerPivot 통합 문서에서 검색된 데이터는 압축되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="95972-132">The data in a PowerPivot workbook is highly compressed; data retrieved from the PowerPivot workbook for a report is not compressed.</span></span> <span data-ttu-id="95972-133">쿼리 디자이너를 사용하여 보고서에 필요한 데이터만 포함되도록 제한할 필터 및 매개 변수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="95972-133">Use the query designer to specify filters and parameters to limit the data to just what is needed in the report.</span></span>  
  
 <span data-ttu-id="95972-134">Analysis Services 큐브에 연결하는 것과 달리 PowerPivot 모델에는 계층이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="95972-134">Unlike connecting to an Analysis Services cube, a PowerPivot model has no hierarchies.</span></span> <span data-ttu-id="95972-135">통합 문서의 관련 슬라이서에 유사한 기능을 제공하려면 보고서에서 연계된 매개 변수를 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="95972-135">To provide similar functionality to related slicers in the workbook, you must create cascading parameters in the report.</span></span> <span data-ttu-id="95972-136">자세한 내용은 [보고서에 연계 매개 변수 추가&#40;보고서 작성기 및 SSRS&#41;](../report-design/add-cascading-parameters-to-a-report-report-builder-and-ssrs.md)에서 만드는 모바일 보고서에서 보고서 매개 변수를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="95972-136">For more information, see [Add Cascading Parameters to a Report &#40;Report Builder and SSRS&#41;](../report-design/add-cascading-parameters-to-a-report-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="95972-137">일부 경우에는 PowerPivot 모델의 기본 데이터 값을 수용하도록 식을 조정해야 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="95972-137">In some cases, you might need to adjust expressions to accommodate the underlying data values from the PowerPivot model.</span></span> <span data-ttu-id="95972-138">데이터를 올바른 데이터 형식으로 변환하거나 집계 함수를 추가 또는 제거하도록 식을 수정해야 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="95972-138">You might need to modify expressions to convert data to the right data type or to add or remove an aggregate function.</span></span> <span data-ttu-id="95972-139">예를 들어 데이터 형식을 String에서 Integer로 변환하려면 `=CInt`를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="95972-139">For example, to convert data type from String to Integer, use `=CInt`.</span></span> <span data-ttu-id="95972-140">보고서를 게시하기 전에 PowerPivot 모델의 데이터에서 원하는 값이 보고서에 표시되는지 항상 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="95972-140">Always verify that the report displays the expected values from the data in the PowerPivot model before you publish the report.</span></span>  
  
 <span data-ttu-id="95972-141">다음 조건이 충족되어야 PowerPivot 갤러리의 보고서에 대한 미리 보기 이미지가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="95972-141">Preview images of a report in a PowerPivot Gallery are generated only if the following conditions are met:</span></span>  
  
-   <span data-ttu-id="95972-142">데이터를 제공하는 보고서 및 PowerPivot 통합 문서는 동일한 PowerPivot 갤러리에 함께 저장되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="95972-142">The report and the PowerPivot workbook that provides the data must be stored together in the same PowerPivot Gallery.</span></span>  
  
-   <span data-ttu-id="95972-143">보고서는 PowerPivot 데이터 원본의 PowerPivot 데이터만 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="95972-143">The report contains only PowerPivot data from a PowerPivot data source.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95972-144">참고 항목</span><span class="sxs-lookup"><span data-stu-id="95972-144">See Also</span></span>  
 <span data-ttu-id="95972-145">[Analysis Services MDX 쿼리 디자이너 사용자 인터페이스&#40;보고서 작성기&#41;](../analysis-services-mdx-query-designer-user-interface-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="95972-145">[Analysis Services MDX Query Designer User Interface &#40;Report Builder&#41;](../analysis-services-mdx-query-designer-user-interface-report-builder.md) </span></span>  
 [<span data-ttu-id="95972-146">식&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="95972-146">Expressions &#40;Report Builder and SSRS&#41;</span></span>](../report-design/expressions-report-builder-and-ssrs.md)  
  
  
