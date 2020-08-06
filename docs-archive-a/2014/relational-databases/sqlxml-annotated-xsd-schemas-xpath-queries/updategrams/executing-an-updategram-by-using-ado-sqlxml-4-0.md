---
title: ADO를 사용 하 여 Updategram 실행 (SQLXML 4.0) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- ADO [SQLXML]
- updategrams [SQLXML], ADO
- executing updategrams [SQLXML]
ms.assetid: 78610ca0-f763-45fc-ac64-da5c192cc3e5
author: rothja
ms.author: jroth
ms.openlocfilehash: d8bc00406705e73eb6c9a4f2474ac1865344a8bb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653768"
---
# <a name="executing-an-updategram-by-using-ado-sqlxml-40"></a><span data-ttu-id="36046-102">ADO를 사용하여 updategram 실행(SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="36046-102">Executing an Updategram by Using ADO (SQLXML 4.0)</span></span>
  <span data-ttu-id="36046-103">이 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic 애플리케이션은 ADO를 사용하여 Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인스턴스에 연결하고 updategram을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="36046-103">This [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic application uses ADO to establish a connection to an instance of Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] and execute an updategram.</span></span> <span data-ttu-id="36046-104">사용되는 updategram은 특정 직원의 성을 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="36046-104">The updategram updates the last name of a specific employee.</span></span> <span data-ttu-id="36046-105">이 예에서는 AdventureWorks 예제 데이터베이스를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="36046-105">This example uses the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="36046-106">이 예제 애플리케이션에서는 다음 작업이 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="36046-106">In this sample application:</span></span>  
  
-   <span data-ttu-id="36046-107">**Conn** 개체 (**ADODB. 연결**) 특정 서버 컴퓨터에서 실행 중인 인스턴스에 대 한 연결을 설정 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 합니다.</span><span class="sxs-lookup"><span data-stu-id="36046-107">The **conn** object (**ADODB.Connection**) establishes a connection to a running instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] on a specific server computer.</span></span>  
  
-   <span data-ttu-id="36046-108">**Cmd** 개체 (**ADODB 명령**)는 설정 된 연결에서 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="36046-108">The **cmd** object (**ADODB.Command**) executes on the established connection.</span></span>  
  
-   <span data-ttu-id="36046-109">명령 언어가 DBGUID_MSSQLXML로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="36046-109">The command dialect is set to DBGUID_MSSQLXML.</span></span>  
  
-   <span data-ttu-id="36046-110">Updategram가 명령 스트림 (**Strmin**)에 복사 됩니다.</span><span class="sxs-lookup"><span data-stu-id="36046-110">The updategram is copied to the command stream (**strmIn**).</span></span>  
  
-   <span data-ttu-id="36046-111">명령의 출력 스트림은 **Strmout** 개체 (**ADODB. Stream**)을 클릭 하 여 반환 된 데이터를 수신 합니다.</span><span class="sxs-lookup"><span data-stu-id="36046-111">The command's output stream is set to the **StrmOut** object (**ADODB.Stream**) to receive any returned data.</span></span>  
  
-   <span data-ttu-id="36046-112">최종적으로 명령(updategram)이 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="36046-112">Finally the command (updategram) is executed.</span></span>  
  
 <span data-ttu-id="36046-113">다음은 예제 코드입니다.</span><span class="sxs-lookup"><span data-stu-id="36046-113">Here is the sample code:</span></span>  
  
```vb  
Private Sub Form_Load()  
  
  Dim cmd As New ADODB.Command  
  Dim conn As New ADODB.Connection  
  Dim strmIn As New ADODB.Stream  
  Dim strmOut As New ADODB.Stream  
  Dim SQLxml As String  
  
  ' Open a connection to the instance of SQL Server.  
  conn.Provider = "SQLOLEDB"  
  conn.Open "server=(local); database=AdventureWorks; Integrated Security=SSPI; "  
  conn.Properties("SQLXML Version") = "SQLXML.4.0"  
  Set cmd.ActiveConnection = conn  
  
  ' Build the command string in the form of an XML template.  
    SQLxml = "<ROOT xmlns:updg='urn:schemas-microsoft-com:xml-updategram' >"  
    SQLxml = SQLxml & "  <updg:sync updg:nullvalue='IsNULL'>"  
    SQLxml = SQLxml & "    <updg:before>"  
    SQLxml = SQLxml & "       <Person.Contact ContactID='64' Title='IsNULL'/>"  
    SQLxml = SQLxml & "    </updg:before>"  
    SQLxml = SQLxml & "    <updg:after>"  
    SQLxml = SQLxml & "       <Person.Contact ContactID='64' Title='Mr.'/>"  
    SQLxml = SQLxml & "    </updg:after>"  
    SQLxml = SQLxml & "  </updg:sync>"  
    SQLxml = SQLxml & "</ROOT>"  
  
  ' Set the command dialect to DBGUID_MSSQLXML.  
  cmd.Dialect = "{5d531cb2-e6ed-11d2-b252-00c04f681b71}"  
  
  ' Open the command stream and write our template to it.  
  strmIn.Open  
  strmIn.WriteText SQLxml  
  strmIn.Position = 0  
  
  Set cmd.CommandStream = strmIn  
  
  ' Execute the command, open the return stream, and read the result.  
  strmOut.Open  
  strmOut.LineSeparator = adCRLF  
  cmd.Properties("Output Stream").Value = strmOut  
  cmd.Properties("Output Encoding").Value = "UTF-8"  
  cmd.Execute , , adExecuteStream  
  strmOut.Position = 0  
  Debug.Print strmOut.ReadText  
  strmOut.Close  
  strmIn.Close  
  
End Sub  
  
```  
  
