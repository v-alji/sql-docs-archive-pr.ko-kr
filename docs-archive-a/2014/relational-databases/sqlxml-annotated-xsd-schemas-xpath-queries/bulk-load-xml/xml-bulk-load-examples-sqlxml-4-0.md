---
title: XML 대량 로드 예제 (SQLXML 4.0) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- overflow-field annotation
- ConnectionCommand property
- XMLFragment property
- relationship chains [SQLXML]
- multiple table bulk loading
- examples [SQLXML], XML Bulk Load
- overflow data [SQLXML]
- sql:datatype
- transaction mode [SQLXML]
- CheckConstraints property
- sql:overflow-field
- XML Bulk Load [SQLXML], examples
- TempFilePath property
- datatype annotation
- Transaction property
- KeepIdentity property
- Execute method
- streaming XML data
- xml data type [SQL Server], SQLXML
- bulk load [SQLXML], examples
ms.assetid: 970e4553-b41d-4a12-ad50-0ee65d1f305d
author: rothja
ms.author: jroth
ms.openlocfilehash: c7eaec77ef068efd28c4da65833afa5047b222f9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728128"
---
# <a name="xml-bulk-load-examples-sqlxml-40"></a><span data-ttu-id="31c3f-102">XML 대량 로드 예(SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="31c3f-102">XML Bulk Load Examples (SQLXML 4.0)</span></span>
  <span data-ttu-id="31c3f-103">다음 예에서는 Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]의 XML 대량 로드 기능을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-103">The following examples illustrate the XML Bulk Load functionality in Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="31c3f-104">각 예는 XSD 스키마와 이에 해당하는 XDR 스키마를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-104">Each example provides an XSD schema and its equivalent XDR schema.</span></span>  
  
## <a name="bulk-loader-script-validateandbulkloadvbs"></a><span data-ttu-id="31c3f-105">대량 로더 스크립트(ValidateAndBulkload.vbs)</span><span class="sxs-lookup"><span data-stu-id="31c3f-105">Bulk Loader Script (ValidateAndBulkload.vbs)</span></span>  
 <span data-ttu-id="31c3f-106">VBScript (Visual Basic Scripting Edition)로 작성 된 다음 스크립트는 xml [!INCLUDE[msCoName](../../../includes/msconame-md.md)] 문서를 XML DOM에 로드 하 고, 스키마에 대해 유효성을 검사 하 고, 문서가 유효한 경우 xml 대량 로드를 실행 하 여 xml을 테이블로 로드 합니다. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="31c3f-106">The following script, written in the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic Scripting Edition (VBScript), loads an XML document into the XML DOM; validates it against a schema; and, if the document is valid, executes an XML bulk load to load the XML into a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] table.</span></span> <span data-ttu-id="31c3f-107">이 스크립트는 이 항목의 뒷부분에서 이 스크립트를 참조하는 각 개별 예와 함께 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-107">This script can be used with each of the individual examples that refer to it later in this topic.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="31c3f-108">데이터 파일에서 업로드되는 내용이 없을 경우 XML 대량 로드는 경고 또는 오류를 표시하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-108">XML Bulk Load does not throw a warning or an error if no content is uploaded from the data file.</span></span> <span data-ttu-id="31c3f-109">따라서 대량 로드 작업을 실행하기 전에 XML 데이터 파일의 유효성을 검사하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-109">Therefore, it is a good practice to validate your XML data file prior to executing a bulk load operation.</span></span>  
  
```  
Dim FileValid  
  
set objBL = CreateObject("SQLXMLBulkLoad.SQLXMLBulkload.4.0")  
objBL.ConnectionString = "provider=SQLOLEDB;data source=MyServer;database=tempdb;integrated security=SSPI"  
objBL.ErrorLogFile = "c:\error.log"  
  
'Validate the data file prior to bulkload  
Dim sOutput   
sOutput = ValidateFile("SampleXMLData.xml", "", "SampleSchema.xml")  
WScript.Echo sOutput  
  
If FileValid Then  
   ' Check constraints and initiate transaction (if needed)  
   ' objBL.CheckConstraints = True  
   ' objBL.Transaction=True  
  'Execute XML bulkload using file.  
  objBL.Execute "SampleSchema.xml", "SampleXMLData.xml"  
  set objBL=Nothing  
End If  
  
Function ValidateFile(strXmlFile,strUrn,strXsdFile)  
  
   ' Create a schema cache and add SampleSchema.xml to it.  
   Dim xs, fso, sAppPath  
   Set fso = CreateObject("Scripting.FileSystemObject")   
   Set xs = CreateObject("MSXML2.XMLSchemaCache.6.0")  
   sAppPath = fso.GetFolder(".")   
   xs.Add strUrn, sAppPath & "\" & strXsdFile  
  
   ' Create an XML DOMDocument object.  
   Dim xd   
   Set xd = CreateObject("MSXML2.DOMDocument.6.0")  
  
   ' Assign the schema cache to the DOM document.  
   ' schemas collection.  
   Set xd.schemas = xs  
  
   ' Load XML document as DOM document.  
   xd.async = False  
   xd.Load sAppPath & "\" & strXmlFile  
  
   ' Return validation results in message to the user.  
   If xd.parseError.errorCode <> 0 Then  
        ValidateFile = "Validation failed on " & _  
             strXmlFile & vbCrLf & _  
             "=======" & vbCrLf & _  
             "Reason: " & xd.parseError.reason & _  
             vbCrLf & "Source: " & _  
             xd.parseError.srcText & _  
             vbCrLf & "Line: " & _  
             xd.parseError.Line & vbCrLf  
             FileValid = False  
    Else  
        ValidateFile = "Validation succeeded for " & _  
             strXmlFile & vbCrLf & _  
             "========" & _  
             vbCrLf & "Contents to be bulkloaded" & vbCrLf  
             FileValid = True  
    End If  
End Function  
```  
  
## <a name="a-bulk-loading-xml-in-a-table"></a><span data-ttu-id="31c3f-110">A.</span><span class="sxs-lookup"><span data-stu-id="31c3f-110">A.</span></span> <span data-ttu-id="31c3f-111">테이블에 XML 대량 로드</span><span class="sxs-lookup"><span data-stu-id="31c3f-111">Bulk loading XML in a table</span></span>  
 <span data-ttu-id="31c3f-112">이 예에서는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ConnectionString 속성 (MyServer)에 지정 된 인스턴스에 대 한 연결을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-112">This example establishes a connection to the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] that is specified in the ConnectionString property (MyServer).</span></span> <span data-ttu-id="31c3f-113">또한이 예제에서는 ErrorLogFile 속성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-113">The example also specifies the ErrorLogFile property.</span></span> <span data-ttu-id="31c3f-114">따라서 오류 출력은 지정된 파일("C:\error.log")에 저장되며 위치는 다른 곳으로 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-114">Therefore, the error output is saved in the specified file ("C:\error.log"), which you might also decide to change to a different location.</span></span> <span data-ttu-id="31c3f-115">또한 Execute 메서드는 매핑 스키마 파일 (SampleSchema.xml)과 XML 데이터 파일 (SampleXMLData.xml)의 매개 변수를 모두 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-115">Notice also that the Execute method has as its parameters both the mapping schema file (SampleSchema.xml) and the XML data file (SampleXMLData.xml).</span></span> <span data-ttu-id="31c3f-116">대량 로드를 실행 하면 **tempdb** 데이터베이스에서 만든 Cust 테이블에 XML 데이터 파일의 내용에 따라 새 레코드가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-116">When the bulk load executes, the Cust table you have created in **tempdb** database will contain new records based upon the contents of the XML data file.</span></span>  
  
#### <a name="to-test-a-sample-bulk-load"></a><span data-ttu-id="31c3f-117">예제 대량 로드를 테스트하려면</span><span class="sxs-lookup"><span data-stu-id="31c3f-117">To test a sample bulk load</span></span>  
  
1.  <span data-ttu-id="31c3f-118">다음 테이블을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-118">Create this table:</span></span>  
  
    ```  
    CREATE TABLE Cust(CustomerID  int PRIMARY KEY,  
                      CompanyName varchar(20),  
                      City        varchar(20));  
    GO  
    ```  
  
2.  <span data-ttu-id="31c3f-119">기본 텍스트 편집기 또는 XML 편집기에서 파일을 만든 후 SampleSchema.xml로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-119">Create a file in your preferred text or XML editor, and save it as SampleSchema.xml.</span></span> <span data-ttu-id="31c3f-120">이 파일에 다음 XSD 스키마를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-120">To this file, add the following XSD schema:</span></span>  
  
    ```  
    <xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
                xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
       <xsd:element name="ROOT" sql:is-constant="1" >  
         <xsd:complexType>  
           <xsd:sequence>  
             <xsd:element name="Customers" sql:relation="Cust" maxOccurs="unbounded">  
               <xsd:complexType>  
                 <xsd:sequence>  
                   <xsd:element name="CustomerID"  type="xsd:integer" />  
                   <xsd:element name="CompanyName" type="xsd:string" />  
                   <xsd:element name="City"        type="xsd:string" />  
                 </xsd:sequence>  
               </xsd:complexType>  
             </xsd:element>  
           </xsd:sequence>  
          </xsd:complexType>  
         </xsd:element>  
    </xsd:schema>  
    ```  
  
3.  <span data-ttu-id="31c3f-121">기본 텍스트 편집기 또는 XML 편집기에서 파일을 만든 후 SampleXMLData.xml로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-121">Create a file in your preferred text or XML editor, and save it as SampleXMLData.xml.</span></span> <span data-ttu-id="31c3f-122">이 파일에 다음 XML 문서를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-122">To this file, add the following XML document:</span></span>  
  
    ```  
    <ROOT>  
      <Customers>  
        <CustomerID>1111</CustomerID>  
        <CompanyName>Sean Chai</CompanyName>  
        <City>New York</City>  
      </Customers>  
      <Customers>  
        <CustomerID>1112</CustomerID>  
        <CompanyName>Tom Johnston</CompanyName>  
         <City>Los Angeles</City>  
      </Customers>  
      <Customers>  
        <CustomerID>1113</CustomerID>  
        <CompanyName>Institute of Art</CompanyName>  
        <City>Chicago</City>  
      </Customers>  
    </ROOT>  
    ```  
  
4.  <span data-ttu-id="31c3f-123">기본 텍스트 편집기 또는 XML 편집기에서 파일을 만든 후 ValidateAndBulkload.vbs로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-123">Create a file in your preferred text or XML editor, and save it as ValidateAndBulkload.vbs.</span></span> <span data-ttu-id="31c3f-124">이 파일에 이 항목의 시작 부분에 제공된 VBScript 코드를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-124">To this file, add the VBScript code that is provided above at the beginning of this topic.</span></span> <span data-ttu-id="31c3f-125">연결 문자열을 수정하여 해당 서버 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-125">Modify the connection string to provide the appropriate server name.</span></span> <span data-ttu-id="31c3f-126">Execute 메서드에 대 한 매개 변수로 지정 된 파일에 대 한 적절 한 경로를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-126">Specify the appropriate path for the files that are specified as parameters to the Execute method.</span></span>  
  
5.  <span data-ttu-id="31c3f-127">VBScript 코드를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-127">Execute the VBScript code.</span></span> <span data-ttu-id="31c3f-128">XML 대량 로드가 Cust 테이블에 XML을 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-128">XML Bulk Load loads the XML into the Cust table.</span></span>  
  
 <span data-ttu-id="31c3f-129">다음은 동등한 XDR 스키마입니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-129">This is the equivalent XDR schema:</span></span>  
  
