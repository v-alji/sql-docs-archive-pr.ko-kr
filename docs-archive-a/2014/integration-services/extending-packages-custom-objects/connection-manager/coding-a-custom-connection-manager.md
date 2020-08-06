---
title: 사용자 지정 연결 관리자 코딩 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- custom connection managers [Integration Services], coding
ms.assetid: b12b6778-1f01-4a7d-984d-73f2f7630aa5
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 793d70ba0a9ae6176ab35c82e16b9aba8c9ba2cb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736586"
---
# <a name="coding-a-custom-connection-manager"></a><span data-ttu-id="7ab08-102">사용자 지정 연결 관리자 코딩</span><span class="sxs-lookup"><span data-stu-id="7ab08-102">Coding a Custom Connection Manager</span></span>
  <span data-ttu-id="7ab08-103"><xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase> 기본 클래스에서 상속된 클래스를 만들고 이 클래스에 <xref:Microsoft.SqlServer.Dts.Runtime.DtsConnectionAttribute> 특성을 적용한 후에는 기본 클래스의 속성 및 메서드 구현을 재정의하여 사용자 지정 기능을 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ab08-103">After you have created a class that inherits from the <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase> base class, and applied the <xref:Microsoft.SqlServer.Dts.Runtime.DtsConnectionAttribute> attribute to the class, you must override the implementation of the properties and methods of the base class to provide your custom functionality.</span></span>  
  
 <span data-ttu-id="7ab08-104">사용자 지정 연결 관리자의 예제는 [사용자 지정 연결 관리자의 사용자 인터페이스 개발](developing-a-user-interface-for-a-custom-connection-manager.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7ab08-104">For samples of custom connection managers, see [Developing a User Interface for a Custom Connection Manager](developing-a-user-interface-for-a-custom-connection-manager.md).</span></span> <span data-ttu-id="7ab08-105">이 항목에 표시된 코드 예는 SQL Server 사용자 지정 연결 관리자 예제에서 가져온 것입니다.</span><span class="sxs-lookup"><span data-stu-id="7ab08-105">The code examples shown in this topic are drawn from the SQL Server Custom Connection Manager sample.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7ab08-106">[!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)]에 기본 제공된 대부분의 태스크, 원본 및 대상은 특정 유형의 기본 제공 연결 관리자와만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ab08-106">Most of the tasks, sources, and destinations that have been built into [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] work only with specific types of built-in connection managers.</span></span> <span data-ttu-id="7ab08-107">따라서 이러한 예제를 기본 제공 태스크 및 구성 요소와 함께 테스트할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7ab08-107">Therefore, these samples cannot be tested with the built-in tasks and components.</span></span>  
  
## <a name="configuring-the-connection-manager"></a><span data-ttu-id="7ab08-108">연결 관리자 구성</span><span class="sxs-lookup"><span data-stu-id="7ab08-108">Configuring the Connection Manager</span></span>  
  
### <a name="setting-the-connectionstring-property"></a><span data-ttu-id="7ab08-109">ConnectionString 속성 설정</span><span class="sxs-lookup"><span data-stu-id="7ab08-109">Setting the ConnectionString Property</span></span>  
 <span data-ttu-id="7ab08-110"><xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.ConnectionString%2A> 속성은 중요한 속성으로서, 사용자 지정 연결 관리자에 고유한 유일한 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="7ab08-110">The <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.ConnectionString%2A> property is an important property and the only property unique to a custom connection manager.</span></span> <span data-ttu-id="7ab08-111">연결 관리자는 이 속성 값을 사용하여 외부 데이터 원본에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="7ab08-111">The connection manager uses the value of this property to connect to the external data source.</span></span> <span data-ttu-id="7ab08-112">서버 이름 및 데이터베이스 이름 등의 다른 여러 속성을 조합하여 연결 문자열을 만들 경우 도우미 함수로 연결 문자열 템플릿의 일부 값을 사용자가 지정한 새 값으로 바꿔 문자열을 조합할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ab08-112">If you are combining several other properties, such as server name and database name, to create the connection string, you can use a helper function to assemble the string by replacing certain values in a connection string template with the new value supplied by the user.</span></span> <span data-ttu-id="7ab08-113">다음 코드 예에서는 도우미 함수를 사용하여 문자열을 조합하는 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.ConnectionString%2A> 속성의 구현을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="7ab08-113">The following code example shows an implementation of the <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.ConnectionString%2A> property that relies on a helper function to assemble the string.</span></span>  
  
