---
title: '예제: CDATA 지시어 지정 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- CDATA directive
ms.assetid: 949071e6-787f-480d-bb86-3ac16a027af1
author: rothja
ms.author: jroth
ms.openlocfilehash: 9b4f949ae1e9f309a13906efe44b329db2e47ec1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728119"
---
# <a name="example-specifying-the-cdata-directive"></a><span data-ttu-id="6e91b-102">예제: CDATA 지시어 지정</span><span class="sxs-lookup"><span data-stu-id="6e91b-102">Example: Specifying the CDATA Directive</span></span>
  <span data-ttu-id="6e91b-103">지시어가 **CDATA**로 설정되면 포함된 데이터가 엔터티 인코딩되지는 않지만 CDATA 섹션에 놓여집니다.</span><span class="sxs-lookup"><span data-stu-id="6e91b-103">If the directive is set to **CDATA**, the contained data is not entity encoded, but is put in the CDATA section.</span></span> <span data-ttu-id="6e91b-104">**CDATA** 특성은 이름이 없어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6e91b-104">The **CDATA** attributes must be nameless.</span></span>  
  
 <span data-ttu-id="6e91b-105">다음 쿼리는 제품 모델 요약 설명을 CDATA 섹션에 포함시킵니다.</span><span class="sxs-lookup"><span data-stu-id="6e91b-105">The following query wraps the product model summary description in a CDATA section.</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
SELECT  1 as Tag,  
        0 as Parent,  
        ProductModelID  as [ProductModel!1!ProdModelID],  
        Name            as [ProductModel!1!Name],  
        '<Summary>This is summary description</Summary>'     
            as [ProductModel!1!!CDATA] -- no attribute name so ELEMENT assumed  
FROM    Production.ProductModel  
WHERE   ProductModelID=19  
FOR XML EXPLICIT  
```  
  
 <span data-ttu-id="6e91b-106">다음은 결과입니다.</span><span class="sxs-lookup"><span data-stu-id="6e91b-106">This is the result:</span></span>  
  
```  
<ProductModel ProdModelID="19" Name="Mountain-100">  
   <![CDATA[<Summary>This is summary description</Summary>]]>  
</ProductModel>  
```  
  
## <a name="see-also"></a><span data-ttu-id="6e91b-107">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6e91b-107">See Also</span></span>  
 [<span data-ttu-id="6e91b-108">FOR XML에서 EXPLICIT 모드 사용</span><span class="sxs-lookup"><span data-stu-id="6e91b-108">Use EXPLICIT Mode with FOR XML</span></span>](use-explicit-mode-with-for-xml.md)  
  
  