```  
<?xml version="1.0" ?>  
<Schema xmlns="urn:schemas-microsoft-com:xml-data"   
        xmlns:dt="urn:schemas-microsoft-com:xml:datatypes"    
        xmlns:sql="urn:schemas-microsoft-com:xml-sql" >   
  
   <ElementType name="CustomerID" dt:type="int" />  
   <ElementType name="CompanyName" dt:type="string" />  
   <ElementType name="City" dt:type="string" />  
  
   <ElementType name="ROOT" sql:is-constant="1">  
      <element type="Customers" />  
   </ElementType>  
  
   <ElementType name="Customers"  sql:relation="Cust" >  
      <element type="CustomerID"  sql:field="CustomerID" />  
      <element type="CompanyName" sql:field="CompanyName" />  
      <element type="City"        sql:field="City" />  
  
   </ElementType>  
</Schema>  
```  
  
## <a name="b-bulk-loading-xml-data-in-multiple-tables"></a><span data-ttu-id="31c3f-130">B.</span><span class="sxs-lookup"><span data-stu-id="31c3f-130">B.</span></span> <span data-ttu-id="31c3f-131">여러 테이블에 XML 데이터 대량 로드</span><span class="sxs-lookup"><span data-stu-id="31c3f-131">Bulk loading XML data in multiple tables</span></span>  
 <span data-ttu-id="31c3f-132">이 예제에서 XML 문서는 및 요소로 구성 됩니다 **\<Customer>** **\<Order>** .</span><span class="sxs-lookup"><span data-stu-id="31c3f-132">In this example, the XML document consists of the **\<Customer>** and **\<Order>** elements.</span></span>  
  
```  
<ROOT>  
  <Customers>  
    <CustomerID>1111</CustomerID>  
    <CompanyName>Sean Chai</CompanyName>  
    <City>NY</City>  
    <Order OrderID="1" />  
    <Order OrderID="2" />  
  </Customers>  
  <Customers>  
    <CustomerID>1112</CustomerID>  
    <CompanyName>Tom Johnston</CompanyName>  
     <City>LA</City>    
    <Order OrderID="3" />  
  </Customers>  
  <Customers>  
    <CustomerID>1113</CustomerID>  
    <CompanyName>Institute of Art</CompanyName>  
    <Order OrderID="4" />  
  </Customers>  
</ROOT>  
```  
  
 <span data-ttu-id="31c3f-133">이 예에서는 XML 데이터를 **Cust** 및 **CustOrder**라는 두 테이블에 대량 로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-133">This example bulk loads the XML data into two tables, **Cust** and **CustOrder**:</span></span>  
  
```  
Cust(CustomerID, CompanyName, City)  
CustOrder(OrderID, CustomerID)  
```  
  
 <span data-ttu-id="31c3f-134">다음 XSD 스키마는 이러한 테이블의 XML 뷰를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-134">The following XSD schema defines the XML view of these tables.</span></span> <span data-ttu-id="31c3f-135">스키마는 및 요소 간의 부모-자식 관계를 지정 합니다 **\<Customer>** **\<Order>** .</span><span class="sxs-lookup"><span data-stu-id="31c3f-135">The schema specifies the parent-child relationship between the **\<Customer>** and **\<Order>** elements.</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:annotation>  
    <xsd:appinfo>  
      <sql:relationship name="CustCustOrder"  
          parent="Cust"  
          parent-key="CustomerID"  
          child="CustOrder"  
          child-key="CustomerID" />  
    </xsd:appinfo>  
  </xsd:annotation>  
  <xsd:element name="ROOT" sql:is-constant="1" >  
    <xsd:complexType>  
      <xsd:sequence>  
        <xsd:element name="Customers" sql:relation="Cust" >  
          <xsd:complexType>  
            <xsd:sequence>  
              <xsd:element name="CustomerID"  type="xsd:integer" />  
              <xsd:element name="CompanyName" type="xsd:string" />  
              <xsd:element name="City"        type="xsd:string" />  
              <xsd:element name="Order"   
                          sql:relation="CustOrder"  
                          sql:relationship="CustCustOrder" >  
                <xsd:complexType>  
                  <xsd:attribute name="OrderID" type="xsd:integer" />  
                </xsd:complexType>  
              </xsd:element>  
             </xsd:sequence>  
          </xsd:complexType>  
        </xsd:element>  
      </xsd:sequence>  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
 <span data-ttu-id="31c3f-136">XML 대량 로드에서는 및 요소 사이에 지정 된 기본 키/외래 키 **\<Cust>** 관계 **\<CustOrder>** 를 사용 하 여 두 테이블에 데이터를 대량 로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-136">XML Bulk Load uses the primary key/foreign key relationship specified above between the **\<Cust>** and **\<CustOrder>** elements to bulk load the data into both tables.</span></span>  
  
#### <a name="to-test-a-sample-bulk-load"></a><span data-ttu-id="31c3f-137">예제 대량 로드를 테스트하려면</span><span class="sxs-lookup"><span data-stu-id="31c3f-137">To test a sample bulk load</span></span>  
  
1.  <span data-ttu-id="31c3f-138">**Tempdb** 데이터베이스에 두 개의 테이블을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-138">Create two tables in **tempdb** database:</span></span>  
  
    ```  
    USE tempdb;  
    CREATE TABLE Cust(  
           CustomerID  int PRIMARY KEY,  
           CompanyName varchar(20),  
           City        varchar(20));  
    CREATE TABLE CustOrder(        OrderID     int PRIMARY KEY,   
            CustomerID int FOREIGN KEY REFERENCES Cust(CustomerID));  
    ```  
  
2.  <span data-ttu-id="31c3f-139">기본 텍스트 편집기 또는 XML 편집기에서 파일을 만든 후 SampleSchema.xml로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-139">Create a file in your preferred text or XML editor, and save it as SampleSchema.xml.</span></span> <span data-ttu-id="31c3f-140">이 예에 제공되는 XSD 스키마를 이 파일에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-140">Add the XSD schema that is provided in this example to the file.</span></span>  
  
3.  <span data-ttu-id="31c3f-141">기본 텍스트 편집기 또는 XML 편집기에서 파일을 만든 후 SampleData.xml로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-141">Create a file in your preferred text or XML editor, and save it as SampleData.xml.</span></span> <span data-ttu-id="31c3f-142">이 예의 앞부분에 제공된 XML 문서를 이 파일에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-142">Add the XML document that was provided earlier in this example to the file.</span></span>  
  
4.  <span data-ttu-id="31c3f-143">기본 텍스트 편집기 또는 XML 편집기에서 파일을 만든 후 ValidateAndBulkload.vbs로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-143">Create a file in your preferred text or XML editor, and save it as ValidateAndBulkload.vbs.</span></span> <span data-ttu-id="31c3f-144">이 파일에 이 항목의 시작 부분에 제공된 VBScript 코드를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-144">To this file, add the VBScript code that is provided above at the beginning of this topic.</span></span> <span data-ttu-id="31c3f-145">연결 문자열을 수정하여 해당 서버 및 데이터베이스 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-145">Modify the connection string to provide the appropriate server and database name.</span></span> <span data-ttu-id="31c3f-146">Execute 메서드에 대 한 매개 변수로 지정 된 파일에 대 한 적절 한 경로를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-146">Specify the appropriate path for the files that are specified as parameters to the Execute method.</span></span>  
  
5.  <span data-ttu-id="31c3f-147">위의 VBScript 코드를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-147">Execute the VBScript code above.</span></span> <span data-ttu-id="31c3f-148">XML 대량 로드가 Cust 및 CustOrder 테이블에 XML 문서를 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-148">XML Bulk Load loads the XML document into the Cust and CustOrder tables.</span></span>  
  
 <span data-ttu-id="31c3f-149">다음은 동등한 XDR 스키마입니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-149">This is the equivalent XDR schema:</span></span>  
  
```  
<?xml version="1.0" ?>  
<Schema xmlns="urn:schemas-microsoft-com:xml-data"   
        xmlns:dt="urn:schemas-microsoft-com:xml:datatypes"    
        xmlns:sql="urn:schemas-microsoft-com:xml-sql" >   
   <ElementType name="CustomerID" dt:type="int" />  
   <ElementType name="CompanyName" dt:type="string" />  
   <ElementType name="City" dt:type="string" />  
  
   <ElementType name="ROOT" sql:is-constant="1">  
      <element type="Customers" />  
   </ElementType>  
  
   <ElementType name="Customers" sql:relation="Cust" >  
      <element type="CustomerID" sql:field="CustomerID" />  
      <element type="CompanyName" sql:field="CompanyName" />  
      <element type="City" sql:field="City" />  
      <element type="Order" >  
<sql:relationship  
                key-relation="Cust"  
                key="CustomerID"  
                foreign-key="CustomerID"  
                foreign-relation="CustOrder" />  
      </element>  
   </ElementType>  
    <ElementType name="Order" sql:relation="CustOrder" >  
      <AttributeType name="OrderID" />  
      <AttributeType name="CustomerID" />  
      <attribute type="OrderID" />  
      <attribute type="CustomerID" />  
    </ElementType>  
</Schema>  
```  
  
## <a name="c-using-chain-relationships-in-the-schema-to-bulk-load-xml"></a><span data-ttu-id="31c3f-150">C.</span><span class="sxs-lookup"><span data-stu-id="31c3f-150">C.</span></span> <span data-ttu-id="31c3f-151">스키마의 체인 관계를 사용하여 XML 대량 로드</span><span class="sxs-lookup"><span data-stu-id="31c3f-151">Using chain relationships in the schema to bulk load XML</span></span>  
 <span data-ttu-id="31c3f-152">이 예에서는 XML 대량 로드에서 매핑 스키마에 지정된 M:N 관계를 사용하여 M:N 관계를 나타내는 테이블에 데이터를 로드하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-152">This example illustrates how the M:N relationship that is specified in the mapping schema is used by XML Bulk Load to load data in a table that represents an M:N relationship.</span></span>  
  
 <span data-ttu-id="31c3f-153">예를 들어 다음 XSD 스키마를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="31c3f-153">For example, consider this XSD schema:</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
<xsd:annotation>  
  <xsd:appinfo>  
    <sql:relationship name="OrderOD"  
          parent="Ord"  
          parent-key="OrderID"  
          child="OrderDetail"  
          child-key="OrderID" />  
  
    <sql:relationship name="ODProduct"  
          parent="OrderDetail"  
          parent-key="ProductID"  
          child="Product"  
          child-key="ProductID"   
          inverse="true"/>  
  </xsd:appinfo>  
