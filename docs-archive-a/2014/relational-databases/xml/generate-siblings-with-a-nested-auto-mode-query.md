---
title: 중첩 AUTO 모드 쿼리를 사용하여 형제 생성 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- queries [XML in SQL Server], nested AUTO mode
- nested AUTO mode query
ms.assetid: 748d9899-589d-4420-8048-1258e9e67c20
author: rothja
ms.author: jroth
ms.openlocfilehash: 20362942bdd0f7e7537433b664e5e63461ded499
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743060"
---
# <a name="generate-siblings-with-a-nested-auto-mode-query"></a><span data-ttu-id="cc69b-102">중첩 AUTO 모드 쿼리를 사용하여 형제 생성</span><span class="sxs-lookup"><span data-stu-id="cc69b-102">Generate Siblings with a Nested AUTO Mode Query</span></span>
  <span data-ttu-id="cc69b-103">다음 예에서는 중첩된 AUTO 모드 쿼리를 사용하여 형제를 생성하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="cc69b-103">The following example shows how to generate siblings by using a nested AUTO mode query.</span></span> <span data-ttu-id="cc69b-104">이러한 XML을 생성하는 다른 방법은 EXPLICIT 모드를 사용하는 것 뿐입니다.</span><span class="sxs-lookup"><span data-stu-id="cc69b-104">The only other way to generate such XML is to use the EXPLICIT mode.</span></span> <span data-ttu-id="cc69b-105">하지만 이 방법은 복잡할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cc69b-105">However, this can be cumbersome.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cc69b-106">예제</span><span class="sxs-lookup"><span data-stu-id="cc69b-106">Example</span></span>  
 <span data-ttu-id="cc69b-107">이 쿼리는 판매 주문 정보를 제공하는 XML을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="cc69b-107">This query constructs XML that provides sales order information.</span></span> <span data-ttu-id="cc69b-108">여기에는 다음이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="cc69b-108">This includes the following:</span></span>  
  
-   <span data-ttu-id="cc69b-109">판매 주문 헤더 정보, `SalesOrderID`, `SalesPersonID`및 `OrderDate`가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="cc69b-109">Sales order header information, `SalesOrderID`, `SalesPersonID`, and `OrderDate`.</span></span> [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] <span data-ttu-id="cc69b-110">에서는 이 정보를 `SalesOrderHeader` 테이블에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="cc69b-110">stores this information in the `SalesOrderHeader` table.</span></span>  
  
-   <span data-ttu-id="cc69b-111">판매 주문 세부 정보.</span><span class="sxs-lookup"><span data-stu-id="cc69b-111">Sales order detail information.</span></span> <span data-ttu-id="cc69b-112">여기에는 주문된 하나 이상의 제품, 단가 및 주문 수량이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="cc69b-112">This includes one or more products ordered, the unit price, and the quantity ordered.</span></span> <span data-ttu-id="cc69b-113">이 정보는 `SalesOrderDetail` 테이블에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="cc69b-113">This information is stored in the `SalesOrderDetail` table.</span></span>  
  
-   <span data-ttu-id="cc69b-114">판매 직원 정보.</span><span class="sxs-lookup"><span data-stu-id="cc69b-114">Sales person information.</span></span> <span data-ttu-id="cc69b-115">주문을 접수한 판매 직원입니다.</span><span class="sxs-lookup"><span data-stu-id="cc69b-115">This is the salesperson who took the order.</span></span> <span data-ttu-id="cc69b-116">`SalesPerson` 테이블은 `SalesPersonID`를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="cc69b-116">The `SalesPerson` table provides the `SalesPersonID`.</span></span> <span data-ttu-id="cc69b-117">이 쿼리에서는 판매 직원 이름을 찾기 위해 이 테이블을 `Employee` 테이블에 조인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cc69b-117">For this query, you have to join this table to the `Employee` table to find the name of the sales person.</span></span>  
  
 <span data-ttu-id="cc69b-118">다음과 같은 두 개의 고유 `SELECT`는 모양이 약간 다른 XML을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="cc69b-118">The two distinct `SELECT` queries that follow generate XML with a small difference in shape.</span></span>  
  
 <span data-ttu-id="cc69b-119">첫 번째 쿼리는 <`SalesPerson`> 및 <`SalesOrderHeader`>가 <`SalesOrder`>의 자식(형제)으로 나타나는 XML을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="cc69b-119">The first query generates XML in which <`SalesPerson`> and <`SalesOrderHeader`> appear as sibling children of <`SalesOrder`>:</span></span>  
  
