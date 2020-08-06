---
title: WITH XMLNAMESPACES를 사용하여 쿼리에 네임스페이스 추가 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- ELEMENTS XSINIL directive
- adding namespaces
- XSINIL directive
- default namespaces
- queries [XML in SQL Server], WITH XMLNAMESPACES clause
- predefined namespaces [XML in SQL Server]
- FOR XML clause, WITH XMLNAMESPACES clause
- namespaces [XML in SQL Server]
- xml data type [SQL Server], WITH XMLNAMESPACES clause
- WITH XMLNAMESPACES clause
ms.assetid: 2189cb5e-4460-46c5-a254-20c833ebbfec
author: rothja
ms.author: jroth
ms.openlocfilehash: ed5d719a845996215fffc18af64401779f848cd0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646246"
---
# <a name="add-namespaces-to-queries-with-with-xmlnamespaces"></a><span data-ttu-id="138e0-102">WITH XMLNAMESPACES를 사용하여 쿼리에 네임스페이스 추가</span><span class="sxs-lookup"><span data-stu-id="138e0-102">Add Namespaces to Queries with WITH XMLNAMESPACES</span></span>
  <span data-ttu-id="138e0-103">[WITH XMLNAMESPACES(Transact-SQL)](/sql/t-sql/xml/with-xmlnamespaces) 는 다음과 같은 방식으로 네임스페이스 URI를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="138e0-103">[WITH XMLNAMESPACES (Transact-SQL)](/sql/t-sql/xml/with-xmlnamespaces) provides namespace URI support in the following way:</span></span>  
  
-   <span data-ttu-id="138e0-104">[FOR XML을 사용하는 XML 생성](for-xml-sql-server.md) 쿼리 시 URI 매핑에 대한 네임스페이스 접두사를 사용할 수 있도록 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="138e0-104">It makes the namespace prefix to URI mapping available when [Constructing XML Using FOR XML](for-xml-sql-server.md) queries.</span></span>  
  
-   <span data-ttu-id="138e0-105">[xml 데이터 형식 메서드](/sql/t-sql/xml/xml-data-type-methods)의 정적 네임스페이스 컨텍스트에 URI 매핑에 대한 네임스페이스를 사용할 수 있도록 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="138e0-105">It makes the namespace to URI mapping available to the static namespace context of the [xml Data Type Methods](/sql/t-sql/xml/xml-data-type-methods).</span></span>  
  
## <a name="using-with-xmlnamespaces-in-the-for-xml-queries"></a><span data-ttu-id="138e0-106">FOR XML 쿼리에서 WITH XMLNAMESPACES 사용</span><span class="sxs-lookup"><span data-stu-id="138e0-106">Using WITH XMLNAMESPACES in the FOR XML Queries</span></span>  
 <span data-ttu-id="138e0-107">WITH XMLNAMESPACES를 사용하면 FOR XML 쿼리에 XML 네임스페이스를 포함시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="138e0-107">WITH XMLNAMESPACES lets you include XML namespaces in FOR XML queries.</span></span> <span data-ttu-id="138e0-108">예를 들어 다음 FOR XML 쿼리를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="138e0-108">For example, consider the following FOR XML query:</span></span>  
  
```  
SELECT ProductID, Name, Color  
FROM   Production.Product  
WHERE  ProductID=316 or ProductID=317  
FOR XML RAW  
```  
  
 <span data-ttu-id="138e0-109">다음은 결과입니다.</span><span class="sxs-lookup"><span data-stu-id="138e0-109">This is the result:</span></span>  
  
