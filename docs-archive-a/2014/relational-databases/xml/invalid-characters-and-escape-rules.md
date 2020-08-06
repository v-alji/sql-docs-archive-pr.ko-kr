---
title: 잘못된 문자 및 이스케이프 규칙 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- FOR XML clause, invalid characters
- FOR XML clause, escape rules
ms.assetid: f2e9b997-f400-4963-b225-59d46c6b93e8
author: rothja
ms.author: jroth
ms.openlocfilehash: 8624a31dea4e97e05da6d86c3c0c518b9c4d0aba
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741660"
---
# <a name="invalid-characters-and-escape-rules"></a><span data-ttu-id="312a4-102">잘못된 문자 및 이스케이프 규칙</span><span class="sxs-lookup"><span data-stu-id="312a4-102">Invalid Characters and Escape Rules</span></span>
  <span data-ttu-id="312a4-103">이 항목에서는 FOR XML 절에서 잘못된 XML 문자를 처리하는 방법에 대해 설명하고 XML 이름의 잘못된 문자에 대한 이스케이프 규칙을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="312a4-103">This topic describes how invalid XML characters are handled by the FOR XML clause, and lists the escape rules for characters that are invalid in XML names.</span></span>  
  
## <a name="for-xml-and-invalid-characters"></a><span data-ttu-id="312a4-104">XML 및 잘못된 문자의 경우</span><span class="sxs-lookup"><span data-stu-id="312a4-104">For XML and Invalid Characters</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="312a4-105">에서는 TYPE 지시어를 사용하지 않는 FOR XML 쿼리 내에서 잘못된 XML 문자가 반환되는 경우 해당 문자를 엔터티화합니다.</span><span class="sxs-lookup"><span data-stu-id="312a4-105">entitizes invalid XML characters when they are returned within FOR XML queries that do not use the TYPE directive.</span></span>  
  
 <span data-ttu-id="312a4-106">이러한 문자는 엔터티화되었는지 여부에 관계없이 XML 1.0 호환 파서에서 구문 분석 오류를 발생시키지만 엔터티화된 형식은 XML 1.1에 보다 적합합니다.</span><span class="sxs-lookup"><span data-stu-id="312a4-106">Although XML 1.0 conformant parsers raise parse errors regardless of whether these characters are entitized or not, the entitized form is better aligned with XML 1.1.</span></span> <span data-ttu-id="312a4-107">엔터티화된 형식은 이후 버전의 XML 표준에도 적합할 가능성이 높습니다.</span><span class="sxs-lookup"><span data-stu-id="312a4-107">The entitized form is also potentially better aligned with future versions of the XML standard.</span></span> <span data-ttu-id="312a4-108">또한 잘못된 문자의 코드 지점이 가시적으로 표시되기 때문에 보다 쉽게 디버깅을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="312a4-108">Additionally, it makes debugging simpler, because the code point of the invalid character becomes visible.</span></span>  
  
 <span data-ttu-id="312a4-109">XML 도구 사용자의 경우에는 데이터 스트림에 잘못된 문자가 있으면 어떤 방식으로든 XML 파서가 실패하기 때문에 해결 방법이 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="312a4-109">For users of XML tools, no workaround is required, because the XML parser will fail either way at the point where the invalid characters occur in the data stream.</span></span> <span data-ttu-id="312a4-110">비-XML 도구를 사용하는 경우 이러한 변경 내용을 적용하려면 엔터티화된 값으로 이러한 문자를 검색할 수 있도록 프로그래밍 논리를 업데이트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="312a4-110">If you use non-XML tools, this change can require you to update your programming logic to search for these characters as entitized values.</span></span>  
  
 <span data-ttu-id="312a4-111">다음 공백 문자는 왕복 중에 해당 문자를 보존할 수 있도록 FOR XML 쿼리에서 다르게 엔터티화됩니다.</span><span class="sxs-lookup"><span data-stu-id="312a4-111">The following white space characters are entitized differently in FOR XML queries to preserve their presence through round-tripping:</span></span>  
  
-   <span data-ttu-id="312a4-112">요소 내용 및 특성의 경우: **hex(0D)** (캐리지 리턴)</span><span class="sxs-lookup"><span data-stu-id="312a4-112">In element content and attributes: **hex(0D)** (carriage return)</span></span>  
  
-   <span data-ttu-id="312a4-113">특성 내용의 경우: **hex(09)** (탭), **hex(0A)** (줄 바꿈)</span><span class="sxs-lookup"><span data-stu-id="312a4-113">In attribute content: **hex(09)** (tab), **hex(0A)** (line feed)</span></span>  
  
 <span data-ttu-id="312a4-114">이러한 문자는 출력에 유지되며 파서에서 문자를 정규화하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="312a4-114">These characters are preserved in output, and a parser will not normalize them.</span></span>  
  
