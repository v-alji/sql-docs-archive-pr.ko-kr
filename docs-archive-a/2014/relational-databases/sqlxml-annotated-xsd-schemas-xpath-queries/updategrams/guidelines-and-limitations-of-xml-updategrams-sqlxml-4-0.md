---
title: XML Updategrams의 지침 및 제한 사항 (SQLXML 4.0) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- updategrams [SQLXML], about updategrams
ms.assetid: b5231859-14e2-4276-bc17-db2817b6f235
author: rothja
ms.author: jroth
ms.openlocfilehash: 6e01e366edc2889691862de639f69220ac4bb439
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87732456"
---
# <a name="guidelines-and-limitations-of-xml-updategrams-sqlxml-40"></a><span data-ttu-id="d5a3a-102">XML updategram에 대한 지침 및 제한 사항(SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="d5a3a-102">Guidelines and Limitations of XML Updategrams (SQLXML 4.0)</span></span>
  <span data-ttu-id="d5a3a-103">XML updategram 사용 시 다음 사항에 유의하십시오.</span><span class="sxs-lookup"><span data-stu-id="d5a3a-103">Remember the following when using XML updategrams:</span></span>  
  
-   <span data-ttu-id="d5a3a-104">Updategram를 사용 하 여 단일 쌍의 and 블록만 포함 하는 삽입 작업을 수행 하는 경우에는 **\<before>** **\<after>** 블록을 **\<before>** 생략할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d5a3a-104">If you are using an updategram for an insert operation with only a single pair of **\<before>** and **\<after>** blocks, the **\<before>** block can be omitted.</span></span> <span data-ttu-id="d5a3a-105">반대로 삭제 작업의 경우에는 **\<after>** 블록을 생략할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d5a3a-105">Conversely, in case of a delete operation, the **\<after>** block can be omitted.</span></span>  
  
-   <span data-ttu-id="d5a3a-106">태그에서 여러 개의 및 블록을 사용 하는 updategram를 사용 하는 경우에는 **\<before>** **\<after>** **\<sync>** **\<before>** 블록과 블록을 모두 **\<after>** 형성 하 고 쌍으로 지정 해야 합니다 **\<before>** **\<after>** .</span><span class="sxs-lookup"><span data-stu-id="d5a3a-106">If you are using an updategram with multiple **\<before>** and **\<after>** blocks in the **\<sync>** tag, both **\<before>** blocks and **\<after>** blocks must be specified to form **\<before>** and **\<after>** pairs.</span></span>  
  
-   <span data-ttu-id="d5a3a-107">Updategram의 업데이트는 XML 스키마에서 제공한 XML 뷰에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="d5a3a-107">The updates in an updategram are applied to the XML view that is provided by the XML schema.</span></span> <span data-ttu-id="d5a3a-108">따라서 기본 매핑이 성공하려면 updategram에서 스키마 파일 이름을 지정하거나, 파일 이름을 지정하지 않을 경우 요소 및 특성 이름이 데이터베이스의 테이블 및 열 이름과 일치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d5a3a-108">Therefore, for the default mapping to succeed either you must specify the schema file name in the updategram or, if the file name is not provided, the element and attribute names must match the table and column names in the database.</span></span>  
  
-   <span data-ttu-id="d5a3a-109">SQLXML 4.0에서는 updategram의 모든 열 값이 제공된 스키마(XDR 또는 XSD)에서 명시적으로 매핑되어야 해당 자식 요소에 대한 XML 뷰를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d5a3a-109">SQLXML 4.0 requires that all column values in an updategram must be explicitly mapped in the schema (either XDR or XSD) provided to compose the XML view for its child elements.</span></span> <span data-ttu-id="d5a3a-110">이 동작은 이전 버전의 SQLXML에서 달라진 동작입니다. 이전 버전에서는 열 값이 `sql:relationship` 주석에서 외래 키의 일부로 암시된 경우 스키마에서 열 값을 매핑하지 않아도 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="d5a3a-110">This behavior differs from earlier versions of SQLXML, which allowed a value for a column not mapped in the schema if it was implied as part of the foreign Key in a `sql:relationship` annotation.</span></span> <span data-ttu-id="d5a3a-111">이 변경 사항은 기본 키 값이 자식 요소로 전파되는 것에는 영향을 주지 않습니다. SQLXML 4.0에서 이 동작은 자식 요소에 대해 값이 명시적으로 지정되지 않은 경우에도 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="d5a3a-111">(Note that this change does not affect propagation of primary key values to child elements, which still occurs for SQLXML 4.0 if no value is explicitly specified for the child element.</span></span>  
  
