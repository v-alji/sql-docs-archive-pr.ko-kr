---
title: XML 스키마 컬렉션에 대한 사용 권한 취소 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- revoking permissions [SQL Server]
ms.assetid: 4e542b70-2d56-4a65-8a39-96a1ed477ca6
author: rothja
ms.author: jroth
ms.openlocfilehash: 3ab37c915f14207376e0c4a9582611bf8e65e0d2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730228"
---
# <a name="revoke-permissions-on-an-xml-schema-collection"></a><span data-ttu-id="9bb7a-102">XML 스키마 컬렉션에 대한 사용 권한 취소</span><span class="sxs-lookup"><span data-stu-id="9bb7a-102">Revoke Permissions on an XML Schema Collection</span></span>
  <span data-ttu-id="9bb7a-103">XML 스키마 컬렉션을 만드는 권한은 다음 중 하나를 사용하여 취소할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9bb7a-103">The permission to create an XML schema collection can be revoked by using one of the following:</span></span>  
  
-   <span data-ttu-id="9bb7a-104">관계형 스키마에 대한 ALTER 권한을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="9bb7a-104">Revoke the ALTER permission for the relational schema.</span></span> <span data-ttu-id="9bb7a-105">그러면 보안 주체가 관계형 스키마에서 XML 스키마 컬렉션을 만들 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9bb7a-105">Then, the principal cannot create an XML schema collection in the relational schema.</span></span> <span data-ttu-id="9bb7a-106">하지만 보안 주체는 동일 데이터베이스의 다른 관계형 스키마에서 여전히 같은 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9bb7a-106">However, the principal can still do so in other relational schemas in the same database.</span></span>  
  
-   <span data-ttu-id="9bb7a-107">데이터베이스에서 보안 주체에 대한 ALTER ANY SCHEMA 권한을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="9bb7a-107">Revoke the ALTER ANY SCHEMA permission on the database for the principal.</span></span> <span data-ttu-id="9bb7a-108">그러면 보안 주체가 데이터베이스의 어느 곳에서도 XML 스키마 컬렉션을 만들 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9bb7a-108">Then, the principal cannot create an XML schema collection anywhere in the database.</span></span>  
  
-   <span data-ttu-id="9bb7a-109">데이터베이스에서 보안 주체에 대한 CREATE XML SCHEMA COLLECTION 또는 ALTER XML SCHEMA COLLECTION 권한을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="9bb7a-109">Revoke the CREATE XML SCHEMA COLLECTION or ALTER XML SCHEMA COLLECTION permission on the database for the principal.</span></span> <span data-ttu-id="9bb7a-110">그러면 보안 주체가 데이터베이스 내에서 XML 스키마 컬렉션을 가져올 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9bb7a-110">This prevents the principal from importing an XML schema collection within the database.</span></span> <span data-ttu-id="9bb7a-111">데이터베이스에서 ALTER 또는 CONTROL 권한을 취소해도 같은 효과가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9bb7a-111">Revoking the ALTER or CONTROL permission on the database has the same effect.</span></span>  
  
## <a name="revoking-permissions-on-an-existing-xml-schema-collection-object"></a><span data-ttu-id="9bb7a-112">기존 XML 스키마 컬렉션 개체에 대한 사용 권한 취소</span><span class="sxs-lookup"><span data-stu-id="9bb7a-112">Revoking Permissions on an Existing XML Schema Collection Object</span></span>  
 <span data-ttu-id="9bb7a-113">다음은 XML 스키마 컬렉션 및 결과에서 취소할 수 있는 권한입니다.</span><span class="sxs-lookup"><span data-stu-id="9bb7a-113">Following are the permissions that can be revoked on an XML schema collection and the results:</span></span>  
  
-   <span data-ttu-id="9bb7a-114">ALTER 권한을 취소하면 보안 주체의 XML 스키마 컬렉션 콘텐츠 수정 기능이 취소됩니다.</span><span class="sxs-lookup"><span data-stu-id="9bb7a-114">Revoking the ALTER permission revokes a principal's ability to modify the content of the XML schema collection.</span></span>  
  
-   <span data-ttu-id="9bb7a-115">TAKE OWNERSHIP 권한을 취소하면 보안 주체의 XML 스키마 컬렉션 소유권 전달 기능이 취소됩니다.</span><span class="sxs-lookup"><span data-stu-id="9bb7a-115">Revoking the TAKE OWNERSHIP permission revokes a principal's ability to transfer ownership of the XML schema collection.</span></span>  
  
