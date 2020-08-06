---
title: XPath 데이터 형식 (SQLXML 4.0) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- mapping XDR types to XPath types [SQLXML]
- data types [XPath]
- arithmetic operators
- mapping data types [SQLXML]
- relational operators [SQLXML]
- node-set [SQLXML]
- data types [SQLXML], XPath
- XPath operators [SQLXML]
- XDR data type [SQLXML]
- equality operators [SQLXML]
- XPath conversions [SQLXML]
- converting data types [SQLXML]
- Boolean operators
- XPath queries [SQLXML], data types
- XPath data types [SQLXML]
- operators [SQLXML]
ms.assetid: a90374bf-406f-4384-ba81-59478017db68
author: rothja
ms.author: jroth
ms.openlocfilehash: 846fc5a17ac97d30b6f0ab65fee176ac459c20cc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652730"
---
# <a name="xpath-data-types-sqlxml-40"></a><span data-ttu-id="d1cbe-102">XPath 데이터 형식(SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="d1cbe-102">XPath Data Types (SQLXML 4.0)</span></span>
  [!INCLUDE[msCoName](../../includes/msconame-md.md)]<span data-ttu-id="d1cbe-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], XPath 및 XSD (XML 스키마)는 데이터 형식이 매우 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="d1cbe-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], XPath, and XML Schema (XSD) have very different data types.</span></span> <span data-ttu-id="d1cbe-104">예를 들어 XPath에는 정수나 날짜 데이터 형식이 없지만 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]와 XSD에는 이러한 데이터 형식이 많습니다.</span><span class="sxs-lookup"><span data-stu-id="d1cbe-104">For example, XPath does not have integer or date data types, but [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and XSD have many.</span></span> <span data-ttu-id="d1cbe-105">XSD는 시간 값에 나노초 정밀도를 사용하지만 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서는 최대 1/300초의 정밀도를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="d1cbe-105">XSD uses nanosecond precision for time values, and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] uses at most 1/300-second precision.</span></span> <span data-ttu-id="d1cbe-106">따라서 한 데이터 형식을 다른 데이터 형식에 매핑할 수 없는 경우도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d1cbe-106">Consequently, mapping one data type to another is not always possible.</span></span> <span data-ttu-id="d1cbe-107">데이터 형식을 XSD 데이터 형식에 매핑하는 방법에 대 한 자세한 내용은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [데이터 형식 강제 변환 및 sql: datatype 주석 &#40;SQLXML 4.0&#41;](../sqlxml-annotated-xsd-schemas-using/data-type-coercions-and-the-sql-datatype-annotation-sqlxml-4-0.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="d1cbe-107">For more information about mapping [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data types to XSD data types, see [Data Type Coercions and the sql:datatype Annotation &#40;SQLXML 4.0&#41;](../sqlxml-annotated-xsd-schemas-using/data-type-coercions-and-the-sql-datatype-annotation-sqlxml-4-0.md).</span></span>  
  
 <span data-ttu-id="d1cbe-108">XPath에는 `string` , 및의 세 가지 데이터 형식이 있습니다. `number` `boolean`</span><span class="sxs-lookup"><span data-stu-id="d1cbe-108">XPath has three data types: `string`, `number`, and `boolean`.</span></span> <span data-ttu-id="d1cbe-109">`number` 데이터 형식은 항상 IEEE 754 배정밀도 부동 소수점입니다.</span><span class="sxs-lookup"><span data-stu-id="d1cbe-109">The `number` data type is always an IEEE 754 double-precision floating-point.</span></span> <span data-ttu-id="d1cbe-110">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `float(53)` 데이터 형식은 XPath와 가장 가깝습니다 `number` .</span><span class="sxs-lookup"><span data-stu-id="d1cbe-110">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]`float(53)` data type is the closest to XPath `number`.</span></span> <span data-ttu-id="d1cbe-111">그러나 `float(53)`가 정확하게 IEEE 754와 같은 것은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="d1cbe-111">However, `float(53)` is not exactly IEEE 754.</span></span> <span data-ttu-id="d1cbe-112">예를 들어 NaN(Not-a-Number)과 무한대는 모두 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d1cbe-112">For example, neither NaN (Not-a-Number) nor infinity is used.</span></span> <span data-ttu-id="d1cbe-113">따라서 숫자가 아닌 문자열을 `number`로 변환하고 0으로 나누려고 하면 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="d1cbe-113">Attempting to convert a nonnumeric string to `number` and trying to divide by zero results in an error.</span></span>  
  
## <a name="xpath-conversions"></a><span data-ttu-id="d1cbe-114">XPath 변환</span><span class="sxs-lookup"><span data-stu-id="d1cbe-114">XPath Conversions</span></span>  
 <span data-ttu-id="d1cbe-115">`OrderDetail[@UnitPrice > "10.0"]` 같은 XPath 쿼리를 사용할 경우 암시적/명시적 데이터 형식 변환으로 인해 쿼리의 의미가 미세하게 변경될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d1cbe-115">When you use an XPath query such as `OrderDetail[@UnitPrice > "10.0"]`, implicit and explicit data type conversions can change the meaning of the query in subtle ways.</span></span> <span data-ttu-id="d1cbe-116">따라서 XPath 데이터 형식의 구현 방법을 올바르게 이해하고 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d1cbe-116">Therefore, it is important to understand how XPath data types are implemented.</span></span> <span data-ttu-id="d1cbe-117">XPath 언어 사양, XPath (XML Path Language) 버전 1.0 W3C 제안 권장 사항 8 월 1999은의 W3C 웹 사이트에서 찾을 수 있습니다 http://www.w3.org/TR/1999/PR-xpath-19991008.html .</span><span class="sxs-lookup"><span data-stu-id="d1cbe-117">The XPath language specification, XML Path Language (XPath) version 1.0 W3C Proposed Recommendation 8 October 1999, can be found at the W3C Web site at http://www.w3.org/TR/1999/PR-xpath-19991008.html.</span></span>  
  
 <span data-ttu-id="d1cbe-118">XPath 연산자는 다음의 네 범주로 나뉩니다.</span><span class="sxs-lookup"><span data-stu-id="d1cbe-118">XPath operators are divided into four categories:</span></span>  
  
