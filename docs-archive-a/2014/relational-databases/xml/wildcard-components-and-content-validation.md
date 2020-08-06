---
title: 와일드카드 구성 요소 및 콘텐츠 유효성 검사 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- wildcard components [XML]
- content validation [XML]
ms.assetid: ffa7d974-3645-446c-8425-f0b22b6b060a
author: rothja
ms.author: jroth
ms.openlocfilehash: 76ff2b48efb8cff0b98827fe8522405682c294e2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647548"
---
# <a name="wildcard-components-and-content-validation"></a><span data-ttu-id="599e5-102">와일드카드 구성 요소 및 콘텐츠 유효성 검사</span><span class="sxs-lookup"><span data-stu-id="599e5-102">Wildcard Components and Content Validation</span></span>
  <span data-ttu-id="599e5-103">와일드카드 구성 요소는 콘텐츠 모델에 나타나는 형식의 유연성을 향상시키는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="599e5-103">Wildcard components are used to increase flexibility in what is allowed to appear in a content model.</span></span> <span data-ttu-id="599e5-104">이러한 구성 요소는 XSD 언어에서 다음과 같은 방식으로 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="599e5-104">These components are supported in the XSD language in the following ways:</span></span>  
  
-   <span data-ttu-id="599e5-105">요소 와일드카드 구성 요소:</span><span class="sxs-lookup"><span data-stu-id="599e5-105">Element wildcard components.</span></span> <span data-ttu-id="599e5-106">이러한 구성 요소는 **\<xsd:any>** 요소로 표현됩니다.</span><span class="sxs-lookup"><span data-stu-id="599e5-106">These are represented by the **\<xsd:any>** element.</span></span>  
  
-   <span data-ttu-id="599e5-107">특성 와일드카드 구성 요소:</span><span class="sxs-lookup"><span data-stu-id="599e5-107">Attribute wildcard components.</span></span> <span data-ttu-id="599e5-108">이러한 구성 요소는 **\<xsd:anyAttribute>** 요소로 표현됩니다.</span><span class="sxs-lookup"><span data-stu-id="599e5-108">These are represented by the **\<xsd:anyAttribute>** element.</span></span>  
  
 <span data-ttu-id="599e5-109">**\<xsd:any>** 및 **\<xsd:anyAttribute>** 와일드카드 문자 요소는 모두 **processContents** 특성의 사용을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="599e5-109">Both wildcard character elements, **\<xsd:any>** and **\<xsd:anyAttribute>**, support the use of a **processContents** attribute.</span></span> <span data-ttu-id="599e5-110">이렇게 하면 XML 애플리케이션에서 이러한 와일드카드 문자 요소와 관련된 문서 내용에 대한 유효성 검사를 처리하는 방법을 나타내는 값을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="599e5-110">This lets you specify a value that indicates how XML applications handle the validation of document content associated with these wildcard character elements.</span></span> <span data-ttu-id="599e5-111">다음은 다양한 값과 해당 기능에 대한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="599e5-111">These are the different values and their effect:</span></span>  
  
-   <span data-ttu-id="599e5-112">**strict** 값은 콘텐츠의 유효성을 완전히 검사하도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="599e5-112">The **strict** value specifies that the contents are fully validated.</span></span>  
  
-   <span data-ttu-id="599e5-113">**skip** 값은 콘텐츠의 유효성을 검사하지 않도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="599e5-113">The **skip** value specifies that the contents are not validated.</span></span>  
  
-   <span data-ttu-id="599e5-114">**lax** 값은 스키마 정의가 사용 가능한 요소와 특성에 대해서만 유효성을 검사하도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="599e5-114">The **lax** value specifies that only elements and attributes for which schema definitions are available are validated.</span></span>  
  
