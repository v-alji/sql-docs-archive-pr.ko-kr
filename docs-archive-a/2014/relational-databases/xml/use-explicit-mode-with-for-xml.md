---
title: FOR XML에서 EXPLICIT 모드 사용 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- EXPLICIT FOR XML mode
- FOR XML clause, EXPLICIT mode
- FOR XML EXPLICIT mode
ms.assetid: 8b26e8ce-5465-4e7a-b237-98d0f4578ab1
author: rothja
ms.author: jroth
ms.openlocfilehash: 7e3db80333c74166301fcff7bb25edea4aca38a2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649955"
---
# <a name="use-explicit-mode-with-for-xml"></a><span data-ttu-id="0c9c4-102">FOR XML에서 EXPLICIT 모드 사용</span><span class="sxs-lookup"><span data-stu-id="0c9c4-102">Use EXPLICIT Mode with FOR XML</span></span>
  <span data-ttu-id="0c9c4-103">[FOR XML을 사용하는 XML 생성](../xml/for-xml-sql-server.md)항목에 설명된 것과 같이 RAW 및 AUTO 모드에서는 쿼리 결과로 생성되는 XML의 모양을 상세하게 조정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0c9c4-103">As described in the topic, [Constructing XML Using FOR XML](../xml/for-xml-sql-server.md), RAW and AUTO mode do not provide much control over the shape of the XML generated from a query result.</span></span> <span data-ttu-id="0c9c4-104">하지만 EXPLICIT 모드에서는 쿼리 결과로 생성되는 XML의 모양을 좀 더 상세하게 조정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0c9c4-104">However, EXPLICIT mode provides the most flexibility in generating the XML you want from a query result.</span></span>  
  
 <span data-ttu-id="0c9c4-105">XML에 예상되는 중첩과 같은 필수 XML에 대한 추가 정보는 쿼리의 일부로 명시적으로 지정하는 방식으로 EXPLICIT 모드 쿼리를 작성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c9c4-105">The EXPLICIT mode query must be written in a specific way so that the additional information about the required XML, such as expected nesting in the XML, is explicitly specified as part of the query.</span></span> <span data-ttu-id="0c9c4-106">요청한 XML에 따라 EXPLICIT 모드 쿼리를 작성하는 작업은 복잡할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0c9c4-106">Depending on the XML you request, writing EXPLICIT mode queries can be cumbersome.</span></span> <span data-ttu-id="0c9c4-107">EXPLICIT 모드 쿼리를 작성하는 것보다는 [PATH 모드 사용](../xml/use-path-mode-with-for-xml.md) 의 설명에 따라 중첩을 사용하는 것이 더 간단합니다.</span><span class="sxs-lookup"><span data-stu-id="0c9c4-107">You may find that [Using PATH Mode](../xml/use-path-mode-with-for-xml.md) with nesting is a simpler alternative to writing EXPLICIT mode queries.</span></span>  
  
 <span data-ttu-id="0c9c4-108">EXPLICIT 모드에서 쿼리의 일부로 원하는 XML을 기술하기 때문에 생성된 XML은 형식이 올바르고 유효해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c9c4-108">Because you describe the XML you want as part of the query in EXPLICIT mode, you must ensure that the generated XML is well formed and valid.</span></span>  
  
## <a name="rowset-processing-in-explicit-mode"></a><span data-ttu-id="0c9c4-109">EXPLICIT 모드의 행 집합 처리</span><span class="sxs-lookup"><span data-stu-id="0c9c4-109">Rowset Processing in EXPLICIT Mode</span></span>  
 <span data-ttu-id="0c9c4-110">EXPLICIT 모드는 쿼리 실행으로부터 만들어지는 행 집합을 XML 문서로 변환합니다.</span><span class="sxs-lookup"><span data-stu-id="0c9c4-110">The EXPLICIT mode transforms the rowset that results from the query execution into an XML document.</span></span> <span data-ttu-id="0c9c4-111">EXPLICIT 모드의 경우 XML문서를 만들기 위해서는 행 집합이 특정 형식을 가져야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c9c4-111">In order for EXPLICIT mode to produce the XML document, the rowset must have a specific format.</span></span> <span data-ttu-id="0c9c4-112">이를 위해서는 처리 논리에서 원하는 XML을 생성할 수 있도록 특정 형식을 지닌 행 집합인 **범용 테이블**을 생성하는 SELECT 쿼리를 작성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c9c4-112">This requires that you write the SELECT query to produce the rowset, the **universal table**, with a specific format so the processing logic can then produce the XML you want.</span></span>  
  
 <span data-ttu-id="0c9c4-113">먼저 쿼리는 다음 두 메타데이터 열을 생성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c9c4-113">First, the query must produce the following two metadata columns:</span></span>  
  
