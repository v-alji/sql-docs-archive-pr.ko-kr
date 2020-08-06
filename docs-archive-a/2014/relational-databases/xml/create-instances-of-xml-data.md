---
title: XML 데이터 인스턴스 만들기 | Microsoft 문서
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- type casting string instances [XML in SQL Server]
- XML [SQL Server], typed
- xml data type [SQL Server], generating instances
- casting string instances [XML in SQL Server]
- typed XML
- generating XML instances [SQL Server]
- XML [SQL Server], generating instances
- white space [XML in SQL Server]
ms.assetid: dbd6c06f-db6e-44a7-855a-6a55bf374907
author: rothja
ms.author: jroth
ms.openlocfilehash: c857b9ebbe559de34fdac925642f9270d9cbf936
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743115"
---
# <a name="create-instances-of-xml-data"></a><span data-ttu-id="859b9-102">XML 데이터 인스턴스 만들기</span><span class="sxs-lookup"><span data-stu-id="859b9-102">Create Instances of XML Data</span></span>
  <span data-ttu-id="859b9-103">이 항목에서는 XML 인스턴스를 생성하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="859b9-103">This topic describes how to generate XML instances.</span></span>  
  
 <span data-ttu-id="859b9-104">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 다음과 같은 방법으로 XML 인스턴스를 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="859b9-104">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], you can generate XML instances in the following ways:</span></span>  
  
-   <span data-ttu-id="859b9-105">문자열 인스턴스의 형식 캐스팅</span><span class="sxs-lookup"><span data-stu-id="859b9-105">Type casting string instances.</span></span>  
  
-   <span data-ttu-id="859b9-106">SELECT 문에 FOR XML 절 사용</span><span class="sxs-lookup"><span data-stu-id="859b9-106">Using the SELECT statement with the FOR XML clause.</span></span>  
  
-   <span data-ttu-id="859b9-107">상수 할당 사용</span><span class="sxs-lookup"><span data-stu-id="859b9-107">Using constant assignments.</span></span>  
  
-   <span data-ttu-id="859b9-108">대량 로드 사용</span><span class="sxs-lookup"><span data-stu-id="859b9-108">Using bulk load.</span></span>  
  
