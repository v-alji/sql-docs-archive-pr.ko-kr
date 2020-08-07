---
title: 선택적 XML 인덱스에 대한 경로 및 최적화 힌트 지정 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
ms.assetid: 486ee339-165b-4aeb-b760-d2ba023d7d0a
author: rothja
ms.author: jroth
ms.openlocfilehash: 1a9d683fe57d489fdb9922b53d2c5c6825835216
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87735135"
---
# <a name="specify-paths-and-optimization-hints-for-selective-xml-indexes"></a><span data-ttu-id="01d3f-102">선택적 XML 인덱스에 대한 경로 및 최적화 힌트 지정</span><span class="sxs-lookup"><span data-stu-id="01d3f-102">Specify Paths and Optimization Hints for Selective XML Indexes</span></span>
  <span data-ttu-id="01d3f-103">이 항목에서는 선택적 XML 인덱스를 만들거나 변경할 때 인덱싱할 노드 경로 및 인덱싱에 대한 최적화 힌트를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="01d3f-103">This topic describes how to specify node paths to index and optimization hints for indexing when you create or alter selective XML indexes.</span></span>  
  
 <span data-ttu-id="01d3f-104">노드 경로 및 최적화 힌트는 다음 문 중 하나에 동시에 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="01d3f-104">You specify node paths and optimization hints at the same time in one of the following statements:</span></span>  
  
-   <span data-ttu-id="01d3f-105">**CREATE** 문의 **FOR** 절</span><span class="sxs-lookup"><span data-stu-id="01d3f-105">In the **FOR** clause of a **CREATE** statement.</span></span> <span data-ttu-id="01d3f-106">자세한 내용은 [CREATE SELECTIVE XML INDEX&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-selective-xml-index-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="01d3f-106">For more information, see [CREATE SELECTIVE XML INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-selective-xml-index-transact-sql).</span></span>  
  
-   <span data-ttu-id="01d3f-107">**ALTER** 문의 **ADD** 절</span><span class="sxs-lookup"><span data-stu-id="01d3f-107">In the **ADD** clause of an **ALTER** statement.</span></span> <span data-ttu-id="01d3f-108">자세한 내용은 [ALTER INDEX&#40;선택적 XML 인덱스&#41;](../indexes/indexes.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="01d3f-108">For more information, see [ALTER INDEX &#40;Selective XML Indexes&#41;](../indexes/indexes.md).</span></span>  
  
 <span data-ttu-id="01d3f-109">선택적 XML 인덱스에 대한 자세한 내용은 [SXI&#40;선택적 XML 인덱스&#41;](../xml/selective-xml-indexes-sxi.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="01d3f-109">For more information about selective XML indexes, see [Selective XML Indexes &#40;SXI&#41;](../xml/selective-xml-indexes-sxi.md).</span></span>  
  
##  <a name="understanding-xquery-and-sql-server-types-in-untyped-xml"></a><a name="untyped"></a> <span data-ttu-id="01d3f-110">형식화된 XML의 XQuery 및 SQL Server 유형 이해</span><span class="sxs-lookup"><span data-stu-id="01d3f-110">Understanding XQuery and SQL Server Types in Untyped XML</span></span>  
 <span data-ttu-id="01d3f-111">선택적 XML 인덱스는 두 가지 유형 시스템, XQuery 유형 및 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 유형을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="01d3f-111">Selective XML indexes support two type systems: XQuery types and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] types.</span></span> <span data-ttu-id="01d3f-112">인덱싱된 경로는 XQuery 식을 일치시키거나 XML 데이터 형식의 value() 메서드에 대한 반환 형식을 일치시키는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="01d3f-112">The indexed path can be used either to match an XQuery expression, or to match the return type of the value() method of the XML data type.</span></span>  
  
-   <span data-ttu-id="01d3f-113">인덱싱할 경로에 주석이 지정되어 있지 않거나 XQUERY 키워드로 주석이 지정된 경우 해당 경로는 XQuery 식과 일치합니다.</span><span class="sxs-lookup"><span data-stu-id="01d3f-113">When a path to index is not annotated, or is annotated with the XQUERY keyword, the path matches an XQuery expression.</span></span> <span data-ttu-id="01d3f-114">XQUERY로 주석이 지정된 노드 경로에는 다음과 같은 두 가지 변형이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="01d3f-114">There are two variations for XQUERY-annotated node paths:</span></span>  
  
    -   <span data-ttu-id="01d3f-115">XQUERY 키워드 및 XQuery 데이터 형식을 지정하지 않으면 기본 매핑이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="01d3f-115">If you do not specify the XQUERY keyword and the XQuery data type, then default mappings are used.</span></span> <span data-ttu-id="01d3f-116">이 경우 일반적으로 성능 및 스토리지는 효율적이지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="01d3f-116">Typically performance and storage are not optimal.</span></span>  
  
    -   <span data-ttu-id="01d3f-117">XQUERY 키워드 및 XQuery 데이터 형식을 지정하고 선택적으로 다른 최적화 옵션을 지정하면 가능한 최상의 성능과 가능한 가장 효율적인 스토리지를 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="01d3f-117">If you specify the XQUERY keyword and the XQuery data type, and optionally other optimization hints, then you can achieve the best possible performance and the most efficient possible storage.</span></span> <span data-ttu-id="01d3f-118">캐스팅은 실패할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="01d3f-118">However, a cast can fail.</span></span>  
  
-   <span data-ttu-id="01d3f-119">인덱싱할 경로에 SQL 키워드로 주석이 지정된 경우 해당 경로는 XML 데이터 형식의 value() 메서드에 대한 반환 형식과 일치합니다.</span><span class="sxs-lookup"><span data-stu-id="01d3f-119">When a path to index is annotated with the SQL keyword, the path matches the return type of the value() method of the XML data type.</span></span> <span data-ttu-id="01d3f-120">value() 메서드의 반환 형식인 적절한 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터 형식을 지정하십시오.</span><span class="sxs-lookup"><span data-stu-id="01d3f-120">Specify the appropriate [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data type, which is the return type that you expect from the value() method.</span></span>  
  
 <span data-ttu-id="01d3f-121">XML 데이터 형식의 value() 메서드에 적용되는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 유형 시스템과 XQuery 식 XML 유형 시스템과 간에는 약간의 차이가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="01d3f-121">There are subtle differences between the XQuery expressions XML type system and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] type system applied to the value() method of the XML data type.</span></span> <span data-ttu-id="01d3f-122">이러한 차이점은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="01d3f-122">These differences include the following:</span></span>  
  
-   <span data-ttu-id="01d3f-123">XQuery 유형 시스템은 후행 공백을 인식합니다.</span><span class="sxs-lookup"><span data-stu-id="01d3f-123">The XQuery type system is aware of trailing spaces.</span></span> <span data-ttu-id="01d3f-124">예를 들어 XQuery 유형 의미 체계에서는 문자열 "abc"와 "abc "가 같은 문자열이 아니지만 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서는 이러한 문자열이 같은 문자열입니다.</span><span class="sxs-lookup"><span data-stu-id="01d3f-124">For example, according to XQuery type semantics, the strings "abc" and "abc " are not equal, while in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] these strings are equal.</span></span>  
  
-   <span data-ttu-id="01d3f-125">XQuery 부동 소수점 데이터 형식에서는 +/- 0 및 +/- 무한대와 같은 특수 값이 지원되지만</span><span class="sxs-lookup"><span data-stu-id="01d3f-125">XQuery floating point data types support special values of +/- zero and +/- infinity.</span></span> <span data-ttu-id="01d3f-126">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 부동 소수점 데이터 형식에서는 이러한 특수 값이 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="01d3f-126">These special values are not supported in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] floating point data types.</span></span>  
  
