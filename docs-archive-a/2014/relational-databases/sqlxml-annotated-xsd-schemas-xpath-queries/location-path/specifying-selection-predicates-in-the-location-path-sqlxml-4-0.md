---
title: 위치 경로에서 선택 조건자 지정 (SQLXML 4.0) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- XPath queries [SQLXML], predicates
- predicates [SQLXML]
- position-based filtering [SQLXML]
- XPath queries [SQLXML], location paths
- filtering [SQLXML]
- location path for XPath query
ms.assetid: dbef4cf4-a89b-4d7e-b72b-4062f7b29a80
author: rothja
ms.author: jroth
ms.openlocfilehash: d323558556fb05d350e48ea9218a8e9b8dc9b5c9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651578"
---
# <a name="specifying-selection-predicates-in-the-location-path-sqlxml-40"></a><span data-ttu-id="55137-102">위치 경로에서 선택 조건자 지정(SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="55137-102">Specifying Selection Predicates in the Location Path (SQLXML 4.0)</span></span>
  <span data-ttu-id="55137-103">조건자는 SELECT 문의 WHERE 절과 유사하게 축을 기준으로 노드 집합을 필터링합니다.</span><span class="sxs-lookup"><span data-stu-id="55137-103">A predicate filters a node-set with respect to an axis (similar to a WHERE clause in a SELECT statement).</span></span> <span data-ttu-id="55137-104">조건자는 대괄호로 묶어서 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="55137-104">The predicate is specified between brackets.</span></span> <span data-ttu-id="55137-105">노드 집합의 각 노드를 필터링하기 위해 해당 노드가 컨텍스트 노드로 사용되고 노드 집합의 노드 수가 컨텍스트 크기로 사용되어 조건자 식이 평가됩니다.</span><span class="sxs-lookup"><span data-stu-id="55137-105">For each node in the node-set to be filtered, the predicate expression is evaluated with that node as the context node, with the number of nodes in the node-set as context size.</span></span> <span data-ttu-id="55137-106">노드에 대한 조건자 식이 TRUE로 평가되면 해당 노드가 결과 노드 집합에 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="55137-106">If the predicate expression evaluates to TRUE for that node, the node is included in the resulting node-set.</span></span>  
  
 <span data-ttu-id="55137-107">XPath에서도 위치 기반 필터링이 가능합니다.</span><span class="sxs-lookup"><span data-stu-id="55137-107">XPath also allows position-based filtering.</span></span> <span data-ttu-id="55137-108">숫자로 계산되는 조건자 식이 필요한 서수 노드를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="55137-108">A predicate expression evaluating to a number selects that ordinal node.</span></span> <span data-ttu-id="55137-109">예를 들어 위치 경로 `Customer[3]`은 세 번째 고객을 반환하지만,</span><span class="sxs-lookup"><span data-stu-id="55137-109">For example, the location path `Customer[3]` returns the third customer.</span></span> <span data-ttu-id="55137-110">이와 같은 숫자 조건자는 지원되지 않고</span><span class="sxs-lookup"><span data-stu-id="55137-110">Such numeric predicates are not supported.</span></span> <span data-ttu-id="55137-111">부울 결과를 반환하는 조건자 식만 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="55137-111">Only predicate expressions that return a Boolean result are supported.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="55137-112">Xpath의 xpath 구현에 대 한 제한 사항 및이를 W3C 사양 간의 차이점에 대 한 자세한 내용은 [&#40;Xpath 쿼리 사용 소개&#41;SQLXML 4.0 ](../introduction-to-using-xpath-queries-sqlxml-4-0.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="55137-112">For information about the limitations of this XPath implementation of XPath and the differences between it and the W3C specification, see [Introduction to Using XPath Queries &#40;SQLXML 4.0&#41;](../introduction-to-using-xpath-queries-sqlxml-4-0.md).</span></span>  
  
## <a name="selection-predicate-example-1"></a><span data-ttu-id="55137-113">선택 조건자: 예 1</span><span class="sxs-lookup"><span data-stu-id="55137-113">Selection Predicate: Example 1</span></span>  
 <span data-ttu-id="55137-114">다음 XPath 식 (위치 경로)은 현재 컨텍스트 노드에서 **\<Customer>** ALFKI 값이 인 **CustomerID** 특성이 있는 모든 요소 자식을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="55137-114">The following XPath expression (location path) selects from the current context node all the **\<Customer>** element children that have the **CustomerID** attribute with value of ALFKI:</span></span>  
  
```  
/child::Customer[attribute::CustomerID="ALFKI"]  
```  
  
 <span data-ttu-id="55137-115">이 XPath 쿼리에서 `child` 및 `attribute`는 축 이름이고,</span><span class="sxs-lookup"><span data-stu-id="55137-115">In this XPath query, `child` and `attribute` are axis names.</span></span> <span data-ttu-id="55137-116">`Customer`는 노드 테스트 (가 `Customer` **\<element node>** **\<element>** 축의 주 노드 유형 이므로가 인 경우 TRUE `child` )입니다.</span><span class="sxs-lookup"><span data-stu-id="55137-116">`Customer` is the node test (TRUE if `Customer` is an **\<element node>**, because **\<element>** is the principal node type for the `child` axis).</span></span> <span data-ttu-id="55137-117">`attribute::CustomerID="ALFKI"`는 조건자입니다.</span><span class="sxs-lookup"><span data-stu-id="55137-117">`attribute::CustomerID="ALFKI"` is the predicate.</span></span> <span data-ttu-id="55137-118">조건자에서는 `attribute` 축이 고 `CustomerID` 는 노드 테스트 ( **CustomerID** **\<attribute>** 가 축의 주 노드 유형 이므로 CustomerID가 컨텍스트 노드의 특성인 경우 TRUE `attribute` )입니다.</span><span class="sxs-lookup"><span data-stu-id="55137-118">In the predicate, `attribute` is the axis and `CustomerID` is the node test (TRUE if **CustomerID** is an attribute of the context node, because **\<attribute>** is the principal node type of `attribute` axis).</span></span>  
  
 <span data-ttu-id="55137-119">축약형 구문을 사용하여 XPath 쿼리를 다음과 같이 지정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="55137-119">Using the abbreviated syntax, the XPath query can also be specified as:</span></span>  
  
```  
/Customer[@CustomerID="ALFKI"]  
```  
  
## <a name="selection-predicate-example-2"></a><span data-ttu-id="55137-120">선택 조건자: 예 2</span><span class="sxs-lookup"><span data-stu-id="55137-120">Selection Predicate: Example 2</span></span>  
 <span data-ttu-id="55137-121">다음 XPath 식 (위치 경로)은 현재 컨텍스트 노드에서 **\<Order>** 값이 1 인 **SalesOrderID** 특성이 있는 모든 손자를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="55137-121">The following XPath expression (location path) selects from the current context node all the **\<Order>** grandchildren that have the **SalesOrderID** attribute with the value 1:</span></span>  
  
```  
/child::Customer/child::Order[attribute::SalesOrderID="1"]  
```  
  
 <span data-ttu-id="55137-122">이 XPath 식에서 `child` 및 `attribute`는 축 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="55137-122">In this XPath expression, `child` and `attribute` are the axis names.</span></span> <span data-ttu-id="55137-123">`Customer`, `Order` 및 `SalesOrderID`는 노드 테스트이고,</span><span class="sxs-lookup"><span data-stu-id="55137-123">`Customer`, `Order`, and `SalesOrderID` are the node tests.</span></span> <span data-ttu-id="55137-124">`attribute::OrderID="1"`는 조건자입니다.</span><span class="sxs-lookup"><span data-stu-id="55137-124">`attribute::OrderID="1"` is the predicate.</span></span>  
  
 <span data-ttu-id="55137-125">축약형 구문을 사용하여 XPath 쿼리를 다음과 같이 지정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="55137-125">Using the abbreviated syntax, the XPath query can also be specified as:</span></span>  
  
```  
/Customer/Order[@SalesOrderID="1"]  
```  
  
## <a name="selection-predicate-example-3"></a><span data-ttu-id="55137-126">선택 조건자: 예제 3</span><span class="sxs-lookup"><span data-stu-id="55137-126">Selection Predicate: Example 3</span></span>  
 <span data-ttu-id="55137-127">다음 XPath 식 (위치 경로)은 현재 컨텍스트 노드에서 **\<Customer>** 하나 이상의 자식을 포함 하는 모든 자식을 선택 합니다 **\<ContactName>** .</span><span class="sxs-lookup"><span data-stu-id="55137-127">The following XPath expression (location path) selects from the current context node all the **\<Customer>** children that have one or more **\<ContactName>** children:</span></span>  
  
```  
child::Customer[child::ContactName]  
```  
  
 <span data-ttu-id="55137-128">이 예에서는이 **\<ContactName>** XML 문서에서 요소의 자식 요소 라고 가정 합니다 .이 요소는 **\<Customer>** 주석이 추가 된 XSD 스키마에서 *요소 중심의 매핑* 이라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="55137-128">This example assumes that the **\<ContactName>** is a child element of the **\<Customer>** element in the XML document, which is referred to as *element-centric mapping* in an annotated XSD schema.</span></span>  
  
 <span data-ttu-id="55137-129">이 XPath 식에서 `child`는 축 이름이고,</span><span class="sxs-lookup"><span data-stu-id="55137-129">In this XPath expression, `child` is the axis name.</span></span> <span data-ttu-id="55137-130">`Customer`는 노드 테스트 (가 `Customer` **\<element>** **\<element>** 축에 대 한 주 노드 유형 이므로가 노드인 경우 TRUE `child` )입니다.</span><span class="sxs-lookup"><span data-stu-id="55137-130">`Customer` is the node test (TRUE if `Customer` is an **\<element>** node, because **\<element>** is the principal node type for `child` axis).</span></span> <span data-ttu-id="55137-131">`child::ContactName`는 조건자입니다.</span><span class="sxs-lookup"><span data-stu-id="55137-131">`child::ContactName` is the predicate.</span></span> <span data-ttu-id="55137-132">조건자에서는 `child` 축이 고 `ContactName` 는 노드 테스트 ( `ContactName` 가 노드인 경우 TRUE)입니다 **\<element>** .</span><span class="sxs-lookup"><span data-stu-id="55137-132">In the predicate, `child` is the axis and `ContactName` is the node test (TRUE if `ContactName` is an **\<element>** node).</span></span>  
  
 <span data-ttu-id="55137-133">이 식은 **\<Customer>** 요소 자식이 있는 컨텍스트 노드의 요소 자식만 반환 합니다 **\<ContactName>** .</span><span class="sxs-lookup"><span data-stu-id="55137-133">This expression returns only the **\<Customer>** element children of the context node that have **\<ContactName>** element children.</span></span>  
  
 <span data-ttu-id="55137-134">축약형 구문을 사용하여 XPath 쿼리를 다음과 같이 지정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="55137-134">Using the abbreviated syntax, the XPath query can also be specified as:</span></span>  
  
```  
Customer[ContactName]  
```  
  
## <a name="selection-predicate-example-4"></a><span data-ttu-id="55137-135">선택 조건자: 예제 4</span><span class="sxs-lookup"><span data-stu-id="55137-135">Selection Predicate: Example 4</span></span>  
 <span data-ttu-id="55137-136">다음 XPath 식은 **\<Customer>** 요소 자식이 없는 컨텍스트 노드의 요소 자식을 선택 합니다 **\<ContactName>** .</span><span class="sxs-lookup"><span data-stu-id="55137-136">The following XPath expression selects **\<Customer>** element children of the context node that do not have **\<ContactName>** element children:</span></span>  
  
```  
child::Customer[not(child::ContactName)]  
```  
  
 <span data-ttu-id="55137-137">이 예에서는이 **\<ContactName>** **\<Customer>** XML 문서에서 요소의 자식 요소이 고 ContactName 필드가 데이터베이스에 필요 하지 않다고 가정 합니다.</span><span class="sxs-lookup"><span data-stu-id="55137-137">This example assumes that **\<ContactName>** is a child element of the **\<Customer>** element in the XML document, and the ContactName field is not required in the database.</span></span>  
  
 <span data-ttu-id="55137-138">이 예에서 `child`는 축이고,</span><span class="sxs-lookup"><span data-stu-id="55137-138">In this example, `child` is the axis.</span></span> <span data-ttu-id="55137-139">`Customer`노드 테스트 (가 노드인 경우 TRUE `Customer` )입니다 \<element> .</span><span class="sxs-lookup"><span data-stu-id="55137-139">`Customer` is the node test (TRUE if `Customer` is an \<element> node).</span></span> <span data-ttu-id="55137-140">`not(child::ContactName)`는 조건자입니다.</span><span class="sxs-lookup"><span data-stu-id="55137-140">`not(child::ContactName)` is the predicate.</span></span> <span data-ttu-id="55137-141">조건자에서는 `child` 축이 고 `ContactName` 는 노드 테스트 ( `ContactName` 가 노드인 경우 TRUE)입니다 \<element> .</span><span class="sxs-lookup"><span data-stu-id="55137-141">In the predicate, `child` is the axis and `ContactName` is the node test (TRUE if `ContactName` is an \<element> node).</span></span>  
  
 <span data-ttu-id="55137-142">축약형 구문을 사용하여 XPath 쿼리를 다음과 같이 지정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="55137-142">Using the abbreviated syntax, the XPath query can also be specified as:</span></span>  
  
```  
Customer[not(ContactName)]  
```  
  
## <a name="selection-predicate-example-5"></a><span data-ttu-id="55137-143">선택 조건자: 예제 5</span><span class="sxs-lookup"><span data-stu-id="55137-143">Selection Predicate: Example 5</span></span>  
 <span data-ttu-id="55137-144">다음 XPath 식은 CustomerID 특성이 있는 모든 자식을 현재 컨텍스트 노드에서 선택 합니다 **\<Customer>** . **CustomerID**</span><span class="sxs-lookup"><span data-stu-id="55137-144">The following XPath expression selects from the current context node all the **\<Customer>** children that have the **CustomerID** attribute:</span></span>  
  
```  
child::Customer[attribute::CustomerID]  
```  
  
 <span data-ttu-id="55137-145">이 예제에서는 `child` 축과 `Customer` 노드 테스트 ( `Customer` 가 노드인 경우 TRUE)입니다 \<element> .</span><span class="sxs-lookup"><span data-stu-id="55137-145">In this example, `child` is the axis and `Customer` is node test (TRUE if `Customer` is an \<element> node).</span></span> <span data-ttu-id="55137-146">`attribute::CustomerID`는 조건자입니다.</span><span class="sxs-lookup"><span data-stu-id="55137-146">`attribute::CustomerID` is the predicate.</span></span> <span data-ttu-id="55137-147">조건자에서는 `attribute` 축이 고 `CustomerID` 는 조건자 ( `CustomerID` 가 노드인 경우 TRUE)입니다 **\<attribute>** .</span><span class="sxs-lookup"><span data-stu-id="55137-147">In the predicate, `attribute` is the axis and `CustomerID` is the predicate (TRUE if `CustomerID` is an **\<attribute>** node).</span></span>  
  
 <span data-ttu-id="55137-148">축약형 구문을 사용하여 XPath 쿼리를 다음과 같이 지정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="55137-148">Using the abbreviated syntax, the XPath query can also be specified as:</span></span>  
  
```  
Customer[@CustomerID]  
```  
  
## <a name="selection-predicate-example-6"></a><span data-ttu-id="55137-149">선택 조건자: 예제 6</span><span class="sxs-lookup"><span data-stu-id="55137-149">Selection Predicate: Example 6</span></span>  
 <span data-ttu-id="55137-150">다음 예에서 볼 수 있는 것처럼 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] SQLXML 4.0은 조건자에 교차곱을 포함하는 XPath 쿼리를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="55137-150">[!INCLUDE[msCoName](../../../includes/msconame-md.md)] SQLXML 4.0 includes support for XPath queries that contain a cross-product in the predicate, as shown in the following example:</span></span>  
  
