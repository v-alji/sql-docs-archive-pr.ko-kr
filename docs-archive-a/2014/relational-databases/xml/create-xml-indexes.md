---
title: XML 인덱스 만들기 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- indexes [XML in SQL Server]
- XML indexes [SQL Server], creating
ms.assetid: 6ecac598-355d-4408-baf7-1b2e8d4cf7c1
author: rothja
ms.author: jroth
ms.openlocfilehash: 9e7800193222b8c9060fee1b247cc5585654cde4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738061"
---
# <a name="create-xml-indexes"></a><span data-ttu-id="fcedc-102">XML 인덱스 만들기</span><span class="sxs-lookup"><span data-stu-id="fcedc-102">Create XML Indexes</span></span>
  <span data-ttu-id="fcedc-103">이 항목에서는 기본 및 보조 XML 인덱스를 만드는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="fcedc-103">This topic describes how to create primary and secondary XML indexes.</span></span>  
  
## <a name="creating-a-primary-xml-index"></a><span data-ttu-id="fcedc-104">기본 XML 인덱스 만들기</span><span class="sxs-lookup"><span data-stu-id="fcedc-104">Creating a Primary XML Index</span></span>  
 <span data-ttu-id="fcedc-105">기본 XML 인덱스를 만들려면 [CREATE INDEX&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql)[!INCLUDE[tsql](../../includes/tsql-md.md)] DDL 문을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="fcedc-105">To create a primary XML index, use the [CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql)[!INCLUDE[tsql](../../includes/tsql-md.md)] DDL statement.</span></span> <span data-ttu-id="fcedc-106">비-XML 인덱스에 대해 사용 가능한 옵션이 XML 인덱스에서 모두 지원되는 것은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="fcedc-106">Not all options available for non-XML indexes are supported on XML indexes.</span></span>  
  
 <span data-ttu-id="fcedc-107">XML 인덱스를 만들 때는 다음 사항을 알아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fcedc-107">Note the following when you are creating an XML index:</span></span>  
  
-   <span data-ttu-id="fcedc-108">기본 XML 인덱스를 만들려면 기본 테이블이라는 인덱싱되는 XML 열이 포함된 테이블에 기본 키에서 클러스터형 인덱스가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fcedc-108">To create a primary XML index, the table that contains the XML column being indexed, called the base table, must have a clustered index on the primary key.</span></span> <span data-ttu-id="fcedc-109">이렇게 하면 기본 테이블이 분할되는 경우 기본 XML 인덱스를 같은 파티션 구성표와 파티션 함수를 사용하여 분할할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fcedc-109">This makes sure that if the base table is partitioned, the primary XML index can be partitioned by using the same partitioning scheme and partitioning function.</span></span>  
  
-   <span data-ttu-id="fcedc-110">XML 인덱스가 있으면 테이블의 클러스터형 기본 키를 수정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="fcedc-110">If an XML index exists, the clustered, primary key of the table cannot be modified.</span></span> <span data-ttu-id="fcedc-111">모든 XML 인덱스를 테이블에서 삭제해야 기본 키를 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fcedc-111">You will have to drop all XML indexes on the table before modifying the primary key.</span></span>  
  
-   <span data-ttu-id="fcedc-112">기본 XML 인덱스는 단일 `xml` 유형 열에서 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fcedc-112">A primary XML index can be created on a single `xml` type column.</span></span> <span data-ttu-id="fcedc-113">XML 유형 열이 있는 다른 인덱스 유형은 키 열로 만들 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="fcedc-113">You cannot create any other type of index with the XML type column as a key column.</span></span> <span data-ttu-id="fcedc-114">그러나 비-XML 인덱스에는 `xml` 유형 열을 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fcedc-114">However, you can include the `xml` L type column in a non-XML index.</span></span> <span data-ttu-id="fcedc-115">테이블의 `xml` 유형 열마다 자신의 기본 XML 인덱스를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fcedc-115">Each `xml` type column in a table can have its own primary XML index.</span></span> <span data-ttu-id="fcedc-116">그러나 기본 XML 인덱스는 `xml` 유형 열마다 하나씩만 허용됩니다.</span><span class="sxs-lookup"><span data-stu-id="fcedc-116">However, only one primary XML index per `xml` type column is permitted.</span></span>  
  
