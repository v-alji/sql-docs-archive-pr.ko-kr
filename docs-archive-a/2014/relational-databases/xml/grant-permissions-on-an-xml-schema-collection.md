---
title: XML 스키마 컬렉션에 대한 사용 권한 부여 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- granting permissions [SQL Server], XML schema collections
- ALTER permission
ms.assetid: ffbb829c-3b8f-4e5d-97d9-ab4059aab0db
author: rothja
ms.author: jroth
ms.openlocfilehash: 2dc6384acb2f079245c80923e683ebe2c03d2562
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87729163"
---
# <a name="grant-permissions-on-an-xml-schema-collection"></a><span data-ttu-id="98608-102">XML 스키마 컬렉션에 대한 사용 권한 부여</span><span class="sxs-lookup"><span data-stu-id="98608-102">Grant Permissions on an XML Schema Collection</span></span>
  <span data-ttu-id="98608-103">XML 스키마 컬렉션을 만들 권한 및 XML 스키마 컬렉션 개체에 대한 권한을 부여할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="98608-103">You can grant permissions to create an XML schema collection and also grant permissions on an XML schema collection object.</span></span>  
  
## <a name="granting-permission-to-create-an-xml-schema-collection"></a><span data-ttu-id="98608-104">XML 스키마 컬렉션을 만들 권한 부여</span><span class="sxs-lookup"><span data-stu-id="98608-104">Granting Permission to Create an XML Schema Collection</span></span>  
 <span data-ttu-id="98608-105">XML 스키마 컬렉션을 만들려면 다음 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="98608-105">To create an XML schema collection, the following permissions are required:</span></span>  
  
-   <span data-ttu-id="98608-106">보안 주체는 데이터베이스 수준에서 CREATE XML SCHEMA COLLECTION 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="98608-106">The principal requires CREATE XML SCHEMA COLLECTION permission at the database-level.</span></span>  
  
-   <span data-ttu-id="98608-107">XML 스키마 컬렉션이 관계형 스키마 범위이므로 보안 주체는 관계형 스키마에 대한 ALTER 권한도 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="98608-107">Because the XML schema collections are relational schema-scoped, the principal must also have ALTER permission on the relational schema.</span></span>  
  
 <span data-ttu-id="98608-108">다음 권한을 사용하여 보안 주체는 서버의 데이터베이스에서 관계형 스키마에 XML 스키마 컬렉션을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="98608-108">The following permissions let a principal create an XML schema collection in a relational schema in a database on a server:</span></span>  
  
-   <span data-ttu-id="98608-109">서버에 대한 CONTROL 권한</span><span class="sxs-lookup"><span data-stu-id="98608-109">CONTROL permission on the server</span></span>  
  
-   <span data-ttu-id="98608-110">서버에 대한 ALTER ANY DATABASE 권한</span><span class="sxs-lookup"><span data-stu-id="98608-110">ALTER ANY DATABASE permission on the server</span></span>  
  
-   <span data-ttu-id="98608-111">데이터베이스에 대한 ALTER 권한</span><span class="sxs-lookup"><span data-stu-id="98608-111">ALTER permission on the database</span></span>  
  
-   <span data-ttu-id="98608-112">데이터베이스의 CONTROL 권한</span><span class="sxs-lookup"><span data-stu-id="98608-112">CONTROL permission in the database</span></span>  
  
-   <span data-ttu-id="98608-113">데이터베이스의 ALTER ANY SCHEMA 권한 및 CREATE XML SCHEMA COLLECTION 권한</span><span class="sxs-lookup"><span data-stu-id="98608-113">ALTER ANY SCHEMA permission and CREATE XML SCHEMA COLLECTION permission in the database</span></span>  
  
