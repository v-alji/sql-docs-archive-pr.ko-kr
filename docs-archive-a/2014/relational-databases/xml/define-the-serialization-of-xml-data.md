---
title: XML 데이터 직렬화 정의 | Microsoft 문서
ms.custom: ''
ms.date: 10/18/2019
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- entitization rules [XML in SQL Server]
- serialization
- reparsing serialized XML structures
- encoding [XML in SQL Server]
- XML [SQL Server], serialization
- xml data type [SQL Server], serialization
- typed XML
ms.assetid: 42b0b5a4-bdd6-4a60-b451-c87f14758d4b
author: rothja
ms.author: jroth
ms.openlocfilehash: df87dddd9fd4cf067125314c9d798eaa42523576
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660922"
---
# <a name="define-the-serialization-of-xml-data"></a><span data-ttu-id="f4473-102">XML 데이터 직렬화 정의</span><span class="sxs-lookup"><span data-stu-id="f4473-102">Define the Serialization of XML Data</span></span>
  <span data-ttu-id="f4473-103">xml 데이터 형식을 명시적이나 암시적으로 SQL 문자열 또는 이진 유형으로 캐스팅할 때 xml 데이터 형식의 콘텐츠는 이 항목에 설명된 규칙에 따라 직렬화됩니다.</span><span class="sxs-lookup"><span data-stu-id="f4473-103">When casting the xml data type explicitly or implicitly to a SQL string or binary type, the content of the xml data type will be serialized according to the rules outlined in this topic.</span></span>  
  
## <a name="serialization-encoding"></a><span data-ttu-id="f4473-104">직렬화 인코딩</span><span class="sxs-lookup"><span data-stu-id="f4473-104">Serialization Encoding</span></span>  
 <span data-ttu-id="f4473-105">SQL 대상 유형이 VARBINARY인 경우 결과는 UTF-16 바이트 순서 표시가 앞에 표시되어 있지만 XML 선언이 없는 UTF-16으로 직렬화됩니다.</span><span class="sxs-lookup"><span data-stu-id="f4473-105">If the SQL target type is VARBINARY, the result is serialized in UTF-16 with a UTF-16-byte order mark in front, but without an XML declaration.</span></span> <span data-ttu-id="f4473-106">대상 유형이 너무 작으면 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="f4473-106">If the target type is too small, an error is raised.</span></span>  
  
 <span data-ttu-id="f4473-107">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="f4473-107">For example:</span></span>  
  
```sql
select CAST(CAST(N'<Δ/>' as XML) as VARBINARY(MAX))  
```  
  
 <span data-ttu-id="f4473-108">다음은 결과입니다.</span><span class="sxs-lookup"><span data-stu-id="f4473-108">This is the result:</span></span>  
  
```  
0xFFFE3C0094032F003E00  
```  
  
 <span data-ttu-id="f4473-109">SQL 대상 유형이 NVARCHAR 또는 NCHAR인 경우 결과는 앞에 바이트 순서 표시가 없고 XML 선언이 없는 UTF-16으로 직렬화됩니다.</span><span class="sxs-lookup"><span data-stu-id="f4473-109">If the SQL target type is NVARCHAR or NCHAR, the result is serialized in UTF-16 without the byte order mark in front and without an XML declaration.</span></span> <span data-ttu-id="f4473-110">대상 유형이 너무 작으면 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="f4473-110">If the target type is too small, an error is raised.</span></span>  
  
 <span data-ttu-id="f4473-111">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="f4473-111">For example:</span></span>  
  
```sql
select CAST(CAST(N'<Δ/>' as XML) as NVARCHAR(MAX))  
```  
  
 <span data-ttu-id="f4473-112">다음은 결과입니다.</span><span class="sxs-lookup"><span data-stu-id="f4473-112">This is the result:</span></span>  
  
```  
<Δ/>  
```  
  
 <span data-ttu-id="f4473-113">SQL 대상 유형이 VARCHAR 또는 NCHAR인 경우 결과는 바이트 순서 표시나 XML 선언이 없이 데이터베이스의 데이터 정렬 코드 페이지에 따른 인코딩으로 직렬화됩니다.</span><span class="sxs-lookup"><span data-stu-id="f4473-113">If the SQL target type is VARCHAR or NCHAR, the result is serialized in the encoding that corresponds to the database's collation code page without a byte order mark or XML declaration.</span></span> <span data-ttu-id="f4473-114">대상 유형이 너무 작거나 값을 대상 데이터 정렬 코드 페이지에 매핑할 수 없는 경우 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="f4473-114">If the target type is too small or the value cannot be mapped to the target collation code page, an error is raised.</span></span>  
  
 <span data-ttu-id="f4473-115">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="f4473-115">For example:</span></span>  
  
