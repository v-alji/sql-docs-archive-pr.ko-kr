---
title: 레코드 생성 프로세스 (SQLXML 4.0) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- XML Bulk Load [SQLXML], record generation process
- node scopes [SQLXML]
- record subsets [SQLXML]
- scope [SQLXML]
- key ordering rules [SQLXML]
- record generation process for bulk loads [SQLXML]
- entering node scope [SQLXML]
- bulk load [SQLXML], record generation process
- leaving node scope [SQLXML]
- schema mapping [SQLXML]
ms.assetid: d8885bbe-6f15-4fb9-9684-ca7883cfe9ac
author: rothja
ms.author: jroth
ms.openlocfilehash: 5734776864aecbda7adaf0b9b16180b5ebd55ce3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728139"
---
# <a name="record-generation-process-sqlxml-40"></a><span data-ttu-id="497c8-102">레코드 생성 프로세스(SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="497c8-102">Record Generation Process (SQLXML 4.0)</span></span>
  <span data-ttu-id="497c8-103">XML 대량 로드는 XML 입력 데이터를 처리하고 Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]의 적절한 테이블로 사용할 수 있도록 레코드를 준비합니다.</span><span class="sxs-lookup"><span data-stu-id="497c8-103">XML Bulk Load processes the XML input data and prepares records for the appropriate tables in Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="497c8-104">XML 대량 로드의 로직은 새 레코드를 생성할 시기, 레코드 필드로 복사할 자식 요소나 특성 값, 레코드가 완성되어 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]에 삽입할 수 있도록 보낼 준비가 끝나는 시기를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="497c8-104">The logic in XML Bulk Load determines when to generate a new record, what child element or attribute values to copy into the fields of the record, and when the record is complete and ready to be sent to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] for insertion.</span></span>  
  
 <span data-ttu-id="497c8-105">XML 대량 로드는 전체 XML 입력 데이터를 메모리로 로드하지 않으며 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]에 데이터를 보내기 전에 전체 레코드 집합을 생성하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="497c8-105">XML Bulk Load does not load the entire XML input data into memory, and does not produce complete record sets before sending data to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="497c8-106">이것은 XML 입력 데이터가 큰 문서일 수 있으며 전체 문서를 메모리로 로드하면 많은 비용이 들 수 있기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="497c8-106">This is because XML input data can be a large document and loading the entire document in memory can be expensive.</span></span> <span data-ttu-id="497c8-107">대신 XML 대량 로드는 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="497c8-107">Instead, XML Bulk Load does the following:</span></span>  
  
1.  <span data-ttu-id="497c8-108">매핑 스키마를 분석하고 필요한 실행 계획을 준비합니다.</span><span class="sxs-lookup"><span data-stu-id="497c8-108">Analyzes the mapping schema and prepares the necessary execution plan.</span></span>  
  