```  
Customer[Order/@OrderDate=Order/@ShipDate]  
```  
  
 <span data-ttu-id="55137-151">이 쿼리는 `Order`가 `OrderDate` 중 하나의 `ShipDate`와 동일한 `Order`가 있는 모든 고객을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="55137-151">This query selects all customers with any `Order` for which the `OrderDate` equals the `ShipDate` of any `Order`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55137-152">참고 항목</span><span class="sxs-lookup"><span data-stu-id="55137-152">See Also</span></span>  
 <span data-ttu-id="55137-153">[SQLXML 4.0&#41;&#40;주석이 추가 된 XSD 스키마 소개](../../sqlxml/annotated-xsd-schemas/introduction-to-annotated-xsd-schemas-sqlxml-4-0.md) </span><span class="sxs-lookup"><span data-stu-id="55137-153">[Introduction to Annotated XSD Schemas &#40;SQLXML 4.0&#41;](../../sqlxml/annotated-xsd-schemas/introduction-to-annotated-xsd-schemas-sqlxml-4-0.md) </span></span>  
 [<span data-ttu-id="55137-154">클라이언트 쪽 XML 서식 지정 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="55137-154">Client-side XML Formatting &#40;SQLXML 4.0&#41;</span></span>](../../sqlxml/formatting/client-side-xml-formatting-sqlxml-4-0.md)  
  
  
