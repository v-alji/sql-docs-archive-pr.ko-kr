---
title: 이름이 있는 열 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- names [SQL Server], columns with
ms.assetid: c994e089-4cfc-4e9b-b7fc-e74f6014b51a
author: rothja
ms.author: jroth
ms.openlocfilehash: 32cfe617b80ed216374249961b85eae401011a67
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87729168"
---
# <a name="columns-with-a-name"></a><span data-ttu-id="ba44d-102">이름이 있는 열</span><span class="sxs-lookup"><span data-stu-id="ba44d-102">Columns with a Name</span></span>
  <span data-ttu-id="ba44d-103">다음은 이름이 있는 행 집합 열이 대/소문자를 구분하여 결과 XML에 매핑되는 특정 조건입니다.</span><span class="sxs-lookup"><span data-stu-id="ba44d-103">The following are the specific conditions in which rowset columns with a name are mapped, case-sensitive, to the resulting XML:</span></span>  
  
-   <span data-ttu-id="ba44d-104">열 이름이 \@ 기호로 시작하는 경우</span><span class="sxs-lookup"><span data-stu-id="ba44d-104">The column name starts with an at sign (\@).</span></span>  
  
-   <span data-ttu-id="ba44d-105">열 이름이 \@ 기호로 시작하지 않는 경우</span><span class="sxs-lookup"><span data-stu-id="ba44d-105">The column name does not start with an at sign (\@).</span></span>  
  
-   <span data-ttu-id="ba44d-106">열 이름이 \@ 기호로 시작하지 않고 슬래시 기호(/)를 포함하는 경우</span><span class="sxs-lookup"><span data-stu-id="ba44d-106">The column name does not start with an at sign\@ and contains a slash mark (/).</span></span>  
  
-   <span data-ttu-id="ba44d-107">여러 열이 같은 접두사를 공유하는 경우</span><span class="sxs-lookup"><span data-stu-id="ba44d-107">Several columns share the same prefix.</span></span>  
  
-   <span data-ttu-id="ba44d-108">하나의 열에 다른 이름이 있는 경우</span><span class="sxs-lookup"><span data-stu-id="ba44d-108">One column has a different name.</span></span>  
  
## <a name="column-name-starts-with-an-at-sign-"></a><span data-ttu-id="ba44d-109">열 이름이 \@ 기호로 시작하는 경우</span><span class="sxs-lookup"><span data-stu-id="ba44d-109">Column Name Starts with an At Sign (\@)</span></span>  
 <span data-ttu-id="ba44d-110">열 이름이 at 기호 ()로 시작 \@ 하 고 슬래시 기호 (/)를 포함 하지 않는 경우 `row` 해당 열 값을 가진 <> 요소의 특성이 생성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ba44d-110">If the column name starts with an at sign (\@) and does not contain a slash mark (/), an attribute of the <`row`> element that has the corresponding column value is created.</span></span> <span data-ttu-id="ba44d-111">예를 들어 다음 쿼리는 2개의 열(\@PmId, Name)로 구성된 행 집합을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="ba44d-111">For example, the following query returns a two-column (\@PmId, Name) rowset.</span></span> <span data-ttu-id="ba44d-112">결과 XML에서 **PmId** 특성이 해당 <`row`> 요소에 추가되고 ProductModelID의 값이 여기에 할당됩니다.</span><span class="sxs-lookup"><span data-stu-id="ba44d-112">In the resulting XML, a **PmId** attribute is added to the corresponding <`row`> element and a value of ProductModelID is assigned to it.</span></span>  
  
```  
  
SELECT ProductModelID as "@PmId",  
       Name  
FROM Production.ProductModel  
WHERE ProductModelID=7  
FOR XML PATH   
go  
  
```  
  
 <span data-ttu-id="ba44d-113">다음은 결과입니다.</span><span class="sxs-lookup"><span data-stu-id="ba44d-113">This is the result:</span></span>  
  
