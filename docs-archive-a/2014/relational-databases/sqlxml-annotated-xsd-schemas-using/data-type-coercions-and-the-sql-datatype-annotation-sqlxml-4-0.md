---
title: '데이터 형식 강제 변환 및 sql: datatype 주석 (SQLXML 4.0) | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- mapping data types [SQLXML]
- type attribute
- sql:datatype
- data types [SQLXML], converting
- annotated XSD schemas, mapping data types
- xsd:type
- datatype annotation
- converting data types [SQLXML]
- data types [SQLXML], mapping data types
- XSD schemas [SQLXML], mapping data types
ms.assetid: db192105-e8aa-4392-b812-9d727918c005
author: rothja
ms.author: jroth
ms.openlocfilehash: 22f1b0af93e3b596d74bc107ab6947b9855a2cf6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650900"
---
# <a name="data-type-coercions-and-the-sqldatatype-annotation-sqlxml-40"></a><span data-ttu-id="69a76-102">데이터 형식 강제 변환 및 sql:datatype 주석(SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="69a76-102">Data Type Coercions and the sql:datatype Annotation (SQLXML 4.0)</span></span>
  <span data-ttu-id="69a76-103">XSD 스키마에서 `xsd:type` 특성은 요소 또는 특성의 XSD 데이터 형식을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="69a76-103">In an XSD schema, the `xsd:type` attribute specifies the XSD data type of an element or attribute.</span></span> <span data-ttu-id="69a76-104">XSD 스키마를 사용하여 데이터베이스에서 데이터를 추출할 경우 지정된 데이터 형식이 데이터 서식 지정에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="69a76-104">When an XSD schema is used to extract data from the database, the data type specified is used to format the data.</span></span>  
  
 <span data-ttu-id="69a76-105">`sql:datatype` 주석을 사용하면 스키마에 XSD 형식을 지정할 수 있을 뿐만 아니라 Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터 형식도 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="69a76-105">In addition to specifying an XSD type in a schema, you can also specify a Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data type by using the `sql:datatype` annotation.</span></span> <span data-ttu-id="69a76-106">`xsd:type` 및 `sql:datatype` 특성은 XSD 데이터 형식과 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터 형식 간의 매핑을 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="69a76-106">The `xsd:type` and `sql:datatype` attributes control the mapping between XSD data types and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data types.</span></span>  
  
