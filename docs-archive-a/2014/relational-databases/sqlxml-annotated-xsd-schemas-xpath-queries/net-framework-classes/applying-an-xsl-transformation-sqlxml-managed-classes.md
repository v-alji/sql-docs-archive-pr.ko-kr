---
title: XSL 변환 적용 (SQLXML 관리 되는 클래스) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- applying XSL transformations [SQLXML]
- Managed Classes [SQLXML], applying XSL transformations
- SQLXML Managed Classes, applying XSL transformations
- XSL Transformations [SQLXML]
ms.assetid: 8562043b-3e9f-41a3-bb41-92b9f14363c4
author: rothja
ms.author: jroth
ms.openlocfilehash: d3225d838db284e2a34ebd41edb109400d0b72f0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651573"
---
# <a name="applying-an-xsl-transformation-sqlxml-managed-classes"></a><span data-ttu-id="c41c3-102">XSL 변환 적용(SQLXML 관리되는 클래스)</span><span class="sxs-lookup"><span data-stu-id="c41c3-102">Applying an XSL Transformation (SQLXML Managed Classes)</span></span>
  <span data-ttu-id="c41c3-103">이 예에서는 AdventureWorks 데이터베이스를 대상으로 SQL 쿼리를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="c41c3-103">In this example, an SQL query is executed against the AdventureWorks database.</span></span> <span data-ttu-id="c41c3-104">그리고 쿼리 결과에 XSL 변환을 적용하여 직원의 이름과 성의 두 개 열로 이루어진 테이블을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="c41c3-104">The XSL transformation is applied to the query result to generate a two-column table of the employees' first and last names.</span></span>  
  
 <span data-ttu-id="c41c3-105">SqlXmlCommand 개체의 XslPath 속성은 XSL 파일 및 해당 디렉터리 경로를 지정 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c41c3-105">The XslPath property of the SqlXmlCommand object is used to specify the XSL file and its directory path.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c41c3-106">코드에서 연결 문자열에 Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인스턴스의 이름을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c41c3-106">In the code, you must provide the name of the instance of Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in the connection string.</span></span>  
  
```  
using System;  
using Microsoft.Data.SqlXml;  
using System.IO;  
class Test  
{  
      static string ConnString = "Provider=SQLOLEDB;Server=(local);database=AdventureWorks;Integrated Security=SSPI";  
      public static int testXSL()  
      {  
         //Stream strm;  
         SqlXmlCommand cmd = new SqlXmlCommand(ConnString);  
         cmd.CommandText = "SELECT TOP 20 FirstName, LastName FROM Person.Contact FOR XML AUTO";  
         cmd.XslPath = "MyXSL.xsl";  
         cmd.RootTag = "root";  
         using (Stream strm = cmd.ExecuteStream()){  
            using (StreamReader sr = new StreamReader(strm)){  
               Console.WriteLine(sr.ReadToEnd());  
            }  
        }  
         return 0;  
      }  
      public static int Main(String[] args)  
      {  
         testXSL();     
         return 0;  
      }  
   }  
```  
  
 <span data-ttu-id="c41c3-107">다음은 애플리케이션을 테스트하는 데 사용할 수 있는 XSL 스타일시트입니다.</span><span class="sxs-lookup"><span data-stu-id="c41c3-107">This is the XSL style sheet you can use to test the application:</span></span>  
  
```  
<?xml version='1.0' encoding='UTF-8'?>  
 <xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0">   
    <xsl:output method="html"/>  
    <xsl:template match = '*'>  
        <xsl:apply-templates />  
    </xsl:template>  
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
           <TR><TH >First name</TH><TH>Last name</TH></TR>  
           <xsl:apply-templates select = 'root' />  
         </TABLE>  
        </BODY>  
      </HTML>  
    </xsl:template>  
</xsl:stylesheet>  
```  
  
 <span data-ttu-id="c41c3-108">이 예를 테스트하려면 컴퓨터에 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework가 설치되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c41c3-108">To test this example, you must have the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework installed on your computer.</span></span>  
  
