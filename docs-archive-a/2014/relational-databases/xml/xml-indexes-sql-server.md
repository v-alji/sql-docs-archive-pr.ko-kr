---
title: XML 인덱스(SQL Server) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- removing indexes
- deleting indexes
- secondary indexes [XML in SQL Server]
- xml data type [SQL Server], indexes
- dropping indexes
- PATH index
- DROP_EXISTING clause
- XML [SQL Server], indexes
- primary indexes [XML in SQL Server]
- indexes [SQL Server], XML
- XML indexes [SQL Server], secondary
- BLOBs, XML indexes
- disabling indexes
- XML indexes [SQL Server], modifying
- XML indexes [SQL Server]
- XML indexes [SQL Server], primary
- modifying indexes
- XML indexes [SQL Server], dropping
- VALUE index
- XML indexes [SQL Server], xml data type
- PROPERTY index
- XML indexes [SQL Server], creating
ms.assetid: f5c9209d-b3f3-4543-b30b-01365a5e7333
author: rothja
ms.author: jroth
ms.openlocfilehash: bf9a33bc18790bf8821d778746a708f78bbb3d8f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652672"
---
# <a name="xml-indexes-sql-server"></a><span data-ttu-id="583bd-102">XML 인덱스(SQL Server)</span><span class="sxs-lookup"><span data-stu-id="583bd-102">XML Indexes (SQL Server)</span></span>
  <span data-ttu-id="583bd-103">XML 인덱스를 `xml` 데이터 형식의 열에 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="583bd-103">XML indexes can be created on `xml` data type columns.</span></span> <span data-ttu-id="583bd-104">그러면 열에 있는 XML 인스턴스에 대해 모든 태그, 값 및 경로가 인덱싱되어 쿼리 성능이 향상됩니다.</span><span class="sxs-lookup"><span data-stu-id="583bd-104">They index all tags, values and paths over the XML instances in the column and benefit query performance.</span></span> <span data-ttu-id="583bd-105">다음 경우에 애플리케이션에서 XML 인덱스를 활용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="583bd-105">Your application may benefit from an XML index in the following situations:</span></span>  
  
-   <span data-ttu-id="583bd-106">XML 열의 쿼리가 작업에서 일반적입니다.</span><span class="sxs-lookup"><span data-stu-id="583bd-106">Queries on XML columns are common in your workload.</span></span> <span data-ttu-id="583bd-107">데이터를 수정하는 동안 XML 인덱스 유지 관리 비용이 고려되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="583bd-107">XML index maintenance cost during data modification must be considered.</span></span>  
  
-   <span data-ttu-id="583bd-108">XML 값이 비교적 크며 검색된 부분은 비교적 작습니다.</span><span class="sxs-lookup"><span data-stu-id="583bd-108">Your XML values are relatively large and the retrieved parts are relatively small.</span></span> <span data-ttu-id="583bd-109">인덱스를 작성하면 런타임 시 전체 데이터의 구문 분석이 방지되므로 인덱스 조회를 통해 쿼리를 효율적으로 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="583bd-109">Building the index avoids parsing the whole data at run time and benefits index lookups for efficient query processing.</span></span>  
  
 <span data-ttu-id="583bd-110">XML 인덱스는 다음 범주로 구분됩니다.</span><span class="sxs-lookup"><span data-stu-id="583bd-110">XML indexes fall into the following categories:</span></span>  
  
-   <span data-ttu-id="583bd-111">기본 XML 인덱스</span><span class="sxs-lookup"><span data-stu-id="583bd-111">Primary XML index</span></span>  
  
