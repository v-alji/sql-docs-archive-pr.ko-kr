---
title: .NET 환경에서 SQLXML 기능 액세스 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- Managed Classes [SQLXML], accessing SQLXML functionality
- SQLXML Managed Classes, accessing SQLXML functionality
- DiffGrams [SQLXML], accessing SQLXML functionality
- .NET Framework [SQLXML], accessing SQLXML functionality
ms.assetid: 74744535-2945-414d-9a5b-7e8cc363953a
author: rothja
ms.author: jroth
ms.openlocfilehash: a2ba0a54310833c0a1a1315aa94d78fe5650d480
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651586"
---
# <a name="accessing-sqlxml-functionality-in-the-net-environment"></a><span data-ttu-id="8ff53-102">.NET 환경에서 SQLXML 기능 액세스</span><span class="sxs-lookup"><span data-stu-id="8ff53-102">Accessing SQLXML Functionality in the .NET Environment</span></span>
  <span data-ttu-id="8ff53-103">이 예에서 보여 주는 항목은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="8ff53-103">This example shows:</span></span>  
  
-   <span data-ttu-id="8ff53-104">[!INCLUDE[msCoName](../../../includes/msconame-md.md)]SQLXML 관리 되는 클래스 (microsoft. Data sqlxml)를 사용 하 여 .NET Framework 환경에서 microsoft에 액세스 하는 방법 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[msCoName](../../../includes/msconame-md.md)] 입니다.</span><span class="sxs-lookup"><span data-stu-id="8ff53-104">How to use [!INCLUDE[msCoName](../../../includes/msconame-md.md)] SQLXML Managed Classes (Microsoft.Data.SqlXml) to access Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework environment.</span></span>  
  
-   <span data-ttu-id="8ff53-105">.NET Framework 환경에서 생성된 DiffGram이 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 테이블에 데이터 업데이트를 적용하는 방법</span><span class="sxs-lookup"><span data-stu-id="8ff53-105">How DiffGrams that are generated in the .NET Framework environment can apply data updates to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] tables.</span></span>  
  
 <span data-ttu-id="8ff53-106">이 애플리케이션에서는 XSD 스키마에 대해 XPath 쿼리를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="8ff53-106">In this application, an XPath query is executed against an XSD schema.</span></span> <span data-ttu-id="8ff53-107">XPath 쿼리를 실행 하면 연락처 데이터 (**FirstName**, **LastName**)로 구성 된 XML 문서가 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ff53-107">The execution of the XPath query returns an XML document that consists of contact data (**FirstName**, **LastName**).</span></span> <span data-ttu-id="8ff53-108">애플리케이션은 .NET Framework 환경의 데이터 세트에 XML 문서를 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="8ff53-108">The application loads the XML document in the dataset in the .NET Framework environment.</span></span> <span data-ttu-id="8ff53-109">그런 다음 데이터 세트에 있는 첫 번째 연락처에서 이름을 &quot;Susan&quot;으로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="8ff53-109">The data in the dataset is modified: the contact's first name is changed to "Susan" for the first contact in the dataset.</span></span> <span data-ttu-id="8ff53-110">그리고 해당 데이터 세트에서 DiffGram을 생성하며, 이 DiffGram에 지정된 업데이트(직원 이름에 대한 변경 내용)를 Person.Contact 테이블에 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="8ff53-110">The DiffGram is generated from the dataset, and the update that is specified in the DiffGram (the change in the employee's first name) is then applied to the Person.Contact table.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8ff53-111">코드에서 연결 문자열에 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인스턴스의 이름을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ff53-111">In the code, you must provide the name of the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in the connection string.</span></span>  
  
```  
using System;  
using System.Data;  
using Microsoft.Data.SqlXml;  
using System.IO;  
class Test  
{  
   static string ConnString = "Provider=SQLOLEDB;Server=SqlServerName;database=AdventureWorks;Integrated Security=SSPI;";  
   public static int testParams()  
   {  
      DataRow row;  
      SqlXmlAdapter ad;  
      //need a memory stream to hold diff gram temporarily  
      MemoryStream ms = new MemoryStream();  
      SqlXmlCommand cmd = new SqlXmlCommand(ConnString);  
      cmd.RootTag = "ROOT";  
      cmd.CommandText = "Con";  
      cmd.CommandType = SqlXmlCommandType.XPath;  
      cmd.SchemaPath = "MySchema.xml";  
      //load data set  
      DataSet ds = new DataSet();  
      ad = new SqlXmlAdapter(cmd);  
      ad.Fill(ds);  
      row = ds.Tables["Con"].Rows[0];  
      row["FName"] = "Susan";  
      ad.Update(ds);  
      return 0;  
   }  
   public static int Main(String[] args)  
   {  
      testParams();  
      return 0;  
   }  
}  
```  
  
 <span data-ttu-id="8ff53-112">**이 예를 테스트하려면**</span><span class="sxs-lookup"><span data-stu-id="8ff53-112">**To test the example:**</span></span>  
  
 <span data-ttu-id="8ff53-113">이 예를 테스트하려면 컴퓨터에 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework가 설치되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ff53-113">To test this example, you must have the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework installed on your computer.</span></span>  
  
1.  <span data-ttu-id="8ff53-114">이 XSD 스키마(MySchema.xml)를 폴더에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="8ff53-114">Save this XSD schema (MySchema.xml) in a folder:</span></span>  
  
    ```  
    <xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
                xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
      <xsd:element name="Con" sql:relation="Person.Contact" >  
       <xsd:complexType>  
         <xsd:sequence>  
            <xsd:element name="FName"    
                         sql:field="FirstName"   
                         type="xsd:string" />   
            <xsd:element name="LName"    
                         sql:field="LastName"    
                         type="xsd:string" />  
         </xsd:sequence>  
         <xsd:attribute name="ContactID" type="xsd:integer" />  
        </xsd:complexType>  
      </xsd:element>  
    </xsd:schema>  
    ```  
  
2.  <span data-ttu-id="8ff53-115">이 예에서 제공하는 C# 코드(DocSample.cs)를 스키마가 저장된 폴더와 같은 폴더에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="8ff53-115">Save the C# code (DocSample.cs) provided in this example in the same folder in which the schema is stored.</span></span> <span data-ttu-id="8ff53-116">(다른 폴더에 파일을 저장하는 경우 코드를 편집하여 매핑 스키마에 대해 적합한 디렉터리 경로를 지정해야 합니다.)</span><span class="sxs-lookup"><span data-stu-id="8ff53-116">(If you store the files in a different folder, you will have to edit the code and specify the appropriate directory path for the mapping schema.)</span></span>  
  
3.  <span data-ttu-id="8ff53-117">코드를 컴파일합니다.</span><span class="sxs-lookup"><span data-stu-id="8ff53-117">Compile the code.</span></span> <span data-ttu-id="8ff53-118">다음을 사용하여 명령 프롬프트에서 코드를 컴파일합니다.</span><span class="sxs-lookup"><span data-stu-id="8ff53-118">To compile the code at the command prompt, use:</span></span>  
  
    ```  
    csc /reference:Microsoft.Data.SqlXML.dll DocSample.cs  
    ```  
  
     <span data-ttu-id="8ff53-119">이렇게 하면 실행 파일(DocSample.exe)이 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="8ff53-119">This creates an executable (DocSample.exe).</span></span>  
  
 <span data-ttu-id="8ff53-120">명령 프롬프트에서 DocSample.exe를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="8ff53-120">At the command prompt, execute DocSample.exe.</span></span>  
  
  
