---
title: XML 스키마 컬렉션에 대한 사용 권한 거부 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- denying permissions [SQL Server], XML server collections
ms.assetid: e2b300b0-e734-4c43-a4da-c78e6e5d4fba
author: rothja
ms.author: jroth
ms.openlocfilehash: 0791a9bd9c7f6b323886a38bed27bea84940770d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646228"
---
# <a name="deny-permissions-on-an-xml-schema-collection"></a><span data-ttu-id="bce3e-102">XML 스키마 컬렉션에 대한 사용 권한 거부</span><span class="sxs-lookup"><span data-stu-id="bce3e-102">Deny Permissions on an XML Schema Collection</span></span>
  <span data-ttu-id="bce3e-103">새 XML 스키마 컬렉션을 만들거나 기존 스키마 컬렉션을 사용할 권한을 거부할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bce3e-103">Permission can be denied to either create a new XML schema collection or use an existing one.</span></span>  
  
## <a name="denying-permission-to-create-an-xml-schema-collection"></a><span data-ttu-id="bce3e-104">XML 스키마 컬렉션을 만드는 권한 거부</span><span class="sxs-lookup"><span data-stu-id="bce3e-104">Denying Permission to Create an XML Schema Collection</span></span>  
 <span data-ttu-id="bce3e-105">다음과 같은 방법으로 XML 스키마 컬렉션을 만드는 권한을 거부할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bce3e-105">You can deny permission to create an XML schema collection in the following ways:</span></span>  
  
-   <span data-ttu-id="bce3e-106">관계형 스키마에 대한 ALTER 권한을 거부합니다.</span><span class="sxs-lookup"><span data-stu-id="bce3e-106">Deny ALTER permission on the relational schema.</span></span>  
  
-   <span data-ttu-id="bce3e-107">관계형 스키마 및 포함된 모든 개체에 대한 모든 사용 권한을 거부하려면 관계형 스키마에 대한 CONTROL 권한을 거부합니다.</span><span class="sxs-lookup"><span data-stu-id="bce3e-107">Deny CONTROL on the relational schema to deny all permissions on the relational schema and on all the contained objects.</span></span>  
  
-   <span data-ttu-id="bce3e-108">데이터베이스에 대한 ALTER ANY SCHEMA를 거부합니다.</span><span class="sxs-lookup"><span data-stu-id="bce3e-108">Deny ALTER ANY SCHEMA on the database.</span></span> <span data-ttu-id="bce3e-109">이 경우 보안 주체가 데이터베이스의 어떤 위치에도 XML 스키마 컬렉션을 만들 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="bce3e-109">In this case, the principal cannot create an XML schema collection anywhere in the database.</span></span> <span data-ttu-id="bce3e-110">데이터베이스에 대한 ALTER 또는 CONTROL 권한을 거부하면 데이터베이스의 모든 개체에 대한 모든 사용 권한이 거부됩니다.</span><span class="sxs-lookup"><span data-stu-id="bce3e-110">Note also that denying ALTER or CONTROL permission on the database denies all permissions on all objects in the database.</span></span>  
  
## <a name="denying-permissions-on-an-xml-schema-collection-object"></a><span data-ttu-id="bce3e-111">XML 스키마 컬렉션 개체에 대한 사용 권한 거부</span><span class="sxs-lookup"><span data-stu-id="bce3e-111">Denying Permissions on an XML Schema Collection Object</span></span>  
 <span data-ttu-id="bce3e-112">다음은 기존 XML 스키마 컬렉션 및 결과에 대해 거부할 수 있는 사용 권한입니다.</span><span class="sxs-lookup"><span data-stu-id="bce3e-112">Following are the permission that can be denied on an existing XML schema collection and the results:</span></span>  
  
-   <span data-ttu-id="bce3e-113">ALTER 권한을 거부하면 XML 스키마 컬렉션의 내용을 수정하는 보안 주체의 권한이 거부됩니다.</span><span class="sxs-lookup"><span data-stu-id="bce3e-113">Denying the ALTER permission denies the principal the ability to modify the contents of the XML schema collection.</span></span>  
  
-   <span data-ttu-id="bce3e-114">CONTROL 권한을 거부하면 XML 스키마 컬렉션에 대한 작업을 수행하는 보안 주체의 권한이 거부됩니다.</span><span class="sxs-lookup"><span data-stu-id="bce3e-114">Denying the CONTROL permission denies the principal the ability to perform any operation on the XML schema collection.</span></span>  
  