### <a name="xquery-types-in-untyped-xml"></a><span data-ttu-id="01d3f-127">형식화되지 않은 XML의 XQuery 유형</span><span class="sxs-lookup"><span data-stu-id="01d3f-127">XQuery Types in Untyped XML</span></span>  
  
-   <span data-ttu-id="01d3f-128">XQuery 유형은 value() 메서드를 비롯한 XML 데이터 형식의 모든 메서드에 있는 XQuery 식과 일치합니다.</span><span class="sxs-lookup"><span data-stu-id="01d3f-128">XQuery types match XQuery expressions in all methods of the XML data type including the value() method.</span></span>  
  
-   <span data-ttu-id="01d3f-129">XQuery 유형은 node(), SINGLETON, DATA TYPE 및 MAXLENGTH 최적화 힌트를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="01d3f-129">XQuery types support these optimization hints: node(), SINGLETON, DATA TYPE, and MAXLENGTH.</span></span>  
  
 <span data-ttu-id="01d3f-130">형식화되지 않은 XML에 대한 XQuery 식의 작업 모드는 다음 두 가지 중에서 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="01d3f-130">For XQuery expressions over untyped XML, you can choose between two modes of operation:</span></span>  
  
-   <span data-ttu-id="01d3f-131">**기본 매핑 모드**.</span><span class="sxs-lookup"><span data-stu-id="01d3f-131">**Default mapping mode**.</span></span> <span data-ttu-id="01d3f-132">이 모드에서는 선택적 XML 인덱스를 만들 때만 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="01d3f-132">In this mode, you specify only the path when creating a selective XML index.</span></span>  
  
-   <span data-ttu-id="01d3f-133">**사용자 지정 매핑 모드**.</span><span class="sxs-lookup"><span data-stu-id="01d3f-133">**User-specified mapping mode**.</span></span> <span data-ttu-id="01d3f-134">이 모드에서는 선택적 최적화 힌트와 경로를 둘 다 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="01d3f-134">In this mode, you specify both the path and optional optimization hints.</span></span>  
  
 <span data-ttu-id="01d3f-135">기본 매핑 모드에서는 안전하고 일반적인 스토리지 옵션을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="01d3f-135">The default mapping mode uses a conservative storage option which is always safe and general.</span></span> <span data-ttu-id="01d3f-136">따라서 경로가 모든 식 유형과 일치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="01d3f-136">It can match any expression type.</span></span> <span data-ttu-id="01d3f-137">런타임 캐스팅이 더 많이 필요하고 보조 인덱스를 사용할 수 없기 때문에 기본 매핑 모드의 제한은 최상의 성능보다 낮습니다.</span><span class="sxs-lookup"><span data-stu-id="01d3f-137">A limitation of the default mapping mode is less than optimal performance, because an increased number of runtime casts are required, and secondary indexes are not available.</span></span>  
  
 <span data-ttu-id="01d3f-138">다음은 기본 매핑을 사용하여 만든 선택적 XML 인덱스의 예입니다.</span><span class="sxs-lookup"><span data-stu-id="01d3f-138">Here is an example of a selective XML index created with default mappings.</span></span> <span data-ttu-id="01d3f-139">세 경로 모두에 기본 노드 형식(**xs:untypedAtomic**) 및 카디널리티가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="01d3f-139">For all three paths, the default node type (**xs:untypedAtomic**) and cardinality are used.</span></span>  
  
```sql  
CREATE SELECTIVE XML INDEX example_sxi_UX_default  
ON Tbl(xmlcol)  
FOR  
(  
mypath01 =  '/a/b',  
mypath02 = '/a/b/c',  
mypath03 = '/a/b/d'  
)  
```  
  
 <span data-ttu-id="01d3f-140">사용자 지정 매핑 모드를 사용하면 더 나은 성능을 얻기 위해 노드에 유형 및 카디널리티를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="01d3f-140">The user-specified mapping mode lets you specify a type and cardinality for the node to obtain better performance.</span></span> <span data-ttu-id="01d3f-141">그러나 캐스팅이 실패할 수 있고 지정된 유형만 선택적 XML 인덱스와 일치하므로 이 향상된 성능은 보안의 희생을 통해 얻어집니다.</span><span class="sxs-lookup"><span data-stu-id="01d3f-141">However, this improved performance is achieved by giving up safety - because a cast can fail - and generality - because only the specified type is matched with the selective XML index.</span></span>  
  
 <span data-ttu-id="01d3f-142">형식화되지 않은 XML에 대해 지원되는 XQuery 형식은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="01d3f-142">The XQuery types supported for untyped XML case are:</span></span>  
  
-   <span data-ttu-id="01d3f-143">**xs: boolean**</span><span class="sxs-lookup"><span data-stu-id="01d3f-143">**xs:boolean**</span></span>  
  
-   <span data-ttu-id="01d3f-144">**xs:double**</span><span class="sxs-lookup"><span data-stu-id="01d3f-144">**xs:double**</span></span>  
  
-   <span data-ttu-id="01d3f-145">**xs:string**</span><span class="sxs-lookup"><span data-stu-id="01d3f-145">**xs:string**</span></span>  
  
-   <span data-ttu-id="01d3f-146">**xs:date**</span><span class="sxs-lookup"><span data-stu-id="01d3f-146">**xs:date**</span></span>  
  
-   <span data-ttu-id="01d3f-147">**xs:time**</span><span class="sxs-lookup"><span data-stu-id="01d3f-147">**xs:time**</span></span>  
  
-   <span data-ttu-id="01d3f-148">**xs:dateTime**</span><span class="sxs-lookup"><span data-stu-id="01d3f-148">**xs:dateTime**</span></span>  
  
 <span data-ttu-id="01d3f-149">노드에 유형을 지정하지 않으면 해당 노드는 **xs:untypedAtomic** 데이터 형식인 것으로 간주됩니다.</span><span class="sxs-lookup"><span data-stu-id="01d3f-149">If the type is not specified, the node is assumed to be of the **xs:untypedAtomic** data type.</span></span>  
  
 <span data-ttu-id="01d3f-150">다음과 같은 방법으로 선택적 XML 인덱스를 최적화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="01d3f-150">You can optimize the selective XML index shown in the following manner:</span></span>  
  
```sql  
CREATE SELECTIVE XML INDEX example_sxi_UX_optimized  
ON Tbl(xmlcol)  
FOR  
(  
mypath= '/a/b' as XQUERY 'node()',  
pathX = '/a/b/c' as XQUERY 'xs:double' SINGLETON,  
pathY = '/a/b/d' as XQUERY 'xs:string' MAXLENGTH(200) SINGLETON  
)  
-- mypath - Only the node value is needed; storage is saved.  
-- pathX - Performance is improved; secondary indexes are possible.  
-- pathY - Performance is improved; secondary indexes are possible; storage is saved.  
```  
  
### <a name="sql-server-types-in-untyped-xml"></a><span data-ttu-id="01d3f-151">형식화되지 않은 XML의 SQL Server 유형</span><span class="sxs-lookup"><span data-stu-id="01d3f-151">SQL Server Types in Untyped XML</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="01d3f-152">유형은 value() 메서드의 반환 값과 일치합니다.</span><span class="sxs-lookup"><span data-stu-id="01d3f-152">types match the return value of the value() method.</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="01d3f-153">유형은 SINGLETON 최적화 힌트를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="01d3f-153">types support this optimization hint: SINGLETON.</span></span>  
  
 <span data-ttu-id="01d3f-154">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 유형을 반환하는 경로에는 유형을 반드시 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="01d3f-154">Specifying a type is mandatory for paths that return [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] types.</span></span> <span data-ttu-id="01d3f-155">이 경우 value() 메서드에서 사용하는 것과 동일한 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 유형을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="01d3f-155">Use the same [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] type that you would use in the value() method.</span></span>  
  
 <span data-ttu-id="01d3f-156">다음과 같은 쿼리를 고려해 보세요.</span><span class="sxs-lookup"><span data-stu-id="01d3f-156">Consider the following query:</span></span>  
  