```  
<row PmId="7">  
  <Name>HL Touring Frame</Name>  
</row>  
```  
  
 <span data-ttu-id="ba44d-114">특성은 같은 수준에서 요소 노드, 텍스트 노드 등 다른 노드 유형 앞에 와야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ba44d-114">Note that attributes must come before any other node types, such as element nodes and text nodes, in the same level.</span></span> <span data-ttu-id="ba44d-115">다음 쿼리는 오류를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="ba44d-115">The following query will return an error:</span></span>  
  
```  
SELECT Name,  
       ProductModelID as "@PmId"  
FROM Production.ProductModel  
WHERE ProductModelID=7  
FOR XML PATH   
go  
```  
  
## <a name="column-name-does-not-start-with-an-at-sign-"></a><span data-ttu-id="ba44d-116">열 이름이 \@ 기호로 시작하지 않는 경우</span><span class="sxs-lookup"><span data-stu-id="ba44d-116">Column Name Does Not Start with an At Sign (\@)</span></span>  
 <span data-ttu-id="ba44d-117">열 이름이 기호 ()로 시작 하지 않고 \@ XPath 노드 테스트 중 하나가 아니고 슬래시 기호 (/)를 포함 하지 않는 경우 기본적으로 <> row 요소의 하위 요소인 XML 요소가 `row` 생성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ba44d-117">If the column name does not start with an at sign (\@), is not one of the XPath node tests, and does not contain a slash mark (/), an XML element that is a subelement of the row element, <`row`> by default, is created.</span></span>  
  
 <span data-ttu-id="ba44d-118">다음 쿼리는 결과인 열 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ba44d-118">The following query specifies the column name, the result.</span></span> <span data-ttu-id="ba44d-119">따라서 <`result`> 요소 자식이 <`row`> 요소에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="ba44d-119">Therefore, a <`result`> element child is added to the <`row`> element.</span></span>  
  
```  
SELECT 2+2 as result  
for xml PATH  
```  
  
 <span data-ttu-id="ba44d-120">다음은 결과입니다.</span><span class="sxs-lookup"><span data-stu-id="ba44d-120">This is the result:</span></span>  
  
```  
<row>  
  <result>4</result>  
</row>  
```  
  
 <span data-ttu-id="ba44d-121">다음 쿼리는 **xml** 유형의 Instructions 열에 대해 지정된 XQuery에서 반환하는 XML에 대해 열 이름 ManuWorkCenterInformation을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ba44d-121">The following query specifies the column name, ManuWorkCenterInformation, for the XML returned by the XQuery specified against Instructions column of **xml** type.</span></span> <span data-ttu-id="ba44d-122">따라서 <`ManuWorkCenterInformation`> 요소가 <`row`> 요소의 자식으로 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="ba44d-122">Therefore, a <`ManuWorkCenterInformation`> element is added as a child of the <`row`> element.</span></span>  
  
```  
SELECT   
       ProductModelID,  
       Name,  
       Instructions.query('declare namespace MI="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
                /MI:root/MI:Location   
              ') as ManuWorkCenterInformation  
FROM Production.ProductModel  
WHERE ProductModelID=7  
FOR XML PATH   
go  
```  
  
 <span data-ttu-id="ba44d-123">다음은 결과입니다.</span><span class="sxs-lookup"><span data-stu-id="ba44d-123">This is the result:</span></span>  
  
```  
<row>  
  <ProductModelID>7</ProductModelID>  
  <Name>HL Touring Frame</Name>  
  <ManuWorkCenterInformation>  
    <MI:Location ...LocationID="10" ...></MI:Location>  
    <MI:Location ...LocationID="20" ...></MI:Location>  
     ...  
  </ManuWorkCenterInformation>  
</row>  
```  
  