```  
<row ProductID="316" Name="Blade" />  
<row ProductID="317" Name="LL Crankarm" Color="Black" />  
  
```  
  
 <span data-ttu-id="138e0-110">FOR XML 쿼리에 의해 생성된 XML에 네임스페이스를 추가하려면 먼저 WITH NAMESPACES 절을 사용하여 URI 매핑에 네임스페이스 접두사를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="138e0-110">To add namespaces to the XML constructed by the FOR XML query, first specify the namespace prefix to URI mappings by using the WITH NAMESPACES clause.</span></span> <span data-ttu-id="138e0-111">그런 다음 수정된 다음 쿼리에 표시된 것과 같이 쿼리에 네임스페이스를 지정할 때 네임스페이스 접두사를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="138e0-111">Then, use the namespace prefixes in specifying the names in the query as shown in the following modified query.</span></span> <span data-ttu-id="138e0-112">WITH XMLNAMESPACES 절은 URI(`ns1`) 매핑에 대해 네임스페이스 접두사(`uri`)를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="138e0-112">Note that the WITH XMLNAMESPACES clause specifies the namespace prefix (`ns1`) to URI (`uri`) mapping.</span></span> <span data-ttu-id="138e0-113">`ns1` 접두사는 FOR XML 쿼리에 의해 생성되는 요소 및 특성 이름을 지정하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="138e0-113">The `ns1` prefix is then used in specifying the element and attribute names to be constructed by the FOR XML query.</span></span>  
  
```  
WITH XMLNAMESPACES ('uri' as ns1)  
SELECT ProductID as 'ns1:ProductID',  
       Name      as 'ns1:Name',   
       Color     as 'ns1:Color'  
FROM Production.Product  
WHERE ProductID=316 or ProductID=317  
FOR XML RAW ('ns1:Prod'), ELEMENTS  
  
```  
  
 <span data-ttu-id="138e0-114">XML 결과에는 네임스페이스 접두사가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="138e0-114">The XML result includes the namespace prefixes:</span></span>  
  
```  
<ns1:Prod xmlns:ns1="uri">  
  <ns1:ProductID>316</ns1:ProductID>  
  <ns1:Name>Blade</ns1:Name>  
</ns1:Prod>  
<ns1:Prod xmlns:ns1="uri">  
  <ns1:ProductID>317</ns1:ProductID>  
  <ns1:Name>LL Crankarm</ns1:Name>  
  <ns1:Color>Black</ns1:Color>  
</ns1:Prod>  
  
```  
  
 <span data-ttu-id="138e0-115">다음은 WITH XMLNAMESPACES 절에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="138e0-115">The following applies to the WITH XMLNAMESPACES clause:</span></span>  
  
-   <span data-ttu-id="138e0-116">FOR XML 쿼리의 RAW, AUTO 및 PATH 모드에서만 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="138e0-116">It is supported only on the RAW, AUTO, and PATH modes of the FOR XML queries.</span></span> <span data-ttu-id="138e0-117">EXPLICIT 모드는 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="138e0-117">The EXPLICIT mode is not supported.</span></span>  
  
-   <span data-ttu-id="138e0-118">FOR XML 쿼리의 네임스페이스 접두사와 **xml** 데이터 형식 메서드에만 영향을 주고 XML 파서에는 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="138e0-118">It only affects the namespace prefixes of FOR XML queries and the **xml** data type methods, but not the XML parser.</span></span> <span data-ttu-id="138e0-119">예를 들어 다음 쿼리는 XML 문서에 myNS 접두사에 대한 네임스페이스 선언이 없기 때문에 오류를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="138e0-119">For example, the following query returns an error, because the XML document has no namespace declaration for the myNS prefix.</span></span>  
  
-   <span data-ttu-id="138e0-120">WITH XMLNAMESPACES 절을 사용하는 경우 FOR XML 지시어, XMLSCHEMA 및 XMLDATA는 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="138e0-120">The FOR XML directives, XMLSCHEMA and XMLDATA cannot be used when a WITH XMLNAMESPACES clause is being used.</span></span>  
  
    ```  
    CREATE TABLE T (x xml)  
    go  
    WITH XMLNAMESPACES ('http://abc' as myNS )  
    INSERT INTO T VALUES('<myNS:root/>')  
    ```  
  
