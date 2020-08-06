---
title: SQLXML 관리 되는 클래스를 사용 하 여 DiffGram 실행 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- DiffGrams [SQLXML], Managed Classes
- SQLXML Managed Classes, DiffGrams
- Managed Classes [SQLXML], DiffGrams
- SQLXML, Managed Classes
ms.assetid: 81c687ca-8c9f-4f58-801f-8dabcc508a06
author: rothja
ms.author: jroth
ms.openlocfilehash: f36127c37eea73a2872d4bf0aef7172a88e430a0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651589"
---
# <a name="executing-a-diffgram-by-using-sqlxml-managed-classes"></a><span data-ttu-id="90cd1-102">SQLXML 관리되는 클래스를 사용하여 DiffGram 실행</span><span class="sxs-lookup"><span data-stu-id="90cd1-102">Executing a DiffGram by Using SQLXML Managed Classes</span></span>
  <span data-ttu-id="90cd1-103">이 예에서는 .NET Framework 환경에서 DiffGram 파일을 실행 하 여 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] SQLXML 관리 되는 클래스 (sqlxml)를 사용 하 여 테이블에 데이터 업데이트를 적용 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="90cd1-103">This example shows how to execute a DiffGram file in the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework environment to apply data updates to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] tables using SQLXML Managed Classes (Microsoft.Data.SqlXml).</span></span>  
  
 <span data-ttu-id="90cd1-104">이 예에서 DiffGram은 고객 ALFKI의 고객 정보(CompanyName 및 ContactName)를 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="90cd1-104">In this example, the DiffGram updates customer information (CompanyName and ContactName) for customer ALFKI.</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql" sql:mapping-schema="DiffGramSchema.xml">  
  <diffgr:diffgram   
           xmlns:msdata="urn:schemas-microsoft-com:xml-msdata"   
           xmlns:diffgr="urn:schemas-microsoft-com:xml-diffgram-v1">  
    <DataInstance>  
      <Customer diffgr:id="Customer1"   
                msdata:rowOrder="0" diffgr:hasChanges="modified"   
                CustomerID="ALFKI">  
          <CompanyName>Bottom Dollar Markets</CompanyName>  
          <ContactName>Antonio Moreno</ContactName>  
      </Customer>  
    </DataInstance>  
    <diffgr:before>  
     <Customer diffgr:id="Customer1"   
               msdata:rowOrder="0"   
               CustomerID="ALFKI">  
        <CompanyName>Alfreds Futterkiste</CompanyName>  
        <ContactName>Maria Anders</ContactName>  
      </Customer>  
    </diffgr:before>  
  </diffgr:diffgram>  