-   <span data-ttu-id="98608-114">관계형 스키마에 대한 ALTER 또는 CONTROL 권한 및 데이터베이스의 CREATE XML SCHEMA COLLECTION 권한</span><span class="sxs-lookup"><span data-stu-id="98608-114">ALTER or CONTROL permission on the relational schema and CREATE XML SCHEMA COLLECTION permission in the database</span></span>  
  
 <span data-ttu-id="98608-115">권한의 마지막 메서드는 다음 예에서 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="98608-115">This last method of permissions is used in the following example.</span></span>  
  
 <span data-ttu-id="98608-116">관계형 스키마의 소유자는 해당 스키마에 만들어진 XML 스키마 컬렉션의 소유자가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="98608-116">The owner of the relational schema becomes the owner of the XML schema collection created in that schema.</span></span> <span data-ttu-id="98608-117">이 소유자에게는 XML 스키마 컬렉션에 대한 모든 권한이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="98608-117">This owner then has full control over the XML schema collection.</span></span> <span data-ttu-id="98608-118">따라서 이 소유자는 XML 스키마 컬렉션을 수정하거나 xml 열을 형식화하거나 XML 스키마 컬렉션을 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="98608-118">Therefore, this owner can modify the XML schema collection, type an xml column, or drop the XML schema collection.</span></span>  
  
## <a name="granting-permissions-on-an-xml-schema-collection-object"></a><span data-ttu-id="98608-119">XML 스키마 컬렉션 개체에 대한 권한 부여</span><span class="sxs-lookup"><span data-stu-id="98608-119">Granting Permissions on an XML Schema Collection Object</span></span>  
 <span data-ttu-id="98608-120">XML 스키마 컬렉션에는 다음 권한이 허용됩니다.</span><span class="sxs-lookup"><span data-stu-id="98608-120">The following permissions are allowed on the XML schema collection:</span></span>  
  
-   <span data-ttu-id="98608-121">ALTER XML SCHEMA COLLECTION 문을 사용하여 기존 XML 스키마 컬렉션의 내용을 수정할 때는 ALTER 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="98608-121">The ALTER permission is required when modifying contents of an existing XML schema collection by using the ALTER XML SCHEMA COLLECTION statement.</span></span>  
  
-   <span data-ttu-id="98608-122">CONTROL 권한을 사용하면 사용자는 XML 스키마 컬렉션에서 모든 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="98608-122">The CONTROL permission lets a user perform any operation on the XML schema collection.</span></span>  
  
-   <span data-ttu-id="98608-123">한 보안 주체에서 다른 보안 주체로 XML 스키마 컬렉션의 소유권을 이전하는 데는 TAKE OWNERSHIP 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="98608-123">The TAKE OWNERSHIP permission is required to transfer ownership of the XML schema collection from one principal to another.</span></span>  
  
-   <span data-ttu-id="98608-124">REFERENCES 권한은 보안 주체가 테이블, 뷰 및 매개 변수에서 XML 스키마 컬렉션을 사용하여 `xml` 유형 열을 형식화하거나 제약하도록 권한을 부여합니다.</span><span class="sxs-lookup"><span data-stu-id="98608-124">The REFERENCES permission authorizes the principal to use the XML schema collection to type or constrain `xml` type columns, in tables and views and parameters.</span></span> <span data-ttu-id="98608-125">REFERENCES 권한은 하나의 XML 스키마 컬렉션이 다른 컬렉션을 참조할 때도 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="98608-125">The REFERENCES permission is also required when one XML schema collection refers to another.</span></span>  
  
-   <span data-ttu-id="98608-126">보안 주체가 컬렉션에 대해 ALTER, REFERENCES 또는 CONTROL 권한 중 하나를 가진 경우 VIEW DEFINITION 권한을 사용하면 보안 주체가 XML_SCHEMA_NAMESPACE 또는 카탈로그 뷰를 통해 XML 스키마 컬렉션의 내용을 쿼리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="98608-126">The VIEW DEFINITION permission allows the principal to query the contents of an XML schema collection either through XML_SCHEMA_NAMESPACE or through the catalog views, provided this principal also has one of the ALTER, REFERENCES, or CONTROL permissions on the collection.</span></span>  
  