-   <span data-ttu-id="d1cbe-119">부울 연산자(and, or)</span><span class="sxs-lookup"><span data-stu-id="d1cbe-119">Boolean operators (and, or)</span></span>  
  
-   <span data-ttu-id="d1cbe-120">관계형 연산자 ( \<, > , \<=, > =)</span><span class="sxs-lookup"><span data-stu-id="d1cbe-120">Relational operators (\<, >, \<=, >=)</span></span>  
  
-   <span data-ttu-id="d1cbe-121">같음 연산자(=, !=)</span><span class="sxs-lookup"><span data-stu-id="d1cbe-121">Equality operators (=, !=)</span></span>  
  
-   <span data-ttu-id="d1cbe-122">산술 연산자(+, -, \*, div, mod)</span><span class="sxs-lookup"><span data-stu-id="d1cbe-122">Arithmetic operators (+, -, \*, div, mod)</span></span>  
  
 <span data-ttu-id="d1cbe-123">연산자 범주마다 해당 피연산자를 변환하는 방법이 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="d1cbe-123">Each category of operator converts its operands differently.</span></span> <span data-ttu-id="d1cbe-124">XPath 연산자는 필요한 경우 피연산자를 암시적으로 변환합니다.</span><span class="sxs-lookup"><span data-stu-id="d1cbe-124">XPath operators implicitly convert their operands if necessary.</span></span> <span data-ttu-id="d1cbe-125">산술 연산자는 피연산자를 `number`로 변환하여 숫자 값을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="d1cbe-125">Arithmetic operators convert their operands to `number`, and result in a number value.</span></span> <span data-ttu-id="d1cbe-126">부울 연산자는 피연산자를 `boolean`으로 변환하여 부울 값을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="d1cbe-126">Boolean operators convert their operands to `boolean`, and result in a Boolean value.</span></span> <span data-ttu-id="d1cbe-127">관계형 연산자와 같음 연산자는 부울 값을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="d1cbe-127">Relational operators and equality operators result in a Boolean value.</span></span> <span data-ttu-id="d1cbe-128">그러나 다음 표에서 볼 수 있듯이 피연산자의 원래 데이터 형식에 따라 서로 다른 변환 규칙이 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="d1cbe-128">However, they have different conversion rules depending on the original data types of their operands, as shown in this table.</span></span>  
  
