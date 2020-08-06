---
title: ASP.NET에서 중첩 FOR XML 쿼리 사용 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- FOR XML clause, nested FOR XML queries
- queries [XML in SQL Server], ASP.NET and
- nested FOR XML queries in ASP.NET
- ASP.NET [SQL Server]
ms.assetid: 691ac7dd-afc5-4760-932c-2b1dcd9394ed
author: rothja
ms.author: jroth
ms.openlocfilehash: 1218b4ad46f0d21d42ba480d68b29d7c39b03ea2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647547"
---
# <a name="use-nested-for-xml-queries-in-aspnet"></a><span data-ttu-id="819d4-102">ASP.NET에서 중첩 FOR XML 쿼리 사용</span><span class="sxs-lookup"><span data-stu-id="819d4-102">Use Nested FOR XML Queries in ASP.NET</span></span>
  <span data-ttu-id="819d4-103">이 예에서ASP.NET 애플리케이션은 SQL Server에서 저장 프로시저를 실행하여 브라우저에 XML을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="819d4-103">In this example, an ASP.NET application returns XML to a browser by executing a stored procedure in SQL Server.</span></span> <span data-ttu-id="819d4-104">저장 프로시저는 중첩 쿼리를 사용하여 XML을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="819d4-104">The stored procedure generates XML using nested queries.</span></span> <span data-ttu-id="819d4-105">유사한 SELECT 문은 [중첩 AUTO 모드 쿼리를 사용하여 형제 생성](generate-siblings-with-a-nested-auto-mode-query.md)항목에 설명되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="819d4-105">A similar SELECT statement is shown in the topic [Generating Siblings by Using a Nested AUTO Mode Query](generate-siblings-with-a-nested-auto-mode-query.md).</span></span> <span data-ttu-id="819d4-106">다음 예에서는 중첩 FOR XML 쿼리를 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에 요소 중심 XML을 생성하는 한 가지 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="819d4-106">This example demonstrates one way to use nested FOR XML queries to generate element-centric XML in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="example"></a><span data-ttu-id="819d4-107">예제</span><span class="sxs-lookup"><span data-stu-id="819d4-107">Example</span></span>  
  
```  
CREATE PROC GetSalesOrderInfo AS  
SELECT   
      (SELECT top 2 SalesOrderID, SalesPersonID, CustomerID,  
         (select top 3 SalesOrderID, ProductID, OrderQty, UnitPrice  
           from Sales.SalesOrderDetail  
            WHERE  SalesOrderDetail.SalesOrderID = SalesOrderHeader.SalesOrderID  
            FOR XML AUTO, TYPE)  
      FROM  Sales.SalesOrderHeader  
        WHERE SalesOrderHeader.SalesOrderID = SalesOrder.SalesOrderID  
      for xml auto, type),  
        (SELECT *   
         FROM  (SELECT SalesPersonID, EmployeeID  
              FROM Sales.SalesPerson, HumanResources.Employee  
              WHERE SalesPerson.SalesPersonID = Employee.EmployeeID) As SalesPerson  
         WHERE  SalesPerson.SalesPersonID = SalesOrder.SalesPersonID  
       FOR XML AUTO, TYPE, ELEMENTS)  
FROM (SELECT SalesOrderHeader.SalesOrderID, SalesOrderHeader.SalesPersonID  
      FROM Sales.SalesOrderHeader, Sales.SalesPerson  
      WHERE SalesOrderHeader.SalesPersonID = SalesPerson.SalesPersonID  
     ) as SalesOrder  
ORDER BY SalesOrder.SalesOrderID  
FOR XML AUTO, TYPE  
GO  
```  
  
 <span data-ttu-id="819d4-108">이 코드는 .aspx 애플리케이션입니다.</span><span class="sxs-lookup"><span data-stu-id="819d4-108">This is the .aspx application.</span></span> <span data-ttu-id="819d4-109">이 코드는 저장 프로시저를 실행하고 브라우저에 XML을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="819d4-109">It executes the stored procedure and returns XML in the browser:</span></span>  
  
```  
<%@LANGUAGE=C# Debug=true %>  
<%@import Namespace="System.Xml"%>  
<%@import namespace="System.Data.SqlClient" %><%  
Response.Expires = -1;  
Response.ContentType = "text/xml";  
%>  
  
<%  
using(System.Data.SqlClient.SqlConnection c = new System.Data.SqlClient.SqlConnection("Data Source=server;Database=AdventureWorks;Integrated Security=SSPI;"))  
using(System.Data.SqlClient.SqlCommand cmd = c.CreateCommand())  
{  
   cmd.CommandText = "GetSalesOrderInfo";  
   cmd.CommandType = CommandType.StoredProcedure;  
   cmd.Connection.Open();  
   System.Xml.XmlReader r = cmd.ExecuteXmlReader();  
   System.Xml.XmlTextWriter w = new System.Xml.XmlTextWriter(Response.Output);  
   w.WriteStartElement("Root");  
   r.MoveToContent();  
   while(! r.EOF)  
   {  
      w.WriteNode(r, true);  
   }  
   w.WriteEndElement();  
   w.Flush();  
}  
%>  
```  
  
##### <a name="to-test-the-application"></a><span data-ttu-id="819d4-110">애플리케이션을 테스트하려면</span><span class="sxs-lookup"><span data-stu-id="819d4-110">To test the application</span></span>  
  
1.  <span data-ttu-id="819d4-111">[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 데이터베이스에 저장 프로시저를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="819d4-111">Create the stored procedure in the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database.</span></span>  
  
2.  <span data-ttu-id="819d4-112">.aspx 애플리케이션을 c:\inetpub\wwwroot 디렉터리에 GetSalesOrderInfo.aspx로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="819d4-112">Save the .aspx application in the c:\inetpub\wwwroot directory (GetSalesOrderInfo.aspx).</span></span>  
  
3.  <span data-ttu-id="819d4-113">응용 프로그램을 실행 http://server/GetSalesOrderInfo.aspx) 합니다.</span><span class="sxs-lookup"><span data-stu-id="819d4-113">Execute the application (http://server/GetSalesOrderInfo.aspx).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="819d4-114">참고 항목</span><span class="sxs-lookup"><span data-stu-id="819d4-114">See Also</span></span>  
 [<span data-ttu-id="819d4-115">중첩 FOR XML 쿼리 사용</span><span class="sxs-lookup"><span data-stu-id="819d4-115">Use Nested FOR XML Queries</span></span>](use-nested-for-xml-queries.md)  
  
  