-   <span data-ttu-id="98608-127">`xml` 유형 열, 변수 및 매개 변수를 형식화하거나 제약하는 XML 스키마 컬렉션에 대해 보안 주체가 삽입하거나 업데이트한 값의 유효성을 검사하려면 EXECUTE 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="98608-127">The EXECUTE permission is required to validate values inserted or updated by the principal against the XML schema collection that is typing or constraining the `xml` type columns, variables, and parameters.</span></span> <span data-ttu-id="98608-128">이 권한은 이러한 열 및 변수에 저장된 XML을 쿼리할 때도 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="98608-128">You also need this permission when you are querying the XML stored in these columns and variables.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="98608-129">예제</span><span class="sxs-lookup"><span data-stu-id="98608-129">Examples</span></span>  
 <span data-ttu-id="98608-130">다음 예의 시나리오에서는 XML 스키마 권한의 작동 방식을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="98608-130">The scenarios in the following examples illustrate how XML schema permissions work.</span></span> <span data-ttu-id="98608-131">각 예에서는 필요한 테스트 데이터베이스, 관계형 스키마 및 로그인을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="98608-131">Each example creates the necessary test database, relational schemas, and logins.</span></span> <span data-ttu-id="98608-132">이러한 로그인에는 필요한 XML 스키마 컬렉션 권한이 부여됩니다.</span><span class="sxs-lookup"><span data-stu-id="98608-132">These logins are granted the necessary XML schema collection permissions.</span></span> <span data-ttu-id="98608-133">각 예에서는 종료 시 필요한 정리를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="98608-133">Each example does the necessary clean up at the end.</span></span>  
  
### <a name="a-granting-permissions-to-create-an-xml-schema-collection"></a><span data-ttu-id="98608-134">A.</span><span class="sxs-lookup"><span data-stu-id="98608-134">A.</span></span> <span data-ttu-id="98608-135">XML 스키마 컬렉션을 만들 권한 부여</span><span class="sxs-lookup"><span data-stu-id="98608-135">Granting permissions to create an XML schema collection</span></span>  
 <span data-ttu-id="98608-136">다음 예에서는 보안 주체가 XML 스키마 컬렉션을 만들 수 있도록 권한을 부여하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="98608-136">The following example shows how to grant permissions so that a principal can create an XML schema collection.</span></span> <span data-ttu-id="98608-137">이 예에서는 `TestLogin1`이라는 테스트 사용자와 예제 데이터베이스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="98608-137">The example creates a sample database and a test user, `TestLogin1`.</span></span> <span data-ttu-id="98608-138">`TestLogin1` 은 관계형 스키마에 대해 `ALTER` 권한을 부여받고 데이터베이스에 대해 `CREATE XML SCHEMA COLLECTION` 권한을 부여받습니다.</span><span class="sxs-lookup"><span data-stu-id="98608-138">`TestLogin1` is then given `ALTER` permission on the relational schema and given `CREATE XML SCHEMA COLLECTION` permission on the database.</span></span> <span data-ttu-id="98608-139">이러한 권한을 통해 `TestLogin1` 은 예제 XML 스키마 컬렉션을 성공적으로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="98608-139">With these permissions, `TestLogin1` succeeds in creating a sample XML schema collection.</span></span>  
  
