---
title: FOR XML 보안 고려 사항 (SQLXML 4.0) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- NESTED mode
- client-side XML formatting
- FOR XML clause, security
- server-side XML formatting
- AUTO mode
- security [SQLXML], FOR XML
ms.assetid: facba279-df93-475b-ad43-0043dc5bae03
author: rothja
ms.author: jroth
ms.openlocfilehash: 9a64fa61848e4b5435b2aa944c53953a8c083ab6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653775"
---
# <a name="for-xml-security-considerations-sqlxml-40"></a><span data-ttu-id="58539-102">FOR XML 보안 고려 사항(SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="58539-102">FOR XML Security Considerations (SQLXML 4.0)</span></span>
  <span data-ttu-id="58539-103">FOR XML AUTO 모드에서는 요소 이름이 테이블 이름에 매핑되고 특성 이름이 열 이름에 매핑되는 XML 계층이 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="58539-103">The FOR XML AUTO mode generates an XML hierarchy in which element names map to table names and attribute names map to column names.</span></span> <span data-ttu-id="58539-104">이를 통해 데이터베이스 테이블과 열 정보가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="58539-104">This exposes the database table and column information.</span></span> <span data-ttu-id="58539-105">AUTO 모드(서버 쪽 서식)를 사용할 때는 쿼리에 테이블 별칭과 열 별칭을 지정하여 데이터베이스 정보를 숨길 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="58539-105">You can hide the database information when you use AUTO mode (server-side formatting) by specifying table and column aliases in the query.</span></span> <span data-ttu-id="58539-106">이러한 별칭은 결과 XML 문서에 요소 이름과 특성 이름으로 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="58539-106">These aliases are returned in the resulting XML document as element and attribute names.</span></span>  
  
 <span data-ttu-id="58539-107">예를 들어 다음 쿼리에서는 AUTO 모드를 지정하므로 XML 서식이 서버에서 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="58539-107">For example, the following query specifies AUTO mode; therefore, the XML formatting is done on the server:</span></span>  
  
```  
SELECT C.FirstName as F,C.LastName as L   
FROM Person.Contact C   
FOR XML AUTO  
```  
  
 <span data-ttu-id="58539-108">다음과 같이 결과 XML 문서에서 요소 이름과 특성 이름에 별칭이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="58539-108">In the resulting XML document, the aliases are used for element and attribute names:</span></span>  
  
```  
<?xml version="1.0" encoding="utf-8" ?>   
<root>  
  <C F="Nancy" L="Fuller" />   
  <CE F="Andrew" L="Peacock" />   
  <C F="Janet" L="Leverling" />   
  ...  
</root>  
```  
  
 <span data-ttu-id="58539-109">NESTED 모드(클라이언트 쪽 서식)를 사용할 때는 결과 XML 문서에서 특성에 대해서만 별칭이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="58539-109">When you use NESTED mode (client-side formatting), aliases are returned only for attributes in the resulting XML document.</span></span> <span data-ttu-id="58539-110">기본 테이블의 이름은 항상 요소 이름으로 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="58539-110">The names of the base tables are always returned as element names.</span></span> <span data-ttu-id="58539-111">예를 들어 다음 쿼리에서는 NESTED 모드를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="58539-111">For example, the following query specifies NESTED mode.</span></span>  
  
```  
SELECT C.FirstName as F,C.LastName as L   
FROM Person.Contact C   
FOR XML AUTO  
```  
  
 <span data-ttu-id="58539-112">결과 XML 문서에서 기본 테이블의 이름은 요소 이름으로 반환되고 테이블 별칭은 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="58539-112">In the resulting XML document, the names of the base tables are returned as element names and table aliases are not used:</span></span>  
  
```  
<?xml version="1.0" encoding="utf-8" ?>   
<root>  
  <Person.Contact F="Nancy" L="Fuller" />   
  <Person.Contact F="Andrew" L="Peacock" />   
  <Person.Contact F="Janet" L="Leverling" />   
       ...  
</root>  
```  
  
  
