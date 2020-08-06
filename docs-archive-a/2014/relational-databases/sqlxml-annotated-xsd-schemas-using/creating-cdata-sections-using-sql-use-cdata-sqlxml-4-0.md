---
title: 'Sql을 사용 하 여 CDATA 섹션 만들기: use-CDATA (SQLXML 4.0) | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- markup characters [SQLXML]
- special characters [SQLXML]
- use-cdata annotation
- plain text [SQLXML]
- CDATA sections
- escaping blocks of text [SQLXML]
- annotated XSD schemas, CDATA sections
- sql:use-cdata
ms.assetid: 26d2b9dc-f857-44ff-bcd4-aaf64ff809d0
author: rothja
ms.author: jroth
ms.openlocfilehash: c0ba0787efbda400590a75f0f3529e3df8819e41
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659901"
---
# <a name="creating-cdata-sections-using-sqluse-cdata-sqlxml-40"></a><span data-ttu-id="30229-102">sql:use-cdata를 사용하여 CDATA 섹션 만들기(SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="30229-102">Creating CDATA Sections Using sql:use-cdata (SQLXML 4.0)</span></span>
  <span data-ttu-id="30229-103">XML에서 CDATA 섹션은 태그 문자로 인식될 문자가 포함된 텍스트 블록을 이스케이프하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="30229-103">In XML, CDATA sections are used to escape blocks of text that contain characters that would otherwise be recognized as markup characters.</span></span>  
  
 <span data-ttu-id="30229-104">Microsoft의 데이터베이스에는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] XML 파서에서 태그 문자로 취급 되는 문자가 포함 될 수 있습니다. 예를 들어 꺾쇠 괄호 ( \< and > ), 작거나 같음 기호 (<=), 앰퍼샌드 (&)는 태그 문자로 처리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="30229-104">A database in Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] can sometimes contain characters that are treated as markup characters by the XML parser; for example, angle brackets (\< and >), the less-than-or-equal-to symbol (<=), and the ampersand (&) are treated as markup characters.</span></span> <span data-ttu-id="30229-105">하지만 이러한 유형의 특수 문자를 CDATA 섹션에 래핑하여 태그 문자로 처리되지 않도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="30229-105">However, you can wrap this type of special characters in a CDATA section to prevent them from being treated as markup characters.</span></span> <span data-ttu-id="30229-106">CDATA 섹션 내의 텍스트는 XML 파서에서 일반 텍스트로 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="30229-106">The text within the CDATA section is treated by the XML parser as plain text.</span></span>  
  
 <span data-ttu-id="30229-107">`sql:use-cdata` 주석은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 반환된 데이터를 CDATA 섹션에 래핑하도록 지정하는 데 사용됩니다. 즉, `sql:field`로 지정된 열의 값을 CDATA 섹션에 포함할지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="30229-107">The `sql:use-cdata` annotation is used to specify that the data returned by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] should be wrapped in a CDATA section (that is, it indicates whether the value from a column that is specified by `sql:field` should be enclosed in a CDATA section).</span></span> <span data-ttu-id="30229-108">`sql:use-cdata` 주석은 데이터베이스 열에 매핑되는 요소에만 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="30229-108">The `sql:use-cdata` annotation can be specified only on elements that map to a database column.</span></span>  
  
 <span data-ttu-id="30229-109">`sql:use-cdata` 주석은 부울 값(0=false, 1=true)을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="30229-109">The `sql:use-cdata` annotation takes a Boolean value (0 = false, 1 = true).</span></span> <span data-ttu-id="30229-110">허용되는 값은 0, 1, true 및 false입니다.</span><span class="sxs-lookup"><span data-stu-id="30229-110">The acceptable values are 0, 1, true, and false.</span></span>  
  
 <span data-ttu-id="30229-111">`sql:url-encode`나 ID, IDREF, IDREFS, NMTOKEN 및 NMTOKENS 특성 유형에는 이 주석을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="30229-111">This annotation cannot be used with `sql:url-encode` or on the ID, IDREF, IDREFS, NMTOKEN, and NMTOKENS attribute types.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="30229-112">예</span><span class="sxs-lookup"><span data-stu-id="30229-112">Examples</span></span>  
 <span data-ttu-id="30229-113">다음 예를 사용하여 작업 예제를 만들려면 특정 요구 사항이 충족되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="30229-113">To create working samples using the following examples, you must meet certain requirements.</span></span> <span data-ttu-id="30229-114">자세한 내용은 [SQLXML 예를 실행 하기 위한 요구 사항](../sqlxml/requirements-for-running-sqlxml-examples.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="30229-114">For more information, see [Requirements for Running SQLXML Examples](../sqlxml/requirements-for-running-sqlxml-examples.md).</span></span>  
  
### <a name="a-specifying-sqluse-cdata-on-an-element"></a><span data-ttu-id="30229-115">A.</span><span class="sxs-lookup"><span data-stu-id="30229-115">A.</span></span> <span data-ttu-id="30229-116">요소에 sql:use-cdata 지정</span><span class="sxs-lookup"><span data-stu-id="30229-116">Specifying sql:use-cdata on an element</span></span>  
 <span data-ttu-id="30229-117">다음 스키마에서는 `sql:use-cdata` 요소 내의에 대해 1 (True)로 설정 됩니다 **\<AddressLine1>** **\<Address>** .</span><span class="sxs-lookup"><span data-stu-id="30229-117">In the following schema, `sql:use-cdata` is set to 1 (True) for the **\<AddressLine1>** within the **\<Address>** element.</span></span> <span data-ttu-id="30229-118">따라서 데이터가 CDATA 섹션으로 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="30229-118">As a result, the data is returned in a CDATA section.</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:element name="Address"   
               sql:relation="Person.Address"   
               sql:key-fields="AddressID" >  
   <xsd:complexType>  
        <xsd:sequence>  
          <xsd:element name="AddressID"  type="xsd:string" />  
          <xsd:element name="AddressLine1" type="xsd:string"   
                       sql:use-cdata="1" />  
        </xsd:sequence>  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a><span data-ttu-id="30229-119">스키마에 대해 예제 XPath 쿼리를 테스트하려면</span><span class="sxs-lookup"><span data-stu-id="30229-119">To test a sample XPath query against the schema</span></span>  
  
1.  <span data-ttu-id="30229-120">위 스키마 코드를 복사한 후 텍스트 파일에 붙여넣습니다.</span><span class="sxs-lookup"><span data-stu-id="30229-120">Copy the schema code above and paste it into a text file.</span></span> <span data-ttu-id="30229-121">파일을 UseCData.xml로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="30229-121">Save the file as UseCData.xml.</span></span>  
  
2.  <span data-ttu-id="30229-122">다음 템플릿을 복사한 후 텍스트 파일에 붙여넣습니다.</span><span class="sxs-lookup"><span data-stu-id="30229-122">Copy the following template and paste it into a text file.</span></span> <span data-ttu-id="30229-123">UseCData.xml을 저장한 디렉터리와 같은 디렉터리에 UseCDataT.xml로 파일을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="30229-123">Save the file as UseCDataT.xml in the same directory where you saved UseCData.xml.</span></span>  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
        <sql:xpath-query mapping-schema="UseCData.xml">  
            /Address[AddressID < 11]  
        </sql:xpath-query>  
    </ROOT>  
    ```  
  
     <span data-ttu-id="30229-124">매핑 스키마(UseCData.xml)에 대해 지정된 디렉터리 경로는 템플릿이 저장된 디렉터리를 기준으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="30229-124">The directory path specified for the mapping schema (UseCData.xml) is relative to the directory where the template is saved.</span></span> <span data-ttu-id="30229-125">또한 다음과 같이 절대 경로를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="30229-125">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\SqlXmlTest\UseCData.xml"  
    ```  
  
3.  <span data-ttu-id="30229-126">SQLXML 4.0 테스트 스크립트(Sqlxml4test.vbs)를 만든 다음 이 스크립트를 사용하여 템플릿을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="30229-126">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="30229-127">자세한 내용은 [ADO를 사용 하 여 SQLXML 4.0 쿼리 실행](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="30229-127">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="30229-128">다음은 결과 집합의 일부입니다.</span><span class="sxs-lookup"><span data-stu-id="30229-128">This is the partial result set:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">   
  <Address>   
    <AddressID>1</CustomerID>   
    <AddressLine1>   
      <![CDATA[ 1970 Napa Ct.  ]]>   
    </AddressLine1>   
  </Address>  
  <Address>  
    <AddressLine1>   
      <![CDATA[ 9833 Mt. Dias Blv. ]]>   
    </AddressLine1>   
  </Address>  
  ...  
</ROOT>  
```  
  
  