## <a name="using-the-xsinil-directive"></a><span data-ttu-id="138e0-121">XSINIL 지시어 사용</span><span class="sxs-lookup"><span data-stu-id="138e0-121">Using the XSINIL Directive</span></span>  
 <span data-ttu-id="138e0-122">ELEMENTS XSINIL 지시어를 사용할 때는 WITH XMLNAMESPACES 절에서 xsi 접두사를 정의할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="138e0-122">You cannot define the xsi prefix in the WITH XMLNAMESPACES clause if you are using the ELEMENTS XSINIL directive.</span></span> <span data-ttu-id="138e0-123">대신 ELEMENTS XSINIL을 사용할 때 자동으로 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="138e0-123">Instead, it is added automatically when you use ELEMENTS XSINIL.</span></span> <span data-ttu-id="138e0-124">다음 쿼리에서는 **xsi:nil** 특성이 True로 설정된 요소에 Null 값이 매핑되는 요소 중심 XML을 생성하는 ELEMENTS XSINIL을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="138e0-124">The following query uses ELEMENTS XSINIL that generates element-centric XML where null values are mapped to elements that have the **xsi:nil** attribute set to True.</span></span>  
  
```  
WITH XMLNAMESPACES ('uri' as ns1)  
SELECT ProductID as 'ns1:ProductID',  
       Name      as 'ns1:Name',   
       Color     as 'ns1:Color'  
FROM Production.Product  
WHERE ProductID=316   
FOR XML RAW, ELEMENTS XSINIL  
```  
  
 <span data-ttu-id="138e0-125">다음은 결과입니다.</span><span class="sxs-lookup"><span data-stu-id="138e0-125">This is the result:</span></span>  
  
```  
<row xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:ns1="uri">  
  <ns1:ProductID>316</ns1:ProductID>  
  <ns1:Name>Blade</ns1:Name>  
  <ns1:Color xsi:nil="true" />  
</row>  
```  
  
## <a name="specifying-default-namespaces"></a><span data-ttu-id="138e0-126">기본 네임스페이스 지정</span><span class="sxs-lookup"><span data-stu-id="138e0-126">Specifying Default Namespaces</span></span>  
 <span data-ttu-id="138e0-127">네임스페이스 접두사를 선언하는 대신 DEFAULT 키워드를 사용하여 기본 네임스페이스를 선언할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="138e0-127">Instead of declaring a namespace prefix, you can declare a default namespace by using a DEFAULT keyword.</span></span> <span data-ttu-id="138e0-128">FOR XML 쿼리에서 기본 네임스페이스를 결과 XML의 XML 노드에 바인딩합니다.</span><span class="sxs-lookup"><span data-stu-id="138e0-128">In the FOR XML query, it will bind the default namespace to XML nodes in the resulting XML.</span></span> <span data-ttu-id="138e0-129">다음 예에서 WITH XMLNAMESPACES는 기본 네임스페이스와 함께 정의된 두 개의 네임스페이스 접두사를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="138e0-129">In the following example, the WITH XMLNAMESPACES defines two namespace prefixes that are defined together with a default namespace.</span></span>  
  
```  
WITH XMLNAMESPACES ('uri1' as ns1,   
                    'uri2' as ns2,  
                    DEFAULT 'uri2')  
SELECT ProductID,   
      Name,  
      Color  
FROM Production.Product   
WHERE ProductID=316 or ProductID=317  
FOR XML RAW ('ns1:Product'), ROOT('ns2:root'), ELEMENTS  
```  
  
 <span data-ttu-id="138e0-130">FOR XML 쿼리는 요소 중심 XML을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="138e0-130">The FOR XML query generates element-centric XML.</span></span> <span data-ttu-id="138e0-131">쿼리는 노드 이름 지정 시에 두 네임스페이스 접두사를 모두 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="138e0-131">Note that the query uses both the namespace prefixes in naming nodes.</span></span> <span data-ttu-id="138e0-132">SELECT 절에서 ProductID, Name 및 Color는 접두사가 포함된 이름을 지정하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="138e0-132">In the SELECT clause, the ProductID, Name, and Color do not specify a name with any prefix.</span></span> <span data-ttu-id="138e0-133">따라서 결과 XML의 해당 요소는 기본 네임스페이스에 속합니다.</span><span class="sxs-lookup"><span data-stu-id="138e0-133">Therefore, the corresponding elements in the resulting XML belong to the default namespace.</span></span>  
  