-   <span data-ttu-id="9bb7a-116">REFERENCES 권한을 취소하면 XML 스키마 컬렉션을 사용하여 테이블 및 뷰에 있는 xml 유형의 열 및 매개 변수를 형식화하거나 제한하는 보안 주체의 기능이 취소됩니다.</span><span class="sxs-lookup"><span data-stu-id="9bb7a-116">Revoking the REFERENCES permission revokes a principal's ability to use the XML schema collection for typing or constraining xml type columns, in tables and views, and parameters.</span></span> <span data-ttu-id="9bb7a-117">또한 다른 XML 스키마 컬렉션에서 이 스키마 컬렉션을 참조하는 권한이 취소됩니다.</span><span class="sxs-lookup"><span data-stu-id="9bb7a-117">It also revokes the permission to refer to this schema collection from other XML schema collections.</span></span>  
  
-   <span data-ttu-id="9bb7a-118">VIEW DEFINITION 권한을 취소하면 보안 주체의 XML 스키마 컬렉션의 콘텐츠를 보는 기능이 취소됩니다.</span><span class="sxs-lookup"><span data-stu-id="9bb7a-118">Revoking the VIEW DEFINITION permission revokes a principal's ability to view the contents of an XML schema collection.</span></span>  
  
-   <span data-ttu-id="9bb7a-119">EXECUTE 권한을 취소하면 XML 컬렉션에 의해 형식화되었거나 제한된 변수, 매개 변수 및 열에 있는 값을 삽입 또는 업데이트하는 보안 주체의 기능이 취소됩니다.</span><span class="sxs-lookup"><span data-stu-id="9bb7a-119">Revoking the EXECUTE permission revokes a principal's ability to insert or update values in columns, variables, and parameters that are typed or constrained by the XML collection.</span></span> <span data-ttu-id="9bb7a-120">또한 이러한 **xml** 유형의 열, 변수 또는 매개 변수를 쿼리하는 기능이 취소됩니다.</span><span class="sxs-lookup"><span data-stu-id="9bb7a-120">It also revokes the ability to query such **xml** type columns, variables, or parameters.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="9bb7a-121">예제</span><span class="sxs-lookup"><span data-stu-id="9bb7a-121">Examples</span></span>  
 <span data-ttu-id="9bb7a-122">다음 예의 시나리오에서는 XML 스키마 권한의 작동 방식을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="9bb7a-122">The scenarios in the following examples illustrate how XML schema permissions work.</span></span> <span data-ttu-id="9bb7a-123">각 예에서는 필요한 테스트 데이터베이스, 관계형 스키마 및 로그인을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="9bb7a-123">Each example creates the necessary test database, relational schemas, and logins.</span></span> <span data-ttu-id="9bb7a-124">이러한 로그인에는 필요한 XML 스키마 컬렉션 권한이 부여됩니다.</span><span class="sxs-lookup"><span data-stu-id="9bb7a-124">These logins are granted the necessary XML schema collection permissions.</span></span> <span data-ttu-id="9bb7a-125">각 예에서는 종료 시 필요한 정리를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="9bb7a-125">Each example does the necessary cleanup at the end.</span></span>  
  
### <a name="a-revoking-permissions-to-create-an-xml-schema-collection"></a><span data-ttu-id="9bb7a-126">A.</span><span class="sxs-lookup"><span data-stu-id="9bb7a-126">A.</span></span> <span data-ttu-id="9bb7a-127">XML 스키마 컬렉션을 만드는 권한 취소</span><span class="sxs-lookup"><span data-stu-id="9bb7a-127">Revoking permissions to create an XML schema collection</span></span>  
 <span data-ttu-id="9bb7a-128">이 예에서는 로그인 계정과 예제 데이터베이스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="9bb7a-128">This example creates a login and a sample database.</span></span> <span data-ttu-id="9bb7a-129">또한 데이터베이스에 관계형 스키마를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="9bb7a-129">It also adds a relational schema in the database.</span></span> <span data-ttu-id="9bb7a-130">초기에 로그인 계정에는 관계형 스키마에 대한 ALTER 권한과 XML 스키마 컬렉션을 만들기 위한 다른 필수 권한이 부여됩니다.</span><span class="sxs-lookup"><span data-stu-id="9bb7a-130">Initially, the login is granted ALTER permission on both relational schemas and other necessary permissions to create XML schema collections.</span></span> <span data-ttu-id="9bb7a-131">이 예에서는 데이터베이스에 있는 관계형 스키마 중 하나에 대한 ALTER 권한을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="9bb7a-131">The example then revokes the ALTER permission on one of the relational schemas in the database.</span></span> <span data-ttu-id="9bb7a-132">이렇게 하면 로그인 계정이 XML 스키마 컬렉션을 만들 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9bb7a-132">This prevents the login from creating an XML schema collection.</span></span>  
  