-   <span data-ttu-id="fcedc-117">XML 인덱스는 비-XML 인덱스와 같은 네임스페이스에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fcedc-117">XML indexes exist in the same namespace as non-XML indexes.</span></span> <span data-ttu-id="fcedc-118">따라서 같은 테이블에서 이름이 같은 XML 인덱스와 비-XML 인덱스를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="fcedc-118">Therefore, you cannot have an XML index and a non-XML index on the same table with the same name.</span></span>  
  
-   <span data-ttu-id="fcedc-119">IGNORE_DUP_KEY 및 ONLINE 옵션은 XML 인덱스에 대해 항상 OFF로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="fcedc-119">IGNORE_DUP_KEY and ONLINE options of are always set to OFF for XML indexes.</span></span> <span data-ttu-id="fcedc-120">이러한 옵션의 값을 OFF로 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fcedc-120">You can specify these options with a value of OFF.</span></span>  
  
-   <span data-ttu-id="fcedc-121">사용자 테이블의 파일 그룹 또는 분할 정보는 XML 인덱스에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="fcedc-121">The filegroup or partitioning information of the user table is applied to the XML index.</span></span> <span data-ttu-id="fcedc-122">사용자는 XML 인덱스에서 이를 별도로 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="fcedc-122">Users cannot specify these separately on an XML index.</span></span>  
  
-   <span data-ttu-id="fcedc-123">DROP_EXISTING 인덱스 옵션은 기본 XML 인덱스를 삭제하고 새 기본 XML 인덱스를 만들거나, 보조 XML 인덱스를 삭제하고 새 보조 XML 인덱스를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fcedc-123">The DROP_EXISTING index option can drop a primary XML index and create a new primary XML index, or drop a secondary XML index and create a new secondary XML index.</span></span> <span data-ttu-id="fcedc-124">그러나 이 옵션을 사용하여 보조 XML 인덱스를 삭제하고 새 기본 XML 인덱스를 만들거나 기본 XML 인덱스를 삭제하고 새 보조 XML 인덱스를 만들 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="fcedc-124">However, this option cannot drop a secondary XML index to create a new primary XML index or vice versa.</span></span>  
  
-   <span data-ttu-id="fcedc-125">기본 XML 인덱스 이름에는 뷰 이름과 같은 제한이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fcedc-125">Primary XML index names have the same restrictions as view names.</span></span>  
  
 <span data-ttu-id="fcedc-126">`xml`뷰의 유형 열, 유형 열이 있는 **테이블** 반환 변수 `xml` 또는 유형 변수에서 XML 인덱스를 만들 수 없습니다 `xml` .</span><span class="sxs-lookup"><span data-stu-id="fcedc-126">You cannot create an XML index on an `xml` type column in a view, on a **table** valued variable with `xml` type columns, or `xml` type variables.</span></span>  
  
-   <span data-ttu-id="fcedc-127">ALTER TABLE ALTER COLUMN 옵션을 사용하여 `xml` 유형 열을 형식화되지 않은 XML에서 형식화된 XML로 변경하거나 그 반대로 변경하려면 열에 XML 인덱스가 있으면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="fcedc-127">To change an `xml` type column from untyped to typed XML, or vice versa, by using the ALTER TABLE ALTER COLUMN option, no XML index on the column should exist.</span></span> <span data-ttu-id="fcedc-128">XML 인덱스가 있으면 열 형식 변경을 시도하기 전에 먼저 삭제해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fcedc-128">If one does exist, it must be dropped before the column type change is tried.</span></span>  
  