```  
SETUSER  
GO  
USE master  
GO  
CREATE LOGIN TestLogin1 WITH password='SQLSvrPwd1'  
GO  
CREATE DATABASE SampleDBForSchemaPermissions  
GO  
USE SampleDBForSchemaPermissions  
GO  
CREATE USER TestLogin1  
GO  
-- User must have ALTER permission on the relational schema in the database.  
GRANT ALTER ON SCHEMA::dbo TO TestLogin1  
GO  
-- User also must have permission to create XML schema collections in the database.  
GRANT CREATE XML SCHEMA COLLECTION   
TO TestLogin1  
GO  
-- Execute CREATE XML SCHEMA COLLECTION.  
SETUSER 'TestLogin1'  
GO  
CREATE XML SCHEMA COLLECTION myTestSchemaCollection AS '<?xml version="1.0" encoding="UTF-8" ?>  
<xsd:schema targetNamespace="http://schemas.adventure-works.com/Additional/ContactInfo"   
            xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
elementFormDefault="qualified">  
<xsd:element name="AdditionalContactInfo" >  
  <xsd:complexType mixed="true" >  
    <xsd:sequence>  
      <xsd:any processContents="strict"    
               namespace="http://schemas.adventure-works.com/Contact/Record   
                          http://schemas.adventure-works.com/AdditionalContactTypes"  
               minOccurs="0" maxOccurs="unbounded" />  
    </xsd:sequence>  
  </xsd:complexType>  
</xsd:element>  
<xsd:element name="root" type="xsd:byte"/>  
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
  
### <a name="b-granting-permission-to-use-an-existing-xml-schema-collection"></a><span data-ttu-id="98608-140">B.</span><span class="sxs-lookup"><span data-stu-id="98608-140">B.</span></span> <span data-ttu-id="98608-141">기존 XML 스키마 컬렉션을 사용할 권한 부여</span><span class="sxs-lookup"><span data-stu-id="98608-141">Granting permission to use an existing XML schema collection</span></span>  
 <span data-ttu-id="98608-142">다음 예에서는 XML 스키마 컬렉션에 대한 권한 모델을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="98608-142">The following example further shows the permission model for the XML schema collection.</span></span> <span data-ttu-id="98608-143">XML 스키마 컬렉션을 만들고 사용하는 데 다른 권한이 필요한지 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="98608-143">The example shows how different permissions are required to create and use the XML schema collection.</span></span>  
  
 <span data-ttu-id="98608-144">이 예에서는 테스트 데이터베이스와 `TestLogin1`이라는 로그인을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="98608-144">The example creates a test database and a login, `TestLogin1`.</span></span> <span data-ttu-id="98608-145">`TestLogin1` 은 데이터베이스에 XML 스키마 컬렉션을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="98608-145">`TestLogin1` creates an XML schema collection in the database.</span></span> <span data-ttu-id="98608-146">이 로그인은 테이블을 만들고 XML 스키마 컬렉션을 사용하여 형식화된 xml 열을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="98608-146">The login then creates a table and uses the XML schema collection to create a typed xml column.</span></span> <span data-ttu-id="98608-147">그런 다음 데이터를 삽입하고 쿼리합니다.</span><span class="sxs-lookup"><span data-stu-id="98608-147">The user then inserts data and queries it.</span></span> <span data-ttu-id="98608-148">이러한 모든 단계에는 코드에 표시된 대로 필요한 스키마 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="98608-148">All these steps require the necessary schema permissions, as shown in the code.</span></span>  
  
```  
SETUSER  
GO  
USE master  
GO  
CREATE LOGIN TestLogin1 WITH password='SQLSvrPwd1'  
GO  
CREATE DATABASE SampleDBForSchemaPermissions  
GO  
USE SampleDBForSchemaPermissions  
GO  
CREATE USER TestLogin1  
GO  
-- Grant permission to the user.  
SETUSER  
GO  
-- User must have ALTER permission on the relational schema in the database.  
GRANT ALTER ON SCHEMA::dbo TO TestLogin1  
GO  
-- User also must have permission to create XML schema collections in the database.  
GRANT CREATE XML SCHEMA COLLECTION   
TO TestLogin1  
GO  
-- Now user can execute the previous CREATE XML SCHEMA COLLECTION statement.  
SETUSER 'TestLogin1'  
GO  
CREATE XML SCHEMA COLLECTION myTestSchemaCollection AS '<?xml version="1.0" encoding="UTF-8" ?>  
<xsd:schema targetNamespace="http://schemas.adventure-works.com/Additional/ContactInfo"   
            xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
elementFormDefault="qualified">  
  
<xsd:element name="AdditionalContactInfo" >  
  <xsd:complexType mixed="true" >  
    <xsd:sequence>  
      <xsd:any processContents="strict"    
               namespace="http://schemas.adventure-works.com/Contact/Record   
                          http://schemas.adventure-works.com/AdditionalContactTypes"  
               minOccurs="0" maxOccurs="unbounded" />  
    </xsd:sequence>  
  </xsd:complexType>  
</xsd:element>  
<xsd:element name="telephone" type="xsd:string" />  
</xsd:schema>'  
GO  
  