## <a name="lax-validation-and-xsanytype-elements"></a><span data-ttu-id="599e5-115">lax 유효성 검사 및 xs:anyType 요소</span><span class="sxs-lookup"><span data-stu-id="599e5-115">Lax Validation and xs:anyType Elements</span></span>  
 <span data-ttu-id="599e5-116">XML 스키마 사양에서는 **anyType** 유형의 요소에 대해 **lax** 유효성 검사를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="599e5-116">The XML Schema specification uses **lax** validation for elements of the **anyType** type.</span></span> <span data-ttu-id="599e5-117">[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 에서는 lax 유효성 검사를 지원하지 않았으므로 **anyType**요소에 엄격한 유효성 검사가 적용되었습니다.</span><span class="sxs-lookup"><span data-stu-id="599e5-117">Because [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] did not support lax validation, strict validation was applied for elements of the **anyType**.</span></span> <span data-ttu-id="599e5-118">[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]부터는 lax 유효성 검사가 지원되므로</span><span class="sxs-lookup"><span data-stu-id="599e5-118">Beginning with [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], lax validation is supported.</span></span> <span data-ttu-id="599e5-119">이를 통해 **anyType** 유형 요소의 콘텐츠에 대한 유효성이 검사됩니다.</span><span class="sxs-lookup"><span data-stu-id="599e5-119">Content of elements of type **anyType** will be validated using lax validation.</span></span>  
  
 <span data-ttu-id="599e5-120">다음 예에서는 lax 유효성 검사를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="599e5-120">The following example illustrates the lax validation.</span></span> <span data-ttu-id="599e5-121">스키마 요소 `e` 는 **anyType** 유형 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="599e5-121">The schema element `e` is of the **anyType** type.</span></span> <span data-ttu-id="599e5-122">이 예에서는 형식화된 **xml** 변수를 만들고 **anyType** 유형 요소의 lax 유효성 검사에 대해 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="599e5-122">The example creates typed **xml** variables and illustrates the lax validation of the element of the **anyType** type.</span></span>  
  
```  
CREATE XML SCHEMA COLLECTION SC AS '  
<schema xmlns="http://www.w3.org/2001/XMLSchema"   
        targetNamespace="http://ns">  
   <element name="e" type="anyType"/>  
   <element name="a" type="byte"/>  
   <element name="b" type="string"/>  
 </schema>'  
GO  
```  
  
 <span data-ttu-id="599e5-123">`<e>` 의 유효성 검사가 성공하므로 다음 예도 성공합니다.</span><span class="sxs-lookup"><span data-stu-id="599e5-123">The following example succeeds, because the validation of `<e>` is successful:</span></span>  
  
```  
DECLARE @var XML(SC)  
SET @var = '<e xmlns="http://ns"><a>1</a><b>data</b></e>'  
GO  
```  
  
 <span data-ttu-id="599e5-124">다음 예도 성공합니다.</span><span class="sxs-lookup"><span data-stu-id="599e5-124">The following example succeeds.</span></span> <span data-ttu-id="599e5-125">스키마에서 `<c>` 요소가 정의되지 않더라도 인스턴스는 수락됩니다.</span><span class="sxs-lookup"><span data-stu-id="599e5-125">The instance is accepted, even though no element `<c>` is defined in the schema:</span></span>  
  
```  
DECLARE @var XML(SC)  
SET @var = '<e xmlns="http://ns"><a>1</a><c>Wrong</c><b>data</b></e>'  
GO  
```  
  
 <span data-ttu-id="599e5-126">다음 예에서 `<a>` 요소의 정의는 문자열 값을 사용할 수 없기 때문에 XML 인스턴스가 거부됩니다.</span><span class="sxs-lookup"><span data-stu-id="599e5-126">The XML instance in the following example is rejected, because the definition of the `<a>` element does not allow a string value.</span></span>  
  
```  
DECLARE @var XML(SC)  
SET @var = '<e xmlns="http://ns"><a>Wrong</a><b>data</b></e>'  
SELECT @var  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="599e5-127">참고 항목</span><span class="sxs-lookup"><span data-stu-id="599e5-127">See Also</span></span>  
 [<span data-ttu-id="599e5-128">서버의 XML 스키마 컬렉션에 대한 요구 사항 및 제한 사항</span><span class="sxs-lookup"><span data-stu-id="599e5-128">Requirements and Limitations for XML Schema Collections on the Server</span></span>](requirements-and-limitations-for-xml-schema-collections-on-the-server.md)  
  
  
