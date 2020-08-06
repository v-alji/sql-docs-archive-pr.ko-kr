---
title: XML 데이터에 비즈니스 논리 추가 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- business logic [XML]
ms.assetid: 0877fb38-f1a2-43d8-86cf-4754be224dc1
author: rothja
ms.author: jroth
ms.openlocfilehash: 5bf8e9edc36e9c420faa92f2db1a92c311194e99
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648872"
---
# <a name="add-business-logic-to-xml-data"></a><span data-ttu-id="52a32-102">XML 데이터에 비즈니스 논리 추가</span><span class="sxs-lookup"><span data-stu-id="52a32-102">Add Business Logic to XML Data</span></span>
  <span data-ttu-id="52a32-103">비즈니스 논리를 여러 가지 방식으로 XML 데이터에 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52a32-103">Your business logic can be added to XML data in several ways:</span></span>  
  
-   <span data-ttu-id="52a32-104">XML 데이터의 삽입 및 수정 중에 도메인 특정 제약 조건을 강화하도록 행 또는 열 제약 조건을 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52a32-104">You can write row or column constraints to enforce domain-specific constraints during insertion and modification of XML data.</span></span>  
  
-   <span data-ttu-id="52a32-105">열에서 값을 삽입 또는 업데이트할 때 발생되는 트리거를 XML 열에 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52a32-105">You can write a trigger on the XML column that fires when you insert or update values in the column.</span></span> <span data-ttu-id="52a32-106">이 트리거는 도메인 특정 유효성 검사 규칙을 포함하거나 속성 테이블을 채울 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52a32-106">The trigger can contain domain-specific validation rules or populate property tables.</span></span>  
  
-   <span data-ttu-id="52a32-107">데이터베이스 엔진에 관리 코드를 실행하는 기능이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="52a32-107">The Database Engine includes the ability execute managed code.</span></span> <span data-ttu-id="52a32-108">이 CLR(공용 언어 런타임) 통합을 사용하여 XML 값을 전달하는 관리 코드에 함수를 작성하고 System.Xml 네임스페이스에서 제공되는 XML 처리 기능을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52a32-108">You can use this common language runtime (CLR) integration to write functions in managed code to which you pass XML values, and use XML processing capabilities provided by the System.Xml namespace.</span></span> <span data-ttu-id="52a32-109">한 예는 XSL 변환을 XML 데이터에 적용하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="52a32-109">An example is to apply XSL transformation to XML data.</span></span> <span data-ttu-id="52a32-110">또는 XML을 하나 이상의 관리 클래스로 역직렬화하고 관리 코드를 사용하여 작업할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52a32-110">Alternatively, you can deserialize the XML into one or more managed classes and operate on them by using managed code.</span></span>  
  
-   <span data-ttu-id="52a32-111">비즈니스 요구에 맞게 XML 열에서 처리를 시작하는 Transact-SQL 저장 프로시저와 함수를 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52a32-111">You can write Transact-SQL stored procedures and functions that start the processing on the XML column for your business needs.</span></span>  
  
## <a name="example-applying-xsl-transformation"></a><span data-ttu-id="52a32-112">예제: XSL 변환 적용</span><span class="sxs-lookup"><span data-stu-id="52a32-112">Example: Applying XSL Transformation</span></span>  
 <span data-ttu-id="52a32-113">**TransformXml()** `xml` 파일에 저장 된 데이터 형식 인스턴스 및 XSL 변환을 수락 하 고, XML 데이터에 변환을 적용 한 다음 변환 된 xml을 결과로 반환 하는 CLR 함수 TransformXml ()를 고려 합니다.</span><span class="sxs-lookup"><span data-stu-id="52a32-113">Consider a CLR function **TransformXml()** that accepts an `xml` data type instance and an XSL transformation stored in a file, applies the transformation to the XML data, and then returns the transformed XML in the result.</span></span> <span data-ttu-id="52a32-114">다음은 C#으로 작성된 기초 함수입니다.</span><span class="sxs-lookup"><span data-stu-id="52a32-114">Following is a skeleton function that is written in C#:</span></span>  
  
```  
public static SqlXml TransformXml (SqlXml XmlData, string xslPath) {  
   // Load XSL transformation  
   XslCompiledTransform xform = new XslCompiledTransform();  
   XPathDocument xslDoc = new XPathDocument (xslPath);  
   xform.Load(xslDoc);  
  
   // Load XML data   
   XPathDocument xDoc = new XPathDocument (XmlData.CreateReader());  
  
   // Return the transformed value  
   MemoryStream xsltResult = new MemoryStream();  
   xform.Transform(xDoc, null, xsltResult);  
   SqlXml retSqlXml = new SqlXml(xsltResult);  
   return (retSqlXml);  
}   
```  
  
 <span data-ttu-id="52a32-115">어셈블리를 등록하고 사용자 정의 [!INCLUDE[tsql](../../includes/tsql-md.md)] 함수를 만든 후 다음 쿼리에서와 같이 **TransformXml()** 에 해당하는 **SqlXslTransform()** 함수를 Transact-SQL로부터 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52a32-115">After the assembly is registered and a user-defined [!INCLUDE[tsql](../../includes/tsql-md.md)] function is created, **SqlXslTransform()** corresponding to **TransformXml()**, the function can be invoked from Transact-SQL as shown in the following query:</span></span>  
  
```  
SELECT SqlXslTransform (xCol, 'C:\MyFile\xsltransform.xsl')  
FROM    T  
WHERE  xCol.exist('/book/title/text()[contains(.,"custom")]') =1;  
```  
  
 <span data-ttu-id="52a32-116">쿼리 결과에는 변환된 XML의 행 집합이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="52a32-116">The query result contains a rowset of the transformed XML.</span></span>  
  
 <span data-ttu-id="52a32-117">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 의 CLR 통합은 XML 데이터를 테이블 또는 속성 승격으로 분해하고 System.Xml 네임스페이스에 있는 관리 클래스를 사용하여 XML 데이터를 쿼리할 수 있는 가능성을 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="52a32-117">The CLR integration into [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] expands the possibilities for decomposing XML data into tables or property promotion, and querying XML data by using managed classes in the System.Xml namespace.</span></span> <span data-ttu-id="52a32-118">자세한 내용은 [XML 데이터&#40;SQL Server&#41;](xml-data-sql-server.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="52a32-118">For more information, see [XML Data &#40;SQL Server&#41;](xml-data-sql-server.md).</span></span>  
  
  
