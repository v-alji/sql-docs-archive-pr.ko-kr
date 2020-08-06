---
title: 'Sql: relationship을 사용 하 여 관계 지정 (SQLXML 4.0) | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- IDREFS relationships [SQLXML]
- parent attribute [SQLXML]
- element relationships [SQLXML]
- multiple element relationships
- attribute relationships [SQLXML]
- sql:relationship
- relationship chains [SQLXML]
- IDREF relationships [SQLXML]
- parent-child relationships [SQLXML]
- relationship annotation
- XSD schemas [SQLXML], relationships
- annotated XSD schemas, relationships
- relationships [SQLXML], specifying
- unnamed relationships
- ID relationships [SQLXML]
- hierarchical relationships [SQLXML]
- named relationships [SQLXML]
ms.assetid: 98820afa-74e1-4e62-b336-6111a3dede4c
author: rothja
ms.author: jroth
ms.openlocfilehash: 42c703de9d564580eb0baa1349a45b193109c87a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650895"
---
# <a name="specifying-relationships-using-sqlrelationship-sqlxml-40"></a><span data-ttu-id="d9b6d-102">sql:relationship을 사용하여 관계 지정(SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="d9b6d-102">Specifying Relationships Using sql:relationship (SQLXML 4.0)</span></span>
  <span data-ttu-id="d9b6d-103">XML 문서의 요소는 서로 관련될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d9b6d-103">The elements in an XML document can be related.</span></span> <span data-ttu-id="d9b6d-104">이러한 요소는 계층적으로 중첩될 수 있으며 요소 간에 ID, IDREF 또는 IDREFS 관계가 지정될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d9b6d-104">The elements can be nested hierarchically, and ID, IDREF, or IDREFS relationships can be specified between the elements.</span></span>  
  
 <span data-ttu-id="d9b6d-105">예를 들어 XSD 스키마에서 **\<Customer>** 요소는 **\<Order>** 자식 요소를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="d9b6d-105">For example, in an XSD schema, a **\<Customer>** element contains **\<Order>** child elements.</span></span> <span data-ttu-id="d9b6d-106">스키마가 AdventureWorks 데이터베이스에 매핑될 때 **\<Customer>** 요소는 sales. Customer 테이블에 매핑되고 **\<Order>** 요소는 SalesOrderHeader 테이블에 매핑됩니다.</span><span class="sxs-lookup"><span data-stu-id="d9b6d-106">When the schema is mapped to the AdventureWorks database, the **\<Customer>** element maps to the Sales.Customer table and the **\<Order>** element maps to the Sales.SalesOrderHeader table.</span></span> <span data-ttu-id="d9b6d-107">이러한 기본 테이블인 Sales.Customer와 Sales.SalesOrderHeader는 고객 주문과 관련하여 서로 관련되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d9b6d-107">These underlying tables, Sales.Customer and Sales.SalesOrderHeader, are related because customers place orders.</span></span> <span data-ttu-id="d9b6d-108">Sales.SalesOrderHeader 테이블의 CustomerID는 Sales.Customer 테이블의 CustomerID 기본 키를 참조하는 외래 키입니다.</span><span class="sxs-lookup"><span data-stu-id="d9b6d-108">The CustomerID in the Sales.SalesOrderHeader table is a foreign key referring to the CustomerID primary key in the Sales.Customer table.</span></span> <span data-ttu-id="d9b6d-109">`sql:relationship` 주석을 사용하면 매핑 스키마 요소 간에 이러한 관계를 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d9b6d-109">You can establish these relationships among mapping schema elements by using the `sql:relationship` annotation.</span></span>  
  
 <span data-ttu-id="d9b6d-110">주석이 추가된 XSD 스키마에서 `sql:relationship` 주석은 요소가 매핑되는 기본 테이블 간의 기본 키 및 외래 키 관계를 기반으로 스키마 요소를 계층적으로 중첩하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="d9b6d-110">In the annotated XSD schema, the `sql:relationship` annotation is used to nest the schema elements hierarchically, on the basis of primary key and foreign key relationships among the underlying tables to which the elements map.</span></span> <span data-ttu-id="d9b6d-111">`sql:relationship` 주석을 지정할 때는 다음을 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d9b6d-111">In specifying the `sql:relationship` annotation, you must identify the following:</span></span>  
  
-   <span data-ttu-id="d9b6d-112">부모 테이블(Sales.Customer)과 자식 테이블(Sales.SalesOrderHeader).</span><span class="sxs-lookup"><span data-stu-id="d9b6d-112">The parent table (Sales.Customer) and the child table (Sales.SalesOrderHeader).</span></span>  
  
