---
title: XPath 쿼리 사용 소개 (SQLXML 4.0) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- XPath queries [SQLXML], about XPath queries
- W3C XPath specification
- XPath queries [SQLXML], functionality
ms.assetid: 01050a8e-0ccc-4a02-a4eb-b48be5c3f4f3
author: rothja
ms.author: jroth
ms.openlocfilehash: dd173f16ee0e97dac1c45039f75022bbf2dc0782
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646305"
---
# <a name="introduction-to-using-xpath-queries-sqlxml-40"></a><span data-ttu-id="d0250-102">XPath 쿼리 사용 소개(SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="d0250-102">Introduction to Using XPath Queries (SQLXML 4.0)</span></span>
  <span data-ttu-id="d0250-103">XPath(XML Path Language) 쿼리는 URL의 일부로 지정하거나 템플릿 내에 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d0250-103">An XML Path Language (XPath) query can be specified as part of a URL or within a template.</span></span> <span data-ttu-id="d0250-104">매핑 스키마에 따라 이 결과 조각의 구조가 결정되고 값은 데이터베이스에서 검색됩니다.</span><span class="sxs-lookup"><span data-stu-id="d0250-104">The mapping schema determines the structure of this resulting fragment, and the values are retrieved from the database.</span></span> <span data-ttu-id="d0250-105">이 프로세스는 CREATE VIEW 문을 사용하여 뷰를 만들고 이러한 뷰에 대한 SQL 쿼리를 작성하는 것과 개념적으로 유사합니다.</span><span class="sxs-lookup"><span data-stu-id="d0250-105">This process is conceptually similar to creating views using the CREATE VIEW statement and writing SQL queries against them.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d0250-106">SQLXML 4.0의 XPath 쿼리를 이해하려면 템플릿 및 매핑 스키마와 같은 관련 개념과 XML 뷰에 대해 잘 알고 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0250-106">To understand XPath queries in SQLXML 4.0, you must be familiar with XML views and related concepts such as templates and mapping schema.</span></span> <span data-ttu-id="d0250-107">자세한 내용은 주석이 추가 된 [XSD 스키마 &#40;SQLXML 4.0&#41;](../sqlxml/annotated-xsd-schemas/introduction-to-annotated-xsd-schemas-sqlxml-4-0.md)및 WORLD WIDE WEB 컨소시엄 (W3C)에서 정의한 XPath 표준 소개를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="d0250-107">For more information, see [Introduction to Annotated XSD Schemas &#40;SQLXML 4.0&#41;](../sqlxml/annotated-xsd-schemas/introduction-to-annotated-xsd-schemas-sqlxml-4-0.md), and the XPath standard defined by the World Wide Web Consortium (W3C).</span></span>  
  
 <span data-ttu-id="d0250-108">XML 문서는 요소 노드, 특성 노드, 텍스트 노드 등과 같은 노드로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="d0250-108">An XML document consists of nodes such as an element node, attribute node, text node, and so on.</span></span> <span data-ttu-id="d0250-109">예를 들어 다음 XML 문서를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="d0250-109">For example, consider this XML document:</span></span>  
  