## <a name="xsdtype-attribute"></a><span data-ttu-id="69a76-107">xsd:type 특성</span><span class="sxs-lookup"><span data-stu-id="69a76-107">xsd:type Attribute</span></span>  
 <span data-ttu-id="69a76-108">`xsd:type` 특성을 사용하여 열에 매핑되는 특성이나 요소의 XML 데이터 형식을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="69a76-108">You can use the `xsd:type` attribute to specify the XML data type of an attribute or element that maps to a column.</span></span> <span data-ttu-id="69a76-109">`xsd:type`은 서버에서 반환되는 문서뿐만 아니라 실행되는 XPath 쿼리에도 영향을 미칩니다.</span><span class="sxs-lookup"><span data-stu-id="69a76-109">The `xsd:type` affects the document that is returned from the server and also the XPath query that is executed.</span></span> <span data-ttu-id="69a76-110">`xsd:type`이 포함된 매핑 스키마를 기준으로 XPath 쿼리가 실행될 때 XPath는 지정된 데이터 형식을 사용하여 쿼리를 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="69a76-110">When an XPath query is executed against a mapping schema that contains `xsd:type`, XPath uses the specified data type when it processes the query.</span></span> <span data-ttu-id="69a76-111">XPath를 사용 하는 방법에 대 한 자세한 내용은 `xsd:type` [&#40;SQLXML 4.0&#41;XSD 데이터 형식을 Xpath 데이터 형식에 매핑 ](../sqlxml-annotated-xsd-schemas-xpath-queries/xpath-data-types-sqlxml-4-0.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="69a76-111">For more information about how XPath uses `xsd:type`, see [Mapping XSD Data Types to XPath Data Types &#40;SQLXML 4.0&#41;](../sqlxml-annotated-xsd-schemas-xpath-queries/xpath-data-types-sqlxml-4-0.md).</span></span>  
  
 <span data-ttu-id="69a76-112">반환된 문서에서 모든 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터 형식은 문자열 표현으로 변환됩니다.</span><span class="sxs-lookup"><span data-stu-id="69a76-112">In a returned document, all [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data types are converted into string representations.</span></span> <span data-ttu-id="69a76-113">일부 데이터 형식에는 추가적인 변환이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="69a76-113">Some data types require additional conversions.</span></span> <span data-ttu-id="69a76-114">다음 표에서는 다양한 `xsd:type` 값에 사용되는 변환을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="69a76-114">The following table lists the conversions that are used for various `xsd:type` values.</span></span>  
  
|<span data-ttu-id="69a76-115">XSD 데이터 형식</span><span class="sxs-lookup"><span data-stu-id="69a76-115">XSD data type</span></span>|<span data-ttu-id="69a76-116">SQL Server 변환</span><span class="sxs-lookup"><span data-stu-id="69a76-116">SQL Server conversion</span></span>|  
|-------------------|---------------------------|  
|<span data-ttu-id="69a76-117">부울</span><span class="sxs-lookup"><span data-stu-id="69a76-117">Boolean</span></span>|<span data-ttu-id="69a76-118">CONVERT(bit, COLUMN)</span><span class="sxs-lookup"><span data-stu-id="69a76-118">CONVERT(bit, COLUMN)</span></span>|  
|<span data-ttu-id="69a76-119">Date</span><span class="sxs-lookup"><span data-stu-id="69a76-119">Date</span></span>|<span data-ttu-id="69a76-120">LEFT(CONVERT(nvarchar(4000), COLUMN, 126), 10)</span><span class="sxs-lookup"><span data-stu-id="69a76-120">LEFT(CONVERT(nvarchar(4000), COLUMN, 126), 10)</span></span>|  
|<span data-ttu-id="69a76-121">decimal</span><span class="sxs-lookup"><span data-stu-id="69a76-121">decimal</span></span>|<span data-ttu-id="69a76-122">CONVERT(money, COLUMN)</span><span class="sxs-lookup"><span data-stu-id="69a76-122">CONVERT(money, COLUMN)</span></span>|  
|<span data-ttu-id="69a76-123">id/idref/idrefs</span><span class="sxs-lookup"><span data-stu-id="69a76-123">id/idref/idrefs</span></span>|<span data-ttu-id="69a76-124">id-prefix + CONVERT(nvarchar(4000), COLUMN, 126)</span><span class="sxs-lookup"><span data-stu-id="69a76-124">id-prefix + CONVERT(nvarchar(4000), COLUMN, 126)</span></span>|  
|<span data-ttu-id="69a76-125">nmtoken/nmtokens</span><span class="sxs-lookup"><span data-stu-id="69a76-125">nmtoken/nmtokens</span></span>|<span data-ttu-id="69a76-126">id-prefix + CONVERT(nvarchar(4000), COLUMN, 126)</span><span class="sxs-lookup"><span data-stu-id="69a76-126">id-prefix + CONVERT(nvarchar(4000), COLUMN, 126)</span></span>|  
|<span data-ttu-id="69a76-127">Time</span><span class="sxs-lookup"><span data-stu-id="69a76-127">Time</span></span>|<span data-ttu-id="69a76-128">SUBSTRING(CONVERT(nvarchar(4000), COLUMN, 126), 1+CHARINDEX(N'T', CONVERT(nvarchar(4000), COLUMN, 126)), 24)</span><span class="sxs-lookup"><span data-stu-id="69a76-128">SUBSTRING(CONVERT(nvarchar(4000), COLUMN, 126), 1+CHARINDEX(N'T', CONVERT(nvarchar(4000), COLUMN, 126)), 24)</span></span>|  
|<span data-ttu-id="69a76-129">나머지</span><span class="sxs-lookup"><span data-stu-id="69a76-129">All others</span></span>|<span data-ttu-id="69a76-130">추가 변환 없음</span><span class="sxs-lookup"><span data-stu-id="69a76-130">No additional conversion</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="69a76-131">"XYZ"를 `xsd:type` 데이터 형식으로 변환하는 경우처럼 변환이 가능하지 않거나 -100000을 `decimal` XSD 형식으로 변환하는 경우처럼 값이 데이터 형식의 범위를 초과하는 경우와 같이, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 반환되는 일부 값이 `UnsignedShort`을 사용하여 지정한 XML 데이터 형식과 호환되지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="69a76-131">Some of the values returned by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] might not be compatible with the XML data types that are specified by using `xsd:type`, either because the conversion is not possible (for example, converting "XYZ" to a `decimal` data type) or because the value exceeds the range of that data type (for example, -100000 converted to an `UnsignedShort` XSD type).</span></span> <span data-ttu-id="69a76-132">호환되지 않는 형식 변환은 XML 문서를 유효하지 않게 만들거나 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 오류를 발생시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="69a76-132">Incompatible type conversions might result in XML documents that are not valid, or in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] errors.</span></span>  
  