-   <span data-ttu-id="583bd-112">보조 XML 인덱스</span><span class="sxs-lookup"><span data-stu-id="583bd-112">Secondary XML index</span></span>  
  
 <span data-ttu-id="583bd-113">`xml` 형식 열의 첫 번째 인덱스는 기본 XML 인덱스여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="583bd-113">The first index on the `xml` type column must be the primary XML index.</span></span> <span data-ttu-id="583bd-114">기본 XML 인덱스를 사용하면 PATH, VALUE 및 PROPERTY 형식의 보조 인덱스가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="583bd-114">Using the primary XML index, the following types of secondary indexes are supported: PATH, VALUE, and PROPERTY.</span></span> <span data-ttu-id="583bd-115">이러한 보조 인덱스는 쿼리 유형에 따라 쿼리 성능을 향상시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="583bd-115">Depending on the type of queries, these secondary indexes might help improve query performance.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="583bd-116">데이터베이스 옵션이 `xml` 데이터 형식 작업에 대해 제대로 설정되지 않을 경우 XML 인덱스를 만들거나 수정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="583bd-116">You cannot create or modify an XML index unless the database options are set correctly for working with the `xml` data type.</span></span> <span data-ttu-id="583bd-117">자세한 내용은 [XML 열에 전체 텍스트 검색 사용](use-full-text-search-with-xml-columns.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="583bd-117">For more information, see [Use Full-Text Search with XML Columns](use-full-text-search-with-xml-columns.md).</span></span>  
  
 <span data-ttu-id="583bd-118">XML 인스턴스는 BLOB(Binary Large Object)으로 `xml` 형식 열에 저장되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="583bd-118">XML instances are stored in `xml` type columns as large binary objects (BLOBs).</span></span> <span data-ttu-id="583bd-119">이러한 XML 인스턴스는 크기가 클 수 있으며 `xml` 데이터 형식 인스턴스의 저장된 이진 표현은 최대 2GB까지 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="583bd-119">These XML instances can be large, and the stored binary representation of `xml` data type instances can be up to 2 GB.</span></span> <span data-ttu-id="583bd-120">이러한 BLOB은 인덱스 없이 런타임 시 단편화되어 쿼리를 계산할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="583bd-120">Without an index, these binary large objects are shredded at run time to evaluate a query.</span></span> <span data-ttu-id="583bd-121">이 단편화 작업에는 시간이 많이 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="583bd-121">This shredding can be time-consuming.</span></span> <span data-ttu-id="583bd-122">예를 들어 다음 쿼리를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="583bd-122">For example, consider the following query:</span></span>  
  
```  
WITH XMLNAMESPACES ('https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription' AS "PD")  
  
SELECT CatalogDescription.query('  
  /PD:ProductDescription/PD:Summary  
') as Result  
FROM Production.ProductModel  
WHERE CatalogDescription.exist ('/PD:ProductDescription/@ProductModelID[.="19"]') = 1  
```  
  
 <span data-ttu-id="583bd-123">`WHERE` 절의 조건에 맞는 XML 인스턴스를 선택할 수 있도록 `Production.ProductModel` 테이블의 각 행에서 XML BLOB이 런타임 시 단편화됩니다.</span><span class="sxs-lookup"><span data-stu-id="583bd-123">To select the XML instances that satisfy the condition in the `WHERE` clause, the XML binary large object (BLOB) in each row of table `Production.ProductModel` is shredded at run time.</span></span> <span data-ttu-id="583bd-124">그런 다음 `(/PD:ProductDescription/@ProductModelID[.="19"]`메서드의 `exist()` ) 식이 계산됩니다.</span><span class="sxs-lookup"><span data-stu-id="583bd-124">Then, the expression `(/PD:ProductDescription/@ProductModelID[.="19"]`) in the `exist()` method is evaluated.</span></span> <span data-ttu-id="583bd-125">이러한 런타임 단편화는 열에 저장된 인스턴스의 크기와 수에 따라 비용이 많이 들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="583bd-125">This run-time shredding can be costly, depending on the size and number of instances stored in the column.</span></span>  
  
 <span data-ttu-id="583bd-126">XML BLOB을 쿼리하는 것이 사용자의 애플리케이션 환경에서 일반적인 경우 이것은 `xml` 형식 열을 인덱싱하는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="583bd-126">If querying XML binary large objects (BLOBs) is common in your application environment, it helps to index the `xml` type columns.</span></span> <span data-ttu-id="583bd-127">그러나 데이터 수정 중 인덱스를 유지 관리하는 비용이 듭니다.</span><span class="sxs-lookup"><span data-stu-id="583bd-127">However, there is a cost associated with maintaining the index during data modification.</span></span>  
  
## <a name="primary-xml-index"></a><span data-ttu-id="583bd-128">기본 XML 인덱스</span><span class="sxs-lookup"><span data-stu-id="583bd-128">Primary XML Index</span></span>  
 <span data-ttu-id="583bd-129">기본 XML 인덱스는 XML의 XML 인스턴스 내에 있는 모든 태그, 값 및 경로를 인덱싱합니다.</span><span class="sxs-lookup"><span data-stu-id="583bd-129">The primary XML index indexes all tags, values, and paths within the XML instances in an XML column.</span></span> <span data-ttu-id="583bd-130">기본 XML 인덱스를 만들려면 XML 열이 발생하는 테이블에는 테이블의 기본 키에 클러스터링된 인덱스가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="583bd-130">To create a primary XML index, the table in which the XML column occurs must have a clustered index on the primary key of the table.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="583bd-131">에서는 이 기본 키를 사용하여 기본 XML 인덱스에 있는 행과 XML 열을 포함하는 테이블에 있는 행의 상관 관계를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="583bd-131">uses this primary key to correlate rows in the primary XML index with rows in the table that contains the XML column.</span></span>  
  
 <span data-ttu-id="583bd-132">기본 XML 인덱스는 `xml` 데이터 형식 열의 XML BLOB을 지속적인 단편 형태로 표현한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="583bd-132">The primary XML index is a shredded and persisted representation of the XML BLOBs in the `xml` data type column.</span></span> <span data-ttu-id="583bd-133">인덱스는 열의 XML BLOB(Binary Large Object)마다 여러 개의 데이터 행을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="583bd-133">For each XML binary large object (BLOB) in the column, the index creates several rows of data.</span></span> <span data-ttu-id="583bd-134">인덱스의 행 수는 대략 XML BLOB의 노드 수와 같습니다.</span><span class="sxs-lookup"><span data-stu-id="583bd-134">The number of rows in the index is approximately equal to the number of nodes in the XML binary large object.</span></span> <span data-ttu-id="583bd-135">쿼리가 전체 XML 인스턴스를 검색할 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서는 XML 열의 인스턴스를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="583bd-135">When a query retrieves the full XML instance, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provides the instance from the XML column.</span></span> <span data-ttu-id="583bd-136">XML 인스턴스 내의 쿼리에서는 기본 XML 인덱스를 사용하고 인덱스 자체를 사용하여 스칼라 값이나 XML 하위 트리를 반환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="583bd-136">Queries within XML instances use the primary XML index, and can return scalar values or XML subtrees by using the index itself.</span></span>  
  
 <span data-ttu-id="583bd-137">각 행에는 다음 노드 정보를 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="583bd-137">Each row stores the following node information:</span></span>  
  