```  
<root>  
  <Customer cid= "C1" name="Janine" city="Issaquah">  
      <Order oid="O1" date="1/20/1996" amount="3.5" />  
      <Order oid="O2" date="4/30/1997" amount="13.4">Customer was  
          very satisfied</Order>  
   </Customer>  
   <Customer cid="C2" name="Ursula" city="Oelde" >  
      <Order oid="O3" date="7/14/1999" amount="100" note="Wrap it blue white red">  
          <Urgency>Important</Urgency>  
      </Order>  
      <Order oid="O4" date="1/20/1996" amount="10000"/>  
   </Customer>  
</root>  
```  
  
 <span data-ttu-id="d0250-110">이 문서에서 **\<Customer>** 는 요소 노드이 고 **cid** 는 Attribute 노드이며 **"Important"** 는 텍스트 노드입니다.</span><span class="sxs-lookup"><span data-stu-id="d0250-110">In this document, **\<Customer>** is an element node, **cid** is an attribute node, and **"Important"** is a text node.</span></span>  
  
 <span data-ttu-id="d0250-111">XPath는 XML 문서에서 노드 집합을 선택하는 데 사용되는 그래프 탐색 언어입니다.</span><span class="sxs-lookup"><span data-stu-id="d0250-111">XPath is a graph navigation language used to select a set of nodes from an XML document.</span></span> <span data-ttu-id="d0250-112">각 XPath 연산자는 이전 XPath 연산자에서 선택한 노드 집합을 기반으로 노드 집합을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d0250-112">Each XPath operator selects a node-set based on a node-set selected by a previous XPath operator.</span></span> <span data-ttu-id="d0250-113">예를 들어 노드 집합이 지정 된 경우 **\<Customer>** XPath는 **\<Order>** **date** 특성 값이 **"7/14/1999"** 인 모든 노드를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d0250-113">For example, given a set of **\<Customer>** nodes, XPath can select all **\<Order>** nodes with the **date** attribute value of **"7/14/1999"**.</span></span> <span data-ttu-id="d0250-114">결과 노드 집합에는 주문 날짜가 1999년 7월 14일인 모든 주문이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="d0250-114">The resulting node-set contains all the orders with order date 7/14/1999.</span></span>  
  
 <span data-ttu-id="d0250-115">XPath 언어는 W3C(World Wide Web Consortium)에서 표준 탐색 언어로 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="d0250-115">The XPath language is defined by the World Wide Web Consortium (W3C) as a standard navigation language.</span></span> <span data-ttu-id="d0250-116">SQLXML 4.0은에 있는 W3C XPath 사양의 하위 집합을 구현 http://www.w3.org/TR/1999/PR-xpath-19991008.html 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0250-116">SQLXML 4.0 implements a subset of the W3C XPath specification, which is located at http://www.w3.org/TR/1999/PR-xpath-19991008.html.</span></span>  
  
 <span data-ttu-id="d0250-117">다음은 W3C XPath 구현과 SQLXML 4.0 구현 간의 주요 차이점입니다.</span><span class="sxs-lookup"><span data-stu-id="d0250-117">The following are key differences between the W3C XPath implementation and the SQLXML 4.0 implementation.</span></span>  
  
-   <span data-ttu-id="d0250-118">**루트 쿼리**</span><span class="sxs-lookup"><span data-stu-id="d0250-118">**Root queries**</span></span>  
  
     <span data-ttu-id="d0250-119">SQLXML 4.0은 루트 쿼리(/)를 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d0250-119">SQLXML 4.0 does not support the root query (/).</span></span> <span data-ttu-id="d0250-120">모든 XPath 쿼리는 스키마의 최상위 수준에서 시작 해야 합니다 **\<ElementType>** .</span><span class="sxs-lookup"><span data-stu-id="d0250-120">Every XPath query must begin at a top-level **\<ElementType>** in the schema.</span></span>  
  
-   <span data-ttu-id="d0250-121">**오류 보고**</span><span class="sxs-lookup"><span data-stu-id="d0250-121">**Reporting errors**</span></span>  
  
     <span data-ttu-id="d0250-122">W3C XPath 사양에서는 오류 조건을 정의하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d0250-122">The W3C XPath specification defines no error conditions.</span></span> <span data-ttu-id="d0250-123">따라서 노드를 선택하지 못하는 XPath 쿼리는 빈 노드 집합을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="d0250-123">XPath queries that fail to select any nodes return an empty node-set.</span></span> <span data-ttu-id="d0250-124">SQLXML 4.0에서는 쿼리에서 여러 가지 오류 메시지를 반환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d0250-124">In SQLXML 4.0, a query can return many types of error messages.</span></span>  
  
