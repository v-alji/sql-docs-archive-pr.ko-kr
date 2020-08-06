---
title: 'Sql: limit 필드 및 sql: limit 값을 사용 하 여 값 필터링 (SQLXML 4.0) | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- annotated XSD schemas, filtering values
- limiting values [SQLXML]
- limit-value annotation
- limit-field annotation
- sql:limit-field
- sql:limit-value
- filtering [SQLXML]
ms.assetid: c0f7ae92-eeec-430e-a66a-f22c3ae64a5e
author: rothja
ms.author: jroth
ms.openlocfilehash: 7886a9a6f51c76ed693576ca6f4659f4051d1f20
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741675"
---
# <a name="filtering-values-using-sqllimit-field-and-sqllimit-value-sqlxml-40"></a><span data-ttu-id="1acbe-102">sql:limit-field와 sql:limit-value를 사용하여 값 필터링(SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="1acbe-102">Filtering Values Using sql:limit-field and sql:limit-value (SQLXML 4.0)</span></span>
  <span data-ttu-id="1acbe-103">데이터베이스 쿼리를 통해 반환되는 행을 어떤 제한 값을 기준으로 제한할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1acbe-103">You can limit rows that are returned from a database query on the basis of some limiting value.</span></span> <span data-ttu-id="1acbe-104">`sql:limit-field` 및 `sql:limit-value` 주석은 제한 값이 포함된 데이터베이스 열을 식별하고 반환되는 데이터를 필터링하는 데 사용할 특정 제한 값을 지정하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="1acbe-104">The `sql:limit-field` and `sql:limit-value` annotations are used to identify the database column that contains limiting values and to specify a specific limiting value to be used to filter the data returned.</span></span>  
  
 <span data-ttu-id="1acbe-105">`sql:limit-field` 주석은 제한 값이 포함된 열을 식별하는 데 사용되며 매핑되는 각각의 요소나 특성에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1acbe-105">The `sql:limit-field` annotation is used to identify a column that contains a limiting value; it is allowed on each mapped element or attribute.</span></span>  
  
 <span data-ttu-id="1acbe-106">`sql:limit-value` 주석은 `sql:limit-field` 주석에 지정한 열에 제한 값을 지정하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="1acbe-106">The `sql:limit-value` annotation is used to specify the limited value in the column that is specified in the `sql:limit-field` annotation.</span></span> <span data-ttu-id="1acbe-107">`sql:limit-value` 주석은 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="1acbe-107">The `sql:limit-value` annotation is optional.</span></span> <span data-ttu-id="1acbe-108">`sql:limit-value`를 지정하지 않으면 NULL 값이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="1acbe-108">If `sql:limit-value` is not specified, a NULL value is assumed.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1acbe-109">매핑되는 SQL 열이 `sql:limit-field` 형식인 경우에 `real`를 사용하면 SQLXML 4.0에서는 XML 스키마에 지정된 대로 `sql:limit-value`를 지정된 `nvarchar` 값으로 변환합니다.</span><span class="sxs-lookup"><span data-stu-id="1acbe-109">When working with a `sql:limit-field` where the mapped SQL column is of type `real`, SQLXML 4.0 performs conversion on the `sql:limit-value` as specified in XML schemas as an `nvarchar` specified value.</span></span> <span data-ttu-id="1acbe-110">이 경우 공학용 표기법을 사용하여 10진수 제한 값을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1acbe-110">This requires that decimal limit values be specified using full scientific notation.</span></span> <span data-ttu-id="1acbe-111">자세한 내용은 아래 2번 예를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="1acbe-111">For more information, see Example B below.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="1acbe-112">예</span><span class="sxs-lookup"><span data-stu-id="1acbe-112">Examples</span></span>  
 <span data-ttu-id="1acbe-113">이러한 예를 사용하여 작업 예제를 만들려면 다음과 같은 제품이 설치되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1acbe-113">To create working samples using these examples, you need to have the following installed:</span></span>  
  
-   <span data-ttu-id="1acbe-114">Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client</span><span class="sxs-lookup"><span data-stu-id="1acbe-114">Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client</span></span>  
  
-   <span data-ttu-id="1acbe-115">MDAC 2.6 이상</span><span class="sxs-lookup"><span data-stu-id="1acbe-115">MDAC 2.6 or later</span></span>  
  
 <span data-ttu-id="1acbe-116">아래의 예에서는 템플릿을 사용하여 매핑 XSD 스키마를 기준으로 XPath 쿼리를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="1acbe-116">In these examples, templates are used to specify XPath queries against the mapping XSD schema.</span></span>  
  
