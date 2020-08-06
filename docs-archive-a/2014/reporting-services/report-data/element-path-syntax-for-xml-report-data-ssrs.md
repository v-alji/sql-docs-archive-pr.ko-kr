---
title: XML 보고서 데이터를 위한 요소 경로 구문(SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- ElementPath syntax
- XML [Reporting Services], data retrieval
ms.assetid: 07bd7a4e-fd7a-4a72-9344-3258f7c286d1
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b7d66b39761dc278abff25a3b22ccd18ca74272b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742880"
---
# <a name="element-path-syntax-for-xml-report-data-ssrs"></a><span data-ttu-id="aa0c2-102">XML 보고서 데이터를 위한 요소 경로 구문(SSRS)</span><span class="sxs-lookup"><span data-stu-id="aa0c2-102">Element Path Syntax for XML Report Data (SSRS)</span></span>
  <span data-ttu-id="aa0c2-103">보고서 디자이너에서 대/소문자 구분 요소 경로를 정의하여 XML 데이터 원본에서 보고서에 사용할 데이터를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa0c2-103">In Report Designer, you specify the data to use for a report from an XML data source by defining a case-sensitive element path.</span></span> <span data-ttu-id="aa0c2-104">요소 경로는 XML 데이터 원본의 XML 계층 노드와 해당 특성으로 이동하는 방법을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="aa0c2-104">An element path indicates how to traverse the XML hierarchical nodes and their attributes in the XML data source.</span></span> <span data-ttu-id="aa0c2-105">기본 요소 경로를 사용하려면 데이터 세트 쿼리나 XML `ElementPath`의 XML `Query`를 비워 둡니다.</span><span class="sxs-lookup"><span data-stu-id="aa0c2-105">To use the default element path, leave the dataset query or the XML `ElementPath` of the XML `Query` empty.</span></span> <span data-ttu-id="aa0c2-106">XML 데이터 원본에서 데이터가 검색될 때 텍스트 값이 있는 요소 노드와 요소 노드 특성은 결과 집합의 열이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="aa0c2-106">When data is retrieved from the XML data source, element nodes that have text values and element node attributes become columns in the result set.</span></span> <span data-ttu-id="aa0c2-107">쿼리를 실행하면 노드 및 특성 값은 행 데이터가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="aa0c2-107">The values of the nodes and attributes become the row data when you run the query.</span></span> <span data-ttu-id="aa0c2-108">열은 보고서 데이터 창에 데이터 세트 필드 컬렉션으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="aa0c2-108">The columns appear as the dataset field collection in the Report Data pane.</span></span> <span data-ttu-id="aa0c2-109">이 항목에서는 요소 경로 구문을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="aa0c2-109">This topic describes the element path syntax.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="aa0c2-110">요소 경로 구문은 네임스페이스로부터 독립적입니다.</span><span class="sxs-lookup"><span data-stu-id="aa0c2-110">Element path syntax is namespace-independent.</span></span> <span data-ttu-id="aa0c2-111">요소 경로에 네임 스페이스를 사용 하려면 xml `ElementPath` [보고서 데이터에 대 한 Xml 쿼리 구문 ](report-data-ssrs.md)에 설명 된 xml 요소를 포함 하는 xml 쿼리 구문을 사용 하 여 SSRS&#41;&#40;합니다.</span><span class="sxs-lookup"><span data-stu-id="aa0c2-111">To use namespaces in an element path, use the XML query syntax that includes an XML `ElementPath` element described in [XML Query Syntax for XML Report Data &#40;SSRS&#41;](report-data-ssrs.md).</span></span>  
  
 <span data-ttu-id="aa0c2-112">다음 표에서는 요소 경로를 정의하는 데 사용되는 규칙을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="aa0c2-112">The following table describes conventions used to define an element path.</span></span>  
  
|<span data-ttu-id="aa0c2-113">규칙</span><span class="sxs-lookup"><span data-stu-id="aa0c2-113">Convention</span></span>|<span data-ttu-id="aa0c2-114">사용 대상</span><span class="sxs-lookup"><span data-stu-id="aa0c2-114">Used for</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="aa0c2-115">**굵게**</span><span class="sxs-lookup"><span data-stu-id="aa0c2-115">**bold**</span></span>|<span data-ttu-id="aa0c2-116">표시된 대로 입력해야 하는 텍스트입니다.</span><span class="sxs-lookup"><span data-stu-id="aa0c2-116">Text that must be typed exactly as shown.</span></span>|  
|<span data-ttu-id="aa0c2-117">&#124; (세로줄)</span><span class="sxs-lookup"><span data-stu-id="aa0c2-117">&#124; (vertical bar)</span></span>|<span data-ttu-id="aa0c2-118">각 구문 항목을 구분합니다.</span><span class="sxs-lookup"><span data-stu-id="aa0c2-118">Separates syntax items.</span></span> <span data-ttu-id="aa0c2-119">항목 중 하나만 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa0c2-119">You can choose only one of the items.</span></span>|  
|`[ ] (brackets)`|<span data-ttu-id="aa0c2-120">선택적 구문 항목입니다.</span><span class="sxs-lookup"><span data-stu-id="aa0c2-120">Optional syntax items.</span></span> <span data-ttu-id="aa0c2-121">대괄호는 입력하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="aa0c2-121">Do not type the brackets.</span></span>|  
|<span data-ttu-id="aa0c2-122">**{}** (중괄호)</span><span class="sxs-lookup"><span data-stu-id="aa0c2-122">**{ }** (braces)</span></span>|<span data-ttu-id="aa0c2-123">구문 항목의 매개 변수 범위를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="aa0c2-123">Delimits parameters of syntax items.</span></span>|  
|<span data-ttu-id="aa0c2-124">[ **,** ...*n*]</span><span class="sxs-lookup"><span data-stu-id="aa0c2-124">[**,**...*n*]</span></span>|<span data-ttu-id="aa0c2-125">앞의 항목이 *n* 번 반복될 수 있음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="aa0c2-125">Indicates the preceding item can be repeated *n* number of times.</span></span> <span data-ttu-id="aa0c2-126">각 항목은 쉼표로 구분됩니다.</span><span class="sxs-lookup"><span data-stu-id="aa0c2-126">The occurrences are separated by commas.</span></span>|  
  
## <a name="syntax"></a><span data-ttu-id="aa0c2-127">구문</span><span class="sxs-lookup"><span data-stu-id="aa0c2-127">Syntax</span></span>  
  
```  
  
Element path ::=  
    ElementNode[/Element path]  
ElementNode ::=  
    XMLName[(Encoding)][{[FieldList]}]  
XMLName ::=  
    [NamespacePrefix:]XMLLocalName  
Encoding ::=  
        HTMLEncoded | Base64Encoded  
FieldList ::=  
    Field[,FieldList]  
Field ::=  
    Attribute | Value | Element | ElementNode  
Attribute ::=  
        @XMLName[(Type)]  
Value ::=  
        @[(Type)]  
Element ::=  
    XMLName[(Type)]  
Type ::=  
        String | Integer | Boolean | Float | Decimal | Date | XML   
NamespacePrefix ::=  
    Identifier that specifies the namespace.  
XMLLocalName :: =  
    Identifier in the XML tag.   
```  
  
## <a name="remarks"></a><span data-ttu-id="aa0c2-128">설명</span><span class="sxs-lookup"><span data-stu-id="aa0c2-128">Remarks</span></span>  
 <span data-ttu-id="aa0c2-129">다음 표에는 요소 경로에서 사용되는 용어가 요약되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa0c2-129">The following table summarizes element path terms.</span></span> <span data-ttu-id="aa0c2-130">이 표의 예에서는 XML 문서 예인 Customers.xml을 참조하며 이 문서는 이 항목의 예 섹션에 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa0c2-130">Examples in the table refer to the example XML document Customers.xml, which is included in the Examples section of this topic.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="aa0c2-131">XML 태그는 대/소문자를 구분합니다.</span><span class="sxs-lookup"><span data-stu-id="aa0c2-131">XML tags are case-sensitive.</span></span> <span data-ttu-id="aa0c2-132">요소 경로에 ElementNode를 지정할 경우 데이터 원본의 XML 태그와 일치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="aa0c2-132">When you specify an ElementNode in the element path, you must exactly match the XML tags in the data source.</span></span>  
  
|<span data-ttu-id="aa0c2-133">용어</span><span class="sxs-lookup"><span data-stu-id="aa0c2-133">Term</span></span>|<span data-ttu-id="aa0c2-134">정의</span><span class="sxs-lookup"><span data-stu-id="aa0c2-134">Definition</span></span>|  
|----------|----------------|  
|<span data-ttu-id="aa0c2-135">요소 경로</span><span class="sxs-lookup"><span data-stu-id="aa0c2-135">Element path</span></span>|<span data-ttu-id="aa0c2-136">XML 데이터 원본을 사용하여 데이터 세트의 필드 데이터를 검색하기 위해 XML 문서 내에서 이동할 노드 시퀀스를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="aa0c2-136">Defines the sequence of nodes to traverse within the XML document in order to retrieve field data for a dataset with an XML data source.</span></span>|  
|`ElementNode`|<span data-ttu-id="aa0c2-137">XML 문서의 XML 노드입니다.</span><span class="sxs-lookup"><span data-stu-id="aa0c2-137">The XML node in the XML document.</span></span> <span data-ttu-id="aa0c2-138">노드는 태그로 지정되며 다른 노드와 계층 관계에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa0c2-138">Nodes are designated by tags and exist in a hierarchical relationship with other nodes.</span></span> <span data-ttu-id="aa0c2-139">예를 들어 \<Customers> 는 루트 요소 노드입니다.</span><span class="sxs-lookup"><span data-stu-id="aa0c2-139">For example, \<Customers> is the root element node.</span></span> <span data-ttu-id="aa0c2-140">\<Customer>는의 하위 요소입니다 \<Customers> .</span><span class="sxs-lookup"><span data-stu-id="aa0c2-140">\<Customer> is a subelement of \<Customers>.</span></span>|  
|`XMLName`|<span data-ttu-id="aa0c2-141">노드의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="aa0c2-141">The name of the node.</span></span> <span data-ttu-id="aa0c2-142">예를 들어 Customers 노드의 이름은 Customers입니다.</span><span class="sxs-lookup"><span data-stu-id="aa0c2-142">For example, the name of the Customers node is Customers.</span></span> <span data-ttu-id="aa0c2-143">`XMLName`에 네임스페이스 식별자를 접두사로 사용하면 모든 노드에 고유 이름을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa0c2-143">An `XMLName` can be prefixed with a namespace identifier to uniquely name every node.</span></span>|  
|`Encoding`|<span data-ttu-id="aa0c2-144">이 요소에 대한 `Value`가 인코딩된 XML이므로 이 값을 디코딩하여 이 요소의 하위 요소로 포함해야 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="aa0c2-144">Indicates that the `Value` for this element is encoded XML and needs to be decoded and included as a subelement of this element.</span></span>|  
|`FieldList`|<span data-ttu-id="aa0c2-145">데이터를 검색하는 데 사용할 요소 및 특성 집합을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="aa0c2-145">Defines the set of elements and attributes to use to retrieve data.</span></span><br /><br /> <span data-ttu-id="aa0c2-146">지정하지 않으면 모든 특성 및 하위 요소가 필드로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="aa0c2-146">If not specified, all attributes and subelements are used as fields.</span></span> <span data-ttu-id="aa0c2-147">빈 필드 목록이 지정 된 경우 ( **{}** )이 노드의 필드는 사용 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="aa0c2-147">If the empty field list is specified (**{}**), no fields from this node are used.</span></span><br /><br /> <span data-ttu-id="aa0c2-148">`FieldList`에 `Value`와 `Element` 또는 `ElementNode`가 모두 포함될 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="aa0c2-148">A `FieldList` may not contain both a `Value` and an `Element` or `ElementNode`.</span></span>|  
|`Field`|<span data-ttu-id="aa0c2-149">데이터 세트 필드로 검색되는 데이터를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="aa0c2-149">Specifies the data that is retrieved as a dataset field.</span></span>|  
|`Attribute`|<span data-ttu-id="aa0c2-150">`ElementNode` 내의 이름-값 쌍입니다.</span><span class="sxs-lookup"><span data-stu-id="aa0c2-150">A name-value pair within the `ElementNode`.</span></span> <span data-ttu-id="aa0c2-151">예를 들어 요소 노드에서 \<Customer ID="1"> `ID` 는 특성이 고는 `@ID(Integer)` 해당 데이터 필드에 정수 형식으로 "1"을 반환 `ID` 합니다.</span><span class="sxs-lookup"><span data-stu-id="aa0c2-151">For example, in the element node \<Customer ID="1">, `ID` is an attribute and `@ID(Integer)` returns "1" as an integer type in the corresponding data field `ID`.</span></span>|  
|`Value`|<span data-ttu-id="aa0c2-152">요소의 값입니다.</span><span class="sxs-lookup"><span data-stu-id="aa0c2-152">The value of the element.</span></span> <span data-ttu-id="aa0c2-153">`Value`는 요소 경로의 마지막 `ElementNode`에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa0c2-153">`Value` can only be used on the last `ElementNode` in the element path.</span></span> <span data-ttu-id="aa0c2-154">예를 들어 \<Return> 은 리프 노드 이므로 요소 경로의 끝에이 노드를 포함 하는 경우의 값 `Return {@}` 은입니다 `Chair` .</span><span class="sxs-lookup"><span data-stu-id="aa0c2-154">For example, because \<Return> is a leaf node, if you include it at the end of an element path, the value of `Return {@}` is `Chair`.</span></span>|  
|`Element`|<span data-ttu-id="aa0c2-155">명명된 하위 요소의 값입니다.</span><span class="sxs-lookup"><span data-stu-id="aa0c2-155">The value of the named subelement.</span></span> <span data-ttu-id="aa0c2-156">예를 들어 Customers {}/Customer {}/LastName은 LastName 요소에 대한 값만 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="aa0c2-156">For example, Customers {}/Customer {}/LastName retrieves values for only the LastName element.</span></span>|  
|`Type`|<span data-ttu-id="aa0c2-157">이 요소에서 만든 필드에 사용할 선택적 데이터 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="aa0c2-157">The optional data type to use for the field created from this element.</span></span>|  
|`NamespacePrefix`|<span data-ttu-id="aa0c2-158">`NamespacePrefix`는 XML 쿼리 요소에 정의되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa0c2-158">`NamespacePrefix` is defined in the XML Query element.</span></span> <span data-ttu-id="aa0c2-159">XML 쿼리 요소가 없으면 XML `ElementPath`의 네임스페이스가 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="aa0c2-159">If no XML Query element exists, namespaces in the XML `ElementPath` are ignored.</span></span> <span data-ttu-id="aa0c2-160">XML 쿼리 요소가 있으면 XML `ElementPath`에 선택적 특성 `IgnoreNamespaces`가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="aa0c2-160">If there is an XML Query element, the XML `ElementPath` has an optional attribute `IgnoreNamespaces`.</span></span> <span data-ttu-id="aa0c2-161">IgnoreNamespaces가 이면 `true` xml `ElementPath` 및 xml 문서의 네임 스페이스가 무시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="aa0c2-161">If IgnoreNamespaces is `true`, namespaces in the XML `ElementPath` and the XML document are ignored.</span></span> <span data-ttu-id="aa0c2-162">자세한 내용은 [XML 보고서 데이터를 위한 XML 쿼리 구문&#40;SSRS&#41;](report-data-ssrs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="aa0c2-162">For more information, see [XML Query Syntax for XML Report Data &#40;SSRS&#41;](report-data-ssrs.md).</span></span>|  
  
## <a name="example---no-namespaces"></a><span data-ttu-id="aa0c2-163">예 - 네임스페이스가 없는 경우</span><span class="sxs-lookup"><span data-stu-id="aa0c2-163">Example - No Namespaces</span></span>  
 <span data-ttu-id="aa0c2-164">다음 예에서는 XML 문서 Customers.xml을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="aa0c2-164">The following examples use the XML document Customers.xml.</span></span> <span data-ttu-id="aa0c2-165">이 표에서는 요소 경로 구문의 예를 보여 주고 XML 문서를 기본 데이터 원본으로 하여 데이터 세트를 정의하는 쿼리에 해당 요소 경로를 사용한 결과를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="aa0c2-165">This table shows examples of element path syntax and the results of using the element path in a query that defines a dataset, based on the XML document as a data source.</span></span>  
  
 <span data-ttu-id="aa0c2-166">요소 경로가 비어 있으면 쿼리는 기본 요소 경로인 리프 노드 컬렉션에 대 한 첫 번째 경로를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="aa0c2-166">Note that when the element path is empty, the query uses the default element path: the first path to a leaf node collection.</span></span> <span data-ttu-id="aa0c2-167">첫 번째 예에서 요소 경로를 비워 둔 것은 /Customers/Customer/Orders/Order 요소 경로를 지정한 것과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="aa0c2-167">In the first example, leaving the element path empty is equivalent to specifying the element path /Customers/Customer/Orders/Order.</span></span> <span data-ttu-id="aa0c2-168">경로와 함께 모든 노드 값과 특성이 결과 세트에 반환되고 노드 이름과 특성 이름은 데이터 세트 필드로 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="aa0c2-168">All node value and attributes along the path are returned in the result set, and the node names and attributes names appear as dataset fields.</span></span>  
  
-   <span data-ttu-id="aa0c2-169">*비어 있음*</span><span class="sxs-lookup"><span data-stu-id="aa0c2-169">*Empty*</span></span>  
  
    |<span data-ttu-id="aa0c2-170">주문</span><span class="sxs-lookup"><span data-stu-id="aa0c2-170">Order</span></span>|<span data-ttu-id="aa0c2-171">수량</span><span class="sxs-lookup"><span data-stu-id="aa0c2-171">Qty</span></span>|<span data-ttu-id="aa0c2-172">ID</span><span class="sxs-lookup"><span data-stu-id="aa0c2-172">ID</span></span>|<span data-ttu-id="aa0c2-173">FirstName</span><span class="sxs-lookup"><span data-stu-id="aa0c2-173">FirstName</span></span>|<span data-ttu-id="aa0c2-174">LastName</span><span class="sxs-lookup"><span data-stu-id="aa0c2-174">LastName</span></span>|<span data-ttu-id="aa0c2-175">Customer.ID</span><span class="sxs-lookup"><span data-stu-id="aa0c2-175">Customer.ID</span></span>|<span data-ttu-id="aa0c2-176">xmlns</span><span class="sxs-lookup"><span data-stu-id="aa0c2-176">xmlns</span></span>|  
    |-----------|---------|--------|---------------|--------------|-----------------|-----------|  
    |<span data-ttu-id="aa0c2-177">Chair</span><span class="sxs-lookup"><span data-stu-id="aa0c2-177">Chair</span></span>|<span data-ttu-id="aa0c2-178">6</span><span class="sxs-lookup"><span data-stu-id="aa0c2-178">6</span></span>|<span data-ttu-id="aa0c2-179">1</span><span class="sxs-lookup"><span data-stu-id="aa0c2-179">1</span></span>|<span data-ttu-id="aa0c2-180">Bobby</span><span class="sxs-lookup"><span data-stu-id="aa0c2-180">Bobby</span></span>|<span data-ttu-id="aa0c2-181">Moore</span><span class="sxs-lookup"><span data-stu-id="aa0c2-181">Moore</span></span>|<span data-ttu-id="aa0c2-182">11</span><span class="sxs-lookup"><span data-stu-id="aa0c2-182">11</span></span>|http://www.adventure-works.com|  
    |<span data-ttu-id="aa0c2-183">표</span><span class="sxs-lookup"><span data-stu-id="aa0c2-183">Table</span></span>|<span data-ttu-id="aa0c2-184">1</span><span class="sxs-lookup"><span data-stu-id="aa0c2-184">1</span></span>|<span data-ttu-id="aa0c2-185">2</span><span class="sxs-lookup"><span data-stu-id="aa0c2-185">2</span></span>|<span data-ttu-id="aa0c2-186">Bobby</span><span class="sxs-lookup"><span data-stu-id="aa0c2-186">Bobby</span></span>|<span data-ttu-id="aa0c2-187">Moore</span><span class="sxs-lookup"><span data-stu-id="aa0c2-187">Moore</span></span>|<span data-ttu-id="aa0c2-188">11</span><span class="sxs-lookup"><span data-stu-id="aa0c2-188">11</span></span>|http://www.adventure-works.com|  
    |<span data-ttu-id="aa0c2-189">Sofa</span><span class="sxs-lookup"><span data-stu-id="aa0c2-189">Sofa</span></span>|<span data-ttu-id="aa0c2-190">2</span><span class="sxs-lookup"><span data-stu-id="aa0c2-190">2</span></span>|<span data-ttu-id="aa0c2-191">8</span><span class="sxs-lookup"><span data-stu-id="aa0c2-191">8</span></span>|<span data-ttu-id="aa0c2-192">Crystal</span><span class="sxs-lookup"><span data-stu-id="aa0c2-192">Crystal</span></span>|<span data-ttu-id="aa0c2-193">Hu</span><span class="sxs-lookup"><span data-stu-id="aa0c2-193">Hu</span></span>|<span data-ttu-id="aa0c2-194">20</span><span class="sxs-lookup"><span data-stu-id="aa0c2-194">20</span></span>|http://www.adventure-works.com|  
    |<span data-ttu-id="aa0c2-195">EndTables</span><span class="sxs-lookup"><span data-stu-id="aa0c2-195">EndTables</span></span>|<span data-ttu-id="aa0c2-196">2</span><span class="sxs-lookup"><span data-stu-id="aa0c2-196">2</span></span>|<span data-ttu-id="aa0c2-197">15</span><span class="sxs-lookup"><span data-stu-id="aa0c2-197">15</span></span>|<span data-ttu-id="aa0c2-198">Wyatt</span><span class="sxs-lookup"><span data-stu-id="aa0c2-198">Wyatt</span></span>|<span data-ttu-id="aa0c2-199">Diaz</span><span class="sxs-lookup"><span data-stu-id="aa0c2-199">Diaz</span></span>|<span data-ttu-id="aa0c2-200">33</span><span class="sxs-lookup"><span data-stu-id="aa0c2-200">33</span></span>|http://www.adventure-works.com|  
  
-   `Customers {}/Customer`  
  
    |<span data-ttu-id="aa0c2-201">FirstName</span><span class="sxs-lookup"><span data-stu-id="aa0c2-201">FirstName</span></span>|<span data-ttu-id="aa0c2-202">LastName</span><span class="sxs-lookup"><span data-stu-id="aa0c2-202">LastName</span></span>|<span data-ttu-id="aa0c2-203">ID</span><span class="sxs-lookup"><span data-stu-id="aa0c2-203">ID</span></span>|  
    |---------------|--------------|--------|  
    |<span data-ttu-id="aa0c2-204">Bobby</span><span class="sxs-lookup"><span data-stu-id="aa0c2-204">Bobby</span></span>|<span data-ttu-id="aa0c2-205">Moore</span><span class="sxs-lookup"><span data-stu-id="aa0c2-205">Moore</span></span>|<span data-ttu-id="aa0c2-206">11</span><span class="sxs-lookup"><span data-stu-id="aa0c2-206">11</span></span>|  
    |<span data-ttu-id="aa0c2-207">Crystal</span><span class="sxs-lookup"><span data-stu-id="aa0c2-207">Crystal</span></span>|<span data-ttu-id="aa0c2-208">Hu</span><span class="sxs-lookup"><span data-stu-id="aa0c2-208">Hu</span></span>|<span data-ttu-id="aa0c2-209">20</span><span class="sxs-lookup"><span data-stu-id="aa0c2-209">20</span></span>|  
    |<span data-ttu-id="aa0c2-210">Wyatt</span><span class="sxs-lookup"><span data-stu-id="aa0c2-210">Wyatt</span></span>|<span data-ttu-id="aa0c2-211">Diaz</span><span class="sxs-lookup"><span data-stu-id="aa0c2-211">Diaz</span></span>|<span data-ttu-id="aa0c2-212">33</span><span class="sxs-lookup"><span data-stu-id="aa0c2-212">33</span></span>|  
  
-   `Customers {}/Customer {}/LastName`  
  
    |<span data-ttu-id="aa0c2-213">LastName</span><span class="sxs-lookup"><span data-stu-id="aa0c2-213">LastName</span></span>|  
    |--------------|  
    |<span data-ttu-id="aa0c2-214">Moore</span><span class="sxs-lookup"><span data-stu-id="aa0c2-214">Moore</span></span>|  
    |<span data-ttu-id="aa0c2-215">Hu</span><span class="sxs-lookup"><span data-stu-id="aa0c2-215">Hu</span></span>|  
    |<span data-ttu-id="aa0c2-216">Diaz</span><span class="sxs-lookup"><span data-stu-id="aa0c2-216">Diaz</span></span>|  
  
-   `Customers {}/Customer {}/Orders/Order {@,@Qty}`  
  
    |<span data-ttu-id="aa0c2-217">주문</span><span class="sxs-lookup"><span data-stu-id="aa0c2-217">Order</span></span>|<span data-ttu-id="aa0c2-218">수량</span><span class="sxs-lookup"><span data-stu-id="aa0c2-218">Qty</span></span>|  
    |-----------|---------|  
    |<span data-ttu-id="aa0c2-219">Chair</span><span class="sxs-lookup"><span data-stu-id="aa0c2-219">Chair</span></span>|<span data-ttu-id="aa0c2-220">6</span><span class="sxs-lookup"><span data-stu-id="aa0c2-220">6</span></span>|  
    |<span data-ttu-id="aa0c2-221">표</span><span class="sxs-lookup"><span data-stu-id="aa0c2-221">Table</span></span>|<span data-ttu-id="aa0c2-222">1</span><span class="sxs-lookup"><span data-stu-id="aa0c2-222">1</span></span>|  
    |<span data-ttu-id="aa0c2-223">Sofa</span><span class="sxs-lookup"><span data-stu-id="aa0c2-223">Sofa</span></span>|<span data-ttu-id="aa0c2-224">2</span><span class="sxs-lookup"><span data-stu-id="aa0c2-224">2</span></span>|  
    |<span data-ttu-id="aa0c2-225">EndTables</span><span class="sxs-lookup"><span data-stu-id="aa0c2-225">EndTables</span></span>|<span data-ttu-id="aa0c2-226">2</span><span class="sxs-lookup"><span data-stu-id="aa0c2-226">2</span></span>|  
  
-   `Customers {}/Customer/Orders/Order{ @ID(Integer)}`  
  
    |<span data-ttu-id="aa0c2-227">Order.ID</span><span class="sxs-lookup"><span data-stu-id="aa0c2-227">Order.ID</span></span>|<span data-ttu-id="aa0c2-228">FirstName</span><span class="sxs-lookup"><span data-stu-id="aa0c2-228">FirstName</span></span>|<span data-ttu-id="aa0c2-229">LastName</span><span class="sxs-lookup"><span data-stu-id="aa0c2-229">LastName</span></span>|<span data-ttu-id="aa0c2-230">ID</span><span class="sxs-lookup"><span data-stu-id="aa0c2-230">ID</span></span>|  
    |--------------|---------------|--------------|--------|  
    |<span data-ttu-id="aa0c2-231">1</span><span class="sxs-lookup"><span data-stu-id="aa0c2-231">1</span></span>|<span data-ttu-id="aa0c2-232">Bobby</span><span class="sxs-lookup"><span data-stu-id="aa0c2-232">Bobby</span></span>|<span data-ttu-id="aa0c2-233">Moore</span><span class="sxs-lookup"><span data-stu-id="aa0c2-233">Moore</span></span>|<span data-ttu-id="aa0c2-234">11</span><span class="sxs-lookup"><span data-stu-id="aa0c2-234">11</span></span>|  
    |<span data-ttu-id="aa0c2-235">2</span><span class="sxs-lookup"><span data-stu-id="aa0c2-235">2</span></span>|<span data-ttu-id="aa0c2-236">Bobby</span><span class="sxs-lookup"><span data-stu-id="aa0c2-236">Bobby</span></span>|<span data-ttu-id="aa0c2-237">Moore</span><span class="sxs-lookup"><span data-stu-id="aa0c2-237">Moore</span></span>|<span data-ttu-id="aa0c2-238">11</span><span class="sxs-lookup"><span data-stu-id="aa0c2-238">11</span></span>|  
    |<span data-ttu-id="aa0c2-239">8</span><span class="sxs-lookup"><span data-stu-id="aa0c2-239">8</span></span>|<span data-ttu-id="aa0c2-240">Crystal</span><span class="sxs-lookup"><span data-stu-id="aa0c2-240">Crystal</span></span>|<span data-ttu-id="aa0c2-241">Hu</span><span class="sxs-lookup"><span data-stu-id="aa0c2-241">Hu</span></span>|<span data-ttu-id="aa0c2-242">20</span><span class="sxs-lookup"><span data-stu-id="aa0c2-242">20</span></span>|  
    |<span data-ttu-id="aa0c2-243">15</span><span class="sxs-lookup"><span data-stu-id="aa0c2-243">15</span></span>|<span data-ttu-id="aa0c2-244">Wyatt</span><span class="sxs-lookup"><span data-stu-id="aa0c2-244">Wyatt</span></span>|<span data-ttu-id="aa0c2-245">Diaz</span><span class="sxs-lookup"><span data-stu-id="aa0c2-245">Diaz</span></span>|<span data-ttu-id="aa0c2-246">33</span><span class="sxs-lookup"><span data-stu-id="aa0c2-246">33</span></span>|  
  
#### <a name="xml-document-customersxml"></a><span data-ttu-id="aa0c2-247">XML 문서: Customers.xml</span><span class="sxs-lookup"><span data-stu-id="aa0c2-247">XML document: Customers.xml</span></span>  
 <span data-ttu-id="aa0c2-248">이전 섹션의 요소 경로 예를 사용하려면 이 XML을 복사하여 보고서 디자이너에서 액세스할 수 있는 URL에 저장한 다음 해당 XML 문서를 XML 데이터 원본으로 사용합니다(예: `http://localhost/Customers.xml`).</span><span class="sxs-lookup"><span data-stu-id="aa0c2-248">To try out the element path examples in the previous section, you can copy this XML and save it to a URL that is accessible by Report Designer, and then use the XML document as an XML data source: for example, `http://localhost/Customers.xml`.</span></span>  
  
```  
<?xml version="1.0"?>  
<Customers xmlns="http://www.adventure-works.com">  
   <Customer ID="11">  
      <FirstName>Bobby</FirstName>  
      <LastName>Moore</LastName>  
      <Orders>  
         <Order ID="1" Qty="6">Chair</Order>  
         <Order ID="2" Qty="1">Table</Order>  
      </Orders>  
      <Returns>  
         <Return ID="1" Qty="2">Chair</Return>  
      </Returns>  
   </Customer>  
   <Customer ID="20">  
      <FirstName>Crystal</FirstName>  
      <LastName>Hu</LastName>  
      <Orders>  
         <Order ID="8" Qty="2">Sofa</Order>  
      </Orders>  
      <Returns/>  
   </Customer>  
   <Customer ID="33">  
      <FirstName>Wyatt</FirstName>  
      <LastName>Diaz</LastName>  
      <Orders>  
         <Order ID="15" Qty="2">EndTables</Order>  
      </Orders>  
      <Returns/>  
   </Customer>  
</Customers>  
```  
  
 <span data-ttu-id="aa0c2-249">또는 다음과 같은 절차에 따라 연결 문자열이 없는 XML 데이터 원본을 만들고 쿼리에 Customers.XML을 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa0c2-249">Alternatively, you can create an XML data source that has no connection string and embed Customers.XML in the query, using the following procedure:</span></span>  
  
###### <a name="to-embed-customersxml-in-a-query"></a><span data-ttu-id="aa0c2-250">쿼리에 Customers.XML을 포함하려면</span><span class="sxs-lookup"><span data-stu-id="aa0c2-250">To embed Customers.XML in a query</span></span>  
  
1.  <span data-ttu-id="aa0c2-251">빈 연결 문자열을 사용하여 XML 데이터 원본을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="aa0c2-251">Create an XML data source with a blank connection string.</span></span>  
  
2.  <span data-ttu-id="aa0c2-252">XML 데이터 원본에 대한 새 데이터 세트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="aa0c2-252">Create a new dataset for the XML data source.</span></span>  
  
3.  <span data-ttu-id="aa0c2-253">**데이터 세트 속성** 대화 상자에서 **쿼리 디자이너**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="aa0c2-253">In the **Dataset Properties** dialog box, click **Query Designer**.</span></span> <span data-ttu-id="aa0c2-254">텍스트 기반의 쿼리 디자이너 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="aa0c2-254">The text-based query designer dialog box opens.</span></span>  
  
4.  <span data-ttu-id="aa0c2-255">쿼리 창에서 다음 두 줄을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="aa0c2-255">In the query pane, enter the following two lines:</span></span>  
  
     `<Query>`  
  
     `<XmlData>`  
  
5.  <span data-ttu-id="aa0c2-256">Customers.XML을 복사하여 쿼리 창에서 `<XmlData>`다음에 텍스트를 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="aa0c2-256">Copy Customers.XML and paste the text in the query pane after `<XmlData>`.</span></span>  
  
6.  <span data-ttu-id="aa0c2-257">쿼리 창에서 Customers.XML로부터 복사한 첫 번째 줄을 삭제합니다. `<?xml version="1.0"?>`</span><span class="sxs-lookup"><span data-stu-id="aa0c2-257">In the query pane, delete the first line that you copied from Customers.XML: `<?xml version="1.0"?>`</span></span>  
  
7.  <span data-ttu-id="aa0c2-258">쿼리 끝에 다음 두 줄을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="aa0c2-258">At the end of the query, add the following two lines:</span></span>  
  
     `<XmlData>`  
  
     `<Query>`  
  
8.  <span data-ttu-id="aa0c2-259">**쿼리 실행** (!)을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="aa0c2-259">Click **Run Query** (!).</span></span>  
  
     <span data-ttu-id="aa0c2-260">다음 열과 함께 4줄의 데이터로 결과 집합이 표시됩니다. `xmlns`, `Customer.ID`, `FirstName`, `LastName`, `ID`, `Qty`, `Order`</span><span class="sxs-lookup"><span data-stu-id="aa0c2-260">The result set displays 4 lines of data with the following columns: `xmlns`, `Customer.ID`, `FirstName`, `LastName`, `ID`, `Qty`, `Order`.</span></span>  
  
9. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="aa0c2-261">참고 항목</span><span class="sxs-lookup"><span data-stu-id="aa0c2-261">See Also</span></span>  
 <span data-ttu-id="aa0c2-262">[SSRS&#41;&#40;XML 연결 형식](xml-connection-type-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="aa0c2-262">[XML Connection Type &#40;SSRS&#41;](xml-connection-type-ssrs.md) </span></span>  
 <span data-ttu-id="aa0c2-263">[SSRS를 &#40;Reporting Services 자습서&#41;](../reporting-services-tutorials-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="aa0c2-263">[Reporting Services Tutorials &#40;SSRS&#41;](../reporting-services-tutorials-ssrs.md) </span></span>  
 [<span data-ttu-id="aa0c2-264">보고서 데이터 창에서 필드 추가, 편집, 새로 고침&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="aa0c2-264">Add, Edit, Refresh Fields in the Report Data Pane &#40;Report Builder and SSRS&#41;</span></span>](add-edit-refresh-fields-in-the-report-data-pane-report-builder-and-ssrs.md)  
  
  
