---
title: 네임 스페이스를 사용 하 여 XPath 쿼리 실행 (SQLXML 관리 되는 클래스) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- namespaces property
- XPath queries [SQLXML], SQLXML Managed Classes
- queries [SQLXML], SQLXML Managed Classes
- XPath queries [SQLXML], namespaces
- Managed Classes [SQLXML], executing XPath queries
- SQLXML Managed Classes, executing XPath queries
- namespaces [SQLXML], XPath queries
ms.assetid: c6fc46d8-6b42-4992-a8f1-a8d4b8886e6e
author: rothja
ms.author: jroth
ms.openlocfilehash: a2d726de95929709c1ae958ee22388df3195bc84
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87638619"
---
# <a name="executing-xpath-queries-with-namespaces-sqlxml-managed-classes"></a><span data-ttu-id="3dc31-102">네임스페이스가 포함된 XPath 쿼리 실행(SQLXML 관리되는 클래스)</span><span class="sxs-lookup"><span data-stu-id="3dc31-102">Executing XPath Queries with Namespaces (SQLXML Managed Classes)</span></span>
  <span data-ttu-id="3dc31-103">XPath 쿼리에는 네임스페이스가 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3dc31-103">XPath queries can include namespaces.</span></span> <span data-ttu-id="3dc31-104">스키마 요소가 네임스페이스로 한정된 경우 즉, 스키마 요소에서 대상 네임스페이스를 사용하는 경우 스키마에 대한 XPath 쿼리에서 해당 네임스페이스를 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3dc31-104">If the schema elements are namespace-qualified (use a target namespace), the XPath queries against the schema must specify the namespace.</span></span>  
  
 <span data-ttu-id="3dc31-105">[!INCLUDE[msCoName](../../../includes/msconame-md.md)] SQLXML 4.0에서는 와일드카드 문자(\*)를 사용할 수 없으므로 네임스페이스 접두사를 사용하여 XPath 쿼리를 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3dc31-105">Because the wildcard character (\*) is not supported in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] SQLXML 4.0, you must specify the XPath query by using a namespace prefix.</span></span> <span data-ttu-id="3dc31-106">접두사를 확인 하려면 네임 스페이스 속성을 사용 하 여 네임 스페이스 바인딩을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3dc31-106">To resolve the prefix, use the namespaces property to specify the namespace binding.</span></span>  
  
 <span data-ttu-id="3dc31-107">다음 예의 XPath 쿼리는 와일드 카드 문자 ( \* )와 로컬 이름 () 및 네임 스페이스 uri () XPath 함수를 사용 하 여 네임 스페이스를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3dc31-107">In the following example, the XPath query specifies namespaces by using the wildcard character (\*) and the local-name() and namespace-uri() XPath functions.</span></span> <span data-ttu-id="3dc31-108">이 XPath 쿼리는 로컬 이름이 `Employee`이고 네임스페이스 URI가 `urn:myschema:Contacts`인 모든 요소를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="3dc31-108">This XPath query returns all the elements where the local name is `Employee` and the namespace URI is `urn:myschema:Contacts`:</span></span>  
  
```  
/*[local-name() = 'Contact' and namespace-uri() = 'urn:myschema:Contacts']  
```  
  
 <span data-ttu-id="3dc31-109">SQLXML 4.0에서는 네임스페이스 접두사를 사용하여 이 XPath 쿼리를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3dc31-109">In SQLXML 4.0, specify this XPath query with a namespace prefix.</span></span> <span data-ttu-id="3dc31-110">예를 들어 `x:Contact`의 경우 `x`가 네임스페이스 접두사입니다.</span><span class="sxs-lookup"><span data-stu-id="3dc31-110">An example is `x:Contact`, where `x` is the namespace prefix.</span></span> <span data-ttu-id="3dc31-111">다음과 같은 XSD 스키마를 살펴보십시오.</span><span class="sxs-lookup"><span data-stu-id="3dc31-111">Consider the following XSD schema:</span></span>  
  
