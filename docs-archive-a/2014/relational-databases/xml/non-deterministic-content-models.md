---
title: 비결정적 콘텐츠 모델 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- non-deterministic content models
- content models [XML in SQL Server]
ms.assetid: 9d4513e7-dd19-4491-b7c7-28bc7c2f8589
author: rothja
ms.author: jroth
ms.openlocfilehash: 6182ff4a5ee0c9c109f6880c7d3337fb6dd20749
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87729151"
---
# <a name="non-deterministic-content-models"></a><span data-ttu-id="d8320-102">비결정적 콘텐츠 모델</span><span class="sxs-lookup"><span data-stu-id="d8320-102">Non-Deterministic Content Models</span></span>
  <span data-ttu-id="d8320-103">[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] SP1(서비스 팩 1) 이전에, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서는 비결정적 콘텐츠 모델이 있는 XML 스키마를 거부했습니다.</span><span class="sxs-lookup"><span data-stu-id="d8320-103">Before [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Service Pack 1 (SP1), [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] rejected XML schemas that had non-deterministic content models.</span></span>  
  
 <span data-ttu-id="d8320-104">그러나 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] SP1부터 비결정적 콘텐츠 모델은 발생빈도 제약 조건이 0 또는 1이거나 해제된 경우 허용됩니다.</span><span class="sxs-lookup"><span data-stu-id="d8320-104">Beginning with [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] SP1, however, non-deterministic content models are accepted if the occurrence constraints are 0,1, or unbounded.</span></span>  
  
## <a name="example-non-deterministic-content-model-rejected"></a><span data-ttu-id="d8320-105">예제: 비결정적 콘텐츠 모델이 거부됨</span><span class="sxs-lookup"><span data-stu-id="d8320-105">Example: Non-deterministic content model rejected</span></span>  
 <span data-ttu-id="d8320-106">다음 예에서는 비결정적 콘텐츠 모델이 있는 XML 스키마를 만들려고 시도합니다.</span><span class="sxs-lookup"><span data-stu-id="d8320-106">The following example attempts to create an XML schema with a non-deterministic content model.</span></span> <span data-ttu-id="d8320-107">`<root>` 요소에 `<a>` 요소가 두 개 포함된 하나의 시퀀스가 있는지 또는 `<root>` 요소에 각각 `<a>` 요소가 하나씩 포함된 두 개의 시퀀스가 있는지가 명확하지 않기 때문에 이 코드는 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="d8320-107">The code fails because it is not clear whether the `<root>` element should have a sequence of two `<a>` elements or if the `<root>` element should have two sequences, each with an `<a>` element.</span></span>  
  
```  
CREATE XML SCHEMA COLLECTION MyCollection AS '  
<schema xmlns="http://www.w3.org/2001/XMLSchema">  
    <element name="root">  
        <complexType>  
            <sequence minOccurs="1" maxOccurs="2">  
                <element name="a" type="string" minOccurs="1" maxOccurs="2"/>  
            </sequence>  
        </complexType>  
    </element>  
</schema>  
'  
GO  
```  
  
 <span data-ttu-id="d8320-108">발생빈도 제약 조건을 고유한 위치로 이동하여 스키마를 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d8320-108">The schema can be fixed by moving the occurrence constraint to a unique location.</span></span> <span data-ttu-id="d8320-109">예를 들어 이 제약 조건을 포함하는 시퀀스 파티클로 이동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d8320-109">For example, the constraint can be moved to the containing sequence particle:</span></span>  
  
```  
<sequence minOccurs="1" maxOccurs="4">  
    <element name="a" type="string" minOccurs="1" maxOccurs="1"/>  
</sequence>  
```  
  
 <span data-ttu-id="d8320-110">또는 이 제약 조건을 포함된 요소로 이동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d8320-110">Or the constraint can be moved to the contained element:</span></span>  
  
```  
<sequence minOccurs="1" maxOccurs="1">  
     <element name="a" type="string" minOccurs="1" maxOccurs="4"/>  
</sequence>  
```  
  
## <a name="example-non-deterministic-content-model-accepted"></a><span data-ttu-id="d8320-111">예제: 비결정적 콘텐츠 모델이 허용됨</span><span class="sxs-lookup"><span data-stu-id="d8320-111">Example: Non-deterministic content model accepted</span></span>  
 <span data-ttu-id="d8320-112">다음 스키마는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SP1 이전의 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 버전에서 거부됩니다.</span><span class="sxs-lookup"><span data-stu-id="d8320-112">The following schema would be rejected in versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] before [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] SP1.</span></span>  
  
```  
CREATE XML SCHEMA COLLECTION MyCollection AS '  
<schema xmlns="http://www.w3.org/2001/XMLSchema">  
    <element name="root">  
        <complexType>  
            <sequence minOccurs="0" maxOccurs="unbounded">  
                <element name="a" type="string" minOccurs="0" maxOccurs="1"/>  
                <element name="b" type="string" minOccurs="1" maxOccurs="unbounded"/>  
            </sequence>  
        </complexType>  
    </element>  
</schema>  
'  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="d8320-113">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d8320-113">See Also</span></span>  
 [<span data-ttu-id="d8320-114">서버의 XML 스키마 컬렉션에 대한 요구 사항 및 제한 사항</span><span class="sxs-lookup"><span data-stu-id="d8320-114">Requirements and Limitations for XML Schema Collections on the Server</span></span>](requirements-and-limitations-for-xml-schema-collections-on-the-server.md)  
  
  