-- Create a table by using the collection to type an XML column.   
--TestLogin1 must have permission to create a table.  
SETUSER  
GO  
GRANT CREATE TABLE TO TestLogin1  
GO  
-- The user also must have REFERENCES permission to use the XML schema collection  
-- to create a typed XML column (REFERENCES permission on schema   
-- collection is not needed).  
GRANT REFERENCES ON XML SCHEMA COLLECTION::myTestSchemaCollection   
TO TestLogin1  
GO  
-- Now user can create a table and use the XML schema collection to create   
-- a typed XML column.  
SETUSER 'TestLogin1'  
GO  
CREATE TABLE MyTestTable (xmlCol xml (dbo.myTestSchemaCollection))  
GO  
-- To insert data in the table, the user needs EXECUTE permission on the XML schema collection.  
-- GRANT EXECUTE permission to TestLogin2 on the xml schema collection.  
SETUSER  
GO  
GRANT EXECUTE ON XML SCHEMA COLLECTION::myTestSchemaCollection   
TO TestLogin1  
GO  
-- TestLogin1 does not own the dbo schema. This user must have INSERT permission.  
GRANT INSERT TO TestLogin1  
GO  
-- Now the user can insert data into the table.  
SETUSER 'TestLogin1'  
GO  
INSERT INTO MyTestTable VALUES('  
<telephone xmlns="http://schemas.adventure-works.com/Additional/ContactInfo">111-1111</telephone>  
')  
GO  
-- To query the table, TestLogin1 must have permissions: SELECT on the table and EXECUTE on the XML schema collection.  
SETUSER  
GO  
GRANT SELECT TO TestLogin1  
GO  
-- TestLogin1 already has EXECUTE permission on the schema (granted before inserting a record in the table).  
SELECT xmlCol.query('declare default element namespace "http://schemas.adventure-works.com/Additional/ContactInfo" /telephone[1]')  
FROM MyTestTable  
GO  
-- To show that the user must have EXECUTE permission to query, revoke the  
-- previously granted permission and return the query.  
SETUSER  
GO  
REVOKE EXECUTE ON XML SCHEMA COLLECTION::myTestSchemaCollection to TestLogin1  
Go  
-- Now TestLogin1 cannot execute the query.  
SETUSER 'TestLogin1'  
GO  
SELECT xmlCol.query('declare default element namespace "http://schemas.adventure-works.com/Additional/ContactInfo" /telephone[1]')  
FROM MyTestTable  
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
  
### <a name="c-granting-alter-permission-on-an-xml-schema-collection"></a><span data-ttu-id="98608-149">C.</span><span class="sxs-lookup"><span data-stu-id="98608-149">C.</span></span> <span data-ttu-id="98608-150">XML 스키마 컬렉션에 대한 ALTER 권한 부여</span><span class="sxs-lookup"><span data-stu-id="98608-150">Granting ALTER permission on an XML schema collection</span></span>  
 <span data-ttu-id="98608-151">사용자가 데이터베이스에서 기존 XML 스키마 컬렉션을 수정하려면 ALTER 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="98608-151">A user must have ALTER permission to modify an existing XML schema collection in the database.</span></span> <span data-ttu-id="98608-152">다음 예에서는 `ALTER` 권한을 부여하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="98608-152">The following example shows how to grant `ALTER` permission.</span></span>  
  
```  
SETUSER  
GO  
USE master  
GO  
CREATE LOGIN TestLogin1 WITH password='SQLSvrPwd1'  
GO  
CREATE DATABASE SampleDBForSchemaPermissions  
GO  
USE SampleDBForSchemaPermissions  
GO  
CREATE USER TestLogin1  
GO  
-- Grant permission to the user.  
SETUSER  
GO  
-- User must have ALTER permission on the relational schema in the database.  
GRANT ALTER ON SCHEMA::dbo TO TestLogin1  
GO  
-- User also must have permission to create XML schema collections in the database.  
GRANT CREATE XML SCHEMA COLLECTION   
TO TestLogin1  
GO  
-- Now user can execute the previous CREATE XML SCHEMA COLLECTION statement.  
SETUSER 'TestLogin1'  
GO  
CREATE XML SCHEMA COLLECTION myTestSchemaCollection AS '<?xml version="1.0" encoding="UTF-8" ?>  
<xsd:schema targetNamespace="http://schemas.adventure-works.com/Additional/ContactInfo"   
            xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
elementFormDefault="qualified">  
  
<xsd:element name="AdditionalContactInfo" >  
  <xsd:complexType mixed="true" >  
    <xsd:sequence>  
      <xsd:any processContents="strict"    
               namespace="http://schemas.adventure-works.com/Contact/Record   
                          http://schemas.adventure-works.com/AdditionalContactTypes"  
               minOccurs="0" maxOccurs="unbounded" />  
    </xsd:sequence>  
  </xsd:complexType>  
</xsd:element>  
<xsd:element name="telephone" type="xsd:string" />  
</xsd:schema>'  
GO  
-- Grant ALTER permission to TestLogin1.  
setuser  
GO  
GRANT ALTER ON XML SCHEMA COLLECTION::myTestSchemaCollection TO TestLogin1  
GO  
-- TestLogin1 should be able to add components to the collection.  
SETUSER 'TestLogin1'  
GO  
ALTER XML SCHEMA COLLECTION myTestSchemaCollection ADD '  
<xsd:schema targetNamespace="http://schemas.adventure-works.com/Additional/ContactInfo"   
            xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
            xmlns="http://schemas.adventure-works.com/Additional/ContactInfo"   
elementFormDefault="qualified">  
 <xsd:element name="pager" type="xsd:string"/>  
</xsd:schema>  
'  
Go  
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
  
### <a name="d-granting-take-ownership-permission-on-an-xml-schema-collection"></a><span data-ttu-id="98608-153">D.</span><span class="sxs-lookup"><span data-stu-id="98608-153">D.</span></span> <span data-ttu-id="98608-154">XML 스키마 컬렉션에 대한 TAKE OWNERSHIP 권한 부여</span><span class="sxs-lookup"><span data-stu-id="98608-154">Granting TAKE OWNERSHIP permission on an XML schema collection</span></span>  
 <span data-ttu-id="98608-155">다음 예에서는 XML 스키마 소유권을 한 사용자에서 다른 사용자로 이전하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="98608-155">The following example shows how to transfer XML schema ownership from one user to another.</span></span> <span data-ttu-id="98608-156">보다 유용한 예로 만들기 위해 사용자는 서로 다른 기본 관계형 스키마에서 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="98608-156">To make the example more interesting, the users in this example work in different default relational schemas.</span></span>  
  
 <span data-ttu-id="98608-157">이 예에서는 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="98608-157">This example does the following:</span></span>  
  
-   <span data-ttu-id="98608-158">`dbo` 및 `myOtherDBSchema`라는 두 개의 관계형 스키마로 데이터베이스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="98608-158">Creates a database with two relational schemas, `dbo` and `myOtherDBSchema`).</span></span>  
  
-   <span data-ttu-id="98608-159">`TestLogin1` 및 `TestLogin2`의 두 사용자를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="98608-159">Creates two users, `TestLogin1` and `TestLogin2`.</span></span> <span data-ttu-id="98608-160">`TestLogin2` 는 `myOtherDBSchema` 관계형 스키마의 소유자가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="98608-160">`TestLogin2` is made the owner of the `myOtherDBSchema` relational schema.</span></span>  
  
-   <span data-ttu-id="98608-161">`TestLogin1` 은 `dbo` 관계형 스키마에 XML 스키마 컬렉션을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="98608-161">`TestLogin1` creates an XML schema collection in the `dbo` relational schema.</span></span>  
  
-   <span data-ttu-id="98608-162">`TestLogin1` 이 그런 다음 XML 스키마 컬렉션에 대한 `TAKE OWNERSHIP` 권한을 `TestLogin2`에게 부여합니다.</span><span class="sxs-lookup"><span data-stu-id="98608-162">`TestLogin1` then gives `TAKE OWNERSHIP` permission on the XML schema collection to `TestLogin2`.</span></span>  
  
-   <span data-ttu-id="98608-163">`TestLogin2` 는 XML 스키마 컬렉션의 관계형 스키마를 변경하지 않고 `myOtherDBSchema`에서 XML 스키마 컬렉션의 소유자가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="98608-163">`TestLogin2` becomes the owner of the XML schema collection in `myOtherDBSchema`, without changing the relational schema of the XML schema collection.</span></span>  
  
```  
CREATE LOGIN TestLogin1 with password='SQLSvrPwd1'  
GO  
CREATE LOGIN TestLogin2 with password='SQLSvrPwd2'  
GO  
CREATE DATABASE SampleDBForSchemaPermissions  
GO  
USE SampleDBForSchemaPermissions  
GO  
-- Create another relational schema in the database.  
CREATE SCHEMA myOtherDBSchema  
GO  
-- Create users in the database. Note TestLogin2's default schema is  
-- myOtherDBSchema.  
CREATE USER TestLogin1  
GO  
CREATE USER TestLogin2 WITH DEFAULT_SCHEMA=myOtherDBSchema  
GO  
-- TestLogin2 will own myOtherDBSchema relational schema.  
ALTER AUTHORIZATION ON SCHEMA::myOtherDBSchema TO TestLogin2  
GO  
  
-- For TestLogin1 to create XML schema collection, the following  
-- permission is required.  
GRANT CREATE XML SCHEMA COLLECTION   
TO TestLogin1  
GO  
GRANT ALTER ON SCHEMA::dbo TO TestLogin1  
GO  
-- Now TestLogin1 can create an XML schema collection.  
setuser 'TestLogin1'  
GO  
CREATE XML SCHEMA COLLECTION myTestSchemaCollection AS '<?xml version="1.0" encoding="UTF-8" ?>  
<xsd:schema targetNamespace="http://schemas.adventure-works.com/Additional/ContactInfo"   
            xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
elementFormDefault="qualified">  
  
<xsd:element name="AdditionalContactInfo" >  
 <xsd:complexType mixed="true" >  
    <xsd:sequence>  
      <xsd:any processContents="strict"   
               namespace="http://schemas.adventure-works.com/Contact/Record   
                          http://schemas.adventure-works.com/AdditionalContactTypes"  
               minOccurs="0" maxOccurs="unbounded" />  
    </xsd:sequence>  
 </xsd:complexType>  
</xsd:element>  
<xsd:element name="telephone" type="xsd:string" />  
</xsd:schema>'  
GO  
  
-- Grant TAKE OWNERSHIP to TestLogin2.  
SETUSER  
GO  
GRANT TAKE OWNERSHIP ON XML SCHEMA COLLECTION::dbo.myTestSchemaCollection   
TO TestLogin2  
GO  
-- Verify the owner. Note the UserName and Principal_id is null.   
SELECT user_name(sys.xml_schema_collections.principal_id) as UserName,   
       sys.schemas.name as RelSchemaName,*   
FROM   sys.xml_schema_collections   
      JOIN sys.schemas   
      ON sys.schemas.schema_id=sys.xml_schema_collections.schema_id  
GO  
-- TestLogin2 can take ownership now.  
setuser 'TestLogin2'  
GO  
ALTER AUTHORIZATION ON XML SCHEMA COLLECTION::dbo.myTestSchemaCollection   
TO TestLogin2  
GO  
-- Note that although TestLogin2 is the owner,the XML schema collection   
-- is still in dbo.  
SELECT user_name(sys.xml_schema_collections.principal_id) as UserName,   
      sys.schemas.name as RelSchemaName,*   
FROM sys.xml_schema_collections JOIN sys.schemas   
     ON sys.schemas.schema_id=sys.xml_schema_collections.schema_id  
GO  
  
-- TestLogin2 moves the collection from dbo to myOtherDBSchema relational schema.  
-- TestLogin2 already has all necessary permissions.  
-- 1) TestLogin2 owns the destination relational schema so he can alter it.  
-- 2) TestLogin2 owns the XML schema collection (therefore, has CONTROL permission).  
ALTER SCHEMA myOtherDBSchema  
TRANSFER XML SCHEMA COLLECTION::dbo.myTestSchemaCollection  
GO  
  
