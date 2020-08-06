---
title: 기존 열을 XML 열로 변경 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- tables [XML]
ms.assetid: 0d951424-9862-41fe-bd46-127f1c059bcb
author: rothja
ms.author: jroth
ms.openlocfilehash: 32447851fcfe2a54143a028a94539532bba6708d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646240"
---
# <a name="change-existing-columns-to-xml-columns"></a><span data-ttu-id="dc610-102">기존 열을 XML 열로 변경</span><span class="sxs-lookup"><span data-stu-id="dc610-102">Change Existing Columns to XML Columns</span></span>
  <span data-ttu-id="dc610-103">ALTER TABLE 문은 `xml` 데이터 형식을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="dc610-103">The ALTER TABLE statement supports the `xml` data type.</span></span> <span data-ttu-id="dc610-104">예를 들어 모든 문자열 유형 열을 `xml` 데이터 형식으로 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc610-104">For example, you can alter any string type column to the `xml` data type.</span></span> <span data-ttu-id="dc610-105">이 경우 열에 포함된 문서는 올바른 형식이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dc610-105">Note that in these cases, the documents contained in the column must be well formed.</span></span> <span data-ttu-id="dc610-106">또한 열 유형을 문자열에서 형식화된 xml로 변경할 경우 지정된 XSD 스키마에 대해 열에 있는 문서의 유효성을 검사합니다.</span><span class="sxs-lookup"><span data-stu-id="dc610-106">Also, if you are changing the type of the column from string to typed xml, the documents in the column are validated against the specified XSD schemas.</span></span>  
  
```  
CREATE TABLE T (Col1 int primary key, Col2 nvarchar(max))  
GO  
INSERT INTO T   
VALUES (1, '<Root><Product ProductID="1"/></Root>')  
GO  
ALTER TABLE T   
ALTER COLUMN Col2 xml  
GO  
```  
  
 <span data-ttu-id="dc610-107">`xml` 유형 열을 형식화되지 않은 XML에서 형식화된 XML로 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc610-107">You can change an `xml` type column from untyped XML to typed XML.</span></span> <span data-ttu-id="dc610-108">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="dc610-108">For example:</span></span>  
  
```  
CREATE TABLE T (Col1 int primary key, Col2 xml)  
GO  
INSERT INTO T   
values (1, '<p1:ProductDescription ProductModelID="1"   
xmlns:p1="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription">  
            </p1:ProductDescription>')  
GO   
-- Make it a typed xml column by specifying a schema collection.  
ALTER TABLE T   
ALTER COLUMN Col2 xml (Production.ProductDescriptionSchemaCollection)  
GO  
```  
  
> [!NOTE]  
>  <span data-ttu-id="dc610-109">XML 스키마 컬렉션인 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 이 `Production.ProductDescriptionSchemaCollection`데이터베이스의 일부로 생성되기 때문에 이 스크립트는 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 데이터베이스에 대해 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="dc610-109">The script will run against [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database, because the XML schema collection, `Production.ProductDescriptionSchemaCollection`, is created as part of the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database.</span></span>  
  
 <span data-ttu-id="dc610-110">이전 예에서는 지정된 컬렉션에 있는 XSD 스키마에 대해 열에 저장된 모든 인스턴스의 유효성을 검사하고 이러한 인스턴스를 형식화합니다.</span><span class="sxs-lookup"><span data-stu-id="dc610-110">In the previous example, all the instances stored in the column are validated and typed against the XSD schemas in the specified collection.</span></span> <span data-ttu-id="dc610-111">지정한 스키마에 맞지 않는 XML 인스턴스가 열에 하나 이상 있을 경우 `ALTER TABLE` 문이 실패하고 형식화되지 않은 XML 열을 형식화된 XML로 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="dc610-111">If the column contains one or more XML instances that are invalid with regard to the specified schema, the `ALTER TABLE` statement will fail and you will not be able to change your untyped XML column into typed XML.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="dc610-112">테이블이 클 경우 `xml` 유형 열을 수정하는 데 비용이 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc610-112">If a table is large, modifying an `xml` type column can be costly.</span></span> <span data-ttu-id="dc610-113">각 문서의 형식이 형식화된 XML로서 알맞은지 검사하고 유효성을 검사해야 하기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="dc610-113">This is because each document must be checked for being well formed and, for typed XML, must also be validated.</span></span>  
  
 <span data-ttu-id="dc610-114">형식화된 XML에 대한 자세한 내용은 [형식화된 XML과 형식화되지 않은 XML 비교](compare-typed-xml-to-untyped-xml.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="dc610-114">For more information about typed XML, see [Compare Typed XML to Untyped XML](compare-typed-xml-to-untyped-xml.md).</span></span>  
  
  
