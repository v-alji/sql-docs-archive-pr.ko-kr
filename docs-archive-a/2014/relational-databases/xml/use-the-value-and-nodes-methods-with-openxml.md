---
title: OPENXML에서 value() 및 nodes() 메서드 사용 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- OpenXML method [XML in SQL Server]
- value method [XML in SQL Server]
- nodes method [XML in SQL Server]
ms.assetid: c73dbe55-d685-42eb-b0ee-9f3c5b9d97f3
author: rothja
ms.author: jroth
ms.openlocfilehash: 5dccf5a7ef626d1f1a42d011d22ba77807b34eba
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738031"
---
# <a name="use-the-value-and-nodes-methods-with-openxml"></a><span data-ttu-id="15299-102">OPENXML에서 value() 및 nodes() 사용</span><span class="sxs-lookup"><span data-stu-id="15299-102">Use the value() and nodes() Methods with OPENXML</span></span>
  <span data-ttu-id="15299-103">SELECT 절에서 데이터 형식에 여러 **value ()** 메서드 `xml` 를 사용 **SELECT** 하 여 추출 된 값의 행 집합을 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15299-103">You can use multiple **value()** methods on `xml` data type in a **SELECT** clause to generate a rowset of extracted values.</span></span> <span data-ttu-id="15299-104">**nodes()** 메서드는 추가 쿼리에 사용할 수 있는 선택된 각 노드에 대해 내부 참조를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="15299-104">The **nodes()** method yields an internal reference for each selected node that can be used for additional query.</span></span> <span data-ttu-id="15299-105">**nodes()** 메서드와 **value()** 메서드를 조합하면 일부 행이 있고 해당 생성 시 사용된 경로 식이 복잡한 경우 행 집합을 더욱 효율적으로 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15299-105">The combination of the **nodes()** and **value()** methods can be more efficient in generating the rowset when it has several columns and, perhaps, when the path expressions used in its generation are complex.</span></span>  
  
 <span data-ttu-id="15299-106">**Nodes ()** 메서드는 특정 데이터 형식의 인스턴스를 생성 하며 각 인스턴스는 `xml` 서로 다른 선택 된 노드로 컨텍스트를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="15299-106">The **nodes()** method yields instances of a special `xml` data type, each of which has its context set to a different selected node.</span></span> <span data-ttu-id="15299-107">이러한 종류의 XML 인스턴스는 **query()** , **value()** , **nodes()** 및 **exist()** 메서드를 지원하며 **count(\*)** 집계에 사용될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15299-107">This kind of XML instance supports **query()**, **value()**, **nodes()**, and **exist()** methods and can be used in **count(\*)** aggregations.</span></span> <span data-ttu-id="15299-108">다른 용도로 사용하면 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="15299-108">All other uses cause an error.</span></span>  
  
## <a name="example-using-nodes"></a><span data-ttu-id="15299-109">예제: nodes() 사용</span><span class="sxs-lookup"><span data-stu-id="15299-109">Example: Using nodes()</span></span>  
 <span data-ttu-id="15299-110">저자의 성과 이름을 추출한다고 가정해 보십시오. 이때 이름은 "David"가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="15299-110">Assume that you want to extract the first and last names of authors, and the first name is not "David".</span></span> <span data-ttu-id="15299-111">또한 이 정보를 FirstName 및 LastName의 두 열이 포함된 행 집합으로 추출합니다.</span><span class="sxs-lookup"><span data-stu-id="15299-111">Additionally, you want to extract this information as a rowset that contains two columns, FirstName and LastName.</span></span> <span data-ttu-id="15299-112">**nodes()** 및 **value()** 메서드를 사용하면 다음과 같이 이 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15299-112">By using **nodes()** and **value()** methods, you can accomplish this as shown in the following:</span></span>  
  
```  
SELECT nref.value('(first-name/text())[1]', 'nvarchar(50)') FirstName,  
       nref.value('(last-name/text())[1]', 'nvarchar(50)') LastName  
FROM   T CROSS APPLY xCol.nodes('//author') AS R(nref)  
WHERE  nref.exist('first-name[. != "David"]') = 1  
```  
  
 <span data-ttu-id="15299-113">이 예에서 `nodes('//author')` 는 각 XML 인스턴스에 대한 `<author>` 요소의 참조 행 집합을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="15299-113">In this example, `nodes('//author')` yields a rowset of references to `<author>` elements for each XML instance.</span></span> <span data-ttu-id="15299-114">작성자의 성과 이름은 이러한 참조에 대해 **value()** 메서드를 평가하여 얻습니다.</span><span class="sxs-lookup"><span data-stu-id="15299-114">The first and last names of authors are obtained by evaluating **value()** methods relative to those references.</span></span>  
  
 <span data-ttu-id="15299-115">SQL Server 2000은 **OpenXml()** 을 사용하여 XML 인스턴스로부터 행 집합을 생성하는 기능을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="15299-115">SQL Server 2000 provides the capability for generating a rowset from an XML instance by using **OpenXml()**.</span></span> <span data-ttu-id="15299-116">행 집합에 대한 관계형 스키마를 지정하고 XML 인스턴스 내의 값이 행 집합의 열로 매핑되는 방식을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15299-116">You can specify the relational schema for the rowset and how values inside the XML instance map to columns in the rowset.</span></span>  
  
