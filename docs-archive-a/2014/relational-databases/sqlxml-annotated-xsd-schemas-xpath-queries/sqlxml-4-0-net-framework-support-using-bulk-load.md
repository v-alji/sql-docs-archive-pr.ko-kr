---
title: .NET 환경에서 SQLXML 대량 로드 사용 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- SQLXML, XML Bulk Load
- XML Bulk Load [SQLXML], .NET environment
- .NET Framework [SQLXML], XML Bulk Load
- bulk load [SQLXML], .NET environment
ms.assetid: b85df83b-ba56-43bf-bcdf-b2a6fca43276
author: rothja
ms.author: jroth
ms.openlocfilehash: 6bd1c44a8b56bc5129aeb9843ed9ba814d45742a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738175"
---
# <a name="using-sqlxml-bulk-load-in-the-net-environment"></a><span data-ttu-id="4b6cc-102">.NET 환경에서 SQLXML 대량 로드 사용</span><span class="sxs-lookup"><span data-stu-id="4b6cc-102">Using SQLXML Bulk Load in the .NET Environment</span></span>
  <span data-ttu-id="4b6cc-103">이 항목에서는 .NET 환경에서 XML 대량 로드 기능을 사용하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="4b6cc-103">This topic explains how the XML Bulk Load functionality can be used in the .NET environment.</span></span> <span data-ttu-id="4b6cc-104">XML 대량 로드에 대 한 자세한 내용은 [Xml 데이터 대량 로드 수행 &#40;SQLXML 4.0&#41;](bulk-load-xml/performing-bulk-load-of-xml-data-sqlxml-4-0.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="4b6cc-104">For detailed information about XML Bulk Load, see [Performing Bulk Load of XML Data &#40;SQLXML 4.0&#41;](bulk-load-xml/performing-bulk-load-of-xml-data-sqlxml-4-0.md).</span></span>  
  
 <span data-ttu-id="4b6cc-105">관리되는 환경에서 SQLXML 대량 로드 COM 개체를 사용하려면 이 개체에 대한 프로젝트 참조를 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4b6cc-105">To use the SQLXML Bulk Load COM object from a managed environment, you need to add a project reference to this object.</span></span> <span data-ttu-id="4b6cc-106">이렇게 하면 대량 로드 COM 개체에 대한 관리되는 래퍼 인터페이스가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="4b6cc-106">This generates a managed wrapper interface around the Bulk Load COM object.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4b6cc-107">관리되는 XML 대량 로드는 관리되는 스트림에는 사용할 수 없으며 네이티브 스트림에 대한 래퍼가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4b6cc-107">Managed XML Bulk load does not work with managed streams and requires a wrapper around native streams.</span></span> <span data-ttu-id="4b6cc-108">SQLXML 대량 로드 구성 요소는 다중 스레드 환경('[MTAThread]' 특성)에서는 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4b6cc-108">The SQLXML Bulk Load component will not run in a multi-threaded environment ('[MTAThread]' attribute).</span></span> <span data-ttu-id="4b6cc-109">다중 스레드 환경에서 대량 로드 구성 요소를 실행 하려고 하면 다음과 같은 추가 정보를 포함 하는 InvalidCastException 예외가 발생 합니다. "인터페이스 Sqlxml대량 Loadlib. 예외가에 대 한 QueryInterface가 실패 했습니다."</span><span class="sxs-lookup"><span data-stu-id="4b6cc-109">If you attempt to run the Bulk Load component in a multi-thread environment, you get an InvalidCastException exception with the following additional information: "QueryInterface for interface SQLXMLBULKLOADLib.ISQLXMLBulkLoad failed."</span></span> <span data-ttu-id="4b6cc-110">해결 방법은 샘플에 표시 된 것 처럼, **[STAThread]** 특성을 사용 하는 등의 방법으로 대량 로드 개체를 포함 하는 개체를 단일 스레드에 액세스할 수 있도록 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="4b6cc-110">The workaround is to make the object that contains the Bulk Load object single-thread accessible (for example, by using the **[STAThread]** attribute as shown in the sample).</span></span>  
  
 <span data-ttu-id="4b6cc-111">이 항목에서는 XML 데이터를 데이터베이스에 대량 로드하기 위한 C# 작업 예제 애플리케이션을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="4b6cc-111">This topic provides a working C# sample application to bulk load XML data in the database.</span></span> <span data-ttu-id="4b6cc-112">작업 예제를 만들려면 다음 단계를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="4b6cc-112">To create a working sample, follow these steps:</span></span>  
  
1.  <span data-ttu-id="4b6cc-113">다음 테이블을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="4b6cc-113">Create the following tables:</span></span>  
  
    ```  
    CREATE TABLE Ord (  
             OrderID     int identity(1,1)  PRIMARY KEY,  
             CustomerID  varchar(5))  
    GO  
    CREATE TABLE Product (  
             ProductID   int identity(1,1) PRIMARY KEY,  
             ProductName varchar(20))  
    GO  
    CREATE TABLE OrderDetail (  
           OrderID     int FOREIGN KEY REFERENCES Ord(OrderID),  
           ProductID   int FOREIGN KEY REFERENCES Product(ProductID),  
                       CONSTRAINT OD_key PRIMARY KEY (OrderID, ProductID))  
    GO  
    ```  
  
2.  <span data-ttu-id="4b6cc-114">다음 스키마를 schema.xml 파일에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="4b6cc-114">Save the following schema in a file (schema.xml):</span></span>  
  
    ```  
    <xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
                xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
    <xsd:annotation>  
      <xsd:appinfo>  
        <sql:relationship name="OrderOD"  
              parent="Ord"  
              parent-key="OrderID"  
              child="OrderDetail"  
              child-key="OrderID" />  
  
        <sql:relationship name="ODProduct"  
              parent="OrderDetail"  
              parent-key="ProductID"  
              child="Product"  
              child-key="ProductID"   
              inverse="true"/>  
      </xsd:appinfo>  
    </xsd:annotation>  
  
      <xsd:element name="Order" sql:relation="Ord"   
                                sql:key-fields="OrderID" >  
       <xsd:complexType>  
         <xsd:sequence>  
            <xsd:element name="Product" sql:relation="Product"   
                         sql:key-fields="ProductID"  
                         sql:relationship="OrderOD ODProduct">  
              <xsd:complexType>  
                 <xsd:attribute name="ProductID" type="xsd:int" />  
                 <xsd:attribute name="ProductName" type="xsd:string" />  
              </xsd:complexType>  
            </xsd:element>  
         </xsd:sequence>  
            <xsd:attribute name="OrderID"   type="xsd:integer" />   
            <xsd:attribute name="CustomerID"   type="xsd:string" />  
        </xsd:complexType>  
      </xsd:element>  
    </xsd:schema>  
    ```  
  
3.  <span data-ttu-id="4b6cc-115">다음 예제 XML 문서를 data.xml 파일에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="4b6cc-115">Save the following sample XML document in a file (data.xml):</span></span>  
  
    ```  
    <ROOT>    
      <Order OrderID="11" CustomerID="ALFKI">  
        <Product ProductID="11" ProductName="Chai" />  
        <Product ProductID="22" ProductName="Chang" />  
      </Order>  
      <Order OrderID="22" CustomerID="ANATR">  
         <Product ProductID="33" ProductName="Aniseed Syrup" />  
        <Product ProductID="44" ProductName="Gumbo Mix" />  
      </Order>  
    </ROOT>  
    ```  
  
4.  <span data-ttu-id="4b6cc-116">Visual Studio를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="4b6cc-116">Start Visual Studio.</span></span>  
  
5.  <span data-ttu-id="4b6cc-117">C# 콘솔 애플리케이션을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="4b6cc-117">Create a C# console application.</span></span>  
  
6.  <span data-ttu-id="4b6cc-118">**프로젝트** 메뉴에서 **참조 추가**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="4b6cc-118">From the **Project** menu, select **Add Reference**.</span></span>  
  
7.  <span data-ttu-id="4b6cc-119">**COM** 탭에서 **Microsoft SQLXML Bulkload 4.0 형식 라이브러리** (xblkld4.dll)를 선택 하 고 **확인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="4b6cc-119">In the **COM** tab, select **Microsoft SQLXML Bulkload 4.0 Type Library** (xblkld4.dll) and click **OK**.</span></span> <span data-ttu-id="4b6cc-120">프로젝트에서 생성 된 **Interop. Sqlxml대량 Loadlib** 어셈블리가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4b6cc-120">You will see the **Interop.SQLXMLBULKLOADLib** assembly created in the project.</span></span>  
  
8.  <span data-ttu-id="4b6cc-121">Main() 메서드를 다음 코드로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="4b6cc-121">Replace the Main() method with the following code.</span></span> <span data-ttu-id="4b6cc-122">**ConnectionString** 속성 및 파일 경로를 스키마 및 데이터 파일로 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="4b6cc-122">Update the **ConnectionString** property and the file path to the schema and data files.</span></span>  
  
    ```  
    [STAThread]  
       static void Main(string[] args)  
       {     
             try  
             {  
                SQLXMLBULKLOADLib.SQLXMLBulkLoad4Class objBL = new SQLXMLBULKLOADLib.SQLXMLBulkLoad4Class();  
                objBL.ConnectionString = "Provider=sqloledb;server=server;database=databaseName;integrated security=SSPI";  
                objBL.ErrorLogFile = "error.xml";  
                objBL.KeepIdentity = false;  
                objBL.Execute ("schema.xml","data.xml");  
             }  
             catch(Exception e)  
             {  
             Console.WriteLine(e.ToString());  
             }  
       }  
    ```  
  
9. <span data-ttu-id="4b6cc-123">앞에서 만든 테이블에 XML을 로드하려면 프로젝트를 빌드하고 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="4b6cc-123">To load the XML in the table you created, build and run the project.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="4b6cc-124">대량 로드 구성 요소(xblkld4.dll)에 대한 참조는 .NET Framework에 포함된 tlbimp.exe 도구를 사용하여 추가할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4b6cc-124">The reference to the Bulk Load component (xblkld4.dll) can also be added using the tlbimp.exe tool, which is available as part of .NET framework.</span></span> <span data-ttu-id="4b6cc-125">이 도구는 네이티브 DLL(xblkld4.dll)에 대한 관리되는 래퍼를 만들며 이 래퍼는 모든 .NET 프로젝트에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4b6cc-125">This tool creates a managed wrapper for the native DLL (xblkld4.dll), which can then be used in any .NET project.</span></span> <span data-ttu-id="4b6cc-126">예:</span><span class="sxs-lookup"><span data-stu-id="4b6cc-126">For example:</span></span>  
  
    ```  
    c:\>tlbimp xblkld4.dll  
    ```  
  
     <span data-ttu-id="4b6cc-127">그러면 .NET Framework 프로젝트에서 사용할 수 있는 관리되는 래퍼 DLL(SQLXMLBULKLOADLib.dll)이 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="4b6cc-127">This creates the managed wrapper DLL (SQLXMLBULKLOADLib.dll) that you can use in the .NET Framework project.</span></span> <span data-ttu-id="4b6cc-128">.NET Framework에서 새로 생성된 DLL에 대한 프로젝트 참조를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="4b6cc-128">In the .NET Framework, you add project reference to the newly created DLL.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b6cc-129">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4b6cc-129">See Also</span></span>  
 [<span data-ttu-id="4b6cc-130">XML 데이터 대량 로드 수행&#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="4b6cc-130">Performing Bulk Load of XML Data &#40;SQLXML 4.0&#41;</span></span>](bulk-load-xml/performing-bulk-load-of-xml-data-sqlxml-4-0.md)  
  
  
