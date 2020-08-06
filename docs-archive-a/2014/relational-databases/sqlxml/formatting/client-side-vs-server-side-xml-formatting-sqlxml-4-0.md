---
title: 클라이언트 쪽 및 서버 쪽 XML 서식 지정 (SQLXML 4.0) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- NESTED mode
- FOR XML clause, formatting
- client-side XML formatting
- server-side XPath
- server-side XML formatting
- AUTO mode
- client-side XPath
ms.assetid: f807ab7a-c5f8-4e61-9b00-23aebfabc47e
author: rothja
ms.author: jroth
ms.openlocfilehash: fa155fc6d346cb90de54e5599aca1c296623faa7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652708"
---
# <a name="client-side-vs-server-side-xml-formatting-sqlxml-40"></a><span data-ttu-id="6ed69-102">클라이언트 쪽 vs. 서버 쪽 XML 서식 지정(SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="6ed69-102">Client-side vs. Server-side XML Formatting (SQLXML 4.0)</span></span>
  <span data-ttu-id="6ed69-103">이 항목에서는 SQL XML의 클라이언트 쪽 XML 서식과 서버 쪽 XML 서식의 일반적인 차이점에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="6ed69-103">This topic describes the general differences between client-side and server-side XML formatting in SQLXML.</span></span>  
  
## <a name="multiple-rowset-queries-not-supported-in-client-side-formatting"></a><span data-ttu-id="6ed69-104">클라이언트 쪽 서식에서 지원되지 않는 여러 행 집합 쿼리</span><span class="sxs-lookup"><span data-stu-id="6ed69-104">Multiple Rowset Queries Not Supported in Client-side Formatting</span></span>  
 <span data-ttu-id="6ed69-105">클라이언트 쪽 XML 서식을 사용하는 경우 여러 행 집합을 생성하는 쿼리는 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6ed69-105">Queries that generate multiple rowsets are not supported when you use client-side XML formatting.</span></span> <span data-ttu-id="6ed69-106">예를 들어 가상 디렉터리에 클라이언트 쪽 서식을 지정했다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="6ed69-106">For example, assume you have a virtual directory in which you have client-side formatting specified.</span></span> <span data-ttu-id="6ed69-107">블록에 SELECT 문이 두 개 있는이 샘플 템플릿을 살펴보겠습니다 **\<sql:query>** .</span><span class="sxs-lookup"><span data-stu-id="6ed69-107">Consider this sample template, which has two SELECT statements in a **\<sql:query>** block:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <sql:query>  
     SELECT FirstName FROM Person.Contact FOR XML Nested;   
     SELECT LastName FROM Person.Contact FOR XML Nested    
  </sql:query>  