2.  <span data-ttu-id="497c8-109">실행 계획을 입력 스트림의 데이터에 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="497c8-109">Applies the execution plan to the data in the input stream.</span></span>  
  
 <span data-ttu-id="497c8-110">이 순차적 처리에서는 XML 입력 데이터를 특정 방식으로 제공해야 하므로</span><span class="sxs-lookup"><span data-stu-id="497c8-110">This sequential processing makes it important to provide the XML input data in a specific way.</span></span> <span data-ttu-id="497c8-111">XML 대량 로드가 매핑 스키마를 분석하는 방법과 레코드 생성 프로세스가 발생하는 방식을 이해하고 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="497c8-111">You must understand how XML Bulk Load analyzes the mapping schema and how the record generation process occurs.</span></span> <span data-ttu-id="497c8-112">이러한 이해를 바탕으로 XML 대량 로드에 원하는 결과를 생성하는 매핑 스키마를 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="497c8-112">With this understanding, you can provide a mapping schema to XML Bulk Load that produces the results you want.</span></span>  
  
 <span data-ttu-id="497c8-113">XML 대량 로드는 주석을 사용하여 명시적으로 지정되거나 기본 매핑을 통해 암시적으로 지정된 열 및 테이블 매핑을 비롯한 일반적인 매핑 스키마 주석과 조인 관계를 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="497c8-113">XML Bulk Load handles common mapping schema annotations, including column and table mappings (specified explicitly by using annotations or implicitly through the default mapping), and join relationships.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="497c8-114">여기에서는 주석이 추가된 XSD 또는 XDR 매핑 스키마를 잘 알고 있다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="497c8-114">It is assumed that you are familiar with annotated XSD or XDR mapping schemas.</span></span> <span data-ttu-id="497c8-115">스키마에 대 한 자세한 내용은 sqlxml [4.0&#41;에서 사용 되지 &#40;](../../sqlxml/annotated-xsd-schemas/annotated-xdr-schemas-deprecated-in-sqlxml-4-0.md)&#41;또는 주석이 추가 된 XDR 스키마 [4.0 &#40;주석이 추가 된 XSD 스키마 소개](../../sqlxml/annotated-xsd-schemas/introduction-to-annotated-xsd-schemas-sqlxml-4-0.md) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="497c8-115">For more information about schemas, see [Introduction to Annotated XSD Schemas &#40;SQLXML 4.0&#41;](../../sqlxml/annotated-xsd-schemas/introduction-to-annotated-xsd-schemas-sqlxml-4-0.md) or [Annotated XDR Schemas &#40;Deprecated in SQLXML 4.0&#41;](../../sqlxml/annotated-xsd-schemas/annotated-xdr-schemas-deprecated-in-sqlxml-4-0.md).</span></span>  
  
 <span data-ttu-id="497c8-116">레코드 생성을 이해하려면 다음 개념을 이해해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="497c8-116">Understanding record generation requires understanding the following concepts:</span></span>  
  
-   <span data-ttu-id="497c8-117">노드 범위</span><span class="sxs-lookup"><span data-stu-id="497c8-117">Scope of a node</span></span>  
  
-   <span data-ttu-id="497c8-118">레코드 생성 규칙</span><span class="sxs-lookup"><span data-stu-id="497c8-118">Record Generation Rule</span></span>  
  
-   <span data-ttu-id="497c8-119">레코드 하위 집합 및 키 순서 지정 규칙</span><span class="sxs-lookup"><span data-stu-id="497c8-119">Record subset and the Key Ordering Rule</span></span>  
  
-   <span data-ttu-id="497c8-120">레코드 생성 규칙의 예외</span><span class="sxs-lookup"><span data-stu-id="497c8-120">Exceptions to the Record Generation Rule</span></span>  
  
## <a name="scope-of-a-node"></a><span data-ttu-id="497c8-121">노드 범위</span><span class="sxs-lookup"><span data-stu-id="497c8-121">Scope of a Node</span></span>  
 <span data-ttu-id="497c8-122">Xml 대량 로드에서 xml 입력 데이터 스트림에이를 발견할 경우 xml 문서의 노드 (요소 또는 특성)가 *범위에* 들어갑니다.</span><span class="sxs-lookup"><span data-stu-id="497c8-122">A node (an element or an attribute) in an XML document enters *into scope* when XML Bulk Load encounters it in the XML input data stream.</span></span> <span data-ttu-id="497c8-123">요소 노드의 경우 요소의 시작 태그로 요소의 범위가 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="497c8-123">For an element node, the start tag of the element brings the element in scope.</span></span> <span data-ttu-id="497c8-124">특성 노드의 경우 특성 이름으로 특성의 범위가 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="497c8-124">For an attribute node, the attribute name brings the attribute in scope.</span></span>  
  
 <span data-ttu-id="497c8-125">범위에 사용할 데이터가 더 이상 없을 때 노드에서 범위가 끝납니다. 즉, 끝 태그(요소 노드의 경우)나 특성 값 끝(특성 노드의 경우)에서 범위가 끝납니다.</span><span class="sxs-lookup"><span data-stu-id="497c8-125">A node leaves scope when there is no more data for it: either at the end tag (in the case of an element node) or at the end of an attribute value (in the case of an attribute node).</span></span>  
  
## <a name="record-generation-rule"></a><span data-ttu-id="497c8-126">레코드 생성 규칙</span><span class="sxs-lookup"><span data-stu-id="497c8-126">Record Generation Rule</span></span>  
 <span data-ttu-id="497c8-127">노드(요소 또는 특성)에서 범위가 시작되면 해당 노드에서 레코드가 생성될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="497c8-127">When a node (element or attribute) enters into scope, there is a potential for generating a record from that node.</span></span> <span data-ttu-id="497c8-128">이러한 레코드는 연결된 노드가 범위에 속하는 동안 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="497c8-128">The record lives as long as the associated node is in scope.</span></span> <span data-ttu-id="497c8-129">노드가 범위를 벗어나면 XML 대량 로드는 생성된 레코드가 완성된 것으로 간주하여 해당 레코드를(데이터와 함께) 삽입할 수 있도록 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="497c8-129">When the node goes out of scope, XML Bulk Load considers the generated record complete (with data) and sends it to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] for insertion.</span></span>  
  
 <span data-ttu-id="497c8-130">예를 들어, 다음 XSD 스키마 조각을 고려해 보십시오.</span><span class="sxs-lookup"><span data-stu-id="497c8-130">For example, consider the following XSD schema fragment:</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:element name="Customer" sql:relation="Customers" >  
   <xsd:complexType>  
     <xsd:attribute name="CustomerID" type="xsd:string" />  
     <xsd:attribute name="CompanyName" type="xsd:string" />  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
 <span data-ttu-id="497c8-131">스키마는 **\<Customer>** **CustomerID** 및 **CompanyName** 특성이 있는 요소를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="497c8-131">The schema specifies a **\<Customer>** element with **CustomerID** and **CompanyName** attributes.</span></span> <span data-ttu-id="497c8-132">`sql:relation`주석은 **\<Customer>** 요소를 Customers 테이블에 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="497c8-132">The `sql:relation` annotation maps the **\<Customer>** element to the Customers table.</span></span>  
  
 <span data-ttu-id="497c8-133">다음 XML 문서 조각을 고려하십시오.</span><span class="sxs-lookup"><span data-stu-id="497c8-133">Consider this fragment of an XML document:</span></span>  
  
