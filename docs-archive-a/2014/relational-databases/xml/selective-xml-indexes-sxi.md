---
title: SXI(선택적 XML 인덱스) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
ms.assetid: 598ecdcd-084b-4032-81b2-eed6ae9f5d44
author: rothja
ms.author: jroth
ms.openlocfilehash: 37dd72c5de2892672dc9f63066075ab5e770d758
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660920"
---
# <a name="selective-xml-indexes-sxi"></a><span data-ttu-id="43894-102">SXI(선택적 XML 인덱스)</span><span class="sxs-lookup"><span data-stu-id="43894-102">Selective XML Indexes (SXI)</span></span>
  <span data-ttu-id="43894-103">선택적 XML 인덱스는 일반 XML 인덱스 외에 추가로 제공되는 또 다른 유형의 XML 인덱스입니다.</span><span class="sxs-lookup"><span data-stu-id="43894-103">Selective XML indexes are another type of XML index that is available to you in addition to ordinary XML indexes.</span></span> <span data-ttu-id="43894-104">선택적 XML 인덱스 기능의 목적은 다음과 같습니다</span><span class="sxs-lookup"><span data-stu-id="43894-104">The goals of the selective XML index feature are the following:</span></span>  
  
-   <span data-ttu-id="43894-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에 저장된 XML 데이터에 대한 쿼리 성능을 향상시킵니다.</span><span class="sxs-lookup"><span data-stu-id="43894-105">To improve the performance of queries over XML data stored in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="43894-106">대량의 XML 데이터 작업의 더 빠른 인덱싱을 지원합니다.'</span><span class="sxs-lookup"><span data-stu-id="43894-106">To support faster indexing of large XML data workloads.</span></span>  
  
-   <span data-ttu-id="43894-107">XML 인덱스의 스토리지 비용을 감소시켜 확장성을 향상시킵니다.</span><span class="sxs-lookup"><span data-stu-id="43894-107">To improve scalability by reducing the storage costs of XML indexes.</span></span>  
  
 <span data-ttu-id="43894-108">일반 XML 인덱스의 주요 제한 사항은 일반 인덱스는 전체 XML 문서를 인덱싱한다는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="43894-108">The main limitation with ordinary XML indexes is that they index the entire XML document.</span></span> <span data-ttu-id="43894-109">이로 인해 쿼리 성능 저하 및 주로 인덱스의 스토리지 비용과 관련된 인덱스의 유지 관리 비용 증가와 같은 몇 가지 중요한 단점이 생겨났습니다.</span><span class="sxs-lookup"><span data-stu-id="43894-109">This leads to several significant drawbacks, such as decreased query performance and increased index maintenance cost, mostly related to the storage costs of the index.</span></span>  
  
 <span data-ttu-id="43894-110">선택적 XML 인덱스 기능을 사용하면 특정 경로만 XML 문서에서 인덱스로 승격시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="43894-110">The selective XML index feature lets you promote only certain paths from the XML documents to index.</span></span> <span data-ttu-id="43894-111">인덱스를 만들 때 이러한 경로가 승격되고 이러한 경로가 가리키는 노드는 분할되어 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 관계형 테이블 내에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="43894-111">At index creation time, these paths are evaluated, and the nodes that they point to are shredded and stored inside a relational table in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="43894-112">이 기능은 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Research와 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 제품 팀의 협업으로 개발한 효율적인 매핑 알고리즘을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="43894-112">This feature uses an efficient mapping algorithm developed by [!INCLUDE[msCoName](../../includes/msconame-md.md)] Research in collaboration with the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] product team.</span></span> <span data-ttu-id="43894-113">이 알고리즘은 XML 노드를 단일 관계형 테이블에 매핑하며, 적당한 스토리지 공간만을 사용하면서도 뛰어난 성능을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="43894-113">This algorithm maps the XML nodes to a single relational table, and achieves exceptional performance while requiring only modest storage space.</span></span>  
  
 <span data-ttu-id="43894-114">또한 선택적 XML 인덱스 기능은 선택적 XML 인덱스에 의해 이미 인덱싱된 노드에 대해 보조 선택적 XML 인덱스를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="43894-114">The selective XML index feature also supports secondary selective XML indexes over nodes that have been indexed by a selective XML index.</span></span> <span data-ttu-id="43894-115">이러한 보조 선택적 인덱스는 효율적이며, 쿼리 성능을 한층 더 향상시킵니다.</span><span class="sxs-lookup"><span data-stu-id="43894-115">These secondary selective indexes are efficient and further improve the performance of queries.</span></span>  
  