```sql  
SELECT T.record,  
    T.xmldata.value('(/a/b/d)[1]', 'NVARCHAR(200)')  
FROM myXMLTable T  
```  
  
 <span data-ttu-id="01d3f-157">지정된 쿼리는 NVARCHAR(200) 데이터 형식으로 압축된 `/a/b/d` 경로에서 값을 반환하기 때문에 노드에 지정할 데이터 형식이 분명합니다.</span><span class="sxs-lookup"><span data-stu-id="01d3f-157">The specified query returns a value from the path `/a/b/d` packed into an NVARCHAR(200) data type, so the data type to specify for the node is obvious.</span></span> <span data-ttu-id="01d3f-158">그러나 형식화되지 않은 XML로 노드의 카디널리티를 지정할 수 있는 스키마는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="01d3f-158">However there is no schema to specify the cardinality of the node in untyped XML.</span></span> <span data-ttu-id="01d3f-159">`d` 노드가 해당 부모 노드인 `b`에 최대 한 번만 표시되도록 지정하려면 다음과 같이 SINGLETON 최적화 힌트를 사용하는 선택적 XML 인덱스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="01d3f-159">To specify that node `d` appears at most once under its parent node `b`, create a selective XML index that uses the SINGLETON optimization hint as follows:</span></span>  
  
```sql  
CREATE SELECTIVE XML INDEX example_sxi_US  
ON Tbl(xmlcol)  
FOR  
(  
node1223 = '/a/b/d' as SQL NVARCHAR(200) SINGLETON  
)  
```  
  

  
##  <a name="understanding-selective-xml-index-support-for-typed-xml"></a><a name="typed"></a> <span data-ttu-id="01d3f-160">형식화된 XML에 대한 선택적 XML 인덱스 지원 이해</span><span class="sxs-lookup"><span data-stu-id="01d3f-160">Understanding Selective XML Index support for typed XML</span></span>  
 <span data-ttu-id="01d3f-161">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 의 형식화된 XML은 지정된 XML 문서와 연결된 스키마입니다.</span><span class="sxs-lookup"><span data-stu-id="01d3f-161">Typed XML in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is a schema associated with a given XML document.</span></span> <span data-ttu-id="01d3f-162">스키마는 전체 문서 구조와 노드 유형을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="01d3f-162">The schema defines overall document structure and types of nodes.</span></span> <span data-ttu-id="01d3f-163">스키마가 있으면 사용자가 경로를 승격시킬 때 선택적 XML 인덱스가 해당 스키마 구조를 적용하기 때문에 경로에 대한 XQUERY 유형을 지정할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="01d3f-163">If a schema exists, Selective XML Index applies the schema structure when the user promotes paths, so there is no need to specify the XQUERY types for paths.</span></span>  
  
 <span data-ttu-id="01d3f-164">선택적 XML 인덱스는 다음 XSD 유형을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="01d3f-164">Selective XML Index supports following XSD types:</span></span>  
  
-   <span data-ttu-id="01d3f-165">**xs:anyUri**</span><span class="sxs-lookup"><span data-stu-id="01d3f-165">**xs:anyUri**</span></span>  
  
-   <span data-ttu-id="01d3f-166">**xs: boolean**</span><span class="sxs-lookup"><span data-stu-id="01d3f-166">**xs:boolean**</span></span>  
  
-   <span data-ttu-id="01d3f-167">**xs:date**</span><span class="sxs-lookup"><span data-stu-id="01d3f-167">**xs:date**</span></span>  
  
-   <span data-ttu-id="01d3f-168">**xs:dateTime**</span><span class="sxs-lookup"><span data-stu-id="01d3f-168">**xs:dateTime**</span></span>  
  
-   <span data-ttu-id="01d3f-169">**xs:day**</span><span class="sxs-lookup"><span data-stu-id="01d3f-169">**xs:day**</span></span>  
  
-   <span data-ttu-id="01d3f-170">**xs:decimal**</span><span class="sxs-lookup"><span data-stu-id="01d3f-170">**xs:decimal**</span></span>  
  
-   <span data-ttu-id="01d3f-171">**xs:double**</span><span class="sxs-lookup"><span data-stu-id="01d3f-171">**xs:double**</span></span>  
  
-   <span data-ttu-id="01d3f-172">**xs:float**</span><span class="sxs-lookup"><span data-stu-id="01d3f-172">**xs:float**</span></span>  
  
-   <span data-ttu-id="01d3f-173">**xs:int**</span><span class="sxs-lookup"><span data-stu-id="01d3f-173">**xs:int**</span></span>  
  
-   <span data-ttu-id="01d3f-174">**xs:integer**</span><span class="sxs-lookup"><span data-stu-id="01d3f-174">**xs:integer**</span></span>  
  
-   <span data-ttu-id="01d3f-175">**xs:language**</span><span class="sxs-lookup"><span data-stu-id="01d3f-175">**xs:language**</span></span>  
  
-   <span data-ttu-id="01d3f-176">**xs:long**</span><span class="sxs-lookup"><span data-stu-id="01d3f-176">**xs:long**</span></span>  
  
-   <span data-ttu-id="01d3f-177">**xs:name**</span><span class="sxs-lookup"><span data-stu-id="01d3f-177">**xs:name**</span></span>  
  
-   <span data-ttu-id="01d3f-178">**xs:NCName**</span><span class="sxs-lookup"><span data-stu-id="01d3f-178">**xs:NCName**</span></span>  
  
-   <span data-ttu-id="01d3f-179">**xs:negativeInteger**</span><span class="sxs-lookup"><span data-stu-id="01d3f-179">**xs:negativeInteger**</span></span>  
  
-   <span data-ttu-id="01d3f-180">**xs:nmtoken**</span><span class="sxs-lookup"><span data-stu-id="01d3f-180">**xs:nmtoken**</span></span>  
  
-   <span data-ttu-id="01d3f-181">**xs:nonNegativeInteger**</span><span class="sxs-lookup"><span data-stu-id="01d3f-181">**xs:nonNegativeInteger**</span></span>  
  
-   <span data-ttu-id="01d3f-182">**xs:nonPositiveInteger**</span><span class="sxs-lookup"><span data-stu-id="01d3f-182">**xs:nonPositiveInteger**</span></span>  
  
-   <span data-ttu-id="01d3f-183">**xs:positiveInteger**</span><span class="sxs-lookup"><span data-stu-id="01d3f-183">**xs:positiveInteger**</span></span>  
  
-   <span data-ttu-id="01d3f-184">**xs:qname**</span><span class="sxs-lookup"><span data-stu-id="01d3f-184">**xs:qname**</span></span>  
  
-   <span data-ttu-id="01d3f-185">**xs:short**</span><span class="sxs-lookup"><span data-stu-id="01d3f-185">**xs:short**</span></span>  
  
-   <span data-ttu-id="01d3f-186">**xs:string**</span><span class="sxs-lookup"><span data-stu-id="01d3f-186">**xs:string**</span></span>  
  
-   <span data-ttu-id="01d3f-187">**xs:time**</span><span class="sxs-lookup"><span data-stu-id="01d3f-187">**xs:time**</span></span>  
  
-   <span data-ttu-id="01d3f-188">**xs:token**</span><span class="sxs-lookup"><span data-stu-id="01d3f-188">**xs:token**</span></span>  
  
