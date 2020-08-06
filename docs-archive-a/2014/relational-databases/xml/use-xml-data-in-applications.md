---
title: 애플리케이션에서 XML 데이터 사용 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- parameters [XML in SQL Server]
- XML [SQL Server], ADO
- columns [XML in SQL Server], ADO.NET
- ADO [XML in SQL Server]
- columns [XML in SQL Server], SQL Server Native Client
- xml data type [SQL Server], ADO
- SQLNCLI, XML
- xml data type [SQL Server], SQL Server Native Client
- SQL Server Native Client, XML
- ADO.NET [XML in SQL Server]
- XML [SQL Server], ADO.NET
- columns [XML in SQL Server], ADO
- xml data type [SQL Server], ADO.NET
- XML [SQL Server], SQL Server Native Client
ms.assetid: 5dabf7e0-c6df-451d-a070-4661f84607fd
author: rothja
ms.author: jroth
ms.openlocfilehash: 79dd4f4d2ff3cd61bc33c632f499bfb8e8817f0f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728088"
---
# <a name="use-xml-data-in-applications"></a><span data-ttu-id="3cc25-102">애플리케이션에서 XML 데이터 사용</span><span class="sxs-lookup"><span data-stu-id="3cc25-102">Use XML Data in Applications</span></span>
  <span data-ttu-id="3cc25-103">이 항목에서는 애플리케이션에서 `xml` 데이터 형식을 사용하기 위해 제공되는 옵션에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="3cc25-103">This topic describes the options that are available to you for working with the `xml` data type in your application.</span></span> <span data-ttu-id="3cc25-104">이 항목에는 다음에 대한 정보가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="3cc25-104">The topic includes information about the following:</span></span>  
  
-   <span data-ttu-id="3cc25-105">ADO 및 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client를 사용하여 `xml` 유형의 열에서 XML 처리</span><span class="sxs-lookup"><span data-stu-id="3cc25-105">Handling XML from an `xml` type column by using ADO and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client</span></span>  
  
-   <span data-ttu-id="3cc25-106">ADO.NET을 사용하여 `xml` 유형의 열에서 XML 처리</span><span class="sxs-lookup"><span data-stu-id="3cc25-106">Handling XML from an `xml` type column by using ADO.NET</span></span>  
  
-   <span data-ttu-id="3cc25-107">ADO.NET을 사용하여 매개 변수에서 `xml` 유형 처리</span><span class="sxs-lookup"><span data-stu-id="3cc25-107">Handling `xml` type in parameters by using ADO.NET</span></span>  
  
## <a name="handling-xml-from-an-xml-type-column-by-using-ado-and-sql-server-native-client"></a><span data-ttu-id="3cc25-108">ADO 및 SQL Server Native Client를 사용하여 xml 유형의 열에서 XML 처리</span><span class="sxs-lookup"><span data-stu-id="3cc25-108">Handling XML from an xml Type Column by Using ADO and SQL Server Native Client</span></span>  
 <span data-ttu-id="3cc25-109">[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]에서 제공된 유형 및 기능에 액세스하여 MDAC 구성 요소를 사용하려면 ADO 연결 문자열에 DataTypeCompatibility 초기화 속성을 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3cc25-109">To use MDAC components to access the types and features that were introduced in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], you must set the DataTypeCompatibility initialization property in the ADO connection string.</span></span>  
  
 <span data-ttu-id="3cc25-110">예를 들어 다음 Visual Basic Scripting Edition(VBScript) 예제는 `Demographics` 예제 데이터베이스의 `Sales.Store` 테이블에서 `AdventureWorks2012`라는 `xml` 데이터 형식 열을 쿼리한 결과를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="3cc25-110">For example, the following Visual Basic Scripting Edition (VBScript) sample shows the results of querying an `xml` data type column, `Demographics`, in the `Sales.Store` table of the `AdventureWorks2012` sample database.</span></span> <span data-ttu-id="3cc25-111">특히 이 쿼리는 이 열의 항목 값에서 `CustomerID` 가 `3`인 행을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="3cc25-111">Specifically, the query looks for the instance value of this column for the row where the `CustomerID` is equal to `3`.</span></span>  
  