</ROOT>  
```  
  
 <span data-ttu-id="6ed69-108">애플리케이션 코드에서 이 템플릿을 실행할 수 있지만 클라이언트 쪽 XML 서식에서 여러 행 집합의 서식 설정을 지원하지 않기 때문에 오류가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="6ed69-108">You can execute this template in application code and an error is returned, because client-side XML formatting does not support formatting of multiple rowsets.</span></span> <span data-ttu-id="6ed69-109">별도의 두 블록에 쿼리를 지정 하는 경우 **\<sql:query>** 원하는 결과를 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6ed69-109">If you specify the queries in two separate **\<sql:query>** blocks, you will get the desired results.</span></span>  
  
## <a name="timestamp-maps-differently-in-client--vs-server-side-formatting"></a><span data-ttu-id="6ed69-110">클라이언트 쪽 서식과 서버 쪽 서식에서 서로 다르게 매핑되는 타임스탬프</span><span class="sxs-lookup"><span data-stu-id="6ed69-110">timestamp Maps Differently in Client- vs. Server-side Formatting</span></span>  
 <span data-ttu-id="6ed69-111">서버 쪽 XML 서식에서 `timestamp` 형식의 데이터베이스 열은 쿼리에 XMLDATA 옵션이 지정된 경우 i8 XDR 형식에 매핑됩니다.</span><span class="sxs-lookup"><span data-stu-id="6ed69-111">In server-side XML formatting, the database column of `timestamp` type maps to the i8 XDR type (when the XMLDATA option is specified in the query).</span></span>  
  
 <span data-ttu-id="6ed69-112">클라이언트 쪽 XML 서식에서 `timestamp` 형식의 데이터베이스 열은 쿼리에 이진 Base64 옵션이 지정되어 있는지 여부에 따라 `uri` 또는 `bin.base64` XDR 형식에 매핑됩니다.</span><span class="sxs-lookup"><span data-stu-id="6ed69-112">In client-side XML formatting, the database column of `timestamp` type maps to either the `uri` or the `bin.base64` XDR type (depending on whether the binary base64 option is specified in the query).</span></span> <span data-ttu-id="6ed69-113">`bin.base64`XDR 형식은 updategram 및 bulkload 기능을 사용 하는 경우에 유용 합니다 .이 형식은 형식으로 변환 되기 때문입니다 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] `timestamp` .</span><span class="sxs-lookup"><span data-stu-id="6ed69-113">The `bin.base64` XDR type is useful if you use the updategram and bulkload features, because this type is converted to the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] `timestamp` type.</span></span> <span data-ttu-id="6ed69-114">이러한 변환 작업을 통해 삽입, 업데이트 또는 삭제 작업이 성공합니다.</span><span class="sxs-lookup"><span data-stu-id="6ed69-114">This way, the insert, update, or delete operation succeeds.</span></span>  
  
## <a name="deep-variants-are-used-in-server-side-formatting"></a><span data-ttu-id="6ed69-115">서버 쪽 서식에는 중첩이 많은 VARIANT가 사용됨</span><span class="sxs-lookup"><span data-stu-id="6ed69-115">Deep VARIANTs Are Used in Server-side Formatting</span></span>  
 <span data-ttu-id="6ed69-116">서버 쪽 XML 서식에는 중첩이 많은 VARIANT 형식이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="6ed69-116">In server-side XML formatting, the deep types of a VARIANT type are used.</span></span> <span data-ttu-id="6ed69-117">클라이언트 쪽 XML 서식을 사용하는 경우 변형은 유니코드 문자열로 변환되고 VARIANT의 하위 유형은 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6ed69-117">If you use client-side XML formatting, the variants are converted to Unicode string, and the subtypes of VARIANT are not used.</span></span>  
  
## <a name="nested-mode-vs-auto-mode"></a><span data-ttu-id="6ed69-118">NESTED 모드와 AUTO 모드</span><span class="sxs-lookup"><span data-stu-id="6ed69-118">NESTED Mode vs. AUTO Mode</span></span>  
 <span data-ttu-id="6ed69-119">클라이언트 쪽 FOR XML의 NESTED 모드는 서버 쪽 FOR XML의 AUTO 모드와 비슷합니다. 단, 다음 사항은 예외입니다.</span><span class="sxs-lookup"><span data-stu-id="6ed69-119">The NESTED mode of the client-side FOR XML is similar to the AUTO mode of server-side FOR XML, with the following exceptions:</span></span>  
  
### <a name="when-you-query-views-using-auto-mode-on-the-server-side-the-view-name-is-returned-as-the-element-name-in-the-resulting-xml"></a><span data-ttu-id="6ed69-120">서버 쪽에서 AUTO 모드를 사용하여 뷰를 쿼리하면 뷰 이름이 결과 XML에 요소 이름으로 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="6ed69-120">When you query views using AUTO mode on the server-side, the view name is returned as the element name in the resulting XML.</span></span>  
 <span data-ttu-id="6ed69-121">예를 들어 AdventureWorksdatabase의 Person 테이블에 다음 뷰가 생성 되어 있다고 가정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ed69-121">For example, assume that the following view is created on the Person.Contact table in the AdventureWorksdatabase:</span></span>  
  
```  
CREATE VIEW ContactView AS (SELECT ContactID as CID,  
                               FirstName  as FName,  
                               LastName  as LName  
                        FROM Person.Contact)  
```  
  
 <span data-ttu-id="6ed69-122">다음 템플릿에서는 ContactView 뷰에 대해 쿼리를 지정하고 서버 쪽 XML 서식도 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="6ed69-122">The following template specifies a query against the ContactView view, and also specifies server-side XML formatting:</span></span>  
  
```  
 <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <sql:query client-side-xml="0">  
    SELECT *  
    FROM   ContactView  
    FOR XML AUTO  
  </sql:query>  