-   <span data-ttu-id="01d3f-189">**xs:unsignedByte**</span><span class="sxs-lookup"><span data-stu-id="01d3f-189">**xs:unsignedByte**</span></span>  
  
-   <span data-ttu-id="01d3f-190">**xs:unsignedInt**</span><span class="sxs-lookup"><span data-stu-id="01d3f-190">**xs:unsignedInt**</span></span>  
  
-   <span data-ttu-id="01d3f-191">**xs:unsignedLong**</span><span class="sxs-lookup"><span data-stu-id="01d3f-191">**xs:unsignedLong**</span></span>  
  
-   <span data-ttu-id="01d3f-192">**xs:unsignedShort**</span><span class="sxs-lookup"><span data-stu-id="01d3f-192">**xs:unsignedShort**</span></span>  
  
 <span data-ttu-id="01d3f-193">스키마가 연결되어 있는 문서에 대해 선택적 XML 인덱스를 만드는 경우 인덱스를 만들거나 변경할 때 XQUERY 유형을 지정하면 오류가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="01d3f-193">When Selective XML Index is created over a document that has schema associated with it, specifying a XQUERY type at index creation or altering returns an error.</span></span> <span data-ttu-id="01d3f-194">사용자는 경로 승격 부분에 SQL 유형 주석을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="01d3f-194">The user can use SQL type annotations in the path promotion part.</span></span> <span data-ttu-id="01d3f-195">SQL 유형은 스키마에 정의된 XSD 유형으로부터의 유효한 변환이어야 합니다. 그렇지 않으면 예외가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="01d3f-195">The SQL type must be a valid conversion from the XSD type defined in the schema, or an error is thrown.</span></span> <span data-ttu-id="01d3f-196">날짜/시간 유형을 제외하고 XSD로 적절하게 표현된 모든 SQL 유형이 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="01d3f-196">All SQL types that have adequate representation in XSD are supported, with an exception of date/time types.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="01d3f-197">선택적 인덱스는 선택적 XML 인덱스 경로 승격에 지정된 유형이 value() 메서드 반환 값과 같을 경우 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="01d3f-197">The selective index is used if the type specified in the Selective XML Index path promotion is the same as the value() method return value.</span></span>  
  
 <span data-ttu-id="01d3f-198">다음은 형식화된 XML 문서에서 사용할 수 있는 최적화 힌트입니다.</span><span class="sxs-lookup"><span data-stu-id="01d3f-198">The following optimization hints can be used with typed XML documents:</span></span>  
  
-   <span data-ttu-id="01d3f-199">node() 최적화 힌트</span><span class="sxs-lookup"><span data-stu-id="01d3f-199">node() optimization hint.</span></span>  
  
