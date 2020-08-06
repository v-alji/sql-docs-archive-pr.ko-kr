---
title: '예제: XMLTEXT 지시어 지정 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- XMLTEXT directive
ms.assetid: e78008ec-51e8-4fd1-b86f-1058a781de17
author: rothja
ms.author: jroth
ms.openlocfilehash: d14299ad3e989c6600434b857a650fbbddd7a590
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659853"
---
# <a name="example-specifying-the-xmltext-directive"></a><span data-ttu-id="61c03-102">예제: XMLTEXT 지시어 지정</span><span class="sxs-lookup"><span data-stu-id="61c03-102">Example: Specifying the XMLTEXT Directive</span></span>
  <span data-ttu-id="61c03-103">이 예에서는 EXPLICIT 모드를 사용하는 `SELECT` 문에서 `XMLTEXT` 지시어를 사용하여 오버플로 열의 데이터 주소를 지정하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="61c03-103">This example illustrates how data in the overflow column is addressed by using the `XMLTEXT` directive in a `SELECT` statement using EXPLICIT mode.</span></span>  
  
 <span data-ttu-id="61c03-104">`Person` 테이블을 검토해 보면</span><span class="sxs-lookup"><span data-stu-id="61c03-104">Consider the `Person` table.</span></span> <span data-ttu-id="61c03-105">이 테이블에는 XML 문서 중 사용되지 않은 부분을 저장하는 `Overflow` 열이 있는 것을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="61c03-105">This table has an `Overflow` column that stores the unconsumed part of the XML document.</span></span>  
  
```  
USE tempdb;  
GO  
CREATE TABLE Person(PersonID varchar(5), PersonName varchar(20), Overflow nvarchar(200));  
GO  
INSERT INTO Person VALUES   
    ('P1','Joe',N'<SomeTag attr1="data">content</SomeTag>')  
   ,('P2','Joe',N'<SomeTag attr2="data"/>')  
   ,('P3','Joe',N'<SomeTag attr3="data" PersonID="P">content</SomeTag>');  
```  
  
 <span data-ttu-id="61c03-106">이 쿼리는 `Person` 테이블로부터 열을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="61c03-106">This query retrieves columns from the `Person` table.</span></span> <span data-ttu-id="61c03-107">`Overflow` 열에 대해 *AttributeName* 은 지정되어 있지 않지만 범용 테이블 열 이름을 제공하는 중에 *directive* 가 `XMLTEXT` 로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="61c03-107">For the `Overflow` column, *AttributeName* is not specified, but *directive* is set to `XMLTEXT` as part of providing a universal table column name.</span></span>  
  
```  
SELECT 1 as Tag, NULL as parent,  
       PersonID as [Parent!1!PersonID],  
       PersonName as [Parent!1!PersonName],  
       Overflow as [Parent!1!!XMLTEST] -- No AttributeName; XMLTEXT directive  
FROM Person  
FOR XML EXPLICIT;  
```  
  
 <span data-ttu-id="61c03-108">결과 XML 문서에서 다음에 유의하십시오.</span><span class="sxs-lookup"><span data-stu-id="61c03-108">In the resulting XML document:</span></span>  
  
-   <span data-ttu-id="61c03-109">*AttributeName*이 `Overflow` 열에 대해 지정되어 있지 않고 `xmltext` 지시어가 지정되어 있기 때문에 <`Parent`> 요소의 특성이 묶는 <`overflow`> 요소의 특성 목록에 첨부됩니다.</span><span class="sxs-lookup"><span data-stu-id="61c03-109">Because *AttributeName* is not specified for the `Overflow` column and the `xmltext` directive is specified, the attributes in the <`overflow`> element are appended to the attribute list of the enclosing <`Parent`> element.</span></span>  
  
