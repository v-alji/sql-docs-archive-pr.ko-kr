---
title: XML 열에서 뷰 만들기 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- views [XML in SQL Server]
ms.assetid: eb5f0439-1f69-49c2-8759-e59bda1633b7
author: rothja
ms.author: jroth
ms.openlocfilehash: bf06f1107cbf4875eb63fe6747775b5c5c04810c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738079"
---
# <a name="create-views-over-xml-columns"></a><span data-ttu-id="c77b8-102">XML 열에서 뷰 만들기</span><span class="sxs-lookup"><span data-stu-id="c77b8-102">Create Views over XML Columns</span></span>
  <span data-ttu-id="c77b8-103">`xml` 유형 열을 사용하여 뷰를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c77b8-103">You can use an `xml` type column to create views.</span></span> <span data-ttu-id="c77b8-104">다음 예에서는 `xml` 데이터 형식의 `value()` 메서드를 사용하여 `xml` 유형 열의 값을 검색하는 뷰를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c77b8-104">The following example creates a view in which the value from an `xml` type column is retrieved using the `value()` method of the `xml` data type.</span></span>  
  
```  
-- Create the table.  
CREATE TABLE T (  
    ProductID          int primary key,   
    CatalogDescription xml)  
GO  
-- Insert sample data.  
INSERT INTO T values(1,'<ProductDescription ProductID="1" ProductName="SomeName" />')  
GO  
-- Create view (note the value() method used to retrieve ProductName   
-- attribute value from the XML).  
CREATE VIEW MyView AS   
  SELECT ProductID,  
         CatalogDescription.value('(/ProductDescription/@ProductName)[1]', 'varchar(40)') AS PName  
  FROM T  
GO   
```  
  
 <span data-ttu-id="c77b8-105">뷰에 대해 다음 쿼리를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="c77b8-105">Execute the following query against the view:</span></span>  
  
```  
SELECT *   
FROM   MyView  
```  
  
 <span data-ttu-id="c77b8-106">다음은 결과입니다.</span><span class="sxs-lookup"><span data-stu-id="c77b8-106">This is the result:</span></span>  
  
```  
ProductID   PName        
----------- ------------  
1           SomeName   
```  
  
 <span data-ttu-id="c77b8-107">다음은 `xml` 데이터 형식을 사용하여 뷰를 만드는 방법에 대한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="c77b8-107">Note the following points about using the `xml` data type to create views:</span></span>  
  
-   <span data-ttu-id="c77b8-108">xml 데이터 형식은 구체화된 뷰에서 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c77b8-108">The xml data type can be created in a materialized view.</span></span> <span data-ttu-id="c77b8-109">구체화된 뷰는 XML 데이터 형식의 메서드를 기반으로 할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c77b8-109">The materialized view cannot be based on an xml data type method.</span></span> <span data-ttu-id="c77b8-110">하지만 기본 테이블에 있는 xml 유형의 열과는 다른 XML 스키마 컬렉션으로 캐스팅할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c77b8-110">However, it can be cast to an XML schema collection that is different from the xml type column in the base table.</span></span>  
  
-   <span data-ttu-id="c77b8-111">분산형 분할 뷰에서는 `xml` 데이터 형식을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c77b8-111">The `xml` data type cannot be used in Distributed Partitioned Views.</span></span>  
  
-   <span data-ttu-id="c77b8-112">뷰에 대해 실행하는 SQL 조건자는 뷰 정의의 XQuery에 밀어넣지 못합니다.</span><span class="sxs-lookup"><span data-stu-id="c77b8-112">SQL predicates running against the view will not be pushed into the XQuery of the view definition.</span></span>  
  
-   <span data-ttu-id="c77b8-113">뷰의 XML 데이터 형식 메서드는 업데이트할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c77b8-113">XML data type methods in a view are not updatable.</span></span>  
  
  