</ROOT>  
```  
  
 <span data-ttu-id="6ed69-123">템플릿을 실행하면 다음 XML이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="6ed69-123">When you execute the template, the following XML is returned.</span></span> <span data-ttu-id="6ed69-124">(일부 결과만 표시 됩니다.) 요소 이름은 쿼리가 실행 되는 뷰의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="6ed69-124">(Only partial results are shown.) Note that the element names are the names of the views against which the query is executed.</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <ContactView CID="1" FName="Gustavo" LName="Achong" />   
  <ContactView CID="2" FName="Catherine" LName="Abel" />   
...  
</ROOT>  
```  
  
 <span data-ttu-id="6ed69-125">해당 NESTED 모드를 사용하여 클라이언트 쪽 XML 서식을 지정하면 기본 테이블 이름이 결과 XML에 요소 이름으로 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="6ed69-125">When you specify client-side XML formatting by using the corresponding NESTED mode, the base table name(s) are returned as the element name(s) in the resulting XML.</span></span> <span data-ttu-id="6ed69-126">예를 들어 다음 수정 된 템플릿은 동일한 SELECT 문을 실행 하지만 XML 서식 지정은 클라이언트 쪽에서 수행 됩니다. 즉, **클라이언트 쪽 xml** 은 템플릿에서 true로 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6ed69-126">For example, the following revised template executes the same SELECT statement, but the XML formatting is performed on the client-side (that is, **client-side-xml** is set to true in the template):</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <sql:query client-side-xml="1">  
    SELECT *  
    FROM   ContactView  
    FOR XML NESTED  
  </sql:query>  
</ROOT>  
```  
  
 <span data-ttu-id="6ed69-127">이 템플릿을 실행하면 다음과 같은 XML이 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="6ed69-127">Executing this template produces the following XML.</span></span> <span data-ttu-id="6ed69-128">이 경우 요소 이름은 기본 테이블 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="6ed69-128">Note that the element name is the base table name in this case.</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Person.Contact CID="1" FName="Gustavo" LName="Achong" />   
  <Person.Contact CID="2" FName="Catherine" LName="Abel" />   
...  
</ROOT>  
```  
  
### <a name="when-you-use-auto-mode-of-the-server-side-for-xml-the-table-aliases-specified-in-the-query-are-returned-as-element-names-in-the-resulting-xml"></a><span data-ttu-id="6ed69-129">서버 쪽 FOR XML의 AUTO 모드를 사용하는 경우 쿼리에 지정된 테이블 별칭이 결과 XML에 요소 이름으로 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="6ed69-129">When you use AUTO mode of the server-side FOR XML, the table aliases specified in the query are returned as element names in the resulting XML.</span></span>  
 <span data-ttu-id="6ed69-130">예를 들어 다음 템플릿을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="6ed69-130">For example, consider this template:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <sql:query client-side-xml="0">  
    SELECT FirstName as fname,  
           LastName as lname  
    FROM   Person.Contact C  
    FOR XML AUTO  
  </sql:query>  
</ROOT>  
```  
  
 <span data-ttu-id="6ed69-131">이 템플릿을 실행하면 다음과 같은 XML이 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="6ed69-131">Executing the template produces the following XML:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <C fname="Gustavo" lname="Achong" />   
  <C fname="Catherine" lname="Abel" />   
...  
</ROOT>   
```  
  
 <span data-ttu-id="6ed69-132">클라이언트 쪽 FOR XML의 NESTED 모드를 사용하는 경우 테이블 이름이 결과 XML에 요소 이름으로 반환되고</span><span class="sxs-lookup"><span data-stu-id="6ed69-132">When you use the NESTED mode of the client-side FOR XML, the table names are returned as element names in the resulting XML.</span></span> <span data-ttu-id="6ed69-133">쿼리에 지정 된 테이블 별칭은 사용 되지 않습니다. 예를 들어 다음 템플릿을 살펴보세요.</span><span class="sxs-lookup"><span data-stu-id="6ed69-133">(Table aliases that are specified in the query are not used.) For example, consider this template:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <sql:query client-side-xml="1">  
    SELECT FirstName as fname,  
           LastName as lname  
    FROM   Person.Contact C  
    FOR XML NESTED  
  </sql:query>  
