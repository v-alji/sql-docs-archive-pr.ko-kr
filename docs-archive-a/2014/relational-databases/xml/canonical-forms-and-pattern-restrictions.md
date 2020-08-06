---
title: 정규 형식 및 패턴 제한 사항 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- pattern restrictions
- canonical forms
ms.assetid: 088314ec-7d0b-4a05-8a33-f35da5bfe59c
author: rothja
ms.author: jroth
ms.openlocfilehash: 569e8c4a01ed1eb9ae26ea9e2f6d471b9aad9fe0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646242"
---
# <a name="canonical-forms-and-pattern-restrictions"></a><span data-ttu-id="72023-102">정규 형식 및 패턴 제한 사항</span><span class="sxs-lookup"><span data-stu-id="72023-102">Canonical Forms and Pattern Restrictions</span></span>
  <span data-ttu-id="72023-103">XSD 패턴 패싯을 사용하면 단순 유형의 어휘 영역을 제한할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="72023-103">The XSD pattern facet allows for the restriction of the lexical space of simple types.</span></span> <span data-ttu-id="72023-104">어휘 표현이 둘 이상 있는 형식에 패턴 제한을 적용한 경우 일부 값으로 인해 유효성 검사 후 예기치 않은 동작이 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="72023-104">When a pattern restriction is put on a type for which there is more than one possible lexical representation, some values could cause unexpected behavior upon validation.</span></span>  
  
 <span data-ttu-id="72023-105">이러한 동작은 이러한 값의 어휘 표현이 데이터베이스에 저장되지 않기 때문에 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="72023-105">This behavior occurs because lexical representations of these values are not stored in the database.</span></span> <span data-ttu-id="72023-106">따라서 출력으로 직렬화될 때 값이 해당 정규 표현으로 변환됩니다.</span><span class="sxs-lookup"><span data-stu-id="72023-106">Therefore, the values are converted to their canonical representations when serialized as output.</span></span> <span data-ttu-id="72023-107">문서에 있는 값의 정규 형식이 값 형식에 대한 패턴 제한을 준수하지 않는 경우 사용자가 이 값을 다시 삽입하려고 하면 해당 문서는 거부됩니다.</span><span class="sxs-lookup"><span data-stu-id="72023-107">If a document contains a value whose canonical form does not comply with the pattern restriction for its type, the document is rejected if a user tries to reinsert it.</span></span>  
  
 <span data-ttu-id="72023-108">이 문제를 방지하기 위해 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서는 값의 정규 형식에서 패턴 제한 사항을 위반하기 때문에 다시 삽입할 수 없는 값이 포함된 XML 문서를 거부합니다.</span><span class="sxs-lookup"><span data-stu-id="72023-108">To prevent this, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] rejects any XML document that contains values that cannot be reinserted, because of the violation of pattern restrictions by their canonical forms.</span></span> <span data-ttu-id="72023-109">예를 들어 "33.000"이라는 값은 "33 **.0+"라는 패턴 제한이 있는** xs:decimal\\에서 파생된 형식에 대해 유효성이 확인되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="72023-109">For example, the value "33.000" does not validate against a type derived from **xs:decimal** with a pattern restriction of "33\\.0+".</span></span> <span data-ttu-id="72023-110">"33.000"은 이 패턴을 준수하지만 정규 형식인 "33"은 이 패턴을 준수하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="72023-110">Although "33.000" complies with this pattern, the canonical form, "33", does not.</span></span>  
  
 <span data-ttu-id="72023-111">따라서 `boolean`, `decimal`, `float`, `double`, `dateTime`, `time`, `date`, `hexBinary`, 및 `base64Binary`의 기본 형식에서 파생된 형식에 패턴 패싯을 적용할 때 주의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="72023-111">Therefore, you should be careful when you apply pattern facets to types derived from the following primitive types: `boolean`, `decimal`, `float`, `double`, `dateTime`, `time`, `date`, `hexBinary`, and `base64Binary`.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="72023-112">에서 경고가 발생됩니다.</span><span class="sxs-lookup"><span data-stu-id="72023-112">issues a warning when you add any such components to a schema collection.</span></span>  
  
 <span data-ttu-id="72023-113">부동 소수점 값을 부정확하게 직렬화할 경우 비슷한 문제가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="72023-113">Imprecise serialization of floating-point values has a similar problem.</span></span> <span data-ttu-id="72023-114">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 사용되는 부동 소수점 직렬화 알고리즘으로 인해 유사한 값들이 동일한 정규 형식을 공유할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="72023-114">Because of the floating-point serialization algorithm used by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], it is possible for similar values to share the same canonical form.</span></span> <span data-ttu-id="72023-115">부동 소수점 값을 직렬화하고 다시 삽입하면 값이 약간 변경될 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="72023-115">When a floating-point value is serialized and then reinserted, its value may change slightly.</span></span> <span data-ttu-id="72023-116">드물지만 이로 인해 값을 다시 삽입한 경우 값이 해당 형식에 대해 **enumeration**, **minInclusive**, **minExclusive**, **maxInclusive**또는 **maxExclusive**와 같은 패싯 중 하나를 위반할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="72023-116">In rare cases, this may result in a value that violates any of the following facets for its type on reinsertion: **enumeration**, **minInclusive**, **minExclusive**, **maxInclusive**, or **maxExclusive**.</span></span> <span data-ttu-id="72023-117">이 문제를 방지하기 위해 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서는 직렬화 및 다시 삽입할 수 없는 `xs:float` 또는 `xs:double` 에서 파생되는 형식의 값을 모두 거부합니다.</span><span class="sxs-lookup"><span data-stu-id="72023-117">To prevent this, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] rejects any values of types derived from `xs:float` or `xs:double` that cannot be serialized and reinserted.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72023-118">참고 항목</span><span class="sxs-lookup"><span data-stu-id="72023-118">See Also</span></span>  
 [<span data-ttu-id="72023-119">서버의 XML 스키마 컬렉션에 대한 요구 사항 및 제한 사항</span><span class="sxs-lookup"><span data-stu-id="72023-119">Requirements and Limitations for XML Schema Collections on the Server</span></span>](requirements-and-limitations-for-xml-schema-collections-on-the-server.md)  
  
  
