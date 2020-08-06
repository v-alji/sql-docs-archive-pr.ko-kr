---
title: FOR XML에서 AUTO 모드 사용 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- FOR XML clause, AUTO mode
- ELEMENTS option
- FOR XML AUTO mode
- AUTO FOR XML mode
ms.assetid: 7140d656-1d42-4f01-a533-5251429f4450
author: rothja
ms.author: jroth
ms.openlocfilehash: 232cc046667c6d31cb9657a7abdc862204507d23
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651560"
---
# <a name="use-auto-mode-with-for-xml"></a><span data-ttu-id="122e7-102">FOR XML에서 AUTO 모드 사용</span><span class="sxs-lookup"><span data-stu-id="122e7-102">Use AUTO Mode with FOR XML</span></span>
  <span data-ttu-id="122e7-103">[FOR XML&#40;SQL Server&#41;](for-xml-sql-server.md)에 설명된 대로 AUTO 모드는 쿼리 결과를 중첩 XML 요소로 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="122e7-103">As described in [FOR XML &#40;SQL Server&#41;](for-xml-sql-server.md), AUTO mode returns query results as nested XML elements.</span></span> <span data-ttu-id="122e7-104">이 모드에서는 쿼리 결과로 생성되는 XML의 모양을 상세하게 조정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="122e7-104">This does not provide much control over the shape of the XML generated from a query result.</span></span> <span data-ttu-id="122e7-105">AUTO 모드 쿼리는 간단한 계층을 생성하려는 경우에 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="122e7-105">The AUTO mode queries are useful if you want to generate simple hierarchies.</span></span> <span data-ttu-id="122e7-106">그러나 [FOR XML에서 EXPLICIT 모드 사용](use-explicit-mode-with-for-xml.md) 및 [FOR XML에서 PATH 모드 사용](use-path-mode-with-for-xml.md) 에서는 쿼리 결과로 생성되는 XML의 모양을 좀 더 상세하게 조정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="122e7-106">However, [Use EXPLICIT Mode with FOR XML](use-explicit-mode-with-for-xml.md) and [Use PATH Mode with FOR XML](use-path-mode-with-for-xml.md) provide more control and flexibility in deciding the shape of the XML from a query result.</span></span>  
  
 <span data-ttu-id="122e7-107">최소한 한 개의 해당 열이 SELECT 절에 나열되는 FROM 절의 각 테이블은 XML 요소로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="122e7-107">Each table in the FROM clause, from which at least one column is listed in the SELECT clause, is represented as an XML element.</span></span> <span data-ttu-id="122e7-108">선택 항목인 ELEMENTS 옵션이 FOR XML 절에 지정된 경우 SELECT 절에 나열되는 열은 특성이나 하위 요소로 매핑됩니다.</span><span class="sxs-lookup"><span data-stu-id="122e7-108">The columns listed in the SELECT clause are mapped to attributes or subelements, if the optional ELEMENTS option is specified in the FOR XML clause.</span></span>  
  
 <span data-ttu-id="122e7-109">결과 XML에서 요소가 중첩된 XML 계층은 SELECT 절에 지정된 열에 의해 식별되는 테이블의 순서를 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="122e7-109">The XML hierarchy, nesting of the elements, in the resulting XML is based on the order of tables identified by the columns specified in the SELECT clause.</span></span> <span data-ttu-id="122e7-110">따라서 SELECT 절에 열 이름이 지정되는 순서가 중요합니다.</span><span class="sxs-lookup"><span data-stu-id="122e7-110">Therefore, the order in which column names are specified in the SELECT clause is significant.</span></span> <span data-ttu-id="122e7-111">맨 앞에서 가장 왼쪽에 있는 것으로 식별되는 테이블은 결과 XML 문서의 최상위 요소를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="122e7-111">The first, leftmost table that is identified forms the top element in the resulting XML document.</span></span> <span data-ttu-id="122e7-112">그 다음으로 SELECT 문의 열로 식별되는 왼쪽에서 두 번째에 있는 테이블은 최상위 요소 안에서 하위 요소를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="122e7-112">The second leftmost table, identified by columns in the SELECT statement, forms a subelement within the top element, and so on.</span></span>  
  
 <span data-ttu-id="122e7-113">SELECT 절에 나열되는 열 이름이 SELECT 절에서 이전에 지정한 열에 의해 이미 식별된 테이블로부터 비롯된 경우 새로운 계층 수준을 여는 대신 이미 생성된 요소의 특성으로 열이 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="122e7-113">If a column name listed in the SELECT clause is from a table that is already identified by a previously specified column in the SELECT clause, the column is added as an attribute of the element already created, instead of opening a new level of hierarchy.</span></span> <span data-ttu-id="122e7-114">ELEMENTS 옵션이 지정된 경우 열이 특성으로 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="122e7-114">If the ELEMENTS option is specified, the column is added as an attribute.</span></span>  
  
 <span data-ttu-id="122e7-115">예를 들어 다음 쿼리를 실행하십시오.</span><span class="sxs-lookup"><span data-stu-id="122e7-115">For example, execute this query:</span></span>  
  
```  
SELECT Cust.CustomerID,   
       OrderHeader.CustomerID,  
       OrderHeader.SalesOrderID,   
       OrderHeader.Status,  
       Cust.CustomerType  
FROM Sales.Customer Cust, Sales.SalesOrderHeader OrderHeader  
WHERE Cust.CustomerID = OrderHeader.CustomerID  
ORDER BY Cust.CustomerID  
FOR XML AUTO  
```  
  
 <span data-ttu-id="122e7-116">다음은 결과의 일부입니다.</span><span class="sxs-lookup"><span data-stu-id="122e7-116">This is the partial result:</span></span>  
  
```  
<Cust CustomerID="1" CustomerType="S">  
  <OrderHeader CustomerID="1" SalesOrderID="43860" Status="5" />  
  <OrderHeader CustomerID="1" SalesOrderID="44501" Status="5" />  
  <OrderHeader CustomerID="1" SalesOrderID="45283" Status="5" />  
  <OrderHeader CustomerID="1" SalesOrderID="46042" Status="5" />  
</Cust>  
...  
```  
  
 <span data-ttu-id="122e7-117">SELECT 절에서 다음에 유의하십시오.</span><span class="sxs-lookup"><span data-stu-id="122e7-117">Note the following in the SELECT clause:</span></span>  
  
-   <span data-ttu-id="122e7-118">CustomerID는 Cust 테이블을 참조합니다.</span><span class="sxs-lookup"><span data-stu-id="122e7-118">The CustomerID references the Cust table.</span></span> <span data-ttu-id="122e7-119">따라서 <`Cust`> 요소가 생성되고 CustomerID가 그 특성으로 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="122e7-119">Therefore, a <`Cust`> element is created and CustomerID is added as its attribute.</span></span>  
  
-   <span data-ttu-id="122e7-120">그런 다음 OrderHeader.CustomerID, OrderHeader.SaleOrderID 및 OrderHeader.Status의 3개 열은 OrderHeader 테이블을 참조합니다.</span><span class="sxs-lookup"><span data-stu-id="122e7-120">Next, three columns, OrderHeader.CustomerID, OrderHeader.SaleOrderID, and OrderHeader.Status, reference the OrderHeader table.</span></span> <span data-ttu-id="122e7-121">따라서 <`OrderHeader`> 요소는 <`Cust`> 요소의 하위 요소로 추가되고 이 3개의 열이 <`OrderHeader`>의 특성으로 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="122e7-121">Therefore, an <`OrderHeader`> element is added as a subelement of the <`Cust`> element and the three columns are added as attributes of <`OrderHeader`>.</span></span>  
  
-   <span data-ttu-id="122e7-122">그런 다음 Cust.CustomerType 열은 Cust.CustomerID 열로 이미 식별된 Cust 테이블을 다시 참조합니다.</span><span class="sxs-lookup"><span data-stu-id="122e7-122">Next, the Cust.CustomerType column again references the Cust table that was already identified by the Cust.CustomerID column.</span></span> <span data-ttu-id="122e7-123">따라서 새 요소는 생성되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="122e7-123">Therefore, no new element is created.</span></span> <span data-ttu-id="122e7-124">대신 이전에 생성된 <`Cust`> 요소에 CustomerType 특성이 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="122e7-124">Instead, the CustomerType attribute is added to the <`Cust`> element that was previously created.</span></span>  
  
-   <span data-ttu-id="122e7-125">이 쿼리는 테이블 이름에 대한 별칭을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="122e7-125">The query specifies aliases for the table names.</span></span> <span data-ttu-id="122e7-126">이러한 별칭은 해당 요소 이름으로 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="122e7-126">These aliases appear as corresponding element names.</span></span>  
  
-   <span data-ttu-id="122e7-127">ORDER BY는 하나의 부모 아래에 있는 모든 자식을 그룹화하는 데 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="122e7-127">ORDER BY is required to group all children under one parent.</span></span>  
  
 <span data-ttu-id="122e7-128">이 쿼리는 이전 쿼리와 비슷하지만 SELECT 절에서 Cust 테이블의 열 앞에 OrderHeader 테이블의 열을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="122e7-128">This query is similar to the previous one, except the SELECT clause specifies columns in the OrderHeader table before the columns in the Cust table.</span></span> <span data-ttu-id="122e7-129">따라서 첫 번째 <`OrderHeader`> 요소가 생성된 다음 <`Cust`> 자식 요소가 여기에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="122e7-129">Therefore, first <`OrderHeader`> element is created and then the <`Cust`> child element is added to it.</span></span>  
  
```  
select OrderHeader.CustomerID,  
       OrderHeader.SalesOrderID,   
       OrderHeader.Status,  
       Cust.CustomerID,   
       Cust.CustomerType  
from Sales.Customer Cust, Sales.SalesOrderHeader OrderHeader  
where Cust.CustomerID = OrderHeader.CustomerID  
for xml auto  
```  
  
 <span data-ttu-id="122e7-130">다음은 결과의 일부입니다.</span><span class="sxs-lookup"><span data-stu-id="122e7-130">This is the partial result:</span></span>  
  
```  
<OrderHeader CustomerID="1" SalesOrderID="43860" Status="5">  
  <Cust CustomerID="1" CustomerType="S" />  
</OrderHeader>  
...  
```  
  
 <span data-ttu-id="122e7-131">ELEMENTS 옵션이 FOR XML 절에 추가된 경우 요소 중심 XML이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="122e7-131">If the ELEMENTS option is added in the FOR XML clause, element-centric XML is returned.</span></span>  
  
```  
SELECT Cust.CustomerID,   
       OrderHeader.CustomerID,  
       OrderHeader.SalesOrderID,   
       OrderHeader.Status,  
       Cust.CustomerType  
FROM Sales.Customer Cust, Sales.SalesOrderHeader OrderHeader  
WHERE Cust.CustomerID = OrderHeader.CustomerID  
ORDER BY Cust.CustomerID  
FOR XML AUTO, ELEMENTS  
```  
  
 <span data-ttu-id="122e7-132">다음은 결과의 일부입니다.</span><span class="sxs-lookup"><span data-stu-id="122e7-132">This is the partial result:</span></span>  
  
```  
<Cust>  
  <CustomerID>1</CustomerID>  
  <CustomerType>S</CustomerType>  
  <OrderHeader>  
    <CustomerID>1</CustomerID>  
    <SalesOrderID>43860</SalesOrderID>  
    <Status>5</Status>  
  </OrderHeader>  
   ...  
</Cust>  
...  
```  
  
 <span data-ttu-id="122e7-133">이 쿼리에서 CustomerID 값은 CustomerID가 테이블의 기본 키이기 때문에 \<Cust> 요소를 만들 때 한 행씩 순서대로 비교됩니다.</span><span class="sxs-lookup"><span data-stu-id="122e7-133">In this query, the CustomerID values are compared from one row to the next in creating the \<Cust> elements, because CustomerID is the primary key of the table.</span></span> <span data-ttu-id="122e7-134">CustomerID가 테이블의 기본 키로 식별되지 않는 경우 모든 열 값(이 쿼리의 CustomerType인 CustomerID)이 한 행씩 순서대로 비교됩니다.</span><span class="sxs-lookup"><span data-stu-id="122e7-134">If CustomerID is not identified as the primary key for the table, all the column values (CustomerID, CustomerType in this query) are compared from one row to the next.</span></span> <span data-ttu-id="122e7-135">값이 다르면 새로운 \<Cust> 요소가 XML에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="122e7-135">If the values differ, a new \<Cust> element is added to the XML.</span></span>  
  
 <span data-ttu-id="122e7-136">이러한 열 값을 비교할 때 비교되는 임의의 열 유형이 **text**, **ntext**, **image**또는 **xml**인 경우 값이 같더라도 FOR XML은 값이 다르고 비교되지 않는 것으로 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="122e7-136">When comparing these column values, if any of the columns to be compared are of type **text**, **ntext**, **image**, or **xml**, FOR XML assumes that the values are different and not compared, even though they may be the same.</span></span> <span data-ttu-id="122e7-137">이러한 이유는 큰 개체에 대한 비교가 지원되지 않기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="122e7-137">This is because comparing large objects is not supported.</span></span> <span data-ttu-id="122e7-138">선택한 각 행에 대한 결과에 요소가 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="122e7-138">Elements are added to the result for each row selected.</span></span> <span data-ttu-id="122e7-139">**(n)varchar(max)** 및 **varbinary(max)** 의 열이 비교되는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="122e7-139">Note that columns of **(n)varchar(max)** and **varbinary(max)** are compared.</span></span>  
  
 <span data-ttu-id="122e7-140">집계 열 또는 계산 열의 경우와 같이 SELECT 절의 열이 FROM 절에서 식별된 어떤 테이블과도 연결될 수 없는 경우 그 열은 목록에서 나타날 때 XML 문서의 가장 깊은 중첩 수준에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="122e7-140">When a column in the SELECT clause cannot be associated with any of the tables identified in the FROM clause, as in the case of an aggregate column or computed column, the column is added in the XML document in the deepest nesting level in place when it is encountered in the list.</span></span> <span data-ttu-id="122e7-141">그러한 열이 SELECT 절에서 첫 번째 열로 나타나는 경우에는 최상위 요소에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="122e7-141">If such a column appears as the first column in the SELECT clause, the column is added to the top element.</span></span>  
  
 <span data-ttu-id="122e7-142">별표(\*) 와일드카드 문자를 SELECT 절에 지정하는 경우 위에 설명한 방법과 동일한 방식으로 행이 쿼리 엔진에 의해 반환되는 순서에 따라 중첩이 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="122e7-142">If the asterisk (\*) wildcard character is specified in the SELECT clause, the nesting is determined in the same way as previously described, based on the order that the rows are returned by the query engine.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="122e7-143">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="122e7-143">In This Section</span></span>  
 <span data-ttu-id="122e7-144">다음 항목에서는 AUTO 모드에 대한 자세한 내용을 제공합니다:</span><span class="sxs-lookup"><span data-stu-id="122e7-144">The following topics provide more information about AUTO mode:</span></span>  
  
-   [<span data-ttu-id="122e7-145">BINARY BASE64 옵션 사용</span><span class="sxs-lookup"><span data-stu-id="122e7-145">Use the BINARY BASE64 Option</span></span>](use-the-binary-base64-option.md)  
  
-   [<span data-ttu-id="122e7-146">반환된 XML 모양 지정에서 AUTO 모드 추론</span><span class="sxs-lookup"><span data-stu-id="122e7-146">AUTO Mode Heuristics in Shaping Returned XML</span></span>](auto-mode-heuristics-in-shaping-returned-xml.md)  
  
-   [<span data-ttu-id="122e7-147">예제: AUTO 모드 사용</span><span class="sxs-lookup"><span data-stu-id="122e7-147">Examples: Using AUTO Mode</span></span>](examples-using-auto-mode.md)  
  
## <a name="see-also"></a><span data-ttu-id="122e7-148">참고 항목</span><span class="sxs-lookup"><span data-stu-id="122e7-148">See Also</span></span>  
 <span data-ttu-id="122e7-149">[SELECT&#40;Transact-SQL&#41;](/sql/t-sql/queries/select-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="122e7-149">[SELECT &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-transact-sql) </span></span>  
 [<span data-ttu-id="122e7-150">FOR XML&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="122e7-150">FOR XML &#40;SQL Server&#41;</span></span>](for-xml-sql-server.md)  
  
  
