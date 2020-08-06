---
title: XML 보고서 데이터를 위한 XML 쿼리 구문(SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- namespaces [Reporting Services]
- data processing extensions [Reporting Services], data sources
- xmldp [Reporting Services]
- XML [Reporting Services], data retrieval
ms.assetid: d203886f-faa1-4a02-88f5-dd4c217181ef
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 62dde2b3ab18b5edb5c3786d39173fea3a0854ac
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639315"
---
# <a name="xml-query-syntax-for-xml-report-data-ssrs"></a><span data-ttu-id="ddf8a-102">XML 보고서 데이터를 위한 XML 쿼리 구문(SSRS)</span><span class="sxs-lookup"><span data-stu-id="ddf8a-102">XML Query Syntax for XML Report Data (SSRS)</span></span>
  <span data-ttu-id="ddf8a-103">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]에서는 XML 데이터 원본에 대한 데이터 세트를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ddf8a-103">In [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], you can create datasets for XML data sources.</span></span> <span data-ttu-id="ddf8a-104">데이터 원본을 정의한 후 데이터 세트에 대한 쿼리를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ddf8a-104">After you define a data source, you create a query for the dataset.</span></span> <span data-ttu-id="ddf8a-105">데이터 원본이 가리키는 XML 데이터의 형식에 따라 XML `Query`나 요소 경로를 포함하여 데이터 세트 쿼리를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ddf8a-105">Depending on the type of XML data pointed to by the data source, you create the dataset query by including an XML `Query` or an element path.</span></span> <span data-ttu-id="ddf8a-106">XML은 `Query` **\<Query>** 태그로 시작 하며 데이터 원본에 따라 달라 지는 네임 스페이스와 xml 요소를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddf8a-106">An XML `Query` starts with a **\<Query>** tag and includes namespaces and XML elements that vary depending on the data source.</span></span> <span data-ttu-id="ddf8a-107">요소 경로는 네임스페이스로부터 독립적이며 기본 XML 데이터에서 사용할 노드 및 노드 특성을 XPath 형식 구문으로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ddf8a-107">An element path is namespace-independent and specifies which nodes and node attributes to use from the underlying XML data with an XPath-like syntax.</span></span> <span data-ttu-id="ddf8a-108">요소 경로에 대한 자세한 내용은 [XML 보고서 데이터를 위한 요소 경로 구문&#40;SSRS&#41;](report-data-ssrs.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ddf8a-108">For more information about element paths, see [Element Path Syntax for XML Report Data &#40;SSRS&#41;](report-data-ssrs.md).</span></span>  
  
 <span data-ttu-id="ddf8a-109">다음과 같은 형식의 XML 데이터에 대한 XML 데이터 원본을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ddf8a-109">You can create an XML data source for the following types of XML data:</span></span>  
  
-   <span data-ttu-id="ddf8a-110">http 프로토콜을 사용하는 URL이 가리키는 XML 문서</span><span class="sxs-lookup"><span data-stu-id="ddf8a-110">Xml documents pointed to by a URL using http protocol</span></span>  
  
-   <span data-ttu-id="ddf8a-111">XML 데이터를 반환하는 웹 서비스 엔드포인트</span><span class="sxs-lookup"><span data-stu-id="ddf8a-111">Web service endpoints that return XML data</span></span>  
  
-   <span data-ttu-id="ddf8a-112">포함 XML 데이터</span><span class="sxs-lookup"><span data-stu-id="ddf8a-112">Embedded XML data</span></span>  
  
 <span data-ttu-id="ddf8a-113">XML `Query`나 요소 경로를 지정하는 방법은 XML 데이터 형식에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="ddf8a-113">How you specify an XML `Query` or an element path depends on the type of XML data.</span></span>  
  
 <span data-ttu-id="ddf8a-114">XML 문서의 경우 XML `Query`는 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="ddf8a-114">For an XML document, the XML `Query` is optional.</span></span> <span data-ttu-id="ddf8a-115">이 쿼리가 포함되어 있지 않으면 선택적 XML `ElementPath`를 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ddf8a-115">If it is included, it can contain an optional XML `ElementPath`.</span></span> <span data-ttu-id="ddf8a-116">XML `ElementPath` 값에는 요소 경로 구문이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="ddf8a-116">The value of the XML `ElementPath` uses the element path syntax.</span></span> <span data-ttu-id="ddf8a-117">데이터 원본의 XML 데이터에 필요한 경우 XML `Query` 및 XML `ElementPath`를 포함하여 네임스페이스를 올바르게 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ddf8a-117">You include the XML `Query` and XML `ElementPath` to process namespaces correctly when it is needed by the XML data from the data source.</span></span>  
  
 <span data-ttu-id="ddf8a-118">연결 문자열 URL이 가리키는 웹 서비스 엔드포인트의 경우 XML `Query`는 웹 서비스 메서드나 SOAP 동작 또는 둘 모두를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="ddf8a-118">For a Web service endpoint pointed to by a connection string URL, the XML `Query` defines either the Web service method, the SOAP action, or both.</span></span> <span data-ttu-id="ddf8a-119">XML 데이터 공급자는 보고서에 사용할 XML 데이터를 검색하는 웹 서비스 요청을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ddf8a-119">The XML data provider creates a Web service request that retrieves XML data to use for the report.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ddf8a-120">웹 서비스 네임스페이스에 슬래시(`/)` 문자가 포함되어 있으면 XML 데이터 처리 확장 프로그램에서 해당 네임스페이스를 올바르게 가져올 수 있도록 웹 서비스 메서드와 SOAP 동작을 모두 포함하십시오.</span><span class="sxs-lookup"><span data-stu-id="ddf8a-120">When a Web service namespace includes a forward slash (`/)` character, include both the Web service method and the SOAP action so that the XML data processing extension can derive the namespace correctly.</span></span>  
  
 <span data-ttu-id="ddf8a-121">포함 XML 문서의 경우 XML `Query`는 사용할 포함 XML 데이터를 정의하고 선택적 네임스페이스와 선택적 XML `ElementPath`를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="ddf8a-121">For an embedded XML document, the XML `Query` defines the embedded XML data to use, includes optional namespaces, and contains an optional XML `ElementPath`..</span></span>  
  
## <a name="specifying-query-parameters-for-xml-data"></a><span data-ttu-id="ddf8a-122">XML 데이터의 쿼리 매개 변수 지정</span><span class="sxs-lookup"><span data-stu-id="ddf8a-122">Specifying Query Parameters for XML Data</span></span>  
 <span data-ttu-id="ddf8a-123">XML 문서의 쿼리 매개 변수를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ddf8a-123">You can specify query parameters for XML documents.</span></span>  
  
-   <span data-ttu-id="ddf8a-124">URL 요청의 경우 쿼리 매개 변수는 표준 URL 매개 변수로 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="ddf8a-124">For URL requests, the query parameters are included as standard URL parameters.</span></span>  
  
-   <span data-ttu-id="ddf8a-125">웹 서비스 요청의 경우 쿼리 매개 변수는 웹 서비스 메서드에 전달됩니다.</span><span class="sxs-lookup"><span data-stu-id="ddf8a-125">For Web service requests, query parameters are passed to the Web service method.</span></span> <span data-ttu-id="ddf8a-126">쿼리 매개 변수를 정의하려면 **데이터 세트 속성** 대화 상자의 **매개 변수** 페이지를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="ddf8a-126">To define a query parameter, use the **Parameters** page of the **Dataset Properties** dialog box.</span></span> <span data-ttu-id="ddf8a-127">자세한 내용은 [데이터 세트 속성 대화 상자, 매개 변수](dataset-properties-dialog-box-parameters.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ddf8a-127">For more information, see [Dataset Properties Dialog Box, Parameters](dataset-properties-dialog-box-parameters.md).</span></span>  
  
### <a name="example"></a><span data-ttu-id="ddf8a-128">예제</span><span class="sxs-lookup"><span data-stu-id="ddf8a-128">Example</span></span>  
 <span data-ttu-id="ddf8a-129">다음 표의 예에서는 보고서 서버 웹 서비스, XML 문서 및 포함 XML 데이터에서 데이터를 검색하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ddf8a-129">The examples in the following table illustrate how to retrieve data from the Report Server Web service, an XML document, and embedded XML data.</span></span>  
  
|<span data-ttu-id="ddf8a-130">XML 데이터 원본</span><span class="sxs-lookup"><span data-stu-id="ddf8a-130">XML data source</span></span>|<span data-ttu-id="ddf8a-131">쿼리 예</span><span class="sxs-lookup"><span data-stu-id="ddf8a-131">Query example</span></span>|  
|---------------------|-------------------|  
|<span data-ttu-id="ddf8a-132">웹 서비스 XML 데이터( ListChildren 메서드 사용)</span><span class="sxs-lookup"><span data-stu-id="ddf8a-132">Web service XML data from ListChildren method.</span></span>|`<Query>`<br /><br /> `<Method Name="ListChildren" Namespace="https://schemas.microsoft.com/sqlserver/2005/06/30/reporting/reportingservices" />`<br /><br /> `</Query>`|  
|<span data-ttu-id="ddf8a-133">웹 서비스 XML 데이터(SoapAction 사용)</span><span class="sxs-lookup"><span data-stu-id="ddf8a-133">Web service XML data from SoapAction.</span></span>|`<Query xmlns=namespace>`<br /><br /> `<SoapAction>http://schemas/microsoft.com/sqlserver/2005/03/23/reporting/reportingservices/ListChildren</SoapAction>`<br /><br /> `</Query>`|  
|<span data-ttu-id="ddf8a-134">네임스페이스를 사용하는 XML 문서 또는 포함 XML 데이터</span><span class="sxs-lookup"><span data-stu-id="ddf8a-134">XML Document or embedded XML data that uses namespaces.</span></span><br /><br /> <span data-ttu-id="ddf8a-135">요소 경로의 네임스페이스를 지정하는 쿼리 요소</span><span class="sxs-lookup"><span data-stu-id="ddf8a-135">Query element specifying namespaces for an element path.</span></span>|`<Query xmlns:es="https://schemas.microsoft.com/StandardSchemas/ExtendedSales">`<br /><br /> `<ElementPath>/Customers/Customer/Orders/Order/es:LineItems/es:LineItem</ElementPath>`<br /><br /> `</Query>`|  
|<span data-ttu-id="ddf8a-136">포함 XML 문서</span><span class="sxs-lookup"><span data-stu-id="ddf8a-136">Embedded XML document.</span></span>|`<Query>`<br /><br /> `<XmlData>`<br /><br /> `<Customers>`<br /><br /> `<Customer ID="1">Bobby</Customer>`<br /><br /> `</Customers>`<br /><br /> `</XmlData>`<br /><br /> `<ElementPath>Customer {@}</ElementPath>`<br /><br /> `</Query>`|  
|<span data-ttu-id="ddf8a-137">기본값을 사용하는 XML 문서</span><span class="sxs-lookup"><span data-stu-id="ddf8a-137">XML document that uses default.</span></span>|<span data-ttu-id="ddf8a-138">*No query*입니다.</span><span class="sxs-lookup"><span data-stu-id="ddf8a-138">*No query*.</span></span><br /><br /> <span data-ttu-id="ddf8a-139">요소 경로는 XML 문서 자체에서 파생되며 네임스페이스로부터 독립적입니다.</span><span class="sxs-lookup"><span data-stu-id="ddf8a-139">The element path is derived from the XML document itself and is namespace-independent.</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="ddf8a-140">첫 번째 웹 서비스 예에서는 <xref:ReportService2006.ReportingService2006.ListChildren%2A> 메서드 사용)</span><span class="sxs-lookup"><span data-stu-id="ddf8a-140">The first Web service example lists the contents of the report server that uses the <xref:ReportService2006.ReportingService2006.ListChildren%2A> method.</span></span> <span data-ttu-id="ddf8a-141">이 쿼리를 실행하려면 새 데이터 원본을 만들고 연결 문자열을 http://localhost/reportserver/reportservice2006.asmx로 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddf8a-141">To run this query, you must create a new data source and set the connection string to http://localhost/reportserver/reportservice2006.asmx.</span></span> <span data-ttu-id="ddf8a-142"><xref:ReportService2006.ReportingService2006.ListChildren%2A> 메서드는 `Item` 및 `Recursive`의 두 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="ddf8a-142">The <xref:ReportService2006.ReportingService2006.ListChildren%2A> method takes two parameters: `Item` and `Recursive`.</span></span> <span data-ttu-id="ddf8a-143">`Item`의 기본값은 `/`로 설정하고 `Recursive`의 기본값은 `1`로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="ddf8a-143">Set the default value for `Item` to `/` and `Recursive` to `1`.</span></span>  
  
## <a name="specifying-namespaces"></a><span data-ttu-id="ddf8a-144">네임스페이스 지정</span><span class="sxs-lookup"><span data-stu-id="ddf8a-144">Specifying Namespaces</span></span>  
 <span data-ttu-id="ddf8a-145">XML `Query` 요소를 사용하여 데이터 원본의 XML 데이터에 사용된 네임스페이스를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ddf8a-145">Use the XML `Query` element to specify the namespaces that are used in the XML data from the data source.</span></span> <span data-ttu-id="ddf8a-146">다음 XML 쿼리에서는 `sales` 네임스페이스를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="ddf8a-146">The following XML query uses the namespace `sales`.</span></span> <span data-ttu-id="ddf8a-147">`sales:LineItems` 및 `sales:LineItem`의 XML `ElementPath` 노드는 `sales` 네임스페이스를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="ddf8a-147">The XML `ElementPath` nodes for `sales:LineItems` and `sales:LineItem` use the namespace `sales`.</span></span>  
  
```  
<Query xmlns:sales=  
"https://schemas.microsoft.com/StandardSchemas/ExtendedSales">  
   <SoapAction>  
      https://schemas.microsoft.com/SalesWebService/ListOrders   
   </SoapAction>  
   <ElementPath>  
      Customers/Customer/Orders/Order/sales:LineItems/sales:LineItem  
   </ElementPath>  
</Query>  
```  
  
 <span data-ttu-id="ddf8a-148">기본 네임스페이스가 빈 상태로 유지되도록 데이터 공급자 네임스페이스를 지정하려면 `xmldp`를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="ddf8a-148">To specify the data provider namespace so that the default namespace remains empty, use `xmldp`.</span></span> <span data-ttu-id="ddf8a-149">다음 예제에서 이를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ddf8a-149">This is shown in the following example.</span></span>  
  
### <a name="example"></a><span data-ttu-id="ddf8a-150">예제</span><span class="sxs-lookup"><span data-stu-id="ddf8a-150">Example</span></span>  
 <span data-ttu-id="ddf8a-151">다음 예에서는 XML 문서 DPNamespace.xml을 사용하며 이 문서는 표 아래에 제공되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ddf8a-151">The following examples use the XML document DPNamespace.xml, which is provided for illustration after the table.</span></span> <span data-ttu-id="ddf8a-152">이 표에서는 네임스페이스 접두사가 포함된 XML ElementPath 구문의 두 가지 예를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ddf8a-152">This table shows two examples of XML ElementPath syntax that includes namespace prefixes.</span></span>  
  
|<span data-ttu-id="ddf8a-153">XML 쿼리 요소</span><span class="sxs-lookup"><span data-stu-id="ddf8a-153">XML Query Element</span></span>|<span data-ttu-id="ddf8a-154">데이터 세트의 결과 필드</span><span class="sxs-lookup"><span data-stu-id="ddf8a-154">Resulting fields in the dataset</span></span>|  
|-----------------------|-------------------------------------|  
|\<Query/>|<span data-ttu-id="ddf8a-155">값 A: `https://schemas.microsoft.com/..` .</span><span class="sxs-lookup"><span data-stu-id="ddf8a-155">Value A: `https://schemas.microsoft.com/..`.</span></span><br /><br /> <span data-ttu-id="ddf8a-156">값 B: `https://schemas.microsoft.com/..` .</span><span class="sxs-lookup"><span data-stu-id="ddf8a-156">Value B: `https://schemas.microsoft.com/..`.</span></span><br /><br /> <span data-ttu-id="ddf8a-157">값 C: `https://schemas.microsoft.com/.` .</span><span class="sxs-lookup"><span data-stu-id="ddf8a-157">Value C: `https://schemas.microsoft.com/.`..</span></span>|  
|\<xmldp:Query xmlns:xmldp="https://schemas.microsoft.com/sqlserver/2005/02/reporting/XmlDPQuery" xmlns:ns="https://schemas.microsoft.com/..."><br /><br /> <span data-ttu-id="ddf8a-158">\<xmldp:ElementPath>Root {} /ns: Element2/Node\</xmldp:ElementPath></span><span class="sxs-lookup"><span data-stu-id="ddf8a-158">\<xmldp:ElementPath>Root {}/ns:Element2/Node\</xmldp:ElementPath></span></span><br /><br /> \</xmldp:Query>|<span data-ttu-id="ddf8a-159">Value D</span><span class="sxs-lookup"><span data-stu-id="ddf8a-159">Value D</span></span><br /><br /> <span data-ttu-id="ddf8a-160">Value E</span><span class="sxs-lookup"><span data-stu-id="ddf8a-160">Value E</span></span><br /><br /> <span data-ttu-id="ddf8a-161">Value F</span><span class="sxs-lookup"><span data-stu-id="ddf8a-161">Value F</span></span>|  
  
#### <a name="xml-document-dpnamespacexml"></a><span data-ttu-id="ddf8a-162">XML 문서: DPNamespace.xml</span><span class="sxs-lookup"><span data-stu-id="ddf8a-162">XML document: DPNamespace.xml</span></span>  
 <span data-ttu-id="ddf8a-163">이 XML을 복사한 후 보고서 디자이너에서 XML 데이터 원본으로 사용할 수 있는 URL에 저장할 수 있습니다(예: http://localhost/DPNamespace.xml).</span><span class="sxs-lookup"><span data-stu-id="ddf8a-163">You can copy this XML and save it to a URL available for Report Designer to use as an XML data source: for example, http://localhost/DPNamespace.xml.</span></span>  
  
```  
<Root xmlns:ns="https://schemas.microsoft.com/...">  
   <ns:Element1>  
      <Node>Value A</Node>  
      <Node>Value B</Node>  
      <Node>Value C</Node>  
   </ns:Element1>  
   <ns:Element2>  
      <Node>Value D</Node>  
      <Node>Value E</Node>  
      <Node>Value F</Node>  
   </ns:Element2>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ddf8a-164">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ddf8a-164">See Also</span></span>  
 <span data-ttu-id="ddf8a-165">[SSRS&#41;&#40;XML 연결 형식](xml-connection-type-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="ddf8a-165">[XML Connection Type &#40;SSRS&#41;](xml-connection-type-ssrs.md) </span></span>  
 [<span data-ttu-id="ddf8a-166">Reporting Services&#40;SSRS&#41; 자습서</span><span class="sxs-lookup"><span data-stu-id="ddf8a-166">Reporting Services Tutorials &#40;SSRS&#41;</span></span>](../reporting-services-tutorials-ssrs.md)  
  
  