##  <a name="benefits-of-selective-xml-indexes"></a><a name="benefits"></a> <span data-ttu-id="43894-116">선택적 XML 인덱스의 이점</span><span class="sxs-lookup"><span data-stu-id="43894-116">Benefits of Selective XML Indexes</span></span>  
 <span data-ttu-id="43894-117">선택적 XML 인덱스는 다음과 같은 이점을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="43894-117">Selective XML indexes provide the following benefits:</span></span>  
  
1.  <span data-ttu-id="43894-118">일반 쿼리 부하에 비해 XML 데이터 형식에 대한 쿼리 성능이 크게 향상됩니다.</span><span class="sxs-lookup"><span data-stu-id="43894-118">Greatly improved query performance over the XML data type for typical query loads.</span></span>  
  
2.  <span data-ttu-id="43894-119">일반 XML 인덱스에 비해 스토리지 요구 사항이 줄어듭니다.</span><span class="sxs-lookup"><span data-stu-id="43894-119">Reduced storage requirements compared to ordinary XML indexes.</span></span>  
  
3.  <span data-ttu-id="43894-120">일반 XML 인덱스에 비해 인덱스 유지 관리 비용이 줄어듭니다.</span><span class="sxs-lookup"><span data-stu-id="43894-120">Reduced index maintenance costs compared to ordinary XML indexes.</span></span>  
  
4.  <span data-ttu-id="43894-121">선택적 XML 인덱스를 사용하기 위해 애플리케이션을 업데이트할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="43894-121">No need to update applications to benefit from selective XML indexes.</span></span>  
  

  
##  <a name="selective-xml-indexes-and-primary-xml-indexes"></a><a name="compare"></a> <span data-ttu-id="43894-122">선택적 XML 인덱스 및 보조 XML 인덱스</span><span class="sxs-lookup"><span data-stu-id="43894-122">Selective XML Indexes and Primary XML Indexes</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="43894-123">대부분의 경우 더 나은 성능과 더 효율적인 스토리지를 위해 일반 XML 인덱스 대신 선택적 XML 인덱스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="43894-123">Create a selective XML index instead of an ordinary XML index in most cases for better performance and more efficient storage.</span></span>  
  
 <span data-ttu-id="43894-124">그러나 다음 조건 중 하나에 해당하는 경우에는 선택적 XML 인덱스가 권장되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="43894-124">However, a selective XML index is not recommended when either of the following conditions is true:</span></span>  
  
-   <span data-ttu-id="43894-125">많은 수의 노드 경로를 매핑하는 경우</span><span class="sxs-lookup"><span data-stu-id="43894-125">You map a large number of node paths.</span></span>  
  
-   <span data-ttu-id="43894-126">문서 구조에서 알 수 없는 위치에 있는 알 수 없는 요소에 대한 쿼리를 지원하는 경우</span><span class="sxs-lookup"><span data-stu-id="43894-126">You support queries for unknown elements or elements in an unknown location in the document structure.</span></span>  
  

  
##  <a name="simple-example-of-a-selective-xml-index"></a><a name="example"></a> <span data-ttu-id="43894-127">선택적 XML 인덱스의 간단한 예</span><span class="sxs-lookup"><span data-stu-id="43894-127">Simple Example of a Selective XML Index</span></span>  
 <span data-ttu-id="43894-128">테이블에 약 500,000개의 행이 있는 XML 문서인 다음 XML 조각을 살펴보십시오.</span><span class="sxs-lookup"><span data-stu-id="43894-128">Consider the following XML fragment as an XML document in a table of approximately 500,000 rows:</span></span>  
  