-   <span data-ttu-id="fcedc-129">ARITHABORT 옵션은 XML 인덱스를 만들 때 ON으로 설정되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fcedc-129">The option ARITHABORT must be set to ON when an XML index is created.</span></span> <span data-ttu-id="fcedc-130">XML 데이터 형식 메서드를 사용하여 XML 열의 값을 쿼리, 삽입, 삭제 또는 업데이트하려면 같은 옵션을 연결에 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fcedc-130">To query, insert, delete, or update values in the XML column using XML data type methods, the same option must be set on the connection.</span></span> <span data-ttu-id="fcedc-131">그렇지 않으면 XML 데이터 형식 메서드가 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="fcedc-131">If it is not, the XML data type methods will fail.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="fcedc-132">XML 인덱스에 대한 정보는 카탈로그 뷰에서 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fcedc-132">Information about an XML index can be found in catalog views.</span></span> <span data-ttu-id="fcedc-133">그러나 **sp_helpindex** 는 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="fcedc-133">However, **sp_helpindex** is not supported.</span></span> <span data-ttu-id="fcedc-134">이 항목의 후반부에 제공된 예에서는 카탈로그 뷰를 쿼리하여 XML 인덱스 정보를 찾는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="fcedc-134">Examples provided later in this topic show how to query the catalog views to find XML index information.</span></span>  
  
 <span data-ttu-id="fcedc-135">1년 미만의 값이 있는 XML 스키마 유형 **xs:date** 또는 **xs:dateTime** 이나 그 하위 유형의 값을 포함하는 XML 데이터 형식 열에 기본 XML 인덱스를 만들거나 다시 만들 경우 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 이상 버전에서 인덱스 만들기에 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="fcedc-135">When creating or recreating a primary XML index on an XML data type column that contains values of the XML Schema types **xs:date** or **xs:dateTime** (or any subtypes of these types) that have a year of less than 1, the index creation will fail in [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] and later versions.</span></span> [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] <span data-ttu-id="fcedc-136">에서는 이러한 값이 허용되었으므로 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]에서 생성된 데이터베이스에 인덱스를 만들 경우 이러한 문제가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fcedc-136">allowed these values, so this problem can occur when creating indexes in a database generated in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].</span></span> <span data-ttu-id="fcedc-137">자세한 내용은 [형식화된 XML과 형식화되지 않은 XML 비교](../xml/compare-typed-xml-to-untyped-xml.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fcedc-137">For more information, see [Compare Typed XML to Untyped XML](../xml/compare-typed-xml-to-untyped-xml.md).</span></span>  
  
### <a name="example-creating-a-primary-xml-index"></a><span data-ttu-id="fcedc-138">예제: 기본 XML 인덱스 만들기</span><span class="sxs-lookup"><span data-stu-id="fcedc-138">Example: Creating a Primary XML Index</span></span>  
 <span data-ttu-id="fcedc-139">대부분의 예에서는 형식화되지 않은 XML 열이 포함된 테이블 T(pk INT PRIMARY KEY, xCol XML)가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="fcedc-139">Table T (pk INT PRIMARY KEY, xCol XML) with an untyped XML column is used in most of the examples.</span></span> <span data-ttu-id="fcedc-140">이러한 예는 직관적인 방식에 따라 형식화된 XML로 확장될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fcedc-140">These can be extended to typed XML in a straightforward way.</span></span> <span data-ttu-id="fcedc-141">간단한 설명을 위해 쿼리는 다음에 표시된 것과 같이 XML 데이터 인스턴스에 대해 기술됩니다.</span><span class="sxs-lookup"><span data-stu-id="fcedc-141">For simplicity, queries are described for XML data instances as shown in the following:</span></span>  
  
```  
<book genre="security" publicationdate="2002" ISBN="0-7356-1588-2">  
   <title>Writing Secure Code</title>  
   <author>  
      <first-name>Michael</first-name>  
      <last-name>Howard</last-name>  
   </author>  
   <author>  
      <first-name>David</first-name>  
      <last-name>LeBlanc</last-name>  
   </author>  
   <price>39.99</price>  
</book>  
```  
  
 <span data-ttu-id="fcedc-142">다음 문은 테이블 T의 XML 열 xCol에서 idx_xCol이라는 XML 인덱스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="fcedc-142">The following statement creates an XML index, called idx_xCol, on the XML column xCol of table T:</span></span>  
  
```  
CREATE PRIMARY XML INDEX idx_xCol on T (xCol)  
```  
  
