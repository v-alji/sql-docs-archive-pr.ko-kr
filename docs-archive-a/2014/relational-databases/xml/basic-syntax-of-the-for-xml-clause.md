---
title: FOR XML 절의 기본 구문 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- BINARY BASE64 directive
- ROOT directive
- FOR XML clause, BINARY BASE64 directive
- FOR XML clause, syntax
- FOR XML clause, ROOT directive
ms.assetid: df19ecbf-d28e-4e9c-aaa3-700f8bbd3be4
author: rothja
ms.author: jroth
ms.openlocfilehash: dc0410e7a54674673f64442d8a3cf9476d250033
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646244"
---
# <a name="basic-syntax-of-the-for-xml-clause"></a><span data-ttu-id="c1b2e-102">FOR XML 절의 기본 구문</span><span class="sxs-lookup"><span data-stu-id="c1b2e-102">Basic Syntax of the FOR XML Clause</span></span>
  <span data-ttu-id="c1b2e-103">FOR XML 모드는 RAW, AUTO, EXPLICIT 또는 PATH일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c1b2e-103">The FOR XML mode can be RAW, AUTO, EXPLICIT, or PATH.</span></span> <span data-ttu-id="c1b2e-104">이 모드는 결과 XML의 셰이프를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="c1b2e-104">It determines the shape of the resulting XML.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="c1b2e-105">XMLDATA 지시어에 FOR XML 옵션은 더 이상 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c1b2e-105">The XMLDATA directive to the FOR XML option is deprecated.</span></span> <span data-ttu-id="c1b2e-106">RAW 및 AUTO 모드의 경우 XSD 생성을 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="c1b2e-106">Use XSD generation in the case of RAW and AUTO modes.</span></span> <span data-ttu-id="c1b2e-107">EXPLICT 모드의 XMLDATA 지시어의 경우에는 대체할 옵션이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c1b2e-107">There is no replacement for the XMLDATA directive in EXPLICT mode.</span></span> [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
 <span data-ttu-id="c1b2e-108">다음은 [FOR 절 (transact-sql)](/sql/t-sql/queries/select-for-clause-transact-sql)에 설명 된 기본 구문입니다.</span><span class="sxs-lookup"><span data-stu-id="c1b2e-108">Following is the basic syntax that is described in [FOR Clause (Transact-SQL)](/sql/t-sql/queries/select-for-clause-transact-sql):</span></span>  
  