</ROOT>  
```  
  
 <span data-ttu-id="90cd1-105">**\<before>** 블록에는 **\<Customer>** 요소 (**diffgr: Id = "Customer1"**)가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="90cd1-105">The **\<before>** block includes a **\<Customer>** element (**diffgr:id="Customer1"**).</span></span> <span data-ttu-id="90cd1-106">블록에는 **\<DataInstance>** **\<Customer>** **id가**같은 해당 요소가 포함 됩니다. **\<customer>** 의 요소는 **\<NewDataSet>** **Diffgr: haschanges = "modified"** 도 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="90cd1-106">The **\<DataInstance>** block includes the corresponding **\<Customer>** element with same **id**. The **\<customer>** element in the **\<NewDataSet>** also specifies **diffgr:hasChanges="modified"**.</span></span> <span data-ttu-id="90cd1-107">이는 업데이트 작업임을 나타내며 이에 따라 Cust 테이블의 고객 레코드가 업데이트됩니다.</span><span class="sxs-lookup"><span data-stu-id="90cd1-107">This indicates an update operation, and the customer record in the Cust table is updated accordingly.</span></span> <span data-ttu-id="90cd1-108">**Diffgr: hasChanges** 특성이 지정 되지 않은 경우 DiffGram 처리 논리는이 요소를 무시 하 고 업데이트를 수행 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="90cd1-108">Note that if the **diffgr:hasChanges** attribute is not specified, the DiffGram processing logic ignores this element and no updates are performed.</span></span>  
  
 <span data-ttu-id="90cd1-109">다음은 SQLXML 관리 되는 클래스를 사용 하 여 위의 DiffGram을 실행 하 고 **tempdb** 데이터베이스에도 만들 두 개의 테이블 (Cust, Ord)을 업데이트 하는 방법을 보여 주는 c # 자습서 응용 프로그램의 코드입니다.</span><span class="sxs-lookup"><span data-stu-id="90cd1-109">The following is code for a C# tutorial application that shows how to use the SQLXML Managed Classes to execute the above DiffGram and update two tables (Cust, Ord) you will also create in the **tempdb** database.</span></span>  
  
```  
using System;  
using System.Data;  
using Microsoft.Data.SqlXml;  
using System.IO;  
class Test  
{  
   static string ConnString = "Provider=SQLOLEDB;Server=MyServer;database=tempdb;Integrated Security=SSPI;";  
   public static int testParams()  
   {  
      SqlXmlAdapter ad;  
      // Need a memory stream to hold diff gram temporarily  
      MemoryStream ms = new MemoryStream();  
      SqlXmlCommand cmd = new SqlXmlCommand(ConnString);  
      cmd.RootTag = "ROOT";  
      cmd.CommandStream = new FileStream("MyDiffgram.xml", FileMode.Open, FileAccess.Read);  
      cmd.CommandType = SqlXmlCommandType.DiffGram;  
      cmd.SchemaPath = "DiffGramSchema.xml";  
      // Load data set  
      DataSet ds = new DataSet();  
      ad = new SqlXmlAdapter(cmd);  
      ad.Fill(ds);  
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
  
### <a name="to-test-the-application"></a><span data-ttu-id="90cd1-110">애플리케이션을 테스트하려면</span><span class="sxs-lookup"><span data-stu-id="90cd1-110">To test the application</span></span>  
  
1.  <span data-ttu-id="90cd1-111">컴퓨터에 .NET Framework가 설치되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="90cd1-111">Ensure that the .NET Framework is installed on your computer.</span></span>  
  
2.  <span data-ttu-id="90cd1-112">다음 XSD 스키마(DiffGramSchema.xml)를 폴더에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="90cd1-112">Save the following XSD schema (DiffGramSchema.xml) in a folder:</span></span>  
  
    ```  
    <xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
                xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
     <xsd:annotation>  
      <xsd:documentation>  
        Diffgram Customers/Orders Schema.  
      </xsd:documentation>  
      <xsd:appinfo>  
           <sql:relationship name="CustomersOrders"   
                      parent="Cust"  
                      parent-key="CustomerID"  
                      child-key="CustomerID"  
                      child="Ord"/>  
      </xsd:appinfo>  
     </xsd:annotation>  
     <xsd:element name="Customer" sql:relation="Cust">  
      <xsd:complexType>  
        <xsd:sequence>  
          <xsd:element name="CompanyName"    type="xsd:string"/>  
          <xsd:element name="ContactName"    type="xsd:string"/>  
           <xsd:element name="Order" sql:relation="Ord" sql:relationship="CustomersOrders">  
            <xsd:complexType>  
              <xsd:attribute name="OrderID" type="xsd:int" sql:field="OrderID"/>  
              <xsd:attribute name="CustomerID" type="xsd:string"/>  
            </xsd:complexType>  
          </xsd:element>  
        </xsd:sequence>  
        <xsd:attribute name="CustomerID" type="xsd:string" sql:field="CustomerID"/>  
      </xsd:complexType>  
     </xsd:element>  
    </xsd:schema>  
    ```  
  
3.  <span data-ttu-id="90cd1-113">이러한 테이블을 **tempdb** 데이터베이스에 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="90cd1-113">Create these tables in the **tempdb** database.</span></span>  
  
    ```  
    CREATE TABLE Cust(  
            CustomerID  nchar(5) Primary Key,  
            CompanyName nvarchar(40) NOT NULL ,  
            ContactName nvarchar(60) NULL)  
    GO  
  
    CREATE TABLE Ord(  
       OrderID    int Primary Key,  
       CustomerID nchar(5) Foreign Key REFERENCES Cust(CustomerID))  
    GO  
    ```  
  
4.  <span data-ttu-id="90cd1-114">다음 예제 데이터를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="90cd1-114">Add this sample data:</span></span>  
  
    ```  
    INSERT INTO Cust(CustomerID, CompanyName, ContactName) VALUES  
         (N'ALFKI', N'Alfreds Futterkiste', N'Maria Anders')  
    INSERT INTO Cust(CustomerID, CompanyName, ContactName) VALUES  
         (N'ANATR', N'Ana Trujillo Emparedados y helados', N'Ana Trujillo')  
    INSERT INTO Cust(CustomerID, CompanyName, ContactName) VALUES  
         (N'ANTON', N'Antonio Moreno Taquer??a', N'Antonio Moreno')  
  
    INSERT INTO Ord(OrderID, CustomerID) VALUES(1, N'ALFKI')  
    INSERT INTO Ord(OrderID, CustomerID) VALUES(2, N'ANATR')  
    INSERT INTO Ord(OrderID, CustomerID) VALUES(3, N'ANTON')  
    ```  
  
5.  <span data-ttu-id="90cd1-115">위 DiffGram을 복사한 후 텍스트 파일에 붙여넣습니다.</span><span class="sxs-lookup"><span data-stu-id="90cd1-115">Copy the DiffGram above and paste it into a text file.</span></span> <span data-ttu-id="90cd1-116">파일을 1단계에 사용된 폴더와 같은 폴더에 MyDiffGram.xml로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="90cd1-116">Save the file as MyDiffGram.xml in the same folder used in step 1.</span></span>  
  
6.  <span data-ttu-id="90cd1-117">위의 C# 코드(DiffgramSample.cs)를 이전 단계에서 DiffGramSchema.xml 및 MyDiffGram.xml을 저장한 폴더와 같은 폴더에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="90cd1-117">Save the C# code (DiffgramSample.cs) that is provided above in the same folder in which the DiffGramSchema.xml and MyDiffGram.xml were stored in previous steps.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="90cd1-118">연결 문자열에 있는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인스턴스 이름 '`MyServer`'는 실제 설치된 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인스턴스 이름으로 업데이트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="90cd1-118">You will need to update the name of the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instance in the connection string from '`MyServer`' to the actual name of your installed instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
     <span data-ttu-id="90cd1-119">다른 폴더에 파일을 저장하는 경우 코드를 편집하여 매핑 스키마에 적합한 디렉터리 경로를 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="90cd1-119">If you store the files in a different folder, you will have to edit the code and specify the appropriate directory path for the mapping schema.</span></span>  
  
7.  <span data-ttu-id="90cd1-120">코드를 컴파일합니다.</span><span class="sxs-lookup"><span data-stu-id="90cd1-120">Compile the code.</span></span> <span data-ttu-id="90cd1-121">다음을 사용하여 명령 프롬프트에서 코드를 컴파일합니다.</span><span class="sxs-lookup"><span data-stu-id="90cd1-121">To compile the code at the command prompt, use:</span></span>  
  
    ```  
    csc /reference:Microsoft.Data.SqlXML.dll DiffgramSample.cs  
    ```  
  
     <span data-ttu-id="90cd1-122">이렇게 하면 실행 파일(DiffgramSample.exe)이 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="90cd1-122">This creates an executable (DiffgramSample.exe).</span></span>  
  
8.  <span data-ttu-id="90cd1-123">명령 프롬프트에서 DiffgramSample.exe를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="90cd1-123">At the command prompt, execute DiffgramSample.exe.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90cd1-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="90cd1-124">See Also</span></span>  
 [<span data-ttu-id="90cd1-125">DiffGram 예 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="90cd1-125">DiffGram Examples &#40;SQLXML 4.0&#41;</span></span>](diffgram-examples-sqlxml-4-0.md)  
  
  
