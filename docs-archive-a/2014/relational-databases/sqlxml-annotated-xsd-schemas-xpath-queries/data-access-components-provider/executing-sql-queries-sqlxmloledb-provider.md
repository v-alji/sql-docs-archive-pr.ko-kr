---
title: SQL 쿼리 실행 (SQLXMLOLEDB Provider) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- queries [SQLXML], SQLXMLOLEDB Provider
- xml root property [SQLXML]
- SQLXMLOLEDB Provider, executing SQL queries
- SQL queries [SQLXML]
ms.assetid: 50334cf5-9c87-4c00-9beb-e08577c4fa82
author: rothja
ms.author: jroth
ms.openlocfilehash: a1e2cc87f90700e3b81a5a2ec3dd80f219a9b1d5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652746"
---
# <a name="executing-sql-queries-sqlxmloledb-provider"></a><span data-ttu-id="6ab60-102">SQL 쿼리 실행(SQLXMLOLEDB 공급자)</span><span class="sxs-lookup"><span data-stu-id="6ab60-102">Executing SQL Queries (SQLXMLOLEDB Provider)</span></span>
  <span data-ttu-id="6ab60-103">이 예에서는 다음 SQLXMLOLEDB 공급자별 속성을 사용하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="6ab60-103">This example illustrates the use of the following SQLXMLOLEDB Provider-specific properties:</span></span>  
  
-   <span data-ttu-id="6ab60-104">ClientSideXML</span><span class="sxs-lookup"><span data-stu-id="6ab60-104">ClientSideXML</span></span>  
  
-   <span data-ttu-id="6ab60-105">xml root</span><span class="sxs-lookup"><span data-stu-id="6ab60-105">xml root</span></span>  
  
 <span data-ttu-id="6ab60-106">이 클라이언트 쪽 ADO 예제 애플리케이션에서는 예제 SQL 쿼리가 클라이언트에서 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="6ab60-106">In this client-side ADO sample application, a simple SQL query is executed on the client.</span></span> <span data-ttu-id="6ab60-107">ClientSideXML 속성이 True로 설정 되어 있기 때문에 FOR XML 절이 없는 SELECT 문이 서버에 전송 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6ab60-107">Because the ClientSideXML property is set to True, the SELECT statement without the FOR XML clause is sent to the server.</span></span> <span data-ttu-id="6ab60-108">서버는 쿼리를 실행하고 클라이언트로 행 집합을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="6ab60-108">The server executes the query and returns a rowset to the client.</span></span> <span data-ttu-id="6ab60-109">그러면 클라이언트에서는 행 집합에 FOR XML 변환을 적용하여 XML 문서를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="6ab60-109">The client then applies the FOR XML transformation to the rowset and produces an XML document.</span></span>  
  
 <span data-ttu-id="6ab60-110">Xml root 속성은 생성 되는 XML 문서에 대해 단일 최상위 루트 요소를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ab60-110">The xml root property provides the single top-level root element for the XML document that is generated.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6ab60-111">코드에서 연결 문자열에 Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인스턴스의 이름을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ab60-111">In the code, you must provide the name of the instance of Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in the connection string.</span></span> <span data-ttu-id="6ab60-112">또한 이 예에서는 데이터 공급자에 대해 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client(SQLNCLI11)를 사용하도록 지정하는데, 이렇게 하려면 추가 네트워크 클라이언트를 설치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ab60-112">Also, this example specifies the use of the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client (SQLNCLI11) for the data provider, which requires additional network client software to be installed.</span></span> <span data-ttu-id="6ab60-113">자세한 내용은 [SQL Server Native Client에 대 한 시스템 요구 사항](../../native-client/system-requirements-for-sql-server-native-client.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="6ab60-113">For more information, see [System Requirements for SQL Server Native Client](../../native-client/system-requirements-for-sql-server-native-client.md).</span></span>  
  
```  
Option Explicit  
Sub main()  
Dim oTestStream As New ADODB.Stream  
Dim oTestConnection As New ADODB.Connection  
Dim oTestCommand As New ADODB.Command  
  
oTestConnection.Open "provider=SQLXMLOLEDB.4.0;data provider=SQLNCLI11;data source=SqlServerName;initial catalog=AdventureWorks;Integrated Security=SSPI ;"  
oTestCommand.ActiveConnection = oTestConnection  
oTestCommand.Properties("ClientSideXML") = True  
oTestCommand.CommandText = "SELECT TOP 10 FirstName, LastName FROM Person.Contact FOR XML AUTO"  
oTestStream.Open  
oTestCommand.Properties("Output Stream").Value = oTestStream  
oTestCommand.Properties("xml root") = "root"  
oTestCommand.Execute , , adExecuteStream  
  
oTestStream.Position = 0  
oTestStream.Charset = "utf-8"  
Debug.Print oTestStream.ReadText(adReadAll)  
End Sub  
Sub Form_Load()  
 main  
End Sub  
```  
  
  
