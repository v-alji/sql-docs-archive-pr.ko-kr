---
title: 애플리케이션 코드에서 FOR XML 결과 사용 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- FOR XML clause, application code usage
- XML [SQL Server], FOR XML clause
- ASP.NET [SQL Server]
- .NET Framework [SQL Server], FOR XML data
- ADO [SQL Server]
- XML data islands [SQL Server]
- data islands [SQL Server]
ms.assetid: 41ae67bd-ece9-49ea-8062-c8d658ab4154
author: rothja
ms.author: jroth
ms.openlocfilehash: 3cabe7e65cb53a28a370615ed84e38ba2b8db44c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659852"
---
# <a name="use-for-xml-results-in-application-code"></a><span data-ttu-id="6d728-102">애플리케이션 코드에서 FOR XML 결과 사용</span><span class="sxs-lookup"><span data-stu-id="6d728-102">Use FOR XML Results in Application Code</span></span>
  <span data-ttu-id="6d728-103">SQL 쿼리에서 FOR XML 절을 사용하면 쿼리 결과 검색은 물론 XML 데이터로 캐스팅할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6d728-103">By using FOR XML clauses with SQL queries, you can retrieve and even cast query results as XML data.</span></span> <span data-ttu-id="6d728-104">이 기능을 사용하면 XML 애플리케이션 코드에서 FOR XML 쿼리 결과를 사용할 수 있을 때 다음을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6d728-104">This functionality allows you to do the following when FOR XML query results can be used in XML application code:</span></span>  
  