## <a name="example-using-openxml-on-the-xml-data-type"></a><span data-ttu-id="15299-117">예제: xml 데이터 형식에서 OpenXml() 사용</span><span class="sxs-lookup"><span data-stu-id="15299-117">Example: Using OpenXml() on the xml Data Type</span></span>  
 <span data-ttu-id="15299-118">다음에 표시된 것과 같이 **OpenXml()** 을 사용하여 이전 예의 쿼리를 다시 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15299-118">The query can be rewritten from the previous example by using **OpenXml()** as shown in the following.</span></span> <span data-ttu-id="15299-119">이러한 작업은 각 XML 인스턴스를 XML 변수로 읽고 OpenXML을 여기에 적용하는 커서를 만들어서 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="15299-119">This is done by creating a cursor that reads each XML instance into an XML variable and then applies OpenXML to it:</span></span>  
  
```  
DECLARE name_cursor CURSOR  
FOR  
   SELECT xCol   
   FROM   T  
OPEN name_cursor  
DECLARE @xmlVal XML  
DECLARE @idoc int  
FETCH NEXT FROM name_cursor INTO @xmlVal  
  
WHILE (@@FETCH_STATUS = 0)  
BEGIN  
   EXEC sp_xml_preparedocument @idoc OUTPUT, @xmlVal  
   SELECT   *  
   FROM   OPENXML (@idoc, '//author')  
          WITH (FirstName  varchar(50) 'first-name',  
                LastName   varchar(50) 'last-name') R  
   WHERE  R.FirstName != 'David'  
  
   EXEC sp_xml_removedocument @idoc  
   FETCH NEXT FROM name_cursor INTO @xmlVal  
END  
CLOSE name_cursor  
DEALLOCATE name_cursor   
```  
  
 <span data-ttu-id="15299-120">**OpenXml()** 은 메모리 내 표현을 만들고 쿼리 프로세서 대신 작업 테이블을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="15299-120">**OpenXml()** creates an in-memory representation and uses work tables instead of the query processor.</span></span> <span data-ttu-id="15299-121">이 함수는 XQuery 엔진 대신 MSXML 버전 3.0의 XPath 버전 1.0 프로세서를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="15299-121">It relies on the XPath version 1.0 processor of MSXML version 3.0 instead of the XQuery engine.</span></span> <span data-ttu-id="15299-122">작업 테이블은 동일 XML 인스턴스에 있는 경우에도 **OpenXml()** 에 대한 여러 호출 간에 공유되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="15299-122">The work tables are not shared among multiple calls to **OpenXml()**, even on the same XML instance.</span></span> <span data-ttu-id="15299-123">이 때문에 확장성이 제한됩니다.</span><span class="sxs-lookup"><span data-stu-id="15299-123">This limits its scalability.</span></span> <span data-ttu-id="15299-124">**OpenXml()** 을 사용하면 WITH 절이 지정되지 않은 경우 XML 데이터에 대한 Edge 테이블 형식에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15299-124">**OpenXml()** allows you to access an edge table format for the XML data when the WITH clause is not specified.</span></span> <span data-ttu-id="15299-125">또한 별개의 "오버플로" 열에서 남아 있는 XML 값을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15299-125">Also, it allows you to use the remaining XML value in a separate, "overflow" column.</span></span>  
  
 <span data-ttu-id="15299-126">**nodes()** 및 **value()** 함수 조합은 XML 인덱스를 효율적으로 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="15299-126">The combination of **nodes()** and **value()** functions uses XML indexes effectively.</span></span> <span data-ttu-id="15299-127">그 결과 이러한 조합은 **OpenXml**보다 많은 확장성을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="15299-127">As a result, this combination can exhibit more scalability than **OpenXml**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15299-128">참고 항목</span><span class="sxs-lookup"><span data-stu-id="15299-128">See Also</span></span>  
 [<span data-ttu-id="15299-129">OPENXML&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="15299-129">OPENXML &#40;SQL Server&#41;</span></span>](openxml-sql-server.md)  
  
  
