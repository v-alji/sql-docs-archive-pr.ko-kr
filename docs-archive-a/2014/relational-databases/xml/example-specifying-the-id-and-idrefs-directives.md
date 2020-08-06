---
title: '예제: ID 및 IDREFS 지시어 지정 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- IDREFS directive
- ID directive
ms.assetid: 99b9f0d8-ecbb-4225-859f-881066c09785
author: rothja
ms.author: jroth
ms.openlocfilehash: c21ba1bd19691014f179801421322970a3dd6dd6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659858"
---
# <a name="example-specifying-the-id-and-idrefs-directives"></a><span data-ttu-id="1d563-102">예제: ID 및 IDREFS 지시어 지정</span><span class="sxs-lookup"><span data-stu-id="1d563-102">Example: Specifying the ID and IDREFS Directives</span></span>
  <span data-ttu-id="1d563-103">요소 특성을 `ID` 유형의 특성으로 지정한 다음 `IDREFS` 특성을 사용하여 이 특성을 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1d563-103">An element attribute can be specified as an `ID` type attribute, and the `IDREFS` attribute can then be used to refer to it.</span></span> <span data-ttu-id="1d563-104">이러한 방식은 문서 간 연결을 설정하며 관계형 데이터베이스의 기본 키 및 외래 키 관계와 비슷합니다.</span><span class="sxs-lookup"><span data-stu-id="1d563-104">This enables intra-document links and is similar to the primary key and foreign key relationships in relational databases.</span></span>  
  
 <span data-ttu-id="1d563-105">이 예에서는 `ID` 및 `IDREFS` 지시어를 사용하여 `ID` 및 `IDREFS` 유형의 특성을 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="1d563-105">This example illustrates how the `ID` and `IDREFS` directives can be used to create attributes of `ID` and `IDREFS` types.</span></span> <span data-ttu-id="1d563-106">ID는 정수 값일 수 없기 때문에 이 예에서는 ID 값이 변환됩니다.</span><span class="sxs-lookup"><span data-stu-id="1d563-106">Because IDs cannot be integer values, the ID values in this example are converted.</span></span> <span data-ttu-id="1d563-107">즉, 다른 유형으로 캐스팅됩니다.</span><span class="sxs-lookup"><span data-stu-id="1d563-107">In other words, they are type casted.</span></span> <span data-ttu-id="1d563-108">ID 값에는 접두사가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="1d563-108">Prefixes are used for the ID values.</span></span>  
  
 <span data-ttu-id="1d563-109">다음과 같이 XML을 생성한다고 가정해 보십시오.</span><span class="sxs-lookup"><span data-stu-id="1d563-109">Assume that you want to construct XML as shown in the following:</span></span>  
  
```  
<Customer CustomerID="C1" SalesOrderIDList=" O11 O22 O33..." >  
    <SalesOrder SalesOrderID="O11" OrderDate="..." />  
    <SalesOrder SalesOrderID="O22" OrderDate="..." />  
    <SalesOrder SalesOrderID="O33" OrderDate="..." />  
    ...  
</Customer>  
```  
  
 <span data-ttu-id="1d563-110">< `SalesOrderIDList` > 요소의 `Customer` 특성은 < `SalesOrderID` > 요소의 `SalesOrder` 특성을 참조하는 다중 값 특성입니다.</span><span class="sxs-lookup"><span data-stu-id="1d563-110">The `SalesOrderIDList` attribute of the < `Customer` > element is a multivalued attribute that refers to the `SalesOrderID` attribute of the < `SalesOrder` > element.</span></span> <span data-ttu-id="1d563-111">이 연결을 구성하려면 `SalesOrderID` 특성이 `ID` 유형으로 선언되어야 하며 <`Customer`> 요소의 `SalesOrderIDList` 특성이 `IDREFS` 유형으로 선언되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1d563-111">To establish this link, the `SalesOrderID` attribute must be declared of `ID` type, and the `SalesOrderIDList` attribute of the < `Customer`> element must be declared of `IDREFS` type.</span></span> <span data-ttu-id="1d563-112">한 고객이 여러 개의 주문을 요청할 수 있으므로 `IDREFS` 유형이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="1d563-112">Because a customer can request several orders, the `IDREFS` type is used.</span></span>  
  
 <span data-ttu-id="1d563-113">`IDREFS` 유형의 요소에는 또한 두 개 이상의 값이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="1d563-113">Elements of `IDREFS` type also have more than one value.</span></span> <span data-ttu-id="1d563-114">따라서 같은 태그, 부모 및 키 열 정보를 다시 사용하는 별개의 SELECT 절을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1d563-114">Therefore, you have to use a separate select clause that will reuse the same tag, parent, and key column information.</span></span> <span data-ttu-id="1d563-115">그런 다음 `ORDER BY`에서 `IDREFS` 값을 구성하는 행 시퀀스가 해당 부모 요소 아래에 함께 표시되도록 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1d563-115">The `ORDER BY` then has to ensure that the sequence of rows that make up the `IDREFS` values appears grouped together under their parent element.</span></span>  
  
 <span data-ttu-id="1d563-116">이 쿼리는 원하는 XML을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="1d563-116">This is the query that produces the XML you want.</span></span> <span data-ttu-id="1d563-117">이 쿼리는 `ID` 및 `IDREFS` 지시어를 사용하여 열 이름(`SalesOrder!2!SalesOrderID!ID`, `Customer!1!SalesOrderIDList!IDREFS`)에 있는 유형을 덮어씁니다.</span><span class="sxs-lookup"><span data-stu-id="1d563-117">The query uses the `ID` and `IDREFS` directives to overwrite the types in the column names (`SalesOrder!2!SalesOrderID!ID`, `Customer!1!SalesOrderIDList!IDREFS`).</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
SELECT  1 as Tag,  
        0 as Parent,  
        C.CustomerID       [Customer!1!CustomerID],  
        NULL               [Customer!1!SalesOrderIDList!IDREFS],  
        NULL               [SalesOrder!2!SalesOrderID!ID],  
        NULL               [SalesOrder!2!OrderDate]  
FROM   Sales.Customer C   
UNION ALL   
SELECT  1 as Tag,  
        0 as Parent,  
        C.CustomerID,  
        'O-'+CAST(SalesOrderID as varchar(10)),   
        NULL,  
        NULL  
FROM   Sales.Customer AS C  
INNER JOIN Sales.SalesOrderHeader AS SOH  
    ON  C.CustomerID = SOH.CustomerID  
UNION ALL  
SELECT 2 as Tag,  
       1 as Parent,  
        C.CustomerID,  
        NULL,  
        'O-'+CAST(SalesOrderID as varchar(10)),  
        OrderDate  
FROM   Sales.Customer AS C  
INNER JOIN Sales.SalesOrderHeader AS SOH  
    ON  C.CustomerID = SOH.CustomerIDORDER BY [Customer!1!CustomerID] ,  
         [SalesOrder!2!SalesOrderID!ID],  
         [Customer!1!SalesOrderIDList!IDREFS]  
FOR XML EXPLICIT;  
```  
  
## <a name="see-also"></a><span data-ttu-id="1d563-118">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1d563-118">See Also</span></span>  
 [<span data-ttu-id="1d563-119">FOR XML에서 EXPLICIT 모드 사용</span><span class="sxs-lookup"><span data-stu-id="1d563-119">Use EXPLICIT Mode with FOR XML</span></span>](use-explicit-mode-with-for-xml.md)  
  
  
