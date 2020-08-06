---
title: XML 인덱스 삭제 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- removing indexes
- dropping indexes
- XML indexes [SQL Server], dropping
ms.assetid: 7591ebea-34af-4925-8553-b2adb5b487c2
author: rothja
ms.author: jroth
ms.openlocfilehash: b7d4621cf2182b4587b12665a1cfe10ddbe0db3a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646229"
---
# <a name="drop-xml-indexes"></a><span data-ttu-id="3b529-102">XML 인덱스 삭제</span><span class="sxs-lookup"><span data-stu-id="3b529-102">Drop XML Indexes</span></span>
  <span data-ttu-id="3b529-103">[DROP INDEX&#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-index-transact-sql)[!INCLUDE[tsql](../../includes/tsql-md.md)] 문을 사용하여 기존 기본 또는 보조 XML 인덱스 및 비 XML 인덱스를 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3b529-103">The [DROP INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-index-transact-sql)[!INCLUDE[tsql](../../includes/tsql-md.md)] statement can be used to drop existing primary or secondary XML and non-XML indexes.</span></span> <span data-ttu-id="3b529-104">그러나 DROP INDEX의 옵션은 XML 인덱스에 적용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3b529-104">However, no options of DROP INDEX apply to XML indexes.</span></span> <span data-ttu-id="3b529-105">기본 XML 인덱스를 삭제하려면 존재하는 보조 인덱스도 모두 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="3b529-105">If you drop the primary XML index, any secondary indexes that are present are also deleted.</span></span>  
  
 <span data-ttu-id="3b529-106">*TableName.IndexName* 이 있는 DROP 구문은 단계적으로 제거하며 XML 인덱스에 대해서는 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3b529-106">The DROP syntax with *TableName.IndexName* is being phased out and is not supported for XML indexes.</span></span>  
  
## <a name="example-creating-and-dropping-a-primary-xml-index"></a><span data-ttu-id="3b529-107">예제: 기본 XML 인덱스 만들기 및 삭제</span><span class="sxs-lookup"><span data-stu-id="3b529-107">Example: Creating and Dropping a Primary XML Index</span></span>  
 <span data-ttu-id="3b529-108">다음 예에서는 XML 인덱스가 `xml` 유형 열에 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="3b529-108">In the following example, an XML index is created on an `xml` type column.</span></span>  
  
```  
DROP TABLE T  
GO  
CREATE TABLE T (Col1 INT PRIMARY KEY, XmlCol XML)  
GO  
-- Create Primary XML index   
CREATE PRIMARY XML INDEX PIdx_T_XmlCol   
ON T(XmlCol)  
GO  
-- Verify the index creation.   
-- Note index type is 3 for xml indexes.  
-- Note the type 3 is index on XML type.  
SELECT *  
FROM sys.xml_indexes  
WHERE object_id = object_id('T')  
AND name='PIdx_T_XmlCol'   
-- Drop the index.  
DROP INDEX PIdx_T_XmlCol ON T  
```  
  
 <span data-ttu-id="3b529-109">테이블이 삭제될 때 그 테이블의 모든 XML 인덱스도 자동으로 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="3b529-109">When a table is dropped, all the XML indexes on it are also automatically dropped.</span></span> <span data-ttu-id="3b529-110">그러나 XML 인덱스가 열에 있는 경우 XML 열은 테이블에서 삭제할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3b529-110">However, an XML column cannot be dropped from a table if an XML index exists on the column.</span></span>  
  
 <span data-ttu-id="3b529-111">다음 예에서는 XML 인덱스가 `xml` 유형 열에 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="3b529-111">In the following example, an XML index is created on an `xml` type column.</span></span> <span data-ttu-id="3b529-112">자세한 내용은 [형식화된 XML과 형식화되지 않은 XML 비교](../xml/compare-typed-xml-to-untyped-xml.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3b529-112">For more information, see [Compare Typed XML to Untyped XML](../xml/compare-typed-xml-to-untyped-xml.md).</span></span>  
  
```  
CREATE TABLE TestTable(  
 Col1 int primary key,   
 Col2 xml (Production.ProductDescriptionSchemaCollection))   
GO  
```  
  
 <span data-ttu-id="3b529-113">이제 `Co12`에 기본 XML 인덱스를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3b529-113">Now, you can create a primary XML index on `Co12`.</span></span>  
  
```  
CREATE PRIMARY XML INDEX PIdx_TestTable_Col2   
ON TestTable(Col2)  
GO  
```  
  
## <a name="example-creating-an-xml-index-by-using-the-drop_existing-index-option"></a><span data-ttu-id="3b529-114">예제: DROP_EXISTING 인덱스 옵션을 사용하여 XML 인덱스 만들기</span><span class="sxs-lookup"><span data-stu-id="3b529-114">Example: Creating an XML Index by Using the DROP_EXISTING Index Option</span></span>  
 <span data-ttu-id="3b529-115">다음 예에서는 XML 인덱스가`XmlColx`열에 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="3b529-115">In the following example, an XML index is created on a column (`XmlColx`).</span></span> <span data-ttu-id="3b529-116">그런 다음 같은 이름으로 된 다른 XML 인덱스가 다른 열`XmlColy`에 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="3b529-116">Then, another XML index with the same name is created on a different column, (`XmlColy`).</span></span> <span data-ttu-id="3b529-117">`DROP_EXISTING` 옵션이 지정되어 있으므로 (`XmlColx)` )의 기존 XML 인덱스가 삭제되고 (`XmlColy`)의 새 XML 인덱스가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="3b529-117">Because the `DROP_EXISTING` option is specified, the existing XML index on (`XmlColx)` is dropped and a new XML index on (`XmlColy`) is created.</span></span>  
  
```  
DROP TABLE T  
GO  
CREATE TABLE T(Col1 int primary key, XmlColx xml, XmlColy xml)  
GO  
-- Create XML index on XmlColx.  
CREATE PRIMARY XML INDEX PIdx_T_XmlCol   
ON T(XmlColx)  
GO  
-- Create same name XML index on XmlColy.  
CREATE PRIMARY XML INDEX PIdx_T_XmlCol   
ON T(XmlColy)   
WITH (DROP_EXISTING = ON)  
-- Verify the index is created on XmlColy.d.  
SELECT sc.name   
FROM   sys.xml_indexes si inner join sys.index_columns sic   
ON     sic.object_id=si.object_id and sic.index_id=si.index_id  
INNER  join sys.columns sc on sc.object_id=sic.object_id   
AND    sc.column_id=sic.column_id  
WHERE  si.name='PIdx_T_XmlCol'   
AND    si.object_id=object_id('T')  
```  
  
 <span data-ttu-id="3b529-118">이 쿼리에서는 지정된 XML 인덱스가 생성된 열 이름을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="3b529-118">This query returns the column name on which the specified XML index is created.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b529-119">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3b529-119">See Also</span></span>  
 [<span data-ttu-id="3b529-120">XML 인덱스&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="3b529-120">XML Indexes &#40;SQL Server&#41;</span></span>](xml-indexes-sql-server.md)  
  
  