```  
<ns2:root xmlns="uri2" xmlns:ns2="uri2" xmlns:ns1="uri1">  
  <ns1:Product>  
    <ProductID>316</ProductID>  
    <Name>Blade</Name>  
  </ns1:Product>  
  <ns1:Product>  
    <ProductID>317</ProductID>  
    <Name>LL Crankarm</Name>  
    <Color>Black</Color>  
  </ns1:Product>  
</ns2:root>  
```  
  
 <span data-ttu-id="138e0-134">다음 쿼리는 이전 쿼리와 비슷하지만 FOR XML AUTO 모드가 지정되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="138e0-134">The following query is similar to the previous one, except that the FOR XML AUTO mode is specified.</span></span>  
  
```  
WITH XMLNAMESPACES ('uri1' as ns1,  'uri2' as ns2,DEFAULT 'uri2')  
SELECT ProductID,   
      Name,  
      Color  
FROM Production.Product as "ns1:Product"  
WHERE ProductID=316 or ProductID=317  
FOR XML AUTO, ROOT('ns2:root'), ELEMENTS  
```  
  
## <a name="using-predefined-namespaces"></a><span data-ttu-id="138e0-135">미리 정의된 네임스페이스 사용</span><span class="sxs-lookup"><span data-stu-id="138e0-135">Using Predefined Namespaces</span></span>  
 <span data-ttu-id="138e0-136">ELEMENTS XSINIL이 사용되는 경우의 xml 네임스페이스 및 xsi 네임스페이스를 제외한 미리 정의된 네임스페이스를 사용하는 경우 WITH XMLNAMESPACES를 사용하여 네임스페이스 바인딩을 명시적으로 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="138e0-136">When you use predefined namespaces, except the xml namespace and the xsi namespace when ELEMENTS XSINIL is used, you must explicitly specify the namespace binding by using WITH XMLNAMESPACES.</span></span> <span data-ttu-id="138e0-137">다음 쿼리는 미리 정의된 네임스페이스에 대해 URI 바인딩에 대한 네임스페이스 접두사를 명시적으로 정의합니다(`urn:schemas-microsoft-com:xml-sql`).</span><span class="sxs-lookup"><span data-stu-id="138e0-137">The following query explicitly defines the namespace prefix to URI binding for the predefined namespace (`urn:schemas-microsoft-com:xml-sql`).</span></span>  
  
