---
title: 위치 경로에 노드 테스트 지정 (SQLXML 4.0) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- XPath queries [SQLXML], location paths
- principal node types [SQLXML]
- node tests [SQLXML]
- location path for XPath query
ms.assetid: f46c30bf-1e24-4435-9ac2-f8ba43a8ff94
author: rothja
ms.author: jroth
ms.openlocfilehash: 9d8535154f4b481c8a47bfdb8b801e3136a1ef0f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651583"
---
# <a name="specifying-a-node-test-in-the-location-path-sqlxml-40"></a><span data-ttu-id="a86d8-102">위치 경로에 노드 테스트 지정(SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="a86d8-102">Specifying a Node Test in the Location Path (SQLXML 4.0)</span></span>
  <span data-ttu-id="a86d8-103">노드 테스트는 위치 단계에서 선택되는 노드 유형을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a86d8-103">A node test specifies the node type selected by the location step.</span></span> <span data-ttu-id="a86d8-104">모든 축(`child`, `parent`, `attribute` 또는 `self`)에는 주 노드 유형이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a86d8-104">Every axis (`child`, `parent`, `attribute`, or `self`) has a principal node type.</span></span> <span data-ttu-id="a86d8-105">축의 경우 `attribute` 주 노드 형식은 **\<attribute>** 입니다.</span><span class="sxs-lookup"><span data-stu-id="a86d8-105">For the `attribute` axis, the principal node type is **\<attribute>**.</span></span> <span data-ttu-id="a86d8-106">`parent`, `child` 및 `self` 축의 경우 주 노드 형식은 **\<element>** 입니다.</span><span class="sxs-lookup"><span data-stu-id="a86d8-106">For the `parent`, `child`, and `self` axes, the principal node type is **\<element>**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a86d8-107">와일드카드 노드 테스트 \*(예: `child::*`)는 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a86d8-107">The wildcard node test \* (for example, `child::*`) is not supported.</span></span>  
  
## <a name="node-test-example-1"></a><span data-ttu-id="a86d8-108">노드 테스트: 예 1</span><span class="sxs-lookup"><span data-stu-id="a86d8-108">Node Test: Example 1</span></span>  
 <span data-ttu-id="a86d8-109">위치 경로는 `child::Customer` **\<Customer>** 컨텍스트 노드의 요소 자식을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="a86d8-109">The location path `child::Customer` selects **\<Customer>** element children of the context node.</span></span>  
  
 <span data-ttu-id="a86d8-110">이 예에서는 `child`가 축이고 `Customer`가 노드 테스트입니다.</span><span class="sxs-lookup"><span data-stu-id="a86d8-110">In this example, `child` is the axis and `Customer` is the node test.</span></span> <span data-ttu-id="a86d8-111">축에 대 한 주 노드 유형은 `child` **\<element>** 입니다.</span><span class="sxs-lookup"><span data-stu-id="a86d8-111">The principal node type for the `child` axis is **\<element>**.</span></span> <span data-ttu-id="a86d8-112">따라서 노드가 노드인 경우 노드 테스트는 TRUE입니다 **\<Customer>** **\<element>** .</span><span class="sxs-lookup"><span data-stu-id="a86d8-112">Therefore, the node test is TRUE if the **\<Customer>** node is an **\<element>** node.</span></span> <span data-ttu-id="a86d8-113">컨텍스트 노드에 **\<Customer>** 자식이 없으면 빈 노드 집합이 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a86d8-113">If the context node has no **\<Customer>** children, an empty set of nodes is returned.</span></span>  
  