```sql
select CAST(CAST(N'<Δ/>' as XML) as VARCHAR(MAX))  
```  
  
 <span data-ttu-id="f4473-116">현재 데이터 정렬의 코드 페이지가 유니코드 문자 & # x10300;을 (를) 나타내지 않거나 특정 인코딩으로 표시 되는 경우이로 인해 오류가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f4473-116">This may result in an error, if the current collation's code page cannot represent the Unicode character &#x10300;, or it will represent it in the specific encoding.</span></span>  
  
 <span data-ttu-id="f4473-117">XML 결과를 클라이언트 쪽에 반환할 때 데이터는 UTF-16 인코딩으로 보내집니다.</span><span class="sxs-lookup"><span data-stu-id="f4473-117">When returning XML results to the client side, the data will be sent in UTF-16 encoding.</span></span> <span data-ttu-id="f4473-118">그런 다음 클라이언트 쪽 공급자는 해당 API 규칙에 따라 이 데이터를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="f4473-118">The client-side provider will then expose the data according to its API rules.</span></span>  
  
## <a name="serialization-of-the-xml-structures"></a><span data-ttu-id="f4473-119">XML 구조의 직렬화</span><span class="sxs-lookup"><span data-stu-id="f4473-119">Serialization of the XML Structures</span></span>  
 <span data-ttu-id="f4473-120">**xml** 데이터 형식의 콘텐츠는 일반적인 방식으로 직렬화됩니다.</span><span class="sxs-lookup"><span data-stu-id="f4473-120">The content of an **xml** data type is serialized in the usual way.</span></span> <span data-ttu-id="f4473-121">특히 요소 노드는 요소 태그로 매핑되고 텍스트 노드는 텍스트 콘텐츠로 매핑됩니다.</span><span class="sxs-lookup"><span data-stu-id="f4473-121">Specifically, element nodes are mapped to element markup, and text nodes are mapped to text content.</span></span> <span data-ttu-id="f4473-122">하지만 문자가 엔터티화되는 경우와 형식화된 원자 값이 직렬화되는 방식은 다음 섹션에 설명됩니다.</span><span class="sxs-lookup"><span data-stu-id="f4473-122">However, the circumstances under which characters are entitized and how typed atomic values are serialized are described in the following sections.</span></span>  
  
## <a name="entitization-of-xml-characters-during-serialization"></a><span data-ttu-id="f4473-123">직렬화 중 XML 문자 엔터티화</span><span class="sxs-lookup"><span data-stu-id="f4473-123">Entitization of XML Characters During Serialization</span></span>  
 <span data-ttu-id="f4473-124">직렬화된 모든 XML 구조는 다시 구문 분석될 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f4473-124">Every serialized XML structure should be capable of being reparsed.</span></span> <span data-ttu-id="f4473-125">따라서 일부 문자는 XML 파서의 정규화 단계를 통해 문자의 왕복 기능을 보존할 수 있도록 엔터티화된 방식으로 직렬화되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f4473-125">Therefore, some characters have to be serialized in an entitized way to preserve the round-trip capability of the characters through the XML parser's normalization phase .</span></span> <span data-ttu-id="f4473-126">하지만 일부 문자는 문서가 잘 작성되고 따라서 구문 분석될 수 있도록 엔터티화되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f4473-126">However, some characters have to be entitized so that the document is well-formed and, therefore, able to be parsed.</span></span> <span data-ttu-id="f4473-127">다음은 직렬화 중에 적용되는 엔터티화 규칙입니다.</span><span class="sxs-lookup"><span data-stu-id="f4473-127">Following are the entitization rules that apply during serialization:</span></span>  
  
-   <span data-ttu-id="f4473-128">&, \<, and > 문자는 특성 값이나 요소 콘텐츠 내에 있는 경우 항상 &amp;, &lt; 및 &gt;로 매핑됩니다.</span><span class="sxs-lookup"><span data-stu-id="f4473-128">The characters &, \<, and > are always entitized to &amp;, &lt;, and &gt; respectively, if they occur inside an attribute value or element content.</span></span>  
  
