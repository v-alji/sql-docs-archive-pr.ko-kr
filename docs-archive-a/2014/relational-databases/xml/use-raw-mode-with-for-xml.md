---
title: FOR XML에서 RAW 모드 사용 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- FOR XML RAW mode
- XMLSCHEMA option
- FOR XML clause, RAW mode
- RAW FOR XML mode
- ELEMENTS directive
- RAW mode
- XMLDATA option
ms.assetid: 02c1bc0b-760c-4589-9ab1-6927c6d9c734
author: rothja
ms.author: jroth
ms.openlocfilehash: b2908a98336ec8a6e12029ad471f22a33d7a4dcf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738067"
---
# <a name="use-raw-mode-with-for-xml"></a><span data-ttu-id="44860-102">FOR XML에서 RAW 모드 사용</span><span class="sxs-lookup"><span data-stu-id="44860-102">Use RAW Mode with FOR XML</span></span>
  <span data-ttu-id="44860-103">RAW 모드는 쿼리 결과 집합의 각 행을 일반 식별자 \<row>가 있는 XML 요소 또는 선택적으로 제공된 요소 이름으로 변환합니다.</span><span class="sxs-lookup"><span data-stu-id="44860-103">RAW mode transforms each row in the query result set into an XML element that has the generic identifier \<row>, or the optionally provided element name.</span></span> <span data-ttu-id="44860-104">기본적으로 행 집합에서 NULL이 아닌 각 열 값은 \<row> 요소의 특성으로 매핑됩니다.</span><span class="sxs-lookup"><span data-stu-id="44860-104">By default, each column value in the rowset that is not NULL is mapped to an attribute of the \<row> element.</span></span> <span data-ttu-id="44860-105">ELEMENTS 지시어가 FOR XML 절에 추가된 경우 각 열 값은 \<row> 요소의 하위 요소로 매핑됩니다.</span><span class="sxs-lookup"><span data-stu-id="44860-105">If the ELEMENTS directive is added to the FOR XML clause, each column value is mapped to a subelement of the \<row> element.</span></span> <span data-ttu-id="44860-106">ELEMENTS 지시어와 함께 선택적으로 XSINIL 옵션을 지정하여 결과 집합의 NULL 열 값을 xsi:nil=`"`true`"`특성이 있는 요소로 매핑할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="44860-106">Together with the ELEMENTS directive, you can optionally specify the XSINIL option to map NULL column values in the result set to an element that has the attribute, xsi:nil=`"`true`"`.</span></span>  
  
 <span data-ttu-id="44860-107">결과 XML에 대한 스키마를 요청할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="44860-107">You can request a schema for the resulting XML.</span></span> <span data-ttu-id="44860-108">XMLDATA 옵션을 지정하면 인라인 XDR 스키마가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="44860-108">Specifying the XMLDATA option returns an in-line XDR schema.</span></span> <span data-ttu-id="44860-109">XMLSCHEMA 옵션을 지정하면 인라인 XSD 스키마가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="44860-109">Specifying the XMLSCHEMA option returns an in-line XSD schema.</span></span> <span data-ttu-id="44860-110">스키마는 데이터 시작 부분에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="44860-110">The schema appears at the start of the data.</span></span> <span data-ttu-id="44860-111">결국 모든 최상위 요소에 대해 스키마 네임스페이스 참조가 반복됩니다.</span><span class="sxs-lookup"><span data-stu-id="44860-111">In the result, the schema namespace reference is repeated for every top-level element.</span></span>  
  
 <span data-ttu-id="44860-112">이진 데이터를 base64 인코딩 형식으로 반환하기 위해 FOR XML 절에서 BINARY BASE64 옵션을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="44860-112">The BINARY BASE64 option must be specified in the FOR XML clause to return the binary data in base64-encoded format.</span></span> <span data-ttu-id="44860-113">RAW 모드에서 BINARY BASE64 옵션을 지정하지 않고 이진 데이터를 검색하면 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="44860-113">In RAW mode, retrieving binary data without specifying the BINARY BASE64 option will result in an error.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="44860-114">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="44860-114">In This Section</span></span>  
 <span data-ttu-id="44860-115">이 섹션에는 다음 예제가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="44860-115">This section contains the following examples:</span></span>  
  