|<span data-ttu-id="d1cbe-129">피연산자</span><span class="sxs-lookup"><span data-stu-id="d1cbe-129">Operand</span></span>|<span data-ttu-id="d1cbe-130">관계형 연산자</span><span class="sxs-lookup"><span data-stu-id="d1cbe-130">Relational operator</span></span>|<span data-ttu-id="d1cbe-131">같음 연산자</span><span class="sxs-lookup"><span data-stu-id="d1cbe-131">Equality operator</span></span>|  
|-------------|-------------------------|-----------------------|  
|<span data-ttu-id="d1cbe-132">두 피연산자가 모두 노드 집합입니다.</span><span class="sxs-lookup"><span data-stu-id="d1cbe-132">Both operands are node-sets.</span></span>|<span data-ttu-id="d1cbe-133">해당 `string` 값을 비교한 결과가 TRUE인 두 노드 중 하나는 첫 번째 집합에 있고 다른 하나는 두 번째 집합에 있는 경우에만 TRUE입니다.</span><span class="sxs-lookup"><span data-stu-id="d1cbe-133">TRUE if and only if there is a node in one set and a node in the second set such that the comparison of their `string` values is TRUE.</span></span>|<span data-ttu-id="d1cbe-134">같습니다.</span><span class="sxs-lookup"><span data-stu-id="d1cbe-134">Same.</span></span>|  
|<span data-ttu-id="d1cbe-135">하나는 노드 집합이고 다른 하나는 `string`입니다.</span><span class="sxs-lookup"><span data-stu-id="d1cbe-135">One is a node-set, the other a `string`.</span></span>|<span data-ttu-id="d1cbe-136">`number`로 변환되었을 때 `string`로 변환된 `number`과 비교한 결과가 TRUE인 노드가 노드 집합에 있는 경우에만 TRUE입니다.</span><span class="sxs-lookup"><span data-stu-id="d1cbe-136">TRUE if and only if there is a node in the node-set such that when converted to `number`, the comparison of it with the `string` converted to `number` is TRUE.</span></span>|<span data-ttu-id="d1cbe-137">`string`으로 변환되었을 때 `string`과 비교한 결과가 TRUE인 노드가 노드 집합에 있는 경우에만 TRUE입니다.</span><span class="sxs-lookup"><span data-stu-id="d1cbe-137">TRUE if and only if there is a node in the node-set such that when converted to `string`, the comparison of it with the `string` is TRUE.</span></span>|  
|<span data-ttu-id="d1cbe-138">하나는 노드 집합이고 다른 하나는 `number`입니다.</span><span class="sxs-lookup"><span data-stu-id="d1cbe-138">One is a node-set, the other a `number`.</span></span>|<span data-ttu-id="d1cbe-139">`number`으로 변환되었을 때 `number`과 비교한 결과가 TRUE인 노드가 노드 집합에 있는 경우에만 TRUE입니다.</span><span class="sxs-lookup"><span data-stu-id="d1cbe-139">TRUE if and only if there is a node in the node-set such that when converted to `number`, the comparison of it with the `number` is TRUE.</span></span>|<span data-ttu-id="d1cbe-140">같습니다.</span><span class="sxs-lookup"><span data-stu-id="d1cbe-140">Same.</span></span>|  
|<span data-ttu-id="d1cbe-141">하나는 노드 집합이고 다른 하나는 `boolean`입니다.</span><span class="sxs-lookup"><span data-stu-id="d1cbe-141">One is a node-set, the other a `boolean`.</span></span>|<span data-ttu-id="d1cbe-142">`boolean`으로 변환된 다음 `number`로 변환되었을 때 `boolean`로 변환된 `number`과 비교한 결과가 TRUE인 노드가 노드 집합에 있는 경우에만 TRUE입니다.</span><span class="sxs-lookup"><span data-stu-id="d1cbe-142">TRUE if and only if there is a node in the node-set such that when converted to `boolean` and then to `number`, the comparison of it with the `boolean` converted to `number` is TRUE.</span></span>|<span data-ttu-id="d1cbe-143">`boolean`으로 변환되었을 때 `boolean`과 비교한 결과가 TRUE인 노드가 노드 집합에 있는 경우에만 TRUE입니다.</span><span class="sxs-lookup"><span data-stu-id="d1cbe-143">TRUE if and only if there is a node in the node-set such that when converted to `boolean`, the comparison of it with the `boolean` is TRUE.</span></span>|  
|<span data-ttu-id="d1cbe-144">둘 모두 노드 집합이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="d1cbe-144">Neither is a node-set.</span></span>|<span data-ttu-id="d1cbe-145">두 피연산자를 모두 `number`로 변환한 다음 비교합니다.</span><span class="sxs-lookup"><span data-stu-id="d1cbe-145">Convert both operands to `number` and then compare.</span></span>|<span data-ttu-id="d1cbe-146">두 피연산자를 모두 일반 형식으로 변환한 다음 비교합니다.</span><span class="sxs-lookup"><span data-stu-id="d1cbe-146">Convert both operands to a common type and then compare.</span></span> <span data-ttu-id="d1cbe-147">둘 중 하나가 `boolean`이면 `boolean`으로 변환하고 둘 중 하나가 `number`이면 `number`로 변환하며 그 외의 경우에는 `string`으로 변환합니다.</span><span class="sxs-lookup"><span data-stu-id="d1cbe-147">Convert to `boolean` if either is `boolean`, `number` if either is `number`; otherwise, convert to `string`.</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="d1cbe-148">XPath 관계형 연산자는 항상 해당 피연산자를 `number`로 변환하므로 `string` 비교는 가능하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d1cbe-148">Because XPath relational operators always convert their operands to `number`, `string` comparisons are not possible.</span></span> <span data-ttu-id="d1cbe-149">날짜 비교를 포함 하기 위해 SQL Server 2000는 XPath 사양에 이러한 변형을 제공 합니다. 관계 연산자가를과 비교 하거나, 노드 집합을로, 문자열 값 노드 집합을 `string` `string` 문자열 값 `string` 노드 집합으로 설정 하면 비교가 `string` 아닌 비교가 `number` 수행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d1cbe-149">To include date comparisons, SQL Server 2000 offers this variation to the XPath specification: When a relational operator compares a `string` to a `string`, a node-set to a `string`, or a string-valued node-set to a string-valued node-set, a `string` comparison (not a `number` comparison) is performed.</span></span>  
  