-   <span data-ttu-id="f4473-129">SQL Server는 특성 값을 묶을 때 따옴표(U+0022)를 사용하기 때문에 특성 값에 있는 따옴표는 &quot;로 엔터티화됩니다.</span><span class="sxs-lookup"><span data-stu-id="f4473-129">Because SQL Server uses a quotation mark (U+0022) for enclosing attribute values, the quotation mark in attribute values is entitized as &quot;.</span></span>  
  
-   <span data-ttu-id="f4473-130">서로게이트 쌍은 서버에서만 캐스팅될 때 단일 숫자 문자 참조로 엔터티화됩니다.</span><span class="sxs-lookup"><span data-stu-id="f4473-130">A surrogate pair is entitized as a single numeric character reference, when casting on the server only.</span></span> <span data-ttu-id="f4473-131">예를 들어 서로게이트 쌍인 U+D800 U+DF00은 숫자 문자 참조인 &\#x00010300;으로 엔터티화됩니다.</span><span class="sxs-lookup"><span data-stu-id="f4473-131">For example the surrogate pair U+D800 U+DF00 is entitized to the numeric character reference &\#x00010300;.</span></span>  
  
-   <span data-ttu-id="f4473-132">TAB(U+0009) 및 줄 바꿈(LF, U+000A) 문자가 구문 분석 중에 정규화되지 않도록 보호하기 위해 이러한 문자는 특성 값 내에서 해당 숫자 문자 참조인 &\#x9; 및 &\#xA;로 엔터티화됩니다.</span><span class="sxs-lookup"><span data-stu-id="f4473-132">To protect a TAB (U+0009) and a linefeed (LF, U+000A) from being normalized during parsing, they are entitized to their numeric character references &\#x9; and &\#xA; respectively, inside attribute values.</span></span>  
  
-   <span data-ttu-id="f4473-133">캐리지 리턴(CR, U+000D) 문자가 구문 분석 중에 정규화되지 않도록 보호하기 위해 이러한 문자는 특성 값 및 요소 콘텐츠 내에서 해당 숫자 문자 참조인 &\#xD;로 엔터티화됩니다.</span><span class="sxs-lookup"><span data-stu-id="f4473-133">To prevent a carriage return (CR, U+000D) from being normalized during parsing, it is entitized to its numeric character reference, &\#xD; inside both attribute values and element content.</span></span>  
  
-   <span data-ttu-id="f4473-134">공백만 포함된 텍스트 노드를 보호하기 위해 공백 문자 중 하나(일반적으로 마지막 공백 문자)는 해당 숫자 문자 참조로 엔터티화됩니다.</span><span class="sxs-lookup"><span data-stu-id="f4473-134">To protect text nodes that only contain white space, one of the white-space characters, generally the last one, is entitized as its numeric character reference.</span></span> <span data-ttu-id="f4473-135">이러한 방식으로 다시 구문 분석 과정에서 구문 분석 중의 공백 처리 설정에 관계없이 공백 문자 텍스트 노드를 보존합니다.</span><span class="sxs-lookup"><span data-stu-id="f4473-135">In this way, reparsing preserves the white-space text node, regardless of the setting of the white-space handling during parsing.</span></span>  
  
 <span data-ttu-id="f4473-136">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="f4473-136">For example:</span></span>  
  
```sql
declare @u NVARCHAR(50)  
set @u = N'<a a="  
    '+NCHAR(0xD800)+NCHAR(0xDF00)+N'>">   '+NCHAR(0xA)+N'</a>'  
select CAST(CONVERT(XML,@u,1) as NVARCHAR(50))  
```  
  
 <span data-ttu-id="f4473-137">다음은 결과입니다.</span><span class="sxs-lookup"><span data-stu-id="f4473-137">This is the result:</span></span>  
  
```  
<a a="  
    𐌀>">     
</a>  
```  
  
 <span data-ttu-id="f4473-138">마지막 공백 보호 규칙을 적용하지 않으려면 **xml** 에서 문자열이나 이진 유형으로 캐스팅할 때 명시적 CONVERT 옵션 1을 사용하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f4473-138">If you do not want to apply the last white-space protection rule, you can use the explicit CONVERT option 1 when casting from **xml** to a string or binary type.</span></span> <span data-ttu-id="f4473-139">예를 들어 엔터티화를 방지하려면 다음을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f4473-139">For example, to avoid entitization, you can do the following:</span></span>  
  