-   <span data-ttu-id="01d3f-200">MAXLENGTH 최적화 힌트는 인덱싱된 값을 줄이기 위해 xs:string 유형과 함께 사용될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="01d3f-200">MAXLENGTH optimization hint can be used with xs:string types to shorten the indexed value.</span></span>  
  
 <span data-ttu-id="01d3f-201">최적화 힌트에 대한 자세한 내용은 [최적화 힌트 지정](#hints)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="01d3f-201">For more information about optimization hints, see [Specifying Optimization Hints](#hints).</span></span>  
  
##  <a name="specifying-paths"></a><a name="paths"></a> <span data-ttu-id="01d3f-202">경로 지정</span><span class="sxs-lookup"><span data-stu-id="01d3f-202">Specifying Paths</span></span>  
 <span data-ttu-id="01d3f-203">선택적 XML 인덱스를 사용하면 저장된 XML 데이터에서 실행할 쿼리와 관련 있는 노드의 하위 집합만 인덱싱할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="01d3f-203">A selective XML index lets you index only a subset of nodes from the stored XML data that are relevant for the queries that you expect to run.</span></span> <span data-ttu-id="01d3f-204">관련 노드의 하위 집합이 XML 문서에 있는 총 노드 수보다 훨씬 적을 경우 선택적 XML 인덱스는 관련 노드만 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="01d3f-204">When the subset of relevant nodes is much smaller than the total number of nodes in the XML document, the selective XML index stores only the relevant nodes.</span></span> <span data-ttu-id="01d3f-205">선택적 XML 인덱스를 사용하려면 인덱싱할 노드의 올바른 하위 집합을 식별해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="01d3f-205">To benefit from a selective XML index, identify the correct subset of nodes to index.</span></span>  
  
### <a name="choosing-the-nodes-to-index"></a><span data-ttu-id="01d3f-206">인덱싱할 노드 선택</span><span class="sxs-lookup"><span data-stu-id="01d3f-206">Choosing the nodes to index</span></span>  
 <span data-ttu-id="01d3f-207">다음과 같은 두 가지 간단한 원칙을 사용하여 선택적 XML 인덱스에 추가할 노드의 올바른 하위 집합을 식별할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="01d3f-207">You can use the following two simple principles to identify the correct subset of nodes to add to a selective XML index.</span></span>  
  
1.  <span data-ttu-id="01d3f-208">**원칙 1**: 지정된 XQuery 식을 평가하려면 검사할 모든 노드를 인덱싱합니다.</span><span class="sxs-lookup"><span data-stu-id="01d3f-208">**Principle 1**: To evaluate a given XQuery expression, index all nodes that you need to examine.</span></span>  
  
    -   <span data-ttu-id="01d3f-209">존재 여부 또는 값이 XQuery 식에 사용되는 모든 노드를 인덱싱합니다.</span><span class="sxs-lookup"><span data-stu-id="01d3f-209">Index all nodes whose existence or value is used in the XQuery expression.</span></span>  
  
    -   <span data-ttu-id="01d3f-210">XQuery 조건자가 적용되는 XQuery 식의 모든 노드를 인덱싱합니다.</span><span class="sxs-lookup"><span data-stu-id="01d3f-210">Index all nodes in the XQuery expression on which XQuery predicates are applied.</span></span>  
  
     <span data-ttu-id="01d3f-211">이 항목의 [샘플 XML 문서](#sample) 에 대한 다음과 같은 간단한 쿼리를 살펴보십시오.</span><span class="sxs-lookup"><span data-stu-id="01d3f-211">Consider the following simple query over the [sample XML document](#sample) in this topic:</span></span>  
  
    ```sql  
    SELECT T.record FROM myXMLTable T  
    WHERE T.xmldata.exist('/a/b[./c = "43"]') = 1  
    ```  
  
     <span data-ttu-id="01d3f-212">아 쿼리를 만족하는 XML 인스턴스를 반환하려면 선택적 XML 인덱스가 각 XML 인스턴스에서 다음 두 노드를 검사해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="01d3f-212">In order to return the XML instances that satisfy this query, a selective XML index needs to examine two nodes in every XML instance:</span></span>  
  
    -   <span data-ttu-id="01d3f-213">`c`노드(해당 값이 XQuery 식에 사용되므로)</span><span class="sxs-lookup"><span data-stu-id="01d3f-213">Node `c`, because its value is used in the XQuery expression.</span></span>  
  
    -   <span data-ttu-id="01d3f-214">`b`노드(XQuery 식에서`b` 노드에 대해 조건자가 적용되므로)</span><span class="sxs-lookup"><span data-stu-id="01d3f-214">Node `b`, because a predicate is applied over node`b` in the XQuery expression.</span></span>  
  
2.  <span data-ttu-id="01d3f-215">**원칙 2**: 최상의 성능을 위해 지정된 XQuery 식을 평가하는 데 필요한 모든 노드를 인덱싱합니다.</span><span class="sxs-lookup"><span data-stu-id="01d3f-215">**Principle 2**: For best performance, index all nodes that are required to evaluate a given XQuery expression.</span></span> <span data-ttu-id="01d3f-216">이러한 노드 중 일부만 인덱싱할 경우 선택적 XML 인덱스가 인덱싱된 노드만 포함하는 하위 식의 평가를 향상시킵니다.</span><span class="sxs-lookup"><span data-stu-id="01d3f-216">If you index only some of the nodes, then the selective XML index improves the evaluation of sub-expressions that include only indexed nodes.</span></span>  
  
 <span data-ttu-id="01d3f-217">위에 표시된 SELECT 문의 성능을 향상시키기 위해 다음과 같은 선택적 XML 인덱스를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="01d3f-217">To improve the performance of the SELECT statement shown above, you can create the following selective XML index:</span></span>  
  
```sql  
CREATE SELECTIVE XML INDEX simple_sxi  
ON Tbl(xmlcol)  
FOR  
(  
    path123 =  '/a/b',  
    path124 =  '/a/b/c'  
)  
```  
  
### <a name="indexing-identical-paths"></a><span data-ttu-id="01d3f-218">동일한 경로 인덱싱</span><span class="sxs-lookup"><span data-stu-id="01d3f-218">Indexing identical paths</span></span>  
 <span data-ttu-id="01d3f-219">동일한 경로를 서로 다른 경로 이름을 사용하는 동일한 데이터 형식으로 승격시킬 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="01d3f-219">You cannot promote identical paths as the same data type under different path names.</span></span> <span data-ttu-id="01d3f-220">예를 들어 다음 쿼리를 실행하면 `pathOne` 과 `pathTwo` 가 동일하기 때문에 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="01d3f-220">For example, the following query raises an error, because `pathOne` and `pathTwo` are identical:</span></span>  
  
```sql  
CREATE SELECTIVE INDEX test_simple_sxi ON T1(xmlCol)  
FOR  
(  
    pathOne = 'book/authors/authorID' AS XQUERY 'xs:string',  
    pathTwo = 'book/authors/authorID' AS XQUERY 'xs:string'  
)  
```  
  
 <span data-ttu-id="01d3f-221">그러나 동일한 경로를 서로 다른 이름을 사용하는 서로 다른 데이터 형식으로는 승격시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="01d3f-221">However, you can promote identical paths as different data types with different names.</span></span> <span data-ttu-id="01d3f-222">예를 들어 다음 쿼리는 데이터 형식이 다르기 때문에 허용될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="01d3f-222">For example, the following query is now acceptable, because the data types are different:</span></span>  
  
```sql  
CREATE SELECTIVE INDEX test_simple_sxi ON T1(xmlCol)  
FOR  
(  
    pathOne = 'book/authors/authorID' AS XQUERY 'xs:double',  
    pathTwo = 'book/authors/authorID' AS XQUERY 'xs:string'  
)  
```  
  
### <a name="examples"></a><span data-ttu-id="01d3f-223">예제</span><span class="sxs-lookup"><span data-stu-id="01d3f-223">Examples</span></span>  
 <span data-ttu-id="01d3f-224">다음은 서로 다른 XQuery 형식에 대해 인덱싱할 올바른 노드를 선택하는 몇 가지 추가 예입니다.</span><span class="sxs-lookup"><span data-stu-id="01d3f-224">Here are some additional examples of selecting the correct nodes to index for different XQuery types.</span></span>  
  
 <span data-ttu-id="01d3f-225">**예제 1**</span><span class="sxs-lookup"><span data-stu-id="01d3f-225">**Example 1**</span></span>  
  
 <span data-ttu-id="01d3f-226">다음은 exist() 메서드를 사용하는 간단한 XQuery입니다.</span><span class="sxs-lookup"><span data-stu-id="01d3f-226">Here is a simple XQuery that uses the exist() method:</span></span>  
  
```sql  
SELECT T.record FROM myXMLTable T  
WHERE T.xmldata.exist('/a/b/c/d/e/h') = 1  
```  
  
 <span data-ttu-id="01d3f-227">다음 표에서는 이 쿼리가 선택적 XML 인덱스를 사용할 수 있도록 하기 위해 인덱싱해야 하는 노드를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="01d3f-227">The following table shows the nodes that should be indexed to let this query use the selective XML index.</span></span>  
  
|<span data-ttu-id="01d3f-228">인덱스에 포함할 열</span><span class="sxs-lookup"><span data-stu-id="01d3f-228">Node to include in the index</span></span>|<span data-ttu-id="01d3f-229">이 노드를 인덱싱하는 이유</span><span class="sxs-lookup"><span data-stu-id="01d3f-229">Reason for indexing this node</span></span>|  
|----------------------------------|-----------------------------------|  
|<span data-ttu-id="01d3f-230">**/a/b/c/d/e/h**</span><span class="sxs-lookup"><span data-stu-id="01d3f-230">**/a/b/c/d/e/h**</span></span>|<span data-ttu-id="01d3f-231">`h` 노드의 존재 여부가 exist() 메서드에서 평가됩니다.</span><span class="sxs-lookup"><span data-stu-id="01d3f-231">The existence of node `h` is evaluated in the exist() method.</span></span>|  
  
 <span data-ttu-id="01d3f-232">**예제 2**</span><span class="sxs-lookup"><span data-stu-id="01d3f-232">**Example 2**</span></span>  
  
 <span data-ttu-id="01d3f-233">다음은 조건자가 적용된 이전 XQuery의 보다 복잡한 변형입니다.</span><span class="sxs-lookup"><span data-stu-id="01d3f-233">Here is a more complex variation of the previous XQuery, with a predicate applied:</span></span>  
  
```sql  
SELECT T.record FROM myXMLTable T  
WHERE T.xmldata.exist('/a/b/c/d/e[./f = "SQL"]') = 1  
```  
  
 <span data-ttu-id="01d3f-234">다음 표에서는 이 쿼리가 선택적 XML 인덱스를 사용할 수 있도록 하기 위해 인덱싱해야 하는 노드를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="01d3f-234">The following table shows the nodes that should be indexed to let this query use the selective XML index.</span></span>  
  
|<span data-ttu-id="01d3f-235">인덱스에 포함할 열</span><span class="sxs-lookup"><span data-stu-id="01d3f-235">Node to include in the index</span></span>|<span data-ttu-id="01d3f-236">이 노드를 인덱싱하는 이유</span><span class="sxs-lookup"><span data-stu-id="01d3f-236">Reason for indexing this node</span></span>|  
|----------------------------------|-----------------------------------|  
|<span data-ttu-id="01d3f-237">**/a/b/c/d/e**</span><span class="sxs-lookup"><span data-stu-id="01d3f-237">**/a/b/c/d/e**</span></span>|<span data-ttu-id="01d3f-238">조건자가 `e`노드를 통해 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="01d3f-238">A predicate is applied over node `e`.</span></span>|  
|<span data-ttu-id="01d3f-239">**/a/b/c/d/e/f**</span><span class="sxs-lookup"><span data-stu-id="01d3f-239">**/a/b/c/d/e/f**</span></span>|<span data-ttu-id="01d3f-240">`f` 노드의 값이 조건자 내에서 평가됩니다.</span><span class="sxs-lookup"><span data-stu-id="01d3f-240">The value of node `f` is evaluated inside the predicate.</span></span>|  
  
 <span data-ttu-id="01d3f-241">**예 3**</span><span class="sxs-lookup"><span data-stu-id="01d3f-241">**Example 3**</span></span>  
  
 <span data-ttu-id="01d3f-242">다음은 value() 절이 포함된 보다 복잡한 쿼리입니다.</span><span class="sxs-lookup"><span data-stu-id="01d3f-242">Here is a more complex query with a value() clause:</span></span>  
  
```sql  
SELECT T.record,  
    T.xmldata.value('(/a/b/c/d/e[./f = "SQL"]/g)[1]', 'nvarchar(100)')  
FROM myXMLTable T  
```  
  
 <span data-ttu-id="01d3f-243">다음 표에서는 이 쿼리가 선택적 XML 인덱스를 사용할 수 있도록 하기 위해 인덱싱해야 하는 노드를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="01d3f-243">The following table shows the nodes that should be indexed to let this query use the selective XML index.</span></span>  
  
|<span data-ttu-id="01d3f-244">인덱스에 포함할 열</span><span class="sxs-lookup"><span data-stu-id="01d3f-244">Node to include in the index</span></span>|<span data-ttu-id="01d3f-245">이 노드를 인덱싱하는 이유</span><span class="sxs-lookup"><span data-stu-id="01d3f-245">Reason for indexing this node</span></span>|  
|----------------------------------|-----------------------------------|  
|<span data-ttu-id="01d3f-246">**/a/b/c/d/e**</span><span class="sxs-lookup"><span data-stu-id="01d3f-246">**/a/b/c/d/e**</span></span>|<span data-ttu-id="01d3f-247">조건자가 `e`노드를 통해 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="01d3f-247">A predicate is applied over node `e`.</span></span>|  
|<span data-ttu-id="01d3f-248">**/a/b/c/d/e/f**</span><span class="sxs-lookup"><span data-stu-id="01d3f-248">**/a/b/c/d/e/f**</span></span>|<span data-ttu-id="01d3f-249">`f` 노드의 값이 조건자 내에서 평가됩니다.</span><span class="sxs-lookup"><span data-stu-id="01d3f-249">The value of node `f` is evaluated inside the predicate.</span></span>|  
|<span data-ttu-id="01d3f-250">**/a/b/c/d/e/g**</span><span class="sxs-lookup"><span data-stu-id="01d3f-250">**/a/b/c/d/e/g**</span></span>|<span data-ttu-id="01d3f-251">`g` 노드의 값이 value() 메서드에 의해 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="01d3f-251">The value of node `g` is returned by the value() method.</span></span>|  
  
 <span data-ttu-id="01d3f-252">**예제 4**</span><span class="sxs-lookup"><span data-stu-id="01d3f-252">**Example 4**</span></span>  
  
 <span data-ttu-id="01d3f-253">다음은 exist() 절 내의 FLWOR 절을 사용하는 쿼리입니다.</span><span class="sxs-lookup"><span data-stu-id="01d3f-253">Here is a query that uses a FLWOR clause inside an exist() clause.</span></span> <span data-ttu-id="01d3f-254">(FLWOR이라는 이름은 XQuery FLWOR 식을 구성하는 다섯 개의 절인 for, let, where, order by 및 return에서 따온 것입니다.)</span><span class="sxs-lookup"><span data-stu-id="01d3f-254">(The name FLWOR comes from the five clauses that can make up an XQuery FLWOR expression: for, let, where, order by, and return.)</span></span>  
  
```sql  
SELECT T.record FROM myXMLTable T  
WHERE T.xmldata.exist('  
  For $x in /a/b/c/d/e  
  Where $x/f = "SQL"  
  Return $x/g  
') = 1  
```  
  
 <span data-ttu-id="01d3f-255">다음 표에서는 이 쿼리가 선택적 XML 인덱스를 사용할 수 있도록 하기 위해 인덱싱해야 하는 노드를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="01d3f-255">The following table shows the nodes that should be indexed to let this query use the selective XML index.</span></span>  
  
|<span data-ttu-id="01d3f-256">인덱스에 포함할 열</span><span class="sxs-lookup"><span data-stu-id="01d3f-256">Node to include in the index</span></span>|<span data-ttu-id="01d3f-257">이 노드를 인덱싱하는 이유</span><span class="sxs-lookup"><span data-stu-id="01d3f-257">Reason for indexing this node</span></span>|  
|----------------------------------|-----------------------------------|  
|<span data-ttu-id="01d3f-258">**/a/b/c/d/e**</span><span class="sxs-lookup"><span data-stu-id="01d3f-258">**/a/b/c/d/e**</span></span>|<span data-ttu-id="01d3f-259">`e` 노드의 존재 여부가 FLWOR 절에서 평가됩니다.</span><span class="sxs-lookup"><span data-stu-id="01d3f-259">The existence of node `e` is evaluated in the FLWOR clause.</span></span>|  
|<span data-ttu-id="01d3f-260">**/a/b/c/d/e/f**</span><span class="sxs-lookup"><span data-stu-id="01d3f-260">**/a/b/c/d/e/f**</span></span>|<span data-ttu-id="01d3f-261">`f` 노드의 값이 FLWOR 절에서 평가됩니다.</span><span class="sxs-lookup"><span data-stu-id="01d3f-261">The value of node `f` is evaluated in the FLWOR clause.</span></span>|  
|<span data-ttu-id="01d3f-262">**/a/b/c/d/e/g**</span><span class="sxs-lookup"><span data-stu-id="01d3f-262">**/a/b/c/d/e/g**</span></span>|<span data-ttu-id="01d3f-263">`g` 노드의 존재 여부가 exist() 메서드에 의해 평가됩니다.</span><span class="sxs-lookup"><span data-stu-id="01d3f-263">The existence of node `g` is evaluated by the exist() method.</span></span>|  
  

  
##  <a name="specifying-optimization-hints"></a><a name="hints"></a> <span data-ttu-id="01d3f-264">최적화 힌트 지정</span><span class="sxs-lookup"><span data-stu-id="01d3f-264">Specifying Optimization Hints</span></span>  
 <span data-ttu-id="01d3f-265">선택적 최적화 힌트를 사용하여 선택적 XML 인덱스에 의해 인덱싱되는 노드에 대한 추가 매핑 정보를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="01d3f-265">You can use optional optimization hints to specify additional mapping details for a node indexed by a selective XML index.</span></span> <span data-ttu-id="01d3f-266">예를 들어 노드의 데이터 형식과 카디널리티, 그리고 데이터의 구조에 대한 특정 정보를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="01d3f-266">For example, you can specify the data type and cardinality of the node, and certain information about the structure of the data.</span></span> <span data-ttu-id="01d3f-267">이 추가 정보를 사용하면 매핑이 향상될 뿐 아니라</span><span class="sxs-lookup"><span data-stu-id="01d3f-267">This additional information supports better mapping.</span></span> <span data-ttu-id="01d3f-268">성능과 스토리지의 저장 능력도 향상됩니다.</span><span class="sxs-lookup"><span data-stu-id="01d3f-268">It also results in improvements in performance or savings in storage, or both.</span></span>  
  
 <span data-ttu-id="01d3f-269">최적화 힌트의 사용은 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="01d3f-269">The use of optimization hints is optional.</span></span> <span data-ttu-id="01d3f-270">언제든지 기본 매핑을 그대로 사용할 수 있습니다. 그러나 기본 매핑을 사용하면 안정적이기는 하지만 최적의 성능과 스토리지를 사용하지 못할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="01d3f-270">You can always accept the default mappings, which are reliable but may not provide optimal performance and storage.</span></span>  
  
 <span data-ttu-id="01d3f-271">SINGLETON 힌트와 같은 일부 최적화 힌트는 데이터에 대한 제약 조건을 소개합니다.</span><span class="sxs-lookup"><span data-stu-id="01d3f-271">Some optimization hints - for example, the SINGLETON hint - introduce constraints over your data.</span></span> <span data-ttu-id="01d3f-272">경우에 따라 이러한 제약 조건을 충족하지 못할 경우 오류가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="01d3f-272">In some cases, errors may be raised when those constraints are not met.</span></span>  
  
### <a name="benefits-of-optimization-hints"></a><span data-ttu-id="01d3f-273">최적화 힌트의 이점</span><span class="sxs-lookup"><span data-stu-id="01d3f-273">Benefits of Optimization Hints</span></span>  
 <span data-ttu-id="01d3f-274">다음 표에서는 보다 효율적인 스토리지 및 향상된 성능을 지원하는 최적화 힌트를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="01d3f-274">The following table identifies the optimization hints that support more efficient storage or improved performance.</span></span>  
  
|<span data-ttu-id="01d3f-275">최적화 힌트</span><span class="sxs-lookup"><span data-stu-id="01d3f-275">Optimization hint</span></span>|<span data-ttu-id="01d3f-276">보다 효율적인 스토리지</span><span class="sxs-lookup"><span data-stu-id="01d3f-276">More efficient storage</span></span>|<span data-ttu-id="01d3f-277">성능 향상</span><span class="sxs-lookup"><span data-stu-id="01d3f-277">Improved performance</span></span>|  
|-----------------------|----------------------------|--------------------------|  
|<span data-ttu-id="01d3f-278">**node()**</span><span class="sxs-lookup"><span data-stu-id="01d3f-278">**node()**</span></span>|<span data-ttu-id="01d3f-279">예</span><span class="sxs-lookup"><span data-stu-id="01d3f-279">Yes</span></span>|<span data-ttu-id="01d3f-280">예</span><span class="sxs-lookup"><span data-stu-id="01d3f-280">No</span></span>|  
|<span data-ttu-id="01d3f-281">**SINGLETON**</span><span class="sxs-lookup"><span data-stu-id="01d3f-281">**SINGLETON**</span></span>|<span data-ttu-id="01d3f-282">예</span><span class="sxs-lookup"><span data-stu-id="01d3f-282">No</span></span>|<span data-ttu-id="01d3f-283">예</span><span class="sxs-lookup"><span data-stu-id="01d3f-283">Yes</span></span>|  
|<span data-ttu-id="01d3f-284">**DATA TYPE**</span><span class="sxs-lookup"><span data-stu-id="01d3f-284">**DATA TYPE**</span></span>|<span data-ttu-id="01d3f-285">예</span><span class="sxs-lookup"><span data-stu-id="01d3f-285">Yes</span></span>|<span data-ttu-id="01d3f-286">예</span><span class="sxs-lookup"><span data-stu-id="01d3f-286">Yes</span></span>|  
|<span data-ttu-id="01d3f-287">**MAXLENGTH**</span><span class="sxs-lookup"><span data-stu-id="01d3f-287">**MAXLENGTH**</span></span>|<span data-ttu-id="01d3f-288">예</span><span class="sxs-lookup"><span data-stu-id="01d3f-288">Yes</span></span>|<span data-ttu-id="01d3f-289">예</span><span class="sxs-lookup"><span data-stu-id="01d3f-289">Yes</span></span>|  
  
### <a name="optimization-hints-and-data-types"></a><span data-ttu-id="01d3f-290">최적화 힌트 및 데이터 형식</span><span class="sxs-lookup"><span data-stu-id="01d3f-290">Optimization Hints and Data Types</span></span>  
 <span data-ttu-id="01d3f-291">노드를 XQuery 데이터 형식 또는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터 형식으로 인덱싱할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="01d3f-291">You can index nodes as XQuery data types or as [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data types.</span></span> <span data-ttu-id="01d3f-292">다음 표에서는 각 데이터 형식에서 지원되는 최적화 힌트를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="01d3f-292">The following table shows which optimization hints are supported with each data type.</span></span>  
  
|<span data-ttu-id="01d3f-293">최적화 힌트</span><span class="sxs-lookup"><span data-stu-id="01d3f-293">Optimization hint</span></span>|<span data-ttu-id="01d3f-294">XQuery 데이터 형식</span><span class="sxs-lookup"><span data-stu-id="01d3f-294">XQuery data types</span></span>|<span data-ttu-id="01d3f-295">SQL 데이터 형식</span><span class="sxs-lookup"><span data-stu-id="01d3f-295">SQL data types</span></span>|  
|-----------------------|-----------------------|--------------------|  
|<span data-ttu-id="01d3f-296">**node()**</span><span class="sxs-lookup"><span data-stu-id="01d3f-296">**node()**</span></span>|<span data-ttu-id="01d3f-297">예</span><span class="sxs-lookup"><span data-stu-id="01d3f-297">Yes</span></span>|<span data-ttu-id="01d3f-298">예</span><span class="sxs-lookup"><span data-stu-id="01d3f-298">No</span></span>|  
|<span data-ttu-id="01d3f-299">**SINGLETON**</span><span class="sxs-lookup"><span data-stu-id="01d3f-299">**SINGLETON**</span></span>|<span data-ttu-id="01d3f-300">예</span><span class="sxs-lookup"><span data-stu-id="01d3f-300">Yes</span></span>|<span data-ttu-id="01d3f-301">예</span><span class="sxs-lookup"><span data-stu-id="01d3f-301">Yes</span></span>|  
|<span data-ttu-id="01d3f-302">**DATA TYPE**</span><span class="sxs-lookup"><span data-stu-id="01d3f-302">**DATA TYPE**</span></span>|<span data-ttu-id="01d3f-303">예</span><span class="sxs-lookup"><span data-stu-id="01d3f-303">Yes</span></span>|<span data-ttu-id="01d3f-304">예</span><span class="sxs-lookup"><span data-stu-id="01d3f-304">No</span></span>|  
|<span data-ttu-id="01d3f-305">**MAXLENGTH**</span><span class="sxs-lookup"><span data-stu-id="01d3f-305">**MAXLENGTH**</span></span>|<span data-ttu-id="01d3f-306">예</span><span class="sxs-lookup"><span data-stu-id="01d3f-306">Yes</span></span>|<span data-ttu-id="01d3f-307">예</span><span class="sxs-lookup"><span data-stu-id="01d3f-307">No</span></span>|  
  
### <a name="node-optimization-hint"></a><span data-ttu-id="01d3f-308">node() 최적화 힌트</span><span class="sxs-lookup"><span data-stu-id="01d3f-308">node() optimization hint</span></span>  
 <span data-ttu-id="01d3f-309">적용 대상: XQuery 데이터 형식</span><span class="sxs-lookup"><span data-stu-id="01d3f-309">Applies to: XQuery data types</span></span>  
  
 <span data-ttu-id="01d3f-310">node() 최적화를 사용하여 일반 쿼리를 평가하는 데 필요 없는 값을 가진 노드를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="01d3f-310">You can use the node() optimization to specify a node whose value is not required to evaluate the typical query.</span></span> <span data-ttu-id="01d3f-311">이 힌트는 일반 쿼리가 노드의 존재 여부를 평가하기만 하면 될 때 스토리지 요구 사항을 줄여줍니다.</span><span class="sxs-lookup"><span data-stu-id="01d3f-311">This hint reduces storage requirements when the typical query only has to evaluate the existence of the node.</span></span> <span data-ttu-id="01d3f-312">기본적으로 선택적 XML 인덱스는 복잡한 노드 유형을 제외하고 승격된 모든 노드의 값을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="01d3f-312">(By default, a selective XML index stores the value for all promoted nodes, except complex node types.)</span></span>  
  
 <span data-ttu-id="01d3f-313">다음과 같은 예제를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="01d3f-313">Consider the following example:</span></span>  
  
```sql  
SELECT T.record FROM myXMLTable T  
WHERE T.xmldata.exist('/a/b[./c=5]') = 1  
```  
  
 <span data-ttu-id="01d3f-314">선택적 XML 인덱스를 사용하여 이 쿼리를 평가하려면 `b` 및 `c`노드를 승격시킵니다.</span><span class="sxs-lookup"><span data-stu-id="01d3f-314">To use a selective XML index to evaluate this query, promote nodes `b` and `c`.</span></span> <span data-ttu-id="01d3f-315">그러나 `b` 노드의 값이 필요 없기 때문에 node() 힌트를 다음 구문과 함께 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="01d3f-315">However, since the value of node `b` is not required, you can use the node() hint with the following syntax:</span></span>  
  
 `/a/b/ as node()`  
  
 <span data-ttu-id="01d3f-316">쿼리에 node() 힌트를 사용하여 인덱싱된 노드의 값이 필요한 경우에는 선택적 XML 인덱스를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="01d3f-316">If a query requires the value of a node that has been indexed with the node() hint, then the selective XML index cannot be used.</span></span>  
  
### <a name="singleton-optimization-hint"></a><span data-ttu-id="01d3f-317">SINGLETON 최적화 힌트</span><span class="sxs-lookup"><span data-stu-id="01d3f-317">SINGLETON optimization hint</span></span>  
 <span data-ttu-id="01d3f-318">적용 대상: XQuery 또는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터 형식</span><span class="sxs-lookup"><span data-stu-id="01d3f-318">Applies to: XQuery or [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data types</span></span>  
  
 <span data-ttu-id="01d3f-319">SINGLETON 최적화 힌트는 노드의 카디널리티를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="01d3f-319">The SINGLETON optimization hint specifies the cardinality of a node.</span></span> <span data-ttu-id="01d3f-320">이 힌트를 사용하면 노드가 해당 부모 노드 또는 상위 항목에 최대 한 번만 표시된다는 것을 미리 알 수 있기 때문에 쿼리 성능이 향상됩니다.</span><span class="sxs-lookup"><span data-stu-id="01d3f-320">This hint improves query performance since it is known in advance that a node appears at most one time within its parent or ancestor.</span></span>  
  
 <span data-ttu-id="01d3f-321">이 항목의 [샘플 XML 문서](#sample) 를 살펴보십시오.</span><span class="sxs-lookup"><span data-stu-id="01d3f-321">Consider the [sample XML document](#sample) in this topic.</span></span>  
  
 <span data-ttu-id="01d3f-322">선택적 XML 인덱스를 사용하여 이 문서를 쿼리하려면 `d` 노드에 대해 SINGLETON 힌트를 지정하면 됩니다. 이는 이 노드가 해당 부모 노드에 최대 한 번만 표시되기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="01d3f-322">To use a selective XML index to query this document, you can specify the SINGLETON hint for node `d` since it appears at most one time within its parent.</span></span>  
  
 <span data-ttu-id="01d3f-323">SINGLETON 힌트가 지정되었지만 노드가 해당 부모 노드 또는 상위 항목에 두 번 이상 표시되면 기존 데이터에 대한 인덱스를 만들거나 새 데이터에 대한 쿼리를 실행할 때 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="01d3f-323">If the SINGLETON hint has been specified, but a node appears more than one time within its parent or ancestor, then an error is raised when you create the index (for existing data) or when you run a query (for new data).</span></span>  
  
### <a name="data-type-optimization-hint"></a><span data-ttu-id="01d3f-324">DATA TYPE 최적화 힌트</span><span class="sxs-lookup"><span data-stu-id="01d3f-324">DATA TYPE optimization hint</span></span>  
 <span data-ttu-id="01d3f-325">적용 대상: XQuery 데이터 형식</span><span class="sxs-lookup"><span data-stu-id="01d3f-325">Applies to: XQuery data types</span></span>  
  
 <span data-ttu-id="01d3f-326">DATA TYPE 최적화 힌트를 사용하면 인덱싱된 노드에 대해 XQuery 또는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터 형식을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="01d3f-326">The DATA TYPE optimization hint lets you specify an XQuery or a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data type for the indexed node.</span></span> <span data-ttu-id="01d3f-327">이 데이터 형식은 선택적 XML 인덱스의 데이터 테이블에서 인덱싱된 노드에 해당하는 열에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="01d3f-327">The data type is used for the column in the data table of the selective XML index that corresponds to the indexed node.</span></span>  
  
 <span data-ttu-id="01d3f-328">기존 값을 지정된 데이터 형식으로 캐스팅하는 작업이 실패해도 인덱스에 대한 삽입 작업은 실패하지 않지만 인덱스의 데이터 테이블에 null 값이 삽입됩니다.</span><span class="sxs-lookup"><span data-stu-id="01d3f-328">When casting an existing value to the specified data type fails, the insert operation (into the index) does not fail; however, a null value is inserted into the data table of the index.</span></span>  
  
### <a name="maxlength-optimization-hint"></a><span data-ttu-id="01d3f-329">MAXLENGTH 최적화 힌트</span><span class="sxs-lookup"><span data-stu-id="01d3f-329">MAXLENGTH optimization hint</span></span>  
 <span data-ttu-id="01d3f-330">적용 대상: XQuery 데이터 형식</span><span class="sxs-lookup"><span data-stu-id="01d3f-330">Applies to: XQuery data types</span></span>  
  
 <span data-ttu-id="01d3f-331">MAXLENGTH 최적화 힌트를 사용하면 xs:string 데이터의 길이를 제한할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="01d3f-331">The MAXLENGTH optimization hint lets you limit the length of xs:string data.</span></span> <span data-ttu-id="01d3f-332">VARCHAR 또는 NVARCHAR 데이터 형식을 지정할 때 길이를 지정하므로 MAXLENGTH는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터 형식과는 관련이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="01d3f-332">MAXLENGTH is not relevant for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data types since you specify the length when you specify the VARCHAR or NVARCHAR date types.</span></span>  
  
 <span data-ttu-id="01d3f-333">기존 문자열이 지정된 MAXLENGTH보다 길면 인덱스에 값을 삽입하는 작업이 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="01d3f-333">When an existing string is longer than the specified MAXLENGTH, then inserting that value into the index fails.</span></span>  
  

  
##  <a name="sample-xml-document-for-examples"></a><a name="sample"></a> <span data-ttu-id="01d3f-334">예제용 샘플 XML 문서</span><span class="sxs-lookup"><span data-stu-id="01d3f-334">Sample XML Document for Examples</span></span>  
 <span data-ttu-id="01d3f-335">다음 샘플 XML 문서는 이 항목의 예에서 참조됩니다.</span><span class="sxs-lookup"><span data-stu-id="01d3f-335">The following sample XML document is referenced in the examples in this topic:</span></span>  
  
```xml  
<a>  
    <b>  
         <c atc="aa">10</c>  
         <c atc="bb">15</c>  
         <d atd1="dd" atd2="ddd">md </d>  
    </b>  
     <b>  
        <c></c>  
        <c atc="">117</c>  
     </b>  
</a>  
```  
  

  
## <a name="see-also"></a><span data-ttu-id="01d3f-336">참고 항목</span><span class="sxs-lookup"><span data-stu-id="01d3f-336">See Also</span></span>  
 <span data-ttu-id="01d3f-337">[SXI&#40;선택적 XML 인덱스&#41;](../xml/selective-xml-indexes-sxi.md) </span><span class="sxs-lookup"><span data-stu-id="01d3f-337">[Selective XML Indexes &#40;SXI&#41;](../xml/selective-xml-indexes-sxi.md) </span></span>  
 [<span data-ttu-id="01d3f-338">선택적 XML 인덱스 만들기, 변경 및 삭제</span><span class="sxs-lookup"><span data-stu-id="01d3f-338">Create, Alter, and Drop Selective XML Indexes</span></span>](../xml/create-alter-and-drop-selective-xml-indexes.md)  
  
  
