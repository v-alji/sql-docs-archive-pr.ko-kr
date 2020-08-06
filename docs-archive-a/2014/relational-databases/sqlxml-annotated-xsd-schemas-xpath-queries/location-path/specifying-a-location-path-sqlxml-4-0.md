---
title: 위치 경로 지정 (SQLXML 4.0) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- absolute location path
- node-set [SQLXML]
- XPath queries [SQLXML], location paths
- relative location path [SQLXML]
- location path for XPath query
ms.assetid: a23a2b75-bc69-49f0-99db-05e14dc15bc0
author: rothja
ms.author: jroth
ms.openlocfilehash: 4dfa1717afe55c1599ccaba4b5d044c6e5a20e84
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651585"
---
# <a name="specifying-a-location-path-sqlxml-40"></a><span data-ttu-id="4bca9-102">위치 경로 지정(SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="4bca9-102">Specifying a Location Path (SQLXML 4.0)</span></span>
  <span data-ttu-id="4bca9-103">XPath 쿼리는 식 형식으로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="4bca9-103">XPath queries are specified in the form of an expression.</span></span> <span data-ttu-id="4bca9-104">식에는 다양한 종류가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4bca9-104">There are various kinds of expressions.</span></span> <span data-ttu-id="4bca9-105">위치 경로는 컨텍스트 노드에 상대적인 노드 집합을 선택하는 식이고</span><span class="sxs-lookup"><span data-stu-id="4bca9-105">A location path is an expression that selects a set of nodes relative to the context node.</span></span> <span data-ttu-id="4bca9-106">위치 경로에 대한 평가 결과는 노드 집합입니다.</span><span class="sxs-lookup"><span data-stu-id="4bca9-106">The result of evaluating a location path is a node-set.</span></span>  
  
## <a name="types-of-location-paths"></a><span data-ttu-id="4bca9-107">위치 경로 유형</span><span class="sxs-lookup"><span data-stu-id="4bca9-107">Types of Location Paths</span></span>  
 <span data-ttu-id="4bca9-108">위치 경로는 다음 중 한 가지 형식으로 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4bca9-108">A location path can take either of these forms:</span></span>  
  
-   <span data-ttu-id="4bca9-109">**절대 위치 경로**</span><span class="sxs-lookup"><span data-stu-id="4bca9-109">**Absolute location path**</span></span>  
  
     <span data-ttu-id="4bca9-110">절대 위치 경로는 문서의 루트 노드에서 시작되고</span><span class="sxs-lookup"><span data-stu-id="4bca9-110">An absolute location path starts at the root node of the document.</span></span> <span data-ttu-id="4bca9-111">슬래시 표시(/)와 그 뒤에 상대 위치 경로(옵션)로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="4bca9-111">It consists of a slash mark (/) optionally followed by a relative location path.</span></span> <span data-ttu-id="4bca9-112">슬래시 표시(/)는 문서의 루트 노드를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="4bca9-112">The slash mark (/) selects the root node of the document.</span></span>  
  
