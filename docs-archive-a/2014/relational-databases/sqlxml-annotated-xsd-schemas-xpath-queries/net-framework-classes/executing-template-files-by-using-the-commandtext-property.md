---
title: CommandText 속성을 사용 하 여 템플릿 파일 실행 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- Managed Classes [SQLXML], executing template files
- SQLXML Managed Classes, executing template files
- templates [SQLXML], SQLXML Managed Classes
- executing template files [SQLXML]
- CommandText property
ms.assetid: f1b1278d-252d-4a06-836e-4ef77f338ef9
author: rothja
ms.author: jroth
ms.openlocfilehash: f5507e84daf57ca4646fae3efe78c6105af35700
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87638621"
---
# <a name="executing-template-files-by-using-the-commandtext-property"></a><span data-ttu-id="495ad-102">CommandText 속성을 사용하여 템플릿 파일 실행</span><span class="sxs-lookup"><span data-stu-id="495ad-102">Executing Template Files by Using the CommandText Property</span></span>
  <span data-ttu-id="495ad-103">이 예에서는 CommandTextproperty를 사용 하 여 SQL 또는 XPath 쿼리로 구성 된 템플릿 파일을 지정할 수 있는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="495ad-103">This example illustrates how template files that consist of SQL or XPath queries can be specified by using the CommandTextproperty.</span></span> <span data-ttu-id="495ad-104">SQL 또는 XPath 쿼리를 CommandText 값으로 지정 하는 대신 파일 이름을 값으로 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="495ad-104">Instead of specifying the SQL or XPath query as the value of CommandText, you can specify a file name as the value.</span></span> <span data-ttu-id="495ad-105">다음 예제에서 CommandType 속성은 SqlXmlCommandType. 템플릿 파일로 지정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="495ad-105">In the following example, the CommandType property is specified as SqlXmlCommandType.TemplateFile.</span></span>  
  
 <span data-ttu-id="495ad-106">예제 애플리케이션에서 이 템플릿을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="495ad-106">The sample application executes this template:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <sql:query>  
    SELECT TOP 2 ContactID, FirstName, LastName   
    FROM   Person.Contact  
    FOR XML AUTO  
  </sql:query>  
</ROOT>  
```  
  
 <span data-ttu-id="495ad-107">이 애플리케이션은 C# 예제 애플리케이션입니다.</span><span class="sxs-lookup"><span data-stu-id="495ad-107">This is the C# sample application.</span></span> <span data-ttu-id="495ad-108">따라서 애플리케이션을 테스트하려면 템플릿(TemplateFile.xml)을 저장한 다음 애플리케이션을 실행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="495ad-108">To test the application, save the template (TemplateFile.xml) and then execute the application.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="495ad-109">코드에서 연결 문자열에 Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인스턴스의 이름을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="495ad-109">In the code, you must provide the name of the instance of Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in the connection string.</span></span>  
  
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
         SqlXmlCommand cmd = new SqlXmlCommand(ConnString);  
         cmd.CommandType = SqlXmlCommandType.TemplateFile;  
         cmd.CommandText = "TemplateFile.xml";  
         using (Stream strm = cmd.ExecuteStream()){  
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
  
### <a name="to-test-the-application"></a><span data-ttu-id="495ad-110">애플리케이션을 테스트하려면</span><span class="sxs-lookup"><span data-stu-id="495ad-110">To test the application</span></span>  
  
1.  <span data-ttu-id="495ad-111">컴퓨터에 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework가 설치되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="495ad-111">Make sure that you have the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework installed on your computer.</span></span>  
  
2.  <span data-ttu-id="495ad-112">이 예에서 제공하는 XML 템플릿(TemplateFile.xml)을 폴더에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="495ad-112">Save the XML template (TemplateFile.xml) that is provided in this example in a folder.</span></span>  
  
3.  <span data-ttu-id="495ad-113">이 예에서 제공하는 C# 코드(DocSample.cs)를 스키마가 저장된 폴더와 같은 폴더에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="495ad-113">Save the C# code (DocSample.cs) that is provided in this example in the same folder in which the schema is stored.</span></span> <span data-ttu-id="495ad-114">(다른 폴더에 파일을 저장하는 경우 코드를 편집하여 매핑 스키마에 대해 적합한 디렉터리 경로를 지정해야 합니다.)</span><span class="sxs-lookup"><span data-stu-id="495ad-114">(If you store the files in a different folder, you will have to edit the code and specify the appropriate directory path for the mapping schema.)</span></span>  
  
4.  <span data-ttu-id="495ad-115">코드를 컴파일합니다.</span><span class="sxs-lookup"><span data-stu-id="495ad-115">Compile the code.</span></span> <span data-ttu-id="495ad-116">다음을 사용하여 명령 프롬프트에서 코드를 컴파일합니다.</span><span class="sxs-lookup"><span data-stu-id="495ad-116">To compile the code at the command prompt, use:</span></span>  
  
    ```  
    csc /reference:Microsoft.Data.SqlXML.dll DocSample.cs  
    ```  
  
     <span data-ttu-id="495ad-117">이렇게 하면 실행 파일(DocSample.exe)이 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="495ad-117">This creates an executable (DocSample.exe).</span></span>  
  
5.  <span data-ttu-id="495ad-118">명령 프롬프트에서 DocSample.exe를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="495ad-118">At the command prompt, execute DocSample.exe.</span></span>  
  
 <span data-ttu-id="495ad-119">템플릿에 매개 변수를 전달 하는 경우 매개 변수 이름은 at 기호 (@)로 시작 해야 합니다. 예를 들면 p.Name = " @ContactID "와 같습니다. 여기서 p는 SqlXmlParameter 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="495ad-119">If you pass a parameter to a template, the parameter name must begin with at sign (@); for example, p.Name="@ContactID", where p is a SqlXmlParameter object.</span></span>  
  
 <span data-ttu-id="495ad-120">다음은 하나의 매개 변수를 사용하는 업데이트된 템플릿입니다.</span><span class="sxs-lookup"><span data-stu-id="495ad-120">This is the updated template which takes one parameter.</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <sql:header>  
     <sql:param name='ContactID'>1</sql:param>    
  </sql:header>  
  <sql:query>  
    SELECT ContactID, FirstName, LastName  
    FROM   Person.Contact  
    WHERE  ContactID=@ContactID  
    FOR XML AUTO  
  </sql:query>  
</ROOT>  
```  
  
 <span data-ttu-id="495ad-121">다음은 템플릿을 실행하기 위해 매개 변수가 전달되는 업데이트된 코드입니다.</span><span class="sxs-lookup"><span data-stu-id="495ad-121">This is the updated code in which a parameter is passed in to execute the template.</span></span>  
  
```  
public static int testParams()  
{  
  
   Stream strm;  
   SqlXmlParameter p;  
  
   SqlXmlCommand cmd = new SqlXmlCommand(ConnString);  
   cmd.CommandType = SqlXmlCommandType.TemplateFile;  
   cmd.CommandText = "TemplateFile.xml";  
   p = cmd.CreateParameter();  
   p.Name="@ContactID";  
   p.Value = "1";  
   strm = cmd.ExecuteStream();  
   StreamReader sw = new StreamReader(strm);  
   Console.WriteLine(sw.ReadToEnd());  
   return 0;        
}  
```  
  
  