-   <span data-ttu-id="bce3e-115">REFERENCES 권한을 거부하면 XML 스키마 컬렉션을 사용하여 xml 유형 열 및 매개 변수를 입력하거나 제한하는 보안 주체의 권한이 거부됩니다.</span><span class="sxs-lookup"><span data-stu-id="bce3e-115">Denying the REFERENCES permission denies the principal the ability to type or constrain xml type columns and parameters using the XML schema collection.</span></span> <span data-ttu-id="bce3e-116">또한 다른 XML 스키마 컬렉션에서 이 XML 스키마 컬렉션을 참조하는 보안 주체의 권한이 거부됩니다.</span><span class="sxs-lookup"><span data-stu-id="bce3e-116">It also denies the principal the ability to refer to this XML schema collection from other XML schema collections.</span></span>  
  
-   <span data-ttu-id="bce3e-117">VIEW DEFINITION 권한을 거부하면 XML 스키마 컬렉션의 내용을 보는 보안 주체의 권한이 거부됩니다.</span><span class="sxs-lookup"><span data-stu-id="bce3e-117">Denying the VIEW DEFINITION permission denies the principal the ability to view the contents of an XML schema collection.</span></span>  
  
-   <span data-ttu-id="bce3e-118">EXECUTE 권한을 거부하면 XML 스키마 컬렉션에 의해 입력되거나 제한되는 열, 변수 및 매개 변수에 값을 삽입하거나 업데이트하는 보안 주체의 권한이 거부됩니다.</span><span class="sxs-lookup"><span data-stu-id="bce3e-118">Denying the EXECUTE permission denies the principal the ability to insert or update the values in columns, variables, and parameters that are typed or constrained by the XML schema collection.</span></span> <span data-ttu-id="bce3e-119">또한 같은 xml 유형 열 및 변수의 값을 쿼리하는 보안 주체의 권한이 거부됩니다.</span><span class="sxs-lookup"><span data-stu-id="bce3e-119">It also denies the principal the ability to query the values in those same xml type columns and variables.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="bce3e-120">예</span><span class="sxs-lookup"><span data-stu-id="bce3e-120">Examples</span></span>  
 <span data-ttu-id="bce3e-121">다음 예의 시나리오에서는 XML 스키마 권한의 작동 방식을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="bce3e-121">The scenarios in the following examples show how XML schema permissions work.</span></span> <span data-ttu-id="bce3e-122">각 예에서는 필요한 테스트 데이터베이스, 관계형 스키마 및 로그인을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="bce3e-122">Each example creates the necessary test database, relational schemas, and logins.</span></span> <span data-ttu-id="bce3e-123">이러한 로그인에는 필요한 XML 스키마 컬렉션 권한이 부여됩니다.</span><span class="sxs-lookup"><span data-stu-id="bce3e-123">These logins are granted the necessary XML schema collection permissions.</span></span> <span data-ttu-id="bce3e-124">각 예에서는 종료 시 필요한 정리를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="bce3e-124">Each example does the necessary cleanup at the end.</span></span>  
  
### <a name="a-preventing-a-user-from-creating-an-xml-schema-collection"></a><span data-ttu-id="bce3e-125">A.</span><span class="sxs-lookup"><span data-stu-id="bce3e-125">A.</span></span> <span data-ttu-id="bce3e-126">사용자가 XML 스키마 컬렉션을 만드는 것을 방지</span><span class="sxs-lookup"><span data-stu-id="bce3e-126">Preventing a user from creating an XML schema collection</span></span>  
 <span data-ttu-id="bce3e-127">사용자가 XML 스키마 컬렉션을 만들 수 없게 하는 방법 중 하나는 관계형 스키마에 대한 ALTER 권한을 거부하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="bce3e-127">One of the ways to prevent a user from creating an XML schema collection is by denying the ALTER permission on a relational schema.</span></span> <span data-ttu-id="bce3e-128">이는 다음 예에서 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bce3e-128">This is shown in the following example.</span></span>  
  
 <span data-ttu-id="bce3e-129">이 예에서는 `TestLogin1`이라는 사용자와 데이터베이스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="bce3e-129">The example creates a user, `TestLogin1`, and a database.</span></span> <span data-ttu-id="bce3e-130">또한 데이터베이스에 `dbo` 스키마 외에 관계형 스키마를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="bce3e-130">It also creates a relational schema, in addition to the `dbo` schema, in the database.</span></span> <span data-ttu-id="bce3e-131">처음에는 사용자가 `CREATE XML SCHEMA` 권한을 사용하여 데이터베이스의 모든 위치에 스키마 컬렉션을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bce3e-131">Initially, the `CREATE XML SCHEMA` permission allows the user to create a schema collection anywhere in the database.</span></span> <span data-ttu-id="bce3e-132">그런 다음 관계형 스키마 중 하나에 대한 사용자의 `ALTER` 권한을 거부합니다.</span><span class="sxs-lookup"><span data-stu-id="bce3e-132">The example then denies `ALTER` permission to the user on one of the relational schemas.</span></span> <span data-ttu-id="bce3e-133">이렇게 하면 사용자가 해당 관계형 스키마에 XML 스키마 컬렉션을 만들 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="bce3e-133">This prevents the user from creating an XML schema collection in that relational schema.</span></span>  
  