-   <span data-ttu-id="61c03-110"><`xmltext`> 요소의 `PersonID` 특성은 동일 요소 수준에서 검색된 `PersonID` 특성과 충돌하기 때문에 <`xmltext`> 요소의 특성은 `PersonID`가 NULL인 경우에도 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="61c03-110">Because the `PersonID`attribute in the <`xmltext`> element conflicts with the `PersonID` attribute retrieved on the same element level, the attribute in the <`xmltext`> element is ignored, even if `PersonID` is NULL.</span></span> <span data-ttu-id="61c03-111">특성은 일반적으로 오버플로의 동일한 이름의 특성에 우선합니다.</span><span class="sxs-lookup"><span data-stu-id="61c03-111">Generally, an attribute overrides an attribute of the same name in the overflow.</span></span>  
  
 <span data-ttu-id="61c03-112">다음은 결과입니다.</span><span class="sxs-lookup"><span data-stu-id="61c03-112">This is the result:</span></span>  
  
 `<Parent PersonID="P1" PersonName="Joe" attr1="data">content</Parent>`  
  
 `<Parent PersonID="P2" PersonName="Joe" attr2="data"></Parent>`  
  
 `<Parent PersonID="P3" PersonName="Joe" attr3="data">content</Parent>`  
  
 <span data-ttu-id="61c03-113">오버플로 데이터에 하위 요소가 있고 동일한 쿼리가 지정되는 경우에는 `Overflow` 열의 하위 요소들이 묶는 <`Parent`> 요소의 하위 요소로 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="61c03-113">If the overflow data has subelements and the same query is specified, the subelements in the `Overflow` column are added as the subelements of the enclosing <`Parent`> element.</span></span>  
  
 <span data-ttu-id="61c03-114">예를 들어 `Person` 열에 하위 요소가 있게 되도록 `Overflow` 테이블의 데이터를 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="61c03-114">For example, change the data in the `Person` table so that the `Overflow` column now has subelements.</span></span>  
  
```  
USE tempdb;  
GO  
TRUNCATE TABLE Person;  
GO  
INSERT INTO Person VALUES   
    ('P1','Joe',N'<SomeTag attr1="data">content</SomeTag>')  
   ,('P2','Joe',N'<SomeTag attr2="data"/>')  
    ,('P3','Joe',N'<SomeTag attr3="data" PersonID="P"><name>PersonName</name></SomeTag>');  
```  
  
 <span data-ttu-id="61c03-115">동일한 쿼리가 실행되는 경우에는 <`xmltext`> 요소의 하위 요소가, 묶는 <`Parent`> 요소의 하위 요소로 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="61c03-115">If the same query is executed, the subelements in the <`xmltext`> element are added as subelements of the enclosing <`Parent`> element:</span></span>  
  
```  
SELECT 1 as Tag, NULL as parent,  
       PersonID as [Parent!1!PersonID],  
       PersonName as [Parent!1!PersonName],  
       Overflow as [Parent!1!!XMLTEXT] -- no AttributeName, XMLTEXT directive  
FROM Person  
FOR XML EXPLICIT;  
```  
  
 <span data-ttu-id="61c03-116">다음은 결과입니다.</span><span class="sxs-lookup"><span data-stu-id="61c03-116">This is the result:</span></span>  
  
 `<Parent PersonID="P1" PersonName="Joe" attr1="data">content</Parent>`  
  
 `<Parent PersonID="P2" PersonName="Joe" attr2="data"></Parent>`  
  
 `<Parent PersonID="P3" PersonName="Joe" attr3="data">`  
  
 `<name>PersonName</name>`  
  
 `</Parent>`  
  
 <span data-ttu-id="61c03-117">*AttributeName*이 `xmltext` 지시어와 함께 지정된 경우 <`overflow`> 요소의 특성이 묶는 <`Parent`> 요소의 하위 요소에 대한 특성으로 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="61c03-117">If *AttributeName* is specified with the `xmltext` directive, the attributes of the <`overflow`> element are added as attributes of the subelements of the enclosing <`Parent`> element.</span></span> <span data-ttu-id="61c03-118">*AttributeName* 에 대해 지정 된 이름은 하위 요소의 이름이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="61c03-118">The name specified for *AttributeName* becomes the name of the subelement.</span></span>  
  
 <span data-ttu-id="61c03-119">이 쿼리에서 *AttributeName*<`overflow`>는 지시문과 함께 지정 됩니다 `xmltext` .</span><span class="sxs-lookup"><span data-stu-id="61c03-119">In this query, *AttributeName*, <`overflow`>, is specified together with the `xmltext` directive:</span></span>  
  