```  
<Customer CustomerID="1" CompanyName="xyz" />  
<Customer CustomerID="2" CompanyName="abc" />  
...  
```  
  
 <span data-ttu-id="497c8-134">XML 대량 로드에 이전 단락에서 설명한 스키마와 XML 데이터가 입력으로 제공되면 XML 대량 로드는 원본 데이터에서 다음과 같은 방식으로 노드(요소와 특성)를 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="497c8-134">When XML Bulk Load is provided with the schema described in the preceding paragraphs and XML data as input, it processes the nodes (elements and attributes) in the source data as follows:</span></span>  
  
-   <span data-ttu-id="497c8-135">첫 번째 요소의 시작 태그는 **\<Customer>** 해당 요소를 범위에 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="497c8-135">The start tag of the first **\<Customer>** element brings that element in scope.</span></span> <span data-ttu-id="497c8-136">이 노드는 Customers 테이블에 매핑되므로</span><span class="sxs-lookup"><span data-stu-id="497c8-136">This node maps to the Customers table.</span></span> <span data-ttu-id="497c8-137">XML 대량 로드는 Customers 테이블에 대한 레코드를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="497c8-137">Therefore, XML Bulk Load generates a record for the Customers table.</span></span>  
  
-   <span data-ttu-id="497c8-138">스키마에서 요소의 모든 특성 **\<Customer>** 은 Customers 테이블의 열에 매핑됩니다.</span><span class="sxs-lookup"><span data-stu-id="497c8-138">In the schema, all attributes of the **\<Customer>** element map to columns of the Customers table.</span></span> <span data-ttu-id="497c8-139">이러한 특성의 범위가 시작되면 XML 대량 로드는 해당 값을 부모 범위에 의해 미리 생성된 고객 레코드에 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="497c8-139">As these attributes enter into scope, XML Bulk Load copies their values to the customer record that is already generated by the parent scope.</span></span>  
  