```vb  
' Default values.  
Private _serverName As String = "(local)"  
Private _databaseName As String = "AdventureWorks"  
Private _connectionString As String = String.Empty  
  
Private Const CONNECTIONSTRING_TEMPLATE As String = _  
  "Data Source=<servername>;Initial Catalog=<databasename>;Integrated Security=SSPI"  
  
Public Property ServerName() As String  
  Get  
    Return _serverName  
  End Get  
  Set(ByVal value As String)  
    _serverName = value  
  End Set  
End Property  
  
Public Property DatabaseName() As String  
  Get  
    Return _databaseName  
  End Get  
  Set(ByVal value As String)  
    _databaseName = value  
  End Set  
End Property  
  
Public Overrides Property ConnectionString() As String  
  Get  
    UpdateConnectionString()  
    Return _connectionString  
  End Get  
  Set(ByVal value As String)  
    _connectionString = value  
  End Set  
End Property  
  
Private Sub UpdateConnectionString()  
  
  Dim temporaryString As String = CONNECTIONSTRING_TEMPLATE  
  
  If Not String.IsNullOrEmpty(_serverName) Then  
    temporaryString = temporaryString.Replace("<servername>", _serverName)  
  End If  
  If Not String.IsNullOrEmpty(_databaseName) Then  
    temporaryString = temporaryString.Replace("<databasename>", _databaseName)  
  End If  
  
  _connectionString = temporaryString  
  
End Sub  
```  
  
```csharp  
// Default values.  
private string _serverName = "(local)";  
private string _databaseName = "AdventureWorks";  
private string _connectionString = String.Empty;  
  
private const string CONNECTIONSTRING_TEMPLATE = "Data Source=<servername>;Initial Catalog=<databasename>;Integrated Security=SSPI";  
  
public string ServerName  
{  
  get  
  {  
    return _serverName;  
  }  
  set  
  {  
    _serverName = value;  
  }  
}  
  
public string DatabaseName  
{  
  get  
  {  
    return _databaseName;  
  }  
  set  
  {  
    _databaseName = value;  
  }  
}  
  
public override string ConnectionString  
{  
  get  
  {  
    UpdateConnectionString();  
    return _connectionString;  
  }  
  set  
  {  
    _connectionString = value;  
  }  
}  
  
private void UpdateConnectionString()  
{  
  
  string temporaryString = CONNECTIONSTRING_TEMPLATE;  
  
  if (!String.IsNullOrEmpty(_serverName))  
  {  
    temporaryString = temporaryString.Replace("<servername>", _serverName);  
  }  
  
  if (!String.IsNullOrEmpty(_databaseName))  
  {  
    temporaryString = temporaryString.Replace("<databasename>", _databaseName);  
  }  
  
  _connectionString = temporaryString;  
  
}  
```  
  
### <a name="validating-the-connection-manager"></a><span data-ttu-id="7ab08-114">연결 관리자 유효성 검사</span><span class="sxs-lookup"><span data-stu-id="7ab08-114">Validating the Connection Manager</span></span>  
 <span data-ttu-id="7ab08-115"><xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.Validate%2A> 메서드를 재정의하여 연결 관리자가 올바르게 구성되어 있는지 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ab08-115">You override the <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.Validate%2A> method to make sure that the connection manager has been configured correctly.</span></span> <span data-ttu-id="7ab08-116">최소한 연결 문자열 형식의 유효성을 검사하고 모든 인수에 값이 지정되었는지 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ab08-116">At a minimum, you should validate the format of the connection string and make sure that values have been provided for all arguments.</span></span> <span data-ttu-id="7ab08-117">연결 관리자가 <xref:Microsoft.SqlServer.Dts.Runtime.DTSExecResult.Success> 메서드에서 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.Validate%2A>를 반환하기 전까지는 실행을 계속할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7ab08-117">Execution cannot continue until the connection manager returns <xref:Microsoft.SqlServer.Dts.Runtime.DTSExecResult.Success> from the <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.Validate%2A> method.</span></span>  
  
 <span data-ttu-id="7ab08-118">다음 코드 예에서는 사용자가 연결의 서버 이름을 지정했는지 확인하는 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.Validate%2A>의 구현을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="7ab08-118">The following code example shows an implementation of <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.Validate%2A> that makes sure that the user has specified a server name for the connection.</span></span>  
  
