---
title: 'Sql: 키-필드를 사용 하 여 키 열 식별 (SQLXML 4.0) | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- nesting XML results
- proper nesting in results [SQLXML]
- sql:key-fields
- XSD schemas [SQLXML], key columns
- identifying key columns [SQLXML]
- annotated XSD schemas, key columns
- key columns [SQLXML]
- relationships [SQLXML], key columns
- hierarchical relationships [SQLXML]
- key-fields annotation
ms.assetid: 1a5ad868-8602-45c4-913d-6fbb837eebb0
author: rothja
ms.author: jroth
ms.openlocfilehash: 0ab12b34874a54bad2e08a96d08ebd0cc994f946
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741664"
---
# <a name="identifying-key-columns-using-sqlkey-fields-sqlxml-40"></a><span data-ttu-id="0697b-102">sql:key-fields(SQLXML 4.0)를 사용하여 키 열 식별</span><span class="sxs-lookup"><span data-stu-id="0697b-102">Identifying Key Columns Using sql:key-fields (SQLXML 4.0)</span></span>
  <span data-ttu-id="0697b-103">XSD 스키마에 대해 XPath 쿼리가 지정된 경우 결과에서 올바른 중첩을 얻으려면 대부분 키 정보가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="0697b-103">When an XPath query is specified against an XSD schema, key information is required in most cases to obtain proper nesting in the result.</span></span> <span data-ttu-id="0697b-104">`sql:key-fields` 주석을 지정하면 적절한 계층이 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="0697b-104">Specifying the `sql:key-fields` annotation is a way of ensuring that the appropriate hierarchy is generated.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0697b-105">올바른 중첩을 얻으려면 테이블에 매핑되는 요소에 대해 `sql:key-fields`를 지정하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="0697b-105">To ensure proper nesting, it is recommended that you specify `sql:key-fields` for elements that map to tables.</span></span> <span data-ttu-id="0697b-106">기본 결과 집합의 순서가 생성되는 XML에 중요합니다.</span><span class="sxs-lookup"><span data-stu-id="0697b-106">The XML produced is sensitive to the ordering of the underlying result set.</span></span> <span data-ttu-id="0697b-107">`sql:key-fields`를 지정하지 않으면 잘못된 형식의 XML이 생성될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0697b-107">If `sql:key-fields` is not specified, the XML generated might not be formed properly.</span></span>  
  
 <span data-ttu-id="0697b-108">`sql:key-fields` 값은 관계의 행을 고유하게 식별하는 열을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="0697b-108">The value of `sql:key-fields` identifies the column(s) that uniquely identify the rows in the relation.</span></span> <span data-ttu-id="0697b-109">행을 고유하게 식별하는 데 둘 이상의 열이 필요한 경우 열 값이 공백으로 구분됩니다.</span><span class="sxs-lookup"><span data-stu-id="0697b-109">If more than one column is required to uniquely identify a row, the column values are delimited by spaces.</span></span>  
  
 <span data-ttu-id="0697b-110">요소가 `sql:key-fields` **\<sql:relationship>** 요소와 자식 요소 사이에 정의 된를 포함 하지만 부모 요소에 지정 된 테이블의 기본 키를 제공 하지 않는 경우 주석을 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0697b-110">You must use the `sql:key-fields` annotation when an element contains a **\<sql:relationship>** that is defined between the element and a child element but does not provide the primary key of the table that is specified in the parent element.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="0697b-111">예</span><span class="sxs-lookup"><span data-stu-id="0697b-111">Examples</span></span>  
 <span data-ttu-id="0697b-112">다음 예를 사용하여 작업 예제를 만들려면 특정 요구 사항이 충족되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0697b-112">To create working samples using the following examples, you must meet certain requirements.</span></span> <span data-ttu-id="0697b-113">자세한 내용은 [SQLXML 예를 실행 하기 위한 요구 사항](../sqlxml/requirements-for-running-sqlxml-examples.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="0697b-113">For more information, see [Requirements for Running SQLXML Examples](../sqlxml/requirements-for-running-sqlxml-examples.md).</span></span>  
  