```xml  
<book>  
    <created>2004-03-01</created>   
    <authors>Various</authors>  
    <subjects>  
        <subject>English wit and humor -- Periodicals</subject>  
        <subject>AP</subject>   
    </subjects>  
    <title>Punch, or the London Charivari, Volume 156, April 2, 1919</title>  
    <id>etext11617</id>  
</book>  
```  
  
 <span data-ttu-id="43894-129">이 간단한 스키마에 있는 무수히 많은 행에 대해 주 XML 인덱스를 만들려고 하면 시간이 많이 걸립니다.</span><span class="sxs-lookup"><span data-stu-id="43894-129">Creating a primary XML index over so many rows of this simple schema takes a long time.</span></span> <span data-ttu-id="43894-130">마찬가지로 주 XML 인덱스가 선택적 인덱스를 지원하지 않으므로 이 데이터를 쿼리하는 것도 쉽지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="43894-130">Querying this data also suffers from the fact that a primary XML index does not support selective indexing.</span></span>  
  
 <span data-ttu-id="43894-131">`/book/title` 경로 및 `/book/subjects` 경로를 통해 이 데이터를 쿼리하기만 하면 되는 경우 다음과 같은 선택적 XML 인덱스를 만들면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="43894-131">If you only need to query this data over the `/book/title` path and the `/book/subjects` path, you can create the following selective XML index:</span></span>  
  
```sql  
CREATE SELECTIVE XML INDEX SXI_index  
ON Tbl(xmlcol)  
FOR   
(  
    pathTitle = '/book/title/text()' AS XQUERY 'xs:string',   
    pathAuthors = '/book/authors' AS XQUERY 'node()',  
    pathId = '/book/id' AS SQL NVARCHAR(100)  
)  
```  
  
 <span data-ttu-id="43894-132">위의 문은 선택적 XML 인덱스를 만들 때 사용하는 CREATE 구문의 좋은 예입니다</span><span class="sxs-lookup"><span data-stu-id="43894-132">The preceding statement is a good example of the CREATE syntax that you use when you create a selective XML index.</span></span> <span data-ttu-id="43894-133">CREATE 문에서 먼저 인덱스 수를 제공하고 인덱싱할 테이블 및 XML 열을 식별한 다음</span><span class="sxs-lookup"><span data-stu-id="43894-133">In the CREATE statement, first you provide a name for the index and identify the table and the XML column to index.</span></span> <span data-ttu-id="43894-134">인덱싱할 경로를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="43894-134">Then you provide the paths to index.</span></span> <span data-ttu-id="43894-135">경로는 다음과 같은 세 부분으로 구성되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="43894-135">A path has three parts:</span></span>  
  
1.  <span data-ttu-id="43894-136">경로를 고유하게 식별하는 이름</span><span class="sxs-lookup"><span data-stu-id="43894-136">A name that uniquely identifies the path.</span></span>  
  
2.  <span data-ttu-id="43894-137">경로를 설명하는 XQuery 식</span><span class="sxs-lookup"><span data-stu-id="43894-137">An XQuery expression that describes the path.</span></span>  
  