```  
SELECT 1 as Tag, NULL as parent,  
       PersonID as [Parent!1!PersonID],  
       PersonName as [Parent!1!PersonName],  
       Overflow as [Parent!1!overflow!XMLTEXT] -- Overflow is AttributeName  
                      -- XMLTEXT is a directive  
FROM Person  
FOR XML EXPLICIT  
```  
  
 <span data-ttu-id="61c03-120">다음은 결과입니다.</span><span class="sxs-lookup"><span data-stu-id="61c03-120">This is the result:</span></span>  
  
 `<Parent PersonID="P1" PersonName="Joe">`  
  
 `<overflow attr1="data">content</overflow>`  
  
 `</Parent>`  
  
 `<Parent PersonID="P2" PersonName="Joe">`  
  
 `<overflow attr2="data" />`  
  
 `</Parent>`  
  
 `<Parent PersonID="P3" PersonName="Joe">`  
  
 `<overflow attr3="data" PersonID="P">`  
  
 `<name>PersonName</name>`  
  
 `</overflow>`  
  
 `</Parent>`  
  
 <span data-ttu-id="61c03-121">이 쿼리 요소에서는 *지시어와 함께 지정됩니다.* 가 `PersonName` 특성에 대해 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="61c03-121">In this query element, *directive* is specified for `PersonName` attribute.</span></span> <span data-ttu-id="61c03-122">그 결과 `PersonName`이 묶는 <`Parent`> 요소의 하위 요소로 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="61c03-122">This results in `PersonName` being added as a subelement of the enclosing <`Parent`> element.</span></span> <span data-ttu-id="61c03-123"><`xmltext`>의 특성은 계속해서 묶는 <`Parent`> 요소에 첨부됩니다.</span><span class="sxs-lookup"><span data-stu-id="61c03-123">The attributes of the <`xmltext`> are still appended to the enclosing <`Parent`> element.</span></span> <span data-ttu-id="61c03-124"><`overflow`> 요소인 하위 요소의 내용은 묶는 <`Parent`> 요소의 다른 하위 요소 앞에 놓입니다.</span><span class="sxs-lookup"><span data-stu-id="61c03-124">The contents of the <`overflow`> element, subelements, are prepended to the other subelements of the enclosing <`Parent`> elements.</span></span>  
  
```  
SELECT 1      AS Tag, NULL as parent,  
       PersonID   AS [Parent!1!PersonID],  
       PersonName AS [Parent!1!PersonName!element], -- element directive  
       Overflow   AS [Parent!1!!XMLTEXT]  
FROM Person  
FOR XML EXPLICIT;  
```  
  
 <span data-ttu-id="61c03-125">다음은 결과입니다.</span><span class="sxs-lookup"><span data-stu-id="61c03-125">This is the result:</span></span>  
  
 `<Parent PersonID="P1" attr1="data">content<PersonName>Joe</PersonName>`  
  
 `</Parent>`  
  
 `<Parent PersonID="P2" attr2="data">`  
  
 `<PersonName>Joe</PersonName>`  
  
 `</Parent>`  
  
 `<Parent PersonID="P3" attr3="data">`  
  
 `<name>PersonName</name>`  
  
 `<PersonName>Joe</PersonName>`  
  
 `</Parent>`  
  
 <span data-ttu-id="61c03-126">`XMLTEXT` 열 데이터의 경우 루트 요소에 특성이 있으면 이 특성은 XML 데이터 스키마에 표시되지 않고 MSXML 파서는 결과 XML 문서 조각의 유효성을 검사하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="61c03-126">If the `XMLTEXT` column data contains attributes on the root element, these attributes are not shown in the XML data schema and the MSXML parser does not validate the resulting XML document fragment.</span></span> <span data-ttu-id="61c03-127">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="61c03-127">For example:</span></span>  
  
```  
SELECT 1 AS Tag,  
       0 ASParent,  
       N'<overflow a="1"/>' AS 'overflow!1!!xmltext'  
FOR XML EXPLICIT, xmldata;  
```  
  
 <span data-ttu-id="61c03-128">다음은 결과입니다.</span><span class="sxs-lookup"><span data-stu-id="61c03-128">This is the result.</span></span> <span data-ttu-id="61c03-129">반환된 스키마에서는 오버플로 특성 `a` 가 스키마에서 손실됩니다.</span><span class="sxs-lookup"><span data-stu-id="61c03-129">Note that in the returned schema, the overflow attribute `a` is missing from the schema:</span></span>  
  
 `<Schema name="Schema2"`  
  
 `xmlns="urn:schemas-microsoft-com:xml-data"`  
  
 `xmlns:dt="urn:schemas-microsoft-com:datatypes">`  
  
 `<ElementType name="overflow" content="mixed" model="open">`  
  
 `</ElementType>`  
  
 `</Schema>`  
  
 `<overflow xmlns="x-schema:#Schema2" a="1">`  
  
 `</overflow>`  
  
## <a name="see-also"></a><span data-ttu-id="61c03-130">참고 항목</span><span class="sxs-lookup"><span data-stu-id="61c03-130">See Also</span></span>  
 [<span data-ttu-id="61c03-131">FOR XML에서 EXPLICIT 모드 사용</span><span class="sxs-lookup"><span data-stu-id="61c03-131">Use EXPLICIT Mode with FOR XML</span></span>](use-explicit-mode-with-for-xml.md)  
  
  
