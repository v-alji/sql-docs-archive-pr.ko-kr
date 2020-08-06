---
title: 저장된 XML 스키마 컬렉션 보기 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- schema collections [SQL Server], viewing
- XML schemas [SQL Server], viewing
- CREATE XML SCHEMA COLLECTION statement
- xml_schema_namespace function
- XML schema collections [SQL Server], viewing
- displaying XML schema collections
- viewing XML schema collections
ms.assetid: e38031af-22df-4cd9-a14e-e316b822f91b
author: rothja
ms.author: jroth
ms.openlocfilehash: 6383fb17183a991d2f83325044663cc9671e9442
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647545"
---
# <a name="view-a-stored-xml-schema-collection"></a><span data-ttu-id="7a927-102">저장된 XML 스키마 컬렉션 보기</span><span class="sxs-lookup"><span data-stu-id="7a927-102">View a Stored XML Schema Collection</span></span>
  <span data-ttu-id="7a927-103">[CREATE XML SCHEMA COLLECTION](/sql/t-sql/statements/create-xml-schema-collection-transact-sql)을 사용하여 XML 스키마 컬렉션을 가져오면 스키마 구성 요소가 메타데이터에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="7a927-103">After you import an XML schema collection by using [CREATE XML SCHEMA COLLECTION](/sql/t-sql/statements/create-xml-schema-collection-transact-sql), the schema components are stored in the metadata.</span></span> <span data-ttu-id="7a927-104">[xml_schema_namespace](/sql/t-sql/xml/xml-schema-namespace)내장 함수를 사용하여 XML 스키마 컬렉션을 다시 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7a927-104">You can use the [xml_schema_namespace](/sql/t-sql/xml/xml-schema-namespace)intrinsic function to reconstruct the XML schema collection.</span></span> <span data-ttu-id="7a927-105">이 함수는 `xml` 데이터 형식을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="7a927-105">This function returns an `xml` data type instance.</span></span>  
  
 <span data-ttu-id="7a927-106">예를 들어 다음 쿼리는`ProductDescriptionSchemaCollection`데이터베이스의 프로덕션 관계형 스키마에서 XML 스키마 컬렉션( [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] )을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="7a927-106">For example, the following query retrieves an XML schema collection (`ProductDescriptionSchemaCollection`) from the production relational schema in the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database.</span></span>  
  
```  
SELECT xml_schema_namespace(N'Production',N'ProductDescriptionSchemaCollection')  
GO  
```  
  
 <span data-ttu-id="7a927-107">XML 스키마 컬렉션에서 한 개의 스키마만 표시하려면 `xml_schema_namespace`가 반환하는 `xml` 유형 결과에 대해 XQuery를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7a927-107">If you want to see only one schema from the XML schema collection, you can specify XQuery against the `xml` type result that is returned by `xml_schema_namespace`.</span></span>  
  
```  
SELECT xml_schema_namespace(N'RelationalSchemaName',N'XmlSchemaCollectionName').query('  
/xs:schema[@targetNamespace="TargetNameSpace"]  
')  
GO  
```  
  
 <span data-ttu-id="7a927-108">예를 들어 다음 쿼리는 `ProductDescriptionSchemaCollection` XML 스키마 컬렉션에서 제품 보증 및 유지 관리 XML 스키마 정보를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="7a927-108">For example, the following query retrieves product warranty and maintenance XML schema information from the `ProductDescriptionSchemaCollection` XML schema collection.</span></span>  
  
```  
SELECT xml_schema_namespace(N'Production',N'ProductDescriptionSchemaCollection').query('  
/xs:schema[@targetNamespace="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain"]  
')  
GO  
```  
  
 <span data-ttu-id="7a927-109">또한 선택적인 대상 네임스페이스를 세 번째 매개 변수로 `xml_schema_namespace` 함수에 전달하여 다음 쿼리처럼 컬렉션에서 특정 스키마를 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7a927-109">You can also pass the optional target namespace as the third parameter to the `xml_schema_namespace` function to retrieve specific schema from the collection, as shown in the following query:</span></span>  
  
```  
SELECT xml_schema_namespace(N'Production',N'ProductDescriptionSchemaCollection', N'https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain')  
GO  
```  
  
 <span data-ttu-id="7a927-110">데이터베이스에 CREATE XML SCHEMA COLLECTION을 사용하여 XML 스키마 컬렉션을 만들면 스키마 구성 요소가 메타데이터에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="7a927-110">When you create an XML schema collection by using CREATE XML SCHEMA COLLECTION in the database, the statement stores the schema components in the metadata.</span></span> <span data-ttu-id="7a927-111">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 가 인식하는 스키마 구성 요소만 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="7a927-111">Note that only the schema components that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] understands are stored.</span></span> <span data-ttu-id="7a927-112">설명, 주석 또는 비-XSD 특성은 저장되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7a927-112">Any comments, annotations, or non-XSD attributes are not stored.</span></span> <span data-ttu-id="7a927-113">따라서 **xml_schema_namespace** 가 다시 만든 스키마는 원래 스키마와 동일한 기능을 하지만 모양이 반드시 같을 필요는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7a927-113">Therefore, the schema reconstructed by **xml_schema_namespace** is functionally equivalent to the original schema, but it will not necessarily look the same.</span></span> <span data-ttu-id="7a927-114">예를 들어 원래 스키마에 있던 동일한 접두사가 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7a927-114">For example, you will not see the same prefixes you had in the original schema.</span></span> <span data-ttu-id="7a927-115">**xml_schema_namespace** 에서 반환된 스키마는 **t** 를 대상 네임스페이스에 대한 접두사로 사용하고 **ns1**, **ns2**등을 다른 네임스페이스에 대한 접두사로 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="7a927-115">The schema returned by **xml_schema_namespace** uses **t** as the prefix for the target namespace and **ns1**, **ns2**, and so on, for other namespaces.</span></span>  
  
 <span data-ttu-id="7a927-116">XML 스키마의 동일한 복사본을 보존하려면 XML 스키마를 파일에 저장하거나 `xml` 유형 열에 있는 데이터베이스 테이블에 저장해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a927-116">If you want to retain an identical copy of the XML schemas, you should save your XML schema in a file or in a database table in an `xml` type column.</span></span>  
  
 <span data-ttu-id="7a927-117">또한 [sys.xml_schema_collections](/sql/relational-databases/system-catalog-views/sys-xml-schema-collections-transact-sql) 카탈로그 뷰는 XML 스키마 컬렉션에 대한 정보를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="7a927-117">The [sys.xml_schema_collections](/sql/relational-databases/system-catalog-views/sys-xml-schema-collections-transact-sql) catalog view also returns information about XML schema collections.</span></span> <span data-ttu-id="7a927-118">이 정보에는 컬렉션의 이름, 만든 날짜, 컬렉션의 소유자 등이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="7a927-118">This information includes the name of the collection, the creation date, and the owner of the collection.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a927-119">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7a927-119">See Also</span></span>  
 [<span data-ttu-id="7a927-120">XML 스키마 컬렉션&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="7a927-120">XML Schema Collections &#40;SQL Server&#41;</span></span>](xml-schema-collections-sql-server.md)  
  
  
