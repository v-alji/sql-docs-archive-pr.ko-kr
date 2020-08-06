---
title: XSL 변환 적용 (SQLXMLOLEDB 공급자) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- SQLXMLOLEDB Provider, applying XSL transformations
- applying XSL transformations [SQLXML]
- xsl property
- Base Path property
- XSL Transformations [SQLXML]
ms.assetid: cb5e41ab-dd20-4873-af20-f417bd1bbf6d
author: rothja
ms.author: jroth
ms.openlocfilehash: 7fbb427a95d9f2308bf65724758a4a1563b42575
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652033"
---
# <a name="applying-an-xsl-transformation-sqlxmloledb-provider"></a><span data-ttu-id="ac7e0-102">XSL 변환 적용(SQLXMLOLEDB 공급자)</span><span class="sxs-lookup"><span data-stu-id="ac7e0-102">Applying an XSL Transformation (SQLXMLOLEDB Provider)</span></span>
  <span data-ttu-id="ac7e0-103">이 예제 ADO 애플리케이션에서는 SQL 쿼리를 실행하고 결과에 XSL 변환을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="ac7e0-103">In this sample ADO application, an SQL query is executed, and an XSL transformation is applied to the result.</span></span> <span data-ttu-id="ac7e0-104">Clientside Xml 속성을 True로 설정 하면 클라이언트 쪽에서 행 집합의 처리가 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ac7e0-104">Setting the ClientSideXML property to True enforces the processing of the rowset on the client side.</span></span> <span data-ttu-id="ac7e0-105">이 예에서는 명령 언어가 {5d531cb2-e6ed-11d2-b252-00c04f681b71}로 설정되었는데 그 이유는 SQL 쿼리가 템플릿에 지정되었고, 템플릿을 실행하려면 이 명령 언어를 지정해야 하기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="ac7e0-105">The command dialect is set to {5d531cb2-e6ed-11d2-b252-00c04f681b71}, because the SQL query is specified in a template and this dialect must be specified when executing a template.</span></span> <span data-ttu-id="ac7e0-106">Xsl 속성은 변환을 적용 하는 데 사용할 XSL 파일을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ac7e0-106">The xsl property specifies the XSL file to use to apply the transformation.</span></span> <span data-ttu-id="ac7e0-107">기본 경로 속성의 값은 XSL 파일을 검색 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ac7e0-107">The value of Base Path property is used to search for the XSL file.</span></span> <span data-ttu-id="ac7e0-108">Xsl 속성의 값에 경로를 지정 하는 경우 경로는 기본 경로 속성에 지정 된 경로를 기준으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="ac7e0-108">If you specify a path in the value of the xsl property, the path is relative to the path that is specified in the Base Path property.</span></span>  
  
 <span data-ttu-id="ac7e0-109">이 예에서는 다음 SQLXMLOLEDB 공급자별 속성을 사용하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ac7e0-109">This example shows how to use the following SQLXMLOLEDB Provider-specific properties:</span></span>  
  
-   <span data-ttu-id="ac7e0-110">ClientSideXML</span><span class="sxs-lookup"><span data-stu-id="ac7e0-110">ClientSideXML</span></span>  
  