```  
WITH XMLNAMESPACES ('urn:schemas-microsoft-com:xml-sql' as sql)  
SELECT 'SELECT * FROM Customers FOR XML AUTO, ROOT("a")' AS "sql:query"  
FOR XML PATH('sql:root')  
```  
  
 <span data-ttu-id="138e0-138">다음은 결과입니다.</span><span class="sxs-lookup"><span data-stu-id="138e0-138">This is the result.</span></span> <span data-ttu-id="138e0-139">SQLXML 사용자는 이러한 XML 템플릿에 익숙합니다.</span><span class="sxs-lookup"><span data-stu-id="138e0-139">SQLXML users are familiar with this XML template.</span></span> <span data-ttu-id="138e0-140">자세한 내용은 [SQLXML 4.0 프로그래밍 개념](../sqlxml/sqlxml-4-0-programming-concepts.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="138e0-140">For more information, see [SQLXML 4.0 Programming Concepts](../sqlxml/sqlxml-4-0-programming-concepts.md).</span></span>  
  
```  
<sql:root xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <sql:query>SELECT * FROM Customers FOR XML AUTO, ROOT("a")</sql:query>  
</sql:root>  
```  
  
 <span data-ttu-id="138e0-141">다음 PATH 모드 쿼리에 표시된 것과 같이 WITH XMLNAMESPACES에 명시적으로 정의할 필요 없이 xml 네임스페이스 접두사만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="138e0-141">Only the xml namespace prefix can be used without explicitly defining it in WITH XMLNAMESPACES, as shown in the following PATH mode query.</span></span> <span data-ttu-id="138e0-142">또한 접두사가 선언된 경우 네임스페이스 http://www.w3.org/XML/1998/namespace 에 바인딩되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="138e0-142">Also, if the prefix is declared, it has to be bound to the namespace http://www.w3.org/XML/1998/namespace.</span></span> <span data-ttu-id="138e0-143">SELECT 절에 지정된 이름은 WITH XMLNAMESPACES를 사용하여 명시적으로 정의되지 않은 xml 네임스페이스 접두사를 참조합니다.</span><span class="sxs-lookup"><span data-stu-id="138e0-143">The names specified in the SELECT clause refer to the xml namespace prefix that is not explicitly defined by using WITH XMLNAMESPACES.</span></span>  
  
```  
SELECT 'en'    as "English/@xml:lang",  
       'food'  as "English",  
       'ger'   as "German/@xml:lang",  
       'Essen' as "German"  
FOR XML PATH ('Translation')  
go  
```  
  
 <span data-ttu-id="138e0-144">@xml:lang 특성은 미리 정의된 xml 네임스페이스를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="138e0-144">The @xml:lang attributes use the predefined xml namespace.</span></span> <span data-ttu-id="138e0-145">XML 버전 1.0에는 xml 네임스페이스 바인딩에 대한 명시적 선언이 필요하지 않기 때문에 결과에는 네임스페이스 바인딩의 명시적 선언이 포함되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="138e0-145">Because XML version 1.0 does not require the explicit declaration of the xml namespace binding, the result will not include an explicit declaration of the namespace binding.</span></span>  
  
 <span data-ttu-id="138e0-146">다음은 결과입니다.</span><span class="sxs-lookup"><span data-stu-id="138e0-146">This is the result:</span></span>  
  
```  
<Translation>  
  <English xml:lang="en">food</English>  
  <German xml:lang="ger">Essen</German>  
</Translation>  
```  
  
## <a name="using-with-xmlnamespaces-with-the-xml-data-type-methods"></a><span data-ttu-id="138e0-147">xml 데이터 형식 메서드에서 WITH XMLNAMESPACES 사용</span><span class="sxs-lookup"><span data-stu-id="138e0-147">Using WITH XMLNAMESPACES with the xml Data Type Methods</span></span>  
 <span data-ttu-id="138e0-148">[modify()](/sql/t-sql/xml/xml-data-type-methods) 메서드인 경우 SELECT 쿼리 또는 UPDATE에 지정된 **xml 데이터 형식 메서드** 는 모두 해당 프롤로그에서 네임스페이스 선언을 반복해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="138e0-148">The [xml Data Type Methods](/sql/t-sql/xml/xml-data-type-methods) specified in a SELECT query, or in UPDATE when it is the **modify()** method, all have to repeat the namespace declaration in their prolog.</span></span> <span data-ttu-id="138e0-149">이 작업은 시간이 많이 걸리는 작업입니다</span><span class="sxs-lookup"><span data-stu-id="138e0-149">This can be time-consuming.</span></span> <span data-ttu-id="138e0-150">예를 들어 다음 쿼리는 카탈로그 설명에 사양이 포함되지 않는 제품 모델 ID를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="138e0-150">For example, the following query retrieves product model IDs whose catalog descriptions do include specification.</span></span> <span data-ttu-id="138e0-151">즉, <`Specifications`> 요소가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="138e0-151">That is, the <`Specifications`> element exists.</span></span>  
  
```  
SELECT ProductModelID, CatalogDescription.query('  
declare namespace pd="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
    <Product   
        ProductModelID= "{ sql:column("ProductModelID") }"   
        />  
') AS Result  
FROM Production.ProductModel  
WHERE CatalogDescription.exist('  
    declare namespace  pd="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
     /pd:ProductDescription[(pd:Specifications)]'  
    ) = 1  
```  
  
 <span data-ttu-id="138e0-152">이전 쿼리에서 **query()** 및 **exist()** 메서드는 모두 해당 프롤로그에서 같은 네임스페이스를 선언합니다.</span><span class="sxs-lookup"><span data-stu-id="138e0-152">In the previous query, both the **query()** and **exist()** methods declare the same namespace in their prolog.</span></span> <span data-ttu-id="138e0-153">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="138e0-153">For example:</span></span>  
  
```  
declare namespace pd="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
```  
  
 <span data-ttu-id="138e0-154">또는 WITH XMLNAMESPACES를 먼저 선언하고 쿼리에 있는 네임스페이스 접두사를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="138e0-154">Alternatively, you can declare WITH XMLNAMESPACES first and use the namespace prefixes in the query.</span></span> <span data-ttu-id="138e0-155">이 경우 **query()** 및 **exist()** 메서드는 해당 프롤로그에 네임스페이스 선언을 포함시킬 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="138e0-155">In this case, the **query()** and **exist()** methods  do not have to include namespace declarations in their prolog.</span></span>  
  
```  
WITH XMLNAMESPACES ('https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription' as pd)  
SELECT ProductModelID, CatalogDescription.query('  
    <Product   
        ProductModelID= "{ sql:column("ProductModelID") }"   
        />  
') AS Result  
FROM Production.ProductModel  
WHERE CatalogDescription.exist('  
     /pd:ProductDescription[(pd:Specifications)]'  
    ) = 1  
Go  
```  
  
 <span data-ttu-id="138e0-156">XQuery 프롤로그에 있는 명시적 선언은 네임스페이스 접두사와 WITH 절에 정의된 기본 요소 네임스페이스를 무시합니다.</span><span class="sxs-lookup"><span data-stu-id="138e0-156">Note that an explicit declaration in the XQuery prolog overrides the namespace prefix and the default element namespace that are defined in the WITH clause.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="138e0-157">참고 항목</span><span class="sxs-lookup"><span data-stu-id="138e0-157">See Also</span></span>  
 <span data-ttu-id="138e0-158">[xml 데이터 형식 메서드](/sql/t-sql/xml/xml-data-type-methods) </span><span class="sxs-lookup"><span data-stu-id="138e0-158">[xml Data Type Methods](/sql/t-sql/xml/xml-data-type-methods) </span></span>  
 <span data-ttu-id="138e0-159">[XQuery 언어 참조&#40;SQL Server&#41;](/sql/xquery/xquery-language-reference-sql-server) </span><span class="sxs-lookup"><span data-stu-id="138e0-159">[XQuery Language Reference &#40;SQL Server&#41;](/sql/xquery/xquery-language-reference-sql-server) </span></span>  
 <span data-ttu-id="138e0-160">[WITH XMLNAMESPACES&#40;Transact-SQL&#41;](/sql/t-sql/xml/with-xmlnamespaces) </span><span class="sxs-lookup"><span data-stu-id="138e0-160">[WITH XMLNAMESPACES &#40;Transact-SQL&#41;](/sql/t-sql/xml/with-xmlnamespaces) </span></span>  
 [<span data-ttu-id="138e0-161">FOR XML&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="138e0-161">FOR XML &#40;SQL Server&#41;</span></span>](for-xml-sql-server.md)  
  
  