```  
SELECT   
      (SELECT top 2 SalesOrderID, SalesPersonID, CustomerID,  
         (select top 3 SalesOrderID, ProductID, OrderQty, UnitPrice  
           from Sales.SalesOrderDetail  
            WHERE  SalesOrderDetail.SalesOrderID =   
                   SalesOrderHeader.SalesOrderID  
            FOR XML AUTO, TYPE)  
        FROM  Sales.SalesOrderHeader  
        WHERE SalesOrderHeader.SalesOrderID = SalesOrder.SalesOrderID  
        for xml auto, type),  
        (SELECT *   
         FROM  (SELECT SalesPersonID, EmployeeID  
              FROM Sales.SalesPerson, HumanResources.Employee  
              WHERE SalesPerson.SalesPersonID = Employee.EmployeeID) As   
                     SalesPerson  
         WHERE  SalesPerson.SalesPersonID = SalesOrder.SalesPersonID  
       FOR XML AUTO, TYPE)  
FROM (SELECT SalesOrderHeader.SalesOrderID, SalesOrderHeader.SalesPersonID  
      FROM Sales.SalesOrderHeader, Sales.SalesPerson  
      WHERE SalesOrderHeader.SalesPersonID = SalesPerson.SalesPersonID  
     ) as SalesOrder  
ORDER BY SalesOrder.SalesOrderID  
FOR XML AUTO, TYPE  
```  
  
 <span data-ttu-id="cc69b-120">위의 쿼리에서 가장 외부에 있는 `SELECT` 문은 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="cc69b-120">In the previous query, the outermost `SELECT` statement does the following:</span></span>  
  
-   <span data-ttu-id="cc69b-121">`SalesOrder` 절에 지정된 행 집합인 `FROM`를 쿼리합니다.</span><span class="sxs-lookup"><span data-stu-id="cc69b-121">Queries the rowset, `SalesOrder`, specified in the `FROM` clause.</span></span> <span data-ttu-id="cc69b-122">결과는 하나 이상의 <`SalesOrder`> 요소가 있는 XML입니다.</span><span class="sxs-lookup"><span data-stu-id="cc69b-122">The result is an XML with one or more <`SalesOrder`> elements.</span></span>  
  
-   <span data-ttu-id="cc69b-123">`AUTO` 모드 및 `TYPE` 지시어를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="cc69b-123">Specifies `AUTO` mode and the `TYPE` directive.</span></span> <span data-ttu-id="cc69b-124">`AUTO`모드는 쿼리 결과를 XML로 변환 하 고 `TYPE` 지시어는 결과를 형식으로 반환 합니다 `xml` .</span><span class="sxs-lookup"><span data-stu-id="cc69b-124">`AUTO` mode transforms the query result into XML, and the `TYPE` directive returns the result as `xml` type.</span></span>  
  
-   <span data-ttu-id="cc69b-125">쉼표로 구분된 두 개의 중첩된 `SELECT` 문을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="cc69b-125">Includes two nested `SELECT` statements separated by a comma.</span></span> <span data-ttu-id="cc69b-126">첫 번째 중첩된 `SELECT` 는 판매 주문 정보, 헤더 및 세부 정보를 검색하고 두 번째 중첩된 `SELECT` 문은 판매 직원 정보를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="cc69b-126">The first nested `SELECT` retrieves sales order information, header and details, and the second nested `SELECT` statement retrieves salesperson information.</span></span>  
  
    -   <span data-ttu-id="cc69b-127">`SELECT` , `SalesOrderID`및 `SalesPersonID`를 검색하는 `CustomerID` 문 자체에 판매 주문 세부 정보를 반환하는 다른 중첩된 `SELECT ... FOR XML` 문( `AUTO` 모드와 `TYPE` 지시어 사용)이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="cc69b-127">The `SELECT` statement that retrieves `SalesOrderID`, `SalesPersonID`, and `CustomerID` itself includes another nested `SELECT ... FOR XML` statement (with `AUTO` mode and `TYPE` directive) that returns sales order detail information.</span></span>  
  
 <span data-ttu-id="cc69b-128">판매 직원 정보를 검색하는 `SELECT` 문은 `SalesPerson`절에서 생성된 `FROM` 행 집합을 쿼리합니다.</span><span class="sxs-lookup"><span data-stu-id="cc69b-128">The `SELECT` statement that retrieves the sales person information queries a rowset, `SalesPerson`, created in the `FROM` clause.</span></span> <span data-ttu-id="cc69b-129">`FOR XML` 쿼리가 작동하려면 `FROM` 절에서 생성된 익명 행 집합에 이름을 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cc69b-129">For `FOR XML` queries to work, you must provide a name for the anonymous rowset generated in the `FROM` clause.</span></span> <span data-ttu-id="cc69b-130">이 경우에 제공된 이름은 `SalesPerson`입니다.</span><span class="sxs-lookup"><span data-stu-id="cc69b-130">In this case, the name provided is `SalesPerson`.</span></span>  
  
 <span data-ttu-id="cc69b-131">다음은 결과의 일부입니다.</span><span class="sxs-lookup"><span data-stu-id="cc69b-131">This is the partial result:</span></span>  
  