### <a name="a-limiting-the-customer-addresses-returned-to-a-specific-address-type"></a><span data-ttu-id="1acbe-117">A.</span><span class="sxs-lookup"><span data-stu-id="1acbe-117">A.</span></span> <span data-ttu-id="1acbe-118">고객 주소를 제한하여 특정 주소 형식만 반환</span><span class="sxs-lookup"><span data-stu-id="1acbe-118">Limiting the customer addresses returned to a specific address type</span></span>  
 <span data-ttu-id="1acbe-119">이 예에서 데이터베이스에는 다음과 같은 두 개의 테이블이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1acbe-119">In this example, a database contains two tables:</span></span>  
  
-   <span data-ttu-id="1acbe-120">Customer (CustomerID, CompanyName)</span><span class="sxs-lookup"><span data-stu-id="1acbe-120">Customer (CustomerID, CompanyName)</span></span>  
  
-   <span data-ttu-id="1acbe-121">Addresses (CustomerID, AddressType, StreetAddress)</span><span class="sxs-lookup"><span data-stu-id="1acbe-121">Addresses (CustomerID, AddressType, StreetAddress)</span></span>  
  
 <span data-ttu-id="1acbe-122">고객에 대해 배달 주소 및/또는 요금 청구서 주소가 존재할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1acbe-122">A customer can have a shipping address and/or a billing address.</span></span> <span data-ttu-id="1acbe-123">AddressType 열의 값은 Shipping과 Billing입니다.</span><span class="sxs-lookup"><span data-stu-id="1acbe-123">The AddressType column values are Shipping and Billing.</span></span>  
  
 <span data-ttu-id="1acbe-124">**ShipTo** Schema 특성이 주소 관계의 StreetAddress 열에 매핑되는 매핑 스키마입니다.</span><span class="sxs-lookup"><span data-stu-id="1acbe-124">This is the mapping schema in which the **ShipTo** schema attribute maps to the StreetAddress column in the Addresses relation.</span></span> <span data-ttu-id="1acbe-125">`sql:limit-field` 및 `sql:limit-value` 주석을 지정하면 이 특성에 대해 배달 주소만 반환되도록 제한할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1acbe-125">The values that are returned for this attribute are limited to only shipping addresses by specifying the `sql:limit-field` and `sql:limit-value` annotations.</span></span> <span data-ttu-id="1acbe-126">마찬가지로 **BillTo** 스키마 특성은 고객의 청구 주소만 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="1acbe-126">Similarly, the **BillTo** schema attribute returns only the billing address of a customer.</span></span>  
  
 <span data-ttu-id="1acbe-127">스키마는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="1acbe-127">This is the schema:</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
<xsd:annotation>  
  <xsd:appinfo>  
    <sql:relationship name="CustAddr"  
        parent="Customer"  
        parent-key="CustomerID"  
        child="Addresses"  
        child-key="CustomerID" />  
  </xsd:appinfo>  
</xsd:annotation>  
  
  <xsd:element name="Customer" sql:relation="Customer" >  
   <xsd:complexType>  
        <xsd:sequence>  
        <xsd:element name="BillTo"   
                       type="xsd:string"   
                       sql:relation="Addresses"   
                       sql:field="StreetAddress"  
                       sql:limit-field="AddressType"  
                       sql:limit-value="billing"  
                       sql:relationship="CustAddr" >  
        </xsd:element>  
        <xsd:element name="ShipTo"   
                       type="xsd:string"   
                       sql:relation="Addresses"   
                       sql:field="StreetAddress"  
                       sql:limit-field="AddressType"  
                       sql:limit-value="shipping"  
                       sql:relationship="CustAddr" >  
        </xsd:element>  
        </xsd:sequence>  
        <xsd:attribute name="CustomerID"   type="xsd:int" />   
        <xsd:attribute name="CompanyName"  type="xsd:string" />  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a><span data-ttu-id="1acbe-128">스키마에 대해 예제 XPath 쿼리를 테스트하려면</span><span class="sxs-lookup"><span data-stu-id="1acbe-128">To test a sample XPath query against the schema</span></span>  
  
1.  <span data-ttu-id="1acbe-129">**Tempdb** 데이터베이스에 두 개의 테이블을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="1acbe-129">Create two tables in the **tempdb** database:</span></span>  
  
    ```  
    USE tempdb  
    CREATE TABLE Customer (CustomerID int primary key,   
                           CompanyName varchar(30))  
    CREATE TABLE Addresses(CustomerID int,   
                           StreetAddress varchar(50),  
                           AddressType varchar(10))  
    ```  
  
