---
title: XPath 쿼리 실행 (SQLXMLOLEDB 공급자) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- SQLXMLOLEDB Provider, executing XPath queries
- queries [SQLXML], SQLXMLOLEDB Provider
- Base Path property
- XPath queries [SQLXML], SQLXMLOLEDB Provider
- Mapping Schema property
ms.assetid: 19063222-dc9c-48ae-a55f-778103674a9e
author: rothja
ms.author: jroth
ms.openlocfilehash: 667bc8dfd95c37c0a10c0bc68f3007e7d04533e6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87732480"
---
# <a name="executing-xpath-queries-sqlxmloledb-provider"></a><span data-ttu-id="ac24a-102">XPath 쿼리 실행(SQLXMLOLEDB 공급자)</span><span class="sxs-lookup"><span data-stu-id="ac24a-102">Executing XPath Queries (SQLXMLOLEDB Provider)</span></span>
  <span data-ttu-id="ac24a-103">이 예에서는 다음 SQLXMLOLEDB 공급자별 속성을 사용하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ac24a-103">This example illustrates the use of the following SQLXMLOLEDB Provider-specific properties:</span></span>  
  
-   `ClientSideXML`  
  
-   `Base Path`  
  
-   `Mapping Schema`  
  
 <span data-ttu-id="ac24a-104">이 예제 ADO 애플리케이션에서는 XPath 쿼리(루트)를 XSD 매핑 스키마(MySchema.xml)에 대해 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ac24a-104">In this sample ADO application, an XPath query (root) is specified against an XSD mapping schema (MySchema.xml).</span></span> <span data-ttu-id="ac24a-105">스키마에는 **\<Contacts>** **ContactID**, **FirstName**및 **LastName** 특성이 포함 된 요소가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac24a-105">The schema has a **\<Contacts>** element with **ContactID**, **FirstName**, and **LastName** attributes.</span></span> <span data-ttu-id="ac24a-106">이 스키마에서는 기본 매핑이 수행됩니다. 즉, 요소 이름은 같은 이름의 테이블에 매핑되고 단순 유형의 특성은 같은 이름의 열에 매핑됩니다.</span><span class="sxs-lookup"><span data-stu-id="ac24a-106">In the schema, default mapping takes place: an element name maps to the table with the same name, and attributes of simple type map to the columns with the same names.</span></span>  
  
```  
<xsd:schema xmlns:xsd='http://www.w3.org/2001/XMLSchema'  
   xmlns:sql='urn:schemas-microsoft-com:mapping-schema'>  
 <xsd:element name= 'root' sql:is-constant='1'>   
    <xsd:complexType>  
       <xsd:sequence>  
         <xsd:element ref = 'Contacts'/>  
       </xsd:sequence>  
    </xsd:complexType>  
  </xsd:element>  
  <xsd:element name='Contacts' sql:relation='Person.Contact'>   
     <xsd:complexType>  
          <xsd:attribute name='ContactID' type='xsd:integer' />  
          <xsd:attribute name='FirstName' type='xsd:string'/>   
          <xsd:attribute name='LastName' type='xsd:string' />   
     </xsd:complexType>  
   </xsd:element>  
</xsd:schema>  
```  
  
 <span data-ttu-id="ac24a-107">매핑 스키마 속성은 XPath 쿼리가 실행 되는 매핑 스키마를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="ac24a-107">The Mapping Schema property provides the mapping schema against which the XPath query is executed.</span></span> <span data-ttu-id="ac24a-108">매핑 스키마는 XSD 또는 XDR 스키마일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac24a-108">The mapping schema can be an XSD or XDR schema.</span></span> <span data-ttu-id="ac24a-109">기본 경로 속성은 매핑 스키마에 대 한 파일 경로를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="ac24a-109">The Base Path property provides the file path to the mapping schema.</span></span>  
  
 <span data-ttu-id="ac24a-110">ClientSideXML 속성이 True로 설정 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac24a-110">The ClientSideXML property is set to True.</span></span> <span data-ttu-id="ac24a-111">따라서 XML 문서는 클라이언트에서 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="ac24a-111">Therefore, the XML document is generated on the client.</span></span>  
  
 <span data-ttu-id="ac24a-112">애플리케이션에서 XPath 쿼리는 직접 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="ac24a-112">In the application, an XPath query is specified directly.</span></span> <span data-ttu-id="ac24a-113">따라서 XPath 언어 {ec2a4293-e898-11d2-b1b7-00c04f680c56}을 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ac24a-113">Therefore, the XPath dialect {ec2a4293-e898-11d2-b1b7-00c04f680c56} must be included.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ac24a-114">코드에서 연결 문자열에 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인스턴스의 이름을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ac24a-114">In the code, you must provide the name of the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in the connection string.</span></span> <span data-ttu-id="ac24a-115">또한 이 예에서는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client(SQLNCLI11)를 데이터 공급자로 사용하도록 지정하고 있으며 이를 위해서는 추가 네트워크 클라이언트 소프트웨어가 설치되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ac24a-115">Also, this example specifies the use of the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client (SQLNCLI11) for the data provider which requires additional network client software to be installed.</span></span> <span data-ttu-id="ac24a-116">자세한 내용은 [SQL Server Native Client에 대 한 시스템 요구 사항](../../native-client/system-requirements-for-sql-server-native-client.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ac24a-116">For more information, see [System Requirements for SQL Server Native Client](../../native-client/system-requirements-for-sql-server-native-client.md).</span></span>  
  
```  
Option Explicit  
Sub main()  
Dim oTestStream As New ADODB.Stream  
Dim oTestConnection As New ADODB.Connection  
Dim oTestCommand As New ADODB.Command  
  
oTestConnection.Open "provider=SQLXMLOLEDB.4.0;data provider=SQLNCLI11;data source=SqlServerName;initial catalog=AdventureWorks;Integrated Security= SSPI;"  
  
oTestCommand.ActiveConnection = oTestConnection  
oTestCommand.Properties("ClientSideXML") = True  
  
oTestCommand.CommandText = "root"  
oTestStream.Open  
oTestCommand.Dialect = "{ec2a4293-e898-11d2-b1b7-00c04f680c56}"  
oTestCommand.Properties("Output Stream").Value = oTestStream  
oTestCommand.Properties("Base Path").Value = "c:\Schemas\SQLXML4\XPathDirect\"  
oTestCommand.Properties("Mapping Schema").Value = "mySchema.xml"  
oTestCommand.Properties("Output Encoding") = "utf-8"  
oTestCommand.Execute , , adExecuteStream  
oTestStream.Position = 0  
oTestStream.Charset = "utf-8"  
Debug.Print oTestStream.ReadText(adReadAll)  
  
End Sub  
Sub Form_Load()  
 main  
End Sub  
```  
  
  