-   <span data-ttu-id="d0250-125">**문서 순서**</span><span class="sxs-lookup"><span data-stu-id="d0250-125">**Document order**</span></span>  
  
     <span data-ttu-id="d0250-126">SQLXML 4.0에서는 문서 순서가 항상 확실하지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d0250-126">In SQLXML 4.0, document order is not always determined.</span></span> <span data-ttu-id="d0250-127">따라서 `following`과 같이 문서 순서를 사용하는 숫자 조건자와 축은 구현되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d0250-127">Therefore, numeric predicates and axes that use document order (such as `following`) are not implemented.</span></span>  
  
     <span data-ttu-id="d0250-128">또한 문서 순서가 없다는 것은 해당 노드가 단일 행의 단일 열에 매핑되는 경우에만 노드의 문자열 값을 평가할 수 있다는 것을 의미하기도 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0250-128">The lack of document order also means that the string value of a node can be evaluated only when that node maps to a single column in a single row.</span></span> <span data-ttu-id="d0250-129">자식 요소가 있는 요소, IDREFS 또는 NMTOKENS 노드는 문자열로 변환할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d0250-129">An element with child elements or an IDREFS or NMTOKENS node cannot be converted to string.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="d0250-130">경우에 따라 `key-fields` 주석이나 `relationship` 주석의 키로 인해 문서 순서가 결정적이 될 수도 있지만</span><span class="sxs-lookup"><span data-stu-id="d0250-130">In some cases, the `key-fields` annotation or keys from the `relationship` annotation can result in a deterministic document order.</span></span> <span data-ttu-id="d0250-131">그러나이 주석은 이러한 주석의 주요 사용이 아닙니다. 자세한 내용은 [sql: 키-필드 &#40;sqlxml 4.0&#41;](../sqlxml-annotated-xsd-schemas-using/identifying-key-columns-using-sql-key-fields-sqlxml-4-0.md) 를 사용 하 여 키 열 식별 및 [sql: relationship &#40;sqlxml 4.0&#41;를 사용 하 여 관계 지정 ](../sqlxml-annotated-xsd-schemas-using/specifying-relationships-using-sql-relationship-sqlxml-4-0.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="d0250-131">However, this is not the primary use of these annotations For more information, see [Identifying Key Columns Using sql:key-fields &#40;SQLXML 4.0&#41;](../sqlxml-annotated-xsd-schemas-using/identifying-key-columns-using-sql-key-fields-sqlxml-4-0.md) and [Specifying Relationships Using sql:relationship &#40;SQLXML 4.0&#41;](../sqlxml-annotated-xsd-schemas-using/specifying-relationships-using-sql-relationship-sqlxml-4-0.md).</span></span>  
  
-   <span data-ttu-id="d0250-132">**데이터 형식**</span><span class="sxs-lookup"><span data-stu-id="d0250-132">**Data types**</span></span>  
  
     <span data-ttu-id="d0250-133">SQLXML 4.0에서는 XPath `string`, `number` 및 `boolean` 데이터 형식의 구현에 제약이 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="d0250-133">SQLXML 4.0 has limitations in implementing the XPath `string`, `number`, and `boolean` data types.</span></span> <span data-ttu-id="d0250-134">자세한 내용은 [&#40;SQLXML 4.0&#41;XPath 데이터 형식 ](xpath-data-types-sqlxml-4-0.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="d0250-134">For more information, see [XPath Data Types &#40;SQLXML 4.0&#41;](xpath-data-types-sqlxml-4-0.md).</span></span>  
  
-   <span data-ttu-id="d0250-135">**교차곱 쿼리**</span><span class="sxs-lookup"><span data-stu-id="d0250-135">**Cross-product queries**</span></span>  
  
     <span data-ttu-id="d0250-136">SQLXML 4.0에서는 `Customers[Order/@OrderDate=Order/@ShipDate]`와 같은 교차곱 XPath 쿼리를 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d0250-136">SQLXML 4.0 does not support cross-product XPath queries, such as `Customers[Order/@OrderDate=Order/@ShipDate]`.</span></span> <span data-ttu-id="d0250-137">이 쿼리는 Order의 OrderDate가 ShipDate와 동일한 Order가 있는 모든 Customer를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d0250-137">This query selects all Customers with any Order for which the OrderDate equals the ShipDate of any Order.</span></span>  
  
     <span data-ttu-id="d0250-138">그러나 SQLXML 4.0에서는 OrderDate가 ShipDate와 동일한 Order가 있는 Customer를 선택하는 `Customer[Order[@OrderDate=@ShippedDate]]`와 같은 쿼리를 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d0250-138">However, SQLXML 4.0 does support queries such as `Customer[Order[@OrderDate=@ShippedDate]]`, which selects Customers with any Order for which the OrderDate equals its ShipDate.</span></span>  
  
-   <span data-ttu-id="d0250-139">**오류 처리 및 보안**</span><span class="sxs-lookup"><span data-stu-id="d0250-139">**Error handling and security**</span></span>  
  
     <span data-ttu-id="d0250-140">사용되는 스키마 및 XPath 쿼리 식에 따라 특정 조건에서 [!INCLUDE[tsql](../../includes/tsql-md.md)] 오류가 사용자에게 표시될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d0250-140">Depending on the schema and XPath query expression that are used, [!INCLUDE[tsql](../../includes/tsql-md.md)] errors could be exposed to users under certain conditions.</span></span>  
  
 <span data-ttu-id="d0250-141">다음 섹션의 표에서는 이러한 영역에서 SQLXML 4.0의 XPath 쿼리 구현이 W3C 사양과 어떻게 다른지 자세히 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="d0250-141">The tables in the following sections provide details about how the implementation of XPath queries in SQLXML 4.0 differs from the W3C specification in these areas.</span></span>  
  
## <a name="supported-functionality"></a><span data-ttu-id="d0250-142">지원되는 기능</span><span class="sxs-lookup"><span data-stu-id="d0250-142">Supported Functionality</span></span>  
 <span data-ttu-id="d0250-143">다음 표에서는 SQLXML 4.0에서 구현되는 XPath 언어의 기능을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="d0250-143">The following table shows the features of the XPath language that are implemented in SQLXML 4.0.</span></span>  
  
|<span data-ttu-id="d0250-144">기능</span><span class="sxs-lookup"><span data-stu-id="d0250-144">Feature</span></span>|<span data-ttu-id="d0250-145">항목</span><span class="sxs-lookup"><span data-stu-id="d0250-145">Item</span></span>|<span data-ttu-id="d0250-146">샘플 쿼리에 대한 링크</span><span class="sxs-lookup"><span data-stu-id="d0250-146">Link to sample queries</span></span>|  
|-------------|----------|----------------------------|  
|<span data-ttu-id="d0250-147">Axes</span><span class="sxs-lookup"><span data-stu-id="d0250-147">Axes</span></span>|<span data-ttu-id="d0250-148">`attribute`, `child`, `parent` 및 `self` 축</span><span class="sxs-lookup"><span data-stu-id="d0250-148">`attribute`, `child`, `parent`, and `self` axes</span></span>|[<span data-ttu-id="d0250-149">XPath 쿼리에 축 지정 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="d0250-149">Specifying Axes in XPath Queries &#40;SQLXML 4.0&#41;</span></span>](samples/specifying-axes-in-xpath-queries-sqlxml-4-0.md)|  
|<span data-ttu-id="d0250-150">연속 및 중첩 조건자를 포함하는 부울 값 조건자</span><span class="sxs-lookup"><span data-stu-id="d0250-150">Boolean-valued predicates including successive and nested predicates</span></span>||[<span data-ttu-id="d0250-151">XPath 쿼리에 산술 연산자 지정 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="d0250-151">Specifying Arithmetic Operators in XPath Queries &#40;SQLXML 4.0&#41;</span></span>](samples/specifying-arithmetic-operators-in-xpath-queries-sqlxml-4-0.md)|  
|<span data-ttu-id="d0250-152">모든 관계 연산자</span><span class="sxs-lookup"><span data-stu-id="d0250-152">All relational operators</span></span>|<span data-ttu-id="d0250-153">=,! =, <, \<=, > , >=</span><span class="sxs-lookup"><span data-stu-id="d0250-153">=, !=, <, \<=, >, >=</span></span>|[<span data-ttu-id="d0250-154">XPath 쿼리에 관계형 연산자 지정 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="d0250-154">Specifying Relational Operators in XPath Queries &#40;SQLXML 4.0&#41;</span></span>](samples/specifying-relational-operators-in-xpath-queries-sqlxml-4-0.md)|  
|<span data-ttu-id="d0250-155">산술 연산자</span><span class="sxs-lookup"><span data-stu-id="d0250-155">Arithmetic operators</span></span>|<span data-ttu-id="d0250-156">+, -, \*, div</span><span class="sxs-lookup"><span data-stu-id="d0250-156">+, -, \*, div</span></span>|[<span data-ttu-id="d0250-157">XPath 쿼리에 산술 연산자 지정 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="d0250-157">Specifying Arithmetic Operators in XPath Queries &#40;SQLXML 4.0&#41;</span></span>](samples/specifying-arithmetic-operators-in-xpath-queries-sqlxml-4-0.md)|  
|<span data-ttu-id="d0250-158">명시적 변환 함수</span><span class="sxs-lookup"><span data-stu-id="d0250-158">Explicit conversion functions</span></span>|<span data-ttu-id="d0250-159">`number()`, `string()`, `Boolean()`</span><span class="sxs-lookup"><span data-stu-id="d0250-159">`number()`, `string()`, `Boolean()`</span></span>|[<span data-ttu-id="d0250-160">XPath 쿼리에 명시적 변환 함수 지정 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="d0250-160">Specifying Explicit Conversion Functions in XPath Queries &#40;SQLXML 4.0&#41;</span></span>](samples/specifying-explicit-conversion-functions-in-xpath-queries-sqlxml-4-0.md)|  
|<span data-ttu-id="d0250-161">부울 연산자</span><span class="sxs-lookup"><span data-stu-id="d0250-161">Boolean operators</span></span>|<span data-ttu-id="d0250-162">AND, OR</span><span class="sxs-lookup"><span data-stu-id="d0250-162">AND, OR</span></span>|[<span data-ttu-id="d0250-163">XPath 쿼리에 부울 연산자 지정 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="d0250-163">Specifying Boolean Operators in XPath Queries &#40;SQLXML 4.0&#41;</span></span>](samples/specifying-boolean-operators-in-xpath-queries-sqlxml-4-0.md)|  
|<span data-ttu-id="d0250-164">부울 함수</span><span class="sxs-lookup"><span data-stu-id="d0250-164">Boolean functions</span></span>|<span data-ttu-id="d0250-165">`true()`, `false()`, `not()`</span><span class="sxs-lookup"><span data-stu-id="d0250-165">`true()`, `false()`, `not()`</span></span>|[<span data-ttu-id="d0250-166">XPath 쿼리에 부울 함수 지정 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="d0250-166">Specifying Boolean Functions in XPath Queries &#40;SQLXML 4.0&#41;</span></span>](samples/specifying-boolean-functions-in-xpath-queries-sqlxml-4-0.md)|  
|<span data-ttu-id="d0250-167">XPath 변수</span><span class="sxs-lookup"><span data-stu-id="d0250-167">XPath variables</span></span>||[<span data-ttu-id="d0250-168">XPath 쿼리에 XPath 변수 지정 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="d0250-168">Specifying XPath Variables in XPath Queries &#40;SQLXML 4.0&#41;</span></span>](samples/specifying-xpath-variables-in-xpath-queries-sqlxml-4-0.md)|  
  
## <a name="unsupported-functionality"></a><span data-ttu-id="d0250-169">지원되지 않는 기능</span><span class="sxs-lookup"><span data-stu-id="d0250-169">Unsupported Functionality</span></span>  
 <span data-ttu-id="d0250-170">다음 표에서는 SQLXML 4.0에서 구현되지 않는 XPath 언어의 기능을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="d0250-170">The following table shows the features of the XPath language that are not implemented in SQLXML 4.0.</span></span>  
  
|<span data-ttu-id="d0250-171">기능</span><span class="sxs-lookup"><span data-stu-id="d0250-171">Feature</span></span>|<span data-ttu-id="d0250-172">항목</span><span class="sxs-lookup"><span data-stu-id="d0250-172">Item</span></span>|  
|-------------|----------|  
|<span data-ttu-id="d0250-173">Axes</span><span class="sxs-lookup"><span data-stu-id="d0250-173">Axes</span></span>|<span data-ttu-id="d0250-174">`ancestor`, `ancestor-or-self`, `descendant`, `descendant-or-self (//)`, `following`, `following-sibling`, `namespace`, `preceding`, `preceding-sibling`</span><span class="sxs-lookup"><span data-stu-id="d0250-174">`ancestor`, `ancestor-or-self`, `descendant`, `descendant-or-self (//)`, `following`, `following-sibling`, `namespace`, `preceding`, `preceding-sibling`</span></span>|  
|<span data-ttu-id="d0250-175">숫자 값 조건자</span><span class="sxs-lookup"><span data-stu-id="d0250-175">Numeric-valued predicates</span></span>||  
|<span data-ttu-id="d0250-176">산술 연산자</span><span class="sxs-lookup"><span data-stu-id="d0250-176">Arithmetic operators</span></span>|<span data-ttu-id="d0250-177">mod</span><span class="sxs-lookup"><span data-stu-id="d0250-177">mod</span></span>|  
|<span data-ttu-id="d0250-178">노드 함수</span><span class="sxs-lookup"><span data-stu-id="d0250-178">Node functions</span></span>|<span data-ttu-id="d0250-179">`ancestor`, `ancestor-or-self`, `descendant`, `descendant-or-self (//)`, `following`, `following-sibling`, `namespace`, `preceding`, `preceding-sibling`</span><span class="sxs-lookup"><span data-stu-id="d0250-179">`ancestor`, `ancestor-or-self`, `descendant`, `descendant-or-self (//)`, `following`, `following-sibling`, `namespace`, `preceding`, `preceding-sibling`</span></span>|  
|<span data-ttu-id="d0250-180">문자열 함수</span><span class="sxs-lookup"><span data-stu-id="d0250-180">String functions</span></span>|<span data-ttu-id="d0250-181">`string()`, `concat()`, `starts-with()`, `contains()`, `substring-before()`, `substring-after()`, `substring()`, `string-length()`, `normalize()`, `translate()`</span><span class="sxs-lookup"><span data-stu-id="d0250-181">`string()`, `concat()`, `starts-with()`, `contains()`, `substring-before()`, `substring-after()`, `substring()`, `string-length()`, `normalize()`, `translate()`</span></span>|  
|<span data-ttu-id="d0250-182">부울 함수</span><span class="sxs-lookup"><span data-stu-id="d0250-182">Boolean functions</span></span>|`lang()`|  
|<span data-ttu-id="d0250-183">숫자 함수</span><span class="sxs-lookup"><span data-stu-id="d0250-183">Numeric functions</span></span>|<span data-ttu-id="d0250-184">`sum()`, `floor()`, `ceiling()`, `round()`</span><span class="sxs-lookup"><span data-stu-id="d0250-184">`sum()`, `floor()`, `ceiling()`, `round()`</span></span>|  
|<span data-ttu-id="d0250-185">Union 연산자</span><span class="sxs-lookup"><span data-stu-id="d0250-185">Union operator</span></span>|<span data-ttu-id="d0250-186">&#124;</span><span class="sxs-lookup"><span data-stu-id="d0250-186">&#124;</span></span>|  
  
 <span data-ttu-id="d0250-187">템플릿에 XPath 쿼리를 지정할 때는 다음 동작에 유의하십시오.</span><span class="sxs-lookup"><span data-stu-id="d0250-187">When you specify XPath queries in a template, note the following behavior:</span></span>  
  
-   <span data-ttu-id="d0250-188">XPath는 < 또는 XML에서 특수 한 의미를 갖는 & (그리고 템플릿이 XML 문서인)와 같은 문자를 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d0250-188">XPath can contain characters such as < or & that have special meanings in XML (and template is an XML document).</span></span> <span data-ttu-id="d0250-189">XML &-인코딩을 사용 하 여 이러한 문자를 이스케이프 하거나 URL에서 XPath를 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0250-189">You must escape these characters using XML &-encoding, or specify the XPath in the URL.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0250-190">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d0250-190">See Also</span></span>  
 [<span data-ttu-id="d0250-191">SQLXML 4.0의 XPath 쿼리 사용</span><span class="sxs-lookup"><span data-stu-id="d0250-191">Using XPath Queries in SQLXML 4.0</span></span>](using-xpath-queries-in-sqlxml-4-0.md)  
  
  