## <a name="mapping-from-sql-server-data-types-to-xsd-data-types"></a><span data-ttu-id="69a76-133">SQL Server 데이터 형식에서 XSD 데이터 형식으로의 매핑</span><span class="sxs-lookup"><span data-stu-id="69a76-133">Mapping from SQL Server Data Types to XSD Data Types</span></span>  
 <span data-ttu-id="69a76-134">다음 표에서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터 형식에서 XSD 데이터 형식으로의 명확한 매핑을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="69a76-134">The following table shows an obvious mapping from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data types to XSD data types.</span></span> <span data-ttu-id="69a76-135">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 형식을 아는 경우 이 표를 통해 XSD 스키마에 지정할 수 있는 해당 XSD 형식을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="69a76-135">If you know the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] type, this table provides the corresponding XSD type that you can specify in the XSD schema.</span></span>  
  
|<span data-ttu-id="69a76-136">SQL Server 데이터 형식</span><span class="sxs-lookup"><span data-stu-id="69a76-136">SQL Server data type</span></span>|<span data-ttu-id="69a76-137">XSD 데이터 형식</span><span class="sxs-lookup"><span data-stu-id="69a76-137">XSD data type</span></span>|  
|--------------------------|-------------------|  
|`bigint`|`long`|  
|`binary`|`base64Binary`|  
|`bit`|`boolean`|  
|`char`|`string`|  
|`datetime`|`dateTime`|  
|`decimal`|`decimal`|  
|`float`|`double`|  
|`image`|`base64Binary`|  
|`int`|`int`|  
|`money`|`decimal`|  
|`nchar`|`string`|  
|`ntext`|`string`|  
|`nvarchar`|`string`|  
|`numeric`|`decimal`|  
|`real`|`float`|  
|`smalldatetime`|`dateTime`|  
|`smallint`|`short`|  
|`smallmoney`|`decimal`|  
|`sql_variant`|`string`|  
|`sysname`|`string`|  
|`text`|`string`|  
|`timestamp`|`dateTime`|  
|`tinyint`|`unsignedByte`|  
|`varbinary`|`base64Binary`|  
|`varchar`|`string`|  
|`uniqueidentifier`|`string`|  
  
## <a name="sqldatatype-annotation"></a><span data-ttu-id="69a76-138">sql:datatype 주석</span><span class="sxs-lookup"><span data-stu-id="69a76-138">sql:datatype Annotation</span></span>  
 <span data-ttu-id="69a76-139">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터 형식을 지정하는 데에는 `sql:datatype` 주석이 사용됩니다. 다음 경우에 이 주석을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="69a76-139">The `sql:datatype` annotation is used to specify the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data type; this annotation must be specified when:</span></span>  
  
