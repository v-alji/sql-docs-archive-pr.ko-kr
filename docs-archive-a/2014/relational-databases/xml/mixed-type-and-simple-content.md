---
title: 혼합 형식 및 단순 내용 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- mixed types [SQL Server]
ms.assetid: 6ea1f11d-e64b-4ebb-ab68-4eb6e4027665
author: rothja
ms.author: jroth
ms.openlocfilehash: eb46769ee4c4d635af36a3c50fda34e8e1801b34
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87729156"
---
# <a name="mixed-type-and-simple-content"></a><span data-ttu-id="2f06f-102">혼합 형식 및 단순 내용</span><span class="sxs-lookup"><span data-stu-id="2f06f-102">Mixed Type and Simple Content</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="2f06f-103">에서는 혼합 형식을 단순 내용으로 제한할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2f06f-103">does not support restricting a mixed type to a simple content.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2f06f-104">예제</span><span class="sxs-lookup"><span data-stu-id="2f06f-104">Example</span></span>  
 <span data-ttu-id="2f06f-105">아래의 XML 스키마 컬렉션에서 `myComplexTypeA` 는 혼합 형식으로 비워둘 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f06f-105">In the following XML schema collection, `myComplexTypeA` is a complex type that can be emptied.</span></span> <span data-ttu-id="2f06f-106">즉 해당 요소의 `minOccurs` 가 모두 0으로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="2f06f-106">That is, both its elements have `minOccurs` set to 0.</span></span> <span data-ttu-id="2f06f-107">`myComplexTypeB` 선언에서처럼 혼합 형식을 단순 내용으로 제한하려는 시도는 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2f06f-107">The attempt to restrict this to a simple content, as in the `myComplexTypeB` declaration, is not supported.</span></span> <span data-ttu-id="2f06f-108">따라서 다음과 같은 XML 스키마 컬렉션을 만들 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2f06f-108">Therefore, the following XML schema collection creation fails:</span></span>  
  
```  
CREATE XML SCHEMA COLLECTION SC AS '  
<schema xmlns="http://www.w3.org/2001/XMLSchema" targetNamespace="http://ns" xmlns:ns="http://ns"  
xmlns:ns1="http://ns1">  
  
    <complexType name="myComplexTypeA" mixed="true">  
        <sequence>  
            <element name="a" type="string" minOccurs="0"/>  
            <element name="b" type="string" minOccurs="0" maxOccurs="23"/>  
        </sequence>  
    </complexType>  
  
    <complexType name="myComplexTypeB">  
        <simpleContent>  
            <restriction base="ns:myComplexTypeA">  
                <simpleType>  
                    <restriction base="int">  
                        <minExclusive value="25"/>  
                    </restriction>  
                </simpleType>  
            </restriction>  
        </simpleContent>  
    </complexType>  
</schema>  
'  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="2f06f-109">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2f06f-109">See Also</span></span>  
 [<span data-ttu-id="2f06f-110">서버의 XML 스키마 컬렉션에 대한 요구 사항 및 제한 사항</span><span class="sxs-lookup"><span data-stu-id="2f06f-110">Requirements and Limitations for XML Schema Collections on the Server</span></span>](requirements-and-limitations-for-xml-schema-collections-on-the-server.md)  
  
  