</xsd:annotation>  
  
  <xsd:element name="ROOT" sql:is-constant="1" >  
    <xsd:complexType>  
      <xsd:sequence>  
        <xsd:element name="Order"   
                     sql:relation="Ord"   
                     sql:key-fields="OrderID" >  
          <xsd:complexType>  
            <xsd:sequence>  
             <xsd:element name="Product"  
                          sql:relation="Product"   
                          sql:key-fields="ProductID"  
                          sql:relationship="OrderOD ODProduct">  
               <xsd:complexType>  
                 <xsd:attribute name="ProductID" type="xsd:int" />  
                 <xsd:attribute name="ProductName" type="xsd:string" />  
               </xsd:complexType>  
             </xsd:element>  
           </xsd:sequence>  
           <xsd:attribute name="OrderID"   type="xsd:integer" />   
           <xsd:attribute name="CustomerID"   type="xsd:string" />  
         </xsd:complexType>  
       </xsd:element>  
      </xsd:sequence>  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
 <span data-ttu-id="31c3f-154">스키마는 **\<Order>** 자식 요소가 있는 요소를 지정 합니다 **\<Product>** .</span><span class="sxs-lookup"><span data-stu-id="31c3f-154">The schema specifies an **\<Order>** element with a **\<Product>** child element.</span></span> <span data-ttu-id="31c3f-155">**\<Order>** 요소는 Ord 테이블에 매핑되고 요소는 **\<Product>** 데이터베이스의 Product 테이블에 매핑됩니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-155">The **\<Order>** element maps to Ord table and the **\<Product>** element maps to the Product table in the database.</span></span> <span data-ttu-id="31c3f-156">요소에 지정 된 체인 관계는 **\<Product>** OrderDetail 테이블로 표시 되는 M:N 관계를 식별 합니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-156">The chain relationship specified on the **\<Product>** element identifies a M:N relationship represented by the OrderDetail table.</span></span> <span data-ttu-id="31c3f-157">하나의 주문이 여러 제품을 포함할 수 있으며, 하나의 제품은 여러 주문에 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-157">(An order can include many products, and a product can be included in many orders.)</span></span>  
  
 <span data-ttu-id="31c3f-158">이 스키마를 사용하여 XML 문서를 대량 로드하는 경우 Ord, Product 및 OrderDetail 테이블에 레코드가 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-158">When you are bulk loading an XML document with this schema, records are added to the Ord, Product, and OrderDetail tables.</span></span>  
  
#### <a name="to-test-a-working-sample"></a><span data-ttu-id="31c3f-159">작업 예제를 테스트하려면</span><span class="sxs-lookup"><span data-stu-id="31c3f-159">To test a working sample</span></span>  
  
1.  <span data-ttu-id="31c3f-160">다음 3개의 테이블을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-160">Create three tables:</span></span>  
  
    ```  
    CREATE TABLE Ord (  
             OrderID     int  PRIMARY KEY,  
             CustomerID  varchar(5));  
    GO  
    CREATE TABLE Product (  
             ProductID   int PRIMARY KEY,  
             ProductName varchar(20));  
    GO  
    CREATE TABLE OrderDetail (  
           OrderID     int FOREIGN KEY REFERENCES Ord(OrderID),  
           ProductID   int FOREIGN KEY REFERENCES Product(ProductID),  
                       CONSTRAINT OD_key PRIMARY KEY (OrderID, ProductID));  
    GO  
    ```  
  
2.  <span data-ttu-id="31c3f-161">이 예의 윗부분에서 제공하는 스키마를 SampleSchema.xml로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-161">Save the schema that is provided above in this example as SampleSchema.xml.</span></span>  
  
3.  <span data-ttu-id="31c3f-162">다음 예제 XML 데이터를 SampleXMLData.xml로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-162">Save the following sample XML data as SampleXMLData.xml:</span></span>  
  
    ```  
    <ROOT>    
      <Order OrderID="1" CustomerID="ALFKI">  
        <Product ProductID="1" ProductName="Chai" />  
        <Product ProductID="2" ProductName="Chang" />  
      </Order>  
      <Order OrderID="2" CustomerID="ANATR">  
        <Product ProductID="3" ProductName="Aniseed Syrup" />  
        <Product ProductID="4" ProductName="Gumbo Mix" />  
      </Order>  
    </ROOT>  
    ```  
  
4.  <span data-ttu-id="31c3f-163">기본 텍스트 편집기 또는 XML 편집기에서 파일을 만든 후 ValidateAndBulkload.vbs로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-163">Create a file in your preferred text or XML editor, and save it as ValidateAndBulkload.vbs.</span></span> <span data-ttu-id="31c3f-164">이 파일에 이 항목의 시작 부분에 제공된 VBScript 코드를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-164">To this file, add the VBScript code that is provided above at the beginning of this topic.</span></span> <span data-ttu-id="31c3f-165">연결 문자열을 수정하여 해당 서버 및 데이터베이스 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-165">Modify the connection string to provide the appropriate server and database name.</span></span> <span data-ttu-id="31c3f-166">이 예의 원본 코드에서 다음 줄의 주석 처리를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-166">Uncomment the following lines from the source code for this example.</span></span>  
  
    ```  
    objBL.CheckConstraints = True  
    objBL.Transaction=True  
    ```  
  
5.  <span data-ttu-id="31c3f-167">VBScript 코드를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-167">Execute the VBScript code.</span></span> <span data-ttu-id="31c3f-168">XML 대량 로드가 Ord 및 Product 테이블에 XML 문서를 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-168">XML Bulk Load loads the XML document into the Ord and Product tables.</span></span>  
  
## <a name="d-bulk-loading-in-identity-type-columns"></a><span data-ttu-id="31c3f-169">D.</span><span class="sxs-lookup"><span data-stu-id="31c3f-169">D.</span></span> <span data-ttu-id="31c3f-170">ID 유형 열에 대량 로드</span><span class="sxs-lookup"><span data-stu-id="31c3f-170">Bulk loading in identity type columns</span></span>  
 <span data-ttu-id="31c3f-171">이 예에서는 대량 로드에서 ID 유형 열이 처리되는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-171">This example illustrates how bulk load handles identity type columns.</span></span> <span data-ttu-id="31c3f-172">이 예에서 데이터는 3개의 테이블(Ord, Product 및 OrderDetail)에 대량 로드됩니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-172">In the example, data is bulk loaded into three tables (Ord, Product, and OrderDetail).</span></span>  
  
 <span data-ttu-id="31c3f-173">이러한 테이블에는 다음이 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-173">In these tables:</span></span>  
  
-   <span data-ttu-id="31c3f-174">Ord 테이블의 OrderID는 ID 유형 열입니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-174">OrderID in the Ord table is an identity type column</span></span>  
  
-   <span data-ttu-id="31c3f-175">Product 테이블의 ProductID는 ID 유형 열입니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-175">ProductID in the Product table is an identity type column.</span></span>  
  
-   <span data-ttu-id="31c3f-176">OrderDetail의 OrderID 및 ProductID는 Ord 및 Product 테이블의 해당 기본 키 열을 참조하는 외래 키 열입니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-176">OrderID and ProductID columns in the OrderDetail are foreign key columns referring to corresponding primary key columns in the Ord and Product tables.</span></span>  
  
 <span data-ttu-id="31c3f-177">다음은 이 예에 대한 테이블 스키마입니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-177">The following are the table schemas for this example:</span></span>  
  
```  
Ord (OrderID, CustomerID)  
Product (ProductID, ProductName)  
OrderDetail (OrderID, ProductID)  
```  
  
 <span data-ttu-id="31c3f-178">이 XML 대량 로드 예제에서 BulkLoad 개체 모델의 KeepIdentity 속성은 false로 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-178">In this example of XML Bulk Load, the KeepIdentity property of the BulkLoad object model is set to false.</span></span> <span data-ttu-id="31c3f-179">따라서 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]는 각각 Product 및 Ord 테이블의 ProductID 및 OrderID 열에 대한 ID 값을 생성합니다(이 문서에서 대량 로드되도록 제공된 모든 값은 무시됨).</span><span class="sxs-lookup"><span data-stu-id="31c3f-179">Therefore, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] generates identity values for the ProductID and OrderID columns in the Product and Ord tables, respectively (any values provided in the documents to be bulk loaded are ignored).</span></span>  
  
 <span data-ttu-id="31c3f-180">여기에서 XML 대량 로드는 테이블 간의 기본 키/외래 키 관계를 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-180">In this case, XML Bulk Load identifies the primary key/foreign key relationship among tables.</span></span> <span data-ttu-id="31c3f-181">대량 로드는 먼저 기본 키가 있는 테이블에 레코드를 삽입한 후 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]에서 생성한 ID 값을 외래 키 열이 있는 테이블로 전파합니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-181">Bulk Load first inserts records in the tables with the primary key, then propagates the identity value generated by [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] to the tables with foreign key columns.</span></span> <span data-ttu-id="31c3f-182">다음 예의 XML 대량 로드는 다음 순서에 따라 데이터를 테이블에 삽입합니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-182">In the following example, XML Bulk Load inserts data in tables in this order:</span></span>  
  
1.  <span data-ttu-id="31c3f-183">제품</span><span class="sxs-lookup"><span data-stu-id="31c3f-183">Product</span></span>  
  
2.  <span data-ttu-id="31c3f-184">Ord</span><span class="sxs-lookup"><span data-stu-id="31c3f-184">Ord</span></span>  
  
3.  <span data-ttu-id="31c3f-185">OrderDetail</span><span class="sxs-lookup"><span data-stu-id="31c3f-185">OrderDetail</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="31c3f-186">Products 및 Orders 테이블에 생성된 ID 값을 전파하기 위해 처리 논리는 XML 대량 로드에서 나중에 OrderDetails 테이블에 삽입할 수 있도록 이러한 값을 추적할 것을 요구합니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-186">In order to propagate identity values generated in the Products and Orders tables, the processing logic requires XML Bulk Load to keep track of these values for later insertion into the OrderDetails table.</span></span> <span data-ttu-id="31c3f-187">이를 수행하기 위해 XML 대량 로드는 중간 테이블을 만들고 이 테이블에 데이터를 채운 후 나중에 테이블을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-187">To do that, XML Bulk Load creates intermediate tables, populates the data in these tables, and later removes them.</span></span>  
  
#### <a name="to-test-a-working-sample"></a><span data-ttu-id="31c3f-188">작업 예제를 테스트하려면</span><span class="sxs-lookup"><span data-stu-id="31c3f-188">To test a working sample</span></span>  
  
1.  <span data-ttu-id="31c3f-189">다음 테이블을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-189">Create these tables:</span></span>  
  
    ```  
    CREATE TABLE Ord (  
             OrderID     int identity(1,1)  PRIMARY KEY,  
             CustomerID  varchar(5));  
    GO  
    CREATE TABLE Product (  
             ProductID   int identity(1,1) PRIMARY KEY,  
             ProductName varchar(20));  
    GO  
    CREATE TABLE OrderDetail (  
           OrderID     int FOREIGN KEY REFERENCES Ord(OrderID),  
           ProductID   int FOREIGN KEY REFERENCES Product(ProductID),  
                       CONSTRAINT OD_key PRIMARY KEY (OrderID, ProductID));  
    GO  
    ```  
  
2.  <span data-ttu-id="31c3f-190">기본 텍스트 편집기 또는 XML 편집기에서 파일을 만든 후 SampleSchema.xml로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-190">Create a file in your preferred text or XML editor, and save it as SampleSchema.xml.</span></span> <span data-ttu-id="31c3f-191">이 파일에 이 XSD 스키마를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-191">Add this XSD schema to this file.</span></span>  
  
    ```  
    <xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
                xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
     <xsd:annotation>  
       <xsd:appinfo>  
        <sql:relationship name="OrderOD"  
              parent="Ord"  
              parent-key="OrderID"  
              child="OrderDetail"  
              child-key="OrderID" />  
        <sql:relationship name="ODProduct"  
              parent="OrderDetail"  
              parent-key="ProductID"  
              child="Product"  
              child-key="ProductID"   
              inverse="true"/>  
       </xsd:appinfo>  
     </xsd:annotation>  
  
      <xsd:element name="Order" sql:relation="Ord"   
                                sql:key-fields="OrderID" >  
       <xsd:complexType>  
         <xsd:sequence>  
            <xsd:element name="Product" sql:relation="Product"   
                         sql:key-fields="ProductID"  
                         sql:relationship="OrderOD ODProduct">  
              <xsd:complexType>  
                 <xsd:attribute name="ProductID" type="xsd:int" />  
                 <xsd:attribute name="ProductName" type="xsd:string" />  
              </xsd:complexType>  
            </xsd:element>  
         </xsd:sequence>  
            <xsd:attribute name="OrderID"   type="xsd:integer" />   
            <xsd:attribute name="CustomerID"   type="xsd:string" />  
        </xsd:complexType>  
      </xsd:element>  
    </xsd:schema>  
    ```  
  
