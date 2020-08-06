---
title: XPath 쿼리에 축 지정 (SQLXML 4.0) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- XPath queries [SQLXML], axes
- context node [SQLXML]
- attribute axis [SQLXML]
- axis [SQLXML]
- child axis
- parent axis
- axes [SQLXML]
ms.assetid: d17b8278-da58-4576-95b4-7a92772566d8
author: rothja
ms.author: jroth
ms.openlocfilehash: f6f17404ea109bb0e687f9116b61025bbc411008
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646286"
---
# <a name="specifying-axes-in-xpath-queries-sqlxml-40"></a><span data-ttu-id="f0da3-102">XPath 쿼리에 축 지정(SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="f0da3-102">Specifying Axes in XPath Queries (SQLXML 4.0)</span></span>
  <span data-ttu-id="f0da3-103">다음 예에서는 XPath 쿼리에 축을 지정하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="f0da3-103">The following examples show how axes are specified in XPath queries.</span></span>  
  
 <span data-ttu-id="f0da3-104">이 예의 XPath 쿼리는 SampleSchema1.xml에 포함된 매핑 스키마에 대해 지정되었습니다.</span><span class="sxs-lookup"><span data-stu-id="f0da3-104">The XPath queries in these examples are specified against the mapping schema contained in SampleSchema1.xml.</span></span> <span data-ttu-id="f0da3-105">이 샘플 스키마에 대 한 자세한 내용은 [예제 주석 XSD schema For XPath 예제 &#40;SQLXML 4.0&#41;](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f0da3-105">For information about this sample schema, see [Sample Annotated XSD Schema for XPath Examples &#40;SQLXML 4.0&#41;](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md).</span></span>  
  
## <a name="examples"></a><span data-ttu-id="f0da3-106">예</span><span class="sxs-lookup"><span data-stu-id="f0da3-106">Examples</span></span>  
  
### <a name="a-retrieve-child-elements-of-the-context-node"></a><span data-ttu-id="f0da3-107">A.</span><span class="sxs-lookup"><span data-stu-id="f0da3-107">A.</span></span> <span data-ttu-id="f0da3-108">컨텍스트 노드의 자식 요소 검색</span><span class="sxs-lookup"><span data-stu-id="f0da3-108">Retrieve child elements of the context node</span></span>  
 <span data-ttu-id="f0da3-109">다음 XPath 쿼리는 **\<Contact>** 컨텍스트 노드의 모든 자식 요소를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="f0da3-109">The following XPath query selects all the **\<Contact>** child elements of the context node:</span></span>  
  
```  
/child::Contact  
```  
  
 <span data-ttu-id="f0da3-110">쿼리에서는 `child` 축 이며 `Contact` 노드 테스트 (는 `Contact` **\<element>** \<element> 축과 관련 된 기본 노드 형식 이므로가 노드인 경우 TRUE `child` )입니다.</span><span class="sxs-lookup"><span data-stu-id="f0da3-110">In the query, `child` is the axis and `Contact` is the node test (TRUE if `Contact` is an **\<element>** node, because \<element> is the primary node type associated with the `child` axis).</span></span>  
  
 <span data-ttu-id="f0da3-111">기본값은 `child` 축입니다.</span><span class="sxs-lookup"><span data-stu-id="f0da3-111">The `child` axis is the default.</span></span> <span data-ttu-id="f0da3-112">따라서 다음과 같이 쿼리를 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f0da3-112">Therefore, the query can be written as:</span></span>  
  
```  
/Contact  
```  
  
##### <a name="to-test-the-xpath-query-against-the-mapping-schema"></a><span data-ttu-id="f0da3-113">매핑 스키마에 대해 XPath 쿼리를 테스트하려면</span><span class="sxs-lookup"><span data-stu-id="f0da3-113">To test the XPath query against the mapping schema</span></span>  
  
1.  <span data-ttu-id="f0da3-114">[샘플 스키마 코드](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md) 를 복사 하 여 텍스트 파일에 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="f0da3-114">Copy the [sample schema code](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md) and paste it into a text file.</span></span> <span data-ttu-id="f0da3-115">파일을 SampleSchema1.xml로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="f0da3-115">Save the file as SampleSchema1.xml.</span></span>  
  
2.  <span data-ttu-id="f0da3-116">다음 템플릿(XPathAxesSampleA.xml)을 만들어 SampleSchema1.xml이 저장된 디렉터리에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="f0da3-116">Create the following template (XPathAxesSampleA.xml) and save it in the directory where SampleSchema1.xml was saved.</span></span>  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:xpath-query mapping-schema="SampleSchema1.xml">  
        /Contact  
      </sql:xpath-query>  
    </ROOT>  
    ```  
  
     <span data-ttu-id="f0da3-117">매핑 스키마(SampleSchema1.xml)에 대해 지정된 디렉터리 경로는 템플릿이 저장된 디렉터리에 상대적입니다.</span><span class="sxs-lookup"><span data-stu-id="f0da3-117">The directory path specified for the mapping schema (SampleSchema1.xml) is relative to the directory where the template is saved.</span></span> <span data-ttu-id="f0da3-118">또한 다음과 같이 절대 경로를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f0da3-118">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\MyDir\SampleSchema1.xml"  
    ```  
  
3.  <span data-ttu-id="f0da3-119">SQLXML 4.0 테스트 스크립트(Sqlxml4test.vbs)를 만든 다음 이 스크립트를 사용하여 템플릿을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="f0da3-119">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="f0da3-120">자세한 내용은 [ADO를 사용 하 여 SQLXML 4.0 쿼리 실행](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f0da3-120">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="f0da3-121">다음은 템플릿 실행 결과 집합의 일부입니다.</span><span class="sxs-lookup"><span data-stu-id="f0da3-121">Here is the partial result set of the template execution:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">   
  <Contact ContactID="1" LastName="Achong" FirstName="Gustavo" Title="Mr." />   
  <Contact ContactID="2" LastName="Abel" FirstName="Catherine" Title="Ms." />   
  <Contact ContactID="3" LastName="Abercrombie" FirstName="Kim" Title="Ms." />   
  <Contact ContactID="4" LastName="Acevedo" FirstName="Humberto" Title="Sr." />  
  ...  
</ROOT>  
```  
  
### <a name="b-retrieve-grandchildren-of-the-context-node"></a><span data-ttu-id="f0da3-122">B.</span><span class="sxs-lookup"><span data-stu-id="f0da3-122">B.</span></span> <span data-ttu-id="f0da3-123">컨텍스트 노드의 손자 검색</span><span class="sxs-lookup"><span data-stu-id="f0da3-123">Retrieve grandchildren of the context node</span></span>  
 <span data-ttu-id="f0da3-124">다음 XPath 쿼리는 **\<Order>** **\<Customer>** 컨텍스트 노드의 요소 자식의 요소 자식을 모두 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="f0da3-124">The following XPath query selects all the **\<Order>** element children of the **\<Customer>** element children of the context node:</span></span>  
  
```  
/child::Customer/child::Order  
```  
  
 <span data-ttu-id="f0da3-125">쿼리에서 `child` 는 축이 고 `Customer` 및 `Order` 는 노드 테스트 (노드가 **\<element>** **\<element>** 축에 대 한 주 노드인지 때문에 Customer 및 Order가 노드인 경우 TRUE `child` )입니다.</span><span class="sxs-lookup"><span data-stu-id="f0da3-125">In the query, `child` is the axis and `Customer` and `Order` are the node tests (these node tests are TRUE if Customer and Order are **\<element>** nodes, because the **\<element>** node is the primary node for the `child` axis).</span></span> <span data-ttu-id="f0da3-126">일치 하는 각 노드에 대해 일치 하는 **\<Customer>** 노드가 **\<Orders>** 결과에 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f0da3-126">For each node matching **\<Customer>**, the nodes matching **\<Orders>** are added to the result.</span></span> <span data-ttu-id="f0da3-127">**\<Order>** 결과 집합에만 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f0da3-127">Only **\<Order>** is returned in the result set.</span></span>  
  
 <span data-ttu-id="f0da3-128">기본값은 `child` 축입니다.</span><span class="sxs-lookup"><span data-stu-id="f0da3-128">The `child` axis is the default.</span></span> <span data-ttu-id="f0da3-129">따라서 다음과 같이 쿼리를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f0da3-129">Therefore, the query can be specified as:</span></span>  
  
```  
/Customer/Order  
```  
  
##### <a name="to-test-the-xpath-query-against-the-mapping-schema"></a><span data-ttu-id="f0da3-130">매핑 스키마에 대해 XPath 쿼리를 테스트하려면</span><span class="sxs-lookup"><span data-stu-id="f0da3-130">To test the XPath query against the mapping schema</span></span>  
  
1.  <span data-ttu-id="f0da3-131">[샘플 스키마 코드](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md) 를 복사 하 여 텍스트 파일에 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="f0da3-131">Copy the [sample schema code](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md) and paste it into a text file.</span></span> <span data-ttu-id="f0da3-132">파일을 SampleSchema1.xml로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="f0da3-132">Save the file as SampleSchema1.xml.</span></span>  
  
2.  <span data-ttu-id="f0da3-133">다음 템플릿(XPathAxesSampleB.xml)을 만들고 다음과 같은 디렉터리에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="f0da3-133">Create the following template (XPathAxesSampleB.xml) and save it in the directory where:</span></span>  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:xpath-query mapping-schema="SampleSchema1.xml">  
        /Customer/Order  
      </sql:xpath-query>  
    </ROOT>  
    ```  
  
     <span data-ttu-id="f0da3-134">매핑 스키마(SampleSchema1.xml)에 대해 지정된 디렉터리 경로는 템플릿이 저장된 디렉터리에 상대적입니다.</span><span class="sxs-lookup"><span data-stu-id="f0da3-134">The directory path specified for the mapping schema (SampleSchema1.xml) is relative to the directory where the template is saved.</span></span> <span data-ttu-id="f0da3-135">또한 다음과 같이 절대 경로를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f0da3-135">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\MyDir\SampleSchema1.xml"  
    ```  
  
3.  <span data-ttu-id="f0da3-136">SQLXML 4.0 테스트 스크립트(Sqlxml4test.vbs)를 만든 다음 이 스크립트를 사용하여 템플릿을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="f0da3-136">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="f0da3-137">자세한 내용은 [ADO를 사용 하 여 SQLXML 4.0 쿼리 실행](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f0da3-137">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="f0da3-138">다음은 템플릿 실행 결과 집합의 일부입니다.</span><span class="sxs-lookup"><span data-stu-id="f0da3-138">Here is the partial result set of the template execution:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Order SalesOrderID="Ord-43860" SalesPersonID="280"   
         OrderDate="2001-08-01T00:00:00"   
         DueDate="2001-08-13T00:00:00"   
         ShipDate="2001-08-08T00:00:00">  
  <OrderDetail ProductID="Prod-729" UnitPrice="226.8571"   
               OrderQty="1" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-732" UnitPrice="440.1742"   
               OrderQty="1" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-738" UnitPrice="220.2496"   
               OrderQty="1" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-753" UnitPrice="2576.3544"   
               OrderQty="2" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-756" UnitPrice="1049.7528"   
               OrderQty="1" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-758" UnitPrice="1049.7528"   
               OrderQty="2" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-761" UnitPrice="503.3507"   
               OrderQty="2" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-762" UnitPrice="503.3507"   
               OrderQty="1" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-763" UnitPrice="503.3507"   
               OrderQty="1" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-765" UnitPrice="503.3507"   
               OrderQty="2" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-768" UnitPrice="503.3507"   
               OrderQty="1" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-770" UnitPrice="503.3507"   
               OrderQty="1" UnitPriceDiscount="0" />   
  </Order>  
   ...  
</ROOT>  
```  
  
 <span data-ttu-id="f0da3-139">XPath 쿼리가로 지정 된 경우 `Customer/Order/OrderDetail` 쿼리와 일치 하는 각 노드에서 **\<Customer>** 해당 **\<Order>** 요소로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="f0da3-139">If the XPath query is specified as `Customer/Order/OrderDetail`, from each node matching **\<Customer>** the query navigates to its **\<Order>** elements.</span></span> <span data-ttu-id="f0da3-140">그리고 일치 하는 각 노드에 대해 **\<Order>** 쿼리는 노드를 **\<OrderDetail>** 결과에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="f0da3-140">And for each node matching **\<Order>**, the query adds the nodes **\<OrderDetail>** to the result.</span></span> <span data-ttu-id="f0da3-141">**\<OrderDetail>** 결과 집합에만 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f0da3-141">Only **\<OrderDetail>** is returned in the result set.</span></span>  
  
### <a name="c-use--to-specify-the-parent-axis"></a><span data-ttu-id="f0da3-142">C.</span><span class="sxs-lookup"><span data-stu-id="f0da3-142">C.</span></span> <span data-ttu-id="f0da3-143">..를 사용하여</span><span class="sxs-lookup"><span data-stu-id="f0da3-143">Use ..</span></span> <span data-ttu-id="f0da3-144">부모 축 지정</span><span class="sxs-lookup"><span data-stu-id="f0da3-144">to specify the parent axis</span></span>  
 <span data-ttu-id="f0da3-145">다음 쿼리는 **\<Order>** **\<Customer>** **CustomerID** 특성 값이 1 인 부모 요소를 사용 하 여 모든 요소를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="f0da3-145">The following query retrieves all the **\<Order>** elements with a parent **\<Customer>** element with a **CustomerID** attribute value of 1.</span></span> <span data-ttu-id="f0da3-146">쿼리에서는 `child` 조건자의 축을 사용 하 여 요소의 부모를 찾습니다 **\<Order>** .</span><span class="sxs-lookup"><span data-stu-id="f0da3-146">The query uses the `child` axis in the predicate to find the parent of the **\<Order>** element.</span></span>  
  
```  
/child::Customer/child::Order[../@CustomerID="1"]  
```  
  
 <span data-ttu-id="f0da3-147">기본값은 `child` 축입니다.</span><span class="sxs-lookup"><span data-stu-id="f0da3-147">The `child` axis is the default axis.</span></span> <span data-ttu-id="f0da3-148">따라서 다음과 같이 쿼리를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f0da3-148">Therefore, the query can be specified as:</span></span>  
  
```  
/Customer/Order[../@CustomerID="1"]  
```  
  
 <span data-ttu-id="f0da3-149">이 XPath 쿼리는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="f0da3-149">The XPath query is equivalent to:</span></span>  
  
```  
/Customer[@CustomerID="1"]/Order.  
```  
  
> [!NOTE]  
>  <span data-ttu-id="f0da3-150">`/Order[../@CustomerID="1"]`의 부모가 없기 때문에 XPath 쿼리는 오류를 반환 합니다 **\<Order>** .</span><span class="sxs-lookup"><span data-stu-id="f0da3-150">The XPath query `/Order[../@CustomerID="1"]` will return an error because there is no parent of **\<Order>**.</span></span> <span data-ttu-id="f0da3-151">매핑 스키마에를 포함 하는 요소가 있을 수 있지만 XPath가 어떤 경우에도 **\<Order>** 시작 되지 않았습니다. 따라서 **\<Order>** 는 문서의 최상위 요소 형식으로 간주 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f0da3-151">Although there may be elements in the mapping schema that contain **\<Order>**, the XPath did not begin at any of them; consequently, **\<Order>** is considered to be the top-level element type in the document.</span></span>  
  
##### <a name="to-test-the-xpath-query-against-the-mapping-schema"></a><span data-ttu-id="f0da3-152">매핑 스키마에 대해 XPath 쿼리를 테스트하려면</span><span class="sxs-lookup"><span data-stu-id="f0da3-152">To test the XPath query against the mapping schema</span></span>  
  
1.  <span data-ttu-id="f0da3-153">[샘플 스키마 코드](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md) 를 복사 하 여 텍스트 파일에 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="f0da3-153">Copy the [sample schema code](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md) and paste it into a text file.</span></span> <span data-ttu-id="f0da3-154">파일을 SampleSchema1.xml로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="f0da3-154">Save the file as SampleSchema1.xml.</span></span>  
  
2.  <span data-ttu-id="f0da3-155">다음 템플릿(XPathAxesSampleC.xml)을 만들고 다음과 같은 디렉터리에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="f0da3-155">Create the following template (XPathAxesSampleC.xml) and save it in the directory where:</span></span>  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:xpath-query mapping-schema="SampleSchema1.xml">  
        /Customer/Order[../@CustomerID="1"]  
      </sql:xpath-query>  
    </ROOT>  
    ```  
  
     <span data-ttu-id="f0da3-156">매핑 스키마(SampleSchema1.xml)에 대해 지정된 디렉터리 경로는 템플릿이 저장된 디렉터리에 상대적입니다.</span><span class="sxs-lookup"><span data-stu-id="f0da3-156">The directory path specified for the mapping schema (SampleSchema1.xml) is relative to the directory where the template is saved.</span></span> <span data-ttu-id="f0da3-157">또한 다음과 같이 절대 경로를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f0da3-157">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\MyDir\SampleSchema1.xml"  
    ```  
  
3.  <span data-ttu-id="f0da3-158">SQLXML 4.0 테스트 스크립트(Sqlxml4test.vbs)를 만든 다음 이 스크립트를 사용하여 템플릿을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="f0da3-158">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="f0da3-159">자세한 내용은 [ADO를 사용 하 여 SQLXML 4.0 쿼리 실행](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f0da3-159">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="f0da3-160">다음은 템플릿 실행 결과 집합의 일부입니다.</span><span class="sxs-lookup"><span data-stu-id="f0da3-160">Here is the partial result set of the template execution:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Order SalesOrderID="Ord-43860" SalesPersonID="280"   
         OrderDate="2001-08-01T00:00:00"   
         DueDate="2001-08-13T00:00:00"   
         ShipDate="2001-08-08T00:00:00">  
  <OrderDetail ProductID="Prod-729" UnitPrice="226.8571"   
               OrderQty="1" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-732" UnitPrice="440.1742"   
               OrderQty="1" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-738" UnitPrice="220.2496"   
               OrderQty="1" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-753" UnitPrice="2576.3544"   
               OrderQty="2" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-756" UnitPrice="1049.7528"   
               OrderQty="1" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-758" UnitPrice="1049.7528"   
               OrderQty="2" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-761" UnitPrice="503.3507"   
               OrderQty="2" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-762" UnitPrice="503.3507"   
               OrderQty="1" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-763" UnitPrice="503.3507"   
               OrderQty="1" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-765" UnitPrice="503.3507"   
               OrderQty="2" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-768" UnitPrice="503.3507"   
               OrderQty="1" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-770" UnitPrice="503.3507"   
               OrderQty="1" UnitPriceDiscount="0" />   
  </Order>  
   ...  
</Order>  
</ROOT>  
```  
  
### <a name="d-specify-the-attribute-axis"></a><span data-ttu-id="f0da3-161">D.</span><span class="sxs-lookup"><span data-stu-id="f0da3-161">D.</span></span> <span data-ttu-id="f0da3-162">특성 축 지정</span><span class="sxs-lookup"><span data-stu-id="f0da3-162">Specify the attribute axis</span></span>  
 <span data-ttu-id="f0da3-163">다음 XPath 쿼리는 **\<Customer>** **CustomerID** 특성 값이 1 인 컨텍스트 노드의 모든 자식 요소를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="f0da3-163">The following XPath query selects all the **\<Customer>** child elements of the context node with a **CustomerID** attribute value of 1:</span></span>  
  
```  
/child::Customer[attribute::CustomerID="1"]  
```  
  
 <span data-ttu-id="f0da3-164">조건자에서는 `attribute::CustomerID` `attribute` 축이 고 `CustomerID` 는 노드 테스트입니다 ( `CustomerID` 이 노드가 **\<attribute>** 축에 대 한 주 노드인지 때문에 노드 테스트가 TRUE 인 경우 `attribute` ).</span><span class="sxs-lookup"><span data-stu-id="f0da3-164">In the predicate `attribute::CustomerID`, `attribute` is the axis and `CustomerID` is the node test (if `CustomerID` is an attribute the node test is TRUE, because the **\<attribute>** node is the primary node for the `attribute` axis).</span></span>  
  
 <span data-ttu-id="f0da3-165">`attribute` 축에 대한 바로 가기(@)를 지정할 수 있으며 `child` 축은 기본 축이므로 쿼리에서 생략할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f0da3-165">A shortcut to the `attribute` axis (@) can be specified, and because `child` is the default axis, it can be omitted from the query:</span></span>  
  
```  
/Customer[@CustomerID="1"]  
```  
  
##### <a name="to-test-the-xpath-query-against-the-mapping-schema"></a><span data-ttu-id="f0da3-166">매핑 스키마에 대해 XPath 쿼리를 테스트하려면</span><span class="sxs-lookup"><span data-stu-id="f0da3-166">To test the XPath query against the mapping schema</span></span>  
  
1.  <span data-ttu-id="f0da3-167">[샘플 스키마 코드](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md) 를 복사 하 여 텍스트 파일에 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="f0da3-167">Copy the [sample schema code](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md) and paste it into a text file.</span></span> <span data-ttu-id="f0da3-168">파일을 SampleSchema1.xml로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="f0da3-168">Save the file as SampleSchema1.xml.</span></span>  
  
2.  <span data-ttu-id="f0da3-169">다음 템플릿(XPathAxesSampleD.xml)을 만들어 SampleSchema1.xml이 저장된 디렉터리에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="f0da3-169">Create the following template (XPathAxesSampleD.xml) and save it in the directory where SampleSchema1.xml is saved.</span></span>  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:xpath-query mapping-schema="SampleSchema1.xml">  
        child::Customer[attribute::CustomerID="1"]  
      </sql:xpath-query>  
    </ROOT>  
    ```  
  
     <span data-ttu-id="f0da3-170">매핑 스키마(SampleSchema1.xml)에 대해 지정된 디렉터리 경로는 템플릿이 저장된 디렉터리에 상대적입니다.</span><span class="sxs-lookup"><span data-stu-id="f0da3-170">The directory path specified for the mapping schema (SampleSchema1.xml) is relative to the directory where the template is saved.</span></span> <span data-ttu-id="f0da3-171">또한 다음과 같이 절대 경로를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f0da3-171">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\MyDir\SampleSchema1.xml"  
    ```  
  
3.  <span data-ttu-id="f0da3-172">SQLXML 4.0 테스트 스크립트(Sqlxml4test.vbs)를 만든 다음 이 스크립트를 사용하여 템플릿을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="f0da3-172">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="f0da3-173">자세한 내용은 [ADO를 사용 하 여 SQLXML 4.0 쿼리 실행](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f0da3-173">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="f0da3-174">다음은 템플릿 실행 결과 집합의 일부입니다.</span><span class="sxs-lookup"><span data-stu-id="f0da3-174">Here is the partial result set of the template execution:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Customer CustomerID="1" SalesPersonID="280"   
            TerritoryID="1" AccountNumber="1"   
            CustomerType="S" Orders="Ord-43860 Ord-44501 Ord-45283 Ord-46042">  
    <Order SalesOrderID="Ord-43860" SalesPersonID="280"   
           OrderDate="2001-08-01T00:00:00"   
           DueDate="2001-08-13T00:00:00"   
           ShipDate="2001-08-08T00:00:00">  
       <OrderDetail ProductID="Prod-729" UnitPrice="226.8571"   
                    OrderQty="1" UnitPriceDiscount="0" />   
       <OrderDetail ProductID="Prod-732" UnitPrice="440.1742"   
                    OrderQty="1" UnitPriceDiscount="0" />   
       <OrderDetail ProductID="Prod-738" UnitPrice="220.2496"   
                    OrderQty="1" UnitPriceDiscount="0" />   
      ...   
    </Order>  
   ...  
  </Customer>  
</ROOT>  
```  
  
  