```  
Const DS = "MyServer"  
Const DB = "AdventureWorks2012"  
  
Set objConn = CreateObject("ADODB.Connection")  
Set objRs = CreateObject("ADODB.Recordset")  
  
CommandText = "SELECT Demographics" & _  
              " FROM Sales.Store" & _  
              " INNER JOIN Sales.Customer" & _  
              " ON Sales.Store.BusinessEntityID = sales.customer.StoreID" & _  
              " WHERE Sales.Customer.CustomerID = 3" & _  
              " OR Sales.Customer.CustomerID = 4"  
  
ConnectionString = "Provider=SQLNCLI11" & _  
                   ";Data Source=" & DS & _  
                   ";Initial Catalog=" & DB & _  
                   ";Integrated Security=SSPI;" & _  
                   "DataTypeCompatibility=80"  
  
'Connect to the data source.  
objConn.Open ConnectionString  
  
'Execute command through the connection and display  
Set objRs = objConn.Execute(CommandText)  
  
Dim rowcount  
rowcount = 0  
Do While Not objRs.EOF  
   rowcount = rowcount + 1  
   MsgBox "Row " & rowcount & _  
           vbCrLf & vbCrLf & objRs(0)  
   objRs.MoveNext  
Loop  
  
'Clean up.  
objRs.Close  
objConn.Close  
Set objRs = Nothing  
Set objConn = Nothing  
```  
  
 <span data-ttu-id="3cc25-112">이 예에서는 데이터 형식 호환성 속성을 설정하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="3cc25-112">This example shows how to set the data type compatibility property.</span></span> <span data-ttu-id="3cc25-113">기본적으로 이 속성은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client를 사용할 경우 0으로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="3cc25-113">By default, this is set to 0 when you are using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client.</span></span> <span data-ttu-id="3cc25-114">이 값을 80으로 설정하면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 공급자가 `xml` 및 사용자 정의 형식 열을 [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] 데이터 형식으로 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="3cc25-114">If you set the value to 80, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client provider will make `xml` and user-defined type columns appear as [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] data types.</span></span> <span data-ttu-id="3cc25-115">이러한 유형은 각각 DBTYPE_WSTR 및 DBTYPE_BYTES입니다.</span><span class="sxs-lookup"><span data-stu-id="3cc25-115">This would be DBTYPE_WSTR and DBTYPE_BYTES, respectively.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="3cc25-116">Native Client는 클라이언트 컴퓨터에도 설치되어 있어야 하며 연결 문자열에는 "`Provider=SQLNCLI11;...`"에서 데이터 공급자로 사용할 수 있도록 이 클라이언트가 지정되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3cc25-116">Native Client must also be installed on the client computer and the connection string must specify it for use as the data provider with "`Provider=SQLNCLI11;...`".</span></span>  
  
#### <a name="to-test-this-example"></a><span data-ttu-id="3cc25-117">이 예를 테스트하려면</span><span class="sxs-lookup"><span data-stu-id="3cc25-117">To test this example</span></span>  
  
1.  <span data-ttu-id="3cc25-118">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client가 설치되어 있고 MDAC 2.6.0 이상 버전을 클라이언트 컴퓨터에서 사용할 수 있는지 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="3cc25-118">Verify that the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client is installed and that MDAC 2.6.0or later is available on the client computer.</span></span>  
  
     <span data-ttu-id="3cc25-119">자세한 내용은 [SQL Server Native Client 프로그래밍](../native-client/sql-server-native-client-programming.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3cc25-119">For more information, see [SQL Server Native Client Programming](../native-client/sql-server-native-client-programming.md).</span></span>  
  
2.  <span data-ttu-id="3cc25-120">[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 예제 데이터베이스가 설치되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="3cc25-120">Verify that the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] sample database in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is installed.</span></span>  
  
     <span data-ttu-id="3cc25-121">이 예에는 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 예제 데이터베이스가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="3cc25-121">This example requires the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] sample database.</span></span>  
  
3.  <span data-ttu-id="3cc25-122">이 항목의 앞에 표시된 코드를 복사하여 텍스트 또는 코드 편집기에 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="3cc25-122">Copy the code shown previously in this topic and paste the code into your text or code editor.</span></span> <span data-ttu-id="3cc25-123">파일을 HandlingXmlDataType.vbs로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="3cc25-123">Save the file as HandlingXmlDataType.vbs.</span></span>  
  
