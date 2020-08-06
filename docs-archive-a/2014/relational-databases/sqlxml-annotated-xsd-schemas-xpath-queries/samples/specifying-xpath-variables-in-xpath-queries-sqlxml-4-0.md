---
title: XPath 쿼리에 XPath 변수 지정 (SQLXML 4.0) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- XPath queries [SQLXML], XPath variables
- XPath variables [SQLXML]
ms.assetid: c11ab816-11b8-4131-8b77-c03fe500fa10
author: rothja
ms.author: jroth
ms.openlocfilehash: 5045831f627722f7dbb9a9189be5c48d830f2add
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646272"
---
# <a name="specifying-xpath-variables-in-xpath-queries-sqlxml-40"></a><span data-ttu-id="107a8-102">XPath 쿼리에 XPath 변수 지정(SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="107a8-102">Specifying XPath Variables in XPath Queries (SQLXML 4.0)</span></span>
  <span data-ttu-id="107a8-103">다음 예에서는 XPath 쿼리에 XPath 변수를 전달하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="107a8-103">The following examples show how XPath variables are passed in XPath queries.</span></span> <span data-ttu-id="107a8-104">이 예의 XPath 쿼리는 SampleSchema1.xml에 포함된 매핑 스키마에 대해 지정되었습니다.</span><span class="sxs-lookup"><span data-stu-id="107a8-104">The XPath queries in these examples are specified against the mapping schema contained in SampleSchema1.xml.</span></span> <span data-ttu-id="107a8-105">이 샘플 스키마에 대 한 자세한 내용은 [예제 주석 XSD schema For XPath 예제 &#40;SQLXML 4.0&#41;](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="107a8-105">For information about this sample schema, see [Sample Annotated XSD Schema for XPath Examples &#40;SQLXML 4.0&#41;](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md).</span></span>  
  
## <a name="examples"></a><span data-ttu-id="107a8-106">예</span><span class="sxs-lookup"><span data-stu-id="107a8-106">Examples</span></span>  
  
### <a name="a-use-the-xpath-variables"></a><span data-ttu-id="107a8-107">A.</span><span class="sxs-lookup"><span data-stu-id="107a8-107">A.</span></span> <span data-ttu-id="107a8-108">XPath 변수 사용</span><span class="sxs-lookup"><span data-stu-id="107a8-108">Use the XPath variables</span></span>  
 <span data-ttu-id="107a8-109">샘플 템플릿은 XPath 쿼리 두 개로 구성되며</span><span class="sxs-lookup"><span data-stu-id="107a8-109">A sample template consists of two XPath queries.</span></span> <span data-ttu-id="107a8-110">각 XPath 쿼리는 하나의 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="107a8-110">Each of the XPath queries takes one parameter.</span></span> <span data-ttu-id="107a8-111">템플릿에는 이러한 매개 변수의 기본값도 지정되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="107a8-111">The template also specifies default values for these parameters.</span></span> <span data-ttu-id="107a8-112">기본값은 매개 변수 값을 지정하지 않은 경우에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="107a8-112">The default values are used if parameter values are not specified.</span></span> <span data-ttu-id="107a8-113">에는 기본값이 지정 된 두 개의 매개 변수가 지정 됩니다 **\<sql:header>** .</span><span class="sxs-lookup"><span data-stu-id="107a8-113">Two parameters with default values are specified in **\<sql:header>**.</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <sql:header>  
     <sql:param name='CustomerID'>1</sql:param>  
     <sql:param name='ContactID'>1</sql:param>   
  </sql:header>  
  <sql:xpath-query mapping-schema="SampleSchema1.xml">  
    Customer[@CustomerID=$CustomerID]   
  </sql:xpath-query >  
  <sql:xpath-query mapping-schema="SampleSchema1.xml">  
   Contact[@ContactID=$ContactID]   
  </sql:xpath-query>  
</ROOT>  
```  
  
##### <a name="to-test-the-xpath-query-against-the-mapping-schema"></a><span data-ttu-id="107a8-114">매핑 스키마에 대해 XPath 쿼리를 테스트하려면</span><span class="sxs-lookup"><span data-stu-id="107a8-114">To test the XPath query against the mapping schema</span></span>  
  
1.  <span data-ttu-id="107a8-115">[샘플 스키마 코드](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md) 를 복사 하 여 텍스트 파일에 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="107a8-115">Copy the [sample schema code](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md) and paste it into a text file.</span></span> <span data-ttu-id="107a8-116">파일을 SampleSchema1.xml로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="107a8-116">Save the file as SampleSchema1.xml.</span></span>  
  
2.  <span data-ttu-id="107a8-117">다음 템플릿(XPathVariables.xml)을 만들고 다음과 같은 디렉터리에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="107a8-117">Create the following template (XPathVariables.xml) and save it in the directory where:</span></span>  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:header>  
         <sql:param name='CustomerID'>1</sql:param>  
         <sql:param name='ContactID'>1</sql:param>   
      </sql:header>  
      <sql:xpath-query mapping-schema="SampleSchema1.xml">  
        Customer[@CustomerID=$CustomerID]   
      </sql:xpath-query >  
      <sql:xpath-query mapping-schema="SampleSchema1.xml">  
       Contact[@ContactID=$ContactID]   
      </sql:xpath-query>  
    </ROOT>  
    ```  
  
     <span data-ttu-id="107a8-118">매핑 스키마(SampleSchema1.xml)에 대해 지정된 디렉터리 경로는 템플릿이 저장된 디렉터리에 상대적입니다.</span><span class="sxs-lookup"><span data-stu-id="107a8-118">The directory path specified for the mapping schema (SampleSchema1.xml) is relative to the directory where the template is saved.</span></span> <span data-ttu-id="107a8-119">또한 다음과 같이 절대 경로를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="107a8-119">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\MyDir\SampleSchema1.xml"  
    ```  
  
3.  <span data-ttu-id="107a8-120">SQLXML 4.0 테스트 스크립트(Sqlxml4test.vbs)를 만든 다음 이 스크립트를 사용하여 템플릿을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="107a8-120">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span> <span data-ttu-id="107a8-121">자세한 내용은 [ADO를 사용 하 여 SQLXML 4.0 쿼리 실행](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="107a8-121">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="107a8-122">이 예에서는 매개 변수를 전달하지 않으므로</span><span class="sxs-lookup"><span data-stu-id="107a8-122">In this example, no parameters are passed.</span></span> <span data-ttu-id="107a8-123">기본 매개 변수 값이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="107a8-123">Therefore, the default parameter values are used.</span></span>  
  
  