</ROOT>  
```  
  
 <span data-ttu-id="6ed69-134">이 템플릿을 실행하면 다음과 같은 XML이 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="6ed69-134">Executing the template produces the following XML:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Person.Contact fname="Gustavo" lname="Achong" />   
  <Person.Contact fname="Catherine" lname="Abel" />   
...  
</ROOT>  
```  
  
### <a name="if-you-have-a-query-that-returns-columns-as-dbobject-queries-you-cannot-use-aliases-for-these-columns"></a><span data-ttu-id="6ed69-135">쿼리에서 열을 dbobject 쿼리로 반환하는 경우 해당 열의 별칭을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6ed69-135">If you have a query that returns columns as dbobject queries, you cannot use aliases for these columns.</span></span>  
 <span data-ttu-id="6ed69-136">예를 들어 다음 템플릿을 살펴보겠습니다. 이 템플릿에서는 직원 ID와 사진을 반환하는 쿼리를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="6ed69-136">For example, consider the following template, which executes a query that returns an employee ID and a photo.</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
<sql:query client-side-xml="1">  
   SELECT ProductPhotoID, LargePhoto as P  
   FROM   Production.ProductPhoto  
   WHERE  ProductPhotoID=5  
   FOR XML NESTED, elements  
</sql:query>  
</ROOT>  
```  
  
 <span data-ttu-id="6ed69-137">이 템플릿을 실행하면 Photo 열이 dbobject 쿼리로 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="6ed69-137">Executing this template returns the Photo column as a dbobject query.</span></span> <span data-ttu-id="6ed69-138">이 dbobject 쿼리에서 `@P`는 존재하지 않는 열 이름을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="6ed69-138">In this dbobject query, `@P` refers to a column name that does not exist.</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Production.ProductPhoto>  
    <ProductPhotoID>5</ProductPhotoID>  
    <LargePhoto>dbobject/Production.ProductPhoto[@ProductPhotoID='5']/@P</LargePhoto>  
  </Production.ProductPhoto>  
</ROOT>  
```  
  
 <span data-ttu-id="6ed69-139">XML 형식이 서버 (**클라이언트 쪽 xml = "0"**)에서 수행 되는 경우에는 별칭을 사용 하 여 실제 테이블 및 열 이름이 반환 되는 dbobject 쿼리를 반환 하는 열에 별칭을 사용할 수 있습니다 (별칭을 지정한 경우에도).</span><span class="sxs-lookup"><span data-stu-id="6ed69-139">If the XML formatting is done on the server (**client-side-xml="0"**), you can use the alias for the columns that return dbobject queries in which actual table and column names are returned (even if you have aliases specified).</span></span> <span data-ttu-id="6ed69-140">예를 들어 다음 템플릿은 쿼리를 실행 하 고 XML 서식 지정은 서버에서 수행 됩니다. 즉, **클라이언트 쪽 xml** 옵션이 지정 되지 않고 **클라이언트에서 실행** 옵션이 가상 루트에 대해 선택 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6ed69-140">For example, the following template executes a query, and the XML formatting is done on the server (the **client-side-xml** option is not specified and the **Run On Client** option is not selected for the virtual root).</span></span> <span data-ttu-id="6ed69-141">또한 이 쿼리는 클라이언트 쪽 NESTED 모드가 아니라 AUTO 모드를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="6ed69-141">The query also specifies AUTO mode (not the client-side NESTED mode).</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
<sql:query   
   SELECT ProductPhotoID, LargePhoto as P  
   FROM   Production.ProductPhoto  
   WHERE  ProductPhotoID=5  
   FOR XML AUTO, elements  
</sql:query>  
</ROOT>  
```  
  
 <span data-ttu-id="6ed69-142">이 템플릿을 실행하면 다음 XML 문서가 반환됩니다. 이 경우 LargePhoto 열에 대한 dbobject 쿼리에 별칭이 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6ed69-142">When this template is executed, the following XML document is returned (note that aliases are not used in the dbobject query for the LargePhoto column):</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Production.ProductPhoto>  
    <ProductPhotoID>5</ProductPhotoID>  
    <LargePhoto>dbobject/Production.ProductPhoto[@ProductPhotoID='5']/@LargePhoto</LargePhoto>  
  </Production.ProductPhoto>  
</ROOT>  
```  
  