-   <span data-ttu-id="583bd-138">요소 또는 특성 이름과 같은 태그 이름</span><span class="sxs-lookup"><span data-stu-id="583bd-138">Tag name such as an element or attribute name.</span></span>  
  
-   <span data-ttu-id="583bd-139">노드 값</span><span class="sxs-lookup"><span data-stu-id="583bd-139">Node value.</span></span>  
  
-   <span data-ttu-id="583bd-140">요소 노드, 특성 노드 또는 텍스트 노드와 같은 노드 유형</span><span class="sxs-lookup"><span data-stu-id="583bd-140">Node type such as an element node, attribute node, or text node.</span></span>  
  
-   <span data-ttu-id="583bd-141">내부 노드 식별자에 의해 표현되는 문서 순서 정보</span><span class="sxs-lookup"><span data-stu-id="583bd-141">Document order information, represented by an internal node identifier.</span></span>  
  
-   <span data-ttu-id="583bd-142">각 노드에서 XML 트리의 루트에 대한 경로.</span><span class="sxs-lookup"><span data-stu-id="583bd-142">Path from each node to the root of the XML tree.</span></span> <span data-ttu-id="583bd-143">이 열은 쿼리의 경로 식으로 검색됩니다.</span><span class="sxs-lookup"><span data-stu-id="583bd-143">This column is searched for path expressions in the query.</span></span>  
  
-   <span data-ttu-id="583bd-144">기본 테이블의 기본 키.</span><span class="sxs-lookup"><span data-stu-id="583bd-144">Primary key of the base table.</span></span> <span data-ttu-id="583bd-145">기본 테이블의 기본 키는 기본 테이블과 백 조인을 위한 기본 XML 인덱스에 복제되고 해당 기본 테이블의 기본 키에 있는 최대 열 수는 15개로 제한됩니다.</span><span class="sxs-lookup"><span data-stu-id="583bd-145">The primary key of the base table is duplicated in the primary XML index for a back join with the base table, and the maximum number of columns in the primary key of the base table is limited to 15.</span></span>  
  
 <span data-ttu-id="583bd-146">이 노드 정보는 지정된 쿼리에 대해 XML 결과를 계산 및 구성하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="583bd-146">This node information is used to evaluate and construct XML results for a specified query.</span></span> <span data-ttu-id="583bd-147">최적화를 위해 태그 이름과 노드 유형 정보는 정수 값으로 인코딩되고 경로 열에서는 같은 인코딩을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="583bd-147">For optimization purposes, the tag name and the node type information are encoded as integer values, and the Path column uses the same encoding.</span></span> <span data-ttu-id="583bd-148">또한 경로는 경로 접미사가 알려져 있는 경우에만 경로에 일치할 수 있도록 반대 순서로 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="583bd-148">Also, paths are stored in reverse order to allow matching paths when only the path suffix is known.</span></span> <span data-ttu-id="583bd-149">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="583bd-149">For example:</span></span>  
  
-   <span data-ttu-id="583bd-150">`//ContactRecord/PhoneNumber` - 마지막 두 단계만 알려져 있는 경우</span><span class="sxs-lookup"><span data-stu-id="583bd-150">`//ContactRecord/PhoneNumber` where only the last two steps are known</span></span>  
  
 <span data-ttu-id="583bd-151">또는</span><span class="sxs-lookup"><span data-stu-id="583bd-151">OR</span></span>  
  
