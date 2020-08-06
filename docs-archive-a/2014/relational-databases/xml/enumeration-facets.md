---
title: 열거 패싯 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- enumeration facets
ms.assetid: dec23a79-ddd6-4701-9721-55a2c435a34d
author: rothja
ms.author: jroth
ms.openlocfilehash: 7e06598890d9b652879327e0351db5113cc17e6a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646227"
---
# <a name="enumeration-facets"></a><span data-ttu-id="75dc1-102">열거 패싯</span><span class="sxs-lookup"><span data-stu-id="75dc1-102">Enumeration Facets</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="75dc1-103">는 패턴 패싯 형식이나 이러한 패싯을 위반하는 열거형의 XML 스키마를 거부합니다.</span><span class="sxs-lookup"><span data-stu-id="75dc1-103">rejects XML schemas with types that have pattern facets or enumerations that violate those facets.</span></span>  
  
## <a name="example"></a><span data-ttu-id="75dc1-104">예제</span><span class="sxs-lookup"><span data-stu-id="75dc1-104">Example</span></span>  
 <span data-ttu-id="75dc1-105">다음 스키마는 주요 열거 값이 대/소문자 값을 포함하기 때문에 거부됩니다.</span><span class="sxs-lookup"><span data-stu-id="75dc1-105">The following schema would be rejected, because the featured enumeration value includes a mixed-case value.</span></span> <span data-ttu-id="75dc1-106">또한 이 값이 소문자로만 값을 제한하는 패턴 값을 위반하기 때문에 거부됩니다.</span><span class="sxs-lookup"><span data-stu-id="75dc1-106">It would also be rejected because this value violates the pattern value that limits values to only lowercase letters.</span></span>  
  
```  
CREATE XML SCHEMA COLLECTION MySampleCollection AS '  
<schema xmlns="http://www.w3.org/2001/XMLSchema" targetNamespace="http://ns" xmlns:ns="http://ns">  
    <simpleType name="MyST">  
       <restriction base="string">  
          <pattern value="[a-z]*"/>  
       </restriction>  
    </simpleType>  
  
    <simpleType name="MyST2">  
       <restriction base="ns:MyST">  
           <enumeration value="mYstring"/>  
       </restriction>  
    </simpleType>  
</schema>'  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="75dc1-107">참고 항목</span><span class="sxs-lookup"><span data-stu-id="75dc1-107">See Also</span></span>  
 [<span data-ttu-id="75dc1-108">서버의 XML 스키마 컬렉션에 대한 요구 사항 및 제한 사항</span><span class="sxs-lookup"><span data-stu-id="75dc1-108">Requirements and Limitations for XML Schema Collections on the Server</span></span>](requirements-and-limitations-for-xml-schema-collections-on-the-server.md)  
  
  