### <a name="a-producing-the-appropriate-nesting-when-sqlrelationship-does-not-provide-sufficient-information"></a><span data-ttu-id="0697b-114">A.</span><span class="sxs-lookup"><span data-stu-id="0697b-114">A.</span></span> <span data-ttu-id="0697b-115">\<sql:relationship>에서 충분 한 정보를 제공 하지 않을 때 적절 한 중첩을 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="0697b-115">Producing the appropriate nesting when \<sql:relationship> does not provide sufficient information</span></span>  
 <span data-ttu-id="0697b-116">이 예에서는 `sql:key-fields`를 지정해야 하는 위치를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="0697b-116">This example shows where `sql:key-fields` must be specified.</span></span>  
  
 <span data-ttu-id="0697b-117">다음과 같은 스키마를 살펴 보십시오.</span><span class="sxs-lookup"><span data-stu-id="0697b-117">Consider the following schema.</span></span> <span data-ttu-id="0697b-118">스키마는 요소가 부모인 요소와 요소가 자식인 요소 간의 계층을 지정 합니다 **\<Order>** **\<Customer>** **\<Order>** **\<Customer>** .</span><span class="sxs-lookup"><span data-stu-id="0697b-118">The schema specifies a hierarchy between the **\<Order>** and **\<Customer>** elements in which the **\<Order>** element is the parent and the **\<Customer>** element is a child.</span></span>  
  
 <span data-ttu-id="0697b-119">**\<sql:relationship>** 태그는 부모-자식 관계를 지정 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0697b-119">The **\<sql:relationship>** tag is used to specify the parent-child relationship.</span></span> <span data-ttu-id="0697b-120">Sales.SalesOrderHeader 테이블의 CustomerID를 Sales.Customer 테이블의 CustomerID 자식 키를 참조하는 부모 키로 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="0697b-120">It identifies CustomerID in the Sales.SalesOrderHeader table as the parent key that refers to the CustomerID child key in the Sales.Customer table.</span></span> <span data-ttu-id="0697b-121">에서 제공 하는 정보는 **\<sql:relationship>** 부모 테이블 (SalesOrderHeader)에서 행을 고유 하 게 식별 하는 데 충분 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0697b-121">The information provided in **\<sql:relationship>** is not sufficient to uniquely identify rows in the parent table (Sales.SalesOrderHeader).</span></span> <span data-ttu-id="0697b-122">따라서 `sql:key-fields` 주석이 없으면 부정확한 계층이 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="0697b-122">Therefore, without the `sql:key-fields` annotation, the hierarchy that is generated is inaccurate.</span></span>  
  
 <span data-ttu-id="0697b-123">에서 지정 된를 사용 하 여 `sql:key-fields` **\<Order>** 주석은 부모 (SalesOrderHeader 테이블)의 행을 고유 하 게 식별 하 고 해당 자식 요소는 부모 아래에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0697b-123">With `sql:key-fields` specified on **\<Order>**, the annotation uniquely identifies the rows in the parent (Sales.SalesOrderHeader table), and its child elements appear below its parent.</span></span>  
  
 <span data-ttu-id="0697b-124">스키마는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="0697b-124">This is the schema:</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
<xsd:annotation>  
  <xsd:appinfo>  
    <sql:relationship name="OrdCust"  
        parent="Sales.SalesOrderHeader"  
        parent-key="CustomerID"  
        child="Sales.Customer"  
        child-key="CustomerID" />  
  </xsd:appinfo>  
</xsd:annotation>  
  <xsd:element name="Order" sql:relation="Sales.SalesOrderHeader"   
               sql:key-fields="SalesOrderID">  
   <xsd:complexType>  
     <xsd:sequence>  
     <xsd:element name="Customer" sql:relation="Sales.Customer"   
                       sql:relationship="OrdCust"  >  
       <xsd:complexType>  
         <xsd:attribute name="CustID" sql:field="CustomerID" />  
         <xsd:attribute name="SoldBy" sql:field="SalesPersonID" />  
       </xsd:complexType>  
     </xsd:element>  
     </xsd:sequence>  
     <xsd:attribute name="SalesOrderID" type="xsd:integer" />  
     <xsd:attribute name= "CustomerID" type="xsd:string" />  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