-   <span data-ttu-id="497c8-140">XML 대량 로드가 요소의 끝 태그에 도달 하면 **\<Customer>** 요소는 범위를 벗어날 것입니다.</span><span class="sxs-lookup"><span data-stu-id="497c8-140">When XML Bulk Load reaches the end tag for the **\<Customer>** element, the element goes out of scope.</span></span> <span data-ttu-id="497c8-141">그러면 XML 대량 로드는 레코드가 완료된 것으로 간주하고 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]로 해당 레코드를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="497c8-141">This causes XML Bulk Load to consider the record complete and send it to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="497c8-142">XML 대량 로드는 각 후속 요소에 대해이 프로세스를 따릅니다 **\<Customer>** .</span><span class="sxs-lookup"><span data-stu-id="497c8-142">XML Bulk Load follows this process for each subsequent **\<Customer>** element.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="497c8-143">이 모델에서는 끝 태그에 도달할 때(또는 노드가 범위를 벗어날 때) 레코드가 삽입되므로 레코드와 관련된 모든 데이터를 노드 범위 내에 정의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="497c8-143">In this model, because a record is inserted when the end tag is reached (or the node is out of scope), you must define all of the data that is associated with the record within the scope of the node.</span></span>  
  
## <a name="record-subset-and-the-key-ordering-rule"></a><span data-ttu-id="497c8-144">레코드 하위 집합 및 키 순서 지정 규칙</span><span class="sxs-lookup"><span data-stu-id="497c8-144">Record Subset and the Key Ordering Rule</span></span>  
 <span data-ttu-id="497c8-145">`<sql:relationship>`을 사용하는 매핑 스키마를 지정할 때 하위 집합이라는 용어는 관계의 외래 쪽에서 생성되는 레코드 집합을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="497c8-145">When you specify a mapping schema that uses `<sql:relationship>`, the subset term refers to the set of records that is generated on the foreign side of the relationship.</span></span> <span data-ttu-id="497c8-146">다음 예에서는 CustOrder 레코드가 `<sql:relationship>`의 외래 쪽에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="497c8-146">In the following example, the CustOrder records are on the foreign side, `<sql:relationship>`.</span></span>  
  
 <span data-ttu-id="497c8-147">예를 들어 데이터베이스에 다음과 같은 테이블이 포함된다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="497c8-147">For example, suppose a database contains the following tables:</span></span>  
  
-   <span data-ttu-id="497c8-148">Cust (CustomerID, CompanyName, City)</span><span class="sxs-lookup"><span data-stu-id="497c8-148">Cust (CustomerID, CompanyName, City)</span></span>  
  
