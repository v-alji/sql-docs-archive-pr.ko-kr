---
title: CommandStream 속성을 사용 하 여 템플릿 파일 실행 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- Managed Classes [SQLXML], executing template files
- SQLXML Managed Classes, executing template files
- templates [SQLXML], SQLXML Managed Classes
- CommandStream property
ms.assetid: 55c564e3-56d1-4d85-bcaa-703e2905dd57
author: rothja
ms.author: jroth
ms.openlocfilehash: c57a2ab2f3780a8bc75b53b0cceeee0799fcfcc2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87638622"
---
# <a name="executing-template-files-by-using-the-commandstream-property"></a><span data-ttu-id="84070-102">CommandStream 속성을 사용하여 템플릿 파일 실행</span><span class="sxs-lookup"><span data-stu-id="84070-102">Executing Template Files by Using the CommandStream Property</span></span>
  <span data-ttu-id="84070-103">이 예에서는 SqlXmlCommand 개체의 CommandStream 속성을 사용 하 여 SQL 또는 XPath 쿼리로 구성 된 템플릿 파일을 지정할 수 있는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="84070-103">This example illustrates how template files that consist of SQL or XPath queries can be specified by using the CommandStream property of the SqlXmlCommand object.</span></span> <span data-ttu-id="84070-104">이 응용 프로그램에서 FileStreamobject는 명령 파일에 대해 열리며, 파일 스트림은 실행 되는 CommandStream으로 할당 됩니다.</span><span class="sxs-lookup"><span data-stu-id="84070-104">In this application, a FileStreamobject is opened for a command file, and the file stream is assigned as the CommandStream that is executed.</span></span>  
  
 <span data-ttu-id="84070-105">다음 예제에서 CommandType 속성은 SqlXmlCommandType로 지정 됩니다 (템플릿 파일 아님).</span><span class="sxs-lookup"><span data-stu-id="84070-105">In the following example, the CommandType property is specified as SqlXmlCommandType.Template (not as TemplateFile).</span></span>  
  
 <span data-ttu-id="84070-106">예제 XML 템플릿은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="84070-106">This is the sample XML template:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <sql:query>  
    SELECT TOP 2 ContactID, FirstName, LastName   
    FROM   Person.Contact  
    FOR XML AUTO  
  </sql:query>  
</ROOT>  
```  
  
 <span data-ttu-id="84070-107">이것은 예제 C# 애플리케이션입니다.</span><span class="sxs-lookup"><span data-stu-id="84070-107">This is the sample C# application.</span></span> <span data-ttu-id="84070-108">따라서 애플리케이션을 테스트하려면 템플릿(TemplateFile.xml)을 저장한 다음 애플리케이션을 실행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="84070-108">To test the application, save the template (TemplateFile.xml) and then execute the application.</span></span> <span data-ttu-id="84070-109">애플리케이션은 XML 템플릿에 지정된 쿼리를 실행하고 생성된 XML 문서를 화면에 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="84070-109">The application executes the query that is specified in the XML template and displays the XML document that is generated on the screen.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="84070-110">코드에서 연결 문자열에 Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인스턴스의 이름을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="84070-110">In the code, you must provide the name of the instance of Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in the connection string.</span></span>  
  
```  
using System;  
using Microsoft.Data.SqlXml;  
using System.IO;  
  
class Test  
{  
      static string ConnString = "Provider=SQLOLEDB;Server=(local);database=AdventureWorks;Integrated Security=SSPI";  
      public static int testParams()  
      {  
         //Stream strm;  
         MemoryStream ms = new MemoryStream();  
         StreamWriter sw = new StreamWriter(ms);  
         ms.Position = 0;  
         SqlXmlCommand cmd = new SqlXmlCommand(ConnString);  
         cmd.CommandStream = new FileStream("TemplateFile.xml", FileMode.Open, FileAccess.Read);  
         cmd.CommandType = SqlXmlCommandType.Template;  
         using (Stream strm = cmd.ExecuteStream())  
         {  
            using (StreamReader sr = new StreamReader(strm)){  
               Console.WriteLine(sr.ReadToEnd());  
            }  
         }  
         return 0;        
      }  
  
      public static int Main(String[] args)  
      {  
         testParams();     
         return 0;  
      }  
   }  
```  
  
### <a name="to-test-the-application"></a><span data-ttu-id="84070-111">애플리케이션을 테스트하려면</span><span class="sxs-lookup"><span data-stu-id="84070-111">To test the application</span></span>  
  
1.  <span data-ttu-id="84070-112">이 예에서 제공하는 XML 템플릿(TemplateFile.xml)을 폴더에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="84070-112">Save the XML template (TemplateFile.xml) that is provided in this example in a folder.</span></span>  
  
2.  <span data-ttu-id="84070-113">이 예에서 제공하는 C# 코드(DocSample.cs)를 스키마가 저장된 폴더와 같은 폴더에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="84070-113">Save the C# code (DocSample.cs) that is provided in this example in the same folder in which the schema is stored.</span></span> <span data-ttu-id="84070-114">(다른 폴더에 파일을 저장하는 경우 코드를 편집하여 매핑 스키마에 대해 적합한 디렉터리 경로를 지정해야 합니다.)</span><span class="sxs-lookup"><span data-stu-id="84070-114">(If you store the files in a different folder, you will have to edit the code and specify the appropriate directory path for the mapping schema.)</span></span>  
  
3.  <span data-ttu-id="84070-115">코드를 컴파일합니다.</span><span class="sxs-lookup"><span data-stu-id="84070-115">Compile the code.</span></span> <span data-ttu-id="84070-116">다음을 사용하여 명령 프롬프트에서 코드를 컴파일합니다.</span><span class="sxs-lookup"><span data-stu-id="84070-116">To compile the code at the command prompt, use:</span></span>  
  
    ```  
    csc /reference:Microsoft.Data.SqlXML.dll DocSample.cs  
    ```  
  
     <span data-ttu-id="84070-117">이렇게 하면 실행 파일(DocSample.exe)이 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="84070-117">This creates an executable (DocSample.exe).</span></span>  
  
4.  <span data-ttu-id="84070-118">명령 프롬프트에서 DocSample.exe를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="84070-118">At the command prompt, execute DocSample.exe.</span></span>  
  
  
