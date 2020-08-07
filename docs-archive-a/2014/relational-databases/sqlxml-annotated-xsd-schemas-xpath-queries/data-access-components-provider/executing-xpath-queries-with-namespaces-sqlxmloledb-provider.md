---
title: 네임 스페이스를 사용 하 여 XPath 쿼리 실행 (SQLXMLOLEDB Provider) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- SQLXMLOLEDB Provider, executing XPath queries
- namespaces property
- queries [SQLXML], SQLXMLOLEDB Provider
- XPath queries [SQLXML], namespaces
- XPath queries [SQLXML], SQLXMLOLEDB Provider
- namespaces [SQLXML], XPath queries
ms.assetid: 024a4b7d-435d-47ba-9e80-2c2f640108f5
author: rothja
ms.author: jroth
ms.openlocfilehash: ff692b49a4c32c14655af3a9eb07071dc60ba2a9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87732471"
---
# <a name="executing-xpath-queries-with-namespaces-sqlxmloledb-provider"></a><span data-ttu-id="5474a-102">네임스페이스가 있는 XPath 쿼리 실행(SQLXMLOLEDB 공급자)</span><span class="sxs-lookup"><span data-stu-id="5474a-102">Executing XPath Queries with Namespaces (SQLXMLOLEDB Provider)</span></span>
  <span data-ttu-id="5474a-103">XPath 쿼리에는 네임스페이스가 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5474a-103">XPath queries can include namespaces.</span></span> <span data-ttu-id="5474a-104">스키마 요소의 네임스페이스가 한정된 경우 즉, 스키마 요소에 대상 네임스페이스가 포함된 경우 스키마에 대한 XPath 쿼리에서 이 네임스페이스를 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5474a-104">If the schema elements are namespace qualified (that is, if they include a target namespace), XPath queries against the schema must specify this namespace.</span></span>  
  
 <span data-ttu-id="5474a-105">SQLXML 4.0에서는 와일드카드 문자(\*)를 사용할 수 없으므로 네임스페이스 접두사를 사용하여 XPath 쿼리를 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5474a-105">Because using the wildcard character (\*) is not supported in SQLXML 4.0, you must specify the XPath query by using a namespace prefix.</span></span> <span data-ttu-id="5474a-106">이 접두사를 확인 하려면 네임 스페이스 속성을 사용 하 여 네임 스페이스 바인딩을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5474a-106">To resolve this prefix, use the namespaces property to specify the namespace binding.</span></span>  
  
 <span data-ttu-id="5474a-107">다음 예의 XPath 쿼리는 와일드 카드 문자 ( \* )와 로컬 이름 () 및 네임 스페이스 uri () XPath 함수를 사용 하 여 네임 스페이스를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5474a-107">In the following example, the XPath query specifies namespaces by using the wildcard character (\*) and the local-name() and namespace-uri() XPath functions.</span></span> <span data-ttu-id="5474a-108">이 XPath 쿼리는 로컬 이름이 `Contact`이고 네임스페이스 URI가 `urn:myschema:Contacts`인 모든 요소를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="5474a-108">This XPath query returns all the elements where the local name is `Contact` and the namespace URI is `urn:myschema:Contacts`.</span></span>  
  