```  
[ FOR { BROWSE | <XML> } ]  
<XML> ::=  
XML   
    {   
      { RAW [ ('ElementName') ] | AUTO }   
        [   
           <CommonDirectives>   
           [ , { XMLDATA | XMLSCHEMA [ ('TargetNameSpaceURI') ]} ]   
           [ , ELEMENTS [ XSINIL | ABSENT ]   
        ]  
      | EXPLICIT   
        [   
           <CommonDirectives>   
           [ , XMLDATA ]   
        ]  
      | PATH [ ('ElementName') ]   
        [   
           <CommonDirectives>   
           [ , ELEMENTS [ XSINIL | ABSENT ] ]  
        ]  
     }   
  
 <CommonDirectives> ::=   
   [ , BINARY BASE64 ]  
   [ , TYPE ]  
   [ , ROOT [ ('RootName') ] ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="c1b2e-109">인수</span><span class="sxs-lookup"><span data-stu-id="c1b2e-109">Arguments</span></span>  
 <span data-ttu-id="c1b2e-110">RAW[('*ElementName*')]</span><span class="sxs-lookup"><span data-stu-id="c1b2e-110">RAW[('*ElementName*')]</span></span>  
 <span data-ttu-id="c1b2e-111">쿼리 결과를 사용하여 결과 집합의 각 행을 요소 태그로 일반 식별자 \<row />를 갖는 XML 요소로 변환합니다.</span><span class="sxs-lookup"><span data-stu-id="c1b2e-111">Takes the query result and transforms each row in the result set into an XML element that has a generic identifier, \<row />, as the element tag.</span></span> <span data-ttu-id="c1b2e-112">이 지시어를 사용하는 경우 필요에 따라 행 요소에 대한 이름을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c1b2e-112">You can optionally specify a name for the row element when you use this directive.</span></span> <span data-ttu-id="c1b2e-113">결과 XML은 각 행에 대해 행 요소가 생성될 때 지정된 *ElementName* 을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="c1b2e-113">The resulting XML will use the specified *ElementName* as the row element generated for each row.</span></span> <span data-ttu-id="c1b2e-114">자세한 내용은 [FOR XML에서 RAW 모드 사용](use-raw-mode-with-for-xml.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c1b2e-114">For more information, see [Use RAW Mode with FOR XML](use-raw-mode-with-for-xml.md).</span></span>  
  
 <span data-ttu-id="c1b2e-115">AUTO</span><span class="sxs-lookup"><span data-stu-id="c1b2e-115">AUTO</span></span>  
 <span data-ttu-id="c1b2e-116">단순하게 중첩된 XML 트리로 쿼리 결과를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="c1b2e-116">Returns query results in a simple, nested XML tree.</span></span> <span data-ttu-id="c1b2e-117">최소한 한 개의 열이 SELECT 절에 나열되는 FROM 절의 각 테이블은 XML 요소로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c1b2e-117">Each table in the FROM clause for which at least one column is listed in the SELECT clause is represented as an XML element.</span></span> <span data-ttu-id="c1b2e-118">SELECT 절에 나열되는 열은 해당 요소의 특성에 매핑됩니다.</span><span class="sxs-lookup"><span data-stu-id="c1b2e-118">The columns listed in the SELECT clause are mapped to the appropriate element attributes.</span></span> <span data-ttu-id="c1b2e-119">자세한 내용은 [FOR XML에서 AUTO 모드 사용](use-auto-mode-with-for-xml.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c1b2e-119">For more information, see [Use AUTO Mode with FOR XML](use-auto-mode-with-for-xml.md).</span></span>  
  
 <span data-ttu-id="c1b2e-120">EXPLICIT</span><span class="sxs-lookup"><span data-stu-id="c1b2e-120">EXPLICIT</span></span>  
 <span data-ttu-id="c1b2e-121">결과 XML 트리 셰이프가 명시적으로 정의되도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c1b2e-121">Specifies that the shape of the resulting XML tree is defined explicitly.</span></span> <span data-ttu-id="c1b2e-122">쿼리는 이 모드를 사용하여 원하는 중첩에 대한 추가 정보가 명시적으로 지정되도록 특정 방식으로 작성되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c1b2e-122">By using this mode, queries must be written in a particular way so additional information about the nesting you want is specified explicitly.</span></span> <span data-ttu-id="c1b2e-123">자세한 내용은 [FOR XML에서 EXPLICIT 모드 사용](use-explicit-mode-with-for-xml.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c1b2e-123">For more information, see [Use EXPLICIT Mode with FOR XML](use-explicit-mode-with-for-xml.md).</span></span>  
  
 <span data-ttu-id="c1b2e-124">PATH</span><span class="sxs-lookup"><span data-stu-id="c1b2e-124">PATH</span></span>  
 <span data-ttu-id="c1b2e-125">요소와 특성을 혼합하고 추가 중첩을 사용하여 복잡한 속성을 나타내는 보다 간단한 방법을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="c1b2e-125">Provides a simpler way to mix elements and attributes, and to introduce additional nesting for representing complex properties.</span></span> <span data-ttu-id="c1b2e-126">FOR XML EXPLICIT 모드 쿼리를 사용하여 행 집합에서 이러한 종류의 XML을 구성할 수 있지만 PATH 모드는 복잡할 수도 있는 EXPLICIT 모드 쿼리 대신 훨씬 간단한 방법을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="c1b2e-126">You can use FOR XML EXPLICIT mode queries to construct this kind of XML from a rowset, but the PATH mode provides a simpler alternative to the possibly cumbersome EXPLICIT mode queries.</span></span> <span data-ttu-id="c1b2e-127">**XML** 유형 인스턴스를 반환하는 중첩 FOR XML 쿼리 및 TYPE 지시어 작성 기능과 함께 PATH 모드를 사용하면 보다 간편하게 쿼리를 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c1b2e-127">PATH mode, together with the ability to write nested FOR XML queries and the TYPE directive to return **xml** type instances, allows you to write queries with less complexity.</span></span> <span data-ttu-id="c1b2e-128">이 모드는 대부분의 EXPLICIT 모드 쿼리 작성을 대신할 방법을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="c1b2e-128">It provides an alternative to writing most EXPLICIT mode queries.</span></span> <span data-ttu-id="c1b2e-129">기본적으로 PATH 모드는 결과 집합의 각 행에 대한 \<row> 요소 래퍼를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="c1b2e-129">By default, PATH mode generates a \<row> element wrapper for each row in the result set.</span></span> <span data-ttu-id="c1b2e-130">필요에 따라 요소 이름을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c1b2e-130">You can optionally specify an element name.</span></span> <span data-ttu-id="c1b2e-131">요소 이름을 지정한 경우 지정된 이름이 래퍼 요소 이름으로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="c1b2e-131">If you do, the specified name is used as the wrapper element name.</span></span> <span data-ttu-id="c1b2e-132">빈 문자열(FOR XML PATH (''))을 제공하면 래퍼 요소가 생성되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c1b2e-132">If you provide an empty string (FOR XML PATH ('')), no wrapper element is generated.</span></span> <span data-ttu-id="c1b2e-133">자세한 내용은 [FOR XML에서 PATH 모드 사용](use-path-mode-with-for-xml.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c1b2e-133">For more information, see [Use PATH Mode with FOR XML](use-path-mode-with-for-xml.md).</span></span>  
  
 <span data-ttu-id="c1b2e-134">XMLDATA</span><span class="sxs-lookup"><span data-stu-id="c1b2e-134">XMLDATA</span></span>  
 <span data-ttu-id="c1b2e-135">인라인 XDR(XML-Data Reduced) 스키마가 반환되어야 함을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c1b2e-135">Specifies that an inline XML-Data Reduced (XDR) schema should be returned.</span></span> <span data-ttu-id="c1b2e-136">스키마는 인라인 스키마로 문서 앞에 놓이게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c1b2e-136">The schema is prepended to the document as an inline schema.</span></span> <span data-ttu-id="c1b2e-137">작업 샘플은 [FOR XML에서 RAW 모드 사용](use-raw-mode-with-for-xml.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c1b2e-137">For a working sample, see [Use RAW Mode with FOR XML](use-raw-mode-with-for-xml.md).</span></span>  
  
 <span data-ttu-id="c1b2e-138">XMLSCHEMA</span><span class="sxs-lookup"><span data-stu-id="c1b2e-138">XMLSCHEMA</span></span>  
 <span data-ttu-id="c1b2e-139">인라인 W3C XML 스키마(XSD)를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="c1b2e-139">Returns an inline W3C XML Schema (XSD).</span></span> <span data-ttu-id="c1b2e-140">이 지시어를 지정할 때 필요에 따라 대상 네임스페이스 URI를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c1b2e-140">You can optionally specify a target namespace URI when specifying this directive.</span></span> <span data-ttu-id="c1b2e-141">이렇게 하면 스키마에 지정된 네임스페이스를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="c1b2e-141">This returns the specified namespace in the schema.</span></span> <span data-ttu-id="c1b2e-142">자세한 내용은 [인라인 XSD 스키마 생성](generate-an-inline-xsd-schema.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c1b2e-142">For more information, see [Generate an Inline XSD Schema](generate-an-inline-xsd-schema.md).</span></span> <span data-ttu-id="c1b2e-143">작업 샘플은 [FOR XML에서 RAW 모드 사용](use-raw-mode-with-for-xml.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c1b2e-143">For a working sample, see [Use RAW Mode with FOR XML](use-raw-mode-with-for-xml.md).</span></span>  
  
 <span data-ttu-id="c1b2e-144">ELEMENTS</span><span class="sxs-lookup"><span data-stu-id="c1b2e-144">ELEMENTS</span></span>  
 <span data-ttu-id="c1b2e-145">ELEMENTS 옵션이 지정되면 열이 하위 요소로 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="c1b2e-145">If the ELEMENTS option is specified, the columns are returned as subelements.</span></span> <span data-ttu-id="c1b2e-146">그렇지 않은 경우에는 XML 특성에 매핑됩니다.</span><span class="sxs-lookup"><span data-stu-id="c1b2e-146">Otherwise, they are mapped to XML attributes.</span></span> <span data-ttu-id="c1b2e-147">이 옵션은 RAW, AUTO 및 PATH 모드에서만 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="c1b2e-147">This option is supported in RAW, AUTO, and PATH modes only.</span></span> <span data-ttu-id="c1b2e-148">이 지시어를 사용하는 경우 필요에 따라 XSINIL 또는 ABSENT를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c1b2e-148">You can optionally specify XSINIL or ABSENT when you use this directive.</span></span> <span data-ttu-id="c1b2e-149">XSINIL은 True로 설정된 **xsi:nil** 특성이 있는 요소가 NULL 열 값에 대해 생성되도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c1b2e-149">XSINIL specifies that an element that has an **xsi:nil** attribute set to True be created for NULL column values.</span></span> <span data-ttu-id="c1b2e-150">기본적으로 또는 ABSENT가 ELEMENTS와 함께 지정된 경우 요소가 NULL 값에 대해 생성되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c1b2e-150">By default or when ABSENT is specified together with ELEMENTS, no elements are created for NULL values.</span></span> <span data-ttu-id="c1b2e-151">작업 샘플은 [FOR XML에서 RAW 모드 사용](use-raw-mode-with-for-xml.md) 및 [FOR XML에서 AUTO 모드 사용](use-auto-mode-with-for-xml.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c1b2e-151">For a working sample, see [Use RAW Mode with FOR XML](use-raw-mode-with-for-xml.md) and [Use AUTO Mode with FOR XML](use-auto-mode-with-for-xml.md).</span></span>  
  
 <span data-ttu-id="c1b2e-152">BINARY BASE64</span><span class="sxs-lookup"><span data-stu-id="c1b2e-152">BINARY BASE64</span></span>  
 <span data-ttu-id="c1b2e-153">BINARY Base64 옵션이 지정되면 쿼리에서 반환되는 이진 데이터가 모두 base64 인코딩 형식으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c1b2e-153">If the BINARY Base64 option is specified, any binary data returned by the query is represented in base64-encoded format.</span></span> <span data-ttu-id="c1b2e-154">RAW와 EXPLICIT 모드를 사용하여 이진 데이터를 검색하려면 이 옵션을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c1b2e-154">To retrieve binary data by using RAW and EXPLICIT mode, this option must be specified.</span></span> <span data-ttu-id="c1b2e-155">AUTO 모드에서 이진 데이터는 기본적으로 참조로 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="c1b2e-155">In AUTO mode, binary data is returned as a reference by default.</span></span> <span data-ttu-id="c1b2e-156">작업 샘플은 [FOR XML에서 RAW 모드 사용](use-raw-mode-with-for-xml.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c1b2e-156">For a working sample, see [Use RAW Mode with FOR XML](use-raw-mode-with-for-xml.md).</span></span>  
  
 <span data-ttu-id="c1b2e-157">TYPE</span><span class="sxs-lookup"><span data-stu-id="c1b2e-157">TYPE</span></span>  
 <span data-ttu-id="c1b2e-158">쿼리가 결과를 **xml** 형식으로 반환하도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c1b2e-158">Specifies that the query returns the results as the **xml** type.</span></span> <span data-ttu-id="c1b2e-159">자세한 내용은 [TYPE Directive in FOR XML Queries](type-directive-in-for-xml-queries.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c1b2e-159">For more information, see [TYPE Directive in FOR XML Queries](type-directive-in-for-xml-queries.md).</span></span>  
  
 <span data-ttu-id="c1b2e-160">ROOT [('*RootName*')]</span><span class="sxs-lookup"><span data-stu-id="c1b2e-160">ROOT [('*RootName*')]</span></span>  
 <span data-ttu-id="c1b2e-161">단일 최상위 요소가 결과 XML에 추가되도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c1b2e-161">Specifies that a single, top-level element be added to the resulting XML.</span></span> <span data-ttu-id="c1b2e-162">필요에 따라 생성할 루트 요소 이름을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c1b2e-162">You can optionally specify the root element name to generate.</span></span> <span data-ttu-id="c1b2e-163">기본값은 "root"입니다.</span><span class="sxs-lookup"><span data-stu-id="c1b2e-163">The default value is "root".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1b2e-164">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c1b2e-164">See Also</span></span>  
 <span data-ttu-id="c1b2e-165">[FOR XML에서 RAW 모드 사용](use-raw-mode-with-for-xml.md) </span><span class="sxs-lookup"><span data-stu-id="c1b2e-165">[Use RAW Mode with FOR XML](use-raw-mode-with-for-xml.md) </span></span>  
 <span data-ttu-id="c1b2e-166">[FOR XML에서 AUTO 모드 사용](use-auto-mode-with-for-xml.md) </span><span class="sxs-lookup"><span data-stu-id="c1b2e-166">[Use AUTO Mode with FOR XML](use-auto-mode-with-for-xml.md) </span></span>  
 <span data-ttu-id="c1b2e-167">[FOR XML에서 EXPLICIT 모드 사용](use-explicit-mode-with-for-xml.md) </span><span class="sxs-lookup"><span data-stu-id="c1b2e-167">[Use EXPLICIT Mode with FOR XML](use-explicit-mode-with-for-xml.md) </span></span>  
 <span data-ttu-id="c1b2e-168">[FOR XML에서 PATH 모드 사용](use-path-mode-with-for-xml.md) </span><span class="sxs-lookup"><span data-stu-id="c1b2e-168">[Use PATH Mode with FOR XML](use-path-mode-with-for-xml.md) </span></span>  
 <span data-ttu-id="c1b2e-169">[SELECT&#40;Transact-SQL&#41;](/sql/t-sql/queries/select-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c1b2e-169">[SELECT &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-transact-sql) </span></span>  
 [<span data-ttu-id="c1b2e-170">FOR XML&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="c1b2e-170">FOR XML &#40;SQL Server&#41;</span></span>](for-xml-sql-server.md)  
  
  