> [!NOTE]  
>  <span data-ttu-id="36046-114">XSD 스키마를 지정하는 updategram을 실행하기 위해 ADO에서 SQLXML을 사용하는 경우 다음 코드 예에서 볼 수 있듯이 연결 개체의 "`SQLXML Version`" 속성을 "`SQLXML.4.0`"으로 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="36046-114">If you're using SQLXML from ADO to execute updategrams that specify an XSD schema, you must set the "`SQLXML Version`" property to "`SQLXML.4.0`" on the connection object, as shown in the following example line of code:</span></span>  
>   
>  `conn.Properties("SQLXML Version") = "SQLXML.4.0"`  
  
## <a name="specifying-a-mapping-schema-for-the-updategram"></a><span data-ttu-id="36046-115">updategram에 대한 매핑 스키마 지정</span><span class="sxs-lookup"><span data-stu-id="36046-115">Specifying a Mapping Schema for the Updategram</span></span>  
 <span data-ttu-id="36046-116">이 예에서는 updategram에 매핑 스키마를 지정하고 사용하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="36046-116">This example illustrates how to specify and use a mapping schema in an updategram.</span></span>  
  
 <span data-ttu-id="36046-117">다음 XSD 스키마(EmpSchema.xml)를 디스크에 저장하고 이 코드에 지정된 경로를 디스크에서 매핑 스키마가 저장된 위치로 업데이트하십시오.</span><span class="sxs-lookup"><span data-stu-id="36046-117">Save the following XSD schema (EmpSchema.xml) to your disk, and be sure to update the path that is specified in the code to the location of the mapping schema on your disk.</span></span> <span data-ttu-id="36046-118">이 코드에서는 스키마가 C: 드라이브의 Schemas 폴더에 저장되어 있다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="36046-118">The code assumes that the schema is saved on the C: drive in the Schemas folder.</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:element name="Contact" sql:relation="Person.Contact" >  
   <xsd:complexType>  
        <xsd:attribute name="CID"    
                       sql:field="ContactID"   
                       type="xsd:string" />   
        <xsd:attribute name="MName"    
                       sql:field="MiddleName"    
                       type="xsd:string" />  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
 <span data-ttu-id="36046-119">XSD 및 XDR 스키마를 모두 지정할 수 있습니다. 다음은 동일한 XDR 스키마입니다.</span><span class="sxs-lookup"><span data-stu-id="36046-119">Because both XSD and XDR schemas can be specified, this is the equivalent XDR schema:</span></span>  
  
```  
<?xml version="1.0" ?>  
   <Schema xmlns="urn:schemas-microsoft-com:xml-data"   
         xmlns:dt="urn:schemas-microsoft-com:datatypes"   
         xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
     <ElementType name="Contact" sql:relation="Person.Contact" >  
       <AttributeType name="CID" />  
       <AttributeType name="MName" />  
  
       <attribute type="CID" sql:field="ContactID" />  
       <attribute type="MName" sql:field="MiddleName" />  
     </ElementType>  
   </Schema>   
```  
  
 <span data-ttu-id="36046-120">다음은 연결된 매핑 스키마가 있는 updategram을 실행하기 위한 Visual Basic 코드입니다.</span><span class="sxs-lookup"><span data-stu-id="36046-120">This is the Visual Basic code to execute an updategram that has an associated mapping schema.</span></span> <span data-ttu-id="36046-121">이 updategram은 Person.Contact 테이블에 있는 연락처 1의 중간 이름을 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="36046-121">The updategram updates the middle name for contact 1 in the Person.Contact table.</span></span>  
  