```  
CREATE LOGIN TestLogin1 WITH password='SQLSvrPwd1'  
GO  
CREATE DATABASE SampleDBForSchemaPermissions  
GO  
USE SampleDBForSchemaPermissions  
GO  
-- Create another relational schema in the database.  
CREATE SCHEMA myOtherDBSchema  
GO  
CREATE USER TestLogin1  
GO  
-- For TestLogin1 to create/import XML schema collection, following  
-- permission needed.  
-- Database-level permissions  
GRANT CREATE XML SCHEMA COLLECTION TO TestLogin1  
GO  
GRANT ALTER ANY SCHEMA TO TestLogin1  
GO  
-- Now TestLogin1 can import an XML schema collection.  
SETUSER 'TestLogin1'  
GO  
CREATE XML SCHEMA COLLECTION myOtherDBSchema.myTestSchemaCollection AS '<?xml version="1.0" encoding="UTF-8" ?>  
<xsd:schema targetNamespace="http://schemas.adventure-works.com/Additional/ContactInfo"   
            xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
elementFormDefault="qualified">  
<xsd:element name="telephone" type="xsd:string" />  
</xsd:schema>'  
GO  
DROP XML SCHEMA COLLECTION myOtherDBSchema.myTestSchemaCollection  
GO  
-- Now deny permission from TestLogin1 to alter myOtherDBSchema.  
setuser  
GO  
DENY ALTER ON SCHEMA::myOtherDBSchema TO TestLogin1  
GO  
-- Now TestLogin1 cannot create xml schema collection.  
SETUSER 'TestLogin1'  
GO  
CREATE XML SCHEMA COLLECTION myOtherDBSchema.myTestSchemaCollection AS '<?xml version="1.0" encoding="UTF-8" ?>  
<xsd:schema targetNamespace="http://schemas.adventure-works.com/Additional/ContactInfo"   
            xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
elementFormDefault="qualified">  
<xsd:element name="telephone" type="xsd:string" />  
</xsd:schema>'  
GO  
-- Final cleanup  
SETUSER  
GO  
USE master  
GO  
DROP DATABASE SampleDBForSchemaPermissions  
GO  
DROP LOGIN TestLogin1  
GO  
```  
  
### <a name="b-denying-permissions-on-an-xml-schema-collection"></a><span data-ttu-id="bce3e-134">B.</span><span class="sxs-lookup"><span data-stu-id="bce3e-134">B.</span></span> <span data-ttu-id="bce3e-135">XML 스키마 컬렉션에 대한 사용 권한 거부</span><span class="sxs-lookup"><span data-stu-id="bce3e-135">Denying permissions on an XML schema collection</span></span>  
 <span data-ttu-id="bce3e-136">다음 예에서는 로그인에 대해 기존 XML 스키마 컬렉션에 대한 특정 권한을 거부할 수 있는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="bce3e-136">The following example shows how a specific permission on an existing XML schema collection can be denied to a login.</span></span> <span data-ttu-id="bce3e-137">이 예에서 테스트 로그인은 기존 XML 스키마 컬렉션에 대한 REFERENCES 권한이 거부됩니다.</span><span class="sxs-lookup"><span data-stu-id="bce3e-137">In this example, a test login is denied REFERENCES permission on an existing XML schema collection.</span></span>  
  
 <span data-ttu-id="bce3e-138">이 예에서는 `TestLogin1`이라는 사용자와 데이터베이스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="bce3e-138">The example creates a user, `TestLogin1`, and a database.</span></span> <span data-ttu-id="bce3e-139">또한 데이터베이스에 `dbo` 스키마 외에 관계형 스키마를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="bce3e-139">It also creates a relational schema, in addition to the `dbo` schema, in the database.</span></span> <span data-ttu-id="bce3e-140">처음에는 사용자가 `CREATE XML SCHEMA` 권한을 사용하여 데이터베이스의 모든 위치에 스키마 컬렉션을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bce3e-140">Initially, the `CREATE XML SCHEMA` permission allows the user to create a schema collection anywhere in the database.</span></span>  
  
 <span data-ttu-id="bce3e-141">XML 스키마 컬렉션에 대한 `REFERENCES` 권한을 통해 `TestLogin1` 은 테이블에 `xml` 유형의 열을 만들 때 스키마를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bce3e-141">The `REFERENCES` permission on the XML schema collection lets `TestLogin1` use the schema in creating a typed `xml` column in a table.</span></span> <span data-ttu-id="bce3e-142">XML 스키마 컬렉션에 대한 `REFERENCES` 권한이 거부되면 `TestLogin1` 은 XML 스키마 컬렉션을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="bce3e-142">If the `REFERENCES` permission on the XML schema collection is denied, it prevents the `TestLogin1` from using the XML schema collection.</span></span>  
  