3.  <span data-ttu-id="31c3f-192">기본 텍스트 편집기 또는 XML 편집기에서 파일을 만든 후 SampleXMLData.xml로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-192">Create a file in your preferred text or XML editor, and save it as SampleXMLData.xml.</span></span> <span data-ttu-id="31c3f-193">다음 XML 문서를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-193">Add the following XML document.</span></span>  
  
    ```  
    <ROOT>    
      <Order OrderID="11" CustomerID="ALFKI">  
        <Product ProductID="11" ProductName="Chai" />  
        <Product ProductID="22" ProductName="Chang" />  
      </Order>  
      <Order OrderID="22" CustomerID="ANATR">  
         <Product ProductID="33" ProductName="Aniseed Syrup" />  
        <Product ProductID="44" ProductName="Gumbo Mix" />  
      </Order>  
    </ROOT>  
    ```  
  
4.  <span data-ttu-id="31c3f-194">기본 텍스트 편집기 또는 XML 편집기에서 파일을 만든 후 ValidateAndBulkload.vbs로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-194">Create a file in your preferred text or XML editor, and save it as ValidateAndBulkload.vbs.</span></span> <span data-ttu-id="31c3f-195">이 파일에 다음 VBScript 코드를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-195">To this file, add the following VBScript code.</span></span> <span data-ttu-id="31c3f-196">연결 문자열을 수정하여 해당 서버 및 데이터베이스 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-196">Modify the connection string to provide the appropriate server and database name.</span></span> <span data-ttu-id="31c3f-197">메서드에 대 한 매개 변수로 사용할 파일의 적절 한 경로를 지정 합니다 `Execute` .</span><span class="sxs-lookup"><span data-stu-id="31c3f-197">Specify the appropriate path for the files that serve as parameters to the `Execute` method.</span></span>  
  
    ```  
    Set objBL = CreateObject("SQLXMLBulkLoad.SQLXMLBulkload.4.0")  
    objBL.ConnectionString = "provider=SQLOLEDB;data source=localhost;database=tempdb;integrated security=SSPI"  
    objBL.ErrorLogFile = "C:\error.log"  
    objBL.CheckConstraints = True  
    objBL.Transaction = False  
    objBL.KeepIdentity = False  
    objBL.Execute "SampleSchema.xml", "SampleXMLData.xml"  
    Set objBL = Nothing  
    MsgBox "Done."  
    ```  
  
5.  <span data-ttu-id="31c3f-198">VBScript 코드를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-198">Execute the VBScript code.</span></span> <span data-ttu-id="31c3f-199">XML 대량 로드에서 해당 테이블에 데이터를 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-199">The XML Bulk Load will load the data into the appropriate tables.</span></span>  
  
## <a name="e-generating-table-schemas-before-bulk-loading"></a><span data-ttu-id="31c3f-200">E.</span><span class="sxs-lookup"><span data-stu-id="31c3f-200">E.</span></span> <span data-ttu-id="31c3f-201">대량 로드 전에 테이블 스키마 생성</span><span class="sxs-lookup"><span data-stu-id="31c3f-201">Generating table schemas before bulk loading</span></span>  
 <span data-ttu-id="31c3f-202">XML 대량 로드는 대량 로드 전에 테이블이 존재하지 않는 경우 필요에 따라 이러한 테이블을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-202">XML Bulk Load can optionally generate the tables if they do not exist before bulk loading.</span></span> <span data-ttu-id="31c3f-203">SQLXMLBulkLoad 개체의 SchemaGen 속성을 TRUE로 설정 하면이를 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-203">Setting the SchemaGen property of the SQLXMLBulkLoad object to TRUE does this.</span></span> <span data-ttu-id="31c3f-204">또한 선택적으로 XML 대량 로드를 요청 하 여 기존 테이블을 삭제 하 고 SGDropTables 속성을 TRUE로 설정 하 여 다시 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-204">You can also optionally request XML Bulk Load to drop any existing tables and re-create them by setting the SGDropTables property to TRUE.</span></span> <span data-ttu-id="31c3f-205">다음 VBScript 예에서는 이러한 속성의 사용 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-205">The following VBScript example illustrates the use of these properties.</span></span>  
  
 <span data-ttu-id="31c3f-206">또한 이 예에서는 두 개의 추가 속성을 TRUE로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-206">Also, this example sets two additional properties to TRUE:</span></span>  
  
-   <span data-ttu-id="31c3f-207">CheckConstraints.</span><span class="sxs-lookup"><span data-stu-id="31c3f-207">CheckConstraints.</span></span> <span data-ttu-id="31c3f-208">이 속성을 TRUE로 설정하면 테이블에 삽입되는 데이터가 테이블에 지정된 제약 조건을 위반하지 않도록 보장할 수 있습니다(이 예에서는 Cust와 CustOrder 테이블 간에 지정된 PRIMARY KEY/FOREIGN KEY 제약 조건).</span><span class="sxs-lookup"><span data-stu-id="31c3f-208">Setting this property to TRUE ensures that the data being inserted into the tables does not violate any constraints that have been specified on the tables (in this case the PRIMARY KEY/FOREIGN KEY constraints specified between the Cust and CustOrder tables).</span></span> <span data-ttu-id="31c3f-209">제약 조건 위반이 발생하면 대량 로드는 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-209">If there is a constraint violation, the bulk load fails.</span></span>  
  
-   <span data-ttu-id="31c3f-210">XMLFragment.</span><span class="sxs-lookup"><span data-stu-id="31c3f-210">XMLFragment.</span></span> <span data-ttu-id="31c3f-211">예제 XML 문서(데이터 원본)에는 단일 최상위 요소가 없고 따라서 조각이므로 이 속성은 TRUE로 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-211">This property must be set to TRUE because the sample XML document (data source) contains no single, top-level element (and is thus a fragment).</span></span>  
  
 <span data-ttu-id="31c3f-212">다음은 VBScript 코드입니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-212">This is the VBScript code:</span></span>  
  
```  
Dim objBL   
Set objBL = CreateObject("SQLXMLBulkLoad.SQLXMLBulkload.4.0")  
objBL.ConnectionString = "provider=SQLOLEDB;data source=localhost;database=tempdb;integrated security=SSPI"  
objBL.ErrorLogFile = "c:\error.log"  
  
objBL.CheckConstraints=true  
objBL.XMLFragment = True  
objBL.SchemaGen = True  
objBL.SGDropTables = True  
  
objBL.Execute "SampleSchema.xml", "SampleXMLData.xml"  
Set objBL = Nothing  
```  
  
#### <a name="to-test-a-working-sample"></a><span data-ttu-id="31c3f-213">작업 예제를 테스트하려면</span><span class="sxs-lookup"><span data-stu-id="31c3f-213">To test a working sample</span></span>  
  
1.  <span data-ttu-id="31c3f-214">기본 텍스트 편집기 또는 XML 편집기에서 파일을 만든 후 SampleSchema.xml로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-214">Create a file in your preferred text or XML editor, and save it as SampleSchema.xml.</span></span> <span data-ttu-id="31c3f-215">앞의 예 "스키마의 체인 관계를 사용하여 XML 대량 로드"에 제공된 XSD 스키마를 파일에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-215">Add the XSD schema that is provided in the earlier example, "Using chain relationships in the schema to bulk load XML", to the file.</span></span>  
  
2.  <span data-ttu-id="31c3f-216">기본 텍스트 편집기 또는 XML 편집기에서 파일을 만든 후 SampleXMLData.xml로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-216">Create a file in your preferred text or XML editor, and save it as SampleXMLData.xml.</span></span> <span data-ttu-id="31c3f-217">앞의 예 "스키마의 체인 관계를 사용하여 XML 대량 로드"에 제공된 XML 문서를 파일에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-217">Add the XML document that is provided in the earlier example, "Using chain relationships in the schema to bulk load XML", to the file.</span></span> <span data-ttu-id="31c3f-218">\<ROOT>문서에서 요소를 제거 하 여 조각으로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-218">Remove the \<ROOT> element from the document (to make it a fragment).</span></span>  
  
3.  <span data-ttu-id="31c3f-219">기본 텍스트 편집기 또는 XML 편집기에서 파일을 만든 후 ValidateAndBulkload.vbs로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-219">Create a file in your preferred text or XML editor, and save it as ValidateAndBulkload.vbs.</span></span> <span data-ttu-id="31c3f-220">이 파일에 이 예의 VBScript 코드를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-220">To this file, add the VBScript code in this example.</span></span> <span data-ttu-id="31c3f-221">연결 문자열을 수정하여 해당 서버 및 데이터베이스 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-221">Modify the connection string to provide the appropriate server and database name.</span></span> <span data-ttu-id="31c3f-222">Execute 메서드에 대 한 매개 변수로 지정 된 파일에 대 한 적절 한 경로를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-222">Specify the appropriate path for the files that are specified as parameters to the Execute method.</span></span>  
  
4.  <span data-ttu-id="31c3f-223">VBScript 코드를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-223">Execute the VBScript code.</span></span> <span data-ttu-id="31c3f-224">XML 대량 로드에서 제공된 매핑 스키마를 기반으로 필요한 테이블을 만들고 이 테이블에 데이터를 대량 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-224">The XML Bulk Load creates the necessary tables on the basis of the mapping schema that is provided and bulk loads the data in it.</span></span>  
  
## <a name="f-bulk-loading-from-a-stream"></a><span data-ttu-id="31c3f-225">F.</span><span class="sxs-lookup"><span data-stu-id="31c3f-225">F.</span></span> <span data-ttu-id="31c3f-226">스트림에서 대량 로드</span><span class="sxs-lookup"><span data-stu-id="31c3f-226">Bulk loading from a stream</span></span>  
 <span data-ttu-id="31c3f-227">XML 대량 로드 개체 모델의 Execute 메서드는 두 개의 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-227">The Execute method of the XML Bulk Load object model takes two parameters.</span></span> <span data-ttu-id="31c3f-228">첫 번째 매개 변수는 매핑 스키마 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-228">The first parameter is the mapping schema file.</span></span> <span data-ttu-id="31c3f-229">두 번째 매개 변수는 데이터베이스에 로드될 XML 데이터를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-229">The second parameter provides the XML data that is to be loaded in the database.</span></span> <span data-ttu-id="31c3f-230">Xml 데이터를 XML 대량 로드의 Execute 메서드에 전달 하는 방법에는 두 가지가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-230">There are two ways to pass the XML data to the Execute method of XML Bulk Load:</span></span>  
  
-   <span data-ttu-id="31c3f-231">파일 이름을 매개 변수로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-231">Specify the file name as the parameter.</span></span>  
  
