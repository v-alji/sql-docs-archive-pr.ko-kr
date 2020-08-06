---
title: 행 집합으로부터 XML을 생성하기 위해 FOR XML 사용 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- FOR XML clause, generating XML from rowsets
ms.assetid: d061c0f1-3de9-4ad1-bbca-ce45d064b6c8
author: rothja
ms.author: jroth
ms.openlocfilehash: dcf9feb4dab9ad1149ab433c9d9b4999c96c1cdd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743059"
---
# <a name="generate-xml-from-rowsets-with-for-xml"></a><span data-ttu-id="bbf86-102">행 집합으로부터 XML을 생성하기 위해 FOR XML 사용</span><span class="sxs-lookup"><span data-stu-id="bbf86-102">Generate XML from Rowsets with FOR XML</span></span>
  <span data-ttu-id="bbf86-103">`xml`New **type** 지시어를 사용 하 여 FOR XML을 사용 하 여 행 집합에서 데이터 형식 인스턴스를 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bbf86-103">You can generate an `xml` data type instance from a rowset by using FOR XML with the new **TYPE** directive.</span></span>  
  
 <span data-ttu-id="bbf86-104">결과는 `xml` 데이터 형식 열, 변수 또는 매개 변수에 할당 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bbf86-104">The result can be assigned to an `xml` data type column, variable, or parameter.</span></span> <span data-ttu-id="bbf86-105">또한 FOR XML은 계층적 구조를 생성하도록 중첩될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bbf86-105">Also, FOR XML can be nested to generate any hierarchical structure.</span></span> <span data-ttu-id="bbf86-106">이로 인해 FOR XML EXPLICIT보다 중첩된 FOR XML이 작성하기에 더욱 편리하지만 중첩이 많은 계층에서는 성능이 저하될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bbf86-106">This makes nested FOR XML much more convenient to write than FOR XML EXPLICIT, but it may not perform as well for deep hierarchies.</span></span> <span data-ttu-id="bbf86-107">FOR XML은 또한 새로운 PATH 모드를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="bbf86-107">FOR XML also introduces a new PATH mode.</span></span> <span data-ttu-id="bbf86-108">이 새로운 모드는 열 값이 나타나는 XML 트리의 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="bbf86-108">This new mode specifies the path in the XML tree where a column's value appears.</span></span>  
  
 <span data-ttu-id="bbf86-109">새로운 **FOR XML TYPE** 지시어를 사용하여 SQL 구문에서 관계형 데이터에 대해 읽기 전용 XML 뷰를 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bbf86-109">The new **FOR XML TYPE** directive can be used to define read-only XML views over relational data with SQL syntax.</span></span> <span data-ttu-id="bbf86-110">이 뷰는 다음 예에서와 같이 SQL 문과 포함된 XQuery에서 쿼리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bbf86-110">The view can be queried with SQL statements and embedded XQuery, as shown in the following example.</span></span> <span data-ttu-id="bbf86-111">또한 저장 프로시저에서 이러한 SQL 뷰를 참조할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bbf86-111">You can also refer to these SQL views in stored procedures.</span></span>  
  
## <a name="example-sql-view-returning-generated-xml-data-type"></a><span data-ttu-id="bbf86-112">예제: 생성된 xml 데이터 형식을 반환하는 SQL 뷰</span><span class="sxs-lookup"><span data-stu-id="bbf86-112">Example: SQL View Returning Generated xml Data Type</span></span>  
 <span data-ttu-id="bbf86-113">다음 SQL 뷰 정의는 XML 열로부터 검색된 관계형 열, pk 및 책 저자에 대해 XML 뷰를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="bbf86-113">The following SQL view definition creates an XML view over a relational column, pk, and book authors retrieved from an XML column:</span></span>  
  
```  
CREATE VIEW V (xmlVal) AS  
SELECT pk, xCol.query('/book/author')  
FROM   T  
FOR XML AUTO, TYPE  
```  
  
 <span data-ttu-id="bbf86-114">V 뷰에는 XML 유형의 단일 columnxmlVal이 있는 단일 행이 포함 되어 `.` 있으므로 일반 데이터 유형 인스턴스와 같이 쿼리할 수 있습니다 `xml` .</span><span class="sxs-lookup"><span data-stu-id="bbf86-114">The V view contains a single row with a single columnxmlVal of XML type`.` It can be queried like a regular `xml` data type instance.</span></span> <span data-ttu-id="bbf86-115">예를 들어 다음 쿼리는 이름이 "David"인 저자를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="bbf86-115">For example, the following query returns the author whose first name is "David":</span></span>  
  
```  
SELECT xmlVal.query('//author[first-name = "David"]')  
FROM   V  
```  
  
 <span data-ttu-id="bbf86-116">SQL 뷰 정의는 주석 지정 스키마를 사용하여 만든 XML 뷰와 일부 비슷합니다.</span><span class="sxs-lookup"><span data-stu-id="bbf86-116">SQL view definitions are somewhat similar to XML views that are created by using annotated schemas.</span></span> <span data-ttu-id="bbf86-117">하지만 여기에는 중요한 차이가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bbf86-117">However, there are important differences.</span></span> <span data-ttu-id="bbf86-118">SQL 뷰 정의는 읽기 전용이며 포함된 XQuery로 조작되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bbf86-118">The SQL view definition is read-only and must be manipulated with embedded XQuery.</span></span> <span data-ttu-id="bbf86-119">XML 뷰는 주석 지정 스키마를 사용하여 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="bbf86-119">The XML views are created by using annotated schema.</span></span> <span data-ttu-id="bbf86-120">또한 SQL 뷰는 XQuery 식을 적용하기 전에 XML 결과를 구체화하지만 XML 뷰의 XPath 쿼리는 기본 테이블에서 SQL 쿼리를 평가합니다.</span><span class="sxs-lookup"><span data-stu-id="bbf86-120">Additionally, the SQL view materializes the XML result before applying the XQuery expression, while the XPath queries on XML views evaluate SQL queries on the underlying tables.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bbf86-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="bbf86-121">See Also</span></span>  
 [<span data-ttu-id="bbf86-122">FOR XML&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="bbf86-122">FOR XML &#40;SQL Server&#41;</span></span>](for-xml-sql-server.md)  
  
  