-   <span data-ttu-id="69a76-140">`dateTime` [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] XSD `dateTime` , `date` 또는 형식에서 열 `time` 로 대량 로드 하 고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="69a76-140">You are bulk loading into a `dateTime`[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] column from an XSD `dateTime`, `date`, or `time` type.</span></span> <span data-ttu-id="69a76-141">이 경우에는 `sql:datatype="dateTime"`을 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 열 데이터 형식을 식별해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="69a76-141">In this case, you must identify the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] column data type by using `sql:datatype="dateTime"`.</span></span> <span data-ttu-id="69a76-142">이 규칙은 updategram에도 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="69a76-142">This rule also applies to updategrams.</span></span>  
  
-   <span data-ttu-id="69a76-143">형식의 열에 대량 로드 하 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `uniqueidentifier` 고 XSD 값이 중괄호 ({및})를 포함 하는 GUID 인 경우</span><span class="sxs-lookup"><span data-stu-id="69a76-143">You are bulk loading into a column of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `uniqueidentifier` type and the XSD value is a GUID that includes braces ({ and }).</span></span> <span data-ttu-id="69a76-144">`sql:datatype="uniqueidentifier"`를 지정하면 열에 값을 삽입하기 전에 중괄호가 제거됩니다.</span><span class="sxs-lookup"><span data-stu-id="69a76-144">When you specify `sql:datatype="uniqueidentifier"`, the braces are removed from the value before it is inserted in the column.</span></span> <span data-ttu-id="69a76-145">`sql:datatype`을 지정하지 않으면 값이 중괄호와 함께 보내지므로 삽입이나 업데이트가 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="69a76-145">If `sql:datatype` is not specified, the value is sent with the braces, and the insert or update fails.</span></span>  
  