```vb  
Public Overrides Function Validate(ByVal infoEvents As Microsoft.SqlServer.Dts.Runtime.IDTSInfoEvents) As Microsoft.SqlServer.Dts.Runtime.DTSExecResult  
  
  If String.IsNullOrEmpty(_serverName) Then  
    infoEvents.FireError(0, "SqlConnectionManager", "No server name specified", String.Empty, 0)  
    Return DTSExecResult.Failure  
  Else  
    Return DTSExecResult.Success  
  End If  
  
End Function  
```  
  
```csharp  
public override Microsoft.SqlServer.Dts.Runtime.DTSExecResult Validate(Microsoft.SqlServer.Dts.Runtime.IDTSInfoEvents infoEvents)  
{  
  
  if (String.IsNullOrEmpty(_serverName))  
  {  
    infoEvents.FireError(0, "SqlConnectionManager", "No server name specified", String.Empty, 0);  
    return DTSExecResult.Failure;  
  }  
  else  
  {  
    return DTSExecResult.Success;  
  }  
  
}  
```  
  
### <a name="persisting-the-connection-manager"></a><span data-ttu-id="7ab08-119">연결 관리자 지속</span><span class="sxs-lookup"><span data-stu-id="7ab08-119">Persisting the Connection Manager</span></span>  
 <span data-ttu-id="7ab08-120">일반적으로 연결 관리자의 사용자 지정 지속성은 구현할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7ab08-120">Usually, you do not have to implement custom persistence for a connection manager.</span></span> <span data-ttu-id="7ab08-121">사용자 지정 지속성은 개체의 속성이 복합 데이터 형식을 사용할 때만 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="7ab08-121">Custom persistence is required only when the properties of an object use complex data types.</span></span> <span data-ttu-id="7ab08-122">자세한 내용은[Integration Services 사용자 지정 개체 개발](../developing-custom-objects-for-integration-services.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7ab08-122">For more information, see [Developing Custom Objects for Integration Services](../developing-custom-objects-for-integration-services.md).</span></span>  
  
## <a name="working-with-the-external-data-source"></a><span data-ttu-id="7ab08-123">외부 데이터 원본 작업</span><span class="sxs-lookup"><span data-stu-id="7ab08-123">Working with the External Data Source</span></span>  
 <span data-ttu-id="7ab08-124">외부 데이터 원본에 대한 연결을 지원하는 메서드는 사용자 지정 연결 관리자의 중요한 메서드입니다.</span><span class="sxs-lookup"><span data-stu-id="7ab08-124">The methods that support connecting to an external data source are the most important methods of a custom connection manager.</span></span> <span data-ttu-id="7ab08-125"><xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.AcquireConnection%2A> 및 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.ReleaseConnection%2A> 메서드는 디자인 타임과 런타임에 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="7ab08-125">The <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.AcquireConnection%2A> and <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.ReleaseConnection%2A> methods are called at various times during both design time and run time.</span></span>  
  
### <a name="acquiring-the-connection"></a><span data-ttu-id="7ab08-126">연결 설정</span><span class="sxs-lookup"><span data-stu-id="7ab08-126">Acquiring the Connection</span></span>  
 <span data-ttu-id="7ab08-127"><xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.AcquireConnection%2A> 메서드가 사용자 지정 연결 관리자에서 반환하는 데 적절한 개체 유형을 결정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ab08-127">You need to decide what type of object it is appropriate for the <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.AcquireConnection%2A> method to return from your custom connection manager.</span></span> <span data-ttu-id="7ab08-128">예를 들어 파일 연결 관리자는 경로 및 파일 이름이 들어 있는 문자열만 반환하는 반면에 ADO.NET 연결 관리자는 이미 열려 있는 관리되는 연결 개체를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="7ab08-128">For example, a File connection manager returns only a string that contains a path and filename, whereas an ADO.NET connection manager returns a managed connection object that is already open.</span></span> <span data-ttu-id="7ab08-129">또한 OLE DB 연결 관리자는 관리 코드에서 사용할 수 없는 네이티브 OLE DB 연결 개체를 반환하고,</span><span class="sxs-lookup"><span data-stu-id="7ab08-129">An OLE DB connection manager returns a native OLE DB connection object that cannot be used from managed code.</span></span> <span data-ttu-id="7ab08-130">사용자 지정 SQL Server 연결 관리자는 열려 있는 `SqlConnection` 개체를 반환합니다. 이 항목의 코드 조각은 이 연결 관리자의 일부입니다.</span><span class="sxs-lookup"><span data-stu-id="7ab08-130">The custom SQL Server connection manager, from which the code snippets in this topic are taken, returns an open `SqlConnection` object.</span></span>  
  
 <span data-ttu-id="7ab08-131">연결 관리자의 사용자는 반환된 개체를 적절한 유형으로 캐스팅하고 해당 메서드 및 속성에 액세스할 수 있도록 예상되는 개체 유형을 미리 알고 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ab08-131">Users of your connection manager need to know in advance what type of object to expect, so that they can cast the returned object to the appropriate type and access its methods and properties.</span></span>  
  