```  
setuser  
go  
create login TestLogin1 with password='SQLSvrPwd1'  
go  
create database SampleDBForSchemaPermissions  
go  
use SampleDBForSchemaPermissions  
go  
-- Create another relational schema in the db (in addition to dbo schema)  
CREATE SCHEMA myOtherDBSchema  
go  
CREATE USER TestLogin1  
go  
-- For TestLogin1 to create/import XML schema collection, following  
-- permission needed  
-- CREATE XML SCHEMA is a database level permission  
GRANT CREATE XML SCHEMA COLLECTION TO TestLogin1  
go  
GRANT ALTER ON SCHEMA::myOtherDBSchema TO TestLogin1  
go  
GRANT ALTER ON SCHEMA::dbo TO TestLogin1  
go  
-- Now TestLogin1 can import an XML schema collection in both relational schemas.  
setuser 'TestLogin1'  
go  
CREATE XML SCHEMA COLLECTION dbo.myTestSchemaCollection AS '<?xml version="1.0" encoding="UTF-8" ?>  
  
<xsd:schema targetNamespace="http://schemas.adventure-works.com/Additional/ContactInfo"   
            xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
elementFormDefault="qualified">  
<xsd:element name="telephone" type="xsd:string" />  
</xsd:schema>'  
go  
-- TestLogin1 can create XML schema collection in myOtherDBSchema relational schema  
CREATE XML SCHEMA COLLECTION myOtherDBSchema.myTestSchemaCollection AS '<?xml version="1.0" encoding="UTF-8" ?>  
  
<xsd:schema targetNamespace="http://schemas.adventure-works.com/Additional/ContactInfo"   
            xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
elementFormDefault="qualified">  
<xsd:element name="telephone" type="xsd:string" />  
</xsd:schema>'  
go  
-- Let us drop XML schema collections from both relational schemas  
DROP XML SCHEMA COLLECTION myOtherDBSchema.myTestSchemaCollection  
go  
DROP XML SCHEMA COLLECTION dbo.myTestSchemaCollection  
go  
-- now REVOKE permission from TestLogin1 to alter myOtherDBSchema  
setuser  
go  
REVOKE ALTER ON SCHEMA::myOtherDBSchema FROM TestLogin1  
go  
-- now TestLogin1 cannot create xml schema collection in myOtherDBSchema  
setuser 'TestLogin1'  
go  
CREATE XML SCHEMA COLLECTION myOtherDBSchema.myTestSchemaCollection AS '<?xml version="1.0" encoding="UTF-8" ?>  
<xsd:schema targetNamespace="http://schemas.adventure-works.com/Additional/ContactInfo"   
            xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
elementFormDefault="qualified">  
<xsd:element name="telephone" type="xsd:string" />  
</xsd:schema>'  
go  
  
-- TestLogin1 can still create XML schema collections in dbo  
-- It cannot create XML schema collections anywhere in the database  
-- if we REVOKE CREATE XML SCHEMA COLLECTION permission  
SETUSER  
go  
REVOKE CREATE XML SCHEMA COLLECTION FROM TestLogin1  
go  
  
setuser 'TestLogin1'  
go  
-- the following now should fail  
CREATE XML SCHEMA COLLECTION dbo.myTestSchemaCollection AS '<?xml version="1.0" encoding="UTF-8" ?>  
<xsd:schema targetNamespace="http://schemas.adventure-works.com/Additional/ContactInfo"   
            xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
elementFormDefault="qualified">  
<xsd:element name="telephone" type="xsd:string" />  
</xsd:schema>'  
go  
  
-- Final cleanup  
SETUSER  
go  
USE master  
go  
DROP DATABASE SampleDBForSchemaPermissions  
go  
DROP LOGIN TestLogin1  
Go  
```  
  
## <a name="see-also"></a><span data-ttu-id="9bb7a-133">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9bb7a-133">See Also</span></span>  
 <span data-ttu-id="9bb7a-134">[XML 데이터&#40;SQL Server&#41;](xml-data-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="9bb7a-134">[XML Data &#40;SQL Server&#41;](xml-data-sql-server.md) </span></span>  
 <span data-ttu-id="9bb7a-135">[형식화된 XML과 형식화되지 않은 XML 비교](compare-typed-xml-to-untyped-xml.md) </span><span class="sxs-lookup"><span data-stu-id="9bb7a-135">[Compare Typed XML to Untyped XML](compare-typed-xml-to-untyped-xml.md) </span></span>  
 <span data-ttu-id="9bb7a-136">[XML 스키마 컬렉션&#40;SQL Server&#41;](xml-schema-collections-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="9bb7a-136">[XML Schema Collections &#40;SQL Server&#41;](xml-schema-collections-sql-server.md) </span></span>  
 [<span data-ttu-id="9bb7a-137">서버의 XML 스키마 컬렉션에 대한 요구 사항 및 제한 사항</span><span class="sxs-lookup"><span data-stu-id="9bb7a-137">Requirements and Limitations for XML Schema Collections on the Server</span></span>](requirements-and-limitations-for-xml-schema-collections-on-the-server.md)  
  
  