3.  <span data-ttu-id="43894-138">선택적 최적화 힌트</span><span class="sxs-lookup"><span data-stu-id="43894-138">Optional optimization hints.</span></span>  
  
 <span data-ttu-id="43894-139">이러한 요소에 대한 자세한 내용은 [관련 태스크](#reltasks)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="43894-139">For more information about these elements, see [Related Tasks](#reltasks).</span></span>  
  

  
## <a name="supported-features-prerequisites-and-limitations"></a><span data-ttu-id="43894-140">지원되는 기능, 사전 요구 사항 및 제한 사항</span><span class="sxs-lookup"><span data-stu-id="43894-140">Supported Features, Prerequisites, and Limitations</span></span>  
  
###  <a name="supported-xml-features"></a><a name="features"></a> <span data-ttu-id="43894-141">지원되는 XML 기능</span><span class="sxs-lookup"><span data-stu-id="43894-141">Supported XML Features</span></span>  
 <span data-ttu-id="43894-142">선택적 XML 인덱스는 exist(), value() 및 nodes() 메서드 내에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 가 지원하는 XQuery를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="43894-142">Selective XML indexes support the XQuery supported by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] inside the exist(), value() and nodes() methods.</span></span>  
  
-   <span data-ttu-id="43894-143">exist(), value() 및 nodes() 메서드의 경우 선택적 XML 인덱스는 전체 식을 변환할 수 있는 충분한 정보를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="43894-143">For the exist(), value() and nodes() methods, selective XML indexes contain enough information to transform the entire expression.</span></span>  
  
-   <span data-ttu-id="43894-144">query() 및 modify() 메서드의 경우 선택적 XML 인덱스는 노드 필터링 목적으로만 사용될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="43894-144">For the query() and modify() methods, selective XML indexes may be used for node filtering only.</span></span>  
  
-   <span data-ttu-id="43894-145">query() 메서드의 경우 선택적 XML 인덱스는 결과를 검색하는 데 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="43894-145">For the query() method, selective XML indexes are not used to retrieve results.</span></span>  
  
-   <span data-ttu-id="43894-146">modify() 메서드의 경우 선택적 XML 인덱스는 XML 문서를 업데이트하는 데 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="43894-146">For the modify() method, selective XML indexes are not used to update XML documents.</span></span>  
  

  
###  <a name="unsupported-xml-features"></a><a name="unsupported"></a> <span data-ttu-id="43894-147">지원되지 않는 XML 기능</span><span class="sxs-lookup"><span data-stu-id="43894-147">Unsupported XML Features</span></span>  
 <span data-ttu-id="43894-148">선택적 XML 인덱스는 XML의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 구현에서 지원되는 다음 기능을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="43894-148">Selective XML indexes do not support the following features that are supported in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] implementation of XML:</span></span>  
  
-   <span data-ttu-id="43894-149">공용 구조체 유형, 시퀀스 유형 및 목록 유형과 같은 복잡한 XS 유형이 있는 노드의 인덱싱</span><span class="sxs-lookup"><span data-stu-id="43894-149">Indexing of nodes with complex XS types: union types, sequence types, and list types.</span></span>  
  
-   <span data-ttu-id="43894-150">base64Binary 및 hexBinary와 같은 이진 XS 유형이 있는 노드의 인덱싱</span><span class="sxs-lookup"><span data-stu-id="43894-150">Indexing of nodes with binary XS types: for example, base64Binary and hexBinary.</span></span>  
  
-   <span data-ttu-id="43894-151">끝에 `*` 와일드카드 문자가 포함된 XPath 식을 사용하여 인덱싱할 노드 지정. 예: `/a/b/c/*`, `/a//b/*` 또는 `/a/b/*:c`.</span><span class="sxs-lookup"><span data-stu-id="43894-151">Specifying the nodes to index with XPath expressions that contain the wildcard character `*` at the end: For example,  `/a/b/c/*`, `/a//b/*`, or `/a/b/*:c`.</span></span>  
  
-   <span data-ttu-id="43894-152">자식, 특성 또는 하위 항목 이외의 모든 축 인덱싱.</span><span class="sxs-lookup"><span data-stu-id="43894-152">Indexing any axis other than child, attribute, or descendant.</span></span> <span data-ttu-id="43894-153">`//<step>` 은 특별한 경우로 허용됩니다.</span><span class="sxs-lookup"><span data-stu-id="43894-153">The `//<step>` case is allowed as a special case.</span></span>  
  