-   <span data-ttu-id="583bd-152">`/Book/*/Title` 와일드카드 문자(`*`)가 식 중간에 지정되어 있는 경우</span><span class="sxs-lookup"><span data-stu-id="583bd-152">`/Book/*/Title` where the wildcard character (`*`) is specified in the middle of the expression.</span></span>  
  
 <span data-ttu-id="583bd-153">쿼리 프로세서에서는 [xml Data Type Methods](/sql/t-sql/xml/xml-data-type-methods) 를 포함하는 쿼리에 대해 기본 XML 인덱스를 사용하고 기본 인덱스 자체에서 스칼라 값이나 XML 하위 트리를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="583bd-153">The query processor uses the primary XML index for queries that involve [xml Data Type Methods](/sql/t-sql/xml/xml-data-type-methods) and returns either scalar values or the XML subtrees from the primary index itself.</span></span> <span data-ttu-id="583bd-154">이 인덱스는 XML 인스턴스를 재구성하는 데 필요한 모든 정보를 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="583bd-154">(This index stores all the necessary information to reconstruct the XML instance.)</span></span>  
  
 <span data-ttu-id="583bd-155">예를 들어 다음 쿼리는 `CatalogDescription``xml` 테이블의 유형 열에 저장 된 요약 정보를 반환 합니다 `ProductModel` .</span><span class="sxs-lookup"><span data-stu-id="583bd-155">For example, the following query returns summary information stored in the `CatalogDescription``xml` type column in the `ProductModel` table.</span></span> <span data-ttu-id="583bd-156">이 쿼리는 카탈로그 설명에 <`Features`> 설명도 저장되어 있는 제품 모델에 대해서만 <`Summary`> 정보를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="583bd-156">The query returns <`Summary`> information only for product models whose catalog description also stores the <`Features`> description.</span></span>  
  
```  
WITH XMLNAMESPACES ('https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription' AS "PD")SELECT CatalogDescription.query('  /PD:ProductDescription/PD:Summary') as ResultFROM Production.ProductModelWHERE CatalogDescription.exist ('/PD:ProductDescription/PD:Features') = 1  
```  
  
 <span data-ttu-id="583bd-157">기본 XML 인덱스에 관해 기본 테이블에서 각 XML BLOB 인스턴스를 단편화하는 대신, 각 XML BLOB에 해당하는 인덱스의 행이 `exist()` 메서드에 지정된 식에 대해 순서대로 검색됩니다.</span><span class="sxs-lookup"><span data-stu-id="583bd-157">With regard to the primary XML index, instead of shredding each XML binary large object instance in the base table, the rows in the index that correspond to each XML binary large object are searched sequentially for the expression specified in the `exist()` method.</span></span> <span data-ttu-id="583bd-158">경로를 인덱스의 경로 열에서 찾은 경우 <`Summary`> 요소와 그 하위 트리는 기본 XML 인덱스에서 함께 검색되고 `query()` 메서드의 결과로 XML BLOB로 변환됩니다.</span><span class="sxs-lookup"><span data-stu-id="583bd-158">If the path is found in the Path column in the index, the <`Summary`> element together with its subtrees is retrieved from the primary XML index and converted into an XML binary large object as the result of the `query()` method.</span></span>  
  
 <span data-ttu-id="583bd-159">전체 XML 인스턴스를 검색할 때는 기본 XML 인덱스가 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="583bd-159">Note that the primary XML index is not used when retrieving a full XML instance.</span></span> <span data-ttu-id="583bd-160">예를 들어 다음 쿼리는 테이블에서 특정 제품 모델에 대한 제조 지침을 나타내는 전체 XML 인스턴스를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="583bd-160">For example, the following query retrieves from the table the whole XML instance that describes the manufacturing instructions for a specific product model.</span></span>  
  
```  
USE AdventureWorks2012;SELECT InstructionsFROM Production.ProductModel WHERE ProductModelID=7;  
```  
  
## <a name="secondary-xml-indexes"></a><span data-ttu-id="583bd-161">보조 XML 인덱스</span><span class="sxs-lookup"><span data-stu-id="583bd-161">Secondary XML Indexes</span></span>  
 <span data-ttu-id="583bd-162">검색 성능을 향상시키기 위해 보조 XML 인덱스를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="583bd-162">To enhance search performance, you can create secondary XML indexes.</span></span> <span data-ttu-id="583bd-163">기본 XML 인덱스가 있어야 보조 인덱스를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="583bd-163">A primary XML index must first exist before you can create secondary indexes.</span></span> <span data-ttu-id="583bd-164">유형은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="583bd-164">These are the types:</span></span>  
  
-   <span data-ttu-id="583bd-165">PATH 보조 XML 인덱스</span><span class="sxs-lookup"><span data-stu-id="583bd-165">PATH secondary XML index</span></span>  
  
-   <span data-ttu-id="583bd-166">VALUE 보조 XML 인덱스</span><span class="sxs-lookup"><span data-stu-id="583bd-166">VALUE secondary XML index</span></span>  
  
-   <span data-ttu-id="583bd-167">PROPERTY 보조 XML 인덱스</span><span class="sxs-lookup"><span data-stu-id="583bd-167">PROPERTY secondary XML index</span></span>  
  
 <span data-ttu-id="583bd-168">다음은 하나 이상의 보조 인덱스를 만드는 데에 대한 몇 가지 지침입니다.</span><span class="sxs-lookup"><span data-stu-id="583bd-168">Following are some guidelines for creating one or more secondary indexes:</span></span>  
  
