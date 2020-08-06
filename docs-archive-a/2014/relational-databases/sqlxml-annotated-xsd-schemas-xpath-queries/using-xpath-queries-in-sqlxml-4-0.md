---
title: SQLXML 4.0에서 XPath 쿼리 사용 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- XPath queries [SQLXML]
- annotated XSD schemas, XPath queries
- queries [SQLXML], XPath
- XML views [SQLXML]
ms.assetid: 7814d099-81ec-4fb8-894a-729cdbb5015a
author: rothja
ms.author: jroth
ms.openlocfilehash: 80d82513b22d2a50aedb37955a210dd33746db86
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652731"
---
# <a name="using-xpath-queries-in-sqlxml-40"></a><span data-ttu-id="d7312-102">SQLXML 4.0의 XPath 쿼리 사용</span><span class="sxs-lookup"><span data-stu-id="d7312-102">Using XPath Queries in SQLXML 4.0</span></span>
  <span data-ttu-id="d7312-103">Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 지원하는 주석이 추가된 XSD 스키마를 사용하면 데이터베이스에 저장된 관계형 데이터의 XML 뷰를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d7312-103">Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] support for annotated XSD schemas allows you to create XML views of the relational data stored in the database.</span></span> <span data-ttu-id="d7312-104">XPath 언어의 하위 집합을 사용하면 주석이 추가된 XSD 스키마로 만든 XML 뷰에 대해 쿼리를 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d7312-104">You can use a subset of the XPath language to query the XML views created by an annotated XSD schema.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d7312-105">SQLXML 4.0의 XPath 쿼리를 이해하려면 템플릿 및 매핑 스키마와 같은 관련 개념과 XML 뷰에 대해 잘 알고 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d7312-105">To understand XPath queries in SQLXML 4.0, you must be familiar with XML views and related concepts such as templates and mapping schema.</span></span> <span data-ttu-id="d7312-106">자세한 내용은 주석이 추가 된 [XSD 스키마 소개 &#40;SQLXML 4.0&#41;](../sqlxml/annotated-xsd-schemas/introduction-to-annotated-xsd-schemas-sqlxml-4-0.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="d7312-106">For more information, see [Introduction to Annotated XSD Schemas &#40;SQLXML 4.0&#41;](../sqlxml/annotated-xsd-schemas/introduction-to-annotated-xsd-schemas-sqlxml-4-0.md).</span></span> <span data-ttu-id="d7312-107">XPath에 대 한 자세한 내용은에서 W3C (World Wide Web 컨소시엄)로 정의 된 XPath 표준을 참조 하세요 http://www.w3.org/TR/xpath .</span><span class="sxs-lookup"><span data-stu-id="d7312-107">For more information about XPath, see the XPath standard defined by the World Wide Web Consortium (W3C) at http://www.w3.org/TR/xpath.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d7312-108">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="d7312-108">In This Section</span></span>  
 [<span data-ttu-id="d7312-109">&#40;하는 XPath 쿼리 사용에 대 한 소개 SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="d7312-109">Introduction to Using XPath Queries &#40;SQLXML 4.0&#41;</span></span>](introduction-to-using-xpath-queries-sqlxml-4-0.md)  
 <span data-ttu-id="d7312-110">W3C XPath 사양에서 지원되는 기능과 그렇지 않은 기능 등 SQLXML 4.0의 XPath 쿼리에 대한 개요를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="d7312-110">Provides introductory information about XPath queries in SQLXML 4.0, including supported and unsupported functionality from the W3C XPath specification.</span></span>  
  
 [<span data-ttu-id="d7312-111">&#40;SQLXML 4.0&#41;위치 경로를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="d7312-111">Specifying a Location Path &#40;SQLXML 4.0&#41;</span></span>](location-path/specifying-a-location-path-sqlxml-4-0.md)  
 <span data-ttu-id="d7312-112">XPath 쿼리에서 위치 경로를 지정하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="d7312-112">Describes how to specify location paths in XPath queries.</span></span>  
  
 [<span data-ttu-id="d7312-113">예제 XPath 쿼리 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="d7312-113">Sample XPath Queries &#40;SQLXML 4.0&#41;</span></span>](samples/sample-xpath-queries-sqlxml-4-0.md)  
 <span data-ttu-id="d7312-114">SQLXML 4.0용 Xpath 쿼리 예제를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="d7312-114">Provides sample XPath queries for SQLXML 4.0.</span></span>  
  
 [<span data-ttu-id="d7312-115">&#40;SQLXML 4.0&#41;XPath 데이터 형식</span><span class="sxs-lookup"><span data-stu-id="d7312-115">XPath Data Types &#40;SQLXML 4.0&#41;</span></span>](xpath-data-types-sqlxml-4-0.md)  
 <span data-ttu-id="d7312-116">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 및 XSD의 데이터 형식과는 많이 다른 XPath 데이터 형식에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="d7312-116">Describes XPath data types, which are significantly different from those of both [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and XSD.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7312-117">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d7312-117">See Also</span></span>  
 [<span data-ttu-id="d7312-118">클라이언트 쪽 XML 서식 지정 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="d7312-118">Client-side XML Formatting &#40;SQLXML 4.0&#41;</span></span>](../sqlxml/formatting/client-side-xml-formatting-sqlxml-4-0.md)  
  
  