## <a name="creating-a-secondary-xml-index"></a><span data-ttu-id="fcedc-143">보조 XML 인덱스 만들기</span><span class="sxs-lookup"><span data-stu-id="fcedc-143">Creating a Secondary XML Index</span></span>  
 <span data-ttu-id="fcedc-144">[CREATE INDEX&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql)[!INCLUDE[tsql](../../includes/tsql-md.md)] DDL 문을 사용하여 보조 XML 인덱스를 만들고 원하는 보조 XML 인덱스의 유형을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fcedc-144">Use the [CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql)[!INCLUDE[tsql](../../includes/tsql-md.md)] DDL statement to create secondary XML indexes and specify the type of the secondary XML index that you want.</span></span>  
  
 <span data-ttu-id="fcedc-145">보조 XML 인덱스를 만들 때는 다음 사항을 알아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fcedc-145">Note the following when you are creating secondary XML indexes:</span></span>  
  
-   <span data-ttu-id="fcedc-146">IGNORE_DUP_KEY 및 ONLINE을 제외하고 비클러스터형 인덱스에 적용되는 모든 인덱싱 옵션을 보조 XML 인덱스에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fcedc-146">All indexing options that apply to a nonclustered index, except IGNORE_DUP_KEY and ONLINE, are permitted on secondary XML indexes.</span></span> <span data-ttu-id="fcedc-147">두 옵션은 보조 XML 인덱스에 대해 항상 OFF로 설정되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fcedc-147">The two options must always be set to OFF for secondary XML indexes.</span></span>  
  
-   <span data-ttu-id="fcedc-148">보조 인덱스는 기본 XML 인덱스와 똑같이 분할됩니다.</span><span class="sxs-lookup"><span data-stu-id="fcedc-148">The secondary indexes are partitioned just like the primary XML index.</span></span>  
  
-   <span data-ttu-id="fcedc-149">DROP_EXISTING은 사용자 테이블에서 보조 인덱스를 삭제하고 다른 보조 인덱스를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fcedc-149">DROP_EXISTING can drop a secondary index on the user table and create another secondary index on the user table.</span></span>  
  
 <span data-ttu-id="fcedc-150">**sys.xml_indexes** 카탈로그 뷰를 쿼리하여 XML 인덱스 정보를 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fcedc-150">You can query the **sys.xml_indexes** catalog view to retrieve XML index information.</span></span> <span data-ttu-id="fcedc-151">**sys.xml_indexes** 카탈로그 뷰의 **secondary_type_desc** 열은 보조 인덱스 유형을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="fcedc-151">Note that the **secondary_type_desc** column in the **sys.xml_indexes** catalog view provides the type of secondary index:</span></span>  
  
```  
SELECT  *   
FROM    sys.xml_indexes;  
```  
  
 <span data-ttu-id="fcedc-152">**secondary_type_desc** 열에 반환된 값은 NULL, PATH, VALUE 또는 PROPERTY가 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fcedc-152">The values returned in the **secondary_type_desc** column can be NULL, PATH, VALUE, or PROPERTY.</span></span> <span data-ttu-id="fcedc-153">기본 XML 인덱스의 경우 반환된 값은 NULL입니다.</span><span class="sxs-lookup"><span data-stu-id="fcedc-153">For the primary XML index, the value returned is NULL.</span></span>  
  
### <a name="example-creating-secondary-xml-indexes"></a><span data-ttu-id="fcedc-154">예제: 보조 XML 인덱스 만들기</span><span class="sxs-lookup"><span data-stu-id="fcedc-154">Example: Creating Secondary XML Indexes</span></span>  
 <span data-ttu-id="fcedc-155">다음 예에서는 보조 XML 인덱스가 만들어지는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="fcedc-155">The following example illustrates how secondary XML indexes are created.</span></span> <span data-ttu-id="fcedc-156">또한 만들어진 XML 인덱스에 대한 정보도 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="fcedc-156">The example also shows information about the XML indexes that you created.</span></span>  
  