##### <a name="to-create-a-working-sample-of-this-schema"></a><span data-ttu-id="0697b-125">이 스키마의 작업 예제를 만들려면</span><span class="sxs-lookup"><span data-stu-id="0697b-125">To create a working sample of this schema</span></span>  
  
1.  <span data-ttu-id="0697b-126">위 스키마 코드를 복사한 후 텍스트 파일에 붙여넣습니다.</span><span class="sxs-lookup"><span data-stu-id="0697b-126">Copy the schema code above and paste it into a text file.</span></span> <span data-ttu-id="0697b-127">파일을 KeyFields1.xml로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="0697b-127">Save the file as KeyFields1.xml.</span></span>  
  
2.  <span data-ttu-id="0697b-128">다음 템플릿을 복사한 후 텍스트 파일에 붙여넣습니다.</span><span class="sxs-lookup"><span data-stu-id="0697b-128">Copy the following template and paste it into a text file.</span></span> <span data-ttu-id="0697b-129">KeyFields1.xml을 저장한 디렉터리와 같은 디렉터리에 KeyFields1T.xml로 파일을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="0697b-129">Save the file as KeyFields1T.xml in the same directory where you saved KeyFields1.xml.</span></span> <span data-ttu-id="0697b-130">템플릿의 XPath 쿼리는 **\<Order>** CustomerID가 3 보다 작은 모든 요소를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="0697b-130">The XPath query in the template returns all the **\<Order>** elements with a CustomerID of less than 3.</span></span>  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
        <sql:xpath-query mapping-schema="KeyFields1.xml">  
            /Order[@CustomerID < 3]  
        </sql:xpath-query>  
    </ROOT>  
    ```  
  
     <span data-ttu-id="0697b-131">매핑 스키마(KeyFields1.xml)에 대해 지정된 디렉터리 경로는 템플릿이 저장된 디렉터리에 상대적입니다.</span><span class="sxs-lookup"><span data-stu-id="0697b-131">The directory path specified for the mapping schema (KeyFields1.xml) is relative to the directory where the template is saved.</span></span> <span data-ttu-id="0697b-132">또한 다음과 같이 절대 경로를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0697b-132">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\MyDir\KeyFields1.xml"  
    ```  
  
