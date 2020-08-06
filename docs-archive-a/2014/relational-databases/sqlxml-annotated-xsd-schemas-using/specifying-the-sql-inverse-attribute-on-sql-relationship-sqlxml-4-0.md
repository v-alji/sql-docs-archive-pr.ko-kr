---
title: 'Sql: relationship에 sql: 역 특성 지정 (SQLXML 4.0) | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- sql:relationship
- bulk load [SQLXML]
- inverse attribute
- relationships [SQLXML], inverse orders
- relationship annotation
- XSD schemas [SQLXML], relationships
- annotated XSD schemas, relationships
- updategrams [SQLXML], relationships
- sql:inverse
ms.assetid: 08904cbd-9c86-493d-90c3-f5e1d13ce59d
author: rothja
ms.author: jroth
ms.openlocfilehash: 5b0781102371b98cced72a5a0edee70c9567c372
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650896"
---
# <a name="specifying-the-sqlinverse-attribute-on-sqlrelationship-sqlxml-40"></a><span data-ttu-id="85fed-102">sql:relationship에 sql:inverse 특성 지정(SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="85fed-102">Specifying the sql:inverse Attribute on sql:relationship (SQLXML 4.0)</span></span>
  <span data-ttu-id="85fed-103">`sql:inverse` 특성은 XSD 스키마를 대량 로드용이나 updategram에서 사용할 경우에만 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="85fed-103">The `sql:inverse` attribute is useful only when the XSD schema is used for either bulk load or by an updategram.</span></span> <span data-ttu-id="85fed-104">`sql:inverse`요소에 특성을 지정할 수 있습니다 **\<sql:relationship>** .</span><span class="sxs-lookup"><span data-stu-id="85fed-104">The `sql:inverse` attribute can be specified on the **\<sql:relationship>** element.</span></span> <span data-ttu-id="85fed-105">Updategram에서 updategram 논리는 스키마를 해석하여 updategram 작업으로 업데이트되는 테이블 및 열을 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="85fed-105">In updategrams, the updategram logic interprets the schema in determining the tables and columns that are updated by the updategram operation.</span></span> <span data-ttu-id="85fed-106">스키마에 지정하는 부모-자식 관계에 따라 레코드가 수정(삽입 또는 삭제)되는 순서가 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="85fed-106">The parent-child relationships that are specified in the schema determine the order in which the records are modified (inserted or deleted).</span></span>  
  
 <span data-ttu-id="85fed-107">부모-자식 관계가 해당 데이터베이스 열 간의 기본 키/외래 키 관계의 역순으로 지정된 XSD 스키마가 있는 경우 기본 키/외래 키 위반 때문에 삽입 또는 삭제 Updategram 작업이 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="85fed-107">If you have an XSD schema in which the parent-child relationship is specified in the inverse order of the primary-key/foreign-key relationship between the corresponding database columns, the insert or delete updategram operation will fail because of the primary-key/foreign-key violation.</span></span> <span data-ttu-id="85fed-108">이러한 경우 `sql:inverse` 요소에 특성이 지정 되 고 ( `sql:inverse="true"` ) **\<sql:relationship>** updategram 논리는 스키마에 지정 된 부모-자식 관계의 해석을 반대 합니다.</span><span class="sxs-lookup"><span data-stu-id="85fed-108">In such cases, the `sql:inverse` attribute is specified (`sql:inverse="true"`) in the **\<sql:relationship>** element, and the updategram logic inverses its interpretation of the parent-child relationship specified in the schema.</span></span>  
  
 <span data-ttu-id="85fed-109">`sql:inverse` 특성은 부울 값(0=false, 1=true)을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="85fed-109">The `sql:inverse` attribute takes a Boolean value (0=false, 1=true).</span></span> <span data-ttu-id="85fed-110">허용되는 값은 0, 1, true 및 false입니다.</span><span class="sxs-lookup"><span data-stu-id="85fed-110">The acceptable values are 0, 1, true, and false.</span></span>  
  
 <span data-ttu-id="85fed-111">주석을 사용 하는 작업 예제는 `sql:inverse` [Updategram에서 주석이 추가 된 매핑 스키마 지정](../sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/specifying-an-annotated-mapping-schema-in-an-updategram-sqlxml-4-0.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="85fed-111">For a working sample using the `sql:inverse` annotation, see [Specifying an Annotated Mapping Schema in an Updategram](../sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/specifying-an-annotated-mapping-schema-in-an-updategram-sqlxml-4-0.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85fed-112">참고 항목</span><span class="sxs-lookup"><span data-stu-id="85fed-112">See Also</span></span>  
 [<span data-ttu-id="85fed-113">Sql: relationship &#40;SQLXML 4.0&#41;를 사용 하 여 관계 지정</span><span class="sxs-lookup"><span data-stu-id="85fed-113">Specifying Relationships Using sql:relationship &#40;SQLXML 4.0&#41;</span></span>](specifying-relationships-using-sql-relationship-sqlxml-4-0.md)  
  
  