-   <span data-ttu-id="0c9c4-114">첫 번째 열은 현재 요소에 대한 정수 형식의 태그 번호를 제공해야 하며 열 이름은 **Tag**여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c9c4-114">The first column must provide the tag number, integer type, of the current element, and the column name must be **Tag**.</span></span> <span data-ttu-id="0c9c4-115">쿼리에서는 행 집합으로부터 생성될 각 요소의 고유 태그 번호를 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c9c4-115">Your query must provide a unique tag number for each element that will be constructed from the rowset.</span></span>  
  
-   <span data-ttu-id="0c9c4-116">두 번째 열은 부모 요소의 태그 번호를 제공해야 하며 이 열 이름은 **Parent**여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c9c4-116">The second column must provide a tag number of the parent element, and this column name must be **Parent**.</span></span> <span data-ttu-id="0c9c4-117">이러한 빙식으로 Tag 및 Parent 열은 계층 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="0c9c4-117">In this way, the Tag and the Parent column provide hierarchy information.</span></span>  
  
 <span data-ttu-id="0c9c4-118">이러한 메타데이터 열 값은 열 이름의 정보와 함께 원하는 XML을 생성하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="0c9c4-118">These metadata column values, together with the information in the column names, are used to produce the XML you want.</span></span> <span data-ttu-id="0c9c4-119">쿼리에서는 특정 방식으로 열 이름을 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c9c4-119">Note that your query must provide column names in a specific way.</span></span> <span data-ttu-id="0c9c4-120">또한 **Parent** 열에 있는 0 또는 NULL은 해당 요소에 부모가 없음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="0c9c4-120">Also note that a 0 or NULL in the **Parent** column indicates that the corresponding element has no parent.</span></span> <span data-ttu-id="0c9c4-121">요소는 최상위 요소로 XML에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="0c9c4-121">The element is added to the XML as a top-level element.</span></span>  
  
 <span data-ttu-id="0c9c4-122">쿼리에 의해 생성된 범용 열이 XML 결과를 생성하도록 처리되는 방법을 이해하려면 이 범용 테이블을 생성하는 쿼리를 작성했다고 가정해 보십시오.</span><span class="sxs-lookup"><span data-stu-id="0c9c4-122">To understand how the universal table generated by a query is processed into generating XML result, assume that you have written a query that produces this universal table:</span></span>  
  
 <span data-ttu-id="0c9c4-123">![샘플 범용 테이블](../../database-engine/media/xmlutable.gif "샘플 범용 테이블")</span><span class="sxs-lookup"><span data-stu-id="0c9c4-123">![Sample universal table](../../database-engine/media/xmlutable.gif "Sample universal table")</span></span>  
  
 <span data-ttu-id="0c9c4-124">이 범용 테이블에 대해 다음 사항을 유의하십시오.</span><span class="sxs-lookup"><span data-stu-id="0c9c4-124">Note the following about this universal table:</span></span>  
  
-   <span data-ttu-id="0c9c4-125">처음 두 열은 **Tag** 및 **Parent** 이며 메타 열입니다.</span><span class="sxs-lookup"><span data-stu-id="0c9c4-125">The first two columns are **Tag** and **Parent** and are meta columns.</span></span> <span data-ttu-id="0c9c4-126">이러한 값은 계층을 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="0c9c4-126">These values determine the hierarchy.</span></span>  
  
-   <span data-ttu-id="0c9c4-127">열 이름은 이 항목의 후반에 설명된 바와 같은 특정 방식으로 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="0c9c4-127">The column names are specified in a certain way, as described later in this topic.</span></span>  
  