2.  <span data-ttu-id="1acbe-130">예제 데이터를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="1acbe-130">Add the sample data:</span></span>  
  
    ```  
    INSERT INTO Customer values (1, 'Company A')  
    INSERT INTO Customer values (2, 'Company B')  
  
    INSERT INTO Addresses values  
               (1, 'Obere Str. 57 Berlin', 'billing')  
    INSERT INTO Addresses values  
               (1, 'Avda. de la Constituci??n 2222 M??xico D.F.', 'shipping')  
    INSERT INTO Addresses values  
               (2, '120 Hanover Sq., London', 'billing')  
    INSERT INTO Addresses values  
               (2, 'Forsterstr. 57, Mannheim', 'shipping')  
    ```  
  
3.  <span data-ttu-id="1acbe-131">위 스키마 코드를 복사한 후 텍스트 파일에 붙여넣습니다.</span><span class="sxs-lookup"><span data-stu-id="1acbe-131">Copy the schema code above and paste it into a text file.</span></span> <span data-ttu-id="1acbe-132">파일을 LimitFieldValue.xml로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="1acbe-132">Save the file as LimitFieldValue.xml.</span></span>  
  
4.  <span data-ttu-id="1acbe-133">다음 템플릿(LimitFieldValueT.xml)을 만들고 이전 단계에서 스키마(LimitFieldValue.xml)를 저장한 것과 같은 디렉터리에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="1acbe-133">Create the following template (LimitFieldValueT.xml), and save it in the same where you saved the schema (LimitFieldValue.xml) in the previous step:</span></span>  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
        <sql:xpath-query mapping-schema="LimitFieldValue.xml">  
            /Customer  
        </sql:xpath-query>  
    </ROOT>  
    ```  
  
     <span data-ttu-id="1acbe-134">매핑 스키마(LimitFieldValue.xml)에 대해 지정된 디렉터리 경로는 템플릿이 저장된 디렉터리에 상대적입니다.</span><span class="sxs-lookup"><span data-stu-id="1acbe-134">The directory path specified for the mapping schema (LimitFieldValue.xml) is relative to the directory where the template is saved.</span></span> <span data-ttu-id="1acbe-135">또한 다음과 같이 절대 경로를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1acbe-135">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\MyDir\LimitFieldValue.xml"  
    ```  
  