4.  <span data-ttu-id="3cc25-124">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 설치에 필요한 대로 스크립트를 수정하고 변경 내용을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="3cc25-124">Modify the script as required for your [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installation and save your changes.</span></span>  
  
     <span data-ttu-id="3cc25-125">예를 들어 `MyServer` 가 지정된 경우 이를 `(local)` 이나 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 가 설치된 서버의 실제 이름으로 바꿔야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3cc25-125">For example, where `MyServer` is specified, you should replace it with either `(local)` or the actual name of the server on which [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is installed.</span></span>  
  
5.  <span data-ttu-id="3cc25-126">HandlingXmlDataType.vbs를 실행하고 스크립트를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="3cc25-126">Run HandlingXmlDataType.vbs and execute the script.</span></span>  
  
 <span data-ttu-id="3cc25-127">결과는 다음 예제 결과와 비슷해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3cc25-127">The results should be similar to the following sample output:</span></span>  
  
```  
Row 1  
  
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
  
Row 2  
  
<StoreSurvey xmlns="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/StoreSurvey">  
  <AnnualSales>300000</AnnualSales>  
  <AnnualRevenue>30000</AnnualRevenue>  
  <BankName>United Security</BankName>  
  <BusinessType>BM</BusinessType>  
  <YearOpened>1976</YearOpened>  
  <Specialty>Road</Specialty>  
  <SquareFeet>6000</SquareFeet>  
  <Brands>2</Brands>  
  <Internet>DSL</Internet>  
  <NumberEmployees>5</NumberEmployees>  
</StoreSurvey>  
```  
  
## <a name="handling-xml-from-an-xml-type-column-by-using-adonet"></a><span data-ttu-id="3cc25-128">ADO.NET을 사용하여 xml 유형의 열에서 XML 처리</span><span class="sxs-lookup"><span data-stu-id="3cc25-128">Handling XML from an xml Type Column by Using ADO.NET</span></span>  
 <span data-ttu-id="3cc25-129">`xml`ADO.NET 및를 사용 하 여 데이터 형식 열에서 XML을 처리 하려면 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 클래스의 표준 동작을 사용할 수 있습니다 `SqlCommand` .</span><span class="sxs-lookup"><span data-stu-id="3cc25-129">To handle XML from an `xml` data type column by using ADO.NET and the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] you can use the standard behavior of the `SqlCommand` class.</span></span> <span data-ttu-id="3cc25-130">예를 들어 `xml` 데이터 형식 열과 해당 값은 `SqlDataReader`를 사용하여 SQL 열을 검색하는 것과 같은 방식으로 검색할 수 있습니다. 하지만 `xml` 데이터 형식 열의 콘텐츠를 XML로 사용하려는 경우 이 콘텐츠를 먼저 `XmlReader` 유형에 할당해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3cc25-130">For example, an `xml` data type column and its values can be retrieved in the same way any SQL column is retrieved by using a `SqlDataReader`.However, if you want to work with the contents of an `xml` data type column as XML, you will first have to assign the contents to an `XmlReader` type.</span></span>  
  
 <span data-ttu-id="3cc25-131">자세한 내용과 예제 코드는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnlong](../../includes/dnprdnlong-md.md)] SDK 문서에서 “XML Column Values in a Data Reader”(데이터 판독기의 XML 열 값)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3cc25-131">For more information and example code, see "XML Column Values in a Data Reader" in the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnlong](../../includes/dnprdnlong-md.md)] SDK documentation.</span></span>  
  
## <a name="handling-an-xml-type-column-in-parameters-by-using-adonet"></a><span data-ttu-id="3cc25-132">ADO.NET을 사용하여 매개 변수의 xml 유형 열 처리</span><span class="sxs-lookup"><span data-stu-id="3cc25-132">Handling an xml Type Column in Parameters by Using ADO.NET</span></span>  
 <span data-ttu-id="3cc25-133">ADO.NET 및 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]의 매개 변수로 전달된 xml 데이터 형식을 처리하려면 `SqlXml` 데이터 형식의 인스턴스로 값을 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3cc25-133">To handle an xml data type passed as a parameter in ADO.NET and the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)], you can supply the value as an instance of the `SqlXml` data type.</span></span> <span data-ttu-id="3cc25-134">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 `xml` 데이터 형식 열은 `string` 또는 `integer`와 같이 다른 열 및 데이터 형식과 동일한 방식으로 매개 변수 값을 수락할 수 있기 때문에 특수한 조치가 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3cc25-134">No special handling is involved, because `xml` data type columns in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] can accept parameter values in the same way as other columns and data types, such as `string` or `integer`.</span></span>  
  
 <span data-ttu-id="3cc25-135">자세한 내용과 예제 코드는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnlong](../../includes/dnprdnlong-md.md)] SDK 문서에서 “XML Values as Command Parameters”(명령 매개 변수인 XML 값)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3cc25-135">For more information and example code, see "XML Values as Command Parameters" in the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnlong](../../includes/dnprdnlong-md.md)] SDK documentation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3cc25-136">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3cc25-136">See Also</span></span>  
 [<span data-ttu-id="3cc25-137">XML 데이터&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="3cc25-137">XML Data &#40;SQL Server&#41;</span></span>](xml-data-sql-server.md)  
  
  