-   <span data-ttu-id="6d728-105">SQL 테이블에서 [XML 데이터&#40;SQL Server&#41;](xml-data-sql-server.md) 값 인스턴스를 쿼리합니다.</span><span class="sxs-lookup"><span data-stu-id="6d728-105">Query SQL tables for instances of [XML Data &#40;SQL Server&#41;](xml-data-sql-server.md) values</span></span>  
  
-   <span data-ttu-id="6d728-106">[TYPE Directive in FOR XML Queries](type-directive-in-for-xml-queries.md) 을 적용하여 XML 유형의 텍스트 또는 이미지 형식의 데이터를 포함하는 쿼리 결과를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="6d728-106">Apply the [TYPE Directive in FOR XML Queries](type-directive-in-for-xml-queries.md) to return the result of queries that contain text or image typed data as XML</span></span>  
  
 <span data-ttu-id="6d728-107">이 항목에서는 이러한 접근 방식을 보여 주는 예를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="6d728-107">This topic provides examples that demonstrate these approaches.</span></span>  
  
## <a name="retrieving-for-xml-data-with-ado-and-xml-data-islands"></a><span data-ttu-id="6d728-108">ADO 및 XML 데이터 아일랜드로 FOR XML 데이터 검색</span><span class="sxs-lookup"><span data-stu-id="6d728-108">Retrieving FOR XML Data with ADO and XML Data Islands</span></span>  
 <span data-ttu-id="6d728-109">ADO `Stream` 개체나 ASP(Active Server Pages) `IStream` 및 `Request` 개체와 같이 COM `Response` 인터페이스를 지원하는 다른 개체를 사용하여 FOR XML 쿼리를 사용할 때 결과를 포함시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6d728-109">The ADO `Stream` object or other objects that support the COM `IStream` interface, such as the Active Server Pages (ASP) `Request` and `Response` objects, can be used to contain the results when you are working with FOR XML queries.</span></span>  
  
 <span data-ttu-id="6d728-110">예를 들어 다음 ASP 코드에서는 AdventureWorks 예제 데이터베이스의 Sales.Store 테이블에서 `xml` 데이터 형식의 열인 Demographics를 쿼리한 결과를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="6d728-110">For example, the following ASP code shows the results of querying an `xml` data type column, Demographics, in the Sales.Store table of the AdventureWorks sample database.</span></span> <span data-ttu-id="6d728-111">특히 이 쿼리는 이 열의 항목 값에서 CustomerID가 3인 행을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="6d728-111">Specifically, the query looks for the instance value of this column for the row where the CustomerID is equal to 3.</span></span>  
  
```  
<!-- BeginRecordAndStreamVBS -->  
<%@ LANGUAGE = VBScript %>  
<!-- %  Option Explicit      % -->  
<!-- 'Request.ServerVariables("SERVER_NAME") & ";" & _ -->  
<HTML>  
<HEAD>  
<META NAME="GENERATOR" Content="Microsoft Developer Studio"/>  
<META HTTP-EQUIV="Content-Type" content="text/html"; charset="iso-8859-1">  
<TITLE>FOR XML Query Example</TITLE>  
<STYLE>  
   BODY  
   {  
      FONT-FAMILY: Tahoma;  
      FONT-SIZE: 8pt;  
      OVERFLOW: auto  
   }  
   H3  
   {  
      FONT-FAMILY: Tahoma;  
      FONT-SIZE: 8pt;  
      OVERFLOW: auto  
   }  
</STYLE>  
  
<!-- #include file="adovbs.inc" -->  
<%  
   Response.Write "<H3>Server-side processing</H3>"  
   Response.Write "Page Generated @ " & Now() & "<BR/>"  
   Dim adoConn  
   Set adoConn = Server.CreateObject("ADODB.Connection")  
   Dim sConn  
   sConn = "Provider=SQLOLEDB;Data Source=(local);" & _  
            "Initial Catalog=AdventureWorks;Integrated Security=SSPI;"  
   Response.write "Connect String = " & sConn & "<BR/>"  
   adoConn.ConnectionString = sConn  
   adoConn.CursorLocation = adUseClient  
   adoConn.Open  
   Response.write "ADO Version = " & adoConn.Version & "<BR/>"  
   Response.write "adoConn.State = " & adoConn.State & "<BR/>"  
   Dim adoCmd  
   Set adoCmd = Server.CreateObject("ADODB.Command")  
   Set adoCmd.ActiveConnection = adoConn  
   Dim sQuery  
   sQuery = "<ROOT xmlns:sql='urn:schemas-microsoft-com:xml-sql'><sql:query>SELECT Demographics from Sales.Store WHERE CustomerID = 3 FOR XML AUTO</sql:query></ROOT>"  
   Response.write "Query String = " & sQuery & "<BR/>"  
   Dim adoStreamQuery  
   Set adoStreamQuery = Server.CreateObject("ADODB.Stream")  
   adoStreamQuery.Open  
   adoStreamQuery.WriteText sQuery, adWriteChar  
   adoStreamQuery.Position = 0  
   adoCmd.CommandStream = adoStreamQuery  
   adoCmd.Dialect = "{5D531CB2-E6Ed-11D2-B252-00C04F681B71}"  
   Response.write "Pushing XML to client for processing "  & "<BR/>"  
   adoCmd.Properties("Output Stream") = Response  
   Response.write "<XML ID='MyDataIsle'>"  
   adoCmd.Execute , , 1024  
   Response.write "</XML>"  
%>  
<SCRIPT language="VBScript" For="window" Event="onload">  
   Dim xmlDoc  
   Set xmlDoc = MyDataIsle.XMLDocument  
   Dim root  
   Set root = xmlDoc.documentElement.childNodes.Item(0).childNodes.Item(0).childNodes.Item(0)  
   For each child in root.childNodes  
      dim OutputXML  
      OutputXML = document.all("log").innerHTML  
      document.all("log").innerHTML = OutputXML & "<LI><B>" & child.nodeName &  ":</B>  " & child.Text  & "</LI>"  
   Next  
   MsgBox xmlDoc.xml  
</SCRIPT>  
</HEAD>  
<BODY>  
   <H3>Client-side processing of XML Document MyDataIsle</H3>  
   <UL id=log>  
   </UL>  
</BODY>  
</HTML>  
<!-- EndRecordAndStreamVBS -->  
```  
  
 <span data-ttu-id="6d728-112">이 ASP 페이지 예에는 ADO를 사용하여 FOR XML 쿼리를 실행하고 XML 데이터 아일랜드인 MyDataIsle로 XML 결과를 반환하는 서버 쪽 VBScript가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="6d728-112">This example ASP page contains server-side VBScript that uses ADO to execute the FOR XML query and return the XML results in an XML data island, MyDataIsle.</span></span> <span data-ttu-id="6d728-113">이 XML 데이터 아일랜드는 추가 클라이언트 쪽 처리를 위해 브라우저에 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="6d728-113">This XML data island is then returned in the browser for additional client-side processing.</span></span> <span data-ttu-id="6d728-114">그런 다음 추가 클라이언트 쪽 VBScript 코드를 사용하여 XML 데이터 아일랜드의 콘텐츠를 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="6d728-114">Additional client-side VBScript code is then used to process the contents of the XML data island.</span></span> <span data-ttu-id="6d728-115">이 프로세스는 콘텐츠를 결과 DHTML의 일부로 표시하고 XML 데이터 아일랜드의 처리된 콘텐츠를 표시하는 메시지 상자를 열기 전에 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="6d728-115">This process is performed before displaying the contents as part of the resultant DHTML and opening a message box to show the preprocessed contents of the XML data island.</span></span>  
  
#### <a name="to-test-this-example"></a><span data-ttu-id="6d728-116">이 예를 테스트하려면</span><span class="sxs-lookup"><span data-stu-id="6d728-116">To test this example</span></span>  
  
1.  <span data-ttu-id="6d728-117">IIS가 설치되어 있으며 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에 대한 AdventureWorks 예제 데이터베이스가 설치되었는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="6d728-117">Verify that IIS is installed and that the AdventureWorks sample database for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] has been installed.</span></span>  
  
     <span data-ttu-id="6d728-118">이 예에서는 ASP 지원이 설정된 인터넷 정보 서비스(IIS) 버전 5.0 이상이 설치되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6d728-118">This example requires that Internet Information Services (IIS) version 5.0, or later versions, are installed with ASP support enabled.</span></span> <span data-ttu-id="6d728-119">또한 AdventureWorks 예제 데이터베이스가 설치되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6d728-119">Also, the AdventureWorks sample database has to be installed.</span></span>  
  
