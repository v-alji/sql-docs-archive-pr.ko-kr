---
title: XML 연결 형식(SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 5b55fff2-1b15-4156-83ef-15ad9cf9f509
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 141f6449e0493ba7a12e9270bedab967b7795ee0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739399"
---
# <a name="xml-connection-type-ssrs"></a><span data-ttu-id="24ad4-102">XML 연결 형식(SSRS)</span><span class="sxs-lookup"><span data-stu-id="24ad4-102">XML Connection Type (SSRS)</span></span>
  <span data-ttu-id="24ad4-103">보고서에 XML 데이터 원본의 데이터를 포함하려면 XML 유형의 보고서 데이터 원본에 기초하는 데이터 세트가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="24ad4-103">To include data from an XML data source in your report, you must have a dataset that is based on a report data source of type XML.</span></span> <span data-ttu-id="24ad4-104">이 기본 제공 데이터 원본 유형은 XML 데이터 확장 프로그램을 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="24ad4-104">This built-in data source type is based on the XML data extension.</span></span> <span data-ttu-id="24ad4-105">이 데이터 원본 유형을 사용하여 쿼리에 포함된 XML 문서, 웹 서비스 또는 XML에서 데이터에 연결하여 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="24ad4-105">Use this data source type to connect to and retrieve data from XML documents, Web services, or XML that is embedded in the query.</span></span>  
  
 <span data-ttu-id="24ad4-106">이 데이터 확장 프로그램은 연결 문자열과 별개로 관리되는 자격 증명 및 매개 변수를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="24ad4-106">This data extension supports parameters and credentials managed separately from the connection string.</span></span>  
  
 <span data-ttu-id="24ad4-107">이 항목의 정보를 사용하여 데이터 원본을 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="24ad4-107">Use the information in this topic to build a data source.</span></span> <span data-ttu-id="24ad4-108">단계별 지침은 [데이터 연결이 나 데이터 원본 &#40;추가 및 확인 보고서 작성기 및 SSRS&#41;](add-and-verify-a-data-connection-report-builder-and-ssrs.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="24ad4-108">For step-by-step instructions, see [Add and Verify a Data Connection or Data Source &#40;Report Builder and SSRS&#41;](add-and-verify-a-data-connection-report-builder-and-ssrs.md).</span></span>  
  
##  <a name="connection-string"></a><a name="Connection"></a> <span data-ttu-id="24ad4-109">연결 문자열</span><span class="sxs-lookup"><span data-stu-id="24ad4-109">Connection String</span></span>  
 <span data-ttu-id="24ad4-110">연결 문자열은 HTTP를 통해 사용할 수 있는 웹 서비스, 웹 기반 애플리케이션 또는 XML 문서를 가리키는 URL이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="24ad4-110">The connection string must be a URL that points to the Web service, Web-based application, or XML document available through HTTP.</span></span> <span data-ttu-id="24ad4-111">XML 문서에는 XML 확장명을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="24ad4-111">XML documents must have the XML extension.</span></span> <span data-ttu-id="24ad4-112">데이터 세트 쿼리에 포함된 XML 데이터의 경우 빈 연결 문자열을 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="24ad4-112">You can also use an empty connection string for XML data embedded in the dataset query.</span></span>  
  
 <span data-ttu-id="24ad4-113">다음 예에서는 웹 서비스 및 XML 문서에 대한 각각의 연결 문자열 구문을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="24ad4-113">The following examples illustrate the connection string syntax for a Web service and XML document, respectively.</span></span> <span data-ttu-id="24ad4-114">`file://` 프로토콜은 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="24ad4-114">The `file://` protocol is not supported.</span></span>  
  
|<span data-ttu-id="24ad4-115">XML 문서 유형</span><span class="sxs-lookup"><span data-stu-id="24ad4-115">XML document type</span></span>|<span data-ttu-id="24ad4-116">연결 문자열 예</span><span class="sxs-lookup"><span data-stu-id="24ad4-116">Connection String Example</span></span>|  
|-----------------------|-------------------------------|  
|<span data-ttu-id="24ad4-117">웹 서비스</span><span class="sxs-lookup"><span data-stu-id="24ad4-117">Web service</span></span>|`http://adventure-works.com/results.aspx`|  
|<span data-ttu-id="24ad4-118">XML 문서</span><span class="sxs-lookup"><span data-stu-id="24ad4-118">XML document</span></span>|`http://localhost/XML/Customers.xml`|  
|<span data-ttu-id="24ad4-119">포함 XML 문서</span><span class="sxs-lookup"><span data-stu-id="24ad4-119">Embedded XML document</span></span>|<span data-ttu-id="24ad4-120">*비어 있음*</span><span class="sxs-lookup"><span data-stu-id="24ad4-120">*Empty*</span></span>|  
  
 <span data-ttu-id="24ad4-121">연결 문자열 예제는 [보고서 작성기의 데이터 연결, 데이터 원본 및 연결 문자열](../data-connections-data-sources-and-connection-strings-in-report-builder.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="24ad4-121">For more connection string examples, see [Data Connections, Data Sources, and Connection Strings in Report Builder](../data-connections-data-sources-and-connection-strings-in-report-builder.md).</span></span>  
  
##  <a name="credentials"></a><a name="Credentials"></a> <span data-ttu-id="24ad4-122">자격 증명</span><span class="sxs-lookup"><span data-stu-id="24ad4-122">Credentials</span></span>  
 <span data-ttu-id="24ad4-123">쿼리를 실행하거나 보고서를 로컬로 미리 보거나 보고서 서버의 보고서를 미리 보려면 자격 증명이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="24ad4-123">Credentials are required to run queries, to preview the report locally, and to preview the report from the report server.</span></span>  
  
 <span data-ttu-id="24ad4-124">보고서를 게시한 후 보고서를 보고서 서버에서 실행할 때 데이터를 검색할 수 있는 권한이 유효하도록 데이터 원본에 대한 자격 증명을 변경해야 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="24ad4-124">After you publish your report, you may need to change the credentials for the data source so that when the report runs on the report server, the permissions to retrieve the data are valid.</span></span>  
  
 <span data-ttu-id="24ad4-125">보고서 작성 클라이언트에서는 다음 옵션을 사용하여 자격 증명을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="24ad4-125">From a report authoring client, the following options are available to specify credentials:</span></span>  
  
-   <span data-ttu-id="24ad4-126">현재 Windows 사용자(통합 보안)</span><span class="sxs-lookup"><span data-stu-id="24ad4-126">Current Windows user (also known as integrated security).</span></span>  
  
-   <span data-ttu-id="24ad4-127">자격 증명 필요 없음.</span><span class="sxs-lookup"><span data-stu-id="24ad4-127">No credentials are required.</span></span> <span data-ttu-id="24ad4-128">자격 증명을 사용하지 않도록 선택하는 경우 익명 액세스가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="24ad4-128">If you select no credentials, Anonymous access is used.</span></span> <span data-ttu-id="24ad4-129">보고서 서버에서 외부 데이터 원본에 연결할 수 있도록 무인 실행 계정을 정의했는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="24ad4-129">Make sure that you have defined the unattended execution account for the report server to connect to an external data source.</span></span> <span data-ttu-id="24ad4-130">XML 데이터 처리 확장 프로그램에서는 자격 증명을 대상 URL이나 웹 서비스로 전달하지 않으므로 무인 실행 계정을 정의하지 않은 경우에는 연결이 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="24ad4-130">The XML data processing extension does not pass credentials to the target URL or the Web service; the connection will be unsuccessful unless you have defined the unattended execution account.</span></span> <span data-ttu-id="24ad4-131">자세한 내용은 msdn.microsoft.com의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [온라인 설명서](https://go.microsoft.com/fwlink/?linkid=121312)에서 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 설명서의 [무인 실행 계정 구성&#40;SSRS 구성 관리자&#41;](../install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="24ad4-131">For more information, see [Configure the Unattended Execution Account &#40;SSRS Configuration Manager&#41;](../install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md) in the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] documentation in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [Books Online](https://go.microsoft.com/fwlink/?linkid=121312) on msdn.microsoft.com.</span></span>  
  
 <span data-ttu-id="24ad4-132">저장된 자격 증명 및 입력 정보를 요청하는 자격 증명은 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="24ad4-132">Stored and prompted credentials are not supported.</span></span> <span data-ttu-id="24ad4-133">Windows 통합 보안을 사용하지 않도록 설정한 경우 이를 사용하여 데이터를 검색할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="24ad4-133">Remember that if you disable Windows integrated security, you cannot use it to retrieve data.</span></span> <span data-ttu-id="24ad4-134">저장된 자격 증명 및 입력 정보를 요청하는 자격 증명을 지정할 경우 런타임에 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="24ad4-134">If you specify stored or prompted credentials, an error will occur at run time.</span></span>  
  
 <span data-ttu-id="24ad4-135">자세한 내용은 [Reporting Services의 데이터 연결, 데이터 원본 및 연결 문자열](../data-connections-data-sources-and-connection-strings-in-reporting-services.md) 을 참조 하거나 [보고서 작성기에서 자격 증명을 지정](../specify-credentials-in-report-builder.md)하세요.</span><span class="sxs-lookup"><span data-stu-id="24ad4-135">For more information, see [Data Connections, Data Sources, and Connection Strings in Reporting Services](../data-connections-data-sources-and-connection-strings-in-reporting-services.md) or [Specify Credentials in Report Builder](../specify-credentials-in-report-builder.md).</span></span>  
  
##  <a name="queries"></a><a name="Query"></a> <span data-ttu-id="24ad4-136">쿼리</span><span class="sxs-lookup"><span data-stu-id="24ad4-136">Queries</span></span>  
 <span data-ttu-id="24ad4-137">쿼리는 보고서 데이터 세트에 대해 검색할 데이터를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="24ad4-137">A query specifies which data to retrieve for a report dataset.</span></span> <span data-ttu-id="24ad4-138">쿼리 결과 집합의 열은 데이터 세트의 필드 컬렉션을 채웁니다.</span><span class="sxs-lookup"><span data-stu-id="24ad4-138">The columns in the result set for a query populate the field collection for a dataset.</span></span> <span data-ttu-id="24ad4-139">보고서는 쿼리에서 검색된 첫 번째 결과 집합만 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="24ad4-139">A report processes only the first result set retrieved by a query.</span></span>  
  
 <span data-ttu-id="24ad4-140">쿼리를 만들려면 텍스트 기반 쿼리 디자이너를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="24ad4-140">You must use the text-based query designer to create the query.</span></span> <span data-ttu-id="24ad4-141">쿼리는 XML 데이터를 반환해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="24ad4-141">The query must return XML data.</span></span>  
  
 <span data-ttu-id="24ad4-142">텍스트 기반 쿼리 디자이너에 대한 자세한 내용은 [텍스트 기반 쿼리 디자이너 사용자 인터페이스&#40;보고서 작성기&#41;](text-based-query-designer-user-interface-report-builder.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="24ad4-142">For more information about the text-based query designer, see [Text-based Query Designer User Interface &#40;Report Builder&#41;](text-based-query-designer-user-interface-report-builder.md).</span></span>  
  
 <span data-ttu-id="24ad4-143">XML 형식의 데이터 원본에 대한 데이터 세트 쿼리에서 사용할 수 있는 값이 아래에 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="24ad4-143">The possible values for a dataset query for a data source that is type XML are shown below.</span></span>  
  
-   <span data-ttu-id="24ad4-144">*Empty*: 빈 쿼리를 사용 하 여 기본 결과 집합을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="24ad4-144">*Empty*: Use an empty query to create a default result set.</span></span> <span data-ttu-id="24ad4-145">기본 쿼리는 데이터 원본을 읽고 XML 노드 계층에서 첫 번째 리프 컬렉션까지 탐색하도록 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="24ad4-145">The default query is created by reading the data source and traversing the XML node hierarchy to the first leaf collection.</span></span> <span data-ttu-id="24ad4-146">결과 집합에는 텍스트 값이 있는 모든 노드와 해당 경로의 모든 노드 특성이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="24ad4-146">The result set includes all nodes with text values and all node attributes along that path.</span></span> <span data-ttu-id="24ad4-147">결과 집합의 열은 데이터 세트의 필드에 매핑됩니다.</span><span class="sxs-lookup"><span data-stu-id="24ad4-147">Columns in the result set are mapped to fields for the dataset.</span></span>  
  
-   <span data-ttu-id="24ad4-148">요소 경로: 데이터 원본에서 XML 데이터를 검색할 때 사용할 노드 시퀀스를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="24ad4-148">An element path: Specifies the sequence of nodes to use when retrieving XML data from the data source.</span></span>  
  
-   <span data-ttu-id="24ad4-149">XML 쿼리 요소: 다음과 같은 선택적 요소를 포함 하는 XML 쿼리 사양입니다.</span><span class="sxs-lookup"><span data-stu-id="24ad4-149">An XML Query element: An XML query specification with the following optional elements:</span></span>  
  
    -   <span data-ttu-id="24ad4-150">**웹 서비스의 경우:**</span><span class="sxs-lookup"><span data-stu-id="24ad4-150">**For a Web service:**</span></span>  
  
         <span data-ttu-id="24ad4-151">필수 XML 요소:</span><span class="sxs-lookup"><span data-stu-id="24ad4-151">Required XML Elements:</span></span>  
  
         <span data-ttu-id="24ad4-152">`<Method Namespace=`*"namespace"*  `Name="MethodName" />`</span><span class="sxs-lookup"><span data-stu-id="24ad4-152">`<Method Namespace=` *"namespace"*  `Name="MethodName" />`</span></span>  
  
         `-- or --`  
  
         <span data-ttu-id="24ad4-153">`<SoapAction>` *soap action* `</SoapAction>`</span><span class="sxs-lookup"><span data-stu-id="24ad4-153">`<SoapAction>` *soap action* `</SoapAction>`</span></span>  
  
         <span data-ttu-id="24ad4-154">선택적 XML 요소:</span><span class="sxs-lookup"><span data-stu-id="24ad4-154">Optional XML Elements:</span></span>  
  
         <span data-ttu-id="24ad4-155">`<ElementPath>`  *element path*  `</ElementPath>`</span><span class="sxs-lookup"><span data-stu-id="24ad4-155">`<ElementPath>`  *element path*  `</ElementPath>`</span></span>  
  
         <span data-ttu-id="24ad4-156">`<Method Namespace=`*"namespace"*  `Name="MethodName" />`</span><span class="sxs-lookup"><span data-stu-id="24ad4-156">`<Method Namespace=` *"namespace"*  `Name="MethodName" />`</span></span>  
  
         `-- or --`  
  
         <span data-ttu-id="24ad4-157">`<SoapAction>` *soap action* `</SoapAction>`</span><span class="sxs-lookup"><span data-stu-id="24ad4-157">`<SoapAction>` *soap action* `</SoapAction>`</span></span>  
  
    -   <span data-ttu-id="24ad4-158">**XML 문서의 경우:**</span><span class="sxs-lookup"><span data-stu-id="24ad4-158">**For an XML document:**</span></span>  
  
         <span data-ttu-id="24ad4-159">선택적 XML 요소:</span><span class="sxs-lookup"><span data-stu-id="24ad4-159">Optional XML Elements:</span></span>  
  
         <span data-ttu-id="24ad4-160">`<ElementPath>`  *element path*  `</ElementPath>`</span><span class="sxs-lookup"><span data-stu-id="24ad4-160">`<ElementPath>`  *element path*  `</ElementPath>`</span></span>  
  
    -   <span data-ttu-id="24ad4-161">**포함 된 XML 문서의 경우:**</span><span class="sxs-lookup"><span data-stu-id="24ad4-161">**For an embedded XML document:**</span></span>  
  
         <span data-ttu-id="24ad4-162">필수 XML 요소:</span><span class="sxs-lookup"><span data-stu-id="24ad4-162">Required XML Elements:</span></span>  
  
         <span data-ttu-id="24ad4-163">`<XmlData>` inner XML `</XmlData>`</span><span class="sxs-lookup"><span data-stu-id="24ad4-163">`<XmlData>` inner XML `</XmlData>`</span></span>  
  
         <span data-ttu-id="24ad4-164">선택적 XML 요소:</span><span class="sxs-lookup"><span data-stu-id="24ad4-164">Optional XML Elements:</span></span>  
  
         <span data-ttu-id="24ad4-165">`<ElementPath>`  *element path*  `</ElementPath>`</span><span class="sxs-lookup"><span data-stu-id="24ad4-165">`<ElementPath>`  *element path*  `</ElementPath>`</span></span>  
  
         `-- or --`  
  
         <span data-ttu-id="24ad4-166">`<ElementPath IgnoreNamespaces="true">`  *element path*  `</ElementPath>`</span><span class="sxs-lookup"><span data-stu-id="24ad4-166">`<ElementPath IgnoreNamespaces="true">`  *element path*  `</ElementPath>`</span></span>  
  
 <span data-ttu-id="24ad4-167">쿼리 구문에 대한 자세한 내용은 msdn.microsoft.com의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [온라인 설명서](https://go.microsoft.com/fwlink/?linkid=121312)에서 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 설명서의 [XML 보고서 데이터를 위한 XML 쿼리 구문&#40;SSRS&#41;](report-data-ssrs.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="24ad4-167">For more information about query syntax, see [XML Query Syntax for XML Report Data &#40;SSRS&#41;](report-data-ssrs.md) in the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] documentation in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [Books Online](https://go.microsoft.com/fwlink/?linkid=121312) on msdn.microsoft.com.</span></span>  
  
 <span data-ttu-id="24ad4-168">예를 보려면 [Reporting Services: XML 및 웹 서비스 데이터 원본 사용(Reporting Services: Using XML and Web Service Data Sources)](https://go.microsoft.com/fwlink/?LinkId=81654)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="24ad4-168">For examples, see [Reporting Services: Using XML and Web Service Data Sources](https://go.microsoft.com/fwlink/?LinkId=81654).</span></span>  
  
### <a name="requirements-for-retrieving-xml-web-service-data"></a><span data-ttu-id="24ad4-169">XML 웹 서비스 데이터 검색을 위한 요구 사항</span><span class="sxs-lookup"><span data-stu-id="24ad4-169">Requirements for Retrieving XML Web Service Data</span></span>  
 <span data-ttu-id="24ad4-170">XML 데이터 처리 확장 프로그램은 스키마를 검색하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="24ad4-170">The XML data processing extension does not detect the schema for you.</span></span> <span data-ttu-id="24ad4-171">따라서 다른 방법으로 원하는 데이터를 검색할 SOAP 메서드를 찾아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="24ad4-171">Therefore, you must have some way of discovering which SOAP methods will retrieve the data that you want.</span></span> <span data-ttu-id="24ad4-172">또한 웹 서비스에서 해당 데이터에 사용하는 주소 지정 스키마나 네임스페이스에 대해 이해하고 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="24ad4-172">You must also understand the addressing scheme or namespace that the Web service uses for its data.</span></span>  
  
 <span data-ttu-id="24ad4-173">웹 서비스의 경우 `Query` 호출할 메서드나 SOAP 동작을 지정 하는 <> 요소를 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="24ad4-173">For a Web service, you can provide a <`Query`> element that specifies a method to call or SOAP action.</span></span> <span data-ttu-id="24ad4-174">XML 데이터 원본에 보고서에 사용할 데이터를 생성하는 계층 구조가 있는 경우 쿼리를 비워 두고 기본 쿼리를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="24ad4-174">You can leave the query empty and use the default query if the XML data source has a hierarchical structure that produces the data that you want to use for your report.</span></span> <span data-ttu-id="24ad4-175">쿼리가 실행될 때 검색되는 XML 요소 노드 값 및 특성은 보고서에서 사용하는 데이터 세트 필드에 매핑됩니다.</span><span class="sxs-lookup"><span data-stu-id="24ad4-175">XML element node values and attributes retrieved when the query runs map to the dataset fields you use in your report.</span></span>  
  
### <a name="requirements-for-retrieving-xml-document-data"></a><span data-ttu-id="24ad4-176">XML 문서 데이터 검색을 위한 요구 사항</span><span class="sxs-lookup"><span data-stu-id="24ad4-176">Requirements for Retrieving XML Document Data</span></span>  
 <span data-ttu-id="24ad4-177">http 프로토콜을 사용할 경우 서버에서 XML 데이터를 반환하거나 XML 데이터가 XML `Query` 요소에 포함되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="24ad4-177">Using the http protocol, the server must return XML data or the XML data must be embedded in the XML `Query` element.</span></span> <span data-ttu-id="24ad4-178">http 프로토콜을 사용하여 XML 문서를 직접 참조하려면 해당 문서의 확장명이 .xml이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="24ad4-178">If you refer to an XML document directly using the http protocol, the extension must be .xml.</span></span>  
  
 <span data-ttu-id="24ad4-179">필요한 모든 데이터를 검색하는 XML 쿼리를 만드는 방법을 알고 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="24ad4-179">You must know how to create an XML query that retrieves all the data you need.</span></span> <span data-ttu-id="24ad4-180">요소 경로를 지정하지 않으면 XML 문서를 구문 분석하는 기본 동작에 따라 XML 문서의 리프 노드 컬렉션에 대한 첫 번째 사용 가능 경로가 선택됩니다.</span><span class="sxs-lookup"><span data-stu-id="24ad4-180">If you do not specify an element path, the default behavior for parsing an XML document is to select the first available path to a leaf-node collection in the XML document.</span></span> <span data-ttu-id="24ad4-181">XML 문서에 다른 형제 리프 노드 컬렉션에 대한 추가 경로가 포함되어 있는 경우 쿼리에 경로를 지정하지 않으면 해당 노드는 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="24ad4-181">If the XML document includes additional paths to other sibling leaf-node collections, those nodes will be ignored unless you specify a path in your query.</span></span>  
  
 <span data-ttu-id="24ad4-182">XQuery와 유사한 XML 구문을 사용하여 요소 경로를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="24ad4-182">You can provide an element path using XML syntax similar to XQuery.</span></span>  
  
 <span data-ttu-id="24ad4-183">자세한 내용은 msdn.microsoft.com의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [온라인 설명서](https://go.microsoft.com/fwlink/?linkid=121312)에서 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 설명서의 [XML 보고서 데이터를 위한 요소 경로 구문&#40;SSRS&#41;](element-path-syntax-for-xml-report-data-ssrs.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="24ad4-183">For more information, see [Element Path Syntax for XML Report Data &#40;SSRS&#41;](element-path-syntax-for-xml-report-data-ssrs.md) in the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] documentation in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [Books Online](https://go.microsoft.com/fwlink/?linkid=121312) on msdn.microsoft.com.</span></span>  
  
##  <a name="parameters"></a><a name="Parameters"></a> <span data-ttu-id="24ad4-184">매개 변수</span><span class="sxs-lookup"><span data-stu-id="24ad4-184">Parameters</span></span>  
 <span data-ttu-id="24ad4-185">쿼리는 매개 변수 식별을 위해 분석되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="24ad4-185">The query is not analyzed to identify parameters.</span></span>  
  
 <span data-ttu-id="24ad4-186">매개 변수를 추가하려면 **데이터 세트 속성** 대화 상자의 [매개 변수](../dataset-properties-dialog-box-parameters-report-builder.md) 페이지를 통해 직접 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="24ad4-186">To add parameters, you must create them manually through the **Parameter** page on the [Dataset Properties](../dataset-properties-dialog-box-parameters-report-builder.md) dialog box.</span></span>  
  
##  <a name="remarks"></a><a name="Remarks"></a> <span data-ttu-id="24ad4-187">주의</span><span class="sxs-lookup"><span data-stu-id="24ad4-187">Remarks</span></span>  
 <span data-ttu-id="24ad4-188">XML 데이터 확장 프로그램은 계층 구조가 아닌 테이블 형식 XML 데이터의 보고를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="24ad4-188">The XML data extension supports reporting from XML data that is tabular and not hierarchical.</span></span> <span data-ttu-id="24ad4-189">자세한 내용은 [외부 데이터 원본의 데이터 추가&#40;SSRS&#41;](add-data-from-external-data-sources-ssrs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="24ad4-189">For more information, see [Add Data from External Data Sources &#40;SSRS&#41;](add-data-from-external-data-sources-ssrs.md).</span></span>  
  
 <span data-ttu-id="24ad4-190">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스에서 XML 문서를 검색하는 작업은 기본적으로 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="24ad4-190">There is no built-in support for retrieving XML documents from a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database.</span></span>  
  
##  <a name="how-to-topics"></a><a name="HowTo"></a><span data-ttu-id="24ad4-191">방법 도움말 항목</span><span class="sxs-lookup"><span data-stu-id="24ad4-191">How-To Topics</span></span>  
 <span data-ttu-id="24ad4-192">이 섹션에서는 데이터 연결, 데이터 원본 및 데이터 세트를 사용하는 방법을 단계별로 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="24ad4-192">This section contains step-by-step instructions for working with data connections, data sources, and datasets.</span></span>  
  
 [<span data-ttu-id="24ad4-193">데이터 연결이 나 데이터 원본 &#40;보고서 작성기 및 SSRS를 추가 하 고 확인&#41;</span><span class="sxs-lookup"><span data-stu-id="24ad4-193">Add and Verify a Data Connection or Data Source &#40;Report Builder and SSRS&#41;</span></span>](add-and-verify-a-data-connection-report-builder-and-ssrs.md)  
  
 [<span data-ttu-id="24ad4-194">공유 데이터 세트 또는 포함된 데이터 세트 만들기&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="24ad4-194">Create a Shared Dataset or Embedded Dataset &#40;Report Builder and SSRS&#41;</span></span>](create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md)  
  
 [<span data-ttu-id="24ad4-195">데이터 세트에 필터 추가&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="24ad4-195">Add a Filter to a Dataset &#40;Report Builder and SSRS&#41;</span></span>](add-a-filter-to-a-dataset-report-builder-and-ssrs.md)  
  
##  <a name="related-sections"></a><a name="Related"></a> <span data-ttu-id="24ad4-196">관련 섹션</span><span class="sxs-lookup"><span data-stu-id="24ad4-196">Related Sections</span></span>  
 <span data-ttu-id="24ad4-197">설명서의 다음 섹션에서는 보고서 데이터에 대한 깊이 있는 개념 정보를 제공하며, 데이터와 관련된 보고서 부분을 정의, 사용자 지정 및 사용하는 방법을 절차적인 측면에서 소개합니다.</span><span class="sxs-lookup"><span data-stu-id="24ad4-197">These sections of the documentation provide in-depth conceptual information about report data, as well as procedural information about how to define, customize, and use parts of a report that are related to data.</span></span>  
  
 [<span data-ttu-id="24ad4-198">보고서 &#40;보고서 작성기 및 SSRS&#41;에 데이터를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="24ad4-198">Add Data to a Report &#40;Report Builder and SSRS&#41;</span></span>](report-datasets-ssrs.md)  
 <span data-ttu-id="24ad4-199">보고서의 데이터 액세스에 대한 개요를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="24ad4-199">Provides an overview of accessing data for your report.</span></span>  
  
 [<span data-ttu-id="24ad4-200">보고서 작성기의 데이터 연결, 데이터 원본 및 연결 문자열</span><span class="sxs-lookup"><span data-stu-id="24ad4-200">Data Connections, Data Sources, and Connection Strings in Report Builder</span></span>](../data-connections-data-sources-and-connection-strings-in-report-builder.md)  
 <span data-ttu-id="24ad4-201">데이터 연결 및 데이터 원본에 대한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="24ad4-201">Provides information about data connections and data sources.</span></span>  
  
 [<span data-ttu-id="24ad4-202">보고서 포함된 데이터 세트 및 공유 데이터 세트&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="24ad4-202">Report Embedded Datasets and Shared Datasets &#40;Report Builder and SSRS&#41;</span></span>](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)  
 <span data-ttu-id="24ad4-203">포함된 데이터 세트 및 공유 데이터 세트에 대한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="24ad4-203">Provides information about embedded and shared datasets.</span></span>  
  
 [<span data-ttu-id="24ad4-204">데이터 세트 필드 컬렉션&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="24ad4-204">Dataset Fields Collection &#40;Report Builder and SSRS&#41;</span></span>](dataset-fields-collection-report-builder-and-ssrs.md)  
 <span data-ttu-id="24ad4-205">쿼리에 의해 생성되는 데이터 세트 필드 컬렉션에 대한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="24ad4-205">Provides information about the dataset field collection generated by the query.</span></span>  
  
 <span data-ttu-id="24ad4-206">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [온라인 설명서](https://go.microsoft.com/fwlink/?linkid=121312)에 있는 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 설명서의 [Reporting Services&#40;SSRS&#41;에서 지원하는 데이터 원본](../create-deploy-and-manage-mobile-and-paginated-reports.md).</span><span class="sxs-lookup"><span data-stu-id="24ad4-206">[Data Sources Supported by Reporting Services &#40;SSRS&#41;](../create-deploy-and-manage-mobile-and-paginated-reports.md) in the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] documentation in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [Books Online](https://go.microsoft.com/fwlink/?linkid=121312).</span></span>  
 <span data-ttu-id="24ad4-207">각 데이터 확장 프로그램의 플랫폼 및 버전 지원에 대한 자세한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="24ad4-207">Provides in-depth information about platform and version support for each data extension.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24ad4-208">참고 항목</span><span class="sxs-lookup"><span data-stu-id="24ad4-208">See Also</span></span>  
 <span data-ttu-id="24ad4-209">[보고서 매개 변수 &#40;보고서 작성기 및 보고서 디자이너&#41;](../report-design/report-parameters-report-builder-and-report-designer.md) </span><span class="sxs-lookup"><span data-stu-id="24ad4-209">[Report Parameters &#40;Report Builder and Report Designer&#41;](../report-design/report-parameters-report-builder-and-report-designer.md) </span></span>  
 <span data-ttu-id="24ad4-210">[데이터 필터링, 그룹화 및 정렬 &#40;보고서 작성기 및 SSRS&#41;](../report-design/filter-group-and-sort-data-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="24ad4-210">[Filter, Group, and Sort Data &#40;Report Builder and SSRS&#41;](../report-design/filter-group-and-sort-data-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="24ad4-211">식&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="24ad4-211">Expressions &#40;Report Builder and SSRS&#41;</span></span>](../report-design/expressions-report-builder-and-ssrs.md)  
  
  
