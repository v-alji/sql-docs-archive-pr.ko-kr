---
title: 기타 주석 (SQLXML 4.0) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- url-encode annotation
- sql:key-fields
- use-cdata annotation
- sql:is-mapping-schema
- sql:url-encode
- sql:id-prefix
- sql:use-cdata
- key-fields annotation
- id-prefix annotation [SQLXML]
- is-mapping-schema annotation
ms.assetid: f7b4d37b-d6d3-4ac3-b2fd-a0b534a924e4
author: rothja
ms.author: jroth
ms.openlocfilehash: b654568c93df0a0c3e08cf6eaa615b7026a9c18a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650884"
---
# <a name="other-annotations-sqlxml-40"></a><span data-ttu-id="96225-102">기타 주석(SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="96225-102">Other Annotations (SQLXML 4.0)</span></span>
  <span data-ttu-id="96225-103">XML 대량 로드는 이 섹션의 이전 항목에서 설명한 주석 외에 다음과 같은 기타 주석도 해석합니다.</span><span class="sxs-lookup"><span data-stu-id="96225-103">In addition to the annotations discussed in the previous topics in this section, XML Bulk Load interprets these other annotations, as follows:</span></span>  
  
 `sql:id-prefix`  
 <span data-ttu-id="96225-104">스키마에서 접두사를 XML 데이터로 지정한 경우 XML 대량 로드는 Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]에 데이터를 보내기 전에 접두사를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="96225-104">If the schema specifies prefixes to the XML data, XML Bulk Load removes the prefixes before sending the data to Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
 `sql:use-cdata`  
 <span data-ttu-id="96225-105">XML 대량 로드는 CDATA 섹션에 저장된 텍스트를 읽어 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="96225-105">XML Bulk Load reads the text that is stored in the CDATA sections and sends it to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
 `sql:url-encode`  
 <span data-ttu-id="96225-106">XML 대량 로드는 이 주석을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="96225-106">XML Bulk Load does not support this annotation.</span></span> <span data-ttu-id="96225-107">예를 들어 XML 데이터 입력에 URL을 지정하면 XML 대량 로드는 데이터베이스의 해당 데이터 저장 위치에서 데이터를 읽지 못합니다.</span><span class="sxs-lookup"><span data-stu-id="96225-107">For example, you cannot specify a URL in the XML data input and expect XML Bulk Load to read data from that location to store it in the database.</span></span>  
  
 `sql:is-mapping-schema`  
 <span data-ttu-id="96225-108">XML 대량 로드는 이 주석이나 `sql:id`를 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="96225-108">XML Bulk Load does not support this annotation, nor does it support `sql:id`.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="96225-109">XML 대량 로드는 인라인 매핑 스키마를 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="96225-109">XML Bulk Load does not support inline mapping schemas.</span></span>  
  
 `sql:key-fields`  
 <span data-ttu-id="96225-110">XML 대량 로드는 이 주석을 항상 무시합니다.</span><span class="sxs-lookup"><span data-stu-id="96225-110">XML Bulk Load always ignores this annotation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96225-111">참고 항목</span><span class="sxs-lookup"><span data-stu-id="96225-111">See Also</span></span>  
 [<span data-ttu-id="96225-112">SQLXML 4.0 &#40;주석 해석&#41;</span><span class="sxs-lookup"><span data-stu-id="96225-112">Annotation Interpretation &#40;SQLXML 4.0&#41;</span></span>](annotation-interpretation-sqlxml-4-0.md)  
  
  