-   <span data-ttu-id="43894-154">명령 및 주석을 처리하는 XML의 인덱싱</span><span class="sxs-lookup"><span data-stu-id="43894-154">Indexing of XML processing instructions and comments.</span></span>  
  
-   <span data-ttu-id="43894-155">id() 함수를 사용하여 노드 식별자 지정 및 검색</span><span class="sxs-lookup"><span data-stu-id="43894-155">Specifying and retrieving the identifier for a node by using the id() function.</span></span>  
  

  
###  <a name="prerequisites"></a><a name="prereq"></a> <span data-ttu-id="43894-156">필수 조건</span><span class="sxs-lookup"><span data-stu-id="43894-156">Prerequisites</span></span>  
 <span data-ttu-id="43894-157">사용자 테이블의 XML 열에 대해 선택적 XML 인덱스를 만들려면 먼저 다음 사전 요구 사항을 충족해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="43894-157">The following prerequisites must exist before you can create a selective XML index over an XML column in a user table:</span></span>  
  
-   <span data-ttu-id="43894-158">클러스터형 인덱스는 사용자 테이블의 기본 키에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="43894-158">A clustered index must exist on the primary key of the user table.</span></span>  
  
-   <span data-ttu-id="43894-159">선택적 XML 인덱스와 함께 사용할 경우 사용자 테이블의 기본 키는 128바이트로 제한됩니다.</span><span class="sxs-lookup"><span data-stu-id="43894-159">The primary key of the user table is limited to a size of 128 bytes when used with selective XML indexes.</span></span>  
  
-   <span data-ttu-id="43894-160">선택적 XML 인덱스와 함께 사용할 경우 사용자 테이블의 클러스터링 키는 15열로 제한됩니다.</span><span class="sxs-lookup"><span data-stu-id="43894-160">The clustering key of the user table is limited to 15 columns when used with selective XML indexes.</span></span>  
  

  
###  <a name="limitations"></a><a name="limits"></a> <span data-ttu-id="43894-161">제한 사항</span><span class="sxs-lookup"><span data-stu-id="43894-161">Limitations</span></span>  
 <span data-ttu-id="43894-162">**일반 요구 사항 및 제한 사항**</span><span class="sxs-lookup"><span data-stu-id="43894-162">**General requirements and limitations**</span></span>  
  
-   <span data-ttu-id="43894-163">하나의 XML 열에 대해 하나의 선택적 XML 인덱스만 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="43894-163">Each selective XML index can only be created on a single XML column.</span></span>  
  
-   <span data-ttu-id="43894-164">XML이 아닌 열에 대해서는 선택적 XML 인덱스를 만들 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="43894-164">You cannot create a selective XML index on a non-XML column.</span></span>  
  
-   <span data-ttu-id="43894-165">테이블의 각 XML 열에는 하나의 선택적 XML 인덱스만 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="43894-165">Each XML column in a table can have only one selective XML index.</span></span>  
  
-   <span data-ttu-id="43894-166">각 테이블에는 최대 249개의 선택적 XML 인덱스가 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="43894-166">Each table can have up to 249 selective XML indexes.</span></span>  
  
 <span data-ttu-id="43894-167">**지원되는 개체에 대한 제한 사항**</span><span class="sxs-lookup"><span data-stu-id="43894-167">**Limitations on supported objects**</span></span>  
  
 <span data-ttu-id="43894-168">다음 개체에 대해서는 선택적 XML 인덱스를 만들 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="43894-168">You cannot create selective XML indexes on the following objects:</span></span>  
  
1.  <span data-ttu-id="43894-169">뷰의 XML 열</span><span class="sxs-lookup"><span data-stu-id="43894-169">XML columns in a view.</span></span>  
  
2.  <span data-ttu-id="43894-170">XML 열이 있는 테이블 반환 변수</span><span class="sxs-lookup"><span data-stu-id="43894-170">Table-valued variable with XML columns.</span></span>  
  
