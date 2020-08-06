---
title: UNIQUE PARTICLE ATTRIBUTION 제약 조건 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
f1_keywords:
- unique particle attribution
helpviewer_keywords:
- schema collections [SQL Server], unique particle attribution
- XML schema collections [SQL Server], unique particle attribution
- UPA constraint rule
- unique particle attribution constraint rule
ms.assetid: 6bb879e9-a5ee-402e-94e4-fe8cec5966b0
author: rothja
ms.author: jroth
ms.openlocfilehash: 7416aa4ea14539f3bf633207768783aa439ec818
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728099"
---
# <a name="unique-particle-attribution-constraint"></a><span data-ttu-id="ed43b-102">UNIQUE PARTICLE ATTRIBUTION 제약 조건</span><span class="sxs-lookup"><span data-stu-id="ed43b-102">Unique Particle Attribution Constraint</span></span>
  <span data-ttu-id="ed43b-103">XSD에서 복잡한 콘텐츠 모델은 UPA(Unique Particle Attribution) 제약 조건 규칙에 의해 제한됩니다.</span><span class="sxs-lookup"><span data-stu-id="ed43b-103">In XSD, complex content models are constrained by the unique particle attribution (UPA) constraint rule.</span></span> <span data-ttu-id="ed43b-104">이 규칙에서는 항목 문서의 각 요소가 해당 부모 콘텐츠 모델에 있는 정확히 하나의 `<xsd:element>` 또는 `<xsd:any>` 파티클과 분명하게 일치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ed43b-104">This rule requires that each element in an instance document correspond unambiguously to exactly one `<xsd:element>` or `<xsd:any>` particle in its parent's content model.</span></span> <span data-ttu-id="ed43b-105">잠재적으로 모호한 콘텐츠 모델이 있는 유형이 포함되는 스키마는 모두 거부됩니다.</span><span class="sxs-lookup"><span data-stu-id="ed43b-105">Any schema that contains a type with a potentially ambiguous content model is rejected.</span></span>  
  
 <span data-ttu-id="ed43b-106">모호성에 대한 가장 일반적인 원인은 minOccurs < maxOccurs와 같은 변수 발생 범위가 있는 `<xsd:any>` 와일드카드 문자 및 파티클입니다.</span><span class="sxs-lookup"><span data-stu-id="ed43b-106">The most common causes of ambiguity are `<xsd:any>` wildcard characters and particles that have variable occurrence ranges, such as minOccurs < maxOccurs.</span></span> <span data-ttu-id="ed43b-107">예를 들어 다음 콘텐츠 모델은 <`e1`> 요소가 `<xsd:element>` 또는 `<xsd:any>` 요소 중 하나와 일치할 수 있기 때문에 모호합니다.</span><span class="sxs-lookup"><span data-stu-id="ed43b-107">For example, the following content model is ambiguous, because an <`e1`> element could match either the `<xsd:element>` or the `<xsd:any>` element.</span></span>  
  
```  
<xsd:element name="root">  
    <xsd:complexType>  
        <xsd:choice>  
            <xsd:element name="e1"/>  
            <xsd:any namespace="##any"/>  
        </xsd:choice>  
    </xsd:complexType>  
</xsd:element>  
```  
  
 <span data-ttu-id="ed43b-108">다음 콘텐츠 모델도 모호합니다.</span><span class="sxs-lookup"><span data-stu-id="ed43b-108">The following content model is also ambiguous:</span></span>  
  
```  
<xsd:element name="root">  
    <xsd:complexType>  
        <xsd:sequence>  
            <xsd:element name="e1" maxOccurs="2"/>  
            <xsd:element name="e2" minOccurs="0"/>  
            <xsd:element name="e1"/>  
        </xsd:sequence>  
    </xsd:complexType>  
</xsd:element>  
```  
  
 <span data-ttu-id="ed43b-109">`<root><e1/><e2/><e1/></root>` 와 같은 문서는 분명하게 유효성을 검사할 수 있지만 `<root><e1/><e1/></root>` 와 같은 문서는 두 번째 `<xsd:element>` 에 해당하는 `<e1/>` 가 명확하지 않기 때문에 분명하게 유효성을 검사할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ed43b-109">Although a document such as `<root><e1/><e2/><e1/></root>` can be validated unambiguously, a document such as `<root><e1/><e1/></root>` cannot, because it is not clear to which `<xsd:element>` the second `<e1/>` corresponds.</span></span> <span data-ttu-id="ed43b-110">일부 문서는 분명하게 유효성을 검사할 수 있더라도 잠재적 모호성으로 인해 스키마가 거부됩니다.</span><span class="sxs-lookup"><span data-stu-id="ed43b-110">Even though some documents can be validated unambiguously, the schema will be rejected, because of the potential for ambiguity.</span></span>  
  
 <span data-ttu-id="ed43b-111">콘텐츠 모델이 유효하려면 자세한 검사 없이도 모든 항목의 유효성을 분명하게 검사할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ed43b-111">Note that for a content model to be valid, it must be possible to validate any instance unambiguously without looking ahead.</span></span> <span data-ttu-id="ed43b-112">예를 들어 다음과 같은 콘텐츠 모델에 유의하십시오.</span><span class="sxs-lookup"><span data-stu-id="ed43b-112">For example, consider the following content model:</span></span>  
  