-   <span data-ttu-id="583bd-169">작업에서 XML 열에 경로 식이 중요하게 사용되는 경우 PATH 보조 XML 인덱스는 작업 속도를 높일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="583bd-169">If your workload uses path expressions significantly on XML columns, the PATH secondary XML index is likely to speed up your workload.</span></span> <span data-ttu-id="583bd-170">가장 일반적인 경우는 Transact-SQL의 WHERE 절에서 XML 열에 대해 **exist()** 메서드를 사용하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="583bd-170">The most common case is the use of the **exist()** method on XML columns in the WHERE clause of Transact-SQL.</span></span>  
  
-   <span data-ttu-id="583bd-171">작업에 경로 식을 사용하여 개별적인 XML 인스턴스로부터 여러 값을 검색하는 경우 PROPERTY 인덱스에 있는 각 XML 인스턴스 내의 경로를 클러스터링하면 도움이 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="583bd-171">If your workload retrieves multiple values from individual XML instances by using path expressions, clustering paths within each XML instance in the PROPERTY index may be helpful.</span></span> <span data-ttu-id="583bd-172">이러한 시나리오는 개체의 속성이 인출되고 해당 기본 키 값이 알려진 속성 모음 시나리오에서 일반적으로 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="583bd-172">This scenario typically occurs in a property bag scenario when properties of an object are fetched and its primary key value is known.</span></span>  
  
-   <span data-ttu-id="583bd-173">작업에 해당 값이 포함된 요소 또는 특성 이름을 알지 못하는 상태에서 XML 인스턴스 내의 값을 쿼리하는 작업이 포함되는 경우 VALUE 인덱스를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="583bd-173">If your workload involves querying for values within XML instances without knowing the element or attribute names that contain those values, you may want to create the VALUE index.</span></span> <span data-ttu-id="583bd-174">이러한 경우는 \<author> 요소가 계층 구조의 어느 수준에서도 발생할 수 있는 //author[last-name="Howard"] 같은 하위 항목 축 조회 시에 일반적으로 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="583bd-174">This typically occurs with descendant axes lookups, such as //author[last-name="Howard"], where \<author> elements can occur at any level of the hierarchy.</span></span> <span data-ttu-id="583bd-175">쿼리가 "novel" 값이 있는 일부 특성을 포함하는 \<book> 요소를 조회하는 /book [@\* = "novel"]과 같은 와일드카드 쿼리에서도 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="583bd-175">It also occurs in wildcard queries, such as /book [@\* = "novel"], where the query looks for \<book> elements that have some attribute having the value "novel".</span></span>  
  
### <a name="path-secondary-xml-index"></a><span data-ttu-id="583bd-176">PATH 보조 XML 인덱스</span><span class="sxs-lookup"><span data-stu-id="583bd-176">PATH Secondary XML Index</span></span>  
 <span data-ttu-id="583bd-177">쿼리에서 일반적으로 `xml` 유형 열에 경로 식을 지정하는 경우에는 PATH 보조 인덱스로 검색 속도를 높일 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="583bd-177">If your queries generally specify path expressions on `xml` type columns, a PATH secondary index may be able to speed up the search.</span></span> <span data-ttu-id="583bd-178">이 항목의 앞에서 설명한 대로 기본 인덱스는 **exist()** 메서드를 WHERE 절에 지정하는 쿼리가 있는 경우에 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="583bd-178">As described earlier in this topic, the primary index is helpful when you have queries that specify **exist()** method in the WHERE clause.</span></span> <span data-ttu-id="583bd-179">또한 PATH 보조 인덱스를 추가하면 이러한 쿼리에서 검색 성능을 향상시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="583bd-179">If you add a PATH secondary index, you may also improve the search performance in such queries.</span></span>  
  
 <span data-ttu-id="583bd-180">기본 XML 인덱스에서 런타임 시 XML BLOB의 단편화는 피할 수 있지만 경로 식을 사용하는 쿼리의 최대 성능은 제공할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="583bd-180">Although a primary XML index avoids having to shred the XML binary large objects at run time, it may not provide the best performance for queries based on path expressions.</span></span> <span data-ttu-id="583bd-181">XML BLOB에 해당하는 기본 XML 인덱스의 모든 행이 대규모의 XML 인스턴스에 대해 순서대로 검색되기 때문에 순차적 검색의 속도가 느려질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="583bd-181">Because all rows in the primary XML index corresponding to an XML binary large object are searched sequentially for large XML instances, the sequential search may be slow.</span></span> <span data-ttu-id="583bd-182">이 경우 기본 인덱스의 경로 값과 노드 값에 보조 인덱스를 만들면 인덱스 검색의 속도가 현저히 빨라질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="583bd-182">In this case, having a secondary index built on the path values and node values in the primary index can significantly speed up the index search.</span></span> <span data-ttu-id="583bd-183">PATH 보조 인덱스에서 경로 값 및 노드 값은 경로 검색 시 효율적으로 검색할 수 있는 키 열입니다.</span><span class="sxs-lookup"><span data-stu-id="583bd-183">In the PATH secondary index, the path and node values are key columns that allow for more efficient seeks when searching for paths.</span></span> <span data-ttu-id="583bd-184">쿼리 최적화 프로그램에서는 다음과 같은 식에 대해 PATH 인덱스를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="583bd-184">The query optimizer may use the PATH index for expressions such as those shown in the following:</span></span>  
  
