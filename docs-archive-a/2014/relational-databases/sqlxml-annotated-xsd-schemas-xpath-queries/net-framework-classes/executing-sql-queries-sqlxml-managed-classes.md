---
title: SQL 쿼리 실행 (SQLXML 관리 되는 클래스) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- queries [SQLXML], SQLXML Managed Classes
- SQLXML Managed Classes, executing SQL queries
- Managed Classes [SQLXML], executing SQL queries
- ExecuteToStream method
- SQL queries [SQLXML]
ms.assetid: a561ae83-a8b6-4b9b-a819-9b86839546b4
author: rothja
ms.author: jroth
ms.openlocfilehash: d869e45de359e602b2451b9f66fa3046f6823c1e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651568"
---
# <a name="executing-sql-queries-sqlxml-managed-classes"></a><span data-ttu-id="48216-102">SQL 쿼리 실행(SQLXML 관리되는 클래스)</span><span class="sxs-lookup"><span data-stu-id="48216-102">Executing SQL Queries (SQLXML Managed Classes)</span></span>
  <span data-ttu-id="48216-103">이 예에서는 다음 작업을 수행하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="48216-103">This example demonstrates:</span></span>  
  
-   <span data-ttu-id="48216-104">매개 변수 만들기 (SqlXmlParameter 개체)</span><span class="sxs-lookup"><span data-stu-id="48216-104">Creating parameters (SqlXmlParameter objects).</span></span>  
  
-   <span data-ttu-id="48216-105">SqlXmlParameter 개체의 속성 (이름 및 값)에 값을 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="48216-105">Assigning values to the properties (Name and Value) of SqlXmlParameter objects.</span></span>  
  
 <span data-ttu-id="48216-106">이 예에서는 간단한 SQL 쿼리를 실행하여 성이 매개 변수로 전달된 직원의 이름, 성 및 생년월일을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="48216-106">In this example, a simple SQL query is executed to retrieve the first name, last name, and birth date of the employee whose last name value is passed as a parameter.</span></span> <span data-ttu-id="48216-107">매개 변수 (*LastName*)를 지정할 때 Value 속성만 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="48216-107">In specifying the parameter (*LastName*), only the Value property is set.</span></span> <span data-ttu-id="48216-108">Name 속성은 설정 되지 않습니다 .이 쿼리에서 매개 변수는 위치 이며 이름이 필요 하지 않기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="48216-108">The Name property is not set, because in this query the parameter is positional and no name is required.</span></span>  
  
 <span data-ttu-id="48216-109">SqlXmlCommand 개체의 CommandType 속성은 기본적으로 **Sql**입니다.</span><span class="sxs-lookup"><span data-stu-id="48216-109">The CommandType property of the SqlXmlCommand object by default is **Sql**.</span></span> <span data-ttu-id="48216-110">명시적으로 설정되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="48216-110">Therefore, the property is not explicitly set.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="48216-111">코드에서 연결 문자열에 Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인스턴스의 이름을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="48216-111">In the code, you must provide the name of the instance of Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in the connection string.</span></span>  
  
 <span data-ttu-id="48216-112">다음은 C# 코드입니다.</span><span class="sxs-lookup"><span data-stu-id="48216-112">This is the C# code:</span></span>  
  