```  
/*[local-name() = 'Contact' and namespace-uri() = 'urn:myschema:Contacts']  
```  
  
 <span data-ttu-id="5474a-109">SQLXML 4.0에서는 이 XPath 쿼리를 네임스페이스 접두사를 사용하여 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5474a-109">In SQLXML 4.0, this XPath query must be specified with a namespace prefix.</span></span> <span data-ttu-id="5474a-110">예를 들어 `x:Contact`의 경우 `x`가 네임스페이스 접두사입니다.</span><span class="sxs-lookup"><span data-stu-id="5474a-110">An example is `x:Contact`, where `x` is the namespace prefix.</span></span> <span data-ttu-id="5474a-111">다음과 같은 XSD 스키마를 살펴보십시오.</span><span class="sxs-lookup"><span data-stu-id="5474a-111">Consider the following XSD schema:</span></span>  
  
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
  
 <span data-ttu-id="5474a-112">이 스키마에서는 대상 네임스페이스를 정의하므로 스키마에 대한 XPath 쿼리(예: "Employee")에 네임스페이스가 포함되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5474a-112">Because this schema defines the target namespace, an XPath query (such as "Employee") against the schema must include the namespace.</span></span>  
  
 <span data-ttu-id="5474a-113">다음은 앞의 XSD 스키마에 대한 XPath 쿼리(x:Employee)를 실행하는 예제 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic 애플리케이션입니다.</span><span class="sxs-lookup"><span data-stu-id="5474a-113">This is a sample [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic application that executes an XPath query (x:Employee) against the preceding XSD schema.</span></span> <span data-ttu-id="5474a-114">접두사를 확인 하려면 네임 스페이스 속성을 사용 하 여 네임 스페이스 바인딩을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5474a-114">To resolve the prefix, the namespace binding is specified by using the namespaces property.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5474a-115">코드에서 연결 문자열에 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인스턴스의 이름을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5474a-115">In the code, you must provide the name of the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in the connection string.</span></span> <span data-ttu-id="5474a-116">또한 이 예에서는 데이터 공급자에 대해 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client(SQLNCLI11)를 사용하도록 지정하는데, 이렇게 하려면 추가 네트워크 클라이언트를 설치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5474a-116">Also, this example specifies the use of the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client (SQLNCLI11) for the data provider, which requires additional network client software to be installed.</span></span> <span data-ttu-id="5474a-117">자세한 내용은 [SQL Server Native Client에 대 한 시스템 요구 사항](../../native-client/system-requirements-for-sql-server-native-client.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="5474a-117">For more information, see [System Requirements for SQL Server Native Client](../../native-client/system-requirements-for-sql-server-native-client.md).</span></span>  
  
```  
Option Explicit  
Private Sub Form_Load()  
    Dim con As New ADODB.Connection  
    Dim cmd As New ADODB.Command  
    Dim stm As New ADODB.Stream  
    con.Open "provider=SQLXMLOLEDB.4.0;Data Provider=SQLNCLI11;Data Source=SqlServerName;Initial Catalog=AdventureWorks;Integrated Security=SSPI;"  
    Set cmd.ActiveConnection = con  
    stm.Open  
    cmd.Properties("Output Stream").Value = stm  
    cmd.Properties("Output Encoding") = "utf-8"  
    cmd.Properties("Mapping schema") = "C:\DirectoryPath\con-ex.xml"  
    cmd.Properties("namespaces") = "xmlns:x='urn:myschema:Contacts'"  
    '  Debug.Print "Set Command Dialect to DBGUID_XPATH"  
    cmd.Dialect = "{ec2a4293-e898-11d2-b1b7-00c04f680c56}"  
    cmd.CommandText = "x:Contact"  
    cmd.Execute , , adExecuteStream   
    stm.Position = 0  
    Debug.Print stm.ReadText(adReadAll)  
End Sub  
```  
  
### <a name="to-test-this-application"></a><span data-ttu-id="5474a-118">이 애플리케이션을 테스트하려면</span><span class="sxs-lookup"><span data-stu-id="5474a-118">To test this application</span></span>  
  
1.  <span data-ttu-id="5474a-119">예제 XSD 스키마를 폴더에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="5474a-119">Save the sample XSD schema in a folder.</span></span>  
  
2.  <span data-ttu-id="5474a-120">Visual Basic 실행 프로젝트를 만들고 여기로 코드를 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="5474a-120">Create a Visual Basic executable project, and copy the code into it.</span></span> <span data-ttu-id="5474a-121">지정된 디렉터리 경로를 적절하게 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="5474a-121">Change the specified directory path as appropriate.</span></span>  
  
3.  <span data-ttu-id="5474a-122">다음 프로젝트 참조를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="5474a-122">Add the following project reference:</span></span>  
  
    ```  
    "Microsoft ActiveX Data Objects 2.8 Library"  
    ```  
  
4.  <span data-ttu-id="5474a-123">애플리케이션을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="5474a-123">Execute the application.</span></span>  
  
 <span data-ttu-id="5474a-124">다음은 결과의 일부입니다.</span><span class="sxs-lookup"><span data-stu-id="5474a-124">This is the partial result:</span></span>  
  
```  
<y0:Employee xmlns:y0="urn:myschema:Contacts"   
             LName="Achong" CID="1" FName="Gustavo"/>  
<y0:Employee xmlns:y0="urn:myschema:Employees"   
             LName="Abel" CID="2" FName="Catherine"/>  
```  
  
 <span data-ttu-id="5474a-125">XML 문서에서 생성되는 접두사는 임의적이지만 동일한 네임스페이스에 매핑됩니다.</span><span class="sxs-lookup"><span data-stu-id="5474a-125">The prefixes that are generated in the XML document are arbitrary, but they map to the same namespace.</span></span>  
  
  