### <a name="client-side-vs-server-side-xpath"></a><span data-ttu-id="6ed69-143">클라이언트 쪽 XPath와 서버 쪽 XPath</span><span class="sxs-lookup"><span data-stu-id="6ed69-143">Client-side vs. Server-side XPath</span></span>  
 <span data-ttu-id="6ed69-144">클라이언트 쪽 XPath와 서버 쪽 XPath는 다음을 제외하고는 동일하게 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="6ed69-144">Client-side XPath and server-side XPath work the same except for these differences:</span></span>  
  
-   <span data-ttu-id="6ed69-145">클라이언트 쪽 XPath 쿼리를 사용할 때 적용되는 데이터 변환은 서버 쪽 XPath 쿼리를 사용할 때 적용되는 데이터 변환과 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="6ed69-145">The data conversions that are applied when you use client-side XPath queries are different from those that are applied when you use server-side XPath queries.</span></span> <span data-ttu-id="6ed69-146">클라이언트 쪽 XPath에는 CONVERT 모드 126 대신 CAST가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="6ed69-146">Client-side XPath uses CAST instead of CONVERT mode 126.</span></span>  
  
-   <span data-ttu-id="6ed69-147">템플릿에서 **클라이언트-xml = "0"** (false)을 지정 하면 서버 쪽 xml 서식 지정을 요청 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="6ed69-147">When you specify **client-side-xml="0"** (false) in a template, you are requesting server-side XML formatting.</span></span> <span data-ttu-id="6ed69-148">따라서 서버에서는 NESTED 옵션이 인식되지 않으므로 FOR XML NESTED를 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6ed69-148">Therefore, you cannot specify FOR XML NESTED because the server does not recognize the NESTED option.</span></span> <span data-ttu-id="6ed69-149">이렇게 하면 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="6ed69-149">This generates an error.</span></span> <span data-ttu-id="6ed69-150">서버에서 인식되는 AUTO, RAW 또는 EXPLICIT 모드를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ed69-150">You must use the AUTO, RAW, or EXPLICIT modes, which the server does recognize.</span></span>  
  
-   <span data-ttu-id="6ed69-151">템플릿에서 **클라이언트-xml = "1"** (true)을 지정 하면 클라이언트 쪽 xml 서식 지정을 요청 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="6ed69-151">When you specify **client-side-xml="1"** (true) in a template, you are requesting client-side XML formatting.</span></span> <span data-ttu-id="6ed69-152">이 경우 FOR XML NESTED를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6ed69-152">In this case, you can specify FOR XML NESTED.</span></span> <span data-ttu-id="6ed69-153">FOR XML AUTO를 지정 하면 **클라이언트 쪽 xml = "1"** 이 템플릿에 지정 된 경우에도 서버 쪽에서 xml 서식 지정이 수행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6ed69-153">If you specify FOR XML AUTO, the XML formatting occurs on the server side although **client-side-xml="1"** is specified in the template.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ed69-154">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6ed69-154">See Also</span></span>  
 <span data-ttu-id="6ed69-155">[XML 보안 고려 사항은 SQLXML 4.0을 &#40;&#41;](../../sqlxml-annotated-xsd-schemas-xpath-queries/security/for-xml-security-considerations-sqlxml-4-0.md) </span><span class="sxs-lookup"><span data-stu-id="6ed69-155">[FOR XML Security Considerations &#40;SQLXML 4.0&#41;](../../sqlxml-annotated-xsd-schemas-xpath-queries/security/for-xml-security-considerations-sqlxml-4-0.md) </span></span>  
 <span data-ttu-id="6ed69-156">[클라이언트 쪽 XML 서식 지정 &#40;SQLXML 4.0&#41;](client-side-xml-formatting-sqlxml-4-0.md) </span><span class="sxs-lookup"><span data-stu-id="6ed69-156">[Client-side XML Formatting &#40;SQLXML 4.0&#41;](client-side-xml-formatting-sqlxml-4-0.md) </span></span>  
 [<span data-ttu-id="6ed69-157">서버 쪽 XML 서식 지정 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="6ed69-157">Server-side XML Formatting &#40;SQLXML 4.0&#41;</span></span>](server-side-xml-formatting-sqlxml-4-0.md)  
  
  
