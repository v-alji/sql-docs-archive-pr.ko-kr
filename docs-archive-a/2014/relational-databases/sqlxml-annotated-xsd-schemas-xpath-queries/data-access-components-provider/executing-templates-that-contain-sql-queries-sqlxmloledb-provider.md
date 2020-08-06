---
title: SQL 쿼리를 포함 하는 템플릿 실행 (SQLXMLOLEDB 공급자) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- templates [SQLXML]
- SQLXMLOLEDB Provider, executing template files
- templates [SQLXML], SQL queries
- XML templates [SQLXML]
- SQL queries [SQLXML]
ms.assetid: ff2bc36f-e3fb-4d8f-8e3a-2680a39eda11
author: rothja
ms.author: jroth
ms.openlocfilehash: c3d3bc340612286e211d85f52a3d914d1d1b6b9f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652032"
---
# <a name="executing-templates-that-contain-sql-queries-sqlxmloledb-provider"></a><span data-ttu-id="f8d87-102">SQL 쿼리를 포함하는 템플릿 실행(SQLXMLOLEDB 공급자)</span><span class="sxs-lookup"><span data-stu-id="f8d87-102">Executing Templates That Contain SQL Queries (SQLXMLOLEDB Provider)</span></span>
  <span data-ttu-id="f8d87-103">이 예제에서는 SQLXMLOLEDB 공급자별 속성 Clientside-by-side Xml을 사용 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="f8d87-103">This example illustrates the use of the SQLXMLOLEDB Provider-specific property ClientSideXML.</span></span> <span data-ttu-id="f8d87-104">이 클라이언트 쪽 ADO 예제 애플리케이션에서는 SQL 쿼리로 구성된 XML 템플릿을 서버에서 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="f8d87-104">In this client-side ADO sample application, an XML template that consists of an SQL query is executed on the server.</span></span>  
  
 <span data-ttu-id="f8d87-105">ClientSideXML 속성이 True로 설정 되어 있기 때문에 FOR XML 절이 없는 SELECT 문이 서버에 전송 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f8d87-105">Because the ClientSideXML property is set to True, the SELECT statement without the FOR XML clause is sent to the server.</span></span> <span data-ttu-id="f8d87-106">서버는 쿼리를 실행하고 클라이언트로 행 집합을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="f8d87-106">The server executes the query and returns a rowset to the client.</span></span> <span data-ttu-id="f8d87-107">그러면 클라이언트에서는 행 집합에 FOR XML 변환을 적용하여 XML 문서를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="f8d87-107">The client then applies the FOR XML transformation to the rowset and produces an XML document.</span></span>  
  
 <span data-ttu-id="f8d87-108">Xml 템플릿은 생성 되는 XML 문서에 대해 단일 최상위 루트 요소 ()를 제공 \<ROOT> 하므로 xml 루트 속성이 제공 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f8d87-108">The XML template provides a single top-level root element (\<ROOT>) for the XML document that is generated; therefore, the xml root property is not provided.</span></span>  
  
 <span data-ttu-id="f8d87-109">XML 템플릿을 실행하려면 언어 {5d531cb2-e6ed-11d2-b252-00c04f681b71}을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f8d87-109">To execute XML templates, the dialect {5d531cb2-e6ed-11d2-b252-00c04f681b71} must be specified.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f8d87-110">코드에서 연결 문자열에 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인스턴스의 이름을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f8d87-110">In the code, you must provide the name of the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in the connection string.</span></span> <span data-ttu-id="f8d87-111">또한 이 예에서는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client(SQLNCLI11)를 데이터 공급자로 사용하도록 지정하고 있으며 이를 위해서는 추가 네트워크 클라이언트 소프트웨어가 설치되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f8d87-111">Also, this example specifies the use of the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client (SQLNCLI11) for the data provider which requires additional network client software to be installed.</span></span> <span data-ttu-id="f8d87-112">자세한 내용은 [SQL Server Native Client에 대 한 시스템 요구 사항](../../native-client/system-requirements-for-sql-server-native-client.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f8d87-112">For more information, see [System Requirements for SQL Server Native Client](../../native-client/system-requirements-for-sql-server-native-client.md).</span></span>  
  
```  
Option Explicit  
  
Sub Main()  
  Dim oTestStream As New ADODB.Stream  
  Dim oTestConnection As New ADODB.Connection  
  Dim oTestCommand As New ADODB.Command  
  oTestConnection.Open "Provider=SQLXMLOLEDB.4.0;Data Provider=SQLNCLI11;Data Source=SqlServerName;Initial Catalog=AdventureWorks;Integrated Security=SSPI;"  
  
  Set oTestCommand.ActiveConnection = oTestConnection  
  oTestCommand.Properties("ClientSideXML") = True  
  oTestCommand.CommandText = "<ROOT xmlns:sql='urn:schemas-microsoft-com:xml-sql'> " & _  
        " <sql:query> " & _  
        "   SELECT TOP 10 FirstName, LastName FROM Person.Contact FOR XML AUTO " & _  
        "   </sql:query> " & _  
        " </ROOT> "  
  oTestStream.Open  
  ' You need the dialect if you are executing   
  ' XML templates (not for SQL queries).  
  oTestCommand.Dialect = "{5d531cb2-e6ed-11d2-b252-00c04f681b71}"  
  oTestCommand.Properties("Output Stream").Value = oTestStream  
  oTestCommand.Execute , , adExecuteStream  
  
  oTestStream.Position = 0  
  oTestStream.Charset = "utf-8"  
  Debug.Print oTestStream.ReadText(adReadAll)  
End Sub  
  
Sub Form_Load()  
  Main  
End Sub  
```  
  
  