```  
<SalesOrder>  
  <Sales.SalesOrderHeader SalesOrderID="43659" SalesPersonID="279" CustomerID="676">  
    <Sales.SalesOrderDetail SalesOrderID="43659" ProductID="776" OrderQty="1" UnitPrice="2024.9940" />  
    <Sales.SalesOrderDetail SalesOrderID="43659" ProductID="777" OrderQty="3" UnitPrice="2024.9940" />  
    <Sales.SalesOrderDetail SalesOrderID="43659" ProductID="778" OrderQty="1" UnitPrice="2024.9940" />  
  </Sales.SalesOrderHeader>  
  <SalesPerson SalesPersonID="279" EmployeeID="279" />  
</SalesOrder>  
...  
```  
  
 <span data-ttu-id="cc69b-132">다음 쿼리는 같은 판매 주문 정보를 생성하지만 결과 XML에서 <`SalesPerson`>이 <`SalesOrderDetail`>의 형제로 표시되는 점이 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="cc69b-132">The following query generates the same sales order information, except that in the resulting XML, the <`SalesPerson`> appears as a sibling of <`SalesOrderDetail`>:</span></span>  
  
```  
<SalesOrder>  
    <SalesOrderHeader ...>  
          <SalesOrderDetail .../>  
          <SalesOrderDetail .../>  
          ...  
          <SalesPerson .../>  
    </SalesOrderHeader>  
  
</SalesOrder>  
<SalesOrder>  
  ...  
</SalesOrder>  
```  
  
 <span data-ttu-id="cc69b-133">다음은 쿼리입니다.</span><span class="sxs-lookup"><span data-stu-id="cc69b-133">This is the query:</span></span>  
  
```  
SELECT SalesOrderID, SalesPersonID, CustomerID,  
             (select top 3 SalesOrderID, ProductID, OrderQty, UnitPrice  
              from Sales.SalesOrderDetail  
              WHERE SalesOrderDetail.SalesOrderID = SalesOrderHeader.SalesOrderID  
              FOR XML AUTO, TYPE),  
              (SELECT *   
               FROM  (SELECT SalesPersonID, EmployeeID  
                    FROM Sales.SalesPerson, HumanResources.Employee  
                    WHERE SalesPerson.SalesPersonID = Employee.EmployeeID) As SalesPerson  
               WHERE  SalesPerson.SalesPersonID = SalesOrderHeader.SalesPersonID  
         FOR XML AUTO, TYPE)  
FROM Sales.SalesOrderHeader  
WHERE SalesOrderID=43659 or SalesOrderID=43660  
FOR XML AUTO, TYPE  
```  
  
 <span data-ttu-id="cc69b-134">다음은 결과입니다.</span><span class="sxs-lookup"><span data-stu-id="cc69b-134">This is the result:</span></span>  
  
