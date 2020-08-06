---
title: Updategram에서 주석이 추가 된 매핑 스키마 지정 (SQLXML 4.0) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- annotated XSD schemas, updategrams
- data types [SQLXML], mapping schema in updategrams
- updategrams [SQLXML], annotated mapping schemas
- annotated XDR schemas, updategrams
- inverse attribute
- parent-child relationships [SQLXML]
- mapping-schema attribute
- mapping schema [SQLXML], updategrams
- sql:inverse
ms.assetid: 2e266ed9-4cfb-434a-af55-d0839f64bb9a
author: rothja
ms.author: jroth
ms.openlocfilehash: a181b3081b51cca160709703364c248e495e0214
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652735"
---
# <a name="specifying-an-annotated-mapping-schema-in-an-updategram-sqlxml-40"></a><span data-ttu-id="a8c5a-102">Updategram에 주석이 추가된 매핑 스키마 지정(SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="a8c5a-102">Specifying an Annotated Mapping Schema in an Updategram (SQLXML 4.0)</span></span>
  <span data-ttu-id="a8c5a-103">이 항목에서는 Updategram에 지정된 매핑 스키마(XSD 또는 XDR)를 사용하여 업데이트를 처리하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="a8c5a-103">This topic explains how the mapping schema (XSD or XDR) that is specified in an updategram is used to process the updates.</span></span> <span data-ttu-id="a8c5a-104">Updategram에서 updategram의 요소와 특성을의 테이블과 열에 매핑하는 데 사용할 주석이 추가 된 매핑 스키마의 이름을 제공할 수 있습니다 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="a8c5a-104">In an updategram, you can provide the name of an annotated mapping schema to use in mapping the elements and attributes in the updategram to tables and columns in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="a8c5a-105">Updategram에 매핑 스키마가 지정되어 있으면 Updategram에 지정된 요소 및 특성 이름이 매핑 스키마의 요소와 특성에 매핑되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8c5a-105">When a mapping schema is specified in an updategram, the element and attribute names that are specified in the updategram must map to the elements and attributes in the mapping schema.</span></span>  
  
 <span data-ttu-id="a8c5a-106">매핑 스키마를 지정 하려면 요소의 특성을 사용 `mapping-schema` **\<sync>** 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8c5a-106">To specify a mapping schema, you use the `mapping-schema` attribute of the **\<sync>** element.</span></span> <span data-ttu-id="a8c5a-107">다음 예에서는 두 개의 Updategram을 보여 줍니다. 하나는 단순한 매핑 스키마를 사용하고 다른 하나는 더 복잡한 스키마를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="a8c5a-107">The following examples show two updategrams: one that uses a simple mapping schema, and one that uses a more complex schema.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a8c5a-108">이 설명서에서는 사용자가 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 의 템플릿 및 매핑 스키마 지원에 대해 잘 알고 있다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="a8c5a-108">This documentation assumes that you are familiar with templates and mapping schema support in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="a8c5a-109">자세한 내용은 주석이 추가 된 [XSD 스키마 소개 &#40;SQLXML 4.0&#41;](../../sqlxml/annotated-xsd-schemas/introduction-to-annotated-xsd-schemas-sqlxml-4-0.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="a8c5a-109">For more information, see [Introduction to Annotated XSD Schemas &#40;SQLXML 4.0&#41;](../../sqlxml/annotated-xsd-schemas/introduction-to-annotated-xsd-schemas-sqlxml-4-0.md).</span></span> <span data-ttu-id="a8c5a-110">XDR을 사용 하는 레거시 응용 프로그램의 경우 [SQLXML 4.0&#41;에서 사용 되지 &#40;주석이 추가 된 Xdr 스키마 ](../../sqlxml/annotated-xsd-schemas/annotated-xdr-schemas-deprecated-in-sqlxml-4-0.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="a8c5a-110">For legacy applications that use XDR, see [Annotated XDR Schemas &#40;Deprecated in SQLXML 4.0&#41;](../../sqlxml/annotated-xsd-schemas/annotated-xdr-schemas-deprecated-in-sqlxml-4-0.md).</span></span>  
  
## <a name="dealing-with-data-types"></a><span data-ttu-id="a8c5a-111">데이터 형식 처리</span><span class="sxs-lookup"><span data-stu-id="a8c5a-111">Dealing with Data Types</span></span>  
 <span data-ttu-id="a8c5a-112">스키마가 `image` 을 `binary` 사용 하 여, 또는 `varbinary` [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 데이터 형식을 지정 하 `sql:datatype` 고 xml 데이터 형식을 지정 하지 않는 경우 updategram는 xml 데이터 형식이 인 `binary base 64` 것으로 가정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8c5a-112">If the schema specifies the `image`, `binary`, or `varbinary`[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] data type (by using `sql:datatype`) and does not specify an XML data type, the updategram assumes that the XML data type is `binary base 64`.</span></span> <span data-ttu-id="a8c5a-113">데이터가 `bin.base` 유형인 경우 명시적으로 유형(`dt:type=bin.base` 또는 `type="xsd:hexBinary"`)을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8c5a-113">If your data is `bin.base` type, you must explicitly specify the type (`dt:type=bin.base` or `type="xsd:hexBinary"`).</span></span>  
  
 <span data-ttu-id="a8c5a-114">스키마에서 `dateTime`, `date` 또는 `time` XSD 데이터 형식을 지정하는 경우 `sql:datatype="dateTime"`을 사용하여 해당 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 데이터 형식도 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8c5a-114">If the schema specifies the `dateTime`, `date`, or `time` XSD data type, you must also specify the corresponding [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] data type by using `sql:datatype="dateTime"`.</span></span>  
  
 <span data-ttu-id="a8c5a-115">형식의 매개 변수를 처리할 때 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] `money` `sql:datatype="money"` 매핑 스키마의 적절 한 노드에 명시적으로를 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8c5a-115">When handling parameters of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] `money` type, you must explicitly specify `sql:datatype="money"` on the appropriate node in the mapping schema.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="a8c5a-116">예</span><span class="sxs-lookup"><span data-stu-id="a8c5a-116">Examples</span></span>  
 <span data-ttu-id="a8c5a-117">다음 예제를 사용 하 여 작업 예제를 만들려면 [SQLXML 예를 실행 하기 위한 요구 사항](../../sqlxml/requirements-for-running-sqlxml-examples.md)에 지정 된 요구 사항을 충족 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8c5a-117">To create working samples using the following examples, you must meet the requirements specified in [Requirements for Running SQLXML Examples](../../sqlxml/requirements-for-running-sqlxml-examples.md).</span></span>  
  
### <a name="a-creating-an-updategram-with-a-simple-mapping-schema"></a><span data-ttu-id="a8c5a-118">A.</span><span class="sxs-lookup"><span data-stu-id="a8c5a-118">A.</span></span> <span data-ttu-id="a8c5a-119">단순한 매핑 스키마를 사용하여 Updategram 만들기</span><span class="sxs-lookup"><span data-stu-id="a8c5a-119">Creating an updategram with a simple mapping schema</span></span>  
 <span data-ttu-id="a8c5a-120">다음 XSD 스키마 (SampleSchema.xml)는 **\<Customer>** 요소를 Sales. Customer 테이블에 매핑하는 매핑 스키마입니다.</span><span class="sxs-lookup"><span data-stu-id="a8c5a-120">The following XSD schema (SampleSchema.xml) is a mapping schema that maps the **\<Customer>** element to the Sales.Customer table:</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:element name="Customer" sql:relation="Sales.Customer" >  
   <xsd:complexType>  
        <xsd:attribute name="CustID"    
                       sql:field="CustomerID"   
                       type="xsd:string" />  
        <xsd:attribute name="RegionID"    
                       sql:field="TerritoryID"    
                       type="xsd:string" />  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
 <span data-ttu-id="a8c5a-121">다음 Updategram은 Sales.Customer 테이블에 레코드를 삽입하고 이전 매핑 스키마를 사용하여 이 데이터를 테이블에 올바르게 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="a8c5a-121">The following updategram inserts a record into the Sales.Customer table and relies on the previous mapping schema to properly map this data to the table.</span></span> <span data-ttu-id="a8c5a-122">Updategram는 스키마에 정의 된 것과 같은 요소 이름를 사용 합니다 **\<Customer>** .</span><span class="sxs-lookup"><span data-stu-id="a8c5a-122">Notice that the updategram uses the same element name, **\<Customer>**, as defined in the schema.</span></span> <span data-ttu-id="a8c5a-123">Updategram에서 특정 스키마를 지정하기 때문에 이 작업은 필수입니다.</span><span class="sxs-lookup"><span data-stu-id="a8c5a-123">This is mandatory because the updategram specifies a particular schema.</span></span>  
  
##### <a name="to-test-the-updategram"></a><span data-ttu-id="a8c5a-124">Updategram을 테스트하려면</span><span class="sxs-lookup"><span data-stu-id="a8c5a-124">To test the updategram</span></span>  
  
1.  <span data-ttu-id="a8c5a-125">위 스키마 코드를 복사한 후 텍스트 파일에 붙여넣습니다.</span><span class="sxs-lookup"><span data-stu-id="a8c5a-125">Copy the schema code above and paste it into a text file.</span></span> <span data-ttu-id="a8c5a-126">파일을 SampleUpdateSchema.xml로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="a8c5a-126">Save the file as SampleUpdateSchema.xml.</span></span>  
  
2.  <span data-ttu-id="a8c5a-127">아래 Updategram 템플릿을 복사한 후 텍스트 파일에 붙여넣습니다.</span><span class="sxs-lookup"><span data-stu-id="a8c5a-127">Copy the updategram template below and paste it into a text file.</span></span> <span data-ttu-id="a8c5a-128">파일을 SampleUpdateSchema.xml을 저장한 디렉터리와 같은 디렉터리에 SampleUpdategram.xml로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="a8c5a-128">Save the file as SampleUpdategram.xml in the same directory where you saved SampleUpdateSchema.xml.</span></span>  
  
    ```  
    <ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
      <updg:sync mapping-schema="SampleUpdateSchema.xml">  
        <updg:before>  
          <Customer CustID="1" RegionID="1"  />  
        </updg:before>  
        <updg:after>  
          <Customer CustID="1" RegionID="2" />  
        </updg:after>  
      </updg:sync>  
    </ROOT>  
    ```  
  
     <span data-ttu-id="a8c5a-129">매핑 스키마(SampleUpdateSchema.xml)에 대해 지정된 디렉터리 경로는 템플릿이 저장된 디렉터리에 상대적입니다.</span><span class="sxs-lookup"><span data-stu-id="a8c5a-129">The directory path specified for the mapping schema (SampleUpdateSchema.xml) is relative to the directory where the template is saved.</span></span> <span data-ttu-id="a8c5a-130">또한 다음과 같이 절대 경로를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8c5a-130">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\SqlXmlTest\SampleUpdateSchema.xml"  
    ```  
  
3.  <span data-ttu-id="a8c5a-131">SQLXML 4.0 테스트 스크립트(Sqlxml4test.vbs)를 만든 다음 이 스크립트를 사용하여 템플릿을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="a8c5a-131">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="a8c5a-132">자세한 내용은 [ADO를 사용 하 여 SQLXML 4.0 쿼리 실행](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="a8c5a-132">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="a8c5a-133">다음은 동등한 XDR 스키마입니다.</span><span class="sxs-lookup"><span data-stu-id="a8c5a-133">This is the equivalent XDR schema:</span></span>  
  
```  
<?xml version="1.0" ?>  
   <Schema xmlns="urn:schemas-microsoft-com:xml-data"   
         xmlns:dt="urn:schemas-microsoft-com:datatypes"   
         xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
     <ElementType name="Customer" sql:relation="Sales.Customer" >  
       <AttributeType name="CustID" />  
       <AttributeType name="RegionID" />  
  
       <attribute type="CustID" sql:field="CustomerID" />  
       <attribute type="RegionID" sql:field="TerritoryID" />  
     </ElementType>  
   </Schema>   
```  
  
### <a name="b-inserting-a-record-by-using-the-parent-child-relationship-specified-in-the-mapping-schema"></a><span data-ttu-id="a8c5a-134">B.</span><span class="sxs-lookup"><span data-stu-id="a8c5a-134">B.</span></span> <span data-ttu-id="a8c5a-135">매핑 스키마에 지정된 부모-자식 관계를 사용하여 레코드 삽입</span><span class="sxs-lookup"><span data-stu-id="a8c5a-135">Inserting a record by using the parent-child relationship specified in the mapping schema</span></span>  
 <span data-ttu-id="a8c5a-136">스키마 요소를 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8c5a-136">Schema elements can be related.</span></span> <span data-ttu-id="a8c5a-137">**\<sql:relationship>** 요소는 스키마 요소 간의 부모-자식 관계를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8c5a-137">The **\<sql:relationship>** element specifies the parent-child relationship between the schema elements.</span></span> <span data-ttu-id="a8c5a-138">이 정보는 기본 키/외래 키 관계가 있는 해당 테이블을 업데이트하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="a8c5a-138">This information is used to update corresponding tables that have primary-key/foreign-key relationship.</span></span>  
  
 <span data-ttu-id="a8c5a-139">다음 매핑 스키마 (SampleSchema.xml)는 및 라는 두 개의 요소로 구성 됩니다 **\<Order>** **\<OD>** .</span><span class="sxs-lookup"><span data-stu-id="a8c5a-139">The following mapping schema (SampleSchema.xml) consists of two elements, **\<Order>** and **\<OD>**:</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
<xsd:annotation>  
  <xsd:appinfo>  
    <sql:relationship name="OrderOD"  
          parent="Sales.SalesOrderHeader"  
          parent-key="SalesOrderID"  
          child="Sales.SalesOrderDetail"  
          child-key="SalesOrderID" />  
  </xsd:appinfo>  
</xsd:annotation>  
  
  <xsd:element name="Order" sql:relation="Sales.SalesOrderHeader" >  
   <xsd:complexType>  
     <xsd:sequence>  
        <xsd:element name="OD"   
                     sql:relation="Sales.SalesOrderDetail"  
                     sql:relationship="OrderOD" >  
           <xsd:complexType>  
              <xsd:attribute name="SalesOrderID"   type="xsd:integer" />  
              <xsd:attribute name="ProductID" type="xsd:integer" />  
             <xsd:attribute name="UnitPrice"  type="xsd:decimal" />  
             <xsd:attribute name="OrderQty"   type="xsd:integer" />  
             <xsd:attribute name="UnitPriceDiscount"   type="xsd:decimal" />  
  
           </xsd:complexType>  
        </xsd:element>  
     </xsd:sequence>  
        <xsd:attribute name="CustomerID"   type="xsd:string" />   
        <xsd:attribute name="SalesOrderID"  type="xsd:integer" />  
        <xsd:attribute name="OrderDate"  type="xsd:date" />  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
 <span data-ttu-id="a8c5a-140">다음 updategram에서는이 XSD 스키마를 사용 하 여 주문 43860에 대해 새 주문 정보 레코드 ( **\<OD>** 블록의 요소)를 추가 합니다 **\<after>** .</span><span class="sxs-lookup"><span data-stu-id="a8c5a-140">The following updategram uses this XSD schema to add a new order detail record (an **\<OD>** element in the **\<after>** block) for order 43860.</span></span> <span data-ttu-id="a8c5a-141">`mapping-schema` 특성은 Updategram의 매핑 스키마를 지정하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="a8c5a-141">The `mapping-schema` attribute is used to specify the mapping schema in the updategram.</span></span>  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
  <updg:sync mapping-schema="SampleUpdateSchema.xml" >  
    <updg:before>  
       <Order SalesOrderID="43860" />  
    </updg:before>  
    <updg:after>  
      <Order SalesOrderID="43860" >  
           <OD ProductID="753" UnitPrice="$10.00"  
               Quantity="5" Discount="0.0" />  
      </Order>  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
##### <a name="to-test-the-updategram"></a><span data-ttu-id="a8c5a-142">Updategram을 테스트하려면</span><span class="sxs-lookup"><span data-stu-id="a8c5a-142">To test the updategram</span></span>  
  
1.  <span data-ttu-id="a8c5a-143">위 스키마 코드를 복사한 후 텍스트 파일에 붙여넣습니다.</span><span class="sxs-lookup"><span data-stu-id="a8c5a-143">Copy the schema code above and paste it into a text file.</span></span> <span data-ttu-id="a8c5a-144">파일을 SampleUpdateSchema.xml로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="a8c5a-144">Save the file as SampleUpdateSchema.xml.</span></span>  
  
2.  <span data-ttu-id="a8c5a-145">위 Updategram 템플릿을 복사한 후 텍스트 파일에 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="a8c5a-145">Copy the updategram template above and paste it into a text file.</span></span> <span data-ttu-id="a8c5a-146">파일을 SampleUpdateSchema.xml을 저장한 디렉터리와 같은 디렉터리에 SampleUpdategram.xml로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="a8c5a-146">Save the file as SampleUpdategram.xml in the same directory where you saved SampleUpdateSchema.xml.</span></span>  
  
     <span data-ttu-id="a8c5a-147">매핑 스키마(SampleUpdateSchema.xml)에 대해 지정된 디렉터리 경로는 템플릿이 저장된 디렉터리에 상대적입니다.</span><span class="sxs-lookup"><span data-stu-id="a8c5a-147">The directory path specified for the mapping schema (SampleUpdateSchema.xml) is relative to the directory where the template is saved.</span></span> <span data-ttu-id="a8c5a-148">또한 다음과 같이 절대 경로를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8c5a-148">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\SqlXmlTest\SampleUpdateSchema.xml"  
    ```  
  
3.  <span data-ttu-id="a8c5a-149">SQLXML 4.0 테스트 스크립트(Sqlxml4test.vbs)를 만든 다음 이 스크립트를 사용하여 템플릿을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="a8c5a-149">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="a8c5a-150">자세한 내용은 [ADO를 사용 하 여 SQLXML 4.0 쿼리 실행](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="a8c5a-150">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="a8c5a-151">다음은 동등한 XDR 스키마입니다.</span><span class="sxs-lookup"><span data-stu-id="a8c5a-151">This is the equivalent XDR schema:</span></span>  
  
```  
<?xml version="1.0" ?>  
<Schema xmlns="urn:schemas-microsoft-com:xml-data"  
        xmlns:dt="urn:schemas-microsoft-com:datatypes"  
        xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  
<ElementType name="OD" sql:relation="Sales.SalesOrderDetail" >  
    <AttributeType name="SalesOrderID" />  
    <AttributeType name="ProductID" />  
    <AttributeType name="UnitPrice"  dt:type="fixed.14.4" />  
    <AttributeType name="OrderQty" />  
    <AttributeType name="UnitPriceDiscount" />  
  
    <attribute type="SalesOrderID" />  
    <attribute type="ProductID" />  
    <attribute type="UnitPrice" />  
    <attribute type="OrderQty" />  
    <attribute type="UnitPriceDiscount" />  
</ElementType>  
  
<ElementType name="Order" sql:relation="Sales.SalesOrderHeader" >  
    <AttributeType name="CustomerID" />  
    <AttributeType name="SalesOrderID" />  
    <AttributeType name="OrderDate" />  
  
    <attribute type="CustomerID" />  
    <attribute type="SalesOrderID" />  
    <attribute type="OrderDate" />  
    <element type="OD" >  
             <sql:relationship   
                   key-relation="Sales.SalesOrderHeader"  
                   key="SalesOrderID"  
                   foreign-key="SalesOrderID"  
                   foreign-relation="Sales.SalesOrderDetail" />  
    </element>  
</ElementType>  
</Schema>  
```  
  
### <a name="c-inserting-a-record-by-using-the-parent-child-relationship-and-inverse-annotation-specified-in-the-xsd-schema"></a><span data-ttu-id="a8c5a-152">C.</span><span class="sxs-lookup"><span data-stu-id="a8c5a-152">C.</span></span> <span data-ttu-id="a8c5a-153">XSD 스키마에 지정된 부모-자식 관계 및 inverse 주석을 사용하여 레코드 삽입</span><span class="sxs-lookup"><span data-stu-id="a8c5a-153">Inserting a record by using the parent-child relationship and inverse annotation specified in the XSD schema</span></span>  
 <span data-ttu-id="a8c5a-154">이 예에서는 Updategram 논리가 XSD에 지정된 부모-자식 관계를 사용하여 업데이트를 처리하는 방법 및 `inverse` 주석이 사용되는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="a8c5a-154">This example illustrates how the updategram logic uses the parent-child relationship specified in the XSD to process updates, and how the `inverse` annotation is used.</span></span> <span data-ttu-id="a8c5a-155">주석에 대 한 자세한 내용은 sql: `inverse` [relationship에 sql: 역함수 지정 &#40;SQLXML 4.0&#41;](../../sqlxml-annotated-xsd-schemas-using/specifying-the-sql-inverse-attribute-on-sql-relationship-sqlxml-4-0.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="a8c5a-155">For more information about the `inverse` annotation, see [Specifying the sql:inverse Attribute on sql:relationship &#40;SQLXML 4.0&#41;](../../sqlxml-annotated-xsd-schemas-using/specifying-the-sql-inverse-attribute-on-sql-relationship-sqlxml-4-0.md).</span></span>  
  
 <span data-ttu-id="a8c5a-156">이 예에서는 다음 테이블이 **tempdb** 데이터베이스에 있다고 가정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8c5a-156">This example assumes that the following tables are in the **tempdb** database:</span></span>  
  
-   <span data-ttu-id="a8c5a-157">`Cust (CustomerID, CompanyName)`. 여기서 `CustomerID`는 기본 키입니다.</span><span class="sxs-lookup"><span data-stu-id="a8c5a-157">`Cust (CustomerID, CompanyName)`, where `CustomerID` is the primary key</span></span>  
  
-   <span data-ttu-id="a8c5a-158">`Ord (OrderID, CustomerID)`. 여기서 `CustomerID`는 `CustomerID` 테이블의 `Cust` 기본 키를 참조하는 외래 키입니다.</span><span class="sxs-lookup"><span data-stu-id="a8c5a-158">`Ord (OrderID, CustomerID)`, where `CustomerID` is a foreign key that refers to the `CustomerID` primary key in the `Cust` table.</span></span>  
  
 <span data-ttu-id="a8c5a-159">Updategram은 다음 XSD 스키마를 사용하여 Cust 및 Ord 테이블에 레코드를 삽입합니다.</span><span class="sxs-lookup"><span data-stu-id="a8c5a-159">The updategram uses the following XSD schema to insert records into the Cust and Ord tables :</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
<xsd:annotation>  
  <xsd:appinfo>  
       <sql:relationship name="OrdCust" inverse="true"  
                  parent="Ord"  
                  parent-key="CustomerID"  
                  child-key="CustomerID"  
                  child="Cust"/>  
  </xsd:appinfo>  
</xsd:annotation>  
  
<xsd:element name="Order" sql:relation="Ord">  
  <xsd:complexType>  
    <xsd:sequence>  
      <xsd:element ref="Customer" sql:relationship="OrdCust"/>  
    </xsd:sequence>  
    <xsd:attribute name="OrderID"   type="xsd:int"/>  
    <xsd:attribute name="CustomerID" type="xsd:string"/>  
  </xsd:complexType>  
</xsd:element>  
  
<xsd:element name="Customer" sql:relation="Cust">  
  <xsd:complexType>  
     <xsd:attribute name="CustomerID"  type="xsd:string"/>  
    <xsd:attribute name="CompanyName" type="xsd:string"/>  
  </xsd:complexType>  
</xsd:element>  
  
</xsd:schema>  
```  
  
 <span data-ttu-id="a8c5a-160">이 예제의 XSD 스키마에는 **\<Customer>** 및 **\<Order>** 요소가 있으며 두 요소 간의 부모-자식 관계를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8c5a-160">The XSD schema in this example has **\<Customer>** and **\<Order>** elements, and it specifies a parent-child relationship between the two elements.</span></span> <span data-ttu-id="a8c5a-161">**\<Order>** 부모 요소 및를 **\<Customer>** 자식 요소로 식별 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8c5a-161">It identifies **\<Order>** as the parent element and **\<Customer>** as the child element.</span></span>  
  
 <span data-ttu-id="a8c5a-162">Updategram 처리 논리에서는 부모-자식 관계에 대한 정보를 사용하여 레코드가 테이블에 삽입되는 순서를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="a8c5a-162">The updategram processing logic uses the information about the parent-child relationship to determine the order in which records are inserted into tables.</span></span> <span data-ttu-id="a8c5a-163">이 예에서 updategram 논리는 먼저 Ord 테이블에 레코드를 삽입 한 다음 (가 자식 이기 때문에) **\<Order>** Cust 테이블에 레코드를 삽입 하려고 시도 합니다 **\<Customer>** .</span><span class="sxs-lookup"><span data-stu-id="a8c5a-163">In this example, the updategram logic first attempts to insert a record into the Ord table (because **\<Order>** is the parent) and then attempts to insert a record into the Cust table (because **\<Customer>** is the child).</span></span> <span data-ttu-id="a8c5a-164">하지만 데이터베이스 테이블 스키마에 포함된 기본 키/외래 키 정보 때문에 이 삽입 작업을 수행하면 데이터베이스에서 외래 키 위반이 발생하고 삽입이 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="a8c5a-164">However, because of the primary key/foreign key information that is contained in the database table schema, this insert operation causes a foreign key violation in the database and the insert fails.</span></span>  
  
 <span data-ttu-id="a8c5a-165">업데이트 작업 중에 부모-자식 관계를 반대로 updategram 논리에 지시 하려면 `inverse` 요소에 주석이 지정 됩니다 **\<relationship>** .</span><span class="sxs-lookup"><span data-stu-id="a8c5a-165">To instruct the updategram logic to reverse the parent-child relationship during the update operation, the `inverse` annotation is specified on the **\<relationship>** element.</span></span> <span data-ttu-id="a8c5a-166">그 결과, 레코드가 먼저 Cust 테이블에 추가된 다음 Ord 테이블에 추가되어 작업이 성공합니다.</span><span class="sxs-lookup"><span data-stu-id="a8c5a-166">As a result, records are added first in the Cust table and then in the Ord table, and the operation succeeds.</span></span>  
  
 <span data-ttu-id="a8c5a-167">다음 Updategram은 지정한 XSD 스키마를 사용하여 Ord 테이블에 주문(OrderID=2)을 삽입하고 Cust 테이블에 고객(CustomerID='AAAAA')을 삽입합니다.</span><span class="sxs-lookup"><span data-stu-id="a8c5a-167">The following updategram inserts an order (OrderID=2) in the Ord table and a customer (CustomerID='AAAAA') in the Cust table by using the specified XSD schema:</span></span>  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
  <updg:sync mapping-schema="SampleUpdateSchema.xml" >  
    <updg:before/>  
    <updg:after>  
      <Order OrderID="2" CustomerID="AAAAA" >  
        <Customer CustomerID="AAAAA" CompanyName="AAAAA Company" />  
      </Order>  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
##### <a name="to-test-the-updategram"></a><span data-ttu-id="a8c5a-168">Updategram을 테스트하려면</span><span class="sxs-lookup"><span data-stu-id="a8c5a-168">To test the updategram</span></span>  
  
1.  <span data-ttu-id="a8c5a-169">**Tempdb** 데이터베이스에 다음 테이블을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="a8c5a-169">Create these tables in the **tempdb** database:</span></span>  
  
    ```  
    USE tempdb  
    CREATE TABLE Cust(CustomerID varchar(5) primary key,   
                      CompanyName varchar(20))  
    GO  
    CREATE TABLE Ord (OrderID int primary key,   
                      CustomerID varchar(5) references Cust(CustomerID))  
    GO  
    ```  
  
2.  <span data-ttu-id="a8c5a-170">위 스키마 코드를 복사한 후 텍스트 파일에 붙여넣습니다.</span><span class="sxs-lookup"><span data-stu-id="a8c5a-170">Copy the schema code above and paste it into a text file.</span></span> <span data-ttu-id="a8c5a-171">파일을 SampleUpdateSchema.xml로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="a8c5a-171">Save the file as SampleUpdateSchema.xml.</span></span>  
  
3.  <span data-ttu-id="a8c5a-172">위 Updategram 템플릿을 복사한 후 텍스트 파일에 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="a8c5a-172">Copy the updategram template above and paste it into a text file.</span></span> <span data-ttu-id="a8c5a-173">파일을 SampleUpdateSchema.xml을 저장한 디렉터리와 같은 디렉터리에 SampleUpdategram.xml로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="a8c5a-173">Save the file as SampleUpdategram.xml in the same directory where you saved SampleUpdateSchema.xml.</span></span>  
  
     <span data-ttu-id="a8c5a-174">매핑 스키마(SampleUpdateSchema.xml)에 대해 지정된 디렉터리 경로는 템플릿이 저장된 디렉터리에 상대적입니다.</span><span class="sxs-lookup"><span data-stu-id="a8c5a-174">The directory path specified for the mapping schema (SampleUpdateSchema.xml) is relative to the directory where the template is saved.</span></span> <span data-ttu-id="a8c5a-175">또한 다음과 같이 절대 경로를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8c5a-175">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\SqlXmlTest\SampleUpdateSchema.xml"  
    ```  
  
4.  <span data-ttu-id="a8c5a-176">SQLXML 4.0 테스트 스크립트(Sqlxml4test.vbs)를 만든 다음 이 스크립트를 사용하여 템플릿을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="a8c5a-176">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="a8c5a-177">자세한 내용은 [ADO를 사용 하 여 SQLXML 4.0 쿼리 실행](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="a8c5a-177">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8c5a-178">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a8c5a-178">See Also</span></span>  
 [<span data-ttu-id="a8c5a-179">Updategram 보안 고려 사항은 SQLXML 4.0&#41;&#40;</span><span class="sxs-lookup"><span data-stu-id="a8c5a-179">Updategram Security Considerations &#40;SQLXML 4.0&#41;</span></span>](../security/updategram-security-considerations-sqlxml-4-0.md)  
  
  