```  
CREATE LOGIN TestLogin1 WITH password='SQLSvrPwd1'  
GO  
CREATE DATABASE SampleDBForSchemaPermissions  
GO  
USE SampleDBForSchemaPermissions  
GO  
-- Create another relational schema in the database.  
CREATE SCHEMA myOtherDBSchema  
GO  
CREATE USER TestLogin1  
GO  
-- For TestLogin1 to create/import XML schema collection, the following  
-- permission is required.  
-- Database-level permissions  
GRANT CREATE XML SCHEMA COLLECTION TO TestLogin1  
GO  
GRANT ALTER ANY SCHEMA TO TestLogin1  
GO  
-- Now TestLogin1 can import an XML schema collection.  
SETUSER 'TestLogin1'  
GO  
CREATE XML SCHEMA COLLECTION myOtherDBSchema.myTestSchemaCollection AS '<?xml version="1.0" encoding="UTF-8" ?>  
<xsd:schema targetNamespace="http://schemas.adventure-works.com/Additional/ContactInfo"   
            xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
elementFormDefault="qualified">  
<xsd:element name="telephone" type="xsd:string" />  
</xsd:schema>'  
GO  
-- Grant permission to TestLogin1 to create a table and reference the XML schema collection.  
SETUSER  
GO  
GRANT CREATE TABLE TO TestLogin1  
GO  
-- The user also needs REFERENCES permission to use the XML schema collection  
-- to create a typed XML column (REFERENCES permission on the schema   
-- collection is not needed).  
GRANT REFERENCES ON XML SCHEMA COLLECTION::myOtherDBSchema.myTestSchemaCollection   
TO TestLogin1  
GO  
  
--TestLogin1 can use the schema.  
CREATE TABLE T(i int, x xml (myOtherDBSchema.myTestSchemaCollection))  
GO  
-- Drop the table.  
DROP TABLE T  
GO  
-- Now deny REFERENCES permission to TestLogin1 on the schema created previously.  
SETUSER  
GO  
DENY REFERENCES ON XML SCHEMA COLLECTION::myOtherDBSchema.myTestSchemaCollection TO TestLogin1  
  
GO  
-- Now TestLogin1 cannot create xml schema collection  
SETUSER 'TestLogin1'  
GO  
-- Following statement fails. TestLogin1 does not have REFERENCES   
-- permission on the XML schema collection.  
CREATE TABLE T(i int, x xml (myOtherDBSchema.myTestSchemaCollection))  
GO  
  
-- Final cleanup  
SETUSER  
GO  
USE master  
GO  
DROP DATABASE SampleDBForSchemaPermissions  
GO  
DROP LOGIN TestLogin1  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="bce3e-143">참고 항목</span><span class="sxs-lookup"><span data-stu-id="bce3e-143">See Also</span></span>  
 <span data-ttu-id="bce3e-144">[형식화된 XML과 형식화되지 않은 XML 비교](compare-typed-xml-to-untyped-xml.md) </span><span class="sxs-lookup"><span data-stu-id="bce3e-144">[Compare Typed XML to Untyped XML](compare-typed-xml-to-untyped-xml.md) </span></span>  
 <span data-ttu-id="bce3e-145">[XML 스키마 컬렉션&#40;SQL Server&#41;](xml-schema-collections-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="bce3e-145">[XML Schema Collections &#40;SQL Server&#41;](xml-schema-collections-sql-server.md) </span></span>  
 <span data-ttu-id="bce3e-146">[서버의 XML 스키마 컬렉션에 대한 요구 사항 및 제한 사항](requirements-and-limitations-for-xml-schema-collections-on-the-server.md) </span><span class="sxs-lookup"><span data-stu-id="bce3e-146">[Requirements and Limitations for XML Schema Collections on the Server](requirements-and-limitations-for-xml-schema-collections-on-the-server.md) </span></span>  
 <span data-ttu-id="bce3e-147">[DENY 개체 사용 권한&#40;Transact-SQL&#41;](/sql/t-sql/statements/deny-object-permissions-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="bce3e-147">[DENY Object Permissions &#40;Transact-SQL&#41;](/sql/t-sql/statements/deny-object-permissions-transact-sql) </span></span>  
 <span data-ttu-id="bce3e-148">[GRANT 개체 사용 권한&#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-object-permissions-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="bce3e-148">[GRANT Object Permissions &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-object-permissions-transact-sql) </span></span>  
 [<span data-ttu-id="bce3e-149">XML 데이터&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="bce3e-149">XML Data &#40;SQL Server&#41;</span></span>](xml-data-sql-server.md)  
  
  