-   <span data-ttu-id="0c9c4-128">이 범용 테이블로부터 XML을 생성할 때 이 테이블의 데이터는 열 그룹으로 수직 분할됩니다.</span><span class="sxs-lookup"><span data-stu-id="0c9c4-128">In generating the XML from this universal table, the data in this table is partitioned vertically into column groups.</span></span> <span data-ttu-id="0c9c4-129">그룹화는 **Tag** 값 및 열 이름에 따라 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="0c9c4-129">The grouping is determined based on the **Tag** value and the column names.</span></span> <span data-ttu-id="0c9c4-130">XML을 생성할 때 처리 논리는 각 행에 대해 하나의 열 그룹을 선택하고 요소를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="0c9c4-130">In constructing XML, the processing logic selects one group of columns for each row and constructs an element.</span></span> <span data-ttu-id="0c9c4-131">이 예에서는 다음 사항이 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="0c9c4-131">The following applies in this example:</span></span>  
  
    -   <span data-ttu-id="0c9c4-132">첫 번째 행에 있는 **Tag** 열 값 1에 대해 이름에 동일한 태그 번호 **Customer!1!cid** 및 **Customer!1!name**이 포함된 열은 하나의 그룹을 형성합니다.</span><span class="sxs-lookup"><span data-stu-id="0c9c4-132">For **Tag** column value 1 in the first row, the columns whose names include the same tag number, **Customer!1!cid** and **Customer!1!name**, form a group.</span></span> <span data-ttu-id="0c9c4-133">이러한 열은 행을 처리하는 데 사용되며 생성된 요소의 모양은 <`Customer id=... name=...`>임을 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0c9c4-133">These columns are used in processing the row, and you may have noticed that the shape of the generated element is <`Customer id=... name=...`>.</span></span> <span data-ttu-id="0c9c4-134">열 이름 형식은 이 항목의 후반에 설명됩니다.</span><span class="sxs-lookup"><span data-stu-id="0c9c4-134">Column name format is described later in this topic.</span></span>  
  
    -   <span data-ttu-id="0c9c4-135">**Tag** 열 값이 2인 행에 대해 **Order!2!id** 및 **Order!2!date** 열은 이후에 <`Order id=... date=... /`> 요소를 생성하는 데 사용되는 그룹을 형성합니다.</span><span class="sxs-lookup"><span data-stu-id="0c9c4-135">For rows with **Tag** column value 2, columns **Order!2!id** and **Order!2!date** form a group that is then used in constructing elements, <`Order id=... date=... /`>.</span></span>  
  
    -   <span data-ttu-id="0c9c4-136">**Tag** 열 값이 3인 행에 대해 **OrderDetail!3!id!id** 및 **OrderDetail!3!pid!idref** 열은 그룹을 형성합니다.</span><span class="sxs-lookup"><span data-stu-id="0c9c4-136">For rows with **Tag** column value 3, columns **OrderDetail!3!id!id** and **OrderDetail!3!pid!idref** form a group.</span></span> <span data-ttu-id="0c9c4-137">이러한 각 행은 이러한 열로부터 <`OrderDetail id=... pid=...`> 요소를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="0c9c4-137">Each of these rows generates an element, <`OrderDetail id=... pid=...`>, from these columns.</span></span>  
  
