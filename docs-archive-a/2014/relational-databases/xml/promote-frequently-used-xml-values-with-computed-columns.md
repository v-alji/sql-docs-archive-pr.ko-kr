---
title: 계산 열을 사용하여 자주 사용되는 XML 값 승격 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- promoting properties [XML in SQL Server]
- property promotion [XML in SQL Server]
ms.assetid: f5111896-c2fd-4209-b500-f2baa45489ad
author: rothja
ms.author: jroth
ms.openlocfilehash: bfb83b7772ffd92eab7087db11e4c3ffd96afa47
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87733671"
---
# <a name="promote-frequently-used-xml-values-with-computed-columns"></a><span data-ttu-id="7b9b1-102">계산 열을 사용하여 자주 사용되는 XML 값 승격</span><span class="sxs-lookup"><span data-stu-id="7b9b1-102">Promote Frequently Used XML Values with Computed Columns</span></span>
  <span data-ttu-id="7b9b1-103">쿼리가 주로 적은 수의 요소 및 특성 값으로 작성된 경우 이러한 수량을 관계형 열로 승격시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7b9b1-103">If queries are made principally on a small number of element and attribute values, you may want to promote those quantities into relational columns.</span></span> <span data-ttu-id="7b9b1-104">이 방식은 전체 XML 인스턴스를 검색하는 동안 XML 데이터의 일부에 대해서 쿼리가 실행된 경우에 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="7b9b1-104">This is helpful when queries are issued on a small part of the XML data while the whole XML instance is retrieved.</span></span> <span data-ttu-id="7b9b1-105">XML 열에 XML 인덱스를 만들 필요는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7b9b1-105">Creating an XML index on the XML column is not required.</span></span> <span data-ttu-id="7b9b1-106">대신 승격된 열을 인덱싱할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7b9b1-106">Instead, the promoted column can be indexed.</span></span> <span data-ttu-id="7b9b1-107">승격된 열을 사용하도록 쿼리를 작성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b9b1-107">Queries must be written to use the promoted column.</span></span> <span data-ttu-id="7b9b1-108">즉, 쿼리 최적화 프로그램은 XML 열에 있는 쿼리를 승격된 열로 다시 대상화하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7b9b1-108">That is, the query optimizer does not target again the queries on the XML column to the promoted column.</span></span>  
  
 <span data-ttu-id="7b9b1-109">승격된 열은 같은 테이블에 있는 계산 열이거나 테이블에서 사용자가 유지 관리하는 별개의 열일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7b9b1-109">The promoted column can be a computed column in the same table or it can be a separate, user-maintained column in a table.</span></span> <span data-ttu-id="7b9b1-110">각 XML 인스턴스로부터 단일 항목 값이 승격되는 경우에는 이것으로 충분합니다.</span><span class="sxs-lookup"><span data-stu-id="7b9b1-110">This is sufficient when singleton values are promoted from each XML instance.</span></span> <span data-ttu-id="7b9b1-111">하지만 다중 값 속성의 경우 다음 섹션의 설명과 같이 속성에 대해 별개의 테이블을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b9b1-111">However, for multi-valued properties, you have to create a separate table for the property, as described in the following section.</span></span>  
  
## <a name="computed-column-based-on-the-xml-data-type"></a><span data-ttu-id="7b9b1-112">xml 데이터 형식에 따른 계산 열</span><span class="sxs-lookup"><span data-stu-id="7b9b1-112">Computed Column Based on the xml Data Type</span></span>  
 <span data-ttu-id="7b9b1-113">데이터 형식 메서드를 호출 하는 사용자 정의 함수를 사용 하 여 계산 열을 만들 수 있습니다 `xml` .</span><span class="sxs-lookup"><span data-stu-id="7b9b1-113">A computed column can be created by using a user-defined function that invokes `xml` data type methods.</span></span> <span data-ttu-id="7b9b1-114">계산 열의 유형은 XML을 포함하는 모든 SQL 유형일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7b9b1-114">The type of the computed column can be any SQL type, including XML.</span></span> <span data-ttu-id="7b9b1-115">다음 예에서 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7b9b1-115">This is illustrated in the following example.</span></span>  
  