-   <span data-ttu-id="31c3f-232">XML 데이터를 포함하는 스트림을 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-232">Pass a stream that contains the XML data.</span></span>  
  
 <span data-ttu-id="31c3f-233">이 예에서는 스트림에서 대량 로드하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-233">This example illustrates how to bulk load from a stream.</span></span>  
  
 <span data-ttu-id="31c3f-234">VBScript는 먼저 SELECT 문을 실행하여 Northwind 데이터베이스의 Customers 테이블에서 고객 정보를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-234">VBScript first executes a SELECT statement to retrieve customer information from the Customers table in the Northwind database.</span></span> <span data-ttu-id="31c3f-235">SELECT 문에 FOR XML 절이 지정되므로(ELEMENTS 옵션 사용) 쿼리는 다음 형식의 요소 중심 XML 문서를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-235">Because the FOR XML clause is specified (with the ELEMENTS option) in the SELECT statement, the query returns an element-centric XML document of this form:</span></span>  
  
```  
<Customer>  
  <CustomerID>..</CustomerID>  
  <CompanyName>..</CompanyName>  
  <City>..</City>  
</Customer>  
...  
```  
  
 <span data-ttu-id="31c3f-236">그런 다음 스크립트는 XML을 Execute 메서드에 대 한 스트림으로 두 번째 매개 변수로 전달 합니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-236">The script then passes the XML as a stream to the Execute method as its second parameter.</span></span> <span data-ttu-id="31c3f-237">Execute 메서드는 데이터를 Cust 테이블에 대량 로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-237">The Execute method bulk loads the data into the Cust table.</span></span>  
  
 <span data-ttu-id="31c3f-238">이 스크립트는 SchemaGen 속성을 TRUE로 설정 하 고 SGDropTables 속성을 TRUE로 설정 하므로 XML 대량 로드는 지정 된 데이터베이스에 Cust 테이블을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-238">Because this script sets the SchemaGen property to TRUE and SGDropTables property to TRUE, XML Bulk Load creates the Cust table in the specified database.</span></span> <span data-ttu-id="31c3f-239">테이블이 이미 있는 경우 이 테이블을 먼저 삭제한 다음 다시 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-239">(If the table already exists, it first drops the table and then re-creates it.)</span></span>  
  
 <span data-ttu-id="31c3f-240">다음은 VBScript 예입니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-240">This is the VBScript example:</span></span>  
  
```  
Set objBL = CreateObject("SQLXMLBulkLoad.SQLXMLBulkload.4.0")  
Set objCmd = CreateObject("ADODB.Command")  
Set objConn = CreateObject("ADODB.Connection")  
Set objStrmOut = CreateObject ("ADODB.Stream")  
  
objBL.ConnectionString = "provider=SQLOLEDB;data source=localhost;database=tempdb;integrated security=SSPI"  
objBL.ErrorLogFile     = "c:\error.log"  
objBL.CheckConstraints = True  
objBL.SchemaGen        = True  
objBL.SGDropTables     = True  
objBL.XMLFragment      = True  
' Open a connection to the instance of SQL Server to get the source data.  
  
objConn.Open "provider=SQLOLEDB;server=(local);database=tempdb;integrated security=SSPI"  
Set objCmd.ActiveConnection = objConn  
objCmd.CommandText = "SELECT CustomerID, CompanyName, City FROM Customers FOR XML AUTO, ELEMENTS"  
  
' Open the return stream and execute the command.  
Const adCRLF = -1  
Const adExecuteStream = 1024  
objStrmOut.Open  
objStrmOut.LineSeparator = adCRLF  
objCmd.Properties("Output Stream").Value = objStrmOut  
objCmd.Execute , , adExecuteStream  
objStrmOut.Position = 0  
  
' Execute bulk load. Read source XML data from the stream.  
objBL.Execute "SampleSchema.xml", objStrmOut  
  
Set objBL = Nothing  
```  
  
 <span data-ttu-id="31c3f-241">다음 XSD 매핑 스키마는 테이블을 만드는 데 필요한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-241">The following XSD mapping schema provides the necessary information to create the table:</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
<xsd:element name="ROOT" sql:is-constant="true" >  
  <xsd:complexType>  
    <xsd:sequence>  
      <xsd:element ref="Customers"/>  
    </xsd:sequence>  
  </xsd:complexType>  
</xsd:element>  
<xsd:element name="Customers" sql:relation="Cust" >  
  <xsd:complexType>  
    <xsd:sequence>  
      <xsd:element name="CustomerID"  
                   type="xsd:string"  
                   sql:datatype="nvarchar(5)"/>  
      <xsd:element name="CompanyName"  
                   type="xsd:string"  
                   sql:datatype="nvarchar(40)"/>  
      <xsd:element name="City"  
                   type="xsd:string"  
                   sql:datatype="nvarchar(40)"/>  
    </xsd:sequence>  
  </xsd:complexType>  
</xsd:element>  
</xsd:schema>  
```  
  
 <span data-ttu-id="31c3f-242">다음은 이에 해당하는 XDR 스키마입니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-242">This is equivalent XDR schema:</span></span>  
  
```  
<?xml version="1.0" ?>  
<Schema xmlns="urn:schemas-microsoft-com:xml-data"   
        xmlns:dt="urn:schemas-microsoft-com:xml:datatypes"    
        xmlns:sql="urn:schemas-microsoft-com:xml-sql" >  
   <ElementType name="CustomerID" dt:type="int" />  
   <ElementType name="CompanyName" dt:type="string" />  
   <ElementType name="City" dt:type="string" />  
  
   <ElementType name="root" sql:is-constant="1">  
      <element type="Customers" />  
   </ElementType>  
  
   <ElementType name="Customers" sql:relation="Cust"  >  
      <element type="CustomerID" sql:field="CustomerID" />  
      <element type="CompanyName" sql:field="CompanyName" />  
      <element type="City" sql:field="City" />  
    </ElementType>  
</Schema>  
```  
  
### <a name="opening-a-stream-on-an-existing-file"></a><span data-ttu-id="31c3f-243">기존 파일에서 스트림 열기</span><span class="sxs-lookup"><span data-stu-id="31c3f-243">Opening a Stream on an Existing File</span></span>  
 <span data-ttu-id="31c3f-244">기존 XML 데이터 파일에서 스트림을 열고 파일 이름을 매개 변수로 전달 하는 대신 Execute 메서드에 스트림으로 전달할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-244">You can also open a stream on an existing XML data file and pass the stream as a parameter to the Execute method (instead of passing the file name as the parameter).</span></span>  
  
 <span data-ttu-id="31c3f-245">다음은 스트림을 매개 변수로 전달하는 Visual Basic 예입니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-245">This is a Visual Basic example of passing a stream as the parameter:</span></span>  
  
```  
Private Sub Form_Load()  
Dim objBL As New SQLXMLBulkLoad  
Dim objStrm As New ADODB.Stream  
Dim objFileSystem As New Scripting.FileSystemObject  
Dim objFile As Scripting.TextStream  
  
MsgBox "Begin BulkLoad..."  
objBL.ConnectionString = "provider=SQLOLEDB;data source=localhost;database=tempdb;integrated security=SSPI"  
objBL.ErrorLogFile = "c:\error.log"  
objBL.CheckConstraints = True  
objBL.SchemaGen = True  
objBL.SGDropTables = True  
' Here again a stream is specified that contains the source data   
' (instead of the file name). But this is just an illustration.  
' Usually this is useful if you have an XML data   
' stream that is created by some other means that you want to bulk   
' load. This example starts with an XML text file, so it may not be the   
' best to use a stream (you can specify the file name directly).  
' Here you could have specified the file name itself.   
Set objFile = objFileSystem.OpenTextFile("c:\SampleData.xml")  
objStrm.Open  
objStrm.WriteText objFile.ReadAll  
objStrm.Position = 0  
objBL.Execute "c:\SampleSchema.xml", objStrm  
  
Set objBL = Nothing  
MsgBox "Done."  
End Sub  
```  
  
 <span data-ttu-id="31c3f-246">애플리케이션을 테스트하려면 파일(SampleData.xml)의 다음 XML 문서와 이 예에 제공된 XSD 스키마를 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="31c3f-246">To test the application, use the following XML document in a file (SampleData.xml) and the XSD schema that is provided in this example:</span></span>  
  
 <span data-ttu-id="31c3f-247">다음은 XML 원본 데이터(SampleData.xml)입니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-247">This is the XML source data (SampleData.xml):</span></span>  
  
```  
<ROOT>  
  <Customers>  
    <CustomerID>1111</CustomerID>  
    <CompanyName>Hanari Carnes</CompanyName>  
    <City>NY</City>  
    <Order OrderID="1" />  
    <Order OrderID="2" />  
  </Customers>  
  
  <Customers>  
    <CustomerID>1112</CustomerID>  
    <CompanyName>Toms Spezialitten</CompanyName>  
     <City>LA</City>  
    <Order OrderID="3" />  
  </Customers>  
  <Customers>  
    <CustomerID>1113</CustomerID>  
    <CompanyName>Victuailles en stock</CompanyName>  
    <Order CustomerID= "4444" OrderID="4" />  
</Customers>  
</ROOT>  
```  
  
 <span data-ttu-id="31c3f-248">다음은 동등한 XDR 스키마입니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-248">This is the equivalent XDR schema:</span></span>  
  
```  
<?xml version="1.0" ?>  
<Schema xmlns="urn:schemas-microsoft-com:xml-data"   
        xmlns:dt="urn:schemas-microsoft-com:xml:datatypes"    
        xmlns:sql="urn:schemas-microsoft-com:xml-sql" >  
  
    <ElementType name="Order" sql:relation="CustOrder" >  
      <AttributeType name="OrderID" />  
      <AttributeType name="CustomerID" />  
      <attribute type="OrderID" />  
      <attribute type="CustomerID" />  
    </ElementType>  
  
   <ElementType name="CustomerID" dt:type="int" />  
   <ElementType name="CompanyName" dt:type="string" />  
   <ElementType name="City" dt:type="string" />  
  
   <ElementType name="root" sql:is-constant="1">  
      <element type="Customers" />  
   </ElementType>  
  
   <ElementType name="Customers" sql:relation="Cust"  >  
      <element type="CustomerID" sql:field="CustomerID" />  
      <element type="CompanyName" sql:field="CompanyName" />  
      <element type="City" sql:field="City" />  
      <element type="Order" >  
             <sql:relationship  
                key-relation="Cust"  
                key="CustomerID"  
                foreign-key="CustomerID"  
                foreign-relation="CustOrder" />  
      </element>  
   </ElementType>  