-   <span data-ttu-id="69a76-146">XML 데이터 형식 `base64Binary`는 다양한 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터 형식(`binary`, `image` 또는 `varbinary`)에 매핑됩니다.</span><span class="sxs-lookup"><span data-stu-id="69a76-146">The XML data type `base64Binary` maps to various [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data types (`binary`, `image`, or `varbinary`).</span></span> <span data-ttu-id="69a76-147">XML 데이터 형식 `base64Binary`를 특정 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터 형식에 매핑하려면 `sql:datatype` 주석을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="69a76-147">To map the XML data type `base64Binary` to a specific [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data type, use the `sql:datatype` annotation.</span></span> <span data-ttu-id="69a76-148">이 주석은 특성이 매핑될 열의 명시적인 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터 형식을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="69a76-148">This annotation specifies the explicit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data type of the column to which the attribute maps.</span></span> <span data-ttu-id="69a76-149">데이터가 데이터베이스에 저장될 경우 이 주석을 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="69a76-149">This is useful when data is being stored in the databases.</span></span> <span data-ttu-id="69a76-150">`sql:datatype` 주석을 지정하면 명시적 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터 형식을 식별할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="69a76-150">By specifying the `sql:datatype` annotation, you can identify the explicit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data type.</span></span>  
  
 <span data-ttu-id="69a76-151">일반적으로 스키마에 `sql:datatype`을 지정하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="69a76-151">It is generally recommended that you specify `sql:datatype` in the schema.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="69a76-152">예</span><span class="sxs-lookup"><span data-stu-id="69a76-152">Examples</span></span>  
 <span data-ttu-id="69a76-153">다음 예를 사용하여 작업 예제를 만들려면 특정 요구 사항이 충족되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="69a76-153">To create working samples using the following examples, you must meet certain requirements.</span></span> <span data-ttu-id="69a76-154">자세한 내용은 [SQLXML 예를 실행 하기 위한 요구 사항](../sqlxml/requirements-for-running-sqlxml-examples.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="69a76-154">For more information, see [Requirements for Running SQLXML Examples](../sqlxml/requirements-for-running-sqlxml-examples.md).</span></span>  
  
### <a name="a-specifying-xsdtype"></a><span data-ttu-id="69a76-155">A.</span><span class="sxs-lookup"><span data-stu-id="69a76-155">A.</span></span> <span data-ttu-id="69a76-156">xsd:type 지정</span><span class="sxs-lookup"><span data-stu-id="69a76-156">Specifying xsd:type</span></span>  
 <span data-ttu-id="69a76-157">이 예에서는 스키마에서 `date` 특성을 사용하여 지정한 XSD `xsd:type` 형식이 결과 XML 문서에 미치는 영향을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="69a76-157">This example shows how an XSD `date` type that is specified by using the `xsd:type` attribute in the schema affects the resulting XML document.</span></span> <span data-ttu-id="69a76-158">이 스키마에서는 AdventureWorks 데이터베이스에 Sales.SalesOrderHeader 테이블의 XML 뷰를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="69a76-158">The schema provides an XML view of the Sales.SalesOrderHeader table in the AdventureWorks database.</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:element name="Order" sql:relation="Sales.SalesOrderHeader">  
     <xsd:complexType>  
       <xsd:attribute name="SalesOrderID" type="xsd:string" />   
       <xsd:attribute name="CustomerID"   type="xsd:string" />   
       <xsd:attribute name="OrderDate"    type="xsd:date" />   
       <xsd:attribute name="DueDate"  />   
       <xsd:attribute name="ShipDate"  type="xsd:time" />   
     </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
 <span data-ttu-id="69a76-159">이 XSD 스키마에는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 날짜 값을 반환하는 세 가지 특성이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="69a76-159">In this XSD schema, there are three attributes that return a date value from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="69a76-160">스키마에서 다음을 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="69a76-160">When the schema:</span></span>  
  
-   <span data-ttu-id="69a76-161">`xsd:type=date` **Orderdate** 특성을 지정 하 고 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **orderdate** 특성에 대해에서 반환 된 값의 날짜 부분을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="69a76-161">Specifies `xsd:type=date` on the **OrderDate** attribute, the date part of the value returned by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] for the **OrderDate** attribute is displayed.</span></span>  
  
-   <span data-ttu-id="69a76-162">`xsd:type=time` **ShipDate** 특성을 지정 하면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **ShipDate** 특성에 대해에서 반환 하는 값의 시간 부분이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="69a76-162">Specifies `xsd:type=time` on the **ShipDate** attribute, the time part of the value that is returned by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] for the **ShipDate** attribute is displayed.</span></span>  
  
-   <span data-ttu-id="69a76-163">`xsd:type` **DueDate** 특성에을 지정 하지 않으면에서 반환 하는 것과 동일한 값 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="69a76-163">Does not specify `xsd:type` on the **DueDate** attribute, the same value that is returned by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is displayed.</span></span>  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a><span data-ttu-id="69a76-164">스키마에 대해 예제 XPath 쿼리를 테스트하려면</span><span class="sxs-lookup"><span data-stu-id="69a76-164">To test a sample XPath query against the schema</span></span>  
  
1.  <span data-ttu-id="69a76-165">위 스키마 코드를 복사한 후 텍스트 파일에 붙여넣습니다.</span><span class="sxs-lookup"><span data-stu-id="69a76-165">Copy the schema code above and paste it into a text file.</span></span> <span data-ttu-id="69a76-166">파일을 xsdType.xml로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="69a76-166">Save the file as xsdType.xml.</span></span>  
  
2.  <span data-ttu-id="69a76-167">다음 템플릿을 복사한 후 텍스트 파일에 붙여넣습니다.</span><span class="sxs-lookup"><span data-stu-id="69a76-167">Copy the following template and paste it into a text file.</span></span> <span data-ttu-id="69a76-168">파일을 xsdType.xml을 저장한 디렉터리와 같은 디렉터리에 xsdTypeT.xml로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="69a76-168">Save the file as xsdTypeT.xml in the same directory where you saved xsdType.xml.</span></span>  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:xpath-query mapping-schema="xsdType.xml">  
        /Order  
      </sql:xpath-query>  
    </ROOT>  
    ```  
  
     <span data-ttu-id="69a76-169">매핑 스키마(xsdType.xml)에 대해 지정된 디렉터리 경로는 템플릿이 저장된 디렉터리에 상대적입니다.</span><span class="sxs-lookup"><span data-stu-id="69a76-169">The directory path specified for the mapping schema (xsdType.xml) is relative to the directory where the template is saved.</span></span> <span data-ttu-id="69a76-170">또한 다음과 같이 절대 경로를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="69a76-170">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\SqlXmlTest\xsdType.xml"  
    ```  
  
3.  <span data-ttu-id="69a76-171">SQLXML 4.0 테스트 스크립트(Sqlxml4test.vbs)를 만든 다음 이 스크립트를 사용하여 템플릿을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="69a76-171">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="69a76-172">자세한 내용은 [ADO를 사용 하 여 SQLXML 4.0 쿼리 실행](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="69a76-172">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="69a76-173">다음은 결과 집합의 일부입니다.</span><span class="sxs-lookup"><span data-stu-id="69a76-173">Here is the partial result set:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Order SalesOrderID="43659"   
         CustomerID="676"   
         OrderDate="2001-07-01"   
         DueDate="2001-07-13T00:00:00"   
         ShipDate="00:00:00" />   
  <Order SalesOrderID="43660"   
         CustomerID="117"   
         OrderDate="2001-07-01"   
         DueDate="2001-07-13T00:00:00"   
         ShipDate="00:00:00" />   
 ...  
</ROOT>  
```  
  
 <span data-ttu-id="69a76-174">다음은 동등한 XDR 스키마입니다.</span><span class="sxs-lookup"><span data-stu-id="69a76-174">This is the equivalent XDR schema:</span></span>  
  
```  
<?xml version="1.0" ?>  
<Schema xmlns="urn:schemas-microsoft-com:xml-data"  
        xmlns:dt="urn:schemas-microsoft-com:datatypes"  
        xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  
<ElementType name="Order" sql:relation="Sales.SalesOrderHeader">  
    <AttributeType name="SalesOrderID" />  
    <AttributeType name="CustomerID"  />  
    <AttributeType name="OrderDate" dt:type="date" />  
    <AttributeType name="DueDate" />  
    <AttributeType name="ShipDate" dt:type="time" />  
  
    <attribute type="SalesOrderID" sql:field="OrderID" />  
    <attribute type="CustomerID" sql:field="CustomerID" />  
    <attribute type="OrderDate" sql:field="OrderDate" />  
    <attribute type="DueDate" sql:field="DueDate" />  
    <attribute type="ShipDate" sql:field="ShipDate" />  
</ElementType>  
</Schema>  
```  
  
### <a name="b-specifying-sql-data-type-using-sqldatatype"></a><span data-ttu-id="69a76-175">B.</span><span class="sxs-lookup"><span data-stu-id="69a76-175">B.</span></span> <span data-ttu-id="69a76-176">sql:datatype을 사용하여 SQL 데이터 형식 지정</span><span class="sxs-lookup"><span data-stu-id="69a76-176">Specifying SQL data type using sql:datatype</span></span>  
 <span data-ttu-id="69a76-177">작업 샘플은 [SQLXML 4.0&#41;&#40;XML 대량 로드 예제의 ](../sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/xml-bulk-load-examples-sqlxml-4-0.md)예제 G를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="69a76-177">For a working sample, see Example G in [XML Bulk Load Examples &#40;SQLXML 4.0&#41;](../sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/xml-bulk-load-examples-sqlxml-4-0.md).</span></span> <span data-ttu-id="69a76-178">이 예에서는 "{" 및 "}"을 포함하는 GUID 값을 대량 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="69a76-178">In this example, a GUID value including "{" and "}" is bulk loaded.</span></span> <span data-ttu-id="69a76-179">이 예의 스키마는 `sql:datatype`을 지정하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터 형식을 `uniqueidentifier`로 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="69a76-179">The schema in this example specifies `sql:datatype` to identify the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data type as `uniqueidentifier`.</span></span> <span data-ttu-id="69a76-180">이 예에서는 스키마에서 `sql:datatype`을 지정해야 하는 경우를 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="69a76-180">This example illustrate when `sql:datatype` must be specified in the schema.</span></span>  
  
  