### <a name="example-computed-column-based-on-the-xml-data-type-method"></a><span data-ttu-id="7b9b1-116">예제: xml 데이터 형식 메서드에 따른 계산 열</span><span class="sxs-lookup"><span data-stu-id="7b9b1-116">Example: Computed Column Based on the xml Data Type Method</span></span>  
 <span data-ttu-id="7b9b1-117">책 ISBN 번호에 대한 사용자 정의 함수를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="7b9b1-117">Create the user-defined function for a book ISBN number:</span></span>  
  
```  
CREATE FUNCTION udf_get_book_ISBN (@xData xml)  
RETURNS varchar(20)  
BEGIN  
   DECLARE @ISBN   varchar(20)  
   SELECT @ISBN = @xData.value('/book[1]/@ISBN', 'varchar(20)')  
   RETURN @ISBN   
END  
```  
  
 <span data-ttu-id="7b9b1-118">ISBN에 대한 테이블에 계산 열을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="7b9b1-118">Add a computed column to the table for the ISBN:</span></span>  
  
```  
ALTER TABLE      T  
ADD   ISBN AS dbo.udf_get_book_ISBN(xCol)  
```  
  
 <span data-ttu-id="7b9b1-119">계산 열은 일반적인 방식으로 인덱싱될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7b9b1-119">The computed column can be indexed in the usual way.</span></span>  
  
### <a name="example-queries-on-a-computed-column-based-on-xml-data-type-methods"></a><span data-ttu-id="7b9b1-120">예제: xml 데이터 형식 메서드에 따른 계산 열 쿼리</span><span class="sxs-lookup"><span data-stu-id="7b9b1-120">Example: Queries on a Computed Column Based on xml Data Type Methods</span></span>  
 <span data-ttu-id="7b9b1-121">ISBN이 0-7356-1588-2인 <`book`>을 가져오려면</span><span class="sxs-lookup"><span data-stu-id="7b9b1-121">To obtain the <`book`> whose ISBN is 0-7356-1588-2:</span></span>  
  
```  
SELECT xCol  
FROM   T  
WHERE  xCol.exist('/book/@ISBN[. = "0-7356-1588-2"]') = 1  
```  
  
 <span data-ttu-id="7b9b1-122">다음과 같이 계산 열을 사용하도록 XML 열의 쿼리를 다시 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7b9b1-122">The query on the XML column can be rewritten to use the computed column as follows:</span></span>  
  
```  
SELECT xCol  
FROM   T  
WHERE  ISBN = '0-7356-1588-2'  
```  
  
 <span data-ttu-id="7b9b1-123">사용자 정의 함수를 만들어 `xml` 사용자 정의 함수를 사용 하 여 데이터 형식과 계산 열을 반환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7b9b1-123">You can create a user-defined function to return the `xml` data type and a computed column by using the user-defined function.</span></span> <span data-ttu-id="7b9b1-124">하지만 XML 계산 열에는 XML 인덱스를 만들 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7b9b1-124">However, you cannot create an XML index on the computed, XML column.</span></span>  
  
## <a name="creating-property-tables"></a><span data-ttu-id="7b9b1-125">속성 테이블 만들기</span><span class="sxs-lookup"><span data-stu-id="7b9b1-125">Creating Property Tables</span></span>  
 <span data-ttu-id="7b9b1-126">XML 데이터에서 여러 값의 속성 중 일부를 하나 이상의 테이블로 승격시키고 해당 테이블에서 인덱스를 만들고 이를 사용하도록 쿼리를 다시 대상화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7b9b1-126">You may want to promote some of the multivalued properties from your XML data into one or more tables, create indexes on those tables, and target again your queries to use them.</span></span> <span data-ttu-id="7b9b1-127">일반적인 시나리오는 속성 중 일부에 대부분의 쿼리 작업이 포함되는 경우입니다.</span><span class="sxs-lookup"><span data-stu-id="7b9b1-127">A typical scenario is one in which a small number of properties covers most of your query workload.</span></span> <span data-ttu-id="7b9b1-128">사용할 수 있는 기능은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="7b9b1-128">You can do the following:</span></span>  
  