</Schema>  
```  
  
## <a name="g-bulk-loading-in-overflow-columns"></a><span data-ttu-id="31c3f-249">G.</span><span class="sxs-lookup"><span data-stu-id="31c3f-249">G.</span></span> <span data-ttu-id="31c3f-250">오버플로 열에 대량 로드</span><span class="sxs-lookup"><span data-stu-id="31c3f-250">Bulk loading in overflow columns</span></span>  
 <span data-ttu-id="31c3f-251">매핑 스키마가 `sql:overflow-field` 주석을 사용하여 오버플로 열을 지정하는 경우 XML 대량 로드는 원본 문서에서 사용되지 않은 모든 데이터를 이 열에 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-251">If the mapping schema specifies an overflow column by using the `sql:overflow-field` annotation, XML Bulk Load copies all unconsumed data from the source document into this column.</span></span>  
  
 <span data-ttu-id="31c3f-252">다음 XSD 스키마를 고려해 보십시오.</span><span class="sxs-lookup"><span data-stu-id="31c3f-252">Consider this XSD schema:</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
<xsd:annotation>  
  <xsd:appinfo>  
    <sql:relationship name="CustCustOrder"  
          parent="Cust"  
          parent-key="CustomerID"  
          child="CustOrder"  
          child-key="CustomerID" />  
  </xsd:appinfo>  
</xsd:annotation>  
  <xsd:element name="Customers" sql:relation="Cust"  
                                sql:overflow-field="OverflowColumn" >  
   <xsd:complexType>  
     <xsd:sequence>  
       <xsd:element name="CustomerID"  type="xsd:integer" />  
       <xsd:element name="CompanyName" type="xsd:string" />  
       <xsd:element name="City"        type="xsd:string" />  
       <xsd:element name="Order"   
                          sql:relation="CustOrder"  
                          sql:relationship="CustCustOrder" >  
         <xsd:complexType>  
          <xsd:attribute name="OrderID" type="xsd:integer" />  
          <xsd:attribute name="CustomerID" type="xsd:integer" />  
         </xsd:complexType>  
       </xsd:element>  
     </xsd:sequence>  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
 <span data-ttu-id="31c3f-253">스키마는 Cust 테이블에 대한 오버플로 열(OverflowColumn)을 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-253">The schema identifies an overflow column (OverflowColumn) for the Cust table.</span></span> <span data-ttu-id="31c3f-254">따라서 각 요소에 대해 소비 되지 않은 모든 XML 데이터가 **\<Customer>** 이 열에 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-254">As a result, all unconsumed XML data for each **\<Customer>** element is added to this column.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="31c3f-255">모든 추상 요소 ( **abstract = "true"** 가 지정 된 요소) 및 모든 금지 된 특성 ( **금지 = "true"** 가 지정 된 특성)은 XML 대량 로드에 의해 오버플로로 간주 되 고 지정 된 경우 오버플로 열에 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-255">All abstract elements (elements for which **abstract="true"** is specified) and all prohibited attributes (attributes for which **prohibited="true"** is specified) are considered overflow by XML Bulk Load and are added to the overflow column, if specified.</span></span> <span data-ttu-id="31c3f-256">지정되지 않은 경우에는 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-256">(Otherwise, they are ignored.)</span></span>  
  
#### <a name="to-test-a-working-sample"></a><span data-ttu-id="31c3f-257">작업 예제를 테스트하려면</span><span class="sxs-lookup"><span data-stu-id="31c3f-257">To test a working sample</span></span>  
  
1.  <span data-ttu-id="31c3f-258">**Tempdb** 데이터베이스에 두 개의 테이블을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-258">Create two tables in **tempdb** database:</span></span>  
  
    ```  
    USE tempdb;  
    CREATE TABLE Cust (  
                  CustomerID     int         PRIMARY KEY,  
                  CompanyName    varchar(20) NOT NULL,  
                  City           varchar(20) DEFAULT 'Seattle',  
                  OverflowColumn nvarchar(200));  
    GO  
    CREATE TABLE CustOrder (  
                  OrderID    int PRIMARY KEY,  
                  CustomerID int FOREIGN KEY   
                                 REFERENCES Cust(CustomerID));  
    GO  
    ```  
  
2.  <span data-ttu-id="31c3f-259">기본 텍스트 편집기 또는 XML 편집기에서 파일을 만든 후 SampleSchema.xml로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-259">Create a file in your preferred text or XML editor, and save it as SampleSchema.xml.</span></span> <span data-ttu-id="31c3f-260">이 예에 제공되는 XSD 스키마를 이 파일에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-260">Add the XSD schema that is provided in this example to the file.</span></span>  
  
3.  <span data-ttu-id="31c3f-261">기본 텍스트 편집기 또는 XML 편집기에서 파일을 만든 후 SampleXMLData.xml로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-261">Create a file in your preferred text or XML editor, and save it as SampleXMLData.xml.</span></span> <span data-ttu-id="31c3f-262">이 파일에 다음 XML 문서를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-262">Add the following XML document to the file:</span></span>  
  
    ```  
    <ROOT>  
      <Customers>  
        <CustomerID>1111</CustomerID>  
        <CompanyName>Hanari Carnes</CompanyName>  
        <City><![CDATA[NY]]> </City>  
        <Junk>garbage in overflow</Junk>  
        <Order OrderID="1" />  
        <Order OrderID="2" />  
      </Customers>  
  
      <Customers>  
        <CustomerID>1112</CustomerID>  
        <CompanyName>Toms Spezialitten</CompanyName>  
         <![CDATA[LA]]>   
        <!-- <xyz><address>111 Maple, Seattle</address></xyz>   -->  
        <Order OrderID="3" />  
      </Customers>  
      <Customers>  
        <CustomerID>1113</CustomerID>  
        <CompanyName>Victuailles en stock</CompanyName>  
        <Order OrderID="4" />  
    </Customers>  
    </ROOT>  
    ```  
  
4.  <span data-ttu-id="31c3f-263">기본 텍스트 편집기 또는 XML 편집기에서 파일을 만든 후 ValidateAndBulkload.vbs로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-263">Create a file in your preferred text or XML editor, and save it as ValidateAndBulkload.vbs.</span></span> <span data-ttu-id="31c3f-264">이 파일에 다음 Microsoft Visual Basic Scripting Edition(VBScript) 코드를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-264">To this file, add the following Microsoft Visual Basic Scripting Edition (VBScript) code.</span></span> <span data-ttu-id="31c3f-265">연결 문자열을 수정하여 해당 서버 및 데이터베이스 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-265">Modify the connection string to provide the appropriate server and database name.</span></span> <span data-ttu-id="31c3f-266">Execute 메서드에 대 한 매개 변수로 지정 된 파일에 대 한 적절 한 경로를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-266">Specify the appropriate path for the files that are specified as parameters to the Execute method.</span></span>  
  
    ```  
    set objBL = CreateObject("SQLXMLBulkLoad.SQLXMLBulkload.4.0")  
    objBL.ConnectionString = "provider=SQLOLEDB;data source=localhost;database=tempdb;integrated security=SSPI"  
    objBL.ErrorLogFile = "c:\error.log"  
    objBL.CheckConstraints = True  
    objBL.Execute "SampleSchema.xml", "SampleXMLData.xml"  
    set objBL=Nothing  
    ```  
  
5.  <span data-ttu-id="31c3f-267">VBScript 코드를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-267">Execute the VBScript code.</span></span>  
  
 <span data-ttu-id="31c3f-268">다음은 동등한 XDR 스키마입니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-268">This is the equivalent XDR schema:</span></span>  
  
```  
<?xml version="1.0" ?>  
<Schema xmlns="urn:schemas-microsoft-com:xml-data"   
        xmlns:dt="urn:schemas-microsoft-com:xml:datatypes"    
        xmlns:sql="urn:schemas-microsoft-com:xml-sql" >  
  
    <ElementType name="Order" sql:relation="CustOrder" >  
      <AttributeType name="OrderID" />  
      <AttributeType name="CustomerID" />  
      <attribute type="OrderID" />  
      <attribute type="CustomerID" />  
    </ElementType>  
  
   <ElementType name="CustomerID" dt:type="int" />  
   <ElementType name="CompanyName" dt:type="string" />  
   <ElementType name="City" dt:type="string" />  
  
   <ElementType name="root" sql:is-constant="1">  
      <element type="Customers" />  
   </ElementType>  
  
   <ElementType name="Customers" sql:relation="Cust"   
                       sql:overflow-field="OverflowColumn"  >  
      <element type="CustomerID" sql:field="CustomerID" />  
      <element type="CompanyName" sql:field="CompanyName" />  
      <element type="City" sql:field="City" />  
      <element type="Order" >  
             <sql:relationship  
                key-relation="Cust"  
                key="CustomerID"  
                foreign-key="CustomerID"  
                foreign-relation="CustOrder" />  
      </element>  
   </ElementType>  