## <a name="node-set-conversions"></a><span data-ttu-id="d1cbe-150">노드 집합 변환</span><span class="sxs-lookup"><span data-stu-id="d1cbe-150">Node-Set Conversions</span></span>  
 <span data-ttu-id="d1cbe-151">노드 집합 변환이 항상 직관적이지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d1cbe-151">Node-set conversions are not always intuitive.</span></span> <span data-ttu-id="d1cbe-152">노드 집합은 집합에 있는 첫 번째 노드의 문자열 값만 사용하여 `string`으로 변환됩니다.</span><span class="sxs-lookup"><span data-stu-id="d1cbe-152">A node-set is converted to a `string` by taking the string value of only the first node in the set.</span></span> <span data-ttu-id="d1cbe-153">노드 집합은 노드 집합이 `number`으로 변환된 다음 이 `string`이 다시 `string`로 변환되는 방법으로 `number`로 변환됩니다.</span><span class="sxs-lookup"><span data-stu-id="d1cbe-153">A node-set is converted to `number` by converting it to `string`, and then converting `string` to `number`.</span></span> <span data-ttu-id="d1cbe-154">노드 집합은 해당 노드 집합의 존재 여부가 테스트되는 방식을 통해 `boolean`으로 변환됩니다.</span><span class="sxs-lookup"><span data-stu-id="d1cbe-154">A node-set is converted to `boolean` by testing for its existence.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="d1cbe-155">에서는 노드 집합에 대해 위치 선택을 수행하지 않습니다. 예를 들어 XPath 쿼리 `Customer[3]`는 세 번째 고객을 의미하는데 이러한 종류의 위치 선택이 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서는 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d1cbe-155">does not perform positional selection on node-sets: for example, the XPath query `Customer[3]` means the third customer; this type of positional selection is not supported in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="d1cbe-156">따라서 XPath 사양에서 설명하는 노드 집합에서 `string`으로의 변환이나 노드 집합에서 `number`로의 변환이 구현되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d1cbe-156">Therefore, the node-set-to-`string` or node-set-to-`number` conversions as described by the XPath specification are not implemented.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="d1cbe-157">에서는 XPath 사양에 "첫 번째" 의미 체계가 지정된 경우 항상 "임의" 의미 체계를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="d1cbe-157">uses "any" semantics wherever the XPath specification specifies "first" semantics.</span></span> <span data-ttu-id="d1cbe-158">예를 들어 W3C XPath 사양을 기반으로 하는 XPath 쿼리는 `Order[OrderDetail/@UnitPrice > 10.0]` **단가** 가 10.0 보다 큰 첫 번째 **orderdetail** 이 포함 된 주문을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="d1cbe-158">For example, based on the W3C XPath specification, the XPath query `Order[OrderDetail/@UnitPrice > 10.0]` selects those orders with the first **OrderDetail** that has a **UnitPrice** greater than 10.0.</span></span> <span data-ttu-id="d1cbe-159">에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 이 XPath 쿼리는 **단가** 가 10.0 보다 큰 **orderdetail** 이 포함 된 주문을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="d1cbe-159">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], this XPath query selects those orders with any **OrderDetail** that has a **UnitPrice** greater than 10.0.</span></span>  
  
 <span data-ttu-id="d1cbe-160">`boolean`으로 변환될 때는 존재 테스트가 수행됩니다. 따라서 XPath 쿼리 `Products[@Discontinued=true()]`는 SQL 식 "Products.Discontinued = 1"이 아니라 SQL 식 "Products.Discontinued is not null"과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="d1cbe-160">Conversion to `boolean` generates an existence test; therefore, the XPath query `Products[@Discontinued=true()]` is equivalent to the SQL expression "Products.Discontinued is not null", not the SQL expression "Products.Discontinued = 1".</span></span> <span data-ttu-id="d1cbe-161">이 XPath 쿼리를 "Products.Discontinued = 1"과 같게 만들려면 먼저 노드 집합을 `boolean`와 같은 `number`이 아닌 형식으로 변환합니다.</span><span class="sxs-lookup"><span data-stu-id="d1cbe-161">To make the query equivalent to the latter SQL expression, first convert the node-set to a non-`boolean` type, such as `number`.</span></span> <span data-ttu-id="d1cbe-162">예들 들어 `Products[number(@Discontinued) = true()]`입니다.</span><span class="sxs-lookup"><span data-stu-id="d1cbe-162">For example, `Products[number(@Discontinued) = true()]`.</span></span>  
  
 <span data-ttu-id="d1cbe-163">대부분의 연산자는 노드 집합의 임의 노드 또는 특정 노드에 대해 TRUE이면 TRUE가 되도록 정의되어 있으므로 노드 집합이 비어 있으면 이러한 연산의 결과가 항상 FALSE입니다.</span><span class="sxs-lookup"><span data-stu-id="d1cbe-163">Because most operators are defined to be TRUE if they are TRUE for any or one of the nodes in the node-set, these operations always evaluate to FALSE if the node-set is empty.</span></span> <span data-ttu-id="d1cbe-164">따라서 A가 비어 있으면 `A = B`와 `A != B`는 모두 FALSE이고 `not(A=B)`와 `not(A!=B)`는 TRUE입니다.</span><span class="sxs-lookup"><span data-stu-id="d1cbe-164">Thus, if A is empty, both `A = B` and `A != B` are FALSE, and `not(A=B)` and `not(A!=B)` are TRUE.</span></span>  
  
 <span data-ttu-id="d1cbe-165">일반적으로 열에 매핑되는 특성이나 요소는 데이터베이스에서 해당 열 값이 `null`이 아닐 경우 존재합니다.</span><span class="sxs-lookup"><span data-stu-id="d1cbe-165">Usually, an attribute or element that maps to a column exists if the value of that column in the database is not `null`.</span></span> <span data-ttu-id="d1cbe-166">행에 매핑되는 요소는 행의 자식이 있는 경우에만 존재합니다.</span><span class="sxs-lookup"><span data-stu-id="d1cbe-166">Elements that map to rows exist if any of their children exist.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d1cbe-167">`is-constant`라는 주석이 추가된 요소는 항상 존재합니다.</span><span class="sxs-lookup"><span data-stu-id="d1cbe-167">Elements annotated with `is-constant` always exist.</span></span> <span data-ttu-id="d1cbe-168">따라서 `is-constant` 요소에는 XPath 조건자를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d1cbe-168">Consequently, XPath predicates cannot be used on `is-constant` elements.</span></span>  
  
 <span data-ttu-id="d1cbe-169">노드 집합이 `string`이나 `number`로 변환될 경우 주석이 추가된 스키마에서 해당 XDR 유형(있는 경우)이 검사된 다음 이를 기반으로 필요한 변환이 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="d1cbe-169">When a node-set is converted to `string` or `number`, its XDR type (if any) is inspected in the annotated schema and that type is used to determine the conversion that is required.</span></span>  
  