2.  <span data-ttu-id="6d728-120">이전에 제공된 코드 예를 복사하여 사용하는 XML 또는 텍스트 편집기에 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="6d728-120">Copy the code example that was previously provided and paste it into the XML or text editor that you use.</span></span> <span data-ttu-id="6d728-121">IIS에 사용되는 루트 디렉터리에 파일을 RetrieveResults.asp로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="6d728-121">Save the file as RetrieveResults.asp in the root directory that is used for IIS.</span></span> <span data-ttu-id="6d728-122">일반적으로 루트 디렉터리의 위치는 C:\Inetpub\wwwroot입니다.</span><span class="sxs-lookup"><span data-stu-id="6d728-122">Typically, this is C:Inetpub\wwwroot.</span></span>  
  
3.  <span data-ttu-id="6d728-123">다음 URL을 사용하여 브라우저 창에서 ASP 페이지를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="6d728-123">Open the ASP page in a browser window by using the following URL.</span></span> <span data-ttu-id="6d728-124">먼저 'MyServer'를 "localhost" 또는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 와 IIS가 설치된 서버의 실제 이름으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="6d728-124">First, replace 'MyServer' with either "localhost" or the actual name of the server where [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and IIS are installed.</span></span>  
  
    ```  
    http://MyServer/RetrieveResults.asp  
    ```  
  
 <span data-ttu-id="6d728-125">생성된 HTML 페이지 결과는 다음 예제 출력과 유사하게 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="6d728-125">The generated HTML page results that appear will be similar to the following sample output:</span></span>  
  
##### <a name="server-side-processing"></a><span data-ttu-id="6d728-126">서버 쪽 처리</span><span class="sxs-lookup"><span data-stu-id="6d728-126">Server-side processing</span></span>  
 <span data-ttu-id="6d728-127">Page Generated \@ 3/11/2006 3:36:02 PM</span><span class="sxs-lookup"><span data-stu-id="6d728-127">Page Generated \@ 3/11/2006 3:36:02 PM</span></span>  
  
 <span data-ttu-id="6d728-128">Connect String = Provider=SQLOLEDB;Data Source=MyServer;Initial Catalog=AdventureWorks;Integrated Security=SSPI;</span><span class="sxs-lookup"><span data-stu-id="6d728-128">Connect String = Provider=SQLOLEDB;Data Source=MyServer;Initial Catalog=AdventureWorks;Integrated Security=SSPI;</span></span>  
  
 <span data-ttu-id="6d728-129">ADO Version = 2.8</span><span class="sxs-lookup"><span data-stu-id="6d728-129">ADO Version = 2.8</span></span>  
  
 <span data-ttu-id="6d728-130">adoConn.State = 1</span><span class="sxs-lookup"><span data-stu-id="6d728-130">adoConn.State = 1</span></span>  
  
 <span data-ttu-id="6d728-131">Query String = SELECT Demographics from Sales.Store WHERE CustomerID = 3 FOR XML AUTO</span><span class="sxs-lookup"><span data-stu-id="6d728-131">Query String = SELECT Demographics from Sales.Store WHERE CustomerID = 3 FOR XML AUTO</span></span>  
  
 <span data-ttu-id="6d728-132">Pushing XML to client for processing</span><span class="sxs-lookup"><span data-stu-id="6d728-132">Pushing XML to client for processing</span></span>  
  
##### <a name="client-side-processing-of-xml-document-mydataisle"></a><span data-ttu-id="6d728-133">XML 문서 MyDataIsle의 클라이언트 쪽 처리</span><span class="sxs-lookup"><span data-stu-id="6d728-133">Client-side processing of XML Document MyDataIsle</span></span>  
  
-   <span data-ttu-id="6d728-134">**AnnualSales:** 1500000</span><span class="sxs-lookup"><span data-stu-id="6d728-134">**AnnualSales:** 1500000</span></span>  
  
-   <span data-ttu-id="6d728-135">**AnnualRevenue:** 150000</span><span class="sxs-lookup"><span data-stu-id="6d728-135">**AnnualRevenue:** 150000</span></span>  
  
-   <span data-ttu-id="6d728-136">**BankName:** Primary International</span><span class="sxs-lookup"><span data-stu-id="6d728-136">**BankName:** Primary International</span></span>  
  
-   <span data-ttu-id="6d728-137">**BusinessType:** OS</span><span class="sxs-lookup"><span data-stu-id="6d728-137">**BusinessType:** OS</span></span>  
  
-   <span data-ttu-id="6d728-138">**YearOpened:** 1974</span><span class="sxs-lookup"><span data-stu-id="6d728-138">**YearOpened:** 1974</span></span>  
  
-   <span data-ttu-id="6d728-139">**Specialty:** 도로</span><span class="sxs-lookup"><span data-stu-id="6d728-139">**Specialty:** Road</span></span>  
  
-   <span data-ttu-id="6d728-140">**SquareFeet:** 38000</span><span class="sxs-lookup"><span data-stu-id="6d728-140">**SquareFeet:** 38000</span></span>  
  
-   <span data-ttu-id="6d728-141">**Brands:** 3</span><span class="sxs-lookup"><span data-stu-id="6d728-141">**Brands:** 3</span></span>  
  
-   <span data-ttu-id="6d728-142">**인터넷:** DSL</span><span class="sxs-lookup"><span data-stu-id="6d728-142">**Internet:** DSL</span></span>  
  
-   <span data-ttu-id="6d728-143">**NumberEmployees:** 40</span><span class="sxs-lookup"><span data-stu-id="6d728-143">**NumberEmployees:** 40</span></span>  
  
 <span data-ttu-id="6d728-144">그런 다음 VBScript 메시지 상자에 FOR XML 쿼리 결과에 의해 반환된 다음과 같은 원래의 필터링되지 않은 XML 데이터 아일랜드 콘텐츠가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="6d728-144">The VBScript message box will then show the following original, unfiltered XML data island contents that were returned by the FOR XML query results.</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Sales.Store>  
    <Demographics>  
      <StoreSurvey xmlns="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/StoreSurvey">  
        <AnnualSales>1500000</AnnualSales>  
        <AnnualRevenue>150000</AnnualRevenue>  
        <BankName>Primary International</BankName>  
        <BusinessType>OS</BusinessType>  
        <YearOpened>1974</YearOpened>  
        <Specialty>Road</Specialty>  
        <SquareFeet>38000</SquareFeet>  
        <Brands>3</Brands>  
        <Internet>DSL</Internet>  
        <NumberEmployees>40</NumberEmployees>  
      </StoreSurvey>  
    </Demographics>  
  </Sales.Store>  
</ROOT>  
```  
  
## <a name="retrieving-for-xml-data-with-aspnet-and-the-net-framework"></a><span data-ttu-id="6d728-145">ASP.NET 및 .NET Framework에서 FOR XML 데이터 검색</span><span class="sxs-lookup"><span data-stu-id="6d728-145">Retrieving FOR XML Data with ASP.NET and the .NET Framework</span></span>  
 <span data-ttu-id="6d728-146">이전 예에서와 같이 다음 ASP.NET 코드에서는 AdventureWorks 예제 데이터베이스의 Sales.Store 테이블에서 `xml` 데이터 형식의 열인 Demographics를 쿼리한 결과를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="6d728-146">As in the previous example, the following ASP.NET code shows the results of querying an `xml` data type column, Demographics, in the Sales.Store table of the AdventureWorks sample database.</span></span> <span data-ttu-id="6d728-147">이전 예에서와 같이 이 쿼리는 이 열의 항목 값에서 CustomerID가 3인 행을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="6d728-147">As in the previous example, the query looks for the instance value of this column for the row where the CustomerID is equal to 3.</span></span>  
  
 <span data-ttu-id="6d728-148">이 예에서는 다음 Microsoft .NET Framework 관리 API를 사용하여 FOR XML 쿼리 결과를 반환 및 렌더링합니다.</span><span class="sxs-lookup"><span data-stu-id="6d728-148">In this example, the following Microsoft .NET Framework managed APIs are used to accomplish the return and rendering of the FOR XML query results:</span></span>  
  
1.  <span data-ttu-id="6d728-149">`SqlConnection`을 사용하여 지정된 연결 문자열 변수인 strConn의 내용에 따라 SQL Server에 대한 연결을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="6d728-149">`SqlConnection` is used to open a connection to SQL Server, based on the contents of a specified connection string variable, strConn.</span></span>  
  
2.  <span data-ttu-id="6d728-150">그런 다음 `SqlDataAdapter`를 데이터 어댑터로 사용하고 SQL 연결 및 지정된 SQL 쿼리 문자열을 사용하여 FOR XML 쿼리를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="6d728-150">`SqlDataAdapter` is then used as the data adapter and it uses the SQL connection and a specified SQL query string to execute the FOR XML query.</span></span>  
  
3.  <span data-ttu-id="6d728-151">쿼리가 실행된 다음 `SqlDataAdapter.Fill` 메서드를 호출하고 데이터 집합인 `DataSet,` MyDataSet의 해당 항목을 전달하여 데이터 집합에 FOR XML 쿼리 출력을 채웁니다.</span><span class="sxs-lookup"><span data-stu-id="6d728-151">After the query has executed, the `SqlDataAdapter.Fill` method is then called and passed an instance of a `DataSet,` MyDataSet, in order to fill the data set with the output of the FOR XML query.</span></span>  
  
4.  <span data-ttu-id="6d728-152">그런 다음 `DataSet.GetXml` 메서드를 호출하여 서버에서 생성된 HTML 페이지에 표시될 수 있는 문자열로 쿼리 결과를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="6d728-152">The `DataSet.GetXml` method is then called to return the query results as a string that can be displayed in the server-generated HTML page.</span></span>  
  
    ```  
    <%@ Page Language="VB" %>  
    <HTML>  
    <HEAD>  
    <TITLE>FOR XML Query Example</TITLE>  
    <STYLE>  
       BODY  
       {  
          FONT-FAMILY: Tahoma;  
          FONT-SIZE: 8pt;  
          OVERFLOW: auto  
       }  
       H3  
       {  
          FONT-FAMILY: Tahoma;  
          FONT-SIZE: 8pt;  
          OVERFLOW: auto  
       }  
    </STYLE>  
    </HEAD>  
    <BODY>  
    <%  
    Dim s as String  
    s = "<H3>Server-side processing</H3>" & _  
        "Page Generated @ " & Now() & "<BR/>"  
  
    Dim SQL As String   
    SQL = "SELECT Demographics from Sales.Store WHERE CustomerID = 3 FOR XML AUTO"  
  
    Dim strConn As String   
    strConn = "Server=(local);Database=AdventureWorks;Integrated Security=SSPI;"  
  
    Dim MySqlConn As New System.Data.SqlClient.SqlConnection(strConn)  
    Dim MySqlAdapter As New System.Data.SqlClient.SqlDataAdapter(SQL,MySqlConn)  
    Dim MyDataSet As New System.Data.DataSet  
  
    MySqlConn.Open()  
    s = s & "<P>SqlConnection opened.</P>"   
  
    MySqlAdapter.Fill(MyDataSet)  
    s = s & "<P>" & MyDataSet.GetXml  & "</P>"  
  
    MySqlConn.Close()  
    s = s & "<P>SqlConnection closed.</P>"   
  
    Message.InnerHtml=s  
    %>  
    <SPAN id="Message" runat=server />  
    </BODY>  
    </HTML>  
    ```  
  
#### <a name="to-test-this-example"></a><span data-ttu-id="6d728-153">이 예를 테스트하려면</span><span class="sxs-lookup"><span data-stu-id="6d728-153">To test this example</span></span>  
  
1.  <span data-ttu-id="6d728-154">IIS가 설치되어 있으며 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에 대한 AdventureWorks 예제 데이터베이스가 설치되었는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="6d728-154">Verify that IIS is installed and that the AdventureWorks sample database for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] has been installed.</span></span>  
  
     <span data-ttu-id="6d728-155">이 예에서는 ASP.NET 지원이 설정된 인터넷 정보 서비스(IIS) 버전 5.0 이상이 설치되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6d728-155">This example requires that Internet Information Services (IIS) version 5.0, or later versions, are installed with ASP.NET support enabled.</span></span> <span data-ttu-id="6d728-156">또한 AdventureWorks 예제 데이터베이스가 설치되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6d728-156">Also, the AdventureWorks sample database has to be installed.</span></span>  
  
2.  <span data-ttu-id="6d728-157">이전에 제공된 코드를 복사하여 사용하는 XML 또는 텍스트 편집기에 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="6d728-157">Copy the code that was previously provided and paste it into the XML or text editor that you use.</span></span> <span data-ttu-id="6d728-158">IIS에 사용되는 루트 디렉터리에 파일을 RetrieveResults.aspx로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="6d728-158">Save the file as RetrieveResults.aspx in the root directory used for IIS.</span></span> <span data-ttu-id="6d728-159">일반적으로 루트 디렉터리의 위치는 C:\Inetpub\wwwroot입니다.</span><span class="sxs-lookup"><span data-stu-id="6d728-159">Typically, this is C:Inetpub\wwwroot.</span></span>  
  
3.  <span data-ttu-id="6d728-160">다음 URL을 사용하여 브라우저 창에서 ASP.NET 페이지를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="6d728-160">Open the ASP.NET page in a browser window using the following URL.</span></span> <span data-ttu-id="6d728-161">먼저 'MyServer'를 "localhost" 또는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 와 IIS가 설치된 서버의 실제 이름으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="6d728-161">First, replace 'MyServer' with either "localhost" or the actual name of the server where [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and IIS are installed.</span></span>  
  
    ```  
    http://MyServer/RetrieveResults.aspx  
    ```  
  
 <span data-ttu-id="6d728-162">생성된 HTML 페이지 결과는 다음 예제 출력과 유사하게 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="6d728-162">The generated HTML page results that appear will be similar to the following sample output:</span></span>  
  
##### <a name="server-side-processing"></a><span data-ttu-id="6d728-163">서버 쪽 처리</span><span class="sxs-lookup"><span data-stu-id="6d728-163">Server-side processing</span></span>  
  
```  
Page Generated @ 3/11/2006 3:36:02 PM  
  
SqlConnection opened.  
  
<Sales.Store><Demographics><StoreSurvey xmlns="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/StoreSurvey"><AnnualSales>1500000</AnnualSales><AnnualRevenue>150000</AnnualRevenue><BankName>Primary International</BankName><BusinessType>OS</BusinessType><YearOpened>1974</YearOpened><Specialty>Road</Specialty><SquareFeet>38000</SquareFeet><Brands>3</Brands><Internet>DSL</Internet><NumberEmployees>40</NumberEmployees></StoreSurvey></Demographics></Sales.Store>  
  
SqlConnection closed.  
```  
  
> [!NOTE]  
>  <span data-ttu-id="6d728-164">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `xml` 데이터 형식 지원을 통해 `xml` [type 지시어](type-directive-in-for-xml-queries.md)를 지정 하 여 FOR XML 쿼리의 결과가 문자열이 나 이미지 형식의 데이터 대신 데이터 형식으로 반환 되도록 요청할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6d728-164">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]`xml` data type support lets you request that the result of a FOR XML query be returned as `xml` data type, instead of as string or image typed data, by specifying the [TYPE directive](type-directive-in-for-xml-queries.md).</span></span> <span data-ttu-id="6d728-165">FOR XML 쿼리에서 TYPE 지시어가 사용된 경우 이 지시어는 [애플리케이션에서 XML 데이터 사용](use-xml-data-in-applications.md)에 표시된 것과 비슷하게 FOR XML 결과에 대한 프로그래밍 방식의 액세스를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="6d728-165">When the TYPE directive is used in FOR XML queries, it provides programmatic access to the FOR XML results similar to that shown in [Use XML Data in Applications](use-xml-data-in-applications.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d728-166">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6d728-166">See Also</span></span>  
 [<span data-ttu-id="6d728-167">FOR XML&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="6d728-167">FOR XML &#40;SQL Server&#41;</span></span>](for-xml-sql-server.md)  
  
  