-   <span data-ttu-id="7b9b1-129">다중 값 속성을 보유하도록 하나 이상의 테이블을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="7b9b1-129">Create one or more tables to hold the multivalued properties.</span></span> <span data-ttu-id="7b9b1-130">테이블마다 하나의 속성을 저장하고 기본 테이블로 다시 조인하기 위해 속성 테이블에 있는 기본 테이블의 기본 키를 중복시키는 것이 편리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7b9b1-130">You may find it convenient to store one property per table and duplicate the primary key of the base table in the property tables for back joining with the base table.</span></span>  
  
-   <span data-ttu-id="7b9b1-131">속성의 상대적 순서를 유지하려면 상대적 순서에 대해 개별 열을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b9b1-131">If you want to maintain the relative order of the properties, you have to introduce a separate column for the relative order.</span></span>  
  
-   <span data-ttu-id="7b9b1-132">속성 테이블을 유지 관리하기 위해 XML 열에 트리거를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="7b9b1-132">Create triggers on the XML column to maintain the property tables.</span></span> <span data-ttu-id="7b9b1-133">트리거 내에서 다음 중 하나를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="7b9b1-133">Within the triggers, do one of the following:</span></span>  
  
    -   <span data-ttu-id="7b9b1-134">`xml` **Nodes ()** 및 **value ()** 와 같은 데이터 형식 메서드를 사용 하 여 속성 테이블의 행을 삽입 하 고 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b9b1-134">Use `xml` data type methods, such as **nodes()** and **value()**, to insert and delete rows of the property tables.</span></span>  
  
    -   <span data-ttu-id="7b9b1-135">속성 테이블의 행을 삽입 및 삭제하기 위해 CLR(공용 언어 런타임)에 스트리밍 테이블 반환 함수를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="7b9b1-135">Create streaming table-valued functions in the common language runtime (CLR) to insert and delete rows of the property tables.</span></span>  
  
    -   <span data-ttu-id="7b9b1-136">속성 테이블에 대한 SQL 액세스 및 기본 테이블의 XML 열에 대한 XML 액세스를 위한 쿼리를 작성하고 해당 기본 키를 사용하여 테이블 간 조인을 포함시킵니다.</span><span class="sxs-lookup"><span data-stu-id="7b9b1-136">Write queries for SQL access to the property tables and for XML access to the XML column in the base table, with joins between the tables by using their primary key.</span></span>  
  
### <a name="example-create-a-property-table"></a><span data-ttu-id="7b9b1-137">예제: 속성 테이블 만들기</span><span class="sxs-lookup"><span data-stu-id="7b9b1-137">Example: Create a Property Table</span></span>  
 <span data-ttu-id="7b9b1-138">이해를 돕기 위해 저자의 이름을 승격해야 한다고 가정해 보십시오.</span><span class="sxs-lookup"><span data-stu-id="7b9b1-138">For illustration, assume that you want to promote the first name of the authors.</span></span> <span data-ttu-id="7b9b1-139">책에는 한 명 이상의 저자가 있으므로 이름은 다중 값 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="7b9b1-139">Books have one or more authors, so that first name is a multivalued property.</span></span> <span data-ttu-id="7b9b1-140">각 이름은 속성 테이블의 별개의 행에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="7b9b1-140">Each first name is stored in a separate row of a property table.</span></span> <span data-ttu-id="7b9b1-141">기본 테이블의 기본 키는 역 조인을 위해 속성 테이블에 중복됩니다.</span><span class="sxs-lookup"><span data-stu-id="7b9b1-141">The primary key of the base table is duplicated in the property table for back join.</span></span>  
  
```  
create table tblPropAuthor (propPK int, propAuthor varchar(max))  
```  
  