## <a name="mapping-xdr-data-types-to-xpath-data-types"></a><span data-ttu-id="d1cbe-170">XDR 데이터 형식을 XPath 데이터 형식에 매핑</span><span class="sxs-lookup"><span data-stu-id="d1cbe-170">Mapping XDR Data Types to XPath Data Types</span></span>  
 <span data-ttu-id="d1cbe-171">다음 표에서와 같이 노드의 XPath 데이터 형식은 스키마의 XDR 데이터 형식에서 파생 됩니다. 노드 **EmployeeID** 는 설명 목적으로 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d1cbe-171">The XPath data type of a node is derived from the XDR data type in the schema, as shown in the following table (the node **EmployeeID** is used for illustrative purpose).</span></span>  
  
|<span data-ttu-id="d1cbe-172">XDR 데이터 형식</span><span class="sxs-lookup"><span data-stu-id="d1cbe-172">XDR data type</span></span>|<span data-ttu-id="d1cbe-173">해당</span><span class="sxs-lookup"><span data-stu-id="d1cbe-173">Equivalent</span></span><br /><br /> <span data-ttu-id="d1cbe-174">XPath 데이터 형식</span><span class="sxs-lookup"><span data-stu-id="d1cbe-174">XPath data type</span></span>|<span data-ttu-id="d1cbe-175">사용되는 SQL Server 변환</span><span class="sxs-lookup"><span data-stu-id="d1cbe-175">SQL Server conversion used</span></span>|  
|-------------------|------------------------------------|--------------------------------|  
|<span data-ttu-id="d1cbe-176">Nonebin.base64bin.hex</span><span class="sxs-lookup"><span data-stu-id="d1cbe-176">Nonebin.base64bin.hex</span></span>|<span data-ttu-id="d1cbe-177">해당 없음</span><span class="sxs-lookup"><span data-stu-id="d1cbe-177">N/A</span></span>|<span data-ttu-id="d1cbe-178">NoneEmployeeID</span><span class="sxs-lookup"><span data-stu-id="d1cbe-178">NoneEmployeeID</span></span>|  
|<span data-ttu-id="d1cbe-179">boolean</span><span class="sxs-lookup"><span data-stu-id="d1cbe-179">boolean</span></span>|<span data-ttu-id="d1cbe-180">boolean</span><span class="sxs-lookup"><span data-stu-id="d1cbe-180">boolean</span></span>|<span data-ttu-id="d1cbe-181">CONVERT(bit, EmployeeID)</span><span class="sxs-lookup"><span data-stu-id="d1cbe-181">CONVERT(bit, EmployeeID)</span></span>|  
|<span data-ttu-id="d1cbe-182">number, int, float,i1, i2, i4, i8,r4, r8ui1, ui2, ui4, ui8</span><span class="sxs-lookup"><span data-stu-id="d1cbe-182">number, int, float,i1, i2, i4, i8,r4, r8ui1, ui2, ui4, ui8</span></span>|<span data-ttu-id="d1cbe-183">숫자</span><span class="sxs-lookup"><span data-stu-id="d1cbe-183">number</span></span>|<span data-ttu-id="d1cbe-184">CONVERT(float(53), EmployeeID)</span><span class="sxs-lookup"><span data-stu-id="d1cbe-184">CONVERT(float(53), EmployeeID)</span></span>|  
|<span data-ttu-id="d1cbe-185">id, idref, idrefsentity, entities, enumerationnotation, nmtoken, nmtokens, chardate, Timedate, Time.tz, string, uri, uuid</span><span class="sxs-lookup"><span data-stu-id="d1cbe-185">id, idref, idrefsentity, entities, enumerationnotation, nmtoken, nmtokens, chardate, Timedate, Time.tz, string, uri, uuid</span></span>|<span data-ttu-id="d1cbe-186">문자열</span><span class="sxs-lookup"><span data-stu-id="d1cbe-186">string</span></span>|<span data-ttu-id="d1cbe-187">CONVERT(nvarchar(4000), EmployeeID, 126)</span><span class="sxs-lookup"><span data-stu-id="d1cbe-187">CONVERT(nvarchar(4000), EmployeeID, 126)</span></span>|  
|<span data-ttu-id="d1cbe-188">fixed14.4</span><span class="sxs-lookup"><span data-stu-id="d1cbe-188">fixed14.4</span></span>|<span data-ttu-id="d1cbe-189">해당 사항 없음(XPath에는 fixed14.4 XDR 데이터 형식에 해당하는 데이터 형식이 없음)</span><span class="sxs-lookup"><span data-stu-id="d1cbe-189">N/A(There is no data type in XPath that is equivalent to the fixed14.4 XDR data type)</span></span>|<span data-ttu-id="d1cbe-190">CONVERT(money, EmployeeID)</span><span class="sxs-lookup"><span data-stu-id="d1cbe-190">CONVERT(money, EmployeeID)</span></span>|  
|<span data-ttu-id="d1cbe-191">date</span><span class="sxs-lookup"><span data-stu-id="d1cbe-191">date</span></span>|<span data-ttu-id="d1cbe-192">문자열</span><span class="sxs-lookup"><span data-stu-id="d1cbe-192">string</span></span>|<span data-ttu-id="d1cbe-193">LEFT(CONVERT(nvarchar(4000), EmployeeID, 126), 10)</span><span class="sxs-lookup"><span data-stu-id="d1cbe-193">LEFT(CONVERT(nvarchar(4000), EmployeeID, 126), 10)</span></span>|  
|<span data-ttu-id="d1cbe-194">time</span><span class="sxs-lookup"><span data-stu-id="d1cbe-194">time</span></span><br /><br /> <span data-ttu-id="d1cbe-195">time.tz</span><span class="sxs-lookup"><span data-stu-id="d1cbe-195">time.tz</span></span>|<span data-ttu-id="d1cbe-196">문자열</span><span class="sxs-lookup"><span data-stu-id="d1cbe-196">string</span></span>|<span data-ttu-id="d1cbe-197">SUBSTRING(CONVERT(nvarchar(4000), EmployeeID, 126), 1 + CHARINDEX(N'T', CONVERT(nvarchar(4000), EmployeeID, 126)), 24)</span><span class="sxs-lookup"><span data-stu-id="d1cbe-197">SUBSTRING(CONVERT(nvarchar(4000), EmployeeID, 126), 1 + CHARINDEX(N'T', CONVERT(nvarchar(4000), EmployeeID, 126)), 24)</span></span>|  
  
 <span data-ttu-id="d1cbe-198">날짜 및 시간 변환은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `datetime` 데이터 형식이 나를 사용 하 여 데이터베이스에 값이 저장 되는지 여부에 따라 작동 하도록 디자인 되었습니다 `string` .</span><span class="sxs-lookup"><span data-stu-id="d1cbe-198">The date and time conversions are designed to work whether the value is stored in the database using the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]`datetime` data type or a `string`.</span></span> <span data-ttu-id="d1cbe-199">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `datetime` 데이터 형식은를 사용 하지 않으며 `timezone` XML 데이터 형식 보다 전체 자릿수가 더 적습니다 `time` .</span><span class="sxs-lookup"><span data-stu-id="d1cbe-199">Note that the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]`datetime` data type does not use `timezone` and has a smaller precision than the XML `time` data type.</span></span> <span data-ttu-id="d1cbe-200">`timezone` 데이터 형식을 사용하거나 전체 자릿수를 늘리려면 `string` 형식을 사용하여 데이터를 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에 저장하십시오.</span><span class="sxs-lookup"><span data-stu-id="d1cbe-200">To include the `timezone` data type or additional precision, store the data in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] using a `string` type.</span></span>  
  
 <span data-ttu-id="d1cbe-201">노드가 해당 XDR 데이터 형식에서 XPath 데이터 형식으로 변환될 때 한 XPath 데이터 형식에서 다른 XPath 데이터 형식으로의 추가 변환이 필요한 경우가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d1cbe-201">When a node is converted from its XDR data type to the XPath data type, additional conversion is sometimes necessary (from one XPath data type to another XPath data type).</span></span> <span data-ttu-id="d1cbe-202">예를 들어 다음과 같은 XPath 쿼리를 살펴봅니다.</span><span class="sxs-lookup"><span data-stu-id="d1cbe-202">For example, consider this XPath query:</span></span>  
  
