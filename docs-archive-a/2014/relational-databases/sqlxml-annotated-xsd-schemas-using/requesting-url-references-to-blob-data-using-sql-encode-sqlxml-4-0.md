---
title: 'Sql: 인코드를 사용 하 여 BLOB 데이터에 대 한 URL 참조 요청 (SQLXML 4.0) | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- sql:encode
- encode annotation
- URL references to BLOB data [SQLXML]
- references to BLOB data [SQLXML]
- annotated XSD schemas, URL references to BLOB data
- requesting URL references to BLOB data
- BLOBs, URL references
- Base 64-encoded format
ms.assetid: 2f8cd93b-c636-462b-8291-167197233ee0
author: rothja
ms.author: jroth
ms.openlocfilehash: 8a9f5edcfab4a9d7307327d97bc2099c78c666c7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659893"
---
# <a name="requesting-url-references-to-blob-data-using-sqlencode-sqlxml-40"></a><span data-ttu-id="bb8c3-102">sql:encode를 사용하여 BLOB 데이터에 대한 URL 참조 요청(SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="bb8c3-102">Requesting URL References to BLOB Data Using sql:encode (SQLXML 4.0)</span></span>
  <span data-ttu-id="bb8c3-103">주석이 추가된 XSD 스키마에서 특성(또는 요소)이 Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 BLOB 열에 매핑된 경우 XML 내의 Base 64 인코딩 형식으로 데이터가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="bb8c3-103">In an annotated XSD schema, when an attribute (or element) is mapped to a BLOB column in Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the data is returned in Base 64-encoded format within XML.</span></span>  
  
 <span data-ttu-id="bb8c3-104">나중에 이진 형식으로 BLOB 데이터를 검색하는 데 사용할 수 있는 데이터 참조(URI)를 반환하려는 경우 `sql:encode` 주석을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="bb8c3-104">If you want a reference to the data (a URI) to be returned that can be used later to retrieve the BLOB data in a binary format, specify the `sql:encode` annotation.</span></span> <span data-ttu-id="bb8c3-105">단순 유형의 특성이나 요소에 `sql:encode`를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bb8c3-105">You can specify `sql:encode` on an attribute or element of simple type.</span></span>  
  
 <span data-ttu-id="bb8c3-106">필드 값 대신 필드에 대한 URL이 반환되도록 하려면 `sql:encode` 주석을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="bb8c3-106">Specify the `sql:encode` annotation to indicate that a URL to the field should be returned instead of the value of the field.</span></span> <span data-ttu-id="bb8c3-107">`sql:encode`는 기본 키를 사용하여 URL에 단일 선택을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="bb8c3-107">`sql:encode` depends on the primary key to generate a singleton select in the URL.</span></span> <span data-ttu-id="bb8c3-108">`sql:key-fields` 주석을 사용하여 기본 키를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bb8c3-108">The primary key can be specified using the `sql:key-fields` annotation.</span></span>  
  
 <span data-ttu-id="bb8c3-109">`sql:encode` 주석에 "url" 또는 "default" 값을 할당할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bb8c3-109">The `sql:encode` annotation can be assigned the "url" or the "default" value.</span></span> <span data-ttu-id="bb8c3-110">"default" 값은 Base 64 인코딩 형식으로 데이터를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="bb8c3-110">A value of "default" returns data in Base 64-encoded format.</span></span>  
  
 <span data-ttu-id="bb8c3-111">`sql:encode`나 ID, IDREF, IDREFS, NMTOKEN 또는 NMTOKENS 특성 유형에는 `sql:use-cdata` 주석을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="bb8c3-111">The `sql:encode` annotation cannot be used with `sql:use-cdata` or on the ID, IDREF, IDREFS, NMTOKEN, or NMTOKENS attribute types.</span></span> <span data-ttu-id="bb8c3-112">XSD **fixed** 특성에도 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="bb8c3-112">It can also not be used with XSD **fixed** attribute.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="bb8c3-113">BLOB 유형의 열은 키 또는 외래 키의 일부로 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="bb8c3-113">BLOB-type columns cannot be used as a part of a key or foreign key.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="bb8c3-114">예</span><span class="sxs-lookup"><span data-stu-id="bb8c3-114">Examples</span></span>  
 <span data-ttu-id="bb8c3-115">다음 예를 사용하여 작업 예제를 만들려면 특정 요구 사항이 충족되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb8c3-115">To create working samples using the following examples, you must meet certain requirements.</span></span> <span data-ttu-id="bb8c3-116">자세한 내용은 [SQLXML 예를 실행 하기 위한 요구 사항](../sqlxml/requirements-for-running-sqlxml-examples.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="bb8c3-116">For more information, see [Requirements for Running SQLXML Examples](../sqlxml/requirements-for-running-sqlxml-examples.md).</span></span>  
  
