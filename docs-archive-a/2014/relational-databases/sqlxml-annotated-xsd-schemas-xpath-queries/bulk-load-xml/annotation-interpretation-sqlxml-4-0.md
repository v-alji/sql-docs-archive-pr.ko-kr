---
title: 주석 해석 (SQLXML 4.0) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- annotated XSD schemas, XML Bulk Load
- XML Bulk Load [SQLXML], annotation intepretations
- annotations [SQLXML]
- bulk load [SQLXML], annotation interpretations
- annotated XDR schemas, XML Bulk Load
ms.assetid: 1c46bdb6-2812-4a13-b60b-7101c04b299f
author: rothja
ms.author: jroth
ms.openlocfilehash: c31d56f7dd577b4b5a5b582eb0e3b1db312109a8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652751"
---
# <a name="annotation-interpretation-sqlxml-40"></a><span data-ttu-id="27169-102">주석 해석(SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="27169-102">Annotation Interpretation (SQLXML 4.0)</span></span>
  <span data-ttu-id="27169-103">이 섹션의 항목에서는 XML 대량 로드가 XSD 스키마의 주석을 해석하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="27169-103">The topics in this section describe how XML Bulk Load interprets annotations in the XSD schema.</span></span> <span data-ttu-id="27169-104">여기서 설명하는 동작은 XDR 스키마의 주석에도 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="27169-104">The behavior described here also applies to the annotations in the XDR schema.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="27169-105">이 항목의 내용은 XML 대량 로드에서 처리 시 사용하는 주석에 대해서만 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="27169-105">The information in these topics describes only the annotations used by XML Bulk Load in its processing.</span></span> <span data-ttu-id="27169-106">SQLXML 4.0에서 지원 되는 XSD 스키마에 대 한 전체 주석 목록은 [Xsd 스키마에서 주석 사용 &#40;sqlxml 4.0&#41;](../../sqlxml-annotated-xsd-schemas-using/using-annotations-in-xsd-schemas-sqlxml-4-0.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="27169-106">For a complete list of annotations for the XSD schema that are supported by SQLXML 4.0, see [Using Annotations in XSD Schemas &#40;SQLXML 4.0&#41;](../../sqlxml-annotated-xsd-schemas-using/using-annotations-in-xsd-schemas-sqlxml-4-0.md).</span></span> <span data-ttu-id="27169-107">XDR 스키마에 대해 지원 되는 주석 목록은 [SQLXML 4.0&#41;에서 사용 되지 &#40;주석이 추가 된 Xdr 스키마 ](../../sqlxml/annotated-xsd-schemas/annotated-xdr-schemas-deprecated-in-sqlxml-4-0.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="27169-107">For a list of supported annotations for XDR schemas, see [Annotated XDR Schemas &#40;Deprecated in SQLXML 4.0&#41;](../../sqlxml/annotated-xsd-schemas/annotated-xdr-schemas-deprecated-in-sqlxml-4-0.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="27169-108">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="27169-108">In This Section</span></span>  
 [<span data-ttu-id="27169-109">sql: relationship 및 키 순서 지정 규칙 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="27169-109">sql:relationship and the Key Ordering Rule &#40;SQLXML 4.0&#41;</span></span>](annotation-interpretation-sql-relationship-and-key-ordering-rule.md)  
 <span data-ttu-id="27169-110">XML 대량 로드에서 `sql:relationship` 주석이 해석되는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="27169-110">Describes how the `sql:relationship` annotation is interpreted in XML Bulk Load.</span></span>  
  
 [<span data-ttu-id="27169-111">sql: 매핑된 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="27169-111">sql:mapped &#40;SQLXML 4.0&#41;</span></span>](annotation-interpretation-sql-mapped.md)  
 <span data-ttu-id="27169-112">XML 대량 로드에서 `sql:mapped` 주석이 해석되는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="27169-112">Describes how the `sql:mapped` annotation is interpreted in XML Bulk Load.</span></span>  
  
 [<span data-ttu-id="27169-113">sql: limit 필드 및 sql: limit 값 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="27169-113">sql:limit-field and sql:limit-value &#40;SQLXML 4.0&#41;</span></span>](annotation-interpretation-sql-limit-field-and-sql-limit-value.md)  
 <span data-ttu-id="27169-114">XML 대량 로드에서 `sql:limit-field` 및 `sql:limit-value` 주석이 해석되는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="27169-114">Describes how the `sql:limit-field` and `sql:limit-value` annotations are interpreted in XML Bulk Load.</span></span>  
  
 [<span data-ttu-id="27169-115">sql: 오버플로 필드 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="27169-115">sql:overflow-field &#40;SQLXML 4.0&#41;</span></span>](annotation-interpretation-sql-overflow-field.md)  
 <span data-ttu-id="27169-116">XML 대량 로드에서 `sql:overflow` 주석이 해석되는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="27169-116">Describes how the `sql:overflow` annotation is interpreted in XML Bulk Load.</span></span>  
  
 [<span data-ttu-id="27169-117">SQLXML 4.0 &#40;다른 주석&#41;</span><span class="sxs-lookup"><span data-stu-id="27169-117">Other Annotations &#40;SQLXML 4.0&#41;</span></span>](annotation-interpretation-other-annotations.md)  
 <span data-ttu-id="27169-118">XML 대량 로드에서 다음 주석을 해석 하는 방법에 대해 설명 합니다. `sql:id-prefix` ,, `sql:use-cdata` `sql:url-encode` , `sql:is-mapping-schema` , `sql:key-fields` .</span><span class="sxs-lookup"><span data-stu-id="27169-118">Describes how the following annotations are interpreted in XML Bulk Load: `sql:id-prefix`, `sql:use-cdata`, `sql:url-encode`, `sql:is-mapping-schema`, `sql:key-fields`.</span></span>  
  
  