-   <span data-ttu-id="583bd-185">`/root/Location` - 경로만 지정한 경우</span><span class="sxs-lookup"><span data-stu-id="583bd-185">`/root/Location` which specify only a path</span></span>  
  
 <span data-ttu-id="583bd-186">또는</span><span class="sxs-lookup"><span data-stu-id="583bd-186">OR</span></span>  
  
-   <span data-ttu-id="583bd-187">`/root/Location/@LocationID[.="10"]` - 경로 값과 노드 값이 모두 지정되어 있는 경우</span><span class="sxs-lookup"><span data-stu-id="583bd-187">`/root/Location/@LocationID[.="10"]` where both the path and the node value are specified.</span></span>  
  
 <span data-ttu-id="583bd-188">다음 쿼리에서는 PATH 인덱스가 유용하게 사용되는 경우를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="583bd-188">The following query shows where the PATH index is helpful:</span></span>  
  
```  
WITH XMLNAMESPACES ('https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription' AS "PD")  
  
SELECT CatalogDescription.query('  
  /PD:ProductDescription/PD:Summary  
') AS Result  
FROM Production.ProductModel  
WHERE CatalogDescription.exist ('/PD:ProductDescription/@ProductModelID[.="19"]') = 1  
```  
  
 <span data-ttu-id="583bd-189">쿼리에서 `/PD:ProductDescription/@ProductModelID` 메서드의 경로 식 `"19"` 및 `exist()` 값은 PATH 인덱스의 키 필드에 해당합니다.</span><span class="sxs-lookup"><span data-stu-id="583bd-189">In the query, the path expression `/PD:ProductDescription/@ProductModelID` and value `"19"` in the `exist()` method correspond to the key fields of the PATH index.</span></span> <span data-ttu-id="583bd-190">따라서 PATH 인덱스에서 직접 찾을 수 있고 기본 인덱스의 경로 값에 대한 순차적 검색보다 더 나은 검색 성능을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="583bd-190">This allows for direct seek in the PATH index and provides better search performance than the sequential search for path values in the primary index.</span></span>  
  
### <a name="value-secondary-xml-index"></a><span data-ttu-id="583bd-191">VALUE 보조 XML 인덱스</span><span class="sxs-lookup"><span data-stu-id="583bd-191">VALUE Secondary XML Index</span></span>  
 <span data-ttu-id="583bd-192">예를 들어 쿼리가 값을 기반으로 하는 `/Root/ProductDescription/@*[. = "Mountain Bike"]` 또는 `//ProductDescription[@Name = "Mountain Bike"]`이고 경로가 완전히 지정되지 않거나 와일드카드를 포함하는 경우에는 기본 XML 인덱스의 노드 값에 보조 XML 인덱스를 만들어 더 빠른 결과를 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="583bd-192">If queries are value based, for example, `/Root/ProductDescription/@*[. = "Mountain Bike"]` or `//ProductDescription[@Name = "Mountain Bike"]`, and the path is not fully specified or it includes a wildcard, you might obtain faster results by building a secondary XML index that is built on node values in the primary XML index.</span></span>  
  
 <span data-ttu-id="583bd-193">VALUE 인덱스의 키 열은 기본 XML 인덱스의 노드 값 및 경로입니다.</span><span class="sxs-lookup"><span data-stu-id="583bd-193">The key columns of the VALUE index are (node value and path) of the primary XML index.</span></span> <span data-ttu-id="583bd-194">값을 포함하는 요소 또는 특성 이름을 알 필요 없이 XML 인스턴스에서 해당 값을 쿼리하는 작업이 포함되는 경우 VALUE 인덱스가 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="583bd-194">If your workload involves querying for values from XML instances without knowing the element or attribute names that contain the values, a VALUE index may be useful.</span></span> <span data-ttu-id="583bd-195">예를 들어 다음 식에 VALUE 인덱스가 있는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="583bd-195">For example, the following expression will benefit from having a VALUE index:</span></span>  
  
-   <span data-ttu-id="583bd-196">`//author[LastName="someName"]` - <`LastName`> 요소의 값은 알지만 <`author`> 부모가 아무 곳에서나 발생할 수 있는 경우</span><span class="sxs-lookup"><span data-stu-id="583bd-196">`//author[LastName="someName"]` where you know the value of the <`LastName`> element, but the <`author`> parent can occur anywhere.</span></span>  
  