</Schema>  
```  
  
## <a name="h-specifying-the-file-path-for-temp-files-in-transaction-mode"></a><span data-ttu-id="31c3f-269">H.</span><span class="sxs-lookup"><span data-stu-id="31c3f-269">H.</span></span> <span data-ttu-id="31c3f-270">트랜잭션 모드에서 임시 파일에 대한 파일 경로 지정</span><span class="sxs-lookup"><span data-stu-id="31c3f-270">Specifying the file path for temp files in transaction mode</span></span>  
 <span data-ttu-id="31c3f-271">트랜잭션 모드에서 대량 로드 하는 경우, 즉 Transaction 속성이 TRUE로 설정 된 경우 다음 조건 중 하나에 해당 하는 경우에도 TempFilePath 속성을 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-271">When you are bulk loading in transaction mode (that is, when the Transaction property is set to TRUE), you also must set the TempFilePath property when either of the following conditions is true:</span></span>  
  
-   <span data-ttu-id="31c3f-272">원격 서버에 대량 로드하는 경우</span><span class="sxs-lookup"><span data-stu-id="31c3f-272">You are bulk loading to a remote server.</span></span>  
  
-   <span data-ttu-id="31c3f-273">TEMP 환경 변수에 지정된 경로와 다른 대체 로컬 드라이브 또는 폴더를 사용하여 트랜잭션 모드에서 만들어진 임시 파일을 저장하려는 경우</span><span class="sxs-lookup"><span data-stu-id="31c3f-273">You want to use an alternate local drive or folder (one other than the path that is specified by the TEMP environment variable) to store the temporary files that are created in the transaction mode.</span></span>  
  
 <span data-ttu-id="31c3f-274">예를 들어 다음 VBScript 코드는 트랜잭션 모드에서 SampleXMLData.xml 파일의 데이터를 데이터베이스 테이블에 대량 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-274">For example, the following VBScript code bulk loads data from the SampleXMLData.xml file into the database tables in transaction mode.</span></span> <span data-ttu-id="31c3f-275">TempFilePath 속성은 트랜잭션 모드에서 생성 된 임시 파일의 경로를 설정 하는 데 지정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-275">The TempFilePath property is specified to set the path for the temporary files that are generated in transaction mode.</span></span>  
  
```  
set objBL = CreateObject("SQLXMLBulkLoad.SQLXMLBulkload.4.0")  
objBL.ConnectionString = "provider=SQLOLEDB;data source=localhost;database=tempdb;integrated security=SSPI"  
objBL.ErrorLogFile = "c:\error.log"  
objBL.CheckConstraints = True  
objBL.Transaction=True  
objBL.TempFilePath="\\Server\MyDir"  
objBL.Execute "SampleSchema.xml", "SampleXMLData.xml"  
set objBL=Nothing  
```  
  
> [!NOTE]  
>  <span data-ttu-id="31c3f-276">임시 파일 경로는 대상 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인스턴스의 서비스 계정과 대량 로드 애플리케이션을 실행 중인 계정에서 액세스 가능한 공유 위치여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-276">The temporary file path must be a shared location that is accessible to the service account of the target instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] and to the account that is running the bulk load application.</span></span> <span data-ttu-id="31c3f-277">로컬 서버에서 대량 로드 하는 경우가 아니면 임시 파일 경로는 UNC 경로 (예: \servername\sharename) 여야 합니다 \\ .</span><span class="sxs-lookup"><span data-stu-id="31c3f-277">Unless you are bulk loading on a local server, the temporary file path must be a UNC path (such as \\\servername\sharename).</span></span>  
  
#### <a name="to-test-a-working-sample"></a><span data-ttu-id="31c3f-278">작업 예제를 테스트하려면</span><span class="sxs-lookup"><span data-stu-id="31c3f-278">To test a working sample</span></span>  
  
1.  <span data-ttu-id="31c3f-279">**Tempdb** 데이터베이스에이 테이블을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-279">Create this table in **tempdb** database:</span></span>  
  
    ```  
    USE tempdb;  
    CREATE TABLE Cust (     CustomerID uniqueidentifier,   
          LastName  varchar(20));  
    GO  
    ```  
  
2.  <span data-ttu-id="31c3f-280">기본 텍스트 편집기 또는 XML 편집기에서 파일을 만든 후 SampleSchema.xml로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-280">Create a file in your preferred text or XML editor, and save it as SampleSchema.xml.</span></span> <span data-ttu-id="31c3f-281">다음 XSD 스키마를 파일에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-281">Add the following XSD schema to the file:</span></span>  
  
    ```  
    <xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
                xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
      <xsd:element name="ROOT" sql:is-constant="true" >  
        <xsd:complexType>  
          <xsd:sequence>  
            <xsd:element ref="Customers" />  
          </xsd:sequence>  
        </xsd:complexType>  
      </xsd:element>  
  
      <xsd:element name="Customers" sql:relation="Cust" >  
       <xsd:complexType>  
         <xsd:attribute name="CustomerID"  type="xsd:string" />  
         <xsd:attribute name="LastName" type="xsd:string" />  
       </xsd:complexType>  
      </xsd:element>  
    </xsd:schema>  
    ```  
  
3.  <span data-ttu-id="31c3f-282">기본 텍스트 편집기 또는 XML 편집기에서 파일을 만든 후 SampleXMLData.xml로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-282">Create a file in your preferred text or XML editor, and save it as SampleXMLData.xml.</span></span> <span data-ttu-id="31c3f-283">이 파일에 다음 XML 문서를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-283">Add the following XML document to the file:</span></span>  
  
    ```  
    <ROOT>  
    <Customers CustomerID="6F9619FF-8B86-D011-B42D-00C04FC964FF"   
               LastName="Smith" />  
    </ROOT>  
    ```  
  
4.  <span data-ttu-id="31c3f-284">기본 텍스트 편집기 또는 XML 편집기에서 파일을 만든 후 ValidateAndBulkload.vbs로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-284">Create a file in your preferred text or XML editor, and save it as ValidateAndBulkload.vbs.</span></span> <span data-ttu-id="31c3f-285">이 파일에 다음 VBScript 코드를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-285">To this file, add the following VBScript code.</span></span> <span data-ttu-id="31c3f-286">연결 문자열을 수정하여 해당 서버 및 데이터베이스 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-286">Modify the connection string to provide the appropriate server and database name.</span></span> <span data-ttu-id="31c3f-287">Execute 메서드에 대 한 매개 변수로 지정 된 파일에 대 한 적절 한 경로를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-287">Specify the appropriate path for the files that are specified as parameters to the Execute method.</span></span> <span data-ttu-id="31c3f-288">또한 TempFilePath 속성에 대해 적절 한 경로를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-288">Also specify the appropriate path for the TempFilePath property.</span></span>  
  
    ```  
    set objBL = CreateObject("SQLXMLBulkLoad.SQLXMLBulkload.4.0")  
    objBL.ConnectionString = "provider=SQLOLEDB;data source=localhost;database=tempdb;integrated security=SSPI"  
    objBL.ErrorLogFile = "c:\error.log"  
    objBL.CheckConstraints = True  
    objBL.Transaction=True  
    objBL.TempFilePath="\\server\folder"  
    objBL.Execute "SampleSchema.xml", "SampleXMLData.xml"  
    set objBL=Nothing  
    ```  
  
5.  <span data-ttu-id="31c3f-289">VBScript 코드를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-289">Execute the VBScript code.</span></span>  
  
     <span data-ttu-id="31c3f-290">`sql:datatype` **Customerid** 의 값이 중괄호 ({및})를 포함 하는 GUID로 지정 된 경우 스키마는 **customerid** 특성에 해당 하는을 지정 해야 합니다. 예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-290">The schema must specify the corresponding `sql:datatype` for the **CustomerID** attribute when the value for **CustomerID** is specified as a GUID that includes braces ({ and }), such as:</span></span>  
  
    ```  
    <ROOT>  
    <Customers CustomerID="{6F9619FF-8B86-D011-B42D-00C04FC964FF}"   
               LastName="Smith" />  
    </ROOT>  
    ```  
  
     <span data-ttu-id="31c3f-291">다음은 업데이트된 스키마입니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-291">This is the updated schema:</span></span>  
  
    ```  
    <xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
                xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
      <xsd:element name="ROOT" sql:is-constant="true" >  
        <xsd:complexType>  
          <xsd:sequence>  
            <xsd:element ref="Customers" />  
          </xsd:sequence>  
        </xsd:complexType>  
      </xsd:element>  
  
      <xsd:element name="Customers" sql:relation="Cust" >  
       <xsd:complexType>  
         <xsd:attribute name="CustomerID"  type="xsd:string"   
                        sql:datatype="uniqueidentifier" />  
         <xsd:attribute name="LastName" type="xsd:string" />  
       </xsd:complexType>  
      </xsd:element>  
    </xsd:schema>  
    ```  
  
     <span data-ttu-id="31c3f-292">`sql:datatype`열 유형을으로 식별 하는을 지정 하면 `uniqueidentifier` 대량 로드 작업은 열에 삽입 하기 전에 **CustomerID** 값에서 중괄호 ({및})를 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-292">When `sql:datatype` is specified identifying the column type as `uniqueidentifier`, the bulk load operation removes the braces ({ and }) from the **CustomerID** value before inserting it in the column.</span></span>  
  
 <span data-ttu-id="31c3f-293">다음은 동등한 XDR 스키마입니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-293">This is the equivalent XDR schema:</span></span>  
  
```  
<?xml version="1.0" ?>  
<Schema xmlns="urn:schemas-microsoft-com:xml-data"   
        xmlns:dt="urn:schemas-microsoft-com:datatypes"    
        xmlns:sql="urn:schemas-microsoft-com:xml-sql" >  
<ElementType name="ROOT" sql:is-constant="1">  
      <element type="Customers" />  
</ElementType>  
<ElementType name="Customers" sql:relation="Cust" >  
  <AttributeType name="CustomerID"  sql:datatype="uniqueidentifier" />  
  <AttributeType name="LastName"   />  
  
  <attribute type="CustomerID" />  
  <attribute type="LastName"   />  
</ElementType>  
</Schema>  
```  
  
## <a name="i-using-an-existing-database-connection-with-the-connectioncommand-property"></a><span data-ttu-id="31c3f-294">9\.</span><span class="sxs-lookup"><span data-stu-id="31c3f-294">I.</span></span> <span data-ttu-id="31c3f-295">ConnectionCommand 속성으로 기존 데이터베이스 연결 사용</span><span class="sxs-lookup"><span data-stu-id="31c3f-295">Using an existing database connection with the ConnectionCommand property</span></span>  
 <span data-ttu-id="31c3f-296">기존 ADO 연결을 사용하여 XML을 대량 로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-296">You can use an existing ADO connection to bulk load XML.</span></span> <span data-ttu-id="31c3f-297">이 방법은 XML 대량 로드 외에도 많은 작업이 데이터 원본에 대해 수행되는 경우 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-297">This is useful if XML Bulk Load is just one of many operations that will be performed on a data source.</span></span>  
  
 <span data-ttu-id="31c3f-298">ConnectionCommand 속성을 사용 하면 ADO 명령 개체를 사용 하 여 기존 ADO 연결을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-298">The ConnectionCommand property enables you to use an existing ADO connection by using an ADO command object.</span></span> <span data-ttu-id="31c3f-299">다음 Visual Basic 예에서 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-299">This is illustrated in the following Visual Basic example:</span></span>  
  
```  
Private Sub Form_Load()  
Dim objBL As New SQLXMLBulkLoad4  
Dim objCmd As New ADODB.Command  
Dim objConn As New ADODB.Connection  
  
'Open a connection to an instance of SQL Server.  
objConn.Open "provider=SQLOLEDB;data source=(local);database=tempdb;integrated security=SSPI"  
'Ask the Command object to use the connection just established.  
Set objCmd.ActiveConnection = objConn  
  
'Tell Bulk Load to use the active command object that is using the Connection obj.  
objBL.ConnectionCommand = objCmd  
objBL.ErrorLogFile = "c:\error.log"  
objBL.CheckConstraints = True  
'The Transaction property must be set to True if you use ConnectionCommand.  
objBL.Transaction = True  
objBL.Execute "SampleSchema.xml", "SampleXMLData.xml"  
Set objBL = Nothing  
End Sub  
```  
  
#### <a name="to-test-a-working-sample"></a><span data-ttu-id="31c3f-300">작업 예제를 테스트하려면</span><span class="sxs-lookup"><span data-stu-id="31c3f-300">To test a working sample</span></span>  
  
1.  <span data-ttu-id="31c3f-301">**Tempdb** 데이터베이스에 두 개의 테이블을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-301">Create two tables in **tempdb** database:</span></span>  
  
    ```  
    USE tempdb;  
    CREATE TABLE Cust(  
                   CustomerID   varchar(5) PRIMARY KEY,  
                   CompanyName  varchar(30),  
                   City         varchar(20));  
    GO  
    CREATE TABLE CustOrder(  
                   CustomerID  varchar(5) references Cust (CustomerID),  
                   OrderID     varchar(5) PRIMARY KEY);  
    GO  
    ```  
  
2.  <span data-ttu-id="31c3f-302">기본 텍스트 편집기 또는 XML 편집기에서 파일을 만든 후 SampleSchema.xml로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-302">Create a file in your preferred text or XML editor, and save it as SampleSchema.xml.</span></span> <span data-ttu-id="31c3f-303">다음 XSD 스키마를 파일에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-303">Add the following XSD schema to the file:</span></span>  
  
    ```  
    <xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
                xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
    <xsd:annotation>  
      <xsd:appinfo>  
        <sql:relationship name="CustCustOrder"  
              parent="Cust"  
              parent-key="CustomerID"  
              child="CustOrder"  
              child-key="CustomerID" />  
      </xsd:appinfo>  
    </xsd:annotation>  
      <xsd:element name="ROOT" sql:is-constant="true" >  
        <xsd:complexType>  
          <xsd:sequence>  
            <xsd:element ref="Customers" />  
          </xsd:sequence>  
        </xsd:complexType>  
      </xsd:element>  
      <xsd:element name="Customers" sql:relation="Cust" >  
       <xsd:complexType>  
         <xsd:sequence>  
           <xsd:element name="CustomerID"  type="xsd:integer" />  
           <xsd:element name="CompanyName" type="xsd:string" />  
           <xsd:element name="City"        type="xsd:string" />  
           <xsd:element name="Order"   
                              sql:relation="CustOrder"  
                              sql:relationship="CustCustOrder" >  
             <xsd:complexType>  
              <xsd:attribute name="OrderID" type="xsd:integer" />  
              <xsd:attribute name="CustomerID" type="xsd:integer" />  
             </xsd:complexType>  
           </xsd:element>  
         </xsd:sequence>  
        </xsd:complexType>  
      </xsd:element>  
    </xsd:schema>  
    ```  
  
3.  <span data-ttu-id="31c3f-304">기본 텍스트 편집기 또는 XML 편집기에서 파일을 만든 후 SampleXMLData.xml로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-304">Create a file in your preferred text or XML editor, and save it as SampleXMLData.xml.</span></span> <span data-ttu-id="31c3f-305">이 파일에 다음 XML 문서를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-305">Add the following XML document to the file:</span></span>  
  
    ```  
    <ROOT>  
      <Customers>  
        <CustomerID>1111</CustomerID>  
        <CompanyName>Hanari Carnes</CompanyName>  
        <City>NY</City>  
        <Order OrderID="1" />  
        <Order OrderID="2" />  
      </Customers>  
  
      <Customers>  
        <CustomerID>1112</CustomerID>  
        <CompanyName>Toms Spezialitten</CompanyName>  
         <City>LA</City>  
        <Order OrderID="3" />  
      </Customers>  
      <Customers>  
        <CustomerID>1113</CustomerID>  
        <CompanyName>Victuailles en stock</CompanyName>  
        <Order OrderID="4" />  
    </Customers>  
    </ROOT>  
    ```  
  
4.  <span data-ttu-id="31c3f-306">Visual Basic(표준 EXE) 애플리케이션과 위의 코드를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-306">Create a Visual Basic (Standard EXE) application and the preceding code.</span></span> <span data-ttu-id="31c3f-307">프로젝트에 다음 참조를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-307">Add these references to the project:</span></span>  
  
    ```  
    Microsoft XML BulkLoad for SQL Server 4.0 Type Library  
    Microsoft ActiveX Data objects 2.6 Library  
    ```  
  
5.  <span data-ttu-id="31c3f-308">애플리케이션을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-308">Execute the application.</span></span>  
  
 <span data-ttu-id="31c3f-309">다음은 동등한 XDR 스키마입니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-309">This is the equivalent XDR schema:</span></span>  
  
```  
<?xml version="1.0" ?>  
<Schema xmlns="urn:schemas-microsoft-com:xml-data"   
        xmlns:dt="urn:schemas-microsoft-com:xml:datatypes"    
        xmlns:sql="urn:schemas-microsoft-com:xml-sql" >  
  
   <ElementType name="CustomerID" dt:type="int" />  
   <ElementType name="CompanyName" dt:type="string" />  
   <ElementType name="City" dt:type="string" />  
  
   <ElementType name="root" sql:is-constant="1">  
      <element type="Customers" />  
   </ElementType>  
  
   <ElementType name="Customers" sql:relation="Cust"  >  
      <element type="CustomerID" sql:field="CustomerID" />  
      <element type="CompanyName" sql:field="CompanyName" />  
      <element type="City" sql:field="City" />  
      <element type="Order" >  
         <sql:relationship  
                key-relation="Cust"  
                key="CustomerID"  
                foreign-key="CustomerID"  
                foreign-relation="CustOrder" />  
      </element>  
   </ElementType>  
    <ElementType name="Order" sql:relation="CustOrder" >  
      <AttributeType name="OrderID" />  
      <AttributeType name="CustomerID" />  
      <attribute type="OrderID" />  
      <attribute type="CustomerID" />  
    </ElementType>  