## <a name="type-casting-string-and-binary-instances"></a><span data-ttu-id="859b9-109">문자열 및 이진 인스턴스의 형식 캐스팅</span><span class="sxs-lookup"><span data-stu-id="859b9-109">Type Casting String and Binary Instances</span></span>  
 <span data-ttu-id="859b9-110">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]**var**문자열을 **image\*\*\*\*n\*\*\*\*char** **varbinary**데이터 형식으로 캐스팅 (CAST) 또는 변환 (CONVERT) 하 여 [n] [var] char, **[n] text**, varbinary 및 image와 같은 문자열 데이터 형식을 `xml` 데이터 형식으로 구문 분석할 수 있습니다 `xml` .</span><span class="sxs-lookup"><span data-stu-id="859b9-110">You can parse any of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] string data types, such as [**n**][**var**]**char**, **[n]text**, **varbinary**,and **image**, into the `xml` data type by casting (CAST) or converting (CONVERT) the string to the `xml` data type.</span></span> <span data-ttu-id="859b9-111">형식화되지 않은 XML의 형식이 올바른지 확인하기 위해 검사합니다.</span><span class="sxs-lookup"><span data-stu-id="859b9-111">Untyped XML is checked to confirm that it is well formed.</span></span> <span data-ttu-id="859b9-112">형식과 연결 된 스키마가 있는 경우 `xml` 유효성 검사도 수행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="859b9-112">If there is a schema associated with the `xml` type, validation is also performed.</span></span> <span data-ttu-id="859b9-113">자세한 내용은 [형식화된 XML과 형식화되지 않은 XML 비교](compare-typed-xml-to-untyped-xml.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="859b9-113">For more information, see [Compare Typed XML to Untyped XML](compare-typed-xml-to-untyped-xml.md).</span></span>  
  
 <span data-ttu-id="859b9-114">XML 문서는 UTF-8, UTF-16, windows-1252 등과 같은 다른 인코딩 방식으로 인코딩할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="859b9-114">XML documents can be encoded with different encodings (for example, UTF-8, UTF-16, windows-1252).</span></span> <span data-ttu-id="859b9-115">다음은 문자열 및 이진 원본 유형이 XML 문서 인코딩과 상호 작용하는 방법 및 파서의 동작 방식에 대한 규칙을 대략적으로 설명한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="859b9-115">The following outlines the rules on how the string and binary source types interact with the XML document encoding and how the parser behaves.</span></span>  
  
 <span data-ttu-id="859b9-116">**nvarchar** 에서는 UTF-16 또는 UCS-2와 같은 2바이트 유니코드 인코딩을 가정하므로 XML 파서는 문자열 값을 2바이트 유니코드로 인코딩된 XML 문서 또는 조각으로 취급합니다.</span><span class="sxs-lookup"><span data-stu-id="859b9-116">Since **nvarchar** assumes a two-byte unicode encoding such as UTF-16 or UCS-2, the XML parser will treat the string value as a two-byte Unicode encoded XML document or fragment.</span></span> <span data-ttu-id="859b9-117">즉, XML 문서는 원본 데이터 형식과 호환되어야 할 뿐 아니라 2바이트 유니코드 인코딩으로 인코딩해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="859b9-117">This means that the XML document needs to be encoded in a two-byte Unicode encoding as well to be compatible with the source data type.</span></span> <span data-ttu-id="859b9-118">UTF-16으로 인코딩된 XML 문서는 UTF-16 BOM(바이트 순서 표시)을 포함할 수 있지만 원본 유형의 컨텍스트에 2바이트 유니코드로 인코딩된 문서만 될 수 있다고 명시되어 있으므로 이 BOM을 반드시 포함할 필요는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="859b9-118">A UTF-16 encoded XML document can have a UTF-16 byte order mark (BOM), but it does not need to, since the context of the source type makes it clear that it can only be a two-byte Unicode encoded document.</span></span>  
  
 <span data-ttu-id="859b9-119">**varchar** 문자열의 내용은 XML 파서에 의해 1바이트로 인코딩된 XML 문서/조각으로 취급됩니다.</span><span class="sxs-lookup"><span data-stu-id="859b9-119">The content of a **varchar** string is treated as a one-byte encoded XML document/fragment by the XML parser.</span></span> <span data-ttu-id="859b9-120">**varchar** 원본 문자열에는 연관된 코드 페이지가 있으므로 파서는 XML 자체에 명시적 인코딩이 지정되지 않은 경우 인코딩에 대해 해당 코드 페이지를 사용하고, XML 인스턴스에 BOM 또는 인코딩 선언이 있는 경우 BOM 또는 선언이 코드 페이지와 일치해야 합니다. 그렇지 않은 경우 파서는 오류를 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="859b9-120">Since the **varchar** source string has a code page associated, the parser will use that code page for the encoding if no explicit encoding is specified in the XML itself If an XML instance has a BOM or an encoding declaration, the BOM or declaration needs to be consistent with the code page, otherwise the parser will report an error.</span></span>  
  
 <span data-ttu-id="859b9-121">**varbinary** 의 내용은 XML 파서로 직접 전달되는 코드 포인트 스트림으로 취급됩니다.</span><span class="sxs-lookup"><span data-stu-id="859b9-121">The content of **varbinary** is treated as a codepoint stream that is passed directly to the XML parser.</span></span> <span data-ttu-id="859b9-122">따라서 XML 문서 또는 조각은 BOM 또는 기타 인코딩 정보를 인라인으로 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="859b9-122">Thus, the XML document or fragment needs to provide the BOM or other encoding information inline.</span></span> <span data-ttu-id="859b9-123">파서는 이 스트림을 통해서만 인코딩을 파악합니다.</span><span class="sxs-lookup"><span data-stu-id="859b9-123">The parser will only look at the stream to determine the encoding.</span></span> <span data-ttu-id="859b9-124">즉, UTF-16으로 인코딩된 XML은 UTF-16 BOM을 제공해야 하고 BOM 및 선언 인코딩이 없는 인스턴스는 UTF-8로 해석됩니다.</span><span class="sxs-lookup"><span data-stu-id="859b9-124">This means that UTF-16 encoded XML needs to provide the UTF-16 BOM and an instance without BOM and without a declaration encoding will be interpreted as UTF-8.</span></span>  
  
 <span data-ttu-id="859b9-125">XML 문서의 인코딩을 미리 알지 못하고 데이터를 XML로 캐스팅하기 전에 데이터가 XML 데이터 대신 문자열이나 이진 데이터로 전달된 경우 해당 데이터를 **varbinary**로 취급하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="859b9-125">If the encoding of the XML document is not known in advance and the data is passed as string or binary data instead of XML data before casting to XML, it is recommended to treat the data as **varbinary**.</span></span> <span data-ttu-id="859b9-126">예를 들어 OpenRowset()을 사용하여 XML 파일에서 데이터를 읽을 때 다음과 같이 해당 데이터가 **varbinary(max)** 값으로 읽히도록 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="859b9-126">For example, when reading data from an XML file using OpenRowset(), one should specify the data to be read as a **varbinary(max)** value:</span></span>  
  
```  
select CAST(x as XML)   
from OpenRowset(BULK 'filename.xml', SINGLE_BLOB) R(x)  
```  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="859b9-127">에서는 내부적으로 UTF-16 인코딩을 사용하는 효율적인 이진 표현으로 XML을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="859b9-127">internally represents XML in an efficient binary representation that uses UTF-16 encoding.</span></span> <span data-ttu-id="859b9-128">사용자가 제공한 인코딩은 유지되지 않지만 구문 분석 프로세스 중에 고려됩니다.</span><span class="sxs-lookup"><span data-stu-id="859b9-128">User-provided encoding is not preserved, but is considered during the parse process.</span></span>  
  
### <a name="type-casting-clr-user-defined-types"></a><span data-ttu-id="859b9-129">CLR 사용자 정의 형식 캐스팅</span><span class="sxs-lookup"><span data-stu-id="859b9-129">Type Casting CLR user-defined types</span></span>  
 <span data-ttu-id="859b9-130">CLR 사용자 정의 형식에 XML 직렬화가 지정되면 명시적으로 해당 형식의 인스턴스를 XML 데이터 형식으로 캐스팅할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="859b9-130">If a CLR user-defined type has an XML Serialization, instances of that type can be explicitly cast to an XML datatype.</span></span> <span data-ttu-id="859b9-131">CLR 사용자 정의 형식의 XML 직렬화에 대한 자세한 내용은 [CLR 데이터베이스 개체에서 XML 직렬화](../../database-engine/dev-guide/xml-serialization-from-clr-database-objects.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="859b9-131">For more details about the XML serialization of a CLR user-defined typed, see [XML Serialization from CLR Database Objects](../../database-engine/dev-guide/xml-serialization-from-clr-database-objects.md).</span></span>  
  
### <a name="white-space-handling-in-typed-xml"></a><span data-ttu-id="859b9-132">형식화된 XML에서 공백 처리</span><span class="sxs-lookup"><span data-stu-id="859b9-132">White Space Handling in Typed XML</span></span>  
 <span data-ttu-id="859b9-133">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 요소 내용 내에 있는 공백은 시작 또는 끝 태그처럼 마크업으로 구분된 공백 전용 문자 데이터 시퀀스 내에 있을 경우와 엔터티화되지 않은 경우 불필요한 것으로 간주됩니다.</span><span class="sxs-lookup"><span data-stu-id="859b9-133">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], white space inside element content is considered insignificant if it occurs inside a sequence of white-space-only character data delimited by markup, such as begin or end tags, and is not entitized.</span></span> <span data-ttu-id="859b9-134">CDATA 섹션은 무시됩니다. 이러한 공백을 처리하는 방식은 W3C(World Wide Web Consortium)에서 게시한 XML 1.0 사양에 설명된 방법과 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="859b9-134">(CDATA sections are ignored.) This handling of white space handling is different from how white space is described in the XML 1.0 specification published by the World Wide Web Consortium (W3C).</span></span> <span data-ttu-id="859b9-135">그 이유는 XML 1.0에 설명된 대로 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 의 XML 파서가 제한된 개수의 DTD 하위 집합만 인식하기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="859b9-135">This is because the XML parser in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] recognizes only a limited number of DTD subsets, as defined in XML 1.0.</span></span> <span data-ttu-id="859b9-136">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 지원하는 제한된 DTD 하위 집합에 대한 자세한 내용은 [CAST 및 CONVERT&#40;Transact-SQL&#41;](/sql/t-sql/functions/cast-and-convert-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="859b9-136">For more information about the limited DTD subsets supported in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], see [CAST and CONVERT &#40;Transact-SQL&#41;](/sql/t-sql/functions/cast-and-convert-transact-sql).</span></span>  
  
 <span data-ttu-id="859b9-137">기본적으로 XML 파서는 문자열 데이터를 XML로 변환할 때 다음 중 하나에 해당하면 불필요한 공백을 무시합니다.</span><span class="sxs-lookup"><span data-stu-id="859b9-137">By default, the XML parser discards insignificant white space when it converts string data to XML if either of the following is true:</span></span>  
  
-   <span data-ttu-id="859b9-138">`The xml:space` 특성이 한 요소 또는 한 요소의 상위 항목 요소에 정의되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="859b9-138">`The xml:space` attribute is not defined on an element or its ancestor elements.</span></span>  
  
-   <span data-ttu-id="859b9-139">한 요소 또는 한 요소의 상위 항목 요소 중 하나에 적용된 `xml:space` 특성에 기본값이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="859b9-139">The `xml:space` attribute in effect on an element, or one of its ancestor elements, has the value of default.</span></span>  
  
 <span data-ttu-id="859b9-140">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="859b9-140">For example:</span></span>  
  
```  
declare @x xml  
set @x = '<root>      <child/>     </root>'  
select @x   
```  
  
 <span data-ttu-id="859b9-141">다음은 결과입니다.</span><span class="sxs-lookup"><span data-stu-id="859b9-141">This is the result:</span></span>  
  
```  
<root><child/></root>  
```  
  
 <span data-ttu-id="859b9-142">그러나 이 동작을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="859b9-142">However, you can change this behavior.</span></span> <span data-ttu-id="859b9-143">xml DT 인스턴스에 대한 공백을 유지하려면 CONVERT 연산자 및 값 1로 설정된 해당 옵션 *style* 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="859b9-143">To preserve white space for an xml DT instance, use the CONVERT operator and its optional *style* parameter set to a value of 1.</span></span> <span data-ttu-id="859b9-144">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="859b9-144">For example:</span></span>  
  
```  
SELECT CONVERT(xml, N'<root>      <child/>     </root>', 1)  
```  
  
 <span data-ttu-id="859b9-145">*style* 매개 변수가 사용되지 않거나 해당 값이 0으로 설정된 경우 xml DT 인스턴스의 변환에 대해 불필요한 공백이 유지되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="859b9-145">If the *style* parameter is either not used or its value is set to 0, insignificant white space is not preserved for the conversion of the xml DT instance.</span></span> <span data-ttu-id="859b9-146">문자열 데이터를 xml DT 인스턴스로 변환할 때 CONVERT 연산자 및 해당 *style* 매개 변수를 사용하는 방법은 [CAST 및 CONVERT&#40;Transact-SQL&#41;](/sql/t-sql/functions/cast-and-convert-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="859b9-146">For more information about how to use the CONVERT operator and its *style* parameter when converting string data to xml DT instances, see [CAST and CONVERT &#40;Transact-SQL&#41;](/sql/t-sql/functions/cast-and-convert-transact-sql).</span></span>  
  
### <a name="example-cast-a-string-value-to-typed-xml-and-assign-it-to-a-column"></a><span data-ttu-id="859b9-147">예제: 문자열 값을 형식화된 xml로 캐스팅하여 열에 할당</span><span class="sxs-lookup"><span data-stu-id="859b9-147">Example: Cast a string value to typed xml and assign it to a column</span></span>  
 <span data-ttu-id="859b9-148">다음 예에서는 XML 조각이 포함 된 문자열 변수를 데이터 형식으로 캐스팅 한 `xml` 다음 type 열에 저장 합니다 `xml` .</span><span class="sxs-lookup"><span data-stu-id="859b9-148">The following example casts a string variable that contains an XML fragment to the `xml` data type and then stores it in the `xml` type column:</span></span>  
  
```  
CREATE TABLE T(c1 int primary key, c2 xml)  
go  
DECLARE  @s varchar(100)  
SET @s = '<Cust><Fname>Andrew</Fname><Lname>Fuller</Lname></Cust>'   
```  
  
 <span data-ttu-id="859b9-149">다음 삽입 작업은 문자열에서 형식으로 암시적으로 변환 합니다 `xml` .</span><span class="sxs-lookup"><span data-stu-id="859b9-149">The following insert operation implicitly converts from a string to the `xml` type:</span></span>  
  
```  
INSERT INTO T VALUES (3, @s)   
```  
  
 <span data-ttu-id="859b9-150">문자열을 형식으로 명시적으로 캐스팅할 수 있습니다 `xml` .</span><span class="sxs-lookup"><span data-stu-id="859b9-150">You can explicitly cast() the string to the `xml` type:</span></span>  
  
```  
INSERT INTO T VALUES (3, cast (@s as xml))  
```  
  
 <span data-ttu-id="859b9-151">또는 다음과 같이 convert()를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="859b9-151">Or you can use convert(), as shown in the following:</span></span>  
  
```  
INSERT INTO T VALUES (3, convert (xml, @s))   
```  
  
### <a name="example-convert-a-string-to-typed-xml-and-assign-it-to-a-variable"></a><span data-ttu-id="859b9-152">예제: 문자열을 형식화된 xml로 변환하여 변수에 할당</span><span class="sxs-lookup"><span data-stu-id="859b9-152">Example: Convert a string to typed xml and assign it to a variable</span></span>  
 <span data-ttu-id="859b9-153">다음 예에서는 문자열이 형식으로 변환 되 `xml` 고 데이터 형식의 변수에 할당 됩니다 `xml` .</span><span class="sxs-lookup"><span data-stu-id="859b9-153">In the following example, a string is converted to `xml` type and assigned to a variable of the `xml` data type:</span></span>  
  
```  
declare @x xml  
declare  @s varchar(100)  
SET @s = '<Cust><Fname>Andrew</Fname><Lname>Fuller</Lname></Cust>'   
set @x =convert (xml, @s)  
select @x  
```  
  
## <a name="using-the-select-statement-with-a-for-xml-clause"></a><span data-ttu-id="859b9-154">SELECT 문에 FOR XML 절 사용</span><span class="sxs-lookup"><span data-stu-id="859b9-154">Using the SELECT Statement with a FOR XML Clause</span></span>  
 <span data-ttu-id="859b9-155">SELECT 문에 FOR XML 절을 사용하여 결과를 XML로 반환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="859b9-155">You can use the FOR XML clause in a SELECT statement to return results as XML.</span></span> <span data-ttu-id="859b9-156">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="859b9-156">For example:</span></span>  
  
```  
DECLARE @xmlDoc xml  
SET @xmlDoc = (SELECT Column1, Column2  
               FROM   Table1, Table2  
               WHERE   Some condition  
               FOR XML AUTO)  
 ...  
```  
  
 <span data-ttu-id="859b9-157">SELECT 문은 데이터 형식 변수에 할당 하는 동안 구문 분석 되는 텍스트 XML 조각을 반환 합니다 `xml` .</span><span class="sxs-lookup"><span data-stu-id="859b9-157">The SELECT statement returns a textual XML fragment that is then parsed during the assignment to the `xml` data type variable.</span></span>  
  
 <span data-ttu-id="859b9-158">For xml 절에 FOR XML 쿼리 결과를 형식으로 직접 반환 하는 [type 지시어](type-directive-in-for-xml-queries.md) 를 사용할 수도 있습니다 `xml` .</span><span class="sxs-lookup"><span data-stu-id="859b9-158">You can also use the [TYPE directive](type-directive-in-for-xml-queries.md) in the FOR XML clause that directly returns a FOR XML query result as `xml` type:</span></span>  
  
```  
Declare @xmlDoc xml  
SET @xmlDoc = (SELECT ProductModelID, Name  
               FROM   Production.ProductModel  
               WHERE  ProductModelID=19  
               FOR XML AUTO, TYPE)  
SELECT @xmlDoc  
```  
  
 <span data-ttu-id="859b9-159">다음은 결과입니다.</span><span class="sxs-lookup"><span data-stu-id="859b9-159">This is the result:</span></span>  
  
```  
<Production.ProductModel ProductModelID="19" Name="Mountain-100" />...  
```  
  
 <span data-ttu-id="859b9-160">다음 예에서는 `xml` FOR XML 쿼리의 형식화 된 결과가 유형 열에 삽입 됩니다 `xml` .</span><span class="sxs-lookup"><span data-stu-id="859b9-160">In the following example, the typed `xml` result of a FOR XML query is inserted into an `xml` type column:</span></span>  
  
```  
CREATE TABLE T1 (c1 int, c2 xml)  
go  
INSERT T1(c1, c2)  
SELECT 1, (SELECT ProductModelID, Name  
           FROM Production.ProductModel  
           WHERE ProductModelID=19  
           FOR XML AUTO, TYPE)  
SELECT * FROM T1  
go  
```  
  
 <span data-ttu-id="859b9-161">FOR XML에 대한 자세한 내용은 [FOR XML&#40;SQL Server&#41;](for-xml-sql-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="859b9-161">For more information about FOR XML, see [FOR XML &#40;SQL Server&#41;](for-xml-sql-server.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="859b9-162">는 TYPE 지시어를 사용하는 FOR XML 쿼리와 같은 여러 서버 생성 결과로 클라이언트에 `xml` 데이터 형식 인스턴스를 반환합니다. 또는 `xml` 데이터 형식을 사용하여 SQL 열, 변수 및 출력 매개 변수로부터 XML을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="859b9-162">returns `xml` data type instances to the client as a result of different server constructs such as FOR XML queries that use the TYPE directive, or where the `xml` data type is used to return XML from SQL columns, variables, and output parameters.</span></span> <span data-ttu-id="859b9-163">클라이언트 애플리케이션 코드에서 ADO.NET 공급자는 이 `xml` 데이터 형식 정보가 서버로부터 이진 인코딩으로 전송되도록 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="859b9-163">In client application code, the ADO.NET provider requests that this `xml` data type information be sent in a binary encoding from the server.</span></span> <span data-ttu-id="859b9-164">하지만 TYPE 지시어 없이 FOR XML을 사용하는 경우 XML 데이터는 문자열 형식으로 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="859b9-164">However, if you are using FOR XML without the TYPE directive, the XML data returns as a string type.</span></span> <span data-ttu-id="859b9-165">클라이언트 공급자는 항상 두 XML 유형 중 하나를 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="859b9-165">In any case, the client provider will always be able to handle either form of XML.</span></span>  
  
## <a name="using-constant-assignments"></a><span data-ttu-id="859b9-166">상수 할당 사용</span><span class="sxs-lookup"><span data-stu-id="859b9-166">Using Constant Assignments</span></span>  
 <span data-ttu-id="859b9-167">문자열 상수는 데이터 형식의 인스턴스가 예상 되는 위치에 사용할 수 있습니다 `xml` .</span><span class="sxs-lookup"><span data-stu-id="859b9-167">A string constant can be used where an instance of the `xml` data type is expected.</span></span> <span data-ttu-id="859b9-168">이것은 문자열을 XML로 암시적 캐스팅하는 것과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="859b9-168">This is the same as an implied CAST of string to XML.</span></span> <span data-ttu-id="859b9-169">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="859b9-169">For example:</span></span>  
  
```  
DECLARE @xmlDoc xml  
SET @xmlDoc = '<Cust><Fname>Andrew</Fname><Lname>Fuller</Lname></Cust>'   
-- Or  
SET @xmlDoc = N'<?xml version="1.0" encoding="ucs-2"?><doc/>'  
```  
  
 <span data-ttu-id="859b9-170">이전 예제에서는 암시적으로 문자열을 데이터 형식으로 변환 하 `xml` 고이를 `xml` 형식 변수에 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="859b9-170">The previous example implicitly converts the string to the `xml` data type and assigns it to an `xml` type variable.</span></span>  
  
 <span data-ttu-id="859b9-171">다음 예에서는 상수 문자열을 형식 열에 삽입 합니다 `xml` .</span><span class="sxs-lookup"><span data-stu-id="859b9-171">The following example inserts a constant string into an `xml` type column:</span></span>  
  
```  
CREATE TABLE T(c1 int primary key, c2 xml)  
INSERT INTO T VALUES (3, '<Cust><Fname>Andrew</Fname><Lname>Fuller</Lname></Cust>')   
```  
  
> [!NOTE]  
>  <span data-ttu-id="859b9-172">형식화된 XML의 경우 지정된 스키마에 대해 XML의 유효성이 검사됩니다.</span><span class="sxs-lookup"><span data-stu-id="859b9-172">For typed XML, the XML is validated against the specified schema.</span></span> <span data-ttu-id="859b9-173">자세한 내용은 [형식화된 XML과 형식화되지 않은 XML 비교](compare-typed-xml-to-untyped-xml.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="859b9-173">For more information, see [Compare Typed XML to Untyped XML](compare-typed-xml-to-untyped-xml.md).</span></span>  
  
## <a name="using-bulk-load"></a><span data-ttu-id="859b9-174">대량 로드 사용</span><span class="sxs-lookup"><span data-stu-id="859b9-174">Using Bulk Load</span></span>  
 <span data-ttu-id="859b9-175">향상된 [OPENROWSET(Transact-SQL)](/sql/t-sql/functions/openrowset-transact-sql) 기능을 사용하면 데이터베이스의 XML 문서를 대량 로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="859b9-175">The enhanced [OPENROWSET (Transact-SQL)](/sql/t-sql/functions/openrowset-transact-sql) functionality allows you to bulk load XML documents in the database.</span></span> <span data-ttu-id="859b9-176">XML 인스턴스를 파일에서 `xml` 데이터베이스의 유형 열로 대량 로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="859b9-176">You can bulk load XML instances from files into the `xml` type columns in the database.</span></span> <span data-ttu-id="859b9-177">작업 샘플은 [XML 문서 대량 가져오기 및 내보내기 예제&#40;SQL Server&#41;](../import-export/examples-of-bulk-import-and-export-of-xml-documents-sql-server.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="859b9-177">For working samples, see [Examples of Bulk Import and Export of XML Documents &#40;SQL Server&#41;](../import-export/examples-of-bulk-import-and-export-of-xml-documents-sql-server.md).</span></span> <span data-ttu-id="859b9-178">XML 문서 로드에 대한 자세한 내용은 [XML 데이터 로드](load-xml-data.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="859b9-178">For more information about loading XML documents, see [Load XML Data](load-xml-data.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="859b9-179">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="859b9-179">In This Section</span></span>  
  
|<span data-ttu-id="859b9-180">항목</span><span class="sxs-lookup"><span data-stu-id="859b9-180">Topic</span></span>|<span data-ttu-id="859b9-181">Description</span><span class="sxs-lookup"><span data-stu-id="859b9-181">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="859b9-182">XML 데이터 검색 및 쿼리</span><span class="sxs-lookup"><span data-stu-id="859b9-182">Retrieve and Query XML Data</span></span>](retrieve-and-query-xml-data.md)|<span data-ttu-id="859b9-183">XML 인스턴스가 데이터베이스에 저장될 때 보존되지 않는 인스턴스의 일부분에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="859b9-183">Describes the parts of XML instances that are not preserved when they are stored in databases.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="859b9-184">참고 항목</span><span class="sxs-lookup"><span data-stu-id="859b9-184">See Also</span></span>  
 <span data-ttu-id="859b9-185">[형식화된 XML과 형식화되지 않은 XML 비교](compare-typed-xml-to-untyped-xml.md) </span><span class="sxs-lookup"><span data-stu-id="859b9-185">[Compare Typed XML to Untyped XML](compare-typed-xml-to-untyped-xml.md) </span></span>  
 <span data-ttu-id="859b9-186">[xml 데이터 형식 메서드](/sql/t-sql/xml/xml-data-type-methods) </span><span class="sxs-lookup"><span data-stu-id="859b9-186">[xml Data Type Methods](/sql/t-sql/xml/xml-data-type-methods) </span></span>  
 <span data-ttu-id="859b9-187">[XML DML&#40;XML 데이터 수정 언어&#41;](/sql/t-sql/xml/xml-data-modification-language-xml-dml) </span><span class="sxs-lookup"><span data-stu-id="859b9-187">[XML Data Modification Language &#40;XML DML&#41;](/sql/t-sql/xml/xml-data-modification-language-xml-dml) </span></span>  
 [<span data-ttu-id="859b9-188">XML 데이터&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="859b9-188">XML Data &#40;SQL Server&#41;</span></span>](xml-data-sql-server.md)  
  
  