-   <span data-ttu-id="583bd-197">`/book[@* = "someValue"]` - 쿼리가 `"someValue"` 값이 있는 일부 특성을 가진 <`book`> 요소를 찾는 경우</span><span class="sxs-lookup"><span data-stu-id="583bd-197">`/book[@* = "someValue"]` where the query looks for the <`book`> element that has some attribute having the value `"someValue"`.</span></span>  
  
 <span data-ttu-id="583bd-198">다음 쿼리에서는 `ContactID` 테이블에서 `Contact` 를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="583bd-198">The following query returns `ContactID` from the `Contact` table.</span></span> <span data-ttu-id="583bd-199">`WHERE`절은 유형 열에서 값을 찾는 필터를 지정 합니다 `AdditionalContactInfo``xml` .</span><span class="sxs-lookup"><span data-stu-id="583bd-199">The `WHERE` clause specifies a filter that looks for values in the `AdditionalContactInfo``xml` type column.</span></span> <span data-ttu-id="583bd-200">연락처 ID는 해당되는 추가 연락처 정보 XML BLOB에 특정 전화 번호가 포함되는 경우에만 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="583bd-200">The contact IDs are returned only if the corresponding additional contact information XML binary large object includes a specific telephone number.</span></span> <span data-ttu-id="583bd-201"><`telephoneNumber`> 요소가 XML의 아무 위치에서나 나타날 수 있기 때문에 경로 식은 하위 또는 자체 축을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="583bd-201">Because the <`telephoneNumber`> element may appear anywhere in the XML, the path expression specifies the descendent-or-self axis.</span></span>  
  
```  
WITH XMLNAMESPACES (  
  'https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactInfo' AS CI,  
  'https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes' AS ACT)  
  
SELECT ContactID   
FROM   Person.Contact  
WHERE  AdditionalContactInfo.exist('//ACT:telephoneNumber/ACT:number[.="111-111-1111"]') = 1  
```  
  
 <span data-ttu-id="583bd-202">이 경우 <`number`>에 대한 검색 값을 알지만 이 값은 <`telephoneNumber`> 요소의 자식으로 XML 인스턴스의 아무 위치에서나 나타날 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="583bd-202">In this situation, the search value for <`number`> is known, but it can appear anywhere in the XML instance as a child of the <`telephoneNumber`> element.</span></span> <span data-ttu-id="583bd-203">이러한 유형의 쿼리를 사용하면 특정 값에 기반한 인덱스 조회의 장점을 활용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="583bd-203">This kind of query might benefit from an index lookup based on a specific value.</span></span>  
  
### <a name="property-secondary-index"></a><span data-ttu-id="583bd-204">PROPERTY 보조 인덱스</span><span class="sxs-lookup"><span data-stu-id="583bd-204">PROPERTY Secondary Index</span></span>  
 <span data-ttu-id="583bd-205">개별 XML 인스턴스에서 하나 이상의 값을 검색하는 쿼리는 PROPERTY 인덱스의 장점을 활용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="583bd-205">Queries that retrieve one or more values from individual XML instances might benefit from a PROPERTY index.</span></span> <span data-ttu-id="583bd-206">이 시나리오는 형식의 **value ()** 메서드를 사용 하 여 개체 속성을 검색 하 `xml` 고 개체의 기본 키 값을 알고 있는 경우에 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="583bd-206">This scenario occurs when you retrieve object properties by using the **value()** method of the `xml` type and when the primary key value of the object is known.</span></span>  
  
 <span data-ttu-id="583bd-207">PK가 기본 테이블의 기본 키인 기본 XML 인덱스의 열(PK, 경로 및 노드 값)에 PROPERTY XML 인덱스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="583bd-207">The PROPERTY index is built on columns (PK, Path and node value) of the primary XML index where PK is the primary key of the base table.</span></span>  
  
 <span data-ttu-id="583bd-208">예를 들어 제품 모델 `19`의 경우 다음 쿼리는 `ProductModelID` 메서드를 사용하여 `ProductModelName` 및 `value()` 특성 값을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="583bd-208">For example, for product model `19`, the following query retrieves the `ProductModelID` and `ProductModelName` attribute values using the `value()` method.</span></span> <span data-ttu-id="583bd-209">기본 XML 인덱스 또는 기타 보조 XML 인덱스를 사용하는 대신 PROPERTY 인덱스를 사용하면 더 빨리 실행될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="583bd-209">Instead of using the primary XML index or the other secondary XML indexes, the PROPERTY index may provide faster execution.</span></span>  
  
