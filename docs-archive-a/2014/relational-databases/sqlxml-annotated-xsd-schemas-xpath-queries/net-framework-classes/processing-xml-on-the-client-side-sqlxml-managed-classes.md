---
title: 클라이언트 쪽에서 XML 처리 (SQLXML 관리 되는 클래스) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- processing XML on client side [SQLXML]
- client-side XML formatting
- Managed Classes [SQLXML], client-side XML formatting
- SQLXML Managed Classes, client-side XML formatting
- ClientSideXml property
ms.assetid: 5e7ecf18-66fc-49ff-bc50-83635cd7ac0b
author: rothja
ms.author: jroth
ms.openlocfilehash: fb90f7c5c823c750b64f47d0c9df9551b9f857b5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646298"
---
# <a name="processing-xml-on-the-client-side-sqlxml-managed-classes"></a><span data-ttu-id="314fe-102">클라이언트 쪽에서 XML 처리(SQLXML 관리되는 클래스)</span><span class="sxs-lookup"><span data-stu-id="314fe-102">Processing XML on the Client Side (SQLXML Managed Classes)</span></span>
  <span data-ttu-id="314fe-103">이 예에서는 ClientSideXml 속성을 사용 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="314fe-103">This example illustrates the use of the ClientSideXml property.</span></span> <span data-ttu-id="314fe-104">애플리케이션은 서버에서 저장 프로시저를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="314fe-104">The application executes a stored procedure on the server.</span></span> <span data-ttu-id="314fe-105">클라이언트 쪽에서 저장 프로시저의 결과(두 개의 열로 이루어진 행 집합)가 처리되어 XML 문서를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="314fe-105">The result of the stored procedure (a two-column rowset) is processed on the client side to produce an XML document.</span></span>  
  
 <span data-ttu-id="314fe-106">다음 GetContacts 저장 프로시저는 AdventureWorks 데이터베이스의 Person. Contact 테이블에서 **FirstName** 및 **LastName** 을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="314fe-106">The following GetContacts stored procedure returns **FirstName** and **LastName** of employees in the Person.Contact table in the AdventureWorks database.</span></span>  
  
```  
USE AdventureWorks  
CREATE PROCEDURE GetContacts @LastName varchar(20)  
AS  
SELECT FirstName, LastName  
FROM   Person.Contact  
WHERE LastName = @LastName  
Go  
```  
  
 <span data-ttu-id="314fe-107">이 c # 응용 프로그램은 저장 프로시저를 실행 하 고 CommandText 값을 지정할 때 FOR XML AUTO 옵션을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="314fe-107">This C# application executes the stored procedure and specifies the FOR XML AUTO option in specifying the CommandText value.</span></span> <span data-ttu-id="314fe-108">응용 프로그램에서 SqlXmlCommand 개체의 ClientSideXml 속성이 true로 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="314fe-108">In the application, the ClientSideXml property of the SqlXmlCommand object is set to true.</span></span> <span data-ttu-id="314fe-109">이렇게 하면 행 집합을 반환하고 클라이언트에서 해당 행 집합에 XML 변환을 적용하는 기존 저장 프로시저를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="314fe-109">This allows you to execute preexisting stored procedures that return a rowset and apply an XML transformation to it on the client.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="314fe-110">코드에서 연결 문자열에 Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인스턴스의 이름을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="314fe-110">In the code, you must provide the name of the instance of Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in the connection string.</span></span>  
  
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
         SqlXmlParameter p;  
         SqlXmlCommand cmd = new SqlXmlCommand(ConnString);  
         cmd.ClientSideXml = true;  
         cmd.CommandText = "EXEC GetContacts ? FOR XML NESTED";  
         p = cmd.CreateParameter();  
         p.Value = "Achong";  
         using (Stream strm = cmd.ExecuteStream())   
         {  
            using (StreamReader sr = new StreamReader(strm))  
                  {  
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
  
 <span data-ttu-id="314fe-111">이 예를 테스트하려면 컴퓨터에 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework가 설치되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="314fe-111">To test this example, you must have the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework installed on your computer.</span></span>  
  
### <a name="to-test-the-application"></a><span data-ttu-id="314fe-112">애플리케이션을 테스트하려면</span><span class="sxs-lookup"><span data-stu-id="314fe-112">To test the application</span></span>  
  
1.  <span data-ttu-id="314fe-113">저장 프로시저를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="314fe-113">Create the stored procedure.</span></span>  
  
2.  <span data-ttu-id="314fe-114">이 예에 제공된 C# 코드(DocSample.cs)를 폴더에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="314fe-114">Save the C# code (DocSample.cs) that is provided in this example in a folder.</span></span> <span data-ttu-id="314fe-115">코드를 편집하여 적절한 로그인 및 암호 정보를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="314fe-115">Edit the code to specify appropriate login and password information.</span></span>  
  
3.  <span data-ttu-id="314fe-116">코드를 컴파일합니다.</span><span class="sxs-lookup"><span data-stu-id="314fe-116">Compile the code.</span></span> <span data-ttu-id="314fe-117">다음을 사용하여 명령 프롬프트에서 코드를 컴파일합니다.</span><span class="sxs-lookup"><span data-stu-id="314fe-117">To compile the code at the command prompt, use:</span></span>  
  
    ```  
    csc /reference:Microsoft.Data.SqlXML.dll DocSample.cs  
    ```  
  
     <span data-ttu-id="314fe-118">이렇게 하면 실행 파일(DocSample.exe)이 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="314fe-118">This creates an executable (DocSample.exe).</span></span>  
  
4.  <span data-ttu-id="314fe-119">명령 프롬프트에서 DocSample.exe를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="314fe-119">At the command prompt, execute DocSample.exe.</span></span>  
  
  