## <a name="escape-rules"></a><span data-ttu-id="312a4-115">이스케이프 규칙</span><span class="sxs-lookup"><span data-stu-id="312a4-115">Escape Rules</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="312a4-116">이름은 유효하지 않은 문자가 이스케이프 숫자 엔터티 인코딩으로 변환되는 방식으로 XML 이름으로 변환됩니다.</span><span class="sxs-lookup"><span data-stu-id="312a4-116">names that contain characters that are invalid in XML names, such as spaces, are translated into XML names in a way in which the invalid characters are translated into escaped numeric entity encoding.</span></span>  
  
 <span data-ttu-id="312a4-117">XML 이름에 사용할 수 있는 알파벳이 아닌 문자는 콜론(:)과 밑줄(_)뿐입니다.</span><span class="sxs-lookup"><span data-stu-id="312a4-117">There are only two non-alphabetic characters that can occur within an XML name: the colon (:) and the underscore (_).</span></span> <span data-ttu-id="312a4-118">콜론은 네임스페이스용으로 이미 예약된 문자이므로 이스케이프 문자로는 밑줄이 선택되었습니다.</span><span class="sxs-lookup"><span data-stu-id="312a4-118">Because the colon is already reserved for namespaces, the underscore is chosen as the escape character.</span></span> <span data-ttu-id="312a4-119">다음은 인코딩에 사용되는 이스케이프 규칙입니다.</span><span class="sxs-lookup"><span data-stu-id="312a4-119">Following are the escape rules that are used for encoding:</span></span>  
  
-   <span data-ttu-id="312a4-120">XML 1.0 사양에 따라 유효한 XML 이름 문자가 아닌 모든 UCS-2 문자는 _xHHHH\_로 이스케이프됩니다.</span><span class="sxs-lookup"><span data-stu-id="312a4-120">Any UCS-2 character that is not a valid XML name character, according to the XML 1.0 specification, is escaped as _xHHHH\_.</span></span> <span data-ttu-id="312a4-121">HHHH는 해당 문자에 대한 최상위 비트 우선 순서의 4자리 16진수 UCS-2 코드를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="312a4-121">The HHHH stands for the four-digit hexadecimal UCS-2 code for the character in the most significant bit-first order.</span></span> <span data-ttu-id="312a4-122">예를 들어 테이블 이름 **Order Details** 는 Order_x0020_Details로 인코딩됩니다.</span><span class="sxs-lookup"><span data-stu-id="312a4-122">For example, the table name **Order Details** is encoded as Order_x0020_Details.</span></span>  
  
-   <span data-ttu-id="312a4-123">UCS-2 영역(U+0010FFFF에 U+00010000 범위의 USC-4 추가)은 _xHHHHHHHH\_로 인코딩됩니다.</span><span class="sxs-lookup"><span data-stu-id="312a4-123">Characters that do not fit into the UCS-2 realm (the UCS-4 additions of the range U+00010000 to U+0010FFFF) are encoded as _xHHHHHHHH\_.</span></span> <span data-ttu-id="312a4-124">HHHHHHHH는 SQL Server 2000 이전 버전과의 호환성 모드인 경우 해당 문자에 대한 8자리 16진수 UCS-4 인코딩을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="312a4-124">The HHHHHHHH stands for the eight-digit hexadecimal UCS-4 encoding of the character, if under SQL Server 2000 backward compatibility mode.</span></span> <span data-ttu-id="312a4-125">그렇지 않으면 ISO 표준에 맞도록 문자가 _xHHHHHH\_로 인코딩됩니다.</span><span class="sxs-lookup"><span data-stu-id="312a4-125">Otherwise, the characters are encoded as_xHHHHHH\_, in order to align with the ISO standard.</span></span>  
  
-   <span data-ttu-id="312a4-126">문자 x가 뒤에 이어지지 않는 경우에는 밑줄 문자를 이스케이프 처리하지 않아도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="312a4-126">The underscore character does not have to be escaped unless it is followed by the character x.</span></span> <span data-ttu-id="312a4-127">예를 들어 테이블 이름 **Order_Details** 는 인코딩되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="312a4-127">For example, the table name **Order_Details** is not encoded.</span></span>  
  
-   <span data-ttu-id="312a4-128">식별자에서 콜론은 이스케이프 처리되지 않으므로 네임스페이스 요소와 특성 이름이 FOR XML 쿼리에 의해 생성될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="312a4-128">The colon in identifiers is not escaped As a result, the namespace element and attribute names can be generated by the FOR XML query.</span></span> <span data-ttu-id="312a4-129">예를 들어 다음 쿼리는 이름에 콜론이 있는 네임스페이스 특성을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="312a4-129">For example, the following query generates a namespace attribute that has a colon in the name:</span></span>  
  
    ```  
    SELECT 'namespace-urn' as 'xmlns:namespace',   
     1 as 'namespace:a'   
    FOR XML RAW  
    ```  
  
     <span data-ttu-id="312a4-130">쿼리 결과는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="312a4-130">The query produces this result:</span></span>  
  
    ```  
    <row xmlns:namespace="namespace-urn" namespace:a="1"/>  
    ```  
  
     <span data-ttu-id="312a4-131">XML 네임스페이스를 추가할 때는 WITH XMLNAMESPACES를 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="312a4-131">Note that WITH XMLNAMESPACES is the recommended way to add XML namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="312a4-132">참고 항목</span><span class="sxs-lookup"><span data-stu-id="312a4-132">See Also</span></span>  
 [<span data-ttu-id="312a4-133">FOR XML&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="312a4-133">FOR XML &#40;SQL Server&#41;</span></span>](for-xml-sql-server.md)  
  
  