```  
WITH XMLNAMESPACES ('https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription' AS "PD")  
  
SELECT CatalogDescription.value('(/PD:ProductDescription/@ProductModelID)[1]', 'int') as ModelID,  
       CatalogDescription.value('(/PD:ProductDescription/@ProductModelName)[1]', 'varchar(30)') as ModelName          
FROM Production.ProductModel     
WHERE ProductModelID = 19  
```  
  
 <span data-ttu-id="583bd-210">이 항목의 뒷부분에서 설명 하는 차이점을 제외 하 고 유형 열에 XML 인덱스를 만드는 `xml` 것은 비-유형 열에 인덱스를 만드는 것과 비슷합니다 `xml` .</span><span class="sxs-lookup"><span data-stu-id="583bd-210">Except for the differences described later in this topic, creating an XML index on an`xml` type column is similar to creating an index on a non-`xml` type column.</span></span> <span data-ttu-id="583bd-211">다음 [!INCLUDE[tsql](../../includes/tsql-md.md)] DDL 문은 XML 인덱스의 작성 및 관리에 사용될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="583bd-211">The following [!INCLUDE[tsql](../../includes/tsql-md.md)] DDL statements can be used to create and manage XML indexes:</span></span>  
  
-   [<span data-ttu-id="583bd-212">CREATE INDEX&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="583bd-212">CREATE INDEX &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-index-transact-sql)  
  
-   [<span data-ttu-id="583bd-213">ALTER INDEX&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="583bd-213">ALTER INDEX &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-index-transact-sql)  
  
-   [<span data-ttu-id="583bd-214">DROP INDEX&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="583bd-214">DROP INDEX &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/drop-index-transact-sql)  
  
## <a name="getting-information-about-xml-indexes"></a><span data-ttu-id="583bd-215">XML 인덱스에 대한 정보 가져오기</span><span class="sxs-lookup"><span data-stu-id="583bd-215">Getting Information about XML Indexes</span></span>  
 <span data-ttu-id="583bd-216">XML 인덱스 항목은 인덱스 "type"이 3인 카탈로그 뷰 sys.indexes에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="583bd-216">XML index entries appear in the catalog view, sys.indexes, with the index "type" 3.</span></span> <span data-ttu-id="583bd-217">이름 열에는 XML 인덱스의 이름이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="583bd-217">The name column contains the name of the XML index.</span></span>  
  
 <span data-ttu-id="583bd-218">XML 인덱스는 또한 카탈로그 뷰 sys.xml_indexes에 기록됩니다.</span><span class="sxs-lookup"><span data-stu-id="583bd-218">XML indexes are also recorded in the catalog view, sys.xml_indexes.</span></span> <span data-ttu-id="583bd-219">여기에는 sys.indexes의 모든 열과 XML 인덱스에 유용한 특정 열이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="583bd-219">This contains all the columns of sys.indexes and some specific ones that are useful for XML indexes.</span></span> <span data-ttu-id="583bd-220">secondary_type 열에 있는 NULL 값은 기본 XML 인덱스를 나타냅니다. 'P', 'R' 및 'V' 값은 각각 PATH, PROPERTY 및 VALUE 보조 XML 인덱스를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="583bd-220">The value NULL in the column, secondary_type, indicates a primary XML index; the values 'P', 'R' and 'V' stand for PATH, PROPERTY, and VALUE secondary XML indexes, respectively.</span></span>  
  
 <span data-ttu-id="583bd-221">XML 인덱스의 공간 사용은 [sys.dm_db_index_physical_stats](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-index-physical-stats-transact-sql)테이블 반환 함수에서 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="583bd-221">The space use of XML indexes can be found in the table-valued function [sys.dm_db_index_physical_stats](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-index-physical-stats-transact-sql).</span></span> <span data-ttu-id="583bd-222">이 함수는 모든 인덱스 유형에 대해 사용된 디스크 페이지 수, 평균 행 크기(바이트) 및 레코드 수와 같은 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="583bd-222">It provides information, such as the number of disk pages occupied, average row size in bytes, and number of records, for all index types..</span></span> <span data-ttu-id="583bd-223">여기에는 XML 인덱스도 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="583bd-223">This also includes XML indexes.</span></span> <span data-ttu-id="583bd-224">이 정보는 각 데이터베이스 파티션에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="583bd-224">This information is available for each database partition.</span></span> <span data-ttu-id="583bd-225">XML 인덱스는 기본 테이블과 동일한 파티션 구성표 및 파티션 함수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="583bd-225">XML indexes use the same partitioning scheme and partitioning function of the base table.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="583bd-226">참고 항목</span><span class="sxs-lookup"><span data-stu-id="583bd-226">See Also</span></span>  
 <span data-ttu-id="583bd-227">[sys.dm_db_index_physical_stats&#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-index-physical-stats-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="583bd-227">[sys.dm_db_index_physical_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-index-physical-stats-transact-sql) </span></span>  
 [<span data-ttu-id="583bd-228">XML 데이터&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="583bd-228">XML Data &#40;SQL Server&#41;</span></span>](../xml/xml-data-sql-server.md)  
  
  