3.  <span data-ttu-id="0697b-133">SQLXML 4.0 테스트 스크립트(Sqlxml4test.vbs)를 만든 다음 이 스크립트를 사용하여 템플릿을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="0697b-133">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="0697b-134">자세한 내용은 [ADO를 사용 하 여 SQLXML 쿼리 실행](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="0697b-134">For more information, see [Using ADO to Execute SQLXML Queries](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="0697b-135">다음은 결과 집합의 일부입니다.</span><span class="sxs-lookup"><span data-stu-id="0697b-135">This is the partial result set:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
    <Order SalesOrderID="43860" CustomerID="1">  
       <Customer CustID="1" SoldBy="280"/>  
    </Order>  
    <Order SalesOrderID="44501" CustomerID="1">  
       <Customer CustID="1" SoldBy="280"/>  
    </Order>  
    <Order SalesOrderID="45283" CustomerID="1">  
       <Customer CustID="1" SoldBy="280"/>  
    </Order>  
    .....  
</ROOT>  
```  
  
### <a name="b-specifying-sqlkey-fields-to-produce-proper-nesting-in-the-result"></a><span data-ttu-id="0697b-136">B.</span><span class="sxs-lookup"><span data-stu-id="0697b-136">B.</span></span> <span data-ttu-id="0697b-137">sql:key-fields를 지정하여 결과에서 올바른 중첩 생성</span><span class="sxs-lookup"><span data-stu-id="0697b-137">Specifying sql:key-fields to produce proper nesting in the result</span></span>  
 <span data-ttu-id="0697b-138">다음 스키마에는를 사용 하 여 지정 된 계층이 없습니다 **\<sql:relationship>** .</span><span class="sxs-lookup"><span data-stu-id="0697b-138">In the following schema, there is no hierarchy specified using **\<sql:relationship>**.</span></span> <span data-ttu-id="0697b-139">이 스키마에서는 HumanResources.Employee 테이블의 직원을 고유하게 식별하기 위해 `sql:key-fields` 주석을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0697b-139">The schema still requires specifying the `sql:key-fields` annotation to uniquely identify employees in the HumanResources.Employee table.</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:element name="HumanResources.Employee" sql:key-fields="EmployeeID" >  
   <xsd:complexType>  
     <xsd:sequence>  
        <xsd:element name="Title">  
          <xsd:complexType>  
            <xsd:simpleContent>  
              <xsd:extension base="xsd:string">  
                 <xsd:attribute name="EmployeeID" type="xsd:integer" />  
              </xsd:extension>  
            </xsd:simpleContent>  
          </xsd:complexType>  
        </xsd:element>  
     </xsd:sequence>  
   </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
##### <a name="to-create-a-working-sample-of-this-schema"></a><span data-ttu-id="0697b-140">이 스키마의 작업 예제를 만들려면</span><span class="sxs-lookup"><span data-stu-id="0697b-140">To create a working sample of this schema</span></span>  
  
1.  <span data-ttu-id="0697b-141">위 스키마 코드를 복사한 후 텍스트 파일에 붙여넣습니다.</span><span class="sxs-lookup"><span data-stu-id="0697b-141">Copy the schema code above and paste it into a text file.</span></span> <span data-ttu-id="0697b-142">파일을 KeyFields2.xml로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="0697b-142">Save the file as KeyFields2.xml.</span></span>  
  
2.  <span data-ttu-id="0697b-143">다음 템플릿을 복사한 후 텍스트 파일에 붙여넣습니다.</span><span class="sxs-lookup"><span data-stu-id="0697b-143">Copy the following template and paste it into a text file.</span></span> <span data-ttu-id="0697b-144">KeyFields2.xml을 저장한 디렉터리와 같은 디렉터리에 KeyFields2T.xml로 파일을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="0697b-144">Save the file as KeyFields2T.xml in the same directory where you saved KeyFields2.xml.</span></span> <span data-ttu-id="0697b-145">템플릿의 XPath 쿼리는 모든 요소를 반환 합니다 **\<HumanResources.Employee>** .</span><span class="sxs-lookup"><span data-stu-id="0697b-145">The XPath query in the template returns all the **\<HumanResources.Employee>** elements:</span></span>  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:xpath-query mapping-schema="KeyFields2.xml">  
        /HumanResources.Employee  
      </sql:xpath-query>  
    </ROOT>  
    ```  
  
     <span data-ttu-id="0697b-146">매핑 스키마(KeyFields2.xml)에 대해 지정된 디렉터리 경로는 템플릿이 저장된 디렉터리에 상대적입니다.</span><span class="sxs-lookup"><span data-stu-id="0697b-146">The directory path specified for the mapping schema (KeyFields2.xml) is relative to the directory where the template is saved.</span></span> <span data-ttu-id="0697b-147">또한 다음과 같이 절대 경로를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0697b-147">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\MyDir\KeyFields2.xml"  
    ```  
  
3.  <span data-ttu-id="0697b-148">SQLXML 4.0 테스트 스크립트(Sqlxml4test.vbs)를 만든 다음 이 스크립트를 사용하여 템플릿을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="0697b-148">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="0697b-149">자세한 내용은 [ADO를 사용 하 여 SQLXML 쿼리 실행](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="0697b-149">For more information, see [Using ADO to Execute SQLXML Queries](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="0697b-150">다음은 결과입니다.</span><span class="sxs-lookup"><span data-stu-id="0697b-150">This is the result:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <HumanResources.Employee>  
    <Title EmployeeID="1">Production Technician - WC60</Title>   
  </HumanResources.Employee>  
  <HumanResources.Employee>  
    <Title EmployeeID="2">Marketing Assistant</Title>   
  </HumanResources.Employee>  
  <HumanResources.Employee>  
    <Title EmployeeID="3">Engineering Manager</Title>   
  </HumanResources.Employee>  
  ...  
</ROOT>  
```  
  
  