</Schema>  
```  
  
## <a name="j-bulk-loading-in-xml-data-type-columns"></a><span data-ttu-id="31c3f-310">J.</span><span class="sxs-lookup"><span data-stu-id="31c3f-310">J.</span></span> <span data-ttu-id="31c3f-311">xml 데이터 형식 열에 대량 로드</span><span class="sxs-lookup"><span data-stu-id="31c3f-311">Bulk loading in xml Data Type columns</span></span>  
 <span data-ttu-id="31c3f-312">매핑 스키마가 주석을 사용 하 여 [xml 데이터 형식](/sql/t-sql/xml/xml-transact-sql) 열을 지정 하는 경우 `sql:datatype="xml"` xml 대량 로드는 원본 문서에서 매핑된 필드의 xml 자식 요소를이 열에 복사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-312">If the mapping schema specifies a [xml data type](/sql/t-sql/xml/xml-transact-sql) column by using the `sql:datatype="xml"` annotation, XML Bulk Load can copy XML child elements for the mapped field from the source document into this column.</span></span>  
  
 <span data-ttu-id="31c3f-313">AdventureWorks 예제 데이터베이스에 있는 Production.ProductModel 테이블의 뷰를 매핑하는 다음 XSD 스키마를 고려해 보십시오.</span><span class="sxs-lookup"><span data-stu-id="31c3f-313">Consider the following XSD schema, which maps a view of the Production.ProductModel table in the AdventureWorks sample database.</span></span> <span data-ttu-id="31c3f-314">이 표에서 데이터 형식의 CatalogDescription 필드는 `xml` **\<Desc>** 및 주석을 사용 하 여 요소에 매핑됩니다 `sql:field` `sql:datatype="xml"` .</span><span class="sxs-lookup"><span data-stu-id="31c3f-314">In this table, the CatalogDescription field of `xml` data type is mapped to a **\<Desc>** element using the `sql:field` and `sql:datatype="xml"` annotations.</span></span>  
  
```  
<?xml version="1.0" encoding="utf-8" ?>  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
           xmlns:sql="urn:schemas-microsoft-com:mapping-schema"  
           xmlns="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription">   
  <xsd:element name="ProductModel"  sql:relation="Production.ProductModel" >  
    <xsd:complexType>  
      <xsd:sequence>  
        <xsd:element name="Name" type="xs:string"></xsd:element>  
        <xsd:element name="Desc" sql:field="CatalogDescription" sql:datatype="xml">  
        <xsd:complexType>  
          <xsd:sequence>  
            <xsd:element name="ProductDescription">  
              <xsd:complexType>  
                <xsd:sequence>  
                  <xsd:element name="Summary" type="xs:anyType"/>  
                </xsd:sequence>  
              </xsd:complexType>  
            </xsd:element>  
          </xsd:sequence>  
        </xsd:complexType>  
        </xsd:element>   
     </xsd:sequence>  
     <xsd:attribute name="ProductModelID" sql:field="ProductModelID" />  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
#### <a name="to-test-a-working-sample"></a><span data-ttu-id="31c3f-315">작업 예제를 테스트하려면</span><span class="sxs-lookup"><span data-stu-id="31c3f-315">To test a working sample</span></span>  
  
1.  <span data-ttu-id="31c3f-316">AdventureWorks 예제 데이터베이스가 설치되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-316">Verify that the AdventureWorks sample database is installed.</span></span>  
  
2.  <span data-ttu-id="31c3f-317">기본 텍스트 편집기 또는 XML 편집기에서 파일을 만든 후 SampleSchema.xml로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-317">Create a file in your preferred text or XML editor, and save it as SampleSchema.xml.</span></span> <span data-ttu-id="31c3f-318">위의 XSD 스키마를 복사하여 파일에 붙여넣고 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-318">Copy the XSD schema above and paste it into the file and save it.</span></span>  
  
3.  <span data-ttu-id="31c3f-319">기본 텍스트 편집기 또는 XML 편집기에서 파일을 만든 후 SampleXMLData.xml로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-319">Create a file in your preferred text or XML editor, and save it as SampleXMLData.xml.</span></span> <span data-ttu-id="31c3f-320">다음 XML 문서를 복사하여 파일에 붙여넣고 이전 단계에서 사용한 폴더와 동일한 폴더에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-320">Copy the following XML document below and paste it into the file and save it in the same folder as was used for the previous step.</span></span>  
  
    ```  
    <ProductModel ProductModelID="2005">  
        <Name>Mountain-100 (2005 model)</Name>  
        <Desc><?xml-stylesheet href="ProductDescription.xsl" type="text/xsl"?>  
            <p1:ProductDescription xmlns:p1="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription"   
                  xmlns:wm="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain"   
                  xmlns:wf="http://www.adventure-works.com/schemas/OtherFeatures"   
                  xmlns:html="http://www.w3.org/1999/xhtml"   
                  xmlns="">  
                <p1:Summary>  
                    <html:p>Our top-of-the-line competition mountain bike.   
          Performance-enhancing options include the innovative HL Frame,   
          super-smooth front suspension, and traction for all terrain.  
                            </html:p>  
                </p1:Summary>  
                <p1:Manufacturer>  
                    <p1:Name>AdventureWorks</p1:Name>  
                    <p1:Copyright>2002-2005</p1:Copyright>  
                    <p1:ProductURL>HTTP://www.Adventure-works.com</p1:ProductURL>  
                </p1:Manufacturer>  
                <p1:Features>These are the product highlights.   
                     <wm:Warranty>  
                        <wm:WarrantyPeriod>3 years</wm:WarrantyPeriod>  
                        <wm:Description>parts and labor</wm:Description>  
                    </wm:Warranty><wm:Maintenance>  
                        <wm:NoOfYears>10 years</wm:NoOfYears>  
                        <wm:Description>maintenance contract available through your dealer or any AdventureWorks retail store.</wm:Description>  
                    </wm:Maintenance><wf:wheel>High performance wheels.</wf:wheel><wf:saddle>  
                        <html:i>Anatomic design</html:i> and made from durable leather for a full-day of riding in comfort.</wf:saddle><wf:pedal>  
                        <html:b>Top-of-the-line</html:b> clipless pedals with adjustable tension.</wf:pedal><wf:BikeFrame>Each frame is hand-crafted in our Bothell facility to the optimum diameter   
          and wall-thickness required of a premium mountain frame.   
          The heat-treated welded aluminum frame has a larger diameter tube that absorbs the bumps.</wf:BikeFrame><wf:crankset> Triple crankset; alumunim crank arm; flawless shifting. </wf:crankset></p1:Features>  
                <!-- add one or more of these elements... one for each specific product in this product model -->  
                <p1:Picture>  
                    <p1:Angle>front</p1:Angle>  
                    <p1:Size>small</p1:Size>  
                    <p1:ProductPhotoID>118</p1:ProductPhotoID>  
                </p1:Picture>  
                <!-- add any tags in <specifications> -->  
                <p1:Specifications> These are the product specifications.  
                       <Material>Almuminum Alloy</Material><Color>Available in most colors</Color><ProductLine>Mountain bike</ProductLine><Style>Unisex</Style><RiderExperience>Advanced to Professional riders</RiderExperience></p1:Specifications>  
            </p1:ProductDescription>  
        </Desc>  
    </ProductModel>  
    ```  
  
4.  <span data-ttu-id="31c3f-321">기본 텍스트 편집기 또는 XML 편집기에서 파일을 만든 후 BulkloadXml.vbs로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-321">Create a file in your preferred text or XML editor, and save it as BulkloadXml.vbs.</span></span> <span data-ttu-id="31c3f-322">다음 VBScript 코드를 복사한 후 파일에 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-322">Copy the following VBScript code and paste it into the file.</span></span> <span data-ttu-id="31c3f-323">이전 XML 데이터 및 스키마 파일에 사용한 폴더와 동일한 폴더에 이 파일을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-323">Save it in the same folder as was used for the previous XML data and schema files.</span></span>  
  
    ```  
    set objBL = CreateObject("SQLXMLBulkLoad.SQLXMLBulkload.4.0")  
    objBL.ConnectionString = "provider=SQLOLEDB;data source=MyServer;database=AdventureWorks;integrated security=SSPI"  
  
    Dim fso, sAppPath  
    Set fso = CreateObject("Scripting.FileSystemObject")   
    sAppPath = fso.GetFolder(".")   
  
    objBL.ErrorLogFile = sAppPath & "\error.log"  
  
    'Execute XML bulkload using file.  
    objBL.Execute "SampleSchema.xml", "SampleXMLData.xml"  
    set objBL=Nothing  
    ```  
  
5.  <span data-ttu-id="31c3f-324">BulkloadXml.vbs 스크립트를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="31c3f-324">Execute the BulkloadXml.vbs script.</span></span>  
  
  