-   <span data-ttu-id="ac7e0-111">xsl</span><span class="sxs-lookup"><span data-stu-id="ac7e0-111">xsl</span></span>  
  
 <span data-ttu-id="ac7e0-112">이 클라이언트 쪽 ADO 예제 애플리케이션에서는 SQL 쿼리로 구성된 XML 템플릿을 서버에서 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="ac7e0-112">In this client-side ADO sample application, an XML template that consists of an SQL query is executed on the server.</span></span>  
  
 <span data-ttu-id="ac7e0-113">ClientSideXML 속성이 True로 설정 되어 있기 때문에 FOR XML 절이 없는 SELECT 문이 서버에 전송 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ac7e0-113">Because the ClientSideXML property is set to True, the SELECT statement without the FOR XML clause is sent to the server.</span></span> <span data-ttu-id="ac7e0-114">서버는 쿼리를 실행하고 클라이언트로 행 집합을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="ac7e0-114">The server executes the query and returns a rowset to the client.</span></span> <span data-ttu-id="ac7e0-115">그러면 클라이언트에서는 행 집합에 FOR XML 변환을 적용하여 XML 문서를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="ac7e0-115">The client then applies the FOR XML transformation to the rowset and produces the XML document.</span></span>  
  
 <span data-ttu-id="ac7e0-116">Xsl 속성은 응용 프로그램에서 지정 됩니다. 따라서 XSL 변환은 클라이언트에서 생성 되는 XML 문서에 적용 되 고 결과는 두 개의 열로 이루어진 테이블입니다.</span><span class="sxs-lookup"><span data-stu-id="ac7e0-116">The xsl property is specified in the application; therefore, the XSL transformation is applied to the XML document that is generated on the client, and the result is a two-column table.</span></span>  
  
 <span data-ttu-id="ac7e0-117">템플릿 명령을 실행 하려면 XML 템플릿 언어 {5d531cb2-e6ed-11d2-b252-00c04f681b71}-를 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ac7e0-117">To execute the template command, the XML template dialect - {5d531cb2-e6ed-11d2-b252-00c04f681b71} - must be specified.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ac7e0-118">코드에서 연결 문자열에 Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인스턴스의 이름을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ac7e0-118">In the code, you must provide the name of the instance of Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in the connection string.</span></span> <span data-ttu-id="ac7e0-119">또한 이 예에서는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client를 데이터 공급자로 사용하도록 지정하는데 이를 위해서는 추가 네트워크 클라이언트 소프트웨어가 설치되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ac7e0-119">Also, this example specifies the use of the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client for the data provider which requires additional network client software to be installed.</span></span> <span data-ttu-id="ac7e0-120">자세한 내용은 [SQL Server Native Client에 대 한 시스템 요구 사항](../../native-client/system-requirements-for-sql-server-native-client.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ac7e0-120">For more information, see [System Requirements for SQL Server Native Client](../../native-client/system-requirements-for-sql-server-native-client.md).</span></span>  
  
```  
Option Explicit  
Sub main()  
Dim oTestStream As New ADODB.Stream  
Dim oTestConnection As New ADODB.Connection  
Dim oTestCommand As New ADODB.Command  
oTestConnection.Open "provider=SQLXMLOLEDB.4.0;data provider=SQLNCLI11;data source=SqlServerName;initial catalog=AdventureWorks;Integrated Security=SSPI;"  
Set oTestCommand.ActiveConnection = oTestConnection  
oTestCommand.Properties("ClientSideXML") = True  
oTestCommand.CommandText = _  
        "<ROOT xmlns:sql='urn:schemas-microsoft-com:xml-sql' >" & _  
       " <sql:query> " & _  
        "   SELECT TOP 25 FirstName, LastName FROM Person.Contact FOR XML AUTO " & _  
        "   </sql:query> " & _  
        " </ROOT> "  
oTestStream.Open  
' You need the dialect if you are executing a template.  
oTestCommand.Dialect = "{5d531cb2-e6ed-11d2-b252-00c04f681b71}"  
oTestCommand.Properties("Output Stream").Value = oTestStream  
oTestCommand.Properties("Base Path").Value = "c:\Schemas\SQLXML4\ExecuteTemplateWithXSL\"  
oTestCommand.Properties("xsl").Value = "myxsl.xsl"  
oTestCommand.Execute , , adExecuteStream  
  
oTestStream.Position = 0  
oTestStream.Charset = "utf-8"  
Debug.Print oTestStream.ReadText(adReadAll)  
End Sub  
Sub Form_Load()  
 main  
End Sub  
```  
  
 <span data-ttu-id="ac7e0-121">다음은 XSL 템플릿입니다.</span><span class="sxs-lookup"><span data-stu-id="ac7e0-121">The XSL template follows.</span></span> <span data-ttu-id="ac7e0-122">이 XSL 템플릿을 적용하면 2열 테이블이 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="ac7e0-122">The result of applying this XSL template is a two-column table.</span></span>  
  
```  
<?xml version='1.0' encoding='UTF-8'?>            
 <xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0">   
  
    <xsl:template match = 'Person.Contact'>  
       <TR>  
         <TD><xsl:value-of select = '@FirstName' /></TD>  
         <TD><B><xsl:value-of select = '@LastName' /></B></TD>  
       </TR>  
    </xsl:template>  
    <xsl:template match = '/'>  
      <HTML>  
        <HEAD>  
           <STYLE>th { background-color: #CCCCCC }</STYLE>  
        </HEAD>  
        <BODY>  
         <TABLE border='1' style='width:300;'>  
           <TR><TH colspan='2'>Contacts</TH></TR>  
           <TR>  
              <TH >First name</TH>  
              <TH>Last name</TH>  
           </TR>  
           <xsl:apply-templates select = 'ROOT' />  
         </TABLE>  
        </BODY>  
      </HTML>  
    </xsl:template>  
</xsl:stylesheet>  
```  
  
  