### <a name="a-specifying-sqlencode-to-obtain-a-url-reference-to-blob-data"></a><span data-ttu-id="bb8c3-117">A.</span><span class="sxs-lookup"><span data-stu-id="bb8c3-117">A.</span></span> <span data-ttu-id="bb8c3-118">sql:encode를 지정하여 BLOB 데이터에 대한 URL 참조 얻기</span><span class="sxs-lookup"><span data-stu-id="bb8c3-118">Specifying sql:encode to obtain a URL reference to BLOB data</span></span>  
 <span data-ttu-id="bb8c3-119">이 예에서 매핑 스키마는 `sql:encode` **LargePhoto** 특성을 지정 하 여 기본 64 인코딩 형식으로 이진 데이터를 검색 하는 대신 특정 제품 사진에 대 한 URI 참조를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb8c3-119">In this example, the mapping schema specifies `sql:encode` on the **LargePhoto** attribute to retrieve the URI reference to a specific product photo (instead of retrieving the binary data in Base 64-encoded format).</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  
  <xsd:element name="ProductPhoto" sql:relation="Production.ProductPhoto"   
               sql:key-fields="ProductPhotoID" >  
   <xsd:complexType>  
      <xsd:attribute name="ProductPhotoID"  type="xsd:int"  />  
     <xsd:attribute name="LargePhoto" type="xsd:string" sql:encode="url" />  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a><span data-ttu-id="bb8c3-120">스키마에 대해 예제 XPath 쿼리를 테스트하려면</span><span class="sxs-lookup"><span data-stu-id="bb8c3-120">To test a sample XPath query against the schema</span></span>  
  
1.  <span data-ttu-id="bb8c3-121">위 스키마 코드를 복사한 후 텍스트 파일에 붙여넣습니다.</span><span class="sxs-lookup"><span data-stu-id="bb8c3-121">Copy the schema code above and paste it into a text file.</span></span> <span data-ttu-id="bb8c3-122">파일을 sqlEncode.xml로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="bb8c3-122">Save the file as sqlEncode.xml.</span></span>  
  
2.  <span data-ttu-id="bb8c3-123">다음 템플릿을 복사한 후 텍스트 파일에 붙여넣습니다.</span><span class="sxs-lookup"><span data-stu-id="bb8c3-123">Copy the following template and paste it into a text file.</span></span> <span data-ttu-id="bb8c3-124">sqlEncode.xml을 저장한 디렉터리와 같은 디렉터리에 sqlEncodeT.xml로 파일을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="bb8c3-124">Save the file as sqlEncodeT.xml in the same directory where you saved sqlEncode.xml.</span></span>  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
        <sql:xpath-query mapping-schema="sqlEncode.xml">  
            /ProductPhoto[@ProductPhotoID=100]  
        </sql:xpath-query>  
    </ROOT>  
    ```  
  
     <span data-ttu-id="bb8c3-125">매핑 스키마(sqlEncode.xml)에 대해 지정된 디렉터리 경로는 템플릿이 저장된 디렉터리에 상대적입니다.</span><span class="sxs-lookup"><span data-stu-id="bb8c3-125">The directory path specified for the mapping schema (sqlEncode.xml) is relative to the directory where the template is saved.</span></span> <span data-ttu-id="bb8c3-126">또한 다음과 같이 절대 경로를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bb8c3-126">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\SqlXmlTest\sqlEncode.xml"  
    ```  
  
3.  <span data-ttu-id="bb8c3-127">SQLXML 4.0 테스트 스크립트(Sqlxml4test.vbs)를 만든 다음 이 스크립트를 사용하여 템플릿을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="bb8c3-127">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="bb8c3-128">자세한 내용은 [ADO를 사용 하 여 SQLXML 4.0 쿼리 실행](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="bb8c3-128">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="bb8c3-129">다음은 결과입니다.</span><span class="sxs-lookup"><span data-stu-id="bb8c3-129">This is the result:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
   <ProductPhoto ProductPhotoID="100"  
                 LargePhoto="dbobject/Production.ProductPhoto[@ProductPhotoID="100"]/@LargePhoto" />   
</ROOT>  
```  
  
  