-   <span data-ttu-id="d5a3a-112">Updategram를 사용 하 여 이진 열 (예: 데이터 형식)의 데이터를 수정 하는 경우 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] `image` [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 데이터 형식 (예: `sql:datatype="image"` ) 및 XML 데이터 형식 (예: `dt:type="binhex"` 또는 `dt:type="binbase64` )을 지정 해야 하는 매핑 스키마를 제공 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d5a3a-112">If you are using an updategram to modify data in a binary column (such as the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] `image` data type), you must provide a mapping schema in which the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] data type (for example, `sql:datatype="image"`) and the XML data type (for example, `dt:type="binhex"` or `dt:type="binbase64`) must be specified.</span></span> <span data-ttu-id="d5a3a-113">Updategram에서는 이진 열에 대한 데이터를 지정해야 합니다. 매핑 스키마에 지정된 `sql:url-encode` 주석은 updategram에서 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="d5a3a-113">The data for the binary column must be specified in the updategram; the `sql:url-encode` annotation that is specified in the mapping schema is ignored by the updategram.</span></span>  
  
-   <span data-ttu-id="d5a3a-114">XSD 스키마를 작성할 때 `sql:relation` 또는 `sql:field` 주석에 대해 지정하는 값에 "Order Details" 테이블 이름처럼 공백 문자 같은 특수 문자가 포함되면 "[Order Details]"처럼 값을 대괄호로 묶어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d5a3a-114">When you are writing an XSD schema, if the value you specify for the `sql:relation` or `sql:field` annotation includes a special character, such as a space character (for example, in the "Order Details" table name), this value must be enclosed in brackets (for example, "[Order Details]").</span></span>  
  
-   <span data-ttu-id="d5a3a-115">Updategram을 사용할 때 체인 관계는 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d5a3a-115">When using updategrams, chain relationships are not supported.</span></span> <span data-ttu-id="d5a3a-116">예를 들어 테이블 A와 C가 테이블 B를 사용하는 체인 관계를 통해 연결된 경우 updategram을 실행하려고 하면 다음 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="d5a3a-116">For example, if tables A and C are related through a chain relationship that uses table B, the following error will occur when attempting to run and execute the updategram:</span></span>  
  
    ```  
    There is an inconsistency in the schema provided.  
    ```  
  
     <span data-ttu-id="d5a3a-117">스키마와 updategram 모두 형식이 올바르고 다른 문제가 없더라도 체인 관계가 있으면 이 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="d5a3a-117">Even if both schema and updategram are otherwise correct and validly formed, this error will occur if a chain relationship is present.</span></span>  
  
-   <span data-ttu-id="d5a3a-118">Updategram은 업데이트 중 `image` 형식 데이터를 매개 변수로 전달하는 것을 허용하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d5a3a-118">Updategrams do not permit the passing of `image` type data as parameters during updates.</span></span>  
  
-   <span data-ttu-id="d5a3a-119">Updategrams으로 작업할 때는 및 이미지와 같은 BLOB (Binary large object) 형식을 `text/ntext` 블록에 사용 하면 안 **\<before>** 됩니다. 동시성 제어에 사용 하기 위해 이러한 형식을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="d5a3a-119">Binary large object (BLOB) types like `text/ntext` and images should not be used in the **\<before>** block in when working with updategrams, because this will include them for use in concurrency control.</span></span> <span data-ttu-id="d5a3a-120">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]에서는 BLOB 형식 비교에 대한 제한으로 인해 문제가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d5a3a-120">This can cause problems with [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] because of the limitations on comparison for BLOB types.</span></span> <span data-ttu-id="d5a3a-121">예를 들어 LIKE 키워드는 `text` 데이터 형식의 열을 비교하기 위해 WHERE 절에 사용되지만 BLOB 형식의 데이터 크기가 8K 이상이면 비교 작업이 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="d5a3a-121">For example, the LIKE keyword is used in the WHERE clause for comparing between columns of the `text` data type; however, comparisons will fail in the case of BLOB types where the size of the data is greater than 8K.</span></span>  
  
-   <span data-ttu-id="d5a3a-122">SQLXML 4.0에서는 BLOB 형식 비교에 대한 제한으로 인해 `ntext` 데이터에 특수 문자가 있으면 문제가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d5a3a-122">Special characters in `ntext` data can cause problems with SQLXML 4.0 because of the limitations on comparison for BLOB types.</span></span> <span data-ttu-id="d5a3a-123">예를 들어 **\<before>** 형식의 열에 대 한 동시성 검사에 사용 될 때 updategram의 블록에 "[Serializable]"을 사용 하면 `ntext` 다음과 같은 SQLOLEDB 오류 설명과 함께 실패 합니다.</span><span class="sxs-lookup"><span data-stu-id="d5a3a-123">For example, the use of "[Serializable]" in the **\<before>** block of an updategrams when used in concurrency checking of a column of `ntext` type will fail with the following SQLOLEDB error description:</span></span>  
  
    ```  
    Empty update, no updatable rows found   Transaction aborted  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="d5a3a-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d5a3a-124">See Also</span></span>  
 [<span data-ttu-id="d5a3a-125">Updategram 보안 고려 사항은 SQLXML 4.0&#41;&#40;</span><span class="sxs-lookup"><span data-stu-id="d5a3a-125">Updategram Security Considerations &#40;SQLXML 4.0&#41;</span></span>](../security/updategram-security-considerations-sqlxml-4-0.md)  
  
  