-   <span data-ttu-id="0c9c4-138">XML 계층을 생성할 때 행은 순서대로 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="0c9c4-138">Note that in generating XML hierarchy, the rows are processed in order.</span></span> <span data-ttu-id="0c9c4-139">XML 계층은 다음과 같이 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="0c9c4-139">The XML hierarchy is determined as shown in the following:</span></span>  
  
    -   <span data-ttu-id="0c9c4-140">첫 번째 행은 **Tag** 값 1과 **Parent** 값 NULL을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="0c9c4-140">The first row specifies **Tag** value 1 and **Parent** value NULL.</span></span> <span data-ttu-id="0c9c4-141">따라서 해당 요소인 <`Customer`> 요소는 XML에서 최상위 요소로 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="0c9c4-141">Therefore, the corresponding element, <`Customer`> element, is added as a top-level element in the XML.</span></span>  
  
        ```  
        <Customer cid="C1" name="Janine">  
        ```  
  
    -   <span data-ttu-id="0c9c4-142">두 번째 행은 **Tag** 값 2와 **Parent** 값 1을 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="0c9c4-142">The second row identifies **Tag** value 2 and **Parent** value 1.</span></span> <span data-ttu-id="0c9c4-143">따라서 <`Order`> 요소는 <`Customer`> 요소의 자식으로 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="0c9c4-143">Therefore, the element, <`Order`> element, is added as a child of the <`Customer`> element.</span></span>  
  
        ```  
        <Customer cid="C1" name="Janine">  
           <Order id="O1" date="1/20/1996">  
        ```  
  
    -   <span data-ttu-id="0c9c4-144">다음 두 행은 **Tag** 값 3과 **Parent** 값 2를 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="0c9c4-144">The next two rows identify **Tag** value 3 and **Parent** value 2.</span></span> <span data-ttu-id="0c9c4-145">따라서 두 <`OrderDetail`> 요소는 <`Order`> 요소의 자식으로 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="0c9c4-145">Therefore, the two elements, <`OrderDetail`> elements, are added as children of the <`Order`> element.</span></span>  
  
        ```  
        <Customer cid="C1" name="Janine">  
           <Order id="O1" date="1/20/1996">  
              <OrderDetail id="OD1" pid="P1"/>  
              <OrderDetail id="OD2" pid="P2"/>  
        ```  
  
    -   <span data-ttu-id="0c9c4-146">마지막 행은 **Tag** 번호로 2를 식별하고 **Parent** 태그 번호로 1을 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="0c9c4-146">The last row identifies 2 as the **Tag** number and 1 as the **Parent** tag number.</span></span> <span data-ttu-id="0c9c4-147">따라서 다른 <`Order`> 요소 자식이 <`Customer`> 부모 요소에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="0c9c4-147">Therefore, another <`Order`> element child is added to the <`Customer`> parent element.</span></span>  
  
        ```  
        <Customer cid="C1" name="Janine">  
           <Order id="O1" date="1/20/1996">  
              <OrderDetail id="OD1" pid="P1"/>  
              <OrderDetail id="OD2" pid="P2"/>  
           </Order>  
           <Order id="O2" date="3/29/1997">  
        </Customer>  
        ```  
  
 <span data-ttu-id="0c9c4-148">요약하면 EXPLICIT 모드에서는 **Tag** 및 **Parent** 메타 열의 값과 열 이름에 제공된 정보 및 행의 올바른 순서로 원하는 XML이 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="0c9c4-148">To summarize, the values in the **Tag** and **Parent** meta columns, the information provided in the column names, and the correct ordering of the rows produce the XML you want when you use EXPLICIT mode.</span></span>  
  
### <a name="universal-table-row-ordering"></a><span data-ttu-id="0c9c4-149">범용 테이블 행 순서 지정</span><span class="sxs-lookup"><span data-stu-id="0c9c4-149">Universal Table Row Ordering</span></span>  
 <span data-ttu-id="0c9c4-150">XML을 생성할 때 범용 테이블의 행은 순서대로 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="0c9c4-150">In constructing the XML, the rows in the universal table are processed in order.</span></span> <span data-ttu-id="0c9c4-151">따라서 해당 부모와 연결된 올바른 자식 요소를 검색하려면 각 부모 노드 바로 다음에 해당 자식 노드가 오도록 행 집합의 행 순서를 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c9c4-151">Therefore, to retrieve the correct children instances associated with their parent, the rows in the rowset must be ordered so that each parent node is immediately followed by its children.</span></span>  
  
## <a name="specifying-column-names-in-a-universal-table"></a><span data-ttu-id="0c9c4-152">범용 테이블에 열 이름 지정</span><span class="sxs-lookup"><span data-stu-id="0c9c4-152">Specifying Column Names in a Universal Table</span></span>  
 <span data-ttu-id="0c9c4-153">EXPLICIT 모드 쿼리를 작성할 때 결과 행 집합에 있는 열 이름은 다음 형식에 따라 지정되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c9c4-153">When writing EXPLICIT mode queries, column names in the resulting rowset must be specified by using this format.</span></span> <span data-ttu-id="0c9c4-154">이러한 형식은 지시어를 사용하여 지정된 요소 및 특성 이름과 기타 추가 정보를 포함하는 변환 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="0c9c4-154">They provide transformation information including element and attribute names and other additional information, specified by using directives.</span></span>  
  
 <span data-ttu-id="0c9c4-155">일반 형식은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="0c9c4-155">This is the general format:</span></span>  
  