```  
<xsd:element name="root">  
    <xsd:complexType>  
        <xsd:choice>  
           <xsd:sequence>  
               <xsd:element name="e1"/>  
               <xsd:element name="e2"/>  
           </xsd:sequence>  
           <xsd:sequence>  
               <xsd:element name="e1"/>  
               <xsd:element name="e3"/>  
           </xsd:sequence>  
       </xsd:choice>  
    </xsd:complexType>  
</xsd:element>  
```  
  
 <span data-ttu-id="ed43b-113">`<root><e1/><e3/></root>`와 같은 문서에서 `<e1/><e3/>` 시퀀스는 두 번째 `<xsd:sequence>`와 분명하게 일치합니다.</span><span class="sxs-lookup"><span data-stu-id="ed43b-113">For a document such as `<root><e1/><e3/></root>`, the sequence `<e1/><e3/>` unambiguously matches the second `<xsd:sequence>`.</span></span> <span data-ttu-id="ed43b-114">하지만 `<xsd:element>` 을 검사하지 않고서는 `<e1/>` 에 해당하는 `<e3/>`를 확인할 수 없기 때문에 이 콘텐츠 모델은 UPA 제약 조건 규칙에 위배됩니다.</span><span class="sxs-lookup"><span data-stu-id="ed43b-114">However, because the `<xsd:element>` to which `<e1/>` corresponds cannot be determined without looking ahead to `<e3/>`, the content model violates the UPA constraint rule.</span></span>  
  
## <a name="finding-more-information"></a><span data-ttu-id="ed43b-115">추가 정보 찾기</span><span class="sxs-lookup"><span data-stu-id="ed43b-115">Finding More Information</span></span>  
 <span data-ttu-id="ed43b-116">다음 문서는 W3C(World Wide Web Consortium)에서 발행했으며 UNIQUE PARTICLE ATTRIBUTION 제약 조건에 대한 기술적인 설명이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ed43b-116">The following document is published by the World Wide Web Consortium (W3C) and contains the technical description of the unique particle attribution constraint:</span></span>  
  
 <span data-ttu-id="ed43b-117">“XML 스키마 1부: 구조 제2판, W3C 제안 수정 권장 사항”:</span><span class="sxs-lookup"><span data-stu-id="ed43b-117">"XML Schema Part 1: Structures Second Edition, W3C Proposed Edited Recommendation":</span></span>  
  
-   <span data-ttu-id="ed43b-118">섹션 3.8.6: 모델 그룹 스키마 구성 요소의 제한 사항</span><span class="sxs-lookup"><span data-stu-id="ed43b-118">Section 3.8.6: Constraints on Model Group Schema Components</span></span>  
  
-   <span data-ttu-id="ed43b-119">부록 H: Unique Particle Attribution 제약 조건 분석(비표준)</span><span class="sxs-lookup"><span data-stu-id="ed43b-119">Appendix H: Analysis of the Unique Particle Attribution Constraint (non-normative)</span></span>  
  
 <span data-ttu-id="ed43b-120">이 문서를 보려면 [http://www.w3.org/TR/xmlschema-1](https://go.microsoft.com/fwlink/?linkid=48881)을 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="ed43b-120">To see the document, visit [http://www.w3.org/TR/xmlschema-1](https://go.microsoft.com/fwlink/?linkid=48881).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed43b-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ed43b-121">See Also</span></span>  
 [<span data-ttu-id="ed43b-122">XML 스키마 컬렉션&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="ed43b-122">XML Schema Collections &#40;SQL Server&#41;</span></span>](xml-schema-collections-sql-server.md)  
  
  