-   <span data-ttu-id="4bca9-113">**상대 위치 경로**</span><span class="sxs-lookup"><span data-stu-id="4bca9-113">**Relative location path**</span></span>  
  
     <span data-ttu-id="4bca9-114">상대 위치 경로는 문서의 컨텍스트 노드에서 시작되고</span><span class="sxs-lookup"><span data-stu-id="4bca9-114">A relative location path starts at the context node in the document.</span></span> <span data-ttu-id="4bca9-115">슬래시 표시(/)로 구분된 하나 이상의 위치 단계의 시퀀스로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="4bca9-115">A location path consists of a sequence of one or more location steps separated by a slash mark (/).</span></span> <span data-ttu-id="4bca9-116">각 단계는 컨텍스트 노드에 상대적인 노드 집합을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="4bca9-116">Each step selects a set of nodes relative to the context node.</span></span> <span data-ttu-id="4bca9-117">초기 단계 시퀀스는 컨텍스트 노드에 상대적인 노드 집합을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="4bca9-117">The initial sequence of steps selects a set of nodes relative to a context node.</span></span> <span data-ttu-id="4bca9-118">이 집합의 각 노드는 다음 단계에 대한 컨텍스트 노드로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="4bca9-118">Each node in that set is used as a context node for the following step.</span></span> <span data-ttu-id="4bca9-119">해당 단계로 식별되는 노드 집합은 서로 조인되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4bca9-119">The sets of nodes identified by that step are joined.</span></span> <span data-ttu-id="4bca9-120">예를 들어 **child:: Order/child:: OrderDetail** 은 **\<OrderDetail>** **\<Order>** 컨텍스트 노드의 요소 자식의 요소 자식을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="4bca9-120">For example, **child::Order/child::OrderDetail** selects the **\<OrderDetail>** element children of the **\<Order>** element children of the context node.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="4bca9-121">SQLXML 4.0의 XPath 구현에서는 명시적으로 절대 XPath가 아닌 XPath까지 포함하여 모든 XPath 쿼리가 루트 컨텍스트에서 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="4bca9-121">In the SQLXML 4.0 implementation of XPath, every XPath query begins at the root context, even if the XPath is not explicitly absolute.</span></span> <span data-ttu-id="4bca9-122">예를 들어 "Customer"로 시작하는 XPath 쿼리는 "/Customer"로 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="4bca9-122">For example, an XPath query beginning with "Customer" is treated as "/Customer".</span></span> <span data-ttu-id="4bca9-123">XPath query **customer [Order]** 에서 고객은 루트 컨텍스트에서 시작 하지만 Order는 고객 컨텍스트에서 시작 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4bca9-123">In the XPath query **Customer[Order]**, Customer begins at the root context, but Order begins at the Customer context.</span></span> <span data-ttu-id="4bca9-124">자세한 내용은 [&#40;는 XPath 쿼리 사용 소개 SQLXML 4.0&#41;](../introduction-to-using-xpath-queries-sqlxml-4-0.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="4bca9-124">For more information, see [Introduction to Using XPath Queries &#40;SQLXML 4.0&#41;](../introduction-to-using-xpath-queries-sqlxml-4-0.md).</span></span>  
  
## <a name="location-steps"></a><span data-ttu-id="4bca9-125">위치 단계</span><span class="sxs-lookup"><span data-stu-id="4bca9-125">Location Steps</span></span>  
 <span data-ttu-id="4bca9-126">위치 경로(절대 또는 상대)는 다음의 세 부분을 포함하는 위치 단계로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="4bca9-126">A location path (absolute or relative) is composed of location steps that contain three parts:</span></span>  
  
-   <span data-ttu-id="4bca9-127">**축**</span><span class="sxs-lookup"><span data-stu-id="4bca9-127">**Axis**</span></span>  
  
     <span data-ttu-id="4bca9-128">축은 위치 단계에서 선택되는 노드와 컨텍스트 노드 간의 트리 관계를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="4bca9-128">The axis specifies the tree relationship between the nodes selected by the location step and the context node.</span></span> <span data-ttu-id="4bca9-129">축에 사용할 수 있는 값은 `parent`, `child`, `attribute` 및 `self`입니다.</span><span class="sxs-lookup"><span data-stu-id="4bca9-129">The `parent`, `child`, `attribute`, and `self` axes are supported.</span></span> <span data-ttu-id="4bca9-130">위치 경로에서 `child` 축을 지정하면 쿼리에서 선택되는 모든 노드가 컨텍스트 노드의 자식입니다.</span><span class="sxs-lookup"><span data-stu-id="4bca9-130">If a `child` axis is specified in the location path, all the nodes selected by the query are the children of the context node.</span></span> <span data-ttu-id="4bca9-131">`parent` 축을 지정하면 선택되는 노드가 컨텍스트 노드의 부모 노드입니다.</span><span class="sxs-lookup"><span data-stu-id="4bca9-131">If a `parent` axis is specified, the node selected is the parent node of the context node.</span></span> <span data-ttu-id="4bca9-132">`attribute` 축을 지정하면 선택되는 노드가 컨텍스트 노드의 특성입니다.</span><span class="sxs-lookup"><span data-stu-id="4bca9-132">If an `attribute` axis is specified, the nodes selected are the attributes of the context node.</span></span>  
  
-   <span data-ttu-id="4bca9-133">**노드 테스트**</span><span class="sxs-lookup"><span data-stu-id="4bca9-133">**Node test**</span></span>  
  
     <span data-ttu-id="4bca9-134">노드 테스트는 위치 단계에서 선택되는 노드 유형을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="4bca9-134">A node test specifies the node type selected by the location step.</span></span> <span data-ttu-id="4bca9-135">모든 축(`child`, `parent`, `attribute` 및 `self`)에는 주 노드 유형이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4bca9-135">Every axis (`child`, `parent`, `attribute`, and `self`) has a principal node type.</span></span> <span data-ttu-id="4bca9-136">축의 경우 `attribute` 주 노드 형식은 **\<attribute>** 입니다.</span><span class="sxs-lookup"><span data-stu-id="4bca9-136">For the `attribute` axis, the principal node type is **\<attribute>**.</span></span> <span data-ttu-id="4bca9-137">`parent`, `child` 및 `self` 축의 경우 주 노드 형식은 **\<element>** 입니다.</span><span class="sxs-lookup"><span data-stu-id="4bca9-137">For the `parent`, `child`, and `self` axes, the principal node type is **\<element>**.</span></span>  
  
     <span data-ttu-id="4bca9-138">예를 들어 위치 경로가 **child:: Customer**를 지정 하는 경우 **\<Customer>** 컨텍스트 노드의 자식 요소가 선택 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4bca9-138">For example, if the location path specifies **child::Customer**, the **\<Customer>** element children of the context node are selected.</span></span> <span data-ttu-id="4bca9-139">축에는 `child` 주 노드 형식이 있으므로 customer 노드 테스트는 customer가 **\<element>** 노드인 경우 TRUE입니다 **\<element>** .</span><span class="sxs-lookup"><span data-stu-id="4bca9-139">Because the `child` axis has **\<element>** as its principal node type, the node test, Customer, is TRUE if Customer is an **\<element>** node.</span></span>  
  
-   <span data-ttu-id="4bca9-140">**선택 조건자(0개 이상)**</span><span class="sxs-lookup"><span data-stu-id="4bca9-140">**Selection predicates (zero or more)**</span></span>  
  
     <span data-ttu-id="4bca9-141">조건자는 축을 기준으로 노드 집합을 필터링합니다.</span><span class="sxs-lookup"><span data-stu-id="4bca9-141">A predicate filters a node-set with respect to an axis.</span></span> <span data-ttu-id="4bca9-142">XPath 식에서 선택 조건자를 지정하는 것은 SELECT 문에서 WHERE 절을 지정하는 것과 비슷합니다.</span><span class="sxs-lookup"><span data-stu-id="4bca9-142">Specifying selection predicates in an XPath expression is similar to specifying a WHERE clause in a SELECT statement.</span></span> <span data-ttu-id="4bca9-143">조건자는 대괄호로 묶어서 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="4bca9-143">The predicate is specified between brackets.</span></span> <span data-ttu-id="4bca9-144">선택 조건자에 지정된 테스트를 적용하면 노드 테스트에서 반환되는 노드가 필터링됩니다.</span><span class="sxs-lookup"><span data-stu-id="4bca9-144">Applying the test specified in the selection predicates filters the nodes returned by the node test.</span></span> <span data-ttu-id="4bca9-145">노드 집합의 각 노드를 필터링하기 위해 해당 노드가 컨텍스트 노드로 사용되고 노드 집합의 노드 수가 컨텍스트 크기로 사용되어 조건자 식이 평가됩니다.</span><span class="sxs-lookup"><span data-stu-id="4bca9-145">For each node in the node-set to be filtered, the predicate expression is evaluated with that node as the context node, with the number of nodes in the node-set as context size.</span></span> <span data-ttu-id="4bca9-146">노드에 대한 조건자 식이 TRUE로 평가되면 해당 노드가 결과 노드 집합에 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="4bca9-146">If the predicate expression evaluates to TRUE for that node, the node is included in the resulting node-set.</span></span>  
  
     <span data-ttu-id="4bca9-147">위치 단계의 구문은 두 개의 콜론(::)으로 구분된 축 이름과 노드 테스트, 그리고 각각 대괄호로 묶인 0개 이상의 식으로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="4bca9-147">The syntax for a location step is the axis name and node test separated by two colons (::), followed by zero or more expressions, each in square brackets.</span></span> <span data-ttu-id="4bca9-148">예를 들어 XPath 식 (위치 경로) **child:: Customer [ @CustomerID = ' ALFKI ']** 는 **\<Customer>** 컨텍스트 노드의 모든 요소 자식을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="4bca9-148">For example, the XPath expression (location path) **child::Customer[@CustomerID='ALFKI']** selects all the **\<Customer>** element children of the context node.</span></span> <span data-ttu-id="4bca9-149">그런 다음 조건자의 테스트가 **\<Customer>** 해당 **CustomerID** 특성에 대해 특성 값이 ' ALFKI ' 인 요소 노드만 반환 하는 노드 집합에 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4bca9-149">Then the test in the predicate is applied to the node-set, which returns only the **\<Customer>** element nodes with attribute value 'ALFKI' for its **CustomerID** attribute.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4bca9-150">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="4bca9-150">In This Section</span></span>  
 [<span data-ttu-id="4bca9-151">&#40;SQLXML 4.0&#41;축을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="4bca9-151">Specifying an Axis &#40;SQLXML 4.0&#41;</span></span>](specifying-an-axis-sqlxml-4-0.md)  
 <span data-ttu-id="4bca9-152">축을 지정하는 예를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="4bca9-152">Provides examples of specifying an axis.</span></span>  
  
 [<span data-ttu-id="4bca9-153">위치 경로에 노드 테스트 지정 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="4bca9-153">Specifying a Node Test in the Location Path &#40;SQLXML 4.0&#41;</span></span>](specifying-a-node-test-in-the-location-path-sqlxml-4-0.md)  
 <span data-ttu-id="4bca9-154">노드 테스트를 지정하는 예를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="4bca9-154">Provides examples of specifying a node test.</span></span>  
  
 [<span data-ttu-id="4bca9-155">위치 경로에서 선택 조건자 지정 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="4bca9-155">Specifying Selection Predicates in the Location Path &#40;SQLXML 4.0&#41;</span></span>](specifying-selection-predicates-in-the-location-path-sqlxml-4-0.md)  
 <span data-ttu-id="4bca9-156">선택 조건자를 지정하는 예를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="4bca9-156">Provides examples of specifying selection predicates.</span></span>  
  
  
