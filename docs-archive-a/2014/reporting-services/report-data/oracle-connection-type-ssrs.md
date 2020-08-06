---
title: Oracle 연결 형식(SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 9db86dd2-beda-42d8-8af7-2629d58a8e3d
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: e9bf19953c5d2dc2f818eddcacf445e641972d4e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650770"
---
# <a name="oracle-connection-type-ssrs"></a><span data-ttu-id="4cf02-102">Oracle 연결 형식(SSRS)</span><span class="sxs-lookup"><span data-stu-id="4cf02-102">Oracle Connection Type (SSRS)</span></span>
  <span data-ttu-id="4cf02-103">보고서에서 Oracle 데이터베이스의 데이터를 사용하려면 Oracle 유형의 보고서 데이터 원본을 기반으로 하는 데이터 세트가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4cf02-103">To use data from an Oracle database in your report, you must you must have a dataset that is based on a report data source of type Oracle.</span></span> <span data-ttu-id="4cf02-104">이 기본 제공 데이터 원본 유형은 .NET Framework Managed Provider for Oracle을 기반으로 하며 Oracle 클라이언트 소프트웨어 구성 요소를 필요로 합니다.</span><span class="sxs-lookup"><span data-stu-id="4cf02-104">This built-in data source type is based on the .NET Framework Managed Provider for Oracle and requires an Oracle client software component.</span></span>  
  
 <span data-ttu-id="4cf02-105">이 항목의 정보를 사용하여 데이터 원본을 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4cf02-105">Use the information in this topic to build a data source.</span></span> <span data-ttu-id="4cf02-106">단계별 지침은 [데이터 연결이 나 데이터 원본 &#40;추가 및 확인 보고서 작성기 및 SSRS&#41;](add-and-verify-a-data-connection-report-builder-and-ssrs.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="4cf02-106">For step-by-step instructions, see [Add and Verify a Data Connection or Data Source &#40;Report Builder and SSRS&#41;](add-and-verify-a-data-connection-report-builder-and-ssrs.md).</span></span>  
  
##  <a name="connection-string"></a><a name="Connection"></a><span data-ttu-id="4cf02-107">연결 문자열</span><span class="sxs-lookup"><span data-stu-id="4cf02-107">Connection String</span></span>  
 <span data-ttu-id="4cf02-108">데이터 원본 연결에 사용할 자격 증명 및 연결 정보는 데이터베이스 관리자에게 문의하십시오.</span><span class="sxs-lookup"><span data-stu-id="4cf02-108">Contact your database administrator for connection information and for the credentials to use to connect to the data source.</span></span> <span data-ttu-id="4cf02-109">다음 연결 문자열 예에서는 유니코드를 사용하는 "Oracle9"라는 서버의 Oracle 데이터베이스를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="4cf02-109">The following connection string example specifies an Oracle database on the server named "Oracle9" using Unicode.</span></span> <span data-ttu-id="4cf02-110">서버 이름은 Tnsnames.ora 구성 파일에 Oracle 서버 인스턴스 이름으로 정의되어 있는 이름과 일치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4cf02-110">The server name must match what is defined in the Tnsnames.ora configuration file as the Oracle server instance name.</span></span>  
  
```  
Data Source="Oracle9"; Unicode="True"  
```  
  
 <span data-ttu-id="4cf02-111">연결 문자열 예제에 대한 자세한 내용은 [보고서 작성기의 데이터 연결, 데이터 원본 및 연결 문자열](../data-connections-data-sources-and-connection-strings-in-report-builder.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4cf02-111">For more information about connection string examples, see [Data Connections, Data Sources, and Connection Strings in Report Builder](../data-connections-data-sources-and-connection-strings-in-report-builder.md).</span></span>  
  
##  <a name="credentials"></a><a name="Credentials"></a><span data-ttu-id="4cf02-112">자격 증명</span><span class="sxs-lookup"><span data-stu-id="4cf02-112">Credentials</span></span>  
 <span data-ttu-id="4cf02-113">쿼리를 실행하거나 보고서를 로컬로 미리 보거나 보고서 서버의 보고서를 미리 보려면 자격 증명이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="4cf02-113">Credentials are required to run queries, to preview the report locally, and to preview the report from the report server.</span></span>  
  
 <span data-ttu-id="4cf02-114">보고서를 게시한 후 보고서를 보고서 서버에서 실행할 때 데이터를 검색할 수 있는 권한이 유효하도록 데이터 원본에 대한 자격 증명을 변경해야 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4cf02-114">After you publish your report, you may need to change the credentials for the data source so that when the report runs on the report server, the permissions to retrieve the data are valid.</span></span>  
  
 <span data-ttu-id="4cf02-115">자세한 내용은 [Reporting Services의 데이터 연결, 데이터 원본 및 연결 문자열](../data-connections-data-sources-and-connection-strings-in-reporting-services.md) 을 참조 하거나 [보고서 작성기에서 자격 증명을 지정](../specify-credentials-in-report-builder.md)하세요.</span><span class="sxs-lookup"><span data-stu-id="4cf02-115">For more information, see [Data Connections, Data Sources, and Connection Strings in Reporting Services](../data-connections-data-sources-and-connection-strings-in-reporting-services.md) or [Specify Credentials in Report Builder](../specify-credentials-in-report-builder.md).</span></span>  
  

  
##  <a name="queries"></a><a name="Query"></a><span data-ttu-id="4cf02-116">쿼리</span><span class="sxs-lookup"><span data-stu-id="4cf02-116">Queries</span></span>  
 <span data-ttu-id="4cf02-117">데이터 세트를 만들려면 드롭다운 목록에서 저장 프로시저를 선택하거나 SQL 쿼리를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="4cf02-117">To create a dataset, you can either select a stored procedure from a drop-down list or create an SQL query.</span></span> <span data-ttu-id="4cf02-118">쿼리를 만들려면 텍스트 기반 쿼리 디자이너를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4cf02-118">To build a query, you must use the text-based query designer.</span></span> <span data-ttu-id="4cf02-119">자세한 내용은 [텍스트 기반 쿼리 디자이너 사용자 인터페이스&#40;보고서 작성기&#41;](text-based-query-designer-user-interface-report-builder.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4cf02-119">For more information, see [Text-based Query Designer User Interface &#40;Report Builder&#41;](text-based-query-designer-user-interface-report-builder.md).</span></span>  
  
 <span data-ttu-id="4cf02-120">결과 집합을 하나만 반환하는 저장 프로시저를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4cf02-120">You can specify stored procedures that return only one result set.</span></span> <span data-ttu-id="4cf02-121">커서 기반 쿼리는 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4cf02-121">Using cursor-based queries are not supported.</span></span>  
  
##  <a name="parameters"></a><a name="Parameters"></a> <span data-ttu-id="4cf02-122">매개 변수</span><span class="sxs-lookup"><span data-stu-id="4cf02-122">Parameters</span></span>  
 <span data-ttu-id="4cf02-123">쿼리에 쿼리 변수가 포함된 경우 해당 보고서 매개 변수가 자동으로 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="4cf02-123">If the query includes query variables, corresponding report parameters are automatically generated.</span></span> <span data-ttu-id="4cf02-124">이 확장 프로그램은 명명된 매개 변수를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="4cf02-124">Named parameters are supported by this extension.</span></span> <span data-ttu-id="4cf02-125">Oracle 버전 9 이상의 경우 다중값 매개 변수가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="4cf02-125">For Oracle version 9 or later, multivalue parameters are supported.</span></span>  
  
 <span data-ttu-id="4cf02-126">보고서 매개 변수는 수정해야 할 수도 있는 기본 속성 값을 사용하여 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="4cf02-126">Report parameters are created with default property values that you might need to modify.</span></span> <span data-ttu-id="4cf02-127">예를 들어 각 보고서 매개 변수의 데이터 형식은 **Text**입니다.</span><span class="sxs-lookup"><span data-stu-id="4cf02-127">For example, each report parameter is data type **Text**.</span></span> <span data-ttu-id="4cf02-128">보고서 매개 변수가 만들어진 후에는 기본값을 변경해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4cf02-128">After the report parameters are created, you might have to change default values.</span></span> <span data-ttu-id="4cf02-129">자세한 내용은 [보고서 매개 변수&#40;보고서 작성기 및 보고서 디자이너&#41;](../report-design/report-parameters-report-builder-and-report-designer.md)에 대해 자세히 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="4cf02-129">For more information, see [Report Parameters &#40;Report Builder and Report Designer&#41;](../report-design/report-parameters-report-builder-and-report-designer.md).</span></span>  
  

  
##  <a name="remarks"></a><a name="Remarks"></a> <span data-ttu-id="4cf02-130">주의</span><span class="sxs-lookup"><span data-stu-id="4cf02-130">Remarks</span></span>  
 <span data-ttu-id="4cf02-131">Oracle 데이터 원본을 연결하려면 시스템 관리자가 Oracle 데이터베이스에서 데이터를 검색할 수 있도록 하는 .NET Data Provider for Oracle 버전을 설치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4cf02-131">Before you can connect an Oracle data source, the system administrator must have installed the version of the .NET Data Provider for Oracle that supports retrieving data from the Oracle database.</span></span> <span data-ttu-id="4cf02-132">이 데이터 공급자는 보고서 작성기와 동일한 컴퓨터뿐 아니라 보고서 서버에도 설치되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4cf02-132">This data provider must be installed on the same computer as Report Builder and also on the report server.</span></span>  
  
 <span data-ttu-id="4cf02-133">자세한 내용은</span><span class="sxs-lookup"><span data-stu-id="4cf02-133">For more information, see the following:</span></span>  
  
-   <span data-ttu-id="4cf02-134">msdn.microsoft.com의[.NET Framework Data Provider for Oracle 사용](https://go.microsoft.com/fwlink/?LinkId=112314)</span><span class="sxs-lookup"><span data-stu-id="4cf02-134">[Using the .NET Framework Data Provider for Oracle](https://go.microsoft.com/fwlink/?LinkId=112314) on msdn.microsoft.com</span></span>  
  
-   [<span data-ttu-id="4cf02-135">Reporting Services를 사용한 Oracle 데이터 원본 구성 및 액세스 방법</span><span class="sxs-lookup"><span data-stu-id="4cf02-135">How to use Reporting Services to configure and to access an Oracle data source</span></span>](https://support.microsoft.com/kb/834305)  
  
-   [<span data-ttu-id="4cf02-136">NETWORK SERVICE 보안 주체에 대한 사용 권한을 추가하는 방법</span><span class="sxs-lookup"><span data-stu-id="4cf02-136">How to add permissions for the NETWORK SERVICE security principal</span></span>](https://support.microsoft.com/kb/870668)  
  
###### <a name="alternate-data-extensions"></a><span data-ttu-id="4cf02-137">대체 데이터 확장 프로그램</span><span class="sxs-lookup"><span data-stu-id="4cf02-137">Alternate Data Extensions</span></span>  
 <span data-ttu-id="4cf02-138">OLE DB 데이터 원본 유형을 사용하여 Oracle 데이터베이스에서 데이터를 검색할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4cf02-138">You can also retrieve data from an Oracle database by using an OLE DB data source type.</span></span> <span data-ttu-id="4cf02-139">자세한 내용은 [OLE DB 연결 형식&#40;SSRS&#41;](ole-db-connection-type-ssrs.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4cf02-139">For more information, see [OLE DB Connection Type &#40;SSRS&#41;](ole-db-connection-type-ssrs.md).</span></span>  
  
###### <a name="report-models"></a><span data-ttu-id="4cf02-140">보고서 모델</span><span class="sxs-lookup"><span data-stu-id="4cf02-140">Report Models</span></span>  
 <span data-ttu-id="4cf02-141">Oracle 데이터베이스를 기반으로 모델을 만들 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4cf02-141">You can also create models based on an Oracle database.</span></span>  
  
###### <a name="platform-and-version-information"></a><span data-ttu-id="4cf02-142">플랫폼 및 버전 정보</span><span class="sxs-lookup"><span data-stu-id="4cf02-142">Platform and Version Information</span></span>  
 <span data-ttu-id="4cf02-143">플랫폼 및 버전 지원에 대한 자세한 내용은 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [온라인 설명서](https://go.microsoft.com/fwlink/?linkid=121312)의 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 설명서에서 [Reporting Services&#40;SSRS&#41;에서 지원하는 데이터 원본](../create-deploy-and-manage-mobile-and-paginated-reports.md).</span><span class="sxs-lookup"><span data-stu-id="4cf02-143">For more information about platform and version support, see [Data Sources Supported by Reporting Services &#40;SSRS&#41;](../create-deploy-and-manage-mobile-and-paginated-reports.md) in the [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] documentation in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [Books Online](https://go.microsoft.com/fwlink/?linkid=121312).</span></span>  
  

  
##  <a name="how-to-topics"></a><a name="HowTo"></a><span data-ttu-id="4cf02-144">방법 도움말 항목</span><span class="sxs-lookup"><span data-stu-id="4cf02-144">How-To Topics</span></span>  
 <span data-ttu-id="4cf02-145">이 섹션에서는 데이터 연결, 데이터 원본 및 데이터 세트를 사용하는 방법을 단계별로 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="4cf02-145">This section contains step-by-step instructions for working with data connections, data sources, and datasets.</span></span>  
  
 [<span data-ttu-id="4cf02-146">데이터 연결이 나 데이터 원본 &#40;보고서 작성기 및 SSRS를 추가 하 고 확인&#41;</span><span class="sxs-lookup"><span data-stu-id="4cf02-146">Add and Verify a Data Connection or Data Source &#40;Report Builder and SSRS&#41;</span></span>](add-and-verify-a-data-connection-report-builder-and-ssrs.md)  
  
 [<span data-ttu-id="4cf02-147">공유 데이터 세트 또는 포함된 데이터 세트 만들기&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="4cf02-147">Create a Shared Dataset or Embedded Dataset &#40;Report Builder and SSRS&#41;</span></span>](create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md)  
  
 [<span data-ttu-id="4cf02-148">데이터 세트에 필터 추가&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="4cf02-148">Add a Filter to a Dataset &#40;Report Builder and SSRS&#41;</span></span>](add-a-filter-to-a-dataset-report-builder-and-ssrs.md)  
  
 
  
##  <a name="related-sections"></a><a name="Related"></a> <span data-ttu-id="4cf02-149">관련 섹션</span><span class="sxs-lookup"><span data-stu-id="4cf02-149">Related Sections</span></span>  
 <span data-ttu-id="4cf02-150">설명서의 다음 섹션에서는 보고서 데이터에 대한 깊이 있는 개념 정보를 제공하며, 데이터와 관련된 보고서 부분을 정의, 사용자 지정 및 사용하는 방법을 절차적인 측면에서 소개합니다.</span><span class="sxs-lookup"><span data-stu-id="4cf02-150">These sections of the documentation provide in-depth conceptual information about report data, as well as procedural information about how to define, customize, and use parts of a report that are related to data.</span></span>  
  
 [<span data-ttu-id="4cf02-151">보고서 &#40;보고서 작성기 및 SSRS&#41;에 데이터를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="4cf02-151">Add Data to a Report &#40;Report Builder and SSRS&#41;</span></span>](report-datasets-ssrs.md)  
 <span data-ttu-id="4cf02-152">보고서의 데이터 액세스에 대한 개요를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="4cf02-152">Provides an overview of accessing data for your report.</span></span>  
  
 [<span data-ttu-id="4cf02-153">보고서 작성기의 데이터 연결, 데이터 원본 및 연결 문자열</span><span class="sxs-lookup"><span data-stu-id="4cf02-153">Data Connections, Data Sources, and Connection Strings in Report Builder</span></span>](../data-connections-data-sources-and-connection-strings-in-report-builder.md)  
 <span data-ttu-id="4cf02-154">데이터 연결 및 데이터 원본에 대한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="4cf02-154">Provides information about data connections and data sources.</span></span>  
  
 [<span data-ttu-id="4cf02-155">보고서 포함된 데이터 세트 및 공유 데이터 세트&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="4cf02-155">Report Embedded Datasets and Shared Datasets &#40;Report Builder and SSRS&#41;</span></span>](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)  
 <span data-ttu-id="4cf02-156">포함된 데이터 세트 및 공유 데이터 세트에 대한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="4cf02-156">Provides information about embedded and shared datasets.</span></span>  
  
 [<span data-ttu-id="4cf02-157">데이터 세트 필드 컬렉션&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="4cf02-157">Dataset Fields Collection &#40;Report Builder and SSRS&#41;</span></span>](dataset-fields-collection-report-builder-and-ssrs.md)  
 <span data-ttu-id="4cf02-158">쿼리에 의해 생성되는 데이터 세트 필드 컬렉션에 대한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="4cf02-158">Provides information about the dataset field collection generated by the query.</span></span>  
  
 <span data-ttu-id="4cf02-159">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [온라인 설명서](https://go.microsoft.com/fwlink/?linkid=121312)에 있는 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 설명서의 [Reporting Services&#40;SSRS&#41;에서 지원하는 데이터 원본](../create-deploy-and-manage-mobile-and-paginated-reports.md).</span><span class="sxs-lookup"><span data-stu-id="4cf02-159">[Data Sources Supported by Reporting Services &#40;SSRS&#41;](../create-deploy-and-manage-mobile-and-paginated-reports.md) in the [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] documentation in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [Books Online](https://go.microsoft.com/fwlink/?linkid=121312).</span></span>  
 <span data-ttu-id="4cf02-160">각 데이터 확장 프로그램의 플랫폼 및 버전 지원에 대한 자세한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="4cf02-160">Provides in-depth information about platform and version support for each data extension.</span></span>  
  

  
## <a name="see-also"></a><span data-ttu-id="4cf02-161">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4cf02-161">See Also</span></span>  
 <span data-ttu-id="4cf02-162">[보고서 매개 변수 &#40;보고서 작성기 및 보고서 디자이너&#41;](../report-design/report-parameters-report-builder-and-report-designer.md) </span><span class="sxs-lookup"><span data-stu-id="4cf02-162">[Report Parameters &#40;Report Builder and Report Designer&#41;](../report-design/report-parameters-report-builder-and-report-designer.md) </span></span>  
 <span data-ttu-id="4cf02-163">[데이터 필터링, 그룹화 및 정렬 &#40;보고서 작성기 및 SSRS&#41;](../report-design/filter-group-and-sort-data-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="4cf02-163">[Filter, Group, and Sort Data &#40;Report Builder and SSRS&#41;](../report-design/filter-group-and-sort-data-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="4cf02-164">식&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="4cf02-164">Expressions &#40;Report Builder and SSRS&#41;</span></span>](../report-design/expressions-report-builder-and-ssrs.md)  
  
  