## <a name="column-name-does-not-start-with-an-at-sign--and-contains-a-slash-mark-"></a><span data-ttu-id="ba44d-124">열 이름이 \@ 기호로 시작하지 않고 슬래시 기호(/)를 포함하는 경우</span><span class="sxs-lookup"><span data-stu-id="ba44d-124">Column Name Does Not Start with an At Sign (\@) and Contains a Slash Mark (/)</span></span>  
 <span data-ttu-id="ba44d-125">열 이름이 \@ 기호로 시작하지 않지만 슬래시 기호(/)를 포함할 경우 열 이름은 XML 계층을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="ba44d-125">If the column name does not start with an at sign (\@), but contains a slash mark (/), the column name indicates an XML hierarchy.</span></span> <span data-ttu-id="ba44d-126">예를 들어 열 이름이 "Name1/Name2/Name3.../Name***n*** "이면 각 Name***i*** 는 현재 행 요소(i=1인 경우)에 중첩된 요소 이름을 나타내거나 이름이 Name***i-1***인 요소 아래의 요소 이름을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="ba44d-126">For example, if the column name is "Name1/Name2/Name3.../Name***n*** ", each Name***i*** represents an element name that is nested in the current row element (for i=1) or that is under the element that has the name Name***i-1***.</span></span> <span data-ttu-id="ba44d-127">Name***n***이 '\@'으로 시작하는 경우 Name***n-1*** 요소의 특성에 매핑됩니다.</span><span class="sxs-lookup"><span data-stu-id="ba44d-127">If Name***n*** starts with '\@', it is mapped to an attribute of Name***n-1*** element.</span></span>  
  
 <span data-ttu-id="ba44d-128">예를 들어 다음 쿼리는 이름, 중간 이름 및 성을 포함하는 복잡한 요소 EmpName으로 표현되는 직원 ID와 이름을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="ba44d-128">For example, the following query returns an employee ID and name that are represented as a complex element EmpName that contains a First, Middle, and Last name.</span></span>  
  
```  
SELECT EmployeeID "@EmpID",   
       FirstName  "EmpName/First",   
       MiddleName "EmpName/Middle",   
       LastName   "EmpName/Last"  
FROM   HumanResources.Employee E, Person.Contact C  
WHERE  E.EmployeeID = C.ContactID  
AND    E.EmployeeID=1  
FOR XML PATH  
```  
  
 <span data-ttu-id="ba44d-129">PATH 모드에서 XML을 생성할 때 열 이름이 경로로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="ba44d-129">The column names are used as a path in constructing XML in the PATH mode.</span></span> <span data-ttu-id="ba44d-130">직원 ID 값을 포함 하는 열 이름은 ' '로 시작 \@ 합니다. 따라서 **EmpID**특성은 <> 요소에 추가 됩니다 `row` .</span><span class="sxs-lookup"><span data-stu-id="ba44d-130">The column name that contains employee ID values, starts with '\@'.Therefore, an attribute, **EmpID**, is added to the <`row`> element.</span></span> <span data-ttu-id="ba44d-131">다른 모든 열에는 계층을 나타내는 열 이름에 슬래시 기호('/')가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ba44d-131">All other columns include a slash mark ('/') in the column name that indicates hierarchy.</span></span> <span data-ttu-id="ba44d-132">결과 XML은 <`row`> 요소 아래에 <`EmpName`> 자식을 포함하고 <`EmpName`> 자식은 <`First`>, <`Middle`> 및 <`Last`> 요소 자식을 갖습니다.</span><span class="sxs-lookup"><span data-stu-id="ba44d-132">The resulting XML will have the <`EmpName`> child under the <`row`> element, and the <`EmpName`> child will have <`First`>, <`Middle`> and <`Last`> element children.</span></span>  
  
```  
<row EmpID="1">  
  <EmpName>  
    <First>Gustavo</First>  
    <Last>Achong</Last>  
  </EmpName>  
</row>  
```  
  
 <span data-ttu-id="ba44d-133">직원 중간 이름은 Null이며 기본적으로 Null 값이 매핑할 요소나 특성이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ba44d-133">The employee middle name is null and, by default, the null value maps to the absence of the element or attribute.</span></span> <span data-ttu-id="ba44d-134">NULL 값에 대해 요소를 생성하려는 경우 이 쿼리에서와 같이 ELEMENTS 지시어와 XSINIL을 함께 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ba44d-134">If you want elements generated for the NULL values, you can specify the ELEMENTS directive with XSINIL as shown in this query.</span></span>  
  