```vb  
Private Sub Form_Load()  
    Dim cmd As New ADODB.Command  
    Dim conn As New ADODB.Connection  
    Dim strmIn As New ADODB.Stream  
    Dim strmOut As New ADODB.Stream  
  
    ' Open a connection to the SQL Server.  
    conn.Provider = "SQLOLEDB"  
    conn.Open "server=(local); database=AdventureWorks; Integrated Security='SSPI' ;"  
    conn.Properties("SQLXML Version") = "SQLXML.4.0"  
    Set cmd.ActiveConnection = conn  
  
    ' Open the command stream and write the template to it.  
    strmIn.Open  
    strmIn.WriteText "<ROOT xmlns:updg='urn:schemas-microsoft-com:xml-updategram' >"  
    strmIn.WriteText "  <updg:sync mapping-schema='C:\Schemas\EmpSchema.xml' >"  
    strmIn.WriteText "      <updg:before>"  
    strmIn.WriteText "          <Contact CID='1' />"  
    strmIn.WriteText "      </updg:before>"  
    strmIn.WriteText "      <updg:after>"  
    strmIn.WriteText "          <Contact MName='M.'/>"  
    strmIn.WriteText "      </updg:after>"  
    strmIn.WriteText "  </updg:sync>"  
    strmIn.WriteText "</ROOT>"  
  
    ' Set the command dialect to XML.  
    cmd.Dialect = "{5d531cb2-e6ed-11d2-b252-00c04f681b71}"  
    strmIn.Position = 0  
    Set cmd.CommandStream = strmIn  
  
    ' Execute the command, open the return stream, and read the result.  
    strmOut.Open  
    strmOut.LineSeparator = adCRLF  
    cmd.Properties("Output Stream").Value = strmOut  
    cmd.Execute , , adExecuteStream  
    strmOut.Position = 0  
    Debug.Print strmOut.ReadText  
    strmOut.Close  
    strmIn.Close  
    conn.Close  
End Sub  
```  
  
## <a name="passing-parameters"></a><span data-ttu-id="36046-122">매개 변수 전달</span><span class="sxs-lookup"><span data-stu-id="36046-122">Passing Parameters</span></span>  
 <span data-ttu-id="36046-123">앞서 살펴보았던 Visual Basic 애플리케이션에서는 매개 변수가 전달되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="36046-123">In the Visual Basic applications provided earlier, parameters are not passed.</span></span> <span data-ttu-id="36046-124">이 응용 프로그램에서 **ContactID** 및 **MiddleName** 값은 매개 변수가 있는 입력으로 updategram에 전달 됩니다.</span><span class="sxs-lookup"><span data-stu-id="36046-124">In this application, the **ContactID** and **MiddleName** values are passed as parameterized input to the updategram.</span></span>  
  
```vb  
Private Sub Form_Load()  
  
  Dim cmd As New ADODB.Command  
  Dim conn As New ADODB.Connection  
  Dim strmIn As New ADODB.Stream  
  Dim strmOut As New ADODB.Stream  
  Dim InputContactID As String  
  Dim InputMiddleName As String  
  
  InputContactID = "1"  
  InputMiddleName = "Q."  
  
  ' Open a connection to the instance of SQL Server.  
  conn.Provider = "SQLOLEDB"  
  conn.Open "server=(local); database=AdventureWorks; Integrated Security=SSPI; "  
  conn.Properties("SQLXML Version") = "SQLXML.4.0"  
  Set cmd.ActiveConnection = conn  
  
  ' Build the command string in the form of an XML template.  
  SQLxml = "<ROOT xmlns:updg='urn:schemas-microsoft-com:xml-updategram' >"  
  SQLxml = SQLxml & "<updg:header>"  
  SQLxml = SQLxml & "<updg:param name='ContactID'/>"  
  SQLxml = SQLxml & "<updg:param name='MiddleName' />"  
  SQLxml = SQLxml & "</updg:header>"  
  SQLxml = SQLxml & "<updg:sync >"  
  SQLxml = SQLxml & " <updg:before>"  
  SQLxml = SQLxml & "   <Person.Contact ContactID='$ContactID' />"  
  SQLxml = SQLxml & "</updg:before>"  
  SQLxml = SQLxml & "<updg:after>"  
  SQLxml = SQLxml & "<Person.Contact MiddleName='$MiddleName' />"  
  SQLxml = SQLxml & "</updg:after>"  
  SQLxml = SQLxml & "</updg:sync>"  
  SQLxml = SQLxml & "</ROOT>"  
  
  ' Set the command dialect to XML.  
  cmd.Dialect = "{5d531cb2-e6ed-11d2-b252-00c04f681b71}"  
  
  ' Open the command stream and write the template to it.  
  strmIn.Open  
  strmIn.WriteText SQLxml  
  strmIn.Position = 0  
  
  Set cmd.CommandStream = strmIn  
  
  ' Execute the command, open the return stream, and read the result.  
  strmOut.Open  
  strmOut.LineSeparator = adCRLF  
  cmd.NamedParameters = True  
  cmd.Parameters.Append cmd.CreateParameter("@ContactID", adBSTR, adParamInput, 1, InputContactID)  
  cmd.Parameters.Append cmd.CreateParameter("@MiddleName", adBSTR, adParamInput, 7, InputMiddleName)  
  cmd.Properties("Output Stream").Value = strmOut  
  cmd.Execute , , adExecuteStream  
  strmOut.Position = 0  
  Debug.Print strmOut.ReadText  
  
End Sub  
```  
  
  