### <a name="example-create-a-user-defined-function-to-generate-a-rowset-from-an-xml-instance"></a><span data-ttu-id="7b9b1-142">예제: XML 인스턴스로부터 행 집합을 생성하기 위한 사용자 정의 함수 만들기</span><span class="sxs-lookup"><span data-stu-id="7b9b1-142">Example: Create a User-defined Function to Generate a Rowset from an XML Instance</span></span>  
 <span data-ttu-id="7b9b1-143">다음 테이블 반환 함수 udf_XML2Table은 기본 키 값과 XML 인스턴스를 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="7b9b1-143">The following table-valued function, udf_XML2Table, accepts a primary key value and an XML instance.</span></span> <span data-ttu-id="7b9b1-144">이 함수는 <`book`> 요소에 대한 모든 저자의 이름을 검색하고 기본 키와 이름의 쌍인 행 집합을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="7b9b1-144">It retrieves the first name of all authors of the <`book`> elements and returns a rowset of primary key, first name pairs.</span></span>  
  
```  
create function udf_XML2Table (@pk int, @xCol xml)  
returns @ret_Table table (propPK int, propAuthor varchar(max))  
with schemabinding  
as  
begin  
      insert into @ret_Table   
      select @pk, nref.value('.', 'varchar(max)')  
      from   @xCol.nodes('/book/author/first-name') R(nref)  
      return  
end  
```  
  
### <a name="example-create-triggers-to-populate-a-property-table"></a><span data-ttu-id="7b9b1-145">예제: 속성 테이블을 채우기 위한 트리거 만들기</span><span class="sxs-lookup"><span data-stu-id="7b9b1-145">Example: Create Triggers to Populate a Property Table</span></span>  
 <span data-ttu-id="7b9b1-146">삽입 트리거는 속성 테이블에 행을 삽입합니다.</span><span class="sxs-lookup"><span data-stu-id="7b9b1-146">The insert trigger inserts rows into the property table:</span></span>  
  
```  
create trigger trg_docs_INS on T for insert  
as  
      declare @wantedXML xml  
      declare @FK int  
      select @wantedXML = xCol from inserted  
      select @FK = PK from inserted  
  
   insert into tblPropAuthor  
   select * from dbo.udf_XML2Table(@FK, @wantedXML)  
```  
  
 <span data-ttu-id="7b9b1-147">삭제 트리거는 삭제된 행의 기본 키 값에 따라 속성 테이블에서 행을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="7b9b1-147">The delete trigger deletes the rows from the property table based on the primary key value of the deleted rows:</span></span>  
  
```  
create trigger trg_docs_DEL on T for delete  
as  
   declare @FK int  
   select @FK = PK from deleted  
   delete tblPropAuthor where propPK = @FK  
```  
  
 <span data-ttu-id="7b9b1-148">업데이트 트리거는 업데이트된 XML 인스턴스에 따라 속성 테이블에서 기존 행을 삭제하고 속성 테이블에 새 행을 삽입합니다.</span><span class="sxs-lookup"><span data-stu-id="7b9b1-148">The update trigger deletes the existing rows in the property table corresponding to the updated XML instance and inserts new rows into the property table:</span></span>  
  
```  
create trigger trg_docs_UPD  
on T  
for update  
as  
if update(xCol) or update(pk)  
begin  
      declare @FK int  
      declare @wantedXML xml  
      select @FK = PK from deleted  
      delete tblPropAuthor where propPK = @FK  
  
   select @wantedXML = xCol from inserted  
   select @FK = pk from inserted  
  
   insert into tblPropAuthor   
      select * from dbo.udf_XML2Table(@FK, @wantedXML)  
end  
```  
  
### <a name="example-find-xml-instances-whose-authors-have-the-same-first-name"></a><span data-ttu-id="7b9b1-149">예제: 저자의 이름이 같은 XML 인스턴스 찾기</span><span class="sxs-lookup"><span data-stu-id="7b9b1-149">Example: Find XML Instances Whose Authors Have the Same First Name</span></span>  
 <span data-ttu-id="7b9b1-150">XML 열에 쿼리를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7b9b1-150">The query can be formed on the XML column.</span></span> <span data-ttu-id="7b9b1-151">또는 속성 테이블에서 "David"라는 이름을 검색하고 기본 테이블에서 역 조인을 수행하여 XML 인스턴스를 반환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7b9b1-151">Alternatively, it can search the property table for first name "David" and perform a back join with the base table to return the XML instance.</span></span> <span data-ttu-id="7b9b1-152">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="7b9b1-152">For example:</span></span>  
  