3.  <span data-ttu-id="43894-171">XML 유형 변수</span><span class="sxs-lookup"><span data-stu-id="43894-171">XML type variables.</span></span>  
  
4.  <span data-ttu-id="43894-172">계산된 XML 열</span><span class="sxs-lookup"><span data-stu-id="43894-172">Computed XML columns.</span></span>  
  
5.  <span data-ttu-id="43894-173">노드가 128번 이상 중첩된 XML 열</span><span class="sxs-lookup"><span data-stu-id="43894-173">XML columns with a depth of more than 128 nested nodes.</span></span>  
  
 <span data-ttu-id="43894-174">**스토리지 관련 제한 사항**</span><span class="sxs-lookup"><span data-stu-id="43894-174">**Limitations related to storage**</span></span>  
  
 <span data-ttu-id="43894-175">XML 문서에서 인덱스에 추가할 수 있는 노드 수는 제한되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="43894-175">There is a finite limit on the number of nodes from the XML document that can be added to the index.</span></span> <span data-ttu-id="43894-176">선택적 XML 인덱스는 XML 문서를 하나의 관계형 테이블에 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="43894-176">A selective XML index maps XML documents to a single relational table.</span></span> <span data-ttu-id="43894-177">따라서 지정된 테이블의 행에는 null이 아닌 행이 1024개 이상 있을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="43894-177">Therefore it cannot have more than 1024 non-null columns in any given row of the table.</span></span> <span data-ttu-id="43894-178">또한 인덱스에서 스토리지 목적으로 스파스 열을 사용하므로 스파스 열에 대한 많은 제한 사항이 선택적 XML 열에도 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="43894-178">Furthermore, many of the limitations of sparse columns also apply to selective XML indexes, because the indexes use sparse columns for storage.</span></span>  
  
 <span data-ttu-id="43894-179">지정된 행에서 지원되는 non이 아닌 열의 최대 수는 다음과 같이 열에 있는 데이터의 크기에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="43894-179">The maximum number of non-null columns supported in any given row depends on the size of the data in the columns:</span></span>  
  
-   <span data-ttu-id="43894-180">최상의 경우에서 모든 열이 **bit**유형이면 1024개의 null이 아닌 열이 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="43894-180">In the best case, 1024 non-null columns are supported when all columns are of type **bit**.</span></span>  
  
-   <span data-ttu-id="43894-181">최악의 경우에서 모든 열이 **varchar**유형의 큰 개체이면 null이 아닌 열이 236개만 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="43894-181">In the worst case, only 236 non-null columns are supported when all columns are large objects of type **varchar**.</span></span>  
  
 <span data-ttu-id="43894-182">선택적 XML 인덱스는 인덱싱되는 각 노드에 대해 1-4개의 열을 내부적으로 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="43894-182">Selective XML indexes use from one to four columns internally for every node path that is indexed.</span></span> <span data-ttu-id="43894-183">인덱싱할 수 있는 총 노드 수는 인덱싱된 경로에 있는 데이터의 실제 크기에 따라 60개부터 수백 개까지 다양합니다.</span><span class="sxs-lookup"><span data-stu-id="43894-183">The total number of nodes that can be indexed ranges from 60 to several hundred nodes, depending on the actual size of the data in the indexed paths.</span></span>  
  
-   <span data-ttu-id="43894-184">최악의 경우에서 일부 또는 모든 노드가 노드 경로 정의에 있는 `//` 코드를 사용하여 매핑되면 인덱싱되는 최대 노드 수는 60개입니다.</span><span class="sxs-lookup"><span data-stu-id="43894-184">In the worst case, when some or all nodes are mapped using `//` in the node path definition, the maximum number of indexed nodes is 60.</span></span>  
  