-   [<span data-ttu-id="44860-116">예: 제품 모델 정보를 XML로 검색</span><span class="sxs-lookup"><span data-stu-id="44860-116">Example: Retrieving Product Model Information as XML</span></span>](example-retrieving-product-model-information-as-xml.md)  
  
-   [<span data-ttu-id="44860-117">예: ELEMENTS 지시어를 사용하여 XSINIL 지정</span><span class="sxs-lookup"><span data-stu-id="44860-117">Example: Specifying XSINIL with the ELEMENTS Directive</span></span>](example-specifying-xsinil-with-the-elements-directive.md)  
  
-   [<span data-ttu-id="44860-118">예제: XMLDATA 및 XMLSCHEMA 옵션을 사용하여 결과로 스키마 요청</span><span class="sxs-lookup"><span data-stu-id="44860-118">Example: Requesting Schemas as Results with the XMLDATA and XMLSCHEMA Options</span></span>](example-requesting-schemas-as-results-with-the-xmldata-and-xmlschema-options.md)  
  
-   [<span data-ttu-id="44860-119">예: 이진 데이터 검색</span><span class="sxs-lookup"><span data-stu-id="44860-119">Example: Retrieving Binary Data</span></span>](example-retrieving-binary-data.md)  
  
-   [<span data-ttu-id="44860-120">예: &#60;행&#62; 요소 이름 바꾸기</span><span class="sxs-lookup"><span data-stu-id="44860-120">Example: Renaming the &#60;row&#62; Element</span></span>](example-renaming-the-row-element.md)  
  
-   [<span data-ttu-id="44860-121">예: FOR XML로 생성된 XML에 대한 루트 요소 지정</span><span class="sxs-lookup"><span data-stu-id="44860-121">Example: Specifying a Root Element for the XML Generated by FOR XML</span></span>](example-specifying-a-root-element-for-the-xml-generated-by-for-xml.md)  
  
-   [<span data-ttu-id="44860-122">예: XMLType 열 쿼리</span><span class="sxs-lookup"><span data-stu-id="44860-122">Example: Querying XMLType Columns</span></span>](example-querying-xmltype-columns.md)  
  
## <a name="see-also"></a><span data-ttu-id="44860-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="44860-123">See Also</span></span>  
 <span data-ttu-id="44860-124">[WITH XMLNAMESPACES를 사용하여 쿼리에 네임스페이스 추가](add-namespaces-to-queries-with-with-xmlnamespaces.md) </span><span class="sxs-lookup"><span data-stu-id="44860-124">[Add Namespaces to Queries with WITH XMLNAMESPACES](add-namespaces-to-queries-with-with-xmlnamespaces.md) </span></span>  
 <span data-ttu-id="44860-125">[FOR XML에서 AUTO 모드 사용](use-auto-mode-with-for-xml.md) </span><span class="sxs-lookup"><span data-stu-id="44860-125">[Use AUTO Mode with FOR XML](use-auto-mode-with-for-xml.md) </span></span>  
 <span data-ttu-id="44860-126">[FOR XML에서 EXPLICIT 모드 사용](use-explicit-mode-with-for-xml.md) </span><span class="sxs-lookup"><span data-stu-id="44860-126">[Use EXPLICIT Mode with FOR XML](use-explicit-mode-with-for-xml.md) </span></span>  
 <span data-ttu-id="44860-127">[FOR XML에서 PATH 모드 사용](use-path-mode-with-for-xml.md) </span><span class="sxs-lookup"><span data-stu-id="44860-127">[Use PATH Mode with FOR XML](use-path-mode-with-for-xml.md) </span></span>  
 <span data-ttu-id="44860-128">[SELECT&#40;Transact-SQL&#41;](/sql/t-sql/queries/select-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="44860-128">[SELECT &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-transact-sql) </span></span>  
 [<span data-ttu-id="44860-129">FOR XML&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="44860-129">FOR XML &#40;SQL Server&#41;</span></span>](../xml/for-xml-sql-server.md)  
  
  