SELECT user_name(sys.xml_schema_collections.principal_id) as UserName,   
       sys.schemas.name as RelSchemaName,*   
FROM   sys.xml_schema_collections JOIN sys.schemas   
       ON sys.schemas.schema_id=sys.xml_schema_collections.schema_id  
GO  
-- Final cleanup   
SETUSER  
GO  
USE master  
GO  
DROP DATABASE SampleDBForSchemaPermissions  
GO  
DROP LOGIN TestLogin1  
DROP LOGIN TestLogin2  
go   
```  
  
### <a name="e-granting-view-definition-permission-on-an-xml-schema-collection"></a><span data-ttu-id="98608-164">E.</span><span class="sxs-lookup"><span data-stu-id="98608-164">E.</span></span> <span data-ttu-id="98608-165">XML 스키마 컬렉션에 대한 VIEW DEFINITION 권한 부여</span><span class="sxs-lookup"><span data-stu-id="98608-165">Granting VIEW DEFINITION permission on an XML schema collection</span></span>  
 <span data-ttu-id="98608-166">다음 예에서는 XML 스키마 컬렉션에 대한 VIEW DEFINITION 권한을 부여하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="98608-166">The following example shows how to grant VIEW DEFINITION permissions for an XML schema collection.</span></span>  
  
```  
SETUSER  
GO  
USE master  
GO  
IF EXISTS( SELECT * FROM sysdatabases WHERE name='permissionsDB' )  
   DROP DATABASE permissionsDB  
