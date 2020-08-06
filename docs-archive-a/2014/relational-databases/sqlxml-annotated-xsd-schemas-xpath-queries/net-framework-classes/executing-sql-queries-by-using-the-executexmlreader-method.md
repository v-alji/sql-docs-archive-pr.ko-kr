---
title: ExecuteXMLReader 메서드를 사용 하 여 SQL 쿼리 실행 | Microsoft Docs
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
- ExecuteXmlReader method
- SQL queries [SQLXML]
ms.assetid: f106a4c5-8d6e-40c0-bf1f-11e121afcb01
author: rothja
ms.author: jroth
ms.openlocfilehash: 1570e877ae84a813e5a053df34c35d5fe840969c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651570"
---
# <a name="executing-sql-queries-by-using-the-executexmlreader-method"></a><span data-ttu-id="bbd1a-102">ExecuteXMLReader 메서드를 사용하여 SQL 쿼리 실행</span><span class="sxs-lookup"><span data-stu-id="bbd1a-102">Executing SQL Queries by Using the ExecuteXMLReader Method</span></span>
  <span data-ttu-id="bbd1a-103">ExecuteToStream 메서드를 사용 하는 대신 SqlXmlCommand 개체의 ExecuteXmlReader 메서드를 사용 하 여 명령을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bbd1a-103">Instead of using the ExecuteToStream method, you can use the ExecuteXmlReader method of the SqlXmlCommand object to execute commands.</span></span> <span data-ttu-id="bbd1a-104">이 메서드는 결과를 추가로 처리 하는 데 사용할 수 있는 XmlReader 개체를 반환 합니다 .이 예제에서는 요소 또는 특성 이름과 값을 인쇄 합니다.</span><span class="sxs-lookup"><span data-stu-id="bbd1a-104">This method returns an XmlReader object that can be used for further processing of the result (which in this example is printing the element or attribute names and the values).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="bbd1a-105">코드에서 연결 문자열에 Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인스턴스의 이름을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bbd1a-105">In the code, you must provide the name of the instance of Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in the connection string.</span></span>  
  
```  
using System;  
using Microsoft.Data.SqlXml;  
using System.IO;  
using System.Xml;  
   class Test  
   {  
      static string ConnString = "Provider=SQLOLEDB;Server=(local);database=AdventureWorks2012;Integrated Security=SSPI";  
      public static int testParams()  
      {  
         SqlXmlParameter p;  
         XmlReader Reader;  
         XmlTextWriter tw;  
         SqlXmlCommand cmd = new SqlXmlCommand(ConnString);  
         cmd.CommandText = "select FirstName, LastName from Person.Person where LastName = ? For XML Auto";  
         p = cmd.CreateParameter();  
         p.Value = "Achong";  
         Reader = cmd.ExecuteXmlReader();  
            tw = new XmlTextWriter(Console.Out);  
         Reader.MoveToContent();  
         tw.WriteNode(Reader, false);  
         tw.Flush();  
         tw.Close();  
         Reader.Close();  
  
         return 0;  
      }  
  
      static int Main(string[] args)  
      {  
         testParams();  
         return 0;  
      }  
   }  
```  
  
### <a name="to-test-the-application"></a><span data-ttu-id="bbd1a-106">애플리케이션을 테스트하려면</span><span class="sxs-lookup"><span data-stu-id="bbd1a-106">To test the application</span></span>  
  
1.  <span data-ttu-id="bbd1a-107">컴퓨터에 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework가 설치되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="bbd1a-107">Make sure that you have the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework installed on your computer.</span></span>  
  
2.  <span data-ttu-id="bbd1a-108">이 항목에 나오는 C# 코드(DocSample.cs)를 폴더에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="bbd1a-108">Save the C# code (DocSample.cs) that is provided in this topic in a folder.</span></span>  
  
3.  <span data-ttu-id="bbd1a-109">코드를 컴파일합니다.</span><span class="sxs-lookup"><span data-stu-id="bbd1a-109">Compile the code.</span></span> <span data-ttu-id="bbd1a-110">다음을 사용하여 명령 프롬프트에서 코드를 컴파일합니다.</span><span class="sxs-lookup"><span data-stu-id="bbd1a-110">To compile the code at the command prompt, use:</span></span>  
  
    ```  
    csc /reference:Microsoft.Data.SqlXML.dll DocSample.cs  
    ```  
  
     <span data-ttu-id="bbd1a-111">이렇게 하면 실행 파일(DocSample.exe)이 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="bbd1a-111">This creates an executable (DocSample.exe).</span></span>  
  
4.  <span data-ttu-id="bbd1a-112">명령 프롬프트에서 DocSample.exe를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="bbd1a-112">At the command prompt, execute DocSample.exe.</span></span>  
  
  