5.  <span data-ttu-id="1acbe-136">SQLXML 4.0 테스트 스크립트(Sqlxml4test.vbs)를 만든 다음 이 스크립트를 사용하여 템플릿을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="1acbe-136">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="1acbe-137">자세한 내용은 [ADO를 사용 하 여 SQLXML 쿼리 실행](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1acbe-137">For more information, see [Using ADO to Execute SQLXML Queries](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="1acbe-138">다음은 결과입니다.</span><span class="sxs-lookup"><span data-stu-id="1acbe-138">This is the result:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">   
  <Customer CustomerID="1" CompanyName="Company A">   
     <BillTo>Obere Str. 57 Berlin</BillTo>   
     <ShipTo>Avda. de la Constituci??n 2222 M??xico D.F.</ShipTo>   
  </Customer>   
  <Customer CustomerID="2" CompanyName="Company B">   
     <BillTo>120 Hanover Sq., London</BillTo>   
     <ShipTo>Forsterstr. 57, Mannheim</ShipTo>   
   </Customer>   
</ROOT>  
```  
  
### <a name="b-limiting-results-based-on-a-discount-value-of-type-real-data"></a><span data-ttu-id="1acbe-139">B.</span><span class="sxs-lookup"><span data-stu-id="1acbe-139">B.</span></span> <span data-ttu-id="1acbe-140">Real 데이터 형식의 할인 값을 기준으로 결과 제한</span><span class="sxs-lookup"><span data-stu-id="1acbe-140">Limiting results based on a discount value of type real data</span></span>  
 <span data-ttu-id="1acbe-141">이 예에서 데이터베이스에는 다음과 같은 두 개의 테이블이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1acbe-141">In this example, a database contains two tables:</span></span>  
  
-   <span data-ttu-id="1acbe-142">Orders (OrderID)</span><span class="sxs-lookup"><span data-stu-id="1acbe-142">Orders (OrderID)</span></span>  
  
-   <span data-ttu-id="1acbe-143">OrderDetails (OrderID, ProductID, UnitPrice, Quantity, Price, Discount)</span><span class="sxs-lookup"><span data-stu-id="1acbe-143">OrderDetails (OrderID, ProductID, UnitPrice, Quantity, Price, Discount)</span></span>  
  
 <span data-ttu-id="1acbe-144">이는 주문 정보의 **orderid** 특성이 주문 관계의 orderid 열에 매핑되는 매핑 스키마입니다.</span><span class="sxs-lookup"><span data-stu-id="1acbe-144">This is the mapping schema in which the **OrderID** attribute on the order details maps to the OrderID column in the orders relation.</span></span> <span data-ttu-id="1acbe-145">이 특성에 대해 반환 되는 값은 및 주석을 사용 하는 **할인율** 에 지정 된 대로 2.0000000 e-001 (0.2) 값을 가진 값 으로만 제한 됩니다 `sql:limit-field` `sql:limit-value` .</span><span class="sxs-lookup"><span data-stu-id="1acbe-145">The values that are returned for this attribute are limited to only those that have a value of 2.0000000e-001 (0.2) as specified for the **Discount** attribute using the `sql:limit-field` and `sql:limit-value` annotations.</span></span>  
  
 <span data-ttu-id="1acbe-146">스키마는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="1acbe-146">This is the schema:</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:annotation>  
   <xsd:appinfo>  
    <sql:relationship name="OrderOrderDetails"  
        parent="Orders"  
        parent-key="OrderID"  
        child="OrderDetails"  
        child-key="OrderID" />  
   </xsd:appinfo>  
  </xsd:annotation>  
  <xsd:element name="root" sql:is-constant="1">  
   <xsd:complexType>  
     <xsd:sequence>  
       <xsd:element name="Order" sql:relation="Orders" >  
          <xsd:complexType>  
             <xsd:sequence>  
                <xsd:element name="orderDetail"   
                       sql:relation="OrderDetails"   
                       sql:limit-field="Discount"                       sql:limit-value="2.0000000e-001"  
                       sql:relationship="OrderOrderDetails">  
                   <xsd:complexType>  
                     <xsd:attribute name="OrderID"   />   
                     <xsd:attribute name="ProductID" />   
                     <xsd:attribute name="Discount"  />   
                     <xsd:attribute name="Quantity"  />   
                     <xsd:attribute name="UnitPrice" />   
                   </xsd:complexType>  
                </xsd:element>  
            </xsd:sequence>  
           <xsd:attribute name="OrderID"/>   
          </xsd:complexType>  
       </xsd:element>  
     </xsd:sequence>  
   </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a><span data-ttu-id="1acbe-147">스키마에 대해 예제 XPath 쿼리를 테스트하려면</span><span class="sxs-lookup"><span data-stu-id="1acbe-147">To test a sample XPath query against the schema</span></span>  
  
1.  <span data-ttu-id="1acbe-148">**Tempdb** 데이터베이스에 두 개의 테이블을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="1acbe-148">Create two tables in the **tempdb** database:</span></span>  
  
    ```  
    USE tempdb  
    CREATE TABLE Orders ([OrderID] int NOT NULL ) ON [PRIMARY]  
    ALTER TABLE Orders WITH NOCHECK ADD   
    CONSTRAINT [PK_Orders] PRIMARY KEY  CLUSTERED (  
       [OrderID]  
     )  ON [PRIMARY]   
    CREATE TABLE [OrderDetails] (  
       [OrderID] int NOT NULL ,  
       [ProductID] int NOT NULL ,  
       [UnitPrice] money NULL ,  
       [Quantity] smallint NOT NULL ,  
       [Discount] real NOT NULL   
    ) ON [PRIMARY]  
    ```  
  
2.  <span data-ttu-id="1acbe-149">예제 데이터를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="1acbe-149">Add the sample data:</span></span>  
  
    ```  
    INSERT INTO Orders ([OrderID]) values (10248)  
    INSERT INTO Orders ([OrderID]) values (10250)  
    INSERT INTO Orders ([OrderID]) values (10251)  
    INSERT INTO Orders ([OrderID]) values (10257)  
    INSERT INTO Orders ([OrderID]) values (10258)  
    INSERT INTO [OrderDetails] ([OrderID],[ProductID],[UnitPrice],[Quantity],[Discount]) values (10248,11,14,12,0)  
    INSERT INTO [OrderDetails] ([OrderID],[ProductID],[UnitPrice],[Quantity],[Discount]) values (10250,51,42.4,35,0.15)  
    INSERT INTO [OrderDetails] ([OrderID],[ProductID],[UnitPrice],[Quantity],[Discount]) values (10251,22,16.8,6,0.05)  
    INSERT INTO [OrderDetails] ([OrderID],[ProductID],[UnitPrice],[Quantity],[Discount]) values (10257,77,10.4,15,0)  
    INSERT INTO [OrderDetails] ([OrderID],[ProductID],[UnitPrice],[Quantity],[Discount]) values (10258,2,15.2,50,0.2)  
    ```  
  
3.  <span data-ttu-id="1acbe-150">디렉터리에 스키마(LimitFieldValue.xml)를 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="1acbe-150">Save the schema (LimitFieldValue.xml) in a directory.</span></span>  
  
4.  <span data-ttu-id="1acbe-151">다음 테스트 스크립트(TestQuery.vbs)를 만들어 MyServer를 현재 사용 중인 SQL Server 컴퓨터의 이름으로 수정한 다음 이전 단계에서 스키마를 저장한 것과 같은 디렉터리에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="1acbe-151">Create the following test script (TestQuery.vbs), modify MyServer to the name of your SQL Server computer and save it in the same directory as you used in the previous step to save the schema:</span></span>  
  
    ```  
    Set conn = CreateObject("ADODB.Connection")  
    conn.Open "Provider=SQLOLEDB;Data Source=MyServer;Database=tempdb;Integrated Security=SSPI"  
    conn.Properties("SQLXML Version") = "sqlxml.4.0"   
    Set cmd = CreateObject("ADODB.Command")  
    Set stm = CreateObject("ADODB.Stream")  
    Set cmd.ActiveConnection = conn  
    stm.open  
    result ="none"  
    strXPathQuery="/root"  
    DBGUID_XPATH = "{EC2A4293-E898-11D2-B1B7-00C04F680C56}"  
    cmd.Dialect = DBGUID_XPATH  
    cmd.CommandText = strXPathQuery  
    cmd.Properties("Mapping schema") = "LimitFieldReal.xml"  
    cmd.Properties("Output Stream").Value = stm  
    cmd.Properties("Output Encoding") = "utf-8"  
    WScript.Echo "executing for xml query"  
    On Error Resume Next  
    cmd.Execute , ,1024  
    if err then  
    Wscript.Echo err.description  
    Wscript.Echo err.Number  
    Wscript.Echo err.source  
    On Error GoTo 0  
    else  
    stm.Position = 0  
    result  = stm.ReadText  
    end if  
    WScript.Echo result  
    Wscript.Echo "done"  
    ```  
  
5.  <span data-ttu-id="1acbe-152">Windows 탐색기에서 TestQuery.vbs 파일을 클릭하여 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="1acbe-152">Execute the TestQuery.vbs file by clicking on it in Windows Explorer.</span></span>  
  
     <span data-ttu-id="1acbe-153">다음은 결과입니다.</span><span class="sxs-lookup"><span data-stu-id="1acbe-153">This is the result:</span></span>  
  
    ```  
    <root>  
      <Order OrderID="10248"/>  
      <Order OrderID="10250"/>  
      <Order OrderID="10251"/>  
      <Order OrderID="10257"/>  
      <Order OrderID="10258">  
        <orderDetail OrderID="10258"   
                     ProductID="2"   
                     Discount="0.2"   
                     Quantity="50"/>  
      </Order>  
    </root>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="1acbe-154">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1acbe-154">See Also</span></span>  
 <span data-ttu-id="1acbe-155">[float 및 real &#40;Transact-sql&#41;](/sql/t-sql/data-types/float-and-real-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="1acbe-155">[float and real &#40;Transact-SQL&#41;](/sql/t-sql/data-types/float-and-real-transact-sql) </span></span>  
 <span data-ttu-id="1acbe-156">[nchar 및 nvarchar &#40;Transact-sql&#41;](/sql/t-sql/data-types/nchar-and-nvarchar-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="1acbe-156">[nchar and nvarchar &#40;Transact-SQL&#41;](/sql/t-sql/data-types/nchar-and-nvarchar-transact-sql) </span></span>  
 <span data-ttu-id="1acbe-157">[SQL Server Native Client 설치](../../relational-databases/native-client/applications/installing-sql-server-native-client.md) </span><span class="sxs-lookup"><span data-stu-id="1acbe-157">[Installing SQL Server Native Client](../../relational-databases/native-client/applications/installing-sql-server-native-client.md) </span></span>  
 [<span data-ttu-id="1acbe-158">쿼리에 주석이 추가 된 XSD 스키마 사용 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="1acbe-158">Using Annotated XSD Schemas in Queries &#40;SQLXML 4.0&#41;</span></span>](../../relational-databases/sqlxml/annotated-xsd-schemas/using-annotated-xsd-schemas-in-queries-sqlxml-4-0.md)  
  
  