GO  
IF EXISTS( SELECT * FROM sys.sql_logins WHERE name='schemaUser' )  
   DROP LOGIN schemaUser  
GO  
CREATE DATABASE permissionsDB  
GO  
CREATE LOGIN schemaUser WITH PASSWORD='Pass#123',DEFAULT_DATABASE=permissionsDB  
GO  
GRANT CONNECT SQL TO schemaUser  
GO  
USE permissionsDB  
GO  
CREATE USER schemaUser WITH DEFAULT_SCHEMA=dbo  
GO  
CREATE XML SCHEMA COLLECTION MySC AS '  
<schema xmlns="http://www.w3.org/2001/XMLSchema" targetNamespace="http://ns"  
xmlns:ns="http://ns">  
  
   <simpleType name="ListOfIntegers">  
      <list itemType="integer"/>  
   </simpleType>  
  
   <element name="root" type="ns:ListOfIntegers"/>  
  
   <element name="gRoot" type="gMonth"/>  
  
</schema>  
'  
GO  
-- schemaUser cannot see the contents of the collection.  
SETUSER 'schemaUser'  
GO  
SELECT XML_SCHEMA_NAMESPACE(N'dbo',N'MySC')  
GO  
  
-- Grant schemaUser VIEW DEFINITION and REFERENCES permissions  
-- on the XML schema collection.  
SETUSER  
GO  
GRANT VIEW DEFINITION ON XML SCHEMA COLLECTION::dbo.MySC TO schemaUser  
GO  
GRANT REFERENCES ON XML SCHEMA COLLECTION::dbo.MySC TO schemaUser  
GO  
-- Now schemaUser can see the content of the collection.  
SETUSER 'schemaUser'  
GO  
SELECT XML_SCHEMA_NAMESPACE(N'dbo',N'MySC')  
GO  
-- Revoke schemaUser VIEW DEFINITION permissions  
-- on the XML schema collection.  
SETUSER  
GO  
REVOKE VIEW DEFINITION ON XML SCHEMA COLLECTION::dbo.MySC FROM schemaUser  
GO  
-- Now schemaUser cannot see the contents of   
-- the collection.  
setuser 'schemaUser'  
GO  
SELECT XML_SCHEMA_NAMESPACE(N'dbo',N'MySC')  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="98608-167">참고 항목</span><span class="sxs-lookup"><span data-stu-id="98608-167">See Also</span></span>  
 <span data-ttu-id="98608-168">[XML 데이터&#40;SQL Server&#41;](xml-data-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="98608-168">[XML Data &#40;SQL Server&#41;](xml-data-sql-server.md) </span></span>  
 <span data-ttu-id="98608-169">[형식화된 XML과 형식화되지 않은 XML 비교](compare-typed-xml-to-untyped-xml.md) </span><span class="sxs-lookup"><span data-stu-id="98608-169">[Compare Typed XML to Untyped XML](compare-typed-xml-to-untyped-xml.md) </span></span>  
 <span data-ttu-id="98608-170">[XML 스키마 컬렉션&#40;SQL Server&#41;](xml-schema-collections-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="98608-170">[XML Schema Collections &#40;SQL Server&#41;](xml-schema-collections-sql-server.md) </span></span>  
 [<span data-ttu-id="98608-171">서버의 XML 스키마 컬렉션에 대한 요구 사항 및 제한 사항</span><span class="sxs-lookup"><span data-stu-id="98608-171">Requirements and Limitations for XML Schema Collections on the Server</span></span>](requirements-and-limitations-for-xml-schema-collections-on-the-server.md)  
  
  