### <a name="to-test-the-application"></a><span data-ttu-id="c41c3-109">애플리케이션을 테스트하려면</span><span class="sxs-lookup"><span data-stu-id="c41c3-109">To test the application</span></span>  
  
1.  <span data-ttu-id="c41c3-110">XSL 스타일시트를 파일(MyXSL.xsl)로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="c41c3-110">Save the XSL style sheet in a file (MyXSL.xsl).</span></span>  
  
2.  <span data-ttu-id="c41c3-111">이 예에서 제공하는 C# 코드(DocSample.cs)를 스타일시트가 저장된 폴더와 같은 폴더에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="c41c3-111">Save the C# code (DocSample.cs) that is provided in this example in the same folder in which the style sheet is stored.</span></span>  
  
3.  <span data-ttu-id="c41c3-112">코드를 컴파일합니다.</span><span class="sxs-lookup"><span data-stu-id="c41c3-112">Compile the code.</span></span> <span data-ttu-id="c41c3-113">다음을 사용하여 명령 프롬프트에서 코드를 컴파일합니다.</span><span class="sxs-lookup"><span data-stu-id="c41c3-113">To compile the code at the command prompt, use:</span></span>  
  
    ```  
    csc /reference:Microsoft.Data.SqlXML.dll DocSample.cs  
    ```  
  
     <span data-ttu-id="c41c3-114">이렇게 하면 실행 파일(DocSample.exe)이 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="c41c3-114">This creates an executable (DocSample.exe).</span></span>  
  
4.  <span data-ttu-id="c41c3-115">명령 프롬프트에서 DocSample.exe를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="c41c3-115">At the command prompt, execute DocSample.exe.</span></span>  
  
## <a name="applying-an-xsl-transformation-in-the-net-framework"></a><span data-ttu-id="c41c3-116">.NET Framework에서 XSL 변환 적용</span><span class="sxs-lookup"><span data-stu-id="c41c3-116">Applying an XSL Transformation in the .NET Framework</span></span>  
 <span data-ttu-id="c41c3-117">앞서 설명한 것처럼 XSL 변환을 중간 계층에 적용하지 않고 클라이언트 쪽(.NET Framework 내부)에 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c41c3-117">Instead of applying an XSL transformation in the middle tier, as described previously, you can apply an XSL transformation on the client side (in the .NET Framework).</span></span> <span data-ttu-id="c41c3-118">다음의 수정된 C# 코드는 XSL 변환을 .NET Framework에 적용하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="c41c3-118">The following revised C# code shows how the XSL transformation is applied in the .NET Framework.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c41c3-119">코드에서 연결 문자열에 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인스턴스의 이름을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c41c3-119">In the code, you must provide the name of the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in the connection string.</span></span>  
  
```  
using System;  
using System.Xml;  
using Microsoft.Data.SqlXml;  
using System.IO;  
using System.Xml.XPath;  
using System.Xml.Xsl;  
  
class Test  
{  
      static string ConnString = "Provider=SQLOLEDB;Server=(local);database=AdventureWorks;Integrated Security=SSPI";  
      public static int testXSL()  
      {  
         //Stream strm;  
         SqlXmlCommand cmd = new SqlXmlCommand(ConnString);  
         cmd.CommandText = "SELECT TOP 20 FirstName, LastName FROM Person.Contact FOR XML AUTO";  
         cmd.RootTag = "root";  
         using (Stream strm = cmd.ExecuteStream()){  
            XmlReader reader = new XmlReader(strm);  
            XPathDocument xd = new XPathDocument(reader, XmlSpace.Preserve);  
            XslCompiledTransform xslt = new XslCompiledTransform();  
            xslt.Load("MyXSL.xsl");  
            XmlWriter writer = XmlWriter.Create("xslt_output.html");  
            xslt.Transform(xd, writer);  
            reader.Close();  
            writer.Close();  
         }  
         return 0;  
      }  
      public static int Main(String[] args)  
      {  
         testXSL();     
         return 0;  
      }  
   }  
```  
  
  