```  
(@m + 3) = 4  
```  
  
 <span data-ttu-id="d1cbe-203">@m가 `fixed14.4` xdr 데이터 형식인 경우 xdr 데이터 형식에서 XPath 데이터 형식으로 변환 하는 작업은 다음을 사용 하 여 수행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d1cbe-203">If @m is of the `fixed14.4` XDR data type, the conversion from XDR data type to XPath data type is accomplished using:</span></span>  
  
```  
CONVERT(money, m)  
```  
  
 <span data-ttu-id="d1cbe-204">이 변환에서는 노드 `m`이 `fixed14.4`에서 `money`로 변환됩니다.</span><span class="sxs-lookup"><span data-stu-id="d1cbe-204">In this conversion, the node `m` is converted from `fixed14.4` to `money`.</span></span> <span data-ttu-id="d1cbe-205">그러나 값 3을 추가하려면 추가 변환이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="d1cbe-205">However, adding the value of 3, requires additional conversion:</span></span>  
  
```  
CONVERT(float(CONVERT(money, m))  
```  
  
 <span data-ttu-id="d1cbe-206">이 XPath 식은 다음과 같이 계산됩니다.</span><span class="sxs-lookup"><span data-stu-id="d1cbe-206">The XPath expression is evaluated as:</span></span>  
  
```  
CONVERT(float(CONVERT(money, m)) + CONVERT(float(53), 3) = CONVERT(float(53), 3)  
```  
  
 <span data-ttu-id="d1cbe-207">다음 표에서 볼 수 있듯이 이 변환은 리터럴 또는 복합 식과 같은 다른 XPath 식에 적용되는 변환과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="d1cbe-207">As shown in the following table, this is the same conversion that is applied for other XPath expressions (such as literals or compound expressions).</span></span>  
  