-   <span data-ttu-id="43894-185">최상의 경우에서 노드가 노드 경로 정의에 있는 `//` 코드를 사용하지 않고 매핑되면 인덱싱되는 최대 노드 수는 200개입니다.</span><span class="sxs-lookup"><span data-stu-id="43894-185">In the best case, when nodes are mapped without using `//` in the node path definition, the maximum number of indexed nodes is 200.</span></span>  
  
 <span data-ttu-id="43894-186">**선택적 XML 인덱스는 사용자가 해당 인덱스를 만들거나 변경하면 다시 작성됩니다.**</span><span class="sxs-lookup"><span data-stu-id="43894-186">**Selective XML indexes are rebuilt when you CREATE or ALTER the index.**</span></span>  
  
 <span data-ttu-id="43894-187">선택적 XML 인덱스를 만들거나 변경하면 해당 인덱스는 단일 스레드 오프라인 모드에서 다시 작성됩니다.</span><span class="sxs-lookup"><span data-stu-id="43894-187">When you CREATE or ALTER a selective XML index, it is rebuilt in a single-threaded, offline mode.</span></span> <span data-ttu-id="43894-188">ALTER 문을 자주 실행하면 인덱싱된 XML 문서에 대한 쿼리 성능에 부정적인 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="43894-188">Frequently ALTER statements negatively affect the performance of queries over the indexed XML documents.</span></span>  
  
 <span data-ttu-id="43894-189">**기타 제한 사항**</span><span class="sxs-lookup"><span data-stu-id="43894-189">**Other limitations**</span></span>  
  
-   <span data-ttu-id="43894-190">선택적 XML 인덱스는 쿼리 힌트에서 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="43894-190">Selective XML indexes are not supported in query hints.</span></span>  
  
-   <span data-ttu-id="43894-191">선택적 XML 인덱스 및 보조 선택적 XML 인덱스는 데이터베이스 튜닝 관리자에서 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="43894-191">Selective XML indexes and secondary selective XML indexes are not supported in Database Tuning Advisor.</span></span>  
  

  
##  <a name="related-tasks"></a><a name="reltasks"></a> <span data-ttu-id="43894-192">관련 작업</span><span class="sxs-lookup"><span data-stu-id="43894-192">Related Tasks</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="43894-193">**Task**</span><span class="sxs-lookup"><span data-stu-id="43894-193">**Task**</span></span>|<span data-ttu-id="43894-194">**항목**</span><span class="sxs-lookup"><span data-stu-id="43894-194">**Topic**</span></span>|  
|<span data-ttu-id="43894-195">선택적 XML 인덱스를 만들거나 변경할 때 인덱싱할 노드 경로 및 선택적 최적화 힌트를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="43894-195">Specify the node paths that you want to index and optional optimization hints when you create or alter a selective XML index.</span></span>|[<span data-ttu-id="43894-196">선택적 XML 인덱스에 대한 경로 및 최적화 힌트 지정</span><span class="sxs-lookup"><span data-stu-id="43894-196">Specify Paths and Optimization Hints for Selective XML Indexes</span></span>](specify-paths-and-optimization-hints-for-selective-xml-indexes.md)|  
|<span data-ttu-id="43894-197">선택적 XML 인덱스를 만들고, 변경하고, 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="43894-197">Create, alter, or drop a selective XML index.</span></span>|[<span data-ttu-id="43894-198">선택적 XML 인덱스 만들기, 변경 및 삭제</span><span class="sxs-lookup"><span data-stu-id="43894-198">Create, Alter, and Drop Selective XML Indexes</span></span>](create-alter-and-drop-selective-xml-indexes.md)|  
|<span data-ttu-id="43894-199">보조 선택적 XML 인덱스를 만들고, 변경하고, 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="43894-199">Create, alter, or drop a secondary selective XML index.</span></span>|[<span data-ttu-id="43894-200">보조 선택적 XML 인덱스 만들기, 변경 및 삭제</span><span class="sxs-lookup"><span data-stu-id="43894-200">Create, Alter, and Drop Secondary Selective XML Indexes</span></span>](create-alter-and-drop-secondary-selective-xml-indexes.md)|  
  

  
  