```  
SELECT xCol   
FROM     T JOIN tblPropAuthor ON T.pk = tblPropAuthor.propPK  
WHERE    tblPropAuthor.propAuthor = 'David'  
```  
  
### <a name="example-solution-using-the-clr-streaming-table-valued-function"></a><span data-ttu-id="7b9b1-153">예제: CLR 스트리밍 테이블 반환 함수를 사용한 해결 방법</span><span class="sxs-lookup"><span data-stu-id="7b9b1-153">Example: Solution Using the CLR Streaming Table-valued Function</span></span>  
 <span data-ttu-id="7b9b1-154">이 해결 방법은 다음 단계로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="7b9b1-154">This solution is made up of the following steps:</span></span>  
  
1.  <span data-ttu-id="7b9b1-155">ISqlReader를 구현하고 XML 인스턴스에 경로 식을 적용하여 스트리밍 테이블 반환 출력을 생성하는 SqlReaderBase라는 CLR 클래스를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="7b9b1-155">Define a CLR class, SqlReaderBase, that implements ISqlReader and generates a streaming, table-valued output by applying a path expression on an XML instance.</span></span>  
  
2.  <span data-ttu-id="7b9b1-156">어셈블리 및 Transact-SQL 사용자 정의 함수를 만들어서 CLR 클래스를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="7b9b1-156">Create an assembly and a Transact-SQL user-defined function to start the CLR class.</span></span>  
  