```  
<schema xmlns="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema"  
            xmlns:con="urn:myschema:Contacts"  
            targetNamespace="urn:myschema:Contacts">  
<complexType name="ContactType">  
  <attribute name="CID" sql:field="ContactID" type="ID"/>  
  <attribute name="FName" sql:field="FirstName" type="string"/>  
  <attribute name="LName" sql:field="LastName"/>   
</complexType>  
<element name="Contact" type="con:ContactType" sql:relation="Person.Contact"/>  
</schema>  
```  
  
 <span data-ttu-id="3dc31-112">이 스키마에서는 대상 네임스페이스를 정의하므로 이 스키마에 대한 XPath 쿼리(예: "Employee")에는 네임스페이스가 포함되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3dc31-112">Because this schema defines the target namespace, an XPath query (such as "Employee") against this schema must include the namespace.</span></span>  
  
 <span data-ttu-id="3dc31-113">다음 C# 예제 애플리케이션은 위의 XSD 스키마(MySchema.xml)에 대해 XPath 쿼리를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="3dc31-113">The following C# sample application executes an XPath query against the preceding XSD schema (MySchema.xml).</span></span> <span data-ttu-id="3dc31-114">접두사를 확인 하려면 SqlXmlCommand 개체의 네임 스페이스 속성을 사용 하 여 네임 스페이스 바인딩을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3dc31-114">To resolve the prefix, specify the namespace binding by using the Namespaces property of the SqlXmlCommand object.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3dc31-115">코드에서 연결 문자열에 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인스턴스의 이름을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3dc31-115">In the code, you must provide the name of the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in the connection string.</span></span>  
  
```  
using System;  
using Microsoft.Data.SqlXml;  
using System.IO;  
class Test  
{  
      static string ConnString = "Provider=SQLOLEDB;Server=(local);database=AdventureWorks;Integrated Security=SSPI";  
      public static int testXPath()  
      {  
         //Stream strm;  
         SqlXmlCommand cmd = new SqlXmlCommand(ConnString);  
         cmd.CommandText = "x:Contact[@CID='1']";  
         cmd.CommandType = SqlXmlCommandType.XPath;  
         cmd.RootTag = "ROOT";  
         cmd.Namespaces = "xmlns:x='urn:myschema:Contacts'";  
         cmd.SchemaPath = "MySchema.xml";  
         using (Stream strm = cmd.ExecuteStream()){  
            using (StreamReader sr = new StreamReader(strm)){  
               Console.WriteLine(sr.ReadToEnd());  
            }  
         }  
         return 0;  
      }  
      public static int Main(String[] args)  
      {  
         testXPath();  
         return 0;  
      }  
   }  
```  
  
 <span data-ttu-id="3dc31-116">이 예를 테스트하려면 컴퓨터에 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework가 설치되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3dc31-116">To test this example, you must have the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework installed on your computer.</span></span>  
  
### <a name="to-test-the-application"></a><span data-ttu-id="3dc31-117">애플리케이션을 테스트하려면</span><span class="sxs-lookup"><span data-stu-id="3dc31-117">To test the application</span></span>  
  
1.  <span data-ttu-id="3dc31-118">이 예에서 제공하는 XSD 스키마(MySchema.xml)를 폴더에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="3dc31-118">Save the XSD schema (MySchema.xml) that is provided in this example in a folder.</span></span>  
  
2.  <span data-ttu-id="3dc31-119">이 예에서 제공하는 C# 코드(DocSample.cs)를 스키마가 저장된 폴더와 같은 폴더에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="3dc31-119">Save the C# code (DocSample.cs) that is provided in this example in the same folder in which the schema is stored.</span></span> <span data-ttu-id="3dc31-120">(다른 폴더에 파일을 저장하는 경우 코드를 편집하여 매핑 스키마에 대해 적합한 디렉터리 경로를 지정해야 합니다.)</span><span class="sxs-lookup"><span data-stu-id="3dc31-120">(If you store the files in a different folder, you will have to edit the code and specify the appropriate directory path for the mapping schema.)</span></span>  
  
3.  <span data-ttu-id="3dc31-121">코드를 컴파일합니다.</span><span class="sxs-lookup"><span data-stu-id="3dc31-121">Compile the code.</span></span> <span data-ttu-id="3dc31-122">다음을 사용하여 명령 프롬프트에서 코드를 컴파일합니다.</span><span class="sxs-lookup"><span data-stu-id="3dc31-122">To compile the code at the command prompt, use:</span></span>  
  
    ```  
    csc /reference:Microsoft.Data.SqlXML.dll DocSample.cs  
    ```  
  
     <span data-ttu-id="3dc31-123">이렇게 하면 실행 파일(DocSample.exe)이 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="3dc31-123">This creates an executable (DocSample.exe).</span></span>  
  
4.  <span data-ttu-id="3dc31-124">명령 프롬프트에서 DocSample.exe를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="3dc31-124">At the command prompt, execute DocSample.exe.</span></span>  
  
  