```  
SELECT EmployeeID "@EmpID",   
       FirstName  "EmpName/First",   
       MiddleName "EmpName/Middle",   
       LastName   "EmpName/Last"  
FROM   HumanResources.Employee E, Person.Contact C  
WHERE  E.EmployeeID = C.ContactID  
AND    E.EmployeeID=1  
FOR XML PATH, ELEMENTS XSINIL  
```  
  
 <span data-ttu-id="ba44d-135">다음은 결과입니다.</span><span class="sxs-lookup"><span data-stu-id="ba44d-135">This is the result:</span></span>  
  
```  
<row xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"   
      EmpID="1">  
  <EmpName>  
    <First>Gustavo</First>  
    <Middle xsi:nil="true" />  
    <Last>Achong</Last>  
  </EmpName>  
</row>  
```  
  
 <span data-ttu-id="ba44d-136">기본적으로 PATH 모드는 요소 중심의 XML을 생성하므로</span><span class="sxs-lookup"><span data-stu-id="ba44d-136">By default, the PATH mode generates element-centric XML.</span></span> <span data-ttu-id="ba44d-137">PATH 모드 쿼리에 ELEMENTS 지시어를 지정하면 아무 영향도 미치지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ba44d-137">Therefore, specifying the ELEMENTS directive in a PATH mode query has no effect.</span></span> <span data-ttu-id="ba44d-138">그러나 이전 예에서와 같이 ELEMENTS 지시어를 XSINIL과 함께 사용하면 Null 값에 대한 요소를 생성하는 데 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="ba44d-138">However, as shown in the previous example, the ELEMENTS directive is useful with XSINIL to generate elements for null values.</span></span>  
  
 <span data-ttu-id="ba44d-139">다음 쿼리에서는 ID와 이름 외에 직원 주소를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="ba44d-139">Besides the ID and name, the following query retrieves an employee address.</span></span> <span data-ttu-id="ba44d-140">주소 열에 대한 열 이름에 있는 각 경로대로 <`Address`> 요소 자식이 <`row`> 요소에 추가되고 주소 정보가 <`Address`> 요소의 요소 자식으로 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="ba44d-140">As per the path in the column names for address columns, an <`Address`> element child is added to the <`row`> element and the address details are added as element children of the <`Address`> element.</span></span>  
  
```  
SELECT EmployeeID   "@EmpID",   
       FirstName    "EmpName/First",   
       MiddleName   "EmpName/Middle",   
       LastName     "EmpName/Last",  
       AddressLine1 "Address/AddrLine1",  
       AddressLine2 "Address/AddrLIne2",  
       City         "Address/City"  
FROM   HumanResources.Employee E, Person.Contact C, Person.Address A  
WHERE  E.EmployeeID = C.ContactID  
AND    E.AddressID = A.AddressID  
AND    E.EmployeeID=1  
FOR XML PATH  
```  
  
 <span data-ttu-id="ba44d-141">다음은 결과입니다.</span><span class="sxs-lookup"><span data-stu-id="ba44d-141">This is the result:</span></span>  
  
```  
<row EmpID="1">  
  <EmpName>  
    <First>Gustavo</First>  
    <Last>Achong</Last>  
  </EmpName>  
  <Address>  
    <AddrLine1>7726 Driftwood Drive</AddrLine1>  
    <City>Monroe</City>  
  </Address>  
</row>  
```  
  