-   <span data-ttu-id="497c8-149">CustOrder (CustomerID, OrderID)</span><span class="sxs-lookup"><span data-stu-id="497c8-149">CustOrder (CustomerID, OrderID)</span></span>  
  
 <span data-ttu-id="497c8-150">CustOrder 테이블의 CustomerID는 Cust 테이블의 CustomerID 기본 키를 참조하는 외래 키입니다.</span><span class="sxs-lookup"><span data-stu-id="497c8-150">The CustomerID in the CustOrder table is a foreign key that refers to the CustomerID primary key in the Cust table.</span></span>  
  
 <span data-ttu-id="497c8-151">이제 다음과 같은 주석이 추가된 XSD 스키마에 지정된 XML 뷰를 고려해 보십시오.</span><span class="sxs-lookup"><span data-stu-id="497c8-151">Now, consider the XML view as specified in the following annotated XSD schema.</span></span> <span data-ttu-id="497c8-152">이 스키마에서는 `<sql:relationship>`을 사용하여 Cust 및 CustOrder 테이블 간의 관계를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="497c8-152">This schema uses `<sql:relationship>` to specify the relationship between the Cust and CustOrder tables.</span></span>  
  
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
</xsd:schema>  
```  
  
 <span data-ttu-id="497c8-153">예제 XML 데이터와 작업 예제를 만드는 단계는 아래에 지정되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="497c8-153">The sample XML data and the steps to create a working sample are given below.</span></span>  
  
-   <span data-ttu-id="497c8-154">**\<Customer>** Xml 데이터 파일의 요소 노드가 범위에 들어가면 Xml 대량 로드가 Cust 테이블에 대 한 레코드를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="497c8-154">When a **\<Customer>** element node in the XML data file enters into scope, XML Bulk Load generates a record for the Cust table.</span></span> <span data-ttu-id="497c8-155">그러면 XML 대량 로드에서 필요한 열 값 (CustomerID, CompanyName 및 City) **\<CustomerID>** 을, **\<CompanyName>** 및 **\<City>** 자식 요소에서 범위에 입력 하는 자식 요소에 복사 합니다.</span><span class="sxs-lookup"><span data-stu-id="497c8-155">XML Bulk Load then copies the necessary column values (CustomerID, CompanyName, and City) from the **\<CustomerID>**, **\<CompanyName>**, and the **\<City>** child elements as these elements enter into scope.</span></span>  
  
-   <span data-ttu-id="497c8-156">**\<Order>** 요소 노드가 범위에 들어가면 XML 대량 로드는 CustOrder 테이블에 대 한 레코드를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="497c8-156">When an **\<Order>** element node enters into scope, XML Bulk Load generates a record for the CustOrder table.</span></span> <span data-ttu-id="497c8-157">XML 대량 로드는 **OrderID** 특성의 값을이 레코드에 복사 합니다.</span><span class="sxs-lookup"><span data-stu-id="497c8-157">XML Bulk Load copies the value of the **OrderID** attribute to this record.</span></span> <span data-ttu-id="497c8-158">CustomerID 열에 필요한 값은 **\<CustomerID>** 요소의 자식 요소에서 가져옵니다 **\<Customer>** .</span><span class="sxs-lookup"><span data-stu-id="497c8-158">The value required for the CustomerID column is obtained from the **\<CustomerID>** child element of the **\<Customer>** element.</span></span> <span data-ttu-id="497c8-159">XML 대량 로드는 요소에 Customerid 특성을 지정 하지 않은 경우에 지정 된 정보를 사용 하 여 `<sql:relationship>` 이 레코드 **CustomerID** 에 대 한 customerid 외래 키 값을 가져옵니다 **\<Order>** .</span><span class="sxs-lookup"><span data-stu-id="497c8-159">XML Bulk Load uses the information that is specified in `<sql:relationship>` to obtain the CustomerID foreign key value for this record, unless the **CustomerID** attribute was specified in the **\<Order>** element.</span></span> <span data-ttu-id="497c8-160">일반 규칙은 자식 요소가 외래 키 특성 값을 명시적으로 지정하는 경우 XML 대량 로드가 해당 값을 사용하고 지정된 `<sql:relationship>`을 사용하여 부모 요소에서 값을 가져오지 않는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="497c8-160">The general rule is that if the child element explicitly specifies a value for the foreign key attribute, XML Bulk Load uses that value and does not obtain the value from the parent element by using the specified `<sql:relationship>`.</span></span> <span data-ttu-id="497c8-161">이 **\<Order>** 요소 노드가 범위를 벗어나면 XML 대량 로드는 레코드를에 보낸 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 다음 동일한 방식으로 모든 후속 **\<Order>** 요소 노드를 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="497c8-161">As this **\<Order>** element node goes out of scope, XML Bulk Load sends the record to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] and then processes all the subsequent **\<Order>** element nodes in the same manner.</span></span>  
  
-   <span data-ttu-id="497c8-162">마지막으로 **\<Customer>** 요소 노드가 범위를 벗어났습니다.</span><span class="sxs-lookup"><span data-stu-id="497c8-162">Finally, the **\<Customer>** element node goes out of scope.</span></span> <span data-ttu-id="497c8-163">이 시점에서 XML 대량 로드가 고객 레코드를 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="497c8-163">At that time, XML Bulk Load sends the customer record to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="497c8-164">XML 대량 로드는 XML 데이터 스트림의 모든 후속 고객에 대해 이 프로세스를 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="497c8-164">XML Bulk Load follows this process for all the subsequent customers in the XML data stream.</span></span>  
  
 <span data-ttu-id="497c8-165">여기서 매핑 스키마에 대한 두 가지 사항을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="497c8-165">Here are two observations about the mapping schema:</span></span>  
  
-   <span data-ttu-id="497c8-166">스키마가 "포함" 규칙을 충족 하는 경우 (예: 고객과 관련 된 모든 데이터와 해당 주문이 연결 된 및 요소 노드의 범위 내에서 정의 된 **\<Customer>** 경우 **\<Order>** ) 대량 로드에 성공 합니다.</span><span class="sxs-lookup"><span data-stu-id="497c8-166">When the schema satisfies the "containment" rule (for example, all data that is associated with the customer and the order is defined within the scope of the associated **\<Customer>** and **\<Order>** element nodes), the bulk load succeeds.</span></span>  
  
-   <span data-ttu-id="497c8-167">요소를 설명 하는 경우 **\<Customer>** 해당 자식 요소가 적절 한 순서로 지정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="497c8-167">In describing the **\<Customer>** element, its child elements are specified in the appropriate order.</span></span> <span data-ttu-id="497c8-168">이 경우 자식 요소는 **\<CustomerID>** 자식 요소 앞에 지정 됩니다 **\<Order>** .</span><span class="sxs-lookup"><span data-stu-id="497c8-168">In this case, the **\<CustomerID>** child element is specified before the **\<Order>** child element.</span></span> <span data-ttu-id="497c8-169">즉, 입력 XML 데이터 파일에서 요소가 **\<CustomerID>** 범위에 들어가면 요소 값을 외래 키 값으로 사용할 수 있습니다 **\<Order>** .</span><span class="sxs-lookup"><span data-stu-id="497c8-169">This means that in the input XML data file, the **\<CustomerID>** element value is available as the foreign key value when the **\<Order>** element enters into scope.</span></span> <span data-ttu-id="497c8-170">키 특성이 먼저 지정되므로 이것은 "키 순서 지정 규칙"입니다.</span><span class="sxs-lookup"><span data-stu-id="497c8-170">The key attributes are specified first; this is the "Key Ordering Rule."</span></span>  
  
     <span data-ttu-id="497c8-171">자식 요소 다음에 자식 요소를 지정 하는 경우 **\<CustomerID>** **\<Order>** **\<Order>** 요소가 범위에 들어가면 값을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="497c8-171">If you specify the **\<CustomerID>** child element after the **\<Order>** child element, the value is not available when the **\<Order>** element enters into scope.</span></span> <span data-ttu-id="497c8-172">**\</Order>** 그런 다음 끝 태그를 읽으면 CustOrder 테이블의 레코드가 완료 된 것으로 간주 되 고 CustOrder 테이블에는 CustomerID 열에 대해 NULL 값이 있는 것으로 간주 되며이는 원하는 결과가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="497c8-172">When the **\</Order>** end tag is then read, the record for CustOrder table is considered complete and is inserted in the CustOrder table with a NULL value for the CustomerID column, which is not the desired result.</span></span>  
  
#### <a name="to-create-a-working-sample"></a><span data-ttu-id="497c8-173">작업 예제를 만들려면</span><span class="sxs-lookup"><span data-stu-id="497c8-173">To create a working sample</span></span>  
  
1.  <span data-ttu-id="497c8-174">이 예에서 제공하는 스키마를 SampleSchema.xml로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="497c8-174">Save the schema that is provided in this example as SampleSchema.xml.</span></span>  
  
2.  <span data-ttu-id="497c8-175">다음 테이블을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="497c8-175">Create these tables:</span></span>  
  
    ```  
    CREATE TABLE Cust (  
                  CustomerID     int         PRIMARY KEY,  
                  CompanyName    varchar(20) NOT NULL,  
                  City           varchar(20) DEFAULT 'Seattle')  
    GO  
    CREATE TABLE CustOrder (  
                 OrderID        int         PRIMARY KEY,  
                 CustomerID     int         FOREIGN KEY REFERENCES                                          Cust(CustomerID))  
    GO  
    ```  
  
3.  <span data-ttu-id="497c8-176">다음 예제 XML 입력 데이터를 SampleXMLData.xml로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="497c8-176">Save the following sample XML input data as SampleXMLData.xml:</span></span>  
  
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
  
4.  <span data-ttu-id="497c8-177">XML 대량 로드를 실행하려면 다음 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] VBScript(Visual Basic Scripting Edition) 예제(BulkLoad.vbs)를 저장한 다음 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="497c8-177">To execute XML Bulk Load, save and execute the following [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic Scripting Edition (VBScript) example (BulkLoad.vbs):</span></span>  
  
    ```  
    set objBL = CreateObject("SQLXMLBulkLoad.SQLXMLBulkload.4.0")  
    objBL.ConnectionString = "provider=SQLOLEDB;data source=localhost;database=tempdb;integrated security=SSPI"  
    objBL.ErrorLogFile = "c:\error.log"  
    objBL.CheckConstraints = True  
    objBL.Execute "c:\SampleSchema.xml", "c:\SampleXMLData.xml"  
    set objBL=Nothing  
    ```  
  
## <a name="exceptions-to-the-record-generation-rule"></a><span data-ttu-id="497c8-178">레코드 생성 규칙의 예외</span><span class="sxs-lookup"><span data-stu-id="497c8-178">Exceptions to the Record Generation Rule</span></span>  
 <span data-ttu-id="497c8-179">노드가 IDREF 또는 IDREFS 형식인 경우 XML 대량 로드는 범위가 시작될 때 노드에 대한 레코드를 생성하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="497c8-179">XML Bulk Load does not generate a record for a node when it enters into scope if that node is either an IDREF or IDREFS type.</span></span> <span data-ttu-id="497c8-180">따라서 스키마의 특정 위치에 레코드의 완전한 설명이 존재해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="497c8-180">You must make sure that a complete description of the record occurs at some place in the schema.</span></span> <span data-ttu-id="497c8-181">IDREFS 형식이 무시되는 것처럼 `dt:type="nmtokens"` 주석이 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="497c8-181">The `dt:type="nmtokens"` annotations are ignored just as the IDREFS type is ignored.</span></span>  
  
 <span data-ttu-id="497c8-182">예를 들어 및 요소를 설명 하는 다음 XSD 스키마를 살펴보세요 **\<Customer>** **\<Order>** .</span><span class="sxs-lookup"><span data-stu-id="497c8-182">For example, consider the following XSD schema that describes **\<Customer>** and **\<Order>** elements.</span></span> <span data-ttu-id="497c8-183">**\<Customer>** 요소는 IDREFS 유형의 **orderlist** 특성을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="497c8-183">The **\<Customer>** element includes an **OrderList** attribute of the IDREFS type.</span></span> <span data-ttu-id="497c8-184">`<sql:relationship>` 태그는 고객과 주문 목록 간의 일 대 다 관계를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="497c8-184">The `<sql:relationship>` tag specifies the one-to-many relationship between the customer and list of orders.</span></span>  
  
 <span data-ttu-id="497c8-185">스키마는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="497c8-185">This is the schema:</span></span>  
  
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
  
  <xsd:element name="Customers" sql:relation="Cust" >  
   <xsd:complexType>  
    <xsd:attribute name="CustomerID" type="xsd:integer" />  
    <xsd:attribute name="CompanyName" type="xsd:string" />  
    <xsd:attribute name="City" type="xsd:string" />  
    <xsd:attribute name="OrderList"   
                       type="xsd:IDREFS"   
                       sql:relation="CustOrder"   
                       sql:field="OrderID"  
                       sql:relationship="CustCustOrder" >  
    </xsd:attribute>  
  </xsd:complexType>  
 </xsd:element>  
  
  <xsd:element name="Order" sql:relation="CustOrder" >  
   <xsd:complexType>  
    <xsd:attribute name="OrderID" type="xsd:string" />  
    <xsd:attribute name="CustomerID" type="xsd:integer" />  
    <xsd:attribute name="OrderDate" type="xsd:date" />  
  </xsd:complexType>  
 </xsd:element>  
</xsd:schema>  
```  
  
 <span data-ttu-id="497c8-186">대량 로드는 IDREFS 유형의 노드를 무시 하므로 **Orderlist** 특성 노드가 범위에 들어가면 레코드를 생성할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="497c8-186">Because Bulk Load ignores the nodes of IDREFS type, there is no record generation when the **OrderList** attribute node enters into scope.</span></span> <span data-ttu-id="497c8-187">따라서 Orders 테이블에 주문 레코드를 추가하려면 스키마의 특정 위치에서 해당 주문을 설명해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="497c8-187">Therefore, if you want the order records added to the Orders table, you must describe those orders somewhere in the schema.</span></span> <span data-ttu-id="497c8-188">이 스키마에서 요소를 지정 하면 **\<Order>** XML 대량 로드에서 주문 레코드를 Orders 테이블에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="497c8-188">In this schema, specifying the **\<Order>** element ensures that XML Bulk Load adds the order records to the Orders table.</span></span> <span data-ttu-id="497c8-189">**\<Order>** 요소는 CustOrder 테이블에 대 한 레코드를 채우는 데 필요한 모든 특성을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="497c8-189">The **\<Order>** element describes all the attributes that are required to fill the record for the CustOrder table.</span></span>  
  
 <span data-ttu-id="497c8-190">요소의 **CustomerID** 및 **OrderID** 값이 **\<Customer>** 요소의 값과 일치 하는지 확인 해야 합니다 **\<Order>** .</span><span class="sxs-lookup"><span data-stu-id="497c8-190">You must ensure that the **CustomerID** and **OrderID** values in the **\<Customer>** element match the values in the **\<Order>** element.</span></span> <span data-ttu-id="497c8-191">참조 무결성을 유지하는 책임은 사용자에게 있습니다.</span><span class="sxs-lookup"><span data-stu-id="497c8-191">You are responsible for maintaining referential integrity.</span></span>  
  