```vb  
Public Overrides Function AcquireConnection(ByVal txn As Object) As Object  
  
  Dim sqlConnection As New SqlConnection  
  
  UpdateConnectionString()  
  
  With sqlConnection  
    .ConnectionString = _connectionString  
    .Open()  
  End With  
  
  Return sqlConnection  
  
End Function  
```  
  
```csharp  
public override object AcquireConnection(object txn)  
{  
  
  SqlConnection sqlConnection = new SqlConnection();  
  
  UpdateConnectionString();  
  
  {  
    sqlConnection.ConnectionString = _connectionString;  
    sqlConnection.Open();  
  }  
  
  return sqlConnection;  
  
}  
```  
  
### <a name="releasing-the-connection"></a><span data-ttu-id="7ab08-132">연결 해제</span><span class="sxs-lookup"><span data-stu-id="7ab08-132">Releasing the Connection</span></span>  
 <span data-ttu-id="7ab08-133"><xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.ReleaseConnection%2A> 메서드에서 수행하는 동작은 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.AcquireConnection%2A> 메서드에서 반환된 개체의 유형에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="7ab08-133">The action that you take in the <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.ReleaseConnection%2A> method depends on the type of object that you returned from the <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.AcquireConnection%2A> method.</span></span> <span data-ttu-id="7ab08-134">열려 있는 연결 개체가 있는 경우 해당 연결 개체를 닫고 이 개체에서 사용 중인 리소스를 해제해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ab08-134">If there is an open connection object, you should close it and to release any resources that it is using.</span></span> <span data-ttu-id="7ab08-135"><xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.AcquireConnection%2A>이 문자열 값만 반환한 경우에는 아무 동작도 수행할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7ab08-135">If <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.AcquireConnection%2A> returned only a string value, no action needs to be taken.</span></span>  
  
```vb  
Public Overrides Sub ReleaseConnection(ByVal connection As Object)  
  
  Dim sqlConnection As SqlConnection  
  
  sqlConnection = DirectCast(connection, SqlConnection)  
  
  If sqlConnection.State <> ConnectionState.Closed Then  
    sqlConnection.Close()  
  End If  
  
End Sub  
```  
  
```csharp  
public override void ReleaseConnection(object connection)  
{  
  SqlConnection sqlConnection;  
  sqlConnection = (SqlConnection)connection;  
  if (sqlConnection.State != ConnectionState.Closed)  
    sqlConnection.Close();  
}  
```  
  
<span data-ttu-id="7ab08-136">![Integration Services 아이콘 (작은 아이콘)](../../media/dts-16.gif "Integration Services 아이콘(작은 아이콘)")  **은 최신 상태로 유지 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="7ab08-136">![Integration Services icon (small)](../../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="7ab08-137">Microsoft의 최신 다운로드, 문서, 예제 및 비디오와 커뮤니티에서 선택된 솔루션을 보려면 MSDN의 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="7ab08-137">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="7ab08-138">MSDN의 Integration Services 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="7ab08-138">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="7ab08-139">이러한 업데이트에 대한 자동 알림을 받으려면 해당 페이지에서 제공하는 RSS 피드를 구독하세요.</span><span class="sxs-lookup"><span data-stu-id="7ab08-139">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ab08-140">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7ab08-140">See Also</span></span>  
 <span data-ttu-id="7ab08-141">[사용자 지정 연결 관리자 만들기](creating-a-custom-connection-manager.md) </span><span class="sxs-lookup"><span data-stu-id="7ab08-141">[Creating a Custom Connection Manager](creating-a-custom-connection-manager.md) </span></span>  
 [<span data-ttu-id="7ab08-142">사용자 지정 연결 관리자의 사용자 인터페이스 개발</span><span class="sxs-lookup"><span data-stu-id="7ab08-142">Developing a User Interface for a Custom Connection Manager</span></span>](developing-a-user-interface-for-a-custom-connection-manager.md)  
  
  