## <a name="several-columns-share-the-same-path-prefix"></a><span data-ttu-id="ba44d-142">여러 열이 같은 경로 접두사를 공유하는 경우</span><span class="sxs-lookup"><span data-stu-id="ba44d-142">Several Columns Share the Same Path Prefix</span></span>  
 <span data-ttu-id="ba44d-143">이어지는 여러 열이 같은 경로 접두사를 공유할 경우 같은 이름으로 함께 그룹화됩니다.</span><span class="sxs-lookup"><span data-stu-id="ba44d-143">If several subsequent columns share the same path prefix, they are grouped together under the same name.</span></span> <span data-ttu-id="ba44d-144">다른 네임스페이스 접두사가 사용되면 같은 네임스페이스로 바인딩되더라도 경로가 다르다고 간주됩니다.</span><span class="sxs-lookup"><span data-stu-id="ba44d-144">If different namespace prefixes are being used even if they are bound to the same namespace, a path is considered different.</span></span> <span data-ttu-id="ba44d-145">이전 쿼리에서 FirstName, MiddleName 및 LastName 열은 동일한 EmpName 접두사를 공유하므로 <`EmpName`> 요소의 자식으로 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="ba44d-145">In the previous query, the FirstName, MiddleName, and LastName columns share the same EmpName prefix.Therefore, they are added as children of the <`EmpName`> element.</span></span> <span data-ttu-id="ba44d-146">이전 예제에서 <`Address`> 요소를 만들던 것도 이와 같은 경우입니다.</span><span class="sxs-lookup"><span data-stu-id="ba44d-146">This is also the case when you were creating the <`Address`> element in the previous example.</span></span>  
  
## <a name="one-column-has-a-different-name"></a><span data-ttu-id="ba44d-147">하나의 열에 다른 이름이 있는 경우</span><span class="sxs-lookup"><span data-stu-id="ba44d-147">One Column Has a Different Name</span></span>  
 <span data-ttu-id="ba44d-148">이름이 다른 열이 중간에 나타나면 다음의 수정된 쿼리에서와 같이 그룹화가 해제됩니다.</span><span class="sxs-lookup"><span data-stu-id="ba44d-148">If a column with a different name appears in between, it will break the grouping, as shown in the following modified query.</span></span> <span data-ttu-id="ba44d-149">쿼리는 FirstName 열과 MiddleName 열 사이에 주소 열을 추가하여 이전 쿼리에 지정된 대로 FirstName, MiddleName 및 LastName의 그룹화를 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="ba44d-149">The query breaks the grouping of FirstName, MiddleName, and LastName, as specified in the previous query, by adding address columns in between the FirstName and MiddleName columns.</span></span>  
  
```  
SELECT EmployeeID "@EmpID",   
       FirstName "EmpName/First",   
       AddressLine1 "Address/AddrLine1",  
       AddressLine2 "Address/AddrLIne2",  
       City "Address/City",  
       MiddleName "EmpName/Middle",   
       LastName "EmpName/Last"  
FROM   HumanResources.EmployeeAddress E, Person.Contact C, Person.Address A  
WHERE  E.EmployeeID = C.ContactID  
AND    E.AddressID = A.AddressID  
AND    E.EmployeeID=1  
FOR XML PATH  
```  
  
 <span data-ttu-id="ba44d-150">그 결과 두 개의 <`EmpName`> 요소가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="ba44d-150">As a result, the query creates two <`EmpName`> elements.</span></span> <span data-ttu-id="ba44d-151">첫 번째 <`EmpName`> 요소는 <`FirstName`> 요소 자식을 포함하고 두 번째 <`EmpName`> 요소는 <`MiddleName`> 및 <`LastName`> 요소 자식을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="ba44d-151">The first <`EmpName`> element has the <`FirstName`> element child and the second <`EmpName`> element has the <`MiddleName`> and <`LastName`> element children.</span></span>  
  
 <span data-ttu-id="ba44d-152">다음은 결과입니다.</span><span class="sxs-lookup"><span data-stu-id="ba44d-152">This is the result:</span></span>  
  
```  
<row EmpID="1">  
  <EmpName>  
    <First>Gustavo</First>  
  </EmpName>  
  <Address>  
    <AddrLine1>7726 Driftwood Drive</AddrLine1>  
    <City>Monroe</City>  
  </Address>  
  <EmpName>  
    <Last>Achong</Last>  
  </EmpName>  
</row>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ba44d-153">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ba44d-153">See Also</span></span>  
 [<span data-ttu-id="ba44d-154">FOR XML에서 PATH 모드 사용</span><span class="sxs-lookup"><span data-stu-id="ba44d-154">Use PATH Mode with FOR XML</span></span>](use-path-mode-with-for-xml.md)  
  
  