```  
using System;  
  
using Microsoft.Data.SqlXml;  
using System.IO;  
class Test  
{  
      static string ConnString = "Provider=SQLOLEDB;Server=(local);database=AdventureWorks;Integrated Security=SSPI";  
      public static int testParams()  
      {  
         Stream strm;  
         SqlXmlParameter p;  
         SqlXmlCommand cmd = new SqlXmlCommand(ConnString);        
         cmd.CommandText = "SELECT FirstName, LastName FROM Person.Contact WHERE LastName=? For XML Auto";  
         p = cmd.CreateParameter();  
         p.Value = "Achong";  
         string strResult;  
         try   
         {  
            strm = cmd.ExecuteStream();  
            strm.Position = 0;  
            using(StreamReader sr = new StreamReader(strm))  
            {  
               Console.WriteLine(sr.ReadToEnd());  
            }  
         }  
         catch (SqlXmlException e)  
         {  
            //in case of an error, this prints error returned.  
            e.ErrorStream.Position=0;  
            strResult=new StreamReader(e.ErrorStream).ReadToEnd();  
            System.Console.WriteLine(strResult);  
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
  
### <a name="to-test-the-application"></a><span data-ttu-id="48216-113">애플리케이션을 테스트하려면</span><span class="sxs-lookup"><span data-stu-id="48216-113">To test the application</span></span>  
  
1.  <span data-ttu-id="48216-114">이 항목에 나오는 C# 코드(DocSample.cs)를 폴더에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="48216-114">Save the C# code (DocSample.cs) provided in this topic in a folder.</span></span>  
  
2.  <span data-ttu-id="48216-115">코드를 컴파일합니다.</span><span class="sxs-lookup"><span data-stu-id="48216-115">Compile the code.</span></span> <span data-ttu-id="48216-116">다음을 사용하여 명령 프롬프트에서 코드를 컴파일합니다.</span><span class="sxs-lookup"><span data-stu-id="48216-116">To compile the code at the command prompt, use:</span></span>  
  
    ```  
    csc /reference:Microsoft.Data.SqlXML.dll DocSample.cs  
    ```  
  
     <span data-ttu-id="48216-117">이렇게 하면 실행 파일(DocSample.exe)이 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="48216-117">This creates an executable (DocSample.exe).</span></span>  
  
3.  <span data-ttu-id="48216-118">명령 프롬프트에서 DocSample.exe를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="48216-118">At the command prompt, execute DocSample.exe.</span></span>  
  
 <span data-ttu-id="48216-119">이 예를 테스트하려면 컴퓨터에 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework가 설치되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="48216-119">To test this example, you must have the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework installed on your computer.</span></span>  
  
 <span data-ttu-id="48216-120">SQL 쿼리를 명령 텍스트로 지정하는 대신 다음 코드 조각에 표시된 것처럼 updategram 템플릿을 실행하는 템플릿을 지정하여 고객 레코드를 삽입할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="48216-120">Instead of specifying SQL queries as the command text, you can specify a template (as shown in the following code fragment) that executes an updategram (which is also a template) to insert a customer record.</span></span> <span data-ttu-id="48216-121">파일에서 템플릿과 updategram을 지정한 후 파일을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="48216-121">You can specify templates and updategrams in files and execute files.</span></span> <span data-ttu-id="48216-122">자세한 내용은 [CommandText 속성을 사용 하 여 템플릿 파일 실행](executing-template-files-by-using-the-commandtext-property.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="48216-122">For more information, see [Executing Template Files by Using the CommandText Property](executing-template-files-by-using-the-commandtext-property.md).</span></span>  
  
```  
SqlXmlCommand cmd = new SqlXmlCommand("Provider=SQLOLEDB;Data Source=SqlServerName;Initial Catalog=Database; Integrated Security=SSPI;");  
Stream stm;  
cmd.CommandType = SqlXmlCommandType.UpdateGram;  
cmd.CommandText = "<ROOT xmlns:sql='urn:schemas-microsoft-com:xml-sql' xmlns:updg='urn:schemas-microsoft-com:xml-updategram'>" +  
      "<updg:sync>" +  
       "<updg:before/>" +  
       "<updg:after>" +  
         "<Customer CustomerID='aaaaa' CustomerName='Some Name' CustomerTitle='SomeTitle' />" +  
       "</updg:after>" +  
       "</updg:sync>" +  
       "</ROOT>";  
  
stm = cmd.ExecuteStream();  
stm = null;  
cmd = null;  
```  
  
## <a name="using-executetostream"></a><span data-ttu-id="48216-123">ExecuteToStream 사용</span><span class="sxs-lookup"><span data-stu-id="48216-123">Using ExecuteToStream</span></span>  
 <span data-ttu-id="48216-124">기존 스트림이 있는 경우 Stream 개체를 만들고 Execute 메서드를 사용 하는 대신 ExecuteToStream 메서드를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="48216-124">If you have an existing stream, you can use the ExecuteToStream method instead of creating a Stream object and using the Execute method.</span></span> <span data-ttu-id="48216-125">이전 예제의 코드는 ExecuteToStream 메서드를 사용 하도록 여기에서 수정 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="48216-125">The code from the preceding example is revised here to use the ExecuteToStream method:</span></span>  
  
```  
using System;  
using Microsoft.Data.SqlXml;  
using System.IO;  
class Test  
{  
   static string ConnString = "Provider=SQLOLEDB;Server=SqlServerName;database=AdventureWorks;Integrated Security=SSPI;";  
   public static int testParams()  
   {  
      SqlXmlParameter p;  
      MemoryStream ms = new MemoryStream();  
      StreamReader sr = new StreamReader(ms);  
      ms.Position = 0;  
      SqlXmlCommand cmd = new SqlXmlCommand(ConnString);  
      cmd.CommandText = "select FirstName, LastName from Person.Contact where LastName = ? For XML Auto";  
      p = cmd.CreateParameter();  
      p.Value = "Achong";  
      cmd.ExecuteToStream(ms);  
      ms.Position = 0;  
      Console.WriteLine(sr.ReadToEnd());  
      return 0;        
   }  
   public static int Main(String[] args)  
   {  
      testParams();     
      return 0;  
   }  
}  
```  
  
> [!NOTE]  
>  <span data-ttu-id="48216-126">XmlReader 개체를 반환 하는 ExecuteXMLReadermethod를 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="48216-126">You can also use the ExecuteXMLReadermethod that returns an XmlReader object.</span></span> <span data-ttu-id="48216-127">자세한 내용은 [ExecuteXMLReader 메서드를 사용 하 여 SQL 쿼리 실행](executing-sql-queries-by-using-the-executexmlreader-method.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="48216-127">For more information, see [Executing SQL Queries by Using the ExecuteXMLReader Method](executing-sql-queries-by-using-the-executexmlreader-method.md).</span></span>  
  
  