-   <span data-ttu-id="d9b6d-113">부모 테이블과 자식 테이블 간의 관계를 구성하는 열(예:</span><span class="sxs-lookup"><span data-stu-id="d9b6d-113">The column or columns that compose the relationship between the parent and child tables.</span></span> <span data-ttu-id="d9b6d-114">부모 테이블과 자식 테이블에 모두 표시되는 CustomerID 열)</span><span class="sxs-lookup"><span data-stu-id="d9b6d-114">For example, the CustomerID column, which appears in both the parent and child tables.</span></span>  
  
 <span data-ttu-id="d9b6d-115">이 정보는 적절한 계층을 생성하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="d9b6d-115">This information is used to generate the proper hierarchy.</span></span>  
  
 <span data-ttu-id="d9b6d-116">테이블 이름과 필요한 조인 정보를 제공하려면 다음 특성을 `sql:relationship` 주석에 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d9b6d-116">To provide the table names and the necessary join information, the following attributes are specified on the `sql:relationship` annotation.</span></span> <span data-ttu-id="d9b6d-117">이러한 특성은 요소에만 사용할 수 **\<sql:relationship>** 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d9b6d-117">These attributes are valid only with the **\<sql:relationship>** element:</span></span>  
  
 <span data-ttu-id="d9b6d-118">**이름**</span><span class="sxs-lookup"><span data-stu-id="d9b6d-118">**Name**</span></span>  
 <span data-ttu-id="d9b6d-119">관계의 고유한 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d9b6d-119">Specifies the unique name of the relationship.</span></span>  
  
 <span data-ttu-id="d9b6d-120">**Parent**</span><span class="sxs-lookup"><span data-stu-id="d9b6d-120">**Parent**</span></span>  
 <span data-ttu-id="d9b6d-121">부모 관계(테이블)를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d9b6d-121">Specifies the parent relation (table).</span></span> <span data-ttu-id="d9b6d-122">이 특성은 옵션입니다. 특성이 지정되지 않으면 문서의 자식 계층에 있는 정보에서 부모 테이블 이름을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="d9b6d-122">This is an optional attribute; if the attribute is not specified, the parent table name is obtained from information in the child hierarchy in the document.</span></span> <span data-ttu-id="d9b6d-123">스키마가 동일 하지만 다른 부모 요소를 사용 하는 두 개의 부모-자식 계층을 지정 하는 경우 **\<sql:relationship>** 에서 부모 특성을 지정 하지 않습니다 **\<sql:relationship>** .</span><span class="sxs-lookup"><span data-stu-id="d9b6d-123">If the schema specifies two parent-child hierarchies that use the same **\<sql:relationship>** but different parent elements, you do not specify the parent attribute in **\<sql:relationship>**.</span></span> <span data-ttu-id="d9b6d-124">이 정보는 스키마의 계층에서 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="d9b6d-124">This information is obtained from the hierarchy in the schema.</span></span>  
  
 <span data-ttu-id="d9b6d-125">**parent-key**</span><span class="sxs-lookup"><span data-stu-id="d9b6d-125">**parent-key**</span></span>  
 <span data-ttu-id="d9b6d-126">부모의 부모 키를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d9b6d-126">Specifies the parent key of the parent.</span></span> <span data-ttu-id="d9b6d-127">부모 키가 여러 열로 구성된 경우 값은 사이에 공백을 두고 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d9b6d-127">If the parent key is composed of multiple columns, values are specified with a space between them.</span></span> <span data-ttu-id="d9b6d-128">여러 열로 구성된 키에 대해 지정된 값과 해당 자식 키에 지정된 값 간에는 위치 매핑이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d9b6d-128">There is a positional mapping between the values that are specified for the multicolumn key and for the corresponding child key.</span></span>  
  
 <span data-ttu-id="d9b6d-129">**자식**</span><span class="sxs-lookup"><span data-stu-id="d9b6d-129">**Child**</span></span>  
 <span data-ttu-id="d9b6d-130">자식 관계(테이블)를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d9b6d-130">Specifies the child relation (table).</span></span>  
  
 <span data-ttu-id="d9b6d-131">**child-key**</span><span class="sxs-lookup"><span data-stu-id="d9b6d-131">**child-key**</span></span>  
 <span data-ttu-id="d9b6d-132">부모의 부모 키를 참조하는 자식의 자식 키를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d9b6d-132">Specifies the child key in the child referring to parent-key in parent.</span></span> <span data-ttu-id="d9b6d-133">자식 키가 여러 특성(열)으로 구성된 경우 자식 키 값은 사이에 공백을 두고 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d9b6d-133">If the child key is composed of multiple attributes (columns), the child-key values are specified with a space between them.</span></span> <span data-ttu-id="d9b6d-134">여러 열로 구성된 키에 대해 지정된 값과 해당 부모 키에 지정된 값 간에는 위치 매핑이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d9b6d-134">There is a positional mapping between the values that are specified for the multicolumn key and for the corresponding parent key.</span></span>  
  
 <span data-ttu-id="d9b6d-135">**Inverse**</span><span class="sxs-lookup"><span data-stu-id="d9b6d-135">**Inverse**</span></span>  
 <span data-ttu-id="d9b6d-136">에 지정 된이 특성 **\<sql:relationship>** 은 updategrams에서 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d9b6d-136">This attribute specified on **\<sql:relationship>** is used by updategrams.</span></span> <span data-ttu-id="d9b6d-137">자세한 내용은 [sql: relationship에 sql: 역 특성 지정](specifying-the-sql-inverse-attribute-on-sql-relationship-sqlxml-4-0.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="d9b6d-137">For more information, see [Specifying the sql:inverse Attribute on sql:relationship](specifying-the-sql-inverse-attribute-on-sql-relationship-sqlxml-4-0.md).</span></span>  
  
 <span data-ttu-id="d9b6d-138">`sql:key-fields` **\<sql:relationship>** 요소와 자식 사이에 정의 된가 있고 부모 요소에 지정 된 테이블의 기본 키를 제공 하지 않는 자식 요소가 포함 된 요소에 주석을 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d9b6d-138">The `sql:key-fields` annotation must be specified in an element that contains a child element, that has a **\<sql:relationship>** defined between the element and the child, and that does not provide the primary key of the table specified in the parent element.</span></span> <span data-ttu-id="d9b6d-139">스키마가을 지정 하지 않은 경우 **\<sql:relationship>** 에도를 지정 `sql:key-fields` 하 여 적절 한 계층을 생성 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d9b6d-139">Even if the schema does not specify **\<sql:relationship>**, you must specify `sql:key-fields` to produce the proper hierarchy.</span></span> <span data-ttu-id="d9b6d-140">자세한 내용은 [sql: 키-필드를 사용 하 여 키 열 식별](identifying-key-columns-using-sql-key-fields-sqlxml-4-0.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="d9b6d-140">For more information, see [Identifying Key Columns by Using sql:key-fields](identifying-key-columns-using-sql-key-fields-sqlxml-4-0.md).</span></span>  
  
 <span data-ttu-id="d9b6d-141">올바른 중첩 결과를 얻으려면 모든 스키마에 `sql:key-fields`를 지정하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="d9b6d-141">To produce proper nesting in the result, it is recommended that `sql:key-fields` are specified in all schemas.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="d9b6d-142">예</span><span class="sxs-lookup"><span data-stu-id="d9b6d-142">Examples</span></span>  
 <span data-ttu-id="d9b6d-143">다음 예를 사용하여 작업 예제를 만들려면 특정 요구 사항이 충족되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d9b6d-143">To create working samples using the following examples, you must meet certain requirements.</span></span> <span data-ttu-id="d9b6d-144">자세한 내용은 [SQLXML 예를 실행 하기 위한 요구 사항](../sqlxml/requirements-for-running-sqlxml-examples.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="d9b6d-144">For more information, see [Requirements for Running SQLXML Examples](../sqlxml/requirements-for-running-sqlxml-examples.md).</span></span>  
  
### <a name="a-specifying-the-sqlrelationship-annotation-on-an-element"></a><span data-ttu-id="d9b6d-145">A.</span><span class="sxs-lookup"><span data-stu-id="d9b6d-145">A.</span></span> <span data-ttu-id="d9b6d-146">요소에 sql:relationship 주석 지정</span><span class="sxs-lookup"><span data-stu-id="d9b6d-146">Specifying the sql:relationship annotation on an element</span></span>  
 <span data-ttu-id="d9b6d-147">주석이 추가 된 다음 XSD 스키마에는 **\<Customer>** 및 요소가 포함 됩니다 **\<Order>** .</span><span class="sxs-lookup"><span data-stu-id="d9b6d-147">The following annotated XSD schema includes **\<Customer>** and **\<Order>** elements.</span></span> <span data-ttu-id="d9b6d-148">요소는 **\<Order>** 요소의 자식 요소입니다 **\<Customer>** .</span><span class="sxs-lookup"><span data-stu-id="d9b6d-148">The **\<Order>** element is a child element of the **\<Customer>** element.</span></span>  
  
 <span data-ttu-id="d9b6d-149">스키마에서 `sql:relationship` 주석은 자식 요소에 지정 됩니다 **\<Order>** .</span><span class="sxs-lookup"><span data-stu-id="d9b6d-149">In the schema, the `sql:relationship` annotation is specified on the **\<Order>** child element.</span></span> <span data-ttu-id="d9b6d-150">관계 자체는 요소에 정의 됩니다 **\<xsd:appinfo>** .</span><span class="sxs-lookup"><span data-stu-id="d9b6d-150">The relationship itself is defined in the **\<xsd:appinfo>** element.</span></span>  
  
 <span data-ttu-id="d9b6d-151">요소는 SalesOrderHeader 테이블의 customerid **\<relationship>** 를 sales. Customer 테이블의 customerid 기본 키를 참조 하는 외래 키로 식별 합니다.</span><span class="sxs-lookup"><span data-stu-id="d9b6d-151">The **\<relationship>** element identifies CustomerID in the Sales.SalesOrderHeader table as a foreign key that refers to the CustomerID primary key in the Sales.Customer table.</span></span> <span data-ttu-id="d9b6d-152">따라서 고객에 게 속한 주문은 해당 요소의 자식 요소로 표시 **\<Customer>** 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d9b6d-152">Therefore, orders that belong to a customer appear as a child element of that **\<Customer>** element.</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
<xsd:annotation>  
  <xsd:appinfo>  
    <sql:relationship name="CustOrders"  
          parent="Sales.Customer"  
          parent-key="CustomerID"  
          child="Sales.SalesOrderHeader"  
          child-key="CustomerID" />  
  </xsd:appinfo>  
</xsd:annotation>  
  
  <xsd:element name="Customer" sql:relation="Sales.Customer" type="CustomerType" />  
   <xsd:complexType name="CustomerType" >  
     <xsd:sequence>  
        <xsd:element name="Order"   
                     sql:relation="Sales.SalesOrderHeader"  
                    sql:relationship="CustOrders" >  
           <xsd:complexType>  
              <xsd:attribute name="SalesOrderID" type="xsd:integer" />  
              <xsd:attribute name="CustomerID" type="xsd:string" />  
           </xsd:complexType>  
        </xsd:element>  
     </xsd:sequence>  
        <xsd:attribute name="CustomerID"   type="xsd:string" />   
    </xsd:complexType>  
  
</xsd:schema>  
```  
  
 <span data-ttu-id="d9b6d-153">앞의 스키마는 명명된 관계를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="d9b6d-153">The previous schema uses a named relationship.</span></span> <span data-ttu-id="d9b6d-154">명명되지 않은 관계도 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d9b6d-154">You can also specify an unnamed relationship.</span></span> <span data-ttu-id="d9b6d-155">결과는 같습니다.</span><span class="sxs-lookup"><span data-stu-id="d9b6d-155">The results are same.</span></span>  
  
 <span data-ttu-id="d9b6d-156">다음은 명명되지 않은 관계가 지정되는 수정된 스키마입니다.</span><span class="sxs-lookup"><span data-stu-id="d9b6d-156">This is the revised schema in which an unnamed relationship is specified:</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  
  <xsd:element name="Customer" sql:relation="Sales.Customer"  type="CustomerType" />  
   <xsd:complexType name="CustomerType" >  
     <xsd:sequence>  
        <xsd:element name="Order"   
                     sql:relation="Sales.SalesOrderHeader">  
           <xsd:annotation>  
            <xsd:appinfo>  
              <sql:relationship   
                parent="Sales.Customer"  
                parent-key="CustomerID"  
                child="Sales.SalesOrderHeader"  
                child-key="CustomerID" />  
            </xsd:appinfo>  
           </xsd:annotation>  
           <xsd:complexType>  
              <xsd:attribute name="SalesOrderID" type="xsd:integer" />  
              <xsd:attribute name="CustomerID" type="xsd:string" />  
           </xsd:complexType>  
        </xsd:element>  
     </xsd:sequence>  
        <xsd:attribute name="CustomerID"   type="xsd:string" />   
    </xsd:complexType>  
  
</xsd:schema>  
```  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a><span data-ttu-id="d9b6d-157">스키마에 대해 예제 XPath 쿼리를 테스트하려면</span><span class="sxs-lookup"><span data-stu-id="d9b6d-157">To test a sample XPath query against the schema</span></span>  
  
1.  <span data-ttu-id="d9b6d-158">위 스키마 코드를 복사한 후 텍스트 파일에 붙여넣습니다.</span><span class="sxs-lookup"><span data-stu-id="d9b6d-158">Copy the schema code above and paste it into a text file.</span></span> <span data-ttu-id="d9b6d-159">파일을 sql-relationship.xml로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="d9b6d-159">Save the file as sql-relationship.xml.</span></span>  
  
2.  <span data-ttu-id="d9b6d-160">다음 템플릿을 복사한 후 텍스트 파일에 붙여넣습니다.</span><span class="sxs-lookup"><span data-stu-id="d9b6d-160">Copy the following template below and paste it into a text file.</span></span> <span data-ttu-id="d9b6d-161">sql-relationship.xml을 저장한 디렉터리에 파일을 sql-relationshipT.xml로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="d9b6d-161">Save the file as sql-relationshipT.xml in the same directory where you saved sql-relationship.xml.</span></span>  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
        <sql:xpath-query mapping-schema="sql-relationship.xml">  
            /Customer[@CustomerID=1]  
        </sql:xpath-query>  
    </ROOT>  
    ```  
  
     <span data-ttu-id="d9b6d-162">매핑 스키마(sql-relationship.xml)에 대해 지정된 디렉터리 경로는 템플릿이 저장된 디렉터리에 대한 상대 경로입니다.</span><span class="sxs-lookup"><span data-stu-id="d9b6d-162">The directory path specified for the mapping schema (sql-relationship.xml) is relative to the directory where the template is saved.</span></span> <span data-ttu-id="d9b6d-163">또한 다음과 같이 절대 경로를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d9b6d-163">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\MyDir\sql-relationship.xml"  
    ```  
  
3.  <span data-ttu-id="d9b6d-164">SQLXML 4.0 테스트 스크립트(Sqlxml4test.vbs)를 만든 다음 이 스크립트를 사용하여 템플릿을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="d9b6d-164">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="d9b6d-165">자세한 내용은 [ADO를 사용 하 여 SQLXML 쿼리 실행](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="d9b6d-165">For more information, see [Using ADO to Execute SQLXML Queries](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="d9b6d-166">결과 집합은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="d9b6d-166">Here is the result set:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">   
  <Customer CustomerID="1">   
    <Order OrderID="43860" CustomerID="1" />   
    <Order OrderID="44501" CustomerID="1" />   
    <Order OrderID="45283" CustomerID="1" />   
    <Order OrderID="46042" CustomerID="1" />   
  </Customer>   
</ROOT>  
```  
  
### <a name="b-specifying-a-relationship-chain"></a><span data-ttu-id="d9b6d-167">B.</span><span class="sxs-lookup"><span data-stu-id="d9b6d-167">B.</span></span> <span data-ttu-id="d9b6d-168">관계 체인 지정</span><span class="sxs-lookup"><span data-stu-id="d9b6d-168">Specifying a relationship chain</span></span>  
 <span data-ttu-id="d9b6d-169">이 예에서는 AdventureWorks 데이터베이스에서 가져온 데이터를 사용하는 다음과 같은 XML 문서가 필요하다고 가정해 보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="d9b6d-169">For this example, assume that you want the following XML document using data obtained from the AdventureWorks database:</span></span>  
  
```  
<Order SalesOrderID="43659">  
  <Product Name="Mountain Bike Socks, M"/>   
  <Product Name="Sport-100 Helmet, Blue"/>  
  ...  
</Order>  
...  
```  
  
 <span data-ttu-id="d9b6d-170">SalesOrderHeader 테이블의 각 주문에 대해 XML 문서에는 하나의 **\<Order>** 요소가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d9b6d-170">For each order in the Sales.SalesOrderHeader table, the XML document has one **\<Order>** element.</span></span> <span data-ttu-id="d9b6d-171">각 요소에는 **\<Order>** **\<Product>** 주문에서 요청 된 각 제품에 대 한 자식 요소 목록이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d9b6d-171">And each **\<Order>** element has a list of **\<Product>** child elements, one for each product requested in the order.</span></span>  
  
 <span data-ttu-id="d9b6d-172">이 계층을 생성 하는 XSD 스키마를 지정 하려면 OrderOD 및 ODProduct의 두 관계를 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d9b6d-172">To specify an XSD schema that will produce this hierarchy, you must specify two relationships: OrderOD and ODProduct.</span></span> <span data-ttu-id="d9b6d-173">OrderOD 관계는 Sales.SalesOrderHeader와 Sales.SalesOrderDetail 테이블 간의 부모-자식 관계를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d9b6d-173">The OrderOD relationship specifies the parent-child relationship between the Sales.SalesOrderHeader and Sales.SalesOrderDetail tables.</span></span> <span data-ttu-id="d9b6d-174">ODProduct 관계는 Sales.SalesOrderDetail와 Production.Product 테이블 간의 관계를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d9b6d-174">The ODProduct relationship specifies the relationship between the Sales.SalesOrderDetail and Production.Product tables.</span></span>  
  
 <span data-ttu-id="d9b6d-175">다음 스키마에서 `msdata:relationship` **\<Product>** 요소의 주석은 Orderod 및 ODProduct의 두 값을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="d9b6d-175">In the following schema, the `msdata:relationship` annotation on the **\<Product>** element specifies two values: OrderOD and ODProduct.</span></span> <span data-ttu-id="d9b6d-176">이 두 값이 지정되는 순서가 중요합니다.</span><span class="sxs-lookup"><span data-stu-id="d9b6d-176">The order in which these values are specified is important.</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:msdata="urn:schemas-microsoft-com:mapping-schema">  
<xsd:annotation>  
  <xsd:appinfo>  
    <msdata:relationship name="OrderOD"  
          parent="Sales.SalesOrderHeader"  
          parent-key="SalesOrderID"  
          child="Sales.SalesOrderDetail"  
          child-key="SalesOrderID" />  
  
    <msdata:relationship name="ODProduct"  
          parent="Sales.SalesOrderDetail"  
          parent-key="ProductID"  
          child="Production.Product"  
          child-key="ProductID" />  
  </xsd:appinfo>  
</xsd:annotation>  
  
  <xsd:element name="Order" msdata:relation="Sales.SalesOrderHeader"   
               msdata:key-fields="SalesOrderID" type="OrderType" />  
   <xsd:complexType name="OrderType" >  
     <xsd:sequence>  
        <xsd:element name="Product" msdata:relation="Production.Product"   
                     msdata:key-fields="ProductID"  
                     msdata:relationship="OrderOD ODProduct">  
          <xsd:complexType>  
             <xsd:attribute name="Name" type="xsd:string" />  
          </xsd:complexType>  
        </xsd:element>  
     </xsd:sequence>  
        <xsd:attribute name="SalesOrderID"   type="xsd:integer" />   
    </xsd:complexType>  
</xsd:schema>  
```  
  
 <span data-ttu-id="d9b6d-177">명명된 관계를 지정하는 대신 익명 관계를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d9b6d-177">Instead of specifying a named relationship, you can specify an anonymous relationship.</span></span> <span data-ttu-id="d9b6d-178">이 경우 두 관계를 설명 하는 ...의 전체 내용이 **\<annotation>** **\</annotation>** 의 자식 요소로 나타납니다 **\<Product>** .</span><span class="sxs-lookup"><span data-stu-id="d9b6d-178">In this case, the entire contents of **\<annotation>**...**\</annotation>**, which describes the two relationships, appear as a child element of **\<Product>**.</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:msdata="urn:schemas-microsoft-com:mapping-schema">  
  
  <xsd:element name="Order" msdata:relation="Sales.SalesOrderHeader"   
               msdata:key-fields="SalesOrderID" type="OrderType" />  
  
   <xsd:complexType name="OrderType" >  
     <xsd:sequence>  
        <xsd:element name="Product" msdata:relation="Production.Product"   
                     msdata:key-fields="ProductID" >  
         <xsd:annotation>  
          <xsd:appinfo>  
           <msdata:relationship   
               parent="Sales.SalesOrderHeader"  
               parent-key="SalesOrderID"  
               child="Sales.SalesOrderDetail"  
               child-key="SalesOrderID" />  
  
           <msdata:relationship   
               parent="Sales.SalesOrderDetail"  
               parent-key="ProductID"  
               child="Production.Product"  
               child-key="ProductID" />  
         </xsd:appinfo>  
       </xsd:annotation>  
       <xsd:complexType>  
          <xsd:attribute name="Name" type="xsd:string" />  
       </xsd:complexType>  
     </xsd:element>  
   </xsd:sequence>  
   <xsd:attribute name="SalesOrderID"   type="xsd:integer" />   
  </xsd:complexType>  
 </xsd:schema>  
```  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a><span data-ttu-id="d9b6d-179">스키마에 대해 예제 XPath 쿼리를 테스트하려면</span><span class="sxs-lookup"><span data-stu-id="d9b6d-179">To test a sample XPath query against the schema</span></span>  
  
1.  <span data-ttu-id="d9b6d-180">위 스키마 코드를 복사한 후 텍스트 파일에 붙여넣습니다.</span><span class="sxs-lookup"><span data-stu-id="d9b6d-180">Copy the schema code above and paste it into a text file.</span></span> <span data-ttu-id="d9b6d-181">파일을 relationshipChain.xml로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="d9b6d-181">Save the file as relationshipChain.xml.</span></span>  
  
2.  <span data-ttu-id="d9b6d-182">다음 템플릿을 복사한 후 텍스트 파일에 붙여넣습니다.</span><span class="sxs-lookup"><span data-stu-id="d9b6d-182">Copy the following template below and paste it into a text file.</span></span> <span data-ttu-id="d9b6d-183">relationshipChain.xml을 저장한 디렉터리에 파일을 relationshipChainT.xml로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="d9b6d-183">Save the file as relationshipChainT.xml in the same directory where you saved relationshipChain.xml.</span></span>  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
        <sql:xpath-query mapping-schema="relationshipChain.xml">  
            /Order  
        </sql:xpath-query>  
    </ROOT>  
    ```  
  
     <span data-ttu-id="d9b6d-184">매핑 스키마(relationshipChain.xml)에 대해 지정된 디렉터리 경로는 템플릿이 저장된 디렉터리에 대한 상대 경로입니다.</span><span class="sxs-lookup"><span data-stu-id="d9b6d-184">The directory path specified for the mapping schema (relationshipChain.xml) is relative to the directory where the template is saved.</span></span> <span data-ttu-id="d9b6d-185">또한 다음과 같이 절대 경로를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d9b6d-185">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\MyDir\relationshipChain.xml"  
    ```  
  
3.  <span data-ttu-id="d9b6d-186">SQLXML 4.0 테스트 스크립트(Sqlxml4test.vbs)를 만든 다음 이 스크립트를 사용하여 템플릿을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="d9b6d-186">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="d9b6d-187">자세한 내용은 [ADO를 사용 하 여 SQLXML 쿼리 실행](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="d9b6d-187">For more information, see [Using ADO to Execute SQLXML Queries](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="d9b6d-188">결과 집합은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="d9b6d-188">Here is the result set:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">   
  <Order SalesOrderID="43659">  
    <Product Name="Mountain Bike Socks, M" />   
    <Product Name="Sport-100 Helmet, Blue" />   
    <Product Name="AWC Logo Cap" />   
    <Product Name="Long-Sleeve Logo Jersey, M" />   
    <Product Name="Long-Sleeve Logo Jersey, XL" />   
    ...  
  </Order>  
  ...  
</ROOT>  
```  
  
### <a name="c-specifying-the-relationship-annotation-on-an-attribute"></a><span data-ttu-id="d9b6d-189">C.</span><span class="sxs-lookup"><span data-stu-id="d9b6d-189">C.</span></span> <span data-ttu-id="d9b6d-190">특성에 관계 주석 지정</span><span class="sxs-lookup"><span data-stu-id="d9b6d-190">Specifying the relationship annotation on an attribute</span></span>  
 <span data-ttu-id="d9b6d-191">이 예제의 스키마에는 \<Customer> \<CustomerID> 자식 요소가 있는 요소와 IDREFS 유형의 OrderIDList 특성이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d9b6d-191">The schema in this example includes a \<Customer> element with a \<CustomerID> child element and an OrderIDList attribute of IDREFS type.</span></span> <span data-ttu-id="d9b6d-192">\<Customer>요소는 AdventureWorks 데이터베이스의 Sales. Customer 테이블에 매핑됩니다.</span><span class="sxs-lookup"><span data-stu-id="d9b6d-192">The \<Customer> element maps to the Sales.Customer table in the AdventureWorks database.</span></span> <span data-ttu-id="d9b6d-193">기본적으로이 매핑의 범위는 자식 요소나 특성에가 지정 되지 않은 경우 모든 자식 요소 또는 특성에 적용 됩니다 `sql:relation` .이 경우 요소를 사용 하 여 적절 한 기본 키/외래 키 관계를 정의 해야 합니다 \<relationship> .</span><span class="sxs-lookup"><span data-stu-id="d9b6d-193">By default, the scope of this mapping applies to all the child elements or attributes unless `sql:relation` is specified on the child element or attribute, in which case, the appropriate primary-key/foreign-key relationship must be defined using the \<relationship> element.</span></span> <span data-ttu-id="d9b6d-194">`relation` 주석을 사용하여 다른 테이블을 지정하는 자식 요소 또는 특성은 `relationship` 주석도 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d9b6d-194">And the child element or attribute, which specifies the different table using the `relation` annotation, must also specify the `relationship` annotation.</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
<xsd:annotation>  
  <xsd:appinfo>  
    <sql:relationship name="CustOrders"  
          parent="Sales.Customer"  
          parent-key="CustomerID"  
          child="Sales.SalesOrderHeader"  
          child-key="CustomerID" />  
     </xsd:appinfo>  
</xsd:annotation>  
  
  <xsd:element name="Customer" sql:relation="Sales.Customer" type="CustomerType" />  
   <xsd:complexType name="CustomerType" >  
     <xsd:sequence>  
        <xsd:element name="CustomerID"   type="xsd:string" />   
     </xsd:sequence>  
     <xsd:attribute name="OrderIDList"   
                     type="xsd:IDREFS"   
                     sql:relation="Sales.SalesOrderHeader"   
                     sql:field="SalesOrderID"  
                     sql:relationship="CustOrders" >  
        </xsd:attribute>  
    </xsd:complexType>  
</xsd:schema>  
```  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a><span data-ttu-id="d9b6d-195">스키마에 대해 예제 XPath 쿼리를 테스트하려면</span><span class="sxs-lookup"><span data-stu-id="d9b6d-195">To test a sample XPath query against the schema</span></span>  
  
1.  <span data-ttu-id="d9b6d-196">위 스키마 코드를 복사한 후 텍스트 파일에 붙여넣습니다.</span><span class="sxs-lookup"><span data-stu-id="d9b6d-196">Copy the schema code above and paste it into a text file.</span></span> <span data-ttu-id="d9b6d-197">파일을 relationship-on-attribute.xml로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="d9b6d-197">Save the file as relationship-on-attribute.xml.</span></span>  
  
2.  <span data-ttu-id="d9b6d-198">다음 템플릿을 복사한 후 파일에 붙여넣습니다.</span><span class="sxs-lookup"><span data-stu-id="d9b6d-198">Copy the following template and paste it into a file.</span></span> <span data-ttu-id="d9b6d-199">relationship-on-attribute.xml을 저장한 디렉터리에 파일을 relationship-on-attributeT.xml로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="d9b6d-199">Save the file as relationship-on-attributeT.xml in the same directory where you saved relationship-on-attribute.xml.</span></span> <span data-ttu-id="d9b6d-200">템플릿의 쿼리에서는 CustomerID가 1인 고객을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d9b6d-200">The query in the template selects a customer with the CustomerID of 1.</span></span>  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:xpath-query mapping-schema="relationship-on-attribute.xml">  
        /Customer[CustomerID=1]  
      </sql:xpath-query>  
    </ROOT>  
    ```  
  
     <span data-ttu-id="d9b6d-201">매핑 스키마(relationship-on-attribute.xml)에 대해 지정된 디렉터리 경로는 템플릿이 저장된 디렉터리에 대한 상대 경로입니다.</span><span class="sxs-lookup"><span data-stu-id="d9b6d-201">The directory path specified for the mapping schema (relationship-on-attribute.xml) is relative to the directory where the template is saved.</span></span> <span data-ttu-id="d9b6d-202">또한 다음과 같이 절대 경로를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d9b6d-202">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\MyDir\relationship-on-attribute.xml"  
    ```  
  
3.  <span data-ttu-id="d9b6d-203">SQLXML 4.0 테스트 스크립트(Sqlxml4test.vbs)를 만든 다음 이 스크립트를 사용하여 템플릿을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="d9b6d-203">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="d9b6d-204">자세한 내용은 [ADO를 사용 하 여 SQLXML 쿼리 실행](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="d9b6d-204">For more information, see [Using ADO to Execute SQLXML Queries](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="d9b6d-205">결과 집합은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="d9b6d-205">Here is the result set:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">   
  <Customer OrderIDList="43860 44501 45283 46042">  
    <CustomerID>1</CustomerID>   
  </Customer>  
</ROOT>  
```  
  
### <a name="d-specifying-sqlrelationship-on-multiple-elements"></a><span data-ttu-id="d9b6d-206">D.</span><span class="sxs-lookup"><span data-stu-id="d9b6d-206">D.</span></span> <span data-ttu-id="d9b6d-207">여러 요소에 대해 sql:relationship 지정</span><span class="sxs-lookup"><span data-stu-id="d9b6d-207">Specifying sql:relationship on multiple elements</span></span>  
 <span data-ttu-id="d9b6d-208">이 예제에서 주석이 추가 된 XSD 스키마에는 **\<Customer>** , **\<Order>** 및 **\<OrderDetail>** 요소가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d9b6d-208">In this example, the annotated XSD schema contains the **\<Customer>**, **\<Order>**, and **\<OrderDetail>** elements.</span></span>  
  
 <span data-ttu-id="d9b6d-209">요소는 **\<Order>** 요소의 자식 요소입니다 **\<Customer>** .</span><span class="sxs-lookup"><span data-stu-id="d9b6d-209">The **\<Order>** element is a child element of the **\<Customer>** element.</span></span> <span data-ttu-id="d9b6d-210">**\<sql:relationship>** 은 자식 요소에 대해 지정 됩니다. **\<Order>** 따라서 고객에 게 속한 주문은의 자식 요소로 표시 됩니다 **\<Customer>** .</span><span class="sxs-lookup"><span data-stu-id="d9b6d-210">**\<sql:relationship>** is specified on the **\<Order>** child element; therefore, orders that belong to a customer appear as child elements of **\<Customer>**.</span></span>  
  
 <span data-ttu-id="d9b6d-211">요소에는 **\<Order>** **\<OrderDetail>** 자식 요소가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d9b6d-211">The **\<Order>** element includes the **\<OrderDetail>** child element.</span></span> <span data-ttu-id="d9b6d-212">**\<sql:relationship>** 은 자식 요소에 대해 지정 **\<OrderDetail>** 되므로 주문과 관련 된 주문 정보는 해당 요소의 자식 요소로 표시 됩니다 **\<Order>** .</span><span class="sxs-lookup"><span data-stu-id="d9b6d-212">**\<sql:relationship>** is specified on **\<OrderDetail>** child element, so the order details that pertain to an order appear as child elements of that **\<Order>** element.</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
<xsd:annotation>  
  <xsd:appinfo>  
    <sql:relationship name="CustOrders"  
        parent="Sales.Customer"  
        parent-key="CustomerID"  
        child="Sales.SalesOrderHeader"  
        child-key="CustomerID" />  
  
    <sql:relationship name="OrderOrderDetail"  
        parent="Sales.SalesOrderHeader"  
        parent-key="SalesOrderID"  
        child="Sales.SalesOrderDetail"  
        child-key="SalesOrderID" />  
  </xsd:appinfo>  
</xsd:annotation>  
  
  <xsd:element name="Customer" sql:relation="Sales.Customer" >  
   <xsd:complexType>  
     <xsd:sequence>  
        <xsd:element name="Order" sql:relation="Sales.SalesOrderHeader"    
              sql:relationship="CustOrders" maxOccurs="unbounded" >  
          <xsd:complexType>  
              <xsd:sequence>  
                <xsd:element name="OrderDetail"   
                             sql:relation="Sales.SalesOrderDetail"   
                             sql:relationship="OrderOrderDetail"   
                             maxOccurs="unbounded" >  
                  <xsd:complexType>  
                    <xsd:attribute name="SalesOrderID" type="xsd:integer" />  
                    <xsd:attribute name="ProductID" type="xsd:string" />  
                    <xsd:attribute name="OrderQty" type="xsd:integer" />  
                  </xsd:complexType>  
                </xsd:element>  
              </xsd:sequence>  
              <xsd:attribute name="SalesOrderID" type="xsd:integer" />  
              <xsd:attribute name="OrderDate" type="xsd:date" />  
              <xsd:attribute name="CustomerID" type="xsd:string" />  
          </xsd:complexType>  
        </xsd:element>  
      </xsd:sequence>  
      <xsd:attribute name="CustomerID" type="xsd:string" />  
     </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a><span data-ttu-id="d9b6d-213">스키마에 대해 예제 XPath 쿼리를 테스트하려면</span><span class="sxs-lookup"><span data-stu-id="d9b6d-213">To test a sample XPath query against the schema</span></span>  
  
1.  <span data-ttu-id="d9b6d-214">위 스키마 코드를 복사한 후 텍스트 파일에 붙여넣습니다.</span><span class="sxs-lookup"><span data-stu-id="d9b6d-214">Copy the schema code above and paste it into a text file.</span></span> <span data-ttu-id="d9b6d-215">파일을 relationship-multiple-elements.xml로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="d9b6d-215">Save the file as relationship-multiple-elements.xml.</span></span>  
  
2.  <span data-ttu-id="d9b6d-216">다음 템플릿을 복사한 후 텍스트 파일에 붙여넣습니다.</span><span class="sxs-lookup"><span data-stu-id="d9b6d-216">Copy the following template and paste it into a text file.</span></span> <span data-ttu-id="d9b6d-217">relationship-multiple-elements.xml을 저장한 디렉터리에 파일을 relationship-multiple-elementsT.xml로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="d9b6d-217">Save the file as relationship-multiple-elementsT.xml in the same directory where you saved relationship-multiple-elements.xml.</span></span> <span data-ttu-id="d9b6d-218">템플릿의 쿼리에서는 CustomerID가 1이고 SalesOrderID가 43860인 고객의 주문 정보를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="d9b6d-218">The query in the template returns order information for a customer with the CustomerID of 1 and SalesOrderID of 43860.</span></span>  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:xpath-query mapping-schema="relationship-multiple-elements.xml">  
        /Customer[@CustomerID=1]/Order[@SalesOrderID=43860]  
      </sql:xpath-query>  
    </ROOT>  
    ```  
  
     <span data-ttu-id="d9b6d-219">매핑 스키마(relationship-multiple-elements.xml)에 대해 지정된 디렉터리 경로는 템플릿이 저장된 디렉터리에 대한 상대 경로입니다.</span><span class="sxs-lookup"><span data-stu-id="d9b6d-219">The directory path specified for the mapping schema (relationship-multiple-elements.xml) is relative to the directory where the template is saved.</span></span> <span data-ttu-id="d9b6d-220">또한 다음과 같이 절대 경로를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d9b6d-220">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\MyDir\relationship-multiple-elements.xml"  
    ```  
  
3.  <span data-ttu-id="d9b6d-221">SQLXML 4.0 테스트 스크립트(Sqlxml4test.vbs)를 만든 다음 이 스크립트를 사용하여 템플릿을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="d9b6d-221">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="d9b6d-222">자세한 내용은 [ADO를 사용 하 여 SQLXML 쿼리 실행](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="d9b6d-222">For more information, see [Using ADO to Execute SQLXML Queries](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="d9b6d-223">결과 집합은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="d9b6d-223">Here is the result set:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Order SalesOrderID="43860" OrderDate="2001-08-01" CustomerID="1">  
     <OrderDetail SalesOrderID="43860" ProductID="761" OrderQty="2" />   
     <OrderDetail SalesOrderID="43860" ProductID="770" OrderQty="1" />   
     <OrderDetail SalesOrderID="43860" ProductID="758" OrderQty="2" />   
     <OrderDetail SalesOrderID="43860" ProductID="765" OrderQty="2" />   
     <OrderDetail SalesOrderID="43860" ProductID="732" OrderQty="1" />   
     <OrderDetail SalesOrderID="43860" ProductID="762" OrderQty="1" />   
     <OrderDetail SalesOrderID="43860" ProductID="738" OrderQty="1" />   
     <OrderDetail SalesOrderID="43860" ProductID="768" OrderQty="1" />   
     <OrderDetail SalesOrderID="43860" ProductID="753" OrderQty="2" />   
     <OrderDetail SalesOrderID="43860" ProductID="729" OrderQty="1" />   
     <OrderDetail SalesOrderID="43860" ProductID="763" OrderQty="1" />   
     <OrderDetail SalesOrderID="43860" ProductID="756" OrderQty="1" />   
  </Order>  
</ROOT>  
```  
  
### <a name="e-specifying-the-sqlrelationship-without-the-parent-attribute"></a><span data-ttu-id="d9b6d-224">E.</span><span class="sxs-lookup"><span data-stu-id="d9b6d-224">E.</span></span> <span data-ttu-id="d9b6d-225">\<sql:relationship>부모 특성을 사용 하지 않고를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="d9b6d-225">Specifying the \<sql:relationship> without the parent attribute</span></span>  
 <span data-ttu-id="d9b6d-226">이 예에서는 부모 특성을 사용 하지 않고를 지정 하는 방법을 보여 줍니다 **\<sql:relationship>** . **parent**</span><span class="sxs-lookup"><span data-stu-id="d9b6d-226">This example illustrates specifying the **\<sql:relationship>** without the **parent** attribute.</span></span> <span data-ttu-id="d9b6d-227">예를 들어 다음과 같은 직원 테이블을 가정해 보십시오.</span><span class="sxs-lookup"><span data-stu-id="d9b6d-227">For example, assume you have the following employee tables:</span></span>  
  
```  
Emp1(SalesPersonID, FirstName, LastName, ReportsTo)  
Emp2(SalesPersonID, FirstName, LastName, ReportsTo)  
```  
  
 <span data-ttu-id="d9b6d-228">다음 XML 뷰에는 **\<Emp1>** **\<Emp2>** Emp1 및 Emp2 테이블에 매핑되는 및 요소가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d9b6d-228">The following XML view has the **\<Emp1>** and **\<Emp2>** elements mapping to the Sales.Emp1 and Sales.Emp2 tables:</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
<xsd:annotation>  
  <xsd:appinfo>  
    <sql:relationship name="EmpOrders"  
          parent-key="SalesPersonID"  
          child="Sales.SalesOrderHeader"  
          child-key="SalesPersonID" />  
     </xsd:appinfo>  
</xsd:annotation>  
  
  <xsd:element name="Emp1" sql:relation="Sales.Emp1" type="EmpType" />  
  <xsd:element name="Emp2" sql:relation="Sales.Emp2" type="EmpType" />  
   <xsd:complexType name="EmpType" >  
     <xsd:sequence>  
        <xsd:element name="Order"   
                     sql:relation="Sales.SalesOrderHeader"   
                     sql:relationship="EmpOrders" >  
          <xsd:complexType>  
             <xsd:attribute name="SalesOrderID" type="xsd:integer" />  
             <xsd:attribute name="CustomerID" type="xsd:string" />  
          </xsd:complexType>  
        </xsd:element>  
     </xsd:sequence>  
        <xsd:attribute name="SalesPersonID"   type="xsd:integer" />   
        <xsd:attribute name="LastName"   type="xsd:string" />   
    </xsd:complexType>  
  
</xsd:schema>  
```  
  
 <span data-ttu-id="d9b6d-229">스키마에서 **\<Emp1>** 요소와 요소는 모두 **\<Emp2>** 형식입니다 `EmpType` .</span><span class="sxs-lookup"><span data-stu-id="d9b6d-229">In the schema, both the **\<Emp1>** element and **\<Emp2>** element are of type `EmpType`.</span></span> <span data-ttu-id="d9b6d-230">형식은 `EmpType` **\<Order>** 자식 요소와 해당을 설명 합니다 **\<sql:relationship>** .</span><span class="sxs-lookup"><span data-stu-id="d9b6d-230">The type `EmpType` describes an **\<Order>** child element and the corresponding **\<sql:relationship>**.</span></span> <span data-ttu-id="d9b6d-231">이 경우 부모 특성을 사용 하 여에서 식별할 수 있는 단일 부모가 없습니다 **\<sql:relationship>** . **parent**</span><span class="sxs-lookup"><span data-stu-id="d9b6d-231">In this case, there is no single parent that can be identified in **\<sql:relationship>** by using the **parent** attribute.</span></span> <span data-ttu-id="d9b6d-232">이 경우에서 **부모** 특성을 지정 하지 않습니다. **\<sql:relationship>** **부모** 특성 정보는 스키마의 계층에서 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="d9b6d-232">In this situation, you don't specify the **parent** attribute in **\<sql:relationship>**; the **parent** attribute information is obtained from the hierarchy in the schema.</span></span>  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a><span data-ttu-id="d9b6d-233">스키마에 대해 예제 XPath 쿼리를 테스트하려면</span><span class="sxs-lookup"><span data-stu-id="d9b6d-233">To test a sample XPath query against the schema</span></span>  
  
1.  <span data-ttu-id="d9b6d-234">AdventureWorks 데이터베이스에 다음 테이블을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d9b6d-234">Create these tables in the AdventureWorks database:</span></span>  
  
    ```  
    USE AdventureWorks  
    CREATE TABLE Sales.Emp1 (  
           SalesPersonID int primary key,   
           FirstName  varchar(20),   
           LastName   varchar(20),   
           ReportsTo int)  
    Go  
    CREATE TABLE Sales.Emp2 (  
           SalesPersonID int primary key,   
           FirstName  varchar(20),   
           LastName   varchar(20),   
           ReportsTo int)  
    Go  
    ```  
  
2.  <span data-ttu-id="d9b6d-235">테이블에 다음 예제 데이터를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="d9b6d-235">Add this sample data in the tables:</span></span>  
  
    ```  
    INSERT INTO Sales.Emp1 values (279, 'Nancy', 'Devolio',NULL)  
    INSERT INTO Sales.Emp1 values (282, 'Andrew', 'Fuller',1)  
    INSERT INTO Sales.Emp1 values (276, 'Janet', 'Leverling',1)  
    INSERT INTO Sales.Emp2 values (277, 'Margaret', 'Peacock',3)  
    INSERT INTO Sales.Emp2 values (283, 'Steven', 'Devolio',4)  
    INSERT INTO Sales.Emp2 values (275, 'Nancy', 'Buchanan',5)  
    INSERT INTO Sales.Emp2 values (281, 'Michael', 'Suyama',6)  
    ```  
  
3.  <span data-ttu-id="d9b6d-236">위 스키마 코드를 복사한 후 텍스트 파일에 붙여넣습니다.</span><span class="sxs-lookup"><span data-stu-id="d9b6d-236">Copy the schema code above and paste it into a text file.</span></span> <span data-ttu-id="d9b6d-237">파일을 relationship-noparent.xml로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="d9b6d-237">Save the file as relationship-noparent.xml.</span></span>  
  
4.  <span data-ttu-id="d9b6d-238">다음 템플릿을 복사한 후 텍스트 파일에 붙여넣습니다.</span><span class="sxs-lookup"><span data-stu-id="d9b6d-238">Copy the following template and paste it into a text file.</span></span> <span data-ttu-id="d9b6d-239">relationship-noparent.xml을 저장한 디렉터리에 파일을 relationship-noparentT.xml로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="d9b6d-239">Save the file as relationship-noparentT.xml in the same directory where you saved relationship-noparent.xml.</span></span> <span data-ttu-id="d9b6d-240">템플릿의 쿼리는 모든 요소를 선택 \<Emp1> 합니다. 따라서 부모는 Emp1입니다.</span><span class="sxs-lookup"><span data-stu-id="d9b6d-240">The query in the template selects all the \<Emp1> elements (therefore, the parent is Emp1).</span></span>  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
        <sql:xpath-query mapping-schema="relationship-noparent.xml">  
            /Emp1  
        </sql:xpath-query>  
    </ROOT>  
    ```  
  
     <span data-ttu-id="d9b6d-241">매핑 스키마(relationship-noparent.xml)에 대해 지정된 디렉터리 경로는 템플릿이 저장된 디렉터리에 대한 상대 경로입니다.</span><span class="sxs-lookup"><span data-stu-id="d9b6d-241">The directory path specified for the mapping schema (relationship-noparent.xml) is relative to the directory where the template is saved.</span></span> <span data-ttu-id="d9b6d-242">또한 다음과 같이 절대 경로를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d9b6d-242">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\MyDir\relationship-noparent.xml"  
    ```  
  
5.  <span data-ttu-id="d9b6d-243">SQLXML 4.0 테스트 스크립트(Sqlxml4test.vbs)를 만든 다음 이 스크립트를 사용하여 템플릿을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="d9b6d-243">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="d9b6d-244">자세한 내용은 [ADO를 사용 하 여 SQLXML 쿼리 실행](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="d9b6d-244">For more information, see [Using ADO to Execute SQLXML Queries](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="d9b6d-245">다음은 결과 집합의 일부입니다.</span><span class="sxs-lookup"><span data-stu-id="d9b6d-245">Here is a partial result set:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
<Emp1 SalesPersonID="276" LastName="Leverling">  
  <Order SalesOrderID="43663" CustomerID="510" />   
  <Order SalesOrderID="43666" CustomerID="511" />   
  <Order SalesOrderID="43859" CustomerID="259" />  
  ...  
</Emp1>  
```  
  
  