```sql
select CONVERT(NVARCHAR(50), CONVERT(XML, '<a>   </a>', 1), 1)  
```  
  
 <span data-ttu-id="f4473-140">[query() 메서드(xml 데이터 형식)](/sql/t-sql/xml/query-method-xml-data-type) 는 xml 데이터 형식 인스턴스를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="f4473-140">Note that, the [query() Method (xml Data Type)](/sql/t-sql/xml/query-method-xml-data-type) results in an xml data type instance.</span></span> <span data-ttu-id="f4473-141">따라서 문자열이나 이진 유형으로 캐스팅된 **query()** 메서드의 결과는 앞에서 설명한 규칙에 따라 엔터티화됩니다.</span><span class="sxs-lookup"><span data-stu-id="f4473-141">Therefore, any result of the **query()** method that is cast to a string or binary type is entitized according to the previously described rules.</span></span> <span data-ttu-id="f4473-142">엔터티화되지 않은 문자열 값을 가져오려면 대신 [value() 메서드(xml 데이터 형식)](/sql/t-sql/xml/value-method-xml-data-type) 를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f4473-142">If you want to obtain the string values that are not entitized, you should use the [value() Method (xml Data Type)](/sql/t-sql/xml/value-method-xml-data-type) instead.</span></span> <span data-ttu-id="f4473-143">다음은 **query()** 메서드를 사용하는 예제입니다.</span><span class="sxs-lookup"><span data-stu-id="f4473-143">Following is an example of using the **query()** method:</span></span>  
  
```sql
declare @x xml  
set @x = N'<a>This example contains an entitized char: <.</a>'  
select @x.query('/a/text()')  
```  
  
 <span data-ttu-id="f4473-144">다음은 결과입니다.</span><span class="sxs-lookup"><span data-stu-id="f4473-144">This is the result:</span></span>  
  
```  
This example contains an entitized char: <.  
```  
  
 <span data-ttu-id="f4473-145">다음은 **value()** 메서드를 사용하는 예제입니다.</span><span class="sxs-lookup"><span data-stu-id="f4473-145">Following is an example of using the **value()** method:</span></span>  
  
```sql
select @x.value('(/a/text())[1]', 'nvarchar(100)')  
```  
  
 <span data-ttu-id="f4473-146">다음은 결과입니다.</span><span class="sxs-lookup"><span data-stu-id="f4473-146">This is the result:</span></span>  
  
```  
This example contains an entitized char: <.  
```  
  
## <a name="serializing-a-typed-xml-data-type"></a><span data-ttu-id="f4473-147">형식화된 xml 데이터 형식 직렬화</span><span class="sxs-lookup"><span data-stu-id="f4473-147">Serializing a Typed xml Data Type</span></span>  
 <span data-ttu-id="f4473-148">형식화된 **xml** 데이터 형식 항목에는 해당 XML 스키마 유형에 따라 형식화된 값이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="f4473-148">A typed **xml** data type instance contains values that are typed according to their XML schema types.</span></span> <span data-ttu-id="f4473-149">이러한 값은 xs:string으로 캐스팅된 XQuery가 만드는 형식과 동일한 형식으로 해당 XML 스키마 유형에 따라 직렬화됩니다.</span><span class="sxs-lookup"><span data-stu-id="f4473-149">These values are serialized according to their XML schema type in the same format as the XQuery cast to xs:string produces.</span></span> <span data-ttu-id="f4473-150">자세한 내용은 [XQuery의 형식 캐스트 규칙](/sql/xquery/type-casting-rules-in-xquery)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f4473-150">For more information, see [Type Casting Rules in XQuery](/sql/xquery/type-casting-rules-in-xquery).</span></span>  
  
 <span data-ttu-id="f4473-151">예를 들어 xs:double 값 1.34e1은 아래 예에서와 같이 13.4로 직렬화됩니다.</span><span class="sxs-lookup"><span data-stu-id="f4473-151">For example, the xs:double value 1.34e1 is serialized to 13.4 as shown in the following example:</span></span>  
  
```sql
declare @x xml  
set @x =''  
select CAST(@x.query('1.34e1') as nvarchar(50))  
```  
  
 <span data-ttu-id="f4473-152">이 예에서는 문자열 값 13.4를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="f4473-152">This returns the string value 13.4.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4473-153">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f4473-153">See Also</span></span>  
 <span data-ttu-id="f4473-154">[XQuery의 형식 캐스트 규칙](/sql/xquery/type-casting-rules-in-xquery) </span><span class="sxs-lookup"><span data-stu-id="f4473-154">[Type Casting Rules in XQuery](/sql/xquery/type-casting-rules-in-xquery) </span></span>  
 [<span data-ttu-id="f4473-155">CAST 및 CONVERT&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="f4473-155">CAST and CONVERT &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/cast-and-convert-transact-sql)  
  
  