#### <a name="to-test-a-working-sample"></a><span data-ttu-id="497c8-192">작업 예제를 테스트하려면</span><span class="sxs-lookup"><span data-stu-id="497c8-192">To test a working sample</span></span>  
  
1.  <span data-ttu-id="497c8-193">다음 테이블을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="497c8-193">Create these tables:</span></span>  
  
    ```  
    CREATE TABLE Cust (  
                  CustomerID     int          PRIMARY KEY,  
                  CompanyName    varchar(20)  NOT NULL,  
                  City           varchar(20)  DEFAULT 'Seattle')  
    GO  
    CREATE TABLE CustOrder (  
                  OrderID        varchar(10) PRIMARY KEY,  
                  CustomerID     int         FOREIGN KEY REFERENCES                                          Cust(CustomerID),  
                  OrderDate      datetime DEFAULT '2000-01-01')  
    GO  
    ```  
  
2.  <span data-ttu-id="497c8-194">이 예에서 제공하는 매핑 스키마를 SampleSchema.xml로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="497c8-194">Save the mapping schema provided in this example as SampleSchema.xml.</span></span>  
  
3.  <span data-ttu-id="497c8-195">다음 예제 XML 데이터를 SampleXMLData.xml로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="497c8-195">Save the following sample XML data as SampleXMLData.xml:</span></span>  
  
    ```  
    <ROOT>  
      <Customers CustomerID="1111" CompanyName="Sean Chai" City="NY"  
                 OrderList="Ord1 Ord2" />  
      <Customers CustomerID="1112" CompanyName="Dont Know" City="LA"  
                 OrderList="Ord3 Ord4" />  
      <Order OrderID="Ord1" CustomerID="1111" OrderDate="1999-01-01" />  
      <Order OrderID="Ord2" CustomerID="1111" OrderDate="1999-02-01" />  
      <Order OrderID="Ord3" CustomerID="1112" OrderDate="1999-03-01" />  
      <Order OrderID="Ord4" CustomerID="1112" OrderDate="1999-04-01" />  
    </ROOT>  
    ```  
  
4.  <span data-ttu-id="497c8-196">XML 대량 로드를 실행하려면 이 VBScript 예(SampleVB.vbs)를 저장한 다음 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="497c8-196">To execute XML Bulk Load, save and execute this VBScript example (SampleVB.vbs):</span></span>  
  
    ```  
    set objBL = CreateObject("SQLXMLBulkLoad.SQLXMLBulkload.4.0")  
    objBL.ConnectionString = "provider=SQLOLEDB;data source=localhost;database=tempdb;integrated security=SSPI"  
    objBL.ErrorLogFile = "c:\error.log"  
    objBL.CheckConstraints=True  
    objBL.Execute "c:\SampleSchema.xml", "c:\SampleXMLData.xml"  
    set objBL=Nothing  
    ```  
  
  