3.  <span data-ttu-id="7b9b1-157">속성 테이블을 유지 관리하기 위한 사용자 정의 함수를 사용하여 삽입, 업데이트 및 삭제 트리거를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="7b9b1-157">Define the insert, update, and delete triggers by using the user-defined function to maintain a property tables.</span></span>  
  
 <span data-ttu-id="7b9b1-158">이렇게 하려면 먼저 스트리밍 CLR 함수를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="7b9b1-158">To do this, you first create the streaming CLR function.</span></span> <span data-ttu-id="7b9b1-159">`xml`데이터 형식은 ADO.NET에서 관리 되는 클래스 SqlXml으로 노출 되며 XmlReader를 반환 하는 **CreateReader ()** 메서드를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b9b1-159">The `xml` data type is exposed as a managed class SqlXml in ADO.NET and supports the **CreateReader()** method that returns an XmlReader.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7b9b1-160">이 섹션의 예제 코드에서는 XPathDocument 및 XPathNavigator가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="7b9b1-160">The example code in this section uses XPathDocument and XPathNavigator.</span></span> <span data-ttu-id="7b9b1-161">이를 통해 사용자는 모든 XML 문서를 메모리에 강제로 로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7b9b1-161">These force you to load all the XML documents into memory.</span></span> <span data-ttu-id="7b9b1-162">일부 큰 XML 문서를 처리하기 위해 애플리케이션에서 비슷한 코드를 사용하는 경우 이 코드는 확장할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7b9b1-162">If you are using similar code in your application to process several large XML documents, this code is not scalable.</span></span> <span data-ttu-id="7b9b1-163">대신 메모리 할당을 적게 유지하고 가능한 모든 경우에 스트리밍 인터페이스를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="7b9b1-163">Instead, keep memory allocations small and use streaming interfaces whenever possible.</span></span> <span data-ttu-id="7b9b1-164">성능에 대한 자세한 내용은 [CLR 통합 아키텍처](../../database-engine/dev-guide/architecture-of-clr-integration.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7b9b1-164">For more information about performance, see [Architecture of CLR Integration](../../database-engine/dev-guide/architecture-of-clr-integration.md).</span></span>  
  
```  
public class c_streaming_xml_tvf {  
   public static ISqlReader streaming_xml_tvf   
(SqlXml xmlDoc, string pathExpression) {  
      return (new TestSqlReaderBase (xmlDoc, pathExpression));  
   }  
}  
  
// Class that implements ISqlReader  
public class TestSqlReaderBase : ISqlReader {  
XPathNodeIterator m_iterator;           
   public SqlChars FirstName;  
// Metadata for current resultset  
private SqlMetaData[] m_rgSqlMetaData;        
  
   public TestSqlReaderBase (SqlXml xmlDoc, string pathExpression) {     
      // Variables for XPath navigation  
      XPathDocument xDoc;  
      XPathNavigator xNav;  
      XPathExpression xPath;  
  
      // Set sql metadata  
      m_rgSqlMetaData = new SqlMetaData[1];  
      m_rgSqlMetaData[0] = new SqlMetaData ("FirstName",    
SqlDbType.NVarChar,50);     
  
      //Set up the Navigator  
      if (!xmlDoc.IsNull)  
          xDoc = new XPathDocument (xmlDoc.CreateReader());  
      else  
          xDoc = new XPathDocument ();  
      xNav = xDoc.CreateNavigator();  
      xPath = xNav.Compile (pathExpression);  
      m_iterator = xNav.Select(xPath);  
   }  
   public bool Read() {  
      bool moreRows = true;  
      if (moreRows = m_iterator.MoveNext())  
         FirstName = new SqlChars (m_iterator.Current.Value);  
      return moreRows;  
   }  
}  
```  
  
 <span data-ttu-id="7b9b1-165">그런 다음 CLR 함수 streaming_xml_tvf에 해당하는 [!INCLUDE[tsql](../../includes/tsql-md.md)] 사용자 정의 함수인 SQL_streaming_xml_tvf(표시 안 됨)와 어셈블리를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="7b9b1-165">Next, create an assembly and a [!INCLUDE[tsql](../../includes/tsql-md.md)] user-defined function, SQL_streaming_xml_tvf (not shown), that corresponds to the CLR function, streaming_xml_tvf.</span></span> <span data-ttu-id="7b9b1-166">행 집합 생성을 위해 테이블 반환 함수인 CLR_udf_XML2Table을 정의하는 데 사용자 정의 함수가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="7b9b1-166">The user-defined function is used to define the table-valued function, CLR_udf_XML2Table, for rowset generation:</span></span>  
  
```  
create function CLR_udf_XML2Table (@pk int, @xCol xml)  
returns @ret_Table table (FK int, FirstName varchar(max))  
with schemabinding  
as  
begin  
      insert into @ret_Table   
   select @pk, FirstName   
   FROM   SQL_streaming_xml_tvf (@xCol, '/book/author/first-name')  
      return  
end  
```  
  
 <span data-ttu-id="7b9b1-167">마지막으로 "속성 테이블을 채우기 위한 트리거 만들기" 예에서 표시된 것과 같이 트리거를 정의하고 udf_XML2Table을 CLR_udf_XML2Table 함수로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="7b9b1-167">Finally, define triggers as shown in the example, "Create triggers to populate a property table", but replace udf_XML2Table with the CLR_udf_XML2Table function.</span></span> <span data-ttu-id="7b9b1-168">다음 예에는 삽입 트리거가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="7b9b1-168">The insert trigger is shown in the following example:</span></span>  
  
```  
create trigger CLR_trg_docs_INS on T for insert  
as  
   declare @wantedXML xml  
   declare @FK int  
   select @wantedXML = xCol from inserted  
   select @FK = PK from inserted  
  
   insert into tblPropAuthor  
      select *  
   from    dbo.CLR_udf_XML2Table(@FK, @wantedXML)  
```  
  
 <span data-ttu-id="7b9b1-169">삭제 트리거는 비-CLR 버전과 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="7b9b1-169">The delete trigger is identical to the non-CLR version.</span></span> <span data-ttu-id="7b9b1-170">하지만 업데이트 트리거는 udf_XML2Table() 함수를 CLR_udf_XML2Table() 함수로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="7b9b1-170">However, the update trigger just replaces the function udf_XML2Table() with CLR_udf_XML2Table().</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b9b1-171">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7b9b1-171">See Also</span></span>  
 [<span data-ttu-id="7b9b1-172">계산 열에 XML 사용</span><span class="sxs-lookup"><span data-stu-id="7b9b1-172">Use XML in Computed Columns</span></span>](use-xml-in-computed-columns.md)  
  
  