||||||  
|-|-|-|-|-|  
||<span data-ttu-id="d1cbe-208">X는 알 수 없는 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="d1cbe-208">X is unknown</span></span>|<span data-ttu-id="d1cbe-209">X는 `string`입니다.</span><span class="sxs-lookup"><span data-stu-id="d1cbe-209">X is `string`</span></span>|<span data-ttu-id="d1cbe-210">X는 `number`입니다.</span><span class="sxs-lookup"><span data-stu-id="d1cbe-210">X is `number`</span></span>|<span data-ttu-id="d1cbe-211">X는 `boolean`입니다.</span><span class="sxs-lookup"><span data-stu-id="d1cbe-211">X is `boolean`</span></span>|  
|<span data-ttu-id="d1cbe-212">string(X)</span><span class="sxs-lookup"><span data-stu-id="d1cbe-212">string(X)</span></span>|<span data-ttu-id="d1cbe-213">CONVERT (nvarchar(4000), X, 126)</span><span class="sxs-lookup"><span data-stu-id="d1cbe-213">CONVERT (nvarchar(4000), X, 126)</span></span>|-|<span data-ttu-id="d1cbe-214">CONVERT (nvarchar(4000), X, 126)</span><span class="sxs-lookup"><span data-stu-id="d1cbe-214">CONVERT (nvarchar(4000), X, 126)</span></span>|<span data-ttu-id="d1cbe-215">CASE WHEN X THEN N'true' ELSE N'false' END</span><span class="sxs-lookup"><span data-stu-id="d1cbe-215">CASE WHEN X THEN N'true' ELSE N'false' END</span></span>|  
|<span data-ttu-id="d1cbe-216">number(X)</span><span class="sxs-lookup"><span data-stu-id="d1cbe-216">number(X)</span></span>|<span data-ttu-id="d1cbe-217">CONVERT (float(53), X)</span><span class="sxs-lookup"><span data-stu-id="d1cbe-217">CONVERT (float(53), X)</span></span>|<span data-ttu-id="d1cbe-218">CONVERT (float(53), X)</span><span class="sxs-lookup"><span data-stu-id="d1cbe-218">CONVERT (float(53), X)</span></span>|-|<span data-ttu-id="d1cbe-219">CASE WHEN X THEN 1 ELSE 0 END</span><span class="sxs-lookup"><span data-stu-id="d1cbe-219">CASE WHEN X THEN 1 ELSE 0 END</span></span>|  
|<span data-ttu-id="d1cbe-220">boolean(X)</span><span class="sxs-lookup"><span data-stu-id="d1cbe-220">boolean(X)</span></span>|-|<span data-ttu-id="d1cbe-221">LEN (X) > 0</span><span class="sxs-lookup"><span data-stu-id="d1cbe-221">LEN(X) > 0</span></span>|<span data-ttu-id="d1cbe-222">X != 0</span><span class="sxs-lookup"><span data-stu-id="d1cbe-222">X != 0</span></span>|-|  
  
## <a name="examples"></a><span data-ttu-id="d1cbe-223">예</span><span class="sxs-lookup"><span data-stu-id="d1cbe-223">Examples</span></span>  
  
### <a name="a-convert-a-data-type-in-an-xpath-query"></a><span data-ttu-id="d1cbe-224">A.</span><span class="sxs-lookup"><span data-stu-id="d1cbe-224">A.</span></span> <span data-ttu-id="d1cbe-225">XPath 쿼리에서 데이터 형식 변환</span><span class="sxs-lookup"><span data-stu-id="d1cbe-225">Convert a data type in an XPath query</span></span>  
 <span data-ttu-id="d1cbe-226">주석이 추가 된 XSD 스키마에 대해 지정 된 다음 XPath 쿼리에서는 **EmployeeID** 특성 값이 E-1 인 모든 **Employee** 노드를 선택 합니다. 여기서 "e-"는 주석을 사용 하 여 지정 된 접두사입니다 `sql:id-prefix` .</span><span class="sxs-lookup"><span data-stu-id="d1cbe-226">In the following XPath query specified against an annotated XSD schema, the query selects all **Employee** nodes with the **EmployeeID** attribute value of E-1, where "E-" is the prefix specified using the `sql:id-prefix` annotation.</span></span>  
  
 `Employee[@EmployeeID="E-1"]`  
  
 <span data-ttu-id="d1cbe-227">쿼리의 조건자는 다음 SQL 식과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="d1cbe-227">The predicate in the query is equivalent to the SQL expression:</span></span>  
  
 `N'E-' + CONVERT(nvarchar(4000), Employees.EmployeeID, 126) = N'E-1'`  
  
 <span data-ttu-id="d1cbe-228">**Employeeid** 는 `id` `idref` `idrefs` `nmtoken` XSD 스키마의 (,,, 등 `nmtokens` ) 데이터 형식 값 중 하나 이므로 **employeeid** 는 `string` 앞에서 설명한 변환 규칙을 사용 하 여 XPath 데이터 형식으로 변환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d1cbe-228">Because **EmployeeID** is one of the `id` (`idref`, `idrefs`, `nmtoken`, `nmtokens`, and so on) data type values in the XSD schema, **EmployeeID** is converted to the `string` XPath data type using the conversion rules described previously.</span></span>  
  
 `CONVERT(nvarchar(4000), Employees.EmployeeID, 126)`  
  
 <span data-ttu-id="d1cbe-229">"E-" 접두사가 문자열에 추가된 다음 그 결과가 `N'E-1'`과 비교됩니다.</span><span class="sxs-lookup"><span data-stu-id="d1cbe-229">The "E-" prefix is added to the string, and the result is then compared with `N'E-1'`.</span></span>  
  