## <a name="node-test-example-2"></a><span data-ttu-id="a86d8-114">노드 테스트: 예 2</span><span class="sxs-lookup"><span data-stu-id="a86d8-114">Node Test: Example 2</span></span>  
 <span data-ttu-id="a86d8-115">위치 경로는 `attribute::CustomerID` 컨텍스트 노드의 **CustomerID** 특성을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="a86d8-115">The location path `attribute::CustomerID` selects the **CustomerID** attribute of the context node.</span></span>  
  
 <span data-ttu-id="a86d8-116">이 예에서는 `attribute`가 축이고 `CustomerID`가 노드 테스트입니다.</span><span class="sxs-lookup"><span data-stu-id="a86d8-116">In the example, `attribute` is the axis and `CustomerID` is the node test.</span></span> <span data-ttu-id="a86d8-117">축의 주 노드 형식은 `attribute` **\<attribute>** 입니다.</span><span class="sxs-lookup"><span data-stu-id="a86d8-117">The principal node type of the `attribute` axis is **\<attribute>**.</span></span> <span data-ttu-id="a86d8-118">따라서 **CustomerID** 가 노드인 경우 노드 테스트는 TRUE입니다 **\<attribute>** .</span><span class="sxs-lookup"><span data-stu-id="a86d8-118">Therefore, the node test is TRUE if **CustomerID** is an **\<attribute>** node.</span></span> <span data-ttu-id="a86d8-119">컨텍스트 노드에 **CustomerID**가 없으면 빈 노드 집합이 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a86d8-119">If the context node has no **CustomerID**, an empty set of nodes is returned.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a86d8-120">이 XPath 구현에서 위치 단계가 **\<element>** 스키마에 선언 되지 않은 또는 유형을 참조 하는 경우 **\<attribute>** 오류가 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="a86d8-120">In this implementation of XPath, if a location step refers to an **\<element>** or an **\<attribute>** type that is not declared in the schema, an error is generated.</span></span> <span data-ttu-id="a86d8-121">이 동작은 빈 노드 집합을 반환하는 MSXML에서의 XPath 구현과는 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="a86d8-121">This is different from the implementation of XPath in MSXML, which returns an empty node set.</span></span>  
  
## <a name="abbreviated-syntax-for-the-axes"></a><span data-ttu-id="a86d8-122">축의 축약형 구문</span><span class="sxs-lookup"><span data-stu-id="a86d8-122">Abbreviated Syntax for the Axes</span></span>  
 <span data-ttu-id="a86d8-123">위치 경로에 대한 다음 축약형 구문이 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="a86d8-123">The following abbreviated syntax for the location path is supported:</span></span>  
  
-   <span data-ttu-id="a86d8-124">`attribute::`는 `@` 기호로 축약할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a86d8-124">`attribute::` can be abbreviated to `@`.</span></span>  
  
     <span data-ttu-id="a86d8-125">위치 경로 `Customer[@CustomerID="ALFKI"]`는 `child::Customer[attribute::CustomerID="ALFKI"]`와 같습니다.</span><span class="sxs-lookup"><span data-stu-id="a86d8-125">The location path `Customer[@CustomerID="ALFKI"]` is the same as `child::Customer[attribute::CustomerID="ALFKI"]`.</span></span>  
  
-   <span data-ttu-id="a86d8-126">`child::`는 위치 단계에서 생략할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a86d8-126">`child::` can be omitted from a location step.</span></span>  
  
     <span data-ttu-id="a86d8-127">따라서 기본 축은 `child`이고,</span><span class="sxs-lookup"><span data-stu-id="a86d8-127">Thus, `child` is the default axis.</span></span> <span data-ttu-id="a86d8-128">위치 경로 `Customer/Order`는 `child::Customer/child::Order`와 같습니다.</span><span class="sxs-lookup"><span data-stu-id="a86d8-128">The location path `Customer/Order` is the same as `child::Customer/child::Order`.</span></span>  
  
-   <span data-ttu-id="a86d8-129">`self::node()`는 한 개의 마침표(.)로 축약할 수 있으며, `parent::node()`는 두 개의 마침표(..)로 축약할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a86d8-129">`self::node()` can be abbreviated to one period (.), and `parent::node()` can be abbreviated to two periods (..).</span></span>  
  
  