```  
CREATE TABLE T (Col1 INT PRIMARY KEY, XmlCol XML);  
GO  
-- Create primary index.  
CREATE PRIMARY XML INDEX PIdx_T_XmlCol   
ON T(XmlCol);  
GO  
-- Create secondary indexes (PATH, VALUE, PROPERTY).  
CREATE XML INDEX PIdx_T_XmlCol_PATH ON T(XmlCol)  
USING XML INDEX PIdx_T_XmlCol  
FOR PATH;  
GO  
CREATE XML INDEX PIdx_T_XmlCol_VALUE ON T(XmlCol)  
USING XML INDEX PIdx_T_XmlCol  
FOR VALUE;  
GO  
CREATE XML INDEX PIdx_T_XmlCol_PROPERTY ON T(XmlCol)  
USING XML INDEX PIdx_T_XmlCol  
FOR PROPERTY;  
GO  
```  
  
 <span data-ttu-id="fcedc-157">`sys.xml_indexes` 를 쿼리하여 XML 인덱스 정보를 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fcedc-157">You can query the `sys.xml_indexes` to retrieve XML indexes information.</span></span> <span data-ttu-id="fcedc-158">`secondary_type_desc` 열은 보조 인덱스 유형을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="fcedc-158">The `secondary_type_desc` column provides the secondary index type.</span></span>  
  
```  
SELECT  *   
FROM    sys.xml_indexes;  
```  
  
 <span data-ttu-id="fcedc-159">카탈로그 뷰에서 인덱스 정보를 쿼리할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fcedc-159">You can also query the catalog view for index information.</span></span>  
  
```  
SELECT *  
FROM sys.xml_indexes  
WHERE object_id = object_id('T');  
```  
  
 <span data-ttu-id="fcedc-160">예제 데이터를 추가한 다음 XML 인덱스 정보를 검토할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fcedc-160">You can add sample data and then review the XML index information.</span></span>  
  
```  
INSERT INTO T VALUES (1,  
'<doc id="123">  
<sections>  
<section num="2">  
<heading>Background</heading>  
</section>  
<section num="3">  
<heading>Sort</heading>  
</section>  
<section num="4">  
<heading>Search</heading>  
</section>  
</sections>  
</doc>');  
GO  
-- Check XML index information.  
SELECT *  
FROM   sys.dm_db_index_physical_stats (db_id(), object_id('T'), NULL, NULL, 'DETAILED');  
GO  
-- Space usage of primary XML index  
DECLARE @index_id int;  
SELECT  @index_id = i.index_id  
FROM    sys.xml_indexes i   
WHERE   i.name = 'PIdx_T_XmlCol' and object_name(i.object_id) = 'T';  
  
SELECT *  
FROM sys.dm_db_index_physical_stats (db_id(), object_id('T') , @index_id, DEFAULT, 'DETAILED');  
go  
--- Space usage of secondary XML index (for example PATH secondary index)  PIdx_T_XmlCol_PATH  
DECLARE @index_id int;  
SELECT  @index_id = i.index_id   
FROM    sys.xml_indexes i   
WHERE  i.name = 'PIdx_T_XmlCol_PATH' and object_name(i.object_id) = 'T';  
  
SELECT *  
FROM sys.dm_db_index_physical_stats (db_id(), object_id('T') , @index_id, DEFAULT, 'DETAILED');  
go  
  
-- Space usage of all secondary XML indexes for a particular table  
SELECT i.name, object_name(i.object_id), stats.*   
FROM   sys.dm_db_index_physical_stats (db_id(), object_id('T'), NULL, DEFAULT, 'DETAILED') stats  
JOIN sys.xml_indexes i ON (stats.object_id = i.object_id and stats.index_id = i.index_id)  
WHERE secondary_type is not null;  
-- Drop secondary indexes.  
DROP INDEX PIdx_T_XmlCol_PATH ON T;  
GO  
DROP INDEX PIdx_T_XmlCol_VALUE ON T;  
GO  
DROP INDEX PIdx_T_XmlCol_PROPERTY ON T;  
GO  
-- Drop primary index.  
DROP INDEX PIdx_T_XmlCol ON T;  
-- Drop table T.  
DROP TABLE T;  
Go  
```  
  
## <a name="see-also"></a><span data-ttu-id="fcedc-161">참고 항목</span><span class="sxs-lookup"><span data-stu-id="fcedc-161">See Also</span></span>  
 <span data-ttu-id="fcedc-162">[XML 인덱스&#40;SQL Server&#41;](xml-indexes-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="fcedc-162">[XML Indexes &#40;SQL Server&#41;](xml-indexes-sql-server.md) </span></span>  
 [<span data-ttu-id="fcedc-163">XML 데이터&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="fcedc-163">XML Data &#40;SQL Server&#41;</span></span>](xml-data-sql-server.md)  
  
  