```  
  
ElementName!TagNumber!AttributeName!Directive  
```  
  
 <span data-ttu-id="0c9c4-156">다음은 형식의 각 부분에 대한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="0c9c4-156">Following is the description of the parts of the format.</span></span>  
  
 <span data-ttu-id="0c9c4-157">*ElementName*</span><span class="sxs-lookup"><span data-stu-id="0c9c4-157">*ElementName*</span></span>  
 <span data-ttu-id="0c9c4-158">요소의 일반적인 결과 식별자입니다.</span><span class="sxs-lookup"><span data-stu-id="0c9c4-158">Is the resulting generic identifier of the element.</span></span> <span data-ttu-id="0c9c4-159">예를 들어 **Customers**가 *ElementName*으로 지정된 경우 \<Customers> 요소가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="0c9c4-159">For example, if **Customers** is specified as *ElementName*, the \<Customers> element is generated.</span></span>  
  
 <span data-ttu-id="0c9c4-160">*TagNumber*</span><span class="sxs-lookup"><span data-stu-id="0c9c4-160">*TagNumber*</span></span>  
 <span data-ttu-id="0c9c4-161">요소에 할당된 고유 태그 값입니다.</span><span class="sxs-lookup"><span data-stu-id="0c9c4-161">Is a unique tag value assigned to an element.</span></span> <span data-ttu-id="0c9c4-162">이 값은 두 메타데이터 열인 **Tag** 및 **Parent**를 통해 결과 XML에서의 요소 중첩을 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="0c9c4-162">This value, with the help of the two metadata columns, **Tag** and **Parent**, determines the nesting of the elements in the resulting XML.</span></span>  
  
 <span data-ttu-id="0c9c4-163">*AttributeName*</span><span class="sxs-lookup"><span data-stu-id="0c9c4-163">*AttributeName*</span></span>  
 <span data-ttu-id="0c9c4-164">지정된 *ElementName*을 생성하기 위해 특성 이름을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="0c9c4-164">Provides the name of the attribute to construct in the specified *ElementName*.</span></span> <span data-ttu-id="0c9c4-165">이 동작은 *Directive* 가 지정되지 않은 경우의 동작입니다.</span><span class="sxs-lookup"><span data-stu-id="0c9c4-165">This is the behavior if *Directive* is not specified.</span></span>  
  
 <span data-ttu-id="0c9c4-166">*Directive* 가 지정되어 있고 **xml**, **cdata**또는 **element**인 경우 이 값은 *ElementName*의 요소 자식을 생성하는 데 사용되고 열 값이 여기에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="0c9c4-166">If *Directive* is specified and it is **xml**, **cdata**, or **element**, this value is used to construct an element child of *ElementName*, and the column value is added to it.</span></span>  
  
 <span data-ttu-id="0c9c4-167">*Directive*를 지정하면 *AttributeName* 을 비워 둘 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0c9c4-167">If you specify the *Directive*, the *AttributeName* can be empty.</span></span> <span data-ttu-id="0c9c4-168">예를 들면 ElementName!TagNumber!!Directive와 같습니다.</span><span class="sxs-lookup"><span data-stu-id="0c9c4-168">For example, ElementName!TagNumber!!Directive.</span></span> <span data-ttu-id="0c9c4-169">이 경우 열 값은 *ElementName*에 직접 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="0c9c4-169">In this case, the column value is directly contained by the *ElementName*.</span></span>  
  
 <span data-ttu-id="0c9c4-170">*Directive*</span><span class="sxs-lookup"><span data-stu-id="0c9c4-170">*Directive*</span></span>  
 <span data-ttu-id="0c9c4-171">*Directive* 는 선택 항목으로서 XML 생성을 위한 추가 정보를 제공하는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0c9c4-171">*Directive* is optional and you can use it to provide additional information for construction of the XML.</span></span> <span data-ttu-id="0c9c4-172">*Directive* 에는 두 가지 용도가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0c9c4-172">*Directive* has two purposes.</span></span>  
  
 <span data-ttu-id="0c9c4-173">하나는 값을 ID, IDREF 및 IDREFS로 인코딩하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="0c9c4-173">One of the purposes is to encode values as ID, IDREF, and IDREFS.</span></span> <span data-ttu-id="0c9c4-174">**ID**, **IDREF**및 **IDREFS** 키워드를 *Directive*로 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0c9c4-174">You can specify **ID**, **IDREF**, and **IDREFS** keywords as *Directives*.</span></span> <span data-ttu-id="0c9c4-175">이러한 지시어는 특성 유형을 덮어씁니다.</span><span class="sxs-lookup"><span data-stu-id="0c9c4-175">These directives overwrite the attribute types.</span></span> <span data-ttu-id="0c9c4-176">이렇게 하면 문서 간 연결을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0c9c4-176">This allows you to create intra-document links.</span></span>  
  
 <span data-ttu-id="0c9c4-177">또한 *Directive* 를 사용하여 문자열 데이터를 XML로 매핑하는 방법을 나타낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0c9c4-177">Also, you can use *Directive* to indicate how to map the string data to XML.</span></span> <span data-ttu-id="0c9c4-178">**hide**, **element, elementxsinil**, **xml**, **xmltext**및 **cdata** 키워드는 *Directive*로 사용될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0c9c4-178">The **hide**, **element, elementxsinil**, **xml**, **xmltext**, and **cdata** keywords can be used as the *Directive*.</span></span> <span data-ttu-id="0c9c4-179">**hide** 지시어는 노드를 숨깁니다.</span><span class="sxs-lookup"><span data-stu-id="0c9c4-179">The **hide** directive hides the node.</span></span> <span data-ttu-id="0c9c4-180">이 키워드는 정렬 목적으로만 값을 검색하고 결과 XML에는 표시되지 않도록 하려는 경우에 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="0c9c4-180">This is useful when you retrieve values only for sorting purposes, but you do not want them in the resulting XML.</span></span>  
  
 <span data-ttu-id="0c9c4-181">**element** 지시어는 특성 대신 포함된 요소를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="0c9c4-181">The **element** directive generates a contained element instead of an attribute.</span></span> <span data-ttu-id="0c9c4-182">포함된 데이터는 엔터티로 인코딩됩니다.</span><span class="sxs-lookup"><span data-stu-id="0c9c4-182">The contained data is encoded as an entity.</span></span> <span data-ttu-id="0c9c4-183">예를 들어 **<** 문자는 &lt;가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0c9c4-183">For example, the **<** character becomes &lt;.</span></span> <span data-ttu-id="0c9c4-184">NULL 열 값에 대해 경우 요소가 생성되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0c9c4-184">For NULL column values, no element is generated.</span></span> <span data-ttu-id="0c9c4-185">Null 열 값에 대해 요소를 생성하려면 **elementxsinil** 지시어를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="0c9c4-185">If you want an element generated for null column values, you can specify the **elementxsinil** directive.</span></span> <span data-ttu-id="0c9c4-186">이렇게 하면 특성이 xsi:nil=TRUE인 요소가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="0c9c4-186">This will generate an element that has the attribute xsi:nil=TRUE.</span></span>  
  
 <span data-ttu-id="0c9c4-187">**xml** 지시어는 **element** 지시어와 비슷하지만 엔터티 인코딩이 발생하지 않는다는 점이 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="0c9c4-187">The **xml** directive is the same as an **element** directive, except that no entity encoding occurs.</span></span> <span data-ttu-id="0c9c4-188">**element** 지시어는 **ID**, **IDREF**또는 **IDREFS**와 조합될 수 있지만 **xml** 지시어는 **hide**를 제외한 다른 지시어와는 조합될 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0c9c4-188">Note that the **element** directive can be combined with **ID**, **IDREF**, or **IDREFS**, whereas the **xml** directive is not allowed with any other directive, except **hide**.</span></span>  
  
 <span data-ttu-id="0c9c4-189">**cdata** 지시어는 CDATA 섹션으로 데이터를 묶어서 포함시킵니다.</span><span class="sxs-lookup"><span data-stu-id="0c9c4-189">The **cdata** directive contains the data by wrapping it with a CDATA section.</span></span> <span data-ttu-id="0c9c4-190">내용은 인코딩된 엔터티가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="0c9c4-190">The content is not entity encoded.</span></span> <span data-ttu-id="0c9c4-191">원래 데이터 형식은 **varchar**, **nvarchar**, **text**또는 **ntext**와 같은 텍스트 유형이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c9c4-191">The original data type must be a text type such as **varchar**, **nvarchar**, **text**, or **ntext**.</span></span> <span data-ttu-id="0c9c4-192">이 지시어와 함께 사용할 수 있는 것은 **hide**뿐입니다.</span><span class="sxs-lookup"><span data-stu-id="0c9c4-192">This directive can be used only with **hide**.</span></span> <span data-ttu-id="0c9c4-193">이 지시어를 사용할 때는 *AttributeName* 을 지정하지 말아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c9c4-193">When this directive is used, *AttributeName* must not be specified.</span></span>  
  
 <span data-ttu-id="0c9c4-194">이러한 두 그룹 간 지시어 조합은 대부분의 경우 허용되지만 자체 그룹에서 지시어를 조합하는 것은 허용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0c9c4-194">Combining directives between these two groups is allowed in most cases, but combining them among themselves is not allowed.</span></span>  
  
 <span data-ttu-id="0c9c4-195">*Customer!1* 과 같은 *Directive* 및 **AttributeName**이 지정되지 않은 경우 **Customer!1!!element** 와 같은 **element**지시어가 내포되고 열 데이터가 *ElementName*에 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="0c9c4-195">If the *Directive* and the *AttributeName* is not specified, for example, **Customer!1**, an **element** directive is implied, such as **Customer!1!!element**, and column data is contained in the *ElementName*.</span></span>  
  
 <span data-ttu-id="0c9c4-196">**xmltext** 지시어가 지정된 경우 열 내용은 문서의 나머지 부분에 통합된 단일 태그로 묶입니다.</span><span class="sxs-lookup"><span data-stu-id="0c9c4-196">If the **xmltext** directive is specified, the column content is wrapped in a single tag that is integrated with the rest of the document.</span></span> <span data-ttu-id="0c9c4-197">이 지시어는 OPENXML에 의해 열에 저장된 사용되지 않은 오버플로 XML 데이터를 인출하는 데 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="0c9c4-197">This directive is useful in fetching overflow, unconsumed, XML data stored in a column by OPENXML.</span></span> <span data-ttu-id="0c9c4-198">자세한 내용은 [OPENXML&#40;SQL Server&#41;](../xml/openxml-sql-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0c9c4-198">For more information, see [OPENXML &#40;SQL Server&#41;](../xml/openxml-sql-server.md).</span></span>  
  
 <span data-ttu-id="0c9c4-199">*AttributeName* 이 지정된 경우 태그 이름이 지정된 이름으로 바뀝니다.</span><span class="sxs-lookup"><span data-stu-id="0c9c4-199">If *AttributeName* is specified, the tag name is replaced by the specified name.</span></span> <span data-ttu-id="0c9c4-200">그렇지 않으면 엔터티 인코딩 없이 포함 내용의 시작 위치에 내용을 배치하여 묶는 요소의 현재 특성 목록에 특성이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="0c9c4-200">Otherwise, the attribute is appended to the current list of attributes of the enclosing elements by putting the content at the beginning of the containment without entity encoding.</span></span> <span data-ttu-id="0c9c4-201">이 지시어가 있는 열은 **varchar**, **nvarchar**, **char**, **nchar**, **text**또는 **ntext**와 같은 텍스트 유형이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c9c4-201">The column with this directive must be a text type, such as **varchar**, **nvarchar**, **char**, **nchar**, **text**, or **ntext**.</span></span> <span data-ttu-id="0c9c4-202">이 지시어와 함께 사용할 수 있는 것은 **hide**뿐입니다.</span><span class="sxs-lookup"><span data-stu-id="0c9c4-202">This directive can be used only with **hide**.</span></span> <span data-ttu-id="0c9c4-203">이 지시어는 열에 저장된 오버플로 데이터를 인출하는 데 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="0c9c4-203">This directive is useful in fetching overflow data stored in a column.</span></span> <span data-ttu-id="0c9c4-204">내용이 잘 작성된 XML이 아니면 동작이 정의되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0c9c4-204">If the content is not a well-formed XML, the behavior is undefined.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0c9c4-205">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="0c9c4-205">In This Section</span></span>  
 <span data-ttu-id="0c9c4-206">다음 예에서는 EXPLICIT 모드를 사용하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="0c9c4-206">The following examples illustrate the use of EXPLICIT mode.</span></span>  
  
-   [<span data-ttu-id="0c9c4-207">예: 직원 정보 검색</span><span class="sxs-lookup"><span data-stu-id="0c9c4-207">Example: Retrieving Employee Information</span></span>](../xml/example-retrieving-employee-information.md)  
  
-   [<span data-ttu-id="0c9c4-208">예: ELEMENT 지시어 지정</span><span class="sxs-lookup"><span data-stu-id="0c9c4-208">Example: Specifying the ELEMENT Directive</span></span>](../xml/example-specifying-the-element-directive.md)  
  
-   [<span data-ttu-id="0c9c4-209">예: ELEMENTXSINIL 지시어 지정</span><span class="sxs-lookup"><span data-stu-id="0c9c4-209">Example: Specifying the ELEMENTXSINIL Directive</span></span>](../xml/example-specifying-the-elementxsinil-directive.md)  
  
-   [<span data-ttu-id="0c9c4-210">예: EXPLICIT 모드를 사용하여 형제 구성</span><span class="sxs-lookup"><span data-stu-id="0c9c4-210">Example: Constructing Siblings with EXPLICIT Mode</span></span>](../xml/example-constructing-siblings-with-explicit-mode.md)  
  
-   [<span data-ttu-id="0c9c4-211">예: ID 및 IDREF 지시어 지정</span><span class="sxs-lookup"><span data-stu-id="0c9c4-211">Example: Specifying the ID and IDREF Directives</span></span>](../xml/example-specifying-the-id-and-idref-directives.md)  
  
-   [<span data-ttu-id="0c9c4-212">예: ID 및 IDREFS 지시어 지정</span><span class="sxs-lookup"><span data-stu-id="0c9c4-212">Example: Specifying the ID and IDREFS Directives</span></span>](../xml/example-specifying-the-id-and-idrefs-directives.md)  
  
-   [<span data-ttu-id="0c9c4-213">예: HIDE 지시어 지정</span><span class="sxs-lookup"><span data-stu-id="0c9c4-213">Example: Specifying the HIDE Directive</span></span>](../xml/example-specifying-the-hide-directive.md)  
  
-   [<span data-ttu-id="0c9c4-214">예: ELEMENT 지시어 및 엔터티 인코딩 지정</span><span class="sxs-lookup"><span data-stu-id="0c9c4-214">Example: Specifying the ELEMENT Directive and Entity Encoding</span></span>](../xml/example-specifying-the-element-directive-and-entity-encoding.md)  
  
-   [<span data-ttu-id="0c9c4-215">예: CDATA 지시어 지정</span><span class="sxs-lookup"><span data-stu-id="0c9c4-215">Example: Specifying the CDATA Directive</span></span>](../xml/example-specifying-the-cdata-directive.md)  
  
-   [<span data-ttu-id="0c9c4-216">예: XMLTEXT 지시어 지정</span><span class="sxs-lookup"><span data-stu-id="0c9c4-216">Example: Specifying the XMLTEXT Directive</span></span>](../xml/example-specifying-the-xmltext-directive.md)  
  
## <a name="see-also"></a><span data-ttu-id="0c9c4-217">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0c9c4-217">See Also</span></span>  
 <span data-ttu-id="0c9c4-218">[FOR XML에서 RAW 모드 사용](../xml/use-raw-mode-with-for-xml.md) </span><span class="sxs-lookup"><span data-stu-id="0c9c4-218">[Use RAW Mode with FOR XML](../xml/use-raw-mode-with-for-xml.md) </span></span>  
 <span data-ttu-id="0c9c4-219">[FOR XML에서 AUTO 모드 사용](../xml/use-auto-mode-with-for-xml.md) </span><span class="sxs-lookup"><span data-stu-id="0c9c4-219">[Use AUTO Mode with FOR XML](../xml/use-auto-mode-with-for-xml.md) </span></span>  
 <span data-ttu-id="0c9c4-220">[FOR XML에서 PATH 모드 사용](../xml/use-path-mode-with-for-xml.md) </span><span class="sxs-lookup"><span data-stu-id="0c9c4-220">[Use PATH Mode with FOR XML](../xml/use-path-mode-with-for-xml.md) </span></span>  
 <span data-ttu-id="0c9c4-221">[SELECT&#40;Transact-SQL&#41;](/sql/t-sql/queries/select-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="0c9c4-221">[SELECT &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-transact-sql) </span></span>  
 [<span data-ttu-id="0c9c4-222">FOR XML&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="0c9c4-222">FOR XML &#40;SQL Server&#41;</span></span>](../xml/for-xml-sql-server.md)  
  
  