### <a name="b-perform-several-data-type-conversions-in-an-xpath-query"></a><span data-ttu-id="d1cbe-230">B.</span><span class="sxs-lookup"><span data-stu-id="d1cbe-230">B.</span></span> <span data-ttu-id="d1cbe-231">XPath 쿼리에서 몇 가지 데이터 형식 변환 수행</span><span class="sxs-lookup"><span data-stu-id="d1cbe-231">Perform several data type conversions in an XPath query</span></span>  
 <span data-ttu-id="d1cbe-232">주석이 추가된 XSD 스키마에 대해 지정된 XPath 쿼리 `OrderDetail[@UnitPrice * @OrderQty > 98]`을 살펴봅니다.</span><span class="sxs-lookup"><span data-stu-id="d1cbe-232">Consider this XPath query specified against an annotated XSD schema: `OrderDetail[@UnitPrice * @OrderQty > 98]`</span></span>  
  
 <span data-ttu-id="d1cbe-233">이 XPath 쿼리는 조건자를 충족 하는 모든 요소를 반환 합니다 **\<OrderDetail>** `@UnitPrice * @OrderQty > 98` .</span><span class="sxs-lookup"><span data-stu-id="d1cbe-233">This XPath query returns all the **\<OrderDetail>** elements satisfying the predicate `@UnitPrice * @OrderQty > 98`.</span></span> <span data-ttu-id="d1cbe-234">주석이 추가 된 스키마의 데이터 형식으로 **UnitPrice** 에 주석을 추가 하는 경우 `fixed14.4` 이 조건자는 SQL 식과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="d1cbe-234">If the **UnitPrice** is annotated with a `fixed14.4` data type in the annotated schema, this predicate is equivalent to the SQL expression:</span></span>  
  
 `CONVERT(float(53), CONVERT(money, OrderDetail.UnitPrice)) * CONVERT(float(53), OrderDetail.OrderQty) > CONVERT(float(53), 98)`  
  
 <span data-ttu-id="d1cbe-235">XPath 쿼리에서 값 변환 시 첫 번째 변환에서는 XDR 데이터 형식을 XPath 데이터 형식으로 변환합니다.</span><span class="sxs-lookup"><span data-stu-id="d1cbe-235">In converting the values in the XPath query, the first conversion converts the XDR data type to the XPath data type.</span></span> <span data-ttu-id="d1cbe-236">이전 표에 설명 된 대로 **UnitPrice** 의 XSD 데이터 형식이 이므로 `fixed14.4` 이는 첫 번째 변환입니다.</span><span class="sxs-lookup"><span data-stu-id="d1cbe-236">Because the XSD data type of **UnitPrice** is `fixed14.4`, as described in the previous table, this is the first conversion that is used:</span></span>  
  
```  
CONVERT(money, OrderDetail.UnitPrice))   
```  
  
 <span data-ttu-id="d1cbe-237">산술 연산자는 해당 피연산자를 `number` XPath 데이터 형식으로 변환하므로 값이 `float(53)`로 변환될 때 한 XPath 데이터 형식에서 다른 XPath 데이터 형식으로의 두 번째 변환이 적용됩니다. `float(53)`는 XPath `number` 데이터 형식과 비슷합니다.</span><span class="sxs-lookup"><span data-stu-id="d1cbe-237">Because the arithmetic operators convert their operands to the `number` XPath data type, the second conversion (from one XPath data type to another XPath data type) is applied in which the value is converted to `float(53)` (`float(53)` is close to the XPath `number` data type):</span></span>  
  
```  
CONVERT(float(53), CONVERT(money, OrderDetail.UnitPrice))   
```  
  
 <span data-ttu-id="d1cbe-238">**Orderqty** 특성에 XSD 데이터 형식이 없으면 **orderqty** 는 `number` 단일 변환에서 XPath 데이터 형식으로 변환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d1cbe-238">Assuming the **OrderQty** attribute has no XSD data type, **OrderQty** is converted to a `number` XPath data type in a single conversion:</span></span>  
  
```  
CONVERT(float(53), OrderDetail.OrderQty)  
```  
  
 <span data-ttu-id="d1cbe-239">마찬가지로 값 98은 `number` XPath 데이터 형식으로 변환됩니다.</span><span class="sxs-lookup"><span data-stu-id="d1cbe-239">Similarly, the value 98 is converted to the `number` XPath data type:</span></span>  
  
```  
CONVERT(float(53), 98)  
```  
  
> [!NOTE]  
>  <span data-ttu-id="d1cbe-240">스키마에 사용된 XSD 데이터 형식이 데이터베이스의 기본 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터 형식과 호환되지 않거나 허용되지 않는 XPath 데이터 형식 변환이 수행되면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 오류를 반환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d1cbe-240">If the XSD data type used in the schema is incompatible with the underlying [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data type in the database, or if an impossible XPath data type conversion is performed, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] may return an error.</span></span> <span data-ttu-id="d1cbe-241">예를 들어 **employeeid** 특성에 주석을 추가 하는 경우에는 `id-prefix` `Employee[@EmployeeID=1]` **employeeid** 가 주석을 포함 하 `id-prefix` 고로 변환할 수 없기 때문에 XPath에서 오류를 생성 합니다 `number` .</span><span class="sxs-lookup"><span data-stu-id="d1cbe-241">For example, if the **EmployeeID** attribute is annotated with `id-prefix` annotation, the XPath `Employee[@EmployeeID=1]` generates an error, because **EmployeeID** has the `id-prefix` annotation and cannot be converted to `number`.</span></span>  
  
  