```  
<Sales.SalesOrderHeader SalesOrderID="43659" SalesPersonID="279" CustomerID="676">  
  <Sales.SalesOrderDetail SalesOrderID="43659" ProductID="776" OrderQty="1" UnitPrice="2024.9940" />  
  <Sales.SalesOrderDetail SalesOrderID="43659" ProductID="777" OrderQty="3" UnitPrice="2024.9940" />  
  <Sales.SalesOrderDetail SalesOrderID="43659" ProductID="778" OrderQty="1" UnitPrice="2024.9940" />  
  <SalesPerson SalesPersonID="279" EmployeeID="279" />  
</Sales.SalesOrderHeader>  
<Sales.SalesOrderHeader SalesOrderID="43660" SalesPersonID="279" CustomerID="117">  
  <Sales.SalesOrderDetail SalesOrderID="43660" ProductID="762" OrderQty="1" UnitPrice="419.4589" />  
  <Sales.SalesOrderDetail SalesOrderID="43660" ProductID="758" OrderQty="1" UnitPrice="874.7940" />  
  <SalesPerson SalesPersonID="279" EmployeeID="279" />  
</Sales.SalesOrderHeader>  
```  
  
 <span data-ttu-id="cc69b-135">`TYPE` 지시어는 쿼리 결과를 `xml` 유형으로 반환하기 때문에 여러 `xml` 데이터 형식 메서드를 사용하여 결과 XML을 쿼리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cc69b-135">Because the `TYPE` directive returns a query result as `xml` type, you can query the resulting XML by using various `xml` data type methods.</span></span> <span data-ttu-id="cc69b-136">자세한 내용은 [xml 데이터 형식 메서드](/sql/t-sql/xml/xml-data-type-methods)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="cc69b-136">For more information, see [xml Data Type Methods](/sql/t-sql/xml/xml-data-type-methods).</span></span> <span data-ttu-id="cc69b-137">다음 쿼리에서는 아래 사항을 유의하십시오.</span><span class="sxs-lookup"><span data-stu-id="cc69b-137">In the following query, note the following:</span></span>  
  
-   <span data-ttu-id="cc69b-138">이전 쿼리가 `FROM` 절에 추가되었습니다.</span><span class="sxs-lookup"><span data-stu-id="cc69b-138">The previous query is added in the `FROM` clause.</span></span> <span data-ttu-id="cc69b-139">쿼리 결과는 테이블로 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="cc69b-139">The query result is returned as a table.</span></span> <span data-ttu-id="cc69b-140">추가된 `XmlCol` 별칭에 유의하십시오.</span><span class="sxs-lookup"><span data-stu-id="cc69b-140">Note the `XmlCol` alias that is added.</span></span>  
  
-   <span data-ttu-id="cc69b-141">`SELECT` 절은 `XmlCol` 절에 반환된 `FROM` 에 대해 XQuery를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="cc69b-141">The `SELECT` clause specifies an XQuery against the `XmlCol` returned in the `FROM` clause.</span></span> <span data-ttu-id="cc69b-142">`query()` 데이터 형식의 `xml` 메서드는 XQuery를 지정하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="cc69b-142">The `query()` method of the `xml` data type is used in specifying the XQuery.</span></span> <span data-ttu-id="cc69b-143">자세한 내용은 [query&#40;&#41; 메서드&#40;xml 데이터 형식&#41;](/sql/t-sql/xml/query-method-xml-data-type)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="cc69b-143">For more information, see [query&#40;&#41; Method &#40;xml Data Type&#41;](/sql/t-sql/xml/query-method-xml-data-type).</span></span>  
  
    ```  
    SELECT XmlCol.query('<Root> { /* } </Root>')  
    FROM (  
    SELECT SalesOrderID, SalesPersonID, CustomerID,  
                 (select top 3 SalesOrderID, ProductID, OrderQty, UnitPrice  
                  from Sales.SalesOrderDetail  
                  WHERE SalesOrderDetail.SalesOrderID = SalesOrderHeader.SalesOrderID  
                  FOR XML AUTO, TYPE),  
                  (SELECT *   
                   FROM  (SELECT SalesPersonID, EmployeeID  
                        FROM Sales.SalesPerson, HumanResources.Employee  
                        WHERE SalesPerson.SalesPersonID = Employee.EmployeeID) As SalesPerson  
                   WHERE  SalesPerson.SalesPersonID = SalesOrderHeader.SalesPersonID  
             FOR XML AUTO, TYPE)  
    FROM Sales.SalesOrderHeader  
    WHERE SalesOrderID='43659' or SalesOrderID='43660'  
    FOR XML AUTO, TYPE ) as T(XmlCol)  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="cc69b-144">참고 항목</span><span class="sxs-lookup"><span data-stu-id="cc69b-144">See Also</span></span>  
 [<span data-ttu-id="cc69b-145">중첩 FOR XML 쿼리 사용</span><span class="sxs-lookup"><span data-stu-id="cc69b-145">Use Nested FOR XML Queries</span></span>](use-nested-for-xml-queries.md)  
  
  
